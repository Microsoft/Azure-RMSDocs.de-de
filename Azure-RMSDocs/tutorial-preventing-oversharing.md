---
title: 'Tutorial: Verhindern übermäßiger Freigaben mit Azure Information Protection (AIP)'
description: Ein ausführliches Tutorial zur Verwendung des Azure Information Protection-Clients (AIP), der eine übermäßige Freigabe von Inhalten durch Benutzer verhindert.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/09/2020
ms.topic: tutorial
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 10f142fb09d8ad65b773f5e02f03233b454da240
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384535"
---
# <a name="tutorial-preventing-oversharing-in-outlook-using-azure-information-protection-aip"></a>Tutorial: Verhindern übermäßiger Freigaben in Outlook mit Azure Information Protection (AIP)

>**Gilt für*: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> ***Relevant für:** [Azure Information Protection-Client für einheitliche Bezeichnungen für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Als Systemadministrator müssen Sie sicherstellen, dass die Daten Ihrer Organisation geschützt sind und nur für vertrauenswürdige Benutzer freigegeben werden. Am häufigsten werden Inhalte von Benutzern unzulässigerweise per E-Mail ausgetauscht. Konfigurieren Sie Ihre Richtlinie, um eine übermäßige Freigabe über Outlook zu verhindern, z. B. das Einschränken des Zugriffs auf bestimmte Benutzer oder das Freigeben von Inhalten nur für vertrauenswürdige externe Benutzer.

**Benötigte Zeit**: Sie können dieses Tutorial innerhalb von 30 Minuten abschließen.

In diesem Tutorial lernen Sie Folgendes:
> [!div class="checklist"]
> * Konfigurieren von Warnungs-, Legitimations- und Blockierverhalten für bestimmte Bezeichnungsbedingungen
> * Testen Ihrer Einstellungen
> * Überprüfen der protokollierten Benutzernachrichten und Benutzeraktionen im Ereignisprotokoll 

## <a name="tutorial-prerequisites"></a>Voraussetzungen für das Lernprogramm

Stellen Sie sicher, dass die folgenden Systemanforderungen erfüllt sind, bevor Sie mit diesem Tutorial beginnen.

|Voraussetzungen  |Beschreibung  |
|---------|---------|
|**Computeranforderungen**     | Stellen Sie sicher, dass Sie: <br /><br />- Über einen Windows-Computer mit einem installierten Azure Information Protection-Client für einheitliche Bezeichnungen verfügen. Weitere Informationen finden Sie unter [Schnellstart: Bereitstellen des Azure Information Protection-Clients (AIP) für einheitliche Bezeichnungen](quickstart-deploy-client.md). <br /><br />- PowerShell installiert haben und dies als Administrator ausführen können. <br /><br />- Sich bei Outlook anmelden können. Sie werden Outlook während dieses Tutorials mehrere Male schließen und öffnen müssen.     |
|**Azure Information Protection-Abonnement**     |   Sie benötigen ein Azure-Abonnement, das [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection/) umfasst. <br /><br />Wenn Sie keines dieser Abonnements besitzen, können Sie ein [kostenloses](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7) Konto für Ihre Organisation erstellen.       |
|**Vertraulichkeitsbezeichnungen und eine Testrichtlinie**     |  Eine **allgemeine** Vertraulichkeitsbezeichnung, die in Ihrer Richtlinie konfiguriert ist. <br /><br />Konfigurieren Sie Vertraulichkeitsbezeichnungen in ihrem Admin Center für Bezeichnungen, zum Beispiel im Microsoft 365 Compliance Center, Microsoft 365 Security Center oder Microsoft 365 Security & Compliance Center. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels). <br /><br />Es wird empfohlen, eine Testrichtlinie für dieses Tutorial zu verwenden, damit Sie nicht Ihre Liverichtlinie beeinträchtigen. <br />Stellen Sie sicher, dass Sie den Namen Ihrer Richtlinie und die GUID für Ihre Bezeichnung **Allgemein** zur Hand haben.   |
| | |

