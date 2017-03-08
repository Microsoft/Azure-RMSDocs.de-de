---
title: "Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung"
description: "Beim Konfigurieren einer Bezeichnung zur Verwendung von Rights Management-Schutz können Sie Ihre sensibelsten Dokumente und E-Mails schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/27/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 5bc117cbff3226a2ee0ff375f0aa02fc3232a183
ms.openlocfilehash: ed6bd63a945b73b792bcafcdc0d07e08e83fc344
ms.lasthandoff: 02/27/2017


---

# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurieren einer Bezeichnung für Rights Management-Schutz

>*Gilt für: Azure Information Protection*

Schützen Sie Ihre vertraulichen Dokumente und E-Mails mithilfe der Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien des Rights Management-Diensts, mit dem sich Datenverlust verhindern lässt. Dieser Schutz wird angewendet, wenn Sie eine Bezeichnung so konfigurieren, dass sie eine Rights Management-Vorlage für Dokumente und E-Mails oder die Option **Nicht weiterleiten** für Outlook-E-Mail-Nachrichten verwendet. 

Bei der Vorlage kann es sich um eine der beim Aktivieren von Azure Rights Management automatisch erstellten Standardvorlagen oder um eine benutzerdefinierte Vorlage handeln. Azure Rights Management-Abteilungsvorlagen werden unterstützt, wenden den Schutz jedoch nur an, wenn der Verfasser des Dokuments oder der E-Mail zum konfigurierten Bereich der Vorlage gehört. Wenn der Benutzer nicht zu diesem Bereich gehört, wird in einer Meldung angezeigt, dass Azure Information Protection die Bezeichnung nicht anwenden kann.

## <a name="how-the-protection-works"></a>Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail mit Rights Management geschützt wird, werden die Inhalte in ruhendem Zustand und während der Übertragung verschlüsselt. Eine Entschlüsselung ist nur durch autorisierte Benutzer möglich. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das vertrauliche, geschäftliche Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail über eine bevorstehende Promo-Aktion bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich lesen.

- Benutzer können keine E-Mail weiterleiten, die Nachrichten über eine interne Neuorganisation enthält.

- Die aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zu Azure Rights Management-Vorlagen sowie zur Konfiguration dieser Nutzungsrechte und Einschränkungen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).

Weitere Informationen zu Azure Rights Management sowie zur Funktionsweise dieser Lösung finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung des Azure Rights Management-Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Wenn Sie den Dienst noch nicht aktiviert haben, finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md) weitere Informationen.

Exchange muss für Information Rights Management (IRM) nicht konfiguriert sein, damit Benutzer in Outlook Bezeichnungen zum Schutz ihrer E-Mails verwenden können. Sie können jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn Exchange für IRM konfiguriert ist. Ohne diese Konfiguration können Benutzer beispielsweise geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook Web Access anzeigen, diese Mails können nicht für die Suche indiziert werden, und Sie können Exchange Online DLP nicht für den Rights Management-Schutz konfigurieren. Weitere Informationen zum Konfigurieren von Exchange, um diese zusätzlichen Szenarien zu unterstützen, finden Sie in den folgenden Ressourcen:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Für lokales Exchange müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](../deploy-use/deploy-rms-connector.md). 


## <a name="to-configure-a-label-for-rights-management-protection"></a>Konfigurieren einer Bezeichnung für Rights Management-Schutz

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, melden Sie sich als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 

    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gilt, wählen Sie **Global** auf dem Blatt **Azure Information Protection** aus. Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie statt dessen die bereichsbezogene Richtlinie aus.

3. Wählen Sie auf dem Blatt **Richtlinie** die Bezeichnung aus, die Sie konfigurieren möchten. Dadurch wird das Blatt **Bezeichnung** geöffnet. 

4. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus.
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit zum Anwenden von Schutz konfiguriert ist und die ausgewählte Bezeichnung keinen Schutz mehr anwenden soll. Fahren Sie dann mit Schritt 10 fort.
    
    - **Schützen**: Wählen Sie diese Option aus, um Schutz anzuwenden, und fahren Sie dann mit Schritt 5 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn er für ein Dokument oder eine E-Mail-Adresse konfiguriert ist. Fahren Sie dann mit Schritt 10 fort.
        
        Beachten Sie, dass Benutzer Berechtigungen zum Entfernen des Rights Management-Schutzes benötigen, um eine Bezeichnung mit dieser Option anzuwenden. Diese Option erfordert, dass der Benutzer über das [Nutzungsrecht](../deploy-use/configure-usage-rights.md) **Exportieren** oder **Vollzugriff** verfügt. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](../deploy-use/configure-super-users.md) fungieren. Die Azure Rights Management-Standardvorlagen umfassen nicht die Nutzungsrechte, die Benutzer zum Aufheben des Schutzes benötigen. 
        
        Wenn ein Benutzer keine Berechtigungen zum Entfernen des Rights Management-Schutzes hat und eine mit der Option **Schutz entfernen** konfigurierte Bezeichnung auswählt, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**

5. Wenn Sie **Schützen** ausgewählt haben, klicken Sie jetzt auf **Schutz**, um das Blatt **Schutz** zu öffnen:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar.png)

6. Wählen Sie auf dem Blatt **Schutz** die Option **Azure RMS** oder **HYOK (AD RMS)** aus. 
    
    In den meisten Fällen wählen Sie **Azure RMS** für Ihre Berechtigungseinstellungen. Wählen Sie nicht **HYOK (AD RMS)** aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser „*Hold-your-own-key*“-Konfiguration (HYOK) einhergehen. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz). Um die Konfiguration für HYOK (AD RMS) fortzufahren, gehen Sie zu Schritt 9.
    
7. Wählen Sie entweder **Nicht weiterleiten** aus, wenn Sie diese Outlook-Option für E-Mails festlegen möchten, oder wählen Sie **Vorlage auswählen** aus. 
    
8. Falls Sie **Vorlage auswählen** für **Azure RMS** ausgewählt haben: Klicken Sie in der Dropdownliste auf die [Vorlage](../deploy-use/configure-custom-templates.md), die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen.
    
    Bei Auswahl einer **Abteilungsvorlage** oder wenn Sie [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
    - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**
    
        Beachten Sie, dass immer alle Vorlagen angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Konfigurieren Sie z. B. eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die Azure RMS-Vorlagen, die Sie auswählen können, werden nicht auf Vorlagen beschränkt, die auf den Bereich „Marketing“ bezogen sind, und es ist möglich, eine abteilungsbezogene Vorlage auszuwählen, die Ihre ausgewählten Benutzer nicht verwenden können. Zur Vereinfachung der Konfiguration und zum Minimieren der Problembehandlung können Sie die Abteilungsvorlage gemäß der Bezeichnung in der bereichsbezogenen Richtlinie benennen. 
            
9. Falls Sie **Vorlage auswählen** für **HYOK (AD RMS)** ausgewählt haben: Stellen Sie die Vorlagen-GUID und die Lizenzierungs-URL Ihres AD RMS-Clusters bereit. [Weitere Informationen](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

10. Klicken Sie auf **OK**, um das Blatt **Schutz** zu schließen und die Auswahl für **Nicht weiterleiten** bzw. die ausgewählte Vorlage für die Option **Schutz** auf dem Blatt **Bezeichnung** anzuzeigen.

10. Klicken Sie auf dem Blatt **Bezeichnung** auf **Speichern**.

11. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
