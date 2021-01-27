---
title: Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection
description: Sie können die Unterstützung für verschiedene Sprachen für die Bezeichnungen und Vorlagen erweitern, die in der Information Protection-Leiste für Benutzer angezeigt werden, indem Sie die Sprachen in der Azure Information Protection-Richtlinie angeben und Ihre Übersetzungen importieren.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ROBOTS: NOINDEX
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: f6a9f17a6679d9752f11b5209d9ce083c8ef8009
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809798"
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Vorgehensweise beim Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified Label-Client finden Sie in der Microsoft 365-Dokumentation unter Informationen [zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) . Verwenden Sie den *localesettings* -Parameter für das Cmdlet " [Set-Label](/powershell/module/exchange/policy-and-compliance/set-label) ", um verschiedene Sprachen für Vertraulichkeits Bezeichnungen zu konfigurieren. *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>

Obwohl die Standardbezeichnungen für Azure Information Protection mehrere Sprachen unterstützen, müssen Sie eine Unterstützung für die Bezeichnungsnamen und -beschreibungen konfigurieren, die Sie angeben. Für diese Konfiguration müssen Sie folgende Aktionen ausführen:

1. Wählen Sie die Sprachen, die Ihre Benutzer verwenden. 

2. Exportieren Sie Ihre aktuellen Bezeichnungsnamen und -beschreibungen in eine Datei.

3. Bearbeiten Sie die Datei, um Ihre Übersetzungen einzugeben.

4. Importieren Sie die Datei wieder zurück in Ihre Azure Information Protection-Richtlinie.

Sie können auch Vorlagen für verschiedene Sprachen konfigurieren, wenn eine der folgenden Bedingungen zutrifft. Diese Konfiguration ist geeignet, wenn Benutzer oder Administratoren den aktuellen Namen und die Beschreibung einer Vorlage in ihrer lokalisierten Sprache anzeigen müssen.

- Die Vorlage wurde im klassischen Azure-Portal oder durch Verwenden von PowerShell erstellt und ist nicht mit einer Bezeichnung durch das Verwenden der Schutzeinstellung **Vordefinierte Vorlage auswählen** verknüpft.

- Sie verfügen nicht über ein Abonnement, das Bezeichnungen unterstützt, deshalb können Sie Vorlagen nur im Azure-Portal erstellen und verwalten.

