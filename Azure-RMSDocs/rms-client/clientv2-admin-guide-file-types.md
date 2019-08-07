---
title: Unterstützte Dateitypen-Azure Information Protection Unified-Bezeichnungs Client
description: Technische Details zu unterstützten Dateitypen, Dateinamen Erweiterungen und Schutz Ebenen für Administratoren, die für den Azure Information Protection Unified Bezeichnung-Client für Windows verantwortlich sind.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ef2b68b531b39a83f88ee9f8f37a64955950f00d
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68789936"
---
# <a name="admin-guide-file-types-supported-by-the-azure-information-protection-unified-labeling-client"></a>Administratorhandbuch: Vom Azure Information Protection Unified Bezeichnung-Client unterstützte Dateitypen

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*>
>
> *Anweisungen für: [Azure Information Protection Unified Bezeichnung-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Der Azure Information Protection Unified Bezeichnung-Client kann Folgendes auf Dokumente und e-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Der Azure Information Protection Unified-Bezeichnungs Client kann auch den Inhalt einiger Dateitypen mithilfe von bekannten sensiblen Informationstypen oder regulären Ausdrücken untersuchen, die Sie definieren.

Verwenden Sie die folgenden Informationen, um zu überprüfen, welche Dateitypen der Azure Information Protection Unified-Bezeichnung-Client unterstützt, wie Sie die verschiedenen Schutz Ebenen verstehen und wie Sie die Standardschutz Ebene ändern und welche Dateien automatisch aus Klassifizierung und Schutz ausgeschlossen (übersprungen).

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

- **Microsoft Office:** Dateitypen in der folgenden Tabelle.

    Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und XML-Formate für Office Open, die die folgenden Office-Programme betreffen: Word, Excel und PowerPoint.

    |Office-Dateityp|Office-Dateityp|
    |----------------------------------|----------------------------------|
    |DOC<br /><br />DOCM<br /><br />DOCX<br /><br />DOT<br /><br />DOTM<br /><br />DOTX<br /><br />POTM<br /><br />POTX<br /><br />PPS<br /><br />PPSM<br /><br />PPSX<br /><br />PPT<br /><br />PPTM<br /><br />PPTX<br /><br />VDW<br /><br />VSD|VSDM<br /><br /> VSDX<br /><br />VSS<br /><br />VSSM<br /><br />VST<br /><br />VSTM<br /><br />VSSX<br /><br />VSTX<br /><br />XLS<br /><br />XLSB<br /><br />XLT<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX|

Zusätzliche Dateitypen unterstützen die Klassifizierung, wenn sie zudem geschützt sind. Weitere Informationen zu diesen Dateitypen finden Sie im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).

Beispiele:

- Wenn die Bezeichnung " **General** Sensitivität" die Klassifizierung anwendet und keinen Schutz anwendet: Sie können die Bezeichnung **Allgemein** auf eine Datei namens „sales.pdf“, aber nicht auf eine Datei namens „sales.txt“ anwenden. 

- Wenn die Vertraulichkeits Bezeichnung " **vertraulich \ alle Mitarbeiter** " die Klassifizierung und den Schutz anwendet: Sie können diese Bezeichnung auf eine Datei namens „sales.pdf“ und eine Datei namens „sales.txt“ anwenden. Sie können den Schutz auch ohne die Klassifizierung auf diese Dateien anwenden.

## <a name="file-types-supported-for-protection"></a>Für den Schutz unterstützte Dateitypen

Der Azure Information Protection Unified Bezeichnung-Client unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben.

