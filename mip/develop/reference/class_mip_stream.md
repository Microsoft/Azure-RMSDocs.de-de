---
title: Klassen Datenstrom
description: 'Dokumentiert die Stream:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: a370d6917306f2865c1d91eb7fa90c2880497a04
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566623"
---
# <a name="class-stream"></a>Klassen Datenstrom 
Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
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
  
## <a name="members"></a>Members
  
### <a name="read-function"></a>Read-Funktion
Wird in einen Puffer aus dem Stream eingelesen.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **BufferLength**: Puffergröße. 



  
**Rückgabe**: Die Anzahl der gelesenen Bytes.
  
### <a name="write-function"></a>Write-Funktion
Wird aus einem Puffer in den Stream geschrieben.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **BufferLength**: Puffergröße. 



  
**Rückgabe**: Die Anzahl der geschriebenen Bytes.
  
### <a name="flush-function"></a>Flush-Funktion
Leert den Stream.

  
**Rückgabe**: TRUE bei erfolgreicher Ausführung; andernfalls wird FALSE zurückgegeben.
  
### <a name="seek-function"></a>Seek-Funktion
Sucht die aktuelle Position im Stream.

Parameter:  
* **Position**: für die Suche im Stream.


  
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
* **Stream**: Größe.

