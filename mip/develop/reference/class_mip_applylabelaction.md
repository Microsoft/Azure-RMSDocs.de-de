---
title: mip::ApplyLabelAction-Klasse
description: Dokumentiert die mip::applylabelaction-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 70f226cc112062582b5441f6c3ae7fc3dc7de118
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60173319"
---
# <a name="class-mipapplylabelaction"></a>mip::ApplyLabelAction-Klasse 
Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public const std::string& GetLabelId() const  |  Ruft die erforderliche Bezeichnungs-ID ab.
public const std::vector\<std::string\>& GetClassificationIds() const  |  Erhalten Sie die Klassifizierung-IDs, die abgeglichen und verursacht diese Bezeichnung angezeigt werden.
public ActionType GetType() const  |  Ruft den Typ der [Aktion](class_mip_action.md) ab.

## <a name="members"></a>Member
  
### <a name="getlabelid-function"></a>GetLabelId-Funktion
Ruft die erforderliche Bezeichnungs-ID ab.

  
**Gibt**: Die bezeichnungs-ID
  
### <a name="getclassificationids-function"></a>GetClassificationIds-Funktion
Erhalten Sie die Klassifizierung-IDs, die abgeglichen und verursacht diese Bezeichnung angezeigt werden.

  
**Gibt**: Const Std:: Vector < Std:: String > und eine Liste der Klassifizierung-IDs, die Ursache dieser Bezeichnung, die angezeigt werden.

### <a name="gettype-function"></a>GetType-Funktion
Ruft den Typ der [Aktion](class_mip_action.md) ab.

  
**Gibt**: ActionType Der Typ der abgeleiteten Aktion, in den diese Basisklasse umgewandelt werden kann.