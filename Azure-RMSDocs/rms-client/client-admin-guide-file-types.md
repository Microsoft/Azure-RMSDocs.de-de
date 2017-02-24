---
title: "Vom Azure Information Protection-Client unterstützte Dateitypen | Azure Information Protection"
description: "Technische Details zu den unterstützten Dateitypen, Dateierweiterungen und Schutzebenen für Administratoren, die für den Azure Information Protection-Client für Windows verantwortlich sind."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f4503c7383f9ffd9dc7e5cd3c676ec929bdc2802
ms.openlocfilehash: c556769aa34282063ae10190202a746eee33abe6


---


# <a name="file-types-supported-by-the-azure-information-protection-client"></a>Vom Azure Information Protection-Client unterstützte Dateitypen

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Der Azure Information Protection-Client kann Folgendes auf Dokumente und E-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Verwenden Sie die folgenden Informationen, um zu überprüfen, welche Dateitypen unterstützt werden, welche verschiedenen Schutzebenen verwendet werden, wie die Standardschutzebene geändert wird und welche Dateien automatisch von der Klassifizierung und dem Schutz ausgeschlossen (übersprungen) werden.

## <a name="file-types-supported-for-classification-only"></a>Nur für die Klassifizierung unterstützte Dateitypen

Die ausschließliche Klassifizierung wird für die folgenden Dateitypen unterstützt. Andere Dateitypen unterstützen die Klassifizierung, wenn sie zudem geschützt sind.

- **Microsoft Visio**: .vsdx, .vsdm, .vssx, .vssm, .vsd, .vdw, .vst

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft Office 97, Office 2010, Office 2003**: .xls, .xlt, .doc, .dot, .ppt, .pps, .pot

- **Microsoft XPS**: .xps .oxps

- **Bilder**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi.png, .tif, .tiff

- **SolidWorks**: .sldprt, .slddrw, .sldasm

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng

## <a name="file-types-supported-for-protection"></a>Für den Schutz unterstützte Dateitypen

Der Azure Information Protection-Client unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben wird.

