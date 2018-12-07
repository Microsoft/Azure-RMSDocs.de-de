---
title: Bereitstellen der Azure Information Protection-Überprüfung
description: Anleitung zum Installieren, Konfigurieren und Ausführen der Azure Information Protection-Überprüfung, um Dateien in Datenspeichern zu suchen, zu klassifizieren und zu schützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/06/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 20d29079-2fc2-4376-b5dc-380597f65e8a
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: 153009e9c9760649bd42d85bece421e3b8ee5afd
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53024245"
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2*

In diesem Artikel erfahren Sie mehr über die Azure Information Protection-Überprüfung und deren erfolgreiche Installation, Konfiguration und Ausführung. 

Diese Überprüfung wird als Dienst unter Windows Server ausgeführt und bietet Ihnen die Möglichkeit, Dateien auf den folgenden Datenspeichern zu suchen, zu klassifizieren und zu schützen:

- Lokale Ordner auf dem Windows Server-Computer, auf dem die Überprüfung ausgeführt wird

- UNC-Pfade zu Netzwerkfreigaben mit dem Server Message Block (SMB)-Protokoll.

- Websites und Bibliotheken für SharePoint Server 2016 und SharePoint Server 2013 SharePoint 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

Verwenden Sie zum Überprüfen und Bezeichnen von Dateien auf Cloudrepositorys [Cloud App Security](https://docs.microsoft.com/cloud-app-security/).

## <a name="overview-of-the-azure-information-protection-scanner"></a>Übersicht über die Azure Information Protection-Überprüfung

Wenn Sie Ihre [Azure Information Protection-Richtlinie](configure-policy.md) für Bezeichnungen konfiguriert haben, die automatisch klassifizieren, können von der Überprüfung gefundene Dateien gekennzeichnet werden. Bezeichnungen wenden Klassifizierungen sowie optional Schutz an, der auch entfernt werden kann:

![Übersicht über die Architektur der Azure Information Protection-Überprüfung](./media/infoprotect-scanner.png)

Die Überprüfung kann jede Datei überprüfen, die von Windows indiziert werden kann. Dazu verwendet sie IFilters, die auf dem Computer installiert sind. Um zu bestimmen, ob die Dateien Bezeichnungen benötigen, verwendet die Überprüfung die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) oder Regex-Muster von Office 365. Da die Überprüfung den Azure Information Protection-Client verwendet, kann sie dieselben [Dateitypen](./rms-client/client-admin-guide-file-types.md) klassifizieren und schützen.

Sie können die Überprüfung im Suchmodus ausführen. In diesem Modus überprüfen Sie anhand der Berichte, was geschähe, wenn die Dateien bezeichnet würden. Alternativ können Sie die Bezeichnungen mit der Überprüfung automatisch anwenden. Sie können die Überprüfung auch zum Ermitteln von Dateien mit vertraulichen Informationstypen ausführen, ohne Bezeichnungen für Bedingungen zu konfigurieren, die die automatische Klassifizierung anwenden.

Beachten Sie, dass die Überprüfung nicht in Echtzeit sucht und bezeichnet. Sie durchforstet systematisch Dateien auf Datenspeichern, die Sie angeben, und Sie können konfigurieren, ob dieser Zyklus einmal oder mehrmals ausgeführt wird.

