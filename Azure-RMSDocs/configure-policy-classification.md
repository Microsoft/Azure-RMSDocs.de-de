---
title: Konfigurieren von Bedingungen für eine Azure Information Protection-Bezeichnung
description: Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/29/2018
ms.topic: article
ms.service: information-protection
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 605173136442ed3af5b50e565cae79a94b16fb27
ms.sourcegitcommit: 0bc877840b168d05a16964b4ed0d28a9ed33f871
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2018
ms.locfileid: "43297989"
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen. 

Beim Konfigurieren dieser Bedingungen können Sie vordefinierte Muster verwenden, z.B. für **Kreditkartennummern** oder **US-Sozialversicherungsnummern (SSN)**. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren. Diese Bedingungen gelten für den Haupttext in Dokumenten und E-Mails sowie für Kopf- und Fußzeilen. Weitere Informationen zu den Bedingungen finden Sie im Schritt 5 der [folgenden Vorgehensweise](#to-configure-recommended-or-automatic-classification-for-a-label).

Um eine bestmögliche Benutzererfahrung und Geschäftskontinuität zu gewährleisten, wird empfohlen, zunächst nicht die automatische Klassifizierung, sondern die empfohlene Klassifizierung zu verwenden. Bei dieser Konfiguration haben Ihre Benutzer die Möglichkeit, die Klassifizierung und zugeordnete Schutzaktionen zu akzeptieren bzw. diese Empfehlungen zu überschreiben, wenn sie nicht für das jeweilige Dokument oder die jeweilige E-Mail-Nachricht geeignet sind.

Nachfolgend sehen Sie eine Beispielaufforderung bei Konfiguration einer Bedingung, um eine Bezeichnung als empfohlene Aktion anzuwenden (einschließlich eines benutzerdefinierten Richtlinientipps):

![Azure Information Protection – Erkennung und Empfehlung](./media/info-protect-recommend-calloutsv2.png)

In diesem Beispiel kann der Benutzer auf **Jetzt ändern** klicken, um die empfohlene Bezeichnung anzuwenden, oder die Empfehlung ignorieren, indem er **Schließen** wählt. Wenn der Benutzer die Empfehlung verwerfen möchte und die Bedingung bei der nächsten Öffnung des Dokuments weiterhin gilt, wird die empfohlene Bezeichnung erneut angezeigt. 

> [!IMPORTANT]
>Konfigurieren Sie Bezeichnungen nicht für die automatische Klassifizierung und eine benutzerdefinierte Berechtigung. Die Option für benutzerdefinierte Berechtigungen ist eine [Schutzeinstellung](configure-policy-protection.md), über die Benutzer angeben können, wem welche Berechtigungen erteilt werden sollen.
>
>Wenn eine Bezeichnung für die automatische Klassifizierung und benutzerdefinierte Berechtigungen konfiguriert ist, wird der Inhalt für die Bedingungen geprüft, und die benutzerdefinierte Berechtigung wird nicht angewendet. Sie können empfohlene Klassifizierungen und benutzerdefinierte Berechtigungen verwenden.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Anwendung von automatischen oder empfohlenen Bezeichnungen

- Die automatische Klassifizierung gilt beim Speichern von Dokumenten in Word, Excel und PowerPoint sowie beim Senden von E-Mails in Outlook. 
    
    Sie können die automatische Klassifizierung nicht für Dokumente und E-Mails verwenden, die zuvor bereits manuell oder automatisch mit einer höheren Klassifizierung benannt wurden. 

- Die empfohlene Klassifizierung gilt beim Speichern von Dokumenten in Word, Excel und PowerPoint. Sie können die empfohlene Klassifizierung für Outlook erst verwenden, wenn Sie eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook) konfiguriert haben, die derzeit in der Vorschauversion verfügbar ist.
    
    Sie können die empfohlene Klassifizierung nicht für Dokumente verwenden, die bereits eine höhere Klassifizierung aufweisen. 

Sie können dieses Verhalten ändern, sodass der Azure Information Protection-Client Dokumente regelmäßig auf die von Ihnen angegebenen Bedingungsregeln überprüft. Für diese Konfiguration ist eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) erforderlich, die derzeit als Vorschau verfügbar ist.

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>So werden mehrere Bedingungen ausgewertet, wenn sie für mehrere Bezeichnungen gelten

1. Die Bezeichnungen werden zur Auswertung basierend auf der jeweiligen Position sortiert, die Sie in der Richtlinie angeben: Die an erster Stelle positionierte Bezeichnung steht an unterster Stelle (geringste Vertraulichkeitsstufe), die an letzter Stelle positionierte Bezeichnung steht an höchster Stelle (höchste Vertraulichkeitsstufe).

2. Die Bezeichnung mit der höchsten Vertraulichkeitsstufe wird angewendet.
 
3. Die letzte untergeordnete Bezeichnung wird angewendet.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Konfigurieren der empfohlenen oder der automatischen Klassifizierung für eine Bezeichnung

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die Bezeichnung aus, die Sie konfigurieren möchten.

3. Klicken Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Configure conditions for automatically applying this label** (Bedingungen konfigurieren, um diese Bezeichnung automatisch anzuwenden) auf **Add a new condition** (Neue Bedingung hinzufügen).

