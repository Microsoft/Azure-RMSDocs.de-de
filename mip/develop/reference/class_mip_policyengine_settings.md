---
title: Die Klasse „mip::PolicyEngine::Settings“
description: Referenz zur Klasse „mip::PolicyEngine::Settings“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6ac94d1e34615a0248dac85f28c55154b127574f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446344"
---
# <a name="class-mippolicyenginesettings"></a>mip::PolicyEngine::Settings-Klasse 
Definiert die einer [PolicyEngine](class_mip_policyengine.md)-Klasse zugeordneten Einstellungen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine
 public Settings(const Identity& identity, const std::string& clientData, const std::string& locale)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Erstellen einer neuen Engine
 public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
 public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
 public const Identity& GetIdentity() const  |  Ruft das Identity-Objekt ab.
 public void SetIdentity(const Identity& identity)  |  Legt das Identity-Objekt fest.
 public const std::string& GetClientData() const  |  Ruft die in den Einstellungen festgelegten Clientdaten ab.
 public void SetClientData(const std::string& clientData)  |  Legt die Zeichenfolge der Clientdaten fest.
 public const std::string& GetLocale() const  |  Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
public void SetCustomSettings(const std::vector<std::pair<std::string, std::string>>& customSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
public const std::vector<std::pair<std::string, std::string>>& GetCustomSettings() const  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Legen Sie diese auf die eindeutige, von AddEngineAsync erstellte oder auf eine selbst erstellte Engine-ID fest. Verwenden Sie beim Laden einer vorhandenen Engine die ID, andernfalls wird eine neue Engine erstellt. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt.


  
### <a name="settings"></a>Einstellung
[PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Erstellen einer neuen Engine

Parameter:  
* **identity**: Informationen zur Identität des Benutzers, der der neuen Engine zugeordnet ist. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt.


  
### <a name="getengineid"></a>GetEngineId
Ruft die Engine-ID ab.

  
**Rückgabe**: Eindeutige Zeichenfolge, die die Engine identifiziert.
  
### <a name="setengineid"></a>SetEngineId
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity"></a>GetIdentity
Ruft das Identity-Objekt ab.

  
**Rückgabe**: Verweis auf die Identität im Einstellungsobjekt. 
  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="setidentity"></a>SetIdentity
Legt das Identity-Objekt fest.

Parameter:  
* **identity**: Die eindeutige Identität eines Benutzers. 


  
**Weitere Informationen finden Sie unter:** mip::Identity
  
### <a name="getclientdata"></a>GetClientData
Ruft die in den Einstellungen festgelegten Clientdaten ab.

  
**Rückgabe**: Vom Client angegebene Datenzeichenfolge.
  
### <a name="setclientdata"></a>SetClientData
Legt die Zeichenfolge der Clientdaten fest.

Parameter:  
* **clientData**: Vom Benutzer angegebene Daten.


  
### <a name="getlocale"></a>GetLocale
Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.

  
**Rückgabe**: Das Gebietsschema.
  
### <a name="setcustomsettings"></a>SetCustomSettings
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **customSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings"></a>GetCustomSettings
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.

Parameter:  
* **sessionId**: Eine eindeutige Zeichenfolge, die Telemetrieereignisse verbindet.


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.

  
**Rückgabe**: die Sitzungs-ID.