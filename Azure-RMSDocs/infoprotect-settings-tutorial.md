---
title: 'Tutorial: Verwenden von Azure Information Protection-Richtlinieneinstellungen zum Klassifizieren von Daten'
description: Ein Einführungstutorial, das Sie schrittweise durch das Konfigurieren von Azure Information Protection-Richtlinieneinstellungen führt, um Dokumente und E-Mails Ihrer Organisation besser zu klassifizieren.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/20/2019
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: f2aa0d6b7068488212697f6f2f2e9b1d19c9d131
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68794055"
---
# <a name="tutorial-configure-azure-information-protection-policy-settings-that-work-together"></a>Tutorial: Konfigurieren von Azure Information Protection-Richtlinieneinstellungen, die nahtlos funktionieren

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> * Konfigurieren von Richtlinieneinstellungen, die nahtlos funktionieren
> * Testen Ihrer Einstellungen

Statt sich darauf zu verlassen, dass Benutzer ihre Dokumente und E-Mails manuell bezeichnen, können Sie mithilfe von Richtlinieneinstellungen Folgendes erreichen:

- Sicherstellen, dass ein grundlegendes Maß an Klassifizierung für neue und bearbeitete Inhalte eingehalten wird

- Informieren von Benutzern über Bezeichnungen und Vereinfachung der Anwendung der richtigen Bezeichnung

Für dieses Tutorial benötigen Sie etwa 15 Minuten.

## <a name="prerequisites"></a>Voraussetzungen 

Voraussetzungen für dieses Tutorial:

1. Ein Abonnement, das Azure Information Protection-Plan 1 oder -Plan 2 beinhaltet.
    
    Wenn Sie kein Abonnement besitzen, das diesen Plan enthält, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

2. Sie haben das Azure Information Protection-Blatt zum Azure-Portal hinzugefügt und sich vergewissert, dass der Schutzdienst aktiviert ist.

    Wenn Sie Hilfe bei diesen Aktionen benötigen, lesen Sie [Schnellstart: Hinzufügen von Azure Information Protection zum Azure-Portal und Anzeigen der Richtlinie](quickstart-viewpolicy.md)

3. Der Azure Information Protection-Client ist auf Ihrem Computer installiert. 
    
    Um den Client zu installieren, navigieren Sie auf der Azure Information Protection-Seite zum [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018), und laden Sie **AzInfoProtection.exe** herunter.

4. Ein Computer unter Windows (mindestens Windows 7 mit Service Pack 1), auf dem Sie bei Office-Apps aus einer der folgenden Kategorien angemeldet sind:
    
    - Mindestversion 1805 von Office-Apps, Build 9330.2078 von Office 365 Business oder Microsoft 365 Business, wenn Ihnen eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.
    
    - Office 365 ProPlus.
    
    - Office Professional Plus 2019.
    
    - Office Professional Plus 2016.
    
    - Office Professional Plus 2013 mit Service Pack 1.
    
    - Office Professional Plus 2010 mit Service Pack 2.

Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

Los geht’s!

## <a name="edit-the-azure-information-protection-policy"></a>Bearbeiten der Azure Information Protection-Richtlinie

Statt sich darauf zu verlassen, dass Benutzer ihre Dokumente und E-Mails manuell bezeichnen, können Sie einige Richtlinieneinstellungen verwenden, um ein grundlegendes Maß an Klassifizierung sicherzustellen. 

Im Azure-Portal wird die globale Richtlinie bearbeitet, um Richtlinieneinstellungen für alle Benutzer zu ändern.

1. Öffnen Sie ein neues Browserfenster, und melden Sie sich als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zu **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Klicken Sie auf **Klassifizierungen** > **Richtlinien** > **Global**, um das Blatt **Richtlinie: Global** zu öffnen. 

