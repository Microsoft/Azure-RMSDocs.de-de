---
title: 'MIP:: computeengine-Klasse'
description: 'Dokumentiert die MIP:: computeengine-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: 1faae8e64bbc2e2f2de54f8152b1227148c7d3de
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77490386"
---
# <a name="class-mipcomputeengine"></a>MIP:: computeengine-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<Std:: shared_ptr\<Bezeichnung\>\>& listsensitivitylabels ()  | _Noch nicht dokumentiert._
Public Std:: shared_ptr\<contentlabel\> getsensitivitylabel (computeenginecontext & context, konstant DocumentState & State)  | _Noch nicht dokumentiert._
Public Std:: Vector\<Std:: shared_ptr\<Action\>\> computeactions (computeenginecontext & Kontext, Konstante DocumentState & DocumentState, Konstanten applicationaction State & Action State)  | _Noch nicht dokumentiert._
Public Std::p Air\<Std:: Vector\<Std:: shared_ptr\<Action\>\>, bool\> computeaction swithremotestate (computeenginecontext & context, Konstante DocumentState & localdocumentstate, Konstanten DocumentState & remotedocumentstate, Konstanten applicationaction State & Action State)  |  Berechnet Aktionen bei der Wahl zwischen Remote-und lokalem Zustand.
öffentliches void notifycommittedactions (computeenginecontext & Kontext, Konst DocumentState & DocumentState, Konstanten applicationaktionstate & aktionstate)  | _Noch nicht dokumentiert._
public virtual ~ computeengine ()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
_Noch nicht dokumentiert._

  
### <a name="getsensitivitylabel-function"></a>Getsensitivitylabel-Funktion
_Noch nicht dokumentiert._

  
### <a name="computeactions-function"></a>Computeactions-Funktion
_Noch nicht dokumentiert._

  
### <a name="computeactionswithremotestate-function"></a>Computeaktionswithremotestate-Funktion
Berechnet Aktionen bei der Wahl zwischen Remote-und lokalem Zustand.
Der Status wird mit dieser Priorität ausgewählt. Unbekannte Schutz Typen (Vorlage oder Ad-hoc nicht in der Richtlinie). Der Schutzstatus ist immer dem ungeschützten Zustand vorzuziehen. Der Dokument Zustand mit der Bezeichnung wird vor einem anderen als bevorzugt. Die Reihenfolge der Bezeichnungen, die höhere Bezeichnung wird bevorzugt. Zeitstempel der Bezeichnung, das neueste gekennzeichnete Dokument bevorzugen. DocumentState lastmodifiedtime optional implementiert, eine neu geänderte Datei bevorzugen.

Parameter:  
* **Kontext**: Comput-Engine-Kontext. 


* **localdocumentstate**: lokaler Dokument Zustand. 


* **remotedocumentstate**: Remote Dokument Zustand. 


* **Action State**: der Aktionszustand der Anwendung.



  
**Gibt zurück**:-Methoden geben ein paar zurück. enthält zuerst eine Liste der Aktion, die zweite ist, ob Sie auf den lokalen angewendet werden soll, wenn auf dem Remote Dokument falsche Aktionen angewendet werden sollen und der Dokument Zustand verwendet werden soll.
  
### <a name="notifycommittedactions-function"></a>Notifycommittedactions-Funktion
_Noch nicht dokumentiert._

  
### <a name="computeengine-function"></a>~ Computeengine-Funktion
_Noch nicht dokumentiert._
