---
title: Schnellstarttutorial Schritt 4 | Azure Rights Management
description: "Schritt 3 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in ungefähr 30 Minuten für Ihre Organisation testen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: bcf1e9ee7a2d6cf8fb264533f150b350ce0a9e56


---

# <a name="step-4-see-classification-labeling-and-protection-in-action"></a>Schritt 4: Klassifizierung, Bezeichnung und Schutz in Aktion 

>*Gilt für: Azure Information Protection*

Nun, da Sie ein Word-Dokument mit dem installierten Azure Information Protection-Client geöffnet haben, können Sie sehen, wie einfach das Bezeichnen und Schützen Ihres Dokuments, mithilfe der Richtlinie ist, die wir konfiguriert haben.

Die Klassifizierung und der Schutz treten in Kraft, wenn Sie das Dokument speichern. Bevor wir dies jedoch tun, verwenden wir unser nicht gespeichertes Dokument und können testen, wie einfach es ist, Bezeichnungen anzuwenden und zu ändern.

## <a name="to-manually-change-our-default-label"></a>So ändern Sie die Standardbezeichnung manuell

Wählen Sie auf der Information Protection-Leiste die Bezeichnung **Persönlich** aus. Daraufhin werden Sie aufgefordert, die Herabsenkung der Klassifizierungsstufe zu begründen:

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Bestätigungsaufforderung bei Reduzierung](../media/info-protect-lower-justification.png)

Wählen Sie **The previous label no longer applies** (Vorherige Bezeichnung gilt nicht mehr) aus, und klicken Sie auf **Bestätigen**. Der Wert **Sensitivity** (Vertraulichkeit) wird zu **Personal** (Privat) geändert.

## <a name="to-remove-the-classification-completely"></a>So entfernen Sie die Klassifizierung vollständig

Klicken Sie auf der Leiste „Information Protection“ auf das Symbol **Edit label** (Bezeichnung bearbeiten) neben **Personal** (Privat). Dadurch werden die verfügbaren Bezeichnungen angezeigt. Klicken Sie dieses mal anstatt auf eine der Bezeichnungen auf das Symbol **Remove label** (Bezeichnung entfernen). Klicken Sie zum Bestätigen auf **OK**, und geben Sie anschließend für diesen Schritt eine Begründung ein.  

Der Wert **Vertraulichkeit** wird mit **Nicht festgelegt** angezeigt. Dies sehen Benutzer zunächst, wenn Sie keine Standardbezeichnung festlegen:

![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Entfernen der Klassifizierung](../media/sensitivity-not-set.png)


## <a name="to-see-a-recommendation-prompt-for-labeling-and-automatic-protection"></a>So wird eine Empfehlungsaufforderung für die Bezeichnung und den automatischen Schutz angezeigt

1. Geben Sie im Word-Dokument eine gültige Kreditkartennummer ein, zum Beispiel: **4242-4242-4242-4242**. 

2. Speichern Sie das Dokument (verwenden Sie einen beliebigen Dateinamen und einen beliebigen Speicherort). 

3. Sie sehen nun die Aufforderung: **It is recommended to label this file as Confidential** (Es wird empfohlen, diese Datei als „Confidential“ (Vertraulich) zu bezeichnen). Klicken Sie auf **Change now** (Jetzt ändern).

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Empfehlungsaufforderung](../media/change-now.png)

    Zusätzlich zum Dokument mit der Bezeichnung „Confidential“ (Vertraulich) wird sofort das Wasserzeichen Ihrer Organisation auf der Seite angezeigt. Zudem wird die Fußnote **Sensitivity: Confidential** (Vertraulichkeit: Vertraulich) angewendet. 

    Das Dokument ist auch mit der angegebenen Azure Rights Management-Vorlage geschützt. Klicken Sie zum Bestätigen auf die Registerkarte **Datei**, und zeigen Sie die Informationen für **Dokument schützen** an. Wenn Sie die Standardvorlage „Confidential“ verwendet haben, erhalten Sie die Information, dass das Dokument auf interne Benutzer beschränkt ist (Benutzer außerhalb Ihrer Organisation können das Dokument nicht öffnen) und dessen Inhalte nicht kopiert oder gedruckt werden können. Als Besitzer des Dokuments können Sie daraus kopieren und es drucken, aber wenn Sie es an einen anderen Benutzer in Ihrer Organisation per E-Mail senden, kann dieser Benutzer diese Vorgänge nicht durchführen.

Sehen wir uns nach der Klassifizierung, der Bezeichnung und dem Schutz von Dokumenten nun an, wie Sie Ihre Dokumente schützen können, wenn diese für andere Benutzer in einer anderen Organisation freigegeben werden. Sie können sogar nachverfolgen, wie sie verwendet werden und den Zugriff auf diese Dokumente widerrufen.

>[!div class="step-by-step"]
[&#171; Schritt 3](infoprotect-tutorial-step3.md)
[Schritt 5 &#187;](infoprotect-tutorial-step5.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


