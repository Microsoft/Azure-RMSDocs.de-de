---
title: Schnellstarttutorial Schritt 5 | Azure Information Protection
description: "Schritt 5 eines Einführungstutorials, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in ungefähr 30 Minuten für Ihre Organisation testen können."
keywords: 
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/22/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4e59a3b3-f0f4-4535-8b96-cac68303d855
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0a79642c3707be4c8dd75ccc80569ba90da01236
ms.openlocfilehash: b8b973766852fcace6e070e73fa87072ad4b3524


---


# <a name="step-5-see-sharing-of-protected-files-in-action-and-track-your-document"></a>Schritt 5: Freigeben geschützter Dateien in Aktion und Nachverfolgen des Dokuments 

>*Gilt für: Azure Information Protection*

Verwenden Sie für diesen letzten Schritt des Tutorials ein Word-Dokument, das Sie bereits erstellt haben und an einen Partner oder Kollegen senden möchten. In diesem Tutorial spielt der enthaltene Text keine Rolle. Etwas Text ist jedoch sinnvoll, damit Sie einfacher überprüfen können, ob der Inhalt vom autorisierten Empfänger gelesen werden kann.

Anschließend können Sie das Dokument sicher per E-Mail freigeben. 

## <a name="to-safely-share-your-document-by-email"></a>So geben Sie Ihr Dokument sicher per E-Mail frei

1.  Öffnen Sie das Dokument in Word. Sie können sehen, dass die Standardbezeichnung **Internal** (Intern) wieder automatisch angewendet wurde. 

2.  Klicken Sie auf der Registerkarte **Start** in der Gruppe **RMS** auf **Geschützt freigeben** und dann im Menü auf **Geschützt freigeben**:

    ![Schnellstarttutorial für Azure Information Protection Schritt 5 – Geschützt freigeben](../media/share-protected-callout.png)

    Das Dialogfeld **Geschützt freigeben** wird angezeigt (ähnelt der folgenden Abbildung):

    ![Schnellstarttutorial für Azure Information Protection Schritt 5 – Dialogfeld „Geschützt freigeben“](../media/example-share-protected-dialog.png)

3. Geben Sie im Feld **BENUTZER** eine oder mehrere geschäftliche E-Mail-Adressen ein, wie um ein Dokument an einen Geschäftspartner Ihrer Organisation zu senden. Sie können auch die E-Mail-Adresse eines Kollegen angeben. Sie müssen eine geschäftliche E-Mail-Adresse wie **janetm@contoso.com** oder **p.dover@fabrikam.com** angeben, weil Azure Information Protection momentan keine privaten E-Mail-Adressen unterstützt. 

    Es spielt keine Rolle, ob der Empfänger über Azure Information Protection verfügt oder nicht.

4. Wählen Sie **Anzeigender Benutzer - Nur anzeigen**.

    Dies bedeutet, dass die Empfänger das Dokument anzeigen, jedoch nicht bearbeiten oder ausdrucken können.

5. Wählen Sie **E-Mail an mich bei Öffnungsversuchen dieser Dokumente durch andere Benutzer**.

    Sie erhalten jedes Mal eine E-Mail-Benachrichtigung, wenn der Empfänger oder eine andere Person (falls der Empfänger die E-Mail an einen Kollegen weiterleitet) versucht, das Dokument zu öffnen. Wenn das Dokument weitergeleitet wird, können Sie sehen, dass der Zugriff verweigert wurde. Sie können dann anhand der Benutzerdetails entscheiden, ob Sie dieser Person eine Kopie des Dokuments zum Öffnen senden möchten.

6. Wählen Sie **Sofortigen Widerruf des Zugriffs auf diese Dokumente zulassen**.

    Bei dieser Option muss der Empfänger bei jedem Öffnen der Anlage mit dem Internet verbunden sein. Das hat für den Absender den Vorteil, dass ein nachträglich widerrufenes Dokument beim nächsten Mal nicht mehr geöffnet werden kann. 

