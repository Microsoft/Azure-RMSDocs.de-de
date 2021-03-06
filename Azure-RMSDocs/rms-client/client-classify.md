---
title: Klassifizieren-Azure Information Protection klassischer Client
description: Anweisungen zum Klassifizieren Ihrer Dokumente und e-Mails, wenn Sie den Azure Information Protection klassischen Client für Windows verwenden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/09/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: d65c7690-fab7-4823-845c-8c73903e9c79
ROBOTS: NOINDEX
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 9d2930b7cc5ed01ecb97a59247f0082900d1a606
ms.sourcegitcommit: 78c7ab80be7c292ea4bc62954a4e29c449e97439
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98164163"
---
# <a name="user-guide-classify-a-file-or-email-with-the-azure-information-protection-classic-client"></a>Benutzerhandbuch: klassifizieren einer Datei oder e-Mail mit dem klassischen Azure Information Protection-Client

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie im [Benutzerhandbuch für Unified Bezeichnung-Client](clientv2-classify.md). *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

> [!TIP]
> Mithilfe dieser Anleitung können Sie Ihre Dokumente und E-Mails klassifizieren, jedoch nicht schützen. Wenn Sie Ihre Dokumente und E-Mails auch schützen möchten, lesen Sie die [Anleitung zum Klassifizieren und Schützen](client-classify-protect.md). Wenn Sie nicht sicher sind, welche Anleitung Sie verwenden sollen, wenden Sie sich an Ihren Systemadministrator oder den Helpdesk.

Die einfachste Möglichkeit zum Klassifizieren Ihrer Dokumente und E-Mails bietet sich, wenn Sie sie in den Office-Desktopanwendungen **Word**, **Excel**, **PowerPoint** oder **Outlook** erstellen oder bearbeiten. 

Sie können jedoch auch Dateien mithilfe des **Datei-Explorers** klassifizieren. Diese Methode unterstützt weitere Dateitypen und ist ein bequemer Weg zum gleichzeitigen Klassifizieren mehrerer Dateien. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren Ihrer Dokumente und E-Mails

Verwenden Sie die Azure Information Protection-Leiste, und wählen Sie eine der Bezeichnungen aus, die für Sie konfiguriert wurde. 

Die folgende Abbildung zeigt beispielsweise, dass das Dokument noch keine Bezeichnung erhalten hat, da für **Vertraulichkeit** die Option **Nicht festgelegt** angezeigt wird. Um eine Bezeichnung wie „Allgemein“ festzulegen, klicken Sie auf **Allgemein**. Wenn Sie nicht sicher sind, welche Bezeichnung auf das aktuelle Dokument oder die E-Mail angewendet werden soll, verwenden Sie die QuickInfos für Bezeichnungen, um weitere Informationen zu den einzelnen Bezeichnungen und ihrer Anwendung zu erhalten. 

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-bar-not-set-callout.png)

Wenn auf das Dokument bereits eine Bezeichnung angewendet wurde und Sie diese ändern möchten, können Sie eine andere Bezeichnung auswählen. Wenn die Bezeichnungen nicht auf der Leiste angezeigt werden, klicken Sie zunächst neben dem aktuellen Bezeichnungswert auf das Symbol **Edit label** (Bezeichnung bearbeiten).

> [!TIP]
> Sie können auch Bezeichnungen über die Schaltfläche **Schützen** auf der Registerkarte **Datei** auswählen.

Neben der manuellen Auswahl von Bezeichnungen können Bezeichnungen auch auf die folgende Weise angewendet werden:

- Ihr Administrator konfiguriert eine Standardbezeichnung, die Sie beibehalten oder ändern können.

- Ihr Administrator konfiguriert empfohlene Aufforderungen zum Auswählen einer bestimmten Bezeichnung, wenn vertrauliche Daten erkannt wurden. Sie können die Empfehlung übernehmen (und die Bezeichnung anwenden) oder zurückweisen (empfohlene Bezeichnung wird nicht angewendet).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Ausnahmen für die Azure Information Protection-Leiste 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Wenn diese Information Protection-Leiste in Ihren Office-Apps nicht angezeigt wird:

- Möglicherweise ist der Azure Information Protection-Client auf Ihrem Computer nicht [installiert](install-client-app.md).

- Der Client ist installiert, jedoch hat Ihr Administrator eine Einstellung vorgenommen, sodass die Leiste nicht angezeigt wird. Wählen Sie stattdessen Bezeichnungen über die Schaltfläche **Schützen** auf der Registerkarte **Datei** im Office-Menüband aus. 

##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>Wenn die erwartete Bezeichnung auf der Leiste nicht angezeigt wird: 

- Wenn Ihr Administrator kürzlich eine neue Bezeichnung für Sie konfiguriert hat, schließen Sie alle Instanzen der Office-App und öffnen Sie sie anschließend erneut. Durch diese Aktion werden Änderungen an den Bezeichnungen gesucht.

- Die Bezeichnung befindet sich möglicherweise in einer bereichsbezogenen Richtlinie, die Ihr Konto nicht umfasst. Wenden Sie sich an den Helpdesk oder Ihren Administrator.


## <a name="using-file-explorer-to-classify-files"></a>Verwenden des Datei-Explorers zum Klassifizieren von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie eine einzelne Datei, mehrere Dateien oder einen Ordner schnell klassifizieren. 

Wenn Sie einen Ordner auswählen, werden automatisch auch alle Dateien und Unterordner in diesem Ordner für die Klassifizierung ausgewählt, die Sie festlegen. Neue Dateien, die Sie in diesem Ordner oder Unterordner erstellen, werden jedoch nicht automatisch klassifiziert.

Wenn Sie den Datei-Explorer zum Klassifizieren Ihrer Dateien verwenden und eine oder mehrere der Bezeichnungen abgeblendet angezeigt werden, unterstützen die ausgewählten Dateien die Klassifizierung nicht, ohne sie nicht gleichzeitig auch zu schützen.

Das Administratorhandbuch enthält eine vollständige Liste der Dateitypen, die Klassifizierung ohne Schutz unterstützen: [Nur für die Klassifizierung unterstützte Dateitypen](client-admin-guide-file-types.md#file-types-supported-for-classification-only).

### <a name="to-classify-a-file-by-using-file-explorer"></a>So klassifizieren Sie eine Datei mithilfe des Datei-Explorers

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**. Beispiel:
    
    ![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

2. Verwenden Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Bezeichnungen wie in einer Office-Anwendung, wodurch die Klassifizierung gemäß der Definition Ihres Administrators festgelegt wird. 
    
    Wenn keine der Bezeichnungen ausgewählt werden kann, weil sie abgeblendet angezeigt werden: Die ausgewählte Datei unterstützt die Klassifizierung nicht. Beispiel:
    
    ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“** verfügbar](../media/info-protect-dialog-labels-dimmed.png)

3. Wenn Sie eine Datei ausgewählt haben, die die Klassifizierung nicht unterstützt, klicken Sie auf **Schließen**. Diese Datei kann nicht ohne Schutz klassifiziert werden.
    
    Wenn Sie eine Bezeichnung ausgewählt haben, klicken Sie auf **Übernehmen**, und warten Sie auf die Nachricht **Verarbeitung abgeschlossen**, um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.

Wenn Sie die Bezeichnung, die Sie ausgewählt haben, ändern möchten, wiederholen Sie diesen Vorgang einfach, und wählen Sie eine andere aus.

Die Klassifizierung, die Sie angegeben haben, bleibt der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. 
## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](../configure-policy.md).

