---
title: Verfolgen und Widerrufen von Dokumenten mithilfe der RMS-Freigabeanwendung – AIP
description: Nachdem Sie Ihre Dokumente mit der RMS-Freigabeanwendung geschützt haben, können Sie nachverfolgen, wie andere mit Ihren geschützten Dokumenten verfahren. Falls nötig, können Sie den Zugriff auf diese Dokumente widerrufen, um ein unerwünschtes Weitergeben und Teilen zu unterbinden.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/04/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 61f349ce-bdd2-45c1-acc5-bc83937fb187
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 80c184892af6f82e744d32d96d562f2fadf9b859
ms.sourcegitcommit: 6a67fc50bd8b8a06974de647c15115a673f0217c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="track-and-revoke-your-documents-when-you-use-the-rms-sharing-application"></a>Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Wenn Sie Ihre Dokumente mit der RMS-Freigabeanwendung geschützt haben und Ihre Organisation nicht Active Directory Rights Management Services, sondern Azure Information Protection verwendet, können Sie verfolgen, wie die Benutzer die geschützten Dokumente verwenden. Falls nötig, können Sie den Zugriff auf diese Dokumente widerrufen, um ein unerwünschtes Weitergeben und Teilen zu unterbinden. Verwenden Sie hierfür die **Website zum Nachverfolgen von Dokumenten**, auf die Sie von Windows-Computern, Mac-Computern und sogar mit Tablets und Smartphones zugreifen können.

