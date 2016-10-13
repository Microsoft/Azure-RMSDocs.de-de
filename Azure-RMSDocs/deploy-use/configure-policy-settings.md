---
title: 'Gewusst wie: Konfigurieren der globalen Richtlinieneinstellungen | Azure Information Protection'
description: "Die Azure Information Protection-Richtlinie enthält drei Einstellungen, die für alle Benutzer und alle Geräte gelten."
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: ebb11148718f22c79bb49c82b9855f5e6f2a5b18
ms.openlocfilehash: e1d0c25995c45d72c1467aa1ff8043ca225a8156


---

# Konfigurieren der globalen Richtlinieneinstellungen für Azure Information Protection

>*Gilt für: Azure Information Protection*

Die Azure Information Protection-Richtlinie enthält drei Einstellungen, die für alle Benutzer und alle Geräte gelten:

![Globale Richtlinieneinstellungen für Azure Information Protection](../media/info-protect-policy-settings.png)


So konfigurieren Sie diese Einstellungen:

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Konfigurieren Sie auf dem Blatt **Azure Information Protection** die folgenden globalen Einstellungen:

    - **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen): Bei Festlegung dieser Option auf **On** (Ein) muss auf alle gespeicherten Dokumente und gesendeten E-Mails eine Bezeichnung angewendet werden. Die Bezeichnung kann manuell von einem Benutzer, automatisch als Ergebnis einer erfüllten [Bedingung](configure-policy-classification.md) oder standardmäßig (durch Festlegung der Option **Select the default label** [Standardbezeichnung auswählen]) zugewiesen werden. 

    Wenn beim Speichern eines Dokuments oder beim Senden einer E-Mail keine Bezeichnung zugewiesen wird, wird der Benutzer zur Auswahl einer Bezeichnung aufgefordert:

    ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-enforce-label.png)

    - **Select the default label** (Standardbezeichnung auswählen): Wählen Sie bei Festlegung dieser Option die Bezeichnung aus, die Dokumenten und E-Mails zugewiesen werden sollen, die nicht über eine Bezeichnung verfügen. Bezeichnungen mit untergeordneten Bezeichnungen können nicht als Standardbezeichnungen festgelegt werden. 

    - **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten**: Ist diese Option auf **Ein** festgelegt und der Benutzer führt eine dieser Aktionen aus (z.B. Ändern der Bezeichnung von **Secret** auf **Personal**), so wird er aufgefordert, eine Begründung für diese Aktion anzugeben. Der Benutzer kann z. B. angeben, dass das Dokument keine sensiblen Informationen mehr enthält. Die Aktion und die Begründung werden im lokalen Windows-Ereignisprotokoll des Benutzers protokolliert: **Anwendung** > **Microsoft Azure Information Protection**.  

    ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-lower-justification.png)

    Diese Option gilt nicht für untergeordnete Bezeichnungen.

3. Klicken Sie auf **Save** (Speichern), um Ihre Änderungen zu speichern.

4. Klicken Sie auf **Publish** (Veröffentlichen), um Ihre Änderungen für Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  












<!--HONumber=Sep16_HO4-->


