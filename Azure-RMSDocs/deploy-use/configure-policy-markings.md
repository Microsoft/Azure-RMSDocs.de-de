---
title: "Konfigurieren optischer Kennzeichnungen für eine Azure Information Protection-Bezeichnung"
description: "Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/17/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: ff444afb1912239ec817882c76fc735f6d35ed1e
ms.sourcegitcommit: 965108d50739148864b2ae7dcc661ae65f1b154c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/17/2017
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection

>*Gilt für: Azure Information Protection*

Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen.

Weitere Informationen zu diesen visuellen Kennzeichnungen finden Sie hier:

- Kopf- und Fußzeilen gelten für Word, Excel, PowerPoint und Outlook.

- Wasserzeichen gelten für Word, Excel und PowerPoint:

    - Excel: Wasserzeichen sind nur im Modus „Seitenlayout“ und „Seitenansicht“ sichtbar sowie beim Drucken.
    
    - PowerPoint: Wasserzeichen werden als Hintergrundbild auf den Folienmaster angewendet.
    
    - Es werden mehrere Zeilen Text unterstützt.

- Sie können einfach eine Textzeichenfolge angeben oder [Variablen](#using-variables-in-the-text-string) verwenden, um die Textzeichenfolge dynamisch zu erstellen, wenn die Kopfzeile, die Fußzeile oder das Wasserzeichen angewendet wird.

- Visuelle Kennzeichnungen unterstützen nur eine Sprache.

## <a name="when-visual-markings-are-applied"></a>Wann visuelle Kennzeichnungen angewendet werden

Bei E-Mail-Nachrichten werden die visuellen Kennzeichnungen beim Senden der E-Mail von Outlook angewendet.

Für Dokumente werden die visuellen Kennzeichnungen wie folgt angewendet:

- In einer Office-App werden die visuellen Kennzeichnungen aus einer Bezeichnung angewendet, wenn die Bezeichnung angewendet wird. Visuelle Kennzeichnungen werden ebenfalls angewendet, wenn ein bezeichnetes Dokument geöffnet und erstmals gespeichert wird.  

- Wenn ein Dokument über den Datei-Explorer oder über PowerShell bezeichnet wird, werden visuelle Kennzeichnungen nicht sofort übernommen. Sie werden angewendet, wenn das Dokument in einer Office-App geöffnet und erstmals gespeichert wird.

## <a name="to-configure-visual-markings-for-a-label"></a>So konfigurieren Sie visuelle Kennzeichnungen für eine Bezeichnung

Verwenden Sie die folgenden Anweisungen, um visuelle Kennzeichnungen für eine Bezeichnung zu konfigurieren.

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gilt, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
    Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Konfigurieren Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Set visual marking (such as header or footer)** (Visuelle Kennzeichnung [z. B. Kopf- oder Fußzeile] festlegen) die Einstellungen für die gewünschten visuellen Kennzeichnungen, und klicken Sie dann auf **Save** (Speichern):
    
    - So konfigurieren Sie eine Kopfzeile: Wählen Sie für **Documents with this label have a header** (Dokumente mit dieser Bezeichnung weisen eine Kopfzeile auf) die Option **On** (Ein), wenn eine Kopfzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Kopfzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung der Kopfzeile an.
    
    - So konfigurieren Sie eine Fußzeile: Wählen Sie für **Documents with this label have a footer** (Dokumente mit dieser Bezeichnung weisen eine Fußzeile auf) die Option **On** (Ein), wenn eine Fußzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Fußzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung der Fußzeile an.
    
    - So konfigurieren Sie ein Wasserzeichen: Wählen Sie für **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung weisen ein Wasserzeichen auf) die Option **On** (Ein), wenn ein Wasserzeichen enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über ein Wasserzeichen verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung des Wasserzeichens an.

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

### <a name="setting-the-font-name"></a>Festlegen des Schriftartnamens

Diese Einstellung ist derzeit als Vorschau verfügbar.

Calibri ist die Standardschriftart für den Text in Kopfzeilen, Fußzeilen und Wasserzeichen. Wenn Sie einen alternativen Schriftartnamen angeben, stellen Sie sicher, dass diese Schriftart auf den Client-Geräten verfügbar ist, die die visuellen Kennzeichnungen anwenden. Andernfalls ist die Schriftart, die verwendet wird, nicht deterministisch. 

Wenn Sie über die Vorschauversion des Azure Information Protection-Clients verfügen, und die angegebene Schriftart nicht verfügbar ist, greift der Client auf die Schriftart Calibri zurück.

### <a name="setting-the-font-color"></a>Festlegen der Schriftartfarbe

Sie können aus der Liste der Farben auswählen oder eine benutzerdefinierte Farbe eingeben, indem Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe eingeben. Beispiel: **#DAA520**. 

Wenn Sie einen Verweis für diese Codes benötigen, ist „[Colors by Name](https://msdn.microsoft.com/library/aa358802\(v=vs.85).aspx“ aus der MSDN-Dokumentation ein hilfreicher Ausgangspunkt. Sie finden diese Codes auch in vielen Anwendungen, in denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
