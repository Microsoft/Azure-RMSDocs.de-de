---
title: "Überwachen des Azure Rights Management-Connectors | Azure Information Protection"
description: "Hier finden Sie Informationen, die Sie beim Überwachen des Connectors und Verwendung des Azure Rights Management-Diensts von Azure Information Protection in Ihre Organisation unterstützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/29/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: e5939bb469af198a74d81724c5417eb63db7732b
ms.openlocfilehash: bf73a79218fa8dba2b90115d0c1573a29f791023


---

# <a name="monitor-the-azure-rights-management-connector"></a>Überwachen des Azure Rights Management-Connectors

>*Gilt für: Azure Information Protection, Windows Server 2012, Windows Server 2012 R2*

Nach der Installation und Konfiguration des RMS-Connectors können Sie die folgenden Methoden und Informationen verwenden, um den Connector und die Nutzung des Azure Rights Management-Diensts von Azure Information Protection in Ihrer Organisation zu überwachen.

## <a name="application-event-log-entries"></a>Anwendungsereignis-Protokolleinträge

Der RMS-Connector zeichnet Einträge für den **Microsoft RMS-Connector** im Anwendungsereignisprotokoll auf. 

Beispiele für diese Einträge sind die folgenden Informationsereignisse: Mit ID 1000 wird bestätigt, dass der Connectordienst gestartet wurde, ID 1002 zeigt an, dass sich ein Server erfolgreich mit dem RMS-Connector verbunden hat, und ID 1004 gibt an, wann die Liste der autorisierten Konten (alle Konten werden aufgeführt) auf den Connector heruntergeladen wurde. 

Wenn der Connector nicht für die Verwendung von HTTPS konfiguriert wurde, wird mit der Warnungs-ID 2002 angezeigt, dass ein Client eine nicht sichere Verbindung (HTTP) verwendet.

Wenn der Connector keine Verbindung mit dem Azure Rights Management-Dienst herstellen kann, wird wahrscheinlich der Fehler 3001 angezeigt. Dieser Fehler kann beispielsweise aufgrund eines DNS-Problems oder bei einer Unterbrechung des Internetzugriffs auf mindestens einem Server auftreten, auf dem der RMS-Connector ausgeführt wird. 

> [!TIP]
> Wenn Server mit dem RMS-Connector keine Verbindung mit dem Azure Rights Management-Dienst herstellen können, sind häufig Webproxykonfigurationen die Ursache.

Lesen Sie wie bei allen Ereignisprotokolleinträgen die Meldung, um weitere Einzelheiten zu erfahren.

Zusätzlich zum Überprüfen des Ereignisprotokolls bei der anfänglichen Bereitstellung des Connectors sollten Sie die Protokolle regelmäßig auf Warnungen und Fehler überprüfen. Beispiel: Der Connector funktioniert anfänglich wie erwartet, später können abhängige Konfigurationen jedoch von anderen Administratoren geändert werden. Ein anderer Administrator kann beispielsweise die Konfiguration des Webproxyservers so ändern, dass Server mit dem RMS-Connector nicht mehr auf das Internet zugreifen können (Fehler 3001). Oder ein Administrator entfernt ein Computerkonto aus einer Gruppe, die Sie für die Verwendung des Connectors berechtigt haben (Warnung 2001).

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

Dieses Ereignis wird protokolliert, wenn bei dem Versuch eines Kontos, eine Verbindung zu dem RMS-Connector aufzubauen, ein Fehler auftritt. Der häufigste Grund dafür ist das Fehlen des Kontos, das die Verbindung herstellt, in der Liste der autorisierten Konten, die der RMS-Connector des Azure Rights Management-Diensts herunterlädt. So z.B., wenn die aktuelle Liste ist noch nicht heruntergeladen wurde (das geschieht alle 15 Minuten) oder das Konto in der Liste fehlt. 

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

**Die Liste der Autorisierungen ist leer. Der Dienst kann nicht verwendet werden, bis die Liste der für den Connector autorisierten Benutzer und Gruppen aufgefüllt wird.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector über keine Liste der autorisierten Konten verfügt, und lokale Server daher keine Verbindung zu ihm herstellen können. Der RMS-Connector lädt die Liste alle 15 Minuten von Azure RMS herunter. 

