---
title: Azure Information Protection – einheitliche bezeichnungs Client – Administratorhandbuch
description: Anweisungen und Informationen für Administratoren in einem Unternehmensnetzwerk, die verantwortlich für die Bereitstellung von Azure Information Protection sind einheitliche bezeichnungs-Client für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 05/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: 9f50eef590b684be95d410ed470bd0d0ee62a76a
ms.sourcegitcommit: b92f60a87f824fc2da1e599f526898e3a0c919c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2019
ms.locfileid: "67343709"
---
# <a name="azure-information-protection-unified-labeling-client-administrator-guide"></a>Azure Information Protection – einheitliche bezeichnungs Client – Administratorhandbuch

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Verwenden Sie die Informationen in diesem Handbuch, wenn Sie für die Azure Information Protection bezeichnungs-Client in einem Unternehmensnetzwerk unified verantwortlich sind, oder sollen weitere technische Informationen benötigen, als in der [Azure Information Protection – einheitliche Bezeichnungen Client – Benutzerhandbuch](clientv2-user-guide.md). 

Zum Beispiel:

- Überblick über die verschiedenen Komponenten dieses Clients und Informationen darüber, in welchen Fällen dieser installiert werden soll

- Informationen zum Installieren des Clients für Benutzer mit Angaben zu den Voraussetzungen, Installationsoptionen, Parametern und Überprüfungen

- Navigieren zu den Clientdateien und Nutzungsprotokollen

- Identifizieren der vom Client unterstützten Dateitypen

- Verwenden des Clients mit PowerShell zur Steuerung über die Befehlszeile

**Haben Sie eine Frage, die in dieser Dokumentation nicht beantwortet wird?** Besuchen Sie unsere [Yammer-Website für Azure Information Protection](https://www.yammer.com/AskIPTeam). 

## <a name="technical-overview-of-the-azure-information-protection-unified-labeling-client"></a>Technischer Überblick über die Azure Information Protection unified bezeichnungs-client

Der einheitliche Bezeichnung Azure Information Protection-Client umfasst Folgendes:

- Eine Office-add-in, das installiert eine **Vertraulichkeit** Menüband auf die Schaltfläche für Benutzer zum Auswählen der vertraulichkeitsbezeichnungen und eine Option aus, um die Azure Information Protection-Leiste für eine bessere Sichtbarkeit der Bezeichnung angezeigt wird.

- Kontextmenüoptionen für den Windows-Datei-Explorer für Benutzer, um Klassifizierungsbezeichnungen und den entsprechenden Schutz auf Dateien anzuwenden.

- Ein Viewer zum Anzeigen geschützter Dateien, wenn diese von einer systemeigenen Anwendung nicht geöffnet werden können.

- Ein PowerShell-Modul zum Anwenden und Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien. 

- Die Rights Management-Client, der kommuniziert mit dem Azure Rights Management (Azure RMS)-Dienst zum Verschlüsseln und Schützen von Dateien.

Mit Ausnahme der im Viewer kann nicht der Azure Information Protection unified bezeichnungs-Client verwendet werden, mit Anwendungen und Diensten, die direkt mit dem Azure Rights Management-Dienst oder die Active Directory Rights Management Services zu kommunizieren.

Wenn Sie über AD RMS verfügen und zu Azure Information Protection migrieren möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../migrate-from-ad-rms-to-azure-rms.md) nach.


## <a name="should-you-deploy-the-azure-information-protection-unified-labeling-client"></a>Sollten Sie den Azure Information Protection unified bezeichnungs-Client bereitstellen?

Den einheitlichen Bezeichnung Azure Information Protection-Client bereitstellen, bei Verwendung von [vertraulichkeitsbezeichnungen im Office 365 Security & Compliance Center](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels), und eine der folgenden gilt:

- Sie möchten Klassifizieren (und optional schützen) Sie Dokumente und e-Mails durch Auswählen von Bezeichnungen innerhalb Ihrer Office-apps (Word, Excel, PowerPoint, Outlook) auf Windows-Computern.

- Sie möchten Dateien mithilfe des Datei-Explorers klassifizieren (und optional schützen), der zusätzliche Dateitypen außer den von Office unterstützten, die Auswahl mehrerer Objekte und Ordner unterstützt.

- Sie möchten Skripts ausführen, die Dokumente mithilfe von PowerShell-Befehlen klassifizieren (und optional schützen).

- Sie möchten geschützte Dokumente anzeigen, wenn eine systemeigene Anwendung zum Anzeigen der Datei nicht installiert ist oder diese Dokumente nicht öffnen kann.

Beispiel für die Office-add-in für Azure Information Protection unified bezeichnungs-Client anzeigen, die neue **Vertraulichkeit** -Taste auf dem Menüband und die optionale Azure Information Protection-Leiste:

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/v2word2016-calloutsv2.png)

