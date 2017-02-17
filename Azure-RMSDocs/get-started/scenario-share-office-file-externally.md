---
title: "Szenario – Freigeben einer Office-Datei für Benutzer in einer anderen Organisation | Azure Information Protection"
description: "In diesem Szenario und der unterstützenden Benutzerdokumentation wird der Azure Rights Management-Schutz verwendet, damit Benutzer eine Office-Datei auf sichere Weise an Personen in einer anderen Organisation senden können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c10a4d7b-f57a-4a43-b66e-477777be59cc
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: f4dbd60aef69ba9ce83101004c508c162cb3f918


---

# <a name="scenario---share-an-office-file-with-users-in-another-organization"></a>Szenario – Freigeben einer Office-Datei für Benutzer in einer anderen Organisation

>*Gilt für: Azure Information Protection, Office 365*

In diesem Szenario und der unterstützenden Benutzerdokumentation wird die Azure Rights Management-Technologie von Azure Information Protection verwendet, damit Benutzer eine Office-Datei auf sichere Weise an Personen in einer anderen Organisation senden können. Eine Office-Datei kann z.B. ein Word-Dokument, eine Excel-Tabelle oder eine PowerPoint-Präsentation sein, die Preislisteninformationen für einen Partner, eine Liste mit Produkten für einen Händler oder eine Liste mit Bereitstellungsfristen für potenzielle Kunden enthält. Wenn der Benutzer die Anweisungen befolgt, wird die in der E-Mail-Nachricht angefügte Datei durch Azure Rights Management geschützt.

Dieses Szenario eignet sich für folgende Fälle:

-   Der Mitarbeiter muss Informationen in Form eines Office-Dokuments als E-Mail-Anlage an Personen außerhalb der Organisation verschicken.

-   Das Dokument enthält Informationen, die nicht öffentlich sind, aber auch nicht ausschließlich intern verwendet werden.

-   Die Benutzer auf der Empfangsseite haben nicht die Anforderung, die Informationen an weitere Benutzer freizugeben, sie zu drucken, oder als Teil ihrer eigenen Dokumentation zu verwenden. Wenn dies nicht der Fall ist, können Sie die Benutzeranweisungen ändern, indem Sie die Berechtigungen von „Nur anzeigen“ auf eine andere Option ändern, mit der der Empfänger die Anlage ändern kann.

-   Der Mitarbeiter möchte unter Umständen wissen, wann dieses Dokument von einem externen Benutzer geöffnet wird.

## <a name="deployment-instructions"></a>Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, bevor Sie mit der Benutzerdokumentation fortfahren.

## <a name="requirements-for-this-scenario"></a>Anforderungen bei diesem Szenario
Damit die Benutzeranweisungen in diesem Szenarion funktionieren, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Sie haben Konten und Gruppen für Office 365 oder Azure Active Directory vorbereitet.|[Vorbereiten für Azure Information Protection](https://technet.microsoft.com/library/jj585029.aspx)|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Die Rights Management-Freigabeanwendung wird auf Benutzercomputern bereitgestellt, auf denen Windows ausgeführt wird.|[Automatische Bereitstellung für die Microsoft Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application)|
|Benutzer verwenden Outlook aus Office 2013.|Wenn Benutzer Office 2016 oder Office 2010 verwenden, ersetzen Sie den Screenshot durch eine entsprechende Version, sodass die Abbildung mit der Version der Benutzer übereinstimmt.|
|Ihr Abonnement für Azure Information Protection umfasst die Dokumentkontrolle.|Wenn Ihr Abonnement keine Dokumentkontrolle und keinen Widerruf von Dokumenten umfasst, können Benutzer nicht alle Schritte in den Benutzeranweisungen ausführen. Erwerben Sie in diesem Fall entweder ein Abonnement, das diese Funktionen unterstützt, oder ändern die Benutzeranweisungen som dass die Schritte entfernt werden, die diese Funktionen verwenden.<br /><br />Überprüfen Sie die [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website.|

## <a name="user-documentation-instructions"></a>Anweisungen für Benutzerdokumentation
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

### <a name="how-to-share-a-ltname-of-office-document-typegt"></a>So geben Sie den &lt;Namen des Office-Dokumenttyps&gt;frei

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

    -   [Schützen einer Datei, die per E-Mail freigegeben ist](../rms-client/sharing-app-protect-by-email.md)

    -   [Nachverfolgen und Widerrufen Ihrer Dokumente](../rms-client/sharing-app-track-revoke.md)

-   Wenden Sie sich an den Helpdesk:

    -   *&lt;Kontaktinformationen&gt;*

### <a name="example-customized-user-documentation"></a>Beispiel für eine angepasste Benutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

#### <a name="how-to-share-a-price-list-with-your-customer"></a>Vorgehensweise bei der Freigabe einer Preisliste für den Kunden

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

    -   [Schützen einer Datei, die per E-Mail freigegeben ist](../rms-client/sharing-app-protect-by-email.md)

    -   [Nachverfolgen und Widerrufen Ihrer Dokumente](../rms-client/sharing-app-track-revoke.md)

-   Wenden Sie sich an den Helpdesk:

    -   E-Mail: helpdesk@vanarsdelltd.com

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


