---
# required metadata

title: Testen Ihrer rechtlich geschützten Anwendung | Azure RMS
description: Beschreibt die erforderlichen Schritte, um die rechtlich geschützte RMS SDK 2.1-Anwendung zu testen.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 834B7242-31D3-4275-A892-CFE95A61E29E
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Testen Ihrer rechtlich geschützten Anwendung

Dieses Thema beschreibt die erforderlichen Schritte, um die rechtlich geschützte Rights Management Services SDK 2.1-Anwendung zu testen.

Um geschützte Inhalte zu veröffentlichen und zu nutzen, verwenden eine Rights Management Services (RMS)-Anwendung unterschiedliche Zertifikat- und Lizenztypen, die jeweils aus einer Zertifikatkette bestehen, die letztendlich zu einer Microsoft-Zertifizierungsstelle zurückführt. Microsoft bietet die folgenden Hierarchien:

-   Die Präproduktionshierarchie kann zum Entwickeln und Testen der Anwendung verwendet werden.
-   Die Produktionshierarchie muss von veröffentlichten Anwendung verwendet werden.

Es wird empfohlen, dass Sie beim Entwickeln einer Anwendung die Präproduktionshierarchie verwenden. Auf diese Weise können Sie arbeiten, ohne einen Produktionslizenzvertrag mit Microsoft abzuschließen.

> [!IMPORTANT]
> Eine bewährte Methode besteht darin, die RMS SDK 2.1-Anwendung zuerst mit der RMS-Präproduktionsumgebung auf einem RMS-Server zu testen. Soll Ihr Kunde dann die Möglichkeit erhalten, Ihre Anwendung mit dem Azure RMS-Dienst zu verwenden, testen Sie in dieser Umgebung. Weitere Informationen finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

 

### Voraussetzungen

-   Eine eingerichtete RMS SDK 2.1-Entwicklungsumgebung. Weitere Informationen finden Sie unter [Einrichten der Entwicklungsumgebung für die Präproduktion](how-to-set-up-the-pre-production-development-environment.md).
-   Eine Beispielanwendung finden Sie unter [IPCHelloWorld – Beispielanwendung](how-to-build-your-first-application.md).

Anweisungen

### Schritt 1:

Erstellen einer rechtlich geschützte Anwendung. Optionen finden Sie im vorangegangenen Abschnitt mit den Voraussetzungen.

### Schritt 2: Generieren eines Anwendungsmanifests mithilfe der Präproduktions-Zertifikatkette

Generieren Sie vor der Ausführung der Anwendung ein Manifest.

**Hinweis**: Wenn die Anwendung den Server-API-Modus (**IPC\_API\_MODE\_SERVER**) verwendet, ist kein Anwendungsmanifest erforderlich. Sie können Ihre Anwendung mit einem AD RMS-Produktionsserver testen. Beim Wechsel zur Produktionsumgebung müssen Sie keine Produktionslizenz beziehen. Weitere Informationen zu Servermodusanwendungen finden Sie unter [Anwendungstypen](application-types.md).

 

Dieser Prozess wird auch als Signieren der Anwendung bezeichnet. Sie können das Manifest mit einer Produktionszertifikatkette oder der mit dem SDK installierten Präproduktions-Zertifikatkette generieren. Es wird empfohlen, während der Entwicklung die Präproduktions-Zertifikatkette zu verwenden.

Weitere Informationen zu Schlüsseln und Zertifikatketten finden Sie unter [Grundlegendes zu Zertifikatketten](understanding-certificate-chains.md).

Informationen dazu, wie Sie eine Anwendung mit einer Produktionszertifikatkette signieren, finden Sie unter [Wechseln zur Produktionsumgebung](switching-to-the-production-environment.md).

Um die Anwendungsmanifestdatei mithilfe der Präproduktions-Zertifikatskette zu generieren, führen Sie auf dem Entwicklungscomputer folgende Schritte aus:

1.  Kopieren Sie die folgenden Dateien aus den Installationsverzeichnissen in denselben Ordner wie die Anwendung.

    %MSIPCSdkDir%\\Tools\\Genmanifest.exe

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningprivkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsigningpubkey.dat

    %MSIPCSdkDir%\\bin\\Isvtier5appsignsdk\_client.xml

    %MSIPCSdkDir%\\bin\\YourAppName.isv.mcf

