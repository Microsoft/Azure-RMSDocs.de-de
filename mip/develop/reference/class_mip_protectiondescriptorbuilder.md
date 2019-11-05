---
title: mip::ProtectionDescriptorBuilder-Klasse
description: Dokumentiert die MIP::p rotectiondescriptorbuilder-Klasse des MIP-SDKs (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: cdc72fd45a4b82611aa02d0a9182cd829b6d8a9e
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560767"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>mip::ProtectionDescriptorBuilder-Klasse 
Erstellt einen Schutz Deskriptor, der den dem Inhalt zugeordneten Schutz beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public MIP_API Std:: shared_ptr\<Schutz Deskriptor\> Build ()  |  Erstellt einen Schutz Deskriptor, dessen Zugriffsberechtigungen von dieser schutzdescriptorbuilder-Instanz definiert werden.
public void SetName(const std::string& value)  |  Legt den Namen für eine Schutzrichtlinie fest.
public void SetDescription(const std::string& value)  |  Legt die Beschreibung der Schutzrichtlinie fest.
öffentliches void setcontentvaliduntil (Konstante Std:: Chrono:: time_point\<Std:: Chrono:: system_clock\>& Wert)  |  Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.
public void SetAllowOfflineAccess(bool value)  |  Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.
public void SetReferrer(const std::string& uri)  |  Legt die Referreradresse der Schutzrichtlinie fest.
public void "stencryptedappdata" (Konstanten Std:: Map\<Std:: String, Std:: String\>& Wert)  |  Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
öffentliches void setsignetdappdata (Konstanten Std:: Map\<Std:: String, Std:: String\>& Wert)  |  Legt anwendungsspezifische Daten fest, die signiert werden sollten.
public virtual ~ProtectionDescriptorBuilder()  | Noch nicht dokumentiert.
public static MIP_API Std:: shared_ptr&lt;schützdeskriptor Builder&gt; MIP::P rotectiondescriptor Builder:: | atefromuserrights | Erstellt einen Schutz Deskriptor Builder, dessen Zugriffsberechtigungen von Benutzern und rechten definiert werden.
public static MIP_API Std:: shared_ptr&lt;schützdeskriptor Builder&gt; MIP::P rotectiondescriptor Builder:: | atefromuserrollen | Erstellt einen Schutz Deskriptor Builder, dessen Zugriffsberechtigungen von Benutzern und Rollen definiert werden.
public static MIP_API Std:: shared_ptr&lt;schutzdescriptor Builder&gt; MIP::P rotectiondescriptor Builder:: | atefromtemplate | Erstellt einen Schutz Deskriptor Builder, dessen Zugriffsberechtigungen von der Schutz Vorlage definiert werden. 

## <a name="members"></a>Member
  
### <a name="build-function"></a>Build-Funktion
Erstellt einen Schutz Deskriptor, dessen Zugriffsberechtigungen von dieser schutzdescriptorbuilder-Instanz definiert werden.

  
**Gibt Folgendes zurück**: neue Schutz Deskriptor Instanz
  
### <a name="setname-function"></a>SetName-Funktion
Legt den Namen für eine Schutzrichtlinie fest.

Parameter:  
* **value**: Name der Schutzrichtlinie


  
### <a name="setdescription-function"></a>SetDescription-Funktion
Legt die Beschreibung der Schutzrichtlinie fest.

Parameter:  
* **value**: Richtlinienbeschreibung


  
### <a name="setcontentvaliduntil-function"></a>Setcontentvaliduntil-Funktion
Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.

Parameter:  
* **value**: Ablaufzeit der Richtlinie


  
### <a name="setallowofflineaccess-function"></a>"Setlowofflineaccess"-Funktion
Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.

Parameter:  
* **value**: Angabe, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.


  
### <a name="setreferrer-function"></a>"Streferrer"-Funktion
Legt die Referreradresse der Schutzrichtlinie fest.

Parameter:  
* **uri**: Referreradresse der Richtlinie


Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Beschaffung der Schutzrichtlinie fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="setencryptedappdata-function"></a>Stencryptedappdata-Funktion
Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.

Parameter:  
* **value**: Anwendungsspezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom RMS-Dienst verschlüsselt wird. Diese verschlüsselten Daten sind durch „SetSignedAppData“ unabhängig von dem signierten Dataset.
  
### <a name="setsignedappdata-function"></a>Setsignetdappdata-Funktion
Legt anwendungsspezifische Daten fest, die signiert werden sollten.

Parameter:  
* **value**: Anwendungsspezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom Schutzdienst signiert wird. Diese signierten Daten sind durch „SetEncryptedAppData“ unabhängig von dem verschlüsselten Dataset.
  
### <a name="protectiondescriptorbuilder-function"></a>~ Schutzdescriptorbuilder-Funktion
_Noch nicht dokumentiert._

### <a name="createfromuserrights-function"></a>Funktion "kreatefromuserrights"
Erstellt einen Schutz Deskriptor Builder, dessen Zugriffsberechtigungen von Benutzern und rechten definiert werden.

Parameter:
* **usersandrights**: Sammlung von Benutzer-zu-Rechte-Zuordnungen.

**Rückgabe**: neue [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz 

### <a name="createfromuserroles-function"></a>Funktion "kreatefromuserrollen"
Erstellt einen Schutz Deskriptor Builder, dessen Zugriffsberechtigungen von Benutzern und Rollen definiert werden.

Parameter:
* **usersandrollen**: Sammlung von Benutzer-zu-Rollen-Zuordnungen.

**Returns**: erstellt einen Schutz [Deskriptor](class_mip_protectiondescriptor.md) , dessen Zugriffsberechtigungen von Benutzern und Rollen definiert werden.

### <a name="createfromtemplate-function"></a>Funktion "kreatefromtemplate"
Erstellt einen Schutz Deskriptor Builder, dessen Zugriffsberechtigungen von der Schutz Vorlage definiert werden. 

Parameter:
* **TemplateID**: eine Schutz Vorlagen-ID.

**Gibt Folgendes zurück**: eine neue Schutz [Deskriptor](class_mip_protectiondescriptor.md) -Instanz.