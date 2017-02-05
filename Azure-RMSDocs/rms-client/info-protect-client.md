---
title: Installieren des Azure Information Protection-Clients | Azure Information Protection
description: "Anweisungen zum Installieren des Clients, durch den Ihren Office-Anwendungen eine Information Protection-Leiste hinzugefügt wird, damit Sie Klassifizierungsbezeichnungen für Ihre Dokumente und E-Mails auswählen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 6012049162d0ac9ee53476640ab3a4bcac18287f
ms.openlocfilehash: 92d6b6f13d124c8c7ab7735fa170890263c9011b


---

# <a name="installing-the-azure-information-protection-client"></a>Installieren des Azure Information Protection-Clients

>*Gilt für: Azure Information Protection*

Um Dokumente und E-Mail-Nachrichten mithilfe von Azure Information Protection zu klassifizieren, müssen Sie zunächst den Azure Information Protection-Client installieren. Durch diese Installation wird eine Information Protection-Leiste zu Ihren Office-Anwendungen (Word, Excel, PowerPoint, Outlook) hinzugefügt, auf der die Klassifizierungsbezeichnungen für Ihre Organisation angezeigt werden. Außerdem wird auf der Registerkarte **Start** (Word, Excel, PowerPoint) eine neue Gruppe **Protection** (Schutz) mit einer Schaltfläche **Protect** (Schützen) angezeigt:

Die folgende Abbildung zeigt diese Information Protection-Leiste sowie die Bezeichnungen der [Standardrichtlinie](../deploy-use/configure-policy-default.md):

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/info-protect-bar-default.png)

Laden Sie den Azure Information Protection-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter. Derzeit können Sie die Version zur allgemeinen Verfügbarkeit (General Availability, GA) und die Vorschauversion installieren. Die Vorschauversion enthält neue Funktionen für Evaluierungszwecke und unterliegt Änderungen. Weitere Informationen finden Sie in der folgenden Blogbeitragsankündigung: [Azure Information Protection – Dezember-Vorschau jetzt verfügbar](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/).

Überprüfen Sie vor der Installation des Clients, ob Sie über die erforderlichen Betriebssystemversionen und Anwendungen für den Azure Information Protection-Client verfügen: [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md). Für die Vorschauversion des Clients benötigen Computer mit Windows 7 SP1 zudem [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), die nach der Installation des Clients installiert werden kann. Wenn dieses Update erforderlich, aber noch nicht installiert ist, werden Sie zur Installation aufgefordert.


## <a name="to-install-the-azure-information-protection-client-manually"></a>Manuelle Installation des Azure Information Protection-Clients