Wählen Sie die Sprachen aus, die der Spracheinstellung Ihrer Benutzer für Office und Windows entsprechen. Diese Bezeichnungsnamen und Beschreibungen werden dann in Office-Apps in der Azure Information Protection-Leiste bzw. im Dialogfeld **Klassifizierung und Schutz – Azure Information Protection** angezeigt. Weitere Informationen über die gewählte Sprache finden Sie auf dieser Seite im Abschnitt [Informationen zu den Kriterien für die Auswahl der Anzeigesprache durch den Azure Information Protection-Client](#how-the-azure-information-protection-client-determines-the-language-to-display). 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>Konfigurieren von Bezeichnungen und Vorlagen für verschiedene Sprachen

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die   >  Menüoption "**Sprachen** verwalten": Wählen Sie im Bereich " **Azure Information Protection-Sprachen** " die Option **neue Sprache für Übersetzung hinzufügen** aus. Wählen Sie die Sprachen aus, die Sie hinzufügen möchten, und klicken Sie dann auf **OK**. Sie können entweder den Namen der Sprache in das Suchfeld eingeben oder durch die Liste der verfügbaren Sprachen scrollen.

3. Die ausgewählten Sprachen werden nun im Bereich **Azure Information Protection-Sprachen** angezeigt:
    
    - Wählen Sie zum Hinzufügen einer anderen Sprache **Neue Sprache für die Übersetzung hinzufügen** aus, und wiederholen Sie die vorherigen Schritte. 
        
        > [!NOTE]
        > Achten Sie darauf, die von Ihren Benutzern für Office und für Windows ausgewählten Sprachen auszuwählen. In einigen Fällen müssen hierfür zwei verschiedene Sprachen pro Computer ausgewählt werden.
        
    - Wenn Sie Ihre Entscheidung bezüglich einer hinzugefügten Sprache ändern möchten, wählen Sie den jeweiligen Eintrag aus der Liste aus, und klicken Sie dann auf **Entfernen**.

4. Wenn alle Sprachen, die unterstützt werden sollen, aufgeführt sind, aktivieren Sie das Kontrollkästchen **SPRACHENNAME**, um alle Einträge (oder alternativ einzelne Einträge) auszuwählen. Klicken Sie anschließend auf **Exportieren**, um eine lokale Kopie der vorhandenen Bezeichnungsnamen und Beschreibungen in einer Datei zu speichern. 
    
    Die heruntergeladene Datei heißt **exported localization.zip** und wird im lokalen Ordner „Downloads“ gespeichert. Sie kann auch durch Auswahl dieses Dateinamens in der Statusleiste des Azure-Portals aufgerufen werden.

5. Extrahieren Sie die Dateien aus **exported localization.zip**, sodass für jede Sprache, die Sie für den Download ausgewählt haben, XML-Dateien verfügbar sind. 

6. So bearbeiten Sie jede XML-Datei: Geben Sie für jede Zeichenfolge in `<LocalizedText>`-Tags die gewünschten Übersetzungen für jede ausgewählte Sprache an. 

7. Wenn Sie alle XML-Dateien bearbeitet haben, erstellen Sie einen neuen ZIP-komprimierten Ordner, der diese Dateien enthält. Der komprimierte Ordner kann mit einem beliebigen Namen versehen werden, muss jedoch die Erweiterung ZIP aufweisen.
    
    Tipp: Sie müssen nicht warten, bis Sie jede Sprachdatei bearbeitet haben, die Sie heruntergeladen haben. Stattdessen können Sie verschiedene Sprachen schrittweise ausrollen, indem Sie in die.zip-Datei eine Teilmenge der gesamten heruntergeladenen Dateien aufnehmen. Wiederholen Sie dann die Schritte 7 und 8, wenn Sie die Übersetzungen für weitere Sprachen abgeschlossen haben.

8. Kehren Sie zum Bereich **Azure Information Protection-Sprachen** zurück, und wählen Sie **importieren** aus. Hinweis: Wenn diese Option nicht verfügbar ist, deaktivieren Sie zuerst das Kontrollkästchen **SPRACHENNAME** oder die Kontrollkästchen der einzeln ausgewählten Sprachen.
    
    Nachdem der Import abgeschlossen wurde, werden die lokalisierten Namen und Beschreibungen im Bereich „Benutzer“ heruntergeladen.

Sie müssen diesen Vorgang wiederholen, wenn Sie eine neue Sprache unterstützen, neue Bezeichnungen erstellen oder den Namen oder die Beschreibung von Bezeichnungen im Azure-Portal ändern müssen.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Informationen zu den Kriterien für die Auswahl der Anzeigesprache durch den Azure Information Protection-Client

Wenn Benutzer eine Azure Information Protection-Richtlinie mit verschiedenen unterstützten Sprachen herunterladen, wird die Sprache, in denen Bezeichnungsnamen und QuickInfos für Benutzer angezeigt werden, gemäß folgender Logik ausgewählt:

**Für die Bezeichnungen und Quick Infos, die Benutzern auf der Azure Information Protection Leiste in Office-Apps angezeigt** werden:

- Wenn eine direkte Übereinstimmung für die Sprache der Office-App gefunden wird, werden Bezeichnungsnamen und Beschreibungen in dieser Sprache angezeigt.

- Wenn keine direkte Übereinstimmung für die Sprache der Office-App gefunden wird, werden Bezeichnungsnamen und Beschreibungen in der Sprache angezeigt, die Sie für alle Benutzer standardmäßig festgelegt haben. Bei dieser Sprache handelt es sich in der Regel um Englisch. Diese Sprache wird in der Standardrichtlinie verwendet.

**Für die Bezeichnungen und Quick Infos, die Benutzern angezeigt werden, wenn Sie mit der rechten Maustaste zum klassifizieren und schützen von Dateien oder Ordnern verwendet** werden:

- Wenn eine direkte Übereinstimmung für die Sprache ihres Betriebssystems gefunden wird, werden Bezeichnungsnamen und Beschreibungen in dieser Sprache angezeigt.

- Wenn keine direkte Übereinstimmung für die Sprache ihres Betriebssystems gefunden wird, werden Bezeichnungsnamen und Beschreibungen in der Sprache angezeigt, die Sie für alle Benutzer standardmäßig festgelegt haben. Bei dieser Sprache handelt es sich in der Regel um Englisch. Diese Sprache wird in der Standardrichtlinie verwendet.

## <a name="when-localized-label-names-are-not-used"></a>Fälle, in denen lokalisierte Bezeichnungsnamen nicht verwendet werden

In folgenden Szenarios werden keine Namen für lokalisierte Bezeichnungen (und untergeordnete Bezeichnungen) verwendet. Um Konsistenz innerhalb Ihres Mandanten sicherzustellen, wird die Standardsprache immer für Folgendes verwendet:

- Clientnutzungsprotokolle

- PowerShell (Ausgabe von „Get-AIPFileStatus“)

- Dokumentmetadaten und E-Mail-Header


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinien zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).