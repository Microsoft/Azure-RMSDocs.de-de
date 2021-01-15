---
title: Class computeengine
description: 'Dokumentiert die computeengine:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: bd3f287022b567ba2531108f9f24f614a3bb6b01
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98211905"
---
# <a name="class-computeengine"></a>Class computeengine 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<std::shared_ptr\<Label\> \> listsensitivitylabels (Konstanten Std:: Vector \<std::string\>& contentformats)  | _Noch nicht dokumentiert._
Public Std:: shared_ptr \<ContentLabel\> getsensitivitylabel (computeenginecontext& context, konstant DocumentState& State)  | _Noch nicht dokumentiert._
Public Std:: Vector \<std::shared_ptr\<Action\> \> computeactions (computeenginecontext& context, Konstante DocumentState& DocumentState, Konstanten applicationaktionstate& aktionstate)  | _Noch nicht dokumentiert._
Public Std::p Air \<std::vector\<std::shared_ptr\<Action\> \> , bool \> computeaktionswithremotestate (computeenginecontext& context, Konstante DocumentState& localdocumentstate, Konstanten DocumentState& remotedocumentstate, Konstanten applicationaktionstate& aktionstate)  |  Berechnet Aktionen bei der Wahl zwischen Remote-und lokalem Zustand.
öffentliches void notifycommittedactions (computeenginecontext& Kontext, Konst DocumentState& DocumentState, Konstanten applicationaktionstate& aktionstate)  | _Noch nicht dokumentiert._
Public Konstanten Std:: shared_ptr \<Label\> getdefaultlabel (Konstante Std:: String& contentformat) konstant  | _Noch nicht dokumentiert._
public const std::string& GetMoreInfoUrl() const  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getupn () Konstanten  | _Noch nicht dokumentiert._
public bool islabelingrequired (Konstanten Std:: String& contentformat) konstant  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getfleid () Konstanten  | _Noch nicht dokumentiert._
public bool hasclassificationrules (Konstanten Std:: Vector \<std::string\>& contentformats) konstant  | _Noch nicht dokumentiert._
public bool isenhancedclassificationaktivierte () Konstante  | _Noch nicht dokumentiert._
Public Std:: shared_ptr \<Label\> getlabelbyid (Konstanten Std:: String& ID) konstant  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& gettenantid () Konstanten  | _Noch nicht dokumentiert._
öffentliches void setsensitivitytypesrulepackages (Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \> && Custom)  | _Noch nicht dokumentiert._
Public Konstanten Std:: Vector \<std::shared_ptr\<SensitivityTypesRulePackage\> \>& getsensitivitytypesrulepackages () Konstanten  | _Noch nicht dokumentiert._
Public Konstanten Std:: Vector \<std::pair\<std::string, std::string\> \>& getcustomsettings () Konstanten  | _Noch nicht dokumentiert._
Public uint32_t GetOpcMetadataVersion () konstant  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getuserobjectid () Konstanten  | _Noch nicht dokumentiert._
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

  
### <a name="getdefaultlabel-function"></a>Getdefaultlabel-Funktion
_Noch nicht dokumentiert._

  
### <a name="getmoreinfourl-function"></a>Getmoreingefourl-Funktion
_Noch nicht dokumentiert._

  
### <a name="getupn-function"></a>Getupn-Funktion
_Noch nicht dokumentiert._

  
### <a name="islabelingrequired-function"></a>Islabelingrequired-Funktion
_Noch nicht dokumentiert._

  
### <a name="getfileid-function"></a>Getfleid-Funktion
_Noch nicht dokumentiert._

  
### <a name="hasclassificationrules-function"></a>Hasclassificationrules-Funktion
_Noch nicht dokumentiert._

  
### <a name="isenhancedclassificationenabled-function"></a>Isenhancedclassificationaktivierte Funktion
_Noch nicht dokumentiert._

  
### <a name="getlabelbyid-function"></a>Getlabelbyid-Funktion
_Noch nicht dokumentiert._

  
### <a name="gettenantid-function"></a>Gettenantid-Funktion
_Noch nicht dokumentiert._

  
### <a name="setsensitivitytypesrulepackages-function"></a>Setsensitivitytypesrulepackages-Funktion
_Noch nicht dokumentiert._

  
### <a name="getsensitivitytypesrulepackages-function"></a>Getsensitivitytypesrulepackages-Funktion
_Noch nicht dokumentiert._

  
### <a name="getcustomsettings-function"></a>Getcustomsettings-Funktion
_Noch nicht dokumentiert._

  
### <a name="getopcmetadataversion-function"></a>GetOpcMetadataVersion-Funktion
_Noch nicht dokumentiert._

  
### <a name="getuserobjectid-function"></a>Getuserobjectid-Funktion
_Noch nicht dokumentiert._

  
### <a name="computeengine-function"></a>~ Computeengine-Funktion
_Noch nicht dokumentiert._
