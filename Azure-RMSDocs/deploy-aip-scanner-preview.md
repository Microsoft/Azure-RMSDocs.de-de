---
title: Bereitstellen des Azure Information Protection-Scanners (VORSCHAU)
description: Anleitung zum Installieren, Konfigurieren und Ausführen der aktuellen Vorschauversion des Azure Information Protection-Scanners, um Dateien in Datenspeichern zu suchen, zu klassifizieren und zu schützen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/13/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: demizets
ms.suite: ems
ms.openlocfilehash: b8ae2b2bb60e531bfa1ee5eba0e64abd9fdea9e0
ms.sourcegitcommit: 4ed27f50545aae1a58cc922202959d427bcba7ac
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/16/2019
ms.locfileid: "56323664"
---
# <a name="deploying-the-preview-version-of-the-azure-information-protection-scanner-to-automatically-classify-and-protect-files"></a>Bereitstellen der Vorschauversion des Azure Information Protection-Scanners zum automatischen Klassifizieren und Schützen von Dateien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2*

> [!NOTE]
> Dieser Artikel ist für die aktuelle Vorschauversion des Azure Information Protection-Scanners bestimmt. Vorschauversionen unterliegen Änderungen.
> 
> Eine Anleitung zur Bereitstellung für die allgemein verfügbare Version des Scanners finden Sie unter [Bereitstellen der Azure Information Protection-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md).
> 
> Wenn Sie ein Upgrade von einer allgemein verfügbaren Version des Scanners auf die Vorschauversion ausführen, lesen Sie [Upgrade der Azure Information Protection-Überprüfung](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).

In diesem Artikel erfahren Sie mehr über den Azure Information Protection-Scanner und dessen erfolgreiche Installation, Konfiguration und Ausführung. 

Diese Überprüfung wird als Dienst unter Windows Server ausgeführt und bietet Ihnen die Möglichkeit, Dateien auf den folgenden Datenspeichern zu suchen, zu klassifizieren und zu schützen:

- Lokale Ordner auf dem Windows Server-Computer, auf dem die Überprüfung ausgeführt wird

- UNC-Pfade zu Netzwerkfreigaben mit dem Server Message Block (SMB)-Protokoll.

- Websites und Bibliotheken für SharePoint Server 2016 und SharePoint Server 2013 SharePoint 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.

Verwenden Sie zum Überprüfen und Bezeichnen von Dateien auf Cloudrepositorys [Cloud App Security](https://docs.microsoft.com/cloud-app-security/) anstelle des Scanners.

## <a name="overview-of-the-azure-information-protection-scanner"></a>Übersicht über die Azure Information Protection-Überprüfung

Wenn Sie Ihre [Azure Information Protection-Richtlinie](configure-policy.md) für Bezeichnungen konfiguriert haben, die automatisch klassifizieren, können von der Überprüfung gefundene Dateien gekennzeichnet werden. Bezeichnungen wenden Klassifizierungen sowie optional Schutz an, der auch entfernt werden kann:

![Übersicht über die Architektur der Azure Information Protection-Überprüfung](./media/infoprotect-scanner.png)

Die Überprüfung kann jede Datei überprüfen, die von Windows indiziert werden kann. Dazu verwendet sie IFilters, die auf dem Computer installiert sind. Um zu bestimmen, ob die Dateien Bezeichnungen benötigen, verwendet die Überprüfung die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP) oder Regex-Muster von Office 365. Da die Überprüfung den Azure Information Protection-Client verwendet, kann sie dieselben [Dateitypen](./rms-client/client-admin-guide-file-types.md) klassifizieren und schützen.

Sie können die Überprüfung im Suchmodus ausführen. In diesem Modus überprüfen Sie anhand der Berichte, was geschähe, wenn die Dateien bezeichnet würden. Alternativ können Sie die Bezeichnungen mit der Überprüfung automatisch anwenden. Sie können die Überprüfung auch zum Ermitteln von Dateien mit vertraulichen Informationstypen ausführen, ohne Bezeichnungen für Bedingungen zu konfigurieren, die die automatische Klassifizierung anwenden.

Beachten Sie, dass die Überprüfung nicht in Echtzeit sucht und bezeichnet. Sie durchforstet systematisch Dateien auf Datenspeichern, die Sie angeben, und Sie können konfigurieren, ob dieser Zyklus einmal oder mehrmals ausgeführt wird.

Sie können angeben, welche Dateitypen überprüft oder vom Scanvorgang ausgeschlossen werden sollen, indem Sie im Rahmen der Scannerkonfiguration eine Dateitypenliste definieren.


