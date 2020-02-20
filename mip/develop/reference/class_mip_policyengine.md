---
title: mip::PolicyEngine-Klasse
description: Dokumentiert die MIP::p olicyengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 114b8dedb46a0e86eb73ff1f6fa58de81927b60e
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77489825"
---
# <a name="class-mippolicyengine"></a>mip::PolicyEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Die Einstellungen der Richtlinien-Engine werden angezeigt.
Public Konstanten Std:: Vector\<Std:: shared_ptr\<Bezeichnung\>\>& listsensitivitylabels ()  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
Public Konstanten Std:: Vector\<Std:: shared_ptr\<sensitivitytypesrulepackage\>\>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.
Public Std:: shared_ptr\<Bezeichnung\> getdefaultsensitivitylabel ()  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
Public Std:: shared_ptr\<Bezeichnung\> getlabelbyid (Konstante Std:: String & ID) Konstanten  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Std:: shared_ptr\<policyhandler\> kreatepolicyhandler (bool isauditdiscoveryaktivierte)  |  Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std:: String & getpolicydataxml ()-Konstanten  |  Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std:: String & getsensitivitytypesdataxml () Konstanten  |  Ruft Daten der Vertraulichkeits Typen ab, die die Vertraulichkeits Typen beschreiben, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
Public Konstanten Std:: String & getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
Public Konstanten Std:: String & getsensitivityfleid () Konstanten  |  Ruft die ID der Vertraulichkeits Datei ab.
public bool hasclassificationrules () konstant  |  Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getlastpolicyfetchtime () konstant.  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Die Einstellungen der Richtlinien-Engine werden angezeigt.

  
**Rückgabe**: Einstellungen der Richtlinien-Engine. 
  
**Siehe auch**: MIP::P olicyengine:: Settings
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.

  
**Rückgabe**: Liste der Vertraulichkeitsbezeichnungen.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Rückgabe**: Liste der Vertraulichkeitsbezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
**Siehe auch**: policyengine:: Settings).
  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Rückgabe:** eine URL im Zeichenfolgenformat
  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.

  
**Rückgabe:** TRUE, wenn eine Bezeichnung erforderlich ist; andernfalls FALSE.
  
### <a name="getdefaultsensitivitylabel-function"></a>Getdefaultsensitivitylabel-Funktion
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Rückgabe**: die Standardvertraulichkeitsbezeichnung, sofern vorhanden. Wenn keine Standardbezeichnung festgelegt ist, wird „nullptr“ zurückgegeben.
  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
Ruft die Bezeichnung entsprechend der angegebenen ID ab.
  
### <a name="createpolicyhandler-function"></a>Funktion "kreatepolicyhandler"
Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.

Parameter:  
* **A**: Boolescher Wert, der angibt, ob die Überwachungs Ermittlung aktiviert ist.



  
**Rückgabe**: Richtlinienhandler
Die Anwendung muss das richtlinienhandlerobjekt für die Lebensdauer des Dokuments beibehalten.
  
### <a name="sendapplicationauditevent-function"></a>Sendapplicationauditevent-Funktion
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **Ebene**: der Protokollebene: info/Fehler/Warnung. 


* **eventType**: eine Beschreibung des Ereignis Typs. 


* **EventData**: die Daten, die dem Ereignis zugeordnet sind.


  
### <a name="getpolicydataxml-function"></a>Getpolicydataxml-Funktion
Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.

  
**Gibt Folgendes zurück**: Richtlinien Daten-XML.
  
### <a name="getsensitivitytypesdataxml-function"></a>Getsensitivitytypesdataxml-Funktion
Ruft Daten der Vertraulichkeits Typen ab, die die Vertraulichkeits Typen beschreiben, die dieser Richtlinie zugeordnet sind.

  
**Gibt Folgendes zurück**: Sensitivität Types Data XML.
  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft eine Liste benutzerdefinierter Einstellungen ab.

  
**Gibt Folgendes zurück**: ein Vektor von benutzerdefinierten Einstellungen.
  
### <a name="getpolicyfileid-function"></a>Getpolicyfleid-Funktion
Ruft die ID der Richtlinien Datei ab.

  
**Returns**: eine Zeichenfolge, die die Richtlinien Datei-ID darstellt.
  
### <a name="getsensitivityfileid-function"></a>Getsensitivityfleid-Funktion
Ruft die ID der Vertraulichkeits Datei ab.

  
**Returns**: eine Zeichenfolge, die die Richtlinien Datei-ID darstellt.
  
### <a name="hasclassificationrules-function"></a>Hasclassificationrules-Funktion
Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.

  
**Gibt Folgendes zurück**: ein boolescher Wert, der Aufschluss darüber gibt, ob die Richtlinie automatische oder Empfehlungs Regeln enthält.
  
### <a name="getlastpolicyfetchtime-function"></a>Getlastpolicyfetchtime-Funktion
Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

  
**Returns**: die Uhrzeit, zu der die Richtlinie zuletzt abgerufen wurde.