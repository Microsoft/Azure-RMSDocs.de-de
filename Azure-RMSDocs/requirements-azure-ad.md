---
title: Zusätzliche Voraussetzungen für Azure AD und Azure Information Protection
description: Informieren Sie sich über zusätzliche Azure AD Voraussetzungen für Azure Information Protection in bestimmten Szenarien, z. b. Multi-Factor-oder Zertifikat basierte Authentifizierung oder Computer mit Office 2010 und mehr.
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
ms.openlocfilehash: b23afa0975f5d8f353b3ed8a5d4cf5332712f3b7
ms.sourcegitcommit: d1f6f10c9cb95de535d8121e90b211f421825caf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87298188"
---
# <a name="additional-azure-ad-requirements-for-azure-information-protection"></a>Zusätzliche Azure AD Anforderungen für Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Ein [Azure AD Verzeichnis ist eine Voraussetzung](requirements.md#azure-active-directory) für die Verwendung von Azure Information Protection. Verwenden Sie ein Konto aus einem Azure AD Verzeichnis, um sich beim Azure-Portal anzumelden, in dem Sie Azure Information Protection Einstellungen konfigurieren können.

Wenn Sie ein Abonnement mit Azure Information Protection oder Azure Rights Management besitzen, wird Ihr Azure AD-Verzeichnis bei Bedarf automatisch für Sie erstellt.

In den folgenden Abschnitten werden zusätzliche AIP-und Azure AD Anforderungen für bestimmte Szenarien aufgelistet. 

## <a name="computers-running-office-2010"></a>Computer mit Office 2010

Zusätzlich zu Azure AD Konto müssen für Computer, auf denen Microsoft Office 2010 ausgeführt wird, der [Azure Information Protection Unified](./rms-client/aip-clientv2.md) -Bezeichnungs Client oder [Azure Information Protection klassischer Client](./rms-client/aip-client.md) für Azure Information Protection und den zugehörigen Datenschutz Dienst (Azure Rights Management) authentifiziert werden.

Wenn Ihre Benutzerkonten einen Verbund haben (z. b. Wenn Sie AD FS verwenden), muss auf diesen Computern die integrierte Windows-Authentifizierung verwendet werden. Bei der formularbasierten Authentifizierung tritt in diesem Szenario beim Authentifizieren von Benutzern für Azure Information Protection ein Fehler auf.

## <a name="support-for-certificate-based-authentication-cba"></a>Unterstützung für Zertifikat basierte Authentifizierung (Certificate-Based Authentication, CBA)

Die Azure Information Protection-Apps für iOS und Android unterstützen die zertifikatbasierte Authentifizierung. 

Weitere Informationen finden Sie unter [Get Started with Certificate-Based Authentication in Azure Active Directory](/azure/active-directory/active-directory-certificate-based-authentication-get-started).

## <a name="multi-factor-authentication-mfa-and-azure-information-protection"></a>Multi-Factor Authentication (MFA) und Azure Information Protection

Wenn Sie die mehrstufige Authentifizierung (Multi-Factor Authentication, MFA) mit Azure Information Protection verwenden möchten, müssen Sie mindestens eine der folgenden Geräte installiert haben:

- **Microsoft Office,** Version 2013 oder höher
- **Ein AIP-Client**. Es ist keine Mindestversion erforderlich. Die AIP-Clients für Windows sowie die Viewer-Apps für IOS und Android unterstützen MFA.
- **Die Rights Management Freigabe-App für**Macintosh-Computer. Die RMS-Freigabe-apps haben seit der Version vom September 2015 MFA unterstützt.

