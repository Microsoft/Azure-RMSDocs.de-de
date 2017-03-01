---
title: "Azure Active Directory-Anforderungen für AIP"
description: "Lernen Sie die Azure AD-Anforderungen für die Verwendung von Azure Information Protection kennen, damit Benutzer erfolgreich authentifiziert werden können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 1422db06905f342f930bce5cd63eb4e08fc8076a
ms.lasthandoff: 02/24/2017


---

# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Azure Active Directory-Anforderungen für Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Für die Verwendung von Azure Information Protection benötigen Sie ein Azure AD-Verzeichnis. Für die Anmeldung am klassischen Azure-Portal, in dem Sie z. B. Rights Management-Vorlagen konfigurieren und verwalten können, verwenden Sie Ihr Organisationskonto für dieses Verzeichnis.

Falls Sie noch kein Azure-Abonnement für Ihre Organisation besitzen, können Sie sich für eine kostenlose Testversion anmelden. Wechseln Sie zur Seite [Erste Schritte mit Azure](https://account.windowsazure.com/organization), und befolgen Sie die Anweisungen.

Weitere Informationen finden Sie in den folgenden Ressourcen in der Azure Active Directory-Dokumentation:

-   [Was ist ein Azure AD-Verzeichnis?](/active-directory/active-directory-whatis)

-   [Beziehung zwischen Azure-Abonnements und Azure AD-Verzeichnissen](/active-directory/active-directory-how-subscriptions-associated-directory)

Wenn Sie das Azure AD-Verzeichnis in Ihre lokalen AD-Gesamtstrukturen integrieren möchten, helfen Ihnen die Informationen unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](/active-directory/active-directory-aadconnect) weiter.

### <a name="scenarios-that-have-specific-requirements"></a>Szenarien mit bestimmten Anforderungen 

Computer mit Office 2010: 

- Wenn Ihre Benutzerkonten verbunden sind (wenn Sie z. B. AD FS verwenden), müssen diese die integrierte Windows-Authentifizierung verwenden. Bei der formularbasierten Authentifizierung tritt in diesem Szenario beim Authentifizieren von Benutzern für Azure Information Protection ein Fehler auf.

Mobile Geräte oder Mac-Computer, die lokal mithilfe von AD FS oder einem äquivalenten Authentifizierungsanbieter authentifiziert werden:

- Sie müssen AD FS mit einer Mindestserverversion von **Windows Server 2012 R2** oder einem alternativen Authentifizierungsanbieter verwenden, der das OAuth 2.0-Protokoll verwendet.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Multi-Factor Authentication (MFA) und Azure Information Protection
Damit Sie Multi-Factor Authentication (MFA) mit Azure Information Protection verwenden können, ist mindestens eine der folgenden Komponenten erforderlich:

-   Office 2013 (Mindestversion):

    -   Wenn Sie Office 2013 haben, müssen Sie auch das [Update vom 9. Juni 2015 für Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853) installieren. Weitere Informationen zu diesem Update sowie dazu, wie die moderne Authentifizierung ADAL-basierte Anmeldungen (Active Directory Authentication Library) in Office 2013 integriert, finden Sie im Office-Blog unter [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) (Ankündigung der öffentlichen Vorschau für moderne Authentifizierung in Office 2013).

- Azure Information Protection-Client:

    - Der [Azure Information Protection-Client](../rms-client/aip-client.md) für Windows, iOS und Android hat immer MFA unterstützt. Es ist keine Mindestversion erforderlich. 

-   Rights Management-Freigabeanwendung für Windows:

    -   Sie müssen mindestens die Version 1.0.1908.0 installiert haben. Sie können dies in der Systemsteuerung in „Programme und Features“ prüfen. Beachten Sie, dass die Rights Management-Freigabeanwendung jetzt durch den Azure Information Protection-Client ersetzt wurde. Weitere Informationen zur Freigabeanwendung finden Sie unter [Rights Management-Freigabeanwendung für Windows](../rms-client/sharing-app-windows.md).

-   Rights Management-Freigabe-App für mobile Geräte und Mac-Computer:

    -   Stellen Sie sicher, dass Sie die neueste Version installiert haben. MFA-Unterstützung wurde in die September 2015-Version der RMS-Freigabe-App integriert.

Konfigurieren Sie dann Ihre MFA-Lösung:

-   Für von Microsoft verwaltete Mandanten (Sie haben Azure Active Directory oder Office 365):

    -   Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. Anweisungen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) in der Multi-Factor Authentication-Dokumentation.

        Weitere Informationen zu Azure MFA finden Sie unter [Was ist Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication).

-   Für Verbundmandanten (Sie betreiben Verbundserver lokal):

    -   Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Office 365. Wenn Sie beispielsweise AD FS verwenden, finden Sie Informationen unter [Konfigurieren zusätzlicher Authentifizierungsmethoden für AD FS](https://technet.microsoft.com/library/dn758113.aspx) auf TechNet.

        Weitere Informationen zu diesem Szenario finden Sie unter [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Programm „Works with Office 365 – Identity“ wurde jetzt optimiert) im Office-Blog.

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

