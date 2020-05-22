---
title: Konfigurieren von Bedingungen für eine Azure Information Protection-Bezeichnung – AIP
description: Mit Bedingungen für eine Bezeichnung können Sie einem Dokument oder einer E-Mail automatisch eine Bezeichnung zuweisen. Alternativ dazu können Sie Benutzer auffordern, eine empfohlene Bezeichnung auszuwählen.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e915f959-eafb-4375-8d2c-2f312edf2d29
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 7ca25b5e36afc9828b01d16c83ce133f3e521469
ms.sourcegitcommit: 8499602fba94fbfa28d7682da2027eeed6583c61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83746880"
---
# <a name="how-to-configure-conditions-for-automatic-and-recommended-classification-for-azure-information-protection"></a>Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021****eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

> [!NOTE]
> Diese Anweisungen gelten für den Azure Information Protection-Client (klassisch) und nicht für den Azure Information Protection-Client für einheitliche Bezeichnungen. Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client) an.
> 
> Informationen zum Konfigurieren der automatischen und empfohlenen Klassifizierung für den Unified-Bezeichnungs Client finden Sie in der Dokumentation zur Microsoft 365 Konformität. Wenden Sie z. b. [eine Vertraulichkeits Bezeichnung automatisch auf Inhalt an](/microsoft-365/compliance/apply-sensitivity-label-automatically).

Beim Konfigurieren von Bedingungen für eine Bezeichnung können Sie automatisch eine Bezeichnung für ein Dokument oder eine E-Mail zuweisen. Alternativ können Sie Benutzer auffordern, die von Ihnen empfohlene Bezeichnung auszuwählen. 

