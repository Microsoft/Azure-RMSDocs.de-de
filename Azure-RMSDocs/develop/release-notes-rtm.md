---
# required metadata

title: Versionshinweise | Azure RMS
description:
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 05/03/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: CE379738-4E1D-42AD-83F4-F89B70456EBB
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Anmerkungen zu dieser Version

Dieses Thema enthält wichtige Informationen zu dieser und früheren Versionen von RMS SDK 2.1.

## Neu für Februar 2016 – SDK-Dokumentationsupdate

>[!Note]  Die Funktionsdokumentationsupdates in diesem Abschnitt gelten für den SDK-Download vom 12.11.2015.

- **Verbesserter Authentifizierungsablauf** – Verwendung von tokenbasierter Authentifizierung von OAuth2 über die [Azure Active Directory Authentication Library (ADAL)](https://azure.microsoft.com/en-us/documentation/articles/active-directory-authentication-libraries/). Weitere Informationen zu diesem Prozess und den API-Erweiterungen dafür finden Sie unter [ADAL-Authentifizierung für Ihre RMS-fähige Anwendung](how-to-use-adal-authentication.md).

- **Update zu ADAL**: Durch das Update der Anwendung dahingehend, dass sie die ADAL-Authentifizierung statt des Microsoft Online-Anmelde-Assistenten verwendet, ergeben sich für Sie und Ihre Kunden folgende Möglichkeiten:

 - Nutzen der mehrstufigen Authentifizierung
 - Installieren des RMS-Client 2.1 ohne Administratorrechte auf dem Computer
 - Zertifizieren Ihrer Anwendung für Windows 10

- **Die Unterstützung für den Microsoft Online Services-Anmeldeassistenten (SIA) mit dem RMS SDK wird entfernt.** Wir werden die Verwendung von SIA noch für sechs Monate unterstützen und danach endet die Zeitunterstützung.


## Dezember 2015-Update

- Leistungssteigerungen wurden unter anderem in folgenden Bereichen implementiert:
    - Veröffentlichen von primären Lizenzserver bei Verwendung von reinen Lizenz-Servern.
    - RMS SDK 2.1 fällt schneller aus, wenn keine Netzwerkverbindung besteht.

- Zahlreiche Updates zur Verbesserung der Fehlermeldungen und der Problembehandlung.
- Beachten Sie auch, dass die Liste der [unterstützten Plattformen](supported-platforms.md) ebenfalls aktualisiert wurde.
- Die Notwendigkeit für die Präproduktionsumgebung und die Verwendung eines Anwendungsmanifests wurden im RMS SDK 2.1 entfernt. Die betreffenden Abschnitte dieser Entwicklerdokumentation wurden entfernt, und die Gesamtdokumentation wurde vereinfacht und umstrukturiert.

## Mai 2015-Update

-   **Dienst-Apps und cloudbasierter RMS** - [**IPC\_CREDENTIAL\_SYMMETRIC\_KEY**](/rights-management/sdk/2.1/api/win/ipc_credential#msipc_ipc_credential_symmetric_key) benötigt drei Angaben: symmetrischen Schlüssel **AppPrincipalId** und **TenantBposId**. Dieses Thema wurde aktualisiert, um Hilfestellung für die Verarbeitung dieser abzurufenden Informationen zu bieten. Lesen Sie zu diesem Update die aktualisierte Version von [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

## April 2015-Update

-   Die **Dokumentenverfolgung** ist jetzt über eine Reihe neuer APIs möglich. Weitere Informationen hierzu finden Sie unter [Nachverfolgung von Inhalten](tracking-content.md).
-   **Verschlüsselungstyp**: Zur Auswahl des Verschlüsselungspakets wird jetzt die Steuerung auf API-Ebene unterstützt. Weitere Informationen finden Sie unter [Verwenden der Verschlüsselung](working-with-encryption.md).

    **Hinweis** Das Flag **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** wird in unserer API nicht länger zur Verfügung gestellt. Zukünftige Anwendungen werden daher nicht mehr kompiliert, wenn sie auf dieses Flag verweisen. Bereits erstellte Anwendungen sind weiterhin funktionsfähig, da wir das Flag privat im API-Code berücksichtigen. Die Vorteile des veralteten Verschlüsselungsalgorithmusflags können weiterhin durch einfaches Ändern eines Flags erreicht werden. Weitere Informationen finden Sie unter [Verwenden der Verschlüsselung](working-with-encryption.md).

-   **Servermodusanwendungen**, die **IPC\_API\_MODE\_SERVER** als [**API-Moduswert**](/rights-management/sdk/2.1/api/win/api%20mode%20values#msipc_api_mode_values_IPC_API_MODE_SERVER) verwenden, benötigen kein Anwendungsmanifest mehr. Sie können Ihre Anwendung mit einem RMS-Produktionsserver testen. Beim Wechseln zur Produktionsumgebung müssen Sie keine Produktionslizenz beziehen. Weitere Informationen zu Servermodusanwendungen finden Sie unter [Anwendungstypen](application-types.md).
-   **Protokollierung** wurde jetzt über die Datei- und Ereignisablaufverfolgung für Windows-Methoden implementiert.
-   Bei Ausführung auf einem **Windows 7 SP1- oder Windows Server 2008 R2-Computer** lesen Sie den Hinweis unter "Wichtige Hinweise für Entwickler".

## Januar 2015-Update

-   **Vergrößerung der unterstützten geschützten Datei (PFILE)**: Jetzt werden PFILE-Dateien über 1 GB unterstützt. Weitere Informationen zu PFILE-Dateien finden Sie unter [Unterstützte Dateiformate](supported-file-formats.md).
-   **Verbesserte Protokollierung für eine bessere Diagnose**: Die Protokollierungsstufen zeigen **FEHLER** oder **WARNUNG** für Nachrichten, die geprüft werden müssen. Alle anderen Nachrichten, einschließlich Ausnahmen, die weiterhin angezeigt werden, werden als **INFO** protokolliert.

    Auf diese Weise bleiben Ihre Details erhalten. Jetzt werden nur die wichtigsten Nachrichten als WARNUNG angezeigt.

-   **Abrufen von Unternehmensvorlagen**: Es wurden wesentliche Korrekturen am Code zum Abrufen von Vorlagen basierend auf Kundenberichten und Feedback vorgenommen.
-   Verbesserte Lokalisierungskonsistenz

## Oktober 2014-Update

-   Das Standardverhalten für die Datei-API-Komponente des SDK wurden aktualisiert. Weitere Informationen finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).
-   Die neue Funktion der E-Mail-Benachrichtigung wird in den Hinweisen für Entwickler im Abschnitt über das [Aktivieren von E-Mail-Benachrichtigungen](how-to-enable-email-notification.md) erläutert.

## Juli 2014-Update

Die Datei-API-Komponenten von SDK wurde erweitert und bieten folgende Funktionen:

-   Identifiziert die zu verwendende Schutzvorrichtung.
-   Bietet RMS-Schutz auf der Detailebene einer Datei.

    In dieser Version hinzugefügte Funktionen:

    **Hinweis**  Weitere hier nicht aufgeführte unterstützende Datentypen und -strukturen wurden für die Datei-API-Erweiterungen hinzugefügt. Alle Themen, die für diese Version aktualisiert wurden, sind als **vorläufig** markiert und können geändert werden.

    -   [**IpcfOpenFileOnHandle**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonhandle)
    -   [**IpcfOpenFileOnILockBytes**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfopenfileonilockbytes)
    -   [**IpcfGetFileProperty**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetfileproperty)
    -   [**IpcfLogicalFileRangeToRawFileRange**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcflogicalfilerangetorawfilerange)
    -   [**IpcfReadFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfreadfile)
    -   [**IpcfSetEndOfFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfsetendoffile)
    -   [**IpcfWriteFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfwritefile)

## April 2014-Update

-   Die **Datei-API-Speicherverwendung**, insbesondere für große PFILE-Dateien, wurde erheblich verbessert.
-   Die **Inhalts-ID** kann jetzt über die Eigenschaft **IPC\_LI\_CONTENT\_ID** geschrieben werden. Weitere Informationen finden Sie unter den Angaben zu [**Lizenzeigenschaftstypen**](/rights-management/sdk/2.1/api/win/License%20property%20types#msipc_license_property_types_IPC_LI_APP_SPECIFIC_DATA).
-   **Manifestanforderungen für die Produktion** – Wenn die RMS-fähige Anwendung bzw. der Diensts im Servermodus ausgeführt wird, ist kein Manifest mehr erforderlich. Weitere Informationen finden Sie unter [Anwendungstypen](application-types.md).
-   **Dokumentationsupdates**

    **Bewährte Testmethoden**: Anleitung zur Verwendung des lokalen Servers vor dem Testen mit Azure RMS hinzugefügt. Weitere Informationen finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

## Wichtige Hinweise für Entwickler

-   **Systemeigene Unterstützung für alle Dateitypen**

    Systemeigene Unterstützung kann für einen beliebigen Dateityp (Erweiterung) mit dieser Version des Rights Management Services SDK 2.1 hinzugefügt werden. Beispielsweise wird für jede &lt;ext&gt;-Erweiterung (nicht Office und PDF) \*.p&lt;ext&gt; verwendet, wenn die Administratorkonfiguration für diese Erweiterung NATIVE lautet.

    Weitere Informationen zu unterstützten Dateitypen finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

-   Auf **Windows 7 SP1- und Windows Server 2008 R2 SP1-Computern** ohne das Update [KB2533623](https://support.microsoft.com/en-us/kb/2533623) tritt möglicherweise der folgende Fehler beim Schutz von Office-Dateien auf: "Der Parameter ist falsch. Fehlercode: 0 x 80070057". Wenn dies angezeigt wird, installieren Sie das Update, und versuchen Sie es erneut. Wenn das Problem weiterhin auftritt, wenden Sie sich an die Feedbackstelle für die RMS SDK-Betaversion unter <rmcstbeta@microsoft.com>.

    **Hinweis**  Ab der April 2015-Version wurde dem Installationsvorgang eine Überprüfung für diese KB hinzugefügt.

     

-   **Datei-API-Integration**

    Die Active Directory Rights Management Services-Datei-API bietet durch das Hinzufügen der Datei-API die folgenden Vorteile und Funktionen.

      - Vertrauliche Daten können automatisch geschützt werden, ohne die Details der Information Rights Management (IRM)-Implementierung zu kennen, die von verschiedenen Dateiformaten verwendet wird.

      - Microsoft Office-Dateien, PDF-Dateien (Portable Document Format) und bestimmte weitere Dateitypen können mit systemeigenem Schutz geschützt werden. Eine vollständige Liste der Dateitypen, die mit systemeigenem Schutz geschützt werden können, finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

      - Alle Dateien außer System- und Office-Dateien können mit dem geschützten RMS-Dateiformat (PFILE) geschützt werden.

    Die Datei-API wird über die vier folgenden neuen Funktionen implementiert: [IpcfDecryptFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile), [IpcfEncryptFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile), [IpcfGetSerializedLicenseFromFile](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile) und [IpcfIsFileEncrypted](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted).

    Die Datei-API erfordert, dass der Rights Management Service Client 2.1 auf dem Clientcomputer installiert ist und dass der Computer mit einem RMS-Server verbunden ist. Weitere Informationen zu RMS-Server, RMS-Client und deren Funktionalität finden Sie im TechNet unter [Dokumentation zu RMS für IT-Spezialisten](https://technet.microsoft.com/en-us/library/cc771234(v=ws.10).aspx).

-   **Problem**: Wenn Sie eine Lizenz von Grund auf neu erstellen, müssen Sie Eigentumsrechte explizit gewähren.

    **Lösung**: Die Anwendung muss dem Lizenzinhaber explizit **Besitzerrechte** hinzufügen, wenn eine von Grund auf neue Lizenz mit [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch) erstellt wird. Weitere Informationen finden Sie unter [Hinzufügen expliziter Besitzerrechte](add-explicit-owner-rights.md).

-   **Problem**: Wenn eine Anwendung [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) oder [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) zweimal für das gleiche Fenster über dessen Handle aufruft, gibt das RMS SDK 2.1 in **HRESULT** einen Fehler zurück.

    **Lösung**: Spezielle Anweisungen hierzu finden Sie in [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow) und [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow) im Abschnitt "Hinweise".

-   **Problem**: Bei der Entwicklung für mehrere Architekturen müssen Sie diese Anweisungen verwenden.

    **Lösung**: Wenn Sie „Ipcsecproc\*isv.dll“ für eine andere Architektur verwenden möchten (Sie haben beispielsweise das 64-Bit-SDK auf einem 64-Bit-Computer installiert, möchten die Bereitstellung aber jetzt auf einem 32-Bit-Computer durchführen, auf dem „Ipcsecproc\*isv.dll“ erforderlich ist), müssen Sie das 32-Bit-SDK auf einem anderen Computer installieren und die Dateien „Ipcsecproc\*isv.dll“ vom Ordner „%PROGRAMFILES%\\Microsoft Information Protection And Control“ (dem Standardordner bzw. von dem Speicherort, den Sie für die Installation des SDK angegeben haben) dorthin kopieren.

## Häufig gestellte Fragen

**F**: Welches Standardverhalten gilt für die Sprache bei Funktionen, die einen LCID-Parameter akzeptieren?

**A**: Verwenden Sie 0 für das Standardgebietsschema. In diesem Fall sucht AD RMS-Client 2.1 in der folgenden Reihenfolge nach Namen und Beschreibungen und ruft die erste verfügbare Sprache auf:

    1 - User preferred LCID.
    2 - System locale LCID.
    3 - The first available language specified in the Rights Management Server (RMS) template.

Wenn kein Name und keine Beschreibung abgerufen werden kann, wird ein Fehler zurückgegeben. Es kann nur ein Name und eine Beschreibung für eine bestimmte LCID vorhanden sein.

## Verwandte Themen

* [Übersicht](ad-rms-overview.md)
* [Hinzufügen expliziter Besitzerrechte](add-explicit-owner-rights.md)
* [Datei-API-Konfiguration](file-api-configuration.md)
* [**IpcfGetSerializedLicenseFromFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfgetserializedlicensefromfile)
* [**IpcfEncryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfencryptfile)
* [**IpcfDecryptFile**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfdecryptfile)
* [**IpcfIsFileEncrypted**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcfisfileencrypted)
* [**IpcCreateLicenseFromScratch**](/rights-management/sdk/2.1/api/win/functions#msipc_ipccreatelicensefromscratch)
* [**IpcProtectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcprotectwindow)
* [**IpcUnprotectWindow**](/rights-management/sdk/2.1/api/win/functions#msipc_ipcunprotectwindow)
 

 


<!--HONumber=Jun16_HO2-->


