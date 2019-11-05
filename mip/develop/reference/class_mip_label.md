---
title: mip::Label-Klasse
description: 'Dokumentiert die MIP:: Label-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 5bdc88746a8921f306d9d52dbe75f3c2b826a5b6
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560139"
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
Public Konstanten Std:: String & getautotooltip () Konstanten  |  Hiermit wird die QuickInfo-Beschreibung der Klassifizierung angezeigt, die dazu führt, dass diese Bezeichnung angewendet wird.
public bool IsActive() const  |  Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
Public Std:: weak_ptr\<Bezeichnung\> GetParent () Konstanten  |  Ruft die übergeordnete Bezeichnung ab
Public Konstanten Std:: Vector\<Std:: shared_ptr\<Label\>\>& GetChildren () Konstanten  |  Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& getcustomsettings () konstant.  |  Die benutzerdefinierten Einstellungen einer Bezeichnung werden angezeigt.
public ActionSource GetActionSource() const  |  Ruft die Aktions Quelle der Bezeichnung ab.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die Bezeichnungs-ID ab

  
**Rückgabe**: Bezeichnungs-ID.
  
### <a name="getname-function"></a>GetName-Funktion
Ruft den Bezeichnungsnamen ab

  
**Rückgabe**: der Bezeichnungsname.
  
### <a name="getdescription-function"></a>GetDescription-Funktion
Ruft die Beschreibung der Bezeichnung ab

  
**Rückgabe**: die Beschreibung der Bezeichnung.
  
### <a name="getcolor-function"></a>GetColor-Funktion
Ruft die Farbe ab, in der die Bezeichnung angezeigt werden soll

  
**Rückgabe**: der Farbwert des Zeichenfolgenformats. „#RRGGBB“, wobei jedes RR, GG, BB ein Hexadezimalwert von 0 bis f ist
  
### <a name="getsensitivity-function"></a>Getsensitivität-Funktion
Ruft die Vertraulichkeit der Bezeichnung ab.

  
**Rückgabe**: ein numerischer Wert Ein höherer Wert steht für eine höhere Vertraulichkeit.
  
### <a name="gettooltip-function"></a>GetToolTip-Funktion
Ruft die QuickInfo-Beschreibung für die Bezeichnung ab

  
**Rückgabe**: eine QuickInfo-Zeichenfolge.
  
### <a name="getautotooltip-function"></a>Getautotooltip-Funktion
Hiermit wird die QuickInfo-Beschreibung der Klassifizierung angezeigt, die dazu führt, dass diese Bezeichnung angewendet wird.

  
**Rückgabe**: eine QuickInfo-Zeichenfolge.
  
### <a name="isactive-function"></a>IsActive-Funktion
Ruft einen booleschen Wert ab, der angibt, ob die Bezeichnung aktiv ist
Es können nur aktive Bezeichnungen angewendet werden. Inaktive Bezeichnungen können nicht angewendet werden und werden nur zu Anzeigezwecken verwendet. 

  
**Rückgabe**: TRUE, wenn die Bezeichnung aktiv ist; andernfalls wird FALSE zurückgegeben.
  
### <a name="getparent-function"></a>GetParent-Funktion
Ruft die übergeordnete Bezeichnung ab

  
**Rückgabe**: ein schwacher Zeiger auf das übergeordnete Element, sofern vorhanden; andernfalls wird ein leerer Zeiger zurückgegeben.
  
### <a name="getchildren-function"></a>GetChildren-Funktion
Ruft die untergeordneten Bezeichnungen der aktuellen Bezeichnung ab

  
**Rückgabe**: ein Vektor der freigegebenen Zeiger für Bezeichnungen.
  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Die benutzerdefinierten Einstellungen einer Bezeichnung werden angezeigt.

  
**Returns**: ein Vektor von Schlüssel-Wert-Paaren, die benutzerdefinierte Einstellungen darstellen.
  
### <a name="getactionsource-function"></a>Getaktionsource-Funktion
Ruft die Aktions Quelle der Bezeichnung ab.

  
**Returns**: Aktions Quelle