Sie können angeben, welche Dateitypen in die Überprüfung eingeschlossen oder von ihr ausgeschlossen werden sollen. Wenn Sie die Dateien einschränken möchten, die bei der Überprüfung untersucht werden sollen, definieren Sie mithilfe von [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes) eine Liste mit Dateitypen.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Voraussetzungen für die Azure Information Protection-Überprüfung
Stellen Sie vor der Installation der Azure Information Protection-Überprüfung sicher, dass folgende Voraussetzungen erfüllt sind.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Windows Server-Computer zum Ausführen des Überprüfungsdiensts:<br /><br />- Prozessoren mit 4 Kernen<br /><br />- 4 GB RAM<br /><br />- 10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien|Windows Server 2016 oder Windows Server 2012 R2 <br /><br />Hinweis: Sie können zu Test- oder Auswertungszwecken ein Windows-Clientbetriebssystem in einer Testumgebung verwenden, das [vom Azure Information Protection-Client unterstützt](requirements.md#client-devices) wird.<br /><br />Dieser Computer kann ein physischer oder ein virtueller Computer mit einer schnellen und zuverlässigen Netzwerkverbindung zu den Datenspeichern sein, die überprüft werden sollen.<br /><br /> Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen. <br /><br />Stellen Sie sicher, dass dieser Computer über die für Azure Information Protection erforderliche [Internetkonnektivität](requirements.md#firewalls-and-network-infrastructure) verfügt. Wenn aufgrund Ihrer Organisationsrichtlinien keine Internetkonnektivität möglich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).|
|SQL-Server, auf dem die Konfiguration der Überprüfung gespeichert wird:<br /><br />- Lokale oder Remoteinstanz<br /><br />– Sysadmin-Rolle zum Installieren der Überprüfung|SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express<br /><br />Bei der Installation von mehreren Instanzen der Überprüfung erfordert jede Überprüfungsinstanz ihre eigene SQL Server-Instanz.<br /><br />Wenn Sie die Überprüfung installieren und Ihr Konto über die Sysadmin-Rolle verfügt, wird während des Installationsprozesses automatisch die AzInfoProtectionScanner-Datenbank erstellt und dem Dienstkonto, das die Überprüfung ausführt, die erforderliche Db_owner-Rolle gewährt. Wenn die Sysadmin-Rolle nicht gewährt wird oder aufgrund der Richtlinien Ihrer Organisation die manuelle Erstellung und Konfiguration von Datenbanken erforderlich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Die Größe der Konfigurationsdatenbank variiert je nach Bereitstellung. Allerdings empfehlen wir, 500 MB je 1.000.000 zu überprüfende Dateien zuzuordnen. |
|Dienstkonto zum Ausführen der Überprüfung|Dieses Konto führt nicht nur den Überprüfungsdienst aus, sondern es wird auch für Azure AD authentifiziert und lädt die Azure Information Protection-Richtlinie herunter. Dieses Konto muss ein Active Directory-Konto sein und mit Azure AD synchronisiert werden. Wenn Sie dieses Konto aufgrund Ihrer Organisationsrichtlinien nicht synchronisieren können, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Für dieses Dienstkonto gelten die folgenden Anforderungen:<br /><br />Berechtigung - **Lokales Anmelden**. Diese Berechtigung ist für die Installation und Konfiguration der Überprüfung erforderlich, aber nicht für den Vorgang selbst. Sie müssen dem Dienstkonto diese Berechtigung gewähren und können sie wieder entfernen, nachdem Sie überprüft haben, dass die Überprüfung Dateien suchen, klassifizieren und schützen kann. Wenn die Gewährung dieser Berechtigung selbst für einen kurzen Zeitraum aufgrund Ihrer Organisationsrichtlinien nicht möglich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Berechtigung - **Als Dienst anmelden**. Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich. <br /><br />– Berechtigungen für Datenrepositorys: Sie müssen **Lese-** und **Schreibberechtigungen** für das Überprüfen, Klassifizieren und Schützen der Dateien erteilen, damit die Dateien die Bedingungen in der Azure Information Protection-Richtlinie erfüllen. Um die Überprüfung nur im Suchmodus auszuführen, genügt eine **Leseberechtigung**.<br /><br />– Für Bezeichnungen, die Schutz erneut anwenden oder ihn entfernen: Um sicherzustellen, dass die Überprüfung immer Zugriff auf geschützte Dateien hat, muss dieses Konto in Azure Rights Management ein [Administrator](configure-super-users.md) sein. Stellen Sie außerdem sicher, dass die Administratorfunktion aktiviert ist. Weitere Informationen zu den Kontoanforderungen zum Anwenden von Schutz finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md). Wenn Sie darüber hinaus [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) für eine stufenweise Bereitstellung implementiert haben, stellen Sie sicher, dass dieses Konto in den von Ihnen konfigurierten Onboarding-Steuerelementen enthalten ist.|
|Der Azure Information Protection-Client ist auf dem Windows Server-Computer installiert.|Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.<br /><br />Eine Anleitung zum Installieren des Clients finden Sie im [Administratorhandbuch](./rms-client/client-admin-guide.md). Wenn Sie die Überprüfung bereits installiert haben und nun auf eine neuere Version aktualisieren müssen, finden Sie weitere Informationen hierzu unter [Aktualisieren der Azure Information Protection-Überprüfung](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|
|Konfigurierte Bezeichnungen, die automatische Klassifizierung und optional Schutz anwenden|Weitere Informationen zur Konfiguration dieser Bedingungen finden Sie unter [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md).<br /><br />Weitere Informationen zum Konfigurieren dieser Bezeichnungen zum Anwenden des Schutzes auf Dateien finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).<br /><br />Diese Bezeichnungen sind in der globalen Richtlinie oder in [bereichsbezogenen Richtlinien](configure-policy-scope.md) zu finden.<br /><br />Hinweis: Obwohl Sie die Überprüfung auch dann ausführen können, wenn Sie über keine konfigurierten Bezeichnungen verfügen, die die automatische Klassifizierung anwenden, wird dieses Szenario in der vorliegenden Anleitung nicht behandelt. [Weitere Informationen](#using-the-scanner-with-alternative-configurations)|
|Für zu scannende Office-Dokumente:<br /><br />-97-2003-Dateiformate und die offene Office-XML-Formate für Word, Excel und PowerPoint|Weitere Informationen zu den Dateitypen, die vom Scanner für diese Dateiformate unterstützt werden, finden Sie unter [Vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md). 

Wenn Sie nicht alle Anforderungen in der Tabelle erfüllen können, da sie aufgrund der Richtlinien Ihrer Organisation nicht zulässig sind, finden Sie im nächsten Abschnitt Alternativen.

Wenn alle Voraussetzungen erfüllt sind, wechseln Sie direkt zum [Abschnitt „Installation“](#install-the-scanner).

### <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die in der Tabelle aufgeführten Voraussetzungen sind die Standardanforderungen für die Überprüfung und werden empfohlen, da sie die einfachste Konfiguration für die Bereitstellung der Überprüfung sind. Sie sollten für die erste Testphase geeignet sein, damit Sie die Funktionen der Überprüfung überprüfen können. In einer Produktumgebung können aufgrund der Richtlinien Ihrer Organisation diese Standardanforderungen jedoch aufgrund einer oder mehrerer der folgenden Einschränkungen nicht zulässig sein:

- Server dürfen nicht mit dem Internet verbunden sein.

- Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

- Die Berechtigung zur **lokalen Anmeldung** kann nicht für Dienstkonten gewährt werden.

- Dienstkonten können nicht mit Azure Active Directory synchronisiert werden, Server verfügen jedoch über Internetkonnektivität.

Bei der Überprüfung können diese Einschränkungen zwar berücksichtigt werden, es ist jedoch eine zusätzliche Konfiguration erforderlich.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Einschränkung: Der Überprüfungsserver kann über keine Internetkonnektivität verfügen.

Folgen Sie den Anweisungen für [nicht verbundene Computer](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers). 

Beachten Sie, dass die Überprüfung in dieser Konfiguration keinen Schutz durch den cloudbasierten Schlüssel Ihrer Organisation anwenden (oder entfernen) kann. Stattdessen ist die Überprüfung auf die Verwendung von Bezeichnungen beschränkt, für die ausschließlich die Klassifizierung verwendet wird, oder auf den Schutz mit [HYOK](configure-adrms-restrictions.md). 

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Wenn Ihnen die Sysadmin-Rolle zur vorübergehenden Installation der Überprüfung zugewiesen werden kann, können Sie diese Rolle nach der Installation der Überprüfung entfernen. Wenn Sie diese Konfiguration verwenden, wird die Datenbank automatisch für Sie erstellt, und das Dienstkonto für die Überprüfung erhält automatisch die erforderlichen Berechtigungen. Das Benutzerkonto, das die Überprüfung konfiguriert, benötigt jedoch die db_owner-Rolle für die AzInfoProtectionScanner-Datenbank, und Sie müssen diese Rolle dem Benutzerkonto manuell zuweisen.

Wenn Ihnen die Sysadmin-Rolle auch nicht vorübergehend zugewiesen werden kann, müssen Sie vor der Installation der Überprüfung manuell eine Datenbank mit dem Namen AzInfoProtectionScanner erstellen. Weisen Sie bei Verwendung dieser Konfiguration die folgenden Rollen zu:
    
|Konto|Rolle auf Datenbankebene|
|--------------------------------|---------------------|
|Dienstkonto für die Überprüfung|db_owner|
|Benutzerkonto für die Installation der Überprüfung|db_owner|
|Benutzerkonto für die Konfiguration der Überprüfung |db_owner|

In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie jedoch unterschiedliche Konten verwenden, benötigen beide die db_owner-Rolle für die AzInfoProtectionScanner-Datenbank.

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Einschränkung: Die Berechtigung zur **lokalen Anmeldung** kann nicht für das Dienstkonto gewährt werden.

Wenn aufgrund der Richtlinien Ihrer Organisation Dienstkonten keine Berechtigung für die **lokale Anwendung** nicht erteilt werden kann, jedoch das **Anmelden als Batchauftrag** zulässig ist, folgen Sie den Anweisungen im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) im Administratorhandbuch.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Einschränkung: Das Überprüfungsdienstkonto kann nicht mit Azure Active Directory synchronisiert werden, der Server verfügt jedoch über Internetkonnektivität.

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Für das Überprüfungsdienstkonto können Sie ein lokales Windows-Konto oder ein Active Directory-Konto verwenden.

- Anweisungen für das Azure Active Directory-Konto finden Sie im Administratorhandbuch im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication).


## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Melden Sie sich bei dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt werden soll. Verwenden Sie ein Konto mit lokalen Administratorrechten und den Berechtigungen zum Schreiben in die SQL Server-Masterdatenbank.

2. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

3. Führen Sie das Cmdlet [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) aus, und geben Sie dabei die SQL Server-Instanz an, auf der eine Datenbank für die Azure Information Protection-Überprüfung erstellt werden soll: 
    
    ```
    Install-AIPScanner -SqlServerInstance <database name>
    ```
    
    Beispiele:
    
    Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`
    
    Verwenden Sie die Onlinehilfe zu diesem Cmdlet, wenn Sie [ausführlichere Beispiele](/powershell/module/azureinformationprotection/install-aipscanner#examples) benötigen.
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Überprüfungsdienstkonto (\<Domäne/Benutzername>) und das Kennwort ein.

4. Stellen Sie unter **Verwaltung** > **Dienste** sicher, dass der Dienst jetzt installiert ist. 
    
    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nun, da Sie die Überprüfung installiert haben, müssen Sie ein Azure AD-Token abrufen, damit das Überprüfungsdienstkonto authentifiziert werden und unbeaufsichtigt ausgeführt werden kann. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Abrufen eines Azure AD-Tokens für die Überprüfung

Mithilfe des Azure AD-Tokens kann das Überprüfungsdienstkonto bei Azure Information Protection authentifiziert werden.

1. Melden Sie auf demselben Windows Server-Computer oder Ihrem Desktop beim Azure-Portal an, um zwei Azure AD-Anwendungen zu erstellen, die für die Angabe eines Zugriffstokens für die Authentifizierung erforderlich sind. Nach einer ersten interaktiven Anmeldung wird die Überprüfung mit diesem Token ohne Benutzereingriff ausgeführt.
    
    Um diese Anwendungen zu erstellen, folgen Sie der Anleitung unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administratorhandbuch.

2. Gehen Sie auf dem Windows Server-Computer folgendermaßen vor, wenn dem Überprüfungsdienstkonto für die Installation das Recht zur **lokalen Anmeldung** erteilt wurde: Melden Sie sich mit diesem Konto an, und starten Sie eine PowerShell-Sitzung. Führen Sie [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) aus, und geben Sie die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```
    
    Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort für Ihr Azure AD-Dienstkonto an, und klicken Sie dann auf **Akzeptieren**.
    
    Wenn Ihrem Überprüfungsdienstkonto das Recht zur **lokalen Anmeldung** für die Installation nicht erteilt werden kann: Befolgen Sie die Anweisungen im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) im Administratorhandbuch. 

Die Überprüfung verfügt jetzt über ein Token für die Authentifizierung bei Azure AD, die ein oder zwei Jahre gültig ist oder nie abläuft, je nach der Konfiguration der **Web-App/API** in Azure AD. Wenn das Token abgelaufen ist, müssen Sie die Schritte 1 und 2 wiederholen.

Sie können nun die zu überprüfenden Datenspeicher angeben. 

## <a name="specify-data-stores-for-the-scanner"></a>Angeben von Datenspeichern für die Überprüfung

Verwenden Sie das Cmdlet [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository), um die Datenspeicher anzugeben, die von der Azure Information Protection-Überprüfung gescannt werden sollen. Sie können lokale Ordner, UNC-Pfade und SharePoint Server-URLs für SharePoint-Websites und -Bibliotheken angeben. 

Unterstützte SharePoint-Versionen: SharePoint Server 2016 oder SharePoint Server 2013 SharePoint Server 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

1. Fügen Sie in der PowerShell-Sitzung über denselben Windows Server-Computer den ersten Datenspeicher hinzu, indem Sie den folgenden Befehl ausführen:
    
        Add-AIPScannerRepository -Path <path>
    
    Beispiel: `Add-AIPScannerRepository -Path \\NAS\Documents`
    
    Weitere Beispiele finden Sie in der [Onlinehilfe](/powershell/module/azureinformationprotection/Add-AIPScannerRepository#examples) zu diesem Cmdlet.

2. Wiederholen Sie diesen Befehl für alle Datenspeicher, die Sie prüfen möchten. Wenn Sie einen hinzugefügten Datenspeicher wieder entfernen möchten, verwenden Sie das Cmdlet [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository).

3. Vergewissern Sie sich mithilfe des Cmdlets [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository), dass Sie alle Datenspeicher richtig angegeben haben:
    
        Get-AIPScannerRepository

Mit der Standardkonfiguration der Überprüfung können Sie nun die erste Überprüfung im Suchmodus ausführen.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Ausführen eines Ermittlungszyklus und Anzeigen von Berichten für die Überprüfung

1. Starten Sie in Ihrer PowerShell-Sitzung den Dienst **Azure Information Protection-Überprüfung** neu, indem Sie den folgenden Befehl ausführen:
    
        Start-AIPScan
    
    Alternativ können Sie die Überprüfung im Azure-Portal vom Blatt **Azure Information Protection** starten, wenn Sie die Option **Überprüfung** > **Knoten (Vorschau)** > \**<* Überprüfungsknoten*>**> **Jetzt überprüfen** verwenden.

2. Warten Sie, bis die Überprüfung ihren Zyklus abgeschlossen hat, indem Sie den folgenden Befehl ausführen:
    
        Get-AIPScannerStatus
    
    Achten Sie darauf, dass der Status **Im Leerlauf** und nicht **Wird überprüft** angezeigt wird. Wenn die Überprüfung alle Dateien in den von Ihnen angegebenen Datenspeichern durchforstet hat, wird die Überprüfung beendet, obwohl der Überprüfungsdienst weiterhin ausgeführt wird. 
    
    Alternativ können Sie den Status im Azure-Portal auf dem Blatt **Azure Information Protection** anzeigen, indem Sie die Spalte **Überprüfung** > **Knoten (Vorschau)** > **\<*Überprüfungsknoten*>**> **STATUS** aktivieren.
    
    Überprüfen Sie das lokale Ereignisprotokoll **Anwendungen und Dienste**, **Azure Information Protection**. Dieses Protokoll gibt außerdem an, wann die Überprüfung abgeschlossen wurde, und zeigt eine Zusammenfassung der Ergebnisse an. Suchen Sie einfach nach der Ereignis-ID **911**.

3. Prüfen Sie die Berichte, die unter %*localappdata*%\Microsoft\MSIP\Scanner\Reports gespeichert sind und im CSV-Format vorliegen. Aufgrund der Standardkonfiguration der Überprüfung sind nur Dateien, die die Bedingungen für die automatische Klassifizierung erfüllen, in diesen Berichten enthalten.
    
    > [!TIP]
    > Überprüfungen senden diese Informationen alle fünf Minuten an Azure Information Protection, so dass Sie die Ergebnisse nahezu in Echtzeit im Azure-Portal anzeigen können. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md). 
        
    Wenn die Ergebnisse nicht wie erwartet ausfallen, müssen Sie die Bedingungen, die Sie in Ihrer Azure Information Protection-Richtlinie angegeben haben, möglicherweise optimieren. Wenn dies der Fall ist, wiederholen Sie die Schritte 1 bis 3, bis Sie die Konfiguration ändern können, um die Klassifizierung und optional den Schutz anzuwenden. 

