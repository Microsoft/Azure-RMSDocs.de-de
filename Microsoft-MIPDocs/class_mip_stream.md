# <a name="class-mipstream"></a>mip::Stream-Klasse 
Eine Klasse, die die Schnittstelle zwischen dem MIP SDK und dem streambasierten Inhalt definiert.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public int64_t Read | Wird in einen Puffer aus dem Stream eingelesen.
public int64_t Write | Wird über einen Puffer in den Stream geschrieben.
public bool Flush | Leert den Stream.
public void Seek | Sucht die aktuelle Position im Stream.
public bool CanRead | Eine Überprüfung, ob der Stream gelesen werden kann.
public bool CanWrite | Eine Überprüfung, ob in den Stream geschrieben werden kann.
public uint64_t Position | Ruft die aktuelle Position im Stream ab.
public uint64_t Size | Ruft den Umfang des Inhalts im Stream ab.
public void Size | Legt die Größe des Streams fest.
public std::shared_ptr< Stream > Clone | Klont den Stream.
## <a name="members"></a>Member
### <a name="read"></a>Überwachungsdaten
Wird in einen Puffer aus dem Stream eingelesen.
#### <a name="parameters"></a>Parameter
* buffer: Zeiger auf einen Puffer 
* bufferLength: Puffergröße. 
#### <a name="returns"></a>Rückgabe
Die Anzahl der tatsächlich gelesenen Bytes.
### <a name="write"></a>Überwachungsdaten
Wird über einen Puffer in den Stream geschrieben.
#### <a name="parameters"></a>Parameter
* buffer: Zeiger auf einen Puffer 
* bufferLength: Puffergröße. 
#### <a name="returns"></a>Rückgabe
Die Anzahl der tatsächlich gelesenen Bytes.
### <a name="flush"></a>Leerung
Leert den Stream.
#### <a name="returns"></a>Rückgabe
TRUE bei erfolgreicher Ausführung; andernfalls wird FALSE zurückgegeben.
### <a name="seek"></a>Seek
Sucht die aktuelle Position im Stream.
#### <a name="parameters"></a>Parameter
* Die Position, nach der im Stream gesucht werden soll.
### <a name="canread"></a>CanRead
Eine Überprüfung, ob der Stream gelesen werden kann.
#### <a name="returns"></a>Rückgabe
TRUE, wenn lesbar; andernfalls wird FALSE zurückgegeben.
### <a name="canwrite"></a>CanWrite
Eine Überprüfung, ob in den Stream geschrieben werden kann.
#### <a name="returns"></a>Rückgabe
TRUE, wenn beschreibbar; andernfalls wird FALSE zurückgegeben.
### <a name="position"></a>Position
Ruft die aktuelle Position im Stream ab.
#### <a name="returns"></a>Rückgabe
Die Position im Stream.
### <a name="size"></a>Size
Ruft den Umfang des Inhalts im Stream ab.
#### <a name="returns"></a>Rückgabe
Die Größe des Streams.
### <a name="size"></a>Size
Legt die Größe des Streams fest.
#### <a name="parameters"></a>Parameter
* Die Größe des Streams.
### <a name="stream"></a>Stream
Klont den Stream.
#### <a name="returns"></a>Rückgabe
Ein neuer Stream.