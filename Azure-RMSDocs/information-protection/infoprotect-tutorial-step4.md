---
title: "Schnellstart-Tutorial für Azure Information Protection Schritt 4 | Azure Rights Management"
description: "Schritt 4 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in 4 Schritten und weniger als 15 Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 468748c1-49d6-4c3e-a612-9c584acdc782
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: cdd8dee1837c34caaeb0f8a1947dea37504e422a


---

# Schritt 4: Klassifizierung, Bezeichnung und Schutz in Aktion 

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Nun, da Sie ein Word-Dokument mit dem installierten Azure Information Protection-Client geöffnet haben, können Sie sehen, wie einfach das Bezeichnen und Schützen Ihres Dokuments, mithilfe der Richtlinie ist, die wir konfiguriert haben.

Die Klassifizierung und der Schutz treten in Kraft, wenn Sie das Dokument speichern. Bevor wir dies jedoch tun, verwenden wir unser nicht gespeichertes Dokument und können testen, wie einfach es ist, Bezeichnungen anzuwenden und zu ändern.

### So ändern wir unsere Standardbezeichnung manuell:

- Klicken Sie auf der Leiste „Information Protection“ auf das Symbol „Edit label“ (Bezeichnung bearbeiten) neben **Internal** (Intern). Dadurch werden die verfügbaren Bezeichnungen angezeigt. Wählen Sie **Personal** (Privat) aus. Sie werden dazu aufgefordert, zu begründen, warum Sie die Klassifizierungsstufe heruntersetzen. Wählen Sie **This file no longer requires that classification** (Diese Datei benötigt nicht länger diese Klassifizierung) und klicken Sie auf **Confirm** (Bestätigen).  

    Der Wert **Sensitivity** (Vertraulichkeit) wird zu **Personal** (Privat) geändert.

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Bestätigungsaufforderung bei Reduzierung](../media/confirm-lowering.png)

### So entfernen Sie die Klassifizierung vollständig:

- Klicken Sie auf der Leiste „Information Protection“ auf das Symbol „Edit label“ (Bezeichnung bearbeiten) neben **Personal** (Privat). Dadurch werden die verfügbaren Bezeichnungen angezeigt. Klicken Sie dieses mal anstatt auf eine der Bezeichnungen auf das Bezeichnungssymbol „Remove“ (Entfernen). Klicken Sie zum Bestätigen auf **OK**, und geben Sie für diesen Schritt eine Begründung ein.  

    Der Wert **Sensitivity** wird mit **Not set** (Nicht festgelegt) angezeigt. Dies sehen Benutzer zunächst, wenn Sie keine Standardbezeichnung festlegen.

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Entfernen der Klassifizierung](../media/sensitivity-not-set.png)


### Anzeigen einer Empfehlungsaufforderung für die Bezeichnung und den automatischen Schutz:

1. Geben Sie im Word-Dokument eine gültige Kreditkartennummer ein, zum Beispiel: **4242-4242-4242-4242**. 

2. Speichern Sie das Dokument (verwenden Sie einen beliebigen Dateinamen und einen beliebigen Speicherort). 

3. Sie sehen nun die Aufforderung: **It is recommended to label this file as Confidential** (Es wird empfohlen, diese Datei als „Confidential“ (Vertraulich) zu bezeichnen). Klicken Sie auf **Change now** (Jetzt ändern).

    ![Schnellstart-Tutorial für Azure Information Protection Schritt 4 – Empfehlungsaufforderung](../media/change-now.png)

    Zusätzlich zum Fußzeilenbereich **Sensitivity: Confidential** wird sofort das Wasserzeichen Ihres Organisationsnamens auf der Seite angezeigt. 

    Wenn Sie die sich dazu entscheiden, die Option auszuwählen eine RMS-Vorlage anzuwenden, wird das Dokument ebenso mit der angegebenen Azure Rights Management-Vorlage geschützt. Klicken Sie zum Bestätigen auf die Registerkarte **Datei**, und zeigen Sie die Information für **Protect Document** (Dokument schützen) an. Wenn Sie die Standardvorlage „Confidential“ verwendet haben, erhalten Sie die Information, dass das Dokument auf interne Benutzer beschränkt ist (Benutzer außerhalb Ihrer Organisation können das Dokument nicht öffnen) und dessen Inhalte nicht kopiert oder gedruckt werden können. Als Besitzer des Dokuments können Sie daraus kopieren und es drucken, aber wenn Sie es an einen anderen Benutzer in Ihrer Organisation per E-Mail senden, kann dieser Benutzer diese Vorgänge nicht durchführen.

> [!NOTE]
>Falls Sie Probleme beim Fertigstellen dieser Schritte haben, klicken Sie auf der Registerkarte **Home** (Start) in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen) und anschließend auf **Help and feedback** (Hilfe und Feedback). 
>
>Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **Send feedback** (Feedback senden). Dadurch senden Sie eine E-Mail an das Information Protection-Team, wobei automatisch Protokolldateien von Ihrem PC angehängt werden, die dabei helfen sollen, das Problem zu diagnostizieren.

##  Nächste Schritte

Nun, da Sie die standardmäßige Azure Information Protection-Richtlinie gesehen haben, und jetzt wissen, wie Sie sie anpassen können und wie das Bezeichnen in einem Word-Dokument funktioniert, testen Sie doch einige der anderen Einstellungen und lernen Sie die Funktionsweise der Office-Apps kennen, die Azure Information Protection verwenden: Excel, PowerPoint, Outlook. Falls diese Anwendungen geöffnet waren, als Sie den Azure Information Protection-Client installiert haben, schließen Sie sie, und öffnen Sie sie erneut, bevor Sie sie mit Azure Information Protection verwenden.

Sie können z.B. den Standardtitel von **Sensitivity** auf der Leiste „Information Protection“ in einen beliebigen Titel Ihrer Wahl ändern. Sie können die QuickInfo, die Farben der Bezeichnungen, die Reihenfolge der Bezeichnungen und deren Namen ändern. Sie können neue Bezeichnungen erstellen und Ihre eigenen automatischen Regeln definieren. Sie können Ihre Wasserzeichen optimieren, indem Sie die Größe und Farbe konfigurieren und die Ausrichtung von diagonal zu horizontal ändern.

Wenn Sie mit Excel Wasserzeichen verwenden, beachten Sie, dass sie nur im Modus „Seitenlayout“ und „Seitenansicht“ sichtbar sind, und wenn sie gedruckt werden.

Bei jeder Änderung einer Einstellung der Information Protection-Richtlinie im Azure-Portal, **speichern** Sie die Richtlinie und **veröffentlichen** Sie sie anschließend. Da Sie Änderungen auf mehreren Blätter vornehmen können, wird empfohlen zu überprüfen, ob bei allen Blättern die Schaltfläche **Save** (Speichern) deaktiviert ist. Dies zeigt an, dass es nicht gespeicherte Änderungen gibt. Falls ihre Office-Anwendung geöffnet war, als Sie die neuen Änderungen veröffentlicht haben, schließen Sie Ihre Anwendung, und öffnen Sie sie erneut, um die neueste Richtlinie herunterzuladen.

Wenn Sie Ihre eigenen Tests abgeschlossen haben, kann es für Sie möglicherweise interessant sein, die [häufig gestellten Fragen für Azure Information Protection](faq.md) anzusehen.




<!--HONumber=Jul16_HO5-->


