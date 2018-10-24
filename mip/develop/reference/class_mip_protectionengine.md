---
title: Die Klasse „mip::ProtectionEngine“
description: Referenz zur Klasse „mip::ProtectionEngine“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: ddc8cfd58acb2a80d024978084b625f3d3728c87
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446735"
---
# <a name="class-mipprotectionengine"></a>mip::ProtectionEngine-Klasse 
Verwaltet schutzbezogene Aktionen, die sich auf eine bestimmte Identität beziehen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const Settings& GetSettings() const  |  Ruft die Engine-Einstellungen ab.
public void GetTemplatesAsync(const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
public std::vector<std::string> GetTemplates(const std::shared_ptr<void>& context)  |  Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.
public void GetRightsForLabelIdAsync(const std::string& documentId, const std::string& labelId, const std::string& ownerEmail, const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
public std::vector<std::string> GetRightsForLabelId(const std::string& documentId, const std::string& labelId, const std::string& ownerEmail, const std::shared_ptr<void>& context)  |  Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.
public void GetGrantingLabelIdsAsync(const std::shared_ptr<ProtectionEngine::Observer>& observer, const std::shared_ptr<void>& context)  |  Ruft die Sammlung von Beschriftungs-IDs ab, die einem Benutzer zur Verfügung stehen.
public std::vector<std::string> GetGrantingLabelIds(const std::shared_ptr<void>& context)  |  Ruft die Sammlung von Beschriftungs-IDs ab, die einem Benutzer zur Verfügung stehen.
public void CreateProtectionHandlerFromDescriptorAsync(const std::shared_ptr<ProtectionDescriptor>& descriptor, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
public std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromDescriptor(const std::shared_ptr<ProtectionDescriptor>& descriptor, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.
public void CreateProtectionHandlerFromPublishingLicenseAsync(const std::vector<uint8_t>& serializedPublishingLicense, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.
public std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicense(const std::vector<uint8_t>& serializedPublishingLicense, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.
public void CreateProtectionHandlerFromPublishingLicenseContextAsync(const PublishingLicenseContext& publishingLicenseContext, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<ProtectionHandler::Observer>& observer, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz
public std::shared_ptr<ProtectionHandler> CreateProtectionHandlerFromPublishingLicenseContext(const PublishingLicenseContext& publishingLicenseContext, const ProtectionHandlerCreationOptions& options, const std::shared_ptr<void>& context)  |  Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz
  
## <a name="members"></a>Member
  
### <a name="settings"></a>Einstellung
Ruft die Engine-Einstellungen ab.

  
**Rückgabe**: Engine-Einstellungen
  
### <a name="gettemplatesasync"></a>GetTemplatesAsync
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **observer**: Klasse, die die Schnittstelle [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) implementiert 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird. Der [HttpDelegate](class_mip_httpdelegate.md) ist optional.


  
### <a name="gettemplates"></a>GetTemplates
Ruft die Sammlung von Vorlagen ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **context**: Clientkontext, der verdeckt an einen optionalen [HttpDelegate](class_mip_httpdelegate.md) zurückgegeben wird.



  
**Rückgabe**: Liste mit Vorlagen-IDs
  
### <a name="getrightsforlabelidasync"></a>GetRightsForLabelIdAsync
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: den Dokumentmetadaten zugeordnete Dokument-ID 


* **labelId**: den Dokumentmetadaten, mit denen das Dokument erstellt wurde, zugeordnete [Beschriftungs](class_mip_label.md)-ID 


* **ownerEmail**: Besitzer des Dokuments 


* **observer**: Klasse, die die Schnittstelle [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) implementiert 


* **context**: derselbe Kontext wird an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) oder [ProtectionEngine::Observer::OnGetTemplatesFailure](class_mip_protectionengine_observer.md#ongetrightsforlabelidfailure) weitergeleitet.


  
### <a name="getrightsforlabelid"></a>GetRightsForLabelId
Ruft eine Sammlung von Rechten ab, die für eine Beschriftungs-ID für einen Benutzer verfügbar sind.

Parameter:  
* **documentId**: den Dokumentmetadaten zugeordnete Dokument-ID 


* **labelId**: den Dokumentmetadaten, mit denen das Dokument erstellt wurde, zugeordnete [Beschriftungs](class_mip_label.md)-ID 


* **ownerEmail**: Besitzer des Dokuments 


* **context**: derselbe Kontext wird an einen optionalen [HttpDelegate](class_mip_httpdelegate.md) weitergeleitet.



  
**Rückgabe**: Liste mit Rechten
  
### <a name="getgrantinglabelidsasync"></a>GetGrantingLabelIdsAsync
Ruft die Sammlung von Beschriftungs-IDs ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **observer**: Klasse, die die Schnittstelle [ProtectionEngine::Observer](class_mip_protectionengine_observer.md) implementiert 


* **context**: derselbe Kontext wird an [ProtectionEngine::Observer::OnGetTemplatesSuccess](class_mip_protectionengine_observer.md#ongetrightsforlabelidsuccess) oder „ProtectionEngine::Observer::OnGrantingLabelIdsFailure“ weitergeleitet.


  
### <a name="getgrantinglabelids"></a>GetGrantingLabelIds
Ruft die Sammlung von Beschriftungs-IDs ab, die einem Benutzer zur Verfügung stehen.

Parameter:  
* **context**: derselbe Kontext wird an einen optionalen [HttpDelegate](class_mip_httpdelegate.md) weitergeleitet.



  
**Rückgabe**: Liste mit Beschriftungs-IDs
  
### <a name="createprotectionhandlerfromdescriptorasync"></a>CreateProtectionHandlerFromDescriptorAsync
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: ein [ProtectionDescriptor](class_mip_protectiondescriptor.md), der die Schutzkonfiguration beschreibt 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird. Der [HttpDelegate](class_mip_httpdelegate.md) ist optional.


  
### <a name="protectionhandler"></a>ProtectionHandler
Erstellt einen Schutzhandler, in dem bestimmten Benutzern Rechte bzw. Rollen zugewiesen werden.

Parameter:  
* **descriptor**: ein [ProtectionDescriptor](class_mip_protectiondescriptor.md), der die Schutzkonfiguration beschreibt 


* **options**: Erstellungsoptionen 


* **context**: Clientkontext, der verdeckt an den optionalen [HttpDelegate](class_mip_httpdelegate.md) zurückgegeben wird.



  
**Rückgabe**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicenseasync"></a>CreateProtectionHandlerFromPublishingLicenseAsync
Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.

Parameter:  
* **serializedPublishingLicense**: eine serialisierte Veröffentlichungslizenz 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird. Der [HttpDelegate](class_mip_httpdelegate.md) ist optional.


  
### <a name="protectionhandler"></a>ProtectionHandler
Erstellt einen Schutzhandler aus einer serialisierten Veröffentlichungslizenz.

Parameter:  
* **serializedPublishingLicense**: eine serialisierte Veröffentlichungslizenz 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Clientkontext, der verdeckt an den optionalen [HttpDelegate](class_mip_httpdelegate.md) zurückgegeben wird.



  
**Rückgabe**: [ProtectionHandler](class_mip_protectionhandler.md)
  
### <a name="createprotectionhandlerfrompublishinglicensecontextasync"></a>CreateProtectionHandlerFromPublishingLicenseContextAsync
Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz

Parameter:  
* **publishingLicenseContext**: ein zuvor verarbeitetes Formular der serialisierten Veröffentlichungslizenz 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Clientkontext, der verdeckt an die Beobachter zurückgegeben wird. Der [HttpDelegate](class_mip_httpdelegate.md) ist optional.


  
### <a name="protectionhandler"></a>ProtectionHandler
Erstellt einen Schutzhandler aus dem Kontext einer Veröffentlichungslizenz

Parameter:  
* **publishingLicenseContext**: ein zuvor verarbeitetes Formular der serialisierten Veröffentlichungslizenz 


* **options**: Erstellungsoptionen 


* **observer**: eine Klasse, die die [ProtectionHandler::Observer](class_mip_protectionhandler_observer.md)-Schnittstelle implementiert 


* **context**: Clientkontext, der verdeckt an den optionalen [HttpDelegate](class_mip_httpdelegate.md) zurückgegeben wird.



  
**Rückgabe**: [ProtectionHandler](class_mip_protectionhandler.md)