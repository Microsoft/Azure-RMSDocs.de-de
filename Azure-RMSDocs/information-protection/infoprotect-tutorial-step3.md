---
title: "Schnellstart-Tutorial für Azure Information Protection Schritt 3 | Azure Rights Management"
description: "Schritt 3 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in nur 4 Schritten und weniger als 15 Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: 264f2be6c62dc7fa670171493941332fe7ff20e5
ms.openlocfilehash: 42649148e58a8ea1baab6317d181c24e6a21d709


---

# Schritt 3: Installieren des Azure Information Protection-Clients 

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

In diesem Schritt installieren Sie den Azure Information Protection-Client, damit die Richtlinie, die Sie gerade konfiguriert haben, auf einen Windows-PC heruntergeladen wird und die Bezeichnungen in Office-Anwendungen angezeigt werden. 

1. [Laden Sie den Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) aus dem Microsoft Download Center auf einen PC herunter, auf dem Office installiert aber Word gerade nicht geöffnet ist. 

2. Führen Sie **AZInfoProtection.exe** aus, und befolgen Sie die Aufforderungen, um den Client zu installieren.

    Für dieses Tutorial ist es unerheblich, ob Sie die Option zum Installieren einer Demorichtlinie auswählen, da die Richtlinie, die Sie gerade konfiguriert haben, aus Azure heruntergeladen wird und die Demorichtlinie ersetzt, falls diese installiert ist. Sie könnten die Option für die Demorichtlinie jedoch verwenden, wenn Sie nur die Standardbezeichnungen testen möchten, ohne eine Verbindung mit Azure Information Protection herzustellen. 

3. Stellen Sie sicher, dass der Client installiert wurde, indem Sie Word und ein neues leeres Dokument öffnen (speichern Sie es noch nicht). Wenn Sie aufgefordert werden, Ihren Benutzernamen und Ihr Kennwort einzugeben, geben Sie die Anmeldeinformationen Ihres globalen Administratorkontos ein. Wenn das Dokument geladen wird, sehen Sie zwei neue Dinge:

    - Auf der Registerkarte **Start** wird die neue Gruppe **Protection** (Schutz) mit einer Schaltfläche namens **Protect** (Schützen) angezeigt.

        Klicken Sie auf **Protect** > **Help and feedback**, und bestätigen Sie im Dialogfeld **Microsoft Azure Information Protection** Ihren Clientstatus. Es sollte **Information Protection policy is installed** (Die Information Protection-Richtlinie wurde installiert) und die letzte Verbindungszeit angezeigt werden. Stellen Sie sicher, dass der angezeigte Benutzername für Ihren Mandanten korrekt ist.

    - Unter dem Menüband wird eine neue Navigationsleiste angezeigt, die Information Protection-Navigationsleiste. Sie zeigt den **Sensitivity**-Titel (Vertraulichkeit) und die von Ihnen konfigurierte Standardbezeichnung **Internal** (Intern) an. 
    
        ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Client installiert](../media/word2013-callouts2.png)

Sie sind bereit für den letzten Schritt, in dem Sie die Klassifizierung, die Bezeichnung und den Schutz in Aktion zu sehen.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zum Installieren des Clients|[Installieren des Azure Information Protection-Clients](info-protect-client.md)|


>[!div class="step-by-step"]
[&#171; Schritt 2](infoprotect-tutorial-step2.md)
[Schritt 4 &#187;](infoprotect-tutorial-step4.md)


<!--HONumber=Aug16_HO2-->


