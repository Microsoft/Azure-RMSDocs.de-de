---
title: removewatermarkaction-Klasse
description: 'Dokumentiert die removewatermarkaction:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: eee2617a7f3c1225d789a5d1f6124caa3d3deec0
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567430"
---
# <a name="class-removewatermarkaction"></a>removewatermarkaction-Klasse 
Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<std::string\>& getuielementnames ()  |  Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
public ActionType GetType() const  |  Ruft den Typ der Aktion ab.
  
## <a name="members"></a>Members
  
### <a name="getuielementnames-function"></a>Getuielementnames-Funktion
Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte

  
**Rückgabe**: Eine Liste mit Namen der Benutzeroberflächenelemente.
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der Aktion ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.