---
title: "ADAL-Authentifizierung für Ihre RMS-fähige Anwendung | Azure RMS"
description: "Skizziert den Prozess für die Authentifizierung mit ADAL"
keywords: Authentifizierung, RMS, ADAL
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 0e138ec62a16b52fd5657037988d8a9b8daa754f


---

# <a name="how-to-use-adal-authentication"></a>Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung

Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory-Authentifizierungsbibliothek (ADAL).

Durch das Aktualisieren der Anwendung zur Verwendung der ADAL-Authentifizierung anstatt des Microsoft Online-Anmelde-Assistenten haben Sie und Ihre Kunden folgende Möglichkeiten:

- Nutzen der mehrstufigen Authentifizierung
- Installieren des RMS-Client 2.1 ohne Administratorrechte auf dem Computer
- Zertifizieren Ihrer Anwendung für Windows 10

## <a name="two-approaches-to-authentication"></a>Zwei Ansätze zur Authentifizierung

Dieses Thema enthält zwei Ansätze zur Authentifizierung mit entsprechenden Codebeispielen.

- **Interne Authentifizierung** – vom RMS SDK verwaltete OAuth-Authentifizierung.

  Verwenden Sie diesen Ansatz, falls Sie möchten, dass der RMS-Client eine ADAL-Authentifizierungsaufforderung anzeigt, wenn eine Authentifizierung erforderlich ist. Weitere Informationen zum Konfigurieren Ihrer Anwendung finden Sie im Abschnitt „Interne Authentifizierung“.

  > [!Note]
  > Es wird empfohlen, die interne Authentifizierungsmethode als Migrationspfad für Ihre Anwendung zu verwenden, wenn diese derzeit AD RMS SDK 2.1 mit dem Anmelde-Assistenten verwendet.

- **Externe Authentifizierung** – von Ihrer Anwendung verwaltete OAuth-Authentifizierung.

  Verwenden Sie diesen Ansatz, wenn Sie möchten, dass Ihre Anwendung ihre eigene OAuth-Authentifizierung verwaltet. Bei diesem Ansatz führt der RMS-Client einen anwendungsdefinierten Rückruf aus, wenn eine Authentifizierung erforderlich ist. Ein ausführliches Beispiel finden Sie unter „Externe Authentifizierung“ am Ende dieses Themas.

  > [!Note]
  > Die externe Authentifizierung impliziert nicht die Fähigkeit, Benutzer zu ändern. Der RMS-Client verwendet immer den Standardbenutzer für einen bestimmten RMS-Mandanten.

## <a name="internal-authentication"></a>Interne Authentifizierung

1. Führen Sie die Azure-Konfigurationsschritte in [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md) aus, und wechseln Sie anschließend zurück zum folgenden App-Initialisierungsschritt.
2. Sie können Ihre Anwendung nun konfigurieren, damit sie die vom RMS SDK 2.1 bereitgestellte interne ADAL-Authentifizierung verwendet.

Fügen Sie einen Aufruf von [IpcSetGlobalProperty](https://msdn.microsoft.com/library/hh535270.aspx) direkt nach dem Aufrufen von [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx) hinzu, um den RMS-Client zu konfigurieren. Verwenden Sie den folgenden Codeausschnitt als Beispiel.

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

## <a name="external-authentication"></a>Externe Authentifizierung

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

## <a name="related-topics"></a>Verwandte Themen

- [Data Types (Datentypen)](https://msdn.microsoft.com/library/hh535288.aspx)
- [Environment properties (Umgebungseigenschaften)](https://msdn.microsoft.com/library/hh535247.aspx)
- [IpcCreateOAuth2Token](https://msdn.microsoft.com/library/mt661866.aspx)
- [IpcGetKey](https://msdn.microsoft.com/library/hh535263.aspx)
- [IpcInitialize](https://msdn.microsoft.com/library/jj127295.aspx)
- [IPC_CREDENTIAL](https://msdn.microsoft.com/library/hh535275.aspx)
- [IPC_NAME_VALUE_LIST](https://msdn.microsoft.com/library/hh535277.aspx)
- [IPC_OAUTH2_CALLBACK_INFO](https://msdn.microsoft.com/library/mt661868.aspx)
- [IPC_PROMPT_CTX](https://msdn.microsoft.com/library/hh535278.aspx)
- [IPC_AAD_APPLICATION_ID](https://msdn.microsoft.com/library/mt661867.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


