---
title: Ausführen des Azure Information Protection Classic Scanner (AIP)
description: Anweisungen zum Ausführen des Azure Information Protection klassischen Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/29/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: c3292782a3a824db1166e255be3935978c8b8ce9
ms.sourcegitcommit: d31cb53de64bafa2097e682550645cadc612ec3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96316397"
---
# <a name="running-the-azure-information-protection-classic-scanner"></a>Ausführen des Azure Information Protection klassischen Scanner

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*

>[!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>
> Wenn Sie mit dem Unified-Bezeichnungs Scanner arbeiten, finden Sie unter [Ausführen des Azure Information Protection Scanners](deploy-aip-scanner-manage.md)Weitere Informationen.

Nachdem Sie die [Systemanforderungen](deploy-aip-scanner-prereqs-classic.md) bestätigt und [Ihren Scanner konfiguriert und installiert](deploy-aip-scanner-configure-install-classic.md)haben, [führen Sie einen Ermittlungs Scan](#run-a-discovery-cycle-and-view-reports-for-the-scanner) aus, um zu beginnen.

Verwenden Sie die unten aufgeführten Schritte, um Ihre Scans zu verwalten.

- [Einen Scanvorgang abbrechen](#stopping-a-scan)
- [Dateien werden neu berechnet](#rescanning-files)
- [Problembehandlung bei einem beendeten Scan](#troubleshooting-a-stopped-scan)
- [Problembehandlung mithilfe des Scanner-Diagnosetools](#troubleshooting-using-the-scanner-diagnostic-tool)
- [Überprüfungs Ereignisprotokoll-IDs und Beschreibungen](#event-log-ids-and-descriptions-for-the-scanner)

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

    - **Aktualisieren Sie die Scanaufträge.**  Wählen Sie im Bereich **Azure Information Protection-Inhalts Scanaufträge** die Option **Aktualisieren** aus.

        Warten Sie, bis die Werte für die Spalte **Letzte Scanergebnisse** und die Spalte Letzte Überprüfung **(Endzeit)** angezeigt werden.

    - **Verwenden Sie einen PowerShell-Befehl.** Führen `Get-AIPScannerStatus` Sie aus, um die Statusänderung zu überwachen.

    - **Überprüfen Sie Windows-Ereignisprotokolle.** Überprüfen Sie das lokale Ereignisprotokoll für Windows **-Anwendungen und-Dienste** mit dem Namen **Azure Information Protection**.

        Dieses Protokoll meldet auch, wann die Überprüfung abgeschlossen ist, einschließlich einer Zusammenfassung der Ergebnisse. Suchen Sie einfach nach der Ereignis-ID **911**. Weitere Informationen finden Sie unter [Ereignisprotokoll-IDs und Beschreibungen für den Scanner](#event-log-ids-and-descriptions-for-the-scanner).

1. Überprüfen Sie nach Abschluss der Überprüfung die im Verzeichnis **% *LocalAppData*% \ microsoft\msip\scanner\reports** gespeicherten Berichte.

    - Die TXT-Zusammenfassungsdateien enthalten die zum Überprüfen benötigte Zeit, die Anzahl der überprüften Dateien sowie die Anzahl der Dateien mit übereinstimmenden Informationstypen.

    - Die CSV-Dateien enthalten mehr Details zu den einzelnen Dateien. In diesem Ordner werden für jeden Scanzyklus bis zu 60 Berichte gespeichert, die bis auf den letzten alle komprimiert werden, um die Speicherplatzbelegung zu minimieren.

[Anfängliche Konfigurationen](deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal) weisen Sie an, die zu **ermittelnden Informationstypen** nur für die **Richtlinie** festzulegen. Diese Konfiguration bedeutet, dass nur Dateien, die die Bedingungen erfüllen, die Sie für die automatische Klassifizierung konfiguriert haben, in den ausführlichen Berichten enthalten sind.

Wenn keine Bezeichnungen angewendet werden, überprüfen Sie, ob die Bezeichnungs Konfiguration eine automatische anstelle der empfohlenen Klassifizierung enthält, oder aktivieren Sie die Option **Empfohlene Bezeichnung als automatisch** aktivieren (verfügbar in Scanner Version 2.7. x. x und höher).

Wenn die Ergebnisse immer noch nicht erwartungsgemäß sind, müssen Sie möglicherweise die Bedingungen, die Sie für ihre Bezeichnungen festgelegt haben, neu konfigurieren. Wenn dies der Fall ist, konfigurieren Sie die Bedingungen nach Bedarf neu, und wiederholen Sie diesen Vorgang, bis Sie mit den Ergebnissen zufrieden sind. Aktualisieren Sie anschließend die Konfiguration automatisch und optional den Schutz.

### <a name="viewing-updates-in-the-azure-portal"></a>Anzeigen von Updates in der Azure-Portal

Diese Informationen werden von den Scannern alle fünf Minuten an Azure Information Protection gesendet, sodass Sie die Ergebnisse nahezu in Echtzeit in der Azure-Portal anzeigen können. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md).

Das Azure-Portal zeigt nur Informationen zur letzten Überprüfung an. Wenn Sie die Ergebnisse vorheriger Überprüfungen anzeigen müssen, sehen Sie sich die Berichte an, die auf dem Überprüfungscomputer im Ordner „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“ gespeichert sind.

### <a name="changing-log-levels-or-locations"></a>Ändern von Protokoll Ebenen oder-Speicherorten

Ändern Sie die Protokollierungsebene, indem Sie den *Report Level* -Parameter mit [Set-aipscannerconfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration)verwenden.

Der Speicherort oder Name des Berichts Ordners kann nicht geändert werden. Wenn Sie Berichte an einem anderen Speicherort speichern möchten, sollten Sie die Verwendung einer Verzeichnis Verknüpfung für den Ordner in Erwägung gezogen.

Verwenden Sie z. b. den Befehl " [mklink](/windows-server/administration/windows-commands/mklink) ": `mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`

Wenn Sie diese Schritte nach der Erstkonfiguration und-Installation durchgeführt haben, fahren Sie mit [Konfigurieren des Scanners fort, um Klassifizierung und Schutz anzuwenden](deploy-aip-scanner-configure-install.md#configure-the-scanner-to-apply-classification-and-protection).

## <a name="stopping-a-scan"></a>Beenden einer Überprüfung

Verwenden Sie eine der folgenden Methoden, um einen aktuell laufenden Scanvorgang zu beenden:

- **Azure-Portal.** Wählen Sie **Scan** Vorgang:

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

Alle Dateien werden auch in den folgenden Szenarien überprüft, wenn der Scanner eine Azure Information Protection Richtlinie mit neuen oder geänderten Bedingungen herunterlädt.

Die Überprüfung aktualisiert die Richtlinie automatisch stündlich, ebenso wie bei jedem Start des Diensts, und die Richtlinie ist länger als eine Stunde alt.

Wenn Sie die Richtlinie früher aktualisieren möchten, z. b. beim Testen, löschen Sie die Richtlinien Datei **Policy.msip**  manuell aus dem Verzeichnis **%LocalAppData%\microsoft\msip** , und starten Sie den Azure Information Protection-Dienst neu.

> [!NOTE]
> Wenn Sie auch die Schutzeinstellungen für ihre Bezeichnungen geändert haben, warten Sie beim Speichern der aktualisierten Schutzeinstellungen vor dem Neustart des Azure Information Protection Dienstanbieter weitere 15 Minuten ab.
>

## <a name="troubleshooting-a-stopped-scan"></a>Problembehandlung bei einem beendeten Scan

Wenn der Scanner unerwartet in der Mitte angehalten wird und das Scannen einer großen Anzahl von Dateien in einem Repository nicht durchführt, müssen Sie möglicherweise eine der folgenden Einstellungen ändern:

- **Anzahl der dynamischen Ports**. Möglicherweise müssen Sie die Anzahl der dynamischen Ports für das Betriebssystem erhöhen, das die Dateien gehostet. Ein Grund dafür, warum der Scanner die Anzahl an zulässigen Netzwerkverbindungen überschreitet und daher angehalten wird, ist die Serverhärtung für SharePoint.

    Um zu überprüfen, ob dies die Ursache für die Beendigung des Scanners ist, sollten Sie überprüfen, ob die folgende Fehlermeldung für den Scanner in der Datei **% *LocalAppData*% \ microsoft\msip\logs\msipscanner.iplog** protokolliert wird.

    **Es kann keine Verbindung mit dem Remote Server hergestellt werden,---> System .net. Sockets. SocketException: Es ist normalerweise nur eine Verwendung der einzelnen Socketadressen (Protokoll/Netzwerkadresse/Port) zulässig. IP: Port**

    > [!NOTE]
    > Diese Datei wird gezippt, wenn mehrere Protokolle vorhanden sind.

    Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).

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
> Wenn Sie den Befehl unter einem Benutzer ausführen, der nicht der Überprüfungs Benutzer ist, stellen Sie sicher, dass Sie den Parameter " **-Ondo** " hinzufügen. 
>

> [!NOTE]
> Das Tool **Start-aipscannerdiagnostics** führt keine vollständige Voraussetzungs Prüfung aus. Wenn bei der Überprüfung Probleme auftreten, stellen Sie auch sicher, dass Ihr System den Überprüfungs [Anforderungen](deploy-aip-scanner-prereqs.md)entspricht und dass die Überprüfungs [Konfiguration und-Installation](deploy-aip-scanner-configure-install.md) fertiggestellt sind.
>

## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>Ereignisprotokoll-IDs und Beschreibungen für die Überprüfung

Die folgenden AIP-Überprüfungsprotokoll Ereignisse werden im Ereignisprotokoll für Windows **-Anwendungen und-Dienste** mit dem Namen **Azure Information Protection** gespeichert.

|Ereignis-ID  |Aktivität  |BESCHREIBUNG  |
|---------|---------|---------|
|**910**     | Scannercycle gestartet        | Wird protokolliert, wenn der Überprüfungs Dienst gestartet wird und mit dem Suchen nach Dateien in den von Ihnen angegebenen Daten Depots beginnt.        |
|**911**     |   Scannercycle abgeschlossen      | Wird protokolliert, wenn die Überprüfung eine manuelle Überprüfung abgeschlossen hat oder die Überprüfung einen Durchlauf für einen kontinuierlichen Zeitplan abgeschlossen hat.       |
| | | |

> [!TIP]
> Wenn die Überprüfung so konfiguriert wurde, dass Sie nicht fortlaufend ausgeführt wird, um die Dateien erneut zu scannen, legen Sie den **Zeitplan** auf **manuell** oder **immer** im inhaltscanauftrag fest, und starten Sie den Dienst neu. Weitere Informationen finden Sie unter [erneutanup von Dateien](#rescanning-files).
>

## <a name="next-steps"></a>Nächste Schritte

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).