Fangen wir also an. 

## <a name="implement-a-warning-message-for-emails-labeled-as-general"></a>Implementieren einer Warnmeldung für E-Mails mit der Bezeichnung „Allgemein“

In diesem Verfahren wird beschrieben, wie Sie Ihre Richtlinie so konfigurieren, dass Outlook-Benutzer gewarnt werden, bevor sie eine E-Mail mit der Bezeichnung **Allgemein** senden. 

Die Benutzer können sich entscheiden, die Warnung zu beachten und entweder die Bezeichnung oder den Inhalt zu ändern, oder die E-Mail trotzdem zu senden.

1. Führen Sie auf dem Clientcomputer PowerShell als Administrator aus.

1. Führen Sie den folgenden Befehl aus, um eine Warnmeldung für die Bezeichnung **Allgemein** zu definieren. Wenn Sie diesen Befehl kopieren, ersetzen Sie **Global** durch den Namen Ihrer Richtlinie und die lange Zeichenfolge mit Ihrer eigenen Bezeichnungs-ID.

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookWarnUntrustedCollaborationLabel="8faca7b8-8d20-48a3-8ea2-0f96310a848e"}
    ```

    In diesem Beispiel heißt die Richtlinie **Global**, und die GUID für die Bezeichnung **Allgemein** lautet **8faca7b8-8d20-48a3-8ea2-0f96310a848e**.

    > [!TIP]
    > Wenn Sie diese Einstellung auf mehrere Bezeichnungen anwenden möchten, listen Sie ihre GUIDs in dem Wert durch Kommas getrennt auf.

1. Testen Sie Ihre Einstellung in Outlook:

    1. Öffnen oder starten Sie Outlook auf dem Clientcomputer, um die aktualisierten Einstellungen abzurufen.

    1. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie die Bezeichnung **Allgemein** an. Wählen Sie in der Symbolleiste der Meldung die Schaltfläche :::image type="icon" source="media/i-sensitivity.PNG" border="false"::: **Vertraulichkeit** und dann **Allgemein** aus.

    1. Geben Sie im Feld **An** Ihre eigene E-Mail-Adresse und im Feld **Betreff**: `Testing a warning message for the General label` ein, und senden Sie dann die E-Mail.

        Die folgende Warnung mit der Aufforderung zur Bestätigung vor dem Senden der E-Mail wird angezeigt. Beispiel:

        :::image type="content" source="media/qs-tutor/ul-see-warnmessage.png" alt-text="Testen einer Warnmeldung für die Bezeichnung „Allgemein“":::

    1. Angenommen, Sie sind ein Benutzer, der versehentlich versucht hat, einen Inhalt mit der Bezeichnung **Allgemein** zu senden. In diesem Fall würden Sie die Warnung beachten, daher wählen Sie **Abbrechen** aus.

        Ihre E-Mail wird nicht gesendet, bleibt jedoch geöffnet, sodass Sie den Inhalt oder die Bezeichnung ändern können.

    1. Es müssen keine Änderungen vorgenommen werden, und Sie können entscheiden, ob der Inhalt zum Senden geeignet ist. Wählen Sie erneut **Senden** aus. Wenn die Warnung dieses Mal angezeigt wird, wählen Sie **Bestätigen und senden** aus.

        Die E-Mail wird gesendet.

Fahren Sie mit Abschnitt [Anzeigen einer Warnmeldung für E-Mails mit Bezeichnung „Allgemein“ nur beim Senden an externen Empfänger](#show-a-warning-message-for-general-emails-only-when-theyre-sent-externally) fort.

## <a name="show-a-warning-message-for-general-emails-only-when-theyre-sent-externally"></a>Anzeigen einer Warnmeldung für E-Mails mit Bezeichnung „Allgemein“ nur beim Senden an externen Empfänger

In diesem Verfahren wird beschrieben, wie Sie der zuvor konfigurierten Warnmeldung eine Ausnahme hinzufügen, sodass die Warnmeldung nur für externe Empfänger angezeigt wird.

Beim internen Senden von E-Mails mit Bezeichnung **Allgemein** wird keine Warnmeldung angezeigt.

1. Führen Sie auf dem Clientcomputer PowerShell als Administrator aus.

1. Führen Sie den folgenden Befehl aus, um Ihre Domäne als für Warnmeldungen vertrauenswürdige Domäne zu definieren. Wenn Sie diesen Befehl kopieren, ersetzen Sie **Global** durch den Namen Ihrer Richtlinie und **contoso.com** durch Ihre eigene Domäne.

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookWarnTrustedDomains="contoso.com"}    
    ```

    > [!TIP]
    > Wenn Sie diese Einstellung auf mehrere Domänen anwenden möchten, z. B. zum Hinzufügen vertrauenswürdiger Partner, listen Sie deren Domänen in dem Wert durch Kommas getrennt auf.

