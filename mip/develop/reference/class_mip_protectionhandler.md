---
title: Klassen Schutz Handler
description: 'Dokumentiert die schutzhandler:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: d70e32793ede4a1184672f3f8755112766ba571b
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98214608"
---
# <a name="class-protectionhandler"></a>Klassen Schutz Handler 
Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public std::shared_ptr\<Stream\> CreateProtectedStream(const std::shared_ptr\<Stream\>& backingStream, int64_t contentStartPosition, int64_t contentSize)  |  Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.
public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Verschlüsselt einen Puffer.
public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Entschlüsselt einen Puffer.
public int64_t GetProtectedContentLength(int64_t unprotectedLength, bool includesFinalBlock)  |  Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem ProtectionHandler verschlüsselt werden würde.
public int64_t GetBlockSize()  |  Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem ProtectionHandler verwendet wird.
Public Std:: Vector \<std::string\> GetRights () Konstanten  |  Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem ProtectionHandler zugeordnet sind.
public bool AccessCheck(const std::string& right) const  |  Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.
public const std::string GetIssuedTo()  |  Ruft den mit dem Schutzhandler verknüpften Benutzer ab.
public const std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist
public std::shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor()  |  Ruft Schutzdetails ab.
public const std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt
public bool IsAuditedExtractAllowed()  |  Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.
Public Konstanten Std:: Vector \<uint8_t\>& getserializedpublishinglicense () Konstanten  |  Serialisiert ProtectionHandler in eine Veröffentlichungslizenz.
Public Konstanten Std:: Vector \<uint8_t\>& getserializedprelicense (prelicenzformat) Konstanten  |  Vorab Lizenz erhalten.
öffentlicher chiffrimode getciphermode () konstant  |  Ruft den Verschlüsselungs Modus des Schutz Handlers ab.
Enumeration prelicenenformat  |  Prälizenzierungs Format.
  
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
Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem ProtectionHandler verschlüsselt werden würde.

Parameter:  
* **unprotectedLength:** Größe (in Bytes) des nicht geschützten Inhalts 


* **includesFinalBlock:** beschreibt, ob der betreffende Inhalt den abschließenden Block enthält. Im Verschlüsselungsmodus CBC4k haben beispielsweise nicht abschließend geschützte Blocks die gleiche Größe wie ungeschützte Blocks. Allerdings sind abschließend geschützte Blocks größer als deren ungeschützte Gegenstücke.



  
**Rückgabe**: Größe (in Bytes) des geschützten Inhalts
  
### <a name="getblocksize-function"></a>Getblocksize-Funktion
Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem ProtectionHandler verwendet wird.

  
**Rückgabe**: Blockgröße (in Bytes)
  
### <a name="getrights-function"></a>GetRights-Funktion
Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem ProtectionHandler zugeordnet sind.

  
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
Serialisiert ProtectionHandler in eine Veröffentlichungslizenz.

  
**Rückgabe**: serialisierte Veröffentlichungslizenz
  
### <a name="getserializedprelicense-function"></a>Getserializedprelicense-Funktion
Vorab Lizenz erhalten.

Parameter:  
* **Format**: Prälizenzierungs Format



  
**Gibt Folgendes zurück**: die serialisierte Pre-License-Pre-License-Funktion ermöglicht es einem Benutzer, Inhalte sofort zu nutzen, ohne einen zusätzlichen http-aufzurufen. Der Schutz Handler muss mit einem Schutz Handler erstellt worden sein::P ublishingsettings:: setprelicenseuseremail-Wert oder andernfalls wird ein leerer Vektor zurückgegeben.
  
### <a name="getciphermode-function"></a>Getciphermode-Funktion
Ruft den Verschlüsselungs Modus des Schutz Handlers ab.

  
**Gibt Folgendes zurück**: der Chiffre Modus
  
### <a name="prelicenseformat-enum"></a>Prelicenenformat-Enumeration

Prälizenzierungs Format.

 Werte                         | Beschreibungen                                
--------------------------------|---------------------------------------------
Xml            | Von msipc verwendetes XML/SOAP-Legacy Format
Json            | Vom MIP SDK und RMS SDK verwendetes JSON/Rest-Format
