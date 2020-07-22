---
title: Unterstützte Dateitypen-Azure Information Protection Client
description: Technische Details zu den unterstützten Dateitypen, Dateierweiterungen und Schutzebenen für Administratoren, die für den Azure Information Protection-Client für Windows verantwortlich sind.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ''
ms.subservice: v1client
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 4213be53fe21491118b4771c22ed43255d5c342d
ms.sourcegitcommit: 6d10435c67434bdbbdd51b4a3535d0efaf8307da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2020
ms.locfileid: "86868942"
---
# <a name="admin-guide-file-types-supported-by-the-azure-information-protection-client"></a>Administratorhandbuch: Vom Azure Information Protection-Client unterstützte Dateitypen

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Der Azure Information Protection-Client kann Folgendes auf Dokumente und E-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Der Azure Information Protection-Client kann außerdem den Inhalt einiger Dateitypen überprüfen, indem er bekannte Typen von vertraulichen Informationen oder die von Ihnen definierten regulären Ausdrücke verwendet.

Verwenden Sie die folgenden Informationen, um zu überprüfen, welche Dateitypen vom Azure Information Protection-Client unterstützt werden, welche verschiedenen Schutzebenen verwendet werden, wie die Standardschutzebene geändert wird und welche Dateien automatisch von der Klassifizierung und dem Schutz ausgeschlossen (übersprungen) werden.

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

In der aktuellen [Standardrichtlinie](../configure-policy-default.md) wendet die Bezeichnung **Allgemein** zum Beispiel die Klassifizierung, aber nicht den Schutz an. Sie können die Bezeichnung **Allgemein** auf eine Datei namens „sales.pdf“, aber nicht auf eine Datei namens „sales.txt“ anwenden. 

In der aktuellen Standardrichtlinie werden Klassifizierung und Schutz durch **Vertraulich\Alle Mitarbeiter** angewendet. Sie können diese Bezeichnung auf eine Datei namens „sales.pdf“ und eine Datei namens „sales.txt“ anwenden. Sie können den Schutz auch ohne die Klassifizierung auf diese Dateien anwenden.

## <a name="file-types-supported-for-protection"></a>Für den Schutz unterstützte Dateitypen

Der Azure Information Protection-Client unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben wird.

