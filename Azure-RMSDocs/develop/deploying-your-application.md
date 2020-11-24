---
title: Bereitstellen Ihrer Anwendung – AIP
description: Erfahren Sie mehr über den Bereitstellungs Prozess für Ihre Azure Information Protection aktivierte Anwendung (AIP)/Rights Management Services (RMS).
keywords: bereitstellen, RMS, AIP
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 03/13/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4B785564-6839-49ED-A243-E2A6DFF88B2E
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: c600f6e332ec230d73c90faafe8fb602e1d3dd88
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568330"
---
# <a name="deploy-into-production"></a>Bereitstellen in der Produktion

Dieses Thema führt Sie durch den Bereitstellungsprozess für Ihre AIP/RMS-fähige Anwendung (Azure Information Protection/Rights Management Services).

## <a name="request-an-information-protection-integration-agreement-ipia"></a>Anfordern einer Integrationsvereinbarung für Information Protection (Information Protection Integration Agreement, IPIA)
Bevor Sie eine mit AIP/RMS entwickelte Anwendung freigeben können, müssen Sie eine formelle Vereinbarung mit Microsoft beantragen und ausfüllen.

### <a name="begin-the-process"></a>Beginn des Prozesses
Beantragen Sie Ihre IPIA, indem Sie eine E-Mail mit folgenden Informationen an <strong>IPIA@microsoft.com</strong> senden:

**Betreff:** Anfordern einer IPIA für *Name des Unternehmens*

Geben Sie im E-Mail-Text folgende Informationen ein:
- Anwendungs- oder Produktname
- Vor- und Nachnamen des Antragstellers
- E-Mail-Adresse des Antragstellers

### <a name="next-steps"></a>Nächste Schritte
Nach Erhalt Ihrer IPIA-Anforderung senden wir Ihnen ein Formular (als Word-Dokument).
Überprüfen Sie die Vertragsbedingungen der IPIA, und senden Sie das Formular mit folgenden Informationen an <strong>IPIA@microsoft.com</strong> zurück:
- Offizieller Name des Unternehmens
- Bundesstaat/Provinz (USA/Kanada) oder Land/Region der Gründung oder Hauptverwaltung des Unternehmens
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
Wenn Sie bereits über eine unterzeichnete IPIA verfügen und eine neue *App-ID* für eine zu veröffentlichende Anwendung hinzufügen möchten, senden Sie eine E-Mail an <strong>IPIA@microsoft.com</strong>, und geben Sie folgende Informationen an:
- Name der Unternehmensanwendung
- Kurze Beschreibung der Anwendung
- Azure-Mandanten-ID (auch wenn sich diese nicht geändert hat)
- App-ID der Anwendung
- Unternehmenskontakte, E-Mail-Adressen und Telefonnummern zur Kommunikation in kritischen Situationen

Nach dem Senden der E-Mail kann es bis zu 72 Stunden dauern, bis der Empfang bestätigt wird.

## <a name="deploying-to-the-client-environment"></a>Bereitstellen der Clientumgebung

Um Ihre mit den Tools Azure Information Protection (AIP) / Rights Management Services (RMS) erstellte Anwendung bereitzustellen, müssen Sie den RMS Client 2.1 auf dem Computer des Endbenutzers bereitstellen.

### <a name="rmsclient21"></a>RMS Client 2.1
Der RMS-Client 2.1 ist dafür konzipiert, den Zugriff auf und die Verwendung von Informationen zu schützen, die AIP-/RMS-fähige Anwendungen durchlaufen – unabhängig davon, ob diese lokal oder in einem Microsoft-Datencenter installiert sind.

Der RMS-Client 2.1 ist keine Komponente des Windows-Betriebssystems. Der Client wird als optionaler Download bereitgestellt, der nach Bestätigung und Annahme der entsprechenden Lizenzvereinbarung kostenlos mit Ihrer Anwendung verteilt werden kann.

> [!IMPORTANT]
> Der RMS Client 2.1 ist architekturspezifisch und muss der Architektur des Zielbetriebssystems entsprechen.


## <a name="rmsclient21-installation-options"></a>Installationsoptionen für den RMS Client 2.1

### <a name="creating-your-deployment-package"></a>Erstellen des Bereitstellungspakets

