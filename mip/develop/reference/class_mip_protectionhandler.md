---
title: mip::ProtectionHandler-Klasse
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: 28250cc27adeb18c2ca723084267341798f5efa7
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057585"
---
# <a name="class-mipprotectionhandler"></a>mip::ProtectionHandler-Klasse 
Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<Stream\> "upateprotectedstream" (konstant Std::\<shared_ptr\>Stream & backingstream, int64_t contentstartposition, int64_t contentsize)  |  Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.
public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Verschlüsselt einen Puffer.
public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Entschlüsselt einen Puffer.
public int64_t GetProtectedContentLength(int64_t unprotectedLength, bool includesFinalBlock)  |  Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.
public int64_t GetBlockSize()  |  Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.
Public Std:: Vector\<Std:: String\> GetRights () Konstanten  |  Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem [ProtectionHandler](class_mip_protectionhandler.md) zugeordnet sind.
public bool AccessCheck(const std::string& right) const  |  Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.
public const std::string GetIssuedTo()  |  Ruft den mit dem Schutzhandler verknüpften Benutzer ab.
public const std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor ()  |  Ruft Schutzdetails ab.
public const std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt
public bool IsAuditedExtractAllowed()  |  Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.
Public Konstanten Std:: Vector\<uint8_t\> getserializedpublishinglicense ()  |  Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.
  
## <a name="members"></a>Member
  
### <a name="createprotectedstream-function"></a>Funktion "deateprotectedstream"
Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.

Parameter:  
* **backingStream**: Sicherungsdaten Strom, aus dem gelesen/geschrieben werden soll 


* **contentStartPosition**: Anfangsposition (in Bytes) innerhalb des Unterstützungs Datenstroms, in dem geschützter Inhalt beginnt 


* **contentSize**: Größe (in Bytes) geschützter Inhalte innerhalb des Sicherungsdaten Stroms



  
**Gibt Folgendes zurück**: Geschützter Datenstrom
  
### <a name="encryptbuffer-function"></a>Verschlüsseltbuffer-Funktion
Verschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: Relative Position von Input Buffer vom Anfang des Klartext-Inhalts. 


* **Input Buffer**: Puffer von Klartext-Inhalt, der verschlüsselt wird. 


* **inputBufferSize**: Größe (in Bytes) des Eingabe Puffers 


* **OUTPUTBUFFER**: Puffer, in den verschlüsselter Inhalt kopiert wird 


* **outputBufferSize**: Größe des Ausgabepuffers (in Bytes) 


* **isFinal**: Wenn der Eingabepuffer die endgültigen Klartext-Bytes enthält oder nicht.



  
**Gibt Folgendes zurück**: Tatsächliche Größe (in Bytes) von verschlüsseltem Inhalt
  
### <a name="decryptbuffer-function"></a>Decryptbuffer-Funktion
Entschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: Relative Position von Input Buffer vom Anfang des verschlüsselten Inhalts 


* **Input Buffer**: Puffer verschlüsselter Inhalte, die entschlüsselt werden 


* **inputBufferSize**: Größe (in Bytes) des Eingabe Puffers 


* **OUTPUTBUFFER**: Puffer, in den der entschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe des Ausgabepuffers (in Bytes) 


* **isFinal**: Wenn der Eingabepuffer die endgültigen verschlüsselten Bytes enthält oder nicht.



  
**Gibt Folgendes zurück**: Tatsächliche Größe (in Bytes) von entschlüsselten Inhalten
  
### <a name="getprotectedcontentlength-function"></a>Getprotectedcontentlength-Funktion
Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.

Parameter:  
* **unprotectedlength**: Größe von ungeschütztem Inhalt (in Bytes) 


* **includesFinalBlock**: Beschreibt, ob der fragliche ungeschützte Inhalt den Endblock enthält oder nicht. Im Verschlüsselungsmodus CBC4k haben beispielsweise nicht abschließend geschützte Blocks die gleiche Größe wie ungeschützte Blocks. Allerdings sind abschließend geschützte Blocks größer als deren ungeschützte Gegenstücke.



  
**Gibt Folgendes zurück**: Größe (in Bytes) geschützter Inhalte
  
### <a name="getblocksize-function"></a>Getblocksize-Funktion
Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.

  
**Gibt Folgendes zurück**: Block Größe (in Bytes)
  
### <a name="getrights-function"></a>GetRights-Funktion
Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem [ProtectionHandler](class_mip_protectionhandler.md) zugeordnet sind.

  
**Gibt Folgendes zurück**: Dem Benutzer gewährte Rechte
  
### <a name="accesscheck-function"></a>Access Check-Funktion
Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.

Parameter:  
* **Rechts**: Recht zum Überprüfen



  
**Gibt Folgendes zurück**: , Wenn der Schutz Handler den Benutzer Zugriff auf das angegebene Recht gewährt oder nicht.
  
### <a name="getissuedto-function"></a>GetIssuedTo-Funktion
Ruft den mit dem Schutzhandler verknüpften Benutzer ab.

  
**Gibt Folgendes zurück**: Dem Schutz Handler zugeordneter Benutzer
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab

  
**Gibt Folgendes zurück**: E-Mail-Adresse des Inhaltsbesitzers
  
### <a name="isissuedtoowner-function"></a>Isissuedtoowner-Funktion
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist

  
**Gibt Folgendes zurück**: , Wenn der aktuelle Benutzer der Inhalts Besitzer ist oder nicht.
  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
Ruft Schutzdetails ab.

  
**Gibt Folgendes zurück**: Details zum Schutz
  
### <a name="getcontentid-function"></a>GetContentID-Funktion
Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.

  
**Gibt Folgendes zurück**: Eindeutiger Inhaltsbezeichner
  
### <a name="doesusedeprecatedalgorithms-function"></a>Doesusedeprekataedalgorithmen-Funktion
Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt

  
**Gibt Folgendes zurück**: Wenn der Schutz Handler als veraltet markierte Kryptografiealgorithmen verwendet
  
### <a name="isauditedextractallowed-function"></a>Isauditedextractallowed-Funktion
Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.

  
**Gibt Folgendes zurück**: Wenn der Schutz Handler den Benutzer das Recht "überwacht extrahieren" gewährt oder nicht.
  
### <a name="getserializedpublishinglicense-function"></a>Getserializedpublishinglicense-Funktion
Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.

  
**Gibt Folgendes zurück**: Lizenz für die serialisierte Veröffentlichung