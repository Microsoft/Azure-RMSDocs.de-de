---
title: Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden | Azure Information Protection
description: "Schützen Sie Ihre vertraulichen Dokumente und E-Mails mithilfe der Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien des Rights Management-Diensts, mit dem sich Datenverlust verhindern lässt. Dieser Schutz wird angewendet, wenn Sie eine Bezeichnung für die Verwendung einer Rights Management-Vorlage konfigurieren."
manager: mbaldwin
ms.date: 09/14/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: fc390680918a08405e914a858c64bb723efa5580
ms.openlocfilehash: ca1534801facc6273d481cc99f23ec8acd5341d1


---

# Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Schützen Sie Ihre vertraulichen Dokumente und E-Mails mithilfe der Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien des Rights Management-Diensts, mit dem sich Datenverlust verhindern lässt. Dieser Schutz wird angewendet, wenn Sie eine Bezeichnung für die Verwendung einer Rights Management-Vorlage konfigurieren. 

Bei dieser Vorlage kann es sich um eine der Standardvorlagen handeln, die beim Aktivieren von Azure Rights Management automatisch erstellt werden, oder um eine benutzerdefinierte Vorlage. Azure Rights Management-Abteilungsvorlagen werden unterstützt, wenden den Schutz jedoch nur an, wenn der Verfasser des Dokuments oder der E-Mail zum konfigurierten Bereich der Vorlage gehört. Wenn der Benutzer nicht zu diesem Bereich gehört, wird in einer Meldung angezeigt, dass Azure Information Protection die Bezeichnung nicht anwenden kann.

## Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail mit Rights Management geschützt wird, werden die Inhalte in ruhendem Zustand und während der Übertragung verschlüsselt. Eine Entschlüsselung ist nur durch autorisierte Benutzer möglich. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das vertrauliche, geschäftliche Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail über eine bevorstehende Promo-Aktion bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich lesen.

- Benutzer können keine E-Mail weiterleiten, die Nachrichten über eine interne Neuorganisation enthält.

- Die aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zu Azure Rights Management-Vorlagen sowie zur Konfiguration dieser Nutzungsrechte und Einschränkungen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).

Weitere Informationen zu Azure Rights Management sowie zur Funktionsweise dieser Lösung finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung des Azure Rights Management-Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Wenn Sie den Dienst noch nicht aktiviert haben, finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md) weitere Informationen.


## Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich beim [Azure-Portal](https://portal.azure.com) als globaler Administrator an, damit Sie die Azure Rights Management-Vorlagen abrufen können. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 

    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wählen Sie auf dem Blatt **Azure Information Protection** die Bezeichnung aus, die Sie zur Anwendung des Rights Management-Schutzes konfigurieren möchten.

3. Wählen Sie im Abschnitt **RMS-Vorlage zum Schützen von Dokumenten und E-Mails mit dieser Bezeichnung festlegen** des **Blatts** der Bezeichnung unter **RMS-Vorlage auswählen von:** entweder **Azure RMS** oder **AD RMS (Vorschau)** aus.
    
    In den meisten Fällen wählen Sie **Azure RMS**. Wählen Sie nicht AD RMS aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser Konfiguration einhergehen, die auch manchmal als „*Hold-your-own-key*“ (HYOK) bezeichnet wird. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz).
    
4. Bei Auswahl von Azure RMS: Klicken Sie auf das Dropdownfeld für **RMS-Vorlage auswählen**, und wählen Sie die [Vorlage](../deploy-use/configure-custom-templates.md) oder Rechteverwaltungsoptionen, die Sie zum Schützen von Dokumenten und E-Mails mit dieser Bezeichnung verwenden möchten.
    
    Weitere Informationen zu den Optionen:
    
    - Haben Sie eine neue Vorlage erstellt, nachdem Sie das Blatt **Bezeichnung** geöffnet haben? Schließen Sie dieses Blatt, und gehen Sie zurück zu Schritt 2, damit Ihre neu erstellte Vorlage aus Azure abgerufen wird und zur Auswahl zur Verfügung steht.
    
    - Bei Auswahl einer **Abteilungsvorlage** oder wenn Sie [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
        - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**
        
    - Bei Auswahl der Option **Schutz entfernen**:
        
        - Benutzer benötigen Berechtigungen zum Entfernen des Rights Management-Schutzes, um eine Bezeichnung mit dieser Option anzuwenden. Diese Option erfordert, dass die Benutzer über das Nutzungsrecht Exportieren (für Office-Dokumente) oder Vollzugriff verfügen. Alternativ muss der Besitzer der Rights Management-Besitzer sein (dieser erhält automatisch Vollzugriff) oder als [Administrator für Azure Rights Management](../deploy-use/configure-super-users.md) fungieren. Die Rights Management-Standardvorlagen umfassen nicht die Nutzungsrechte, die Benutzer zum Aufheben des Schutzes benötigen. 

            Wenn Benutzer keine Berechtigungen zum Entfernen des Rights Management-Schutzes haben und diese Bezeichnung mit der Option **Schutz entfernen** auswählen, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**

5. Falls Sie AD RMS ausgewählt haben: Stellen Sie die Vorlagen-GUID und die Lizenzierungs-URL Ihres AD RMS-Clusters bereit. [Weitere Informationen](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. Klicken Sie auf **Speichern**.

7. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Sep16_HO3-->