## <a name="installing-and-supporting-the-azure-information-protection-unified-labeling-client"></a>Installieren und unterstützen die Azure Information Protection unified bezeichnungs-Clients

Sie können den Azure Information Protection unified bezeichnungs-Client mithilfe einer ausführbaren Datei oder eine Windows Installer-Datei installieren. Weitere Informationen zu sämtlichen Auswahloptionen und Anleitungen finden Sie unter [Installieren des einheitlichen Azure Information Protection-Bezeichnung-Clients für Benutzer](clientv2-admin-guide-install.md).  

In den folgenden Abschnitten finden Sie Informationen zur Unterstützung bei der Installation des Clients. 

### <a name="installation-checks-and-troubleshooting"></a>Installationsüberprüfungen und Problembehandlung

Nachdem Sie den Client installiert haben, verwenden Sie die Option **Hilfe und Feedback**, um das Dialogfeld **Microsoft Azure Information Protection** zu öffnen:

- Aus einer officeanwendung: Auf der **Startseite** Registerkarte die **Vertraulichkeit** Gruppe **Vertraulichkeit**, und wählen Sie dann **Hilfe und Feedback**.

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und anschließend **Hilfe und Feedback** aus. 

#### <a name="help-and-feedback-section"></a>Abschnitt **Hilfe und Feedback**

Die **Link zu weiteren Informationen** in der Standardeinstellung wird an die [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection) Website. Sie können eigene URL-Link konfigurieren, der auf eine benutzerdefinierte Hilfe-Seite als eine der Einstellungen in der Office 365 Security & Compliance Center gesendet wird.

Die **Protokolle exportieren** automatisch erfasst und fügt Sie Protokolldateien für Azure Information Protection bezeichnungs-Client, Unified Wenn Sie gebeten wurden, diese an den Microsoft Support senden. Diese Option kann auch von Endbenutzern verwendet werden, um diese Dateien an Ihren Helpdesk zu senden.

Die **Einstellungen zurücksetzen** meldet den Benutzer, löscht die aktuell heruntergeladene vertraulichkeitsbezeichnungen sowie die Richtlinien und setzt die benutzereinstellungen für den Azure Rights Management-Dienst zurück.

##### <a name="more-information-about-the-reset-settings-option"></a>Weitere Informationen zur Option „Einstellungen“ zurücksetzen

- Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 

- Sofern die Dateien nicht gesperrt sind, löscht diese Aktion alle Dateien in den folgenden Speicherorten. Diese Dateien enthalten die Clientzertifikate, Rights Management-Vorlagen, vertraulichkeitsbezeichnungen und Richtlinien über das Office 365 Security & Compliance Center und die zwischengespeicherten Benutzeranmeldeinformationen. Die Clientprotokolldateien werden nicht gelöscht.
    
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
    
    - HKEY_CURRENT_USER\SOFTWARE\Classes\Local Settings\Software\Microsoft\MSIPC

- Der derzeit angemeldete Benutzer wird abgemeldet.

#### <a name="client-status-section"></a>Abschnitt **Clientstatus**

Verwenden Sie den Wert **Verbunden als**, um zu bestätigen, dass der angezeigte Benutzername das Konto identifiziert, das für die Azure Information Protection-Authentifizierung verwendet werden soll. Dieser Benutzername muss mit einem Konto übereinstimmen, das für Office 365 oder Azure Active Directory verwendet wird. Das Konto muss auch mit einem Office 365-Mandanten gehören, die für die von vertraulichkeitsbezeichnungen in Office 365 Security & Compliance Center konfiguriert ist.

