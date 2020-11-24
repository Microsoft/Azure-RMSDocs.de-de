---
title: Class MetadataAction
description: 'Dokumentiert die metadataaction:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 082a4332482bce35a436b70d4fa86ee7320d6f52
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566779"
---
# <a name="class-metadataaction"></a>Class MetadataAction 
Eine Aktion, die Metadateninformationen zum Inhalt hinzufügt
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<std::string\>& GetMetadataToRemove () Konstanten  |  Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.
Public Konstanten Std:: Vector \<MetadataEntry\>& GetMetadataToAdd () Konstanten  |  Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.
  
## <a name="members"></a>Members
  
### <a name="getmetadatatoremove-function"></a>GetMetadataToRemove-Funktion
Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.

  
**Rückgabe**: ein Vektor von Zeichenfolgen, die entfernt werden sollen. Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="getmetadatatoadd-function"></a>GetMetadataToAdd-Funktion
Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector <MetadataEntry>& das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.