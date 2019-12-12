---
title: 'Konzepte: Authentifizierung im MIP SDK'
description: Dieser Artikel wird Ihnen helfen zu verstehen, wie das MIP SDK die Authentifizierung implementiert. Außerdem werden die Anforderungen an Clientanwendungen beschrieben, um OAuth2-Zugriffstoken-Abruflogik bereitzustellen.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 55bfba6da57fa07614165f4d5fcc5fba226cfca7
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "69886235"
---
# <a name="microsoft-information-protection-sdk---authentication-concepts"></a>Microsoft Information Protection SDK: Authentifizierungskonzepte

Die Authentifizierung im MIP SDK erfolgt durch Erweiterung der `mip::AuthDelegate`-Klasse, um die von Ihnen bevorzugte Authentifizierungsmethode zu implementieren. `mip::AuthDelegate` enthält Folgendes:

- `mip::AuthDelegate::OAuth2Challenge`: Eine Klasse, die die Informationen der OAuth2-Autorität verwaltet und für die Clientanwendung bereitstellt.
- `mip::AuthDelegate::OAuth2Token`: Eine Klasse, die den Abruf von OAuth2-Zugriffstoken (aus der Clientanwendung) und die Tokenspeicherung verwaltet.
- `mip::AuthDelegate::AcquireOAuth2Token()`: Eine rein virtuelle Funktion, deren Implementierung die Methode des Zugriffstokenabrufs bestimmt. Nach dem Aufruf durch das SDK ruft sie das Zugriffstoken ab und stellt es dann erneut der Authentifizierungslogik des SDK zur Verfügung.

`mip::AuthDelegate::AcquireOAuth2Token` nimmt die folgenden Parameter an und gibt einen booleschen Wert zurück, der angibt, ob der Tokenabruf erfolgreich war:

- `mip::Identity`: Die Identität des zu authentifizierenden Benutzers oder Diensts, sofern bekannt.
- `mip::AuthDelegate::OAuth2Challenge`: akzeptiert vier Parameter, **Autorität**, **Ressource**, **Ansprüche**und **Bereiche**. **Authority** ist der Dienst, für den das Token generiert wird. **Resource** ist der Dienst, auf den wir zugreifen möchten. Das SDK verarbeitet beim Aufruf die Übergabe dieser Parameter an den Delegaten. **Ansprüche** sind die Bezeichnungs spezifischen Ansprüche, die für den Schutzdienst erforderlich sind. **Bereiche** sind die Azure AD Berechtigungs Bereiche, die für den Zugriff auf die Ressource erforderlich sind. 
- `mip::AuthDelegate::OAuth2Token`: Das Tokenergebnis wird in dieses Objekt geschrieben. Es wird durch das SDK genutzt, wenn die Engine geladen wird. Außerhalb unserer Authentifizierungsimplementierung sollte das Abrufen oder Festlegen dieses Werts nirgendwo erforderlich sein.

**Wichtig:** Anwendungen rufen `AcquireOAuth2Token` nicht direkt auf. Das SDK ruft diese Funktion bei Bedarf auf.

## <a name="consent"></a>Consent

Azure AD verlangt, dass einer Anwendung Zustimmung erteilt wird, bevor ihr die Erlaubnis zum Zugriff auf gesicherte Ressourcen/APIs unter der Identität eines Kontos erteilt wird. Die Zustimmung wird als dauerhafte Bestätigung der Berechtigung im Mandanten des Kontos, für das jeweilige Konto (Benutzer Zustimmung) oder für alle Konten (Administrator Zustimmung) aufgezeichnet. Zustimmung tritt in verschiedenen Szenarien basierend auf der API auf, auf die zugegriffen wird, den Berechtigungen, nach denen die Anwendung sucht, und dem Konto, das für die Anmeldung verwendet wird: 

- Konten aus dem *gleichen Mandanten*, in dem Ihre Anwendung registriert ist, wenn Sie oder ein Administrator nicht explizit dem Zugriff über das Feature „Berechtigungen erteilen“ vorab zugestimmt haben.
- Konten aus einer *anderen Mandanten*, wenn Ihre Anwendung als mehrinstanzenfähig registriert ist und der Mandantenadministrator nicht für alle Benutzer vorab zugestimmt hat.

Die `mip::Consent`-Enumerationsklasse implementiert einen benutzerfreundlichen Ansatz, der es Anwendungsentwicklern ermöglicht, eine benutzerdefinierte Zustimmungserfahrung basierend auf dem Endpunkt bereitzustellen, auf den das SDK zugreift. Die Benachrichtigung kann einen Benutzer über die zu erfassenden Daten, die Entfernung der Daten oder alle anderen Informationen informieren, die aufgrund von gesetzlichen Vorschriften oder Compliancerichtlinien erforderlich sind. Sobald der Benutzer seine Zustimmung erteilt hat, kann die Anwendung fortgesetzt werden. 

