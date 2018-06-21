---
title: Schnellstart-Tutorial Schritt 3 – AIP
description: Schritt 3 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Installieren des Clients
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 209815b9-81c9-430c-a82f-32cac991449b
ms.openlocfilehash: 363902fac8036b118ce28c3ea87c812e262c3d47
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
ms.locfileid: "30206076"
---
# <a name="step-3-install-the-client"></a>Schritt 3: installieren des Clients

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

In diesem Schritt installieren Sie den Azure Information Protection-Client, damit die Richtlinie, die Sie gerade konfiguriert haben, auf einen Windows-PC heruntergeladen wird und die Bezeichnungen in Office-Anwendungen angezeigt werden.


## <a name="install-the-azure-information-protection-client"></a>Installieren des Azure Information Protection-Clients

1. Laden Sie aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) **AzInfoProtection.exe** auf einen PC herunter, auf dem Office installiert aber Word gerade nicht geöffnet ist.
    
2. Führen Sie die ausführbaren Dateien aus, die Sie gerade heruntergeladen haben, und folgen Sie den Aufforderungen zur Installation des Clients.
    
    Für dieses Tutorial ist es unerheblich, ob Sie die Option zum Installieren einer Demorichtlinie auswählen, da die Richtlinie, die Sie gerade konfiguriert haben, aus Azure heruntergeladen wird und die Demorichtlinie ersetzt, falls diese installiert ist. Sie könnten die Option für die Demorichtlinie jedoch verwenden, wenn Sie nur die Standardbezeichnungen testen möchten, ohne eine Verbindung mit Azure Information Protection herzustellen. 

## <a name="verify-the-installation"></a>Überprüfen Sie die Installation

Stellen Sie sicher, dass die Installation erfolgreich durchgeführt wurde, indem Sie Word und ein neues leeres Dokument öffnen (speichern Sie es noch nicht). Wenn Sie aufgefordert werden, Ihren Benutzernamen und Ihr Kennwort einzugeben, geben Sie die Anmeldeinformationen Ihres globalen Administratorkontos ein. 

Wenn Sie den Client zum ersten Mal installiert haben, wird eine Seite mit **Glückwunsch** und grundlegenden Anweisungen angezeigt. Nachdem Sie sie gelesen haben, klicken Sie auf **schließen**.

Wenn das Dokument geladen wird, sehen Sie zwei neue Dinge:

![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Client installiert](../media/word2016-calloutsv2.png)

- Auf der Registerkarte **Start** wird die neue Gruppe **Protection** (Schutz) mit der Schaltfläche **Protect** (Schützen) angezeigt.
    
    Klicken Sie auf **Schützen** > **Hilfe und Feedback**, und bestätigen Sie im Dialogfeld **Microsoft Azure Information Protection** Ihren Clientstatus. Es sollte **Connected as** (Verbunden als) und Ihren Benutzernamen anzeigen. Darüber hinaus sollten eine aktuelle Uhrzeit und das Datum der letzten Verbindung sowie der Installation der Information Protection-Richtlinie angezeigt werden. Stellen Sie sicher, dass der angezeigte Benutzername für Ihren Mandanten korrekt ist.

- Unter dem Menüband wird eine neue Navigationsleiste angezeigt – die Information Protection-Navigationsleiste. Diese zeigt **Empfindlichkeit** an sowie die Bezeichnungen, die wir aus dem Azure-Portal kennen. 

Sie können nun Azure Information Protection in Aktion sehen.

|Weitere Informationen zu|Zusätzliche Informationen|
|--------------------------------|--------------------------|
|Informationen zur Installation des Azure Information Protection-Clients|[Herunterladen und Installieren des Azure Information Protection-Clients](../rms-client/install-client-app.md)|
|Administratoranweisungen für den Azure Information Protection-Client|[Azure Information Protection-Client – Administratorhandbuch](../rms-client/client-admin-guide.md)|


>[!div class="step-by-step"]
[&#171; Schritt 2](infoprotect-tutorial-step2.md)
[Schritt 4 &#187;](infoprotect-tutorial-step4.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]