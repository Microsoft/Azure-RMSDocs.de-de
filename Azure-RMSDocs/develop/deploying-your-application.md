---
# required metadata

title: Bereitstellen der Anwendung | Azure RMS
description: Dieses Thema beschreibt und führt Sie durch die Bereitstellungsoptionen für Ihre Rechte-fähige Anwendung
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Bereitstellen in der Präproduktion


Dieses Thema beschreibt und führt Sie durch die Bereitstellungsoptionen für die rechtlich geschützte Anwendung.

## Anfordern eines Produktionslizenzvertrags

 Bevor Sie eine mithilfe des Rights Management Services SDK 2.1 entwickelte Anwendung freigeben können, müssen Sie einen Produktionslizenzvertrag beantragen, um ein Produktionszertifikat zu erhalten.

> [!IMPORTANT]
> Wenn Sie Ihre Clientanwendung mit einem auf Azure basierenden RMS ausführen, müssen Sie eigene Mandanten erstellen. Weitere Informationen finden Sie unter [Azure RMS-Anforderungen: Cloudabonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).
> Weitere Informationen zur Ausführung mit Azure RMS finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

Sie können das Zertifikat beziehen, indem Sie einen Produktionslizenzvertrag beantragen.

Senden Sie eine E-Mail mit folgenden Angaben an [RMLA@microsoft.com](mailto:rmla@microsoft.com):

- Vollständiger Firmenname
- Physische Anschrift des Unternehmens (einschließlich Ort, Bundesland, Land oder Region und Postleitzahl)
- Postanschrift des Unternehmens (einschließlich Ort, Bundesland, Land oder Region und Postleitzahl)
- Telefon- und Faxnummer des Unternehmens
- URL des Unternehmens
- Land oder Region der Gesellschaft
- Anwendung oder Produktname
- Vor- und Nachnamen des Antragstellers
- Titel oder Position des Antragstellers
- E-Mail-Adresse des Antragstellers

Obwohl ein E-Mail-Konto nicht zwingend erforderlich ist, erfolgt die Kommunikation im Rahmen des Anwendungsprozesses in der Regel per E-Mail. Sie können unter Microsoft Outlook.com ein kostenloses E-Mail-Konto erstellen. Wenn Sie kein E-Mail-Konto haben und keins erstellen möchten, können Sie an folgende Adresse einen maschinenschriftlichen Antrag senden:

      Active Directory Rights Management License Agreements (ADRMLA)

      Microsoft Corporation

      One Microsoft Way

      Redmond, WA 98052-6399

Gehen Sie zum Beantragen eines Vertrags wie Folgt vor:
- Senden Sie in Englisch die im Vertrag aufzuführenden Angaben.
- Senden Sie alle angeforderten Informationen. Fehlende oder unvollständige Informationen können die Verarbeitung Ihres Antrags verzögern.

Das Active Directory Rights Management Licensing Agreement (ADRMLA)-Team antwortet binnen drei Werktagen auf Ihren per E-Mail gesendeten Antrag. Die Beantwortung von per Post gesendeten Anträgen dauert länger. Die Antwort enthält das Formular für den Lizenzvertrag und weitere Anweisungen. Lesen Sie den vollständigen Vertrag, unterzeichnen Sie ihn, und senden Sie alle Seiten an das ADRMLA-Team zurück. Bitte ändern Sie weder die Schriftarten noch die Formatierung der Absätze des Lizenzvertrags.

Beachten Sie unbedingt die vom ADRMLA-Team erhaltenen Anweisungen. In den Anweisungen sind die digitalen Informationen aufgeführt, die Sie in Ihrem Zertifikatsantrag angeben müssen. Indem Sie die schrittweisen Anweisungen befolgen, vermeiden Sie Verzögerungen.

Das ADRMLA-Team leitet das daraufhin erstellte Produktionszertifikat an Sie weiter. Beachten Sie, dass die Zusendung Ihres Zertifikats durch das ADRMLA-Team bis zu 15 Werktage dauern kann. Die Zusendung per Post kann länger dauern.


## Installationsoptionen und Voraussetzungen für Rights Management Service Client 2.1

Sofern Sie RMS SDK 2.1 genutzt haben, muss Active Directory Rights Management Services Client 2.1 auf dem Endbenutzercomputer bereitgestellt werden.

### RMS Client 2.1

Der RMS Client 2.1 ist eine Software, die entwickelt wurde, damit auf Ihren Clientcomputern der Zugriff auf und die Verwendung von Informationen möglich ist, die durch Anwendungen fließen, die AD RMS verwenden und lokal oder in einem Microsoft-Rechenzentrum installiert sind.

