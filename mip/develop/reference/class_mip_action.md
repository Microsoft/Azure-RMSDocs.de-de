---
title: mip::Action-Klasse
description: 'Dokumentiert die MIP:: Action-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: d3cc1aecfb5ca8bf2d78dd9d6c8c280b5541389d
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560417"
---
# <a name="class-mipaction"></a>mip::Action-Klasse 
Schnittstelle für eine Aktion. Jede Aktion bedeutet einen Schritt, der von der Anwendung ausgeführt werden muss, um die Bezeichnung (wie in der Richtlinie definiert) anzuwenden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public ActionType GetType() const  |  Gibt den Typ der Aktion an.
  
## <a name="members"></a>Member
  
### <a name="gettype-function"></a>GetType-Funktion
Gibt den Typ der Aktion an.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.