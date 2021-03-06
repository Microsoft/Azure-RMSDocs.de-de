---
title: Überwachen des Rights Management-Connectors – AIP
description: Hier finden Sie Informationen, die Sie beim Überwachen des Connectors und Verwendung des Azure Rights Management-Diensts von Azure Information Protection in Ihre Organisation unterstützen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/20/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e
ms.subservice: connector
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: cfa8a6892fe7f6146b2f6a76d00530a1a83cb18d
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809424"
---
# <a name="monitor-the-azure-rights-management-connector"></a>Überwachen des Azure Rights Management-Connectors

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Nach der Installation und Konfiguration des RMS-Connectors können Sie die folgenden Methoden und Informationen verwenden, um den Connector und die Nutzung des Azure Rights Management-Diensts von Azure Information Protection in Ihrer Organisation zu überwachen.

## <a name="application-event-log-entries"></a>Anwendungsereignis-Protokolleinträge

Der RMS-Connector zeichnet Einträge für den **Microsoft RMS-Connector** im Anwendungsereignisprotokoll auf. 

Dazu zählen beispielsweise Informationsereignisse wie die folgenden:

- ID 1000 bestätigt, dass der Connectordienst gestartet wurde.

- ID 1002 bedeutet, dass ein Server erfolgreich eine Verbindung mit dem RMS-Connector hergestellt hat

- 1004 bedeutet, dass die Liste autorisierter Konten (jedes Konto ist aufgeführt) in den Connector heruntergeladen wurde. 

Wenn der Connector nicht für die Verwendung von HTTPS konfiguriert wurde, wird mit der Warnungs-ID 2002 angezeigt, dass ein Client eine nicht sichere Verbindung (HTTP) verwendet.

Wenn der Connector keine Verbindung mit dem Azure Rights Management-Dienst herstellen kann, wird wahrscheinlich der Fehler 3001 angezeigt. Dieser Verbindungsfehler kann beispielsweise aufgrund eines DNS-Problems oder eines fehlenden Internet Zugriffs für einen oder mehrere Server, auf denen der RMS-Connector ausgeführt wird, verursacht werden. 

> [!TIP]
> Wenn Server mit dem RMS-Connector keine Verbindung mit dem Azure Rights Management-Dienst herstellen können, sind häufig Webproxykonfigurationen die Ursache.

Lesen Sie wie bei allen Ereignisprotokolleinträgen die Meldung, um weitere Einzelheiten zu erfahren.

Zusätzlich zum Überprüfen des Ereignisprotokolls bei der anfänglichen Bereitstellung des Connectors sollten Sie die Protokolle regelmäßig auf Warnungen und Fehler überprüfen. Der Connector funktioniert anfänglich wie erwartet, später können abhängige Konfigurationen jedoch von anderen Administratoren geändert werden. Beispielsweise ändert ein anderer Administrator die Konfiguration des Webproxyservers so, dass RMS-Verbindungs Server nicht mehr auf das Internet zugreifen können (Fehler 3001) oder ein Computer Konto aus einer Gruppe entfernt wird, die Sie als autorisiert zur Verwendung des Connectors angegeben haben (Warnung 2001).

### <a name="event-log-ids-and-descriptions"></a>Ereignisprotokoll-IDs und Beschreibungen

Mithilfe der folgenden Abschnitte können Sie mögliche Ereignis-IDs, Beschreibungen und zusätzliche Informationen ermitteln.

-----

Information **1000**

**Der Webdienst „Microsoft RMS-Connector“ wurde gestartet.**

Dieses Ereignis wird beim ersten Startversuch des RMS-Connectors protokolliert.

----

Information **1001**

**Der Webdienst „Microsoft RMS-Connector“ wurde beendet.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector infolge eines normalen Vorgangs beendet wird. So z.B., wenn IIS neu gestartet oder der Computer heruntergefahren wird. 

----

Information **1002**

**Einem autorisierten Server wurde Zugriff auf den Microsoft RMS-Connector gewährt.**

Dieses Ereignis wird beim ersten Verbindungsaufbau eines Kontos von einem lokalen Server zum RMS-Connector protokolliert, nachdem der Azure RMS-Administrator das Konto im Administrator-Tool des RMS-Connectors autorisiert hat. Die Ereignismeldung enthält die SID, den Kontonamen sowie den Namen des Computers, der die Verbindung herstellt.

----

Information **1003**

**Die Verbindung des unten aufgeführten Clients hat von einer unsicheren Verbindung (HTTP) zu einer sicheren Verbindung (HTTPS) gewechselt.**

Dieses Ereignis wird protokolliert, wenn die Verbindung eines lokalen Servers zum RMS-Connector von HTTP (weniger sicher) zu HTTPS (sicherer) geändert wird. Die Ereignismeldung enthält die SID, den Kontonamen sowie den Namen des Computers, der die Verbindung herstellt.

