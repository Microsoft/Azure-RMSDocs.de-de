---
title: Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer
description: Anweisungen und Informationen für Administratoren zum Bereitstellen des Azure Information Protection Unified Bezeichnung-Clients für Windows in Unternehmensnetzwerken.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/07/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 1c0280de31b36358cd670c1d1b147dd4132ac6ac
ms.sourcegitcommit: efeb486e49c3e370d7fd8244687cd3de77cd8462
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97583420"
---
# <a name="admin-guide-install-the-azure-information-protection-unified-labeling-client-for-users"></a>Administrator Handbuch: Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen [unter AIP für Windows und Office-Versionen unter Erweiterter Support](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support).*
>
>***Anweisungen für**: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie im [klassischen Client Administrator Handbuch](client-admin-guide-install.md). *

Überprüfen Sie vor der Installation des Azure Information Protection Unified Bezeichnung-Clients in Ihrem Unternehmensnetzwerk, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen: [Anforderungen für Azure Information Protection](../requirements.md). 

Überprüfen Sie dann die zusätzlichen Voraussetzungen, die möglicherweise für den Azure Information Protection Unified Bezeichnung-Client erforderlich sind, wie im nächsten Abschnitt beschrieben. Das Installationsprogramm überprüft nicht alle Voraussetzungen.

## <a name="additional-prerequisites-for-the-azure-information-protection-unified-labeling-client"></a>Zusätzliche Voraussetzungen für den Azure Information Protection Unified-Bezeichnungs Client

Die folgenden Voraussetzungen für den AIP Unified-Bezeichnungs Client sind zusätzlich zu den in [Azure Information Protection Anforderungen](../requirements.md)aufgeführten Elementen aufgeführt.

