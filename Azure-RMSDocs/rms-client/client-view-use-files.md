---
title: "Anzeigen und Verwenden von mit dem AIP-Client geschützten Dokumenten"
description: "Anweisungen zum Anzeigen und Verwenden eines geschützten Dokuments, das die Installation des Azure Information Protection-Clients erfordert."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6d73a8651b3bea3b8773b4aba49c7d2e85873a80
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="view-and-use-files-that-have-been-protected-by-rights-management" class="xliff"></a>

# Anzeigen und Verwenden der durch Rights Management geschützten Dateien

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Sie können ein geschütztes Dokument beliebig oft anzeigen, indem Sie es öffnen. Sie können z. B. einfach auf eine Anlage einer E-Mail klicken oder im Datei-Explorer auf eine Datei doppelklicken. Alternativ können Sie auch auf den Link zu einer Datei klicken.

Wenn die Dateien nicht sofort geöffnet werden, kann eventuell der **Azure Informationen Protection-Viewer** Abhilfe leisten. Dieser Viewer kann geschützte Textdateien, geschützte Bilddateien geschützte PDF-Dateien und alle Dateien mit der Erweiterung **PFILE** öffnen.

Dieser Viewer wird automatisch als Teil des Azure Information Protection-Clients oder separat installiert. Sie können sowohl den Client als auch den Viewer über die Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) auf der Microsoft-Website installieren. Weitere Informationen zum Installieren des Clients finden Sie unter [Herunterladen und Installieren des Azure Information Protection-Clients](install-client-app.md).

> [!NOTE]
> Obwohl das Installieren des Clients mehr Funktionalität bietet, sind lokale Administratorberechtigungen erforderlich und die volle Funktionalität erfordert einen entsprechenden Dienst für Ihre Organisation:
> 
> - Azure Information Protection
> 
> - Azure Rights Management
> 
> - Active Directory-Rechteverwaltungsdienste 
> 
> Installieren Sie den Viewer, wenn Ihnen von einer Person aus einer anderen Organisation ein geschütztes Dokument gesendet wurde oder Sie nicht über lokale Administratorrechte auf Ihrem PC verfügen.

Um ein geschütztes Dokument öffnen zu können, muss es sich um eine RMS-fähige Anwendung handeln. Zu RMS-fähigen Anwendungen zählen beispielsweise Office-Apps und der Azure Informationen Protection-Viewer. Eine Liste der Anwendungen nach Typ und unterstützten Geräten finden Sie in der Tabelle [RMS-fähige Anwendungen](../get-started/requirements-applications.md#rms-enlightened-applications).  
<a id="messagerpmsg-as-an-email-attachment" class="xliff"></a>

## Message.rpmsg als E-Mail-Anhang

Wenn in einer E-Mail **message.rpmsg** als Dateianhang angezeigt wird, handelt es sich nicht um ein geschütztes Dokument, sondern um eine geschützte, als Anhang angezeigte E-Mail-Nachricht. Sie können den Azure Information Protection-Viewer nicht bei Windows verwenden, um diese geschützte E-Mail-Nachricht auf Ihrem Windows-PC anzuzeigen. Stattdessen benötigen Sie eine E-Mail-Anwendung für Windows, die Rights Management-Schutz wie etwa bei Office Outlook unterstützt. Alternativ können Sie Outlook im Web verwenden.

Wenn Sie jedoch ein iOS- oder Android-Gerät besitzen, können Sie diese geschützten E-Mail-Nachrichten mit der Azure Information Protection-App öffnen. Sie können die App für diese mobilen Geräte über die Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) auf der Microsoft-Website installieren.

<a id="prompts-for-authentication" class="xliff"></a>

## Aufforderung zur Authentifizierung

Bevor Sie die geschützte Datei anzeigen können, muss der Rights Management-Dienst, mit dem die Datei geschützt wurde, bestätigen, dass Sie zum Anzeigen der Datei berechtigt sind. Dazu überprüft der Dienst Ihren Benutzernamen und Ihr Kennwort. In einigen Fällen können Ihre Anmeldeinformationen zwischengespeichert sein, und Sie sehen keine Eingabeaufforderung, in der nach diesen Informationen gefragt wird. In anderen Fällen werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben.

Wenn Ihre Organisation kein cloudbasiertes Konto besitzt (für Office 365 oder Azure), das Sie verwenden können, und keine vergleichbare lokale Version (AD RMS) verwendet, können Sie ein kostenloses Konto beantragen, für das Ihre Anmeldeinformationen akzeptiert werden, sodass Sie Dateien öffnen können, die mithilfe von Rights Management geschützt wurden:

-   Um dieses Konto zu beantragen, klicken Sie auf den Link, um [RMS for Individuals](http://go.microsoft.com/fwlink/?LinkId=309469)zu beantragen.
    
    Wenn Sie sich anmelden, verwenden Sie Ihre Unternehmens-E-Mail-Adresse anstelle einer privaten E-Mail-Adresse. Wenn Sie sich anmelden, weil Sie per E-Mail eine geschützte Dateianlage erhalten haben, verwenden Sie die E-Mail-Adresse, die zum Senden der E-Mail-Nachricht an Sie verwendet wurde.
    
-   Weitere Informationen finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md).

<a id="to-view-and-use-a-protected-document" class="xliff"></a>

## Anzeigen und Verwenden von geschützten Dokumenten

1. Öffnen Sie die geschützte Datei (indem Sie z. B. auf die Datei doppelklicken oder auf den Link zur Datei klicken). Wenn Sie zum Auswählen einer App aufgefordert werden, wählen Sie **Azure Information Protection-Viewer** aus. 

2. Wenn eine Seite zum **Anmelden** oder **Registrieren** angezeigt wird: Klicken Sie auf **Anmelden**, und geben Sie Ihre Anmeldeinformationen ein. Wenn Ihnen die geschützte Datei als Anlage gesendet wurde, müssen Sie die gleiche E-Mail-Adresse angeben, die zum Senden der Datei verwendet wurde.
    
    Wenn Sie nicht über ein akzeptiertes Konto verfügen, finden Sie weitere Informationen auf dieser Seite im Abschnitt [Aufforderung zur Authentifizierung](#prompts-for-authentication). Melden Sie sich für ein kostenloses Konto an, und kehren Sie zu diesen Anweisungen zurück.

3. Eine schreibgeschützte Version der Datei wird im **Azure Information Protection-Viewer** geöffnet. Wenn Sie über entsprechende Berechtigungen verfügen, können Sie die Datei drucken und bearbeiten. 

    Sie können Ihre Berechtigungen für die Datei überprüfen, indem Sie auf **Berechtigungen** klicken. Über das Dialogfeld **Berechtigungen** können Sie auch den Dateibesitzer identifizieren, um ihn zu kontaktieren, falls Sie eine neue Version der Datei mit zusätzlichen Berechtigungen anfordern möchten.
    
    Ausführlichere Informationen zu den Berechtigungen und den jeweils enthaltenen Nutzungsrechten, finden Sie unter [In Berechtigungsstufen enthaltene Rechte](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Klicken Sie zum Bearbeiten der Datei auf **Speichern unter**, wodurch Sie die Datei ohne Schutz mit der ursprünglichen Dateierweiterung speichern können. Sie können die Datei dann mithilfe der Anwendung bearbeiten, die diesem Dateityp zugeordnet ist.

5. Wenn Sie weitere geschützte Dateien öffnen müssen, können Sie über den Viewer direkt zu ihnen navigieren, indem Sie die Option **Öffnen** verwenden. Ihre ausgewählte Datei ersetzt die ursprüngliche Datei im Viewer. 

> [!TIP]
> Wenn die geschützte Datei nicht geöffnet wird, laden Sie das [RMS Analyzer-Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437) herunter und verwenden es. Befolgen Sie die Anweisungen in dem Tool und suchen Sie nach Problemen auf Ihrem Computer, die das Öffnen des geschützten Dokuments verhindern können.


<a id="other-instructions" class="xliff"></a>

## Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]