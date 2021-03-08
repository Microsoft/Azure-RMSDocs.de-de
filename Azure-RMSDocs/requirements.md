---
title: Anforderungen an Azure Information Protection – AIP
description: Ermitteln Sie die Voraussetzungen für die Bereitstellung von Azure Information Protection in Ihrer Organisation.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/04/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: c5eade80b9e3f46e5288b4604f64063cf097a170
ms.sourcegitcommit: 95f3b19e1034025e7de0ca523b837843d9c15d86
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "102094846"
---
# <a name="azure-information-protection-requirements"></a>Anforderungen an Azure Information Protection

>****Gilt für:** _[Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)_
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen AIP-Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Bevor Sie Azure Information Protection bereitstellen, stellen Sie sicher, dass Ihr System folgende Voraussetzungen erfüllt:

- [Abonnement für Azure Information Protection](#subscription-for-azure-information-protection)
- [Azure Active Directory](#azure-active-directory)
- [Clientgeräte](#client-devices)
- [Anwendungen](#applications)
- [Firewalls und Netzwerkinfrastruktur](#firewalls-and-network-infrastructure)

## <a name="subscription-for-azure-information-protection"></a>Abonnement für Azure Information Protection

Je nachdem, welche Azure Information Protection-Features Sie verwenden werden, benötigen Sie eins der folgenden Elemente:

- **Einen [Azure Information Protection-Plan](https://azure.microsoft.com/pricing/details/information-protection/)** . Erforderlich für die Klassifizierung, Bezeichnung und den Schutz über den Azure Information Protection-Scanner oder -Client

- **Einen [Office 365-Plan, der Azure Information Protection einschließt](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)** . Nur für den Schutz erforderlich.

Überprüfen Sie anhand der Featureliste auf der [Preisseite für Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), ob Ihr Abonnement die gewünschten Azure Information Protection-Features umfasst.

Wenn Sie Fragen zur Lizenzierung haben, lesen Sie die [häufig gestellten Fragen](https://azure.microsoft.com/pricing/details/information-protection#faq) zur Lizenzierung.

> [!TIP]
> Möchten Sie wissen, ob Ihr Plan die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) unterstützt, damit geschützte E-Mails an persönliche E-Mail-Adressen gesendet werden können? Beispiele sind Gmail, Yahoo und Microsoft. Weitere Informationen finden Sie in folgenden Ressourcen:
>
> - [Exchange Online-Dienstbeschreibung](/office365/servicedescriptions/exchange-online-service-description/exchange-online-service-description)
>
> - [Vergleich der Lizenzierung für Microsoft 365-Konformität](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-business-service-description)
>
> - [Office 365 Education](/office365/servicedescriptions/office-365-platform-service-description/office-365-education)
>
> - [Office 365 US Government](/office365/servicedescriptions/office-365-platform-service-description/office-365-us-government/office-365-us-government)

Wenn Sie Fragen zum Abonnement oder zur Lizenzierung haben, dann stellen Sie diese bitte nicht auf dieser Seite. Möglicherweise finden Sie passende Antworten im Abschnitt [Häufig gestellte Fragen zur Lizenzierung](https://azure.microsoft.com/pricing/details/information-protection#faq). Wenden Ihre Frage darin nicht beantwortet wird, wenden Sie sich an Ihren Microsoft-Konto-Manager oder an den [Microsoft-Support](information-support.md#to-contact-microsoft-support).

## <a name="azure-active-directory"></a>Azure Active Directory

Zur Unterstützung der Authentifizierung und Autorisierung für Azure Information Protection müssen Sie über ein Azure Active Directory (Azure AD) verfügen. Wenn Sie Benutzerkonten aus Ihrem lokalen Verzeichnis (AD DS) verwenden möchten, müssen Sie auch die Verzeichnisintegration konfigurieren.

- Das **einmalige Anmelden (Single Sign-On, SSO)** wird für Azure Information Protection unterstützt, sodass Benutzer nicht wiederholt zur Angabe ihrer Anmeldeinformationen aufgefordert werden. Wenn Sie die Lösung eines anderen Anbieters für den Verbund verwenden, fragen Sie beim Anbieter nach, wie die Lösung für Azure AD konfiguriert werden muss. WS-Trust ist eine häufige Anforderung für diese Lösungen zur Unterstützung des einmaligen Anmeldens. 

- **Multi-Factor Authentication (MFA)** wird mit Azure Information Protection unterstützt, wenn die erforderliche Clientsoftware installiert und die Infrastruktur zur Unterstützung von MFA richtig konfiguriert ist.

Bedingter Zugriff wird in der Vorschauversion für Dokumente unterstützt, die mithilfe von Azure Information Protection geschützt sind. Weitere Informationen finden Sie in folgenden Quellen: [Azure Information Protection wird als verfügbare Cloud App für den bedingten Zugriff genannt. Wie funktioniert das?](faqs.md#i-see-azure-information-protection-is-listed-as-an-available-cloud-app-for-conditional-accesshow-does-this-work)

Für bestimmte Szenarien gelten weitere Voraussetzungen, beispielsweise für die zertifikatbasierte oder mehrstufige Authentifizierung, oder wenn UPN-Werte nicht mit E-Mail-Adressen von Benutzern übereinstimmen.

Weitere Informationen finden Sie unter

- [Zusätzliche Azure AD-Anforderungen für Azure Information Protection](requirements-azure-ad.md).
- [Was ist ein Azure AD-Verzeichnis?](/azure/active-directory/fundamentals/active-directory-whatis)
- [Integrieren lokaler Active Directory-Domänen in Azure Active Directory](/azure/architecture/reference-architectures/identity/azure-ad).

## <a name="client-devices"></a>Clientgeräte

Computer oder mobile Geräte von Benutzern müssen ein Betriebssystem ausführen, das Azure Information Protection unterstützt.

- [Unterstützte Betriebssysteme für Clientgeräte](#supported-operating-systems-for-client-devices)
- [Virtuelle Computer](#virtual-machines)
- [Serverunterstützung](#server-support)
- [Zusätzliche Anforderungen pro Client](#additional-requirements-per-client)

### <a name="supported-operating-systems-for-client-devices"></a>Unterstützte Betriebssysteme für Clientgeräte

Die Azure Information Protection-Clients werden von den folgenden Windows-Betriebssystemen unterstützt:

- **Windows 10** (x86, x64). Handschriftliche Einträge werden im Windows 10 RS4-Build und höher nicht unterstützt.
 
- **Windows 8.1** (x86, x64)

- **Windows 8** (x86, x64)

- **Windows Server 2019**

- **Windows Server 2016**

- **Windows Server 2012 R2** und **Windows Server 2012**

Weitere Informationen zur Unterstützung in früheren Windows-Versionen erhalten Sie von Ihrem Microsoft-Kontobeauftragten oder einem Microsoft-Supportmitarbeiter.

> [!NOTE]
> Wenn der Azure Information Protection-Client Daten mithilfe des Azure Rights Management-Diensts schützt, können die Daten von den [gleichen Geräten](#client-devices) genutzt werden, die auch den Azure Rights Management-Dienst unterstützen.
>
### <a name="arm64"></a>ARM64 

ARM64 wird derzeit **nicht** unterstützt. 

### <a name="virtual-machines"></a>Virtuelle Computer

Wenn Sie mit virtuellen Computern arbeiten, erkundigen Sie sich beim Softwareanbieter Ihrer virtuellen Desktoplösung, ob für die Ausführung des Azure Information Protection-Clients für einheitliche Bezeichnungen oder des Azure Information Protection-Clients zusätzliche Konfigurationen erforderlich sind. 

Ein Beispiel: In Citrix-Lösungen müssen Sie möglicherweise für Office, den Azure Information Protection-Client für einheitliche Bezeichnungen oder den Azure Information Protection-Client die [Citrix-API-Hooks deaktivieren](https://support.citrix.com/article/CTX107825). 

Diese Anwendungen nutzen die folgenden Dateien: **winword.exe**, **excel.exe**, **outlook.exe**, **powerpnt.exe**, **msip.app.exe**, **msip.viewer.exe**

### <a name="server-support"></a>Serverunterstützung

Unter jeder der aufgelisteten Serverversionen werden Azure Information Protection-Clients für Remotedesktopdienste unterstützt. 

Wenn Sie bei Verwendung der Azure Information Protection-Clients mit Remotedesktopdiensten Benutzerprofile löschen, löschen Sie nicht den Ordner **%Appdata%\Microsoft\Protect**.

Server Core und Nano Server werden nicht unterstützt.

### <a name="additional-requirements-per-client"></a>Zusätzliche Anforderungen pro Client

Für jeden Azure Information Protection-Client gelten zusätzliche Voraussetzungen. Einzelheiten dazu finden Sie unter:

- [Zusätzliche Anforderungen für die Installation des Clients für einheitliche Bezeichnungen in Unternehmensnetzwerken](./rms-client/reqs-ul-client.md)

- [Zusätzliche Voraussetzungen für den Azure Information Protection-Client](./rms-client/client-admin-guide-install.md#additional-prerequisites-for-the-azure-information-protection-client)

## <a name="applications"></a>Anwendungen

Die Azure Information Protection-Clients können Dokumente und E-Mails bezeichnen und schützen. Dafür werden die Microsoft-Anwendungen **Word**, **Excel**, **PowerPoint** und **Outlook** aus einer der folgenden Office-Editionen verwendet:

- **Office-Apps** für die in der [Tabelle der unterstützten Versionen für Microsoft 365-Apps nach Updatekanal](/officeupdates/update-history-microsoft365-apps-by-date) aufgeführten Versionen von Microsoft 365 Apps for Business oder Microsoft 365 Business Premium, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Microsoft 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.

- **Microsoft 365 Apps for Enterprise**

- **Office Professional Plus 2019**

- **Office Professional Plus 2016**

- **Office Professional Plus 2013 mit Service Pack 1**

- **Office Professional Plus 2010 mit Service Pack 2**

Andere Office-Suiten können keine Dokumente und E-Mails mithilfe eines Rights Management-Diensts schützen. Bei diesen Editionen wird Azure Information Protection nur für die Klassifizierung unterstützt. Bezeichnungen, die Schutz anwenden, werden für Benutzer nicht angezeigt. 

Bezeichnungen werden in einer Leiste oben im Office-Dokument angezeigt, auf die Sie über die Schaltfläche **Sensitivity** (Vertraulichkeit) im Client für einheitliche Bezeichnungen oder über die Schaltfläche **Protect** (Schutz) im klassischen Client zugreifen können.

Weitere Informationen finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](requirements-applications.md).

> [!IMPORTANT]
> Der erweiterte Support für Office 2010 endete am 13. Oktober 2020. Weitere Informationen finden Sie unter [AIP und ältere Windows- und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).
> 

### <a name="office-features-and-capabilities-not-supported"></a>Nicht unterstützte Office-Features und -Funktionen

- Die Azure Information Protection-Clients für Windows unterstützen nicht mehrere Office-Versionen auf demselben Computer. Auch der Wechsel von Benutzerkonten in Office wird nicht unterstützt.

- Das Office-Feature [Seriendruck](https://support.office.com/article/use-mail-merge-for-bulk-email-letters-labels-and-envelopes-f488ed5b-b849-4c11-9cff-932c49474705) wird mit keinem Azure Information Protection-Feature unterstützt.

## <a name="firewalls-and-network-infrastructure"></a>Firewalls und Netzwerkinfrastruktur

Wenn Sie eine Firewall oder ähnliche Interventionsnetzwerkgeräte verwenden, die so konfiguriert wurden, dass bestimmte Verbindungen erlaubt sind, finden Sie hier die Netzwerkanforderungen: [Microsoft 365 allgemein und Office Online](/office365/enterprise/urls-and-ip-address-ranges#microsoft-365-common-and-office-online).

Für Azure Information Protection gelten die folgenden zusätzlichen Voraussetzungen:

- **Client für einheitliche Bezeichnungen**: Zum Herunterladen von Bezeichnungen und Bezeichnungsrichtlinien lassen Sie die folgende URL über HTTPS zu: **_.protection.outlook.com_*.

- **Webproxys**: Wenn Sie einen Webproxy verwenden, der eine Authentifizierung erfordert, müssen Sie ihn so konfigurieren, dass er die integrierte Windows-Authentifizierung mit den Active Directory-Anmeldeinformationen des Benutzers verwendet.

    Um bei Verwendung eines Proxys zum Abrufen eines Tokens **Proxy.pac**-Dateien zu unterstützen, fügen Sie den folgenden neuen Registrierungsschlüssel hinzu:

    - **Pfad**: `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIP\`
    - **Schlüssel**: `UseDefaultCredentialsInProxy`
    - **Typ:** `DWORD`
    - **Wert**: `1`
    
- **TLS-Verbindungen zwischen Client und Dienst**. Beenden Sie keine TLS-Client-zu-Dienst-Verbindungen (z. B. zur Durchführung von Überprüfungen auf Paketebene) mit der URL **aadrm.com**. Ansonsten wird die Anheftung von Zertifikaten beendet, die von RMS-Clients für von Microsoft verwaltete Zertifizierungsstellen verwendet wird, um die Kommunikation mit dem Azure Rights Management-Dienst zu schützen.
     
    Wenn Sie ermitteln möchten, ob Ihre Clientverbindung beendet wird, bevor sie den Azure Rights Management-Dienst erreicht, verwenden Sie die folgenden PowerShell-Befehle:

    ```PowerShell
    $request = [System.Net.HttpWebRequest]::Create("https://admin.na.aadrm.com/admin/admin.svc")
    $request.GetResponse()
    $request.ServicePoint.Certificate.Issuer
    ```

    Das Ergebnis sollte zeigen, dass die ausstellende Zertifizierungsstelle von einer Microsoft Zertifizierungsstelle stammt, z. B. `CN=Microsoft Secure Server CA 2011, O=Microsoft Corporation, L=Redmond, S=Washington, C=US`. 
    
    Wenn Sie den Namen einer ausstellenden Zertifizierungsstelle sehen, die nicht von Microsoft stammt, ist es wahrscheinlich, dass Ihre sichere Client-zu-Dienst-Verbindung beendet wurde und in Ihrer Firewall neu konfiguriert werden muss.

- **TLS-Version 1.2 oder höher** (nur Client für einheitliche Bezeichnungen): Der Client für einheitliche Bezeichnungen erfordert die TLS-Version 1.2 oder höher, um die Verwendung von kryptografisch sicheren Protokollen und die Übereinstimmung mit Microsoft-Sicherheitsrichtlinien sicherzustellen.

- **Microsoft 365 Enhanced Configuration Service (ECS)**. AIP muss Zugriff auf die **config.edge.skype.com**-URL haben, bei der es sich um eine Microsoft 365 Enhanced Configuration Service-Instanz (ECS) handelt.
 
    ECS bietet Microsoft die Möglichkeit, AIP-Installationen neu zu konfigurieren, ohne dass Sie AIP erneut bereitstellen müssen. Dieser Dienst wird verwendet, um den sukzessiven Rollout von Features oder Updates zu steuern, wobei die Auswirkungen des Rollouts über die gesammelten Diagnosedaten überwacht werden.
    
    ECS wird auch verwendet, um Sicherheits- oder Leistungsprobleme mit einem Feature oder Update zu mindern. ECS unterstützt auch Konfigurationsänderungen im Zusammenhang mit Diagnosedaten, um sicherzustellen, dass die richtigen Ereignisse gesammelt werden. 
 
    Das Einschränken der **config.edge.skype.com**-URL kann die Fähigkeit von Microsoft beeinträchtigen, Fehler zu beheben, und kann sich auf das Testen von Vorschaufeatures auswirken.
 
    Weitere Informationen finden Sie unter [Wesentliche Dienste für Office](/deployoffice/privacy/essential-services).
### <a name="coexistence-of-ad-rms-with-azure-rms"></a>Gleichzeitige Verwendung von AD RMS mit Azure RMS

Die parallele Verwendung von AD RMS und Azure RMS innerhalb einer Organisation zum Schutz von Inhalten ein und desselben Benutzers in ein und derselben Organisation wird **nur** in AD RMS für den [HYOK-Schutz (Hold Your Own Key)](configure-adrms-restrictions.md) mit Azure Information Protection unterstützt.

Dieses Szenario wird während der [Migration](migrate-from-ad-rms-to-azure-rms.md) *nicht* unterstützt.
Folgende Migrationspfade werden unterstützt:

* [Von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)

* [Von Azure Information Protection zu AD RMS](/powershell/module/aipservice/Set-AipServiceMigrationUrl)

> [!TIP]
> Wenn Sie Azure Information Protection bereitstellen und dann beschließen, diesen Clouddienst nicht mehr zu verwenden, finden Sie weitere Informationen unter [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](decommission-deactivate.md).

In anderen, nicht migrationsbezogenen Szenarien, in denen beide Dienste in ein und derselben Organisation aktiv sind, müssen beide Dienste so konfiguriert werden, dass nur einer der Dienste einem Benutzer das Schützen von Inhalten erlaubt. Konfigurieren Sie solche Szenarien folgendermaßen:

* Verwenden Sie Umleitungen für eine [Migration von AD RMS zu Azure RMS](migrate-from-ad-rms-to-azure-rms.md).

* Wenn beide Dienste gleichzeitig für verschiedene Benutzer aktiv sein müssen, verwenden Sie dienstseitige Konfigurationen, um Exklusivität zu erzwingen.  Verwenden Sie die Azure RMS-Steuerelemente für das Onboarding im Clouddienst und eine Zugriffssteuerungsliste in der Veröffentlichungs-URL, um den **schreibgeschützten** Modus für AD RMS festzulegen.

### <a name="service-tags"></a>Diensttags

Wenn Sie einen Azure-Endpunkt und eine NSG verwenden, stellen Sie sicher, dass Sie für die folgenden Diensttags den Zugriff auf alle Ports zulassen:

- **AzureInformationProtection**
- **AzureActiveDirectory**
- **AzureFrontDoor.Frontend**

Außerdem benötigt der Azure Information Protection-Dienst in diesem Fall die folgenden IP-Adressen und folgenden Port:

 - **13.107.9.198**
 - **13.107.6.198**
 - **2620:1ec:4::198**
 - **2620:1ec:a92::198**
 - **13.107.6.181** 
 - **13.107.9.181**
 - **Port 443** für HTTPS-Datenverkehr

Erstellen Sie unbedingt Regeln, um den ausgehenden Zugriff auf diese IP-Adressen über diesen Port zuzulassen.

## <a name="supported-on-premises-servers-for-azure-rights-management-data-protection"></a>Unterstützte lokale Server für den Azure Rights Management-Datenschutz

Bei Verwendung des Azure Rights Management-Connectors werden die folgenden lokalen Server mit Azure Information Protection unterstützt.

Dieser Connector dient als Kommunikationsschnittstelle und vermittelt zwischen lokalen Servern und dem Azure Rights Management-Dienst, der Office-Dokumente und E-Mails mithilfe von Azure Information Protection schützt. 

Für die Verwendung des Connectors müssen Sie die Verzeichnissynchronisierung zwischen Ihren Active Directory-Gesamtstrukturen und Azure Active Directory konfigurieren.

Folgende Server werden unterstützt:

|Servertyp  |Unterstützte Versionen  |
|---------|---------|
|**Exchange Server**     | – Exchange Server 2016 </br>– Exchange Server 2013 </br>– Exchange Server 2010       |
|**Office SharePoint Server**     |– Office SharePoint Server 2016 </br>– Office SharePoint Server 2013 </br>– Office SharePoint Server 2010         |
|**Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI) verwenden**     |- Windows Server 2016 </br>Windows Server 2012 R2 </br>Windows Server 2012       |
| | |

Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

## <a name="supported-operating-systems-for-azure-rights-management"></a>Unterstützte Betriebssysteme für Azure Rights Management

Die folgenden Betriebssysteme unterstützen den Azure Rights Management-Dienst, der Datenschutz für AIP bietet:

|OS  |Unterstützte Versionen  |
|---------|---------|
|**Windows-Computer**     |– Windows 7 (x86, x64) </br>- Windows 8 (x86, x64) </br>- Windows 8.1 (x86, x64) </br>- Windows 10 (x86, x64)       | 
|**macOS**     |   Mindestversion von macOS 10.8 (Mountain Lion)      |
|**Android-Smartphones und -Tablets**     | Mindestversion: Android 6.0        |
|**iPhone und iPad**     | Mindestversion: iOS 11.0        |
|**Windows-Smartphones und -Tablets** | Windows 10 Mobile|
| | |



## <a name="next-steps"></a>Nächste Schritte

Wenn Sie alle AIP-Anforderungen überprüft und sich vergewissert haben, dass Ihr System konform ist, fahren Sie mit [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md) fort.