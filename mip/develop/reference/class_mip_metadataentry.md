---
title: Class MetadataEntry
description: 'Dokumentiert die metadataentry:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: dd758d49d0c207fe5e4c5eeb04bb63ba91174fcc
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98215186"
---
# <a name="class-metadataentry"></a>Class MetadataEntry 
Eine Abstraktions Klasse für den Metadateneintrag.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MetadataEntry (Konstanten Std:: String& Key, Konstanten Std:: String& Wert, uint32_t Version)  |  Der c-Tor für eine MetadataEntry-Abstraktion.
Public MetadataEntry (Konstante Std:: String& Key, Konstanten Std:: String& Wert, konstant MetadataVersion& Version)  |  Der c-Tor für eine MetadataEntry-Abstraktion.
Public MetadataEntry (Konstanten Std:: String& Key, Konstanten Std:: String& Wert)  |  Der c/Tor für eine MetadataEntry-Abstraktion, Version ist auf den Standardwert 0 festgelegt.
Public Konstanten Std:: String& GetKey () Konstanten  |  Den Schlüssel für den Metadateneintrag erhalten.
Public Konstanten Std:: String& GetValue () Konstanten  |  Den Metadateneintrags Wert erhalten.
Public MetadataVersion GetVersion () konstant  |  Die Version des Metadateneintrags erhalten.
  
## <a name="members"></a>Member
  
### <a name="metadataentry-function"></a>MetadataEntry-Funktion
Der c-Tor für eine MetadataEntry-Abstraktion.

Parameter:  
* **Schlüssel**: metadatenschlüsseleintrag. 


* **Wert**: Eintrag für Metadatenwert 


* **Version**: metadatenversionswert


  
### <a name="metadataentry-function"></a>MetadataEntry-Funktion
Der c-Tor für eine MetadataEntry-Abstraktion.

Parameter:  
* **Schlüssel**: metadatenschlüsseleintrag. 


* **Wert**: Eintrag für Metadatenwert 


* **Version**: metadatenversionswert


  
### <a name="metadataentry-function"></a>MetadataEntry-Funktion
Der c/Tor für eine MetadataEntry-Abstraktion, Version ist auf den Standardwert 0 festgelegt.

Parameter:  
* **Schlüssel**: metadatenschlüsseleintrag. 


* **Wert**: Eintrag für Metadatenwert


  
### <a name="getkey-function"></a>GetKey-Funktion
Den Schlüssel für den Metadateneintrag erhalten.

  
**Gibt Folgendes zurück**: Metadateneintrags Schlüssel.
  
### <a name="getvalue-function"></a>GetValue-Funktion
Den Metadateneintrags Wert erhalten.

  
**Gibt Folgendes zurück**: Metadateneintrags Wert.
  
### <a name="getversion-function"></a>GetVersion-Funktion
Die Version des Metadateneintrags erhalten.

  
**Gibt Folgendes zurück**: Metadateneintrags Version.