4. Wählen Sie auf dem Blatt **Bedingung** die Option **Informationstypen** aus, wenn Sie eine vordefinierte Bedingung verwenden möchten, oder **Benutzerdefiniert**, um eine eigene Bedingung anzugeben:
    - Für **Informationstypen**: Wählen Sie eine der verfügbaren Bedingungen aus der Liste aus, und legen Sie dann die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Die Informationstypen verwenden die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP). Sie können aus vielen häufig verwendeten vertraulichen Informationstypen wählen. Einige davon sind spezifisch für verschiedene Regionen. Weitere Informationen finden Sie in der Office-Dokumentation unter [What the sensitive information types look for (Wonach die vertraulichen Informationstypen suchen)](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b).
        
        Die Liste der Informationstypen, die Sie im Azure-Portal auswählen können, wird regelmäßig mit allen neuen Office-DLP-Ergänzungen aktualisiert. Die Liste schließt jedoch benutzerdefinierte Typen vertraulicher Informationen aus, die Sie als Regelpaket definiert und in das Office 365 Security & Compliance Center hochgeladen haben.
        
        > [!IMPORTANT]
        > Einige der Typen von Informationen erfordern eine Mindestversion des Clients. [Weitere Informationen](#sensitive-information-types-that-require-a-minimum-version-of-the-client) 
        
        Wenn Azure Information Protection die von Ihnen ausgewählten Informationstypen auswertet, verwendet es nicht die Office-DLP-Einstellung auf Konfidenzniveau, sondern sucht entsprechend der niedrigsten Konfidenz nach Übereinstimmungen.
    
    - Für **Custom** (Benutzerdefiniert): Geben Sie einen Namen und eine Zeichenfolge für den Abgleich an. Diese darf weder Anführungszeichen noch Sonderzeichen enthalten. Legen Sie dann fest, ob für den Abgleich ein regulärer Ausdruck verwendet und ob die Groß-/Kleinschreibung beachtet werden soll. Legen Sie außerdem die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Die regulären Ausdrücke verwenden die RegEx-Muster von Office 365. Damit Sie reguläre Ausdrücke für Ihre benutzerdefinierten Bedingungen einfach angeben können, sehen Sie sich die folgende spezifische Version der [Perl Regular Expression Syntax](https://www.boost.org/doc/libs/1_37_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html) von Boost an.
        
5. Entscheiden Sie, ob Sie die Werte unter **Mindestanzahl an Vorkommen** und **Count occurrence with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) ändern müssen, und klicken Sie dann auf **Speichern**. 
    
    Beispiel für die Optionen zu Vorkommen: Sie wählen den Informationstyp für die US-Sozialversicherungsnummer aus und legen für die Mindestanzahl von Vorkommen den Wert „2“ fest. Sie verfügen über ein Dokument, in dem dieselbe Sozialversicherungsnummer zweimal aufgeführt wird: Wenn Sie für **Count occurrences with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) die Einstellung **Ein** wählen, wird die Bedingung nicht erfüllt. Wenn Sie diese Option auf **Aus** festlegen, wird die Bedingung erfüllt.

6. Konfigurieren Sie auf dem Blatt **Bezeichnung** die folgenden Einstellungen, und klicken Sie dann auf **Speichern**:
    
    - Wählen Sie die automatische oder die empfohlene Klassifizierung: Wählen Sie für **Select how this label is applied: automatically or recommended to user** (Festlegen, wie diese Bezeichnung angewendet wird: automatisch oder empfohlen) die Einstellung **Automatic** (Automatisch) oder **Recommended** (Empfohlen).
    
    - Geben Sie den Text für die Benutzeraufforderung oder den Richtlinientipp an: Übernehmen Sie den Standardtext, oder geben Sie eine eigene Zeichenfolge ein.

Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

### <a name="sensitive-information-types-that-require-a-minimum-version-of-the-client"></a>Typen von vertraulichen Informationen, die eine Mindestversion des Clients erfordern

Die folgenden Typen vertraulicher Informationen erfordern zurzeit die Vorschauversion des Azure Information Protection-Clients:

- **EU Phone Number** (EU-Telefonnummer)
- **EU Mobile Phone Number** (EU-Mobiltelefonnummer)
- **EU Passport Number** (EU-Reisepassnummer)
- **EU Driver's License Number** (EU-Führerscheinnummer)
- **EU GPS Coordinates** (EU-GPS-Koordinaten)
- **EU National Identification Number** (Nationale EU-Identifikationsnummer)
- **EU Social Security Number (SSN) or Equivalent ID** (EU-Sozialversicherungsnummer (SSN) oder entsprechende ID)
- **EU Tax Identification Number (TIN)** (EU-Steueridentifikationsnummer)
- **Thai Population Identification Code** (Thailändischer Bevölkerungsidentifikationscode)
- **EU National Identification Number** (Nationale türkische Identifikationsnummer)
- **Japanese Residence Card Number** (Nummer einer japanischen Aufenthaltskarte)


## <a name="next-steps"></a>Nächste Schritte

Ziehen Sie in Betracht, die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md) bereitzustellen. Dadurch können Ihre automatischen Klassifizierungsregeln genutzt werden, um Dateien aus Netzwerkfreigaben und lokalen Dateispeichern zu suchen, zu klassifizieren und zu schützen.  

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).


