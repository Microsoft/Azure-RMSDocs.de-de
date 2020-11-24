---
title: 'Konzepte: die Kernkonzepte in der MIP SDK-Proxy Unterstützung'
description: In diesem Artikel erfahren Sie, wie Sie die Proxy Unterstützung im MIP SDK verstehen.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 07/29/2020
ms.author: tommos
ms.openlocfilehash: fdbcf9d618612021a971af34380b65dc062c2802
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567916"
---
# <a name="microsoft-information-protection-sdk---proxy-support"></a>Microsoft Information Protection SDK-Proxy Unterstützung

## <a name="proxies-and-the-mip-sdk"></a>Proxys und MIP SDK

Im MIP SDK werden heute nicht transparente Proxys nur unter Windows unterstützt.

* Der **transparente Proxy** verweist auf einen beliebigen Proxytyp, der keine Client seitige Konfiguration erfordert, einschließlich expliziter oder automatisch ermittelter Einstellungen.
* Der **authentifizierte Proxy** bezieht sich auf einen beliebigen Proxytyp, der erfordert, dass der Aufrufer authentifiziert wird.
* Die automatische Ermittlung von **Proxys** bezieht sich auf Proxys oder Einstellungen, die mithilfe von Web Proxy AutoDiscovery (WPAD) gefunden werden
* Der **explizite Proxy** verweist auf einen Proxy, der direkt für das Betriebssystem oder die Anwendung bereitgestellt wird.
  
| Plattform        | Transparenter Proxy | Authentifizierte Proxys | Automatische Proxy Ermittlung | Expliziter Proxy |
| --------------- | ----------------- | --------------------- | -------------------- | -------------- |
| **Windows**     | Unterstützt         | Nicht unterstützt         | Unterstützt            | Unterstützt      |
| **Linux (alle)** | Unterstützt         | Nicht unterstützt         | Nicht unterstützt        | Nicht unterstützt  |
| ****       | Unterstützt         | Nicht unterstützt         | Nicht unterstützt        | Nicht unterstützt  |
| **Android**     | Unterstützt         | Nicht unterstützt         | Nicht unterstützt        | Nicht unterstützt  |
| **iOS**         | Unterstützt         | Nicht unterstützt         | Nicht unterstützt        | Nicht unterstützt  |

## <a name="proxies-on-windows"></a>Proxys unter Windows

MIP SDK-Anwendungen, die unter Windows ausgeführt werden, verwenden WinHTTP für den Zugriff auf das Netzwerk. Die WinHTTP-Konfigurationseinstellung ist unabhängig von den Proxy Einstellungen für den Internet browsen von Windows Internet (WinInet) und kann nur mithilfe der folgenden Ermittlungsmethoden einen Proxy Server ermitteln:

* AutoDiscovery-Methoden:
  * Transparenter Proxy
  * WebProxy-AutoDiscovery-Protokoll (WPAD)
* Manuelle Konfiguration statischer Proxys:
  * WinHTTP-Konfiguration mithilfe des netsh-Befehls

Weitere Informationen zum Konfigurieren von WinHTTP finden Sie in der [WinHTTP-Dokumentation](/windows/win32/winhttp/winhttp-start-page).

## <a name="proxies-on-other-platforms"></a>Proxys auf anderen Plattformen

MIP SDK unterstützt keine vollständig transparenten Proxys eines beliebigen Typs auf nicht-Windows-Plattformen. Wenn diese Funktion erforderlich ist, finden Sie weitere Informationen in den Abschnitten benutzerdefinierter HTTP-Delegat und Problem Umgehung.

## <a name="custom-http-delegate"></a>Custom http-Delegat

Das Microsoft Information Protection SDK unterstützt die Implementierung eines benutzerdefinierten HTTP-Delegaten, der den Standard-HTTP-Stapel des SDK überschreiben kann. Wenn keine Features vorhanden sind oder eine bestimmte HTTP-Implementierung erforderlich ist, kann dieser Delegat implementiert werden, indem eine neue Klasse hinzugefügt wird, die erbt [`mip::HttpDelegate`](./reference/class_mip_httpdelegate.md) .

Diese von `mip::HttpDelegate` abgeleitete Klasse wird über Folgendes festgelegt `mip::FileProfile::Settings` :

```cpp
std::shared_ptr<MyHttpDelegate> httpDelegate = std::make_shared<MyHttpDelegate>();
            
FileProfile::Settings profileSettings(mMipContext,
    mip::CacheStorageType::OnDisk,
    std::make_shared<sample::consent::ConsentDelegateImpl>(),
    std::make_shared<FileProfileObserver>());

profileSettings.SetHttpDelegate(httpDelegate);
```

## <a name="other-workarounds"></a>Weitere Problem Umgehungen

Wenn ein benutzerdefinierter HTTP-Delegat keine Option ist, muss der Proxy umgangen werden, und die direkte Netzwerk Konnektivität für die MIP-Bezeichnung und die Schutz Endpunkte sowie die Azure Active Directory werden zugelassen. Wenn die Überwachungs [Protokollierung](/azure/information-protection/reports-aip) gewünscht ist, ist auch der Endpunkt für die Überwachungs Protokollierung erforderlich.

| Endpunkt           | Hostname                                                                                                                                                                |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Schutzdienst | https://api.aadrm.com                                                                                                                                                   |
| Richtlinie             | https:// \* . Protection.Outlook.com                                                                                                                                       |
| Überwachungsprotokollierung      | https:// \* . Events.Data.Microsoft.com, https:// \* . Aria.Microsoft.com (nur IOS)                                                                                          |
| Authentication     | [Lesen Sie Azure AD Dokumentation.](/azure/active-directory/develop/authentication-national-cloud#azure-ad-authentication-endpoints) |