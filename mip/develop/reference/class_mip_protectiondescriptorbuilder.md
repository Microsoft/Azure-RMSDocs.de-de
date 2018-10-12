---
title: Microsoft Information Protection-Klasse „ProtectionDescriptorBuilder“
description: Referenz für die Microsoft Information Protection-Klasse „ProtectionDescriptorBuilder“
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: 42e44cfaf269a43d0210c0c040ea70ccc1fb192e
ms.sourcegitcommit: 1cf14852cd14ea91ac964fb03a901238455ffdff
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2018
ms.locfileid: "47446633"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>mip::ProtectionDescriptorBuilder-Klasse 
Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public MIP_API std::shared_ptr<ProtectionDescriptor> Build()  |  Erstellt einen [ProtectionDescriptor](class_mip_protectiondescriptor.md), dessen Zugriffsberechtigungen von dieser [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)-Instanz definiert werden.
 public void SetName(const std::string& value)  |  Legt den Namen für eine Schutzrichtlinie fest.
 public void SetDescription(const std::string& value)  |  Legt die Beschreibung der Schutzrichtlinie fest.
public void SetContentValidUntil(const std::chrono::time_point<std::chrono::system_clock>& value)  |  Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.
 public void SetAllowOfflineAccess(bool value)  |  Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.
 public void SetReferrer(const std::string& uri)  |  Legt die Referreradresse der Schutzrichtlinie fest.
public void SetEncryptedAppData(const std::map<std::string, std::string>& value)  |  Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
public void SetSignedAppData(const std::map<std::string, std::string>& value)  |  Legt anwendungsspezifische Daten fest, die signiert werden sollten.
 public virtual ~ProtectionDescriptorBuilder()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="protectiondescriptor"></a>ProtectionDescriptor
Erstellt einen [ProtectionDescriptor](class_mip_protectiondescriptor.md), dessen Zugriffsberechtigungen von dieser [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)-Instanz definiert werden.

  
**Rückgabe**: neue [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz
  
### <a name="setname"></a>SetName
Legt den Namen für eine Schutzrichtlinie fest.

Parameter:  
* **value**: Name der Schutzrichtlinie


  
### <a name="setdescription"></a>SetDescription
Legt die Beschreibung der Schutzrichtlinie fest.

Parameter:  
* **value**: Richtlinienbeschreibung


  
### <a name="setcontentvaliduntil"></a>GetContentValidUntil
Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.

Parameter:  
* **value**: Ablaufzeit der Richtlinie


  
### <a name="setallowofflineaccess"></a>SetAllowOfflineAccess
Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.

Parameter:  
* **value**: Angabe, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.


  
### <a name="setreferrer"></a>SetReferrer
Legt die Referreradresse der Schutzrichtlinie fest.

Parameter:  
* **uri**: Referreradresse der Richtlinie


Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Beschaffung der Schutzrichtlinie fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="setencryptedappdata"></a>SetEncryptedAppData
Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.

Parameter:  
* **value**: Anwendungsspezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom RMS-Dienst verschlüsselt wird. Diese verschlüsselten Daten sind durch „SetSignedAppData“ unabhängig von dem signierten Dataset.
  
### <a name="setsignedappdata"></a>SetSignedAppData
Legt anwendungsspezifische Daten fest, die signiert werden sollten.

Parameter:  
* **value**: Anwendungsspezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom Schutzdienst signiert wird. Diese signierten Daten sind durch „SetEncryptedAppData“ unabhängig von dem verschlüsselten Dataset.
  
### <a name="protectiondescriptorbuilder"></a>~ProtectionDescriptorBuilder
_Noch nicht dokumentiert._