1. Testen Sie Ihre Einstellung in Outlook:

    1. Öffnen oder starten Sie Outlook auf dem Clientcomputer, um die aktualisierten Einstellungen abzurufen.

    1. Erstellen Sie eine neue E-Mail-Nachricht, und wenden Sie die Bezeichnung **Allgemein** an. Wählen Sie in der Symbolleiste der Meldung die Schaltfläche :::image type="icon" source="media/i-sensitivity.PNG" border="false"::: **Vertraulichkeit** und dann **Allgemein** aus.

    1. Geben Sie im Feld **An** Ihre eigene E-Mail-Adresse und im Feld **Betreff**: `Testing a warning message for the General label` ein, und senden Sie dann die E-Mail.

        Die E-Mail wird gesendet, und es wird keine Warnung angezeigt.

## <a name="request-users-to-justify-sending-unlabeled-content"></a>Auffordern von Benutzern, das Senden von nicht bezeichneten Inhalten zu begründen

In diesem Verfahren wird beschrieben, wie erweiterte Einstellungen so konfiguriert werden, dass Benutzer das Senden von nicht bezeichneten Inhalten begründen müssen. 

1. Führen Sie auf dem Clientcomputer PowerShell als Administrator aus.

1. Damit Outlook eine Legitimationsmeldung für die Benutzer anzeigt, wenn sie versuchen, eine nicht bezeichnete E-Mail zu senden, ersetzen Sie **Global** durch den Namen Ihrer Richtlinie. Führen Sie dann Folgendes aus:
 
    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationAction="Justify"}
    ```

1. Testen Sie Ihre Einstellung in Outlook:

    1. Öffnen oder starten Sie Outlook auf dem Clientcomputer, um die aktualisierten Einstellungen abzurufen.

    1. Erstellen Sie eine neue E-Mail-Nachricht, und stellen Sie sicher, dass keine Bezeichnung angewendet wird.
    
        Wenn Ihre Richtlinie z. B. eine Standardbezeichnung anwendet, verwenden Sie die Schaltfläche :::image type="icon" source="media/i-sensitivity.PNG" border="false":::, um sie zu entfernen. 

    1. Geben Sie im Feld **An** Ihre eigene E-Mail-Adresse und im Feld **Betreff**: `Testing the justification message for unlabeled content` ein, und senden Sie dann die E-Mail.
    
        Es wird ein Popupfenster ähnlich dem folgenden angezeigt:

        :::image type="content" source="media/qs-tutor/ul-see-nolabljustify.png" alt-text="Beispiel für eine Legitimationsmeldung für nicht bezeichneten Inhalt":::

    1. Wählen Sie eine der Optionen aus. Wenn Sie die dritte Option **Sonstige, wie angegeben** auswählen, geben Sie in das Textfeld einen Beispieltext ein. 
    
    1. Wählen Sie **Bestätigen und senden** aus.
    
        Die E-Mail wird gesendet.

Fahren Sie mit Abschnitt [Anpassen der Eingabeaufforderung zur Legitimation mit freier Texteingabe](#customize-the-free-text-justification-prompt) fort.

## <a name="customize-the-free-text-justification-prompt"></a>Anpassen der Eingabeaufforderung zur Legitimation mit freier Texteingabe

In diesem Verfahren wird beschrieben, wie Sie die dritte Option in der standardmäßigen Legitimationsmeldung anpassen. 

Sie können dort zum Beispiel Text hinzufügen, um den Benutzer zur Eingabe bestimmter Details aufzufordern oder die Benutzer daran zu erinnern, keine vertraulichen Daten einzugeben.

1. Führen Sie auf dem Clientcomputer PowerShell als Administrator aus.

1. Um die Freitext-Eingabeaufforderung in der angezeigten Legitimationsmeldung anzupassen, ersetzen Sie **Global** durch Ihren Richtliniennamen und führen Sie diese aus:

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{JustificationTextForUserText="Other (please explain) - Do not enter sensitive info"}
    ```

    > [!TIP]
    > Es steht Ihnen frei, den Wert in Anführungszeichen durch einen anderen Text zu ersetzen, den Sie stattdessen dort einfügen möchten. 

