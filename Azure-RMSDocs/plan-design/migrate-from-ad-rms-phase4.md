---
title: "Migrieren von AD RMS-Azure Information Protection – Phase 4"
description: Phase 4 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 8 bis 9 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4157148c0109317851ed2f128a5ae74603d82af2
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Migrationsphase 4: Unterstützung der Dienstekonfiguration

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Verwenden Sie die folgenden Informationen für Phase 4 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 8 bis 9 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Schritt 8: Konfigurieren der IRM-Integration mit Exchange Online

Wenn Sie Ihre TDP von AD RMS mit Exchange Online bereits importiert haben, müssen Sie diese TDP entfernen, um Konflikte verursachende Vorlagen und Richtlinien nach der Migration zu Azure Information Protection zu vermeiden. Verwenden Sie hierzu das Exchange Online-Cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx).

Bei Verwendung der Azure Information Protection-Mandantenschlüsseltopologie **von Microsoft verwaltet**:

1. Verwenden Sie die Anweisungen im Abschnitt [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration) im Artikel [Office 365: Konfigurationen für Clients und Onlinedienste](../deploy-use/configure-office365.md). Dieser Abschnitt enthält typische auszuführende Befehle, die eine Verbindung mit dem Exchange Online-Dienst herstellen, den Mandantenschlüssel aus Azure Information Protection importieren und IRM-Funktionen für Exchange Online aktivieren. Nachdem Sie diese Schritte abgeschlossen haben, verfügen Sie über die volle Schutzfunktionalität von Azure Rights Management mit Exchange Online.

2. Neben der Standardkonfiguration zur Aktivierung von IRM für Exchange Online führen Sie die folgenden PowerShell-Befehle aus, um sicherzustellen, dass Benutzer E-Mails lesen können, die unter dem AD RMS-Schutz gesendet wurden.

    Ersetzen Sie Ihren eigenen Domänennamen der Organisation mit *\<ihrunternehmen.domäne>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation
        $list += "https://adrms.<yourcompany.domain>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list
        Set-IRMConfiguration -internallicensingenabled $false
        Set-IRMConfiguration -internallicensingenabled $true


Bei Verwendung der Azure Information Protection-Mandantenschlüsseltopologie **vom Kunden verwaltet (BYOK)**:

-   Sie verfügen hierbei über eine reduzierte Rights Management-Schutzfunktionalität für Exchange Online. Dies ist im Artikel [BYOK – Preise und Einschränkungen](byok-price-restrictions.md) beschrieben.


## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Schritt 9: Konfigurieren der IRM-Integration für Exchange Server und SharePoint Server

Wenn Sie die Information Rights Management-Funktion (IRM) von Exchange Server oder SharePoint Server mit AD RMS verwendet haben, müssen Sie den Rights Management-Connector (RMS) bereitstellen, der als Kommunikationsschnittstelle (ein Relais) zwischen ihren lokalen Servern und dem Schutzdienst für Azure Information Protection fungiert.

Dieser Schritt behandelt die Installation und Konfiguration des Connectors, was IRM für Exchange und SharePoint deaktiviert und diese Server so konfiguriert, dass sie den Connector verwenden. Wenn Sie AD RMS-Datenkonfigurationsdateien (XML) zum Schutz von E-Mail-Nachrichten in Azure Information Protection importiert haben, müssen Sie zum Schluss noch die Registrierung auf den Exchange Server-Computern manuell bearbeiten, um alle URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten.

> [!NOTE]
> Überprüfen Sie vor Beginn unter [Lokale Server, die Azure RMS unterstützen](../get-started/requirements-servers.md) die Versionen der lokalen Server, die der Azure Rights Management-Dienst unterstützt.

### <a name="install-and-configure-the-rms-connector"></a>Installieren und Konfigurieren des RMS-Verbindungsdiensts

Verwenden Sie die Anweisungen im Artikel [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md), und führen Sie die Schritte 1 bis 4 aus. Beginnen Sie noch nicht mit Schritt 5 der Connectoranweisungen. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Deaktivieren von IRM auf Exchange Servern und Entfernen der AD RMS-Konfiguration

1.  Suchen Sie auf jedem Exchange Server den folgenden Ordner, und löschen Sie alle Einträge in diesem Ordner: **\ProgramData\Microsoft\DRM\Server\S-1-5-18**

2. Führen Sie von einem der Exchange-Server die folgenden PowerShell-Befehle aus, um sicherzustellen, dass Benutzer E-Mails lesen können, die durch Azure Rights Management geschützt sind.

    Bevor Sie diese Befehle ausführen, ersetzen Sie Ihre eigene Azure Rights Management-Dienst-URL durch die *\<URL Ihres Mandanten>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list + "<Your Tenant URL>/_wmcs/licensing"
        Set-IRMConfiguration -LicensingLocation $list

