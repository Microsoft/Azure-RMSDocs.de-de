---
title: Grundlegendes zum Azure Information Protection Unified Bezeichnung Scanner-aip
description: Anweisungen zum Installieren, konfigurieren und Ausführen der aktuellen Version des Azure Information Protection Unified-Beschriftungs Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/15/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: f674cd162131b0a45dbefbe70e617296695d6126
ms.sourcegitcommit: caf2978ab03e4893b59175ce753791867793dcfe
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2021
ms.locfileid: "100524743"
---
# <a name="what-is-the-azure-information-protection-unified-labeling-scanner"></a>Was ist der Azure Information Protection-Scanner für einheitliche Bezeichnungen?

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie unter [Was ist der klassische Azure Information Protection-Scanner?](deploy-aip-scanner-classic.md)*

>[!NOTE] 
> Verwenden Sie zum Überprüfen und Bezeichnen von Dateien auf Cloudrepositorys [Cloud App Security](/cloud-app-security/) anstelle des Scanners.

Verwenden Sie die Informationen in diesem Abschnitt, um sich über den Azure Information Protection Unified-Bezeichnungs Scanner zu informieren und dann zu installieren, zu konfigurieren, auszuführen und ggf. Probleme zu beheben.

Der AIP-Scanner wird als Dienst unter Windows Server ausgeführt und ermöglicht das ermitteln, klassifizieren und schützen von Dateien in den folgenden Daten speichern:

- **UNC-Pfade** für Netzwerkfreigaben, die das SMB-oder NFS-Protokoll (Vorschau) verwenden.

- **SharePoint-Dokument Bibliotheken und-Ordner** für SharePoint Server 2019 über SharePoint Server 2013. SharePoint 2010 wird auch für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

Um Ihre Dateien zu klassifizieren und zu schützen, verwendet die Überprüfung [Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) , die in einer der Microsoft 365 bezeichnet werden, die Admin Center, einschließlich der Microsoft 365 Security Center, des Microsoft 365 Compliance Centers und der Microsoft 365 Security and Compliance Center. 

## <a name="azure-information-protection-unified-labeling-scanner-overview"></a>Übersicht über Azure Information Protection Unified-Beschriftungs Scanner

Der AIP-Scanner kann alle Dateien überprüfen, die von Windows indiziert werden können. Wenn Sie die Vertraulichkeits Bezeichnungen so konfiguriert haben, dass die automatische Klassifizierung angewendet wird, kann die Überprüfung erkannte Dateien bezeichnen, um diese Klassifizierung anzuwenden, und optional den Schutz anwenden oder entfernen. 

Die folgende Abbildung zeigt die AIP-Überprüfungs Architektur, in der die Überprüfung Dateien auf Ihren lokalen und SharePoint-Servern ermittelt.

:::image type="content" source="media/ul-scanner-arch.png" alt-text="Azure Information Protection Unified Bezeichnung Scanner-Architektur":::

Zum Überprüfen der Dateien werden auf dem Computer installierte IFilters verwendet. Um zu ermitteln, ob die Dateien beschriftet werden müssen, verwendet die Überprüfung die in den Microsoft 365 integrierten Datenverlust (Data Loss Prevention, DLP) vertraulichen Informationstypen und die Mustererkennung bzw. Microsoft 365 Regex-Muster.

Der Scanner verwendet den Azure Information Protection Client und kann dieselben Dateitypen wie der Client klassifizieren und schützen. Weitere Informationen finden Sie [unter vom Azure Information Protection Unified Bezeichnung-Client unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md).

Führen Sie eine der folgenden Aktionen aus, um Ihre Scans nach Bedarf zu konfigurieren:

- **Führen Sie die Überprüfung nur im Ermittlungs Modus aus** , um Berichte zu erstellen, mit denen Sie überprüfen, was geschieht, wenn Ihre Dateien beschriftet werden
- **Führen Sie den Scanner aus, um Dateien mit sensiblen Informationen zu ermitteln**, ohne Bezeichnungen zu konfigurieren, die die automatische Klassifizierung anwenden.
- **Führen Sie den Scanner automatisch** aus, um die Bezeichnungen wie konfiguriert anzuwenden. 
- **Definieren Sie eine Liste der Dateitypen** , um bestimmte Dateien anzugeben, die gescannt oder ausgeschlossen werden sollen.

