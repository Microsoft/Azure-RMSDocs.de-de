---
title: "Szenario – Beibehalten der Kontrolle über in SharePoint gespeicherte Dokumente | Azure Information Protection"
description: "In diesem Szenario und der unterstützenden Benutzerdokumentation wird der Azure Rights Management-Schutz verwendet, um sicherzustellen, dass in SharePoint gespeicherte Office-Dokumente mithilfe geschützter Bibliotheken unter Ihrer Kontrolle bleiben."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1b6244c7-5ab9-4881-bc8f-6fa960390d89
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 371e566a166dad74b55266db23e034f926942a26


---

# <a name="scenario-retain-control-of-documents-stored-in-sharepoint"></a>Szenario – Beibehalten der Kontrolle über in SharePoint gespeicherte Dokumente

>*Gilt für: Azure Information Protection, Office 365*

In diesem Szenario und der unterstützenden Benutzerdokumentation wird die Azure Rights Management-Technologie von Azure Information Protection verwendet, um sicherzustellen, dass in SharePoint gespeicherte Office-Dokumente mithilfe geschützter Bibliotheken unter Ihrer Kontrolle bleiben. Die Dokumente werden beispielsweise automatisch vor durch Benutzer versehentlich oder beabsichtigt verursachte Datenlecks geschützt, und Sie können den Zugriff auf Inhalte blockieren, auch nachdem sie heruntergeladen oder synchronisiert wurden. Die Dateien, die Sie schützen möchten, dienen möglicherweise der internen Zusammenarbeit an Entwurfsdokumenten, Plänen oder sonstigem Lieferumfang. Wenn Sie geschützte Bibliotheken für SharePoint konfigurieren, werden die darin gespeicherten Office-Dateien von Azure Rights Management geschützt.

Die Anweisungen sind unter den folgenden Umständen geeignet:

-   Mitarbeiter nutzen Office-Dokumente in einer SharePoint-Bibliothek gemeinsam und arbeiten zusammen daran.

-   Mitarbeiter müssen nicht die Berechtigungen festlegen oder ändern, die ein Administrator auf Bibliotheksebene festlegt.

-   Mitarbeiter müssen diese Dokumente nicht an Personen außerhalb Ihrer Organisation weitergeben.

## <a name="deployment-instructions"></a>Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt und die unterstützenden Verfahren vorhanden sind, bevor Sie mit der Benutzerdokumentation fortfahren.

