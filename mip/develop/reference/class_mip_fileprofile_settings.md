---
title: mip::FileProfile::Settings-Klasse
description: 'Beschreibt die Klasse:: fileprofile-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: d85fe9f4b3de485ab966a38b2c41358a6ba091e0
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574278"
---
# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
[Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Einstellungen für die öffentliche (const Std:: String & Pfad, "bool" UseInMemoryStorage, Std:: shared_ptr\<AuthDelegate\> AuthDelegate, Std:: shared_ptr\<ConsentDelegate\> ConsentDelegate, Std:: shared_ptr\< Beobachter\> Observer, const ApplicationInfo & ApplicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor
public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.
public bool GetUseInMemoryStorage() const  |  Ruft ab, ob alle Zustände im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.
Public Std:: shared_ptr\<AuthDelegate\> GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
Public Std:: shared_ptr\<ConsentDelegate\> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.
Public Std:: shared_ptr\<Beobachter\> GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.
public const ApplicationInfo GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK nutzt.
public void SetNewFeaturesDisabled()  |  Deaktiviert neue Features
public bool AreNewFeaturesDisabled() const  |  Ruft ab, ob neue Features deaktiviert sind
Public Std:: shared_ptr\<LoggerDelegate\> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
Öffentliche void SetLoggerDelegate (const Std:: shared_ptr\<LoggerDelegate\>& LoggerDelegate)  |  Überschreibt die Standardprotokollierung.
Public Std:: shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
Öffentliche void SetHttpDelegate (const Std:: shared_ptr\<HttpDelegate\>& HttpDelegate)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
public std::shared_ptr\<TaskDispatcherDelegate\> GetTaskDispatcherDelegate() const  |  Rufen Sie den TaskDispatcher-Delegaten (sofern vorhanden), von der Anwendung bereitgestellt.
public void SetTaskDispatcherDelegate(const std::shared_ptr\<TaskDispatcherDelegate\>& taskDispatcherDelegate)  |  Überschreiben Sie die Standardaufgabe asynchroner Verarbeitung mit des Clients zu verteilen.
public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab
public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den niedrigsten Protokolliergrad fest, der ein Protokollierungsereignis auslöst.
public LogLevel GetMinimumLogLevel() const  |  Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslöst.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
[FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor

Parameter:  
* **path**: Pfad der Datei unter die Protokollierung, Telemetrie und andere persistente Zustand wird gespeichert. 


* **useInMemoryStorage**: TRUE, wenn alle Zustände im Speicher gespeichert werden sollen, FALSE, wenn Zustände auf dem Datenträger zwischengespeichert werden sollen. 


* **authDelegate**: Auth-Delegat, der für den Erwerb von Authentifizierungstoken verwendet wird. 


* **observer**: [Beobachter](class_mip_fileprofile_observer.md) -Instanz, die Benachrichtigungen von Ereignissen empfängt, wird im Zusammenhang mit [FileProfile](class_mip_fileprofile.md)


* **applicationInfo**: Informationen zur Anwendung, die das SDK verwendet


  
### <a name="getpath-function"></a>GetPath-Funktion
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.

  
**Gibt**: Pfad unter die Protokollierung, Telemetrie und andere persistente Zustand wird gespeichert.
  
### <a name="getuseinmemorystorage-function"></a>GetUseInMemoryStorage-Funktion
Ruft ab, ob alle Zustände im Arbeitsspeicher (und nicht auf dem Datenträger) gespeichert werden sollen.

  
**Gibt**: Wenn alle Status im Arbeitsspeicher gespeichert werden soll (im Gegensatz zu auf dem Datenträger)
  
### <a name="getauthdelegate-function"></a>GetAuthDelegate-Funktion
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Gibt**: Auth-Delegat, der für den Erwerb von Authentifizierungstoken verwendet wird.
  
### <a name="getconsentdelegate-function"></a>GetConsentDelegate-Funktion
Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.

  
**Gibt**: Zustimmung-Delegat, der zum Anfordern der Zustimmung des Benutzers verwendet wird.
  
### <a name="getobserver-function"></a>GetObserver-Funktion
Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.

  
**Gibt**: [Beobachter](class_mip_fileprofile_observer.md) , empfängt Benachrichtigungen von Ereignissen im Zusammenhang mit [FileProfile](class_mip_fileprofile.md)
  
### <a name="getapplicationinfo-function"></a>GetApplicationInfo-Funktion
Ruft Informationen zu der Anwendung ab, die das SDK nutzt.

  
**Gibt**: Informationen zur Anwendung, die das SDK verwendet
  
### <a name="setnewfeaturesdisabled-function"></a>SetNewFeaturesDisabled-Funktion
Deaktiviert neue Features
Für Anwendungen, die keine neuen Features testen möchten
  
### <a name="arenewfeaturesdisabled-function"></a>AreNewFeaturesDisabled-Funktion
Ruft ab, ob neue Features deaktiviert sind

  
**Gibt**: Wenn Sie neue Features deaktiviert sind oder nicht
  
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


  
### <a name="optouttelemetry-function"></a>OptOutTelemetry-Funktion
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout-function"></a>IsTelemetryOptedOut function
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Gibt**: Sammeln von Telemetriedaten oder nicht deaktiviert werden soll
  
### <a name="setsessionid-function"></a>SetSessionId-Funktion
Legt die Sitzungs-ID fest

Parameter:  
* **sessionId**: Sitzungs-ID, die zum Korrelieren von Protokollen bzw. der Telemetrie verwendet werden


  
### <a name="getsessionid-function"></a>GetSessionId-Funktion
Ruft die Sitzungs-ID ab

  
**Gibt**: Sitzungs-ID, die zum Korrelieren von Protokollen bzw. der Telemetrie verwendet werden
  
### <a name="setminimumloglevel-function"></a>SetMinimumLogLevel-Funktion
Legt den niedrigsten Protokolliergrad fest, der ein Protokollierungsereignis auslöst.

Parameter:  
* **logLevel**: Der niedrigste Protokolliergrad, der ein Protokollierungsereignis auslöst. 



  
**Gibt**: True
  
### <a name="getminimumloglevel-function"></a>GetMinimumLogLevel-Funktion
Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslöst.

  
**Gibt**: Niedrigste Protokolliergrad, die ein Ereignis für die nachrichtenprotokollierung ausgelöst wird.