---
title: 'Struktur MIP:: telemetryconfiguration'
description: Dokumentiert Strukturen, die mit dem Microsoft Information Protection (MIP) SDK verknüpft sind.
author: msmbaldwin
ms.service: information-protection
ms.topic: reference
ms.author: mbaldwin
ms.date: 10/29/2019
ms.openlocfilehash: 4e3e9be086bbcddea5398ccfbe549ffc2ca1aae6
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73567526"
---
# <a name="struct-miptelemetryconfiguration"></a>Struktur MIP:: telemetryconfiguration 
Benutzerdefinierte telemetrieeinstellungen (nicht häufig verwendet)
  
## <a name="summary"></a>Zusammenfassung
 Member                        | Beschreibungen                                
--------------------------------|---------------------------------------------
Public Std:: String hostnameoverride  |  Der hosttelemetrie-Instanzname. Wenn nicht festgelegt, fungiert MIP als eigener Host.
Public Std:: String librarynameoverride  |  Dateiname der alternativen telemetriebibliothek (dll).
Public Std:: shared_ptr\<httpdelegat\> httpdelegateoverride  |  Wenn festgelegt, wird die HTTP-Behandlung von dieser Instanz verwaltet.
Public Std:: shared_ptr\<taskdispatcherdelegat\> taskdispatcherdelegateoverride  |  Wenn festgelegt, wird die asynchrone Task Verarbeitung von dieser Instanz verwaltet. taskdispatcherdelegateoverides sollten nicht freigegeben werden, da Sie telemetrieobjekte enthalten können, und ihre Freigabe verhindern, bis taskdispatcher freigegeben wurde.
public bool isnetworkdetectionaktivierte  |  Wenn festgelegt, Pingt die telemetriekomponente den Netzwerkstatus im Hintergrund Thread.
public bool islocalcachingenabled  |  Wenn festgelegt, verwendet die telemetriekomponente das Zwischenspeichern auf dem Datenträger.
public bool istraceloggingenabled  |  Wenn festgelegt, schreibt die telemetriekomponente Warn-/Fehlerprotokolle auf den Datenträger.
public bool istelemetryoptedout  |  Wenn festgelegt, wird nur die erforderliche dienstdatentelemetrie gesendet.
public bool isfastshutdownaktivierte  |  Wenn festgelegt, werden keine Ereignisse beim Herunterfahren hochgeladen, Überwachungs Ereignisse werden sofort nach der Protokollierung hochgeladen.
Public Std:: Map\<Std:: String, Std:: String\> CustomSettings  |  Benutzerdefinierte telemetrieeinstellungen >
  
## <a name="members"></a>Member
  
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