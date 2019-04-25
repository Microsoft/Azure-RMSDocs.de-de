---
title: 'Gewusst wie: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung | Azure RMS'
description: In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: dbd7969d5e6d87ec2d8e935f44867d58dfee9751
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60178385"
---
# <a name="how-to-enable-your-service-application-to-work-with-cloud-based-rms"></a>Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung

In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert. Weitere Informationen finden Sie unter [Erste Schritte mit Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx).

**Wichtig**  
Sie müssen eigene Mandanten erstellen, um die Rights Management Services SDK 2.1-Dienstanwendung mit Azure RMS zu verwenden. Weitere Informationen finden Sie unter [Azure RMS-Anforderungen: Cloud-Abonnements, die Azure RMS unterstützen](../requirements.md).

## <a name="prerequisites"></a>Vorraussetzungen

-   RMS SDK 2.1 muss installiert und konfiguriert sein. Weitere Informationen finden Sie unter [Erste Schritte mit RMS SDK 2.1](getting-started-with-ad-rms-2-0.md).
-   [Erstellen Sie eine Dienstidentität über ACS](https://msdn.microsoft.com/library/gg185924.aspx) mithilfe der symmetrischen Schlüsseloption oder auf andere Weise, und zeichnen Sie die Schlüsselinformation dieses Prozesses auf.

## <a name="connecting-to-the-azure-rights-management-service"></a>Verbinden mit dem Azure-Rechteverwaltungsdienst

-   Rufen Sie [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) auf.
-   Legen Sie [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) fest.

        C++
        int mode = IPC_API_MODE_SERVER;
        IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));


  **Hinweis**  Weitere Informationen finden Sie unter [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md).


-   Mit den folgenden Schritten erstellen Sie eine Instanz einer [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx)-Struktur. Das Mitglied *pcCredential* ([IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)) wird dabei mit Verbindungsinformationen aus dem Azure Rights Management-Dienst aufgefüllt.
-   Verwenden Sie die beim Erstellen der Dienstidentität für den symmetrischen Schlüssel aufgezeichneten Informationen (siehe die weiter oben aufgeführten Voraussetzungen), um die Parameter *wszServicePrincipal*, *wszBposTenantId* und *cbKey* festzulegen, wenn Sie eine Instanz der [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx)-Struktur erstellen.

