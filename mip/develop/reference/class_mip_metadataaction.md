---
title: Microsoft Information Protection-Klasse „MetadataAction“
description: Referenz für die Microsoft Information Protection-Klasse „MetadataAction“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 8f7480775a0226c7161c9ad770184e54427a5084
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47444618"
---
# <a name="class-mipmetadataaction"></a>mip::MetadataAction-Klasse 
Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector<std::string>& GetMetadataToRemove() const  |  Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.
public const std::vector<std::pair<std::string, std::string>>& GetMetadataToAdd() const  |  Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.
 public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getmetadatatoremove"></a>GetMetadataToRemove
Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.

  
**Rückgabe**: ein Vektor von Zeichenfolgen, die entfernt werden sollen. Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="getmetadatatoadd"></a>GetMetadataToAdd
Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.

  
**Rückgabe**: Const std::vector<std::pair<std::string, std::string>>& (Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.)
  
### <a name="actiontype"></a>ActionType
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Rückgabe**: ActionType, der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.