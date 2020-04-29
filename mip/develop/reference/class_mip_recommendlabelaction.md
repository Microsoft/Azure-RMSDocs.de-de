---
title: Class RecommendLabelAction
description: 'Dokumentiert die recommendlabelaction:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 3990d6de9d78002d9c240e621f96351cd337aabb
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81764541"
---
# <a name="class-recommendlabelaction"></a>Class RecommendLabelAction 
Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: shared_ptr\<-Bezeichnung\>& GetLabel () Konstanten  |  Holen Sie sich die vorgeschlagene Bezeichnung.
Public Konstanten Std:: Vector\<Std:: String\>& getclassificationids () Konstanten  |  Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Holen Sie sich die vorgeschlagene Bezeichnung.

  
**Gibt Folgendes zurück**: die Bezeichnung.
  
### <a name="getclassificationids-function"></a>Getclassificationids-Funktion
Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector<Std:: String>& eine Liste der Klassifizierungs-IDs, die dazu geführt haben, dass diese Bezeichnung angezeigt wird.