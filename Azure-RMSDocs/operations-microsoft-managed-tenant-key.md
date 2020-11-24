---
title: 'Von Microsoft verwaltet: Lebenszyklusvorgänge für AIP-Mandantenschlüssel'
description: Informationen zu den Lebenszyklusvorgängen, die relevant sind, wenn Ihr Mandantenschlüssel für Azure Information Protection von Microsoft verwaltet wird (Standard).
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 10/23/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 3c48cda6-e004-4bbd-adcf-589815c56c55
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 5121fb6acac65b5325376a047bfbfa40279619f0
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567622"
---
# <a name="microsoft-managed-tenant-key-life-cycle-operations"></a>Von Microsoft verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Wenn Ihr Mandantenschlüssel für Azure Information Protection von Microsoft verwaltet wird (Standard), finden Sie in den folgenden Abschnitten weitere Informationen zu den Lebenszyklusvorgängen, die für diese Topologie relevant sind.

## <a name="revoke-your-tenant-key"></a>Widerrufen Ihres Mandantenschlüssels
Wenn Sie Ihr Abonnement für Azure Information Protection kündigen, wird Ihr Mandantenschlüssel in Azure Information Protection nicht mehr verwendet. Es ist keine weitere Aktion erforderlich.

## <a name="rekey-your-tenant-key"></a>Neuerstellung Ihres Mandantenschlüssels
Die Neuerstellung eines Schlüssels wird auch als „Rollover“ bezeichnet. Wenn Sie diesen Vorgang ausführen, verwendet Azure Information Protection nicht mehr den vorhandenen Mandantenschlüssel zum Schützen von Dokumenten und E-Mails sondern einen anderen Schlüssel. Richtlinien und Vorlagen werden umgehend erneut signiert. Diese Umstellung erfolgt jedoch gestaffelt für vorhandene Kunden und Dienste, die Azure Information Protection verwenden. Daher werden neue Inhalte eine Zeit lang noch durch den alten Mandantenschlüssel geschützt.

Um einen neuen Schlüssel zu erstellen, müssen Sie das Mandantenschlüsselobjekt konfigurieren und den alternativen Schlüssel angeben, der verwendet werden soll. Anschließend wird der zuvor verwendete Schlüssel für Azure Information Protection automatisch als archiviert gekennzeichnet. Diese Konfiguration stellt sicher, dass der Inhalt, der mithilfe dieses Schlüssels geschützt wurde, weiterhin zugänglich ist.

Beispiele für Fälle, in denen Sie möglicherweise einen neuen Schlüssel für Azure Information Protection erstellen müssen:

- Sie haben die Migration von Active Directory Rights Management Services (AD RMS) mithilfe eines Schlüssels für den Kryptografiemodus 1 durchgeführt. Wenn die Migration abgeschlossen ist, sollten Sie einen Schlüssel verwenden, der den Kryptografiemodus 2 verwendet.

- Ihr Unternehmen wurde in zwei oder mehr Unternehmen aufgeteilt. Wenn Sie Ihren Mandantenschlüssel neu erstellen, hat das neue Unternehmen keinen Zugriff auf neue Inhalte, die von Ihren Mitarbeitern veröffentlicht werden. Sie können auf den alten Inhalt zugreifen, wenn sie eine Kopie des alten Mandantenschlüssels besitzen.

- Sie möchten eine andere Schlüsselverwaltungstopologie verwenden.

- Sie glauben, dass die Masterkopie Ihres Mandantenschlüssels kompromittiert wurde.

Zum Erstellen eines neuen Schlüssels können Sie einen anderen von Microsoft verwalteten Schlüssel als Mandantenschlüssel auswählen, jedoch keinen neuen von Microsoft verwalteten Schlüssel erstellen. Um einen neuen Schlüssel zu erstellen, müssen Sie Ihre Mandantenschlüsseltopologie so ändern, dass sie vom Kunden verwaltet wird (BYOK).

Sie verfügen über mehr als einen von Microsoft verwalteten Schlüssel, wenn Sie eine Migration von Active Directory Rights Management Services (AD RMS) durchgeführt und die Topologie für von Microsoft verwaltete Schlüssel für Azure Information Protection ausgewählt haben. In diesem Szenario verfügen Sie über mindestens zwei von Microsoft verwaltete Schlüssel für Ihren Mandanten. Sie haben mindestens einen Schlüssel aus AD Rights Management Services importiert. Sie verfügen auch über den Standardschlüssel, der automatisch für Ihren Azure Information Protection-Mandanten erstellt wurde.

