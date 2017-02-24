---
title: "Azure Information Protection-Client – Administratorhandbuch | Azure Information Protection"
description: "Anweisungen und Informationen für Administratoren in einem Unternehmensnetzwerk, die für die Bereitstellung des Azure Information Protection-Clients für Windows zuständig sind."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f82c7964b16ad984ad920059e2f61f19ad0f471a
ms.openlocfilehash: dff30520c149c29663c340b70a12c427b31659b9


---


# <a name="azure-information-protection-client-administrator-guide"></a>Azure Information Protection-Client – Administratorhandbuch

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*


Verwenden Sie die folgenden Informationen, wenn Sie für den Azure Information Protection-Client in einem Unternehmensnetzwerk verantwortlich sind oder wenn Sie mehr technische Informationen erhalten möchten als vorhanden sind im [Azure Information Protection-Client – Benutzerhandbuch](client-user-guide.md).

Der Azure Information Protection-Client umfasst Folgendes:

- Ein Add-On für Office, das die Azure Information Protection-Leiste für Benutzer zum Auswählen der Klassifizierungsbezeichnungen sowie die Schaltfläche **Schützen** im Menüband für weitere Optionen installiert.

- Kontextmenüoptionen für den Windows-Datei-Explorer für Benutzer, um Klassifizierungsbezeichnungen und den entsprechenden Schutz auf Dateien anzuwenden.

- Ein Viewer zum Anzeigen geschützter Dateien, wenn diese von einer systemeigenen Anwendung nicht geöffnet werden können.

- Ein PowerShell-Modul zum Anwenden und Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien.

- Der Rights Management-Client, der mit Azure Rights Management (Azure RMS) oder Active Directory Rights Management Services (AD RMS) kommuniziert.

Der Azure Information Protection-Client ist am besten für die Arbeit mit seinen Azure-Diensten geeignet. Azure Information Protection und seine Datenschutzdienste, Azure Rights Management. Der Azure Information Protection-Client funktioniert mit einigen Einschränkungen auch mit der lokalen Version von Rights Management, AD RMS. Einen umfassenden Vergleich der Funktionen, die von Azure Information Protection und AD RMS unterstützt werden, finden Sie unter [Vergleich zwischen Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Wenn Sie über AD RMS verfügen und zu Azure Information Protection migrieren möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) nach.

