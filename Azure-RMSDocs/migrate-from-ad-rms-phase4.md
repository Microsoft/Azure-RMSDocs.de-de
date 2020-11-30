---
title: Migrieren von AD RMS-Azure Information Protection – Phase 4
description: Phase 4 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 8 bis 9 der Migration von AD RMS zu Azure Information Protection ab.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/26/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.subservice: migration
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e7431ebdf016b89e1750b833dc4fca2d9646b195
ms.sourcegitcommit: d31cb53de64bafa2097e682550645cadc612ec3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96316720"
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Migrationsphase 4: Unterstützung der Dienstekonfiguration

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Verwenden Sie die folgenden Informationen für Phase 4 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 8 bis 9 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.

## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Schritt 8: Konfigurieren der IRM-Integration mit Exchange Online

> [!IMPORTANT]
> Sie können nicht steuern, welche Empfänger migrierte Benutzer möglicherweise für geschützte e-Mails ausgewählt werden.
>
> Stellen Sie daher sicher, dass alle Benutzer und e-Mail-aktivierten Gruppen in Ihrer Organisation über ein Konto in Azure AD verfügen, das mit Azure Information Protection verwendet werden kann.
>
> Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

Führen Sie unabhängig von der gewählten Azure Information Protection Mandanten Schlüssel Topologie die folgenden Schritte aus:

1. **Voraussetzung**: damit Exchange Online e-Mails entschlüsseln kann, die durch AD RMS geschützt sind, müssen Sie wissen, dass die AD RMS-URL für Ihren Cluster dem in Ihrem Mandanten verfügbaren Schlüssel entspricht. 

    Dieser Abgleich geschieht mithilfe des DNS-SRV-Datensatzes für Ihren AD RMS-Cluster, der auch verwendet wird, um Office-Clients für die Verwendung von Azure Information Protection neu zu konfigurieren. 

    Wenn Sie den DNS-SRV-Datensatz für die Neukonfiguration des Clients in [Schritt 7](migrate-from-ad-rms-phase3.md#step-7-reconfigure-windows-computers-to-use-azure-information-protection)nicht erstellt haben, erstellen Sie diesen Datensatz jetzt, um Exchange Online zu unterstützen. [Anweisungen](migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection)
    
    Wenn dieser DNS-Eintrag vorhanden ist, können Benutzer, die Outlook im Web und mobile E-Mail-Clients verwenden, AD RMS-geschützte E-Mails in diesen Apps anzeigen. Zudem kann Exchange den von AD RMS importierten Schlüssel zum Entschlüsseln, Indizieren, Erfassen und Schützen von Inhalten verwenden, die durch AD RMS geschützt wurden.  

1. **Führen Sie den Exchange Online-Befehl [Get-IRMConfiguration](/powershell/module/exchange/get-irmconfiguration) aus.** 

    Wenn Sie beim Ausführen dieses Befehls Hilfe benötigen, sehen Sie sich die ausführlichen Anweisungen unter [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration) an.
    
    Überprüfen Sie mithilfe der Ausgabe, ob **AzureRMSLicensingEnabled** auf **TRUE** festlegt ist:
    
    - Wenn **azurermslicensingenabled** auf **true** festgelegt ist, ist für diesen Schritt keine weitere Konfiguration erforderlich. 
    
    - Wenn **azurermslicensingenabled** auf **false** festgelegt ist, führen Sie aus, `Set-IRMConfiguration -AzureRMSLicensingEnabled $true` und vergewissern Sie sich, dass Exchange Online jetzt für die Verwendung des Azure-Rights Management Dienstanbieter bereit ist 
    
        Weitere Informationen finden Sie in den Überprüfungs Schritten unter [Einrichten neuer Microsoft 365 Nachrichten Verschlüsselungsfunktionen, die auf Azure Information Protection basieren](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e).

## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Schritt 9 Konfigurieren der IRM-Integration für Exchange Server und SharePoint Server

Wenn Sie die Information Rights Management (unm)-Funktionalität von Exchange Server oder SharePoint Server mit AD RMS verwendet haben, müssen Sie den Rights Management-Connector (RMS) bereitstellen.

Der Connector fungiert als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und dem Schutzdienst für Azure Information Protection.

Dieser Schritt behandelt die Installation und Konfiguration des Connectors, die Deaktivierung von IRM für Exchange und SharePoint und die Konfiguration dieser Server für die Verwendung des Connectors. 

Wenn Sie zum Schluss AD RMS. XML-Daten Konfigurationsdateien importiert haben, die zum Schützen von e-Mail-Nachrichten Azure Information Protection in verwendet wurden, müssen Sie die Registrierung auf den Exchange Server-Computern manuell bearbeiten, um alle URLs der vertrauenswürdigen Veröffentlichungs Domäne an den RMS-Verbindungs Dienst umzuleiten.

> [!NOTE]
> Überprüfen Sie vor Beginn unter [Lokale Server, die Azure RMS unterstützen](requirements.md#supported-on-premises-servers-for-azure-rights-management-data-protection) die Versionen der lokalen Server, die der Azure Rights Management-Dienst unterstützt.

### <a name="install-and-configure-the-rms-connector"></a>Installieren und Konfigurieren des RMS-Verbindungsdiensts

Befolgen Sie die Anweisungen im Artikel bereitstellen [des Azure-Rights Management-Verbindungs-Connector](./deploy-rms-connector.md) , und führen Sie die Schritte 1 bis 4 aus. 

Beginnen Sie noch nicht mit Schritt 5 der Connectoranweisungen.

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Deaktivieren von IRM auf Exchange Servern und Entfernen der AD RMS-Konfiguration

> [!IMPORTANT]
> Wenn Sie für einen Ihrer Exchange-Server noch nicht "IRiM" konfiguriert haben, führen Sie nur die Schritte 2 und 6 aus.
> 
> Führen Sie diese Schritte aus, wenn alle Lizenzierungs-URLs für alle Ihre AD RMS Cluster nicht im *licensingloation* -Parameter angezeigt werden, wenn Sie [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration)ausführen.

1. Suchen Sie auf jedem Exchange-Server den folgenden Ordner, und löschen Sie alle Einträge in diesem Ordner: **\programdata\microsoft\drm\server\s-1-5-18**

2. Führen Sie von einem der Exchange-Server die folgenden PowerShell-Befehle aus, um sicherzustellen, dass Benutzer E-Mails lesen können, die durch Azure Rights Management geschützt sind.

    Bevor Sie diese Befehle ausführen, ersetzen Sie die URL Ihres eigenen Azure-Rights Management Dienstanbieter *\<Your Tenant URL>* .

    ```PowerShell
    $irmConfig = Get-IRMConfiguration
    $list = $irmConfig.LicensingLocation 
    $list += "<Your Tenant URL>/_wmcs/licensing"
    Set-IRMConfiguration -LicensingLocation $list
    ```

    Wenn Sie " [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration)" ausführen, sehen Sie nun alle Ihre URL für die AD RMS-Cluster Lizenzierung und die URL Ihres Azure Rights Management-Dienstanbieter für den Parameter " *licensingloation* ".

3.  Deaktivieren Sie nun die IRM-Funktionen für Nachrichten, die an interne Empfänger gesendet werden:

    ```PowerShell
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

4. Verwenden Sie als anschließend das gleiche Cmdlet, um IRM in Microsoft Office Outlook Web App und Microsoft Exchange ActiveSync zu deaktivieren:

    ```PowerShell
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Verwenden Sie schließlich das gleiche Cmdlet, um alle zwischengespeicherten Zertifikate zu löschen:

    ```PowerShell
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Setzen Sie nun IIS auf jedem Exchange Server zurück, z. B. indem Sie eine Eingabeaufforderung als Administrator ausführen und **iisreset** eingeben.

### <a name="disable-irm-on-sharepoint-servers-and-remove-ad-rms-configuration"></a>Deaktivieren von IRM auf SharePoint Servern und Entfernen der AD RMS-Konfiguration

1.  Stellen Sie sicher, dass keine Dokumente aus RMS-geschützten Bibliotheken ausgecheckt sind. Wenn dies der Fall ist, kann am Ende dieses Verfahrens nicht mehr darauf zugegriffen werden.

2.  Klicken Sie auf der Website der Microsoft SharePoint-Zentraladministration im Abschnitt **Schnellstart** auf **Sicherheit**.

3.  Klicken Sie auf der Seite **Sicherheit** im Abschnitt **Informationsrichtlinie** auf **Verwaltung von Informationsrechten konfigurieren**.

4.  Wählen Sie auf der Seite **Information Rights Management** im Abschnitt **Information Rights Management****Verwenden Sie IRM nicht auf diesem Server**, und klicken Sie dann auf **OK**.

5.  Löschen Sie auf jedem der SharePoint Server-Computer den Inhalt des Ordners \programdata\microsoft\msipc\server \\ < *SID des Kontos, auf dem SharePoint Server>ausgeführt* wird.

### <a name="configure-exchange-and-sharepoint-to-use-the-connector"></a>Konfigurieren von Exchange und SharePoint zur Verwendung des Connectors

1. Wechseln Sie zurück zu den Anweisungen für die Bereitstellung des RMS-Connectors: [Schritt 5: Konfigurieren von Servern für die Verwendung des RMS-Connectors](./configure-servers-rms-connector.md).

    Wenn Sie nur über SharePoint Server verfügen, gehen Sie direkt zu [Nächste Schritte](#next-steps), um die Migration fortzusetzen. 

2. Fügen Sie auf jedem Exchange Server die Registrierungsschlüssel im nächsten Abschnitt manuell für jede Konfigurationsdatendatei (XML) hinzu, um die URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten. Diese Registrierungseinträge sind migrationsspezifisch und werden nicht vom Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst hinzugefügt.

    Gehen Sie beim Vornehmen dieser Änderungen an der Registrierung wie folgt vor:

    -   Ersetzen Sie *Connector FQDN* durch den Namen, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

    -   Verwenden Sie das HTTP- oder HTTPS-Präfix für die Verbindungsdienst-URL, je nachdem, ob Sie HTTP oder HTTPS für die Kommunikation zwischen dem Verbindungsdienst und Ihren lokalen Servern konfiguriert haben.

#### <a name="registry-edits-for-exchange"></a>Bearbeitung der Registrierung für Exchange

Fügen Sie für alle Exchange-Server die folgenden Registrierungswerte zu „LicenseServerRedirection“ hinzu, abhängig von Ihren Exchange-Versionen:

1. Fügen Sie für **Exchange 2013 und Exchange 2016** den folgenden Registrierungs Wert hinzu:

    - **Registrierungs Pfad:**`HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection`

    - **Typ:** Reg_SZ

    - **Wert**: `https://\<AD RMS Intranet Licensing URL\>/_wmcs/licensing`

    - **Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

        - `http://\<connector FQDN\>/_wmcs/licensing`
        
        - `https://\<connector FQDN\>/_wmcs/licensing`

1. Fügen Sie für Exchange 2013 den folgenden zusätzlichen Registrierungs Wert hinzu:

    - **Registrierungs Pfad:**`HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection` 

    - **Typ:** Reg_SZ

    - **Wert:** https:// \<AD RMS Extranet Licensing URL\> /_wmcs/licensing

    - **Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

        - `http://\<connector FQDN\>/_wmcs/licensing`

        - `https://\<connector FQDN\>/_wmcs/licensing`

## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Phase 5: Aufgaben nach der Migration](migrate-from-ad-rms-phase5.md) fort, um die Migration fortzusetzen.