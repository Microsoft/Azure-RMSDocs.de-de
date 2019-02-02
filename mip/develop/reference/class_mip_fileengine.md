---
title: mip::FileEngine-Klasse
description: 'Beschreibt die Klasse:: fileengine-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 4bcdd08cb7ced9e2eea8fa09d9364064a8d198df
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651461"
---
# <a name="class-mipfileengine"></a>mip::FileEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Gibt die Engine-Einstellungen zurück.
public const std::vector\<std::shared_ptr\<SensitivityTypesRulePackage\>\>& ListSensitivityTypes() const  |  sind die Vertraulichkeit-Typen, die die Richtlinien-Engine zugeordnet.
public const std::vector\<std::shared_ptr\<Label\>\>& ListSensitivityLabels()  |  Eine Liste der Vertraulichkeitsbezeichnungen
public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.
Öffentliche void CreateFileHandlerAsync (const Std:: String & InputFilePath, const Std:: String & ContentIdentifier, const ContentState ContentState, "bool" IsAuditDiscoveryEnabled, const Std:: shared_ptr\<fileHandler\>& FileHandlerObserver, const Std:: shared_ptr\<"void"\>& Kontext, const Std:: shared_ptr\<FileExecutionState\>& FileExecutionState)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.
Öffentliche void CreateFileHandlerAsync (const Std:: shared_ptr\<Stream\>& InputStream, const Std:: String & InputFilePath, const Std:: String & ContentIdentifier, const mip::ContentState ContentState, "bool" IsAuditDiscoveryEnabled, const Std:: shared_ptr\<fileHandler\>& FileHandlerObserver, const Std:: shared_ptr\<"void"\>& Kontext, const Std:: shared_ptr\< FileExecutionState\>& FileExecutionState)  |  Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.
public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Ruft eine Liste der benutzerdefinierten Einstellungen ab.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Gibt die Engine-Einstellungen zurück.
  
### <a name="listsensitivitytypes-function"></a>ListSensitivityTypes-Funktion
sind die Vertraulichkeit-Typen, die die Richtlinien-Engine zugeordnet.

  
**Gibt**: Eine Liste der vertraulichkeitsbezeichnungen. leer, wenn LoadSensitivityTypesEnabled wurde "false")
  
**Siehe auch**: [FileEngine::Settings](class_mip_fileengine_settings.md)).
  
### <a name="listsensitivitylabels-function"></a>ListSensitivityLabels-Funktion
Eine Liste der Vertraulichkeitsbezeichnungen
  
### <a name="getmoreinfourl-function"></a>GetMoreInfoUrl-Funktion
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Gibt**: Eine Url im Zeichenfolgenformat.
  
### <a name="islabelingrequired-function"></a>IsLabelingRequired-Funktion
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss.

  
**Gibt**: True, wenn die Bezeichnung ist obligatorisch, andernfalls "false".
  
### <a name="createfilehandlerasync-function"></a>CreateFileHandlerAsync-Funktion
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateipfad.

Parameter:  
* **inputFilePath**: Die zu öffnende Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **ContentIdentifier**: ein Benutzer lesbarer Bezeichner für den Inhalt. Beispiel für eine Datei: 'C:\mip-sdk-for-cpp\files\audit.docx"[' Pfad\Dateiname'] Beispiel für eine e-Mail: "RE: Audit design:user1@contoso.com"[Betreff: Absender] 


* **contentState**: Der Status des Inhalts während die Anwendung mit ihm interagiert. 


* **IsAuditDiscoveryEnabled**: Darstellung, ob der Audit-Ermittlung aktiviert ist oder nicht. 


* **fileHandlerObserver**: Eine Klasse, welche die [FileHandler::Observer](class_mip_filehandler_observer.md)-Schnittstelle implementiert. 


* **context**: Clientkontext, der Clientkontext an dem Beobachter übergeben wird.


  
### <a name="createfilehandlerasync-function"></a>CreateFileHandlerAsync-Funktion
Beginnt mit der Erstellung eines Dateihandlers für den angegebenen Dateidatenstrom.

Parameter:  
* **inputStream**: Ein Datenstrom, der die Dateidaten enthält. 


* **inputFilePath**: Der Pfad zur Datei. Der Pfad muss den Dateinamen und, sofern vorhanden, die Erweiterung enthalten. 


* **ContentIdentifier**: ein Benutzer lesbarer Bezeichner für den Inhalt. Beispiel für eine Datei: 'C:\mip-sdk-for-cpp\files\audit.docx"[' Pfad\Dateiname'] Beispiel für eine e-Mail: "RE: Audit design:user1@contoso.com"[Betreff: Absender] 


* **contentState**: Der Status des Inhalts während die Anwendung mit ihm interagiert. 


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