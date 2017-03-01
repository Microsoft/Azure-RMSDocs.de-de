---
title: "Von Microsoft verwaltet – Lebenszyklusvorgänge für AIP-Mandantenschlüssel"
description: "Informationen zu den Lebenszyklusvorgängen, die relevant sind, wenn Ihr Mandantenschlüssel für Azure Information Protection von Microsoft verwaltet wird (Standard)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: caacc4174ddb63e9c9091c0df294b93cf947a7c4
ms.lasthandoff: 02/24/2017


---


# <a name="microsoft-managed-tenant-key-lifecycle-operations"></a>Von Microsoft verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel

>*Gilt für: Azure Information Protection, Office 365*

Wenn Ihr Mandantenschlüssel für Azure Information Protection von Microsoft verwaltet wird (Standard), finden Sie in den folgenden Abschnitten weitere Informationen zu den Lebenszyklusvorgängen, die für diese Topologie relevant sind.

## <a name="revoke-your-tenant-key"></a>Widerrufen Ihres Mandantenschlüssels
Wenn Sie Ihr Abonnement für Azure Information Protection kündigen, wird Ihr Mandantenschlüssel in Azure Information Protection nicht mehr verwendet. Es ist keine weitere Aktion erforderlich.

## <a name="re-key-your-tenant-key"></a>Neuvergabe (Rollover) Ihres Mandantenschlüssels
Die Neuvergabe Ihres Schlüssels wird auch als „Rollover“ bezeichnet. Führen Sie eine Neuvergabe Ihres Mandantenschlüssels nur durch, wenn es wirklich notwendig ist. Ältere Clients wie Office 2010 wurden nicht darauf ausgelegt, problemlos mit Schlüsseländerungen umzugehen. In diesem Szenario müssen Sie den Rights Management-Status auf Computern löschen, indem Sie eine Gruppenrichtlinie oder einen entsprechenden Mechanismus verwenden. Es gibt jedoch einige berechtigte Ereignisse, die Sie zwingen können, Ihren Mandantenschlüssel neu zu vergeben. Beispiel:

-   Ihr Unternehmen wurde in zwei oder mehr Unternehmen aufgeteilt. Wenn Sie Ihren Mandantenschlüssel neu vergeben, hat das neue Unternehmen keinen Zugriff auf neue Inhalte, die von Ihren Mitarbeitern veröffentlicht werden. Sie können auf den alten Inhalt zugreifen, wenn sie eine Kopie des alten Mandantenschlüssels besitzen.

-   Sie glauben, dass die Masterkopie Ihres Mandantenschlüssels (die in Ihrem Besitz befindliche Kopie) kompromittiert wurde.

Sie können Ihren Mandantenschlüssel erneuern, indem Sie sich an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support) wenden und eine **Azure Information Protection-Supportanfrage öffnen, um die Neuvergabe Ihres Azure Information Protection-Mandantenschlüssels anzufordern**. Sie müssen nachweisen, dass Sie der Administrator Ihres Azure Information Protection-Mandanten sind. Beachten Sie jedoch, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Dabei fallen die Standardgebühren für Support an. Die Neuvergabe Ihres Mandantenschlüssels ist keine kostenfreie Supportleistung.

Wenn Sie Ihren Mandantenschlüssel neu vergeben, wird neuer Inhalt unter Verwendung des neuen Mandantenschlüssels geschützt. Dies geschieht in einer gestaffelten Weise, sodass für einen gewissen Zeitraum neue Inhalte noch teilweise durch den alten Mandantenschlüssel geschützt sind. Zuvor geschützte Inhalte bleiben durch den alten Mandantenschlüssel geschützt. Zur Unterstützung dieses Szenarios wird Ihr alter Mandantenschlüssel in Azure Information Protection beibehalten, damit Lizenzen für alte Inhalte erteilt werden können.

## <a name="backup-and-recover-your-tenant-key"></a>Sicherung und Wiederherstellung Ihres Mandantenschlüssels
Microsoft ist für die Sicherung Ihres Mandantenschlüssels verantwortlich, sodass von Ihnen keine weitere Aktion erforderlich ist.

## <a name="export-your-tenant-key"></a>Exportieren Ihres Mandantenschlüssels
Sie können Ihre Azure Information Protection-Konfiguration und den Mandantenschlüssel anhand der Anweisungen mit den folgenden drei Schritten exportieren:

### <a name="step-1-initiate-export"></a>Schritt 1: Initiieren des Exports

