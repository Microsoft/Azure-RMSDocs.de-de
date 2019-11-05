---
title: Bereitstellen der Azure Information Protection Scanner-aip
description: Anweisungen zum Installieren, konfigurieren und Ausführen der aktuellen Version des Azure Information Protection Scanners zum ermitteln, klassifizieren und schützen von Dateien in Daten speichern.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 76e074719b031543436cb367ca08e8238c2dbfa7
ms.sourcegitcommit: f5d8cf4440a35afaa1ff1a58b2a022740ed85ffd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/04/2019
ms.locfileid: "73559821"
---
# <a name="deploying-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*
>
> [!NOTE]
> Dieser Artikel ist für die aktuelle Version der allgemeinen Verfügbarkeit des Azure Information Protection Scanners mit dem Azure Information Protection Client (klassisch) und der Vorschauversion des Scanners für die aktuelle allgemein verfügbare Version von Azure Information Protection Unified-Bezeichnungs Client.
> 
> Wenn Sie den Scanner bereits installiert haben und ein Upgrade durchführen möchten, verwenden Sie die folgenden Upgradeanweisungen, und befolgen Sie dann die Anweisungen auf dieser Seite, und lassen Sie den Schritt zum Installieren der Überprüfung aus:
> - Für den klassischen Client: [Aktualisieren der Azure Information Protection Scanner](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner)
> - Für den Unified-Bezeichnungs Client: [Upgrade der Azure Information Protection Scanner](./rms-client/clientv2-admin-guide.md#upgrading-the-azure-information-protection-scanner)
> 
> Wenn Sie über eine Version des Scanners verfügen, die älter als 1.48.204.0 ist und Sie nicht zur Aktualisierung bereit sind, finden Sie weitere Informationen unter Bereitstellen [vorheriger Versionen des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner-previousversions.md).


In diesem Artikel erfahren Sie mehr über die Azure Information Protection-Überprüfung und deren erfolgreiche Installation, Konfiguration und Ausführung.

Diese Überprüfung wird als Dienst unter Windows Server ausgeführt und bietet Ihnen die Möglichkeit, Dateien auf den folgenden Datenspeichern zu suchen, zu klassifizieren und zu schützen:

- Lokale Ordner auf dem Windows Server-Computer, auf dem die Überprüfung ausgeführt wird

- UNC-Pfade zu Netzwerkfreigaben mit dem Server Message Block (SMB)-Protokoll.

- Dokument Bibliotheken und Ordner für SharePoint Server 2019 über SharePoint Server 2013. SharePoint 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

Verwenden Sie zum Überprüfen und Bezeichnen von Dateien auf Cloudrepositorys [Cloud App Security](https://docs.microsoft.com/cloud-app-security/) anstelle des Scanners.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Übersicht über die Azure Information Protection-Überprüfung

Wenn Sie Bezeichnungen konfiguriert haben, die die automatische Klassifizierung anwenden, können von diesem Scanner ermittelte Dateien als bezeichnet werden. Bezeichnungen wenden Klassifizierungen sowie optional Schutz an, der auch entfernt werden kann:

![Übersicht über die Architektur der Azure Information Protection-Überprüfung](./media/infoprotect-scanner.png)

Die Überprüfung kann jede Datei überprüfen, die von Windows indiziert werden kann. Dazu verwendet sie IFilters, die auf dem Computer installiert sind. Um zu bestimmen, ob die Dateien Bezeichnungen benötigen, verwendet die Überprüfung die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) oder Regex-Muster von Office 365. Da bei der Überprüfung der Azure Information Protection Client (der klassische Client oder der Unified-Bezeichnungs Client) verwendet wird, kann der Scanner dieselben Dateitypen klassifizieren und schützen:

- Klassischer Client: [vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md)

- Einheitlicher Bezeichnungs Client: [vom Azure Information Protection Unified-Bezeichnungs Client unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md)

Sie können die Überprüfung im Suchmodus ausführen. In diesem Modus überprüfen Sie anhand der Berichte, was geschähe, wenn die Dateien bezeichnet würden. Alternativ können Sie die Bezeichnungen mit der Überprüfung automatisch anwenden. Sie können die Überprüfung auch zum Ermitteln von Dateien mit vertraulichen Informationstypen ausführen, ohne Bezeichnungen für Bedingungen zu konfigurieren, die die automatische Klassifizierung anwenden.

Beachten Sie, dass die Überprüfung nicht in Echtzeit sucht und bezeichnet. Sie durchforstet systematisch Dateien auf Datenspeichern, die Sie angeben, und Sie können konfigurieren, ob dieser Zyklus einmal oder mehrmals ausgeführt wird.

Sie können angeben, welche Dateitypen überprüft oder vom Scanvorgang ausgeschlossen werden sollen, indem Sie im Rahmen der Scannerkonfiguration eine Dateitypenliste definieren.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Voraussetzungen für die Azure Information Protection-Überprüfung
Stellen Sie vor der Installation der Azure Information Protection-Überprüfung sicher, dass folgende Voraussetzungen erfüllt sind.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Windows Server-Computer zum Ausführen des Überprüfungsdiensts:<br /><br />- Prozessoren mit 4 Kernen<br /><br />– 8 GB RAM<br /><br />- 10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien|Windows Server 2019, Windows Server 2016 oder Windows Server 2012 R2. <br /><br />Hinweis: Sie können zu Test- oder Auswertungszwecken ein Windows-Clientbetriebssystem in einer Testumgebung verwenden, das [vom Azure Information Protection-Client unterstützt](requirements.md#client-devices) wird.<br /><br />Dieser Computer kann ein physischer oder ein virtueller Computer mit einer schnellen und zuverlässigen Netzwerkverbindung zu den Datenspeichern sein, die überprüft werden sollen.<br /><br /> Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen. <br /><br /> Wenn die Internetverbindung aufgrund ihrer Organisations Richtlinien nicht möglich ist, finden Sie weitere Informationen im Abschnitt bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations) . Stellen Sie andernfalls sicher, dass dieser Computer über eine Internetverbindung verfügt, die die folgenden URLs über HTTPS (Port 443) zulässt:<br /> \*.aadrm.com <br /> \*.azurerms.com<br /> \*.informationprotection.azure.com <br /> informationprotection.hosting.portal.azure.net <br /> \*.aria.microsoft.com <br /> \*.Protection.Outlook.com (Scanner nur vom Unified-Bezeichnungs Client)|
|Dienstkonto zum Ausführen der Überprüfung|Über das Ausführen des Überprüfungsdiensts auf dem Windows-Servercomputer hinaus wird dieses Windows-Konto auch bei Azure AD authentifiziert und lädt die Azure Information Protection-Richtlinie herunter. Dieses Konto muss ein Active Directory-Konto sein und mit Azure AD synchronisiert werden. Wenn Sie dieses Konto aufgrund Ihrer Organisationsrichtlinien nicht synchronisieren können, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Für dieses Dienstkonto gelten die folgenden Anforderungen:<br /><br />- **Lokale Anmeldung** für die Zuweisung von Benutzerrechten. Diese Berechtigung ist für die Installation und Konfiguration der Überprüfung erforderlich, aber nicht für den Vorgang selbst. Sie müssen dem Dienstkonto diese Berechtigung gewähren und können sie wieder entfernen, nachdem Sie überprüft haben, dass die Überprüfung Dateien suchen, klassifizieren und schützen kann. Wenn die Gewährung dieser Berechtigung selbst für einen kurzen Zeitraum aufgrund Ihrer Organisationsrichtlinien nicht möglich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />- **Anmeldung als Dienst** für die Zuweisung von Benutzerrechten. Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich. <br /><br />– Berechtigungen für Datenrepositorys: Sie müssen **Lese-** und **Schreibberechtigungen** für das Überprüfen, Klassifizieren und Schützen der Dateien erteilen, damit die Dateien die Bedingungen in der Azure Information Protection-Richtlinie erfüllen. Um die Überprüfung nur im Suchmodus auszuführen, genügt eine **Leseberechtigung**.<br /><br />-Für Bezeichnungen, die den Schutz erneut schützen oder entfernen: um sicherzustellen, dass die Überprüfung stets Zugriff auf geschützte Dateien hat, machen Sie dieses Konto als [Administrator für Azure Information Protection](configure-super-users.md) , und stellen Sie sicher, dass die Administrator Funktion aktiviert ist. Wenn Sie darüber hinaus [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) für eine stufenweise Bereitstellung implementiert haben, stellen Sie sicher, dass dieses Konto in den von Ihnen konfigurierten Onboarding-Steuerelementen enthalten ist.|
|SQL-Server, auf dem die Konfiguration der Überprüfung gespeichert wird:<br /><br />- Lokale oder Remoteinstanz<br /><br />– Sysadmin-Rolle zum Installieren der Überprüfung|SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express<br /><br />Vom Azure Information Protection-Scanner werden beim Angeben eines benutzerdefinierten Profilnamens für den Scanner mehrere Konfigurationsdatenbanken auf einer SQL Server-Instanz unterstützt. Wenn Sie die Vorschauversion der Überprüfung des Unified-Bezeichnungs Clients verwenden, können mehrere Scanner dieselbe Konfigurations Datenbank gemeinsam verwenden.<br /><br />Wenn Sie den Scanner installieren und Ihr Konto über die Sysadmin-Rolle verfügt, wird während des Installationsprozesses automatisch die Konfigurationsdatenbank des Scanners erstellt und dem Dienstkonto, das den Scanner ausführt, die erforderliche Db_owner-Rolle gewährt. Wenn die Sysadmin-Rolle nicht gewährt wird oder aufgrund der Richtlinien Ihrer Organisation die manuelle Erstellung und Konfiguration von Datenbanken erforderlich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br /> Informationen zur Kapazitäts Orientierung finden Sie unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).|
|Eine der folgenden Azure Information Protection Clients ist auf dem Windows Server-Computer installiert. <br /><br /> -Klassischer Client <br /><br /> -Unified-Bezeichnungs Client ([aktuelle Version der allgemeinen Verfügbarkeit](./rms-client/unifiedlabelingclient-version-release-history.md#version-25330)) |Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.<br /><br />Installations-und Upgradeanweisungen: <br /> klassischer - -[Client](./rms-client/client-admin-guide.md)<br /> - [Unified](./rms-client/clientv2-admin-guide.md#installing-the-azure-information-protection-scanner) -Bezeichnungs Client |
|Konfigurierte Bezeichnungen, die automatische Klassifizierung und optional Schutz anwenden|Anweisungen für den klassischen Client zum Konfigurieren einer Bezeichnung für Bedingungen und zum Anwenden des Schutzes:<br /> - [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)<br /> - [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md) <br /><br />Tipp: Sie können die Anweisungen aus dem [Tutorial](infoprotect-quick-start-tutorial.md) zum Testen des Scanners mit einer Bezeichnung verwenden, die in einem vorbereiteten Word-Dokument nach Kreditkartennummern sucht. Sie müssen jedoch die Bezeichnungskonfiguration ändern, sodass die Option **Wählen Sie aus, wie diese Bezeichnung angewendet wird** auf **Automatisch** und nicht auf **als Empfehlung** festgelegt wird. Entfernen Sie anschließend die Bezeichnung vom Dokument (sofern angewendet), und kopieren Sie die Datei in ein Datenrepository für den Scanner. Bei einem schnellen Test kann dies ein lokaler Ordner auf dem Computer mit dem Scanner sein.<br /><br /> Anweisungen für den Unified Label-Client zum Konfigurieren einer Bezeichnung für die automatische Kennzeichnung und zum Anwenden des Schutzes:<br /> - [eine Vertraulichkeits Bezeichnung automatisch auf Inhalt anwenden](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)<br /> - [beschränken Sie den Zugriff auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) .<br /><br /> Zwar können Sie die Überprüfung auch dann ausführen, wenn Sie über keine konfigurierten Bezeichnungen verfügen, die die automatische Klassifizierung anwenden, dieses Szenario wird in der vorliegenden Anleitung jedoch nicht behandelt. [Weitere Informationen](#using-the-scanner-with-alternative-configurations)|
|Für das Scannen von SharePoint-Dokument Bibliotheken und-Ordnern:<br /><br />-SharePoint 2019<br /><br />– SharePoint 2016<br /><br />– SharePoint 2013<br /><br />– SharePoint 2010|Andere Versionen von SharePoint werden für die Überprüfung nicht unterstützt.<br /><br />Wenn Sie die [Versions](https://docs.microsoft.com/sharepoint/governance/versioning-content-approval-and-check-out-planning)Verwaltung verwenden, wird die zuletzt veröffentlichte Version vom Scanner überprüft und beschriftet. Wenn die Überprüfung eine Datei und eine [Genehmigung von Inhalten](https://docs.microsoft.com/sharepoint/governance/versioning-content-approval-and-check-out-planning#plan-content-approval) erfordert, muss die bezeichnete Datei als verfügbar für Benutzer verfügbar sein. <br /><br />Überprüfen Sie für große SharePoint-Farmen, ob Sie den Schwellwert der Listenansicht (standardmäßig 5.000) erhöhen müssen, damit der Scanner auf alle Dateien zugreifen kann. Weitere Informationen finden Sie in der folgenden SharePoint-Dokumentation: [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server) .|
|Für zu scannende Office-Dokumente:<br /><br />-97-2003-Dateiformate und die offene Office-XML-Formate für Word, Excel und PowerPoint|Weitere Informationen zu den Dateitypen, die von der Überprüfung für diese Dateiformate unterstützt werden, finden Sie in den folgenden Informationen: <br />-Klassischer Client: [vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md)<br />-Unified-Bezeichnungs Client: [vom Azure Information Protection Unified Bezeichnung-Client unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md)|
|Für lange Pfade:<br /><br />– höchstens 260 Zeichen, es sei denn, der Scanner ist unter Windows 2016 installiert und der Computer ist für die Unterstützung von langen Pfaden konfiguriert|Windows 10 und Windows Server 2016 unterstützen Pfadlängen von mehr als 260 Zeichen mit der folgenden [Gruppenrichtlinien Einstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/): **Richtlinie für lokale Computer** > **Computer Konfiguration** > **Administrative Vorlagen**@no_ _T-6**alle Einstellungen** >  für**Win32 Long-Pfade aktivieren**<br /><br /> Weitere Informationen zur Unterstützung von langen Dateipfaden finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Wenn Sie nicht alle Anforderungen in der Tabelle erfüllen können, weil Sie von ihren Organisations Richtlinien nicht zugelassen werden, lesen Sie den Abschnitt [Alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations) .

Wenn Sie den Scanner in der Produktionsumgebung bereitstellen oder die Leistung für mehrere Scanner testen, finden Sie im nächsten Abschnitt eine Anleitung zur Kapazitätsplanung für SQL Server.

Wenn Sie jedoch bereit sind, mit der Bereitstellung der Überprüfung zu beginnen, wechseln Sie direkt zu [Konfigurieren des Abschnitts Scanner](#configure-the-scanner-in-the-azure-portal).

### <a name="storage-requirements-and-capacity-planning-for-sql-server"></a>Speicheranforderungen und Kapazitätsplanung für SQL Server

Der erforderliche Speicherplatz für die Konfigurations Datenbank des Scanners und die Angabe des Computers, auf dem SQL Server ausgeführt wird, kann je nach Umgebung variieren. Daher empfehlen wir Ihnen, ihre eigenen Tests durchzuführen. Sie können jedoch die folgende Anleitung als Ausgangspunkt verwenden.

Weitere Informationen finden Sie im Abschnitt [Optimieren der Leistung der über](#optimizing-the-performance-of-the-scanner) Prüfung.

##### <a name="scanner-from-the-classic-client"></a>Überprüfung des klassischen Clients:

- Datenträger **Größe**: die Größe der Konfigurations Datenbank variiert für jede Bereitstellung, aber es wird empfohlen, dass Sie 500 MB für alle 1 Million-Dateien zuordnen, die Sie überprüfen möchten.

- **Für jeden Scanner**: vier Kern Prozessoren; 8 GB RAM empfohlen (mindestens 4 GB).

##### <a name="scanner-from-the-unified-labeling-client"></a>Überprüfung des Unified-Bezeichnungs Clients:

- Datenträger **Größe**: Obwohl die Größe der Überprüfungs Konfigurationsdatenbank für jede Bereitstellung variiert, können Sie die folgende Gleichung als Leitfaden verwenden: `100 KB + <file count> *(1000 + 4*<average file name length>)`. 
    
    Um z. b. 1 Million Dateien mit einer durchschnittlichen Dateinamen Länge von 250 Bytes zu scannen, müssen Sie 2 GB Speicherplatz zuweisen.

- **Für mehrere Scanner, bis zu 12**: 4 Kern Prozessoren; 8 GB RAM empfohlen (mindestens 4 GB).

- **Für mehrere Scanner mit mehr als 12 (max. 40)** : 8 Kernprozessen; 16 GB RAM empfohlen (mindestens 8 GB).

### <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die in der Tabelle aufgeführten Voraussetzungen sind die Standardanforderungen für die Überprüfung und werden empfohlen, da sie die einfachste Konfiguration für die Bereitstellung der Überprüfung sind. Sie sollten für die erste Testphase geeignet sein, damit Sie die Funktionen der Überprüfung überprüfen können. In einer Produktumgebung können aufgrund der Richtlinien Ihrer Organisation diese Standardanforderungen jedoch aufgrund einer oder mehrerer der folgenden Einschränkungen nicht zulässig sein:

- Server sind keine Internet Konnektivität zulässig.

- Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

- Die Berechtigung zur **lokalen Anmeldung** kann nicht für Dienstkonten gewährt werden.

- Dienst Konten können nicht mit Azure Active Directory synchronisiert werden, aber Server haben eine Internetverbindung.

Bei der Überprüfung können diese Einschränkungen zwar berücksichtigt werden, es ist jedoch eine zusätzliche Konfiguration erforderlich.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Einschränkung: der Überprüfungs Server kann keine Internetverbindung haben.

Befolgen Sie die Anweisungen in den Administrator Handbüchern, um einen getrennten Computer zu unterstützen:

- Für den klassischen Client: [Unterstützung für nicht verbundene Computer](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers)
    
    In dieser Konfiguration kann die Überprüfung des klassischen Clients keinen Schutz anwenden, den Schutz entfernen oder geschützte Dateien mit dem cloudbasierten Schlüssel Ihrer Organisation überprüfen. Stattdessen ist der Scanner auf die Verwendung von Bezeichnungen beschränkt, die nur die Klassifizierung anwenden, oder den Schutz anwenden, der [Hyok](configure-adrms-restrictions.md) verwendet.

- Für den Unified-Bezeichnungs Client: [Unterstützung für nicht verbundene Computer](./rms-client/clientv2-admin-guide-customizations.md#support-for-disconnected-computers)
    
    In dieser Konfiguration kann die Überprüfung des Unified-Bezeichnungs Clients Schutz anwenden, Schutz entfernen und geschützte Dateien überprüfen, indem der *delegateduser* -Parameter mit dem Cmdlet " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " verwendet wird.

Führen Sie dann folgende Schritte aus:

1. Konfigurieren Sie den Scanner im Azure-Portal, indem Sie ein Scannerprofil erstellen. Unterstützung zu diesem Schritt finden Sie im Abschnitt [Konfigurieren des Scanners im Azure-Portal](#configure-the-scanner-in-the-azure-portal).

2. Exportieren Sie Ihr Scanner-Profil aus dem Bereich **Azure Information Protection profile** , indem Sie die **Export** Option verwenden.

3. Führen Sie schließlich das Cmdlet [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) in einer PowerShell-Sitzung aus, und geben Sie die Datei an, in der die exportierten Einstellungen enthalten sind.

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Wenn Ihnen die Sysadmin-Rolle zur vorübergehenden Installation der Überprüfung zugewiesen werden kann, können Sie diese Rolle nach der Installation der Überprüfung entfernen. Wenn Sie diese Konfiguration verwenden, wird die Datenbank automatisch für Sie erstellt, und das Dienstkonto für die Überprüfung erhält automatisch die erforderlichen Berechtigungen. Für das Benutzerkonto, mit dem der Scanner konfiguriert wird, wird jedoch die db_owner-Rolle für die Konfigurationsdatenbank des Scanners benötigt, und Sie müssen diese Rolle dem Benutzerkonto manuell zuweisen.

Wenn Sie die sysadmin-Rolle nicht auch vorübergehend erhalten können, müssen Sie einen Benutzer mit sysadmin-Berechtigung bitten, vor der Installation des Scanners manuell eine Datenbank zu erstellen. Für diese Konfiguration müssen die folgenden Rollen zugewiesen werden:
    
|Konto|Rolle auf Datenbankebene|
|--------------------------------|---------------------|
|Dienstkonto für die Überprüfung|db_owner|
|Benutzerkonto für die Installation der Überprüfung|db_owner|
|Benutzerkonto für die Konfiguration der Überprüfung |db_owner|

In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie jedoch unterschiedliche Konten verwenden, benötigen beide die db_owner-Rolle für die Konfigurationsdatenbank des Scanners.

- Wenn Sie keinen eigenen Profilnamen für den Scanner angeben (nur klassischer Client), wird die Konfigurations Datenbank mit dem Namen **AIPScanner_\<computer_name >** benannt. 

- Wenn Sie Ihren eigenen Profilnamen angeben, wird die Konfigurations Datenbank mit dem Namen **AIPScanner_\<profile_name >** (klassischer Client) oder **AIPScannerUL_\<profile_name >** (einheitlicher Bezeichnungs Client) benannt.

Um einen Benutzer zu erstellen und db_owner-Rechte für diese Datenbank zu erteilen, bitten Sie den sysadmin, das folgende SQL-Skript zweimal auszuführen. Beim ersten Mal für das Dienst Konto, mit dem die Überprüfung ausgeführt wird, und das zweite Mal zum Installieren und Verwalten des Scanners. Vor dem Ausführen des Skripts:
1. Ersetzen Sie Domäne *\ Benutzer* durch den Domänen Namen und den Benutzerkonto Namen des Dienst Kontos bzw. des Benutzerkontos.
2. Ersetzen Sie *dbname* durch den Namen der Überprüfungs Konfigurationsdatenbank.

SQL-Skript:

    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    USE DBName IF NOT EXISTS (select * from sys.database_principals where sid = SUSER_SID('domain\user')) BEGIN declare @X nvarchar(500) Set @X = 'CREATE USER ' + quotename('domain\user') + ' FROM LOGIN ' + quotename('domain\user'); exec sp_addrolemember 'db_owner', 'domain\user' exec(@X) END

Weiterhin gilt:

- Sie müssen ein lokaler Administrator auf dem Server sein, auf dem die Überprüfung ausgeführt wird.
- Das Dienst Konto, unter dem der Scanner ausgeführt wird, muss über Vollzugriff auf die folgenden Registrierungsschlüssel verfügen:
    
    - HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\Server
    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server

Wenn nach dem Konfigurieren dieser Berechtigungen ein Fehler angezeigt wird, wenn Sie den Scanner installieren, kann der Fehler ignoriert werden, und Sie können den Überprüfungs Dienst manuell starten.


#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Einschränkung: Die Berechtigung zur **lokalen Anmeldung** kann nicht für das Dienstkonto gewährt werden.

Wenn Ihre Organisations Richtlinien das Recht " **Lokal anmelden** " für Dienst Konten nicht zulassen, aber das Recht " **Anmelden als Batch Auftrag** " zulassen, verwenden Sie die folgenden Anweisungen:

- Für den klassischen Client: Weitere Informationen finden Sie unter [angeben und Verwenden des Token-Parameters für "Set-aipauthentication" im](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) Administrator Handbuch dieses Clients.

- Für den Unified Label-Client: Verwenden Sie den *onbehalfof* -Parameter mit "Set-aipauthentication", wie unter [How to Label files Non-interaktiv for Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) in the Admin Guide dieses Clients beschrieben.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Für das Überprüfungsdienstkonto können Sie ein lokales Windows-Konto oder ein Active Directory-Konto verwenden.

- Verwenden Sie für das Azure Active Directory-Konto die folgenden Anweisungen:
    - Für den klassischen Client: Weitere Informationen finden Sie unter [angeben und Verwenden des Token-Parameters für "Set-aipauthentication" im](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) Administrator Handbuch dieses Clients.
    - Für den Unified Label-Client: Geben Sie Ihr lokales Konto für den *onbehalfof* -Parameter mit "Set-aipauthentication" an, wie unter [How to Label files Non-interaktiv for Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administrator Handbuch dieses Clients beschrieben.


## <a name="configure-the-scanner-in-the-azure-portal"></a>Konfigurieren des Scanners im Azure-Portal

Bevor Sie die Überprüfung installieren oder von einer älteren Version der Überprüfung mit allgemeiner Verfügbarkeit aktualisieren, erstellen Sie ein Profil für den Scanner in der Azure-Portal. Konfigurieren Sie das Profil für Scannereinstellungen und die Datenrepositorys, die überprüft werden sollen.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie dann zum Bereich **Azure Information Protection** . 
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.
    
2. Suchen Sie die **Scanner**-Menüoptionen, und wählen Sie **Profile** aus.

3. Wählen Sie im Bereich **Azure Information Protection profile** die Option **Hinzufügen**aus:
    
    ![Hinzufügen eines Profils für den Azure Information Protection-Scanner](./media/scanner-add-profile.png)

4. Geben Sie im Bereich **Neues Profil hinzufügen** einen Namen für die Überprüfung an, mit der die zu überprüfenden Konfigurationseinstellungen und Daten Depots identifiziert werden. Sie können beispielsweise **Europa** angeben, um den geografischen Standort der Datenrepositorys anzugeben, für die Ihr Scanner zuständig ist. Diesen Profilnamen müssen Sie angeben, wenn Sie den Scanner später installieren oder upgraden.
    
    Optional können Sie eine Beschreibung für administrative Zwecke eingeben, damit Sie den Profilnamen des Scanners leichter erkennen.

5. Konfigurieren Sie für diese Erstkonfiguration die folgenden Einstellungen, und wählen Sie dann **Speichern** aus, aber schließen Sie den Bereich nicht:
    
    Für den Abschnitt " **Profileinstellungen** ":
    - **Zeitplan**: behalten Sie den Standardwert **manuell** bei.
    - **Zu ermittelnde Informationstypen**: **nur in Richtlinie** ändern
    - **Repository konfigurieren**: Konfigurieren Sie zu diesem Zeitpunkt nicht, weil das Profil zuerst gespeichert werden muss.
    
    Für den Abschnitt **Richtlinien** Erzwingung:
    - **Erzwingen**: SELECT **Off**
    - Bezeichnungs **Dateien basierend auf dem Inhalt**: behalten Sie die Standardeinstellung **bei** .
    - **Standard Bezeichnung**: Standardwert der Standard **Richtlinie für Richtlinie** beibehalten
    - **Dateien**neu bezeichnen: Standardwert " **aus** " beibehalten
    
    Im Abschnitt **Konfigurieren von Datei Einstellungen** :
    - **"Datum geändert", "zuletzt geändert" und "geändert von**" beibehalten: behalten Sie die Standardeinstellung **bei** .
    - **Zu überprüfende Dateitypen**: Standard Dateitypen für **Ausschluss** beibehalten
    - **Standard Besitzer**: behalten Sie die Standardeinstellung **Scanner-Konto** bei.

6. Nachdem Sie das Profil erstellt und gespeichert haben, können Sie zur Option **Repositorys konfigurieren** zurückkehren, um die Datenspeicher anzugeben, die überprüft werden sollen. Sie können lokale Ordner, UNC-Pfade und SharePoint-Server-URLs für lokale SharePoint-Dokument Bibliotheken und-Ordner angeben. 
    
    SharePoint Server 2019, SharePoint Server 2016 und SharePoint Server 2013 werden für SharePoint unterstützt. Ferner wird SharePoint Server 2010 unterstützt, wenn Sie über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.
    
    Wenn Sie den ersten Datenspeicher hinzufügen möchten, wählen Sie im Bereich **Neues Profil hinzufügen** die Option **Repository konfigurieren** aus, um den Bereich **Depots** zu öffnen:
    
    ![Konfigurieren von Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repositories-bar.png)

7. Wählen Sie im Bereich **Depots** die Option **Hinzufügen**aus:
    
    ![Hinzufügen eines Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repository-add.png)

8. Geben Sie im Bereich **Repository** den Pfad für das Datenrepository an. 
    
    Platzhalter und WebDav-Speicherorte werden nicht unterstützt.
    
    Beispiele:
    
    - Für einen lokalen Pfad: `C:\Folder`
    
    - Für eine Netzwerkfreigabe: `C:\Folder\Filename`
    
    - Für einen UNC-Pfad: `\\Server\Folder`
    
    - Für eine SharePoint-Bibliothek: `http://sharepoint.contoso.com/Shared%20Documents/Folder`
    
    > [!TIP]
    > Beachten Sie beim Hinzufügen eines SharePoint-Pfads für „Freigegebene Dokumente“ Folgendes:
    >
     >- Geben Sie **Freigegebene Dokumente** im Pfad an, wenn alle Dokumente und Ordner in „Freigegebene Dokumente“ überprüft werden sollen. Beispiel: `http://sp2013/Shared Documents`
     >
     >- Geben Sie **Dokumente** im Pfad an, wenn alle Dokumente und Ordner in einem Unterordner von „Freigegebene Dokumente“ überprüft werden sollen. Beispiel: `http://sp2013/Documents/Sales Reports`
    
    Für die restlichen Einstellungen in diesem Bereich sollten Sie diese nicht für diese anfängliche Konfiguration ändern, sondern als **Profil Standard**beibehalten. So werden die Einstellungen vom Datenrepository aus dem Scannerprofil übernommen. 
    
    Wählen Sie **Speichern** aus.

9. Wiederholen Sie die Schritte 7 und 8, wenn Sie ein weiteres Datenrepository hinzufügen möchten.

10. Sie können jetzt den Bereich " **Repository** " und ihren Profilbereich schließen. Im Bereich **Azure Information Protection profile** sehen Sie, dass Ihr Profilname angezeigt wird, und die Spalte **Schedule** zeigt **manuell** und die Spalte **erzwingen** ist leer.

Nun können Sie den Scanner mit dem Scannerprofil installieren, das Sie eben erstellt haben.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Melden Sie sich bei dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt werden soll. Verwenden Sie ein Konto mit lokalen Administratorrechten und den Berechtigungen zum Schreiben in die SQL Server-Masterdatenbank.

2. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

3. Führen Sie das Cmdlet [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) aus, und geben Sie dabei die SQL Server-Instanz an, auf der eine Datenbank für den Azure Information Protection-Scanner erstellt werden soll, und den Profilnamen des Scanners, den Sie im vorherigen Abschnitt angegeben haben: 
    
    ```
    Install-AIPScanner -SqlServerInstance <name> -Profile <profile name>
    ```
    
    Beispiele, in denen der Profilname **Europa** verwendet wird:
    
    - Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile Europe`
    
    - Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile Europe`
    
    - Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile Europe`
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Überprüfungsdienstkonto (\<Domäne/Benutzername>) und das Kennwort ein.

4. Stellen Sie unter **Verwaltung** > **Dienste** sicher, dass der Dienst jetzt installiert ist. 
    
    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nachdem Sie den Scanner installiert haben, müssen Sie ein Azure AD-Token abrufen, damit das Dienstkonto des Scanners authentifiziert und der Scanner unbeaufsichtigt ausgeführt werden kann. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Abrufen eines Azure AD-Tokens für die Überprüfung

Das Azure AD Token ermöglicht es dem Scanner, sich beim Azure Information Protection-Dienst zu authentifizieren.

1. Kehren Sie zum Azure-Portal zurück, um zwei Azure AD Anwendungen (nur eine Azure AD Anwendung für die Überprüfung des Unified-Bezeichnungs Clients) zu erstellen, die erforderlich sind, um ein Zugriffs Token für die Authentifizierung anzugeben. Mit diesem Token kann der Scanner nicht interaktiv ausgeführt werden.
    
    Befolgen Sie die Anweisungen in den Administrator Handbüchern für die relevanten Clients, um diese Anwendungen zu erstellen:
    
    - Für den klassischen Client: [wie werden Dateien nicht interaktiv für Azure Information Protection beschriftet](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection)
    
    - Für den Unified Label-Client: Gewusst [wie: nicht interaktiv Bezeichnungs Dateien für Azure Information Protection](./rms-client/clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection)

2. Gehen Sie auf dem Windows Server-Computer folgendermaßen vor, wenn dem Überprüfungsdienstkonto für die Installation das Recht zur **lokalen Anmeldung** erteilt wurde: Melden Sie sich mit diesem Konto an, und starten Sie eine PowerShell-Sitzung. Führen Sie [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) aus, und geben Sie die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:
    
    **Für den klassischen Client:**
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```

    Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort für Ihr Azure AD-Dienstkonto an, und klicken Sie dann auf **Akzeptieren**.
    
    Wenn Ihr Überprüfungs Dienst Konto nicht über die Berechtigung **Lokal anmelden** für die Installation verfügen kann, finden Sie im Administrator Handbuch dieses Clients unter [angeben und Verwenden des Token-Parameters für "Set-aipauthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) " Weitere Informationen.
    
    **Für den Unified-Bezeichnungs Client:**
    
    ```
    Set-AIPAuthentication -AppId <ID of the registered app> -AppSecret <client secret sting> -TenantId <your tenant ID> -DelegatedUser <Azure AD account>
    ```
    
    Wenn Ihrem Überprüfungs Dienst Konto die Berechtigung " **Lokal anmelden** " für die Installation nicht gewährt werden kann, verwenden Sie den Parameter " *onbehalfof* " mit "Set-aipauthentication", wie unter Gewusst [wie: nicht interaktiv für Azure-Informationen beschrieben. Schutz](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) vor dem Administrator Handbuch dieses Clients.

Der Scanner verfügt jetzt über ein Token zum Authentifizieren bei Azure AD, das ein Jahr, zwei Jahre oder nie abläuft, gemäß ihrer Konfiguration der **Web-App/API** (klassischer Client) oder des geheimen Client Schlüssels (einheitlicher Bezeichnungs Client) in Azure AD. Wenn das Token abgelaufen ist, müssen Sie die Schritte 1 und 2 wiederholen.

Nun können Sie den ersten Scanvorgang im Ermittlungsmodus ausführen.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Ausführen eines Ermittlungszyklus und Anzeigen von Berichten für die Überprüfung

1. Wählen Sie im Azure-Portal im Bereich **Azure Information Protection profile** das Profil Ihres Scanners aus, und klicken Sie dann auf die Option **jetzt** überprüfen:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)
    
    Führen Sie alternativ in der PowerShell-Sitzung den folgenden Befehl aus:
    
        Start-AIPScan

2. Warten Sie, bis die Überprüfung den Zyklus abgeschlossen hat. Wenn der Scanner alle Dateien in den von Ihnen angegebenen Datenspeichern durchforstet hat, wird der Scanner beendet, obwohl der Scannerdienst weiterhin ausgeführt wird.
    
    - Verwenden Sie im Bereich **Azure Information Protection profile** die Option **Aktualisieren** , und warten Sie, bis die Werte für die Spalte **Letzte Überprüfungs Ergebnisse** und die Spalte **Letzter Scan (Endzeit)** angezeigt werden.
    
    - Mit PowerShell können Sie `Get-AIPScannerStatus` ausführen, um die Statusänderung zu überwachen.
    
    - Nur Überprüfung des klassischen Clients: Überprüfen Sie das lokale Ereignisprotokoll für Windows **-Anwendungen und-Dienste** **Azure Information Protection**. Dieses Protokoll gibt außerdem an, wann die Überprüfung abgeschlossen wurde, und zeigt eine Zusammenfassung der Ergebnisse an. Suchen Sie einfach nach der Ereignis-ID **911**.

3. Lesen Sie die Berichte, die unter %*localappdata*%\Microsoft\MSIP\Scanner\Reports gespeichert sind. Die TXT-Zusammenfassungsdateien enthalten die zum Überprüfen benötigte Zeit, die Anzahl der überprüften Dateien sowie die Anzahl der Dateien mit übereinstimmenden Informationstypen. Die CSV-Dateien enthalten mehr Details zu den einzelnen Dateien. In diesem Ordner werden für jeden Scanzyklus bis zu 60 Berichte gespeichert, die bis auf den letzten alle komprimiert werden, um die Speicherplatzbelegung zu minimieren.
    
    > [!NOTE]
    > Mit dem Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) können Sie mithilfe des Parameters *ReportLevel* den Protokolliergrad ändern, den Speicherort oder Namen des Berichtsordners jedoch nicht. Wenn Sie die Berichte in einem anderen Volume oder in einer anderen Partition speichern möchten, sollten Sie eine Verzeichnisverbindung verwenden.
    >
    > Verwenden Sie hierzu beispielsweise den Befehl [Mklink](/windows-server/administration/windows-commands/mklink): `mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`
    
    Aufgrund der Einstellung **Nur Richtlinie** für **Zu ermittelnde Infotypen** sind nur die Dateien in den ausführlichen Berichten enthalten, die den Bedingungen entsprechen, die Sie für die automatische Klassifizierung konfiguriert haben. Wenn keine der angewendeten Bezeichnungen angezeigt werden, überprüfen Sie, ob die Bezeichnungskonfiguration anstelle der empfohlenen Klassifizierung die automatische Klassifizierung enthält.
    
    > [!TIP]
    > Überprüfungen senden diese Informationen alle fünf Minuten an Azure Information Protection, so dass Sie die Ergebnisse nahezu in Echtzeit im Azure-Portal anzeigen können. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md). 
        
    Wenn die Ergebnisse nicht erwartungsgemäß sind, müssen Sie möglicherweise die Bedingungen, die Sie für ihre Bezeichnungen angegeben haben, neu konfigurieren. Wenn dies der Fall ist, wiederholen Sie die Schritte 1 bis 3, bis Sie die Konfiguration ändern können, um die Klassifizierung und optional den Schutz anzuwenden. 

Das Azure-Portal zeigt nur Informationen zur letzten Überprüfung an. Wenn Sie die Ergebnisse vorheriger Überprüfungen anzeigen müssen, sehen Sie sich die Berichte an, die auf dem Überprüfungscomputer im Ordner „%*localappdata*%\Microsoft\MSIP\Scanner\Reports“ gespeichert sind.

Wenn Sie für das automatische Bezeichnen der Dateien, die die Überprüfung sucht, bereit sind, fahren Sie mit dem nächsten Abschnitt fort. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz

Wenn Sie diese Anweisungen befolgen, wird der Scanner einmal und nur im Modus für die Berichterstellung ausgeführt. Wenn Sie diese Einstellungen ändern möchten, bearbeiten Sie das Scannerprofil:

1. Wählen Sie im Bereich **Azure Information Protection profile** das Überprüfungs Profil aus, um es zu bearbeiten.

2. Ändern Sie im Bereich \<**Profilname**> die folgenden beiden Einstellungen, und wählen Sie dann **Speichern**aus:
    
   - Im Abschnitt " **Profileinstellungen** ": Ändern des **Zeitplans** in " **immer** "
   - Aus dem Abschnitt zur **Richtlinien** Erzwingung: Ändern von **erzwingen** **in ein**
    
     Es gibt andere Konfigurationseinstellungen, die Sie ggf. ändern sollten, z. B. ob Dateiattribute geändert werden und Dateien vom Scanner neu bezeichnet werden können. Weitere Informationen zu den einzelnen Konfigurationseinstellungen finden Sie in der Popuphilfe mit Informationen.

3. Notieren Sie sich die aktuelle Uhrzeit, und starten Sie die Überprüfung erneut über den Bereich **Azure Information Protection profile** :
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)
    
    Alternativ können Sie den folgenden Befehl in der PowerShell-Sitzung ausführen:
    
        Start-AIPScan

4. Nur **911** auf dem klassischen Client überprüfen: Überwachen Sie das Ereignisprotokoll mit einem Zeitstempel, der später als beim Start der Überprüfung im vorherigen Schritt folgt.
    
    Überprüfen Sie die Berichte, um festzustellen, welche Dateien eine Bezeichnung erhalten haben, welche Klassifizierung für die einzelnen Dateien vergeben wurde und ob Schutz angewendet wurde. Oder verwenden Sie das Azure-Portal, um diese Informationen einfacher anzuzeigen.

Da der Zeitplan als fortlaufend konfiguriert wurde, startet der Scanner automatisch einen neuen Zyklus, sobald der alte abgeschlossen wurde, damit neue und geänderte Dateien gefunden werden.

## <a name="how-files-are-scanned"></a>So werden Dateien überprüft

Der Scanner führt die folgenden Prozesse zur Überprüfung von Dateien aus.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. bestimmen Sie, ob Dateien für die Überprüfung eingeschlossen oder ausgeschlossen werden. 
Der Scanner überspringt automatisch Dateien, die von der Klassifizierung und dem Schutz ausgeschlossen sind, z. b. ausführbare Dateien und Systemdateien. Weitere Informationen finden Sie in den folgenden Administrator Handbüchern:

- Für den klassischen Client: [Dateitypen, die von der Klassifizierung und dem Schutz ausgeschlossen sind](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

- Für den Unified-Bezeichnungs Client: [Dateitypen, die von der Klassifizierung und dem Schutz ausgeschlossen sind](./rms-client/clientv2-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection)

Sie können dieses Verhalten ändern, indem Sie eine Liste mit Dateitypen definieren, die überprüft oder von der Überprüfung ausgeschlossen werden sollen. Sie können diese Liste für den Scanner angeben, damit standardmäßig alle Datenrepositorys angewendet werden. Zudem können Sie eine Liste für jedes Datenrepository angeben. Verwenden Sie zum Angeben dieser Liste die Einstellung **Zu scannende Dateitypen** im Scannerprofil:

![Konfigurieren der zu überprüfenden Dateitypen für den Azure Information Protection-Scanner](./media/scanner-file-types.png)

### <a name="2-inspect-and-label-files"></a>2. überprüfen und bezeichnen von Dateien

Anschließend verwendet der Scanner Filter, um unterstützte Dateitypen zu überprüfen. Diese Filter werden auch vom Betriebssystem für Windows Search und die Indizierung verwendet. Wenn keine anderen Konfigurationen vorhanden sind, wird Windows-IFilter verwendet, um Dateitypen zu überprüfen, die nicht für Word-, Excel-, PowerPoint- und PDF-Dokumente sowie Textdateien verwendet werden.

Eine vollständige Liste der standardmäßig unterstützten Dateitypen sowie weitere Informationen zum Konfigurieren von vorhandenen Filtern, die ZIP-Dateien und TIFF-Dateien enthalten, finden Sie in den folgenden Administrator Handbüchern:

- Für den klassischen Client: [für die Überprüfung Unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-inspection)
- Für den Unified-Bezeichnungs Client: [für die Überprüfung Unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md#file-types-supported-for-inspection)

Nach der Überprüfung können diese Dateitypen mithilfe der Bedingungen bezeichnet werden, die Sie für Ihre Bezeichnungen angegeben haben. Wenn Sie den Suchmodus verwenden, ist für diese Dateien stattdessen festgelegt, dass sie die Bedingungen enthalten, die Sie für Ihre Bezeichnungen angegeben haben, oder dass sämtliche bekannten Typen von vertraulichen Informationen enthalten sind. 

Der Scanner kann die Dateien jedoch unter den folgenden Bedingungen nicht bezeichnen:

- Wenn die Bezeichnung Klassifizierung und nicht Schutz anwendet, unterstützt der Dateityp nicht nur die Klassifizierung durch den [klassischen Client](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only) oder den Unified Label- [Client](./rms-client/clientv2-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Wenn die Bezeichnung zwar Klassifizierung und Schutz anwendet, aber der Scanner den Dateityp nicht schützt
    
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Andere Dateitypen können geschützt werden, wenn Sie wie im folgenden Abschnitt beschrieben [ändern, welche Dateitypen geschützt werden](#change-which-file-types-to-protect) .

Beispielsweise kann der Scanner, nachdem er TXT-Dateien überprüft hat, keine Bezeichnungen anwenden, die nur für die Klassifizierung und nicht für den Schutz konfiguriert sind, weil der TXT-Dateityp dies nicht unterstützt. Wenn die Bezeichnung für Klassifizierung und Schutz konfiguriert ist und die Dateinamenerweiterung. txt für den zu schützenden Scanner enthalten ist, kann die Überprüfung die Datei bezeichnen. 

> [!TIP]
> Wenn während dieses Vorgangs der Scanner stoppt und die Überprüfung einer großen Anzahl von Dateien in einem Repository nicht abgeschlossen wird:
> 
> - Möglicherweise müssen Sie die Anzahl der dynamischen Ports für das Betriebssystem erhöhen, das die Dateien hostet. Ein Grund dafür, warum der Scanner die Anzahl an zulässigen Netzwerkverbindungen überschreitet und daher angehalten wird, ist die Serverhärtung für SharePoint.
>     
>     Wenn Sie überprüfen möchten, ob dies die Ursache für die Beendigung der Überprüfung ist, überprüfen Sie, ob die folgende Fehlermeldung für den Scanner in%*LocalAppData*% \ microsoft\msip\protokolle\msipscanner.iplog protokolliert wird (ZIP-Dateien, wenn mehrere Protokolle vorhanden sind): **keine Verbindung mit der Remote Server---> System .net. Sockets. SocketException: nur eine Verwendung der einzelnen Socketadressen (Protokoll/Netzwerkadresse/Port) ist normalerweise als IP: Port zulässig** .
>    
>     Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](https://docs.microsoft.com/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).
> 
> - Für große SharePoint-Farmen müssen Sie möglicherweise den Schwellenwert der Listenansicht (standardmäßig 5.000) erhöhen. Weitere Informationen finden Sie in der folgenden SharePoint-Dokumentation: [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).

### <a name="3-label-files-that-cant-be-inspected"></a>3. Bezeichnungs Dateien, die nicht überprüft werden können
Bei Dateitypen, die nicht überprüft werden können, wendet der Scanner die Standardbezeichnung in der Azure Information Protection-Richtlinie oder die von Ihnen für die Überprüfung konfigurierte Standardbezeichnung an.

Wie im vorherigen Schritt kann der Scanner die Dateien jedoch unter den folgenden Bedingungen nicht bezeichnen:

- Wenn die Bezeichnung Klassifizierung und nicht Schutz anwendet, unterstützt der Dateityp nicht nur die Klassifizierung durch den [klassischen Client](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only) oder den Unified Label- [Client](./rms-client/clientv2-admin-guide-file-types.md#file-types-supported-for-classification-only).

- Wenn die Bezeichnung zwar Klassifizierung und Schutz anwendet, aber der Scanner den Dateityp nicht schützt
    
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Andere Dateitypen können geschützt werden, wenn Sie wie im folgenden beschrieben ändern, welche Dateitypen geschützt werden.

## <a name="change-which-file-types-to-protect"></a>Ändern der zu schützenden Dateitypen

Standardmäßig schützt der Scanner nur Office-Dateitypen und PDF-Dateien. Sie können dieses Verhalten ändern, sodass z. b. die Überprüfung alle Dateitypen schützt, bei denen es sich um das gleiche Schutzverhalten wie der Client handelt. Oder der Scanner schützt zusätzlich zu den Office-Dateitypen und PDF-Dateien zusätzliche Dateitypen, die Sie angeben. 

Konfigurations Anweisungen finden Sie in den folgenden Abschnitten.

### <a name="scanner-from-the-classic-client-use-the-registry-to-change-which-file-types-are-protected"></a>Überprüfung des klassischen Clients: Verwenden Sie die Registrierung, um die geschützten Dateitypen zu ändern.

Dieser Abschnitt gilt nur für die Überprüfung des klassischen Clients.

Wenn Sie das Standard Scanner Verhalten zum Schutz von Dateitypen außer Office-Dateien und-PDF-Dateien ändern möchten, müssen Sie die Registrierung bearbeiten und die zusätzlichen Dateitypen angeben, die Sie schützen möchten, sowie den Typ des Schutzes (System eigen oder generisch). Weitere Informationen hierzu finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet. Folgendes gilt außerdem speziell für den Scanner:

- Der Scanner verfügt über ein eigenes Standardverhalten: nur Office-Dateiformate und PDF-Dokumente werden standardmäßig geschützt. Wenn die Registrierung nicht geändert wird, werden andere Dateitypen nicht vom Scanner bezeichnet oder geschützt.

- Wenn Sie das gleiche Standardschutz Verhalten wie der Azure Information Protection-Client wünschen, wobei alle Dateien automatisch durch systemeigenen oder generischen Schutz geschützt werden: Geben Sie den `*` Platzhalter als Registrierungsschlüssel an, `Encryption` als Wert (REG_SZ) und @no__ t_2_ als Wertdaten.

Wenn Sie die Registrierung bearbeiten, erstellen Sie manuell die beiden Schlüssel **MSIPC** und **FileProtection**, falls noch nicht vorhanden, sowie einen Schlüssel für jede Erweiterung.

Damit der Scanner beispielsweise neben Office- und PDF-Dateien auch TIFF-Bilder schützt, sieht die Registrierung nach Ihrer Bearbeitung wie auf der folgenden Abbildung aus. TIFF-Dateien unterstützen als Bilddateien den nativen Schutz. Die entsprechende Erweiterung lautet „.ptiff“.

![Bearbeiten der Registrierung für die Überprüfung zum Anwenden von Schutz](./media/editregistry-scanner.png)

Eine Liste mit Text-und Bild Dateitypen, die auf ähnliche Weise systemeigenen Schutz unterstützen, aber in der Registrierung angegeben werden müssen, finden Sie [unter Unterstützte Dateitypen für Klassifizierung und Schutz](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection).

Geben Sie für Dateien, die den nativen Schutz nicht unterstützten, die Erweiterung als einen neuen Schlüssel und **PFILE** für den generischen Schutz an. Die Erweiterung für die geschützte Datei lautet dann „.pfile“.

### <a name="scanner-from-the-unified-labeling-client-use-powershell-to-change-which-file-types-are-protected"></a>Überprüfung des Unified-Bezeichnungs Clients: Verwenden Sie PowerShell, um die geschützten Dateitypen zu ändern.

Dieser Abschnitt gilt nur für die Überprüfung des Unified-Beschriftungs Clients.

Geben Sie für eine Bezeichnungs Richtlinie, die für das Benutzerkonto gilt, das Bezeichnungen für den Scanner herunterlädt, eine PowerShell-erweiterte Einstellung mit dem Namen **pfilesupportedextensions**an. 

> [!NOTE]
> Bei einem Scanner, der Zugriff auf das Internet hat, ist dieses Benutzerkonto das Konto, das Sie für den Parameter " *delegateduser* " mit dem Befehl "Set-aipauthentication" angeben.

Beispiel 1: PowerShell-Befehl für die Überprüfung, um alle Dateitypen zu schützen, deren Bezeichnung "Scanner" lautet:

    Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions="*"}

Beispiel 2: PowerShell-Befehl für die Überprüfung, um XML-Dateien und TIFF-Dateien zu schützen, zusätzlich zu Office-Dateien und PDF-Dateien, bei denen die Bezeichnung "Scanner" lautet:

    Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions=ConvertTo-Json(".xml", ".tiff")}

Ausführliche Anweisungen finden Sie im Administrator Handbuch unter [Ändern der zu schützenden Dateitypen](./rms-client/clientv2-admin-guide-customizations.md#change-which-file-types-to-protect) .


## <a name="when-files-are-rescanned"></a>Wann Dateien überprüft werden

Im ersten Überprüfungszyklus untersucht die Überprüfung alle Dateien in den Datenspeichern. In den nachfolgenden Überprüfungen werden dann nur noch neue oder geänderte Dateien untersucht. 

Sie können erzwingen, dass der Scanner alle Dateien erneut aus dem Bereich **Azure Information Protection profile** in der Azure-Portal prüft. Wählen Sie Ihr Überprüfungs Profil aus der Liste aus, und wählen Sie dann die Option **alle Dateien neu** Einlesen aus:

![Initiieren eines erneuten Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-rescan-files2.png)

Das erneute Überprüfen aller Dateien ist nützlich, wenn Sie möchten, dass die Berichte alle Dateien enthalten. Diese Konfiguration wird in der Regel verwendet, wenn die Überprüfung im Ermittlungsmodus ausgeführt wird. Wenn eine vollständige Überprüfung abgeschlossen ist, ändert sich der Überprüfungstyp automatisch auf „inkrementell“, sodass bei nachfolgenden Überprüfungen nur noch neue oder geänderte Dateien untersucht werden.

Außerdem werden alle Dateien überprüft, wenn die Überprüfung des klassischen Clients eine Azure Information Protection Richtlinie mit neuen oder geänderten Bedingungen herunterlädt und die Überprüfung des Unified-Bezeichnungs Clients über neue oder geänderte Einstellungen für automatisches und Empfohlene Bezeichnung. 

Die Überprüfung aktualisiert die Richtlinie gemäß den folgenden Triggern:

- Scanner vom klassischen Client: stündlich und wenn der Dienst gestartet wird und die Richtlinie älter als eine Stunde ist. 

- Scanner vom Unified-Bezeichnungs Client: alle vier Stunden und beim Start des Dienstanbieter. 

> [!TIP]
> Wenn Sie die Richtlinie früher als das Standardintervall aktualisieren müssen, z. b. während eines Testzeitraums: 
>
> - Scanner vom klassischen Client: Löschen Sie die Richtlinien Datei **Policy. MSIP** manuell aus **%LocalAppData%\microsoft\msip\policy.MSIP**.
>
> - Scanner vom Unified-Bezeichnungs Client: Löschen Sie den Inhalt manuell aus **%LocalAppData%\microsoft\msip\mip\\<*ProcessName*> \mip**.
>
Starten Sie anschließend den Azure Information-Überprüfungsdienst neu. Wenn Sie Schutzeinstellungen für ihre Bezeichnungen geändert haben, warten Sie auch 15 Minuten ab dem Zeitpunkt, an dem Sie die Schutzeinstellungen gespeichert haben, bevor Sie den Dienst neu starten.


## <a name="editing-in-bulk-for-the-data-repository-settings"></a>Gleichzeitiges Bearbeiten von mehreren Datenrepositoryeinstellungen

Für die Datenrepositorys, die Sie einem Scannerprofil hinzugefügt haben, können Sie die Optionen **Exportieren** und **Importieren** verwenden, um die Einstellungen im Handumdrehen zu ändern. Dies ist beispielsweise möglich, wenn Sie für Ihre SharePoint-Datenrepositorys einen neuen Dateityp hinzufügen möchten, um ihn vom Scanvorgang auszuschließen.

Anstatt jedes Datenrepository im Azure-Portal zu bearbeiten, verwenden Sie die **Export** -Option aus dem Bereich " **Depots** ":

![Exportieren der Datenrepositoryeinstellungen für den Scanner](./media/export-scanner-repositories.png)

Bearbeiten Sie die Datei manuell, um die Änderung vorzunehmen, und verwenden Sie dann die Option **importieren** im gleichen Bereich.

## <a name="using-the-scanner-with-alternative-configurations"></a>Verwenden der Überprüfung mit alternativen Konfigurationen

Der Azure Information Protection Scanner unterstützt drei alternative Szenarios, in denen Bezeichnungen nicht für Bedingungen konfiguriert werden müssen: 

- Anwenden einer Standardbezeichnung auf alle Dateien in einem Datenrepository:
    
    Legen Sie für diese Konfiguration Bezeichnungs **Dateien auf der Grundlage von Inhalt** auf **Off**fest. Legen Sie dann die **Standard Bezeichnung** auf **Custom**fest, und wählen Sie die zu verwendende Bezeichnung aus.
    
    Der Inhalt der Dateien wird nicht überprüft, und alle nicht beschrifteten Dateien im Datenrepository sind entsprechend der Standard Bezeichnung gekennzeichnet, die Sie für das Datenrepository oder das Scanner-Profil angeben. 
    
    Bei der Überprüfung des Unified Label-Clients können Sie auch die Option **Standard Bezeichnung erzwingen** auswählen, wenn die Standard Bezeichnung auf alle Dateien angewendet werden soll, auch wenn Sie bereits mit der Bezeichnung versehen sind.
    

- Entfernen Sie vorhandene Bezeichnungen aus allen Dateien in einem Datenrepository.
    
    Dies gilt nur für die Überprüfung des Unified Label-Clients. diese Konfiguration ermöglicht es Ihnen, vorhandene Bezeichnungen zu entfernen. Dies umfasst auch den Schutz, wenn dieser mit dieser Bezeichnung angewendet wurde. Der Schutz, der unabhängig von einer Bezeichnung angewendet wurde, wird beibehalten. Verwenden Sie diese Konfiguration, wenn Sie alle Bezeichnungen aus Dateien in einem Repository entfernen müssen.
    
    Konfigurieren Sie die folgenden Einstellungen:
    - Bezeichnungs **Dateien basierend auf dem Inhalt**: **Off**
    - **Standard Bezeichnung**: **keine**
    - **Dateien**neu bezeichnen: **aktivieren** Sie das Kontrollkästchen **Standard Bezeichnung erzwingen** ausgewählt haben.

- Identifizieren aller benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen:
    
    Legen Sie für diese Konfiguration die Option **Zu ermittelnde Infotypen** auf **Alle** fest.
    
    Für die Überprüfung des klassischen Clients: der Scanner verwendet alle benutzerdefinierten Bedingungen, die Sie in der Azure Information Protection Richtlinie für Bezeichnungen angegeben haben, sowie die Liste der Informationstypen, die zur Angabe für Bezeichnungen in den Azure-Informationen verfügbar sind. Schutzrichtlinie. 
    
    Für die Überprüfung des Unified-Bezeichnungs Clients: der Scanner verwendet alle benutzerdefinierten sensiblen Informationstypen, die Sie angegeben haben, und die Liste der integrierten sensiblen Informationstypen, die in Ihrem Bezeichnungs Verwaltungs Center ausgewählt werden können.
    
    Mit dieser Einstellung können Sie nach vertraulichen Informationen suchen, von denen Sie möglicherweise nicht einmal wissen, dass Sie sie haben. Das geht jedoch auf Kosten der Scangeschwindigkeit des Scanners.
    
    In der folgenden Schnellstartanleitung für die Überprüfung wird diese Konfiguration verwendet: [Schnellstart: finden Sie heraus, welche sensiblen Informationen Sie besitzen](quickstart-findsensitiveinfo.md).

## <a name="optimizing-the-performance-of-the-scanner"></a>Optimieren der Überprüfungsleistung

Nutzen Sie den folgenden Leitfaden, um die Leistung der Überprüfung zu optimieren. Wenn Sie jedoch die Reaktionsfähigkeit des scannercomputers anstelle der Überprüfungs Leistung haben, können Sie eine [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#limit-the-number-of-threads-used-by-the-scanner) verwenden, um die Anzahl der von der Überprüfung verwendeten Threads einzuschränken (nur klassischer Client).

So maximieren Sie die Überprüfungsleistung:

- **Verwenden Sie eine schnelle und zuverlässige Netzwerkverbindung zwischen dem Überprüfungscomputer und dem überprüften Datenspeicher**
    
    Platzieren Sie beispielsweise den überprüfenden Computer im gleichen LAN oder (vorzugsweise) im gleichen Netzwerksegment wie den überprüften Datenspeicher.
    
    Die Qualität der Netzwerkverbindung wirkt sich auf die Überprüfungsleistung aus, da die Überprüfung die Dateien zur Untersuchung auf den Computer überträgt, auf dem der Überprüfungsdienst ausgeführt wird. Durch Reduzieren (oder Ausschalten) der Anzahl der Netzwerkhops, über die diese Daten transportiert werden, verringern Sie zugleich Ihre Netzwerkauslastung. 

- **Achten Sie darauf, dass der überprüfende Computer verfügbare Prozessorressourcen aufweist**
    
    Das Untersuchen der Dateiinhalte und Ver- und Entschlüsseln der Dateien sind prozessorlastige Aktionen. Überprüfen Sie typische Überprüfungszyklen für Ihre angegebenen Datenquellen, um zu bestimmen, ob ein Mangel an Prozessorressourcen sich negativ auf die Überprüfungsleistung auswirkt.
    
- **Überprüfen Sie keine lokalen Ordner auf dem Computer, auf dem der Überprüfungsdienst ausgeführt wird**
    
    Wenn Ordner auf einem Windows-Servercomputer untersucht werden müssen, installieren Sie die Überprüfung auf einem anderen Computer, und konfigurieren Sie diese Ordner als zu überprüfende Netzwerkfreigaben. Das Trennen der beiden Funktionen des Hostens der Dateien und des Überprüfens der Dateien bedeutet, dass die Computerressourcen für diese Dienste nicht in Konkurrenz miteinander stehen.

Installieren Sie ggf. mehrere Instanzen der Überprüfung. Vom Azure Information Protection-Scanner werden beim Angeben eines benutzerdefinierten Profilnamens für den Scanner mehrere Konfigurationsdatenbanken auf einer SQL Server-Instanz unterstützt. Bei der Überprüfung des Unified-Bezeichnungs Clients können mehrere Scanner dasselbe Profil verwenden, was zu schnelleren Scanzeiten führt.

Weitere Faktoren, die sich auf die Überprüfungsleistung auswirken:

- Die aktuelle Last und die Antwortzeiten der Datenspeicher, in denen die zu überprüfenden Dateien enthalten sind

- Ob die Überprüfung im Suchmodus oder im Durchsetzungsmodus ausgeführt wird
    
    Im Suchmodus wird normalerweise eine höhere Überprüfungsrate als im Durchsetzungsmodus erreicht, da für die Ermittlung ein einzelner Dateilesevorgang erforderlich ist, während für den Durchsetzungsmodus Lese- und Schreibvorgänge erforderlich sind.

- Sie ändern die Bedingungen in der Richtlinie für die Azure Information Protection (klassischer Client) oder die automatische Bezeichnung in der Bezeichnungs Richtlinie (Unified Label-Client).
    
    Der erste Scanzyklus, in dem der Scanner jede Datei untersuchen muss, benötigt mehr Zeit als die nachfolgenden Scanzyklen, in denen standardmäßig nur neue und geänderte Dateien untersucht werden. Wenn Sie jedoch die Bedingungen oder Einstellungen für die automatische Bezeichnung ändern, werden alle Dateien erneut gescannt, wie im [vorherigen Abschnitt](#when-files-are-rescanned)beschrieben.

- Die Erstellung von regulären Ausdrücken für benutzerdefinierte Bedingungen
    
    Überprüfen Sie Ihre regulären Ausdrücke für einen effizienten Musterabgleich, um eine hohe Arbeitsspeichernutzung und das Risiko von Timeouts (15 Minuten pro Datei) zu vermeiden. Beispiele:
    
    - Vermeiden Sie [gierige Quantifizierer](https://docs.microsoft.com/dotnet/standard/base-types/quantifiers-in-regular-expressions)
    
    - Verwenden Sie Gruppen ohne Erfassung wie `(?:expression)` anstelle von `(expression)`

- Der ausgewählte Protokolliergrad
    
    Sie können für die Überprüfungsberichte zwischen **Debuggen**, **Info**, **Fehler** und **Aus** wählen. **Aus** führt zur besten Leistung; **Debuggen** verlangsamt die Überprüfung erheblich und sollte nur zur Problembehebung verwendet werden. Weitere Informationen finden Sie beim Parameter *ReportLevel* für das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration).

- Die Dateien selbst:
    
    - Mit Ausnahme von Excel-Dateien werden Office-Dateien schneller gescannt als PDF-Dateien.
    
    - Ungeschützte Dateien sind schneller zu überprüfen als geschützte Dateien.
    
    - Das Überprüfen großer Dateien beansprucht naturgemäß mehr Zeit als das Überprüfen kleiner Dateien.

- Weiterhin gilt:
    
    - Vergewissern Sie sich, dass das Dienst Konto, unter dem die Überprüfung ausgeführt wird, nur über die im Abschnitt Überprüfungs [Voraussetzungen](#prerequisites-for-the-azure-information-protection-scanner) dokumentierten Rechte verfügt, und konfigurieren Sie dann die Einstellung erweiterter [Client](./rms-client/client-admin-guide-customizations.md#disable-the-low-integrity-level-for-the-scanner) , um die Ebene mit niedriger Integrität für den Scanner zu deaktivieren (nur klassischer Client)
    
    - Die Überprüfung wird schneller ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der eine Standardbezeichnung auf alle Dateien angewendet wird, ohne dass die Dateiinhalte überprüft werden.
    
    - Die Überprüfung wird langsamer ausgeführt, wenn Sie die [alternative Konfiguration](#using-the-scanner-with-alternative-configurations) verwenden, bei der alle benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen identifiziert werden.
    
    - Sie können die Überprüfungs Timeouts (nur klassischer Client) mit [erweiterten Client Einstellungen](./rms-client/client-admin-guide-customizations.md#change-the-timeout-settings-for-the-scanner) verringern, um eine bessere Scanrate zu erzielen und den Speicherverbrauch zu verringern, aber mit der Bestätigung, dass einige Dateien übersprungen werden.

## <a name="list-of-cmdlets-for-the-scanner"></a>Auflisten der Cmdlets für die Überprüfung

Da der Scanner jetzt über das Azure-Portal konfiguriert wird, sind Cmdlets von früheren Versionen, mit denen Datenrepositorys konfiguriert wurden, und die Liste der überprüften Dateitypen veraltet. 

Zu den verbleibenden Cmdlets gehören diejenigen, mit denen der Scanner installiert und upgegradet werden kann und die Konfigurationsdatenbank und das Profil des Scanners sowie der Grad der lokalen Berichterstellung geändert und Konfigurationseinstellungen für einen nicht verbundenen Computer importiert werden können. 

Die vollständige Liste der Cmdlets für den Scanner: 

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Export-aiplogs](/powershell/module/azureinformationprotection/Export-AIPLogs) -einheitlicher Bezeichnungs Client

- [Import-aipscannerconfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

- [Start-AIPScan](/powershell/module/azureinformationprotection/Start-AIPScan)

- [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner)

- [Update-AIPScanner](/powershell/module/azureinformationprotection/Update-AIPScanner)


## <a name="event-log-ids-and-descriptions-for-the-scanner"></a>Ereignisprotokoll-IDs und Beschreibungen für die Überprüfung

Anhand der folgenden Abschnitte können Sie mögliche Ereignis-IDs und Beschreibungen für die Überprüfung ermitteln. Diese Ereignisse werden im Windows-Ereignisprotokoll für **Anwendungen und Dienste**, **Azure Information Protection**, auf dem Server erfasst, auf dem der Überprüfungsdienst ausgeführt wird.

> [!NOTE]
> Dieser Abschnitt gilt nur für die Überprüfung des klassischen Clients. Derzeit schreibt der Scanner vom Unified-Bezeichnungs Client keine Informationen in das Ereignisprotokoll.

-----

Information **910**

**Scanner cycle started.** (Überprüfungszyklus wurde gestartet)

Dieses Ereignis wird protokolliert, wenn die Überprüfung gestartet wird und beginnt, die Dateien in den Datenrepositorys zu prüfen, die Sie angegeben haben.

----

Information **911**

**Scanner cycle finished.** (Überprüfungszyklus wurde abgeschlossen)

Dieses Ereignis wird protokolliert, wenn der Scanner eine manuelle Überprüfung oder eine Schleife mit kontinuierlichen Ausführungen beendet hat.

Wenn der Scanner so konfiguriert wurde, dass er manuell und nicht kontinuierlich ausgeführt wird, legen Sie zum erneuten Scannen der Dateien den **Zeitplan** im Scannerprofil auf **Manuell** oder **Immer** fest und starten den Dienst anschließend neu.

----

## <a name="next-steps"></a>Nächste Schritte

Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Sie fragen sich womöglich, [was der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung ist](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner).

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden Sie in den folgenden Abschnitten der Administrator Handbücher:

- Für den klassischen Client: [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md)

- Für den Unified-Bezeichnungs Client: [Verwenden von PowerShell mit dem Azure Information Protection Unified-Beschriftungs Client](./rms-client/clientv2-admin-guide-powershell.md)
