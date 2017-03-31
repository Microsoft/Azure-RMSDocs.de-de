---
title: "Konfigurieren bereichsbezogener Richtlinien für Azure Information Protection"
description: "Um andere Einstellungen und Bezeichnungen für bestimmte Benutzer zu konfigurieren, müssen Sie eine bereichsbezogene Richtlinie für Azure Information Protection konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/28/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 2fc0059f0cc2d7c1a0eb08d6f8ee89ea2bf4bfbd
ms.sourcegitcommit: 16fec44713c7064959ebb520b9f0857744fecce9
translationtype: HT
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien

>*Gilt für: Azure Information Protection*

Beim die Azure Information Protection-Richtlinie auf Computer heruntergeladen wird, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist, erhalten alle Benutzer die Einstellungen und Bezeichnungen der Standardrichtlinie oder die Änderungen, die Sie für die globale Richtlinie konfiguriert haben. Wenn Sie dies für bestimmte Benutzer ergänzen möchten, indem Sie verschiedene Einstellungen und Bezeichnungen verwenden, müssen Sie eine **bereichsbezogene Richtlinie** erstellen, die für diese Benutzer konfiguriert ist.

Alle Benutzer erhalten die globale Richtlinie, die Titel und QuickInfo sowie globale Einstellungen und globale Bezeichnungen der Information Protection-Leiste enthält. Wenn Sie bereichsbezogene Richtlinien für bestimmte Benutzer konfiguriert haben, erhalten diese Benutzer diese zusätzlichen Einstellungen und Bezeichnungen. 

Bereichsbezogene Richtlinien sind wie Bezeichnungen im Azure-Portal angeordnet. Wenn ein Benutzer für mehrere Bereiche konfiguriert ist, wird eine effektive Richtlinie für den Benutzer berechnet, bevor sie heruntergeladen wird. Gemäß der Reihenfolge der Richtlinien wird die letzte Einstellung angewendet. Die Bezeichnungen, die dem Benutzer angezeigt werden, stammen aus der globalen Richtlinie und allen zusätzlichen Bezeichnungen aus bereichsbezogenen Richtlinien, denen der Benutzer angehört. 

Da eine bereichsbezogene Richtlinie immer die Bezeichnungen und Einstellungen der globalen Richtlinie erbt, werden die Bezeichnungen der globalen Richtlinie angezeigt, wenn Sie eine bereichsbezogene Richtlinie erstellen oder bearbeiten. Sie können jedoch nicht die Bezeichnungen der globalen Richtlinie bearbeiten, wenn Sie eine bereichsbezogene Richtlinie bearbeiten. Sie können diesen geerbten Bezeichnungen jedoch untergeordnete Bezeichnungen hinzufügen.

Wenn Sie z.B. in der globalen Richtlinie über eine Bezeichnung namens **Vertraulich** verfügen, wird diese Bezeichnung allen Benutzern angezeigt. Sie können sie nicht mit einer bereichsbezogenen Richtlinie entfernen oder neu anordnen. Aber möglicherweise möchten Sie eine bereichsbezogene Richtlinie für die Marketing-Abteilung erstellen, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Vertraulich\Aktionen** angezeigt wird. Sie erstellen zudem eine weitere bereichsbezogene Richtlinie für die Vertriebsabteilung, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Vertraulich\Partner** angezeigt wird. Jede untergeordnete Bezeichnung kann dann für unterschiedliche Einstellungen konfiguriert werden, und die untergeordnete Bezeichnung wird nur den entsprechenden Benutzern in der Abteilung angezeigt.


So konfigurieren Sie eine bereichsbezogene Richtlinie für Azure Information Protection

1. Melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Weitere Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 

    Auf dem ersten **Azure Information Protection**-Blatt wählen Sie **Add a new policy** (Neue Richtlinie hinzufügen) aus. Dann wird das zweite Blatt angezeigt, das normalerweise die Aktualisierung der globalen Richtlinie anzeigt, sodass Sie jetzt Ihre neue bereichsbezogene Richtlinie konfigurieren können.

3. Geben Sie einen Richtliniennamen und eine Beschreibung an, die nur für Administratoren im Azure-Portal angezeigt wird. Der Name muss für Ihren Mandanten eindeutig sein. Klicken Sie dann auf **Specify which users/groups get this policy** (Benutzer/Gruppen angeben, die diese Richtlinie erhalten). Auf den nachfolgenden Blättern können Sie dann die Benutzer und Gruppen für diese Richtlinie suchen und auswählen. Die Bezeichnungen und Einstellungen, die Sie in dieser bereichsbezogenen Richtlinie konfigurieren, werden nur auf diese Benutzer angewendet.

4. Erstellen Sie jetzt neue Bezeichnungen, oder konfigurieren Sie die bereichsbezogenen Richtlinieneinstellungen. Die globale Richtlinie wird immer zuerst angewendet, so können Sie die globale Richtlinie mit neuen Bezeichnungen ergänzen, und Sie können die globalen Einstellungen außer Kraft setzen. Die globale Richtlinie verfügt möglicherweise über keine Standardbezeichnung, und Sie konfigurieren eine andere Standardbezeichnung in verschiedenen bereichsbezogenen Richtlinien für bestimmte Abteilungen.

    Wenn Sie beim Konfigurieren der Bezeichnungen oder Einstellungen Hilfe benötigen, verwenden Sie die Links im Abschnitt [Konfigurieren der Richtlinien Ihrer Organisation](configure-policy.md#configuring-your-organizations-policy).

5. Wenn Sie wie beim Bearbeiten der globalen Richtlinie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

6. Wenn Sie die Änderungen für diese bereichsbezogene Richtlinie abgeschlossen haben, stellen Sie auf dem ersten Blatt **Azure Informationsschutz** sicher, dass diese bereichsbezogene Richtlinie gemäß Ihren Vorstellungen angeordnet ist. Dies ist wichtig, wenn Sie denselben Benutzer für mehrere bereichsbezogene Richtlinien ausgewählt haben. Klicken Sie dann auf **Publish** (Veröffentlichen). 

Beim Start einer unterstützten Office-Anwendung oder Öffnen des Datei-Explorers prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Der Client lädt dann alle Änderungen an der globalen Richtlinie oder bereichsbezogenen Richtlinie herunter, die für diesen Benutzer gelten.

> [!TIP]
> Nachdem Sie Ihre bereichsbezogene Richtlinie gespeichert haben, können Sie den **richtlinienübergreifenden Editor** auf dem anfänglichen Blatt **Azure Information Protection** verwenden, um alle Bezeichnungen Ihrer Azure Information Protection-Richtlinie anzuzeigen und neu zu konfigurieren. Diese Methode bietet eine einfache Möglichkeit, Bezeichnungen aus mehreren Richtlinien (Ihrer globalen Richtlinie und allen bereichsbezogenen Richtlinien) zu vergleichen. In diesem Editor können Sie jedoch keine Bezeichnungen hinzufügen oder neu anordnen oder die Richtlinieneinstellungen anzeigen oder konfigurieren.

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
