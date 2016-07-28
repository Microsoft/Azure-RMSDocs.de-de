---
title: "Schnellstart-Tutorial für Azure Information Protection Schritt 2 | Azure Rights Management"
description: "Schritt 2 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in 4 Schritten und weniger als 15 Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 07/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
translationtype: Human Translation
ms.sourcegitcommit: 463c0bc1fa86f73e2623faf5a624afeabcadeedb
ms.openlocfilehash: c6ecf22b72d862c605f8be2ab1f75fd2126f8575


---

# Schritt 2: Konfigurieren und Veröffentlichen der Azure Information Protection-Richtlinie

*Gilt für: Azure Information Protection (Preview)*

Obwohl Azure Information Protection eine Standardrichtlinie enthält, die Sie ohne Konfiguration verwenden können, werden wir einen Blick auf die Richtlinie werfen und einige Änderungen vornehmen.

1. Melden Sie sich mithilfe dieses Links im Azure-Portal an, um Azure Information Protection zu verwenden: https://portal.azure.com/?microsoft_azure_informationprotection=true
 
2. Klicken Sie anschließend im Hubmenü auf **Durchsuchen**, und geben Sie **Information** im Filterfeld ein. Wählen Sie **Azure Information Protection** aus.

- Nun sehen Sie das Hauptblatt von **Azure Information Protection**, das die automatisch erstellte Standardrichtlinie von Information Protection anzeigt. Diese Standardrichtlinie enthält die folgenden Bezeichnungen für die Klassifizierung: **Personal** (Privat), **Public** (Öffentlich), **Internal** (Intern), **Confidential** (Vertraulich) und **Secret** (Geheim). Lesen Sie die QuickInfo zu jeder Bezeichnung, um die Verwendung jeder einzelnen kennenzulernen. Beachten Sie, dass **Secret** die zwei Unterbezeichnungen **All-Employees** (Alle Mitarbeiter) und **My-Group** (Meine Gruppe) besitzt. Dies ist ein Beispiel für Unterkategorien von Klassifizierungen.

- In ihren Standardeinstellungen verfügen die Bezeichnungen **Internal**, **Confidential** und **Secret** über optische Kennzeichnungen (z.B. Kopf- und Fußzeilen sowie Wasserzeichen), und für keine der Bezeichnungen ist ein Schutz festgelegt. Darüber hinaus werden die drei globalen Einstellungen nicht festgelegt, sodass nicht alle Dokumente und E-Mails Bezeichnungen aufweisen müssen. Es gibt keine Standardbezeichnung, und Benutzer müssen keine Begründung dafür geben, wenn sie die Vertraulichkeitsstufe herabsetzen.

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](../media/info-protect-policy.png)

Für unser Tutorial ändern wir einige dieser globalen Einstellungen, damit Sie sehen können, wie diese funktionieren:

-  **Select the default label** (Standardbezeichnung auswählen): Legen Sie diese Einstellung auf **Internal** fest.

- **Users must provide justification when lowering the sensitivity level** (Benutzer müssen bei der Herabsenkung der Vertraulichkeitsstufe eine Begründung angeben): Legen Sie diese Einstellung auf **On** (An) fest.

Ändern wir nun die Einstellungen einer der Bezeichnungen, und zwar **Confidential**:

1. Klicken Sie auf den Eintrag der Bezeichnung **Confidential**.

2. Im Blatt **Label: Confidential** (Bezeichnung: Vertraulich) werden alle für diese Bezeichnungen verfügbaren Einstellungen angezeigt. Nehmen Sie die folgenden Änderungen vor:

    a. Wenn Sie Azure Rights Management aktiviert haben, gehen Sie für **Select RMS template** (RMS-Vorlage auswählen) wie folgt vor: Klicken Sie auf das Dropdownfeld, und wählen Sie die Standardvorlage **\<Your Organization Name > Confidential** (Name Ihrer Organisation > Vertraulich) aus. Wenn der Name Ihrer Organisation beispielsweise „VanArsdel, Ltd“ lautet, wird der Name angezeigt. Wählen Sie **VanArsdel, Ltd - Confidential** aus. Wenn Sie diese Standardvorlage von Azure Rights Management deaktiviert haben, wählen Sie eine alternative Vorlage aus. Wenn Sie jedoch eine Abteilungsvorlage auswählen, sollten Sie sicherstellen, dass Ihr Konto im Bereich enthalten ist.

    Wenn Sie Azure Rights Management nicht aktiviert haben, können Sie diese Option nicht verwenden.

    b. **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung haben ein Wasserzeichen): Klicken Sie auf **On**, und geben Sie im **Textfeld** den Namen Ihrer Organisation ein. In unserem Beispiel lautet er **VanArsdel, Ltd**. 

    c. Klicken Sie auf **Add a new condition** (Eine neue Bedingung hinzufügen), und wählen Sie anschließend auf dem Blatt **Condition** (Bedingung) Folgendes aus:

    - **Choose the type of condition** (Bedingungstyp auswählen): **Built-in** (Integriert)

    - **Select built-in** (Integriert auswählen): **Credit Card Number** (Kreditkartennummer)

    - **Minimum number of occurrences** (Mindestanzahl der Vorkommen): **1**

    - Klicken Sie auf **Save** (Speichern), um wieder auf das Blatt **Label: Confidential** zurückzukehren.

3. Auf dem Blatt **Label: Confidential** erkennen Sie, dass **Credit Card Number** als **CONDITION NAME** (Name der Bedingung) angezeigt wird, mit **1** **OCCURRENCES** (Vorkommen).

4. Belassen Sie **Select how this label is applied** (Anwendungsweise dieser Bezeichnung auswählen) bei **Recommended** (Empfohlen).

5. Geben Sie im Textfeld **Enter notes for internal housekeeping** (Notizen für interne Haushaltsführung eingeben) **For testing purposes only** (Ausschließlich für Testzwecke) ein.

6. Klicken Sie auf dem Blatt **Label: Confidential** auf **Save**, und klicken Sie im Hauptblatt **Azure Information Protection** erneut auf **Save**.

7. Da wir nun unsere Änderungen vorgenommen und gespeichert haben, möchten wir sie unseren Benutzern zur Verfügung stellen. Klicken Sie dazu auf **Publish** (Veröffentlichen) und anschließend auf **Yes** (Ja), um zu bestätigen.

![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie konfiguriert](../media/info-protect-policy-configured.png)

Nachdem Sie dieses Tutorial abgeschlossen haben, können Sie das Azure-Portal entweder schließen oder es offen lassen, um zusätzliche Konfigurationsoptionen auszuprobieren.

Da Sie jetzt die Standardrichtlinie kennen und einige Änderungen daran vorgenommen haben, lernen Sie im nächsten Schritt, den Azure Information Protection-Client zu installieren.


>[!div class="step-by-step"]
[&#171; Schritt 1](infoprotect-tutorial-step1.md)
[Schritt 3 &#187;](infoprotect-tutorial-step3.md)


<!--HONumber=Jul16_HO3-->


