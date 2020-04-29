---
title: Klasse msginspector
description: 'Dokumentiert die msginspector:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 04/16/2020
ms.openlocfilehash: 79a044099c09d799d77f4af11eb0b80ecc21d6d6
ms.sourcegitcommit: f54920bf017902616589aca30baf6b64216b6913
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81761482"
---
# <a name="class-msginspector"></a>Klasse msginspector 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<uint8_t\>& GetBody ()  |  Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.
öffentlicher BodyType getbodytype () Konstanten  |  Typ des Get-Texts.
Public Konstanten Std::\<Vector Std:: shared_ptr\<msgattachmentdata\> \>& getattachments () Konstanten  |  Eine Liste der Anlage als Datenobjekte der Nachrichten Anlage erhalten.
Public Inspector Type GetInspector Type () Konstanten  |  Dateitypen erhalten.
Public Std:: shared_ptr\<Stream\> GetFileStream () konstant  |  Den Dateistream erhalten.
  
## <a name="members"></a>Member
  
### <a name="getbody-function"></a>GetBody-Funktion
Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.

  
**Gibt Folgendes zurück**: ein Vektor von Bytes.
  
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