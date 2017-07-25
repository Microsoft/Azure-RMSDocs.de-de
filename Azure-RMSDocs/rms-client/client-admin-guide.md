---
title: "Azure Information Protection-Client – Administratorhandbuch"
description: "Anweisungen und Informationen für Administratoren in einem Unternehmensnetzwerk, die für die Bereitstellung des Azure Information Protection-Clients für Windows zuständig sind."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 036fae62087bf71e0f3bf5ef2859acac701c5e62
ms.sourcegitcommit: 724b0b5d7a3ab694643988148ca68c0eac769f1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2017
---
# <a name="azure-information-protection-client-administrator-guide"></a>Azure Information Protection-Client – Administratorhandbuch

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Verwenden Sie die Informationen in diesem Handbuch, wenn Sie für den Azure Information Protection-Client in einem Unternehmensnetzwerk verantwortlich sind oder wenn Sie mehr technische Informationen erhalten möchten als im [Azure Information Protection-Client – Benutzerhandbuch](client-user-guide.md) vorhanden sind. 

Beispiel:

- Überblick über die verschiedenen Komponenten dieses Clients und Informationen darüber, in welchen Fällen dieser installiert werden soll

- Informationen zum Installieren des Clients für Benutzer mit Angaben zu den Voraussetzungen, Installationsoptionen, Parametern und Überprüfungen

- Informationen zum Anpassen von benutzerdefinierten Konfigurationen, die häufig die Bearbeitung der Registrierung erfordern

- Navigieren zu den Clientdateien und Nutzungsprotokollen

- Identifizieren der vom Client unterstützten Dateitypen

- Konfigurieren und Verwenden der Website für die Dokumentnachverfolgung durch Benutzer

- Verwenden des Clients mit PowerShell zur Steuerung über die Befehlszeile

**Haben Sie eine Frage, die in dieser Dokumentation nicht beantwortet wird?** Besuchen Sie unsere [Yammer-Website für Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-client"></a>Technische Übersicht über den Azure Information Protection-Client

Der Azure Information Protection-Client umfasst Folgendes:

- Ein Add-On für Office, das die Azure Information Protection-Leiste für Benutzer zum Auswählen der Klassifizierungsbezeichnungen sowie die Schaltfläche **Schützen** im Menüband für weitere Optionen installiert.

- Kontextmenüoptionen für den Windows-Datei-Explorer für Benutzer, um Klassifizierungsbezeichnungen und den entsprechenden Schutz auf Dateien anzuwenden.

- Ein Viewer zum Anzeigen geschützter Dateien, wenn diese von einer systemeigenen Anwendung nicht geöffnet werden können.

- Ein PowerShell-Modul zum Anwenden und Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien.

- Der Rights Management-Client, der mit Azure Rights Management (Azure RMS) oder Active Directory Rights Management Services (AD RMS) kommuniziert.

Der Azure Information Protection-Client ist am besten für die Arbeit mit seinen Azure-Diensten geeignet. Azure Information Protection und seine Datenschutzdienste, Azure Rights Management. Der Azure Information Protection-Client funktioniert mit einigen Einschränkungen auch mit der lokalen Version von Rights Management, AD RMS. Einen umfassenden Vergleich der Funktionen, die von Azure Information Protection und AD RMS unterstützt werden, finden Sie unter [Vergleich zwischen Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). 

Wenn Sie über AD RMS verfügen und zu Azure Information Protection migrieren möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) nach.


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Sollten Sie den Azure Information Protection-Client bereitstellen?

Stellen Sie den Azure Information Protection-Client bereit, wenn eine der folgenden Optionen zutrifft:

- Sie möchten Dokumente und E-Mails durch Auswählen von Bezeichnungen innerhalb Ihrer Office-Anwendungen (Word, Excel, PowerPoint, Outlook) klassifizieren (und optional schützen).

