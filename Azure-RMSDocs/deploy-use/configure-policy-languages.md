---
title: "Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection"
description: "Sie können die Unterstützung für verschiedene Sprachen für die Bezeichnungen erweitern, die in der Information Protection-Leiste für Benutzer angezeigt werden, indem Sie die Sprachen in der Azure Information Protection-Richtlinie angeben und Ihre Übersetzungen importieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a0e89fd0-795b-4e7a-aea9-ff6fc9163bde
ms.openlocfilehash: ec99bf36e8904a7304a9d33c32d17ba92e2e22d2
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2017
---
# <a name="how-to-configure-labels-for-different-languages-in-azure-information-protection"></a>Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen in Azure Information Protection

>*Gilt für: Azure Information Protection*

>[!NOTE]
>Diese Funktion ist derzeit in der Vorschau verfügbar und ist für die Verwendung in der **Vorschauversion** des Azure Information Protection-Clients bestimmt, die Sie aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018) herunterladen können.

Standardmäßig wird für die Namen und Beschreibungen von Bezeichnungen eine einzelne Sprache unterstützt, die für alle Benutzer in Ihrer Organisation angezeigt wird. Sie können die Unterstützung für verschiedene Sprachen erweitern, indem Sie die benötigten Sprachen auswählen, Ihre aktuellen Bezeichnungsnamen und Beschreibungen in eine Datei exportieren, die Datei für die Bereitstellung Ihrer Übersetzungen bearbeiten und die Datei wieder in Ihre Azure Information Protection-Richtlinie importieren.

