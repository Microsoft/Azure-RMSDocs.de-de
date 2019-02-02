---
title: Klasse mip::FileExecutionState
description: Dokumentiert die mip::fileexecutionstate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 08a9064645f0ffb3ffbaa72f00db26c5b29d3643
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55652335"
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