4.  Wenn Sie auf **Senden** klicken, wird eine E-Mail-Nachricht angezeigt, die an die angegebenen Empfänger gesendet werden kann und den Standardtext der Anweisungen enthält. Beispiel:

    ![Beispiel für E-Mail-Nachricht bei geschützter Freigabe](../media/example-email-share-protected.png)
    
    **HINWEIS:** Wenn Outlook bei der Installation des Azure Information Protection-Clients geöffnet war, wird die Information Protection-Leiste nicht angezeigt, die in der vorherigen Abbildung zu sehen ist. In diesem Schritt zur Veranschaulichung der Freigabe geschützter Dateien wird diese Leiste nicht speziell verwendet. Daher müssen Sie Outlook für dieses Tutorial nicht schließen und wieder öffnen. Wenn Sie Outlook nach der Installation des Azure Information Protection-Clients geöffnet haben, können Sie sehen, dass diese E-Mail-Nachricht, wie das Word-Dokument beim ersten Öffnen, standardmäßig mit der Bezeichnung **Internal** (Intern) angezeigt wird, da diese globale Einstellung in der Azure Information Protection-Richtlinie konfiguriert wurde.
    
    Sie werden feststellen, dass die E-Mail zwei Anlagen umfasst: das Word-Originaldokument und eine Datei mit demselben Namen, jedoch mit der Dateierweiterung **.ppdf**. Die PPDF-Version ist eine geschützte PDF-Datei, die in der Rights Management-Freigabeanwendung automatisch erstellt wird, für den Fall, dass der Empfänger nicht über eine Version von Office verfügt, in der geschützte Dokumente unterstützt werden. Durch diese zusätzliche Datei kann der Empfänger das geschützte Dokument mit dem Viewer lesen, der mit der Rights Management-Freigabeanwendung installiert wird.

    Klicken Sie in der E-Mail-Nachricht auf **Senden**.

Nachdem Sie Ihr geschütztes Dokument nun gesendet haben, bitten Sie die Empfänger, das Dokument anzunehmen und zu öffnen. Word sollte zu diesem Zeitpunkt nicht geschlossen werden, da die Anwendung beim letzten Vorgang zum Nachverfolgen des freigegebenen Dokuments noch benötigt wird.

## <a name="ask-your-recipients-to-open-the-emailed-document"></a>Bitten Sie die Empfänger, das E-Mail-Dokument zu öffnen.

Die Empfänger können das als E-Mail-Anlage gesendete, geschützte Dokument auf verschiedenen Geräten lesen. Die Geräte umfassen iPads, iPhones, Android-Tablets und -Smartphones sowie Macintosh- und Windows-Computer.

