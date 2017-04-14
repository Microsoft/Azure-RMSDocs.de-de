---
title: "Azure Information Protection-Client – Administratorhandbuch"
description: "Anweisungen und Informationen für Administratoren in einem Unternehmensnetzwerk, die für die Bereitstellung des Azure Information Protection-Clients für Windows zuständig sind."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d442a9540243cd020b885f7dc2c13d999bbad868
ms.sourcegitcommit: 7b773ca5bf1abf30e527c34717ecb2dc96f88033
translationtype: HT
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

Der Azure Information Protection-Client ist am besten für die Arbeit mit seinen Azure-Diensten geeignet. Azure Information Protection und seine Datenschutzdienste, Azure Rights Management. Der Azure Information Protection-Client funktioniert mit einigen Einschränkungen auch mit der lokalen Version von Rights Management, AD RMS. Einen umfassenden Vergleich der Funktionen, die von Azure Information Protection und AD RMS unterstützt werden, finden Sie unter [Vergleich zwischen Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). 

Wenn Sie über AD RMS verfügen und zu Azure Information Protection migrieren möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) nach.

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

![Azure Information Protection-Leiste mit Standardrichtlinie](../media/word2016-calloutsv2.png)

## <a name="how-to-install-the-azure-information-protection-client-for-users"></a>Installieren des Azure Information Protection-Clients für Benutzer

Überprüfen Sie vor der Installation des Clients, ob Sie über die erforderlichen Betriebssystemversionen und Anwendungen für den Azure Information Protection-Client verfügen: [Anforderungen für Azure Information Protection](../get-started/requirements-azure-rms.md). 

Zusätzliche Voraussetzungen für den Azure Information Protection-Client:

- Die vollständige Installation des Azure Information Protection-Clients erfordert standardmäßig Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden. Sie können diese Anforderung mit einem benutzerdefinierten Installationsparameter umgehen. Diese Vorgehensweise wird nicht empfohlen.

- Wenn der Azure Information Protection-Viewer separat installiert wird, ist Microsoft .NET Framework 4.5.2 oder höher erforderlich. Wenn diese Version fehlt, wird sie vom Installationsprogramm nicht heruntergeladen oder installiert.

