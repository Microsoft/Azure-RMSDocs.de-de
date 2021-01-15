---
title: 'Class policyprofile:: Settings'
description: 'Dokumentiert die policyprofile:: Settings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 49cff6afb3f42b427e656f886eef82fff6bde51e
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98213350"
---
# <a name="class-policyprofilesettings"></a>Class policyprofile:: Settings 
Einstellungen, die während der Erstellung und Lebensdauer von PolicyProfile verwendet werden
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche Einstellungen (Konstante Std:: shared_ptr \<MipContext\>& mipcontext, cachestoragetype cachestoragetype, Konstanten Std:: shared_ptr \<PolicyProfile::Observer\>& Observer)  |  Eine Schnittstelle für die Konfiguration des Profils
Public cachestoragetype getcachestoragetype () Konstanten  |  Gibt an, ob Caches im Arbeitsspeicher oder auf dem Datenträger gespeichert werden.
Public Konstanten Std:: shared_ptr \<PolicyProfile::Observer\>& getobserver ()-Konstanten  |  Ruft den Ereignisbeobachter ab.
Public Std:: shared_ptr \<MipContext\> getmipcontext () Konstanten  |  MIP-Kontext, der den gemeinsamen Zustand für alle Profile darstellt.
public std::shared_ptr\<HttpDelegate\> GetHttpDelegate() const  |  Ruft den von der Anwendung bereitgestellten HTTP-Delegaten ab (falls vorhanden).
public void SetHttpDelegate(const std::shared_ptr\<HttpDelegate\>& httpDelegate)  |  Überschreibt den HTTP-Standardstapel mit dem Stapel des Clients.
Public Std:: shared_ptr \<TaskDispatcherDelegate\> gettaskdispatcherdelegat () Konstanten  |  Sie erhalten den von der Anwendung bereitgestellten taskdispatcher-Delegaten (sofern vorhanden).
öffentliches void settaskdispatcherdelegat (konstant Std:: shared_ptr \<TaskDispatcherDelegate\>& taskdispatcherdelegat)  |  Überschreiben Sie die standardmäßige asynchrone Aufgabenverteilung mit dem Client.
public void SetSessionId(const std::string& sessionId)  | _Noch nicht dokumentiert._
public const std::string& GetSessionId() const  | _Noch nicht dokumentiert._
öffentliches void setcustomsettings (Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& CustomSettings)  |  Legt die benutzerdefinierten Einstellungen fest, wird für Gating und Tests von Features verwendet.
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  |  Ruft die benutzerdefinierten Einstellungen ab, die für Gating und Tests von Features verwendet werden.
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
