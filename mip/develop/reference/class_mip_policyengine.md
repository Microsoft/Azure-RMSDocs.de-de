---
title: Klasse policyengine
description: 'Dokumentiert die policyengine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 10f913029af2be9f0430c55b8296269eb04beb7b
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98213435"
---
# <a name="class-policyengine"></a>Klasse policyengine 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Einstellungen der Richtlinien-Engine ab.
Public Konstanten Std:: Vector \<std::shared_ptr\<Label\> \> listsensitivitylabels (Konstanten Std:: Vector \<std::string\>& contentformats)  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Bezeichnungen entsprechend den bereitgestellten contentformats auf.
Public Konstanten Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
public bool islabelingrequired (Konstanten Std:: String& contentformat) konstant  |  Überprüft, ob die Richtlinie festlegt, dass ein Inhalt entsprechend dem bereitgestellten contentformat bezeichnet werden muss.
Public Konstante Std:: shared_ptr \<Label\> getdefaultsensitivitylabel (Konstanten Std:: String& contentformat) konstant  |  Die standardmäßige Vertraulichkeits Bezeichnung gemäß dem bereitgestellten contentformat-Wert erhalten.
Public Std:: shared_ptr \<Label\> getlabelbyid (Konstanten Std:: String& ID) konstant  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Std:: shared_ptr \<PolicyHandler\> kreatepolicyhandler (bool isauditdiscoveryaktivierte, bool isgetsensitivitylabelauditdiscoveryaktivierte)  |  Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std:: String& gettenantid () Konstanten  |  Ruft die der Engine zugeordnete Mandanten-ID ab.
Public Konstanten Std:: String& getpolicydataxml ()-Konstanten  |  Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std:: String& getsensitivitytypesdataxml () Konstanten  |  Ruft Daten der Vertraulichkeits Typen ab, die die Vertraulichkeits Typen beschreiben, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
Public Konstanten Std:: String& getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
Public Konstanten Std:: String& getsensitivityfleid () Konstanten  |  Ruft die ID der Vertraulichkeits Datei ab.
public bool hasclassificationrules (Konstanten Std:: Vector \<std::string\>& contentformats) konstant  |  Ruft ab, ob die Richtlinie gemäß den bereitgestellten contentformats über automatische oder Empfehlungs Regeln verfügt.
Public Std:: Chrono:: time_point \<std::chrono::system_clock\> getlastpolicyfetchtime () Konstanten  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
Public uint32_t GetWxpMetadataVersion () konstant  |  Ruft die empfohlene WXP-Metadatenversion (Word, Excel, PowerPoint) ab, die derzeit 0 für die alte Verifizierung 1 für die Co-Authoring-aktivierte Version ist.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Einstellungen der Richtlinien-Engine ab.

  
**Rückgabe**: Einstellungen der Richtlinien-Engine. 
  
**Siehe auch**: MIP::P olicyengine:: Settings
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Bezeichnungen entsprechend den bereitgestellten contentformats auf.

Parameter:  
* **contentformats**: contentformats-Vektor von Formaten zum Filtern der Vertraulichkeits Bezeichnungen, wie z. b. "file", "Email" usw. Legen Sie contentformats auf einen leeren Vektor fest, um die Vertraulichkeits Bezeichnungen nach den Standardformaten zu filtern.



  
**Returns**: eine Liste von Vertraulichkeits Bezeichnungen.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Returns**: eine Liste von Vertraulichkeits Bezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
**Siehe auch**: policyengine:: Settings).
  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Rückgabe:** eine URL im Zeichenfolgenformat
  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Inhalt entsprechend dem bereitgestellten contentformat bezeichnet werden muss.

Parameter:  
* **contentformat**: das zu filternde Format, wenn bestimmt wird, ob eine Bezeichnung erforderlich ist: Beispiel: "file", "Email" usw. Legen Sie contentformat auf eine leere Zeichenfolge fest, um zu bestimmen, ob eine Bezeichnung für das Standardformat erforderlich ist.



  
**Rückgabe:** TRUE, wenn eine Bezeichnung erforderlich ist; andernfalls FALSE.
  
### <a name="getdefaultsensitivitylabel-function"></a>Getdefaultsensitivitylabel-Funktion
Die standardmäßige Vertraulichkeits Bezeichnung gemäß dem bereitgestellten contentformat-Wert erhalten.

Parameter:  
* **contentformat**: das zu filternde Format beim Abrufen der Standard Sensitivität-Bezeichnung: Beispiel: "file", "Email" usw. Legen Sie contentformat auf eine leere Zeichenfolge fest, um die standardmäßige Vertraulichkeits Bezeichnung für das Standardformat abzurufen.



  
**Rückgabe**: die Standardvertraulichkeitsbezeichnung, sofern vorhanden. Wenn keine Standardbezeichnung festgelegt ist, wird „nullptr“ zurückgegeben.
  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
Ruft die Bezeichnung entsprechend der angegebenen ID ab.

Parameter:  
* **ID**: Bezeichner für die Bezeichnung.



  
**Gibt Folgendes zurück**: Bezeichnung
  
### <a name="createpolicyhandler-function"></a>Funktion "kreatepolicyhandler"
Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.

Parameter:  
* **isauditdiscoveryaktivierte**: Beschreibt, ob die Überwachungs Ermittlung aktiviert ist.



  
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
Ruft ab, ob die Richtlinie gemäß den bereitgestellten contentformats über automatische oder Empfehlungs Regeln verfügt.

Parameter:  
* **contentformat**: Vektor der zu berücksichtigenden Formate, wenn festgestellt wird, ob eine Regel für ein beliebiges Format definiert ist. Legen Sie contentformats auf einen leeren Vektor fest, wenn die bereitgestellten contentformats Standardformate sind.



  
**Gibt Folgendes zurück**: ein boolescher Wert, der Aufschluss darüber gibt, ob die Richtlinie automatische oder Empfehlungs Regeln enthält.
  
### <a name="getlastpolicyfetchtime-function"></a>Getlastpolicyfetchtime-Funktion
Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

  
**Returns**: die Uhrzeit, zu der die Richtlinie zuletzt abgerufen wurde.
  
### <a name="getwxpmetadataversion-function"></a>GetWxpMetadataVersion-Funktion
Ruft die empfohlene WXP-Metadatenversion (Word, Excel, PowerPoint) ab, die derzeit 0 für die alte Verifizierung 1 für die Co-Authoring-aktivierte Version ist.

  
**Gibt Folgendes zurück**: Uint32_t int, welche Version von Metadaten der Mandant für WXP-Dateien unterstützt.