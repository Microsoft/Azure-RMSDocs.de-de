---
title: 'Konzepte: Authentifizierungs Szenarien für Microsoft Information Protection (MIP) SDK c#-Clients'
description: Technische Details zu Authentifizierungs Szenarien für c#-Client Anwendungen von Microsoft Information Protection SDK.
author: Pathak-Aniket
ms.author: v-anikep
ms.date: 09/02/2020
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: 8d210d74ecfd4ebdc50ec618415191894431fcdc
ms.sourcegitcommit: 7420cf0200c90687996124424a254c289b11a26f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "101844317"
---
# <a name="quickstart-public-and-confidential-clients-c"></a>Schnellstart: öffentliche und vertrauliche Clients (c#)

Beim Entwickeln von Anwendungen mit dem MIP SDK werden zwei gängige Szenarien verwendet. Im ersten Szenario authentifiziert sich der Benutzer direkt bei Azure AD. In der zweiten wird die Anwendung mit einem geheimen Dienst Prinzipal Schlüssel oder-Zertifikat authentifiziert.

## <a name="public-client-applications"></a>Öffentliche Client Anwendungen

Bei diesen Anwendungen handelt es sich um Desktop Anwendungen oder Mobile Anwendungen, bei denen die Anwendung, die auf dem Gerät ausgeführt wird, den Benutzer zur Authentifizierung auffordert. Der Benutzer stellt eine direkte Verbindung mit den MIP-Back-Ends her. In diesem Szenario sollten Authentifizierungs Bibliotheken verwendet werden, um sicherzustellen, dass sich der Benutzer bei Azure AD anmelden kann, sämtliche Anforderungen an den Multi-Factor-oder bedingten Zugriff erfüllt und ein OAuth2-Token für die entsprechende Ressource abruft.

