---
title: "Bereitstellen der Azure Information Protection-Überprüfung"
description: "Anleitung zum Installieren, Konfigurieren und Ausführen der Azure Information Protection-Überprüfung, um Dateien in Datenspeichern zu suchen, zu klassifizieren und zu schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/29/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 986603d54b69fcf85bafecef2691fbd44af94942
ms.sourcegitcommit: c5408506170bdb00d9e677b02161b9f61d4d5d3c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2017
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien

>*Gilt für: Azure Information Protection, Windows Server 2016, Windows Server 2012 R2*

> [!NOTE]
> Dieses Feature befindet sich in der Vorschau und unterliegt Änderungen.

In diesem Artikel erfahren Sie mehr über die Azure Information Protection-Überprüfung und deren erfolgreiche Installation, Konfiguration und Ausführung. 

Diese Überprüfung wird als Dienst unter Windows Server ausgeführt und bietet Ihnen die Möglichkeit, Dateien auf den folgenden Datenspeichern zu suchen, zu klassifizieren und zu schützen:

- Lokale Ordner auf dem Windows Server-Computer, auf dem die Überprüfung ausgeführt wird

- UNC-Pfade für Netzwerkfreigaben, die das CIFS-Protokoll (Common Internet File System) verwenden

- Websites und Bibliotheken für SharePoint Server 2016 und SharePoint Server 2013

## <a name="overview-of-the-azure-information-protection-scanner"></a>Übersicht über die Azure Information Protection-Überprüfung

Wenn Sie Ihre [Azure Information Protection-Richtlinie](configure-policy.md) für Bezeichnungen konfiguriert haben, die automatisch klassifizieren, können von der Überprüfung gefundene Dateien gekennzeichnet werden. Bezeichnungen wenden Klassifizierungen sowie optional Schutz an, der auch entfernt werden kann:

![Übersicht über die Azure Information Protection-Überprüfung](../media/infoprotect-scanner.png)

Die Überprüfung kann jede Datei überprüfen, die von Windows indiziert werden kann. Dazu verwendet er iFilters, die auf dem Computer installiert sind. Um zu bestimmen, ob die Dateien Bezeichnungen benötigen, verwendet die Überprüfung die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) oder Regex-Muster von Office 365. Da die Überprüfung den Azure Information Protection-Client verwendet, kann sie dieselben [Dateitypen](../rms-client/client-admin-guide-file-types.md) klassifizieren und schützen.

Sie können die Überprüfung im Suchmodus ausführen. In diesem Modus überprüfen Sie anhand der Berichte, was geschähe, wenn die Dateien bezeichnet würden. Alternativ können Sie die Bezeichnungen mit der Überprüfung automatisch anwenden.

Beachten Sie, dass die Überprüfung nicht in Echtzeit sucht und bezeichnet. Sie durchforstet systematisch Dateien auf Datenspeichern, die Sie angeben, und Sie können konfigurieren, ob dieser Zyklus einmal oder mehrmals ausgeführt wird.

## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Voraussetzungen für die Azure Information Protection-Überprüfung
Stellen Sie vor der Installation der Azure Information Protection-Überprüfung sicher, dass folgende Voraussetzungen erfüllt sind.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Windows Server-Computer zum Ausführen des Überprüfungsdiensts:<br /><br />- 4 Prozessoren<br /><br />- 4 GB RAM|Windows Server 2016 oder Windows Server 2012 R2 <br /><br />Hinweis: Sie können zu Test- oder Auswertungszwecken ein Windows-Clientbetriebssystem in einer Testumgebung verwenden, das [vom Azure Information Protection-Client unterstützt](../get-started/requirements.md#client-devices) wird.<br /><br />Dieser Computer kann ein physischer oder ein virtueller Computer mit einer schnellen und zuverlässigen Netzwerkverbindung zu den Datenspeichern sein, die überprüft werden sollen. <br /><br />Stellen Sie sicher, dass dieser Computer über die für Azure Information Protection erforderliche [Internetkonnektivität](../get-started/requirements.md#firewalls-and-network-infrastructure) verfügt. Andernfalls müssen Sie ihn als einen [getrennten Computer](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers) konfigurieren. |
|SQL-Server, auf dem die Konfiguration der Überprüfung gespeichert wird:<br /><br />- Lokale oder Remoteinstanz|SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express|
|Dienstkonto zum Ausführen der Überprüfung|Dieses Konto muss ein Active Directory-Konto sein, das mit Azure AD synchronisiert wird, und die folgenden zusätzlichen Anforderungen erfüllen:<br /><br />Berechtigung - **Lokales Anmelden**. Diese Berechtigung ist für die Installation und Konfiguration der Überprüfung erforderlich, aber nicht für den Vorgang selbst. Sie müssen dem Dienstkonto diese Berechtigung gewähren und können sie wieder entfernen, nachdem Sie überprüft haben, dass die Überprüfung Dateien suchen, klassifizieren und schützen kann.<br /><br />Berechtigung - **Als Dienst anmelden**. Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich. <br /><br />– Berechtigungen für Datenrepositorys: Sie müssen **Lese-** und **Schreibberechtigungen** für das Überprüfen, Klassifizieren und Schützen der Dateien erteilen, damit die Dateien die Bedingungen in der Azure Information Protection-Richtlinie erfüllen. Um die Überprüfung nur im Suchmodus auszuführen, genügt eine **Leseberechtigung**.<br /><br />– Für Bezeichnungen, die Schutz erneut anwenden oder ihn entfernen: Um sicherzustellen, dass die Überprüfung immer Zugriff auf geschützte Dateien hat, muss dieses Konto in Azure Rights Management ein [Administrator](configure-super-users.md) sein. Stellen Sie außerdem sicher, dass die Administratorfunktion aktiviert ist. Weitere Informationen zu den Kontoanforderungen zum Anwenden von Schutz finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](../plan-design/prepare.md).|
|Der Azure Information Protection-Client ist auf dem Windows Server-Computer installiert.|Die Azure Information Protection-Überprüfung erfordert zurzeit die Vorschauversion des Azure Information Protection-Clients.<br /><br />Bei Bedarf können Sie den Client nur mit dem PowerShell-Modul (AzureInformationProtection) installieren, mit dem die Überprüfung installiert und konfiguriert wird.<br /><br />Eine Anleitung zum Installieren des Clients finden Sie im [Administratorhandbuch](../rms-client/client-admin-guide.md).|
|Konfigurierte Bezeichnungen, die automatische Klassifizierung und optional Schutz anwenden|Weitere Informationen zur Konfiguration dieser Bedingungen finden Sie unter [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md).<br /><br />Weitere Informationen zum Konfigurieren dieser Bezeichnungen zum Anwenden des Schutzes auf Dateien finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).<br /><br />Diese Bezeichnungen sind in der globalen Richtlinie oder in [bereichsbezogenen Richtlinien](configure-policy-scope.md) zu finden.|


## <a name="install-the-azure-information-protection-scanner"></a>Installieren der Azure Information Protection-Überprüfung

1. Wenn Sie das Dienstkonto verwenden, das Sie für die Ausführung der Überprüfung erstellt haben, melden Sie sich auf dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt wird.

2. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

