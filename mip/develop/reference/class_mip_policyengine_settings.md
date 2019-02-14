---
title: mip::PolicyEngine::Settings-Klasse
description: 'Beschreibt die Klasse:: policyengine-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 6ad384768ef876109a6a43237765474345a666bc
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56257534"
---
# <a name="class-mippolicyenginesettings"></a>mip::PolicyEngine::Settings-Klasse 
Definiert die einer [PolicyEngine](class_mip_policyengine.md)-Klasse zugeordneten Einstellungen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& engineId, const std::string& clientData, const std::string& locale, bool loadSensitivityTypes)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine
public Settings(const Identity& identity, const std::string& clientData, const std::string& locale, bool loadSensitivityTypes)  |  [PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Erstellen einer neuen Engine
public const std::string& GetEngineId() const  |  Ruft die Engine-ID ab.
public void SetEngineId(const std::string& id)  |  Legt die Engine-ID fest.
public const Identity& GetIdentity() const  |  Abrufen der [Identität](class_mip_identity.md) Objekt.
public void SetIdentity(const Identity& identity)  |  Legen Sie die [Identität](class_mip_identity.md) Objekt.
public const std::string& GetClientData() const  |  Ruft die in den Einstellungen festgelegten Clientdaten ab.
public void SetClientData(const std::string& clientData)  |  Legt die Zeichenfolge der Clientdaten fest.
public const std::string& GetLocale() const  |  Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.
Öffentliche void SetCustomSettings (const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.
public bool IsLoadSensitivityTypesEnabled() const  |  Abrufen der das Flag gibt an, ob Load vertraulichkeitsbezeichnungen aktiviert ist.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
[PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Laden einer vorhandenen Engine

Parameter:  
* **engineId**: Legen Sie sie an, auf die eindeutige Engine-ID, die von addengineasync erstellte oder selbst generiert werden. Verwenden Sie beim Laden einer vorhandenen Engine die ID, andernfalls wird eine neue Engine erstellt. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **Optionale**: Flag zum angeben, wenn das Skriptmodul geladen ist sollte geladen werden auch benutzerdefinierte Empfindlichkeit-Typen, wenn "true" OnPolicyChange Beobachter für das Profil für Updates für benutzerdefinierte Empfindlichkeit-Typen sowie der Änderungen aufgerufen werden soll. Wenn "false" ListSensitivityTypes aufrufen, gibt immer eine leere Liste zurück.


  
### <a name="settings-function"></a>Settings-Funktion
[PolicyEngine::Settings](class_mip_policyengine_settings.md)-Konstruktor zum Erstellen einer neuen Engine

Parameter:  
* **identity**: [Identität](class_mip_identity.md) Informationen des Benutzers, das neue Modul zugeordnet. 


* **clientData**: Anpassbare Clientdaten können beim Entladen mit der Engine gespeichert und aus einer geladenen Engine abgerufen werden. 


* **locale**: Von der Engine lokalisierbare Ausgaben werden in diesem Gebietsschema bereitgestellt. 


* **Optionale**: Flag zum angeben, wenn das Skriptmodul geladen ist sollte geladen werden auch benutzerdefinierte Empfindlichkeit-Typen, wenn "true" OnPolicyChange Beobachter für das Profil für Updates für benutzerdefinierte Empfindlichkeit-Typen sowie der Änderungen aufgerufen werden soll. Wenn "false" ListSensitivityTypes aufrufen, gibt immer eine leere Liste zurück.


  
### <a name="getengineid-function"></a>GetEngineId-Funktion
Ruft die Engine-ID ab.

  
**Gibt**: Eine eindeutige Zeichenfolge, die das Modul identifiziert.
  
### <a name="setengineid-function"></a>SetEngineId-Funktion
Legt die Engine-ID fest.

Parameter:  
* **id**: Engine-ID.


  
### <a name="getidentity-function"></a>"Getidentity"-Funktion
Abrufen der [Identität](class_mip_identity.md) Objekt.

  
**Gibt**: Ein Verweis auf die Identität im Einstellungsobjekt. 
  
**Siehe auch**: [MIP:: Identity](class_mip_identity.md)
  
### <a name="setidentity-function"></a>SetIdentity-Funktion
Legen Sie die [Identität](class_mip_identity.md) Objekt.

Parameter:  
* **identity**: Die eindeutige Identität eines Benutzers. 


  
**Siehe auch**: [MIP:: Identity](class_mip_identity.md)
  
### <a name="getclientdata-function"></a>GetClientData-Funktion
Ruft die in den Einstellungen festgelegten Clientdaten ab.

  
**Gibt**: Eine Zeichenfolge mit Daten, die vom Client angegeben.
  
### <a name="setclientdata-function"></a>SetClientData-Funktion
Legt die Zeichenfolge der Clientdaten fest.

Parameter:  
* **clientData**: Vom Benutzer angegebene Daten.


  
### <a name="getlocale-function"></a>GetLocale-Funktion
Gibt die in den Einstellungen festgelegte Gebietseinstellung zurück.

  
**Gibt**: Das Gebietsschema.
  
### <a name="setcustomsettings-function"></a>SetCustomSettings-Funktion
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **customSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings-function"></a>GetCustomSettings-Funktion
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Gibt**: Liste von Name-Wert-Paaren.
  
### <a name="setsessionid-function"></a>SetSessionId-Funktion
Legt die Sitzungs-ID fest und wird für clientdefinierte Telemetrie verwendet.

Parameter:  
* **sessionId**: Eine eindeutige Zeichenfolge, die Telemetrieereignisse verbindet.


  
### <a name="getsessionid-function"></a>GetSessionId-Funktion
Ruft die Sitzungs-ID ab, ein eindeutiger Bezeichner.

  
**Gibt**: Die Sitzungs-ID.
  
### <a name="isloadsensitivitytypesenabled-function"></a>IsLoadSensitivityTypesEnabled-Funktion
Abrufen der das Flag gibt an, ob Load vertraulichkeitsbezeichnungen aktiviert ist.

  
**Gibt**: True, wenn aktiviert, andernfalls False.
