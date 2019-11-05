---
title: 'MIP::P rotectionhandler:: consumptionsettings-Klasse'
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 63a7f3c377a40a5faf82afe332a12efed0d646c4
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73560722"
---
# <a name="class-mipprotectionhandlerconsumptionsettings"></a>MIP::P rotectionhandler:: consumptionsettings-Klasse 
Einstellungen zum Erstellen eines Schutz Handlers, um vorhandenen Inhalt zu nutzen.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public consumptionsettings (Konstante Std:: Vector\<uint8_t\>& serializedpublishinglicense)  |  Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public consumptionsettings (Konst Std:: shared_ptr\<publishinglicenseinfo\>& LicenseInfo)  |  Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public Std:: shared_ptr\<publishinglicenseinfo\> getpublishinglicenseinfo () konstant  |  Holen Sie sich die Veröffentlichungs Lizenz, die dem geschützten Inhalt zugeordnet ist.
public bool getisofflineonly () const  |  Ruft ab, ob die erstellungshandlererstellung http-Online Vorgänge zulässt.
öffentliches void "* tisofflineonly" (bool isofflineonly)  |  Legt fest, ob die schutzhandlererstellung http-Online Vorgänge zulässt.
öffentliches void setdelegateduseremail (konstant Std:: String & delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String & getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
  
## <a name="members"></a>Member
  
### <a name="consumptionsettings-function"></a>Consumptionsettings-Funktion
Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.

Parameter:  
* **serializedpublishinglicense**: serialisierte Veröffentlichungs Lizenz aus geschütztem Inhalt


  
### <a name="consumptionsettings-function"></a>Consumptionsettings-Funktion
Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.

Parameter:  
* **LicenseInfo**: Veröffentlichen von Lizenzinformationen aus geschützten Inhalten


Durch die Bereitstellung von publishinglicenseingefo (im Gegensatz zu einer reinen serialisierten Veröffentlichungs Lizenz) ist es nicht mehr erforderlich, dass MIP SDK die Veröffentlichungs Lizenz analysiert.
  
### <a name="getpublishinglicenseinfo-function"></a>Getpublishinglicenseingefo-Funktion
Holen Sie sich die Veröffentlichungs Lizenz, die dem geschützten Inhalt zugeordnet ist.

  
**Gibt Folgendes zurück**: Veröffentlichen von Lizenzinformationen
  
### <a name="getisofflineonly-function"></a>Getisofflineonly-Funktion
Ruft ab, ob die erstellungshandlererstellung http-Online Vorgänge zulässt.

  
**Gibt Folgendes zurück**: "true", wenn http-Vorgänge nicht zulässig sind, andernfalls "false", wenn diese Eigenschaft auf "true" festgelegt ist, wird die Schutz Handler-Erstellung nur erfolgreich ausgeführt, wenn der Inhalt bereits zuvor entschlüsselt und seine nicht abgelaufene Lizenz Ein MIP:: NetworkError wird ausgelöst, wenn keine zwischengespeicherten Inhalte gefunden werden.
  
### <a name="setisofflineonly-function"></a>Funktion "stisofflineonly"
Legt fest, ob die schutzhandlererstellung http-Online Vorgänge zulässt.

Parameter:  
* **isofflineonly**: true, wenn http-Vorgänge nicht zulässig sind, andernfalls false.


Wenn diese Eigenschaft auf "true" festgelegt ist, wird die erstellungshandlererstellung nur erfolgreich ausgeführt, wenn der Inhalt bereits zuvor entschlüsselt und seine nicht abgelaufene Lizenz zwischengespeichert wird. Ein MIP:: NetworkError wird ausgelöst, wenn keine zwischengespeicherten Inhalte gefunden werden.
  
### <a name="setdelegateduseremail-function"></a>Setdelegateduseremail-Funktion
Legt den Delegierten Benutzer fest.

Parameter:  
* **delegateduseremail**: die Delegierungs-e-Mail.


Ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="getdelegateduseremail-function"></a>Getdelegateduseremail-Funktion
Ruft den Delegierten Benutzer ab.

  
**Returns**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.