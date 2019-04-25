---
title: Von der Azure Information Protection unified bezeichnungs-Client unterstützte Dateitypen
description: Technische Details zu unterstützten Dateitypen, Dateierweiterungen und Schutzebenen für Administratoren, die sind verantwortlich für den einheitlichen Azure Information Protection-Bezeichnung-Client für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: aca0fe5d3d9624676bc2bb12a772f5b753eb1a0d
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60183754"
---
# <a name="admin-guide-file-types-supported-by-the-azure-information-protection-unified-labeling-client"></a>Administratorhandbuch: Von der Azure Information Protection unified bezeichnungs-Client unterstützte Dateitypen

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*>
>
> *Anleitungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Der einheitliche Bezeichnung Azure Information Protection-Client kann Folgendes auf Dokumente und e-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Der einheitliche Bezeichnung Azure Information Protection-Client kann auch überprüfen, den Inhalt des einige Dateitypen, die mit der bekannten vertraulichen Informationstypen oder regulären Ausdrücken, die Sie definieren.

Verwenden Sie die folgende Informationen zum Überprüfen eines welche Dateitypen vom Azure Information Protection unified bezeichnungs-Client unterstützt verschiedenen Ebenen der Schutz und wie die standardschutzebene ändern, und ermitteln, welche Dateien automatisch zu verstehen ausgeschlossen (übersprungen), von der Klassifizierung und Schutz.

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

- Wenn die **allgemeine** vertraulichkeitsbezeichnung gilt der Klassifizierung und Schutz nicht angewendet: Sie können die Bezeichnung **Allgemein** auf eine Datei namens „sales.pdf“, aber nicht auf eine Datei namens „sales.txt“ anwenden. 

- Wenn die **vertraulich \ alle Mitarbeiter** vertraulichkeitsbezeichnung gilt, Klassifizierung und Schutz: Sie können diese Bezeichnung auf eine Datei namens „sales.pdf“ und eine Datei namens „sales.txt“ anwenden. Sie können den Schutz auch ohne die Klassifizierung auf diese Dateien anwenden.

## <a name="file-types-supported-for-protection"></a>Für den Schutz unterstützte Dateitypen

Der einheitliche Bezeichnung Azure Information Protection-Client unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben.

