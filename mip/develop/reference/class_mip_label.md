---
title: mip::Label-Klasse
description: 'Dokumentiert die MIP:: Label-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 5a2444ab0abd944418a8d55eae35c5f6023282f7
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56253228"
---
# <a name="class-miplabel"></a>mip::Label-Klasse 
Eine Abstraktion für eine einzelne Microsoft Information Protection-Bezeichnung
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetId() const  |  Ruft die Bezeichnungs-ID ab
public const std::string& GetName() const  |  Ruft den Bezeichnungsnamen ab
public const std::string& GetDescription() const  |  Ruft die Beschreibung der Bezeichnung ab
public const std::string& GetColor() const  |  Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll
public int GetSensitivity() const  |  Ruft die Vertraulichkeit der Bezeichnung ab.
public const std::string& GetTooltip() const  |  Ruft die QuickInfo-Beschreibung für die Bezeichnung ab
public bool IsActive() const  |  Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
public std::weak_ptr\<Label\> GetParent() const  |  Ruft die übergeordnete Bezeichnung ab
Public const Std:: vector\<Std:: shared_ptr\<Bezeichnung\>\>& GetChildren() const  |  Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab
Public const Std:: vector\<Std:: Pair\<Std:: String, Std:: String\>\>& GetCustomSettings() const  |  Rufen Sie die benutzerdefinierten Einstellungen einer Bezeichnung.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Bezeichnungs-ID ab

  
**Gibt**: Die bezeichnungs-ID
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Bezeichnungsnamen ab

  
**Gibt**: Der Bezeichnungsname.
  
### <a name="getdescription-function"></a>GetDescription-Funktion
Ruft die Beschreibung der Bezeichnung ab

  
**Gibt**: Die Beschreibung der Bezeichnung.
  
### <a name="getcolor-function"></a>GetColor-Funktion
Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll

  
**Gibt**: Der Farbwert des Zeichenfolgenformats. „#RRGGBB“, wobei jedes RR, GG, BB ein Hexadezimalwert von 0 bis f ist
  
### <a name="getsensitivity-function"></a>GetSensitivity-Funktion
Ruft die Vertraulichkeit der Bezeichnung ab.

  
**Gibt**: Ein numerischer Wert. Ein höherer Wert steht für eine höhere Vertraulichkeit.
  
### <a name="gettooltip-function"></a>GetTooltip-Funktion
Ruft die QuickInfo-Beschreibung für die Bezeichnung ab

  
**Gibt**: Eine QuickInfo-Zeichenfolge.
  
### <a name="isactive-function"></a>IsActive-Funktion
Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
Es können nur aktive Bezeichnungen angewendet werden. Inaktive Bezeichnungen können nicht angewendet werden und werden nur zu Anzeigezwecken verwendet. 

  
**Gibt**: True, wenn die Bezeichnung aktiv ist; andernfalls "false".
  
### <a name="getparent-function"></a>GetParent-Funktion
Ruft die übergeordnete Bezeichnung ab

  
**Gibt**: Ein schwacher Zeiger auf das übergeordnete Element zu bezeichnen, wenn vorhanden; andernfalls wird einen leeren Zeiger zurückgegeben.
  
### <a name="getchildren-function"></a>GetChildren-Funktion
Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab

  
**Gibt**: Ein Vektor der freigegebenen Zeiger für Bezeichnungen.
  
### <a name="getcustomsettings-function"></a>GetCustomSettings-Funktion
Rufen Sie die benutzerdefinierten Einstellungen einer Bezeichnung.

  
**Gibt**: Ein Vektor von Schlüssel-Wert-Paaren, die benutzerdefinierte Einstellungen darstellt.