> [!NOTE]
> Der Scanner erkennt und Bezeichnungs nicht in Echtzeit. Die Dateien in den von Ihnen angegebenen Daten speichern werden systematisch durchsucht. Konfigurieren Sie diesen Zeitraum so, dass er einmal oder wiederholt ausgeführt wird.

> [!TIP]
> Der Unified-Beschriftungs Scanner unterstützt Scanner-Cluster mit mehreren Knoten, sodass Ihre Organisation horizontal hochskalieren, schnellere Überprüfungszeiten und einen umfassenderen Bereich erreichen kann. 
> 
> Stellen Sie mehrere Knoten direkt von Anfang an bereit, oder starten Sie mit einem Cluster mit einem einzelnen Knoten, und fügen Sie später zusätzliche Knoten hinzu, wenn Sie wachsen. Stellen Sie mehrere Knoten mithilfe des gleichen Cluster namens und der gleichen Datenbank für das Cmdlet **install-aipscanner** bereit.
> 

## <a name="aip-scanning-process"></a>AIP-Scanvorgang

Beim Scannen von Dateien führt der AIP-Scanner die folgenden Schritte aus:

[1. bestimmen Sie, ob Dateien für die Überprüfung eingeschlossen oder ausgeschlossen werden.](#1-determine-whether-files-are-included-or-excluded-for-scanning)

[2. überprüfen und bezeichnen von Dateien](#2-inspect-and-label-files)

[3. Bezeichnungs Dateien, die nicht überprüft werden können](#3-label-files-that-cant-be-inspected) 

Weitere Informationen finden Sie unter [Dateien, die nicht vom Scanner bezeichnet](#files-not-labeled-by-the-scanner)werden.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. bestimmen Sie, ob Dateien für die Überprüfung eingeschlossen oder ausgeschlossen werden. 

Bei der Überprüfung werden von der Klassifizierung und vom Schutz ausgeschlossene Dateien wie ausführbare Dateien und Systemdateien übersprungen. Weitere Informationen finden Sie unter [Dateitypen, die von der Klassifizierung und dem Schutz ausgeschlossen sind](./rms-client/clientv2-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection).

Der Scanner berücksichtigt auch alle Dateilisten, die explizit für die Überprüfung definiert oder von der Überprüfung ausgeschlossen werden sollen. Dateilisten gelten standardmäßig für alle Daten Depots und können auch nur für bestimmte Depots definiert werden.

Zum Definieren von Dateilisten für das Scannen oder ausschließen verwenden Sie die Einstellung **Dateitypen** für die Überprüfung im Inhalts Überprüfungs Auftrag. Beispiel:

![Konfigurieren der zu überprüfenden Dateitypen für den Azure Information Protection-Scanner](./media/scanner-file-types.png)

Weitere Informationen finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner-configure-install.md).

### <a name="2-inspect-and-label-files"></a>2. überprüfen und bezeichnen von Dateien

Nach der Identifizierung ausgeschlossener Dateien filtert der Scanner erneut, um die für die Prüfung unterstützten Dateien zu identifizieren.

Diese zusätzlichen Filter sind dieselben, die vom Betriebssystem für die Windows-Suche und-Indizierung verwendet werden, und es ist keine zusätzliche Konfiguration erforderlich. Windows IFilter wird auch zum Überprüfen von Dateitypen verwendet, die von Word, Excel und PowerPoint sowie von PDF-Dokumenten und Textdateien verwendet werden.

Eine vollständige Liste der für die Überprüfung unterstützten Dateitypen sowie weitere Anweisungen zum Konfigurieren von Filtern, um Zip-und TIFF-Dateien einzuschließen, finden Sie [unter Unterstützte Dateitypen für die Überprüfung](./rms-client/clientv2-admin-guide-file-types.md#file-types-supported-for-inspection).

Nach der Überprüfung werden die unterstützten Dateitypen unter Verwendung der für ihre Bezeichnungen angegebenen Bedingungen bezeichnet. Wenn Sie den Ermittlungs Modus verwenden, können diese Dateien entweder so gemeldet werden, dass Sie die für ihre Bezeichnungen angegebenen Bedingungen enthalten, oder dass alle bekannten sensiblen Informationstypen enthalten sind.

#### <a name="stopped-scanner-processes"></a>Beendete Überprüfungsprozesse

Wenn die Überprüfung beendet wird und keine Überprüfung für eine große Anzahl von Dateien in Ihrem Repository durchgeführt wird, müssen Sie möglicherweise die Anzahl der dynamischen Ports für das Betriebssystem erhöhen, in dem die Dateien gehostet werden.

Beispielsweise ist die Serverhärtung für SharePoint ein Grund, warum die Überprüfung die Anzahl der zulässigen Netzwerkverbindungen überschreiten würde und daher angehalten wird.

Wenn Sie überprüfen möchten, ob dies die Ursache für die Beendigung des Scanners ist, überprüfen Sie die Überprüfungs Protokolle unter **%LocalAppData%\microsoft\msip\logs\msipscanner.iplog** (mehrere Protokolle werden in eine ZIP-Datei komprimiert):

`Unable to connect to the remote server ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted IP:port`

Weitere Informationen zum Anzeigen des aktuellen Port Bereichs und zum Erhöhen des aktuellen Port Bereichs finden Sie unter [Einstellungen, die geändert werden können, um die Netzwerkleistung zu verbessern](/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).

> [!TIP]
> Für große SharePoint-Farmen müssen Sie möglicherweise den Schwellenwert für die Listenansicht erhöhen, der den Standardwert **5.000** hat.
>
> Weitere Informationen finden Sie unter [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).
>

### <a name="3-label-files-that-cant-be-inspected"></a>3. Bezeichnungs Dateien, die nicht überprüft werden können

Für alle Dateitypen, die nicht überprüft werden können, wendet der AIP-Scanner die Standard Bezeichnung in der Azure Information Protection Richtlinie oder die für den Scanner konfigurierte Standard Bezeichnung an.

### <a name="files-not-labeled-by-the-scanner"></a>Dateien, die nicht vom Scanner bezeichnet werden
Der AIP-Scanner kann die Dateien unter den folgenden Umständen nicht bezeichnen:

- Wenn die Bezeichnung die Klassifizierung, aber nicht den Schutz anwendet, und der Dateityp die Klassifizierung nur vom Client unterstützt. Weitere Informationen finden Sie unter [Unified-Bezeichnung für Client Dateitypen](./rms-client/clientv2-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Wenn die Bezeichnung Klassifizierung und Schutz anwendet, wird der Dateityp vom Scanner nicht unterstützt.
  
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. 

    Andere Dateitypen können zum Schutz hinzugefügt werden, wenn Sie [die Typen der zu schützenden Dateien ändern](deploy-aip-scanner-configure-install.md#change-which-file-types-to-protect).

**Beispiel**: nach der Überprüfung von txt-Dateien kann der Scanner keine Bezeichnung anwenden, die nur für die Klassifizierung konfiguriert ist, da der Dateityp ". txt" nur die Klassifizierung unterstützt. 

Wenn die Bezeichnung jedoch für die Klassifizierung und den Schutz konfiguriert ist und der txt-Dateityp für die Überprüfung enthalten ist, kann der Scanner die Datei bezeichnen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Bereitstellen des Scanners finden Sie in den folgenden Artikeln:

- [Bereitstellungs Voraussetzungen für AIP-Scanner](deploy-aip-scanner-prereqs.md)
- [Konfigurieren und Installieren des AIP-Scanners](deploy-aip-scanner-configure-install.md)
- [Ausführen von Scans mit dem AIP-Scanner](deploy-aip-scanner-manage.md)

**Weitere Informationen**:

- [Sehen Sie sich unsere Bereitstellung an.](https://techcommunity.microsoft.com/t5/microsoft-security-and/mip-scanner-deployment-watch-our-video/ba-p/2023277) Sehen Sie sich eine Schritt-für-Schritt-Anleitung zum Installieren und Konfigurieren des lokalen Scanners mit einheitlicher Bezeichnung an.

- Weitere Informationen finden Sie in unserem Blog zu bewährten Methoden für die einheitliche Bezeichnung Scanner: [bewährte Methoden für die Bereitstellung und Verwendung des AIP-UL-Scanners](https://aka.ms/AIPScannerBestPractices) .

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).
