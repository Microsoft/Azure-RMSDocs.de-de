---
title: "Löschen oder Ändern der Position einer Azure Information Protection-Bezeichnung"
description: "Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen löschen oder deren Position ändern, indem Sie diese Einstellungen in der Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
ms.openlocfilehash: 8cb5c6270c90b7d012607da9aa9e4e6172d33a7b
ms.sourcegitcommit: f0402cf14506b4c61a156a2baf7e69b7b16883a1
translationtype: HT
---
# <a name="how-to-delete-or-reorder-a-label-for-azure-information-protection"></a>Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen löschen oder deren Position ändern, indem Sie diese Einstellungen in der Azure Information Protection-Richtlinie konfigurieren.

![Löschen oder Ändern der Position von Bezeichnungen in der Azure Information Protection-Richtlinie](../media/info-protect-contextmenu.png)

Wenn Sie eine Bezeichnung löschen, die auf Dokumente und E-Mails angewendet wurde, und anschließend die Azure Information Protection-Richtlinie veröffentlichen, wird diese Bezeichnung automatisch von diesen Dokumenten oder E-Mails entfernt, wenn diese das nächste Mal vom Azure Information Protection-Client geöffnet werden.

Bevor Sie eine Bezeichnung löschen, erwägen Sie, diese stattdessen zu deaktivieren. Wenn Sie eine Bezeichnung deaktivieren, die auf Dokumente und E-Mails angewendet wurde, wird die angewendete Bezeichnung nicht von diesen Dokumenten und E-Mails entfernt. Sie wird aber in der Information Protection-Leiste nicht mehr als Bezeichnung angezeigt, die von Benutzern ausgewählt werden kann. Durch Deaktivieren einer Bezeichnung können Sie zudem die ursprüngliche Konfiguration beibehalten, damit Benutzer die Bezeichnung zu einem späteren Zeitpunkt wieder auswählen können, wenn Sie diese wieder aktivieren.

Ordnen Sie die Bezeichnungen so an, dass Sie auf der Information Protection-Leiste in einer logischen Reihenfolge für die Benutzer angezeigt werden. Ordnen Sie die Bezeichnungen z. B. nach steigender Vertraulichkeitsstufe an, sodass den Benutzern zuerst die niedrigste Vertraulichkeitsstufe und zuletzt die höchste Vertraulichkeitsstufe angezeigt wird. Die [Standardrichtlinie](configure-policy-default.md) verwendet diese Konfiguration und spiegelt die zunehmende Vertraulichkeit in den Bezeichnungsnamen wider.

> [!IMPORTANT]
>Wenn Sie [Bedingungen](configure-policy-classification.md) für Ihre Bezeichnungen konfigurieren, die für mehrere Bezeichnungen gelten, müssen Sie diese Anordnung für Ihre Bezeichnungen wählen (niedrigste bis höchste Vertraulichkeitsstufe). Mit dieser Anordnung wird sichergestellt, dass bei der Auswertung der Bedingungen die Bezeichnung mit der höchsten Vertraulichkeitsstufe angewendet wird.


Verwenden Sie die folgenden Anleitungen, um diese Änderungen vorzunehmen.

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die Bezeichnung, die Sie löschen, deaktivieren oder umstrukturieren möchten, für alle Benutzer gilt, führen Sie einen der folgenden Schritte auf dem Blatt **Policy: Global** (Richtlinie: Global) aus. 

    - So löschen Sie eine Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, die gelöscht werden soll, klicken Sie auf **Delete this label** (Diese Bezeichnung löschen), und klicken Sie auf **Yes** (Ja), um den Vorgang zu bestätigen. Klicken Sie dann auf **Save** (Speichern). 

    - So deaktivieren Sie eine Bezeichnung: Wählen Sie die Bezeichnung aus, die Sie deaktivieren möchten. Klicken Sie auf dem Blatt **Label** (Bezeichnung) für **Enabled** (Aktiviert) auf **Off** (Aus), und klicken Sie dann auf **Save** (Speichern).

    - So ändern Sie die Position einer Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, deren Position Sie ändern möchten, und klicken Sie auf **Move up** (Nach oben) oder **Move down** (Nach unten), bis sich die Bezeichnung an der gewünschten Position befindet. Klicken Sie dann auf **Save** (Speichern). 

     Wenn sich die Bezeichnung, die Sie löschen, deaktivieren oder umstrukturieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie zunächst die bereichsbezogene Richtlinie auf dem ersten Blatt **Azure Information Protection** aus.

3. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

