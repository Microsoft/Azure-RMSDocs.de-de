---
title: mip::MetadataAction-Klasse
description: 'Dokumentiert die MIP:: metadataaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 405bb153527cb3fde346203d3b11c09c97110f12
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73558680"
---
# <a name="class-mipmetadataaction"></a>mip::MetadataAction-Klasse 
Eine Aktion, mit der dem Inhalt Metadateninformationen hinzugefügt werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<Std:: String\>& GetMetadataToRemove () Konstanten  |  Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.
Public Konstanten Std:: Vector\<Std::p Air\<Std:: String, Std:: String\>\>& GetMetadataToAdd () Konstanten  |  Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.
  
## <a name="members"></a>Member
  
### <a name="getmetadatatoremove-function"></a>GetMetadataToRemove-Funktion
Ruft die Liste von Namen der Metadaten ab, die aus dem Inhalt entfernt werden sollen.

  
**Rückgabe**: ein Vektor von Zeichenfolgen, die entfernt werden sollen. Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.
  
### <a name="getmetadatatoadd-function"></a>GetMetadataToAdd-Funktion
Ruft die Metadaten-Name-Wert-Paare ab, die dem Inhalt hinzugefügt werden sollen.

  
**Rückgabe**: Const std::vector<std::pair<std::string, std::string>>& (Das Entfernen von Metadaten sollte vor dem Hinzufügen von Metadaten erfolgen.)