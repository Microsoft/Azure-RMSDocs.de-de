---
title: "Vorgehensweise: Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS | Azure RMS"
description: "Beschreibt die Grundlagen der Benutzerauthentifizierung für Ihre RMS-fähige Anwendung."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 0c06a498c62b61c106572e049f8ef40fdb07485f
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-register-and-rms-enable-your-app-with-azure-ad"></a>Vorgehensweise: Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS

In diesem Thema werden die Grundlagen der App-Registrierung und RMS-Aktivierung über das Azure-Portal vermittelt. Anschließend wird die Benutzerauthentifizierung mit der Azure Active Directory Authentication Library (ADAL) erläutert.

## <a name="what-is-user-authentication"></a>Was ist Benutzerauthentifizierung?
Benutzerauthentifizierung ist ein grundlegender Schritt beim Aufbau der Kommunikation zwischen der Geräte-App und der RMS-Infrastruktur. In diesem Authentifizierungsprozess wird das OAuth 2.0-Standardprotokoll verwendet, für das wichtige Angaben über den aktuellen Benutzer und die zugehörige Authentifizierungsanforderung benötigt werden.

## <a name="registration-via-azure-portal"></a>Registrierung über das Azure-Portal
Befolgen Sie zunächst die Anleitungen unter [Konfigurieren von Azure RMS für die ADAL-Authentifizierung](adal-auth.md), um die Registrierung Ihrer App über das Azure-Portal zu konfigurieren. Kopieren und speichern Sie die **Client-ID** und den **Umleitungs-URI** aus diesem Prozess zur späteren Verwendung.

## <a name="complete-your-rights-managagment-license-agreement-rmla"></a>Abschließen Ihres Rights Management-Lizenzvertrags (Rights Management License Agreement; RMLA)
Bevor Sie Ihre Anwendung bereitstellen können, müssen Sie einen RMLA mit dem Microsoft Rights Management-Team abschließen. Ausführliche Informationen finden Sie im ersten Abschnitt des Themas [Bereitstellen in der Produktion – Anfordern eines Produktionslizenzvertrags](deploying-your-application.md).

## <a name="implement-user-authentication-for-your-app"></a>Implementieren der Benutzerauthentifizierung für Ihre App
Jede RMS-API verfügt über einen Rückruf, der implementiert werden muss, um eine Authentifizierung des Benutzers zu ermöglichen. Das RMS SDK 4.2 verwendet Ihre Implementierung des Rückrufs, wenn Sie kein Zugriffstoken angeben, wenn das Zugriffstoken aktualisiert werden muss oder wenn das Zugriffstoken abgelaufen ist.

