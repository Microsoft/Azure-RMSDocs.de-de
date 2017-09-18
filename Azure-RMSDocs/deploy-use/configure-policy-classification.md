---
title: "Konfigurieren von Bedingungen für eine Azure Information Protection-Bezeichnung"
description: "Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/07/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.openlocfilehash: 09ee8587e6b254584f70dbe2475063831fd5b845
ms.sourcegitcommit: 6636defa6eca24360f15fb9ef93c2b82dc36cf76
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen: 

- Die automatische Klassifizierung gilt beim Speichern von Dateien in Word, Excel und PowerPoint sowie beim Senden von E-Mails in Outlook. Sie können die automatische Klassifizierung nicht für Dateien verwenden, für die zuvor bereits manuell eine Bezeichnung festgelegt wurde.
 
- Die empfohlene Klassifizierung gilt beim Speichern von Dateien in Word, Excel und PowerPoint.

Beim Konfigurieren von Bedingungen können Sie vordefinierte Muster verwenden, z.B. für **Kreditkartennummern** oder **US-Sozialversicherungsnummern (SSN)**. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren. Diese Bedingungen gelten für den Haupttext in Dokumenten und E-Mails sowie für Kopf- und Fußzeilen. Weitere Informationen zu diesen Bedingungen finden Sie im Abschnitt [Details about the information types (Einzelheiten zu den Informationstypen)](#details-about-the-information-types).

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

5. Wählen Sie auf dem Blatt **Bedingung** die Option **Informationstypen** aus, wenn Sie eine vordefinierte Bedingung verwenden möchten, oder **Benutzerdefiniert**, um eine eigene Bedingung anzugeben. Klicken Sie anschließend auf **Speichern**:
    - Für **Informationstypen**: Wählen Sie eine der verfügbaren Bedingungen aus der Liste aus, und legen Sie dann die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Sie müssen die aktuelle Vorschauversion des Azure Information Protection-Clients verwenden, um die vollständige Liste der Bedingungen zu verwenden. Wenn Sie die aktuelle allgemein verfügbare Version des Clients besitzen, werden die folgenden fünf Bestimmungen unterstützt: **SWIFT-Code**, **Kreditkartennummer**, **US-Bankleitzahl (ABA Routing Number)**, **US-Sozialversicherungsnummer (SSN)** und **International Banking Account Number (IBAN)**. [Weitere Informationen](#details-about-the-information-types)
    
    - Für **Custom** (Benutzerdefiniert): Geben Sie einen Namen und eine Zeichenfolge für den Abgleich an. Diese darf weder Anführungszeichen noch Sonderzeichen enthalten. Legen Sie dann fest, ob für den Abgleich ein regulärer Ausdruck verwendet und ob die Groß-/Kleinschreibung beachtet werden soll. Legen Sie außerdem die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Wenn Sie die aktuelle Vorschauversion des Azure Information Protection-Clients besitzen, verwenden die regulären Ausdrücke die Regex-Muster von Office 365. Weitere Informationen finden Sie in der Office-Dokumentation unter [Defining regular expression based matches](https://technet.microsoft.com/library/jj674702(v=exchg.150).aspx#Anchor_2) (Definieren von Matches, die auf regulären Ausdrücken basieren). 
        
    **Beispiel für die Optionen zu Vorkommen**: Sie wählen die integrierte Option zum Ermitteln von US-Sozialversicherungsnummern und legen für die Mindestanzahl von Vorkommen den Wert „2“ fest. Sie verfügen über ein Dokument, in dem dieselbe Sozialversicherungsnummer zweimal aufgeführt wird: Wenn Sie für **Nur Vorkommen mit eindeutigen Werten zählen** die Einstellung **Ein** wählen, wird die Bedingung nicht erfüllt. Wenn Sie diese Option auf **Aus** festlegen, wird die Bedingung erfüllt.

6. Konfigurieren Sie auf dem Blatt **Label** (Bezeichnung) die folgenden Einstellungen, und klicken Sie dann auf **Save** (Speichern):
    
    - Wählen Sie die automatische oder die empfohlene Klassifizierung: Wählen Sie für **Select how this label is applied: automatically or recommended to user** (Festlegen, wie diese Bezeichnung angewendet wird: automatisch oder empfohlen) die Einstellung **Automatic** (Automatisch) oder **Recommended** (Empfohlen).
    
    - Geben Sie den Text für die Benutzeraufforderung oder den Richtlinientipp an: Übernehmen Sie den Standardtext, oder geben Sie eine eigene Zeichenfolge ein.

7. Klicken Sie auf dem anfänglichen Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="details-about-the-information-types"></a>Einzelheiten zu den Informationstypen

Wenn Sie über die aktuelle Vorschauversion des Azure Information Protection-Clients verfügen, wird die vollständige Liste der Informationstypen, die im Portal zur Verfügung steht, unterstützt:

- Die Informationstypen verwenden die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP). Sie können aus vielen häufig verwendeten vertraulichen Informationstypen wählen. Einige davon sind spezifisch für verschiedene Regionen. Weitere Informationen zu den Informationstypen, die Sie auswählen können, finden Sie in der Office-Dokumentation unter [What the sensitive information types look for (Wonach die vertraulichen Informationstypen suchen)](https://support.office.com/article/What-the-sensitive-information-types-look-for-fd505979-76be-4d9f-b459-abef3fc9e86b). 

- Die Liste der Informationstypen, die Sie im Azure-Portal auswählen können, wird regelmäßig mit allen neuen Office-DLP-Ergänzungen aktualisiert. Die Liste schließt jedoch benutzerdefinierte Typen vertraulicher Informationen aus, die Sie als Regelpaket definiert und in das Office 365 Security & Compliance Center hochgeladen haben. 

- Wenn Azure Information Protection die von Ihnen ausgewählten Informationstypen auswertet, verwendet es nicht die Office-DLP-Einstellung auf Konfidenzniveau, sondern sucht entsprechend der niedrigsten Konfidenz nach Übereinstimmungen.

Wenn Sie die aktuell verfügbare allgemeine Version des Clients besitzen, werden nur die folgenden Informationstypen unterstützt:

- [SWIFT Code](#swift-code ) (SWIFT-Code)

- [Credit Card Number](#credit-card-number ) (Kreditkartennummer)

- [ABA Routing Number](#aba-routing-number ) (BLZ)

- [USA Social Security Number](#usa-social-security-number-ssn) (US-Sozialversicherungsnummer)

- [International Banking Account Number (IBAN)](#international-banking-account-number-iban)

In den folgenden Abschnitten finden Sie weitere Informationen zu jedem dieser Informationstypen für allgemein verfügbare Versionen des Clients.

### <a name="swift-code"></a>SWIFT Code (SWIFT-Code)

Übereinstimmung für diesen Informationstyp anzeigen, wenn die Inhalte Folgendes enthalten:  

1. Eine der folgenden Zeichenfolgen: **swift**, **swiftnumber**, **swiftroutingnumber** 

2. Einen SWIFT-Code mit formatiertem Muster:  

    a. 4 Buchstaben (Bankcode)  

    b. 2 Buchstaben (Ländercode)  

    c. 2 Buchstaben oder Ziffern (Codierung des Ortes)  

    d. Optional 3 Buchstaben oder Ziffern (Kennzeichnung der Filiale)  


Beispiele zum Durchführen von Tests:

- **NEDSZAJJXXX Swiftroutingnumber**

- **NEDSZAJJ100 Swiftnumber** 

----


### <a name="credit-card-number"></a>Credit Card Number (Kreditkartennummer)

Übereinstimmung für diesen Informationstyp anzeigen, wenn die Inhalte Folgendes enthalten:  

- Eine gültige Kreditkartennummer mit formatiertem oder unformatiertem Muster, die mit dem [Luhn-Algorithmus](https://wikipedia.org/wiki/Luhn_algorithm) überprüft werden kann. Dieser Informationstyp ermittelt Karten aller großen Gesellschaften weltweit (u. a. Visa, MasterCard, Discover Card, American Express und Diners Club).

    - **Formatiert**:
    
        - 16 Ziffern: (dddd-dddd-dddd-dddd)  
        
    - **Unformatiert**:
    
        - (dddddddddddddddd)  


Beispiele zum Durchführen von Tests:

- **4242-4242-4242-4242**

- **4242424242424242** 

----

### <a name="aba-routing-number"></a>ABA Routing Number (BLZ)

Übereinstimmung für diesen Informationstyp anzeigen, wenn die Inhalte Folgendes enthalten:  

1. Mindestens eine der folgenden Zeichenfolgen: **aba**, **rtn**, **routing number** 

2. Eine US-amerikanische Bankleitzahl (ABA Routing Number) aus 9 Ziffern, formatiert oder unformatiert: 

    - **Formatiert**: 
        
        a. Vier Ziffern, die mit 0, 1, 2, 3, 6, 7 oder 8 beginnen 
        
        b. Ein Bindestrich 
        
        c. Vier Ziffern 
        
        d. Ein Bindestrich 
        
        e. Eine Ziffer 
        
        Beispiel: 3456-9876-1 ABA 
        
    - **Unformatiert**: 
        
        9 aufeinanderfolgende Ziffern, die mit 0, 1, 2, 3, 6, 7 oder 8 beginnen 
        
        Beispiel: 345698761 RTN 
 

Beispiele zum Durchführen von Tests:

- **3456-9876-1 ABA**

- **345698761 RTN** 

----

### <a name="usa-social-security-number-ssn"></a>USA Social Security Number (US-Sozialversicherungsnummer)

Übereinstimmung für diesen Informationstyp anzeigen, wenn die Inhalte Folgendes enthalten:  

1. Mindestens eine der folgenden Zeichenfolgen: **ssn**, **social security**, **ssid**, **ss#** 

2. Eine US-Sozialversicherungsnummer: 9 Ziffern, formatiert oder unformatiert:

    - **Formatiert**: 
    
        - Neun Ziffern mit folgendem Format: ddd-dd-dddd ODER ddd dd dddd 
        
    - **Unformatiert**: 
    
        - Neun Ziffern mit folgendem Format: ddddddddd 


Beispiele zum Durchführen von Tests:

- **SSN 123-45-6789**

- **SS# 123456789** 


----

### <a name="international-banking-account-number-iban"></a>International Banking Account Number (IBAN)

Übereinstimmung für diesen Informationstyp anzeigen, wenn die Inhalte Folgendes enthalten:  

1. Die folgende Zeichenfolge: **IBAN** 

2. Eine IBAN: Die IBAN beginnt mit dem Ländercode (zwei Buchstaben), auf den die Prüfziffern (zwei Ziffern) und die Kontoidentifikation (bis zu 30 Ziffern) folgen.


Beispiele zum Durchführen von Tests:

- **GB29 NWBK 6016 1331 9268 19 IBAN**


## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


