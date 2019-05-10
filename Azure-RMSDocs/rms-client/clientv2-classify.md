---
title: Klassifizieren Sie mithilfe des Azure Information Protection unified bezeichnungs-Clients
description: Anweisungen, wie Sie Ihre Dokumente und e-Mails klassifizieren, bei der Verwendung von Azure Information Protection bezeichnungs-Client für Windows Unified.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: c7ec1c5f6a929d9b6b810b647e6cb6dbe3c42316
ms.sourcegitcommit: f9077101a974459a4252e763b5fafe51ff15a16f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64767957"
---
# <a name="user-guide-classify-a-file-or-email-by-using-the-azure-information-protection-unified-labeling-client-for-windows"></a>Leitfaden: Klassifizieren einer Datei oder e-Mail mithilfe des Azure Information Protection unified bezeichnungs-Clients für Windows

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

> [!NOTE]
> Mithilfe dieser Anleitung können Sie Ihre Dokumente und E-Mails klassifizieren, jedoch nicht schützen. Wenn Sie Ihre Dokumente und E-Mails auch schützen möchten, lesen Sie die [Anleitung zum Klassifizieren und Schützen](clientv2-classify-protect.md). Wenn Sie nicht sicher sind, welche Anleitung Sie verwenden sollen, wenden Sie sich an Ihren Systemadministrator oder den Helpdesk.

Ihre Dokumente und E-Mails können Sie am einfachsten klassifizieren, indem Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können jedoch auch Dateien mithilfe des **Datei-Explorers** klassifizieren. Diese Methode unterstützt weitere Dateitypen und ist ein bequemer Weg zum gleichzeitigen Klassifizieren mehrerer Dateien. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren Ihrer Dokumente und E-Mails

Von der **Startseite** Registerkarte die **Vertraulichkeit** Menüband auf die Schaltfläche, und wählen Sie dann eine der Bezeichnungen, die für Sie konfiguriert wurde. Zum Beispiel:

![Beispiel für die Schaltfläche Empfindlichkeit](../media/sensitivity-not-set-callout.png)

Oder, wenn Sie ausgewählt haben **Leiste anzeigen** aus der **Vertraulichkeit** Schaltfläche können Sie eine Bezeichnung aus der Azure Information Protection-Leiste auswählen. Zum Beispiel:

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-barv2-not-set-callout.png)

Wählen Sie zum Festlegen einer Bezeichnung wie "Allgemein" **allgemeine**. Wenn Sie nicht sicher sind, welche Bezeichnung auf das aktuelle Dokument oder die E-Mail angewendet werden soll, verwenden Sie die QuickInfos für Bezeichnungen, um weitere Informationen zu den einzelnen Bezeichnungen und ihrer Anwendung zu erhalten. 

Wenn auf das Dokument bereits eine Bezeichnung angewendet wurde und Sie diese ändern möchten, können Sie eine andere Bezeichnung auswählen. Wenn Sie die Azure Information Protection-Leiste angezeigt haben, und die Bezeichnungen nicht, auf der Leiste für die Sie auswählen angezeigt werden, klicken Sie zuerst auf die **Bezeichnung bearbeiten** Symbol neben dem aktuellen Bezeichnungswert.

Neben der manuellen Auswahl von Bezeichnungen können Bezeichnungen auch auf die folgende Weise angewendet werden:

- Ihr Administrator konfiguriert eine Standardbezeichnung, die Sie beibehalten oder ändern können.

- Ihr Administrator konfiguriert die Bezeichnungen automatisch festgelegt werden, wenn vertraulicher Informationen erkannt wird.

- Ihr Administrator konfiguriert empfohlene Bezeichnungen aus, wenn vertraulicher Informationen erkannt wird, und Sie aufgefordert werden, die Empfehlung übernehmen (und die Bezeichnung angewendet wird) oder zurückweisen (empfohlene Bezeichnung wird nicht angewendet).

### <a name="exceptions-for-the-sensitivity-button"></a>Ausnahmen für die Schaltfläche "Vertraulichkeit"

