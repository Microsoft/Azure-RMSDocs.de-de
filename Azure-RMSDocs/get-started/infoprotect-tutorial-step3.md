---
title: "Schnellstart-Tutorial Schritt 3 – AIP"
description: "Schritt 3 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Installieren des Clients"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
translationtype: Human Translation
ms.sourcegitcommit: 611b65589bdd8aa495fbfbd4a67c30a5fb9c387a
ms.openlocfilehash: 340cce9bec3eae7e507b5a33ebd380a38e9e7f19
ms.lasthandoff: 03/01/2017


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
