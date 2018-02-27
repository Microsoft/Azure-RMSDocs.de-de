---
title: "Konfigurieren bereichsbezogener Richtlinien für Azure Information Protection"
description: "Um andere Einstellungen und Bezeichnungen für bestimmte Benutzer zu konfigurieren, müssen Sie eine bereichsbezogene Richtlinie für Azure Information Protection konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 081766a70c6d142e3016797708e347d2b9bc2204
ms.sourcegitcommit: 67750454f8fa86d12772a0075a1d01a69f167bcb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien

>*Gilt für: Azure Information Protection*

Beim die Azure Information Protection-Richtlinie auf Computer heruntergeladen wird, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist, erhalten alle Benutzer die Einstellungen und Bezeichnungen der Standardrichtlinie oder die Änderungen, die Sie für die globale Richtlinie konfiguriert haben. Wenn Sie dies für bestimmte Benutzer ergänzen möchten, indem Sie verschiedene Einstellungen und Bezeichnungen verwenden, müssen Sie eine **bereichsbezogene Richtlinie** erstellen, die für diese Benutzer konfiguriert ist.

Alle Benutzer erhalten die globale Richtlinie, die Titel und QuickInfo sowie globale Einstellungen und globale Bezeichnungen der Information Protection-Leiste enthält. Wenn Sie bereichsbezogene Richtlinien für bestimmte Benutzer konfiguriert haben, erhalten diese Benutzer diese zusätzlichen Einstellungen und Bezeichnungen. 

Bereichsbezogene Richtlinien sind wie Bezeichnungen im Azure-Portal angeordnet. Wenn ein Benutzer für mehrere Bereiche konfiguriert ist, wird eine effektive Richtlinie für den Benutzer berechnet, bevor sie heruntergeladen wird. Gemäß der Reihenfolge der Richtlinien wird die letzte Einstellung angewendet. Die Bezeichnungen, die dem Benutzer angezeigt werden, stammen aus der globalen Richtlinie und allen zusätzlichen Bezeichnungen aus bereichsbezogenen Richtlinien, denen der Benutzer angehört. 

Da eine bereichsbezogene Richtlinie immer die Bezeichnungen und Einstellungen der globalen Richtlinie erbt, werden die Bezeichnungen der globalen Richtlinie angezeigt, wenn Sie eine bereichsbezogene Richtlinie erstellen oder bearbeiten. Sie können jedoch nicht die Bezeichnungen der globalen Richtlinie bearbeiten, wenn Sie eine bereichsbezogene Richtlinie bearbeiten. Sie können diesen geerbten Bezeichnungen jedoch untergeordnete Bezeichnungen hinzufügen.

Wenn Sie z.B. in der globalen Richtlinie über eine Bezeichnung namens **Vertraulich** verfügen, wird diese Bezeichnung allen Benutzern angezeigt. Sie können sie nicht über eine bereichsbezogenen Richtlinie entfernen oder neu anordnen. Aber Sie sollten eine bereichsbezogene Richtlinie für die Marketingabteilung erstellen, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Confidential/Promotions** (Vertraulich/Aktionen) angezeigt wird. Sie erstellen zudem eine weitere bereichsbezogene Richtlinie für die Vertriebsabteilung, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Confidential/Partners** (Vertraulich/Partner) angezeigt wird. Jede untergeordnete Bezeichnung kann dann für unterschiedliche Einstellungen konfiguriert werden, und die untergeordnete Bezeichnung wird nur den entsprechenden Benutzern in der Abteilung angezeigt.

So konfigurieren Sie eine bereichsbezogene Richtlinie für Azure Information Protection

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.

    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**.

3. Klicken Sie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien) auf **Neue Richtlinie hinzufügen**. Ihnen wird dann das Blatt **Richtlinie** angezeigt, das Ihre bestehende globale Richtlinie anzeigt. Dort können Sie nun Ihre neue bereichsbezogene Richtlinie konfigurieren.

4. Geben Sie einen Richtliniennamen und eine Beschreibung an, die nur für Administratoren im Azure-Portal angezeigt wird. Der Name muss für Ihren Mandanten eindeutig sein. Klicken Sie dann auf **Specify which users/groups get this policy** (Benutzer/Gruppen angeben, die diese Richtlinie erhalten). Auf den nachfolgenden Blättern können Sie dann die Benutzer und Gruppen für diese Richtlinie suchen und auswählen. Die Bezeichnungen und Einstellungen, die Sie in dieser bereichsbezogenen Richtlinie konfigurieren, werden nur auf diese Benutzer angewendet.
    
    Aus Leistungsgründen wird die Gruppenmitgliedschaft für bereichsbezogene Richtlinien [zwischengespeichert](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection).

5. Erstellen Sie jetzt neue Bezeichnungen, oder konfigurieren Sie die bereichsbezogenen Richtlinieneinstellungen. Die globale Richtlinie wird immer zuerst angewendet, so können Sie die globale Richtlinie mit neuen Bezeichnungen ergänzen, und Sie können die globalen Einstellungen außer Kraft setzen. Die globale Richtlinie verfügt möglicherweise über keine Standardbezeichnung, und Sie konfigurieren eine andere Standardbezeichnung in verschiedenen bereichsbezogenen Richtlinien für bestimmte Abteilungen.

    Wenn Sie beim Konfigurieren der Bezeichnungen oder Einstellungen Hilfe benötigen, verwenden Sie die Links im Abschnitt [Konfigurieren der Richtlinien Ihrer Organisation](configure-policy.md#configuring-your-organizations-policy).

6. Wenn Sie wie beim Bearbeiten der globalen Richtlinie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

7. Wenn Sie die Änderungen für diese bereichsbezogene Richtlinie abgeschlossen haben, stellen Sie auf dem ersten Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien) sicher, dass diese bereichsbezogene Richtlinie gemäß Ihren Vorstellungen angeordnet ist. Dies ist wichtig, wenn Sie denselben Benutzer für mehrere bereichsbezogene Richtlinien ausgewählt haben. Klicken Sie zum Ändern der Reihenfolge auf das Kontextmenü (**...**), und klicken Sie auf **Nach oben** oder **Nach unten**. 

8. Klicken Sie zum Bereitstellen Ihrer Änderungen auf **Veröffentlichen**. 

Beim Start einer unterstützten Office-Anwendung oder Öffnen des Datei-Explorers prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Der Client lädt dann alle Änderungen an der globalen Richtlinie oder bereichsbezogenen Richtlinie herunter, die für diesen Benutzer gelten.

> [!TIP]
> Nachdem Sie Ihre bereichsbezogene Richtlinie gespeichert haben, können Sie im Abschnitt **RICHTLINIEN** die Option **Alle – richtlinienübergreifende Ansicht** verwenden, um alle Bezeichnungen Ihrer Azure Information Protection-Richtlinie anzuzeigen und neu zu konfigurieren. Diese Methode bietet eine einfache Möglichkeit, Bezeichnungen aus Ihrer globalen Richtlinie und allen bereichsbezogenen Richtlinien zu vergleichen. 

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
