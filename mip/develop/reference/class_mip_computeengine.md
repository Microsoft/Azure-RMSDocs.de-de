---
title: Class computeengine
description: 'Dokumentiert die computeengine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 3b33c9a91f40422c29282ddee9292f6bbbad90c9
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81763508"
---
# <a name="class-computeengine"></a>Class computeengine 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std::\<Vector Std:: shared_ptr\<-Bezeichnung\> \>& listsensitivitylabels ()  | _Noch nicht dokumentiert._
Public Std:: shared_ptr\<contentlabel\> getsensitivitylabel (computeenginecontext& context, konstant DocumentState& State)  | _Noch nicht dokumentiert._
Public Std:: Vector\<Std:: shared_ptr\<Action\> \> computeactions (computeenginecontext& context, Konstanten DocumentState& DocumentState, Konstanten applicationaction State& Action State)  | _Noch nicht dokumentiert._
Public Std::p Air\<Std:: Vector\<Std:: shared_ptr\<Action\>\>, bool\> computeaction swithremotestate (computeenginecontext& context, Konstanten DocumentState& localdocumentstate, Konstanten DocumentState& remotedocumentstate, Konstanten applicationaction State& Action State)  |  Berechnet Aktionen bei der Wahl zwischen Remote-und lokalem Zustand.
öffentliches void notifycommittedactions (computeenginecontext& Kontext, Konst DocumentState& DocumentState, Konstanten applicationaktionstate& aktionstate)  | _Noch nicht dokumentiert._
öffentliche Konstante Std:: shared_ptr\<Bezeichnung\>& getdefaultlabel () Konstanten  | _Noch nicht dokumentiert._
public const std::string& GetMoreInfoUrl() const  | _Noch nicht dokumentiert._
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
Der Status wird mit dieser Priorität ausgewählt. Unbekannte Schutz Typen (Vorlage oder Ad-hoc nicht in der Richtlinie). Der Schutzstatus ist immer dem ungeschützten Zustand vorzuziehen. Der Dokument Zustand mit der Bezeichnung wird vor einem anderen als bevorzugt. Die Reihenfolge der Bezeichnungen, die höhere Bezeichnung wird bevorzugt. Zeitstempel der Bezeichnung, das neueste gekennzeichnete Dokument bevorzugen. [DocumentState](class_mip_documentstate.md) Lastmodifiedtime optional implementiert, neu geänderte Datei bevorzugen.

Parameter:  
* **Kontext**: Comput-Engine-Kontext. 


* **localdocumentstate**: lokaler Dokument Zustand. 


* **remotedocumentstate**: Remote Dokument Zustand. 


* **Action State**: der Aktionszustand der Anwendung.



  
**Gibt zurück**:-Methoden geben ein paar zurück. enthält zuerst eine Liste der Aktion, die zweite ist, ob Sie auf den lokalen angewendet werden soll, wenn auf dem Remote Dokument falsche Aktionen angewendet werden sollen und der Dokument Zustand verwendet werden soll.
  
### <a name="notifycommittedactions-function"></a>Notifycommittedactions-Funktion
_Noch nicht dokumentiert._

  
### <a name="getdefaultlabel-function"></a>Getdefaultlabel-Funktion
_Noch nicht dokumentiert._

  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
_Noch nicht dokumentiert._

  
### <a name="computeengine-function"></a>~ Computeengine-Funktion
_Noch nicht dokumentiert._