3. Führen Sie das Cmdlet [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) aus, und geben Sie dabei die SQL Server-Instanz an, auf der eine Datenbank für die Azure Information Protection-Überprüfung erstellt werden soll. Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Überprüfungsdienstkonto (\<Domäne/Benutzername>) und das Kennwort ein: 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name>
    ```
    
    Beispiele:
        
    - Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    - Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    - Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`
    
    Verwenden Sie die Onlinehilfe zu diesem Cmdlet, wenn Sie [ausführlichere Beispiele](/powershell/module/azureinformationprotection/install-aipscanner#examples) benötigen.

4. Stellen Sie unter **Verwaltung** > **Dienste** sicher, dass der Dienst jetzt installiert ist. 
    
    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nun, da Sie die Überprüfung installiert haben, müssen Sie ein Azure AD-Token abrufen, damit das Überprüfungsdienstkonto authentifiziert werden und unbeaufsichtigt ausgeführt werden kann. 

## <a name="get-an-azure-ad-token-for-the-scanner-service-account-to-authenticate-to-the-azure-information-protection-service"></a>Abrufen eines Azure AD-Tokens, damit das Überprüfungsdienstkonto bei Azure Information Protection authentifiziert werden kann

1. Melden Sie auf demselben Windows Server-Computer oder Ihrem Desktop beim Azure-Portal an, um zwei Azure AD-Anwendungen zu erstellen, die für die Angabe eines Zugriffstokens für die Authentifizierung erforderlich sind. Nach einer ersten interaktiven Anmeldung wird die Überprüfung mit diesem Token ohne Benutzereingriff ausgeführt.
    
    Um diese Anwendungen zu erstellen, folgen Sie der Anleitung unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](../rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administratorhandbuch.

2. Führen Sie über den Windows Server-Computer, der weiterhin beim Überprüfungsdienstkonto angemeldet ist, [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) aus, und geben Sie dabei die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application>  -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application >
    ```

3. Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort für Ihr Azure AD-Dienstkonto an, und klicken Sie dann auf **Akzeptieren**.

Die Überprüfung verfügt jetzt über ein Token für die Authentifizierung bei Azure AD, die ein oder zwei Jahre gültig ist oder nie abläuft, je nach der Konfiguration der **Web-App/API** in Azure AD. Wenn das Token abgelaufen ist, müssen Sie die Schritte 1 bis 3 wiederholen.

Sie können nun die zu überprüfenden Datenspeicher angeben. 

## <a name="specify-data-stores-for-the-azure-information-protection-scanner"></a>Angeben der Datenspeicher für die Azure Information Protection-Überprüfung

Verwenden Sie das Cmdlet [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository), um die Datenspeicher anzugeben, die von der Azure Information Protection-Überprüfung gescannt werden sollen. Sie können lokale Ordner, UNC-Pfade und SharePoint Server-URLs für SharePoint-Websites und -Bibliotheken angeben. 

Unterstützte SharePoint-Versionen: SharePoint Server 2016 oder SharePoint Server 2013

1. Fügen Sie in der PowerShell-Sitzung über denselben Windows Server-Computer den ersten Datenspeicher hinzu, indem Sie den folgenden Befehl ausführen:
    
        Add-AIPScannerRepository -Path <path>
    
    Beispiel: `Add-AIPScannerRepository -Path \\NAS\Documents`
    
    Weitere Beispiele finden Sie in der [Onlinehilfe](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples) zu diesem Cmdlet.

2. Wiederholen Sie diesen Befehl für alle Datenspeicher, die Sie prüfen möchten. Wenn Sie einen hinzugefügten Datenspeicher wieder entfernen möchten, verwenden Sie das Cmdlet [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository).

3. Vergewissern Sie sich mithilfe des Cmdlets [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository), dass Sie alle Datenspeicher richtig angegeben haben:
    
        Get-AIPScannerRepository

Mit der Standardkonfiguration der Überprüfung können Sie nun die erste Überprüfung im Suchmodus ausführen.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-azure-information-protection-scanner"></a>Ausführen eines Suchzyklus und Anzeigen von Berichten für die Azure Information Protection-Überprüfung

1. Starten Sie unter **Verwaltung** > **Dienste** den Dienst **Azure Information Protection-Überprüfung**.

2. Warten Sie, bis die Überprüfung den Zyklus abgeschlossen hat. Wenn die Überprüfung alle Dateien in den von Ihnen angegebenen Datenspeichern durchforstet hat, wird der Dienst beendet. Mithilfe des lokalen Windows-Ereignisprototokolls für **Anwendungen und Dienste**, **Azure Information Protection-Überprüfung**, können Sie ermitteln, wann der Dienst beendet wurde. Suchen Sie einfach nach der Ereignis-ID **911**.

3. Prüfen Sie die Berichte, die unter %*localappdata*%\Microsoft\MSIP\Scanner\Reports gespeichert sind und im CSV-Format vorliegen. Aufgrund der Standardkonfiguration der Überprüfung sind nur Dateien, die die Bedingungen für die automatische Klassifizierung erfüllen, in diesen Berichten enthalten.
    
    Wenn die Ergebnisse nicht wie erwartet ausfallen, müssen Sie die Bedingungen, die Sie in Ihrer Azure Information Protection-Richtlinie angegeben haben, möglicherweise optimieren. Wenn dies der Fall ist, wiederholen Sie die Schritte 1 bis 3, bis Sie die Konfiguration ändern können, um die Klassifizierung und optional den Schutz anzuwenden. Führen Sie bei jeder Wiederholung dieser Schritte den folgenden PowerShell-Befehl auf dem Windows Server-Computer aus:
    
        Set-AIPScannerConfiguration -Schedule OneTime

Wenn Sie für das automatische Bezeichnen der Dateien, die die Überprüfung sucht, bereit sind, fahren Sie mit dem nächsten Abschnitt fort. 

## <a name="configure-the-azure-information-protection-scanner-to-apply-classification-and-protection-to-discovered-files"></a>Konfigurieren der Azure Information Protection-Überprüfung zum Anwenden von Klassifizierung und Schutz auf gefundene Dateien

In der Standardeinstellung wird die Überprüfung einmal und nur im Modus für die Berichterstattung aufgeführt. Um diese Einstellungen zu ändern, führen Sie das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) aus.

1. Führen Sie auf dem Windows Server-Computer in der PowerShell-Sitzung den folgenden Befehl aus:
    
        Set-AIPScannerConfiguration -ScanMode Enforce -Schedule Continuous
    
    Es gibt andere Konfigurationseinstellungen, die Sie ggf. ändern sollten, z.B. ob Dateiattribute geändert werden und was in Berichten protokolliert wird. Wenn Ihre Azure Information Protection-Richtlinie darüber hinaus die Einstellung enthält, die eine Begründungsnachricht erfordert, damit die Klassifizierungsstufe gesenkt oder der Schutz entfernt wird, geben Sie die Nachricht mit diesem Cmdlet an. In der [Onlinehilfe](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#parameters) finden Sie weitere Informationen zu den einzelnen Konfigurationseinstellungen. 

2. Starten Sie unter **Verwaltung** > **Dienste** den Dienst **Azure Information Protection-Überprüfung** neu.

3. Überwachen Sie wie zuvor das Ereignisprotokoll und die Berichte, um festzustellen, welche Dateien eine Bezeichnung haben, welche Klassifizierung vergeben wurde und ob Schutz angewendet wurde.

Da der Zeitplan als fortlaufend konfiguriert wurde, startet die Überprüfung einen neuen Synchronisierungszyklus, sobald der alte abgeschlossen wurde, damit neue und geänderte Dateien gefunden werden.

## <a name="when-files-are-rescanned-by-the-azure-information-protection-scanner"></a>Erneutes Einlesen von Dateien durch die Azure Information Protection-Überprüfung

Im ersten Überprüfungszyklus untersucht die Überprüfung alle Dateien in den Datenspeichern. In den nachfolgenden Überprüfungen werden dann nur noch neue oder geänderte Dateien untersucht. 

Sie können erzwingen, dass die Überprüfung alle Dateien erneut untersucht, indem Sie [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) ausführen, während der Parameter `-Type` auf **Vollständig** festgelegt ist. Diese Konfiguration ist hilfreich, wenn Sie möchten, dass die Berichte alle Dateien umfassen. Standardmäßig wird sie verwendet, wenn die Überprüfung im Suchmodus ausgeführt wird. Wenn eine vollständige Überprüfung abgeschlossen ist, ändert sich der Überprüfungstyp automatisch auf „inkrementell“, sodass bei nachfolgenden Überprüfungen nur noch neue oder geänderte Dateien untersucht werden.

Außerdem werden alle Dateien untersucht, wenn die Überprüfung eine Azure Information Protection-Richtlinie herunterlädt, die über neue oder geänderte Bedingungen verfügt. Die Überprüfung aktualisiert die Richtlinie jede Stunde und wenn der Dienst gestartet wird.

## <a name="optimizing-the-performance-of-the-azure-information-protection-scanner"></a>Leistungsoptimierung der Azure Information Protection-Überprüfung

So maximieren Sie die Überprüfungsleistung:

- **Verwenden Sie eine schnelle und zuverlässige Netzwerkverbindung zwischen dem Überprüfungscomputer und dem überprüften Datenspeicher**
    
    Platzieren Sie beispielsweise den überprüfenden Computer im gleichen LAN oder (vorzugsweise) im gleichen Netzwerksegment wie den überprüften Datenspeicher.
    
    Die Qualität der Netzwerkverbindung wirkt sich auf die Überprüfungsleistung aus, da die Überprüfung die Dateien zur Untersuchung auf den Computer überträgt, auf dem der Überprüfungsdienst ausgeführt wird. Durch Reduzieren (oder Ausschalten) der Anzahl der Netzwerkhops, über die diese Daten transportiert werden, verringern Sie zugleich Ihre Netzwerkauslastung. 

- **Achten Sie darauf, dass der überprüfende Computer verfügbare Prozessorressourcen aufweist**
    
    Das Untersuchen der Dateiinhalte auf eine Übereinstimmung mit den von Ihnen konfigurierten Bedingungen sowie Ver- und Entschlüsseln der Dateien sind prozessorlastige Aktionen. Überprüfen Sie typische Überprüfungszyklen für Ihre angegebenen Datenquellen, um zu bestimmen, ob ein Mangel an Prozessorressourcen sich negativ auf die Überprüfungsleistung auswirkt.
    
- **Überprüfen Sie keine lokalen Ordner auf dem Computer, auf dem der Überprüfungsdienst ausgeführt wird**
    
    Wenn Ordner auf einem Windows-Servercomputer untersucht werden müssen, installieren Sie die Überprüfung auf einem anderen Computer, und konfigurieren Sie diese Ordner als zu überprüfende Netzwerkfreigaben. Das Trennen der beiden Funktionen des Hostens der Dateien und des Überprüfens der Dateien bedeutet, dass die Computerressourcen für diese Dienste nicht in Konkurrenz miteinander stehen.

Weitere Faktoren, die sich auf die Überprüfungsleistung auswirken:

- Die aktuelle Last und die Antwortzeiten der Datenspeicher, in denen die zu überprüfenden Dateien enthalten sind

- Ob die Überprüfung im Suchmodus oder im Durchsetzungsmodus ausgeführt wird
    
    Im Suchmodus wird normalerweise eine höhere Überprüfungsrate als im Durchsetzungsmodus erreicht, da für die Ermittlung ein einzelner Dateilesevorgang erforderlich ist, während für den Durchsetzungsmodus Lese- und Schreibvorgänge erforderlich sind.

- Sie können die Bedingungen in Azure Information Protection ändern
    
    Der erste Überprüfungszyklus, in dem die Überprüfung jede Datei untersuchen muss, benötigt naturgemäß mehr Zeit als die nachfolgenden Überprüfungszyklen, in denen standardmäßig nur neue und geänderte Dateien untersucht werden. Wenn Sie jedoch die Bedingungen in der Azure Information Protection-Richtlinie ändern, werden alle Dateien erneut untersucht, wie im [vorhergehenden Abschnitt](#when-files-are-rescanned-by-the-azure-information-protection-scanner) beschrieben.

- Der ausgewählte Protokolliergrad
    
    Sie können für die Überprüfungsberichte zwischen **Debuggen**, **Info**, **Fehler** und **Aus** wählen. **Aus** führt zur besten Leistung; **Debuggen** verlangsamt die Überprüfung erheblich und sollte nur zur Problembehebung verwendet werden. Weitere Informationen finden Sie beim Parameter *ReportLevel* für das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).

- Die Dateien selbst:
    
    - Office-Dateien lassen sich schneller überprüfen als PDF-Dateien.
    
    - Ungeschützte Dateien sind schneller zu überprüfen als geschützte Dateien.
    
    - Das Überprüfen großer Dateien beansprucht naturgemäß mehr Zeit als das Überprüfen kleiner Dateien.

## <a name="list-of-cmdlets-for-the-azure-information-protection-scanner"></a>Liste der Cmdlets für die Azure Information Protection-Überprüfung 

Mit anderen Cmdlets für die Überprüfung können Sie das Dienstkonto und die Datenbank für die Überprüfung ändern, die aktuellen Einstellungen für die Überprüfung abrufen und die Überprüfung deinstallieren. Die Überprüfung verwendet die folgenden Cmdlets:

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)


## <a name="event-log-ids-and-descriptions"></a>Ereignisprotokoll-IDs und Beschreibungen

Anhand der folgenden Abschnitte können Sie mögliche Ereignis-IDs und Beschreibungen für die Überprüfung ermitteln. Diese Ereignisse werden im Windows-Ereignisprotokoll für **Anwendungen und Dienste**, **Azure Information Protection**, auf dem Server erfasst, auf dem der Überprüfungsdienst ausgeführt wird.

-----

Information **910**

**Scanner cycle started.** (Überprüfungszyklus wurde gestartet)

Dieses Ereignis wird protokolliert, wenn die Überprüfung gestartet wird und beginnt, die Dateien in den Datenrepositorys zu prüfen, die Sie angegeben haben.

----

Information **911**

**Scanner cycle finished.** (Überprüfungszyklus wurde abgeschlossen)

Dieses Ereignis wird protokolliert, wenn die Überprüfung eine einmalige Überprüfung seit der Inbetriebnahme des Servers oder eine Schleife mit kontinuierlichen Ausführungen beendet hat.

----

Information **913**

**Scanner is stopped because scanner is set to Never.** (Überprüfung wird beendet, weil die Überprüfung auf „Nie“ festgelegt ist)

Dieses Ereignis wird erfasst, wenn die Überprüfung für eine einmalige statt einer fortlaufenden Ausführung konfiguriert ist und die Azure Information Protection-Überprüfung seit der Inbetriebnahme des Computers manuell neu gestartet wurde.  

Um die Dateien erneut zu überprüfen, müssen Sie den Zeitplan auf **OneTime** (einmalig) oder **Continuous** (fortlaufend) festlegen und den Dienst anschließend manuell neu starten. Verwenden Sie zum Ändern des Zeitplans das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) und den Parameter **Schedule**.

----

Error **912** (Fehler 912)

**Unbekannter Fehler.**

Weitere Informationen sind im detaillierten Bericht protokolliert, der unter %localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_YYYY_MM_DD_HH_MM.csv gespeichert ist.

Wenden Sie sich an den [Microsoft-Support](../get-started/information-support.md#to-contact-microsoft-support), wenn dieses Ereignis weiterhin protokolliert wird. 

----

Error **914** (Fehler 914)

**Service was automatically stopped due to bad configuration: policy file is missing or corrupted.** (Der Dienst wurde aufgrund einer fehlerhaften Konfiguration automatisch beendet: Richtliniendatei fehlt oder wurde manipuliert.)

Dieses Ereignis wird protokolliert, wenn der Azure Information Protection-Client keine gültige Richtliniendatei für die auszuführende Überprüfung hat.

Die Azure Information Protection-Richtlinie ist unter %localappdata%\Microsoft\MSIP gespeichert und muss mit Bezeichnungen konfiguriert werden, deren Bedingungen automatische Klassifizierung anwenden. Andernfalls muss die Richtlinie für eine Standardbezeichnung konfiguriert werden.

Stellen Sie sicher, dass die erforderliche Konnektivität mit dem Internet nicht durch Firewalls blockiert wird. Weitere Informationen finden Sie in den Anforderungen zu [Firewalls und Netzwerkinfrastruktur](../get-started/requirements.md#firewalls-and-network-infrastructure) für Azure Information Protection. Wenn Internetkonnektivität nicht möglich ist, folgen Sie der Anleitung für die Unterstützung von [getrennten Computern](../rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).


## <a name="next-steps"></a>Nächste Schritte

Sie fragen sich womöglich, [was der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung ist](../get-started/faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner).

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](../rms-client/client-admin-guide-powershell.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
