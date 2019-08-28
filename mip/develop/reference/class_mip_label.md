---
title: mip::Label-Klasse
description: 'Dokumentiert die MIP:: Label-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 364f28ee45b20208be4ac31b30a11bef389fc7b4
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054698"
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
Public Std:: weak_ptr\<Label\> GetParent () Konstanten  |  Ruft die übergeordnete Bezeichnung ab
Public Konstanten Std::\<Vector Std:: shared_ptr\<Label\>\>& GetChildren () Konstanten  |  Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () Konstanten  |  Die benutzerdefinierten Einstellungen einer Bezeichnung werden angezeigt.
public ActionSource GetActionSource() const  |  Ruft die Aktions Quelle der Bezeichnung ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Bezeichnungs-ID ab

  
**Gibt Folgendes zurück**: Die Bezeichnungs-ID.
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Bezeichnungsnamen ab

  
**Gibt Folgendes zurück**: Der Name der Bezeichnung.
  
### <a name="getdescription-function"></a>GetDescription-Funktion
Ruft die Beschreibung der Bezeichnung ab

  
**Gibt Folgendes zurück**: Die Beschreibung der Bezeichnung.
  
### <a name="getcolor-function"></a>GetColor-Funktion
Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll

  
**Gibt Folgendes zurück**: Farbwert das Zeichen folgen Format. „#RRGGBB“, wobei jedes RR, GG, BB ein Hexadezimalwert von 0 bis f ist
  
### <a name="getsensitivity-function"></a>Getsensitivität-Funktion
Ruft die Vertraulichkeit der Bezeichnung ab.

  
**Gibt Folgendes zurück**: Ein numerischer Wert. Ein höherer Wert steht für eine höhere Vertraulichkeit.
  
### <a name="gettooltip-function"></a>GetToolTip-Funktion
Ruft die QuickInfo-Beschreibung für die Bezeichnung ab

  
**Gibt Folgendes zurück**: Eine QuickInfo-Zeichenfolge.
  
### <a name="isactive-function"></a>IsActive-Funktion
Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
Es können nur aktive Bezeichnungen angewendet werden. Inaktive Bezeichnungen können nicht angewendet werden und werden nur zu Anzeigezwecken verwendet. 

  
**Gibt Folgendes zurück**: True, wenn die Bezeichnung aktiv ist, andernfalls false.
  
### <a name="getparent-function"></a>GetParent-Funktion
Ruft die übergeordnete Bezeichnung ab

  
**Gibt Folgendes zurück**: Ein schwacher Zeiger auf die übergeordnete Bezeichnung, wenn vorhanden ist, andernfalls ein leerer Zeiger.
  
### <a name="getchildren-function"></a>GetChildren-Funktion
Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab

  
**Gibt Folgendes zurück**: Ein Vektor von freigegebenen Zeigern auf Bezeichnungen.
  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Die benutzerdefinierten Einstellungen einer Bezeichnung werden angezeigt.

  
**Gibt Folgendes zurück**: Ein Vektor von Schlüssel-Wert-Paaren, die benutzerdefinierte Einstellungen darstellen.
  
### <a name="getactionsource-function"></a>Getaktionsource-Funktion
Ruft die Aktions Quelle der Bezeichnung ab.

  
**Gibt Folgendes zurück**: [Aktions](class_mip_action.md) Quelle