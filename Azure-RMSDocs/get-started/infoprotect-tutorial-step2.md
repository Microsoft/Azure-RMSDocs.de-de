---
title: "Schnellstart-Tutorial Schritt 2 – AIP"
description: "Schritt 2 eines Einführungstutorials zum schnellen Ausprobieren von Azure Information Protection – Konfigurieren der Richtlinie"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/21/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 3bc193c2-0be0-4c8e-8910-5d2cee5b14f7
ms.openlocfilehash: 7db581d07698edf50fda8379d622e35414ad3671
ms.sourcegitcommit: f0402cf14506b4c61a156a2baf7e69b7b16883a1
translationtype: HT
---
# <a name="step-2-configure-and-publish-the-azure-information-protection-policy"></a>Schritt 2: Konfigurieren und Veröffentlichen der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

Obwohl Azure Information Protection eine Standardrichtlinie enthält, die Sie ohne Konfiguration verwenden können, werden wir einen Blick auf die Richtlinie werfen und einige Änderungen vornehmen.

1. Melden Sie sich in einem neuen Browserfenster als globaler Administrator für Ihren Mandanten beim [Azure-Portal](https://portal.azure.com) an.

2. Klicken Sie im Hubmenü auf **Neu**, und wählen Sie dann in der Liste **MARKETPLACE** die Option **Sicherheit und Identität** aus. Wählen Sie auf dem Blatt **Sicherheit und Identität** in der Liste **AUSGEWÄHLTE APPS** die Option **Azure Information Protection** aus. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Erstellen**.

    Dadurch wird der Dienst für Ihren Mandanten aktiviert und das Blatt **Azure Information Protection** erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst im Hubmenü aus der Liste unter **More services** (Weitere Dienste) auswählen. 

    > [!TIP] 
    > Wählen Sie **An das Dashboard anheften** zum Erstellen einer **Azure Information Protection**-Kachel auf Ihrem Dashboard aus, damit Sie bei der nächsten Anmeldung nicht erneut nach dem Dienst suchen müssen können.

3.  Klicken Sie auf dem Azure Information Protection-Blatt auf **Global**, und untersuchen Sie das Blatt **Policy: Global** (Richtlinie: Global), das die für Ihren Mandanten automatisch erstellte Standardrichtlinie von Information Protection anzeigt.
    
    Auf dem Blatt **Policy: Global** (Richtlinie: Global) sehen Sie Folgendes:
    
    - Bezeichnungen für die Klassifizierung: **Personal** (Persönlich), **Public** (Öffentlich), **General** (Allgemein), **Confidential** (Vertraulich) und **Highly Confidential** (Streng vertraulich). Beachten Sie, dass die beiden letzten Bezeichnungen erweitert werden können, um untergeordnete Bezeichnungen anzuzeigen: **All Employees** (Alle Mitarbeiter) und **Anyone (not protected)** (Jeder (nicht geschützt)) sind Beispiele für eine Klassifizierung mit Unterkategorien.
    
       > [!NOTE]
       > Die Standardrichtlinie kann etwas anders aussehen als in diesem Tutorial. Zum Beispiel kann eine Bezeichnung **Internal** (Intern) heißen anstatt **General** (Allgemein) und **Secret** (Geheim) anstatt **Highly Confidential** (Streng vertraulich). Wenn dies der Fall ist, verwenden Sie wahrscheinlich eine ältere Version der Richtlinie. Oder Sie haben sie möglicherweise vor dem Start des Tutorials selbst bearbeitet.
       > 
       > Wenn die Standardrichtlinie anders aussieht, können Sie dieses Tutorial dennoch verwenden, sollten sich dieser Änderungen aber bei den folgenden Anweisungen und Abbildungen bewusst sein. Wenn Sie die Standardrichtlinie ändern möchten, damit sie der aktuellen Standardrichtlinie entspricht, finden Sie dazu Informationen unter [Die Azure Information Protection-Standardrichtlinie](../deploy-use/configure-policy-default.md).

    - In der Standardkonfiguration verfügen einige Bezeichnungen nicht über optische Kennzeichnungen (z.B. Kopf- und Fußzeilen sowie Wasserzeichen), und für keine der Bezeichnungen ist ein Schutz festgelegt: 
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](../media/info-protect-policy-default-labelsv2.png)
    
    Darüber hinaus werden einige Richtlinieneinstellungen nicht festgelegt, sodass zum Beispiel nicht alle Dokumente und E-Mails Bezeichnungen aufweisen müssen, es keine Standardbezeichnung gibt und Benutzer keine Begründung angeben müssen, wenn sie Bezeichnungen ändern:
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie](../media/info-protect-policy-default-settings.png)

