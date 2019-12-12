---
title: 'Konzepte: Verwenden von Python zum Abrufen eines Zugriffstokens'
description: In diesem Artikel erfahren Sie, wie Sie mithilfe von Python ein OAuth2-Zugriffstoken abrufen. Dieser Aufruf ist für die Implementierung des Authentifizierungsdelegaten erforderlich.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: b46f478dc38e9010cc2eb221f587f3d3ca3f60a2
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "69884741"
---
# <a name="acquire-an-access-token-python"></a>Abrufen eines Zugriffstokens (Python)

Dieses Beispiel veranschaulicht den Abruf eines OAuth2-Tokens mithilfe des Aufrufs eines externen Python-Skripts. Ein gültiges OAuth2-Zugriffs Token ist für die Implementierung des Authentifizierungs Delegaten erforderlich.

## <a name="prerequisites"></a>Voraussetzungen

So führen Sie das folgende Beispiel aus:

- Installieren Sie Python 2,7 oder höher.
- Implementierung von utils.h/cpp in Ihrem Projekt. 
- Auth.py sollte dem Projekt hinzugefügt werden und im gleichen Verzeichnis wie die Binärdateien beim Build vorhanden sein.
- Complete [(MIP) SDK-Setup und-Konfiguration](setup-configure-mip.md). Neben anderen Aufgaben registrieren Sie Ihre Client Anwendung in Ihrem Azure Active Directory-Mandanten (Azure AD). Azure AD geben eine Anwendungs-ID (auch als Client-ID bezeichnet) an, die in der tokenerwerbs-Logik verwendet wird.

Dieser Code ist nicht für die Verwendung in der Produktion bestimmt. Sie kann nur für die Entwicklung und das Verständnis von Authentifizierungs Konzepten verwendet werden. Das Beispiel ist plattformübergreifend.

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

Im Beispiel für die einfache Authentifizierung haben wir eine einfache `AcquireToken()` Funktion veranschaulicht, die keine Parameter angenommen hat und einen hart codierten Tokenwert zurückgegeben hat. In diesem Beispiel überladen wir AcquireToken(), um Authentifizierungsparameter anzunehmen und ein externes Python-Skript aufzurufen, um das Token zurückzugeben.

### <a name="authh"></a>auth.h

In „auth.h“ ist `AcquireToken()` überladen, und die überladene Funktion und die aktualisierten Parameter lauten wie folgt:

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {    
    std::string AcquireToken(
        const std::string& userName, //A string value containing the user's UPN.
        const std::string& password, //The user's password in plaintext
        const std::string& clientId, //The Azure AD client ID (also known as Application ID) of your application.
        const std::string& resource, //The resource URL for which an OAuth2 token is required. Provided by challenge object.
        const std::string& authority); //The authentication authority endpoint. Provided by challenge object.
    }
}
```

Die ersten drei Parameter werden durch eine Benutzereingabe bereitgestellt oder in Ihrer Anwendung festcodiert. Die beiden letzten Parameter werden vom SDK für den Authentifizierungsdelegaten bereitgestellt. 


### <a name="authcpp"></a>auth.cpp

In „auth.cpp“ fügen wir die Definition der überladenen Funktion hinzu und definieren dann den erforderlichen Code für den Aufruf des Python-Skripts. Die Funktion nimmt alle angegebenen Parameter an und übergibt sie an das Python-Skript. Das Skript wird ausgeführt und gibt das Token im Zeichenfolgenformat zurück.

```cpp
#include "auth.h"
#include "utils.h"

#include <fstream>
#include <functional>
#include <memory>
#include <string>

using std::string;
using std::runtime_error;

namespace sample {
    namespace auth {

