---
title: Konfigurieren optischer Kennzeichnungen für eine Azure Information Protection-Bezeichnung – AIP
description: Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 05/27/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 5ff7dc706d272228892b238da99a008ed626e522
ms.sourcegitcommit: 16d2c7477b96c5e8f6e4328a61fe1dc3d12c878d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86927368"
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>[!NOTE]
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen.

Weitere Informationen zu diesen optische Kennzeichnungen finden Sie hier:

- Kopf- und Fußzeilen gelten für Word, Excel, PowerPoint und Outlook.

- Wasserzeichen gelten für Word, Excel und PowerPoint:

    - Excel: Wasserzeichen sind nur im Modus „Seitenlayout“ und „Seitenansicht“ sichtbar sowie beim Drucken.

    - PowerPoint: Wasserzeichen werden als Hintergrundbild auf den Folienmaster angewendet. Stellen Sie sicher, dass auf der Registerkarte **Ansicht** im **Folienmaster** die Option **Hintergrundbilder ausblenden** aktiviert ist.

- Mehrere Zeilen werden für Wasserzeichen und für Kopf- und Fußzeilen in Word, Excel und PowerPoint unterstützt. Wenn Sie mehrere Zeilen für die Kopf- oder Fußzeile einer Bezeichnung angeben, die in Outlook angewendet wird, werden die Zeilen verkettet. Ziehen Sie in diesem Szenario die Verwendung der Konfiguration zum [Festlegen verschiedener optischer Kennzeichnungen für Word, Excel, PowerPoint und Outlook](#setting-different-visual-markings-for-word-excel-powerpoint-and-outlook) in Betracht.

- Maximale Zeichenfolgenlänge:

    - Die maximale Zeichenfolgenlänge, die Sie für Kopf- und Fußzeile eingeben können, beträgt 1024 Zeichen. Excel hat ein Gesamtlimit von 255 Zeichen für Kopf- und Fußzeilen. Dieser Grenzwert schließt Zeichen ein, die nicht in Excel angezeigt werden, wie z.B. Formatierungscodes. Wenn dieses Limit erreicht wurde, wird die eingegebene Zeichenfolge in Excel nicht angezeigt.

    - Die maximale Zeichenfolgenlänge für Wasserzeichen beträgt 255 Zeichen.

- Sie können einfach eine Textzeichenfolge angeben oder [Variablen](#using-variables-in-the-text-string) verwenden, um die Textzeichenfolge dynamisch zu erstellen, wenn die Kopfzeile, die Fußzeile oder das Wasserzeichen angewendet wird.

- Optische Kennzeichnungen werden in Word, PowerPoint, Outlook und jetzt auch Excel in unterschiedlichen Farben unterstützt.

- Optische Kennzeichnungen unterstützen nur eine Sprache.

## <a name="when-visual-markings-are-applied"></a>Wann visuelle Kennzeichnungen angewendet werden

Bei E-Mail-Nachrichten werden die visuellen Kennzeichnungen beim Senden einer E-Mail von Outlook angewendet. Wenn beim Weiterleiten oder Antworten auf diese E-Mail eine Kennzeichnung geändert wird, werden die ursprünglichen visuellen Kennzeichnungen immer beibehalten.

Für Dokumente werden die visuellen Kennzeichnungen wie folgt angewendet:

- In einer Office-App werden die visuellen Kennzeichnungen aus einer Bezeichnung angewendet, wenn die Bezeichnung angewendet wird. Visuelle Kennzeichnungen werden ebenfalls angewendet, wenn ein bezeichnetes Dokument geöffnet und erstmals gespeichert wird.  

- Wenn ein Dokument über den Datei-Explorer, über PowerShell oder über die Azure Information Protection-Überprüfung bezeichnet wird, werden optische Kennzeichnungen nicht sofort übernommen. Sie werden vom Azure Information Protection-Client angewendet, wenn das Dokument in einer Office-App geöffnet und erstmals gespeichert wird.

    Eine Ausnahme stellt die Verwendung von [Autosave](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) mit Office-Apps für Dateien dar, die in Microsoft SharePoint, onedrive for Work oder School oder onedrive for Home gespeichert sind: Wenn die automatische Speicherung aktiviert ist, werden visuelle Kennzeichnungen nicht angewendet, es sei denn, Sie konfigurieren die [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) , um die Klassifizierung so zu aktivieren, dass Sie fortlaufend im Hintergrund ausgeführt wird.

## <a name="to-configure-visual-markings-for-a-label"></a>So konfigurieren Sie visuelle Kennzeichnungen für eine Bezeichnung

Verwenden Sie die folgenden Anweisungen, um visuelle Kennzeichnungen für eine Bezeichnung zu konfigurieren.

1. Wenn Sie dies nicht bereits getan haben, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal). Navigieren Sie anschließend zum Bereich **Azure Information Protection**.

    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die Bezeichnung aus, die die visuellen Markierungen enthält, die Sie hinzufügen oder ändern möchten.

3. Konfigurieren Sie im Bereich **Bezeichnung** im Bereich **visuelle Kennzeichnung festlegen (z. b. Kopf-oder Fußzeile)** die Einstellungen für die gewünschten visuellen Markierungen, und klicken Sie dann auf **Speichern**:

    - So konfigurieren Sie eine Kopfzeile: Wählen Sie für **Documents with this label have a header** (Dokumente mit dieser Bezeichnung weisen eine Kopfzeile auf) die Option **On** (Ein), wenn eine Kopfzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Kopfzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung der Kopfzeile an.

    - So konfigurieren Sie eine Fußzeile: Wählen Sie für **Documents with this label have a footer** (Dokumente mit dieser Bezeichnung weisen eine Fußzeile auf) die Option **On** (Ein), wenn eine Fußzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Fußzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung der Fußzeile an.

    - So konfigurieren Sie ein Wasserzeichen: Wählen Sie für **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung weisen ein Wasserzeichen auf) die Option **On** (Ein), wenn ein Wasserzeichen enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über ein Wasserzeichen verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung des Wasserzeichens an.

Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

