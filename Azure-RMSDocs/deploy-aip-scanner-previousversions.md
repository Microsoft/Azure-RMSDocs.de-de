---
title: Deploy the Azure Information Protection scanner - previous versions
description: Deployment instructions for versions of the Azure Information Protection scanner older than the current general availability version.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 08/28/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e5f0efad328a4c3cd479895e2324538e45a9b922
ms.sourcegitcommit: d9442efe61b55bb158bd50ee69873c028234842d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297609"
---
# <a name="deploying-previous-versions-of-the-azure-information-protection-scanner"></a>Deploying previous versions of the Azure Information Protection scanner

>*Applies to: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*
>
> *Instructions for: [Azure Information Protection client for Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

> [!NOTE]
> This article is for versions of the Azure Information Protection scanner that are earlier than version **1.48.204.0** but still in support. To upgrade earlier versions to the current version, see [Upgrading the Azure Information Protection scanner](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).
> 
> If you are looking for deployment instructions for the current version of the scanner, which includes configuration from the Azure portal, see [Deploying the Azure Information Protection scanner to automatically classify and protect files](deploy-aip-scanner.md).

In diesem Artikel erfahren Sie mehr über die Azure Information Protection-Überprüfung und deren erfolgreiche Installation, Konfiguration und Ausführung.

Diese Überprüfung wird als Dienst unter Windows Server ausgeführt und bietet Ihnen die Möglichkeit, Dateien auf den folgenden Datenspeichern zu suchen, zu klassifizieren und zu schützen:

- Lokale Ordner auf dem Windows Server-Computer, auf dem die Überprüfung ausgeführt wird

- UNC-Pfade zu Netzwerkfreigaben mit dem Server Message Block (SMB)-Protokoll.

- Document libraries and folders for SharePoint Server 2019 through SharePoint Server 2013. SharePoint 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

Verwenden Sie zum Überprüfen und Bezeichnen von Dateien auf Cloudrepositorys [Cloud App Security](https://docs.microsoft.com/cloud-app-security/) anstelle des Scanners.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Übersicht über die Azure Information Protection-Überprüfung

Wenn Sie Ihre [Azure Information Protection-Richtlinie](configure-policy.md) für Bezeichnungen konfiguriert haben, die automatisch klassifizieren, können von der Überprüfung gefundene Dateien gekennzeichnet werden. Bezeichnungen wenden Klassifizierungen sowie optional Schutz an, der auch entfernt werden kann:

![Übersicht über die Architektur der Azure Information Protection-Überprüfung](./media/infoprotect-scanner.png)

Die Überprüfung kann jede Datei überprüfen, die von Windows indiziert werden kann. Dazu verwendet sie IFilters, die auf dem Computer installiert sind. Um zu bestimmen, ob die Dateien Bezeichnungen benötigen, verwendet die Überprüfung die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) oder Regex-Muster von Office 365. Da die Überprüfung den Azure Information Protection-Client verwendet, kann sie dieselben [Dateitypen](./rms-client/client-admin-guide-file-types.md) klassifizieren und schützen.

Sie können die Überprüfung im Suchmodus ausführen. In diesem Modus überprüfen Sie anhand der Berichte, was geschähe, wenn die Dateien bezeichnet würden. Alternativ können Sie die Bezeichnungen mit der Überprüfung automatisch anwenden. Sie können die Überprüfung auch zum Ermitteln von Dateien mit vertraulichen Informationstypen ausführen, ohne Bezeichnungen für Bedingungen zu konfigurieren, die die automatische Klassifizierung anwenden.

Beachten Sie, dass die Überprüfung nicht in Echtzeit sucht und bezeichnet. Sie durchforstet systematisch Dateien auf Datenspeichern, die Sie angeben, und Sie können konfigurieren, ob dieser Zyklus einmal oder mehrmals ausgeführt wird.

Sie können angeben, welche Dateitypen in die Überprüfung eingeschlossen oder von ihr ausgeschlossen werden sollen. Wenn Sie die Dateien einschränken möchten, die bei der Überprüfung untersucht werden sollen, definieren Sie mithilfe von **Set-AIPScannerScannedFileTypes** eine Liste mit Dateitypen.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Voraussetzungen für die Azure Information Protection-Überprüfung
Stellen Sie vor der Installation der Azure Information Protection-Überprüfung sicher, dass folgende Voraussetzungen erfüllt sind.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Windows Server-Computer zum Ausführen des Überprüfungsdiensts:<br /><br />- Prozessoren mit 4 Kernen<br /><br />– 8 GB RAM<br /><br />- 10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien|Windows Server 2019, Windows Server 2016, or Windows Server 2012 R2. <br /><br />**Note**: For testing or evaluation purposes in a non-production environment, you can use a Windows client operating system that is [supported by the Azure Information Protection client](requirements.md#client-devices).<br /><br />Dieser Computer kann ein physischer oder ein virtueller Computer mit einer schnellen und zuverlässigen Netzwerkverbindung zu den Datenspeichern sein, die überprüft werden sollen.<br /><br /> Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen. <br /><br />If internet connectivity is not possible because of your organization policies, see the [Deploying the scanner with alternative configurations](#deploying-the-scanner-with-alternative-configurations) section. Otherwise, make sure that this computer has internet connectivity that allows the following URLs over HTTPS (port 443):<br /> \*.aadrm.com <br /> \*.azurerms.com<br /> \*.informationprotection.azure.com <br /> informationprotection.hosting.portal.azure.net <br /> \*.aria.microsoft.com|
|Dienstkonto zum Ausführen der Überprüfung |Über das Ausführen des Überprüfungsdiensts auf dem Windows-Servercomputer hinaus wird dieses Windows-Konto auch bei Azure AD authentifiziert und lädt die Azure Information Protection-Richtlinie herunter. Dieses Konto muss ein Active Directory-Konto sein und mit Azure AD synchronisiert werden. Wenn Sie dieses Konto aufgrund Ihrer Organisationsrichtlinien nicht synchronisieren können, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Für dieses Dienstkonto gelten die folgenden Anforderungen:<br /><br />- **Lokale Anmeldung** für die Zuweisung von Benutzerrechten. Diese Berechtigung ist für die Installation und Konfiguration der Überprüfung erforderlich, aber nicht für den Vorgang selbst. Sie müssen dem Dienstkonto diese Berechtigung gewähren und können sie wieder entfernen, nachdem Sie überprüft haben, dass die Überprüfung Dateien suchen, klassifizieren und schützen kann. Wenn die Gewährung dieser Berechtigung selbst für einen kurzen Zeitraum aufgrund Ihrer Organisationsrichtlinien nicht möglich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />- **Anmeldung als Dienst** für die Zuweisung von Benutzerrechten. Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich. <br /><br />- Permissions to the data repositories: For data repositories on SharePoint on-premises, always grant the **Edit** permission if **Add and Customize Pages** is selected for the site, or grant the **Design** permission. For other data repositories, grant **Read** and **Write** permissions for scanning the files and then applying classification and protection to the files that meet the conditions in the Azure Information Protection policy. To run the scanner in discovery mode only for these other data repositories, **Read** permission is sufficient.<br /><br />– Für Bezeichnungen, die Schutz erneut anwenden oder ihn entfernen: Um sicherzustellen, dass die Überprüfung immer Zugriff auf geschützte Dateien hat, muss dieses Konto in Azure Rights Management ein [Administrator](configure-super-users.md) sein. Stellen Sie außerdem sicher, dass die Administratorfunktion aktiviert ist. Weitere Informationen zu den Kontoanforderungen zum Anwenden von Schutz finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md). Wenn Sie darüber hinaus [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) für eine stufenweise Bereitstellung implementiert haben, stellen Sie sicher, dass dieses Konto in den von Ihnen konfigurierten Onboarding-Steuerelementen enthalten ist.|
|SQL-Server, auf dem die Konfiguration der Überprüfung gespeichert wird:<br /><br />- Lokale oder Remoteinstanz<br /><br />- [Case insensitive collation](https://docs.microsoft.com/sql/relational-databases/collations/collation-and-unicode-support?view=sql-server-ver15) <br /><br />– Sysadmin-Rolle zum Installieren der Überprüfung|SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express<br /><br />Bei der Installation von mehreren Instanzen der Überprüfung erfordert jede Überprüfungsinstanz ihre eigene SQL Server-Instanz.<br /><br />Wenn Sie die Überprüfung installieren und Ihr Konto über die Sysadmin-Rolle verfügt, wird während des Installationsprozesses automatisch die AzInfoProtectionScanner-Datenbank erstellt und dem Dienstkonto, das die Überprüfung ausführt, die erforderliche Db_owner-Rolle gewährt. Wenn die Sysadmin-Rolle nicht gewährt wird oder aufgrund der Richtlinien Ihrer Organisation die manuelle Erstellung und Konfiguration von Datenbanken erforderlich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Die Größe der Konfigurationsdatenbank variiert je nach Bereitstellung. Allerdings empfehlen wir, 500 MB je 1.000.000 zu überprüfende Dateien zuzuordnen. |
|The Azure Information Protection client (classic) is installed on the Windows Server computer|Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.<br /><br />Eine Anleitung zum Installieren des Clients finden Sie im [Administratorhandbuch](./rms-client/client-admin-guide.md). Wenn Sie die Überprüfung bereits installiert haben und nun auf eine neuere Version aktualisieren müssen, finden Sie weitere Informationen hierzu unter [Aktualisieren der Azure Information Protection-Überprüfung](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|
|Konfigurierte Bezeichnungen, die automatische Klassifizierung und optional Schutz anwenden|Informationen zum Konfigurieren einer Bezeichnung für Bedingungen und zum Anwenden von Schutz:<br /> - [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)<br /> - [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md) <br /><br />**Tip**: You can use the instructions from the [tutorial](infoprotect-quick-start-tutorial.md) to test the scanner with a label that looks for credit card numbers in a prepared Word document. Sie müssen jedoch die Bezeichnungskonfiguration ändern, sodass **Wählen Sie aus, wie diese Bezeichnung angewendet wird** auf **Automatisch** und nicht auf **als Empfehlung** festgelegt wird. Entfernen Sie anschließend die Bezeichnung vom Dokument (sofern angewendet), und kopieren Sie die Datei in ein Datenrepository für den Scanner. Bei einem schnellen Test kann dies ein lokaler Ordner auf dem Computer mit dem Scanner sein.<br /><br /> Zwar können Sie die Überprüfung auch dann ausführen, wenn Sie über keine konfigurierten Bezeichnungen verfügen, die die automatische Klassifizierung anwenden, dieses Szenario wird in der vorliegenden Anleitung jedoch nicht behandelt. [Weitere Informationen](#using-the-scanner-with-alternative-configurations)|
|For SharePoint document libraries and folders to be scanned:<br /><br />- SharePoint 2019<br /><br />– SharePoint 2016<br /><br />– SharePoint 2013<br /><br />– SharePoint 2010|Andere Versionen von SharePoint werden für die Überprüfung nicht unterstützt.<br /><br />When you use [versioning](https://docs.microsoft.com/sharepoint/governance/versioning-content-approval-and-check-out-planning), the scanner inspects and labels the last published version. If the scanner labels a file and [content approval](https://docs.microsoft.com/sharepoint/governance/versioning-content-approval-and-check-out-planning#plan-content-approval) is required, that labeled file must be approved to be available for users. <br /><br />Überprüfen Sie für große SharePoint-Farmen, ob Sie den Schwellwert der Listenansicht (standardmäßig 5.000) erhöhen müssen, damit der Scanner auf alle Dateien zugreifen kann. For more information, see the following SharePoint documentation: [Manage large lists and libraries in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server)|
|Für zu scannende Office-Dokumente:<br /><br />-97-2003-Dateiformate und die offene Office-XML-Formate für Word, Excel und PowerPoint|Weitere Informationen zu den Dateitypen, die vom Scanner für diese Dateiformate unterstützt werden, finden Sie unter [Vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).|
|Für lange Pfade:<br /><br />– höchstens 260 Zeichen, es sei denn, der Scanner ist unter Windows 2016 installiert und der Computer ist für die Unterstützung von langen Pfaden konfiguriert|Windows 10 and Windows Server 2016 support path lengths greater than 260 characters with the following [group policy setting](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/): **Local Computer Policy** > **Computer Configuration** > **Administrative Templates** > **All Settings** > **Enable Win32 long paths**<br /><br /> Weitere Informationen zur Unterstützung von langen Dateipfaden finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Wenn Sie nicht alle Anforderungen in der Tabelle erfüllen können, da sie aufgrund der Richtlinien Ihrer Organisation nicht zulässig sind, finden Sie im nächsten Abschnitt Alternativen.

Wenn alle Voraussetzungen erfüllt sind, wechseln Sie direkt zum [Abschnitt „Installation“](#install-the-scanner).

### <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die in der Tabelle aufgeführten Voraussetzungen sind die Standardanforderungen für die Überprüfung und werden empfohlen, da sie die einfachste Konfiguration für die Bereitstellung der Überprüfung sind. Sie sollten für die erste Testphase geeignet sein, damit Sie die Funktionen der Überprüfung überprüfen können. In einer Produktumgebung können aufgrund der Richtlinien Ihrer Organisation diese Standardanforderungen jedoch aufgrund einer oder mehrerer der folgenden Einschränkungen nicht zulässig sein:

- Servers are not allowed internet connectivity

- Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

- Die Berechtigung zur **lokalen Anmeldung** kann nicht für Dienstkonten gewährt werden.

- Service accounts cannot be synchronized to Azure Active Directory but servers have internet connectivity

Bei der Überprüfung können diese Einschränkungen zwar berücksichtigt werden, es ist jedoch eine zusätzliche Konfiguration erforderlich.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Restriction: The scanner server cannot have internet connectivity

Folgen Sie den Anweisungen für [nicht verbundene Computer](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers). 

Beachten Sie, dass die Überprüfung in dieser Konfiguration keinen Schutz durch den cloudbasierten Schlüssel Ihrer Organisation anwenden (oder entfernen) kann. Stattdessen ist die Überprüfung auf die Verwendung von Bezeichnungen beschränkt, für die ausschließlich die Klassifizierung verwendet wird, oder auf den Schutz mit [HYOK](configure-adrms-restrictions.md). 

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Wenn Ihnen die Sysadmin-Rolle zur vorübergehenden Installation der Überprüfung zugewiesen werden kann, können Sie diese Rolle nach der Installation der Überprüfung entfernen. Wenn Sie diese Konfiguration verwenden, wird die Datenbank automatisch für Sie erstellt, und das Dienstkonto für die Überprüfung erhält automatisch die erforderlichen Berechtigungen. Das Benutzerkonto, das die Überprüfung konfiguriert, benötigt jedoch die db_owner-Rolle für die AzInfoProtectionScanner-Datenbank, und Sie müssen diese Rolle dem Benutzerkonto manuell zuweisen.

If you cannot be granted the Sysadmin role even temporarily, you must ask a user with Sysadmin rights to manually create a database named AzInfoProtectionScanner before you install the scanner. For this configuration, the following roles must be assigned:
    
|Konto|Rolle auf Datenbankebene|
|--------------------------------|---------------------|
|Dienstkonto für die Überprüfung|db_owner|
|Benutzerkonto für die Installation der Überprüfung|db_owner|
|Benutzerkonto für die Konfiguration der Überprüfung |db_owner|

In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie jedoch unterschiedliche Konten verwenden, benötigen beide die db_owner-Rolle für die AzInfoProtectionScanner-Datenbank.

To create a user and grant db_owner rights on this database, ask the Sysadmin to run the following SQL script twice. The first time, for the service account that runs the scanner, and the second time for you to install and manage the scanner. Before running the script, replace *domain\user* with the domain name and user account name of the service account or user account:

    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    USE AzInfoProtectionScanner IF NOT EXISTS (select * from sys.database_principals where sid = SUSER_SID('domain\user')) BEGIN declare @X nvarchar(500) Set @X = 'CREATE USER ' + quotename('domain\user') + ' FROM LOGIN ' + quotename('domain\user'); exec sp_addrolemember 'db_owner', 'domain\user' exec(@X) END

Weiterhin gilt:

- You must be a local administrator on the server that will run the scanner
- The service account that will run the scanner must be granted Full Control permissions to the following registry keys:
    
    - HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\Server
    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server

If, after configuring these permissions, you see an error when you install the scanner, the error can be ignored and you can manually start the scanner service.

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Einschränkung: Die Berechtigung zur **lokalen Anmeldung** kann nicht für das Dienstkonto gewährt werden.

Wenn aufgrund der Richtlinien Ihrer Organisation Dienstkonten keine Berechtigung für die **lokale Anwendung** nicht erteilt werden kann, jedoch das **Anmelden als Batchauftrag** zulässig ist, folgen Sie den Anweisungen im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) im Administratorhandbuch.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Restriction: The scanner service account cannot be synchronized to Azure Active Directory but the server has internet connectivity

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Für das Überprüfungsdienstkonto können Sie ein lokales Windows-Konto oder ein Active Directory-Konto verwenden.

- Anweisungen für das Azure Active Directory-Konto finden Sie im Administratorhandbuch im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication).


## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Melden Sie sich bei dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt werden soll. Verwenden Sie ein Konto mit lokalen Administratorrechten und den Berechtigungen zum Schreiben in die SQL Server-Masterdatenbank.

2. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

3. Führen Sie das Cmdlet **Install-AIPScanner** aus, und geben Sie dabei die SQL Server-Instanz an, auf der eine Datenbank für die Azure Information Protection-Überprüfung erstellt werden soll: 
    
    ```
    Install-AIPScanner -SqlServerInstance <name>
    ```
    
    Beispiele:
    
    Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1`
    
    Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER`
    
    Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS`
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Überprüfungsdienstkonto (\<Domäne/Benutzername>) und das Kennwort ein.

4. Stellen Sie unter **Verwaltung** > **Dienste** sicher, dass der Dienst jetzt installiert ist. 
    
    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nun, da Sie die Überprüfung installiert haben, müssen Sie ein Azure AD-Token abrufen, damit das Überprüfungsdienstkonto authentifiziert werden und unbeaufsichtigt ausgeführt werden kann. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Abrufen eines Azure AD-Tokens für die Überprüfung

Mithilfe des Azure AD-Tokens kann das Überprüfungsdienstkonto bei Azure Information Protection authentifiziert werden.

1. Melden Sie auf demselben Windows Server-Computer oder Ihrem Desktop beim Azure-Portal an, um zwei Azure AD-Anwendungen zu erstellen, die für die Angabe eines Zugriffstokens für die Authentifizierung erforderlich sind. Nach einer ersten interaktiven Anmeldung wird die Überprüfung mit diesem Token ohne Benutzereingriff ausgeführt.
    
    Um diese Anwendungen zu erstellen, folgen Sie der Anleitung unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administratorhandbuch.

2. Gehen Sie auf dem Windows Server-Computer folgendermaßen vor, wenn dem Überprüfungsdienstkonto für die Installation das Recht zur **lokalen Anmeldung** erteilt wurde: Melden Sie sich mit diesem Konto an, und starten Sie eine PowerShell-Sitzung. Führen Sie **Set-AIPAuthentication** aus, und geben Sie die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```
    
    Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort für Ihr Azure AD-Dienstkonto an, und klicken Sie dann auf **Akzeptieren**.
    
    Wenn Ihrem Überprüfungsdienstkonto das Recht zur **lokalen Anmeldung** für die Installation nicht erteilt werden kann: Befolgen Sie die Anweisungen im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) im Administratorhandbuch. 

Die Überprüfung verfügt jetzt über ein Token für die Authentifizierung bei Azure AD, die ein oder zwei Jahre gültig ist oder nie abläuft, je nach der Konfiguration der **Web-App/API** in Azure AD. Wenn das Token abgelaufen ist, müssen Sie die Schritte 1 und 2 wiederholen.

Sie können nun die zu überprüfenden Datenspeicher angeben. 

## <a name="specify-data-stores-for-the-scanner"></a>Angeben von Datenspeichern für die Überprüfung

Verwenden Sie das Cmdlet **Add-AIPScannerRepository**, um die Datenspeicher anzugeben, die von der Azure Information Protection-Überprüfung gescannt werden sollen. You can specify local folders, UNC paths, and SharePoint Server URLs for SharePoint document libraries and folders. 

Supported versions for SharePoint: SharePoint Server 2019, SharePoint Server 2016, and SharePoint Server 2013. SharePoint Server 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

1. Fügen Sie in der PowerShell-Sitzung über denselben Windows Server-Computer den ersten Datenspeicher hinzu, indem Sie den folgenden Befehl ausführen:
    
        Add-AIPScannerRepository -Path <path>
    
    Beispiel: `Add-AIPScannerRepository -Path \\NAS\Documents`
    
    For other examples, use the PowerShell help command `Get-Help Add-AIPScannerRepository -examples` for this cmdlet.

2. Wiederholen Sie diesen Befehl für alle Datenspeicher, die Sie prüfen möchten. Wenn Sie einen hinzugefügten Datenspeicher wieder entfernen möchten, verwenden Sie das Cmdlet **Remove-AIPScannerRepository**.

3. Vergewissern Sie sich mithilfe des Cmdlets **Get-AIPScannerRepository**, dass Sie alle Datenspeicher richtig angegeben haben:
    
        Get-AIPScannerRepository

Mit der Standardkonfiguration der Überprüfung können Sie nun die erste Überprüfung im Suchmodus ausführen.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Ausführen eines Ermittlungszyklus und Anzeigen von Berichten für die Überprüfung

1. Führen Sie in Ihrer PowerShell-Sitzung den folgenden Befehl aus, um die Überprüfung zu starten:
    
        Start-AIPScan
    
    Alternativ können Sie den Scanner über das Azure-Portal starten. From the **Azure Information Protection - Nodes** pane, select your scanner node, and then the **Scan now** option:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

2. Warten Sie, bis die Überprüfung ihren Zyklus abgeschlossen hat, indem Sie den folgenden Befehl ausführen:
    
        Get-AIPScannerStatus
    
    Alternatively, you can view the status from the **Azure Information Protection - Nodes** pane in the Azure portal, by checking the **STATUS** column.
    
    Achten Sie darauf, dass der Status **Im Leerlauf** und nicht **Wird überprüft** angezeigt wird.
    
    Wenn die Überprüfung alle Dateien in den von Ihnen angegebenen Datenspeichern durchforstet hat, wird die Überprüfung beendet, obwohl der Überprüfungsdienst weiterhin ausgeführt wird.
    
    Überprüfen Sie das lokale Ereignisprotokoll **Anwendungen und Dienste**, **Azure Information Protection**. Dieses Protokoll gibt außerdem an, wann die Überprüfung abgeschlossen wurde, und zeigt eine Zusammenfassung der Ergebnisse an. Suchen Sie einfach nach der Ereignis-ID **911**.

3. Lesen Sie die Berichte, die unter %*localappdata*%\Microsoft\MSIP\Scanner\Reports gespeichert sind. Die TXT-Zusammenfassungsdateien enthalten die zum Überprüfen benötigte Zeit, die Anzahl der überprüften Dateien sowie die Anzahl der Dateien mit übereinstimmenden Informationstypen. Die CSV-Dateien enthalten mehr Details zu den einzelnen Dateien. In diesem Ordner werden für jeden Scanzyklus bis zu 60 Berichte gespeichert, die bis auf den letzten alle komprimiert werden, um die Speicherplatzbelegung zu minimieren.
    
    > [!NOTE]
    > Mit dem Cmdlet **Set-AIPScannerConfiguration** können Sie mithilfe des Parameters *ReportLevel* den Protokolliergrad ändern, den Speicherort oder Namen des Berichtsordners jedoch nicht. Wenn Sie die Berichte in einem anderen Volume oder in einer anderen Partition speichern möchten, sollten Sie eine Verzeichnisverbindung verwenden.
    >
    > Verwenden Sie hierzu beispielsweise den Befehl [Mklink](/windows-server/administration/windows-commands/mklink): `mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`
    
    Aufgrund der Standardeinstellung sind nur die Dateien in den ausführlichen Berichten enthalten, die den Bedingungen entsprechen, die Sie für die automatische Klassifizierung konfiguriert haben. Wenn keine von den in diesen Berichten angewendeten Bezeichnungen angezeigt werden, überprüfen Sie, ob die Bezeichnungskonfiguration anstelle der empfohlenen Klassifizierung die automatische Klassifizierung enthält.
    
    > [!TIP]
    > Überprüfungen senden diese Informationen alle fünf Minuten an Azure Information Protection, so dass Sie die Ergebnisse nahezu in Echtzeit im Azure-Portal anzeigen können. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md). 
        
    Wenn die Ergebnisse nicht wie erwartet ausfallen, müssen Sie die Bedingungen, die Sie in Ihrer Azure Information Protection-Richtlinie angegeben haben, möglicherweise optimieren. Wenn dies der Fall ist, wiederholen Sie die Schritte 1 bis 3, bis Sie die Konfiguration ändern können, um die Klassifizierung und optional den Schutz anzuwenden. 

Das Azure-Portal zeigt nur Informationen zur letzten Überprüfung an. Wenn Sie die Ergebnisse vorheriger Überprüfungen anzeigen müssen, sehen Sie sich die Berichte an, die auf dem Überprüfungscomputer im Ordner „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“ gespeichert sind.

Wenn Sie für das automatische Bezeichnen der Dateien, die die Überprüfung sucht, bereit sind, fahren Sie mit dem nächsten Abschnitt fort. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz

In der Standardeinstellung wird die Überprüfung einmal und nur im Modus für die Berichterstattung aufgeführt. To change these settings, use the **Set-AIPScannerConfiguration**:

1. Führen Sie auf dem Windows Server-Computer in der PowerShell-Sitzung den folgenden Befehl aus:
    
        Set-AIPScannerConfiguration -Enforce On -Schedule Always
    
    Es gibt andere Konfigurationseinstellungen, die Sie ggf. ändern sollten, z.B. ob Dateiattribute geändert werden und was in Berichten protokolliert wird. Wenn Ihre Azure Information Protection-Richtlinie darüber hinaus die Einstellung enthält, die eine Begründungsnachricht erfordert, damit die Klassifizierungsstufe gesenkt oder der Schutz entfernt wird, geben Sie die Nachricht mit diesem Cmdlet an. Use the following PowerShell help command for more information about each configuration setting: `Get-Help Set-AIPScannerConfiguration -detailed`

2. Notieren Sie sich die aktuelle Uhrzeit, und starten Sie die Überprüfung erneut, indem Sie den folgenden Befehl ausführen:
    
        Start-AIPScan
    
    Alternativ können Sie den Scanner über das Azure-Portal starten. From the **Azure Information Protection - Nodes** pane, select your scanner node, and then the **Scan now** option:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)

3. Überwachen Sie das Ereignisprotokoll erneut, und achten Sie auf den Informationstyp **911** mit einem Zeitstempel, der nach der im vorherigen Schritt notierten Startzeit der Überprüfung liegt. 
    
    Überprüfen Sie die Berichte, um festzustellen, welche Dateien eine Bezeichnung erhalten haben, welche Klassifizierung für die einzelnen Dateien vergeben wurde und ob Schutz angewendet wurde. Oder verwenden Sie das Azure-Portal, um diese Informationen einfacher anzuzeigen.

Da der Zeitplan als fortlaufend konfiguriert wurde, startet die Überprüfung einen neuen Zyklus, sobald der alte abgeschlossen wurde, damit neue und geänderte Dateien gefunden werden.


## <a name="how-files-are-scanned"></a>So werden Dateien überprüft

Der Scanner führt die folgenden Prozesse zur Überprüfung von Dateien aus.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. Determine whether files are included or excluded for scanning 
Bei der Überprüfung werden [von der Klassifizierung und vom Schutz ausgeschlossene](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection) Dateien wie ausführbare Dateien und Systemdateien übersprungen.

Sie können dieses Verhalten ändern, indem Sie eine Liste mit Dateitypen definieren, die überprüft oder von der Überprüfung ausgeschlossen werden sollen. Wenn Sie diese Liste angeben, aber kein Datenrepository, gilt die Liste für alle Datenrepositorys, für die keine eigene Liste angegeben wurde. Verwenden Sie zum Angeben der Liste **Set-AIPScannerScannedFileTypes**. 

Nachdem Sie die Liste mit Dateitypen angegeben haben, können Sie mithilfe von **Add-AIPScannerScannedFileTypes** einen neuen Dateityp zur Liste hinzufügen. Mit **Remove-AIPScannerScannedFileTypes** kann ein Dateityp aus der Liste entfernt werden.

### <a name="2-inspect-and-label-files"></a>2. Inspect and label files

Anschließend verwendet der Scanner Filter, um unterstützte Dateitypen zu überprüfen. Diese Filter werden auch vom Betriebssystem für Windows Search und die Indizierung verwendet. Wenn keine anderen Konfigurationen vorhanden sind, wird Windows-IFilter verwendet, um Dateitypen zu überprüfen, die nicht für Word-, Excel-, PowerPoint- und PDF-Dokumente sowie Textdateien verwendet werden.

Eine vollständige Liste der standardmäßig unterstützten Dateitypen und zusätzliche Informationen zum Konfigurieren vorhandener Filter, die ZIP- und TIFF-Dateien umfassen, finden Sie unter [File types supported for inspection (Für die Überprüfung unterstützte Dateitypen)](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-inspection).

Nach der Überprüfung können diese Dateitypen mithilfe der Bedingungen bezeichnet werden, die Sie für Ihre Bezeichnungen angegeben haben. Wenn Sie den Suchmodus verwenden, ist für diese Dateien stattdessen festgelegt, dass sie die Bedingungen enthalten, die Sie für Ihre Bezeichnungen angegeben haben, oder dass sämtliche bekannten Typen von vertraulichen Informationen enthalten sind. 

Der Scanner kann die Dateien jedoch unter den folgenden Bedingungen nicht bezeichnen:

- Wenn die Bezeichnung zwar die Klassifizierung, aber keinen Schutz anwendet und der Dateityp nicht [ausschließlich die Klassifizierung unterstützt](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only)

- Wenn die Bezeichnung zwar Klassifizierung und Schutz anwendet, aber der Scanner den Dateityp nicht schützt
    
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Sie können andere Dateitypen schützen, indem Sie wie im folgenden Abschnitt beschrieben [die Registrierung bearbeiten](#editing-the-registry-for-the-scanner).

Beispielsweise kann der Scanner, nachdem er TXT-Dateien überprüft hat, keine Bezeichnungen anwenden, die nur für die Klassifizierung und nicht für den Schutz konfiguriert sind, weil der TXT-Dateityp dies nicht unterstützt. Wenn die Bezeichnung für Klassifizierung und Schutz konfiguriert ist und die Registrierung für den TXT-Dateityp bearbeitet wird, kann der Scanner die Datei bezeichnen. 

> [!TIP]
> Wenn während dieses Vorgangs der Scanner stoppt und die Überprüfung einer großen Anzahl von Dateien in einem Repository nicht abgeschlossen wird:
> 
> - Möglicherweise müssen Sie die Anzahl der dynamischen Ports für das Betriebssystem erhöhen, das die Dateien hostet. Ein Grund dafür, warum der Scanner die Anzahl an zulässigen Netzwerkverbindungen überschreitet und daher angehalten wird, ist die Serverhärtung für SharePoint.
>     
>     To check whether this is the cause of the scanner stopping, look to see if the following error message is logged for the scanner in %*localappdata*%\Microsoft\MSIP\Logs\MSIPScanner.iplog (zipped if there are multiple logs): **Unable to connect to the remote server ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted IP:port**
>    
>     Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](https://docs.microsoft.com/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).
> 
> - Für große SharePoint-Farmen müssen Sie möglicherweise den Schwellenwert der Listenansicht (standardmäßig 5.000) erhöhen. For more information, see the following SharePoint documentation: [Manage large lists and libraries in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).

### <a name="3-label-files-that-cant-be-inspected"></a>3. Label files that can't be inspected
Bei Dateitypen, die nicht überprüft werden können, wendet der Scanner die Standardbezeichnung in der Azure Information Protection-Richtlinie oder die von Ihnen für die Überprüfung konfigurierte Standardbezeichnung an.

Wie im vorherigen Schritt kann der Scanner die Dateien jedoch unter den folgenden Bedingungen nicht bezeichnen:

- Wenn die Bezeichnung zwar die Klassifizierung, aber keinen Schutz anwendet und der Dateityp nicht [ausschließlich die Klassifizierung unterstützt](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only)

- Wenn die Bezeichnung zwar Klassifizierung und Schutz anwendet, aber der Scanner den Dateityp nicht schützt
    
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Sie können andere Dateitypen schützen, indem Sie wie im folgenden Abschnitt beschrieben [die Registrierung bearbeiten](#editing-the-registry-for-the-scanner).


### <a name="editing-the-registry-for-the-scanner"></a>Bearbeiten der Registrierung für die Überprüfung

Um das Standardverhalten der Überprüfung zum Schutz von Dateien zu ändern, bei denen es sich weder um Office- noch um PDF-Dateien handelt, müssen Sie die Registrierung manuell bearbeiten und die zusätzlichen Dateitypen angeben, die geschützt werden sollen, sowie den Typ des Schutzes (nativ oder generisch) festlegen. Weitere Informationen hierzu finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet. Folgendes gilt außerdem speziell für den Scanner:

- The scanner has its own default behavior: Only Office file formats and PDF documents are protected by default. Wenn die Registrierung nicht geändert wird, werden andere Dateitypen nicht vom Scanner bezeichnet oder geschützt.

- If you want the same default protection behavior as the Azure Information Protection client, where all files are automatically protected with native or generic protection: Specify the `*` wildcard as a registry key, `Encryption` as the value (REG_SZ), and `Default` as the value data.

Wenn Sie die Registrierung bearbeiten, erstellen Sie manuell die beiden Schlüssel **MSIPC** und **FileProtection**, falls noch nicht vorhanden, sowie einen Schlüssel für jede Erweiterung.

Damit die Überprüfung beispielsweise neben Office- und PDF-Dateien auch TIFF-Bilder schützt, sieht die Registrierung nach Ihrer Bearbeitung wie in der folgenden Abbildung aus. TIFF-Dateien unterstützen als Bilddateien den nativen Schutz. Die entsprechende Erweiterung lautet „.ptiff“.

![Bearbeiten der Registrierung für die Überprüfung zum Anwenden von Schutz](./media/editregistry-scanner.png)

Eine Liste mit Text- und Bilddateitypen, die zwar ebenfalls den nativen Schutz unterstützen, aber in der Registrierung angegeben werden müssen, finden Sie im Administratorleitfaden unter [Unterstützte Dateitypen für Klassifizierung und Schutz](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection).

Geben Sie für Dateien, die den nativen Schutz nicht unterstützten, die Erweiterung als einen neuen Schlüssel und **PFILE** für den generischen Schutz an. Die Erweiterung für die geschützte Datei lautet dann „.pfile“.


## <a name="when-files-are-rescanned"></a>Wann Dateien überprüft werden

Im ersten Überprüfungszyklus untersucht die Überprüfung alle Dateien in den Datenspeichern. In den nachfolgenden Überprüfungen werden dann nur noch neue oder geänderte Dateien untersucht. 

You can force the scanner to inspect all files again by running **Start-AIPScan** with the *Reset* parameter. The scanner must be configured for a manual schedule, which requires the *Schedule* parameter to be set to **Manual** with **Set-AIPScannerConfiguration**.

Alternatively, you can force the scanner to inspect all files again from the **Azure Information Protection - Nodes** pane in the Azure portal. Wählen Sie in der Liste den Scanner und dann die Option **Rescan all files** (Alle Dateien erneut überprüfen) aus:

![Initiieren eines erneuten Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-rescan-files.png)

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
    
    Verwenden Sie für diese Konfiguration das Cmdlet **Set-AIPScannerRepository**, und legen Sie den Parameter *MatchPolicy* auf **Off** fest. 
    
    Die Inhalte der Dateien werden nicht überprüft, und alle Dateien im Datenrepository werden entsprechend der Standardbezeichnung bezeichnet, die Sie für das Datenrepository (mithilfe des Parameters *SetDefaultLabel*) angeben. Andernfalls wird die Standardbezeichnung verwendet, die als Richtlinieneinstellung für das Konto für die Überprüfung angegeben ist.
    

- Identifizieren aller benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen:
    
    Verwenden Sie für diese Konfiguration das Cmdlet **Set-AIPScannerConfiguration**, und legen Sie den Parameter *DiscoverInformationTypes* auf **All** fest.
    
    Bei der Überprüfung werden alle benutzerdefinierten Bedingungen verwendet, die Sie für Bezeichnungen in der Azure Information Protection-Richtlinie angegeben haben, sowie die Liste der Informationstypen, die zum Angeben von Bezeichnungen in der Azure Information Protection-Richtlinie verfügbar sind.
    
    The following quickstart uses this configuration, although it's for the current version of the scanner: [Quickstart: Find what sensitive information you have](quickstart-findsensitiveinfo.md).

## <a name="optimizing-the-performance-of-the-scanner"></a>Optimieren der Überprüfungsleistung

Nutzen Sie den folgenden Leitfaden, um die Leistung der Überprüfung zu optimieren. However, if your priority is the responsiveness of the scanner computer rather than the scanner performance, you can use an [advanced client setting](./rms-client/client-admin-guide-customizations.md#limit-the-number-of-threads-used-by-the-scanner) to limit the number of threads used by the scanner.

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

- Die Erstellung von regulären Ausdrücken für benutzerdefinierte Bedingungen
    
    Überprüfen Sie Ihre regulären Ausdrücke für einen effizienten Musterabgleich, um eine hohe Arbeitsspeichernutzung und das Risiko von Timeouts (15 Minuten pro Datei) zu vermeiden. Beispiele:
    
    - Vermeiden Sie [gierige Quantifizierer](https://docs.microsoft.com/dotnet/standard/base-types/quantifiers-in-regular-expressions)
    
    - Verwenden Sie Gruppen ohne Erfassung wie `(?:expression)` anstelle von `(expression)`

- Der ausgewählte Protokolliergrad
    
    Sie können für die Überprüfungsberichte zwischen **Debuggen**, **Info**, **Fehler** und **Aus** wählen. **Aus** führt zur besten Leistung; **Debuggen** verlangsamt die Überprüfung erheblich und sollte nur zur Problembehebung verwendet werden. For more information, see the *ReportLevel* parameter for the Set-AIPScannerConfiguration cmdlet by running `Get-Help Set-AIPScannerConfiguration -detailed`.

- Die Dateien selbst:
    
    - With the exception of Excel files, Office files are more quickly scanned than PDF files.
    
    - Ungeschützte Dateien sind schneller zu überprüfen als geschützte Dateien.
    
    - Das Überprüfen großer Dateien beansprucht naturgemäß mehr Zeit als das Überprüfen kleiner Dateien.

- Weiterhin gilt:
    
    - Confirm that the service account that runs the scanner has only the rights documented in the [scanner prerequisites](#prerequisites-for-the-azure-information-protection-scanner) section, and then configure the [advanced client setting](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) to disable the low integrity level for the scanner.
    
    - Die Überprüfung wird schneller ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der eine Standardbezeichnung auf alle Dateien angewendet wird, ohne dass die Dateiinhalte überprüft werden.
    
    - Die Überprüfung wird langsamer ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der alle benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen identifiziert werden.
    
    - You can decrease the scanner timeouts with [advanced client settings](./rms-client/client-admin-guide-customizations.md#change-the-timeout-settings-for-the-scanner) for better scanning rates and lower memory consumption, but with the acknowledgment that some files might be skipped.

## <a name="list-of-cmdlets-for-the-scanner"></a>Auflisten der Cmdlets für die Überprüfung 

Mit anderen Cmdlets für die Überprüfung können Sie das Dienstkonto und die Datenbank für die Überprüfung ändern, die aktuellen Einstellungen für die Überprüfung abrufen und die Überprüfung deinstallieren. Die Überprüfung verwendet die folgenden Cmdlets:

- Add-AIPScannerScannedFileTypes

- Add-AIPScannerRepository

- Get-AIPScannerConfiguration

- Get-AIPScannerRepository

- Get-AIPScannerStatus

- Install-AIPScanner

- Remove-AIPScannerRepository

- Remove-AIPScannerScannedFileTypes

- Set-AIPScanner

- Set-AIPScannerConfiguration

- Set-AIPScannerScannedFileTypes

- Set-AIPScannerRepository

- Start-AIPScan

- Uninstall-AIPScanner

- Update-AIPScanner

> [!NOTE]
> Many of these cmdlets are now deprecated in the current version of the scanner, and the online help for the scanner cmdlets reflects this change. For cmdlet help earlier than version 1.48.204.0 of the scanner, use the built-in `Get-Help <cmdlet name>` command in your PowerShell session.

## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>Ereignisprotokoll-IDs und Beschreibungen für die Überprüfung

Anhand der folgenden Abschnitte können Sie mögliche Ereignis-IDs und Beschreibungen für die Überprüfung ermitteln. Diese Ereignisse werden im Windows-Ereignisprotokoll für **Anwendungen und Dienste**, **Azure Information Protection**, auf dem Server erfasst, auf dem der Überprüfungsdienst ausgeführt wird.

-----

Information **910**

**Scanner cycle started.** (Überprüfungszyklus wurde gestartet)

Dieses Ereignis wird protokolliert, wenn die Überprüfung gestartet wird und beginnt, die Dateien in den Datenrepositorys zu prüfen, die Sie angegeben haben.

----

Information **911**

**Scanner cycle finished.** (Überprüfungszyklus wurde abgeschlossen)

Dieses Ereignis wird protokolliert, wenn der Scanner eine manuelle Überprüfung oder eine Schleife mit kontinuierlichen Ausführungen beendet hat.

Wenn der Scanner so konfiguriert wurde, dass er manuell anstelle von fortlaufend ausgeführt wird, verwenden Sie das **Start-AIPScan**-Cmdlet, um eine erneute Überprüfung durchzuführen. Verwenden Sie zum Ändern des Zeitplans das Cmdlet **Set-AIPScannerConfiguration** und den Parameter *Schedule*.

----

## <a name="next-steps"></a>Nächste Schritte

Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Sie fragen sich womöglich, [was der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung ist](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner).

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).
