---
title: Class MetadataVersion
description: 'Dokumentiert die metadataversion:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 05154ec7777fb94478c2065f6e637dea47d58d28
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566767"
---
# <a name="class-metadataversion"></a>Class MetadataVersion 
Eine Schnittstelle für eine MetadataVersion. MetadataVersion bestimmt, welche Metadaten aktiv sind und wie Sie verarbeitet werden.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MetadataVersion (uint32_t Version, MetadataVersionFormat-Flags)  |  MetadataVersion-Konstruktor.
öffentliches virtuelles uint32_t GetValue () konstant  |  Die numerische Version erhalten.
public virtual bool hasflag (MetadataVersionFormat-Flag) konstant  |  Gibt an, ob ein bestimmtes Flag festgelegt ist.
public virtual MetadataVersionFormat GetFlags () konstant  |  Dient zum Festlegen der Flags, die definieren, wie Metadaten für eine bestimmte Version verarbeitet werden.
  
## <a name="members"></a>Members
  
### <a name="metadataversion-function"></a>MetadataVersion-Funktion
MetadataVersion-Konstruktor.

Parameter:  
* **Version**: für metadatenaktionen zu verwendende numerische Version 


* **Flags**: Flags, um anzugeben, wie die Version zum Berechnen von metadatenaktionen verwendet wird.


  
### <a name="getvalue-function"></a>GetValue-Funktion
Die numerische Version erhalten.

  
**Gibt Folgendes zurück**: die numerische Version.
  
### <a name="hasflag-function"></a>Hasflag-Funktion
Gibt an, ob ein bestimmtes Flag festgelegt ist.

  
**Gibt Folgendes zurück**: true, wenn das-Flag festgelegt ist.
  
### <a name="getflags-function"></a>GetFlags-Funktion
Dient zum Festlegen der Flags, die definieren, wie Metadaten für eine bestimmte Version verarbeitet werden.

  
**Returns**: die Flags, die angeben, wie die Metadaten verarbeitet werden.