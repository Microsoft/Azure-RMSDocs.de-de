---
title: Microsoft Information Protection-Klasse „Stream“
description: Referenz für die Microsoft Information Protection-Klasse „Stream“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: e6296c5e15590741e008979dcf12373ff5fcdf00
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47445222"
---
# <a name="class-mipstream"></a>class mip::Stream 
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
  
### <a name="read"></a>Überwachungsdaten
Wird in einen Puffer aus dem Stream eingelesen.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Rückgabe**: Die Anzahl der gelesenen Bytes.
  
### <a name="write"></a>Überwachungsdaten
Wird aus einem Puffer in den Stream geschrieben.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Rückgabe**: Die Anzahl der geschriebenen Bytes.
  
### <a name="flush"></a>Leerung
Leert den Stream.

  
**Rückgabe**: TRUE bei erfolgreicher Ausführung; andernfalls wird FALSE zurückgegeben.
  
### <a name="seek"></a>Seek
Sucht die aktuelle Position im Stream.

Parameter:  
* **Position**, nach der im Stream gesucht werden soll.


  
### <a name="canread"></a>CanRead
Eine Überprüfung, ob aus dem Datenstrom gelesen werden kann.

  
**Rückgabe**: TRUE, wenn lesbar; andernfalls wird FALSE zurückgegeben.
  
### <a name="canwrite"></a>CanWrite
Eine Überprüfung, ob in den Datenstrom geschrieben werden kann.

  
**Rückgabe**: TRUE, wenn beschreibbar; andernfalls wird FALSE zurückgegeben.
  
### <a name="position"></a>Position
Ruft die aktuelle Position im Stream ab.

  
**Rückgabe**: Position im Stream.
  
### <a name="size"></a>Size
Ruft den Umfang des Inhalts im Stream ab.

  
**Rückgabe**: Größe des Streams.
  
### <a name="size"></a>Size
Legt die Größe des Streams fest.

Parameter:  
* **Größe des Streams**.

