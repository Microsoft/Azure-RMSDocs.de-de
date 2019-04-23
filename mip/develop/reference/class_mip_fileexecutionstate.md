---
title: Klasse mip::FileExecutionState
description: Dokumentiert die mip::fileexecutionstate-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: bdf0814e56d64bd16918a6f4d269a057620f92f5
ms.sourcegitcommit: 682dc48cbbcbee93b26ab3872231b3fa54d3f6eb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "60184670"
---
# <a name="class-mipfileexecutionstate"></a>Klasse mip::FileExecutionState 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public virtual DataState GetDataState() const  |  Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert
public virtual std::shared_ptr\<ClassificationResults\> GetClassificationResults(const std::shared_ptr\<FileHandler\> &, const std::vector\<std::shared_ptr\<ClassificationRequest\>\> &) const  |  Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.
public virtual std::vector\<uint8_t\> GetSerializedProtectionInfo() const  |  Geben Sie einen Puffer mit den serialisierten PL zurück
public virtual std::map\<std::string, std::string\> GetAuditMetadata() const  |  Geben Sie eine Zuordnung der Anwendung spezifischen Überwachung Schlüssel-Wert-Paaren zurück.
  
## <a name="members"></a>Member
  
### <a name="getdatastate-function"></a>GetDataState-Funktion
Ruft den Inhaltsstatus ab, während die Anwendung mit diesem interagiert

  
**Gibt**: Status der Inhaltsdaten
  
### <a name="getclassificationresults-function"></a>GetClassificationResults-Funktion
Gibt eine Zuordnung der Klassifizierungsergebnisse zurück.

Parameter:  
* **FileHandler**:-das Dateihandle der Datei verwendet 


* **ClassificationIds**: eine Liste der IDs-Klassifizierung. 



  
**Gibt**: Eine Liste der Klassifizierungsergebnisse.
  
### <a name="getserializedprotectioninfo-function"></a>GetSerializedProtectionInfo-Funktion
Geben Sie einen Puffer mit den serialisierten PL zurück

  
**Gibt**: Ein Puffer mit den serialisierten PL
  
### <a name="getauditmetadata-function"></a>GetAuditMetadata-Funktion
Geben Sie eine Zuordnung der Anwendung spezifischen Überwachung Schlüssel-Wert-Paaren zurück.

  
**Gibt**: Eine Liste der Anwendung spezifischen Überwachung Metadaten registriert Schlüssel-Wert-Paare Absender: Für den Absender-Empfänger-e-Mail-Id: Stellt ein JSON-Array von Empfängern für eine e-Mail LastModifiedBy dar: E-Mail-Id für den Benutzer, der den Inhalt LastModifiedDate & lt; zuletzt geändert: Datum, an der letzten des Inhalts Änderung