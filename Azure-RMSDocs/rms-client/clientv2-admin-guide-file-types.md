---
title: Unterstützte Dateitypen-Azure Information Protection Unified-Bezeichnungs Client
description: Technische Details zu unterstützten Dateitypen, Dateinamen Erweiterungen und Schutz Ebenen für Administratoren, die für den Azure Information Protection Unified Bezeichnung-Client für Windows verantwortlich sind.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 40b2a6de06fb20f8fab0d1a1d7e8a774fe2b54fc
ms.sourcegitcommit: af7ac2eeb8f103402c0036dd461c77911fbc9877
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "98560185"
---
# <a name="file-types-supported-by-the-azure-information-protection-unified-labeling-client"></a>Vom Azure Information Protection Unified Bezeichnung-Client unterstützte Dateitypen

>***Gilt für** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*>
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen unter [AIP und ältere Windows-und Office-Versionen](../known-issues.md#aip-and-legacy-windows-and-office-versions).*
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie unter [klassische Client Dateitypen](client-admin-guide-file-types.md) .*

Der Azure Information Protection Unified Bezeichnung-Client kann Folgendes auf Dokumente und e-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Der Azure Information Protection Unified-Bezeichnungs Client kann auch den Inhalt einiger Dateitypen mithilfe von bekannten sensiblen Informationstypen oder regulären Ausdrücken untersuchen, die Sie definieren.

Verwenden Sie die folgenden Informationen, um zu überprüfen, welche Dateitypen der Azure Information Protection Unified-Bezeichnungs Client unterstützt, welche verschiedenen Schutz Ebenen Sie verwenden und wie Sie die Standardschutz Ebene ändern können, und um festzustellen, welche Dateien von der Klassifizierung und dem Schutz automatisch ausgeschlossen (übersprungen) werden.

Für aufgelisteten Dateitypen werden WebDav-Positionen nicht unterstützt.

## <a name="file-types-supported-for-classification-only"></a>Nur für die Klassifizierung unterstützte Dateitypen

Folgende Dateitypen können klassifiziert werden, auch wenn diese nicht geschützt sind.

- **Adobe Portable Document Format**: .pdf

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft XPS**: .xps .oxps

- **Bilder**: JPG, JPE, JPEG, JIF, JFIF, JFI PNG, TIF, TIFF

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng

- **Microsoft Office**: Dateitypen in der folgenden Tabelle.

    Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und Office Open XML für die folgenden Office-Programme: Word, Excel und PowerPoint.

    |Office-Dateityp|Office-Dateityp|
    |----------------------------------|----------------------------------|
    |.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />VDW<br /><br />.vsd|VSDM<br /><br /> VSDX<br /><br />VSS<br /><br />VSSM<br /><br />VST<br /><br />VSTM<br /><br />VSSX<br /><br />VSTX<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx|

Zusätzliche Dateitypen unterstützen die Klassifizierung, wenn sie zudem geschützt sind. Weitere Informationen zu diesen Dateitypen finden Sie im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).

Beispiele:

- Wenn die Bezeichnung **General** Sensitivität die Klassifizierung anwendet und keinen Schutz anwendet: Sie können die **Allgemeine** Bezeichnung auf eine Datei mit dem Namen sales.pdf anwenden, aber Sie können diese Bezeichnung nicht auf eine Datei mit dem Namen sales.txt anwenden.

- Wenn die **Vertraulichkeits Bezeichnung "vertraulich \ alle Mitarbeiter** " Klassifizierung und Schutz anwendet: Sie können diese Bezeichnung auf eine Datei namens "sales.pdf" und eine Datei mit dem Namen "sales.txt" anwenden. Sie können den Schutz auch ohne die Klassifizierung auf diese Dateien anwenden.

## <a name="file-types-supported-for-protection"></a>Für den Schutz unterstützte Dateitypen

Der Azure Information Protection Unified Bezeichnung-Client unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben.

