---
title: mip::PolicyProfile::Settings-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 2edec96a34b6885aa6c38477d36e401ebc49242a
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055657"
---
# <a name="class-mippolicyprofilesettings"></a>mip::PolicyProfile::Settings-Klasse 
[Einstellungen](class_mip_policyprofile_settings.md), die während der Erstellung und Lebensdauer von [PolicyProfile](class_mip_policyprofile.md) verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: String & Path, cachestoragetype cachestoragetype, Konst\<Std:: shared_ptr\>authdelegat & authdelegat, Konstanten Std:: shared_ptr\<policyprofile:: Observer\> & Observer, Konstante ApplicationInfo & ApplicationInfo)  |  Eine Schnittstelle für die Konfiguration des Profils
öffentliche Einstellungen (Konstante Std::\<shared_ptr mipcontext\>& mipcontext, cachestoragetype cachestoragetype, Konstanten Std\>:: shared_ptr\<authdelegat & authdelegat, Konstanten Std:: shared_ptr\< Policyprofile:: Observer\>& Observer)  |  Eine Schnittstelle für die Konfiguration des Profils
public const std::string& GetPath() const  |  Ruft den Pfad zum gespeicherten Status ab.
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
Public Konstanten Std:: shared_ptr\<\>authdelegat & getauthdelegat () Konstanten  |  Ruft den Authentifizierungsdelegaten ab.
Public konstant Std:: shared_ptr\<policyprofile:: Observer\>& getobserver () Konstanten  |  Ruft den Ereignisbeobachter ab.
public const ApplicationInfo& GetApplicationInfo() const  |  Ruft die Anwendungsinformationen ab.
Public Std:: shared_ptr\<mipcontext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
Public Std:: shared_ptr\<\> loggerdelegat getloggerdelegat () Konstanten  |  Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).
öffentliches void setloggerdelegat (konstant Std:: shared_ptr\<\>loggerdelegat & loggerdelegat)  |  Überschreibt die Standardprotokollierung.
Public Std:: shared_ptr\<\> httpdelegat gethttpdeleg() Konstanten  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
öffentliches void-Setup Delegat (Konstante Std:: shared_ptr\<\>httpdelegat & httpdelegat)  |  Überschreibt den Standard-HTTP-Stapel mit dem des Clients.
Public Std:: shared_ptr\<\> taskdispatcherdelegat gettaskdispatcherdelegat () Konstanten  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (Konstanten Std:: shared_ptr\<\>taskdispatcherdelegat & taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void OptOutTelemetry()  |  Deaktiviert die Sammlung sämtlicher Telemetriedaten.
public bool IsTelemetryOptedOut() const  |  Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.
public void SetMinimumLogLevel(LogLevel logLevel)  |  Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.
public LogLevel GetMinimumLogLevel() const  |  Ruft das Mindestprotokolliergrad-Objekt ab.
public void SetSessionId(const std::string& sessionId)  | _Noch nicht dokumentiert._
public const std::string& GetSessionId() const  | _Noch nicht dokumentiert._
public ~Settings()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **Pfad**: Der Pfad zu einem Verzeichnis, in dem das SDK den Profil Status speichert. 


* **cachestoragetype**: Zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger speichern 


* authdelegat: Der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird. 


* **Beobachter**: Eine Klasse, die die [policyprofile:: Observer](class_mip_policyprofile_observer.md) -Schnittstelle implementiert. Kann „nullptr“ lauten. 


* **applicationInfo**: Die Anwendungs-IDs, die für den Dienst Zugriff verwendet werden.


> Veraltet Dieser Konstruktor wird in Kürze als veraltet markiert, sodass er einen MIP:: mipcontext-Parameter erfordert.
  
### <a name="settings-function"></a>Settings-Funktion
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **mipcontext**: Globale Kontext Einstellungen 


* **cachestoragetype**: Zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger speichern 


* authdelegat: Der Authentifizierungs Delegat, der vom SDK zum Abrufen von Authentifizierungs Token verwendet wird. 


* **Beobachter**: Eine Klasse, die die [policyprofile:: Observer](class_mip_policyprofile_observer.md) -Schnittstelle implementiert. Kann „nullptr“ lauten.


  
### <a name="getpath-function"></a>GetPath-Funktion
Ruft den Pfad zum gespeicherten Status ab.

  
**Gibt Folgendes zurück**: Pfad zum gespeicherten Zustand.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="getcachestoragetype-function"></a>Getcachestoragetype-Funktion
Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.

  
**Gibt Folgendes zurück**: Verwendeter Speichertyp
  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Ruft den Authentifizierungsdelegaten ab.

  
**Gibt Folgendes zurück**: Der Authentifizierungs Delegat.
  
### <a name="getobserver-function"></a>Getobserver-Funktion
Ruft den Ereignisbeobachter ab.

  
**Gibt Folgendes zurück**: Der Ereignis Beobachter.
  
### <a name="getapplicationinfo-function"></a>Getapplicationinfo-Funktion
Ruft die Anwendungsinformationen ab.

  
**Gibt Folgendes zurück**: Die Anwendungsinformationen.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="getmipcontext-function"></a>Getmipcontext-Funktion
MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.

  
**Gibt Folgendes zurück**: MIP-Kontext
  
### <a name="getloggerdelegate-function"></a>Getloggerdelegatfunktion
Ruft den von der Anwendung bereitgestellten Protokollierungsdelegaten ab (falls vorhanden).

  
**Gibt Folgendes zurück**: Protokollierung
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="setloggerdelegate-function"></a>Setloggerdelegatfunktion
Überschreibt die Standardprotokollierung.

Parameter:  
* **loggerDelegate**: Von Client Anwendungen implementierte Protokollierungs Rückruf Schnittstelle


Diese Methode sollte durch Clientanwendungen aufgerufen werden, die ihre eigene Implementierung für die Protokollierung verwenden. 
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
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
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="istelemetryoptedout-function"></a>Istelemetryoptedout-Funktion
Ruft ab, ob die Sammlung von Telemetriedaten deaktiviert werden soll oder nicht.

  
**Gibt Folgendes zurück**: True, wenn die telemetrieerfassung deaktiviert werden soll, andernfalls false.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="setminimumloglevel-function"></a>Setminimumloglevel-Funktion
Legt den Mindestprotokolliergrad fest, der ein Protokollierereignis auslöst.

Parameter:  
* **logLevel**: Mindestprotokolliergrad, der ein Protokollierereignis auslöst.


> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="getminimumloglevel-function"></a>Getminimumloglevel-Funktion
Ruft das Mindestprotokolliergrad-Objekt ab.

  
**Gibt Folgendes zurück**: Mindestprotokolliergrad, der ein Protokollierungs Ereignis auslöst.
> Veraltet Diese Methode wird in Kürze als veraltet markiert, um allgemeine Kontext Daten durch MIP:: mipcontext zu erhalten/festzulegen.
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
_Noch nicht dokumentiert._

  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
_Noch nicht dokumentiert._

  
### <a name="settings-function"></a>~ Settings-Funktion
_Noch nicht dokumentiert._