|Art des Schutzes|Systemeigen|Allgemein|
|----------------------|----------|-----------|
|Beschreibung|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Sicherheitsebene, zu der Dateikapselung mithilfe des Dateityps PFILE und Authentifizierung gehören, um zu überprüfen, ob ein Benutzer berechtigt ist, die Datei zu öffnen.|
|Schutz|Der Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts beim Schützen der Dateien festgelegt wurden, erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Der Schutz der Dateien wird auf folgende Weise erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für Personen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben. Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Die Überwachungsprotokollierung von autorisierten Benutzern, die Dateien öffnen und auf diese zugreifen kommt vor. Nutzungsrechte werden jedoch nicht erzwungen.|
|Standardebene für Dateitypen|Dies ist die Standardebene des Schutzes für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt, [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den nativen Schutz unterstützt werden.|

Sie können die Standardschutzebene ändern, die der Azure Information Protection-Client anwendet. Sie können die Standardebene von systemeigen zu generisch oder von generisch zu systemeigen ändern und sogar verhindern, dass der Azure Information Protection-Client anwendet. Weitere Informationen finden Sie im Abschnitt [Ändern der Standardschutzebene von Dateien](#changing-the-default-protection-level-of-files) dieses Artikels.

Dieser Datenschutz kann automatisch angewendet werden, wenn ein Benutzer eine vom Administrator konfigurierte Bezeichnung auswählt. Benutzer können mithilfe von [Berechtigungsstufen](../configure-usage-rights.md#rights-included-in-permissions-levels) auch eigene Schutzeinstellungen angeben. 

### <a name="file-sizes-supported-for-protection"></a>Für den Schutz unterstützte Dateigrößen

Für den Schutz werden folgende maximale Dateigrößen vom Azure Information Protection-Client unterstützt.

- **Bei Office-Dateien:**


  |                                                     Office-Anwendung                                                      |                                                Maximale unterstützte Dateigröße                                                 |
  |-----------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------|
  |             Word 2007 (nur von AD RMS unterstützt)<br /><br />Word 2010<br /><br />Word 2013<br /><br />Word 2016             |                                          32-Bit: 512 MB<br /><br />64-Bit: 512 MB                                          |
  |           Excel 2007 (nur von AD RMS unterstützt)<br /><br />Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016           |                      32-Bit: 2 GB<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt                       |
  | PowerPoint 2007 (nur von AD RMS unterstützt)<br /><br />PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016 | 32-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt |


- **Bei allen anderen Dateien**: 

  - Beachten Sie zum Schutz anderer Dateitypen und zum Öffnen dieser Dateitypen im Azure Information Protection-Viewer: Die maximale Dateigröße ist nur durch den verfügbaren Speicherplatz begrenzt.

  - Beachten Sie beim Aufheben des Dateischutzes mit dem [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile)-Cmdlet folgendes: Die maximale Dateigröße für PST-Dateien beträgt 5 GB. Die Dateigröße für andere Dateitypen ist nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt.

    Tipp: Wenn Sie geschützte Elemente in großen .pst-Dateien suchen oder wiederherstellen müssen, finden Sie hierzu weitere Informationen unter [Guidance for using Unprotect-RMSFile for eDiscovery (Anleitung für die Verwendung von Unprotect-RMSFile für eDiscovery)](../configure-super-users.md#guidance-for-using-unprotect-rmsfile-for-ediscovery).

### <a name="supported-file-types-for-classification-and-protection"></a>Unterstützte Dateitypen für Klassifizierung und Schutz

Die folgende Tabelle enthält eine Teilmenge der Typen von Dateien, die den nativen Schutz durch den Azure Information Protection-Client unterstützen und die auch klassifiziert werden können. 

Diese Dateitypen sind separat aufgeführt, da wenn sie nativ geschützt sind, die Namenserweiterung der ursprünglichen Datei geändert wird und diese Dateien dadurch schreibgeschützt werden. Beachten Sie, dass wenn Dateien generisch geschützt sind, die ursprüngliche Namenserweiterung immer in PFILE geändert wird.

> [!WARNING]
> Wenn Sie über Firewalls, Webproxys oder Sicherheitssoftware verfügen, die Erweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie die Netzwerkgeräte und die Software möglicherweise zur Unterstützung der neuen Erweiterungen neu konfigurieren.

|Ursprüngliche Dateinamenerweiterung|Geschützte Dateierweiterung|
|--------------------------------|-------------------------------------|
|.txt|PTXT|
|.xml|PXML|
|.jpg|PJPG|
|JPEG|PJPEG|
|.pdf|PPDF [[1]](#footnote-1)|
|.png|PPNG|
|.tif|PTIF|
|TIFF|PTIFF|
|BMP|PBMP|
|.gif|PFIG|
|JPE|PJPE|
|JFIF|PJFIF|
|.jt|.pjt|

###### <a name="footnote-1"></a>Fußnote 1
Mit der aktuellen Version des Azure Information Protection-Clients bleibt die Erweiterung des geschützten PDF-Dokuments [in der Regel](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption) „.pdf“.

Die nächste Tabelle enthält die verbleibenden Dateitypen, die den nativen Schutz durch den Azure Information Protection-Client unterstützen und auch klassifiziert werden können. Sie erkennen diese als Dateitypen für Microsoft Office-Apps. Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und Office Open XML für die folgenden Office-Programme: Word, Excel und PowerPoint.

Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|.doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />VSDM|VSDX<br /><br />VSSM<br /><br />VSSX<br /><br />VSTM<br /><br />VSTX<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps|

### <a name="changing-the-default-protection-level-of-files"></a>Ändern der Standard-Schutzebene für Dateien
Sie können ändern, wie der Azure Information Protection-Client Dateien durch Bearbeiten der Registrierung schützt. Beispielsweise können Sie erzwingen, dass Dateien, die systemeigenen Schutz unterstützen, durch den Azure Information Protection-Client generisch geschützt werden.

Die folgenden Gründe können dafür sprechen:

- Um sicherzustellen, dass alle Benutzer die Datei öffnen können, wenn Sie keine Anwendung haben, die systemeigenen Schutz unterstützt.

- So werden Sicherheitssysteme untergebracht, die über die Dateinamenerweiterung Einfluss auf Dateien haben und neu konfiguriert werden können, um die Dateinamenerweiterung ".pfile" aufzunehmen. Die Sicherheitssysteme können allerdings nicht neu konfiguriert werden, um mehrere Dateinamenerweiterungen für einen systemeigenen Schutz unterzubringen.

Auf ähnliche Weise können Sie erzwingen, dass der Azure Information Protection-Client systemeigenen Schutz auf Dateien anwendet, die in der Standardeinstellung durch generischen Schutz geschützt würden. Diese Aktion kann sinnvoll sein, wenn Sie über eine Anwendung verfügen, die RMS-APIs unterstützt. Beispiele hierfür sind eine Branchenanwendung, die von internen Entwicklern geschrieben wurde, oder eine Anwendung, die von einem unabhängigen Softwareanbieter erworben wurde.

Sie können auch erzwingen, dass der Azure Information Protection-Client den Schutz von Dateien blockiert (der systemeigene oder generische Schutz wird nicht angewendet). Diese Aktion kann z.B. erforderlich sein, wenn Sie über eine automatische Anwendung oder einen automatischen Dienst verfügen, die bzw. der eine bestimmte Datei öffnen muss, um ihren Inhalt zu verarbeiten. Wenn Sie den Schutz für einen Dateityp blockieren, können Benutzer den Azure Information Protection-Client nicht verwenden, um eine Datei mit diesem Dateityp zu schützen. Wenn sie dies versuchen, wird eine Nachricht angezeigt, der zufolge der Administrator einen Schutz verhindert hat. Sie müssen dann ihre Aktion zum Schützen der Datei abbrechen.

Bearbeiten Sie die folgenden Registrierungseinträge, um den Azure Information Protection-Client so zu konfigurieren, dass er generischen Schutz auf alle Dateien anwendet, die in der Standardeinstellung durch native Schutzfunktionen geschützt würden. Beachten Sie, dass Sie den Schlüssel „FileProtection“ manuell erstellen müssen, falls dieser nicht vorhanden ist.

1. Erstellen Sie einen neuen Schlüssel mit dem Namen * für den folgenden Registrierungspfad, der Dateien mit beliebiger Erweiterung anzeigt:

    - Für 32-Bit-Versionen von Windows: **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection**

    - Für 64-Bit-Version von Windows: **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\msipc\fileprotection** und **HKEY_LOCAL_MACHINE \software\microsoft\msipc\fileprotection**

2. Erstellen Sie im neu hinzugefügten Schlüssel (zum Beispiel HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\\\*) einen neuen Zeichenfolgenwert (REG_SZ) mit dem Namen **Encryption** und dem Datenwert **Pfile**.

    Diese Einstellung führt dazu, dass der Azure Information Protection-Client den generischen Schutz anwendet.

Diese beiden Einstellungen führen dazu, dass der Azure Information Protection-Client generischen Schutz auf alle Dateien mit einer Dateinamenerweiterung anwendet. Wenn Sie damit Ihr Ziel erreicht haben, ist keine weitere Konfiguration erforderlich. Sie können jedoch Ausnahmen für bestimmte Dateitypen definieren, so dass diese weiterhin systemintern geschützt werden. Zu diesem Zweck müssen Sie drei (für Windows 32-Bit) oder 6 (für Windows 64-Bit) zusätzliche Registrierungseinträge für jeden Dateityp bearbeiten:

1. Für **HKEY_LOCAL_MACHINE \software\microsoft\msipc\fileprotection** und **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\msipc\fileprotection** (falls zutreffend): Fügen Sie einen neuen Schlüssel mit dem Namen der Dateinamenerweiterung (ohne vorangehenden Punkt) hinzu.

    Bei Dateien mit der Dateinamenerweiterung ".docx", erstellen Sie beispielsweise einen Schlüssel namens **DOCX**.

2. Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen DWORD-Wert namens **AllowPFILEEncryption** mit dem Wert **0**.

3. Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z. B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX**) einen neuen Zeichenfolgenwert namens **Encryption** mit dem Wert **Native**.

Durch diese Einstellungen sind alle Dateien generisch geschützt, mit Ausnahme von Dateien mit der Erweiterung DOCX. Diese Dateien werden nativ vom Azure Information Protection-Client geschützt.

Wiederholen Sie diese drei Schritte für andere Dateitypen, die Sie als Ausnahmen definieren möchten, weil sie systemeigenen Schutz unterstützen und nicht durch den generisch Azure Information Protection-Client geschützt werden sollen.

Sie können für andere Szenarien ähnliche Bearbeitungen der Registrierung durchführen, indem Sie den Wert der Zeichenfolge **Verschlüsselung** ändern, der die folgenden Werte unterstützt:

- **Pfile**: Allgemeiner Schutz

- **Native**: systemeigener Schutz

- **Off**: Schutz blockieren

Nachdem Sie diese Registrierungsänderungen vorgenommen haben, müssen Sie den Computer nicht neu starten. Wenn Sie jedoch PowerShell-Befehle zum Schützen von Dateien verwenden, müssen Sie eine neue PowerShell-Sitzung starten, damit die Änderungen wirksam werden.

Weitere Informationen zum Bearbeiten der Registrierung, um die Standardschutzebene von Dateien zu ändern, finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](../develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet.

## <a name="file-types-that-are-excluded-from-classification-and-protection"></a>Von der Klassifizierung und dem Schutz ausgeschlossene Dateitypen

Um zu verhindern, dass Benutzer Dateien ändern, die für Vorgänge auf dem Computer entscheidend sind, werden einige Dateitypen und Ordner von der Klassifizierung und dem Schutz automatisch ausgeschlossen. Wenn Benutzer versuchen, diese Dateien mithilfe des Azure Information Protection-Clients zu klassifizieren oder zu schützen, wird eine Meldung angezeigt, dass diese Dateien ausgeschlossen sind.

- **Ausgeschlossene Dateitypen**: .lnk, .exe, .com, .cmd, .bat, .dll, .ini, .pst, .sca, .drm, .sys, .cpl, .inf, .drv, .dat, .tmp, .msg,.msp, .msi, .pdb, .jar


- **Ausgeschlossener Ordner**: 
    - Windows
    - Programme (\Programme und \Programme (x86))
    - \ProgramData 
    - \AppData (für alle Benutzer)

### <a name="file-types-that-are-excluded-from-classification-and-protection-by-the-azure-information-protection-scanner"></a>Dateitypen, die von der Klassifizierung und vom Schutz durch die Azure Information Protection-Überprüfung ausgeschlossen sind

Bei der Überprüfung werden standardmäßig dieselben Dateitypen wie vom Azure Information Protection-Client ausgeschlossen – mit folgenden Ausnahmen:

- RTF und RAR sind ebenfalls ausgeschlossen.

Sie können die enthaltenen oder ausgeschlossenen Dateitypen für die Überprüfung der Dateien durch den Scanner ändern:

- Konfigurieren [Sie mithilfe der Azure-Portal die](../deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal) **Dateitypen** , die im Überprüfungs Profil gescannt werden sollen.

> [!NOTE]
> Überwachen Sie die Überprüfung sorgfältig,wenn Sie RTF-Dateien in der Überprüfung miteinbeziehen. Einige RTF-Dateien können nicht erfolgreich überprüft werden. Die Überprüfung wird nicht abgeschlossen, und Sie müssen den Dienst neustarten. 

Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Um das Verhalten bei der Überprüfung zu ändern, bearbeiten Sie die Registrierung und geben Sie weitere Dateitypen an, die Sie schützen möchten. Anweisungen finden Sie unter [Verwenden der Registrierung, um zu ändern, welche Dateitypen](../deploy-aip-scanner-configure-install-classic.md#change-which-file-types-to-protect) vor den Überprüfungs Anweisungen für die Scanner geschützt sind.

### <a name="files-that-cannot-be-protected-by-default"></a>Dateien, die standardmäßig nicht geschützt werden können

Jede Datei, die mit einem Kennwort geschützt ist, kann nur nativ vom Azure Information Protection-Client geschützt werden, wenn sie gerade in der Anwendung geöffnet ist, die für diesen Schutz sorgt. Am häufigsten sind PDF-Dateien kennwortgeschützt. Diese Funktion wird jedoch auch von anderen Anwendungen bereitgestellt, wie z.B. Office-Apps.

Wenn Sie das [Standardverhalten](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption) des Azure Information Protection-Clients so ändern, dass er PDF-Dateien mit der .ppdf-Dateinamenerweiterung schützt, kann der Client PDF-Dateien unter einem der folgenden Umstände nicht nativ schützen oder den Schutz aufheben:

- eine formularbasierte PDF-Datei

- eine geschützte PDF-Datei mit PDF-Erweiterung

    Der Azure Information Protection-Client kann eine nicht geschützte PDF-Datei schützen, deren Schutz aufheben und eine geschützte PDF-Datei erneut schützen, wenn diese eine PPDF-Erweiterung aufweist.

### <a name="limitations-for-container-files-such-as-zip-files"></a>Einschränkungen für Containerdateien, z.B. ZIP-Dateien

Weitere Informationen finden Sie in der [Sammlung der Azure Information Protection Einschränkungen](../known-issues.md#client-support-for-container-files-such-as-zip-files).

## <a name="file-types-supported-for-inspection"></a>Bei der Überprüfung unterstützte Dateitypen

Wenn keine weiteren Konfigurationen vorhanden sind, verwendet der Azure Information Protection-Client Windows-IFilter, um die Inhalte der Dokumente zu überprüfen. Windows-IFilter wird von Windows Search für die Indizierung verwendet. Aus diesem Grund können die folgenden Dateitypen überprüft werden, wenn Sie den [Azure Information Protection-Scanner](../deploy-aip-scanner.md) oder den PowerShell-Befehl [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification) verwenden.

|Anwendungstyp|Dateityp|
|--------------------------------|-------------------------------------|
|Word|Post docx;. docm;. dot;. dotm;. dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|PDF |.pdf|
|Text|.txt; .xml; .csv|

Wenn zusätzliche Konfigurationen vorgenommen werden, können auch andere Dateitypen überprüft werden. Beispielsweise können Sie [eine benutzerdefinierte Erweiterung für die Verwendung des vorhandenen Windows-Filters für Textdateien registrieren](https://docs.microsoft.com/windows/desktop/search/-search-ifilter-registering-filters) und zusätzliche Filter von Softwareherstellern installieren.

Wenn Sie überprüfen möchten, welche Filter installiert sind, finden Sie weitere Informationen im Windows Search-Leitfaden für Entwickler unter [Finding a Filter Handler for a Given File Extension (Finden eines Filterhandlers für eine angegebene Erweiterung)](https://docs.microsoft.com/windows/desktop/search/-search-ifilter-registering-filters#finding-a-filter-handler-for-a-given-file-extension).

In den folgenden Abschnitten finden Sie Konfigurationsanweisungen zum Überprüfen von ZIP- und TIFF-Dateien.

### <a name="to-inspect-zip-files"></a>Überprüfen von ZIP-Dateien

Der Azure Information Protection-Scanner und der PowerShell-Befehl [Set-AIPFileClassification](/powershell/module/azureinformationprotection/set-aipfileclassification) können ZIP-Dateien überprüfen, wenn Sie die folgenden Anweisungen befolgen:

1. Installieren Sie [Office 2010 Filter Pack SP2](https://support.microsoft.com/help/2687447/description-of-office-2010-filter-pack-sp2) auf dem Computer, auf dem die Überprüfung ausgeführt wird.

2. Für den Scanner: Nachdem Sie vertrauliche Informationen gefunden haben und die ZIP-Datei mit einer Bezeichnung klassifiziert und geschützt werden soll, fügen Sie einen Registrierungs Eintrag für diese Dateinamenerweiterung hinzu, um einen generischen Schutz (Pfile) zu erhalten, wie unter [Verwenden der Registrierung zum Ändern der Dateitypen](../deploy-aip-scanner-configure-install-classic.md#change-which-file-types-to-protect) vor den Überprüfungs Anweisungen für die Scanner beschrieben.

Beispielszenario nach dem Ausführen dieser Schritte: 

Eine Datei mit dem Namen **accounts.zip** enthält Excel-Kalkulationstabellen mit Kreditkartennummern. Ihre Azure Information Protection-Richtlinie verfügt über eine Bezeichnung mit dem Namen **Confidential \ Finance** (Vertraulich \ Finanzen), die zum Erkennen von Kreditkartennummern konfiguriert ist und verwendet automatisch die Bezeichnung geschützt, wodurch der Zugriff auf die Finanzgruppe einschränkt wird. 

Nach dem Überprüfen der Datei klassifiziert die Überprüfung diese Datei als **Confidential \ Finance** (Vertraulich \ Finanzen), wendet für die Datei einen generischen Schutz an, damit sie nur von Mitgliedern der Finanzgruppen entzippt werden kann, und benennt die Datei in **accounts.zip.pfile** um.

### <a name="to-inspect-tiff-files-by-using-ocr"></a>Überprüfen von TIFF-Dateien unter Verwendung der OCR

Der Azure Information Protection-Scanner und der PowerShell-Befehl [Set-AIPFileClassiciation](/powershell/module/azureinformationprotection/set-aipfileclassification) können die optische Zeichenerkennung (OCR) verwenden, um TIFF-Bilder zu überprüfen, wenn Sie das Windows-TIFF-IFilter-Feature installieren und anschließend die [Windows-TIFF-IFilter-Einstellungen](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/dd744701%28v%3dws.10%29) auf dem Computer konfigurieren, auf dem der Scanner oder die PowerShell-Sitzung ausgeführt wird.

Für den Scanner: Nachdem Sie vertrauliche Informationen gefunden haben und die TIFF-Datei mit einer Bezeichnung klassifiziert und geschützt werden soll, fügen Sie einen Registrierungs Eintrag für diese Dateinamenerweiterung hinzu, um systemeigenen Schutz zu erhalten, wie unter [Verwenden der Registrierung zum Ändern der Dateitypen](../deploy-aip-scanner-configure-install-classic.md#change-which-file-types-to-protect) vor den Überprüfungs Anweisungen für die Scanner beschrieben.

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie alle Dateitypen ermittelt haben, die vom Azure Information Protection-Client unterstützt werden, helfen Ihnen die folgenden zusätzlichen Ressourcen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentkontrolle](client-admin-guide-document-tracking.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)

