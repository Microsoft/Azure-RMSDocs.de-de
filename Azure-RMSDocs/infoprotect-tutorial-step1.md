---
title: Schnellstart-Tutorial Schritt 1 – AIP
description: Schritt 1 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Aktivieren des Schutzdiensts.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/28/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: af3958d7c3bafc37772944e2cb39a9b3244eccc2
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49169973"
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

2. Wählen Sie im Hubmenü die Option **Ressource erstellen** aus, und geben Sie dann im Suchfeld für den Marketplace **Azure Information Protection** ein. 
    
3. Wählen Sie aus den Ergebnisliste **Azure Information Protection** aus. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Erstellen**.
    
    > [!TIP] 
    > Wählen Sie optional **An Dashboard anheften** aus, um eine **Azure Information Protection**-Kachel auf Ihrem Dashboard zu erstellen, damit Sie bei der nächsten Anmeldung beim Portal nicht erneut nach dem Dienst suchen müssen können.
    
    Klicken Sie erneut auf **Erstellen**.

4. Beachten Sie die Informationen auf der Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Sie können später zu dieser Seite zurückkehren. Klicken Sie für dieses Tutorial auf **Verwalten** > **Schutzaktivierung**. 

5. Dann sehen Sie, ob der Schutz für Ihren Mandanten aktiviert ist. 
    
    - Wenn der Schutz aktiviert ist, wird Ihnen die folgende Bestätigung angezeigt:
        
        ![Azure Information Protection-Status für Azure RMS](./media/info-protect-azurerms-activated.png)
        
    - Wenn der Schutz nicht aktiviert ist, werden Ihnen eine entsprechende Statusmeldung und die Option angezeigt, um ihn zu aktivieren:
        
        ![Azure Information Protection-Status für Azure RMS](./media/info-protect-azurerms-deactivated.png)

6. Wenn der Schutz noch nicht aktiviert ist, klicken Sie auf **Aktivieren**. 

    Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

Dies ist bereits alles im ersten Schritt dieses Tutorials. Sie können nun mit Schritt 2 beginnen.

|Weitere Informationen zu|Zusätzliche Informationen|
|--------------------------------|--------------------------|
|Informationen zum Aktivieren des Schutzes|[Aktivieren von Azure Rights Management](activate-service.md)|


>[!div class="step-by-step"]
[&#171; Einführung in](infoprotect-quick-start-tutorial.md)
[Schritt 2 &#187;](infoprotect-tutorial-step2.md)