##### <a name="dont-see-the-sensitivity-button-in-your-office-apps"></a>Werden die Schaltfläche "Vertraulichkeit", in Ihren Office-apps nicht angezeigt?

- Sie besitzen möglicherweise nicht den Azure Information Protection unified bezeichnungs-Client [installiert](install-unifiedlabelingclient-app.md).

- Wenn Sie nicht angezeigt wird eine **Vertraulichkeit** Menüband auf die Schaltfläche allerdings sehe eine **schützen** stattdessen die Schaltfläche mit den Beschriftungen, Sie haben die Azure Information Protection-Client installiert ist und nicht die Azure Information Protection einheitliche bezeichnungs-Client. [Weitere Informationen](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)

##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>Wird die erwartete Bezeichnung nicht angezeigt? 

- Wenn Ihr Administrator kürzlich eine neue Bezeichnung für Sie konfiguriert hat, schließen Sie alle Instanzen der Office-App und öffnen Sie sie anschließend erneut. Durch diese Aktion werden Änderungen an den Bezeichnungen gesucht.

- Die Bezeichnung befindet sich möglicherweise in einer bereichsbezogenen Richtlinie, die Ihr Konto nicht umfasst. Wenden Sie sich an den Helpdesk oder Ihren Administrator.


## <a name="using-file-explorer-to-classify-files"></a>Verwenden des Datei-Explorers zum Klassifizieren von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie eine einzelne Datei, mehrere Dateien oder einen Ordner schnell klassifizieren. 

Wenn Sie einen Ordner auswählen, werden automatisch auch alle Dateien und Unterordner in diesem Ordner für die Klassifizierung ausgewählt, die Sie festlegen. Neue Dateien, die Sie in diesem Ordner oder Unterordner erstellen, werden jedoch nicht automatisch klassifiziert.

Wenn Sie den Datei-Explorer zum Klassifizieren Ihrer Dateien verwenden und eine oder mehrere der Bezeichnungen abgeblendet angezeigt werden, unterstützen die ausgewählten Dateien die Klassifizierung nicht, ohne sie nicht gleichzeitig auch zu schützen.

Das Administratorhandbuch enthält eine vollständige Liste der Dateitypen, die Klassifizierung ohne Schutz unterstützen: [Nur für die Klassifizierung unterstützte Dateitypen](clientv2-admin-guide-file-types.md#file-types-supported-for-classification-only).

### <a name="to-classify-a-file-by-using-file-explorer"></a>So klassifizieren Sie eine Datei mithilfe des Datei-Explorers

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**. Zum Beispiel:
    
    ![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

2. Verwenden Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Bezeichnungen wie in einer Office-Anwendung, wodurch die Klassifizierung gemäß der Definition Ihres Administrators festgelegt wird. 
    
    Wenn keine der Bezeichnungen ausgewählt werden kann (Bezeichnungen sind abgeblendet): Die ausgewählte Datei unterstützt die Klassifizierung nicht. Zum Beispiel:
    
    ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“** verfügbar](../media/v2info-protect-dialog-labels-dimmed.png)

3. Wenn Sie eine Datei ausgewählt haben, die die Klassifizierung nicht unterstützt, klicken Sie auf **Schließen**. Diese Datei kann nicht ohne Schutz klassifiziert werden.
    
    Wenn Sie eine Bezeichnung ausgewählt haben, klicken Sie auf **Übernehmen**, und warten Sie auf die Nachricht **Verarbeitung abgeschlossen**, um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.

Wenn Sie die Bezeichnung, die Sie ausgewählt haben, ändern möchten, wiederholen Sie diesen Vorgang einfach, und wählen Sie eine andere aus.

Die Klassifizierung, die Sie angegeben haben, bleibt der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. 

## <a name="other-instructions"></a>Sonstige Anweisungen

Weitere Anleitung des Benutzers führen für den einheitlichen Azure Information Protection-Bezeichnung-Client für Windows:

- [Was möchten Sie tun?](clientv2-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren

Finden Sie unter [Überblick über die vertraulichkeitsbezeichnungen](/Office365/SecurityCompliance/sensitivity-labels).

