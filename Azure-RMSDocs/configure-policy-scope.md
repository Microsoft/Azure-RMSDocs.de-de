---
title: Konfigurieren bereichsbezogener Richtlinien für Azure Information Protection – AIP
description: Um andere Einstellungen und Bezeichnungen für bestimmte Benutzer zu konfigurieren, müssen Sie eine bereichsbezogene Richtlinie für Azure Information Protection konfigurieren.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/09/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4b134785-0353-4109-8fa7-096d1caa2242
ms.subservice: aiplabels
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d0a370950bb5853453106e59af3da9c9a2f8f463
ms.sourcegitcommit: b66b249ab5681d02ec3b5af0b820eda262d5976a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "78972888"
---
# <a name="how-to-configure-the-azure-information-protection-policy-for-specific-users-by-using-scoped-policies"></a>Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Beim die Azure Information Protection-Richtlinie auf Computer heruntergeladen wird, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist, erhalten alle Benutzer die Einstellungen und Bezeichnungen der Standardrichtlinie oder die Änderungen, die Sie für die globale Richtlinie konfiguriert haben. Wenn Sie diese Konfiguration für bestimmte Benutzer ergänzen möchten, indem Sie verschiedene Einstellungen und Bezeichnungen haben, müssen Sie eine Bereichs bezogene **Richtlinie** erstellen, die für diese Benutzer konfiguriert ist.

## <a name="how-scoped-policies-work"></a>Funktionsweise von Bereichs bezogenen Richtlinien

Für Anwendungen, die den Azure Information Protection-Client verwenden erhalten alle Benutzer die globale Richtlinie, die Titel und QuickInfo sowie globale Einstellungen und globale Bezeichnungen der Information Protection-Leiste enthält. Wenn Sie bereichsbezogene Richtlinien für bestimmte Benutzer konfiguriert haben, erhalten diese Benutzer diese zusätzlichen Einstellungen und Bezeichnungen. 

Beachten Sie, dass zusätzlich zu den Office-Desktopanwendungen, die dan Azure Information Protection-Client unterstützen, ebenfalls Bezeichnungen mit PowerShell sowie die Azure Information Protection-Überprüfung unterstützt werden. Das bedeutet, dass Sie bereichsbezogene Richtlinien für Konten, die PowerShell-Befehle ausführen, oder für die Überprüfung konfigurieren können. 

Bereichsbezogene Richtlinien sind wie Bezeichnungen im Azure-Portal angeordnet. Wenn ein Benutzer für mehrere Bereiche konfiguriert ist, wird eine effektive Richtlinie für den Benutzer berechnet, bevor sie heruntergeladen wird. Gemäß der Reihenfolge der Richtlinien wird die letzte Richtlinien Einstellung angewendet. Die Bezeichnungen, die dem Benutzer angezeigt werden, stammen aus der globalen Richtlinie und allen zusätzlichen Bezeichnungen aus bereichsbezogenen Richtlinien, denen der Benutzer angehört.

Die Ausnahme ist, wenn ein Dokument oder eine E-Mail mit einer Bezeichnung von einem Benutzer Ihres Mandanten geöffnet wird, der sich nicht im Bezeichnungsbereich befindet. In diesem Fall sieht der Benutzer den Namen des Bezeichnungssets, doch die Bezeichnung selbst kann nicht ausgewählt werden.  

Da eine bereichsbezogene Richtlinie immer die Bezeichnungen und Einstellungen der globalen Richtlinie erbt, werden die Bezeichnungen der globalen Richtlinie angezeigt, wenn Sie eine bereichsbezogene Richtlinie erstellen oder bearbeiten. Sie können jedoch nicht die Bezeichnungen der globalen Richtlinie bearbeiten, wenn Sie eine bereichsbezogene Richtlinie bearbeiten. Sie können diesen geerbten Bezeichnungen jedoch untergeordnete Bezeichnungen hinzufügen.

