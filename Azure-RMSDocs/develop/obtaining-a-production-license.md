---
# required metadata

title: Bezug einer Produktionslizenz | Azure RMS
description: Zum Freigeben einer mit dem RMS SDK 2.1 entwickelten Anwendung ist ein Produktionslizenzvertrag erforderlich.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6749817E-FF34-4384-BF63-39AEA5C372CA
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Bezug einer Produktionslizenz

Bevor Sie eine mithilfe der Rights Management Services SDK 2.1 entwickelte Anwendung freigeben können, müssen Sie einen Produktionslizenzvertrag beantragen, um ein Produktionszertifikat zu beziehen.

> [!IMPORTANT]
> Wenn Sie Ihre Clientanwendung mit einem auf Azure basierenden RMS ausführen, müssen Sie einen Azure RMS-Mandanten anfordern. Senden Sie eine E-Mail mit Ihrer Mandantenanforderung an <rmcstbeta@microsoft.com>.

Weitere Informationen zur Ausführung mit Azure RMS finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).


Das Produktionszertifikat und das Präproduktionszertifikat haben eine ähnliche Funktion, sind aber für unterschiedliche Umgebungen vorgesehen. Beide enthalten eine Zertifikatkette mit einem Microsoft-Zertifikat an der Stammzertifizierungsstelle. Das Präproduktionszertifikat wird jedoch nur zum Entwickeln einer RMS-Anwendung verwendet. Das Produktionszertifikat wird in Umgebung nach der Veröffentlichung verwendet. Mit dem Produktionszertifikat und dem zugehörigen privaten Schlüssel erstellen und signieren Sie ein Manifest, das identifiziert, welche Dateien in den Prozessbereich der Anwendung geladen werden können oder müssen.

Weitere Informationen über Schlüssel finden Sie unter [Testen Ihrer rechtlich geschützten Anwendung](running-your-first-application.md).

Sie können das Zertifikat beziehen, indem Sie einen Produktionslizenzvertrag beantragen.

## Anfordern eines Produktionslizenzvertrags

-   Senden Sie eine E-Mail mit folgenden Angaben an [RMLA@microsoft.com](mailto:rmla@microsoft.com):

    -   Vollständiger Firmenname

    -   Physische Anschrift des Unternehmens (einschließlich Ort, Bundesland, Land oder Region und Postleitzahl)
    -   Postanschrift des Unternehmens (einschließlich Ort, Bundesland, Land oder Region und Postleitzahl)
    -   Telefon- und Faxnummer des Unternehmens
    -   URL des Unternehmens
    -   Land oder Region der Gesellschaft
    -   Anwendung oder Produktname
    -   Vor- und Nachnamen des Antragstellers
    -   Titel oder Position des Antragstellers
    -   E-Mail-Adresse des Antragstellers

    Obwohl ein E-Mail-Konto nicht zwingend erforderlich ist, erfolgt die Kommunikation im Rahmen des Anwendungsprozesses in der Regel per E-Mail. Sie können unter Microsoft Outlook.com ein kostenloses E-Mail-Konto erstellen. Wenn Sie kein E-Mail-Konto haben und keins erstellen möchten, können Sie an folgende Adresse einen maschinenschriftlichen Antrag senden:

    `Active Directory Rights Management License Agreements (ADRMLA)`

    `Microsoft Corporation`

    `One Microsoft Way`

    `Redmond, WA 98052-6399`

    Gehen Sie zum Beantragen eines Vertrags wie Folgt vor:

    -   Senden Sie in Englisch die im Vertrag aufzuführenden Angaben.
    -   Senden Sie alle angeforderten Informationen. Fehlende oder unvollständige Informationen können die Verarbeitung Ihres Antrags verzögern.

    Das Active Directory Rights Management Licensing Agreement (ADRMLA)-Team antwortet binnen drei Werktagen auf Ihren per E-Mail gesendeten Antrag. Die Beantwortung von per Post gesendeten Anträgen dauert länger. Die Antwort enthält das Formular für den Lizenzvertrag und weitere Anweisungen. Lesen Sie den vollständigen Vertrag, unterzeichnen Sie ihn, und senden Sie alle Seiten an das ADRMLA-Team zurück. Bitte ändern Sie weder die Schriftarten noch die Formatierung der Absätze des Lizenzvertrags.

    Beachten Sie unbedingt die vom ADRMLA-Team erhaltenen Anweisungen. In den Anweisungen sind die digitalen Informationen aufgeführt, die Sie in Ihrem Zertifikatsantrag angeben müssen. Indem Sie die schrittweisen Anweisungen befolgen, vermeiden Sie Verzögerungen.

    Das ADRMLA-Team leitet das daraufhin erstellte Produktionszertifikat an Sie weiter. Das Zertifikat wird basierend auf dem Lizenzvertrag und den von Ihnen bereitgestellten digitalen Informationen (einschließlich eines öffentlichen Schlüssels) erstellt. Beachten Sie, dass die Zusendung Ihres Zertifikats durch das ADRMLA-Team bis zu 15 Werktage dauern kann. Die Zusendung per Post kann länger dauern.

## Verwandte Themen

* [Vorgehensweise](how-to-use-msipc.md)
* [Testen Ihrer rechtlich geschützten Anwendung](running-your-first-application.md)
 

 





<!--HONumber=Apr16_HO4-->


