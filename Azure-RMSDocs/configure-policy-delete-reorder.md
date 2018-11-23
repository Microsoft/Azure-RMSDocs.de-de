---
title: Löschen oder Ändern der Position einer Azure Information Protection-Bezeichnung
description: Sie können die Position der Azure Information Protection-Bezeichnungen, die Benutzern angezeigt werden, löschen oder ändern.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/04/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: cf5d5a97c03bca090b65e43d6db0393909d0572f
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170075"
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Sie können die Position der Azure Information Protection-Bezeichnungen, die Benutzern in ihren Office-Anwendungen angezeigt werden, löschen oder ändern, indem Sie die folgenden Aktionen für die Bezeichnungen auswählen.

![Löschen oder Ändern der Position von Bezeichnungen in der Azure Information Protection-Richtlinie](./media/info-protect-contextmenu.png)

Wenn Sie eine Bezeichnung löschen, die auf Dokumente und E-Mails angewendet wurde, wird Benutzern der Bezeichnungsstatus **Nicht festgelegt** angezeigt, wenn diese Dokumente und E-Mails anschließend vom Azure Information Protection-Client geöffnet werden. Die Bezeichnungsinformationen bleiben jedoch in den Metadaten und können weiterhin von Diensten gelesen werden, die nach diesen Informationen suchen.

Wenn die Bezeichnung Schutz angewendet hat, wird dieser zudem nicht entfernt. Die Schutzeinstellungen der Bezeichnung sind nach wie vor vorhanden und werden im Abschnitt **Schutzvorlagen** angezeigt. Eine solche Vorlage kann nun in eine neue Bezeichnung konvertiert werden. Solange diese Vorlage vorhanden ist, können Sie keine neue Bezeichnung mit dem Namen der gelöschten Bezeichnung erstellen. Wenn Sie diese Aktion dennoch ausführen möchten, habe Sie mehrere Möglichkeiten:

- Konvertieren Sie die Vorlage in eine Bezeichnung. 
    
    Diese Aktion wird empfohlen, da Sie bei Bedarf den Namen der Vorlage ändern und die Schutzeinstellungen modifizieren können.

- Verwenden Sie PowerShell zum Umbenennen oder Löschen der Vorlage.
    
    Achten Sie vor dem Ausführen dieser Aktionen darauf, ob andere Administratoren oder Dienste die Vorlage verwenden, und identifizieren Sie diese anhand ihres aktuellen Namens. Löschen Sie eine Vorlage nur, wenn Sie Dokumente oder E-Mails, die durch diese Vorlage geschützt wurden, nicht öffnen müssen.

Weitere Informationen zum Verwalten von Schutzvorlagen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).

Bevor Sie eine Bezeichnung löschen, sollten Sie stattdessen in Erwägung ziehen, diese zu deaktivieren oder aus der Richtlinie zu entfernen:
    
- Wenn Sie eine Bezeichnung deaktivieren, die auf Dokumente und E-Mails angewendet wurde, wird die angewendete Bezeichnung nicht aus diesen Dokumenten und E-Mails entfernt. Die Bezeichnung ist nach wie vor in der Richtlinie vorhanden, wird jedoch nicht mehr als Bezeichnung angezeigt, die Benutzer in der Information Protection-Leiste auswählen können. Durch Deaktivieren einer Bezeichnung können Sie die ursprüngliche Konfiguration beibehalten, damit Benutzer die Bezeichnung zu einem späteren Zeitpunkt wieder auswählen können, wenn Sie diese wieder aktivieren.

- Wenn Sie eine Bezeichnung aus einer Richtlinie entfernen, wird die angewendete Bezeichnung ebenfalls nicht aus diesen Dokumenten und E-Mails entfernt. Wenn Sie die Bezeichnung aus der Richtlinie entfernen, wird sie jedoch für Sie verfügbar und kann zu einer anderen Richtlinie hinzugefügt werden. Weitere Informationen finden Sie unter [Hinzufügen einer Bezeichnung zu oder Entfernen aus einer Azure Information Protection-Richtlinie](configure-policy-add-remove-label.md).

Ordnen Sie die Bezeichnungen so an, dass Sie auf der Information Protection-Leiste in einer logischen Reihenfolge für die Benutzer angezeigt werden. Ordnen Sie die Bezeichnungen z. B. nach steigender Vertraulichkeitsstufe an, sodass den Benutzern zuerst die niedrigste Vertraulichkeitsstufe und zuletzt die höchste Vertraulichkeitsstufe angezeigt wird. Die [Standardrichtlinie](configure-policy-default.md) verwendet diese Konfiguration und spiegelt die zunehmende Vertraulichkeit in den Bezeichnungsnamen wider.

> [!IMPORTANT]
>Wenn Sie [Bedingungen](configure-policy-classification.md) für Ihre Bezeichnungen konfigurieren, die für mehrere Bezeichnungen gelten, müssen Sie diese Anordnung für Ihre Bezeichnungen wählen (niedrigste bis höchste Vertraulichkeitsstufe). Mit dieser Anordnung wird sichergestellt, dass bei der Auswertung der Bedingungen die Bezeichnung mit der höchsten Vertraulichkeitsstufe angewendet wird.


Verwenden Sie die folgenden Anleitungen, um diese Änderungen vorzunehmen.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Führen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** mindestens eine der folgenden Aktionen aus: 

    - So löschen Sie eine Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die zu löschende Bezeichnung auf. Klicken Sie auf **Diese Bezeichnung löschen** und anschließend auf **Ja**, um den Vorgang zu bestätigen. 

    - So deaktivieren Sie eine Bezeichnung: Wählen Sie die Bezeichnung aus, die Sie deaktivieren möchten. Wählen Sie auf dem Blatt **Bezeichnung** bei **Aktiviert** den Eintrag **Aus** aus, und klicken Sie anschließend auf **Speichern**.

    - So ändern Sie die Position einer Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, deren Position Sie ändern möchten, und klicken Sie auf **Move up** (Nach oben) oder **Move down** (Nach unten), bis sich die Bezeichnung an der gewünschten Position befindet.  

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

