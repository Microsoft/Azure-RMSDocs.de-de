---
title: Ausführen des Azure Information Protection Unified Bezeichnung Scanner (AIP)
description: Anweisungen zum Ausführen des Azure Information Protection Unified-Beschriftungs Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 02/01/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 13484ad0301ec8d7404c4127ff78720df81d8eb5
ms.sourcegitcommit: caf2978ab03e4893b59175ce753791867793dcfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2021
ms.locfileid: "100524777"
---
# <a name="running-the-azure-information-protection-scanner"></a>Ausführen des Azure Information Protection-Scanners

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Scanner finden Sie unter [Ausführen der Azure Information Protection klassischen Scanner](deploy-aip-scanner-manage-classic.md). *

Nachdem Sie die [Systemanforderungen](deploy-aip-scanner-prereqs.md) bestätigt und [Ihren Scanner konfiguriert und installiert](deploy-aip-scanner-configure-install.md)haben, [führen Sie einen Ermittlungs Scan](#run-a-discovery-cycle-and-view-reports-for-the-scanner) aus, um zu beginnen.

Verwenden Sie die unten aufgeführten Schritte, um Ihre Scans zu verwalten.

- [Einen Scanvorgang abbrechen](#stopping-a-scan)
- [Dateien werden neu berechnet](#rescanning-files)

Weitere Informationen finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Ausführen eines Ermittlungszyklus und Anzeigen von Berichten für die Überprüfung

Gehen Sie wie folgt vor, nachdem Sie [Ihren Scanner konfiguriert und installiert](deploy-aip-scanner-configure-install.md) haben, um ein ursprüngliches Verständnis ihrer Inhalte zu erhalten.

Führen Sie diese Schritte nach Bedarf erneut aus, wenn sich Ihre Inhalte ändern.

1. Wählen Sie im Azure-Portal im Bereich **Azure Information Protection-Inhalts Scan** Aufträge ihre Inhalts Scanaufträge aus, und wählen Sie dann die Option **jetzt** überprüfen aus:

    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

    Führen Sie alternativ in der PowerShell-Sitzung den folgenden Befehl aus:

    ```PowerShell
    Start-AIPScan
    ```

1. Warten Sie, bis die Überprüfung den Zyklus abgeschlossen hat. Die Überprüfung ist abgeschlossen, wenn der Scanner alle Dateien in den angegebenen Daten speichern durchlaufen hat.

    Führen Sie einen der folgenden Schritte aus, um den Überprüfungs Fortschritt zu überwachen

    - **Aktualisieren Sie die Scanaufträge.**  Wählen Sie im Bereich **Azure Information Protection-Inhalts Scanaufträge** die Option **Aktualisieren** aus.

        Warten Sie, bis die Werte für die Spalte **Letzte Scanergebnisse** und die Spalte Letzte Überprüfung **(Endzeit)** angezeigt werden.

    - **Verwenden Sie einen PowerShell-Befehl.** Führen `Get-AIPScannerStatus` Sie aus, um die Statusänderung zu überwachen.

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

    ```PowerShell
    Stop-AIPScan 
    ```

## <a name="rescanning-files"></a>Dateien werden neu berechnet

Beim [ersten Scan](#run-a-discovery-cycle-and-view-reports-for-the-scanner)Vorgang prüft der Scanner alle Dateien in den konfigurierten Daten speichern. Bei nachfolgenden Scans werden nur neue oder geänderte Dateien überprüft.

Die erneute Überprüfung aller Dateien ist in der Regel hilfreich, wenn Sie möchten, dass die Berichte alle Dateien einschließen, wenn Sie Änderungen vorgenommen haben, die Sie auf alle Dateien anwenden möchten, und wenn die Überprüfung im Ermittlungs Modus ausgeführt wird.

So **führen Sie einen vollständigen erneuten Scan manuell** aus:

1. Navigieren Sie in der Azure-Portal zum Bereich **Azure Information Protection-Inhalts Scanaufträge** .

1. Wählen Sie den Auftrag für die Inhalts Überprüfung aus der Liste aus, und wählen Sie dann die Option **alle Dateien neu** Einlesen aus:

    ![Initiieren eines erneuten Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-rescan-files.png)

Wenn eine vollständige Überprüfung durchgeführt wird, wird der Überprüfungstyp automatisch in inkrementell geändert, sodass bei nachfolgenden Scans nur neue oder geänderte Dateien erneut gescannt werden.

> [!TIP]
> Wenn Sie Änderungen an Ihrem AIP- [Inhalts Überprüfungs Auftrag](deploy-aip-scanner-configure-install.md#create-a-content-scan-job)vorgenommen haben, werden Sie vom Azure-Portal aufgefordert, eine vollständige erneute Überprüfung zu überspringen. Um sicherzustellen, dass die erneute Überprüfung ausgeführt wird, stellen Sie sicher, dass in der angezeigten Eingabeaufforderung **Nein** ausgewählt ist.
> 
### <a name="trigger-a-full-rescan-by-modifying-your-settings-versions-271010-and-lower"></a>Einen vollständigen erneuten Scan durch Ändern der Einstellungen (Versionen 2.7.101.0 und niedriger) auslöst

In den Überprüfungs Versionen [2.7.101.0](rms-client/unifiedlabelingclient-version-release-history.md#version-271010) und niedriger werden alle Dateien gescannt, wenn der Scanner neue oder geänderte Einstellungen für die automatische und empfohlene Bezeichnung erkennt. Die Überprüfung aktualisiert die Richtlinie automatisch alle vier Stunden.

Wenn Sie die Richtlinie früher aktualisieren möchten, z. b. beim Testen, löschen Sie den Inhalt des Verzeichnisses **%LocalAppData%\microsoft\msip\mip \<processname> \mip** , und starten Sie den Azure Information Protection-Dienst neu.

Wenn Sie auch die Schutzeinstellungen für ihre Bezeichnungen geändert haben, warten Sie beim Speichern der aktualisierten Schutzeinstellungen vor dem Neustart des Azure Information Protection Dienstanbieter weitere 15 Minuten ab.

> [!IMPORTANT]
> Wenn Sie ein Upgrade auf Version [2.8.85.0](rms-client/unifiedlabelingclient-version-release-history.md#version-28850) oder höher durchgeführt haben, überspringt AIP den vollständigen erneuten Scanvorgang für aktualisierte Einstellungen, um eine konsistente Leistung sicherzustellen. Wenn Sie ein Upgrade durchgeführt haben, stellen Sie sicher, dass Sie bei Bedarf [manuell einen vollständigen erneuten Scan ausführen](#rescanning-files) . 
>
> Wenn Sie z. b. die **Vertraulichkeitsrichtlinien** Einstellungen von **erzwingen = aus** in **erzwingen = on** geändert haben, stellen Sie sicher, dass Sie eine vollständige erneute Überprüfung ausführen, um ihre Bezeichnungen auf Ihre Inhalte anzuwenden.
> 

## <a name="next-steps"></a>Nächste Schritte

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).