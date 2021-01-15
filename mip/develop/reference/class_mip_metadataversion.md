---
title: Class MetadataVersion
description: 'Dokumentiert die metadataversion:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 35ed3ef28cd4a1a822c11f64b422a474edcd4b53
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98213605"
---
# <a name="class-metadataversion"></a>Class MetadataVersion 
Eine Schnittstelle für eine MetadataVersion. MetadataVersion bestimmt, welche Metadaten aktiv sind und wie Sie verarbeitet werden.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MetadataVersion (uint32_t Version, MetadataVersionFormat-Flags)  |  MetadataVersion-Konstruktor.
öffentliches virtuelles uint32_t GetValue () konstant  |  Die numerische Version erhalten.
public virtual bool hasflag (MetadataVersionFormat-Flag) konstant  |  Gibt an, ob ein bestimmtes Flag festgelegt ist.
public virtual MetadataVersionFormat GetFlags () konstant  |  Dient zum Festlegen der Flags, die definieren, wie Metadaten für eine bestimmte Version verarbeitet werden.
  
## <a name="members"></a>Member
  
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