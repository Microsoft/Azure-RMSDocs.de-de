---
title: mip::ClassificationResult-Klasse
description: 'Dokumentiert die MIP:: classificationresult-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 2744e2d5fe188667ff7c1c93a7f98719f200aecd
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056230"
---
# <a name="class-mipclassificationresult"></a>mip::ClassificationResult-Klasse 
Klasse, die das Ergebnis eines Klassifizierungsaufrufs im Ausführungsstatus enthält
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::string GetId() const  |  Ruft die ID der Klassifizierungsrichtlinie ab.
public int GetCount() const  |  Ruft die Anzahl der Instanzen ab.
public int GetConfidenceLevel() const  |  Ruft die Zuverlässigkeit des Ergebnisses ab.
Public Std:: String getsensitiveinformationerkenctions () Konstanten  |  Die Erkennungen für sensible Informationen erhalten.
  
## <a name="members"></a>Member
  
### <a name="getid-function"></a>GetId-Funktion
Ruft die ID der Klassifizierungsrichtlinie ab.

  
**Gibt Folgendes zurück**: ID der Klassifizierungs Richtlinie.
  
### <a name="getcount-function"></a>GetCount-Funktion
Ruft die Anzahl der Instanzen ab.

  
**Gibt Folgendes zurück**: Die Anzahl der Instanzen.
  
### <a name="getconfidencelevel-function"></a>Getconficelevel-Funktion
Ruft die Zuverlässigkeit des Ergebnisses ab.
  
### <a name="getsensitiveinformationdetections-function"></a>Getsensitiveingeformationdetections-Funktion
Die Erkennungen für sensible Informationen erhalten.

  
**Gibt Folgendes zurück**: JSON-Zeichenfolge aller Erkennungen sensibler Informationen.