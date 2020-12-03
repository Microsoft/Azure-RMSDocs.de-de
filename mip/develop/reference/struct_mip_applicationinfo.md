---
title: ApplicationInfo-Struktur
description: Dokumentiert die ApplicationInfo-Struktur.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: d56fdcaccf67f46b2d6632ec6586e2b140717696
ms.sourcegitcommit: 6322f840388067edbe3642661e313ff225be5563
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535585"
---
# <a name="struct-applicationinfo"></a>ApplicationInfo-Struktur 
Eine Struktur, die anwendungsspezifische Informationen umfasst
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string applicationId  |  Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
public std::string applicationName  |  Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
public std::string applicationVersion  |  Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
  
## <a name="members"></a>Members
  
### <a name="applicationid-struct-member"></a>ApplicationId-Strukturmember
Im Aad-Portal fest gelegender Anwendungs Bezeichner (sollte eine GUID ohne eckige Klammern sein).
  
### <a name="applicationname-struct-member"></a>ApplicationName-Strukturmember
Anwendungsname (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)
  
### <a name="applicationversion-struct-member"></a>applicationVersion-Strukturmember
Die Version der verwendeten Anwendung (sollte nur gültiges ASCII-Zeichen mit Ausnahme von '; ' enthalten)