3. Suchen Sie die Richtlinieneinstellungen nach den Bezeichnungen im Abschnitt **Einstellungen konfigurieren, die für Information Protection-Endbenutzer angezeigt und angewendet werden**. Ihre Einstellungen enthalten möglicherweise andere Werte als die in den Abbildungen dargestellten Einstellungen:
    
    ![Azure Information Protection-Tutorial: Standardeinstellungen](./media/defaultsettings-aip.png)

4. Ändern Sie Ihre Einstellungen entsprechend des Werts in der folgenden Tabelle. Notieren Sie sich die Einstellungen, die Sie ändern, für den Fall, dass Sie sie wieder zurück ändern möchten, wenn Sie dieses Tutorial abgeschlossen haben. 

    |Einstellung|Wert|Informationen|
    |-------|-----|-----|
    |**Standardbezeichnung auswählen**|**Allgemein**|Wenn Sie nicht über eine Bezeichnung namens **Allgemein** verfügen, wählen Sie eine andere Bezeichnung aus der Dropdownliste aus. Bei nicht gekennzeichneten Dokumenten und E-Mails wird diese Bezeichnung automatisch als Basisklassifizierung angewendet. Allerdings können Benutzer Ihre ausgewählte Bezeichnung ändern.|
    |**Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen**|**Ein**|Diese Einstellung wird häufig als obligatorische Bezeichnung bezeichnet, da sie verhindert, dass Benutzer Dokumente speichern oder E-Mails senden, die nicht bezeichnet sind. Zusammen mit der Standardbezeichnung weisen Dokumente und E-Mails entweder die Standardbezeichnung auf, die Sie festlegen, oder eine von Ihnen gewählte Bezeichnung.
    |**Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht**|**Empfohlen**|Diese Einstellung fordert Benutzer auf, eine höhere Klassifizierungsbezeichnung für ihre E-Mails auszuwählen, wenn sie Dokumente anhängen, die eine höhere Klassifizierung aufweisen als Ihre ausgewählte Standardbezeichnung.
    |**Information Protection-Leiste in Office-Apps anzeigen**|**Ein**|Die Anzeige der Information Protection-Leiste macht es Benutzern einfacher, die Standardbezeichnung anzuzeigen und zu ändern.
    
    Die Einstellungen sollten nun wie folgt aussehen:
    
    ![Azure Information Protection-Tutorial: Geänderte Standardeinstellungen](./media/defaultsettings-aip-changed.png)

5. Wählen Sie **Speichern** auf diesem Blatt **Richtlinie: Global** aus, und wenn Sie zum Bestätigen der Aktion aufgefordert werden, wählen Sie **OK** aus. 

## <a name="see-your-policy-settings-in-action"></a>Testen Ihrer Richtlinieneinstellungen 

In diesem Tutorial werden Ihre Richtlinienänderungen mithilfe von Word und Outlook getestet. Wenn diese Apps bereits geladen wurden, bevor Sie die Richtlinieneinstellungen geändert haben, starten Sie sie neu, um die Änderungen herunterzuladen.

### <a name="default-label-and-the-information-protection-bar"></a>Standardbezeichnung und Information Protection-Leiste

Öffnen Sie ein neues Dokument in Word. Daraufhin wird das Dokument automatisch mit der Bezeichnung **Allgemein** bezeichnet, sodass der Benutzer keine Bezeichnung auswählen muss. 

Durch die angezeigte Information Protection-Leiste und die angezeigten verfügbaren Bezeichnungen ist es für Benutzer einfach, die ausgewählte Bezeichnung auf einen Blick zu sehen und zu ändern, falls die Standardbezeichnung nicht geeignet ist:

![Azure Information Protection-Tutorial: Neues Dokument mit Standardbezeichnung](./media/defaultlabel-word.png)

Statt die Bezeichnung zu ändern, schließen Sie die Information Protection-Leiste, um die Oberfläche mit der Darstellung zu vergleichen, wenn die Leiste nicht angezeigt wird:

![Azure Information Protection-Tutorial: Leiste schließen](./media/infoprotect-bar-close.png)

