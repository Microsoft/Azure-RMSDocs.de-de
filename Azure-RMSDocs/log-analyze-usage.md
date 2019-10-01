---
title: Protokoll & Analysieren der Schutz Verwendung von Azure Information Protection
description: Informationen und Anweisungen zur Verwendung der Verwendungs Protokollierung für den Schutzdienst von Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 0052d3474c728518d3acdd9af3ef2d9aae1a2d0a
ms.sourcegitcommit: 319c0691509748e04aecf839adaeb3b5cac2d2cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71684359"
---
# <a name="logging-and-analyzing-the-protection-usage-from-azure-information-protection"></a>Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Verwenden Sie diese Informationen, um zu verstehen, wie Sie die Verwendungs Protokollierung für den Schutzdienst (Azure Rights Management) über Azure Information Protection verwenden können. Dieser Schutzdienst stellt den Datenschutz für die Dokumente und e-Mails Ihrer Organisation bereit und kann jede Anforderung an ihn protokollieren. Folgende Vorgänge zählen als Anforderungen: Benutzer schützen Dokumente und E-Mails und nutzen die Inhalte; Aktionen, die von Ihren Administratoren für diesen Dienst ausgeführt werden; Aktionen, die von Microsoft-Technikern zur Unterstützung Ihrer Azure Information Protection-Bereitstellung ausgeführt werden. 

Anschließend können Sie diese Schutz Verwendungs Protokolle verwenden, um die folgenden Geschäftsszenarien zu unterstützen:

-   **Analyse hinsichtlich geschäftlicher Erkenntnisse**

    Die vom Schutzdienst generierten Protokolle können in ein Repository ihrer Wahl importiert werden (z. b. eine Datenbank, ein OLAP-System (Online Analytical Processing) oder ein Map-Reduce-System), um die Informationen zu analysieren und Berichte zu erzeugen. Beispielsweise können Sie feststellen, wer auf Ihre geschützten Daten zugreift. Sie können ermitteln, auf welche geschützten Daten Benutzer zugreifen, von welchen Geräten aus und von wo. Sie können herausfinden, ob Benutzer geschützte Inhalte erfolgreich lesen können. Sie können ferner identifizieren, welche Personen ein wichtiges Dokument gelesen haben, das geschützt it.

-   **Überwachung auf Missbrauch**

    Protokollierungs Informationen zur Schutz Verwendung stehen Ihnen nahezu in Echtzeit zur Verfügung, sodass Sie die Verwendung des Schutz Dienstanbieter in Ihrem Unternehmen kontinuierlich überwachen können. 99,9 % der Protokolle sind innerhalb von 15 Minuten nach einer für den Dienst ausgelösten Aktion verfügbar.

    Beispielsweise können Sie sich benachrichtigen lassen, wenn ein plötzlicher Anstieg der Personen zu verzeichnen ist, die geschützte Daten außerhalb der Standardarbeitszeiten lesen, was darauf hindeuten kann, dass ein böswilliger Benutzer Informationen sammelt, um sie an die Konkurrenz zu verkaufen. Oder wenn derselbe Benutzer innerhalb eines kurzen Zeitraums offensichtlich von zwei verschiedenen IP-Adressen aus auf Daten zugreift, was darauf hindeuten kann, dass ein Benutzerkonto kompromittiert wurde.

-   **Durchführen forensischer Analysen**

    Wenn Sie ein Informationsleck haben, werden Sie wahrscheinlich gefragt, wer in der jüngsten Zeit auf bestimmte Dokumente zugegriffen hat, und auf welche Informationen eine verdächtigte Person zuletzt zugegriffen hat. Sie können diese Arten von Fragen beantworten, wenn Sie diese Protokollierung verwenden, weil Personen, die geschützte Inhalte verwenden, immer eine Rights Management Lizenz erhalten müssen, um Dokumente und Bilder zu öffnen, die durch Azure Information Protection geschützt sind, auch wenn diese Dateien verschoben werden. e-Mail oder Kopieren auf USB-Laufwerke oder andere Speichergeräte. Dies bedeutet, dass Sie diese Protokolle als definitive Informationsquelle für die forensische Analyse verwenden können, wenn Sie Ihre Daten mit Azure Information Protection schützen.

