---
title: "Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection | Azure Rights Management"
description: 
author: cabailey
manager: mbaldwin
ms.date: 07/29/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
translationtype: Human Translation
ms.sourcegitcommit: 93444affe94b280db2c9e4e2960c6902e491dec6
ms.openlocfilehash: 9f2d28e4f162891497a7b0518322338628118b9d


---

# Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen:

Diese visuellen Kennzeichnungen werden beim Anwenden der Bezeichnung auf Word-, Excel- und PowerPoint-Dokumente angewendet sowie beim Speichern des Dokuments. Bei E-Mail-Nachrichten werden die visuellen Kennzeichnungen beim Senden der E-Mail angewendet.

Weitere Informationen zu diesen visuellen Kennzeichnungen finden Sie hier:

- Kopf- und Fußzeilen gelten für Word, Excel, PowerPoint und Outlook.

- Wasserzeichen gelten für Word, Excel und PowerPoint:

    - Excel: Wasserzeichen sind nur im Modus „Seitenlayout“ und „Seitenansicht“ sichtbar sowie beim Drucken.

    - PowerPoint: Wasserzeichen werden als Hintergrundbild auf den Folienmaster angewendet.

Verwenden Sie die folgenden Anweisungen, um visuelle Kennzeichnungen für eine Bezeichnung zu konfigurieren.

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.
 
2. Klicken Sie anschließend im Hubmenü auf **Durchsuchen**, und geben Sie **Information** im Filterfeld ein. Wählen Sie **Azure Information Protection** aus.

3. Wählen Sie auf dem Blatt **Azure Information Protection** die Bezeichnung, die Sie für visuelle Kennzeichnungen konfigurieren möchten.

4. Konfigurieren Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Set visual marking (such as header or footer)** (Visuelle Kennzeichnung [z. B. Kopf- oder Fußzeile] festlegen) die Einstellungen für die gewünschten visuellen Kennzeichnungen, und klicken Sie dann auf **Save** (Speichern):

    - So konfigurieren Sie eine Kopfzeile: Wählen Sie für **Documents with this label have a header** (Dokumente mit dieser Bezeichnung weisen eine Kopfzeile auf) die Option **On** (Ein), wenn eine Kopfzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Kopfzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die Farbe und die Ausrichtung der Kopfzeile an.

    - So konfigurieren Sie eine Fußzeile: Wählen Sie für **Documents with this label have a footer** (Dokumente mit dieser Bezeichnung weisen eine Fußzeile auf) die Option **On** (Ein), wenn eine Fußzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Fußzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die Farbe und die Ausrichtung der Fußzeile an.

    - So konfigurieren Sie ein Wasserzeichen: Wählen Sie für **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung weisen ein Wasserzeichen auf) die Option **On** (Ein), wenn ein Wasserzeichen enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über ein Wasserzeichen verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die Farbe und das Layout des Wasserzeichens an.

5. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organization-s-policy).  





<!--HONumber=Jul16_HO5-->


