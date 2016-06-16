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

# Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung

Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory-Authentifizierungsbibliothek (ADAL).

Durch das Aktualisieren der Anwendung zur Verwendung der ADAL-Authentifizierung anstatt des Microsoft Online-Anmelde-Assistenten haben Sie und Ihre Kunden folgende Möglichkeiten:

- Nutzen der mehrstufigen Authentifizierung
- Installieren des RMS-Client 2.1 ohne Administratorrechte auf dem Computer
- Zertifizieren Ihrer Anwendung für Windows 10

## Zwei Ansätze zur Authentifizierung

Dieses Thema enthält zwei Ansätze zur Authentifizierung mit entsprechenden Codebeispielen.

- **Interne Authentifizierung** – vom RMS SDK verwaltete OAuth-Authentifizierung.

  Verwenden Sie diesen Ansatz, falls Sie möchten, dass der RMS-Client eine ADAL-Authentifizierungsaufforderung anzeigt, wenn eine Authentifizierung erforderlich ist. Weitere Informationen zum Konfigurieren Ihrer Anwendung finden Sie im Abschnitt „Interne Authentifizierung“.

  >AZURE.NOTE Wenn die Anwendung derzeit das AD RMS SDK 2.1 mit dem Anmelde-Assistenten verwendet, empfiehlt es sich, die interne Authentifizierungsmethode als Migrationspfad für die Anwendung zu verwenden.

- **Externe Authentifizierung** – von Ihrer Anwendung verwaltete OAuth-Authentifizierung.

  Verwenden Sie diesen Ansatz, wenn Sie möchten, dass Ihre Anwendung ihre eigene OAuth-Authentifizierung verwaltet. Bei diesem Ansatz führt der RMS-Client einen anwendungsdefinierten Rückruf aus, wenn eine Authentifizierung erforderlich ist. Ein ausführliches Beispiel finden Sie unter „Externe Authentifizierung“ am Ende dieses Themas.

  >AZURE.NOTE Die externe Authentifizierung impliziert nicht die Fähigkeit, Benutzer zu ändern. Der RMS-Client verwendet immer den Standardbenutzer für einen bestimmten RMS-Mandanten.

## Interne Authentifizierung

1. Führen Sie die Azure-Konfigurationsschritte in [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md) aus, und wechseln Sie anschließend zurück zum folgenden App-Initialisierungsschritt.
2. Sie können Ihre Anwendung nun konfigurieren, damit sie die vom RMS SDK 2.1 bereitgestellte interne ADAL-Authentifizierung verwendet.

Fügen Sie einen Aufruf von [IpcSetGlobalProperty](/rights-management/sdk/2.1/api/win/functions#msipc_ipcsetglobalproperty) direkt nach dem Aufrufen von [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize) hinzu, um den RMS-Client zu konfigurieren. Verwenden Sie den folgenden Codeausschnitt als Beispiel.

      C++
      IpcInitialize();

      IPC_AAD_APPLICATION_ID applicationId = { 0 };
      applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);
      applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";
      applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";
      HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &applicationId);
      if (FAILED(hr)) {
        //Handle the error
      }

## Externe Authentifizierung

Verwenden Sie diesen Code als Beispiel für die Verwaltung Ihrer eigenen Authentifizierungstoken.
C++ extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST& Parameters, __out wstring wstrToken) throw();

      HRESULT GetLicenseKey(PCIPC_BUFFER pvLicense, __in LPVOID pContextForAdal, __out IPC_KEY_HANDLE &hKey)
      {
          IPC_OAUTH2_CALLBACK pfGetADALToken =
          [](LPVOID pvContext, PIPC_NAME_VALUE_LIST pParameters, IPC_AUTH_TOKEN_HANDLE* phAuthToken) -> HRESULT
          {
              wstring wstrToken;
              HRESULT hr = GetADALToken(pvContext, *pParameters, wstrToken);
              return SUCCEEDED(hr) ? IpcCreateOAuth2Token(wstrToken.c_str(), OUT phAuthToken) : hr;
          };

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
          credentialContext.pcOAuth2 = &callbackCredentialContext;

          IPC_PROMPT_CTX promptContext =
          {
              sizeof(IPC_PROMPT_CTX),
              NULL,
              IPC_PROMPT_FLAG_SILENT | IPC_PROMPT_FLAG_HAS_USER_CONSENT,
              NULL,
              &credentialContext
          };

          hKey = 0L;
          return IpcGetKey(pvLicense, 0, &promptContext, NULL, &hKey);
      }

## Verwandte Themen

* [Datentypen](/rights-management/sdk/2.1/api/win/datatypes)
* [Umgebungseigenschaften](/rights-management/sdk/2.1/api/win/environmentproperties)
* [IpcCreateOAuth2Token](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreateoauth2token)
* [IpcGetKey](/rights-management/sdk/2.1/api/win/functions#msipc_ipcgetkey)
* [IpcInitialize](/rights-management/sdk/2.1/api/win/functions#msipc_ipcinitialize)
* [IPC_CREDENTIAL](/rights-management/sdk/2.1/api/win/IPC_CREDENTIAL)
* [IPC_NAME_VALUE_LIST](/rights-management/sdk/2.1/api/win/IPC_NAME_VALUE_LIST)
* [IPC_OAUTH2_CALLBACK_INFO](/rights-management/sdk/2.1/api/win/IIPC_OAUTH2_CALLBACK_INFO)
* [IPC_PROMPT_CTX](/rights-management/sdk/2.1/api/win/IPC_PROMPT_CTX)
* [IPC_AAD_APPLICATION_ID](/rights-management/sdk/2.1/api/win/IIPC_AAD_APPLICATION_ID)


<!--HONumber=Jun16_HO2-->