|Typ des Schutzes|Systemeigenes Format|Generisch|
|----------------------|----------|-----------|
|Beschreibung|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Schutzebene, die Dateiverkapselung mit dem PFILE-Dateityp und Authentifizierung umfasst, um zu überprüfen, ob ein Benutzer zum Öffnen der Datei autorisiert ist.|
|Schutz|Der Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts beim Schützen der Dateien festgelegt wurden, erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für Personen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben. Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Die Überwachungsprotokollierung von autorisierten Benutzern, die Dateien öffnen und auf diese zugreifen kommt vor. Nutzungsrechte werden jedoch nicht erzwungen.|
|Standard für Dateitypen|Dies ist die Standardschutzebene für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt, [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den nativen Schutz unterstützt werden.|

Sie können die standardschutzebene ändern, die der Azure Information Protection unified bezeichnungs-Client anwendet. Sie können die Standardebene von systemeigen zu generisch oder von generisch zu systemeigen ändern und sogar verhindern, dass den Azure Information Protection unified bezeichnungs-Client Schutz anwendet. Weitere Informationen finden Sie im Abschnitt [Ändern der Standardschutzebene von Dateien](#changing-the-default-protection-level-of-files) dieses Artikels.

Der Schutz kann automatisch angewendet werden, wenn ein Benutzer eine vertraulichkeitsbezeichnung auswählt, die ein Administrator konfiguriert hat, oder Benutzer können eigene schutzeinstellungen angeben, mit [Berechtigungsebenen](../configure-usage-rights.md#rights-included-in-permissions-levels). 

### <a name="file-sizes-supported-for-protection"></a>Für den Schutz unterstützte Dateigrößen

Es gibt maximalen Dateigrößen, die der Azure Information Protection unified bezeichnungs-Client für den Schutz unterstützt.

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

Die folgende Tabelle enthält einer Teilmenge der Typen von Dateien, die den nativen Schutz durch den Azure Information Protection unified bezeichnungs-Client und, auch klassifiziert werden kann unterstützen. 

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

Die nächste Tabelle enthält den verbleibenden Dateitypen, die den nativen Schutz durch den Azure Information Protection unified bezeichnungs-Client und, auch klassifiziert werden kann unterstützen. Sie erkennen diese als Dateitypen für Microsoft Office-Apps. Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und XML-Formate für Office Open, die die folgenden Office-Programme betreffen: Word, Excel und PowerPoint.

Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|DOC<br /><br />DOCM<br /><br />DOCX<br /><br />DOT<br /><br />DOTM<br /><br />DOTX<br /><br />POTM<br /><br />POTX<br /><br />PPS<br /><br />PPSM<br /><br />PPSX<br /><br />PPT<br /><br />PPTM<br /><br />PPTX<br /><br />VSDM|VSDX<br /><br />VSSM<br /><br />VSSX<br /><br />VSTM<br /><br />VSTX<br /><br />XLA<br /><br />XLAM<br /><br />XLS<br /><br />XLSB<br /><br />XLT<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX<br /><br />XPS|

### <a name="changing-the-default-protection-level-of-files"></a>Ändern der Standardschutzebene von Dateien
Sie können ändern, wie der Azure Information Protection unified bezeichnungs-Client Dateien durch Bearbeiten der Registrierung schützt. Beispielsweise können Sie Dateien erzwingen, die systemeigenen Schutz durch den Azure Information Protection unified bezeichnungs-Client generisch geschützt werden zu unterstützen.

Dafür kann es folgende Gründe geben:

- Um sicherzustellen, dass alle Benutzer die Datei öffnen können, wenn sie keine Anwendung haben, die systemeigenen Schutz unterstützt.

- Um Sicherheitssysteme zu unterstützen, die Maßnahmen für Dateien anhand der Dateinamenerweiterung ergreifen und neu konfiguriert werden können, um die PFILE-Erweiterung zu unterstützen, aber nicht neu konfiguriert werden können, um mehrere Dateinamenerweiterungen für den systemeigenen Schutz zu unterstützen.

Auf ähnliche Weise können Sie erzwingen, die einheitlichen Azure Information Protection-Bezeichnung-Client systemeigenen Schutz auf Dateien, die in der Standardeinstellung generischen Schutz angewendet hätten anwendet. Diese Aktion kann sinnvoll sein, wenn Sie über eine Anwendung verfügen, die RMS-APIs unterstützt. Beispiele hierfür sind eine Branchenanwendung, die von internen Entwicklern geschrieben wurde, oder eine Anwendung, die von einem unabhängigen Softwareanbieter erworben wurde.

Sie können auch erzwingen, den Azure Information Protection unified bezeichnungs Client den Schutz von Dateien blockiert (nicht systemeigene oder generische Schutz angewendet). Diese Aktion kann z.B. erforderlich sein, wenn Sie über eine automatische Anwendung oder einen automatischen Dienst verfügen, die bzw. der eine bestimmte Datei öffnen muss, um ihren Inhalt zu verarbeiten. Wenn Sie den Schutz für einen Dateityp blockieren, können nicht Benutzer den Azure Information Protection unified bezeichnungs-Client verwenden, um eine Datei, die diesem Dateityp zu schützen. Wenn sie es versuchen, wird eine Meldung angezeigt, dass der Administrator den Schutz verhindert hat, und sie müssen ihre Aktion zum Schutz der Datei abbrechen.

Zum Konfigurieren der Azure Information Protection unified bezeichnungs Clients generischen Schutz anwendet, um alle Dateien, die in der Standardeinstellung systemeigenen Schutz aktiviert hätte, stellen Sie die folgenden Registrierungseinträge vor. Beachten Sie, dass Sie den Schlüssel „FileProtection“ manuell erstellen müssen, falls dieser nicht vorhanden ist.

1. Erstellen Sie einen neuen Schlüssel mit dem Namen * für den folgenden Registrierungspfad, der Dateien mit beliebiger Erweiterung anzeigt:

    - Für eine 32-Bit-Version von Windows: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**

    - Für eine 64-Bit-Version von Windows: **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection** und **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**

2. Erstellen Sie im neu hinzugefügten Schlüssel (zum Beispiel HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\*) einen neuen Zeichenfolgenwert (REG_SZ) mit dem Namen **Encryption** und dem Datenwert **Pfile**.

    Diese Einstellung führt dazu, dass der Azure Information Protection-Client den generischen Schutz anwendet.

Diese beiden Einstellungen führen in der Azure Information Protection unified bezeichnungs-Client generischen Schutz auf alle Dateien mit einer Dateinamenerweiterung anwendet. Wenn dies Ihr Ziel ist, ist keine weitere Konfiguration erforderlich. Sie können aber auch Ausnahmen für bestimmte Dateitypen definieren, damit diese weiterhin systemeigen geschützt werden. Zu diesem Zweck müssen Sie drei (für Windows 32-Bit) oder 6 (für Windows 64-Bit) zusätzliche Registrierungseinträge für jeden Dateityp bearbeiten:

1. Für **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection** und **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection** (sofern zutreffend): Fügen Sie einen neuen Schlüssel mit dem Namen des der Dateinamenerweiterung (ohne vorangestellten Punkt) hinzu.

    Für Dateien mit der Erweiterung „.docx“ erstellen Sie beispielsweise einen Schlüssel namens **DOCX**.

2. Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen DWORD-Wert namens **AllowPFILEEncryption** mit dem Wert **0**.

3. Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen Zeichenfolgenwert namens **Encryption** mit dem Wert **Native**.

Durch diese Einstellungen sind alle Dateien generisch geschützt, mit Ausnahme von Dateien mit der Erweiterung DOCX. Diese Dateien werden nativ vom Azure Information Protection unified bezeichnungs-Client geschützt.

Wiederholen Sie die folgenden drei Schritte für andere Dateitypen, die als Ausnahmen definieren, weil sie systemeigenen Schutz unterstützen und Sie möchten nicht durch den Azure Information Protection unified bezeichnungs-Client generisch geschützt werden sollen.

Sie können ähnliche Registrierungseinträge für andere Szenarien durch Ändern des Werts der **Encryption** -Zeichenfolge vornehmen, die die folgenden Werte unterstützt:

- **Pfile**: Allgemeiner Schutz

- **Native**: systemeigener Schutz

- **Off**: Schutz blockieren

Nachdem Sie diese Registrierungsänderungen vorgenommen haben, müssen Sie den Computer nicht neu starten. Wenn Sie jedoch PowerShell-Befehle zum Schützen von Dateien verwenden, müssen Sie eine neue PowerShell-Sitzung starten, damit die Änderungen wirksam werden.

Weitere Informationen zum Bearbeiten der Registrierung, um die Standardschutzebene von Dateien zu ändern, finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](../develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet.

## <a name="file-types-that-are-excluded-from-classification-and-protection"></a>Von der Klassifizierung und dem Schutz ausgeschlossene Dateitypen

Um zu verhindern, dass Benutzer Dateien ändern, die für Vorgänge auf dem Computer entscheidend sind, werden einige Dateitypen und Ordner von der Klassifizierung und dem Schutz automatisch ausgeschlossen. Wenn Benutzer versuchen, zu klassifizieren oder diese Dateien mithilfe des Azure Information Protection unified bezeichnungs-Clients zu schützen, wird eine Meldung, dass sie ausgeschlossen werden angezeigt.

- **Ausgeschlossene Dateitypen**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msg,.msp, .msi, .pdb, .jar


- **Ausgeschlossener Ordner**: 
    - Windows
    - Programme (\Programme und \Programme (x86))
    - \ProgramData 
    - \AppData (für alle Benutzer)


### <a name="files-that-cannot-be-protected-by-default"></a>Dateien, die standardmäßig nicht geschützt werden können

Jede Datei, die ein Kennwort geschützt ist, kann nicht nativ vom Azure Information Protection unified bezeichnungs-Client geschützt werden, es sei denn, die Datei derzeit in der Anwendung geöffnet ist, die den Schutz anwendet. Am häufigsten sind PDF-Dateien kennwortgeschützt. Diese Funktion wird jedoch auch von anderen Anwendungen bereitgestellt, wie z.B. Office-Apps.

### <a name="limitations-for-container-files-such-as-zip-files"></a>Einschränkungen für Containerdateien, z.B. ZIP-Dateien

Containerdateien sind Dateien, die andere Dateien enthalten. Ein typisches Beispiel sind ZIP-Dateien, die komprimierte Dateien enthalten. Weitere Beispiele sind RAR-, .7z- und MSG-Dateien sowie PDF-Dokumente, die Anlagen enthalten.

Sie können diese Containerdateien klassifizieren und schützen, jedoch werden die Klassifizierung und der Schutz nicht auf jede Datei im Container angewendet.

Bei einer Containerdatei, die klassifizierte und geschützte Dateien enthält, müssen Sie zuerst die Dateien extrahieren, um die Einstellungen für die Klassifizierung oder den Schutz zu ändern.

Mit dem Azure Information Protection-Viewer können keine Anlagen in einem geschützten PDF-Dokument geöffnet werden. In diesem Szenario sind die Anlagen bei geöffnetem Dokument im Viewer nicht sichtbar.

## <a name="next-steps"></a>Nächste Schritte
Nun, da Sie die vom Azure Information Protection unified bezeichnungs-Client unterstützte Dateitypen ermittelt haben, finden Sie unter den folgenden Ressourcen für zusätzliche Informationen, Sie zur Unterstützung dieses Clients müssen eventuell:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)

