---
title: "Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ae0f603f-a632-4ac5-a3f7-6358d4255eff
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 50a60f8a0f8cb92aba7453e6c1dedacbe004a5ed


---

# Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen löschen oder deren Position ändern, indem Sie diese Einstellungen in der Azure Information Protection-Richtlinie konfigurieren.

![Löschen oder Ändern der Position von Bezeichnungen in der Azure Information Protection-Richtlinie](../media/info-protect-contextmenu.png)

Anstatt eine Bezeichnung zu löschen, können Sie sie auch deaktivieren. Dadurch wird die Konfiguration der Bezeichnung beibehalten, die Bezeichnung wird jedoch nicht in der Information Protection-Leiste angezeigt.

Ordnen Sie die Bezeichnungen so an, dass Sie auf der Information Protection-Leiste in einer logischen Reihenfolge für die Benutzer angezeigt werden. Ordnen Sie die Bezeichnungen z. B. nach steigender Vertraulichkeitsstufe an, sodass den Benutzern zuerst die niedrigste Vertraulichkeitsstufe und zuletzt die höchste Vertraulichkeitsstufe angezeigt wird. Diese Konfiguration wird in der [Standardrichtlinie](configure-policy-default.md) verwendet.

> [!IMPORTANT]
>Wenn Sie [Bedingungen](configure-policy-classification.md) für Ihre Bezeichnungen konfigurieren, die für mehrere Bezeichnungen gelten, müssen Sie diese Anordnung für Ihre Bezeichnungen wählen (niedrigste bis höchste Vertraulichkeitsstufe). Mit dieser Anordnung wird sichergestellt, dass bei der Auswertung der Bedingungen die Bezeichnung mit der höchsten Vertraulichkeitsstufe angewendet wird.


Verwenden Sie die folgenden Anleitungen, um diese Änderungen vorzunehmen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Klicken Sie anschließend im Hubmenü auf **Durchsuchen**, und geben Sie **Information** im Filterfeld ein. Wählen Sie **Azure Information Protection** aus.

3. Führen Sie auf dem Blatt **Azure Information Protection** eine der folgenden Aktionen aus (abhängig davon, ob Sie eine Bezeichnung löschen, deaktivieren oder neu anordnen möchten):

    - So löschen Sie eine Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, die gelöscht werden soll, klicken Sie auf **Delete this label** (Diese Bezeichnung löschen), und klicken Sie auf **Yes** (Ja), um den Vorgang zu bestätigen. Klicken Sie dann auf **Save** (Speichern). 

    - So deaktivieren Sie eine Bezeichnung: Wählen Sie die Bezeichnung aus, die Sie deaktivieren möchten. Klicken Sie auf dem Blatt **Label** (Bezeichnung) für **Enabled** (Aktiviert) auf **Off** (Aus), und klicken Sie dann auf **Save** (Speichern).

    - So ändern Sie die Position einer Bezeichnung: Klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü (**...**) für die Bezeichnung auf, deren Position Sie ändern möchten, und klicken Sie auf **Move up** (Nach oben) oder **Move down** (Nach unten), bis sich die Bezeichnung an der gewünschten Position befindet. Klicken Sie dann auf **Save** (Speichern). 

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Jul16_HO5-->


