---
title: "Bereitstellen Ihrer Anwendung – AIP"
description: "Dieses Thema beschreibt und führt Sie durch die Bereitstellung Ihrer Anwendung."
keywords: deploy, RMS, AIP
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 03/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 9275bce1e56107648905875c19b2e4e78a05afe6
ms.sourcegitcommit: 93124ef58e471277c7793130f1a82af33dabcea9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2018
---
# <a name="deploy-into-production"></a>Bereitstellen in der Produktion

Dieses Thema führt Sie durch den Bereitstellungsprozess für Ihre für Azure Information Protection (AIP) / Rights Management Services (RMS) aktivierte Anwendung.

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Anfordern einer Integrationsvereinbarung für Information Protection (Information Protection Integration Agreement, IPIA)
Bevor Sie eine mit AIP/RMS entwickelte Anwendung freigeben können, müssen Sie eine formelle Vereinbarung mit Microsoft beantragen und abschließen.

### <a name="begin-the-process"></a>Beginn des Prozesses
Beantragen Sie Ihre IPIA, indem Sie eine E-Mail mit folgenden Informationen an **IPIA@microsoft.com** senden:

**Betreff:** Anfordern einer IPIA für *Name des Unternehmens*

Geben Sie im E-Mail-Text folgende Informationen ein:
- Anwendungs- oder Produktname
- Vor- und Nachnamen des Antragstellers
- E-Mail-Adresse des Antragstellers

### <a name="next-steps"></a>Nächste Schritte
Nach Erhalt Ihrer IPIA-Anforderung senden wir Ihnen ein Formular (als Word-Dokument).
Überprüfen Sie die Vertragsbedingungen der IPIA, und senden Sie das Formular mit folgenden Informationen an **IPIA@microsoft.com** zurück:
- Offizieller Name des Unternehmens
- Bundesstaat/Provinz (USA/Kanada) oder Land der Gründung oder Hauptverwaltung des Unternehmens
- URL des Unternehmens
- E-Mail-Adresse der Kontaktperson
- Weitere Unternehmensanschriften (optional)
- Name der Unternehmensanwendung
- Kurze Beschreibung der Anwendung
- *Azure-Mandanten-ID*
- *App-ID* der Anwendung
- Unternehmenskontakte, E-Mail-Adressen und Telefonnummern zur Kommunikation in kritischen Situationen

### <a name="completing-the-agreement"></a>Abschließen der Vereinbarung
Nachdem wir Ihr Formular erhalten haben, senden wir Ihnen den Link zur endgültigen IPIA zur digitalen Unterzeichnung. Wenn Sie das Formular unterzeichnet haben, wird es vom zuständigen Microsoft-Vertreter ebenfalls unterzeichnet, womit die Vereinbarung abgeschlossen ist.

### <a name="already-have-a-signed-ipia"></a>Haben Sie bereits eine IPIA unterzeichnet?
Wenn Sie bereits über eine unterzeichnete IPIA verfügen und eine neue *App-ID* für eine zu veröffentlichende Anwendung hinzufügen möchten, senden Sie eine E-Mail an **IPIA@microsoft.com**, und geben Sie folgende Informationen an:
- Name der Unternehmensanwendung
- Kurze Beschreibung der Anwendung
- Azure-Mandanten-ID (auch wenn es die gleiche ist wie zuvor)
- App-ID der Anwendung
- Unternehmenskontakte, E-Mail-Adressen und Telefonnummern zur Kommunikation in kritischen Situationen

Nach dem Senden der E-Mail kann es bis zu 72 Stunden dauern, bis der Empfang bestätigt wird.

## <a name="deploying-to-the-client-environment"></a>Bereitstellen in der Clientumgebung

Um Ihre mit den Tools Azure Information Protection (AIP) / Rights Management Services (RMS) erstellte Anwendung bereitzustellen, müssen Sie den RMS Client 2.1 auf dem Computer des Endbenutzers bereitstellen.

### <a name="rms-client-21"></a>RMS Client 2.1
Der RMS Client 2.1 ist dafür konzipiert, den Zugriff auf und die Verwendung von Informationen zu schützen, die durch über AIP/RMS aktivierte Anwendungen fließen – unabhängig davon, ob diese und lokal oder in einem Microsoft-Rechenzentrum installiert sind.

Der RMS Client 2.1 ist keine Komponente des Windows-Betriebssystems. Der Client wird als optionaler Download ausgeliefert, der nach Bestätigung und Annahme der zugehörigen Lizenzvereinbarung kostenlos mit Ihrer Anwendung verteilt werden kann.