Um einen anderen Schlüssel als aktiven Mandanten Schlüssel für Azure Information Protection auszuwählen, verwenden Sie das Cmdlet [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) aus dem aipservice-Modul. Verwenden Sie das Cmdlet [Get-aipservicekeys](/powershell/module/aipservice/get-aipservicekeys) , um Ihnen die Identifizierung des zu verwendenden Schlüssels zu erleichtern. Sie können den Standardschlüssel identifizieren, der automatisch für Ihren Azure Information Protection-Mandanten erstellt wurde, indem Sie den folgenden Befehl ausführen:

```ps
(Get-AipServiceKeys) | Sort-Object CreationTime | Select-Object -First 1
```

Informationen zum Ändern der Schlüssel Topologie in eine vom Kunden verwaltete (Byok) finden Sie unter [Planen und Implementieren Ihres Azure Information Protection Mandanten Schlüssels](plan-implement-tenant-key.md).

## <a name="backup-and-recover-your-tenant-key"></a>Sicherung und Wiederherstellung Ihres Mandantenschlüssels
Microsoft ist für die Sicherung Ihres Mandantenschlüssels verantwortlich, sodass von Ihnen keine weitere Aktion erforderlich ist.

## <a name="export-your-tenant-key"></a>Exportieren Ihres Mandantenschlüssels
Sie können Ihre Azure Information Protection-Konfiguration und den Mandantenschlüssel anhand der Anweisungen mit den folgenden drei Schritten exportieren:

### <a name="step-1-initiate-export"></a>Schritt 1: Initiieren des Exports

