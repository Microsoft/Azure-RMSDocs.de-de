---
title: "Konfigurieren der globalen Richtlinieneinstellungen für Azure Information Protection | Azure Rights Management"
description: "Die Azure Information Protection-Richtlinie enthält drei Einstellungen, die für alle Benutzer und alle Geräte gelten."
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 629815c0-457d-4697-a4cc-df0e6cc0c1a6
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: c48f5488e49a54b970f76012e0f2f17fe4158691


---

# Konfigurieren der globalen Richtlinieneinstellungen für Azure Information Protection

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Die Azure Information Protection-Richtlinie enthält drei Einstellungen, die für alle Benutzer und alle Geräte gelten:

![Globale Richtlinieneinstellungen für Azure Information Protection](../media/info-protect-policy-settings.png)


So konfigurieren Sie diese Einstellungen:

1. Falls Sie sich noch nicht im [Azure-Portal](https://portal.azure.com) angemeldet haben, tun Sie dies, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Durchsuchen**, und geben Sie **Information** im Filterfeld ein. Wählen Sie **Azure Information Protection** aus.

2. Konfigurieren Sie auf dem Blatt **Azure Information Protection** die folgenden globalen Einstellungen:

    - **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen): Bei Festlegung dieser Option auf **On** (Ein) muss auf alle gespeicherten Dokumente und gesendeten E-Mails eine Bezeichnung angewendet werden. Die Bezeichnung kann manuell von einem Benutzer, automatisch als Ergebnis einer erfüllten [Bedingung](configure-policy-classification.md) oder standardmäßig (durch Festlegung der Option **Select the default label** [Standardbezeichnung auswählen]) zugewiesen werden. 

    Wenn beim Speichern eines Dokuments oder beim Senden einer E-Mail keine Bezeichnung zugewiesen wird, wird der Benutzer zur Auswahl einer Bezeichnung aufgefordert:

    ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-enforce-label.png)

    - **Select the default label** (Standardbezeichnung auswählen): Wählen Sie bei Festlegung dieser Option die Bezeichnung aus, die Dokumenten und E-Mails zugewiesen werden sollen, die nicht über eine Bezeichnung verfügen. Bezeichnungen mit untergeordneten Bezeichnungen können nicht als Standardbezeichnungen festgelegt werden. 

    - **Users must provide justification when lowering the sensitivity level** (Benutzer müssen bei der Herabsenkung der Vertraulichkeitsstufe eine Begründung angeben): Wenn Sie diese Option auf **On** (Ein) festlegen und ein Benutzer die Bezeichnung eines vorhandenen Dokuments oder einer vorhandenen E-Mail in eine Bezeichnung mit niedrigerer Vertraulichkeitsstufe ändert (z. B. von **Secret** [Geheim] in **Public** [Öffentlich]), muss der Benutzer eine Begründung für diese Änderung angeben. Der Benutzer kann z. B. angeben, dass das Dokument keine sensiblen Informationen mehr enthält. Die Aktion und die Begründung werden im lokalen Windows-Ereignisprotokoll des Benutzers protokolliert: **Anwendung** > **Microsoft Azure Information Protection**.  

    ![Azure Information Protection-Aufforderung, wenn die neue Klassifizierung eine niedrigere Vertraulichkeitsstufe aufweist](../media/info-protect-lower-justification.png)

    Diese Option gilt nicht für untergeordnete Bezeichnungen.

3. Klicken Sie auf **Save** (Speichern), um Ihre Änderungen zu speichern.

4. Klicken Sie auf **Publish** (Veröffentlichen), um Ihre Änderungen für Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  












<!--HONumber=Aug16_HO4-->


