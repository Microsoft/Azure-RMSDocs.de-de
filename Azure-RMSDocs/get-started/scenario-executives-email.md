---
# required metadata

title: Szenario – Führungskräfte tauschen vertrauliche Informationen sicher aus | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e18cf5df-859e-4028-8d19-39b0842df33d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Szenario – Führungskräfte tauschen vertrauliche Informationen sicher aus

*Gilt für: Azure Rights Management, Office 365*

In diesem Szenario und der unterstützenden Benutzerdokumentation wird Azure Rights Management verwendet, damit Führungskräfte E-Mail-Nachrichten und Anlagen sicher austauschen können. Richtlinien beschränken automatisch den Zugriff auf die Führungskräfte, ohne dass diese eine bestimmte Aktion ausführen müssen. Die E-Mail-Nachrichten und Anlagen werden automatisch von Azure Rights Management geschützt.

Bei Bedarf können Sie der Regel eine Ausnahme hinzufügen, indem Sie beispielsweise im Betreff der E-Mail-Nachricht die Abkürzung "DNP" (Do Not Protect = Nicht schützen) hinzufügen. Führungskräfte können dies etwa angeben, wenn sie eine ungeschützte E-Mail zur Überprüfung an bestimmte Führungskräfte senden möchten, bevor Sie sie an andere Kollegen weiterleiten.

Die Anweisungen sind unter den folgenden Umständen geeignet:

-   Führungskräfte tauschen vertrauliche Informationen untereinander aus, die für andere nicht freigegeben werden sollen.

-   Führungskräfte können diese E-Mail-Nachrichten quasi wie bisher senden, müssen sie allerdings an eine geschäftliche E-Mail-Adresse anstatt an eine private E-Mail-Adresse senden.

-   Führungskräfte haben eine Möglichkeit, die Regel selbst zu überschreiben, wenn sie eine ungeschützte E-Mail-Nachricht an andere Führungskräfte senden möchten.

## Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, und führen Sie dann die Anweisungen für die unterstützenden Verfahren durch, bevor Sie mit der Benutzerdokumentation fortfahren.

