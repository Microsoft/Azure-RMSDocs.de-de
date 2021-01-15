---
title: addcontenderaderaction-Klasse
description: 'Dokumentiert die addcontenderaderaction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: e5a2993af705855dde94f5be37e22f1e9ab87c99
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98212450"
---
# <a name="class-addcontentheaderaction"></a>addcontenderaderaction-Klasse 
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
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>Getuielementname-Funktion
Eine API, mit der das Inhaltsheaderelement markiert wird

  
**Rückgabe**: Name, der für das UI-Element verwendet werden sollte, das den Kopfzeileninhalt enthält. Wenn der Inhaltsheader entfernt werden muss, wird derselbe Name in RemoveContentHeaderAction zurückgegeben.
  
### <a name="gettext-function"></a>Gettext-Funktion
Ruft den Text ab, der im Inhaltsheader enthalten sein soll.

  
**Rückgabe**: Text des Inhaltsheaders.
  
### <a name="getfontname-function"></a>Getfontname-Funktion
Ruft den Namen der Schriftart ab, in der der Inhaltsheader angezeigt wird.

  
**Rückgabe**: Schriftartname Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem der Inhaltsheader angezeigt wird.

  
**Rückgabe**: Schriftgrad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>Getfontcolor-Funktion
Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.

  
**Gibt Folgendes zurück**: Schriftart Farbe als Zeichenfolge (z. b. #000000 ").
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung des Headers ab.

  
**Rückgabe**: Der ContentMarkAlignment-Enumerator: LEFT|RIGHT|CENTER. 
  
**Weitere Informationen finden Sie unter:** ContentMarkAlignment
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand des Headers im unteren Bereich ab

  
**Rückgabe**: Die Ränder im unteren Bereich des Dokuments (z.B. 10 mm).