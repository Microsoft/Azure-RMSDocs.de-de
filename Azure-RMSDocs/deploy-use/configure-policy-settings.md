---
title: Konfigurieren der Azure Information Protection-Richtlinieneinstellungen
description: "Konfigurieren Sie die Einstellungen in der Azure Information Protection-Richtlinie, die für alle Benutzer und alle Geräte gelten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
ms.openlocfilehash: 9aeea563b0f77680e79cd7f1808999531f1a5e5c
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-configure-the-policy-settings-for-azure-information-protection"></a>Konfigurieren der Richtlinieneinstellungen für Azure Information Protection

>*Gilt für: Azure Information Protection*

Zusätzlich zum Titel und der QuickInfo für die Information Protection-Leiste gibt es vier Einstellungen in der Azure Information Protection-Richtlinie, die für alle Benutzer und alle Geräte gelten:

![Globale Richtlinieneinstellungen für Azure Information Protection](../media/info-protect-policy-settings.png)


So konfigurieren Sie diese Einstellungen:

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn diese Einstellungen, die Sie konfigurieren möchten, für alle Benutzer gelten sollen, konfigurieren Sie die folgenden globalen Einstellungen auf dem Blatt **Policy:Global** (Richtlinie: Global):

    - **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen): Bei Festlegung dieser Option auf **On** (Ein) muss auf alle gespeicherten Dokumente und gesendeten E-Mails eine Bezeichnung angewendet werden. Die Bezeichnung kann manuell von einem Benutzer, automatisch als Ergebnis einer erfüllten [Bedingung](configure-policy-classification.md) oder standardmäßig (durch Festlegung der Option **Select the default label** [Standardbezeichnung auswählen]) zugewiesen werden. 

    Wenn beim Speichern eines Dokuments oder beim Senden einer E-Mail keine Bezeichnung zugewiesen wird, wird der Benutzer zur Auswahl einer Bezeichnung aufgefordert:

    ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-enforce-label.png)

    - **Select the default label** (Standardbezeichnung auswählen): Wählen Sie bei Festlegung dieser Option die Bezeichnung aus, die Dokumenten und E-Mails zugewiesen werden sollen, die nicht über eine Bezeichnung verfügen. Bezeichnungen mit untergeordneten Bezeichnungen können nicht als Standardbezeichnungen festgelegt werden. 

    - **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten**: Ist diese Option auf **Ein** festgelegt und der Benutzer führt eine dieser Aktionen aus (z.B. Ändern der Bezeichnung von **Secret** auf **Personal**), so wird er aufgefordert, eine Begründung für diese Aktion anzugeben. Der Benutzer kann z. B. angeben, dass das Dokument keine sensiblen Informationen mehr enthält. Die Aktion und die Begründung werden im lokalen Windows-Ereignisprotokoll des Benutzers protokolliert: **Anwendung** > **Microsoft Azure Information Protection**.  

    ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-lower-justification.png)

    Diese Option gilt nicht für untergeordnete Bezeichnungen.

    - **Geben Sie eine benutzerdefinierte URL für die „Weitere Infos“-Webseite des Azure Information Protection-Clients an**: Benutzer sehen diesen Link im Dialogfeld **Microsoft Azure Information Protection** im Abschnitt **Hilfe und Feedback** Abschnitt, wenn sie in ihren Office-Clientanwendungen auf der Registerkarte **Startseite** die Option **Schützen** > **Hilfe und Feedback** auswählen. Standardmäßig gelangen Sie über diesen Link zur [Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection)-Website. Sie können eine HTTP- oder HTTPS-URL (empfohlen) eingeben, wenn dieser Link auf eine andere Webseite verweisen soll. Es wird nicht überprüft, ob die eingegebene benutzerdefinierte URL erreichbar ist oder auf allen Geräten ordnungsgemäß angezeigt wird.
        
        Sie könnten beispielsweise für Ihr Helpdesk die Seite der Microsoft-Dokumentation eingeben, die Informationen zum Installieren und Verwenden des Clients enthält (**https://docs.microsoft.com/information-protection/rms-client/info-protect-client**) oder Informationen zur Version (**https://docs.microsoft.com/information-protection/rms-client/client-version-release-history**). Alternativ können Sie eine eigene Webseite veröffentlichen, die Benutzern Informationen zur Kontaktaufnahme mit Ihrem Helpdesk bereitstellt oder ein Video enthält, das Benutzern zeigt, wie die konfigurierten Bezeichnungen verwendet werden.
        
     Diese Einstellungen können für bestimmte Benutzer überschrieben werden, wenn Sie eine [bereichsbezogene Richtlinie](configure-policy-scope.md) erstellt haben. Um diese Einstellungen in einer bereichsbezogenen Richtlinie zu konfigurieren, wählen Sie zuerst die bereichsbezogene Richtlinie auf dem ersten Blatt **Azure Information Protection** aus.

3. Klicken Sie auf **Save** (Speichern), um Ihre Änderungen zu speichern.

4. Klicken Sie auf dem anfänglichen Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
