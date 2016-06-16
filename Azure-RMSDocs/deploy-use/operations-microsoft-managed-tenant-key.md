---
# required metadata

title: Von Microsoft verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/03/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Von Microsoft verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel

*Gilt für: Azure Rights Management, Office 365*

Wenn Ihr Mandantenschlüssel für Azure RMS von Microsoft verwaltet wird (Standard), finden Sie in den folgenden Abschnitten weitere Informationen zu den Lebenszyklusvorgängen, die für diese Topologie relevant sind.

## Widerrufen Ihres Mandantenschlüssels
Wenn Sie Ihr Abonnement von Azure RMS kündigen, beendet Azure RMS die Verwendung Ihres Mandantenschlüssels, und von Ihnen ist keine weitere Aktion mehr erforderlich.

## Neuvergabe (Rollover) Ihres Mandantenschlüssels
Die Neuvergabe Ihres Schlüssels wird auch als „Rollover“ bezeichnet. Führen Sie eine Neuvergabe Ihres Mandantenschlüssels nur durch, wenn es wirklich notwendig ist. Ältere Clients wie Office 2010 wurden nicht darauf ausgelegt, problemlos mit Schlüsseländerungen umzugehen. In diesem Szenario müssen Sie den RMS-Zustand auf Computern löschen, indem Sie eine Gruppenrichtlinie oder einen entsprechenden Mechanismus verwenden. Es gibt jedoch einige berechtigte Ereignisse, die Sie zwingen können, Ihren Mandantenschlüssel neu zu vergeben. Beispiel:

-   Ihr Unternehmen wurde in zwei oder mehr Unternehmen aufgeteilt. Wenn Sie Ihren Mandantenschlüssel neu vergeben, hat das neue Unternehmen keinen Zugriff auf neue Inhalte, die von Ihren Mitarbeitern veröffentlicht werden. Sie können auf den alten Inhalt zugreifen, wenn sie eine Kopie des alten Mandantenschlüssels besitzen.

-   Sie glauben, dass die Masterkopie Ihres Mandantenschlüssels (die in Ihrem Besitz befindliche Kopie) kompromittiert wurde.

Sie können Ihren Mandantenschlüssel neu vergeben, indem Sie den Microsoft-Kundendienst (CSS) anrufen und nachweisen, dass Sie der Mandantenadministrator sind.

Wenn Sie Ihren Mandantenschlüssel neu vergeben, wird neuer Inhalt unter Verwendung des neuen Mandantenschlüssels geschützt. Dies geschieht in einer gestaffelten Weise, sodass für einen gewissen Zeitraum neue Inhalte noch teilweise durch den alten Mandantenschlüssel geschützt sind. Zuvor geschützte Inhalte bleiben durch den alten Mandantenschlüssel geschützt. Um dieses Szenario zu unterstützen, behält Azure RMS Ihren alten Mandantenschlüssel bei, damit es Lizenzen für alte Inhalte erteilen kann.

## Sicherung und Wiederherstellung Ihres Mandantenschlüssels
Microsoft ist für die Sicherung Ihres Mandantenschlüssels verantwortlich, sodass von Ihnen keine weitere Aktion erforderlich ist.

## Exportieren Ihres Mandantenschlüssels
Sie können Ihre Azure RMS-Konfiguration und den Mandantenschlüssel anhand der folgenden Anleitung mit diesen drei Schritten exportieren:

### Schritt 1: Initiieren des Exports

-   Wenden Sie sich hierfür an den Microsoft-Kundendienst (CSS), um eine **Azure Rights Management-Supportanfrage mit einer Anforderung eines Azure RMS-Schlüsselexports** zu öffnen. Sie müssen nachweisen, dass Sie der Administrator Ihres Azure RMS-Mandanten sind; beachten Sie, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Dabei fallen die Standardgebühren für Support an; das Exportieren Ihres Mandatenschlüssels ist keine kostenfreie Supportleistung.

### Schritt 2: Warten auf Überprüfung

-   Microsoft überprüft, ob Ihre Anfrage zum Freigeben Ihres RMS-Mandantenschlüssels legitim ist. Der Vorgang kann bis zu drei Wochen dauern.

### Schritt 3: Erhalten von Schlüsselanweisungen vom Kundendienst (CSS)

