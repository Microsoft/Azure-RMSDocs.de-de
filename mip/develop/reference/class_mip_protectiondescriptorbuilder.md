---
title: mip::ProtectionDescriptorBuilder-Klasse
description: Dokumentiert die MIP::p rotectiondescriptorbuilder-Klasse des MIP-SDKs (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 5985aad4f4cb9b8276ca855026119507febc9445
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69885109"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>mip::ProtectionDescriptorBuilder-Klasse 
Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MIP_API Std:: shared_ptr\<schutzdescriptor\> Build ()  |  Erstellt einen [ProtectionDescriptor](class_mip_protectiondescriptor.md), dessen Zugriffsberechtigungen von dieser [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)-Instanz definiert werden.
public void SetName(const std::string& value)  |  Legt den Namen für eine Schutzrichtlinie fest.
public void SetDescription(const std::string& value)  |  Legt die Beschreibung der Schutzrichtlinie fest.
öffentliches void setcontentvaliduntil (Konstante Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\>& Wert)  |  Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.
public void SetAllowOfflineAccess(bool value)  |  Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.
public void SetReferrer(const std::string& uri)  |  Legt die Referreradresse der Schutzrichtlinie fest.
public void "stencryptedappdata" (Konstanten Std::\<Map Std:: String, Std::\>String & Wert)  |  Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
öffentliches void setsignetdappdata (Konstanten Std:: map\<Std:: String, Std:: String\>& Wert)  |  Legt anwendungsspezifische Daten fest, die signiert werden sollten.
public virtual ~ProtectionDescriptorBuilder()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="build-function"></a>Build-Funktion
Erstellt einen [ProtectionDescriptor](class_mip_protectiondescriptor.md), dessen Zugriffsberechtigungen von dieser [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)-Instanz definiert werden.

  
**Gibt Folgendes zurück**: Neue [schutzdeskriptorinstanz](class_mip_protectiondescriptor.md)
  
### <a name="setname-function"></a>SetName-Funktion
Legt den Namen für eine Schutzrichtlinie fest.

Parameter:  
* **Wert**: Name der Schutzrichtlinie


  
### <a name="setdescription-function"></a>SetDescription-Funktion
Legt die Beschreibung der Schutzrichtlinie fest.

Parameter:  
* **Wert**: Richtlinienbeschreibung


  
### <a name="setcontentvaliduntil-function"></a>Setcontentvaliduntil-Funktion
Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.

Parameter:  
* **Wert**: Ablaufzeit der Richtlinie


  
### <a name="setallowofflineaccess-function"></a>"Setlowofflineaccess"-Funktion
Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.

Parameter:  
* **Wert**: Wenn die Richtlinie Offline Zugriff auf Inhalte zulässt oder nicht


  
### <a name="setreferrer-function"></a>"Streferrer"-Funktion
Legt die Referreradresse der Schutzrichtlinie fest.

Parameter:  
* **uri**: Referenrer Adresse der Richtlinie


Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Beschaffung der Schutzrichtlinie fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="setencryptedappdata-function"></a>Stencryptedappdata-Funktion
Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.

Parameter:  
* **Wert**: App-spezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom RMS-Dienst verschlüsselt wird. Diese verschlüsselten Daten sind durch „SetSignedAppData“ unabhängig von dem signierten Dataset.
  
### <a name="setsignedappdata-function"></a>Setsignetdappdata-Funktion
Legt anwendungsspezifische Daten fest, die signiert werden sollten.

Parameter:  
* **Wert**: App-spezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom Schutzdienst signiert wird. Diese signierten Daten sind durch „SetEncryptedAppData“ unabhängig von dem verschlüsselten Dataset.
  
### <a name="protectiondescriptorbuilder-function"></a>~ Schutzdescriptorbuilder-Funktion
_Noch nicht dokumentiert._