## <a name="requirements-for-this-scenario"></a>Anforderungen bei diesem Szenario
Damit dieses Szenario funktioniert, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Sie haben Konten und Gruppen für Office 365 oder Azure Active Directory vorbereitet.|[Vorbereiten für Azure Information Protection](../plan-design/prepare.md)|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|
|Wenn Sie SharePoint Server verwenden möchten: Stellen Sie den RMS-Connector bereit, und konfigurieren Sie ihn für SharePoint.|[Bereitstellen des Azure Rights Management-Connectors](../deploy-use/deploy-rms-connector.md)|
|Konfigurieren von Berechtigungen zum Schutz der SharePoint-Website|[Verwalten von Berechtigungen für Listen, Bibliotheken, Ordner, Dokumente oder Listenelemente](https://support.office.com/en-ca/article/Manage-permissions-for-a-list-library-folder-document-or-list-item-9d13e7df-a770-4646-91ab-e3c117fcef45)<br /><br />[Anwenden der Verwaltung von Informationsrechten (IRM) auf eine Liste oder Bibliothek](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|
|Konfigurieren Sie SharePoint für IRM und geschützte Bibliotheken.|[Einrichten der Verwaltung von Informationsrechten (IRM) im SharePoint Admin Center](https://support.office.com/en-us/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239ce6eb-4e81-42db-bf86-a01362fed65c)<br /><br />[Anwenden der Verwaltung von Informationsrechten (IRM) auf eine Liste oder Bibliothek](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)|

### <a name="to-configure-the-sharepoint-library-for-irm-settings"></a>So konfigurieren Sie die SharePoint-Bibliothek für IRM-Einstellungen

1.  Nachdem Sie SharePoint zur Verwendung des IRM-Diensts konfiguriert haben, navigieren Sie zu Ihrer SharePoint-Bibliothek, um sie mit Azure RMS zu schützen. Wählen Sie unter **Einstellungen** &gt; **Information Rights Management (IRM)** die Option **Berechtigungen für diese Bibliothek beim Herunterladen einschränken**, geben Sie einen Richtlinientitel für Administratoren und eine Richtlinienbeschreibung für Benutzer an, und klicken Sie auf **OPTIONEN ANZEIGEN**.

2.  Wählen Sie Folgendes:

    -   **Benutzer dürfen keine Dokumente hochladen, die IRM nicht unterstützen**

    -   Optional: Wählen Sie **Gruppenschutz zulassen. Standardgruppe**, und geben Sie dann den Namen einer weiteren Gruppe ein, die gegebenenfalls an Dokumenten in dieser Bibliothek zusammenarbeiten muss, dies jedoch außerhalb von SharePoint tut. Beispiel: Die Vertriebsgruppe verfügt über Bearbeitungsrechte für die Website. Ein Mitglied der Gruppe lädt ein Dokument herunter, speichert es auf einem Datenträger und sendet es per E-Mail an einen Kollegen außerhalb der Vertriebsgruppe. Wenn der Kollege Mitglied der hier angegebenen Gruppe ist, erhält er automatisch die für die Website konfigurierten Berechtigungen und kann das Dokument bearbeiten.

        Ohne diese Option können nur Benutzer, die Zugriff auf die SharePoint-Bibliothek haben, an diesen Dokumenten zusammenarbeiten, aber nur, wenn sie die Dokumente direkt aus SharePoint herunterladen. Diese Einschränkung ist in vielen Fällen angemessen.

## <a name="user-documentation-instructions"></a>Anweisungen für Benutzerdokumentation
Es gibt keine spezifischen Benutzeranweisungen für dieses Szenario, da geschützte Bibliotheken keine besondere Aktionen von Benutzern verlangen. Dokumente sind beim Herunterladen automatisch entsprechend den Berechtigungen geschützt, die ein SharePoint-Administrator für die Website festgelegt hat. Informieren Sie die Benutzer jedoch bezüglich dieser Änderung, damit sie wissen, was sie erwartet. Teilen Sie zudem dem Helpdesk mit, welche Bibliotheken geschützt sind und wie dies die Verwendung der Dokumente einschränken kann. Aufgrund derzeit geltender Einschränkungen können diese Dokumente auf mobilen Geräten zwar angezeigt, aber nicht bearbeitet werden. Wenn Sie den Gruppenschutz konfiguriert haben, informieren Sie die Benutzer, welche Gruppen auf Dokumente außerhalb von SharePoint zugreifen und diese bearbeiten können.

Verwenden Sie die folgende Vorlage, kopieren Sie die Ankündigung, und fügen Sie sie in eine Nachricht für die Endbenutzer ein. Nehmen Sie in Anpassung an Ihre Umgebung die folgenden Änderungen vor:

1.  Ersetzen Sie jede Instanz von *&lt;Name der SharePoint-Bibliothek&gt;* durch den Namen und den Link der SharePoint-Bibliothek, die Sie für Azure Rights Management konfiguriert haben. Wenn diese Nachricht mehrere geschützte Bibliotheken betrifft, ändern Sie die Anweisungen entsprechend.

2.  Wenn Sie die Option **Gruppenschutz zulassen. Standardgruppe** konfiguriert haben, ersetzen Sie *&lt;Gruppenname&gt;* durch den Namen der konfigurierten Gruppe. Geben Sie außerdem den Grund für &lt;Grund, warum diese Gruppe Zugriffsberechtigungen für die Zusammenarbeit an den Dateien hat, aber nicht in der SharePoint-Bibliothek&gt; an. Wenn Sie diese Option nicht konfiguriert haben, löschen Sie diesen Satz.

3.  Ersetzen Sie die *&lt;Kontaktdetails&gt;* durch Anweisungen dazu, wie sich Benutzer an das Helpdesk wenden können, z.B. über einen Link zur Website, eine E-Mail-Adresse oder eine Telefonnummer.

4.  Nehmen Sie jegliche sonstigen Änderungen an der Ankündigung vor, und senden Sie sie anschließend an diese Benutzer.

Die Beispieldokumentation veranschaulicht, wie diese Ankündigung für Benutzer nach Ihren Anpassungen aussehen könnte.

![Benutzerdokumentationsvorlage für die Azure RMS-Schnellbereitstellung](../media/AzRMS_UsersBanner.png)

### <a name="it-announcement-changes-to-the-ltname-of-sharepoint-librarygt-site"></a>IT-Ankündigung: Änderungen an der Website &lt;Name der SharePoint-Bibliothek&gt;
Die SharePoint-Website **&lt;Name der SharePoint-Bibliothek&gt;** ist jetzt für die sichere Zusammenarbeit konfiguriert. Dies bedeutet, dass von nun an nur Mitglieder der Gruppe &lt;Gruppenname&gt; auf die Dokumente dieser Website zugreifen können. Das gilt auch, wenn Sie sie lokal speichern oder per E-Mail an Dritte senden. Die einzige Ausnahme besteht darin, dass Sie die Dokumente an alle Mitgliedern der Gruppe &lt;Gruppenname&gt; freigeben können, nachdem Sie die Dokumente heruntergeladen haben, um &lt;Grund, warum diese Gruppe Zugriffsrechte für die Zusammenarbeit an den Dateien hat, aber nicht in der SharePoint-Bibliothek&gt;. Beim Bearbeiten eines dieser Dokumente wird oben ein gelbes Banner mit Informationen darüber angezeigt, dass dieses Dokument geschützt ist und wer darauf zugreifen kann.

Diese Änderung hilft, unsere vertraulichen Unternehmensdaten vor einem Zugriff durch nicht berechtigte Personen zu schützen. Wenn Sie mit einem Mobilgerät auf diese geschützten Dokumente zugreifen, können Sie sie lediglich anzeigen. Zum Bearbeiten müssen Sie ein Desktopgerät verwenden.

Sie können nur Dokumente auf die Website &lt;Name der SharePoint-Website&gt; hochladen, die die sichere Zusammenarbeit unterstützen.

**Benötigen Sie Unterstützung?**

-   Wenden Sie sich an den Helpdesk: &lt;Kontaktdetails&gt;

### <a name="example-user-documentation"></a>Beispielbenutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

#### <a name="it-announcement-changes-to-the-sales-forecasts-and-reports-site"></a>IT-Ankündigung: Änderungen an der Website „Vertriebsprognosen und Berichte“
Die SharePoint-Website **Vertriebsprognosen und Berichte**ist jetzt für die sichere Zusammenarbeit konfiguriert. Das heißt: Von nun an können nur Mitglieder unseres Vertriebs- und Marketingteams auf die Dokumente auf dieser Website zugreifen. Das gilt auch, wenn Sie sie lokal speichern oder per E-Mail an Dritte senden. Dabei gibt eine Ausnahme. Nachdem Sie die Dokumente heruntergeladen haben, können Sie sie mit Angehörigen der Finanzabteilung teilen, damit diese die monatlichen Prognosezahlen extrahieren können. Beim Bearbeiten eines dieser Dokumente wird oben ein gelbes Banner mit Informationen darüber angezeigt, dass dieses Dokument geschützt ist und wer darauf zugreifen kann.

Diese Änderung hilft, unsere vertraulichen Unternehmensdaten vor einem Zugriff durch nicht berechtigte Personen zu schützen. Wenn Sie mit einem Mobilgerät auf diese geschützten Dokumente zugreifen, können Sie sie lediglich anzeigen. Zum Bearbeiten müssen Sie ein Desktopgerät verwenden.

Sie können nur Dokumente auf die Website „Vertriebsprognosen und Berichte“ hochladen, die die sichere Zusammenarbeit unterstützen.

**Benötigen Sie Unterstützung?**

-   Wenden Sie sich an den Helpdesk: helpdesk@vanarsdelltd.com




<!--HONumber=Nov16_HO2-->


