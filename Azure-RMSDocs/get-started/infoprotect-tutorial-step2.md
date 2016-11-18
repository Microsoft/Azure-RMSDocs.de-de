---
title: Schnellstarttutorial Schritt 1 | Azure Information Protection
description: "Schritt 2 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in ungefähr 30 Minuten für Ihre Organisation testen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 3c2523119020232b9044506b2d2a602104e81d0b


---

# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Schritt 2: Konfigurieren und Veröffentlichen der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

Obwohl Azure Information Protection eine Standardrichtlinie enthält, die Sie ohne Konfiguration verwenden können, werden wir einen Blick auf die Richtlinie werfen und einige Änderungen vornehmen.

1. Melden Sie sich in einem neuen Browserfenster als globaler Administrator für Ihren Mandanten beim [Azure-Portal](https://portal.azure.com) an.

2. Klicken Sie im Hubmenü auf **Neu**, und wählen Sie dann in der Liste **MARKETPLACE** die Option **Sicherheit und Identität** aus. Wählen Sie auf dem Blatt **Sicherheit und Identität** in der Liste **AUSGEWÄHLTE APPS** die Option **Azure Information Protection** aus. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Erstellen**.

    Dadurch wird das Blatt **Azure Information Protection** erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst im Hubmenü aus der Liste unter **Weitere Dienste** auswählen. 

    > [!TIP] 
    > Wählen Sie **An das Dashboard anheften** zum Erstellen einer **Azure Information Protection**-Kachel auf Ihrem Dashboard aus, damit Sie bei der nächsten Anmeldung nicht erneut nach dem Dienst suchen müssen können.

3.  Lernen Sie nun das Hauptblatt von **Azure Information Protection** kennen, das die automatisch erstellte Standardrichtlinie von Information Protection anzeigt:
    
    - Bezeichnungen für die Klassifizierung: **Personal** (Privat), **Public** (Öffentlich), **Internal** (Intern), **Confidential** (Vertraulich) und **Secret** (Geheim). Lesen Sie die QuickInfo zu jeder Bezeichnung, um die Verwendung jeder einzelnen kennenzulernen. Beachten Sie, dass **Secret** die zwei Unterbezeichnungen **All-Employees** (Alle Mitarbeiter) und **My-Group** (Meine Gruppe) besitzt. Dies ist ein Beispiel für Unterkategorien von Klassifizierungen.

    - In den Standardeinstellungen verfügen die Bezeichnungen **Internal**, **Confidential** und **Secret** über optische Kennzeichnungen (z.B. Kopf- und Fußzeilen sowie Wasserzeichen), und für keine der Bezeichnungen ist ein Schutz festgelegt. Darüber hinaus werden die drei globalen Einstellungen nicht festgelegt, sodass nicht alle Dokumente und E-Mails Bezeichnungen aufweisen müssen. Es gibt keine Standardbezeichnung, und Benutzer müssen keine Begründung angeben, wenn sie die Klassifizierungsstufe herabsetzen.

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](../media/info-protect-policy.png)

## <a name="changing-the-global-settings-for-a-default-template-and-prompt-for-justification"></a>Ändern der globalen Einstellungen für eine Standardvorlage und Aufforderung zur Eingabe einer Begründung

Für unser Tutorial ändern wir einige dieser globalen Einstellungen, damit Sie sehen können, wie diese funktionieren:

1. Legen Sie **Select the default label** (Standardbezeichnung auswählen) auf **Intern** fest.

2. Legen Sie **Users must provide justification to set a lower classification label, remove a label, or remove protection** (Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten) auf **Ein** fest.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Konfigurieren einer Bezeichnung für den Schutz, eines Wasserzeichens und einer Bedingung für die Aufforderung zur Eingabe einer Klassifizierung

Ändern wir nun die Einstellungen einer der Bezeichnungen, und zwar **Confidential**:

1. Klicken Sie auf die Bezeichnung **Confidential**. 
    
    Auf dem neuen Blatt **Label: Confidential** (Bezeichnung: Vertraulich) werden alle für diese Bezeichnungen verfügbaren Einstellungen angezeigt. 

