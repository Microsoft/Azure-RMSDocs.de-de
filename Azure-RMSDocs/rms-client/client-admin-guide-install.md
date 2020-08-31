---
title: Installieren des Azure Information Protection-Clients für Benutzer
description: Eine Anleitung und Informationen für Administratoren zum Bereitstellen des Azure Information Protection-Clients für Windows in Unternehmensnetzwerken
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/30/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ea3ec965-3720-4614-8564-3ecfe60bc175
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: bb2f7d2cacad3623eb590c338a7f19585e9c80d1
ms.sourcegitcommit: dd21de9f06ef019634dc2b5d8baf2670bb8171a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/31/2020
ms.locfileid: "89176649"
---
# <a name="admin-guide-install-the-azure-information-protection-client-for-users"></a>Administratorhandbuch: Installieren des Azure Information Protection-Clients für Benutzer

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>
> **Zum Bereitstellen des klassischen AIP-Clients** öffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.

Überprüfen Sie vor der Installation des Azure Information Protection-Clients in Ihrem Unternehmensnetzwerk, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen. Weitere Informationen finden Sie auf der Seite zu den [Anforderungen für Azure Information Protection](../requirements.md).

Überprüfen Sie anschließend die zusätzlichen Voraussetzungen im nächsten Absatz, die eventuell für den Azure Information Protection-Client erforderlich sind. Das Installationsprogramm überprüft nicht alle Voraussetzungen.

## <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Zusätzliche Voraussetzungen für den Azure Information Protection-Client

- Microsoft .NET Framework 4.6.2

    Die vollständige Installation des Azure Information Protection-Clients erfordert standardmäßig Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht der Setup-Assistent, aus dem ausführbaren Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden. Sie können diese Voraussetzung mit einem [benutzerdefinierten Installationsparameter](#more-information-about-the-downgradedotnetrequirement-installation-parameter) umgehen, wenn Sie den Setup-Assistenten verwenden. Diese Vorgehensweise wird jedoch nicht empfohlen.

    Diese Voraussetzung ist nicht automatisch installiert, wenn Sie den Client im Hintergrund über das ausführbare Installationsprogramm, Windows Update oder Windows Installer installieren. Für diese Szenarios müssen Sie diese Voraussetzung ggf. separat installieren, andernfalls schlägt die Installation fehl. Sie können Microsoft .NET Framework 4.6.2 (Offlineinstaller) aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53344) herunterladen.

- Microsoft .NET Framework 4.5.2

    Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom ausführbaren Installationsprogramm nicht heruntergeladen oder installiert.