|Anforderung  |BESCHREIBUNG  |
|---------|---------|
|**Microsoft .NET Framework 4.6.2**     | Die vollständige Installation des Azure Information Protection Unified Bezeichnung-Clients erfordert standardmäßig eine Mindestversion von Microsoft .NET Framework 4.6.2. <br><br>Wenn dieses Framework fehlt, versucht der Setup-Assistent des ausführbaren Installationsprogramms, diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.       |
|**Microsoft .NET Framework 4.5.2**     | Wenn der Azure Information Protection Viewer separat installiert wird, ist für die Viewer-Anwendung mindestens eine Version von Microsoft .NET Framework 4.5.2 erforderlich. <br><br>**Wichtig**: Wenn dieses Framework für den Viewer fehlt, wird es vom ausführbaren Installationsprogramm *nicht* heruntergeladen oder installiert.        |
|**Windows PowerShell-Mindestversion 4,0**     |   Das PowerShell-Modul für den Client erfordert eine Mindestversion von Windows PowerShell 4,0, die unter Umständen unter älteren Betriebssystemen installiert werden muss. <br><br>Weitere Informationen finden Sie unter [How to Install Windows PowerShell 4.0](https://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Installieren von Windows PowerShell 4.0). <br><br>**Wichtig**: Diese erforderliche Komponente wird vom Installationsprogramm *nicht* überprüft oder installiert. Zum Überprüfen, welche Version von Windows PowerShell auf dem Computer ausgeführt wird, geben Sie `$PSVersionTable` in einer PowerShell-Sitzung ein.      |
|**Bildschirmauflösung von mehr als 800 × 600**    |     Bei einer Auflösung von 800 × 600 und niedriger kann das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** nicht vollständig angezeigt werden, wenn Sie im Datei-Explorer mit der rechten Maustaste auf eine Datei oder einen Ordner klicken.    |
|**Microsoft Online Services-Anmeldeassistent 7.250.4303.0**     |   Für Computer, auf denen [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support) ausgeführt wird, ist die Microsoft Online Services-Anmelde-Assistent-Version 7.250.4303.0 erforderlich, die in der Client Installation enthalten ist. <br><br>Wenn Sie über eine spätere Version des Anmelde-Assistenten verfügen, deinstallieren Sie diese, bevor Sie den Azure Information Protection Unified Bezeichnung-Client installieren. <br><br>Überprüfen Sie beispielsweise die Version, und deinstallieren Sie den Anmelde Assistenten mithilfe der **System Steuerungs** Option  >  **Programm und Features**  >  **deinstallieren oder ändern Sie ein Programm**.      |
|**4482887 KB**     | Installieren Sie [1. März 2019 – KB4482887 (Betriebssystembuild 17763.348)](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887) nur für die Windows 10-Version 1809 mit Betriebssystembuilds, die älter sind als 17763.348, damit die Information Protection-Leiste in Office-Anwendungen korrekt angezeigt wird. <br><br>Dieses Update ist nicht nötig, wenn Sie Office 365 in der Version 1902 oder höher haben.        |
|**Administrator Berechtigungen**| Zum Installieren des Azure Information Protection Unified Bezeichnung-Clients sind lokale Administrator Berechtigungen erforderlich.| 
|**Exploit-Schutz deaktivieren (nur .NET 2 oder 3)**   |Der AIP-Client wird auf Computern mit .NET 2 oder 3, für die der [Exploit-Schutz](/windows/security/threat-protection/microsoft-defender-atp/enable-exploit-protection) aktiviert ist, nicht unterstützt. Wenn auf Ihrem Computer neben einer oben aufgeführten .NET 4. x-Version .NET 2 oder 3 vorhanden ist, sollten Sie den [Exploit-Schutz deaktivieren](../known-issues.md#known-issues-for-aip-and-exploit-protection) , bevor Sie den AIP-Client installieren.  |
|||
        
### <a name="configure-your-group-policy-to-prevent-disabling-aip"></a>Konfigurieren Sie die Gruppenrichtlinie, um das Deaktivieren von AIP zu verhindern.

Für Office-Versionen 2013 und höher wird empfohlen, die Gruppenrichtlinie so zu konfigurieren, dass das **Microsoft Azure Information Protection** -Add-in für Office-Anwendungen immer aktiviert ist.  Ohne dieses Add-in können Benutzer Ihre Dokumente oder e-Mails in Office-Anwendungen nicht bezeichnen.   

Verwenden Sie für Word, Excel, PowerPoint und Outlook die Liste mit den Gruppenrichtlinien Einstellungen **der verwalteten Add-ins** , die in [keine Add-Ins geladen wurden, die aufgrund von Gruppenrichtlinien Einstellungen für Office 2013-und Office 2016-Programme geladen](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off)wurden. 

Geben Sie die folgenden programmgesteuerten Bezeichner (ProgID) für AIP an, und legen Sie die Option auf **1 fest: das Add-in ist immer aktiviert**.

|Application  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

## <a name="applications"></a>Anwendungen

Der Azure Information Protection Unified Label-Client kann Dokumente und e-Mails mit den Office-Anwendungen Word, Excel, PowerPoint und Outlook aus einer der folgenden Office-Editionen bezeichnen und schützen:

- Office-Apps für die in der [Tabelle der unterstützten Versionen für Microsoft 365-Apps nach Updatekanal](/officeupdates/update-history-microsoft365-apps-by-date) aufgeführten Versionen von Microsoft 365 Apps for Business oder Microsoft 365 Business Premium, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Microsoft 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.
- Microsoft 365 Apps for Enterprise
- Office Professional Plus 2019
- Office Professional Plus 2016
- Office Professional Plus 2013 mit Service Pack 1
- Office Professional Plus 2010 mit Service Pack 2

Andere Editionen (z. b. **Standard**) von Office können Dokumente und e-Mails nicht mithilfe eines Rights Management Dienstanbieter schützen. Für diese Editionen wird Azure Information Protection nur für die **Bezeichnung** unterstützt. Folglich werden Bezeichnungen, die Schutz anwenden, den Benutzern auf der Schaltfläche "Azure Information Protection Sensitivität" oder der Leiste nicht angezeigt.

Informationen dazu, welche Office-Editionen den Datenschutzdienst unterstützen, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../requirements-applications.md).

### <a name="office-features-and-capabilities-not-supported"></a>Nicht unterstützte Office-Features und -Funktionen

Der Azure Information Protection Unified-Bezeichnungs Client unterstützt nicht mehrere Office-Versionen auf demselben Computer oder das Wechseln von Benutzerkonten in Office.

Das Office-Feature Seriendruck wird mit keinem Azure Information Protection-Feature unterstützt.

## <a name="options-to-install-the-azure-information-protection-unified-labeling-client-for-users"></a>Optionen zum Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer

Es gibt zwei Optionen zum Installieren des Clients für Benutzer:

**Ausführbare Version (.exe) des Clients ausführen**: Die empfohlene Installationsmethode, die Sie interaktiv oder im Hintergrund ausführen können. Diese Methode bietet die größte Flexibilität und wird empfohlen, da das Installationsprogramm eine Vielzahl der erforderlichen Komponenten überprüft und fehlende erforderliche Komponenten automatisch installieren kann. [Anweisungen](#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer)

**Windows Installer-Version (MSI) des Clients bereitstellen**: Wird nur für Installationen im Hintergrund unterstützt, die einen zentralen Bereitstellungsmechanismus verwenden, z.B. Gruppenrichtlinien, Konfigurations-Manager und Microsoft Intune. Diese Methode ist für Windows 10-PCs erforderlich, die von Intune und der Verwaltung mobiler Geräte (MDM) verwaltet werden, da bei diesen Computern keine ausführbaren Dateien für die Installation unterstützt werden. Wenn Sie dennoch diese Installationsmethode verwenden, müssen Sie die abhängige Software, die das Installationsprogramm für jeden Computer für die ausführbare Datei ausführen würde, manuell überprüfen und installieren oder deinstallieren. [Anweisungen](#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-msi-installer)

Nachdem der Azure Information Protection Unified Bezeichnung-Client installiert wurde, können Sie diesen Client aktualisieren, indem Sie die ausgewählte Installationsmethode wiederholen, oder Windows Update verwenden, um den Client automatisch zu aktualisieren. Weitere Informationen zum Upgrade finden Sie im Abschnitt [Upgraden und Verwalten des Azure Information Protection-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer"></a>So installieren Sie den Azure Information Protection Unified Bezeichnung-Client mithilfe des ausführbaren Installationsprogramms

Befolgen Sie die nachstehenden Anweisungen zum Installieren des Clients, wenn Sie nicht den Microsoft Update-Katalog verwenden oder die MSI-Datei über eine zentrale Bereitstellungsmethode wie Intune bereitstellen.

1. Laden Sie die ausführbare Version des Azure Information Protection Unified Bezeichnung Client (Dateiname AzInfoProtection_UL) aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen. 

2. Für eine Standardinstallation führen Sie einfach die ausführbare Datei aus, z. b. **AzInfoProtection_UL.exe**. Wenn Sie jedoch die Installationsoptionen anzeigen möchten, führen Sie zuerst die ausführbare Datei mit **/Help** aus: `AzInfoProtection_UL.exe /help`

    Beispiel zum automatischen Installieren des Clients: `AzInfoProtection_UL.exe /quiet`
    
    Beispiel zum automatischen Installieren der PowerShell-Befehle: `AzInfoProtection_UL.exe  PowerShellOnly=true /quiet`
    
    Diese zusätzlichen Parameter sind im Hilfebildschirm nicht aufgelistet:
    
    - **ServiceLocation**: Verwenden Sie diesen Parameter, wenn Sie den Client auf Computern installieren, die Office 2010 ausführen, und Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind, oder wenn Sie keine Eingabeaufforderung für die Benutzer anzeigen lassen möchten. Weitere Informationen finden Sie unter

        - [Weitere Informationen zum **servicelokation** -Installationsparameter](#more-information-about-the-servicelocation-installation-parameter) 
        - [AIP für Windows und Office-Versionen in erweiterter Unterstützung](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)

    
    - **AllowTelemetry=0**: Verwenden Sie diesen Parameter, um die Installationsoption **Senden Sie Nutzungsstatistiken an Microsoft, und & helfen Sie so mit, Azure Information Protection zu verbessern.** zu deaktivieren. 

3. So schließen Sie die Installation ab: 

    - Wenn auf Ihrem Computer [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)ausgeführt wird, starten Sie den Computer neu. 
        
        Wenn der Client nicht mit dem serviceloationsparameter installiert wurde, müssen Sie beim ersten Öffnen einer der Office-Anwendungen, die den Azure Information Protection Unified Client (z. b. Word) verwenden, alle Eingabe Aufforderungen bestätigen, um die Registrierung für diese erstmalige Verwendung zu aktualisieren. [Dienstermittlung](client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. 
        
5. Sie können anhand der standardmäßig im Ordner „%temp%“ erstellten Installationsprotokolldatei überprüfen, ob die Installation erfolgreich war. Sie können diesen Speicherort mit dem Installationsparameter **/log** ändern. 
 
    Der Name der Datei weist das folgende Format auf: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`.
    
    Beispiel: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Suchen Sie in dieser Protokolldatei nach der folgenden Zeichenfolge: **Product: Microsoft Azure Information Protection--Installation wurde erfolgreich abgeschlossen**. Wenn Fehler bei der Installation auftreten, enthält diese Protokolldatei Informationen, anhand derer Sie Probleme erkennen und diese beheben können.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Weitere Informationen zum ServiceLocation-Installationsparameter

Wenn Sie den-Client für Benutzer installieren, die über [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support) verfügen und über keine lokalen Administrator Berechtigungen verfügen, geben Sie den serviceloationsparameter und die URL für Ihren Azure Rights Management-Dienst an. Dieser Parameter und Wert erstellt die folgenden Registrierungsschlüssel und legt sie fest:

`HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation`

`HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing`

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing`

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation`

Verwenden Sie das folgende Verfahren, um den Wert zu identifizieren, der für den **serviceloationsparameter** angegeben wird. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>So identifizieren Sie die Wert, der für den ServiceLocation-Parameter angegeben wird

1. Führen Sie in einer PowerShell-Sitzung zuerst [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) aus, und geben Sie Ihre Administrator Anmelde Informationen an, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen Führen [Sie dann Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration)aus. 
 
    Wenn Sie das PowerShell-Modul für den Azure Rights Management-Dienst noch nicht installiert haben, finden Sie weitere Informationen unter [Installieren des PowerShell-Moduls für aipservice](../install-powershell.md).

2. Identifizieren Sie in der Ausgabe den Wert von **LicensingIntranetDistributionPointUrl**.

    Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Entfernen Sie in dem Wert **/_wmcs/licensing** aus der Zeichenfolge. Beispiel: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Die verbleibende Zeichenfolge ist der Wert, der für Ihren ServiceLocation-Parameter angegeben wird.

Beispiel für die unbeaufsichtigte Installation des Clients für [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support) und Azure RMS: `AzInfoProtection_UL.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


### <a name="to-install-the-azure-information-protection-unified-labeling-client-by-using-the-msi-installer"></a>So installieren Sie den Azure Information Protection Unified Bezeichnung-Client mit dem MSI-Installationsprogramm

Verwenden Sie für die zentrale Bereitstellung die folgenden Informationen, die für die MSI-Installationsversion des Azure Information Protection Unified Bezeichnung-Clients spezifisch sind. 

Wenn Sie Intune als Bereitstellungsmethode für Ihre Software verwenden, berücksichtigen Sie neben diesen Anweisungen auch die Informationen unter [Hinzufügen von Apps mit Microsoft Intune](/mem/intune/apps/apps-add).

1. Laden Sie die MSI-Version des Azure Information Protection Unified Bezeichnung-Clients (AzInfoProtection_UL) aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen.

1. Bei jedem Computer, auf dem die MSI-Datei ausgeführt wird, müssen Sie sicherstellen, dass folgende Softwareabhängigkeiten vorliegen. Fügen Sie diese beispielsweise in ein Paket mit der MSI-Version des Clients ein oder stellen Sie sie nur auf Computern bereit, die diese Abhängigkeiten erfüllen:
    
    |Office-Version|Betriebssystem|Software|Aktion|
    |--------------------|--------------|----------------|---------------------|
    |**Alle Versionen akzeptieren Office 365, Version 1902 und höher**|Nur Windows 10 Version 1809 mit Betriebssystembuilds, die älter als 17763.348 sind|[4482887 KB](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887)|Installieren|
    |**Office 2016**|Alle unterstützten Versionen|64-Bit: [KB3178666](https://www.microsoft.com/download/details.aspx?id=55007)<br /><br />32-Bit: [KB3178666](https://www.microsoft.com/download/details.aspx?id=54999)<br /><br /> Version: 1.0|Installieren|
    |**Office 2013**|Alle unterstützten Versionen|64-Bit: [KB3172523](https://www.microsoft.com/download/details.aspx?id=54992)<br /><br /> 32-Bit: [KB3172523](https://www.microsoft.com/download/details.aspx?id=54979) <br /><br />Version: 1.0|Installieren|
    |[**Office 2010**](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)|Alle unterstützten Versionen|[Microsoft Online Services-Anmelde-Assistent](https://www.microsoft.com/download/details.aspx?id=28177)<br /><br /> Version: 2.1|Installieren|
    |[**Office 2010**](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)|Windows 8.1 und Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB2843630 oder KB2919355 nicht installiert sind.|
    |[**Office 2010**](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)|Windows 8 und Windows Server 2012|[KB2843630](https://www.microsoft.com/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren|
    | | | | |

1. Führen Sie die MSI-Datei bei einer Standardinstallation mit **/quiet** aus, z.B. `AzInfoProtection_UL.msi /quiet`.

    Möglicherweise müssen Sie zusätzliche Installationsparameter angeben. Weitere Informationen finden Sie in den [Anweisungen zum Installationsprogramm für ausführbare](#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer)Dateien.

    > [!NOTE]
    > Standardmäßig ist die Option zur **Verbesserung Azure Information Protection durch das Senden von Nutzungsstatistiken an die Microsoft** -Installation aktiviert. Um diese Option zu deaktivieren, stellen Sie sicher, dass Sie eine der folgenden Aktionen ausführen:
    >
    >- Geben Sie während der Installation **allowtelemetry = 0** an.
    >- Aktualisieren Sie den Registrierungsschlüssel nach der Installation wie folgt: **enabletelemetry = 0**.
    >

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client installiert haben, finden Sie hier weitere Informationen, die Sie möglicherweise zur Unterstützung dieses Clients benötigen:

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)