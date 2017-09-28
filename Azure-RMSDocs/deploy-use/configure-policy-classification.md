---
title: "Konfigurieren von Bedingungen für eine Azure Information Protection-Bezeichnung"
description: "Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: aa41d4f34f0ed43682f9ba426ec18204457980c3
ms.sourcegitcommit: 2f1936753adf8d2fbea780d0a3878afa621daab5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen: 

- Die automatische Klassifizierung gilt beim Speichern von Dateien in Word, Excel und PowerPoint sowie beim Senden von E-Mails in Outlook. Sie können die automatische Klassifizierung nicht für Dateien verwenden, für die zuvor bereits manuell eine Bezeichnung festgelegt wurde.
 
- Die empfohlene Klassifizierung gilt beim Speichern von Dateien in Word, Excel und PowerPoint.

Beim Konfigurieren von Bedingungen können Sie vordefinierte Muster verwenden, z.B. für **Kreditkartennummern** oder **US-Sozialversicherungsnummern (SSN)**. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren. Diese Bedingungen gelten für den Haupttext in Dokumenten und E-Mails sowie für Kopf- und Fußzeilen. Weitere Informationen zu den Bedingungen finden Sie im Schritt 5 der [folgenden Vorgehensweise](#to-configure-recommended-or-automatic-classification-for-a-label).

So werden mehrere Bedingungen ausgewertet, wenn sie für mehrere Bezeichnungen gelten:

1. Die Bezeichnungen werden zur Auswertung basierend auf der jeweiligen Position sortiert, die Sie in der Richtlinie angeben: Die an erster Stelle positionierte Bezeichnung steht an unterster Stelle (geringste Vertraulichkeitsstufe), die an letzter Stelle positionierte Bezeichnung steht an höchster Stelle (höchste Vertraulichkeitsstufe).

2. Die Bezeichnung mit der höchsten Vertraulichkeitsstufe wird angewendet.
 
3. Die letzte untergeordnete Bezeichnung wird angewendet.

> [!TIP]
>Um eine bestmögliche Benutzererfahrung und Geschäftskontinuität zu gewährleisten, wird empfohlen, zunächst nicht die automatische Klassifizierung, sondern die empfohlene Klassifizierung zu verwenden. Bei dieser Konfiguration haben Ihre Benutzer die Möglichkeit, die Bezeichnungs- oder Schutzaktion zu akzeptieren bzw. diese Empfehlungen zu überschreiben, wenn sie nicht für das jeweilige Dokument oder die jeweilige E-Mail-Nachricht geeignet sind.

Nachfolgend sehen Sie eine Beispielaufforderung bei Konfiguration einer Bedingung, um eine Bezeichnung als empfohlene Aktion anzuwenden (einschließlich eines benutzerdefinierten Richtlinientipps):

![Azure Information Protection – Erkennung und Empfehlung](../media/info-protect-recommend-calloutsv2.png)

In diesem Beispiel kann der Benutzer auf **Jetzt ändern** klicken, um die empfohlene Bezeichnung anzuwenden, oder die Empfehlung ignorieren, indem er **Schließen** wählt.

## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Konfigurieren der empfohlenen oder der automatischen Klassifizierung für eine Bezeichnung

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gilt, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien).
    
    Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Wählen Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien) oder auf dem Blatt **Richtlinie\<name>** die zu konfigurierende Bezeichnung. 

4. Klicken Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Configure conditions for automatically applying this label** (Bedingungen konfigurieren, um diese Bezeichnung automatisch anzuwenden) auf **Add a new condition** (Neue Bedingung hinzufügen).

5. Wählen Sie auf dem Blatt **Bedingung** die Option **Informationstypen** aus, wenn Sie eine vordefinierte Bedingung verwenden möchten, oder **Benutzerdefiniert**, um eine eigene Bedingung anzugeben:
    - Für **Informationstypen**: Wählen Sie eine der verfügbaren Bedingungen aus der Liste aus, und legen Sie dann die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Die Informationstypen verwenden die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP). Sie können aus vielen häufig verwendeten vertraulichen Informationstypen wählen. Einige davon sind spezifisch für verschiedene Regionen. Weitere Informationen finden Sie in der Office-Dokumentation unter [What the sensitive information types look for (Wonach die vertraulichen Informationstypen suchen)](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b). 
        
        Die Liste der Informationstypen, die Sie im Azure-Portal auswählen können, wird regelmäßig mit allen neuen Office-DLP-Ergänzungen aktualisiert. Die Liste schließt jedoch benutzerdefinierte Typen vertraulicher Informationen aus, die Sie als Regelpaket definiert und in das Office 365 Security & Compliance Center hochgeladen haben. 
        
        Wenn Azure Information Protection die von Ihnen ausgewählten Informationstypen auswertet, verwendet es nicht die Office-DLP-Einstellung auf Konfidenzniveau, sondern sucht entsprechend der niedrigsten Konfidenz nach Übereinstimmungen.
    
    - Für **Custom** (Benutzerdefiniert): Geben Sie einen Namen und eine Zeichenfolge für den Abgleich an. Diese darf weder Anführungszeichen noch Sonderzeichen enthalten. Legen Sie dann fest, ob für den Abgleich ein regulärer Ausdruck verwendet und ob die Groß-/Kleinschreibung beachtet werden soll. Legen Sie außerdem die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Die regulären Ausdrücke verwenden die RegEx-Muster von Office 365. Weitere Informationen finden Sie in der Office-Dokumentation unter [Defining regular expression based matches](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) (Definieren von Matches, die auf regulären Ausdrücken basieren).
        
6. Entscheiden Sie, ob Sie die Werte unter **Mindestanzahl an Vorkommen** und **Count occurrence with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) ändern müssen, und klicken Sie dann auf **Speichern**. 
    
    Beispiel für die Optionen zu Vorkommen: Sie wählen den Informationstyp für die US-Sozialversicherungsnummer aus und legen für die Mindestanzahl von Vorkommen den Wert „2“ fest. Sie verfügen über ein Dokument, in dem dieselbe Sozialversicherungsnummer zweimal aufgeführt wird: Wenn Sie für **Count occurrences with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) die Einstellung **Ein** wählen, wird die Bedingung nicht erfüllt. Wenn Sie diese Option auf **Aus** festlegen, wird die Bedingung erfüllt.

7. Konfigurieren Sie auf dem Blatt **Bezeichnung** die folgenden Einstellungen, und klicken Sie dann auf **Speichern**:
    
    - Wählen Sie die automatische oder die empfohlene Klassifizierung: Wählen Sie für **Select how this label is applied: automatically or recommended to user** (Festlegen, wie diese Bezeichnung angewendet wird: automatisch oder empfohlen) die Einstellung **Automatic** (Automatisch) oder **Recommended** (Empfohlen).
    
    - Geben Sie den Text für die Benutzeraufforderung oder den Richtlinientipp an: Übernehmen Sie den Standardtext, oder geben Sie eine eigene Zeichenfolge ein.

8. Klicken Sie auf dem anfänglichen Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


