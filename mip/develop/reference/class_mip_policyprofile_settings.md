---
title: mip::PolicyProfile::Settings-Klasse
description: Dokumentiert die mip::policyprofile-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: d3105bd9c13e91108c44e847c3eae74f166c5e04
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60173438"
---
# <a name="class-mippolicyprofilesettings"></a>mip::PolicyProfile::Settings-Klasse 
[Einstellungen](class_mip_policyprofile_settings.md), die während der Erstellung und Lebensdauer von [PolicyProfile](class_mip_policyprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Einstellungen für die öffentliche (const Std:: String & Pfad, "bool" UseInMemoryStorage, const Std:: shared_ptr\<AuthDelegate\>& AuthDelegate, const Std:: shared_ptr\<PolicyProfile::Observer\>& Observer, const ApplicationInfo & ApplicationInfo)  |  Eine Schnittstelle für die Konfiguration des Profils
public const std::string& GetPath() const  |  Ruft den Pfad zum gespeicherten Status ab.
public bool GetUseInMemoryStorage() const  |  Ruft das Flag „Arbeitsspeicher verwenden“ ab.
Public const Std:: shared_ptr\<AuthDelegate\>& GetAuthDelegate() const  |  Ruft den Authentifizierungsdelegaten ab.
Public const Std:: shared_ptr\<PolicyProfile::Observer\>& GetObserver() const  |  Ruft den Ereignisbeobachter ab.
public const ApplicationInfo GetApplicationInfo() const  |  Ruft die Anwendungsinformationen ab.
Public Std:: shared_ptr\<LoggerDelegate\> GetLoggerDelegate() const  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
Öffentliche void SetLoggerDelegate (const Std:: shared_ptr\<LoggerDelegate\>& LoggerDelegate)  |  Überschreibt die Standardprotokollierung.
Public Std:: shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
Öffentliche void SetHttpDelegate (const Std:: shared_ptr\<HttpDelegate\>& HttpDelegate)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
public std::shared_ptr\<TaskDispatcherDelegate\> GetTaskDispatcherDelegate() const  |  Rufen Sie den TaskDispatcher-Delegaten (sofern vorhanden), von der Anwendung bereitgestellt.
public void SetTaskDispatcherDelegate(const std::shared_ptr\<TaskDispatcherDelegate\>& taskDispatcherDelegate)  |  Überschreiben Sie die Standardaufgabe asynchroner Verarbeitung mit des Clients zu verteilen.
public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.
public LogLevel GetMinimumLogLevel() const  |  Ruft das Mindestprotokolliergrad-Objekt ab.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **path**: Der Pfad zu einem Verzeichnis, in dem das SDK den Profilstatus speichert. 


* **useInMemoryStorage**: Store Sie alle zwischengespeicherten Zustand im Arbeitsspeicher und nicht auf dem Datenträger. 


* **authDelegate**: Der authentifizierungsdelegat, der vom SDK zum Abrufen von Authentifizierungstoken verwendet wird. 


* **observer**: Eine Klasse implementiert die [PolicyProfile::Observer](class_mip_policyprofile_observer.md) Schnittstelle. Kann „nullptr“ lauten. 


* **applicationInfo**: Der Anwendungsbezeichner für den Dienstzugriff verwendet.


  
### <a name="getpath-function"></a>GetPath-Funktion
Ruft den Pfad zum gespeicherten Status ab.

  
**Gibt**: Der Pfad zum gespeicherten Status.
  
### <a name="getuseinmemorystorage-function"></a>GetUseInMemoryStorage-Funktion
Ruft das Flag „Arbeitsspeicher verwenden“ ab.

  
**Gibt**: True, wenn die Verwendung in den Speicher andernfalls "false" festgelegt ist.
  
### <a name="getauthdelegate-function"></a>GetAuthDelegate-Funktion
Ruft den Authentifizierungsdelegaten ab.

  
**Gibt**: Der Authentifizierungsdelegat.
  
### <a name="getobserver-function"></a>GetObserver-Funktion
Ruft den Ereignisbeobachter ab.

  
**Gibt**: Der ereignisbeobachter.
  
### <a name="getapplicationinfo-function"></a>GetApplicationInfo-Funktion
Ruft die Anwendungsinformationen ab.

  
**Gibt**: Die Anwendungsinformationen.
  
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

  
**Gibt**: True, wenn das Sammeln von Telemetriedaten deaktiviert werden soll else "false"
  
### <a name="setminimumloglevel-function"></a>SetMinimumLogLevel-Funktion
Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.

Parameter:  
* **logLevel**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst. 



  
**Gibt**: True
  
### <a name="getminimumloglevel-function"></a>GetMinimumLogLevel-Funktion
Ruft das Mindestprotokolliergrad-Objekt ab.

  
**Gibt**: Mindestprotokolliergrad, die ein Ereignis für die nachrichtenprotokollierung ausgelöst wird.