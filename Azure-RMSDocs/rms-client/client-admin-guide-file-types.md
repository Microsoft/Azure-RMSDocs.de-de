---
title: "Von Azure Information Protection unterstützte Dateitypen"
description: "Technische Details zu den unterstützten Dateitypen, Dateierweiterungen und Schutzebenen für Administratoren, die für den Azure Information Protection-Client für Windows verantwortlich sind."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4f187b3fa991fb4ed3a11ded34fa663dc6b4bafc
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="file-types-supported-by-the-azure-information-protection-client" class="xliff"></a>

# Vom Azure Information Protection-Client unterstützte Dateitypen

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Der Azure Information Protection-Client kann Folgendes auf Dokumente und E-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Verwenden Sie die folgenden Informationen, um zu überprüfen, welche Dateitypen unterstützt werden, welche verschiedenen Schutzebenen verwendet werden, wie die Standardschutzebene geändert wird und welche Dateien automatisch von der Klassifizierung und dem Schutz ausgeschlossen (übersprungen) werden.

<a id="file-types-supported-for-classification-only" class="xliff"></a>

## Nur für die Klassifizierung unterstützte Dateitypen

Die ausschließliche Klassifizierung wird für die folgenden Dateitypen unterstützt. Zusätzliche Dateitypen unterstützen die Klassifizierung, wenn sie auch geschützt sind (weitere Informationen finden Sie im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection)).

- **Adobe Portable Document Format**: .pdf

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

<a id="file-types-supported-for-protection" class="xliff"></a>

## Für den Schutz unterstützte Dateitypen

Der Azure Information Protection-Client unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben wird.

