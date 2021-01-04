---
title: Neue Azure Information Protection-Bezeichnung – AIP
description: Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen, die Benutzern auf der Information Protection-Leiste angezeigt werden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/16/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 1b45faa5-0c9c-40d6-910a-f117e7b6e8a3
ROBOTS: NOINDEX
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 0a191dbdba3ceb2408757284847e4565d9338950
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97806582"
---
# <a name="how-to-create-a-new-label-for-azure-information-protection"></a>Erstellen einer neuen Bezeichnung für Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Sensitivitäts Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenngleich Azure Information Protection anpassbare Standardbezeichnungen umfasst, können Sie auch eigene Bezeichnungen erstellen.

Sie können eine neue Bezeichnung hinzufügen oder einer vorhandenen Bezeichnung eine neue untergeordnete Bezeichnung hinzufügen, wenn eine weitere Klassifizierungsebene erforderlich ist. Die letzte Bezeichnung in der [Standardrichtlinie](configure-policy-default.md) enthält z.B. untergeordnete Bezeichnungen.

Wenn Sie die erste untergeordnete Bezeichnung für eine Bezeichnung erstellen, können Benutzer nicht länger die ursprüngliche Bezeichnung, also die übergeordnete Bezeichnung, auswählen. Erstellen Sie falls nötig eine neue untergeordnete Bezeichnung, um die Einstellungen der übergeordneten Bezeichnung neu zu erstellen, sodass Benutzer die gleichen Einstellungen anwenden können.

Fügen Sie mithilfe der folgenden Anweisungen eine neue Bezeichnung hinzu, die zur Azure Information Protection-Richtlinie hinzugefügt werden kann.

## <a name="to-create-a-new-label"></a>So erstellen Sie eine neue Bezeichnung

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : führen Sie im Bereich **Azure Information Protection-Bezeichnungen** eine der folgenden Aktionen aus:
    
    - So erstellen Sie eine neue Bezeichnung: Klicken Sie auf **Add a new label** (Neue Bezeichnung hinzufügen).
    
    - So erstellen Sie eine neue untergeordnete Bezeichnung: Klicken Sie mit der rechten Maustaste, oder wählen Sie das Kontextmenü (**...**) für die Bezeichnung aus, für die Sie eine untergeordnete Bezeichnung erstellen möchten, und klicken Sie dann auf **untergeordnete Bezeichnung hinzufügen**.

3. Wählen Sie im Bereich **Bezeichnung** oder **untergeordnete Bezeichnung** die gewünschten Optionen für diese neue Bezeichnung aus, und klicken Sie dann auf **Speichern**.
    
    Wenn Sie einen Anzeigenamen angeben, dürfen Sie einige Zeichen nicht verwenden (z.B. den umgekehrten Schrägstrich und das kaufmännische Und-Zeichen), da diese Zeichen nicht von allen Diensten und Anwendungen unterstützt werden, die Azure Information Protection nutzen. Geben Sie zusätzlich zu den blockierten Zeichen nicht das **#** Zeichen an.    
    
    Beachten Sie, dass neuen Bezeichnungen automatisch die Farbe Schwarz zugewiesen wird. Wählen Sie eine eindeutige Farbe aus der Liste der Farben aus, oder geben Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe ein. Beispiel: **#DAA520**. Wenn Sie einen Verweis auf diese Codes benötigen, finden Sie eine hilfreiche Tabelle auf der [\<color>](https://developer.mozilla.org/docs/Web/CSS/color_value) Seite der MSDN-Webdokumentation. Außerdem finden Sie diese Codes in vielen Anwendungen, mit denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

4. So machen Sie die neue Bezeichnung Benutzern verfügbar: Wählen Sie in der Menüoption **Klassifizierungen**  >  **Richtlinien** die Richtlinie aus, die die neue Bezeichnung enthalten soll. Wählen Sie **Bezeichnungen hinzufügen oder entfernen** aus. Wählen Sie die Bezeichnung im Bereich **Richtlinie: Bezeichnungen hinzufügen oder entfernen** aus, klicken Sie auf **OK**, und wählen Sie dann **Speichern** aus.
    
    >[!TIP]
    >Bei neuen Bezeichnungen sollten Sie in Erwägung ziehen, diese zuerst zu einer bereichsbezogenen Richtlinie hinzuzufügen, die Sie zu Testzwecken verwenden. Wenn Sie mit den Ergebnissen zufrieden sind, können Sie die Bezeichnung aus diesem Testbereich entfernen und sie anschließend zu einer Richtlinie hinzufügen, die Sie zu Produktionszwecken verwenden.     
    
    Weitere Informationen zum Hinzufügen von Bezeichnungen finden Sie unter [Hinzufügen oder Entfernen einer Bezeichnung](configure-policy-add-remove-label.md).
    
    Ihre vorgenommenen Änderungen sind automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

5. Wenn Sie diesen neuen Bezeichnungsnamen und eine Beschreibung in verschiedenen Sprachen anzeigen möchten, führen Sie die Verfahren unter [Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md) aus. 

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  


