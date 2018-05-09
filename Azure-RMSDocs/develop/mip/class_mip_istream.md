# <a name="class-mipistream"></a>mip::IStream-Klasse 
Die Basisschnittstelle für geschützte Streams.
Portiert aus Windows::Storage::Streams::IRandomAccessStream::IRandomAccessStream und Windows::Storage::Streams::FileRandomAccessStream::FileRandomAccessStream. [https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.irandomaccessstream.aspx)[https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.filerandomaccessstream.aspx](https://msdn.microsoft.com/en-us/library/windows/apps/windows.storage.streams.filerandomaccessstream.aspx)
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_future<int64_t> ReadAsync(uint8_t* pbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Liest asynchron einen Datenblock aus dem Stream.
public std::shared_future<int64_t> WriteAsync(const uint8_t* cpbBuffer, int64_t cbBuffer, int64_t cbOffset, std::launch launchType)  |  Schreibt asynchron einen Datenblock in den Stream.
public std::future<bool> FlushAsync(std::launch launchType)  |  Leert asynchron den Puffer für den Ausgabestream.
public int64_t Read(uint8_t* pbBuffer, int64_t cbBuffer)  |  Liest synchron einen Datenblock aus dem Stream.
public int64_t Write(const uint8_t* cpbBuffer, int64_t cbBuffer)  |  Schreibt synchron einen Datenblock in den Stream.
public bool Flush()  |  Leert synchron den Puffer für den Ausgabestream.
public SharedStream Clone()  |  Klont den Stream.
public void Seek(uint64_t u64Position)  |  Sucht eine Position im Stream.
public bool CanRead() const  |  Ruft ab, ob ein Stream gelesen werden kann.
public bool CanWrite() const  |  Ruft ab, ob in den Stream geschrieben werden kann.
public uint64_t Position()  |  Ruft die aktuelle Position des Streams vom Anfang ab (in Bytes)
public uint64_t Size()  |  Ruft die Größe des Streams ab (in Bytes)
public void Size(uint64_t u64Value)  |  Legt die Größe des Streams fest (in Bytes)
public inline virtual std::vector<uint8_t> Read(uint64_t u64size)  |  Liest synchron einen Datenblock aus dem Stream.
  
## <a name="members"></a>Member
  
### <a name="readasync"></a>ReadAsync
Liest asynchron einen Datenblock aus dem Stream.
  
#### <a name="parameters"></a>Parameter
* pbBuffer Puffer, in den der Stream gelesen werden soll 
* cbBuffer Die Puffergröße 
* cbOffset: Offset vom Beginn des Eingabestreams, bei dem mit dem Lesen begonnen werden soll 
* launchType asynchroner Starttyp
  
#### <a name="returns"></a>Rückgabe
Async-Funktion „future“: enthält die tatsächliche Anzahl der gelesenen Bytes und stellt sicher, dass ein Puffer vorhanden ist, bis das Ergebnis von std::future abgerufen wird
  
### <a name="writeasync"></a>WriteAsync
Schreibt asynchron einen Datenblock in den Stream.
  
#### <a name="parameters"></a>Parameter
* cpbBuffer Puffer für zu schreibende Daten 
* cbBuffer Die Puffergröße 
* cbOffset: Offset vom Beginn des Ausgabestreams, bei dem mit dem Schreiben begonnen werden soll 
* launchType asynchroner Starttyp
  
#### <a name="returns"></a>Rückgabe
Async-Funktion „future“: enthält die tatsächliche Anzahl der geschriebenen Bytes und stellt sicher, dass ein Puffer vorhanden ist, bis das Ergebnis von std::future abgerufen wird
  
### <a name="flushasync"></a>FlushAsync
Leert asynchron den Puffer für den Ausgabestream.
  
#### <a name="parameters"></a>Parameter
* launchType asynchroner Starttyp
  
#### <a name="returns"></a>Rückgabe
Async-Funktion „future“: gibt an, ob die Leerung erfolgreich war
  
### <a name="read"></a>Überwachungsdaten
Liest synchron einen Datenblock aus dem Stream.
  
#### <a name="parameters"></a>Parameter
* pbBuffer Puffer, in den der Stream gelesen werden soll 
* cbBuffer Die Puffergröße
  
#### <a name="returns"></a>Rückgabe
Die tatsächliche Anzahl der gelesenen Bytes
  
### <a name="write"></a>Überwachungsdaten
Schreibt synchron einen Datenblock in den Stream.
  
#### <a name="parameters"></a>Parameter
* cpbBuffer Puffer für zu schreibende Daten 
* cbBuffer Die Puffergröße
  
#### <a name="returns"></a>Rückgabe
Die tatsächliche Anzahl der geschriebenen Bytes
  
### <a name="flush"></a>Leerung
Leert synchron den Puffer für den Ausgabestream.
  
#### <a name="returns"></a>Rückgabe
Angabe, ob die Leerung erfolgreich war
  
### <a name="sharedstream"></a>SharedStream
Klont den Stream.
  
#### <a name="returns"></a>Rückgabe
Der geklonte Stream
  
### <a name="seek"></a>Seek
Sucht eine Position im Stream.
  
#### <a name="parameters"></a>Parameter
* u64Position: Byte-Offset vom Beginn des Streams
  
### <a name="canread"></a>CanRead
Ruft ab, ob ein Stream gelesen werden kann.
  
#### <a name="returns"></a>Rückgabe
Angabe, ob der Stream gelesen werden kann
  
### <a name="canwrite"></a>CanWrite
Ruft ab, ob in den Stream geschrieben werden kann.
  
#### <a name="returns"></a>Rückgabe
Angabe, ob ein Stream geschrieben werden kann
  
### <a name="position"></a>Position
Ruft die aktuelle Position des Streams vom Anfang ab (in Bytes)
  
#### <a name="returns"></a>Rückgabe
Die aktuelle Position des Streams von Anfang an (in Bytes)
  
### <a name="size"></a>Size
Ruft die Größe des Streams ab (in Bytes)
  
#### <a name="returns"></a>Rückgabe
Die Größe des Streams (in Bytes)
  
### <a name="size"></a>Size
Legt die Größe des Streams fest (in Bytes)
  
#### <a name="parameters"></a>Parameter
* u64Value die Größe des Streams (in Bytes)
  
### <a name="read"></a>Überwachungsdaten
Liest synchron einen Datenblock aus dem Stream.
  
#### <a name="parameters"></a>Parameter
* u64size die Größe der zu lesenden Daten (in Bytes)
  
#### <a name="returns"></a>Rückgabe
Vektor der tatsächlich gelesenen Daten