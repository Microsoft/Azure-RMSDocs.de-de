---
title: Class Protection Handler::P ublishingsettings
description: Dokumentiert die Schutz Handler::p ublishingsettings-Klasse des MIP-SDK (Microsoft Information Protection).
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: c5edcb9eca5e14d0f0f611f32e2f91d9ed2fcb25
ms.sourcegitcommit: 3f5f9f7695b9ed3c45e9230cd8b8cb39a1c5a5ed
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "95567116"
---
# <a name="class-protectionhandlerpublishingsettings"></a>Class Protection Handler::P ublishingsettings 
Einstellungen zum Erstellen eines Schutz Handlers zum Schutz neuer Inhalte.
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public publishingsettings (Konstante Std:: shared_ptr \<ProtectionDescriptor\>& schutzdescriptor)  |  Schutzhandler:: Settings-Konstruktor zum Erstellen einer neuen Engine.
public std::shared_ptr\<ProtectionDescriptor\> GetProtectionDescriptor() const  | _Noch nicht dokumentiert._
public bool getisauditedextractionallowed () konstant  |  Ruft ab, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.
öffentliches void setisauditedextractionallowed (bool isauditedextractionallowed)  |  Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.
public bool getisdepretoredalgorithmpreferred () konstant  |  Ruft ab, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.
öffentliches void setisdeprealisiedalgorithmpreferred (bool isdepretoredalgorithmpreferred)  |  Legt fest, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.
öffentliches void setdelegateduseremail (konstant Std:: String& delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String& getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
public bool ispublishingformatjson () konstant  |  Ruft ab, ob die zurückgegebene pl im JSON-Format vorliegt (das XML-Format ist besser akzeptiert und ist die Standardeinstellung).
öffentliches void setpublishingformatjson (bool ispublishingformatjson)  |  Gibt an, ob die zurückgegebene pl im JSON-Format vorliegt (das XML-Format ist in größerem Umfang akzeptiert und ist die Standardeinstellung).
öffentliches void setprelicenseuseremail (Konstanten Std:: String& prelicenseuseremail)  |  Legt den Benutzer vor der Lizenz fest.
Public Konstanten Std:: String& getprelicenseuseremail () Konstanten  |  Ruft den Benutzer vor der Lizenzierung ab.
  
## <a name="members"></a>Members
  
### <a name="publishingsettings-function"></a>Publishingsettings-Funktion
Schutzhandler:: Settings-Konstruktor zum Erstellen einer neuen Engine.

Parameter:  
* **schutzdeskriptor**: Schutz Details


  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
Noch nicht dokumentiert.

  
### <a name="getisauditedextractionallowed-function"></a>Getisauditedextractionallowed-Funktion
Ruft ab, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.

  
**Gibt Folgendes zurück**: Wenn Anwendungen, die keine MIP unterstützen, geschützte Inhalte öffnen dürfen
  
### <a name="setisauditedextractionallowed-function"></a>"Tartisauditedextractionallowed"-Funktion
Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.

Parameter:  
* **isauditedextractionallowed**: Wenn Anwendungen ohne MIP-Unterstützung geschützte Inhalte öffnen dürfen


  
### <a name="getisdeprecatedalgorithmpreferred-function"></a>Getisdeprealisiedalgorithmpreferred-Funktion
Ruft ab, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.

  
**Gibt Folgendes zurück**: Wenn der veraltete Kryptografiealgorithmus bevorzugt wird.
  
### <a name="setisdeprecatedalgorithmpreferred-function"></a>"Stisdepretoredalgorithmpreferred"-Funktion
Legt fest, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.

Parameter:  
* **If**: der veraltete Kryptografiealgorithmus wird bevorzugt.


  
### <a name="setdelegateduseremail-function"></a>Setdelegateduseremail-Funktion
Legt den Delegierten Benutzer fest.

Parameter:  
* **delegateduseremail**: die Delegierungs-e-Mail.


Ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="getdelegateduseremail-function"></a>Getdelegateduseremail-Funktion
Ruft den Delegierten Benutzer ab.

  
**Returns**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.
  
### <a name="ispublishingformatjson-function"></a>Ispublishingformatjson-Funktion
Ruft ab, ob die zurückgegebene pl im JSON-Format vorliegt (das XML-Format ist besser akzeptiert und ist die Standardeinstellung).

  
**Gibt Folgendes zurück**: true, wenn auf die JSON-Format Ausgabe festgelegt ist.
  
### <a name="setpublishingformatjson-function"></a>Setpublishingformatjson-Funktion
Gibt an, ob die zurückgegebene pl im JSON-Format vorliegt (das XML-Format ist in größerem Umfang akzeptiert und ist die Standardeinstellung).

Parameter:  
* **ispublishingformatjson**:, wenn das JSON-Format aktiviert ist.


  
### <a name="setprelicenseuseremail-function"></a>Setprelicenseuseremail-Funktion
Legt den Benutzer vor der Lizenz fest.

Parameter:  
* **prelicenseuseremail**: Benutzer vor der Lizenzierung


Wenn kein Benutzer vor der Lizenzierung angegeben ist, wird keine vorab Lizenz abgerufen.
  
### <a name="getprelicenseuseremail-function"></a>Getprelicenseuseremail-Funktion
Ruft den Benutzer vor der Lizenzierung ab.

  
**Gibt Folgendes zurück**: Benutzer vor der Lizenz