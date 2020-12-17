---
title: Zusätzliche Voraussetzungen für Azure AD und Azure Information Protection
description: Informieren Sie sich über zusätzliche Azure AD-Voraussetzungen für Azure Information Protection in bestimmten Szenarios, z. B. bei mehrstufiger oder zertifikatbasierter Authentifizierung oder bei Computern mit Office 2010.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/22/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ed25aa83-e272-437b-b445-3f01e985860c
ms.subservice: prereqs
ms.suite: ems
ms.custom: admin, has-adal-ref
ms.openlocfilehash: 7ac67d72d329f9782a80c434f936cadad3e13882
ms.sourcegitcommit: efeb486e49c3e370d7fd8244687cd3de77cd8462
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97583352"
---
# <a name="additional-azure-ad-requirements-for-azure-information-protection"></a>Zusätzliche Azure AD-Anforderungen für Azure Information Protection

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen AIP-Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Ein [Azure AD-Verzeichnis ist eine Anforderung](requirements.md#azure-active-directory) für die Verwendung von Azure Information Protection. Verwenden Sie ein Konto aus einem Azure AD-Verzeichnis, um sich beim Azure-Portal anzumelden, wo Sie Azure Information Protection-Einstellungen konfigurieren können.

Wenn Sie ein Abonnement mit Azure Information Protection oder Azure Rights Management besitzen, wird Ihr Azure AD-Verzeichnis bei Bedarf automatisch für Sie erstellt.

In den folgenden Abschnitten werden zusätzliche Azure Information Protection- und Azure AD-Anforderungen für bestimmte Szenarios aufgelistet. 

## <a name="computers-running-office-2010"></a>Computer mit Office 2010

Neben einem Azure AD-Konto benötigen Computer mit Office 2010 den Azure Information Protection-Client für Windows, um sich bei Azure Information Protection sowie dessen Datenschutzdienst Azure Rights Management zu authentifizieren. 

Wenn Ihre Benutzerkonten verbunden sind (wenn Sie z. B. AD FS verwenden), müssen diese Computer die integrierte Windows-Authentifizierung verwenden. Bei der formularbasierten Authentifizierung tritt in diesem Szenario beim Authentifizieren von Benutzern für Azure Information Protection ein Fehler auf.

Es wird empfohlen, den Azure Information Protection-Client für einheitliche Bezeichnungen bereitzustellen. Wenn Sie noch kein Upgrade durchgeführt haben, ist möglicherweise weiterhin der [klassische Azure Information Protection-Client](./rms-client/aip-client.md) in Ihrem System bereitgestellt. 

Weitere Informationen finden Sie unter [Die Clientseite von Azure Information Protection](rms-client/use-client.md) und [AIP für Windows- und Office-Versionen in erweiterter Unterstützung](known-issues.md#aip-for-windows-and-office-versions-in-extended-support).

> [!NOTE]
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. 
>
> In diesem Zeitraum haben alle aktuellen Azure Information Protection-Kunden die Möglichkeit, zur Microsoft Information Protection-Lösung für einheitliche Bezeichnungen zu wechseln. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

## <a name="support-for-certificate-based-authentication-cba"></a>Unterstützung für die zertifikatbasierte Authentifizierung

Die Azure Information Protection-Apps für iOS und Android unterstützen die zertifikatbasierte Authentifizierung. 

Weitere Informationen finden Sie unter [Erste Schritte mit der zertifikatbasierten Authentifizierung in Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Multi-Factor Authentication (MFA) und Azure Information Protection

Damit Sie die mehrstufige Authentifizierung mit Azure Information Protection verwenden können, ist mindestens eine der folgenden Komponenten erforderlich:

- **Microsoft Office**, Version 2013 oder höher
- **Ein Azure Information Protection-Client**. Es gibt keine Mindestversion. Die Azure Information Protection-Clients für Windows sowie die Viewer-Apps für IOS und Android unterstützen die mehrstufige Authentifizierung.
- **Die Microsoft Rights Management-Freigabeanwendung für Mac-Computer**. Die Microsoft Rights Management-Freigabeanwendung unterstützt seit September 2015 die mehrstufige Authentifizierung.

> [!NOTE]
> Wenn Sie Office 2013 nutzen, müssen Sie möglicherweise ein weiteres Update zur Unterstützung der Active Directory-Authentifizierungsbibliothek (ADAL) installieren, z. B. [das Update für Office 2013 vom 9. Juni 2015 (KB3054853)](https://support.microsoft.com/kb/3054853). 
>
> Weitere Informationen finden Sie im Office-Blogbeitrag zur [Ankündigung der öffentlichen Vorschau der Authentifizierung für Microsoft 2013](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/).       

Führen Sie je nach Mandantenkonfiguration einen der folgenden Schritte aus, nachdem Sie diese Voraussetzungen überprüft haben:

- **Für von Microsoft verwaltete Mandanten mit Azure AD oder Microsoft 365**: Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. 

    Weitere Informationen finden Sie unter 
    - [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud)
    - [Was ist Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication)

- **Für Verbundmandanten, bei denen die Verbundserver lokal ausgeführt werden**: Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Microsoft 365. Wenn Sie beispielsweise AD FS verwenden, finden Sie Informationen unter [Konfigurieren zusätzlicher Authentifizierungsmethoden für AD FS](/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs). 

    Weitere Informationen zu diesem Szenario finden Sie unter [Das Programm „Works with Microsoft 365 – Identity“ wurde optimiert](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) auf dem Office-Blog. 

## <a name="rights-management-connector--aip-scanner-requirements"></a>Anforderungen für den Rights Management-Connector und den Azure Information Protection-Scanner

Der Rights Management-Connector und der Azure Information Protection-Scanner unterstützen die MFA nicht. 

Wenn Sie den Connector oder den Scanner bereitstellen, dürfen die folgenden Konten keine MFA erfordern:

- Das Konto, das den Connector installiert und konfiguriert.
- Das Dienstprinzipalkonto in Azure AD, das der Connector erstellt: **Aadrm_S-1-7-0**.
- Das Dienstkonto, das den Scanner ausführt.

## <a name="user-upn-values-dont-match-their-email-addresses"></a>UPN-Werte von Benutzern stimmen nicht mit deren E-Mail-Adressen überein

Konfigurationen, bei denen die UPN-Werte von Benutzern nicht mit deren E-Mail-Adressen übereinstimmen, sind keine empfohlene Konfiguration und unterstützen das einmalige Anmelden für Azure Information Protection nicht.

Wenn Sie den UPN-Wert nicht ändern können, konfigurieren Sie alternative Anmelde-IDs für Benutzer, und erklären Sie den Benutzern, wie sie sich mit dieser alternativen Anmelde-ID bei Office anmelden können. 

Weitere Informationen finden Sie unter

- [Konfigurieren einer alternativen Anmelde-ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id)
- [Office-Anwendungen fordern in regelmäßigen Abständen zur Eingabe von Anmeldeinformationen für SharePoint, OneDrive und Lync Online auf](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).

> [!TIP]
> Fügen Sie den UPN-Wert des Benutzers als weitere E-Mail-Adresse zum Attribut **proxyAddresses** in Azure AD hinzu, wenn der Domänenname im UPN-Wert eine Domäne ist, die für Ihren Mandanten überprüft wurde. Dadurch kann der Benutzer für Azure Rights Management autorisiert werden, wenn sein UPN-Wert zum Zeitpunkt der Gewährung der Nutzungsrechte festgelegt wird. 

Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

## <a name="authenticating-on-premises-using-ad-fs-or-another-authentication-provider"></a>Lokales Authentifizieren mithilfe von AD FS oder eines anderen Authentifizierungsanbieters

Wenn Sie ein mobiles Gerät oder einen Mac-Computer verwenden, der lokal mithilfe von AD FS oder einem vergleichbaren Authentifizierungsanbieter authentifiziert wird, müssen Sie AD FS mit einer der folgenden Konfigurationen verwenden:

- Mindestens **Windows Server 2012 R2**
- Mit einem alternativen Authentifizierungsanbieter, der das OAuth 2.0-Protokoll unterstützt

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
