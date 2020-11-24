---
title: Class schutzdescriptorbuilder
description: 'Dokumentiert die schutzdescriptorbuilder:: nicht definierte Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 2e5573a896ef0935c33e85a2ed7f73451ced8e7c
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567154"
---
# <a name="class-protectiondescriptorbuilder"></a>Class schutzdescriptorbuilder 
Erstellt eine ProtectionDescriptor-Instanz, die den Schutz für ein Inhaltsobjekt beschreibt.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
public MIP_API std::shared_ptr\<ProtectionDescriptor\> Build()  |  Erstellt einen ProtectionDescriptor, dessen Zugriffsberechtigungen von dieser ProtectionDescriptorBuilder-Instanz definiert werden.
public void SetName(const std::string& value)  |  Legt den Namen für eine Schutzrichtlinie fest.
public void SetDescription(const std::string& value)  |  Legt die Beschreibung der Schutzrichtlinie fest.
öffentliches void setcontentvaliduntil (Konstante Std:: Chrono:: time_point \<std::chrono::system_clock\>& Wert)  |  Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.
public void SetAllowOfflineAccess(bool value)  |  Legt fest, ob die Schutzrichtlinie den Zugriff auf Offlineinhalte erlaubt oder nicht.
public void SetReferrer(const std::string& uri)  |  Legt die Referreradresse der Schutzrichtlinie fest.
öffentliches void "stencryptedappdata" (Konstanten Std:: map- \<std::string, std::string\>& Wert)  |  Legt anwendungsspezifische Daten fest, die verschlüsselt werden sollten.
öffentliches void setsignetdappdata (Konstanten Std:: map \<std::string, std::string\>& Wert)  |  Legt anwendungsspezifische Daten fest, die signiert werden sollten.
öffentliches void setdoublekeyurl (Konstante Std:: String& doublekeyurl)  |  Legt die doppelte Schlüssel-URL fest, die für den benutzerdefinierten Schutz verwendet werden soll.
  
## <a name="members"></a>Members
  
### <a name="build-function"></a>Build-Funktion
Erstellt einen ProtectionDescriptor, dessen Zugriffsberechtigungen von dieser ProtectionDescriptorBuilder-Instanz definiert werden.

  
**Rückgabe**: neue ProtectionDescriptor-Instanz
  
### <a name="setname-function"></a>SetName-Funktion
Legt den Namen für eine Schutzrichtlinie fest.

Parameter:  
* **value**: Name der Schutzrichtlinie


  
### <a name="setdescription-function"></a>SetDescription-Funktion
Legt die Beschreibung der Schutzrichtlinie fest.

Parameter:  
* **Wert**: Richtlinien Beschreibung


  
### <a name="setcontentvaliduntil-function"></a>Setcontentvaliduntil-Funktion
Legt den Ablaufzeitpunkt der Schutzrichtlinie fest.

Parameter:  
* **Wert**: Ablaufzeit der Richtlinie


  
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
  
### <a name="setdoublekeyurl-function"></a>Setdoublekeyurl-Funktion
Legt die doppelte Schlüssel-URL fest, die für den benutzerdefinierten Schutz verwendet werden soll.

Parameter:  
* **Wert**: Double Key URL

