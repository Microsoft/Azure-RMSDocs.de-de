---
# required metadata

title: Überwachen des Azure Rights Management-Connectors | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8a1b3e54-f788-4f84-b9d7-5d5079e50b4e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Überwachen des Azure Rights Management-Connectors

*Gilt für: Azure Rights Management, Windows Server 2012, Windows Server 2012 R2*

Nach der Installation und Konfiguration des RMS-Connectors können Sie die folgenden Methoden und Informationen verwenden, um den Connector und die Nutzung von Azure RMS in Ihrer Organisation zu überwachen.

## Anwendungsereignis-Protokolleinträge

Der RMS-Connector zeichnet Einträge für den **Microsoft RMS-Connector** im Anwendungsereignisprotokoll auf. 

Beispiele für diese Einträge sind die folgenden Informationsereignisse: Mit ID 1000 wird bestätigt, dass der Connectordienst gestartet wurde, ID 1002 zeigt an, dass sich ein Server erfolgreich mit dem RMS-Connector verbunden hat, und ID 1004 gibt an, wann die Liste der autorisierten Konten (alle Konten werden aufgeführt) auf den Connector heruntergeladen wurde. 

Wenn der Connector nicht für die Verwendung von HTTPS konfiguriert wurde, wird mit der Warnungs-ID 2002 angezeigt, dass ein Client eine nicht sichere Verbindung (HTTP) verwendet.

Wenn der Connector keine Verbindung mit Azure RMS herstellen kann, wird wahrscheinlich der Fehler 3001 angezeigt. Dieser Fehler kann beispielsweise aufgrund eines DNS-Problems oder bei einer Unterbrechung des Internetzugriffs auf mindestens einem Server auftreten, auf dem der RMS-Connector ausgeführt wird. 

> [!TIP] Wenn Server mit dem RMS-Connector keine Verbindung mit Azure RMS herstellen können, sind häufig Webproxykonfigurationen die Ursache.

Lesen Sie wie bei allen Ereignisprotokolleinträgen die Meldung, um weitere Einzelheiten zu erfahren.

Zusätzlich zum Überprüfen des Ereignisprotokolls bei der anfänglichen Bereitstellung des Connectors sollten Sie die Protokolle regelmäßig auf Warnungen und Fehler überprüfen. Beispiel: Der Connector funktioniert anfänglich wie erwartet, später können abhängige Konfigurationen jedoch von anderen Administratoren geändert werden. Ein anderer Administrator kann beispielsweise die Konfiguration des Webproxyservers so ändern, dass Server mit dem RMS-Connector nicht mehr auf das Internet zugreifen können (Fehler 3001). Oder ein Administrator entfernt ein Computerkonto aus einer Gruppe, die Sie für die Verwendung des Connectors berechtigt haben (Warnung 2001).

## Leistungsindikatoren

Bei der Installation des RMS-Connectors werden automatisch Leistungsindikatoren für den **Microsoft Rights Management-Connector** erstellt. Diese Leistungsindikatoren sind nützlich, um die Leistung bei Verwendung von Azure RMS über den Connector zu überwachen. 

Beispiel: Wenn beim Schützen von Dokumenten oder E-Mails oder beim Öffnen geschützter Dokumente oder E-Mails regelmäßig Verzögerungen auftreten, können Sie anhand der Leistungsindikatoren ermitteln, ob diese Verzögerungen aufgrund der Verarbeitungszeit des Connectors, aufgrund der Verarbeitungszeit von Azure RMS oder aufgrund von Netzwerkverzögerungen auftreten. Um die Ursache der Verzögerung zu ermitteln, überprüfen Sie Leistungsindikatoren mit Durchschnittswerten für **Connector-Verarbeitungszeit**, **Dienstantwortzeit** und **Connector-Antwortzeit**. Beispiel: **Lizenzierung erfolgreich. Batchanforderung – Durchschnittliche Connector-Antwortzeit**.

Wenn Sie vor Kurzem neue Serverkonten für die Verwendung des Connectors hinzugefügt haben, sollten Sie anhand des Leistungsindikators **Verstrichene Zeit seit der letzten Aktualisierung der Autorisierungsrichtlinie** überprüfen, ob der Connector die Liste seit der Aktualisierung heruntergeladen hat, oder ob Sie noch warten müssen (bis zu 15 Minuten).

## RMS Analyzer

Sie können das Analyzer-Tool von Rights Management Services zum Überwachen der Integrität des Connectors und Bestimmen etwaiger Konfigurationsprobleme verwenden.

Wenn Sie dieses Tool noch nicht heruntergeladen haben, können Sie dies im [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=46437) tun. Installieren Sie das Tool auf allen Computern, die über Internetzugriff verfügen und eine Verbindung mit dem RMS-Connector herstellen können. Führen Sie das Tool aus, und wählen Sie auf der Seite **Willkommen** die Option **Azure RMS-Connector**.

Weitere Informationen und Anleitungen finden Sie auf der Downloadseite unter **Details** und **Installationsanweisungen**.

## Logging

Mithilfe der Verwendungsprotokollierung können Sie ermitteln, wann E-Mails und Dokumente geschützt und verwendet werden. Wenn diese Protokollierung unter Verwendung des RMS-Connectors erfolgt, enthält das Feld mit der Benutzer-ID in den Protokollen den Dienstprinzipalnamen, der bei der Installation des RMS-Connectors automatisch erstellt wird.

Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Nutzung von Azure Rights Management](log-analyze-usage.md).

Wenn eine detailliertere Protokollierung zu Diagnosezwecken erforderlich ist, können Sie [Debugview](http://go.microsoft.com/fwlink/?LinkID=309277) von Windows Sysinternals verwenden und die Nachverfolgung für den RMS-Connector aktivieren, indem Sie die Datei „web.config“ für die Standardwebsite in IIS ändern. Dazu gehen Sie folgendermaßen vor:

1. Wechseln Sie unter **%programfiles%\Microsoft Rights Management connector\Web Service** zur Datei „web.config“.

2. Suchen Sie nach der folgenden Zeile:

        <trace enabled="false" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

3. Ersetzen Sie diese Zeile durch folgende:

        <trace enabled="true" requestLimit="10" pageOutput="false" traceMode="SortByTime" localOnly="true"/>

4.  Halten Sie IIS an, und starten Sie die Dienste neu, um die Ablaufverfolgung zu aktivieren. 

5.  Nachdem Sie die benötigten Ablaufverfolgungen erfasst haben, stellen Sie die Zeile in Schritt 3 wieder her. Anschließend halten Sie IIS erneut an und starten die Dienste neu.



<!--HONumber=Jun16_HO2-->


