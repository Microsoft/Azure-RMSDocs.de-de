---
title: 'Konzepte: Implementierung des Authentifizierungsdelegaten (C++)'
description: In diesem Artikel erfahren Sie, wie Sie einen Authentifizierungsdelegaten in C++ implementieren.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: e3436acdd6a2900f4a21bb50b283d12065cd659b
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "69886247"
---
# <a name="microsoft-information-protection-sdk---implementing-an-authentication-delegate-c"></a>Microsoft Azure Information Protection SDK: Implementieren eines Authentifizierungsdelegaten (C++)

Das MIP SDK implementiert einen Authentifizierungsdelegaten zum Verarbeiten von Problemen bei der Authentifizierung und zum Antworten mit einem Token. Es implementiert den Tokenabruf nicht selbst. Der Prozess des Tokenabrufs wird vom Entwickler festgelegt. Dafür muss die `mip::AuthDelegate`-Klasse und insbesondere die Memberfunktion `AcquireOAuth2Token` abgerufen werden.

## <a name="building-authdelegateimpl"></a>Erstellen von AuthDelegateImpl

Damit die Basisklasse `mip::AuthDelegate`erweitert werden kann, wird eine neue Klasse mit dem Namen `sample::auth::AuthDelegateImpl` erstellt. Diese Klasse implementiert die Funktion `AcquireOAuth2Token` und richtet den Konstruktor ein, der zu den Authentifizierungsparametern hinzugefügt werden soll.

### <a name="auth_delegate_implh"></a>auth_delegate_impl.h

In diesem Beispiel akzeptiert der Standardkonstruktor nur den Benutzernamen, das Kennwort und die [Anwendungs-ID](/azure/active-directory/develop/developer-glossary#application-id-client-id). Diese Elemente werden in den privaten Variablen `mUserName`, `mPassword` und `mClientId` gespeichert.

Es gilt zu beachten, dass Informationen wie der Identitätsanbieter oder der Ressourcen-URI nicht unbedingt in den Konstruktor `AuthDelegateImpl` implementiert werden müssen. Diese Informationen werden als Bestandteil von `AcquireOAuth2Token` an das `OAuth2Challenge`-Objekt übergeben. D.h., sie werden an den `AcquireToken`-Aufruf in `AcquireOAuth2Token` übergeben.

```cpp
//auth_delegate_impl.h
#include <string.h>
#include "mip/common_types.h"

namespace sample {
namespace auth {
class AuthDelegateImpl final : public mip::AuthDelegate { //extend mip::AuthDelegate base class
public:
  AuthDelegateImpl() = delete;

//constructor accepts username, password, and mip::ApplicationInfo.
  AuthDelegateImpl::AuthDelegateImpl(
    const mip::ApplicationInfo& applicationInfo,
    std::string& username,
    const std::string& password)
    : mApplicationInfo(applicationInfo),
      mUserName(username),
      mPassword(password) {
  }

  bool AcquireOAuth2Token(const mip::Identity& identity, const OAuth2Challenge& challenge, OAuth2Token& token) override;

  private:
    std::string mUserName;
    std::string mPassword;
    std::string mClientId;
    mip::ApplicationInfo mApplicationInfo;
};
}
}
```

### <a name="auth_delegate_implcpp"></a>auth_delegate_impl.cpp

Im `AcquireOAuth2Token` wird der Aufruf des OAuth2-Anbieters durchgeführt. Im nachfolgenden Beispiel wird `AcquireToken()` zweimal aufgerufen. In der Praxis würde nur ein Aufruf ausgeführt werden. Diese Implementierungen werden in den [Nächsten Schritten](#next-steps) erläutert.

```cpp
//auth_delegate_impl.cpp
#include "auth_delegate_impl.h"
#include <stdexcept>
#include "auth.h" //contains the auth class used later for token acquisition

using std::runtime_error;
using std::string;

namespace sample {
namespace auth {

AuthDelegateImpl::AuthDelegateImpl(
    const string& userName,
    const string& password,
    const string& clientId)
    : mApplicationInfo(applicationInfo),
    mUserName(userName),
    mPassword(password) {
}

//Here we could simply add our token acquisition code to AcquireOAuth2Token
//Instead, that code is implemented in auth.h/cpp to demonstrate calling an external library
bool AuthDelegateImpl::AcquireOAuth2Token(
    const mip::Identity& /*identity*/, //This won't be used
    const OAuth2Challenge& challenge,
    const OAuth2Token& token) {

      //sample::auth::AcquireToken is the code where the token acquisition routine is implemented.
      //AcquireToken() returns a string that contains the OAuth2 token.

      //Simple example for getting hard coded token. Comment out if not used.
      string accessToken = sample::auth::AcquireToken();

      //Practical example for calling external OAuth2 library with provided authentication details.
      string accessToken = sample::auth::AcquireToken(mUserName, mPassword, mApplicationInfo.applicationId, challenge.GetAuthority(), challenge.GetResource());

      //set the passed in OAuth2Token value to the access token acquired by our provider
      token.SetAccessToken(accessToken);
      return true;
    }
}
}
```

## <a name="next-steps"></a>Nächste Schritte

Sie müssen den Code hinter der `AcquireToken()`-Funktion erstellen, um die Implementierung der Authentifizierung abzuschließen. In den nachfolgenden Beispielen werden einige Möglichkeiten zum Abrufen des Token beschrieben.

- [Simple/PowerShell token acquisition example (Beispiel für das Abrufen eines einfachen Token bzw. eines PowerShell-Token)](concept-authentication-acquire-token-ps.md)
- [Python token acquisition example (Beispiel für das Abrufen eines Token in Python)](concept-authentication-acquire-token-py.md)