3.  Deaktivieren Sie nun die IRM-Funktionen für Nachrichten, die an interne Empfänger gesendet werden:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

4. Verwenden Sie als anschließend das gleiche Cmdlet, um IRM in Microsoft Office Outlook Web App und Microsoft Exchange ActiveSync zu deaktivieren:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Verwenden Sie schließlich das gleiche Cmdlet, um alle zwischengespeicherten Zertifikate zu löschen:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Setzen Sie nun IIS auf jedem Exchange Server zurück, z.B. indem Sie eine Eingabeaufforderung als Administrator ausführen und **iisreset** eingeben.

### <a name="disable-irm-on-sharepoint-servers-and-remove-ad-rms-configuration"></a>Deaktivieren von IRM auf SharePoint Servern und Entfernen der AD RMS-Konfiguration

1.  Stellen Sie sicher, dass keine Dokumente aus RMS-geschützten Bibliotheken ausgecheckt sind. Wenn dies der Fall ist, kann am Ende dieses Verfahrens nicht mehr darauf zugegriffen werden.

2.  Klicken Sie auf der Website der Microsoft SharePoint-Zentraladministration im Abschnitt **Schnellstart** auf **Sicherheit**.

3.  Klicken Sie auf der Seite **Sicherheit** im Abschnitt **Informationsrichtlinie** auf **Verwaltung von Informationsrechten konfigurieren**.

4.  Wählen Sie auf der Seite **Information Rights Management** im Abschnitt **Information Rights Management** **Verwenden Sie IRM nicht auf diesem Server**, und klicken Sie dann auf **OK**.

5.  Löschen Sie auf jedem der SharePoint Server-Computer den Inhalt des Ordners „\ProgramData\Microsoft\MSIPC\Server\\<*SID des Kontos, das SharePoint Server ausführt>*“.

### <a name="configure-exchange-and-sharepoint-to-use-the-connector"></a>Konfigurieren von Exchange und SharePoint zur Verwendung des Connectors

1. Wechseln Sie zurück zu den Anweisungen für die Bereitstellung des RMS-Connectors: [Schritt 5: Konfigurieren von Servern für die Verwendung des RMS-Connectors](../deploy-use/configure-servers-rms-connector.md).

    Wenn Sie nur über SharePoint Server verfügen, gehen Sie direkt zu [Nächste Schritte](#next-steps), um die Migration fortzusetzen. 

2. Fügen Sie auf jedem Exchange Server die Registrierungsschlüssel im nächsten Abschnitt manuell für jede Konfigurationsdatendatei (XML) hinzu, um die URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten. Diese Registrierungseinträge sind migrationsspezifisch und werden nicht vom Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst hinzugefügt.

    Gehen Sie beim Vornehmen dieser Änderungen an der Registrierung wie folgt vor:

    -   Ersetzen Sie *Connector FQDN* durch den Namen, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

    -   Verwenden Sie das HTTP- oder HTTPS-Präfix für die Verbindungsdienst-URL, je nachdem, ob Sie HTTP oder HTTPS für die Kommunikation zwischen dem Verbindungsdienst und Ihren lokalen Servern konfiguriert haben.

#### <a name="registry-edits-for-exchange"></a>Bearbeitung der Registrierung für Exchange

Entfernen Sie für alle Exchange-Server die Registrierungswerte, die Sie für LicenseServerRedirection während der Vorbereitungsphase hinzugefügt haben. Diese Werte wurden den folgenden Pfaden hinzugefügt:

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection


Für Exchange 2013 und Exchange 2016 – Bearbeitung der Registrierung 1:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://\<AD RMS-Intranetlizenzierungs-URL\>/_wmcs/licensing

**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://\<Connector FQDN\>/_wmcs/licensing

- https://\<Connector FQDN\>/_wmcs/licensing


---

Für Exchange 2013 – Bearbeitung der Registrierung 2:

**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 

**Typ:** Reg_SZ

**Wert:** https://\<AD RMS-Extranetlizenzierungs-URL\>/_wmcs/licensing

**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://\<Connector FQDN\>/_wmcs/licensing

- https://\<Connector FQDN\>/_wmcs/licensing

---

Für Exchange 2010 – Bearbeitung der Registrierung 1:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://\<AD RMS-Intranetlizenzierungs-URL\>/_wmcs/licensing

**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://\<Connector FQDN\>/_wmcs/licensing

- https://\<connectorname\>/_wmcs/licensing


---

Für Exchange 2010 – Bearbeitung der Registrierung 2:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://\<AD RMS-Extranetlizenzierungs-URL\>/_wmcs/licensing

**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://\<Connector FQDN\>/_wmcs/licensing

- https://\<Connector FQDN\>/_wmcs/licensing

---


## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Phase 5: Aufgaben nach der Migration](migrate-from-ad-rms-phase5.md) fort, um die Migration fortzusetzen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]