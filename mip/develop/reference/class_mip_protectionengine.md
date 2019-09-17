---
title: mip::ProtectionEngine-Klasse
description: Dokumentiert die MIP::p rotectionengine-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 0bf87713b209e17d2728232f97f68946ca5d847f
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057657"
---
# <a name="class-mipprotectionengine"></a>mip::ProtectionEngine-Klasse 
Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
öffentliches void gettemplatesasync (Konst Std:: shared_ptr\<schutzengine:: Observer\>& Observer, Konst Std:: shared_ptr\<void\>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
Public Std:: Vector\<Std:: String\> gettemplates (Konst Std:: shared_ptr\<void\>& Kontext)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
public void GetRightsForLabelIdAsync (Konstante Std:: String & DocumentID, Konstante Std:: String & LabelId, Konstante Std:: String & besitzemail, Konstante Std:: String & delegateduseremail, Konstante Std:: shared_ptr\<schutzengine:: O bServer\>& Observer, Konst Std:: shared_ptr\<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: Vector\<Std:: String\> GetRightsForLabelId (Konstante Std:: String & DocumentID, Konstante Std:: String & LabelId, Konstante Std:: String & besitzemail, Konstanten Std:: String & delegateduseremail, Konstante Std:: Shared _Ptr\<void\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
öffentliches void-Element "detoriprotection handlerfromdescriptorasync" ("Konstante\<Std::\>shared_ptr schutzdescriptor & Descriptor", "Konstanten schutzhandlerkreationoptions" & "Optionen\< ", "Konstanten Std:: shared_ptr" Schutz Handler:: Observer\>& Observer, Konst Std:: shared_ptr\<void\>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> \| ateschutzhandlerfromdescriptor (Konstante Std:: shared_ptr\<schutzdescriptor\>& Deskriptor, Konstanten schutzhandlerkreationoptions & Optionen, Konst Std:: shared_ptr\<void\>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
öffentliches void-Ereignis für "detoriprotection handlerfrompublishinglicengasync" ("\<Konstante\>Std:: Vector uint8_t & serializedpublishinglicense", "Konst schutzhandlerkreationoptions & Optionen", "Konstante Std:: shared_ptr\<"Schutz Handler:: Observer\>& Observer, Konst Std:: shared_ptr\<void\>& context)  |  Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.
Public Std:: shared_ptr\<schutzhandler\> \| ateschutzhandlerfrompublishinglicense (Konstanten Std:: Vector\<uint8_t\>& serializedpublishinglicense, konstant Schutzhandlerkreationoptions & Optionen, Konst Std:: shared_ptr\<void\>& context)  |  Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.
öffentliches void-Ereignis "deaktivitätshandlerforpublishingasync" (konstanter Schutz Handler::P ublishingsettings & Settings, Konstanten Std:\<: shared_ptr schutzhandler:\>: Observer & Observer, Konstanten Std:: shared_ptr\<&\>Kontext void)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> \| ateschutzhandlerforpublishing (konstanten Schutz Handler::P ublishingsettings & Settings, Konstante Std:: shared_ptr\<void\>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
öffentliches void-Ereignis "kreateschutzhandlerforconsumptionasync" (Konstante Schutz Handler:: consumptionsettings & Settings, "Configuration Manager\<Std:: shared_ptr schutzhandler:: Observer\>& Observer, konstant Std:: shared_ptr\<&\>Kontext void)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<schutzhandler\> \| ateschutzhandlerforverbrauch (Konstante Schutz Handler:: consumptionsettings & Einstellungen, Konstante Std:: shared_ptr\<void\>& Kontext )  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Engine-Einstellungen ab.

  
**Gibt Folgendes zurück**: Engine-Einstellungen
  
### <a name="gettemplatesasync-function"></a>Gettemplatesasync-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **Beobachter**: Eine Klasse, die die [schutzengine:: Observer](class_mip_protectionengine_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Beobachter und optional [httpdelegat](class_mip_httpdelegate.md) zurückgegeben wird


  
### <a name="gettemplates-function"></a>Gettemplates-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **Kontext**: Client Kontext, der an den optionalen [httpdelegaten](class_mip_httpdelegate.md) übergeben wird.



  
**Gibt Folgendes zurück**: Liste der Vorlagen-IDs
  
### <a name="getrightsforlabelidasync-function"></a>GetRightsForLabelIdAsync-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **DocumentID**: Dokument-ID, die den Dokument Metadaten zugeordnet ist 


* **labelId**: [Bezeichnung](class_mip_label.md) ID, die den Dokument Metadaten zugeordnet ist, mit denen das Dokument erstellt wurde. 


* **ownerEmail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **Beobachter**: Eine Klasse, die die [schutzengine:: Observer](class_mip_protectionengine_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Der gleiche Kontext wird an Schutz- [Engine:: Observer:: OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) oder [schutzengine:: Observer:: OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function) weitergeleitet.


  
### <a name="getrightsforlabelid-function"></a>GetRightsForLabelId-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **DocumentID**: Dokument-ID, die den Dokument Metadaten zugeordnet ist 


* **labelId**: [Bezeichnung](class_mip_label.md) ID, die den Dokument Metadaten zugeordnet ist, mit denen das Dokument erstellt wurde. 


* **ownerEmail**: Besitzer des Dokuments 


* **A**: Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert, leer, wenn keine 


* **Kontext**: Derselbe Kontext wird an den optionalen [httpdelegaten](class_mip_httpdelegate.md) weitergeleitet.



  
**Gibt Folgendes zurück**: Liste der Rechte
  
### <a name="createprotectionhandlerfromdescriptorasync-function"></a>Funktion "kreateschutzhandlerfromdescriptorasync"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: Ein Schutz [Deskriptor](class_mip_protectiondescriptor.md) , der die Schutz Konfiguration beschreibt. 


* **Optionen**: Erstellungs Optionen 


* **Beobachter**: Eine Klasse, die die [schutzhandler:: Observer](class_mip_protectionhandler_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Beobachter und optional [httpdelegat](class_mip_httpdelegate.md) zurückgegeben wird


> Veraltet Diese Methode wird in Kürze als veraltet markiert, zugunsten von "kreateschutzhandlerforpublishingasync".
  
### <a name="createprotectionhandlerfromdescriptor-function"></a>Funktion "kreateschutzhandlerfromdescriptor"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: Ein Schutz [Deskriptor](class_mip_protectiondescriptor.md) , der die Schutz Konfiguration beschreibt. 


* **Optionen**: Erstellungs Optionen 


* **Kontext**: Client Kontext, der an den optionalen [httpdelegaten](class_mip_httpdelegate.md) zurückgegeben wird



  
**Gibt Folgendes zurück**: [ProtectionHandler](class_mip_protectionhandler.md)
> Veraltet Diese Methode wird in Kürze als veraltet markiert, zugunsten von "kreateschutzhandlerforpublishingasync".
  
### <a name="createprotectionhandlerfrompublishinglicenseasync-function"></a>Funktion "kreateschutzhandlerfrompublishinglicenlasync"
Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.

Parameter:  
* **serializedPublishingLicense**: Eine serialisierte Veröffentlichungs Lizenz 


* **Optionen**: Erstellungs Optionen 


* **Beobachter**: Eine Klasse, die die [schutzhandler:: Observer](class_mip_protectionhandler_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Beobachter und optional [httpdelegat](class_mip_httpdelegate.md) zurückgegeben wird


> Veraltet Diese Methode wird in Kürze als veraltet markiert, zugunsten von "kreateschutzhandlerforconsumptionasync".
  
### <a name="createprotectionhandlerfrompublishinglicense-function"></a>Funktion "kreateschutzhandlerfrompublishinglicense"
Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.

Parameter:  
* **serializedPublishingLicense**: Eine serialisierte Veröffentlichungs Lizenz 


* **Optionen**: Erstellungs Optionen 


* **Beobachter**: Eine Klasse, die die [schutzhandler:: Observer](class_mip_protectionhandler_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an den optionalen [httpdelegaten](class_mip_httpdelegate.md) zurückgegeben wird



  
**Gibt Folgendes zurück**: [ProtectionHandler](class_mip_protectionhandler.md)
> Veraltet Diese Methode wird in Kürze als veraltet markiert, zugunsten von "kreateschutzhandlerforverbrauch".
  
### <a name="createprotectionhandlerforpublishingasync-function"></a>Funktion "forateschutzhandlerforpublishingasync"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Beobachter**: Eine Klasse, die die [schutzhandler:: Observer](class_mip_protectionhandler_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Beobachter und optional [httpdelegat](class_mip_httpdelegate.md) weitergeleitet wird


  
### <a name="createprotectionhandlerforpublishing-function"></a>Funktion "forateschutzhandlerforpublishing"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Kontext**: Client Kontext, der an den optionalen [httpdelegaten](class_mip_httpdelegate.md) weitergeleitet wird



  
**Gibt Folgendes zurück**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerforconsumptionasync-function"></a>Funktion "forateschutzhandlerforconsumptionasync"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Beobachter**: Eine Klasse, die die [schutzhandler:: Observer](class_mip_protectionhandler_observer.md) -Schnittstelle implementiert. 


* **Kontext**: Client Kontext, der an Beobachter und optional [httpdelegat](class_mip_httpdelegate.md) weitergeleitet wird


  
### <a name="createprotectionhandlerforconsumption-function"></a>Funktion "forateschutzhandlerforverbrauch"
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **Einstellungen**: Schutzeinstellungen 


* **Kontext**: Client Kontext, der an den optionalen [httpdelegaten](class_mip_httpdelegate.md) weitergeleitet wird



  
**Gibt Folgendes zurück**: [ProtectionHandler](class_mip_protectionhandler.md)