- Das PowerShell-Modul erfordert Windows PowerShell, Version 4.0. Dieses muss auf älteren Betriebssystemen ggf. installiert werden. Weitere Informationen finden Sie unter [How to Install Windows PowerShell 4.0](http://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Installieren von Windows PowerShell 4.0). Das Installationsprogramm überprüft oder installiert diese erforderlichen Komponenten nicht für Sie. Zum Überprüfen, welche Version von Windows PowerShell auf dem Computer ausgeführt wird, geben Sie **$PSVersionTable** in einer PowerShell-Sitzung ein.

- Computer unter Windows 7 Service Pack 1 benötigen KB 2533623. Weitere Informationen zu diesem Update finden Sie unter [Microsoft-Sicherheitsempfehlung: Unsichere Bibliothekladevorgänge können eine Codeausführung von Remotestandorten aus ermöglichen](https://support.microsoft.com/en-us/kb/2533623). Möglicherweise können Sie dieses Update direkt installieren, oder ein anderes Update könnte Vorrang haben, das es für Sie installiert.
    
    Wenn dieses Update benötigt wird und nicht installiert ist, werden Sie in der Clientinstallation gewarnt, dass es installiert werden muss. Dieses Update kann nach der Installation des Clients installiert werden, aber einige Aktionen werden blockiert, und die Meldung wird erneut angezeigt.  

> [!NOTE]
> Für diese Installation sind lokale Administratorrechte erforderlich.

Der Azure Information Protection-Client ist auch im Microsoft Update-Katalog enthalten. Sie können deshalb den Client mit einem beliebigem Softwareupdatedienst installieren und aktualisieren, der den Katalog nutzt. 

1. Laden Sie den Azure Information Protection-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunter. 
    
    Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen. 

2. Führen Sie für eine Standardinstallation einfach die ausführbare Datei aus, z.B. **AzInfoProtection.exe**. Führen Sie die ausführbare Datei mit dem Parameter **/help** aus, um zuvor die Installationsoptionen anzuzeigen: `AzInfoProtection.exe /help`

    Beispiel zum automatischen Installieren des Clients: `AzInfoProtection.exe /quiet`
    
    Beispiel zum automatischen Installieren der PowerShell-Befehle: `AzInfoProtection.exe  PowerShellOnly=true /quiet`
    
    Diese zusätzlichen Parameter sind im Hilfebildschirm nicht aufgelistet:
    
    - **ServiceLocation**: Verwenden Sie diesen Parameter, wenn Sie den Client auf Computern installieren, die Office 2010 ausführen, und Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind, oder wenn Sie keine Eingabeaufforderung für die Benutzer anzeigen lassen möchten. [Weitere Informationen](#more-information-about-the-servicelocation-installation-parameter) 
    
    - **DowngradeDotNetRequirement**: Verwenden Sie diesen Parameter, um die Notwendigkeit von Microsoft Framework .NET, Version 4.6.2, zu umgehen. [Weitere Informationen](#more-information-about-the-downgradedotnetrequirement-installation-parameter)

3. Wenn Sie die interaktive Installation verwenden und sich nicht mit Office 365 oder Azure Active Directory verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer **Demorichtlinie**, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.
    
4. So schließen Sie die Installation ab: 

    - Starten Sie den Computer neu, wenn darauf Office 2010 ausgeführt wird. 
        
        Wenn der Client nicht mit dem Parameter „ServiceLocation“ installiert wurde, müssen Sie alle Aufforderungen zum Aktualisieren der Registrierung für diese erste Verwendung bestätigen, wenn Sie erstmalig eine der Office-Anwendungen öffnen, die die Azure Information Protection-Leiste verwenden (z. B. Word). [Dienstermittlung](../rms-client/client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. 
        
5. Sie können anhand der standardmäßig im Ordner „%temp%“ erstellten Installationsprotokolldatei überprüfen, ob die Installation erfolgreich war. Sie können diesen Speicherort mit dem Installationsparameter **/log** ändern. 
 
    Der Name der Datei weist das folgende Format auf: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`.
    
    Beispiel: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Suchen Sie in dieser Protokolldatei nach der folgenden Zeichenfolge: **Product: Microsoft Azure Information Protection -- Installation completed successfully** (Produkt: Microsoft Azure Information Protection – Installation erfolgreich abgeschlossen). Wenn Fehler bei der Installation auftreten, enthält diese Protokolldatei Informationen, anhand derer Sie Probleme erkennen und diese beheben können.

### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Weitere Informationen zum ServiceLocation-Installationsparameter

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


### <a name="more-information-about-the-downgradedotnetrequirement-installation-parameter"></a>Weitere Informationen zum DowngradeDotNetRequirement-Installationsparameter

Um automatische Upgrades über Windows Update zu unterstützen und für eine zuverlässige Integration in Office-Anwendungen zu sorgen, verwendet der Azure Information Protection-Client die Microsoft .NET Framework-Version 4.6.2. Diese Installation prüft standardmäßig, ob diese Version vorhanden ist, und versucht sie zu installieren, falls sie nicht vorhanden ist. Die Installation erfordert einen Neustart des Computers.

Wenn die Installation dieser höheren Version von Microsoft .NET Framework nicht praktikabel ist, können Sie den Client mit dem auf „True“ festgelegten Parameter **DowngradeDotNetRequirement** installieren. Dadurch wird dieses Erfordernis umgangen, wenn Microsoft .NET Framework, Version 4.5.1, installiert ist.

Beispiel: `AzInfoProtection.exe DowngradeDotNetRequirement=True`

Wir empfehlen, diesen Parameter mit Vorsicht zu verwenden, da uns Probleme mit Office-Anwendungen gemeldet wurden, die nicht mehr reagieren, wenn der Azure Information Protection-Client mit dieser älteren Version von Microsoft .NET Framework verwendet wird. Wenn Sie Probleme mit nicht mehr reagierenden Anwendungen bemerken, aktualisieren Sie auf die empfohlene Version, bevor Sie andere Problembehandlungslösungen versuchen. 

Denken Sie auch an Folgendes: Wenn Sie Windows Update zum Aktualisieren des Azure Information Protection-Clients verwenden, benötigen Sie einen anderen Mechanismus für die Softwarebereitstellung, um den Client auf höhere Versionen zu aktualisieren.

## <a name="additional-checks-and-troubleshooting"></a>Zusätzliche Prüfungen und Problembehandlung

Verwenden Sie die Option **Hilfe und Feedback**, um das Dialogfeld **Microsoft Azure Information Protection** zu öffnen:

- In einer Office-Anwendung: Wählen Sie auf der Registerkarte **Start** in der Gruppe **Schutz** die Optionen **Schützen** und anschließend **Hilfe und Feedback** aus.

- Im Datei-Explorer: Klicken Sie mit der rechten Maustaste auf eine oder mehrere Dateien oder einen Ordner, wählen Sie **Klassifizieren und schützen** und dann **Hilfe und Feedback** aus. 

### <a name="help-and-feedback-section"></a>Abschnitt **Hilfe und Feedback**

Der Link **Weitere Infos** verweist standardmäßig auf die [Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)-Website. Sie können aber auch eine benutzerdefinierte URL als eine der [Richtlinieneinstellungen](../deploy-use/configure-policy-settings.md) in der Azure Information Protection-Richtlinie festlegen.

Verwenden Sie den Link **Feedback senden**, um Vorschläge oder Anfragen an das Information Protection-Team zu senden. Verwenden Sie diese Option nicht für den technischen Support, sondern nutzen Sie dafür stattdessen die [Supportoptionen und Communityressourcen](../get-started/information-support.md#support-options-and-community-resources). 

Die Option **Protokolle exportieren** dient dazu, Protokolldateien für den Azure Information Protection-Client automatisch zu erfassen und anzuhängen, wenn Sie darum gebeten wurden, diese an den Microsoft Support zu senden. Diese Option kann auch von Endbenutzern verwendet werden, um diese Dateien an Ihren Helpdesk zu senden.

Um Diagnoseinformationen zu erhalten und den Client zurückzusetzen, wählen Sie **Diagnose ausführen** aus. Wenn die Diagnosetests abgeschlossen sind, klicken Sie auf **Ergebnisse kopieren**, um die Informationen in eine E-Mail einzufügen, die Sie an den Microsoft Support bzw. Ihre Endbenutzer an Ihren Helpdesk senden können. Wenn die Tests abgeschlossen sind, können Sie auch den Client zurücksetzen.

Weitere Informationen zur Option **Zurücksetzen**:

- Sie müssen kein lokaler Administrator sein, um diese Option zu verwenden, und diese Aktion wird nicht in der Ereignisanzeige protokolliert. 

- Außer wenn Dateien gesperrt sind, löscht diese Aktion alle Dateien im Ordner **%localappdata%\Microsoft\MSIPC**, in dem Clientzertifikate und Rights Management-Vorlagen gespeichert werden. Die Azure Information Protection-Richtlinie oder Clientprotokolldateien werden nicht gelöscht, und der Benutzer wird nicht abgemeldet.

- Der folgende Registrierungsschlüssel wird samt Einstellungen gelöscht: **HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC**. Wenn Sie Einstellungen für diesen Registrierungsschlüssel konfigurieren (z. B. Einstellungen für die Umleitung zu Ihrem Azure Information Protection-Mandanten, da Sie von AD RMS zu Azure Information Protection migrieren und noch einen Dienstverbindungspunkt in Ihrem Netzwerk haben), müssen Sie die Registrierungseinstellungen nach dem Zurücksetzen des Clients neu konfigurieren.

- Nachdem Sie den Client zurückgesetzt haben, müssen Sie die Benutzerumgebung erneut initialisieren. Hierdurch werden die Zertifikate für den Client sowie die neuesten Vorlagen heruntergeladen. Schließen Sie hierzu alle Instanzen von Office, und starten Sie eine Office-Anwendung neu. Diese Aktion prüft außerdem, ob Sie die neueste Azure Information Protection-Richtlinie heruntergeladen haben. Führen Sie die Diagnose erst erneut aus, nachdem Sie dies getan haben.


### <a name="client-status-section"></a>Abschnitt **Clientstatus**

Verwenden Sie den Wert **Verbunden als**, um zu bestätigen, dass der angezeigte Benutzername das Konto identifiziert, das für die Azure Information Protection-Authentifizierung verwendet werden soll. Der Benutzername muss zu einem für Office 365 oder Azure Active Directory verwendeten Konto passen, und dieses muss zu einem Mandanten gehören, der für Azure Information Protection konfiguriert ist.

Wenn Sie sich als ein anderer Benutzer anmelden müssen als der angezeigte Benutzer, finden Sie weitere Informationen im Abschnitt [Anmelden als ein anderer Benutzer](#sign-in-as-a-different-user) auf dieser Seite.

Die **letzte Verbindung** zeigt an, wann der Client zuletzt mit dem Azure Information Protection-Dienst verbunden war. Diese Informationen können zusammen mit dem Datum und der Uhrzeit unter **Information Protection-Richtlinie wurde installiert am** verwendet werden, um zu bestätigen, wann die Azure Information Protection-Richtlinie zuletzt installiert oder aktualisiert wurde. Wenn der Client eine Verbindung mit dem Dienst herstellt, lädt er automatisch die letzte Richtlinie herunter, sofern diese von der aktuellen Richtlinie abweicht. Die Richtlinie wird außerdem alle 24 Stunden heruntergeladen. Wenn Sie nach dem angezeigten Zeitpunkt Änderungen vorgenommen haben, schließen Sie die Office-Anwendung, und öffnen Sie sie erneut.

Wenn die Meldung **Dieser Client ist nicht für Office Professional Plus lizenziert** angezeigt wird, hat der Azure Information Protection-Client festgestellt, dass die installierte Office-Edition das Anwenden des Rights Management-Schutzes nicht unterstützt. In diesem Fall werden Bezeichnungen, die diesen Schutz anwenden, auf der Azure Information Protection-Leiste nicht angezeigt.

Verwenden Sie die Informationen unter **Version**, um zu bestätigen, welche Version des Clients installiert ist. Klicken Sie auf den Link **Neuigkeiten**, um den [Versionsveröffentlichungsverlauf](client-version-release-history.md) des Clients zu lesen und zu überprüfen, ob es sich um die neueste Version handelt und die entsprechenden Fixes und neuen Features installiert sind.

## <a name="custom-configurations"></a>Benutzerdefinierte Konfigurationen

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie möglicherweise für spezifische Szenarien oder eine Teilmenge der Benutzer benötigen. 

### <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als ein anderer Benutzer anmelden, wenn sie den Azure Information Protection-Client verwenden. Als Administrator ist dies jedoch möglicherweise erforderlich, wenn Sie über mehrere Mandanten verfügen. Dies gilt z.B., wenn Ihre Organisation zusätzlich zu einem Office 365- oder einem Azure-Mandanten auch einen Testmandanten verwendet.

Sie können mithilfe des Dialogfelds **Microsoft Azure Information Protection** überprüfen, mit welchem Konto Sie gerade angemeldet sind: Öffnen Sie dazu eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie – insbesondere bei Nutzung eines Administratorkontos – den angezeigten Domänennamen des angemeldeten Kontos. Beispiel: Wenn Sie ein Administratorkonto für zwei verschiedene Mandanten haben, kann leicht übersehen werden, dass Sie zwar mit dem richtigen Kontonamen, aber mit der falschen Domäne angemeldet sind. Ein Hinweis darauf können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige erwarteter Bezeichnungen oder unerwartete Verhaltensweisen sein.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie im Registrierungs-Editor zu **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**, und löschen Sie den **TokenCache**-Wert (und die zugehörigen Wertdaten).

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich von Windows abmelden und sich mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Registrierung bearbeitet haben. Der Azure Information Protection-Client wird automatisch mit Ihrem aktuell angemeldeten Benutzerkonto authentifiziert.

- Um die Umgebung für den Azure Rights Management-Dienst (auch bekannt als Bootstrapping) erneut zu initialisieren, verwenden Sie die Option **Zurücksetzen** im [RMS Analyzer Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Wenn Sie die aktuell heruntergeladene Azure Information Protection-Richtlinie löschen möchten, löschen Sie die Datei **Policy.msip** aus dem Ordner **%localappdata%\Microsoft\MSIP**.

### <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ausblenden der Menüoption „Klassifizieren und schützen“ im Windows-Dateiexplorer

Sie können diese erweiterte Konfiguration einrichten, indem Sie die Registrierung bearbeiten, wenn Sie den Azure Information Protection-Client in der Version 1.3.0.0 oder höher verwenden. 

Erstellen Sie den folgenden DWORD-Wert (mit beliebigen Wertdaten):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

### <a name="support-for-disconnected-computers"></a>Unterstützung für getrennte Computer

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen, um die neueste Azure Information Protection-Richtlinie herunterzuladen. Wenn Sie über einen Computer verfügen, von dem Sie wissen, dass er für einen bestimmten Zeitraum keine Verbindung mit dem Internet herstellen kann, können Sie den Client durch Bearbeiten der Registrierung am Verbindungsversuch mit dem Dienst hindern. 

Suchen Sie nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Stellen Sie sicher, dass der Client über eine gültige Richtliniendatei namens **Policy.msip** im Ordner **%localappdata%\Microsoft\MSIP** verfügt. Falls erforderlich, können Sie die Richtlinie aus dem Azure-Portal exportieren und die exportierte Datei auf den Clientcomputer kopieren. Sie können mithilfe dieser Methode auch eine veraltete Richtliniendatei durch die neueste veröffentlichte Richtlinie ersetzen.

## <a name="to-uninstall-the-azure-information-protection-client"></a>Deinstallieren des Azure Information Protection-Clients

Sie können jede beliebige Option verwenden:

- Deinstallieren Sie ein Programm über die Systemsteuerung: Klicken Sie auf **Microsoft Azure Information Protection** > **Deinstallieren**

- Führen Sie die ausführbare Datei (z. B. **AzInfoProtection.exe**) erneut aus, und klicken Sie auf der Seite **Setup ändern** auf **Deinstallieren**. 

- Führen Sie die ausführbare Datei mit **/uninstall** aus. Beispiel: `AzInfoProtection.exe /uninstall`

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection-Client installiert haben, helfen Ihnen die folgenden zusätzlichen Informationen möglicherweise bei der Unterstützung dieses Clients:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
