---
title: mip::ProtectionDescriptor-Klasse
description: Dokumentiert die MIP::p rotectiondescriptor-Klasse des MIP-SDKs (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 43871eeae67cd55cc85b06f22c5dd6e76fb91f2f
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77487037"
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
Public Std:: String getContentID () Konstanten  |  Ruft ggf. die Inhalts-ID ab.
Public Std:: Vector\<Userrights\> getuserrights () Konstanten  |  Ruft die Auflistung von Benutzerrechtszuordnungen ab.
Public Std:: Vector\<userrollen\> getuserrollen () konstant.  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
öffentliches bool doescontentexpire () konstant  |  Überprüft, ob der Inhalt eine Ablaufzeit hat.
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getcontentvaliduntil () konstant.  |  Ruft den Ablaufzeitpunkt des Schutzes ab.
public bool DoesAllowOfflineAccess() const  |  Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.
public std::string GetReferrer() const  |  Ruft die Verweiseradresse des Schutzes ab.
Public Std:: Map\<Std:: String, Std:: String\> getencryptedappdata () konstant.  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
Public Std:: Map\<Std:: String, Std:: String\> getsignetdappdata () Konstanten  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
  
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

  
**Rückgabe**: Vorlagen-ID
  
### <a name="getlabelid-function"></a>Getlabelid-Funktion
Ruft ggf. die Bezeichnungs-ID ab.

  
**Returns**: Bezeichnungs-ID diese Eigenschaft wird nur in schutzdeskriptoren für bereits vorhandene geschützte Inhalte aufgefüllt. Es handelt sich um ein Feld, das dann vom Server aufgefüllt wird, wenn geschützter Inhalt verarbeitet wird.
  
### <a name="getcontentid-function"></a>GetContentID-Funktion
Ruft ggf. die Inhalts-ID ab.

  
**Gibt Folgendes zurück**: Inhalts-ID
  
### <a name="getuserrights-function"></a>Getuserrights-Funktion
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Gibt Folgendes zurück**: Auflistung von Benutzer-zu-Rechte-Zuordnungen der Wert der Userrights-Eigenschaft ist leer, wenn der aktuelle Benutzer keinen Zugriff auf diese Informationen hat (d. h., wenn der Benutzer nicht der Besitzer ist und nicht über das Recht "vieschreightsdata" verfügt).
  
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

  
**Returns**: App-spezifische Daten ein Schutz Handler kann ein Wörterbuch mit App-spezifischen Daten enthalten, die vom Schutzdienst verschlüsselt wurden. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über Schutz Deskriptor:: getsignetdappdata zugänglich sind.
  
### <a name="getsignedappdata-function"></a>Getsignetdappdata-Funktion
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Returns**: App-spezifische Daten ein Schutz Handler kann ein Wörterbuch mit App-spezifischen Daten enthalten, die vom Schutzdienst signiert wurden. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, auf die über Schutz Deskriptor:: getencryptedappdata zugegriffen werden kann.