- Windows PowerShell-Mindestversion 4,0

    Das PowerShell-Modul für den Client erfordert eine Mindestversion von 4,0 für Windows PowerShell, die unter Umständen unter älteren Betriebssystemen installiert werden muss. Weitere Informationen finden Sie unter [How to Install Windows PowerShell 4.0](https://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Installieren von Windows PowerShell 4.0). Das Installationsprogramm überprüft oder installiert diese erforderlichen Komponenten nicht für Sie. Zum Überprüfen, welche Version von Windows PowerShell auf dem Computer ausgeführt wird, geben Sie `$PSVersionTable` in einer PowerShell-Sitzung ein.

- Bildschirmauflösung von mehr als 800 × 600

    Bei einer Auflösung von 800 × 600 und niedriger kann das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** nicht vollständig angezeigt werden, wenn Sie im Datei-Explorer mit der rechten Maustaste auf eine Datei oder einen Ordner klicken.

- Microsoft Online Services-Anmeldeassistent 7.250.4303.0

    Computer, auf denen Office 2010 ausgeführt wird, benötigen Microsoft Online Services-Anmeldeassistent Version 7.250.4303.0. Diese Version ist in der Clientinstallation enthalten. Wenn Sie eine höhere Version des Anmeldeassistenten besitzen, deinstallieren Sie sie vor der Installation des Azure Information Protection-Clients. Überprüfen Sie beispielsweise die Version, und deinstallieren Sie den Anmelde Assistenten mithilfe der **System Steuerungs**Option  >  **Programm und Features**  >  **deinstallieren oder ändern Sie ein Programm**.

- 4482887 KB

    Installieren Sie [1. März 2019 – KB4482887 (Betriebssystembuild 17763.348)](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887) nur für die Windows 10-Version 1809 mit Betriebssystembuilds, die älter sind als 17763.348, damit die Information Protection-Leiste in Office-Anwendungen korrekt angezeigt wird. Dieses Update ist nicht nötig, wenn Sie Office 365 in der Version 1902 oder höher haben.

- Konfigurieren der Gruppenrichtlinie, um die Deaktivierung des Azure Information Protection-Add-In zu verhindern

    Konfigurieren Sie die Gruppenrichtlinie für Office 2013 und höher so, dass das Add-In **Microsoft Azure Information Protection** für Office-Anwendungen immer aktiviert ist. Ohne diese Konfiguration wird das Microsoft Azure Information Protection-Add-In möglicherweise deaktiviert, und Benutzer können ihre Dokumente und E-Mails in ihren Office-Anwendungen nicht kennzeichnen.

    - Für Outlook: Verwenden Sie die Gruppenrichtlinieneinstellung, die in der Office-Dokumentation unter [Kontrolle des Systemadministrators über Add-Ins](https://docs.microsoft.com/office/vba/outlook/concepts/getting-started/support-for-keeping-add-ins-enabled#system-administrator-control-over-add-ins) dokumentiert ist.

    - Für Word, Excel und PowerPoint: Verwenden Sie die Gruppenrichtlinieneinstellung **Liste der verwalteten Add-Ins**, die im Supportartikel [Keine Add-Ins geladen durch Gruppenrichtlinien für Office 2013 und Office 2016](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off) dokumentiert ist.

        Geben Sie die folgenden programmgesteuerten Bezeichner (ProgID) für Azure Information Protection an, und legen Sie die Option auf **1: The add-in is always enabled** (1: Das Add-In ist immer aktiviert) fest.

        Für Word: `MSIP.WordAddin`

        Für Excel: `MSIP.ExcelAddin`

        Für PowerPoint: `MSIP.PowerPointAddin`

- Der AIP-Client wird auf Computern, auf denen der [Exploit-Schutz](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/enable-exploit-protection) aktiviert ist, nicht unterstützt. Achten Sie darauf, den [Exploit-Schutz](../known-issues.md#known-issues-for-installing-the-aip-client) vor der Installation des AIP-Clients zu deaktivieren.  

> [!IMPORTANT]
> Für die Installation des Azure Information Protection-Clients sind lokale Administratorrechte erforderlich.

## <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Optionen zum Installieren des Azure Information Protection-Clients für Benutzer

Verwenden Sie eine der folgenden Optionen zum Installieren des-Clients für Benutzer:

|Option installieren  |BESCHREIBUNG  |
|---------|---------|
|**Ausführen der ausführbaren Client Datei (. exe)**  </br></br> [Anweisungen](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)      | Es wird empfohlen, die exe-Version des Clients auszuführen, um die Installation interaktiv oder im Hintergrund auszuführen.</br></br> Das Ausführen der exe-Datei bietet die größte Flexibilität und wird empfohlen, da Sie außerdem eine Reihe von Voraussetzungen prüft und auch fehlende fehlende Voraussetzungen installieren kann. |
|**Bereitstellen des Windows Installer (. msi) des Clients** </br></br> [Anweisungen](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)    | Der Azure Information Protection-Client Windows Installer wird nur für unbeaufsichtigte Installationen unterstützt, die einen zentralen Bereitstellungs Mechanismus verwenden.</br></br> Verwenden Sie z. b. die MSI-Datei, wenn Sie mit einer Gruppenrichtlinie, Configuration Manager und Microsoft InTune bereitstellen.</br></br> Sie müssen die tis-Methode für Windows 10-PCs verwenden, die von InTune und der Verwaltung mobiler Geräte (Mobile Device Management, MDM) verwaltet werden, da exe-Dateien für diese Computer nicht unterstützt werden.</br></br>**Hinweis:** Wenn Sie die MSI-Installation verwenden, müssen Sie manuell nach erforderlichen Komponenten suchen und abhängige Software installieren oder deinstallieren. |

Führen Sie nach der Installation des-Clients Updates aus, indem Sie die gleiche Installationsmethode wiederholen, oder verwenden Sie Windows Update, um den Client automatisch zu aktualisieren. Vor der Installation einer neuen Version müssen ältere Versionen des Clients nicht deinstalliert werden.

Weitere Informationen finden Sie unter [Upgraden und Verwalten des Azure Information Protection-Clients](client-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-client).

> [!NOTE]
> Verwenden **Sie** zum Deinstallieren des-Clients die Option Software für Windows, z. b. in [der Windows-Systemsteuerung](https://support.microsoft.com/help/4028054/windows-10-repair-or-remove-programs).

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>Installieren des Azure Information Protection-Clients mithilfe des ausführbaren Installationsprogramms

Befolgen Sie die nachstehenden Anweisungen zum Installieren des Clients, wenn Sie nicht den Microsoft Update-Katalog verwenden oder die MSI-Datei über eine zentrale Bereitstellungsmethode wie Intune bereitstellen.

1. Führen Sie für eine Standardinstallation einfach die ausführbare Datei aus, z.B. **AzInfoProtection.exe**. 

    Um andere Installationsoptionen anzuzeigen, führen Sie zuerst die ausführbare Datei mit **/Help**aus: `AzInfoProtection.exe /help`

    Beispiel zum automatischen Installieren des Clients: `AzInfoProtection.exe /quiet`

    Beispiel zum automatischen Installieren der PowerShell-Befehle: `AzInfoProtection.exe  PowerShellOnly=true /quiet`

    Diese zusätzlichen Parameter sind im Hilfebildschirm nicht aufgelistet:

    - **ServiceLocation**: Verwenden Sie diesen Parameter, wenn Sie den Client auf Computern installieren, die Office 2010 ausführen, und Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind, oder wenn Sie keine Eingabeaufforderung für die Benutzer anzeigen lassen möchten. [Weitere Informationen](#more-information-about-the-servicelocation-installation-parameter)

    - **DowngradeDotNetRequirement**: Verwenden Sie diesen Parameter, um die Notwendigkeit von Microsoft Framework .NET, Version 4.6.2, zu umgehen. [Weitere Informationen](#more-information-about-the-downgradedotnetrequirement-installation-parameter)

    - **AllowTelemetry=0**: Verwenden Sie diesen Parameter, um die Installationsoption **Senden Sie Nutzungsstatistiken an Microsoft, und & helfen Sie so mit, Azure Information Protection zu verbessern.** zu deaktivieren.

1. Wenn Sie die interaktive Installation verwenden und sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer **Demorichtlinie**, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.

1. So schließen Sie die Installation ab:

    - Starten Sie den Computer neu, wenn darauf Office 2010 ausgeführt wird.

        Wenn der Client nicht mit dem Parameter „ServiceLocation“ installiert wurde, müssen Sie alle Aufforderungen zum Aktualisieren der Registrierung für diese erste Verwendung bestätigen, wenn Sie erstmalig eine der Office-Anwendungen öffnen, die die Azure Information Protection-Leiste verwenden (z. B. Word). [Dienstermittlung](client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen.

    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu.

1. Sie können anhand der standardmäßig im Ordner „%temp%“ erstellten Installationsprotokolldatei überprüfen, ob die Installation erfolgreich war. Sie können diesen Speicherort mit dem Installationsparameter **/log** ändern.

    Der Name der Datei weist das folgende Format auf: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`.

    Beispiel: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**

    Suchen Sie in dieser Protokolldatei nach der folgenden Zeichenfolge: **Product: Microsoft Azure Information Protection -- Installation completed successfully** (Produkt: Microsoft Azure Information Protection – Installation erfolgreich abgeschlossen). Wenn Fehler bei der Installation auftreten, enthält diese Protokolldatei Informationen, anhand derer Sie Probleme erkennen und diese beheben können.

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

2. Identifizieren Sie in der Ausgabe den Wert von **LicensingIntranetDistributionPointUrl**.

    Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Entfernen Sie in dem Wert **/_wmcs/licensing** aus der Zeichenfolge. Beispiel: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Die Zeichenfolge "restin" ist der Wert, der für Ihren servicelokation-Parameter angegeben wird.

Beispiel zum automatischen Installieren des Clients für Office 2010 und Azure RMS: `AzInfoProtection_UL.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`

#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Weitere Informationen zum DowngradeDotNetRequirement-Installationsparameter

Um automatische Upgrades über Windows Update zu unterstützen und für eine zuverlässige Integration in Office-Anwendungen zu sorgen, verwendet der Azure Information Protection-Client die Microsoft .NET Framework-Version 4.6.2. Eine interaktive Installation prüft standardmäßig mithilfe ausführbarer Überprüfungen, ob diese Version vorhanden ist, und versucht, sie zu installieren, falls sie nicht vorhanden ist. Die Installation erfordert einen Neustart des Computers.

Wenn die Installation dieser höheren Version von Microsoft .NET Framework nicht praktikabel ist, können Sie den Client mit dem auf „True“ festgelegten Parameter **DowngradeDotNetRequirement** installieren. Dadurch wird dieses Erfordernis umgangen, wenn Microsoft .NET Framework, Version 4.5.1, installiert ist.

Beispiel: `AzInfoProtection.exe DowngradeDotNetRequirement=True`

Wir empfehlen, diesen Parameter mit Vorsicht zu verwenden, da uns Probleme mit Office-Anwendungen gemeldet wurden, die nicht mehr reagieren, wenn der Azure Information Protection-Client mit dieser älteren Version von Microsoft .NET Framework verwendet wird. Wenn Sie Probleme mit nicht mehr reagierenden Anwendungen bemerken, aktualisieren Sie auf die empfohlene Version, bevor Sie andere Problembehandlungslösungen versuchen. 

Denken Sie auch an Folgendes: Wenn Sie Windows Update zum Aktualisieren des Azure Information Protection-Clients verwenden, benötigen Sie einen anderen Mechanismus für die Softwarebereitstellung, um den Client auf höhere Versionen zu aktualisieren.

### <a name="to-install-the-azure-information-protection-client-by-using-the-msi-installer"></a>Installieren des Azure Information Protection-Clients mithilfe des MSI-Installationsprogramms

Verwenden Sie bei zentralen Bereitstellungen folgende Informationen, die speziell für die MSI-Installationsversion des Azure Information Protection-Clients gelten. 

Wenn Sie Intune als Bereitstellungsmethode für Ihre Software verwenden, berücksichtigen Sie neben diesen Anweisungen auch die Informationen unter [Hinzufügen von Apps mit Microsoft Intune](/intune/deploy-use/add-apps).

1. Bei jedem Computer, auf dem die MSI-Datei ausgeführt wird, müssen Sie sicherstellen, dass folgende Softwareabhängigkeiten vorliegen. Fügen Sie diese beispielsweise in ein Paket mit der MSI-Version des Clients ein oder stellen Sie sie nur auf Computern bereit, die diese Abhängigkeiten erfüllen:
    
    |Office-Version|Betriebssystem|Software|Aktion|
    |--------------------|--------------|----------------|---------------------|
    |Alle Versionen akzeptieren Office 365, Version 1902 und höher|Nur Windows 10 Version 1809 mit Betriebssystembuilds, die älter als 17763.348 sind|[4482887 KB](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887)|Installieren|
    |Office 2013|Alle unterstützten Versionen|64-Bit: [KB3172523](https://www.microsoft.com/download/details.aspx?id=54992)<br /><br /> 32-Bit: [KB3172523](https://www.microsoft.com/download/details.aspx?id=54979) <br /><br />Version: 1.0|Installieren|
    |Office 2010|Alle unterstützten Versionen|[Microsoft Online Services-Anmelde-Assistent](https://www.microsoft.com/download/details.aspx?id=28177)<br /><br /> Version: 2.1|Installieren|
    |Office 2016|Alle unterstützten Versionen|64-Bit: [KB3178666](https://www.microsoft.com/download/details.aspx?id=55007)<br /><br />32-Bit: [KB3178666](https://www.microsoft.com/download/details.aspx?id=54999)<br /><br /> Version: 1.0|Installieren|
    |Office 2010|Alle unterstützten Versionen|[Microsoft Online Services-Anmelde-Assistent](https://www.microsoft.com/download/details.aspx?id=28177)<br /><br /> Version: 2.1|Installieren|
    |Office 2010|Windows 8.1 und Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB2843630 oder KB2919355 nicht installiert sind.|
    |Office 2010|Windows 8 und Windows Server 2012|[KB2843630](https://www.microsoft.com/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren|

1. Führen Sie die MSI-Datei bei einer Standardinstallation mit **/quiet** aus, z.B. `AzInfoProtection.msi /quiet`. Allerdings müssen möglicherweise weitere Installationsparameter angegeben werden, die in den [Anweisungen zum ausführbaren Installationsprogramm](#to-install-the-azure-information-protection-client-by-using-the-executable-installer) dokumentiert sind.

    > [!NOTE]
    > Standardmäßig ist die Option zur **Verbesserung Azure Information Protection durch das Senden von Nutzungsstatistiken an die Microsoft** -Installation aktiviert. Um diese Option zu deaktivieren, stellen Sie sicher, dass Sie eine der folgenden Aktionen ausführen:
    >
    >- Geben Sie während der Installation **allowtelemetry = 0** an.
    >- Aktualisieren Sie den Registrierungsschlüssel nach der Installation wie folgt: **enabletelemetry = 0**.
    >

## <a name="how-to-install-the-azure-information-protection-scanner"></a>Installieren der Azure Information Protection-Überprüfung

Das im Azure Information Protection-Client enthaltene PowerShell-Modul verfügt über Cmdlets für das Installieren und Konfigurieren der Überprüfung. Um jedoch die Überprüfung verwenden zu können, müssen Sie die Vollversion des Clients installieren. Das PowerShell-Modul alleine reicht nicht aus.

Um den Client für die Überprüfung zu installieren, befolgen Sie die Anleitungen in den vorangehenden Abschnitten. Anschließend können Sie den Scanner konfigurieren und dann installieren. Weitere Informationen finden Sie unter [Was ist der Azure Information Protection Classic Scanner?](../deploy-aip-scanner-classic.md).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie den Azure Information Protection-Client installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentkontrolle](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
