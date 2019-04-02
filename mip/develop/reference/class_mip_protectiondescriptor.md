---
title: mip::ProtectionDescriptor-Klasse
description: Dokumentiert die mip::protectiondescriptor-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 922ff8811e5cb71d6d4d5920dfec80eadbcbc744
ms.sourcegitcommit: 8da0aa8f9bb9f91375580a703682d23a81a441bf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/02/2019
ms.locfileid: "58809793"
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
Public Std:: vector\<UserRights\> GetUserRights() const  |  Ruft die Auflistung von Benutzerrechtszuordnungen ab.
Public Std:: vector\<UserRoles\> GetUserRoles() const  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
public bool DoesContentExpire() const  |  Überprüft, ob der Inhalt eine Ablaufzeit hat oder nicht.
public std::chrono::time_point\<std::chrono::system_clock\> GetContentValidUntil() const  |  Ruft den Ablaufzeitpunkt des Schutzes ab.
public bool DoesAllowOfflineAccess() const  |  Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.
public std::string GetReferrer() const  |  Ruft die Verweiseradresse des Schutzes ab.
public std::map\<std::string, std::string\> GetEncryptedAppData() const  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
public std::map\<std::string, std::string\> GetSignedAppData() const  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
  
## <a name="members"></a>Member
  
### <a name="getprotectiontype-function"></a>GetProtectionType-Funktion
Ruft den Schutztyp ab, unabhängig davon, ob er aus der Protection SDK-Vorlage stammt oder nicht.

  
**Gibt**: Typ des Schutzes
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft den Besitzer für den Schutz ab.

  
**Gibt**: Besitzer des Schutzes
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Schutznamen ab.

  
**Gibt**: Schutz-name
  
### <a name="getdescription-function"></a>GetDescription-Funktion
Ruft eine Beschreibung zum Schutz ab.

  
**Gibt**: Beschreibung der Protection
  
### <a name="gettemplateid-function"></a>GetTemplateId-Funktion
Ruft ggf. die Schutzvorlagen-ID ab.

  
**Gibt**: Vorlagen-ID
  
### <a name="getlabelid-function"></a>GetLabelId-Funktion
Ruft ggf. die Bezeichnungs-ID ab.

  
**Gibt**: [Bezeichnung](class_mip_label.md) diese Eigenschaft nur in ProtectionDescriptors werden, für die bereits vorhandene aufgefüllt wird ID, geschützte Inhalte. Es handelt sich um ein Feld, das dann vom Server aufgefüllt wird, wenn geschützter Inhalt verarbeitet wird.
  
### <a name="getuserrights-function"></a>GetUserRights-Funktion
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Gibt**: Auflistung von Zuordnungen für Benutzer-zu-Rechte den Wert des der [UserRights](class_mip_userrights.md) -Eigenschaft ist leer, wenn der aktuelle Benutzer keinen Zugriff auf diese Informationen hat (d.h., wenn der Benutzer nicht der Besitzer ist und verfügt nicht über das Recht ViewRightsData verfügt).
  
### <a name="getuserroles-function"></a>GetUserRoles-Funktion
Ruft die Auflistung von Benutzerrollenzuordnungen ab.

  
**Gibt**: Auflistung von Benutzerrollenzuordnungen
  
### <a name="doescontentexpire-function"></a>DoesContentExpire-Funktion
Überprüft, ob der Inhalt eine Ablaufzeit hat oder nicht.

  
**Gibt**: True, wenn Inhalt ablaufen kann, andernfalls false
  
### <a name="getcontentvaliduntil-function"></a>GetContentValidUntil-Funktion
Ruft den Ablaufzeitpunkt des Schutzes ab.

  
**Gibt**: Schutz für den Ablauf
  
### <a name="doesallowofflineaccess-function"></a>DoesAllowOfflineAccess-Funktion
Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.

  
**Gibt**: Wenn Schutz den Zugang zu Offlineinhalten oder nicht erlaubt (Standardwert = True)
  
### <a name="getreferrer-function"></a>GetReferrer-Funktion
Ruft die Verweiseradresse des Schutzes ab.

  
**Gibt**: Referreradresse der Schutz wird der Verweiser ein URI, der für den Benutzer anzeigbaren ist, wenn sie den Inhalt den Schutz aufheben können nicht an. Dieser enthält Informationen dazu, wie der Benutzer die Berechtigung erhalten kann, auf den Inhalt zuzugreifen.
  
### <a name="getencryptedappdata-function"></a>GetEncryptedAppData-Funktion
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.

  
**Gibt**: App-Specific Data eine [ProtectionHandler](class_mip_protectionhandler.md) möglicherweise enthalten ein Wörterbuch mit anwendungsspezifischen Daten, die von den Schutzdienst verschlüsselt wurde. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [ProtectionDescriptor::GetSignedAppData](class_mip_protectiondescriptor.md#getsignedappdata-function) zugänglich sind
  
### <a name="getsignedappdata-function"></a>GetSignedAppData-Funktion
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Gibt**: App-Specific Data eine [ProtectionHandler](class_mip_protectionhandler.md) möglicherweise enthalten ein Wörterbuch mit anwendungsspezifischen Daten, die von den Schutzdienst signiert wurde. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata-function) zugänglich sind.
