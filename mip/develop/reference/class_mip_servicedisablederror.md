---
title: Class servicedisablederror
description: 'Dokumentiert die servicedisablederror:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 3dc6d73f12dc1512d1850d465a966e99d13b52c9
ms.sourcegitcommit: dc50f9a6c2f66544893278a7fd16dff38eef88c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88564452"
---
# <a name="class-servicedisablederror"></a>Class servicedisablederror

Der Benutzer konnte aufgrund eines deaktivierten diensdienstanbieter keinen Zugriff auf den Inhalt erhalten.
  
## <a name="summary"></a>Zusammenfassung

| Member                          | Beschreibungen
|----------------------------------|--------------------------------------------------------
| Public Block GetExtent () konstant  | Ruft den Umfang ab, für den der Dienst deaktiviert ist.
| Aufzählungs Block                      | Beschreibt den Umfang, für den der Dienst deaktiviert ist.
  
## <a name="members"></a>Member
  
### <a name="getextent-function"></a>GetExtent-Funktion
Ruft den Umfang ab, für den der Dienst deaktiviert ist.

**Gibt**den Wert zurück, für den der Dienst deaktiviert ist.
  
### <a name="extent-enum"></a>Block-Aufzählung

Beschreibt den Umfang, für den der Dienst deaktiviert ist.

| Werte   | Beschreibungen
|----------|---------------------------------------
| Benutzer     | Der Dienst ist für den Benutzer deaktiviert.
| Sicherungsmedium   | Der Dienst ist für das Gerät deaktiviert.
| Plattform | Der Dienst ist für die Plattform deaktiviert.
| Tenant   | Der Dienst ist für den Mandanten deaktiviert.
