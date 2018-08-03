---
title: Anmelden und Analysieren der Nutzung des Azure RMS-Diensts – AIP
description: Informationen und Anweisungen zum Einsatz der Verwendungsprotokollierung mit Azure Rights Management (Azure RMS).
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 98fe9b957d577cc59a719dbe5a7ba3b532ea8c87
ms.sourcegitcommit: 44ff610dec678604c449d42cc0b0863ca8224009
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39371406"
---
# <a name="logging-and-analyzing-usage-of-the-azure-rights-management-service"></a>Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Anhand der folgenden Informationen erhalten Sie eine Übersicht darüber, wie Sie die Verwendungsprotokollierung für den Azure Rights Management-Dienst von Azure Information Protection verwenden können. Dieser Dienst stellt den Datenschutz für die Dokumente und E-Mails Ihrer Organisation bereit und kann jede diesbezügliche Anforderung protokollieren. Folgende Vorgänge zählen als Anforderungen: Benutzer schützen Dokumente und E-Mails und nutzen die Inhalte; Aktionen, die von Ihren Administratoren für diesen Dienst ausgeführt werden; Aktionen, die von Microsoft-Technikern zur Unterstützung Ihrer Azure Information Protection-Bereitstellung ausgeführt werden. 

Sie können dann mithilfe dieser Protokolle des Azure Rights Management-Diensts die folgenden Geschäftsszenarios unterstützen:

-   **Analyse hinsichtlich geschäftlicher Erkenntnisse**

    Die vom Azure Rights Management-Dienst generierten Protokolle können in ein Repository Ihrer Wahl importiert werden (z.B. eine Datenbank, ein OLAP-System (Online Analytical Processing) oder ein Zuordnen/Reduzieren-System), um die Informationen zu analysieren und Berichte zu erstellen. Beispielsweise können Sie feststellen, wer auf Ihre geschützten Daten zugreift. Sie können ermitteln, auf welche geschützten Daten Benutzer zugreifen, von welchen Geräten aus und von wo. Sie können herausfinden, ob Benutzer geschützte Inhalte erfolgreich lesen können. Sie können ferner identifizieren, welche Personen ein wichtiges Dokument gelesen haben, das geschützt ist.

-   **Überwachung auf Missbrauch**

    Azure Rights Management-Protokollierungsinformationen stehen Ihnen praktisch in Echtzeit zur Verfügung, sodass Sie die Verwendung des Rights Management-Diensts in Ihrem Unternehmen kontinuierlich überwachen können. 99,9 % der Protokolle sind innerhalb von 15 Minuten nach einer für den Dienst ausgelösten Aktion verfügbar.

    Beispielsweise können Sie sich benachrichtigen lassen, wenn ein plötzlicher Anstieg der Personen zu verzeichnen ist, die geschützte Daten außerhalb der Standardarbeitszeiten lesen, was darauf hindeuten kann, dass ein böswilliger Benutzer Informationen sammelt, um sie an die Konkurrenz zu verkaufen. Oder wenn derselbe Benutzer innerhalb eines kurzen Zeitraums offensichtlich von zwei verschiedenen IP-Adressen aus auf Daten zugreift, was darauf hindeuten kann, dass ein Benutzerkonto kompromittiert wurde.

-   **Durchführen forensischer Analysen**

    Wenn Sie ein Informationsleck haben, werden Sie wahrscheinlich gefragt, wer in der jüngsten Zeit auf bestimmte Dokumente zugegriffen hat, und auf welche Informationen eine verdächtigte Person zuletzt zugegriffen hat. Sie können diese Arten von Fragen beantworten, wenn Sie diese Protokollierung verwenden. Personen, die geschützte Inhalte verwenden, müssen nämlich immer eine Rights Management-Lizenz abrufen, um Dokumente und Bilder zu öffnen, die durch den Azure Rights Management-Dienst geschützt sind. Das gilt auch dann, wenn diese Dateien per E-Mail verschoben oder auf USB-Laufwerke oder andere Speichergeräte kopiert werden. Dies bedeutet, dass Sie diese Protokolle als maßgebliche Quelle für Informationen zur forensischen Analyse verwenden können, wenn Sie Ihre Daten mithilfe des Azure Rights Management-Diensts schützen.

Zusätzlich zu dieser Verwendungsprotokollierung stehen folgende Protokollierungsoptionen zur Verfügung:

