---
title: "Gewusst wie: Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung | Azure Information Protection"
description: "Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
translationtype: Human Translation
ms.sourcegitcommit: 4fcfcebc7da5a22a91911d70d4d787dc525d3485
ms.openlocfilehash: 4211adef1696a1b615bd3f25df568f4b5149c186


---

# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection

>*Gilt für: Azure Information Protection*

Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen: 

- Die automatische Klassifizierung gilt beim Speichern von Dateien in Word, Excel und PowerPoint sowie beim Senden von E-Mails in Outlook. Sie können die automatische Klassifizierung nicht für Dateien verwenden, für die zuvor bereits manuell eine Bezeichnung festgelegt wurde.
 
- Die empfohlene Klassifizierung gilt beim Speichern von Dateien in Word, Excel und PowerPoint.

Beim Konfigurieren von Bedingungen können Sie vordefinierte Muster verwenden, z. B. für Kreditkartennummern oder US-Sozialversicherungsnummern. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren. Diese Bedingungen gelten für den Haupttext in Dokumenten und E-Mails sowie für Kopf- und Fußzeilen. Weitere Informationen zu diesen Bedingungen finden Sie im Abschnitt [Informationen zu den integrierten Bedingungen](#information-about-the-built-in-conditions).

So werden mehrere Bedingungen ausgewertet, wenn sie für mehrere Bezeichnungen gelten:

1. Die Bezeichnungen werden zur Auswertung basierend auf der jeweiligen Position sortiert, die Sie in der Richtlinie angeben: Die an erster Stelle positionierte Bezeichnung steht an unterster Stelle (geringste Vertraulichkeitsstufe), die an letzter Stelle positionierte Bezeichnung steht an höchster Stelle (höchste Vertraulichkeitsstufe).

2. Die Bezeichnung mit der höchsten Vertraulichkeitsstufe wird angewendet.
 
3. Die letzte untergeordnete Bezeichnung wird angewendet.

> [!TIP]
>Um eine bestmögliche Benutzererfahrung und Geschäftskontinuität zu gewährleisten, wird empfohlen, zunächst nicht die automatische Klassifizierung, sondern die empfohlene Klassifizierung zu verwenden. Bei dieser Konfiguration haben Ihre Benutzer die Möglichkeit, die Bezeichnungs- oder Schutzaktion zu akzeptieren bzw. diese Empfehlungen zu überschreiben, wenn sie nicht für das jeweilige Dokument oder die jeweilige E-Mail-Nachricht geeignet sind.

Nachfolgend sehen Sie eine Beispielaufforderung bei Konfiguration einer Bedingung, um eine Bezeichnung als empfohlene Aktion anzuwenden (einschließlich eines benutzerdefinierten Richtlinientipps):

![Azure Information Protection – Erkennung und Empfehlung](../media/info-protect-recommend-callouts.png)

In diesem Beispiel kann der Benutzer auf **Change now** (Jetzt ändern) klicken, um die empfohlene Bezeichnung anzuwenden, oder die Empfehlung ignorieren, indem er die Leiste schließt.

## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Konfigurieren der empfohlenen oder der automatischen Klassifizierung für eine Bezeichnung

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die Bezeichnung, die Sie für die automatische oder empfohlene Klassifizierung konfigurieren möchten, für alle Benutzer gilt, wählen Sie die zu ändernde Bezeichnung auf dem Blatt **Policy:Global** (Richtlinie: Global) aus und nehmen dann Ihre Änderungen bei Bedarf am Blatt **Label** (Bezeichnung) und allen nachfolgenden Blättern vor. 

     Wenn sich die Bezeichnung, die Sie konfigurieren möchten, in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, wählen Sie zunächst die bereichsbezogene Richtlinie auf dem ersten Blatt **Azure Information Protection** aus.  

3. Klicken Sie auf dem Blatt **Label** (Bezeichnung) im Abschnitt **Configure conditions for automatically applying this label** (Bedingungen konfigurieren, um diese Bezeichnung automatisch anzuwenden) auf **Add a new condition** (Neue Bedingung hinzufügen).

4. Wählen Sie auf dem Blatt **Condition** (Bedingung) die Option **Built-in** (Integriert) aus, wenn Sie eine vordefinierte Bedingung verwenden möchten, oder **Custom** (Benutzerdefiniert), um eine eigene Bedingung anzugeben. Klicken Sie anschließend auf **Save** (Speichern):

    - Für **Built-in** (Integriert): Wählen Sie eine der verfügbaren Bedingungen aus der Liste aus, und legen Sie dann die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Weitere Informationen zu den Erkennungsregeln für diese Bedingungen sowie eine Reihe von Beispielen finden Sie im Abschnitt [Informationen zu den integrierten Bedingungen](#information-about-the-built-in-conditions).

    - Für **Custom** (Benutzerdefiniert): Geben Sie einen Namen und eine Zeichenfolge für den Abgleich an. Diese darf weder Anführungszeichen noch Sonderzeichen enthalten. Legen Sie dann fest, ob für den Abgleich ein regulärer Ausdruck verwendet und ob die Groß-/Kleinschreibung beachtet werden soll. Legen Sie außerdem die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
    **Beispiel für die Optionen zu Vorkommen**: Sie wählen die integrierte Option zum Ermitteln von US-Sozialversicherungsnummern und legen für die Mindestanzahl von Vorkommen den Wert 2 fest. Sie verfügen über ein Dokument, in dem dieselbe Sozialversicherungsnummer zweimal aufgeführt wird: Wenn Sie für **Count occurrences with unique values only** (Nur Vorkommen mit eindeutigen Werten zählen) die Einstellung **On** (Ein) wählen, wird die Bedingung nicht erfüllt. Wenn Sie für diese Option die Einstellung **Off** (Aus) festlegen, wird die Bedingung erfüllt.

5. Konfigurieren Sie auf dem Blatt **Label** (Bezeichnung) die folgenden Einstellungen, und klicken Sie dann auf **Save** (Speichern):

    - Wählen Sie die automatische oder die empfohlene Klassifizierung: Wählen Sie für **Select how this label is applied: automatically or recommended to user** (Festlegen, wie diese Bezeichnung angewendet wird: automatisch oder empfohlen) die Einstellung **Automatic** (Automatisch) oder **Recommended** (Empfohlen).

    - Geben Sie den Text für die Benutzeraufforderung oder den Richtlinientipp an: Übernehmen Sie den Standardtext, oder geben Sie eine eigene Zeichenfolge ein.

6. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Publish** (Veröffentlichen), um Ihre Änderungen für die Benutzer verfügbar zu machen.

## <a name="information-about-the-built-in-conditions"></a>Informationen zu den integrierten Bedingungen

Während des Vorschauzeitraums können Sie die folgenden Bedingungen wählen (beachten Sie, dass diese Beispiele auf US-amerikanischen Standards basieren):

- [SWIFT Code](#swift-code ) (SWIFT-Code)

- [Credit Card Number](#credit-card-number ) (Kreditkartennummer)

- [ABA Routing Number](#aba-routing-number ) (BLZ)

- [USA Social Security Number](#usa-social-security-number-ssn) (US-Sozialversicherungsnummer)

- [International Banking Account Number (IBAN)](#international-banking-account-number-iban)


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






<!--HONumber=Dec16_HO1-->


