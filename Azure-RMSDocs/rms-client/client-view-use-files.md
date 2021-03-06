---
title: Anzeigen geschützter Dateien mit dem Azure Information Protection Classic Client Viewer
description: Anweisungen zum Anzeigen und Verwenden einer geschützten Datei, die erfordert, dass der Azure Information Protection-Client-Viewer installiert ist.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 1/13/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ROBOTS: NOINDEX
ms.subservice: v1client
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 5a0bbc3160784259f3bf6799135b6cb82fb64693
ms.sourcegitcommit: b32c16e41ba36167b5a3058b56a73183bdd4306d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/29/2020
ms.locfileid: "97807041"
---
# <a name="user-guide-view-protected-files-with-the-azure-information-protection-classic-client-viewer"></a>Benutzerhandbuch: Anzeigen geschützter Dateien mit dem Azure Information Protection Classic Client Viewer

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8 *
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie im [Benutzerhandbuch für Unified Bezeichnung-Client](clientv2-view-use-files.md). *

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Sie können eine geschützte Datei häufig anzeigen, indem Sie sie einfach öffnen. Sie können z. B. einfach auf eine Anlage einer E-Mail klicken oder im Datei-Explorer auf eine Datei doppelklicken. Alternativ können Sie auch auf den Link zu einer Datei klicken.

Wenn die Dateien nicht sofort geöffnet werden, kann eventuell der **Azure Informationen Protection-Viewer** Abhilfe leisten. Dieser Viewer kann geschützte Textdateien, geschützte Bilddateien geschützte PDF-Dateien und alle Dateien mit der Erweiterung **PFILE** öffnen.

Dieser Viewer wird automatisch als Teil des Azure Information Protection-Clients oder separat installiert. Sie können sowohl den Client als auch den Viewer über die Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) auf der Microsoft-Website installieren. Weitere Informationen zum Installieren des Clients finden Sie unter [Herunterladen und Installieren des Azure Information Protection-Clients](install-client-app.md).

> [!NOTE]
> Obwohl das Installieren des Clients mehr Funktionalität bietet, sind lokale Administratorberechtigungen erforderlich, und die volle Funktionalität erfordert einen entsprechenden Dienst für Ihre Organisation. Zum Beispiel Azure Information Protection oder Active Directory Rights Management Services.
> 
> Installieren Sie den Viewer, wenn Ihnen von einer Person aus einer anderen Organisation ein geschütztes Dokument gesendet wurde oder Sie nicht über lokale Administratorrechte auf Ihrem PC verfügen.

Um ein geschütztes Dokument öffnen zu können, muss es sich um eine RMS-fähige Anwendung handeln. Zu RMS-fähigen Anwendungen zählen beispielsweise Office-Apps und der Azure Informationen Protection-Viewer. Eine Liste der Anwendungen nach Typ und unterstützten Geräten finden Sie in den Tabellen mit [RMS-fähigen Anwendungen](../requirements-applications.md) .
  
## <a name="messagerpmsg-as-an-email-attachment"></a>Message.rpmsg als E-Mail-Anhang

Wenn in einer E-Mail **message.rpmsg** als Dateianlage angezeigt wird, handelt es sich bei dieser Datei nicht um ein geschütztes Dokument, sondern um eine geschützte, als Anlage angezeigte E-Mail-Nachricht. Sie können den Azure Information Protection-Viewer nicht bei Windows verwenden, um diese geschützte E-Mail-Nachricht auf Ihrem Windows-PC anzuzeigen. Stattdessen benötigen Sie eine E-Mail-Anwendung für Windows, die Rights Management-Schutz wie etwa bei Office Outlook unterstützt. Alternativ können Sie Outlook im Web verwenden.

Wenn Sie jedoch ein iOS- oder Android-Gerät besitzen, können Sie diese geschützten E-Mail-Nachrichten mit der Azure Information Protection-App öffnen. Sie können die App für diese mobilen Geräte über die Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) auf der Microsoft-Website installieren.

## <a name="prompts-for-authentication"></a>Aufforderung zur Authentifizierung

Bevor Sie die geschützte Datei anzeigen können, muss der Rights Management-Dienst, mit dem die Datei geschützt wurde, bestätigen, dass Sie zum Anzeigen der Datei berechtigt sind. Dazu überprüft der Dienst Ihren Benutzernamen und Ihr Kennwort. In einigen Fällen können Ihre Anmeldeinformationen zwischengespeichert sein, und Sie sehen keine Eingabeaufforderung, um sich anzumelden. In anderen Fällen werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben.

