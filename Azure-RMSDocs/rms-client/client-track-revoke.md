---
title: "Nachverfolgen und Widerrufen von Dokumenten – Azure Information Protection"
description: "Nachdem Sie Ihre Dokumente geschützt haben, können Sie verfolgen, wie sie von Benutzern verwendet werden. Bei Bedarf können Sie auch den Zugriff auf diese Dokumente widerrufen, wenn Benutzer nicht mehr in der Lage sein sollen, sie zu lesen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 643c762e-23ca-4b02-bc39-4e3eeb657a1d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 710e614f9ba6e5732046cfb85d3463875ab34566
ms.sourcegitcommit: d5ce1bce5e63b3e510033ff9d4d246dd3511ed7c
translationtype: HT
---
# <a name="track-and-revoke-your-documents-when-you-use-azure-information-protection"></a>Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung von Azure Information Protection

>*Gilt für: Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Nachdem Sie Ihre Dokumente mithilfe von Azure Information Protection geschützt haben, können Sie nachverfolgen, wie andere mit Ihren geschützten Dokumenten verfahren. Bei Bedarf können Sie auch den Zugriff auf diese Dokumente widerrufen, wenn Benutzer nicht mehr in der Lage sein sollen, sie zu lesen. Verwenden Sie hierfür die **Website zum Nachverfolgen von Dokumenten**, auf die Sie von Windows-Computern, Mac-Computern und sogar mit Tablets und Smartphones zugreifen können.

Wenn Sie auf diese Website zugreifen möchten, melden Sie sich dort an, um Ihre Dokumente zu nachzuverfolgen. Sofern Ihre Organisation über ein [Abonnement verfügt, das das Nachverfolgen und Sperren von Dokumenten unterstützt](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features), und Ihnen eine Lizenz für dieses Abonnement zugewiesen ist, können Sie sehen, wer versucht hat, die geschützten Dateien zu öffnen. Sie können außerdem sehen, ob dieser Versuch erfolgreich war (ob die betreffenden Personen erfolgreich authentifiziert wurden). Sie können auch jeden Zugriffsversuch der Personen auf das Dokument sowie deren Position zu diesem Zeitpunkt sehen. Zusätzlich:

-   Wenn Sie die Freigabe eines Dokuments aufheben müssen: Klicken Sie auf **Zugriff widerrufen**, notieren Sie den Zeitraum, für den das Dokument weiterhin verfügbar sein wird, und entscheiden Sie, ob Sie den Personen mitteilen möchten, dass Sie den Zugriff auf das zuvor freigegebene Dokument widerrufen, und verfassen Sie bei Bedarf eine angepasste E-Mail-Nachricht. Wenn Sie ein Dokument widerrufen, wird das freigegebene Dokument nicht gelöscht, aber autorisierte Benutzer können es nicht mehr öffnen:
    
    ![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](../media/tracking-site-revoke-access-icon.png)

-   Wenn Sie das Dokument nach Excel exportieren möchten: Klicken Sie auf **In CSV-Datei exportieren**, um die Daten ändern und eigene Ansichten und Diagramme erstellen zu können:
    
    ![Symbol „In CSV-Datei exportieren“ auf der Website zur Dokumentenverfolgung](../media/tracking-site-export-icon.png)

-   Wenn Sie E-Mail-Benachrichtigungen konfigurieren möchten: Klicken Sie auf **Einstellungen** , und geben Sie an, wie und ob Sie bei einem Zugriff auf das Dokument per E-Mail benachrichtigt werden möchten:
    
    ![Symbol „In CSV-Datei exportieren“ auf der Website zur Dokumentenverfolgung](../media/tracking-site-settings-email.png)

- Wenn Sie freigegebene Dokumente nachverfolgen und für andere sperren möchten: Azure Information Protection-Administratoren können geschützte Dokumente nachverfolgen und für andere sperren, indem sie auf das Adminsymbol klicken. Dieses Symbol wird ausschließlich Administratoren angezeigt:
    
    ![Adminsymbol auf der Website zur Dokumentenverfolgung](../media/tracking-site-admin-icon.png)

Um ein geschütztes Dokument nachzuverfolgen, muss es auf der Website zur Dokumentenverfolgung registriert werden. Zu diesem Zweck verwenden Sie entweder den Datei-Explorer oder die Office-Apps.

## <a name="using-office-to-track-or-revoke-the-document"></a>Verwenden von Office zum Nachverfolgen oder Widerrufen des Dokuments

Bei den Office-Anwendungen wie Word, Excel, PowerPoint und Outlook: 

1. Öffnen Sie das geschützte Dokument, das Sie nachverfolgen oder widerrufen möchten.

2. Klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen** > **Nachverfolgen und widerrufen**:

    ![Option „Verwendung nachverfolgen“](../media/track-usage-callout.png)

Wenn diese Optionen in Ihren Office-Anwendungen nicht angezeigt werden, hat dies wahrscheinlich einen der folgenden Gründe: der Azure Information Protection-Client ist nicht auf dem Computer installiert, die Office-Anwendungen müssen neu gestartet werden oder Ihr Computer muss neu gestartet werden, um die Installation abzuschließen. Weitere Informationen zum Installieren des Azure Information Protection-Clients finden Sie unter [Herunterladen und Installieren des Azure Information Protection-Clients](install-client-app.md).

## <a name="using-file-explorer-to-track-or-revoke-the-document"></a>Verwenden des Datei-Explorer zum Nachverfolgen oder Widerrufen des Dokuments

1. Klicken Sie mit der rechten Maustaste auf die geschützte Datei, und wählen Sie **Klassifizieren und schützen** aus.

2. Wählen Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Option **Track and revoke** (Nachverfolgen und widerrufen) aus.

    ![Symbol für „Nachverfolgen und widerrufen“ im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“](../media/track-and-revoke.png)


### <a name="using-a-web-browser-track-and-revoke-documents-that-you-have-registered"></a>Verwenden eines Webbrowser zum Nachverfolgen und Widerrufen von registrierten Dokumenten

Nachdem Sie das geschützte Dokument mithilfe der Office-Apps oder des Datei-Explorer registriert haben, können Sie diese Dokumente mithilfe eines unterstützten Webbrowsers nachverfolgen und widerrufen:

- Besuchen Sie die [Website für die Dokumentverfolgung](https://go.microsoft.com/fwlink/?LinkId=529562) über Ihren Windows-PC, Macintosh-Computer oder Ihr mobiles Gerät.

    **Unterstützte Browser**: Wir empfehlen Internet Explorer in der Version 10 oder höher. Sie können aber auch alle der folgenden Browser verwenden, um auf die Website zum Nachverfolgen von Dokumenten zuzugreifen:

    -   Internet Explorer: Mindestens Version 10

    -   Internet Explorer 9 mindestens mit MS12-037: Kumulatives Sicherheitsupdate für Internet Explorer: 12. Juni 2012

    -   Mozilla Firefox: Mindestens Version 12

    -   Apple Safari 5: Mindestens Version 5

    -   Google Chrome: Mindestens Version 18


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]