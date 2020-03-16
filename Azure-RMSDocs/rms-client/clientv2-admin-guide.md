---
title: Azure Information Protection Unified Bezeichnung Client Admin Guide
description: Anweisungen und Informationen für Administratoren in einem Unternehmensnetzwerk, die für die Bereitstellung des Azure Information Protection Unified Bezeichnung-Clients für Windows verantwortlich sind.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e77a4696114dc7b7271db55ca846d5dfecff650f
ms.sourcegitcommit: 2917e822a5d1b21bf465f2cb93cfe46937b1faa7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79403738"
---
# <a name="azure-information-protection-unified-labeling-client-administrator-guide"></a>Azure Information Protection Unified Bezeichnung-Client Administrator Handbuch

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Verwenden Sie die Informationen in diesem Handbuch, wenn Sie für den Azure Information Protection Unified Bezeichnung-Client in einem Unternehmensnetzwerk verantwortlich sind oder wenn Sie weitere technische Informationen benötigen, als im [Azure Information Protection Unified Bezeichnung-Client Benutzerhandbuch](clientv2-user-guide.md)zu finden. 

Beispiel:

- Überblick über die verschiedenen Komponenten dieses Clients und Informationen darüber, in welchen Fällen dieser installiert werden soll

- Informationen zum Installieren des Clients für Benutzer mit Angaben zu den Voraussetzungen, Installationsoptionen, Parametern und Überprüfungen

- Navigieren zu den Clientdateien und Nutzungsprotokollen

- Identifizieren der vom Client unterstützten Dateitypen

- Verwenden des Clients mit PowerShell zur Steuerung über die Befehlszeile

**Haben Sie eine Frage, die in dieser Dokumentation nicht beantwortet wird?** Besuchen Sie unsere [Yammer-Website für Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-unified-labeling-client"></a>Technische Übersicht über den Azure Information Protection Unified-Bezeichnungs Client

Der Azure Information Protection Unified Bezeichnung-Client umfasst Folgendes:

- Ein Office-Add-in, das eine **Vertraulichkeits** Schaltfläche auf dem Menüband installiert, damit Benutzer Vertraulichkeits Bezeichnungen auswählen können, und eine Option zum Anzeigen der Azure Information Protection Leiste zur besseren Bezeichnung der Sichtbarkeit.

- Kontextmenüoptionen für den Windows-Datei-Explorer für Benutzer, um Klassifizierungsbezeichnungen und den entsprechenden Schutz auf Dateien anzuwenden.

- Ein Viewer zum Anzeigen geschützter Dateien, wenn diese von einer systemeigenen Anwendung nicht geöffnet werden können.

- Ein PowerShell-Modul zum Ermitteln sensibler Informationen in Dateien und zum Anwenden oder Entfernen von Klassifizierungs Bezeichnungen und des Schutzes von Dateien. 
    
    Der-Client umfasst Cmdlets zum Installieren und Konfigurieren des [Azure Information Protection Scanner](../deploy-aip-scanner.md) , der als Dienst unter Windows Server ausgeführt wird. Mit diesem Dienst können Sie Dateien in Daten speichern wie Netzwerkfreigaben und SharePoint-Server Bibliotheken ermitteln, klassifizieren und schützen.

- Der Rights Management-Client, der mit dem Schutzdienst (Azure Rights Management) kommuniziert, um Dateien zu verschlüsseln und zu schützen.

Mit Ausnahme des Viewers kann der Azure Information Protection Unified-Bezeichnungs Client nicht mit Anwendungen und Diensten verwendet werden, die direkt mit dem Schutzdienst oder Active Directory Rights Management Services kommunizieren.

Wenn Sie über AD RMS verfügen und zu Azure Information Protection migrieren möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../migrate-from-ad-rms-to-azure-rms.md) nach.


## <a name="should-you-deploy-the-azure-information-protection-unified-labeling-client"></a>Sollten Sie den Azure Information Protection Unified-Bezeichnungs Client bereitstellen?

Stellen Sie den Azure Information Protection Unified Label-Client bereit, wenn Sie [die Vertraulichkeits Bezeichnungen in Office 365 Security & Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)verwenden und eine der folgenden Punkte zutrifft:

- Sie möchten Dokumente und e-Mail-Nachrichten klassifizieren (und optional schützen), indem Sie in Ihren Office-Apps (Word, Excel, PowerPoint, Outlook) auf Windows-Computern Bezeichnungen auswählen.

