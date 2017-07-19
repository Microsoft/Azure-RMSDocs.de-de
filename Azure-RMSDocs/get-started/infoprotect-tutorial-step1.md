---
title: "Schnellstart-Tutorial Schritt 1 – AIP"
description: "Schritt 1 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Aktivieren des Rights Management-Diensts."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
ms.openlocfilehash: adc2baa875595d5044b47a9f014cc1381ba85dc2
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="step-1-activate-the-rights-management-service"></a>Schritt 1: Aktivieren des Rights Management-Diensts
 
>*Gilt für: Azure Information Protection*

> [!NOTE]
>Wenn Sie wissen, dass der Azure Rights Management-Dienst für Ihren Mandanten bereits aktiviert wurde, können Sie direkt mit dem [nächsten Schritt](infoprotect-tutorial-step2.md) fortfahren. 
>
>Wenn Sie nicht sicher sind, ob dieser Dienst aktiviert ist, verwenden Sie zur Überprüfung die Anweisungen in diesem Schritt.

Wenn der Azure Rights Management-Dienst aktiviert ist, können Sie die vertraulichen Dokumente und E-Mails Ihrer Organisation schützen und nachverfolgen, wie geschützte Dokumente verwendet werden, wenn Sie sie für andere Benutzer freigeben. Dieser Dienst kann auf verschiedene Weise aktiviert werden, z.B. mit Windows PowerShell oder über die Verwaltungsportale.

Für dieses Tutorial gehen wir direkt zur Aktivierungsseite im Verwaltungsportal für Office 365-Administratoren. Wenn Sie jedoch nicht direkt, sondern über Ihr Office 365-Verwaltungsportal zu dieser Seite navigieren möchten, finden Sie die entsprechenden vollständigen Anweisungen unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md). Diese vollständigen Anweisungen können Sie auch befolgen, wenn Sie Zugriff auf das Azure-Portal, jedoch nicht auf das Office 365-Verwaltungsportal haben.

## <a name="to-activate-the-rights-management-service"></a>So aktivieren Sie den Rights Management-Dienst

1. Öffnen Sie ein neues Browserfenster, und navigieren Sie direkt zur [Rights Management-Aktivierungsseite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rights Management** auf **Aktivieren**. Wenn diese Schaltfläche **Deaktivieren** anzeigt, ist der Dienst bereits aktiviert und Sie können direkt mit dem [nächsten Schritt](infoprotect-tutorial-step2.md) fortfahren. 

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 1 – Dienst aktivieren](../media/info-protect-activate.png)

3. Wenn Sie gefragt werden **Do you want to activate Rights Management?** (Möchten Sie die Rechteverwaltung aktivieren?), klicken Sie auf **Aktivieren**, um den Vorgang zu bestätigen.

    **Rechteverwaltung ist aktiviert** und die Option zum Deaktivieren sollte jetzt angezeigt werden (Sie müssen die Seite u. U. manuell aktualisieren).

    Klicken Sie zu diesem Zeitpunkt nicht auf **Erweiterte Funktionen**. Dadurch gelangen Sie zum klassischen Azure-Portal, wo Sie benutzerdefinierte Vorlagen konfigurieren können, die für dieses Tutorial jedoch nicht benötigt werden. Stattdessen können Sie diese Seite schließen.

Dies ist bereits alles im ersten Schritt dieses Tutorials. Für eine Produktionsbereitstellung sollten Sie benutzerdefinierte Vorlagen konfigurieren, zusätzlich zu den oder anstelle der beiden Standardvorlagen von Azure Rights Management. Da in diesem Tutorial aber keine benutzerdefinierten Vorlagen erforderlich sind, können Sie direkt zum zweiten Schritt übergehen.

|Weitere Informationen zu|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zum Aktivieren von Rights Management|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|
|Standardvorlagen und Erstellung neuer benutzerdefinierter Vorlagen|[Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md)|

>[!div class="step-by-step"]
[&#171; Einführung in](infoprotect-quick-start-tutorial.md)
[Schritt 2 &#187;](infoprotect-tutorial-step2.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