Die Bezeichnung **Allgemein** ist nach wie vor ausgewählt, aber deutlich schlechter auf einen Blick zu erkennen. Zudem ist es schwieriger herauszufinden, wie eine andere Bezeichnung ausgewählt werden kann. Zu diesem Zweck müssen Benutzer auf die Schaltfläche **Schützen** klicken:

![Azure Information Protection-Tutorial: Markierte Schaltfläche „Schützen“](./media/infoprotect-protectbutton-pulldown.png)

Im Pulldownmenü sehen Sie nun anhand des Häkchens, dass die Bezeichnung **Allgemein** ausgewählt ist. Um die derzeit ausgewählte Bezeichnung zu ändern, können Benutzer eine andere Bezeichnung aus der Liste auswählen. Wenn Benutzer nicht mit Bezeichnungen vertraut sind, werden sie wahrscheinlich nicht daran denken, jedes Mal auf die Schaltfläche **Schützen** zu klicken. Zudem wird es Ihnen möglicherweise nicht in den Sinn kommen, dass sie eine andere Bezeichnung auswählen können.

Um die Information Protection-Leiste erneut anzuzeigen, wählen Sie aus dem Pulldownmenü **Leiste anzeigen** aus.

> [!TIP]
> Sie können eine andere Standardbezeichnung für Outlook auswählen, indem Sie eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#set-a-different-default-label-for-outlook) konfigurieren.

### <a name="mandatory-labeling"></a>Obligatorische Bezeichnung

Sie können die derzeit ausgewählte Bezeichnung **Allgemein** in eine andere Bezeichnung ändern, diese aber nicht entfernen. Da Sie die Einstellung **Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen** in **Ein** geändert haben, wird das Symbol **Bezeichnung löschen** nicht in der Information Protection-Leiste angezeigt. 

Wenn Sie diese Einstellung nicht geändert hätten, würden in der Information Protection-Leiste folgendes Symbol angezeigt werden:

![Azure Information Protection-Tutorial: Leiste schließen](./media/infoprotect-deletelabel-icon.png)

Zusammen mit einer Standardbezeichnung stellt die obligatorische Bezeichnung sicher, dass neue und bearbeitete Dokumente (und E-Mails) eine grundlegende Klassifizierung Ihrer Wahl aufweisen. 

Wenn eine Standardbezeichnung nicht mit der obligatorischen Bezeichnung festgelegt worden wäre, würden Benutzer immer aufgefordert, eine Bezeichnung auszuwählen, wenn sie ein nicht gekennzeichnetes Dokument speichern oder eine nicht gekennzeichnete E-Mail senden. Für viele Benutzer können diese ständigen Eingabeaufforderungen frustrierend sein und zudem zu ungenauen Bezeichnungen führen. Denn die Aufforderung, eine Bezeichnung auszuwählen, nachdem Benutzer ihre Arbeit an einem Dokument oder eine E-Mail abgeschlossen haben, stellt eine Unterbrechung ihrer Workflows dar, sodass es naheliegt für sie, irgendeine beliebige Bezeichnung auszuwählen, damit sie mit dem nächsten Schritt fortfahren können.

### <a name="recommendations-for-emails-with-attachments"></a>Empfehlungen für E-Mails mit Anlagen

Wählen Sie für das geöffnete Word-Dokument eine Bezeichnung mit einer höheren Klassifizierung als **Allgemein** aus. Beispiel: Eine der untergeordneten Bezeichnungen unter **Vertraulich**, z.B. **Vertraulich – jeder (nicht geschützt)** . Speichern Sie das Dokument lokal, und geben sie einen beliebigen Namen an. 

Starten Sie Outlook, und erstellen Sie eine neue E-Mail-Nachricht. Genau wie es bei Word der Fall war, wird die neue E-Mail-Nachricht automatisch mit der Bezeichnung **Allgemein** bezeichnet, und die Information Protection-Leiste wird angezeigt.

