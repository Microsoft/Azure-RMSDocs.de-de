---
title: mip::RemoveContentFooterAction-Klasse
description: 'Beschreibt die Klasse:: removecontentfooteraction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 14afd4688c13f419ab3019e9c268ba7d355121c8
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60184313"
---
# <a name="class-mipremovecontentfooteraction"></a>mip::RemoveContentFooterAction-Klasse 
Eine Aktionsklasse, die angibt, dass der Fußzeileninhalt aus dem Dokument entfernt wird.
  
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