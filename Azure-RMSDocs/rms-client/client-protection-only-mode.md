---
title: Reiner Schutzmodus für Azure Information Protection
description: Informationen für Benutzer, die den Azure Information Protection-Client im reinen Schutzmodus ausführen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 1/13/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 16042717-0d7a-41f5-87e3-12826fda35df
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 9701cba6481271f1ac88beffd0f01a9c0e789485
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97385810"
---
# <a name="user-guide-protection-only-mode-for-the-azure-information-protection-client"></a>Benutzerhandbuch: Reiner Schutzmodus für den Azure Information Protection-Client

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [Azure Information Protection klassischer Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn der Azure Information Protection-Client keine Bezeichnungen aufweist, um Ihre Dokumente und E-Mails zu klassifizieren, wird er im **reinen Schutzmodus** ausgeführt. Wenn Sie in diesem Modus z.B. den Windows-Explorer verwenden und mit der rechten Maustaste auf **Klassifizieren und schützen** klicken, wird Folgendes angezeigt:

![Reiner Schutzmodus](../media/protection-only-mode.png)

Der reine Schutzmodus wird in den folgenden Szenarien ausgeführt:

- Ihre Organisation verfügt nicht über ein Abonnement für Azure Information Protection, das Klassifizierungs-und Beschriftungs Features umfasst, aber über ein Abonnement für Microsoft 365 verfügt, das den Schutz von Daten mithilfe des Azure-Rights Management Dienstanbieter umfasst. 
    
    - Sie können den Azure Information Protection-Client zum Schützen von Dateien und zum Anzeigen geschützter Dateien verwenden. Sie können Dokumente und E-Mails nicht klassifizieren oder mit Bezeichnungen versehen.

- Ihre Organisation besitzt ein Abonnement für Azure Information Protection, aber nur für einen Teil der Benutzer:
    
    - Bei einer solchen Kombination aus Abonnements liegt es in der Verantwortung des Administrators sicherzustellen, dass nur diese Teilmenge der Benutzer die Klassifizierungs- und Bezeichnungsfeatures verwenden kann. Die anderen Benutzer sollten den Azure Information Protection-Client im reinen Schutzmodus ausführen. 

- Ihre Organisation verfügt über ein Abonnement für Azure Information Protection, aber Ihre Bezeichner wurden noch nicht für Sie konfiguriert.
    
    - Dies kann geschehen, wenn alle Bezeichner in der globalen Richtlinie deaktiviert sind und Ihr Konto nicht einer bereichsbezogenen Richtlinie hinzugefügt wurde. Möglicherweise ist der Grund dafür, dass Ihre IT-Abteilung erst damit begonnen hat, Azure Information Protection einzuführen, aber noch keine Bezeichner für die Klassifizierung Ihrer Dokumente und E-Mails bereitgestellt hat. In der Zwischenzeit können Sie den Azure Information Protection-Client zum Schützen von Dateien und zum Anzeigen geschützter Dateien verwenden.

- Ihre Organisation verfügt über ein Abonnement von Azure Information Protection, aber Sie können die Azure Information Protection-Richtlinie nicht herunterladen. 
    
    - Dies kann aufgrund einer Fehlkonfiguration oder einer nicht erfolgreichen Anmeldung auftreten. Wenden Sie sich an den Helpdesk oder Ihren Administrator, aber in der Zwischenzeit können Sie möglicherweise mit dem Azure Information Protection-Client Dateien schützen und geschützte Dateien anzeigen.

- Ihre Organisation nutzt ausschließlich Active Directory Rights Management Services (AD RMS). 


## <a name="limitations-for-protection-only-mode"></a>Einschränkungen für den reinen Schutzmodus

- In Office-Apps wird die Azure Information Protection-Leiste nicht angezeigt. Wenn Sie auf **Schutz**  >  **Leiste anzeigen** klicken, ist diese Menüoption nicht verfügbar.

- Wenn Sie das Dialogfeld **Klassifizieren und schützen – Azure Information Protection** mit dem Datei-Explorer verwenden, werden keine Bezeichnungen für die Klassifizierung angezeigt. Stattdessen wird eine Option zum Auswählen von RMS-Vorlagen angezeigt, wie in der vorherigen Abbildung veranschaulicht. 

## <a name="supported-tasks-for-protection-only-mode"></a>Unterstützte Aufgaben für den reinen Schutzmodus

- Schützen (und Aufheben des Schutzes) von Dokumenten und e-Mails in Ihren Office-Apps mithilfe des Office Information Rights Management (unm)-Features: Klicken Sie beispielsweise auf **Datei**  >  **Info**  >  **Schutz Dokument**  >  **beschränken Zugriff**. Weitere Informationen finden Sie unter [Verwenden von Informationsschutz mit Office 365, Office 2019, Office 2016 oder Office 2013](../help-users.md#using-information-protection-with-office365-office-2019-office-2016-or-office2013).

- Dateien mithilfe des Windows-Datei-Explorer schützen (und den Schutz aufheben): Klicken Sie mit der rechten Maustaste auf die Datei, Dateien oder den Ordner, und wählen Sie dann **Klassifizieren und schützen** aus. Klicken Sie zum Anwenden von Schutz, der von Ihrem Administrator konfiguriert wurde, im Dialogfeld **Klassifizieren und schützen - Azure Information Protection** auf **Vorlage auswählen**, und wählen Sie dann eine der verfügbaren Vorlagen aus.

- Zeigen Sie geschützte Dateien mit dem Azure Information Protection-Viewer an.

- Greifen Sie über Ihre Office-Apps auf die Website zum Nachverfolgen von Dokumenten zu. Sie müssen jedoch über ein gültiges Abonnement zum Nachverfolgen und Widerrufen von Dokumenten für diese Website verfügen.
  