## <a name="prerequisites-for-the-azure-information-protection-scanner"></a>Voraussetzungen für die Azure Information Protection-Überprüfung
Stellen Sie vor der Installation der Azure Information Protection-Überprüfung sicher, dass folgende Voraussetzungen erfüllt sind.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Windows Server-Computer zum Ausführen des Überprüfungsdiensts:<br /><br />- Prozessoren mit 4 Kernen<br /><br />– 8 GB RAM<br /><br />- 10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien|Windows Server 2016 oder Windows Server 2012 R2 <br /><br />Hinweis: Sie können zu Test- oder Auswertungszwecken ein Windows-Clientbetriebssystem in einer Testumgebung verwenden, das [vom Azure Information Protection-Client unterstützt](requirements.md#client-devices) wird.<br /><br />Dieser Computer kann ein physischer oder ein virtueller Computer mit einer schnellen und zuverlässigen Netzwerkverbindung zu den Datenspeichern sein, die überprüft werden sollen.<br /><br /> Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen. <br /><br />Wenn aufgrund Ihrer Organisationsrichtlinien keine Internetkonnektivität möglich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations). Andernfalls stellen Sie sicher, dass dieser Computer über eine Internetverbindung verfügt, die die folgenden URLs zulässt:<br /> \*.aadrm.com <br /> \*.azurerms.com<br /> \*.informationprotection.azure.com <br /> informationprotection.hosting.portal.azure.net <br /> \*.aria.microsoft.com|
|Dienstkonto zum Ausführen der Überprüfung|Über das Ausführen des Überprüfungsdiensts auf dem Windows-Servercomputer hinaus wird dieses Windows-Konto auch bei Azure AD authentifiziert und lädt die Azure Information Protection-Richtlinie herunter. Dieses Konto muss ein Active Directory-Konto sein und mit Azure AD synchronisiert werden. Wenn Sie dieses Konto aufgrund Ihrer Organisationsrichtlinien nicht synchronisieren können, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Für dieses Dienstkonto gelten die folgenden Anforderungen:<br /><br />- **Lokale Anmeldung** für die Zuweisung von Benutzerrechten. Diese Berechtigung ist für die Installation und Konfiguration der Überprüfung erforderlich, aber nicht für den Vorgang selbst. Sie müssen dem Dienstkonto diese Berechtigung gewähren und können sie wieder entfernen, nachdem Sie überprüft haben, dass die Überprüfung Dateien suchen, klassifizieren und schützen kann. Wenn die Gewährung dieser Berechtigung selbst für einen kurzen Zeitraum aufgrund Ihrer Organisationsrichtlinien nicht möglich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />- **Anmeldung als Dienst** für die Zuweisung von Benutzerrechten. Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich. <br /><br />– Berechtigungen für die Datenrepositorys: Sie müssen **Lese-** und **Schreibberechtigungen** für das Überprüfen, Klassifizieren und Schützen der Dateien erteilen, damit die Dateien die Bedingungen der Azure Information Protection-Richtlinie erfüllen. Um die Überprüfung nur im Suchmodus auszuführen, genügt eine **Leseberechtigung**.<br /><br />– Für Bezeichnungen, die Schutz erneut anwenden oder ihn entfernen: Um sicherzustellen, dass die Überprüfung stets Zugriff auf geschützte Dateien hat, muss dieses Konto im Azure Rights Management-Dienst ein [Administrator](configure-super-users.md) sein. Stellen Sie außerdem sicher, dass die Administratorfunktion aktiviert ist. Weitere Informationen zu den Kontoanforderungen zum Anwenden von Schutz finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md). Wenn Sie darüber hinaus [Onboarding-Steuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) für eine stufenweise Bereitstellung implementiert haben, stellen Sie sicher, dass dieses Konto in den von Ihnen konfigurierten Onboarding-Steuerelementen enthalten ist.|
|SQL-Server, auf dem die Konfiguration der Überprüfung gespeichert wird:<br /><br />- Lokale oder Remoteinstanz<br /><br />– Sysadmin-Rolle zum Installieren der Überprüfung|SQL Server 2012 ist die mindestens erforderliche Version für die folgenden Editionen:<br /><br />- SQL Server Enterprise<br /><br />- SQL Server Standard<br /><br />- SQL Server Express<br /><br />Vom Azure Information Protection-Scanner werden beim Angeben eines benutzerdefinierten Profilnamens für den Scanner mehrere Konfigurationsdatenbanken auf einer SQL Server-Instanz unterstützt.<br /><br />Wenn Sie den Scanner installieren und Ihr Konto über die Sysadmin-Rolle verfügt, wird während des Installationsprozesses automatisch die Konfigurationsdatenbank des Scanners erstellt und dem Dienstkonto, das den Scanner ausführt, die erforderliche Db_owner-Rolle gewährt. Wenn die Sysadmin-Rolle nicht gewährt wird oder aufgrund der Richtlinien Ihrer Organisation die manuelle Erstellung und Konfiguration von Datenbanken erforderlich ist, finden Sie weitere Informationen in Abschnitt [Bereitstellen der Überprüfung mit alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations).<br /><br />Die Größe der Konfigurationsdatenbank variiert je nach Bereitstellung. Allerdings empfehlen wir, 500 MB je 1.000.000 zu überprüfende Dateien zuzuordnen. |
|Die Vorschauversion des Azure Information Protection-Clients ist auf dem Windows Server-Computer installiert.|Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.<br /><br />Eine Anleitung zum Installieren des Clients finden Sie im [Administratorhandbuch](./rms-client/client-admin-guide.md). Wenn Sie die Überprüfung bereits installiert haben und nun auf eine neuere Version aktualisieren müssen, finden Sie weitere Informationen hierzu unter [Aktualisieren der Azure Information Protection-Überprüfung](./rms-client/client-admin-guide.md#upgrading-the-azure-information-protection-scanner).|
|Konfigurierte Bezeichnungen, die automatische Klassifizierung und optional Schutz anwenden|Informationen zum Konfigurieren einer Bezeichnung für Bedingungen und zum Anwenden von Schutz:<br /> - [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)<br /> - [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md) <br /><br />Tipp: Sie können die Anweisungen im [Tutorial](infoprotect-quick-start-tutorial.md) verwenden, um den Scanner mit einer Bezeichnung zu testen, mit der in einem vorbereiteten Word-Dokument nach Kreditkartennummern gesucht wird. Sie müssen jedoch die Bezeichnungskonfiguration ändern, sodass die Option **Wählen Sie aus, wie diese Bezeichnung angewendet wird** auf **Automatisch** und nicht auf **als Empfehlung** festgelegt wird. Entfernen Sie anschließend die Bezeichnung vom Dokument (sofern angewendet), und kopieren Sie die Datei in ein Datenrepository für den Scanner. Bei einem schnellen Test kann dies ein lokaler Ordner auf dem Computer mit dem Scanner sein.<br /><br /> Zwar können Sie die Überprüfung auch dann ausführen, wenn Sie über keine konfigurierten Bezeichnungen verfügen, die die automatische Klassifizierung anwenden, dieses Szenario wird in der vorliegenden Anleitung jedoch nicht behandelt. [Weitere Informationen](#using-the-scanner-with-alternative-configurations)|
|Für SharePoint-Websites und -Bibliotheken, die überprüft werden sollen:<br /><br />– SharePoint 2016<br /><br />– SharePoint 2013<br /><br />– SharePoint 2010|Andere Versionen von SharePoint werden für die Überprüfung nicht unterstützt.<br /><br />Überprüfen Sie für große SharePoint-Farmen, ob Sie den Schwellwert der Listenansicht (standardmäßig 5.000) erhöhen müssen, damit der Scanner auf alle Dateien zugreifen kann. Weitere Informationen finden Sie in der folgenden SharePoint-Dokumentation: [Manage large lists and libraries in SharePoint (Verwalten von großen Listen und Bibliotheken in SharePoint)](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server)|
|Für zu scannende Office-Dokumente:<br /><br />-97-2003-Dateiformate und die offene Office-XML-Formate für Word, Excel und PowerPoint|Weitere Informationen zu den Dateitypen, die vom Scanner für diese Dateiformate unterstützt werden, finden Sie unter [Vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md).|
|Für lange Pfade:<br /><br />– höchstens 260 Zeichen, es sei denn, der Scanner ist unter Windows 2016 installiert und der Computer ist für die Unterstützung von langen Pfaden konfiguriert|Windows 10 und Windows Server 2016 unterstützen Pfade, die mehr als 260 Zeichen umfassen, mit der folgenden [Gruppenrichtlinieneinstellung](https://blogs.msdn.microsoft.com/jeremykuhne/2016/07/30/net-4-6-2-and-long-paths-on-windows-10/): **Lokale Computerrichtlinie** > **Computerkonfiguration** > **Administrative Vorlagen** > **Alle Einstellungen** > **NTFS** > **Lange Win32-Pfade aktivieren**<br /><br /> Weitere Informationen zur Unterstützung von langen Dateipfaden finden Sie im Abschnitt [Maximum Path Length Limitation (Einschränkung der Pfadlänge)](https://docs.microsoft.com/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Entwicklerdokumentation für Windows 10.

Wenn Sie nicht alle Anforderungen in der Tabelle erfüllen können, da sie aufgrund der Richtlinien Ihrer Organisation nicht zulässig sind, finden Sie im nächsten Abschnitt Alternativen.

Wenn alle Voraussetzungen erfüllt sind, wechseln Sie direkt zum Abschnitt über die [Konfiguration des Scanners](#configure-the-scanner-in-the-azure-portal).

### <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die in der Tabelle aufgeführten Voraussetzungen sind die Standardanforderungen für die Überprüfung und werden empfohlen, da sie die einfachste Konfiguration für die Bereitstellung der Überprüfung sind. Sie sollten für die erste Testphase geeignet sein, damit Sie die Funktionen der Überprüfung überprüfen können. In einer Produktumgebung können aufgrund der Richtlinien Ihrer Organisation diese Standardanforderungen jedoch aufgrund einer oder mehrerer der folgenden Einschränkungen nicht zulässig sein:

- Server dürfen nicht mit dem Internet verbunden sein.

- Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

- Die Berechtigung zur **lokalen Anmeldung** kann nicht für Dienstkonten gewährt werden.

- Dienstkonten können nicht mit Azure Active Directory synchronisiert werden, Server verfügen jedoch über Internetkonnektivität.

Bei der Überprüfung können diese Einschränkungen zwar berücksichtigt werden, es ist jedoch eine zusätzliche Konfiguration erforderlich.


#### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Einschränkung: Der Überprüfungsserver kann über keine Internetkonnektivität verfügen.

Folgen Sie den Anweisungen für [nicht verbundene Computer](./rms-client/client-admin-guide-customizations.md#support-for-disconnected-computers). Führen Sie anschließend Folgendes aus:

1. Konfigurieren Sie den Scanner im Azure-Portal, indem Sie ein Scannerprofil erstellen. Unterstützung zu diesem Schritt finden Sie im Abschnitt [Konfigurieren des Scanners im Azure-Portal](#configure-the-scanner-in-the-azure-portal).

2. Exportieren Sie Ihr Scannerprofil über das Blatt **Azure Information Protection - Profiles (Preview)** (Azure Information Protection – Profile (Vorschau)) mithilfe der Option **Exportieren**.

3. Führen Sie schließlich das Cmdlet [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) in einer PowerShell-Sitzung aus, und geben Sie die Datei an, in der die exportierten Einstellungen enthalten sind.

Beachten Sie, dass die Überprüfung in dieser Konfiguration keinen Schutz durch den cloudbasierten Schlüssel Ihrer Organisation anwenden (oder entfernen) kann. Stattdessen ist die Überprüfung auf die Verwendung von Bezeichnungen beschränkt, für die ausschließlich die Klassifizierung verwendet wird, oder auf den Schutz mit [HYOK](configure-adrms-restrictions.md). 

#### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Wenn Ihnen die Sysadmin-Rolle zur vorübergehenden Installation der Überprüfung zugewiesen werden kann, können Sie diese Rolle nach der Installation der Überprüfung entfernen. Wenn Sie diese Konfiguration verwenden, wird die Datenbank automatisch für Sie erstellt, und das Dienstkonto für die Überprüfung erhält automatisch die erforderlichen Berechtigungen. Für das Benutzerkonto, mit dem der Scanner konfiguriert wird, wird jedoch die db_owner-Rolle für die Konfigurationsdatenbank des Scanners benötigt, und Sie müssen diese Rolle dem Benutzerkonto manuell zuweisen.

Wenn Ihnen die Sysadmin-Rolle auch nicht vorübergehend zugewiesen werden kann, müssen Sie vor der Installation des Scanners manuell eine Datenbank erstellen. Weisen Sie bei Verwendung dieser Konfiguration die folgenden Rollen zu:
    
|Konto|Rolle auf Datenbankebene|
|--------------------------------|---------------------|
|Dienstkonto für die Überprüfung|db_owner|
|Benutzerkonto für die Installation der Überprüfung|db_owner|
|Benutzerkonto für die Konfiguration der Überprüfung |db_owner|

In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie jedoch unterschiedliche Konten verwenden, benötigen beide die db_owner-Rolle für die Konfigurationsdatenbank des Scanners.

- Wenn Sie für den Scanner keinen eigenen Profilnamen angeben, erhält die Konfigurationsdatenbank den Namen **AIPScanner_\<Computername>**. 

- Wenn Sie einen eigenen Profilnamen angeben, erhält die Konfigurationsdatenbank den Namen **AIPScanner_\<Profilname>**.

#### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Einschränkung: Die Berechtigung zur **lokalen Anmeldung** kann nicht für das Überprüfungsdienstkonto gewährt werden.

Wenn aufgrund der Richtlinien Ihrer Organisation Dienstkonten keine Berechtigung für die **lokale Anwendung** nicht erteilt werden kann, jedoch das **Anmelden als Batchauftrag** zulässig ist, folgen Sie den Anweisungen im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) im Administratorhandbuch.

#### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Einschränkung: Das Überprüfungsdienstkonto kann nicht mit Azure Active Directory synchronisiert werden, der Server verfügt jedoch über Internetkonnektivität.

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Für das Überprüfungsdienstkonto können Sie ein lokales Windows-Konto oder ein Active Directory-Konto verwenden.

- Anweisungen für das Azure Active Directory-Konto finden Sie im Administratorhandbuch im Abschnitt [Angeben und Verwenden des Token-Parameters für „Set-AIPAuthentication“](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication).


## <a name="configure-the-scanner-in-the-azure-portal"></a>Konfigurieren des Scanners im Azure-Portal

Erstellen Sie vor dem Installieren des Scanners bzw. vor dem Upgraden des Scanners von der allgemein verfügbaren Version im Azure-Portal ein Profil für den Scanner. Konfigurieren Sie das Profil für Scannereinstellungen und die Datenrepositorys, die überprüft werden sollen.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
2. Suchen Sie die **Scanner**-Menüoptionen, und wählen Sie **Profiles (Preview)** (Profile (Vorschau)) aus.
    
    Für diese Option wird noch ein Rollout an Mandanten ausgeführt. Wenn sie nicht angezeigt wird, können Sie das Blatt direkt über den folgenden Link öffnen: https://portal.azure.com/?ScannerConfiguration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade

3. Wählen Sie auf dem Blatt **Azure Information Protection - Profiles (Preview)** (Azure Information Protection – Profile (Vorschau)) die Option **Hinzufügen** aus:
    
    ![Hinzufügen eines Profils für den Azure Information Protection-Scanner](./media/scanner-add-profile.png)

4. Geben Sie auf dem Blatt **Neues Profil hinzufügen** einen Namen für den Scanner ein, der zum Erkennen der Konfigurationseinstellungen und der Datenrepositorys verwendet wird, die überprüft werden sollen. Sie können beispielsweise **Europa** angeben, um den geografischen Standort der Datenrepositorys anzugeben, für die Ihr Scanner zuständig ist. Diesen Profilnamen müssen Sie angeben, wenn Sie den Scanner später installieren oder upgraden.
    
    Optional können Sie eine Beschreibung für administrative Zwecke eingeben, damit Sie den Profilnamen des Scanners leichter erkennen.

5. Konfigurieren Sie bei dieser ersten Konfiguration die folgenden Einstellungen, und wählen Sie anschließend **Speichern** aus, schließen Sie das Blatt jedoch nicht:
    
    - **Zeitplan:** Behalten Sie die Standardeinstellung **Manuell** bei.
    - **Zu ermittelnde Infotypen**: Ändern Sie diese Einstellung in **Nur Richtlinie**.
    - **Repositorys konfigurieren**: Konfigurieren Sie diese Einstellung noch nicht, da das Profil zunächst gespeichert werden muss.
    - **Erzwingen**: Wählen Sie **Aus** aus.
    - **Dateien basierend auf dem Inhalt bezeichnen**: Behalten Sie die Standardeinstellung **Ein** bei.
    - **Standardbezeichnung**: Behalten Sie die Standardeinstellung **Richtlinienstandard** bei.
    - **Dateien neu bezeichnen**: Behalten Sie die Standardeinstellung **Aus** bei.
    - **Preserve "Date modified", "Last modified" and "Modified by"** („Änderungsdatum“, „Zuletzt geändert“ und „Geändert von“ beibehalten): Behalten Sie die Standardeinstellung **Ein** bei.
    - **Zu scannende Dateitypen**: Behalten Sie die Standarddateitypen für **Ausschließen** bei.
    - **Standardbesitzer**: Behalten Sie die Standardeinstellung **Scannerkonto** bei.

6. Nachdem Sie das Profil erstellt und gespeichert haben, können Sie zur Option **Repositorys konfigurieren** zurückkehren, um die Datenspeicher anzugeben, die überprüft werden sollen. Sie können lokale Ordner, UNC-Pfade und SharePoint Server-URLs für SharePoint-Websites und -Bibliotheken angeben. 
    
    Für SharePoint werden SharePoint Server 2016 und SharePoint Server 2013 unterstützt. Ferner wird SharePoint Server 2010 unterstützt, wenn Sie über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.
    
    Zum Hinzufügen des ersten Datenspeichers wählen Sie auf dem Blatt **Neues Profil hinzufügen** die Option **Repositorys konfigurieren** aus, um das Blatt **Repositorys** zu öffnen:
    
    ![Konfigurieren von Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repositories-bar.png)

7. Wählen Sie auf dem Blatt **Repositorys** die Option **Hinzufügen** aus:
    
    ![Hinzufügen eines Datenrepositorys für den Azure Information Protection-Scanner](./media/scanner-repository-add.png)

8. Geben Sie auf dem Blatt **Repository** den Pfad für das Datenrepository an. 
    
    Platzhalter und WebDav-Speicherorte werden nicht unterstützt.
    
    Beispiele:
    
    Für einen lokalen Pfad: `C:\Folder`
    
    Für eine Netzwerkfreigabe: `C:\Folder\Filename`
    
    Für einen UNC-Pfad: `\\Server\Folder`
    
    Für eine SharePoint-Bibliothek: `http://sharepoint.contoso.com/Shared%20Documents/Folder`
    
    > [!TIP]
    > Beachten Sie beim Hinzufügen eines SharePoint-Pfads für „Freigegebene Dokumente“ Folgendes:
    >
     >- Geben Sie **Freigegebene Dokumente** im Pfad an, wenn alle Dokumente und Ordner in „Freigegebene Dokumente“ überprüft werden sollen. Beispiel: `http://sp2013/Shared Documents`
     >
     >- Geben Sie **Dokumente** im Pfad an, wenn alle Dokumente und Ordner in einem Unterordner von „Freigegebene Dokumente“ überprüft werden sollen. Beispiel: `http://sp2013/Documents/Sales Reports`
    
    Nehmen Sie bei dieser ersten Konfiguration an den restlichen Einstellungen auf diesem Blatt keine Änderungen vor, sondern behalten Sie diese als **Profilstandard** bei. So werden die Einstellungen vom Datenrepository aus dem Scannerprofil übernommen. 
    
    Wählen Sie **Speichern** aus.

9. Wiederholen Sie die Schritte 7 und 8, wenn Sie ein weiteres Datenrepository hinzufügen möchten.

10. Sie können das Blatt **Neues Profil hinzufügen** jetzt schließen. Daraufhin wird auf dem Blatt **Azure Information Protection - Profiles (Preview)** (Azure Information Protection – Profile (Vorschau)) der Profilname zusammen mit der Spalte **ZEITPLAN** mit der Einstellung **Manuell** und der leeren Spalte **ERZWINGEN** angezeigt.

Nun können Sie den Scanner mit dem Scannerprofil installieren, das Sie eben erstellt haben.

## <a name="install-the-scanner"></a>Installieren der Überprüfung

1. Melden Sie sich bei dem Windows Server-Computer an, auf dem die Überprüfung ausgeführt werden soll. Verwenden Sie ein Konto mit lokalen Administratorrechten und den Berechtigungen zum Schreiben in die SQL Server-Masterdatenbank.

2. Starten Sie eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**.

3. Führen Sie das Cmdlet [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner) aus, und geben Sie dabei die SQL Server-Instanz an, auf der eine Datenbank für den Azure Information Protection-Scanner erstellt werden soll, und den Profilnamen des Scanners, den Sie im vorherigen Abschnitt angegeben haben: 
    
    ```
    Install-AIPScanner -SqlServerInstance <name> -Profile <profile name>
    ```
    
    Beispiele, in denen der Profilname **Europa** verwendet wird:
    
    Für eine Standardinstanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1 -Profile Europe`
    
    Für eine benannte Instanz: `Install-AIPScanner -SqlServerInstance SQLSERVER1\AIPSCANNER -Profile Europe`
    
    Für SQL Server Express: `Install-AIPScanner -SqlServerInstance SQLSERVER1\SQLEXPRESS -Profile Europe`
    
    Wenn Sie dazu aufgefordert werden, geben Sie die Anmeldeinformationen für das Überprüfungsdienstkonto (\<Domäne/Benutzername>) und das Kennwort ein.

4. Stellen Sie unter **Verwaltung** > **Dienste** sicher, dass der Dienst jetzt installiert ist. 
    
    Der installierte Dienst heißt **Azure Information Protection-Überprüfung** und ist für die Ausführung mithilfe des von Ihnen erstellten Überprüfungsdienstkontos konfiguriert.

Nachdem Sie den Scanner installiert haben, müssen Sie ein Azure AD-Token abrufen, damit das Dienstkonto des Scanners authentifiziert und der Scanner unbeaufsichtigt ausgeführt werden kann. 

## <a name="get-an-azure-ad-token-for-the-scanner"></a>Abrufen eines Azure AD-Tokens für die Überprüfung

Mithilfe des Azure AD-Tokens kann das Überprüfungsdienstkonto bei Azure Information Protection authentifiziert werden.

1. Kehren Sie zum Azure-Portal zurück, um zwei Azure AD-Anwendungen zu erstellen, die für die Angabe eines Zugriffstokens für die Authentifizierung erforderlich sind. Nach einer ersten interaktiven Anmeldung wird die Überprüfung mit diesem Token ohne Benutzereingriff ausgeführt.
    
    Um diese Anwendungen zu erstellen, folgen Sie der Anleitung unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client/client-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administratorhandbuch.

2. Gehen Sie auf dem Windows Server-Computer folgendermaßen vor, wenn dem Überprüfungsdienstkonto für die Installation das Recht zur **lokalen Anmeldung** erteilt wurde: Melden Sie sich mit diesem Konto an, und starten Sie eine PowerShell-Sitzung. Führen Sie [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) aus, und geben Sie die Werte an, die Sie aus dem vorherigen Schritt kopiert haben:
    
    ```
    Set-AIPAuthentication -webAppId <ID of the "Web app / API" application> -webAppKey <key value generated in the "Web app / API" application> -nativeAppId <ID of the "Native" application>
    ```
    
    Wenn Sie dazu aufgefordert werden, geben Sie das Kennwort für Ihr Azure AD-Dienstkonto an, und klicken Sie dann auf **Akzeptieren**.
    
    Wenn Ihrem Überprüfungsdienstkonto für die Installation kein Recht zur **lokalen Anmeldung** erteilt werden kann: Folgen Sie den Anweisungen im Abschnitt über das [Angeben und Verwenden des Token-Parameters für Set-AIPAuthentication](./rms-client/client-admin-guide-powershell.md#specify-and-use-the-token-parameter-for-set-aipauthentication) im Administratorhandbuch. 

Die Überprüfung verfügt jetzt über ein Token für die Authentifizierung bei Azure AD, die ein oder zwei Jahre gültig ist oder nie abläuft, je nach der Konfiguration der **Web-App/API** in Azure AD. Wenn das Token abgelaufen ist, müssen Sie die Schritte 1 und 2 wiederholen.

Nun können Sie den ersten Scanvorgang im Ermittlungsmodus ausführen.

## <a name="run-a-discovery-cycle-and-view-reports-for-the-scanner"></a>Ausführen eines Ermittlungszyklus und Anzeigen von Berichten für die Überprüfung

1. Kehren Sie im Azure-Portal zu Azure Information Protection zurück, um den Scanner zu starten. Wählen Sie im Menü **Scanner** die Option **Knoten** aus. Wählen Sie den Scannerknoten und dann die Option **Jetzt überprüfen** aus:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)
    
    Führen Sie alternativ in der PowerShell-Sitzung den folgenden Befehl aus:
    
        Start-AIPScan

2. Warten Sie, bis die Überprüfung den Zyklus abgeschlossen hat. Wenn der Scanner alle Dateien in den von Ihnen angegebenen Datenspeichern durchforstet hat, wird der Scanner beendet, obwohl der Scannerdienst weiterhin ausgeführt wird.
    
    - Auf dem Blatt **Azure Information Protection – Knoten** ändert sich der Wert für die Spalte **STATUS** von **Scannen** in **Im Leerlauf**.
    
    - Mit PowerShell können Sie `Get-AIPScannerStatus` ausführen, um die Statusänderung zu überwachen.
    
    - Überprüfen Sie das lokale Ereignisprotokoll **Anwendungen und Dienste**, **Azure Information Protection**. Dieses Protokoll gibt außerdem an, wann die Überprüfung abgeschlossen wurde, und zeigt eine Zusammenfassung der Ergebnisse an. Suchen Sie einfach nach der Ereignis-ID **911**.

3. Lesen Sie die Berichte, die unter %*localappdata*%\Microsoft\MSIP\Scanner\Reports gespeichert sind. Die TXT-Zusammenfassungsdateien enthalten die zum Überprüfen benötigte Zeit, die Anzahl der überprüften Dateien sowie die Anzahl der Dateien mit übereinstimmenden Informationstypen. Die CSV-Dateien enthalten mehr Details zu den einzelnen Dateien. In diesem Ordner werden für jeden Scanzyklus bis zu 60 Berichte gespeichert, die bis auf den letzten alle komprimiert werden, um die Speicherplatzbelegung zu minimieren.
    
    > [!NOTE]
    > Mit dem Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) können Sie mithilfe des Parameters *ReportLevel* den Protokolliergrad ändern, den Speicherort oder Namen des Berichtsordners jedoch nicht. Wenn Sie die Berichte in einem anderen Volume oder in einer anderen Partition speichern möchten, sollten Sie eine Verzeichnisverbindung verwenden.
    >
    > Verwenden Sie hierzu beispielsweise den Befehl [Mklink](/windows-server/administration/windows-commands/mklink): `mklink /j D:\Scanner_reports C:\Users\aipscannersvc\AppData\Local\Microsoft\MSIP\Scanner\Reports`
    
    Aufgrund der Einstellung **Nur Richtlinie** für **Zu ermittelnde Infotypen** sind nur die Dateien in den ausführlichen Berichten enthalten, die den Bedingungen entsprechen, die Sie für die automatische Klassifizierung konfiguriert haben. Wenn keine der angewendeten Bezeichnungen angezeigt werden, überprüfen Sie, ob die Bezeichnungskonfiguration anstelle der empfohlenen Klassifizierung die automatische Klassifizierung enthält.
    
    > [!TIP]
    > Überprüfungen senden diese Informationen alle fünf Minuten an Azure Information Protection, so dass Sie die Ergebnisse nahezu in Echtzeit im Azure-Portal anzeigen können. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md). 
        
    Wenn die Ergebnisse nicht wie erwartet ausfallen, müssen Sie die Bedingungen, die Sie in Ihrer Azure Information Protection-Richtlinie für Ihre Bezeichnungen angegeben haben, möglicherweise neu konfigurieren. Wenn dies der Fall ist, wiederholen Sie die Schritte 1 bis 3, bis Sie die Konfiguration ändern können, um die Klassifizierung und optional den Schutz anzuwenden. 

Wenn Sie für das automatische Bezeichnen der Dateien, die die Überprüfung sucht, bereit sind, fahren Sie mit dem nächsten Abschnitt fort. 

## <a name="configure-the-scanner-to-apply-classification-and-protection"></a>Konfigurieren der Überprüfung zum Anwenden von Klassifizierung und Schutz

Wenn Sie diese Anweisungen befolgen, wird der Scanner einmal und nur im Modus für die Berichterstellung ausgeführt. Wenn Sie diese Einstellungen ändern möchten, bearbeiten Sie das Scannerprofil:

1. Kehren Sie zum Blatt **[Azure Information Protection - Profiles (Preview)](https://portal.azure.com/?ScannerConfiguration=true#blade/Microsoft_Azure_InformationProtection/DataClassGroupEditBlade/scannerProfilesBlade)** (Azure Information Protection – Profile (Vorschau)) zurück, und wählen Sie das Scannerprofil aus, um es zu bearbeiten.

2. Ändern Sie auf dem Blatt „\<**Profilname**>“ die folgenden beiden Einstellungen, und klicken Sie dann auf **Speichern**:
    
   - **Zeitplan:** Ändern Sie die Einstellung in **Immer**.
   - **Erzwingen**: Wählen Sie **Ein** aus.
    
     Es gibt andere Konfigurationseinstellungen, die Sie ggf. ändern sollten, z. B. ob Dateiattribute geändert werden und Dateien vom Scanner neu bezeichnet werden können. Weitere Informationen zu den einzelnen Konfigurationseinstellungen finden Sie in der Popuphilfe mit Informationen.

3. Notieren Sie sich die aktuelle Uhrzeit, und starten Sie den Scanner auf dem Blatt **Azure Information Protection – Knoten** neu:
    
    ![Initiieren des Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-scan-now.png)
    
    Alternativ können Sie den folgenden Befehl in der PowerShell-Sitzung ausführen:
    
        Start-AIPScan

4. Überwachen Sie das Ereignisprotokoll erneut, und achten Sie auf den Informationstyp **911** mit einem Zeitstempel, der nach der im vorherigen Schritt notierten Startzeit der Überprüfung liegt. 
    
    Überprüfen Sie die Berichte, um festzustellen, welche Dateien eine Bezeichnung erhalten haben, welche Klassifizierung für die einzelnen Dateien vergeben wurde und ob Schutz angewendet wurde. Oder verwenden Sie das Azure-Portal, um diese Informationen einfacher anzuzeigen.

Da der Zeitplan als fortlaufend konfiguriert wurde, startet der Scanner automatisch einen neuen Zyklus, sobald der alte abgeschlossen wurde, damit neue und geänderte Dateien gefunden werden.


## <a name="how-files-are-scanned"></a>So werden Dateien überprüft

Der Scanner führt die folgenden Prozesse zur Überprüfung von Dateien aus.

### <a name="1-determine-whether-files-are-included-or-excluded-for-scanning"></a>1. Bestimmen, ob Dateien überprüft oder von der Überprüfung ausgeschlossen werden sollen 
Bei der Überprüfung werden [von der Klassifizierung und vom Schutz ausgeschlossene](./rms-client/client-admin-guide-file-types.md#file-types-that-are-excluded-from-classification-and-protection) Dateien wie ausführbare Dateien und Systemdateien übersprungen.

Sie können dieses Verhalten ändern, indem Sie eine Liste mit Dateitypen definieren, die überprüft oder von der Überprüfung ausgeschlossen werden sollen. Sie können diese Liste für den Scanner angeben, damit standardmäßig alle Datenrepositorys angewendet werden. Zudem können Sie eine Liste für jedes Datenrepository angeben. Verwenden Sie zum Angeben dieser Liste die Einstellung **Zu scannende Dateitypen** im Scannerprofil:

![Konfigurieren der zu überprüfenden Dateitypen für den Azure Information Protection-Scanner](./media/scanner-file-types.png)

### <a name="2-inspect-and-label-files"></a>2. Überprüfen und Bezeichnen von Dateien

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
>     Prüfen Sie in der „%*localappdata*%\Microsoft\MSIP\Logs\MSIPScanner.iplog“-Datei (wenn mehrere Protokolle vorhanden sind, werden diese gemeinsam in einer ZIP-Datei gespeichert), ob die folgende Fehlermeldung für den Scanner protokolliert wurde, um festzustellen, ob dies der Grund für die Beendigung des Scanner ist: **Unable to connect to the remote server ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted IP:port.** (Die Verbindung mit dem Remoteserver kann nicht hergestellt werden. ---> System.Net.Sockets.SocketException: Normalerweise darf jede Socketadresse (Protokoll, Netzwerkadresse oder Anschluss) nur jeweils einmal verwendet werden IP:port)
>    
>     Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](https://docs.microsoft.com/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).
> 
> - Für große SharePoint-Farmen müssen Sie möglicherweise den Schwellenwert der Listenansicht (standardmäßig 5.000) erhöhen. Weitere Informationen finden Sie in der folgenden SharePoint-Dokumentation: [Manage large lists and libraries in SharePoint (Verwalten von großen Listen und Bibliotheken in SharePoint)](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).

### <a name="3-label-files-that-cant-be-inspected"></a>3. Bezeichnen von Dateien, die nicht überprüft werden können
Bei Dateitypen, die nicht überprüft werden können, wendet der Scanner die Standardbezeichnung in der Azure Information Protection-Richtlinie oder die von Ihnen für die Überprüfung konfigurierte Standardbezeichnung an.

Wie im vorherigen Schritt kann der Scanner die Dateien jedoch unter den folgenden Bedingungen nicht bezeichnen:

- Wenn die Bezeichnung zwar die Klassifizierung, aber keinen Schutz anwendet und der Dateityp nicht [ausschließlich die Klassifizierung unterstützt](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-classification-only)

- Wenn die Bezeichnung zwar Klassifizierung und Schutz anwendet, aber der Scanner den Dateityp nicht schützt
    
    Standardmäßig unterstützt der Scanner nur Office-Dateitypen und PDF-Dateien, wenn diese gemäß dem ISO-Standard für die PDF-Verschlüsselung geschützt werden. Sie können andere Dateitypen schützen, indem Sie wie im folgenden Abschnitt beschrieben [die Registrierung bearbeiten](#editing-the-registry-for-the-scanner).


### <a name="editing-the-registry-for-the-scanner"></a>Bearbeiten der Registrierung für die Überprüfung

Um das Standardverhalten der Überprüfung zum Schutz von Dateien zu ändern, bei denen es sich weder um Office- noch um PDF-Dateien handelt, müssen Sie die Registrierung manuell bearbeiten und die zusätzlichen Dateitypen angeben, die geschützt werden sollen, sowie den Typ des Schutzes (nativ oder generisch) festlegen. Weitere Informationen hierzu finden Sie in der Anleitung für Entwickler unter [Datei-API-Konfiguration](develop/file-api-configuration.md). Allgemeiner Schutz wird in dieser Dokumentation für Entwickler als „PFile“ bezeichnet. Folgendes gilt außerdem speziell für den Scanner:

- Die Überprüfung hat ein eigenes Standardverhalten: Standardmäßig werden nur die Office-Dateiformate und PDF-Dokumente geschützt. Wenn die Registrierung nicht geändert wird, werden andere Dateitypen nicht vom Scanner bezeichnet oder geschützt.

- Wenn Sie das gleiche Standardschutzverhalten wie beim Azure Information Protection-Client wünschen, bei dem alle Dateien automatisch nativen oder generischen Schutz haben, gehen Sie wie folgt vor: Geben Sie den Platzhalter `*` als Registrierungsschlüssel und `Default` als Wertdaten an.

Wenn Sie die Registrierung bearbeiten, erstellen Sie manuell die beiden Schlüssel **MSIPC** und **FileProtection**, falls noch nicht vorhanden, sowie einen Schlüssel für jede Erweiterung.

Damit der Scanner beispielsweise neben Office- und PDF-Dateien auch TIFF-Bilder schützt, sieht die Registrierung nach Ihrer Bearbeitung wie auf der folgenden Abbildung aus. TIFF-Dateien unterstützen als Bilddateien den nativen Schutz. Die entsprechende Erweiterung lautet „.ptiff“.

![Bearbeiten der Registrierung für die Überprüfung zum Anwenden von Schutz](./media/editregistry-scanner.png)

Eine Liste mit Text- und Bilddateitypen, die zwar ebenfalls den nativen Schutz unterstützen, aber in der Registrierung angegeben werden müssen, finden Sie im Administratorleitfaden unter [Unterstützte Dateitypen für Klassifizierung und Schutz](./rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection).

Geben Sie für Dateien, die den nativen Schutz nicht unterstützten, die Erweiterung als einen neuen Schlüssel und **PFILE** für den generischen Schutz an. Die Erweiterung für die geschützte Datei lautet dann „.pfile“.


## <a name="when-files-are-rescanned"></a>Wann Dateien überprüft werden

Im ersten Überprüfungszyklus untersucht die Überprüfung alle Dateien in den Datenspeichern. In den nachfolgenden Überprüfungen werden dann nur noch neue oder geänderte Dateien untersucht. 

Über das Blatt **Azure Information Protection – Knoten** im Azure-Portal können Sie erzwingen, dass der Scanner alle Dateien erneut überprüft. Wählen Sie in der Liste den Scanner und dann die Option **Rescan all files** (Alle Dateien erneut überprüfen) aus:

![Initiieren eines erneuten Scanvorgangs für den Azure Information Protection-Scanner](./media/scanner-rescan-files.png)

Das erneute Überprüfen aller Dateien ist nützlich, wenn Sie möchten, dass die Berichte alle Dateien enthalten. Diese Konfiguration wird in der Regel verwendet, wenn die Überprüfung im Ermittlungsmodus ausgeführt wird. Wenn eine vollständige Überprüfung abgeschlossen ist, ändert sich der Überprüfungstyp automatisch auf „inkrementell“, sodass bei nachfolgenden Überprüfungen nur noch neue oder geänderte Dateien untersucht werden.

Außerdem werden alle Dateien untersucht, wenn die Überprüfung eine Azure Information Protection-Richtlinie herunterlädt, die über neue oder geänderte Bedingungen verfügt. Die Überprüfung aktualisiert die Richtlinie entweder jede Stunde oder wenn der Dienst gestartet wird und die Richtlinie älter als eine Stunde ist.  

> [!TIP]
> Wenn Sie die Richtlinie früher als gemäß diesem einstündigen Intervall aktualisieren müssen (z. B. während einer Testphase): Löschen Sie manuell die Richtliniendatei **Policy.msip** aus den Ordnern **%LocalAppData%\Microsoft\MSIP\Policy.msip** und **%LocalAppData%\Microsoft\MSIP\Scanner**. Starten Sie anschließend den Azure Information-Überprüfungsdienst neu.
> 
> Wenn Sie die Schutzeinstellungen in der Richtlinie geändert haben, warten Sie 15 Minuten ab dem Zeitpunkt, an dem Sie die Schutzeinstellungen gespeichert haben, bevor Sie den Dienst neu starten.

Wenn die Überprüfung eine Richtlinie heruntergeladen hat, für die keine automatischen Bedingungen konfiguriert wurden, wird die Kopie der Richtliniendatei im Überprüfungsordner nicht aktualisiert. In diesem Szenario müssen Sie die Richtliniendatei **Policy.msip** sowohl aus **%LocalAppData%\Microsoft\MSIP\Policy.msip** als auch aus **%LocalAppData%\Microsoft\MSIP\Scanner** löschen, damit die Überprüfung eine neu heruntergeladene Richtliniendatei verwenden kann, bei der die Bezeichnungen für automatische Bedingungen ordnungsgemäß konfiguriert sind.

## <a name="editing-in-bulk-for-the-data-repository-settings"></a>Gleichzeitiges Bearbeiten von mehreren Datenrepositoryeinstellungen

Für die Datenrepositorys, die Sie einem Scannerprofil hinzugefügt haben, können Sie die Optionen **Exportieren** und **Importieren** verwenden, um die Einstellungen im Handumdrehen zu ändern. Dies ist beispielsweise möglich, wenn Sie für Ihre SharePoint-Datenrepositorys einen neuen Dateityp hinzufügen möchten, um ihn vom Scanvorgang auszuschließen.

Statt jedes Datenrepository einzeln im Azure-Portal zu bearbeiten, können Sie die Option **Exportieren** auf dem Blatt **Repositorys** verwenden:

![Exportieren der Datenrepositoryeinstellungen für den Scanner](./media/export-scanner-repositories.png)

Ändern Sie die Datei manuell, und verwenden Sie anschließend die Option **Importieren** auf demselben Blatt.

## <a name="using-the-scanner-with-alternative-configurations"></a>Verwenden der Überprüfung mit alternativen Konfigurationen

Für die Überprüfung stehen Ihnen zwei alternative Szenarios zur Verfügung, die von Azure Information Protection unterstützt werden, bei denen keine Bezeichnungen für Bedingungen konfiguriert werden müssen: 

- Anwenden einer Standardbezeichnung auf alle Dateien in einem Datenrepository:
    
    Legen Sie für diese Konfiguration die Option **Standardbezeichnung** auf **Benutzerdefiniert** fest, und wählen Sie anschließend die zu verwendende Bezeichnung aus.
    
    Der Inhalt der Dateien wird nicht überprüft, und alle Dateien im Datenrepository werden entsprechend der Standardbezeichnung bezeichnet, die Sie für das Datenrepository oder das Scannerprofil angeben.
    

- Identifizieren aller benutzerdefinierten Bedingungen und bekannten vertraulichen Informationstypen:
    
    Legen Sie für diese Konfiguration die Option **Zu ermittelnde Infotypen** auf **Alle** fest.
    
    Bei der Überprüfung werden alle benutzerdefinierten Bedingungen verwendet, die Sie für Bezeichnungen in der Azure Information Protection-Richtlinie angegeben haben, sowie die Liste der Informationstypen, die zum Angeben von Bezeichnungen in der Azure Information Protection-Richtlinie verfügbar sind. Mit dieser Einstellung können Sie nach vertraulichen Informationen suchen, von denen Sie möglicherweise nicht einmal wissen, dass Sie sie haben. Das geht jedoch auf Kosten der Scangeschwindigkeit des Scanners.
    
    Für diese Schnellstartanleitung wird für die allgemein verfügbare Version des Scanners die folgende Konfiguration verwendet: [Schnellstart: Bestimmen vertraulicher Informationen](quickstart-findsensitiveinfo.md).

## <a name="optimizing-the-performance-of-the-scanner"></a>Optimieren der Überprüfungsleistung

So maximieren Sie die Überprüfungsleistung:

- **Verwenden Sie eine schnelle und zuverlässige Netzwerkverbindung zwischen dem Überprüfungscomputer und dem überprüften Datenspeicher**
    
    Platzieren Sie beispielsweise den überprüfenden Computer im gleichen LAN oder (vorzugsweise) im gleichen Netzwerksegment wie den überprüften Datenspeicher.
    
    Die Qualität der Netzwerkverbindung wirkt sich auf die Überprüfungsleistung aus, da die Überprüfung die Dateien zur Untersuchung auf den Computer überträgt, auf dem der Überprüfungsdienst ausgeführt wird. Durch Reduzieren (oder Ausschalten) der Anzahl der Netzwerkhops, über die diese Daten transportiert werden, verringern Sie zugleich Ihre Netzwerkauslastung. 

- **Achten Sie darauf, dass der überprüfende Computer verfügbare Prozessorressourcen aufweist**
    
    Das Untersuchen der Dateiinhalte und Ver- und Entschlüsseln der Dateien sind prozessorlastige Aktionen. Überprüfen Sie typische Überprüfungszyklen für Ihre angegebenen Datenquellen, um zu bestimmen, ob ein Mangel an Prozessorressourcen sich negativ auf die Überprüfungsleistung auswirkt.
    
- **Überprüfen Sie keine lokalen Ordner auf dem Computer, auf dem der Überprüfungsdienst ausgeführt wird**
    
    Wenn Ordner auf einem Windows-Servercomputer untersucht werden müssen, installieren Sie die Überprüfung auf einem anderen Computer, und konfigurieren Sie diese Ordner als zu überprüfende Netzwerkfreigaben. Das Trennen der beiden Funktionen des Hostens der Dateien und des Überprüfens der Dateien bedeutet, dass die Computerressourcen für diese Dienste nicht in Konkurrenz miteinander stehen.

Installieren Sie ggf. mehrere Instanzen der Überprüfung. Vom Azure Information Protection-Scanner werden beim Angeben eines benutzerdefinierten Profilnamens für den Scanner mehrere Konfigurationsdatenbanken auf einer SQL Server-Instanz unterstützt.

Weitere Faktoren, die sich auf die Überprüfungsleistung auswirken:

- Die aktuelle Last und die Antwortzeiten der Datenspeicher, in denen die zu überprüfenden Dateien enthalten sind

- Ob die Überprüfung im Suchmodus oder im Durchsetzungsmodus ausgeführt wird
    
    Im Suchmodus wird normalerweise eine höhere Überprüfungsrate als im Durchsetzungsmodus erreicht, da für die Ermittlung ein einzelner Dateilesevorgang erforderlich ist, während für den Durchsetzungsmodus Lese- und Schreibvorgänge erforderlich sind.

- Sie können die Bedingungen in Azure Information Protection ändern
    
    Der erste Scanzyklus, in dem der Scanner jede Datei untersuchen muss, benötigt mehr Zeit als die nachfolgenden Scanzyklen, in denen standardmäßig nur neue und geänderte Dateien untersucht werden. Wenn Sie jedoch die Bedingungen in der Azure Information Protection-Richtlinie ändern, werden alle Dateien erneut untersucht, wie im [vorhergehenden Abschnitt](#when-files-are-rescanned) beschrieben.

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

Da der Scanner jetzt über das Azure-Portal konfiguriert wird, sind Cmdlets von früheren Versionen, mit denen Datenrepositorys konfiguriert wurden, und die Liste der überprüften Dateitypen veraltet. 

Zu den verbleibenden Cmdlets gehören diejenigen, mit denen der Scanner installiert und upgegradet werden kann und die Konfigurationsdatenbank und das Profil des Scanners sowie der Grad der lokalen Berichterstellung geändert und Konfigurationseinstellungen für einen nicht verbundenen Computer importiert werden können. 

Im Folgenden sind alle Cmdlets aufgeführt, die von der Vorschauversion des Scanners unterstützt werden: 

- [Get-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Get-AIPScannerConfiguration)

- [Get-AIPScannerStatus](/powershell/module/azureinformationprotection/Get-AIPScannerStatus)

- [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner)

- [Set-AIPScanner](/powershell/module/azureinformationprotection/Set-AIPScanner)

- [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Set-AIPScannerConfiguration)

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

Dieses Ereignis wird protokolliert, wenn der Scanner eine manuelle Überprüfung oder eine Schleife mit kontinuierlichen Ausführungen beendet hat.

Wenn der Scanner so konfiguriert wurde, dass er manuell und nicht kontinuierlich ausgeführt wird, legen Sie zum erneuten Scannen der Dateien den **Zeitplan** im Scannerprofil auf **Manuell** oder **Immer** fest und starten den Dienst anschließend neu.

----

## <a name="next-steps"></a>Nächste Schritte

Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie: [Automating data protection with Azure Information Protection scanner](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner) (Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung).

Möglicherweise stellen Sie sich folgende Fragen: [Was ist der Unterschied zwischen der Windows Server-Dateiklassifizierungsinfrastruktur und der Azure Information Protection-Überprüfung?](faqs.md#whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner)

Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).


