---
title: Entfernen von Azure Information Protection-Bezeichnungen
description: "Anweisungen zum Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien, die von Azure Information Protection bezeichnet oder durch Rights Management geschützt wurden."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: af6f57c265509f383dfe1354e5d1256665fc155b
ms.lasthandoff: 02/24/2017


---

# <a name="remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection-or-protected-by-rights-management"></a>Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien und E-Mails, die von Azure Information Protection bezeichnet oder durch Rights Management geschützt wurden

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Wenn der [Azure Information Protection-Client auf Ihrem Computer installiert ist](install-client-app.md), können Sie Klassifizierungsbezeichnungen und den Schutz von Dateien und E-Mails entfernen.

Wenn die zu entfernende Bezeichnung für die Anwendung von Schutz konfiguriert ist, wird durch diese Aktion auch der Schutz der Datei entfernt. Sie werden möglicherweise zur Dokumentierung aufgefordert, warum Sie die Bezeichnung entfernen.

> [!IMPORTANT]
> Sie müssen Besitzer der Datei sein, um den Schutz entfernen zu können, oder Ihnen müssen die Berechtigungen zum Entfernen des Schutzes erteilt worden sein (Rights Management-Berechtigung „Extrahieren“ oder „Vollzugriff“).

Wenn Sie eine andere Bezeichnung oder einen anderen Satz von Schutzeinstellungen auswählen möchten, müssen Sie die Bezeichnung oder den Schutz entfernen. Wählen Sie stattdessen eine neue Bezeichnung und bei Bedarf können Sie benutzerdefinierte Berechtigungen definieren. 

Sie können Bezeichnungen und den Schutz von Office-Dokumenten und E-Mails entfernen, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können Bezeichnungen und den Schutz auch über den **Datei-Explorer** entfernen, der zusätzliche Dateitypen unterstützt und eine bequeme Methode zum Entfernen von Bezeichnungen und des Schutzes von mehreren Dateien gleichzeitig darstellt.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Verwenden von Office-Apps zum Entfernen von Bezeichnungen und des Schutzes von Dokumenten und E-Mails

Klicken Sie auf der Leiste „Information Protection“ auf das Symbol **Delete label ** (Bezeichnung löschen):

![Azure Information Protection-Leiste – Bezeichnung löschen](../media/delete-label.png)

Wenn das Symbol **Delete label** (Bezeichnung löschen) nicht sofort verfügbar ist, klicken Sie zuerst auf das Symbol **Edit label** (Bezeichnung bearbeiten):

![Azure Information Protection-Leiste – Bezeichnung bearbeiten](../media/edit-label.png)

> [!NOTE]
> Wenn diese Information Protection-Leiste in Ihren Office-Apps nicht angezeigt wird:
> 
> - Möglicherweise ist der Azure Information Protection-Client nicht [installiert](install-client-app.md) oder der Client wird im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt.

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Verwenden des Datei-Explorer zum Entfernen von Bezeichnungen und des Schutzes von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie die Bezeichnungen und den Schutz einzelner Dateien, mehrerer Dateien oder eines Ordners schnell entfernen. Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch ausgewählt. 

1.  Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**.

2. So entfernen Sie eine Bezeichnung: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf **Delete label** (Bezeichnung löschen). Wenn die Bezeichnung für die Anwendung von Schutz konfiguriert wurde, wird dieser Schutz automatisch entfernt.

3. So entfernen Sie den benutzerdefinierten Schutz einer einzelnen Datei: Deaktivieren Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen).
    
4. So entfernen Sie den benutzerdefinierten Schutz für mehrere Dateien: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf die Option **Remove custom permissions** (Benutzerdefinierte Berechtigungen entfernen).

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
