---
title: "Gewusst wie: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung | Azure RMS"
description: "In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79397c82d9478cbd55630a376fe2d12f3873ebc4
ms.openlocfilehash: fce408a8c7a1114375745c3783443b87cd80ba78


---

# Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung

In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert. Weitere Informationen finden Sie unter [Erste Schritte mit Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx).

**Wichtig**  
Sie müssen eigene Mandanten erstellen, um die Rights Management Services SDK 2.1-Dienstanwendung mit Azure RMS zu verwenden. Weitere Informationen finden Sie unter [Azure RMS-Anforderungen: Cloudabonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md)

## Voraussetzungen

-   RMS SDK 2.1 muss installiert und konfiguriert sein. Weitere Informationen finden Sie unter [Erste Schritte mit RMS SDK 2.1](getting-started-with-ad-rms-2-0.md).
-   [Erstellen Sie eine Dienstidentität über ACS](https://msdn.microsoft.com/en-us/library/gg185924.aspx) mithilfe der symmetrischen Schlüsseloption oder auf andere Weise, und zeichnen Sie die Schlüsselinformation dieses Prozesses auf.

## Verbinden mit dem Azure-Rechteverwaltungsdienst

-   Rufen Sie [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) auf.
-   Legen Sie [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) fest.

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **Hinweis**  Weitere Informationen finden Sie unter [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md).

     
-   Mit den folgenden Schritten erstellen Sie eine Instanz einer [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx)-Struktur. Das Mitglied **pcCredential** ([**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)) wird dabei mit Verbindungsinformationen aus dem Azure Rights Management-Dienst aufgefüllt.
-   Verwenden Sie die beim Erstellen der Dienstidentität für den symmetrischen Schlüssel aufgezeichneten Informationen (siehe die weiter oben aufgeführten Voraussetzungen), um die Parameter **wszServicePrincipal**, **wszBposTenantId** und **cbKey** festzulegen, wenn Sie eine Instanz der [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key)-Struktur erstellen.

**Hinweis** Aufgrund einer Bedingung unseres Ermittlungsdiensts sind Anmeldeinformationen für symmetrische Schlüssel von anderen Regionen nur zulässig, wenn Sie sich in Nordamerika befinden. Aus diesem Grund müssen Sie Ihre Mandanten-URLs direkt eingeben. Verwenden Sie hierfür den Parameter [**IPC\_CONNECTION\_INFO**](/rights-management/sdk/2.1/api/win/ipc_connection_info#msipc_ipc_connection_info) von [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) oder [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist).

## Generieren Sie einen symmetrischen Schlüssel, und sammeln Sie die benötigten Informationen.

### Anweisungen zum Generieren eines symmetrischen Schlüssels

-   Installieren Sie den [Microsoft Online-Anmeldeassistenten](http://go.microsoft.com/fwlink/p/?LinkID=286152).
-   Installieren Sie das [Azure AD Powershell-Modul](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Hinweis**  Sie muss ein Mandantenadministrator sein, um die Powershell-Cmdlets verwenden zu können.

-   Starten Sie PowerShell, und führen Sie die folgenden Befehle zum Generieren eines Schlüssels aus         `Import-Module MSOnline`
            `Connect-MsolService` (Geben Sie Ihre Administrator-Anmeldeinformationen ein.)         `New-MsolServicePrincipal` (Geben Sie einen Anzeigenamen ein.)
-   Nachdem der symmetrische Schlüssel generiert wurde, werden Informationen zu dem Schlüssel sowie der Schlüssel an sich und **AppPrincipalId** ausgegeben.


    Der folgende symmetrische Schlüssel wurde erstellt, weil keiner angegeben wurde: ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

    DisplayName : RMSTestApp ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963} ObjectId : 0ee53770-ec86-409e-8939-6d8239880518 AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### Anweisungen zum Ermitteln von **TenantBposId** und **Urls**

-   Installieren Sie das [Azure RMS Powershell-Modul](https://technet.microsoft.com/en-us/library/jj585012.aspx).
-   Starten Sie Powershell, und führen Sie die folgenden Befehle aus, um die RMS-Konfiguration des Mandanten abzurufen.

    `Import-Module aadrm`

    `Connect-AadrmService` (Geben Sie Ihre Administrator-Anmeldeinformationen ein.)

    `Get-AadrmConfiguration`


-   Erstellen Sie eine Instanz von [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key), und legen Sie Mitglieder fest.

    // Erstellen Sie eine Schlüsselstruktur.
    IPC_CREDENTIAL_SYMMETRIC_KEY SymKey = {0};

    // Legen Sie jedes Mitglied mit Informationen von der Diensterstellung fest.
    symKey.wszBase64Key = "Ihr Dienstprinzipalschlüssel"; symKey.wszAppPrincipalId = "Ihr App-Prinzipalbezeichner"; symKey.wszBposTenantId = "Ihr Mandantenbezeichner";


Weitere Informationen finden Sie unter [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key).

-   Erstellen Sie eine Instanz der [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)-Struktur, die Ihre [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key)-Instanz enthält.

**Hinweis** Die *connectionInfo*-Mitglieder sind mit URLs aus dem vorherigen Aufruf von `Get-AadrmConfiguration` konfiguriert und mit diesen Feldnamen angegeben.

    // Create a credential structure.
    IPC_CREDENTIAL cred = {0};

    IPC_CONNECTION_INFO connectionInfo = {0};
    connectionInfo.wszIntranetUrl = LicensingIntranetDistributionPointUrl;
    connectionInfo.wszExtranetUrl = LicensingExtranetDistributionPointUrl;

    // Set each member.
    cred.dwType = IPC_CREDENTIAL_TYPE_SYMMETRIC_KEY;
    cred.pcCertContext = (PCCERT_CONTEXT)&symKey;

    // Create your prompt control.
    IPC_PROMPT_CTX promptCtx = {0};

    // Set each member.
    promptCtx.cbSize = sizeof(IPC_PROMPT_CTX);
    promptCtx.hwndParent = NULL;
    promptCtx.dwflags = IPC_PROMPT_FLAG_SILENT;
    promptCtx.hCancelEvent = NULL;
    promptCtx.pcCredential = &cred;

### Identifizieren einer Vorlage und Verschlüsselung

-   Wählen Sie eine Vorlage für die Verschlüsselung aus.
    Rufen Sie [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist) auf, und übergeben Sie dieselbe Instanz von [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx) zu übergeben.


    PCIPC_TIL pTemplates = NULL; IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

    hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),        IPC_GTL_FLAG_FORCE_DOWNLOAD,        0,        &promptCtx,        NULL,        &pTemplates);


-   Rufen Sie mit der bereits in diesem Thema behandelten Vorlage [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile) auf, und übergeben Sie dieselbe Instanz von [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx).

Beispiel für die Verwendung von [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile):

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Beispiel für die Verwendung von [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile):

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Sie haben jetzt die erforderlichen Schritte zum Aktivieren der Anwendung für die Verwendung von Azure Rights Management abgeschlossen.

## Verwandte Themen

* [Erste Schritte mit Azure Rights Management](https://technet.microsoft.com/en-us/library/jj585016.aspx)
* [Erste Schritte mit RMS SDK 2.1](getting-started-with-ad-rms-2-0.md)
* [Erstellen einer Dienstidentität über ACS](https://msdn.microsoft.com/en-us/library/gg185924.aspx)
* [**IpcSetGlobalProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty)
* [**IpcInitialize**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [**IPC\_PROMPT\_CTX**](/rights-management/sdk/2.1/api/win/ipc_prompt_ctx#msipc_ipc_prompt_ctx)
* [**IPC\_CREDENTIAL**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential)
* [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential_symmetric_key#msipc_ipc_credential_symmetric_key)
* [**IpcGetTemplateIssuerList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplateissuerlist)
* [**IpcGetTemplateList**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgettemplatelist)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfEncrcyptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcCreateLicenseFromTemplateID**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromtemplateid)
 

 



<!--HONumber=Jul16_HO4-->


