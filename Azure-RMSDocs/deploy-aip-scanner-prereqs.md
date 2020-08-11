---
title: Voraussetzungen für den einheitlichen Bezeichnungs Scanner Azure Information Protection (AIP)
description: Listet die Voraussetzungen für die Installation und Bereitstellung des Azure Information Protection Unified Beschriftung Scanner auf.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/24/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 38489d1d1ff7183e5e7a3963b401cdaecf2313dc
ms.sourcegitcommit: e6b594b8d15f81884b0999f5c0009386aef02cc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2020
ms.locfileid: "88073651"
---
# <a name="prerequisites-for-installing-and-deploying-the-azure-information-protection-unified-labeling-scanner"></a>Voraussetzungen für die Installation und Bereitstellung der Azure Information Protection Unified-Beschriftungs Scanner

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2*

>[!NOTE]
> Wenn Sie mit dem klassischen Scanner arbeiten, finden Sie weitere Informationen unter [Voraussetzungen für die Installation und Bereitstellung des Azure Information Protection klassischen Scanner](deploy-aip-scanner-prereqs-classic.md).

Vergewissern Sie sich vor der Installation des Azure Information Protection Scanners, dass Ihr System die folgenden Anforderungen erfüllt:

- [Windows Server-Anforderungen](#windows-server-requirements)
- [Dienstkontenanforderungen](#service-account-requirements)
- [SQL Server-Anforderungen](#sql-server-requirements)
- [Azure Information Protection Client Anforderungen](#azure-information-protection-client-requirements)
- [Bezeichnungs Konfigurations Anforderungen](#label-configuration-requirements)
- [SharePoint-Anforderungen](#sharepoint-requirements)
- [Microsoft Office Anforderungen](#microsoft-office-requirements)
- [Dateipfad-Anforderungen](#file-path-requirements)
- [Anforderungen an die Nutzungsstatistik](#usage-statistics-requirements)

Wenn Sie nicht alle Anforderungen in der Tabelle erfüllen können, weil Sie von ihren Organisations Richtlinien nicht zugelassen werden, lesen Sie den Abschnitt [Alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations) .

Wenn Sie den Scanner in der Produktionsumgebung bereitstellen oder die Leistung mehrerer Scanner testen, finden Sie weitere Informationen unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

Wenn Sie bereit sind, mit der Installation und Bereitstellung Ihres Scanners zu beginnen, können Sie mit der Bereitstellung [des Azure Information Protection Scanners fortfahren, um Dateien automatisch zu klassifizieren](deploy-aip-scanner-configure-install.md)

## <a name="windows-server-requirements"></a>Windows Server-Anforderungen

Sie müssen über einen Windows Server-Computer verfügen, auf dem die Überprüfung ausgeführt werden kann. diese verfügt über die folgenden Systemspezifikationen:

|Spezifikation  |Details  |
|---------|---------|
|**Prozessor**     |4-Kern Prozessoren         |
|**RAM**     |8 GB         |
|**Speicherplatz**     |10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien. </br></br>Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. </br></br>Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen.
|**Betriebssystem**     |-Windows Server 2019 </br>- Windows Server 2016 </br>Windows Server 2012 R2 </br></br>**Hinweis:** Zu Test-oder Evaluierungs Zwecken in einer nicht-Produktionsumgebung können Sie auch ein beliebiges Windows-Betriebssystem verwenden, das [vom Azure Information Protection-Client unterstützt](requirements.md#client-devices)wird.
|**Netzwerkverbindungen**     | Bei dem Überprüfungs Computer kann es sich um einen physischen oder virtuellen Computer mit einer schnellen und zuverlässigen Netzwerkverbindung mit den zu überprüfenden Daten speichern handeln. </br></br> Wenn die Internetverbindung aufgrund ihrer Organisations Richtlinien nicht möglich ist, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations). </br></br>Stellen Sie andernfalls sicher, dass dieser Computer über eine Internetverbindung verfügt, die die folgenden URLs über HTTPS (Port 443) zulässt:</br><br />-  \*. aadrm.com <br />-  \*. azurerms.com<br />-  \*. informationprotection.Azure.com <br /> -informationprotection.Hosting.Portal.Azure.net <br /> - \*. Aria.Microsoft.com <br />-  \*. Protection.Outlook.com |
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
|**Berechtigungen für die Daten Depots**     |- **Dateifreigaben oder lokale Dateien:** Erteilen **Sie Lese**-, **Schreib**-und **Änderungs Berechtigungen zum** Scannen der Dateien und zum anschließenden anwenden der Klassifizierung und des Schutzes entsprechend der Konfiguration.  <br /><br />- **SharePoint:** Erteilen Sie **voll** Zugriffsberechtigungen für das Scannen der Dateien, und wenden Sie dann die Klassifizierung und den Schutz wie konfiguriert an.  <br /><br />- Ermittlungs **Modus:** Die **Lese** Berechtigung ist ausreichend, um die Überprüfung nur im Ermittlungs Modus auszuführen.         |
|**Für Bezeichnungen, die den Schutz erneut schützen oder entfernen**     | Um sicherzustellen, dass die Überprüfung stets Zugriff auf geschützte Dateien hat, machen Sie dieses Konto als [Administrator für Azure Information Protection](configure-super-users.md) , und stellen Sie sicher, dass die Administrator Funktion aktiviert ist. </br></br>Wenn Sie [Onboarding](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) -Steuerelemente für eine stufenweise Bereitstellung implementiert haben, stellen Sie außerdem sicher, dass das Dienst Konto in den Onboarding-Steuerelementen enthalten ist, die Sie konfiguriert haben.|
| ||

## <a name="sql-server-requirements"></a>SQL Server-Anforderungen

Verwenden Sie zum Speichern der Überprüfungs Konfigurationsdaten einen SQL-Server mit den folgenden Anforderungen:

- **Eine lokale Instanz oder eine Remote Instanz.**

    Es wird empfohlen, den SQL Server-und Scanner-Dienst auf verschiedenen Computern zu verwenden, es sei denn, Sie arbeiten mit einer kleinen Bereitstellung.

    SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:

    - SQL Server Enterprise
    - SQL Server Standard
    - SQL Server Express (nur für Testumgebungen empfohlen)

- **Ein Konto mit der sysadmin-Rolle zum Installieren des Scanners.**

    Die sysadmin-Rolle ermöglicht dem Installationsvorgang das automatische Erstellen der Überprüfungs Konfigurationsdatenbank und das Erteilen der erforderlichen **db_owner** Rolle für das Dienst Konto, von dem die Überprüfung ausgeführt wird.

    Wenn Ihnen die sysadmin-Rolle nicht gewährt werden kann oder wenn Ihre Organisations Richtlinien erfordern, dass Datenbanken manuell erstellt und konfiguriert werden, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

- **Capacity** (Kapazität): Informationen zur Kapazitäts Orientierung finden Sie unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

- **[Sortierung ohne Beachtung](https://docs.microsoft.com/sql/relational-databases/collations/collation-and-unicode-support?view=sql-server-ver15)**

> [!NOTE]
> Mehrere Konfigurations Datenbanken auf demselben SQL Server werden unterstützt, wenn Sie einen benutzerdefinierten Cluster Namen (Profil) für die Überprüfung angeben oder wenn Sie die Vorschauversion der Überprüfung verwenden.
>
### <a name="storage-requirements-and-capacity-planning-for-sql-server"></a>Speicheranforderungen und Kapazitätsplanung für SQL Server

Der erforderliche Speicherplatz für die Konfigurations Datenbank des Scanners und die Angabe des Computers, auf dem SQL Server ausgeführt wird, kann je nach Umgebung variieren. Daher empfehlen wir Ihnen, ihre eigenen Tests durchzuführen. Verwenden Sie die folgende Anleitung als Ausgangspunkt.

Weitere Informationen finden Sie unter [Optimieren der Leistung des Scanners](deploy-aip-scanner-configure-install.md#optimizing-scanner-performance).

Die Datenträger Größe für die scannerkonfigurationsdatenbank variiert für jede Bereitstellung. Verwenden Sie die folgende Gleichung als Leitfaden:

```cli
100 KB + <file count> *(1000 + 4* <average file name length>)
```

Um z. b. 1 Million Dateien mit einer durchschnittlichen Dateinamen Länge von 250 Bytes zu scannen, müssen Sie 2 GB Speicherplatz zuweisen.

Für mehrere Scanner:

- **Bis zu 10 Scanner, verwenden Sie** Folgendes:

    - 4-Kern Prozessoren
    - 8 GB RAM empfohlen

- **Mehr als 10 Scanner** (max. 40), verwenden Sie Folgendes:
    - 8-Kern-Prozesse
    - 16 GB RAM empfohlen

## <a name="azure-information-protection-client-requirements"></a>Azure Information Protection Client Anforderungen

Auf dem Windows Server-Computer muss entweder die [aktuelle Version der allgemeinen Verfügbarkeit](./rms-client/unifiedlabelingclient-version-release-history.md) des Azure Information Protection-Clients installiert sein.

Weitere Informationen finden Sie unter [Unified Bezeichnung Client Admin Guide](./rms-client/clientv2-admin-guide.md#installing-the-azure-information-protection-scanner).

> [!IMPORTANT]
> Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.
>

## <a name="label-configuration-requirements"></a>Bezeichnungs Konfigurations Anforderungen

Sie müssen Bezeichnungen konfiguriert haben, die automatisch Klassifizierung und optional Schutz anwenden.

Wenn Sie diese Bezeichnungen nicht konfiguriert haben, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

Weitere Informationen finden Sie unter

- [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf Inhalte](https://docs.microsoft.com/microsoft-365/compliance/apply-sensitivity-label-automatically)
- [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels)

## <a name="sharepoint-requirements"></a>SharePoint-Anforderungen

Stellen Sie sicher, dass Ihr SharePoint-Server die folgenden Anforderungen erfüllt, um SharePoint-Dokument Bibliotheken und-Ordner zu überprüfen:

- **Unterstützte Versionen.** Folgende Versionen werden unterstützt: SharePoint 2019, SharePoint 2016, SharePoint 2013 und SharePoint 2010. Andere Versionen von SharePoint werden für die Überprüfung nicht unterstützt.

- **Versionsverwaltung.** Wenn Sie die [Versions](https://docs.microsoft.com/sharepoint/governance/versioning-content-approval-and-check-out-planning)Verwaltung verwenden, wird die zuletzt veröffentlichte Version vom Scanner überprüft und beschriftet. Wenn die Überprüfung eine Datei und eine [Genehmigung von Inhalten](https://docs.microsoft.com/sharepoint/governance/versioning-content-approval-and-check-out-planning#plan-content-approval) erfordert, muss die bezeichnete Datei als verfügbar für Benutzer verfügbar sein.  

- **Große SharePoint-Farmen.** Überprüfen Sie für große SharePoint-Farmen, ob Sie den Schwellwert der Listenansicht (standardmäßig 5.000) erhöhen müssen, damit der Scanner auf alle Dateien zugreifen kann. Weitere Informationen finden Sie unter [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).

## <a name="microsoft-office-requirements"></a>Microsoft Office Anforderungen

Zum Scannen von Office-Dokumenten müssen Ihre Dokumente in einem der folgenden Formate vorliegen:

- Microsoft Office 97-2003
- Office Open XML-Formate für Word, Excel und PowerPoint

Weitere Informationen finden Sie [unter vom Azure Information Protection Unified Bezeichnung-Client unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md).

## <a name="file-path-requirements"></a>Dateipfad-Anforderungen

Zum Scannen von Dateien müssen standardmäßig die Dateipfade maximal 260 Zeichen enthalten.

Zum Überprüfen von Dateien mit Dateipfaden mit mehr als 260 Zeichen installieren Sie die Überprüfung auf einem Computer mit einer der folgenden Windows-Versionen, und konfigurieren Sie den Computer nach Bedarf:

|Windows-Version  |BESCHREIBUNG  |
|---------|---------|
|**Windows 2016 oder höher**     |   Konfigurieren des Computers zur Unterstützung von langen Pfaden      |
|**Windows 10 oder Windows Server 2016**     | Definieren Sie die folgende [Gruppenrichtlinien Einstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/): **lokale Computer Richtlinie**  >  **Computerkonfiguration**  >  **Administrative Vorlagen**  >  **alle Einstellungen**  >  **aktivieren Win32 Long-Pfade**.    </br></br>Weitere Informationen zur Unterstützung von langen Dateipfaden in diesen Versionen finden Sie im Abschnitt [Maximale Pfadlängen Beschränkung](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Windows 10-Entwicklerdokumentation.    |
|**Windows 10, Version 1607 oder höher**     |  Entscheiden Sie sich für die aktualisierten **MAX_PATH** Funktionen. Weitere Informationen finden Sie unter [Aktivieren von langen Pfaden in Windows 10, Version 1607 und](https://docs.microsoft.com/windows/win32/fileio/naming-a-file#enable-long-paths-in-windows-10-version-1607-and-later)höher.      |
| | |
## <a name="usage-statistics-requirements"></a>Anforderungen an die Nutzungsstatistik

Deaktivieren Sie Verwendungs Statistiken mithilfe einer der folgenden Methoden:

- Festlegen des [allowtelemetry](https://docs.microsoft.com/azure/information-protection/rms-client/client-admin-guide-install#to-install-the-azure-information-protection-client-by-using-the-executable-installer) -Parameters auf 0

- Stellen Sie sicher, dass die Option zur **Verbesserung der Azure Information Protection durch das Senden von Nutzungsstatistiken an Microsoft** während der Überprüfung der Installation nicht ausgewählt ist.

## <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die oben aufgeführten Voraussetzungen sind die Standardanforderungen für die Scanner-Bereitstellung und werden empfohlen, da Sie die einfachste Überprüfungs Konfiguration unterstützen.

Die Standardanforderungen sollten für die ersten Tests geeignet sein, damit Sie die Funktionen des Scanners überprüfen können.

In einer Produktionsumgebung können diese Standardanforderungen in den Richtlinien Ihrer Organisation jedoch untersagt werden. Der Scanner kann die folgenden Einschränkungen mit zusätzlicher Konfiguration erfüllen:

- [Der Überprüfungs Server kann keine Internetverbindung haben.](#restriction-the-scanner-server-cannot-have-internet-connectivity)

- [Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.](#restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity)

- [Einschränkung: dem Dienst Konto für die Überprüfung kann nicht die Berechtigung zum **lokalen anmelden** erteilt werden.](#restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right)

- [Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.](#restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually)

### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Einschränkung: der Überprüfungs Server kann keine Internetverbindung haben.

Führen Sie die folgenden Schritte aus, um einen getrennten Computer zu unterstützen:

1. Konfigurieren Sie Bezeichnungen in der Richtlinie, und importieren Sie dann die Richtlinie mithilfe des Cmdlets [Import-aipscannerconfiguration](https://docs.microsoft.com/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration?view=azureipps) . Obwohl der Unified Label-Client keinen Schutz ohne Internetverbindung anwenden kann, kann der Scanner weiterhin Bezeichnungen auf der Grundlage importierter Richtlinien anwenden.

1. Konfigurieren Sie die Überprüfung im Azure-Portal, indem Sie einen scannercluster erstellen. Unterstützung zu diesem Schritt finden Sie im Abschnitt [Konfigurieren des Scanners im Azure-Portal](deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal).

1. Exportieren Sie den Inhalts Auftrag aus dem Bereich **Azure Information Protection-Inhalts Scanaufträge** mithilfe der **Export** Option.

1. Führen Sie in einer PowerShell [-Sitzung Import-aipscannerconfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) aus, und geben Sie die Datei an, die die exportierten Einstellungen enthält.

### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Wenn Sie die sysadmin-Rolle *vorübergehend* zur Installation der Überprüfung erhalten können, können Sie diese Rolle entfernen, wenn die Überprüfung des Scanners beendet ist.

Führen Sie je nach den Anforderungen Ihrer Organisation einen der folgenden Schritte aus:

- **Die sysadmin-Rolle kann vorübergehend vorhanden sein.** Wenn Sie vorübergehend über die sysadmin-Rolle verfügen, wird die Datenbank automatisch für Sie erstellt, und dem Dienst Konto für den Scanner werden automatisch die erforderlichen Berechtigungen erteilt.

    Das Benutzerkonto, das die Überprüfung konfiguriert, erfordert jedoch weiterhin die **db_owner** Rolle für die scannerkonfigurationsdatenbank. Wenn Sie nur über die sysadmin-Rolle verfügen, bis die Überprüfung des Scanners fertiggestellt ist, erteilen Sie dem [Benutzerkonto die db_owner Rolle manuell](#create-a-user-and-grant-db_owner-rights-manually).

- **Sie können nicht über die sysadmin-Rolle verfügen**. Wenn Sie die sysadmin-Rolle nicht auch vorübergehend erhalten können, müssen Sie einen Benutzer mit sysadmin-Berechtigung bitten, vor der Installation des Scanners manuell eine Datenbank zu erstellen.

    Für diese Konfiguration muss die **db_owner** Rolle den folgenden Konten zugewiesen werden:

    - Dienstkonto für die Überprüfung
    - Benutzerkonto für die Scannerinstallation
    - Benutzerkonto für die Konfiguration der Überprüfung

    In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie unterschiedliche Konten verwenden, benötigen beide die db_owner Rolle für die scannerkonfigurationsdatenbank. Erstellen Sie diesen Benutzer und die Rechte bei Bedarf. Wenn Sie einen eigenen Cluster Namen (Profilnamen) angeben, wird die Konfigurations Datenbank **AIPScannerUL_<cluster_name>** benannt.

Außerdem zu beachten:

- Sie müssen ein lokaler Administrator auf dem Server sein, auf dem die Überprüfung ausgeführt wird.
- Das Dienst Konto, unter dem der Scanner ausgeführt wird, muss über Vollzugriff auf die folgenden Registrierungsschlüssel verfügen:

    - HKEY_LOCAL_MACHINE \software\wow6432node \microsoft\msipc\server
    - HKEY_LOCAL_MACHINE \software\microsoft\msipc\server

Wenn nach dem Konfigurieren dieser Berechtigungen ein Fehler angezeigt wird, wenn Sie den Scanner installieren, kann der Fehler ignoriert werden, und Sie können den Überprüfungs Dienst manuell starten.

#### <a name="populate-the-database-manually"></a>Manuelles Auffüllen der Datenbank

Füllen Sie die Datenbank mit dem folgenden Skript auf:

```cli
if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END 
```

#### <a name="create-a-user-and-grant-db_owner-rights-manually"></a>Erstellen Sie einen Benutzer, und erteilen Sie db_owner Rechte manuell.

Um einen Benutzer zu erstellen und db_owner Berechtigungen für diese Datenbank zu erteilen, bitten Sie den sysadmin, die folgenden Schritte auszuführen:

1. Erstellen Sie eine Datenbank für Scanner:

    ```cli
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

Wenn Ihre Organisations Richtlinien das Recht " **Lokal anmelden** " für Dienst Konten nicht zulassen, aber das Recht " **Anmelden als Batch Auftrag** " zulassen, verwenden Sie den Parameter " *onbehalfof* " mit "Set-aipauthentication".

Weitere Informationen finden Sie unter Vorgehens [Weise beim nicht interaktiven bezeichnen von Dateien für Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Verwenden Sie **für das Scanner-Dienst Konto** ein lokales Windows-Konto oder ein Active Directory Konto.

- Geben Sie **für das Azure Active Directory-Konto** Ihr lokales Konto für den *onbehalfof* -Parameter mit "Set-aipauthentication" an. Weitere Informationen finden Sie unter Vorgehens [Weise beim nicht interaktiven bezeichnen von Dateien für Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich vergewissert haben, dass Ihr System die Überprüfungs Voraussetzungen erfüllt, fahren Sie mit dem bereitstellen [des Azure Information Protection Scanners fort, um Dateien automatisch zu klassifizieren und zu schützen](deploy-aip-scanner-configure-install.md)

Eine Übersicht über den Scanner finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).

**Weitere Informationen:**

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Vielleicht Fragen Sie sich: [worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).
