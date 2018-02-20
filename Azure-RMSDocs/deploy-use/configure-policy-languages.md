---
title: "Konfigurieren von Bezeichnungen und Vorlagen für verschiedene Sprachen in Azure Information Protection"
description: "Sie können die Unterstützung für verschiedene Sprachen für die Bezeichnungen und Vorlagen erweitern, die in der Information Protection-Leiste für Benutzer angezeigt werden, indem Sie die Sprachen in der Azure Information Protection-Richtlinie angeben und Ihre Übersetzungen importieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: f57b3802386aced71967a5ab619cdabf2fd67a37
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-configure-labels-and-templates-for-different-languages-in-azure-information-protection"></a>Vorgehensweise beim Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection

>*Gilt für: Azure Information Protection*

Obwohl die Standardbezeichnungen für Azure Information Protection mehrere Sprachen unterstützen, müssen Sie eine Unterstützung für die Bezeichnungsnamen und -beschreibungen konfigurieren, die Sie angeben. Für diese Konfiguration müssen Sie folgende Aktionen ausführen:

1. Wählen Sie die Sprachen, die Ihre Benutzer verwenden. 

2. Exportieren Sie Ihre aktuellen Bezeichnungsnamen und -beschreibungen in eine Datei.

3. Bearbeiten Sie die Datei, um Ihre Übersetzungen einzugeben.

4. Importieren Sie die Datei wieder zurück in Ihre Azure Information Protection-Richtlinie.

Sie können auch Vorlagen für verschiedene Sprachen konfigurieren, wenn eine der folgenden Bedingungen zutrifft. Diese Konfiguration ist geeignet, wenn Benutzer oder Administratoren den aktuellen Namen und die Beschreibung einer Vorlage in ihrer lokalisierten Sprache anzeigen müssen.

- Die Vorlage wurde im klassischen Azure-Portal oder durch Verwenden von PowerShell erstellt und ist nicht mit einer Bezeichnung durch das Verwenden der Schutzeinstellung **Vordefinierte Vorlage auswählen** verknüpft.

- Sie verfügen nicht über ein Abonnement, das Bezeichnungen unterstützt, deshalb können Sie Vorlagen nur im Azure-Portal erstellen und verwalten.

