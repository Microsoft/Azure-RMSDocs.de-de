---
title: "Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung | Azure Information Protection"
description: Anweisungen zur sicheren Freigabe eines Dokuments per E-Mail.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/04/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4c1cd1d3-78dd-4f90-8b37-dcc9205a6736
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 7b8fe306b82e0eb964106b3ab3b890d1a115037d


---

# <a name="protect-a-file-that-you-share-by-email-by-using-the-rights-management-sharing-application"></a>Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Wenn Sie eine Datei schützen, die Sie per E-Mail freigeben, wird eine neue Version der ursprünglichen Datei erstellt. Die ursprüngliche Datei bleibt ungeschützt und die neue Version ist geschützt und wird automatisch an die E-Mail-Nachricht angefügt, die Sie senden.

In einigen Fällen (für Dateien, die mit Microsoft Word, Excel und PowerPoint erstellt wurden) erstellt die RMS-Freigabeanwendung zwei Versionen der Datei, die an die E-Mail-Nachricht angefügt wird. Die zweite Version der Datei hat die Dateierweiterung **.ppdf** und ist eine PDF-Schattenkopie der Datei. Diese Version der Datei sorgt dafür, dass Empfänger die Datei immer lesen können, selbst wenn sie nicht die gleiche Anwendung installiert haben, mit der Sie die Datei erstellt haben. Dies ist häufig der Fall, wenn Mitarbeiter ihre E-Mails auf mobilen Geräten lesen und ihre E-Mail-Anlagen angezeigt werden sollen. Zum Öffnen wird lediglich die RMS-Freigabeanwendung benötigt. Dann können sie die angefügte Datei lesen, aber nicht bearbeiten, solange sie nicht die andere Version der Datei mit einer Anwendung öffnen, die einen Rights Management-Dienst unterstützt.

Wenn Ihr Unternehmen Azure Information Protection verwendet, können Sie die Dateien nachverfolgen, die Sie durch die Freigabe schützen:

-   Wählen Sie eine Option aus, um E-Mails zu erhalten, wenn jemand versucht, diese geschützten Anlagen zu öffnen. Jedes Mal, wenn auf die Datei zugegriffen wird, werden Sie benachrichtigt, wer wann versucht hat, die Datei zu öffnen, und ob der Vorgang erfolgreich war (sich der Benutzer erfolgreich authentifiziert hat).

-   Verwenden Sie die Website für die Dokumentationsbestandsverfolgung. Sie können die Freigabe der Datei auch Aufheben, indem Sie den Zugriff darauf auf der Website "Dokumentenbestandsverfolgung" zurückziehen. Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](sharing-app-track-revoke.md).

## <a name="using-outlook-to-protect-a-file-that-you-share-by-email"></a>Mit Outlook: So schützen Sie eine per E-Mail freigegebene Datei

1.  Erstellen Sie Ihre E-Mail-Nachricht, und fügen Sie die Datei an. Klicken Sie dann auf der Registerkarte **Nachricht** in der Gruppe **RMS** auf **Geschützt freigeben** und dann erneut auf **Geschützt freigeben** :

    ![Outlook-Add-In für die RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_SP_OutlookToolbar.png)

    Wenn diese Schaltfläche nicht angezeigt wird, hat dies wahrscheinlich einen der folgenden Gründe: die RMS-Freigabeanwendung oder die neuste Version davon ist nicht auf Ihrem Computer installiert oder Ihr Computer muss neu gestartet werden, um die Installation abzuschließen. Weitere Informationen zum Installieren der Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

2.  Geben Sie die gewünschten Optionen im [Dialogfeld „Geschützt freigeben“](sharing-app-dialog-box.md) an, und klicken Sie dann auf **Jetzt senden**.

### <a name="other-ways-to-protect-a-file-that-you-share-by-email"></a>Andere Möglichkeiten zum Schützen einer per E-Mail freigegebenen Datei
Sie können eine geschützte Datei nicht nur mit Outlook freigeben. Zusätzlich stehen Ihnen folgende Möglichkeiten zur Verfügung:

-   Datei-Explorer: Diese Methode funktioniert für alle Dateien.

-   In einer Office-Anwendung: Diese Methode funktioniert in Anwendungen, die von der RMS-Freigabeanwendung unterstützt werden. Sie müssen hierfür das Office-Add-In verwenden, das Sie im Menüband in der Gruppe **RMS** enthalten ist.

#### <a name="using-file-explorer-or-an-office-application-to-protect-a-file-that-you-share-by-email"></a>Mit Datei-Explorer oder einer Office-Anwendung: So schützen Sie eine per E-Mail freigegebene Datei

1.  Verwenden Sie eine der folgenden Optionen:

    -   Datei-Explorer: Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Mit RMS schützen** und dann **Geschützt freigeben** aus:

        ![Menüoption „Geschützt freigeben“](../media/ADRMS_MSRMSApp_ShareProtectedMenu.png)

    -   Office-Anwendungen Word, Excel und PowerPoint: Stellen Sie sicher, dass Sie die Datei zuerst gespeichert haben. Klicken Sie dann auf der Registerkarte **Start** in der Gruppe **RMS** auf **Geschützt freigeben** , und klicken Sie dann erneut auf **Geschützt freigeben** :

        ![Office-Symbolleisten-Add-In](../media/ADRMS_MSRMSApp_SP_OfficeToolbar.png)

    Wenn diese Optionen zum Schutz nicht angezeigt werden, hat dies wahrscheinlich einen der folgenden Gründe: die RMS-Freigabeanwendung oder die neuste Version davon ist nicht auf Ihrem Computer installiert oder Ihr Computer muss neu gestartet werden, um die Installation abzuschließen. Weitere Informationen zum Installieren der Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

2.  Geben Sie die gewünschten Optionen für diese Datei im [Dialogfeld „Geschützt freigeben“](sharing-app-dialog-box.md) an, und klicken Sie dann auf **Senden**.

3.  Möglicherweise sehen Sie kurzzeitig ein Dialogfeld, in dem der Dateischutz bestätigt wird, und dann sehen Sie eine automatisch erstellten E-Mail-Nachricht, die den Empfänger über den Schutz der Anlagen mit Microsoft RMS benachrichtigt und ihn dazu auffordert, sich anzumelden. Wenn der Benutzer auf dem Link zur Anmeldung klickt, werden ihm Anweisungen und Links angezeigt, die ihm beim Öffnen des geschützten Anhangs helfen.

    Beispiel:

    ![E-Mail-Nachricht für Azure Information Protection](../media/ADRMS_MSRMSApp_EmailMessage.PNG)

    Möglicherweise wünschen Sie sich eine [Erläuterung zur automatisch erstellten PPDF-Datei](sharing-app-dialog-box.md#whats-the-ppdf-file-thats-automatically-created).

4.  Optional: Sie können beliebige Änderungen an der E-Mail-Nachricht vornehmen. Sie können z. B. einen Betreff oder Nachrichtentext hinzufügen oder ändern.

    > [!WARNING]
    > Obwohl Sie Personen hinzufügen oder entfernen können, hat dies keinerlei Auswirkungen auf die Berechtigungen für den Anhang, die im Dialogfeld **Geschützt freigeben** angegeben haben. Wenn Sie diese Berechtigungen ändern möchten (z. B. einer anderen Person Berechtigungen zum Öffnen der Datei erteilen möchten), schließen Sie die E-Mail-Nachricht ohne sie zu speichern oder zu senden, und kehren Sie zu Schritt 1 zurück.

5.  Senden Sie die E-Mail-Nachricht.

## <a name="examples-and-other-instructions"></a>Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Siehe auch
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


