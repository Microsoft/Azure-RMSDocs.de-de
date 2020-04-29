---
title: 'Konzepte: Zustimmung im MIP-SDK.'
description: Dieser Artikel hilft Ihnen, zu verstehen, wie das MIP SDK Zustimmungs Flows implementiert, damit Benutzer eine Verbindung mit dem RMS-Dienst herstellen können.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: 7025e042d0ded7164b26efbe9b453b4546c5ca05
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81766540"
---
# <a name="microsoft-information-protection-sdk---consent"></a>Microsoft Information Protection SDK: Zustimmung

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

Zu Test-und Entwicklungszwecken kann ein `ConsentDelegate` einfaches implementiert werden, das wie folgt aussieht:

```cpp
Consent ConsentDelegateImpl::GetUserConsent(const string& url) {
  return Consent::AcceptAlways;
}
```

Im Produktionscode ist es jedoch möglicherweise erforderlich, dass der Benutzer je nach Regions-oder Geschäftsanforderungen und-Vorschriften mit einer Wahl zur Zustimmung angezeigt wird. 