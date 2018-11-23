---
title: Microsoft Information Protection-Klasse „AddWatermarkAction“
description: Referenz für die Microsoft Information Protection-Klasse „AddWatermarkAction“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: f49bd7aa16ae12aef240d05fff6acf507ddc341d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446089"
---
# <a name="class-mipaddwatermarkaction"></a>mip::AddWatermarkAction-Klasse 
Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetUIElementName()  |  Eine zum Markieren des Wasserzeichenelements genutzte API.
 public WatermarkLayout GetLayout() const  |  Eine zum Abrufen des Wasserzeichenlayouts genutzte API.
 public const std::string& GetText() const  |  Ruft den Text ab, der im Wasserzeichen enthalten sein soll.
 public const std::string& GetFontName() const  |  Ruft den Namen der Schriftart ab, in der das Wasserzeichen angezeigt wird.
 public int GetFontSize() const  |  Ruft den Schriftgrad ab, in dem das Wasserzeichen angezeigt wird.
 public const std::string& GetFontColor() const  |  Ruft die Schriftfarbe ab, in der das Wasserzeichen angezeigt wird.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementname"></a>GetUIElementName
Eine zum Markieren des Wasserzeichenelements genutzte API.

  
**Rückgabe**: Name, der für das UI-Element verwendet werden soll, welches das Wasserzeichen enthält. Der gleiche Name wird in RemoveWatermarkingAction zurückgegeben, falls das Wasserzeichen entfernt werden muss.
  
### <a name="getlayout"></a>GetLayout
Eine zum Abrufen des Wasserzeichenlayouts genutzte API.

  
**Rückgabe**: WatermarkLayout Das Wasserzeichenlayout in der Form einer Enumeration HORIZONTAL|DIAGONAL. ,
  
### <a name="gettext"></a>GetText
Ruft den Text ab, der im Wasserzeichen enthalten sein soll.

  
**Rückgabe**: Text des Inhaltsheaders.
  
### <a name="getfontname"></a>GetFontName
Ruft den Namen der Schriftart ab, in der das Wasserzeichen angezeigt wird.

  
**Rückgabe**: Schriftartname Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize"></a>GetFontSize
Ruft den Schriftgrad ab, in dem das Wasserzeichen angezeigt wird.

  
**Rückgabe**: Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor"></a>GetFontColor
Ruft die Schriftfarbe ab, in der das Wasserzeichen angezeigt wird.

  
**Rückgabe**: Schriftfarbe als Zeichenfolge (z.B. „#000000“).
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.