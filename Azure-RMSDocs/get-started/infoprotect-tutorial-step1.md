---
title: "Schnellstart-Tutorial Schritt 1 – AIP"
description: "Schritt 1 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Aktivieren des Rights Management-Diensts."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: e80d47d1a477c03296b9a2e0eb4373929cfaa66b
ms.sourcegitcommit: 94a9b6714c555b95f6064088e77ed94f08224a15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2017
---
# <a name="step-1-activate-the-rights-management-service"></a>Schritt 1: Aktivieren des Rights Management-Diensts
 
>*Gilt für: Azure Information Protection*

> [!NOTE]
>Schließen Sie diesen Schritt auch dann ab, wenn Sie den Azure Rights Management-Dienst für Ihren Mandanten bereits abgeschlossen haben, um den Aktivierungsstatus zu bestätigen. Die Anweisungen beinhalten das Anmelden beim Azure-Portal und das Erstellen eines Azure Information Protection-Blatts, sodass Sie für Schritt 2 bereit sind. 

Wenn der Azure Rights Management-Dienst aktiviert ist, können Sie die vertraulichen Dokumente und E-Mails Ihrer Organisation schützen und nachverfolgen, wie geschützte Dokumente verwendet werden, wenn Sie sie für andere Benutzer freigeben. Dieser Dienst kann auf verschiedene Weise aktiviert werden, z.B. mit Windows PowerShell oder über die Verwaltungsportale.

Für dieses Tutorial verwenden wir das Azure-Portal, dort werden auch die Bezeichnungen für Benutzer konfiguriert. 

## <a name="to-activate-the-azure-rights-management-service"></a>Aktivieren des Azure Rights Management-Diensts

1. Melden Sie sich als globaler Administrator oder Sicherheitsadministrator für Ihren Mandanten beim [Azure-Portal](https://portal.azure.com) an.

2. Klicken Sie im Hubmenü auf **Neu**, und wählen Sie dann in der Liste **MARKETPLACE** die Option **Sicherheit und Identität** aus. 
    
3.  Wählen Sie auf dem Blatt **Sicherheit und Identität** in der Liste **AUSGEWÄHLTE APPS** die Option **Azure Information Protection** aus. Klicken Sie dann auf dem Blatt **Azure Information Protection** auf **Erstellen**.
    
    Dadurch wird das Blatt **Azure Information Protection** erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst im Hubmenü aus der Liste unter **Weitere Dienste** auswählen. 
    
    > [!TIP] 
    > Wählen Sie **An das Dashboard anheften** zum Erstellen einer **Azure Information Protection**-Kachel auf Ihrem Dashboard aus, damit Sie bei der nächsten Anmeldung nicht erneut nach dem Dienst suchen müssen können.

4. Beachten Sie die Informationen auf der Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Sie können später zu dieser Seite zurückkehren. Wählen Sie für dieses Tutorial **RMS-Einstellungen** oder **Protection activation** (Aktivierung des Schutzes) aus. Diese Option wird zurzeit umbenannt. 

5. Ihnen wird angezeigt, ob der Azure Rights Management-Dienst für Ihren Mandanten aktiviert ist. 
    
    - Wenn der Dienst aktiviert ist, wird Ihnen die folgende Bestätigung angezeigt:
        
        ![Azure Information Protection-Status für Azure RMS](../media/info-protect-azurerms-activated.png)
        
    - Wenn der Dienst nicht aktiviert ist, wird Ihnen eine entsprechende Statusmeldung angezeigt und die Option, um ihn zu aktivieren. Beispiel:
        
        ![Azure Information Protection-Status für Azure RMS](../media/info-protect-azurerms-deactivated.png)

6. Wenn der Dienst nicht aktiviert ist, klicken Sie auf **Aktivieren**. 

    Wenn die Aktivierung abgeschlossen ist, zeigt die Informationsleiste **Activation finished successfully** (Aktivierung erfolgreich) an.

Dies ist bereits alles im ersten Schritt dieses Tutorials. Sie können nun mit Schritt 2 beginnen.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zum Aktivieren von Rights Management|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|


>[!div class="step-by-step"]
[&#171; Einführung in](infoprotect-quick-start-tutorial.md)
[Schritt 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