- [Wenden Sie sich hierfür an den Microsoft-Support](information-support.md#to-contact-microsoft-support), und öffnen Sie eine **Azure Information Protection-Supportanfrage zur Anforderung eines Azure Information Protection-Schlüsselexports**. Sie müssen nachweisen, dass Sie ein globaler Administrator für Ihren Mandanten sind, und wissen, dass dieser Vorgang einige Tage dauert, um zu bestätigen. Dabei fallen Standardsupportgebühren an. Das Exportieren Ihres Mandantenschlüssels ist keine kostenfreie Supportleistung.

### <a name="step-2-wait-for-verification"></a>Schritt 2: Warten auf Überprüfung

- Microsoft überprüft, ob Ihre Anforderung zum Freigeben Ihres Azure Information Protection-Mandantenschlüssels legitim ist. Der Vorgang kann bis zu drei Wochen dauern.

### <a name="step-3-receive-key-instructions-from-css"></a>Schritt 3: Erhalten von Schlüsselanweisungen vom Kundendienst (CSS)

- Microsoft Customer Support Services (CSS) sendet Ihren Ihre Azure Information Protection-Konfiguration und den Mandantenschlüssel verschlüsselt in einer kennwortgeschützten Datei zu. Diese Datei hat die Dateierweiterung **TPD**. Hierzu sendet Ihnen (als der Person, die den Export initiiert hat) der Kundendienst zuerst per E-Mail ein Tool. Sie müssen das Tool wie folgt an einer Eingabeaufforderung ausführen:

    ```ps
    AadrmTpd.exe -createkey
    ```

    Hierdurch wird ein RSA-Schlüsselpaar generiert, und die öffentliche und private Hälfte wird jeweils als Datei im aktuellen Ordner gespeichert. Beispiel: **PublicKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt** und **PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt**.

    Antworten Sie auf die E-Mail des Kundendiensts, indem Sie die Datei mit dem Namen, der mit **PublicKey** beginnt, anfügen. CSS sendet Ihnen als Nächstes eine TPD-Datei als XML-Datei, die mit Ihrem RSA-Schlüssel verschlüsselt ist. Kopieren Sie diese Datei in den Ordner, in dem Sie das Tool „AadrmTpd“ ursprünglich ausgeführt haben, und führen Sie das Tool erneut aus, wobei Sie Ihre Datei, die mit **PrivateKey** beginnt, und die Datei vom Kundendienst verwenden. Beispiel:

    ```ps
    AadrmTpd.exe -key PrivateKey-FA29D0FE-5049-4C8E-931B-96C6152B0441.txt -target TPD-77172C7B-8E21-48B7-9854-7A4CEAC474D0.xml
    ```

    Die Ausgabe dieses Befehls sollte aus zwei Dateien bestehen: Eine enthält das Klartextkennwort für die kennwortgeschützte TPD-Datei, die andere ist die kennwortgeschützte TPD-Datei selbst. Die Dateien weisen eine neue GUID auf, z.B.:
     
  - Password-5E4C2018-8C8C-4548-8705-E3218AA1544E.txt

  - ExportedTPD-5E4C2018-8C8C-4548-8705-E3218AA1544E.xml

    Sichern Sie diese Dateien, und speichern Sie sie an einer sicheren Stelle, um zu gewährleisten, dass Sie weiterhin Inhalte entschlüsseln können, die mit diesem Mandantenschlüssel geschützt wurden. Zusätzlich können Sie, wenn Sie zu AD RMS migrieren, diese TPD-Datei (die Datei, die mit **ExportedTDP** beginnt) in Ihren AD RMS-Server importieren.

### <a name="step-4-ongoing-protect-your-tenant-key"></a>Schritt 4: Fortlaufend: Schützen Ihres Mandantenschlüssels

Nachdem Sie Ihren Mandantenschlüssel erhalten haben, bewahren Sie ihn sicher auf, weil jede Person, die darauf zugreifen kann, alle Dokumente entschlüsseln kann, die mithilfe dieses Schlüssels geschützt werden.

Wenn der Grund für das Exportieren Ihres Mandantenschlüssels darin liegt, dass Sie Azure Information Protection nicht mehr verwenden möchten, sollten Sie als bewährte Methode den Azure Rights Management-Dienst von Ihrem Azure Information Protection-Mandanten nun deaktivieren. Führen Sie diesen Vorgang unmittelbar nach dem Erhalt des Mandantenschlüssels aus, weil diese Vorsichtsmaßnahme die möglichen Konsequenzen minimiert, wenn auf Ihren Mandantenschlüssel durch eine Person zugegriffen wird, die nicht über diesen Schlüssel verfügen sollte. Anweisungen hierzu finden Sie unter Außerbetriebsetzen [und Deaktivieren von Azure-Rights Management](decommission-deactivate.md).

## <a name="respond-to-a-breach"></a>Reaktion auf eine Sicherheitsverletzung
Kein Sicherheitssystem, egal wie stark es ist, kommt vollständig ohne einen Prozess für Reaktion auf eine Sicherheitsverletzung aus. Ihr Mandantenschlüssel könnte kompromittiert oder gestohlen werden. Auch wenn er gut geschützt ist, können Sicherheitslücken in der Schlüsseltechnologie der aktuellen Generation oder bei aktuellen Schlüssellängen und Algorithmen auftreten.

Microsoft hat ein dediziertes Team, um auf Sicherheitsvorfälle bei eigenen Produkten und Diensten zu reagieren. Sobald ein glaubhafter Bericht über einen Vorfall vorliegt, kümmert sich dieses Team um die Untersuchung des Umfangs, der Ursache und um Abhilfen. Wenn sich dieser Vorfall auf Ihre Assets auswirkt, werden die globalen Administratoren von Microsoft per e-Mail benachrichtigt.

Wenn bei Ihnen eine Sicherheitsverletzung aufgetreten ist, hängt die beste Vorgehensweise auf Ihrer und auf Microsofts Seite vom Umfang der Sicherheitsverletzung ab. Microsoft führt diesen Prozess gemeinsam mit Ihnen durch. In der folgenden Tabelle finden Sie einige typische Situationen und die wahrscheinliche Reaktion darauf, obgleich die exakte Reaktion immer von allen Informationen abhängt, die im Rahmen der Untersuchung gewonnen werden.

|Beschreibung des Vorfalls|Wahrscheinliche Reaktion|
|------------------------|-------------------|
|Ihr Mandantenschlüssel wurde abgegriffen.|Erstellen Sie Ihren Mandantenschlüssel neu. Weitere Informationen finden Sie im Abschnitt [Neuerstellung Ihres Mandantenschlüssels](#rekey-your-tenant-key) in diesem Artikel.|
|Eine nicht autorisierte Person oder Schadsoftware hat Rechte zur Verwendung Ihres Mandantenschlüssels erlangt, aber nicht den Schlüssel selbst.|Die Neuerstellung Ihres Mandantenschlüssels schafft hierbei keine Abhilfe, stattdessen ist eine Ursachenanalyse erforderlich. Wenn ein Prozess- oder Softwarefehler dafür verantwortlich war, dass die nicht autorisierte Person Zugriff erlangt hat, muss dieser Zustand behoben werden.|
|Im RSA-Algorithmus oder bei der Schlüssellänge entdeckte Sicherheitslücken oder auch Brute-Force-Angriffe werden von der Rechenleistung her möglich.|Microsoft muss Azure Information Protection so aktualisieren, dass neue, robuste Algorithmen und längere Schlüssellängen unterstützt werden, und alle Kunden anweisen, ihre Mandantenschlüssel neu zu erstellen.|
| | |