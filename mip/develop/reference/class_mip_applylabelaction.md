---
title: Microsoft Information Protection-Klasse „ApplyLabelAction“
description: Referenz für die Microsoft Information Protection-Klasse „ApplyLabelAction“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 06a17ef1e60503cfb7d690bea9bb72316544f16d
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445766"
---
# <a name="class-mipapplylabelaction"></a>mip::ApplyLabelAction-Klasse 
Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public const std::string& GetLabelId() const  |  Ruft die erforderliche Bezeichnungs-ID ab.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getlabelid"></a>GetLabelId
Ruft die erforderliche Bezeichnungs-ID ab.

  
**Rückgabe**: Bezeichnungs-ID.
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.