> [!NOTE]
> Für diese Installation sind lokale Administratorrechte erforderlich.

    
1. Nachdem Sie den [Client heruntergeladen haben](https://www.microsoft.com/en-us/download/details.aspx?id=53018), führen Sie die ausführbare Datei wie **AzInfoProtection.exe** aus, und befolgen Sie die Aufforderungen, um den Client zu installieren.
    
    Wenn Sie sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer **Demorichtlinie**, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.
    
    Weitere Informationen darüber, was installiert wird:

    - Die Version zur allgemeinen Verfügbarkeit installiert die Azure Information Protection-Leiste für die Office-Anwendungen. 
    
    - Die aktuelle Vorschauversion des Clients installiert die Azure Information Protection-Leiste für die Office-Anwendungen. Klicken Sie mit der rechten Maustaste auf „Optionen“ für den Datei-Explorer, einen Viewer für geschützte Dateien und Windows PowerShell-Cmdlets zur gleichzeitigen Klassifizierung und zum Schutz von Dateien. 
        
        Beachten Sie, dass Sie nur das PowerShell-Modul (RMSProtection) durch Angeben des Parameters **PowerShellOnly = True** installieren können. Beispiel: `AzInfoProtection_PREVIEW_1.3.98.0.exe  PowerShellOnly=true`

2. So schließen Sie die Installation ab: 

    - Starten Sie den Computer neu, wenn darauf Office 2010 ausgeführt wird. 
        
        **Wenn Sie die Vorschauversion des Clients installiert haben**: Öffnen Sie zusätzlich zum Neustart Ihres Computers eine der Office-Anwendungen, die die Azure Information Protection-Leiste verwenden (z.B. Word), und bestätigen Sie alle Aufforderungen, die Registrierung für diese erste Verwendung zu aktualisieren. [Dienstermittlung](../rms-client/client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - Bei anderen Office-Versionen starten Sie eine beliebige Office-Anwendung neu. 
        
        **Wenn Sie die Vorschauversion des Clients installiert haben**: Schließen Sie zusätzlich zum Neustart von Office-Anwendungen den Datei-Explorer, und starten Sie ihn erneut.

## <a name="to-install-the-azure-information-protection-client-for-users"></a>Installieren des Azure Information Protection-Clients für Benutzer

Sie können die Installation des Azure Information Protection-Clients mithilfe von Befehlszeilenoptionen in Skripts automatisieren. Führen Sie die ausführbare Datei mit **/help** aus, um die Installationsoptionen anzuzeigen. Beispiel: `AzInfoProtection.exe /help`

Beispiel für die unbeaufsichtigte Installation der Version zur allgemeinen Verfügbarkeit des Clients: `AzInfoProtection.exe /quiet`

Beispiel für die unbeaufsichtigte Installation mit dem Preview-Client von einzig und allein dem PowerShell-Modul: `AzInfoProtection_PREVIEW_1.3.98.0.exe  PowerShellOnly=true /quiet`

Wenn Sie die Vorschauversion des Clients auf Computern installieren, die Office 2010 ausführen, geben Sie den Parameter **ServiceLocation** an, wenn Benutzer keine lokalen Administratoren auf ihren Computern sind. Weitere Informationen finden Sie im nächsten Abschnitt.

Der Azure Information Protection-Client ist auch im Microsoft Update-Katalog enthalten. Sie können deshalb den Client mit einem beliebigem Softwareupdatedienst installieren und aktualisieren, der den Katalog nutzt. 

### <a name="preview-version-and-office-2010-only"></a>Nur Vorschauversion und Office 2010

Geben Sie bei der Installation des Clients für Benutzer den ServiceLocation-Parameter und die URL für Ihren Azure Rights Management-Dient für die Vorschauversion des Clients und Office 2010 an. Dieser Parameter und Wert erstellt die folgenden Registrierungsschlüssel und legt sie fest:

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


## <a name="to-verify-installation-connection-status-or-report-a-problem"></a>Überprüfen der Installation und des Verbindungsstatus oder Melden von Problemen

1. Öffnen Sie eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen) und anschließend auf **Help and feedback** (Hilfe und Feedback).

2. Beachten Sie im Dialogfeld **Microsoft Azure Information Protection** Folgendes:

    - Im Abschnitt **Clientstatus**: Überprüfen Sie anhand des Werts von**Version**, ob die Installation erfolgreich war. Außerdem erkennen Sie, wann sich der Client zuletzt mit dem Azure Information Protection-Dienst Ihrer Organisation verbunden hat und wann die Azure Information Protection-Richtlinie zuletzt installiert oder aktualisiert wurde. Wenn der Client eine Verbindung mit dem Dienst herstellt, lädt er automatisch die letzte Richtlinie herunter (sofern diese von der aktuellen Richtlinie abweicht). Wenn Sie nach dem angezeigten Zeitpunkt Änderungen vorgenommen haben, schließen Sie die Office-Anwendung, und öffnen Sie sie erneut.
    
        Ihr ebenfalls angezeigter Benutzername gibt das Konto an, mit dem Sie bei Azure Information Protection authentifiziert werden. Der Benutzername muss zu einem für Office 365 oder Azure Active Directory verwendeten Konto passen, und es muss zu einem Mandanten gehören, der für Azure Information Protection konfiguriert ist.

    - Im Abschnitt**Hilfe und Feedback**: Der Link **Weitere Infos** verweist standardmäßig auf die [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection)-Website. Sie können aber auch eine benutzerdefinierte URL als eine der [Richtlinieneinstellungen](../deploy-use/configure-policy-settings.md) in der Azure Information Protection-Richtlinie festlegen.
        
        Über den Link **Feedback senden** können Sie automatisch Clientprotokolle an eine E-Mail-Nachricht anfügen, um diese zur Untersuchung eines Problems an das Information Protection-Team zu senden. 
    
        Um Diagnoseinformationen zu erhalten und den Client zurückzusetzen, klicken Sie auf **Diagnose ausführen**. Wenn die Diagnosetests abgeschlossen sind, klicken Sie auf **Ergebnisse kopieren**, um die Informationen in eine E-Mail einzufügen, die Sie an Ihr Helpdesk oder den Microsoft Support senden können. Wenn die Tests abgeschlossen sind, können Sie auch den Client zurücksetzen.
        
        Weitere Informationen zur Option **Zurücksetzen**:
        
        - Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 
        
        - Außer wenn Dateien gesperrt sind, löscht diese Aktion alle Dateien im Ordner **%localappdata%\Microsoft\MSIPC**, in dem Clientzertifikate und Rights Management-Vorlagen gespeichert werden. Die Azure Information Protection-Richtlinie oder Clientprotokolldateien werden nicht gelöscht, und der Benutzer wird nicht abgemeldet.
        
        - Der folgende Registrierungsschlüssel wird samt Einstellungen gelöscht: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Wenn Sie Einstellungen für diesen Registrierungsschlüssel konfigurieren (z. B. Einstellungen für die Umleitung zu Ihrem Azure Information Protection-Mandanten, da Sie von AD RMS zu Azure Information Protection migrieren und noch einen Dienstverbindungspunkt in Ihrem Netzwerk haben), müssen Sie die Registrierungseinstellungen nach dem Zurücksetzen des Clients neu konfigurieren.
        
        - Nachdem Sie den Client zurückgesetzt haben, müssen Sie die Benutzerumgebung erneut initialisieren (was auch als „Bootstrapping“ bezeichnet wird). Dabei werden die Zertifikate für den Client und die neuesten Vorlagen heruntergeladen. Schließen Sie hierzu alle Instanzen von Office, und starten Sie eine Office-Anwendung neu. Diese Aktion prüft außerdem, ob Sie die neueste Azure Information Protection-Richtlinie heruntergeladen haben. Führen Sie die Diagnose erst erneut aus, nachdem Sie dies getan haben.


## <a name="usage-logging"></a>Nutzungsprotokollierung

**[Dieses Feature erfordert die Vorschauversion des Clients und unterliegt Änderungen.]**

Für die Vorschauversion des Azure Information Protection-Clients protokolliert der Client die Benutzeraktivität im lokalen Windows-**Anwendungen und Dienste**-Ereignisprotokoll, **Azure Information Protection**. Die Ereignisse umfassen die folgenden Informationen:

- Datum, Clientversion, Richtlinien-ID

- Angemeldeter Benutzername, Computername

- Dateiname und Speicherort

- Aktion:

    - Bezeichnung festlegen: Informationen ID 101
    
    - Bezeichnung festlegen (niedriger): Informations-ID 102
    
    - Bezeichnung festlegen (höher): Informations-ID 103
    
    - Bezeichnung entfernen: Informations-ID 104
   
    - Empfohlener Tipp: Information 105
    
    - Benutzerdefinierten Schutz anwenden: Informations-ID 201
    
    - Benutzerdefinierten Schutz entfernen: Informations-ID 202
    
    - Anmelden (betriebsbereit): Informations-ID 902
    
    - Richtlinie herunterladen (betriebsbereit): Informations-ID 901
    
- Aktionsquelle:
    
    - Manuell 
    
    - Empfohlen
    
    - Automatisch  
    
    - System (zum Anmelden und Herunterladen der Richtlinie)
    
- Bezeichnung vor und nach Aktion 
    
- Schutz vor und nach Aktion
    
- Benutzerausrichtung (falls zutreffend)
    

## <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Tastenkombinationen für die Azure Information Protection-Leiste

Für den Zugriff auf die Azure Information Protection-Leiste über Tastenkürzel können Sie die folgenden Tastenkombinationen nutzen:

- Drücken Sie **STRG** + **UMSCHALT** + **~** 

Verwenden Sie dann die TAB-TASTE, um die Bezeichnungen und andere Steuerelemente auf der Leiste auszuwählen (die Symbole**Bezeichnungen ausblenden** und **Bezeichnung entfernen**), und drücken Sie die EINGABETASTE, um sie auszuwählen.


## <a name="file-locations"></a>Dateispeicherorte

Clientdateien:   

- Für 64-Bit-Betriebssysteme: **\ProgramFiles (x86)\Microsoft Azure Information Protection**

- Für 32-Bit-Betriebssysteme: **\Programme\Microsoft Azure Information Protection**

Clientprotokolldateien und aktuell installierte Richtliniendatei:

- Für 64-Bit- und 32-Bit-Betriebssysteme: **%localappdata%\Microsoft\MSIP**


## <a name="next-steps"></a>Nächste Schritte

Um die Bezeichnungen auf der Information Protection-Leiste zu ändern, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](../deploy-use/configure-policy.md).

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

Im [Verlauf der Versionsveröffentlichung](client-version-release-history.md) finden Sie die Informationen zu veröffentlichten Versionen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO5-->


