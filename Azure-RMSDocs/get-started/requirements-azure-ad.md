---
title: 'Azure RMS-Anforderungen: Azure AD-Verzeichnis | Azure RMS'
description: "Identifizieren Sie die Azure AD-Anforderungen für die Verwendung von Azure Rights Management (Azure RMS), damit Benutzer erfolgreich authentifiziert werden können."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: b4ac71492ba9ad883d481149a248b919973d7386


---

# Azure RMS-Anforderungen: Azure AD-Verzeichnis

>*Gilt für: Azure Rights Management, Office 365*


Sie benötigen ein Azure AD-Verzeichnis, um Azure Rights Management (Azure RMS) verwenden zu können. Für die Anmeldung am klassischen Azure-Portal, in dem Sie z. B. Rights Management-Vorlagen konfigurieren und verwalten können, verwenden Sie Ihr Organisationskonto für dieses Verzeichnis.

Falls Sie noch kein Azure-Abonnement für Ihre Organisation besitzen, können Sie sich für eine kostenlose Testversion anmelden: Folgen Sie den Anweisungen auf der [Seite für die ersten Schritten mit Azure](https://account.windowsazure.com/organization).

Weitere Informationen finden Sie in den folgenden Ressourcen in der Azure Active Directory-Dokumentation:

-   [Was ist ein Azure AD-Verzeichnis?](/active-directory/active-directory-whatis)

-   [Beziehung zwischen Azure-Abonnements und Azure AD-Verzeichnissen](/active-directory/active-directory-how-subscriptions-associated-directory)

Wenn Sie das Azure AD-Verzeichnis in Ihre lokalen AD-Gesamtstrukturen integrieren möchten, helfen Ihnen die Informationen unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](/active-directory/active-directory-aadconnect) weiter.

> [!NOTE]
> Wenn Sie über mobile Geräte oder Mac-Computer verfügen, die lokal mithilfe von AD FS oder einem äquivalenten Authentifizierungsanbieter authentifiziert werden, müssen Sie wie folgt vorgehen:
> 
> -   Sie müssen AD FS mit einer Mindestserverversion von **Windows Server 2012 R2** oder einem alternativen Authentifizierungsanbieter verwenden, der das OAuth 2.0-Protokoll verwendet.

## Multi-Factor-Authentication (MFA) und Azure RMS
Damit Sie Multi-Factor-Authentication (MFA) und Azure RMS verwenden können, ist mindestens eine der folgenden Komponenten erforderlich:

-   Office 2013 (Mindestversion):

    -   Wenn Sie Office 2013 haben, müssen Sie auch das [Update vom 9. Juni 2015 für Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853) installieren. Weitere Informationen zu diesem Update sowie dazu, wie die moderne Authentifizierung ADAL-basierte Anmeldungen (Active Directory Authentication Library) in Office 2013 integriert, finden Sie im Office-Blog unter [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) (Ankündigung der öffentlichen Vorschau für moderne Authentifizierung in Office 2013).

-   Rights Management-Freigabeanwendung für Windows:

    -   Sie müssen mindestens die Version 1.0.1908.0 installiert haben. Sie können dies in der Systemsteuerung in „Programme und Features“ prüfen. Weitere Informationen zur Freigabeanwendung finden Sie unter [Rights Management-Freigabeanwendung für Windows](../rms-client/sharing-app-windows.md).

-   Rights Management-Freigabe-App für mobile Geräte und Mac-Computer:

    -   Stellen Sie sicher, dass Sie die neueste Version installiert haben. MFA-Unterstützung wurde in die September 2015-Version der RMS-Freigabe-App integriert.

Konfigurieren Sie dann Ihre MFA-Lösung:

-   Für von Microsoft verwaltete Mandanten (Sie haben Azure Active Directory oder Office 365):

    -   Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. Anweisungen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) in der Multi-Factor Authentication-Dokumentation.

        Weitere Informationen zu Azure MFA finden Sie unter [Was ist Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication).

-   Für Verbundmandanten (Sie betreiben Verbundserver lokal):

    -   Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Office 365. Wenn Sie beispielsweise AD FS verwenden, finden Sie Informationen unter [Konfigurieren zusätzlicher Authentifizierungsmethoden für AD FS](https://technet.microsoft.com/library/dn758113.aspx) auf TechNet.

        Weitere Informationen zu diesem Szenario finden Sie unter [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Programm „Works with Office 365 – Identity“ wurde jetzt optimiert) im Office-Blog.

## Nächste Schritte
Weitere Anforderungen finden Sie unter [Voraussetzungen für Azure Rights Management](requirements-azure-rms.md).




<!--HONumber=Aug16_HO4-->


