---
title: Klasse proxyauthenticationerror
description: 'Dokumentiert die proxyauthenticationerror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 04915e74cc09f271a2ca3bb256b906bc442bb3fd
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214302"
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

Kategorie des Netzwerk Fehlers.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Unbekannt            | Unbekannter Netzwerkfehler.
Failureresponsecode            | HTTP-Antwort Code zeigt einen Fehler an
Badresponse            | Die HTTP-Antwort konnte nicht gelesen werden.
Nicht expectedresponse            | Die HTTP-Antwort ist abgeschlossen, enthielt jedoch unerwartete Daten.
NoConnection            | Fehler beim Herstellen einer Verbindung.
Proxy            | Proxy Fehler
SSL            | SSL-Fehler
Timeout            | Timeout bei Verbindung
Offline            | Der Vorgang erfordert eine Netzwerk Konnektivität.
Gedrosselt            | Fehler beim http-Vorgang aufgrund von Serverdaten Verkehrs Drosselung.
Abgebrochen            | Der http-Vorgang wurde von der Anwendung abgebrochen.
