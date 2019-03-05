---
title: mip::ProtectionHandler-Klasse
description: Dokumentiert die mip::protectionhandler-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 87ab4b9b040297cc73baf40a274377654ec5df9b
ms.sourcegitcommit: 471b3683367d93f0673c1cf276a15f83572aa80e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2019
ms.locfileid: "57331748"
---
# <a name="class-mipprotectionhandler"></a>mip::ProtectionHandler-Klasse 
Verwaltet schutzbezogene Aktionen für eine bestimmte Schutzkonfiguration.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr\<Stream\> CreateProtectedStream (const Std:: shared_ptr\<Stream\>& BackingStream, int64_t ContentStartPosition, int64_t contentSize)  |  Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.
public int64_t EncryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Verschlüsselt einen Puffer.
public int64_t DecryptBuffer(int64_t offsetFromStart, const uint8_t* inputBuffer, int64_t inputBufferSize, uint8_t* outputBuffer, int64_t outputBufferSize, bool isFinal)  |  Entschlüsselt einen Puffer.
public int64_t GetProtectedContentLength(int64_t unprotectedLength, bool includesFinalBlock)  |  Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.
public int64_t GetBlockSize()  |  Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.
Public Std:: vector\<Std:: String\> GetRights() const  |  Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem [ProtectionHandler](class_mip_protectionhandler.md) zugeordnet sind.
public bool AccessCheck(const std::string& right) const  |  Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.
public const std::string GetIssuedTo()  |  Ruft den mit dem Schutzhandler verknüpften Benutzer ab.
public const std::string GetOwner()  |  Ruft die E-Mail-Adresse des Inhaltsbesitzers ab
public bool IsIssuedToOwner()  |  Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist
Public Std:: shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor()  |  Ruft Schutzdetails ab.
public const std::string GetContentId()  |  Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.
public bool DoesUseDeprecatedAlgorithms()  |  Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt
public bool IsAuditedExtractAllowed()  |  Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.
Public const Std:: vector\<uint8_t\> GetSerializedPublishingLicense()  |  Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.
Public const Std:: vector\<uint8_t\> GetSerializedProtectionInfo()  |  Ruft Informationen zu Protection ab.
  
## <a name="members"></a>Member
  
### <a name="createprotectedstream-function"></a>CreateProtectedStream-Funktion
Erstellt einen geschützten Stream für die Verschlüsselung bzw. Entschlüsselung von Inhalten.

Parameter:  
* **backingStream**: Sichern der Stream, aus dem Lese-/Schreibzugriff 


* **contentStartPosition**: Startposition (in Byte) in den sicherungsdatenstrom geschützter Inhalte beginnt 


* **contentSize**: Größe (in Bytes) von geschützten Inhalten in Stream sichern



  
**Gibt**: Geschützten Datenstroms
  
### <a name="encryptbuffer-function"></a>EncryptBuffer-Funktion
Verschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: Relative Position der InputBuffer aus am Anfang des Klartext-Inhalts 


* **inputBuffer**: Der Puffer Klartext-Inhalte, die verschlüsselt werden 


* **inputBufferSize**: Größe (in Bytes) der Eingabepuffer 


* **outputBuffer**: Puffer, die in den verschlüsselter Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Byte) des Ausgabepuffers 


* **isFinal**: Wenn der Eingabepuffer enthält die endgültigen Klartext-Bytes oder nicht



  
**Gibt**: Tatsächliche Größe (in Bytes) des verschlüsselten Inhalts
  
### <a name="decryptbuffer-function"></a>DecryptBuffer-Funktion
Entschlüsselt einen Puffer.

Parameter:  
* **offsetFromStart**: Relative Position der InputBuffer aus am Anfang des verschlüsselten Inhalts 


* **inputBuffer**: Puffer mit den verschlüsselten Inhalt, der entschlüsselt werden 


* **inputBufferSize**: Größe (in Bytes) der Eingabepuffer 


* **outputBuffer**: Puffer, die in der entschlüsselte Inhalt kopiert wird 


* **outputBufferSize**: Größe (in Byte) des Ausgabepuffers 


* **isFinal**: Wenn der Eingabepuffer enthält die verschlüsselte schlussbytes oder nicht



  
**Gibt**: Tatsächliche Größe (in Bytes) der entschlüsselte Inhalt
  
