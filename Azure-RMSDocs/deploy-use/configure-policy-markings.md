---
title: Konfigurieren optischer Kennzeichnungen für eine Azure Information Protection-Bezeichnung
description: Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/10/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df2676eeb062-f25a-4cf8-a782-e59664427d54
ms.openlocfilehash: c41dcb0a11e61be4a2dfd974d9bf6803a992b858
ms.sourcegitcommit: ef3d187da900107095d499de7e7dac5c947e4b13
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2018
ms.locfileid: "37947453"
---
# <a name="how-to-configure-a-label-for-visual-markings-for-azure-information-protection"></a>Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Wenn Sie einem Dokument oder einer E-Mail-Nachricht eine Bezeichnung zuweisen, können Sie verschiedene Optionen auswählen, damit die gewählte Klassifizierung gut sichtbar ist. Bei diesen visuellen Kennzeichnungen handelt es sich um eine Kopfzeile, eine Fußzeile und ein Wasserzeichen.

Weitere Informationen zu diesen optische Kennzeichnungen finden Sie hier:

- Kopf- und Fußzeilen gelten für Word, Excel, PowerPoint und Outlook.

- Wasserzeichen gelten für Word, Excel und PowerPoint:

    - Excel: Wasserzeichen sind nur im Modus „Seitenlayout“ und „Seitenansicht“ sichtbar sowie beim Drucken.
    
    - PowerPoint: Wasserzeichen werden als Hintergrundbild auf den Folienmaster angewendet. Stellen Sie sicher, dass auf der Registerkarte **Ansicht** im **Folienmaster** die Option **Hintergrundbilder ausblenden** aktiviert ist.
    
    - Es werden mehrere Zeilen Text unterstützt.

