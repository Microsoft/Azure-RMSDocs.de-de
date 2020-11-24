---
title: 'Class Protection Handler:: consumptionsettings'
description: 'Dokumentiert die schutzhandler:: consumptionsettings-Klasse des Microsoft Information Protection (MIP) SDK.'
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: 627845405fc0d4fc2523e958e2226d343d0013cc
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95566575"
---
# <a name="class-protectionhandlerconsumptionsettings"></a>Class Protection Handler:: consumptionsettings 
Einstellungen zum Erstellen eines Schutz Handlers, um vorhandenen Inhalt zu nutzen.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public consumptionsettings (Konstante Std:: Vector \<uint8_t\>& serializedpublishinglicense)  |  Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public consumptionsettings (Konstanten Std:: Vector \<uint8_t\>& serializedprelicense, Konstanten Std:: Vector \<uint8_t\>& serializedpublishinglicense)  |  Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public consumptionsettings (Konst Std:: shared_ptr \<PublishingLicenseInfo\>& LicenseInfo)  |  Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.
Public Std:: shared_ptr \<PublishingLicenseInfo\> getpublishinglicenseinfo () konstant  |  Holen Sie sich die Veröffentlichungs Lizenz, die dem geschützten Inhalt zugeordnet ist.
public bool getisofflineonly () const  |  Ruft ab, ob die erstellungshandlererstellung http-Online Vorgänge zulässt.
öffentliches void "* tisofflineonly" (bool isofflineonly)  |  Legt fest, ob die schutzhandlererstellung http-Online Vorgänge zulässt.
öffentliches void setdelegateduseremail (konstant Std:: String& delegateduseremail)  |  Legt den Delegierten Benutzer fest.
öffentliches void setcontentname (Konst Std:: String& ContentName)  | _Noch nicht dokumentiert._
Public Konstanten Std:: String& getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
Public Konstanten Std:: String& getcontentname () Konstanten  | _Noch nicht dokumentiert._
  
## <a name="members"></a>Members
  
### <a name="consumptionsettings-function"></a>Consumptionsettings-Funktion
Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.

Parameter:  
* **serializedpublishinglicense**: serialisierte Veröffentlichungs Lizenz aus geschütztem Inhalt


  
### <a name="consumptionsettings-function"></a>Consumptionsettings-Funktion
Schutzhandler:: consumptionsettings-Konstruktor zum Erstellen eines neuen Handlers.

Parameter:  
* **serializedprelicense**: die vorab Lizenz, die an den Inhalt angehängt ist, wurde serialisiert. 


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
  
### <a name="setcontentname-function"></a>Setcontentname-Funktion
Noch nicht dokumentiert.

  
### <a name="getdelegateduseremail-function"></a>Getdelegateduseremail-Funktion
Ruft den Delegierten Benutzer ab.

  
**Returns**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="getcontentname-function"></a>Getcontentname-Funktion
Noch nicht dokumentiert.
