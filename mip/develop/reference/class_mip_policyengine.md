---
title: mip::PolicyEngine-Klasse
description: Dokumentiert die MIP::p olicyengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: e70e7c94ee37cfaaf2e56538977377f421f702a3
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055817"
---
# <a name="class-mippolicyengine"></a>mip::PolicyEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die [Einstellungen](class_mip_policyengine_settings.md) der Richtlinien-Engine ab.
Public Konstanten Std::\<Vector Std:: shared_ptr\<Label\>\>& listsensitivitylabels ()  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
Public Konstanten Std::\<Vector Std:: shared_ptr\<sensitivitytypesrulepackage\>\>& listsensitivitytypes () Konstanten  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.
Public Std:: shared_ptr\<-\> Bezeichnung getdefaultsensitivitylabel ()  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
Public Std:: shared_ptr\<Label\> getlabelbyid (Konstanten Std:: String & ID) Konstanten  |  Ruft die Bezeichnung entsprechend der angegebenen ID ab.
Public Std:: shared_ptr\<policyhandler\> kreatepolicyhandler (bool isauditdiscoveryaktivierte)  |  Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public Konstanten Std:: String & getpolicydataxml ()-Konstanten  |  Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () Konstanten  |  Ruft eine Liste benutzerdefinierter Einstellungen ab.
Public Konstanten Std:: String & getpolicyfleid () Konstanten  |  Ruft die ID der Richtlinien Datei ab.
public bool hasclassificationrules () konstant  |  Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getlastpolicyfetchtime () Konstanten  |  Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die [Einstellungen](class_mip_policyengine_settings.md) der Richtlinien-Engine ab.

  
**Gibt Folgendes zurück**: Richtlinien-Engine-Einstellungen. 
  
**Weitere Informationen finden Sie unter:** [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.

  
**Gibt Folgendes zurück**: Eine Liste der Vertraulichkeits Bezeichnungen.
  
### <a name="listsensitivitytypes-function"></a>Listsensitivitytypes-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeits Typen auf.

  
**Gibt Folgendes zurück**: Eine Liste der Vertraulichkeits Bezeichnungen. leer, wenn loadsensitivitytypesaktivierte false war (
  
**Siehe auch**: [Policyengine:: Settings](class_mip_policyengine_settings.md)).
  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Gibt Folgendes zurück**: Eine URL im Zeichen folgen Format.
  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.

  
**Gibt Folgendes zurück**: True, wenn die Bezeichnung obligatorisch ist, andernfalls false.
  
### <a name="getdefaultsensitivitylabel-function"></a>Getdefaultsensitivitylabel-Funktion
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Gibt Folgendes zurück**: Standardmäßige Vertraulichkeits Bezeichnung, falls vorhanden, nullptr, wenn keine Standard Bezeichnung festgelegt ist.
  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
Ruft die Bezeichnung entsprechend der angegebenen ID ab.
  
### <a name="createpolicyhandler-function"></a>Funktion "kreatepolicyhandler"
Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.

Parameter:  
* **A**: Boolescher Wert, der angibt, ob die Überwachungs Ermittlung aktiviert ist.



  
**Gibt Folgendes zurück**: Richtlinien Handler.
Die Anwendung muss das richtlinienhandlerobjekt für die Lebensdauer des Dokuments beibehalten.
  
### <a name="sendapplicationauditevent-function"></a>Sendapplicationauditevent-Funktion
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **Ebene**: der Protokollebene: Info/Fehler/Warnung. 


* **eventType**: eine Beschreibung des Ereignis Typs. 


* **EventData**: die Daten, die dem Ereignis zugeordnet sind.


  
### <a name="getpolicydataxml-function"></a>Getpolicydataxml-Funktion
Ruft Richtlinien Daten-XML ab, die die Einstellungen, Bezeichnungen und Regeln beschreibt, die dieser Richtlinie zugeordnet sind.

  
**Gibt Folgendes zurück**: Richtlinien Daten-XML.
  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft eine Liste benutzerdefinierter Einstellungen ab.

  
**Gibt Folgendes zurück**: Ein Vektor von benutzerdefinierten Einstellungen.
  
### <a name="getpolicyfileid-function"></a>Getpolicyfleid-Funktion
Ruft die ID der Richtlinien Datei ab.

  
**Gibt Folgendes zurück**: Eine Zeichenfolge, die die Richtlinien Datei-ID darstellt.
  
### <a name="hasclassificationrules-function"></a>Hasclassificationrules-Funktion
Ruft ab, ob die Richtlinie über automatische oder Empfehlungs Regeln verfügt.

  
**Gibt Folgendes zurück**: Ein boolescher Wert, der mitteilt, ob in der Richtlinie automatische oder Empfehlungs Regeln vorhanden sind.
  
### <a name="getlastpolicyfetchtime-function"></a>Getlastpolicyfetchtime-Funktion
Ruft den Zeitpunkt ab, zu dem die Richtlinie zuletzt abgerufen wurde.

  
**Gibt Folgendes zurück**: Der Zeitpunkt, zu dem die Richtlinie zuletzt abgerufen wurde.