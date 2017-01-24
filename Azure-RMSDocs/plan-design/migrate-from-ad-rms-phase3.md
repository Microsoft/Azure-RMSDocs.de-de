---
title: "Migrieren von AD RMS zu Azure Information Protection – Phase 3 | Azure Information Protection"
description: Phase 3 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 6 bis 7 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8b039ad5-95a6-4c73-9c22-78c7b0e12cb7
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 0ad1df8a8343052a85f85b94e0413fe0a0265d4b


---

# <a name="migration-phase-3---supporting-services-configuration"></a>Migrationsphase 3: Unterstützung der Dienstekonfiguration

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*


Verwenden Sie die folgenden Informationen für Phase 3 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 6 bis 7 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.


## <a name="step-6-configure-irm-integration-for-exchange-online"></a>Schritt 6: Konfigurieren der IRM-Integration mit Exchange Online

Wenn Sie Ihre TDP von AD RMS mit Exchange Online bereits importiert haben, müssen Sie diese TDP entfernen, um Konflikte verursachende Vorlagen und Richtlinien nach der Migration zu Azure Information Protection zu vermeiden. Verwenden Sie hierzu das Exchange Online-Cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/library/jj200720%28v=exchg.150%29.aspx).

Bei Verwendung der Azure Information Protection-Mandantenschlüsseltopologie **von Microsoft verwaltet**:

-   Informationen finden Sie im Abschnitt [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration) im Artikel [Office 365: Konfigurationen für Clients und Onlinedienste](../deploy-use/configure-office365.md). Dieser Abschnitt enthält typische auszuführende Befehle, die eine Verbindung mit dem Exchange Online-Dienst herstellen, den Mandantenschlüssel aus Azure Information Protection importieren und IRM-Funktionen für Exchange Online aktivieren. Nachdem Sie diese Schritte abgeschlossen haben, verfügen Sie über die volle Schutzfunktionalität von Azure Rights Management mit Exchange Online.

Bei Verwendung der Azure Information Protection-Mandantenschlüsseltopologie **vom Kunden verwaltet (BYOK)**:

-   Sie verfügen hierbei über eine reduzierte Rights Management-Schutzfunktionalität für Exchange Online. Dies ist im Artikel [BYOK – Preise und Einschränkungen](byok-price-restrictions.md) beschrieben.

## <a name="step-7-deploy-the-rms-connector"></a>Schritt 7: Bereitstellen des RMS-Connectors
Wenn Sie die Funktion zur Verwaltung von Informationsrechten (IRM) von Exchange Server oder SharePoint Server mit AD RMS verwendet haben, müssen Sie zuerst IRM auf diesen Servern deaktivieren und die AD RMS-Konfiguration entfernen. Anschließend stellen Sie den Rights Management-Connector (RMS-Connector) bereit, der als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und dem Schutzdienst von Azure Information Protection fungiert.

Wenn Sie mehrere AD RMS-Datenkonfigurationsdateien (XML) zum Schutz von E-Mail-Nachrichten in Azure Information Protection importiert haben, müssen Sie zum Schluss noch die Registrierung auf den Exchange Server-Computern manuell bearbeiten, um alle URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten.

> [!NOTE]
> Überprüfen Sie vor Beginn unter [Lokale Server, die Azure RMS unterstützen](../get-started/requirements-servers.md) die Versionen der lokalen Server, die der Azure Rights Management-Dienst unterstützt.

### <a name="disable-irm-on-exchange-servers-and-remove-ad-rms-configuration"></a>Deaktivieren von IRM auf Exchange Servern und Entfernen der AD RMS-Konfiguration

1.  Suchen Sie auf jedem Exchange Server den folgenden Ordner, und löschen Sie alle Einträge in diesem Ordner: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Verwenden Sie auf einem der Exchange Server das Exchange-Cmdlet [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) , um zuerst IRM-Funktionen für Nachrichten, die an interne Empfänger gesendet werden, zu deaktivieren:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Verwenden Sie dann das gleiche Cmdlet, um IRM-Funktionen für Nachrichten, die an externe Empfänger gesendet werden, zu deaktivieren:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Verwenden Sie als Nächstes das gleiche Cmdlet, um IRM in Microsoft Office Outlook Web App und Microsoft Exchange ActiveSync zu deaktivieren:

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

5.  Löschen Sie auf jedem der SharePoint Server-Computer den Inhalt des Ordners „\ProgramData\Microsoft\MSIPC\Server\*&lt;SID des Kontos, das SharePoint Server ausführt&gt;*“.

#### <a name="install-and-configure-the-rms-connector"></a>Installieren und Konfigurieren des RMS-Verbindungsdiensts

-   Verwenden Sie die Anweisungen im Artikel [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

#### <a name="for-exchange-only-and-multiple-tpds-edit-the-registry"></a>Nur für Exchange und mehrere TPDs: Bearbeiten der Registrierung

-   Fügen Sie auf jedem Exchange Server die folgenden Registrierungsschlüssel manuell für jede zusätzlich importierte Datei mit Konfigurationsdaten (XML) hinzu, um die URLs von vertrauenswürdigen Veröffentlichungsdomänen an den RMS-Connector umzuleiten. Diese Registrierungseinträge sind migrationsspezifisch und werden nicht vom Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst hinzugefügt.

    Gehen Sie beim Vornehmen dieser Änderungen an der Registrierung wie folgt vor:

    -   Ersetzen Sie *ConnectorFQDN* durch den Namen, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

    -   Verwenden Sie das HTTP- oder HTTPS-Präfix für die Verbindungsdienst-URL, je nachdem, ob Sie HTTP oder HTTPS für die Kommunikation zwischen dem Verbindungsdienst und Ihren lokalen Servern konfiguriert haben.

Für Exchange 2013 – Bearbeitung der Registrierung 1:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:**

Reg_SZ

**Wert:**

https://<AD RMS Intranet Licensing URL>/_wmcs/licensing

**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorName>/_wmcs/licensing


---

Für Exchange 2013 – Bearbeitung der Registrierung 2:

**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection 


**Typ:**

Reg_SZ

**Wert:**

https://<AD RMS Extranet Licensing URL>/_wmcs/licensing


**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorFQDN>/_wmcs/licensing

---

Für Exchange 2010 – Bearbeitung der Registrierung 1:



**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:**

Reg_SZ

**Wert:**

https://<AD RMS Intranet Licensing URL>/_wmcs/licensing

**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorName>/_wmcs/licensing


---

Für Exchange 2010 – Bearbeitung der Registrierung 2:


**Registrierungspfad:**

HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection
 

**Typ:**

Reg_SZ

**Wert:**

https://<AD RMS Extranet Licensing URL>/_wmcs/licensing


**Daten:**

Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://<connectorFQDN>/_wmcs/licensing

- https://<connectorFQDN>/_wmcs/licensing

---

Nachdem Sie diese Verfahren ausgeführt haben, können Sie den Abschnitt **Nächste Schritte** im Artikel [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md) lesen.

## <a name="next-steps"></a>Nächste Schritte
Fahren Sie mit [Phase 4: Aufgaben nach der Migration](migrate-from-ad-rms-phase4.md) fort, um die Migration fortzusetzen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


