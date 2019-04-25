---
title: Zeigen Sie geschützter Dateien mithilfe des Azure Information Protection unified bezeichnungs-Clients für Windows an
description: Anweisungen, um eine geschützte Datei anzeigen, die der Azure Information Protection unified bezeichnungs Client installiert werden müssen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: 6c6e5ddd7ddc39810e05cdc8b2bf0f5b24bf8176
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60180986"
---
# <a name="user-guide-view-files-that-have-been-protected-by-rights-management"></a>Leitfaden: Anzeigen von Dateien, die durch Rights Management geschützt wurden

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*
>
> *Anleitungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Sie können ein geschütztes Dokument beliebig oft anzeigen, indem Sie es öffnen. Sie können z. B. einfach auf eine Anlage einer E-Mail klicken oder im Datei-Explorer auf eine Datei doppelklicken. Alternativ können Sie auch auf den Link zu einer Datei klicken.

Wenn die Dateien nicht sofort geöffnet werden, kann eventuell der **Azure Informationen Protection-Viewer** Abhilfe leisten. Dieser Viewer kann geschützte Textdateien, geschützte Bilddateien geschützte PDF-Dateien und alle Dateien mit der Erweiterung **PFILE** öffnen.

Der Viewer wird automatisch als Teil des Azure Information Protection unified bezeichnungs-Clients installiert, oder Sie können es separat installieren. Installieren Sie diesen Client und den Viewer aus der [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) auf der Microsoft-Website. Weitere Informationen zu diesen Client zu installieren, finden Sie unter [herunterladen und installieren Sie den Azure Information Protection unified bezeichnungs-Client](install-unifiedlabelingclient-app.md).

> [!NOTE]
> Obwohl das Installieren des Clients mehr Funktionalität bietet, sind lokale Administratorberechtigungen erforderlich, und die volle Funktionalität erfordert einen entsprechenden Dienst für Ihre Organisation. Beispiel: Azure Information Protection.
> 
> Installieren Sie den Viewer, wenn Ihnen von einer Person aus einer anderen Organisation ein geschütztes Dokument gesendet wurde oder Sie nicht über lokale Administratorrechte auf Ihrem PC verfügen.

Um ein geschütztes Dokument öffnen zu können, muss es sich um eine RMS-fähige Anwendung handeln. Zu RMS-fähigen Anwendungen zählen beispielsweise Office-Apps und der Azure Informationen Protection-Viewer. Eine Liste der Anwendungen nach Typ und unterstützten Geräten finden Sie in der Tabelle [RMS-fähige Anwendungen](../requirements-applications.md#rms-enlightened-applications). 

## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg als E-Mail-Anhang

Wenn in einer E-Mail **message.rpmsg** als Dateianlage angezeigt wird, handelt es sich bei dieser Datei nicht um ein geschütztes Dokument, sondern um eine geschützte, als Anlage angezeigte E-Mail-Nachricht. Sie können den Azure Information Protection-Viewer nicht bei Windows verwenden, um diese geschützte E-Mail-Nachricht auf Ihrem Windows-PC anzuzeigen. Stattdessen benötigen Sie eine E-Mail-Anwendung für Windows, die Rights Management-Schutz wie etwa bei Office Outlook unterstützt. Alternativ können Sie Outlook im Web verwenden.

Wenn Sie jedoch ein iOS- oder Android-Gerät besitzen, können Sie diese geschützten E-Mail-Nachrichten mit der Azure Information Protection-App öffnen. Sie können die App für diese mobilen Geräte über die Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) auf der Microsoft-Website installieren.

## <a name="prompts-for-authentication"></a>Aufforderung zur Authentifizierung

Bevor Sie die geschützte Datei anzeigen können, muss der Rights Management-Dienst, mit dem die Datei geschützt wurde, bestätigen, dass Sie zum Anzeigen der Datei berechtigt sind. Dazu überprüft der Dienst Ihren Benutzernamen und Ihr Kennwort. In einigen Fällen können Ihre Anmeldeinformationen zwischengespeichert sein, und Sie sehen keine Eingabeaufforderung, um sich anzumelden. In anderen Fällen werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben.

Wenn Ihre Organisation Ihnen kein cloudbasiertes Konto für Office 365 oder Azure zur Verfügung stellt und auch keine gleichwertige lokale Version (AD RMS) verwendet, haben Sie zwei Optionen:

- Wenn Sie eine geschützte E-Mail erhalten haben, folgen Sie den Anweisungen zur Anmeldung bei Ihrem sozialen Netzwerk als Identitätsanbieter (z.B. Google bei einem Gmail-Konto), oder beantragen Sie eine einmalige Kennung.

- Sie können ein kostenloses Konto beantragen, bei dem Sie sich mit Ihren Anmeldeinformationen anmelden können. Auf diese Weise können Sie Dokumente öffnen, die von Rights Management geschützt werden. Klicken Sie zur Beantragung eines Kontos auf den Link [RMS for Individuals](https://go.microsoft.com/fwlink/?LinkId=309469). Verwenden Sie nicht Ihre private E-Mail-Adresse, sondern die Ihrer Organisation. 

## <a name="to-view-a-protected-file"></a>So zeigen Sie eine geschützte Datei an

1. Öffnen Sie die geschützte Datei (indem Sie z. B. auf die Datei doppelklicken oder auf den Link zur Datei klicken). Wenn Sie zum Auswählen einer App aufgefordert werden, wählen Sie **Azure Information Protection-Viewer** aus. 

2. Wenn Sie eine Seite **Anmelden** oder **Registrieren** sehen: Klicken Sie auf **Anmelden**, und geben Sie Ihre Anmeldeinformationen ein. Wenn Ihnen die geschützte Datei als Anlage gesendet wurde, müssen Sie die gleiche E-Mail-Adresse angeben, die zum Senden der Datei verwendet wurde.
    
    Wenn Sie nicht über ein akzeptiertes Konto verfügen, finden Sie weitere Informationen auf dieser Seite im Abschnitt [Aufforderung zur Authentifizierung](#prompts-for-authentication).

3. Eine schreibgeschützte Version der Datei wird geöffnet, der **Azure Information Protection-Viewer** oder in die Anwendung mit der Dateinamenerweiterung.

4. Wenn Sie weitere geschützte Dateien öffnen müssen, können Sie über den Viewer direkt zu ihnen navigieren, indem Sie die Option **Öffnen** verwenden. Ihre ausgewählte Datei ersetzt die ursprüngliche Datei im Viewer. 

> [!TIP]
> Wenn die geschützte Datei nicht geöffnet wird und der vollständige Azure Information Protection Client installiert ist, versuchen Sie es mit der Option **Einstellungen zurücksetzen**. Um diese Option aus einer Office-app zuzugreifen, wählen die **Vertraulichkeit** Schaltfläche > **Hilfe und Feedback** > **Einstellungen zurücksetzen**. 
> 
> [Weitere Informationen zur Option „Einstellungen zurücksetzen“](clientv2-admin-guide.md#more-information-about-the-reset-settings-option)

## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