----

Information **1004**

**Die Liste der autorisierten Konten wurde aktualisiert.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector die aktuelle Liste der zur Verwendung des RMS-Connectors autorisierten Konten heruntergeladen hat (vorhandene Konten und jegliche Änderungen). Wenn der RMS-Connector mit dem Azure Rights Management-Dienst kommunizieren kann, wird diese Liste alle 15 Minuten heruntergeladen.

----

Warnung **2000**

**Der Benutzerprinzipal im HTTP-Kontext ist nicht vorhanden oder ungültig. Überprüfen Sie bitte, ob die anonyme Authentifizierung in IIS auf der Website des Microsoft RMS-Connectors deaktiviert wurde und nur die Windows-Authentifizierung aktiviert ist.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector das Konto nicht eindeutig identifizieren kann, das versucht, eine Verbindung mit dem RMS-Connector herzustellen. Das Ereignis wird möglicherweise durch eine falsche Konfiguration der anonymen Authentifizierung für IIS oder der Kontoherkunft aus einer nicht vertrauenswürdigen Gesamtstruktur hervorgerufen.

----

Warnung **2001**

**Nichtautorisierter Zugriffsversuch auf den Microsoft RMS-Connector.**

Dieses Ereignis wird protokolliert, wenn bei dem Versuch eines Kontos, eine Verbindung zu dem RMS-Connector aufzubauen, ein Fehler auftritt. Der häufigste Grund für diese Warnung ist das Fehlen des Kontos, das die Verbindung herstellt, in der Liste der autorisierten Konten, die der RMS-Connector des Azure Rights Management-Diensts herunterlädt. So z.B., wenn die aktuelle Liste noch nicht heruntergeladen wurde (dieses Ereignis tritt alle 15 Minuten auf) oder das Konto in der Liste fehlt. 

Das Ereignis kann aber auch dadurch hervorgerufen werden, dass Sie den RMS-Connector auf dem gleichen Server installiert haben, der für die Verwendung des Connectors konfiguriert ist. So z.B., wenn Sie den RMS-Connector auf einem Server mit Exchange Server installieren und ein Exchange-Konto zur Verwendung des Connectors autorisieren. Diese Konfiguration wird nicht unterstützt, da der RMS-Connector das Konto bei dem Versuch der Verbindungsherstellung nicht korrekt identifizieren kann.

Die Ereignismeldung enthält Informationen über das Konto und den Computer, die versuchen, eine Verbindung zum RMS-Connector herzustellen:

