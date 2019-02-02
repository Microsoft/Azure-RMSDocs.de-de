---
title: mip::AddContentFooterAction-Klasse
description: 'Beschreibt die Klasse:: addcontentfooteraction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 064581d2b3a3c0ab9b926f0defe161dba46dfe49
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650849"
---
# <a name="class-mipaddcontentfooteraction"></a>mip::AddContentFooterAction-Klasse 
Eine Aktionsklasse, die angibt, dass dem Dokument Fußzeileninhalt hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  Eine API, mit der das Element des Fußzeileninhalts markiert wird.
public const std::string& GetText() const  |  Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.
public const std::string& GetFontName() const  |  Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.
public int GetFontSize() const  |  Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.
public const std::string& GetFontColor() const  |  Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.
public ContentMarkAlignment GetAlignment() const  |  Ruft die Ausrichtung der Fußzeile ab.
public int GetMargin() const  |  Ruft den Rand der Fußzeile im unteren Bereich ab
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>GetUIElementName-Funktion
Eine API, mit der das Element des Fußzeileninhalts markiert wird.

  
**Gibt**: Der Name, der für das UI-Element verwendet werden soll, der der Fußzeileninhalt enthält. Wenn der Fußzeileninhalt entfernt werden muss, wird der gleiche Name in [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) zurückgegeben.
  
### <a name="gettext-function"></a>GetText-Funktion
Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.

  
**Gibt**: Inhalt des Fußzeilentexts
  
### <a name="getfontname-function"></a>GetFontName-Funktion
Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Gibt**: Schriftartname. Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.

  
**Gibt**: Der Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>GetFontColor-Funktion
Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Gibt**: Schriftfarbe als Zeichenfolge (z. B. "#000000").
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung der Fußzeile ab.

  
**Gibt**: Der ContentMarkAlignment-Enumerator: LEFT|RIGHT|CENTER. 
  
**Siehe auch**: [ContentMarkAlignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand der Fußzeile im unteren Bereich ab

  
**Gibt**: Die Ränder im unteren Bereich des Dokuments (z. B. 10 mm).
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.