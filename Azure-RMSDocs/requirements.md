---
title: Anforderungen an Azure Information Protection – AIP
description: Voraussetzungen für die Bereitstellung von Azure Information Protection für Ihre Organisation.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/16/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: fc76b7da1f687ab9876a6831539bf515df59aea1
ms.sourcegitcommit: 9221a0a9f3862739446b9027931a05023e0d5fc3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/17/2019
ms.locfileid: "68286997"
---
# <a name="requirements-for-azure-information-protection"></a>Anforderungen an Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, müssen die folgenden Voraussetzungen erfüllt sein. 

## <a name="subscription-for-azure-information-protection"></a>Abonnement für Azure Information Protection

**Für Klassifizierung, Bezeichnung und Schutz**: Sie benötigen einen [Azure Information Protection-Plan](https://azure.microsoft.com/pricing/details/information-protection/). 

**Für die reine Schutzfunktion**: Sie benötigen einen [Office 365-Plan, der Azure Information Protection einschließt](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Überprüfen Sie anhand der Abonnementinformationen auf der [Preisseite](https://azure.microsoft.com/pricing/details/information-protection) für Azure Information Protection, ob das Abonnement Ihrer Organisation die gewünschten Azure Information Protection-Features umfasst.

Wenn Sie Fragen zur Lizenzierung haben, lesen Sie die [häufig gestellten Fragen](https://azure.microsoft.com/pricing/details/information-protection#faq) zur Lizenzierung.

> [!TIP]
> Möchten Sie wissen, ob Ihr Office 365-Plan oder eigenständiger Exchange Online-Plan die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) unterstützt, damit geschützte E-Mails an persönliche E-Mail-Adressen gesendet werden können? Beispiele sind Gmail, Yahoo und Microsoft. Weitere Informationen finden Sie in folgenden Ressourcen:
>
> - [Exchange Online-Dienstbeschreibung](https://technet.microsoft.com/library/exchange-online-service-description.aspx)
>
> - [Office 365 Education](https://technet.microsoft.com/library/mt844095.aspx)
>
> - [Office 365 US Government](https://technet.microsoft.com/library/mt774581.aspx)

Wenn Sie Fragen zum Abonnement oder zur Lizenzierung haben, dann stellen Sie diese bitte nicht auf dieser Seite. Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq). Wenden Ihre Frage darin nicht beantwortet wird, wenden Sie sich an Ihren Microsoft-Konto-Manager oder an den [Microsoft-Support](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

Ihre Organisation muss über ein Azure Active Directory-Verzeichnis (Azure AD) verfügen, um die Benutzerauthentifizierung und -autorisierung für Azure Information Protection zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.

Das einmalige Anmelden (Single Sign-On, SSO) wird für Azure Information Protection unterstützt, sodass Benutzer nicht wiederholt zur Angabe ihre Anmeldeinformationen aufgefordert werden. Wenn Sie die Lösung eines anderen Anbieters für den Verbund verwenden, fragen Sie bei dem Anbieter nach, wie die Lösung für Azure AD konfiguriert werden muss. WS-Trust ist eine häufige Anforderung für diese Lösungen zur Unterstützung des einmaligen Anmeldens. 

Multi-Factor Authentication (MFA) wird mit Azure Information Protection unterstützt, wenn die erforderliche Clientsoftware installiert ist und Sie die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.

Bedingter Zugriff wird in der Vorschauversion für Dokumente unterstützt, die mithilfe von Azure Information Protection geschützt sind. Weitere Informationen finden Sie unter den folgenden FAQ: [Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [Azure Active Directory-Anforderungen für Azure Information Protection](requirements-azure-ad.md). 

Weitere Informationen zu den Anforderungen zum Autorisieren von Benutzer- und Gruppenkonten finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

## <a name="client-devices"></a>Clientgeräte

Benutzer müssen Clientgeräte (Computer oder mobile Geräte) verwenden, unter deren Betriebssystem Azure Information Protection unterstützt wird.

Die folgenden Geräte unterstützen den Azure Information Protection Unified-Bezeichnungs Client und den Azure Information Protection-Client. Mit [beiden Clients](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client) können Benutzer Ihre Dokumente und e-Mails klassifizieren und bezeichnen:

- Windows 10 (x86, x64)
    
    - Keine Unterstützung für Handschriften im Windows 10 RS4-Build oder höher. 

- Windows 8.1 (x86, x64)

- Windows 8 (x86, x64)

- Windows 7 Service Pack 1 (x86, x64)

- Windows Server 2016 

- Windows Server 2012 R2 und Windows Server 2012

- Windows Server 2008 R2 

Zusätzlich zur Installation des-Clients auf physischen Computern können Sie ihn auch auf virtuellen Computern installieren. Überprüfen Sie, ob der Softwareanbieter für die virtuelle Desktop Lösung über zusätzliche Konfigurationsfunktionen verfügt, die möglicherweise erforderlich sind, um den Azure Information Protection Unified Bezeichnung-Client oder den Azure Information Protection-Client auszuführen. Beispielsweise müssen Sie für Citrix-Lösungen möglicherweise [Citrix Application Programming Interface (API) Hooks](https://support.citrix.com/article/CTX107825) für Office (Winword. exe, Excel. exe, Outlook. exe, PowerPoint. exe) und die ausführbare Datei für die Azure Information Protection Unified bezeichnen von Client-oder Azure Information Protection Client (MSIP. app. exe, MSIP. Viewer. exe).

Für die aufgelisteten Serverversionen werden die Azure Information Protection-Clients für Remotedesktopdienste unterstützt. Löschen Sie den Ordner **%AppData%\microsoft\protect** nicht, wenn Sie Benutzerprofile löschen, wenn Sie die Azure Information Protection Clients mit Remotedesktopdienste verwenden.

Wenn die Azure Information Protection-Clients die Daten mithilfe des Azure Rights Management-Dienstanbieter schützen, können die Daten von [denselben Geräten](requirements-client-devices.md) genutzt werden, die den Azure Rights Management-Dienst unterstützen.

Die Azure Information Protection Clients verfügen über zusätzliche erforderliche Komponenten, die in den jeweiligen Administrator Handbüchern aufgeführt sind:

- Azure Information Protection-Client für einheitliche Bezeichnungen: [Erforderliche Komponenten](./rms-client/clientv2-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-unified-labeling-client)

- Azure Information Protection-Client: [Erforderliche Komponenten](./rms-client/client-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-client)


## <a name="applications"></a>Applications

Die Azure Information Protection Clients können Dokumente und e-Mails mit den Office-Anwendungen **Word**, **Excel**, **PowerPoint**und **Outlook** aus einer der folgenden Office-Editionen bezeichnen und schützen:

- Mindestversion 1805 von Office-Apps, Build 9330.2078 von Office 365 Business oder Microsoft 365 Business, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.

- Office 365 ProPlus

- Office Professional Plus 2019

- Office Professional Plus 2016

- Office Professional Plus 2013 mit Service Pack 1

- Office Professional Plus 2010 mit Service Pack 2

Andere Office-Suiten können keine Dokumente und E-Mails mithilfe eines Rights Management-Diensts schützen. Für diese Editionen wird Azure Information Protection nur für die Klassifizierung unterstützt. Deshalb werden Bezeichnungen, die Schutz anwenden, nicht in der Leiste für Azure Information Protection oder über die Schaltfläche **Schützen** des Office-Menübands angezeigt. 

Die Azure Information Protection-Clients unterstützen nicht mehrere Office-Versionen auf demselben Computer. Diese Clients unterstützen außerdem nicht das Wechseln von Benutzerkonten in Office.

Informationen dazu, welche Office-Editionen den Datenschutzdienst unterstützen, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-applications.md).

## <a name="firewalls-and-network-infrastructure"></a>Firewalls und Netzwerkinfrastruktur

Wenn Sie eine Firewall oder ähnliche Interventionsnetzwerkgeräte verwenden, die so konfiguriert wurden, dass bestimmte Verbindungen erlaubt sind, sind die Netzwerkanforderungen im Office-Artikel [Office 365-URLs und IP-Adressbereiche](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) enthalten. Weitere Informationen finden Sie im Abschnitt **Microsoft 365 Common and Office Online (Microsoft 365 Common und Office Online)** .

Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure Information Protection:

- Damit der Unified Label-Client Bezeichnungen und Bezeichnungs Richtlinien herunterlädt: Lassen Sie die URL * **. Protection.Outlook.com** über HTTPS zu.

- Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.

- Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene) zur URL **aadrm.com**. Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um deren Kommunikation mit dem Azure Rights Management-Dienst zu sichern.
    
    - Tipp: Aufgrund der Darstellungsweise von sicheren Verbindungen in der Adressleiste von Chrome können Sie diesen Browser verwenden, um schnell zu überprüfen, ob Ihre Clientverbindung beendet wird, bevor diese den Azure Rights Management-Dienst erreicht. Geben Sie folgende URL in die Adressleiste des Browsers ein: `https://admin.na.aadrm.com/admin/admin.svc` 
    
        Beachten Sie die im Browserfenster angezeigten Inhalte nicht. Klicken Sie stattdessen auf das Schloss in der Adressleiste, um die Websiteinformationen anzuzeigen. In den Websiteinformationen wird Ihnen die ausstellende Zertifizierungsstelle angezeigt. Wenn das Zertifikat nicht von einer Microsoft-Zertifizierungsstelle ausgestellt wird, ist es wahrscheinlich, dass Ihre sichere Client-zu-Dienst-Verbindung beendet wurde und in Ihrer Firewall neu konfiguriert werden muss. In der folgenden Abbildung wird ein Beispiel für eine ausstellende Zertifizierungsstelle von Microsoft dargestellt. Wenn Sie feststellen, dass das Zertifikat von einer internen Zertifizierungsstelle ausgestellt wurde, ist diese Konfiguration nicht mit Azure Information Protection kompatibel.
        
        ![Überprüfen des ausgestellten Zertifikats für Azure Information Protection-Verbindungen](./media/certificate-checking.png)

### <a name="on-premises-servers"></a>Lokale Server

Wenn Sie den Azure Rights Management-Dienst von Azure Information Protection auf lokalen Servern verwenden möchten, werden folgende Produkte unterstützt:

- Exchange Server

- SharePoint Server

- Windows Server-Dateiserver, die die Dateiklassifizierungsinfrastruktur unterstützen.

Informationen zu den zusätzlichen Anforderungen für dieses Szenario finden Sie unter [Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-servers.md).

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Gleichzeitige Verwendung von AD RMS mit Azure RMS

Das folgende Bereitstellungsszenario wird nur unterstützt, wenn Sie AD RMS für [HYOK-Schutz](configure-adrms-restrictions.md) mit Azure Information Protection verwenden (Hold Your Own Key-Konfiguration):

- Parallele Ausführung von AD RMS und Azure RMS in derselben Organisation (mit Ausnahme der Migration), wie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) beschrieben.

Es gibt einen unterstützten Migrationspfad [von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) und [von Azure Information Protection zu AD RMS](/powershell/module/aipservice/Set-AipServiceMigrationUrl). Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](decommission-deactivate.md).

