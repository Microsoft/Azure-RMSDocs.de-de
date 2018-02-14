---
title: "Ändern einer Azure Information Protection-Bezeichnung"
description: "Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern oder anpassen, indem Sie sie in der Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: f1ffd4c459f2fa194372450f5713c920422f744d
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern oder anpassen, indem Sie sie in der Azure Information Protection-Richtlinie konfigurieren.

Sie können beispielsweise den Namen, die QuickInfo, die Farbe und die Reihenfolge von Bezeichnungen oder untergeordneten Bezeichnungen ändern. Sie können festlegen, ob die Bezeichnung visuelle Kennzeichnungen wie Fußzeilen oder Wasserzeichen anwendet. Außerdem können Sie angeben, ob Schutz und die empfohlene oder die automatische Klassifizierung angewendet werden.

In den folgenden Anweisungen wird erläutert, wie Sie eine Bezeichnung ändern:

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie beispielsweise im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Um eine Bezeichnung der globalen Richtlinie so zu ändern, dass sie für alle Benutzer gilt, wählen Sie die zu ändernde Bezeichnung auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinie) und bei Bedarf auf allen nachfolgenden Blättern aus. Wenn Sie eine Bezeichnung einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) ändern möchten, sodass diese nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** zunächst auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien) aus.

    Ausnahme: Sie möchten die Position einer Bezeichnung ändern. Auf dem Blatt „Richtlinie“ der globalen Richtlinie oder der ausgewählten bereichsbezogenen Richtlinie: Klicken Sie entweder mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü für die Bezeichnung auf. Wählen Sie dann die Option **Nach oben** oder **Nach unten**.

3. Wenn Sie Ihre Änderungen auf einem Blatt übernehmen möchten, klicken Sie auf dem jeweiligen Blatt auf **Speichern**.

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Veröffentlichen**, um Ihre Änderungen für Benutzer verfügbar zu machen.

5. Wenn Sie den Anzeigenamen oder die Beschreibung der Bezeichnung geändert und für weitere Sprachen konfiguriert haben, müssen Sie Ihre Azure Information Protection-Richtlinie erneut exportieren, neue Übersetzungen bereitstellen und die Änderungen importieren. Weitere Informationen finden Sie unter [Vorgehensweise beim Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection](configure-policy-languages.md).

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


