---
title: Die Klasse „mip::ProtectionDescriptor“
description: Referenz zur Klasse „mip::ProtectionDescriptor“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e723041af1eec7be7a839bf36f6d3db67b32447f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446548"
---
# <a name="class-mipprotectiondescriptor"></a>mip::ProtectionDescriptor-Klasse 
Beschreibung des Schutzes, der einem Inhaltselement zugeordnet ist.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public ProtectionType GetProtectionType() const  |  Ruft den Schutztyp ab, unabhängig davon, ob er aus der Protection SDK-Vorlage stammt oder nicht.
 public std::string GetOwner() const  |  Ruft den Besitzer für den Schutz ab.
 public std::string GetName() const  |  Ruft den Schutznamen ab.
 public std::string GetDescription() const  |  Ruft eine Beschreibung zum Schutz ab.
 public std::string GetTemplateId() const  |  Ruft ggf. die Schutzvorlagen-ID ab.
 public std::string GetLabelId() const  |  Ruft ggf. die Bezeichnungs-ID ab.
public std::vector<UserRights> GetUserRights() const  |  Ruft die Auflistung von Benutzerrechtszuordnungen ab.
public std::vector<UserRoles> GetUserRoles() const  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
public std::chrono::time_point<std::chrono::system_clock> GetContentValidUntil() const  |  Ruft den Ablaufzeitpunkt des Schutzes ab.
 public bool DoesAllowOfflineAccess() const  |  Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.
 public std::string GetReferrer() const  |  Ruft die Verweiseradresse des Schutzes ab.
public std::map<std::string, std::string> GetEncryptedAppData() const  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
public std::map<std::string, std::string> GetSignedAppData() const  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
  
## <a name="members"></a>Member
  
### <a name="protectiontype"></a>ProtectionType
Ruft den Schutztyp ab, unabhängig davon, ob er aus der Protection SDK-Vorlage stammt oder nicht.

  
**Rückgabe**: Typ des Schutzes
  
### <a name="getowner"></a>GetOwner
Ruft den Besitzer für den Schutz ab.

  
**Rückgabe**: Besitzer des Schutzes
  
### <a name="getname"></a>GetName
Ruft den Schutznamen ab.

  
**Rückgabe**: Schutzname
  
### <a name="getdescription"></a>GetDescription
Ruft eine Beschreibung zum Schutz ab.

  
**Rückgabe:** Schutzbeschreibung
  
### <a name="gettemplateid"></a>GetTemplateId
Ruft ggf. die Schutzvorlagen-ID ab.

  
**Rückgabe**: Vorlagen-ID
  
### <a name="getlabelid"></a>GetLabelId
Ruft ggf. die Bezeichnungs-ID ab.

  
**Rückgabe:** [Bezeichnung-ID](class_mip_label.md) Diese Eigenschaft wird nur in ProtectionDescriptors für bereits geschützten Inhalt aufgefüllt. Es handelt sich um ein Feld, das dann vom Server aufgefüllt wird, wenn geschützter Inhalt verarbeitet wird.
  
### <a name="userrights"></a>UserRights
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Rückgabe**: Sammlung von Benutzerrechtszuordnungen: Der Wert der Eigenschaft [UserRights](class_mip_userrights.md) ist leer, wenn der aktuelle Benutzer keinen Zugriff auf diese Informationen hat (er also nicht der Besitzer ist und nicht über das Recht „VIEWRIGHTSDATA“ verfügt).
  
### <a name="userroles"></a>UserRoles
Ruft die Auflistung von Benutzerrollenzuordnungen ab.

  
**Rückgabe**: Auflistung von Benutzerrollenzuordnungen
  
### <a name="getcontentvaliduntil"></a>GetContentValidUntil
Ruft den Ablaufzeitpunkt des Schutzes ab.

  
**Rückgabe:** Ablaufzeitpunkt des Schutzes
  
### <a name="doesallowofflineaccess"></a>DoesAllowOfflineAccess
Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.

  
**Rückgabe:** Legt fest, ob der Schutz den Zugriff auf Offlineinhalte erlaubt (standardmäßig auf TRUE festgelegt).
  
### <a name="getreferrer"></a>GetReferrer
Ruft die Verweiseradresse des Schutzes ab.

  
**Rückgabe:** Verweiseradresse des Schutzes. Der Verweiser ist ein URI, der dem Benutzer angezeigt werden kann, wenn dieser den Schutz für den Inhalt nicht aufheben kann. Dieser enthält Informationen dazu, wie der Benutzer die Berechtigung erhalten kann, auf den Inhalt zuzugreifen.
  
### <a name="getencryptedappdata"></a>GetEncryptedAppData
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.

  
**Rückgabe**: App-spezifische Daten. Ein [ProtectionHandler](class_mip_protectionhandler.md) kann ein Wörterbuch mit App-spezifischen Daten enthalten, die durch den Schutzdienst verschlüsselt wurden. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata) zugänglich sind
  
### <a name="getsignedappdata"></a>GetSignedAppData
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Rückgabe**: App-spezifische Daten. Ein [ProtectionHandler](class_mip_protectionhandler.md) kann ein Wörterbuch mit App-spezifischen Daten enthalten, die durch den Schutzdienst signiert wurden. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata) zugänglich sind.