---
title: Versionshinweise
description: Weitere Informationen finden Sie in den Anmerkungen zu dieser Version des Microsoft Rights Management Service SDK v 2.1 Oktober 2019 und früheren Updates.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 10/18/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: b0bd50f739a98d261924e4dba96accc40e87e2bb
ms.sourcegitcommit: dc50f9a6c2f66544893278a7fd16dff38eef88c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/18/2020
ms.locfileid: "88563755"
---
# <a name="release-notes"></a>Versionshinweise

Dieser Artikel enthält wichtige Informationen zu diesem und früheren Releases des RMS SDK 2.1.

## <a name="october-2019---update"></a>Oktober 2019-Update

- Unter bestimmten Umständen kann die Verwendung der symmetrischen Schlüssel Authentifizierung den Benutzer nicht mit Azure RMS authentifizieren, was den Schutz und den Schutz von Inhalten verhindert.
- Der RMS-Client stürzt möglicherweise ab, um zu überprüfen, ob einige PDF-Dokumente, die zuvor geschützt und ungeschützt waren, zurzeit geschützt sind.
- Die Verwendung der DNS-Umleitung für AD RMS Server, die auf besonderen Ports konfiguriert wurden, funktioniert nicht ordnungsgemäß.

## <a name="september-2019---update"></a>September 2019-Update

- Korrigiert eines Deadlocks, der auftreten kann, wenn versucht wird, die Initialisierungs Methoden zur gleichen Zeit wie andere RMS-Client Methoden aufzurufen.
- Es wurde ein Problem behoben, das bestimmt, ob Kenn Wort geschützte Office-Dateien RMS-geschützt sind
-   Aktualisieren Sie die Lizenzierungs Überprüfung für spezielle Zweck Lizenzen.
- Updates für die PDF-Schutzvorrichtung.
- Andere Fehlerbehebungen.
- Aktualisieren Sie, um statisch mit den C-Laufzeitbibliotheken zu verknüpfen.

## <a name="april-2019---update"></a>April 2019-Update
- Fehlerbehebungen in der Datei-API.
- Die Datei-API wurde aktualisiert, um beim Entschlüsseln von Inhalten das Export Recht und nicht das Extract-Recht zu überprüfen.
- Installationsprogramm Korrektur, um sicherzustellen, dass die neue PDF v2-Schutzvorrichtung bei der Aktualisierung installiert wird.
- Telemetrieänderungen. Diese Änderung erforderte ein Update des Installationspakets, mit dem die C-Laufzeitbibliotheken installiert werden.
- Die Dienst-Back-End-Authentifizierung ändert sich, **Bitte aktualisieren Sie diese SDK-Version, um die Unterbrechung zu minimieren, wenn Sie die Authentifizierung mit symmetrischem Schlüssel**
- Unterstützung für VC 15,9


## <a name="october-2017---update"></a>Oktober 2017: Update

