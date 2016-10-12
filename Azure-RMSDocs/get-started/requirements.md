---
title: Anforderungen an Azure Information Protection | Azure Information Protection
description: "Voraussetzungen für die Bereitstellung von Azure Information Protection für Ihre Organisation."
author: cabailey
manager: mbaldwin
ms.date: 10/03/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4591d5c45104108ccf151bb1d7a9382652e585a6
ms.openlocfilehash: ec0668cfa86f3331741aea1a1f88f3d60b9ed0a3


---

# Anforderungen an Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*


Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, müssen die folgenden Voraussetzungen erfüllt sein. 

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Abonnement für Azure Information Protection|Überprüfen Sie anhand der [Abonnementinformationen](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) und der [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website, ob das Abonnement Ihrer Organisation die gewünschten Azure Information Protection-Features umfasst.|
|Azure AD-Verzeichnis|Ihre Organisation muss über ein Azure AD-Verzeichnis verfügen, um die Benutzerauthentifizierung für Azure Information Protection unterstützen zu können. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.<br /><br />Multi-Factor Authentication (MFA) wird mit Azure Information Protection unterstützt, wenn die erforderliche Clientsoftware installiert ist und Sie die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.<br /><br />Weitere Informationen finden Sie unter [Azure Active Directory-Anforderungen für Azure Information Protection](requirements-azure-ad.md).|
|Clientgeräte|Benutzer müssen Clientgeräte (Computer oder mobile Geräte) verwenden, unter deren Betriebssystem Azure Information Protection unterstützt wird.<br /><br />Die folgenden Geräte unterstützen den Azure Information Protection-Client, mit dem Benutzer ihre Office-Dokumente und E-Mails klassifizieren und bezeichnen können:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 Service Pack 1 (x86, x64)<br /><br />Wenn auf diesem Client die Daten mit dem Azure Rights Management-Dienst geschützt werden, kann er von den gleichen Geräten (Windows, Mac, iOS, Android) genutzt werden, die auch den Azure Rights Management-Dienst unterstützen. <br /><br />Weitere Informationen zu den vom Azure Rights Management-Dienst unterstützten Geräten finden Sie unter [Clientgeräte mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-client-devices.md).|
|Anwendungen|Der Azure Information Protection-Client unterstützt die Bezeichnung und den Schutz von Dateien und E-Mails, die mithilfe der folgenden Office-Programme erstellt werden: **Word**, **Excel**, **PowerPoint** und **Outlook** aus folgenden Office-Suiten:<br /><br />Office Professional Plus 2016<br /><br />Office Professional Plus 2013 mit Service Pack 1<br /><br />Office Professional Plus 2010<br /><br />Informationen zu den Anwendungen, die der Azure Rights Management-Dienst unterstützt, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-applications.md).|
|Infrastruktur, die Verbindungen mit dem Internet und abhängige Cloud-Dienste unterstützt|Wenn Sie eine Firewall oder ähnliche zwischengeschaltete Netzwerkgeräte nutzen, die konfiguriert werden müssen, um bestimmte Verbindungen zu erlauben, lesen Sie die Informationen zu **Azure Rights Management (RMS)** im Abschnitt [Office 365-Portal und gemeinsame Dienste](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) aus dem folgenden Office-Artikel: [URLs und IP-Adressbereiche von Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Verwenden Sie die Anleitungen in diesem Office-Artikel, um bei Änderungen an diesen Informationen mithilfe eines RSS-Feed-Abonnements auf dem neuesten Stand zu bleiben.<br /><br />Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure Information Protection:<br /><br />- Lassen Sie auf TCP 443 HTTPS-Datenverkehr zu **api.informationprotection.azure.com** zu.<br /><br />– Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene). Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um ihre Kommunikation mit Azure RMS zu sichern.<br /><br />– Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.|

Wenn Sie den Azure Rights Management-Dienst von Azure Information Protection auf lokalen Servern verwenden möchten, werden folgende Produkte unterstützt:

-   Exchange Server

-   SharePoint Server

-   Windows Server-Dateiserver, die die Dateiklassifizierungsinfrastruktur unterstützen.

Informationen zu den zusätzlichen Anforderungen für dieses Szenario finden Sie unter [Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-servers.md).

> [!IMPORTANT]
> Das folgende Bereitstellungsszenario wird nur unterstützt, wenn Sie den AD RMS-Schutz mit Azure Information Protection verwenden (HYOK-Konfiguration, „Hold Your Own Key“):
> 
> -   Parallele Ausführung von AD RMS und Azure RMS in derselben Organisation (mit Ausnahme der Migration), wie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) beschrieben.
> 
> Es gibt einen unterstützten Migrationspfad [von AD RMS zu Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) und [von Azure Information Protection zu AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](../deploy-use/decommission-deactivate.md).






<!--HONumber=Oct16_HO1-->


