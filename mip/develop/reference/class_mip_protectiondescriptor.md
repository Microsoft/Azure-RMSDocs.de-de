---
title: Klassen Schutz Deskriptor
description: 'Dokumentiert die Schutz Deskriptor:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: ad643c235f322a32239d702aa4ecafd3f0e36792
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214693"
---
# <a name="class-protectiondescriptor"></a>Klassen Schutz Deskriptor 
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
Public Std:: String getContentID () Konstanten  |  Ruft ggf. die Inhalts-ID ab.
public std::vector\<UserRights\> GetUserRights() const  |  Ruft die Auflistung von Benutzerrechtszuordnungen ab.
public std::vector\<UserRoles\> GetUserRoles() const  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
öffentliches bool doescontentexpire () konstant  |  Überprüft, ob der Inhalt eine Ablaufzeit hat.
Public Std:: Chrono:: time_point \<std::chrono::system_clock\> getcontentvaliduntil () Konstanten  |  Ruft den Ablaufzeitpunkt des Schutzes ab.
public bool DoesAllowOfflineAccess() const  |  Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.
public std::string GetReferrer() const  |  Ruft die Verweiseradresse des Schutzes ab.
Public Std:: map \<std::string, std::string\> getencryptedappdata () Konstanten  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
Public Std:: map \<std::string, std::string\> getsignetdappdata () Konstanten  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
Public Std:: String getdoublekeyurl () Konstanten  |  Ruft die doppelte Schlüssel-URL ab, die für den benutzerdefinierten Schutz verwendet werden soll.
  
## <a name="members"></a>Member
  
### <a name="getprotectiontype-function"></a>Getschutztype-Funktion
Ruft den Schutztyp ab, unabhängig davon, ob er aus der Protection SDK-Vorlage stammt oder nicht.

  
**Rückgabe**: Typ des Schutzes
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft den Besitzer für den Schutz ab.

  
**Rückgabe**: Besitzer des Schutzes
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Schutznamen ab.

  
**Rückgabe**: Schutzname
  
### <a name="getdescription-function"></a>GetDescription-Funktion
Ruft eine Beschreibung zum Schutz ab.

  
**Rückgabe:** Schutzbeschreibung
  
### <a name="gettemplateid-function"></a>Gettemplateid-Funktion
Ruft ggf. die Schutzvorlagen-ID ab.

  
**Gibt Folgendes zurück**: Vorlagen-ID
  
### <a name="getlabelid-function"></a>Getlabelid-Funktion
Ruft ggf. die Bezeichnungs-ID ab.

  
**Returns**: Bezeichnungs-ID diese Eigenschaft wird nur in schutzdeskriptoren für bereits vorhandene geschützte Inhalte aufgefüllt. Es handelt sich um ein Feld, das dann vom Server aufgefüllt wird, wenn geschützter Inhalt verarbeitet wird.
  
### <a name="getcontentid-function"></a>GetContentID-Funktion
Ruft ggf. die Inhalts-ID ab.

  
**Gibt Folgendes zurück**: Inhalts-ID
  
### <a name="getuserrights-function"></a>Getuserrights-Funktion
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Rückgabe**: Sammlung von Benutzerrechtszuordnungen: Der Wert der Eigenschaft UserRights ist leer, wenn der aktuelle Benutzer keinen Zugriff auf diese Informationen hat (er also nicht der Besitzer ist und nicht über das Recht „VIEWRIGHTSDATA“ verfügt).
  
### <a name="getuserroles-function"></a>Getuserrollen-Funktion
Ruft die Auflistung von Benutzerrollenzuordnungen ab.

  
**Rückgabe**: Auflistung von Benutzerrollenzuordnungen
  
### <a name="doescontentexpire-function"></a>Doescontentexpire-Funktion
Überprüft, ob der Inhalt eine Ablaufzeit hat.

  
**Gibt Folgendes zurück**: true, wenn der Inhalt ablaufen kann, andernfalls false.
  
### <a name="getcontentvaliduntil-function"></a>Getcontentvaliduntil-Funktion
Ruft den Ablaufzeitpunkt des Schutzes ab.

  
**Rückgabe:** Ablaufzeitpunkt des Schutzes
  
### <a name="doesallowofflineaccess-function"></a>Doesallowofflineaccess-Funktion
Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.

  
**Rückgabe:** Legt fest, ob der Schutz den Zugriff auf Offlineinhalte erlaubt (standardmäßig auf TRUE festgelegt).
  
### <a name="getreferrer-function"></a>Getreferrer-Funktion
Ruft die Verweiseradresse des Schutzes ab.

  
**Rückgabe:** Verweiseradresse des Schutzes. Der Verweiser ist ein URI, der dem Benutzer angezeigt werden kann, wenn dieser den Schutz für den Inhalt nicht aufheben kann. Dieser enthält Informationen dazu, wie der Benutzer die Berechtigung erhalten kann, auf den Inhalt zuzugreifen.
  
### <a name="getencryptedappdata-function"></a>Getencryptedappdata-Funktion
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.

  
**Rückgabe**: App-spezifische Daten. Ein ProtectionHandler kann ein Wörterbuch mit App-spezifischen Daten enthalten, die durch den Schutzdienst verschlüsselt wurden. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über ProtectionDescriptor::GetSignedAppData zugänglich sind
  
### <a name="getsignedappdata-function"></a>Getsignetdappdata-Funktion
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Rückgabe**: App-spezifische Daten. Ein ProtectionHandler kann ein Wörterbuch mit App-spezifischen Daten enthalten, die durch den Schutzdienst signiert wurden. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über ProtectionDescriptor::GetEncryptedAppData zugänglich sind.
  
### <a name="getdoublekeyurl-function"></a>Getdoublekeyurl-Funktion
Ruft die doppelte Schlüssel-URL ab, die für den benutzerdefinierten Schutz verwendet werden soll.

  
**Gibt Folgendes zurück**: doppelte Schlüssel-URL die doppelte Schlüssel-URL, die in benutzerdefinierten Anforderungen zum Schutz von Informationen mit einem zweiten Schlüssel verwendet wird.