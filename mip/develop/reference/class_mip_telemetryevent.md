---
title: Class telemetryevent
description: 'Dokumentiert die telemetryevent:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 8776eff24a889a1132fc71d11c38b02c49822263
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224950"
---
# <a name="class-telemetryevent"></a>Class telemetryevent 
Ein einzelnes telemetrieereignis.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetName() const  |  Ereignis Namen erhalten.
öffentliches Eventlevel GetLevel () konstant  |  Get-Ereignis Ebene, die angibt, ob es sich um die erforderlichen Dienst Daten (nsd) handelt.
Public Konstanten Std:: Chrono:: steady_clock:: time_point& getstarttime () konstant  |  Ereignis Startzeit erhalten.
öffentliches void AddProperty-Objekt (konstant Std:: shared_ptr \<EventProperty\>& prop)  |  Fügen Sie dem-Ereignis eine Eigenschaft hinzu.
öffentliches void AddProperty (Konstante Std:: String& Name, boolescher Wert)  |  Fügen Sie dem-Ereignis eine boolesche Eigenschaft hinzu.
public void AddProperty (Konstanten Std:: String& Name, Double value, PII PII)  |  Fügen Sie dem-Ereignis eine Double-Eigenschaft hinzu.
public void AddProperty (Konstanten Std:: String& Name, int64_t Wert, PII PII)  |  Fügen Sie dem-Ereignis eine Int64-Eigenschaft hinzu.
public void AddProperty (Konstante Std:: String& Name, Konstanten Std:: String& Wert, PII PII)  |  Fügen Sie dem-Ereignis eine Zeichen folgen Eigenschaft hinzu.
öffentliches void addauditonlyproperty (Konst Std:: String& Name, Konstanten Std:: String& Wert)  |  Fügen Sie dem-Ereignis eine schreibgeschützte String-Eigenschaft hinzu.
Public Std:: Vector \<std::shared_ptr\<EventProperty\> \> GetProperties () Konstanten  |  Alle Ereignis Eigenschaften erhalten.
Public Std:: shared_ptr \<EventProperty\> GetProperty (Konst Std:: String& Name)  |  Eigenschaft mit dem angegebenen Namen, sofern vorhanden, erhalten.
  
## <a name="members"></a>Member
  
### <a name="getname-function"></a>GetName-Funktion
Ereignis Namen erhalten.

  
**Gibt Folgendes zurück**: Ereignis Name
  
### <a name="getlevel-function"></a>GetLevel-Funktion
Get-Ereignis Ebene, die angibt, ob es sich um die erforderlichen Dienst Daten (nsd) handelt.

  
**Returns**: Ereignis Ebene
  
### <a name="getstarttime-function"></a>Getstarttime-Funktion
Ereignis Startzeit erhalten.

  
**Gibt Folgendes zurück**: Ereignis Start Zeit
  
### <a name="addproperty-function"></a>AddProperty-Funktion
Fügen Sie dem-Ereignis eine Eigenschaft hinzu.

Parameter:  
* **Prop**: hinzu zufügende Eigenschaft


  
### <a name="addproperty-function"></a>AddProperty-Funktion
Fügen Sie dem-Ereignis eine boolesche Eigenschaft hinzu.

Parameter:  
* **Name**: Eigenschaftsname 


* **Wert**: Eigenschafts Wert


  
### <a name="addproperty-function"></a>AddProperty-Funktion
Fügen Sie dem-Ereignis eine Double-Eigenschaft hinzu.

Parameter:  
* **Name**: Eigenschaftsname 


* **Wert**: Eigenschafts Wert 


* **PII**: PII-Klassifizierung


  
### <a name="addproperty-function"></a>AddProperty-Funktion
Fügen Sie dem-Ereignis eine Int64-Eigenschaft hinzu.

Parameter:  
* **Name**: Eigenschaftsname 


* **Wert**: Eigenschafts Wert 


* **PII**: PII-Klassifizierung


  
### <a name="addproperty-function"></a>AddProperty-Funktion
Fügen Sie dem-Ereignis eine Zeichen folgen Eigenschaft hinzu.

Parameter:  
* **Name**: Eigenschaftsname 


* **Wert**: Eigenschafts Wert 


* **PII**: PII-Klassifizierung


  
### <a name="addauditonlyproperty-function"></a>Addauditonlyproperty-Funktion
Fügen Sie dem-Ereignis eine schreibgeschützte String-Eigenschaft hinzu.

Parameter:  
* **Name**: Eigenschaftsname 


* **Wert**: Eigenschafts Wert


Eine nur für die Überprüfung geschützte Eigenschaft enthält vertrauliche Informationen und darf nicht in Datei Protokolle oder in eine Pipeline geschrieben werden, außer für die Überwachung, bis Sie manuell bereinigt wird.
  
### <a name="getproperties-function"></a>GetProperties-Funktion
Alle Ereignis Eigenschaften erhalten.

  
**Returns**: Ereignis Eigenschaften
  
### <a name="getproperty-function"></a>GetProperty-Funktion
Eigenschaft mit dem angegebenen Namen, sofern vorhanden, erhalten.

Parameter:  
* **Name**: Name der Get-Eigenschaft



  
**Gibt Folgendes zurück**: Eigenschaft mit dem angegebenen Namen oder nullptr, wenn keine