---
title: Microsoft Information Protection-Klasse „ProtectByTemplateAction“
description: Referenz für die Microsoft Information Protection-Klasse „ProtectByTemplateAction“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: cb5f42b25e6f499bc09f3f460ec4a253627b45a5
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445460"
---
# <a name="class-mipprotectbytemplateaction"></a>mip::ProtectByTemplateAction-Klasse 
Eine Aktionsklasse, die angibt, dass dem Dokument Schutz nach Vorlage hinzugefügt wird.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetTemplateId() const  |  Ruft die Schutzvorlagen-ID ab, die mit der Aktion verknüpft ist.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="gettemplateid"></a>GetTemplateId
Ruft die Schutzvorlagen-ID ab, die mit der Aktion verknüpft ist.

  
**Rückgabe**: Die Schutzvorlagen-ID.
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.