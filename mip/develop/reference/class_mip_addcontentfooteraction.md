---
title: mip::AddContentFooterAction-Klasse
description: 'Dokumentiert die MIP:: addcontentfooteraction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 48b558c423c8cefa37333b1c5133dda31d70433d
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884594"
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
  
## <a name="members"></a>Member
  
### <a name="getuielementname-function"></a>Getuielementname-Funktion
Eine API, mit der das Element des Fußzeileninhalts markiert wird.

  
**Gibt Folgendes zurück**: Der Name, der für das UI-Element verwendet werden soll, das den Content Footer enthält. Wenn der Fußzeileninhalt entfernt werden muss, wird der gleiche Name in [RemoveContentFooterAction](class_mip_removecontentfooteraction.md) zurückgegeben.
  
### <a name="gettext-function"></a>Gettext-Funktion
Ruft den Text ab, der im Fußzeileninhalt enthalten sein soll.

  
**Gibt Folgendes zurück**: Textfootertext.
  
### <a name="getfontname-function"></a>Getfontname-Funktion
Ruft den Namen der Schriftart ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Gibt Folgendes zurück**: Der Schriftart Name. Standardwert ist Calibri, wenn keiner von der Richtlinie festgelegt ist.
  
### <a name="getfontsize-function"></a>GetFontSize-Funktion
Ruft den Schriftgrad ab, in dem der Fußzeileninhalt angezeigt werden soll.

  
**Gibt Folgendes zurück**: Schrift Grad als ganze Zahl.
  
### <a name="getfontcolor-function"></a>Getfontcolor-Funktion
Ruft die Schriftfarbe ab, in der der Fußzeileninhalt angezeigt werden soll.

  
**Gibt Folgendes zurück**: Schriftfarbe als Zeichenfolge (z. b. "#000000").
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung der Fußzeile ab.

  
**Gibt Folgendes zurück**: Der contentmarkalignment-Enumerator: LINKS | RECHTS | TAGESSTÄTTE. 
  
**Siehe auch**: [ContentMarkAlignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand der Fußzeile im unteren Bereich ab

  
**Gibt Folgendes zurück**: Die Ränder vom Ende des Dokuments (z. b. 10 mm).