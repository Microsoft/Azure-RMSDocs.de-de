---
title: mip::FileEngine-Klasse
description: 'Beschreibt die Klasse:: fileengine-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 15ce90a80430f50854580f6c7a2993d92db0a744
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60184789"
---
# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
public const std::vector\<std::shared_ptr\<SensitivityTypesRulePackage\>\>& ListSensitivityTypes() const  |  sind die Vertraulichkeit-Typen, die die Richtlinien-Engine zugeordnet.
Public const Std:: shared_ptr\<Bezeichnung\> GetDefaultSensitivityLabel() const  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
public const std::vector\<std::shared_ptr\<Label\>\>& ListSensitivityLabels()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
Public const Std:: String & GetPolicyId() const  |  Ruft die ID der Richtlinie ab.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.
public std::chrono::time_point\<std::chrono::system_clock\> GetLastPolicyFetchTime() const  |  Ruft den Zeitpunkt, wenn die Richtlinie zuletzt abgerufen wurde.
Öffentliche void CreateFileHandlerAsync (const Std:: String & InputFilePath, const Std:: String & ActualFilePath, "bool" IsAuditDiscoveryEnabled, const Std:: shared_ptr\<fileHandler\>& FileHandlerObserver const Std:: shared_ptr\<"void"\>& Kontext, const Std:: shared_ptr\<FileExecutionState\>& FileExecutionState)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
Öffentliche void CreateFileHandlerAsync (const Std:: shared_ptr\<Stream\>& InputStream, const Std:: String & ActualFilePath, "bool" IsAuditDiscoveryEnabled, const Std:: shared_ptr\<fileHandler \>& FileHandlerObserver, const Std:: shared_ptr\<"void"\>& Kontext, const Std:: shared_ptr\<FileExecutionState\>& FileExecutionState)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Ruft eine Liste der benutzerdefinierten Einstellungen ab.
public Bool HasClassificationRules() const  |  Ruft ab, die Richtlinie Regeln automatisch oder empfohlen wird.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Engine-Einstellungen zurück.
  
### <a name="listsensitivitytypes-function"></a>ListSensitivityTypes-Funktion
sind die Vertraulichkeit-Typen, die die Richtlinien-Engine zugeordnet.

  
**Gibt**: Eine Liste der vertraulichkeitsbezeichnungen. leer, wenn LoadSensitivityTypesEnabled wurde "false")
  
**Siehe auch**: [FileEngine::Settings](class_mip_fileengine_settings.md)).
  
### <a name="getdefaultsensitivitylabel-function"></a>GetDefaultSensitivityLabel-Funktion
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Gibt**: Vertraulichkeitsbezeichnung standardmäßig, wenn vorhanden, "nullptr", wenn es gibt keine standardbezeichnung festgelegt.
  
### <a name="listsensitivitylabels-function"></a>ListSensitivityLabels-Funktion
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="getmoreinfourl-function"></a>GetMoreInfoUrl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Gibt**: Eine Url im Zeichenfolgenformat.
  
### <a name="getpolicyid-function"></a>GetPolicyId-Funktion
Ruft die ID der Richtlinie ab.

  
**Gibt**: Eine Zeichenfolge, die Richtlinien-ID darstellt.
  
### <a name="islabelingrequired-function"></a>IsLabelingRequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.

  
**Gibt**: True, wenn die Bezeichnung ist obligatorisch, andernfalls "false".
  
### <a name="getlastpolicyfetchtime-function"></a>GetLastPolicyFetchTime-Funktion
Ruft den Zeitpunkt, wenn die Richtlinie zuletzt abgerufen wurde.

  
**Gibt**: Die Zeit, wenn die Richtlinie zuletzt abgerufen wurde
  
### <a name="createfilehandlerasync-function"></a>CreateFileHandlerAsync-Funktion
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **inputFilePath**: Die zu öffnende Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **actualFilePath**: Der tatsächliche (nicht temporär) Dateipfad wird für die Überwachung verwendet werden. 


* **IsAuditDiscoveryEnabled**: Darstellung, ob der Audit-Ermittlung aktiviert ist oder nicht. 


* **fileHandlerObserver**: Eine Klasse, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **context**: Clientkontext, der Clientkontext an dem Beobachter übergeben wird.


  
### <a name="createfilehandlerasync-function"></a>CreateFileHandlerAsync-Funktion
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **inputStream**: Ein Datenstrom, der die Dateidaten enthält. 


* **actualFilePath**: Der Pfad zur Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. wird auch verwenden, um die Datei in der Überwachung zu identifizieren. 


* **IsAuditDiscoveryEnabled**: Darstellung, ob der Audit-Ermittlung aktiviert ist oder nicht. 


* **fileHandlerObserver**: Eine Klasse, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **context**: Clientkontext, der Clientkontext an dem Beobachter übergeben wird.


  
### <a name="sendapplicationauditevent-function"></a>SendApplicationAuditEvent-Funktion
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **Ebene**: eine Beschreibung für den Protokolliergrad: Info/Fehler/Warnung 


* **eventType:** Beschreibung des Ereignistyps 


* **eventData:** dem Ereignis zugeordnete Daten


  
### <a name="getcustomsettings-function"></a>GetCustomSettings-Funktion
Ruft eine Liste der benutzerdefinierten Einstellungen ab.

  
**Gibt**: Ein Vektor von benutzerdefinierten Einstellungen
  
### <a name="hasclassificationrules-function"></a>HasClassificationRules-Funktion
Ruft ab, die Richtlinie Regeln automatisch oder empfohlen wird.

  
**Gibt**: Ein boolescher Wert, der darüber informiert, wenn es automatische oder Recommandation in der Richtlinie Regeln