-   Der Microsoft-Kundendienst (CSS) sendet Ihren Ihre Azure RMS-Konfiguration und den Mandantenschlüssel als verschlüsselte, kennwortgeschützte Datei mit der Dateinamenerweiterung „TPD“ zu. Hierzu sendet Ihnen (als der Person, die den Export initiiert hat) der Kundendienst zuerst per E-Mail ein Tool. Sie müssen das Tool wie folgt an einer Eingabeaufforderung ausführen:

    ```
    AadrmTpd.exe -createkey
    ```
    Hierdurch wird ein RSA-Schlüsselpaar generiert, und die öffentliche und private Hälfte wird jeweils als Datei im aktuellen Ordner gespeichert. Beispiel: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** und **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Antworten Sie auf die E-Mail des Kundendiensts, indem Sie die Datei mit dem Namen anfügen, der mit **PublicKey** beginnt. Der Kundendienst sendet Ihnen als Nächstes eine TPD-Datei als XML-Datei, die mit Ihrem RSA-Schlüssel verschlüsselt ist. Kopieren Sie diese Datei in den Ordner, in dem Sie das Tool „AadrmTpd“ ursprünglich ausgeführt haben, und führen Sie das Tool erneut aus, wobei Sie Ihre Datei, die mit **PrivateKey** beginnt, und die Datei vom Kundendienst verwenden. Beispiel:

    ```
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```
    Die Ausgabe dieses Befehls sollte aus zwei Dateien bestehen: Eine enthält das Klartextkennwort für die kennwortgeschützte TPD-Datei und die andere die kennwortgeschützte TPD-Datei selbst. Zu Querverweiszwecken sollten beide dieselbe GUID wie die öffentliche und die private Schlüsseldatei haben, als Sie den Befehl „AadrmTpd.exe -createkey“ ausgeführt haben:

    -   Password-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt

    -   ExportedTPD-FA29D0FE-5049-4C8E-931B-96C6152B0441.xml

    Sichern Sie diese Dateien, und speichern Sie sie sicher, um zu gewährleisten, dass Sie weiterhin Inhalte entschlüsseln können, die mit diesem Mandantenschlüssel geschützt wurden. Zusätzlich können Sie, wenn Sie zu AD RMS migrieren, diese TPD-Datei (die Datei, die mit **ExportedTDP** beginnt) in Ihren AD RMS-Server importieren.

### Schritt 4: Fortlaufend: Schützen Ihres Mandantenschlüssels

-   Nachdem Sie Ihren Mandantenschlüssel erhalten haben, bewahren Sie ihn sicher auf, weil jede Person, die darauf zugreifen kann, alle Dokumente entschlüsseln kann, die mithilfe dieses Schlüssels geschützt werden.

    Wenn der Grund für das Exportieren Ihres Mandantenschlüssels darin besteht, dass Sie Azure RMS nicht mehr verwenden möchten, sollten Sie als bewährte Methode Ihren RMS-Mandanten nun deaktivieren. Führen Sie diesen Vorgang unmittelbar nach dem Erhalt des Mandantenschlüssels aus, weil diese Vorsichtsmaßnahme die möglichen Konsequenzen minimiert, wenn auf Ihren Mandantenschlüssel durch eine Person zugegriffen wird, die nicht über diesen Schlüssel verfügen sollte. Eine Anleitung finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md).

## Reaktion auf eine Sicherheitsverletzung
Kein Sicherheitssystem, egal wie stark es ist, kommt vollständig ohne einen Prozess für Reaktion auf eine Sicherheitsverletzung aus. Ihr Mandantenschlüssel könnte kompromittiert oder gestohlen werden. Auch wenn er gut geschützt ist, können Sicherheitslücken in der HSM-Technologie der aktuellen Generation oder bei aktuellen Schlüssellängen und Algorithmen gefunden werden.

Microsoft hat ein dediziertes Team, um auf Sicherheitsvorfälle bei eigenen Produkten und Diensten zu reagieren. Sobald ein glaubhafter Bericht über einen Vorfall vorliegt, kümmert sich dieses Team um die Untersuchung des Umfangs, der Ursache und um Abhilfen. Wenn sich dieser Vorfall auf Ihre Objekte auswirkt, wird Ihr Azure RMS-Mandantenadministrator per E-Mail von Microsoft unter der Adresse benachrichtig, die Sie beim Abschluss des Abonnements angegeben haben.

Wenn bei Ihnen eine Sicherheitsverletzung aufgetreten ist, hängt die beste Vorgehensweise auf Ihrer und auf Microsofts Seite vom Umfang der Sicherheitsverletzung ab. Microsoft führt diesen Prozess gemeinsam mit Ihnen durch. In der folgenden Tabelle finden Sie einige typische Situationen und die wahrscheinliche Reaktion darauf, obgleich die exakte Reaktion immer von allen Informationen abhängt, die im Rahmen der Untersuchung gewonnen werden.

|Beschreibung des Vorfalls|Wahrscheinliche Reaktion|
|------------------------|-------------------|
|Ihr Mandantenschlüssel wurde abgegriffen.|Vergeben Sie Ihren Mandantenschlüssel neu. Weitere Informationen finden Sie im Abschnitt [Neuvergabe (Rollover) Ihres Mandantenschlüssels](operations-tenant-key.md#re-key-your-tenant-key) in diesem Artikel.|
|Eine nicht autorisierte Person oder Schadsoftware hat Rechte zur Verwendung Ihres Mandantenschlüssels erlangt, aber nicht den Schlüssel selbst.|Die Neuvergabe (Rollover) Ihres Mandantenschlüssels schafft hierbei keine Abhilfe und erfordert eine Ursachenanalyse. Wenn ein Prozess- oder Softwarefehler dafür verantwortlich war, dass die nicht autorisierte Person Zugriff erlangt hat, muss dieser Zustand behoben werden.|
|Im RSA-Algorithmus oder bei der Schlüssellänge entdeckte Sicherheitslücken oder auch Brute-Force-Angriffe werden von der Rechenleistung her möglich.|Microsoft muss den Azure RMS so aktualisieren, dass neue Algorithmen und längere Schlüssellängen unterstützt werden, die robust sind, und alle Kunden anweisen, ihre Mandantenschlüssel zu erneuern.|




<!--HONumber=Jun16_HO1-->


