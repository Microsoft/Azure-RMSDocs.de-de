---
title: Remove-vertraulichkeitsbezeichnungen mithilfe von Azure Information Protection unified bezeichnungs-Client für Windows
description: Anweisungen zum Entfernen von vertraulichkeitsbezeichnungen und des Schutzes von Dateien, die von Azure Information Protection Bezeichnung erhalten haben.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ''
ms.suite: ems
ms.openlocfilehash: 187c36acddb8a6b2e5b1451500640dfd832a8f3f
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60181133"
---
# <a name="user-guide-remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection"></a>Leitfaden: Entfernen von Bezeichnungen und des Schutzes von Dateien und e-Mails, die von Azure Information Protection gekennzeichnet wurde, haben

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*
>
> *Anleitungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn die einheitliche Azure Information Protection-Client ist [auf Ihrem Computer installierten](install-client-app.md), Sie können die vertraulichkeitsbezeichnungen und den Schutz von Dateien und e-Mails entfernen.

Wenn die vertraulichkeitsbezeichnung, die Sie entfernen zum Anwenden von Schutz konfiguriert ist, entfernt diese Aktion auch Schutz aus der Datei. Sie werden möglicherweise zur Dokumentierung aufgefordert, warum Sie die Bezeichnung entfernen.

> [!IMPORTANT]
> Sie müssen Besitzer der Datei sein, um den Schutz entfernen zu können, oder Ihnen müssen die Berechtigungen zum Entfernen des Schutzes erteilt worden sein (Rights Management-Berechtigung **Exportieren** oder **Vollzugriff**).

Wenn Sie eine andere Bezeichnung oder einen anderen Satz von Schutzeinstellungen auswählen möchten, müssen Sie die Bezeichnung oder den Schutz entfernen. Wählen Sie stattdessen eine neue Bezeichnung und bei Bedarf können Sie benutzerdefinierte Berechtigungen definieren, indem Sie die Datei-Explorer. 

Sie können Bezeichnungen und den Schutz von Office-Dokumenten und E-Mails entfernen, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können Bezeichnungen und den Schutz auch über den **Datei-Explorer** entfernen, der zusätzliche Dateitypen unterstützt und eine bequeme Methode zum Entfernen von Bezeichnungen und des Schutzes von mehreren Dateien gleichzeitig darstellt.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Verwenden von Office-Apps zum Entfernen von Bezeichnungen und des Schutzes von Dokumenten und E-Mails

Von der **Startseite** Registerkarte die **Vertraulichkeit** Menüband auf die Schaltfläche, und deaktivieren Sie die ausgewählte Bezeichnung.

Oder, wenn Sie ausgewählt haben **Leiste anzeigen** aus der **Vertraulichkeit** Schaltfläche können Sie auswählen, die **Bezeichnung löschen** Symbol in der Azure Information Protection-Leiste:

![Azure Information Protection-Leiste – Bezeichnung löschen](../media/v2delete-label.png)

Wenn die **Bezeichnung löschen** Symbol nicht sofort verfügbar ist, wählen Sie zuerst die **Bezeichnung bearbeiten** Symbol:

![Azure Information Protection-Leiste – Bezeichnung bearbeiten](../media/v2edit-label.png)

Wenn Sie noch immer nicht angezeigt werden die **Bezeichnung löschen** Symbol, erlaubt Ihr Administrator nicht Sie diese Option verwenden, da alle Dokumente und e-Mails Bezeichnungen aufweisen müssen.

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Verwenden des Datei-Explorer zum Entfernen von Bezeichnungen und des Schutzes von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie die Bezeichnungen und den Schutz einzelner Dateien, mehrerer Dateien oder eines Ordners schnell entfernen. Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch ausgewählt. 

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**.

2. So entfernen Sie eine Bezeichnung: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf **Bezeichnung löschen**. Wenn die Bezeichnung für die Anwendung von Schutz konfiguriert wurde, wird dieser Schutz automatisch entfernt.

3. So entfernen Sie den benutzerdefinierten Schutz einer einzelnen Datei: Deaktivieren Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen). 

4. So entfernen Sie den benutzerdefinierten Schutz von mehreren Dateien: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf die Option **Remove custom permissions** (Benutzerdefinierte Berechtigungen entfernen).

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    

Finden Sie unter [Überblick über die vertraulichkeitsbezeichnungen](/Office365/SecurityCompliance/sensitivity-labels).

