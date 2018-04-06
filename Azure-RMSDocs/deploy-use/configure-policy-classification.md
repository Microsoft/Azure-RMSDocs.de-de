---
title: Konfigurieren von Bedingungen für eine Azure Information Protection-Bezeichnung
description: Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/20/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 80537b32bee11df72673b869932f2d59cef11469
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen. 

Beim Konfigurieren dieser Bedingungen können Sie vordefinierte Muster verwenden, z.B. für **Kreditkartennummern** oder **US-Sozialversicherungsnummern (SSN)**. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren. Diese Bedingungen gelten für den Haupttext in Dokumenten und E-Mails sowie für Kopf- und Fußzeilen. Weitere Informationen zu den Bedingungen finden Sie im Schritt 5 der [folgenden Vorgehensweise](#to-configure-recommended-or-automatic-classification-for-a-label).

Um eine bestmögliche Benutzererfahrung und Geschäftskontinuität zu gewährleisten, wird empfohlen, zunächst nicht die automatische Klassifizierung, sondern die empfohlene Klassifizierung zu verwenden. Bei dieser Konfiguration haben Ihre Benutzer die Möglichkeit, die Klassifizierung und zugeordnete Schutzaktionen zu akzeptieren bzw. diese Empfehlungen zu überschreiben, wenn sie nicht für das jeweilige Dokument oder die jeweilige E-Mail-Nachricht geeignet sind.

Nachfolgend sehen Sie eine Beispielaufforderung bei Konfiguration einer Bedingung, um eine Bezeichnung als empfohlene Aktion anzuwenden (einschließlich eines benutzerdefinierten Richtlinientipps):

![Azure Information Protection – Erkennung und Empfehlung](../media/info-protect-recommend-calloutsv2.png)

In diesem Beispiel kann der Benutzer auf **Jetzt ändern** klicken, um die empfohlene Bezeichnung anzuwenden, oder die Empfehlung ignorieren, indem er **Schließen** wählt.

> [!IMPORTANT]
>Konfigurieren Sie Bezeichnungen nicht für die automatische Klassifizierung und eine benutzerdefinierte Berechtigung. Die Option für benutzerdefinierte Berechtigungen ist eine [Schutzeinstellung](configure-policy-protection.md), über die Benutzer angeben können, wem welche Berechtigungen erteilt werden sollen.
>
>Wenn eine Bezeichnung für die automatische Klassifizierung und benutzerdefinierte Berechtigungen konfiguriert ist, wird der Inhalt für die Bedingungen geprüft, und die benutzerdefinierte Berechtigung wird nicht angewendet. Sie können empfohlene Klassifizierungen und benutzerdefinierte Berechtigungen verwenden.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Anwendung von automatischen oder empfohlenen Bezeichnungen

**Für die allgemein verfügbare Version des Azure Information Protection-Clients:**

- Die automatische Klassifizierung gilt beim Speichern von Dokumenten in Word, Excel und PowerPoint sowie beim Senden von E-Mails in Outlook. 
    
    Sie können die automatische Klassifizierung nicht für Dokumente und E-Mails verwenden, die zuvor bereits manuell oder automatisch mit einer höheren Klassifizierung benannt wurden. 

- Die empfohlene Klassifizierung gilt beim Speichern von Dokumenten in Word, Excel und PowerPoint. Sie können für Outlook keine empfohlene Klassifizierung verwenden.
    
    Sie können für Dokumente, die vorher bereits benannt wurden, die empfohlene Klassifizierung mit einer oder ohne eine höhere Klassifizierung verwenden. 


**Für die aktuelle Vorschauversion des Azure Information Protection-Clients:**

- Die automatische Klassifizierung ist für Word, Excel, PowerPoint und Outlook geeignet. Die automatische Klassifizierung wird für Dokumente [ständig im Hintergrund](#more-information-about-running-continuously) ausgeführt. Die automatische Klassifizierung in Outlook wird beim Senden von E-Mails ausgeführt. 
    
    Sie können die automatische Klassifizierung nicht für Dokumente verwenden, die zuvor bereits manuell oder automatisch mit einer höheren Klassifizierung benannt wurden. Eine Ausnahme gilt nur, wenn Sie den Parameter OverrideLabel für die Azure Information Protection-Überprüfung aktivieren.

- Die empfohlene Klassifizierung wird in Word, Excel und PowerPoint angewendet. Die empfohlene Klassifizierung wird für diese Dokumente [ständig im Hintergrund](#more-information-about-running-continuously) ausgeführt. Sie können für Outlook keine empfohlene Klassifizierung verwenden.
    
    Sie können für Dokumente, die vorher bereits benannt wurden, die empfohlene Klassifizierung mit einer oder ohne eine höhere Klassifizierung verwenden. 

#### <a name="more-information-about-running-continuously"></a>Weitere Informationen zum dauerhaften Ausführen

Die aktuelle Vorschauversion des Azure Information Protection-Clients überprüft regelmäßig Dokumente auf die von Ihnen angegebenen Bedingungsregeln. Dieses Verhalten aktiviert die automatische und empfohlene Klassifizierung und den Schutz für Dokumente, die in SharePoint Online gespeichert sind. Große Dateien werden schneller gespeichert, da die Bedingungsregeln bereits ausgeführt wurden. 

Diese Bedingungsregeln werden nicht in Echtzeit, während der Benutzer tippt, ausgeführt. Stattdessen werden sie regelmäßig als Hintergrundaufgabe ausgeführt, wenn das Dokument geändert wird. 

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>So werden mehrere Bedingungen ausgewertet, wenn sie für mehrere Bezeichnungen gelten

Für die allgemein verfügbare Version des Azure Information Protection-Clients und die aktuelle Vorschauversion des Clients:

1. Die Bezeichnungen werden zur Auswertung basierend auf der jeweiligen Position sortiert, die Sie in der Richtlinie angeben: Die an erster Stelle positionierte Bezeichnung steht an unterster Stelle (geringste Vertraulichkeitsstufe), die an letzter Stelle positionierte Bezeichnung steht an höchster Stelle (höchste Vertraulichkeitsstufe).

2. Die Bezeichnung mit der höchsten Vertraulichkeitsstufe wird angewendet.
 
3. Die letzte untergeordnete Bezeichnung wird angewendet.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Konfigurieren der empfohlenen oder der automatischen Klassifizierung für eine Bezeichnung

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

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
        
        Die regulären Ausdrücke verwenden die RegEx-Muster von Office 365. Weitere Informationen finden Sie in der Office-Dokumentation unter [Defining regular expression based matches](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) (Definieren von Matches, die auf regulären Ausdrücken basieren). Darüber hinaus kann es hilfreich sein, die Programmbibliothek [Perl Regular Expression Syntax](http://www.boost.org/doc/libs/1_66_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html) von Boost als Referenz zu verwenden.
        
6. Entscheiden Sie, ob Sie die Werte unter **Mindestanzahl an Vorkommen** und **Count occurrence with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) ändern müssen, und klicken Sie dann auf **Speichern**. 
    
    Beispiel für die Optionen zu Vorkommen: Sie wählen den Informationstyp für die US-Sozialversicherungsnummer aus und legen für die Mindestanzahl von Vorkommen den Wert „2“ fest. Sie verfügen über ein Dokument, in dem dieselbe Sozialversicherungsnummer zweimal aufgeführt wird: Wenn Sie für **Count occurrences with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) die Einstellung **Ein** wählen, wird die Bedingung nicht erfüllt. Wenn Sie diese Option auf **Aus** festlegen, wird die Bedingung erfüllt.

7. Konfigurieren Sie auf dem Blatt **Bezeichnung** die folgenden Einstellungen, und klicken Sie dann auf **Speichern**:
    
    - Wählen Sie die automatische oder die empfohlene Klassifizierung: Wählen Sie für **Select how this label is applied: automatically or recommended to user** (Festlegen, wie diese Bezeichnung angewendet wird: automatisch oder empfohlen) die Einstellung **Automatic** (Automatisch) oder **Recommended** (Empfohlen).
    
    - Geben Sie den Text für die Benutzeraufforderung oder den Richtlinientipp an: Übernehmen Sie den Standardtext, oder geben Sie eine eigene Zeichenfolge ein.

8. Klicken Sie auf dem anfänglichen Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Ziehen Sie in Betracht, die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md) bereitzustellen. Dadurch können Ihre automatischen Klassifizierungsregeln genutzt werden, um Dateien aus Netzwerkfreigaben und lokalen Dateispeichern zu suchen, zu klassifizieren und zu schützen.  

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

