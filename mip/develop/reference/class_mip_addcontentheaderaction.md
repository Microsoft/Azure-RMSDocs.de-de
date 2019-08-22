---
title: mip::AddContentHeaderAction-Klasse
description: 'Dokumentiert die MIP:: addcontenderaderaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: e9de81595ead9a629c3266962a08f1b13fdb9675
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885939"
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
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>Getuielementname-Funktion
Eine API, mit der das Inhaltsheaderelement markiert wird

  
**Gibt Folgendes zurück**: Der Name, der für das UI-Element verwendet werden soll, das den Content-Header enthält. Wenn der Inhaltsheader entfernt werden muss, wird derselbe Name in [RemoveContentHeaderAction](class_mip_removecontentheaderaction.md) zurückgegeben.
  
### <a name="gettext-function"></a>Gettext-Funktion
Ruft den Text ab, der im Inhaltsheader enthalten sein soll.

  
**Gibt Folgendes zurück**: Text Header Text.
  
### <a name="getfontname-function"></a>Getfontname-Funktion
Ruft den Namen der Schriftart ab, in der der Inhaltsheader angezeigt wird.

  
**Gibt Folgendes zurück**: Der Schriftart Name. Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem der Inhaltsheader angezeigt wird.

  
**Gibt Folgendes zurück**: Schrift Grad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>Getfontcolor-Funktion
Ruft die Schriftfarbe ab, in der der Inhaltsheader angezeigt wird.

  
**Gibt Folgendes zurück**: Schriftfarbe als Zeichenfolge (z. b. #000000 ").
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung des Headers ab.

  
**Gibt Folgendes zurück**: Der contentmarkalignment-Enumerator: LINKS | RECHTS | TAGESSTÄTTE. 
  
**Siehe auch**: [ContentMarkAlignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand des Headers im unteren Bereich ab

  
**Gibt Folgendes zurück**: Die Ränder vom Ende des Dokuments (z. b. 10 mm).