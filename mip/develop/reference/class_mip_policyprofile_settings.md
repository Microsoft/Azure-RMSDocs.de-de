---
title: Microsoft Information Protection-Klasse „PolicyProfile Settings“
description: Referenz für die Microsoft Information Protection-Klasse „PolicyProfile Settings“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 07cbcbc022c02a43f751e1cf55b5b0efdfb816d1
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446878"
---
# <a name="class-mippolicyprofilesettings"></a>mip::PolicyProfile::Settings-Klasse 
[Einstellungen](class_mip_policyprofile_settings.md), die während der Erstellung und Lebensdauer von [PolicyProfile](class_mip_policyprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public Settings(const std::string& path, bool useInMemoryStorage, const std::shared_ptr<AuthDelegate>& authDelegate, const std::shared_ptr<PolicyProfile::Observer>& observer, const ApplicationInfo& applicationInfo)  |  Eine Schnittstelle für die Konfiguration des Profils
 public const std::string& GetPath() const  |  Ruft den Pfad zum gespeicherten Status ab.
 public bool GetUseInMemoryStorage() const  |  Ruft das Flag „Arbeitsspeicher verwenden“ ab.
public const std::shared_ptr<AuthDelegate>& GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab.
public const std::shared_ptr<PolicyProfile::Observer>& GetObserver() const  |  Ruft den Ereignisbeobachter ab.
 public const ApplicationInfo GetApplicationInfo() const  |  Ruft die Anwendungsinformationen ab.
public std::shared_ptr<LoggerDelegate> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
public void SetLoggerDelegate(const std::shared_ptr<LoggerDelegate>& loggerDelegate)  |  Überschreibt die Standardprotokollierung.
public std::shared_ptr<HttpDelegate> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
public void SetHttpDelegate(const std::shared_ptr<HttpDelegate>& httpDelegate)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
 public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
 public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
 public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.
 public LogLevel GetMinimumLogLevel() const  |  Ruft das Mindestprotokolliergrad-Objekt ab.
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **path**: Pfad zu einem Verzeichnis, in dem das SDK den Profilstatus speichert. 


* **useInMemoryStorage**: Speichert jeden zwischengespeicherten Status im Arbeitsspeicher und nicht auf dem Datenträger. 


* **authDelegate**: Authentifizierungsdelegat, der vom SDK zum Abrufen von Authentifizierungstoken verwendet wird 


* **observer**: Klasse, die die Schnittstelle [PolicyProfile::Observer](class_mip_policyprofile_observer.md) implementiert. Kann „nullptr“ lauten. 


* **applicationInfo**: Anwendungsbezeichner für den Dienstzugriff.


  
### <a name="getpath"></a>GetPath
Ruft den Pfad zum gespeicherten Status ab.

  
**Rückgabe**: Pfad zum gespeicherten Status.
  
### <a name="getuseinmemorystorage"></a>GetUseInMemoryStorage
Ruft das Flag „Arbeitsspeicher verwenden“ ab.

  
**Rückgabe**: TRUE, wenn In-Memory-Speicher-Verwendung festgelegt ist; andernfalls wird FALSE zurückgegeben.
  
### <a name="getauthdelegate"></a>GetAuthDelegate
Ruft den Authentifizierungsdelegaten ab.

  
**Rückgabe**: Authentifizierungsdelegat.
  
### <a name="policyprofileobserver"></a>PolicyProfile::Observer
Ruft den Ereignisbeobachter ab.

  
**Rückgabe**: Ereignisbeobachter.
  
### <a name="applicationinfo"></a>ApplicationInfo
Ruft die Anwendungsinformationen ab.

  
**Rückgabe**: die Anwendungsinformationen.
  
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

  
**Rückgabe**: HTTP-Delegat, der für HTTP-Vorgänge verwendet wird.
  
### <a name="sethttpdelegate"></a>SetHttpDelegate
Überschreibt den Standard-HTTP-Stapel mit dem des Clients.

Parameter:  
* **httpDelegate**: HTTP-Rückrufschnittstelle, die von Clientanwendungen implementiert wird.


  
### <a name="optouttelemetry"></a>OptOutTelemetry
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
  
### <a name="istelemetryoptedout"></a>IsTelemetryOptedOut
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Rückgabe**: Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
  
### <a name="setminimumloglevel"></a>SetMinimumLogLevel
Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.

Parameter:  
* **logLevel**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst. 



  
**Rückgabe**: TRUE.
  
### <a name="loglevel"></a>LogLevel
Ruft das Mindestprotokolliergrad-Objekt ab.

  
**Rückgabe**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst.