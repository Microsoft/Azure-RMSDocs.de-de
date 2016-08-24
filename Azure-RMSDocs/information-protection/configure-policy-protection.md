---
title: Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden | Azure Rights Management
description: 
author: cabailey
manager: mbaldwin
ms.date: 08/15/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: e11a5a836d6a410ba49ac17cfe95d8530ecb785f
ms.openlocfilehash: 60738c310a3e7c734bfe3e48e16535ed3be05bb4


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

1. Wenn Sie dies noch nicht getan haben, melden Sie sich beim [Azure-Portal](https://portal.azure.com) als ein globaler Administrator an, damit Sie die Azure Rights Management-Vorlagen abrufen können. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 

    Klicken Sie z.B. im Hubmenü auf **Durchsuchen**, und geben Sie **Information** im Filterfeld ein. Wählen Sie **Azure Information Protection** aus.

2. Wählen Sie auf dem Blatt **Azure Information Protection** die Bezeichnung aus, die Sie zur Anwendung des Rights Management-Schutzes konfigurieren möchten.

3. Wählen Sie im Abschnitt **RMS-Vorlage zum Schützen von Dokumenten und E-Mails mit dieser Bezeichnung festlegen** des **Blatts** der Bezeichnung unter **RMS-Vorlage auswählen von:** entweder **Azure RMS** oder **AD RMS (Vorschau)** aus.
    
    In den meisten Fällen wählen Sie **Azure RMS**. Wählen Sie nicht AD RMS aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser Konfiguration einhergehen, die auch manchmal als „*Hold-your-own-key*“ (HYOK) bezeichnet wird. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz).
    
4. Falls Sie Azure RMS ausgewählt haben: Wählen Sie für **Select RMS template** (RMS-Vorlage auswählen) die Vorlage der Dropdownliste aus, die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen.

    > [!NOTE] 
    > Wenn Sie nach dem Öffnen des Blatts **Label** (Bezeichnung) eine neue Vorlage erstellen, schließen Sie dieses Blatt, und kehren Sie zu Schritt 2 zurück, damit Azure Ihre neu erstellte Vorlage abrufen und zur Auswahl anzeigen kann.
    
    Beachten Sie Folgendes, wenn Sie eine Abteilungsvorlage auswählen oder [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
    - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**
    
5. Falls Sie AD RMS ausgewählt haben: Stellen Sie die Vorlagen-GUID und die Lizenzierungs-URL Ihres AD RMS-Clusters bereit. [Weitere Informationen](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

6. Klicken Sie auf **Speichern**.

7. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Aug16_HO3-->


