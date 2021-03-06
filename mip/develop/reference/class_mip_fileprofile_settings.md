---
title: 'class file profile:: Settings'
description: 'Dokumentiert die File profile:: Settings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 052aef83e44fa1f804464feee968d80c84221a24
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98211430"
---
# <a name="class-fileprofilesettings"></a>class file profile:: Settings 
Einstellungen, die während der Erstellung und Lebensdauer von FileProfile verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: shared_ptr \<MipContext\>& mipcontext, cachestoragetype cachestoragetype, Std:: shared_ptr genehmidelegat \<ConsentDelegate\> , Std:: shared_ptr \<Observer\> Observer)  |  FileProfile::Settings-Konstruktor
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
public std::shared_ptr\<ConsentDelegate\> GetConsentDelegate() const  |  Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.
public std::shared_ptr\<Observer\> GetObserver() const  |  Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu FileProfile gehören.
Public Std:: shared_ptr \<MipContext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
public std::shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
public void SetHttpDelegate(const std::shared_ptr\<HttpDelegate\>& httpDelegate)  |  Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.
Public Std:: shared_ptr \<TaskDispatcherDelegate\> gettaskdispatcherdelegat () Konstanten  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (konstant Std:: shared_ptr \<TaskDispatcherDelegate\>& taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab.
öffentliches void setcancachelicenses (bool-abfrageelicenses)  |  Konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.
public bool abgebrochen () konstant  |  Ruft ab, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
FileProfile::Settings-Konstruktor

Parameter:  
* **mipcontext**: globale Kontext Einstellungen 


* **cachestoragetype**: speichert jeden zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger. 


* genehmigungsdelegat: Delegat zum Abrufen der Benutzer Berechtigung für den Zugriff auf externe Ressourcen 


* **Observer**: Observer-Instanz, die Benachrichtigungen über Ereignisse im Zusammenhang mit File profile empfängt


  
### <a name="getcachestoragetype-function"></a>Getcachestoragetype-Funktion
Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.

  
**Returns**: verwendeter Speichertyp
  
### <a name="getconsentdelegate-function"></a>Geteinvernehmdelegatfunktion
Ruft den Zustimmungsdelegaten ab, der die Benutzerzustimmung für die Verbindung mit Diensten anfordert.

  
**Rückgabe**: Zustimmungsdelegat für die Anforderung der Zustimmung eines Benutzers
  
### <a name="getobserver-function"></a>Getobserver-Funktion
Ruft den Beobachter ab, der Benachrichtigungen von Ereignissen empfängt, die zu FileProfile gehören.

  
**Gibt Folgendes zurück**: Observer, das Benachrichtigungen über Ereignisse im Zusammenhang mit File profile empfängt.
  
### <a name="getmipcontext-function"></a>Getmipcontext-Funktion
MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.

  
**Gibt Folgendes zurück**: MIP-Kontext
  
### <a name="gethttpdelegate-function"></a>Gethttpdelegatfunktion
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Rückgabe**: Der HTTP-Delegat, der für HTTP-Vorgänge verwendet werden soll
  
### <a name="sethttpdelegate-function"></a>Setup-Delegatfunktion
Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.

Parameter:  
* **httpdelegat**: http-Rückruf Schnittstelle von Client Anwendung implementiert


  
### <a name="gettaskdispatcherdelegate-function"></a>Gettaskdispatcherdelegatfunktion
Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).

  
**Gibt Folgendes zurück**: taskdispatcher-Delegat, der zum Ausführen von asynchronen Aufgaben verwendet wird.
  
### <a name="settaskdispatcherdelegate-function"></a>Settaskdispatcherdelegatfunktion
Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.

Parameter:  
* **taskdispatcherdelegat**: Aufgaben Verteiler-Rückruf Schnittstelle von Client Anwendung implementiert


Tasks können auf Profil Objekte verweisen, die ihre Zerstörung verhindern, weil taskdispatcher-Warteschlangen nicht freigegeben werden sollten.
  
### <a name="setsessionid-function"></a>Funktion "-essionid"
Legt die Sitzungs-ID fest.

Parameter:  
* **sessionId**: die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetriedaten verwendet wird


  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
Ruft die Sitzungs-ID ab.

  
**Rückgabe**: die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetriedaten verwendet wird
  
### <a name="setcancachelicenses-function"></a>Setcancachelicenses-Funktion
Konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

Parameter:  
* **Abbrechen**: gibt an, ob die Engine beim Öffnen von geschütztem Inhalt eine Lizenz zwischenspeichern soll.


Wenn der Wert true ist, wird die zugehörige Lizenz lokal durch das Öffnen geschützter Inhalte zwischengespeichert Wenn der Wert false ist, wird durch das Öffnen geschützter Inhalte immer der http-Vorgang zum Abrufen der Lizenz vom RMS-Dienst durchgeführt.
  
### <a name="cancachelicenses-function"></a>Abbrechen-Funktion
Ruft ab, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

  
**Gibt Folgendes zurück**: Lizenz Cache Konfiguration