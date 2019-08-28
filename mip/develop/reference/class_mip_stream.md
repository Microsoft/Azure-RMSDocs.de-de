---
title: mip::Stream-Klasse
description: 'Dokumentiert die MIP:: Stream-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: c799708931103c595ce1ad66a41accb9f0dcfc85
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70056837"
---
# <a name="class-mipstream"></a>mip::Stream-Klasse 
Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public int64_t Read(uint8_t* buffer, int64_t bufferLength)  |  Wird in einen Puffer aus dem Stream eingelesen.
public int64_t Write(const uint8_t* buffer, int64_t bufferLength)  |  Wird aus einem Puffer in den Stream geschrieben.
public bool Flush()  |  Leert den Stream.
public void Seek(int64_t position)  |  Sucht die aktuelle Position im Stream.
public bool CanRead() const  |  Eine Überprüfung, ob aus dem Datenstrom gelesen werden kann.
public bool CanWrite() const  |  Eine Überprüfung, ob in den Datenstrom geschrieben werden kann.
public int64_t Position()  |  Ruft die aktuelle Position im Stream ab.
public int64_t Size()  |  Ruft den Umfang des Inhalts im Stream ab.
public void Size(int64_t value)  |  Legt die Größe des Streams fest.
  
## <a name="members"></a>Member
  
### <a name="read-function"></a>Read-Funktion
Wird in einen Puffer aus dem Stream eingelesen.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Gibt Folgendes zurück**: Anzahl der gelesenen Bytes.
  
### <a name="write-function"></a>Write-Funktion
Wird aus einem Puffer in den Stream geschrieben.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Gibt Folgendes zurück**: Anzahl der geschriebenen Bytes.
  
### <a name="flush-function"></a>Flush-Funktion
Leert den Stream.

  
**Gibt Folgendes zurück**: True, wenn erfolgreich, andernfalls false.
  
### <a name="seek-function"></a>Seek-Funktion
Sucht die aktuelle Position im Stream.

Parameter:  
* **Position**, nach der im Stream gesucht werden soll.


  
### <a name="canread-function"></a>CanRead-Funktion
Eine Überprüfung, ob aus dem Datenstrom gelesen werden kann.

  
**Gibt Folgendes zurück**: True, wenn lesbar, sonst false.
  
### <a name="canwrite-function"></a>CanWrite-Funktion
Eine Überprüfung, ob in den Datenstrom geschrieben werden kann.

  
**Gibt Folgendes zurück**: True, wenn beschreibbar ist, andernfalls false.
  
### <a name="position-function"></a>Position-Funktion
Ruft die aktuelle Position im Stream ab.

  
**Gibt Folgendes zurück**: Die Position innerhalb des Streams.
  
### <a name="size-function"></a>Size-Funktion
Ruft den Umfang des Inhalts im Stream ab.

  
**Gibt Folgendes zurück**: Die Streamgröße.
  
### <a name="size-function"></a>Size-Funktion
Legt die Größe des Streams fest.

Parameter:  
* **Größe des Streams**.

