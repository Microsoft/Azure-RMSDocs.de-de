---
title: Schnellstarttutorial Schritt 1 | Azure Information Protection
description: "Schritt 1 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in ungefähr 30 Minuten für Ihre Organisation testen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f6dbb143-96f7-4a9c-8208-be9280d69de9
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: edb98a61d247b51319a1eb172f9978e3d64d0e1b


---

# <a name="step-1-activate-the-rights-management-service"></a>Schritt 1: Aktivieren des Rights Management-Diensts
 
>*Gilt für: Azure Information Protection*

> [!NOTE]
>Wenn Sie den Azure Rights Management-Dienst für Ihren Mandanten bereits aktiviert haben, können Sie direkt zum [nächsten Schritt](infoprotect-tutorial-step2.md) wechseln. 

Wenn der Azure Rights Management-Dienst aktiviert ist, können Sie die vertraulichen Dokumente und E-Mails Ihrer Organisation schützen und nachverfolgen, wie diese verwendet werden, wenn Sie sie für andere Benutzer freigeben. Dieser Dienst kann auf verschiedene Weise aktiviert werden, z.B. mit Windows PowerShell oder über die Verwaltungsportale.

In diesem Tutorial wechseln wir direkt zur Aktivierungsseite für Office 365-Administratoren. Diese Seite ist im klassischen Office 365-Portal und im Office 365 Admin Center (Vorschau) identisch. 

Wenn Sie nicht direkt, sondern über Ihr Office 365-Verwaltungsportal zu dieser Seite navigieren möchten, finden Sie die entsprechenden vollständigen Anweisungen unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md). Diese vollständigen Anweisungen können Sie auch befolgen, wenn Sie Zugriff auf das Azure-Portal, jedoch nicht auf das Office 365-Verwaltungsportal haben.

## <a name="to-activate-the-rights-management-service"></a>So aktivieren Sie den Rights Management-Dienst

1. Öffnen Sie ein neues Browserfenster, und navigieren Sie direkt zur [Rights Management-Aktivierungsseite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rights Management** auf **Aktivieren**.

3. Wenn Sie gefragt werden **Möchten Sie die Rechteverwaltung aktivieren?**, klicken Sie auf **Aktivieren**.

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



<!--HONumber=Nov16_HO2-->

