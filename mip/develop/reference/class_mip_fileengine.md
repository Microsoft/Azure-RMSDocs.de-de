---
title: Klassen-fileengine
description: 'Dokumentiert die fileengine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 5b9c3d33fe538810975d4f156aef36280fdd4bda
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215322"
---
# <a name="class-fileengine"></a>Klassen-fileengine 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
Public Konstanten Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
Public Konstanten Std:: shared_ptr \<Label\> getdefaultsensitivitylabel () Konstanten  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
Public Std:: shared_ptr \<Label\> getlabelbyid (Konstanten Std:: String& ID) konstant  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Konstanten Std:: Vector \<std::shared_ptr\<Label\> \> listsensitivitylabels ()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
Public Konstanten Std:: String& getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
Public Konstanten Std:: String& getsensitivityfleid () Konstanten  |  Ruft die ID der Vertraulichkeits Datei ab.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.
Public Std:: Chrono:: time_point \<std::chrono::system_clock\> getlastpolicyfetchtime () Konstanten  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
Public Konstanten Std:: String& getpolicydataxml ()-Konstanten  |  Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.
Public Std:: shared_ptr \<AsyncControl\> kreatefilehandlerasync (Konstante Std:: Zeichenfolge& inputfilepath, Konstante Std:: String& actualfilepath, bool isauditdiscoveryaktivierte, Konstante Std:: shared_ptr \<FileHandler::Observer\>& filehandlerobserver, Konst Std:: shared_ptr \<void\>& context, Konstante Std:: shared_ptr \<FileExecutionState\>& fileexecutionstate, bool isgetsensitivitylabelauditdiscoveryaktivierte)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
Public Std:: shared_ptr \<AsyncControl\> kreatefilehandlerasync (Konstante Std:: shared_ptr \<Stream\>& InputStream, Konstanten Std:: String& actualfilepath, bool isauditdiscoveryaktivierte, Konstante Std:: shared_ptr \<FileHandler::Observer\>& filehandlerobserver, Konstanten Std:: shared_ptr \<void\>& context, Konstante Std:: shared_ptr \<FileExecutionState\>& fileexecutionstate, bool isgetsensitivitylabelauditdiscoveryaktivierte)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
public bool hasclassificationrules () konstant  |  Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Engine-Einstellungen zurück.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Returns**: eine Liste von Vertraulichkeits Bezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
**Siehe auch**: fileengine:: Settings).
  
### <a name="getdefaultsensitivitylabel-function"></a>Getdefaultsensitivitylabel-Funktion
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Rückgabe**: die Standardvertraulichkeitsbezeichnung, sofern vorhanden. Wenn keine Standardbezeichnung festgelegt ist, wird „nullptr“ zurückgegeben.
  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
Ruft die Bezeichnung entsprechend der angegebenen ID ab.
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Rückgabe:** eine URL im Zeichenfolgenformat
  
### <a name="getpolicyfileid-function"></a>Getpolicyfleid-Funktion
Ruft die ID der Richtlinien Datei ab.

  
**Returns**: eine Zeichenfolge, die die Richtlinien Datei-ID darstellt.
  
### <a name="getsensitivityfileid-function"></a>Getsensitivityfleid-Funktion
Ruft die ID der Vertraulichkeits Datei ab.

  
**Returns**: eine Zeichenfolge, die die Richtlinien Datei-ID darstellt.
  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.

  
**Rückgabe:** TRUE, wenn eine Bezeichnung erforderlich ist; andernfalls FALSE.
  
### <a name="getlastpolicyfetchtime-function"></a>Getlastpolicyfetchtime-Funktion
Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

  
**Returns**: die Uhrzeit, zu der die Richtlinie zuletzt abgerufen wurde.
  
### <a name="getpolicydataxml-function"></a>Getpolicydataxml-Funktion
Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.

  
**Gibt Folgendes zurück**: Richtlinien Daten-XML.
  
### <a name="createfilehandlerasync-function"></a>Funktion "kreatefilehandlerasync"
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **inputfilepath**: die Datei, die geöffnet werden soll. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **actualfilepath**: der eigentliche (nicht temporäre) Dateipfad wird für die Überwachung verwendet. 


* **isauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung aktiviert ist. 


* **fileHandlerObserver:** eine Klasse, die die FileHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an den Beobachter zurückgegeben wird. 


* **isgetsensitivitylabelauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung für "getsensitivitylabel" ausgelöst wird. 



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="createfilehandlerasync-function"></a>Funktion "kreatefilehandlerasync"
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **inputStream:** ein Stream, der die Dateidaten enthält 


* **actualfilepath**: der Pfad zur Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. wird auch verwendet, um die Datei in Audit zu identifizieren. 


* **isauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung aktiviert ist. 


* **fileHandlerObserver:** eine Klasse, die die FileHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an den Beobachter zurückgegeben wird. 


* **isgetsensitivitylabelauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung für "getsensitivitylabel" ausgelöst wird. 



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="sendapplicationauditevent-function"></a>Sendapplicationauditevent-Funktion
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **level:** Beschreibung der Protokollebene: Information/Fehler/Warnung 


* **eventType:** Beschreibung des Ereignistyps 


* **eventData:** dem Ereignis zugeordnete Daten


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft eine Liste benutzerdefinierter Einstellungen ab.

  
**Gibt Folgendes zurück**: ein Vektor von benutzerdefinierten Einstellungen.
  
### <a name="hasclassificationrules-function"></a>Hasclassificationrules-Funktion
Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.

  
**Gibt Folgendes zurück**: ein boolescher Wert, der Aufschluss darüber gibt, ob die Richtlinie automatische oder Empfehlungs Regeln enthält.