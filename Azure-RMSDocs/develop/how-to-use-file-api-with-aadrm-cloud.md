---
title: 'Gewusst wie: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung | Azure RMS'
description: In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: EA1457D1-282F-4CF3-A23C-46793D2C2F32
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: a760f59effa09cf55f7618e6ab965c5e95f015d3
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568303"
---
# <a name="how-to-enable-your-service-application-to-work-with-cloud-based-rms"></a>Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung

[!INCLUDE [deprecation notice](../includes/deprecation-warning.md)]

In diesem Thema werden die Schritte zum Einrichten Ihrer Dienstanwendung zur Verwendung von Azure Rights Management erläutert. Weitere Informationen finden Sie unter [Erste Schritte mit Azure Rights Management](../requirements.md).

**Wichtig**  
Sie müssen eigene Mandanten erstellen, um die Rights Management Services SDK 2.1-Dienstanwendung mit Azure RMS zu verwenden. Weitere Informationen finden Sie [unter Azure RMS Requirements: Cloud-Abonnements, die Azure RMS unterstützen](../requirements.md) .

## <a name="prerequisites"></a>Voraussetzungen

-   RMS SDK 2.1 muss installiert und konfiguriert sein. Weitere Informationen finden Sie unter [Erste Schritte mit RMS SDK 2.1](getting-started-with-ad-rms-2-0.md).
-   [Erstellen Sie eine Dienstidentität über ACS](/previous-versions/azure/azure-services/gg185924(v=azure.100)) mithilfe der symmetrischen Schlüsseloption oder auf andere Weise, und zeichnen Sie die Schlüsselinformation dieses Prozesses auf.

## <a name="connecting-to-the-azure-rights-management-service"></a>Verbinden mit dem Azure-Rechteverwaltungsdienst

- Rufen Sie [IpcInitialize](/previous-versions/windows/desktop/msipc/ipcinitialize) auf.
- Legen Sie [IpcSetGlobalProperty](/previous-versions/windows/desktop/msipc/ipcsetglobalproperty) fest.

  ```cpp
  int mode = IPC_API_MODE_SERVER;
  IpcSetGlobalProperty(IPC_EI_API_MODE, &(mode));
  ```

  **Hinweis**  Weitere Informationen finden Sie unter [Festlegen des API-Sicherheitsmodus](setting-the-api-security-mode-api-mode.md).


-   Die folgenden Schritte sind das Setup für das Erstellen einer Instanz einer [IPC \_ prompt \_ ctx](/previous-versions/windows/desktop/msipc/ipc-prompt-ctx) -Struktur mit dem Element *pccredential*  ([IPC \_ Credential](/previous-versions/windows/desktop/msipc/ipc-credential)), das mit Verbindungsinformationen aus dem Azure Rights Management-Dienst aufgefüllt wurde.
-   Verwenden Sie die Informationen aus der Erstellung der Dienst Identität ihrer symmetrischen Schlüssel (siehe die weiter oben aufgeführten Voraussetzungen), um die Parameter *wszserviceprincipal*, *wszbpostenantid* und *cbkey* festzulegen, wenn Sie eine Instanz einer [IPC \_ Credential \_ symmetrischen \_ Key](/previous-versions/windows/desktop/msipc/ipc-credential-symmetric-key) -Struktur erstellen.

**Hinweis** – Aufgrund einer Bedingung unseres Ermittlungsdiensts sind Anmeldeinformationen für symmetrische Schlüssel von anderen Regionen nur zulässig, wenn Sie sich in Nordamerika befinden. Aus diesem Grund müssen Sie Ihre Mandanten-URLs direkt eingeben. Verwenden Sie hierfür den Parameter *pConnectionInfo* mit dem Typ [IPC\_CONNECTION\_INFO](/previous-versions/windows/desktop/msipc/ipc-connection-info) in den Funktionen [IpcGetTemplateList](/previous-versions/windows/desktop/msipc/ipcgettemplatelist) oder [IpcGetTemplateIssuerList](/previous-versions/windows/desktop/msipc/ipcgettemplateissuerlist).

