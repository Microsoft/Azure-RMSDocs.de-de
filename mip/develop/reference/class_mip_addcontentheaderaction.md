---
title: mip::AddContentHeaderAction-Klasse
description: 'Beschreibt die Klasse:: addcontentheaderaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 8cd04bc610944bbbdf00873267161b06a9c09038
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650934"
---
# <a name="class-mipaddcontentheaderaction"></a>mip::AddContentHeaderAction-Klasse 
Eine Aktionsklasse, die angibt, dass der Inhaltsheader hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  Eine API, mit der das Inhaltsheaderelement markiert wird
public const std::string& GetText() const  |  Ruft den Text ab, der im Inhaltsheader enthalten sein soll.
public const std::string& GetFontName() const  |  Ruft den Namen der Schriftart ab, in der der Inhaltsheader angezeigt wird.
public int GetFontSize() const  |  Ruft den Schriftgrad ab, in dem der Inhaltsheader angezeigt wird.
public const std::string& GetFontColor() const  |  Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.
public ContentMarkAlignment GetAlignment() const  |  Ruft die Ausrichtung des Headers ab.
public int GetMargin() const  |  Ruft den Rand des Headers im unteren Bereich ab
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>GetUIElementName-Funktion
Eine API, mit der das Inhaltsheaderelement markiert wird

  
**Gibt**: Der Name, der für das UI-Element verwendet werden soll, der der Inhaltsheader enthält. Wenn der Inhaltsheader entfernt werden muss, wird derselbe Name in [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) zurückgegeben.
  
### <a name="gettext-function"></a>GetText-Funktion
Ruft den Text ab, der im Inhaltsheader enthalten sein soll.

  
**Gibt**: Text des inhaltsheaders.
  
### <a name="getfontname-function"></a>GetFontName-Funktion
Ruft den Namen der Schriftart ab, in der der Inhaltsheader angezeigt wird.

  
**Gibt**: Schriftartname. Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem der Inhaltsheader angezeigt wird.

  
**Gibt**: Der Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>GetFontColor-Funktion
Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.

  
**Gibt**: Schriftfarbe als Zeichenfolge (z. B. #000000 ").
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung des Headers ab.

  
**Gibt**: Der ContentMarkAlignment-Enumerator: LEFT|RIGHT|CENTER. 
  
**Siehe auch**: [ContentMarkAlignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand des Headers im unteren Bereich ab

  
**Gibt**: Die Ränder im unteren Bereich des Dokuments (z. B. 10 mm).
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.