> [!NOTE]
> Wenn Sie über Office 2013 verfügen, müssen Sie möglicherweise ein zusätzliches Update installieren, um Active Directory-Authentifizierungsbibliothek (Adal) zu unterstützen, z. b. das [Update vom 9. Juni 2015, für Office 2013 (KB3054853)](https://support.microsoft.com/kb/3054853). 
>
> Weitere Informationen finden Sie unter [Office 2013 modern Authentication Public Preview, angekündigt](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) im Office-Blog.       

Nachdem Sie diese Voraussetzungen bestätigt haben, führen Sie je nach Mandanten Konfiguration einen der folgenden Schritte aus:

- **Von Microsoft verwaltete Mandanten mit Azure AD oder Office 365**. Konfigurieren Sie Azure MFA, um MFA für Benutzer zu erzwingen. 

    Weitere Informationen finden Sie unter 
    - [Erste Schritte mit Azure Multi-Factor Authentication in der Cloud](/multi-factor-authentication/multi-factor-authentication-get-started-cloud)
    - [Was ist Azure Multi-Factor Authentication?](/multi-factor-authentication/multi-factor-authentication)

- **Verbund Mandanten, in denen Verbund Server lokal ausgeführt werden**. Konfigurieren Sie Ihre Verbundserver für Azure Active Directory oder Office 365. Wenn Sie z. b. AD FS verwenden, finden Sie weitere Informationen unter [Konfigurieren zusätzlicher Authentifizierungsmethoden für AD FS](/windows-server/identity/ad-fs/operations/configure-additional-authentication-methods-for-ad-fs). 

    Weitere Informationen zu diesem Szenario finden Sie im Office-Blog [unter Works with Office 365 – Identity Program](https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/) . 

## <a name="rights-management-connector--aip-scanner-requirements"></a>Rights Management Connector/AIP-Scanner-Anforderungen

Der Rights Management-Connector und der Azure Information Protection-Scanner unterstützen die MFA nicht. 

Wenn Sie den Connector oder den Scanner bereitstellen, dürfen die folgenden Konten keine MFA erfordern:

- Das Konto, das den Connector installiert und konfiguriert.
- Das Dienstprinzipalkonto in Azure AD, das der Connector erstellt: **Aadrm_S-1-7-0**.
- Das Dienstkonto, das den Scanner ausführt.

## <a name="user-upn-values-dont-match-their-email-addresses"></a>Benutzer-UPN-Werte stimmen nicht mit Ihren e-Mail

Konfigurationen, bei denen die UPN-Werte von Benutzern nicht mit Ihren e-Mail-Adressen identisch sind, sind keine empfohlene Konfiguration und unterstützen das einmalige Anmelden für Azure Information Protection nicht.

Wenn Sie den UPN-Wert nicht ändern können, konfigurieren Sie alternative IDs für die relevanten Benutzer, und weisen Sie Sie an, wie Sie sich mit dieser alternativen ID bei Office anmelden. 

Weitere Informationen finden Sie unter

- [Konfigurieren einer alternativen Anmelde-ID](/windows-server/identity/ad-fs/operations/configuring-alternate-login-id)
- [Office-Anwendungen fordern regelmäßig Anmelde Informationen für SharePoint, onedrive und lync Online an](https://support.microsoft.com/help/2913639/office-applications-periodically-prompt-for-credentials-to-sharepoint-online,-onedrive,-and-lync-online).

> [!TIP]
> Wenn der Domänen Name im UPN-Wert eine Domäne ist, die für Ihren Mandanten überprüft wurde, fügen Sie den UPN-Wert des Benutzers als weitere e-Mail-Adresse zum Azure AD **proxyAddress** -Attribut hinzu. Dadurch kann der Benutzer für Azure Rights Management autorisiert werden, wenn der UPN-Wert zu dem Zeitpunkt angegeben wird, zu dem die Nutzungsrechte erteilt werden. 

Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

## <a name="authenticating-on-premises-using-adfs-or-another-authentication-provider"></a>Lokales authentifizieren mithilfe AD FS oder eines anderen Authentifizierungs Anbieters

Wenn Sie ein mobiles Gerät oder einen Mac-Computer verwenden, der lokal mithilfe von AD FS oder einem äquivalenten Authentifizierungs Anbieter authentifiziert wird, müssen Sie AD FS für eine der folgenden Konfigurationen verwenden:

- Eine minimale Server Version von **Windows Server 2012 R2**
- Ein alternativer Authentifizierungs Anbieter, der das OAuth 2,0-Protokoll unterstützt.

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