|Typ des Schutzes|Systemeigenes Format|Generisch|
|----------------------|----------|-----------|
|Beschreibung|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Schutzebene, die Dateiverkapselung mit dem PFILE-Dateityp und Authentifizierung umfasst, um zu überprüfen, ob ein Benutzer zum Öffnen der Datei autorisiert ist.|
|Schutz|Dateien werden vollständig verschlüsselt, und der Schutz folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, wenn Dateien geschützt werden, vollständig erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Eine Überwachungsprotokollierung der autorisierten Benutzer, die auf Dateien zugreifen und diese öffnen, findet statt, es werden aber keine Nutzungsrechte durch nicht unterstützende Anwendungen erzwungen|
|Standard für Dateitypen|Dies ist die Standardschutzebene für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt: [Unterstützte Dateitypen und Dateinamenerweiterungen](#supported-file-types-for-protection-and-their-file-name-extensions).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den vollständigen Schutz unterstützt werden.|

Sie können die Standardschutzebene ändern, die der Azure Information Protection-Client anwendet. Sie können die Standardebene von systemeigen zu generisch oder von generisch zu systemeigen ändern und sogar verhindern, dass der Azure Information Protection-Client anwendet. Weitere Informationen finden Sie im Abschnitt [Ändern der Standardschutzebene von Dateien](#changing-the-default-protection-level-of-files) dieses Artikels.

Dieser Datenschutz kann automatisch angewendet werden, wenn ein Benutzer eine vom Administrator konfigurierte Bezeichnung auswählt. Benutzer können mithilfe von [Berechtigungsstufen](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels) auch eigene Schutzeinstellungen angeben. 

### <a name="supported-file-types-for-protection-and-their-file-name-extensions"></a>Unterstützte Dateitypen für den Schutz und ihre Dateierweiterungen
Die folgende Tabelle enthält die Dateitypen, die systemeigen vom Azure Information Protection-Client unterstützt werden. Für diese Dateitypen wird die ursprüngliche Namenserweiterung geändert, wenn systemeigener Schutz angewendet wird, und diese Dateien schreibgeschützt werden.

Für Dateien, die generisch geschützt sind, wird die ursprüngliche Namenserweiterung immer in PFILE geändert.

> [!WARNING]
> Wenn Sie Firewalls, Webproxys oder Sicherheitssoftware haben, die Dateinamenerweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie diese möglicherweise zur Unterstützung der neuen Dateinamenerweiterungen neu konfigurieren.

|Ursprüngliche Dateinamenerweiterung|Geschützte Dateierweiterung|
|--------------------------------|-------------------------------------|
|TXT|PTXT|
|XML|PXML|
|JPG|PJPG|
|JPEG|PPNG|
|PDF|PPDF|
|PNG|PPNG|
|TIF|PTIF|
|TIFF|PTIFF|
|BMP|PBMP|
|GIF|PGIF|
|GIFF|PGIFF|
|JPE|PJPE|
|JFIF|PJFIF|
|JT|PJT|


Die folgende Tabelle enthält die Dateitypen, die systemeigen vom Azure Information Protection-Client für Microsoft Office-Apps unterstützt werden. Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|DOC<br /><br />DOCM<br /><br />DOCX<br /><br />DOT<br /><br />DOTM<br /><br />DOTX<br /><br />POTM<br /><br />POTX<br /><br />PPS<br /><br />PPSM<br /><br />PPSX<br /><br />PPT<br /><br />PPTM|PPTX<br /><br />THMX<br /><br />XLA<br /><br />XLAM<br /><br />XLS<br /><br />XLSB<br /><br />XLT<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX<br /><br />XPS|

### <a name="changing-the-default-protection-level-of-files"></a>Ändern der Standardschutzebene von Dateien
Sie können ändern, wie der Azure Information Protection-Client Dateien durch Bearbeiten der Registrierung schützt. Beispielsweise können Sie erzwingen, dass Dateien, die systemeigenen Schutz unterstützen, durch den Azure Information Protection-Client generisch geschützt werden.

Dafür kann es folgende Gründe geben:

-   Um sicherzustellen, dass alle Benutzer die Datei öffnen können, wenn sie keine Anwendung haben, die systemeigenen Schutz unterstützt.

-   Um Sicherheitssysteme zu unterstützen, die Maßnahmen für Dateien anhand der Dateinamenerweiterung ergreifen und neu konfiguriert werden können, um die PFILE-Erweiterung zu unterstützen, aber nicht neu konfiguriert werden können, um mehrere Dateinamenerweiterungen für den systemeigenen Schutz zu unterstützen.

Auf ähnliche Weise können Sie erzwingen, dass der Azure Information Protection-Client systemeigenen Schutz auf Dateien anwendet, die in der Standardeinstellung durch generischen Schutz geschützt würden. Dies ist möglicherweise geeignet, wenn Sie eine Anwendung haben, die RMS-APIs unterstützt, zum Beispiel eine Line-of-Business-Anwendung, die von Ihren internen Entwicklern geschrieben wurde, oder eine Anwendung, die von einem unabhängigen Softwareanbieter (ISV) erworben wurde.

Sie können auch erzwingen, dass der Azure Information Protection-Client den Schutz von Dateien blockiert (der systemeigene oder generische Schutz wird nicht angewendet). Dies kann z. B. erforderlich sein, wenn Sie eine automatische Anwendung oder einen automatischen Dienst haben, die bzw. der eine bestimmte Datei öffnen muss, um ihren Inhalt zu verarbeiten. Wenn Sie den Schutz für einen Dateityp blockieren, können Benutzer den Azure Information Protection-Client nicht verwenden, um eine Datei mit diesem Dateityp zu schützen. Wenn sie es versuchen, wird eine Meldung angezeigt, dass der Administrator den Schutz verhindert hat, und sie müssen ihre Aktion zum Schutz der Datei abbrechen.

Bearbeiten Sie die folgenden Registrierungseinträge, um den Azure Information Protection-Client so zu konfigurieren, dass er generischen Schutz auf alle Dateien anwendet, die in der Standardeinstellung durch native Schutzfunktionen geschützt würden. Beachten Sie, dass Sie den Schlüssel „FileProtection“ manuell erstellen müssen, falls dieser nicht vorhanden ist.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**: Erstellen Sie einen neuen Schlüssel mit dem Namen *.

    Diese Einstellung gibt Dateien mit beliebiger Erweiterung an.

2.  Erstellen Sie im neu hinzugefügten Schlüssel für HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\* einen neuen Zeichenfolgenwert (REG_SZ) namens **Encryption** mit dem Datenwert **Pfile**.

    Diese Einstellung führt dazu, dass der Azure Information Protection-Client den generischen Schutz anwendet.

Diese beiden Einstellungen führen dazu, dass der Azure Information Protection-Client generischen Schutz auf alle Dateien mit einer Dateinamenerweiterung anwendet. Wenn dies Ihr Ziel ist, ist keine weitere Konfiguration erforderlich. Sie können aber auch Ausnahmen für bestimmte Dateitypen definieren, damit diese weiterhin systemeigen geschützt werden. Zu diesem Zweck müssen Sie drei zusätzliche Registrierungseinträge für jeden Dateityp bearbeiten:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**: Fügen Sie einen neuen Schlüssel mit dem Namen der Dateierweiterung (ohne vorangestellten Punkt) hinzu.

    Für Dateien mit der Erweiterung „.docx“ erstellen Sie beispielsweise einen Schlüssel namens **DOCX**.

2.  Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen DWORD-Wert namens **AllowPFILEEncryption** mit dem Wert **0**.

3.  Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen Zeichenfolgenwert namens **Encryption** mit dem Wert **Native**.

Durch diese Einstellungen sind alle Dateien generisch geschützt, mit Ausnahme der Dateien mit der Erweiterung DOCX, die systemeigen durch den Azure Information Protection-Client geschützt werden.

Wiederholen Sie diese drei Schritte für andere Dateitypen, die Sie als Ausnahmen definieren möchten, weil sie systemeigenen Schutz unterstützen und nicht durch den generisch Azure Information Protection-Client geschützt werden sollen.

Sie können ähnliche Registrierungseinträge für andere Szenarien durch Ändern des Werts der **Encryption** -Zeichenfolge vornehmen, die die folgenden Werte unterstützt:

-   **Pfile**: Allgemeiner Schutz

-   **Native**: systemeigener Schutz

-   **Off**: Schutz blockieren

Weitere Informationen finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](../develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet. 

## <a name="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-client"></a>Dateitypen, die von der Klassifizierung und vom Schutz durch den Azure Information Protection-Client ausgeschlossen sind

Um zu verhindern, dass Benutzer Dateien ändern, die für Vorgänge auf dem Computer entscheidend sind, werden einige Dateitypen und Ordner von der Klassifizierung und dem Schutz automatisch ausgeschlossen. Wenn Benutzer versuchen, diese Dateien zu klassifizieren oder zu schützen, wird eine Meldung angezeigt, dass diese Dateien ausgeschlossen sind.

- **Ausgeschlossene Dateitypen**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msp, .msi, .pdb, .jar

- **Ausgeschlossener Ordner**: 
    - Windows
    - Programme (\Programme und \Programme (x86))
    - \ProgramData 
    - \AppData (für alle Benutzer)




## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Dateitypen ermittelt haben, die vom Azure Information Protection-Client unterstützt werden, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO2-->


