---
title: mip::ProtectByTemplateAction-Klasse
description: 'Beschreibt die Klasse:: protectbytemplateaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 18bdf3caa5eba2f335376d81f525fe93da4d0352
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60173247"
---
# <a name="class-mipprotectbytemplateaction"></a>mip::ProtectByTemplateAction-Klasse 
Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetTemplateId() const  |  Ruft die Schutzvorlagen-ID ab, die mit der Aktion verknüpft ist.
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.

## <a name="members"></a>Member
  
### <a name="gettemplateid-function"></a>GetTemplateId-Funktion
Ruft die Schutzvorlagen-ID ab, die mit der Aktion verknüpft ist.

  
**Gibt**: Die Schutz-Vorlagen-ID.


### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.