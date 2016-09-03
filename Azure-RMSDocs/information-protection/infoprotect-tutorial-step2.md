---
title: "Schnellstart-Tutorial für Azure Information Protection Schritt 2 | Azure Rights Management"
description: "Schritt 2 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in 4 Schritten und weniger als 15 Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 08/08/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 679d03c499ccdd044444c73ebef8f59b281278cd


---

# Schritt 2: Konfigurieren und Veröffentlichen der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Obwohl Azure Information Protection eine Standardrichtlinie enthält, die Sie ohne Konfiguration verwenden können, werden wir einen Blick auf die Richtlinie werfen und einige Änderungen vornehmen.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an. Wenn Sie sowohl den Schutz als auch die Klassifizierung und Bezeichnung testen möchten, melden Sie sich als globaler Administrator an, damit Sie die Azure Rights Management-Vorlagen abrufen können.
 
2. Im Hubmenü: Klicken Sie auf **Neu**  >  **Sicherheit und Identität**  >  **Azure Information Protection (Vorschau)**  >  **Erstellen**.

    Dadurch wird das Blatt **Azure Information Protection** erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst nun im Hubmenü aus der Liste unter **Durchsuchen** auswählen. 

    > [!TIP] 
    > Wählen Sie **An das Dashboard anheften** zum Erstellen einer **Azure Information Protection**-Kachel auf Ihrem Dashboard aus, damit Sie den Schritt „Durchsuchen“ bei der nächsten Anmeldung überspringen können.

3.  Lernen Sie nun das Hauptblatt von **Azure Information Protection** kennen, das die automatisch erstellte Standardrichtlinie von Information Protection anzeigt:
    
    - Bezeichnungen für die Klassifizierung: **Personal** (Privat), **Public** (Öffentlich), **Internal** (Intern), **Confidential** (Vertraulich) und **Secret** (Geheim). Lesen Sie die QuickInfo zu jeder Bezeichnung, um die Verwendung jeder einzelnen kennenzulernen. Beachten Sie, dass **Secret** die zwei Unterbezeichnungen **All-Employees** (Alle Mitarbeiter) und **My-Group** (Meine Gruppe) besitzt. Dies ist ein Beispiel für Unterkategorien von Klassifizierungen.

    - In den Standardeinstellungen verfügen die Bezeichnungen **Internal**, **Confidential** und **Secret** über optische Kennzeichnungen (z.B. Kopf- und Fußzeilen sowie Wasserzeichen), und für keine der Bezeichnungen ist ein Schutz festgelegt. Darüber hinaus werden die drei globalen Einstellungen nicht festgelegt, sodass nicht alle Dokumente und E-Mails Bezeichnungen aufweisen müssen. Es gibt keine Standardbezeichnung, und Benutzer müssen keine Begründung dafür geben, wenn sie die Vertraulichkeitsstufe herabsetzen.

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](../media/info-protect-policy.png)

Für unser Tutorial ändern wir einige dieser globalen Einstellungen, damit Sie sehen können, wie diese funktionieren:

-  **Select the default label** (Standardbezeichnung auswählen): Legen Sie diese Einstellung auf **Internal** fest.

- **Users must provide justification when lowering the sensitivity level** (Benutzer müssen bei der Herabsenkung der Vertraulichkeitsstufe eine Begründung angeben): Legen Sie diese Einstellung auf **On** (An) fest.

Ändern wir nun die Einstellungen einer der Bezeichnungen, und zwar **Confidential**:

1. Klicken Sie auf die Bezeichnung **Confidential**.

2. Im Blatt **Label: Confidential** (Bezeichnung: Vertraulich) werden alle für diese Bezeichnungen verfügbaren Einstellungen angezeigt. Nehmen Sie die folgenden Änderungen vor:

    a. Wenn Sie Azure Rights Managment aktiviert haben: Wenn im Abschnitt **Set RMS template for protecting documents and emails containing this label** (RMS-Vorlage für den Schutz von Dokumenten und E-Mails mit dieser Bezeichnung festlegen) die Option **Select RMS template from** (RMS-Vorlage auswählen aus) angezeigt wird, übernehmen Sie die Standardeinstellung **Azure RMS**. Klicken Sie dann auf das Dropdownfeld für **Select RMS template** (RMS-Vorlage auswählen), und wählen Sie die Standardvorlage **\<your organization name> - Confidential** (<Name Ihrer Organisation> – „Vertraulich“) aus. Wenn der Name Ihrer Organisation beispielsweise „VanArsdel, Ltd“ lautet, wird der Name angezeigt. Wählen Sie **VanArsdel, Ltd - Confidential** aus. Wenn Sie diese Standardvorlage von Azure Rights Management deaktiviert haben, wählen Sie eine alternative Vorlage aus. Wenn Sie jedoch eine Abteilungsvorlage auswählen, sollten Sie sicherstellen, dass Ihr Konto im Bereich enthalten ist.
    
    Wenn Sie Azure Rights Management nicht aktiviert haben, können Sie diese Option nicht verwenden.
    
    b. **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung haben ein Wasserzeichen): Klicken Sie auf **On**, und geben Sie im **Textfeld** den Namen Ihrer Organisation ein. In unserem Beispiel lautet er **VanArsdel, Ltd**. 
    
    c. Klicken Sie auf **Add a new condition** (Eine neue Bedingung hinzufügen), und wählen Sie anschließend auf dem Blatt **Condition** (Bedingung) Folgendes aus:
    
    - **Choose the type of condition** (Bedingungstyp auswählen): **Built-in** (Integriert)
    
    - **Select built-in** (Integriert auswählen): **Credit Card Number** (Kreditkartennummer)
    
    - **Minimum number of occurrences** (Mindestanzahl der Vorkommen): **1**
    
    - **Count occurrences with unique values only** (Nur Vorkommen mit eindeutigen Werten zählen): **On** (Ein)
    
    - Klicken Sie auf **Save** (Speichern), um wieder auf das Blatt **Label: Confidential** zurückzukehren.

3. Auf dem Blatt **Label: Confidential** erkennen Sie, dass **Credit Card Number** als **CONDITION NAME** (Name der Bedingung) angezeigt wird, mit **1** **OCCURRENCES** (Vorkommen).

4. Belassen Sie **Select how this label is applied** (Anwendungsweise dieser Bezeichnung auswählen) bei **Recommended** (Empfohlen).

5. Geben Sie im Textfeld **Enter notes for internal housekeeping** (Notizen für interne Haushaltsführung eingeben) **For testing purposes only** (Ausschließlich für Testzwecke) ein.

6. Klicken Sie auf dem Blatt **Label: Confidential** auf **Save**, und klicken Sie im Hauptblatt **Azure Information Protection** erneut auf **Save**.

7. Da wir nun unsere Änderungen vorgenommen und gespeichert haben, möchten wir sie unseren Benutzern zur Verfügung stellen. Klicken Sie dazu auf **Publish** (Veröffentlichen) und anschließend auf **Yes** (Ja), um zu bestätigen.

![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie konfiguriert](../media/info-protect-policy-configured.png)

Nachdem Sie dieses Tutorial abgeschlossen haben, können Sie das Azure-Portal entweder schließen oder es offen lassen, um zusätzliche Konfigurationsoptionen auszuprobieren.

Da Sie jetzt die Standardrichtlinie kennen und einige Änderungen daran vorgenommen haben, lernen Sie im nächsten Schritt, den Azure Information Protection-Client zu installieren.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zu den Konfigurationsoptionen für die Richtlinie|[Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Schritt 1](infoprotect-tutorial-step1.md)
[Schritt 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Aug16_HO4-->


