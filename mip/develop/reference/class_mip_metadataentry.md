---
title: Class MetadataEntry
description: 'Dokumentiert die metadataentry:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: c9c1c8f9683ebb4be079f1817aa92a71e72005ca
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81766506"
---
# <a name="class-metadataentry"></a>Class MetadataEntry 
Eine Abstraktions Klasse für den Metadateneintrag.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MetadataEntry (Konstante Std:: String& Key, Konstanten Std:: String& Wert, Ganzzahl ohne Vorzeichen int-Version)  |  Der c-Tor für eine MetadataEntry-Abstraktion.
Public MetadataEntry (Konstanten Std:: String& Key, Konstanten Std:: String& Wert)  |  Der c/Tor für eine MetadataEntry-Abstraktion, Version ist auf den Standardwert 0 festgelegt.
Public Konstanten Std:: String& GetKey () Konstanten  |  Den Schlüssel für den Metadateneintrag erhalten.
Public Konstanten Std:: String& GetValue () Konstanten  |  Den Metadateneintrags Wert erhalten.
Public Ganzzahl ohne Vorzeichen int GetVersion () Konstanten  |  Die Version des Metadateneintrags erhalten.
  
## <a name="members"></a>Member
  
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