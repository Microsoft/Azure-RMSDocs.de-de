---
title: mip::ProtectionEngine-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 23f9f54a3f9701d0c9321b7ba643ed7dd3f47be1
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77486833"
---
# <a name="class-mipprotectionengine"></a>mip::ProtectionEngine-Klasse 
Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
Public Std:: shared_ptr\<AsyncControl\> gettemplatesasync (konstant Std:: shared_ptr\<schutzengine:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
Public Std:: Vector\<Std:: shared_ptr\<templateDescriptor\>\> gettemplates (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
public bool isfeaturesupported (FeatureId FeatureId)  |  Die Überprüfung wird unterstützt.
Public Std:: shared_ptr\<AsyncControl\> GetRightsForLabelIdAsync (konstant Std:: String & DocumentID, Konst Std:: String & LabelId, Konstante Std:: String & besitzemail, Konstante Std:: String & delegateduseremail, Konstante Std:: shared_ptr\<schutzengine:: Observer\>& Observer, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: Vector\<Std:: String\> GetRightsForLabelId (Konstante Std:: String & DocumentID, Konstante Std:: String & LabelId, Konstante Std:: String & besitzemail, Konstante Std:: String & delegateduseremail, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: shared_ptr\<AsyncControl\> kreateschutzhandlerforpublishingasync (konstanter Schutz Handler::P ublishingsettings & Settings, Configuration Manager Std:: shared_ptr\<Protection Handler:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> kreateschutzhandlerforpublishing (konstanten Schutz Handler::P ublishingsettings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<AsyncControl\> kreateschutzhandlerforconsumptionasync (Konst schutzhandler:: consumptionsettings & Settings, Konstante Std:: shared_ptr\<Protection Handler:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> kreateschutzhandlerforconsuler (konstanten Schutz Handler:: consumptionsettings & Settings, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
public bool loadusercert (konstant Std:: shared_ptr\<void\>& Kontext)  |  Laden Sie das Zertifikat für den Benutzer Lizenzierungs Dienst vorab aus. Dies ist hilfreich, wenn das Laden des Hintergrunds durch das Laden mit der vorab Lizenz einen zusätzlichen Netzwerk Aufruf
Public Std:: shared_ptr\<AsyncControl\> loadusercertasync (Konstante Std:: shared_ptr\<schutzengine:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Laden Sie das Zertifikat für den Benutzer Lizenzierungs Dienst vorab aus. Dies ist hilfreich, wenn das Laden des Hintergrunds durch das Laden mit der vorab Lizenz einen zusätzlichen Netzwerk Aufruf
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Engine-Einstellungen ab.

  
**Rückgabe**: Engine-Einstellungen
  
### <a name="gettemplatesasync-function"></a>Gettemplatesasync-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **Observer**: eine Klasse, die die schutzengine:: Observer-Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Observer und optional httpdelegat zurückgegeben wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="gettemplates-function"></a>Gettemplates-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **Kontext**: Client Kontext, der an den optionalen httpdelegaten übergeben wird.



  
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


* **ownerEmail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **Observer**: eine Klasse, die die schutzengine:: Observer-Schnittstelle implementiert. 


* **Kontext**: dieser Kontext wird an Schutz Modul:: Observer:: OnGetRightsForLabelIdSuccess oder schutzengine:: Observer:: OnGetRightsForLabelIdFailure weitergeleitet.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.
  
### <a name="getrightsforlabelid-function"></a>GetRightsForLabelId-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: den Dokumentmetadaten zugeordnete Dokument-ID 


* **LabelId**: Bezeichnungs-ID, die den Dokument Metadaten zugeordnet ist, mit denen das Dokument erstellt wurde. 


* **ownerEmail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **Kontext**: derselbe Kontext wird an den optionalen httpdelegaten weitergeleitet.



  
**Rückgabe**: Liste mit Rechten
  
### <a name="createprotectionhandlerforpublishingasync-function"></a>Funktion "forateschutzhandlerforpublishingasync"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Observer**: eine Klasse, die die schutzhandler:: Observer-Schnittstelle implementiert. 


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


* **Observer**: eine Klasse, die die schutzhandler:: Observer-Schnittstelle implementiert. 


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
* **Observer**: eine Klasse, die die schutzhandler:: Observer-Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Beobachter und optional httpdelegat weitergeleitet wird.



  
**Gibt Folgendes zurück**: Async-Steuerelement Objekt.