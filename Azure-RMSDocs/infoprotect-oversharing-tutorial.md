---
title: 'Tutorial: Verwenden von Azure Information Protection zur Vermeidung übermäßiger Informationsfreigaben – AIP'
description: Ein Einführungstutorial zum Konfigurieren und Anzeigen von erweiterten Clienteinstellungen für den Azure Information Protection-Client zum Ausgeben von Warnungen – zur Legitimierungsaufforderung oder zum Blockieren von Popupmeldungen –, die über Outlook gesendet werden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/17/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 6bb35700a025105b584b93b5a38219b567dbe99c
ms.sourcegitcommit: 325bb21a2210069f6d838ca7a875d7082c5e02a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/17/2020
ms.locfileid: "88264428"
---
# <a name="tutorial-configure-azure-information-protection-to-control-oversharing-of-information-using-outlook"></a>Tutorial: Konfigurieren von Azure Information Protection zur Vermeidung übermäßiger Informationsfreigaben mit Outlook

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).
>
> **Zum Bereitstellen des klassischen AIP-Clients** öffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.

In diesem Tutorial lernen Sie, wie die folgenden Aufgaben ausgeführt werden:
> [!div class="checklist"]
> * Konfigurieren von Einstellungen, über die Warn-, Legitimierungs- oder Blockierungsmeldungen in Outlook implementiert werden
> * Testen Ihrer Einstellungen
> * Überprüfen der protokollierten Benutzernachrichten und Benutzeraktionen im Ereignisprotokoll 


Durch das Senden von E-Mails durch die Benutzer werden am häufigsten unbeabsichtigt Informationen freigeben, sei es in der E-Mail-Nachricht selbst oder in Anhängen. Möglicherweise verwenden Sie Lösungen zur Verhinderung von Datenverlust (DLP), die bekannte vertrauliche Informationen identifizieren können und verhindern, dass diese Ihre Organisation verlassen. Sie können jedoch auch den Azure Information Protection-Client mit einigen erweiterten Clienteinstellungen verwenden, um übermäßige Informationsfreigaben zu vermeiden und Ihre Benutzer mit interaktiven Nachrichten zu sensibilisieren, die Feedback in Echtzeit bereitstellen.

In diesem Tutorial werden Sie Schritt für Schritt durch eine einfache Konfiguration geleitet, die nur eine Bezeichnung verwendet, um die Meldungen zum Warnen, Legitimieren und Blockieren darzustellen, die Benutzern angezeigt werden, und auf die sie reagieren können.

Für dieses Tutorial benötigen Sie etwa 15 Minuten.

## <a name="prerequisites"></a>Voraussetzungen 

Voraussetzungen für dieses Tutorial:

1. Ein Abonnement, das Azure Information Protection-Plan 2 beinhaltet.
    
    Wenn Sie kein Abonnement besitzen, das diesen Plan enthält, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.

1. Der Bereich „Azure Information Protection“ wurde zum Azure-Portal hinzugefügt, und Sie haben mindestens eine Bezeichnung in der globalen Azure Information Protection-Richtlinie veröffentlicht.
    
    Obwohl in diesem Tutorial die Standardbezeichnung **Allgemein** verwendet wird, können Sie diese, falls gewünscht, durch eine andere Bezeichnung ersetzen. Wenn Sie beim Hinzufügen des Azure Information Protection-Bereichs Hilfe benötigen oder noch keine Bezeichnungen in der globalen Richtlinie veröffentlicht haben, lesen Sie den Artikel [Schnellstart: Hinzufügen von Azure Information Protection zum Azure-Portal und Anzeigen der Richtlinie](quickstart-viewpolicy.md).

1. Einen Computer unter Windows (mindestens Windows 7 mit Service Pack 1), auf dem Sie sich bei Outlook anmelden können. Sie werden Outlook während dieses Tutorials mehrere Male schließen und öffnen müssen.

1. Der auf Ihrem Windows-Computer installierte Azure Information Protection-Client (klassisch); mindestens Windows 7 mit Service Pack 1. 