Zusätzlich zu dieser Verwendungsprotokollierung stehen folgende Protokollierungsoptionen zur Verfügung:

|Protokollierungsoption|Beschreibung|
|----------------|---------------|
|Administratorprotokoll|Protokolliert administrative Aufgaben für den Schutzdienst. Beispiele: der Dienst wird deaktiviert, das Administratorfeature wird aktiviert, Administratorberechtigungen für den Dienst werden an Benutzer delegiert. <br /><br />Weitere Informationen finden Sie im PowerShell-Cmdlet " [Get-aipserviceadminlog](/powershell/module/aipservice/get-aipserviceadminlog)".|
|Dokumentkontrolle|Ermöglicht Benutzern das Nachverfolgen und Widerrufen von Dokumenten, die sie mit dem Azure Information Protection-Client nachverfolgt haben. Globale Administratoren können diese Dokumente im Auftrag von Benutzern nachverfolgen. <br /><br />Weitere Informationen finden Sie unter [Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection](./rms-client/client-admin-guide-document-tracking.md).|
|Clientereignisprotokolle|Benutzeraktivität für den Azure Information Protection-Client, protokolliert im lokalen Windows-Ereignisprotokoll **Anwendungen und Dienste**: **Azure Information Protection**. <br /><br />Weitere Informationen finden Sie unter [Verwendungsprotokollierung für den Azure Information Protection-Client](./rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client).|
|Clientprotokolldateien|Problembehandlungsprotokolle für den Azure Information Protection-Client, die sich unter **%localappdata%\Microsoft\MSIP** befinden. <br /><br />Diese Dateien werden vom Microsoft Support benötigt.|

Darüber hinaus werden Informationen aus den Azure Information Protection-Clientnutzungsprotokollen und der Azure Information Protection-Überprüfung gesammelt und zusammengefasst, um im Azure-Portal Berichte zu erstellen. Weitere Informationen finden Sie unter [Berichterstellung für Azure Information Protection](reports-aip.md).

In den folgenden Abschnitten finden Sie weitere Informationen zur Verwendungs Protokollierung für den Schutzdienst. 

## <a name="how-to-enable-logging-for-protection-usage"></a>Aktivieren der Protokollierung für die Schutz Verwendung
Die Protokollierung der Schutz Nutzung ist standardmäßig für alle Kunden aktiviert. 

Es fallen keine zusätzlichen Kosten für den Protokollspeicher oder die Protokollierungsfunktionalität an.