1. Testen Sie Ihre Einstellung in Outlook:

    1. Öffnen oder starten Sie Outlook auf dem Clientcomputer, um die aktualisierten Einstellungen abzurufen.

    1. Erstellen Sie eine neue E-Mail-Nachricht, und stellen Sie sicher, dass keine Bezeichnung angewendet wird. 

        Wenn Ihre Richtlinie z. B. eine Standardbezeichnung anwendet, verwenden Sie die Schaltfläche :::image type="icon" source="media/i-sensitivity.PNG" border="false":::, um sie zu entfernen. 

    1. Geben Sie im Feld **An** Ihre eigene E-Mail-Adresse und im Feld **Betreff**: `Testing a customized free text justification prompt` ein, und senden Sie dann die E-Mail.
    
        Das Popupfenster für die Legitimation wird angezeigt, diesmal mit Ihrem angepassten Text. Beispiel: 

        :::image type="content" source="media/qs-tutor/ul-see-nolabljustify-custom.png" alt-text="Beispiel für angepasste Eingabeaufforderung zur Legitimation mit Freitexteingabe":::
        
## <a name="block-users-from-sending-unlabeled-powerpoint-messages"></a>Verhindern des Sendens von Nachrichten mit PowerPoint-Dateien ohne Bezeichnung

In diesem Verfahren wird beschrieben, wie Sie verhindern können, dass Benutzer PowerPoint-Dateien ohne Bezeichnung über Outlook senden.

1. Führen Sie auf dem Clientcomputer PowerShell als Administrator aus.

1. Damit keine Inhalte ohne Bezeichnung über Outlook gesendet werden, ersetzen Sie **Global** durch ihren Richtliniennamen. Führen Sie dann Folgendes aus:

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationAction="Block"}
    ```

1. Um das Blockierverhalten nur auf bestimmte PowerPoint-Dateitypen zu beschränken, ersetzen Sie **Global** durch Ihren Richtliniennamen. Führen Sie dann Folgendes aus:

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookOverrideUnlabeledCollaborationExtensions=".PPTX,.PPTM,.POTX,.POTM,.POT,.PPTX"}
    ```

