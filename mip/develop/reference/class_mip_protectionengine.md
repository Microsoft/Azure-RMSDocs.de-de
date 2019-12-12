---
title: mip::ProtectionEngine-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 9eb44a39f32c2997729e6d77ddace96c580328cd
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "73557739"
---
# <a name="class-mipprotectionengine"></a>mip::ProtectionEngine-Klasse 
Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
öffentliches void gettemplatesasync (Konst Std:: shared_ptr\<schutzengine:: Observer\>& Observer, Konstante Std:: shared_ptr\<void\>& Kontext)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
Public Std:: Vector\<Std:: String\> gettemplates (Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
öffentliches void-GetRightsForLabelIdAsync (Konstante Std:: String & DocumentID, Konstante Std:: String & LabelId, Konstante Std:: String & Besitzer-e-Mail, Konstante Std:: String & delegateduseremail, Konstante Std:: shared_ptr\<Protection Engine:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: Vector\<Std:: String\> GetRightsForLabelId (Konstante Std:: String & DocumentID, Konstante Std:: String & LabelId, Konstante Std:: String & besitzemail, Konstante Std:: String & delegateduseremail, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
öffentliches void-Ereignis erstellungenschutzhandlerforpublishingasync (konstanter Schutz Handler::P ublishingsettings & Settings, Konstante Std:: shared_ptr\<schutzhandler:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> \| ateschutzhandlerforpublishing (konstanten Schutz Handler::P ublishingsettings & Settings, Konstante Std:: shared_ptr\<void\>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
öffentliches void-Ereignis erstellungshandlerforconsumptionasync (Konstante Schutz Handler:: consumptionsettings & Einstellungen, Konstante Std:: shared_ptr\<Schutz Handler:: Observer\>& Observer, Konstanten Std:: shared_ptr\<void\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> \| ateschutzhandlerforverbrauch (Konstante Schutz Handler:: consumptionsettings & Einstellungen, Konstante Std:: shared_ptr\<void\>& Kontext )  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Engine-Einstellungen ab.

  
**Rückgabe**: Engine-Einstellungen
  
### <a name="gettemplatesasync-function"></a>Gettemplatesasync-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **Observer**: eine Klasse, die die schutzengine:: Observer-Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Observer und optional httpdelegat zurückgegeben wird.


  
### <a name="gettemplates-function"></a>Gettemplates-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **Kontext**: Client Kontext, der an den optionalen httpdelegaten übergeben wird.



  
**Rückgabe**: Liste mit Vorlagen-IDs
  
### <a name="getrightsforlabelidasync-function"></a>GetRightsForLabelIdAsync-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: den Dokumentmetadaten zugeordnete Dokument-ID 


* **LabelId**: Bezeichnungs-ID, die den Dokument Metadaten zugeordnet ist, mit denen das Dokument erstellt wurde. 


* **ownerEmail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **Observer**: eine Klasse, die die schutzengine:: Observer-Schnittstelle implementiert. 


* **Kontext**: dieser Kontext wird an Schutz Modul:: Observer:: OnGetRightsForLabelIdSuccess oder schutzengine:: Observer:: OnGetRightsForLabelIdFailure weitergeleitet.


  
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


  
### <a name="createprotectionhandlerforconsumption-function"></a>Funktion "forateschutzhandlerforverbrauch"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Kontext**: Client Kontext, der an den optionalen httpdelegaten weitergeleitet wird.



  
**Gibt Folgendes zurück**: Schutz Handler