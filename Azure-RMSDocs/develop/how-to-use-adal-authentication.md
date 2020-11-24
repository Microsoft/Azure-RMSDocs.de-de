---
title: ADAL-Authentifizierung für Ihre RMS-fähige Anwendung | Azure RMS
description: Weitere Informationen finden Sie unter Authentifizieren Ihrer APP mit Azure RMS mithilfe Azure Active Directory Authentifizierungs Bibliothek (Adal).
keywords: Authentifizierung, RMS, ADAL
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: a7cf207b0976db31ffa4df83d20e172876c7ee88
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568315"
---
# <a name="how-to-use-adal-authentication"></a>Exemplarische Vorgehensweise: Verwenden der ADAL-Authentifizierung

Authentifizierung mit Azure RMS für Ihre App mit der Azure Active Directory Authentication Library (ADAL).

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

Fügen Sie einen Aufruf von [IpcSetGlobalProperty](/previous-versions/windows/desktop/msipc/ipcsetglobalproperty) direkt nach dem Aufrufen von [IpcInitialize](/previous-versions/windows/desktop/msipc/ipcinitialize) hinzu, um den RMS-Client zu konfigurieren. Verwenden Sie den folgenden Codeausschnitt als Beispiel.

```cpp
IpcInitialize();

IPC_AAD_APPLICATION_ID applicationId = { 0 };
applicationId.cbSize = sizeof(IPC_AAD_APPLICATION_ID);
applicationId.wszClientId = L"GUID-provided-by-AAD-for-your-app-(no-brackets)";
applicationId.wszRedirectUri = L"RedirectionUriWeProvidedAADForOurApp://authorize";
HRESULT hr = IpcSetGlobalProperty(IPC_EI_APPLICATION_ID, &applicationId);
if (FAILED(hr)) {
  //Handle the error
}
```

## <a name="external-authentication"></a>Externe Authentifizierung

Verwenden Sie diesen Code als Beispiel für die Verwaltung Ihrer eigenen Authentifizierungstoken.

```cpp
extern HRESULT GetADALToken(LPVOID pContext, const IPC_NAME_VALUE_LIST& Parameters, __out wstring wstrToken) throw();

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
```

## <a name="related-topics"></a>Verwandte Themen

- [Datentypen](/previous-versions/windows/desktop/msipc/microsoft-information-protection-and-control-client-data-types)
- [Umgebungseigenschaften](/previous-versions/windows/desktop/msipc/environment-properties)
- [IpcCreateOAuth2Token](/previous-versions/windows/desktop/msipc/ipccreateoauth2token)
- [IpcGetKey](/previous-versions/windows/desktop/msipc/ipcgetkey)
- [IpcInitialize](/previous-versions/windows/desktop/msipc/ipcinitialize)
- [IPC_CREDENTIAL](/previous-versions/windows/desktop/msipc/ipc-credential)
- [IPC_NAME_VALUE_LIST](/previous-versions/windows/desktop/msipc/ipc-name-value-list)
- [IPC_OAUTH2_CALLBACK_INFO](/previous-versions/windows/desktop/msipc/ipc-oath2-callback-info)
- [IPC_PROMPT_CTX](/previous-versions/windows/desktop/msipc/ipc-prompt-ctx)
- [IPC_AAD_APPLICATION_ID](/previous-versions/windows/desktop/msipc/ipc-aad-application-id)