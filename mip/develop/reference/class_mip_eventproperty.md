---
title: Event Property-Klasse
description: 'Dokumentiert die eventproperty:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 5ee28e454aa5d7854c572df8ef6e4642482c1104
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224964"
---
# <a name="class-eventproperty"></a>Event Property-Klasse 
Eine einzelne Audit/Telemetry-Eigenschaft.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public eventpropertytype GetPropertyType () Konstanten  |  Hiermit wird der zugrunde liegende Datentyp für diese Eigenschaft angezeigt.
public const std::string& GetName() const  |  Gibt den Namen der Eigenschaft an.
Public PII getpii () konstant  |  Erhalten Sie ggf. eine PII-Klassifizierung (persönlich identifizierbare Informationen).
public bool isauditonly () konstant  |  Hiermit wird angezeigt, ob diese Eigenschaft auf die Überwachungs Pipeline beschränkt ist.
öffentliches Double GetDouble () konstant  |  Eigenschafts Wert (Double)
Public int64_t GetInt64 () konstant  |  Get-Eigenschafts Wert (Int64)
Public Konstanten Std:: String& GetString () Konstanten  |  Get-Eigenschafts Wert (Zeichenfolge)
  
## <a name="members"></a>Member
  
### <a name="getpropertytype-function"></a>GetPropertyType-Funktion
Hiermit wird der zugrunde liegende Datentyp für diese Eigenschaft angezeigt.

  
**Returns**: zugrunde liegender Datentyp
  
### <a name="getname-function"></a>GetName-Funktion
Gibt den Namen der Eigenschaft an.

  
**Returns**: Name der Eigenschaft
  
### <a name="getpii-function"></a>Getpii-Funktion
Erhalten Sie ggf. eine PII-Klassifizierung (persönlich identifizierbare Informationen).

  
**Gibt Folgendes zurück**: PII-Klassifizierung
  
### <a name="isauditonly-function"></a>Isauditonly-Funktion
Hiermit wird angezeigt, ob diese Eigenschaft auf die Überwachungs Pipeline beschränkt ist.

  
**Gibt zurück**: ob diese Eigenschaften auf die Überwachungs Pipeline beschränkt sind oder nicht, wenn dies zutrifft, enthält die Eigenschaft vertrauliche Informationen und darf nicht in Datei Protokolle oder in eine Pipeline geschrieben werden, außer für die Überwachung, bis Sie manuell bereinigt wird.
  
### <a name="getdouble-function"></a>GetDouble-Funktion
Eigenschafts Wert (Double)

  
**Gibt Folgendes zurück**: Eigenschafts Wert
  
### <a name="getint64-function"></a>GetInt64-Funktion
Get-Eigenschafts Wert (Int64)

  
**Gibt Folgendes zurück**: Eigenschafts Wert
  
### <a name="getstring-function"></a>GetString-Funktion
Get-Eigenschafts Wert (Zeichenfolge)

  
**Gibt Folgendes zurück**: Eigenschafts Wert