> [!TIP]
> Die vollständige Liste der Voraussetzungen an Azure Information Protection finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
> 
Los geht’s! Fahren Sie mit [Identifizieren einer Bezeichnungs-ID zum Testen](#identify-a-label-id-for-testing) fort.

**Client für einheitliche Bezeichnungen**

Wenn Sie den Client für einheitliche Bezeichnungen anstelle des klassischen Clients verwenden, sehen Sie sich die folgenden Anweisungen an, die erläutern, wie Sie die erweiterten PowerShell-Einstellungen für die entsprechenden Konfigurationen in diesem Tutorial verwenden:
    
- Anweisungen im Administratorleitfaden: [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](./rms-client/clientv2-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)

- Video: [Azure Information Protection Outlook Popup Configuration](https://azure.microsoft.com/resources/videos/how-to-configure-azure-information-protection-popup-for-outlook/) (Konfiguration von Azure Information Protection-Popupmeldungen in Outlook)



## <a name="identify-a-label-id-for-testing"></a>Identifizieren einer Bezeichnungs-ID zum Testen

In diesem Tutorial wird nur eine Bezeichnung verwendet, um das resultierende Verhalten für Benutzer anzuzeigen. Sie können eine beliebige Bezeichnung verwenden, ein gutes Beispiel zum Testen stellt aber die Standardbezeichnung namens **Allgemein** dar, die in der Regel für Geschäftsdaten geeignet ist, die nicht zur öffentlichen Nutzung bestimmt sind und die keinen Schutz anwendet.

Sie müssen die ID der ausgewählten Bezeichnung kennen, um diese anzugeben. Die ID identifizieren Sie über das Azure-Portal:

1. Öffnen Sie ein neues Browserfenster, und melden Sie sich als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zu **Azure Information Protection**. 
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.
    
    Wenn Sie nicht der globale Administrator sind, verwenden Sie den folgenden Link für andere Rollen: [Anmelden beim Azure-Portal](configure-policy.md#signing-in-to-the-azure-portal)

2. Wählen Sie **Klassifizierungen** > **Bezeichnungen** aus, und klicken Sie dann auf die Bezeichnung **Allgemein** zum Öffnen des Blatts **Bezeichnung: Allgemein**. 

3. Suchen Sie die Bezeichnungs-ID am unteren Rand des Bereichs:
    
    ![Azure Information Protection-Tutorial – Suchen der Bezeichnungs-ID](./media/label-id.png)

4. Kopieren Sie den Wert der Bezeichnungs-ID, und fügen Sie ihn in eine temporäre Datei ein, um ihn später problemlos für einen weiteren Schritt wieder kopieren zu können. In Ihrem Beispiel ist dieser Bezeichnungs-ID-Wert **0e421e6d-ea17-4fdb-8f01-93a3e71333b8**.

5. Schließen Sie das Blatt **Bezeichnung: Allgemein**, jedoch nicht das Azure-Portal.

## <a name="create-a-scoped-policy-to-test-the-new-advanced-client-settings"></a>Erstellen einer bereichsbezogenen Richtlinie zum Testen der neuen erweiterten Clienteinstellungen

Sie erstellen eine neue bereichsbezogene Richtlinie, damit die neuen erweiterten Clienteinstellungen nur für Ihre Testzwecke angewendet werden.

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** auf die Option **Neue Richtlinie hinzufügen**. Der Bereich **Richtlinie** wird angezeigt, auf dem Bezeichnungen und Einstellungen aus Ihrer bestehenden globalen Richtlinie dargestellt sind.

2. Geben Sie den Richtliniennamen von **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben) an und optional eine Beschreibung von **Advanced client settings to control oversharing using Outlook** (Erweiterte Clienteinstellungen zur Vermeidung übermäßiger Informationsfreigaben mit Outlook).

3. Wählen Sie **Specify which users/groups get this policy** (Benutzer/Gruppen angeben, die diese Richtlinie abrufen), und geben Sie in den folgenden Bereichen Ihr eigenes Benutzerkonto an.

4. Klicken Sie, wenn Ihr Kontoname nun im Bereich **Richtlinie** angezeigt wird, auf **Speichern**, ohne weitere Änderungen an den Bezeichnungen oder Einstellungen in diesem Bereich vorzunehmen. Möglicherweise werden Sie zur Bestätigung Ihrer Auswahl aufgefordert. 

Zu dieser bereichsbezogenen Richtlinie können nun erweiterte Clienteinstellungen hinzugefügt werden. Schließen Sie das Blatt **Policy: Oversharing tutorial** (Richtlinie: Tutorial zur Vermeidung übermäßiger Informationsfreigaben), jedoch nicht das Azure-Portal.

## <a name="configure-and-test-advanced-client-settings-to-warn-prompt-for-justification-or-block-emails-that-have-the-general-label"></a>Konfigurieren und Testen von erweiterten Clienteinstellungen zum Ausgeben von Warnungen, Auffordern zum Legitimieren oder Blockieren von E-Mails mit der Bezeichnung „Allgemein“

Geben Sie für diesen Tutorialschritt die folgenden erweiterten Clienteinstellungen an, und testen Sie diese nacheinander:

- **OutlookWarnUntrustedCollaborationLabel**
- **OutlookJustifyUntrustedCollaborationLabel**
- **OutlookBlockUntrustedCollaborationLabel**

### <a name="create-the-advanced-client-setting-to-warn-users-if-an-email-or-attachment-has-the-general-label"></a>Erstellen der erweiterten Clienteinstellung zum Warnen von Benutzern, wenn eine E-Mail oder ein Anhang die Bezeichnung „Allgemein“ aufweist

Verwenden Sie die neu erstellte bereichsbezogene Richtlinie, und fügen Sie eine neue erweiterte Clienteinstellung namens **OutlookWarnUntrustedCollaborationLabel** mit der ID Ihrer Bezeichnung **Allgemein** hinzu: 

1. Klicken Sie dann im Bereich **Azure Information Protection – Richtlinien** auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Geben Sie im Bereich **Erweiterte Einstellungen** den Namen für die erweiterten Einstellungen ein (**OutlookWarnUntrustedCollaborationLabel**), und fügen Sie Ihre eigene Bezeichnungs-ID für den Wert ein. Verwenden Sie Ihre Beispiel-Bezeichnungs-ID:
    
    
    ![Azure Information Protection-Tutorial – Erstellen der erweiterten „OutlookWarnUntrustedCollaborationLabel“-Clienteinstellung ](./media/configure-warnmessage.png)

3. Klicken Sie auf **Speichern und schließen**.

Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

### <a name="test-the-advanced-client-setting-to-warn-users-if-an-email-or-attachment-has-the-general-label"></a>Testen der erweiterten Clienteinstellung, um Benutzer bei E-Mails oder Anhängen mit der Bezeichnung „Allgemein“ zu warnen

Auf Ihrem Clientcomputer sind nun die Konfigurationsergebnisse dieser erweiterten Clienteinstellung zu sehen.

1. Öffnen Sie Outlook auf Ihrem Clientcomputer. 
    
    Wenn Outlook bereits geöffnet ist, starten Sie es neu. Der Neustart ist erforderlich, um die eben vorgenommene Änderung herunterzuladen.

2. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie die Bezeichnung **Allgemein** an. Klicken Sie beispielsweise auf die Schaltfläche **Schützen** auf der Registerkarte **Datei**, und wählen Sie dann **Allgemein** aus.

3. Geben Sie für das Feld **To** (An) Ihre eigene E-Mail-Adresse an, und als Betreff geben Sie **Testing the General label for the Warn message** (Testen der Bezeichnung „Allgemein“ für die Warnmeldung) ein. Senden Sie dann die E-Mail.

4. Aufgrund der erweiterten Clienteinstellung wird die folgende Warnung mit der Aufforderung zur Bestätigung vor dem Senden der E-Mail angezeigt: Beispiel:
    
    ![Azure Information Protection-Tutorial – Anzeigen der erweiterten Clienteinstellung „OutlookWarnUntrustedCollaborationLabel“ ](./media/see-warnmessage.png)
    
5. Wählen Sie **Abbrechen** aus, als wären Sie ein Benutzer, der versehentlich versucht hat, etwas als **Allgemein** bezeichnetes per E-Mail zu senden. Sie sehen, dass die E-Mail nicht gesendet wurde, die E-Mail-Nachricht selbst aber angezeigt bleibt, sodass Sie Änderungen vornehmen können, beispielsweise am Inhalt oder der Bezeichnung.

6. Wählen Sie erneut **Senden** aus, ohne Änderungen vorzunehmen. Wählen Sie dieses Mal **Bestätigen und senden** aus, als wären Sie ein Benutzer, der bestätigt, dass der Inhalt zum Senden geeignet ist. Die E-Mail wird gesendet.

### <a name="change-the-advanced-client-setting-to-prompt-users-to-justify-if-an-email-has-the-general-label"></a>Ändern der erweiterten Clienteinstellung, um Benutzer aufzufordern, eine E-Mail mit der Bezeichnung „Allgemein“ zu begründen

Sie bearbeiten die vorhandene Clienteinstellung, um Ihre Bezeichnungsweise-ID **Allgemein** zu behalten, Sie ändern jedoch den Namen in **OutlookJustifyUntrustedCollaborationLabel**: 

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Ersetzen Sie im Bereich **Erweiterte Einstellungen** den vorherigen Namen der erweiterten Einstellung, den Sie erstellt haben (**OutlookWarnUntrustedCollaborationLabel**), durch den Namen **OutlookJustifyUntrustedCollaborationLabel**:
    
    ![Azure Information Protection-Tutorial – Erstellen der erweiterten Clienteinstellung „OutlookJustifyUntrustedCollaborationLabel“ ](./media/configure-justifymessage.png)

3. Klicken Sie auf **Speichern und schließen**.

Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

### <a name="test-the-advanced-client-setting-to-prompt-users-to-justify-if-an-email-has-the-general-label"></a>Testen der erweiterten Clienteinstellung, um Benutzer aufzufordern, eine E-Mail mit der Bezeichnung „Allgemein“ zu begründen

Auf Ihrem Clientcomputer sehen Sie nun die Ergebnisse dieser neuen erweiterten Clienteinstellung.

1. Starten Sie auf Ihrem Clientcomputer Outlook neu, um die gerade vorgenommene Änderung herunterzuladen.

2. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie wie zuvor die Bezeichnung **Allgemein** an. Klicken Sie beispielsweise auf die Schaltfläche **Schützen** auf der Registerkarte **Datei**, und wählen Sie dann **Allgemein** aus.

3. Geben Sie für das Feld **To** (An) Ihre eigene E-Mail-Adresse an, und als Betreff geben Sie **Testing the General label for the Justify message** (Testen der Bezeichnung „Allgemein“ für die Legitimationsmeldung) ein. Senden Sie dann die E-Mail.

4. Dieses Mal wird die folgende Meldung angezeigt, in der Sie aufgefordert werden, vor dem Senden der E-Mail eine Begründung anzugeben. Beispiel:
    
    ![Azure Information Protection-Tutorial – Anzeigen der erweiterten Clienteinstellung „OutlookJustifyUntrustedCollaborationLabel“ ](./media/see-justifymessage.png)
    
5. Wenn Sie ein Benutzer wären, der versehentlich versucht hat, eine E-Mail mit der Bezeichnung **Allgemein** zu senden, dann würden Sie nun auf **Abbrechen** klicken. Sie sehen, dass die E-Mail nicht gesendet wurde, die E-Mail-Nachricht selbst aber angezeigt bleibt, sodass Sie Änderungen vornehmen können, beispielsweise am Inhalt oder der Bezeichnung.

6. Wählen Sie erneut **Senden** aus, ohne Änderungen vorzunehmen. Dieses Mal wählen Sie eine der Legitimierungssoptionen wie beispielsweise **I confirm the recipients are approved for sharing this content** (Ich bestätige die Genehmigung der Freigabe dieses Inhalts für die Empfänger) aus, und klicken dann auf **Bestätigen und senden**. Die E-Mail wird gesendet.

### <a name="change-the-advanced-client-setting-to-block-users-from-sending-an-email-that-has-the-general-label"></a>Ändern der erweiterten Clienteinstellung zum Blockieren von Benutzern für das Senden einer E-Mail mit der Bezeichnung „Allgemein“

Sie bearbeiten die vorhandene Clienteinstellung ein weiteres Mal, um Ihre Bezeichnungsweise-ID **Allgemein** zu behalten, Sie ändern jedoch den Namen in **OutlookBlockUntrustedCollaborationLabel**: 

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** im Azure-Portal auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Ersetzen Sie im Bereich **Erweiterte Einstellungen** den vorherigen Namen der erweiterten Einstellung, den Sie erstellt haben (**OutlookJustifyUntrustedCollaborationLabel**), durch den Namen **OutlookBlockUntrustedCollaborationLabel**:
    
    ![Azure Information Protection-Tutorial – Erstellen der erweiterten „OutlookBlockUntrustedCollaborationLabel“-Clienteinstellung ](./media/configure-blockmessage.png)

3. Klicken Sie auf **Speichern und schließen**.

Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

### <a name="test-the-advanced-client-setting-to-block-users-from-sending-an-email-that-has-the-general-label"></a>Testen der erweiterten Clienteinstellung, zum Blockieren von Benutzern für das Senden einer E-Mail mit der Bezeichnung „Allgemein“

Auf Ihrem Clientcomputer sehen Sie nun die Ergebnisse dieser neuen erweiterten Clienteinstellung.

1. Starten Sie auf Ihrem Clientcomputer Outlook neu, um die gerade vorgenommene Änderung herunterzuladen.

2. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie wie zuvor die Bezeichnung **Allgemein** an. Klicken Sie beispielsweise auf die Schaltfläche **Schützen** auf der Registerkarte **Datei**, und wählen Sie dann **Allgemein** aus.

3. Geben Sie für das Feld **To** (An) Ihre eigene E-Mail-Adresse an, und als Betreff geben Sie **Testing the General label for the Block message** (Testen der Bezeichnung „Allgemein“ für die Blockierungsmeldung) ein. Senden Sie dann die E-Mail.

4. Dieses Mal wird die folgende Meldung angezeigt, die verhindert, dass die E-Mail gesendet wird. Beispiel:
    
    ![Azure Information Protection-Tutorial – Blockieren von E-Mail-Popupmeldung](./media/see-blockmessage.png)

5. Wenn Sie einer Ihrer Benutzer wären, würden Sie sehen, dass die einzige verfügbare Option **OK** ist, durch die Sie zurück zur E-Mail-Nachricht gelangen, die Sie dann ändern können. Klicken Sie auf **OK**, und brechen Sie diese E-Mail-Nachricht ab.

### <a name="use-event-log-to-identify-the-messages-and-user-actions-for-the-general-label"></a>Verwenden des Ereignisprotokolls zum Identifizieren der Meldungen und Benutzeraktionen für die Bezeichnung „Allgemein“

Bevor Sie mit den nächsten Szenario beginnen, in dem eine E-Mail oder ein Anhang keine Bezeichnung hat, starten Sie die Ereignisanzeige, und navigieren Sie zu **Anwendungs- und Dienstprotokolle** > **Azure Information Protection**.

Für alle von Ihnen durchgeführten Tests werden Informationsereignisse erstellt, um sowohl die Meldung als auch die Antwort des Benutzers aufzuzeichnen:

- Warnmeldungen: Informations-ID 301

- Legitimationsmeldungen: Informations-ID 302

- Blockiermeldungen: Informations-ID 303

Wenn beispielsweise der erste Test eine Warnung für den Benutzer war, und Sie **Abbrechen** ausgewählt haben, wird **Dismissed** (Verworfen) als **Benutzerantwort** im ersten Ereignis 301 angezeigt. Beispiel:

```
Client Version: 1.53.10.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing the General label for the Warn message.msg
Item Name: Testing the General label for the Warn message
Process Name: OUTLOOK
Action: Warn
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
Action Source: 
User Response: Dismissed
```

Sie haben allerdings **Bestätigen und senden** ausgewählt, was im nächsten Ereignis 301 wiedergegeben wird, in dem **Confirmed** (Bestätigt) als **Benutzerantwort** angezeigt wird:

```
Client Version: 1.53.10.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing the General label for the Warn message.msg
Item Name: Testing the General label for the Warn message
Process Name: OUTLOOK
Action: Warn
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
Action Source: 
User Response: Confirmed
```

Das gleiche Muster wird für die Legitimationsmeldung wiederholt, die ein Ereignis 302 aufweist. Das erste Ereignis zeigt **Dismissed** (Verworfen) als **Benutzerantwort** an, und das zweite zeigt die ausgewählte Begründung an. Beispiel:

```
Client Version: 1.53.10.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing the General label for the Justify message.msg
Item Name: Testing the General label for the Justify message
Process Name: OUTLOOK
Action: Justify
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
User Justification: I confirm the recipients are approved for sharing this content
Action Source: 
User Response: Confirmed

```

Oben im Ereignisprotokoll sehen Sie die protokollierte Blockierungsmeldung, die ein Ereignis 303 aufweist. Beispiel:

```
Client Version: 1.53.10.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing the General label for the Block message.msg
Item Name: Testing the General label for the Block message
Process Name: OUTLOOK
Action: Block
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
Action Source: 
```

### <a name="optional-create-an-additional-advanced-client-setting-to-exempt-these-messages-for-internal-recipients"></a>Optional: Erstellen einer zusätzlichen erweiterten Clienteinstellung, um diese Meldungen ausnahmsweise für interne Empfänger freizugeben

Sie haben Ihre Warn-, Legitimierungs- und Blockierungsmeldungen mit Ihrer eigenen E-Mail-Adresse als Empfänger getestet. In einer Produktionsumgebung ist es möglicherweise empfehlenswert, diese Meldungen für die von Ihnen angegebenen Bezeichnungen nur anzuzeigen, wenn sich Empfänger außerhalb Ihrer Organisation befinden. Sie können diese Ausnahme für Partner erweitern, mit denen Ihre Organisation regelmäßig zusammenarbeitet.

Um die Funktionsweise in der Praxis zu erleben, erstellen Sie eine zusätzliche erweiterte Clienteinstellung namens **OutlookBlockTrustedDomains** und geben Ihren eigenen Domänennamen aus Ihrer E-Mail-Adresse an. Damit wird verhindert, dass die Blockierungsmeldung für Empfänger angezeigt wird, deren E-Mail-Adresse den gleichen Domänennamen enthält. Für andere Empfänger wird die Meldung weiterhin angezeigt. Auf ähnliche Weise können Sie zusätzliche erweiterte Clienteinstellungen für **OutlookWarnTrustedDomains** und **OutlookJustifyTrustedDomains** erstellen.

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** im Azure-Portal auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Geben Sie im Bereich **Erweiterte Einstellungen** den Namen der erweiterten Einstellung (**OutlookBlockTrustedDomains**) ein, und fügen Sie Ihren Domänennamen aus Ihrer E-Mail-Adresse für den Wert ein. Beispiel:
    
    ![Azure Information Protection-Tutorial – Erstellen der erweiterten „OutlookBlockTrustedDomains“-Clienteinstellung](./media/configure-exemptblockdomain.png)

4. Klicken Sie auf **Speichern und schließen**. Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

5. Wiederholen Sie jetzt den oben beschriebenen [Test zum Blockieren von Benutzern für das Senden einer E-Mail mit der Bezeichnung „Allgemein“](#test-the-advanced-client-setting-to-block-users-from-sending-an-email-that-has-the-general-label): Die Blockierungsmeldung wird nicht mehr angezeigt, wenn Sie Ihre eigene E-Mail-Adresse verwenden. Die E-Mail wird ohne Unterbrechung gesendet.
    
    Um sich zu vergewissern, dass die Blockierungsmeldung für externe Empfänger weiterhin angezeigt wird, wiederholen Sie den Test ein weiteres Mal, geben aber einen Empfänger von außerhalb Ihrer Organisation an. Dieses Mal wird die Blockierungsmeldung wieder angezeigt, und diese führt die neue Empfängeradresse als nicht vertrauenswürdig auf.

## <a name="configure-and-test-an-advanced-client-setting-to-warn-prompt-for-justification-or-block-emails-that-dont-have-a-label"></a>Konfigurieren und Testen einer erweiterten Clienteinstellung zum Ausgeben von Warnungen, Auffordern zum Legitimieren oder Blockieren von E-Mails ohne Bezeichnung

Geben Sie für diesen Tutorialschritt eine neue erweiterte Clienteinstellung mit anderen Werten an, und testen Sie diese nacheinander:

- **OutlookUnlabeledCollaborationAction**

### <a name="create-the-advanced-client-setting-to-warn-users-if-an-email-doesnt-have-a-label"></a>Erstellen der erweiterten Clienteinstellung zum Warnen von Benutzern, wenn eine E-Mail keine Bezeichnung aufweist

Diese neue erweiterte Clienteinstellung namens **OutlookUnlabeledCollaborationAction** benötigt keine Bezeichnungs-ID, sie gibt jedoch die Aktion an, die für Inhalte ohne Bezeichnung auszuführen ist: 

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** im Azure-Portal auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Geben Sie im Bereich **Erweiterte Einstellungen** den Namen der erweiterten Einstellung ein (**OutlookUnlabeledCollaborationAction**), und geben Sie für den Wert **Warn** (Warnen) an:
    
    ![Azure Information Protection-Tutorial – Erstellen der erweiterten „OutlookUnlabeledCollaborationAction“-Clienteinstellung mit Warnungswert ](./media/configure-nolablewarn.png)

3. Klicken Sie auf **Speichern und schließen**.

Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

### <a name="test-the-advanced-client-setting-to-warn-users-if-an-email-doesnt-have-a-label"></a>Testen der erweiterten Clienteinstellung, um Benutzer bei E-Mails oder Anhängen ohne Bezeichnung zu warnen

Auf Ihrem Clientcomputer sind nun die Konfigurationsergebnisse dieser neuen erweiterten Clienteinstellung für Inhalte ohne Bezeichnung zu sehen:

1. Starten Sie auf Ihrem Clientcomputer Outlook neu, um die gerade vorgenommene Änderung herunterzuladen.

2. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie dieses Mal keine Bezeichnung an.

3. Geben Sie für das Feld **To** (An) Ihre eigene E-Mail-Adresse an, und als Betreff geben Sie **Testing send an email without a label for the Warn message** (Testen des Sendens einer E-Mail ohne Bezeichnung für die Warnmeldung) ein. Senden Sie dann die E-Mail.

4. Dieses Mal sehen Sie die Meldung **Bestätigung erforderlich**, die Sie **Bestätigen und senden** oder **Abbrechen** können:
    
    ![Azure Information Protection-Tutorial – Anzeigen der erweiterten „OutlookUnlabeledCollaborationAction“-Clienteinstellung mit Warnungswert](./media/see-nolablewarn.png)

5. Wählen Sie **Bestätigen und senden** aus.

### <a name="change-the-advanced-client-setting-to-prompt-users-to-justify-if-an-email-is-unlabeled"></a>Ändern der erweiterten Clienteinstellung, um Benutzer aufzufordern, eine E-Mail ohne Bezeichnung zu begründen

Sie bearbeiten die vorhandene erweiterte Clienteinstellung, um den Namen von **OutlookUnlabeledCollaborationAction** zu behalten, Sie ändern jedoch den Wert in **Justify** (Legitimieren): 

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Suchen Sie im Bereich **Erweiterte Einstellungen** die Einstellung **OutlookUnlabeledCollaborationAction**, und ersetzen Sie den vorherigen Wert für **Warnung** durch den neuen Wert **Justify** (Legitimieren):
    
    ![Azure Information Protection-Tutorial – Ändern der erweiterten „OutlookUnlabeledCollaborationAction“-Clienteinstellung in Legitimationswert](./media/configure-justifymessage2.png)

3. Klicken Sie auf **Speichern und schließen**.

Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

### <a name="test-the-advanced-client-setting-to-prompt-users-to-justify-if-an-email-isnt-labeled"></a>Testen der erweiterten Clienteinstellung, um Benutzer aufzufordern, eine E-Mail ohne Bezeichnung zu begründen

Auf Ihrem Clientcomputer sehen Sie nun die Ergebnisse aufgrund der Änderung des Werts für diese erweiterte Clienteinstellung.

1. Starten Sie auf Ihrem Clientcomputer Outlook neu, um die gerade vorgenommene Änderung herunterzuladen.

2. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie wie zuvor keine Bezeichnung an.

3. Geben Sie für das Feld **To** (An) Ihre eigene E-Mail-Adresse an, und als Betreff geben Sie **Testing send an email without a label for the Justify message** (Testen des Sendens einer E-Mail ohne Bezeichnung für die Legitimationsmeldung) ein. Senden Sie dann die E-Mail.

4. Dieses Mal sehen Sie die Meldung **Bestätigung erforderlich** mit verschiedenen Optionen:
    
    ![Azure Information Protection-Tutorial – Anzeigen der erweiterten „OutlookUnlabeledCollaborationAction“-Clienteinstellung mit Legitimationswert](./media/see-nolabljustify.png)

5. Wählen Sie eine Option aus, beispielsweise **My manager approved sharing of this content** (Mein Vorgesetzter hat die Freigabe dieser Inhalte genehmigt). Klicken Sie dann auf **Bestätigen und senden**.

### <a name="change-the-advanced-client-setting-to-block-users-from-sending-an-email-that-isnt-labeled"></a>Ändern der erweiterten Clienteinstellung zum Blockieren von Benutzern für das Senden einer E-Mail ohne Bezeichnung

Wie zuvor bearbeiten Sie nun die vorhandene erweiterte Clienteinstellung, um den Namen von **OutlookUnlabeledCollaborationAction** zu behalten, Sie ändern jedoch den Wert in **Block** (Blockieren): 

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Wählen Sie dann **Erweiterte Einstellungen** aus.

2. Suchen Sie im Bereich **Erweiterte Einstellungen** die Einstellung **OutlookUnlabeledCollaborationAction**, und ersetzen Sie den vorherigen Wert für **Justify** (Legitimieren) durch den neuen Wert **Blockieren**:
    
    ![Azure Information Protection-Tutorial – Ändern der erweiterten „OutlookUnlabeledCollaborationAction“-Clienteinstellung in Blockierwert](./media/configure-blockmessage2.png)

3. Klicken Sie auf **Speichern und schließen**.

Schließen Sie nicht den Bereich **Richtlinien** oder das Azure-Portal.

### <a name="test-the-advanced-client-setting-to-block-users-from-sending-an-email-that-isnt-labeled"></a>Testen der erweiterten Clienteinstellung zum Blockieren von Benutzern für das Senden einer E-Mail ohne Bezeichnung

Auf Ihrem Clientcomputer sehen Sie nun die Ergebnisse aufgrund der Änderung des Werts dieser erweiterten Clienteinstellung.

1. Starten Sie auf Ihrem Clientcomputer Outlook neu, um die gerade vorgenommene Änderung herunterzuladen.

2. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie wie zuvor keine Bezeichnung an.

3. Geben Sie für das Feld **To** (An) Ihre eigene E-Mail-Adresse an, und als Betreff geben Sie **Testing send an email without a label for the Block message** (Testen des Sendens einer E-Mail ohne Bezeichnung für die Blockierungsmeldung) ein. Senden Sie dann die E-Mail.

4. Dieses Mal wird, mit einer Erklärung für den Benutzer, die folgende Meldung angezeigt, durch die die E-Mail nicht gesendet wird. Beispiel:
    
    ![Azure Information Protection-Tutorial – Anzeigen der erweiterten „OutlookWarnUntrustedCollaborationLabel“-Clienteinstellung mit Blockierwert](./media/see-blockmessage2.png)

5. Wenn Sie einer Ihrer Benutzer wären, würden Sie sehen, dass die einzige verfügbare Option **OK** ist, durch die Sie zurück zur E-Mail-Nachricht gelangen, wo Sie dann eine Bezeichnung auswählen können.
    
    Klicken Sie auf **OK**, und brechen Sie diese E-Mail-Nachricht ab.

### <a name="use-event-log-to-identify-the-messages-and-user-actions-for-the-unlabeled-email"></a>Verwenden des Ereignisprotokolls zum Identifizieren der Meldungen und Benutzeraktionen für E-Mails ohne Bezeichnung

Wie zuvor werden die Meldungen und Benutzerantworten in der Ereignisanzeige **Anwendungs- und Dienstprotokolle** > **Azure Information Protection** mit den gleichen Ereignis-IDs protokolliert.

- Warnmeldungen: Informations-ID 301

- Legitimationsmeldungen: Informations-ID 302

- Blockiermeldungen: Informations-ID 303

Zum Beispiel die Ergebnisse Ihrer Aufforderung zur Legitimation, wenn die E-Mail keine Bezeichnung aufgewiesen hat:

```
Client Version: 1.53.10.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing send an email without a label for the Justify message.msg
Item Name: Testing send an email without a label for the Justify message
Process Name: OUTLOOK
Action: Justify
User Justification: My manager approved sharing of this content
Action Source: 
User Response: Confirmed
```

## <a name="clean-up-resources"></a>Bereinigen der Ressourcen

Führen Sie die folgenden Schritte durch, wenn Sie die Änderungen, die Sie in diesem Tutorial vorgenommen haben, nicht beibehalten möchten:

1. Klicken Sie im Bereich **Azure Information Protection – Richtlinien** im Azure-Portal auf das Kontextmenü (**...**) neben **Oversharing tutorial** (Tutorial zur Vermeidung übermäßiger Informationsfreigaben). Klicken Sie dann auf **Richtlinie löschen**.

2. Wenn Sie zur Bestätigung dieser Aktion aufgefordert werden, klicken Sie auf **OK**.

Starten Sie Outlook neu, damit die für dieses Tutorial konfigurierten Einstellungen zurückgesetzt werden.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial wurde eine E-Mail-Nachricht ohne Anhang an einen einzelnen Empfänger verwendet, um schneller testen zu können. Sie können sowohl die gleiche Methode mit mehreren Empfängern und mehren Bezeichnungen anwenden, als auch die gleiche Logik zum Senden von E-Mail-Anhängen, deren Bezeichnungsstatus für Benutzer oft nicht klar hervorgeht. Die E-Mail-Nachricht selbst weist z. B. die Bezeichnung „Öffentlich“ auf, die angehängte PowerPoint-Präsentation die Bezeichnung „Allgemein“. Weitere Informationen zu den Konfigurationsoptionen finden Sie im folgenden Abschnitt des Administratorhandbuchs: [Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](./rms-client/client-admin-guide-customizations.md#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)

Das Administratorhandbuch enthält auch Informationen über erweiterte Clienteinstellungen, die Sie verwenden können, um das Verhalten des Client anzupassen. Eine vollständige Liste der Einstellungen finden Sie unter [Verfügbare erweiterte Clienteinstellungen](./rms-client/client-admin-guide-customizations.md#available-advanced-client-settings).
