---
title: 'Konzepte: Authentifizierungs Szenarien für Microsoft Information Protection (MIP) SDK c#-Clients'
description: Technische Details zu Authentifizierungs Szenarien für c#-Client Anwendungen von Microsoft Information Protection SDK.
author: Pathak-Aniket
ms.author: v-anikep
ms.date: 09/02/2020
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: 10d6f5ce615373f0955c42f2573b7ddd59629734
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567919"
---
# <a name="quickstart-public-and-confidential-clients-c"></a>Schnellstart: öffentliche und vertrauliche Clients (c#)

Beim Entwickeln von Anwendungen mit dem MIP SDK werden zwei gängige Szenarien verwendet. Ein Szenario sieht vor, dass sich der Benutzer direkt bei Azure AD authentifiziert, wobei wie im anderen Fall, dass die Anwendung authentifiziert einen geheimen Dienst Prinzipal Schlüssel oder ein Zertifikat verwendet.

## <a name="public-client-applications"></a>Öffentliche Client Anwendungen

Dabei handelt es sich im Allgemeinen um Desktop-oder Mobile Anwendungen, bei denen die Anwendung, die auf dem Gerät ausgeführt wird, den Benutzer zur Authentifizierung auffordert und der Benutzer direkt eine Verbindung mit den MIP-Back-Ends In diesem Szenario sollten Authentifizierungs Bibliotheken verwendet werden, um sicherzustellen, dass sich der Benutzer bei Azure AD anmelden kann, alle Anforderungen an den Multi-Factor-oder bedingten Zugriff erfüllt und ein OAuth2-Token für die entsprechende Ressource abruft.

Weitere Informationen finden Sie in der Dokumentation für den Azure AD [Public Client Authentifizierung-Fluss](/azure/active-directory/develop/msal-net-initializing-client-applications#initializing-a-public-client-application-from-configuration-options) .

Im folgenden finden Sie einen schnellen Code, der die Authentifizierung mit dem öffentlichen Client für die Microsoft Information Protection SDK-Client Anwendung mithilfe der Microsoft Authentication Library (msal) demonstriert.

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

Tenant-GUID steht für Mandanten-GUID für den Azure AD-Mandanten, während Application-ID die Anwendungs-ID in der Anwendungs Registrierung auf Azure AD Portal ist.

## <a name="confidential-client-applications"></a>Vertrauliche Client Anwendungen

Dabei handelt es sich im Allgemeinen um cloudbasierte oder Dienst basierte Anwendungen, bei denen der Benutzer nicht direkt eine Verbindung mit den MIP-Diensten des Back-Ends herstellt, aber der Dienst muss MIP-fähige Inhalte bezeichnen, schützen oder den Schutz aufheben. In diesem Szenario muss die Anwendung ein Zertifikat oder ein Anwendungs Geheimnis speichern, das für die Authentifizierung bei der Azure AD verwendet werden kann, und dieses Geheimnis zum Abrufen von Token für die MIP-Back-End-Dienste verwenden. Anschließend können die Delegierungs Funktionen des MIP SDK verwendet werden, um im Namen des authentifizierten Benutzers Inhalte zu schützen oder zu nutzen.

Weitere Informationen finden Sie in der [Dokumentation zum Azure AD vertraulichen Client Authentifizierung-Fluss](/azure/active-directory/develop/msal-net-initializing-client-applications#initializing-a-confidential-client-application-from-code) .

Im folgenden finden Sie einen kurzen Code Ausschnitt, der den vertraulichen Client Authentifizierungs Fluss für die Microsoft Information Protection SDK-Client Anwendung mithilfe der Microsoft Authentication Library (msal) demonstriert. Eine Anwendung kann entweder mit dem AD-Zertifikat oder dem geheimen Client Schlüssel authentifiziert werden.

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

Tenant-GUID steht für Mandanten-GUID für den Azure AD-Mandanten, während Application-ID die Anwendungs-ID in der Anwendungs Registrierung auf Azure AD Portal ist.