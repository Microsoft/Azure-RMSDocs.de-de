---
title: mip::ProtectionDescriptor-Klasse
description: Dokumentiert die MIP::p rotectiondescriptor-Klasse des MIP-SDKs (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 0d1f16f9bd14854911951adfc35aeea01ce493b9
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883517"
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
Public Std:: Vector\<userrollen\> getuserrollen () konstant  |  Ruft die Auflistung von Benutzerrollenzuordnungen ab.
öffentliches bool doescontentexpire () konstant  |  Überprüft, ob der Inhalt eine Ablaufzeit hat.
Public Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\> getcontentvaliduntil () Konstanten  |  Ruft den Ablaufzeitpunkt des Schutzes ab.
public bool DoesAllowOfflineAccess() const  |  Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.
public std::string GetReferrer() const  |  Ruft die Verweiseradresse des Schutzes ab.
Public Std:: map\<Std:: String, Std:: String\> getencryptedappdata () Konstanten  |  Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.
Public Std:: map\<Std:: String, Std:: String\> getsignetdappdata () Konstanten  |  Ruft anwendungsspezifische Daten ab, die signiert waren.
  
## <a name="members"></a>Member
  
### <a name="getprotectiontype-function"></a>Getschutztype-Funktion
Ruft den Schutztyp ab, unabhängig davon, ob er aus der Protection SDK-Vorlage stammt oder nicht.

  
**Gibt Folgendes zurück**: Typ des Schutzes
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft den Besitzer für den Schutz ab.

  
**Gibt Folgendes zurück**: Besitzer des Schutzes
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Schutznamen ab.

  
**Gibt Folgendes zurück**: Schutz Name
  
### <a name="getdescription-function"></a>GetDescription-Funktion
Ruft eine Beschreibung zum Schutz ab.

  
**Gibt Folgendes zurück**: Schutz Beschreibung
  
### <a name="gettemplateid-function"></a>Gettemplateid-Funktion
Ruft ggf. die Schutzvorlagen-ID ab.

  
**Gibt Folgendes zurück**: Vorlagen-ID
  
### <a name="getlabelid-function"></a>Getlabelid-Funktion
Ruft ggf. die Bezeichnungs-ID ab.

  
**Gibt Folgendes zurück**: [Bezeichnung](class_mip_label.md) ID diese Eigenschaft wird nur in schutzdeskriptoren für bereits vorhandene geschützte Inhalte aufgefüllt. Es handelt sich um ein Feld, das dann vom Server aufgefüllt wird, wenn geschützter Inhalt verarbeitet wird.
  
### <a name="getcontentid-function"></a>GetContentID-Funktion
Ruft ggf. die Inhalts-ID ab.

  
**Gibt Folgendes zurück**: Inhalts-ID
  
### <a name="getuserrights-function"></a>Getuserrights-Funktion
Ruft die Auflistung von Benutzerrechtszuordnungen ab.

  
**Gibt Folgendes zurück**: Sammlung von Benutzer-zu-Rechte-Zuordnungen der Wert der [Userrights](class_mip_userrights.md) -Eigenschaft ist leer, wenn der aktuelle Benutzer keinen Zugriff auf diese Informationen hat (d. h., wenn der Benutzer nicht der Besitzer ist und nicht über das Recht "vieschreightsdata" verfügt).
  
### <a name="getuserroles-function"></a>Getuserrollen-Funktion
Ruft die Auflistung von Benutzerrollenzuordnungen ab.

  
**Gibt Folgendes zurück**: Auflistung von Benutzerrollenzuordnungen
  
### <a name="doescontentexpire-function"></a>Doescontentexpire-Funktion
Überprüft, ob der Inhalt eine Ablaufzeit hat.

  
**Gibt Folgendes zurück**: True, wenn der Inhalt ablaufen kann, andernfalls false.
  
### <a name="getcontentvaliduntil-function"></a>Getcontentvaliduntil-Funktion
Ruft den Ablaufzeitpunkt des Schutzes ab.

  
**Gibt Folgendes zurück**: Ablaufzeit des Schutzes
  
### <a name="doesallowofflineaccess-function"></a>Doesallowofflineaccess-Funktion
Ruft ab, ob der Schutz den Zugriff auf Offlineinhalte erlaubt.

  
**Gibt Folgendes zurück**: Wenn der Schutz Offline Zugriff auf Inhalte zulässt oder nicht (Standard = true)
  
### <a name="getreferrer-function"></a>Getreferrer-Funktion
Ruft die Verweiseradresse des Schutzes ab.

  
**Gibt Folgendes zurück**: Schutz referenrer address der Verweiser ist ein URI, der für den Benutzer angezeigt wird, wenn der Schutz des Inhalts nicht aufgehoben werden kann. Dieser enthält Informationen dazu, wie der Benutzer die Berechtigung erhalten kann, auf den Inhalt zuzugreifen.
  
### <a name="getencryptedappdata-function"></a>Getencryptedappdata-Funktion
Ruft anwendungsspezifische Daten ab, die verschlüsselt waren.

  
**Gibt Folgendes zurück**: App-spezifische Daten ein Schutz [Handler](class_mip_protectionhandler.md) kann ein Wörterbuch mit App-spezifischen Daten enthalten, die vom Schutzdienst verschlüsselt wurden. Diese verschlüsselten Daten sind unabhängig von den signierten Daten, die über [ProtectionDescriptor::GetSignedAppData](#getsignedappdata-function) zugänglich sind
  
### <a name="getsignedappdata-function"></a>Getsignetdappdata-Funktion
Ruft anwendungsspezifische Daten ab, die signiert waren.

  
**Gibt Folgendes zurück**: App-spezifische Daten ein Schutz [Handler](class_mip_protectionhandler.md) kann ein Wörterbuch mit App-spezifischen Daten enthalten, die vom Schutzdienst signiert wurden. Diese signierten Daten sind unabhängig von den verschlüsselten Daten, die über [ProtectionDescriptor::GetEncryptedAppData](class_mip_protectiondescriptor.md#getencryptedappdata-function) zugänglich sind.