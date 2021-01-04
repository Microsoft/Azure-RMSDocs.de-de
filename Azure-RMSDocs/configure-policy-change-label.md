---
title: Ändern einer Azure Information Protection-Bezeichnung – AIP
description: Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern oder anpassen, indem Sie sie in der Azure Information Protection-Richtlinie konfigurieren.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/16/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ROBOTS: NOINDEX
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 4f8a58ccb9d237a5a3d784a9f92c57e07b6ac21f
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97806804"
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Sensitivitäts Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Sie können die Bezeichnungen, die Benutzern in der Information Protection-Leiste oder über die Schaltfläche **Schützen** im Office-Menüband angezeigt werden, ändern oder verfeinern, indem Sie diese im Azure-Portal konfigurieren.

Sie können beispielsweise den Namen, die QuickInfo, die Farbe und die Reihenfolge von Bezeichnungen oder untergeordneten Bezeichnungen ändern. Sie können festlegen, ob die Bezeichnung visuelle Kennzeichnungen wie Fußzeilen oder Wasserzeichen anwendet. Außerdem können Sie angeben, ob Schutz und die empfohlene oder die automatische Klassifizierung angewendet werden.

In den folgenden Anweisungen wird erläutert, wie Sie eine Bezeichnung ändern:

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die Bezeichnung aus, die Sie ändern möchten.

    Eine Ausnahme besteht darin, wenn Sie eine Bezeichnung neu anordnen möchten: Statt die Bezeichnung auszuwählen, müssen Sie in diesem Fall mit der rechten Maustaste auf die Bezeichnung klicken oder das Kontextmenü der Bezeichnung aufrufen. Wählen Sie dann die Option **Nach oben** oder **Nach unten**.

3. Wenn Sie Änderungen in einem neuen Bereich vornehmen, klicken Sie in diesem Bereich auf **Speichern** , wenn Sie die Änderungen beibehalten möchten.
    
    Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

4. Wenn Sie den Anzeigenamen oder die Beschreibung der Bezeichnung geändert und für weitere Sprachen konfiguriert haben, müssen Sie Ihre Azure Information Protection-Richtlinie erneut exportieren, neue Übersetzungen bereitstellen und die Änderungen importieren. Weitere Informationen finden Sie unter [Vorgehensweise beim Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection](configure-policy-languages.md).

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).