|Art des Schutzes|Systemeigenes Format|Allgemein|
|----------------------|----------|-----------|
|BESCHREIBUNG|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Bei anderen unterstützten Dateitypen bietet der generische Schutz eine Schutz Ebene, die die Datei Kapselung mit dem Pfile-Dateityp und die Authentifizierung umfasst, um zu überprüfen, ob ein Benutzer zum Öffnen der Datei autorisiert ist.|
|Schutz|Der Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts beim Schützen der Dateien festgelegt wurden, erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Der Schutz der Dateien wird auf folgende Weise erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für Personen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben. Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Die Überwachungsprotokollierung von autorisierten Benutzern, die Dateien öffnen und auf diese zugreifen kommt vor. Nutzungsrechte werden jedoch nicht erzwungen.|
|Standardebene für Dateitypen|Dies ist die Standardebene des Schutzes für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt, [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den nativen Schutz unterstützt werden.|

Die Standardschutz Ebene, die der Azure Information Protection Unified-Bezeichnungs Client oder der Scanner anwendet, kann nicht geändert werden. Sie können jedoch ändern, welche Dateitypen geschützt werden. Weitere Informationen finden Sie unter [Ändern der zu schützenden Dateitypen](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect).

Der Schutz kann automatisch angewendet werden, wenn ein Benutzer eine Vertraulichkeits Bezeichnung auswählt, die ein Administrator konfiguriert hat, oder Benutzer können mithilfe von [Berechtigungsstufen](../configure-usage-rights.md#rights-included-in-permissions-levels)eigene benutzerdefinierte Schutzeinstellungen angeben.

### <a name="file-sizes-supported-for-protection"></a>Für den Schutz unterstützte Dateigrößen

Es gibt maximale Dateigrößen, die der Azure Information Protection Unified-Bezeichnung-Client für den Schutz unterstützt.

**Für Office-Dateien**:

|                                                     Office-Anwendung                                                      |                                                Maximale unterstützte Dateigröße                                                 |
|-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
|             Word 2010<br /><br />Word 2013<br /><br />Word 2016             |                                          32-Bit: 512 MB<br /><br />64-Bit: 512 MB                                          |
|           Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016           |                      32-Bit: 2 GB<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt                       |
| PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016 | 32-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt |
| | |

> [!IMPORTANT]
> Der erweiterte Support von Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows-und Office-Versionen](../known-issues.md#aip-and-legacy-windows-and-office-versions).
>

**Bei allen anderen Dateien**:

- So **schützen Sie andere Dateitypen** und öffnen diese Dateitypen im Azure Information Protection Viewer: die maximale Dateigröße wird nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt.

- So heben Sie den **Schutz von Dateien** mit dem Cmdlet " [aufheben-rmsfile](/powershell/module/azureinformationprotection/unprotect-rmsfile) " auf: die maximale Dateigröße, die für PST-Dateien unterstützt wird, beträgt 5 GB. Die Dateigröße für andere Dateitypen ist nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt.

> [!TIP]
> Informationen zum Suchen oder Wiederherstellen geschützter Elemente in großen PST-Dateien finden [Sie in der Anleitung zum Verwenden von Unprotect-RMSFile für eDiscovery](../configure-super-users.md#guidance-for-using-unprotect-rmsfile-for-ediscovery).
> 
### <a name="supported-file-types-for-classification-and-protection"></a>Unterstützte Dateitypen für Klassifizierung und Schutz

In der folgenden Tabelle ist eine Teilmenge der Dateitypen aufgeführt, die den systemeigenen Schutz durch den Azure Information Protection Unified Bezeichnung-Client unterstützen und auch klassifiziert werden können.

Diese Dateitypen sind separat aufgeführt, da wenn sie nativ geschützt sind, die Namenserweiterung der ursprünglichen Datei geändert wird und diese Dateien dadurch schreibgeschützt werden. Beachten Sie, dass wenn Dateien generisch geschützt sind, die ursprüngliche Namenserweiterung immer in PFILE geändert wird.

> [!WARNING]
> Wenn Sie über Firewalls, Webproxys oder Sicherheitssoftware verfügen, die Erweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie die Netzwerkgeräte und die Software möglicherweise zur Unterstützung der neuen Erweiterungen neu konfigurieren.

|Ursprüngliche Dateinamenerweiterung|Geschützte Dateierweiterung|
|--------------------------------|-------------------------------------|
|.txt|PTXT|
|.xml|PXML|
|.jpg|PJPG|
|JPEG|PJPEG|
|.png|PPNG|
|.tif|PTIF|
|TIFF|PTIFF|
|BMP|PBMP|
|.gif|PFIG|
|JPE|PJPE|
|JFIF|PJFIF|
|.jt|.pjt|

In der nächsten Tabelle werden die verbleibenden Dateitypen aufgelistet, die den systemeigenen Schutz durch den Azure Information Protection Unified Bezeichnung-Client unterstützen und auch klassifiziert werden können. Sie erkennen diese als Dateitypen für Microsoft Office-Apps. Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und Office Open XML für die folgenden Office-Programme: Word, Excel und PowerPoint.

Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />VSDM|VSDX<br /><br />VSSM<br /><br />VSSX<br /><br />VSTM<br /><br />VSTX<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

## <a name="file-types-that-are-excluded-from-classification-and-protection"></a>Von der Klassifizierung und dem Schutz ausgeschlossene Dateitypen

Um zu verhindern, dass Benutzer Dateien ändern, die für Vorgänge auf dem Computer entscheidend sind, werden einige Dateitypen und Ordner von der Klassifizierung und dem Schutz automatisch ausgeschlossen. Wenn Benutzer versuchen, diese Dateien mithilfe des Azure Information Protection Unified Bezeichnung-Clients zu klassifizieren oder zu schützen, wird eine Meldung angezeigt, dass Sie ausgeschlossen werden.

- **Ausgeschlossene Dateitypen**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msp, .msi, .pdb, .jar

- **Ausgeschlossener Ordner**:
    - Windows
    - Programme (\Programme und \Programme (x86))
    - \ProgramData
    - \AppData (für alle Benutzer)

### <a name="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-scanner"></a>Dateitypen, die von der Klassifizierung und vom Schutz durch die Azure Information Protection-Überprüfung ausgeschlossen sind

Standardmäßig schließt der Scanner auch dieselben Dateitypen wie der Azure Information Protection Unified-Bezeichnungs Client mit den folgenden Ausnahmen aus:

- . msg,. RTF und. rar werden ebenfalls ausgeschlossen.

Sie können die enthaltenen oder ausgeschlossenen Dateitypen für die Überprüfung der Dateien durch den Scanner ändern:

- Konfigurieren Sie [mithilfe des Azure-Portals](../deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal)**zu überprüfende Dateitypen** im Scannerprofil.
    
    > [!NOTE]
    > Überwachen Sie die Überprüfung sorgfältig,wenn Sie RTF-Dateien in der Überprüfung miteinbeziehen. Einige RTF-Dateien können nicht erfolgreich überprüft werden. Die Überprüfung wird nicht abgeschlossen, und Sie müssen den Dienst neustarten.

Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Um dieses Verhalten für den Scanner zu ändern, verwenden Sie die erweiterte PowerShell-Einstellung **pfilesupportedextensions**. Weitere Informationen finden Sie unter [Verwenden von PowerShell, um zu ändern, welche Dateitypen](../deploy-aip-scanner-configure-install.md#change-which-file-types-to-protect) vor den Überprüfungs Anweisungen für die Scanner geschützt sind.

### <a name="files-that-cannot-be-protected-by-default"></a>Dateien, die standardmäßig nicht geschützt werden können

Jede Datei, die Kenn Wort geschützt ist, kann nicht System intern durch den Azure Information Protection Unified-Bezeichnungs Client geschützt werden, es sei denn, die Datei ist zurzeit in der Anwendung geöffnet, die den Schutz anwendet. Am häufigsten sind PDF-Dateien kennwortgeschützt. Diese Funktion wird jedoch auch von anderen Anwendungen bereitgestellt, wie z.B. Office-Apps.

### <a name="limitations-for-container-files-such-as-zip-files"></a>Einschränkungen für Containerdateien, z.B. ZIP-Dateien

Weitere Informationen finden Sie unter [Azure Information Protection bekannten Probleme](../known-issues.md#client-support-for-container-files-such-as-zip-files).

## <a name="file-types-supported-for-inspection"></a>Bei der Überprüfung unterstützte Dateitypen

Ohne zusätzliche Konfiguration verwendet der Azure Information Protection Unified-Bezeichnungs Client den Inhalt von Dokumenten mithilfe von Windows IFilter. Windows-IFilter wird von Windows Search für die Indizierung verwendet. Daher können die folgenden Dateitypen bei Verwendung des PowerShell [-Befehls Set-aipfileclassification](/powershell/module/azureinformationprotection/set-aipfileclassification) überprüft werden.

|Anwendungstyp|Dateityp|
|--------------------------------|-------------------------------------|
|Word|Post docx;. docm;. dot;. dotm;. dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|PDF |.pdf|
|Text|.txt; .xml; .csv|

Wenn zusätzliche Konfigurationen vorgenommen werden, können auch andere Dateitypen überprüft werden. Beispielsweise können Sie [eine benutzerdefinierte Erweiterung für die Verwendung des vorhandenen Windows-Filters für Textdateien registrieren](/windows/desktop/search/-search-ifilter-registering-filters) und zusätzliche Filter von Softwareherstellern installieren.

Wenn Sie überprüfen möchten, welche Filter installiert sind, finden Sie weitere Informationen im Windows Search-Leitfaden für Entwickler unter [Finding a Filter Handler for a Given File Extension (Finden eines Filterhandlers für eine angegebene Erweiterung)](/windows/desktop/search/-search-ifilter-registering-filters#finding-a-filter-handler-for-a-given-file-extension).

In den folgenden Abschnitten finden Sie Konfigurationsanweisungen zum Überprüfen von ZIP- und TIFF-Dateien.

### <a name="to-inspect-zip-files"></a>Überprüfen von ZIP-Dateien

Der Azure Information Protection-Scanner und der PowerShell-Befehl [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification) können ZIP-Dateien überprüfen, wenn Sie die folgenden Anweisungen befolgen:

1. Installieren Sie [Office 2010 Filter Pack SP2](https://support.microsoft.com/help/2687447/description-of-office-2010-filter-pack-sp2) auf dem Computer, auf dem die Überprüfung ausgeführt wird.

2. Für den Scanner: Nachdem Sie vertrauliche Informationen gefunden haben und die ZIP-Datei mit einer Bezeichnung klassifiziert und geschützt werden soll, geben Sie die Dateinamenerweiterung ". zip" mit der erweiterten PowerShell-Einstellung " **pfilesupportedextensions**" an, wie unter [Verwenden von PowerShell zum ändern, welche Dateitypen](../deploy-aip-scanner-configure-install.md#change-which-file-types-to-protect) vor den Überprüfungs Anweisungen für Scanner geschützt sind.

Beispielszenario nach dem Ausführen dieser Schritte:

Eine Datei mit dem Namen **accounts.zip** enthält Excel-Kalkulationstabellen mit Kreditkartennummern. Sie haben eine **Vertraulichkeits Bezeichnung namens Confidential \ Finance**, die für die Ermittlung von Kreditkartennummern konfiguriert ist, und wendet die Bezeichnung automatisch mit Schutz an, der den Zugriff auf die Finanzgruppe einschränkt.

Nach der Überprüfung der Datei klassifiziert der Unified-Bezeichnungs Client aus der PowerShell-Sitzung diese Datei als **vertraulich \ Finanzen**, wendet den generischen Schutz auf die Datei an, sodass nur Mitglieder der Finanzgruppen Sie Entzippen können, und benennt die Datei **accounts.zip. Pfile** um.

### <a name="to-inspect-tiff-files-by-using-ocr"></a>Überprüfen von TIFF-Dateien unter Verwendung der OCR

Der PowerShell-Befehl [Set-aipfileclassiciations](/powershell/module/azureinformationprotection/set-aipfileclassification) kann die optische Zeichenerkennung (OCR) verwenden, um TIFF-Bilder mit der Dateinamenerweiterung ". TIFF" zu überprüfen, wenn Sie die Windows-TIFF-IFilter-Funktion installieren, und konfigurieren Sie dann die [Windows-TIFF-IFilter-Einstellungen](/previous-versions/windows/it-pro/windows-7/dd744701(v=ws.10)) auf dem Computer, auf dem die

Für den Scanner: Nachdem Sie vertrauliche Informationen gefunden haben und die TIFF-Datei mit einer Bezeichnung klassifiziert und geschützt werden soll, geben Sie diese Dateinamenerweiterung mit der erweiterten PowerShell-Einstellung " **pfilesupportedextensions**" an, wie unter [Verwenden von PowerShell zum Ändern](../deploy-aip-scanner-configure-install.md#change-which-file-types-to-protect) der von der Überprüfungs Anleitung für Scanner geschützten Dateitypen beschrieben.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie die vom Azure Information Protection Unified Bezeichnung-Client unterstützten Dateitypen identifiziert haben, finden Sie in den folgenden Ressourcen weitere Informationen, die Sie möglicherweise benötigen, um diesen Client zu unterstützen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)