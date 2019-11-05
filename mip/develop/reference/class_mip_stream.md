---
title: mip::Stream-Klasse
description: 'Dokumentiert die MIP:: Stream-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: f1bd4220369d036c2071453412844e0691efb2ec
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73559975"
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



  
**Rückgabe**: Die Anzahl der gelesenen Bytes.
  
### <a name="write-function"></a>Write-Funktion
Wird aus einem Puffer in den Stream geschrieben.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Rückgabe**: Die Anzahl der geschriebenen Bytes.
  
### <a name="flush-function"></a>Flush-Funktion
Leert den Stream.

  
**Rückgabe**: TRUE bei erfolgreicher Ausführung; andernfalls wird FALSE zurückgegeben.
  
### <a name="seek-function"></a>Seek-Funktion
Sucht die aktuelle Position im Stream.

Parameter:  
* **Position**, nach der im Stream gesucht werden soll.


  
### <a name="canread-function"></a>CanRead-Funktion
Eine Überprüfung, ob aus dem Datenstrom gelesen werden kann.

  
**Rückgabe**: TRUE, wenn lesbar; andernfalls wird FALSE zurückgegeben.
  
### <a name="canwrite-function"></a>CanWrite-Funktion
Eine Überprüfung, ob in den Datenstrom geschrieben werden kann.

  
**Rückgabe**: TRUE, wenn beschreibbar; andernfalls wird FALSE zurückgegeben.
  
### <a name="position-function"></a>Position-Funktion
Ruft die aktuelle Position im Stream ab.

  
**Rückgabe**: Position im Stream.
  
### <a name="size-function"></a>Size-Funktion
Ruft den Umfang des Inhalts im Stream ab.

  
**Rückgabe**: Größe des Streams.
  
### <a name="size-function"></a>Size-Funktion
Legt die Größe des Streams fest.

Parameter:  
* **Größe des Streams**.

