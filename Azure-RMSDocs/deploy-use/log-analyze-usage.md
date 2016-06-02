---
# required metadata

title: Protokollieren und Analysieren der Nutzung von Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/13/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Protokollieren und Analysieren der Nutzung von Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*

In diesem Thema wird erläutert, wie Sie die Verwendungsprotokollierung bei Azure Rights Management (Azure RMS) verwenden können. Der Azure Rights Management-Dienst kann jede Anforderung protokollieren, die für Ihre Organisation durchgeführt wird. Hierzu gehören die Anforderungen von Benutzern, die von Rights Management-Administratoren in Ihrer Organisation ausgeführten Aktionen und die von Microsoft-Mitarbeitern ausgeführten Aktionen, mit denen Ihre Azure Rights Management-Bereitstellung unterstützt wird.

Sie können dann mithilfe der Azure Rights Management-Protokolle die folgenden Geschäftsszenarios unterstützen:

-   **Analyse hinsichtlich geschäftlicher Erkenntnisse**

    Die von Azure Rights Management generierten Protokolle können in ein Repository Ihrer Wahl importiert werden (z. B. eine Datenbank, ein OLAP-System (Online Analytical Processing) oder ein Zuordnen/Reduzieren-System), um die Informationen zu analysieren und Berichte zu erstellen. Beispielsweise könnten Sie identifizieren, wer auf Ihre RMS-geschützten Daten zugreift. Sie können bestimmen, auf welche RMS-geschützten Daten Benutzer zugreifen, von welchen Geräten aus und von wo. Sie können herausfinden, ob Benutzer geschützte Inhalte erfolgreich lesen können. Sie können ferner identifizieren, welche Personen ein wichtiges Dokument gelesen haben, das geschützt ist.

-   **Überwachung auf Missbrauch**

    Azure Rights Management-Protokollierungsinformationen stehen Ihnen praktisch in Echtzeit zur Verfügung, sodass Sie die Verwendung von Rights Management in Ihrem Unternehmen kontinuierlich überwachen können. 99,9 % der Protokolle sind innerhalb von 15 Minuten nach einer RMS-ausgelösten Aktion verfügbar.

    Beispielsweise können Sie sich benachrichtigen lassen, wenn ein plötzlicher Anstieg der Personen zu verzeichnen ist, die RMS-geschützte Daten außerhalb der Standardarbeitszeiten lesen, was darauf hindeuten kann, dass ein bösartiger Benutzer Informationen sammelt, um sie an die Konkurrenz zu verkaufen. Oder wenn derselbe Benutzer innerhalb eines kurzen Zeitraums offensichtlich von zwei verschiedenen IP-Adressen aus auf Daten zugreift, was darauf hindeuten kann, dass ein Benutzerkonto kompromittiert wurde.

-   **Durchführen forensischer Analysen**

    Wenn Sie ein Informationsleck haben, werden Sie wahrscheinlich gefragt, wer in der jüngsten Zeit auf bestimmte Dokumente zugegriffen hat, und auf welche Informationen eine verdächtigte Person zuletzt zugegriffen hat. Sie können diese Arten von Fragen beantworten, wenn Sie Azure Rights Management mit Protokollierung verwenden. Personen, die geschützte Inhalte verwenden, müssen nämlich immer eine Rights Management-Lizenz abrufen, um Dokumente und Bilder zu öffnen, die mit Azure Rights Management geschützt sind. Das gilt auch dann, wenn diese Dateien per E-Mail verschoben oder auf USB-Laufwerke oder andere Speichergeräte kopiert werden. Dies bedeutet, dass Sie Azure Rights Management-Protokolle als maßgebliche Quelle für Informationen zur forensischen Analyse verwenden können, wenn Sie Ihre Daten mithilfe von Azure Rights Management schützen.