Bitten Sie die Empfänger, die gesendete E-Mail zu lesen. In der Annahme, dass diese zum ersten Mal Anlagen erhalten haben, die durch Rights Management geschützt sind, bitten Sie sie, auf den Link für die Anweisungen zu klicken. Dadurch gelangen die Empfänger zur Seite [Willkommen bei Microsoft RMS!](https://portal.azurerms.com/#/rmshelp), die Anweisungen zur Installation der RMS-Freigabeanwendung und gegebenenfalls zur Registrierung für ein kostenloses Konto enthält. Die Empfänger können dann die geschützte Anlage lesen.

### <a name="instructions-for-recipient-to-view-the-protected-document-attachment"></a>Anweisungen für Empfänger: So zeigen Sie die Anlage mit dem geschützten Dokument an

1. Öffnen Sie eine der Anlagen, um das Dokument zu lesen:
    
    - Wenn Sie eine Version von Office auf Ihrem Gerät installiert haben, die Rights Management unterstützt:
    
        -  Öffnen Sie das Dokument mit der Dateierweiterung **.docx**.
        
    - Wenn Sie keine Version von Office installiert haben, die Rights Management unterstützt, wenn Sie sich nicht sicher sind, oder wenn Sie einfach nur den Viewer der Rights Management-Freigabeanwendung testen möchten: 
    
        - Öffnen Sie das Dokument mit der Dateierweiterung **.ppdf**.

2.  Wenn Sie zur Eingabe von Benutzernamen und Kennwort aufgefordert werden, geben Sie Ihren Benutzernamen im gleichen Format wie die E-Mail-Adresse ein, die Sie zum Senden der E-Mail und der Anlage verwendet haben. Beispiel: **janetm@contoso.com** oder **p.dover@fabrikam.com**. Geben Sie das Kennwort ein, das Sie beim Registrieren von RMS for Individuals erhalten haben. Wenn Ihre Organisation über einen Clouddienst wie Office 365 verfügt oder Azure verwendet, geben Sie Ihr übliches Arbeitskennwort ein.

3. Nach dem Öffnen können Sie den Inhalt des Dokuments lesen. Da der Inhalt schreibgeschützt ist, können Sie ihn nicht ändern.

Als optionalen Schritt kann der Empfänger die E-Mail an andere Personen weiterleiten, die Sie in der ursprünglichen E-Mail nicht angegeben haben. Diese Personen können die Anlage nicht öffnen. Bei der Aufforderung zur Eingabe des Benutzernamens wird den Empfängern der Zugriff verweigert.

Nachdem der Empfänger die Anlage nun geöffnet und optional an einen anderen Empfänger weitergeleitet hat, erhalten Sie eine E-Mail-Benachrichtigung über die jeweiligen Aktivitäten. Da E-Mails jedoch leicht in Vergessenheit geraten, lassen sich Dokumentzugriffe einfacher über die Website zur Dokumentenverfolgung überwachen. Dies wird im letzten Vorgang veranschaulicht.

## <a name="to-track-your-protected-document"></a>So verfolgen Sie das geschützte Dokument

1.  Klicken Sie in Word auf der Registerkarte **Start** in der Gruppe **RMS** auf **Geschützt freigeben** und dann im Menü auf **Verwendung nachverfolgen**:

    ![Option „Verwendung nachverfolgen“](../media/track-usage-callout.png)

    Dadurch gelangen Sie zu der Website für die Dokumentennachverfolgung.

2.  Wenn die Seite **Schutz und Freigabe nach Ihren Vorgaben** angezeigt wird, klicken Sie auf **Anmelden** und geben Benutzernamen und Kennwort erneut ein.

3.  Auf der Seite **Your shared documents** (Freigegebene Dokumente) wird der Name des freigegebenen Dokuments angezeigt. Zu diesem Zeitpunkt wird nur diese Datei angezeigt. Sobald Sie jedoch zusätzliche geschützte Dokumente freigeben, wird die Liste erweitert.

    Auf dieser Seite sehen Sie, wann Sie das Dokument freigegeben (d. h. die E-Mail mit dem geschützten Anhang versendet) haben, sowie das Datum der letzten Aktivität und den Namen des Empfängers der E-Mail. Klicken Sie auf den Dokumentnamen, um weitere Details zu sehen.

4.  Auf der neuen Seite, die den Namen der angeklickten Datei hat, sehen Sie spezifische Übersichtsdetails für das Dokument und eine Liste weiterer Optionen, die für das Dokument verfügbar sind (**Liste**, **Zeitskala**, **Karte**, **Einstellungen**).

    Klicken Sie auf die einzelnen Optionen, um verschiedene Möglichkeiten zum Verfolgen des geschützten Dokuments auszuprobieren. Sie können auf der Seite **Zusammenfassung** aber auch auf **In Excel öffnen** klicken, um die Informationen in eine Kalkulationstabelle zu exportieren, oder auf **Zugriff widerrufen** , um die Freigabe des Dokuments zu beenden.

Sie können zu dieser Website zurückkehren, um weitere Aktivitäten für das geschützte Dokument zu verfolgen oder um den Zugriff ggf. zu widerrufen. Sie können auch von Ihrem mobilen Gerät oder Tablet auf die Website zugreifen, indem Sie den Browserlink [Dokumentenverfolgung](http://go.microsoft.com/fwlink/?LinkId=529562)auswählen.



|Weitere Informationen zu|Weitere Informationen|
|--------------------------------|--------------------------|
|Umfassende Anweisungen und alternative Methoden zum Schutz der per E-Mail freigegebenen Dateien|[Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung](../rms-client/sharing-app-protect-by-email.md)|
|Optionen im Dialogfeld **Geschützt freigeben**|[Dialogfeldoptionen der Rights Management-Freigabeanwendung](../rms-client/sharing-app-dialog-box.md)|
|Informationen zum kostenlosen Konto, für das sich andere Benutzer registrieren können|[RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md)|
|Verwenden der Website zur Dokumentennachverfolgung|[Nachverfolgen und Widerrufen Ihrer Dokumente](../rms-client/sharing-app-track-revoke.md)


## <a name="next-steps"></a>Nächste Schritte

Nun, da Sie die standardmäßige Azure Information Protection-Richtlinie gesehen haben, und jetzt wissen, wie Sie sie anpassen können und wie das Bezeichnen in einem Word-Dokument funktioniert, testen Sie doch einige der anderen Einstellungen und lernen Sie die Funktionsweise der Office-Apps kennen, die Azure Information Protection verwenden: Excel, PowerPoint, Outlook. Falls diese Anwendungen geöffnet waren, als Sie den Azure Information Protection-Client installiert haben, schließen Sie sie, und öffnen Sie sie erneut, bevor Sie sie mit Azure Information Protection verwenden.

Geben Sie weitere Dokumente frei, und verfolgen Sie deren Verwendung. Testen Sie auch den Widerruf von Dokumenten.

Es empfiehlt sich zudem, einige der [häufig gestellten Fragen](faqs.md) zu Azure Information Protection sowie einige andere Artikel der Dokumentation zu lesen. Wenn Sie mit der Bereitstellung von Azure Information Protection für Ihre Organisation beginnen möchten, sollte Ihre nächste Station die [Roadmap für die Bereitstellung von Azure Information Protection](../plan-design/deployment-roadmap.md) sein. 


<!--HONumber=Nov16_HO4-->


