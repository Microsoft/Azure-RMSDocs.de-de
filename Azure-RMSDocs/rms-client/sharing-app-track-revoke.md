---
# required metadata

title: Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung

*Gilt für: Azure Rights Management, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Wenn Sie Ihre Dokumente mit der RMS-Freigabeanwendung geschützt haben und Ihre Organisation nicht Active Directory Rights Management Services, sondern Azure Rights Management verwendet, können Sie verfolgen, wie die Benutzer die geschützten Dokumente verwenden. Falls nötig, können Sie den Zugriff auf diese Dokumente widerrufen, um ein unerwünschtes Weitergeben und Teilen zu unterbinden. Verwenden Sie hierfür die **Website zum Nachverfolgen von Dokumenten**, auf die Sie von Windows-Computern, Mac-Computern und sogar mit Tablets und Smartphones zugreifen können.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

Wenn Sie auf diese Website zugreifen möchten, melden Sie sich dort an, um Ihre Dokumente zu nachzuverfolgen. Sofern Ihre Organisation über ein [Abonnement verfügt, das das Nachverfolgen und Sperren von Dokumenten unterstützt](https://technet.microsoft.com/dn858608.aspx), und Ihnen eine Lizenz für dieses Abonnement zugewiesen ist, können Sie sehen, wer versucht hat, die geschützten Dateien zu öffnen. Sie können außerdem sehen, ob dieser Versuch erfolgreich war (ob die betreffenden Personen erfolgreich authentifiziert wurden). Jeder Versuch, auf das Dokument zuzugreifen und der zum Zeitpunkt geltende Standort werden dokumentiert. Zusätzlich:

-   Wenn Sie die Freigabe eines Dokuments aufheben müssen: Klicken Sie auf **Zugriff widerrufen**, notieren Sie den Zeitraum, für den das Dokument weiterhin verfügbar sein wird, und entscheiden Sie, ob Sie den Personen mitteilen möchten, dass Sie den Zugriff auf das zuvor freigegebene Dokument widerrufen, und verfassen Sie bei Bedarf eine angepasste E-Mail-Nachricht. Wenn Sie ein Dokument widerrufen, wird das Dokument, das Sie freigegeben haben, nicht gelöscht, aber autorisierte Benutzer können es nicht mehr öffnen.

-   Wenn Sie das Dokument nach Excel exportieren möchten: Klicken Sie auf **In Excel öffnen**, um die Daten ändern und eigene Ansichten und Diagramm erstellen zu können.

-   Wenn Sie E-Mail-Benachrichtigungen konfigurieren möchten: Klicken Sie auf **Einstellungen** , und geben Sie an, wie und ob Sie bei einem Zugriff auf das Dokument per E-Mail benachrichtigt werden möchten.

-   Wenn Sie Fragen haben oder Feedback zur Website zum Nachverfolgen von Dokumenten geben möchten: Klicken Sie auf das Symbol „Hilfe“, um auf die [Häufig gestellten Fragen zur Nachverfolgung von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=523977)zuzugreifen..

## Verwenden von Office für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Bei den Office-Anwendungen wie Word, Excel und PowerPoint: Klicken Sie auf der Registerkarte **Start** in der Gruppe **RMS** auf **Geschützt freigeben**, und klicken Sie anschließend auf **Verwendung nachverfolgen**..

    ![Verwendung nachverfolgen von Office-Anwendungen bei Verwendung der RMS-Freigabeanwendung ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

-   In Outlook: Klicken Sie auf der Registerkarte **Start** in der Gruppe  **RMS** auf **Verwendung nachverfolgen**:

    ![Auswählen von Verwendung nachverfolgen in Outlook bei der Verwendung der RMS-Freigabeanwendung ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

Wenn diese Optionen für RMS nicht angezeigt werden, ist die RMS-Freigabeanwendung entweder nicht oder nicht in der neuesten Version auf Ihrem Computer installiert, oder der Computer muss neu gestartet werden muss, um die Installation abzuschließen. Weitere Informationen zum Installieren der Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md)..

### Weitere Methoden zum Nachverfolgen von und zum Widerrufen des Zugriffs auf Dokumente
Neben den Funktionen zum Nachverfolgen Ihrer Dokumente auf Windows-Computern mithilfe von Office-Anwendungen gibt es auch die folgenden Alternativen:

-   **Verwenden eines Webbrowsers**: Diese Methode kann auf allen unterstützten Geräten angewendet werden.

-   **Verwenden des Datei-Explorers**: Diese Methode funktioniert auf Windows-Computern.

-   **Verwenden einer Outlook-E-Mail-Nachricht**: Diese Methode funktioniert auf Windows-Computern.

#### Verwenden eines Webbrowsers für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Öffnen Sie einen der unterstützten Webbrowser, und wechseln Sie zur [Website zum Nachverfolgen von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=529562)..

    Unterstützte Browser: Wir empfehlen Internet Explorer in der neuesten Version 10, Sie können aber auch alle der folgenden Browser verwenden, um auf die Website zum Nachverfolgen von Dokumenten zuzugreifen:

    -   Internet Explorer: Mindestens Version 10

    -   Internet Explorer 9 mindestens mit MS12-037: Kumulatives Sicherheitsupdate für Internet Explorer: 12. Juni 2012

    -   Mozilla Firefox: Mindestens Version 12

    -   Apple Safari 5: Mindestens Version 5

    -   Google Chrome: Mindestens Version 18

#### Verwenden des Datei-Explorers für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Mit RMS schützen** und dann **Verwendung nachverfolgen** aus:

    ![Auswählen von Verwendung nachverfolgen im Explorer bei der Verwendung der RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### Verwenden einer Outlook-E-Mail-Nachricht für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Klicken Sie in einer E-Mail-Nachricht auf der Registerkarte **Nachricht** in der Gruppe  **RMS** auf **Geschützt freigeben**und dann auf **Verwendung nachverfolgen**:

    ![Auswählen von Verwendungsnachverfolgung in Outlook bei der Verwendung der RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do-)

## Weitere Informationen
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)


<!--HONumber=May16_HO2-->

