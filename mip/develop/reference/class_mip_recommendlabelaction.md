---
title: Class RecommendLabelAction
description: 'Dokumentiert die recommendlabelaction:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 2a0318c0da7bfc3a2be72c1139754da1f7142d71
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566569"
---
# <a name="class-recommendlabelaction"></a>Class RecommendLabelAction 
Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: shared_ptr \<Label\>& GetLabel ()-Konstanten  |  Holen Sie sich die vorgeschlagene Bezeichnung.
Public Konstanten Std:: Vector \<std::string\>& getclassificationids () Konstanten  |  Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.
  
## <a name="members"></a>Members
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Holen Sie sich die vorgeschlagene Bezeichnung.

  
**Gibt Folgendes zurück**: die Bezeichnung.
  
### <a name="getclassificationids-function"></a>Getclassificationids-Funktion
Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector<Std:: String>& eine Liste der Klassifizierungs-IDs, die dazu geführt haben, dass diese Bezeichnung angezeigt wird.