---
title: "Installieren des Azure Information Protection-Clients für Benutzer"
description: "Eine Anleitung und Informationen für Administratoren zum Bereitstellen des Azure Information Protection-Clients für Windows in Unternehmensnetzwerken"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ea3ec965-3720-4614-8564-3ecfe60bc175
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 92e4f6c05378b36165db0628f14941b0ccd26cb7
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="admin-guide-install-the-azure-information-protection-client-for-users"></a>Administratorhandbuch: Installieren des Azure Information Protection-Clients für Benutzer

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Überprüfen Sie vor der Installation des Azure Information Protection-Clients in Ihrem Unternehmensnetzwerk, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen. Weitere Informationen finden Sie auf der Seite zu den [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md). 

Überprüfen Sie anschließend die zusätzlichen Voraussetzungen im nächsten Absatz, die eventuell für den Azure Information Protection-Client erforderlich sind. Das Installationsprogramm überprüft nicht alle Voraussetzungen.

## <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Zusätzliche Voraussetzungen für den Azure Information Protection-Client

- Microsoft .NET Framework 4.6.2
    
    Die vollständige Installation des Azure Information Protection-Clients erfordert standardmäßig Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden. Sie können diese Voraussetzung mit einem [benutzerdefinierten Installationsparameter](#more-information-about-the-downgradedotnetrequirement-installation-parameter) umgehen. Diese Vorgehensweise wird jedoch nicht empfohlen.

- Microsoft .NET Framework 4.5.2
    
    Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom Installationsprogramm nicht heruntergeladen oder installiert.

- Windows PowerShell Version 4.0
    
    Das PowerShell-Modul für den Client erfordert Windows PowerShell Version 4.0. Dieses muss ggf. auf älteren Betriebssystemen installiert werden. Weitere Informationen finden Sie unter [How to Install Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Installieren von Windows PowerShell 4.0). Das Installationsprogramm überprüft oder installiert diese erforderlichen Komponenten nicht für Sie. Zum Überprüfen, welche Version von Windows PowerShell auf dem Computer ausgeführt wird, geben Sie `$PSVersionTable` in einer PowerShell-Sitzung ein.

- Microsoft Online Services-Anmeldeassistent 7.250.4303.0
    
    Computer, auf denen Office 2010 ausgeführt wird, benötigen Microsoft Online Services-Anmeldeassistent Version 7.250.4303.0. Diese Version ist in der Clientinstallation enthalten. Wenn Sie eine höhere Version des Anmeldeassistenten besitzen, deinstallieren Sie sie vor der Installation des Azure Information Protection-Clients. Überprüfen Sie beispielsweise die Version, und deinstallieren Sie den Anmeldeassistenten über **Systemsteuerung** > **Programme und Funktionen** > **Programm deinstallieren oder ändern**.

- KB 2533623
    
    Computer unter Windows 7 Service Pack 1 benötigen KB 2533623. Weitere Informationen zu diesem Update finden Sie unter [Microsoft-Sicherheitsempfehlung: Unsichere Bibliothekladevorgänge können eine Codeausführung von Remotestandorten aus ermöglichen](https://support.microsoft.com/en-us/kb/2533623). Möglicherweise können Sie dieses Update direkt installieren, oder ein anderes Update könnte Vorrang haben, das es für Sie installiert.
    
    Wenn dieses Update benötigt wird und nicht installiert ist, werden Sie in der Clientinstallation gewarnt, dass es installiert werden muss. Dieses Update kann nach der Installation des Clients installiert werden, aber einige Aktionen werden blockiert, und die Meldung wird erneut angezeigt.  

- Visual C++ Redistributable für Visual Studio 2015 (32-Bit Version)
    
    Installieren Sie bei Computern mit Windows 7 Service Pack 1 **vc_redist.x86.exe** von der Downloadseite [Visual C++ Redistributable für Visual Studio 2015](https://www.microsoft.com/en-us/download/details.aspx?id=48145)
    
    Die Installation des Clients überprüft nicht auf diese Voraussetzung, sie ist jedoch für den Azure Information Protection-Client notwendig, um PDF-Dateien zu klassifizieren und zu schützen.

- Deaktivieren Sie die Add-Ins **Microsoft Azure Information Protection** nicht für Office-Anwendungen
    
    Wenn Sie die Einstellung **Liste der verwalteten Add-Ins** der Gruppenrichtlinie konfiguriert haben, fügen Sie das Add-In von Microsoft Azure Information Protection für Office-Anwendungen durch Angabe der folgenden programmgesteuerten Bezeichner (ProgID) für Azure Information Protection hinzu, und legen Sie die Option auf **1: Das Add-In ist immer aktiviert** fest.
    
    - Für Outlook: `MSIP.OutlookAddin`
    
    - Für Word: `MSIP.WordAddin`
    
    - Für Excel: `MSIP.ExcelAddin`
    
    - Für PowerPoint: `MSIP.PowerPointAddin`
    
    Auch wenn Sie die Gruppenrichtlinieneinstellung **Liste der verwalteten Add-Ins** noch nicht konfiguriert haben, müssen Sie diese konfigurieren, wenn Sie Berichte erhalten, dass das Add-In von Microsoft Azure Information Protection deaktiviert wird. Wenn dieses Add-In deaktiviert ist, wird die Leiste von Azure Information Protection Benutzern in der Officeanwendung nicht angezeigt.
    
    Weitere Informationen zur Einstellung der Gruppenrichtlinie finden Sie unter [No Add-ins loaded due to group policy settings for Office 2013 and Office 2016 programs (Es wurden keine Add-Ins geladen aufgrund von Gruppenrichtlinieneinstellungen für die Programme Office 2013 und Office 2016)](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off).

- Für Office Versionen 16.0.8628.2010 und höher (Klick-und-Los): Aktivieren Sie die Legacyunterstützung für Monitore
    
    Hinweis: Für die aktuelle Vorschauversion des Azure Information Protection-Clients gilt diese Voraussetzung nicht. 
    
    Aktivieren Sie ggf. die Legacyunterstützung für Monitore, um zu verhindern, dass die Azure Information Protection-Leiste in diesen Office-Versionen außerhalb der Office-Anwendungen angezeigt wird. Wenn die Leiste in diesem Szenario nicht richtig angezeigt wird, wird Sie möglicherweise als **AdxTaskPane** angezeigt. 
    
    So konfigurieren Sie die Office-Anwendungen für diese Anforderung: **Datei** > **Optionen** > **Allgemein** > **Benutzeroberflächenoptionen**:
    
    - Wenn die Option **bei Verwendung mehrerer Bildschirme** auf **Optimieren für beste Darstellung** eingestellt ist, klicken Sie stattdessen auf **die Kompatibilität optimieren (Neustart der Anwendung erforderlich)**. 
        
    - Falls die Option **Beste Einstellungen für meinen Bildschirm verwenden** ausgewählt ist, entfernen Sie die Auswahl.
    
    - Wenn keine dieser Optionen angezeigt wird, ist keine zusätzliche Konfiguration erforderlich.

> [!IMPORTANT]
> Für die Installation des Azure Information Protection-Clients sind lokale Administratorrechte erforderlich.


## <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Optionen zum Installieren des Azure Information Protection-Clients für Benutzer

Es gibt drei Optionen zum Installieren des Clients für Benutzer:

**Windows Update**: Der Azure Information Protection-Client ist im Microsoft Update-Katalog enthalten. Sie können deshalb den Client mit einem beliebigem Softwareupdatedienst installieren und aktualisieren, der den Katalog nutzt.

**Ausführbare Version (.exe) des Clients ausführen**: Die empfohlene Installationsmethode, die Sie interaktiv oder im Hintergrund ausführen können. Diese Methode bietet die größte Flexibilität und wird empfohlen, da das Installationsprogramm eine Vielzahl der erforderlichen Komponenten überprüft und fehlende erforderliche Komponenten automatisch installieren kann. [Anweisungen](#to-install-the-azure-information-protection-client-by-using-the-executable-installer)

**Windows Installer-Version (MSI) des Clients bereitstellen**: Wird nur für Installationen im Hintergrund unterstützt, die einen zentralen Bereitstellungsmechanismus verwenden, z.B. Gruppenrichtlinien, Konfigurations-Manager und Microsoft Intune. Diese Methode ist für Windows 10-PCs erforderlich, die von Intune und der Verwaltung mobiler Geräte (MDM) verwaltet werden, da bei diesen Computern keine ausführbaren Dateien für die Installation unterstützt werden. Wenn Sie dennoch diese Installationsmethode verwenden, müssen Sie die abhängige Software, die das Installationsprogramm für jeden Computer für die ausführbare Datei ausführen würde, manuell überprüfen und installieren oder deinstallieren. [Anweisungen](#to-install-the-azure-information-protection-client-by-using-the-msi-installer)

### <a name="to-install-the-azure-information-protection-client-by-using-the-executable-installer"></a>Installieren des Azure Information Protection-Clients mithilfe des ausführbaren Installationsprogramms

Befolgen Sie die nachstehenden Anweisungen zum Installieren des Clients, wenn Sie nicht den Microsoft Update-Katalog verwenden oder die MSI-Datei über eine zentrale Bereitstellungsmethode wie Intune bereitstellen.

1. Laden Sie die ausführbare Version des Azure Information Protection-Clients aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen. 

2. Führen Sie für eine Standardinstallation einfach die ausführbare Datei aus, z.B. **AzInfoProtection.exe**. Führen Sie die ausführbare Datei mit dem Parameter **/help** aus, um zuvor die Installationsoptionen anzuzeigen: `AzInfoProtection.exe /help`

    Beispiel zum automatischen Installieren des Clients: `AzInfoProtection.exe /quiet`
    
    Beispiel zum automatischen Installieren der PowerShell-Befehle: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    Diese zusätzlichen Parameter sind im Hilfebildschirm nicht aufgelistet:
    
    - **ServiceLocation**: Verwenden Sie diesen Parameter, wenn Sie den Client auf Computern installieren, die Office 2010 ausführen, und Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind, oder wenn Sie keine Eingabeaufforderung für die Benutzer anzeigen lassen möchten. [Weitere Informationen](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: Verwenden Sie diesen Parameter, um die Notwendigkeit von Microsoft Framework .NET, Version 4.6.2, zu umgehen. [Weitere Informationen](#more-information-about-the-downgradedotnetrequirement-installation-parameter)
    
    - **AllowTelemetry=0**: Verwenden Sie diesen Parameter, um die Installationsoption **Senden Sie Nutzungsstatistiken an Microsoft, und & helfen Sie so mit, Azure Information Protection zu verbessern.** zu deaktivieren. 
    
3. Wenn Sie die interaktive Installation verwenden und sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer **Demorichtlinie**, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.
    
4. So schließen Sie die Installation ab: 

    - Starten Sie den Computer neu, wenn darauf Office 2010 ausgeführt wird. 
        
        Wenn der Client nicht mit dem Parameter „ServiceLocation“ installiert wurde, müssen Sie alle Aufforderungen zum Aktualisieren der Registrierung für diese erste Verwendung bestätigen, wenn Sie erstmalig eine der Office-Anwendungen öffnen, die die Azure Information Protection-Leiste verwenden (z. B. Word). [Dienstermittlung](../rms-client/client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. 
        
5. Sie können anhand der standardmäßig im Ordner „%temp%“ erstellten Installationsprotokolldatei überprüfen, ob die Installation erfolgreich war. Sie können diesen Speicherort mit dem Installationsparameter **/log** ändern. 
 
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

1. Führen Sie aus einer PowerShell-Sitzung zuerst [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) aus, und geben Sie Ihre Administratoranmeldeinformationen an, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen. Führen Sie dann [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration) aus. 
 
    Wenn Sie das PowerShell-Modul für den Azure Rights Management-Dienst noch nicht installiert haben, lesen Sie [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2. Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.

    Beispiel: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Entfernen Sie im Wert den Text **/_wmcs/licensing** aus der Zeichenfolge. Zum Beispiel: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Die verbleibende Zeichenfolge ist der Wert, der für Ihren ServiceLocation-Parameter angegeben wird.

Beispiel zum automatischen Installieren des Clients für Office 2010 und Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


#### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Weitere Informationen zum DowngradeDotNetRequirement-Installationsparameter

Um automatische Upgrades über Windows Update zu unterstützen und für eine zuverlässige Integration in Office-Anwendungen zu sorgen, verwendet der Azure Information Protection-Client die Microsoft .NET Framework-Version 4.6.2. Diese Installation prüft standardmäßig, ob diese Version vorhanden ist, und versucht sie zu installieren, falls sie nicht vorhanden ist. Die Installation erfordert einen Neustart des Computers.

Wenn die Installation dieser höheren Version von Microsoft .NET Framework nicht praktikabel ist, können Sie den Client mit dem auf „True“ festgelegten Parameter **DowngradeDotNetRequirement** installieren. Dadurch wird dieses Erfordernis umgangen, wenn Microsoft .NET Framework, Version 4.5.1, installiert ist.

Beispiel: `AzInfoProtection.exe DowngradeDotNetRequirement=True`

Wir empfehlen, diesen Parameter mit Vorsicht zu verwenden, da uns Probleme mit Office-Anwendungen gemeldet wurden, die nicht mehr reagieren, wenn der Azure Information Protection-Client mit dieser älteren Version von Microsoft .NET Framework verwendet wird. Wenn Sie Probleme mit nicht mehr reagierenden Anwendungen bemerken, aktualisieren Sie auf die empfohlene Version, bevor Sie andere Problembehandlungslösungen versuchen. 

Denken Sie auch an Folgendes: Wenn Sie Windows Update zum Aktualisieren des Azure Information Protection-Clients verwenden, benötigen Sie einen anderen Mechanismus für die Softwarebereitstellung, um den Client auf höhere Versionen zu aktualisieren.

### <a name="to-install-the-azure-information-protection-client-by-using-the-msi-installer"></a>Installieren des Azure Information Protection-Clients mithilfe des MSI-Installationsprogramms

Verwenden Sie bei zentralen Bereitstellungen folgende Informationen, die speziell für die MSI-Installationsversion des Azure Information Protection-Clients gelten. 

Wenn Sie Intune als Bereitstellungsmethode für Ihre Software verwenden, berücksichtigen Sie neben diesen Anweisungen auch die Informationen unter [Hinzufügen von Apps mit Microsoft Intune](/intune/deploy-use/add-apps).

1. Laden Sie die MSI-Version des Azure Information Protection-Clients aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen. 

2. Bei jedem Computer, auf dem die MSI-Datei ausgeführt wird, müssen Sie sicherstellen, dass folgende Softwareabhängigkeiten vorliegen. Fügen Sie diese beispielsweise in ein Paket mit der MSI-Version des Clients ein oder stellen Sie sie nur auf Computern bereit, die diese Abhängigkeiten erfüllen:
    
    |Office-Version|Betriebssystem|Software|Aktion|
    |--------------------|--------------|----------------|---------------------|
    |Office 2016|Alle unterstützten Versionen|64-Bit: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=55007)<br /><br />32-Bit: [KB3178666](https://www.microsoft.com/en-us/download/details.aspx?id=54999)<br /><br /> Version: 1.0|„Installieren“ zu klicken.|
    |Office 2013|Alle unterstützten Versionen|64-Bit: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54992)<br /><br /> 32-Bit: [KB3172523](https://www.microsoft.com/en-us/download/details.aspx?id=54979) <br /><br />Version: 1.0|„Installieren“ zu klicken.|
    |Office 2010|Alle unterstützten Versionen|[Microsoft Online Services-Anmeldeassistent](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Version: 2.1|„Installieren“ zu klicken.|
    |Office 2010|Windows 8.1 und Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB2843630 oder KB2919355 nicht installiert sind.|
    |Office 2010|Windows 8 und Windows Server 2012|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|„Installieren“ zu klicken.|
    |Office 2010|Windows 7 und Windows Server 2008 R2|[KB2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB 3125574 nicht installiert ist|
    |Nicht verfügbar|Windows 7|[vc_redist.x86.exe](https://www.microsoft.com/en-us/download/details.aspx?id=48145)|„Installieren“ zu klicken.|
    |Nicht verfügbar|Windows 7|KB2627273 <br /><br /> Im Dateinamen enthaltene Versionsnummer: v4|Deinstallieren|

3. Führen Sie die MSI-Datei bei einer Standardinstallation mit **/quiet** aus, z.B. `AzInfoProtection.msi /quiet`. Allerdings müssen möglicherweise weitere Installationsparameter angegeben werden, die in den [Anweisungen zum ausführbaren Installationsprogramm](#to-install-the-azure-information-protection-client-by-using-the-executable-installer) dokumentiert sind.  


## <a name="how-to-install-the-azure-information-protection-scanner"></a>Installieren der Azure Information Protection-Überprüfung

Derzeit muss die allgemein verfügbare Version der Azure Information Protection-Überprüfung (**AzInfoProtectionScanner.exe**) separat über das [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) heruntergeladen werden. Nachfolgende Releases der Überprüfung sollen im Lieferumfang des Azure Information Protection-Clients enthalten sein.

Die aktuelle Vorschauversion des Azure Information Protection-Clients enthält ebenfalls die Azure Information Protection-Überprüfung. 

Das im Überprüfungs- und Vorschauclient enthaltene PowerShell-Modul verfügt über Cmdlets für das Installieren und Konfigurieren der Überprüfung.

Um den Client für die Überprüfung zu installieren, befolgen Sie die Anleitungen in den vorangehenden Abschnitten. Wenn Sie nicht alle Komponenten des Clients wie z.B. die Office-Add-Ins und -Viewer benötigen, können Sie nur das PowerShell-Modul installieren. Die ausführbare Datei lässt sich z.B. mit `PowerShellOnly=true /quiet` ausführen.

Nachdem Sie den Client installiert haben, können Sie die Überprüfung installieren. Eine Anleitung hierzu finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](../deploy-use/deploy-aip-scanner.md).


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection-Client installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
