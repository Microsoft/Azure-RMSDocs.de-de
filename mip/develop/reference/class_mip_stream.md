---
title: mip::Stream-Klasse
description: 'MIP:: Stream-Klasse von der Microsoft Information Protection (MIP) SDK-Dokumente.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/28/2019
ms.openlocfilehash: 4289b39ba454b19c6836a7eaccb6333cbb9000b4
ms.sourcegitcommit: be05adc7750e22c110b261882de0389b9dfb2726
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2019
ms.locfileid: "55651699"
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



  
**Gibt**: Die Anzahl der gelesenen Bytes.
  
### <a name="write-function"></a>Write-Funktion
Wird aus einem Puffer in den Stream geschrieben.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Gibt**: Die Anzahl der geschriebenen Bytes.
  
### <a name="flush-function"></a>Flush-Funktion
Leert den Stream.

  
**Gibt**: True, wenn erfolgreich, andernfalls False.
  
### <a name="seek-function"></a>Seek-Funktion
Sucht die aktuelle Position im Stream.

Parameter:  
* **Position**, nach der im Stream gesucht werden soll.


  
### <a name="canread-function"></a>"CanRead"-Funktion
Eine Überprüfung, ob aus dem Datenstrom gelesen werden kann.

  
**Gibt**: True, wenn lesbar, andernfalls False.
  
### <a name="canwrite-function"></a>CanWrite-Funktion
Eine Überprüfung, ob in den Datenstrom geschrieben werden kann.

  
**Gibt**: True, wenn beschreibbar, andernfalls False.
  
### <a name="position-function"></a>Position-Funktion
Ruft die aktuelle Position im Stream ab.

  
**Gibt**: Die Position im Stream.
  
### <a name="size-function"></a>Size-Funktion
Ruft den Umfang des Inhalts im Stream ab.

  
**Gibt**: Die Größe des Streams.
  
### <a name="size-function"></a>Size-Funktion
Legt die Größe des Streams fest.

Parameter:  
* **Größe des Streams**.

