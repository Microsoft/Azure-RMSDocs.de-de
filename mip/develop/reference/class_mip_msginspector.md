---
title: 'MIP:: msginspector-Klasse'
description: 'Dokumentiert die MIP:: msginspector-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: d1234168e4ce3996077b705e904f5765b761ec4c
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73558606"
---
# <a name="class-mipmsginspector"></a>MIP:: msginspector-Klasse 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Konstanten Std:: Vector\<uint8_t\>& GetBody ()  |  Gibt den Text der Meldung an, wenn txt/HTML als UTF8 formatiert ist.
öffentlicher BodyType getbodytype () Konstanten  |  Typ des Get-Texts.
Public Konstanten Std:: Vector\<Std:: unique_ptr\<msgattachmentdata\>\>& getattachments () konstant.  |  Eine Liste der Anlage als Datenobjekte der Nachrichten Anlage erhalten.
  
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