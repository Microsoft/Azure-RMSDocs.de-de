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

# Bereitstellen der Anwendung


Dieses Thema beschreibt und führt Sie durch die Bereitstellungsoptionen für Ihre Rechte-fähige Anwendung.

> [!IMPORTANT]
> Eine bewährte Methode besteht darin, die Rights Management Services SDK 2.1-Anwendung zuerst mit der RMS-Präproduktionsumgebung auf einem RMS-Server zu testen. Soll Ihr Kunde dann die Möglichkeit erhalten, Ihre Anwendung mit dem Azure RMS-Dienst zu verwenden, testen Sie in dieser Umgebung. Weitere Informationen finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

 

## Installationsoptionen für Active Directory Rights Management Services Client 2.1

Nach dem Erstellen der Manifestdatei mithilfe eins Produktionszertifikats kann die Anwendung bereitgestellt werden. Sofern Sie RMS SDK 2.1 genutzt haben, muss Active Directory Rights Management Services Client 2.1 auf dem Endbenutzercomputer bereitgestellt werden.

### AD RMS-Client 2.1

Der AD RMS-Client 2.1 ist eine Software, die entwickelt wurde, damit auf Ihren Clientcomputern der Zugriff auf und die Verwendung von Informationen möglich ist, die durch Anwendungen fließen, die AD RMS verwenden und lokal oder in einem Microsoft-Rechenzentrum installiert sind.

Der AD RMS-Client 2.1 ist keine Komponente des Windows-Betriebssystems. Der AD RMS-Client 2.1 wird als optionaler Download bereitgestellt, der mit Bestätigung und Annahme des Lizenzvertrags mit der Software von Drittanbietern frei verteilt werden kann, um Clients Zugriff auf Inhalte zu ermöglichen, die durch Nutzung und Bereitstellung von RMS-Servern in Ihrer Umgebung geschützt wurden.

> [!IMPORTANT]
> Die AD RMS-Client 2.1-Architektur ist speziell und muss der Architektur des Zielbetriebssystems entsprechen.


## Installationsoptionen für den AD RMS-Client 2.1

-   **Weiterverbreitung des AD RMS-Client 2.1**

    Es wird empfohlen, das RMS-Client-Installationspaket mit Ihrer Anwendung oder Lösung mithilfe des bevorzugten Installationsverfahrens zu packen. Der RMS-Client kann kostenlos zusammen mit anderen Anwendungen und IT-Lösungen weiterverbreitet und gebündelt werden.

    Sie können den AD RMS-Client 2.1 interaktiv durch Starten des AD RMS-Client 2.1-Installationsprogramms oder im Hintergrund installieren. Die Integrationsschritte sind wie folgt:

    -   Herunterladen des RMS-Client 2.1-Installationsprogramms
    -   Integrieren des AD RMS-Client 2.1-Installationsprogramms in das Anwendungsinstallationsprogramm

    Zwei gute Beispiele für die Integration des AD RMS-Client 2.1 in Ihre Anwendung sind das RMS SDK 2.1-Installationspaket und das die Right Protected Folder Explorer-Paket. Installieren Sie sie selbst, um den Ansatz zu verstehen.

-   **AD RMS-Client 2.1 als Voraussetzung für die Anwendungsinstallation festlegen**

    In diesem Fall erstellen Sie eine Voraussetzung, z. B. dass die Installation der Anwendung fehlschlägt, wenn AD RMS-Client 2.1 nicht auf dem Computer des Endbenutzers vorhanden ist.

    Wenn der Client nicht vorhanden ist, wird eine Fehlermeldung bereitgestellt, die den Benutzer darüber informiert, wo eine Kopie des AD RMS-Client 2.1 heruntergeladen werden kann.

    Wenn der Client vorhanden ist wird die Anwendungsinstallation fortgesetzt.

## Aktivieren von Azure Rights Management Services mit Ihrer Anwendung

> [!NOTE]
> Wenn Sie in das neue ADAL-Modell für die Authentifizierung migriert haben, müssen Sie SIA nicht installieren. Weitere Informationen finden Sie im Thema zur ADAL-Authentifizierung für Ihre RMS-fähige Anwendung.

- **Zertifizieren Ihrer Anwendung für Windows 10**: Durch die Aktualisierung der Anwendung zur Verwendung der ADAL-Authentifizierung anstatt des Microsoft Online-Anmelde-Assistenten haben Sie und Ihre Kunden folgende Möglichkeiten:
  - Nutzen der mehrstufigen Authentifizierung
  - Installieren des RMS-Client 2.1 ohne Administratorrechte auf dem Computer
 
  Damit Endbenutzer Azure Rights Management Services nutzen können, müssen Sie den *Online Services-Anmelde-Assistenten* bereitstellen. Als Anwendungsentwickler wissen Sie nicht, ob der Endbenutzer RMS (lokal) oder Azure Rights Management Services (Clouddienst) verwenden wird.

> [!IMPORTANT]
> Das Ausführen der RMS SDK 2.1-Clientanwendung mit Azure RMS erfordert das Anfordern eines Azure RMS-Mandanten. Senden Sie eine E-Mail mit Ihrer Mandantenanforderung an <rmcstbeta@microsoft.com>.

-   Laden Sie den [Microsoft Online Services-Anmeldeassistenten](http://www.microsoft.com/en-us/download/details.aspx?id=28177) aus dem Microsoft Download Center herunter.
-   Stellen Sie sicher, dass die Bereitstellung einer rechtefähigen Anwendung eine Überprüfung der Voraussetzungen für diese Dienstauswahl enthält.
-   Informationen zu eigenen Tests und zur Verwendung des Onlinediensts durch die Endbenutzer finden Sie im TechNet-Thema [Konfigurieren von Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx).

Weitere Informationen zum Ermöglichen der Verwendung von RMS für Azure Rights Management Services durch Ihre Anwendung finden Sie im Thema zum [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Anwendung](how-to-use-file-api-with-aadrm-cloud.md).

## Verwandte Themen

* [Vorgehensweise](how-to-use-msipc.md)
* [Microsoft-Onlinedienst-Anmeldungs-Assistent](http://www.microsoft.com/en-us/download/details.aspx?id=28177)
* [Konfigurieren von Rights Management](https://TechNet.Microsoft.Com/en-us/library/jj585002.aspx)
* [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Anwendung](how-to-use-file-api-with-aadrm-cloud.md)
 

 





<!--HONumber=Apr16_HO4-->


