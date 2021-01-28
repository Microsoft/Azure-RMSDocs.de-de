---
title: Problembehandlung bei Ihrer lokalen Scanner-Bereitstellung
description: Anleitung für die Problembehandlung bei der Bereitstellung von lokalen bereit Stellungen mit einheitlicher Bezeichnung
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/26/2021
ms.topic: reference
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 46a994c5191e82d68f318e4900e0a5d45c1e176b
ms.sourcegitcommit: 3136ce04e185b93503585466b7ab4b5bb1df6827
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "98958073"
---
# <a name="troubleshooting-your-unified-labeling-on-premises-scanner-deployment"></a>Problembehandlung bei der Bereitstellung der lokalen Bereitstellung mit Unified-Bezeichnung

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). *

Verwenden Sie den Inhalt dieses Artikels, um die Problembehandlung für Ihre lokale Scanner-Bereitstellung zu unterstützen.

## <a name="troubleshooting-using-the-scanner-diagnostic-tool"></a>Problembehandlung mithilfe des Scanner-Diagnosetools

Wenn Sie Probleme mit dem Azure Information Scanner haben, überprüfen Sie mithilfe des PowerShell-Befehls [Start-aipscannerdiagnostics](/powershell/module/azureinformationprotection/start-aipscannerdiagnostics) , ob die Bereitstellung fehlerfrei ist:

```powershell
Start-AIPScannerDiagnostics
```

Das Diagnosetool überprüft die folgenden Details und exportiert dann eine Protokolldatei mit den Ergebnissen:

- Gibt an, ob die Datenbank aktuell ist.
- Ob Netzwerk-URLs zugänglich sind
- Gibt an, ob ein gültiges Authentifizierungs Token vorhanden ist, und die Richtlinie kann abgerufen werden.
- Gibt an, ob das Profil in der Azure-Portal definiert ist.
- Gibt an, ob die Offline-/Online Konfiguration vorhanden und abgerufen werden kann
- Ob die konfigurierten Regeln gültig sind

> [!TIP]
> Wenn Sie den Befehl unter einem Benutzer ausführen, der nicht der Überprüfungs Benutzer ist, stellen Sie sicher, dass Sie den Parameter " **-Ondo** " hinzufügen. 
>

> [!NOTE]
> Der Befehl " **Start-aipscannerdiagnostics** " führt keine vollständige Voraussetzungs Prüfung aus. Wenn bei der Überprüfung Probleme auftreten, stellen Sie auch sicher, dass Ihr System den Überprüfungs [Anforderungen](deploy-aip-scanner-prereqs.md)entspricht und dass die Überprüfungs [Konfiguration und-Installation](deploy-aip-scanner-configure-install.md) fertiggestellt sind.
>

## <a name="troubleshooting-a-scan-that-timed-out"></a>Problembehandlung bei einem Überprüfungs Timeout

Wenn der Scanner unerwartet in der Mitte anhält und die Überprüfung einer großen Anzahl von Dateien in einem Repository nicht durchführt, müssen Sie möglicherweise eine der folgenden Einstellungen ändern:

- **Anzahl der dynamischen Ports**. Möglicherweise müssen Sie die Anzahl der dynamischen Ports für das Betriebssystem erhöhen, das die Dateien gehostet. Ein Grund dafür, warum der Scanner die Anzahl an zulässigen Netzwerkverbindungen überschreitet und daher angehalten wird, ist die Serverhärtung für SharePoint.

    Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).

- **Schwellenwert für Listenansicht**. Für große SharePoint-Farmen müssen Sie möglicherweise den Schwellenwert für die Listenansicht erhöhen. Standardmäßig ist der Schwellenwert für die Listenansicht auf **5.000** festgelegt.

    Weitere Informationen finden Sie unter [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server).


## <a name="scanner-error-reference"></a>Fehler Referenz für Scanner

Verwenden Sie die folgenden Abschnitte, um bestimmte Fehlermeldungen zu verstehen, die von der Überprüfung generiert werden, sowie Problembehandlung oder Lösungs Aktionen, um das Problem zu beheben