**Hinweis** – Aufgrund einer Bedingung unseres Ermittlungsdiensts sind Anmeldeinformationen für symmetrische Schlüssel von anderen Regionen nur zulässig, wenn Sie sich in Nordamerika befinden. Aus diesem Grund müssen Sie Ihre Mandanten-URLs direkt eingeben. Verwenden Sie hierfür den Parameter *pConnectionInfo* mit dem Typ [IPC\_CONNECTION\_INFO](https://msdn.microsoft.com/library/hh535274.aspx) in den Funktionen [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx) oder [IpcGetTemplateIssuerList](https://msdn.microsoft.com/library/hh535266.aspx).

## <a name="generate-a-symmetric-key-and-collect-the-needed-information"></a>Generieren Sie einen symmetrischen Schlüssel, und sammeln Sie die benötigten Informationen.

### <a name="instructions-to-generate-a-symmetric-key"></a>Anweisungen zum Generieren eines symmetrischen Schlüssels

-   Installieren Sie den [Microsoft Online-Anmeldeassistenten](https://go.microsoft.com/fwlink/p/?LinkID=286152).
-   Installieren Sie das [Azure AD Powershell-Modul](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Hinweis** – Sie muss ein Mandantenadministrator sein, um die Powershell-Cmdlets verwenden zu können.

- Starten Sie PowerShell, und führen Sie die folgenden Befehle zum Generieren eines Schlüssels aus.

    `Import-Module MSOnline`

    `Connect-MsolService` (Geben Sie Ihre Administrator-Anmeldeinformationen ein.)

    `New-MsolServicePrincipal` (Geben Sie einen Anzeigenamen ein.)

- Nachdem der symmetrische Schlüssel generiert wurde, werden Informationen zu dem Schlüssel einschließlich des Schlüssels selbst und *AppPrincipalId* ausgegeben.

      The following symmetric key was created as one was not supplied
      ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

      DisplayName : RMSTestApp
      ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
      ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
      AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963


### <a name="instructions-to-find-out-tenantbposid-and-urls"></a>Anweisungen zum Ermitteln von **TenantBposId** und **Urls**

-   Installieren Sie das [Azure RMS PowerShell-Modul](https://technet.microsoft.com/library/jj585012.aspx).
-   Starten Sie PowerShell, und führen Sie die folgenden Befehle aus, um die RMS-Konfiguration des Mandanten abzurufen.

    `Import-Module aadrm`

    `Connect-AadrmService` (Geben Sie Ihre Administrator-Anmeldeinformationen ein.)

    `Get-AadrmConfiguration`


- Erstellen Sie eine Instanz von [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx), und legen Sie ein paar Mitglieder fest.

      // Create a key structure.
      IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

      // Set each member with information from service creation.
      symKey.wszBase64Key = "your service principal key";
      symKey.wszAppPrincipalId = "your app principal identifier";
      symKey.wszBposTenantId = "your tenant identifier";


Weitere Informationen finden Sie unter [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx).

-   Erstellen Sie eine Instanz der [IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)-Struktur, die Ihre [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx)-Instanz enthält.

**Hinweis** – Die *connectionInfo*-Mitglieder sind durch URLs aus dem vorherigen Aufruf von `Get-AadrmConfiguration` festgelegt und hier mit diesen Feldnamen angegeben.

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

### <a name="identify-a-template-and-then-encrypt"></a>Identifizieren einer Vorlage und Verschlüsselung

-   Wählen Sie eine Vorlage für die Verschlüsselung aus.
    Rufen Sie [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx) auf, und übergeben Sie dieselbe Instanz von [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx).


~~~
PCIPC_TIL pTemplates = NULL;
IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),
       IPC_GTL_FLAG_FORCE_DOWNLOAD,
       0,
       &promptCtx,
       NULL,
       &pTemplates);
~~~


-   Rufen Sie mit der bereits in diesem Thema behandelten Vorlage [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx) auf, und übergeben Sie dieselbe Instanz von [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx).

Beispiel für die Verwendung von [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx):

    LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
    hr = IpcfEncryptFile(wszInputFilePath,
           wszContentTemplateId,
           IPCF_EF_TEMPLATE_ID,
           IPC_EF_FLAG_KEY_NO_PERSIST,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Beispiel für die Verwendung von [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx):

    hr = IpcfDecryptFile(wszInputFilePath,
           IPCF_DF_FLAG_DEFAULT,
           &promptCtx,
           NULL,
           &wszOutputFilePath);

Sie haben jetzt die erforderlichen Schritte zum Aktivieren der Anwendung für die Verwendung von Azure Rights Management abgeschlossen.

## <a name="related-topics"></a>Verwandte Themen

* [Erste Schritte mit Azure Rights Management](https://technet.microsoft.com/library/jj585016.aspx)
* [Erste Schritte mit RMS SDK 2.1](getting-started-with-ad-rms-2-0.md)
* [Erstellen einer Dienstidentität über ACS](https://msdn.microsoft.com/library/gg185924.aspx)
* [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx)
* [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx)
* [IPC\_PROMPT\_CTX](https://msdn.microsoft.com/library/hh535278.aspx)
* [IPC\_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)
* [IPC\_CREDENTIAL\_SYMMETRIC\_KEY](https://msdn.microsoft.com/library/dn133062.aspx)
* [IpcGetTemplateIssuerList](https://msdn.microsoft.com/library/hh535266.aspx)
* [IpcGetTemplateList](https://msdn.microsoft.com/library/hh535267.aspx)
* [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx)
* [IpcfEncrcyptFile](https://msdn.microsoft.com/library/dn133059.aspx)
* [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx)
* [IpcCreateLicenseFromTemplateID](https://msdn.microsoft.com/library/hh535257.aspx)