- Android: die Schnittstellen [AuthenticationRequestCallback](https://msdn.microsoft.com/library/dn758255.aspx) und [AuthenticationCompletionCallback](https://msdn.microsoft.com/library/dn758250.aspx).
- iOS/OS X: das Protokoll [MSAuthenticationCallback](https://msdn.microsoft.com/library/dn758312.aspx).
-  Windows Phone/Windows RT: die Schnittstelle [IAuthenticationCallback](https://msdn.microsoft.com/library/microsoft.rightsmanagement.iauthenticationcallback.aspx).
- Linux: die Schnittstelle [IAuthenticationCallback](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html).

### <a name="what-library-to-use-for-authentication"></a>Welche Bibliothek zur Authentifizierung verwendet werden soll
Zur Implementierung eines eigenen Authentifizierungsrückrufs müssen Sie eine entsprechende Bibliothek herunterladen und Ihre Entwicklungsumgebung für deren Verwendung konfigurieren. Auf GitHub finden Sie die ADAL-Bibliotheken für diese Plattformen.

Jede der folgenden Ressourcen enthält Anleitungen zum Einrichten Ihrer Umgebung und Verwenden der Bibliothek.

-   [Windows Azure Active Directory Authentication Library (ADAL) for iOS (Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für iOS)](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Windows Azure Active Directory Authentication Library (ADAL) for Mac (Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für Mac)](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Windows Azure Active Directory Authentication Library (ADAL) for Android (Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für Android)](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Windows Azure Active Directory Authentication Library (ADAL) for dotnet (Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für dotnet)](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   Beim Linux-SDK befindet sich die ADAL-Bibliothek im SDK-Quellcodepaket, das über [Github](https://github.com/AzureAD/rms-sdk-for-cpp) verfügbar ist.

>[!NOTE]  
> Es wird empfohlen, dass Sie selbst dann eine ADAL verwenden, wenn Sie andere Authentifizierungsbibliotheken verwenden könnten.

### <a name="authentication-parameters"></a>Authentifizierungsparameter

Die ADAL benötigt verschiedene Angaben, um Benutzer von Azure RMS (oder AD RMS) erfolgreich authentifizieren zu können. Es handelt sich dabei um die OAuth 2.0-Standardparameter, die in der Regel für jede Azure AD-App erforderlich sind. Sie finden die aktuellen Richtlinien für die Verwendung der ADAL in der README-Datei der entsprechenden GitHub-Repositorys, die oben aufgeführt wurden.

- **Autorität** – Die URL des Authentifizierungsendpunkts, in der Regel AAD oder ADFS.
- **Ressource** – URL/URI der Dienstanwendung, auf die Sie zuzugreifen versuchen, in der Regel Azure RMS oder AD RMS.
- **Benutzer-ID** – UPN, in der Regel die E-Mail-Adresse des Benutzers, der auf die Anwendung zugreifen möchte. Dieser Parameter kann leer sein, wenn der Benutzer noch nicht bekannt ist, und er dient außerdem zum Zwischenspeichern von Benutzertoken oder zum Anfordern eines Token aus dem Cache. Dies wird in der Regel auch als *Hinweis* für Benutzereingabeaufforderungen verwendet.
- **Client-ID** – Die ID der Client-App. Dies muss eine gültige ID für Azure AD-Anwendung sein.
Diese stammt aus dem vorherigen Registrierungsschritt, der über das Azure-Portal ausgeführt wurde.
- **Umleitungs-URI** – Stellt der Authentifizierungsbibliothek einen Ziel-URI für den Authentifizierungscode bereit. Für iOS und Android sind spezielle Formate erforderlich. Diese sind in den README-Dateien der entsprechenden GitHub-Repositorys der ADAL beschrieben. Dieser Wert stammt aus dem vorherigen Registrierungsschritt, der über das Azure-Portal ausgeführt wurde.

>[!NOTE]
> Der **Bereich** wird aktuell nicht verwendet, kann aber verwendet werden und ist daher für die zukünftige Verwendung reserviert.

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

>[!NOTE] 
> Bei den Azure RMS- und Azure AD-Workflows tritt wahrscheinlich ein Fehler auf, und diese Workflows werden von Microsoft nicht unterstützt, wenn Ihre App diesen Richtlinien nicht entspricht. Darüber hinaus kann es einen Verstoß gegen die Rights Management License Agreement (RMLA) darstellen, wenn in einer Produktions-App eine ungültige Client-ID verwendet wird.

### <a name="what-should-an-authentication-callback-implementation-look-like"></a>Wie sollte die Implementieren eines Authentifizierungsrückrufs aussehen
**Codebeispiele für die Authentifizierung** –Dieses SDK enthält Beispielcode, der die Verwendung von Authentifizierungsrückrufen veranschaulicht. Der Einfachheit halber werden diese Codebeispiele sowohl hier als auch in jedem der folgenden verknüpften Themen dargestellt.

**Android-Benutzerauthentifizierung** – Weitere Informationen finden Sie unter [Codebeispiele für Android](android-code.md), **Schritt 2** des ersten Szenarios mit dem Titel "Nutzen einer RMS-geschützten Datei".


    class MsipcAuthenticationCallback implements AuthenticationRequestCallback
    {
    ...

    @Override
    public void getToken(Map<String, String> authenticationParametersMap,
                         final AuthenticationCompletionCallback authenticationCompletionCallbackToMsipc)
    {
        String authority = authenticationParametersMap.get("oauth2.authority");
        String resource = authenticationParametersMap.get("oauth2.resource");
        String userId = authenticationParametersMap.get("userId");
        mClientId = “12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”; // get your registered Azure AD application ID here
        mRedirectUri = “urn:ietf:wg:oauth:2.0:oob”;
        final String userHint = (userId == null)? "" : userId;
        AuthenticationContext authenticationContext = App.getInstance().getAuthenticationContext();
        if (authenticationContext == null || !authenticationContext.getAuthority().equalsIgnoreCase(authority))
        {
            try
            {
                authenticationContext = new AuthenticationContext(App.getInstance().getApplicationContext(), authority, …);
                App.getInstance().setAuthenticationContext(authenticationContext);
            }
            catch (NoSuchAlgorithmException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
            catch (NoSuchPaddingException e)
            {
                …
                authenticationCompletionCallbackToMsipc.onFailure();
            }
       }
        App.getInstance().getAuthenticationContext().acquireToken(mParentActivity, resource, mClientId, mRedirectURI, userId, mPromptBehavior,
                       "&USERNAME=" + userHint, new AuthenticationCallback<AuthenticationResult>()
                        {
                            @Override
                            public void onError(Exception exc)
                            {
                                …
                                if (exc instanceof AuthenticationCancelError)
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onCancel();
                                }
                                else
                                {
                                     …
                                    authenticationCompletionCallbackToMsipc.onFailure();
                                }
                            }

                            @Override
                            public void onSuccess(AuthenticationResult result)
                            {
                                …
                                if (result == null || result.getAccessToken() == null
                                        || result.getAccessToken().isEmpty())
                                {
                                     …
                                }
                                else
                                {
                                    // request is successful
                                    …
                                    authenticationCompletionCallbackToMsipc.onSuccess(result.getAccessToken());
                                }
                            }
                        });
                         }


**iOS/OS X-Benutzerauthentifizierung** – Weitere Informationen finden Sie unter [Codebeispiele für iOS/OS X](ios-os-x-code-examples.md), *Schritt 2* des ersten Szenarios mit dem Titel „Nutzen einer RMS-geschützten Datei“.


    // AuthenticationCallback holds the necessary information to retrieve an access token.
    @interface MsipcAuthenticationCallback : NSObject<MSAuthenticationCallback>

    @end

    @implementation MsipcAuthenticationCallback

    - (void)accessTokenWithAuthenticationParameters:
         (MSAuthenticationParameters *)authenticationParameters
                                completionBlock:
         (void(^)(NSString *accessToken, NSError *error))completionBlock
    {
    ADAuthenticationError *error;
    ADAuthenticationContext* context = [ADAuthenticationContext authenticationContextWithAuthority:authenticationParameters.authority error:&error];

    NSString *appClientId = @”12345678-ABCD-ABCD-ABCD-ABCDEFGHIJ”;

    // get your registered Azure AD application ID here

    NSURL *redirectURI = [NSURL URLWithString:@”ms-sample://com.microsoft.sampleapp”];

    // get your <app-scheme>://<bundle-id> here
    // Retrieve token using ADAL
    [context acquireTokenWithResource:authenticationParameters.resource
                             clientId:appClientId
                          redirectUri:redirectURI
                               userId:authenticationParameters.userId
                      completionBlock:^(ADAuthenticationResult *result)
                      {
                          if (result.status != AD_SUCCEEDED)
                          {
                              NSLog(@"Auth Failed");
                              completionBlock(nil, result.error);
                          }
                          else
                          {
                              completionBlock(result.accessToken, result.error);
                          }
                      }

        ];
    }



**Linux-Benutzerauthentifizierung** – Weitere Informationen finden Sie unter [Codebeispiele für Linux](linux-c-code-examples.md).



    // Class Header
    class AuthCallback : public IAuthenticationCallback {
    private:

      std::shared_ptr<rmsauth::FileCache> FileCachePtr;
      std::string clientId_;
      std::string redirectUrl_;

      public:

      AuthCallback(const std::string& clientId,
               const std::string& redirectUrl);
      virtual std::string GetToken(shared_ptr<AuthenticationParameters>& ap) override;
    };

    class ConsentCallback : public IConsentCallback {
      public:

      virtual ConsentList Consents(ConsentList& consents) override;
    };

    // Class Implementation
    AuthCallback::AuthCallback(const string& clientId, const string& redirectUrl)
    : clientId_(clientId), redirectUrl_(redirectUrl) {
      FileCachePtr = std::make_shared<FileCache>();
    }

    string AuthCallback::GetToken(shared_ptr<AuthenticationParameters>& ap)
    {
      string redirect =
      ap->Scope().empty() ? redirectUrl_ : ap->Scope();

      try
      {
        if (redirect.empty()) {
        throw rmscore::exceptions::RMSInvalidArgumentException(
              "redirect Url is empty");
      }

      if (clientId_.empty()) {
      throw rmscore::exceptions::RMSInvalidArgumentException("client Id is empty");
      }

      AuthenticationContext authContext(
        ap->Authority(), AuthorityValidationType::False, FileCachePtr);

      auto result = authContext.acquireToken(ap->Resource(),
                                           clientId_, redirect,
                                           PromptBehavior::Auto,
                                           ap->UserId());
      return result->accessToken();
      }

      catch (const rmsauth::Exception& ex)
      {
        // out logs
        throw;
      }
    }

[!INCLUDE[Commenting house rules](../includes/houserules.md)]