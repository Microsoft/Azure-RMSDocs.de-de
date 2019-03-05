---
title: Klasse mip::FileExecutionState
description: Dokumentiert die mip::fileexecutionstate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 9433ca2f47496e0d28d46c68b3100b53cd25c3f3
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57333683"
---
# <a name="class-mipfileexecutionstate"></a>Klasse mip::FileExecutionState 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
öffentliche virtuelle Std:: Map\<Std:: String, Std:: shared_ptr\<ClassificationResult\> \> GetClassificationResults (const Std:: shared_ptr\<FileHandler\> &, const std :: Vector\<Std:: shared_ptr\<ClassificationRequest\> \> &) const  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual std::vector\<uint8_t\> GetSerializedProtectionInfo() const  |  Geben Sie einen Puffer mit den serialisierten PL zurück
  
## <a name="members"></a>Member
  
### <a name="getclassificationresults-function"></a>GetClassificationResults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **FileHandler**:-das Dateihandle der Datei verwendet 


* **ClassificationIds**: eine Liste der IDs-Klassifizierung. 



  
**Gibt**: Eine Liste der Klassifizierung Ergebnis.
  
### <a name="getserializedprotectioninfo-function"></a>GetSerializedProtectionInfo-Funktion
Geben Sie einen Puffer mit den serialisierten PL zurück

  
**Gibt**: Ein Puffer mit den serialisierten PL
