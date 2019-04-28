---
title: mip::ProtectionProfile::Settings-Klasse
description: 'Beschreibt die Klasse:: protectionprofile-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 3d3685656f8814fe495e6e29d7fe12cf54d7d7d4
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60173614"
---
# <a name="class-mipprotectionprofilesettings"></a>mip::ProtectionProfile::Settings-Klasse 
[Einstellungen](class_mip_protectionprofile_settings.md), die während der Erstellung und Lebensdauer von [ProtectionProfile](class_mip_protectionprofile.md) verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Einstellungen für die öffentliche (const Std:: String & Pfad, "bool" UseInMemoryStorage, const Std:: shared_ptr\<AuthDelegate\>& AuthDelegate, const Std:: shared_ptr\<ConsentDelegate\>& ConsentDelegate const Std:: shared_ptr\<protectionprofile:: Observer\>& Observer, const ApplicationInfo & ApplicationInfo)  |  Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der einen Beobachter angibt, der für asynchrone Vorgänge verwendet werden soll.
Einstellungen für die öffentliche (const Std:: String & Pfad, "bool" UseInMemoryStorage, const Std:: shared_ptr\<AuthDelegate\>& AuthDelegate, const Std:: shared_ptr\<ConsentDelegate\>& ConsentDelegate const ApplicationInfo & ApplicationInfo)  |  Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der für synchrone Vorgänge verwendet wird
public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.
public bool GetUseInMemoryStorage() const  |  Ruft ab, ob Caches nur im Arbeitsspeicher (und nicht auch auf Datenträgern) gespeichert werden.
Public Std:: shared_ptr\<AuthDelegate\> GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
Public Std:: shared_ptr\<ConsentDelegate\> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.
Public Std:: shared_ptr\<protectionprofile:: Observer\> GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen zu Ereignissen empfängt, die in Verbindung mit [ProtectionProfile](class_mip_protectionprofile.md) stehen.
public const ApplicationInfo& GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das Protection SDK nutzt.
public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
Public Std:: shared_ptr\<LoggerDelegate\> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
Öffentliche void SetLoggerDelegate (const Std:: shared_ptr\<LoggerDelegate\>& LoggerDelegate)  |  Überschreibt die Standardprotokollierung.
Public Std:: shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
Öffentliche void SetHttpDelegate (const Std:: shared_ptr\<HttpDelegate\>& HttpDelegate)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
public std::shared_ptr\<TaskDispatcherDelegate\> GetTaskDispatcherDelegate() const  |  Rufen Sie den TaskDispatcher-Delegaten (sofern vorhanden), von der Anwendung bereitgestellt.
public void SetTaskDispatcherDelegate(const std::shared_ptr\<TaskDispatcherDelegate\>& taskDispatcherDelegate)  |  Überschreiben Sie die Standardaufgabe asynchroner Verarbeitung mit des Clients zu verteilen.
public void SetNewFeaturesDisabled()  |  Deaktiviert neue Features
public bool AreNewFeaturesDisabled() const  |  Ruft ab, ob neue Features deaktiviert sind
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab
public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.
public LogLevel GetMinimumLogLevel() const  |  Ruft das Mindestprotokolliergrad-Objekt ab.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der einen Beobachter angibt, der für asynchrone Vorgänge verwendet werden soll.

Parameter:  
* **path**: Dateipfad, unter der Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert ist 


* **useInMemoryStorage**: Alle zwischengespeicherten Zustand Store, nicht auf dem Datenträger, sondern im Arbeitsspeicher 


* **authDelegate**: Callback-Objekt, für die Authentifizierung von Client-Anwendung implementiert werden 


* **observer**: [Beobachter](class_mip_protectionprofile_observer.md) -Instanz, die Benachrichtigungen von Ereignissen empfängt, wird im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md)


* **applicationInfo**: Informationen zur Anwendung, die das SDK den Schutz nutzt


  
### <a name="settings-function"></a>Settings-Funktion
Der [ProtectionProfile::Settings](class_mip_protectionprofile_settings.md)-Konstruktor, der für synchrone Vorgänge verwendet wird

Parameter:  
* **path**: Dateipfad, unter der Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert ist 


* **useInMemoryStorage**: Alle zwischengespeicherten Zustand Store, nicht auf dem Datenträger, sondern im Arbeitsspeicher 


* **authDelegate**: Callback-Objekt, für die Authentifizierung von Client-Anwendung implementiert werden 


* **applicationInfo**: Informationen zur Anwendung, die SDK für den Schutz nutzt


  
### <a name="getpath-function"></a>GetPath-Funktion
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind.

  
**Gibt**: Der Pfad, in dem Protokollierung, Telemetrie und weitere Begleitmaterialien zum Schutz gespeichert sind
  
