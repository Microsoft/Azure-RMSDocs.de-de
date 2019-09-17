---
title: 'MIP::P rotectionhandler:: consumptionsettings-Klasse'
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 08/27/2019
ms.openlocfilehash: d99b7c3468cc98ad655e41bdd2aaa771a287aca2
ms.sourcegitcommit: 1499790746145d40d667d138baa6e18598421f0e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2019
ms.locfileid: "70057566"
---
# <a name="class-mipprotectionhandlerconsumptionsettings"></a>MIP::P rotectionhandler:: consumptionsettings-Klasse 
Einstellungen zum Erstellen eines Schutz [Handlers](class_mip_protectionhandler.md) , um vorhandenen Inhalt zu nutzen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public consumptionsettings (Konstanten Std:: Vector\<uint8_t\>& serializedpublishinglicense)  | Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public consumptionsettings (Konst Std:: shared_ptr\<publishinglicenseinfo\>& LicenseInfo)  |  Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public Std:: shared_ptr\<publishinglicenseinfo\> getpublishinglicenseinfo () konstant  |  Holen Sie sich die Veröffentlichungs Lizenz, die dem geschützten Inhalt zugeordnet ist.
public bool getisofflineonly () const  |  Ruft ab, ob bei der Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) HTTP-Onlinevorgänge zulässig sind
öffentliches void "* tisofflineonly" (bool isofflineonly)  |  Legt fest, ob die [schutzhandlererstellung](class_mip_protectionhandler.md) http-Online Vorgänge zulässt.
öffentliches void setdelegateduseremail (konstant Std:: String & delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String & getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
  
## <a name="members"></a>Member
  
### <a name="consumptionsettings-function"></a>Consumptionsettings-Funktion
Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.

Parameter:  
* **serializedPublishingLicense**: Serialisierte Veröffentlichungs Lizenz aus geschütztem Inhalt


  
### <a name="consumptionsettings-function"></a>Consumptionsettings-Funktion
Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.

Parameter:  
* **licenseingefo**: Veröffentlichen von Lizenzinformationen aus geschützten Inhalten


Durch die Bereitstellung von publishinglicenseingefo (im Gegensatz zu einer reinen serialisierten Veröffentlichungs Lizenz) ist es nicht mehr erforderlich, dass MIP SDK die Veröffentlichungs Lizenz analysiert.
  
### <a name="getpublishinglicenseinfo-function"></a>Getpublishinglicenseingefo-Funktion
Holen Sie sich die Veröffentlichungs Lizenz, die dem geschützten Inhalt zugeordnet ist.

  
**Gibt Folgendes zurück**: Veröffentlichen von Lizenzinformationen
  
### <a name="getisofflineonly-function"></a>Getisofflineonly-Funktion
Ruft ab, ob bei der Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) HTTP-Onlinevorgänge zulässig sind

  
**Gibt Folgendes zurück**: „True“, wenn HTTP-Vorgänge nicht zulässig sind, andernfalls „false“. Wenn dieser Wert auf „true“ festgelegt ist, ist die Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) nur erfolgreich, wenn der Inhalt bereits entschlüsselt wurde und die noch gültige Lizenz zwischengespeichert wurde. Ein MIP:: NetworkError = wird ausgelöst, wenn keine zwischengespeicherten Inhalte gefunden werden.
  
### <a name="setisofflineonly-function"></a>Funktion "stisofflineonly"
Legt fest, ob die [schutzhandlererstellung](class_mip_protectionhandler.md) http-Online Vorgänge zulässt.

Parameter:  
* **isofflineonly**: True, wenn http-Vorgänge nicht zulässig sind, andernfalls false.


Wenn dieser Wert auf „true“ festgelegt ist, ist die Erstellung von [ProtectionHandler](class_mip_protectionhandler.md) nur erfolgreich, wenn der Inhalt bereits entschlüsselt wurde und die noch gültige Lizenz zwischengespeichert wurde. Ein MIP:: NetworkError wird ausgelöst, wenn keine zwischengespeicherten Inhalte gefunden werden.
  
### <a name="setdelegateduseremail-function"></a>Setdelegateduseremail-Funktion
Legt den Delegierten Benutzer fest.

Parameter:  
* **delegateduseremail**: die Delegierungs-e-Mail.


Ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="getdelegateduseremail-function"></a>Getdelegateduseremail-Funktion
Ruft den Delegierten Benutzer ab.

  
**Gibt Folgendes zurück**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.