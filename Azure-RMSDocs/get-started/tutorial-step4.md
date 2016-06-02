---
# erforderliche Metadaten

Titel: Azure RMS Schnellstart-Tutorial Schritt 4 | Azure RMS-Beschreibung: Der vierte Schritt eines Tutorials, in dem Sie Microsoft Azure Rights Management in nur fünf Schritten und weniger als 15 Minuten für Ihr Unternehmen testen können.
keywords: author: cabailey manager: mbaldwin ms.date: 04/28/2016 ms.topic: get-started-article ms.prod: azure ms.service: rights-management ms.technology: techgroup-identity ms.assetid: f8340056-87a1-4daa-8b63-3d95fc381b9c

# optionale Metadaten

ROBOTS: audience: ms.devlang: ms.reviewer: esaggese ms.suite: ems ms.tgt_pltfrm: ms.technology: ms.custom:

---


# Azure RMS Quick Start – Schritt 4: Bitten Sie die Empfänger, das E-Mail-Dokument zu öffnen

*Gilt für: Azure Rights Management, Office 365*


Wechseln zu: 
> [!div class="op_single_selector"]
- [Einführung](quick-start-tutorial.md)
- [Schritt 1: Aktivieren von Azure RMS](tutorial-step1.md)
- [Schritt 2: Installieren der RMS-Freigabe-App](tutorial-step2.md)
- [Schritt 3: Senden des vertraulichen Dokuments per E-Mail](tutorial-step3.md)
- [Schritt 4: Lesen des Dokuments durch den Empfänger](tutorial-step4.md)
- [Schritt 5: Nachverfolgen des Dokuments](tutorial-step5.md)


![Azure RMS Schnellstart-Tutorial Schritt 4](../media/AzRMS_QuickStartSteps4.PNG)

Die Empfänger können das als E-Mail-Anlage gesendete, geschützte Dokument auf verschiedenen Geräten lesen. Die Geräte umfassen iPads, iPhones, Android-Tablets und -Smartphones sowie Macintosh- und Windows-Computer.

Bitten Sie die Empfänger, die gesendete E-Mail zu lesen. Die E-Mail wird den Empfängern mit dem folgenden vorangehenden Text angezeigt:

**Der Absender hat die Anlagen mit Microsoft RMS geschützt. Sie müssen sich** [anmelden](http://aka.ms/rms)
      **, um sie zu öffnen.**

Sobald der Empfänger auf den Link klickt, wird er weitergeleitet und erhält Anweisungen zur Installation der RMS-Freigabe-App und ggf. zur Registrierung für ein kostenloses Konto. Das kostenlose Konto gewährt Zugriff auf ein RMS for Individuals-Abonnement, mit dem autorisierte Benutzer ein geschütztes Dokument immer lesen können, auch wenn ihre Organisation nicht über Azure RMS verfügt. Sie können die geschützte Anlage dann mithilfe der folgenden Anweisungen lesen.

![Screenshots zu Schritt 4 des Tutorials](../media/AzRMS_Tutorial_4_Screenshots.png)

### So zeigen Sie die Anlage des geschützten Dokuments an

1.  Da die mit Azure Rights Management geschützte Datei ein Word-Dokument ist, verfügt die E-Mail über zwei Anlagen. Es handelt sich tatsächlich um zwei Versionen derselben Datei, aber mit unterschiedlichen Dateierweiterungen. Öffnen Sie die Version, die über die Dateinamenerweiterung **.ppdf** verfügt (**Confidential.ppdf**).

    Wenn Sie eine [Office-Version mit Rights Management-Unterstützung auf Ihrem Gerät installiert haben](https://technet.microsoft.com/library/dn655136.aspx), können Sie die andere Version der Datei (**Confidential.docx**) öffnen, um sie in Word zu lesen.

2.  Wenn Sie zur Eingabe von Benutzernamen und Kennwort aufgefordert werden, geben Sie Ihren Benutzernamen im gleichen Format wie die E-Mail-Adresse ein, die Sie zum Senden der E-Mail und der Anlage verwendet haben. Beispiel: **janetm@contoso.com** oder **p.dover@fabrikam.com**. Geben Sie das Kennwort ein, das Sie beim Registrieren von RMS for Individuals erhalten haben. Wenn Ihre Organisation jedoch über Azure RMS verfügt, geben Sie Ihr übliches Arbeitskennwort ein.

Das Dokument wird geöffnet, und Sie können nun den Inhalt lesen. Der Text könnte wie folgt lauten: **Wenn dieser Text in der E-Mail-Anlage lesbar ist, hat der Absender eine mit Azure RMS geschützte Datei erfolgreich freigegeben.** Da der Inhalt schreibgeschützt ist, können Sie ihn nicht ändern.

Als optionalen Schritt könnten Sie den Empfänger bitten, die E-Mail an andere Personen weiterzuleiten, die in der ursprünglichen E-Mail nicht enthalten waren. Diese Empfänger sind nicht in der Lage, die Anlage zu öffnen, selbst wenn sie in einer Organisation tätig sind, die über Azure Rights Management verfügt, oder ein eigenes RMS for Individuals-Abonnement angefordert haben. Bei der Aufforderung zur Eingabe des Benutzernamens wird den Empfängern der Zugriff verweigert.

Nachdem der Empfänger die Anlage nun geöffnet und optional an einen anderen Empfänger weitergeleitet hat, erhalten Sie eine E-Mail-Benachrichtigung über die jeweiligen Aktivitäten. Da E-Mails jedoch leicht in Vergessenheit geraten, lassen sich Dokumentzugriffe einfacher mithilfe der Dokumentenverfolgungs-Website überwachen. Dies wird im letzten Schritt veranschaulicht.

|Weitere Informationen zu...|Weitere Informationen|
|--------------------------------|--------------------------|
|Umfassende Erläuterung dazu, wie die durch Azure Rights Management geschützten Dateien angezeigt werden|[Anzeigen und Verwenden der durch Rights Management geschützten Dateien](../rms-client/sharing-app-view-use-files.md)|
|Kostenloses RMS for Individuals-Abonnement|[RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|Informationen zu den beiden Versionen der an die E-Mail angehängten Datei|[Erläuterung zur automatisch erstellten PPDF-Datei](../rms-client/sharing-app-dialog-box.md#what-s-the-ppdf-file-that-s-automatically-created-)|


>[!div class="step-by-step"] [« Schritt 3](tutorial-step3.md)
[Schritt 5 »](tutorial-step5.md)

<!--HONumber=May16_HO2-->