Weitere Informationen finden Sie in der [Dokumentation zum öffentlichen Client Authentifizierung-Fluss](/azure/active-directory/develop/msal-net-initializing-client-applications#initializing-a-public-client-application-from-configuration-options) .

Im folgenden finden Sie ein schnelles Code-Ausschnitt, das die Authentifizierung der öffentlichen Client Authentifizierung für die Microsoft Information Protection SDK-Client Anwendung mithilfe der Microsoft Authentication Library (msal) demonstriert.

```csharp

public string AcquireToken(Identity identity, string authority, string resource, string claims)
{
     var authorityUri = new Uri(authority);
     authority = String.Format("https://{0}/{1}", authorityUri.Host, "<Tenant-GUID>");

     _app = PublicClientApplicationBuilder.Create("<Application-Id>").WithAuthority(authority).WithDefaultRedirectUri().Build();

     var accounts = (_app.GetAccountsAsync()).GetAwaiter().GetResult();

     // Append .default to the resource passed in to AcquireToken().
     string[] scopes = new string[] { resource[resource.Length - 1].Equals('/') ? $"{resource}.default" : $"{resource}/.default" };
     var result = _app.AcquireTokenInteractive(scopes).WithAccount(accounts.FirstOrDefault()).WithPrompt(Prompt.SelectAccount)
                    .ExecuteAsync().ConfigureAwait(false).GetAwaiter().GetResult();

     return result.AccessToken;
}
```

**Tenant-GUID** ist die eindeutige Mandanten-GUID für den Azure AD Mandanten.
Die Anwendungs **-ID** ist die Anwendungs-ID in der Anwendungs Registrierung auf Azure AD-Portal.

## <a name="confidential-client-applications"></a>Vertrauliche Client Anwendungen

Bei diesen Anwendungen handelt es sich um cloudbasierte oder Dienst basierte Anwendungen, bei denen der Benutzer nicht direkt eine Verbindung mit den MIP-Back-Ends Der Dienst muss MIP-fähige Inhalte bezeichnen, schützen oder den Schutz aufheben. In diesem Szenario muss die Anwendung ein Zertifikat oder ein Anwendungs Geheimnis speichern. Diese geheimen Schlüssel werden für die Authentifizierung bei der Azure AD verwendet und verwenden diesen geheimen Schlüssel zum Abrufen von Token für die MIP-Back-End-Dienste. Anschließend können die Delegierungs Funktionen des MIP SDK verwendet werden, um im Namen des authentifizierten Benutzers Inhalte zu schützen oder zu nutzen.

Die Integration des MIP SDK in Dienst basierte Anwendungen erfordert die Verwendung des Client Anmelde Informationen Grant-Flows. Die Microsoft Authentication Library (msal) kann verwendet werden, um dies in einem Muster zu implementieren, das dem in einer öffentlichen Client Anwendung entsprechenden Muster ähnelt. In diesem Artikel wird kurz erläutert, wie Sie das MIP SDK `IAuthDelegate` in .NET aktualisieren, um die Authentifizierung für Dienst basierte Anwendungen mit diesem Flow auszuführen. Zum Zeitpunkt der Veröffentlichung gibt es keine msal-Version für C++, aber es ist möglich, diesen Flow über [direkte Rest-Aufrufe](/azure/active-directory/develop/v2-oauth2-client-creds-grant-flow#get-a-token)zu implementieren.

Weitere Informationen finden Sie in der [Dokumentation zum vertraulichen Client Authentifizierung-Fluss](/azure/active-directory/develop/msal-net-initializing-client-applications#initializing-a-confidential-client-application-from-code) .

Im folgenden finden Sie einen kurzen Code Ausschnitt, der den vertraulichen Client Authentifizierungs Fluss für die Microsoft Information Protection SDK-Client Anwendung mithilfe der Microsoft Authentication Library (msal) demonstriert. Eine Anwendung kann entweder mit dem AD-Zertifikat oder dem geheimen Client Schlüssel authentifiziert werden.

> [!NOTE]
> Beachten Sie diese Zeile im folgenden Beispiel besonders. 
>
> ```csharp
> string[] scopes = new string[] { resource[resource.Length - 1].Equals('/') ? $"{resource}.default" : $"{resource}/.default" };
> ```
> Hierdurch werden die msal-Bereiche aus der für die-Methode bereitgestellten Ressource konstruiert `AcquireToken()` . 

### <a name="msal-confidential-client-example"></a>Beispiel für vertraulichen msal-Client

```csharp
public string AcquireToken(Identity identity, string authority, string resource, string claim)
{
     AuthenticationResult result;
     var authorityUri = new Uri(authority);
     authority = string.Format("https://{0}/{1}", authorityUri.Host, "<Tenant-GUID>");

     // Certification Based Auth
     if (doCertAuth)
     {
          // Build ConfidentialClientApplication using certificate.
          _app = ConfidentialClientApplicationBuilder.Create("<Application-Id>")
               .WithCertificate(certificate) //Assumption here is Application passes a certificate created using certificate thumbprint
               .WithAuthority(new Uri(authority))
               .Build();
     }

     // Client secret based Auth
     else
     {
          // Build ConfidentialClientApplication using app secret
          _app = ConfidentialClientApplicationBuilder.Create("<Application-Id>")
               .WithClientSecret(clientSecret)
               .WithAuthority(new Uri(authority))
               .Build();
     }

     // Append .default to the resource passed in to AcquireToken().
     string[] scopes = new string[] { resource[resource.Length - 1].Equals('/') ? $"{resource}.default" : $"{resource}/.default" };

     try{
          result = _app.AcquireTokenForClient(scopes).ExecuteAsync().Result;
     }
     catch (MsalServiceException ex) when (ex.Message.Contains("AADSTS70011"))
     {
          // Invalid scope. The scope has to be of the form "https://resourceurl/.default"
          // Mitigation: change the scope to be as expected
          Console.WriteLine("Scope provided is not supported");
          return null;
     }
            return result.AccessToken;
}

```
**Tenant-GUID** ist die eindeutige Mandanten-GUID für den Azure AD Mandanten.
Die Anwendungs **-ID** ist die Anwendungs-ID in der Anwendungs Registrierung auf Azure AD-Portal.