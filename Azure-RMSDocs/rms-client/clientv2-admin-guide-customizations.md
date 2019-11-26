---
title: Custom configurations - Azure Information Protection unified labeling client
description: Information about customizing the Azure Information Protection unified labeling client for Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.subservice: v2client
ms.reviewer: maayan
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 1fcab238281326ff8e885f655a936392e1519eb1
ms.sourcegitcommit: fed1df1858f8316f7dd45e751c6910b444651a87
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74474376"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-unified-labeling-client"></a>Admin Guide: Custom configurations for the Azure Information Protection unified labeling client

>*Applies to: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 with SP1, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Instructions for: [Azure Information Protection unified labeling client for Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Use the following information for advanced configurations that you might need for specific scenarios or a subset of users when you manage the Azure Information Protection unified labeling client.

These settings require editing the registry or specifying advanced settings. The advanced settings use [Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

### <a name="how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell"></a>How to configure advanced settings for the client by using Office 365 Security & Compliance Center PowerShell

When you use Office 365 Security & Compliance Center PowerShell, you can configure advanced settings that support customizations for label policies and labels. Beispiele:

- The setting to display the Information Protection bar in Office apps is a ***label policy advanced setting***.
- The setting to specify a label color is a ***label advanced setting***.

In both cases, after you [connect to Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps), specify the *AdvancedSettings* parameter with the identity (name or GUID) of the policy or label, and specify key/value pairs in a [hash table](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables). Verwenden Sie die folgende Syntax:

For a label policy setting, single string value:

    Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key="value1,value2"}

For label policy settings, multiple string values for the same key:

    Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}

For a label setting, single string value:

    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key="value1,value2"}

For label settings, multiple string values for the same key:

    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}

To remove an advanced setting, use the same syntax but specify a null string value.


#### <a name="examples-for-setting-advanced-settings"></a>Examples for setting advanced settings

Example 1: Set a label policy advanced setting for a single string value:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}

Example 2: Set a label advanced setting for a single string value:

    Set-Label -Identity Internal -AdvancedSettings @{smimesign="true"}

Example 3: Set a label advanced setting for multiple string values:

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}

Example 4: Remove a label policy advanced setting by specifying a null string value:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions=""}

#### <a name="specifying-the-identity-for-the-label-policy-or-label"></a>Specifying the identity for the label policy or label

Specifying the label policy name for the PowerShell *Identity* parameter is straightforward because you see only one policy name in the admin center where you manage your label policies. However, for labels, you see both a **Name** and **Display name** in the admin centers. In some cases, the value for both will be the same but they can be different:

- **Name** is the original name of the label and it is unique across all your labels. If you change the name of your label after it is created, this value remains the same. For labels that have been migrated from Azure Information Protection, you might see the label ID of the label from the Azure portal.

- **Display name** is the name of the label that users see and it doesn't have to be unique across all your labels. For example, users see one **All Employees** sublabel for the **Confidential** label, and another **All Employees** sublabel for the **Highly Confidential** label. These sublabels both display the same name, but are not the same label and have different settings.

For configuring your label advanced settings, use the **Name** value. For example, to identify the label in the following picture, you would specify `-Identity "All Company"`:

![Use 'Name' rather than 'Display name' to identify a sensitivity label](../media/labelname_scc.png)

If you prefer to specify the label GUID, this value is not displayed in the admin center where you manage your labels. However, you can use the following Office 365 Security & Compliance Center PowerShell command to find this value:

    Get-Label | Format-Table -Property DisplayName, Name, Guid


#### <a name="order-of-precedence---how-conflicting-settings-are-resolved"></a>Order of precedence - how conflicting settings are resolved

Using one of the admin centers where you manage your sensitivity labels, you can configure the following label policy settings:

- **Apply this label by default to documents and emails**

- **Users must provide justification to remove a label or lower classification label**

- **Require users to apply a label to their email or document**

- **Provide users with a link to a custom help page**

