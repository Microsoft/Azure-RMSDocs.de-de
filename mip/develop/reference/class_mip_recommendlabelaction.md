---
title: Microsoft Information Protection-Klasse „RecommendLabelAction“
description: Referenz für die Microsoft Information Protection-Klasse „RecommendLabelAction“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: b8e56daed967523b7580087d7bb934c1b2164320
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446004"
---
# <a name="class-miprecommendlabelaction"></a>mip::RecommendLabelAction-Klasse 
Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetLabelId() const  |  Ruft die vorgeschlagene Bezeichnungs-ID ab.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getlabelid"></a>GetLabelId
Ruft die vorgeschlagene Bezeichnungs-ID ab.

  
**Rückgabe**: Bezeichnungs-ID.
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.