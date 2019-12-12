---
title: mip::FileEngine-Klasse
description: 'Dokumentiert die MIP:: fileengine-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 8f1ef9e1ca46037243e170a59717be74954d4cb1
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73560280"
---
# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
Public Konstanten Std:: Vector\<Std:: shared_ptr\<sensitivitytypesrulepackage\>\>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
Public Konstanten Std:: shared_ptr\<Bezeichnung\> getdefaultsensitivitylabel () Konstanten  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
Public Std:: shared_ptr\<Bezeichnung\> getlabelbyid (Konstante Std:: String & ID) Konstanten  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Konstanten Std:: Vector\<Std:: shared_ptr\<Bezeichnung\>\>& listsensitivitylabels ()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
Public Konstanten Std:: String & getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
Public Konstanten Std:: String & getsensitivityfleid () Konstanten  |  Ruft die ID der Vertraulichkeits Datei ab.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getlastpolicyfetchtime () konstant.  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
öffentliches void-Ereignis "kreatefilehandlerasync" (Konstante Std:: String & inputfilepath, Konstante Std:: String & actualfilepath, bool isauditdiscoveryaktivierte, Konstante Std:: shared_ptr\<fileHandler:: Observer\>& filehandlerobserver, Konstanten Std:: shared_ptr\<void\>& Kontext, Konstante Std:: shared_ptr\<fileexecutionstate\>& fileexecutionstate)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
öffentliches void-Objekt "deatefilehandlerasync" (Konstante Std:: shared_ptr\<Stream\>& InputStream, Konstante Std:: String & actualfilepath, bool isauditdiscoveryaktivierte, Konst Std:: shared_ptr\<fileHandler:: Observer\>& filehandlerobserver, Konstanten Std:: shared_ptr\<void\>& context, Konstante Std:: shared_ptr\<fileexecutionstate\>& fileexecutionstate)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
public bool hasclassificationrules () konstant  |  Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Engine-Einstellungen zurück.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Rückgabe**: Liste der Vertraulichkeitsbezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
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
  
### <a name="createfilehandlerasync-function"></a>Funktion "kreatefilehandlerasync"
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **inputfilepath**: die Datei, die geöffnet werden soll. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **actualfilepath**: der eigentliche (nicht temporäre) Dateipfad wird für die Überwachung verwendet. 


* **isauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung aktiviert ist. 


* **filehandlerobserver**: eine Klasse, die die fileHandler:: Observer-Schnittstelle implementiert. 


* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
### <a name="createfilehandlerasync-function"></a>Funktion "kreatefilehandlerasync"
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **inputStream:** ein Stream, der die Dateidaten enthält 


* **actualfilepath**: der Pfad zur Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. wird auch verwendet, um die Datei in Audit zu identifizieren. 


* **isauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung aktiviert ist. 


* **filehandlerobserver**: eine Klasse, die die fileHandler:: Observer-Schnittstelle implementiert. 


* **context**: Clientkontext, der verdeckt an den Beobachter zurückgegeben wird.


  
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