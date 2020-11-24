---
title: addwatermarkaction-Klasse
description: 'Dokumentiert die addwatermarkaction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 60120fbfb9d35cdb92c312af62bddf456dc88cfd
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567316"
---
# <a name="class-addwatermarkaction"></a>addwatermarkaction-Klasse 
Eine Aktionsklasse, die angibt, dass ein Wasserzeichen hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetUIElementName()  |  Eine zum Markieren des Wasserzeichenelements genutzte API.
public WatermarkLayout GetLayout() const  |  Eine zum Abrufen des Wasserzeichenlayouts genutzte API.
public const std::string& GetText() const  |  Ruft den Text ab, der im Wasserzeichen enthalten sein soll.
public const std::string& GetFontName() const  |  Ruft den Namen der Schriftart ab, in der das Wasserzeichen angezeigt wird.
public int GetFontSize() const  |  Ruft den Schriftgrad ab, in dem das Wasserzeichen angezeigt wird.
public const std::string& GetFontColor() const  |  Ruft die Schriftfarbe ab, in der das Wasserzeichen angezeigt wird.
  
## <a name="members"></a>Members
  
### <a name="getuielementname-function"></a>Getuielementname-Funktion
Eine zum Markieren des Wasserzeichenelements genutzte API.

  
**Rückgabe**: Name, der für das UI-Element verwendet werden soll, welches das Wasserzeichen enthält. Der gleiche Name wird in RemoveWatermarkingAction zurückgegeben, falls das Wasserzeichen entfernt werden muss.
  
### <a name="getlayout-function"></a>GetLayout-Funktion
Eine zum Abrufen des Wasserzeichenlayouts genutzte API.

  
**Rückgabe**: WatermarkLayout Das Wasserzeichenlayout in der Form einer Enumeration HORIZONTAL|DIAGONAL. ,
  
### <a name="gettext-function"></a>Gettext-Funktion
Ruft den Text ab, der im Wasserzeichen enthalten sein soll.

  
**Rückgabe**: Text des Inhaltsheaders.
  
### <a name="getfontname-function"></a>Getfontname-Funktion
Ruft den Namen der Schriftart ab, in der das Wasserzeichen angezeigt wird.

  
**Rückgabe**: Schriftartname Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem das Wasserzeichen angezeigt wird.

  
**Rückgabe**: Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>Getfontcolor-Funktion
Ruft die Schriftfarbe ab, in der das Wasserzeichen angezeigt wird.

  
**Rückgabe**: Schriftfarbe als Zeichenfolge (z.B. „#000000“).