### <a name="implementation"></a>Implementierung

Zustimmung wird durch Erweitern der `mip::Consent`-Basisklasse und Implementieren von `GetUserConsent` zum Zurückgeben eines der `mip::Consent`-Enumerationswerte implementiert. 

Das von `mip::Consent` abgeleitete Objekt wird an den `mip::FileProfile::Settings`- oder `mip::ProtectionProfile::Settings`-Konstruktor übergeben.

Wenn ein Benutzer einen Vorgang ausführt, der Zustimmung erfordert, ruft das SDK die `GetUserConsent`-Methode auf und übergibt die Ziel-URL als Parameter. In dieser Methode würde die Anzeige der erforderlichen Informationen für den Benutzer implementiert, sodass er eine Entscheidung darüber treffen kann, ob er der Nutzung des Dienstes zustimmt oder nicht. 

### <a name="consent-options"></a>Zustimmungsoptionen

- **AcceptAlways**: Zustimmen und die Entscheidung speichern.
- **Accept**: Ein Mal zustimmen.
- **Reject**: Keine Zustimmung.

Wenn das SDK die Zustimmung des Benutzers mit dieser Methode anfordert, sollte die Clientanwendung dem Benutzer die URL anzeigen. Clientanwendungen sollten eine Möglichkeit bieten, die Zustimmung des Benutzers einzuholen und die entsprechende Zustimmungsenumeration zurückzugeben, die der Entscheidung des Benutzers entspricht.

### <a name="sample-implementation"></a>Beispielimplementierung

#### <a name="consent_delegate_implh"></a>consent_delegate_impl.h

```cpp
class ConsentDelegateImpl final : public mip::ConsentDelegate {
public:
  ConsentDelegateImpl() = default;
  
  virtual mip::Consent GetUserConsent(const std::string& url) override;

};
```

#### <a name="consent_delegate_implcpp"></a>consent_delegate_impl.cpp

Wenn das SDK Zustimmung erfordert, wird die `GetUserConsent`-Methode *vom SDK* aufgerufen und die URL als Parameter übergeben. Im folgenden Beispiel wird der Benutzer benachrichtigt, dass das SDK eine Verbindung mit der bereitgestellten URL herstellt und dem Benutzer eine Option in der Befehlszeile bereitstellt. Basierend auf der Auswahl des Benutzers akzeptiert oder lehnt der Benutzer die Zustimmung ab, und er wird an das SDK übergeben. Wenn der Benutzer seine Zustimmung ablehnt, löst die Anwendung eine Ausnahme aus, und es wird kein Rückruf für den Schutzdienst durchgeführt. 

```cpp
Consent ConsentDelegateImpl::GetUserConsent(const string& url) {
  //Print the consent URL, ask user to choose
  std::cout << "SDK will connect to: " << url << std::endl;

  std::cout << "1) Accept Always" << std::endl;
  std::cout << "2) Accept" << std::endl;
  std::cout << "3) Reject" << std::endl;
  std::cout << "Select an option: ";
  char input;
  std::cin >> input;

  switch (input)
  {
  case '1':
    return Consent::AcceptAlways;
    break;
  case '2':
    return Consent::Accept;
    break;
  case '3':
    return Consent::Reject;
    break;
  default:
    return Consent::Reject;
  }  
}
```

Zu Test-und Entwicklungszwecken kann eine einfache `ConsentDelegate` implementiert werden, die wie folgt aussieht:

```cpp
Consent ConsentDelegateImpl::GetUserConsent(const string& url) {
  return Consent::AcceptAlways;
}
```

Im Produktionscode ist es jedoch möglicherweise erforderlich, dass der Benutzer je nach Regions-oder Geschäftsanforderungen und-Vorschriften mit einer Wahl zur Zustimmung angezeigt wird. 

## <a name="next-steps"></a>Nächste Schritte

Der Einfachheit halber werden Beispiele, die den Delegaten zeigen, den Tokenabruf durch Aufrufen eines externen Skripts implementieren. Dieses Skript kann durch einen anderen Typ von Skript, eine Open-Source-OAuth2-Bibliothek oder eine benutzerdefinierte OAuth2-Bibliothek ersetzt werden.

- [Abrufen eines Zugriffstokens mithilfe von PowerShell](concept-authentication-acquire-token-ps.md)
- [Abrufen eines Zugriffstokens mithilfe von Python](concept-authentication-acquire-token-py.md)