When more than one label policy is configured for a user, each with potentially different policy settings, the last policy setting is applied according to the order of the policies in the admin center. For more information, see [Label policy priority (order matters)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#label-policy-priority-order-matters)

Label advanced settings follow the same logic for precedence: When a label is in multiple label policies and that label has advanced settings, the last advanced setting is applied according to the order of the policies in the admin center.

Label policy advanced settings are applied in the reverse order: With one exception, the advanced settings from the first policy are applied, according to the order of the policies in the admin center. The exception is the advanced setting *OutlookDefaultLabel*, which sets a different default label for Outlook. For this label policy advanced setting only, the last setting is applied according to the order of the policies in the admin center.

#### <a name="available-advanced-settings-for-label-policies"></a>Available advanced settings for label policies

Use the *AdvancedSettings* parameter with [New-LabelPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-labelpolicy?view=exchange-ps) and [Set-LabelPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-labelpolicy?view=exchange-ps).

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|AttachmentAction|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
|AttachmentActionTip|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments) 
|DisableMandatoryInOutlook|[Exempt Outlook messages from mandatory labeling](#exempt-outlook-messages-from-mandatory-labeling)
|EnableAudit|[Disable sending audit data to Azure Information Protection analytics](#disable-sending-audit-data-to-azure-information-protection-analytics)|
|EnableCustomPermissions|[Disable custom permissions in File Explorer](#disable-custom-permissions-in-file-explorer)|
|EnableCustomPermissionsForCustomProtectedFiles|[Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer) |
|EnableLabelByMailHeader|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|EnableLabelBySharePointProperties|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)
|HideBarByDefault|[Information Protection-Leiste in Office-Apps anzeigen](##display-the-information-protection-bar-in-office-apps)|
|LogMatchedContent|[Send information type matches to Azure Information Protection analytics](#send-information-type-matches-to-azure-information-protection-analytics)|
|OutlookBlockTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookBlockUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookDefaultLabel|[Festlegen einer anderen Standardbezeichnung für Outlook](#set-a-different-default-label-for-outlook)|
|OutlookJustifyTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookJustifyUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookRecommendationEnabled|[Die empfohlene Klassifizierung in Outlook aktivieren](#enable-recommended-classification-in-outlook)|
|OutlookOverrideUnlabeledCollaborationExtensions|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|PFileSupportedExtensions|[Change which file types to protect](#change-which-file-types-to-protect)|
|PostponeMandatoryBeforeSave|[Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|RemoveExternalContentMarkingInApp|[Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Add "Report an Issue" for users](#add-report-an-issue-for-users) ("Problem melden" für Benutzer hinzufügen)|
|RunAuditInformationTypesDiscovery|[Disable sending discovered sensitive information in documents to Azure Information Protection analytics](#disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics)|
|ScannerConcurrencyLevel|[Begrenzen der Anzahl der von der Überprüfung verwendeten Threads](#limit-the-number-of-threads-used-by-the-scanner)|

Example PowerShell command to check your label policy settings in effect for a label policy named "Global":

    (Get-LabelPolicy -Identity Global).settings

#### <a name="available-advanced-settings-for-labels"></a>Available advanced settings for labels

Use the *AdvancedSettings* parameter with [New-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-label?view=exchange-ps) and [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps).

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|color|[Specify a color for the label](#specify-a-color-for-the-label)|
|customPropertiesByLabel|[Apply a custom property when a label is applied](#apply-a-custom-property-when-a-label-is-applied)|
|DefaultSubLabelId|[Specify a default sublabel for a parent label](#specify-a-default-sublabel-for-a-parent-label) 
|labelByCustomProperties|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|SMimeEncrypt|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|
|SMimeSign|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|

Example PowerShell command to check your label settings in effect for a label named "Public":

    (Get-Label -Identity Public).settings

## <a name="display-the-information-protection-bar-in-office-apps"></a>Information Protection-Leiste in Office-Apps anzeigen

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

By default, users must select the **Show Bar** option from the **Sensitivity** button to display the Information Protection bar in Office apps. Use the **HideBarByDefault** key and set the value to **False** to automatically display this bar for users so that they can select labels from either the bar or the button. 

For the selected label policy, specify the following strings:

- Key: **HideBarByDefault**

- Wert: **FALSE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{HideBarByDefault="False"}

## <a name="exempt-outlook-messages-from-mandatory-labeling"></a>Exempt Outlook messages from mandatory labeling

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

By default, when you enable the label policy setting of **All documents and emails must have a label**, all saved documents and sent emails must have a label applied. When you configure the following advanced setting, the policy setting applies only to Office documents and not to Outlook messages.

For the selected label policy, specify the following strings:

- Key: **DisableMandatoryInOutlook**

- Wert: **TRUE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{DisableMandatoryInOutlook="True"}

## <a name="enable-recommended-classification-in-outlook"></a>Aktivieren der empfohlenen Klassifizierung in Outlook

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Wenn Sie eine Bezeichnung für die empfohlene Klassifizierung konfigurieren, werden Benutzer dazu aufgefordert, die empfohlene Bezeichnung in Word, Excel und PowerPoint anzunehmen oder abzulehnen. Diese Einstellung erweitert diese Bezeichnungsempfehlung, sodass sie auch in Outlook angezeigt wird.

For the selected label policy, specify the following strings:

- Schlüssel: **OutlookRecommendationEnabled**

- Wert: **TRUE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookRecommendationEnabled="True"}

## <a name="set-a-different-default-label-for-outlook"></a>Festlegen anderer Standardbezeichnung für Outlook

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

When you configure this setting, Outlook doesn't apply the default label that is configured as a policy setting for the option **Apply this label by default to documents and emails**. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden.

For the selected label policy, specify the following strings:

- Schlüssel: **OutlookDefaultLabel**

- Value: \<**label GUID**> or **None**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookDefaultLabel="None"}

## <a name="change-which-file-types-to-protect"></a>Change which file types to protect

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

By default, the Azure Information Protection unified labeling client protects all file types, and the scanner from the client protects only Office file types and PDF files.

You can change this default behavior for a selected label policy, by specifying the following:

- Key: **PFileSupportedExtensions**

- Value: **<string value>** 

Use the following table to identify the string value to specify:

| Zeichenfolgenwert| client| Scanner|
|-------------|-------|--------|
|\*|Default value: Apply protection to all file types|Apply protection to all file types|
|\<null value>| Apply protection to Office file types and PDF files| Default value: Apply protection to Office file types and PDF files|
|ConvertTo-Json(".jpg", ".png")|In addition to Office file types and PDF files, apply protection to the specified file name extensions | In addition to Office file types and PDF files, apply protection to the specified file name extensions

Example 1: PowerShell command for the unified client to protect only Office file types and PDF files, where your label policy is named "Client":

    Set-LabelPolicy -Identity Client -AdvancedSettings @{PFileSupportedExtensions=""}

Example 2:  PowerShell command for the scanner to protect all file types, where your label policy is named "Scanner":

    Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions="*"}

Example 3: PowerShell command for the scanner to protect .txt files and .csv files in addition to Office files and PDF files, where your label policy is named "Scanner":

    Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions=ConvertTo-Json(".txt", ".csv")}

With this setting, you can change which file types are protected but you cannot change the default protection level from native to generic. For example, for users running the unified labeling client, you can change the default setting so that only Office files and PDF files are protected instead of all file types. But you cannot change these file types to be generically protected with a .pfile file name extension.

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>„Not now“ („Nicht jetzt“) für Dokumente bei Verwendung der obligatorischen Bezeichnung entfernen

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

When you use the label policy setting of **All documents and emails must have a label**, users are prompted to select a label when they first save an Office document and when they send an email. Bei Office-Dokumenten können Benutzer **Not now** (nicht jetzt) wählen, um die Aufforderung zum Auswählen einer Bezeichnung vorübergehend zu schließen und zum Dokument zurückzukehren. Sie können das gespeicherte Dokument jedoch nicht schließen, ohne es zu bezeichnen. 

Wenn Sie diese Einstellung konfigurieren, wird die Option **Not now** (nicht jetzt) entfernt, sodass die Benutzer eine Bezeichnung wählen müssen, wenn das Dokument zum ersten Mal gespeichert wird.

For the selected label policy, specify the following strings:

- Schlüssel: **PostponeMandatoryBeforeSave**

- Wert: **FALSE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{PostponeMandatoryBeforeSave="False"}

## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen

This configuration uses policy [advanced settings](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Mit diesen Einstellungen können Sie textbasierte Kopf- und Fußzeilen in Dokumenten entfernen oder ersetzen, wenn diese optischen Kennzeichnungen von einer anderen Bezeichnungslösung angewendet wurden. For example, the old footer contains the name of an old label that you have now migrated to sensitivity labels to use a new label name and its own footer.

When the unified labeling client gets this configuration in its policy, the old headers and footers are removed or replaced when the document is opened in the Office app and any sensitivity label is applied to the document.

Diese Konfiguration wird für Outlook nicht unterstützt. Beachten Sie außerdem, dass die Verwendung mit Word, Excel und PowerPoint sich negativ auf die Leistung dieser Apps für Benutzer auswirken kann. Mithilfe der Konfiguration können Sie Einstellungen für jede einzelne Anwendung definieren, z.B. die Suche nach Text in Kopf- oder Fußzeilen von Word-Dokumenten, jedoch nicht von Excel-Tabellen oder PowerPoint-Präsentationen.

Because the pattern matching affects the performance for users, we recommend that you limit the Office application types (**W**ord, E**X**cel, **P**owerPoint) to just those that need to be searched.

For the selected label policy, specify the following strings:

- Key: **RemoveExternalContentMarkingInApp**

- Value: \<**Office-Anwendungstypen WXP**> 

Beispiele:

- Geben Sie **W** an, um nur Word-Dokumente zu durchsuchen.

- Geben Sie **WP** an, um Word-Dokumente und PowerPoint-Präsentationen zu durchsuchen.

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RemoveExternalContentMarkingInApp="WX"}

Sie benötigen dann mindestens eine weitere erweiterte Clienteinstellung, **ExternalContentMarkingToRemove**, um die Inhalte der Kopf- oder Fußzeile anzugeben und diese zu entfernen oder zu ersetzen.

### <a name="how-to-configure-externalcontentmarkingtoremove"></a>Konfigurieren von ExternalContentMarkingToRemove

Wenn Sie den Zeichenfolgenwert für den Schlüssel **ExternalContentMarkingToRemove** angeben, stehen drei Optionen zur Verfügung, die reguläre Ausdrücke verwenden:

- Partielle Übereinstimmung, um alles aus der Kopf- oder Fußzeile zu entfernen.
    
    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten diese Kopf- oder Fußzeilen vollständig entfernen. Geben Sie den Wert `*TEXT*` an.

- Vollständige Übereinstimmung, um nur bestimmte Wörter aus der Kopf- oder Fußzeile zu entfernen.
    
    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten nur das Wort **TEXT** entfernen, wodurch die Zeichenfolge der Kopf- oder Fußzeile **TO REMOVE** entspricht. Geben Sie den Wert `TEXT ` an.

- Vollständige Übereinstimmung, um alles aus der Kopf- oder Fußzeile zu entfernen.
    
    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten die Kopf- oder Fußzeilen entfernen, die genau diese Zeichenfolge enthalten. Geben Sie den Wert `^TEXT TO REMOVE$` an.
    

Der Musterabgleich für die angegebene Zeichenfolge berücksichtigt keine Groß- und Kleinschreibung. Die maximale Zeichenfolgenlänge beträgt 255 Zeichen.

Da einige Dokumente unsichtbare Zeichen oder andere Arten von Leerzeichen oder Tabstopps enthalten können, wird die Zeichenfolge, die Sie für einen Begriff oder einen Satz angeben, möglicherweise nicht erkannt. Geben Sie nach Möglichkeit immer ein einzelnes unterscheidendes Wort für den Wert an, und testen Sie die Ergebnisse, bevor Sie diese für die Produktion bereitstellen.

For the same label policy, specify the following strings:

- Key: **ExternalContentMarkingToRemove**

- Value: \<**zu vergleichende Zeichenfolge; als regulärer Ausdruck definiert**> 

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*TEXT*"}

#### <a name="multiline-headers-or-footers"></a>Mehrzeilige Kopf- oder Fußzeilen

Wenn der Text in einer Kopf- oder Fußzeile mehr als eine Zeile umfasst, erstellen Sie einen Schlüssel und einen Wert für jede Zeile. Angenommen, folgende Fußzeile mit zwei Zeilen ist vorhanden:

**The file is classified as Confidential**

**Label applied manually**

To remove this multiline footer, you create the following two entries for the same label policy:

- Key: **ExternalContentMarkingToRemove**

- Key Value 1: **\*Confidential***

- Key Value 2: **\*Label applied*** 

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*Confidential*,*Label applied*"}


#### <a name="optimization-for-powerpoint"></a>Optimierung für PowerPoint

In PowerPoint werden Fußzeilen als Formen implementiert. Wenn Sie vermeiden möchten, dass Formen entfernt werden, die den angegeben Text enthalten, jedoch keine Kopf- oder Fußzeilen sind, verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **PowerPointShapeNameToRemove**. Es wird empfohlen, diese Einstellung ebenfalls zu verwenden, um zu verhindern, dass der Text in allen Formen überprüft wird, denn dieser Prozess ist sehr ressourcenintensiv.

Wenn Sie diese zusätzliche erweiterte Clienteinstellung nicht angeben und PowerPoint im Schlüsselwert **RemoveExternalContentMarkingInApp** eingeschlossen ist, werden alle Formen auf den Text überprüft, den Sie im Wert **ExternalContentMarkingToRemove** angeben. 

So finden Sie den Namen der Form, die Sie als Kopf- oder Fußzeile verwenden:

1. Zeigen Sie in PowerPoint den Bereich **Auswahl** an: **Format** > **Anordnen** > **Auswahlbereich**.

2. Wählen Sie die Form auf der Folie aus, die die Kopf- oder Fußzeile enthält. Der Name der ausgewählten Form wird nun im Bereich **Auswahl** hervorgehoben.

Verwenden Sie den Namen der Form, um einen Zeichenfolgenwert für den Schlüssel **PowerPointShapeNameToRemove** anzugeben. 

Beispiel: Der Name der Form ist **fc**. Geben Sie den Wert `fc` an, um die Form mit diesem Namen zu entfernen.

- Key: **PowerPointShapeNameToRemove**

- Value: \<**Name der PowerPoint-Form**> 

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{PowerPointShapeNameToRemove="fc"}

When you have more than one PowerPoint shape to remove, specify as many values as you have shapes to remove.

Standardmäßig werden nur die Masterfolien auf Kopf- oder Fußzeilen überprüft. Wenn Sie diese Suche auf alle Folien ausweiten möchten (dieser Prozess ist jedoch wesentlich ressourcenintensiver), verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **RemoveExternalContentMarkingInAllSlides**:

- Key: **RemoveExternalContentMarkingInAllSlides**

- Wert: **TRUE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RemoveExternalContentMarkingInAllSlides="True"}


## <a name="disable-custom-permissions-in-file-explorer"></a>Disable custom permissions in File Explorer

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

By default, users see an option named **Protect with custom permissions** when they right-click in File Explorer and choose **Classify and protect**. This option lets them set their own protection settings that can override any protection settings that you might have included with a label configuration. Benutzer können außerdem eine Option zum Entfernen des Schutzes sehen. When you configure this setting, users do not see these options.

To configure this advanced setting, enter the following strings for the selected label policy:

- Schlüssel: **EnableCustomPermissions**

- Wert: **FALSE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}

## <a name="for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer"></a>Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

When you configure the advanced client setting to [disable custom permissions in File Explorer](#disable-custom-permissions-in-file-explorer), by default, users are not able to see or change custom permissions that are already set in a protected document.

However, there's another advanced client setting that you can specify so that in this scenario, users can see and change custom permissions for a protected document when they use File Explorer and right-click the file.

To configure this advanced setting, enter the following strings for the selected label policy:

- Key: **EnableCustomPermissionsForCustomProtectedFiles**

- Wert: **TRUE**

Example PowerShell command:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissionsForCustomProtectedFiles="True"}


## <a name="for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments"></a>Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht

This configuration uses policy [advanced settings](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

This setting is for when users attach labeled documents to an email, and do not label the email message itself. In this scenario, a label is automatically selected for them, based on the classification labels that are applied to the attachments. The highest classification label is selected.

Die Anlage muss eine physische Datei sein, es darf sich nicht um einen Link zu einer Datei handeln (beispielsweise um einen Link zu einer Datei in SharePoint oder OneDrive for Business).

You can configure this setting to **Recommended**, so that users are prompted to apply the selected label to their email message, with a customizable tooltip. Benutzer können die Empfehlung akzeptieren oder ablehnen. Or, you can configure this setting to **Automatic**, where the selected label is automatically applied but users can remove the label or select a different label before sending the email.

Note: When the attachment with the highest classification label is configured for protection with the setting of user-defined permissions:

- When the label's user-defined permissions include Outlook (Do Not Forward), that label is selected and Do Not Forward protection is applied to the email.
- When the label's user-defined permissions are just for Word, Excel, PowerPoint, and File Explorer, that label is not applied to the email message, and neither is protection.

To configure this advanced setting, enter the following strings for the selected label policy:

- Key 1: **AttachmentAction**

- Key Value 1: **Recommended** or **Automatic**

- Key 2: **AttachmentActionTip**

- Key Value 2: "\<customized tooltip>"

The customized tooltip supports a single language only.

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{AttachmentAction="Automatic"}

## <a name="add-report-an-issue-for-users"></a>Add "Report an Issue" for users ("Problem melden" für Benutzer hinzufügen)

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Wenn Sie die folgende erweiterte Clienteinstellung angeben, wird Benutzern die Option **Problem melden** angezeigt, die sie aus dem Clientdialogfeld **Hilfe und Feedback** auswählen können. Geben Sie eine HTTP-Zeichenfolge für den Link an. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. 

To configure this advanced setting, enter the following strings for the selected label policy:

- Key: **ReportAnIssueLink**

- Value: **\<HTTP string>**

Beispielwert für eine Website: `https://support.contoso.com`

Beispielwert für eine E-Mail-Adresse: `mailto:helpdesk@contoso.com`

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ReportAnIssueLink="mailto:helpdesk@contoso.com"}

## <a name="implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent"></a>Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben

This configuration uses policy [advanced settings](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Wenn Sie die folgenden erweiterten Clienteinstellungen erstellen und konfigurieren, werden Benutzern Popupmeldungen in Outlook angezeigt, die sie vor dem Senden einer E-Mail warnen können, oder sie nach einer Legitimierung fragen, warum sie eine E-Mail versenden, oder sie aus folgenden Gründen davon abhalten, eine E-Mail zu senden:

- **Die E-Mail oder der E-Mail-Anhang hat eine bestimmte Bezeichnung:**
    - Der Anhang kann einen beliebigen Dateityp haben

- **Die E-Mail oder der E-Mail-Anhang hat keine bestimmte Bezeichnung:**
    - Der Anhang kann ein Office-Dokument oder ein PDF-Dokument sein

When these conditions are met, the user sees a pop-up message with one of the following actions:

- **Warn**: The user can confirm and send, or cancel.

- **Justify**: The user is prompted for justification (predefined options or free-form).  Der Benutzer kann dann die E-Mail senden oder abbrechen. Der Legitimationstext wird in den X-Header der E-Mail geschrieben, sodass dieser von anderen Systemen gelesen werden kann. Zum Beispiel von Diensten, die der Verhinderung von Datenverlust dienen.

- **Block**: The user is prevented from sending the email while the condition remains. Die Nachricht beinhaltet den Grund dafür, warum die E-Mail blockiert wird, sodass der Benutzer das Problem aufheben kann. So kann er z.B. bestimmte Empfänger entfernen, oder der E-Mail eine Bezeichnung hinzufügen. 

When the popup-messages are for a specific label, you can configure exceptions for recipients by domain name.

> [!TIP]
> See the video [Azure Information Protection Outlook Popup Configuration](https://azure.microsoft.com/resources/videos/how-to-configure-azure-information-protection-popup-for-outlook/) for a walkthrough example of how to configure these settings.

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren für bestimme Bezeichnungen implementiert:

For the selected policy, create one or more of the following advanced settings with the following keys. For the values, specify one or more labels by their GUIDs, each one separated by a comma.

Example value for multiple label GUIDs as a comma-separated string: `dcf781ba-727f-4860-b3c1-73479e31912b,1ace2cc3-14bc-4142-9125-bf946a70542c,3e9df74d-3168-48af-8b11-037e3021813f`


- Warnmeldungen:
    
    - Key: **OutlookWarnUntrustedCollaborationLabel**
    
    - Value: \<**label GUIDs, comma-separated**>

- Legitimationsmeldungen:
    
    - Key: **OutlookJustifyUntrustedCollaborationLabel**
    
    - Value: \<**label GUIDs, comma-separated**>

- Blockiermeldungen:
    
    - Key: **OutlookBlockUntrustedCollaborationLabel**
    
    - Value: \<**label GUIDs, comma-separated**>


Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookWarnUntrustedCollaborationLabel="8faca7b8-8d20-48a3-8ea2-0f96310a848e,b6d21387-5d34-4dc8-90ae-049453cec5cf,bb48a6cb-44a8-49c3-9102-2d2b017dcead,74591a94-1e0e-4b5d-b947-62b70fc0f53a,6c375a97-2b9b-4ccd-9c5b-e24e4fd67f73"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyUntrustedCollaborationLabel="dc284177-b2ac-4c96-8d78-e3e1e960318f,d8bb73c3-399d-41c2-a08a-6f0642766e31,750e87d4-0e91-4367-be44-c9c24c9103b4,32133e19-ccbd-4ff1-9254-3a6464bf89fd,74348570-5f32-4df9-8a6b-e6259b74085b,3e8d34df-e004-45b5-ae3d-efdc4731df24"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockUntrustedCollaborationLabel="0eb351a6-0c2d-4c1d-a5f6-caa80c9bdeec,40e82af6-5dad-45ea-9c6a-6fe6d4f1626b"}

#### <a name="to-exempt-domain-names-for-pop-up-messages-configured-for-specific-labels"></a>To exempt domain names for pop-up messages configured for specific labels

For the labels that you've specified with these pop-up messages, you can exempt specific domain names so that users do not see the messages for recipients who have that domain name included in their email address. In diesem Fall werden die E-Mails problemlos gesendet. Wenn Sie mehrere Domänen angeben möchten, fügen Sie sie kommagetrennt als einzelne Zeichenfolge hinzu.

Eine übliche Konfiguration ist es, die Popupmeldungen nur für die Empfänger anzuzeigen, die nicht zu Ihrer Organisation gehören, oder die keine für Ihre Organisation autorisierte Partner sind. In diesem Fall geben Sie alle E-Mail-Domänen an, die von Ihrer Organisation und von Ihren Partnern verwendet werden.

For the same label policy, create the following advanced client settings and for the value, specify one or more domains, each one separated by a comma.

Beispielwert für mehrere Domänen als kommagetrennte Zeichenfolge: `contoso.com,fabrikam.com,litware.com`

- Warnmeldungen:
    
    - Key: **OutlookWarnTrustedDomains**
    
    - Wert: **\<** Domänenname, kommagetrennt **>**

- Legitimationsmeldungen:
    
    - Key: **OutlookJustifyTrustedDomains**
    
    - Wert: **\<** Domänenname, kommagetrennt **>**

- Blockiermeldungen:
    
    - Key: **OutlookBlockTrustedDomains**
    
    - Wert: **\<** Domänenname, kommagetrennt **>**

For example, you have specified the **OutlookBlockUntrustedCollaborationLabel** advanced client setting for the **Confidential \ All Employees** label. You now specify the additional advanced client setting of **OutlookJustifyTrustedDomains** and **contoso.com**. As a result, a user can send an email to john@sales.contoso.com when it is labeled **Confidential \ All Employees** but will be blocked from sending an email with the same label to a Gmail account.

Example PowerShell commands, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockTrustedDomains="gmail.com"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyTrustedDomains="contoso.com,fabrikam.com,litware.com"}

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-emails-or-attachments-that-dont-have-a-label"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren von E-Mails oder Anhängen implementiert, die keine Bezeichnung haben:

For the same label policy, create the following advanced client setting with one of the following values:

- Warnmeldungen:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Value: **Warn**

- Legitimationsmeldungen:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Value: **Justify**

- Blockiermeldungen:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Value: **Block**

- Diese Meldungen deaktivieren:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Value: **Off**


Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationAction="Warn"}


#### <a name="to-define-specific-file-name-extensions-for-the-warn-justify-or-block-pop-up-messages-for-email-attachments-that-dont-have-a-label"></a>To define specific file name extensions for the warn, justify, or block pop-up messages for email attachments that don't have a label

By default, the warn, justify, or block pop-up messages apply to all Office documents and PDF documents. You can refine this list by specifying which file name extensions should display the warn, justify, or block messages with an additional advanced setting and a comma-separated list of file name extensions.

Example value for multiple file name extensions to define as a comma-separated string: `.XLSX,.XLSM,.XLS,.XLTX,.XLTM,.DOCX,.DOCM,.DOC,.DOCX,.DOCM,.PPTX,.PPTM,.PPT,.PPTX,.PPTM`

In this example, an unlabeled PDF document will not result in warn, justify, or block pop-up messages.

For the same label policy, enter the following strings: 


- Key: **OutlookOverrideUnlabeledCollaborationExtensions**

- Value: **\<** file name extensions to display messages, comma separated **>**


Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookOverrideUnlabeledCollaborationExtensions=".PPTX,.PPTM,.PPT,.PPTX,.PPTM"}

#### <a name="to-specify-a-different-action-for-email-messages-without-attachments"></a>To specify a different action for email messages without attachments

By default, the value that you specify for OutlookUnlabeledCollaborationAction to warn, justify, or block pop-up messages applies to emails or attachments that don't have a label. You can refine this configuration by specifying another advanced setting for email messages that don't have attachments.

Erstellen Sie die folgende erweiterte Clienteinstellung mit einem der folgenden Werte:

- Warnmeldungen:
    
    - Key: **OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior**
    
    - Value: **Warn**

- Legitimationsmeldungen:
    
    - Key: **OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior**
    
    - Value: **Justify**

- Blockiermeldungen:
    
    - Key: **OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior**
    
    - Value: **Block**

- Diese Meldungen deaktivieren:
    
    - Key: **OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior**
    
    - Value: **Off**

If you don't specify this client setting, the value that you specify for OutlookUnlabeledCollaborationAction is used for unlabeled email messages without attachments as well as unlabeled email messages with attachments.

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior="Warn"}

## <a name="disable-sending-audit-data-to-azure-information-protection-analytics"></a>Disable sending audit data to Azure Information Protection analytics

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

The Azure Information Protection unified labeling client supports central reporting and by default, sends its audit data to [Azure Information Protection analytics](../reports-aip.md). For more information about what information is sent and stored, see the [Information collected and sent to Microsoft](../reports-aip.md#information-collected-and-sent-to-microsoft) section from the central reporting documentation.

To change this behavior so that this information is not sent by the unified labeling client, enter the following strings for the selected label policy:

- Key: **EnableAudit**

- Wert: **FALSE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableAudit="False"}


## <a name="disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics"></a>Disable sending discovered sensitive information in documents to Azure Information Protection analytics

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

When the Azure Information Protection unified labeling client is used in Office apps, it looks for sensitive information in documents when they are first saved. Providing the [EnableAudit](#disable-sending-audit-data-to-azure-information-protection-analytics) advanced setting is not set to **False**, any predefined and custom sensitive information types found are then sent to [Azure Information Protection analytics](../reports-aip.md).

To change this behavior so that sensitive information types found by the unified labeling client are not sent, enter the following strings for the selected label policy:

- Key: **RunAuditInformationTypesDiscovery**

- Wert: **FALSE**

If you set this advanced client setting, auditing information can still be sent from the client, but the information is limited to reporting when a user has accessed labeled content.

Beispiele:

- With this setting, you can see that a user accessed Financial.docx that is labeled **Confidential \ Sales**.

- Without this setting, you can see that Financial.docx contains 6 credit card numbers.
    
    - Wenn Sie zusätzlich [Inhaltsübereinstimmungen für umfassendere Analysen](../reports-aip.md#content-matches-for-deeper-analysis) aktivieren, sind außerdem die tatsächlichen Kreditkartennummern einsehbar.

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RunAuditInformationTypesDiscovery="False"}

## <a name="send-information-type-matches-to-azure-information-protection-analytics"></a>Send information type matches to Azure Information Protection analytics
 
This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

By default, the unified labeling client does not send content matches for sensitive info types to [Azure Information Protection analytics](../reports-aip.md). For more information about this additional information that can be sent, see the [Content matches for deeper analysis](../reports-aip.md#content-matches-for-deeper-analysis) section from the central reporting documentation.

To send content matches when sensitive information types are sent, create the following advanced client setting in a label policy: 

- Key: **LogMatchedContent**

- Wert: **TRUE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{LogMatchedContent="True"}

## <a name="limit-the-number-of-threads-used-by-the-scanner"></a>Begrenzen der Anzahl der von der Überprüfung verwendeten Threads

This configuration uses a policy [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Standardmäßig verwendet die Überprüfung alle verfügbaren Prozessorressourcen des Computers, auf dem der Überprüfungsdienst ausgeführt wird. If you need to limit the CPU consumption while this service is scanning, create the following advanced setting in a label policy. 

Geben Sie als Wert die Anzahl von gleichzeitigen Threads an, die von der Überprüfung parallel ausgeführt werden dürfen. Die Überprüfung verwendet für jede Datei, die überprüft wird, einen separaten Thread, daher definiert diese Drosselungskonfiguration auch die Anzahl von Dateien, die parallel überprüft werden können. 

Wenn Sie den Wert zu Testzwecken zum ersten Mal konfigurieren, empfehlen wir Ihnen, „2 pro Kern“ anzugeben und die Ergebnisse zu überwachen. Wenn Sie die Überprüfung z.B. auf einem Computer mit vier Kernen ausführen, legen Sie den Wert auf „8“ fest. Erhöhen oder verringern Sie den Wert nach Bedarf – je nachdem, welche Leistung Sie für den Überprüfungscomputer und die Überprüfungshäufigkeit benötigen. 

- Key: **ScannerConcurrencyLevel**

- Wert: **\<Anzahl von gleichzeitigen Threads>**

Example PowerShell command, where your label policy is named "Scanner":

    Set-LabelPolicy -Identity Scanner -AdvancedSettings @{ScannerConcurrencyLevel="8"}


## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren

This configuration uses a label [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

This configuration is not compatible with protected PDF files that have a .ppdf file name extension. These files cannot be opened by the client using File Explorer or PowerShell.

For Office documents that are labeled by Secure Islands, you can relabel these documents with a sensitivity label by using a mapping that you define. Mit dieser Methode können Sie auch Bezeichnungen aus anderen Lösungen wiederverwenden, wenn diese Bezeichnungen sich in Office-Dokumenten befinden. 

As a result of this configuration option, the new sensitivity label is applied by the Azure Information Protection unified labeling client as follows:

- For Office documents: When the document is opened in the desktop app, the new sensitivity label is shown as set and is applied when the document is saved.

- For PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) and [Set-AIPFileClassificiation](/powershell/module/azureinformationprotection/set-aipfileclassification) can apply the new sensitivity label.

- For File Explorer: In the Azure Information Protection dialog box, the new sensitivity label is shown but isn't set.

This configuration requires you to specify an advanced setting named **labelByCustomProperties** for each sensitivity label that you want to map to the old label. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Geben Sie einen Namen für die Migrationsregel an. Use a descriptive name that helps you to identify how one or more labels from your previous labeling solution should be mapped to sensitivity label.

Beachten Sie, dass durch diese Einstellung keine ursprüngliche Bezeichnung aus dem Dokument bzw. keine optische Kennzeichnung im Dokument entfernt wird, die von der ursprünglichen Bezeichnung möglicherweise angewendet wurde. To remove headers and footers, see the earlier section, [Remove headers and footers from other labeling solutions](#remove-headers-and-footers-from-other-labeling-solutions).

#### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Beispiel 1: Eine 1:1-Zuordnung des gleichen Bezeichnungsnamens

Requirement: Documents that have a Secure Islands label of "Confidential" should be relabeled as "Confidential" by Azure Information Protection.

In diesem Beispiel:

- Die Secure Islands-Bezeichnung lautet **Vertraulich** und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

The advanced setting:

- Key: **labelByCustomProperties**

- Value: **Secure Islands label is Confidential,Classification,Confidential**

Example PowerShell command, where your label is named "Confidential":

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Confidential,Classification,Confidential"}

#### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Beispiel 2: Eine 1:1-Zuordnung für einen anderen Bezeichnungsnamen

Requirement: Documents labeled as "Sensitive" by Secure Islands should be relabeled as "Highly Confidential" by Azure Information Protection.

In diesem Beispiel:

- Die Secure Islands-Bezeichnung lautet **Sensitive** (Sensibel) und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

The advanced setting:

- Key: **labelByCustomProperties**

- Value: **Secure Islands label is Sensitive,Classification,Sensitive**

Example PowerShell command, where your label is named "Highly Confidential":

    Set-Label -Identity "Highly Confidential" -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Sensitive,Classification,Sensitive"}

#### <a name="example-3-many-to-one-mapping-of-label-names"></a>Beispiel 3: n:1-Zuordnung von Bezeichnungsnamen

Requirement: You have two Secure Islands labels that include the word "Internal" and you want documents that have either of these Secure Islands labels to be relabeled as "General" by the Azure Information Protection unified labeling client.

In diesem Beispiel:

- Die Secure Islands-Bezeichnungen enthalten den Begriff **Internal** (intern) und sind in der benutzerdefinierten Eigenschaft namens **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

- Key: **labelByCustomProperties**

- Value: **Secure Islands label contains Internal,Classification,.\*Internal.\***

Example PowerShell command, where your label is named "General":

    Set-Label -Identity General -AdvancedSettings @{labelByCustomProperties="Secure Islands label contains Internal,Classification,.*Internal.*"}

#### <a name="example-4-multiple-rules-for-the-same-label"></a>Example 4: Multiple rules for the same label

When you need multiple rules for the same label, define multiple string values for the same key. 

In this example, the Secure Islands labels named "Confidential" and "Secret" are stored in the custom property named **Classification**, and you want the Azure Information Protection unified labeling client to apply the sensitivity label named "Confidential":

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}

### <a name="extend-your-label-migration-rules-to-emails"></a>Extend your label migration rules to emails

You can use your labelByCustomProperties advanced settings with Outlook emails in addition to Office documents by specifying an additional label policy advanced setting. However, this setting has a known negative impact on the performance of Outlook, so configure this additional setting only when you have a strong business requirement for it and remember to set it to a null string value when you have completed the migration from the other labeling solution.

To configure this advanced setting, enter the following strings for the selected label policy:

- Key: **EnableLabelByMailHeader**

- Wert: **TRUE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableLabelByMailHeader="True"}

### <a name="extend-your-label-migration-rules-to-sharepoint-properties"></a>Extend your label migration rules to SharePoint properties

You can use your labelByCustomProperties advanced settings with SharePoint properties that you might expose as columns to users.

This setting is supported when you use Word, Excel, and PowerPoint.

To configure this advanced setting, enter the following strings for the selected label policy:

- Key: **EnableLabelBySharePointProperties**

- Wert: **TRUE**

Example PowerShell command, where your label policy is named "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableLabelBySharePointProperties="True"}

## <a name="apply-a-custom-property-when-a-label-is-applied"></a>Apply a custom property when a label is applied

This configuration uses a label [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

There might be some scenarios when you want to apply one or more custom properties to a document or email message in addition to the metadata that's applied by a sensitivity label.

Beispiele:

- You are in the process of [migrating from another labeling solution](#migrate-labels-from-secure-islands-and-other-labeling-solutions), such as Secure Islands. For interoperability during the migration, you want sensitivity labels to also apply a custom property that is used by the other labeling solution.

- For your content management system (such as SharePoint or a document management solution from another vendor) you want to use a consistent custom property name with different values for the labels, and with user-friendly names instead of the label GUID.

For Office documents and Outlook emails that users label by using the Azure Information Protection unified labeling client, you can add one or more custom properties that you define. You can also use this method for the unified labeling client to display a custom property as a label from other solutions for content that isn't yet labeled by the unified labeling client.

As a result of this configuration option, any additional custom properties are applied by the Azure Information Protection unified labeling client as follows:

- For Office documents: When the document is labeled in the desktop app, the additional custom properties are applied when the document is saved.

- For Outlook emails: When the email message is labeled in Outlook, the additional properties are applied to the x-header when the email is sent.

- For PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) and [Set-AIPFileClassificiation](/powershell/module/azureinformationprotection/set-aipfileclassification) applies the additional custom properties when the document is labeled and saved. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) displays custom properties as the mapped label if a sensitivity label isn't applied.

- For File Explorer: When the user right-clicks the file and applies the label, the custom properties are applied.

This configuration requires you to specify an advanced setting named **customPropertiesByLabel** for each sensitivity label that you want to apply the additional custom properties. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[custom property name],[custom property value]`

#### <a name="example-1-add-a-single-custom-property-for-a-label"></a>Example 1: Add a single custom property for a label

Requirement: Documents that are labeled as "Confidential" by the Azure Information Protection unified labeling client should have the additional custom property named "Classification" with the value of "Secret".

In diesem Beispiel:

- The sensitivity label is named **Confidential** and creates a custom property named **Classification** with the value of **Secret**.

The advanced setting:

- Key: **customPropertiesByLabel**

- Value: **Classification,Secret**

Example PowerShell command, where your label is named "Confidential":

    Set-Label -Identity Confidential -AdvancedSettings @{customPropertiesByLabel="Classification,Secret"}

#### <a name="example-2-add-multiple-custom-properties-for-a-label"></a>Example 2: Add multiple custom properties for a label

To add more than one custom property for the same label, you need to define multiple string values for the same key.

Example PowerShell command, where your label is named "General" and you want to add one custom property named **Classification** with the value of **General** and a second custom property named **Sensitivity** with the value of **Internal**:

    Set-Label -Identity General -AdvancedSettings @{customPropertiesByLabel=ConvertTo-Json("Classification,General", "Sensitivity,Internal")}

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden

This configuration uses label [advanced settings](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Use these settings only when you have a working [S/MIME deployment](https://docs.microsoft.com/microsoft-365/security/office-365-security/s-mime-for-message-signing-and-encryption) and want a label to automatically apply this protection method for emails rather than Rights Management protection from Azure Information Protection. Der resultierende Schutz ist derselbe wie bei der manuellen Auswahl von S/MIME-Optionen in Outlook.

To configure an advanced setting for an S/MIME digital signature, enter the following strings for the selected label:

- Key: **SMimeSign**

- Wert: **TRUE**

To configure an advanced setting for  S/MIME encryption, enter the following strings for the selected label:

- Key: **SMimeEncrypt**

- Wert: **TRUE**

If the label you specify is configured for encryption, for the Azure Information Protection unified labeling client, S/MIME protection replaces the Rights Management protection only in Outlook. The general availability version of the unified labeling client continues to use the encryption settings specified for the label in the admin center. For Office apps with built-in labeling, these do not apply the S/MIME protection but instead, apply Do Not Forward protection.

If you want the label to be visible in Outlook only, configure the label to apply encryption to **Only email messages in Outlook**.

Example PowerShell commands, where your label is named "Recipients Only":

    Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeSign="True"}

    Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeEncrypt="True"}

## <a name="specify-a-default-sublabel-for-a-parent-label"></a>Specify a default sublabel for a parent label

This configuration uses a label [advanced setting](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

When you add a sublabel to a label, users can no longer apply the parent label to a document or email. By default, users select the parent label to see the sublabels that they can apply, and then select one of those sublabels. If you configure this advanced setting, when users select the parent label, a sublabel is automatically selected and applied for them: 

- Key: **DefaultSubLabelId**

- Value: \<sublabel GUID>

Example PowerShell command, where your parent label is named "Confidential" and the "All Employees" sublabel has a GUID of 8faca7b8-8d20-48a3-8ea2-0f96310a848e:

    Set-Label -Identity "Confidential" -AdvancedSettings @{DefaultSubLabelId="8faca7b8-8d20-48a3-8ea2-0f96310a848e"}


## <a name="specify-a-color-for-the-label"></a>Specify a color for the label

This configuration uses label [advanced settings](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) that you must configure by using Office 365 Security & Compliance Center PowerShell.

Use this advanced setting to set a color for a label. To specify the color, enter a hex triplet code for the red, green, and blue (RGB) components of the color. For example, #40e0d0 is the RGB hex value for turquoise.

If you need a reference for these codes, you'll find a helpful table from the [\<color>](https://developer.mozilla.org/docs/Web/CSS/color_value) page from the MSDN web docs. You also find these codes in many applications that let you edit pictures. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

To configure the advanced setting for a label's color, enter the following strings for the selected label:

- Key: **color**

- Value: \<RGB hex value>

Example PowerShell command, where your label is named "Public":

    Set-Label -Identity Public -AdvancedSettings @{color="#40e0d0"}

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In a production environment, users wouldn't usually need to sign in as a different user when they are using the Azure Information Protection unified labeling client. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

You can verify which account you're currently signed in as by using the **Microsoft Azure Information Protection** dialog box: Open an Office application and on the **Home** tab, select the **Sensitivity** button, and then select **Help and feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. A symptom of using the wrong account includes failing to download the labels, or not seeing the labels or behavior that you expect.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. If you do not see a prompt in your Office application to sign in to the Azure Information Protection service, return to the **Microsoft Azure Information Protection** dialog box and select **Sign in** from the updated **Client status** section.

Weiterhin gilt:

- If the Azure Information Protection unified labeling client is still signed in with the old account after completing these steps, delete all cookies from Internet Explorer, and then repeat steps 1 and 2.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich bei Windows abmelden und mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Tokendatei gelöscht haben. The Azure Information Protection unified labeling client then automatically authenticates by using your currently signed in user account.

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- You can use the **Reset settings** option from **Help and Feedback** to sign out and delete the currently downloaded labels and policy settings from the Office 365 Security & Compliance Center, the Microsoft 365 Security center, or the Microsoft 365 Compliance center.


## <a name="support-for-disconnected-computers"></a>Unterstützung für getrennte Computer

> [!IMPORTANT]
> Disconnected computers are supported for the following labeling scenarios only: File Explorer, PowerShell, and the scanner. To label documents in your Office apps, you must have connectivity to the internet.

By default, the Azure Information Protection unified labeling client automatically tries to connect to the internet to download the labels and label policy settings from your labeling management center: The Office 365 Security & Compliance Center, the Microsoft 365 security center, or the Microsoft 365 compliance center. If you have computers that cannot connect to the internet for a period of time, you can export and copy files that manually manages the policy for the unified labeling client.

Anweisungen:

1. Choose or create a user account in Azure AD that you will use to download labels and policy settings that you want to use on your disconnected computer.

2. As an additional label policy setting for this account, [disable sending audit data to Azure Information Protection analytics](#disable-sending-audit-data-to-azure-information-protection-analytics) by using the **EnableAudit** advanced setting.
    
    We recommend this step because if the disconnected computer does have periodic internet connectivity, it will send logging information to Azure Information Protection analytics that includes the user name from step 1. That user account might be different from the local account you're using on the disconnected computer.

3. From a computer with internet connectivity that has the unified labeling client installed and signed in with the user account from step 1, download the labels and policy settings.

4. From this computer, export the log files.
    
    For example, run the [Export-AIPLogs](https://docs.microsoft.com/powershell/module/azureinformationprotection/export-aiplogs) cmdlet, or use the **Export Logs** option from the client's [Help and Feedback](clientv2-admin-guide.md#installing-and-supporting-the-azure-information-protection-unified-labeling-client) dialog box. 
    
    The log files are exported as a single compressed file.

5.  Open the compressed file, and from the MSIP folder, copy any files that have a .xml file name extension.

6. Paste these files into the **%localappdata%\Microsoft\MSIP** folder on the disconnected computer.

7. If your chosen user account is one that usually connects to the internet, enable sending audit data again, by setting the **EnableAudit** value to **True**.

8. For the disconnected computer to protect files, reprotect files, remove protection from files, or to inspect protected files: On the disconnected computer, run the [Set-AIPAuthentication](/powershell/module/azureinformationprotection/set-aipauthentication) cmdlet with the *DelegatedUser* parameter and specify the user account from step 1 to set the user context. Beispiele:
    
        Set-AIPAuthentication -TenantId "9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a" -DelegatedUser offlineuser@contoso.com

Be aware that if a user on this computer selects the **Reset Settings** option from [Help and feedback](clientv2-admin-guide.md#help-and-feedback-section), this action deletes the policy files and renders the client inoperable until you manually replace the files or the client connects to the internet and downloads the files.

If your disconnected computer is running the Azure Information Protection scanner, there are additional configuration steps you must take. For more information, see [Restriction: The scanner server cannot have internet connectivity](../deploy-aip-scanner.md#restriction-the-scanner-server-cannot-have-internet-connectivity) from the scanner deployment instructions.

## <a name="change-the-local-logging-level"></a>Ändern des lokalen Protokolliergrads

By default, the Azure Information Protection unified labeling client writes client log files to the **%localappdata%\Microsoft\MSIP** folder. Diese Dateien dienen zur Problembehandlung durch den Microsoft-Support.
 
To change the logging level for these files, locate the following value name in the registry and set the value data to the required logging level:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\LogLevel**

Legen Sie den Protokolliergrad auf einen der folgenden Werte fest:

- **Off**: No local logging.

- **Error**: Errors only.

- **Warn**: Errors and warnings.

- **Info**: Minimum logging, which includes no event IDs (the default setting for the scanner).

- **Debug**: Full information.

- **Trace**: Detailed logging (the default setting for clients).

This registry setting does not change the information that's sent to Azure Information Protection for [central reporting](../reports-aip.md).

## <a name="next-steps"></a>Nächste Schritte
Now that you've customized the Azure Information Protection unified labeling client, see the following resources for additional information that you might need to support this client:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