- Wenn das Konto, das eine Verbindung mit dem RMS-Connector herstellen möchte, ein gültiges Konto ist, verwenden Sie das Administrator-Tool für den RMS-Connector, um das Konto in die Liste der autorisierten Konten aufzunehmen. Weitere Informationen darüber, welche Konten autorisiert sein müssen, finden Sie unter [Hinzufügen eines Servers zur Liste der zugelassenen Server](install-configure-rms-connector.md#add-a-server-to-the-list-of-allowed-servers). 

- Wenn sich das Konto, das eine Verbindung mit dem RMS-Connector herstellen möchte, auf dem gleichen Computer wie der Server des RMS-Connectors befindet, installieren Sie den Connector auf einem separaten Server. Weitere Informationen zu den Voraussetzungen finden Sie unter [Voraussetzungen für den RMS-Connector]( deploy-rms-connector.md#prerequisites-for-the-rms-connector).

----

Warnung **2002**

**Der unten aufgeführte Client verwendet eine nicht gesicherte Verbindung (HTTP).**

Dieses Ereignis wird protokolliert, wenn ein lokaler Server erfolgreich eine Verbindung zum RMS-Connector herstellt, die Verbindung aber HTTP (weniger sicher) statt HTTPS (sicherer) verwendet. Ein Ereignis wird pro Konto, nicht pro Verbindung protokolliert. Dieses Ereignis wird erneut ausgelöst, wenn das Konto zunächst erfolgreich auf die Verwendung von HTTPS gewechselt hatte und anschließend doch zu HTTP zurückkehrt.

Die Ereignismeldung enthält die Konto-SID, den Kontonamen und den Namen des Computers, der die Verbindung zum RMS-Connector herstellt.

Informationen zum Konfigurieren des RMS-Connectors für HTTPS-Verbindungen finden Sie unter [Konfigurieren des RMS-Connectors für die Verwendung von HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https).

----

Warnung **2003**

**Die Liste der Autorisierungen ist leer. Der Dienst kann erst verwendet werden, wenn die Liste der autorisierten Benutzer und Gruppen für den Connector aufgefüllt ist.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector über keine Liste der autorisierten Konten verfügt, und lokale Server daher keine Verbindung zu ihm herstellen können. Der RMS-Connector lädt die Liste alle 15 Minuten von Azure RMS herunter. 

Verwenden Sie das Administrator-Tool des RMS-Connectors, um die Konten anzugeben. Weitere Informationen finden Sie unter [Autorisieren von Servern für die Verwendung des RMS-Connectors]( install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). 

----

Fehler **3000**

**Im Microsoft RMS-Connector ist ein Ausnahmefehler aufgetreten.**

Dieses Ereignis wird jedes Mal protokolliert, wenn im RMS-Connector ein unerwarteter Fehler auftritt. Die Details des Fehlers werden in der Ereignismeldung protokolliert.

Eine mögliche Ursache kann durch den Text **Anforderung mit Leerantwort fehlgeschlagen** in der Ereignismeldung identifiziert werden. Wird dieser Text angezeigt, liegt dies möglicherweise daran, dass Sie ein Netzwerkgerät verwenden, das eine SSL-Überprüfung der Pakete zwischen den lokalen Servern und dem RMS-Connectorserver ausführt. Der Azure Rights Management-Dienst unterstützt diese Konfiguration nicht. Die Ergebnisse sind ein Kommunikationsfehler und diese Ereignisprotokollmeldung.

----

Fehler **3001**

**Beim Herunterladen von Autorisierungsinformationen ist eine Ausnahme aufgetreten.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector die aktuelle Liste der für den RMS-Connector autorisierten Konten nicht herunterladen kann. Details des Fehlers werden in der Ereignismeldung protokolliert.



----

## <a name="performance-counters"></a>Leistungsindikatoren

Bei der Installation des RMS-Connectors werden automatisch Leistungsindikatoren für den **Microsoft Rights Management-Connector** erstellt. Diese Leistungsindikatoren sind nützlich, um die Leistung bei Verwendung des Azure Rights Management-Diensts zu überwachen und zu verbessern. 

Es treten beispielsweise regelmäßig Verzögerungen auf, wenn Dokumente oder E-Mails geschützt sind. Oder es kommt zu Verzögerungen, wenn geschützte Dokumente oder E-Mails geöffnet werden. In diesen Fällen können Sie mithilfe der Leistungsindikatoren die Ursache der Verzögerungen bestimmen: die Verarbeitungszeit im Connector, die Verarbeitungszeit im Azure Rights Management-Dienst oder Netzwerkverzögerungen. 

Um die Ursache der Verzögerung zu ermitteln, überprüfen Sie Leistungsindikatoren mit Durchschnittswerten für **Connector-Verarbeitungszeit**, **Dienstantwortzeit** und **Connector-Antwortzeit**. Beispiel: **Lizenzierung erfolgreich. Batchanforderung – Durchschnittliche Connector-Antwortzeit**.

Wenn Sie vor Kurzem neue Serverkonten für die Verwendung des Connectors hinzugefügt haben, sollten Sie anhand des Leistungsindikators **Verstrichene Zeit seit der letzten Aktualisierung der Autorisierungsrichtlinie** überprüfen, ob der Connector die Liste seit der Aktualisierung heruntergeladen hat, oder ob Sie noch warten müssen (bis zu 15 Minuten).

## <a name="logging"></a>Protokollierung

Mithilfe der Verwendungsprotokollierung können Sie ermitteln, wann E-Mails und Dokumente geschützt und verwendet werden. Wenn der RMS-Verbindungsdienst zum Schützen und Nutzen von Inhalten verwendet wird, enthält das Feld „Benutzer-ID“ in den Protokollen den Dienstprinzipalnamen **Aadrm_S-1-7-0**. Dieser Name wird automatisch für den RMS-Connector erstellt.

Weitere Informationen zur Verwendungs Protokollierung finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](log-analyze-usage.md).

Wenn Sie eine ausführlichere Protokollierung zu Diagnose Zwecken benötigen, verwenden Sie [DebugView](/sysinternals/downloads/debugview) von Windows Sysinternals, um die Protokolle an eine debugpipe auszugeben. 

1. Starten Sie DebugView als Administrator, und wählen Sie **Erfassung**  >  **Global Win32** erfassen aus.

1. Aktivieren Sie die Ablauf Verfolgung für den RMS-Connector, indem Sie die **web.config** Datei für die Standard Website in IIS ändern:

    1. Suchen Sie die Datei **web.config** im Ordner **%ProgramFiles%\Microsoft Rights Management connector\webdienst** .

    1. Suchen Sie die folgende Zeile:

        ```sh
        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>
        ```

    1. Ersetzen Sie diese Zeile durch folgenden Text:
        ```sh
        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>
        ```

1.  Halten Sie IIS an, und starten Sie die Dienste neu, um die Ablaufverfolgung zu aktivieren. 

1.  Wenn Sie die von Ihnen benötigten Ablauf Verfolgungen in der gewünschten debuview aufgezeichnet haben, setzen Sie die Zeile in Schritt 3 zurück, und starten Sie IIS erneut.