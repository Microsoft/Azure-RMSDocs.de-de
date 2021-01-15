---
title: Class RecommendLabelAction
description: 'Dokumentiert die recommendlabelaction:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: d86f9a77a7e198ed47b633bd74da49db41edda15
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98213265"
---
# <a name="class-recommendlabelaction"></a>Class RecommendLabelAction 
Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: shared_ptr \<Label\>& GetLabel ()-Konstanten  |  Holen Sie sich die vorgeschlagene Bezeichnung.
Public Konstanten Std:: Vector \<std::string\>& getclassificationids () Konstanten  |  Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Holen Sie sich die vorgeschlagene Bezeichnung.

  
**Gibt Folgendes zurück**: die Bezeichnung.
  
### <a name="getclassificationids-function"></a>Getclassificationids-Funktion
Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector<Std:: String>& eine Liste der Klassifizierungs-IDs, die dazu geführt haben, dass diese Bezeichnung angezeigt wird.