|Typ des Schutzes|Systemeigenes Format|Generisch|
|----------------------|----------|-----------|
|Beschreibung|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Schutzebene, die Dateiverkapselung mit dem PFILE-Dateityp und Authentifizierung umfasst, um zu überprüfen, ob ein Benutzer zum Öffnen der Datei autorisiert ist.|
|Schutz|Der Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts beim Schützen der Dateien festgelegt wurden, erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für Personen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben. Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Die Überwachungsprotokollierung von autorisierten Benutzern, die Dateien öffnen und auf diese zugreifen kommt vor. Nutzungsrechte werden jedoch nicht erzwungen.|
|Standard für Dateitypen|Dies ist die Standardschutzebene für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt, [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den nativen Schutz unterstützt werden.|

Derzeit ist es nicht möglich, die Standardschutz Ebene zu ändern, die der Azure Information Protection vereinheitlichte Bezeichnung-Client anwendet.

Der Schutz kann automatisch angewendet werden, wenn ein Benutzer eine Vertraulichkeits Bezeichnung auswählt, die ein Administrator konfiguriert hat, oder Benutzer können mithilfe von [Berechtigungsstufen](../configure-usage-rights.md#rights-included-in-permissions-levels)eigene benutzerdefinierte Schutzeinstellungen angeben. 

### <a name="file-sizes-supported-for-protection"></a>Für den Schutz unterstützte Dateigrößen

Es gibt maximale Dateigrößen, die der Azure Information Protection Unified-Bezeichnung-Client für den Schutz unterstützt.

- **Bei Office-Dateien:**


  |                                                     Office-Anwendung                                                      |                                                Maximale unterstützte Dateigröße                                                 |
  |-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
  |             Word 2010<br /><br />Word 2013<br /><br />Word 2016             |                                          32-Bit: 512 MB<br /><br />64-Bit: 512 MB                                          |
  |           Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016           |                      32-Bit: 2 GB<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt                       |
  | PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016 | 32-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt |


- **Bei allen anderen Dateien**: 

  - Gehen Sie wie folgt vor, um andere Dateitypen zu schützen und im Azure Information Protection-Viewer zu öffnen: Die maximale Dateigröße wird nur durch den verfügbaren Speicherplatz und den Arbeitsspeicher beschränkt.

  - Gehen Sie wie folgt vor, um den Schutz von Dateien mithilfe des [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile)-Cmdlets aufzuheben: PST-Dateien dürfen eine Größe von höchstens 5 GB haben. Die Dateigröße für andere Dateitypen ist nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt.

    Tipp: Wenn Sie geschützte Elemente in großen PST-Dateien suchen oder wiederherstellen müssen, finden Sie hierzu weitere Informationen unter [Anleitung für die Verwendung von Unprotect-RMSFile für eDiscovery](../configure-super-users.md#guidance-for-using-unprotect-rmsfile-for-ediscovery).

### <a name="supported-file-types-for-classification-and-protection"></a>Unterstützte Dateitypen für Klassifizierung und Schutz

In der folgenden Tabelle ist eine Teilmenge der Dateitypen aufgeführt, die den systemeigenen Schutz durch den Azure Information Protection Unified Bezeichnung-Client unterstützen und auch klassifiziert werden können. 

Diese Dateitypen sind separat aufgeführt, da wenn sie nativ geschützt sind, die Namenserweiterung der ursprünglichen Datei geändert wird und diese Dateien dadurch schreibgeschützt werden. Beachten Sie, dass wenn Dateien generisch geschützt sind, die ursprüngliche Namenserweiterung immer in PFILE geändert wird.

> [!WARNING]
> Wenn Sie über Firewalls, Webproxys oder Sicherheitssoftware verfügen, die Erweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie die Netzwerkgeräte und die Software möglicherweise zur Unterstützung der neuen Erweiterungen neu konfigurieren.

|Ursprüngliche Dateinamenerweiterung|Geschützte Dateierweiterung|
|--------------------------------|-------------------------------------|
|TXT|PTXT|
|XML|PXML|
|JPG|PJPG|
|JPEG|PJPEG|
|PNG|PPNG|
|TIF|PTIF|
|TIFF|PTIFF|
|BMP|PBMP|
|GIF|PGIF|
|JPE|PJPE|
|JFIF|PJFIF|
|JT|PJT|

In der nächsten Tabelle werden die verbleibenden Dateitypen aufgelistet, die den systemeigenen Schutz durch den Azure Information Protection Unified Bezeichnung-Client unterstützen und auch klassifiziert werden können. Sie erkennen diese als Dateitypen für Microsoft Office-Apps. Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und XML-Formate für Office Open, die die folgenden Office-Programme betreffen: Word, Excel und PowerPoint.

Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|DOC<br /><br />DOCM<br /><br />DOCX<br /><br />DOT<br /><br />DOTM<br /><br />DOTX<br /><br />POTM<br /><br />POTX<br /><br />PPS<br /><br />PPSM<br /><br />PPSX<br /><br />PPT<br /><br />PPTM<br /><br />PPTX<br /><br />VSDM|VSDX<br /><br />VSSM<br /><br />VSSX<br /><br />VSTM<br /><br />VSTX<br /><br />XLA<br /><br />XLAM<br /><br />XLS<br /><br />XLSB<br /><br />XLT<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX<br /><br />XPS|


## <a name="file-types-that-are-excluded-from-classification-and-protection"></a>Von der Klassifizierung und dem Schutz ausgeschlossene Dateitypen

Um zu verhindern, dass Benutzer Dateien ändern, die für Vorgänge auf dem Computer entscheidend sind, werden einige Dateitypen und Ordner von der Klassifizierung und dem Schutz automatisch ausgeschlossen. Wenn Benutzer versuchen, diese Dateien mithilfe des Azure Information Protection Unified Bezeichnung-Clients zu klassifizieren oder zu schützen, wird eine Meldung angezeigt, dass Sie ausgeschlossen werden.

- **Ausgeschlossene Dateitypen**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msg,.msp, .msi, .pdb, .jar


- **Ausgeschlossener Ordner**: 
    - Windows
    - Programme (\Programme und \Programme (x86))
    - \ProgramData 
    - \AppData (für alle Benutzer)

### <a name="files-that-cannot-be-protected-by-default"></a>Dateien, die standardmäßig nicht geschützt werden können

Jede Datei, die Kenn Wort geschützt ist, kann nicht System intern durch den Azure Information Protection Unified-Bezeichnungs Client geschützt werden, es sei denn, die Datei ist zurzeit in der Anwendung geöffnet, die den Schutz anwendet. Am häufigsten sind PDF-Dateien kennwortgeschützt. Diese Funktion wird jedoch auch von anderen Anwendungen bereitgestellt, wie z.B. Office-Apps.

### <a name="limitations-for-container-files-such-as-zip-files"></a>Einschränkungen für Containerdateien, z.B. ZIP-Dateien

Containerdateien sind Dateien, die andere Dateien enthalten. Ein typisches Beispiel sind ZIP-Dateien, die komprimierte Dateien enthalten. Weitere Beispiele sind RAR-, .7z- und MSG-Dateien sowie PDF-Dokumente, die Anlagen enthalten.

Sie können diese Containerdateien klassifizieren und schützen, jedoch werden die Klassifizierung und der Schutz nicht auf jede Datei im Container angewendet.

Bei einer Containerdatei, die klassifizierte und geschützte Dateien enthält, müssen Sie zuerst die Dateien extrahieren, um die Einstellungen für die Klassifizierung oder den Schutz zu ändern.

Mit dem Azure Information Protection-Viewer können keine Anlagen in einem geschützten PDF-Dokument geöffnet werden. In diesem Szenario sind die Anlagen bei geöffnetem Dokument im Viewer nicht sichtbar.

## <a name="file-types-supported-for-inspection"></a>Bei der Überprüfung unterstützte Dateitypen

Ohne zusätzliche Konfiguration verwendet der Azure Information Protection Unified-Bezeichnungs Client den Inhalt von Dokumenten mithilfe von Windows IFilter. Windows-IFilter wird von Windows Search für die Indizierung verwendet. Daher können die folgenden Dateitypen bei Verwendung des PowerShell [-Befehls Set-aipfileclassification](/powershell/module/azureinformationprotection/set-aipfileclassification) überprüft werden.

|Anwendungstyp|Dateityp|
|--------------------------------|-------------------------------------|
|Word|.docx; .docm; .dotm; .dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|PDF |PDF|
|Text|.txt; .xml; .csv|

Wenn zusätzliche Konfigurationen vorgenommen werden, können auch andere Dateitypen überprüft werden. Beispielsweise können Sie [eine benutzerdefinierte Erweiterung für die Verwendung des vorhandenen Windows-Filters für Textdateien registrieren](https://docs.microsoft.com/windows/desktop/search/-search-ifilter-registering-filters) und zusätzliche Filter von Softwareherstellern installieren.

Wenn Sie überprüfen möchten, welche Filter installiert sind, finden Sie weitere Informationen im Windows Search-Leitfaden für Entwickler unter [Finding a Filter Handler for a Given File Extension (Finden eines Filterhandlers für eine angegebene Erweiterung)](https://docs.microsoft.com/windows/desktop/search/-search-ifilter-registering-filters#finding-a-filter-handler-for-a-given-file-extension).

In den folgenden Abschnitten finden Sie Konfigurationsanweisungen zum Überprüfen von ZIP- und TIFF-Dateien.

### <a name="to-inspect-zip-files"></a>Überprüfen von ZIP-Dateien

Mit dem PowerShell [-Befehl Set-aipfileclassification](/powershell/module/azureinformationprotection/set-aipfileclassification) können ZIP-Dateien überprüft werden, wenn Sie das [Office 2010 Filter Pack SP2](https://support.microsoft.com/en-us/help/2687447/description-of-office-2010-filter-pack-sp2) auf dem Computer installieren, auf dem die PowerShell-Sitzung ausgeführt wird.

Beispielszenario nach dem Ausführen dieser Schritte: 

Eine Datei mit dem Namen **accounts.zip** enthält Excel-Kalkulationstabellen mit Kreditkartennummern. Sie haben eine Vertraulichkeits Bezeichnung namens **Confidential \ Finance**, die für die Ermittlung von Kreditkartennummern konfiguriert ist, und wendet die Bezeichnung automatisch mit Schutz an, der den Zugriff auf die Finanzgruppe einschränkt. 

Nach der Überprüfung der Datei klassifiziert der Unified-Bezeichnungs Client aus der PowerShell-Sitzung diese Datei als **vertraulich \ Finanzen**, wendet den generischen Schutz auf die Datei an, sodass nur Mitglieder der Finanzgruppen Sie entpacken können, und benennt die Datei **um. Accounts. zip. Pfile**.

### <a name="to-inspect-tiff-files-by-using-ocr"></a>Überprüfen von TIFF-Dateien unter Verwendung der OCR

Der PowerShell-Befehl [Set-aipfileclassiciations](/powershell/module/azureinformationprotection/set-aipfileclassification) kann mithilfe der optischen Zeichenerkennung (OCR) TIFF-Bilder mit der Dateinamenerweiterung ". TIFF" untersuchen, wenn Sie die Windows-TIFF-IFilter-Funktion installieren und anschließend [Windows-TIFF-IFilter konfigurieren. Einstellungen](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/dd744701%28v%3dws.10%29) auf dem Computer, auf dem die PowerShell-Sitzung ausgeführt wird.

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie die vom Azure Information Protection Unified Bezeichnung-Client unterstützten Dateitypen identifiziert haben, finden Sie in den folgenden Ressourcen weitere Informationen, die Sie möglicherweise benötigen, um diesen Client zu unterstützen:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)