> [!IMPORTANT]
> Der RMS Client 2.1 ist architekturspezifisch und muss der Architektur des Zielbetriebssystems entsprechen.


## <a name="rms-client-21-installation-options"></a>Installationsoptionen für den RMS Client 2.1

### <a name="creating-your-deployment-package"></a>Erstellen des Bereitstellungspakets

Es wird empfohlen, das RMS Client-Installationspaket mit Ihrer Anwendung oder Lösung und dem bevorzugten Installationsverfahren zu packen. Der RMS-Client kann kostenlos zusammen mit anderen Anwendungen und Lösungen weiterverteilt werden.

Sie können den RMS Client 2.1 interaktiv durch Starten des RMS Client 2.1-Installationsprogramms oder im Hintergrund installieren. Die Integrationsschritte sind wie folgt:

-   Herunterladen des RMS-Client 2.1-Installationsprogramms
-   Integrieren des RMS Client 2.1-Installationsprogramms zur Ausführung im Anwendungsinstallationsprogramm

Ein Beispiel für die Integration des RMS Client 2.1 in Ihre Anwendung ist das [Rights Protected Folder Explorer](https://technet.microsoft.com/en-us/library/rights-protected-folder-explorer(v=ws.10).aspx)-Paket. Installieren Sie es selbst, um den Ansatz zu verstehen.

### <a name="make-rms-client-21-a-pre-requisite-for-your-application-install"></a>Festlegen von RMS Client 2.1 als Voraussetzung für die Installation der Anwendung

In diesem Fall erstellen Sie eine Voraussetzung, z.B. dass die Installation der Anwendung fehlschlägt, wenn RMS Client 2.1 nicht auf dem Computer des Endbenutzers vorhanden ist.

Wenn der Client nicht vorhanden ist, wird eine Fehlermeldung bereitgestellt, die den Benutzer darüber informiert, wo eine Kopie des RMS Client 2.1 heruntergeladen werden kann.

Wenn der Client vorhanden ist wird die Anwendungsinstallation fortgesetzt.

## <a name="enabling-azure-information-protection-services-with-your-application"></a>Aktivieren von Azure Information Protection-Diensten für Ihre Anwendung

> [!NOTE]
> Wenn Sie zum neuen ADAL-Modell für die Authentifizierung migriert haben, müssen Sie **SIA** nicht installieren. Weitere Informationen finden Sie unter [ADAL-Authentifizierung für Ihre RMS-fähige Anwendung](adal-auth.md).
> Außerdem können Sie **Ihre Anwendung für Windows 10 zertifizieren**: Durch Aktualisieren der Anwendung für die Verwendung der ADAL-Authentifizierung anstelle des Microsoft Online-Anmelde-Assistenten verfügen Sie und Ihre Kunden über folgende Möglichkeiten: Nutzen der Multi-Factor Authentication, Installieren des RMS Client 2.1 ohne Administratorrechte auf dem Computer

Damit Endbenutzer Information Protection-Dienste nutzen können, müssen Sie den *Online Services-Anmelde-Assistenten* bereitstellen. Als Entwickler einer Anwendung wissen Sie nicht, ob Endbenutzer Information Protection über RMS (lokal) oder über Azure Information Protection verwenden werden.


> [!IMPORTANT]
> Wenn Sie Ihre Clientanwendung mit einem auf Azure basierenden RMS ausführen, müssen Sie eigene Mandanten erstellen. Weitere Informationen finden Sie unter [Azure RMS-Anforderungen: Cloudabonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).
> Weitere Informationen zur Ausführung mit Azure RMS finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

-   Laden Sie den [Microsoft Online Services-Anmeldeassistenten](http://www.microsoft.com/en-us/download/details.aspx?id=28177) aus dem Microsoft Download Center herunter.
-   Stellen Sie sicher, dass die Bereitstellung einer rechtefähigen Anwendung eine Überprüfung der Voraussetzungen für diese Dienstauswahl enthält.
-   Informationen zu eigenen Tests und zur Verwendung des Onlinediensts durch die Endbenutzer finden Sie im TechNet-Thema [Konfigurieren von Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Sie benötigen auch dieses Handbuch zum Konfigurieren Ihrer App: [Konfigurieren Ihrer App Service-Anwendung für die Azure Active Directory-Anmeldung](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication).

Weitere Informationen zum Ermöglichen der Verwendung von RMS für Azure Rights Management Services durch Ihre Anwendung finden Sie im Thema zum [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Anwendung](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="related-topics"></a>Verwandte Themen

* [Microsoft Online Services-Anmeldeassistent](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Konfigurieren von Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Anwendung](how-to-use-file-api-with-aadrm-cloud.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
