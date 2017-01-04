---
title: "Gewusst wie: Ändern oder Anpassen einer vorhandenen Bezeichnung | Azure Information Protection"
description: "Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
translationtype: Human Translation
ms.sourcegitcommit: 4fcfcebc7da5a22a91911d70d4d787dc525d3485
ms.openlocfilehash: f7b5e9e0bb32e4a04dfb407f11e361d959ebb807


---

# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren.

Sie können z. B. folgende Merkmale einer Bezeichnung oder einer untergeordneten Bezeichnung ändern: den Namen, die QuickInfo, die Farbe und die Reihenfolge. Außerdem können festlegen, ob visuelle Kennzeichnungen wie Fußzeilen oder Wasserzeichen, der Azure Rights Management-Schutz und die empfohlene oder die automatische Klassifizierung angewendet werden.

Verwenden Sie die folgenden Anleitungen, um eine Bezeichnung zu ändern.


1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Um eine Bezeichnung der globalen Richtlinie zu ändern, damit sie für alle Benutzer gilt, wählen Sie die zu ändernde Bezeichnung auf dem Blatt **Policy:Global** (Richtlinie: Global) aus und nehmen dann Ihre Änderungen bei Bedarf am Blatt **Label** (Bezeichnung) und allen nachfolgenden Blättern vor. Um eine Bezeichnung von einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) zu ändern, damit sie für ausgewählte Benutzer gilt, wählen Sie zunächst diese Richtlinie auf dem Blatt **Azure Information Protection** aus.

    Ausnahme: Wenn Sie die Position einer Bezeichnung ändern möchten, was Sie auf dem Richtlinienblatt der globalen Richtlinie oder der bereichsbezogenen Richtlinie ausführen: Klicken Sie entweder mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü für die Bezeichnung auf, und wählen Sie dann **Move up** (Nach oben) oder **Move down** (Nach unten).

3. Wenn Sie Ihre Änderungen auf einem Blatt übernehmen möchten, klicken Sie auf dem jeweiligen Blatt auf **Save** (Speichern).

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).






<!--HONumber=Dec16_HO1-->


