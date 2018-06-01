---
title: Anforderungen an Azure Information Protection
description: Voraussetzungen für die Bereitstellung von Azure Information Protection für Ihre Organisation.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/18/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9cdb205488c300f1df1e002be105765a90ce1a1a
ms.sourcegitcommit: 09072591f1aa9878d063feb78ffcc4accec63fd1
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/18/2018
ms.locfileid: "34308170"
---
# <a name="requirements-for-azure-information-protection"></a>Anforderungen an Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Damit Sie Azure Information Protection für Ihre Organisation bereitstellen können, müssen die folgenden Voraussetzungen erfüllt sein. 

## <a name="subscription-for-azure-information-protection"></a>Abonnement für Azure Information Protection

**Zur Klassifizierung, zur Bezeichnung und zum Schutz:** Sie benötigen einen [Azure Information Protection-Plan](https://azure.microsoft.com/pricing/details/information-protection/). 

**Für die reine Schutzfunktion:** Sie müssen über einen [Office 365-Plan verfügen, der Azure Information Protection einschließt](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Überprüfen Sie anhand der Abonnementinformationen auf der [Preisseite](https://azure.microsoft.com/pricing/details/information-protection) für Azure Information Protection, ob das Abonnement Ihrer Organisation die gewünschten Azure Information Protection-Features umfasst.

> [!TIP]
> Möchten Sie wissen, ob Ihr Office 365-Plan oder eigenständiger Exchange Online-Plan die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) unterstützt, damit geschützte E-Mails an persönliche E-Mail-Adressen gesendet werden können? Beispiele sind Gmail, Yahoo und Microsoft. Weitere Informationen finden Sie in folgenden Ressourcen:
>
> [Exchange Online-Dienstbeschreibung](https://technet.microsoft.com/library/exchange-online-service-description.aspx)
>
> [Office 365 Education](https://technet.microsoft.com/library/mt844095.aspx)
>
> [Office 365 US Government](https://technet.microsoft.com/library/mt774581.aspx)

Wenn Sie Fragen zu Abonnements oder zur Lizenzierung haben, veröffentlichen Sie sie nicht auf dieser Seite, sondern wenden Sie sich an Ihren Microsoft-Kundenbetreuer oder an den [Microsoft-Support](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

Ihre Organisation muss über ein Azure Active Directory-Verzeichnis (Azure AD) verfügen, um die Benutzerauthentifizierung und -autorisierung für Azure Information Protection zu unterstützen. Zusätzlich müssen Sie, wenn Sie Ihre Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, auch die Verzeichnisintegration konfigurieren.

Das einmalige Anmelden (Single Sign-On, SSO) wird für Azure Information Protection unterstützt, sodass Benutzer nicht wiederholt zur Angabe ihre Anmeldeinformationen aufgefordert werden. Wenn Sie die Lösung eines anderen Anbieters für den Verbund verwenden, fragen Sie bei dem Anbieter nach, wie die Lösung für Azure AD konfiguriert werden muss. WS-Trust ist eine häufige Anforderung für diese Lösungen zur Unterstützung des einmaligen Anmeldens. 

Multi-Factor Authentication (MFA) wird mit Azure Information Protection unterstützt, wenn die erforderliche Clientsoftware installiert ist und Sie die für MFA erforderliche unterstützende Infrastruktur richtig konfiguriert haben.

Bedingter Zugriff wird in der Vorschauversion für Dokumente unterstützt, die mithilfe von Azure Information Protection geschützt sind. Weitere Informationen finden Sie in den folgenden häufig gestellten Fragen (FAQ): [Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Weitere Informationen zu Authentifizierungsanforderungen finden Sie unter [Azure Active Directory-Anforderungen für Azure Information Protection](requirements-azure-ad.md). 

Weitere Informationen zu den Anforderungen zum Autorisieren von Benutzer- und Gruppenkonten finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](../plan-design/prepare.md).

## <a name="client-devices"></a>Clientgeräte

Benutzer müssen Clientgeräte (Computer oder mobile Geräte) verwenden, unter deren Betriebssystem Azure Information Protection unterstützt wird.

Die folgenden Geräte unterstützen den Azure Information Protection-Client, mit dem Benutzer ihre Dokumente und E-Mails klassifizieren und bezeichnen können:

- Windows 10 (x86, x64)
    
    - Keine Unterstützung für Handschriften im Windows 10 RS4-Build für Insider 

- Windows 8.1 (x86, x64)

- Windows 8 (x86, x64)

- Windows 7 Service Pack 1 (x86, x64)

- Windows Server 2016 

- Windows Server 2012 R2 und Windows Server 2012

- Windows Server 2008 R2 

Für die aufgelisteten Serverversionen wird der Azure Information Protection-Client für Remotedesktopdienste unterstützt. Wenn Sie bei der Verwendung des Azure Information Protection-Clients mit den Remotedesktopdiensten Benutzerprofile löschen, löschen Sie nicht den Ordner **%Appdata%\Microsoft\Protect**.

Wenn durch den Azure Information Protection-Client Daten mit dem Azure Rights Management-Dienst geschützt werden, können die Daten von den [gleichen Geräten](requirements-client-devices.md) genutzt werden, die auch den Azure Rights Management-Dienst unterstützen.

## <a name="applications"></a>Applications

Der Azure Information Protection-Client kann Dokumente und E-Mails bezeichnen und schützen, indem er die Office-Anwendungen **Word**, **Excel**, **PowerPoint** und **Outlook** aus einer der folgenden Office-Suiten verwendet:

- Office 365 ProPlus mit 2016-Apps oder 2013-Apps (Klick-und-Los- oder Windows Installer-basierte Installation)
    
    Diese Editionen von Office sind in den meisten Office 365-Abonnements enthalten, bei denen durch Azure Information Protection Datenschutz gewährleistet wird. Überprüfen Sie Ihre Abonnementinformationen, um zu sehen, ob Office 365 ProPlus enthalten ist. Sie finden diese Informationen auch im [Datenblatt zu Azure Information Protection](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

- Office Professional Plus 2016

- Office Professional Plus 2013 mit Service Pack 1

- Office Professional Plus 2010 mit Service Pack 2

Andere Office-Suiten können keine Dokumente und E-Mails mithilfe eines Rights Management-Diensts schützen. Für diese Editionen wird Azure Information Protection nur für die Klassifizierung unterstützt. Deshalb werden Bezeichnungen, die Schutz anwenden, nicht in der Leiste für Azure Information Protection oder über die Schaltfläche **Schützen** des Office-Menübands angezeigt. 

Der Azure Information Protection-Client unterstützt nur Computer, auf denen nur eine Office-Version installiert ist. Außerdem unterstützt der Client nicht das Wechseln zwischen mehreren Benutzerkonten in Office.

Informationen dazu, welche Office-Editionen den Datenschutzdienst unterstützen, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-applications.md).

## <a name="firewalls-and-network-infrastructure"></a>Firewalls und Netzwerkinfrastruktur

Wenn Sie eine Firewall oder ähnliche zwischengeschaltete Netzwerkgeräte nutzen, die konfiguriert werden, um bestimmte Verbindungen zu erlauben, lesen Sie die Informationen zu **Azure Rights Management (RMS)** im Abschnitt [Office 365-Portal und gemeinsame Dienste](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&rs=en-US&ad=US#bkmk_portal-identity) aus dem folgenden Office-Artikel: [URLs und IP-Adressbereiche von Office 365](https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2).

Verwenden Sie die Anleitungen in diesem Office-Artikel, um bei Änderungen an diesen Informationen mithilfe eines RSS-Feed-Abonnements auf dem neuesten Stand zu bleiben.

Zusätzlich zu den Informationen im Office-Artikel, spezifisch für Azure Information Protection:

- Lassen Sie auf TCP 443 HTTPS-Datenverkehr zu **api.informationprotection.azure.com** zu.

- Lassen Sie auf TCP 443 HTTPS-Datenverkehr zu **mobile.pipe.aria.microsoft.com** zu.

- Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.

- Beenden Sie nicht die TLS-Client-zu-Dienst-Verbindung (z.B. zur Durchführung von Überprüfungen auf Paketebene) zum Azure Rights Management-Dienst. Wenn Sie dies tun, wird die Anheftung von Zertifikaten unterbrochen, die RMS-Clients mit von Microsoft verwalteten Zertifizierungsstellen verwenden, um deren Kommunikation mit dem Azure Rights Management-Dienst zu sichern.
    
    - Tipp: Aufgrund der Darstellungsweise von sicheren Verbindungen in der Adressleiste von Chrome können Sie diesen Browser verwenden, um schnell zu überprüfen, ob Ihre Clientverbindung beendet wird, bevor diese den Azure Rights Management-Dienst erreicht. Geben Sie folgende URL in die Adressleiste des Browsers ein: `https://admin.na.aadrm.com/admin/admin.svc` 
    
        Beachten Sie die im Browserfenster angezeigten Inhalte nicht. Klicken Sie stattdessen auf das Schloss in der Adressleiste, um die Websiteinformationen anzuzeigen. In den Websiteinformationen wird Ihnen die ausstellende Zertifizierungsstelle angezeigt. Wenn das Zertifikat nicht von einer Microsoft-Zertifizierungsstelle ausgestellt wird, ist es wahrscheinlich, dass Ihre sichere Client-zu-Dienst-Verbindung beendet wurde und in Ihrer Firewall neu konfiguriert werden muss. In der folgenden Abbildung wird ein Beispiel für eine ausstellende Zertifizierungsstelle von Microsoft dargestellt. Wenn Sie feststellen, dass das Zertifikat von einer internen Zertifizierungsstelle ausgestellt wurde, ist diese Konfiguration nicht mit Azure Information Protection kompatibel.
        
        ![Überprüfen des ausgestellten Zertifikats für Azure Information Protection-Verbindungen](../media/certificate-checking.png)

### <a name="on-premises-servers"></a>Lokale Server

Wenn Sie den Azure Rights Management-Dienst von Azure Information Protection auf lokalen Servern verwenden möchten, werden folgende Produkte unterstützt:

- Exchange Server

- SharePoint Server

- Windows Server-Dateiserver, die die Dateiklassifizierungsinfrastruktur unterstützen.

Informationen zu den zusätzlichen Anforderungen für dieses Szenario finden Sie unter [Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-servers.md).

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Gleichzeitige Verwendung von AD RMS mit Azure RMS

Das folgende Bereitstellungsszenario wird nur unterstützt, wenn Sie AD RMS für [HYOK-Schutz](../deploy-use/configure-adrms-restrictions.md) mit Azure Information Protection verwenden (Hold Your Own Key-Konfiguration):

- Parallele Ausführung von AD RMS und Azure RMS in derselben Organisation (mit Ausnahme der Migration), wie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) beschrieben.

Es gibt einen unterstützten Migrationspfad [von AD RMS zu Azure Information Protection](http://technet.microsoft.com/library/Dn858447.aspx) und [von Azure Information Protection zu AD RMS](/powershell/module/aadrm/Set-AadrmMigrationUrl). Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](../deploy-use/decommission-deactivate.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


