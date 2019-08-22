---
title: mip::FileEngine-Klasse
description: 'Dokumentiert die MIP:: fileengine-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 86437533b2451b613231d668857b1402fc9f4272
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885813"
---
# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
Public Konstanten Std::\<Vector Std:: shared_ptr\<sensitivitytypesrulepackage\>\>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
Public Konstanten Std:: shared_ptr\<-Bezeichnung\> getdefaultsensitivitylabel () Konstanten  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
Public Std:: shared_ptr\<Label\> getlabelbyid (Konstanten Std:: String & ID) Konstanten  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Konstanten Std::\<Vector Std:: shared_ptr\<Label\>\>& listsensitivitylabels ()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
Public Konstanten Std:: String & getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getlastpolicyfetchtime () Konstanten  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
öffentliches void-Ereignis "fiatefilehandlerasync" (Konstante Std:: String & inputfilepath, Konstante Std:: String & actualfilepath, bool isauditdiscoveryaktivierte, Konstante Std:\<: shared_ptr fileHandler:\>: Observer & filehandlerobserver , Konst Std:: shared_ptr\<void\>& Kontext, Konstante Std:: shared_ptr\<fileexecutionstate\>& fileexecutionstate)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
öffentliches void-Ereignis "debugfilehandlerasync" (Konstante Std\<:\>: shared_ptr Stream & InputStream, Konstanten Std:: String & actualfilepath, bool isauditdiscoveryaktivierte, Konstante Std:\<: shared_ptr fileHandler:: Observer \>\<\>\<& filehandlerobserver, Konst Std:: shared_ptr void & context, Konstanten Std:: shared_ptr fileexecutionstate & fileexecutionstate) \>  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () Konstanten  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
public bool hasclassificationrules () konstant  |  Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Engine-Einstellungen zurück.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Gibt Folgendes zurück**: Eine Liste der Vertraulichkeits Bezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
**Siehe auch**: [Fileengine:: Settings](class_mip_fileengine_settings.md)).
  
### <a name="getdefaultsensitivitylabel-function"></a>Getdefaultsensitivitylabel-Funktion
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Gibt Folgendes zurück**: Standardmäßige Vertraulichkeits Bezeichnung, falls vorhanden, nullptr, wenn keine Standard Bezeichnung festgelegt ist.
  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
Ruft die Bezeichnung entsprechend der angegebenen ID ab.
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Gibt Folgendes zurück**: Eine URL im Zeichen folgen Format.
  
### <a name="getpolicyfileid-function"></a>Getpolicyfleid-Funktion
Ruft die ID der Richtlinien Datei ab.

  
**Gibt Folgendes zurück**: Eine Zeichenfolge, die die Richtlinien Datei-ID darstellt.
  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.

  
**Gibt Folgendes zurück**: True, wenn die Bezeichnung obligatorisch ist, andernfalls false.
  
### <a name="getlastpolicyfetchtime-function"></a>Getlastpolicyfetchtime-Funktion
Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

  
**Gibt Folgendes zurück**: Der Zeitpunkt, zu dem die Richtlinie zuletzt abgerufen wurde.
  
### <a name="createfilehandlerasync-function"></a>Funktion "kreatefilehandlerasync"
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **inputFilePath**: Die zu öffnende Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **actualFilePath**: Der tatsächliche (nicht temporäre) Dateipfad wird für die Überwachung verwendet. 


* **isauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung aktiviert ist. 


* **fileHandlerObserver**: Eine Klasse, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an den Beobachter zurückgegeben wird.


  
### <a name="createfilehandlerasync-function"></a>Funktion "kreatefilehandlerasync"
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **inputStream**: Ein Stream, der die Datei Daten enthält. 


* **actualFilePath**: Der Pfad zur Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. wird auch verwendet, um die Datei in Audit zu identifizieren. 


* **isauditdiscoveryaktivierte**: gibt an, ob die Überwachungs Ermittlung aktiviert ist. 


* **fileHandlerObserver**: Eine Klasse, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an den Beobachter zurückgegeben wird.


  
### <a name="sendapplicationauditevent-function"></a>Sendapplicationauditevent-Funktion
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **Ebene**: eine Beschreibung der Protokollebene: Info/Fehler/Warnung 


* **eventType:** Beschreibung des Ereignistyps 


* **eventData:** dem Ereignis zugeordnete Daten


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft eine Liste benutzerdefinierter Einstellungen ab.

  
**Gibt Folgendes zurück**: Ein Vektor von benutzerdefinierten Einstellungen
  
### <a name="hasclassificationrules-function"></a>Hasclassificationrules-Funktion
Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.

  
**Gibt Folgendes zurück**: Ein boolescher Wert, der mitteilt, ob in der Richtlinie automatische oder Empfehlungs Regeln vorhanden sind.