Wenn Ihre Organisation kein cloudbasiertes Konto hat, das Sie verwenden können (für Microsoft 365 oder Azure) und keine entsprechende lokale Version (AD RMS) verwendet, haben Sie zwei Möglichkeiten:

- Wenn Sie eine geschützte E-Mail erhalten haben, folgen Sie den Anweisungen zur Anmeldung bei Ihrem sozialen Netzwerk als Identitätsanbieter (z.B. Google bei einem Gmail-Konto), oder beantragen Sie eine einmalige Kennung.

- Sie können ein kostenloses Konto beantragen, bei dem Sie sich mit Ihren Anmeldeinformationen anmelden können. Auf diese Weise können Sie Dokumente öffnen, die von Rights Management geschützt werden. Klicken Sie zur Beantragung eines Kontos auf den Link [RMS for Individuals](https://go.microsoft.com/fwlink/?LinkId=309469). Verwenden Sie nicht Ihre private E-Mail-Adresse, sondern die Ihrer Organisation. 

## <a name="to-view-and-use-a-protected-document"></a>Anzeigen und Verwenden von geschützten Dokumenten

1. Öffnen Sie die geschützte Datei (indem Sie z. B. auf die Datei doppelklicken oder auf den Link zur Datei klicken). Wenn Sie zum Auswählen einer App aufgefordert werden, wählen Sie **Azure Information Protection-Viewer** aus. 

2. Wenn eine Seite zum **Anmelden** oder **Registrieren** angezeigt wird: Klicken Sie auf **Anmelden**, und geben Sie Ihre Anmeldeinformationen ein. Wenn Ihnen die geschützte Datei als Anlage gesendet wurde, müssen Sie die gleiche E-Mail-Adresse angeben, die zum Senden der Datei verwendet wurde.
    
    Wenn Sie nicht über ein akzeptiertes Konto verfügen, finden Sie weitere Informationen auf dieser Seite im Abschnitt [Aufforderung zur Authentifizierung](#prompts-for-authentication).

3. Eine schreibgeschützte Version der Datei wird im **Azure Information Protection-Viewer** geöffnet. Wenn Sie über entsprechende Berechtigungen verfügen, können Sie die Datei drucken und bearbeiten. 

    Sie können Ihre Berechtigungen für die Datei überprüfen, indem Sie auf **Berechtigungen** klicken. Über das Dialogfeld **Berechtigungen** können Sie auch den Dateibesitzer identifizieren, um ihn zu kontaktieren, falls Sie eine neue Version der Datei mit zusätzlichen Berechtigungen anfordern möchten.
    
    Ausführlichere Informationen zu den Berechtigungen und den jeweils enthaltenen Nutzungsrechten, finden Sie unter [In Berechtigungsstufen enthaltene Rechte](../configure-usage-rights.md#rights-included-in-permissions-levels).

4. Klicken Sie zum Bearbeiten der Datei auf **Speichern unter**, wodurch Sie die geschützte Datei mit der ursprünglichen Dateierweiterung speichern können. Sie können die Datei dann mithilfe der Anwendung bearbeiten, die diesem Dateityp zugeordnet ist. Zu diesem Zeitpunkt werden die Bezeichnung und der Schutz der Datei entfernt.
    
    Da der Viewer für geschützte Dateien vorgesehen ist, beachten Sie, dass die Schaltfläche **Speichern unter** nur für geschützte Dateien aktiviert ist.
    
5. Wenn Sie die Datei nicht weiter bearbeiten möchten, klicken Sie im Datei-Explorer mit der rechten Maustaste, um die Bezeichnung erneut anzuwenden. Durch diesen Vorgang wird der Schutz erneut angewendet.

6. Wenn Sie weitere geschützte Dateien öffnen müssen, können Sie über den Viewer direkt zu ihnen navigieren, indem Sie die Option **Öffnen** verwenden. Ihre ausgewählte Datei ersetzt die ursprüngliche Datei im Viewer. 

> [!TIP]
> Wenn die geschützte Datei nicht geöffnet wird und der vollständige Azure Information Protection Client installiert ist, versuchen Sie es mit der Option **Einstellungen zurücksetzen**. Klicken Sie dazu in einer Office-App auf **Schützen** > **Hilfe und Feedback** > **Einstellungen zurücksetzen**. 
> 
> [Weitere Informationen zur Option „Einstellungen zurücksetzen“](client-admin-guide.md#more-information-about-the-reset-settings-option)

## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

