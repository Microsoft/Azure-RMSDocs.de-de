---
title: Registrierungseinstellungen für den Rights Management-Connector – AIP
description: Informationen zu den Registrierungseinträgen auf Servern, die den RMS-Connector verwenden. Die empfohlene Methode zum Konfigurieren dieser Einstellungen ist die Verwendung des Serverkonfigurationstools für den Microsoft RMS-Connector.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 11/30/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39
ms.subservice: connector
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: fb2a081b03ae8b92fa58073b37336066f087da4c
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567715"
---
# <a name="registry-setting-for-the-rights-management-connector"></a>Registrierungseinstellung für den Rights Management-Verbindungsdienst

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*


Verwenden Sie die Tabellen in den folgenden Abschnitten nur, wenn Sie Registrierungseinstellungen auf den Servern manuell hinzufügen oder überprüfen möchten, die Exchange, SharePoint oder Windows Server ausführen. Diese Registrierungseinstellungen konfigurieren die Server zur Verwendung des [RMS-Connectors](deploy-rms-connector.md). Die empfohlene Methode zum Konfigurieren dieser Server ist die Verwendung des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst.

Anleitungen für den Fall, dass Sie diese Einstellungen verwenden:

-   *\<YourTenantURL>* ist die URL des Azure-Rights Management Dienstanbieter für Ihren Azure Information Protection Mandanten. So finden Sie diesen Wert

    1.  Führen Sie das Cmdlet [Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration) für den Azure Rights Management-Dienst aus. Wenn Sie das aipservice-Modul noch nicht installiert haben, finden Sie weitere Informationen unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

    2.  Identifizieren Sie in der Ausgabe den Wert von **LicensingIntranetDistributionPointUrl**.

        Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Entfernen Sie in dem Wert **/_wmcs/licensing** aus der Zeichenfolge. Die Zeichenfolge, die übrig bleibt, ist Ihre Azure Rights Management-Dienst-URL In unserem Beispiel wäre die Azure Rights Management-Dienst-URL der folgende Wert:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**
        
        Sie können überprüfen, ob Sie den korrekten Wert besitzen, indem Sie den folgenden PowerShell-Befehl ausführen.

        ```ps
        (Get-AipServiceConfiguration).LicensingIntranetDistributionPointUrl -match "https:\/\/[0-9A-Za-z\.-]*" | Out-Null; $matches[0]
        ```

-   *\<ConnectorFQDN>* ist der Name des Lasten Ausgleichs, den Sie in DNS für den Connector definiert haben. Beispielsweise **rmsconnector.contoso.com**.

-   Verwenden Sie das HTTPS-Präfix für die Connector-URL, wenn Sie den Connector für die Verwendung von HTTPS zur Kommunikation mit Ihren lokalen Servern konfiguriert haben. Weitere Informationen finden Sie im Abschnitt [Konfigurieren des RMS-Connector für die Verwendung von HTTPS](install-configure-rms-connector.md#configuring-the-rms-connector-to-use-https) in der Hauptanleitung. Die Azure AD Rights Management-Dienst-URL verwendet immer HTTPS.


## <a name="exchange-2016-or-exchange-2013-registry-settings"></a>Exchange 2016- oder Exchange 2013-Registrierungseinstellungen

**Registrierungs Pfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https:// *\<YourTenantURL>* /_wmcs/Certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https:// *\<YourTenantURL>* /_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*\<YourTenantURL>*


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*< \connectori>*

- https://*< \connectori>*

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*< \yourtenanturl>*


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*< \connectori>*

- https://*< \connectori>*


## <a name="exchange-2010-registry-settings"></a>Exchange 2010-Registrierungseinstellungen

**Registrierungs Pfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*< \yourtenanturl>*/_wmcs/Certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*<\IhreMandantenURL>*/_wmcs/Licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*< \yourtenanturl>*

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*< \connectori>*

- https://*< \connectori>*

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*< \yourtenanturl>*

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*< \connectori>*

- https://*< \connectori>*


## <a name="sharepoint-2016-or-sharepoint-2013-registry-settings"></a>Registrierungseinstellungen für SharePoint 2016 oder SharePoint 2013

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**Typ:** Reg_SZ

**Wert:** https://*<\IhreMandantenURL>*/_wmcs/licensing


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*< \connectori>*/_wmcs/licensing

- https://*< \connectori>*/_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*< \connectori>*/_wmcs/Certification

- https://*< \connectori>*/_wmcs/Certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*< \connectori>*/_wmcs/licensing

- https://*< \connectori>*/_wmcs/licensing




## <a name="file-server-and-file-classification-infrastructure-registry-settings"></a>Registrierungseinstellungen für Dateiserver, die die Dateiklassifizierungsinfrastruktur verwenden

**Registrierungs Pfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** http://*< \Connector>*/_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** http://*< \Connector>*/_wmcs/Certification


Zurück zu [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md)
