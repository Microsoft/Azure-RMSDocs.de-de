# <a name="class-mipcustomprotectedstream"></a>mip::CustomProtectedStream-Klasse 
Umschließt einen Stream, um beim Lesen und Schreiben transparente Verschlüsselung und Entschlüsselung zu gewährleisten.
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_future< int64_t > ReadAsync | Liest asynchron einen Datenblock aus dem Stream.
public std::shared_future< int64_t > WriteAsync | Schreibt asynchron einen Datenblock in den Stream.
public std::future< bool > FlushAsync | Leert asynchron den Puffer für den Ausgabestream.
public int64_t Read | Liest synchron einen Datenblock aus dem Stream.
public inline virtual std::vector< uint8_t > Read | Liest synchron einen Datenblock aus dem Stream.
public int64_t Write | Schreibt synchron einen Datenblock in den Stream.
public bool Flush | Leert synchron den Puffer für den Ausgabestream.
public SharedStream Clone | Klont den Stream.
public void Seek | Sucht eine Position im Stream.
public bool CanRead | Ruft ab, ob ein Stream gelesen werden kann.
public bool CanWrite | Ruft ab, ob in den Stream geschrieben werden kann.
public uint64_t Position | Ruft die aktuelle Position des Streams vom Anfang ab (in Bytes)
public uint64_t Size | Ruft die Größe des Streams ab (in Bytes)
public void Size | Legt die Größe des Streams fest (in Bytes)
## <a name="members"></a>Member
### <a name="readasync"></a>ReadAsync
Liest asynchron einen Datenblock aus dem Stream.
#### <a name="parameters"></a>Parameter
* PbBuffer: Puffer, in den der Stream gelesen werden soll 
* cbBuffer: Die Puffergröße 
* cbOffset: Offset vom Beginn des Eingabestreams, bei dem mit dem Lesen begonnen werden soll 
* launchType: asynchroner Starttyp
#### <a name="returns"></a>Rückgabe
Async-Funktion „future“: enthält die tatsächliche Anzahl der gelesenen Bytes und stellt sicher, dass ein Puffer vorhanden ist, bis das Ergebnis von std::future abgerufen wird
### <a name="writeasync"></a>WriteAsync
Schreibt asynchron einen Datenblock in den Stream.
#### <a name="parameters"></a>Parameter
* CpbBuffer: Puffer für zu schreibende Daten 
* cbBuffer: Die Puffergröße 
* cbOffset: Offset vom Beginn des Ausgabestreams, bei dem mit dem Schreiben begonnen werden soll 
* launchType: asynchroner Starttyp
#### <a name="returns"></a>Rückgabe
Async-Funktion „future“: enthält die tatsächliche Anzahl der geschriebenen Bytes und stellt sicher, dass ein Puffer vorhanden ist, bis das Ergebnis von std::future abgerufen wird
### <a name="flushasync"></a>FlushAsync
Leert asynchron den Puffer für den Ausgabestream.
#### <a name="parameters"></a>Parameter
* launchType: asynchroner Starttyp
#### <a name="returns"></a>Rückgabe
Async-Funktion „future“: gibt an, ob die Leerung erfolgreich war
### <a name="read"></a>Überwachungsdaten
Liest synchron einen Datenblock aus dem Stream.
#### <a name="parameters"></a>Parameter
* PbBuffer: Puffer, in den der Stream gelesen werden soll 
* cbBuffer: Die Puffergröße
#### <a name="returns"></a>Rückgabe
Die tatsächliche Anzahl der gelesenen Bytes
### <a name="read"></a>Überwachungsdaten
Liest synchron einen Datenblock aus dem Stream.
#### <a name="parameters"></a>Parameter
* u64size: die Größe der zu lesenden Daten (in Bytes)
#### <a name="returns"></a>Rückgabe
Vektor der tatsächlich gelesenen Daten
### <a name="write"></a>Überwachungsdaten
Schreibt synchron einen Datenblock in den Stream.
#### <a name="parameters"></a>Parameter
* CpbBuffer: Puffer für zu schreibende Daten 
* cbBuffer: Die Puffergröße
#### <a name="returns"></a>Rückgabe
Die tatsächliche Anzahl der geschriebenen Bytes
### <a name="flush"></a>Leerung
Leert synchron den Puffer für den Ausgabestream.
#### <a name="returns"></a>Rückgabe
Gibt an, ob die Leerung erfolgreich war
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
Angabe, ob in einen Stream geschrieben werden kann
### <a name="position"></a>Position
Ruft die aktuelle Position des Streams vom Anfang ab (in Bytes)
#### <a name="returns"></a>Rückgabe
Die aktuelle Position des Streams vom Anfang ab (in Bytes)
### <a name="size"></a>Size
Ruft die Größe des Streams ab (in Bytes)
#### <a name="returns"></a>Rückgabe
Die Größe des Streams (in Bytes)
### <a name="size"></a>Size
Legt die Größe des Streams fest (in Bytes)
#### <a name="parameters"></a>Parameter
* u64Value: die Größe des Streams (in Bytes)