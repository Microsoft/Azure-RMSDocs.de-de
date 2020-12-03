---
title: Struktur telemetryconfiguration
description: Dokumentiert die telemetryconfiguration-Struktur.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 09/21/2020
ms.openlocfilehash: a152f604feabe66e354b0c85abd2d7cfca64e7b5
ms.sourcegitcommit: 6322f840388067edbe3642661e313ff225be5563
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/02/2020
ms.locfileid: "96535806"
---
# <a name="struct-telemetryconfiguration"></a>Struktur telemetryconfiguration 
Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)
  
## <a name="summary"></a>Zusammenfassung
 Members                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String hostnameoverride  |  Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
Public Std:: String librarynameoverride  |  Dateiname der alternativen telemetriebibliothek (dll).
Public Std:: shared_ptr \<HttpDelegate\> httpdelegateoverride  |  Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
Public Std:: shared_ptr \<TaskDispatcherDelegate\> taskdispatcherdelegateoverride  |  Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
public bool isnetworkdetectionaktivierte  |  Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
public bool islocalcachingenabled  |  Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
public bool istraceloggingenabled  |  Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
public bool istelemetryoptedout  |  Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
public bool isfastshutdownaktivierte  |  Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
Public Std:: map \<std::string, std::string\> CustomSettings  |  Benutzerdefinierte telemetrieeinstellungen >
Public Std:: map \<std::string, std::vector\<std::string\> \> maskedproperties  |  Telemetrieereignisse/-Eigenschaften, die maskiert werden sollen
  
## <a name="members"></a>Members
  
### <a name="hostnameoverride-struct-member"></a>hostnameoverride-Strukturmember
Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
  
### <a name="librarynameoverride-struct-member"></a>librarynameoverride-Strukturmember
Dateiname der alternativen telemetriebibliothek (dll).
  
### <a name="httpdelegate"></a>HttpDelegate
Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
  
### <a name="taskdispatcherdelegate"></a>TaskDispatcherDelegate
Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
  
### <a name="isnetworkdetectionenabled-struct-member"></a>isnetworkdetectionaktivierter Strukturmember
Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
  
### <a name="islocalcachingenabled-struct-member"></a>islocalcachingenabled-Strukturmember
Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
  
### <a name="istraceloggingenabled-struct-member"></a>istraceloggingenabled-Strukturmember
Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
  
### <a name="istelemetryoptedout-struct-member"></a>istelemetryoptedout-Strukturmember
Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
  
### <a name="isfastshutdownenabled-struct-member"></a>isfastshutdownaktivierter Strukturmember
Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
  
### <a name="customsettings-struct-member"></a>CustomSettings-Strukturmember
Benutzerdefinierte telemetrieeinstellungen >
  
### <a name="maskedproperties-struct-member"></a>maskedproperties-Strukturmember
Telemetrieereignisse/-Eigenschaften, die maskiert werden sollen