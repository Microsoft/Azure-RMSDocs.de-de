---
title: mip::PolicyEngine-Klasse
description: 'Beschreibt die Klasse:: policyengine-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: ffc2adc3e48de3f7efc7426c1276ccba8f0a70f3
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57332802"
---
# <a name="class-mippolicyengine"></a>mip::PolicyEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die [Einstellungen](class_mip_policyengine_settings.md) der Richtlinien-Engine ab.
public const std::vector\<std::shared_ptr\<Label\>\>& ListSensitivityLabels()  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
public const std::vector\<std::shared_ptr\<SensitivityTypesRulePackage\>\>& ListSensitivityTypes() const  |  sind die Vertraulichkeit-Typen, die die Richtlinien-Engine zugeordnet.
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.
Public Std:: shared_ptr\<Bezeichnung\> GetDefaultSensitivityLabel()  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
public std::shared_ptr\<PolicyHandler\> CreatePolicyHandler(bool isAuditDiscoveryEnabled)  |  Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
public const std::string& GetPolicyDataXml() const  |  Ruft ab die Richtliniendaten XML werden die Einstellungen, Bezeichnungen und Regeln, die dieser Richtlinie unterliegen.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Ruft eine Liste der benutzerdefinierten Einstellungen ab.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die [Einstellungen](class_mip_policyengine_settings.md) der Richtlinien-Engine ab.

  
**Gibt**: Einstellungen für Gruppenrichtlinien-Engine. 
  
**Weitere Informationen finden Sie unter:** [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="listsensitivitylabels-function"></a>ListSensitivityLabels-Funktion
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.

  
**Gibt**: Eine Liste der vertraulichkeitsbezeichnungen.
  
### <a name="listsensitivitytypes-function"></a>ListSensitivityTypes-Funktion
sind die Vertraulichkeit-Typen, die die Richtlinien-Engine zugeordnet.

  
**Gibt**: Eine Liste der vertraulichkeitsbezeichnungen. leer, wenn LoadSensitivityTypesEnabled wurde "false")
  
**Siehe auch**: [PolicyEngine::Settings](class_mip_policyengine_settings.md)).
  
### <a name="getmoreinfourl-function"></a>GetMoreInfoUrl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Gibt**: Eine Url im Zeichenfolgenformat.
  
### <a name="islabelingrequired-function"></a>IsLabelingRequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.

  
**Gibt**: True, wenn die Bezeichnung ist obligatorisch, andernfalls "false".
  
### <a name="getdefaultsensitivitylabel-function"></a>GetDefaultSensitivityLabel-Funktion
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Gibt**: Vertraulichkeitsbezeichnung standardmäßig, wenn vorhanden, "nullptr", wenn es gibt keine standardbezeichnung festgelegt.
  
### <a name="createpolicyhandler-function"></a>CreatePolicyHandler-Funktion
Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.

Parameter:  
* **Ein**: "bool" darstellt, ob der Audit-Ermittlung aktiviert ist.



  
**Gibt**: Richtlinie-Handler.
Anwendung muss das Richtlinienobjekt für den Handler für die Lebensdauer des Dokuments beibehalten werden sollen.
  
### <a name="sendapplicationauditevent-function"></a>SendApplicationAuditEvent-Funktion
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **Ebene**: der dem aktuellen Protokolliergrad: Info/Fehler/Warnung 


* **eventType:** Beschreibung des Ereignistyps 


* **eventData:** dem Ereignis zugeordnete Daten


  
### <a name="getpolicydataxml-function"></a>GetPolicyDataXml-Funktion
Ruft ab die Richtliniendaten XML werden die Einstellungen, Bezeichnungen und Regeln, die dieser Richtlinie unterliegen.

  
**Gibt**: XML-Daten
  
### <a name="getcustomsettings-function"></a>GetCustomSettings-Funktion
Ruft eine Liste der benutzerdefinierten Einstellungen ab.

  
**Gibt**: Ein Vektor von benutzerdefinierten Einstellungen
