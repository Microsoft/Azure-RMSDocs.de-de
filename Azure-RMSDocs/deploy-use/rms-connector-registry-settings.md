---
title: Registrierungseinstellungen für den Rights Management-Connector – AIP
description: Informationen zu den Registrierungseinträgen auf Servern, die den RMS-Connector verwenden. Die empfohlene Methode zum Konfigurieren dieser Einstellungen ist die Verwendung des Serverkonfigurationstools für den Microsoft RMS-Connector.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/01/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bc0cb2a7349bf19ee19a42bdb283cd86297748bc
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="registry-setting-for-the-rights-management-connector"></a>Registrierungseinstellung für den Rights Management-Verbindungsdienst

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Verwenden Sie die Tabellen in den folgenden Abschnitten nur, wenn Sie Registrierungseinstellungen auf den Servern manuell hinzufügen oder überprüfen möchten, die Exchange, SharePoint oder Windows Server ausführen. Diese Registrierungseinstellungen konfigurieren die Server zur Verwendung des [RMS-Connectors](deploy-rms-connector.md). Die empfohlene Methode zum Konfigurieren dieser Server ist die Verwendung des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst.

Anleitungen für den Fall, dass Sie diese Einstellungen verwenden:

-   *\<IhreMandantenURL>* ist Ihre Azure Rights Management-Dienst-URL für Ihren Azure Rights Management-Mandanten. So finden Sie diesen Wert

    1.  Führen Sie das [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx)-Cmdlet für den Azure Rights Management-Dienst aus. Wenn Sie das Windows PowerShell-Modul für Azure RMS noch nicht installiert haben, lesen Sie [Installieren des AADRM-PowerShell-Moduls](install-powershell.md).

    2.  Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.

        Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Entfernen Sie im Wert den Text **/_wmcs/licensing** aus der Zeichenfolge. Die Zeichenfolge, die übrig bleibt, ist Ihre Azure Rights Management-Dienst-URL In unserem Beispiel wäre die Azure Rights Management-Dienst-URL der folgende Wert:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**
        
        Sie können überprüfen, ob Sie den korrekten Wert besitzen, indem Sie den folgenden PowerShell-Befehl ausführen.
        
            (Get-AadrmConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]

-   *\<ConnectorFQDN>* ist der Name des Lastenausgleichs, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

-   Verwenden Sie das HTTPS-Präfix für die Connector-URL, wenn Sie den Connector für die Verwendung von HTTPS zur Kommunikation mit Ihren lokalen Servern konfiguriert haben. Weitere Informationen finden Sie im Abschnitt [Konfigurieren des RMS-Connector für die Verwendung von HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) in der Hauptanleitung. Die Azure AD Rights Management-Dienst-URL verwendet immer HTTPS.


## <a name="exchange-2016-or-exchange-2013-registry-settings"></a>Exchange 2016- oder Exchange 2013-Registrierungseinstellungen

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*\<IhreMandantenURL>*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*\<IhreMandantenURL>*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*\<IhreMandantenURL>*


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*<\IhreMandantenURL>*


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*


## <a name="exchange-2010-registry-settings"></a>Exchange 2010-Registrierungseinstellungen

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*<\IhreMandantenURL>*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*<\IhreMandantenURL>*/_wmcs/Licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*<\IhreMandantenURL>*

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*<\IhreMandantenURL>*

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*

- https://*<\ConnectorFQDN>*


## <a name="sharepoint-2016-or-sharepoint-2013-registry-settings"></a>Registrierungseinstellungen für SharePoint 2016 oder SharePoint 2013

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**Typ:** Reg_SZ

**Wert:** https://*<\IhreMandantenURL>*/_wmcs/licensing


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*/_wmcs/licensing

- https://*<\ConnectorFQDN>*/_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*/_wmcs/certification

- https://*<\ConnectorFQDN>*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*<\ConnectorFQDN>*/_wmcs/licensing

- https://*<\ConnectorFQDN>*/_wmcs/licensing




## <a name="file-server-and-file-classification-infrastructure-registry-settings"></a>Registrierungseinstellungen für Dateiserver, die die Dateiklassifizierungsinfrastruktur verwenden

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** http://*<\ConnectorFQDN>*/_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** http://*<\ConnectorFQDN>*/_wmcs/certification


Zurück zu [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]