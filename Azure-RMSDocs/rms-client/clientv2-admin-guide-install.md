---
title: Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer
description: Anweisungen und Informationen für Administratoren zum Bereitstellen des Azure Information Protection Unified Bezeichnung-Clients für Windows in Unternehmensnetzwerken.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ce175ae67c443cf14f6b265c314c490b7661f638
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68793273"
---
# <a name="admin-guide-install-the-azure-information-protection-unified-labeling-client-for-users"></a>Administratorhandbuch: Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified Bezeichnung-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Überprüfen Sie vor der Installation des Azure Information Protection Unified Bezeichnung-Clients in Ihrem Unternehmensnetzwerk, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen: [Anforderungen für Azure Information Protection](../requirements.md). 

Überprüfen Sie dann die zusätzlichen Voraussetzungen, die möglicherweise für den Azure Information Protection Unified Bezeichnung-Client erforderlich sind, wie im nächsten Abschnitt beschrieben. Das Installationsprogramm überprüft nicht alle Voraussetzungen.

## <a name="additional-prerequisites-for-the-azure-information-protection-unified-labeling-client"></a>Zusätzliche Voraussetzungen für den Azure Information Protection Unified-Bezeichnungs Client

- Microsoft .NET Framework 4.6.2
    
    Die vollständige Installation des Azure Information Protection Unified Bezeichnung-Clients erfordert standardmäßig eine Mindestversion von Microsoft .NET Framework 4.6.2 und wenn dies fehlt, versucht der Setup-Assistent des ausführbaren Installationsprogramms, dieses herunterzuladen und zu installieren. setzung. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden. Sie können diese Voraussetzung mit einem [benutzerdefinierten Installationsparameter](#more-information-about-the-downgradedotnetrequirement-installation-parameter) umgehen, wenn Sie den Setup-Assistenten verwenden. Diese Vorgehensweise wird jedoch nicht empfohlen.
    
    Diese Voraussetzung ist nicht automatisch installiert, wenn Sie den Client im Hintergrund über das ausführbare Installationsprogramm, Windows Update oder Windows Installer installieren. Für diese Szenarios müssen Sie diese Voraussetzung ggf. separat installieren, andernfalls schlägt die Installation fehl. Sie können Microsoft .NET Framework 4.6.2 (Offlineinstaller) aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53344) herunterladen.

- Microsoft .NET Framework 4.5.2
    
    Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom ausführbaren Installationsprogramm nicht heruntergeladen oder installiert.