## <a name="generate-a-symmetric-key-and-collect-the-needed-information"></a>Generieren Sie einen symmetrischen Schlüssel, und sammeln Sie die benötigten Informationen.

### <a name="instructions-to-generate-a-symmetric-key"></a>Anweisungen zum Generieren eines symmetrischen Schlüssels

-   Installieren Sie den [Microsoft Online-Anmeldeassistenten](https://go.microsoft.com/fwlink/p/?LinkID=286152).
-   Installieren Sie das [Azure AD PowerShell-Modul](https://bposast.vo.msecnd.net/MSOPMW/8073.4/amd64/AdministrationConfig-en.msi).

**Hinweis** – Sie muss ein Mandantenadministrator sein, um die Powershell-Cmdlets verwenden zu können.

- Starten Sie PowerShell, und führen Sie die folgenden Befehle zum Generieren eines Schlüssels aus.

    `Import-Module MSOnline`

    `Connect-MsolService` (Geben Sie Ihre Administrator-Anmeldeinformationen ein.)

    `New-MsolServicePrincipal` (Geben Sie einen Anzeigenamen ein.)

- Nachdem der symmetrische Schlüssel generiert wurde, werden Informationen zu dem Schlüssel einschließlich des Schlüssels selbst und *AppPrincipalId* ausgegeben.

  ```output
  The following symmetric key was created as one was not supplied
  ZYbF/lTtwE28qplQofCpi2syWd11D83+A3DRlb2Jnv8=

  DisplayName : RMSTestApp
  ServicePrincipalNames : {7d9c1f38-600c-4b4d-8249-22427f016963}
  ObjectId : 0ee53770-ec86-409e-8939-6d8239880518
  AppPrincipalId : 7d9c1f38-600c-4b4d-8249-22427f016963
  ```


### <a name="instructions-to-find-out-tenantbposid-and-urls"></a>Anweisungen zum Ermitteln von **TenantBposId** und **Urls**

-   Installieren Sie das [Azure RMS PowerShell-Modul](../install-powershell.md).
-   Starten Sie Powershell, und führen Sie die folgenden Befehle aus, um die RMS-Konfiguration des Mandanten abzurufen.

    `Import-Module AIPService`

    `Connect-AipService` (Geben Sie Ihre Administrator-Anmeldeinformationen ein.)

    `Get-AipServiceConfiguration`


- Erstellen Sie eine Instanz eines  [ \_ symmetrischen IPC Credential- \_ \_ Schlüssels](/previous-versions/windows/desktop/msipc/ipc-credential-symmetric-key) , und legen Sie einige Member fest.

  ```cpp
  // Create a key structure.
  IPC_CREDENTIAL_SYMMETRIC_KEY symKey = {0};

  // Set each member with information from service creation.
  symKey.wszBase64Key = "your service principal key";
  symKey.wszAppPrincipalId = "your app principal identifier";
  symKey.wszBposTenantId = "your tenant identifier";
  ```

Weitere Informationen finden Sie unter [IPC \_ Credential \_ Symmetric \_ Key](/previous-versions/windows/desktop/msipc/ipc-credential-symmetric-key).

- Erstellen Sie eine Instanz einer [IPC \_ Credential](/previous-versions/windows/desktop/msipc/ipc-credential) -Struktur, die Ihre [IPC \_ Credential \_ Symmetric \_ Key](/previous-versions/windows/desktop/msipc/ipc-credential-symmetric-key) -Instanz enthält.

  **Hinweis**   -Die *ConnectionInfo* -Member werden mit URLs aus dem vorherigen-Befehl festgelegt `Get-AipServiceConfiguration` und hier mit diesen Feldnamen angegeben.

  ```cpp
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
  ```

### <a name="identify-a-template-and-then-encrypt"></a>Identifizieren einer Vorlage und Verschlüsselung

- Wählen Sie eine Vorlage für die Verschlüsselung aus.
    Nennen Sie [ipcgettemplatelist](/previous-versions/windows/desktop/msipc/ipcgettemplatelist) , und übergeben Sie dieselbe Instanz von [IPC \_ prompt \_ ctx](/previous-versions/windows/desktop/msipc/ipc-prompt-ctx).

  ```cpp
  PCIPC_TIL pTemplates = NULL;
  IPC_TEMPLATE_ISSUER templateIssuer = (pTemplateIssuerList->aTi)[0];

  hr = IpcGetTemplateList(&(templateIssuer.connectionInfo),
         IPC_GTL_FLAG_FORCE_DOWNLOAD,
         0,
         &promptCtx,
         NULL,
         &pTemplates);
  ```

- Mit der Vorlage von weiter oben in diesem Thema, nennen Sie [ipcfencr. tfile](/previous-versions/windows/desktop/msipc/ipcfencryptfile), und übergeben Sie dieselbe Instanz von [IPC \_ prompt \_ ctx](/previous-versions/windows/desktop/msipc/ipc-prompt-ctx).

  Beispiel für die Verwendung von [IpcfEncrcyptFile](/previous-versions/windows/desktop/msipc/ipcfencryptfile):

  ```cpp
  LPCWSTR wszContentTemplateId = pTemplates->aTi[0].wszID;
  hr = IpcfEncryptFile(wszInputFilePath,
         wszContentTemplateId,
         IPCF_EF_TEMPLATE_ID,
         IPC_EF_FLAG_KEY_NO_PERSIST,
         &promptCtx,
         NULL,
         &wszOutputFilePath);
  ```

  Beispiel für die Verwendung von [IpcfDecryptFile](/previous-versions/windows/desktop/msipc/ipcfdecryptfile):

  ```cpp
  hr = IpcfDecryptFile(wszInputFilePath,
         IPCF_DF_FLAG_DEFAULT,
         &promptCtx,
         NULL,
         &wszOutputFilePath);
  ```

Sie haben jetzt die erforderlichen Schritte zum Aktivieren der Anwendung für die Verwendung von Azure Rights Management abgeschlossen.

## <a name="related-topics"></a>Verwandte Themen

* [Erste Schritte mit Azure Rights Management](../requirements.md)
* [Erste Schritte mit RMS SDK 2.1](getting-started-with-ad-rms-2-0.md)
* [Erstellen einer Dienstidentität über ACS](/previous-versions/azure/azure-services/gg185924(v=azure.100))
* [IpcSetGlobalProperty](/previous-versions/windows/desktop/msipc/ipcsetglobalproperty)
* [IpcInitialize](/previous-versions/windows/desktop/msipc/ipcinitialize)
* [IPC \_ prompt \_ ctx](/previous-versions/windows/desktop/msipc/ipc-prompt-ctx)
* [IPC-Anmelde Informationen \_](/previous-versions/windows/desktop/msipc/ipc-credential)
* [IPC \_ Credential \_ Symmetric \_ Key](/previous-versions/windows/desktop/msipc/ipc-credential-symmetric-key)
* [IpcGetTemplateIssuerList](/previous-versions/windows/desktop/msipc/ipcgettemplateissuerlist)
* [IpcGetTemplateList](/previous-versions/windows/desktop/msipc/ipcgettemplatelist)
* [IpcfDecryptFile](/previous-versions/windows/desktop/msipc/ipcfdecryptfile)
* [IpcfEncrcyptFile](/previous-versions/windows/desktop/msipc/ipcfencryptfile)
* [IpcCreateLicenseFromScratch](/previous-versions/windows/desktop/msipc/ipccreatelicensefromscratch)
* [IpcCreateLicenseFromTemplateID](/previous-versions/windows/desktop/msipc/ipccreatelicensefromtemplateid)