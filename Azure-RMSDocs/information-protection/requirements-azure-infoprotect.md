---
title: Anforderungen an Azure Information Protection | Azure RMS
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/10/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: aa4353e5-c5b0-47f6-a6f9-87d13e8f075f
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c0652e05576ab28d7b77380ab1b8aa0ca2d3e479
ms.openlocfilehash: e3eb845af4e2cfec43c63c9625163f62c83cf954


---

# Anforderungen an Azure Information Protection

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Stellen Sie sicher, dass Sie die folgenden Anforderungen erfüllen, um das Vorschaurelease von Azure Information Protection auswerten zu können. 

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Ein Cloud-Abonnement, das Azure RMS enthält|Ihre Organisation muss ein Cloud-Abonnement besitzen, das Rights Management unterstützt.<br /><br />Weitere Informationen und Links zu kostenlosen Testversionen finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).|
|Azure AD-Verzeichnis|Ihre Organisation muss über ein Azure AD-Verzeichnis verfügen, um die Benutzerauthentifizierung für Azure RMS und Azure Information Protection zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.<br /><br />Multi-Factor Authentication (MFA) wird mit Azure RMS unterstützt, wenn Sie die erforderliche Clientsoftware haben und die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.<br /><br />Weitere Informationen finden Sie im Artikel [Azure AD-Verzeichnis](../get-started/requirements-azure-ad.md), in dem die Informationen für Azure RMS auch für Azure Information Protection gelten.|
|Clientgeräte|Diese Vorschau unterstützt die folgenden Clientgeräte:<br /><br />- Windows 10 (x86, x64)<br /><br />- Windows 8.1 (x86, x64)<br /><br />- Windows 8 (x86, x64)<br /><br />- Windows 7 Service Pack 1 (x86, x64)<br /><br />Wenn Sie Daten schützen, können sie von den gleichen Geräten genutzt werden (Windows, Mac, iOS, Android), die Azure Rights Management unterstützen. Weitere Informationen zu diesen Geräten und den unterstützten Versionen finden Sie unter [Azure RMS-Anforderungen: Clientgeräte, die Azure RMS unterstützen](../get-started/requirements-client-devices.md).|
|Anwendungen|Azure Information Protection unterstützt im Vorschau- und im GA-Release die Bezeichnung und den Schutz von Dateien und E-Mails, die mithilfe der folgenden Office-Programme erstellt wurden: **Word**, **Excel**, **PowerPoint** und **Outlook** aus folgenden Office-Suiten:<br /><br />Office Professional Plus 2016<br /><br />Office Professional Plus 2013 mit Service Pack 1<br /><br />Office Professional Plus 2010<br /><br />Eine Ankündigung, wann Azure Information Protection zusätzliche Dateitypen wie PDF, Audio-, Video- und Bilddateien unterstützen wird, können Sie nach der Veröffentlichung des allgemein verfügbaren Release auf dem [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) finden (Blog mit Informationen in englischer Sprache zu Enterprise Mobility und Sicherheit).|
|Infrastruktur, die Verbindungen mit dem Internet und abhängige Cloud-Dienste unterstützt|Wenn Sie eine Firewall oder ähnliche zwischengeschaltete Netzwerkgeräte nutzen, die dazu konfiguriert werden müssen, bestimmte Verbindungen zu erlauben, lesen Sie die Informationen zu **Azure Rights Management (RMS)** im Abschnitt [Office 365-Portal und gemeinsame Dienste](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2#BKMK_Portal-identity) aus dem folgenden Office-Artikel: [URLs und IP-Adressbereiche von Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2)<br /><br />Zusätzlich:<br /><br />- Lassen Sie auf TCP 443 HTTPS-Datenverkehr zu **informationprotection.azure.com** zu.<br /><br />– Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene). <br /><br />– Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.|

## Nächste Schritte

Wenn Sie diese Anforderungen erfüllt haben, probieren Sie unser Tutorial aus, um Azure Information Protection einständig zu erleben und zu konfigurieren: [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).




<!--HONumber=Aug16_HO2-->


