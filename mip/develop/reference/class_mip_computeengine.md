---
title: Class computeengine
description: 'Dokumentiert die computeengine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 7371c72cb10e1f08fcacaf286597f9534737996d
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567226"
---
# <a name="class-computeengine"></a>Class computeengine 
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<std::shared_ptr\<Label\> \>& listsensitivitylabels ()  | _Noch nicht dokumentiert._
Public Std:: shared_ptr \<ContentLabel\> getsensitivitylabel (computeenginecontext& context, konstant DocumentState& State)  | _Noch nicht dokumentiert._
Public Std:: Vector \<std::shared_ptr\<Action\> \> computeactions (computeenginecontext& context, Konstante DocumentState& DocumentState, Konstanten applicationaktionstate& aktionstate)  | _Noch nicht dokumentiert._
Public Std::p Air \<std::vector\<std::shared_ptr\<Action\> \> , bool \> computeaktionswithremotestate (computeenginecontext& context, Konstante DocumentState& localdocumentstate, Konstanten DocumentState& remotedocumentstate, Konstanten applicationaktionstate& aktionstate)  |  Berechnet Aktionen bei der Wahl zwischen Remote-und lokalem Zustand.
öffentliches void notifycommittedactions (computeenginecontext& Kontext, Konst DocumentState& DocumentState, Konstanten applicationaktionstate& aktionstate)  | _Noch nicht dokumentiert._
Public Konstanten Std:: shared_ptr \<Label\>& getdefaultlabel () Konstanten  | _Noch nicht dokumentiert._
public const std::string& GetMoreInfoUrl() const  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getupn () Konstanten  | _Noch nicht dokumentiert._
public bool IsLabelingRequired() const  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getfleid () Konstanten  | _Noch nicht dokumentiert._
public bool hasclassificationrules () konstant  | _Noch nicht dokumentiert._
public bool isenhancedclassificationaktivierte () Konstante  | _Noch nicht dokumentiert._
Public Std:: shared_ptr \<Label\> getlabelbyid (Konstanten Std:: String& ID) konstant  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& gettenantid () Konstanten  | _Noch nicht dokumentiert._
öffentliches void setsensitivitytypesrulepackages (Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \> && Custom)  | _Noch nicht dokumentiert._
Public Konstanten Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \>& getsensitivitytypesrulepackages () Konstanten  | _Noch nicht dokumentiert._
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  | _Noch nicht dokumentiert._
Public uint32_t GetOpcMetadataVersion () konstant  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getuserobjectid () Konstanten  | _Noch nicht dokumentiert._
public virtual ~ computeengine ()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Members
  
### <a name="listsensitivitylabels-function"></a>Listsensitivitylabels-Funktion
Noch nicht dokumentiert.

  
### <a name="getsensitivitylabel-function"></a>Getsensitivitylabel-Funktion
Noch nicht dokumentiert.

  
### <a name="computeactions-function"></a>Computeactions-Funktion
Noch nicht dokumentiert.

  
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
Noch nicht dokumentiert.

  
### <a name="getdefaultlabel-function"></a>Getdefaultlabel-Funktion
Noch nicht dokumentiert.

  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
Noch nicht dokumentiert.

  
### <a name="getupn-function"></a>Getupn-Funktion
Noch nicht dokumentiert.

  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
Noch nicht dokumentiert.

  
### <a name="getfileid-function"></a>Getfleid-Funktion
Noch nicht dokumentiert.

  
### <a name="hasclassificationrules-function"></a>Hasclassificationrules-Funktion
Noch nicht dokumentiert.

  
### <a name="isenhancedclassificationenabled-function"></a>Isenhancedclassificationaktivierte Funktion
Noch nicht dokumentiert.

  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
Noch nicht dokumentiert.

  
### <a name="gettenantid-function"></a>Gettenantid-Funktion
Noch nicht dokumentiert.

  
### <a name="setsensitivitytypesrulepackages-function"></a>Setsensitivitytypesrulepackages-Funktion
Noch nicht dokumentiert.

  
### <a name="getsensitivitytypesrulepackages-function"></a>Getsensitivitytypesrulepackages-Funktion
Noch nicht dokumentiert.

  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
Noch nicht dokumentiert.

  
### <a name="getopcmetadataversion-function"></a>GetOpcMetadataVersion-Funktion
Noch nicht dokumentiert.

  
### <a name="getuserobjectid-function"></a>Getuserobjectid-Funktion
Noch nicht dokumentiert.

  
### <a name="computeengine-function"></a>~ Computeengine-Funktion
Noch nicht dokumentiert.
