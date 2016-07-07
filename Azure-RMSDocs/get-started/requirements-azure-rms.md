---
title: "Voraussetzungen für Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/17/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.sourcegitcommit: 50ebcd71336baeb68687e2d0c1ff1f0608925761
ms.openlocfilehash: 72a75712da9efa201865440affa80461dcd7df53


---

# Voraussetzungen für Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*


Für die Bereitstellung von Azure Rights Management (RMS) in Ihrer Organisation müssen die folgenden Voraussetzungen erfüllt sein. Anschließend können Sie Rights Management mithilfe der [Roadmap für die Bereitstellung von Azure Rights Management](../plan-design/deployment-roadmap.md) für Ihre Organisation bereitstellen.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Cloud-Abonnement für RMS|Ihre Organisation muss ein Cloud-Abonnement besitzen, das RMS unterstützt.<br /><br />Informationen zur Lizenzierung finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](requirements-subscriptions.md).|
|Azure AD-Verzeichnis|Ihre Organisation muss ein Azure AD-Verzeichnis besitzen, um die Benutzerauthentifizierung für RMS zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.<br /><br />Multi-Factor Authentication (MFA) wird mit Azure RMS unterstützt, wenn Sie die erforderliche Clientsoftware haben und die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.<br /><br />Weitere Informationen finden Sie unter [Azure AD-Verzeichnis](requirements-azure-ad.md).|
|Clientgeräte|Benutzer müssen Clientgeräte (Computer oder mobile Geräte) besitzen, die ein Betriebssystem ausführen, das RMS unterstützt.<br /><br />Weitere Informationen finden Sie unter [Clientgeräte, die Azure RMS unterstützen](requirements-client-devices.md).|
|Applications|Benutzer müssen Anwendungen ausführen, die RMS unterstützen.<br /><br />Weitere Informationen finden Sie unter [Anwendungen, die Azure RMS unterstützen](requirements-applications.md).|
|Infrastruktur, die Verbindungen mit dem Internet und abhängige Cloud-Dienste unterstützt|Wenn Sie eine Firewall oder ähnliche Interventionsnetzwerkgeräte verwenden, die so konfiguriert werden müssen, dass bestimmte Verbindungen erlaubt sind, helfen Ihnen die Informationen unter [Office 365-URLs und IP-Adressbereiche](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) weiter.<br /><br />Die Liste mit den URLs und IP-Adressen in den Abschnitten **Office 365-Portal und gemeinsame Dienste** und **Office 365-Authentifizierung und -Identität** gilt für das Office 365-Portal, Azure Active Directory-Ressourcen und Azure Rights Management. Verwenden Sie die Anleitungen in diesem Artikel, um bei Änderungen an diesen Informationen auf dem neuesten Stand zu bleiben, indem Sie einen RSS-Feed abonnieren.<br /><br />Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure RMS:<br /><br />– Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene). Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um ihre Kommunikation mit Azure RMS zu sichern.<br /><br />– Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.|

Wenn Sie Azure RMS mit lokalen Servern verwenden möchten, werden folgende Produkte unterstützt:

-   Exchange Server

-   SharePoint Server

-   Windows Server-Dateiserver, die die Dateiklassifizierungsinfrastruktur unterstützen.

Informationen zu den zusätzlichen Voraussetzungen für Azure RMS für dieses Szenario finden Sie unter [Lokale Server, die Azure RMS unterstützen](requirements-servers.md).

> [!IMPORTANT] Das folgende Bereitstellungsszenario wird nicht unterstützt:
> 
> -   Parallele Ausführung von AD RMS und Azure RMS in derselben Organisation (mit Ausnahme der Migration), wie unter [Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md) beschrieben.
> 
> Es gibt einen unterstützten Migrationspfad [von AD RMS zu Azure RMS](http://technet.microsoft.com/library/Dn858447.aspx) und von [Azure RMS zu AD RMS](http://msdn.microsoft.com/library/azure/dn629429.aspx). Wenn Sie Azure RMS bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md).






<!--HONumber=Jun16_HO3-->


