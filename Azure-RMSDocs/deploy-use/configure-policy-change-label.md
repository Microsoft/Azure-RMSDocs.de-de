---
title: "Ändern einer Azure Information Protection-Bezeichnung"
description: "Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: 343b38caa14d3f67a932eedae37ed10c55f371ff
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2017
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren.

Sie können z. B. folgende Merkmale einer Bezeichnung oder einer untergeordneten Bezeichnung ändern: den Namen, die QuickInfo, die Farbe und die Reihenfolge. Außerdem können festlegen, ob visuelle Kennzeichnungen wie Fußzeilen oder Wasserzeichen, der Azure Rights Management-Schutz und die empfohlene oder die automatische Klassifizierung angewendet werden.

Verwenden Sie die folgenden Anleitungen, um eine Bezeichnung zu ändern.

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Um eine Bezeichnung der globalen Richtlinie zu ändern, damit sie für alle Benutzer gilt, wählen Sie die zu ändernde Bezeichnung auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) und bei Bedarf auf allen nachfolgenden Blättern aus. Zum Ändern eines Bezeichners, der sich in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass diese nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** zunächst auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

    Ausnahme: Wenn Sie die Position einer Bezeichnung ändern möchten, was Sie auf dem Richtlinienblatt der globalen Richtlinie oder der bereichsbezogenen Richtlinie ausführen: Klicken Sie entweder mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü für die Bezeichnung auf, und wählen Sie dann **Move up** (Nach oben) oder **Move down** (Nach unten).

3. Wenn Sie Ihre Änderungen auf einem Blatt übernehmen möchten, klicken Sie auf dem jeweiligen Blatt auf **Save** (Speichern).

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

5. Wenn Sie den Bezeichnungsnamen oder die Beschreibung geändert und für weitere Sprachen konfiguriert haben, müssen Sie Ihre Azure Information Protection-Richtlinie erneut exportieren, neue Übersetzungen bereitstellen und die Änderungen importieren. Weitere Informationen finden Sie unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md).

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


