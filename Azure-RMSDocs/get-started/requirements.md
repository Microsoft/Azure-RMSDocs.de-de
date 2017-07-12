---
title: Anforderungen an Azure Information Protection
description: "Voraussetzungen für die Bereitstellung von Azure Information Protection für Ihre Organisation."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/09/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 66874f6e60c2cd5efb2dedaae470170811a84a67
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="requirements-for-azure-information-protection" class="xliff"></a>

# Anforderungen an Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, müssen die folgenden Voraussetzungen erfüllt sein. 

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Abonnement für Azure Information Protection|Zur Klassifizierung, zur Bezeichnung und zum Schutz benötigen Sie einen [Azure Information Protection-Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing). Für die reine Schutzfunktion benötigen Sie einen [Office 365-Plan, der Rights Management umfasst](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).<br /><br /> Überprüfen Sie anhand der [Abonnementinformationen](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) und der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website, ob das Abonnement Ihrer Organisation die gewünschten Azure Information Protection-Features umfasst.<br /><br />Hinweis: Wenn Sie Fragen zu Abonnements oder zur Lizenzierung haben, veröffentlichen Sie sie nicht auf dieser Seite, sondern wenden Sie sich an Ihren Microsoft-Kundenbetreuer oder an den [Microsoft-Support](information-support.md#to-contact-microsoft-support). |
|Azure Active Directory|Ihre Organisation muss über ein Azure Active Directory-Verzeichnis (Azure AD) verfügen, um die Benutzerauthentifizierung und -autorisierung für Azure Information Protection zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.<br /><br />Multi-Factor Authentication (MFA) wird mit Azure Information Protection unterstützt, wenn die erforderliche Clientsoftware installiert ist und Sie die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.<br /><br />Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [Azure Active Directory-Anforderungen für Azure Information Protection](requirements-azure-ad.md). <br /><br />Weitere Informationen zu den Anforderungen zum Autorisieren von Benutzer- und Gruppenkonten finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](../plan-design/prepare.md).|
|Clientgeräte|Benutzer müssen Clientgeräte (Computer oder mobile Geräte) verwenden, unter deren Betriebssystem Azure Information Protection unterstützt wird.<br /><br />Die folgenden Geräte unterstützen den Azure Information Protection-Client, mit dem Benutzer ihre Office-Dokumente und E-Mails klassifizieren und bezeichnen können:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 Service Pack 1 (x86, x64)<br /><br />- Windows Server 2016 <br /><br /> - Windows Server 2012 R2 und Windows Server 2012<br /><br />Wenn auf diesem Client die Daten mit dem Azure Rights Management-Dienst geschützt werden, können die Daten von den gleichen Geräten (Windows, Mac, iOS, Android) genutzt werden, die auch den Azure Rights Management-Dienst unterstützen. <br /><br />Weitere Informationen zu den vom Azure Rights Management-Dienst unterstützten Geräten finden Sie unter [Clientgeräte mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-client-devices.md).|
|Anwendungen|Der Azure Information Protection-Client kann Dateien und E-Mails bezeichnen und schützen, indem er die Office-Anwendungen **Word**, **Excel**, **PowerPoint** und **Outlook** aus einer der folgenden Office-Suiten verwendet:<br /><br /> – Office 365 ProPlus mit 2016-Apps oder 2013-Apps (Klick-und-Los- oder Windows Installer-basierte Installation)<br /><br />Office Professional Plus 2016<br /><br />Office Professional Plus 2013 mit Service Pack 1<br /><br />Office Professional Plus 2010 <br /><br />Andere Office-Suiten können keine Dokumente und E-Mails mithilfe eines Rights Management-Diensts schützen. Bei diesen Suiten wird Azure Information Protection nur für die Klassifizierung unterstützt, während Bezeichnungen, die Schutz anwenden, nicht in der Azure Information Protection-Leiste angezeigt werden. <br /><br />Informationen dazu, welche Office-Editionen den Datenschutzdienst unterstützen, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-applications.md).|
|Infrastruktur, die Verbindungen mit dem Internet und abhängige Cloud-Dienste unterstützt|Wenn Sie eine Firewall oder ähnliche zwischengeschaltete Netzwerkgeräte nutzen, die konfiguriert werden müssen, um bestimmte Verbindungen zu erlauben, lesen Sie die Informationen zu **Azure Rights Management (RMS)** im Abschnitt [Office 365-Portal und gemeinsame Dienste](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) aus dem folgenden Office-Artikel: [URLs und IP-Adressbereiche von Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).<br /><br />Verwenden Sie die Anleitungen in diesem Office-Artikel, um bei Änderungen an diesen Informationen mithilfe eines RSS-Feed-Abonnements auf dem neuesten Stand zu bleiben.<br /><br />Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure Information Protection:<br /><br />- Lassen Sie auf TCP 443 HTTPS-Datenverkehr zu **api.informationprotection.azure.com** zu.<br /><br />– Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene). Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um ihre Kommunikation mit Azure RMS zu sichern.<br /><br />– Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.|

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
> Es gibt einen unterstützten Migrationspfad [von AD RMS zu Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) und [von Azure Information Protection zu AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](../deploy-use/decommission-deactivate.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


