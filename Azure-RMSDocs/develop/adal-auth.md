---
# required metadata

title: ADAL-Authentifizierung für Ihre RMS-fähige Anwendung | Azure RMS
description: Skizziert den Prozess für die Authentifizierung mit ADAL
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# ADAL-Authentifizierung für Ihre RMS-fähige Anwendung

Die Authentifizierung mit Azure RMS für Ihre App mithilfe von Azure ADAL ist nun Teil des RMS-Clients 2.1.

Durch das Aktualisieren der Anwendung zur Verwendung der ADAL-Authentifizierung anstatt des Microsoft Online-Anmelde-Assistenten haben Sie und Ihre Kunden folgende Möglichkeiten:

- Nutzen der mehrstufigen Authentifizierung
- Installieren des RMS-Client 2.1 ohne Administratorrechte auf dem Computer
- Zertifizieren Ihrer Anwendung für Windows 10

## Zwei Ansätze zur Authentifizierung

Dieses Thema enthält zwei Ansätze zur Authentifizierung mit entsprechenden Codebeispielen.

- **Interne Authentifizierung** – vom RMS SDK verwaltete OAuth-Authentifizierung. Verwenden Sie diesen Ansatz, falls Sie möchten, dass der RMS-Client eine ADAL-Authentifizierungsaufforderung anzeigt, wenn eine Authentifizierung erforderlich ist. Weitere Informationen zum Konfigurieren Ihrer Anwendung finden Sie im Abschnitt „Interne Authentifizierung“.

> [!NOTE] Es wird empfohlen, die interne Authentifizierungsmethode als Migrationspfad für Ihre Anwendung zu verwenden, wenn diese derzeit AD RMS SDK 2.1 mit dem Anmelde-Assistenten verwendet.

- **Externe Authentifizierung** – von Ihrer Anwendung verwaltete OAuth-Authentifizierung. Verwenden Sie diesen Ansatz, wenn Sie möchten, dass Ihre Anwendung ihre eigene OAuth-Authentifizierung verwaltet. Bei diesem Ansatz führt der RMS-Client einen anwendungsdefinierten Rückruf aus, wenn eine Authentifizierung erforderlich ist. Ein ausführliches Beispiel finden Sie unter „Externe Authentifizierung“ am Ende dieses Themas.

> [!NOTE] Die externe Authentifizierung impliziert nicht die Fähigkeit, Benutzer zu ändern. Der RMS-Client verwendet immer den Standardbenutzer für einen bestimmten RMS-Mandanten.

### Interne Authentifizierung

Folgendes wird benötigt:

- Ein [Abonnement für Microsoft Azure](https://azure.microsoft.com/en-us/) (eine kostenlose Testversion ist ausreichend):
- Ein Abonnement für Microsoft Azure Rights Management (ein kostenloses [RMS für Einzelpersonen](https://technet.microsoft.com/en-us/library/dn592127.aspx)-Konto ist ausreichend).

> [!NOTE] Fragen Sie Ihren IT-Administrator, ob Sie über ein Abonnement für Microsoft Azure Rights Management verfügen oder nicht, und lassen Sie Ihren IT-Administrator die nachstehenden Schritte ausführen. Wenn Ihre Organisation nicht über ein Abonnement verfügt, sollte Ihr IT-Administrator eines erstellen. Ihr IT-Administrator sollte das Abonnement außerdem mit einem Geschäfts-, Schul- oder Unikonto anstelle eines Microsoft-Kontos (z.B. Hotmail) erstellen.

Nach der Registrierung für Microsoft Azure:

- Melden Sie sich beim [Azure-Verwaltungsportal](https://manage.windowsazure.com) für Ihre Organisation über ein Konto mit Administratorrechten an.

![Azure-Anmeldung](../media/AzurePortalLogin.png)

- Navigieren Sie nach unten zur **Active Directory**-Anwendung auf der linken Seite des Portals.

![Auswählen von „Active Directory“](../media/AzureADPick.png)

- Wenn Sie noch kein Verzeichnis erstellt haben, wählen Sie die Schaltfläche **Neu** aus, die sich in der unteren linken Ecke des Portals befindet.

![Auswählen von NEU](../media/AzureNewBtn.png)

- Wählen Sie die Registerkarte **Rights Management** aus, und stellen Sie sicher, dass der **Rights Management-Status** entweder **Aktiv**, **Unbekannt** oder **Nicht autorisiert** ist. Wenn der Status **Inaktiv** ist, wählen Sie die Schaltfläche **Aktivieren** im unteren mittleren Bereich des Portals aus, und bestätigen Sie Ihre Auswahl.

![Auswählen von AKTIVIEREN](../media/RMTab.png)

- Erstellen Sie nun eine neue *Native Anwendung* in Ihrem Verzeichnis, indem Sie Ihr Verzeichnis und „Anwendungen“ auswählen.

![Auswählen von ANWENDUNGEN](../media/CreateNativeApp.png)

- Wählen Sie dann die Schaltfläche **Hinzufügen** aus, die sich im unteren, mittleren Bereich des Portals befindet.

![Auswählen von HINZUFÜGEN](../media/AddAppBtn.png)

- Wählen Sie an der Eingabeaufforderung **Eine von meinem Unternehmen entwickelte Anwendung hinzufügen** aus.

![Auswählen von „Eine von meinem Unternehmen entwickelte Anwendung hinzufügen“](../media/AddAnAppPick.png)

- Benennen Sie Ihre Anwendung, indem Sie **NATIVE CLIENTANWENDUNG** und die Schaltfläche **Weiter** auswählen.

![Benennen Ihrer App](../media/TellUsInput.png)

- Fügen Sie einen Umleitungs-URI hinzu, und wählen Sie „Weiter“ aus. Der Umleitungs-URI muss ein gültiger URI und in Ihrem Verzeichnis einmalig sein. Beispielsweise könnten Sie etwas wie `com.mycompany.myapplication://authorize` verwenden.

![Hinzufügen eines Umleitungs-URI](../media/RedirectURI.png)

- Wählen Sie Ihre Anwendung im Verzeichnis und anschließend **KONFIGURIEREN** aus.

![Auswählen von KONFIGURIEREN](../media/ConfigYourApp.png)

>[!NOTE] Kopieren Sie die **CLIENT-ID** und den **UMLEITUNGS-URI**, und speichern Sie diese für die spätere Verwendung bei der Konfiguration des RMS-Clients.

- Navigieren Sie zum unteren Rand Ihrer Anwendungseinstellungen, und wählen Sie unter **Berechtigungen für andere Anwendungen** die Schaltfläche **Anwendung hinzufügen** aus.

![Auswählen von „Anwendung hinzufügen“](../media/PermissionsToOtherBtn.png)

- Geben Sie nun die GUID `00000012-0000-0000-c000-000000000000` in das Eingabefeld **Beginnend mit** ein, und klicken Sie auf das Häkchen.

![Hinzufügen der GUID](../media/AddGUID.png)

- Wählen Sie das Pluszeichen (+) neben **Microsoft Rights Management** aus.

![Auswählen des Pluszeichens (+)](../media/ChoosePlusBtn.png)

- Klicken Sie nun auf das Häkchen in der unteren linken Ecke des Dialogfelds.

![Klicken des Häkchens](../media/ChooseCheck.png)

- Nun können Sie Ihrer Anwendung für Azure RMS eine Abhängigkeit hinzufügen. Wählen Sie zum Hinzufügen der Abhängigkeit den neuen Eintrag **Microsoft Rights Management Services** unter **Berechtigungen für andere Anwendungen** aus, und aktivieren Sie das Kontrollkästchen **Create and access protected content for users** (Geschützten Inhalt für Benutzer erstellen und darauf zugreifen) in der Dropdownliste bei **Delegierte Berechtigungen:**.

![Einrichten von Berechtigungen](../media/AddDependency.png)

- Speichern Sie Ihre Anwendung, damit die Änderungen beibehalten werden, indem Sie das Symbol **SPEICHERN** im unteren, mittleren Bereich des Portals auswählen.

![Auswählen von SPEICHERN](../media/SaveApplication.png)

- Sie können Ihre Anwendung nun konfigurieren, damit sie die vom RMS SDK 2.1 bereitgestellte interne ADAL-Authentifizierung verwendet. Fügen Sie einen Aufruf von [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/IpcSetGlobalProperty) direkt nach dem Aufrufen von [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize) hinzu, um den RMS-Client zu konfigurieren. Verwenden Sie den folgenden Codeausschnitt als Beispiel.


    IpcInitialize();

    IPC_AAD_APPLICATION_ID applicationId = { 0 };   applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);   applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";   applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";

    HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &amp;applicationId);

    if (FAILED(hr)) {    //Handle the error   }

### Externe Authentifizierung

- Verwenden Sie diesen Code als Beispiel für die Verwaltung Ihrer eigenen Authentifizierungstoken.


    extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST&amp; Parameters, __out wstring wstrToken) throw();

    HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &amp;hKey)   {     IPC_OAUTH2_CALLBACK pfGetADALToken =         [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -&gt; HRESULT     {         wstring wstrToken;         HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken);         return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr;     };

      IPC_OAUTH2_CALLBACK_INFO callbackCredentialContext =
      {
          sizeof(IPC_OAUTH2_CALLBACK_INFO),
          pfGetADALToken,
          pContextForAdal
      };

      IPC_CREDENTIAL credentialContext =
      {
          IPC_CREDENTIAL_TYPE_OAUTH2,
          NULL
      };
      credentialContext.pcOAuth2 = &amp;callbackCredentialContext;

      IPC_PROMPT_CTX promptContext =
      {
        sizeof(IPC_PROMPT_CTX),
        NULL,
        IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
        NULL,
        &amp;credentialContext
      };

      hKey = 0L;
      return IpcGetKey(pvLicense, 0, &amp;promptContext, NULL, &amp;hKey);
  }

### Verwandte Themen
- [Datentypen](/rights-management/sdk/2.1/api/win/Data%20types)
- [Umgebungseigenschaften](/rights-management/sdk/2.1/api/win/Environment%20properties)
- [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/IpcCreateOAuth2Token)
- [IpcGetKey](/rights-management/sdk/2.1/api/win/IpcGetKey)
- [IpcInitialize](/rights-management/sdk/2.1/api/win/IpcInitialize)
- [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC\_CREDENTIAL)
- [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC\_NAME\_VALUE\_LIST)
- [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/IPC\_OAUTH2\_CALLBACK\_INFO)
- [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC\_PROMPT\_CTX)
- [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/IPC\_AAD\_APPLICATION\_ID)


<!--HONumber=May16_HO2-->