- Hinzufügen von zwei neuen APIs zur Initialisierung bzw. zur Aufhebung der Initialisierung von Umgebungen. Weitere Informationen finden Sie unter [IpcInitializeEnvironment](https://msdn.microsoft.com/library/hh535289.aspx) und [IpcUninitializeEnvironment](https://msdn.microsoft.com/library/hh535289.aspx).
- Visio-Dateitypen werden jetzt unterstützt. Weitere Informationen finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

## <a name="february-2016---sdk-documentation-update"></a>Februar 2016 – SDK-Dokumentationsupdate

>[!Note]
> Die Funktionsdokumentationsupdates in diesem Abschnitt gelten für den SDK-Download vom 12.11.2015.

- **Verbesserter Authentifizierungsablauf** – Verwendung von tokenbasierter Authentifizierung von OAuth2 über die [Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/documentation/articles/active-directory-authentication-libraries/). Weitere Informationen zu diesem Prozess und den API-Erweiterungen dafür finden Sie unter [Adal-Authentifizierung für Ihre RMS-fähige Anwendung](how-to-use-adal-authentication.md).

- **Update zu ADAL**: Durch das Update der Anwendung dahingehend, dass sie die ADAL-Authentifizierung statt des Microsoft Online-Anmelde-Assistenten verwendet, ergeben sich für Sie und Ihre Kunden folgende Möglichkeiten:

  - Nutzen der mehrstufigen Authentifizierung
  - Installieren des RMS-Client 2.1 ohne Administratorrechte auf dem Computer
  - Zertifizieren Ihrer Anwendung für Windows 10

- **Die Unterstützung für den Microsoft Online Services-Anmeldeassistenten (SIA) mit dem RMS SDK wird entfernt.** Die Verwendung von SIA wird noch für sechs Monate unterstützt. Danach endet die Zeitunterstützung.


## <a name="december-2015-update"></a>Update vom Dezember 2015

- Leistungssteigerungen wurden unter anderem in folgenden Bereichen implementiert:
    - Veröffentlichen von primären Lizenzserver bei Verwendung von reinen Lizenz-Servern.
    - RMS SDK 2.1 fällt schneller aus, wenn keine Netzwerkverbindung besteht.

- Zahlreiche Updates zur Verbesserung der Fehlermeldungen und der Problembehandlung.
- Beachten Sie auch, dass die Liste der [unterstützten Plattformen](supported-platforms.md) ebenfalls aktualisiert wurde.
- Die Notwendigkeit für die Präproduktionsumgebung und die Verwendung eines Anwendungsmanifests wurden im RMS SDK 2.1 entfernt. Die betreffenden Abschnitte dieser Entwicklerdokumentation wurden entfernt, und die Gesamtdokumentation wurde vereinfacht und umstrukturiert.

## <a name="may-2015-update"></a>Mai 2015-Update

-   **Dienst-apps und cloudbasierter RMS**  -  [IPC \_ Der \_ \_ symmetrische](https://msdn.microsoft.com/library/dn133062.aspx) Anmelde Informations Schlüssel benötigt drei Informationen: symmetrische Schlüssel, **appprincipalid**und **tenantbposid**. Dieser Artikel wurde aktualisiert, um Hilfestellung für die Verarbeitung dieser Informationen zu bieten. Lesen Sie zu diesem Update die überarbeitete Version von [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="april-2015-update"></a>April 2015-Update

-   Die **Dokumentenverfolgung** ist jetzt über eine Reihe neuer APIs möglich. Weitere Informationen finden Sie unter nach [Verfolgen von Inhalten](tracking-content.md).
-   **Verschlüsselungstyp**: Zur Auswahl des Verschlüsselungspakets wird jetzt die Steuerung auf API-Ebene unterstützt. Weitere Informationen finden Sie unter [Arbeiten mit der Verschlüsselung](working-with-encryption.md).

    **Hinweis**    Das Flag " **IPC \_ Li \_ deprecated \_ Encryption \_ Algorithmen** " wird in unserer API nicht mehr verfügbar gemacht. Zukünftige Anwendungen werden daher nicht mehr kompiliert, wenn sie auf dieses Flag verweisen. Bereits erstellte Anwendungen sind weiterhin funktionsfähig, da wir das Flag privat im API-Code berücksichtigen. Die Vorteile des veralteten Verschlüsselungsalgorithmusflags können weiterhin durch einfaches Ändern eines Flags erreicht werden. Weitere Informationen finden Sie unter [Arbeiten mit der Verschlüsselung](working-with-encryption.md).

-   **Servermodusanwendungen**, die **IPC\_API\_MODE\_SERVER** als [API-Moduswert](https://msdn.microsoft.com/library/hh535236.aspx) verwenden, benötigen kein Anwendungsmanifest mehr. Sie können Ihre Anwendung mit einem RMS-Produktionsserver testen. Beim Wechseln zur Produktionsumgebung müssen Sie keine Produktionslizenz beziehen. Weitere Informationen zu servermodusanwendungen finden Sie unter [Anwendungs Typen](application-types.md).
-   **Protokollierung** wurde jetzt über die Datei- und Ereignisablaufverfolgung für Windows-Methoden implementiert.
-   Bei Ausführung auf einem **Windows 7 SP1- oder Windows Server 2008 R2-Computer** lesen Sie den Hinweis unter "Wichtige Hinweise für Entwickler".

## <a name="january-2015-update"></a>Januar 2015-Update

-   **Vergrößerung der unterstützten geschützten Datei (PFILE)**: Jetzt werden PFILE-Dateien über 1 GB unterstützt. Weitere Informationen zu PFILE-Dateien finden Sie unter [Unterstützte Dateiformate](supported-file-formats.md).
-   **Verbesserte Protokollierung für eine bessere Diagnose**: Die Protokollierungsstufen zeigen **FEHLER** oder **WARNUNG** für Nachrichten, die geprüft werden müssen. Alle anderen Nachrichten, einschließlich Ausnahmen, die weiterhin angezeigt werden, werden als **Info**protokolliert.

    Auf diese Weise bleiben Ihre Details erhalten. Jetzt werden nur die wichtigsten Nachrichten als WARNUNG angezeigt.

-   **Abrufen von Unternehmensvorlagen**: Es wurden wesentliche Korrekturen am Code zum Abrufen von Vorlagen basierend auf Kundenberichten und Feedback vorgenommen.
-   Verbesserte Lokalisierungskonsistenz

## <a name="october-2014-update"></a>Oktober 2014-Update

-   Das Standardverhalten für die Datei-API-Komponente des SDK wurden aktualisiert. Weitere Informationen finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).
-   Die neue Funktion der E-Mail-Benachrichtigung wird in den Hinweisen für Entwickler im Abschnitt über das [Aktivieren von E-Mail-Benachrichtigungen](how-to-enable-email-notification.md) erläutert.

## <a name="july-2014-update"></a>Juli 2014-Update

Die Datei-API-Komponente des SDK wurde erweitert und bietet folgende Funktionen:

-   Identifiziert die zu verwendende Schutzvorrichtung.
-   Bietet RMS-Schutz auf der Detailebene einer Datei.

    In dieser Version hinzugefügte Funktionen:

    **Hinweis**   -Weitere unterstützende Datentypen und-Strukturen, die hier nicht aufgeführt sind, wurden für die Datei-API-Erweiterungen hinzugefügt. Alle Artikel, die für dieses Release aktualisiert wurden, sind als **vorläufig markiert und können geändert werden**.

    -   [IpcfOpenFileOnHandle](https://msdn.microsoft.com/library/dn771751.aspx)
    -   [IpcfOpenFileOnILockBytes](https://msdn.microsoft.com/library/dn771752.aspx)
    -   [IpcfGetFileProperty](https://msdn.microsoft.com/library/dn771749.aspx)
    -   [IpcfLogicalFileRangeToRawFileRange](https://msdn.microsoft.com/library/dn771750.aspx)
    -   [IpcfReadFile](https://msdn.microsoft.com/library/dn771753.aspx)
    -   [IpcfSetEndOfFile](https://msdn.microsoft.com/library/dn771754.aspx)
    -   [IpcfWriteFile](https://msdn.microsoft.com/library/dn771756.aspx)

## <a name="april-2014-update"></a>April 2014-Update

-   Die **Datei-API-Speicherverwendung**, insbesondere für große PFILE-Dateien, wurde erheblich verbessert.
-   Die **Inhalts-ID** ist nun über die Eigenschaft **IPC \_ Li \_ Content \_ ID**beschreibbar. Weitere Informationen finden Sie unter den Angaben zu [Lizenzeigenschaftstypen](https://msdn.microsoft.com/library/hh535287.aspx).
-   **Manifestanforderungen für die Produktion** – Wenn die RMS-fähige Anwendung bzw. der Diensts im Servermodus ausgeführt wird, ist kein Manifest mehr erforderlich. Weitere Informationen finden Sie unter [Anwendungs Typen](application-types.md).
-   **Dokumentationsupdates**

    **Bewährte Testmethoden**: Anleitung zur Verwendung des lokalen Servers vor dem Testen mit Azure RMS hinzugefügt. Weitere Informationen finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

## <a name="important-developer-notes"></a>Wichtige Hinweise für Entwickler

-   **Native Unterstützung für alle Dateitypen**

    Native Unterstützung kann für einen beliebigen Dateityp (Erweiterung) mit dieser Version des Rights Management Services SDK 2.1 hinzugefügt werden. Beispielsweise wird für jede &lt;ext&gt;-Erweiterung (nicht Office und PDF) \*.p&lt;ext&gt; verwendet, wenn die Administratorkonfiguration für diese Erweiterung NATIVE lautet.

    Weitere Informationen zu unterstützten Dateitypen finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

-   Auf **Windows 7 SP1- und Windows Server 2008 R2 SP1-Computern** ohne das Update [KB2533623](https://support.microsoft.com/kb/2533623) tritt möglicherweise der folgende Fehler beim Schutz von Office-Dateien auf: "Der Parameter ist falsch. Fehlercode: 0 x 80070057". Wenn dies angezeigt wird, installieren Sie das Update, und versuchen Sie es erneut. Wenn das Problem weiterhin auftritt, geben Sie uns Feedback zur Betaversion des RMS SDK unter <rmcstbeta@microsoft.com>.

    **Hinweis**    Ab Version April 2015 wurde dem Installationsvorgang für dieses KB eine Prüfung hinzugefügt.



-   **Datei-API-Integration**

    Die Datei-API für Active Directory Rights Management Services bietet durch das Hinzufügen der Datei-API die folgenden Vorteile und Funktionen.

      - Vertrauliche Daten können automatisch geschützt werden, ohne die Details der Information Rights Management (IRM)-Implementierung zu kennen, die von verschiedenen Dateiformaten verwendet wird.

      - Microsoft Office-Dateien, PDF-Dateien (Portable Document Format) und bestimmte weitere Dateitypen können mit systemeigenem Schutz geschützt werden. Eine umfassende Liste von Dateitypen, die mit System eigenem Schutz geschützt werden können, finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

      - Alle Dateien außer System- und Office-Dateien können mit dem geschützten RMS-Dateiformat (PFILE) geschützt werden.

    Die Datei-API wird über die vier folgenden neuen Funktionen implementiert: [IpcfDecryptFile](https://msdn.microsoft.com/library/dn133058.aspx), [IpcfEncryptFile](https://msdn.microsoft.com/library/dn133059.aspx), [IpcfGetSerializedLicenseFromFile](https://msdn.microsoft.com/library/dn133060.aspx) und [IpcfIsFileEncrypted](https://msdn.microsoft.com/library/dn133061.aspx).

    Die Datei-API erfordert, dass der Rights Management Service Client 2.1 auf dem Clientcomputer installiert ist und dass der Computer mit einem RMS-Server verbunden ist. Weitere Informationen zu RMS-Server, RMS-Client und deren Funktionalität finden Sie im TechNet unter [Dokumentation zu RMS für IT-Spezialisten](https://technet.microsoft.com/library/cc771234(v=ws.10).aspx).

-   **Problem**: Wenn Sie eine Lizenz von Grund auf neu erstellen, müssen Sie Eigentumsrechte explizit gewähren.

    **Lösung**: Die Anwendung muss dem Lizenzinhaber explizit **Besitzerrechte** hinzufügen, wenn eine von Grund auf neue Lizenz mit [IpcCreateLicenseFromScratch](https://msdn.microsoft.com/library/hh535256.aspx) erstellt wird. Weitere Informationen finden Sie unter [Hinzufügen expliziter Besitzer Rechte](add-explicit-owner-rights.md).

-   **Problem**: Wenn eine Anwendung [ipcprotectwindow](https://msdn.microsoft.com/library/hh535268.aspx) oder [ipcunprotectwindow](https://msdn.microsoft.com/library/hh535272.aspx) zweimal für das gleiche Fenster mithilfe Ihres Handles aufruft, gibt RMS SDK 2,1 einen Fehler in **HRESULT**zurück.

    **Lösung**: spezifische Anleitungen hierzu finden Sie im Abschnitt "Hinweise" in [ipcprotectwindow](https://msdn.microsoft.com/library/hh535268.aspx) und [ipcunprotectwindow](https://msdn.microsoft.com/library/hh535272.aspx).

-   **Problem**: Bei der Entwicklung für mehrere Architekturen müssen Sie diese Anweisungen verwenden.

    **Lösung**: Wenn Sie die ipcsecproc- \*isv.dll für eine andere Architektur verwenden möchten (z. b. Wenn Sie das 64-Bit SDK auf einem 64-Bit-Computer installiert haben, aber jetzt auf einem 32-Bit-Computer bereitstellen möchten, für den ipcsecproc \*isv.dll erforderlich ist), Sie müssen das 32-Bit-SDK auf einem anderen Computer installieren und die ipcsecproc- \*isv.dll Dateien aus dem Ordner "% Program Files% \\ Microsoft Information Protection und Control" (dem Standard Speicherort oder wo Sie sich für die Installation des SDK ausgewählt haben) dorthin kopieren.

## <a name="frequently-asked-questions"></a>Häufig gestellte Fragen

**F**: Welches Standardverhalten gilt für die Sprache bei Funktionen, die einen LCID-Parameter akzeptieren?

**A**: Verwenden Sie 0 für das Standardgebietsschema. In diesem Fall sucht der AD RMS-Client 2.1 in der folgenden Reihenfolge nach Namen und Beschreibungen und ruft die erste verfügbare Sprache auf:

1. Vom Benutzer bevorzugte LCID.
2. LCID des System Gebiets Schemas.
3. Die erste verfügbare Sprache, die in der Vorlage für den Rights Management Server (RMS) angegeben ist.

Wenn kein Name und keine Beschreibung abgerufen werden kann, wird ein Fehler zurückgegeben. Es kann nur ein Name und eine Beschreibung für eine bestimmte LCID vorhanden sein.
