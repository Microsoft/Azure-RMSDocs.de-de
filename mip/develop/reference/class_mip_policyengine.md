---
title: Die Klasse „mip::PolicyProfile“
description: Referenz zur Klasse „mip PolicyEngine“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 57dd325e9c00a3cb2a4056f7ef0b522efef5d0c4
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446038"
---
# <a name="class-mippolicyengine"></a>mip::PolicyEngine-Klasse 
Diese Klasse stellt eine Schnittstelle für alle Engine-Funktionen bereit.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Ruft die [Einstellungen](class_mip_policyengine_settings.md) der Richtlinien-Engine ab.
public const std::vector<std::shared_ptr<Label>>& ListSensitivityLabels()  |  Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.
 public const std::string& GetMoreInfoUrl() const  |  Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.
 public bool IsLabelingRequired() const  |  Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.
public std::shared_ptr<Label> GetDefaultSensitivityLabel()  |  Ruft die Standardvertraulichkeitsbezeichnung ab.
public std::shared_ptr<PolicyHandler> CreatePolicyHandler(const std::string& contentIdentifier)  |  Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.
 public void SendApplicationAuditEvent(const std::string& level, const std::string& eventType, const std::string& eventData)  |  Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft die [Einstellungen](class_mip_policyengine_settings.md) der Richtlinien-Engine ab.

  
**Rückgabe**: Einstellungen der Richtlinien-Engine. 
  
**Weitere Informationen finden Sie unter:** [mip::PolicyEngine::Settings](class_mip_policyengine_settings.md)
  
### <a name="label"></a>Label
Listet die mit der Richtlinien-Engine verknüpften Vertraulichkeitsbezeichnungen auf.

  
**Rückgabe**: Liste der Vertraulichkeitsbezeichnungen.
  
### <a name="getmoreinfourl"></a>GetMoreInfoUrl
Geben Sie eine URL an, um weitere Informationen zur Richtlinie bzw. zu den Bezeichnungen zu suchen.

  
**Rückgabe:** eine URL im Zeichenfolgenformat
  
### <a name="islabelingrequired"></a>IsLabelingRequired
Überprüft, ob die Richtlinie festlegt, dass ein Dokument eine Bezeichnung erhalten muss oder nicht.

  
**Rückgabe:** TRUE, wenn eine Bezeichnung erforderlich ist; andernfalls FALSE.
  
### <a name="label"></a>Label
Ruft die Standardvertraulichkeitsbezeichnung ab.

  
**Rückgabe**: die Standardvertraulichkeitsbezeichnung, sofern vorhanden. Wenn keine Standardbezeichnung festgelegt ist, wird „nullptr“ zurückgegeben.
  
### <a name="policyhandler"></a>PolicyHandler
Erstellt einen Richtlinienhandler, um Funktionen für den Ausführungszustand einer Datei auszuführen, die im Zusammenhang mit einer Richtlinie stehen.

Parameter:  
* **contentIdentifier**: ein lesbarer Inhaltsbezeichner. Dateibeispiel: „C:\mip-sdk-for-cpp\files\audit.docx“ [Pfad] E-Mail-Beispiel „RE: Überprüfung design:user1@contoso.com“ [Betreff:Sender]



  
**Rückgabe**: Richtlinienhandler
  
### <a name="sendapplicationauditevent"></a>SendApplicationAuditEvent
Protokolliert ein anwendungsspezifisches Ereignis in der Überprüfungspipeline.

Parameter:  
* **description:** Beschreibung der Protokollebene: Information/Fehler/Warnung 


* **eventType:** Beschreibung des Ereignistyps 


* **eventData:** dem Ereignis zugeordnete Daten

