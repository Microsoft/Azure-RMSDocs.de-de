---
title: Klassifizieren mithilfe des Azure Information Protection Unified Bezeichnung-Clients
description: Anweisungen zum Klassifizieren Ihrer Dokumente und e-Mails, wenn Sie den Azure Information Protection Unified-Bezeichnungs Client für Windows verwenden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 09/03/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 5c95995477e05ba1cd7bfea2b517b762bfa6748b
ms.sourcegitcommit: af7ac2eeb8f103402c0036dd461c77911fbc9877
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "98559981"
---
# <a name="user-guide-classify-a-file-or-email-by-using-the-azure-information-protection-unified-labeling-client-for-windows"></a>Benutzerhandbuch: klassifizieren einer Datei oder e-Mail mit dem Azure Information Protection Unified Bezeichnung-Client für Windows

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen unter [AIP und ältere Windows-und Office-Versionen](../known-issues.md#aip-and-legacy-windows-and-office-versions).*
>
>***Relevant für**: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie im [klassischen Client Benutzerhandbuch](client-classify.md). *

> [!NOTE]
> Mithilfe dieser Anleitung können Sie Ihre Dokumente und E-Mails klassifizieren, jedoch nicht schützen. Wenn Sie Ihre Dokumente und E-Mails auch schützen möchten, lesen Sie die [Anleitung zum Klassifizieren und Schützen](clientv2-classify-protect.md). Wenn Sie nicht sicher sind, welche Anleitung Sie verwenden sollen, wenden Sie sich an Ihren Systemadministrator oder den Helpdesk.

Die einfachste Möglichkeit zum Klassifizieren Ihrer Dokumente und E-Mails bietet sich, wenn Sie sie in den Office-Desktopanwendungen **Word**, **Excel**, **PowerPoint** oder **Outlook** erstellen oder bearbeiten. 

Sie können jedoch auch Dateien mithilfe des **Datei-Explorers** klassifizieren. Diese Methode unterstützt weitere Dateitypen und ist ein bequemer Weg zum gleichzeitigen Klassifizieren mehrerer Dateien. 

## <a name="using-office-apps-to-classify-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren Ihrer Dokumente und E-Mails

Wählen Sie auf der Registerkarte **Startseite** die **Vertraulichkeits** Schaltfläche im Menüband aus, und wählen Sie dann eine der Bezeichnungen aus, die für Sie konfiguriert wurde. Zum Beispiel:

![Beispiel für sensible Schaltfläche](../media/sensitivity-not-set-callout.png)

Wenn Sie in der **Vertraulichkeits** Schaltfläche **Leiste anzeigen** ausgewählt haben, können Sie auf der Azure Information Protection Leiste eine Bezeichnung auswählen. Zum Beispiel:

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-barv2-not-set-callout.png)

Wählen Sie zum Festlegen einer Bezeichnung (z. b. "Allgemein") die Option **Allgemein** aus. Wenn Sie nicht sicher sind, welche Bezeichnung auf das aktuelle Dokument oder die E-Mail angewendet werden soll, verwenden Sie die QuickInfos für Bezeichnungen, um weitere Informationen zu den einzelnen Bezeichnungen und ihrer Anwendung zu erhalten. 

Wenn auf das Dokument bereits eine Bezeichnung angewendet wurde und Sie diese ändern möchten, können Sie eine andere Bezeichnung auswählen. Wenn Sie die Azure Information Protection Leiste angezeigt haben und die Bezeichnungen nicht auf der Leiste angezeigt werden, die Sie auswählen können, klicken Sie zuerst auf das Symbol " **Bezeichnung bearbeiten** " neben dem Wert der aktuellen Bezeichnung.

Neben der manuellen Auswahl von Bezeichnungen können Bezeichnungen auch auf die folgende Weise angewendet werden:

- Ihr Administrator konfiguriert eine Standardbezeichnung, die Sie beibehalten oder ändern können.

- Der Administrator hat Bezeichnungen so konfiguriert, dass Sie automatisch festgelegt werden, wenn sensible Informationen erkannt werden.

- Ihr Administrator hat Empfohlene Bezeichnungen konfiguriert, wenn vertrauliche Informationen erkannt werden, und Sie werden aufgefordert, die Empfehlung zu akzeptieren (und die Bezeichnung wird angewendet), oder Sie ablehnen (die empfohlene Bezeichnung wird nicht angewendet).

