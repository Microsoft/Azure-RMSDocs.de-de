---
title: Voraussetzungen für den klassischen Azure Information Protection (AIP)-Scanner
description: Listet die Voraussetzungen für die Installation und Bereitstellung des Azure Information Protection klassischen Scanner auf.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 02/03/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ROBOTS: NOINDEX
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: fb1d7a7ce57eb6ae8659b7e268726143d4ca4028
ms.sourcegitcommit: 1aba7f2d5c15f2657d1db293118f6670bf99323d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "99505270"
---
# <a name="prerequisites-for-installing-and-deploying-the-azure-information-protection-classic-scanner"></a>Voraussetzungen für die Installation und Bereitstellung des Azure Information Protection klassischen Scanners

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum vereinheitlichten Bezeichnungs Scanner finden Sie unter [Voraussetzungen für die vereinheitlichte Bezeichnung](deploy-aip-scanner-prereqs.md) .*

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Stellen Sie vor der Installation des Azure Information Protection lokalen Scanners sicher, dass Ihr System die grundlegenden [Azure Information Protection Anforderungen](requirements.md)erfüllt und die folgenden Anforderungen für die Überprüfung erfüllt sind:

- [Windows Server-Anforderungen](#windows-server-requirements)
- [Dienstkontenanforderungen](#service-account-requirements)
- [SQL Server-Anforderungen](#sql-server-requirements)
- [Zusätzliche Voraussetzungen für den Azure Information Protection-Client](#azure-information-protection-client-requirements)
- [Bezeichnungs Konfigurations Anforderungen](#label-configuration-requirements)
- [SharePoint-Anforderungen](#sharepoint-requirements)
- [Microsoft Office Anforderungen](#microsoft-office-requirements)
- [Dateipfad-Anforderungen](#file-path-requirements)

Wenn Sie nicht alle Anforderungen in der Tabelle erfüllen können, weil Sie von ihren Organisations Richtlinien nicht zugelassen werden, lesen Sie den Abschnitt [Alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations) .

Wenn Sie den Scanner in der Produktionsumgebung bereitstellen oder die Leistung mehrerer Scanner testen, finden Sie weitere Informationen unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

Wenn Sie bereit sind, mit der Installation und Bereitstellung Ihres Scanners zu beginnen, können Sie mit der Bereitstellung [des Azure Information Protection Scanners fortfahren, um Dateien automatisch zu klassifizieren](deploy-aip-scanner-configure-install-classic.md)

## <a name="windows-server-requirements"></a>Windows Server-Anforderungen

Sie müssen über einen Windows Server-Computer verfügen, auf dem die Überprüfung ausgeführt werden kann. diese verfügt über die folgenden Systemspezifikationen:

|Spezifikation  |Details  |
|---------|---------|
|**Prozessor**     |4-Kern Prozessoren         |
|**RAM**     |8 GB         |
|**Speicherplatz**     |10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien. </br></br>Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. </br></br>Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen. 
|**Betriebssystem**     |-Windows Server 2019 </br>- Windows Server 2016 </br>Windows Server 2012 R2 </br></br>**Hinweis**: zu Test-oder Evaluierungs Zwecken in einer nicht-Produktionsumgebung können Sie auch ein beliebiges Windows-Betriebssystem verwenden, das [vom Azure Information Protection-Client unterstützt](requirements.md#client-devices)wird.
|**Netzwerkverbindungen**     | Bei dem Überprüfungs Computer kann es sich um einen physischen oder virtuellen Computer mit einer schnellen und zuverlässigen Netzwerkverbindung mit den zu überprüfenden Daten speichern handeln. </br></br> Wenn die Internetverbindung aufgrund ihrer Organisations Richtlinien nicht möglich ist, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations). </br></br>Stellen Sie andernfalls sicher, dass dieser Computer über eine Internetverbindung verfügt, die die folgenden URLs über HTTPS (Port 443) zulässt:</br><br />-  \*. aadrm.com <br />-  \*. azurerms.com<br />-  \*. informationprotection.Azure.com <br /> -informationprotection.Hosting.Portal.Azure.net <br /> - \*. Aria.Microsoft.com|
| ||

## <a name="service-account-requirements"></a>Dienstkontenanforderungen

Sie müssen über ein Dienst Konto verfügen, um den Überprüfungs Dienst auf dem Windows Server-Computer auszuführen. Außerdem müssen Sie sich bei Azure AD authentifizieren und die Azure Information Protection-Richtlinie herunterladen.

Ihr Dienst Konto muss ein Active Directory Konto sein und mit Azure AD synchronisiert werden.

Wenn Sie dieses Konto aufgrund ihrer Organisations Richtlinien nicht synchronisieren können, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

Für dieses Dienstkonto gelten die folgenden Anforderungen:

|Anforderung  |Details  |
|---------|---------|
|**Lokale** Benutzerrechte Zuweisung anmelden     |Erforderlich, um die Überprüfung zu installieren und zu konfigurieren, aber nicht zum Ausführen von Scans erforderlich.  </br></br>Nachdem Sie sich vergewissert haben, dass die Überprüfung Dateien ermitteln, klassifizieren und schützen kann, können Sie diese direkt aus dem Dienst Konto entfernen.  </br></br>Wenn diese Berechtigung auch für kurze Zeit nicht möglich ist, ist dies aufgrund ihrer Organisations Richtlinien nicht möglich. Weitere Informationen hierzu finden Sie unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).         |
|**Anmeldung als Dienst** für die Zuweisung von Benutzerrechten.     |  Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich.        |
|**Berechtigungen für die Daten Depots**     |- **Dateifreigaben oder lokale Dateien**: erteilen **Sie Lese**-, **Schreib**-und Änderungs Berechtigungen zum Scannen der **Dateien und zum** anschließenden Anwenden von Klassifizierung und Schutz.  <br /><br />- **SharePoint**: erteilen Sie **voll** Zugriffsberechtigungen zum Scannen der Dateien und zum anschließenden anwenden der Klassifizierung und des Schutzes entsprechend der Konfiguration.  <br /><br />- Ermittlungs **Modus**: um die Überprüfung nur im Ermittlungs Modus auszuführen, genügt die **Lese** Berechtigung.         |
|**Für Bezeichnungen, die den Schutz erneut schützen oder entfernen**     | Um sicherzustellen, dass die Überprüfung stets Zugriff auf geschützte Dateien hat, machen Sie dieses Konto als [Administrator für Azure Information Protection](configure-super-users.md) , und stellen Sie sicher, dass die Administrator Funktion aktiviert ist. </br></br>Wenn Sie [Onboarding](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) -Steuerelemente für eine stufenweise Bereitstellung implementiert haben, stellen Sie außerdem sicher, dass das Dienst Konto in den Onboarding-Steuerelementen enthalten ist, die Sie konfiguriert haben.|
| ||

## <a name="sql-server-requirements"></a>SQL Server-Anforderungen

Verwenden Sie zum Speichern der Überprüfungs Konfigurationsdaten einen SQL-Server mit den folgenden Anforderungen:

- **Eine lokale Instanz oder eine Remote Instanz.**

    Es wird empfohlen, SQL Server und den Scanner-Dienst auf unterschiedlichen Computern zu verwenden, es sei denn, Sie arbeiten mit einer kleinen Bereitstellung. Außerdem wird empfohlen, dass Sie über eine dedizierte SQL-Instanz verfügen, die nur für die Überprüfungs Datenbank dient und die nicht mit anderen Anwendungen gemeinsam genutzt wird.

    Wenn Sie an einem freigegebenen Server arbeiten, stellen Sie sicher, dass die [Empfohlene Anzahl von Kernen](#windows-server-requirements) für die Ausführung der Überprüfungs Datenbank frei ist.

    SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:

    - SQL Server Enterprise
    - SQL Server Standard
    - SQL Server Express (nur für Testumgebungen empfohlen)

- **Ein Konto mit der sysadmin-Rolle zum Installieren des Scanners.**

    Dies ermöglicht es dem Installationsprozess, die Überprüfungs Konfigurationsdatenbank automatisch zu erstellen und dem Dienst Konto, das die Überprüfung ausführt, die erforderliche **db_owner** Rolle zu erteilen. 

    Wenn Ihnen die sysadmin-Rolle nicht gewährt werden kann oder wenn Ihre Organisations Richtlinien erfordern, dass Datenbanken manuell erstellt und konfiguriert werden, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

- **Capacity** (Kapazität): Informationen zur Kapazitäts Orientierung finden Sie unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

- **[Sortierung](/sql/relational-databases/collations/collation-and-unicode-support)ohne Beachtung**

> [!NOTE]
> Mehrere Konfigurations Datenbanken auf demselben SQL Server werden unterstützt, wenn Sie einen benutzerdefinierten Cluster Namen (Profilnamen) für die Überprüfung angeben.
> 

### <a name="storage-requirements-and-capacity-planning-for-sql-server"></a>Speicheranforderungen und Kapazitätsplanung für SQL Server

Der erforderliche Speicherplatz für die Konfigurations Datenbank des Scanners und die Angabe des Computers, auf dem SQL Server ausgeführt wird, kann je nach Umgebung variieren. Daher empfehlen wir Ihnen, ihre eigenen Tests durchzuführen. Verwenden Sie die folgende Anleitung als Ausgangspunkt.

Weitere Informationen finden Sie unter [Optimieren der Leistung des Scanners](deploy-aip-scanner-configure-install-classic.md#optimizing-scanner-performance).

Die Datenträger Größe für die Konfigurations Datenbank variiert für jede Bereitstellung. Es wird empfohlen, dass Sie 500 MB für alle 1 Million-Dateien zuordnen, die Sie überprüfen möchten. 

Verwenden Sie für jeden Scanner Folgendes:

- 4-Kern Prozessoren
- 8 GB RAM (mindestens 4 GB)

## <a name="azure-information-protection-client-requirements"></a>Zusätzliche Voraussetzungen für den Azure Information Protection-Client

Der Azure Information Protection-Client muss auf dem Windows Server-Computer installiert sein.

Weitere Informationen finden Sie im [klassischen Client Administrator Handbuch](./rms-client/client-admin-guide.md).

> [!IMPORTANT]
> Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.
> 

## <a name="label-configuration-requirements"></a>Bezeichnungs Konfigurations Anforderungen

Sie müssen Bezeichnungen konfiguriert haben, die automatisch Klassifizierung und optional Schutz anwenden.

Wenn Sie diese Bezeichnungen nicht konfiguriert haben, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

Weitere Informationen finden Sie unter

- [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)
- [How to configure a label for Rights Management protection (Konfigurieren einer Bezeichnung für Rights Management-Schutz)](configure-policy-protection.md)

> [!TIP] 
> Verwenden Sie die Anweisungen aus dem [Tutorial](infoprotect-quick-start-tutorial.md) , um den Scanner mit einer Bezeichnung zu testen, die in einem vorbereiteten Word-Dokument nach Kreditkartennummern sucht. Allerdings müssen Sie die Bezeichnungs Konfiguration ändern, damit die Option **Wählen Sie aus, wie diese Bezeichnung angewendet wird** auf " **automatisch**" und nicht auf "empfohlen" festgelegt ist **, oder die** **Empfohlene Bezeichnung als "automatisch" behandeln** (verfügbar in der Überprüfungs Version 2.7. x. x und höher). 
>
> Entfernen Sie anschließend die Bezeichnung vom Dokument (sofern angewendet), und kopieren Sie die Datei in ein Datenrepository für den Scanner. 

## <a name="sharepoint-requirements"></a>SharePoint-Anforderungen

Stellen Sie sicher, dass Ihr SharePoint-Server die folgenden Anforderungen erfüllt, um SharePoint-Dokument Bibliotheken und-Ordner zu überprüfen:

- **Unterstützte Versionen.** Folgende Versionen werden unterstützt: SharePoint 2019, SharePoint 2016 und SharePoint 2013. Andere Versionen von SharePoint werden für die Überprüfung nicht unterstützt.

- **Versionsverwaltung.** Wenn Sie die [Versions](/sharepoint/governance/versioning-content-approval-and-check-out-planning)Verwaltung verwenden, wird die zuletzt veröffentlichte Version vom Scanner überprüft und beschriftet. Wenn die Überprüfung eine Datei und eine [Genehmigung von Inhalten](/sharepoint/governance/versioning-content-approval-and-check-out-planning#plan-content-approval) erfordert, muss die bezeichnete Datei als verfügbar für Benutzer verfügbar sein.  

- **Große SharePoint-Farmen.** Überprüfen Sie für große SharePoint-Farmen, ob Sie den Schwellwert der Listenansicht (standardmäßig 5.000) erhöhen müssen, damit der Scanner auf alle Dateien zugreifen kann. Weitere Informationen finden Sie unter [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).


## <a name="microsoft-office-requirements"></a>Microsoft Office Anforderungen

Zum Scannen von Office-Dokumenten müssen Ihre Dokumente in einem der folgenden Formate vorliegen:

- Microsoft Office 97-2003 
- Office Open XML-Formate für Word, Excel und PowerPoint

Weitere Informationen finden Sie [unter vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).

## <a name="file-path-requirements"></a>Dateipfad-Anforderungen

Um Dateien zu überprüfen, dürfen die Dateipfade maximal 260 Zeichen lang sein, es sei denn, der Scanner ist unter Windows 2016 installiert, und der Computer ist für die Unterstützung von langen Pfaden konfiguriert.

Windows 10-und Windows Server 2016-Support Pfadlängen von mehr als 260 Zeichen mit der folgenden [Gruppenrichtlinien Einstellung](/archive/blogs/jeremykuhne/net-4-6-2-and-long-paths-on-windows-10): **lokale Computer Richtlinie**  >  **Computer Konfiguration**  >  **Administrative Vorlagen**  >  **alle Einstellungen**  >  **Aktivieren von Win32 Long-Pfaden**

Weitere Informationen zur Unterstützung von langen Dateipfaden finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

## <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die oben aufgeführten Voraussetzungen sind die Standardanforderungen für die Scanner-Bereitstellung und werden empfohlen, da Sie die einfachste Überprüfungs Konfiguration unterstützen.

Die Standardanforderungen sollten für die ersten Tests geeignet sein, damit Sie die Funktionen des Scanners überprüfen können. 

In einer Produktionsumgebung können diese Standardanforderungen in den Richtlinien Ihrer Organisation jedoch untersagt werden. Der Scanner kann die folgenden Einschränkungen mit zusätzlicher Konfiguration erfüllen:

- [Der Überprüfungs Server kann keine Internetverbindung haben.](#restriction-the-scanner-server-cannot-have-internet-connectivity)

- [Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.](#restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity)

- [Einschränkung: dem Dienst Konto für die Überprüfung kann nicht die Berechtigung zum **lokalen anmelden** erteilt werden.](#restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right)

- [Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.](#restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually)

- [Einschränkung: ihre Bezeichnungen haben keine automatischen Beschriftungs Bedingungen.](#restriction-your-labels-do-not-have-auto-labeling-conditions)

### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Einschränkung: der Überprüfungs Server kann keine Internetverbindung haben.

Führen Sie die folgenden Schritte aus, um einen getrennten Computer zu unterstützen:

1. Konfigurieren Sie Bezeichnungen, die nur die Klassifizierung anwenden, oder wenden Sie Schutz an, der den [Hyok-Schutz](configure-adrms-restrictions.md)verwendet. 

    Ohne Internetverbindung kann der Scanner keinen Schutz anwenden, den Schutz entfernen oder geschützte Dateien mit dem cloudbasierten Schlüssel Ihrer Organisation überprüfen. Stattdessen ist der Scanner auf die Verwendung von Bezeichnungen beschränkt, die nur die Klassifizierung anwenden, oder den Schutz anwenden, der den Hyok-Schutz verwendet.
    
    Weitere Informationen finden Sie [unter Unterstützung für nicht verbundene Computer](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers).

1. Konfigurieren Sie die Überprüfung im Azure-Portal, indem Sie einen scannercluster erstellen. Unterstützung zu diesem Schritt finden Sie im Abschnitt [Konfigurieren des Scanners im Azure-Portal](deploy-aip-scanner-configure-install-classic.md#configure-the-scanner-in-the-azure-portal).

2. Exportieren Sie den Inhalts Auftrag aus dem Bereich **Azure Information Protection-Inhalts Scanaufträge** mithilfe der **Export** Option.

3. Führen Sie in einer PowerShell [-Sitzung Import-aipscannerconfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) aus, und geben Sie die Datei an, die die exportierten Einstellungen enthält.

### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Wenn Sie die sysadmin-Rolle *vorübergehend* zur Installation der Überprüfung erhalten können, können Sie diese Rolle entfernen, wenn die Überprüfung des Scanners beendet ist.

Führen Sie je nach den Anforderungen Ihrer Organisation einen der folgenden Schritte aus:

- **Die sysadmin-Rolle kann vorübergehend vorhanden sein.** Wenn Sie vorübergehend über die sysadmin-Rolle verfügen, wird die Datenbank automatisch für Sie erstellt, und dem Dienst Konto für den Scanner werden automatisch die erforderlichen Berechtigungen erteilt.

    Das Benutzerkonto, das die Überprüfung konfiguriert, erfordert jedoch weiterhin die **db_owner** Rolle für die scannerkonfigurationsdatenbank. Wenn Sie nur über die sysadmin-Rolle verfügen, bis die Überprüfung des Scanners fertiggestellt ist, erteilen Sie dem [Benutzerkonto die db_owner Rolle manuell](#create-a-user-and-grant-db_owner-rights-manually).

- **Sie können nicht über die sysadmin-Rolle verfügen.** Wenn Sie die sysadmin-Rolle nicht auch vorübergehend erhalten können, müssen Sie einen Benutzer mit sysadmin-Berechtigung bitten, vor der Installation des Scanners manuell eine Datenbank zu erstellen. 

    Für diese Konfiguration muss die **db_owner** Rolle den folgenden Konten zugewiesen werden: 

    - Dienstkonto für die Überprüfung

    - Benutzerkonto für die Scannerinstallation

    - Benutzerkonto für die Konfiguration der Überprüfung
      
    In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie unterschiedliche Konten verwenden, benötigen beide die db_owner Rolle für die scannerkonfigurationsdatenbank. Erstellen Sie diesen Benutzer und die Rechte bei Bedarf. 

    Wenn Sie keinen eigenen Cluster Namen (Profilnamen) für die Überprüfung angeben, wird die Konfigurations Datenbank mit dem Namen **AIPScanner_ \<computer_name>** benannt. </br>Setzen Sie [die Erstellung eines Benutzers fort, und erteilen Sie db_owner Rechte für die Datenbank](#create-a-user-and-grant-db_owner-rights-manually). 

Darüber hinaus gilt:

- Sie müssen ein lokaler Administrator auf dem Server sein, auf dem die Überprüfung ausgeführt wird.
- Das Dienst Konto, unter dem der Scanner ausgeführt wird, muss über Vollzugriff auf die folgenden Registrierungsschlüssel verfügen:
    
    - HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\Server
    - HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server

Wenn nach dem Konfigurieren dieser Berechtigungen ein Fehler angezeigt wird, wenn Sie den Scanner installieren, kann der Fehler ignoriert werden, und Sie können den Überprüfungs Dienst manuell starten.

#### <a name="populate-the-database-manually"></a>Manuelles Auffüllen der Datenbank

Füllen Sie die Datenbank mit dem folgenden Skript auf: 

```sql
if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END 
```

#### <a name="create-a-user-and-grant-db_owner-rights-manually"></a>Erstellen Sie einen Benutzer, und erteilen Sie db_owner Rechte manuell.

Um einen Benutzer zu erstellen und db_owner Berechtigungen für diese Datenbank zu erteilen, bitten Sie den sysadmin, folgende Aufgaben durchzuführen:

1. Erstellen Sie eine Datenbank für Scanner:

    ```sql
    **CREATE DATABASE AIPScannerUL_[clustername]**
    
    **ALTER DATABASE AIPScannerUL_[clustername] SET TRUSTWORTHY ON**
    ```
    
2. Erteilen Sie dem Benutzer, der den Installations Befehl ausführt, Rechte, und wird zum Ausführen von Überprüfungs Verwaltungs Befehlen verwendet.

    SQL-Skript:
    
    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    USE DBName IF NOT EXISTS (select * from sys.database_principals where sid = SUSER_SID('domain\user')) BEGIN declare @X nvarchar(500) Set @X = 'CREATE USER ' + quotename('domain\user') + ' FROM LOGIN ' + quotename('domain\user'); exec sp_addrolemember 'db_owner', 'domain\user' exec(@X) END
    ```

3. Erteilen Sie die Rechte für das Scanner-Dienst Konto.

    SQL-Skript:

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    ```

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Einschränkung: Die Berechtigung zur **lokalen Anmeldung** kann nicht für das Dienstkonto gewährt werden.

Wenn Ihre Organisations Richtlinien das Recht " **Lokal anmelden** " für Dienst Konten nicht zulassen, aber das Recht " **Anmelden als Batch Auftrag** " zulassen, finden Sie weitere Informationen unter [angeben und Verwenden des Token-Parameters für "Set-aipauthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)".

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Verwenden Sie **für das Scanner-Dienst Konto** ein lokales Windows-Konto oder ein Active Directory Konto.

- Geben Sie **für das Azure Active Directory Konto** [den tokenparameter für "Set-aipauthentication" an, und verwenden](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication)Sie ihn.

#### <a name="restriction-your-labels-do-not-have-auto-labeling-conditions"></a>Einschränkung: ihre Bezeichnungen haben keine automatischen Beschriftungs Bedingungen.

Wenn Ihre Bezeichnungen keine automatischen Bezeichnungen aufweisen, sollten Sie beim Konfigurieren Ihres Scanners eine der folgenden Optionen verwenden:

|Option  |BESCHREIBUNG  |
|---------|---------|
|**Alle Informationstypen ermitteln**     |  Legen Sie in Ihrem [inhaltscanauftrag](deploy-aip-scanner-configure-install.md#create-a-content-scan-job)die Option zu **ermittelnde Informationstypen** auf **alle** fest. </br></br>Mit dieser Option wird der Inhalts Überprüfungs Auftrag so festgelegt, dass der Inhalt auf alle sensiblen Informationstypen überprüft wird.      |
|**Definieren einer Standard Bezeichnung**     |   Definieren Sie eine Standard Bezeichnung in der [Richtlinie](/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do), im [Inhalts Scanauftrag](deploy-aip-scanner-configure-install.md#create-a-content-scan-job)oder im [Repository](deploy-aip-scanner-configure-install.md#apply-a-default-label-to-all-files-in-a-data-repository). </br></br>In diesem Fall wendet der Scanner die Standard Bezeichnung auf alle gefundenen Dateien an.       |
| | |

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich vergewissert haben, dass Ihr System die Überprüfungs Voraussetzungen erfüllt, fahren Sie mit dem bereitstellen [des Azure Information Protection Scanners fort, um Dateien automatisch zu klassifizieren und zu schützen](deploy-aip-scanner-configure-install-classic.md)

Eine Übersicht über den Scanner finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner-classic.md).

**Weitere Informationen**:

Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs-classic.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem klassischen Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md)