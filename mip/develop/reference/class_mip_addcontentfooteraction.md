---
title: Microsoft Information Protection-Klasse „AddContentFooterAction“
description: Referenz für die Microsoft Information Protection-Klasse „AddContentFooterAction“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 73f641d965c3cf0236919557128af2ed07705672
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445834"
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
  
### <a name="getuielementname"></a>GetUIElementName
Eine API, mit der das Element des Fußzeileninhalts markiert wird.

  
**Rückgabe**: Name, der für das UI-Element verwendet werden sollte, das den Fußzeileninhalt enthält. Wenn der Fußzeileninhalt entfernt werden muss, wird der gleiche Name in [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) zurückgegeben.
  
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.

  
**Rückgabe**: Inhalt des Fußzeilentexts.
  
### <a name="getfontname"></a>GetFontName
Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Rückgabe**: Schriftartname Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.

  
**Rückgabe**: Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Rückgabe**: Schriftfarbe als Zeichenfolge (z.B. „#000000“).
  
### <a name="getalignment"></a>GetAlignment
Ruft die Ausrichtung der Fußzeile ab.

  
**Rückgabe**: Der ContentMarkAlignment-Enumerator: LEFT|RIGHT|CENTER. 
  
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
  
### <a name="getmargin"></a>GetMargin
Ruft den Rand der Fußzeile im unteren Bereich ab

  
**Rückgabe**: Die Ränder im unteren Bereich des Dokuments (z.B. 10 mm).
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.