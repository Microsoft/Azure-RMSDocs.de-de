---
title: Azure Information Protection-Client – Administratorhandbuch
description: Anweisungen und Informationen für Administratoren in einem Unternehmensnetzwerk, die für die Bereitstellung des Azure Information Protection-Clients für Windows zuständig sind.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 33a5982f-7125-4031-92c2-05daf760ced1
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 4162e3df46377a4de859d1bb2dce1363d7146d08
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68793592"
---
# <a name="azure-information-protection-client-administrator-guide"></a>Azure Information Protection-Client – Administratorhandbuch

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Verwenden Sie die Informationen in diesem Handbuch, wenn Sie für den Azure Information Protection-Client in einem Unternehmensnetzwerk verantwortlich sind oder wenn Sie mehr technische Informationen erhalten möchten als im [Azure Information Protection-Client – Benutzerhandbuch](client-user-guide.md) vorhanden sind. 

Zum Beispiel:

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

- Ein Add-In für Office, das die Azure Information Protection-Leiste für Benutzer zum Auswählen der Klassifizierungsbezeichnungen sowie die Schaltfläche **Schützen** im Menüband für weitere Optionen installiert. Für Outlook ist auf dem Menüband zusätzlich die Schaltfläche **Nicht weiterleiten** verfügbar.

- Kontextmenüoptionen für den Windows-Datei-Explorer für Benutzer, um Klassifizierungsbezeichnungen und den entsprechenden Schutz auf Dateien anzuwenden.

- Ein Viewer zum Anzeigen geschützter Dateien, wenn diese von einer systemeigenen Anwendung nicht geöffnet werden können.

- Ein PowerShell-Modul zum Anwenden und Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien. 
    
    Dieses Modul beinhaltet Cmdlets zur Installation und konfiguriert die [Azure Information Protection-Überprüfung](../deploy-aip-scanner.md), die als Dienst unter Windows Server ausgeführt wird. Mithilfe dieses Dienstes können Sie Dateien in Datenspeichern wie Netzwerkfreigaben und Serverbibliotheken in SharePoint suchen, klassifizieren und schützen.

- Der Rights Management-Client, der mit Azure Rights Management (Azure RMS) oder Active Directory Rights Management Services (AD RMS) kommuniziert.

Der Azure Information Protection-Client ist am besten für die Arbeit mit seinen Azure-Diensten geeignet. Azure Information Protection und seine Datenschutzdienste, Azure Rights Management. Der Azure Information Protection-Client funktioniert mit einigen Einschränkungen auch mit der lokalen Version von Rights Management, AD RMS. Einen umfassenden Vergleich der Funktionen, die von Azure Information Protection und AD RMS unterstützt werden, finden Sie unter [Vergleich zwischen Azure Information Protection und AD RMS](../compare-on-premise.md). 

Wenn Sie über AD RMS verfügen und zu Azure Information Protection migrieren möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../migrate-from-ad-rms-to-azure-rms.md) nach.


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Sollten Sie den Azure Information Protection-Client bereitstellen?

Stellen Sie den Azure Information Protection Client bereit, wenn Sie [in Office 365 Security & Compliance Center keine Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels) verwenden, sondern stattdessen Azure Information Protection Bezeichnungen verwenden, die Sie aus Azure herunterladen, und eine der folgenden gelten

- Sie möchten Dokumente und E-Mails durch Auswählen von Bezeichnungen innerhalb Ihrer Office-Anwendungen (Word, Excel, PowerPoint, Outlook) klassifizieren (und optional schützen).

- Sie möchten Dateien mithilfe des Datei-Explorers klassifizieren (und optional schützen), der zusätzliche Dateitypen außer den von Office unterstützten, die Auswahl mehrerer Objekte und Ordner unterstützt.

- Sie möchten Skripts ausführen, die Dokumente mithilfe von PowerShell-Befehlen klassifizieren (und optional schützen).