## <a name="using-variables-in-the-text-string"></a>Verwenden von Variablen in der Textzeichenfolge

Sie können die folgenden Variablen in der Textzeichenfolge für die Kopfzeile, die Fußzeile oder das Wasserzeichen verwenden:

- `${Item.Label}` für die ausgewählte Bezeichnung. Beispiel: Allgemein

- `${Item.Name}` für den Dateinamen oder E-Mail-Betreff. Beispiel: JulySales.docx

- `${Item.Location}` für den Pfad und den Dateinamen bei Dokumenten und für den Betreff bei E-Mails. Beispiel: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` für den Besitzer des Dokuments oder der E-Mail, gemäß dem Namen des angemeldeten Windows-Benutzers. Beispiel: rsimone

- `${User.PrincipalName}` für den Besitzer des Dokuments oder der E-Mail, gemäß der E-Mail-Adresse des angemeldeten Azure Information Protection-Clients (UPN). Beispiel: rsimone@vanarsdelltd.com

- `${Event.DateTime}` für Datum und Uhrzeit, zu denen die ausgewählte Bezeichnung festgelegt wurde. Beispiel: 16.08.2016 13:30 Uhr

> [!NOTE]
>Bei dieser Syntax wird die Groß-/Kleinschreibung beachtet. Wenn Sie z. b. die Zeichenfolge `Document: ${Item.Name}  Classification: ${Item.Label}` für die Fußzeile der **allgemeinen** Bezeichnung angeben, wird der FooterText, der auf ein Dokument mit dem Namen project.docx angewendet wird, **Dokument: project.docx Classification: General**.

<!-- REMOVED w JUNE 2020 RELEASE> [!NOTE]
> Use of either the `${User.Name}` and/or `${User.PrincipalName}` variable are currently not supported by the Azure Information Protection unified labeling client. 
-->
>[!TIP]
> Sie können auch einen [Feldcode verwenden, um den](faqs-infoprotect.md#can-i-create-a-document-template-that-automatically-includes-the-classification) Bezeichnungs Namen in ein Dokument oder eine Vorlage einzufügen.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Festlegen verschiedener optischer Kennzeichnungen für Word, Excel, PowerPoint und Outlook

Die von Ihnen angegebenen optischen Kennzeichnungen werden standardmäßig auf Word, Excel, PowerPoint und Outlook angewendet. Sie können optische Kennzeichnungen jedoch pro Office-Anwendungstyp festlegen, wenn Sie die Variablenanweisung „If.App“ in der Textzeichenfolge verwenden und den Anwendungstyp mithilfe der Werte **Word**, **Excel**, **PowerPoint** bzw. **Outlook** angeben. Sie können diese Werte auch abkürzen. Das ist notwendig, wenn Sie mehrere Werte in der gleichen If.App-Anweisung angeben möchten.

Verwenden Sie die folgende Syntax:

```ps
${If.App.<application type>}<your visual markings text> ${If.End}
```

> [!NOTE]
>Bei der Syntax in dieser Anweisung muss die Groß-/Kleinschreibung beachtet werden.

Beispiele:

- **Legen Sie Headertext nur für Word-Dokumente fest:**

    `${If.App.Word}This Word document is sensitive ${If.End}`

    Die Bezeichnung legt nur in Headern von Word-Dokumenten den Headertext „This Word document is sensitive“ fest. Für andere Office-Anwendungen wird kein Headertext angewendet.

- **Legen Sie einen Fußzeilentext für Word, Excel und Outlook und einen anderen Fußzeilentext für PowerPoint fest:**

    `${If.App.WXO}This content is confidential. ${If.End}${If.App.PowerPoint}This presentation is confidential. ${If.End}`

    In Word, Excel und Outlook wendet die Bezeichnung den Fußzeilentext „This content is confidential“ an. In PowerPoint wendet die Bezeichnung den Fußzeilentext „This presentation is confidential“ an.

- **Legen Sie spezifischen Wasserzeichentext für Word und PowerPoint und Wasserzeichentext für Word, Excel und PowerPoint fest:**

    `${If.App.WP}This content is ${If.End}Confidential`

    In Word und PowerPoint wendet die Bezeichnung den Wasserzeichentext „This content is Confidential“ an. In Excel wird der Wasserzeichentext „Confidential“ angewendet. In Outlook wird kein Wasserzeichentext angewendet, da Wasserzeichen als optische Kennzeichnungen in Outlook nicht unterstützt werden.

> [!NOTE]
> Wenn Sie den Azure Information Protection Unified Bezeichnung-Client verwenden, ist das Festlegen von Werten für den **Schriftart Namen** nur über das Azure Information Protection-Portal möglich. Wenn Sie Werte für die **Schriftfarbe** über einen der fünf Standardwerte hinaus festlegen, ist auch nur über das Azure Information Protection-Portal möglich.

### <a name="setting-the-font-name"></a>Festlegen des Schriftartnamens

Calibri ist die Standardschriftart für den Text in Kopfzeilen, Fußzeilen und Wasserzeichen. Wenn Sie einen alternativen Schriftartnamen angeben, stellen Sie sicher, dass diese Schriftart auf den Clientgeräten verfügbar ist, die die optischen Kennzeichnungen anwenden.
Wenn die angegebene Schriftart nicht verfügbar ist, verwendet der Client die Schriftart Calibri.

### <a name="setting-the-font-color"></a>Festlegen der Schriftartfarbe

Sie können aus der Liste der Farben auswählen oder eine benutzerdefinierte Farbe eingeben, indem Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe eingeben. Beispielsweise ist **#40e0d0** der RGB-Hexadezimalwert für türkis.

Wenn Sie einen Verweis auf diese Codes benötigen, finden Sie eine hilfreiche Tabelle auf der [\<color>](https://developer.mozilla.org/docs/Web/CSS/color_value) Seite der MSDN-Webdokumentation. Außerdem finden Sie diese Codes in vielen Anwendungen, mit denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  
