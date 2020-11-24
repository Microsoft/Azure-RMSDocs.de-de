---
title: Class MetadataEntry
description: 'Dokumentiert die metadataentry:: undefinierte-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 026fecc8da2008a2798ca8bc44951bc97ec5455a
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566785"
---
# <a name="class-metadataentry"></a>Class MetadataEntry 
Eine Abstraktions Klasse für den Metadateneintrag.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MetadataEntry (Konstanten Std:: String& Key, Konstanten Std:: String& Wert, uint32_t Version)  |  Der c-Tor für eine MetadataEntry-Abstraktion.
Public MetadataEntry (Konstante Std:: String& Key, Konstanten Std:: String& Wert, konstant MetadataVersion& Version)  |  Der c-Tor für eine MetadataEntry-Abstraktion.
Public MetadataEntry (Konstanten Std:: String& Key, Konstanten Std:: String& Wert)  |  Der c/Tor für eine MetadataEntry-Abstraktion, Version ist auf den Standardwert 0 festgelegt.
Public Konstanten Std:: String& GetKey () Konstanten  |  Den Schlüssel für den Metadateneintrag erhalten.
Public Konstanten Std:: String& GetValue () Konstanten  |  Den Metadateneintrags Wert erhalten.
Public MetadataVersion GetVersion () konstant  |  Die Version des Metadateneintrags erhalten.
  
## <a name="members"></a>Members
  
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