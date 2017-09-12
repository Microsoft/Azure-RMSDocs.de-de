---
title: "Reiner Schutzmodus für Azure Information Protection"
description: "Informationen für Benutzer, die den Azure Information Protection-Client im reinen Schutzmodus ausführen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 84644f717a6005245847c9e9598b87c5af885aa7
ms.sourcegitcommit: 6000258a9f973a3ab8e608eda57b88a469e7b754
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="protection-only-mode-for-the-azure-information-protection-client"></a>Reiner Schutzmodus für den Azure Information Protection-Client

Wenn der Azure Information Protection-Client keine Bezeichnungen aufweist, um Ihre Dokumente und E-Mails zu klassifizieren, wird er im **reinen Schutzmodus** ausgeführt. Wenn Sie in diesem Modus z.B. den Windows-Explorer verwenden und mit der rechten Maustaste auf **Klassifizieren und schützen** klicken, wird Folgendes angezeigt:

![Reiner Schutzmodus](../media/protection-only-mode.png)

Der reine Schutzmodus wird in den folgenden Szenarien ausgeführt:

- Ihre Organisation verfügt nicht über ein Abonnement für Azure Information Protection, das Features zum Klassifizieren und Schützen von Daten enthält, besitzt aber ein Abonnement für Office 365, das Datenschutz über den Azure Rights Management-Dienst umfasst. 
    
    - Sie können den Azure Information Protection-Client zum Schützen von Dateien und zum Anzeigen geschützter Dateien verwenden. Sie können Dokumente und E-Mails nicht klassifizieren oder mit Bezeichnungen versehen.

- Ihre Organisation besitzt ein Abonnement für Azure Information Protection, aber nur für einen Teil der Benutzer:
    
    - Bei einer solchen Kombination aus Abonnements liegt es in der Verantwortung des Administrators, sicherzustellen, dass nur diese Teilmenge der Benutzer die Klassifizierungs- und Bezeichnungsfeatures verwenden kann. Die anderen Benutzer sollten den Azure Information Protection-Client im reinen Schutzmodus ausführen. 

- Ihre Organisation verfügt über ein Abonnement von Azure Information Protection, aber Sie können die Azure Information Protection-Richtlinie nicht herunterladen. 
    
    - Dies kann aufgrund einer Fehlkonfiguration oder einer nicht erfolgreichen Anmeldung auftreten. Wenden Sie sich an den Helpdesk oder Ihren Administrator, aber in der Zwischenzeit können Sie möglicherweise mit dem Azure Information Protection-Client Dateien schützen und geschützte Dateien anzeigen.

## <a name="limitations-for-protection-only-mode"></a>Einschränkungen für den reinen Schutzmodus

- In Office-Apps wird die Azure Information Protection-Leiste nicht angezeigt. Wenn Sie auf **Schützen** > **Leiste anzeigen** klicken, ist diese Menüoption nicht verfügbar.

- Wenn Sie das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** mit dem Datei-Explorer verwenden, werden keine Bezeichnungen für die Klassifizierung angezeigt. Stattdessen wird eine Option zum Auswählen von RMS-Vorlagen angezeigt, wie in der vorherigen Abbildung veranschaulicht. 

## <a name="supported-tasks-for-protection-only-mode"></a>Unterstützte Aufgaben für den reinen Schutzmodus

- Dokumente und E-Mails mithilfe des Office Information Rights Management (IRM)-Features innerhalb von Office-Apps schützen (und den Schutz aufheben): Beispiel: Klicken Sie auf **Datei** > **Info** > **Dokument schützen** > **Zugriff einschränken**. Weitere Informationen finden Sie unter [Verwenden von Informationsschutz mit Office 365, Office 2016 oder Office 2013](../deploy-use/help-users.md).

- Dateien mithilfe des Windows-Datei-Explorer schützen (und den Schutz aufheben): Klicken Sie mit der rechten Maustaste auf die Datei, Dateien oder den Ordner, und wählen Sie dann **Klassifizieren und schützen** aus. Klicken Sie zum Anwenden von Schutz, der von Ihrem Administrator konfiguriert wurde, im Dialogfeld **Klassifizieren und schützen - Azure Information Protection** auf **Vorlage auswählen**, und wählen Sie dann eine der verfügbaren Vorlagen aus.

- Zeigen Sie geschützte Dateien mit dem Azure Information Protection-Viewer an.

- Greifen Sie über Ihre Office-Apps auf die Website zum Nachverfolgen von Dokumenten zu. Sie müssen jedoch über ein gültiges Abonnement zum Nachverfolgen und Widerrufen von Dokumenten für diese Website verfügen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]  