- Sie möchten einen Dienst ausführen, der lokal gespeicherte Dateien sucht, klassifiziert (und gegebenenfalls schützt).

- Sie möchten geschützte Dokumente anzeigen, wenn eine systemeigene Anwendung zum Anzeigen der Datei nicht installiert ist oder diese Dokumente nicht öffnen kann.

- Sie möchten Dateien mithilfe des Datei-Explorers oder mithilfe von PowerShell-Befehlen nur schützen.

- Sie möchten, dass Benutzer und Administratoren in der Lage sind, geschützte Dokumente nachzuverfolgen und den Schutz zu widerrufen.

- Sie möchten die Verschlüsselung von Dateien und Containern für Datenwiederherstellungszwecke in Massen entfernen (Schutz aufheben).

- Sie führen Office 2010 aus und möchten Dokumente und E-Mails-mithilfe des Azure Rights Management-Diensts schützen.

Beispiel zur Veranschaulichung des Azure Information Protection-Client-Add-Ins für eine Office-Anwendung, in dem die Klassifizierungsbezeichnungen für Ihre Organisation und die neue Schaltfläche **Schützen** im Menüband angezeigt wird:

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-client"></a>Installieren und Unterstützen des Azure Information Protection-Clients

Sie können den Azure Information Protection-Client mithilfe einer ausführbaren Datei oder einer Windows-Installationsdatei installieren. Weitere Informationen zu sämtlichen Auswahloptionen und Anleitungen finden Sie unter [Install the Azure Information Protection client for users (Installieren des Azure Information Protection-Clients für Benutzer)](client-admin-guide-install.md).  

In den folgenden Abschnitten finden Sie Informationen zur Unterstützung bei der Installation des Clients. 

### <a name="installation-checks-and-troubleshooting"></a>Installationsüberprüfungen und Problembehandlung

Nachdem Sie den Client installiert haben, verwenden Sie die Option **Hilfe und Feedback**, um das Dialogfeld **Microsoft Azure Information Protection** zu öffnen:

- Aus einer Office-Anwendung: Wählen Sie auf der Registerkarte **Home** in der Gruppe **Schutz** die Optionen **Schützen** und anschließend **Hilfe und Feedback** aus.

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und anschließend **Hilfe und Feedback** aus. 

#### <a name="help-and-feedback-section"></a>Abschnitt **Hilfe und Feedback**

Der Link **Weitere Infos** verweist standardmäßig auf die [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)-Website. Sie können aber auch eine benutzerdefinierte URL als eine der [Richtlinieneinstellungen](../configure-policy-settings.md) in der Azure Information Protection-Richtlinie festlegen.

