---
title: Entfernen von Azure Information Protection-Bezeichnungen
description: Anweisungen zum Entfernen von Klassifizierungsbezeichnungen und des Schutzes von Dateien, die von Azure Information Protection bezeichnet oder durch Rights Management geschützt wurden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 1/13/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ''
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 7dfffcc87a90464dcc2f74b99c74cdb2408214e9
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97385827"
---
# <a name="user-guide-remove-labels-and-protection-from-files-and-emails-that-have-been-labeled-by-azure-information-protection-or-protected-by-rights-management"></a>Benutzerhandbuch: Entfernen der Bezeichnungen und des Schutzes von Dateien und E-Mails, die von Azure Information Protection bezeichnet oder durch Rights Management geschützt wurden

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie im [Benutzerhandbuch für Unified Bezeichnung-Client](client-remove-label-protection.md). *

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn der [Azure Information Protection-Client auf Ihrem Computer installiert ist](install-client-app.md), können Sie Klassifizierungsbezeichnungen und den Schutz von Dateien und E-Mails entfernen.

Wenn die zu entfernende Bezeichnung für die Anwendung von Schutz konfiguriert ist, wird durch diese Aktion auch der Schutz der Datei entfernt. Sie werden möglicherweise zur Dokumentierung aufgefordert, warum Sie die Bezeichnung entfernen.

> [!IMPORTANT]
> Sie müssen Besitzer der Datei sein, um den Schutz entfernen zu können, oder Ihnen müssen die Berechtigungen zum Entfernen des Schutzes erteilt worden sein (Rights Management-Berechtigung **Exportieren** oder **Vollzugriff**).

Wenn Sie eine andere Bezeichnung oder einen anderen Satz von Schutzeinstellungen auswählen möchten, müssen Sie die Bezeichnung oder den Schutz entfernen. Wählen Sie stattdessen eine neue Bezeichnung aus, und bei Bedarf können Sie benutzerdefinierte Berechtigungen definieren, sofern der Administrator diese Konfiguration zulässt. 

Sie können Bezeichnungen und den Schutz von Office-Dokumenten und E-Mails entfernen, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können Bezeichnungen und den Schutz auch über den **Datei-Explorer** entfernen, der zusätzliche Dateitypen unterstützt und eine bequeme Methode zum Entfernen von Bezeichnungen und des Schutzes von mehreren Dateien gleichzeitig darstellt.

## <a name="using-office-apps-to-remove-labels-and-protection-from-documents-and-emails"></a>Verwenden von Office-Apps zum Entfernen von Bezeichnungen und des Schutzes von Dokumenten und E-Mails

Klicken Sie auf der Leiste „Information Protection“ auf das Symbol **Delete label** (Bezeichnung löschen):

![Azure Information Protection-Leiste – Bezeichnung löschen](../media/delete-label.png)

Wenn das Symbol **Delete label** (Bezeichnung löschen) nicht sofort verfügbar ist, klicken Sie zuerst auf das Symbol **Edit label** (Bezeichnung bearbeiten):

![Azure Information Protection-Leiste – Bezeichnung bearbeiten](../media/edit-label.png)

Wenn das Symbol " **Bezeichnung löschen** " weiterhin nicht angezeigt wird, ist es Ihnen nicht gestattet, diese Option zu verwenden, da alle Dokumente und e-Mails über eine Bezeichnung verfügen müssen.

> [!NOTE]
> Wenn diese Information Protection-Leiste in Ihren Office-Apps nicht angezeigt wird:
>
> - Wenn die Schaltfläche **Schützen** auf dem Menüband angezeigt wird, klicken Sie auf **Schützen** und anschließend auf **Leiste anzeigen**.
> 
> - Möglicherweise ist der Azure Information Protection-Client nicht [installiert](install-client-app.md) oder der Client wird im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt.

## <a name="using-file-explorer-to-remove-labels-and-protection-from-files"></a>Verwenden des Datei-Explorer zum Entfernen von Bezeichnungen und des Schutzes von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie die Bezeichnungen und den Schutz einzelner Dateien, mehrerer Dateien oder eines Ordners schnell entfernen. Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch ausgewählt. 

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**.

2. So entfernen Sie eine Bezeichnung: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf **Delete label** (Bezeichnung löschen). Wenn die Bezeichnung für die Anwendung von Schutz konfiguriert wurde, wird dieser Schutz automatisch entfernt.

3. So entfernen Sie den benutzerdefinierten Schutz einer einzelnen Datei: Deaktivieren Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen). 
    
    Wenn Ihnen die Option **Mit benutzerdefinierten Berechtigungen schützen** nicht angezeigt wird, erlaubt Ihr Administrator Ihnen die Verwendung dieser Option nicht.
    
4. So entfernen Sie den benutzerdefinierten Schutz für mehrere Dateien: Klicken Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** auf die Option **Remove custom permissions** (Benutzerdefinierte Berechtigungen entfernen).
    
    Wenn Ihnen die Option **Remove custom permissions** (Benutzerdefinierte Berechtigungen entfernen) nicht angezeigt wird, erlaubt Ihr Administrator Ihnen die Verwendung dieser Option nicht.

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Konfigurationsanweisungen zum Aktivieren der Richtlinieneinstellung **Make the custom permissions option available to users** (Die Option der benutzerdefinierten Berechtigungen Benutzern zur Verfügung stellen) finden Sie unter [Konfigurieren der Richtlinieneinstellungen für Azure Information Protection](../configure-policy-settings.md).

Weitere Konfigurationsanweisungen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](../configure-policy.md).

