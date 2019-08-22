---
title: mip::RecommendLabelAction-Klasse
description: 'Dokumentiert die MIP:: recommendlabelaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: dd3d2d0ecf7b549105e1a6373a998e77d4e77de8
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69883215"
---
# <a name="class-miprecommendlabelaction"></a>mip::RecommendLabelAction-Klasse 
Durch Aktionen zum Empfehlen einer Bezeichnung erhalten Benutzer einen Vorschlag für eine Bezeichnung. Die Unterdrückung dieses Aufrufs, nachdem ein Benutzer die empfohlene Bezeichnung ignoriert hat, sollte durch die unterstützten Aktionen im Ausführungsstatus erfolgen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: shared_ptr\<-Bezeichnung\>& GetLabel () Konstanten  |  Holen Sie sich die vorgeschlagene Bezeichnung.
Public Konstanten Std:: Vector\<Std:: String\>& getclassificationids () Konstanten  |  Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Holen Sie sich die vorgeschlagene Bezeichnung.

  
**Gibt Folgendes zurück**: Die Bezeichnung.
  
### <a name="getclassificationids-function"></a>Getclassificationids-Funktion
Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector < Std:: String > & eine Liste der Klassifizierungs-IDs, die dazu geführt haben, dass diese Bezeichnung angezeigt wird.