Wenn Sie für das automatische Bezeichnen der Dateien, die die Überprüfung sucht, bereit sind, fahren Sie mit dem nächsten Abschnitt fort. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz

In der Standardeinstellung wird die Überprüfung einmal und nur im Modus für die Berichterstattung aufgeführt. Um diese Einstellungen zu ändern, führen Sie das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) aus.

1. Führen Sie auf dem Windows Server-Computer in der PowerShell-Sitzung den folgenden Befehl aus:
    
        Set-AIPScannerConfiguration -Enforce On -Schedule Always
    
    Es gibt andere Konfigurationseinstellungen, die Sie ggf. ändern sollten, z.B. ob Dateiattribute geändert werden und was in Berichten protokolliert wird. Wenn Ihre Azure Information Protection-Richtlinie darüber hinaus die Einstellung enthält, die eine Begründungsnachricht erfordert, damit die Klassifizierungsstufe gesenkt oder der Schutz entfernt wird, geben Sie die Nachricht mit diesem Cmdlet an. In der [Onlinehilfe](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration#optional-parameters) finden Sie weitere Informationen zu den einzelnen Konfigurationseinstellungen. 

2. Notieren Sie sich die aktuelle Uhrzeit, und starten Sie die Überprüfung erneut, indem Sie den folgenden Befehl ausführen:
    
        Start-AIPScan
    
    Alternativ können Sie die Überprüfung im Azure-Portal vom Blatt **Azure Information Protection** starten, wenn Sie unter **Überprüfung** > **Knoten (Vorschau)** > \**<* Überprüfungsknoten*>**> die Option **Jetzt überprüfen** verwenden.

3. Überwachen Sie das Ereignisprotokoll erneut, und achten Sie auf den Informationstyp **911** mit einem Zeitstempel, der nach der im vorherigen Schritt notierten Startzeit der Überprüfung liegt. 
    
    Überprüfen Sie die Berichte, um festzustellen, welche Dateien eine Bezeichnung erhalten haben, welche Klassifizierung für die einzelnen Dateien vergeben wurde und ob Schutz angewendet wurde. Oder verwenden Sie das Azure-Portal, um diese Informationen einfacher anzuzeigen.

Da der Zeitplan als fortlaufend konfiguriert wurde, startet die Überprüfung einen neuen Zyklus, sobald der alte abgeschlossen wurde, damit neue und geänderte Dateien gefunden werden.


## <a name="how-files-are-scanned"></a>So werden Dateien überprüft

Bei der Überprüfung werden [von der Klassifizierung und vom Schutz ausgeschlossene](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection) Dateien übersprungen, etwa ausführbare Dateien und Systemdateien.

Sie können dieses Verhalten ändern, indem Sie eine Liste mit Dateitypen definieren, die überprüft oder von der Überprüfung ausgeschlossen werden sollen. Wenn Sie diese Liste angeben, aber kein Datenrepository, gilt die Liste für alle Datenrepositorys, für die keine eigene Liste angegeben wurde. Verwenden Sie zum Angeben der Liste [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes). Nachdem Sie die Liste mit Dateitypen angegeben haben, können Sie mithilfe von [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes) einen neuen Dateityp zur Liste hinzufügen. Mit [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes) kann ein Dateityp aus der Liste entfernt werden.

Die Überprüfung verwendet dann Windows-IFilter, um die folgenden Dateitypen zu überprüfen. Bei diesen Dateitypen wird das Dokument mithilfe der Bedingungen bezeichnet, die Sie für Ihre Bezeichnungen angegeben haben.

|Anwendungstyp|Dateityp|
|--------------------------------|-------------------------------------|
|Word|.docx; .docm; .dotm; .dotx|
|Excel|.xls; .xlt; .xlsx; .xltx; .xltm; .xlsm; .xlsb|
|PowerPoint|.ppt; .pps; .pot; .pptx; .ppsx; .pptm; .ppsm; .potx; .potm|
|PDF |PDF|
|Text|.txt; .xml; .csv|

Darüber hinaus kann die Überprüfung auch optische Zeichenerkennung (Optical Character Recognition, OCR) verwenden, um TIFF-Bilder mit der Dateinamenerweiterung „.tiff“ zu überprüfen, wenn Sie das Windows-TIFF-IFilter-Feature installieren und die [Windows-TIFF-IFilter-Einstellungen](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-7/dd744701%28v%3dws.10%29) auf dem Computer konfigurieren, der die Überprüfung ausführt.

Standardmäßig werden nur Office-Dateitypen von der Überprüfung geschützt. PDF-Dokumente und Textdateien sowie TIFF-Bilder werden also nicht geschützt, sofern Sie nicht die [Registrierung bearbeiten](#editing-the-registry-for-the-scanner), um die Dateitypen anzugeben:

- Wenn Sie den PDF-Dateityp nicht zur Registrierung hinzufügen, werden Dateien mit dieser Erweiterung zwar mit einer Bezeichnung versehen, aber wenn diese nicht für den Schutz konfiguriert ist, wird dieser nicht angewendet.

- Wenn Sie die TXT-, XML- oder CSV-Dateitypen nicht zur Registrierung hinzufügen, werden Dateien mit dieser Erweiterung nicht mit einer Bezeichnung versehen, da diese Dateitypen die ausschließliche Klassifizierung nicht unterstützen.

- Wenn Sie den TIFF-Dateityp nach der Windows-TIFF-IFilter-Konfiguration nicht der Registrierung hinzufügen, werden Dateien mit dieser Erweiterung zwar mit einer Bezeichnung versehen, aber wenn diese Bezeichnung für der Schutz konfiguriert ist, wird der Schutz nicht angewendet.

Schließlich überprüft die Überprüfung die übrigen Dateitypen zwar nicht, wendet aber die Standardbezeichnung in der Azure Information Protection-Richtlinie oder die von Ihnen für die Überprüfung konfigurierte Standardbezeichnung an.

|Anwendungstyp|Dateityp|
|--------------------------------|-------------------------------------|
|Projekt|.mpp; .mpt|
|Herausgeber|.pub|
|Visio|.vsd; .vdw; .vst; .vss; .vsdx; .vsdm; .vssx; .vssm; .vstx; .vstm|
|XPS|.xps; .oxps; .dwfx|
|Solidworks|.sldprt; .slddrw; .sldasm|
|JPEG |.jpg; .jpeg; .jpe; .jif; .jfif; .jfi|
|PNG |PNG|
|GIF|GIF|
|Bitmap|.bmp; .giff|
|TIFF|.tif; .tiff|
|Photoshop|.psdv|
|DigitalNegative|.dng|
|Pfile|PFILE|

Wenn die Überprüfung eine Bezeichnung mit Schutz anwendet, werden standardmäßig nur Office-Dateitypen geschützt. Sie können dieses Verhalten so ändern, dass zusätzliche Dateitypen geschützt werden. Wenn eine Bezeichnung jedoch allgemeinen Schutz auf Dokumente anwendet, wird die Erweiterung in „.pfile“ geändert. Andere Dateitypen können auch ihre Erweiterung ändern. Darüber hinaus sind diese Dateien schreibgeschützt, bis sie von einem autorisierten Benutzer geöffnet und in ihrem nativen Format gespeichert werden.

### <a name="editing-the-registry-for-the-scanner"></a>Bearbeiten der Registrierung für die Überprüfung

Um das Standardverhalten der Überprüfung zum Schutz von Nicht-Office-Dateien zu ändern, müssen Sie die Registrierung manuell bearbeiten und die zusätzlichen Dateitypen angeben, die Sie schützen möchten. Weitere Informationen hierzu finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet. Folgendes gilt außerdem speziell für den Scanner:

- Der Scanner hat sein eigenes Standardverhalten: Nur Office-Dateiformate werden standardmäßig geschützt. Wenn die Registrierung nicht geändert wird, werden andere Dateitypen nicht vom Scanner geschützt.

- Wenn Sie das gleiche Standardschutzverhalten wie beim Azure Information Protection-Client wünschen, d.h. alle Dateien haben automatisch nativen oder generischen Schutz, geben Sie den Platzhalter `*` als Registrierungsschlüssel und `Default` als Wertdaten an.

Wenn Sie die Registrierung bearbeiten, erstellen Sie manuell die beiden Schlüssel **MSIPC** und **FileProtection**, falls noch nicht vorhanden, sowie einen Schlüssel für jede Erweiterung.

Damit die Überprüfung beispielsweise neben Office-Dateien auch PDF-Dateien schützt, sieht die Registrierung nach ihrer Bearbeitung wie folgt aus:

![Bearbeiten der Registrierung für die Überprüfung zum Anwenden von Schutz](./media/editregistry-scanner.png)

## <a name="when-files-are-rescanned"></a>Wann Dateien überprüft werden

Im ersten Überprüfungszyklus untersucht die Überprüfung alle Dateien in den Datenspeichern. In den nachfolgenden Überprüfungen werden dann nur noch neue oder geänderte Dateien untersucht. 

Sie können erzwingen, dass die Überprüfung alle Dateien erneut untersucht, indem Sie den Befehl [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan) mit dem Parameter `-Reset` ausführen. Die Überprüfung muss für einen manuellen Zeitplan konfiguriert sein, was voraussetzt, dass der `-Schedule`-Parameter mit [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) auf **Manual** festgelegt wird.

Alternativ können Sie im Azure-Portal vom Blatt **Azure Information Protection** die Überprüfung aller Dateien erzwingen, indem Sie unter **Überprüfung** > **Knoten (Vorschau)** > \**<* Überprüfungsknoten*>**> die Option **Alle Dateien erneut überprüfen** verwenden.

Das erneute Überprüfen aller Dateien ist nützlich, wenn Sie möchten, dass die Berichte alle Dateien enthalten. Diese Konfiguration wird in der Regel verwendet, wenn die Überprüfung im Ermittlungsmodus ausgeführt wird. Wenn eine vollständige Überprüfung abgeschlossen ist, ändert sich der Überprüfungstyp automatisch auf „inkrementell“, sodass bei nachfolgenden Überprüfungen nur noch neue oder geänderte Dateien untersucht werden.

Außerdem werden alle Dateien untersucht, wenn die Überprüfung eine Azure Information Protection-Richtlinie herunterlädt, die über neue oder geänderte Bedingungen verfügt. Die Überprüfung aktualisiert die Richtlinie entweder jede Stunde oder wenn der Dienst gestartet wird und die Richtlinie älter als eine Stunde ist.  

> [!TIP]
> Wenn Sie die Richtlinie schon früher als dieses einstündige Intervall aktualisieren müssen, beispielsweise während einer Testphase, löschen Sie die Richtliniendatei **Policy.msip** von Hand aus **%LocalAppData%\Microsoft\MSIP\Policy.msip** und **%LocalAppData%\Microsoft\MSIP\Scanner**. Starten Sie anschließend den Azure Information-Überprüfungsdienst neu.
> 
> Wenn Sie die Schutzeinstellungen in der Richtlinie geändert haben, warten Sie 15 Minuten ab dem Zeitpunkt, an dem Sie die Schutzeinstellungen gespeichert haben, bevor Sie den Dienst neu starten.

Wenn die Überprüfung eine Richtlinie heruntergeladen hat, für die keine automatischen Bedingungen konfiguriert wurden, wird die Kopie der Richtliniendatei im Überprüfungsordner nicht aktualisiert. In diesem Szenario müssen Sie die Richtliniendatei **Policy.msip** sowohl aus **%LocalAppData%\Microsoft\MSIP\Policy.msip** als auch aus **%LocalAppData%\Microsoft\MSIP\Scanner** löschen, damit die Überprüfung eine neu heruntergeladene Richtliniendatei verwenden kann, bei der die Bezeichnungen für automatische Bedingungen ordnungsgemäß konfiguriert sind.

## <a name="using-the-scanner-with-alternative-configurations"></a>Verwenden der Überprüfung mit alternativen Konfigurationen

Für die Überprüfung stehen Ihnen zwei alternative Szenarios zur Verfügung, die von Azure Information Protection unterstützt werden, bei denen keine Bezeichnungen für Bedingungen konfiguriert werden müssen: 

- Anwenden einer Standardbezeichnung auf alle Dateien in einem Datenrepository:
    
    Verwenden Sie für diese Konfiguration das Cmdlet [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository), und legen Sie den Parameter *MatchPolicy* auf **Off** fest. 
    
    Die Inhalte der Dateien werden nicht überprüft, und alle Dateien im Datenrepository werden entsprechend der Standardbezeichnung bezeichnet, die Sie für das Datenrepository (mithilfe des Parameters *SetDefaultLabel*) angeben. Andernfalls wird die Standardbezeichnung verwendet, die als Richtlinieneinstellung für das Konto für die Überprüfung angegeben ist.
    

- Identifizieren aller benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen:
    
    Verwenden Sie für diese Konfiguration das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration), und legen Sie den Parameter *DiscoverInformationTypes* auf **All** fest.
    
    Bei der Überprüfung werden alle benutzerdefinierten Bedingungen verwendet, die Sie für Bezeichnungen in der Azure Information Protection-Richtlinie angegeben haben, sowie die Liste der Informationstypen, die zum Angeben von Bezeichnungen in der Azure Information Protection-Richtlinie verfügbar sind.
    
    Diese Konfiguration wird im folgenden Schnellstart verwendet: [Schnellstart: Suche nach vertraulichen Informationen in lokal gespeicherten Dateien](quickstart-findsensitiveinfo.md).

## <a name="optimizing-the-performance-of-the-scanner"></a>Optimieren der Überprüfungsleistung

So maximieren Sie die Überprüfungsleistung:

- **Verwenden Sie eine schnelle und zuverlässige Netzwerkverbindung zwischen dem Überprüfungscomputer und dem überprüften Datenspeicher**
    
    Platzieren Sie beispielsweise den überprüfenden Computer im gleichen LAN oder (vorzugsweise) im gleichen Netzwerksegment wie den überprüften Datenspeicher.
    
    Die Qualität der Netzwerkverbindung wirkt sich auf die Überprüfungsleistung aus, da die Überprüfung die Dateien zur Untersuchung auf den Computer überträgt, auf dem der Überprüfungsdienst ausgeführt wird. Durch Reduzieren (oder Ausschalten) der Anzahl der Netzwerkhops, über die diese Daten transportiert werden, verringern Sie zugleich Ihre Netzwerkauslastung. 

- **Achten Sie darauf, dass der überprüfende Computer verfügbare Prozessorressourcen aufweist**
    
    Das Untersuchen der Dateiinhalte auf eine Übereinstimmung mit den von Ihnen konfigurierten Bedingungen sowie Ver- und Entschlüsseln der Dateien sind prozessorlastige Aktionen. Überprüfen Sie typische Überprüfungszyklen für Ihre angegebenen Datenquellen, um zu bestimmen, ob ein Mangel an Prozessorressourcen sich negativ auf die Überprüfungsleistung auswirkt.
    
- **Überprüfen Sie keine lokalen Ordner auf dem Computer, auf dem der Überprüfungsdienst ausgeführt wird**
    
    Wenn Ordner auf einem Windows-Servercomputer untersucht werden müssen, installieren Sie die Überprüfung auf einem anderen Computer, und konfigurieren Sie diese Ordner als zu überprüfende Netzwerkfreigaben. Das Trennen der beiden Funktionen des Hostens der Dateien und des Überprüfens der Dateien bedeutet, dass die Computerressourcen für diese Dienste nicht in Konkurrenz miteinander stehen.

Installieren Sie ggf. mehrere Instanzen der Überprüfung. Jede Überprüfungsinstanz erfordert eine eigene Konfigurationsdatenbank in einer anderen SQL Server-Instanz.

Weitere Faktoren, die sich auf die Überprüfungsleistung auswirken:

- Die aktuelle Last und die Antwortzeiten der Datenspeicher, in denen die zu überprüfenden Dateien enthalten sind

- Ob die Überprüfung im Suchmodus oder im Durchsetzungsmodus ausgeführt wird
    
    Im Suchmodus wird normalerweise eine höhere Überprüfungsrate als im Durchsetzungsmodus erreicht, da für die Ermittlung ein einzelner Dateilesevorgang erforderlich ist, während für den Durchsetzungsmodus Lese- und Schreibvorgänge erforderlich sind.

- Sie können die Bedingungen in Azure Information Protection ändern
    
    Der erste Überprüfungszyklus, in dem die Überprüfung jede Datei untersuchen muss, benötigt naturgemäß mehr Zeit als die nachfolgenden Überprüfungszyklen, in denen standardmäßig nur neue und geänderte Dateien untersucht werden. Wenn Sie jedoch die Bedingungen in der Azure Information Protection-Richtlinie ändern, werden alle Dateien erneut untersucht, wie im [vorhergehenden Abschnitt](#when-files-are-rescanned) beschrieben.

- Der ausgewählte Protokolliergrad
    
    Sie können für die Überprüfungsberichte zwischen **Debuggen**, **Info**, **Fehler** und **Aus** wählen. **Aus** führt zur besten Leistung; **Debuggen** verlangsamt die Überprüfung erheblich und sollte nur zur Problembehebung verwendet werden. Weitere Informationen finden Sie beim Parameter *ReportLevel* für das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).

- Die Dateien selbst:
    
    - Office-Dateien lassen sich schneller überprüfen als PDF-Dateien.
    
    - Ungeschützte Dateien sind schneller zu überprüfen als geschützte Dateien.
    
    - Das Überprüfen großer Dateien beansprucht naturgemäß mehr Zeit als das Überprüfen kleiner Dateien.

- Darüber hinaus gilt:
    
    - Stellen Sie sicher, dass das Dienstkonto, mit dem die Überprüfung ausgeführt wird, nur über die im Abschnitt [Voraussetzungen für die Azure Information Protection-Überprüfung](#prerequisites-for-the-azure-information-protection-scanner) dokumentierten Rechte verfügt. Konfigurieren Sie anschließend die Eigenschaft [Erweiterter Client](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner), um die niedrige Integritätsebene für die Überprüfung zu deaktivieren.
    
    - Die Überprüfung wird schneller ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der eine Standardbezeichnung auf alle Dateien angewendet wird, ohne dass die Dateiinhalte überprüft werden.
    
    - Die Überprüfung wird langsamer ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der alle benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen identifiziert werden.
    

## <a name="list-of-cmdlets-for-the-scanner"></a>Auflisten der Cmdlets für die Überprüfung 

Mit anderen Cmdlets für die Überprüfung können Sie das Dienstkonto und die Datenbank für die Überprüfung ändern, die aktuellen Einstellungen für die Überprüfung abrufen und die Überprüfung deinstallieren. Die Überprüfung verwendet die folgenden Cmdlets:

- [Add-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Add-AIPScannerScannedFileTypes)

- [Add-AIPScannerRepository](/powershell/module/azureinformationprotection/Add-AIPScannerRepository)

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerRepository](/powershell/module/azureinformationprotection/Get-AIPScannerRepository)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/Remove-AIPScannerRepository)

