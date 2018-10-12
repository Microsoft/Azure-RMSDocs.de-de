---
title: Microsoft Information Protection-Klasse „ClassificationResult“
description: Referenz für die Microsoft Information Protection-Klasse „ClassificationResult“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: ea312330c656b6daefbc1bcba690f53ebfbf419f
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446293"
---
# <a name="class-mipclassificationresult"></a>mip::ClassificationResult-Klasse 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
 public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
 public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
  
## <a name="members"></a>Member
  
### <a name="getid"></a>GetId
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Rückgabe**: ID der Klassifizierungsrichtlinie.
  
### <a name="getcount"></a>GetCount
Ruft die Anzahl der Instanzen ab.

  
**Rückgabe**: Anzahl von Instanzen.
  
### <a name="getconfidencelevel"></a>GetConfidenceLevel
Ruft die Zuverlässigkeit des Ergebnisses ab.