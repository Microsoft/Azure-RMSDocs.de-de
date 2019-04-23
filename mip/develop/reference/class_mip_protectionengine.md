---
title: mip::ProtectionEngine-Klasse
description: Dokumentiert die mip::protectionengine-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 60a61f5e06b5e76cbf0c557e7d489a8d618a8261
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60173154"
---
# <a name="class-mipprotectionengine"></a>mip::ProtectionEngine-Klasse 
Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
public void GetTemplatesAsync(const std::shared_ptr\<ProtectionEngine::Observer\>& observer, const std::shared_ptr\<void\>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
Public Std:: vector\<Std:: String\> GetTemplates (const Std:: shared_ptr\<"void"\>& Kontext)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
Öffentliche void GetRightsForLabelIdAsync (const Std:: String & DocumentId, const Std:: String & LabelId, const Std:: String & OwnerEmail, const Std:: shared_ptr\<ProtectionEngine::Observer\>& Observer, const std: : "shared_ptr"\<"void"\>& Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Public Std:: vector\<Std:: String\> GetRightsForLabelId (const Std:: String & DocumentId, const Std:: String & LabelId, const Std:: String & OwnerEmail, const Std:: shared_ptr\<"void"\> & Kontext)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
Öffentliche void CreateProtectionHandlerFromDescriptorAsync (const Std:: shared_ptr\<ProtectionDescriptor\>& Deskriptor, const ProtectionHandlerCreationOptions "und" Optionen "," const Std:: shared_ptr\< ProtectionHandler::Observer\>& Observer, const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Public Std:: shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromDescriptor (const Std:: shared_ptr\<ProtectionDescriptor\>& Deskriptor, const ProtectionHandlerCreationOptions & Optionen "," const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
Öffentliche void CreateProtectionHandlerFromPublishingLicenseAsync (const Std:: vector\<uint8_t\>& SerializedPublishingLicense, const ProtectionHandlerCreationOptions & Optionen, const Std:: shared_ptr\<ProtectionHandler::Observer\>& Observer, const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.
Public Std:: shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromPublishingLicense (const Std:: vector\<uint8_t\>&, const SerializedPublishingLicense ProtectionHandlerCreationOptions "und" Optionen "," const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.
Öffentliche void CreateProtectionHandlerFromProtectionInfoAsync (const Std:: vector\<uint8_t\>& SerializedPublishingLicense, const Std:: vector\<uint8_t\>& SerializedProtectionInfo, const Std:: shared_ptr\<ProtectionHandler::Observer\>& Observer, const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutz-Handler aus einem serialisierten Veröffentlichungslizenz und einen serialisierten Schutzdaten an.
Public Std:: shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromProtectionInfo (const Std:: vector\<uint8_t\>& SerializedPublishingLicense, const Std:: vector\< uint8_t\>& SerializedProtectionInfo, const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutz-Handler aus einem serialisierten Veröffentlichungslizenz und einen serialisierten Schutzdaten an.
Öffentliche void CreateProtectionHandlerFromPublishingLicenseContextAsync (const PublishingLicenseContext & PublishingLicenseContext, const ProtectionHandlerCreationOptions & Optionen, const Std:: shared_ptr\< ProtectionHandler::Observer\>& Observer, const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz
Public Std:: shared_ptr\<ProtectionHandler\> CreateProtectionHandlerFromPublishingLicenseContext (const PublishingLicenseContext & PublishingLicenseContext, const ProtectionHandlerCreationOptions & Optionen "," const Std:: shared_ptr\<"void"\>& Kontext)  |  Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz
  
## <a name="members"></a>Member
  
### <a name="getsettings-function"></a>GetSettings-Funktion
Ruft die Engine-Einstellungen ab.

  
**Gibt**: Engine-Einstellungen
  
### <a name="gettemplatesasync-function"></a>GetTemplatesAsync-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **observer**: Eine Klasse implementiert die [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) Schnittstelle 


* **context**: Clientkontext, die Clientkontext zurück an den Beobachter übergeben und optional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="gettemplates-function"></a>GetTemplates-Funktion
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **context**: Clientkontext, der Clientkontext auf optional übergeben werden [HttpDelegate](class_mip_httpdelegate.md)



  
**Gibt**: Liste der Vorlagen-IDs
  
### <a name="getrightsforlabelidasync-function"></a>GetRightsForLabelIdAsync-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: Dokument-ID, die die Metadaten des Dokuments zugeordnet 


* **labelId**: [Bezeichnung](class_mip_label.md) zugeordnete ID auf die Metadaten des Dokuments mit dem das Dokument erstellt haben. 


* **ownerEmail**: Besitzer des Dokuments 


* **observer**: Eine Klasse implementiert die [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) Schnittstelle 


* **context**: An diesem gleichen Kontext weitergeleitet werden [ProtectionEngine::Observer::OnGetRightsForLabelIdSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess-function) oder [ProtectionEngine::Observer::OnGetRightsForLabelIdFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure-function)


  
### <a name="getrightsforlabelid-function"></a>GetRightsForLabelId-Funktion
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: Dokument-ID, die die Metadaten des Dokuments zugeordnet 


* **labelId**: [Bezeichnung](class_mip_label.md) zugeordnete ID auf die Metadaten des Dokuments mit dem das Dokument erstellt haben. 


* **ownerEmail**: Besitzer des Dokuments 


* **context**: Diesem gleichen Kontext werden weitergeleitet, auf optional [HttpDelegate](class_mip_httpdelegate.md)



  
**Gibt**: Liste der Rechte
  
### <a name="createprotectionhandlerfromdescriptorasync-function"></a>CreateProtectionHandlerFromDescriptorAsync-Funktion
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: Ein [ProtectionDescriptor](class_mip_protectiondescriptor.md) , beschreibt die Konfiguration für den Schutz 


* **options**: Optionen für die Erstellung 


* **observer**: Eine Klasse implementiert die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) Schnittstelle 


* **context**: Clientkontext, die Clientkontext zurück an den Beobachter übergeben und optional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="createprotectionhandlerfromdescriptor-function"></a>CreateProtectionHandlerFromDescriptor-Funktion
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: Ein [ProtectionDescriptor](class_mip_protectiondescriptor.md) , beschreibt die Konfiguration für den Schutz 


* **options**: Optionen für die Erstellung 


* **context**: Clientkontext, die an optionalen Clientkontext übergeben werden [HttpDelegate](class_mip_httpdelegate.md)



  
**Gibt**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicenseasync-function"></a>CreateProtectionHandlerFromPublishingLicenseAsync-Funktion
Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.

Parameter:  
* **serializedPublishingLicense**: Eine serialisierte Veröffentlichungslizenz 


* **options**: Optionen für die Erstellung 


* **observer**: Eine Klasse implementiert die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) Schnittstelle 


* **context**: Clientkontext, die Clientkontext zurück an den Beobachter übergeben und optional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="createprotectionhandlerfrompublishinglicense-function"></a>CreateProtectionHandlerFromPublishingLicense-Funktion
Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.

Parameter:  
* **serializedPublishingLicense**: Eine serialisierte Veröffentlichungslizenz 


* **options**: Optionen für die Erstellung 


* **observer**: Eine Klasse implementiert die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) Schnittstelle 


* **context**: Clientkontext, die an optionalen Clientkontext übergeben werden [HttpDelegate](class_mip_httpdelegate.md)



  
**Gibt**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfromprotectioninfoasync-function"></a>CreateProtectionHandlerFromProtectionInfoAsync-Funktion
Erstellt einen Schutz-Handler aus einem serialisierten Veröffentlichungslizenz und einen serialisierten Schutzdaten an.

Parameter:  
* **serializedPublishingLicense**: Eine serialisierte Veröffentlichungslizenz 


* **serializedProtectionInfo**: Eine serialisierte Schutzdaten 


* **observer**: Eine Klasse implementiert die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) Schnittstelle 


* **context**: Clientkontext, der Clientkontext zurück an den Beobachter übergeben werden


  
### <a name="createprotectionhandlerfromprotectioninfo-function"></a>CreateProtectionHandlerFromProtectionInfo-Funktion
Erstellt einen Schutz-Handler aus einem serialisierten Veröffentlichungslizenz und einen serialisierten Schutzdaten an.

Parameter:  
* **serializedPublishingLicense**: Eine serialisierte Veröffentlichungslizenz 


* **serializedProtectionInfo**: Eine serialisierte Schutzdaten 


* **context**: Clientkontext, der Clientkontext zurück an den Beobachter übergeben werden



  
**Gibt**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicensecontextasync-function"></a>CreateProtectionHandlerFromPublishingLicenseContextAsync-Funktion
Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz

Parameter:  
* **publishingLicenseContext**: Eine vorab verarbeiteten Form der die serialisierten Lizenz 


* **options**: Optionen für die Erstellung 


* **observer**: Eine Klasse implementiert die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) Schnittstelle 


* **context**: Clientkontext, die Clientkontext zurück an den Beobachter übergeben und optional [HttpDelegate](class_mip_httpdelegate.md)


  
### <a name="createprotectionhandlerfrompublishinglicensecontext-function"></a>CreateProtectionHandlerFromPublishingLicenseContext function
Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz

Parameter:  
* **publishingLicenseContext**: Eine vorab verarbeiteten Form der die serialisierten Lizenz 


* **options**: Optionen für die Erstellung 


* **observer**: Eine Klasse implementiert die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md) Schnittstelle 


* **context**: Clientkontext, die an optionalen Clientkontext übergeben werden [HttpDelegate](class_mip_httpdelegate.md)



  
**Gibt**: [ProtectionHandler](class_mip_protectionhandler.md)