### <a name="getuseinmemorystorage-function"></a>GetUseInMemoryStorage-Funktion
Ruft ab, ob Caches nur im Arbeitsspeicher (und nicht auch auf Datenträgern) gespeichert werden.

  
**Gibt**: True, wenn Sie Caches nur im Speicher gespeichert sind
  
### <a name="getauthdelegate-function"></a>GetAuthDelegate-Funktion
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Gibt**: Auth-Delegat, der für den Erwerb von Authentifizierungstoken verwendet wird.
  
### <a name="getconsentdelegate-function"></a>GetConsentDelegate-Funktion
Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.

  
**Gibt**: Zustimmung-Delegat, der für die Verbindung mit Diensten verwendet wird.
  
### <a name="getobserver-function"></a>GetObserver-Funktion
Ruft den Beobachter ab, der Benachrichtigungen zu Ereignissen empfängt, die in Verbindung mit [ProtectionProfile](class_mip_protectionprofile.md) stehen.

  
**Gibt**: [Beobachter](class_mip_protectionprofile_observer.md) , empfängt Benachrichtigungen von Ereignissen im Zusammenhang mit [ProtectionProfile](class_mip_protectionprofile.md)
  
### <a name="getapplicationinfo-function"></a>GetApplicationInfo-Funktion
Ruft Informationen zu der Anwendung ab, die das Protection SDK nutzt.

  
**Gibt**: Informationen zur Anwendung, die das SDK den Schutz nutzt
  
### <a name="optouttelemetry-function"></a>OptOutTelemetry-Funktion
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout-function"></a>IsTelemetryOptedOut function
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Gibt**: Sammeln von Telemetriedaten oder nicht deaktiviert werden soll
  
### <a name="getloggerdelegate-function"></a>GetLoggerDelegate-Funktion
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Gibt**: Protokollierung
  
### <a name="setloggerdelegate-function"></a>SetLoggerDelegate-Funktion
Überschreibt die Standardprotokollierung.

Parameter:  
* **loggerDelegate**: Protokollieren die Rückrufschnittstelle implementiert, die von Clientanwendungen


Diese Methode sollte durch Clientanwendungen aufgerufen werden, die ihre eigene Implementierung für die Protokollierung verwenden.
  
### <a name="gethttpdelegate-function"></a>GetHttpDelegate-Funktion
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Gibt**: HTTP-Delegat, der für HTTP-Vorgänge verwendet werden
  
### <a name="sethttpdelegate-function"></a>SetHttpDelegate-Funktion
Überschreibt den Standard-HTTP-Stapel mit dem des Clients.

Parameter:  
* **httpDelegate**: HTTP-Rückrufschnittstelle, die von der Clientanwendung implementiert


  
### <a name="gettaskdispatcherdelegate-function"></a>GetTaskDispatcherDelegate-Funktion
Rufen Sie den TaskDispatcher-Delegaten (sofern vorhanden), von der Anwendung bereitgestellt.

  
**Gibt**: TaskDispatcher-Delegat, der zum Ausführen von asynchronen Aufgaben verwendet werden soll
  
### <a name="settaskdispatcherdelegate-function"></a>SetTaskDispatcherDelegate-Funktion
Überschreiben Sie die Standardaufgabe asynchroner Verarbeitung mit des Clients zu verteilen.

Parameter:  
* **taskDispatcherDelegate**: Aufgabe, die Verteilung der Rückrufschnittstelle, die von der Clientanwendung implementiert


  
### <a name="setnewfeaturesdisabled-function"></a>SetNewFeaturesDisabled-Funktion
Deaktiviert neue Features
Für Anwendungen, die keine neuen Features testen möchten
  
### <a name="arenewfeaturesdisabled-function"></a>AreNewFeaturesDisabled-Funktion
Ruft ab, ob neue Features deaktiviert sind

  
**Gibt**: Wenn Sie neue Features deaktiviert sind oder nicht
  
### <a name="setsessionid-function"></a>SetSessionId-Funktion
Legt die Sitzungs-ID fest

Parameter:  
* **sessionId**: Sitzungs-ID, die zum Korrelieren von Protokollen bzw. der Telemetrie verwendet werden


  
### <a name="getsessionid-function"></a>GetSessionId-Funktion
Ruft die Sitzungs-ID ab

  
**Gibt**: Sitzungs-ID, die zum Korrelieren von Protokollen bzw. der Telemetrie verwendet werden
  
### <a name="setminimumloglevel-function"></a>SetMinimumLogLevel-Funktion
Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.

Parameter:  
* **logLevel**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst. 



  
**Gibt**: True
  
### <a name="getminimumloglevel-function"></a>GetMinimumLogLevel-Funktion
Ruft das Mindestprotokolliergrad-Objekt ab.

  
**Gibt**: Mindestprotokolliergrad, die ein Ereignis für die nachrichtenprotokollierung ausgelöst wird.