---
title: Anforderungen an Azure Information Protection – AIP
description: Identifizieren Sie die Voraussetzungen für die Bereitstellung von Azure Information Protection in Ihrer Organisation.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/04/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: a87c83afd6e1747a2fc3db6a12ef8734ff445c77
ms.sourcegitcommit: 2cb5fa2a8758c916da8265ae53dfb35112c41861
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/27/2020
ms.locfileid: "88952826"
---
# <a name="azure-information-protection-requirements"></a>Azure Information Protection Anforderungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Vergewissern Sie sich vor dem Bereitstellen von Azure Information Protection, dass Ihr System die folgenden Voraussetzungen erfüllt:

- [Abonnement für Azure Information Protection](#subscription-for-azure-information-protection)
- [Azure Active Directory](#azure-active-directory)
- [Clientgeräte](#client-devices)
- [Anwendungen](#applications)
- [Firewalls und Netzwerkinfrastruktur](#firewalls-and-network-infrastructure)

## <a name="subscription-for-azure-information-protection"></a>Abonnement für Azure Information Protection

Abhängig von den Azure Information Protection Features, die Sie verwenden werden, benötigen Sie eine der folgenden Funktionen:

- **Ein [Azure Information Protection Plan](https://azure.microsoft.com/pricing/details/information-protection/)**. Erforderlich für Klassifizierung, Bezeichnung und Schutz mithilfe der Azure Information Protection Scanner oder Client (klassisch oder vereinheitlichte Bezeichnung)

- **Ein [Office 365-Plan, der Azure Information Protection enthält](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)**. Nur für den Schutz erforderlich.

Um zu überprüfen, ob Ihr Abonnement die Azure Information Protection Features enthält, die Sie verwenden möchten, überprüfen Sie die Featureliste unter [Azure Information Protection Preise](https://azure.microsoft.com/pricing/details/information-protection).

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

Um die Authentifizierung und Autorisierung für Azure Information Protection zu unterstützen, müssen Sie über eine Azure Active Directory (AD) verfügen. Um Benutzerkonten von Ihrem lokalen Director (AD DS) zu verwenden, müssen Sie auch die Verzeichnisintegration konfigurieren.

- **Einmaliges Anmelden (Single Sign-on, SSO)** wird für Azure Information Protection unterstützt, sodass Benutzer nicht wiederholt zur Eingabe Ihrer Anmelde Informationen aufgefordert werden. Wenn Sie eine andere Anbieter Lösung für den Verbund verwenden, wenden Sie sich an diesen Anbieter, um ihn für Azure AD zu konfigurieren. WS-Trust ist eine häufige Anforderung für diese Lösungen zur Unterstützung des einmaligen Anmeldens. 

- Die **mehrstufige Authentifizierung (Multi-Factor Authentication, MFA)** wird mit Azure Information Protection unterstützt, wenn Sie über die erforderliche Client Software verfügen und die MFA-unterstützende Infrastruktur ordnungsgemäß konfiguriert haben.

Bedingter Zugriff wird in der Vorschauversion für Dokumente unterstützt, die mithilfe von Azure Information Protection geschützt sind. Weitere Informationen finden Sie unter: [Azure Information Protection wird als verfügbare Cloud-App für den bedingten Zugriff aufgeführt – wie funktioniert das?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Zusätzliche Voraussetzungen sind für bestimmte Szenarien erforderlich, z. b. bei Verwendung von Office 2010, Zertifikat basierte oder mehrstufige Authentifizierung, oder wenn UPN-Werte nicht mit Benutzer-e-Mail-Adressen identisch sind. Weitere Informationen finden Sie unter [zusätzliche Azure AD Anforderungen für Azure Information Protection](requirements-azure-ad.md).

Weitere Informationen finden Sie unter

- [Was ist ein Azure AD-Verzeichnis?](/azure/active-directory/fundamentals/active-directory-whatis)
- [Integrieren lokaler Active Directory-Domänen in Azure Active Directory](/azure/architecture/reference-architectures/identity/azure-ad).

## <a name="client-devices"></a>Clientgeräte

Benutzer Computer oder mobile Geräte müssen unter einem Betriebssystem ausgeführt werden, das Azure Information Protection unterstützt.

- [Unterstützte Betriebssysteme für Client Geräte](#supported-operating-systems-for-client-devices)
- [Virtuelle Computer](#virtual-machines)
- [Serverunterstützung](#server-support)
- [Zusätzliche Anforderungen pro Client](#additional-requirements-per-client)

### <a name="supported-operating-systems-for-client-devices"></a>Unterstützte Betriebssysteme für Client Geräte

Die folgenden Betriebssysteme unterstützen die Azure Information Protection Unified-Bezeichnung und die Azure Information Protection-Clients: 

- **Windows 10** (x86, x64). Das Handschrift wird in Windows 10 RS4 Build und höher nicht unterstützt.
 
- **Windows 8.1** (x86, x64)

- **Windows 8** (x86, x64)

- **Windows Server 2019**

- **Windows Server 2016**

- **Windows Server 2012 R2** und **Windows Server 2012**

Mit [beiden Clients](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients) können Benutzer Ihre Dokumente und e-Mails klassifizieren und bezeichnen.

Weitere Informationen zur Unterstützung früherer Windows-Versionen erhalten Sie von Ihrem Microsoft-Konto oder Supportmitarbeiter.

> [!NOTE]
> Wenn die Azure Information Protection-Clients die Daten mithilfe des Azure Rights Management-Dienstanbieter schützen, können die Daten von [denselben Geräten](#client-devices) genutzt werden, die den Azure Rights Management-Dienst unterstützen.
>

### <a name="virtual-machines"></a>Virtuelle Computer
Wenn Sie mit virtuellen Computern arbeiten, überprüfen Sie, ob der Softwareanbieter für Ihre virtuelle Desktop Lösung als zusätzliche Konfigurationen für die Ausführung der Azure Information Protection Unified-Bezeichnung oder des Azure Information Protection-Clients erforderlich ist. 

Beispielsweise müssen Sie für Citrix-Lösungen möglicherweise [Citrix Application Programming Interface (API) Hooks](https://support.citrix.com/article/CTX107825) für Office, den Azure Information Protection Unified-Bezeichnungs Client oder den Azure Information Protection-Client deaktivieren. 

Diese Anwendungen verwenden die folgenden Dateien: **winword.exe**, **excel.exe**, **outlook.exe**, **powerpnt.exe**, **msip.app.exe**, **msip.viewer.exe**

### <a name="server-support"></a>Serverunterstützung

Für jede der oben aufgeführten Serverversionen werden Azure Information Protection Clients für Remotedesktopdienste unterstützt. 

Löschen Sie den Ordner **%AppData%\microsoft\protect** nicht, wenn Sie Benutzerprofile löschen, wenn Sie die Azure Information Protection Clients mit Remotedesktopdienste verwenden.

Außerdem werden Server Core und Nano Server nicht unterstützt.

### <a name="additional-requirements-per-client"></a>Zusätzliche Anforderungen pro Client

Für jeden Azure Information Protection Client gelten zusätzliche Voraussetzungen. Einzelheiten dazu finden Sie unter:

- [Azure Information Protection vereinheitlichte Client Voraussetzungen](./rms-client/clientv2-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-unified-labeling-client)

- [Azure Information Protection Client Voraussetzungen](./rms-client/client-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-client)

## <a name="applications"></a>Anwendungen

Die Azure Information Protection Clients können Dokumente und e-Mails mithilfe von Microsoft **Word**, **Excel**, **PowerPoint**und **Outlook** aus einer der folgenden Office-Editionen bezeichnen und schützen:

- **Office-Apps, Mindestversion 1805**, Build 9330,2078 aus Office 365 Business oder Microsoft 365 Business. 

    Diese Edition wird nur unterstützt, wenn dem Benutzer eine Lizenz für Azure Rights Management zugewiesen ist, auch bekannt als Azure Information Protection für Office 365.

- **Office 365 ProPlus**

- **Office Professional Plus 2019**

- **Office Professional Plus 2016**

- **Office Professional Plus 2013 mit Service Pack 1**

- **Office Professional Plus 2010 mit Service Pack 2**

Andere Office-Suiten können keine Dokumente und E-Mails mithilfe eines Rights Management-Diensts schützen. Für diese Editionen wird Azure Information Protection nur für die Klassifizierung unterstützt, und Bezeichnungen, die Schutz anwenden, werden für Benutzer nicht angezeigt. 

Diese Bezeichnungen würden andernfalls auf der Azure Information Protection Leiste oder im Unified Label-Client im Office-Menüband angezeigt (über die Schaltfläche **schützen** auf dem klassischen Client oder über **die Schaltfläche** "Vertraulichkeit" im Unified Label-Client). 

Weitere Informationen finden Sie [unter Anwendungen, die Azure Rights Management Datenschutz unterstützen](requirements-applications.md).

### <a name="office-features-and-capabilities-not-supported"></a>Office-Features und-Funktionen werden nicht unterstützt

- Die Azure Information Protection Clients, einschließlich der klassischen und einheitlichen Bezeichnung, unterstützen nicht mehrere Office-Versionen auf demselben Computer oder das Wechseln von Benutzerkonten in Office.

- Das Feature für die Office-e- [Mail](https://support.office.com/article/use-mail-merge-for-bulk-email-letters-labels-and-envelopes-f488ed5b-b849-4c11-9cff-932c49474705) -Zusammenführung wird von keiner Azure Information Protection Funktion unterstützt

## <a name="firewalls-and-network-infrastructure"></a>Firewalls und Netzwerkinfrastruktur

Wenn Sie über eine Firewall oder ähnliche zwischengeschaltete Netzwerkgeräte verfügen, die so konfiguriert sind, dass Sie bestimmte Verbindungen zulässt, sind die Anforderungen an die Netzwerk Konnektivität in diesem Office-Artikel aufgeführt: [Office 365-URLs und IP-Adressbereiche > Microsoft 365 Common und Office Online](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online).

Azure Information Protection hat die folgenden zusätzlichen Anforderungen:

- **Einheitlicher**Bezeichnungs Client. Zum Herunterladen von Bezeichnungen und Bezeichnungs Richtlinien lassen Sie die folgende URL über HTTPS zu: ***. Protection.Outlook.com**

- **Webproxys**. Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie den Proxy so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Anmelde Informationen des Active Directory Anmelde Informationen des Benutzers verwendet.

    
- **TLS-Client-zu-Dienst-Verbindungen**. Beenden Sie keine TLS-Client-zu-Dienst-Verbindungen, z. b. zur Durchführung der Überprüfung auf Paketebene, für die **aadrm.com** -URL. Ansonsten wird die Anheftung von Zertifikaten beendet, die von RMS-Clients für von Microsoft verwaltete Zertifizierungsstellen verwendet wird, um die Kommunikation mit dem Azure Rights Management-Dienst zu schützen.
     
    Verwenden Sie die folgenden PowerShell-Befehle, um zu bestimmen, ob Ihre Client Verbindung beendet wurde, bevor Sie den Azure Rights Management-Dienst erreicht:

    ```ps
    $request = [System.Net.HttpWebRequest]::Create("https://admin.na.aadrm.com/admin/admin.svc")
    $request.GetResponse()
    $request.ServicePoint.Certificate.Issuer
    ```

    Das Ergebnis sollte anzeigen, dass die ausstellende Zertifizierungsstelle von einer Microsoft-Zertifizierungsstelle aus ist, beispielsweise: `CN=Microsoft Secure Server CA 2011, O=Microsoft Corporation, L=Redmond, S=Washington, C=US` . 
    
    Wenn Sie einen ausstellenden Zertifizierungsstellen Namen sehen, der nicht von Microsoft abhängt, ist es wahrscheinlich, dass Ihre sichere Client-zu-Dienst-Verbindung beendet wird und eine Neukonfiguration der Firewall erforderlich ist.

- **TLS-Version 1,2 oder höher** (einheitlicher Bezeichnungs Client). Der Unified-Bezeichnungs Client erfordert eine TLS-Version von 1,2 oder höher, um die Verwendung kryptografisch sicherer Protokolle sicherzustellen und den Sicherheitsrichtlinien von Microsoft auszurichten.

### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Gleichzeitige Verwendung von AD RMS mit Azure RMS

Die Verwendung von AD RMS und Azure RMS nebeneinander in derselben Organisation, um Inhalte durch denselben Benutzer in derselben Organisation zu schützen, wird **nur** in AD RMS für den [Hyok-Schutz (Hold Your Own Key)](configure-adrms-restrictions.md) mit Azure Information Protection unterstützt.

Dieses Szenario wird bei der [Migration](migrate-from-ad-rms-to-azure-rms.md) *nicht* unterstützt.
Zu den unterstützten Migrations Pfaden gehören:

* [Von AD RMS bis Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)

* [Von Azure Information Protection bis AD RMS](/powershell/module/aipservice/Set-AipServiceMigrationUrl)

> [!TIP]
> Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](decommission-deactivate.md).

Für andere Szenarien ohne Migration, bei denen beide Dienste in derselben Organisation aktiv sind, müssen beide Dienste so konfiguriert werden, dass nur einer der Benutzerinhalte schützen kann. Konfigurieren Sie solche Szenarien wie folgt:

* Verwenden von Umleitungen für eine [AD RMS zum Azure RMS der Migration](migrate-from-ad-rms-to-azure-rms.md)

* Wenn beide Dienste gleichzeitig für verschiedene Benutzer aktiv sein müssen, verwenden Sie Dienst seitige Konfigurationen, um die Exklusivität zu erzwingen.  Verwenden **Sie** die Azure RMS onboardingsteuerelemente im clouddienst und eine ACL für die Veröffentlichungs-URL, um den schreibgeschützten Modus für AD RMS festzulegen.

### <a name="service-tags"></a>Diensttags

Stellen Sie sicher, dass Sie den Zugriff auf alle Ports für die folgenden Dienst Tags zulassen:

- **AzureInformationProtection**
- **AzureActiveDirectory**
- **AzureFrontDoor.Frontend**

Der Azure Information Protection-Dienst ist auch von zwei bestimmten IP-Adressen abhängig:
 - **13.107.6.181** 
 - **13.107.9.181**

Stellen Sie sicher, dass Sie Regeln erstellen, die den ausgehenden Zugriff auf diese spezifischen IP-Adressen zulassen.

## <a name="supported-on-premises-servers-for-azure-rights-management-data-protection"></a>Unterstützte lokale Server für den Schutz von Daten in Azure Rights Management

Die folgenden lokalen Server werden mit Azure Information Protection unterstützt, wenn Sie den Azure Rights Management-Connector verwenden.

Dieser Connector fungiert als Kommunikationsschnittstelle und Relays zwischen lokalen Servern und dem Azure Rights Management-Dienst, der von Azure Information Protection verwendet wird, um Office-Dokumente und e-Mails zu schützen. 

Für die Verwendung des Connectors müssen Sie die Verzeichnissynchronisierung zwischen Ihren Active Directory-Gesamtstrukturen und Azure Active Directory konfigurieren.

Folgende Server werden unterstützt:

|Servertyp  |Unterstützte Versionen  |
|---------|---------|
|**Exchange Server**     | -Exchange Server 2016 </br>-Exchange Server 2013 </br>-Exchange Server 2010       |
|**Office SharePoint Server**     |-Office SharePoint Server 2016 </br>-Office SharePoint Server 2013 </br>-Office SharePoint Server 2010         |
|**Dateiserver, die unter Windows Server ausgeführt werden und die Datei Klassifizierungs Infrastruktur (FCI) verwenden**     |- Windows Server 2016 </br>Windows Server 2012 R2 </br>Windows Server 2012       |
| | |

Weitere Informationen finden Sie unter Bereitstellen [des Azure Rights Management-Verbindungs-Connector](deploy-rms-connector.md).

## <a name="supported-operating-systems-for-azure-rights-management"></a>Unterstützte Betriebssysteme für Azure Rights Management

Die folgenden Betriebssysteme unterstützen den Azure Rights Management-Dienst, der Datenschutz für AIP bereitstellt:

|OS  |Unterstützte Versionen  |
|---------|---------|
|**Windows-Computer**     |-Windows 7 (x86, x64) </br>- Windows 8 (x86, x64) </br>- Windows 8.1 (x86, x64) </br>- Windows 10 (x86, x64)       | 
|**macOS**     |   Mindestversion von macOS 10.8 (Mountain Lion)      |
|**Android-Telefone und-Tablets**     | Mindestversion von Android 6,0        |
|**iPhone und iPad**     | Mindestversion von IOS 11,0        |
|**Windows-Telefone und-Tablets** | Windows 10 Mobile|
| | |



## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie alle AIP-Anforderungen überprüft und bestätigt haben, dass Ihr System konform ist, können Sie die [Vorbereitung von Benutzern und Gruppen auf Azure Information Protection](prepare.md)fortsetzen.

