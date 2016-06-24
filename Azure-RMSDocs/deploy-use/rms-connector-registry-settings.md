---
# required metadata

title: Registrierungseinstellungen für den RMS-Verbindungsdienst | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed3e9a3d-0f7c-4abc-9d0b-aa3b18403d39

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Registrierungseinstellung für den Rights Management-Verbindungsdienst

*Gilt für: Azure Rights Management, Office 365*


Verwenden Sie die Tabellen in den folgenden Abschnitten nur, wenn Sie Registrierungseinstellungen auf den Servern mit Exchange, SharePoint oder Windows Server, mit denen die Server für die Verwendung des [RMS-Verbindungsdiensts](deploy-rms-connector.md) konfiguriert werden, manuell hinzufügen oder überprüfen möchten. Die empfohlene Methode zum Konfigurieren dieser Server ist die Verwendung des Serverkonfigurationstools für den Microsoft RMS-Verbindungsdienst.

Anleitungen für den Fall, dass Sie diese Einstellungen verwenden:

-   *MicrosoftRMSURL* ist die URL des Microsoft RMS-Diensts Ihrer Organisation. So finden Sie diesen Wert

    1.  Führen Sie das [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS aus. Wenn Sie das Windows PowerShell-Modul für Azure RMS noch nicht installiert haben, helfen Ihnen die Informationen unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md) weiter..

    2.  Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.

        Beispiel: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

    3.  Entfernen Sie im Wert den Text **/_wmcs/licensing** aus der Zeichenfolge. Die restliche Zeichenfolge ist Ihre Microsoft RMS-URL. In unserem Beispiel hätte die Microsoft RMS-URL folgenden Wert:

        **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

-   *ConnectorFQDN* ist der Name des Lastenausgleichs, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

-   Verwenden Sie das HTTPS-Präfix für die Connector-URL, wenn Sie den Connector für die Verwendung von HTTPS zur Kommunikation mit Ihren lokalen Servern konfiguriert haben. Weitere Informationen finden Sie in diesem Thema im Abschnitt [Konfigurieren des RMS-Verbindungsdiensts für die Verwendung von HTTPS](deploy-rms-connector.md#BKMK_ConfiguringHTTPS). Die Microsoft RMS-URLs verwenden immer HTTPS.


## Exchange 2016- oder Exchange 2013-Registrierungseinstellungen

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*MicrosoftRMSURL*


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*MicrosoftRMSURL*


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*


## Exchange 2010-Registrierungseinstellungen

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*MicrosoftRMSURL*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** https://*MicrosoftRMSURL*/_wmcs/Licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*MicrosoftRMSURL*

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection

**Typ:** Reg_SZ

**Wert:** https://*MicrosoftRMSURL*

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*

- https://*ConnectorFQDN*


## Registrierungseinstellungen für SharePoint 2016 oder SharePoint 2013

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection

**Typ:** Reg_SZ

**Wert:** https://*MicrosoftRMSURL*/_wmcs/licensing


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*/_wmcs/licensing

- https://*ConnectorFQDN*/_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*/_wmcs/certification

- https://*ConnectorFQDN*/_wmcs/certification

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default


**Daten:** Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem SharePoint-Server zum RMS-Connector verwenden:

- http://*ConnectorFQDN*/_wmcs/licensing

- https://*ConnectorFQDN*/_wmcs/licensing




## Registrierungseinstellungen für Dateiserver, die die Dateiklassifizierungsinfrastruktur verwenden

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** http://*ConnectorFQDN*/_wmcs/licensing

---

**Registrierungspfad:** HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation

**Typ:** Reg_SZ

**Wert:** Default

**Daten:** http://*ConnectorFQDN*/_wmcs/certification


Zurück zu [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md)

<!--HONumber=Apr16_HO4-->