- Sie möchten Dokumente und E-Mails mithilfe des Datei-Explorers klassifizieren (und optional schützen), der zusätzliche Dateitypen, die Auswahl mehrerer Objekte und Ordner unterstützt.

- Sie möchten Skripts ausführen, die Dokumente mithilfe von PowerShell-Befehlen klassifizieren (und optional schützen).

- Sie möchten geschützte Dokumente anzeigen, wenn eine systemeigene Anwendung zum Anzeigen der Datei nicht installiert ist oder diese Dokumente nicht öffnen kann.

- Sie möchten Dateien mithilfe des Datei-Explorers oder mithilfe von PowerShell-Befehlen nur schützen.

- Sie möchten, dass Benutzer und Administratoren in der Lage sind, geschützte Dokumente nachzuverfolgen und den Schutz zu widerrufen.

- Sie möchten die Verschlüsselung von Dateien und Containern für Datenwiederherstellungszwecke in Massen entfernen (Schutz aufheben).

- Sie führen Office 2010 aus und möchten Dokumente und E-Mails-mithilfe des Azure Rights Management-Diensts schützen.

Beispiel zur Veranschaulichung des Azure Information Protection-Client-Add-Ons in einer Office-Anwendung, in dem die Klassifizierungsbezeichnungen für Ihre Organisation und die neue Schaltfläche **Schützen** im Menüband angezeigt wird:

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/word2016-calloutsv2.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Installieren des Azure Information Protection-Clients für Benutzer

Überprüfen Sie vor der Installation des Clients, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen: [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md). 

Überprüfen Sie anschließend die zusätzlichen Voraussetzungen, die eventuell für den Azure Information Protection-Client erforderlich sind.

### <a name="additional-prerequisites-for-the-azure-information-protection-client"></a>Zusätzliche Voraussetzungen für den Azure Information Protection-Client

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

> [!IMPORTANT]
> Für die Installation des Azure Information Protection-Clients sind lokale Administratorrechte erforderlich.