Verwenden Sie das Administrator-Tool des RMS-Connectors, um die Konten anzugeben. Weitere Informationen finden Sie unter [Autorisieren von Servern für die Verwendung des RMS-Connectors]( install-configure-rms-connector.md#authorizing-servers-to-use-the-rms-connector). 

----

Fehler **3000**

**Im Microsoft RMS-Connector ist ein Ausnahmefehler aufgetreten.**

Dieses Ereignis wird jedes Mal protokolliert, wenn im RMS-Connector ein unerwarteter Fehler auftritt. Die Details des Fehlers werden in der Ereignismeldung protokolliert.

Eine mögliche Ursache kann durch den Text **Anforderung mit Leerantwort fehlgeschlagen** in der Ereignismeldung identifiziert werden. Wird dieser Text angezeigt, liegt dies möglicherweise daran, dass Sie ein Netzwerkgerät verwenden, das eine SSL-Überprüfung der Pakete zwischen den lokalen Servern und dem RMS-Connectorserver ausführt. Dies wird nicht unterstützt und führt zu einem Fehler bei der Kommunikation und dieser Meldung im Ereignisprotokoll.

----

Fehler **3001**

**Beim Herunterladen von Autorisierungsinformationen ist eine Ausnahme aufgetreten.**

Dieses Ereignis wird protokolliert, wenn der RMS-Connector die aktuelle Liste der für den RMS-Connector autorisierten Konten nicht herunterladen kann. Die Details des Fehlers werden in der Ereignismeldung protokolliert.



----

## <a name="performance-counters"></a>Leistungsindikatoren

Bei der Installation des RMS-Connectors werden automatisch Leistungsindikatoren für den **Microsoft Rights Management-Connector** erstellt. Diese Leistungsindikatoren sind nützlich, um die Leistung bei Verwendung des Azure Rights Management-Diensts über den Connector zu überwachen. Beispiel: Wenn beim Schützen von Dokumenten oder E-Mails oder beim Öffnen geschützter Dokumente oder E-Mails regelmäßig Verzögerungen auftreten, können Sie anhand der Leistungsindikatoren ermitteln, ob diese Verzögerungen aufgrund der Verarbeitungszeit des Connectors, aufgrund der Verarbeitungszeit des Azure Rights Management-Diensts oder aufgrund von Netzwerkverzögerungen auftreten. Um die Ursache der Verzögerung zu ermitteln, überprüfen Sie Leistungsindikatoren mit Durchschnittswerten für **Connector-Verarbeitungszeit**, **Dienstantwortzeit** und **Connector-Antwortzeit**. Beispiel: **Lizenzierung erfolgreich. Batchanforderung – Durchschnittliche Connector-Antwortzeit**.

Wenn Sie vor Kurzem neue Serverkonten für die Verwendung des Connectors hinzugefügt haben, sollten Sie anhand des Leistungsindikators **Verstrichene Zeit seit der letzten Aktualisierung der Autorisierungsrichtlinie** überprüfen, ob der Connector die Liste seit der Aktualisierung heruntergeladen hat, oder ob Sie noch warten müssen (bis zu 15 Minuten).

## <a name="rms-analyzer"></a>RMS Analyzer

Auch wenn für dieses Tool die derzeit vorhandenen Supportoptionen verfügbar sind, können Sie das Analyzer-Tool von Rights Management Services zum Überwachen der Integrität des Connectors und zum Identifizieren etwaiger Konfigurationsprobleme verwenden. Wenn Sie dieses Tool noch nicht heruntergeladen haben, können Sie dies im [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=46437) tun. 

Melden Sie sich mithilfe eines Kontos, das Sie für die Nutzung des Connectors für diese Arbeitsauslastung autorisiert haben, an einem der für den RMS-Connector konfigurierten Server an. Wenn Sie den RMS-Connector zum Beispiel für Exchange konfiguriert haben, melden Sie sich an diesem Server mithilfe eines der Konten an, die Sie im Konfigurationstool für den RMS-Connector für Exchange autorisiert haben. Führen Sie dann das RMS Analyzer-Tool mit der Option **Als Administrator ausführen** aus.

Wählen Sie beim Laden des Tools auf der Seite **Willkommen** die Option **Azure RMS-Connector** aus. Geben Sie die URL Ihres RMS-Connectors als aktive Adresse ein, und klicken Sie auf den grünen Pfeil. Dann sollten die Details Ihres Mandanten angezeigt werden, wodurch bestätigt wird, dass der Connector erfolgreich eine Verbindung mit dem Azure Rights Management-Dienst herstellen kann. Wenn dieser erste Test fehlerhaft ist, überprüfen Sie die Konfiguration des Proxyservers und die Firewalls, die den Serverdatenverkehr möglicherweise blockieren. Nachdem die Details zu Ihrem Mandanten erfolgreich angezeigt werden, können Sie das Ausführen von Diagnosetests für diese Serverarbeitsauslastung fortsetzen. Dabei werden unterstützte Versionsnummern, Voraussetzungen, Registrierungseinstellungen etc. geprüft.

Weitere Informationen und Anleitungen finden Sie auf der Downloadseite unter **Details** und **Installationsanweisungen**.

## <a name="logging"></a>Logging

Mithilfe der Verwendungsprotokollierung können Sie ermitteln, wann E-Mails und Dokumente geschützt und verwendet werden. Wenn diese Protokollierung mithilfe des RMS-Connectors erfolgt, enthält das Feld mit der Benutzer-ID in den Protokollen den Dienstprinzipalnamen **Aadrm_S-1-7-0**, der automatisch für den RMS-Connector erstellt wird.

Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](log-analyze-usage.md).

Wenn eine detailliertere Protokollierung zu Diagnosezwecken erforderlich ist, können Sie [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277) von Windows Sysinternals verwenden und die Nachverfolgung für den RMS-Connector aktivieren, indem Sie die Datei „web.config“ für die Standardwebsite in IIS ändern. Dazu gehen Sie folgendermaßen vor:

1. Wechseln Sie unter **%programfiles%\Microsoft Rights Management connector\Web Service** zur Datei „web.config“.

2. Suchen Sie nach der folgenden Zeile:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Ersetzen Sie diese Zeile durch folgende:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Halten Sie IIS an, und starten Sie die Dienste neu, um die Ablaufverfolgung zu aktivieren. 

5.  Nachdem Sie die benötigten Ablaufverfolgungen erfasst haben, stellen Sie die Zeile in Schritt 3 wieder her. Anschließend halten Sie IIS erneut an und starten die Dienste neu.




<!--HONumber=Nov16_HO5-->


