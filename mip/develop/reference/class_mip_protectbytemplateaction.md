---
title: mip::ProtectByTemplateAction-Klasse
description: 'Beschreibt die Klasse:: protectbytemplateaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 1c05a04df39e6454eb934b5db48e96339afdac0c
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55650815"
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