Wenn Sie z.B. in der globalen Richtlinie über eine Bezeichnung namens **Vertraulich** verfügen, wird diese Bezeichnung allen Benutzern angezeigt. Sie können sie nicht über eine bereichsbezogenen Richtlinie entfernen oder neu anordnen. Aber Sie sollten eine bereichsbezogene Richtlinie für die Marketingabteilung erstellen, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Confidential/Promotions** (Vertraulich/Aktionen) angezeigt wird. Sie erstellen zudem eine weitere bereichsbezogene Richtlinie für die Vertriebsabteilung, die eine neue untergeordnete Bezeichnung zu „Vertraulich“ hinzufügt, sodass diesen Benutzern **Confidential/Partners** (Vertraulich/Partner) angezeigt wird. Jede untergeordnete Bezeichnung kann dann für unterschiedliche Einstellungen konfiguriert werden, und die untergeordnete Bezeichnung wird nur den entsprechenden Benutzern in der Abteilung angezeigt.

## <a name="configure-a-scoped-policy"></a>Konfigurieren einer Bereichs bezogenen Richtlinie

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.

    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Über die Menüoption **Klassifizierungen** > **Richtlinien** : Wählen Sie im Bereich " **Azure Information Protection-Richtlinien** " die Option **neue Richtlinie hinzufügen**aus. Daraufhin wird der Bereich **Richtlinie** angezeigt, in dem Ihre vorhandene globale Richtlinie angezeigt wird, in der Sie nun Ihre neue Bereichs bezogene Richtlinie konfigurieren können.

3. Geben Sie einen Richtliniennamen und eine Beschreibung an, die nur für Administratoren im Azure-Portal angezeigt wird. Der Name muss für Ihren Mandanten eindeutig sein. Wählen Sie dann **angeben, welche Benutzer/Gruppen diese Richtlinie erhalten**. in den nachfolgenden Bereichen können Sie die Benutzer und Gruppen für diese Richtlinie suchen und auswählen. Die Bezeichnungen und Einstellungen, die Sie in dieser bereichsbezogenen Richtlinie konfigurieren, werden nur auf diese Benutzer angewendet.
    
    Aus Leistungsgründen wird die Gruppenmitgliedschaft für bereichsbezogene Richtlinien [zwischengespeichert](prepare.md#group-membership-caching-by-azure-information-protection).

4. Fügen Sie jetzt neue Bezeichnungen hinzu, oder konfigurieren Sie die bereichsbezogenen Richtlinieneinstellungen. Die globale Richtlinie wird immer zuerst angewendet, so können Sie die globale Richtlinie mit neuen Bezeichnungen ergänzen, und Sie können die globalen Einstellungen außer Kraft setzen. Die globale Richtlinie verfügt möglicherweise über keine Standardbezeichnung, und Sie konfigurieren eine andere Standardbezeichnung in verschiedenen bereichsbezogenen Richtlinien für bestimmte Abteilungen.

    Wenn Sie Hilfe beim Konfigurieren der Bezeichnungen oder Einstellungen benötigen, verwenden Sie die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy) .

6. Wenn Sie in einem Azure Information Protection Bereich Änderungen vornehmen, klicken Sie auf **Speichern** , um die Änderungen zu speichern, oder auf **verwerfen** , um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

7. Wenn Sie die gewünschten Änderungen für diese Bereichs bezogene Richtlinie abgeschlossen haben, stellen Sie im Bereich anfängliche **Azure Information Protection-Richtlinien** sicher, dass diese Bereichs bezogene Richtlinie in der gewünschten Reihenfolge angezeigt wird. Dies ist wichtig, wenn Sie denselben Benutzer für mehrere bereichsbezogene Richtlinien ausgewählt haben. Klicken Sie zum Ändern der Reihenfolge auf das Kontextmenü ( **...** ), und klicken Sie auf **Nach oben** oder **Nach unten**. 

Beim Start einer unterstützten Office-Anwendung oder Öffnen des Datei-Explorers prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Der Client lädt dann alle Änderungen an der globalen Richtlinie oder bereichsbezogenen Richtlinie herunter, die für diesen Benutzer gelten.

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Tutorial: Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md).
