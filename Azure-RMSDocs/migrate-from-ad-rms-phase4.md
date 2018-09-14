---
title: Migrieren von AD RMS-Azure Information Protection – Phase 4
description: Phase 4 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 8 bis 9 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/01/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 84bd09aef5390c9ff8eee299febf41e91c2cb606
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44149479"
---
# <a name="migration-phase-4---supporting-services-configuration"></a>Migrationsphase 4: Unterstützung der Dienstekonfiguration

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Verwenden Sie die folgenden Informationen für Phase 4 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 8 bis 9 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.



## <a name="step-8-configure-irm-integration-for-exchange-online"></a>Schritt 8: Konfigurieren der IRM-Integration mit Exchange Online

> [!IMPORTANT]
> Da Sie nicht steuern können, welche Empfänger migrierte Benutzer womöglich für geschützte E-Mails auswählen, stellen Sie sicher, dass alle Benutzer und E-Mail-aktivierte Gruppen in Ihrer Organisation über ein Konto in Azure AD verfügen, das mit Azure Information Protection verwendet werden kann. [Weitere Informationen](prepare.md)

Gehen Sie unabhängig von der Topologie des von Ihnen ausgewählten Azure Information Protection-Mandantenschlüssels wie folgt vor:

1. Damit Exchange Online E-Mails entschlüsseln kann, die durch AD RMS geschützt sind, muss die AD RMS-URL für Ihren Cluster mit dem Schlüssel übereinstimmen, der in Ihrem Mandanten verfügbar ist. Dieser Abgleich geschieht mithilfe des DNS-SRV-Datensatzes für Ihren AD RMS-Cluster, der auch verwendet wird, um Office-Clients für die Verwendung von Azure Information Protection neu zu konfigurieren. Wenn Sie den DNS-SRV-Bericht für die Clientkonfiguration in Schritt 7 nicht erstellt haben, erstellen Sie diesen Bericht jetzt, um Exchange Online zu unterstützen. [Anweisungen](migrate-from-ad-rms-phase3.md#client-reconfiguration-by-using-dns-redirection)
    
    Wenn dieser DNS-Eintrag vorhanden ist, können Benutzer, die Outlook im Web und mobile E-Mail-Clients verwenden, AD RMS-geschützte E-Mails in diesen Apps anzeigen. Zudem kann Exchange den von AD RMS importierten Schlüssel zum Entschlüsseln, Indizieren, Erfassen und Schützen von Inhalten verwenden, die durch AD RMS geschützt wurden.  

2. Führen Sie den Exchange Online-Befehl [Get-IRMConfiguration](https://technet.microsoft.com/library/dd776120(v=exchg.160\).aspx) aus. Wenn Sie beim Ausführen dieses Befehls Hilfe benötigen, sehen Sie sich die ausführlichen Anweisungen unter [Exchange Online: IRM-Konfiguration](/..deploy-use/configure-office365.md#exchange-online-irm-configuration) an.
    
    Überprüfen Sie mithilfe der Ausgabe, ob **AzureRMSLicensingEnabled** auf **TRUE** festlegt ist:
    
    - Wenn AzureRMSLicensingEnabled auf **TRUE** festgelegt ist, ist für diesen Schritt keine weitere Konfiguration vonnöten. 
    
    - Wenn AzureRMSLicensingEnabled auf **FALSE** festgelegt ist, führen Sie `Set-IRMConfiguration -AzureRMSLicensingEnabled $true` aus, führen Sie anschließend die Überprüfungsschritte vom Artikel [Set up new Office 365 Message Encryption capabilities built on top of Azure Information Protection (Einrichten von neuen Funktionen der Office 365-Nachrichtenverschlüsselung, die auf Azure Information Protection aufgebaut sind)](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) durch, um sicherzustellen, dass Exchange Online nun zur Verwendung des Azure Rights Management-Diensts bereit ist. 

## <a name="step-9-configure-irm-integration-for-exchange-server-and-sharepoint-server"></a>Schritt 9: Konfigurieren der IRM-Integration für Exchange Server und SharePoint Server

Wenn Sie die Information Rights Management-Funktion (IRM) von Exchange Server oder SharePoint Server mit AD RMS verwendet haben, müssen Sie den Rights Management-Connector (RMS) bereitstellen, der als Kommunikationsschnittstelle (ein Relais) zwischen ihren lokalen Servern und dem Schutzdienst für Azure Information Protection fungiert.

Dieser Schritt behandelt die Installation und Konfiguration des Connectors, die Deaktivierung von IRM für Exchange und SharePoint und die Konfiguration dieser Server für die Verwendung des Connectors. Wenn Sie AD RMS-Datenkonfigurationsdateien (XML) zum Schutz von E-Mail-Nachrichten in Azure Information Protection importiert haben, müssen Sie zum Schluss noch die Registrierung auf den Exchange Server-Computern manuell bearbeiten, um alle URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten.

> [!NOTE]
> Überprüfen Sie vor Beginn unter [Lokale Server, die Azure RMS unterstützen](./requirements-servers.md) die Versionen der lokalen Server, die der Azure Rights Management-Dienst unterstützt.

### <a name="install-and-configure-the-rms-connector"></a>Installieren und Konfigurieren des RMS-Verbindungsdiensts

Verwenden Sie die Anweisungen im Artikel [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md), und führen Sie die Schritte 1 bis 4 aus. Beginnen Sie noch nicht mit Schritt 5 der Connectoranweisungen. 

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Deaktivieren von IRM auf Exchange Servern und Entfernen der AD RMS-Konfiguration

1.  Suchen Sie auf jedem Exchange Server den folgenden Ordner, und löschen Sie alle Einträge in diesem Ordner: **\ProgramData\Microsoft\DRM\Server\S-1-5-18**

2. Führen Sie von einem der Exchange-Server die folgenden PowerShell-Befehle aus, um sicherzustellen, dass Benutzer E-Mails lesen können, die durch Azure Rights Management geschützt sind.

    Bevor Sie diese Befehle ausführen, ersetzen Sie Ihre eigene Azure Rights Management-Dienst-URL durch die *\<URL Ihres Mandanten>*.

        $irmConfig = Get-IRMConfiguration
        $list = $irmConfig.LicensingLocation 
        $list += "<Your Tenant URL>/_wmcs/licensing"
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

1. Wechseln Sie zurück zu den Anweisungen für die Bereitstellung des RMS-Connectors: [Schritt 5: Konfigurieren von Servern für die Verwendung des RMS-Connectors](./configure-servers-rms-connector.md).

    Wenn Sie nur über SharePoint Server verfügen, gehen Sie direkt zu [Nächste Schritte](#next-steps), um die Migration fortzusetzen. 

2. Fügen Sie auf jedem Exchange Server die Registrierungsschlüssel im nächsten Abschnitt manuell für jede Konfigurationsdatendatei (XML) hinzu, um die URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten. Diese Registrierungseinträge sind migrationsspezifisch und werden nicht vom Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst hinzugefügt.

    Gehen Sie beim Vornehmen dieser Änderungen an der Registrierung wie folgt vor:

    -   Ersetzen Sie *Connector FQDN* durch den Namen, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

    -   Verwenden Sie das HTTP- oder HTTPS-Präfix für die Verbindungsdienst-URL, je nachdem, ob Sie HTTP oder HTTPS für die Kommunikation zwischen dem Verbindungsdienst und Ihren lokalen Servern konfiguriert haben.

#### <a name="registry-edits-for-exchange"></a>Bearbeitung der Registrierung für Exchange

Fügen Sie für alle Exchange-Server die folgenden Registrierungswerte zu „LicenseServerRedirection“ hinzu, abhängig von Ihren Exchange-Versionen:

---

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

Exchange 2013 – Bearbeitung der Registrierung 2:

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