|Protokollierungsoption|Beschreibung|
|----------------|---------------|
|Administratorprotokoll|Protokolliert administrative Aufgaben für den Azure Rights Management-Dienst. Beispiele: der Dienst wird deaktiviert, das Administratorfeature wird aktiviert, Administratorberechtigungen für den Dienst werden an Benutzer delegiert. <br /><br />Weitere Informationen finden Sie im PowerShell-Cmdlet [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog).|
|Dokumentkontrolle|Ermöglicht Benutzern das Nachverfolgen und Sperren von Dokumenten, die sie mit dem Azure Information Protection-Client oder der RMS-Freigabe-App nachverfolgt haben. Globale Administratoren können diese Dokumente im Auftrag von Benutzern nachverfolgen. <br /><br />Weitere Informationen finden Sie unter [Konfigurieren und Verwenden der Dokumentenverfolgung für Azure Information Protection](../rms-client/client-admin-guide-document-tracking.md).|
|Clientereignisprotokolle|Benutzeraktivität für den Azure Information Protection-Client, protokolliert im lokalen Windows-Ereignisprotokoll **Anwendungen und Dienste**: **Azure Information Protection**. <br /><br />Weitere Informationen finden Sie unter [Verwendungsprotokollierung für den Azure Information Protection-Client](../rms-client/client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client).|
|Clientprotokolldateien|Problembehandlungsprotokolle für den Azure Information Protection-Client, die sich unter **%localappdata%\Microsoft\MSIP** befinden. <br /><br />Diese Dateien werden vom Microsoft Support benötigt.|


In den folgenden Abschnitten finden Sie Informationen zur Verwendungsprotokollierung für den Azure Rights Management-Dienst. 

## <a name="how-to-enable-azure-rights-management-usage-logging"></a>Aktivieren der Verwendungsprotokollierung von Azure Rights Management
Seit Februar 2016 ist die Azure Rights Management-Verwendungsprotokollierung standardmäßig für alle Kunden aktiviert. Dies gilt für Kunden, die ihren Azure Rights Management-Dienst vor Februar 2016 aktiviert haben, und für Kunden, die den Dienst nach Februar 2016 aktiviert haben. 

> [!NOTE]
> Es fallen keine zusätzlichen Kosten für den Protokollspeicher oder die Protokollierungsfunktionalität an.
> 
> Wenn Sie die Verwendungsprotokollierung für Azure Rights Management vor Februar 2016 verwendet haben, benötigten Sie ein Abonnement für Azure und ausreichend Speicherplatz auf Azure, was nun nicht mehr der Fall ist.



