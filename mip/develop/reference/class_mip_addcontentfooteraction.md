---
title: addcontentfooteraction-Klasse
description: 'Dokumentiert die addcontentfooteraction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 58c0767f2c880a52ef4a831e5d57670820187fc7
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763769"
---
# <a name="class-addcontentfooteraction"></a>addcontentfooteraction-Klasse 
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
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>Getuielementname-Funktion
Eine API, mit der das Element des Fußzeileninhalts markiert wird.

  
**Rückgabe**: Name, der für das UI-Element verwendet werden sollte, das den Fußzeileninhalt enthält. Wenn der Fußzeileninhalt entfernt werden muss, wird der gleiche Name in [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) zurückgegeben.
  
### <a name="gettext-function"></a>Gettext-Funktion
Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.

  
**Rückgabe**: Inhalt des Fußzeilentexts.
  
### <a name="getfontname-function"></a>Getfontname-Funktion
Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Rückgabe**: Schriftartname Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.

  
**Rückgabe**: Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>Getfontcolor-Funktion
Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Rückgabe**: Schriftfarbe als Zeichenfolge (z.B. „#000000“).
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung der Fußzeile ab.

  
**Rückgabe**: Der ContentMarkAlignment-Enumerator: LEFT|RIGHT|CENTER. 
  
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand der Fußzeile im unteren Bereich ab

  
**Rückgabe**: Die Ränder im unteren Bereich des Dokuments (z.B. 10 mm).