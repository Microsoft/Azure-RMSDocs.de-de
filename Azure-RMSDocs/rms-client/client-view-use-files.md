---
title: "Anzeigen und Verwenden von Dateien, die mit Rights Management geschützt wurden | Azure Information Protection"
description: "Anweisungen zum Anzeigen und Verwenden einer geschützten Datei, die die Installation des Azure Information Protection-Clients erfordert."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ce1c7d4c-b5ff-4672-8b9a-a72129bac992
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 364891123720daaacacbea1b382b7d101d75cd1a


---

# <a name="view-and-use-files-that-have-been-protected-by-rights-management"></a>Anzeigen und Verwenden der durch Rights Management geschützten Dateien

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

**[Diese Version des Clients ist eine Vorschau und unterliegt Änderungen.]**

Wenn der [Azure Information Protection-Client auf Ihrem Computer installiert ist](install-client-app.md), können Sie eine geschützte Datei anzeigen, indem Sie sie einfach öffnen. Sie können z. B. einfach auf eine Anlage einer E-Mail klicken oder im Datei-Explorer auf eine Datei doppelklicken. Alternativ können Sie auch auf den Link zu einer Datei klicken.

> [!NOTE]
> Bevor Sie die geschützte Datei anzeigen können, muss der Rights Management-Dienst bestätigen, dass Sie zum Anzeigen der Datei berechtigt sind. Dazu überprüft er Ihren Benutzernamen und Ihr Kennwort. In einigen Fällen können Ihre Anmeldeinformationen zwischengespeichert sein, und Sie sehen keine Eingabeaufforderung, in der nach diesen Informationen gefragt wird. In anderen Fällen werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben.
>
> Wenn Ihre Organisation kein cloudbasiertes Konto besitzt (für Office 365 oder Azure), das Sie verwenden können, und kein AD RMS verwendet, können Sie ein kostenloses Konto beantragen, für das Ihre Anmeldeinformationen akzeptiert werden, sodass Sie Dateien öffnen können, die mithilfe von Rights Management geschützt wurden:
>
> -   Um dieses Konto zu beantragen, klicken Sie auf den Link, um [RMS for Individuals](http://go.microsoft.com/fwlink/?LinkId=309469)zu beantragen.
>
>     Wenn Sie sich anmelden, verwenden Sie Ihre Unternehmens-E-Mail-Adresse anstelle einer privaten E-Mail-Adresse. Wenn Sie sich anmelden, weil Sie per E-Mail eine geschützte Dateianlage erhalten haben, verwenden Sie die E-Mail-Adresse, die zum Senden der E-Mail-Nachricht an Sie verwendet wurde.
> -   Weitere Informationen finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md).

## <a name="to-view-and-use-a-protected-file"></a>So zeigen Sie geschützte Dateien an und verwenden sie

1. Öffnen Sie die geschützte Datei (indem Sie z. B. auf die Datei doppelklicken oder auf den Link zur Datei klicken). Wenn Sie zum Auswählen einer App aufgefordert werden, wählen Sie **Azure Information Protection-Viewer (Vorschau)** aus. 

2. Wenn eine Seite zum **Anmelden** oder **Registrieren** angezeigt wird: Klicken Sie auf **Anmelden**, und geben Sie Ihre Anmeldeinformationen ein. Wenn Ihnen die geschützte Datei als Anlage gesendet wurde, müssen Sie die gleiche E-Mail-Adresse angeben, die zum Senden der Datei verwendet wurde.
    
    Wenn Sie kein akzeptiertes Konto besitzen, finden Sie im Hinweis am Anfang dieser Seite weitere Informationen. Melden Sie sich für ein kostenloses Konto an, und kehren Sie zu diesen Anweisungen zurück.

3. Eine schreibgeschützte Version der Datei wird im **Azure Information Protection-Viewer** geöffnet. Wenn Sie über entsprechende Berechtigungen verfügen, können Sie die Datei drucken und bearbeiten. 

    Sie können Ihre Berechtigungen für die Datei überprüfen, indem Sie auf **Berechtigungen** klicken. Über das Dialogfeld **Berechtigungen** können Sie auch den Dateibesitzer identifizieren, um ihn zu kontaktieren, falls Sie eine neue Version der Datei mit zusätzlichen Berechtigungen anfordern möchten.
    
    Ausführlichere Informationen zu den Berechtigungen und den jeweils enthaltenen Nutzungsrechten, finden Sie unter [In Berechtigungsstufen enthaltene Rechte](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels).

4. Klicken Sie zum Bearbeiten der Datei auf **Speichern unter**, wodurch Sie die Datei ohne Schutz mit der ursprünglichen Dateierweiterung speichern können. Sie können die Datei dann mithilfe der Anwendung bearbeiten, die diesem Dateityp zugeordnet ist.

5. Wenn Sie weitere geschützte Dateien öffnen müssen, können Sie über den Viewer direkt zu ihnen navigieren, indem Sie die Option **Öffnen** verwenden. Ihre ausgewählte Datei ersetzt die ursprüngliche Datei im Viewer. 

> [!TIP]
> Wenn die geschützte Datei nicht geöffnet wird, laden Sie das [RMS Analyzer-Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437) herunter und verwenden es. Befolgen Sie die Anweisungen in dem Tool und suchen Sie nach Problemen auf Ihrem Computer, die das Öffnen des geschützten Dokuments verhindern können.


## <a name="other-instructions"></a>Sonstige Anweisungen
Anweisungen zur Vorgehensweise finden Sie in den folgenden Abschnitten des Azure Information Protection-Benutzerhandbuchs:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


