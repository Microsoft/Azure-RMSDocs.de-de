---
title: Klasse proxyauthenticationerror
description: 'Dokumentiert die proxyauthenticationerror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 2787403c387bbe31b559e069104cb2af28dd0e6a
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764580"
---
# <a name="class-proxyauthenticationerror"></a>Klasse proxyauthenticationerror 
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
Unknown            | Unbekannter Netzwerkfehler.
Failureresponsecode            | HTTP-Antwort Code zeigt einen Fehler an
Badresponse            | Die HTTP-Antwort konnte nicht gelesen werden.
Nicht expectedresponse            | Die HTTP-Antwort ist abgeschlossen, enthielt jedoch unerwartete Daten.
NoConnection            | Fehler beim Herstellen einer Verbindung.
Proxy            | Proxy Fehler
SSL            | SSL-Fehler
Timeout            | Verbindungs Timeout
Offline            | Der Vorgang erfordert eine Netzwerk Konnektivität.
Gedrosselt            | Fehler beim http-Vorgang aufgrund von Serverdaten Verkehrs Drosselung.
Abgebrochen            | Der http-Vorgang wurde von der Anwendung abgebrochen.
Kategorie des Netzwerk Fehlers.