Wenn Sie auf diese Website zugreifen möchten, melden Sie sich dort an, um Ihre Dokumente zu nachzuverfolgen. Sofern Ihre Organisation über ein [Abonnement verfügt, das das Nachverfolgen und Sperren von Dokumenten unterstützt](https://www.microsoft.com/cloud-platform/azure-information-protection-features), und Ihnen eine Lizenz für dieses Abonnement zugewiesen ist, können Sie sehen, wer versucht hat, die geschützten Dateien zu öffnen. Sie können außerdem sehen, ob dieser Versuch erfolgreich war (ob die betreffenden Personen erfolgreich authentifiziert wurden). Jeder Versuch, auf das Dokument zuzugreifen und der zum Zeitpunkt geltende Standort werden dokumentiert. In seltenen Fällen ist der berichtete Standort möglicherweise nicht genau. Dies ist beispielsweise dann der Fall, wenn ein Benutzer, der ein geschütztes Dokument öffnet, eine VPN-Verbindung verwendet oder sein Computer eine IPv6-Adresse aufweist.

Folgende Aktionen können Sie auf der Website zum Nachverfolgen von Dokumenten ausführen:

- Wenn Sie die Freigabe eines Dokuments aufheben müssen: Klicken Sie auf **Zugriff widerrufen**, notieren Sie den Zeitraum, für den das Dokument weiterhin verfügbar sein wird, und entscheiden Sie, ob Sie den Personen mitteilen möchten, dass Sie den Zugriff auf das zuvor freigegebene Dokument widerrufen, und verfassen Sie bei Bedarf eine angepasste E-Mail-Nachricht. Wenn Sie ein Dokument widerrufen, wird das Dokument, das Sie freigegeben haben, nicht gelöscht, aber autorisierte Benutzer können es nicht mehr öffnen.

- Wenn Sie das Dokument nach Excel exportieren möchten: Klicken Sie auf **In CSV-Datei exportieren**, um die Daten ändern und eigene Ansichten und Diagramme erstellen zu können.

- Wenn Sie E-Mail-Benachrichtigungen konfigurieren möchten: Klicken Sie auf **Einstellungen** , und geben Sie an, wie und ob Sie bei einem Zugriff auf das Dokument per E-Mail benachrichtigt werden möchten.

- Wenn Sie freigegebene Dokumente nachverfolgen und für andere sperren möchten: Azure Information Protection-Administratoren können Dokumente nachverfolgen und für andere sperren, indem sie auf das Adminsymbol klicken. Dieses Symbol wird ausschließlich Administratoren angezeigt.
    
    Hinweis: Wenn Sie dieses Symbol nicht sehen, obwohl Sie über globale Administratorrechte verfügen, liegt das daran, dass Sie selbst noch keine Dokumente freigegeben haben. Verwenden Sie in diesem Fall die folgende URL, um auf die Website zur Dokumentenverfolgung zu gelangen: https://portal.azurerms.com/#/admin

- Wenn Sie Fragen haben oder Feedback zur Website zum Nachverfolgen von Dokumenten geben möchten: Klicken Sie auf das Symbol „Hilfe“, um auf die [Häufig gestellten Fragen zur Nachverfolgung von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=523977)zuzugreifen.

## <a name="using-office-to-access-the-document-tracking-site"></a>Verwenden von Office für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

- Bei den Office-Anwendungen wie Word, Excel und PowerPoint: Klicken Sie auf der Registerkarte **Start** ihn der Gruppe **RMS** auf **Geschützt freigeben**, und klicken Sie dann auf **Verwendung nachverfolgen**.

    ![Verwendung nachverfolgen von Office-Anwendungen bei Verwendung der RMS-Freigabeanwendung ](../media/ADRMS_MSRMSApp_OfficeToolbarTrackUsage.png)

- In Outlook: Klicken Sie auf der Registerkarte **Start** in der Gruppe  **RMS** auf **Verwendung nachverfolgen**:

    ![Auswählen von Verwendung nachverfolgen in Outlook bei der Verwendung der RMS-Freigabeanwendung ](../media/ADRMS_MSRMSApp_OutlookTrackUsage.png)

Wenn diese Optionen für RMS nicht angezeigt werden, ist die RMS-Freigabeanwendung entweder nicht oder nicht in der neuesten Version auf Ihrem Computer installiert, oder der Computer muss neu gestartet werden muss, um die Installation abzuschließen. Weitere Informationen zum Installieren der Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

> [!NOTE] 
> Wenn Sie den [Azure Information Protection-Client](../rms-client/info-protect-client.md) installiert haben, können Sie auch über die Schaltfläche **Schützen** auf die Website zur Dokumentkontrolle zugreifen: 
> 
> - Klicken Sie in einer Office-Anwendung auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**  >  **Verwendung nachverfolgen**. 

### <a name="other-ways-to-track-and-revoke-your-documents"></a>Weitere Methoden zum Nachverfolgen von und zum Widerrufen des Zugriffs auf Dokumente
Neben den Funktionen zum Nachverfolgen Ihrer Dokumente auf Windows-Computern mithilfe von Office-Anwendungen gibt es auch die folgenden Alternativen:

-   **Verwenden eines Webbrowsers**: Diese Methode kann auf allen unterstützten Geräten angewendet werden.

-   **Verwenden des Datei-Explorers**: Diese Methode funktioniert auf Windows-Computern.

-   **Verwenden einer Outlook-E-Mail-Nachricht**: Diese Methode funktioniert auf Windows-Computern.

#### <a name="using-a-web-browser-to-access-the-doc-tracking-site"></a>Verwenden eines Webbrowsers für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

- Öffnen Sie einen der unterstützten Webbrowser, und wechseln Sie zur [Website zum Nachverfolgen von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=529562).

    Unterstützte Browser: Wir empfehlen Internet Explorer in der neuesten Version 10, Sie können aber auch alle der folgenden Browser verwenden, um auf die Website zum Nachverfolgen von Dokumenten zuzugreifen:

    -   Internet Explorer: Mindestens Version 10

    -   Internet Explorer 9 mindestens mit MS12-037: Kumulatives Sicherheitsupdate für Internet Explorer: 12. Juni 2012

    -   Mozilla Firefox: Mindestens Version 12

    -   Apple Safari 5: Mindestens Version 5

    -   Google Chrome: Mindestens Version 18

#### <a name="using-file-explorer-to-access-the-doc-tracking-site"></a>Verwenden des Datei-Explorers für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

- Klicken Sie mit der rechten Maustaste auf die Datei, und wählen Sie **Mit RMS schützen** und dann **Verwendung nachverfolgen** aus:

    ![Auswählen von Verwendung nachverfolgen im Explorer bei der Verwendung der RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_ExplorerTrackUsage.png)

#### <a name="using-an-outlook-email-message-to-access-the-doc-tracking-site"></a>Verwenden einer Outlook-E-Mail-Nachricht für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

- Klicken Sie in einer E-Mail-Nachricht auf der Registerkarte **Nachricht** in der Gruppe  **RMS** auf **Geschützt freigeben**und dann auf **Verwendung nachverfolgen**:

    ![Auswählen von Verwendung nachverfolgen in Outlook bei der Verwendung der RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_OutlookMessageTrackUsage.png)

## <a name="examples-and-other-instructions"></a>Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Siehe auch
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]