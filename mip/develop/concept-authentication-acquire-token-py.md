---
title: 'Konzepte: Verwenden von Python zum Abrufen eines Zugriffstokens'
description: In diesem Artikel erfahren Sie, wie Sie mithilfe von Python ein OAuth2-Zugriffstoken abrufen. Dieser Abruf ist für die Implementierung des Authentifizierungsdelegaten erforderlich.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 02/04/2019
ms.author: bryanla
ms.openlocfilehash: 423ae80df11dcf8031f845fdabf881606daf89c7
ms.sourcegitcommit: fa7551060aaecc62d0c1f9179dd07f035d86651f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742166"
---
# <a name="acquire-an-access-token-python"></a>Abrufen eines Zugriffstokens (Python)

Dieses Beispiel veranschaulicht den Abruf eines OAuth2-Tokens mithilfe des Aufrufs eines externen Python-Skripts. Ein gültiger OAuth2-Zugriffstoken ist durch die Implementierung von der authentifizierungsdelegat erforderlich.

## <a name="prerequisites"></a>Vorraussetzungen

So führen Sie das folgende Beispiel aus:

- Installation von Python 2.7.
- Implementierung von utils.h/cpp in Ihrem Projekt. 
- Auth.py Ihrem Projekt hinzugefügt werden sollen, und klicken Sie im gleichen Verzeichnis wie die Binärdateien auf der Build vorhanden.
- Vollständige [(MIP) SDK-Setup und Konfiguration](setup-configure-mip.md). U.a. müssen Sie Ihre Client-Anwendung in Ihrem Mandanten für Azure Active Directory (Azure AD) registrieren. Azure AD bietet eine Anwendungs-ID, auch bekannt als Client-ID, die in Ihrer Logik tokenabruf verwendet wird.

Dieser Code ist nicht für Produktionszwecke vorgesehen. Es kann nur für Entwicklungs- und Grundlegendes zu Auth Konzepten verwendet werden. Das Beispiel ist plattformübergreifend.

## <a name="sampleauthacquiretoken"></a>sample::auth::AcquireToken()

Im Beispiel einfache Authentifizierung veranschaulichten wir ein einfaches `AcquireToken()` Funktion, die keine Parameter hat und einen Tokenwert mit hartcodierten zurückgegeben. In diesem Beispiel überladen wir AcquireToken(), um Authentifizierungsparameter anzunehmen und ein externes Python-Skript aufzurufen, um das Token zurückzugeben.

### <a name="authh"></a>auth.h

In „auth.h“ ist `AcquireToken()` überladen, und die überladene Funktion und die aktualisierten Parameter lauten wie folgt:

```cpp
//auth.h
#include <string>

namespace sample {
  namespace auth {
    std::string AcquireToken();

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

    string AcquireToken() { //ignore in this sample
    }

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

Dieses Skript ruft Authentifizierungstoken direkt über eine einfache HTTP-Anforderung ab. Dies ist nur als eine Möglichkeit zum Abrufen von Authentifizierungstoken für die Verwendung durch die Beispiel-Apps enthalten und nicht für die Verwendung in Produktionscode vorgesehen. Das Skript funktioniert nur mit Mandanten, die die einfache alte HTTP-Authentifizierung mit Benutzername/Kennwort unterstützen. MFA oder zertifikatbasierte Authentifizierung (CBA) funktionieren nicht.

```python
import getopt
import sys
import json
import urllib
import urllib2
import re

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
    authority = authority + 'token'

  # Build REST call
  headers = {
    'Content-Type': 'application/x-www-form-urlencoded',
    'Accept': 'application/json'
  }

  params = {
    'resource': resource,
    'client_id': clientId,
    'grant_type': 'password',
    'username': username,
    'password': password
  }

  req = urllib2.Request(
    url = authority,
    headers = headers,
    data = urllib.urlencode(params))

  f = urllib2.urlopen(req)
  response = f.read()
  f.close()
  sys.stdout.write(json.loads(response)['access_token'])

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


