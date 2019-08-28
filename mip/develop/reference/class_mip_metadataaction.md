---
title: mip::MetadataAction-Klasse
description: 'Dokumentiert die MIP:: metadataaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 9175fc9278f012b3f3247cab6a09650c55713ac3
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70055913"
---
# <a name="class-mipmetadataaction"></a>mip::MetadataAction-Klasse 
Eine [Aktion](class_mip_action.md), die Metadateninformationen zum Inhalt hinzufügt
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<Std:: String\>& GetMetadataToRemove () Konstanten  |  Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.
Public Konstanten Std::\<Vector Std::p Air\<Std:: String, Std:: String\>\>& GetMetadataToAdd () Konstanten  |  Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.
  
## <a name="members"></a>Member
  
### <a name="getmetadatatoremove-function"></a>GetMetadataToRemove-Funktion
Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.

  
**Gibt Folgendes zurück**: Ein Vektor von Zeichen folgen, die entfernt werden sollen. Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="getmetadatatoadd-function"></a>GetMetadataToAdd-Funktion
Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector < Std::p Air < Std:: String, Std:: String > > & das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.