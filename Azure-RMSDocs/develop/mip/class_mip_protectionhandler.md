# <a name="class-mipprotectionhandler"></a>mip::ProtectionHandler-Klasse 
Führt schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration (d.h. Benutzer, Rechte, Rollen usw.) aus.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr<Stream> CreateProtectedStream(const std::shared_ptr<Stream>& backingStream, uint64_t contentStartPosition, uint64_t contentSize)  |  Erstellt einen geschützten Datenstrom für die Verschlüsselung bzw. Entschlüsselung von Inhalten.
 public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Verschlüsselt einen Puffer.
 public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Entschlüsselt einen Puffer.
 public uint64_t GetProtectedContentLength(uint64_t size)  |  Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.
 public uint64_t GetBlockSize()  |  Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.
 public bool AccessCheck(const std::string& right) const  |  Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.
 public const std::string GetIssuedTo()  |  Ruft den mit dem Schutzhandler verknüpften Benutzer ab.
 public const std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
 public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht.
public std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor()  |  Ruft Schutzdetails ab.
 public const std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
 public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt.
 public bool IsAuditedExtractAllowed()  |  Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht.
public const std::vector<uint8_t> GetSerializedPublishingLicense()  |  Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.
  
## <a name="members"></a>Member
  
### <a name="stream"></a>Stream
Erstellt einen geschützten Datenstrom für die Verschlüsselung bzw. Entschlüsselung von Inhalten.

Parameter:  
* **backingStream**: Sicherungsdatenstrom für Lese- und Schreibvorgänge 


* **contentStartPosition**: Startposition (in Bytes) im Sicherungsdatenstrom, an der der geschützte Inhalt beginnt 


* **contentSize**: Größe (in Bytes) des geschützten Inhalts im Sicherungsdatenstrom



  
**Rückgabe**: geschützter Datenstrom
  
### <a name="encryptbuffer"></a>EncryptBuffer
Verschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: relative Position von „inputBuffer“ vom Anfang des Klartextinhalts 


* **inputBuffer**: Puffer für zu verschlüsselnde Klartextinhalte 


* **inputBufferSize**: Größe (in Bytes) des Eingabepuffers 


* **outputBuffer**: Puffer, in den der verschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Bytes) des Ausgabepuffers 


* **isFinal**: Information, ob der Eingabepuffer die letzten Klartextbytes enthält oder nicht



  
**Rückgabe**: Tatsächliche Größe (in Bytes) des verschlüsselten Inhalts
  
### <a name="decryptbuffer"></a>DecryptBuffer
Entschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: relative Position von „inputBuffer“ vom Anfang des verschlüsselten Inhalts 


* **inputBuffer**: Puffer für verschlüsselte Inhalte, die entschlüsselt werden sollen 


* **inputBufferSize**: Größe (in Bytes) des Eingabepuffers 


* **outputBuffer**: Puffer, in den der entschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Bytes) des Ausgabepuffers 


* **isFinal**: Information, ob der Eingabepuffer die letzten verschlüsselten Bytes enthält oder nicht



  
**Rückgabe**: Tatsächliche Größe (in Bytes) des entschlüsselten Inhalts
  
### <a name="getprotectedcontentlength"></a>GetProtectedContentLength
Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.

Parameter:  
* **contentLength**: Größe (in Bytes) des nicht geschützten Inhalts



  
**Rückgabe**: Größe (in Bytes) des geschützten Inhalts
  
### <a name="getblocksize"></a>GetBlockSize
Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.

  
**Rückgabe**: Blockgröße (in Bytes)
  
### <a name="accesscheck"></a>AccessCheck
Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.

Parameter:  
* **right**: Zu prüfendes Recht



  
**Rückgabe**: Information, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt oder nicht
  
### <a name="getissuedto"></a>GetIssuedTo
Ruft den mit dem Schutzhandler verknüpften Benutzer ab.

  
**Rückgabe**: Benutzer, der der Schutzhandler zugeordnet ist
  
### <a name="getowner"></a>GetOwner
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab

  
**Rückgabe**: E-Mail-Adresse des Inhaltsbesitzers
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht.

  
**Rückgabe**: Angabe, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Ruft Schutzdetails ab.

  
**Rückgabe**: Schutzdetails
  
### <a name="getcontentid"></a>GetContentId
Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.

  
**Rückgabe**: Eindeutiger Inhaltsbezeichner
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt.

  
**Rückgabe**: Information, ob der Schutzhandler veraltete Kryptografiealgorithmen nutzt oder nicht
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht.

  
**Rückgabe**: Information, ob ein Schutzhandler dem Benutzer das Recht „überwacht extrahieren“ gewährt oder nicht
  
### <a name="getserializedpublishinglicense"></a>GetSerializedPublishingLicense
Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.

  
**Rückgabe**: serialisierte Veröffentlichungslizenz