- Sie möchten Dateien mithilfe des Datei-Explorers klassifizieren (und optional schützen), der zusätzliche Dateitypen außer den von Office unterstützten, die Auswahl mehrerer Objekte und Ordner unterstützt.

- Sie möchten Skripts ausführen, die Dokumente mithilfe von PowerShell-Befehlen klassifizieren (und optional schützen).

- Sie möchten einen Dienst testen, der lokal gespeicherte Dateien entdeckt, klassifiziert (und optional schützt).

- Sie möchten geschützte Dokumente anzeigen, wenn eine systemeigene Anwendung zum Anzeigen der Datei nicht installiert ist oder diese Dokumente nicht öffnen kann.

Beispiel für das Office-Add-in für den Azure Information Protection Unified-Bezeichnungs Client, das die neue **Vertraulichkeits** Schaltfläche auf dem Menüband und die optionale Azure Information Protection Leiste anzeigt:

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/v2word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-unified-labeling-client"></a>Installieren und unterstützen des Azure Information Protection Unified Bezeichnung-Clients

Sie können den Azure Information Protection Unified Bezeichnung-Client mithilfe einer ausführbaren Datei oder einer Windows Installer-Datei installieren. Weitere Informationen zu den einzelnen Entscheidungen und Anweisungen finden Sie unter [install the Azure Information Protection Unified Bezeichnung Client for users](clientv2-admin-guide-install.md).  

In den folgenden Abschnitten finden Sie Informationen zur Unterstützung bei der Installation des Clients. 

### <a name="installation-checks-and-troubleshooting"></a>Installationsüberprüfungen und Problembehandlung

Nachdem Sie den Client installiert haben, verwenden Sie die Option **Hilfe und Feedback**, um das Dialogfeld **Microsoft Azure Information Protection** zu öffnen:

- Aus einer Office-Anwendung: Wählen Sie auf der Registerkarte **Startseite** in der Gruppe **Sensitivität** die Option **Sensitivität**aus, und wählen Sie dann **Hilfe und Feedback**aus.

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und dann **Hilfe und Feedback** aus. 

#### <a name="help-and-feedback-section"></a>Abschnitt **Hilfe und Feedback**

Standardmäßig wird der **Link "Weitere Informationen** " auf der [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection) -Website angezeigt. Sie können einen eigenen URL-Link konfigurieren, der auf eine benutzerdefinierte Hilfeseite als eine der Richtlinien Einstellungen in der Bezeichnung Management Center fest geht: Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Compliance Center.