|Fehlertyp |Problembehandlung  |
|---------|---------|
|**Authentifizierungsfehler**     |  - [Das Authentifizierungs Token wurde nicht akzeptiert.](#authentication-token-not-accepted) <br>  - [Authentifizierungs Token fehlt.](#authentication-token-missing)|
|**Richtlinienfehler**     |  - [Fehlende Richtlinie](#policy-missing) <br>- [Die Richtlinie enthält keine automatische Bezeichnungs Bedingung.](#policy-doesnt-include-any-automatic-labeling-condition)      |
|**DB/Schema-Fehler**     |  - [Datenbankfehler](#database-errors) <br> - [Nicht übereinstimmendes oder veraltetes Schema](#mismatched-or-outdated-schema)  |
|**Sonstige Fehler**     |  - [Die zugrunde liegende Verbindung wurde geschlossen.](#underlying-connection-was-closed) <br> - [Hält Scanner-Prozesse](#stuck-scanner-processes) <br>- [Es kann keine Verbindung mit dem Remote Server hergestellt werden](#unable-to-connect-to-remote-server) <br>- [Fehler beim Senden der Anforderung.](#error-occurred-while-sending-the-request) <br>- [Fehlender inhaltscanauftrag oder Profil](#missing-content-scan-job-or-profile) <br>- [Keine Depots konfiguriert](#no-repositories-configured) <br>- [Kein Cluster gefunden.](#no-cluster-found)   |
|     |         |


<!--Authentication errors-->

### <a name="authentication-token-not-accepted"></a>Das Authentifizierungs Token wurde nicht akzeptiert.

**Fehlermeldung**

`Microsoft.InformationProtection.Exceptions.AccessDeniedException: The service didn't accept the auth token.`

**Lösung**

Wenn der Befehl " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " fehlgeschlagen ist, stellen Sie sicher, dass Sie die Berechtigungen im Azure-Portal ordnungsgemäß definieren.

Weitere Informationen finden Sie unter [Erstellen und Konfigurieren von Azure AD Anwendungen für "Set-aipauthentication](rms-client/clientv2-admin-guide-powershell.md#create-and-configure-azure-ad-applications-for-set-aipauthentication)".

### <a name="authentication-token-missing"></a>Authentifizierungs Token fehlt.

**Fehlermeldung**

Einer der folgenden:

- `NoAuthTokenException: Client application failed to provide authentication token for HTTP request`

- `Microsoft.InformationProtection.Exceptions.NoAuthTokenException: Client application failed to provide authentication token for HTTP request. Failed with: System.AggregateException: One or more errors occurred. ---> Microsoft.IdentityModel.Clients.ActiveDirectory.AdalException: user_interaction_required: One of two conditions was encountered: 1. The PromptBehavior.Never flag was passed, but the constraint could not be honored, because user interaction was required. 2. An error occurred during a silent web authentication that prevented the http authentication flow from completing in a short enough time frame`

- `Failed to acquire a token using windows integrated authentication (No SSO)`

- Aus der Azure-Portal auf der Seite " **Knoten** ": `Policy does not include any automatic labeling condition`

**Lösung**

Damit der Scanner nicht interaktiv ausgeführt werden kann, müssen Sie sich mit einem Token authentifizieren. 

Wenn Sie den Befehl [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) ausführen, stellen Sie sicher, dass Sie im Namen des Überprüfungs Benutzers den Token-Parameter verwenden.

Beispiel:

```powershell
$pscreds = Get-Credential CONTOSO\scanner
Set-AIPAuthentication -AppId "77c3c1c3-abf9-404e-8b2b-4652836c8c66" -AppSecret "OAkk+rnuYc/u+]ah2kNxVbtrDGbS47L4" -DelegatedUser scanner@contoso.com -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -OnBehalfOf $pscreds
Acquired application access token on behalf of CONTOSO\scanner.
```

Weitere Informationen finden Sie unter [Get a Azure AD Token for the Scanner](deploy-aip-scanner-configure-install.md#get-an-azure-ad-token-for-the-scanner).

<!--Policy errors-->

### <a name="policy-missing"></a>Fehlende Richtlinie

**Fehlermeldung**

`Policy is missing`

**Beschreibung**

Die Überprüfung kann Ihre MIP-Richtlinien Datei (Microsoft Information Protection) nicht finden.

**Lösung**

Um zu überprüfen, ob die Richtlinien Datei erwartungsgemäß vorhanden ist, checken Sie den folgenden Speicherort ein: **% LocalAppData% \Microsoft\MSIP\mip\MSIP.Scanner.exe \mip\mip.Policies.sqlite3**

Weitere Informationen zu MIP-Bezeichnungen und Bezeichnungs Richtlinien finden Sie unter [Erstellen und Konfigurieren von Vertraulichkeits Bezeichnungen und deren Richtlinien](/microsoft-365/compliance/create-sensitivity-labels) in der Microsoft 365-Dokumentation.

### <a name="policy-doesnt-include-any-automatic-labeling-condition"></a>Die Richtlinie enthält keine automatische Bezeichnungs Bedingung.

**Fehler**

Fehler zeigen an, dass in ihrer Bezeichnungs Richtlinie Automatische Beschriftungs Bedingungen fehlen.

**Lösung**

Überprüfen Sie die folgenden Probleme:

|Lösung  |Details  |
|---------|---------|
|**Überprüfen der Einstellungen des Inhalts Scan Auftrags**     | Führen Sie im Azure-Portal folgende Schritte aus: <br> <br>- [Legen Sie die zu **ermittelnden Informationstypen** auf **alle** fest.](deploy-aip-scanner-configure-install.md#identify-all-custom-conditions-and-known-sensitive-information-types)  <br>- [Beim Scannen anzuwendende Standard Bezeichnung definieren](deploy-aip-scanner-configure-install.md#apply-a-default-label-to-all-files-in-a-data-repository)      |
|**Überprüfen der Richtlinien Einstellungen für die Bezeichnung**     |  Führen Sie in Ihrem Bezeichnungs-Admin Center, wie z. b. dem Microsoft 365 Security & Compliance Center, folgende Schritte aus: <br> <br>- [Definieren einer Standard Vertraulichkeits Bezeichnung](/microsoft-365/compliance/create-sensitivity-labels#publish-sensitivity-labels-by-creating-a-label-policy)  <br> - [Definieren von automatischen/empfohlenen Bezeichnungs Regeln](/microsoft-365/compliance/apply-sensitivity-label-automatically)       |
|**Überprüfen Sie, ob die Richtlinie zugänglich ist**     | Wenn Ihre Einstellungen erwartungsgemäß definiert sind, ist die Richtlinien Datei möglicherweise nicht vorhanden oder nicht zugänglich, z. b. Wenn ein Timeout von der Microsoft 365 Security & Compliance Center vorliegt. <br>  <br>Überprüfen Sie zum Überprüfen der Richtlinien Datei, ob die folgende Datei vorhanden ist: **% LocalAppData% \Microsoft\MSIP\mip\MSIP.Scanner.exe \mip\mip.Policies.sqlite3**        |
| | |

Weitere Informationen finden Sie unter [Was ist der Azure Information Protection Unified Label Scanner?](deploy-aip-scanner.md) , und [erfahren Sie mehr über Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels).

<!--DB / Schema errors-->

### <a name="database-errors"></a>Datenbankfehler

**Fehlermeldung**

`DB error`

**Beschreibung**

Der Scanner kann möglicherweise keine Verbindung mit der Datenbank herstellen.

**Lösung**

Überprüfen Sie die Netzwerk Konnektivität zwischen dem Überprüfungs Computer und der Datenbank. 

Stellen Sie außerdem sicher, dass das Dienst Konto, das zum Ausführen von Überprüfungs Prozessen verwendet wird, über alle erforderlichen Berechtigungen für den Zugriff auf die Datenbank verfügt.

### <a name="mismatched-or-outdated-schema"></a>Nicht übereinstimmendes oder veraltetes Schema

**Fehlermeldung**

Einer der folgenden:

- `SchemaMismatchException`

- In der Azure-Portal auf der Seite " **Knoten** ": `DB schema is not up to date. Run Update-AIPScanner command to update the DB schema` oder `Error: DB schema is not up to date`

**Lösung**

Führen Sie den Befehl [Update-aipscanner](/powershell/module/azureinformationprotection/Update-AIPScanner) aus, um das Schema erneut zu synchronisieren, und stellen Sie sicher, dass es mit den aktuellen Änderungen auf dem neuesten Stand ist.


<!--Other errors-->

### <a name="underlying-connection-was-closed"></a>Die zugrunde liegende Verbindung wurde geschlossen

**Fehlermeldung**

`System.Net.WebException: The underlying connection was closed: An unexpected error occurred on a send. ---> System.IO.IOException: Authentication failed because the remote party has closed the transport stream.`

**Lösung**

Dieser Fehler bedeutet in der Regel, dass TLS 1,2 nicht aktiviert ist.

Weitere Informationen finden Sie unter [Firewalls und Netzwerkinfrastruktur](requirements.md#firewalls-and-network-infrastructure). 

Informationen zum Aktivieren von TLS 1,2 finden Sie unter [Aktivieren von TLS 1,2](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client) in der Enterprise Mobility + Security-Dokumentation.

### <a name="stuck-scanner-processes"></a>Hält Scanner-Prozesse

**Fehlermeldung**

Der Scanner verarbeitet eine einzelne Datei länger als erwartet. Der Prozess kann hängen bleiben.

**Lösung**

Überprüfen Sie den ausführlichen Bericht, um festzustellen, ob die Datei noch wächst. 

Wenn die Datei weiter wächst, bedeutet dies, dass der Scanner weiterhin Daten verarbeitet, und Sie müssen warten, bis der Vorgang abgeschlossen ist.

Wenn die Datei jedoch nicht mehr wächst, gehen Sie folgendermaßen vor:

1. Führen Sie einen oder beide der folgenden Schritte aus:

    - Führen Sie das Cmdlet [Start-aipscannerdiagnostics](/powershell/module/azureinformationprotection/start-aipscannerdiagnostics) aus, um Diagnose Überprüfungen für Ihren Scanner auszuführen, und exportieren und zippen Sie Protokolldateien für alle gefundenen Fehler.
    - Führen Sie das [Export-aiplogs-](/powershell/module/azureinformationprotection/export-aiplogs) Cmdlet aus, um Protokolldateien aus dem Verzeichnis " **%LocalAppData%\microsoft\msip\logs** " zu exportieren und zu komprimieren.

1. Erstellen Sie eine Dumpdatei für den MSIP-Überprüfungs Dienst. Klicken Sie im Windows Task-Manager mit der rechten Maustaste auf den **MSIP**-Überprüfungs Dienst, und wählen Sie **Dumpdatei erstellen** aus.

1. Beendet den Scanvorgang in der Azure-Portal. 

1. Starten Sie den Dienst auf dem Überprüfungs Computer neu.

1. Öffnen Sie ein Support Ticket, und fügen Sie die Dumpdateien aus dem Überprüfungsprozess an.

Weitere Informationen finden Sie unter [Problembehandlung für einen Scan, bei dem ein Timeout](#troubleshooting-a-scan-that-timed-out)aufgetreten ist. 

### <a name="unable-to-connect-to-remote-server"></a>Es kann keine Verbindung mit dem Remote Server hergestellt werden

**Fehler**

In der Datei **% *LocalAppData*% \ microsoft\msip\logs\msipscanner.iplog**`Unable to connect to the remote server ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted IP:port`    

> [!NOTE]
> Diese Datei wird gezippt, wenn mehrere Protokolle vorhanden sind.

**Beschreibung**

Der Scanner hat die Anzahl der zulässigen Netzwerkverbindungen überschritten.

**Lösung**

Erhöhen Sie die Anzahl der dynamischen Ports für das Betriebssystem, das die Dateien gehostet.

Weitere Informationen zum Abrufen des aktuellen Portbereichs und zu dessen Vergrößerung finden Sie unter [Settings that can be Modified to Improve Network Performance (Einstellungen, die zur Verbesserung der Netzwerkleistung geändert werden können)](/biztalk/technical-guides/settings-that-can-be-modified-to-improve-network-performance).


Siehe auch: [Problembehandlung bei einem Scan, bei dem ein Timeout](#troubleshooting-a-scan-that-timed-out)aufgetreten ist
### <a name="error-occurred-while-sending-the-request"></a>Fehler beim Senden der Anforderung.

**Fehlermeldung**

`[System.Net.Http.HttpRequestException: An error occurred while sending the request. ---> System.Net.WebException: The underlying connection was closed: An unexpected error occurred on a send. ---> System.IO.IOException: Unable to read data from the transport connection: An existing connection was forcibly closed by the remote host. ---> System.Net.Sockets.SocketException: An existing connection was forcibly closed by the remote host`

**Lösung**

Dieser Fehler bedeutet in der Regel, dass TLS 1,2 nicht aktiviert ist.

Weitere Informationen finden Sie unter [Firewalls und Netzwerkinfrastruktur](requirements.md#firewalls-and-network-infrastructure). 

Informationen zum Aktivieren von TLS 1,2 finden Sie unter [Aktivieren von TLS 1,2](/mem/configmgr/core/plan-design/security/enable-tls-1-2-client) in der Enterprise Mobility + Security-Dokumentation.


### <a name="missing-content-scan-job-or-profile"></a>Fehlender inhaltscanauftrag oder Profil

**Fehler**

Fehler zeigen an, dass Ihr inhaltscanauftrag oder Profil nicht gefunden werden kann.

Beispiel: der folgende Fehler in der Azure-Portal auf der Seite " **Knoten** ": `No content scan job found`

**Lösung**

Überprüfen Sie die Scannerkonfiguration im Azure-Portal.

Weitere Informationen finden Sie unter [Konfigurieren und Installieren des Azure Information Protection Unified Bezeichnung Scanner](deploy-aip-scanner-configure-install.md). 

> [!NOTE]
> Bei einem *Profil* handelt es sich um einen Legacy Scanner-Begriff, der in neueren Versionen des Scanners durch den scannercluster und den Inhalts Scanauftrag ersetzt wurde.
> 
### <a name="no-repositories-configured"></a>Keine Depots konfiguriert

**Fehlermeldung**

In der Azure-Portal auf der Seite **Knoten** : `No repositories are configured`

**Beschreibung**

Möglicherweise verfügen Sie über einen inhaltscanauftrag ohne konfigurierte Depots. 

**Lösung**

Überprüfen Sie die Einstellungen des Inhalts Scan Auftrags, und fügen Sie mindestens ein Repository hinzu. 

Weitere Informationen finden Sie unter [Erstellen eines Inhalts Scan Auftrags](deploy-aip-scanner-configure-install.md#create-a-content-scan-job).

### <a name="no-cluster-found"></a>Kein Cluster gefunden.

**Fehlermeldung**

In der Azure-Portal auf der Seite **Knoten** : `No cluster found`

**Beschreibung**

Es wurde keine tatsächliche Entsprechung für einen der von Ihnen definierten scannercluster gefunden.

**Lösung**

Überprüfen Sie die Cluster Konfiguration, und überprüfen Sie Sie anhand ihrer eigenen Systemdetails für Tippfehler und Fehler.

Weitere Informationen finden Sie unter [Erstellen eines Scanner-Clusters](deploy-aip-scanner-configure-install.md#create-a-scanner-cluster).

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen finden Sie in unserem Blog zu [bewährten Methoden für die Bereitstellung und Verwendung des AIP-UL-Scanners](https://techcommunity.microsoft.com/t5/microsoft-security-and/best-practices-for-deploying-and-using-the-aip-ul-scanner/ba-p/1878168).