## <a name="how-to-access-and-use-your-protection-usage-logs"></a>Zugreifen auf und Verwenden von Schutz Verwendungs Protokollen
Azure Information Protection schreibt Protokolle als eine Serie von BLOB in ein Azure Storage-Konto, das automatisch für Ihren Mandanten erstellt wird. Jedes BLOB enthält mindestens einen Protokolldatensatz im erweiterten W3C-Protokollformat. Die BLOB-Namen sind Zahlen in der Reihenfolge ihrer Erstellung. Im Abschnitt [Interpretieren von Azure Rights Management-Verwendungsprotokollen](#how-to-interpret-your-usage-logs) weiter unten in diesem Dokument finden Sie weitere Informationen zu den Protokollinhalten und deren Erstellung.

Es kann eine Weile dauern, bis Protokolle nach einer Schutz Aktion in Ihrem Speicherkonto angezeigt werden. Die meisten Protokolle werden innerhalb von 15 Minuten angezeigt. Es empfiehlt sich, dass Sie die Protokolle in den lokalen Speicher herunterladen, z. B. einen lokalen Ordner, eine Datenbank oder ein Zuordnen/Reduzieren-Repository.

Zum Herunterladen Ihrer Verwendungs Protokolle verwenden Sie das aipservice-PowerShell-Modul für Azure Information Protection. Installationsanweisungen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

### <a name="to-download-your-usage-logs-by-using-powershell"></a>So laden Sie Ihre Verwendungsprotokolle mit PowerShell herunter

1.  Starten Sie Windows PowerShell mit der Option **als Administrator ausführen** , und verwenden Sie das Cmdlet [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) , um eine Verbindung mit Azure Information Protection herzustellen:

    ```
    Connect-AipService
    ```
    
2.  Führen Sie den folgenden Befehl aus, um die Protokolle für ein bestimmtes Datum herunterzuladen: 

    ```
    Get-AipServiceUserLog -Path <location> -fordate <date>
    ```

    Angenommen, Sie haben einen Ordner namens „Protokolle“ auf Laufwerk E: erstellt:
    
    * Um Protokolle für ein bestimmtes Datum (z.B. 1.2.2016) herunterzuladen, führen Sie den folgenden Befehl aus: `Get-AipServiceUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Um Protokolle für einen Datumsbereich (z.B. 1.2.2016 bis 14.2.2016) herunterzuladen, führen Sie den folgenden Befehl aus: `Get-AipServiceUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Wenn Sie, wie in diesen Beispielen, nur den Tag angeben, wird 00:00:00 als Uhrzeit in Ihrer lokalen Uhrzeit angenommen und dann in UTC umgewandelt. Wenn Sie eine Uhrzeit für den -fromdate- oder -todate-Parameter angeben (z.B. -fordate "01.02.2016 15:00:00"), werden das Datum und die Uhrzeit in UTC umgewandelt. Der Get-aipserviceuserlog-Befehl ruft dann die Protokolle für diese UTC-Zeitspanne ab.

Die kleinste Zeitspanne, die Sie für ein Herunterladen angeben können, ist ein ganzer Tag.

Standardmäßig werden für dieses Cmdlet drei Threads verwendet, um die Protokolle herunterzuladen. Ist genügend Netzwerkbandbreite verfügbar und möchten Sie die Zeit verkürzen, die zum Herunterladen der Protokolle erforderlich ist, verwenden Sie den -NumberOfThreads-Parameter, der jeden Wert von 1 bis 32 unterstützt. Wenn Sie beispielsweise den folgenden Befehl ausführen, erzeugt das Cmdlet 10 Threads, um die Protokolle herunterzuladen: `Get-AipServiceUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> Sie können mit dem [Protokollparser von Microsoft](https://www.microsoft.com/download/details.aspx?id=24659) alle heruntergeladenen Protokolldateien in einem CSV-Format aggregieren. Dies ist ein Tool zum Konvertieren zwischen verschiedenen bekannten Protokollformaten. Sie können mit diesem Tool auch Daten in das SYSLOG-Format konvertieren oder in eine Datenbank importieren. Nachdem Sie das Tool installiert haben, führen Sie `LogParser.exe /?` aus, um Hilfe und Informationen zu diesem Tool anzuzeigen. 
>
> Beispielsweise können Sie folgenden Befehl ausführen, um alle Informationen in eine Datei im LOG-Format zu importieren: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

## <a name="how-to-interpret-your-usage-logs"></a>Interpretieren der Verwendungs Protokolle
Verwenden Sie die folgenden Informationen, um die Schutz Verwendungs Protokolle zu interpretieren.

### <a name="the-log-sequence"></a>Die Abfolge von Protokollen
Azure Information Protection schreibt die Protokolle als eine Serie von blobvorgängen.

Jeder Eintrag im Protokoll hat einen UTC-Zeitstempel. Da der Schutzdienst auf mehreren Servern in mehreren Rechenzentren ausgeführt wird, scheinen die Protokolle möglicherweise nicht in der Reihenfolge zu sein, auch wenn Sie nach Zeitstempel sortiert sind. Die Abweichung ist jedoch in der Regel gering und liegt im Bereich von einer Minute. In den meisten Fällen ist dies kein Problem, das sich nachteilig bei der Protokollanalyse manifestieren würde.

### <a name="the-blob-format"></a>Das BLOB-Format
Jedes BLOB ist im erweiterten W3C-Protokollformat. Es beginnt mit den folgenden zwei Zeilen:

**#Software: RMS**

**#Version: 1.1**

Die erste Zeile identifiziert, dass es sich hierbei um Schutz Protokolle aus Azure Information Protection handelt. Die zweite Zeile gibt an, dass der Rest des BLOBs die Spezifikation der Version 1.1 einhält. Wir empfehlen, dass alle Anwendungen, die diese Protokolle analysieren, diese beiden Zeilen überprüfen, bevor sie die Analyse des Rests des BLOBs fortsetzen.

In der dritten Zeile wird eine Liste von Feldnamen aufgezählt, die durch Tabstopps voneinander getrennt sind:

**#Felder: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip            admin-action            acting-as-user**

Jede der folgenden Zeilen stellt einen Protokolldatensatz dar. Die Werte der Felder sind in derselben Reihenfolge wie die vorangehende Zeile, auch durch Tabstopps getrennt. Verwenden Sie die folgende Tabelle, um die Felder zu interpretieren.


|   Feldname   | W3C-Datentyp |                                                                                                                                                                          Beschreibung                                                                                                                                                                          |                                                            Beispielwert                                                            |
|----------------|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------|
|      date      |     Datum      |                                                                                                                     Das UTC-Datum, an dem die Anforderung verarbeitet wurde.<br /><br />Die Quelle ist die lokale Uhr auf dem Server, von dem die Anforderung bearbeitet wurde.                                                                                                                     |                                                             2013-06-25                                                              |
|      time      |     Zeit      |                                                                                                            Die UTC-Zeit im 24-Stunden-Format, zu der die Anforderung verarbeitet wurde.<br /><br />Die Quelle ist die lokale Uhr auf dem Server, von dem die Anforderung bearbeitet wurde.                                                                                                            |                                                              21:59:28                                                               |
|     row-id     |     Text      |                                                                           Eindeutige GUID für diesen Protokolldatensatz. Wenn ein Wert nicht vorhanden ist, verwenden Sie zum Identifizieren des Eintrags die Korrelations-ID.<br /><br />Dieser Wert ist hilfreich, wenn Sie Protokolle aggregieren oder in ein anderes Format kopieren.                                                                           |                                                1c3fe7a9-d9e0-4654-97b7-14fafa72ea63                                                 |
|  request-type  |     Name      |                                                                                                                                                            Der Name der angeforderten RMS-API.                                                                                                                                                            |                                                           AcquireLicense                                                            |
|    user-id     |    Zeichenfolge     |                                                               Der Benutzer, der die Anforderung gesendet hat.<br /><br />Der Wert steht in einfachen Anführungszeichen. Aufrufe von einem Mandantenschlüssel, der von Ihnen verwaltet wird (BYOK), haben einen Wert von **"** , der auch gilt, wenn die Anforderungstypen anonym sind.                                                                |                                                          ‘joe@contoso.com’                                                          |
|     result     |    Zeichenfolge     |                                                                                                                  'Success', wenn die Anforderung erfolgreich verarbeitet wurde.<br /><br />Der Fehlertyp in einfachen Anführungszeichen zeigt an, wenn die Anforderung fehlgeschlagen ist.                                                                                                                   |                                                              'Success'                                                              |
| correlation-id |     Text      |                                                                                                 Eine GUID, die das RMS-Clientprotokoll und das Serverprotokoll für eine bestimmte Anforderung gemeinsam haben.<br /><br />Dieser Wert kann bei der Behandlung von Clientproblemen hilfreich sein.                                                                                                 |                                                cab52088-8925-4371-be34-4b71a3112356                                                 |
|   content-id   |     Text      |                                                                      Eine GUID in geschweiften Klammern, die den geschützten Inhalt identifiziert (z. B. ein Dokument).<br /><br />Dieses Feld hat nur dann einen Wert, wenn „request-type“ den Wert „AcquireLicense“ hat, und ist bei allen anderen Anforderungstypen leer.                                                                       |                                               {bb4af47b-cfed-4719-831d-71b98191a4f2}                                                |
|  owner-email   |    Zeichenfolge     |                                                                                                                       Die E-Mail-Adresse des Besitzers des Dokuments.<br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.                                                                                                                        |                                                          alice@contoso.com                                                          |
|     issuer     |    Zeichenfolge     |                                                                                                                          Die E-Mail-Adresse des Ausstellers des Dokuments. <br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.                                                                                                                          |                       alice@contoso.com (oder) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'                       |
|  template-id   |    Zeichenfolge     |                                                                                                                    ID der Vorlage, die zum Schützen des Dokuments verwendet wurde. <br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.                                                                                                                     |                                               {6d9371a6-4e2d-4e97-9a38-202233fed26e}                                                |
|   file-name    |    Zeichenfolge     | Dateiname eines geschützten Dokuments, das mit dem Azure Information Protection-Client für Windows nachverfolgt wird. <br /><br />Derzeit werden einige Dateien (z.B. Office-Dokumente) als GUIDs und nicht beim tatsächlichen Dateinamen angezeigt.<br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist. |                                                       TopSecretDocument.docx                                                        |
| date-published |     date      |                                                                                                                          Das Datum, an dem das Dokument geschützt wurde.<br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.                                                                                                                           |                                                         2015-10-15T21:37:00                                                         |
|     c-info     |    Zeichenfolge     |                                                                                   Informationen zur Clientplattform, von der die Anforderung gesendet wird.<br /><br />Die spezifische Zeichenfolge variiert in Abhängigkeit von der Anwendung (z. B. Betriebssystem oder Browser).                                                                                   | 'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64' |
|      c-ip      |    Adresse    |                                                                                                                                                       Die IP-Adresse des Clients, von dem die Anforderung stammt.                                                                                                                                                        |                                                            64.51.202.144                                                            |
|  admin-aktion  |     Bool      |                                                                                                                                    Gibt an, ob ein Administrator auf die Website zur Dokumentennachverfolgung im Administratormodus zugegriffen hat.                                                                                                                                    |                                                                True                                                                 |
| fungiert-als-benutzer |    Zeichenfolge     |                                                                                                                               Die E-Mail-Adresse des Benutzers von der aus ein Administrator auf die Website zur Dokumentennachverfolgung zugreift.                                                                                                                                |                                                          'joe@contoso.com'                                                          |

#### <a name="exceptions-for-the-user-id-field"></a>Ausnahmen für das Feld „user-id“
Obgleich das Feld „user-id“ normalerweise den Benutzer angibt, von dem die Anforderung stammt, gibt es zwei Ausnahmen, bei denen der Wert keinem echten Benutzer entspricht:

-   Der Wert **'microsoftrmsonline@&lt;IhreMandantenID&gt;.rms.&lt;Region&gt;.aadrm.com'** .

    Dies zeigt an, dass die Anforderung von einem Office 365-Dienst wie Exchange Online oder SharePoint Online stammt. In der Zeichenfolge steht *&lt;IhreMandantenID&gt;* für die GUID Ihres Mandanten und *&lt;Region&gt;* für die Region, in der Ihr Mandant registriert ist. Beispielsweise steht **Na** für Nordamerika, **Eu** für Europa und **ap** für Asien.

-   Wenn Sie den RMS-Verbindungsdienst verwenden.

    Anforderungen von diesem Connector werden mit dem Dienstprinzipalnamen von **Aadrm_S-1-7-0** protokolliert, der automatisch generiert wird, wenn Sie den RMS-Connector installieren.

#### <a name="typical-request-types"></a>Typische Anforderungstypen
Es gibt viele Anforderungs Typen für den Schutzdienst, aber in der folgenden Tabelle sind einige der am häufigsten verwendeten Anforderungs Typen aufgeführt.

|Anforderungstyp|Beschreibung|
|----------------|---------------|
|AcquireLicense|Ein Client von einem Windows-basierten Computer fordert eine Lizenz für geschützte Inhalte an.|
|AcquirePreLicense|Ein Client fordert im Auftrag des Benutzers eine Lizenz für geschützte Inhalte an.|
|AcquireTemplates|Ein Aufruf wird ausgelöst, um Vorlagen anhand von Vorlagen-IDs abzurufen.|
|AcquireTemplateInformation|Ein Aufruf wird ausgelöst, um die IDs der Vorlage vom Dienst abzurufen.|
|AddTemplate|Vom Azure-Portal wird ein Aufruf zum Hinzufügen einer Vorlage ausgelöst.|
|AllDocsCsv|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf zum Herunterladen der CSV-Datei von der Seite **Alle Dokumente**.|
|BECreateEndUserLicenseV1|Von einem Mobilgerät wird ein Aufruf ausgelöst, um eine Endbenutzerlizenz zu erstellen.|
|BEGetAllTemplatesV1|Von einem Mobilgerät (Back-End) wird ein Aufruf ausgelöst, um alle Vorlagen abzurufen.|
|Certify|Der Benutzer wird vom Client für die Verwendung und Erstellung von geschütztem Inhalt zertifiziert.|
|DeleteTemplateById|Vom Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage nach Vorlagen-ID zu löschen.|
|DocumentEventsCsv|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf zum Herunterladen der CSV-Datei für ein einziges Dokument.|
|ExportTemplateById|Vom Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage anhand einer Vorlagen-ID zu exportieren.|
|FECreateEndUserLicenseV1|Ähnlich wie bei der „AcquireLicense“-Anforderung, aber von mobilen Geräten aus.|
|FECreatePublishingLicenseV1|Identisch mit „Certify“ und „GetClientLicensorCert“ in Kombination, von mobilen Clients aus.|
|FEGetAllTemplates|Von einem Mobilgerät (Front-End) wird ein Aufruf ausgelöst, um die Vorlagen abzurufen.|
|FindServiceLocationsForUser|Ein Aufruf zum Abfragen von URLs wird ausgelöst, die zum Aufrufen von „Certify“ oder von „AcquireLicense“ verwendet werden.|
|GetAllDocs|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf zum Laden der Seite **Alle Dokumente** für einen Benutzer oder zum Durchsuchen aller Dokumente des Mandanten. Verwenden Sie diesen Wert in den Feldern „admin-action“ (Adminaktion) und „acting-as-user“ (Fungiert als Benutzer):<br /><br />- „admin-action“ ist leer: Ein Benutzer zeigt die Seite **Alle Dokumente** für seine eigenen Dokumente an.<br /><br />- admin-action ist TRUE und acting-as-user ist leer: Ein Administrator zeigt alle Dokumente für seinen Mandanten an.<br /><br />- admin-action ist TRUE und acting-as-user ist nicht leer: Ein Administrator zeigt die Seite **Alle Dokumente** für einen Benutzer an.|
|GetAllTemplates|Vom Azure-Portal wird ein Aufruf ausgelöst, um alle Vorlagen abzurufen.|
|GetClientLicensorCert|Der Client fordert von einem Windows-basierten Computer aus ein Veröffentlichungszertifikat an (das später zum Schützen von Inhalt verwendet wird).|
|GetConfiguration|Ein Azure PowerShell-Cmdlet wird aufgerufen, um die Konfiguration des Azure RMS-Mandanten abzurufen.|
|GetConnectorAuthorizations|Von den RMS-Connectors wird ein Aufruf ausgelöst, um deren Konfiguration aus der Cloud abzurufen.|
|GetRecipients|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, für ein einzelnes Dokument zur Listenansicht zu navigieren.|
|GetSingle|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, zur Seite **Einzelnes Dokument** zu navigieren.|
|GetTenantFunctionalState|Der Azure-Portal überprüft, ob der Schutzdienst (Azure Rights Management) aktiviert ist.|
|GetTemplateById|Vom Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage mit einer angegebenen Vorlagen-ID abzurufen.|
|KeyVaultDecryptRequest|Der Client versucht, den RMS-geschützten Inhalt zu entschlüsseln. Gilt nur für einen vom Kunden verwalteten Mandantenschlüssel (BYOK) in Azure Key Vault.|
|KeyVaultGetKeyInfoRequest|Ein Aufruf erfolgt, um zu überprüfen, ob der angegebene Schlüssel, der in Azure Key Vault als Azure Information Protection-Mandantenschlüssel verwendet werden soll, verfügbar ist und nicht bereits verwendet wird.|
|KeyVaultSignDigest|Ein Aufruf erfolgt, wenn ein vom Kunden verwalteter Schlüssel (BYOK) in Azure Key Vault zu Signaturzwecken verwendet wird. Dieser Aufruf erfolgt normalerweise einmal pro „AcquireLicence“ (oder „FECreateEndUserLicenseV1“), „Certify“ und „GetClientLicensorCert“ (oder „FECreatePublishingLicenseV1“).|
|KMSPDecrypt|Der Client versucht, den RMS-geschützten Inhalt zu entschlüsseln. Gilt nur für einen vom Kunden verwalteten Legacymandantenschlüssel (BYOK).|
|KMSPSignDigest|Ein Aufruf erfolgt, wenn ein vom Kunden verwalteter Legacyschlüssel (BYOK) zu Signaturzwecken verwendet wird. Dieser Aufruf erfolgt normalerweise einmal pro „AcquireLicence“ (oder „FECreateEndUserLicenseV1“), „Certify“ und „GetClientLicensorCert“ (oder „FECreatePublishingLicenseV1“).|
|LoadEventsForMap|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, für ein einzelnes Dokument zur Kartenansicht zu navigieren.|
|LoadEventsForSummary|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, für ein einzelnes Dokument zur Zeitachsenansicht zu navigieren.|
|LoadEventsForTimeline|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, für ein einzelnes Dokument zur Kartenansicht zu navigieren.|
|ImportTemplate|Vom Azure-Portal wird ein Aufruf zum Importieren einer Vorlage ausgelöst.|
|RevokeAccess|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, ein Dokument zu sperren.|
|SearchUsers |Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, alle Benutzer in einem Mandanten zu suchen.|
|ServerCertify|Von einem RMS-fähigen Client (z. B. SharePoint) wird ein Aufruf zum Zertifizieren des Servers ausgelöst.|
|SetUsageLogFeatureState|Ein Aufruf zum Aktivieren der Verwendungsprotokollierung wird ausgelöst.|
|SetUsageLogStorageAccount|Ein Aufruf wird ausgelöst, um den Speicherort der Protokolle des Azure Rights Management-Diensts anzugeben.|
|UpdateNotificationSettings|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, die Benachrichtigungseinstellungen für ein einzelnes Dokument zu ändern.|
|UpdateTemplate|Vom Azure-Portal wird ein Aufruf zum Aktualisieren einer vorhandenen Vorlage ausgelöst.|


## <a name="powershell-reference"></a>PowerShell-Referenz

Das einzige PowerShell-Cmdlet, das Sie für den Zugriff auf die Protokollierung der Schutz Verwendung benötigen, ist [Get-aipserviceuserlog](/powershell/module/aipservice/get-aipserviceuserlog). 

Weitere Informationen zur Verwendung von PowerShell für Azure Information Protection finden Sie unter [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](administer-powershell.md).