### <a name="options-to-install-the-azure-information-protection-client-for-users"></a>Optionen zum Installieren des Azure Information Protection-Clients für Benutzer

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
    |Office 2013|Alle unterstützten Versionen|[KB 3054941](https://www.microsoft.com/en-us/download/details.aspx?id=49337)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|„Installieren“ zu klicken.|
    |Office 2010|Alle unterstützten Versionen|[Microsoft Online Services-Anmeldeassistent](https://www.microsoft.com/en-us/download/details.aspx?id=28177)<br /><br /> Version: 2.1|„Installieren“ zu klicken.|
    |Office 2010|Windows 8.1 und Windows Server 2012 R2|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren, wenn KB 2843630 oder KB 2919355 nicht installiert ist|
    |Office 2010|Windows 8 und Windows Server 2012|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|„Installieren“ zu klicken.|
    |Office 2010|Windows 7|[KB 2843630](https://www.microsoft.com/en-us/download/details.aspx?id=41709)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren, wenn KB 3125574 nicht installiert ist|
    |Nicht verfügbar|Windows 7|KB 2627273 <br /><br /> Im Dateinamen enthaltene Versionsnummer: v4|Deinstallieren|

3. Führen Sie die MSI-Datei bei einer Standardinstallation mit **/quiet** aus, z.B. `AzInfoProtection.msi /quiet`. Allerdings müssen möglicherweise weitere Installationsparameter angegeben werden, die in den [Anweisungen zum ausführbaren Installationsprogramm](#to-install-the-azure-information-protection-client-by-using-the-executable-installer) dokumentiert sind.  

## <a name="additional-checks-and-troubleshooting"></a>Zusätzliche Prüfungen und Problembehandlung

Verwenden Sie die Option **Hilfe und Feedback**, um das Dialogfeld **Microsoft Azure Information Protection** zu öffnen:

- In einer Office-Anwendung: Wählen Sie auf der Registerkarte **Start** in der Gruppe **Schutz** die Optionen **Schützen** und anschließend **Hilfe und Feedback** aus.

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und dann **Hilfe und Feedback** aus. 

### <a name="help-and-feedback-section"></a>Abschnitt **Hilfe und Feedback**

Der Link **Weitere Infos** verweist standardmäßig auf die [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)-Website. Sie können aber auch eine benutzerdefinierte URL als eine der [Richtlinieneinstellungen](../deploy-use/configure-policy-settings.md) in der Azure Information Protection-Richtlinie festlegen.

Verwenden Sie den Link **Feedback senden**, um Vorschläge oder Anfragen an das Information Protection-Team zu senden. Verwenden Sie diese Option nicht für den technischen Support, sondern nutzen Sie dafür stattdessen die [Supportoptionen und Communityressourcen](../get-started/information-support.md#support-options-and-community-resources). 

Die Option **Protokolle exportieren** erfasst automatisch Protokolldateien für den Azure Information Protection-Client und hängt diese an, wenn Sie darum gebeten wurden, diese an den Microsoft Support zu senden. Diese Option kann auch von Endbenutzern verwendet werden, um diese Dateien an Ihren Helpdesk zu senden.

Um Diagnoseinformationen zu erhalten und den Client zurückzusetzen, wählen Sie **Diagnose ausführen** aus. Wenn die Diagnosetests abgeschlossen sind, klicken Sie auf **Ergebnisse kopieren**, um die Informationen in eine E-Mail einzufügen, die Sie an den Microsoft Support bzw. Ihre Endbenutzer an Ihren Helpdesk senden können. Wenn die Tests abgeschlossen sind, können Sie auch den Client zurücksetzen.

> [!NOTE]
> In der Vorschauversion des Clients wurde **Diagnose ausführen** entfernt und durch **Einstellungen zurücksetzen** ersetzt. Darüber hinaus wurde das Verhalten für diese Option [geändert](#more-information-about-the-reset-option-for-the-current-preview-version-of-the-azure-information-protection-client).

#### <a name="more-information-about-the-reset-option-for-the-general-availability-ga-version-of-the-azure-information-protection-client"></a>Weitere Informationen über die Zurücksetzungsoption für die Azure Information Protection-Clientversion für die allgemeine Verfügbarkeit

- Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 

- Sofern Dateien nicht gesperrt sind, löscht diese Aktion alle Dateien im Ordner **%LocalAppData%\Microsoft\MSIPC**, in dem Clientzertifikate und Rights Management-Vorlagen gespeichert werden. Die Azure Information Protection-Richtlinie oder Clientprotokolldateien werden nicht gelöscht, und der Benutzer wird nicht abgemeldet.

- Der folgende Registrierungsschlüssel wird samt Einstellungen gelöscht: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Wenn Sie Einstellungen für diesen Registrierungsschlüssel konfiguriert haben, müssen Sie die Registrierungseinstellungen nach dem Zurücksetzen des Clients konfigurieren. Sie haben z.B.Einstellungen für die Umleitung zu Ihrem Azure Information Protection-Mandanten konfiguriert, da Sie von AD RMS zu Azure Information Protection migrieren und noch einen Dienstverbindungspunkt in Ihrem Netzwerk haben.

- Nachdem Sie den Client zurückgesetzt haben, müssen Sie die Benutzerumgebung erneut initialisieren. Hierdurch werden die Zertifikate für den Client sowie die neuesten Vorlagen heruntergeladen. Schließen Sie hierzu alle Instanzen von Office, und starten Sie eine Office-Anwendung neu. Diese Aktion prüft außerdem, ob Sie die neueste Azure Information Protection-Richtlinie heruntergeladen haben. Führen Sie die Diagnose erst erneut aus, nachdem Sie dies getan haben.

#### <a name="more-information-about-the-reset-option-for-the-current-preview-version-of-the-azure-information-protection-client"></a>Weitere Informationen über die Zurücksetzungsoption für die aktuelle Vorschauversion des Azure Information Protection-Clients

- Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 

- Sofern die Dateien nicht gesperrt sind, löscht diese Aktion alle Dateien in den folgenden Speicherorten. Dies umfasst Clientzertifikate, Rights Management-Vorlagen, die Azure Information Protection-Richtlinie und die zwischengespeicherten Benutzeranmeldeinformationen. Die Clientprotokolldateien werden nicht gelöscht.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- Die folgenden Registrierungsschlüssel und -einstellungen werden gelöscht. Wenn Sie Einstellungen für einen dieser Registrierungsschlüssel konfiguriert haben, müssen Sie diese nach dem Zurücksetzen des Clients erneut konfigurieren. Sie haben z.B. Einstellungen für die Umleitung zu Ihrem Azure Information Protection-Mandanten konfiguriert, da Sie von AD RMS migrieren und noch ein Dienstverbindungspunkt in Ihrem Netzwerk vorhanden ist:
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT-USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC    

- Der derzeit angemeldete Benutzer wird abgemeldet.

### <a name="client-status-section"></a>Abschnitt **Clientstatus**

Verwenden Sie den Wert **Verbunden als**, um zu bestätigen, dass der angezeigte Benutzername das Konto identifiziert, das für die Azure Information Protection-Authentifizierung verwendet werden soll. Dieser Benutzername muss mit einem Konto übereinstimmen, das für Office 365 oder Azure Active Directory verwendet wird. Das Konto muss auch zu einem Mandanten gehören, der für Azure Information Protection konfiguriert ist.

Wenn Sie sich als ein anderer Benutzer anmelden müssen als den angezeigten Benutzer, lesen Sie die Informationen zu Anpassungen unter [Anmelden als ein anderer Benutzer](client-admin-guide-customizations.md#sign-in-as-a-different-user).

Der Wert **Last connection** (Letzte Verbindung) gibt an, wann der Client sich zuletzt mit dem Azure Information Protection-Dienst Ihrer Organisation verbunden hat. Sie können diese Informationen mit der Datums- und Zeitangabe **Die Information Protection-Richtlinie wurde am...installiert** verwenden, um zu bestätigen, wann die Azure Information Protection-Richtlinie zuletzt installiert oder aktualisiert wurde. Wenn der Client eine Verbindung mit dem Dienst herstellt, lädt er automatisch die letzte Richtlinie herunter, sofern diese von der aktuellen Richtlinie abweicht. Die Richtlinie wird außerdem alle 24 Stunden heruntergeladen. Wenn Sie nach dem angezeigten Zeitpunkt Änderungen vorgenommen haben, schließen Sie die Office-Anwendung, und öffnen Sie sie erneut.

Wenn die Meldung **Dieser Client ist nicht für Office Professional Plus lizenziert** angezeigt wird, hat der Azure Information Protection-Client festgestellt, dass die installierte Office-Edition das Anwenden des Rights Management-Schutzes nicht unterstützt. In diesem Fall werden Bezeichnungen, die diesen Schutz anwenden, auf der Azure Information Protection-Leiste nicht angezeigt.

Verwenden Sie die Informationen unter **Version**, um zu bestätigen, welche Version des Clients installiert ist. Klicken Sie auf den Link **Neuigkeiten**, um den [Versionsveröffentlichungsverlauf](client-version-release-history.md) des Clients zu lesen und zu überprüfen, ob es sich um die neueste Version handelt und die entsprechenden Fixes und neuen Features installiert sind.


## <a name="to-uninstall-the-azure-information-protection-client"></a>Deinstallieren des Azure Information Protection-Clients

Sie können jede beliebige Option verwenden:

- Deinstallieren Sie ein Programm über die Systemsteuerung: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**

- Führen Sie die ausführbare Datei (z. B. **AzInfoProtection.exe**) erneut aus, und klicken Sie auf der Seite **Setup ändern** auf **Deinstallieren**. 

- Führen Sie die ausführbare Datei mit **/uninstall** aus. Beispiel: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection-Client installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