1. Testen Sie Ihre Einstellung in Outlook:

    1. Öffnen Sie PowerPoint auf dem Clientcomputer, und erstellen Sie eine neue **PPTX**-Datei. Stellen Sie sicher, dass die Datei keine Bezeichnung hat.

    1. Öffnen oder starten Sie Outlook, um die aktualisierten Einstellungen abzurufen.
    
    1. Fügen Sie Ihre PowerPoint-Datei ohne Bezeichnung an eine neue Outlook-Nachricht an.

    1. Geben Sie im Feld **An** Ihre eigene E-Mail-Adresse und im Feld **Betreff**: `Testing sending unlabeled PowerPoint files` ein, und senden Sie dann die E-Mail.
    
        Outlook blockiert das Senden der E-Mail und zeigt die folgende Meldung an:

        :::image type="content" source="media/qs-tutor/ul-see-blockmessage.png" alt-text="Beispiel für eine Blockiermeldung für eine PowerPoint-Anlage ohne Bezeichnung":::

Fahren Sie mit Abschnitt [Anpassen der Blockiermeldung für Nachrichten mit PowerPoint-Dateien ohne Bezeichnung](#customize-the-block-message-for-unlabeled-powerpoint-messages) fort.

## <a name="customize-the-block-message-for-unlabeled-powerpoint-messages"></a>Anpassen der Blockiermeldung für Nachrichten mit PowerPoint-Dateien ohne Bezeichnung

In diesem Verfahren wird beschrieben, wie Sie die Meldung anpassen, die einem Benutzer angezeigt wird, der eine PowerPoint-Datei ohne Bezeichnung an externe Benutzer senden möchte.

> [!IMPORTANT]
> Mit diesem Verfahren werden alle Einstellungen außer Kraft gesetzt, die Sie bereits mit der erweiterten Eigenschaft **OutlookUnlabeledCollaborationAction** definiert haben, und nur zu Lernzwecken im Tutorial angezeigt.
>
> Es wird empfohlen, in der Produktionsumgebung Probleme zu vermeiden, indem Sie *entweder* die erweiterte Eigenschaft **OutlookUnlabeledCollaborationAction** verwenden, um Ihre Regeln zu definieren, *oder* komplexe Regeln mit einer JSON-Datei wie unten beschrieben definieren, aber nicht beides.
>

**So definieren Sie eine Regel mithilfe einer JSON-Datei**:

1. Erstellen Sie eine **JSON**-Datei mit dem Namen **OutlookCollaborationRule_1.json** und dem folgenden Code:

    ```JSON
    {   
    "type" : "And",     
    "nodes" : [         
        {           
            "type" : "Except" ,             
            "node" :{               
                "type" : "SentTo",                  
                "Domains" : [                   
                    "contoso.com",                  
                ]               
            }       
        },
        {           
            "type" : "Or",          
            "nodes" : [                 
                {           
                    "type" : "AttachmentLabel",
                     "LabelId" : null,
                    "Extensions": [
                                    ".PPTX",
                                    ".PPTM",
                                    ".POTX",
                                    ".POTM",
                                    ".POT",
                                    ".PPTX"
                                 ]
                    
                },
                {                   
                    "type" : "EmailLabel",
                     "LabelId" : null
                }
            ]
        },      
        {           
            "type" : "Email Block",             
            "LocalizationData": {               
                "en-us": {                
                    "Title": "Email Blocked",                 
                    "Body": "Sending PowerPoint files to external recipients requires that you label your files so that we can classify and protect Contoso content.<br><br>List of attachments that are not labeled:<br><br>${MatchedAttachmentName}<br><br><br>This message will not be sent.<br>You are responsible for ensuring compliance to classification requirement as per Contoso’s policies.<br><br>Label your document and send it again."              
                },          
            },          
            "DefaultLanguage": "en-us"      
        }   
      ] 
    }
    ```
1. Speichern Sie Ihre **OutlookCollaborationRule_1.json**-Datei an einem Ort, auf den Ihr Clientcomputer Zugriff hat.

1. Führen Sie auf dem Clientcomputer PowerShell als Administrator aus.

1. Um die Blockiermeldung anzupassen, kopieren Sie den folgenden Code und ersetzen **C:\OutlookCollaborationRule_1.json** durch den Pfad zu Ihrer JSON-Datei und **Allgemein** durch den Namen Ihrer Richtlinie. 

    ```PowerShell
    $filedata = Get-Content "C:\OutlookCollaborationRule_1.json”
    Set-LabelPolicy -Identity General -AdvancedSettings @{OutlookCollaborationRule_1 ="$filedata"}    
    ```

    Führen Sie den Code aus, um die in der JSON-Datei definierten Einstellungen zu übernehmen.

1. Testen Sie Ihre Einstellung in Outlook:

    1. Öffnen Sie PowerPoint auf dem Clientcomputer, und erstellen Sie eine neue **PPTX**-Datei. Stellen Sie sicher, dass die Datei keine Bezeichnung hat.

    1. Öffnen oder starten Sie Outlook, um die aktualisierten Einstellungen abzurufen.
    
    1. Fügen Sie Ihre PowerPoint-Datei ohne Bezeichnung an eine neue Outlook-Nachricht an.

    1. Geben Sie im Feld **An** Ihre eigene E-Mail-Adresse und im Feld **Betreff**: `Testing customized blocking message for unlabeled PowerPoint files` ein, und senden Sie dann die E-Mail.
    
        Outlook blockiert das Senden der E-Mail und zeigt die folgende Meldung an:

        :::image type="content" source="media/qs-tutor/ul-see-custom-blockmessage.png" alt-text="Angepasste Blockiermeldung für PowerPoint-Dateien ohne Bezeichnung":::

Fahren Sie mit Abschnitt [Verwenden des Ereignisprotokolls zum Identifizieren der Meldungen und Benutzeraktionen für die Bezeichnung „Allgemein“](#use-event-log-to-identify-the-messages-and-user-actions-for-the-general-label)

## <a name="use-event-log-to-identify-the-messages-and-user-actions-for-the-general-label"></a>Verwenden des Ereignisprotokolls zum Identifizieren der Meldungen und Benutzeraktionen für die Bezeichnung „Allgemein“

In diesem Tutorial haben Sie gelernt, wie Sie das Verhalten von AIP in Outlook anpassen können, um einige Typen von übermäßigen Freigaben zu verhindern, einschließlich Warnungs-, Legitimations- und Blockiermeldungen. Zudem haben Sie das Verhalten von Outlook auf dem lokalen Clientcomputer geprüft.

Nun können Sie die Windows-Ereignisanzeige starten, um die Protokolle für die aufgetretenen Ereignisse einzusehen.

**So überprüfen Sie die Ereignisanzeige für AIP-Protokollierungsereignisse**:

Öffnen Sie auf Ihrem Clientcomputer die Windows-Ereignisanzeige, und navigieren Sie zu **Anwendungs- und Dienstprotokolle** > **Azure Information Protection**.

Sie sehen, dass für jeden ausgeführten Test ein Informationsereignis mit Details zur Meldung und Benutzerantwort protokolliert wurde:

- **Warnungsmeldungen**: Informations-ID 301
- **Legitimationsmeldungen**: Informations-ID 302
- **Blockiermeldungen**: Informations-ID 303

Beispiel:

- [Überprüfen des Ereignisprotokolls für die Tests der Warnungsmeldung](#check-the-event-log-for-your-warning-message-tests)
- [Überprüfen des Ereignisprotokolls für die Tests der Legitimationsmeldung](#check-the-event-log-for-your-justify-message-tests)
- [Überprüfen des Ereignisprotokolls für die Tests der Blockiermeldung](#check-the-event-log-for-your-block-message-tests)

### <a name="check-the-event-log-for-your-warning-message-tests"></a>Überprüfen des Ereignisprotokolls für die Tests der Warnungsmeldung

Im ersten Test wurde der Benutzer gewarnt, und Sie haben **Abbrechen** ausgewählt. In diesem Fall wird im ersten Ereignis 301 für **Benutzerantwort** **Verworfen** angezeigt:

```
Client Version: 2.8.85.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing a warning message for the General label.msg
Item Name: Testing a warning message for the General label
Process Name: OUTLOOK
Action: Warn
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
Action Source: 
User Response: Dismissed
```

Sie haben allerdings **Bestätigen und senden** ausgewählt, was im nächsten Ereignis 301 wiedergegeben wird, in dem **Confirmed** (Bestätigt) als **Benutzerantwort** angezeigt wird:

```
Client Version: 2.8.85.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing a warning message for the General label.msg
Item Name: Testing a warning message for the General label
Process Name: OUTLOOK
Action: Warn
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
Action Source: 
User Response: Confirmed
```

### <a name="check-the-event-log-for-your-justify-message-tests"></a>Überprüfen des Ereignisprotokolls für die Tests der Legitimationsmeldung

Das gleiche Muster wird für die Legitimationsmeldung wiederholt, die ein Ereignis 302 aufweist. Das erste Ereignis zeigt **Dismissed** (Verworfen) als **Benutzerantwort** an, und das zweite zeigt die ausgewählte Begründung an. Beispiel:

```
Client Version: 2.8.85.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing the justification message for unlabeled content.msg
Item Name: Testing the justification message for unlabeled content
Process Name: OUTLOOK
Action: Justify
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
User Justification: I confirm the recipients are approved for sharing this content
Action Source: 
User Response: Confirmed

```

### <a name="check-the-event-log-for-your-block-message-tests"></a>Überprüfen des Ereignisprotokolls für die Tests der Blockiermeldung

Oben im Ereignisprotokoll sehen Sie die protokollierte Blockierungsmeldung, die ein Ereignis 303 aufweist. Beispiel:

```
Client Version: 2.8.85.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Testing sending unlabeled PowerPoint files.msg
Item Name: Testing sending unlabeled PowerPoint files
Process Name: OUTLOOK
Action: Block
Label After Action: General
Label ID After Action: 0e421e6d-ea17-4fdb-8f01-93a3e71333b8
Action Source: 
```

## <a name="clean-up-resources"></a>Bereinigen von Ressourcen

Nach Abschluss dieses Tutorials können Sie die Testrichtlinien zur weiteren Verwendung aufbewahren oder sie löschen, um Ihre Ressourcen zu bereinigen.

Wenn Sie die Richtlinie löschen möchten, nutzen Sie hierzu das Admin Center, in dem sie erstellt wurde, d. h. entweder das Microsoft 365 Compliance Center, das Microsoft 365 Security Center oder das Microsoft 365 Security & Compliance Center.

Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](https://docs.microsoft.com/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy).

Starten Sie Outlook nach dem Löschen auf dem Clientcomputer neu, sodass es nicht mehr mit den in diesem Tutorial definierten Einstellungen konfiguriert ist.

## <a name="next-steps"></a>Nächste Schritte

In diesem Tutorial wurde eine E-Mail-Nachricht ohne Anhang an einen einzelnen Empfänger verwendet, um schneller testen zu können. 

Wenden Sie die gleichen Methoden mit mehreren Empfängern und Bezeichnungen oder auf Anlagen an, deren Bezeichnungsstatus für die Benutzer manchmal weniger offensichtlich ist.

Beispielsweise können Sie eine Popupmeldung bei E-Mail-Nachrichten mit der Bezeichnung **Öffentlich** anzeigen, wobei eine PowerPoint-Präsentation mit der Bezeichnung **Allgemein** angefügt wird.

Weitere Informationen zu erweiterten Eigenschaften und Outlook-Anpassungen finden Sie im [Admin Guide: Custom configurations for the Azure Information Protection unified labeling client](rms-client/clientv2-admin-guide-customizations.md) (Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client für einheitliche Bezeichnungen).