**Haben Sie eine Frage, die in dieser Dokumentation nicht beantwortet wird?** Besuchen Sie unsere [Yammer-Website für Azure Information Protection](https://www.yammer.com/AskIPTeam). 


## <a name="should-you-deploy-the-azure-information-protection-client"></a>Sollten Sie den Azure Information Protection-Client bereitstellen?

Stellen Sie den Azure Information Protection-Client bereit, wenn eine der folgenden Optionen zutrifft:

- Sie möchten Dokumente und E-Mails durch Auswählen von Bezeichnungen innerhalb Ihrer Office-Anwendungen (Word, Excel, PowerPoint, Outlook) klassifizieren (und optional schützen).

- Sie möchten Dokumente und E-Mails mithilfe des Datei-Explorers klassifizieren (und optional schützen), der zusätzliche Dateitypen, die Auswahl mehrerer Objekte und Ordner unterstützt.

- Sie möchten Skripts ausführen, die Dokumente mithilfe von PowerShell-Befehlen klassifizieren (und optional schützen).

- Sie möchten geschützte Dokumente anzeigen, wenn eine systemeigene Anwendung zum Anzeigen der Datei nicht installiert ist oder diese Dokumente nicht öffnen kann.

- Sie möchten Dateien mithilfe des Datei-Explorers oder mithilfe von PowerShell-Befehlen nur schützen.

- Sie möchten, dass Benutzer und Administratoren in der Lage sind, geschützte Dokumente nachzuverfolgen und den Schutz zu widerrufen.

- Sie möchten die Verschlüsselung von Dateien und Containern für Datenwiederherstellungszwecke in Massen entfernen (Schutz aufheben).

- Sie führen Office 2010 aus und möchten Dokumente und E-Mails-mithilfe des Azure Rights Management-Diensts schützen.

Beispiel zur Veranschaulichung des Azure Information Protection-Client-Add-Ons in Office-Anwendungen, in dem die Klassifizierungsbezeichnungen für Ihre Organisation und die neue Schaltfläche **Schützen** im Menüband angezeigt wird:

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/info-protect-bar-default.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Installieren des Azure Information Protection-Clients für Benutzer

Überprüfen Sie vor der Installation des Clients, ob Sie über die erforderlichen Betriebssystemversionen und Anwendungen für den Azure Information Protection-Client verfügen: [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md). 

Zusätzlich:

- Die vollständige Installation des Azure Information Protection-Clients erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.

- Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom Installationsprogramm nicht heruntergeladen oder installiert.

- Computer unter Windows 7 Service Pack 1 benötigen [KB 2533623](https://support.microsoft.com/en-us/kb/2533623). Diese Option kann nach der Installation des Clients installiert werden. Wenn dieses Update erforderlich, aber noch nicht installiert ist, werden Sie zur Installation aufgefordert.

> [!NOTE]
> Für diese Installation sind lokale Administratorrechte erforderlich.

Zusätzlich zur Verwendung der folgenden Anweisungen ist der Azure Information Protection-Client auch im Microsoft Update-Katalog enthalten. Sie können deshalb den Client mit einem beliebigem Softwareupdatedienst installieren und aktualisieren, der den Katalog nutzt. 

1. Laden Sie den Azure Information Protection-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter. 

2. Für eine Standardinstallation führen Sie einfach die ausführbare Datei **AzInfoProtection.exe** aus. Führen Sie die ausführbare Datei mit dem Parameter **/help** aus, um zuvor die Installationsoptionen anzuzeigen: `AzInfoProtection.exe /help`

   Beispiel zum automatischen Installieren des Clients: `AzInfoProtection.exe /quiet`
   
   Beispiel zum automatischen Installieren der PowerShell-Befehle: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
   
   Wenn Sie den Client zudem auf Computern installieren, die Office 2010 ausführen, müssen Sie den Parameter **ServiceLocation** angeben (nicht auf dem Hilfebildschirm enthalten), wenn Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind. Weitere Informationen finden Sie im nächsten Abschnitt.

3. Wenn Sie die interaktive Installation verwenden und sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer **Demorichtlinie**, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.
    
4. So schließen Sie die Installation ab: 

    - Starten Sie den Computer neu, wenn darauf Office 2010 ausgeführt wird. 
        
        Wenn der Client nicht mit dem Parameter „ServiceLocation“ installiert wurde, müssen Sie alle Aufforderungen zum Aktualisieren der Registrierung für diese erste Verwendung bestätigen, wenn Sie erstmalig eine der Office-Anwendungen öffnen, die die Azure Information Protection-Leiste verwenden (z. B. Word). [Dienstermittlung](../rms-client/client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. 
        


### <a name="additional-instructions-for-office-2010-only"></a>Zusätzliche Anweisungen für Office 2010

Geben Sie den „ServiceLocation“-Parameter und die URL für Ihren Azure Rights Management-Dienst an, wenn Sie den Client für Benutzer installieren, die Office 2010 verwenden und nicht über lokale Administratorrechte verfügen. Dieser Parameter und Wert erstellt die folgenden Registrierungsschlüssel und legt sie fest:

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation

HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

Verwenden Sie das folgende Verfahren, um den Wert zu identifizieren, den Sie für den ServiceLocation-Parameter angeben. 

#### <a name="to-identify-the-value-to-specify-for-the-servicelocation-parameter"></a>So identifizieren Sie die Wert, der für den ServiceLocation-Parameter angegeben wird

1. Führen Sie aus einer PowerShell-Sitzung zuerst [Connect-AadrmService](https://docs.microsoft.com/powershell/aadrm/vlatest/connect-aadrmservice) aus, und geben Sie Ihre Administratoranmeldeinformationen an, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen. Führen Sie dann [Get-AadrmConfiguration](https://docs.microsoft.com/powershell/aadrm/vlatest/get-aadrmconfiguration) aus. 
 
    Wenn Sie das PowerShell-Modul für den Azure Rights Management-Dienst noch nicht installiert haben, lesen Sie [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2. Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.

    Beispiel: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Entfernen Sie im Wert den Text **/_wmcs/licensing** aus der Zeichenfolge. Zum Beispiel: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Die verbleibende Zeichenfolge ist der Wert, der für Ihren ServiceLocation-Parameter angegeben wird.

Beispiel zum automatischen Installieren des Clients für Office 2010 und Azure RMS: `AzInfoProtection.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com`


## <a name="to-uninstall-the-azure-information-protection-client"></a>Deinstallieren des Azure Information Protection-Clients

Sie können jede beliebige Option verwenden:

- Deinstallieren Sie ein Programm über die Systemsteuerung: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**

- Führen Sie die ausführbare Datei (z. B. **AzInfoProtection.exe**) erneut aus, und klicken Sie auf der Seite **Setup ändern** auf **Deinstallieren**. 

- Führen Sie die ausführbare Datei mit **/uninstall** aus. Beispiel: `AzInfoProtection.exe /uninstall`


## <a name="to-verify-installation-connection-status-or-send-feedback"></a>So überprüfen Sie die Installation und den Verbindungsstatus oder senden Feedback

1. Öffnen Sie eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen) und anschließend auf **Help and feedback** (Hilfe und Feedback).

2. Beachten Sie im Dialogfeld **Microsoft Azure Information Protection** Folgendes:

    - Im Abschnitt **Clientstatus**: Überprüfen Sie anhand des Werts von**Version**, ob die Installation erfolgreich war. Außerdem erkennen Sie, wann sich der Client zuletzt mit dem Azure Information Protection-Dienst Ihrer Organisation verbunden hat und wann die Azure Information Protection-Richtlinie zuletzt installiert oder aktualisiert wurde. Wenn der Client eine Verbindung mit dem Dienst herstellt, lädt er automatisch die letzte Richtlinie herunter (sofern diese von der aktuellen Richtlinie abweicht). Wenn Sie nach dem angezeigten Zeitpunkt Änderungen vorgenommen haben, schließen Sie die Office-Anwendung, und öffnen Sie sie erneut.
    
        Ihr ebenfalls angezeigter Benutzername gibt das Konto an, mit dem Sie bei Azure Information Protection authentifiziert werden. Der Benutzername muss zu einem für Office 365 oder Azure Active Directory verwendeten Konto passen, und es muss zu einem Mandanten gehören, der für Azure Information Protection konfiguriert ist.

    - Im Abschnitt**Hilfe und Feedback**: Der Link **Weitere Infos** verweist standardmäßig auf die [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection)-Website. Sie können aber auch eine benutzerdefinierte URL als eine der [Richtlinieneinstellungen](../deploy-use/configure-policy-settings.md) in der Azure Information Protection-Richtlinie festlegen.
        
        Verwenden Sie den Link **Feedback senden**, um Vorschläge oder Anfragen an das Information Protection-Team zu senden. Verwenden Sie diese Option nicht für den technischen Support, sondern nutzen Sie dafür stattdessen die [Supportoptionen und Communityressourcen](../get-started/information-support.md#support-options-and-community-resources). 
    
        Um Diagnoseinformationen zu erhalten und den Client zurückzusetzen, klicken Sie auf **Diagnose ausführen**. Wenn die Diagnosetests abgeschlossen sind, klicken Sie auf **Ergebnisse kopieren**, um die Informationen in eine E-Mail einzufügen, die Sie an Ihr Helpdesk oder den Microsoft Support senden können. Wenn die Tests abgeschlossen sind, können Sie auch den Client zurücksetzen.
        
        Weitere Informationen zur Option **Zurücksetzen**:
        
        - Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 
        
        - Außer wenn Dateien gesperrt sind, löscht diese Aktion alle Dateien im Ordner **%localappdata%\Microsoft\MSIPC**, in dem Clientzertifikate und Rights Management-Vorlagen gespeichert werden. Die Azure Information Protection-Richtlinie oder Clientprotokolldateien werden nicht gelöscht, und der Benutzer wird nicht abgemeldet.
        
        - Der folgende Registrierungsschlüssel wird samt Einstellungen gelöscht: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Wenn Sie Einstellungen für diesen Registrierungsschlüssel konfigurieren (z. B. Einstellungen für die Umleitung zu Ihrem Azure Information Protection-Mandanten, da Sie von AD RMS zu Azure Information Protection migrieren und noch einen Dienstverbindungspunkt in Ihrem Netzwerk haben), müssen Sie die Registrierungseinstellungen nach dem Zurücksetzen des Clients neu konfigurieren.
        
        - Nachdem Sie den Client zurückgesetzt haben, müssen Sie die Benutzerumgebung erneut initialisieren (was auch als „Bootstrapping“ bezeichnet wird). Dabei werden die Zertifikate für den Client und die neuesten Vorlagen heruntergeladen. Schließen Sie hierzu alle Instanzen von Office, und starten Sie eine Office-Anwendung neu. Diese Aktion prüft außerdem, ob Sie die neueste Azure Information Protection-Richtlinie heruntergeladen haben. Führen Sie die Diagnose erst erneut aus, nachdem Sie dies getan haben.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection-Client installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO2-->


