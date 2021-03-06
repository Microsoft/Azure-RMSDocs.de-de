---
title: Konfigurieren bereichsbezogener Richtlinien für Azure Information Protection – AIP
description: Wenn Sie verschiedene Einstellungen und Bezeichnungen für bestimmte Benutzer konfigurieren möchten, müssen Sie eine bereichsbezogene Richtlinie für Azure Information Protection konfigurieren.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/17/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ROBOTS: NOINDEX
ms.subservice: aiplabels
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: b815109ddaa62c48a5034d3277b807495d0a7a97
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97806616"
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Sensitivitäts Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Beim Herunterladen der Azure Information Protection-Richtlinie auf Computer, auf denen der Azure Information Protection-Client installiert ist, erhalten alle Benutzer die Einstellungen und Bezeichnungen der Standardrichtlinie oder die Änderungen, die Sie für die globale Richtlinie konfiguriert haben. Wenn Sie diese Konfiguration für bestimmte Benutzer ergänzen möchten, indem Sie verschiedene Einstellungen und Bezeichnungen haben, müssen Sie eine Bereichs bezogene **Richtlinie** erstellen, die für diese Benutzer konfiguriert ist.

## <a name="how-scoped-policies-work"></a>Funktionsweise von Bereichs bezogenen Richtlinien

Für Anwendungen, die den Azure Information Protection-Client verwenden erhalten alle Benutzer die globale Richtlinie, die Titel und QuickInfo sowie globale Einstellungen und globale Bezeichnungen der Information Protection-Leiste enthält. Wenn Sie bereichsbezogene Richtlinien für bestimmte Benutzer konfiguriert haben, erhalten diese Benutzer diese zusätzlichen Einstellungen und Bezeichnungen. 

Beachten Sie, dass zusätzlich zu den Office-Desktopanwendungen, die dan Azure Information Protection-Client unterstützen, ebenfalls Bezeichnungen mit PowerShell sowie die Azure Information Protection-Überprüfung unterstützt werden. Das bedeutet, dass Sie bereichsbezogene Richtlinien für Konten, die PowerShell-Befehle ausführen, oder für die Überprüfung konfigurieren können. 

Bereichsbezogene Richtlinien sind wie Bezeichnungen im Azure-Portal angeordnet. Wenn ein Benutzer für mehrere Bereiche konfiguriert ist, wird eine effektive Richtlinie für den Benutzer berechnet, bevor sie heruntergeladen wird. Gemäß der Reihenfolge der Richtlinien wird die letzte Richtlinien Einstellung angewendet. Die Bezeichnungen, die dem Benutzer angezeigt werden, stammen aus der globalen Richtlinie und alle zusätzlichen Bezeichnungen aus bereichsbezogenen Richtlinien, denen der Benutzer angehört.

Die Ausnahme ist, wenn ein Dokument oder eine E-Mail mit einer Bezeichnung von einem Benutzer Ihres Mandanten geöffnet wird, der sich nicht im Bezeichnungsbereich befindet. In diesem Fall sieht der Benutzer den Namen des Bezeichnungssets, doch die Bezeichnung selbst kann nicht ausgewählt werden.  

Da eine bereichsbezogene Richtlinie immer die Bezeichnungen und Einstellungen der globalen Richtlinie erbt, werden die Bezeichnungen der globalen Richtlinie angezeigt, wenn Sie eine bereichsbezogene Richtlinie erstellen oder bearbeiten. Sie können jedoch nicht die Bezeichnungen der globalen Richtlinie bearbeiten, wenn Sie eine bereichsbezogene Richtlinie bearbeiten. Sie können diesen geerbten Bezeichnungen jedoch untergeordnete Bezeichnungen hinzufügen.

