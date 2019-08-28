---
title: mip::AddWatermarkAction-Klasse
description: 'Dokumentiert die MIP:: addwatermarkaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 2b6a50385e5d891b8893949a8761e7f38f591f17
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056335"
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
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>Getuielementname-Funktion
Eine zum Markieren des Wasserzeichenelements genutzte API.

  
**Gibt Folgendes zurück**: Der Name, der für das UI-Element verwendet werden soll, das das Wasserzeichen enthält. Der gleiche Name wird in RemoveWatermarkingAction zurückgegeben, falls das Wasserzeichen entfernt werden muss.
  
### <a name="getlayout-function"></a>GetLayout-Funktion
Eine zum Abrufen des Wasserzeichenlayouts genutzte API.

  
**Gibt Folgendes zurück**: WatermarkLayout Das Wasserzeichenlayout in der Form einer Enumeration HORIZONTAL|DIAGONAL. ,
  
### <a name="gettext-function"></a>Gettext-Funktion
Ruft den Text ab, der im Wasserzeichen enthalten sein soll.

  
**Gibt Folgendes zurück**: Text Header Text.
  
### <a name="getfontname-function"></a>Getfontname-Funktion
Ruft den Namen der Schriftart ab, in der das Wasserzeichen angezeigt wird.

  
**Gibt Folgendes zurück**: Der Schriftart Name. Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem das Wasserzeichen angezeigt wird.

  
**Gibt Folgendes zurück**: Schrift Grad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>Getfontcolor-Funktion
Ruft die Schriftfarbe ab, in der das Wasserzeichen angezeigt wird.

  
**Gibt Folgendes zurück**: Schriftfarbe als Zeichenfolge (z. b. "#000000").