Wenn Sie verwenden möchten, melden Sie sich als ein anderer Benutzer in der folgenden angezeigt, finden Sie unter den [melden Sie sich als anderer Benutzer](clientv2-admin-guide-customizations.md#sign-in-as-a-different-user) Anweisungen.

Verwenden Sie die Informationen unter **Version**, um zu bestätigen, welche Version des Clients installiert ist. Sie können überprüfen, ob es sich um die neueste Version handelt release-Version und die entsprechenden Fixes und neuen Features durch Lesen der [Versionsinformationen für die Version](unifiedlabelingclient-version-release-history.md) für den Client.

## <a name="support-for-multiple-languages"></a>Unterstützung mehrerer Sprachen

Der einheitliche Bezeichnung Azure Information Protection-Client unterstützt alle Sprachen, die Office 365 unterstützt. Eine Liste dieser Sprachen finden Sie im Abschnitt **Office 365, Exchange Online-Schutz und Power BI** auf der Office-Seite zur [internationalen Verfügbarkeit](https://products.office.com/business/international-availability).

Für diese Sprachen, Menüoptionen, Dialogfelder und Meldungen von der Azure Information Protection werden einheitliche bezeichnungs-Client in der Sprache des Benutzers angezeigt. Es gibt ein Installationsprogramm, das die Sprache erkennt, weshalb keine weitere Konfiguration erforderlich ist, um die einheitliche Azure Information Protection-Bezeichnung-Client für verschiedene Sprachen zu installieren. 

Allerdings unterstützt der Azure Information Protection unified bezeichnungs-Client derzeit verschiedene Sprachen für die Bezeichnungen nicht. Darüber hinaus visuelle Kennzeichnungen werden nicht übersetzt und mehr als eine Sprache nicht unterstützt.

## <a name="post-installation-tasks"></a>Aufgaben nach der Installation

Nachdem Sie den Azure Information Protection unified bezeichnungs-Client installiert haben, stellen Sie sicher, dass Sie Benutzern Anweisungen dazu, wie auf ihre Dokumente und e-Mails bezeichnen und Anleitungen für die Bezeichnungen für bestimmte Szenarien auswählen bieten. Zum Beispiel:

- Online-Benutzeranweisungen: [Azure Information Protection – einheitliche bezeichnungs-Benutzerhandbuch](clientv2-user-guide.md)

- Herunterladen eines anpassbaren Leitfadens: [Azure Information Protection End User Adoption Guide](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf) (Endbenutzerhandbuch für die Einführung in Azure Information Protection)

## <a name="upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client"></a>Aktualisierung und das Verwalten des Azure Information Protection unified bezeichnungs-Clients

> [!NOTE]
> Die Azure Information Protection – einheitliche bezeichnungs Client unterstützt das Aktualisieren des Azure Information Protection-Clients als auch ein Upgrade von früheren Versionen des Azure Information Protection unified bezeichnungs-Clients.

Die Azure Information Protection-Team aktualisiert regelmäßig den einheitlichen Azure Information Protection-Bezeichnung-Client für die neuen Funktionen und Fehlerbehebungen. Ankündigungen werden auf der [Yammer-Website](https://www.yammer.com/AskIPTeam) des Teams veröffentlicht.

Wenn Sie Windows Update verwenden, aktualisiert der einheitliche Bezeichnung Azure Information Protection-Client automatisch die allgemein verfügbare Version dieses Clients, unabhängig davon, wie der Client installiert wurde. Neue Clientreleases werden wenige Wochen nach der Release im Katalog veröffentlicht.

Alternativ können Sie den Client manuell aktualisieren, indem Sie die neue Version aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen. Installieren Sie dann die neue Version, um ein Upgrade des Clients auszuführen. Sie müssen diese Methode verwenden, um Preview-Versionen und wenn Sie ein aus dem Azure Information Protection-Client Upgrade zu aktualisieren.

Wenn Sie aus dem Azure Information Protection-Client auf Windows 7 aktualisieren, werden alle Office-Anwendungen während des Clientupgrades automatisch neu gestartet. Diesen automatische Neustart wird nicht für neueren Betriebssystemen, oder wenn Sie ein von einer älteren Version des einheitlichen bezeichnungs-Clients Upgrade.

Bei einem manuellen Upgrade deinstallieren Sie die vorherige Version nur, wenn Sie die Installationsmethode ändern. Beispielsweise wechseln Sie von der ausführbaren Version (.exe) des Clients zur Windows Installer-Version (.msi) des Clients. Oder, wenn Sie eine frühere Version des Clients installieren müssen. Beispielsweise haben Sie die aktuelle Vorschauversion zu Testzwecken installiert und müssen nun auf die aktuelle allgemein verfügbare Version zurückgreifen.

Verwenden der [Version Versionsgeschichte und Supportrichtlinie](unifiedlabelingclient-version-release-history.md) , die Support-Richtlinie zu verstehen, für die Azure Information Protection – bezeichnungs-Client einheitliche, welche Versionen derzeit unterstützt werden, und die Neuigkeiten und Änderungen in Bezug auf die unterstützten frei. 

## <a name="uninstalling-the-azure-information-protection-unified-labeling-client"></a>Deinstallieren die Azure Information Protection unified bezeichnungs-client

Verwenden Sie eine der folgenden Optionen zur Deinstallation des Clients:

- Verwenden der Systemsteuerung, um ein Programm zu deinstallieren: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**.

- Führen Sie die ausführbare Datei erneut aus (z. B. **AzInfoProtection_UL.exe**), und von der **Setup ändern** auf **Deinstallieren**. 

- Führen Sie die ausführbare Datei mit **/uninstall** aus. Beispiel: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Nächste Schritte
Um den Client installieren zu können, finden Sie unter [Installieren des einheitlichen Azure Information Protection-Bezeichnung-Clients für Benutzer](clientv2-admin-guide-install.md).

Wenn Sie den Azure Information Protection-Client bereits installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei dessen Unterstützung:

- [Anpassungen](clientv2-admin-guide-customizations.md)

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