Fügen Sie das Word-Dokument hinzu, das Sie soeben als Anlage der E-Mail-Nachricht bezeichnet haben. Es wird eine Aufforderung angezeigt, die E-Mail-Bezeichnung in die Bezeichnung **Vertraulich** zu ändern, die der Word-Anlage entspricht. Sie können die Empfehlung akzeptieren oder verwerfen:

![Azure Information Protection-Tutorial: Aufforderung zum Neubezeichnen der E-Mail entsprechend der bezeichneten Anlage](./media/infoprotect-matchemail-label.png)

Wenn Sie auf **Verwerfen** klicken, wird die neue Bezeichnung nicht angewendet, Sie sehen jedoch, dass die E-Mail immer noch mit der Standardbezeichnung **Allgemein** versehen ist, die Sie konfiguriert haben. Die verfügbaren Bezeichnungen werden nach wie vor als Alternative angezeigt.

Wenn Sie **Jetzt ändern** auswählen, wird die E-Mail in die untergeordnete Bezeichnung **Vertraulich** neubezeichnet. Benutzer können jedoch nach wie vor die Bezeichnung ändern, bevor Sie die E-Mail senden, indem sie auf das Symbol „Bezeichnung bearbeiten“ klicken:

![Azure Information Protection-Tutorial: Symbol „Bezeichnung bearbeiten“](./media/infoprotect-editlabel-icon.png)

Die Information Protection-Leiste wird dann erneut angezeigt, sodass Benutzer eine alternative Bezeichnung auswählen können.

Da die Bezeichnung vor dem Senden der E-Mail ausgewählt ist, besteht keine Notwendigkeit, die E-Mail tatsächlich zu senden, um die Funktionsweise dieser Richtlinieneinstellung zu veranschaulichen. Sie können die E-Mail schließen, ohne sie zu senden oder zu speichern.

Sie sollten diese Übung jedoch wiederholen, jedoch auch ein anderes Dokument mit einer höheren Klassifizierung anhängen (eine untergeordnete Bezeichnung der Bezeichnung **Streng vertraulich**). Sie werden dann sehen, dass die Eingabeaufforderung dahingehend geändert wird, dass die höhere Klassifizierungsbezeichnung angewendet wird. Wenn Sie mehrere Anlagen mit untergeordneten Bezeichnungen mit gleicher übergeordneter Bezeichnung testen, müssen Sie [eine erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#enable-order-support-for-sublabels-on-attachments) zur Unterstützung ihrer Reihenfolge im Azure-Portal konfigurieren.

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie die Änderungen, die Sie in diesem Tutorial vorgenommen haben, nicht beibehalten möchten:

1. Klicken Sie auf **Klassifizierungen** > **Richtlinien** > **Global**, um das Blatt **Richtlinie: Global** zu öffnen.

2. Setzen Sie die Richtlinieneinstellungen auf die ursprünglichen Werte zurück, die Sie zuvor notiert haben, und klicken Sie dann auf **Speichern**.

Starten Sie Ihre Word- und Outlook-Apps neu, um diese Änderungen herunterzuladen.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Bearbeiten der Azure Information Protection-Richtlinieneinstellungen finden Sie unter [Gewusst wie: Konfigurieren der Richtlinieneinstellungen für Azure Information Protection](configure-policy-settings.md).

Mit den Richtlinieneinstellungen, die Sie geändert haben, wird ein grundlegendes Maß an Klassifizierung sichergestellt, und Benutzer werden dazu angeregt, eine geeignete Bezeichnung auszuwählen. Der nächste Schritt ist, diese Strategie auf die nächste Stufe zu bringen, indem Sie den Inhalt der Dokumente und E-Mails untersuchen und dann eine entsprechende Bezeichnung empfehlen oder automatisch anwenden lassen. Hierfür können Sie Bezeichnungen für Bedingungen konfigurieren. Weitere Informationen finden Sie unter [Gewusst wie: Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md).
