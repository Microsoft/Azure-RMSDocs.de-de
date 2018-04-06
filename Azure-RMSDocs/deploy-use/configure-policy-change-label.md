---
title: Ändern einer Azure Information Protection-Bezeichnung
description: Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: aac1d87fb76848e31a21a046f14442293d29aa9f
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren.

Beispielsweise können Sie den Namen einer Bezeichnung oder einer untergeordneten Bezeichnung, eine QuickInfo, eine Farbe oder eine Reihenfolge ändern. Sie können einstellen, dass eine Bezeichnung optische Kennzeichnungen wie Fußzeilen oder Wasserzeichen anwendet. Außerdem können Sie einstellen, dass die Bezeichnung einen Schutz oder eine empfohlene bzw. eine automatische Klassifizierung anwendet.

Verwenden Sie die folgenden Anweisungen, um eine Bezeichnung zu ändern:

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Um eine Bezeichnung der globalen Richtlinie zu ändern, damit sie für alle Benutzer gilt, wählen Sie die zu ändernde Bezeichnung auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) und bei Bedarf auf allen nachfolgenden Blättern aus. Zum Ändern eines Bezeichners, der sich in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass diese nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** zunächst auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

    Eine Ausnahme besteht, wenn Sie eine Bezeichnung neu sortieren möchten. Führen Sie im Richtlinienbereich der globalen oder einer ausgewählten bereichsbezogenen Richtlinie folgende Vorgänge durch: Klicken Sie entweder mit der rechten Maustaste auf die Bezeichnung, oder klicken Sie auf das Kontextmenü der Bezeichnung. Klicken Sie dann entweder auf die Option **Move up** (Nach oben) oder auf die Option **Move down** (Nach unten).

3. Wenn Sie Ihre Änderungen auf einem Blatt übernehmen möchten, klicken Sie auf dem jeweiligen Blatt auf **Save** (Speichern).

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

5. Gehen Sie wie folgt vor, wenn Sie den Anzeigenamen für Bezeichnung oder die Beschreibung geändert und für weitere Sprachen konfiguriert haben: Exportieren Sie Ihre Azure Information Protection-Richtlinie erneut, stellen Sie neue Übersetzungen bereit, und importieren Sie die Änderungen. Weitere Informationen finden Sie unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md).

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


