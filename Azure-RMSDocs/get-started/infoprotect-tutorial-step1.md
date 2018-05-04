---
title: Schnellstart-Tutorial Schritt 1 – AIP
description: Schritt 1 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Aktivieren des Schutzdiensts.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/22/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: 5dcc63f6ffbd7402c94258fe0d8677908c603e1f
ms.sourcegitcommit: 94d1c7c795e305444e9fde17ad73e46f242bcfa9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2018
---
# <a name="step-1-activate-protection"></a>Schritt 1: Aktivieren des Schutzes
 
>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

> [!NOTE]
>Schließen Sie diesen Schritt auch dann ab, wenn der Schutz für Ihren Mandanten bereits aktiviert ist, um den Aktivierungsstatus zu bestätigen. Die Anweisungen beinhalten das Anmelden beim Azure-Portal und das Erstellen eines Azure Information Protection-Blatts und sind für Schritt 2 erforderlich.

Wenn der Schutz für Azure Information Protection bereits aktiviert ist, können Sie die vertraulichen Dokumente und E-Mails Ihrer Organisation schützen. Außerdem können Sie verfolgen, wie diese geschützten Dokumente verwendet werden, wenn Sie sie für andere Benutzer freigeben. 

Es gibt verschiedene Möglichkeiten zur Aktivierung des Schutzes. Sie können sowohl PowerShell als auch die Administratorportale verwenden. Für dieses Tutorial wird jedoch das Azure-Portal genutzt, in dem auch Bezeichnungen für Benutzer konfiguriert werden. 

## <a name="to-activate-protection"></a>Aktivieren des Schutzes

1. Melden Sie sich mit dem globalen Administratorkonto für Ihren Mandanten im [Azure-Portal](https://portal.azure.com) an. 
    
    Wenn Sie nicht über globale Administratorrechte verfügen, können Sie die folgenden [administrativen Rollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) verwenden: **Information Protection-Administrator** oder **Sicherheitsadministrator**.

2. Klicken Sie im Hubmenü auf **Ressource erstellen**, und wählen Sie dann in der Liste **MARKETPLACE** die Option **Sicherheit + Identität** aus. 
    
3.  Wählen Sie auf dem Blatt **Sicherheit und Identität** in der Liste **AUSGEWÄHLTE APPS** die Option **Azure Information Protection** aus. Klicken Sie dann auf dem Blatt **Azure Information Protection** auf **Erstellen**.
    
    Dadurch wird das Blatt **Azure Information Protection** erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst im Hubmenü aus der Liste unter **Alle Dienste** auswählen. 
    
    > [!TIP] 
    > Wählen Sie **An das Dashboard anheften** zum Erstellen einer **Azure Information Protection**-Kachel auf Ihrem Dashboard aus, damit Sie bei der nächsten Anmeldung nicht erneut nach dem Dienst suchen müssen können.

4. Beachten Sie die Informationen auf der Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Sie können später zu dieser Seite zurückkehren. Klicken Sie für dieses Tutorial auf **VERWALTEN** > **Schutzaktivierung**. 

5. Dann sehen Sie, ob der Schutz für Ihren Mandanten aktiviert ist. 
    
    - Wenn der Schutz aktiviert ist, wird Ihnen die folgende Bestätigung angezeigt:
        
        ![Azure Information Protection-Status für Azure RMS](../media/info-protect-azurerms-activated.png)
        
    - Wenn der Schutz nicht aktiviert ist, werden Ihnen eine entsprechende Statusmeldung und die Option angezeigt, um ihn zu aktivieren:
        
        ![Azure Information Protection-Status für Azure RMS](../media/info-protect-azurerms-deactivated.png)

6. Wenn der Schutz noch nicht aktiviert ist, klicken Sie auf **Aktivieren**. 

    Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

Dies ist bereits alles im ersten Schritt dieses Tutorials. Sie können nun mit Schritt 2 beginnen.

|Weitere Informationen zu|Zusätzliche Informationen|
|--------------------------------|--------------------------|
|Informationen zum Aktivieren des Schutzes|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|


>[!div class="step-by-step"]
[&#171; Einführung in](infoprotect-quick-start-tutorial.md)
[Schritt 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
