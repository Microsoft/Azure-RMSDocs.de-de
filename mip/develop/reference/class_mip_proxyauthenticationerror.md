---
title: Klasse proxyauthenticationerror
description: 'Dokumentiert die proxyauthenticationerror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 0da14f6a13632c0bf45ac3a409b0033a9ee1c603
ms.sourcegitcommit: dc50f9a6c2f66544893278a7fd16dff38eef88c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88564415"
---
# <a name="class-proxyauthenticationerror"></a>Klasse proxyauthenticationerror 
Fehler bei der Proxy Authentifizierung.
  
## <a name="summary"></a>Zusammenfassung

| Member                                       | Beschreibungen
|-----------------------------------------------|---------------------------------------------
| öffentliche Kategorie getCategory () konstant           |  Ruft die Kategorie des Netzwerk Fehlers ab.
| öffentliches int32_t getresponsestatus Code () Konstanten  |  Ruft den Statuscode der HTTP-Antwort ab.
| Enumeration-Kategorie                                 |  Kategorie des Netzwerk Fehlers.
  
## <a name="members"></a>Member
  
### <a name="getcategory-function"></a>GetCategory-Funktion

Ruft die Kategorie des Netzwerk Fehlers ab.

**Gibt Folgendes zurück**: Kategorie des Netzwerk Fehlers
  
### <a name="getresponsestatuscode-function"></a>Getresponsestatus Code-Funktion

Ruft den Statuscode der HTTP-Antwort ab.

**Gibt Folgendes zurück**: Statuscode der HTTP-Antwort, 0, wenn keine
  
### <a name="category-enum"></a>Kategorieenum

Kategorie des Netzwerk Fehlers.

| Werte                   | Beschreibungen
|--------------------------|---------------------------------------------
| Unknown                  | Unbekannter Netzwerkfehler.
| Failureresponsecode      | HTTP-Antwort Code zeigt einen Fehler an
| Badresponse              | Die HTTP-Antwort konnte nicht gelesen werden.
| Nicht expectedresponse       | Die HTTP-Antwort ist abgeschlossen, enthielt jedoch unerwartete Daten.
| NoConnection             | Fehler beim Herstellen einer Verbindung.
| Proxy                    | Proxy Fehler
| SSL                      | SSL-Fehler
| Timeout                  | Timeout bei Verbindung
| Offline                  | Der Vorgang erfordert eine Netzwerk Konnektivität.
| Gedrosselt                | Fehler beim http-Vorgang aufgrund von Serverdaten Verkehrs Drosselung.
| Abgebrochen                | Der http-Vorgang wurde von der Anwendung abgebrochen.