## <a name="how-to-access-and-use-your-azure-rights-management-usage-logs"></a>Zugreifen auf und Verwenden von Azure Rights Management-Verwendungsprotokollen
Der Azure Rights Management-Dienst schreibt Protokolle als eine Serie von Blobs in Ihr Azure-Speicherkonto. Jedes BLOB enthält mindestens einen Protokolldatensatz im erweiterten W3C-Protokollformat. Die BLOB-Namen sind Zahlen in der Reihenfolge ihrer Erstellung. Im Abschnitt [Interpretieren von Azure Rights Management-Verwendungsprotokollen](#how-to-interpret-your-azure-rights-management-usage-logs) weiter unten in diesem Dokument finden Sie weitere Informationen zu den Protokollinhalten und deren Erstellung.

Es kann einen Moment dauern, bis nach einer Azure Rights Management-Aktion Protokolle in Ihrem Speicherkonto angezeigt werden. Die meisten Protokolle werden innerhalb von 15 Minuten angezeigt. Es empfiehlt sich, dass Sie die Protokolle in den lokalen Speicher herunterladen, z. B. einen lokalen Ordner, eine Datenbank oder ein Zuordnen/Reduzieren-Repository.

Um die Verwendungsprotokolle herunterzuladen, verwenden Sie das Azure Rights Management-Administrationsmodul für Windows PowerShell. Installationsanweisungen finden Sie unter [Installieren des AADRM-PowerShell-Moduls](install-powershell.md). Wenn Sie dieses Windows PowerShell-Modul zuvor heruntergeladen haben, überprüfen Sie anhand des folgenden Befehls, ob Sie Version **2.4.0.0** oder höher verwenden: `(Get-Module aadrm -ListAvailable).Version` 

### <a name="to-download-your-usage-logs-by-using-powershell"></a>So laden Sie Ihre Verwendungsprotokolle mit PowerShell herunter

1.  Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen**, und stellen Sie mit dem Cmdlet [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) eine Verbindung mit dem Azure Rights Management-Dienst her:

    ```
    Connect-AadrmService
    ```
    
2.  Führen Sie den folgenden Befehl aus, um die Protokolle für ein bestimmtes Datum herunterzuladen: 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    Angenommen, Sie haben einen Ordner namens „Protokolle“ auf Laufwerk E: erstellt:
    
    * Um Protokolle für ein bestimmtes Datum (z.B. 1.2.2016) herunterzuladen, führen Sie den folgenden Befehl aus: `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Um Protokolle für einen Datumsbereich (z.B. 1.2.2016 bis 14.2.2016) herunterzuladen, führen Sie den folgenden Befehl aus: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Wenn Sie, wie in diesen Beispielen, nur den Tag angeben, wird 00:00:00 als Uhrzeit in Ihrer lokalen Uhrzeit angenommen und dann in UTC umgewandelt. Wenn Sie eine Uhrzeit für den -fromdate- oder -todate-Parameter angeben (z.B. -fordate "01.02.2016 15:00:00"), werden das Datum und die Uhrzeit in UTC umgewandelt. Der Get-AadrmUserLog-Befehl ruft dann die Protokolle für diese UTC-Zeitspanne ab.

Die kleinste Zeitspanne, die Sie für ein Herunterladen angeben können, ist ein ganzer Tag.

Standardmäßig werden für dieses Cmdlet drei Threads verwendet, um die Protokolle herunterzuladen. Ist genügend Netzwerkbandbreite verfügbar und möchten Sie die Zeit verkürzen, die zum Herunterladen der Protokolle erforderlich ist, verwenden Sie den -NumberOfThreads-Parameter, der jeden Wert von 1 bis 32 unterstützt. Wenn Sie beispielsweise den folgenden Befehl ausführen, erzeugt das Cmdlet 10 Threads, um die Protokolle herunterzuladen: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> Sie können mit dem [Protokollparser von Microsoft](https://www.microsoft.com/download/details.aspx?id=24659) alle heruntergeladenen Protokolldateien in einem CSV-Format aggregieren. Dies ist ein Tool zum Konvertieren zwischen verschiedenen bekannten Protokollformaten. Sie können mit diesem Tool auch Daten in das SYSLOG-Format konvertieren oder in eine Datenbank importieren. Nachdem Sie das Tool installiert haben, führen Sie `LogParser.exe /?` aus, um Hilfe und Informationen zu diesem Tool anzuzeigen. 
>
> Beispielsweise können Sie folgenden Befehl ausführen, um alle Informationen in eine Datei im LOG-Format zu importieren: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### <a name="if-you-manually-enabled-azure-rights-management-usage-logging-before-the-logging-change-february-22-2016"></a>Wenn Sie die Azure Rights Management-Verwendungsprotokollierung vor der Protokollierungsänderung (22. Februar 2016) manuell aktiviert haben


Wenn Sie Verwendungsprotokollierung vor der Protokollierungsänderung verwendet haben, haben Sie Verwendungsprotokolle in Ihrem konfigurierten Azure-Speicherkonto. Microsoft kopiert diese Protokolle nicht als Teil dieser Protokollierungsänderung aus Ihrem Speicherkonto in das neue verwaltete Azure Rights Management-Speicherkonto. Sie sind dafür zuständig, den Lebenszyklus der zuvor generierten Protokolle zu verwalten, und Sie können das [Get-AadrmUsageLog](/powershell/aadrm/vlatest/get-aadrmusagelog)-Cmdlet verwenden, um Ihre alten Protokolle herunterzuladen. Beispiel:

- So laden Sie alle verfügbaren Protokolle in Ihren Ordner „E:\logs“ herunter: `Get-AadrmUsageLog -Path "E:\Logs"`
    
- So laden Sie einen bestimmten Bereich von Blobs herunter: `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

Sie müssen keine Protokolle mit dem Get-AadrmUsageLog-Cmdlet herunterladen, wenn einer der folgenden Punkte zutrifft:

-  Sie haben den Azure Rights Management-Dienst am oder vor dem 22. Februar 2016 aktiviert, haben die Verwendungsprotokollierung aber nicht aktiviert.

- Sie haben den Azure Rights Management-Dienst nach dem 22. Februar 2016 aktiviert.

## <a name="how-to-interpret-your-azure-rights-management-usage-logs"></a>Interpretieren von Azure Rights Management-Verwendungsprotokollen
Verwenden Sie folgende Informationen als Hilfestellung bei der Interpretation der Azure Rights Management-Verwendungsprotokolle.

### <a name="the-log-sequence"></a>Die Abfolge von Protokollen
Der Azure Rights Management-Dienst schreibt die Protokolle als eine Serie von Blobs. 

Jeder Eintrag im Protokoll hat einen UTC-Zeitstempel. Da der Azure Rights Management-Dienst auf mehreren Servern in mehreren Rechenzentren ausgeführt wird, scheinen die Protokolle manchmal nicht in der richtigen Reihenfolge zu sein, auch wenn sie nach Zeitstempel sortiert sind. Die Abweichung ist jedoch in der Regel gering und liegt im Bereich von einer Minute. In den meisten Fällen ist dies kein Problem, das sich nachteilig bei der Protokollanalyse manifestieren würde.

### <a name="the-blob-format"></a>Das BLOB-Format
Jedes BLOB ist im erweiterten W3C-Protokollformat. Es beginnt mit den folgenden zwei Zeilen:

**#Software: RMS**

**#Version: 1.1**

Die erste Zeile gibt an, dass es sich um Azure Rights Management-Protokolle handelt. Die zweite Zeile gibt an, dass der Rest des BLOBs die Spezifikation der Version 1.1 einhält. Wir empfehlen, dass alle Anwendungen, die diese Protokolle analysieren, diese beiden Zeilen überprüfen, bevor sie die Analyse des Rests des BLOBs fortsetzen.

In der dritten Zeile wird eine Liste von Feldnamen aufgezählt, die durch Tabstopps voneinander getrennt sind:

**#Felder: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip            admin-action            acting-as-user**

Jede der folgenden Zeilen stellt einen Protokolldatensatz dar. Die Werte der Felder sind in derselben Reihenfolge wie die vorangehende Zeile, auch durch Tabstopps getrennt. Verwenden Sie die folgende Tabelle, um die Felder zu interpretieren.

|Feldname|W3C-Datentyp|Beschreibung|Beispielwert|
|--------------|-----------------|---------------|-----------------|
|date|Datum|Das UTC-Datum, an dem die Anforderung verarbeitet wurde.<br /><br />Die Quelle ist die lokale Uhr auf dem Server, von dem die Anforderung bearbeitet wurde.|2013-06-25|
|time|Zeit|Die UTC-Zeit im 24-Stunden-Format, zu der die Anforderung verarbeitet wurde.<br /><br />Die Quelle ist die lokale Uhr auf dem Server, von dem die Anforderung bearbeitet wurde.|21:59:28|
|row-id|Text|Eindeutige GUID für diesen Protokolldatensatz. Wenn ein Wert nicht vorhanden ist, verwenden Sie zum Identifizieren des Eintrags die Korrelations-ID.<br /><br />Dieser Wert ist hilfreich, wenn Sie Protokolle aggregieren oder in ein anderes Format kopieren.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|Name|Der Name der angeforderten RMS-API.|AcquireLicense|
|user-id|Zeichenfolge|Der Benutzer, der die Anforderung gesendet hat.<br /><br />Der Wert steht in einfachen Anführungszeichen. Aufrufe von einem Mandantenschlüssel, der von Ihnen verwaltet wird (BYOK), haben einen Wert von **"**, der auch gilt, wenn die Anforderungstypen anonym sind.|‘joe@contoso.com’|
|result|Zeichenfolge|'Success', wenn die Anforderung erfolgreich verarbeitet wurde.<br /><br />Der Fehlertyp in einfachen Anführungszeichen zeigt an, wenn die Anforderung fehlgeschlagen ist.|'Success'|
|correlation-id|Text|Eine GUID, die das RMS-Clientprotokoll und das Serverprotokoll für eine bestimmte Anforderung gemeinsam haben.<br /><br />Dieser Wert kann bei der Behandlung von Clientproblemen hilfreich sein.|cab52088-8925-4371-be34-4b71a3112356|
|content-id|Text|Eine GUID in geschweiften Klammern, die den geschützten Inhalt identifiziert (z. B. ein Dokument).<br /><br />Dieses Feld hat nur dann einen Wert, wenn „request-type“ den Wert „AcquireLicense“ hat, und ist bei allen anderen Anforderungstypen leer.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|owner-email|Zeichenfolge|Die E-Mail-Adresse des Besitzers des Dokuments.<br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.|alice@contoso.com|
|issuer|Zeichenfolge|Die E-Mail-Adresse des Ausstellers des Dokuments. <br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.|alice@contoso.com (oder) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'|
|template-id|Zeichenfolge|ID der Vorlage, die zum Schützen des Dokuments verwendet wurde. <br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|file-name|Zeichenfolge|Der Dateiname eines geschützten Dokuments, das mit dem Azure Information Protection-Client für Windows oder mit der Rights Management-Freigabeanwendung für Windows nachverfolgt wird. <br /><br />Derzeit werden einige Dateien (z.B. Office-Dokumente) als GUIDs und nicht beim tatsächlichen Dateinamen angezeigt.<br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.|TopSecretDocument.docx|
|date-published|Datum|Das Datum, an dem das Dokument geschützt wurde.<br /><br /> Dieses Feld ist leer, wenn der Anforderungstyp „RevokeAccess“ ist.|2015-10-15T21:37:00|
|c-info|Zeichenfolge|Informationen zur Clientplattform, von der die Anforderung gesendet wird.<br /><br />Die spezifische Zeichenfolge variiert in Abhängigkeit von der Anwendung (z. B. Betriebssystem oder Browser).|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|Adresse|Die IP-Adresse des Clients, von dem die Anforderung stammt.|64.51.202.144|
|admin-aktion|Bool|Gibt an, ob ein Administrator auf die Website zur Dokumentennachverfolgung im Administratormodus zugegriffen hat.|True|
|fungiert-als-benutzer|Zeichenfolge|Die E-Mail-Adresse des Benutzers von der aus ein Administrator auf die Website zur Dokumentennachverfolgung zugreift. |'joe@contoso.com'|


#### <a name="exceptions-for-the-user-id-field"></a>Ausnahmen für das Feld „user-id“
Obgleich das Feld „user-id“ normalerweise den Benutzer angibt, von dem die Anforderung stammt, gibt es zwei Ausnahmen, bei denen der Wert keinem echten Benutzer entspricht:

-   Der Wert **'microsoftrmsonline@&lt;IhreMandantenID&gt;.rms.&lt;Region&gt;.aadrm.com'**.

    Dies zeigt an, dass die Anforderung von einem Office 365-Dienst wie Exchange Online oder SharePoint Online stammt. In der Zeichenfolge steht *&lt;IhreMandantenID&gt;* für die GUID Ihres Mandanten und *&lt;Region&gt;* für die Region, in der Ihr Mandant registriert ist. Beispielsweise steht **Na** für Nordamerika, **Eu** für Europa und **ap** für Asien.

-   Wenn Sie den RMS-Verbindungsdienst verwenden.

    Anforderungen von diesem Connector werden mit dem Dienstprinzipalnamen von **Aadrm_S-1-7-0** protokolliert, der automatisch generiert wird, wenn Sie den RMS-Connector installieren.

#### <a name="typical-request-types"></a>Typische Anforderungstypen
Es gibt zahlreiche Anforderungstypen für den Azure Rights Management-Dienst. In der folgenden Tabelle sind einige der am häufigsten verwendeten Anforderungstypen benannt und beschrieben.

|Anforderungstyp|Beschreibung|
|----------------|---------------|
|AcquireLicense|Ein Client fordert von einem Windows-basierten Computer aus eine Lizenz für RMS-geschützten Inhalt an.|
|AcquirePreLicense|Ein Client fordert im Auftrag des Benutzers eine Lizenz für RMS-geschützten Inhalt an.|
|AcquireTemplates|Ein Aufruf wird ausgelöst, um Vorlagen anhand von Vorlagen-IDs abzurufen.|
|AcquireTemplateInformation|Ein Aufruf wird ausgelöst, um die IDs der Vorlage vom Dienst abzurufen.|
|AddTemplate|Vom Azure-Portal wird ein Aufruf zum Hinzufügen einer Vorlage ausgelöst.|
|AllDocsCsv|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf zum Herunterladen der CSV-Datei von der Seite **Alle Dokumente**.|
|BECreateEndUserLicenseV1|Von einem Mobilgerät wird ein Aufruf ausgelöst, um eine Endbenutzerlizenz zu erstellen.|
|BEGetAllTemplatesV1|Von einem Mobilgerät (Back-End) wird ein Aufruf ausgelöst, um alle Vorlagen abzurufen.|
|Certify|Der Client zertifiziert den Inhalt für den Schutz.|
|DeleteTemplateById|Vom Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage nach Vorlagen-ID zu löschen.|
|DocumentEventsCsv|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf zum Herunterladen der CSV-Datei für ein einziges Dokument.|
|ExportTemplateById|Vom Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage anhand einer Vorlagen-ID zu exportieren.|
|FECreateEndUserLicenseV1|Ähnlich wie bei der „AcquireLicense“-Anforderung, aber von mobilen Geräten aus.|
|FECreatePublishingLicenseV1|Identisch mit „Certify“ und „GetClientLicensorCert“ in Kombination, von mobilen Clients aus.|
|FEGetAllTemplates|Von einem Mobilgerät (Front-End) wird ein Aufruf ausgelöst, um die Vorlagen abzurufen.|
|FindServiceLocationsForUser|Ein Aufruf zum Abfragen von URLs wird ausgelöst, die zum Aufrufen von „Certify“ oder von „AcquireLicense“ verwendet werden.|
|GetAllDocs|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf zum Laden der Seite **Alle Dokumente** für einen Benutzer oder zum Durchsuchen aller Dokumente des Mandanten. Verwenden Sie diesen Wert in den Feldern „admin-action“ (Adminaktion) und „acting-as-user“ (Fungiert als Benutzer):<br /><br />- „admin-action“ ist leer: Einem Benutzer wird die Seite **Alle Dokumente** für seine eigenen Dokumente angezeigt.<br /><br />- „admin-action“ ist TRUE und „acting-as-user“ ist leer: Einem Administrator werden alle Dokumente für seinen Mandanten angezeigt.<br /><br />- „admin-action“ ist TRUE und „acting-as-user“ ist nicht leer: Einem Administrator wird die Seite **Alle Dokumente** für einen Benutzer angezeigt.|
|GetAllTemplates|Vom Azure-Portal wird ein Aufruf ausgelöst, um alle Vorlagen abzurufen.|
|GetClientLicensorCert|Der Client fordert von einem Windows-basierten Computer aus ein Veröffentlichungszertifikat an (das später zum Schützen von Inhalt verwendet wird).|
|GetConfiguration|Ein Azure PowerShell-Cmdlet wird aufgerufen, um die Konfiguration des Azure RMS-Mandanten abzurufen.|
|GetConnectorAuthorizations|Von den RMS-Connectors wird ein Aufruf ausgelöst, um deren Konfiguration aus der Cloud abzurufen.|
|GetRecipients|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, für ein einzelnes Dokument zur Listenansicht zu navigieren.|
|GetSingle|Von der Website zur Dokumentnachverfolgung erfolgt ein Aufruf, zur Seite **Einzelnes Dokument** zu navigieren.|
|GetTenantFunctionalState|Das Azure-Portal überprüft, ob der Azure Rights Management-Dienst aktiviert ist.|
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


## <a name="windows-powershell-reference"></a>Windows PowerShell-Referenz
Seit Februar 2016 ist [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) das einzige Windows PowerShell-Cmdlet, das Sie für die Azure Rights Management-Verwendungsprotokollierung benötigen. 

Vor dieser Änderung wurden die folgenden Cmdlets, die nun veraltet sind, für die Azure Rights Management-Verwendungsprotokolle benötigt:  

-   [Disable-AadrmUsageLogFeature](/powershell/module/aadrm/disable-aadrmusagelogfeature)

-   [Enable-AadrmUsageLogFeature](/powershell/module/aadrm/enable-aadrmusagelogfeature)

-   [Get-AadrmUsageLog](/powershell/module/aadrm/get-aadrmusagelog)

-   [Get-AadrmUsageLogFeature](/powershell/module/aadrm/get-aadrmusagelogfeature)

-   [Get-AadrmUsageLogLastCounterValue](/powershell/module/aadrm/get-aadrmusageloglastcountervalue)

-   [Get-AadrmUsageLogStorageAccount](/powershell/module/aadrm/get-aadrmusagelogstorageaccount)

-   [Set-AadrmUsageLogStorageAccount](/powershell/module/aadrm/set-aadrmusagelogstorageaccount)

Wenn Sie Protokolle in Ihrem eigenen Azure-Speicher gespeichert haben, die vor der Azure Rights Management-Protokollierungsänderung erstellt wurden, können Sie diese Protokolle wie bisher mit den alten Cmdlets Get-AadrmUsageLog und Get-AadrmUsageLogLastCounterValue herunterladen. Alle neuen Verwendungsprotokolle werden dagegen in den neuen Azure RMS-Speicher geschrieben und müssen mit „Get-AadrmUserLog“ heruntergeladen werden.

Weitere Informationen zum Verwenden von Windows PowerShell für den Azure Rights Management-Dienst finden Sie unter [Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell](administer-powershell.md).