Der Link **Problem melden** wird nur angezeigt, wenn Sie eine [erweiterte Clienteinstellung](client-admin-guide-customizations.md#add-report-an-issue-for-users) angeben. Wenn Sie diese Einstellung konfigurieren, müssen Sie einen HTTP-Link angeben, z. B. die E-Mail-Adresse Ihres Helpdesks.

Die Option **Protokolle exportieren** erfasst automatisch Protokolldateien für den Azure Information Protection-Client und hängt diese an, wenn Sie darum gebeten wurden, diese an den Microsoft Support zu senden. Diese Option kann auch von Endbenutzern verwendet werden, um diese Dateien an Ihren Helpdesk zu senden.

Die Option **Einstellungen zurücksetzen** meldet den Benutzer ab, löscht die derzeit heruntergeladene Azure Information Protection-Richtlinie und setzt die Benutzereinstellungen für den Azure Rights Management-Dienst zurück.

##### <a name="more-information-about-the-reset-settings-option"></a>Weitere Informationen zur Option „Einstellungen“ zurücksetzen

- Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 

- Sofern die Dateien nicht gesperrt sind, löscht diese Aktion alle Dateien in den folgenden Speicherorten. Dies umfasst Clientzertifikate, Rights Management-Vorlagen, die Azure Information Protection-Richtlinie und die zwischengespeicherten Benutzeranmeldeinformationen. Die Clientprotokolldateien werden nicht gelöscht.
    
    - %LocalAppData%\Microsoft\DRM
    
    - %LocalAppData%\Microsoft\MSIPC
    
    - %LocalAppData%\Microsoft\MSIP\Policy.msip
    
    - %LocalAppData%\Microsoft\MSIP\TokenCache

- Die folgenden Registrierungsschlüssel und -einstellungen werden gelöscht. Wenn die Einstellungen für einen dieser Registrierungsschlüssel benutzerdefinierte Werte aufweisen, müssen diese nach dem Zurücksetzen des Clients erneut konfiguriert werden. 
    
    In der Regel werden diese Einstellungen für Unternehmensnetzwerke unter Verwendung einer Gruppenrichtlinie konfiguriert. In diesem Fall werden sie automatisch erneut angewendet, wenn die Gruppenrichtlinie auf dem Computer aktualisiert wird. Es sind jedoch möglicherweise einige Einstellungen vorhanden, die einmal mit einem Skript oder manuell konfiguriert werden. In diesem Fall müssen Sie weitere Schritte durchlaufen, um diese Einstellungen erneut zu konfigurieren. Ein Beispiel: Computer können ein Skript einmal ausführen, um Einstellungen für die Umleitung zu Azure Information Protection zu konfigurieren, weil Sie von AD RMS migrieren und noch einen Dienstverbindungspunkt in Ihrem Netzwerk haben. Nach der Zurücksetzung des Clients muss der Computer dieses Skript erneut ausführen.
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\Identity
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\15.0\Common\DRM
    
    - HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\16.0\Common\DRM
    
    - HKEY_CURRENT_USER\SOFTWARE\Classes\Local settings\software\microsoft\msipc    

- Der derzeit angemeldete Benutzer wird abgemeldet.

#### <a name="client-status-section"></a>Abschnitt **Clientstatus**

Verwenden Sie den Wert **Verbunden als**, um zu bestätigen, dass der angezeigte Benutzername das Konto identifiziert, das für die Azure Information Protection-Authentifizierung verwendet werden soll. Dieser Benutzername muss mit einem Konto übereinstimmen, das für Office 365 oder Azure Active Directory verwendet wird. Das Konto muss auch zu einem Mandanten gehören, der für Azure Information Protection konfiguriert ist.

Wenn Sie sich als ein anderer Benutzer anmelden müssen als den angezeigten Benutzer, lesen Sie die Informationen zu Anpassungen unter [Anmelden als ein anderer Benutzer](client-admin-guide-customizations.md#sign-in-as-a-different-user).

Der Wert **Last connection** (Letzte Verbindung) gibt an, wann der Client sich zuletzt mit dem Azure Information Protection-Dienst Ihrer Organisation verbunden hat. Sie können diese Informationen mit der Datums- und Zeitangabe **Die Information Protection-Richtlinie wurde am...installiert** verwenden, um zu bestätigen, wann die Azure Information Protection-Richtlinie zuletzt installiert oder aktualisiert wurde. Wenn der Client eine Verbindung mit dem Dienst herstellt, lädt er automatisch die letzte Richtlinie herunter, sofern diese von der aktuellen Richtlinie abweicht. Die Richtlinie wird außerdem alle 24 Stunden heruntergeladen. Wenn Sie nach dem angezeigten Zeitpunkt Änderungen vorgenommen haben, schließen Sie die Office-Anwendung, und öffnen Sie sie erneut.

Wenn die Meldung **Dieser Client ist nicht für Office Professional Plus lizenziert** angezeigt wird: Der Azure Information Protection-Client hat festgestellt, dass die installierte Office-Edition das Anwenden des Rights Management-Schutzes nicht unterstützt. In diesem Fall werden Bezeichnungen, die diesen Schutz anwenden, auf der Azure Information Protection-Leiste nicht angezeigt.

Verwenden Sie die Informationen unter **Version**, um zu bestätigen, welche Version des Clients installiert ist. Klicken Sie auf den Link **Neuigkeiten**, um den [Versionsveröffentlichungsverlauf](client-version-release-history.md) des Clients zu lesen und zu überprüfen, ob es sich um die neueste Version handelt und die entsprechenden Fixes und neuen Features installiert sind.

## <a name="support-for-multiple-languages"></a>Unterstützung mehrerer Sprachen

Der Azure Information Protection-Client unterstützt alle Sprachen, die Office 365 unterstützt. Eine Liste dieser Sprachen finden Sie im Abschnitt **Office 365, Exchange Online-Schutz und Power BI** auf der Office-Seite zur [internationalen Verfügbarkeit](https://products.office.com/business/international-availability).

Für diese Sprachen werden Menüoptionen, Dialogfelder und Meldungen des Azure Information Protection-Client in der Sprache des Benutzers angezeigt. Es gibt ein Installationsprogramm, das die Sprache erkennt, weshalb keine weitere Konfiguration erforderlich ist, um den Azure Information Protection-Client für verschiedene Sprachen zu installieren. 

Die Namen und Beschreibungen von Bezeichnungen, die Sie angeben, werden jedoch nicht automatisch übersetzt, wenn Sie Bezeichnungen in der Azure Information Protection-Richtlinie konfigurieren. Ab 30. August 2017 enthält die aktuelle [Standardrichtlinie](../configure-policy-default.md) Unterstützung für einige Sprachen. Damit Benutzer Bezeichnungen in ihrer bevorzugten Sprachen angezeigt bekommen, stellen Sie eigene Übersetzungen bereit, und konfigurieren Sie die Azure Information Protection-Richtlinie, um diese Übersetzungen zu verwenden. Weitere Informationen finden Sie unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection](../configure-policy-languages.md). Optische Kennzeichnungen werden nicht übersetzt und unterstützen nicht mehr als eine Sprache.

## <a name="post-installation-tasks"></a>Aufgaben nach der Installation

Nachdem Sie den Azure Information Protection-Client installiert haben, stellen Sie sicher, dass Sie Benutzern Anweisungen zur Bezeichnung ihrer Dokumente und E-Mails und Anleitungen dazu geben, welche Bezeichnungen für bestimmte Szenarien ausgewählt werden müssen. Beispiel:

- Online-Benutzeranweisungen: [Azure Information Protection-Benutzerhandbuch](client-user-guide.md)

- Herunterladen eines anpassbaren Leitfadens: [Azure Information Protection End User Adoption Guide](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf) (Endbenutzerhandbuch für die Einführung in Azure Information Protection)

## <a name="upgrading-and-maintaining-the-azure-information-protection-client"></a>Upgraden und Verwalten des Azure Information Protection-Clients

Das Azure Information Protection-Team aktualisiert den Azure Information Protection-Client regelmäßig, um Korrekturen und neue Funktionen zu implementieren. Ankündigungen werden auf der [Yammer-Website](https://www.yammer.com/AskIPTeam) des Teams veröffentlicht.

Wenn Sie Windows Update verwenden, aktualisiert der Azure Information Protection-Client automatisch die Version für die allgemeine Verfügbarkeit des Clients, unabhängig davon, wie der Client installiert wurde. Neue Clientreleases werden wenige Wochen nach der Release im Katalog veröffentlicht.

Alternativ können Sie den Client manuell aktualisieren, indem Sie die neue Version aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. Installieren Sie dann die neue Version, um ein Upgrade des Clients auszuführen. Vorschauversionen lassen sich nur mit dieser Methode aktualisieren.

Bei einem manuellen Upgrade deinstallieren Sie die vorherige Version nur, wenn Sie die Installationsmethode ändern. Beispielsweise wechseln Sie von der ausführbaren Version (.exe) des Clients zur Windows Installer-Version (.msi) des Clients. Oder, wenn Sie eine frühere Version des Clients installieren müssen. Beispielsweise haben Sie die aktuelle Vorschauversion zu Testzwecken installiert und müssen nun auf die aktuelle allgemein verfügbare Version zurückgreifen.

Im Artikel [Verlauf der Releases und Supportrichtlinie](client-version-release-history.md) finden Sie weitere Informationen zur Supportrichtlinie für den Azure Information Protection-Client, zu den derzeit unterstützten Versionen und zu den Neuerungen und Änderungen für die unterstützten Versionen. 

### <a name="upgrading-the-azure-information-protection-scanner"></a>Upgrade der Azure Information Protection-Überprüfung

Verwenden Sie die folgenden Anweisungen, um die Überprüfung von einer allgemein verfügbaren Version, die älter als 1.48.204.0 ist, auf die aktuelle Version der Überprüfung zu aktualisieren.

#### <a name="to-upgrade-the-scanner-to-the-current-version"></a>So führen Sie ein Upgrade des Scanners auf die aktuelle Version durch

> [!IMPORTANT]
> Wenn Sie einen Smooth-Upgradepfad verwenden möchten, installieren Sie den Azure Information Protection-Client nicht auf dem Computer, auf dem die Überprüfung ausgeführt wird, als ersten Schritt zum Aktualisieren des Scanners. Verwenden Sie stattdessen die folgenden Upgradeanweisungen.

Ab Version 1.48.204.0 ändert der Upgradeprozess von vorherigen Versionen automatisch den Scanner, sodass er seine Konfigurationseinstellungen vom Azure-Portal abruft. Ferner wird das Schema für die Konfigurationsdatenbank des Scanners aktualisiert, und diese Datenbank wird über AzInfoProtection umbenannt:

- Wenn Sie keinen eigenen Profilnamen angeben, wird die Konfigurationsdatenbank in **AIPScanner_\<Computername>** umbenannt. 

- Wenn Sie einen eigenen Profilnamen angeben, wird die Konfigurationsdatenbank in **AIPScanner_\<Profilname>** umbenannt.

Der Scanner kann zwar in einer anderen Reihenfolge upgegradet werden, es werden jedoch die folgenden Schritte empfohlen:

1. Verwenden Sie das Azure-Portal, um ein neues Scannerprofil zu erstellen, das die Einstellungen für den Scanner und die Datenrepositorys mit allen erforderlichen Einstellungen enthält. Hilfe zu diesem Schritt finden Sie im Abschnitt [configure the Scanner in the Azure-Portal in](../deploy-aip-scanner.md#configure-the-scanner-in-the-azure-portal) den Anweisungen zur Überprüfung der Bereitstellung.
    
    Diesen Schritt müssen Sie auch dann ausführen, wenn der Computer, auf dem der Scanner ausgeführt wird, nicht mit dem Internet verbunden ist. Verwenden Sie anschließend im Azure-Portal die Option **Exportieren**, um das Scannerprofil in eine Datei zu exportieren.

2. Beenden Sie auf dem Computer mit dem Scanner den Scannerdienst **Azure Information Protection-Scanner**.

3. Aktualisieren Sie den Azure Information Protection Client, indem Sie die aktuelle allgemein verfügbare Version aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)installieren.

4. Führen Sie den Befehl „Update-AIPScanner“ in einer PowerShell-Sitzung mit dem Profilnamen aus, den Sie in Schritt 1 angegeben haben. Beispiel: `Update-AIPScanner –Profile Europe`

5. Nur für den Fall, dass der Scanner auf einem nicht verbundenen Computer ausgeführt wird: Führen Sie nun das Cmdlet [Import-AIPScannerConfiguration](/powershell/module/azureinformationprotection/Import-AIPScannerConfiguration) aus, und geben Sie die Datei an, in der die exportierten Einstellungen enthalten sind.

6. Starten Sie den Azure Information Protection-Scannerdienst **Azure Information Protection-Scanner** neu.

Sie können jetzt die restlichen Anweisungen unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](../deploy-aip-scanner.md)verwenden, sodass Sie den Schritt zum Installieren des Scanners weglassen. Da der Scanner bereits installiert ist, gibt es keinen Grund, ihn erneut zu installieren.

##### <a name="upgrading-in-a-different-order-to-the-recommended-steps"></a>Upgraden in einer anderen Reihenfolge als der der empfohlenen Schritte

Wenn Sie den Scanner nicht vor dem Ausführen des Befehls „Update-AIPScanner“ im Azure-Portal konfigurieren, gibt es keinen Profilnamen zum Angeben, anhand dessen die Konfigurationseinstellungen des Scanners für den Upgradevorgang erkannt werden. 

Wenn Sie in diesem Szenario den Scanner im Azure-Portal konfigurieren, müssen Sie genau den Profilnamen angeben, den Sie beim Ausführen des Befehls „Update-AIPScanner“ verwendet haben. Der Scanner wird nur mit Ihren Einstellungen konfiguriert, wenn die Namen identisch sind. 

> [!TIP]
> Verwenden Sie das Blatt **Azure Information Protection – Knoten** im Azure-Portal, um Scanner mit dieser fehlerhaften Konfiguration zu erkennen.
>  
> Für Scanner, die über Internet Konnektivität verfügen, wird der Computername mit der GA-Versionsnummer des Azure Information Protection Clients, aber ohne Profilnamen angezeigt. Nur für Scanner mit der Versionsnummer 1.41.51.0 sollte auf diesem Blatt kein Profilname angezeigt werden. 

Wenn Sie beim Ausführen des Befehls „Update-AIPScanner“ keinen Profilnamen angegeben haben, wird automatisch der Computername zum Erstellen des Profilnamens für den Scanner verwendet.

#### <a name="moving-the-scanner-configuration-database-to-a-different-sql-server-instance"></a>Verschieben der Konfigurationsdatenbank des Scanners in eine andere SQL Server-Instanz

In der aktuellen GA-Version gibt es ein bekanntes Problem, wenn Sie versuchen, die scannerkonfigurationsdatenbank nach dem Ausführen des upgradebefehls in eine neue SQL Server Instanz zu verschieben.

Wenn Sie wissen, dass Sie die Überprüfungs Konfigurations Datenbank für die GA-Version verschieben möchten, gehen Sie wie folgt vor:

1. Deinstallieren Sie den Scanner mit dem Befehl [Uninstall-AIPScanner](/powershell/module/azureinformationprotection/Uninstall-AIPScanner).

2. Wenn Sie noch kein Upgrade auf die aktuelle allgemein verfügbare Version des Azure Information Protection Clients durchgeführt haben, führen Sie jetzt ein Upgrade des Clients aus.

3. Installieren Sie den Scanner mithilfe des Befehls [Install-AIPScanner](/powershell/module/azureinformationprotection/Install-AIPScanner), und geben Sie dabei die neue SQL Server-Instanz und den Profilnamen an.

4. Optional: Wenn Sie nicht möchten, dass der Scanner alle Dateien erneut überprüft, exportieren Sie die Tabelle „ScannerFiles“, und importieren Sie sie in die neue Datenbank.

## <a name="uninstalling-the-azure-information-protection-client"></a>Deinstallieren des Azure Information Protection-Clients

Verwenden Sie eine der folgenden Optionen zur Deinstallation des Clients:

- Verwenden der Systemsteuerung, um ein Programm zu deinstallieren: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**.

- Führen Sie die ausführbare Datei (z. B. **AzInfoProtection.exe**) erneut aus, und klicken Sie auf der Seite **Setup ändern** auf **Deinstallieren**. 

- Führen Sie die ausführbare Datei mit **/uninstall** aus. Beispiel: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Nächste Schritte
Informationen zum Installieren des Clients finden Sie unter [Install the Azure Information Protection client for users (Installieren des Azure Information Protection-Clients für Benutzer)](client-admin-guide-install.md).

Wenn Sie den Azure Information Protection-Client bereits installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei dessen Unterstützung:

- [Anpassungen](client-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