    //This function implements token acquisition in the application by calling an external Python script.
    //The Python script requires username, password, clientId, resource, and authority.
    //Username, Password, and ClientId are provided by the user/developer
    //Resource and Authority are provided as part of the OAuth2Challenge object that is passed in by the SDK to the AuthDelegate.
    string AcquireToken(
        const string& userName,
        const string& password,
        const string& clientId,
        const string& resource,
        const string& authority) {

    string cmd = "python";
    if (sample::FileExists("auth.py"))
        cmd += " auth.py -u ";

    else
        throw runtime_error("Unable to find auth script.");

    cmd += userName;
    cmd += " -p ";
    cmd += password;
    cmd += " -a ";
    cmd += authority;
    cmd += " -r ";
    cmd += resource;
    cmd += " -c ";
    // Replace <application-id> with the Application ID provided during your Azure AD application registration.
    cmd += (!clientId.empty() ? clientId : "<application-id>");

    string result = sample::Execute(cmd.c_str());
    if (result.empty())
        throw runtime_error("Failed to acquire token. Ensure Python is installed correctly.");

    return result;
    }
    }
}

```

## <a name="python-script"></a>Python-Skript

Dieses Skript ruft Authentifizierungs Token direkt über [Adal für python](https://github.com/AzureAD/azure-activedirectory-library-for-python)ab. Dieser Code ist nur als Mittel zum Abrufen von Authentifizierungs Token für die Verwendung durch die Beispiel-Apps enthalten und ist nicht für die Verwendung in der Produktion bestimmt. Das Skript funktioniert nur mit Mandanten, die die einfache alte HTTP-Authentifizierung mit Benutzername/Kennwort unterstützen. MFA oder zertifikatbasierte Authentifizierung (CBA) funktionieren nicht.

> [!NOTE] 
> Vor dem Ausführen dieses Beispiels müssen Sie Adal für python installieren, indem Sie einen der folgenden Befehle ausführen:

```shell
pip install adal
pip3 install adal
```

```python
import getopt
import sys
import json
import re
from adal import AuthenticationContext

def printUsage():
  print('auth.py -u <username> -p <password> -a <authority> -r <resource> -c <clientId>')

def main(argv):
  try:
    options, args = getopt.getopt(argv, 'hu:p:a:r:c:')
  except getopt.GetoptError:
    printUsage()
    sys.exit(-1)

  username = ''
  password = ''
  authority = ''
  resource = ''

  clientId = ''
    
  for option, arg in options:
    if option == '-h':
      printUsage()
      sys.exit()
    elif option == '-u':
      username = arg
    elif option == '-p':
      password = arg
    elif option == '-a':
      authority = arg
    elif option == '-r':
      resource = arg
    elif option == '-c':
      clientId = arg

  if username == '' or password == '' or authority == '' or resource == '' or clientId == '':
    printUsage()
    sys.exit(-1)

  # Find everything after the last '/' and replace it with 'token'
  if not authority.endswith('token'):
    regex = re.compile('^(.*[\/])')
    match = regex.match(authority)
    authority = match.group()
    authority = authority + username.split('@')[1]

  auth_context = AuthenticationContext(authority)
  token = auth_context.acquire_token_with_username_password(resource, username, password, clientId)
  print(token["accessToken"])

if __name__ == '__main__':  
  main(sys.argv[1:])
```

## <a name="update-acquireoauth2token"></a>Aktualisieren von AcquireOAuth2Token

Aktualisieren Sie abschließend die `AcquireOAuth2Token`-Funktion in `AuthDelegateImpl` für den Aufruf der überladenen `AcquireToken`-Funktion. Die Ressourcen- und Autoritäts-URLs werden durch Lesen von `challenge.GetResource()` und `challenge.GetAuthority()` ermittelt. Das `OAuth2Challenge`-Element wird an den Authentifizierungsdelegaten übergeben, wenn die Engine hinzugefügt wird. Diese Aufgabe wird durch das SDK erledigt und erfordert keinen zusätzlichen Aufwand seitens des Entwicklers. 

```cpp
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/,
    const OAuth2Challenge& challenge,
    OAuth2Token& token) {

    //call our AcquireToken function, passing in username, password, clientId, and getting the resource/authority from the OAuth2Challenge object
    string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mClientId, challenge.GetResource(), challenge.GetAuthority());
    token.SetAccessToken(accessToken);
    return true;
}
```

Wenn die `engine` hinzugefügt wird, ruft das SDK die `AcquireOAuth2Token-Funktion auf, übergibt die Abfrage, führt das Python-Skript aus, empfängt ein Token und stellt das Token für den Dienst bereit.


