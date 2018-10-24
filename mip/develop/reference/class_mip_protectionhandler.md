---
title: Die Klasse „mip::ProtectionHandler“
description: Referenz zur Klasse „mip::ProtectionHandler“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 6fbae05030f56d3c9e680e6de9c8177a11b2f1e2
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446752"
---
# <a name="class-mipprotectionhandler"></a>mip::ProtectionHandler-Klasse 
Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr<Stream> CreateProtectedStream(const std::shared_ptr<Stream>& backingStream, int64_t contentStartPosition, int64_t contentSize)  |  Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.
 public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Verschlüsselt einen Puffer.
 public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Entschlüsselt einen Puffer.
 public int64_t GetProtectedContentLength(int64_t unprotectedLength, bool includesFinalBlock)  |  Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.
 public int64_t GetBlockSize()  |  Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.
public std::vector<std::string> GetRights() const  |  Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem [ProtectionHandler](class_mip_protectionhandler.md) zugeordnet sind.
 public bool AccessCheck(const std::string& right) const  |  Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.
 public const std::string GetIssuedTo()  |  Ruft den mit dem Schutzhandler verknüpften Benutzer ab.
 public const std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
 public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist
public std::shared_ptr<ProtectionDescriptor> GetProtectionDescriptor()  |  Ruft Schutzdetails ab.
 public const std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
 public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt
 public bool IsAuditedExtractAllowed()  |  Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.
public const std::vector<uint8_t> GetSerializedPublishingLicense()  |  Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.
  
## <a name="members"></a>Member
  
### <a name="stream"></a>Stream
Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.

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


* **isFinal**: Information, ob der Eingabepuffer die letzten Klartextbytes enthält



  
**Rückgabe**: Tatsächliche Größe (in Bytes) des verschlüsselten Inhalts
  
### <a name="decryptbuffer"></a>DecryptBuffer
Entschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: relative Position von „inputBuffer“ vom Anfang des verschlüsselten Inhalts 


* **inputBuffer**: Puffer für verschlüsselte Inhalte, die entschlüsselt werden sollen 


* **inputBufferSize**: Größe (in Bytes) des Eingabepuffers 


* **outputBuffer**: Puffer, in den der entschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Bytes) des Ausgabepuffers 


* **isFinal**: Information, ob der Eingabepuffer die letzten verschlüsselten Bytes enthält



  
**Rückgabe**: Tatsächliche Größe (in Bytes) des entschlüsselten Inhalts
  
### <a name="getprotectedcontentlength"></a>GetProtectedContentLength
Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.

Parameter:  
* **unprotectedLength:** Größe (in Bytes) des nicht geschützten Inhalts 


* **includesFinalBlock:** beschreibt, ob der betreffende Inhalt den abschließenden Block enthält. Im Verschlüsselungsmodus CBC4k haben beispielsweise nicht abschließend geschützte Blocks die gleiche Größe wie ungeschützte Blocks. Allerdings sind abschließend geschützte Blocks größer als deren ungeschützte Gegenstücke.



  
**Rückgabe**: Größe (in Bytes) des geschützten Inhalts
  
### <a name="getblocksize"></a>GetBlockSize
Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.

  
**Rückgabe**: Blockgröße (in Bytes)
  
### <a name="getrights"></a>GetRights
Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem [ProtectionHandler](class_mip_protectionhandler.md) zugeordnet sind.

  
**Rückgabe:** die dem Benutzer erteilten Rechte
  
### <a name="accesscheck"></a>AccessCheck
Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.

Parameter:  
* **right**: Zu prüfendes Recht



  
**Rückgabe:** Angabe, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt
  
### <a name="getissuedto"></a>GetIssuedTo
Ruft den mit dem Schutzhandler verknüpften Benutzer ab.

  
**Rückgabe**: Benutzer, der der Schutzhandler zugeordnet ist
  
### <a name="getowner"></a>GetOwner
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab

  
**Rückgabe**: E-Mail-Adresse des Inhaltsbesitzers
  
### <a name="isissuedtoowner"></a>IsIssuedToOwner
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist

  
**Rückgabe:** Angabe, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Ruft Schutzdetails ab.

  
**Rückgabe**: Schutzdetails
  
### <a name="getcontentid"></a>GetContentId
Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.

  
**Rückgabe**: Eindeutiger Inhaltsbezeichner
  
### <a name="doesusedeprecatedalgorithms"></a>DoesUseDeprecatedAlgorithms
Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt

  
**Rückgabe**: Angabe, ob der Schutzhandler veraltete Kryptografiealgorithmen nutzt
  
### <a name="isauditedextractallowed"></a>IsAuditedExtractAllowed
Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.

  
**Rückgabe**: Angabe, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (überwachtes Extrahieren) gewährt oder nicht
  
### <a name="getserializedpublishinglicense"></a>GetSerializedPublishingLicense
Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.

  
**Rückgabe**: serialisierte Veröffentlichungslizenz