Der Link " **Problem melden** " wird nur angezeigt, wenn Sie eine [Erweiterte Einstellung](clientv2-admin-guide-customizations.md#add-report-an-issue-for-users)angeben. Wenn Sie diese Einstellung konfigurieren, müssen Sie einen HTTP-Link angeben, z. B. die E-Mail-Adresse Ihres Helpdesks. 

Die **Export Protokolle** sammelt und fügt automatisch Protokolldateien für den Azure Information Protection Unified-Bezeichnungs Client ein, wenn Sie aufgefordert wurden, diese an Microsoft-Support zu senden. Diese Option kann auch von Endbenutzern verwendet werden, um diese Dateien an Ihren Helpdesk zu senden. Alternativ dazu können Sie das PowerShell-Cmdlet [Export-aiplogs](/powershell/module/azureinformationprotection/export-aiplogs) verwenden.

Mit den **Einstellungen zum Zurücksetzen** wird der Benutzer abgemeldet, die derzeit heruntergeladenen Vertraulichkeits Bezeichnungen und Bezeichnungs Richtlinien werden gelöscht, und die Benutzereinstellungen für den Azure Rights Management-Dienst werden zurückgesetzt.

> [!NOTE]
> Wenn Sie technische Probleme mit dem-Client haben, finden Sie weitere Informationen [unter Support Optionen und Communityressourcen](../information-support.md#support-options-and-community-resources).

##### <a name="more-information-about-the-reset-settings-option"></a>Weitere Informationen zur Option „Einstellungen“ zurücksetzen

- Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 

- Sofern die Dateien nicht gesperrt sind, löscht diese Aktion alle Dateien in den folgenden Speicherorten. Diese Dateien umfassen Client Zertifikate, Schutz Vorlagen, Vertraulichkeits Bezeichnungen und Richtlinien aus Ihrem Bezeichnungs Verwaltungs Center und die zwischengespeicherten Benutzer Anmelde Informationen. Die Clientprotokolldateien werden nicht gelöscht.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\microsoft\msip\mip\\ *\<ProcessName. exe\>*
    
    - %LocalAppData%\microsoft\msip\appdetails
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- Die folgenden Registrierungsschlüssel und -einstellungen werden gelöscht. Wenn die Einstellungen für einen dieser Registrierungsschlüssel benutzerdefinierte Werte aufweisen, müssen diese nach dem Zurücksetzen des Clients erneut konfiguriert werden.
    
    In der Regel werden diese Einstellungen für Unternehmensnetzwerke unter Verwendung einer Gruppenrichtlinie konfiguriert. In diesem Fall werden sie automatisch erneut angewendet, wenn die Gruppenrichtlinie auf dem Computer aktualisiert wird. Es sind jedoch möglicherweise einige Einstellungen vorhanden, die einmal mit einem Skript oder manuell konfiguriert werden. In diesem Fall müssen Sie weitere Schritte durchlaufen, um diese Einstellungen erneut zu konfigurieren. Ein Beispiel: Computer können ein Skript einmal ausführen, um Einstellungen für die Umleitung zu Azure Information Protection zu konfigurieren, weil Sie von AD RMS migrieren und noch einen Dienstverbindungspunkt in Ihrem Netzwerk haben. Nach der Zurücksetzung des Clients muss der Computer dieses Skript erneut ausführen.
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT_USER \software\classes\local settings\software\microsoft\msipc

- Der derzeit angemeldete Benutzer wird abgemeldet.

#### <a name="client-status-section"></a>Abschnitt **Clientstatus**

Verwenden Sie den Wert **Verbunden als**, um zu bestätigen, dass der angezeigte Benutzername das Konto identifiziert, das für die Azure Information Protection-Authentifizierung verwendet werden soll. Dieser Benutzername muss mit einem Konto übereinstimmen, das für Office 365 oder Azure Active Directory verwendet wird. Das Konto muss auch zu einem Office 365-Mandanten gehören, der für Vertraulichkeits Bezeichnungen in Ihrem Bezeichnungs Verwaltungs Portal konfiguriert ist.

Wenn Sie sich als ein anderer Benutzer anmelden müssen, der angezeigt wird, finden Sie weitere Informationen unter [Anmelden als anderer](clientv2-admin-guide-customizations.md#sign-in-as-a-different-user) Benutzer.

Verwenden Sie die Informationen unter **Version**, um zu bestätigen, welche Version des Clients installiert ist. Sie können überprüfen, ob es sich um die neueste Releaseversion und die entsprechenden Korrekturen und neuen Features handelt, indem Sie die [Versions Freigabe Informationen](unifiedlabelingclient-version-release-history.md) für den Client lesen.

## <a name="support-for-multiple-languages"></a>Unterstützung mehrerer Sprachen

Der Azure Information Protection Unified Bezeichnung-Client unterstützt die gleichen Sprachen wie Office 365. Eine Liste dieser Sprachen finden Sie im Abschnitt **Office 365, Exchange Online-Schutz und Power BI** auf der Office-Seite zur [internationalen Verfügbarkeit](https://products.office.com/business/international-availability).

Für diese Sprachen werden Menü Optionen, Dialogfelder und Meldungen aus dem Azure Information Protection Unified-Beschriftungs Client in der Sprache des Benutzers angezeigt. Es gibt ein einzelnes Installationsprogramm, das die Sprache erkennt, sodass keine zusätzliche Konfiguration erforderlich ist, um den Azure Information Protection Unified-Bezeichnungs Client für verschiedene Sprachen zu installieren. 

Bezeichnungs Namen und Beschreibungen, die Sie angeben, werden jedoch nicht automatisch übersetzt, wenn Sie Bezeichnungen in der Beschriftungs zentrale konfigurieren. Damit Benutzer Bezeichnungen in Ihrer bevorzugten Sprache anzeigen können, stellen Sie Ihre eigenen Übersetzungen bereit, und konfigurieren Sie Sie für die Bezeichnungen mithilfe von Office 365 Security & Compliance PowerShell und des *localesettings* -Parameters für " [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps)". Optische Kennzeichnungen werden nicht übersetzt und unterstützen nicht mehr als eine Sprache.

## <a name="post-installation-tasks"></a>Aufgaben nach der Installation

Nachdem Sie den Azure Information Protection Unified Label-Client installiert haben, stellen Sie sicher, dass Sie Benutzern Anweisungen zum bezeichnen der Dokumente und e-Mails sowie Anleitungen für die Auswahl der Bezeichnungen für bestimmte Szenarien erteilen. Beispiel:

- Online Benutzeranweisungen: [Azure Information Protection Unified-Bezeichnung-Benutzerhandbuch](clientv2-user-guide.md)

- Download des anpassbaren Benutzerhandbuchs: [Azure Information Protection End User Adoption Guide (Benutzerhandbuch für die Einführung in Azure Information Protection)](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

## <a name="installing-the-azure-information-protection-scanner"></a>Installieren des Azure Information Protection Scanners

Der Scanner für den Unified-Bezeichnungs Client ist allgemein verfügbar. Installieren Sie die aktuelle Version des Unified-Bezeichnung-Clients aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

Wenn Sie den Scanner zum ersten Mal auf einem Computer installieren, müssen Sie diesen Client herunterladen und installieren, und befolgen Sie dann die Anweisungen unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](../deploy-aip-scanner.md).

Wenn Sie die Überprüfung vom Azure Information Protection Client (klassisch) oder einer früheren Version des Unified-Bezeichnungs Clients aktualisieren, finden Sie entsprechende Anweisungen im Abschnitt [Aktualisieren des Azure Information Protection Scanners](#upgrading-the-azure-information-protection-scanner) .

## <a name="upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client"></a>Aktualisieren und warten des Azure Information Protection Unified-Bezeichnungs Clients

> [!NOTE]
> Der Azure Information Protection Unified Bezeichnung-Client unterstützt das Upgrade des Azure Information Protection-Clients (klassisch) sowie das Upgrade von früheren Versionen des Azure Information Protection Unified-Bezeichnungs Clients.

Das Azure Information Protection-Team aktualisiert den Azure Information Protection Unified-Bezeichnungs Client regelmäßig auf neue Funktionen und Korrekturen. Ankündigungen werden auf der [Yammer-Website](https://www.yammer.com/AskIPTeam) des Teams veröffentlicht.

Wenn Sie Windows Update verwenden, aktualisiert der Azure Information Protection Unified Bezeichnung-Client automatisch die allgemeine Verfügbarkeits Version dieses Clients, unabhängig davon, wie der-Client installiert wurde. Neue Clientreleases werden wenige Wochen nach der Release im Katalog veröffentlicht.

Alternativ können Sie den Client manuell aktualisieren, indem Sie die neue Version aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. Installieren Sie dann die neue Version, um ein Upgrade des Clients auszuführen. Sie müssen diese Methode verwenden, um die Vorschau Versionen zu aktualisieren, und wenn Sie ein Upgrade vom Azure Information Protection Client (klassisch) durchführen.

Wenn Sie ein Upgrade vom Azure Information Protection-Client (klassisch) unter Windows 7 ausführen, werden alle Office-Anwendungen während des Client Upgrades automatisch neu gestartet. Dieser automatische Neustart gilt nicht für spätere Betriebssysteme oder, wenn Sie ein Upgrade von einer älteren Version des Unified Bezeichnung-Clients durchführen.

Bei einem manuellen Upgrade deinstallieren Sie die vorherige Version nur, wenn Sie die Installationsmethode ändern. Beispielsweise wechseln Sie von der ausführbaren Version (.exe) des Clients zur Windows Installer-Version (.msi) des Clients. Oder, wenn Sie eine frühere Version des Clients installieren müssen. Angenommen, Sie haben eine Vorschauversion zum Testen installiert und müssen nun zur aktuellen Version der allgemeinen Verfügbarkeit zurückkehren.

Verwenden Sie den [Versions releaseverlauf und die Unterstützungs Richtlinie](unifiedlabelingclient-version-release-history.md) , um die Unterstützungs Richtlinie für den Azure Information Protection Unified-Bezeichnungs Client, die derzeit unterstützten Versionen und die Neuerungen und Änderungen für die unterstützten Releases zu verstehen. 

### <a name="upgrading-the-azure-information-protection-scanner"></a>Upgrade der Azure Information Protection-Überprüfung

Anweisungen zum Aktualisieren des Scanners sind davon abhängig, ob Sie ein Upgrade von einer früheren Version des Scanners vom Azure Information Protection Unified-Bezeichnungs Client oder vom Azure Information Protection-Client (klassisch) durchführen.

#### <a name="to-upgrade-the-scanner-from-an-earlier-version-of-the-unified-labeling-client"></a>So führen Sie ein Upgrade des Scanners von einer früheren Version des Unified-Bezeichnungs Clients durch

1. Beenden Sie auf dem Computer mit dem Scanner den Scannerdienst **Azure Information Protection-Scanner**.

2.    Aktualisieren Sie den Azure Information Protection Unified-Bezeichnungs Client, indem Sie die neueste Version des Unified-Bezeichnungs Clients aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen und installieren.

3. Führen Sie in einer PowerShell-Sitzung den Befehl Update-aipscanner mit dem Profil Ihres Scanners aus. Beispiel: `Update-AIPScanner –Profile Europe`

4. Starten Sie den Azure Information Protection-Scannerdienst **Azure Information Protection-Scanner** neu.

Sie können jetzt die restlichen Anweisungen unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](../deploy-aip-scanner.md)verwenden, sodass Sie den Schritt zum Installieren des Scanners weglassen. Da der Scanner bereits installiert ist, gibt es keinen Grund, ihn erneut zu installieren.

#### <a name="to-upgrade-the-scanner-from-the-classic-client"></a>So führen Sie ein Upgrade des Scanners vom klassischen Client aus

Wenn Sie derzeit den Azure Information Protection Scanner vom Azure Information Protection-Client (klassisch) verwenden, können Sie ein Upgrade durchführen, um vertrauliche Informationstypen und Vertraulichkeits Bezeichnungen zu verwenden, die aus der Sicherheits & von Office 365 veröffentlicht werden. Compliance Center (oder das Microsoft 365 Security Center oder das Microsoft 365 Compliance Center).

Das Upgrade des Scanners ist von der Version des klassischen Clients abhängig, den Sie zurzeit ausführen:

- [Upgrade von Version 1.48.204.0 und höheren Versionen](#upgrade-from-the-azure-information-protection-client-classic-version-1482040-and-later-versions-of-this-client)

- [Upgrade von früheren Versionen als 1.48.204.0](#upgrade-from-the-azure-information-protection-client-classic-versions-earlier-than-1482040)

Beim Upgrade wird eine neue Datenbank mit dem Namen **AIPScannerUL_\<profile_name >** erstellt, und die vorherige Überprüfungs Datenbank wird für den Fall beibehalten, dass Sie für die vorherige Version benötigt wird. Wenn Sie sicher sind, dass Sie die vorherige Scanner-Datenbank nicht benötigen, können Sie Sie löschen. Da beim Upgrade eine neue Datenbank erstellt wird, werden bei der erstmaligen Ausführung der Überprüfung alle Dateien neu erstellt.

##### <a name="upgrade-from-the-azure-information-protection-client-classic-version-1482040-and-later-versions-of-this-client"></a>Upgrade von der Azure Information Protection Client (klassisch) Version 1.48.204.0 und höheren Versionen dieses Clients

Wenn Sie den Scanner mithilfe der Vorschauversion des Unified-Bezeichnungs Clients aktualisiert haben, müssen Sie diese Anweisungen nicht erneut ausführen.

1. Beenden Sie auf dem Computer mit dem Scanner den Scannerdienst **Azure Information Protection-Scanner**.

2. Aktualisieren Sie auf den Azure Information Protection Unified-Bezeichnungs Client, indem Sie den Unified-Bezeichnungs Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen und installieren.

3. Führen Sie in einer PowerShell-Sitzung den Befehl Update-aipscanner mit dem Profil Ihres Scanners aus. Beispiel: `Update-AIPScanner –Profile Europe`.
    
    In diesem Schritt wird eine neue Datenbank mit dem Namen **AIPScannerUL_\<profile_name erstellt >**

4. Starten Sie den Azure Information Protection-Scannerdienst **Azure Information Protection-Scanner** neu.

Sie können jetzt die restlichen Anweisungen unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](../deploy-aip-scanner.md)verwenden, sodass Sie den Schritt zum Installieren des Scanners weglassen. Da der Scanner bereits installiert ist, gibt es keinen Grund, ihn erneut zu installieren.

##### <a name="upgrade-from-the-azure-information-protection-client-classic-versions-earlier-than-1482040"></a>Upgrade von den Azure Information Protection-Client Versionen (klassisch) vor 1.48.204.0

> [!IMPORTANT]
> Installieren Sie bei einem Smooth-Upgradepfad nicht den Azure Information Protection Unified-Bezeichnungs Client auf dem Computer, auf dem die Überprüfung ausgeführt wird, als ersten Schritt zum Aktualisieren der Überprüfung. Verwenden Sie stattdessen die folgenden Upgradeanweisungen.

Ab Version 1.48.204.0 werden die Konfigurationseinstellungen des Scanners mithilfe eines Konfigurations Profils aus dem Azure-Portal abgerufen. Das Upgrade des Scanners umfasst das anweisen der Überprüfung, diese Online Konfiguration zu verwenden, und für den Unified-Bezeichnungs Client wird die Offline Konfiguration für den Scanner nicht unterstützt.

1. Verwenden Sie das Azure-Portal, um ein neues Scannerprofil zu erstellen, das die Einstellungen für den Scanner und die Datenrepositorys mit allen erforderlichen Einstellungen enthält. Hilfe zu diesem Schritt finden Sie im Abschnitt [configure the Scanner in the Azure-Portal in](../deploy-aip-scanner.md#configure-the-scanner-in-the-azure-portal) den Anweisungen zur Überprüfung der Bereitstellung.

2. Beenden Sie auf dem Computer mit dem Scanner den Scannerdienst **Azure Information Protection-Scanner**.

3. Aktualisieren Sie auf den Azure Information Protection Unified-Bezeichnungs Client, indem Sie den Unified-Bezeichnungs Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen und installieren.

4. Führen Sie den Befehl „Update-AIPScanner“ in einer PowerShell-Sitzung mit dem Profilnamen aus, den Sie in Schritt 1 angegeben haben. Beispiel: `Update-AIPScanner –Profile Europe`

5. Starten Sie den Azure Information Protection-Scannerdienst **Azure Information Protection-Scanner** neu.

Sie können jetzt die restlichen Anweisungen unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](../deploy-aip-scanner.md)verwenden, sodass Sie den Schritt zum Installieren des Scanners weglassen. Da der Scanner bereits installiert ist, gibt es keinen Grund, ihn erneut zu installieren.

###### <a name="upgrading-in-a-different-order-to-the-recommended-steps"></a>Upgraden in einer anderen Reihenfolge als der der empfohlenen Schritte

Wenn Sie ein Upgrade von einer früheren Version als 1.48.204.0 ausführen und die Überprüfung nicht im Azure-Portal konfigurieren, bevor Sie den Befehl Update-aipscanner ausführen, haben Sie keinen Profilnamen, der angibt, dass die Überprüfungs Konfigurationseinstellungen für das Upgrade identifiziert. ESS. 

Wenn Sie in diesem Szenario den Scanner im Azure-Portal konfigurieren, müssen Sie genau den Profilnamen angeben, den Sie beim Ausführen des Befehls „Update-AIPScanner“ verwendet haben. Der Scanner wird nur mit Ihren Einstellungen konfiguriert, wenn die Namen identisch sind. 

> [!TIP]
> Um Scanner zu identifizieren, die diese Fehlkonfiguration aufweisen, verwenden Sie den Bereich **Azure Information Protection-Knoten** in der Azure-Portal.
>  
> Für Scanner, die über Internet Konnektivität verfügen, wird der Computername mit der GA-Versionsnummer des Azure Information Protection Clients, aber ohne Profilnamen angezeigt. Nur Scanner mit der Versionsnummer 1.41.51.0 sollten in diesem Bereich keinen Profilnamen anzeigen. 

## <a name="uninstalling-the-azure-information-protection-unified-labeling-client"></a>Deinstallieren des Azure Information Protection Unified Bezeichnung-Client

Verwenden Sie eine der folgenden Optionen zur Deinstallation des Clients:

- Deinstallieren Sie ein Programm über die Systemsteuerung: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**

- Führen Sie die ausführbare Datei (z **. b. AzInfoProtection_UL. exe**) erneut aus, und klicken Sie auf der Seite **Setup ändern** auf **deinstallieren**. 

- Führen Sie die ausführbare Datei mit **/uninstall** aus. Beispiel: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Nächste Schritte
Informationen zum Installieren des-Clients finden Sie unter [install the Azure Information Protection Unified Bezeichnung Client for users](clientv2-admin-guide-install.md).

Wenn Sie den Azure Information Protection-Client bereits installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei dessen Unterstützung:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


