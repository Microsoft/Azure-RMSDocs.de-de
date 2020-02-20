---
title: 'MIP:: nopermissionserror-Klasse'
description: 'Dokumentiert die MIP:: nopermissionserror-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: d5067dfcac8ad66464df061d6d043ae343d967cf
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77487649"
---
# <a name="class-mipnopermissionserror"></a>MIP:: nopermissionserror-Klasse 
Der Benutzer konnte nicht auf den Inhalt zugreifen. Das ist ggf. darauf zurückzuführen, dass ihm Berechtigungen fehlen oder Inhalte widerrufen wurden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetReferrer() const  |  Ruft den Kontakt im Falle fehlender Rechte für das Dokument ab.
public std::string GetOwner() const  |  Ruft den Besitzer des Dokuments ab.
  
## <a name="members"></a>Member
  
### <a name="getreferrer-function"></a>Getreferrer-Funktion
Ruft den Kontakt im Falle fehlender Rechte für das Dokument ab.

  
**Gibt Folgendes zurück**: der Kontakt im Fall fehlender Rechte für das Dokument.
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft den Besitzer des Dokuments ab.

  
**Gibt Folgendes zurück**: Dokument Besitzer