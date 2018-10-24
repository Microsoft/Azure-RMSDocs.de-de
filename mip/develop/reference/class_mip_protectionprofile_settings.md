---
title: Die Klasse „mip::ProtectionProfile::Settings“
description: Referenz zur Klasse „mip::ProtectionProfile::Settings“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: fe2413b2265cf4994dce0e57a7c472d59336902a
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446667"
---
# <a name="class-mipprotectionprofilesettings"></a>mip::ProtectionProfile::Settings-Klasse 
[Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const std::shared_ptr<ProtectionProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der einen Beobachter angibt, der für asynchrone Vorgänge verwendet werden soll.
public Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<ConsentDelegate>& consentDelegate, const ApplicationInfo& applicationInfo)  |  Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der für synchrone Vorgänge verwendet wird
 public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.
 public bool GetUseInMemoryStorage() const  |  Ruft ab, ob Caches nur im Arbeitsspeicher (und nicht auch auf Datenträgern) gespeichert werden.
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
public std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.
public std::shared_ptr<ProtectionProfile::Observer> GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen zu Ereignissen empfängt, die in Verbindung mit [ProtectionProfile](class_mip_protectionprofile.md) stehen.
 public const ApplicationInfo& GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das Protection SDK nutzt.
 public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
 public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Überschreibt die Standardprotokollierung.
public std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
public void SetHttpDelegate(const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
 public bool GetSkipTelemetryInit() const  |  Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden soll
 public void SetSkipTelemetryInit()  |  Deaktiviert die Initialisierung der Telemetrie.
 public void SetNewFeaturesDisabled()  |  Deaktiviert neue Features
 public bool AreNewFeaturesDisabled() const  |  Ruft ab, ob neue Features deaktiviert sind
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab
 public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.
 public LogLevel GetMinimumLogLevel() const  |  Ruft das Mindestprotokolliergrad-Objekt ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der einen Beobachter angibt, der für asynchrone Vorgänge verwendet werden soll.

Parameter:  
* **path**: Dateipfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind 


* **useInMemoryStorage**: Speichert jeden zwischengespeicherten Status im Arbeitsspeicher und nicht auf dem Datenträger. 


* **authDelegate**: von der Clientanwendung implementiertes Rückrufobjekt zur Authentifizierung 


* **observer**: [Observer](class_mip_protectionprofile_observer.md)-Instanz, die Benachrichtigungen von Ereignissen empfängt, die mit [ProtectionProfile](class_mip_protectionprofile.md) in Verbindung stehen


* **applicationInfo**: Informationen zur Anwendung, die das Protection SDK nutzt.


  
### <a name="settings"></a>Einstellung
Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der für synchrone Vorgänge verwendet wird

Parameter:  
* **path**: Dateipfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind 


* **useInMemoryStorage**: Speichert jeden zwischengespeicherten Status im Arbeitsspeicher und nicht auf dem Datenträger. 


* **authDelegate**: von der Clientanwendung implementiertes Rückrufobjekt zur Authentifizierung 


* **applicationInfo**: Informationen zur Anwendung, die das Protection SDK nutzt


  
### <a name="getpath"></a>GetPath
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.

  
**Rückgabe**: der Pfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft ab, ob Caches nur im Arbeitsspeicher (und nicht auch auf Datenträgern) gespeichert werden.

  
**Rückgabe**: „TRUE“, wenn das Zwischenspeichern ausschließlich im Arbeitsspeicher erfolgt.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Rückgabe**: Authentifizierungsdelegat, der für die Beschaffung von Authentifizierungstoken verwendet wird
  
### <a name="consentdelegate"></a>ConsentDelegate
Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.

  
**Rückgabe**: Zustimmungsdelegat, der für die Verbindung mit Diensten verwendet wird
  
### <a name="protectionprofileobserver"></a>ProtectionProfile::Observer
Ruft den Beobachter ab, der Benachrichtigungen zu Ereignissen empfängt, die in Verbindung mit [ProtectionProfile](class_mip_protectionprofile.md) stehen.

  
**Rückgabe**: [Beobachter](class_mip_protectionprofile_observer.md), der Benachrichtigungen von Ereignissen empfängt, die in Verbindung mit dem [ProtectionProfile](class_mip_protectionprofile.md) stehen
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft Informationen zu der Anwendung ab, die das Protection SDK nutzt.

  
**Rückgabe**: Informationen zu der Anwendung, die das Protection SDK nutzt
  
### <a name="optouttelemetry"></a>OptOutTelemetry
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Rückgabe**: Angabe, ob die Erfassung von Telemetriedaten deaktiviert werden soll
  
### <a name="loggerdelegate"></a>LoggerDelegate
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Rückgabe**: Protokollierung
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Überschreibt die Standardprotokollierung.

Parameter:  
* **loggerDelegate**: Rückrufschnittstelle für die Protokollierung, die von Clientanwendungen implementiert wird.


Diese Methode sollte durch Clientanwendungen aufgerufen werden, die ihre eigene Implementierung für die Protokollierung verwenden.
  
### <a name="httpdelegate"></a>HttpDelegate
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Rückgabe**: Der HTTP-Delegat, der für HTTP-Vorgänge verwendet werden soll
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Überschreibt den Standard-HTTP-Stapel mit dem des Clients.

Parameter:  
* **httpDelegate**: HTTP-Rückrufschnittstelle, die von Clientanwendungen implementiert wird


  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden soll

  
**Rückgabe**: Angabe, ob die Initialisierung der Telemetrie übersprungen werden soll
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Deaktiviert die Initialisierung der Telemetrie.
Diese Methode wird in der Regel nicht von Clientanwendungen aufgerufen. Sie wird stattdessen vom File SDK verwendet, um eine doppelte Initialisierung zu verhindern.
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
Deaktiviert neue Features
Für Anwendungen, die keine neuen Features testen möchten
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
Ruft ab, ob neue Features deaktiviert sind

  
**Rückgabe**: Angabe, ob neue Features deaktiviert sind
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest

Parameter:  
* **sessionId**: die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetriedaten verwendet wird


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab

  
**Rückgabe**: die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetriedaten verwendet wird
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.

Parameter:  
* **logLevel**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst. 



  
**Rückgabe**: TRUE.
  
### <a name="loglevel"></a>LogLevel
Ruft das Mindestprotokolliergrad-Objekt ab.

  
**Rückgabe**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst.