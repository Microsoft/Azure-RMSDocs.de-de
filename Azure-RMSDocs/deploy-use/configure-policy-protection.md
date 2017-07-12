---
title: "Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung"
description: "Beim Konfigurieren einer Bezeichnung zur Verwendung von Rights Management-Schutz können Sie Ihre sensibelsten Dokumente und E-Mails schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: f5c4e2f7513832a884820ec0c57c7da2dec5f04e
ms.sourcegitcommit: 8b768e7e249e124f24acdf630d165eaf743f9c21
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/05/2017
---
<a id="how-to-configure-a-label-for-rights-management-protection" class="xliff"></a>

# Konfigurieren einer Bezeichnung für Rights Management-Schutz

>*Gilt für: Azure Information Protection*

Schützen Sie Ihre vertraulichen Dokumente und E-Mails mithilfe der Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien des Rights Management-Diensts, mit dem sich Datenverlust verhindern lässt. Dieser Schutz wird angewendet, wenn Sie eine Bezeichnung so konfigurieren, dass sie eine Rights Management-Vorlage für Dokumente und E-Mails oder die Option **Nicht weiterleiten** für Outlook-E-Mail-Nachrichten verwendet. 

Bei der Vorlage kann es sich um eine der beim Aktivieren von Azure Rights Management automatisch erstellten Standardvorlagen oder um eine benutzerdefinierte Vorlage handeln. Azure Rights Management-Abteilungsvorlagen werden unterstützt, wenden den Schutz jedoch nur an, wenn der Verfasser des Dokuments oder der E-Mail zum konfigurierten Bereich der Vorlage gehört. Wenn der Benutzer nicht zu diesem Bereich gehört, wird in einer Meldung angezeigt, dass Azure Information Protection die Bezeichnung nicht anwenden kann.

<a id="how-the-protection-works" class="xliff"></a>

## Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail mit Rights Management geschützt wird, werden die Inhalte in ruhendem Zustand und während der Übertragung verschlüsselt. Eine Entschlüsselung ist nur durch autorisierte Benutzer möglich. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das vertrauliche, geschäftliche Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail zu einer bevorstehenden Werbeaktion bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich lesen.

- Benutzer können keine E-Mails weiterleiten oder darin enthaltene Informationen kopieren, die Nachrichten über eine interne Neuorganisation enthalten.

- Die aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zu Azure Rights Management-Vorlagen sowie zu ihrer Konfiguration im klassischen Azure-Portal finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).

Weitere Informationen zu Azure Rights Management sowie zur Funktionsweise dieser Lösung finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung des Azure Rights Management-Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Wenn Sie den Dienst noch nicht aktiviert haben, finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md) weitere Informationen.

Exchange muss für Information Rights Management (IRM) nicht konfiguriert sein, damit Benutzer in Outlook Bezeichnungen zum Schutz ihrer E-Mails verwenden können. Sie können jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn Exchange für IRM konfiguriert ist. Ohne diese Konfiguration können Benutzer beispielsweise geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook im Web anzeigen, derartige E-Mails können nicht für die Suche indiziert werden, und Sie können Exchange Online DLP nicht für den Rights Management-Schutz konfigurieren. Weitere Informationen zum Konfigurieren von Exchange, um diese zusätzlichen Szenarien zu unterstützen, finden Sie in den folgenden Ressourcen:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Für lokales Exchange müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](../deploy-use/deploy-rms-connector.md). 


<a id="to-configure-a-label-for-rights-management-protection" class="xliff"></a>

## Konfigurieren einer Bezeichnung für Rights Management-Schutz

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 

    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gilt, wählen Sie **Global** auf dem Blatt **Azure Information Protection** aus. Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie statt dessen die bereichsbezogene Richtlinie aus.

3. Wählen Sie auf dem Blatt **Richtlinie** die Bezeichnung aus, die Sie konfigurieren möchten. Dadurch wird das Blatt **Bezeichnung** geöffnet. 

4. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus.
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit zum Anwenden von Schutz konfiguriert ist und die ausgewählte Bezeichnung keinen Schutz mehr anwenden soll. Fahren Sie dann mit Schritt 11 fort.
    
    - **Schützen**: Wählen Sie diese Option aus, um Schutz anzuwenden, und fahren Sie dann mit Schritt 5 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn er für ein Dokument oder eine E-Mail-Adresse konfiguriert ist. Fahren Sie dann mit Schritt 11 fort.
        
        Beachten Sie, dass Benutzer Berechtigungen zum Entfernen des Rights Management-Schutzes benötigen, um eine Bezeichnung mit dieser Option anzuwenden. Diese Option erfordert, dass der Benutzer über das [Nutzungsrecht](../deploy-use/configure-usage-rights.md) **Exportieren** oder **Vollzugriff** verfügt. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](../deploy-use/configure-super-users.md) fungieren. Die Azure Rights Management-Standardvorlagen umfassen nicht die Nutzungsrechte, die Benutzer zum Aufheben des Schutzes benötigen. 
        
        Wenn ein Benutzer keine Berechtigungen zum Entfernen des Rights Management-Schutzes hat und eine mit der Option **Schutz entfernen** konfigurierte Bezeichnung auswählt, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**

5. Wenn Sie **Schützen** ausgewählt haben, klicken Sie jetzt auf **Schutz**, um das Blatt **Schutz** zu öffnen:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar.png)

6. Wählen Sie auf dem Blatt **Schutz** die Option **Azure RMS** oder **HYOK (AD RMS)** aus. 
    
    In den meisten Fällen wählen Sie **Azure RMS** für Ihre Berechtigungseinstellungen. Wählen Sie nicht **HYOK (AD RMS)** aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser „*Hold-your-own-key*“-Konfiguration (HYOK) einhergehen. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz). Um mit der Konfiguration für HYOK (AD RMS) fortzufahren, wechseln Sie zu Schritt 10.
    
7. Wählen Sie eine der folgenden Optionen aus:
    
    - **Nicht weiterleiten**: Zum Festlegen dieser Outlook-Option für E-Mails.
    
    - **Vordefinierte Vorlage auswählen**: Zum Verwenden einer der Standardvorlagen oder einer benutzerdefinierten Vorlage, die Sie konfiguriert haben.
    
    - **Berechtigungen festlegen (Vorschau)** zum Definieren neuer Schutzeinstellungen in diesem Portal.