## <a name="changing-the-settings-for-a-default-label-and-prompt-for-justification"></a>Ändern der Einstellungen für eine Standardbezeichnung und Aufforderung zur Eingabe einer Begründung

Für unser Tutorial ändern wir einige dieser Richtlinieneinstellungen, damit Sie sehen, wie diese funktionieren:

1. Legen Sie **Select the default label** (Standardbezeichnung auswählen) auf **General** (Allgemein) fest. 

    Wenn Sie nicht über diese Bezeichnung verfügen, da Sie eine ältere Version der Richtlinie verwenden, wählen Sie **Internal** (Intern) als entsprechende Bezeichnung.

2. Legen Sie **Users must provide justification to set a lower classification label, remove a label, or remove protection** (Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten) auf **Ein** fest.

## <a name="configuring-a-label-for-protection-a-watermark-and-a-condition-to-prompt-for-classification"></a>Konfigurieren einer Bezeichnung für den Schutz, eines Wasserzeichens und einer Bedingung für die Aufforderung zur Eingabe einer Klassifizierung

Wir ändern nun die Einstellungen der untergeordneten Bezeichnung **All Employees** (Alle Mitarbeiter) aus der Hauptbezeichnung **Confidential** (Vertraulich). 

Wenn die Bezeichnung **Confidential** (Vertraulich) nicht über untergeordnete Bezeichnungen verfügt, da Sie eine ältere Version der Richtlinie haben, können Sie stattdessen die Bezeichnung **Confidential** (Vertraulich) verwenden. Die Konfigurationsschritte sind dieselben, aber das Bezeichnungsblatt heißt **Confidential** (Vertraulich) anstatt **All Employees** (Alle Mitarbeiter).

1. Stellen Sie sicher, dass die Bezeichnung **Confidential** (Vertraulich) erweitert ist, und wählen Sie dann aus dieser Bezeichnung **All Employees** (Alle Mitarbeiter) aus.
    
    Auf dem neuen Blatt **Label: All Employees** (Bezeichnung: Alle Mitarbeiter) werden alle für diese Bezeichnungen verfügbaren Einstellungen angezeigt. 

2. Lesen Sie den **Beschreibungstext** für diese Bezeichnung. Darin wird beschrieben, wie die ausgewählte Bezeichnung verwendet werden soll; er wird Benutzern als QuickInfo angezeigt, um ihnen bei der Auswahl der Bezeichnung zu helfen.

3. Gehen Sie zum Abschnitt **Set permissions for documents and emails containing this label** (Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen) und wählen Sie **Protect** (Schützen):
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-barv2.png) 
    
    Daraufhin öffnet sich das Blatt **Schutz**.
    
3. Vergewissern Sie sich, dass im Blatt **Schutz** die Optionen **Azure RMS** und **Vorlage auswählen** ausgewählt sind. Klicken Sie dann auf das Dropdownfeld, und wählen Sie die Standardvorlage **\<Name Ihrer Organisation> – Vertraulich** aus.     
    
    Wenn der Name Ihrer Organisation beispielsweise „VanArsdel, Ltd“ lautet, wird der Name angezeigt. Wählen Sie **VanArsdel, Ltd - Confidential** (VanArsdel, Ltd – Vertraulich) aus: 
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Festlegen des Azure RMS-Schutzes](../media/step2-select-rms-template.png)
    
    Wenn Sie diese Standardvorlage von Azure Rights Management deaktiviert haben, wählen Sie eine alternative Vorlage aus. Wenn Sie jedoch eine Abteilungsvorlage auswählen, sollten Sie sicherstellen, dass Ihr Konto im Bereich enthalten ist.
    
4. Klicken Sie auf **OK**, um die Änderungen zu speichern und das Blatt **Protection** (Schutz) zu schließen. Ihre Konfiguration wird auf dem Blatt **Label: All Employees** (Bezeichnung: Alle Mitarbeiter) angezeigt:
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Azure RMS-Schutz konfiguriert](../media/protection-bar-configured.png)
    
5. Suchen Sie nun auf dem Blatt **Label: All Employees** (Bezeichnung: Alle Mitarbeiter) den Abschnitt **Set visual marking** (Optische Kennzeichnung festlegen):
    
    Klicken Sie für die Einstellung **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung haben ein Wasserzeichen) auf **Ein**, und geben Sie dann im **Textfeld** den Namen Ihrer Organisation ein. In diesem Beispiel lautet er **VanArsdel, Ltd**: 
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Festlegen des Azure RMS-Schutzes](../media/step2-configure-watermark.png)
    
    Die Größe, die Farbe und das Layout für Wasserzeichen können zwar jeweils geändert werden, wir behalten jedoch hier die Standardwerte bei.
    
