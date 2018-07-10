# <a name="class-mipstream"></a>mip::Stream-Klasse 
Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
 public int64_t Read(uint8_t* buffer, int64_t bufferLength)  |  Wird in einen Puffer aus dem Stream eingelesen.
 public int64_t Write(const uint8_t* buffer, int64_t bufferLength)  |  Wird aus einem Puffer in den Stream geschrieben.
 public bool Flush()  |  Leert den Stream.
 public void Seek(uint64_t position)  |  Sucht die aktuelle Position im Stream.
 public bool CanRead() const  |  Eine Überprüfung, ob der Stream gelesen werden kann.
 public bool CanWrite() const  |  Eine Überprüfung, ob der Stream geschrieben werden kann.
 public uint64_t Position()  |  Ruft die aktuelle Position im Stream ab.
 public uint64_t Size()  |  Ruft den Umfang des Inhalts im Stream ab.
 public void Size(uint64_t value)  |  Legt die Größe des Streams fest.
  
## <a name="members"></a>Member
  
### <a name="read"></a>Überwachungsdaten
Wird in einen Puffer aus dem Stream eingelesen.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Rückgabe**: Anzahl der tatsächlich gelesenen Bytes.
  
### <a name="write"></a>Überwachungsdaten
Wird aus einem Puffer in den Stream geschrieben.

Parameter:  
* **buffer**: Zeiger auf einen Puffer 


* **bufferLength**: Puffergröße. 



  
**Rückgabe**: Anzahl der tatsächlich geschriebenen Bytes
  
### <a name="flush"></a>Leerung
Leert den Stream.

  
**Rückgabe**: TRUE bei erfolgreicher Ausführung; andernfalls wird FALSE zurückgegeben.
  
### <a name="seek"></a>Seek
Sucht die aktuelle Position im Stream.

Parameter:  
* **Position**, nach der im Stream gesucht werden soll.


  
### <a name="canread"></a>CanRead
Eine Überprüfung, ob der Stream gelesen werden kann.

  
**Rückgabe**: TRUE, wenn lesbar; andernfalls wird FALSE zurückgegeben.
  
### <a name="canwrite"></a>CanWrite
Eine Überprüfung, ob der Stream geschrieben werden kann.

  
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

