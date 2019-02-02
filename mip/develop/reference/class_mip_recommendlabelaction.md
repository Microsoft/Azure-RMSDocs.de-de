---
title: mip::RecommendLabelAction-Klasse
description: Dokumentiert die mip::recommendlabelaction-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: ec1f82ab5951a5b7813fff2ebd5be6650a80203b
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651342"
---
# <a name="class-miprecommendlabelaction"></a>mip::RecommendLabelAction-Klasse 
Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetLabelId() const  |  Ruft die vorgeschlagene Bezeichnungs-ID ab.
public const std::vector\<std::string\>& GetClassificationIds() const  |  Erhalten Sie die Klassifizierung-IDs, die abgeglichen und verursacht diese Bezeichnung angezeigt werden.
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.
  
## <a name="members"></a>Member
  
### <a name="getlabelid-function"></a>GetLabelId-Funktion
Ruft die vorgeschlagene Bezeichnungs-ID ab.

  
**Gibt**: Die bezeichnungs-ID
  
### <a name="getclassificationids-function"></a>GetClassificationIds-Funktion
Erhalten Sie die Klassifizierung-IDs, die abgeglichen und verursacht diese Bezeichnung angezeigt werden.

  
**Gibt**: Const Std:: Vector < Std:: String > und eine Liste der Klassifizierung-IDs, die Ursache dieser Bezeichnung, die angezeigt werden.
  
### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.