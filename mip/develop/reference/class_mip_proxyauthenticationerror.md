---
title: MIP::P roxyauthenticationerror-Klasse
description: Dokumentiert die MIP::p roxyauthenticationerror-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: c0289f9b2f2a8a1163e62e6c6a96e3023f297194
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489621"
---
# <a name="class-mipproxyauthenticationerror"></a>MIP::P roxyauthenticationerror-Klasse 
Fehler bei der Proxy Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Kategorie getCategory () konstant  |  Ruft die Kategorie des Netzwerk Fehlers ab.
öffentliches int32_t getresponsestatus Code () Konstanten  |  Ruft den Statuscode der HTTP-Antwort ab.
Enumeration-Kategorie  |  Kategorie des Netzwerk Fehlers.
  
## <a name="members"></a>Member
  
### <a name="getcategory-function"></a>GetCategory-Funktion
Ruft die Kategorie des Netzwerk Fehlers ab.

  
**Gibt Folgendes zurück**: Kategorie des Netzwerk Fehlers
  
### <a name="getresponsestatuscode-function"></a>Getresponsestatus Code-Funktion
Ruft den Statuscode der HTTP-Antwort ab.

  
**Gibt Folgendes zurück**: Statuscode der HTTP-Antwort, 0, wenn keine
  
### <a name="category-enum"></a>Kategorieenum
 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Unbekannt            | Unbekannter Netzwerkfehler.
Failureresponsecode            | HTTP-Antwort Code zeigt einen Fehler an
Badresponse            | Die HTTP-Antwort konnte nicht gelesen werden.
Nicht expectedresponse            | Die HTTP-Antwort ist abgeschlossen, enthielt jedoch unerwartete Daten.
NoConnection            | Fehler beim Herstellen einer Verbindung.
Proxy            | Proxy Fehler
SSL            | SSL-Fehler
Timeout            | Verbindungs Timeout
Offline            | Der Vorgang erfordert eine Netzwerk Konnektivität.
Throttled            | Fehler beim http-Vorgang aufgrund von Serverdaten Verkehrs Drosselung.
Abgebrochen            | Der http-Vorgang wurde von der Anwendung abgebrochen.
Kategorie des Netzwerk Fehlers.