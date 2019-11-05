---
title: mip::ProtectionProfile::Settings-Klasse
description: Dokumentiert die MIP::p rotectionprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: e39260036f1e4f4413b008e75cbbd761aea7d751
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560077"
---
# <a name="class-mipprotectionprofilesettings"></a>mip::ProtectionProfile::Settings-Klasse 
Einstellungen, die von Protection Profile während der Erstellung und während der gesamten Lebensdauer verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: shared_ptr\<mipcontext\>& mipcontext, cachestoragetype cachestoragetype, Konstante Std:: shared_ptr\<authdelegat\>& authdelegat, Konst Std:: shared_ptr\<genehmigende Delegat\>& zugenehmifdelegaten, Konstante Std:: shared_ptr\<Schutzprofile:: Observer\>& Observer)  |  Schutzprofile:: Settings-Konstruktor, der einen Beobachter angibt, der für asynchrone Vorgänge verwendet werden soll.
öffentliche Einstellungen (Konstante Std:: shared_ptr\<mipcontext\>& mipcontext, cachestoragetype cachestoragetype, Konstante Std:: shared_ptr\<authdelegat\>& authdelegat, Konst Std:: shared_ptr\<genehmigende Delegat\>& genehmifdelegaten)  |  Schutzprofile:: Settings-Konstruktor, der für synchrone Vorgänge verwendet wird.
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
Public Std:: shared_ptr\<authdelegat\> getauthdelegat () Konstanten  |  Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.
Public Std:: shared_ptr\<genehmidelegat\> getgenehmidelegat () Konstanten  |  Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.
Public Std:: shared_ptr\<Schutzprofile:: Observer\> getobserver () konstant  |  Ruft den Observer ab, der Benachrichtigungen über Ereignisse empfängt, die sich auf das Schutzprofil beziehen.
Public Std:: shared_ptr\<mipcontext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
Public Std:: shared_ptr\<httpdelegat\> gethttpdeleg() Konstanten  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
öffentliches void-Setup Delegat (Konstante Std:: shared_ptr\<httpdelegat\>& httpdelegat)  |  Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.
Public Std:: shared_ptr\<taskdispatcherdelegat\> gettaskdispatcherdelegat () Konstanten  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (konstant Std:: shared_ptr\<taskdispatcherdelegat\>& taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void SetSessionId(const std::string& sessionId)  |  Legt die Sitzungs-ID fest.
public const std::string& GetSessionId() const  |  Ruft die Sitzungs-ID ab
öffentliches void setcancachelicenses (bool-abfrageelicenses)  |  Konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.
public bool abgebrochen () konstant  |  Ruft ab, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Schutzprofile:: Settings-Konstruktor, der einen Beobachter angibt, der für asynchrone Vorgänge verwendet werden soll.

Parameter:  
* **mipcontext**: globale Kontext Einstellungen 


* **cachestoragetype**: speichert jeden zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger. 


* **authDelegate**: von der Clientanwendung implementiertes Rückrufobjekt zur Authentifizierung 


* genehmigungsdelegat: Delegat zum Abrufen der Benutzer Berechtigung für den Zugriff auf externe Ressourcen 


* **Observer**: Observer-Instanz, die Benachrichtigungen über Ereignisse im Zusammenhang mit Schutzprofile empfängt


* **applicationInfo**: Informationen zur Anwendung, die das Protection SDK nutzt.


  
### <a name="settings-function"></a>Settings-Funktion
Schutzprofile:: Settings-Konstruktor, der für synchrone Vorgänge verwendet wird.

Parameter:  
* **mipcontext**: globale Kontext Einstellungen 


* **cachestoragetype**: speichert jeden zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger. 


* **authDelegate**: von der Clientanwendung implementiertes Rückrufobjekt zur Authentifizierung 


* genehmigungsdelegat: Delegat zum Abrufen der Benutzer Berechtigung für den Zugriff auf externe Ressourcen 


* **applicationInfo**: Informationen zur Anwendung, die das Protection SDK nutzt


  
### <a name="getcachestoragetype-function"></a>Getcachestoragetype-Funktion
Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.

  
**Returns**: verwendeter Speichertyp
  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Ruft den Authentifizierungsdelegaten ab, der für die Beschaffung von Authentifizierungstoken verwendet wird.

  
**Rückgabe**: Authentifizierungsdelegat, der für die Beschaffung von Authentifizierungstoken verwendet wird
  
### <a name="getconsentdelegate-function"></a>Geteinvernehmdelegatfunktion
Ruft den Zustimmungsdelegaten ab, der für die Verbindung mit Diensten verwendet wird.

  
**Rückgabe**: Zustimmungsdelegat, der für die Verbindung mit Diensten verwendet wird
  
### <a name="getobserver-function"></a>Getobserver-Funktion
Ruft den Observer ab, der Benachrichtigungen über Ereignisse empfängt, die sich auf das Schutzprofil beziehen.

  
**Gibt Folgendes zurück**: Observer, das Benachrichtigungen über Ereignisse im Zusammenhang mit Schutzprofile empfängt.
  
### <a name="getmipcontext-function"></a>Getmipcontext-Funktion
MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.

  
**Gibt Folgendes zurück**: MIP-Kontext
  
### <a name="gethttpdelegate-function"></a>Gethttpdelegatfunktion
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Rückgabe**: Der HTTP-Delegat, der für HTTP-Vorgänge verwendet werden soll
  
### <a name="sethttpdelegate-function"></a>Setup-Delegatfunktion
Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.

Parameter:  
* **httpDelegate**: HTTP-Rückrufschnittstelle, die von Clientanwendungen implementiert wird.


  
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
Ruft die Sitzungs-ID ab

  
**Rückgabe**: die Sitzungs-ID, die zum Korrelieren von Protokollen bzw. Telemetriedaten verwendet wird
  
### <a name="setcancachelicenses-function"></a>Setcancachelicenses-Funktion
Konfiguriert, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

Parameter:  
* **Abbrechen**: gibt an, ob die Engine beim Öffnen von geschütztem Inhalt eine Lizenz zwischenspeichern soll.


Wenn der Wert true ist, wird die zugehörige Lizenz lokal durch das Öffnen geschützter Inhalte zwischengespeichert Wenn der Wert false ist, wird durch das Öffnen geschützter Inhalte immer der http-Vorgang zum Abrufen der Lizenz vom RMS-Dienst durchgeführt.
  
### <a name="cancachelicenses-function"></a>Abbrechen-Funktion
Ruft ab, ob Endbenutzer Lizenzen (Euls) lokal zwischengespeichert werden.

  
**Gibt Folgendes zurück**: Lizenz Cache Konfiguration
  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **customSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren