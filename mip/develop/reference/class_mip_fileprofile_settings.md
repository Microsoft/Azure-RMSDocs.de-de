---
title: mip::FileProfile::Settings-Klasse
description: 'Dokumentiert die MIP:: File Profile-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: e559228104450c83063634470c285ed1057aab60
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056068"
---
# <a name="class-mipfileprofilesettings"></a>mip::FileProfile::Settings-Klasse 
[Einstellungen](class_mip_fileprofile_settings.md), die während der Erstellung und Lebensdauer von [FileProfile](class_mip_fileprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: String & Path, cachestoragetype cachestoragetype,\<Std:: shared_ptr\> authdelegat authdelegat, Std\> ::\<shared_ptr genehmidelegat genehmidelegat, Std:: shared_ptr\<Observer\> Observer, Konstante ApplicationInfo & ApplicationInfo)  |  [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor
öffentliche Einstellungen (Konstante Std:: shared_ptr\<mipcontext\>& mipcontext, cachestoragetype cachestoragetype, Std\> :: shared_ptr\<authdelegerauthdelegat, Std::\< shared_ptr Genehmifdelegat, Std:: shared_ptr\<Observer\> Observer)\>  |  [FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor
public const std::string& GetPath() const  |  Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
Public Std:: shared_ptr\<\> authdelegat getauthdelegat () Konstanten  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
Public Std:: shared_ptr\<\> genehmidelegat getgenehmidelegat () konstant  |  Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.
Public Std:: shared_ptr\<Observer\> getobserver () konstant  |  Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.
public const ApplicationInfo& GetApplicationInfo() const  |  Ruft Informationen zu der Anwendung ab, die das SDK nutzt.
Public Std:: shared_ptr\<mipcontext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
Public Std:: shared_ptr\<\> loggerdelegat getloggerdelegat () Konstanten  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
öffentliches void setloggerdelegat (konstant Std:: shared_ptr\<\>loggerdelegat & loggerdelegat)  |  Überschreibt die Standardprotokollierung.
Public Std:: shared_ptr\<\> httpdelegat gethttpdeleg() Konstanten  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
öffentliches void-Setup Delegat (Konstante Std:: shared_ptr\<\>httpdelegat & httpdelegat)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
Public Std:: shared_ptr\<\> taskdispatcherdelegat gettaskdispatcherdelegat () Konstanten  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (Konstanten Std:: shared_ptr\<\>taskdispatcherdelegat & taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab
public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den niedrigsten Protokolliergrad fest, der ein Protokollierungsereignis auslöst.
public LogLevel GetMinimumLogLevel() const  |  Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslöst.
öffentliches void setcancachelicenses (bool-abfrageelicenses)  |  Konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.
public bool abgebrochen () konstant  |  Ruft ab, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
[FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor

Parameter:  
* **Pfad**: Dateipfad, unter dem Protokollierung, Telemetrie und anderer persistenter Zustand gespeichert werden 


* **cachestoragetype**: Zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger speichern 


* authdelegat: Authentifizierungs Delegat zum Abrufen von Authentifizierungs Token 


* genehmifdelegat: Delegat zum Abrufen der Benutzer Berechtigung für den Zugriff auf externe Ressourcen 


* **Beobachter**: [Beobachter](class_mip_fileprofile_observer.md) Instanz, die Benachrichtigungen über Ereignisse im Zusammenhang mit [File profile](class_mip_fileprofile.md) empfängt


* **applicationInfo**: Informationen über die Anwendung, die das SDK nutzt


> Veraltet Dieser Konstruktor wird in Kürze als veraltet markiert, sodass er einen MIP:: mipcontext-Parameter erfordert.
  
### <a name="settings-function"></a>Settings-Funktion
[FileProfile::Settings](class_mip_fileprofile_settings.md)-Konstruktor

Parameter:  
* **mipcontext**: Globale Kontext Einstellungen 


* **cachestoragetype**: Zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger speichern 


* authdelegat: Authentifizierungs Delegat zum Abrufen von Authentifizierungs Token 


* genehmifdelegat: Delegat zum Abrufen der Benutzer Berechtigung für den Zugriff auf externe Ressourcen 


* **Beobachter**: [Beobachter](class_mip_fileprofile_observer.md) Instanz, die Benachrichtigungen über Ereignisse im Zusammenhang mit [File profile](class_mip_fileprofile.md) empfängt


  
### <a name="getpath-function"></a>GetPath-Funktion
Ruft den Pfad ab, in dem Protokollierung, Telemetrie und weitere persistente Status gespeichert sind.

  
**Gibt Folgendes zurück**: Der Pfad, unter dem Protokollierung, Telemetrie und anderer persistenter Zustand gespeichert werden.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="getcachestoragetype-function"></a>Getcachestoragetype-Funktion
Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.

  
**Gibt Folgendes zurück**: Verwendeter Speichertyp
  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Gibt Folgendes zurück**: Authentifizierungs Delegat zum Abrufen von Authentifizierungs Token
  
### <a name="getconsentdelegate-function"></a>Geteinvernehmdelegatfunktion
Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.

  
**Gibt Folgendes zurück**: Zustimmungs Delegat, der zum Anfordern der Benutzer Zustimmung verwendet wird
  
### <a name="getobserver-function"></a>Getobserver-Funktion
Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu [FileProfile](class_mip_fileprofile.md) gehören.

  
**Gibt Folgendes zurück**: [Beobachter](class_mip_fileprofile_observer.md) , der Benachrichtigungen über Ereignisse im Zusammenhang mit [File profile](class_mip_fileprofile.md) empfängt
  
### <a name="getapplicationinfo-function"></a>Getapplicationinfo-Funktion
Ruft Informationen zu der Anwendung ab, die das SDK nutzt.

  
**Gibt Folgendes zurück**: Informationen über die Anwendung, die das SDK nutzt
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="getmipcontext-function"></a>Getmipcontext-Funktion
MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.

  
**Gibt Folgendes zurück**: MIP-Kontext
  
### <a name="getloggerdelegate-function"></a>Getloggerdelegatfunktion
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Gibt Folgendes zurück**: Protokollierung
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="setloggerdelegate-function"></a>Setloggerdelegatfunktion
Überschreibt die Standardprotokollierung.

Parameter:  
* **loggerDelegate**: Von Client Anwendungen implementierte Protokollierungs Rückruf Schnittstelle


Diese Methode sollte durch Clientanwendungen aufgerufen werden, die ihre eigene Implementierung für die Protokollierung verwenden. 
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="gethttpdelegate-function"></a>Gethttpdelegatfunktion
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Gibt Folgendes zurück**: Für http-Vorgänge zu verwendende http-Delegat
  
### <a name="sethttpdelegate-function"></a>Setup-Delegatfunktion
Überschreibt den Standard-HTTP-Stapel mit dem des Clients.

Parameter:  
* **httpdelegat**: Von der Client Anwendung implementierte HTTP-Rückruf Schnittstelle


  
### <a name="gettaskdispatcherdelegate-function"></a>Gettaskdispatcherdelegatfunktion
Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).

  
**Gibt Folgendes zurück**: Taskdispatcher-Delegat, der zum Ausführen von asynchronen Aufgaben verwendet werden soll.
  
### <a name="settaskdispatcherdelegate-function"></a>Settaskdispatcherdelegatfunktion
Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.

Parameter:  
* **taskDispatcherDelegate**: Von der Client Anwendung implementierte Rückruf Schnittstelle für die Task Verteilung


  
### <a name="optouttelemetry-function"></a>Optouttelemetry-Funktion
Deaktiviert die Sammlung sämtlicher Telemetriedaten.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="istelemetryoptedout-function"></a>Istelemetryoptedout-Funktion
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Gibt Folgendes zurück**: Wenn das Sammeln von Telemetriedaten deaktiviert werden soll oder nicht.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID fest

Parameter:  
* **sessionId**: Die Sitzungs-ID, die zum Korrelieren von Protokollen/Telemetrie verwendet wird.


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID ab

  
**Gibt Folgendes zurück**: Die Sitzungs-ID, die zum Korrelieren von Protokollen/Telemetrie verwendet wird.
  
### <a name="setminimumloglevel-function"></a>Setminimumloglevel-Funktion
Legt den niedrigsten Protokolliergrad fest, der ein Protokollierungsereignis auslöst.

Parameter:  
* **logLevel**: Der niedrigste Protokolliergrad, der ein Protokollierungsereignis auslöst.


> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="getminimumloglevel-function"></a>Getminimumloglevel-Funktion
Ruft den niedrigsten Protokolliergrad ab, der ein Protokollierungsereignis auslöst.

  
**Gibt Folgendes zurück**: Niedrigste Protokollebene, die ein Protokollierungs Ereignis auslöst.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten.
  
### <a name="setcancachelicenses-function"></a>Setcancachelicenses-Funktion
Konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

Parameter:  
* **Abbrechen**: Gibt an, ob die Engine beim Öffnen von geschütztem Inhalt eine Lizenz zwischenspeichern soll.


Wenn der Wert true ist, wird die zugehörige Lizenz lokal durch das Öffnen geschützter Inhalte zwischengespeichert Wenn der Wert false ist, wird durch das Öffnen geschützter Inhalte immer der http-Vorgang zum Abrufen der Lizenz vom RMS-Dienst durchgeführt.
  
### <a name="cancachelicenses-function"></a>Abbrechen-Funktion
Ruft ab, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

  
**Gibt Folgendes zurück**: Lizenz zwischen Speicherungs Konfiguration