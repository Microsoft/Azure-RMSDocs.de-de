---
title: ApplicationInfo-Struktur
description: Dokumentiert Strukturen, die mit dem Microsoft Information Protection (MIP) SDK verknüpft sind.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 4971d7cf0891308733dafd0dc64d58c02343f1e4
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566551"
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