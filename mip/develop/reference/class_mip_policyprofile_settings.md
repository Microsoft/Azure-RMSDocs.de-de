---
title: 'Class policyprofile:: Settings'
description: 'Dokumentiert die policyprofile:: Settings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 317a6cfaaac7572ae320860a0d5a11fabce356e9
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760648"
---
# <a name="class-policyprofilesettings"></a>Class policyprofile:: Settings 
Einstellungen, die während der Erstellung und Lebensdauer von PolicyProfile verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std::\<shared_ptr mipcontext\>& mipcontext, cachestoragetype cachestoragetype, Konstanten Std:: shared_ptr\<policyprofile:: Observer\>& Observer)  |  Eine Schnittstelle für die Konfiguration des Profils
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
Public Konstante Std:: shared_ptr\<policyprofile:: Observer\>& getobserver () konstant  |  Ruft den Ereignisbeobachter ab.
Public Std:: shared_ptr\<mipcontext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
Public Std:: shared_ptr\<httpdelegat\> gethttpdeleg() Konstanten  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
öffentliches void-Setup Delegat (Konstante Std:: shared_ptr\<httpdelegat\>& httpdelegat)  |  Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.
Public Std:: shared_ptr\<taskdispatcherdelegat\> gettaskdispatcherdelegat () konstant  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (konstant Std:: shared_ptr\<taskdispatcherdelegat\>& taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void SetSessionId(const std::string& sessionId)  | _Noch nicht dokumentiert._
public const std::string& GetSessionId() const  | _Noch nicht dokumentiert._
öffentliches void setcustomsettings (Konst Std:: Vector\<Std::p Air\<Std:: String, Std:: String\> \>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\> \>& getcustomsettings () Konstanten  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
public ~Settings()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="settings-function"></a>Settings-Funktion
Eine Schnittstelle für die Konfiguration des Profils

Parameter:  
* **mipcontext**: globale Kontext Einstellungen 


* **cachestoragetype**: speichert jeden zwischengespeicherten Status im Arbeitsspeicher oder auf dem Datenträger. 


* **observer**: Klasse, die die Schnittstelle PolicyProfile::Observer implementiert. Kann „nullptr“ lauten.


  
### <a name="getcachestoragetype-function"></a>Getcachestoragetype-Funktion
Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.

  
**Returns**: verwendeter Speichertyp
  
### <a name="getobserver-function"></a>Getobserver-Funktion
Ruft den Ereignisbeobachter ab.

  
**Rückgabe**: Ereignisbeobachter.
  
### <a name="getmipcontext-function"></a>Getmipcontext-Funktion
MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.

  
**Gibt Folgendes zurück**: MIP-Kontext
  
### <a name="gethttpdelegate-function"></a>Gethttpdelegatfunktion
Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).

  
**Gibt Folgendes zurück**: http-Delegat für http-Vorgänge
  
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
* **CustomSettings**: Liste von Name-Wert-Paaren.


  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.

  
**Rückgabe**: Liste von Name-Wert-Paaren
  
### <a name="settings-function"></a>~ Settings-Funktion
_Noch nicht dokumentiert._
