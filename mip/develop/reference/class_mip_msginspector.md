---
title: Klasse msginspector
description: 'Dokumentiert die msginspector:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 9f19c53a2c6eca82cdf1469c63436ad56112dc52
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "95567943"
---
# <a name="class-msginspector"></a>Klasse msginspector 
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector \<uint8_t\>& GetBody () Konstanten  |  Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.
Public Ganzzahl ohne Vorzeichen int getcodepage () konstant  |  Codepage für die Text Codierung, die für txt-, HTML-Textformate relevant ist.
öffentlicher BodyType getbodytype () Konstanten  |  Typ des Get-Texts.
Public Konstanten Std:: Vector \<std::shared_ptr\<MsgAttachmentData\> \>& getattachments () konstant  |  Eine Liste der Anlage als Datenobjekte der Nachrichten Anlage erhalten.
Public Inspector Type GetInspector Type () Konstanten  |  Dateitypen erhalten.
Public Std:: shared_ptr \<Stream\> GetFileStream () Konstanten  |  Den Dateistream erhalten.
  
## <a name="members"></a>Members
  
### <a name="getbody-function"></a>GetBody-Funktion
Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.

  
**Gibt Folgendes zurück**: ein Vektor von Bytes.
  
### <a name="getcodepage-function"></a>Getcodepage-Funktion
Codepage für die Text Codierung, die für txt-, HTML-Textformate relevant ist.

  
**Gibt Folgendes zurück**: eine nicht signierte Codepage. 
  
**Siehe auch**: [https://docs.microsoft.com/en-us/windows/win32/intl/code-page-identifiers](/windows/win32/intl/code-page-identifiers)
  
### <a name="getbodytype-function"></a>Getbodytype-Funktion
Typ des Get-Texts.

  
**Gibt Folgendes zurück**: der Texttyp der Nachricht.
  
### <a name="getattachments-function"></a>Getattachments-Funktion
Eine Liste der Anlage als Datenobjekte der Nachrichten Anlage erhalten.

  
**Gibt Folgendes zurück**: ein Vektor von Std:: unique_ptr<MsgAttachmentData>
  
### <a name="getinspectortype-function"></a>Getinspectortype-Funktion
Dateitypen erhalten.

  
**Gibt Folgendes zurück**: Inspector Type.
  
### <a name="getfilestream-function"></a>GetFileStream-Funktion
Den Dateistream erhalten.

  
**Gibt Folgendes zurück**: einen freigegebenen PTR für den Dateistream.