- [Remove-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Remove-AIPScannerScannedFileTypes)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Set-AIPScannerScannedFileTypes](/powershell/module/azureinformationprotection/Set-AIPScannerScannedFileTypes)

- [Set-AIPScannerRepository](/powershell/module/azureinformationprotection/Set-AIPScannerRepository)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)


## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>Ereignisprotokoll-IDs und Beschreibungen für die Überprüfung

Anhand der folgenden Abschnitte können Sie mögliche Ereignis-IDs und Beschreibungen für die Überprüfung ermitteln. Diese Ereignisse werden im Windows-Ereignisprotokoll für **Anwendungen und Dienste**, **Azure Information Protection**, auf dem Server erfasst, auf dem der Überprüfungsdienst ausgeführt wird.

-----

Information **910**

**Scanner cycle started.** (Überprüfungszyklus wurde gestartet)

Dieses Ereignis wird protokolliert, wenn die Überprüfung gestartet wird und beginnt, die Dateien in den Datenrepositorys zu prüfen, die Sie angegeben haben.

----

Information **911**

**Scanner cycle finished.** (Überprüfungszyklus wurde abgeschlossen)

Dieses Ereignis wird protokolliert, wenn die Überprüfung eine einmalige Überprüfung seit der Inbetriebnahme des Servers oder eine Schleife mit kontinuierlichen Ausführungen beendet hat.

Wenn die Überprüfung so konfiguriert wurde, dass sie einmalig und nicht kontinuierlich ausgeführt wird, müssen Sie zum erneuten Überprüfen der Dateien den Zeitplan auf **OneTime** (einmalig) oder **Continuous** (fortlaufend) festlegen und den Dienst anschließend manuell neu starten. Verwenden Sie zum Ändern des Zeitplans das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration) und den Parameter **Schedule**.

----

## <a name="next-steps"></a>Nächste Schritte

Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Sie fragen sich womöglich, [was der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung ist](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner).

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).


