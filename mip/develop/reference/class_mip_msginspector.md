---
title: 'MIP:: msginspector-Klasse'
description: 'Dokumentiert die MIP:: msginspector-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 274ada562bae46add2429a2f87442bb77528ea05
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70054276"
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