8. Falls Sie **Vordefinierte Vorlage auswählen** für **Azure RMS** ausgewählt haben, klicken Sie in der Dropdownfeld auf die [Vorlage](../deploy-use/configure-custom-templates.md), die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen.
    
    Bei Auswahl einer **Abteilungsvorlage** oder wenn Sie [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
    - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**
    
        Beachten Sie, dass immer alle Vorlagen angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Konfigurieren Sie z. B. eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die Azure RMS-Vorlagen, die Sie auswählen können, werden nicht auf Vorlagen beschränkt, die auf den Bereich „Marketing“ bezogen sind, und es ist möglich, eine abteilungsbezogene Vorlage auszuwählen, die Ihre ausgewählten Benutzer nicht verwenden können. Zur Vereinfachung der Konfiguration und zum Minimieren der Problembehandlung können Sie die Abteilungsvorlage gemäß der Bezeichnung in der bereichsbezogenen Richtlinie benennen. 
            
9. Wenn Sie **Berechtigungen festlegen (Vorschau)** für **Azure RMS** ausgewählt haben, weist diese Option die meisten Konfigurationsoptionen für [benutzerdefinierte Vorlagen](configure-custom-templates.md) auf, die Sie im klassischen Azure-Portal konfigurieren können. Darüber hinaus können Sie problemlos alle Benutzer aus Ihrer Organisation hinzufügen und externe E-Mail-Adressen für einzelne Benutzer oder Gruppen oder für alle Benutzer in einer anderen Organisation angeben, wenn Sie einen Domänennamen angeben. 
    
    Weitere Informationen zu dieser Vorschau-Konfiguration finden Sie im Blogbeitrag [Azure Information Protection unified administration now in Preview (Einheitliche Verwaltung für Azure Information Protection jetzt in der Vorschau)](https://blogs.technet.microsoft.com/enterprisemobility/2017/04/26/azure-information-protection-unified-administration-now-in-preview/). 
    
    Weitere Informationen zu den Berechtigungen, die Sie auswählen können, finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md).
    
    Überprüfen Sie bei der Option **Berechtigungen festlegen (Vorschau)** auch, ob Sie Änderungen an den folgenden Einstellungen vornehmen möchten. Beachten Sie, dass diese Einstellungen wie bei den Berechtigungen nicht für den [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder einen beliebigen zugewiesenen [Administrator](configure-super-users.md) gelten.
    
    |Einstellung|Weitere Informationen|Empfohlene Einstellung
    |-----------|--------------------|--------------------|
    |**Inhalt läuft ab am**|Definieren Sie ein Datum oder eine Anzahl von Tagen für diese Vorlage, nach deren Ablauf Dokumente oder E-Mails, die durch diese Vorlage geschützt sind, nicht mehr von ausgewählten Benutzern geöffnet werden sollen. Sie können ein Datum oder eine Anzahl von Tagen beginnend ab dem Zeitpunkt angeben, an dem der Schutz auf den Inhalt angewendet wird.<br /><br />Wenn Sie ein Datum angeben, wird der Schutz ab Mitternacht in Ihrer aktuellen Zeitzone wirksam.|**Inhalt läuft nie ab**, sofern für den Inhalt keine bestimmten zeitgebundenen Anforderungen vorliegen.|
    |**Offlinezugriff zulassen**|Mit dieser Einstellung können Sie Ihre bestehenden Sicherheitsanforderungen abstimmen (einschließlich des Zugriffs nach einem Widerruf) mit der Möglichkeit für ausgewählte Benutzer, geschützte Inhalte zu öffnen, wenn keine Internetverbindung besteht.<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich diese Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und ihre Zugriffe werden protokolliert. Wenn ihre Anmeldeinformationen nicht zwischengespeichert wurden, werden Benutzer in diesem Fall aufgefordert, sich anzumelden, bevor sie das Dokument oder die E-Mail öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden die Richtlinie und die Benutzergruppenmitgliedschaft erneut ausgewertet. Dies bedeutet, dass es bei Benutzern für dasselbe Dokument oder dieselbe E-Mail zu unterschiedlichen Zugriffsergebnissen kommen kann, wenn sich seit ihrem letzten Zugriff auf den Inhalt Änderungen an der Richtlinie oder ihrer Gruppenmitgliedschaft ereignet haben. Dies könnte dazu führen, dass der Zugriff verweigert wird, wenn das Dokument [widerrufen](../rms-client/client-track-revoke.md) wurde.|Je nach Wichtigkeit des Inhalts:<br /><br />- **Anzahl der Tage, die der Inhalt ohne Internetverbindung verfügbar ist** = **7** für sensible Geschäftsdaten, die dem Unternehmen schaden können, wenn sie an unbefugte Personen weitergegeben werden. Diese Empfehlung bietet einen ausgewogenen Kompromiss zwischen Flexibilität und Sicherheit. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebsdaten.<br /><br />- **Nie** bei sehr sensiblen Geschäftsdaten, die dem Unternehmen schaden würden, wenn sie an Unbefugte weitergegeben werden. Diese Empfehlung räumt der Sicherheit Vorrang gegenüber Flexibilität ein und stellt sicher, dass unmittelbar nach einem Widerruf des Dokument keine der autorisierten Benutzer das Dokument öffnen können. Beispiele hierfür sind Mitarbeiter- und Kundeninformationen, Kennwörter, Quellcode und vorangekündigte Finanzberichte.|
    
    Bei dieser Gruppierung von Einstellungen wird eine benutzerdefinierte Vorlage für den Azure Rights Management-Dienst erstellt. Diese Vorlagen können in Anwendungen und Diensten verwendet werden, die in Azure Rights Management integriert sind. Informationen zum Herunterladen und Aktualisieren dieser Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

10. Falls Sie **Vorlage auswählen** für **HYOK (AD RMS)** ausgewählt haben: Stellen Sie die Vorlagen-GUID und die Lizenzierungs-URL Ihres AD RMS-Clusters bereit. [Weitere Informationen](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

11. Klicken Sie auf **OK**, um das Blatt **Schutz** zu schließen und die Auswahl für **Nicht weiterleiten** bzw. die ausgewählte Vorlage für die Option **Schutz** auf dem Blatt **Bezeichnung** anzuzeigen.

12. Klicken Sie auf dem Blatt **Bezeichnung** auf **Speichern**.

13. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

<a id="next-steps" class="xliff"></a>

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]