---
title: Klasse delegationlicensesettings
description: 'Dokumentiert die delegationlicensesettings:: nicht definierte Klasse des MIP-SDKs (Microsoft Information Protection).'
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 01/13/2021
ms.openlocfilehash: 947accd8104f8eda9f7b7320a1fbdb956810f34d
ms.sourcegitcommit: 76926b357bbfc8772ed132ce5f2426fbea59e98b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/14/2021
ms.locfileid: "98224924"
---
# <a name="class-delegationlicensesettings"></a>Klasse delegationlicensesettings 
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: shared_ptr \<const PublishingLicenseInfo\> getlicenseinfo () konstant  |  Ruft die Veröffentlichungs Lizenz publishinglicenseinfo ab.
Public Konstanten Std:: Vector \<std::string\>& getusers () konstant  |  Ruft die Liste der Benutzer für die Anforderung ab.
public bool getaquireenduserlicenses () konstant  |  Ruft den booleschen Wert ab, der angibt, ob eine Endbenutzer Lizenz zusätzlich zur delegatlizenz abgerufen werden soll oder nicht.
  
## <a name="members"></a>Member
  
### <a name="getlicenseinfo-function"></a>Getlicenseingefo-Funktion
Ruft die Veröffentlichungs Lizenz publishinglicenseinfo ab.

  
**Gibt Folgendes zurück**: publishinglicenseingefo
  
### <a name="getusers-function"></a>Getusers-Funktion
Ruft die Liste der Benutzer für die Anforderung ab.

  
**Gibt Folgendes zurück**: die Benutzer
  
### <a name="getaquireenduserlicenses-function"></a>Getaquireenduserlicenses-Funktion
Ruft den booleschen Wert ab, der angibt, ob eine Endbenutzer Lizenz zusätzlich zur delegatlizenz abgerufen werden soll oder nicht.

  
**Gibt Folgendes zurück**: ob Endbenutzer Lizenzen werden