- Sie können einfach eine Textzeichenfolge angeben oder [Variablen](#using-variables-in-the-text-string) verwenden, um die Textzeichenfolge dynamisch zu erstellen, wenn die Kopfzeile, die Fußzeile oder das Wasserzeichen angewendet wird.

- Optische Kennzeichnungen werden in Word, PowerPoint und Outlook in unterschiedlichen Farben unterstützt. Optische Kennzeichnungen, die für Farben konfiguriert sind, werden in Excel stets in Schwarz angezeigt.

- Optische Kennzeichnungen unterstützen nur eine Sprache.

## <a name="when-visual-markings-are-applied"></a>Wann visuelle Kennzeichnungen angewendet werden

Bei E-Mail-Nachrichten werden die visuellen Kennzeichnungen beim Senden der E-Mail von Outlook angewendet.

Für Dokumente werden die visuellen Kennzeichnungen wie folgt angewendet:

- In einer Office-App werden die visuellen Kennzeichnungen aus einer Bezeichnung angewendet, wenn die Bezeichnung angewendet wird. Visuelle Kennzeichnungen werden ebenfalls angewendet, wenn ein bezeichnetes Dokument geöffnet und erstmals gespeichert wird.  

- Wenn ein Dokument über den Datei-Explorer, über PowerShell oder über die Azure Information Protection-Überprüfung bezeichnet wird, werden optische Kennzeichnungen nicht sofort übernommen. Sie werden vom Azure Information Protection-Client angewendet, wenn das Dokument in einer Office-App geöffnet und erstmals gespeichert wird.
    
    Eine Ausnahme gilt, wenn Sie [AutoSpeichern](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) in Office 2016 für Dateien verwenden, die in SharePoint Online, OneDrive oder OneDrive for Business gespeichert sind: Wenn „AutoSpeichern“ aktiviert ist, werden optische Kennzeichnungen nur dann angewendet, wenn Sie die [erweiterte Clienteinstellung](../rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) so konfigurieren, dass die Klassifizierung kontinuierlich im Hintergrund ausgeführt wird. 

## <a name="to-configure-visual-markings-for-a-label"></a>So konfigurieren Sie visuelle Kennzeichnungen für eine Bezeichnung

Verwenden Sie die folgenden Anweisungen, um visuelle Kennzeichnungen für eine Bezeichnung zu konfigurieren.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Navigieren Sie über die Menüoption **KLASSIFIZIERUNGEN** > **Bezeichnungen** zum Blatt **Azure Information Protection - Labels** (Azure Information Protection: Bezeichnungen), und wählen Sie dort die Bezeichnung mit den optischen Kennzeichnungen aus, die Sie ändern möchten.

3. Konfigurieren Sie auf dem Blatt **Bezeichnung** im Abschnitt **Optische Kennzeichnung festlegen (z. B. Kopf- oder Fußzeile)** die Einstellungen für die gewünschten optischen Kennzeichnungen, und klicken Sie dann auf **Speichern**:
    
    - So konfigurieren Sie eine Kopfzeile: Wählen Sie für **Documents with this label have a header** (Dokumente mit dieser Bezeichnung weisen eine Kopfzeile auf) die Option **On** (Ein), wenn eine Kopfzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Kopfzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung der Kopfzeile an.
    
    - So konfigurieren Sie eine Fußzeile: Wählen Sie für **Documents with this label have a footer** (Dokumente mit dieser Bezeichnung weisen eine Fußzeile auf) die Option **On** (Ein), wenn eine Fußzeile enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über eine Fußzeile verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung der Fußzeile an.
    
    - So konfigurieren Sie ein Wasserzeichen: Wählen Sie für **Documents with this label have a watermark** (Dokumente mit dieser Bezeichnung weisen ein Wasserzeichen auf) die Option **On** (Ein), wenn ein Wasserzeichen enthalten sein soll, und **Off** (Aus), wenn die Dokumente nicht über ein Wasserzeichen verfügen sollen. Geben Sie bei Auswahl von **On** (Ein) den Text, die Größe, die [Schriftart](#setting-the-font-name), die [Farbe](#setting-the-font-color) und die Ausrichtung des Wasserzeichens an.
    
Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.


## <a name="using-variables-in-the-text-string"></a>Verwenden von Variablen in der Textzeichenfolge

Sie können die folgenden Variablen in der Textzeichenfolge für die Kopfzeile, die Fußzeile oder das Wasserzeichen verwenden:

- `${Item.Label}` für die ausgewählte Bezeichnung. Beispiel: intern

- `${Item.Name}` für den Dateinamen oder E-Mail-Betreff. Beispiel: JulySales.docx

- `${Item.Location}` für den Pfad und den Dateinamen bei Dokumenten und für den Betreff bei E-Mails. Beispiel: \\\Sales\2016\Q3\JulyReport.docx

- `${User.Name}` für den Besitzer des Dokuments oder der E-Mail, gemäß dem Namen des angemeldeten Windows-Benutzers. Beispiel: rsimone

- `${User.PrincipalName}` für den Besitzer des Dokuments oder der E-Mail, gemäß der E-Mail-Adresse des angemeldeten Azure Information Protection-Clients (UPN). Beispiel: rsimone@vanarsdelltd.com

- `${Event.DateTime}` für Datum und Uhrzeit, zu denen die ausgewählte Bezeichnung festgelegt wurde. Beispiel: 16.08.2016 13:30 Uhr

Beispiel: Wenn Sie die Zeichenfolge `Document: ${item.name}  Classification: ${item.label}` für die Fußzeile der Bezeichnung **General** (Allgemein) angeben, so lautet der Text in der Fußzeile, der auf ein Dokument namens „project.docx“ angewendet wird, **Dokument: project.docx Klassifizierung: Allgemein**.

## <a name="setting-different-visual-markings-for-word-excel-powerpoint-and-outlook"></a>Festlegen verschiedener optischer Kennzeichnungen für Word, Excel, PowerPoint und Outlook

Die von Ihnen angegebenen optischen Kennzeichnungen werden standardmäßig auf Word, Excel, PowerPoint und Outlook angewendet. Sie können optische Kennzeichnungen jedoch pro Office-Anwendungstyp festlegen, wenn Sie die Variablenanweisung „If.App“ in der Textzeichenfolge verwenden und den Anwendungstyp mithilfe der Werte **Word**, **Excel**, **PowerPoint** bzw. **Outlook** angeben. Sie können diese Werte auch abkürzen. Dies ist erforderlich, wenn Sie mehrere Werte in derselben If.App-Anweisung angeben möchten.

Verwenden Sie die folgende Syntax:

    ${If.App.<application type>}<your visual markings text> ${If.End}

Bei der Syntax in dieser Anweisung muss die Groß-/Kleinschreibung beachtet werden.

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

### <a name="setting-the-font-name"></a>Festlegen des Schriftartnamens

Calibri ist die Standardschriftart für den Text in Kopfzeilen, Fußzeilen und Wasserzeichen. Wenn Sie einen alternativen Schriftartnamen angeben, stellen Sie sicher, dass diese Schriftart auf den Clientgeräten verfügbar ist, die die optischen Kennzeichnungen anwenden. 

Wenn die angegebene Schriftart nicht verfügbar ist, verwendet der Client die Schriftart Calibri.

### <a name="setting-the-font-color"></a>Festlegen der Schriftartfarbe

Sie können aus der Liste der Farben auswählen oder eine benutzerdefinierte Farbe eingeben, indem Sie ein hexadezimales Tripel für die Komponenten Rot, Grün und Blau (RGB) der Farbe eingeben. Beispiel: **#DAA520**. 

Wenn Sie einen Verweis für diese Codes benötigen, ist der Artikel zu [Farben nach Namen](https://msdn.microsoft.com/library/aa358802\(v=vs.85\).aspx) aus der MSDN-Dokumentation ein hilfreicher Ausgangspunkt. Sie finden diese Codes auch in vielen Anwendungen, in denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
