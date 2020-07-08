---
title: Grundlegendes zum Azure Information Protection klassischen Scanner-aip
description: Anweisungen zum Installieren, konfigurieren und Ausführen des Azure Information Protection klassischen Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 65c3a37f68676616d7342879d9621a143842f4bf
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86049539"
---
# <a name="what-is-the-azure-information-protection-classic-scanner"></a>Was ist der klassische Azure Information Protection-Scanner?

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*

>[!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>
> Wenn Sie den Unified-Bezeichnungs Client verwenden, finden Sie weitere Informationen unter [Was ist der Azure Information Protection Unified-Beschriftungs Scanner?](deploy-aip-scanner.md).

Verwenden Sie die Informationen in diesem Abschnitt, um sich mit dem Azure Information Protection Scanner vertraut zu machen und dann zu installieren, zu konfigurieren, auszuführen und ggf. Probleme zu beheben.

Der AIP-Scanner wird als Dienst unter Windows Server ausgeführt und ermöglicht das ermitteln, klassifizieren und schützen von Dateien in den folgenden Daten speichern:

- **UNC-Pfade** für Netzwerkfreigaben, die das SMB-Protokoll (Server Message Block) verwenden.

- **SharePoint-Dokument Bibliotheken und-Ordner** für SharePoint Server 2019 über SharePoint Server 2013. SharePoint 2010 wird auch für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

> [!NOTE]
> Verwenden Sie zum Überprüfen und Bezeichnen von Dateien auf Cloudrepositorys [Cloud App Security](https://docs.microsoft.com/cloud-app-security/) anstelle des Scanners.
>
## <a name="azure-information-protection-classic-scanner-overview"></a>Übersicht über Azure Information Protection klassischen Scanner

Der AIP-Scanner kann alle Dateien überprüfen, die von Windows indiziert werden können. Wenn Sie Bezeichnungen konfiguriert haben, die die automatische Klassifizierung anwenden, kann der Scanner ermittelte Dateien so bezeichnen, dass diese Klassifizierung angewendet wird, und optional den Schutz anwenden oder entfernen.

Die folgende Abbildung zeigt die AIP-Überprüfungs Architektur, in der die Überprüfung Dateien auf Ihren lokalen und SharePoint-Servern ermittelt.

:::image type="content" source="media/classic-scanner-arch.png" alt-text="Azure Information Protection klassische scannerarchitektur":::

Zum Überprüfen der Dateien werden auf dem Computer installierte IFilters verwendet. Um zu ermitteln, ob die Dateien beschriftet werden müssen, verwendet die Überprüfung die vertraulichen Informationstypen und die Mustererkennung von Office 365 (Data Loss Prevention, DLP) oder Office 365 Regex-Muster.

Der Scanner verwendet den Azure Information Protection Client und kann dieselben Dateitypen wie der Client klassifizieren und schützen. Weitere Informationen finden Sie [unter vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).

Führen Sie eine der folgenden Aktionen aus, um Ihre Scans nach Bedarf zu konfigurieren:

- **Führen Sie die Überprüfung nur im Ermittlungs Modus aus** , um Berichte zu erstellen, mit denen Sie überprüfen, was geschieht, wenn Ihre Dateien beschriftet werden
- **Führen Sie den Scanner aus, um Dateien mit sensiblen Informationen zu ermitteln,** ohne Bezeichnungen zu konfigurieren, die die automatische Klassifizierung anwenden.
- **Führen Sie den Scanner automatisch** aus, um die Bezeichnungen wie konfiguriert anzuwenden.
- **Definieren Sie eine Liste der Dateitypen** , um bestimmte Dateien anzugeben, die gescannt oder ausgeschlossen werden sollen.

> [!NOTE]
> Der Scanner erkennt und Bezeichnungs nicht in Echtzeit. Die Dateien in den von Ihnen angegebenen Daten speichern werden systematisch durchsucht. Konfigurieren Sie diesen Zeitraum so, dass er einmal oder wiederholt ausgeführt wird.

## <a name="aip-scanning-process"></a>AIP-Scanvorgang

Beim Scannen von Dateien führt der AIP-Scanner die folgenden Schritte aus:

[1. bestimmen Sie, ob Dateien für die Überprüfung eingeschlossen oder ausgeschlossen werden.](#1-determine-whether-files-are-included-or-excluded-for-scanning)

[2. überprüfen und bezeichnen von Dateien](#2-inspect-and-label-files)

[3. Bezeichnungs Dateien, die nicht überprüft werden können](#3-label-files-that-cant-be-inspected)

> [!NOTE]
> Weitere Informationen finden Sie unter [Dateien, die nicht vom Scanner bezeichnet](#files-not-labeled-by-the-scanner)werden.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. bestimmen Sie, ob Dateien für die Überprüfung eingeschlossen oder ausgeschlossen werden.

Bei der Überprüfung werden von der Klassifizierung und vom Schutz ausgeschlossene Dateien wie ausführbare Dateien und Systemdateien übersprungen. Weitere Informationen finden Sie unter [Dateitypen, die von der Klassifizierung und dem Schutz ausgeschlossen sind](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection).

Der Scanner berücksichtigt auch alle Dateilisten, die explizit für die Überprüfung definiert oder von der Überprüfung ausgeschlossen werden sollen. Dateilisten gelten standardmäßig für alle Daten Depots und können auch nur für bestimmte Depots definiert werden.

Zum Definieren von Dateilisten für das Scannen oder ausschließen verwenden Sie die Einstellung **Dateitypen** für die Überprüfung im Inhalts Überprüfungs Auftrag. Zum Beispiel:

![Konfigurieren der zu überprüfenden Dateitypen für den Azure Information Protection-Scanner](./media/scanner-file-types.png)

Weitere Informationen finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner-configure-install.md).

### <a name="2-inspect-and-label-files"></a>2. überprüfen und bezeichnen von Dateien

Nach der Identifizierung ausgeschlossener Dateien filtert der Scanner erneut, um die für die Prüfung unterstützten Dateien zu identifizieren.

Diese zusätzlichen Filter sind dieselben, die vom Betriebssystem für die Windows-Suche und-Indizierung verwendet werden, und es ist keine zusätzliche Konfiguration erforderlich. Windows IFilter wird auch zum Überprüfen von Dateitypen verwendet, die von Word, Excel und PowerPoint sowie von PDF-Dokumenten und Textdateien verwendet werden.

Eine vollständige Liste der für die Überprüfung unterstützten Dateitypen sowie weitere Anweisungen zum Konfigurieren von Filtern, um Zip-und TIFF-Dateien einzuschließen, finden Sie [unter Unterstützte Dateitypen für die Überprüfung](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-inspection).

Nach der Überprüfung werden die unterstützten Dateitypen unter Verwendung der für ihre Bezeichnungen angegebenen Bedingungen bezeichnet. Wenn Sie den Ermittlungs Modus verwenden, können diese Dateien entweder so gemeldet werden, dass Sie die für ihre Bezeichnungen angegebenen Bedingungen enthalten, oder dass alle bekannten sensiblen Informationstypen enthalten sind.

### <a name="3-label-files-that-cant-be-inspected"></a>3. Bezeichnungs Dateien, die nicht überprüft werden können

Für alle Dateitypen, die nicht überprüft werden können, wendet der AIP-Scanner die Standard Bezeichnung in der Azure Information Protection Richtlinie oder die für den Scanner konfigurierte Standard Bezeichnung an.

### <a name="files-not-labeled-by-the-scanner"></a>Dateien, die nicht vom Scanner bezeichnet werden

Der AIP-Scanner kann die Dateien unter den folgenden Umständen nicht bezeichnen:

- Wenn die Bezeichnung die Klassifizierung, aber nicht den Schutz anwendet, und der Dateityp die Klassifizierung nur vom Client unterstützt. Weitere Informationen finden Sie unter [klassische Client Dateitypen](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Wenn die Bezeichnung Klassifizierung und Schutz anwendet, wird der Dateityp vom Scanner nicht unterstützt.
  
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden.

    Andere Dateitypen können zum Schutz hinzugefügt werden, wenn Sie [die Typen der zu schützenden Dateien ändern](deploy-aip-scanner-configure-install.md#change-which-file-types-to-protect).

**Beispiel:** Nach dem Überprüfen von txt-Dateien kann die Überprüfung keine Bezeichnung anwenden, die nur für die Klassifizierung konfiguriert ist, da der txt-Dateityp nur Klassifizierung unterstützt.

Wenn die Bezeichnung jedoch für die Klassifizierung und den Schutz konfiguriert ist und der txt-Dateityp für die Überprüfung enthalten ist, kann der Scanner die Datei bezeichnen.

## <a name="upgrading-your-scanner"></a>Aktualisieren Ihres Scanners

Wenn Sie den Scanner bereits installiert haben und ein Upgrade durchführen möchten, finden Sie weitere Informationen unter [Aktualisieren der Azure Information Protection Scanner](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

[Konfigurieren](deploy-aip-scanner-configure-install.md) und verwenden Sie dann wie gewohnt [Ihren Scanner](deploy-aip-scanner-manage.md) , und überspringen Sie die Schritte zur Installation des Scanners.

>[!NOTE]
> Wenn Sie über eine Version des Scanners verfügen, die älter als 1.48.204.0 ist und Sie nicht zur Aktualisierung bereit sind, finden Sie weitere Informationen unter Bereitstellen [vorheriger Versionen des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner-previousversions.md).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Bereitstellen des Scanners finden Sie in den folgenden Artikeln:

- [Bereitstellungs Voraussetzungen für AIP-Scanner](deploy-aip-scanner-prereqs.md)
- [Konfigurieren und Installieren des AIP-Scanners](deploy-aip-scanner-configure-install.md)
- [Ausführen von Scans mit dem AIP-Scanner](deploy-aip-scanner-manage.md)

**Weitere Informationen:**

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).