Wählen Sie die Sprachen aus, die der Spracheinstellung Ihrer Benutzer für Office und Windows entsprechen. Diese Bezeichnungsnamen und Beschreibungen werden dann in Office-Apps in der Azure Information Protection-Leiste bzw. im Dialogfeld **Klassifizierung und Schutz – Azure Information Protection** angezeigt. Weitere Informationen über die gewählte Sprache finden Sie auf dieser Seite im Abschnitt [Informationen zu den Kriterien für die Auswahl der Anzeigesprache durch den Azure Information Protection-Client](#how-the-azure-information-protection-client-determines-the-language-to- display). 

## <a name="to-configure-labels-and-templates-for-different-languages"></a>Konfigurieren von Bezeichnungen und Vorlagen für verschiedene Sprachen

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Klicken Sie in der Menüauswahl **Verwalten** auf **Sprachen**.

3. Klicken Sie auf dem Blatt**Azure Information Protection - Languages** (Azure Information Protection: Sprachen) auf **Neue Sprache für Übersetzung hinzufügen**. Wählen Sie die Sprachen aus, die Sie hinzufügen möchten, und klicken Sie dann auf **OK**. Sie können entweder den Namen der Sprache in das Suchfeld eingeben oder durch die Liste der verfügbaren Sprachen scrollen.

4. Ihre ausgewählten Sprachen werden nun auf dem Blatt **Azure Information Protection - Languages** (Azure Information Protection: Sprachen) angezeigt:
    
    - Wählen Sie zum Hinzufügen einer anderen Sprache **Neue Sprache für die Übersetzung hinzufügen** aus, und wiederholen Sie die vorherigen Schritte. 
        
        > [!NOTE]
        > Achten Sie darauf, die von Ihren Benutzern für Office und für Windows ausgewählten Sprachen auszuwählen. In einigen Fällen müssen hierfür zwei verschiedene Sprachen pro Computer ausgewählt werden.
        
    - Wenn Sie Ihre Entscheidung bezüglich einer hinzugefügten Sprache ändern möchten, wählen Sie den jeweiligen Eintrag aus der Liste aus, und klicken Sie dann auf **Entfernen**.

5. Wenn alle Sprachen, die unterstützt werden sollen, aufgeführt sind, aktivieren Sie das Kontrollkästchen **SPRACHENNAME**, um alle Einträge (oder alternativ einzelne Einträge) auszuwählen. Klicken Sie anschließend auf **Exportieren**, um eine lokale Kopie der vorhandenen Bezeichnungsnamen und Beschreibungen in einer Datei zu speichern. 
    
    Die heruntergeladene Datei heißt **exported localization.zip** und wird im lokalen Ordner „Downloads“ gespeichert. Sie kann auch durch Auswahl dieses Dateinamens in der Statusleiste des Azure-Portals aufgerufen werden.

6. Extrahieren Sie die Dateien aus **exported localization.zip**, sodass für jede Sprache, die Sie für den Download ausgewählt haben, XML-Dateien verfügbar sind. 

7. So bearbeiten Sie jede XML-Datei: Geben Sie für jede Zeichenfolge in `<LocalizedText>`-Tags die gewünschten Übersetzungen für jede ausgewählte Sprache an. 

8. Wenn Sie alle XML-Dateien bearbeitet haben, erstellen Sie einen neuen ZIP-komprimierten Ordner, der diese Dateien enthält. Der komprimierte Ordner kann mit einem beliebigen Namen versehen werden, muss jedoch die Erweiterung ZIP aufweisen.

9. Kehren Sie zum Blatt **Azure Information Protection - Languages** (Azure Information Protection: Sprachen) zurück, und klicken Sie auf **Importieren**. Hinweis: Wenn diese Option nicht verfügbar ist, deaktivieren Sie zuerst das Kontrollkästchen **SPRACHENNAME** oder die Kontrollkästchen der einzeln ausgewählten Sprachen.
    
    Wenn der Import abgeschlossen ist, werden die lokalisierten Namen und Beschreibungen für Benutzer nach der Veröffentlichung der Azure Information Protection-Richtlinie heruntergeladen. Auf dem Blatt **Globale Richtlinie** oder **Bereichsbezogene Richtlinien** können Sie auf **Veröffentlichen** klicken.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Informationen zu den Kriterien für die Auswahl der Anzeigesprache durch den Azure Information Protection-Client

Wenn Benutzer eine Azure Information Protection-Richtlinie mit verschiedenen unterstützten Sprachen herunterladen, wird die Sprache, in denen Bezeichnungsnamen und QuickInfos für Benutzer angezeigt werden, gemäß folgender Logik ausgewählt:

**Bei Bezeichnungen und QuickInfos, die Benutzer in der Azure Information Protection-Leiste in Office-Apps sehen:**

- Wenn eine direkte Übereinstimmung für die Sprache der Office-App gefunden wird, werden Bezeichnungsnamen und Beschreibungen in dieser Sprache angezeigt.

- Wenn keine direkte Übereinstimmung für die Sprache der Office-App gefunden wird, werden Bezeichnungsnamen und Beschreibungen in der Sprache angezeigt, die Sie für alle Benutzer standardmäßig festgelegt haben. Bei dieser Sprache handelt es sich in der Regel um Englisch. Diese Sprache wird in der Standardrichtlinie verwendet.

**Bei Bezeichnungen und QuickInfos, die Benutzern angezeigt werden, wenn sie per Rechtsklick Dateien oder Ordner klassifizieren und schützen:**

- Wenn eine direkte Übereinstimmung für die Sprache ihres Betriebssystems gefunden wird, werden Bezeichnungsnamen und Beschreibungen in dieser Sprache angezeigt.

- Wenn keine direkte Übereinstimmung für die Sprache ihres Betriebssystems gefunden wird, werden Bezeichnungsnamen und Beschreibungen in der Sprache angezeigt, die Sie für alle Benutzer standardmäßig festgelegt haben. Bei dieser Sprache handelt es sich in der Regel um Englisch. Diese Sprache wird in der Standardrichtlinie verwendet.

## <a name="when-localized-label-names-are-not-used"></a>Fälle, in denen lokalisierte Bezeichnungsnamen nicht verwendet werden

In folgenden Szenarios werden keine Namen für lokalisierte Bezeichnungen (und untergeordnete Bezeichnungen) verwendet. Um Konsistenz innerhalb Ihres Mandanten sicherzustellen, wird die Standardsprache immer für Folgendes verwendet:

- Clientnutzungsprotokolle

- PowerShell (Ausgabe von „Get-AIPFileStatus“)

- Dokumentmetadaten und E-Mail-Header


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