Es wird empfohlen, das Installationspaket für den RMS-Client mithilfe der bevorzugten Installationstechnologie mit Ihrer Anwendung oder Lösung zu kombinieren. Der RMS-Client kann kostenlos zusammen mit anderen Anwendungen und Lösungen weiterverteilt werden.

Sie können den RMS-Client 2.1 interaktiv durch Starten des dazugehörigen Installationsprogramms oder im Hintergrund installieren. Die Integrationsschritte umfassen Folgendes:

-   Herunterladen des Installationsprogramms für den RMS-Client 2.1
-   Integrieren des RMS Client 2.1-Installationsprogramms zur Ausführung im Anwendungsinstallationsprogramm

Ein Beispiel für die Integration des RMS-Clients 2.1 in Ihre Anwendung ist das Paket [Rights Protected Folder Explorer](/previous-versions/orphan-topics/ws.10/hh538204(v=ws.10)). Installieren Sie es selbst, um das Konzept nachzuvollziehen.

### <a name="make-rmsclient21-a-pre-requisite-for-your-application-install"></a>Festlegen von RMS Client 2.1 als Voraussetzung für die Installation der Anwendung

In diesem Fall erstellen Sie eine Voraussetzung, die dafür sorgt, dass bei der Installation Ihrer Anwendung ein Fehler auftritt, wenn der RMS-Client 2.1 auf dem Computer des Endbenutzers nicht vorhanden ist.

Für den Fall, dass der Client nicht vorhanden ist, geben Sie eine Fehlermeldung an, die den Benutzer darüber informiert, wo er den RMS-Client 2.1 herunterladen kann.

Wenn der Client vorhanden ist, wird die Anwendungsinstallation fortgesetzt.

## <a name="enabling-azure-information-protection-services-with-your-application"></a>Aktivieren von Azure Information Protection-Diensten für Ihre Anwendung

> [!NOTE]
> Wenn Sie bei der Authentifizierung auf das neue ADAL-Modell umgestiegen sind, müssen Sie **SIA** nicht installieren. Weitere Informationen finden Sie unter [Konfigurieren Ihrer App für die ADAL-Authentifizierung](adal-auth.md).
> Außerdem können Sie **Ihre Anwendung für Windows 10 zertifizieren**: Wenn Sie Ihre Anwendung für die Verwendung der ADAL-Authentifizierung (anstelle des Microsoft Online Services-Anmeldeassistenten) aktualisieren, können Sie und Ihre Kunden die mehrstufige Authentifizierung verwenden und den RMS-Client 2.1 ohne Administratorrechte auf dem Computer installieren.

Damit Ihre Endbenutzer Information Protection-Dienste nutzen können, müssen Sie den *Online Services-Anmeldeassistenten* (Sign-In Assistant, SIA) bereitstellen. Als Entwickler einer Anwendung wissen Sie nicht, ob Endbenutzer Information Protection über RMS (lokal) oder über Azure Information Protection verwenden werden.


> [!IMPORTANT]
> Wenn Sie Ihre Clientanwendung mit Azure-basierten RMS ausführen, müssen Sie eigene Mandanten erstellen. Weitere Informationen finden Sie unter [Azure Information Protection](../requirements.md).
> Weitere Informationen zur Ausführung mit Azure RMS finden Sie unter [Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

-   Laden Sie den [Microsoft Online Services-Anmeldeassistenten](https://www.microsoft.com/download/details.aspx?id=28177) aus dem Microsoft Download Center herunter.
-   Stellen Sie sicher, dass Ihre Bereitstellung einer rechtefähigen Anwendung diese Dienstauswahl als Voraussetzung überprüft.
-   Informationen zu eigenen Tests und zur Verwendung des Onlinediensts durch die Endbenutzer finden Sie im TechNet-Thema [Roadmap für die Bereitstellung von Azure Information Protection](../deployment-roadmap.md).

Verwenden Sie außerdem die folgende Konfigurationsanleitung für Ihre App: [Konfigurieren Ihrer App Service-App zur Verwendung der Azure Active Directory-Anmeldung](/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication).

Weitere Informationen zum Ermöglichen der Verwendung von RMS für Azure Rights Management Services in Ihrer Anwendung finden Sie unter [Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="related-topics"></a>Verwandte Themen

* [Microsoft Online Services-Anmelde-Assistent](https://www.microsoft.com/download/details.aspx?id=28177)
* [Roadmap für die Bereitstellung von Azure Information Protection](../deployment-roadmap.md)
* [Exemplarische Vorgehensweise: Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md)