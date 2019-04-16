---
title: mip::MetadataAction-Klasse
description: 'Beschreibt die Klasse:: metadataaction-Klasse von der Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 677de5965c0fe506af3731c2b54b4faaab225471
ms.sourcegitcommit: ea76aade54134afaf5023145fcb755e40c7b84b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/15/2019
ms.locfileid: "59573376"
---
# <a name="class-mipmetadataaction"></a>mip::MetadataAction-Klasse 
Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::vector\<std::string\>& GetMetadataToRemove() const  |  Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.
public const std::vector\<std::pair\<std::string, std::string\>\>& GetMetadataToAdd() const  |  Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.

## <a name="members"></a>Member
  
### <a name="getmetadatatoremove-function"></a>GetMetadataToRemove-Funktion
Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.

  
**Gibt**: Ein Vektor von Zeichenfolgen, die entfernt werden soll. Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="getmetadatatoadd-function"></a>GetMetadataToAdd-Funktion
Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.

  
**Gibt**: Const Std:: Vector < Std:: Pair < Std:: String, Std:: String >> & entfernt Metadaten sollte vor dem Hinzufügen der Metadaten durchgeführt werden.


### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.