## Anforderungen bei diesem Szenario
Damit die Anweisungen in diesem Szenario funktionieren, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Sie haben Konten und Gruppen für Office 365 oder Azure Active Directory vorbereitet:<br /><br />– Eine E-Mail-aktivierte Gruppe namens **Führungskräfte**, der alle Führungskräfte angehören<br /><br />– Eine E-Mail-aktivierte Gruppe namens **RMS-Administratoren**, der alle Administratoren angehören, die Azure RMS konfigurieren|[Vorbereiten für Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Ihr Azure Rights Management-Mandantenschlüssel wird von Microsoft verwaltet. Sie verwenden nicht BYOK (Bring your own key, Eigenen Schlüssel verwenden)|[Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](https://technet.microsoft.com/library/dn440580.aspx)|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Einer der folgenden Konfigurationen:<br /><br />– Exchange Online ist für Azure Rights Management aktiviert<br /><br />– Der RMS-Connector ist für die lokale Exchange-Anwendung installiert und konfiguriert|Für Exchange Online: Weitere Informationen finden Sie im Abschnitt **Exchange Online: IRM-Konfiguration** unter [Konfigurieren von Anwendungen für Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx).<br /><br />Für lokales Exchange: [Bereitstellen des Azure Rights Management-Verbindungsdiensts](https://technet.microsoft.com/library/dn375964.aspx)|
|Sie haben wie nachfolgend beschrieben eine benutzerdefinierte Vorlage konfiguriert.|[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Sie haben wie später in diesem Artikel beschrieben eine Transportschutzregel für IRM konfiguriert .|Für Exchange Online: [Erstellen einer Transportschutzregel](https://technet.microsoft.com/library/dd302432.aspx)<br /><br />Für Exchange 2013: [Erstellen einer Transportschutzregel](https://technet.microsoft.com/en-us/library/dd302432%28v=exchg.150%29.asp)<br /><br />Für Exchange 2010: [Erstellen einer Transportschutzregel](https://technet.microsoft.com/en-us/library/dd302432%28v=exchg.141%29.aspx)|

### So konfigurieren Sie die benutzerdefinierte Vorlage für Führungskräfte

1.  Im klassischen Azure-Portal: Erstellen Sie eine neue benutzerdefinierte Vorlage für Azure Rights Management, die die folgenden Werte und Einstellungen enthält:

    -   Name: **Führungskräfte**

    -   Rechte: Erteilen Sie der E-Mail-aktivierten Gruppe **Führungskräfte** das Recht **Mitbesitzer**.

    -   Bereich: Wählen Sie die E-Mail-aktivierten Gruppen **Führungskräfte** und **RMS-Administratoren** aus.

2.  Veröffentlichen Sie die neue Vorlage.

3.  Nur für Exchange Online: Aktualisieren Sie die Vorlagen für Exchange Online mithilfe des Windows PowerShell-Befehls für Exchange Online:

    ```
    Import-RMSTrustedPublishingDomain -Name "RMS Online -1" -RefreshTemplates -RMSOnline
    ```

### So konfigurieren Sie die Transportregel für IRM

-   Entnehmen Sie der in der Tabelle angegebenen Exchange-Dokumentation die Verfahrensinformationen, um die Transportregel mit den folgenden Einstellungen zu erstellen:

    -   Name: **Vorlagen vom Typ "Führungskräfte" auf E-Mails von Führungskräften anwenden**

    -   Geben Sie die Gruppe **Führungskräfte** als Absender und Empfänger für die Regel sowie weitere Bedingungen an.

    -   Wählen Sie für die Aktion **Rechteschutz auf Nachricht anwenden mit**, und wählen Sie dann die konfigurierte Vorlage **Führungskräfte** aus.

    -   Fügen Sie die Ausnahme **DNP** (als Abkürzung für "Do Not Protect" = Nicht schützen) hinzu oder spezifizieren Sie die Ausnahme mit eigenen Worten, die in die Betreffzeile eingegeben werden kann.

    -   Stellen Sie sicher, dass für die Regel **Erzwingen** festgelegt ist.

## Anweisungen für Benutzerdokumentation
Sofern Sie keine Anweisungen zur Angabe von **DNP** oder Ihrer eigenen Worte oder Ausdrücke im E-Mail-Betreff bereitstellen, erhalten die Benutzer keine Verfahrensanweisungen zu diesem Szenario, da der Schutz der von und zu Führungskräften gesendeten E-Mails keine spezielle Aktion seitens der Führungskräfte erfordert. E-Mail-Nachrichten und -Anlagen werden automatisch so geschützt, dass nur die Mitglieder der Gruppe "Führungskräfte" darauf zugreifen können.

Allerdings müssen Sie die Führungskräfte und das Helpdesk gegebenenfalls informieren, dass diese E-Mails automatisch geschützt werden und dies ihre Nutzung einschränken kann. Die E-Mails können beispielsweise nicht von unberechtigten Benutzern gelesen werden, wenn sie später an diese weitergeleitet werden. Wenn Sie die DNP-Ausnahme (oder ein Äquivalent) konfiguriert haben, stellen Sie sicher, dass diese Konfiguration dem Helpdesk bekannt ist, sodass Führungskräfte die Regel selbst überschreiben können, ohne einen Exchange-Administrator kontaktieren zu müssen.

Verwenden Sie die folgende Vorlage, kopieren Sie die Ankündigung, und fügen Sie sie in eine Nachricht für die Endbenutzer ein. Nehmen Sie in Anpassung an Ihre Umgebung die folgenden Änderungen vor:

1.  Ersetzen Sie die Instanzen von *&lt;Organisationsname&gt;* durch den Namen Ihrer Organisation.

2.  Wenn Sie anstatt DNP eine andere Zeichenfolge für die Ausnahme wählen, ersetzen Sie diesen Wert und die Erklärung entsprechend.

3.  Ersetzen Sie *&lt;E-Mail-Domäne&gt;* durch den E-Mail-Domänennamen Ihres Unternehmens.

4.  Ersetzen Sie die *&lt;Kontaktdetails&gt;* durch Anweisungen dazu, wie sich Benutzer an das Helpdesk wenden können, z.B. über einen Link zur Website, eine E-Mail-Adresse oder eine Telefonnummer.

5.  Nehmen Sie jegliche sonstigen Änderungen an der Ankündigung vor, und senden Sie sie anschließend an diese Benutzer.

Die Beispieldokumentation veranschaulicht, wie diese Ankündigung für Benutzer nach Ihren Anpassungen aussehen könnte.

![Benutzerdokumentationsvorlage für die Azure RMS-Schnellbereitstellung](../media/AzRMS_UsersBanner.png)

### IT-Ankündigung: E-Mails von Führungskräften der Gruppe &lt;Organisationsname&gt; sind jetzt automatisch geschützt.
Von nun an werden Inhalte und Anlagen von E-Mail-Nachrichten, die an andere &lt;Organisationsname&gt;-Führungskräfte im Unternehmen gesendet werden, automatisch so geschützt, dass nur andere Führungskräfte im Unternehmen darauf Zugriff haben, um die Informationen zu lesen, zu drucken, zu kopieren usw. Diese Einschränkung gilt auch, wenn Sie die E-Mail-Nachricht an andere weiterleiten oder die Anlagen speichern. Dieser Schutz hilft, Datenverluste bei vertraulichen oder sensiblen Informationen zu vermeiden.

Wenn Sie möchten, dass Dritte, die keine &lt;Organisationsname&gt;-Führungskräfte sind, die Informationen in diesen E-Mails lesen und bearbeiten können, müssen Sie diesen die Informationen in einer separaten E-Mail senden. Um den automatischen Schutz zu überschreiben, geben Sie die Buchstaben **DNP** (als Abkürzung für "Do Not Protect" = Nicht schützen) an einer beliebigen Stelle in den Betreff der E-Mail-Nachricht ein.

Wenn Sie vertrauliche geschäftliche Informationen an eine andere &lt;Organisationsname&gt;-Führungskraft senden möchten, wählen Sie deren geschäftliche E-Mail-Adresse (*Name*@@&lt;E-Mail-Domäne&gt;) und keine private E-Mail-Adresse.

**Benötigen Sie Unterstützung?**

-   Wenden Sie sich an das Helpdesk: &lt;Kontaktdetails&gt;

### Beispielbenutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

#### IT-Ankündigung: E-Mails von VanArsdel-Führungskräften sind jetzt automatisch geschützt.
Von nun an werden Inhalte und Anlagen von E-Mail-Nachrichten, die an andere VanArsdel-Führungskräfte im Unternehmen gesendet werden, automatisch so geschützt, dass nur diese Führungskräfte im Unternehmen darauf Zugriff haben, um die Informationen zu lesen, zu drucken, zu kopieren usw. Diese Einschränkung gilt auch, wenn Sie die E-Mail-Nachricht an andere weiterleiten oder die Anlagen speichern. Dieser Schutz hilft, Datenverluste bei vertraulichen oder sensiblen Informationen zu vermeiden.

Wenn Sie möchten, dass Dritte, die keine VanArsdel-Führungskräfte sind, die Informationen in diesen E-Mails lesen und bearbeiten können, müssen Sie die Informationen in einer separaten E-Mail an sie senden. Um den automatischen Schutz zu überschreiben, geben Sie die Buchstaben **DNP** (als Abkürzung für "Do Not Protect" = Nicht schützen) an einer beliebigen Stelle in den Betreff der E-Mail-Nachricht ein.

Wenn Sie vertrauliche Unternehmensinformationen an eine andere VanArsdel-Führungskraft senden möchten, wählen Sie deren geschäftliche E-Mail-Adresse (*name*@vanarsdelltd.com) und keine private E-Mail-Adresse.

**Benötigen Sie Unterstützung?**

-   Wenden Sie sich an das Helpdesk: helpdesk@vanarsdelltd.com



<!--HONumber=May16_HO3-->


