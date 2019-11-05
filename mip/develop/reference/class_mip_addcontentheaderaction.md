---
title: mip::AddContentHeaderAction-Klasse
description: 'Dokumentiert die MIP:: addcontenderaderaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 40e9b648799008bcc75b48ae9379f7a3010bd7bd
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73559049"
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

  
**Rückgabe**: Name, der für das UI-Element verwendet werden sollte, das den Kopfzeileninhalt enthält. Der gleiche Name wird in removecontenderaderaction zurückgegeben, falls der Inhalts Header entfernt werden muss.
  
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

  
**Rückgabe**: Schriftfarbe als Zeichenfolge (z.B. „#000000“).
  
### <a name="getalignment-function"></a>GetAlignment-Funktion
Ruft die Ausrichtung des Headers ab.

  
**Rückgabe**: Der ContentMarkAlignment-Enumerator: LEFT|RIGHT|CENTER. 
  
**Siehe auch**: [contentmarkalignment](mip-enums-and-structs.md#contentmarkalignment-enum)
  
### <a name="getmargin-function"></a>GetMargin-Funktion
Ruft den Rand des Headers im unteren Bereich ab

  
**Rückgabe**: Die Ränder im unteren Bereich des Dokuments (z.B. 10 mm).