---
title: Ändern einer Azure Information Protection-Bezeichnung – AIP
description: Sie können die auf der Information Protection-Leiste angezeigten Bezeichnungen ändern, indem Sie diese in der Azure Information Protection-Richtlinie konfigurieren.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e3b6d95f-334b-4d17-80a9-7d5487ab5d32
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 35952412712573ec1134393b1679ca65dd39809e
ms.sourcegitcommit: 8c39347d9b7a120014120860fff89c5616641933
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "79482418"
---
# <a name="how-to-change-or-customize-an-existing-label-for-azure-information-protection"></a>Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Sie können die Bezeichnungen, die Benutzern in der Information Protection-Leiste oder über die Schaltfläche **Schützen** im Office-Menüband angezeigt werden, ändern oder verfeinern, indem Sie diese im Azure-Portal konfigurieren.

Beispielsweise können Sie den Namen einer Bezeichnung oder einer untergeordneten Bezeichnung, eine QuickInfo, eine Farbe oder eine Reihenfolge ändern. Sie können einstellen, dass eine Bezeichnung optische Kennzeichnungen wie Fußzeilen oder Wasserzeichen anwendet. Außerdem können Sie einstellen, dass die Bezeichnung einen Schutz oder eine empfohlene bzw. eine automatische Klassifizierung anwendet.

Verwenden Sie die folgenden Anweisungen, um eine Bezeichnung zu ändern:

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die Bezeichnung aus, die Sie ändern möchten.

    Eine Ausnahme besteht darin, wenn Sie eine Bezeichnung neu anordnen möchten: Statt die Bezeichnung auszuwählen, müssen Sie in diesem Fall mit der rechten Maustaste auf die Bezeichnung klicken oder das Kontextmenü der Bezeichnung aufrufen. Klicken Sie dann entweder auf die Option **Move up** (Nach oben) oder auf die Option **Move down** (Nach unten).

3. Wenn Sie Änderungen in einem neuen Bereich vornehmen, klicken Sie in diesem Bereich auf **Speichern** , wenn Sie die Änderungen beibehalten möchten.
    
    Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

4. Gehen Sie wie folgt vor, wenn Sie den Anzeigenamen für Bezeichnung oder die Beschreibung geändert und für weitere Sprachen konfiguriert haben: Exportieren Sie Ihre Azure Information Protection-Richtlinie erneut, stellen Sie neue Übersetzungen bereit, und importieren Sie die Änderungen. Weitere Informationen finden Sie unter [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md).

> [!TIP]
>Informationen zum Wiederherstellen der Standardwerte einer Standardbezeichnung finden Sie unter [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md).

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).



