---
title: Ausführen des Azure Information Protection Unified Bezeichnung Scanner (AIP)
description: Anweisungen zum Ausführen des Azure Information Protection Unified-Beschriftungs Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/25/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e6dcad16cdcb2c2d00277ce94b9cf4ab5db94227
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86049535"
---
# <a name="running-the-azure-information-protection-scanner"></a>Ausführen des Azure Information Protection Scanners

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*

>[!NOTE]
> Wenn Sie den klassischen Scanner verwenden, finden Sie weitere Informationen unter [Installieren und Konfigurieren des Azure Information Protection klassischen Scanner](deploy-aip-scanner-configure-install-classic.md).

Nachdem Sie die [Systemanforderungen](deploy-aip-scanner-prereqs.md) bestätigt und [Ihren Scanner konfiguriert und installiert](deploy-aip-scanner-configure-install.md)haben, [führen Sie einen Ermittlungs Scan](#run-a-discovery-cycle-and-view-reports-for-the-scanner) aus, um zu beginnen.

Verwenden Sie die unten aufgeführten Schritte, um Ihre Scans zu verwalten.

- [Einen Scanvorgang abbrechen](#stopping-a-scan)
- [Dateien werden neu berechnet](#rescanning-files)
- [Problembehandlung bei einem beendeten Scan](#troubleshooting-a-stopped-scan)
- [Problembehandlung mithilfe des Scanner-Diagnosetools](#troubleshooting-using-the-scanner-diagnostic-tool)

Weitere Informationen finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Ausführen eines Ermittlungszyklus und Anzeigen von Berichten für die Überprüfung

Gehen Sie wie folgt vor, nachdem Sie [Ihren Scanner konfiguriert und installiert](deploy-aip-scanner-configure-install.md) haben, um ein ursprüngliches Verständnis ihrer Inhalte zu erhalten.

Führen Sie diese Schritte nach Bedarf erneut aus, wenn sich Ihre Inhalte ändern.

1. Wählen Sie im Azure-Portal im Bereich **Azure Information Protection-Inhalts Scan** Aufträge ihre Inhalts Scanaufträge aus, und wählen Sie dann die Option **jetzt** überprüfen aus:

    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

    Führen Sie alternativ in der PowerShell-Sitzung den folgenden Befehl aus:

    ```ps
    Start-AIPScan
    ```

1. Warten Sie, bis die Überprüfung den Zyklus abgeschlossen hat. Die Überprüfung ist abgeschlossen, wenn der Scanner alle Dateien in den angegebenen Daten speichern durchlaufen hat.

    Führen Sie einen der folgenden Schritte aus, um den Überprüfungs Fortschritt zu überwachen

    - **Aktualisieren Sie die Scanaufträge.**  Wählen Sie im Bereich **Azure Information Protection-Inhalts Scanaufträge** die Option **Aktualisieren**aus.

        Warten Sie, bis die Werte für die Spalte **Letzte Scanergebnisse** und die Spalte Letzte Überprüfung **(Endzeit)** angezeigt werden.

    - **Verwenden Sie einen PowerShell-Befehl.** Führen `Get-AIPScannerStatus` Sie aus, um die Statusänderung zu überwachen.

1. Überprüfen Sie nach Abschluss der Überprüfung die im Verzeichnis ** % *LocalAppData*% \ microsoft\msip\scanner\reports** gespeicherten Berichte.

    - Die TXT-Zusammenfassungsdateien enthalten die zum Überprüfen benötigte Zeit, die Anzahl der überprüften Dateien sowie die Anzahl der Dateien mit übereinstimmenden Informationstypen.

    - Die CSV-Dateien enthalten mehr Details zu den einzelnen Dateien. In diesem Ordner werden für jeden Scanzyklus bis zu 60 Berichte gespeichert, die bis auf den letzten alle komprimiert werden, um die Speicherplatzbelegung zu minimieren.

[Anfängliche Konfigurationen](deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal) weisen Sie an, die zu **ermittelnden Informationstypen** nur für die **Richtlinie**festzulegen. Diese Konfiguration bedeutet, dass nur Dateien, die die Bedingungen erfüllen, die Sie für die automatische Klassifizierung konfiguriert haben, in den ausführlichen Berichten enthalten sind.

Wenn keine Bezeichnungen angewendet werden, überprüfen Sie, ob die Bezeichnungs Konfiguration eine automatische anstelle der empfohlenen Klassifizierung enthält, oder aktivieren Sie die Option **Empfohlene Bezeichnung als automatisch** aktivieren (verfügbar in Scanner Version 2.7. x. x und höher).

Wenn die Ergebnisse immer noch nicht erwartungsgemäß sind, müssen Sie möglicherweise die Bedingungen, die Sie für ihre Bezeichnungen festgelegt haben, neu konfigurieren. Wenn dies der Fall ist, konfigurieren Sie die Bedingungen nach Bedarf neu, und wiederholen Sie diesen Vorgang, bis Sie mit den Ergebnissen zufrieden sind. Aktualisieren Sie anschließend die Konfiguration automatisch und optional den Schutz.

### <a name="viewing-updates-in-the-azure-portal"></a>Anzeigen von Updates in der Azure-Portal

Diese Informationen werden von den Scannern alle fünf Minuten an Azure Information Protection gesendet, sodass Sie die Ergebnisse nahezu in Echtzeit in der Azure-Portal anzeigen können. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md).

Das Azure-Portal zeigt nur Informationen zur letzten Überprüfung an. Wenn Sie die Ergebnisse vorheriger Überprüfungen anzeigen müssen, sehen Sie sich die Berichte an, die auf dem Überprüfungscomputer im Ordner „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“ gespeichert sind.

### <a name="changing-log-levels-or-locations"></a>Ändern von Protokoll Ebenen oder-Speicherorten

Ändern Sie die Protokollierungsebene, indem Sie den *Report Level* -Parameter mit [Set-aipscannerconfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration)verwenden.

Der Speicherort oder Name des Berichts Ordners kann nicht geändert werden. Wenn Sie Berichte an einem anderen Speicherort speichern möchten, sollten Sie die Verwendung einer Verzeichnis Verknüpfung für den Ordner in Erwägung gezogen.

Verwenden Sie z. b. den Befehl " [mklink](/windows-server/administration/windows-commands/mklink) ":`mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`

Wenn Sie diese Schritte nach der Erstkonfiguration und-Installation durchgeführt haben, fahren Sie mit [Konfigurieren des Scanners fort, um Klassifizierung und Schutz anzuwenden](deploy-aip-scanner-configure-install.md#configure-the-scanner-to-apply-classification-and-protection).

## <a name="stopping-a-scan"></a>Beenden einer Überprüfung

Verwenden Sie eine der folgenden Methoden, um einen aktuell laufenden Scanvorgang zu beenden:

- **Azure-Portal.** Wählen Sie **Scan**Vorgang:

    ![Beendet eine Überprüfung für den Azure Information Protection Scanner.](./media/scanner-stop-scan.png)

- **Führen Sie einen PowerShell-Befehl aus.** Führen Sie den folgenden Befehl aus:

    ```ps
    Stop-AIPScan 
    ```

## <a name="rescanning-files"></a>Dateien werden neu berechnet

Beim [ersten Scan](#run-a-discovery-cycle-and-view-reports-for-the-scanner)Vorgang prüft der Scanner alle Dateien in den konfigurierten Daten speichern. Bei nachfolgenden Scans werden nur neue oder geänderte Dateien überprüft.

Die erneute Überprüfung aller Dateien ist in der Regel hilfreich, wenn Sie möchten, dass die Berichte alle Dateien einschließen und der Scanner im Ermittlungs Modus ausgeführt wird.

Führen Sie eine neue Überprüfung aller Dateien mit einer der folgenden Methoden aus:

- [Manuelles Ausführen eines vollständigen erneuten Scans](#manually-run-a-full-rescan)
- [Durch Aktualisieren der Richtlinie eine vollständige erneute Überprüfung auslöst](#trigger-a-full-rescan-by-refreshing-the-policy)

### <a name="manually-run-a-full-rescan"></a>Manuelles Ausführen eines vollständigen erneuten Scans

Erzwingen Sie, dass die Überprüfung alle Dateien nach Bedarf erneut aus dem Bereich **Azure Information Protection-Inhalts Scanaufträge** in der Azure-Portal prüft.

Wählen Sie den Auftrag für die Inhalts Überprüfung aus der Liste aus, und wählen Sie dann die Option **alle Dateien neu** Einlesen aus:

![Initiieren eines erneuten Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-rescan-files.png)

Wenn eine vollständige Überprüfung durchgeführt wird, wird der Überprüfungstyp automatisch in inkrementell geändert, sodass bei nachfolgenden Scans nur neue oder geänderte Dateien erneut gescannt werden.

### <a name="trigger-a-full-rescan-by-refreshing-the-policy"></a>Durch Aktualisieren der Richtlinie eine vollständige erneute Überprüfung auslöst

Alle Dateien werden auch dann überprüft, wenn der Scanner über neue oder geänderte Einstellungen für die automatische und empfohlene Bezeichnung verfügt. Die Überprüfung aktualisiert die Richtlinie automatisch alle vier Stunden.

Wenn Sie die Richtlinie früher aktualisieren möchten, z. b. beim Testen, löschen Sie den Inhalt des Verzeichnisses **%LocalAppData%\microsoft\msip\mip \\ < *ProcessName*> \mip** , und starten Sie den Azure Information Protection-Dienst neu.

> [!NOTE]
> Wenn Sie auch die Schutzeinstellungen für ihre Bezeichnungen geändert haben, warten Sie beim Speichern der aktualisierten Schutzeinstellungen vor dem Neustart des Azure Information Protection Dienstanbieter weitere 15 Minuten ab.
>

## <a name="troubleshooting-a-stopped-scan"></a>Problembehandlung bei einem beendeten Scan

Wenn der Scanner unerwartet in der Mitte angehalten wird und das Scannen einer großen Anzahl von Dateien in einem Repository nicht durchführt, müssen Sie möglicherweise eine der folgenden Einstellungen ändern:

- **Anzahl der dynamischen Ports**. Möglicherweise müssen Sie die Anzahl der dynamischen Ports für das Betriebssystem erhöhen, das die Dateien gehostet. Ein Grund dafür, warum der Scanner die Anzahl an zulässigen Netzwerkverbindungen überschreitet und daher angehalten wird, ist die Serverhärtung für SharePoint.

    Um zu überprüfen, ob dies die Ursache für die Beendigung des Scanners ist, sollten Sie überprüfen, ob die folgende Fehlermeldung für den Scanner in der Datei ** % *LocalAppData*% \ microsoft\msip\logs\msipscanner.iplog** protokolliert wird.

    **Es kann keine Verbindung mit dem Remote Server hergestellt werden,---> System .net. Sockets. SocketException: Es ist normalerweise nur eine Verwendung der einzelnen Socketadressen (Protokoll/Netzwerkadresse/Port) zulässig. IP: Port**

    > [!NOTE]
    > Diese Datei wird gezippt, wenn mehrere Protokolle vorhanden sind.

    Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](https://docs.microsoft.com/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).

- **Schwellenwert für Listenansicht.** Für große SharePoint-Farmen müssen Sie möglicherweise den Schwellenwert für die Listenansicht erhöhen. Standardmäßig ist der Schwellenwert für die Listenansicht auf 5.000 festgelegt.

    Weitere Informationen finden Sie unter [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).

## <a name="troubleshooting-using-the-scanner-diagnostic-tool"></a>Problembehandlung mithilfe des Scanner-Diagnosetools

Wenn Sie Probleme mit dem Azure Information Scanner haben, überprüfen Sie mit dem folgenden PowerShell-Befehl, ob die Bereitstellung fehlerfrei ist:

```ps
Start-AIPScannerDiagnostics
```

Das Diagnosetool überprüft die folgenden Details und exportiert dann eine Protokolldatei mit den Ergebnissen:

- Gibt an, ob die Datenbank aktuell ist.
- Ob Netzwerk-URLs zugänglich sind
- Gibt an, ob ein gültiges Authentifizierungs Token vorhanden ist, und die Richtlinie kann abgerufen werden.
- Gibt an, ob das Profil in der Azure-Portal definiert ist.
- Gibt an, ob die Offline-/Online Konfiguration vorhanden und abgerufen werden kann
- Ob die konfigurierten Regeln gültig sind

> [!TIP]
> Wenn Sie den Befehl unter einem Benutzer ausführen, der nicht der Überprüfungs Benutzer ist, stellen Sie sicher, dass Sie den Parameter " **-Ondo** " hinzufügen. <!--For more information, see <x>.-->
>

> [!NOTE]
> Das Tool **Start-aipscannerdiagnostics** führt keine vollständige Voraussetzungs Prüfung aus. Wenn bei der Überprüfung Probleme auftreten, stellen Sie auch sicher, dass Ihr System den Überprüfungs [Anforderungen](deploy-aip-scanner-prereqs.md)entspricht und dass die Überprüfungs [Konfiguration und-Installation](deploy-aip-scanner-configure-install.md) fertiggestellt sind.
>

## <a name="next-steps"></a>Nächste Schritte

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).