Der RMS Client 2.1 ist keine Komponente des Windows-Betriebssystems. Der RMS Client 2.1 wird als optionaler Download bereitgestellt, der mit Bestätigung und Annahme des Lizenzvertrags mit der Software von Drittanbietern frei verteilt werden kann, um Clients Zugriff auf Inhalte zu ermöglichen, die durch Nutzung und Bereitstellung von RMS-Servern in Ihrer Umgebung geschützt wurden.


> [!IMPORTANT] Die AD RMS-Client 2.1-Architektur ist speziell und muss der Architektur des Zielbetriebssystems entsprechen.


## Installationsoptionen für den RMS Client 2.1

-   **Weiterverbreiten des RMS Client 2.1**

    Es wird empfohlen, das RMS-Client-Installationspaket mit Ihrer Anwendung oder Lösung mithilfe des bevorzugten Installationsverfahrens zu packen. Der RMS-Client kann kostenlos zusammen mit anderen Anwendungen und IT-Lösungen weiterverbreitet und gebündelt werden.

    Sie können den RMS Client 2.1 interaktiv durch Starten des RMS Client 2.1-Installationsprogramms oder im Hintergrund installieren. Die Integrationsschritte sind wie folgt:

    -   Herunterladen des RMS-Client 2.1-Installationsprogramms
    -   Integrieren des RMS Client 2.1-Installationsprogramms in das Anwendungsinstallationsprogramm

    Zwei gute Beispiele für die Integration des RMS Client 2.1 in Ihre Anwendung sind das RMS SDK 2.1-Installationspaket und das Right Protected Folder Explorer-Paket. Installieren Sie sie selbst, um den Ansatz zu verstehen.

-   **Festlegen von RMS Client 2.1 als Voraussetzung für die Installation der Anwendung**

    In diesem Fall erstellen Sie eine Voraussetzung, z.B. dass die Installation der Anwendung fehlschlägt, wenn RMS Client 2.1 nicht auf dem Computer des Endbenutzers vorhanden ist.

    Wenn der Client nicht vorhanden ist, wird eine Fehlermeldung bereitgestellt, die den Benutzer darüber informiert, wo eine Kopie des RMS Client 2.1 heruntergeladen werden kann.

    Wenn der Client vorhanden ist wird die Anwendungsinstallation fortgesetzt.

## Aktivieren von Azure Rights Management Services mit Ihrer Anwendung

> [!NOTE]
> Wenn Sie in das neue ADAL-Modell für die Authentifizierung migriert haben, müssen Sie SIA nicht installieren. Weitere Informationen finden Sie unter [ADAL-Authentifizierung für Ihre RMS-fähige Anwendung](adal-auth.md).
> Außerdem können Sie **Ihre Anwendung für Windows 10 zertifizieren**: Durch Aktualisieren der Anwendung für die Verwendung der ADAL-Authentifizierung anstelle des Microsoft Online-Anmelde-Assistenten verfügen Sie und Ihre Kunden über folgende Möglichkeiten: Nutzen der Multi-Factor Authentication, Installieren des RMS Client 2.1 ohne Administratorrechte auf dem Computer


Damit Endbenutzer Azure Rights Management Services nutzen können, müssen Sie den *Online Services-Anmelde-Assistenten* bereitstellen. Als Anwendungsentwickler wissen Sie nicht, ob der Endbenutzer RMS (lokal) oder Azure Rights Management Services (Clouddienst) verwenden wird.


> [!IMPORTANT]
> Zum Ausführen der RMS SDK 2.1-Clientanwendung mit Azure RMS müssen Sie eigene Mandanten erstellen. Weitere Informationen finden Sie unter [Azure RMS-Anforderungen: Cloudabonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).

-   Laden Sie den [Microsoft Online Services-Anmeldeassistenten](http://www.microsoft.com/en-us/download/details.aspx?id=28177) aus dem Microsoft Download Center herunter.
-   Stellen Sie sicher, dass die Bereitstellung einer rechtefähigen Anwendung eine Überprüfung der Voraussetzungen für diese Dienstauswahl enthält.
-   Informationen zu eigenen Tests und zur Verwendung des Onlinediensts durch die Endbenutzer finden Sie im TechNet-Thema [Konfigurieren von Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Weitere Informationen zum Ermöglichen der Verwendung von RMS für Azure Rights Management Services durch Ihre Anwendung finden Sie im Thema zum [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Anwendung](how-to-use-file-api-with-aadrm-cloud.md).

## Verwandte Themen

* [Microsoft-Onlinedienst-Anmeldungs-Assistent](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Konfigurieren von Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Anwendung](how-to-use-file-api-with-aadrm-cloud.md)
 

 


<!--HONumber=Jun16_HO2-->