> [!NOTE] Wenn Sie nur an der Protokollierung von administrativen Aufgaben für Azure Rights Management interessiert sind und nicht nachverfolgen möchten, wie die Benutzer Rights Management verwenden, können Sie das Cmdlet [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) von Windows PowerShell für Azure Rights Management nutzen.
> 
> Sie können auch das klassische Azure-Portal für allgemeine Verwendungsberichte verwenden. Hierzu gehören **Übersicht zu RMS**, **Aktive RMS-Benutzer**, **RMS-Geräteplattformen** und **RMS-Anwendungsnutzung**. Klicken Sie für den Zugriff auf diese Berichte im klassischen Azure-Portal auf **Active Directory**, wählen und öffnen Sie ein Verzeichnis, und klicken Sie dann auf **BERICHTE**.

In den folgenden Abschnitten finden Sie Informationen zur Verwendungsprotokollierung von Azure Rights Management.

## Aktivieren der Verwendungsprotokollierung von Azure Rights Management
Seit Februar 2016 ist die Azure Rights Management-Verwendungsprotokollierung standardmäßig für alle Kunden aktiviert. Dies gilt für Kunden, die ihren Azure RMS-Dienst vor Februar 2016 aktiviert haben, und für Kunden, die den Dienst nach Februar 2016 aktiviert haben. 

> [!NOTE] Es fallen keine zusätzlichen Kosten für den Protokollspeicher oder die Protokollierungsfunktionalität an.
> 
> Haben Sie Verwendungsprotokollierung für Azure RMS vor Februar 2016 verwendet, haben Sie ein Abonnement für Azure und ausreichend Speicherplatz auf Azure benötigt, was nun nicht mehr der Fall ist.



## Zugreifen auf und Verwenden von Azure Rights Management-Verwendungsprotokollen
Azure Rights Management schreibt Protokolle als eine Serie von BLOBs in Ihr Azure-Speicherkonto. Jedes BLOB enthält mindestens einen Protokolldatensatz im erweiterten W3C-Protokollformat. Die BLOB-Namen sind Zahlen in der Reihenfolge ihrer Erstellung. Im Abschnitt [Interpretieren von Azure Rights Management-Verwendungsprotokollen](#how-to-interpret-your-azure-rights-management-usage-logs) weiter unten in diesem Dokument finden Sie weitere Informationen zu den Protokollinhalten und deren Erstellung.

Es kann einen Moment dauern, bis nach einer Azure Rights Management-Aktion Protokolle in Ihrem Speicherkonto angezeigt werden. Die meisten Protokolle werden innerhalb von 15 Minuten angezeigt. Es empfiehlt sich, dass Sie die Protokolle in den lokalen Speicher herunterladen, z. B. einen lokalen Ordner, eine Datenbank oder ein Zuordnen/Reduzieren-Repository.

Um die Verwendungsprotokolle herunterzuladen, verwenden Sie das Azure RMS-Administrationsmodul für Windows PowerShell. Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md). Wenn Sie dieses Windows PowerShell-Modul zuvor heruntergeladen haben, führen Sie den folgenden Befehl aus, um zu überprüfen, ob Ihre Version mindestens **2.4.0.0** ist: `(Get-Module aadrm -ListAvailable).Version` 

### So laden Sie Ihre Verwendungsprotokolle mit PowerShell herunter