-   Wenden Sie sich hierfür an den [Microsoft Support](../get-started/information-support.md#to-contact-microsoft-support), und öffnen Sie eine **Azure Information Protection-Supportanfrage zur Anforderung eines Azure Information Protection-Schlüsselexports**. Sie müssen nachweisen, dass Sie der Administrator Ihres Azure Information Protection-Mandanten sind. Beachten Sie jedoch, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Dabei fallen die Standardgebühren für Support an; das Exportieren Ihres Mandatenschlüssels ist keine kostenfreie Supportleistung.

### <a name="step-2-wait-for-verification"></a>Schritt 2: Warten auf Überprüfung

-   Microsoft überprüft, ob Ihre Anforderung zum Freigeben Ihres Azure Information Protection-Mandantenschlüssels legitim ist. Der Vorgang kann bis zu drei Wochen dauern.

### <a name="step-3-receive-key-instructions-from-css"></a>Schritt 3: Erhalten von Schlüsselanweisungen vom Kundendienst (CSS)

-   Microsoft Customer Support Services (CSS) sendet Ihren Ihre Azure Information Protection-Konfiguration und den Mandantenschlüssel als verschlüsselte, kennwortgeschützte Datei mit der Dateierweiterung „.tpd“ zu. Hierzu sendet Ihnen (als der Person, die den Export initiiert hat) der Kundendienst zuerst per E-Mail ein Tool. Sie müssen das Tool wie folgt an einer Eingabeaufforderung ausführen:

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

### <a name="step-4-ongoing-protect-your-tenant-key"></a>Schritt 4: Fortlaufend: Schützen Ihres Mandantenschlüssels

-   Nachdem Sie Ihren Mandantenschlüssel erhalten haben, bewahren Sie ihn sicher auf, weil jede Person, die darauf zugreifen kann, alle Dokumente entschlüsseln kann, die mithilfe dieses Schlüssels geschützt werden.

    Wenn der Grund für das Exportieren Ihres Mandantenschlüssels darin liegt, dass Sie Azure Information Protection nicht mehr verwenden möchten, sollten Sie als bewährte Methode den Azure Rights Management-Dienst von Ihrem Azure Information Protection-Mandanten nun deaktivieren. Führen Sie diesen Vorgang unmittelbar nach dem Erhalt des Mandantenschlüssels aus, weil diese Vorsichtsmaßnahme die möglichen Konsequenzen minimiert, wenn auf Ihren Mandantenschlüssel durch eine Person zugegriffen wird, die nicht über diesen Schlüssel verfügen sollte. Eine Anleitung finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md).

## <a name="respond-to-a-breach"></a>Reaktion auf eine Sicherheitsverletzung
Kein Sicherheitssystem, egal wie stark es ist, kommt vollständig ohne einen Prozess für Reaktion auf eine Sicherheitsverletzung aus. Ihr Mandantenschlüssel könnte kompromittiert oder gestohlen werden. Auch wenn er gut geschützt ist, können Sicherheitslücken in der HSM-Technologie der aktuellen Generation oder bei aktuellen Schlüssellängen und Algorithmen gefunden werden.

Microsoft hat ein dediziertes Team, um auf Sicherheitsvorfälle bei eigenen Produkten und Diensten zu reagieren. Sobald ein glaubhafter Bericht über einen Vorfall vorliegt, kümmert sich dieses Team um die Untersuchung des Umfangs, der Ursache und um Abhilfen. Wenn sich dieser Vorfall auf Ihre Objekte auswirkt, wird Ihr Azure Information Protection-Mandantenadministrator per E-Mail von Microsoft unter der Adresse benachrichtigt, die Sie beim Abschluss des Abonnements angegeben haben.

Wenn bei Ihnen eine Sicherheitsverletzung aufgetreten ist, hängt die beste Vorgehensweise auf Ihrer und auf Microsofts Seite vom Umfang der Sicherheitsverletzung ab. Microsoft führt diesen Prozess gemeinsam mit Ihnen durch. In der folgenden Tabelle finden Sie einige typische Situationen und die wahrscheinliche Reaktion darauf, obgleich die exakte Reaktion immer von allen Informationen abhängt, die im Rahmen der Untersuchung gewonnen werden.

|Beschreibung des Vorfalls|Wahrscheinliche Reaktion|
|------------------------|-------------------|
|Ihr Mandantenschlüssel wurde abgegriffen.|Vergeben Sie Ihren Mandantenschlüssel neu. Weitere Informationen finden Sie im Abschnitt [Neuvergabe (Rollover) Ihres Mandantenschlüssels](operations-microsoft-managed-tenant-key.md#re-key-your-tenant-key) in diesem Artikel.|
|Eine nicht autorisierte Person oder Schadsoftware hat Rechte zur Verwendung Ihres Mandantenschlüssels erlangt, aber nicht den Schlüssel selbst.|Die Neuvergabe (Rollover) Ihres Mandantenschlüssels schafft hierbei keine Abhilfe und erfordert eine Ursachenanalyse. Wenn ein Prozess- oder Softwarefehler dafür verantwortlich war, dass die nicht autorisierte Person Zugriff erlangt hat, muss dieser Zustand behoben werden.|
|Im RSA-Algorithmus oder bei der Schlüssellänge entdeckte Sicherheitslücken oder auch Brute-Force-Angriffe werden von der Rechenleistung her möglich.|Microsoft muss Azure Information Protection so aktualisieren, dass neue, robuste Algorithmen und längere Schlüssellängen unterstützt werden, und alle Kunden anweisen, ihre Mandantenschlüssel zu erneuern.|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


