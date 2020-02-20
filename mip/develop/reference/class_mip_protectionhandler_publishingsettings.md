---
title: MIP::P rotectionhandler::P ublishingsettings
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 02/14/2020
ms.openlocfilehash: e61eb300cbc787ecbb7fd14ec5dcb060d4f47d0a
ms.sourcegitcommit: 2d3c638fb576f3f074330a33d077db0cf0e7d4e7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2020
ms.locfileid: "77490760"
---
# <a name="class-mipprotectionhandlerpublishingsettings"></a>MIP::P rotectionhandler::P ublishingsettings 
Einstellungen zum Erstellen eines Schutz Handlers zum Schutz neuer Inhalte.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public publishingsettings (Konstante Std:: shared_ptr\<schutzdescriptor\>& schutzdescriptor)  |  Schutzhandler:: Settings-Konstruktor zum Erstellen einer neuen Engine.
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor () konstant  | _Noch nicht dokumentiert._
public bool getisauditedextractionallowed () konstant  |  Ruft ab, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.
öffentliches void setisauditedextractionallowed (bool isauditedextractionallowed)  |  Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.
public bool getisdepretoredalgorithmpreferred () konstant  |  Ruft ab, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.
öffentliches void setisdeprealisiedalgorithmpreferred (bool isdepretoredalgorithmpreferred)  |  Legt fest, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.
öffentliches void setdelegateduseremail (konstant Std:: String & delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String & getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
public bool ispublishingformatjson () konstant  |  Ruft ab, ob die zurückgegebene pl im JSON-Format vorliegt (das XML-Format ist besser akzeptiert und ist die Standardeinstellung).
öffentliches void setpublishingformatjson (bool ispublishingformatjson)  |  Gibt an, ob die zurückgegebene pl im JSON-Format vorliegt (das XML-Format ist in größerem Umfang akzeptiert und ist die Standardeinstellung).
  
## <a name="members"></a>Member
  
### <a name="publishingsettings-function"></a>Publishingsettings-Funktion
Schutzhandler:: Settings-Konstruktor zum Erstellen einer neuen Engine.

Parameter:  
* **schutzdeskriptor**: Schutz Details


  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
_Noch nicht dokumentiert._

  
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