2.  Benennen Sie im Anwendungsordner die Manifestkonfigurationsdatei "YourAppName.isv.mcf" in den Namen der Anwendung um, und fügen Sie die Dateinamenerweiterung .mcf an. Beispiel: Wenn die Anwendung MyApp.exe heißt, benennen Sie "YourAppName.isv.mcf" in "MyApp.exe.mcf" um.

3.  Verwenden Sie einen Text-Editor, um Ihre Anwendung der Manifestkonfigurationsdatei hinzuzufügen. Ersetzen Sie hierzu den Platzhalter &lt;YourAppName&gt;.exe in der Modulliste in Ihrer MCF-Datei durch den Namen der Anwendung, beispielsweise "MyApp.exe".

    Der Signiervorgang generiert einen Fehler, wenn die MCF-Datei unverändert verwendet wird.

4.  Führen Sie Genmanifest.exe aus, um die Anwendungsmanifestdatei zu generieren. Dieser Prozess wird auch als Signieren der Anwendung bezeichnet. Bei diesem Vorgang sollte eine MAN-Datei ausgegeben werden. Beispiel: Wenn Ihre Anwendung "MyApp.exe" und die Manifestkonfigurationsdatei "MyApp.exe.mcf" heißt, führen Sie den folgenden Befehl aus:

    **genmanifest.exe -chain isvtier5appsignsdk\_client.xml MyApp.exe.mcf MyApp.exe.man**

### Schritt 3: Ausführen der Anwendung

Sie können die Anwendung aus einem beliebigen Verzeichnis ausführen. Die Anwendungsmanifestdatei (MyApp.exe.man) muss sich jedoch im gleichen Verzeichnis wie die ausführbare Datei (MyApp.exe) befinden.

-   **Verwendung der RMS-Umgebung für einen Computer**

    Wenn Sie die RMS-Umgebung für einen Computer zum Testen Ihrer Anwendung verwenden, kopieren Sie die ausführbare Datei der Anwendung und die Anwendungsmanifestdatei in ein beliebiges Verzeichnis in der Umgebung für einen Computer und führen Sie dann die Anwendung aus.

    Informationen über die RMS-Umgebung für einen Computer finden Sie unter [Einrichten der Testumgebung](how-to-set-up-your-test-environment.md).

-   **Verwenden eine Präproduktions-Serverkonfiguration**

    Wenn Sie Ihre Anwendung mit einem RMS-Server testen, der für die Präproduktion konfiguriert ist, stellen Sie sicher, dass Sie Active Directory Rights Management Services Client 2.1 auf dem Computer konfiguriert haben, auf dem die Anwendung ausgeführt wird (beispielsweise auf Ihrem Entwicklungscomputer). Stellen Sie anschließend sicher, dass sich sowohl die ausführbare Datei der Anwendung als auch die Anwendungsmanifestdatei im selben Verzeichnis auf dem Computer befinden, und führen Sie die Anwendung aus.

    Informationen zum Konfigurieren des Clients auf Ihrem Computer finden Sie unter [Konfigurieren des Clients](how-to-configure-the-ad-rms-client-2-0.md). Weitere Informationen zum Installieren eines RMS-Servers finden Sie unter [Installieren und Konfigurieren des Servers](how-to-install-and-configure-an-rms-server.md).

## Verwandte Themen

* [Vorgehensweise](how-to-use-msipc.md)
* [Konfigurieren des Clients](how-to-configure-the-ad-rms-client-2-0.md)
* [Installieren und Konfigurieren des Servers](how-to-install-and-configure-an-rms-server.md)
* [IPCHelloWorld – Beispielanwendung](how-to-build-your-first-application.md)
* [Einrichten der Entwicklungsumgebung für die Präproduktion](how-to-set-up-the-pre-production-development-environment.md)
* [Wechseln zur Produktionsumgebung](switching-to-the-production-environment.md)
* [Einrichten der Testumgebung](how-to-set-up-your-test-environment.md)
* [Grundlegendes zu Zertifikatketten](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO4-->


