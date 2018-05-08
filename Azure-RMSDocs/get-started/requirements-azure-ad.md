---
title: Azure Active Directory-Anforderungen für AIP
description: Lernen Sie die Azure AD-Anforderungen für die Verwendung von Azure Information Protection kennen, damit Benutzer erfolgreich authentifiziert werden können.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/26/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 53d9d9b25ab71c91275bf770a6038eccbaa2659c
ms.sourcegitcommit: f4a97427d61e4b539c91c49c952658aa2dc729ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
# <a name="azure-active-directory-requirements-for-azure-information-protection"></a>Azure Active Directory-Anforderungen für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Für die Verwendung von Azure Information Protection benötigen Sie ein Azure AD-Verzeichnis. Für die Anmeldung im Azure-Portal, in dem Sie z.B. Azure Information Protection-Bezeichnungen und Azure Rights Management-Vorlagen konfigurieren und verwalten können, verwenden Sie ein Konto aus diesem Verzeichnis.

Wenn Sie ein Abonnement mit Azure Information Protection oder Azure Rights Management besitzen, wird Ihr Azure AD-Verzeichnis bei Bedarf automatisch für Sie erstellt.  

Weitere Informationen zu Azure AD finden Sie unter [Was ist ein Azure AD-Verzeichnis?](/active-directory/active-directory-whatis).

Informationen zum Integrieren eines Azure AD-Verzeichnisses in Ihre lokalen AD-Gesamtstrukturen finden Sie unter [Integrieren Ihrer lokalen Identitäten in Azure Active Directory](/active-directory/active-directory-aadconnect).

### <a name="scenarios-that-have-specific-requirements"></a>Szenarien mit bestimmten Anforderungen 

Computer mit Office 2010: 

- Diese Computer erfordern den [Azure Information Protection-Client](../rms-client/aip-client.md) (empfohlen) oder die [Rights Management-Freigabeanwendung für Windows](../rms-client/sharing-app-windows.md) für die Authentifizierung bei Azure Information Protection und den dazugehörigen Datenschutzdienst, Azure Rights Management.

- Wenn Ihre Benutzerkonten verbunden sind (wenn Sie z. B. AD FS verwenden), müssen diese die integrierte Windows-Authentifizierung verwenden. Bei der formularbasierten Authentifizierung tritt in diesem Szenario beim Authentifizieren von Benutzern für Azure Information Protection ein Fehler auf.

Unterstützung für die zertifikatbasierte Authentifizierung (CBA):

- Die Azure Information Protection-Apps für iOS und Android unterstützen die zertifikatbasierte Authentifizierung. Informationen zum Konfigurieren einer zertifikatbasierten Authentifizierung finden Sie unter [Erste Schritte mit zertifikatbasierter Authentifizierung in Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started).

Der UPN-Wert eines Benutzers entspricht nicht seiner E-Mail-Adresse:

- Dies ist keine empfohlene Konfiguration. Wenn Sie den UPN-Wert nicht ändern können, konfigurieren Sie alternative Anmelde-IDs für Benutzer, und erläutern Sie den Benutzern, wie sie sich mit dieser alternativen Anmelde-ID bei Office anmelden. Weitere Informationen finden Sie unter [Konfigurieren einer alternativen Anmelde-ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id) und [Office-Anwendungen fordern regelmäßig Anmeldeinformationen für SharePoint Online, OneDrive und Lync Online an](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).
    
    Wenn der Domänenname im UPN-Wert eine Domäne ist, die für Ihren Mandanten überprüft wurde, fügen Sie den UPN-Wert des Benutzers als weitere E-Mail-Adresse zum Attribut „Azure AD proxyAddresses“ hinzu. Dadurch kann der Benutzer für Azure Rights Management autorisiert werden, wenn sein UPN-Wert zum Zeitpunkt der Gewährung der Nutzungsrechte festgelegt wird. Weitere Informationen hierzu und zum Autorisieren von Benutzerkonten finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](../plan-design/prepare.md).

Mobile Geräte oder Mac-Computer, die lokal mithilfe von AD FS oder einem äquivalenten Authentifizierungsanbieter authentifiziert werden:

- Sie müssen AD FS mit einer Mindestserverversion von **Windows Server 2012 R2** oder einem alternativen Authentifizierungsanbieter verwenden, der das OAuth 2.0-Protokoll verwendet.

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Multi-Factor Authentication (MFA) und Azure Information Protection
Damit Sie Multi-Factor Authentication (MFA) mit Azure Information Protection verwenden können, ist mindestens eine der folgenden Komponenten erforderlich:

-   Office 2013 (Mindestversion):

    -   Wenn Sie Office 2013 haben, müssen Sie möglicherweise ein weiteres Update zur Unterstützung der Active Directory-Authentifizierungsbibliothek(ADAL) installieren. Zum Beispiel das [Update vom 9. Juni 2015 für Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). Weitere Informationen zu diesem Update sowie dazu, wie die moderne Authentifizierung ADAL-basierte Anmeldungen (Active Directory Authentication Library) in Office 2013 integriert, finden Sie im Office-Blog unter [Office 2013 modern authentication public preview announced](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) (Ankündigung der öffentlichen Vorschau für moderne Authentifizierung in Office 2013).

- Azure Information Protection-Client:

    - Der [Azure Information Protection-Client](../rms-client/aip-client.md) für Windows, iOS und Android hat immer MFA unterstützt. Es ist keine Mindestversion erforderlich. 

-   Rights Management-Freigabeanwendung für Windows:

    - Sie müssen mindestens die Version 1.0.1908.0 installiert haben. Sie können dies in der Systemsteuerung in „Programme und Features“ prüfen. Beachten Sie, dass die Rights Management-Freigabeanwendung jetzt durch den Azure Information Protection-Client ersetzt wurde. Weitere Informationen zur Freigabeanwendung finden Sie unter [Rights Management-Freigabeanwendung für Windows](../rms-client/sharing-app-windows.md).

-   Rights Management-Freigabe-App für mobile Geräte und Mac-Computer:

    -   Stellen Sie sicher, dass Sie die neueste Version installiert haben. MFA-Unterstützung wurde in die September 2015-Version der RMS-Freigabe-App integriert.

Konfigurieren Sie dann Ihre MFA-Lösung:

-   Für von Microsoft verwaltete Mandanten (Sie haben Azure Active Directory oder Office 365):

    - Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. Anweisungen finden Sie unter [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud) in der Multi-Factor Authentication-Dokumentation.

        Weitere Informationen zu Azure MFA finden Sie unter [Was ist Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication).

- Für Verbundmandanten (Sie betreiben Verbundserver lokal):

    - Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Office 365. Wenn Sie beispielsweise AD FS verwenden, finden Sie Informationen unter [Konfigurieren zusätzlicher Authentifizierungsmethoden für AD FS](https://technet.microsoft.com/library/dn758113.aspx) auf TechNet.

        Weitere Informationen zu diesem Szenario finden Sie unter [The Works with Office 365 – Identity program now streamlined](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) (Programm „Works with Office 365 – Identity“ wurde jetzt optimiert) im Office-Blog.

Der Rights Management-Connector und der Azure Information Protection-Scanner unterstützen die MFA nicht. Wenn Sie den Connector oder den Scanner bereitstellen, dürfen die folgenden Konten keine MFA erfordern:

- Das Konto, das den Connector installiert und konfiguriert.

- Das Dienstprinzipalkonto in Azure AD, das der Connector erstellt: **Aadrm_S-1-7-0**.
 
- Das Dienstkonto, das den Scanner ausführt.

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
