---
title: "Rights Management-Freigabeanwendung – Administratorhandbuch | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/05/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d9992e30-f3d1-48d5-aedc-4e721f7d7c25
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: f7cf74355aa39928fd66a4be13a9b65428da7480
ms.openlocfilehash: 08226cd930f90bc7c9cda4c65315ee6472fbcf52


---


# Administratorhandbuch der Rights Management-Freigabeanwendung

*Gilt für: Active Directory Rights Management Services, Azure Rights Management, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1.*


Verwenden Sie die folgenden Informationen, wenn Sie für die Microsoft Rights Management-Freigabeanwendung in einem Unternehmensnetzwerk verantwortlich sind oder wenn Sie mehr technische Informationen benötigen, als im [Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md) oder in der [FAQ für die Microsoft Rights Management-Freigabeanwendung für Windows](http://go.microsoft.com/fwlink/?LinkId=303971) vorhanden sind:

Die RMS-Freigabeanwendung ist am besten für die Arbeit mit Azure RMS geeignet, da diese Bereitstellungskonfiguration das Senden geschützter Anhänge an Benutzer in einer anderen Organisation sowie Optionen, wie z. B. E-Mail-Benachrichtigungen und Dokumentenverfolgung mit Sperrung, unterstützt.  Sie funktioniert aber auch mit einigen Einschränkungen mit der lokalen Version AD RMS. Einen umfassenden Vergleich der Funktionen, die von Azure RMS und AD RMS unterstützt werden, finden Sie unter [Vergleich zwischen Azure Rights Management und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md). Wenn Sie AD RMS haben und zu Azure RMS migrieren möchten, finden Sie entsprechende Informationen unter [Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

Eine technische Übersicht über die Rights Management-Freigabeanwendung und Informationen zu nativem und generischem Schutz, den unterstützten Dateitypen, Dateierweiterungen und der Vorgehensweise zum Ändern der Standardschutzebene finden Sie unter [Technische Übersicht für die Microsoft Rights Management-Freigabeanwendung](sharing-app-admin-guide-technical.md). 

## Automatische Bereitstellung für die Microsoft Rights Management-Freigabeanwendung
Die Windows-Version des RMS-Freigabeanwendung unterstützt eine skriptbasierte Installation, sodass sie auch für Unternehmensbereitstellungen geeignet ist.

Die einzige Voraussetzung für Installationen besteht darin, dass der Computer mindestens Windows 7 Service Pack 1 ausführt und dass mindestens das Microsoft-Framework Version 4.0 installiert ist. Wenn Sie Microsoft .NET Framework 4.0 installieren müssen, können Sie [es zur Installation über das Microsoft Download Center herunterladen](http://www.microsoft.com/download/details.aspx?id=17718).

### So laden Sie die RMS-Freigabeanwendung für die automatische Bereitstellung herunter

1.  Klicken Sie auf der Seite [Microsoft Rights Management-Freigabeanwendung für Windows](http://www.microsoft.com/download/details.aspx?id=40857) im Microsoft Download Center auf **Herunterladen**.

2.  Wählen Sie die benötigten Dateien aus, und laden Sie sie herunter. Es sind zwei Client-Installationspakete verfügbar: eines für Windows 64 Bit (Microsoft Rights Management-Freigabeanwendung x64.zip) und eines für Windows 32 Bit (Microsoft Rights Management-Freigabeanwendung x86.zip).

3.  Extrahieren Sie die Dateien aus den komprimierten Installationspaketen, z. B. durch Doppelklick. Kopieren Sie dann die extrahierten Dateien an einen Speicherort im Netzwerk, auf den Clientcomputer zugreifen können.

Die Setuppakete für die RMS-Freigabeanwendung unterstützen verschiedene Bereitstellungsszenarien und enthalten Folgendes:

|Beschreibung|Bereitstellungsszenario|
|---------------|-----------------------|
|Microsoft Online-Anmelde-Assistent|Office 2010 und Azure RMS<br /><br />Office 2013 und Azure RMS, wenn Sie das [Update für Office 2013 vom 9. Juni 2015](https://support.microsoft.com/kb/3054853) (KB3054853) nicht installiert haben|
|Hotfix für Office (KB 2596501)|Office 2010 und Azure RMS<br /><br />Office 2010 und Active Directory RMS|
|Hotfix, damit der AD RMS-Client 1.0 zusammen mit Azure RMS funktioniert (KB 2843630)|Office 2010 und Azure RMS<br /><br />Office 2010 und Active Directory RMS|
|AD RMS-Client und die RMS-Freigabeanwendung|Office 2016 oder Office 2013 und Azure RMS oder Active Directory RMS<br /><br />Office 2010 und Azure RMS<br /><br />Office 2010 und Active Directory RMS<br /><br />Nur RMS-Freigabeanwendung und Office-Add-In|
|Office-Add-in für Menüband|Office 2016 oder Office 2013 und Azure RMS oder Active Directory RMS<br /><br />Office 2010 und Azure RMS<br /><br />Office 2010 und Active Directory RMS<br /><br />Nur RMS-Freigabeanwendung und Office-Add-In|
|Vorbereitungstool für Azure Active Directory Rights Management|Office 2010 und Azure RMS|
Verwenden Sie die folgenden Verfahren, um die Befehle, die zum Bereitstellen der RMS-Freigabeanwendung für diese Bereitstellungsszenarien erforderlich sind, zu identifizieren:

-   **Office 2016 oder Office 2013 und Azure RMS oder Active Directory RMS**

    Ihre Benutzer führen Office 2016 oder Office 2013 aus, Ihre Organisation verwendet Azure RMS oder Active Directory RMS, Benutzer arbeiten mit anderen Organisationen zusammen, die Azure RMS oder Active Directory RMS verwenden.

-   **Office 2010 und Azure RMS**

    Ihre Benutzer führen Office 2010 aus, Ihre Organisation verwendet Azure RMS, Benutzer arbeiten mit anderen Organisationen zusammen, die Azure RMS oder Active Directory RMS verwenden.

-   **Office 2010 und Active Directory RMS**

    Ihre Benutzer führen Office 2010 aus, Ihre Organisation verwendet AD RMS, Benutzer arbeiten mit anderen Organisationen zusammen, die Azure RMS verwenden.

-   **Nur RMS-Freigabeanwendung und Office-Add-In**

    Ihre Benutzer führen Office 2016, Office 2013 oder Office 2010 aus, Ihre Organisation verwendet AD RMS, Benutzer müssen nicht mit anderen Organisationen zusammenarbeiten, die Azure RMS verwenden. Mit dieser Installation können Sie nur die Freigabeanwendung und das Office-Add-In installieren.

> [!NOTE]
> Wenn Ihre Organisation in diesen Szenarien AD RMS verwendet, können die Benutzer geschützte Inhalte von anderen Organisationen, die Azure RMS verwenden, erhalten, aber die Benutzer können keine geschützten Inhalte an Benutzer in einer Organisation senden, die Azure RMS verwendet. Wenn Ihre Organisation aber Azure RMS ausführt, können die Benutzer geschützte Inhalte an andere bzw. von anderen Organisationen senden und empfangen.

Um die Installation für jedes Verfahren abzuschließen, muss der Computer neu gestartet werden. Sie können einen automatischen Neustart initiieren, indem Sie einen Befehl wie **shutdown /i** verwenden.

### So stellen Sie die RMS-Freigabeanwendung für Office 2016 oder Office 2013 und Azure RMS oder Active Directory RMS bereit

-   Führen Sie auf jedem Computer, auf dem Sie die RMS-Freigabeanwendung und zugehörige Komponenten installieren möchten, den folgenden Befehl mit erhöhten Rechten aus:

    ```
    setup.exe /s
    ```

Informationen zum Überprüfen des Erfolgs finden Sie in diesem Artikel im Abschnitt [Überprüfen der erfolgreichen Installation](#verifying-installation-success).

### So stellen Sie die RMS-Freigabeanwendung für Office 2010 und Azure RMS bereit

1.  Sie müssen der globale Administrator für Ihren Office 365- oder Azure Active Directory-Mandanten sein, damit Sie durch Ausführen des Vorbereitungstools für Azure Active Directory Rights Management die Zertifizierungsdienst-URL Ihrer Organisation abrufen können. Sie müssen dieses Tool nur ein Mal auf einem einzigen Computer ausführen. Sie verwenden die Zertifizierungsdienst-URL bei der Installation der RMS-Freigabeanwendung auf allen Computern:

    1.  Melden Sie sich an einem Computer mit einem lokalen Administratorkonto an.

    2.  Laden Sie auf diesem Computer [den Microsoft Online Services-Anmelde-Assistenten herunter, und installieren Sie ihn](http://www.microsoft.com/download/details.aspx?id=28177).

    3.  Führen Sie den folgenden Befehl aus, damit die Zertifizierungsdienst-URL, die Sie dann kopieren und für den nächsten Schritt speichern können, auf dem Bildschirm angezeigt wird:

        -   Für Windows 8.1 und Windows 8, 64-Bit:

            ```
            x64\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Für Windows 8.1 und Windows 8, 32-Bit:

            ```
            X86\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        -   Für Windows 7, 64 Bit:

            ```
            x64\win7\aadrmprep.exe /findCertificationUrl /logfile "<log file path and name>"
            ```

        > [!NOTE]
        > Dieser Befehl fordert Sie möglicherweise zur Eingabe Ihrer Anmeldeinformationen für Azure auf. Wenn der Computer nicht zu einer Domäne angehört, werden Sie aufgefordert. Wenn der Computer einer Domäne angehört, kann das Tool möglicherweise zwischengespeicherte Anmeldeinformationen verwenden.

2.  Führen Sie auf jedem Computer, auf dem Sie die RMS-Freigabeanwendung installieren werden, den folgenden Befehl einmal mit erhöhten Rechten aus:

    ```
    setup.exe /s /configureO2010Admin /certificationUrl <certification_url>
    ```

3.  Auf jedem Computer, auf dem Sie die RMS-Freigabeanwendung installieren werden, muss jeder Benutzer dieses Computers den folgenden Befehl ausführen (erhöhte Rechte werden nicht benötigt). Es gibt dazu verschiedene Möglichkeiten. Sie können Benutzer zum Ausführen des Befehls auffordern (z. B. durch einen Link in einer E-Mail-Nachricht oder im Helpdesk-Portal), oder Sie können ihn dem Anmeldeskript hinzufügen:

    ```
    bin\RMSSetup.exe /configureO2010Only
    ```

Informationen zum Überprüfen des Erfolgs finden Sie in diesem Artikel im Abschnitt [Überprüfen der erfolgreichen Installation](#verifying-installation-success).

### So stellen Sie die RMS-Freigabeanwendung für Office 2010 und Active Directory RMS bereit

1.  Führen Sie auf jedem Computer, auf dem Sie die RMS-Freigabeanwendung installieren werden, den folgenden Befehl mit erhöhten Rechten aus:

    ```
    setup.exe /s /configureO2010Admin
    ```

2.  Auf jedem Computer, auf dem Sie die RMS-Freigabeanwendung installieren werden, müssen Benutzer den folgenden Befehl (ohne erhöhte Rechten) ausführen. Es gibt dazu verschiedene Möglichkeiten. Sie können Benutzer zum Ausführen des Befehls auffordern (z. B. durch einen Link in einer E-Mail-Nachricht oder im Helpdesk-Portal), oder Sie können ihn dem Anmeldeskript hinzufügen:

    -   Für Windows 10, Windows 8.1 und Windows 8, 64-Bit:

        ```
        x64\aadrmprep.exe /configureO2010
        ```

    -   Für Windows 10, Windows 8.1 und Windows 8, 32-Bit:

        ```
        X86\aadrmprep.exe /configureO2010
        ```

    -   Für Windows 7, 64 Bit:

        ```
        x64\win7\aadrmpep.exe /configureO2010
        ```

Informationen zum Überprüfen des Erfolgs finden Sie in diesem Artikel im Abschnitt [Überprüfen der erfolgreichen Installation](#verifying-installation-success).

### So installieren Sie nur die RMS-Freigabeanwendung und das Office-Add-In

1.  Installieren Sie den AD RMS-Client und die RMS-Freigabeanwendung mithilfe des folgenden Befehls:

    -   Für 64-Bit-Windows:

        ```
        x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    -   Für 32-Bit-Windows:

        ```
        X86\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "<log file path and name>"
        ```

    Beispiel: `\\server5\apps\rms\x64\setup_ipviewer.exe /norestart /quiet /msicl "MSIRESTARTMANAGERCONTROL=Disable" /log "C:\Log files\ipviewerinstall.log"`

2.  Installieren Sie das Office-Add-in mit den folgenden Befehlen:

    -   Für 64-Bit-Version von Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "<log file path and name>"
        ```

    -   Für 32-Bit-Version von Office:

        ```
        msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x86\Setup.msi" /L*v "<log file path and name>"
        ```

    Beispiel: `\\server5\apps\rms\msiexec.exe /norestart /quiet MSIRESTARTMANAGERCONTROL=Disable /i "x64\Setup64.msi" /L*v "C:\Log files\rmsofficeinstall.log"`

Informationen zum Überprüfen des Erfolgs finden Sie in diesem Artikel im Abschnitt [Überprüfen der erfolgreichen Installation](#verifying-installation-success).

## Überprüfen der erfolgreichen Installation
Sie können die Installationsprotokolldateien zum Überprüfen der erfolgreichen Installation verwenden.

### So überprüfen Sie die erfolgreiche Installation der RMS-Freigabeanwendung für Office 2016 oder Office 2013 und Azure RMS oder Active Directory RMS

-   Um den Erfolg des Befehls „Setup.exe“ zu überprüfen, suchen Sie auf jedem Computer nach der Installationsprotokolldatei **RMInstaller.log** im Ordner *%temp%\RMS_installer_&lt;guid&gt;*, und identifizieren Sie anschließend den Exitcode.

    Eine erfolgreiche Installation hat einen Exitcode von 0. Jede andere Zahl weist auf eine fehlerhafte Installation hin.

    Beispiel eines Protokolldateinamens: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0\RMInstaller.log**

### So überprüfen Sie die erfolgreiche Installation der RMS-Freigabeanwendung für Office 2010 und Azure RMS

1.  Um den Erfolg des Befehls „Setup.exe“ zu überprüfen, suchen Sie auf jedem Computer nach der Installationsprotokolldatei **RMInstaller.log** im Ordner *%temp%\RMS_installer_&lt;guid&gt;*, und identifizieren Sie anschließend den Exitcode.

    Eine erfolgreiche Installation hat einen Exitcode von 0. Jede andere Zahl weist auf eine fehlerhafte Installation hin.

    Beispiel eines Protokolldateinamens: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Um den Erfolg des Befehls "RMSSetup.exe" zu überprüfen, muss der Benutzer die folgenden Dateien im Ordner *%localappdata%\microsoft\drm* erstellen:

    -   CERT-Machine-2048.drm

    -   CERT-Machine.drm

    -   CLC-&#42;.drm

    -   GIC-&#42;.drm

    Beispiel einer CLC-&#42;.drm-Datei:

    **CLC-alice@isvtenant999.onmicrosoft.com-{1b9cfccf;k5b11;k4a10;kac15;k29b2b6980f4c}.drm**

### So überprüfen Sie die erfolgreiche Installation der RMS-Freigabeanwendung für Office 2010 und Active Directory RMS

1.  Um den Erfolg des Befehls „Setup.exe“ zu überprüfen, suchen Sie auf jedem Computer die Installationsprotokolldatei im Ordner *%temp%\RMS_installer_&lt;guid&gt;*, und identifizieren Sie anschließend den Exitcode.

    Eine erfolgreiche Installation hat einen Exitcode von 0. Jede andere Zahl weist auf eine fehlerhafte Installation hin.

    Beispiel eines Protokolldateinamens: **C:\temp\RMS_Installer_9352fc91-1982-43bf-958a-2ef1fe9c2ed0**

2.  Um den Erfolg des Befehls „aadrmprep.exe“ auf den einzelnen Computern zu überprüfen, suchen Sie den folgenden Text in der Installationsprotokolldatei: **aadrmprep.exe exited with status SUCCESS**.

    > [!NOTE]
    > In manchen Fällen kann diese Installation zweimal ausgeführt werden. Die erste Ausführung ist fehlerhaft, die zweite ist erfolgreich.

    Wenn Sie die Registrierungsänderungen, die dieses Tool vornimmt, manuell überprüfen möchten, finden Sie diese im Folgenden:

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\Federation]

        "FederationStartRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\Federation]

        "FederationStartRealm"="urn:HostedRmsOnlineService:Certification"

    -   [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation]

        @="&lt;certification url&gt;"

    -   [HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\14.0\Common\DRM]

        DefaultUser="&lt;default_user&gt;"

### So überprüfen Sie die erfolgreiche Installation der RMS-Freigabeanwendung nur für das Office-Add-In

1.  Um den Erfolg des Befehls "Setup_ipviewer.exe" zu überprüfen, suchen Sie den folgenden Text in der Installationsprotokolldatei: **Installation success or error status: 0**

    Beispiel für Zeilen aus einer erfolgreichen Installation:

    **MSI (s) (F0:B8) [14:19:57:854]: Product: Active Directory Rights Management Services Client 2.1 -- Installation completed successfully.**

    **MSI (s) (F0:B8) [14:19:57:854]: Windows Installer installed the product. Product Name: Active Directory Rights Management Services Client 2.1. Product Version: 1.0.1179.1. Product Language: 1033. Hersteller: Microsoft Corporation. Installation success oder in der erroder in der status: 0.**

2.  Um den Erfolg des Office-Add-ins zu überprüfen, suchen Sie auf jedem Computer den folgenden Text in der Installationsprotokolldatei: **Installation success or error status: 0**

    Beispiel für Zeilen aus einer erfolgreichen Installation:

    **MSI (s) (9C:88) [18:49:04:007]: Product: Microsoft RMS Office Addins -- Installation completed successfully.**

    **MSI (s) (9C:88) [18:49:04:007]: Windows Installer installed the product. Product Name: Microsoft RMS Office Addins. Product Version: 1.0.7. Product Language: 1033. Hersteller: Microsoft. Installation success oder in der erroder in der status: 0.**

## Deinstallationsbefehle
Nicht alle Installationsbefehle, die für diese Bereitstellungen erforderlich sind, unterstützen einen Deinstallationsbefehl. Sie können den AD RMS-Client, die Freigabeanwendung und das Office-Add-in deinstallieren. Verwenden Sie die folgenden Befehle, um diese Elemente zu deinstallieren.

### So deinstallieren Sie den AD RMS-Client und die RMS-Freigabeanwendung

-   Verwenden Sie die folgenden Befehle:

    -   Für 64-Bit-Windows:

        ```
        x64\setup_ipviewer.exe /uninstall /quiet
        ```

    -   Für 32-Bit-Windows:

        ```
        x86\setup_ipviewer.exe /uninstall /quiet
        ```

### So deinstallieren Sie das Office-Add-in

-   Verwenden Sie die folgenden Befehle:

    -   Für 64-Bit-Version von Office:

        ```
        msiexec /x \x64\Setup[64].msi /quiet
        ```

    -   Für die 32-Bit-Version von Office:

        ```
        msiexec /x \x86\Setup.msi /quiet
        ```

## Unterdrücken automatischer Updates
Standardmäßig werden Benutzer benachrichtigt, wenn es eine neuere Version der RMS-Freigabeanwendung gibt, und dazu aufgefordert, sie herunterzuladen. Sie können diese Benachrichtigung unterdrücken, indem Sie den folgenden Registrierungsschlüssel bearbeiten:

1.  Navigieren Sie zu **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC**, und erstellen Sie, sofern nicht bereits vorhanden, einen neuen Schlüssel mit dem Namen **RmsSharingApp**.

2.  Wählen Sie **RmsSharingApp**aus, erstellen Sie einen neuen DWORD-Wert mit **AllowUpdatePrompt**, und legen Sie den Wert auf **0**fest.

Da die RMS-Freigabeanwendung nicht von WSUS unterstützt wird, können Sie das folgende Verfahren verwenden, um neue Versionen der RMS-Freigabeanwendung vor der Bereitstellung für alle Benutzer zu testen:

1.  Führen Sie auf allen Benutzercomputern ein Skript aus, um automatische Updates zu unterdrücken. Führen Sie dieses Skript auf den Computern, die Administratoren verwenden, um neue Versionen zu testen, nicht aus.

2.  Wenn eine neue Version verfügbar ist, können Administratoren sie herunterladen und testen.

3.  Wenn die Tests abgeschlossen sind und alle Probleme gelöst wurden, können Sie die neueste Version allen Benutzern mithilfe der Anweisungen zur automatischen Bereitstellung in diesem Handbuch bereitstellen.

## Nur Azure RMS: Konfigurieren der Dokumentenverfolgung
Wenn Sie ein [Abonnement haben, das die Dokumentenverfolgung unterstützt](https://technet.microsoft.com/dn858608), ist die Website für die Dokumentnachverfolgung standardmäßig für alle Benutzer in Ihrer Organisation aktiviert.  Die Dokumentenverfolgung zeigt Informationen, wie z. B. E-Mail-Adressen der Personen, die auf geschützte Dokumente zugegriffen haben, die von Benutzern freigegeben wurden, wann diese Benutzer versucht haben, darauf zuzugreifen, sowie deren Standort. Wenn das Anzeigen dieser Informationen in Ihrer Organisation aufgrund von Datenschutzanforderungen nicht zulässig ist, können Sie den Zugriff auf die Website der Dokumentenverfolgung mithilfe des Cmdlets [Disable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623032) deaktivieren. Sie können den Zugriff auf die Website jederzeit mit dem Cmdlet [Enable-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) wieder aktivieren und mit [Get-AadrmDocumentTrackingFeature](http://go.microsoft.com/fwlink/?LinkId=623037) überprüfen, ob der Zugriff derzeit aktiviert oder deaktiviert ist.

Zum Ausführen dieser Cmdlets benötigen Sie mindestens Version **2.3.0.0** des Azure RMS-Moduls für Windows PowerShell.  Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

> [!TIP]
> Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm –ListAvailable).Version`

Die folgenden URLs werden für die Dokumentenverfolgung verwendet und müssen zulässig sein (z. B. durch Hinzufügen zu Ihren vertrauenswürdigen Websites, wenn Sie Internet Explorer mit erhöhter Sicherheit verwenden):

-   https://&#42;.azurerms.com

-   https://ecn.dev.virtualearth.net

    > [!NOTE]
    > Dieser URL ist für Bing-Karten.

-   https://&#42;.microsoftonline.com

-   https://&#42;.microsoftonline-p.com

### Nachverfolgen und Sperren von Dokumenten für Benutzer

Wenn sich Benutzer auf der Nachverfolgungswebsite anmelden, können sie Dokumente nachverfolgen und sperren, die sie mithilfe der RMS-Freigabeanwendung geteilt haben. Wenn Sie sich als Administrator bei Azure RMS anmelden (globaler Administrator), können Sie auf das Admin-Symbol in der oberen rechten Ecke der Seite klicken, mit dem Sie in den Administratormodus wechseln. So können Sie die Dokumente anzeigen, die von den Benutzern in Ihrer Organisation freigegeben wurden.

Aktionen, die Sie im Administratormodus durchführen, werden geprüft und in Verwendungsprotokolldateien protokolliert, und Sie müssen Ihre Einwilligung geben, um den Vorgang fortzusetzen. Weitere Informationen über diese Protokollierung finden Sie im nächsten Abschnitt.

Wenn Sie sich im Administratormodus befinden, können Sie nach Benutzern oder Dokumenten suchen. Wenn Sie nach Benutzern suchen, werden Ihnen alle Dokumente angezeigt, die dem angegebenen Benutzer freigegeben wurden. Wenn Sie nach Dokumenten suchen, sehen alle Benutzer in Ihrer Organisation, die das Dokument freigegeben haben. Sie können die Suchergebnisse näher betrachten, um Dokumente zu überwachen, die Benutzer freigegeben haben, und diese Dokumente, falls erforderlich, wieder zu sperren. 

Klicken Sie auf das **X** neben **Administratormodus beenden**, um den Administratormodus zu verlassen.

Eine Anleitung zur Verwendung der Website zur Dokumentnachverfolgung finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](sharing-app-track-revoke.md) im Benutzerhandbuch.



### Verwendungsprotokollierung für die Website zur Dokumentnachverfolgung

Für die Dokumentnachverfolgung kommen zwei Felder in den Verwendungsprotokolldateien infrage: **AdminAction** und **ActingAsUser**.

**AdminAction** – Dieses Feld weist den Wert TRUE auf, wenn ein Administrator die Website zur Dokumentnachverfolgung im Administratormodus verwendet, z.B. um ein Dokument im Auftrag des Benutzers zu sperren oder um festzustellen, wann es freigegeben wurde. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer.

**ActingAsUser** – Wenn das Feld „AdminAction“ TRUE aufweist, enthält dieses Feld den Benutzernamen, in dessen Auftrag der Administrator als der gesuchte Benutzer oder Besitzer des Dokuments handelt. Wenn sich ein Benutzer auf der Website zur Dokumentnachverfolgung anmeldet, ist dieses Feld leer. 

Einige der Anforderungstypen protokollieren die Verwendungsweise der Website zur Dokumentnachverfolgung vonseiten der Benutzer und Administratoren. **RevokeAccess** ist beispielsweise der verwendete Anforderungstyp, wenn ein Benutzer oder Administrator im Auftrag eines Benutzers ein Dokument auf der Website zur Dokumentnachverfolgung gesperrt hat. Verwenden Sie diesen Anforderungstyp in Kombination mit dem AdminAction-Feld, um zu ermitteln, ob ein Benutzer sein eigenes Dokument gesperrt hat (AdminAction ist leer) oder ob der Administrator dies im Namen eines Benutzers getan hat (AdminAction ist TRUE).


Weitere Informationen zur Verwendungsprotokollierung finden Sie unter [Protokollieren und Analysieren der Nutzung von Azure Rights Management](../deploy-use/log-analyze-usage.md).

## Nur AD RMS: Unterstützung für mehrere E-Mail-Domänen innerhalb Ihrer Organisation
Wenn Sie AD RMS verwenden und Benutzer in Ihrer Organisation mehrere E-Mail-Domänen haben, möglicherweise aufgrund einer Fusion oder Übernahme, müssen Sie den folgenden Registrierungsschlüssel bearbeiten:

1.  Navigieren Sie zu **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC**, und erstellen Sie, sofern nicht bereits vorhanden, einen neuen Schlüssel mit dem Namen **RmsSharingApp**.

2.  Wählen Sie **RmsSharingApp** aus, erstellen Sie einen neuen mehrteiligen Zeichenfolgenwert namens **FederatedDomains**, und fügen Sie die Domänen und alle Unterdomänen hinzu, die Ihre Organisation verwendet. Platzhalter werden nicht unterstützt.

    Beispiel: Das Unternehmen Coho Vineyard &amp; Winery verfügt über die Standard-E-Mail-Domäne **cohovineyardandwinery.com**, aber durch Fusionen verwendet es auch die E-Mail-Domänen **cohowinery.com**, **eastcoast.cohowinery.com** und **cohovineyard**. Für den **FederatedDomains**-Wert gibt der Administrator **cohowinery.com; eastcoast.cohowinery.com; cohovineyard** ein.

Wenn Sie diese Registrierungsänderung nicht vornehmen, können Benutzer möglicherweise keine Inhalte nutzen, die von anderen Benutzern in ihrer Organisation geschützt wurden. Diese Bearbeitung der Registrierung ist nicht erforderlich, wenn Sie Azure RMS verwenden.


## Nächste Schritte
Weitere technische Informationen einschließlich einer Erläuterung des Unterschieds zwischen den Schutzebenen (systemeigene und generische), der unterstützten Dateitypen und Dateinameerweiterungen und einer Anleitung zum Ändern der Standardschutzebene finden Sie unter [Technische Übersicht für die Rights Management-Freigabeanwendung](sharing-app-admin-guide-technical.md).




<!--HONumber=Aug16_HO1-->


