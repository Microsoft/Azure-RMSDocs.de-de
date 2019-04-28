---
title: mip::ProtectionDescriptorBuilder-Klasse
description: Dokumentiert die mip::protectiondescriptorbuilder-Klasse von der Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.collection: M365-security-compliance
ms.author: mbaldwin
ms.date: 01/28/2019
ms.openlocfilehash: 7ed2c118d2f57f93d0445c113fd6127704e52637
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60174152"
---
# <a name="class-mipprotectiondescriptorbuilder"></a>mip::ProtectionDescriptorBuilder-Klasse 
Erstellt eine [ProtectionDescriptor](class_mip_protectiondescriptor.md)-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Öffentliche MIP_API Std:: shared_ptr\<ProtectionDescriptor\> Build()  |  Erstellt einen [ProtectionDescriptor](class_mip_protectiondescriptor.md), dessen Zugriffsberechtigungen von dieser [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)-Instanz definiert werden.
public void SetName(const std::string& value)  |  Legt den Namen für eine Schutzrichtlinie fest.
public void SetDescription(const std::string& value)  |  Legt die Beschreibung der Schutzrichtlinie fest.
public void SetContentValidUntil(const std::chrono::time_point\<std::chrono::system_clock\>& value)  |  Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.
public void SetAllowOfflineAccess(bool value)  |  Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.
public void SetReferrer(const std::string& uri)  |  Legt die Referreradresse der Schutzrichtlinie fest.
public void SetEncryptedAppData(const std::map\<std::string, std::string\>& value)  |  Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
public void SetSignedAppData(const std::map\<std::string, std::string\>& value)  |  Legt anwendungsspezifische Daten fest, die signiert werden sollten.
public virtual ~ProtectionDescriptorBuilder()  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Member
  
### <a name="build-function"></a>Funktion erstellen
Erstellt einen [ProtectionDescriptor](class_mip_protectiondescriptor.md), dessen Zugriffsberechtigungen von dieser [ProtectionDescriptorBuilder](class_mip_protectiondescriptorbuilder.md)-Instanz definiert werden.

  
**Gibt**: Neue [ProtectionDescriptor](class_mip_protectiondescriptor.md) Instanz
  
### <a name="setname-function"></a>SetName-Funktion
Legt den Namen für eine Schutzrichtlinie fest.

Parameter:  
* **value**: Name des Protection-Richtlinie


  
### <a name="setdescription-function"></a>SetDescription-Funktion
Legt die Beschreibung der Schutzrichtlinie fest.

Parameter:  
* **value**: Richtlinienbeschreibung


  
### <a name="setcontentvaliduntil-function"></a>SetContentValidUntil-Funktion
Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.

Parameter:  
* **value**: Ablaufzeit der Richtlinie


  
### <a name="setallowofflineaccess-function"></a>SetAllowOfflineAccess-Funktion
Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.

Parameter:  
* **value**: Wenn Richtlinie den Zugang zu Offlineinhalten oder nicht erlaubt


  
### <a name="setreferrer-function"></a>SetReferrer-Funktion
Legt die Referreradresse der Schutzrichtlinie fest.

Parameter:  
* **uri**: Referreradresse der Richtlinie


Der Referrer ist ein URI, der dem Benutzer angezeigt wird, nachdem die Beschaffung der Schutzrichtlinie fehlgeschlagen ist. Dieser enthält Informationen darüber, wie dieser Benutzer für den Zugriff auf den Inhalt berechtigt werden kann.
  
### <a name="setencryptedappdata-function"></a>SetEncryptedAppData-Funktion
Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.

Parameter:  
* **value**: App-spezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom RMS-Dienst verschlüsselt wird. Diese verschlüsselten Daten sind durch „SetSignedAppData“ unabhängig von dem signierten Dataset.
  
### <a name="setsignedappdata-function"></a>SetSignedAppData-Funktion
Legt anwendungsspezifische Daten fest, die signiert werden sollten.

Parameter:  
* **value**: App-spezifische Daten


Eine Anwendung kann ein Wörterbuch von anwendungsspezifischen Daten angeben, das vom Schutzdienst signiert wird. Diese signierten Daten sind durch „SetEncryptedAppData“ unabhängig von dem verschlüsselten Dataset.
  
### <a name="protectiondescriptorbuilder-function"></a>~ ProtectionDescriptorBuilder-Funktion
_Noch nicht dokumentiert._