### <a name="getprotectedcontentlength-function"></a>GetProtectedContentLength-Funktion
Berechnet die Größe (in Byte) des Inhalts, wenn dieser mit diesem [ProtectionHandler](class_mip_protectionhandler.md) verschlüsselt werden würde.

Parameter:  
* **unprotectedLength**: Größe (in Bytes) von nicht geschützten Inhalt 


* **includesFinalBlock**: Beschreibt, die nicht geschützte Inhalte, die betreffende den abschließende Block enthält oder nicht. Im Verschlüsselungsmodus CBC4k haben beispielsweise nicht abschließend geschützte Blocks die gleiche Größe wie ungeschützte Blocks. Allerdings sind abschließend geschützte Blocks größer als deren ungeschützte Gegenstücke.



  
**Gibt**: Größe (in Bytes) von geschütztem Inhalt
  
### <a name="getblocksize-function"></a>GetBlockSize-Funktion
Ruft die Blockgröße (in Byte) für den Verschlüsselungsmodus ab, der von diesem [ProtectionHandler](class_mip_protectionhandler.md) verwendet wird.

  
**Gibt**: Blockgröße (in Byte)
  
### <a name="getrights-function"></a>GetRights-Funktion
Ruft die Rechte ab, die dem Benutzer bzw. der Identität erteilt werden, die diesem [ProtectionHandler](class_mip_protectionhandler.md) zugeordnet sind.

  
**Gibt**: Dem Benutzer gewährten Rechte
  
### <a name="accesscheck-function"></a>AccessCheck-Funktion
Überprüft, ob der Schutzhandler Benutzerzugriff auf das angegebene Recht gewährt.

Parameter:  
* **right**: Zu prüfendes Recht



  
**Gibt**: Wenn Benutzer den Zugriff auf den angegebenen nach rechts oder nicht Protection Handler gewährt
  
### <a name="getissuedto-function"></a>GetIssuedTo-Funktion
Ruft den mit dem Schutzhandler verknüpften Benutzer ab.

  
**Gibt**: Benutzer mit Schutz-Handler verbunden
  
### <a name="getowner-function"></a>GetOwner-Funktion
Ruft die E-Mail-Adresse des Inhaltsbesitzers ab

  
**Gibt**: E-Mail-Adresse des Inhaltsbesitzers
  
### <a name="isissuedtoowner-function"></a>IsIssuedToOwner-Funktion
Ruft ab, ob der aktuelle Benutzer der Inhaltsbesitzer ist

  
**Gibt**: Wenn der aktuelle Benutzer der Inhaltsbesitzer oder nicht ist
  
### <a name="getprotectiondescriptor-function"></a>GetProtectionDescriptor-Funktion
Ruft Schutzdetails ab.

  
**Gibt**: Schutzdetails
  
### <a name="getcontentid-function"></a>GetContentId-Funktion
Ruft den eindeutigen Bezeichner für das Dokument bzw. den Inhalt ab.

  
**Gibt**: Eindeutiger Inhaltsbezeichner
  
### <a name="doesusedeprecatedalgorithms-function"></a>DoesUseDeprecatedAlgorithms-Funktion
Ruft ab, ob ein Schutzhandler veraltete Kryptografiealgorithmen für die Abwärtskompatibilität nutzt

  
**Gibt**: Wenn der Schutz-Ereignishandler verwendet veraltete Kryptografiealgorithmen oder nicht
  
### <a name="isauditedextractallowed-function"></a>IsAuditedExtractAllowed-Funktion
Ruft ab, ob ein Schutzhandler dem Benutzer das Recht „audited extract“ (Überwachtes Extrahieren) gewährt oder nicht.

  
**Gibt**: Wenn Schutz Handler Benutzer gewährt "Extract nach rechts oder nicht überwacht"
  
### <a name="getserializedpublishinglicense-function"></a>GetSerializedPublishingLicense-Funktion
Serialisiert [ProtectionHandler](class_mip_protectionhandler.md) in eine Veröffentlichungslizenz.

  
**Gibt**: Serialisierte Veröffentlichungslizenz
  
### <a name="getserializedprotectioninfo-function"></a>GetSerializedProtectionInfo-Funktion
Ruft Informationen zu Protection ab.

  
**Gibt**: Serialisierte Schutzdaten
