---
title: "Szenario – Freigeben einer Office-Datei für Benutzer in einer anderen Organisation | Azure RMS"
description: "In diesem Szenario und der begleitenden Benutzerdokumentation wird Azure Rights Management verwendet, damit Benutzer eine Office-Datei auf sichere Weise an Personen in einer anderen Organisation senden können."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 26e81330c58057aac9629690f1d4fe85e56a64f8


---

# Szenario – Freigeben einer Office-Datei für Benutzer in einer anderen Organisation

>*Gilt für: Azure Rights Management, Office 365*

In diesem Szenario und der begleitenden Benutzerdokumentation wird Azure Rights Management verwendet, damit Benutzer eine Office-Datei auf sichere Weise an Personen in einer anderen Organisation senden können. Eine Office-Datei kann z.B. ein Word-Dokument, eine Excel-Tabelle oder eine PowerPoint-Präsentation sein, die Preislisteninformationen für einen Partner, eine Liste mit Produkten für einen Händler oder eine Liste mit Bereitstellungsfristen für potenzielle Kunden enthält. Wenn der Benutzer die Anweisungen befolgt, wird die in der E-Mail-Nachricht angefügte Datei durch Azure Rights Management geschützt.

Dieses Szenario eignet sich für folgende Fälle:

-   Der Mitarbeiter muss Informationen in Form eines Office-Dokuments als E-Mail-Anlage an Personen außerhalb der Organisation verschicken.

-   Das Dokument enthält Informationen, die nicht öffentlich sind, aber auch nicht ausschließlich intern verwendet werden.

-   Die Benutzer auf der Empfangsseite haben nicht die Anforderung, die Informationen an weitere Benutzer freizugeben, sie zu drucken, oder als Teil ihrer eigenen Dokumentation zu verwenden. Wenn dies nicht der Fall ist, können Sie die Benutzeranweisungen ändern, indem Sie die Berechtigungen von „Nur anzeigen“ auf eine andere Option ändern, mit der der Empfänger die Anlage ändern kann.

-   Der Mitarbeiter möchte unter Umständen wissen, wann dieses Dokument von einem externen Benutzer geöffnet wird.

## Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, bevor Sie mit der Benutzerdokumentation fortfahren.

