---
title: Schnellstarttutorial Schritt 3 | Azure Information Protection
description: "Schritt 3 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in ungefähr 20 Minuten für Ihre Organisation testen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: ffed64826982756072456be18cced0226b6bb6cc
ms.openlocfilehash: 559136e48a709b91c544352c38a5bbb40d66261f


---

# <a name="step-3-install-the-client"></a>Schritt 3: installieren des Clients

>*Gilt für: Azure Information Protection*

In diesem Schritt installieren Sie den Azure Information Protection-Client, damit die Richtlinie, die Sie gerade konfiguriert haben, auf einen Windows-PC heruntergeladen wird und die Bezeichnungen in Office-Anwendungen angezeigt werden.


## <a name="install-the-azure-information-protection-client"></a>Installieren des Azure Information Protection-Clients

1. [Laden Sie den Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) aus dem Microsoft Download Center auf einen PC herunter, auf dem Office installiert aber Word gerade nicht geöffnet ist. 

2. Führen Sie **AzInfoProtection.exe** aus, und befolgen Sie die Aufforderungen, um den Client zu installieren.

    Für dieses Tutorial ist es unerheblich, ob Sie die Option zum Installieren einer Demorichtlinie auswählen, da die Richtlinie, die Sie gerade konfiguriert haben, aus Azure heruntergeladen wird und die Demorichtlinie ersetzt, falls diese installiert ist. Sie könnten die Option für die Demorichtlinie jedoch verwenden, wenn Sie nur die Standardbezeichnungen testen möchten, ohne eine Verbindung mit Azure Information Protection herzustellen. 

## <a name="verify-the-installations"></a>Überprüfen der Installationen

Stellen Sie sicher, dass die Installation erfolgreich durchgeführt wurde, indem Sie Word und ein neues leeres Dokument öffnen (speichern Sie es noch nicht). Wenn Sie aufgefordert werden, Ihren Benutzernamen und Ihr Kennwort einzugeben, geben Sie die Anmeldeinformationen Ihres globalen Administratorkontos ein. 

Wenn Sie den Client zum ersten Mal installiert haben, wird eine Seite mit **Glückwunsch** und grundlegenden Anweisungen angezeigt. Nachdem Sie sie gelesen haben, klicken Sie auf **schließen**.

Wenn das Dokument geladen wird, sehen Sie zwei neue Dinge:

- Auf der Registerkarte **Start** wird die neue Gruppe **Protection** (Schutz) mit einer Schaltfläche namens **Protect** (Schützen) angezeigt.

    Klicken Sie auf **Protect** > **Help and feedback**, und bestätigen Sie im Dialogfeld **Microsoft Azure Information Protection** Ihren Clientstatus. Es sollte **Connected as** (Verbunden als) und Ihren Benutzernamen anzeigen. Darüber hinaus sollten eine aktuelle Uhrzeit und das Datum der letzten Verbindung sowie der Installation der Information Protection-Richtlinie angezeigt werden. Stellen Sie sicher, dass der angezeigte Benutzername für Ihren Mandanten korrekt ist.

- Unter dem Menüband wird eine neue Navigationsleiste angezeigt – die Information Protection-Navigationsleiste. Sie zeigt den **Sensitivity**-Titel (Vertraulichkeit) und die von Ihnen konfigurierte Standardbezeichnung **Internal** (Intern) an. 
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Client installiert](../media/word2013-callouts2.png)

Sie können nun Azure Information Protection in Aktion sehen.

|Weitere Informationen zu|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zur Installation des Azure Information Protection-Clients|[Herunterladen und Installieren des Azure Information Protection-Clients](../rms-client/install-client-app.md)|
|Administratoranweisungen für den Azure Information Protection-Client|[Azure Information Protection-Client – Administratorhandbuch](../rms-client/client-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Schritt 2](infoprotect-tutorial-step2.md)
[Schritt 4 &#187;](infoprotect-tutorial-step4.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


