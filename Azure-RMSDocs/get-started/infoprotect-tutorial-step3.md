---
title: Schnellstarttutorial Schritt 3 | Azure Information Protection
description: "Schritt 3 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in ungefähr 30 Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: b5c87669c965d1e67b47dcfbd8ba97f1da41d104
ms.openlocfilehash: 042e168452d2b5cbc1eeec4fc06a3b0f137a5caf


---

# Schritt 3: Installieren von Client und Anwendung 

>*Gilt für: Azure Information Protection*

In diesem Schritt installieren Sie zunächst den Azure Information Protection-Client, damit die Richtlinie, die Sie gerade konfiguriert haben, auf einen Windows-PC heruntergeladen wird und die Bezeichnungen in Office-Anwendungen angezeigt werden.

Anschließend installieren Sie die Rights Management-Freigabeanwendung, damit Sie die Möglichkeit haben, ein Dokument per E-Mail sicher freizugeben und anschließend nachzuverfolgen, wie es verwendet wird. 

Diese beiden Installationen können in Office-Anwendungen integriert werden. Zum gegenwärtigen Zeitpunkt müssen sie separat installiert werden.


## Installieren des Azure Information Protection-Clients

1. [Laden Sie den Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) aus dem Microsoft Download Center auf einen PC herunter, auf dem Office installiert aber Word gerade nicht geöffnet ist. 

2. Führen Sie **AzInfoProtection.exe** aus, und befolgen Sie die Aufforderungen, um den Client zu installieren.

    Für dieses Tutorial ist es unerheblich, ob Sie die Option zum Installieren einer Demorichtlinie auswählen, da die Richtlinie, die Sie gerade konfiguriert haben, aus Azure heruntergeladen wird und die Demorichtlinie ersetzt, falls diese installiert ist. Sie könnten die Option für die Demorichtlinie jedoch verwenden, wenn Sie nur die Standardbezeichnungen testen möchten, ohne eine Verbindung mit Azure Information Protection herzustellen. 

## Installieren der Rights Management-Freigabeanwendung 

1. Navigieren Sie auf der Microsoft-Website zur Seite [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970) .

2. Klicken Sie im Abschnitt **Computer** auf das Symbol für **RMS-App für Windows** , und speichern Sie die Datei **Setup.exe** , um die Microsoft Rights Management-Freigabeanwendung zu installieren.

3. Klicken Sie auf der Seite **Microsoft RMS-Setup** auf **Weiter**, und warten Sie das Ende der Installation ab. Klicken Sie dann auf **Neu starten**, wenn Sie zum Neustart des Computers aufgefordert werden, oder auf **Schließen**, um die Installation abzuschließen.


## Überprüfen der Installationen

Stellen Sie sicher, dass diese Installationen erfolgreich durchgeführt wurden, indem Sie Word und ein neues leeres Dokument öffnen (speichern Sie es noch nicht). Wenn Sie aufgefordert werden, Ihren Benutzernamen und Ihr Kennwort einzugeben, geben Sie die Anmeldeinformationen Ihres globalen Administratorkontos ein. 

Wenn das Dokument geladen wird, sollten drei neue Elemente angezeigt werden:

- Auf der Registerkarte **Start** wird die neue Gruppe **Protection** (Schutz) mit einer Schaltfläche namens **Protect** (Schützen) angezeigt.

    Klicken Sie auf **Protect** > **Help and feedback**, und bestätigen Sie im Dialogfeld **Microsoft Azure Information Protection** Ihren Clientstatus. Es sollte **Information Protection policy is installed** (Die Information Protection-Richtlinie wurde installiert) und die letzte Verbindungszeit angezeigt werden. Stellen Sie sicher, dass der angezeigte Benutzername für Ihren Mandanten korrekt ist.

- Zudem wird auf der Registerkarte **Start** die neue Gruppe **RMS** mit einer Schaltfläche namens **Geschützt freigeben** angezeigt.

- Unter dem Menüband wird eine neue Navigationsleiste angezeigt – die Information Protection-Navigationsleiste. Sie zeigt den **Sensitivity**-Titel (Vertraulichkeit) und die von Ihnen konfigurierte Standardbezeichnung **Internal** (Intern) an. 
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Client installiert](../media/word2013-callouts2.png)

Sie können nun Azure Information Protection in Aktion sehen.

|Weitere Informationen zu|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zur Installation des Azure Information Protection-Clients|[Installieren des Azure Information Protection-Clients](../rms-client/info-protect-client.md)|
|Informationen zur Installation der Rights Management-Freigabeanwendung und Anweisungen für Benutzer|[Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md)|
|Skriptgesteuerte Installation der Rights Management-Freigabeanwendung für Windows und weiterführende technische Informationen|[Administratorhandbuch der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Schritt 2](infoprotect-tutorial-step2.md)
[Schritt 4 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Sep16_HO4-->


