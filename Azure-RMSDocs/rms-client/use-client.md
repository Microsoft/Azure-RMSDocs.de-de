---
title: The client for Azure Information Protection - AIP
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: a5139eed7bccb8a7a57fda0a3b346a1965f7ea50
ms.sourcegitcommit: fed1df1858f8316f7dd45e751c6910b444651a87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474326"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Applies to: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- The client can be the built-in labeling client for Office, the Azure Information Protection unified labeling client for Windows, the Azure Information Protection client (classic) for Windows, or the Rights Management client.
    
    These clients are often referred to as the **Office built-in labeling client**, the **unified labeling client**, the **classic client**, and the **RMS client**, respectively. Whichever client you use, it integrates with applications that you run on computers and mobile devices.

- The service resides in the cloud or on-premises. The cloud service is Azure Information Protection, which uses the Azure Rights Management service for the data protection. The on-premises service is Active Directory Rights Management Services, more commonly known as AD RMS. 

All these clients integrate with Office applications but the unified labeling client and the classic client must be installed separately and support additional features and components. For example, these clients include support for File Explorer, so you can classify and protect files outside Office. Additional components include a viewer for protected PDF documents and protected images, and a scanner for on-premises data stores.

The RMS client provides protection only. This client is automatically installed with some applications, such as Office applications, the Azure Information Protection clients, and RMS-enlightened applications from software vendors. Er kann jedoch auch [eigenständig installiert](https://www.microsoft.com/en-us/download/details.aspx?id=38396) werden, um das [Synchronisieren von Dateien von IRM-geschützten Bibliotheken und OneDrive for Business](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668) zu unterstützen sowie für Entwickler, die den Rights Management-Schutz in branchenspezifische Anwendungen integrieren möchten.

## <a name="choose-which-labeling-client-to-use-for-windows-computers"></a>Choose which labeling client to use for Windows computers

Where possible, use one of the labeling clients because labels abstract the complexity of applying protection for users, and labels also provide classification so you can track and manage your data.

Your choice of labeling client for your Windows computers might be influenced by which management portal you use:

- The Office built-in labeling client and the Azure Information Protection unified labeling client download labels and policy settings from the following admin centers: 
    - Office 365 Security & Compliance Center
    - Microsoft 365 security center
    - Microsoft 365 compliance center

- The Azure Information Protection client (classic) downloads label and policy settings from the Azure portal.

Because the unified labeling client and the classic client require a separate installation to Office, you must download and install these clients from the [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018). 

Which client should you use?

- Use the **labeling client built in to Office** for your Windows computers when you have Office 365 apps that are a minimum version 1910, you want to use the same labels and policy settings that can also be used by MacOS, iOS, and Android, and you don't need features in your Office apps that require the unified labeling client or classic client. These features include the Information Protection bar under the ribbon for easier label selection and visibility. This client supports switching accounts, and because it doesn't use an Office add-in, it has better performance in Office apps than using either of the Azure Information Protection clients.

- Use the **Azure Information Protection unified labeling client** on Windows computers for labels and policy settings that can also be used by MacOS, iOS, and Android, you want to label files independently from Office 365 apps, and you don’t need features that are only supported by the classic client. These features currently include protecting content with an on-premises key (HYOK) and a general availability version of the scanner for on-premises data stores.

- Install the **Azure Information Protection client (classic)** on Windows computers if you need a version of the client that has features that are not yet available with the unified labeling client. Although this client can use the same labels as those used by MacOS, iOS, and Android, it has different policy settings. So your tradeoff is administration using another management portal and a different user experience for users.

The latest version of the unified labeling client brings it to close parity in features with the classic client. As this gap closes, you can expect new features to be added only to the unified labeling client. For this reason, we recommend you deploy the unified labeling client if its current feature set and functionality meet your business requirements. If not, or if you have configured labels in the Azure portal that you haven't yet [migrated to the unified labeling store](../configure-policy-migrate-labels.md), use the classic client.

You can use different clients in the same environment to support different business requirements, as demonstrated in the following deployment example. In a mixed client environment, we recommend you use unified labels so that clients share the same set of labels for ease of administration. New customers have unified labels by default because their tenants are on the unified labeling platform. For more information, see [How can I determine if my tenant is on the unified labeling platform?](../faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)

When you have a Windows computer that runs Office 365 apps that are a minimum version 1910 and one of the Azure Information Protection clients is installed, by default the built-in labeling client is disabled in Office apps. However, you can change this behavior to use the built-in labeling client for just your Office apps. With this configuration, the Azure Information Protection client (classic or unified labeling) remains available for labeling in File Explorer, PowerShell, and the scanner. For instructions to disable the Azure Information Protection client in Office 365 apps, see the section [Can sensitivity labels run alongside the Azure Information Protection client in Office for Windows?](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps#can-sensitivity-labels-run-alongside-the-azure-information-protection-client-in-office-for-windows) from the Office documentation.

##### <a name="example-deployment-strategy"></a>Example deployment strategy:

- For the majority of users, you deploy the Azure Information Protection unified labeling client because this client meets the business needs for these users. 
    
    For these users, their labeling experience is very similar across Windows, Mac, iOS, and Android because they have the same labels published to them and the same policy settings. As an admin, you manage these labels and policy settings in the same management center.

- You also install the unified labeling client for yourself, to test the preview version of the Azure Information Protection scanner.

- For a subset of users, you deploy the classic client because these users require labels that apply hold your own key (HYOK) protection.
    
    For these users, they have a slightly different labeling experience when they use this client. For example, they see a **Protect** button rather than a **Sensitivity** button in Office apps. As an admin, you need to manage their labels for HYOK settings and policy settings in a different management center to the labels and settings for the other client platforms.

- You have on-premises data stores with documents that need to be scanned for sensitive information, or classified and protected. For production use, you deploy the classic client on servers to run the Azure Information Protection scanner.

## <a name="compare-the-labeling-clients-for-windows-computers"></a>Compare the labeling clients for Windows computers

Use the following table to help compare which features are supported by the three labeling clients for Windows computers.

To compare the Office built-in sensitivity labeling features across different operating system platforms (Windows, MacOS, iOS, and Android) and for the web, see the Office documentation, [What sensitivity label capabilities are supported in Office today?](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps#what-sensitivity-label-capabilities-are-supported-in-office-today)

|Komponente|Classic client|Unified labeling client|Office built-in labeling client|
|:------|:------------:|:---------------------:|:-----------------------------:|
|Manual labeling:| **Ja** | **Ja** |**Ja** |
|Default label:| **Ja** | **Ja** | **Ja** |
|Recommended or automatic labeling:| **Ja** | **Ja** | Nein |
|Mandatory labeling:| **Ja** | **Ja** | Nein |
|User-defined permissions for a label:<br />- Do Not Forward for emails<br />- Custom permissions for Word, Excel, PowerPoint, File Explorer| **Ja** | **Ja** | Nein |
|Multilanguage support for labels:| **Ja** | **Ja** |**Ja** |
|Vererbung von Bezeichnungen aus E-Mail-Anhängen:| **Ja** | **Ja**  |Nein |
|Customizations that include:<br />– Standardbezeichnung für E-Mails<br />- Pop-up messages in Outlook <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| **Yes** <sup>1</sup> | **Yes** <sup>2</sup> | Nein |
|Überprüfung für lokale Datenspeicher:| **Ja** | **Yes <br />(preview)** | Nein |
|Zentrale Berichterstellung (Analysen):| **Ja** | **Ja** | Nein |
|Custom permissions set independently from a label:| **Ja** | **Yes** <sup>3</sup>| Nein |
|Information Protection-Leiste in Office-Apps:| **Ja** | **Ja**| Nein |
|Visual markings as a label action (header, footer, watermark):| **Ja** | **Ja** | **Ja**|
|Per app visual markings:| **Ja** | Nein | Nein |
|Dynamic visual markings with variables:| **Ja** | Nein | Nein |
|Label with File Explorer:| **Ja** | **Ja** | Nein |
|A viewer for protected files (text, images, PDF, .pfile):| **Ja** | **Ja** | Nein|
|PPDF support for applying labels:| **Ja** | Nein | Nein |
|PowerShell labeling cmdlets:| **Ja** | **Yes** <sup>4</sup> | Nein |
|Offlineunterstützung für Schutzaktionen:| **Ja** | **Yes** <sup>5</sup> | **Ja** |
|Manual policy file management for disconnected computers:| **Ja** |**Yes** <sup>6</sup>| Nein |
|HYOK-Unterstützung:| **Ja** | Nein | Nein |
|Usage logging in Event Viewer:| **Ja** | Nein |Nein |
|Display the Do Not Forward button in Outlook:| **Ja** | Nein | Nein |
|Track protected documented:| **Ja** | **Yes** <sup>7</sup> | Nein |
|Revoke protected documents:| **Ja** | Nein | Nein |
|Reiner Schutzmodus (keine Bezeichnungen):| **Ja** | Nein | Nein |
|Support for account switching:| Nein | Nein | **Ja** |
|Unterstützung für AD RMS:| **Ja** | No <sup>8</sup> | Nein |

Fußnoten:

<sup>1</sup> These settings, and many more are supported as [advanced client settings that you configure in the Azure portal](client-admin-guide-customizations.md#how-to-configure-advanced-client-configuration-settings-in-the-portal).

<sup>2</sup> These settings, and many more are supported as [advanced settings that you configure with PowerShell](clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell).

<sup>3</sup> Supported by File Explorer and PowerShell. In Office apps, users can select **File Info** > **Protect Document** > **Restrict Access**.

<sup>4</sup> No support to remove protection from container files (zip, .rar, .7z, .msg, and .pst).

<sup>5</sup> For File Explorer and PowerShell commands, the user must be connected to the internet to protect files.

<sup>6</sup> Supported for labeling with File Explorer, PowerShell, and the scanner. Not supported for labeling in Office apps.

<sup>7</sup> The document tracking site that's supported by the classic client isn't supported by the unified labeling client. However, without the need to first register the document for tracking, administrators can use [central reporting](../reports-aip.md) to identify whether protected documented are accessed from Windows computers, and whether access was granted or denied. 

<sup>8</sup> Labeling and protection actions aren't supported. However, for an AD RMS deployment, the viewer can open protected documents when you use the [Active Directory Rights Management Services Mobile Device Extension](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\)).


### <a name="detailed-comparisons-for-the-azure-information-protection-clients"></a>Detailed comparisons for the Azure Information Protection clients

When the Azure Information Protection client (classic) and the Azure Information Protection unified labeling client both support the same feature, use the following table to help identify some functional differences between the two clients.

|Funktion |Classic client|Unified labeling client|
|--------------|-----------------------------------|-----------------------------------------------------------|
|Setup:| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|Auswahl und Anzeige von Bezeichnungen, wenn diese in Office-Apps angewendet werden:|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|Verwalten der Information Protection-Leiste in Office-Apps:|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Schützen** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App ausgeblendet, aber in neu geöffneten Apps weiterhin automatisch angezeigt <br /><br /> Für Administratoren: <br /><br />– Richtlinieneinstellungen zum automatischen Anzeigen oder Ausblenden der Leiste beim ersten Öffnen einer App sowie zum Steuern, ob die Leiste bei neu geöffneten Apps automatisch ausgeblendet wird, nachdem ein Benutzer die Leiste in einer App ausgeblendet hat|Für Benutzer: <br /><br />– Option zum Anzeigen oder Ausblenden der Leiste über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br />– Wenn ein Benutzer die Leiste ausblendet, wird sie standardmäßig in dieser App und in neu geöffneten Apps ausgeblendet <br /><br />Für Administratoren: <br /><br />- PowerShell setting to manage the bar |
|Bezeichnungsfarbe: | Konfigurieren im Azure-Portal | Retained after label migration and configurable with [PowerShell](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)|
|Labels support different languages:| Konfigurieren im Azure-Portal | Configure by using Office 365 Security & Compliance PowerShell and the *LocaleSettings* parameter for [New-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-label?view=exchange-ps) and [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps)|
|Richtlinienaktualisierung: | Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 24 Stunden <br /><br />For the scanner: Every hour and when the service starts and the policy is older than one hour| Beim Öffnen einer Office-App <br /><br /> Beim Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen <br /><br />Beim Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz<br /><br />Alle 4 Stunden <br /><br />For the scanner: Every 4 hours|
|Unterstützte Formate für PDF:| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /><br /> – PPDF <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz| Schutz: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br /> <br /><br /> Verbrauch: <br /><br /> – ISO-Standard für die PDF-Verschlüsselung <br /><br />– PPDF<br /><br />– SharePoint-IRM-Schutz|
|Generically protected files (.pfile) opened with the viewer:| File opens in the original app where it can then be viewed, modified, and saved without protection | File opens in the original app where it can then be viewed and modified, but not saved|
|Unterstützte Cmdlets:| Cmdlets for labeling and cmdlets for protection-only | Cmdlets for labeling:<br /><br /> Set-AIPFileClassification and Set-AIPFileLabel don't support the *Owner* parameter <br /><br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> Set-AIPFileClassification supports the *WhatIf* parameter, so it can be run in discovery mode <br /><br /> Set-AIPFileLabel unterstützt den Parameter *EnableTracking* nicht <br /><br /> Get-AIPFileStatus gibt keine Bezeichnungsinformationen aus anderen Mandanten zurück und zeigt den Parameter *RMSIssuedTime* nicht an<br /><br />In addition, the *LabelingMethod* parameter for Get-AIPFileStatus displays **Privileged** or **Standard** instead of **Manual** or **Automatic**. Weitere Informationen finden Sie in der [Onlinedokumentation](/powershell/module/azureinformationprotection/get-aipfilestatus).|
|Aufforderungen zur Angabe einer Begründung (sofern konfiguriert) für Aktionen in Office: | Frequency: Per file <br /><br /> Herabsetzen der Vertraulichkeitsstufe <br /><br /> Entfernen einer Bezeichnung<br /><br /> Entfernen des Schutzes | Frequency: Per session <br /><br /> Herabsetzen der Vertraulichkeitsstufe<br /><br /> Entfernen einer Bezeichnung|
|Angewendete Bezeichnungsaktionen entfernen: | Benutzer wird zur Bestätigung aufgefordert <br /><br />Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet  <br /><br />| Benutzer wird nicht zur Bestätigung aufgefordert<br /><br /> Standardbezeichnung oder automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet|
|Automatic and recommended labels: | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br /><br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /><br /> – Mindestanzahl| Konfiguration in den Admin-Centers mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](https://docs.microsoft.com/microsoft-365/compliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br /><br />– Nur Anzahl eindeutiger Vorkommnisse <br /><br />– Mindest- und Höchstanzahl <br /><br />– Unterstützung von AND und OR bei Informationstypen <br /><br />– Wörterbuch mit Schlüsselwörtern<br /><br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|
|Customizable policy tip for automatic and recommended labels: | Ja <br /><br />Use the Azure portal to replace the default message to users | Nein <br /><br /> Although the admin centers have an option to supply a customized policy tip, this option is not currently supported by the unified labeling client|
|Change the default protection behavior for file types: | You can use [registry edits](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) to override the defaults of native and generic protection | You can use [PowerShell](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect) to change which file types get protected|

For a detailed comparison of behavior differences for specific protection settings, see [Comparing the behavior of protection settings for a label](../configure-policy-migrate-labels.md#comparing-the-behavior-of-protection-settings-for-a-label).

### <a name="features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client"></a>Features not planned to be in the Azure Information Protection unified labeling client

Although the Azure Information Protection unified labeling client is still under development, the following features and behavior differences from the classic client are not currently planned to be available in future releases for the unified labeling client: 

- Support Office apps for disconnected computers with manual policy file management

- Custom permissions as a separate option that users can select in Office apps: Word, Excel, and PowerPoint

- Nachverfolgen und widerrufen von Office-Apps und dem Datei-Explorer

- Titel und QuickInfo der Information Protection-Leiste

- Protection-only mode (no labels) using templates

- Schutz von PDF-Dokumenten im .ppdf-Format

- Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen

- Demorichtlinien

- Begründung für das Entfernen eines Schutzes

- Confirmation prompt **Do you want to delete this label?** for users when you don't use the policy setting for justification

- Unabhängige PowerShell-Cmdlets zur Verbindung mit einem Rights Management-Dienst


### <a name="parent-labels-and-their-sublabels"></a>Übergeordnete und untergeordnete Bezeichnungen 

The Azure Information Protection client (classic) doesn't support configurations that specify a parent label that has sublabels. Diese Konfigurationen umfassen die Angabe einer Standardbezeichnung sowie einer Bezeichnung für die empfohlene oder automatische Klassifizierung. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, können Sie eine der untergeordneten Bezeichnungen angeben, aber nicht die übergeordnete Bezeichnung.

Aus Paritätsgründen unterstützt der Azure Information Protection-Client für einheitliche Bezeichnungen die Anwendung von übergeordneten Bezeichnungen mit untergeordneten Bezeichnungen ebenfalls nicht, auch wenn Sie diese Bezeichnungen in den Admin-Centers auswählen können. In diesem Szenario wendet der Azure Information Protection-Client für einheitliche Bezeichnungen die übergeordnete Bezeichnung nicht an.

## <a name="next-steps"></a>Nächste Schritte

To install and configure the Azure Information Protection clients, use the following documentation:

- [Azure Information Protection-Client](AIP-client.md)

- [Azure Information Protection-Client für einheitliche Bezeichnungen](unifiedlabelingclient-version-release-history.md)

For more information about using the built-in labeling client for Office 365 apps, see [Sensitivity labels in Office apps](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps).