- Windows PowerShell Version 4.0
    
    Das PowerShell-Modul für den Client erfordert Windows PowerShell Version 4.0. Dieses muss ggf. auf älteren Betriebssystemen installiert werden. Weitere Informationen finden Sie unter [How to Install Windows PowerShell 4.0](https://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Installieren von Windows PowerShell 4.0). Das Installationsprogramm überprüft oder installiert diese erforderlichen Komponenten nicht für Sie. Zum Überprüfen, welche Version von Windows PowerShell auf dem Computer ausgeführt wird, geben Sie `$PSVersionTable` in einer PowerShell-Sitzung ein.

- Bildschirmauflösung von mehr als 800 × 600
    
    Bei einer Auflösung von 800 × 600 und niedriger kann das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** nicht vollständig angezeigt werden, wenn Sie im Datei-Explorer mit der rechten Maustaste auf eine Datei oder einen Ordner klicken.


- Microsoft Online Services-Anmeldeassistent 7.250.4303.0
    
    Computer, auf denen Office 2010 ausgeführt wird, benötigen Microsoft Online Services-Anmeldeassistent Version 7.250.4303.0. Diese Version ist in der Clientinstallation enthalten. Wenn Sie über eine spätere Version des Anmelde-Assistenten verfügen, deinstallieren Sie diese, bevor Sie den Azure Information Protection Unified Bezeichnung-Client installieren. Überprüfen Sie beispielsweise die Version, und deinstallieren Sie den Anmeldeassistenten über **Systemsteuerung** > **Programme und Funktionen** > **Programm deinstallieren oder ändern**.

- 4482887 KB
    
    Installieren Sie [1. März 2019 – KB4482887 (Betriebssystembuild 17763.348)](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887) nur für die Windows 10-Version 1809 mit Betriebssystembuilds, die älter sind als 17763.348, damit die Information Protection-Leiste in Office-Anwendungen korrekt angezeigt wird. Dieses Update ist nicht nötig, wenn Sie Office 365 in der Version 1902 oder höher haben.

- KB 2533623
    
    Computer unter Windows 7 Service Pack 1 benötigen KB 2533623. Weitere Informationen zu diesem Update finden Sie unter [Microsoft-Sicherheitsempfehlung: Unsichere Bibliothekladevorgänge können eine Codeausführung von Remotestandorten aus ermöglichen](https://support.microsoft.com/en-us/kb/2533623). Möglicherweise können Sie dieses Update direkt installieren, oder ein anderes Update könnte Vorrang haben, das es für Sie installiert.
    
    Wenn dieses Update benötigt wird und nicht installiert ist, werden Sie in der Clientinstallation gewarnt, dass es installiert werden muss. Dieses Update kann nach der Installation des Clients installiert werden, aber einige Aktionen werden blockiert, und die Meldung wird erneut angezeigt.  

- Visual C++ Redistributable für Visual Studio 2015 (32-Bit Version)
    
    Installieren Sie bei Computern mit Windows 7 Service Pack 1 **vc_redist.x86.exe** von der folgenden Downloadseite: [Visual C++ Redistributable für Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
    
    Die Client Installation prüft diese Voraussetzung nicht, Sie ist jedoch für den Azure Information Protection Unified-Bezeichnungs Client erforderlich, um PDF-Dateien zu klassifizieren und zu schützen.

- Konfigurieren der Gruppenrichtlinie, um die Deaktivierung des Azure Information Protection-Add-In zu verhindern
    
    Konfigurieren Sie die Gruppenrichtlinie für Office 2013 und höher so, dass das Add-In **Microsoft Azure Information Protection** für Office-Anwendungen immer aktiviert ist. Ohne diese Konfiguration wird das Microsoft Azure Information Protection-Add-In möglicherweise deaktiviert, und Benutzer können ihre Dokumente und E-Mails in ihren Office-Anwendungen nicht kennzeichnen.
    
    - Für Outlook: Verwenden Sie die Gruppenrichtlinieneinstellung, die in der Office-Dokumentation unter [System-Administratorkontrolle über Add-Ins](https://docs.microsoft.com/office/vba/outlook/concepts/getting-started/support-for-keeping-add-ins-enabled#system-administrator-control-over-add-ins) dokumentiert ist.
    
    - In Word, Excel und PowerPoint: Verwenden Sie die Gruppenrichtlinieneinstellung **Liste der verwalteten Add-Ins**, die im Supportartikel [Keine Add-Ins geladen durch Gruppenrichtlinien für Office 2013 und Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) dokumentiert ist. 
        
        Geben Sie die folgenden programmgesteuerten Bezeichner (ProgID) für Azure Information Protection an, und setzen Sie die Option auf **1: Das Add-in ist immer aktiviert**.
        
        Für Word: `MSIP.WordAddin`
        
        Für Excel: `MSIP.ExcelAddin`
        
        Für PowerPoint: `MSIP.PowerPointAddin`

> [!IMPORTANT]
> Für die Installation des Azure Information Protection Unified Bezeichnung-Clients sind lokale Administrator Berechtigungen erforderlich.


## <a name="options-to-install-the-azure-information-protection-unified-labeling-client-for-users"></a>Optionen zum Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer

Es gibt zwei Optionen zum Installieren des Clients für Benutzer:

**Ausführbare Version (EXE) des Clients ausführen**: Die empfohlene Installationsmethode, die Sie interaktiv oder im Hintergrund ausführen können. Diese Methode bietet die größte Flexibilität und wird empfohlen, da das Installationsprogramm eine Vielzahl der erforderlichen Komponenten überprüft und fehlende erforderliche Komponenten automatisch installieren kann. [Anweisungen](#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer)

**Windows Installer-Version (MSI) des Clients bereitstellen**: Wird nur für Installationen im Hintergrund unterstützt, die einen zentralen Bereitstellungsmechanismus verwenden, z. B. Gruppenrichtlinien, Configuration Manager und Microsoft Intune. Diese Methode ist für Windows 10-PCs erforderlich, die von Intune und der Verwaltung mobiler Geräte (MDM) verwaltet werden, da bei diesen Computern keine ausführbaren Dateien für die Installation unterstützt werden. Wenn Sie dennoch diese Installationsmethode verwenden, müssen Sie die abhängige Software, die das Installationsprogramm für jeden Computer für die ausführbare Datei ausführen würde, manuell überprüfen und installieren oder deinstallieren. [Anweisungen](#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-msi-installer)

Nachdem der Azure Information Protection Unified Bezeichnung-Client installiert wurde, können Sie diesen Client aktualisieren, indem Sie die ausgewählte Installationsmethode wiederholen, oder Windows Update verwenden, um den Client automatisch zu aktualisieren. Weitere Informationen zum Upgrade finden Sie im Abschnitt [Upgraden und Verwalten des Azure Information Protection-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer"></a>So installieren Sie den Azure Information Protection Unified Bezeichnung-Client mithilfe des ausführbaren Installationsprogramms

Befolgen Sie die nachstehenden Anweisungen zum Installieren des Clients, wenn Sie nicht den Microsoft Update-Katalog verwenden oder die MSI-Datei über eine zentrale Bereitstellungsmethode wie Intune bereitstellen.

1. Laden Sie die ausführbare Version des Azure Information Protection Unified Bezeichnung Client (Dateiname von AzInfoProtection_UL) aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen. 

2. Für eine Standardinstallation führen Sie einfach die ausführbare Datei aus, z. b. **AzInfoProtection_UL. exe**. Führen Sie die ausführbare Datei mit dem Parameter **/help** aus, um zuvor die Installationsoptionen anzuzeigen: `AzInfoProtection_UL.exe /help`

    Beispiel zum automatischen Installieren des Clients: `AzInfoProtection_UL.exe /quiet`
    
    Beispiel zum automatischen Installieren der PowerShell-Befehle: `AzInfoProtection_UL.exe  PowerShellOnly=true /quiet`
    
    Diese zusätzlichen Parameter sind im Hilfebildschirm nicht aufgelistet:
    
    - **ServiceLocation**: Verwenden Sie diesen Parameter, wenn Sie den Client auf Computern installieren, die Office 2010 ausführen und Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind, oder wenn Sie keine Eingabeaufforderung für die Benutzer anzeigen lassen möchten. [Weitere Informationen](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: Verwenden Sie diesen Parameter, um die Notwendigkeit von Microsoft Framework .NET, Version 4.6.2, zu umgehen. [Weitere Informationen](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: Verwenden Sie diesen Parameter, um die Installationsoption **Senden Sie Nutzungsstatistiken an Microsoft, und helfen Sie so mit, Azure Information Protection zu verbessern** zu deaktivieren. 

3. So schließen Sie die Installation ab: 

    - Starten Sie den Computer neu, wenn darauf Office 2010 ausgeführt wird. 
        
        Wenn der Client nicht mit dem serviceloationsparameter installiert wurde, müssen Sie beim ersten Öffnen einer der Office-Anwendungen, die den Azure Information Protection Unified Client (z. b. Word) verwenden, alle Eingabe Aufforderungen bestätigen, um die Registrierung für diesen zu aktualisieren. erstmalige Verwendung. [Dienstermittlung](client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. 
        
5. Sie können anhand der standardmäßig im Ordner „%temp%“ erstellten Installationsprotokolldatei überprüfen, ob die Installation erfolgreich war. Sie können diesen Speicherort mit dem Installationsparameter **/log** ändern. 
 
    Der Name der Datei weist das folgende Format auf: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`.
    
    Zum Beispiel: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Suchen Sie in dieser Protokolldatei nach der folgenden Zeichenfolge: **Product: Microsoft Azure Information Protection – Installation completed successfully.** Wenn Fehler bei der Installation auftreten, enthält diese Protokolldatei Informationen, anhand derer Sie Probleme erkennen und diese beheben können.

#### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Weitere Informationen zum ServiceLocation-Installationsparameter

Geben Sie den „ServiceLocation“-Parameter und die URL für Ihren Azure Rights Management-Dienst an, wenn Sie den Client für Benutzer installieren, die Office 2010 verwenden und nicht über lokale Administratorrechte verfügen. Dieser Parameter und Wert erstellt die folgenden Registrierungsschlüssel und legt sie fest:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Verwenden Sie das folgende Verfahren, um den Wert zu identifizieren, den Sie für den ServiceLocation-Parameter angeben. 

##### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>So identifizieren Sie die Wert, der für den ServiceLocation-Parameter angegeben wird

1. Führen Sie in einer PowerShell-Sitzung zuerst [Connect-aipservice](https://docs.microsoft.com/powershell/module/aipservice/connect-aipservice) aus, und geben Sie Ihre Administrator Anmelde Informationen an, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen Führen [Sie dann Get-aipserviceconfiguration](https://docs.microsoft.com/powershell/module/aipservice/get-aipserviceconfiguration)aus. 
 
    Wenn Sie das PowerShell-Modul für den Azure Rights Management-Dienst noch nicht installiert haben, finden Sie weitere Informationen unter [Installieren des PowerShell-Moduls für aipservice](../install-powershell.md).

2. Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.

    Zum Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Entfernen Sie im Wert den Text **/_wmcs/licensing** aus der Zeichenfolge. Beispiel: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Die verbleibende Zeichenfolge ist der Wert, der für Ihren ServiceLocation-Parameter angegeben wird.

Beispiel zum automatischen Installieren des Clients für Office 2010 und Azure RMS: `AzInfoProtection_UL.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Weitere Informationen zum DowngradeDotNetRequirement-Installationsparameter

Zur Unterstützung automatischer Upgrades mithilfe von Windows Update und zur zuverlässigen Integration in Office-Anwendungen verwendet der Azure Information Protection Unified-Bezeichnungs Client Microsoft .NET Framework-Version 4.6.2. Eine interaktive Installation prüft standardmäßig mithilfe ausführbarer Überprüfungen, ob diese Version vorhanden ist, und versucht, sie zu installieren, falls sie nicht vorhanden ist. Die Installation erfordert einen Neustart des Computers.

Wenn die Installation dieser höheren Version von Microsoft .NET Framework nicht praktikabel ist, können Sie den Client mit dem auf „True“ festgelegten Parameter **DowngradeDotNetRequirement** installieren. Dadurch wird dieses Erfordernis umgangen, wenn Microsoft .NET Framework, Version 4.5.1, installiert ist.

Beispiel: `AzInfoProtection_UL.exe DowngradeDotNetRequirement=True`

Es wird empfohlen, diesen Parameter mit Vorsicht zu verwenden, und mit dem wissen, dass es gemeldete Probleme mit Office-Anwendungen gibt, die hängen, wenn der Azure Information Protection Unified Bezeichnung-Client mit dieser älteren Version von verwendet wird Microsoft .net Framework. Wenn Sie Probleme mit nicht mehr reagierenden Anwendungen bemerken, aktualisieren Sie auf die empfohlene Version, bevor Sie andere Problembehandlungslösungen versuchen. 

Beachten Sie auch Folgendes: Wenn Sie Windows Update verwenden, um den Azure Information Protection Unified-Bezeichnungs Client zu aktualisieren, benötigen Sie einen anderen Mechanismus für die Software Bereitstellung, um den Client auf spätere Versionen zu aktualisieren.

### <a name="to-install-the-azure-information-protection-unified-labeling-client-by-using-the-msi-installer"></a>So installieren Sie den Azure Information Protection Unified Bezeichnung-Client mit dem MSI-Installationsprogramm

Verwenden Sie für die zentrale Bereitstellung die folgenden Informationen, die für die MSI-Installationsversion des Azure Information Protection Unified Bezeichnung-Clients spezifisch sind. 

Wenn Sie Intune als Bereitstellungsmethode für Ihre Software verwenden, berücksichtigen Sie neben diesen Anweisungen auch die Informationen unter [Hinzufügen von Apps mit Microsoft Intune](/intune/deploy-use/add-apps).

1. Laden Sie die MSI-Version des Azure Information Protection Unified-Bezeichnungs Client (AzInfoProtection_UL) aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen.

2. Bei jedem Computer, auf dem die MSI-Datei ausgeführt wird, müssen Sie sicherstellen, dass folgende Softwareabhängigkeiten vorliegen. Fügen Sie diese beispielsweise in ein Paket mit der MSI-Version des Clients ein oder stellen Sie sie nur auf Computern bereit, die diese Abhängigkeiten erfüllen:
    
    |Office-Version|Betriebssystem|Software|Aktion|
    |--------------------|--------------|----------------|---------------------|
    |Alle Versionen akzeptieren Office 365, Version 1902 und höher|Nur Windows 10 Version 1809 mit Betriebssystembuilds, die älter als 17763.348 sind|[4482887 KB](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887)|„Installieren“ zu klicken.|
    |Office 2016|Alle unterstützten Versionen|64-Bit: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=55007)<br /><br />32-Bit: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=54999)<br /><br /> Version: 1.0|„Installieren“ zu klicken.|
    |Office 2013|Alle unterstützten Versionen|64-Bit: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54992)<br /><br /> 32-Bit: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54979) <br /><br />Version: 1.0|„Installieren“ zu klicken.|
    |Office 2010|Alle unterstützten Versionen|[Microsoft Online Services-Anmeldeassistent](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Version: 2.1|„Installieren“ zu klicken.|
    |Office 2010|Windows 8.1 und Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB2843630 oder KB2919355 nicht installiert sind.|
    |Office 2010|Windows 8 und Windows Server 2012|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|„Installieren“ zu klicken.|
    |Office 2010|Windows 7 und Windows Server 2008 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB 3125574 nicht installiert ist|
    |Nicht verfügbar|Windows 7|[vc_redist.x86.exe](https://www.microsoft.com/en-us/download/details.aspx?id=48145)|„Installieren“ zu klicken.|
    |Nicht verfügbar|Windows 7|KB2627273 <br /><br /> Im Dateinamen enthaltene Versionsnummer: v4|Deinstallieren|

3. Führen Sie die MSI-Datei bei einer Standardinstallation mit **/quiet** aus, z.B. `AzInfoProtection_UL.msi /quiet`. Allerdings müssen möglicherweise weitere Installationsparameter angegeben werden, die in den [Anweisungen zum ausführbaren Installationsprogramm](#to-install-the-azure-information-protection-unified-labeling-client-by-using-the-executable-installer) dokumentiert sind.  


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client installiert haben, finden Sie hier weitere Informationen, die Sie möglicherweise zur Unterstützung dieses Clients benötigen:

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)

