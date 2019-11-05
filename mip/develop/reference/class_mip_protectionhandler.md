---
title: mip::ProtectionHandler-Klasse
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 6b5468986d62c01d2d3f0b55a57946d5fa06bab3
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560114"
---
# <a name="class-mipprotectionhandler"></a>mip::ProtectionHandler-Klasse 
Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<Stream\>-Stream-Datenstrom (Konstanten Std:: shared_ptr\<Stream\>& backingstream, int64_t contentstartposition, int64_t contentsize)  |  Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.
public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Verschlüsselt einen Puffer.
public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Entschlüsselt einen Puffer.
public int64_t GetProtectedContentLength(int64_t unprotectedLength, bool includesFinalBlock)  |  Berechnet die Größe des Inhalts (in Bytes), wenn er mit diesem Schutz Handler verschlüsselt werden soll.
public int64_t GetBlockSize()  |  Ruft die Blockgröße (in Bytes) für den Verschlüsselungs Modus ab, der von diesem Schutz Handler verwendet wird.
Public Std:: Vector\<Std:: String\> GetRights () Konstanten  |  Ruft die Rechte ab, die dem Benutzer/der Identität gewährt werden, der diesem Schutz Handler zugeordnet ist.
public bool AccessCheck(const std::string& right) const  |  Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.
public const std::string GetIssuedTo()  |  Ruft den mit dem Schutzhandler verknüpften Benutzer ab.
public const std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor ()  |  Ruft Schutzdetails ab.
public const std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt
public bool IsAuditedExtractAllowed()  |  Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.
Public Konstanten Std:: Vector\<uint8_t\> getserializedpublishinglicense ()  |  Serialisieren des Schutz Handlers in eine Veröffentlichungs Lizenz (PL)
  
## <a name="members"></a>Member
  
### <a name="createprotectedstream-function"></a>Funktion "deateprotectedstream"
Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.

Parameter:  
* **backingStream**: Sicherungsdatenstrom für Lese- und Schreibvorgänge 


* **contentStartPosition**: Startposition (in Bytes) im Sicherungsdatenstrom, an der der geschützte Inhalt beginnt 


* **contentSize**: Größe (in Bytes) des geschützten Inhalts im Sicherungsdatenstrom



  
**Rückgabe**: geschützter Datenstrom
  
### <a name="encryptbuffer-function"></a>Verschlüsseltbuffer-Funktion
Verschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: relative Position von „inputBuffer“ vom Anfang des Klartextinhalts 


* **inputBuffer**: Puffer für zu verschlüsselnde Klartextinhalte 


* **inputBufferSize**: Größe (in Bytes) des Eingabepuffers 


* **outputBuffer**: Puffer, in den der verschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Bytes) des Ausgabepuffers 


* **isFinal**: Information, ob der Eingabepuffer die letzten Klartextbytes enthält



  
**Rückgabe**: Tatsächliche Größe (in Bytes) des verschlüsselten Inhalts
  
### <a name="decryptbuffer-function"></a>Decryptbuffer-Funktion
Entschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: relative Position von „inputBuffer“ vom Anfang des verschlüsselten Inhalts 


* **inputBuffer**: Puffer für verschlüsselte Inhalte, die entschlüsselt werden sollen 


* **inputBufferSize**: Größe (in Bytes) des Eingabepuffers 


* **outputBuffer**: Puffer, in den der entschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Bytes) des Ausgabepuffers 


* **isFinal**: Information, ob der Eingabepuffer die letzten verschlüsselten Bytes enthält



  
**Rückgabe**: Tatsächliche Größe (in Bytes) des entschlüsselten Inhalts
  
### <a name="getprotectedcontentlength-function"></a>Getprotectedcontentlength-Funktion
Berechnet die Größe des Inhalts (in Bytes), wenn er mit diesem Schutz Handler verschlüsselt werden soll.

Parameter:  
* **unprotectedLength:** Größe (in Bytes) des nicht geschützten Inhalts 


* **includesFinalBlock:** beschreibt, ob der betreffende Inhalt den abschließenden Block enthält. Im Verschlüsselungsmodus CBC4k haben beispielsweise nicht abschließend geschützte Blocks die gleiche Größe wie ungeschützte Blocks. Allerdings sind abschließend geschützte Blocks größer als deren ungeschützte Gegenstücke.



  
**Rückgabe**: Größe (in Bytes) des geschützten Inhalts
  
### <a name="getblocksize-function"></a>Getblocksize-Funktion
Ruft die Blockgröße (in Bytes) für den Verschlüsselungs Modus ab, der von diesem Schutz Handler verwendet wird.

  
**Rückgabe**: Blockgröße (in Bytes)
  
### <a name="getrights-function"></a>GetRights-Funktion
Ruft die Rechte ab, die dem Benutzer/der Identität gewährt werden, der diesem Schutz Handler zugeordnet ist.

  
**Rückgabe:** die dem Benutzer erteilten Rechte
  
### <a name="accesscheck-function"></a>Access Check-Funktion
Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.

Parameter:  
* **right**: Zu prüfendes Recht



  
**Rückgabe:** Angabe, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt
  
### <a name="getissuedto-function"></a>GetIssuedTo-Funktion
Ruft den mit dem Schutzhandler verknüpften Benutzer ab.

  
**Rückgabe**: Benutzer, der der Schutzhandler zugeordnet ist
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab

  
**Rückgabe**: E-Mail-Adresse des Inhaltsbesitzers
  
### <a name="isissuedtoowner-function"></a>Isissuedtoowner-Funktion
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist

  
**Rückgabe:** Angabe, ob der aktuelle Benutzer der Inhaltsbesitzer ist oder nicht
  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
Ruft Schutzdetails ab.

  
**Rückgabe**: Schutzdetails
  
### <a name="getcontentid-function"></a>GetContentID-Funktion
Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.

  
**Rückgabe**: Eindeutiger Inhaltsbezeichner
  
### <a name="doesusedeprecatedalgorithms-function"></a>Doesusedeprekataedalgorithmen-Funktion
Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt

  
**Rückgabe**: Angabe, ob der Schutzhandler veraltete Kryptografiealgorithmen nutzt
  
### <a name="isauditedextractallowed-function"></a>Isauditedextractallowed-Funktion
Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.

  
**Rückgabe**: Angabe, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (überwachtes Extrahieren) gewährt oder nicht
  
### <a name="getserializedpublishinglicense-function"></a>Getserializedpublishinglicense-Funktion
Serialisieren des Schutz Handlers in eine Veröffentlichungs Lizenz (PL)

  
**Rückgabe**: serialisierte Veröffentlichungslizenz