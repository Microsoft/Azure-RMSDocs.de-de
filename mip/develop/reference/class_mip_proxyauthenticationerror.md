---
title: Klasse proxyauthenticationerror
description: 'Dokumentiert die proxyauthenticationerror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: d4468fe243f7120630d0a34d453ff4e9a5bf6527
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567079"
---
# <a name="class-proxyauthenticationerror"></a>Klasse proxyauthenticationerror 
Fehler bei der Proxy Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Kategorie getCategory () konstant  |  Ruft die Kategorie des Netzwerk Fehlers ab.
öffentliches int32_t getresponsestatus Code () Konstanten  |  Ruft den Statuscode der HTTP-Antwort ab.
Enumeration-Kategorie  |  Kategorie des Netzwerk Fehlers.
  
## <a name="members"></a>Members
  
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
Timeout            | Timeout bei Verbindung
Offline            | Der Vorgang erfordert eine Netzwerk Konnektivität.
Gedrosselt            | Fehler beim http-Vorgang aufgrund von Serverdaten Verkehrs Drosselung.
Abgebrochen            | Der http-Vorgang wurde von der Anwendung abgebrochen.

Kategorie des Netzwerk Fehlers.