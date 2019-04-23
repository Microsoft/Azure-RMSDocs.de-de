---
title: mip::RemoveWatermarkAction-Klasse
description: 'Beschreibt die Klasse:: removewatermarkaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 7b6ef32e69fefad0371f75ea22b99f4181732e90
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60174169"
---
# <a name="class-mipremovewatermarkaction"></a>mip::RemoveWatermarkAction-Klasse 
Eine Aktionsklasse, die angibt, dass das Wasserzeichen aus dem Dokument entfernt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector\<std::string\>& GetUIElementNames()  |  Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getuielementnames-function"></a>GetUIElementNames-Funktion
Ruft eine Liste mit Namen ab, die zur Suche nach zu entfernenden Benutzeroberflächenelementen verwendet werden sollte

  
**Gibt**: Eine Liste der Namen der Ui-Elemente.
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.