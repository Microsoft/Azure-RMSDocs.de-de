---
title: Ändern einer Azure Information Protection-Bezeichnung – AIP
description: Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.openlocfilehash: 5f844ae0ad8e159dc7544fc844ccb22d5e95f7b0
ms.sourcegitcommit: 7992e1dc791d6d919036f7aa98bcdd21a6c32ad0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68428481"
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Sie können die Bezeichnungen, die Benutzern in der Information Protection-Leiste oder über die Schaltfläche **Schützen** im Office-Menüband angezeigt werden, ändern oder verfeinern, indem Sie diese im Azure-Portal konfigurieren.

Beispielsweise können Sie den Namen einer Bezeichnung oder einer untergeordneten Bezeichnung, eine QuickInfo, eine Farbe oder eine Reihenfolge ändern. Sie können einstellen, dass eine Bezeichnung optische Kennzeichnungen wie Fußzeilen oder Wasserzeichen anwendet. Außerdem können Sie einstellen, dass die Bezeichnung einen Schutz oder eine empfohlene bzw. eine automatische Klassifizierung anwendet.

Verwenden Sie die folgenden Anweisungen, um eine Bezeichnung zu ändern:

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die Bezeichnung aus, die Sie ändern möchten.

    Eine Ausnahme ist gegeben, wenn Sie eine Bezeichnung neu sortieren möchten: Anstatt die Bezeichnung auszuwählen, klicken Sie mit der rechten Maustaste auf die Bezeichnung, oder rufen Sie das Kontextmenü der Bezeichnung auf. Klicken Sie dann entweder auf die Option **Move up** (Nach oben) oder auf die Option **Move down** (Nach unten).

3. Wenn Sie Ihre Änderungen auf einem neuen Blatt übernehmen möchten, klicken Sie auf dem jeweiligen Blatt auf **Speichern**.
    
    Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

4. Wenn Sie den Anzeigenamen der Bezeichnung oder Beschreibung geändert und diese für weitere Sprachen konfiguriert haben: Exportieren Sie Ihre Azure Information Protection-Richtlinie erneut, stellen Sie neue Übersetzungen bereit, und importieren Sie die Änderungen. Weitere Informationen finden Sie unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md).

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).