Wählen Sie die Sprachen aus, die der Spracheinstellung Ihrer Benutzer für Office und Windows entsprechen. Diese Bezeichnungsnamen und Beschreibungen werden dann in Office-Apps in der Azure Information Protection-Leiste bzw. im Dialogfeld **Klassifizierung und Schutz – Azure Information Protection** angezeigt. Weitere Informationen über die gewählte Sprache finden Sie auf dieser Seite im Abschnitt [Informationen zu den Kriterien für die Auswahl der Anzeigesprache durch den Azure Information Protection-Client](#how-the-azure-information-protection-client-determines-the-language-to- display). 

## <a name="to-configure-labels-to-display-in-different-languages"></a>Konfigurieren von Bezeichnungen zur Anzeige in verschiedenen Sprachen

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Navigieren Sie auf dem ersten **Azure Information Protection**-Blatt zu **VERWALTEN**, und wählen Sie dann **Sprachen (Vorschau)** aus.

3. Navigieren Sie auf dem Blatt **Azure Information Protection – Sprachen (Vorschau)** zu der ersten Sprache, die hinzugefügt werden soll, indem Sie den Namen in das Suchfeld eingeben oder durch die Liste der verfügbaren Sprachen scrollen. 

4. Wählen Sie Ihre Sprache aus, und klicken Sie auf **OK**.

5. Auf dem nächsten Blatt sehen Sie, dass Ihre ausgewählte Sprache zu einer Liste hinzugefügt wurde:
    
    - Wählen Sie zum Hinzufügen einer anderen Sprache **Neue Sprache für die Übersetzung hinzufügen** aus, und wiederholen Sie die Schritte 3 und 4. 
        
        > [!NOTE]
        > Achten Sie darauf, die von Ihren Benutzern für Office und für Windows ausgewählten Sprachen auszuwählen. In einigen Fällen müssen hierfür zwei verschiedene Sprachen pro Computer ausgewählt werden.
        
    - Wenn Sie Ihre Entscheidung bezüglich einer hinzugefügten Sprache ändern möchten, wählen Sie den jeweiligen Eintrag aus der Liste aus, und klicken Sie dann auf **Entfernen**.

6. Wenn alle Sprachen, die unterstützt werden sollen, aufgeführt sind, aktivieren Sie das Kontrollkästchen **SPRACHENNAME**, um alle Einträge (oder alternativ einzelne Einträge) auszuwählen. Klicken Sie anschließend auf **Exportieren**, um eine lokale Kopie der vorhandenen Bezeichnungsnamen und Beschreibungen in einer Datei zu speichern. 
    
    Die heruntergeladene Datei heißt **exported localization.zip** und wird im lokalen Ordner „Downloads“ gespeichert. Sie kann auch durch Auswahl dieses Dateinamens in der Statusleiste des Azure-Portals aufgerufen werden.

7. Extrahieren Sie die Dateien aus **exported localization.zip**, sodass für jede Sprache, die Sie für den Download ausgewählt haben, XML-Dateien verfügbar sind. 

8. So bearbeiten Sie jede XML-Datei: Geben Sie für jede Zeichenfolge in `<LocalizedText>`-Tags die gewünschten Übersetzungen für jede ausgewählte Sprache an. 

9. Wenn Sie alle XML-Dateien bearbeitet haben, erstellen Sie einen neuen ZIP-komprimierten Ordner, der diese Dateien enthält. Der komprimierte Ordner kann mit einem beliebigen Namen versehen werden, muss jedoch die Erweiterung ZIP aufweisen.

10. Kehren Sie zum Blatt des Azure-Portals zurück, und wählen Sie **Importieren**. Hinweis: Wenn diese Option nicht verfügbar ist, deaktivieren Sie zuerst das Kontrollkästchen **SPRACHENNAME** oder die Kontrollkästchen der einzeln ausgewählten Sprachen.
    
    Wenn der Import abgeschlossen ist, werden die lokalisierten Bezeichnungsnamen und Beschreibungen für Benutzer nach der Veröffentlichung der Azure Information Protection-Richtlinie heruntergeladen. Auf dem Blatt **Globale Richtlinie** oder **Bereichsbezogene Richtlinien** können Sie auf **Veröffentlichen** klicken.

## <a name="how-the-azure-information-protection-client-determines-the-language-to-display"></a>Informationen zu den Kriterien für die Auswahl der Anzeigesprache durch den Azure Information Protection-Client

Wenn Benutzer eine Azure Information Protection-Richtlinie mit verschiedenen unterstützten Sprachen herunterladen, wird die Sprache, in denen Bezeichnungsnamen und QuickInfos für Benutzer angezeigt werden, gemäß folgender Logik ausgewählt:

**Bei Bezeichnungen und QuickInfos, die Benutzer in der Azure Information Protection-Leiste in Office-Apps sehen:**

- Wenn eine direkte Übereinstimmung für die Sprache der Office-App gefunden wird, werden Bezeichnungsnamen und Beschreibungen in dieser Sprache angezeigt.

- Wenn keine direkte Übereinstimmung für die Sprache der Office-App gefunden wird, werden Bezeichnungsnamen und Beschreibungen in der Sprache angezeigt, die Sie für alle Benutzer standardmäßig festgelegt haben. Bei dieser Sprache handelt es sich in der Regel um Englisch. Diese Sprache wird in der Standardrichtlinie verwendet.

**Bei Bezeichnungen und QuickInfos, die Benutzern angezeigt werden, wenn sie per Rechtsklick Dateien oder Ordner klassifizieren und schützen:**

- Wenn eine direkte Übereinstimmung für die Sprache ihres Betriebssystems gefunden wird, werden Bezeichnungsnamen und Beschreibungen in dieser Sprache angezeigt.

- Wenn keine direkte Übereinstimmung für die Sprache ihres Betriebssystems gefunden wird, werden Bezeichnungsnamen und Beschreibungen in der Sprache angezeigt, die Sie für alle Benutzer standardmäßig festgelegt haben. Bei dieser Sprache handelt es sich in der Regel um Englisch. Diese Sprache wird in der Standardrichtlinie verwendet.

## <a name="when-localized-label-names-are-not-used"></a>Fälle, in denen lokalisierte Bezeichnungsnamen nicht verwendet werden

In folgenden Szenarien werden Namen für lokalisierte Bezeichnungen (und untergeordnete Bezeichnungen) nicht verwendet. Um Konsistenz innerhalb Ihres Mandanten sicherzustellen, wird die Standardsprache immer für Folgendes verwendet:

- Clientnutzungsprotokolle

- PowerShell (Ausgabe von „Get-AIPFileStatus“)

- Dokumentmetadaten und E-Mail-Header


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zur Konfiguration der verfügbaren Optionen für eine Bezeichnung sowie zu weiteren Einstellungen für Ihre Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