## Anforderungen bei diesem Szenario
Damit die Benutzeranweisungen in diesem Szenarion funktionieren, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Sie haben Konten und Gruppen für Office 365 oder Azure Active Directory vorbereitet.|[Vorbereiten für Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Die Rights Management-Freigabeanwendung wird auf Benutzercomputern bereitgestellt, auf denen Windows ausgeführt wird.|[Automatische Bereitstellung für die Microsoft Rights Management-Freigabeanwendung.](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|Benutzer verwenden Outlook aus Office 2013.|Wenn Benutzer Office 2010 haben, ersetzen Sie den Screenshot mit einer entsprechenden Version, damit die Ansicht das zeigt, was Benutzer sehen.|
|Ihr Azure RMS-Abonnement umfasst die Dokumentnachverfolgung.|Wenn Sie Ihr Abonnement für Azure RMS keine Nachverfolgung und keinen Widerruf von Dokumenten umfasst, können Benutzer nicht alle Schritte in den Benutzeranweisungen ausführen. Erwerben Sie in diesem Fall entweder ein Abonnement, das diese Funktionen unterstützt, oder ändern die Benutzeranweisungen som dass die Schritte entfernt werden, die diese Funktionen verwenden.<br /><br />So überprüfen Sie Ihren Abonnementsupport: [Vergleich der Rights Management Services(RMS)-Angebote](https://technet.microsoft.com/dn858608)|

## Anweisungen für Benutzerdokumentation
Verwenden Sie die folgende Vorlage, kopieren Sie die Benutzeranweisungen, und fügen Sie sie in eine Nachricht für die Endbenutzer ein. Nehmen Sie als Anpassung an Ihre Umgebung die folgenden Änderungen vor:

1.  Ersetzen Sie *&lt;Name des Office-Dokumenttyps&gt;* durch den Dokumenttyp, der von Ihren Benutzern gesendet wird. Verwenden Sie anstelle von "Word-Dokument" oder "Excel-Tabelle" Formulierungen, die konkret sind und sich auf die Workflows beziehen, wie z. B. "Preisliste", "Lieferzeiten" und "Angebot erstellen". Mit dieser präziseren Wortwahl wird die Wahrscheinlichkeit erhöht, dass beim Verwenden der Dokumente die Anweisungen befolgt werden.

2.  Ersetzen Sie die *&lt;Kontaktdetails&gt;* durch Anweisungen dazu, wie sich Benutzer an das Helpdesk wenden können, z.B. über einen Link zur Website, eine E-Mail-Adresse oder eine Telefonnummer.

3.  **Zudem können Sie folgende Änderungen vornehmen:**

    -   Bei Schritt 2 empfehlen wir, die Berechtigung **Anzeigender Benutzer – Nur anzeigen** einzustellen, wodurch das angefügte Dokument (jedoch nicht das Original) für Empfänger schreibgeschützt ist. Wenn diese Einschränkung nicht für Ihre geschäftlichen Anforderungen geeignet ist, ändern Sie die Option auf einen anderen Berechtigungssatz, wie z. B. **Prüfer – Anzeigen und Bearbeiten**.

    -   In Schritt 3 empfehlen wir die Berechtigung **Zulassen, dass ich den Zugriff auf diese Dokumente sofort widerrufe** , sodass es keine Verzögerung gibt, wenn Ihre Benutzer das Dokument später widerrufen. Allerdings erfordert diese Option, dass der Empfänger stets über eine Internetverbindung verfügt, um die Anlage zu öffnen. Für diesen Schritt benötigen Sie außerdem ein Abonnement, das die Nachverfolgung und den Widerruf von Dokumenten unterstützt. Löschen Sie diesen Schritt, wenn er nicht für Ihre Benutzer geeignet ist.

    -   In Schritt 4 empfehlen wir die Option **E-Mail verschicken, sobald jemand dieses Dokument öffnet**. Wenn Benutzer ihre Dokumente mithilfe des Portals für die Dokumentennachverfolgung im Auge behalten möchten, sind E-Mail-Benachrichtigungen möglicherweise nicht erforderlich, und Sie können diesen Schritt löschen.

    -   Die Schritte beinhalten nicht das Festlegen eines Ablaufdatums. Falls die Informationen nach einem bestimmten Datum nicht mehr verwendet werden sollen, können Sie einen weiteren Schritt zum Festlegen eines geeigneten Ablaufzeitpunkts hinzufügen, z.B. 90 Tage nach dem Senden der E-Mail.

    > [!NOTE]
    > Weitere Informationen zu den einzelnen Optionen, die Benutzer auswählen können, finden Sie unter [Optionen des Dialogfelds für die Rights Management-Freigabeanwendung](https://technet.microsoft.com/library/dn574738.aspx).

4.  Nehmen Sie jegliche sonstigen Änderungen an den Anweisungen vor, und senden Sie sie an diese Benutzer.

Die Beispieldokumentation veranschaulicht, wie diese Anweisungen für Benutzer nach Ihren Anpassungen aussehen können.

![Benutzerdokumentationsvorlage für die Azure RMS-Schnellbereitstellung](../media/AzRMS_UsersBanner.png)

### So geben Sie den &lt;Namen des Office-Dokumenttyps frei&gt;

1.  Erstellen Sie Ihre E-Mail-Nachricht durch Angabe der E-Mail-Adresse oder -Adressen, geben Sie Ihre Nachricht ein, und fügen Sie den *&lt;Namen des Office-Dokumenttyps&gt;* an. Klicken Sie dann auf der Registerkarte **NACHRICHT** in der Gruppe **RMS** auf **Geschützt freigeben** , und klicken Sie dann erneut auf **Geschützt freigeben** :

    ![Ein Screenshot, der anzeigt, wie ein Office-Dokument mithilfe von Outlook freigegeben wird](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  Wählen Sie im Dialogfeld **Geschützt freigeben** **Anzeigender Benutzer – Nur Anzeigen**:

    ![Dialogfeld „Geschützt freigeben“ –„Viewer“ – „Nur Anzeigen“](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Wählen Sie **Zulassen, dass ich den Zugriff auf diese Dokumente sofort widerrufe**aus.

    ![Dialogfeld „Geschützt freigeben“ – sofort wiederrufen](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Wählen Sie **E-Mail verschicken, sobald jemand diese Dokumente öffnet**:

    ![Dialogfeld „Geschützt freigeben“ – E-Mail an mich senden](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  Klicken Sie auf **Jetzt senden**.

Wenn ein Empfänger der Zeilen **An**, **Cc** oder **Bcc** diese E-Mail erhält, erscheint eine Nachricht mit Anweisungen, wie der angefügte *&lt;Name des Office-Dokumenttyps&gt;* gelesen werden kann. Die Person kann das Dokument auf vielen Geräten lesen, einschließlich iPads, iPhones, Android-Tablets und -Telefonen, Mac- und Windows-Computern.

Nutzen Sie das [Portal für die Dokumentennachverfolgung](https://track.azurerms.com/), um zu prüfen, ob und wann der angefügte &lt;Name des Office-Dokumenttyps&gt; geöffnet wird. Sie können mit einem Telefonanruf bei der Person nachfassen, sobald Sie feststellen, dass diese den &lt;Namen des Office-Dokumenttyps&gt; geöffnet hat.

**Benötigen Sie Unterstützung?**

-   Zusätzliche Informationen:

    -   [Schützen einer Datei, die per E-Mail freigegeben ist](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Verfolgen und Widerrufen von Dokumenten](https://technet.microsoft.com/library/dn986611.aspx)

-   Wenden Sie sich an den Helpdesk:

    -   *&lt;Kontaktinformationen&gt;*

### Beispiel für eine angepasste Benutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

#### Vorgehensweise bei der Freigabe einer Preisliste für den Kunden

1.  Erstellen Sie Ihre E-Mail-Nachricht durch Angabe der E-Mail-Adresse oder -Adressen des Kunden, geben Sie Ihre Nachricht ein, und fügen Sie die aktuelle Preisliste an. Klicken Sie dann auf der Registerkarte **NACHRICHT** in der Gruppe **RMS** auf **Geschützt freigeben** , und klicken Sie dann erneut auf **Geschützt freigeben** :

    ![Ein Screenshot, der anzeigt, wie ein Office-Dokument mithilfe von Outlook freigegeben wird](../media/AzRMSUserInstructions_ShareProtectedRibbon2013.png)

2.  Wählen Sie im Dialogfeld **Geschützt freigeben** **Anzeigender Benutzer – Nur Anzeigen**:

    ![Dialogfeld „Geschützt freigeben“ –„Viewer“ – „Nur Anzeigen“](../media/AzRMS_SharedProtected_ViewerOnly.PNG)

3.  Wählen Sie **Zulassen, dass ich den Zugriff auf diese Dokumente sofort widerrufe**aus.

    ![Dialogfeld „Geschützt freigeben“ – sofort wiederrufen](../media/AzRMS_SharedProtected_InstantRevoke.PNG)

4.  Wählen Sie **E-Mail verschicken, sobald jemand diese Dokumente öffnet**:

    ![Dialogfeld „Geschützt freigeben“ – E-Mail an mich senden](../media/AzRMS_SharedProtected_EmailMe.PNG)

5.  Klicken Sie auf **Jetzt senden**.

Wenn ein Empfänger der Zeilen **An**, **Cc**oder **Bcc** diese E-Mail erhält, erscheint eine Nachricht mit Anweisungen, wie die angefügte Preisliste gelesen werden kann. Die Person kann das Dokument auf vielen Geräten lesen, einschließlich iPads, iPhones, Android-Tablets und -Telefonen, Mac- und Windows-Computern.

Nutzen Sie das [Portal für die Dokumentennachverfolgung](https://track.azurerms.com/) , um zu prüfen, ob und wann die angefügte Preisliste geöffnet wurde. Sie können mit einem Telefonanruf bei der Person nachfassen, sobald Sie feststellen, dass diese die Preisliste geöffnet hat.

**Benötigen Sie Unterstützung?**

-   Zusätzliche Informationen:

    -   [Schützen einer Datei, die per E-Mail freigegeben ist](https://technet.microsoft.com/library/dn574735%28v=ws.10%29.aspx)

    -   [Verfolgen und Widerrufen von Dokumenten](https://technet.microsoft.com/library/dn986611.aspx)

-   Wenden Sie sich an den Helpdesk:

    -   E-Mail: helpdesk@vanarsdelltd.com




<!--HONumber=Aug16_HO4-->