### <a name="exceptions-for-the-sensitivity-button"></a>Ausnahmen für die Vertraulichkeits Schaltfläche

##### <a name="dont-see-the-sensitivity-button-in-your-office-apps"></a>Wird die Vertraulichkeits Schaltfläche in Ihren Office-Apps nicht angezeigt?

- Möglicherweise ist der Azure Information Protection Unified Bezeichnung-Client nicht [installiert](install-unifiedlabelingclient-app.md).

- Wenn auf dem Menüband keine **Vertraulichkeits** Schaltfläche angezeigt wird, aber stattdessen die Schaltfläche **schützen** mit Bezeichnungen angezeigt wird, ist der Azure Information Protection Classic-Client installiert und nicht der Azure Information Protection Unified Label-Client. [Weitere Informationen](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)

##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>Wird die erwartete Bezeichnung nicht angezeigt? 

- Wenn Ihr Administrator kürzlich eine neue Bezeichnung für Sie konfiguriert hat, schließen Sie alle Instanzen der Office-App und öffnen Sie sie anschließend erneut. Durch diese Aktion werden Änderungen an den Bezeichnungen gesucht.

- Die Bezeichnung befindet sich möglicherweise in einer bereichsbezogenen Richtlinie, die Ihr Konto nicht umfasst. Wenden Sie sich an den Helpdesk oder Ihren Administrator.


## <a name="using-file-explorer-to-classify-files"></a>Verwenden des Datei-Explorers zum Klassifizieren von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie eine einzelne Datei, mehrere Dateien oder einen Ordner schnell klassifizieren. 

Wenn Sie einen Ordner auswählen, werden automatisch auch alle Dateien und Unterordner in diesem Ordner für die Klassifizierung ausgewählt, die Sie festlegen. Neue Dateien, die Sie in diesem Ordner oder Unterordner erstellen, werden jedoch nicht automatisch klassifiziert.

Wenn Sie den Datei-Explorer zum Klassifizieren Ihrer Dateien verwenden und eine oder mehrere der Bezeichnungen abgeblendet angezeigt werden, unterstützen die ausgewählten Dateien die Klassifizierung nicht, ohne sie nicht gleichzeitig auch zu schützen.

Das Administratorhandbuch enthält eine vollständige Liste der Dateitypen, die Klassifizierung ohne Schutz unterstützen: [Nur für die Klassifizierung unterstützte Dateitypen](clientv2-admin-guide-file-types.md#file-types-supported-for-classification-only).

### <a name="to-classify-a-file-by-using-file-explorer"></a>So klassifizieren Sie eine Datei mithilfe des Datei-Explorers

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**. Beispiel:
    
    ![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

2. Verwenden Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Bezeichnungen wie in einer Office-Anwendung, wodurch die Klassifizierung gemäß der Definition Ihres Administrators festgelegt wird. 
    
    Wenn keine der Bezeichnungen ausgewählt werden kann, weil sie abgeblendet angezeigt werden: Die ausgewählte Datei unterstützt die Klassifizierung nicht. Zum Beispiel:
    
    ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“** verfügbar](../media/v2info-protect-dialog-labels-dimmed.png)

3. Wenn Sie eine Datei ausgewählt haben, die die Klassifizierung nicht unterstützt, klicken Sie auf **Schließen**. Diese Datei kann nicht ohne Schutz klassifiziert werden.
    
    Wenn Sie eine Bezeichnung ausgewählt haben, klicken Sie auf **Übernehmen**, und warten Sie auf die Nachricht **Verarbeitung abgeschlossen**, um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.

Wenn Sie die Bezeichnung, die Sie ausgewählt haben, ändern möchten, wiederholen Sie diesen Vorgang einfach, und wählen Sie eine andere aus.

Die Klassifizierung, die Sie angegeben haben, bleibt der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. 

## <a name="other-instructions"></a>Sonstige Anweisungen

Weitere Anleitungen finden Sie im Benutzerhandbuch für den Azure Information Protection Unified Bezeichnung-Client für Windows:

- [Was möchten Sie tun?](clientv2-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren

Weitere [Informationen finden Sie unter Informationen zu Sensitivität](/microsoft-365/compliance/sensitivity-labels).

