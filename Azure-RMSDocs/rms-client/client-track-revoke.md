---
title: "Nachverfolgen und Widerrufen Ihrer geschützten Dokumente bei Verwendung von Azure Information Protection | Azure Information Protection"
description: "Nachdem Sie Ihre Dokumente geschützt haben, können Sie verfolgen, wie sie von Benutzern verwendet werden. Bei Bedarf können Sie auch den Zugriff auf diese Dokumente widerrufen, wenn Benutzer nicht mehr in der Lage sein sollen, sie zu lesen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 1107f484f204e64d76c389daef4d9decbfbb20e8
ms.openlocfilehash: e83d0352003fa3790fd4f8d5c59f4f7b40ef4265


---

# <a name="track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung von Azure Information Protection

>*Gilt für: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

**[Diese Version des Clients ist eine Vorschau und unterliegt Änderungen.]**

Nachdem Sie Ihre Dokumente mithilfe von Azure Information Protection geschützt haben, können Sie nachverfolgen, wie andere mit Ihren geschützten Dokumenten verfahren. Bei Bedarf können Sie auch den Zugriff auf diese Dokumente widerrufen, wenn Benutzer nicht mehr in der Lage sein sollen, sie zu lesen. Verwenden Sie hierfür die **Website zum Nachverfolgen von Dokumenten**, auf die Sie von Windows-Computern, Mac-Computern und sogar mit Tablets und Smartphones zugreifen können.

<div style="padding-top: 56.25%; position: relative; width: 100%;">
<iframe style="position: absolute;top: 0;left: 0;right: 0;bottom: 0;" width="100%" height="100%" src="https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation/player" frameborder="0" allowfullscreen></iframe>
</div>

Wenn Sie auf diese Website zugreifen möchten, melden Sie sich dort an, um Ihre Dokumente zu nachzuverfolgen. Sofern Ihre Organisation über ein [Abonnement verfügt, das das Nachverfolgen und Sperren von Dokumenten unterstützt](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), und Ihnen eine Lizenz für dieses Abonnement zugewiesen ist, können Sie sehen, wer versucht hat, die geschützten Dateien zu öffnen. Sie können außerdem sehen, ob dieser Versuch erfolgreich war (ob die betreffenden Personen erfolgreich authentifiziert wurden). Sie können auch jeden Zugriffsversuch der Personen auf das Dokument sowie deren Position zu diesem Zeitpunkt sehen. Zusätzlich:

-   Wenn Sie die Freigabe eines Dokuments aufheben müssen: Klicken Sie auf **Zugriff widerrufen**, notieren Sie den Zeitraum, für den das Dokument weiterhin verfügbar sein wird, und entscheiden Sie, ob Sie den Personen mitteilen möchten, dass Sie den Zugriff auf das zuvor freigegebene Dokument widerrufen, und verfassen Sie bei Bedarf eine angepasste E-Mail-Nachricht. Wenn Sie ein Dokument widerrufen, wird das Dokument, das Sie freigegeben haben, nicht gelöscht, aber autorisierte Benutzer können es nicht mehr öffnen.

-   Wenn Sie das Dokument nach Excel exportieren möchten: Klicken Sie auf **In CSV-Datei exportieren**, um die Daten ändern und eigene Ansichten und Diagramme erstellen zu können.

-   Wenn Sie E-Mail-Benachrichtigungen konfigurieren möchten: Klicken Sie auf **Einstellungen** , und geben Sie an, wie und ob Sie bei einem Zugriff auf das Dokument per E-Mail benachrichtigt werden möchten.

- Wenn Sie freigegebene Dokumente nachverfolgen und für andere sperren möchten: Azure Information Protection-Administratoren können geschützte Dokumente nachverfolgen und für andere sperren, indem sie auf das Adminsymbol klicken. Dieses Symbol wird ausschließlich Administratoren angezeigt.

-   Wenn Sie Fragen haben oder Feedback zur Website zum Nachverfolgen von Dokumenten geben möchten: Klicken Sie auf das Symbol „Hilfe“, um auf die [Häufig gestellten Fragen zur Nachverfolgung von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=523977)zuzugreifen.

## <a name="using-office-to-access-the-document-tracking-site"></a>Verwenden von Office für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Für die Office-Anwendungen Word, Excel, PowerPoint und Outlook: Klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen** > **Verwendung nachverfolgen**.

Wenn diese Optionen in Ihren Office-Anwendungen nicht angezeigt werden, hat dies wahrscheinlich einen der folgenden Gründe: der Azure Information Protection-Client ist nicht auf dem Computer installiert, die Office-Anwendungen müssen neu gestartet werden oder Ihr Computer muss neu gestartet werden, um die Installation abzuschließen. Weitere Informationen zum Installieren des Azure Information Protection-Clients finden Sie unter [Herunterladen und Installieren des Azure Information Protection-Clients](install-client-app.md).


### <a name="other-ways-to-track-and-revoke-your-documents"></a>Weitere Methoden zum Nachverfolgen von und zum Widerrufen des Zugriffs auf Dokumente
Neben den Funktionen zum Nachverfolgen Ihrer geschützten Dokumente auf Windows-Computern mithilfe von Office-Anwendungen gibt es auch die folgenden Alternativen:

-   **Verwenden eines Webbrowsers**: Diese Methode kann auf allen unterstützten Geräten angewendet werden.

-   **Verwenden des Datei-Explorers**: Diese Methode funktioniert auf Windows-Computern.

#### <a name="using-a-web-browser-to-access-the-doc-tracking-site"></a>Verwenden eines Webbrowsers für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Öffnen Sie einen der unterstützten Webbrowser, und wechseln Sie zur [Website zum Nachverfolgen von Dokumenten](https://go.microsoft.com/fwlink/?LinkId=529562).

    Unterstützte Browser: Wir empfehlen Internet Explorer in der neuesten Version 10, Sie können aber auch alle der folgenden Browser verwenden, um auf die Website zum Nachverfolgen von Dokumenten zuzugreifen:

    -   Internet Explorer: Mindestens Version 10

    -   Internet Explorer 9 mindestens mit MS12-037: Kumulatives Sicherheitsupdate für Internet Explorer: 12. Juni 2012

    -   Mozilla Firefox: Mindestens Version 12

    -   Apple Safari 5: Mindestens Version 5

    -   Google Chrome: Mindestens Version 18

#### <a name="using-file-explorer-to-access-the-doc-tracking-site"></a>Verwenden des Datei-Explorers für den Zugriff auf die Website zum Nachverfolgen von Dokumenten

-   Klicken Sie mit der rechten Maustaste auf die Datei, wählen Sie **Klassifizieren und schützen (Vorschau)** und dann im **Azure Information Protection-Viewer** das Symbol „Verwendung nachverfolgen“ aus.


## <a name="other-instructions"></a>Sonstige Anweisungen
Anweisungen zur Vorgehensweise finden Sie in den folgenden Abschnitten des Azure Information Protection-Benutzerhandbuchs:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)





<!--HONumber=Dec16_HO1-->


