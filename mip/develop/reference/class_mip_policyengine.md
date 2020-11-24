---
title: Klasse policyengine
description: 'Dokumentiert die policyengine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 733e1ced7a1f5ca1ec8d47709ef4c364c04e37a5
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566671"
---
# <a name="class-policyengine"></a>Klasse policyengine 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Einstellungen der Richtlinien-Engine ab.
Public Konstanten Std:: Vector \<std::shared_ptr\<Label\> \>& listsensitivitylabels ()  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
Public Konstanten Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.
public std::shared_ptr\<Label\> GetDefaultSensitivityLabel()  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
Public Std:: shared_ptr \<Label\> getlabelbyid (Konstanten Std:: String& ID) konstant  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Std:: shared_ptr \<PolicyHandler\> kreatepolicyhandler (bool isauditdiscoveryaktivierte)  |  Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std:: String& gettenantid () Konstanten  |  Ruft die der Engine zugeordnete Mandanten-ID ab.
Public Konstanten Std:: String& getpolicydataxml ()-Konstanten  |  Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std:: String& getsensitivitytypesdataxml () Konstanten  |  Ruft Daten der Vertraulichkeits Typen ab, die die Vertraulichkeits Typen beschreiben, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
Public Konstanten Std:: String& getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
Public Konstanten Std:: String& getsensitivityfleid () Konstanten  |  Ruft die ID der Vertraulichkeits Datei ab.
public bool hasclassificationrules () konstant  |  Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.
öffentliches classificationscheme getclassificationscheme () konstant  |  Ruft ab, ob die Richtlinie basierend auf der aktuellen klassifiziert werden soll.
Public Std:: Chrono:: time_point \<std::chrono::system_clock\> getlastpolicyfetchtime () Konstanten  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
Public uint32_t GetWxpMetadataVersion () konstant  |  Ruft die empfohlene WXP-Metadatenversion (Windows, Excel, PowerPoint) ab, die derzeit 0 für die alte Verifizierung 1 für die Co-Authoring-aktivierte Version ist.
  
## <a name="members"></a>Members
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Einstellungen der Richtlinien-Engine ab.

  
**Rückgabe**: Einstellungen der Richtlinien-Engine. 
  
**Siehe auch**: MIP::P olicyengine:: Settings
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.

  
**Returns**: eine Liste von Vertraulichkeits Bezeichnungen.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Returns**: eine Liste von Vertraulichkeits Bezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
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


  
### <a name="gettenantid-function"></a>Gettenantid-Funktion
Ruft die der Engine zugeordnete Mandanten-ID ab.

  
**Gibt Folgendes zurück**: Mandanten-ID
  
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
  
### <a name="getclassificationscheme-function"></a>Getclassificationscheme-Funktion
Ruft ab, ob die Richtlinie basierend auf der aktuellen klassifiziert werden soll.

  
**Gibt Folgendes zurück**: einen Engine-Typ, der dem Kunden mitteilt, welches Modul verwendet werden soll.
  
### <a name="getlastpolicyfetchtime-function"></a>Getlastpolicyfetchtime-Funktion
Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

  
**Returns**: die Uhrzeit, zu der die Richtlinie zuletzt abgerufen wurde.
  
### <a name="getwxpmetadataversion-function"></a>GetWxpMetadataVersion-Funktion
Ruft die empfohlene WXP-Metadatenversion (Windows, Excel, PowerPoint) ab, die derzeit 0 für die alte Verifizierung 1 für die Co-Authoring-aktivierte Version ist.

  
**Gibt Folgendes zurück**: Uint32_t int, welche Version von Metadaten der Mandant für WXP-Dateien unterstützt.