2. Suchen Sie auf dem Blatt **Label: Confidential** (Bezeichnung: Vertraulich) den Abschnitt **Set RMS template for protecting documents and emails containing this label** (RMS-Vorlage für den Schutz von Dokumenten und E-Mails mit dieser Bezeichnung festlegen):
    
    Behalten Sie für die Option **Select RMS template from** (RMS-Vorlage auswählen aus) den Standardwert **Azure RMS** bei. Klicken Sie dann auf das Dropdownfeld für **Select RMS template** (RMS-Vorlage auswählen), und wählen Sie die Standardvorlage **\<your organization name> - Confidential** (<Name Ihrer Organisation> – „Vertraulich“) aus. 
    
    Wenn der Name Ihrer Organisation beispielsweise „VanArsdel, Ltd“ lautet, wird der Name angezeigt. Wählen Sie **VanArsdel, Ltd - Confidential** (VanArsdel, Ltd – Vertraulich) aus: 
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Festlegen des Azure RMS-Schutzes](../media/step2-select-rms-template.png)
    
    Wenn Sie diese Standardvorlage von Azure Rights Management deaktiviert haben, wählen Sie eine alternative Vorlage aus. Wenn Sie jedoch eine Abteilungsvorlage auswählen, sollten Sie sicherstellen, dass Ihr Konto im Bereich enthalten ist.
    
3. Suchen Sie den Abschnitt **Set visual marking** (Visuelle Kennzeichnung festlegen):
    
    Klicken Sie für die Einstellung **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung haben ein Wasserzeichen) auf **Ein**, und geben Sie dann im **Textfeld** den Namen Ihrer Organisation ein. In diesem Beispiel lautet er **VanArsdel, Ltd**: 
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Festlegen des Azure RMS-Schutzes](../media/step2-configure-watermark.png)
    
    Die Größe, die Farbe und das Layout für Wasserzeichen können zwar jeweils geändert werden, wir behalten jedoch hier die Standardwerte bei.
    
4. Suchen Sie den Abschnitt **Configure conditions for automatically applying this label** (Bedingungen konfigurieren, um diese Bezeichnung automatisch anzuwenden):
    
    Klicken Sie auf **Add a new condition** (Eine neue Bedingung hinzufügen), und wählen Sie anschließend auf dem Blatt **Condition** (Bedingung) Folgendes aus:
    
    a. **Choose the type of condition:** (Bedingungstyp auswählen) Behalten Sie den Standardwert **Integriert** bei.
    
    b. **Integriert auswählen:** Wählen Sie in der Dropdownliste die Option **Kreditkartennummer** aus.
    
    c. **Minimum number of occurrences:** (Mindestanzahl der Vorkommen) Behalten Sie den Standardwert **1** bei.
    
    d. **Count occurrences with unique values only:** (Nur Vorkommen mit eindeutigen Werten zählen) Behalten Sie den Standardwert **Aus** bei.
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Konfigurieren der Bedingung für Kreditkarten](../media/step2-configure-condition.png)
    
    Klicken Sie auf **Save** (Speichern), um wieder auf das Blatt **Label: Confidential** zurückzukehren.

5. Auf dem Blatt **Label: Confidential** (Bezeichnung: Vertraulich) können Sie sehen, dass **Kreditkartennummer** als **BEDINGUNGSNAME** angezeigt wird, mit **1** **VORKOMMEN**:
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Konfigurieren der Bedingung für Kreditkarten](../media/step2-see-condition.png)

6. Behalten Sie für **Select how this label is applied** (Anwendungsweise dieser Bezeichnung auswählen) den Standardwert **Empfohlen** bei, und ändern Sie den Tipp für die Standardrichtlinie nicht:
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Empfohlene Klassifizierung](../media/step2-keep-recommended.png)

7. Geben Sie im Textfeld **Enter notes for internal housekeeping** (Notizen für interne Haushaltsführung eingeben) den Wert **For testing purposes only** (Ausschließlich für Testzwecke) ein:
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Eingeben von Notizen](../media/step2-type-notes.png)

8. Klicken Sie auf diesem Blatt **Label: Confidential** (Bezeichnung: Vertraulich) auf **Speichern**. Klicken Sie dann auf dem Hauptblatt **Azure Information Protection** erneut auf **Speichern**.

9. Da wir nun unsere Änderungen vorgenommen und gespeichert haben, möchten wir sie unseren Benutzern zur Verfügung stellen. Klicken Sie dazu auf **Publish** (Veröffentlichen) und anschließend auf **Yes** (Ja), um zu bestätigen.

![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie konfiguriert](../media/info-protect-policy-configured.png)

Nachdem Sie dieses Tutorial abgeschlossen haben, können Sie das Azure-Portal entweder schließen oder es offen lassen, um zusätzliche Konfigurationsoptionen auszuprobieren.

Da Sie jetzt die Standardrichtlinie kennen und einige Änderungen daran vorgenommen haben, lernen Sie im nächsten Schritt, wie der Azure Information Protection-Client und die Rights Management-Freigabeanwendung installiert werden.

|Weitere Informationen zu|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zu den Konfigurationsoptionen für die Richtlinie|[Konfigurieren der Azure Information Protection-Richtlinie](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Schritt 1](infoprotect-tutorial-step1.md)
[Schritt 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Nov16_HO2-->


