---
title: 'MIP:: msginspector-Klasse'
description: 'Dokumentiert die MIP:: msginspector-Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: cb0b85b0de42eae46d6cd7c9c6d6e18680b2e545
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69892748"
---
# <a name="class-mipmsginspector"></a>MIP:: msginspector-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<uint8_t\>& GetBody ()  |  Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.
öffentlicher BodyType getbodytype () Konstanten  |  Typ des Get-Texts.
Public Konstanten Std::\<Vector Std:: unique_ptr\<msgattachmentdata\>\>& getattachments () Konstanten  |  Eine Liste der Anlage als Datenobjekte der Nachrichten Anlage erhalten.
Public Inspector Type GetInspector Type () Konstanten  |  Dateitypen erhalten.
Public Std:: shared_ptr\<Stream\> GetFileStream () konstant  |  Den Dateistream erhalten.
  
## <a name="members"></a>Member
  
### <a name="getbody-function"></a>GetBody-Funktion
Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.

  
**Gibt Folgendes zurück**: Ein Vektor von Bytes.
  
### <a name="getbodytype-function"></a>Getbodytype-Funktion
Typ des Get-Texts.

  
**Gibt Folgendes zurück**: Der Texttyp der Nachricht.
  
### <a name="getattachments-function"></a>Getattachments-Funktion
Eine Liste der Anlage als Datenobjekte der Nachrichten Anlage erhalten.

  
**Gibt Folgendes zurück**: Ein Vektor von Std:: unique_ptr<MsgAttachmentData>
  
### <a name="getinspectortype-function"></a>Getinspectortype-Funktion
Dateitypen erhalten.

  
**Gibt Folgendes zurück**: Inspector Type.
  
### <a name="getfilestream-function"></a>GetFileStream-Funktion
Den Dateistream erhalten.

  
**Gibt Folgendes zurück**: Ein frei gegebener PTR für den Datei Datenstrom.