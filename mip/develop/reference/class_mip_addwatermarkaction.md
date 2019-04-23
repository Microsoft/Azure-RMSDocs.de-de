---
title: mip::AddWatermarkAction-Klasse
description: 'Beschreibt die Klasse:: addwatermarkaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: f3a8d50d55dc615a7aa81e8686b356bfc2d41654
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60173522"
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
  
### <a name="getuielementname-function"></a>GetUIElementName-Funktion
Eine zum Markieren des Wasserzeichenelements genutzte API.

  
**Gibt**: Der Name, der für das UI-Element verwendet werden soll, die das Wasserzeichen enthält. Der gleiche Name wird in RemoveWatermarkingAction zurückgegeben, falls das Wasserzeichen entfernt werden muss.
  
### <a name="getlayout-function"></a>GetLayout-Funktion
Eine zum Abrufen des Wasserzeichenlayouts genutzte API.

  
**Gibt**: WatermarkLayout Das Wasserzeichenlayout in der Form einer Enumeration HORIZONTAL|DIAGONAL. ,
  
### <a name="gettext-function"></a>GetText-Funktion
Ruft den Text ab, der im Wasserzeichen enthalten sein soll.

  
**Gibt**: Text des inhaltsheaders.
  
### <a name="getfontname-function"></a>GetFontName-Funktion
Ruft den Namen der Schriftart ab, in der das Wasserzeichen angezeigt wird.

  
**Gibt**: Schriftartname. Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem das Wasserzeichen angezeigt wird.

  
**Gibt**: Der Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>GetFontColor-Funktion
Ruft die Schriftfarbe ab, in der das Wasserzeichen angezeigt wird.

  
**Gibt**: Schriftfarbe als Zeichenfolge (z. B. "#000000").

### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.