Beim Konfigurieren dieser Bedingungen können Sie vordefinierte Muster verwenden, z.B. für **Kreditkartennummern** oder **US-Sozialversicherungsnummern (SSN)**. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren. Diese Bedingungen gelten für den Haupttext in Dokumenten und E-Mails sowie für Kopf- und Fußzeilen. Weitere Informationen zu den Bedingungen finden Sie im Schritt 5 der [folgenden Vorgehensweise](#to-configure-recommended-or-automatic-classification-for-a-label).

Um eine bestmögliche Benutzererfahrung und Geschäftskontinuität zu gewährleisten, wird empfohlen, zunächst nicht die automatische Klassifizierung, sondern die empfohlene Klassifizierung zu verwenden. Bei dieser Konfiguration haben Ihre Benutzer die Möglichkeit, die Klassifizierung und zugeordnete Schutzaktionen zu akzeptieren bzw. diese Empfehlungen zu überschreiben, wenn sie nicht für das jeweilige Dokument oder die jeweilige E-Mail-Nachricht geeignet sind.

Nachfolgend sehen Sie eine Beispielaufforderung bei Konfiguration einer Bedingung, um eine Bezeichnung als empfohlene Aktion anzuwenden (einschließlich eines benutzerdefinierten Richtlinientipps):

![Azure Information Protection – Erkennung und Empfehlung](./media/info-protect-recommend-calloutsv2.png)

In diesem Beispiel kann der Benutzer auf **Jetzt ändern** klicken, um die empfohlene Bezeichnung anzuwenden, oder die Empfehlung ignorieren, indem er **Schließen** wählt. Wenn der Benutzer die Empfehlung verwerfen möchte und die Bedingung bei der nächsten Öffnung des Dokuments weiterhin gilt, wird die empfohlene Bezeichnung erneut angezeigt.

Wenn Sie die automatische und nicht die empfohlene Klassifizierung konfigurieren, wird die Bezeichnung automatisch angewendet, und dem Benutzer wird weiterhin eine Benachrichtigung in Word, Excel und PowerPoint angezeigt. Die Schaltflächen **jetzt ändern** und **verwerfen** werden jedoch durch **OK**ersetzt. In Outlook gibt es keine Benachrichtigung für die automatische Klassifizierung, und die Bezeichnung wird dann angewendet, wenn die E-Mail versendet wird.

> [!IMPORTANT]
>Konfigurieren Sie Bezeichnungen nicht für die automatische Klassifizierung und eine benutzerdefinierte Berechtigung. Die Option für benutzerdefinierte Berechtigungen ist eine [Schutzeinstellung](configure-policy-protection.md), über die Benutzer angeben können, wem welche Berechtigungen erteilt werden sollen.
>
>Wenn eine Bezeichnung für die automatische Klassifizierung und benutzerdefinierte Berechtigungen konfiguriert ist, wird der Inhalt für die Bedingungen geprüft, und die benutzerdefinierte Berechtigung wird nicht angewendet. Sie können empfohlene Klassifizierungen und benutzerdefinierte Berechtigungen verwenden.

## <a name="how-automatic-or-recommended-labels-are-applied"></a>Anwendung von automatischen oder empfohlenen Bezeichnungen

- Die automatische Klassifizierung gilt für Word, Excel und PowerPoint, wenn Sie Dokumente speichern und beim Senden von e-Mails auf Outlook anwenden. 
    
    Sie können die automatische Klassifizierung nicht für Dokumente und E-Mails verwenden, die zuvor manuell oder automatisch mit einer höheren Klassifizierung versehen wurden. 

- Die empfohlene Klassifizierung gilt für Word, Excel und PowerPoint beim Speichern von Dokumenten. Sie können die empfohlene Klassifizierung für Outlook erst verwenden, wenn Sie eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#enable-recommended-classification-in-outlook) konfiguriert haben, die derzeit in der Vorschauversion verfügbar ist.
    
    Sie können die empfohlene Klassifizierung nicht für Dokumente verwenden, die bereits eine höhere Klassifizierung aufweisen. 

Sie können dieses Verhalten ändern, sodass der Azure Information Protection-Client Dokumente regelmäßig auf die von Ihnen angegebenen Bedingungsregeln überprüft. Dies ist beispielsweise dann sinnvoll, wenn Sie [Auto Save](https://support.office.com/article/what-is-autosave-6d6bd723-ebfd-4e40-b5f6-ae6e8088f7a5) mit Office-Apps verwenden, die automatisch in Microsoft SharePoint, onedrive for Work, School oder onedrive for Home gespeichert werden. Zur Unterstützung dieses Szenarios können Sie eine [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#turn-on-classification-to-run-continuously-in-the-background) konfigurieren, die sich derzeit in der Vorschau Phase befindet. Die-Einstellung schaltet die Klassifizierung so um, dass Sie fortlaufend im Hintergrund ausgeführt wird.

### <a name="how-multiple-conditions-are-evaluated-when-they-apply-to-more-than-one-label"></a>So werden mehrere Bedingungen ausgewertet, wenn sie für mehrere Bezeichnungen gelten

1. Die Bezeichnungen werden zur Auswertung basierend auf der jeweiligen Position sortiert, die Sie in der Richtlinie angeben: Die an erster Stelle positionierte Bezeichnung steht an unterster Stelle (geringste Vertraulichkeitsstufe), die an letzter Stelle positionierte Bezeichnung steht an höchster Stelle (höchste Vertraulichkeitsstufe).

2. Die Bezeichnung mit der höchsten Vertraulichkeitsstufe wird angewendet.
 
3. Die letzte untergeordnete Bezeichnung wird angewendet.


## <a name="to-configure-recommended-or-automatic-classification-for-a-label"></a>Konfigurieren der empfohlenen oder der automatischen Klassifizierung für eine Bezeichnung

1. Wenn Sie dies nicht bereits getan haben, öffnen Sie ein neues Browserfenster, und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal). Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die zu konfigurier tende Bezeichnung aus.

3. Klicken Sie im Bereich **Bezeichnung** im Abschnitt **Konfigurieren von Bedingungen für die automatische Anwendung dieser Bezeichnung** auf **neue Bedingung hinzufügen**.

4. Wählen Sie im Bereich **Bedingung** die Option **Informationstypen** aus, wenn Sie eine vordefinierte Bedingung verwenden möchten, oder **Benutzer** definiert, wenn Sie Ihre eigenen angeben möchten:
    - Für **Informationstypen**: Wählen Sie eine der verfügbaren Bedingungen aus der Liste aus, und legen Sie dann die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Die Informationstypen verwenden die vertraulichen Informationstypen und die Mustererkennung von Office 365 zur Verhinderung von Datenverlust (Data Loss Prevention, DLP). Sie können aus vielen häufig verwendeten vertraulichen Informationstypen wählen. Einige davon sind spezifisch für verschiedene Regionen. Weitere Informationen finden Sie in der Office 365-Dokumentation unter [Wonach die vertraulichen Informationstypen suchen](/microsoft-365/compliance/what-the-sensitive-information-types-look-for).
        
        Die Liste der Informationstypen, die Sie im Azure-Portal auswählen können, wird regelmäßig mit allen neuen Office-DLP-Ergänzungen aktualisiert. Die Liste schließt jedoch benutzerdefinierte Typen vertraulicher Informationen aus, die Sie als Regelpaket definiert und in das Office 365 Security & Compliance Center hochgeladen haben.
        
        > [!IMPORTANT]
        > Einige der Typen von Informationen erfordern eine Mindestversion des Clients. [Weitere Informationen](#sensitive-information-types-that-require-a-minimum-version-of-the-client) 
        
        Wenn Azure Information Protection die von Ihnen ausgewählten Informationstypen auswertet, verwendet es nicht die Office-DLP-Einstellung auf Konfidenzniveau, sondern sucht entsprechend der niedrigsten Konfidenz nach Übereinstimmungen.
    
    - Für **Custom** (Benutzerdefiniert): Geben Sie einen Namen und eine Zeichenfolge für den Abgleich an. Diese darf weder Anführungszeichen noch Sonderzeichen enthalten. Legen Sie dann fest, ob für den Abgleich ein regulärer Ausdruck verwendet und ob die Groß-/Kleinschreibung beachtet werden soll. Legen Sie außerdem die Mindestanzahl der Vorkommen sowie die Einstellung fest, ob das Vorkommen über einen eindeutigen Wert verfügen muss, um gezählt zu werden.
        
        Die regulären Ausdrücke verwenden die RegEx-Muster von Office 365. Damit Sie reguläre Ausdrücke für Ihre benutzerdefinierten Bedingungen einfach angeben können, sehen Sie sich die folgende spezifische Version der [Perl Regular Expression Syntax](https://www.boost.org/doc/libs/1_37_0/libs/regex/doc/html/boost_regex/syntax/perl_syntax.html) von Boost an.
        
5. Entscheiden Sie, ob Sie die Werte unter **Mindestanzahl an Vorkommen** und **Count occurrence with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) ändern müssen, und klicken Sie dann auf **Speichern**. 
    
    Beispiel für die Optionen zu Vorkommen: Sie wählen den Informationstyp für die US-Sozialversicherungsnummer aus und legen für die Mindestanzahl von Vorkommen den Wert „2“ fest. Sie verfügen über ein Dokument, in dem dieselbe Sozialversicherungsnummer zweimal aufgeführt wird: Wenn Sie für **Count occurrences with unique value only** (Nur Vorkommen mit eindeutigem Wert zählen) die Einstellung **Ein** wählen, wird die Bedingung nicht erfüllt. Wenn Sie diese Option auf **Aus** festlegen, wird die Bedingung erfüllt.

6. Legen Sie im Bereich **Bezeichnung** Folgendes fest, und klicken Sie dann auf **Speichern**:
    
    - Wählen Sie die automatische oder die empfohlene Klassifizierung: Wählen Sie für **Select how this label is applied: automatically or recommended to user** (Festlegen, wie diese Bezeichnung angewendet wird: automatisch oder empfohlen) die Einstellung **Automatic** (Automatisch) oder **Recommended** (Empfohlen).
    
    - Geben Sie den Text für die Benutzeraufforderung oder den Richtlinientipp an: Übernehmen Sie den Standardtext, oder geben Sie eine eigene Zeichenfolge ein.

Nachdem Sie auf **Speichern** geklickt haben, sind Ihre vorgenommenen Änderungen automatisch für Benutzer und Dienste verfügbar. Es gibt keine gesonderte Veröffentlichungsoption mehr.

### <a name="sensitive-information-types-that-require-a-minimum-version-of-the-client"></a>Typen von vertraulichen Informationen, die eine Mindestversion des Clients erfordern

Die folgenden sensiblen Informationstypen erfordern mindestens eine Version von 1.48.204.0 des Azure Information Protection Clients:

- **Azure Service Bus-Verbindungszeichenfolge**
- **Azure IoT-Verbindungszeichenfolge**
- **Azure Storage-Konto**
- **Azure IAAS-Datenbankverbindungszeichenfolge und Azure SQL-Verbindungszeichenfolge**
- **Azure Redis Cache-Verbindungszeichenfolge**
- **Azure SaaS**
- **SQL Server-Verbindungszeichenfolge**
- **Azure DocumentDB-Authentifizierungsschlüssel**
- **Azure-Veröffentlichungseinstellung: Kennwort**
- **Azure Storage-Kontoschlüssel (generisch)**

Weitere Informationen zu diesen sensiblen Informationstypen finden Sie im folgenden Blogbeitrag: [Azure Information Protection unterstützt Sie bei der automatischen Ermittlung von Anmelde](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-helps-you-to-be-more-secure-by/ba-p/360181) Informationen.

Außerdem werden die folgenden sensiblen Informationstypen ab 1.48.204.0 des Azure Information Protection Clients nicht mehr unterstützt und im Azure-Portal nicht mehr angezeigt. Wenn Sie über Bezeichnungen verfügen, die diese vertraulichen Informationstypen verwenden, empfiehlt es sich, diese zu entfernen, da wir nicht sicherstellen können, dass Sie richtig erkannt werden und dass Verweise darauf in den Überprüfungs Berichten ignoriert werden sollten:

- **EU-Telefonnummer**
- **EU-GPS-Koordinaten**

## <a name="next-steps"></a>Nächste Schritte

Ziehen Sie in Betracht, die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md) bereitzustellen. Dadurch können Ihre automatischen Klassifizierungsregeln genutzt werden, um Dateien aus Netzwerkfreigaben und lokalen Dateispeichern zu suchen, zu klassifizieren und zu schützen.  

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).
