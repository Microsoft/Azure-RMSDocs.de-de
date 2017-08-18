---
title: "Konfigurieren optischer Kennzeichnungen für eine Azure Information Protection-Bezeichnung"
description: "Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/16/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: a65299651abd97adb0fc7641be2f2f3c6f1d8d2f
ms.sourcegitcommit: adb38b008656ac706920a8488fd2beafedadbc97
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2017
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection

>*Gilt für: Azure Information Protection*

Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen.

Weitere Informationen zu diesen visuellen Kennzeichnungen finden Sie hier:

- Kopf- und Fußzeilen gelten für Word, Excel, PowerPoint und Outlook.

- Wasserzeichen gelten für Word, Excel und PowerPoint:

    - Excel: Wasserzeichen sind nur im Modus „Seitenlayout“ und „Seitenansicht“ sichtbar sowie beim Drucken.
    
    - PowerPoint: Wasserzeichen werden als Hintergrundbild auf den Folienmaster angewendet.
    
    - Mehrere Textzeilen werden unterstützt, wenn Sie die aktuelle Vorschauversion des Azure Information Protection-Clients verwenden.

- Sie können einfach eine Textzeichenfolge angeben oder [Variablen](#using-variables-in-the-text-string) verwenden, um die Textzeichenfolge dynamisch zu erstellen, wenn die Kopfzeile, die Fußzeile oder das Wasserzeichen angewendet wird.

## <a name="when-visual-markings-are-applied"></a>Wann visuelle Kennzeichnungen angewendet werden

Bei E-Mail-Nachrichten werden die visuellen Kennzeichnungen beim Senden der E-Mail von Outlook angewendet.

Für Dokumente werden die visuellen Kennzeichnungen wie folgt angewendet:

- **Für die allgemein verfügbare Version** des Azure Information Protection-Clients: 
    
    - In einer Office-App werden die visuellen Kennzeichnungen aus einer Bezeichnung angewendet, wenn die Bezeichnung angewendet und wenn das Dokument gespeichert wird. 
    
    - Wenn ein Dokument über den Datei-Explorer oder über PowerShell bezeichnet wird, werden visuelle Kennzeichnungen nicht sofort übernommen. Sie werden angewendet, wenn das Dokument in einer Office-App geöffnet wird und wenn es gespeichert wird.

- **Für die aktuelle Vorschauversion** des Azure Information Protection-Clients: 
    
    - In einer Office-App werden die visuellen Kennzeichnungen aus einer Bezeichnung angewendet, wenn die Bezeichnung angewendet wird. Visuelle Kennzeichnungen werden ebenfalls angewendet, wenn ein bezeichnetes Dokument geöffnet und erstmals gespeichert wird.  
    
    - Wenn ein Dokument über den Datei-Explorer oder über PowerShell bezeichnet wird, werden visuelle Kennzeichnungen nicht sofort übernommen. Sie werden angewendet, wenn das Dokument in einer Office-App geöffnet und erstmals gespeichert wird.

## <a name="to-configure-visual-markings-for-a-label"></a>So konfigurieren Sie visuelle Kennzeichnungen für eine Bezeichnung

Verwenden Sie die folgenden Anweisungen, um visuelle Kennzeichnungen für eine Bezeichnung zu konfigurieren.

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**.

    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die für visuelle Markierungen zu konfigurierende Bezeichnung für alle Benutzer gilt, wählen Sie die zu ändernde Bezeichnung auf dem Blatt **Policy: Global** (Richtlinie: Global) aus.

     Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie zunächst die bereichsbezogene Richtlinie auf dem ersten Blatt **Azure Information Protection** aus.

3. Konfigurieren Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Set visual marking (such as header or footer)** (Visuelle Kennzeichnung [z. B. Kopf- oder Fußzeile] festlegen) die Einstellungen für die gewünschten visuellen Kennzeichnungen, und klicken Sie dann auf **Save** (Speichern):

    - So konfigurieren Sie eine Kopfzeile: Wählen Sie für **Documents with this label have a header** (Dokumente mit dieser Bezeichnung weisen eine Kopfzeile auf) die Option **On** (Ein), wenn eine Kopfzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Kopfzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die Farbe und die Ausrichtung der Kopfzeile an.

    - So konfigurieren Sie eine Fußzeile: Wählen Sie für **Documents with this label have a footer** (Dokumente mit dieser Bezeichnung weisen eine Fußzeile auf) die Option **On** (Ein), wenn eine Fußzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Fußzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die Farbe und die Ausrichtung der Fußzeile an.

    - So konfigurieren Sie ein Wasserzeichen: Wählen Sie für **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung weisen ein Wasserzeichen auf) die Option **On** (Ein), wenn ein Wasserzeichen enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über ein Wasserzeichen verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die Farbe und das Layout des Wasserzeichens an.

4. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="using-variables-in-the-text-string"></a>Verwenden von Variablen in der Textzeichenfolge

Sie können die folgenden Variablen in der Textzeichenfolge für die Kopfzeile, die Fußzeile oder das Wasserzeichen verwenden:

- `${Item.Label}` für die ausgewählte Bezeichnung. Beispiel: intern

- `${Item.Name}` für den Dateinamen oder E-Mail-Betreff. Beispiel: JulySales.docx

- `${Item.Location}` für den Pfad und den Dateinamen bei Dokumenten und für den Betreff bei E-Mails. Beispiel: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` für den Besitzer des Dokuments oder der E-Mail, gemäß dem Namen des angemeldeten Windows-Benutzers. Beispiel: rsimone

- `${User.PrincipalName}` für den Besitzer des Dokuments oder der E-Mail, gemäß der E-Mail-Adresse des angemeldeten Azure Information Protection-Clients (UPN). Beispiel: rsimone@vanarsdelltd.com

- `${Event.DateTime}` für Datum und Uhrzeit, zu denen die ausgewählte Bezeichnung festgelegt wurde. Beispiel: 16.08.2016 13:30 Uhr

Beispiel: Wenn Sie die Zeichenfolge `Document: ${item.name}  Classification: ${item.label}` für die Fußzeile der Bezeichnung **General** (Allgemein) angeben, so lautet der Text in der Fußzeile, der auf ein Dokument namens „project.docx“ angewendet wird, **Dokument: project.docx Klassifizierung: Allgemein**.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