Wenn die globale Richtlinie beispielsweise eine Bezeichnung namens **Vertraulich** enthält, wird diese Bezeichnung allen Benutzern angezeigt. Sie können sie nicht über eine bereichsbezogenen Richtlinie entfernen oder neu anordnen. Unter Umständen möchten Sie jedoch eine bereichsbezogene Richtlinie für die Marketingabteilung erstellen, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Vertraulich\Werbeaktionen** angezeigt wird. Sie erstellen zudem eine weitere bereichsbezogene Richtlinie für die Vertriebsabteilung, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Vertraulich\Partner** angezeigt wird. Jede untergeordnete Bezeichnung kann dann für unterschiedliche Einstellungen konfiguriert werden, und die untergeordnete Bezeichnung wird nur den Benutzern in der entsprechenden Abteilung angezeigt.

## <a name="configure-a-scoped-policy"></a>Konfigurieren einer Bereichs bezogenen Richtlinie

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.

    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die Menüoption **Klassifizierungen**  >  **Richtlinien** : Wählen Sie im Bereich **Azure Information Protection-Richtlinien** die Option **neue Richtlinie hinzufügen** aus. Daraufhin wird der Bereich **Richtlinie** angezeigt, in dem Ihre vorhandene globale Richtlinie angezeigt wird, in der Sie nun Ihre neue Bereichs bezogene Richtlinie konfigurieren können.

3. Geben Sie einen Richtliniennamen und eine Beschreibung an, die nur für Administratoren im Azure-Portal angezeigt wird. Der Name muss für Ihren Mandanten eindeutig sein. Wählen Sie dann **angeben, welche Benutzer/Gruppen diese Richtlinie erhalten**. in den nachfolgenden Bereichen können Sie die Benutzer und Gruppen für diese Richtlinie suchen und auswählen. Die Bezeichnungen und Einstellungen, die Sie in dieser bereichsbezogenen Richtlinie konfigurieren, werden nur auf diese Benutzer angewendet.
    
    Aus Leistungsgründen wird die Gruppenmitgliedschaft für bereichsbezogene Richtlinien [zwischengespeichert](prepare.md#group-membership-caching-by-azure-information-protection).

    > [!NOTE]
    > Wählen Sie bis zu 200 Benutzer oder Gruppen aus. Wenn mehr als 200 Benutzer erforderlich sind, um die Bereichs bezogene Richtlinie zu erhalten, erstellen Sie eine neue Gruppe, fügen Sie der Gruppe relevante Benutzer hinzu, und legen Sie dann den Richtlinien Bereich auf die neue Gruppe fest. 

4. Fügen Sie jetzt neue Bezeichnungen hinzu, oder konfigurieren Sie die bereichsbezogenen Richtlinieneinstellungen. Die globale Richtlinie wird immer zuerst angewendet. Dadurch können Sie die globale Richtlinie mit neuen Bezeichnungen ergänzen und die globalen Einstellungen überschreiben. Beispielsweise verfügt die globale Richtlinie unter Umständen über keine Standardbezeichnung, und Sie konfigurieren eine andere Standardbezeichnung in verschiedenen bereichsbezogenen Richtlinien für bestimmte Abteilungen.

    Wenn Sie Hilfe beim Konfigurieren der Bezeichnungen oder Einstellungen benötigen, verwenden Sie die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy) .

6. Wenn Sie in einem Azure Information Protection Bereich Änderungen vornehmen, klicken Sie auf **Speichern** , um die Änderungen zu speichern, oder auf **verwerfen** , um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

7. Wenn Sie die gewünschten Änderungen für diese Bereichs bezogene Richtlinie abgeschlossen haben, stellen Sie im Bereich anfängliche **Azure Information Protection-Richtlinien** sicher, dass diese Bereichs bezogene Richtlinie in der gewünschten Reihenfolge angezeigt wird. Dies ist wichtig, wenn Sie denselben Benutzer für mehrere bereichsbezogene Richtlinien ausgewählt haben. Klicken Sie zum Ändern der Reihenfolge auf das Kontextmenü (**...**) und dann auf **Nach oben** oder **Nach unten**. 

Beim Starten einer unterstützten Office-Anwendung oder beim Öffnen des Datei-Explorers prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Der Client lädt dann alle Änderungen an der globalen Richtlinie oder den bereichsbezogenen Richtlinien herunter, die für diesen Benutzer gelten.

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Tutorial: Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md).
