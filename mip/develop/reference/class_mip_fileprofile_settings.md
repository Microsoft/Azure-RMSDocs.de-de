---
title: Microsoft Information Protection-Klasse „FileProfile Settings“
description: Referenz für die Microsoft Information Protection-Klasse „FileProfile Settings“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 4b79d8eb75a54a56f1b3e48645bdd5eec0afaa19
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446378"
---
# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
[Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, std::shared_ptr<AuthDelegate> authDelegate, std::shared_ptr<ConsentDelegate> consentDelegate, std::shared_ptr<Observer> observer, const ApplicationInfo& applicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor
 public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.
 public bool GetUseInMemoryStorage() const  |  Ruft ab, ob alle Zustände im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.
public std::shared_ptr<AuthDelegate> GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
public std::shared_ptr<ConsentDelegate> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.
public std::shared_ptr<Observer> GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.
 public const ApplicationInfo GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK nutzt.
 public bool GetSkipTelemetryInit() const  |  Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden soll.
 public void SetSkipTelemetryInit()  |  Deaktiviert die Initialisierung der Telemetrie.
 public void SetNewFeaturesDisabled()  |  Deaktiviert neue Features.
 public bool AreNewFeaturesDisabled() const  |  Ruft ab, ob neue Features deaktiviert sind.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Überschreibt die Standardprotokollierung.
public std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
public void SetHttpDelegate(const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.
 public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
 public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Erfassung von Telemetriedaten deaktiviert werden soll.
 public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
 public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab.
 public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den niedrigsten Protokolliergrad fest, der ein Protokollierungsereignis auslöst.
 public LogLevel GetMinimumLogLevel() const  |  Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslöst.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
[FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor

Parameter:  
* **path**: Pfad, in dem Protokollierung, Telemetrie und weitere persistente Status zum Schutz gespeichert sind 


* **useInMemoryStorage**: TRUE, wenn alle Zustände im Speicher gespeichert werden sollen, FALSE, wenn Zustände auf dem Datenträger zwischengespeichert werden sollen. 


* **authDelegate**: Authentifizierungsdelegat für die Beschaffung von Authentifizierungstoken 


* **observer**: [Beobachterinstanz](class_mip_fileprofile_observer.md), die Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.


* **applicationInfo**: Informationen zur Anwendung, die das SDK nutzt.


  
### <a name="getpath"></a>GetPath
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.

  
**Rückgabe**: Pfad zum Speicherort für Protokollierung, Telemetrie und weitere persistente Status
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft ab, ob alle Zustände im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.

  
**Rückgabe**: Ob alle Zustände im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Rückgabe**: Authentifizierungsdelegat, der für die Beschaffung von Authentifizierungstoken verwendet wird
  
### <a name="consentdelegate"></a>ConsentDelegate
Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.

  
**Rückgabe**: Zustimmungsdelegat für die Anforderung der Zustimmung eines Benutzers
  
### <a name="observer"></a>Beobachter
Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.

  
[Rückgabe](class_mip_fileprofile_observer.md): Der **Beobachter**, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft Informationen zu der Anwendung ab, die das SDK nutzt.

  
**Rückgabe**: Informationen zu der Anwendung, die das SDK nutzt.
  
### <a name="getskiptelemetryinit"></a>GetSkipTelemetryInit
Ruft ab, ob eine Initialisierung der Telemetrie übersprungen werden soll.

  
**Rückgabe**: Ob eine Initialisierung der Telemetrie übersprungen werden soll.
  
### <a name="setskiptelemetryinit"></a>SetSkipTelemetryInit
Deaktiviert die Initialisierung der Telemetrie.
Diese Methode wird in der Regel nicht von Clientanwendungen aufgerufen. Sie wird stattdessen vom File-SDK verwendet, um eine doppelte Initialisierung zu verhindern.
  
### <a name="setnewfeaturesdisabled"></a>SetNewFeaturesDisabled
Deaktiviert neue Features.
Für Anwendungen, die keine neuen Features testen möchten.
  
### <a name="arenewfeaturesdisabled"></a>AreNewFeaturesDisabled
Ruft ab, ob neue Features deaktiviert sind.

  
**Rückgabe**: Ob neue Features deaktiviert sind.
  
### <a name="loggerdelegate"></a>LoggerDelegate
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Rückgabe**: Protokollierung.
  
### <a name="setloggerdelegate"></a>SetLoggerDelegate
Überschreibt die Standardprotokollierung.

Parameter:  
* **loggerDelegate**: Rückrufschnittstelle für die Protokollierung, die von Clientanwendungen implementiert wird.


Diese Methode sollte durch Clientanwendungen aufgerufen werden, die ihre eigene Implementierung für die Protokollierung verwenden.
  
### <a name="httpdelegate"></a>HttpDelegate
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Rückgabe**: Der HTTP-Delegat, der für HTTP-Vorgänge verwendet werden soll.
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.

Parameter:  
* **httpDelegate**: HTTP-Rückrufschnittstelle, die von Clientanwendungen implementiert wird.


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Ruft ab, ob die Erfassung von Telemetriedaten deaktiviert werden soll.

  
**Rückgabe**: Ob die Erfassung von Telemetriedaten deaktiviert werden soll oder nicht.
  
### <a name="setsessionid"></a>SetSessionId
Legt die Sitzungs-ID fest.

Parameter:  
* **sessionId**: Die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetrie verwendet wird.


  
### <a name="getsessionid"></a>GetSessionId
Ruft die Sitzungs-ID ab.

  
**Rückgabe**: Die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetrie verwendet wird.
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Legt den niedrigsten Protokolliergrad fest, der ein Protokollierungsereignis auslöst.

Parameter:  
* **logLevel**: Der niedrigste Protokolliergrad, der ein Protokollierungsereignis auslöst. 



  
**Rückgabe**: TRUE.
  
### <a name="loglevel"></a>LogLevel
Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslöst.

  
**Rückgabe**: Der niedrigste Protokolliergrad, der ein Protokollierungsereignis auslöst.