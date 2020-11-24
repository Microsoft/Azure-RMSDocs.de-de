---
title: Class Protection Engine
description: 'Dokumentiert die Schutz-Engine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: f87b65f85693850ea3344aa2b1340f9fc4de4e73
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567151"
---
# <a name="class-protectionengine"></a>Class Protection Engine 
Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
Public Std:: shared_ptr \<AsyncControl\> gettemplatesasync (Konst Std:: shared_ptr \<ProtectionEngine::Observer\>& Observer, Konstante Std:: shared_ptr \<void\>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
Public Std:: Vector \<std::shared_ptr\<TemplateDescriptor\> \> gettemplates (Konst Std:: shared_ptr \<void\>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
public bool isfeaturesupported (FeatureId FeatureId)  |  Die Überprüfung wird unterstützt.
Public Std:: shared_ptr \<AsyncControl\> GetRightsForLabelIdAsync (Konstante Std:: String& DocumentID, Konstante Std:: String& LabelId, Konstanten Std:: String& besitzemail, Konstante Std:: String& delegateduseremail, Konstante Std:: shared_ptr& \<ProtectionEngine::Observer\> Observer, Konstante Std:: shared_ptr \<void\>& context)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: Vector \<std::string\> GetRightsForLabelId (Konstante Std:: String& DocumentID, Konst Std:: String& LabelId, Konstante Std:: String& besitzemail, Konstante Std:: String& delegateduseremail, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: shared_ptr \<AsyncControl\> kreateschutzhandlerforpublishingasync (konstanter Schutz Handler::P ublishingsettings& Settings, Konstanten Std:: shared_ptr \<ProtectionHandler::Observer\>& Observer, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr \<ProtectionHandler\> kreateschutzhandlerforpublishing (Konst Schutz Handler::P ublishingsettings& Settings, Konstante Std:: shared_ptr \<void\>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr \<AsyncControl\> kreateschutzhandlerforconsumptionasync (Konstante Schutz Handler:: consumptionsettings& Settings, Konstanten Std:: shared_ptr \<ProtectionHandler::Observer\>& Observer, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr \<ProtectionHandler\> kreateschutzhandlerforconsua (konstanten Schutz Handler:: consumptionsettings& Settings, Konstante Std:: shared_ptr \<void\>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
public bool loadusercert (Konst Std:: shared_ptr \<void\>& Kontext)  |  Laden Sie das Zertifikat für den Benutzer Lizenzierungs Dienst vorab aus. Dies ist hilfreich, wenn das Laden des Hintergrunds durch das Laden mit der vorab Lizenz einen zusätzlichen Netzwerk Aufruf
Public Std:: shared_ptr \<AsyncControl\> loadusercertasync (Konstante Std:: shared_ptr \<ProtectionEngine::Observer\>& Observer, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Laden Sie das Zertifikat für den Benutzer Lizenzierungs Dienst vorab aus. Dies ist hilfreich, wenn das Laden des Hintergrunds durch das Laden mit der vorab Lizenz einen zusätzlichen Netzwerk Aufruf
öffentliches void registercontentfortrackingandrevocation (konstant Std:: Vector \<uint8_t\>& serializedpublishinglicense, Konstante Std:: String& ContentName, bool isownernotificationaktivierte, Konstante Std:: shared_ptr \<void\>& Kontext)  |  Registrieren Sie die Veröffentlichungs Lizenz (PL) für die Dokument Nachverfolgung & Sperrung.
Public Std:: shared_ptr \<AsyncControl\> registercontentfortrackingandrevocationasync (Konst Std:: Vector \<uint8_t\>& serializedpublishinglicense, Konstanten Std:: String& ContentName, bool isownernotificationaktivierte, Konstante Std:: shared_ptr \<ProtectionEngine::Observer\>& Observer, Konstante Std:: shared_ptr \<void\>& context)  |  Registrieren Sie die Veröffentlichungs Lizenz (PL) für die Dokument Nachverfolgung & Sperrung.
öffentliches void revokecontent (Konstante Std:: Vector \<uint8_t\>& serializedpublishinglicense, Konst Std:: shared_ptr \<void\>& context)  |  Führt eine Sperrung für den Inhalt durch.
Public Std:: shared_ptr \<AsyncControl\> revokecontentasync (Konstanten Std:: Vector \<uint8_t\>& serializedpublishinglicense, Konstante Std:: shared_ptr \<ProtectionEngine::Observer\>& Observer, Konstanten Std:: shared_ptr \<void\>& Kontext)  |  Führt eine Sperrung für den Inhalt durch.
  
## <a name="members"></a>Members
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Engine-Einstellungen ab.

  
**Rückgabe**: Engine-Einstellungen
  
### <a name="gettemplatesasync-function"></a>Gettemplatesasync-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **observer**: Klasse, die die Schnittstelle ProtectionEngine::Observer implementiert 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird. Der HttpDelegate ist optional.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="gettemplates-function"></a>Gettemplates-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **context**: Clientkontext, der verdeckt an einen optionalen HttpDelegate zurückgegeben wird.



  
**Rückgabe**: Liste mit Vorlagen-IDs
  
### <a name="isfeaturesupported-function"></a>Isfeaturesupported-Funktion
Die Überprüfung wird unterstützt.

Parameter:  
* **FeatureId**: ID der zu überprüfen Funktion



  
**Returns**: boolesches Ergebnis
  
### <a name="getrightsforlabelidasync-function"></a>GetRightsForLabelIdAsync-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: den Dokumentmetadaten zugeordnete Dokument-ID 


* **LabelId**: Bezeichnungs-ID, die den Dokument Metadaten zugeordnet ist, mit denen das Dokument erstellt wurde. 


* Besitzer **-e-Mail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **observer**: Klasse, die die Schnittstelle ProtectionEngine::Observer implementiert 


* **context**: derselbe Kontext wird an ProtectionEngine::Observer::OnGetTemplatesSuccess oder ProtectionEngine::Observer::OnGetTemplatesFailure weitergeleitet.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="getrightsforlabelid-function"></a>GetRightsForLabelId-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: den Dokumentmetadaten zugeordnete Dokument-ID 


* **LabelId**: Bezeichnungs-ID, die den Dokument Metadaten zugeordnet ist, mit denen das Dokument erstellt wurde. 


* **ownerEmail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **context**: derselbe Kontext wird an einen optionalen HttpDelegate weitergeleitet.



  
**Rückgabe**: Liste mit Rechten
  
### <a name="createprotectionhandlerforpublishingasync-function"></a>Funktion "forateschutzhandlerforpublishingasync"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="createprotectionhandlerforpublishing-function"></a>Funktion "forateschutzhandlerforpublishing"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Kontext**: Client Kontext, der an den optionalen httpdelegaten weitergeleitet wird.



  
**Gibt Folgendes zurück**: Schutz Handler
  
### <a name="createprotectionhandlerforconsumptionasync-function"></a>Funktion "forateschutzhandlerforconsumptionasync"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="createprotectionhandlerforconsumption-function"></a>Funktion "forateschutzhandlerforverbrauch"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Kontext**: Client Kontext, der an den optionalen httpdelegaten weitergeleitet wird.



  
**Gibt Folgendes zurück**: Schutz Handler
  
### <a name="loadusercert-function"></a>Loadusercert-Funktion
Laden Sie das Zertifikat für den Benutzer Lizenzierungs Dienst vorab aus. Dies ist hilfreich, wenn das Laden des Hintergrunds durch das Laden mit der vorab Lizenz einen zusätzlichen Netzwerk Aufruf

Parameter:  
* **Kontext**: Client Kontext, der an den optionalen httpdelegaten weitergeleitet wird.



  
**Gibt Folgendes zurück**: true, wenn erfolgreich geladen, sonst false.
  
### <a name="loadusercertasync-function"></a>Loadusercertasync-Funktion
Laden Sie das Zertifikat für den Benutzer Lizenzierungs Dienst vorab aus. Dies ist hilfreich, wenn das Laden des Hintergrunds durch das Laden mit der vorab Lizenz einen zusätzlichen Netzwerk Aufruf

Parameter:  
* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="registercontentfortrackingandrevocation-function"></a>Registercontentfortrackingandrevocation-Funktion
Registrieren Sie die Veröffentlichungs Lizenz (PL) für die Dokument Nachverfolgung & Sperrung.

Parameter:  
* **ContentName**: der Name, der dem durch die serializedpublishinglicense angegebenen Inhalt zugeordnet werden soll. Wenn die serializedpublishinglicense einen Inhalts Namen angibt, hat dieser Wert Vorrang. 


* **isownernotificationaktivierte**: Legen Sie diese Einstellung auf "true" fest, um den Besitzer bei der Entschlüsselung des Dokuments per e-Mail zu benachrichtigen, oder "false", um die Benachrichtigung nicht zu senden. 


* **Kontext**: Client Kontext, der an den optionalen httpdelegaten weitergeleitet wird.


  
### <a name="registercontentfortrackingandrevocationasync-function"></a>Registercontentfortrackingandrevocationasync-Funktion
Registrieren Sie die Veröffentlichungs Lizenz (PL) für die Dokument Nachverfolgung & Sperrung.

Parameter:  
* **serializedpublishinglicense**: serialisierte Veröffentlichungs Lizenz aus geschütztem Inhalt 


* **ContentName**: der Name, der dem durch die serializedpublishinglicense angegebenen Inhalt zugeordnet werden soll. Wenn die serializedpublishinglicense einen Inhalts Namen angibt, hat dieser Wert Vorrang. 


* **isownernotificationaktivierte**: Legen Sie diese Einstellung auf "true" fest, um den Besitzer bei der Entschlüsselung des Dokuments per e-Mail zu benachrichtigen, oder "false", um die Benachrichtigung nicht zu senden. 


* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="revokecontent-function"></a>Revokecontent-Funktion
Führt eine Sperrung für den Inhalt durch.

Parameter:  
* **serializedpublishinglicense**: serialisierte Veröffentlichungs Lizenz aus geschütztem Inhalt 


* **Kontext**: Client Kontext, der an den optionalen httpdelegaten weitergeleitet wird.


  
### <a name="revokecontentasync-function"></a>Revokecontentasync-Funktion
Führt eine Sperrung für den Inhalt durch.

Parameter:  
* **serializedpublishinglicense**: serialisierte Veröffentlichungs Lizenz aus geschütztem Inhalt 


* **observer**: eine Klasse, die die ProtectionHandler::Observer-Schnittstelle implementiert 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.