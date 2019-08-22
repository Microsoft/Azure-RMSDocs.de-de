---
title: mip::MetadataAction-Klasse
description: 'Dokumentiert die MIP:: metadataaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 26a189d714001f4145ce328c163a052313923136
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885417"
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