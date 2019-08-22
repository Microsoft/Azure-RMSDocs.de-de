---
title: MIP::P rotectionhandler::P ublishingsettings
description: Dokumentiert die MIP::p rotectionhandler-Klasse des MIP-SDK (Microsoft Information Protection).
author: BryanLa
ms.service: information-protection
ms.topic: reference
ms.author: bryanla
ms.date: 07/16/2019
ms.openlocfilehash: 83489b41811cdaaf46b7336b21eeccb8289eb9f1
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69893122"
---
# <a name="class-mipprotectionhandlerpublishingsettings"></a>MIP::P rotectionhandler::P ublishingsettings 
Einstellungen zum Erstellen eines Schutz [Handlers](class_mip_protectionhandler.md) zum Schutz neuer Inhalte.
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public publishingsettings (Konstanten Std:: shared_ptr\<schutzdescriptor\>& schutzdescriptor)  |  Schutzhandler:: Settings-Konstruktor zum Erstellen einer neuen Engine.
Public Std:: shared_ptr\<schutzdescriptor\> getschutzdescriptor () konstant  | _Noch nicht dokumentiert._
public bool getisauditedextractionallowed () konstant  |  Ruft ab, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.
öffentliches void setisauditedextractionallowed (bool isauditedextractionallowed)  |  Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.
public bool getisdepretoredalgorithmpreferred () konstant  |  Ruft ab, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.
öffentliches void setisdeprealisiedalgorithmpreferred (bool isdepretoredalgorithmpreferred)  |  Legt fest, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.
öffentliches void setdelegateduseremail (konstant Std:: String & delegateduseremail)  |  Legt den Delegierten Benutzer fest.
Public Konstanten Std:: String & getdelegateduseremail () Konstanten  |  Ruft den Delegierten Benutzer ab.
  
## <a name="members"></a>Member
  
### <a name="publishingsettings-function"></a>Publishingsettings-Funktion
Schutzhandler:: Settings-Konstruktor zum Erstellen einer neuen Engine.

Parameter:  
* Schutz **Deskriptor**: Details zum Schutz


  
### <a name="getprotectiondescriptor-function"></a>Getschutzdescriptor-Funktion
_Noch nicht dokumentiert._

  
### <a name="getisauditedextractionallowed-function"></a>Getisauditedextractionallowed-Funktion
Ruft ab, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.

  
**Gibt Folgendes zurück**: Wenn Anwendungen ohne MIP-Unterstützung geschützte Inhalte öffnen dürfen
  
### <a name="setisauditedextractionallowed-function"></a>"Tartisauditedextractionallowed"-Funktion
Legt fest, ob nicht-MIP-fähige Anwendungen den geschützten Inhalt öffnen dürfen oder nicht.

Parameter:  
* **isauditedextractionallowed**: Wenn Anwendungen ohne MIP-Unterstützung geschützte Inhalte öffnen dürfen


  
### <a name="getisdeprecatedalgorithmpreferred-function"></a>Getisdeprealisiedalgorithmpreferred-Funktion
Ruft ab, ob der als veraltet markierte Kryptografiealgorithmus (ECB) für die Abwärtskompatibilität bevorzugt wird oder nicht.

  
**Gibt Folgendes zurück**: Wenn der veraltete Kryptografiealgorithmus bevorzugt wird
  
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

  
**Gibt Folgendes zurück**: Delegierter Benutzer ein Delegierter Benutzer wird angegeben, wenn der authentifizier Ende Benutzer/die Anwendung im Auftrag eines anderen Benutzers agiert.