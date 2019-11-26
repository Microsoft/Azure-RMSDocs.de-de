---
title: Migrate Azure Information Protection labels to unified sensitivity labels - AIP
description: Migrate Azure Information Protection labels to unified sensitivity labels for clients and services that support the Microsoft Information Protection framework.
author: cabailey
ms.author: cabailey
manager: rkarlin
ms.date: 11/25/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: labelmigrate
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: bb493943696c5bb349ef66e13891ce4139d904e3
ms.sourcegitcommit: fed1df1858f8316f7dd45e751c6910b444651a87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474241"
---
# <a name="how-to-migrate-azure-information-protection-labels-to-unified-sensitivity-labels"></a>How to migrate Azure Information Protection labels to unified sensitivity labels

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
> *Instructions for: [Azure Information Protection client for Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Migrate Azure Information Protection labels to the unified labeling platform so that you can use them as sensitivity labels by [clients and services that support unified labeling](#clients-and-services-that-support-unified-labeling).

> [!NOTE]
> If your Azure Information Protection subscription is fairly new, you might not need to migrate labels because your tenant is already on the unified labeling platform. For more information, see [How can I determine if my tenant is on the unified labeling platform?](faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)

After you migrate your labels, you won't see any difference with the Azure Information Protection client (classic) because this client continues to download the labels with the Azure Information Protection policy from the Azure portal. However, you can now use the labels with the Azure Information Protection unified labeling client and other clients and services that use sensitivity labels.

Before you read the instructions to migrate your labels, you might find the following frequently asked questions useful:

- [Was ist der Unterschied zwischen Bezeichnungen in Azure Information Protection und Office 365?](faqs.md#whats-the-difference-between-labels-in-azure-information-protection-and-labels-in-office-365)

- [When is the right time to migrate my labels?](faqs.md#when-is-the-right-time-to-migrate-my-labels)

- [Welches Verwaltungsportal kann ich verwenden, nachdem ich meine Bezeichnungen migriert habe?](faqs.md?#after-ive-migrated-my-labels-which-management-portal-do-i-use )

### <a name="administrative-roles-that-support-the-unified-labeling-platform"></a>Administrative roles that support the unified labeling platform

If you use admin roles for delegated administration in your organization, you might need to do some changes for the unified labeling platform:

The [Azure AD roles](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) of **Azure Information Protection administrator** (formerly **Information Protection administrator**), **Security reader**, and **Global reader** are not supported by the unified labeling platform. If any of these administrative roles are used in your organization to manage Azure Information Protection, add the users who have this role to the Azure AD roles of **Compliance administrator**, **Compliance data administrator**, or **Security administrator**. Eine Anleitung zu diesem Schritt finden Sie unter [Gewähren von Benutzerzugriff auf das Office 365 Security & Compliance Center](https://docs.microsoft.com/microsoft-365/security/office-365-security/grant-access-to-the-security-and-compliance-center). Diese Rollen können auch im Azure AD-Portal, Microsoft 365 Security Center und Microsoft 365 Compliance Center zugewiesen werden.

Statt Rollen zu verwenden, können Sie auch im jeweiligen Admin Center eine neue Rollengruppe für diese Benutzer erstellen und dieser Gruppe die Rolle **Administrator für Vertraulichkeitsbezeichnungen** oder **Organisationskonfiguration** zuweisen.

Wenn Sie diesen Benutzern nicht über eine dieser Konfigurationen Zugriff auf die Admin Centers gewähren, sind die Benutzer nach der Migration Ihrer Bezeichnungen nicht mehr in der Lage, Azure Information Protection im Azure-Portal zu konfigurieren.

Globale Administratoren für Ihren Mandanten können nach der Migration Ihrer Bezeichnungen weiterhin Bezeichnungen und Richtlinien sowohl im Azure-Portal als auch in den Admin-Centers verwalten.

## <a name="before-you-begin"></a>Vorbereitung

Label migration has many benefits but is irreversible, so make sure that you are aware of the following changes and considerations:

- Make sure that you have [clients that support unified labels](#clients-and-services-that-support-unified-labeling) and if necessary, be prepared for administration in both the Azure portal (for clients that don't support unified labels) and the admin centers (for client that do support unified labels).

- Richtlinien, einschließlich Richtlinieneinstellungen und der entsprechenden Zugriffberechtigungen (bereichsbezogene Richtlinien), sowie alle erweiterten Clienteinstellungen werden nicht migriert. Your options to configure these settings after your label migration include the following:
    - Your admin center for sensitivity labels.
    - [Office 365 Security & Compliance PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps), which you must use to configure [advanced client settings](./rms-client/clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell).
    

- Nicht alle Einstellungen einer migrierten Bezeichnung werden von den Admin-Centers unterstützt. Verwenden Sie die Tabelle im Abschnitt [In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen](#label-settings-that-are-not-supported-in-the-admin-centers), um die entsprechenden Einstellungen sowie die empfohlene Vorgehensweise zu ermitteln.

- Schutzvorlagen:
    
    - Vorlagen, die einen cloudbasierten Schlüssel verwenden und Teil einer Bezeichnungskonfiguration sind, werden ebenfalls mit der Bezeichnung migriert. Andere Schutzvorlagen werden nicht migriert. 
    
    - Wenn Sie über Bezeichnungen verfügen, die für eine vordefinierte Vorlage konfiguriert sind, können Sie diese Bezeichnungen bearbeiten und die Option **Berechtigungen festlegen** auswählen, um die gleichen Schutzeinstellungen wie in Ihrer Vorlage zu konfigurieren. Bezeichnungen mit vordefinierten Vorlagen verhindern die Bezeichnungsmigration nicht, diese Bezeichnungskonfiguration wird jedoch in den Admin-Centers nicht unterstützt.
        
        Tip: To help you reconfigure these labels, you might find it useful to have two browser windows: One window in which you select the **Edit Template** button for the label to view the protection settings, and the other window to configure the same settings when you select **Set permissions**.
    
    - After a label with cloud-based protection settings has been migrated, the resulting scope of the protection template is the scoped that is defined in the Azure portal (or by using the AIPService PowerShell module) and the scope that is defined in the admin centers. 

- Das Azure-Portal zeigt nur den Anzeigenamen der jeweiligen Bezeichnung an, den Sie bearbeiten können. Users see this label name in their apps. Die Admin-Centers zeigen sowohl den Anzeigenamen als auch den Bezeichnungsnamen an. The label name is the initial name that you specify when the label is first created and this property is used by the back-end service for identification purposes. When you migrate your labels, the display name remains the same and the label name is renamed to the label ID from the Azure portal.

- Lokalisierte Zeichenfolgen für die Bezeichnungen werden nicht migriert. Define new localized strings for the migrated labels by using Office 365 Security & Compliance PowerShell and the *LocaleSettings* parameter for [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps).

- Wenn Sie nach der Migration eine migrierte Bezeichnung im Azure-Portal bearbeiten, wird die entsprechende Änderung automatisch in den Admin-Centers angezeigt. However, when you edit a migrated label in one of the admin centers, you must return to the Azure portal, **Azure Information Protection - Unified labeling** pane, and select **Publish**. This additional action is needed for the Azure Information Protection clients (classic) to pick up the label changes.

### <a name="label-settings-that-are-not-supported-in-the-admin-centers"></a>In den Admin-Centers nicht unterstützte Bezeichnungseinstellungen

Anhand der folgenden Tabelle können Sie feststellen, welche Konfigurationseinstellungen einer migrierten Bezeichnung vom Office 365 Security & Compliance Center, dem Microsoft 365 Security Center, oder dem Microsoft Compliance Center nicht unterstützt werden. If you have labels with these settings, when the migration is complete, use the administration guidance in the final column before you publish your labels in one of the referenced admin centers.

Wenn Sie nicht sicher sind, wie Ihre Bezeichnungen konfiguriert sind, zeigen Sie die zugehörigen Einstellungen im Azure-Portal an. Eine Anleitung zu diesem Schritt finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

Azure Information Protection clients (classic) can use all label settings listed without any problems because they continue to download the labels from the Azure portal.

|Bezeichnungskonfiguration|Unterstützt von Clients für einheitliche Bezeichnungen| Leitfaden für die Admin-Centers|
|-------------------|---------------------------------------------|-------------------------|
|Statusangabe „Aktiviert“/„Deaktiviert“<br /><br />This status is not synchronized to the admin centers |Nicht verfügbar|Das Äquivalent ist, ob die Bezeichnung veröffentlicht wurde oder nicht. |
|Die Bezeichnungsfarbe, die Sie aus der Liste auswählen oder mit einem RGB-Code angeben |Ja|Keine Konfigurationsoption für Bezeichnungsfarben. Instead, you can configure label colors in the Azure portal or use [PowerShell](./rms-client/clientv2-admin-guide-customizations.md#specify-a-color-for-the-label).|
|Cloudbasierter Schutz oder HYOK-Schutz (Hold Your Own Key) mit vordefinierter Vorlage |Nein|Keine Konfigurationsoption für vordefinierte Vorlagen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.|
|Cloudbasierter Schutz mit benutzerdefinierten Berechtigungen für Word, Excel und PowerPoint |Ja|The admin centers now have a configuration option for user-defined permissions. <br /><br /> If you publish a label with this configuration, check the results of applying the label from the [following table](#comparing-the-behavior-of-protection-settings-for-a-label).|
|HYOK-Schutz mit benutzerdefinierten Berechtigungen für Outlook („Nicht weiterleiten“) |Nein|Keine Konfigurationsoption für HYOK. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen. Wenn Sie dies tun, finden Sie die Ergebnisse der Anwendung der Bezeichnung in der [folgenden Tabelle](#comparing-the-behavior-of-protection-settings-for-a-label).|
|Entfernen von Schutz |Nein|Keine Konfigurationsoption, um Schutz zu entfernen. Wir empfehlen nicht, eine Bezeichnung ohne diese Konfiguration zu veröffentlichen.<br /><br /> If you do publish a label with this configuration, when it is applied, protection is always removed, whether the protection was previously applied by a label or independently from a label.|
|Any authenticated user protection setting |Ja|No configuration option to select this protection setting. Publish a label with this configuration when this setting has been migrated or you configure it in the Azure portal.|
|Benutzerdefinierte Schriftart und -farbe (RGB-Code) für optische Kennzeichnungen (Kopfzeile, Fußzeile, Wasserzeichen)|Ja|Die Konfiguration für optische Kennzeichnungen ist begrenzt auf eine Farb- und Schriftgradliste. Sie können diese Bezeichnung ohne Änderungen veröffentlichen, obwohl Sie sich die konfigurierten Werte in den Admin-Centers nicht ansehen können. <br /><br />Wenn Sie diese Optionen ändern möchten, verwenden Sie dazu das Azure-Portal. Sie sollten jedoch in Betracht ziehen, die Farbe in eine der in den Admin-Centers aufgelisteten Optionen zu ändern, um die Verwaltung zu vereinfachen.|
|Visuelle Kennzeichnungsvariablen (Kopfzeile, Fußzeile)|Nein|Wenn Sie diese Bezeichnung ohne Änderungen veröffentlichen, werden Variablen auf Clients als Text und nicht als dynamische Werte angezeigt. Bearbeiten Sie die Zeichenfolgen, um die Variablen zu entfernen, bevor Sie die Bezeichnung veröffentlichen.|
|Visuelle Kennzeichnungen pro App|Nein|Wenn Sie diese Bezeichnung ohne Änderungen veröffentlichen, werden die Anwendungsvariablen auf Clients in allen Anwendungen als Text angezeigt und zeigen nicht Ihre Textzeichenfolgen auf ausgewählten Anwendungen an. Veröffentlichen Sie diese Bezeichnung nur, wenn Sie sich für alle Anwendungen eignet, und bearbeiten Sie die Zeichenfolgen, um die Anwendungsvariablen zu entfernen.|
|Bedingungen und entsprechende Einstellungen <br /><br /> Einschließlich automatischer und empfohlener Bezeichnungen samt QuickInfos|Nicht verfügbar|Konfigurieren Sie Ihre Bedingungen neu, indem Sie die automatische Bezeichnung als eine von den Bezeichnungseinstellungen eigenständige Konfiguration verwenden.|

### <a name="comparing-the-behavior-of-protection-settings-for-a-label"></a>Vergleichen des Verhaltens von Schutzeinstellungen für eine Bezeichnung

Use the following table to identify how the same protection setting for a label behaves differently, depending on whether it's used by the Azure Information Protection client (classic), the Azure Information Protection unified labeling client, or by Office apps that have labeling built in (also known as "native Office labeling"). The differences in label behavior might change your decision whether to publish the labels, especially when you have a mix of clients in your organization.

If you are not sure how your protection settings are configured, view their settings in the **Protection** pane, in the Azure portal. Eine Anleitung zu diesem Schritt finden Sie unter [So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen](configure-policy-protection.md#to-configure-a-label-for-protection-settings).

Schutzeinstellungen, die sich genauso verhalten, werden in der Tabelle nicht aufgeführt, mit den folgenden Ausnahmen:
- Wenn Sie Office-Apps mit integrierter Bezeichnungsfunktion verwenden, werden Bezeichnungen im Datei-Explorer nicht angezeigt, es sei denn, Sie installieren auch den Azure Information Protection Unified Labeling-Client.
- Wenn Sie Office-Apps mit integrierter Bezeichnungsfunktion verwenden, bleibt dieser Schutz bestehen, wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde [[1]](#footnote-1).

|Schutzeinstellung für eine Bezeichnung |Azure Information Protection-Client (klassisch) |Azure Information Protection-Client für einheitliche Bezeichnungen| Office-Apps mit integrierter Bezeichnungsfunktion
|-------------------|-----------------------------------|-----------------------------------------------------------|---------------
|Azure (Cloudschlüssel) mit benutzerdefinierten Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer:| Wird in Word, Excel, PowerPoint und im Datei-Explorer angezeigt <br /><br /> Wenn die Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> - Benutzer werden nach benutzerdefinierten Berechtigungen gefragt, die dann als Schutz mit einem cloudbasierten Schlüssel angewendet werden| Wird in Word, Excel, PowerPoint und im Datei-Explorer angezeigt <br /><br /> Wenn die Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> - Benutzer werden nach benutzerdefinierten Berechtigungen gefragt, die dann als Schutz mit einem cloudbasierten Schlüssel angewendet werden|Wird in Word, Excel, PowerPoint und Outlook angezeigt: <br /><br /> Wenn die Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – Benutzer werden nicht nach benutzerdefinierten Berechtigungen gefragt, und es wird kein Schutz angewendet <br /><br /> – Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1)|
|HYOK (AD RMS) mit Vorlage:| Wird in Word, Excel, PowerPoint, Outlook und im Datei-Explorer angezeigt<br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– HYOK-Schutz wird auf Dokumente und E-Mails angewendet | Wird in Word, Excel, PowerPoint, Outlook und im Datei-Explorer angezeigt  <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen |Wird in Word, Excel, PowerPoint und Outlook angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1) |
|HYOK (AD RMS) mit benutzerdefinierten Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer:| Wird in Word, Excel, PowerPoint und im Datei-Explorer angezeigt<br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – HYOK-Schutz wird auf Dokumente und E-Mails angewendet| Wird in Word, Excel und PowerPoint angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen|Wird in Word, Excel und PowerPoint angezeigt <br /><br /> Wenn diese Bezeichnung angewendet wird, geschieht Folgendes: <br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen |
|HYOK (AD RMS) mit benutzerdefinierten Berechtigungen für Outlook:|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br />– „Nicht weiterleiten“ mit HYOK-Schutz wird auf E-Mails angewendet|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br /> – Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen|Wird in Outlook angezeigt<br /><br />Wenn diese Bezeichnung angewendet wird, geschieht Folgendes:<br /><br />– Es wird kein Schutz angewendet, und der Schutz wird entfernt [[2]](#footnote-2), wenn er zuvor von einer Bezeichnung angewendet wurde <br /><br />– Wenn der Schutz zuvor unabhängig von einer Bezeichnung angewendet wurde, bleibt dieser Schutz bestehen [[1]](#footnote-1)|

###### <a name="footnote-1"></a>Fußnote 1

In Outlook, protection is preserved with one exception: When an email has been protected with the Encrypt-Only option, that protection is removed.


###### <a name="footnote-2"></a>Fußnote 2

Der Schutz wird entfernt, wenn der Benutzer über ein Nutzungsrecht oder eine Nutzungsrolle verfügt, wovon diese Aktion unterstützt wird:
- Das [Nutzungsrecht](configure-usage-rights.md#usage-rights-and-descriptions) „Exportieren“ oder „Vollzugriff“.
- Die Rolle [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder [Administrator](configure-super-users.md).

Wenn der Benutzer über keine/s dieser Nutzungsrechte oder Nutzungsrollen verfügt, wird die Bezeichnung nicht angewendet, und der ursprüngliche Schutz wird beibehalten.


## <a name="to-migrate-azure-information-protection-labels"></a>Migrieren von Azure Information Protection-Bezeichnungen

Use the following instructions to migrate your tenant and Azure Information Protection labels to use the unified labeling store.

You must be a Compliance administrator, Compliance data administrator, Security administrator, or Global administrator to migrate your labels.

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**.
    
    For example, in the search box for resources, services, and docs: Start typing **Information** and select **Azure Information Protection**.

2. From the **Manage** menu option, select **Unified labeling**.

3. On the **Azure Information Protection - Unified labeling** pane, select **Activate** and follow the online instructions.
    
    If the option to activate is not available, check the **Unified labeling status**: If you see **Activated**, your tenant is already using the unified labeling store and there is no need to migrate your labels.

Die Bezeichnungen, die erfolgreich migriert wurden, können nun von [Clients und Diensten, die einheitliche Bezeichnungen unterstützen](#clients-and-services-that-support-unified-labeling), verwendet werden. However, you must first publish these labels in one of the admin centers: Office 365 Security & Compliance Center, Microsoft 365 security center, or Microsoft 365 compliance center.

> [!IMPORTANT]
> If you edit the labels outside the Azure portal, for Azure Information Protection clients (classic), return to this **Azure Information Protection - Unified labeling** pane, and select **Publish**.

### <a name="copy-policies"></a>Copy policies

> [!NOTE]
> This option is in preview and subject to change.

After you have migrated your labels, you can select an option to copy policies. If you select this option, a one-time copy of your policies with their [policy settings](configure-policy-settings.md) and any [advanced client settings](./rms-client/client-admin-guide-customizations.md#available-advanced-client-settings) is sent to the admin center where you manage your labels: Office 365 Security & Compliance Center, Microsoft 365 security center, Microsoft 365 compliance center.

Before you select the **Copy policies (preview)** option on the **Azure Information Protection - Unified labeling** pane, be aware of the following:

- You cannot selectively choose policies and settings to copy. All policies (the **Global** policy and any scoped policies) are copied, and all settings that are supported as label policy settings are copied. If you already have a label policy with the same name, it will be overwritten with the policy settings in the Azure portal.

- Some advanced client settings are not copied because for the Azure Information Protection unified labeling client, these are supported as *label advanced settings* rather than policy settings. You can configure these label advanced settings with [Office 365 Security & Compliance Center PowerShell](./rms-client/clientv2-admin-guide-customizations.md#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell). The advanced client settings that are not copied:
    - [LabelbyCustomProperty](./rms-client/client-admin-guide-customizations.md#migrate-labels-from-secure-islands-and-other-labeling-solutions)
    - [LabelToSMIME](./rms-client/client-admin-guide-customizations.md#configure-a-label-to-apply-smime-protection-in-outlook)

- Unlike label migration where subsequent changes to labels are synchronized, the copy policies action doesn't synchronize any subsequent changes to your policies or policy settings. You can repeat the copy policy action after making changes in the Azure portal, and any existing policies and their settings will be overwritten again. Or, use the Set-LabelPolicy or Set-Label cmdlets with the *AdvancedSettings* parameter from Office 365 Security & Compliance Center PowerShell.

- The **Copy policies (Preview)** option is not available until unified labeling is activated for your tenant.

For more information about configuring the policy settings, advanced client settings, and label settings for the Azure Information Protection unified labeling client, see [Custom configurations for the Azure Information Protection unified labeling client](./rms-client/clientv2-admin-guide-customizations.md) from the admin guide.

### <a name="clients-and-services-that-support-unified-labeling"></a>Clients und Dienste, die einheitliche Bezeichnungen unterstützen

To confirm whether the clients and services you use support unified labeling, refer to their documentation to check whether they can use sensitivity labels that are published from one of the admin centers: Office 365 Security & Compliance Center, Microsoft 365 security center, or Microsoft 365 compliance center. 

##### <a name="clients-that-currently-support-unified-labeling-include"></a>Folgende Clients unterstützen derzeit einheitliche Bezeichnungen:

- The [Azure Information Protection unified labeling client for Windows](./rms-client/unifiedlabelingclient-version-release-history.md). For a comparison of this client with the Azure Information Protection client (classic), see [Compare the labeling clients for Windows computers](./rms-client/use-client.md#compare-the-labeling-clients-for-windows-computers).

- Apps von Office, die sich in verschiedenen Stadien der Verfügbarkeit befinden. For more information, see [What sensitivity label capabilities are supported in Office today?](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps#what-sensitivity-label-capabilities-are-supported-in-office-today) from the Office documentation.
    
- Apps von Softwarevertreibern und -herstellern, die das [Microsoft Azure Information Protection SDK](https://docs.microsoft.com/information-protection/develop/overview) verwenden.

##### <a name="services-that-currently-support-unified-labeling-include"></a>Folgende Dienste unterstützen derzeit einheitliche Bezeichnungen:

- [Power BI (in preview)](https://docs.microsoft.com/power-bi/admin/service-security-data-protection-overview)

- Office Online (in preview) and Outlook on the web

- SharePoint Online, OneDrive for Business, Microsoft Teams, and Office 365 groups (in preview)
    
    For more information, see [Use sensitivity labels with Microsoft Teams, Office 365 groups, and SharePoint sites (public preview)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites) and [Enable sensitivity labels for Office files in SharePoint and OneDrive (public preview)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files).

- Microsoft Defender Advanced Threat Protection

- Microsoft Cloud App Security
    
    Dieser Dienst unterstützt Bezeichnungen sowohl vor der Migration in den einheitlichen Bezeichnungsspeicher, als auch nach der Migration, und verwendet dabei die folgende Logik:
    
    - If the admin centers have the same labels as those in the Azure portal: Unified labels are retrieved from the admin centers. Wenn Sie diese Bezeichnungen in Cloud App Security auswählen möchten, muss mindestens eine Bezeichnung für mindestens einen Benutzer veröffentlicht worden sein.
    
    - If the admin centers don't have the same labels as those in the Azure portal: Unified labels are not used from the admin centers, and instead, labels are retrieved from the Azure portal.

- Dienste von Softwarevertreibern und -herstellern, die das [Microsoft Azure Information Protection SDK](https://docs.microsoft.com/information-protection/develop/overview) verwenden.

## <a name="next-steps"></a>Nächste Schritte

For additional guidance and tips from our Customer Experience team, see the following blog post: [Understanding Unified Labeling Migration](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Understanding-Unified-Labeling-migration/ba-p/783185).

Weitere Informationen zu Ihren migrierten Bezeichnungen, die nun in einem der Admin-Centers konfiguriert und veröffentlicht werden können, finden Sie unter [Übersicht über Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/sensitivity-labels).

If you haven't already done so, install the Azure Information Protection unified labeling client. For release information, an admin guide, and user guide, see [Azure Information Protection unified labeling client for Windows](./rms-client/aip-clientv2.md).
