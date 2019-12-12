---
title: mip::PolicyProfile::Settings-Klasse
description: Dokumentiert die MIP::p olicyprofile-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 324b31a9589cff75a758da2936a3aba242fd63c2
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73560870"
---
# <a name="class-mippolicyprofilesettings"></a>mip::PolicyProfile::Settings-Klasse 
Einstellungen, die von policyprofile während der Erstellung und während der gesamten Lebensdauer von verwendet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: shared_ptr\<mipcontext\>& mipcontext, cachestoragetype cachestoragetype, Konstante Std:: shared_ptr\<authdelegat\>& authdelegat, Konstanten Std:: shared_ptr\<policyprofile:: Observer\>& Observer)  |  Eine Schnittstelle für die Konfiguration des Profils
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
Public Konstanten Std:: shared_ptr\<authdelegat\>& getauthdelegat () Konstanten  |  Ruft den Authentifizierungsdelegaten ab.
Public Konstante Std:: shared_ptr\<policyprofile:: Observer\>& getobserver () konstant  |  Ruft den Ereignisbeobachter ab.
Public Std:: shared_ptr\<mipcontext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
Public Std:: shared_ptr\<httpdelegat\> gethttpdeleg() Konstanten  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
öffentliches void-Setup Delegat (Konstante Std:: shared_ptr\<httpdelegat\>& httpdelegat)  |  Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.
Public Std:: shared_ptr\<taskdispatcherdelegat\> gettaskdispatcherdelegat () Konstanten  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (Konstanten Std:: shared_ptr\<taskdispatcherdelegaten\>& taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void SetSessionId(const std::string& sessionId)  | Noch nicht dokumentiert.
public const std::string& GetSessionId() const  | Noch nicht dokumentiert.
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
public ~Settings()  | Noch nicht dokumentiert.
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **mipcontext**: globale Kontext Einstellungen 


* **cachestoragetype**: speichert jeden zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger. 


* **authDelegate**: Authentifizierungsdelegat, der vom SDK zum Abrufen von Authentifizierungstoken verwendet wird 


* **Observer**: eine Klasse, die die policyprofile:: Observer-Schnittstelle implementiert. Kann „nullptr“ lauten.


  
### <a name="getcachestoragetype-function"></a>Getcachestoragetype-Funktion
Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.

  
**Returns**: verwendeter Speichertyp
  
### <a name="getauthdelegate-function"></a>Getauthdelegatfunktion
Ruft den Authentifizierungsdelegaten ab.

  
**Rückgabe**: Authentifizierungsdelegat.
  
### <a name="getobserver-function"></a>Getobserver-Funktion
Ruft den Ereignisbeobachter ab.

  
**Rückgabe**: Ereignisbeobachter.
  
### <a name="getmipcontext-function"></a>Getmipcontext-Funktion
MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.

  
**Gibt Folgendes zurück**: MIP-Kontext
  
### <a name="gethttpdelegate-function"></a>Gethttpdelegatfunktion
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Rückgabe**: HTTP-Delegat, der für HTTP-Vorgänge verwendet wird.
  
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
_Noch nicht dokumentiert._

  
### <a name="getsessionid-function"></a>Geungessionid-Funktion
_Noch nicht dokumentiert._

  
### <a name="setcustomsettings-function"></a>Setcustomsettings-Funktion
Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.

Parameter:  
* **customSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren
  
### <a name="settings-function"></a>~ Settings-Funktion
_Noch nicht dokumentiert._
