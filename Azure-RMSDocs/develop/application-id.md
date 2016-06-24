---
# required metadata

title: Gewusst wie&#58; Abrufen einer Azure-Anwendungs-ID | Azure RMS
description: Um eine RMS-fähige App mit dem MS RMS SDK 4.2 erstellen zu können, müssen Sie eine Dienstnutzungsvereinbarung mit dem RMS-Team treffen.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0fe9dc-bc91-4018-b28d-2db293a3eaa2
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gewusst wie: Abrufen einer Azure-Anwendungs-ID

Um eine RMS-fähige App mit dem MS RMS SDK 4.2 erstellen zu können, müssen Sie eine Dienstnutzungsvereinbarung mit dem RMS-Team treffen.

## Übersicht

Zum Erstellen und Freigeben einer RMS-fähigen App mit dem MS RMS SDK 4.2 ist erforderlich, dass Sie auch eine Dienstnutzungsvereinbarung mit dem RMS-Team erstellen. Diese Vereinbarung, die auch als Rights Management License Agreement (RMLA) bezeichnet wird, ist Ihre Orientierungshilfe zum Vertrag über den Schutz von Inhalten, den Sie im Namen der Benutzer bzw. der Eigentümer des Inhalts durch die Verhaltensweisen (Einhaltung von Geschäftsregeln) Ihrer App Befolgung einhalten werden. Ihr Vertrag mit dem RMS-Team als Ersteller einer RMS-fähigen App wird durch das Vorhandensein einer „Azure-Anwendungs-ID“ durchgesetzt, welche diese Vereinbarung repräsentiert und Ihre App in die Lage versetzt, sich mit dem Azure AD-Authentifizierungsdienst zu verbinden.

## Process

Gehen Sie wie folgt vor, um Ihre App-ID zu erstellen und Ihre Nutzungsvereinbarung mit dem RMS-Team zu unterzeichnen.

-   Befolgen Sie die Hinweise im Thema [Erstellen einer App-ID in Azure](https://msdn.microsoft.com/en-us/library/azure/dn132599.aspx), um Ihre App-ID zu erstellen.
-   Schreiben Sie das RMS-Team an, um den RMLA-Prozess zu initiieren, indem Sie Ihre „App-ID“ an <askipteam@microsoft.com> senden..
-   Unterzeichnen Sie die RMLA, und senden Sie sie zurück an das RMS-Team.
-   Nachdem Sie eine unterzeichnete RMLA besitzen, sollten Sie die Anwendungs-ID beim Aufruf der Authentifizierungsbibliothek im *ClientID*-Parameter übergeben.

    Dies zeigt der Authentifizierungsaufruf in unserem Thema [Codebeispiele iOS/OS X](ios-os-x-code-examples.md).


    // Abrufen eines Tokens mithilfe von ADAL
        [context acquireTokenWithResource:authenticationParameters.resource
                                 clientId:appClientId
                              redirectUri:redirectURI
                                   userId:authenticationParameters.userId
                          completionBlock:^(ADAuthenticationResult *result)



**Hinweis** Wenn das RMS-Team Ihre unterzeichnete RMLA nicht innerhalb von 60 Tagen erhält, wird Ihre App für die Authentifizierung beim Azure-Authentifizierungssystem gesperrt.

 

 

 


<!--HONumber=Apr16_HO4-->