6. Suchen Sie den Abschnitt **Configure conditions for automatically applying this label** (Bedingungen konfigurieren, um diese Bezeichnung automatisch anzuwenden):
    
    Klicken Sie auf **Add a new condition** (Eine neue Bedingung hinzufügen), und wählen Sie anschließend auf dem Blatt **Condition** (Bedingung) Folgendes aus:
    
    a. **Choose the type of condition:** (Bedingungstyp auswählen) Behalten Sie den Standardwert **Integriert** bei.
    
    b. **Integriert auswählen:** Wählen Sie in der Dropdownliste die Option **Kreditkartennummer** aus.
    
    c. **Minimum number of occurrences:** (Mindestanzahl der Vorkommen) Behalten Sie den Standardwert **1** bei.
    
    d. **Count occurrences with unique values only:** (Nur Vorkommen mit eindeutigen Werten zählen) Behalten Sie den Standardwert **Aus** bei.
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Konfigurieren der Bedingung für Kreditkarten](../media/step2-configure-condition.png)
    
    Klicken Sie auf **Speichern**, um wieder auf das Blatt **Label: All Employees** (Bezeichnung: Alle Mitarbeiter) zurückzukehren.

7. Auf dem Blatt **Label: All Employees** (Bezeichnung: Alle Mitarbeiter) können Sie sehen, dass **Credit Card Number** (Kreditkartennummer) als **CONDITION NAME** (BEDINGUNGSNAME) angezeigt wird, mit **1** **OCCURRENCES** (VORKOMMEN):
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Konfigurieren der Bedingung für Kreditkarten](../media/step2-see-condition.png)

8. Behalten Sie für **Select how this label is applied** (Anwendungsweise dieser Bezeichnung auswählen) den Standardwert **Empfohlen** bei, und ändern Sie den Tipp für die Standardrichtlinie nicht:
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Empfohlene Klassifizierung](../media/step2-keep-recommendedv2.png)

9. Geben Sie im Textfeld **Enter notes for internal housekeeping** (Notizen für interne Haushaltsführung eingeben) den Wert **For testing purposes only** (Ausschließlich für Testzwecke) ein:
    
    ![Schnellstarttutorial für Azure Information Protection Schritt 3 – Eingeben von Notizen](../media/step2-type-notes.png)

10. Klicken Sie auf diesem Blatt **Label: All Employees** (Bezeichnung: Alle Mitarbeiter) auf **Speichern**. Klicken Sie dann auf dem Blatt **Policy: Global** (Richtlinie: Global) erneut auf **Speichern**.
    
    Nun wird in der Liste Ihrer Bezeichnungen unter „Protection“ (Schutz) für die gerade geänderte Bezeichnung „Azure RMS“ angezeigt:

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Standardrichtlinie konfiguriert](../media/info-protect-policy-configuredv2.png)
    
    Die Einstellungen werden mit Ihren Änderungen für die Standardbezeichnung und mit Ihrer Begründung konfiguriert:
    
    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – Einstellungen konfiguriert](../media/info-protect-settings-configuredv2.png)
    
11. Da wir nun unsere Änderungen vorgenommen und gespeichert haben, möchten wir sie unseren Benutzern zur Verfügung stellen. Klicken Sie dazu auf dem ersten **Azure Information Protection**-Blatt auf **Publish** (Veröffentlichen) und anschließend auf **Yes** (Ja), um zu bestätigen.

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 3 – konfigurierte Richtlinie veröffentlichen](../media/info-protect-publish.png)

Nachdem Sie dieses Tutorial abgeschlossen haben, können Sie das Azure-Portal entweder schließen oder es offen lassen, um zusätzliche Konfigurationsoptionen auszuprobieren.

Da Sie jetzt die Standardrichtlinie kennen und einige Änderungen daran vorgenommen haben, lernen Sie im nächsten Schritt, den Azure Information Protection-Client zu installieren.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Informationen zu den Konfigurationsoptionen für die Richtlinie|[Konfigurieren der Azure Information Protection-Richtlinie](../deploy-use/configure-policy.md)|


>[!div class="step-by-step"]
[&#171; Schritt 1](infoprotect-tutorial-step1.md)
[Schritt 3 &#187;](infoprotect-tutorial-step3.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]