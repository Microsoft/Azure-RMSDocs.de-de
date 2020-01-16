---
title: Entfernen von Bezeichnungen mit dem Azure Information Protection Unified Label-Client
description: Anweisungen zum Entfernen von Vertraulichkeits Bezeichnungen und zum Schutz von Dateien und e-Mails mithilfe des Azure Information Protection Unified Label-Clients.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/13/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ''
ms.subservice: v2client
ms.suite: ems
ms.custom: user
ms.openlocfilehash: dd65c04165b125df6239792e528f28586a75e78f
ms.sourcegitcommit: 03dc2eb973b20897b30659c2ac6cb43ce0a40e71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/15/2020
ms.locfileid: "75959866"
---
# <a name="user-guide-remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection"></a>Benutzerhandbuch: Entfernen von Bezeichnungen und des Schutzes von Dateien und e-Mails, die von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn die Azure Information Protection Unified Client [auf Ihrem Computer installiert](install-client-app.md)ist, können Sie Vertraulichkeits Bezeichnungen und den Schutz von Dateien und e-Mails entfernen.

Wenn die Vertraulichkeits Bezeichnung, die Sie entfernen, zum Anwenden des Schutzes konfiguriert ist, wird durch diese Aktion auch der Schutz für die Datei entfernt. Sie werden möglicherweise zur Dokumentierung aufgefordert, warum Sie die Bezeichnung entfernen.

> [!IMPORTANT]
> Sie müssen Besitzer der Datei sein, um den Schutz entfernen zu können, oder Ihnen müssen die Berechtigungen zum Entfernen des Schutzes erteilt worden sein (Rights Management-Berechtigung **Exportieren** oder **Vollzugriff**).

Wenn Sie eine andere Bezeichnung oder einen anderen Satz von Schutzeinstellungen auswählen möchten, müssen Sie die Bezeichnung oder den Schutz entfernen. Wählen Sie stattdessen eine neue Bezeichnung aus, und Sie können ggf. benutzerdefinierte Berechtigungen mithilfe des Datei-Explorers definieren. 

Sie können Bezeichnungen und den Schutz von Office-Dokumenten und E-Mails entfernen, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können Bezeichnungen und den Schutz auch über den **Datei-Explorer** entfernen, der zusätzliche Dateitypen unterstützt und eine bequeme Methode zum Entfernen von Bezeichnungen und des Schutzes von mehreren Dateien gleichzeitig darstellt.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Verwenden von Office-Apps zum Entfernen von Bezeichnungen und des Schutzes von Dokumenten und E-Mails

Wählen Sie auf der Registerkarte **Startseite** die **Vertraulichkeits** Schaltfläche im Menüband aus, und löschen Sie die aktuell ausgewählte Bezeichnung.

Wenn Sie die Option **Leiste anzeigen** von der **Vertraulichkeits** Schaltfläche ausgewählt haben, können Sie auf der Azure Information Protection Leiste das Symbol " **Bezeichnung löschen** " auswählen:

![Azure Information Protection-Leiste – Bezeichnung löschen](../media/v2delete-label.png)

Wenn das Symbol " **Bezeichnung löschen** " nicht sofort verfügbar ist, wählen Sie zuerst das Symbol " **Bezeichnung bearbeiten** " aus:

![Azure Information Protection-Leiste – Bezeichnung bearbeiten](../media/v2edit-label.png)

Wenn das Symbol " **Bezeichnung löschen** " weiterhin nicht angezeigt wird, ist es Ihnen nicht gestattet, diese Option zu verwenden, da alle Dokumente und e-Mails über eine Bezeichnung verfügen müssen.

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Verwenden des Datei-Explorer zum Entfernen von Bezeichnungen und des Schutzes von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie die Bezeichnungen und den Schutz einzelner Dateien, mehrerer Dateien oder eines Ordners schnell entfernen. Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch ausgewählt. 

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**.

2. So entfernen Sie eine Bezeichnung: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf **Delete label** (Bezeichnung löschen). Wenn die Bezeichnung für die Anwendung von Schutz konfiguriert wurde, wird dieser Schutz automatisch entfernt.

3. So entfernen Sie den benutzerdefinierten Schutz einer einzelnen Datei: Deaktivieren Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen). 

4. So entfernen Sie den benutzerdefinierten Schutz für mehrere Dateien: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf die Option **Remove custom permissions** (Benutzerdefinierte Berechtigungen entfernen).

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    

Siehe [Übersicht über Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels).