1.  Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen**, und stellen Sie mit dem Cmdlet [Connect-AadrmService](https://msdn.microsoft.com/library/azure/dn629415.aspx) eine Verbindung mit dem Azure Rights Management-Dienst her:

    ```
    Connect-AadrmService
    ```
    
2.  Führen Sie den folgenden Befehl aus, um die Protokolle für ein bestimmtes Datum herunterzuladen: 

    ```
    Get-AadrmUserLog -Path <location> -fordate <date>
    ```

    Angenommen, Sie haben einen Ordner namens „Protokolle“ auf Laufwerk E: erstellt:
    
    * Um Protokolle für ein bestimmtes Datum (z. B. 01.02.2016) herunterzuladen, führen Sie den folgenden Befehl aus: `Get-AadrmUserLog -Path E:\Logs -fordate 2/1/2016`
    
    * Um Protokolle für einen Datumsbereich (z. B. 01.02.2016 bis 14.02.2016) herunterzuladen, führen Sie den folgenden Befehl aus: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016` 

Wenn Sie, wie in diesen Beispielen, nur den Tag angeben, wird 00:00:00 als Uhrzeit in Ihrer lokalen Uhrzeit angenommen und dann in UTC umgewandelt. Wenn Sie eine Uhrzeit für den -fromdate- oder -todate-Parameter angeben (z.B. -fordate "01.02.2016 15:00:00"), werden das Datum und die Uhrzeit in UTC umgewandelt. Der Get-AadrmUserLog-Befehl ruft dann die Protokolle für diese UTC-Zeitspanne ab.

Die kleinste Zeitspanne, die Sie für ein Herunterladen angeben können, ist ein ganzer Tag.

Standardmäßig werden für dieses Cmdlet drei Threads verwendet, um die Protokolle herunterzuladen. Ist genügend Netzwerkbandbreite verfügbar und möchten Sie die Zeit verkürzen, die zum Herunterladen der Protokolle erforderlich ist, verwenden Sie den -NumberOfThreads-Parameter, der jeden Wert von 1 bis 32 unterstützt. Wenn Sie beispielsweise den folgenden Befehl ausführen, erzeugt das Cmdlet 10 Threads, um die Protokolle herunterzuladen: `Get-AadrmUserLog -Path E:\Logs -fromdate 2/1/2016 –todate 2/14/2016 -numberofthreads 10`


> [!TIP]
> Sie können mit dem [Protokollparser von Microsoft](https://www.microsoft.com/download/details.aspx?id=24659) alle heruntergeladenen Protokolldateien in einem CSV-Format aggregieren. Dies ist ein Tool zum Konvertieren zwischen verschiedenen bekannten Protokollformaten. Sie können mit diesem Tool auch Daten in das SYSLOG-Format konvertieren oder in eine Datenbank importieren. Nachdem Sie das Tool installiert haben, führen Sie `LogParser.exe /?` aus, um Hilfe und Informationen zu diesem Tool anzuzeigen. 
>
> Beispielsweise können Sie folgenden Befehl ausführen, um alle Informationen in eine Datei im LOG-Format zu importieren: `logparser –i:w3c –o:csv "SELECT * INTO AllLogs.csv FROM *.log"`

#### Wenn Sie Azure RMS-Verwendungsprotokollierung vor der Protokollierungsänderung (22. Februar 2016) manuell aktiviert haben


Wenn Sie Verwendungsprotokollierung vor der Protokollierungsänderung verwendet haben, haben Sie Verwendungsprotokolle in Ihrem konfigurierten Azure-Speicherkonto. Microsoft kopiert diese Protokolle nicht als Teil dieser Protokollierungsänderung aus Ihrem Speicherkonto in das neue verwaltete Azure RMS-Speicherkonto. Sie sind dafür zuständig, den Lebenszyklus der zuvor generierten Protokolle zu verwalten, und Sie können das [Get-AadrmUsageLog](https://msdn.microsoft.com/library/dn629401.aspx)-Cmdlet verwenden, um Ihre alten Protokolle herunterzuladen. Beispiel:

- So laden Sie alle verfügbaren Protokolle in Ihren Ordner „E:\logs“ herunter `Get-AadrmUsageLog -Path "E:\Logs"`
    
- So laden Sie einen bestimmten Bereich von BLOBs herunter `Get-AadrmUsageLog –Path "E:\Logs" –FromCounter 1024 –ToCounter 2047`

Sie müssen keine Protokolle mit dem Get-AadrmUsageLog-Cmdlet herunterladen, wenn einer der folgenden Punkte zutrifft:

-  Sie haben Azure Rights Management vor dem 22. Februar 2016 aktiviert, haben die Verwendungsprotokollierung aber nicht aktiviert.

- Sie haben Azure Rights Management nach dem 22. Februar 2016 aktiviert.

## Interpretieren von Azure Rights Management-Verwendungsprotokollen
Verwenden Sie folgende Informationen als Hilfestellung bei der Interpretation der Azure Rights Management-Verwendungsprotokolle.

### Die Abfolge von Protokollen
Azure Rights Management schreibt die Protokolle als eine Serie von BLOBs. 

Jeder Eintrag im Protokoll hat einen UTC-Zeitstempel. Da Azure Rights Management auf mehreren Servern in mehreren Datencentern ausgeführt wird, scheinen die Protokolle manchmal nicht in der richtigen Reihenfolge zu sein, auch wenn sie nach Zeitstempel sortiert sind. Die Abweichung ist jedoch in der Regel gering und liegt im Bereich von einer Minute. In den meisten Fällen ist dies kein Problem, das sich nachteilig bei der Protokollanalyse manifestieren würde.

### Das BLOB-Format
Jedes BLOB ist im erweiterten W3C-Protokollformat. Es beginnt mit den folgenden zwei Zeilen:

**#Software: RMS**

**#Version: 1.1**

Die erste Zeile gibt an, dass es sich um Azure Rights Management-Protokolle handelt. Die zweite Zeile gibt an, dass der Rest des BLOBs die Spezifikation der Version 1.1 einhält. Wir empfehlen, dass alle Anwendungen, die diese Protokolle analysieren, diese beiden Zeilen überprüfen, bevor sie die Analyse des Rests des BLOBs fortsetzen.

In der dritten Zeile wird eine Liste von Feldnamen aufgezählt, die durch Tabstopps voneinander getrennt sind:

**#Fields: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip**

Jede der folgenden Zeilen stellt einen Protokolldatensatz dar. Die Werte der Felder sind in derselben Reihenfolge wie die vorangehende Zeile, auch durch Tabstopps getrennt. Verwenden Sie die folgende Tabelle, um die Felder zu interpretieren.

|Feldname|W3C-Datentyp|Beschreibung|Beispielwert|
|--------------|-----------------|---------------|-----------------|
|date|Datum|Das UTC-Datum, an dem die Anforderung verarbeitet wurde.<br /><br />Die Quelle ist die lokale Uhr auf dem Server, von dem die Anforderung bearbeitet wurde.|2013-06-25|
|time|Zeit|Die UTC-Zeit im 24-Stunden-Format, zu der die Anforderung verarbeitet wurde.<br /><br />Die Quelle ist die lokale Uhr auf dem Server, von dem die Anforderung bearbeitet wurde.|21:59:28|
|row-id|Text|Eindeutige GUID für diesen Protokolldatensatz.<br /><br />Dieser Wert ist hilfreich, wenn Sie Protokolle aggregieren oder in ein anderes Format kopieren.|1c3fe7a9-d9e0-4654-97b7-14fafa72ea63|
|request-type|Name|Der Name der angeforderten RMS-API.|AcquireLicense|
|user-id|String|Der Benutzer, der die Anforderung gesendet hat.<br /><br />Der Wert steht in einfachen Anführungszeichen. Manche Anforderungstypen sind anonym, wobei der Wert dann "" ist.|'joe@contoso.com'|
|result|String|„Success“, wenn die Anforderung erfolgreich verarbeitet wurde.<br /><br />Der Fehlertyp in einfachen Anführungszeichen zeigt an, wenn die Anforderung fehlgeschlagen ist.|'Success'|
|correlation-id|Text|Eine GUID, die das RMS-Clientprotokoll und das Serverprotokoll für eine bestimmte Anforderung gemeinsam haben.<br /><br />Dieser Wert kann bei der Behandlung von Clientproblemen hilfreich sein.|cab52088-8925-4371-be34-4b71a3112356|
|content-id|Text|Eine GUID in geschweiften Klammern, die den geschützten Inhalt identifiziert (z. B. ein Dokument).<br /><br />Dieses Feld hat nur dann einen Wert, wenn „request-type“ den Wert „AcquireLicense“ hat, und ist bei allen anderen Anforderungstypen leer.|{bb4af47b-cfed-4719-831d-71b98191a4f2}|
|owner-email|String|Die E-Mail-Adresse des Besitzers des Dokuments.|alice@contoso.com|
|issuer|String|Die E-Mail-Adresse des Ausstellers des Dokuments.|alice@contoso.com (oder) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com|
|Template-id|String|ID der Vorlage, die zum Schützen des Dokuments verwendet wurde.|{6d9371a6-4e2d-4e97-9a38-202233fed26e}|
|File-name|String|Der Dateiname des geschützten Dokuments. <br /><br />Derzeit werden einige Dateien (z.B. Office-Dokumente) als GUIDs und nicht beim tatsächlichen Dateinamen angezeigt.|TopSecretDocument.docx|
|Date-published|Datum|Das Datum, an dem das Dokument geschützt wurde.|2015-10-15T21:37:00|
|c-info|String|Informationen zur Clientplattform, von der die Anforderung gesendet wird.<br /><br />Die spezifische Zeichenfolge variiert in Abhängigkeit von der Anwendung (z. B. Betriebssystem oder Browser).|'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'|
|c-ip|Adresse|Die IP-Adresse des Clients, von dem die Anforderung stammt.|64.51.202.144|

#### Ausnahmen für das Feld „user-id“
Obgleich das Feld „user-id“ normalerweise den Benutzer angibt, von dem die Anforderung stammt, gibt es zwei Ausnahmen, bei denen der Wert keinem echten Benutzer entspricht:

-   Der Wert **'microsoftrmsonline@&lt;IhreMandantenID&gt;.rms.&lt;Region&gt;.aadrm.com'**.

    Dies zeigt an, dass die Anforderung von einem Office 365-Dienst wie Exchange Online oder SharePoint Online stammt. In der Zeichenfolge steht *&lt;IhreMandantenID&gt;* für die GUID Ihres Mandanten und *&lt;Region&gt;* für die Region, in der Ihr Mandant registriert ist. Beispielsweise steht **Na** für Nordamerika, **Eu** für Europa und **ap** für Asien.

-   Wenn Sie den RMS-Verbindungsdienst verwenden.

    Anforderungen von diesem Connector werden mit dem Dienstprinzipalnamen protokolliert, der von RMS automatisch generiert wird, wenn Sie den RMS-Connector installieren.

#### Typische Anforderungstypen
Es gibt zahlreiche Anforderungstypen in Azure Rights Management. Die folgende Tabelle benennt und beschreibt einige der am häufigsten verwendeten Anforderungstypen.

|Anforderungstyp|Beschreibung|
|----------------|---------------|
|AcquireLicense|Ein Client fordert von einem Windows-basierten Computer aus eine Lizenz für RMS-geschützten Inhalt an.|
|AcquirePreLicense|Ein Client fordert im Auftrag des Benutzers eine Lizenz für RMS-geschützten Inhalt an.|
|AcquireTemplates|Ein Aufruf wird ausgelöst, um Vorlagen anhand von Vorlagen-IDs abzurufen.|
|AcquireTemplateInformation|Ein Aufruf wird ausgelöst, um die IDs der Vorlage vom Dienst abzurufen.|
|AddTemplate|Vom klassischen Azure-Portal wird ein Aufruf zum Hinzufügen einer Vorlage ausgelöst.|
|BECreateEndUserLicenseV1|Von einem Mobilgerät wird ein Aufruf ausgelöst, um eine Endbenutzerlizenz zu erstellen.|
|BEGetAllTemplatesV1|Von einem Mobilgerät (Back-End) wird ein Aufruf ausgelöst, um alle Vorlagen abzurufen.|
|Certify|Der Client zertifiziert den Inhalt für den Schutz.|
|Decrypt|Der Client versucht, den RMS-geschützten Inhalt zu entschlüsseln.|
|DeleteTemplateById|Vom klassischen Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage nach Vorlagen-ID zu löschen.|
|ExportTemplateById|Vom klassischen Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage anhand einer Vorlagen-ID zu exportieren.|
|FECreateEndUserLicenseV1|Ähnlich wie bei der „AcquireLicense“-Anforderung, aber von mobilen Geräten aus.|
|FECreatePublishingLicenseV1|Identisch mit „Certify“ und „GetClientLicensorCert“ in Kombination, von mobilen Clients aus.|
|FEGetAllTemplates|Von einem Mobilgerät (Front-End) wird ein Aufruf ausgelöst, um die Vorlagen abzurufen.|
|GetAllTemplates|Vom klassischen Azure-Portal wird ein Aufruf ausgelöst, um alle Vorlagen abzurufen.|
|GetClientLicensorCert|Der Client fordert von einem Windows-basierten Computer aus ein Veröffentlichungszertifikat an (das später zum Schützen von Inhalt verwendet wird).|
|GetConfiguration|Ein Azure PowerShell-Cmdlet wird aufgerufen, um die Konfiguration des Azure RMS-Mandanten abzurufen.|
|GetConnectorAuthorizations|Von den RMS-Connectors wird ein Aufruf ausgelöst, um deren Konfiguration aus der Cloud abzurufen.|
|GetTenantFunctionalState|Das klassische Azure-Portal überprüft, ob Azure RMS aktiviert ist.|
|GetTemplateById|Vom klassischen Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage mit einer angegebenen Vorlagen-ID abzurufen.|
|ExportTemplateById|Vom klassischen Azure-Portal wird ein Aufruf ausgelöst, um eine Vorlage mit einer angegebenen Vorlagen-ID zu exportieren.|
|FindServiceLocationsForUser|Ein Aufruf zum Abfragen von URLs wird ausgelöst, die zum Aufrufen von „Certify“ oder von „AcquireLicense“ verwendet werden.|
|ImportTemplate|Vom klassischen Azure-Portal wird ein Aufruf zum Importieren einer Vorlage ausgelöst.|
|ServerCertify|Von einem RMS-fähigen Client (z. B. SharePoint) wird ein Aufruf zum Zertifizieren des Servers ausgelöst.|
|SetUsageLogFeatureState|Ein Aufruf zum Aktivieren der Verwendungsprotokollierung wird ausgelöst.|
|SetUsageLogStorageAccount|Ein Aufruf wird ausgelöst, um den Speicherort der Azure RMS-Protokolle anzugeben.|
|SignDigest|Ein Aufruf wird ausgelöst, wenn ein Schlüssel für Signaturzwecke verwendet wird. Dieser Aufruf erfolgt normalerweise einmal pro „AcquireLicence“ (oder „FECreateEndUserLicenseV1“), „Certify“ und „GetClientLicensorCert“ (oder „FECreatePublishingLicenseV1“).|
|UpdateTemplate|Vom klassischen Azure-Portal wird ein Aufruf zum Aktualisieren einer vorhandenen Vorlage ausgelöst.|

## Windows PowerShell-Referenz
Seit Februar 2016 ist [Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx) das einzige Windows PowerShell-Cmdlet, das Sie für die Azure RMS-Verwendungsprotokollierung benötigen. 

Vor dieser Änderung wurden die folgenden Cmdlets, die nun veraltet sind, für die Azure RMS-Verwendungsprotokolle benötigt:  

-   [Disable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629404.aspx)

-   [ENable-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629421.aspx)

-   [Get-AadrmUsageLog](https://msdn.microsoft.com/library/azure/dn629401.aspx)

-   [Get-AadrmUsageLogFeature](https://msdn.microsoft.com/library/azure/dn629425.aspx)

-   [Get-AadrmUsageLogLastCounterValue](https://msdn.microsoft.com/library/azure/dn629423.aspx)

-   [Get-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629419.aspx)

-   [Set-AadrmUsageLogStorageAccount](https://msdn.microsoft.com/library/azure/dn629426.aspx)

Wenn Sie Protokolle in Ihrem eigenen Azure-Speicher haben, die vor der Azure RMS-Protokollierungsänderung erstellt wurden, können Sie diese Protokolle wie bisher mit den alten Cmdlets „Get-AadrmUsageLog“ und „Get-AadrmUsageLogLastCounterValue“ herunterladen. Alle neuen Verwendungsprotokolle werden dagegen in den neuen Azure RMS-Speicher geschrieben und müssen mit „Get-AadrmUserLog“ heruntergeladen werden.

Weitere Informationen zum Verwenden von Windows PowerShell für Azure Rights Management finden Sie unter [Verwaltung von Azure Rights Management mithilfe von Windows PowerShell](administer-powershell.md).





<!--HONumber=May16_HO3-->


