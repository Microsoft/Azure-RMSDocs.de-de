---
title: mip::RemoveContentHeaderAction-Klasse
description: 'Beschreibt die Klasse:: removecontentheaderaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 3cc2fbdcfeae4e168e342a3c7af0edc971039db4
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59574311"
---
# <a name="class-mipremovecontentheaderaction"></a>mip::RemoveContentHeaderAction-Klasse 
Eine Aktionsklasse, die angibt, dass der Inhaltsheader aus dem Dokument entfernt wird.
  
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