---
# required metadata

title: Gewusst wie &#58; Hinzufügen von Authentifizierung zu einer App | Azure RMS
description: Beschreibt die Grundlagen der Benutzerauthentifizierung für Ihre RMS-fähige Anwendung.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 200D9B23-F35D-4165-9AC4-C482A5CE1D28
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gewusst wie: Hinzufügen von Authentifizierung zu einer App

Dieses Thema beschreibt die Grundlagen der Benutzerauthentifizierung für Ihre RMS-fähige Anwendung.

## Was ist Benutzerauthentifizierung?
Benutzerauthentifizierung ist ein grundlegender Schritt beim Aufbau der Kommunikation zwischen der Geräte-App und der RMS-Infrastruktur. In diesem Authentifizierungsprozess wird das OAuth 2.0-Standardprotokoll verwendet, bei dem die folgenden Angaben über den aktuellen Benutzer und die zugehörige Authentifizierungsanforderung benötigt werden: **Autorität**, **Ressource** und **Benutzer-ID**.

**Hinweis** Der Bereich wird aktuell nicht verwendet, kann aber verwendet werden und ist daher für die zukünftige Verwendung reserviert.

 

**Benutzerauthentifizierungsrückruf** – Das Microsoft Rights Management SDK 4.2 verwendet Ihre Implementierung eines Authentifizierungsrückrufs, wenn Sie kein Zugriffstoken angeben, wenn das Zugriffstoken aktualisiert werden muss oder wenn das Zugriffstoken abgelaufen ist.

Jede der RMS-APIs der Plattform verfügt über einen Rückruf, der implementiert werden muss, um eine Authentifizierung des Benutzers zu ermöglichen.

-   Die Android-API verwendet die Schnittstellen [**AuthenticationRequestCallback**](/rights-management/sdk/4.2/api/android/com.microsoft.rightsmanagement#msipcthin2_authenticationrequestcallback_interface_java) und [**AuthenticationCompletionCallback**](/rights-management/sdk/4.2/api/android/authenticationcompletioncallback#msipcthin2_authenticationcompletioncallback_interface_java).
-   Die iOS/OS X-API verwendet das [**MSAuthenticationCallback**](/rights-management/sdk/4.2/api/iOS/iOS#msipcthin2_msauthenticationcallback_protocol_objc)-Protokoll.
-   Die WinPhone-API verwendet die [**IAuthenticationCallback**](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_iauthenticationcallback)-Schnittstelle.
-   Die Linux-API verwendet die [IAuthenticationCallback](http://azuread.github.io/rms-sdk-for-cpp/classrmscore_1_1modernapi_1_1IAuthenticationCallback.html)-Schnittstelle.

## Welche Bibliothek zur Authentifizierung verwendet werden soll

Zur Implementierung eines eigenen Authentifizierungsrückrufs müssen Sie eine entsprechende Bibliothek herunterladen und Ihre Entwicklungsumgebung für deren Verwendung konfigurieren. Auf GitHub finden Sie die ADAL-Bibliotheken für diese Plattformen. Jede der folgenden Ressourcen enthält Anleitungen zum Einrichten Ihrer Umgebung und Verwenden der Bibliothek.

-   [Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für iOS](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für Mac](https://github.com/MSOpenTech/azure-activedirectory-library-for-ios/)
-   [Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für Android](https://github.com/MSOpenTech/azure-activedirectory-library-for-android)
-   [Windows Azure Active Directory-Authentifizierungsbibliotheken (ADAL) für dotnet](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)
-   Beim Linux-SDK befindet sich die ADAL-Bibliothek im SDK-Quellcodepaket, das über [Github](https://github.com/AzureAD/rms-sdk-for-cpp) verfügbar ist.

**Hinweis** Es wird empfohlen, dass Sie selbst dann eine der oben genannten Active Directory-Authentifizierungsbibliotheken (ADAL) verwenden, wenn Sie andere Authentifizierungsbibliotheken verwenden könnten.

## Eingaben für die Authentifizierung mit der Azure Active Directory-Authentifizierungsbibliothek (ADAL)

Die ADAL erfordert einige Parameter, um Benutzer von Azure RMS (oder AD RMS) erfolgreich authentifizieren zu können. Es handelt sich dabei um die OAuth 2.0-Standardparameter, die in der Regel für jede Azure AD-App ebenso wie RMS-fähige Apps erforderlich sind. Sie finden die aktuellen Richtlinien für die Verwendung von ADAL in der README-Datei der entsprechenden Github-Repositorys, die oben aufgeführt wurden.

Diese Parameter und Richtlinien sind für die RMS-Workflows erforderlich:

-   **Autorität** – Die URL des Authentifizierungsendpunkts, in der Regel AAD oder ADFS. Dieser Parameter wird durch den RMS-SDK-Authentifizierungsrückruf für Ihre Anwendung bereitgestellt.
-   **Ressource** – URL/URI der Dienstanwendung, auf die Sie zuzugreifen versuchen, in der Regel Azure RMS oder AD RMS. Dieser Parameter wird durch den RMS-SDK-Authentifizierungsrückruf für Ihre Anwendung bereitgestellt.
-   **Benutzer-ID** – UPN, in der Regel die E-Mail-Adresse des Benutzers, der auf die Anwendung zugreifen möchte. Dieser Parameter kann leer sein, wenn der Benutzer noch nicht bekannt ist, und er dient außerdem zum Zwischenspeichern von Benutzertoken oder zum Anfordern eines Token aus dem Cache. Dies wird auch in der Regel als „Hinweis“ für Benutzereingabeaufforderungen verwendet.
-   **Client-ID** – Die ID der Client-App. Dies muss eine gültige ID für Azure AD-Anwendung sein. Weitere Informationen finden Sie unter „Gewusst wie: Abrufen einer Azure-Anwendungs-ID“.
-   **Umleitungs-URI** – Stellt der Authentifizierungsbibliothek einen Ziel-URI für den Authentifizierungscode bereit. Beachten Sie, dass für IOS und Android spezielle Formate erforderlich sind, die in den README-Dateien der entsprechenden GitHub-Repositorys von ADAL erläutert werden.

    Android: `msauth://packagename/Base64UrlencodedSignature`

    iOS: `<app-scheme>://<bundle-id>`

**Hinweis** Die Azure RMS- und Azure AD-Workflows schlagen wahrscheinlich fehl und werden von Microsoft nicht unterstützt, wenn Ihre App diesen Richtlinien nicht entspricht. Darüber hinaus kann es einen Verstoß gegen die Rights Management License Agreement (RMLA) darstellen, wenn in einer Produktions-App eine ungültige Client-ID verwendet wird.

## Wie sollte die Implementieren eines Authentifizierungsrückrufs aussehen

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


**iOS/OS X-Benutzerauthentifizierung** – Weitere Informationen finden Sie unter [Codebeispiele für iOS/OS X](ios-os-x-code-examples.md),

**Schritt 2** des ersten Szenarios mit dem Titel "Nutzen einer RMS-geschützten Datei".


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



**Linux/C++-Benutzerauthentifizierung** – Weitere Informationen finden Sie unter [Codebeispiele für Linux](linux-c-code-examples.md).



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



 

 


<!--HONumber=Apr16_HO4-->