|Typ des Schutzes|Systemeigenes Format|Generisch|
|----------------------|----------|-----------|
|Beschreibung|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Schutzebene, die Dateiverkapselung mit dem PFILE-Dateityp und Authentifizierung umfasst, um zu überprüfen, ob ein Benutzer zum Öffnen der Datei autorisiert ist.|
|Schutz|Der Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, wenn Dateien geschützt werden, vollständig erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Die Überwachungsprotokollierung von autorisierten Benutzern, die Dateien öffnen und auf diese zugreifen kommt vor. Nutzungsrechte werden jedoch nicht erzwungen.|
|Standard für Dateitypen|Dies ist die Standardschutzebene für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt, [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den nativen Schutz unterstützt werden.|

Sie können die Standardschutzebene ändern, die der Azure Information Protection-Client anwendet. Sie können die Standardebene von systemeigen zu generisch oder von generisch zu systemeigen ändern und sogar verhindern, dass der Azure Information Protection-Client anwendet. Weitere Informationen finden Sie im Abschnitt [Ändern der Standardschutzebene von Dateien](#changing-the-default-protection-level-of-files) dieses Artikels.

Dieser Datenschutz kann automatisch angewendet werden, wenn ein Benutzer eine vom Administrator konfigurierte Bezeichnung auswählt. Benutzer können mithilfe von [Berechtigungsstufen](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels) auch eigene Schutzeinstellungen angeben. 

<a id="file-sizes-supported-for-protection" class="xliff"></a>

### Für den Schutz unterstützte Dateigrößen

Für den Schutz werden folgende maximale Dateigrößen vom Azure Information Protection-Client unterstützt.

- **Bei Office-Dateien:**
    
    |Office-Anwendung|Maximale unterstützte Dateigröße|
    |--------------------------------|-------------------------------------|
    |Word 2007 (nur von AD RMS unterstützt)<br /><br />Word 2010<br /><br />Word 2013<br /><br />Word 2016|32-Bit: 512 MB<br /><br />64-Bit: 512 MB
    |Excel 2007 (nur von AD RMS unterstützt)<br /><br />Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016|32-Bit: 2 GB<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt|
    |PowerPoint 2007 (nur von AD RMS unterstützt)<br /><br />PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016|32-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt

- **Bei allen anderen Dateien**: 1 GB

<a id="supported-file-types-for-classification-and-protection" class="xliff"></a>

### Unterstützte Dateitypen für Klassifizierung und Schutz

Die folgende Tabelle enthält eine Teilmenge der Typen von Dateien, die den nativen Schutz durch den Azure Information Protection-Client unterstützen und die auch klassifiziert werden können. 

Diese Dateitypen sind separat aufgeführt, da wenn sie nativ geschützt sind, die Namenserweiterung der ursprünglichen Datei geändert wird und diese Dateien dadurch schreibgeschützt werden. Beachten Sie, dass wenn Dateien generisch geschützt sind, die ursprüngliche Namenserweiterung immer in PFILE geändert wird.

> [!WARNING]
> Wenn Sie Firewalls, Webproxys oder Sicherheitssoftware haben, die Dateinamenerweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie diese möglicherweise zur Unterstützung der neuen Dateinamenerweiterungen neu konfigurieren.

|Ursprüngliche Dateinamenerweiterung|Geschützte Dateierweiterung|
|--------------------------------|-------------------------------------|
|TXT|PTXT|
|XML|PXML|
|JPG|PJPG|
|JPEG|PJPEG|
|PDF|PPDF|
|PNG|PPNG|
|TIF|PTIF|
|TIFF|PTIFF|
|BMP|PBMP|
|GIF|PGIF|
|JPE|PJPE|
|JFIF|PJFIF|
|JT|PJT|

Die nächste Tabelle enthält die verbleibenden Dateitypen, die den nativen Schutz durch den Azure Information Protection-Client unterstützen und auch klassifiziert werden können. Sie erkennen diese als Dateitypen für Microsoft Office-Apps. 

Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|DOC<br /><br />DOCM<br /><br />DOCX<br /><br />DOT<br /><br />DOTM<br /><br />DOTX<br /><br />POTM<br /><br />POTX<br /><br />PPS<br /><br />PPSM<br /><br />PPSX<br /><br />PPT<br /><br />PPTM|PPTX<br /><br />THMX<br /><br />XLA<br /><br />XLAM<br /><br />XLS<br /><br />XLSB<br /><br />XLT<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX<br /><br />XPS|

<a id="changing-the-default-protection-level-of-files" class="xliff"></a>

### Ändern der Standardschutzebene von Dateien
Sie können ändern, wie der Azure Information Protection-Client Dateien durch Bearbeiten der Registrierung schützt. Beispielsweise können Sie erzwingen, dass Dateien, die systemeigenen Schutz unterstützen, durch den Azure Information Protection-Client generisch geschützt werden.

Dafür kann es folgende Gründe geben:

- Um sicherzustellen, dass alle Benutzer die Datei öffnen können, wenn sie keine Anwendung haben, die systemeigenen Schutz unterstützt.

- Um Sicherheitssysteme zu unterstützen, die Maßnahmen für Dateien anhand der Dateinamenerweiterung ergreifen und neu konfiguriert werden können, um die PFILE-Erweiterung zu unterstützen, aber nicht neu konfiguriert werden können, um mehrere Dateinamenerweiterungen für den systemeigenen Schutz zu unterstützen.

Auf ähnliche Weise können Sie erzwingen, dass der Azure Information Protection-Client systemeigenen Schutz auf Dateien anwendet, die in der Standardeinstellung durch generischen Schutz geschützt würden. Dies ist möglicherweise geeignet, wenn Sie eine Anwendung haben, die RMS-APIs unterstützt, zum Beispiel eine Line-of-Business-Anwendung, die von Ihren internen Entwicklern geschrieben wurde, oder eine Anwendung, die von einem unabhängigen Softwareanbieter (ISV) erworben wurde.

Sie können auch erzwingen, dass der Azure Information Protection-Client den Schutz von Dateien blockiert (der systemeigene oder generische Schutz wird nicht angewendet). Dies kann z. B. erforderlich sein, wenn Sie eine automatische Anwendung oder einen automatischen Dienst haben, die bzw. der eine bestimmte Datei öffnen muss, um ihren Inhalt zu verarbeiten. Wenn Sie den Schutz für einen Dateityp blockieren, können Benutzer den Azure Information Protection-Client nicht verwenden, um eine Datei mit diesem Dateityp zu schützen. Wenn sie es versuchen, wird eine Meldung angezeigt, dass der Administrator den Schutz verhindert hat, und sie müssen ihre Aktion zum Schutz der Datei abbrechen.

Bearbeiten Sie die folgenden Registrierungseinträge, um den Azure Information Protection-Client so zu konfigurieren, dass er generischen Schutz auf alle Dateien anwendet, die in der Standardeinstellung durch native Schutzfunktionen geschützt würden. Beachten Sie, dass Sie den Schlüssel „FileProtection“ manuell erstellen müssen, falls dieser nicht vorhanden ist.

1. Erstellen Sie einen neuen Schlüssel mit dem Namen * für den folgenden Registrierungspfad, der Dateien mit beliebiger Erweiterung anzeigt:
    
    - Für 32-Bit-Versionen von Windows: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**
    
    - Für 64-Bit-Versionen von Windows: **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection**

2. Erstellen Sie im neu hinzugefügten Schlüssel (zum Beispiel HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\*) einen neuen Zeichenfolgenwert (REG_SZ) mit dem Namen **Encryption** und dem Datenwert **Pfile**.

    Diese Einstellung führt dazu, dass der Azure Information Protection-Client den generischen Schutz anwendet.

Diese beiden Einstellungen führen dazu, dass der Azure Information Protection-Client generischen Schutz auf alle Dateien mit einer Dateinamenerweiterung anwendet. Wenn dies Ihr Ziel ist, ist keine weitere Konfiguration erforderlich. Sie können aber auch Ausnahmen für bestimmte Dateitypen definieren, damit diese weiterhin systemeigen geschützt werden. Zu diesem Zweck müssen Sie drei zusätzliche Registrierungseinträge für jeden Dateityp bearbeiten:

1. Für **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection** (32-Bit Windows) oder **HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\FileProtection** (64-Bit Windows): Fügen Sie einen neuen Schlüssel hinzu, der den Namen der Dateierweiterung trägt (ohne den vorangestellten Punkt).

    Für Dateien mit der Erweiterung „.docx“ erstellen Sie beispielsweise einen Schlüssel namens **DOCX**.

2. Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen DWORD-Wert namens **AllowPFILEEncryption** mit dem Wert **0**.

3. Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen Zeichenfolgenwert namens **Encryption** mit dem Wert **Native**.

Durch diese Einstellungen sind alle Dateien generisch geschützt, mit Ausnahme der Dateien mit der Erweiterung DOCX, die systemeigen durch den Azure Information Protection-Client geschützt werden.

Wiederholen Sie diese drei Schritte für andere Dateitypen, die Sie als Ausnahmen definieren möchten, weil sie systemeigenen Schutz unterstützen und nicht durch den generisch Azure Information Protection-Client geschützt werden sollen.

Sie können ähnliche Registrierungseinträge für andere Szenarien durch Ändern des Werts der **Encryption** -Zeichenfolge vornehmen, die die folgenden Werte unterstützt:

- **Pfile**: Allgemeiner Schutz

- **Native**: systemeigener Schutz

- **Off**: Schutz blockieren

Weitere Informationen finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](../develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet. 

<a id="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-client" class="xliff"></a>

## Dateitypen, die von der Klassifizierung und vom Schutz durch den Azure Information Protection-Client ausgeschlossen sind

Um zu verhindern, dass Benutzer Dateien ändern, die für Vorgänge auf dem Computer entscheidend sind, werden einige Dateitypen und Ordner von der Klassifizierung und dem Schutz automatisch ausgeschlossen. Wenn Benutzer versuchen, diese Dateien zu klassifizieren oder zu schützen, wird eine Meldung angezeigt, dass diese Dateien ausgeschlossen sind.

- **Ausgeschlossene Dateitypen**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msp, .msi, .pdb, .jar

- **Ausgeschlossener Ordner**: 
    - Windows
    - Programme (\Programme und \Programme (x86))
    - \ProgramData 
    - \AppData (für alle Benutzer)


<a id="next-steps" class="xliff"></a>

## Nächste Schritte
Nachdem Sie alle Dateitypen ermittelt haben, die vom Azure Information Protection-Client unterstützt werden, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
