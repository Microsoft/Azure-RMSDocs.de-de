---
title: Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden | Azure Rights Management
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
translationtype: Human Translation
ms.sourcegitcommit: 00b4cd2b1e7b1196cedd39d7052db534e781bb13
ms.openlocfilehash: 7a20b59c404959c4ec209e8c29ac61ab71233e87


---

# Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Schützen Sie Ihre vertraulichen Dokumente und E-Mails mithilfe der Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien von Azure Rights Management, mit denen sich Datenverlust verhindern lässt. Dieser Schutz wird angewendet, wenn Sie eine Bezeichnung für die Verwendung einer Rights Management-Vorlage konfigurieren. 

Bei dieser Vorlage kann es sich um eine der Standardvorlagen handeln, die beim Aktivieren von Azure Rights Management automatisch erstellt werden, oder um eine benutzerdefinierte Vorlage. Abteilungsvorlagen werden unterstützt, wenden den Schutz jedoch nur an, wenn der Verfasser des Dokuments oder der E-Mail zum konfigurierten Bereich der Vorlage gehört. Wenn der Benutzer nicht zu diesem Bereich gehört, wird in einer Meldung angezeigt, dass Azure Information Protection die Bezeichnung nicht anwenden kann.

## Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail mit Azure Rights Management geschützt wird, werden die Inhalte in ruhendem Zustand und während der Übertragung verschlüsselt. Eine Entschlüsselung ist nur durch autorisierte Benutzer möglich. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich anzeigen.

- Benutzer können eine E-Mail nicht weiterleiten.

- Dokumente oder E-Mails, die an Geschäftspartner gesendet werden, können nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zu diesen Vorlagen sowie zur Konfiguration dieser Nutzungsrechte und Einschränkungen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).

Weitere Informationen zu Azure Rights Management sowie zur Funktionsweise dieser Lösung finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung des Rights Management-Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Wenn Sie den Dienst noch nicht aktiviert haben, finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md) weitere Informationen.


## Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
 
2. Klicken Sie anschließend im Hubmenü auf **Durchsuchen**, und geben Sie **Information** im Filterfeld ein. Wählen Sie **Azure Information Protection** aus.

3. Wählen Sie auf dem Blatt **Azure Information Protection** die Bezeichnung aus, die Sie zur Anwendung des Rights Management-Schutzes konfigurieren möchten.

4. Konfigurieren Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Set RMS template for protecting documents and emails containing this label** (RMS-Vorlage für den Schutz von Dokumenten und E-Mails mit dieser Bezeichnung festlegen) folgende Einstellungen:

    - Wenn **Select RMS template from** (RMS-Vorlage auswählen aus) angezeigt wird, wählen Sie **Azure RMS**. 
    
        Wählen Sie **AD RMS** und die zugehörigen Konfigurationsoptionen nur mit Unterstützung durch Microsoft. Wenn Sie Azure Information Protection mit Active Directory Rights Management Services testen möchten, senden Sie eine E-Mail an folgende Adresse: askipteam@microsoft.com 
    
    - Für **Select RMS template** (RMS-Vorlage auswählen): Wählen Sie in der Dropdownliste die Vorlage aus, die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen.

        > [!NOTE] Wenn Sie nach dem Öffnen des Blatts **Label** (Bezeichnung) eine neue Vorlage erstellen, schließen Sie dieses Blatt, und kehren Sie zu Schritt 3 zurück, damit Azure Ihre neu erstellte Vorlage abrufen und zur Auswahl anzeigen kann.

5. Klicken Sie auf **Speichern**.

6. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  



<!--HONumber=Jul16_HO5-->


