---
title: "Löschen oder Ändern der Position einer Azure Information Protection-Bezeichnung"
description: "Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen löschen oder deren Position ändern, indem Sie diese Einstellungen in der Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: b6694c7c205f7ccd899669cc887b79ab39ec8ec4
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen löschen oder deren Position ändern, indem Sie die folgenden Aktionen in der Azure Information Protection-Richtlinie auswählen.

![Löschen oder Ändern der Position von Bezeichnungen in der Azure Information Protection-Richtlinie](../media/info-protect-contextmenu.png)

Wenn Sie eine Bezeichnung löschen, die auf Dokumente und E-Mails angewendet wurde, und anschließend die Azure Information Protection-Richtlinie veröffentlichen, wird diese Bezeichnung automatisch von diesen Dokumenten oder E-Mails entfernt, wenn diese das nächste Mal vom Azure Information Protection-Client geöffnet werden.

Wenn die Bezeichnung jedoch Schutz angewendet hat, wird dieser nicht entfernt. Die Schutzeinstellungen der Bezeichnung sind nach wie vor vorhanden und werden in den **Protection templates** (Schutzvorlagen) angezeigt. Eine solche Vorlage kann nun in eine neue Bezeichnung konvertiert oder mit einer Bezeichnung verknüpft werden. Solange diese Vorlage vorhanden ist, können Sie keine neue Bezeichnung mit dem Namen der gelöschten Bezeichnung erstellen. Wenn Sie diese Aktion dennoch ausführen möchten, habe Sie mehrere Möglichkeiten:

- Konvertieren Sie die Vorlage in eine Bezeichnung. 
    
    Diese Aktion wird empfohlen, da Sie bei Bedarf den Namen der Vorlage ändern und die Schutzeinstellungen modifizieren können.

- Verwenden Sie PowerShell zum Umbenennen oder Löschen der Vorlage.
    
    Achten Sie vor dem Ausführen dieser Aktionen darauf, ob andere Administratoren oder Dienste die Vorlage verwenden, und identifizieren Sie diese anhand ihres aktuellen Namens. Löschen Sie eine Vorlage nur, wenn Sie Dokumente oder E-Mails, die durch diese Vorlage geschützt wurden, nicht öffnen müssen.

Weitere Informationen zum Verwalten von Schutzvorlagen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).

Bevor Sie eine Bezeichnung löschen, erwägen Sie, diese stattdessen zu deaktivieren. Wenn Sie eine Bezeichnung deaktivieren, die auf Dokumente und E-Mails angewendet wurde, wird die angewendete Bezeichnung nicht von diesen Dokumenten und E-Mails entfernt. Sie wird aber in der Information Protection-Leiste nicht mehr als Bezeichnung angezeigt, die von Benutzern ausgewählt werden kann. Durch Deaktivieren einer Bezeichnung können Sie zudem die ursprüngliche Konfiguration beibehalten, damit Benutzer die Bezeichnung zu einem späteren Zeitpunkt wieder auswählen können, wenn Sie diese wieder aktivieren.

Ordnen Sie die Bezeichnungen so an, dass Sie auf der Information Protection-Leiste in einer logischen Reihenfolge für die Benutzer angezeigt werden. Ordnen Sie die Bezeichnungen z. B. nach steigender Vertraulichkeitsstufe an, sodass den Benutzern zuerst die niedrigste Vertraulichkeitsstufe und zuletzt die höchste Vertraulichkeitsstufe angezeigt wird. Die [Standardrichtlinie](configure-policy-default.md) verwendet diese Konfiguration und spiegelt die zunehmende Vertraulichkeit in den Bezeichnungsnamen wider.

> [!IMPORTANT]
>Wenn Sie [Bedingungen](configure-policy-classification.md) für Ihre Bezeichnungen konfigurieren, die für mehrere Bezeichnungen gelten, müssen Sie diese Anordnung für Ihre Bezeichnungen wählen (niedrigste bis höchste Vertraulichkeitsstufe). Mit dieser Anordnung wird sichergestellt, dass bei der Auswertung der Bedingungen die Bezeichnung mit der höchsten Vertraulichkeitsstufe angewendet wird.


Verwenden Sie die folgenden Anleitungen, um diese Änderungen vorzunehmen.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gilt, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
    Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Führen Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) oder auf dem Blatt **Richtlinie:\<name>** eine der folgenden Aktionen durch: 

    - So löschen Sie eine Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, die gelöscht werden soll, klicken Sie auf **Delete this label** (Diese Bezeichnung löschen), und klicken Sie auf **Yes** (Ja), um den Vorgang zu bestätigen. Klicken Sie dann auf **Save** (Speichern). 

    - So deaktivieren Sie eine Bezeichnung: Wählen Sie die Bezeichnung aus, die Sie deaktivieren möchten. Klicken Sie auf dem Blatt **Label** (Bezeichnung) für **Enabled** (Aktiviert) auf **Off** (Aus), und klicken Sie dann auf **Save** (Speichern).

    - So ändern Sie die Position einer Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, deren Position Sie ändern möchten, und klicken Sie auf **Move up** (Nach oben) oder **Move down** (Nach unten), bis sich die Bezeichnung an der gewünschten Position befindet. Klicken Sie dann auf **Save** (Speichern). 

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

