---
title: Installieren des Azure Information Protection-Clients | Azure Information Protection
description: "Anweisungen zum Installieren des Clients, durch den Ihren Office-Anwendungen eine Information Protection-Leiste hinzugefügt wird, damit Sie Klassifizierungsbezeichnungen für Ihre Dokumente und E-Mails auswählen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4445adff-4c5a-450f-aff8-88bf5bd4ca78
translationtype: Human Translation
ms.sourcegitcommit: 23c437479c756f2a9335606e686f117d514a38f6
ms.openlocfilehash: 71972b0a057b1958dfa5e5b4af41b65d5080a086


---

# <a name="installing-the-azure-information-protection-client"></a>Installieren des Azure Information Protection-Clients

>*Gilt für: Azure Information Protection*

Um Dokumente und E-Mail-Nachrichten mithilfe von Azure Information Protection zu klassifizieren, müssen Sie zunächst den Azure Information Protection-Client installieren. Durch diese Installation wird eine Information Protection-Leiste zu Ihren Office-Anwendungen (Word, Excel, PowerPoint, Outlook) hinzugefügt, auf der die Klassifizierungsbezeichnungen für Ihre Organisation angezeigt werden. Außerdem wird auf der Registerkarte **Start** (Word, Excel, PowerPoint) eine neue Gruppe **Protection** (Schutz) mit einer Schaltfläche **Protect** (Schützen) angezeigt:

Die folgende Abbildung zeigt diese Information Protection-Leiste sowie die Bezeichnungen der [Standardrichtlinie](../deploy-use/configure-policy-default.md):

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/info-protect-bar-default.png)

Laden Sie den Azure Information Protection-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter. Derzeit können Sie die Version zur allgemeinen Verfügbarkeit (General Availability, GA) und die Vorschauversion installieren. Die Vorschauversion enthält neue Funktionen für Evaluierungszwecke und unterliegt Änderungen. Weitere Informationen finden Sie in der folgenden Blogbeitragsankündigung: [Azure Information Protection – Dezember-Vorschau jetzt verfügbar](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/).

Überprüfen Sie vor der Installation des Clients, ob Sie über die erforderlichen Betriebssystemversionen und Anwendungen für den Azure Information Protection-Client verfügen: [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md). Für die Vorschauversion des Clients benötigen Computer mit Windows 7 SP1 zudem [KB 2533623](https://support.microsoft.com/en-us/kb/2533623), die nach der Installation des Clients installiert werden kann. Wenn dieses Update erforderlich, aber noch nicht installiert ist, werden Sie zur Installation aufgefordert.

## <a name="to-install-the-azure-information-protection-client-manually"></a>Manuelle Installation des Azure Information Protection-Clients

1. Nachdem Sie den [Client heruntergeladen haben](https://www.microsoft.com/en-us/download/details.aspx?id=53018), führen Sie die ausführbare Datei wie **AzInfoProtection.exe** aus, und befolgen Sie die Aufforderungen, um den Client zu installieren. Für diese Installation sind lokale Administratorrechte erforderlich.

    Wenn Sie sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer Demorichtlinie, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt. 

2. So beginnen Sie mit der Verwendung des Azure Information Protection-Clients: Wenn auf Ihrem Computer Office 2010 ausgeführt wird, starten Sie Ihren Computer neu. Bei anderen Office-Versionen starten Sie eine beliebige Office-Anwendung neu.

## <a name="to-install-the-azure-information-protection-client-for-users"></a>Installieren des Azure Information Protection-Clients für Benutzer

Sie können die Installation des Azure Information Protection-Clients mithilfe von Befehlszeilenoptionen in Skripts automatisieren. Führen Sie die ausführbare Datei mit **/help** aus, um die Installationsoptionen anzuzeigen. Beispiel: `AzInfoProtection.exe /help`.

Beispiel zum automatischen Installieren des Clients: `AzInfoProtection.exe /passive | quiet`

Die Version zur allgemeinen Verfügbarkeit des Azure Information Protection-Clients ist auch im Microsoft Update-Katalog enthalten. Sie können deshalb den Client mit einem beliebigem Softwareupdatedienst installieren und aktualisieren, der den Katalog nutzt. Die Vorschauversionen des Clients sind nicht im Microsoft Update-Katalog enthalten.

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



<!--HONumber=Dec16_HO1-->


