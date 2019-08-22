---
title: mip::ApplyLabelAction-Klasse
description: 'Dokumentiert die MIP:: applylabelaction-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 7d2067ad030e909d53602fcdb3eefa9b88af56bf
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69884525"
---
# <a name="class-mipapplylabelaction"></a>mip::ApplyLabelAction-Klasse 
Aktionen zum Anwenden von Bezeichnungen veranlassen, dass die aufrufende Anwendung eine bestimmte Bezeichnung anwendet.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: shared_ptr\<-Bezeichnung\>& GetLabel () Konstanten  |  Holen Sie sich die erforderliche Bezeichnung.
Public Konstanten Std:: Vector\<Std:: String\>& getclassificationids () Konstanten  |  Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.
  
## <a name="members"></a>Member
  
### <a name="getlabel-function"></a>GetLabel-Funktion
Holen Sie sich die erforderliche Bezeichnung.

  
**Gibt Folgendes zurück**: Die Bezeichnung.
  
### <a name="getclassificationids-function"></a>Getclassificationids-Funktion
Die Klassifizierungs-IDs, die abgeglichen wurden, werden angezeigt, und diese Bezeichnung wird angezeigt.

  
**Gibt Folgendes zurück**: Konstante Std:: Vector < Std:: String > & eine Liste der Klassifizierungs-IDs, die dazu geführt haben, dass diese Bezeichnung angezeigt wird.