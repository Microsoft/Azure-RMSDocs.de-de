---
title: Benutzerdefinierte Konfigurationen-Azure Information Protection Unified-Beschriftungs Client
description: Informationen zum Anpassen des Azure Information Protection Unified Bezeichnung-Clients für Windows.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/30/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.subservice: v2client
ms.reviewer: maayan
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ee77dc60e1300f494508479925963178413c48d9
ms.sourcegitcommit: 129370798e7d1b5baa110b2d7b2f24abd3cad5c8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "89316847"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-unified-labeling-client"></a>Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client für einheitliche Bezeichnungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> **Kunden mit erweitertem Microsoft-Support für Windows 7 und Office 2010 können auch Azure Information Protection Unterstützung für diese Versionen erhalten. Wenden Sie sich an Ihren Support, um ausführliche Informationen zu erhalten.*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie möglicherweise für bestimmte Szenarien oder eine Teilmenge von Benutzern benötigen, wenn Sie den Azure Information Protection Unified Bezeichnung-Client verwalten.

Für diese Einstellungen müssen Sie die Registrierung bearbeiten oder erweiterte Einstellungen angeben. Die erweiterten Einstellungen verwenden [Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

### <a name="how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell"></a>Konfigurieren erweiterter Einstellungen für den Client mithilfe von Office 365 Security & Compliance Center PowerShell

Wenn Sie Office 365 Security & Compliance Center PowerShell verwenden, können Sie erweiterte Einstellungen konfigurieren, die Anpassungen für Bezeichnungs Richtlinien und Bezeichnungen unterstützen. Beispiel:

- Die Einstellung zum Anzeigen der Information Protection Leiste in Office-Apps ist eine ***Erweiterte Einstellung der Bezeichnung "Bezeichnung***".
- Die Einstellung zum Angeben einer Bezeichnungs Farbe ist eine ***Erweiterte Einstellung***für die Bezeichnung.

Geben Sie in beiden Fällen nach dem [Herstellen einer Verbindung mit Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps)den Parameter *advancedsettings* mit der Identität (Name oder GUID) der Richtlinie oder Bezeichnung an, und geben Sie Schlüssel-Wert-Paare in einer [Hash Tabelle](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables)an. Verwenden Sie die folgende Syntax:

Für eine Bezeichnungs Richtlinieneinstellung ist ein einzelner Zeichen folgen Wert:

```PowerShell
Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key="value1,value2"}
```

Für Bezeichnungs Richtlinien Einstellungen werden mehrere Zeichen folgen Werte für den gleichen Schlüssel angezeigt:

```PowerShell
Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}
```

Für eine Bezeichnungs Einstellung lautet der Wert einer einzelnen Zeichenfolge:

```PowerShell
Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key="value1,value2"}
```

Für Bezeichnungs Einstellungen werden mehrere Zeichen folgen Werte für denselben Schlüssel angezeigt:

```PowerShell
Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}
```

Verwenden Sie die gleiche Syntax, und geben Sie einen NULL-Zeichen folgen Wert an, um eine erweiterte Einstellung zu entfernen.

> [!IMPORTANT]
> Durch die Verwendung von Leerzeichen in der Zeichenfolge wird die Anwendung der Bezeichnungen verhindert. 

#### <a name="examples-for-setting-advanced-settings"></a>Beispiele für das Festlegen von erweiterten Einstellungen

Beispiel 1: Festlegen der erweiterten Einstellung für die Bezeichnung "Bezeichnung" für einen einzelnen Zeichen folgen Wert:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}
```

Beispiel 2: Festlegen der erweiterten Einstellung für die Bezeichnung für einen einzelnen Zeichen folgen Wert:

```PowerShell
Set-Label -Identity Internal -AdvancedSettings @{smimesign="true"}
```

Beispiel 3: Festlegen der erweiterten Einstellung für die Bezeichnung für mehrere Zeichen folgen Werte:

```PowerShell
Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}
```

Beispiel 4: Entfernen einer erweiterten Einstellung für eine Bezeichnungs Richtlinie durch Angeben eines NULL-Zeichen folgen Werts:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions=""}
```

#### <a name="specifying-the-identity-for-the-label-policy-or-label"></a>Angeben der Identität für die Bezeichnungs Richtlinie oder-Bezeichnung

Das Angeben des Namens der Bezeichnungs Richtlinie für den PowerShell- *Identitäts* Parameter ist einfach, da im Admin Center nur ein Richtlinien Name angezeigt wird, in dem Sie Ihre Bezeichnungs Richtlinien verwalten. Für Bezeichnungen werden jedoch sowohl ein **Name** als auch ein **Anzeige Name** in den Admin Centers angezeigt. In einigen Fällen ist der Wert für beide identisch, aber Sie können sich unterscheiden:

- **Name** ist der ursprüngliche Name der Bezeichnung, der in allen Bezeichnungen eindeutig ist. Wenn Sie den Namen der Bezeichnung nach der Erstellung ändern, bleibt dieser Wert unverändert. Bei Bezeichnungen, die von Azure Information Protection migriert wurden, wird möglicherweise die Bezeichnungs-ID der Bezeichnung aus der Azure-Portal angezeigt.

- Der **Anzeige Name** ist der Name der Bezeichnung, die Benutzern angezeigt wird, und Sie muss in allen Bezeichnungen nicht eindeutig sein. Beispielsweise sehen **Benutzer eine unter** geordnete Bezeichnung für " **vertraulich** " und eine andere **untergeordnete** Bezeichnung für die Bezeichnung " **streng vertraulich** ". Diese untergeordneten Bezeichnungen sehen beide denselben Namen, sind jedoch nicht die gleiche Bezeichnung und haben andere Einstellungen.

Verwenden Sie zum Konfigurieren der erweiterten Einstellungen für die Bezeichnung den Wert " **Name** ". Um z. b. die Bezeichnung in der folgenden Abbildung zu identifizieren, geben Sie Folgendes an `-Identity "All Company"` :

![Verwenden Sie "Name" anstelle von "Anzeige Name", um eine Vertraulichkeits Bezeichnung zu identifizieren.](../media/labelname_scc.png)

Wenn Sie die GUID der Bezeichnung angeben möchten, wird dieser Wert nicht im Admin Center angezeigt, in dem Sie Ihre Bezeichnungen verwalten. Sie können jedoch den folgenden PowerShell-Befehl von Office 365 Security & Compliance Center verwenden, um diesen Wert zu finden:

```PowerShell
Get-Label | Format-Table -Property DisplayName, Name, Guid
```

#### <a name="order-of-precedence---how-conflicting-settings-are-resolved"></a>Rangfolge: so werden widersprüchliche Einstellungen aufgelöst

Mit einem der Admin Center, in dem Sie Ihre Vertraulichkeits Bezeichnungen verwalten, können Sie die folgenden Bezeichnungs Richtlinien Einstellungen konfigurieren:

- **Diese Bezeichnung standardmäßig auf Dokumente und e-Mails anwenden**

- **Benutzer müssen eine Begründung angeben, um eine Bezeichnung oder eine niedrigere Klassifizierungs Bezeichnung zu entfernen.**

- **Erzwingen, dass Benutzer eine Bezeichnung auf Ihre e-Mail oder Ihr Dokument anwenden**

- **Bereitstellen eines Links zu einer benutzerdefinierten Hilfeseite für Benutzer**

Wenn für einen Benutzer mehr als eine Bezeichnungs Richtlinie konfiguriert ist, von denen jede möglicherweise unterschiedliche Richtlinien Einstellungen hat, wird die letzte Richtlinien Einstellung gemäß der Reihenfolge der Richtlinien im Admin Center angewendet. Weitere Informationen finden Sie unter [Bezeichnung der Richtlinien Priorität (Reihenfolge wichtig)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels#label-policy-priority-order-matters) .

Erweiterte Einstellungen für Bezeichnung befolgen die gleiche Logik für Vorrang: Wenn sich eine Bezeichnung in mehreren Bezeichnungs Richtlinien befindet und diese Bezeichnung Erweiterte Einstellungen aufweist, wird die letzte erweiterte Einstellung gemäß der Reihenfolge der Richtlinien im Admin Center angewendet.

Die erweiterten Einstellungen für die Bezeichnungs Richtlinie werden in umgekehrter Reihenfolge angewendet: mit einer Ausnahme werden die erweiterten Einstellungen der ersten Richtlinie entsprechend der Reihenfolge der Richtlinien im Admin Center angewendet. Bei der Ausnahme handelt es sich um die erweiterte Einstellung *outlookdefaultlabel*, mit der eine andere Standard Bezeichnung für Outlook festgelegt wird. Bei dieser Einstellung für die erweiterte Bezeichnung "Bezeichnung" wird die letzte Einstellung gemäß der Reihenfolge der Richtlinien im Admin Center angewendet.


#### <a name="available-advanced-settings-for-label-policies"></a>Verfügbare erweiterte Einstellungen für Bezeichnungs Richtlinien

Verwenden Sie den *advancedsettings* -Parameter mit [New-labelpolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-labelpolicy?view=exchange-ps) und [Set-labelpolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-labelpolicy?view=exchange-ps).

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|Additionalpprefixextensions|[Unterstützung für das Ändern von \<EXT> . Pfile in P mit \<EXT> dieser erweiterten Eigenschaft](#additionalpprefixextensions)
|Attachmentaction|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
|Attachmentaktiontip|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments) 
|Disablemandatoryinoutlook|[Ausschließen von Outlook-Nachrichten von der obligatorischen Bezeichnung](#exempt-outlook-messages-from-mandatory-labeling)
|EnableAudit|[Deaktivieren des Sendens von Überwachungsdaten an Azure Information Protection Analytics](#disable-sending-audit-data-to-azure-information-protection-analytics)|
|Enablecontainersupport|[Entfernen des Schutzes von PST-, rar-, 7zip-und MSG-Dateien aktivieren](#enable-removal-of-protection-from-compressed-files)
|EnableCustomPermissions|[Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer](#disable-custom-permissions-in-file-explorer)|
|EnableCustomPermissionsForCustomProtectedFiles|[Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer) |
|Enablelabelbymailheader|[Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|Enablelabelbysharepointproperties|[Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren](#migrate-labels-from-secure-islands-and-other-labeling-solutions)
|Hidebarbydefault|[Information Protection-Leiste in Office-Apps anzeigen](#display-the-information-protection-bar-in-office-apps)|
|LogMatchedContent|[Senden von Informationstypen Übereinstimmungen an Azure Information Protection Analytics](#send-information-type-matches-to-azure-information-protection-analytics)|
|Outlookblocktreuhänddomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookBlockUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookDefaultLabel|[Festlegen einer anderen Standardbezeichnung für Outlook](#set-a-different-default-label-for-outlook)|
|Outlookjustifytreuhänddomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookJustifyUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookRecommendationEnabled|[Die empfohlene Klassifizierung in Outlook aktivieren](#enable-recommended-classification-in-outlook)|
|Outlookoverridkollaborationextensions|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|Outlookunlabeledcollaborationaktionoverridemailbodybehavior|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|Outlookwarntreuddomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|Pfilesupportedextensions|[Ändern der zu schützenden Dateitypen](#change-which-file-types-to-protect)|
|PostponeMandatoryBeforeSave|[Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|RemoveExternalContentMarkingInApp|[Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Add "Report an Issue" for users ("Problem melden" für Benutzer hinzufügen)](#add-report-an-issue-for-users)|
|RunPolicyInBackground|[Aktivieren der dauerhaft im Hintergrund ausgeführten Klassifizierung](#turn-on-classification-to-run-continuously-in-the-background)
|ScannerConcurrencyLevel|[Begrenzen der Anzahl der von der Überprüfung verwendeten Threads](#limit-the-number-of-threads-used-by-the-scanner)|
|Scannerssattributestoskip | [Dateien während Scans in Abhängigkeit von Dateiattributen überspringen oder ignorieren](#skip-or-ignore-files-during-scans-depending-on-file-attributes)
|Usecopyandkonservientschsowner | [Beibehalten von NTFS-Besitzern während der Bezeichnung](#preserve-ntfs-owners-during-labeling-public-preview)

PowerShell-Beispiel Befehl zum Überprüfen Ihrer Bezeichnungs Richtlinien Einstellungen für eine Bezeichnungs Richtlinie mit dem Namen "Global":

```PowerShell
(Get-LabelPolicy -Identity Global).settings
```

#### <a name="available-advanced-settings-for-labels"></a>Verfügbare erweiterte Einstellungen für Bezeichnungen

Verwenden Sie den *advancedsettings* -Parameter mit [New-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-label?view=exchange-ps) und [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps).

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|color|[Farbe für die Bezeichnung angeben](#specify-a-color-for-the-label)|
|custompropertiesbylabel|[Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird](#apply-a-custom-property-when-a-label-is-applied)|
|Defaultsublabelid|[Festlegen einer Standard untergeordneten Bezeichnung für eine übergeordnete Bezeichnung](#specify-a-default-sublabel-for-a-parent-label) 
|labelbycustomproperties|[Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|Smimeverschlüsseln|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|
|Smimesign|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|

PowerShell-Beispiel Befehl zum Überprüfen Ihrer Bezeichnungs Einstellungen für eine Bezeichnung mit dem Namen "Public":

```PowerShell
(Get-Label -Identity Public).settings
```

## <a name="display-the-information-protection-bar-in-office-apps"></a>Information Protection-Leiste in Office-Apps anzeigen

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig müssen Benutzer die Option **Leiste anzeigen** auf der **Vertraulichkeits** Schaltfläche auswählen, um die Information Protection Leiste in Office-Apps anzuzeigen. Verwenden Sie den **hidebarbydefault** -Schlüssel, und legen Sie den Wert auf " **false** " fest, um diese Leiste für Benutzer automatisch anzuzeigen, damit Sie Bezeichnungen aus der Leiste oder der Schaltfläche auswählen können. 

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Schlüssel: **hidebarbydefault**

- Wert: **FALSE**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{HideBarByDefault="False"}
```

## <a name="exempt-outlook-messages-from-mandatory-labeling"></a>Ausschließen von Outlook-Nachrichten von der obligatorischen Bezeichnung

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die Bezeichnungs Richtlinien Einstellung für **alle Dokumente aktivieren und e-Mails über eine Bezeichnung verfügen müssen**, muss für alle gespeicherten Dokumente und gesendeten e-Mails standardmäßig eine Bezeichnung angewendet werden. Wenn Sie die folgende erweiterte Einstellung konfigurieren, gilt die Richtlinien Einstellung nur für Office-Dokumente und nicht für Outlook-Nachrichten.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Schlüssel: **disablemandatoryinoutlook**

- Wert: **true**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{DisableMandatoryInOutlook="True"}
```

## <a name="enable-recommended-classification-in-outlook"></a>Aktivieren der empfohlenen Klassifizierung in Outlook

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie eine Bezeichnung für die empfohlene Klassifizierung konfigurieren, werden Benutzer dazu aufgefordert, die empfohlene Bezeichnung in Word, Excel und PowerPoint anzunehmen oder abzulehnen. Diese Einstellung erweitert diese Bezeichnungsempfehlung, sodass sie auch in Outlook angezeigt wird.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Schlüssel: **OutlookRecommendationEnabled**

- Wert: **true**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookRecommendationEnabled="True"}
```

## <a name="enable-removal-of-protection-from-compressed-files"></a>Entfernen des Schutzes von komprimierten Dateien aktivieren

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie diese Einstellung konfigurieren, wird das  [PowerShell](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-powershell) -Cmdlet **Set-aipfilelabel** aktiviert, um das Entfernen des Schutzes von PST-, rar-, 7zip-und MSG-Dateien zu ermöglichen.

- Schlüssel: **enablecontainersupport**

- Wert: **true**

Beispiel-PowerShell-Befehl, bei dem Ihre Richtlinie aktiviert ist:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableContainerSupport="True"}
```

## <a name="set-a-different-default-label-for-outlook"></a>Festlegen anderer Standardbezeichnung für Outlook

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie diese Einstellung konfigurieren, wendet Outlook nicht die Standard Bezeichnung an, die als Richtlinien Einstellung für die Option **diese Bezeichnung standardmäßig auf Dokumente und e-Mails anwenden**konfiguriert ist. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Schlüssel: **OutlookDefaultLabel**

- Wert: \<**label GUID**> oder **None**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookDefaultLabel="None"}
```

## <a name="change-which-file-types-to-protect"></a>Ändern der zu schützenden Dateitypen

Diese Konfigurationen verwenden eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig schützt der Azure Information Protection Unified Bezeichnung-Client alle Dateitypen, und der Scanner vom Client schützt nur Office-Dateitypen und PDF-Dateien.

Sie können dieses Standardverhalten für eine ausgewählte Bezeichnungs Richtlinie ändern, indem Sie einen der folgenden Werte angeben:

### <a name="pfilesupportedextension"></a>Pfilesupportedextension

- Schlüssel: **pfilesupportedextensions**

- Wert **\<string value>** 

Verwenden Sie die folgende Tabelle, um den angegebenen Zeichen folgen Wert zu identifizieren:

| Zeichenfolgenwert| Client| Scanner|
|-------------|-------|--------|
|\*|Standardwert: Schutz auf alle Dateitypen anwenden|Anwenden von Schutz auf alle Dateitypen|
|\<null value>| Anwenden von Schutz auf Office-Dateitypen und PDF-Dateien| Standardwert: Anwenden von Schutz auf Office-Dateitypen und PDF-Dateien|
|ConvertTo-JSON (". jpg", ". png")|Zusätzlich zu den Office-Dateitypen und PDF-Dateien, wenden Sie den Schutz auf die angegebenen Dateinamen Erweiterungen an. | Zusätzlich zu den Office-Dateitypen und PDF-Dateien, wenden Sie den Schutz auf die angegebenen Dateinamen Erweiterungen an.

Beispiel 1: PowerShell-Befehl für den Unified Client zum Schutz von nur Office-Dateitypen und PDF-Dateien, bei denen die Bezeichnung "Client" lautet:

```PowerShell
Set-LabelPolicy -Identity Client -AdvancedSettings @{PFileSupportedExtensions=""}
```

Beispiel 2: PowerShell-Befehl für die Überprüfung, um alle Dateitypen zu schützen, deren Bezeichnung "Scanner" lautet:

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions="*"}
```

Beispiel 3: PowerShell-Befehl für die Überprüfung, um TXT-Dateien und CSV-Dateien zusätzlich zu Office-Dateien und PDF-Dateien zu schützen, wobei die Bezeichnung "Scanner" lautet:

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{PFileSupportedExtensions=ConvertTo-Json(".txt", ".csv")}
```

Mit dieser Einstellung können Sie ändern, welche Dateitypen geschützt sind, aber Sie können die Standardschutz Ebene nicht von "nativ" in "generisch" ändern. Beispielsweise können Sie für Benutzer, die den Unified-Bezeichnungs Client ausführen, die Standardeinstellung so ändern, dass nur Office-Dateien und PDF-Dateien anstelle aller Dateitypen geschützt werden. Sie können diese Dateitypen jedoch nicht so ändern, dass Sie generisch durch die Dateinamenerweiterung ". Pfile" geschützt werden.

### <a name="additionalpprefixextensions"></a>Additionalpprefixextensions

Der Unified-Bezeichnungs Client unterstützt das Ändern von \<EXT> . Pfile in P \<EXT> mithilfe der erweiterten Eigenschaft **additionalpprefixextensions**. Diese erweiterte Eigenschaft wird mit einem Rechtsklick, PowerShell und Scanner unterstützt. Alle apps weisen ein ähnliches Verhalten auf.   

- Schlüssel: **additionalpprefixextensions**

- Wert **\<string value>** 

Verwenden Sie die folgende Tabelle, um den angegebenen Zeichen folgen Wert zu identifizieren:

| Zeichenfolgenwert| Client und Scanner|
|-------------|---------------|
|\*|Alle Pfile-Erweiterungen werden P\<EXT>|
|\<null value>| Der Standardwert verhält sich wie der Standardschutz Wert.|
|ConvertTo-JSON (". DWG", ". zip")|Zusätzlich zur vorherigen Liste werden ". DWG" und ". zip" zu "P".\<EXT>| 

Beispiel 1: PowerShell-Befehl verhält sich wie das Standardverhalten, bei dem der Schutz von ". DWG" zu ". dwg. Pfile" wird:

```PowerShell
Set-LabelPolicy -AdvancedSettings @{ AdditionalPPrefixExtensions =""}
```

Beispiel 2: PowerShell-Befehl zum Ändern aller Pfile-Erweiterungen vom generischen Schutz (DWG. Pfile) in den nativen Schutz (. pdwg), wenn die Dateien geschützt sind:

```PowerShell
Set-LabelPolicy -AdvancedSettings @{ AdditionalPPrefixExtensions ="*"}
```

Beispiel 3: PowerShell-Befehl zum Ändern von ". DWG" in ". pdwg" Wenn Sie diesen Dienst verwenden, schützen Sie diese Datei:

```PowerShell
Set-LabelPolicy -AdvancedSettings @{ AdditionalPPrefixExtensions =ConvertTo-Json(".dwg")}
```

Mit dieser Einstellung werden die folgenden Erweiterungen (". txt", ". xml", ". bmp", ". JT", ". jpg", ". JPEG", ". jpe", ". jif", ". jff", ". JFI", ". png", ". TIF", ". TIFF", ". gif") werden immer P \<EXT> . Der bedeutende Ausschluss besteht darin, dass "ptxt" nicht "txt. Pfile" wird. 
**Additionalpprefixextensions** funktioniert nur, wenn der Schutz von pfiles mit der erweiterten Eigenschaft " [**pfilesupportedextension**](#pfilesupportedextension) " aktiviert ist. 

Beispielsweise in einem Fall, in dem der folgende Befehl verwendet wird:

```PowerShell
Set-LabelPolicy -AdvancedSettings @{PFileSupportedExtensions=""}
```

Der Pfile-Schutz ist nicht möglich, und der Wert in **additionalpprefixextensions** wird ignoriert. 

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>„Not now“ („Nicht jetzt“) für Dokumente bei Verwendung der obligatorischen Bezeichnung entfernen

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die Bezeichnung "Bezeichnung" für **alle Dokumente verwenden, und e-Mails müssen eine Bezeichnung aufweisen**, werden die Benutzer beim ersten Speichern eines Office-Dokuments und beim Senden einer e-Mail aufgefordert, eine Bezeichnung auszuwählen. Bei Office-Dokumenten können Benutzer **Not now** (nicht jetzt) wählen, um die Aufforderung zum Auswählen einer Bezeichnung vorübergehend zu schließen und zum Dokument zurückzukehren. Sie können das gespeicherte Dokument jedoch nicht schließen, ohne es zu bezeichnen. 

Wenn Sie diese Einstellung konfigurieren, wird die Option **Not now** (nicht jetzt) entfernt, sodass die Benutzer eine Bezeichnung wählen müssen, wenn das Dokument zum ersten Mal gespeichert wird.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Schlüssel: **PostponeMandatoryBeforeSave**

- Wert: **FALSE**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{PostponeMandatoryBeforeSave="False"}
```

## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen

Diese Konfiguration verwendet [Erweiterte Richtlinien Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Es gibt zwei Methoden, um Klassifizierungen aus anderen Bezeichnungs Lösungen zu entfernen. Die erste Methode entfernt alle Formen aus Word-Dokumenten, bei denen der Shape-Name mit dem Namen übereinstimmt, der in der erweiterten Eigenschaft **wordshapenametoremove**definiert wurde. mit der zweiten Methode können Sie textbasierte Kopf-oder Fußzeilen aus Word-, Excel-und PowerPoint-Dokumenten entfernen oder ersetzen, wie in der erweiterten Eigenschaft **removeexternalcontentmarkinginapp** 

### <a name="use-the-wordshapenametoremove-advanced-property"></a>Verwenden der erweiterten Eigenschaft wordshapenametoremove

*Die Eigenschaft **wordshapenametoremove** Advanced wird von Version 2.6.101.0 und höher unterstützt.*

Mit dieser Einstellung können Sie formbasierte Bezeichnungen aus Word-Dokumenten entfernen oder ersetzen, wenn diese visuellen Kennzeichnungen von einer anderen Bezeichnungs Lösung angewendet wurden. Die Form enthält z. b. den Namen einer alten Bezeichnung, die Sie nun zu Vertraulichkeits Bezeichnungen migriert haben, um einen neuen Bezeichnungs Namen und eine eigene Form zu verwenden.

Um diese erweiterte Eigenschaft verwenden zu können, müssen Sie den Namen der Form im Word-Dokument suchen und diese dann in der erweiterten Eigenschaften Liste von **wordshapenametoremove** definieren. Der Dienst entfernt eine beliebige Form in Word, die mit einem Namen beginnt, der in der Liste der Formen in dieser erweiterten Eigenschaft definiert ist.

Vermeiden Sie das Entfernen von Formen, die den zu ignorierenden Text enthalten, indem Sie den Namen aller zu entfernenden Formen definieren und das Überprüfen des Texts in allen Formen vermeiden, bei dem es sich um einen ressourcenintensiven Prozess handelt.

Wenn Sie in dieser zusätzlichen erweiterten Eigenschaften Einstellung keine Wortformen angeben und Word im Schlüsselwert **removeexternalcontentmarkinginapp** enthalten ist, werden alle Formen auf den Text überprüft, den Sie im Wert von **externalcontentmarkingtoremove** angeben. 

So finden Sie den Namen der von Ihnen verwendeten Form und möchten Sie ausschließen:

1. Zeigen Sie in Word den **Auswahl** Bereich an: Registerkarte " **Home** " > **Bearbeitungs** Gruppe > **Wählen Sie** die Option > **Auswahl**Bereich aus.

2. Wählen Sie die Form auf der Seite aus, die Sie zum Entfernen markieren möchten. Der Name der von Ihnen markierten Form ist nun im Bereich **Auswahl** hervorgehoben.

Verwenden Sie den Namen der Form, um einen Zeichen folgen Wert für den Schlüssel * * * * wordshapenametoremove * * * * anzugeben. 

Beispiel: der Name der Form ist **DC**. Geben Sie den Wert `dc` an, um die Form mit diesem Namen zu entfernen.

- Schlüssel: **wordshapenametoremove**

- Wert: \<**Word shape name**> 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{WordShapeNameToRemove="dc"}
```

Wenn Sie mehr als eine Wort Form entfernen möchten, geben Sie so viele Werte an, wie die zu entfernenden Formen vorhanden sind.

### <a name="use-the-removeexternalcontentmarkinginapp-advanced-property"></a>Verwenden der erweiterten removeexternalcontentmarkinginapp-Eigenschaft

Mit dieser Einstellung können Sie textbasierte Kopf-oder Fußzeilen aus Dokumenten entfernen oder ersetzen, wenn diese visuellen Kennzeichnungen durch eine andere Bezeichnungs Lösung angewendet wurden. Beispielsweise enthält die alte Fußzeile den Namen einer alten Bezeichnung, die Sie nun zu den Vertraulichkeits Bezeichnungen migriert haben, um einen neuen Bezeichnungs Namen und eine eigene Fußzeile zu verwenden.

Wenn der Unified Label-Client diese Konfiguration in der Richtlinie abruft, werden die alten Kopf-und Fußzeilen entfernt oder ersetzt, wenn das Dokument in der Office-App geöffnet wird und jede Vertraulichkeits Bezeichnung auf das Dokument angewendet wird.

Diese Konfiguration wird für Outlook nicht unterstützt. Beachten Sie außerdem, dass die Verwendung mit Word, Excel und PowerPoint sich negativ auf die Leistung dieser Apps für Benutzer auswirken kann. Mithilfe der Konfiguration können Sie Einstellungen für jede einzelne Anwendung definieren, z.B. die Suche nach Text in Kopf- oder Fußzeilen von Word-Dokumenten, jedoch nicht von Excel-Tabellen oder PowerPoint-Präsentationen.

Da der Musterabgleich die Leistung für Benutzer beeinflusst, empfiehlt es sich, die Office-Anwendungs Typen (**W**Ord, E**X**cel, **P**owerpoint) nur auf die zu durchsuchenden Anwendungen einzuschränken.
Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:
- Key: **RemoveExternalContentMarkingInApp**

- Wert: \<**Office application types WXP**> 

Beispiele:

- Geben Sie **W** an, um nur Word-Dokumente zu durchsuchen.

- Geben Sie **WP** an, um Word-Dokumente und PowerPoint-Präsentationen zu durchsuchen.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{RemoveExternalContentMarkingInApp="WX"}
```

Sie benötigen dann mindestens eine weitere erweiterte Clienteinstellung, **ExternalContentMarkingToRemove**, um die Inhalte der Kopf- oder Fußzeile anzugeben und diese zu entfernen oder zu ersetzen.

### <a name="how-to-configure-externalcontentmarkingtoremove"></a>Konfigurieren von ExternalContentMarkingToRemove

Wenn Sie den Zeichenfolgenwert für den Schlüssel **ExternalContentMarkingToRemove** angeben, stehen drei Optionen zur Verfügung, die reguläre Ausdrücke verwenden:

- Partielle Übereinstimmung, um alles aus der Kopf- oder Fußzeile zu entfernen.

    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten diese Kopf- oder Fußzeilen vollständig entfernen. Geben Sie den Wert `*TEXT*` an.

- Vollständige Übereinstimmung, um nur bestimmte Wörter aus der Kopf- oder Fußzeile zu entfernen.

    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten nur das Wort **TEXT** entfernen, wodurch die Zeichenfolge der Kopf- oder Fußzeile **TO REMOVE** entspricht. Geben Sie den Wert `TEXT ` an.

- Vollständige Übereinstimmung, um alles aus der Kopf- oder Fußzeile zu entfernen.

    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten die Kopf- oder Fußzeilen entfernen, die genau diese Zeichenfolge enthalten. Geben Sie den Wert `^TEXT TO REMOVE$` an.


Der Musterabgleich für die angegebene Zeichenfolge berücksichtigt keine Groß- und Kleinschreibung. Die maximale Zeichen folgen Länge beträgt 255 Zeichen und darf keine Leerzeichen enthalten. 

Da einige Dokumente unsichtbare Zeichen oder andere Arten von Leerzeichen oder Tabstopps enthalten können, wird die Zeichenfolge, die Sie für einen Begriff oder einen Satz angeben, möglicherweise nicht erkannt. Geben Sie nach Möglichkeit immer ein einzelnes unterscheidendes Wort für den Wert an, und testen Sie die Ergebnisse, bevor Sie diese für die Produktion bereitstellen.

Geben Sie für dieselbe Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **ExternalContentMarkingToRemove**

- Wert: \<**string to match, defined as regular expression**> 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*TEXT*"}
```

#### <a name="multiline-headers-or-footers"></a>Mehrzeilige Kopf- oder Fußzeilen

Wenn der Text in einer Kopf- oder Fußzeile mehr als eine Zeile umfasst, erstellen Sie einen Schlüssel und einen Wert für jede Zeile. Angenommen, folgende Fußzeile mit zwei Zeilen ist vorhanden:

**The file is classified as Confidential**

**Label applied manually**

Um diese mehrzeilige Fußzeile zu entfernen, erstellen Sie die folgenden zwei Einträge für die gleiche Bezeichnungs Richtlinie:

- Key: **ExternalContentMarkingToRemove**

- Schlüsselwert 1: ** \* vertraulich***

- Schlüsselwert 2: ** \* Bezeichnung angewendet*** 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*Confidential*,*Label applied*"}
```

#### <a name="optimization-for-powerpoint"></a>Optimierung für PowerPoint

In PowerPoint werden Fußzeilen als Formen implementiert. Wenn Sie vermeiden möchten, dass Formen entfernt werden, die den angegeben Text enthalten, jedoch keine Kopf- oder Fußzeilen sind, verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **PowerPointShapeNameToRemove**. Es wird empfohlen, diese Einstellung ebenfalls zu verwenden, um zu verhindern, dass der Text in allen Formen überprüft wird, denn dieser Prozess ist sehr ressourcenintensiv.

Wenn Sie diese zusätzliche erweiterte Clienteinstellung nicht angeben und PowerPoint im Schlüsselwert **RemoveExternalContentMarkingInApp** eingeschlossen ist, werden alle Formen auf den Text überprüft, den Sie im Wert **ExternalContentMarkingToRemove** angeben. 

So finden Sie den Namen der Form, die Sie als Kopf- oder Fußzeile verwenden:

1. Zeigen Sie in PowerPoint den Bereich **Auswahl** an: **Format** > **Anordnen** > **Auswahlbereich**.

2. Wählen Sie die Form auf der Folie aus, die die Kopf- oder Fußzeile enthält. Der Name der ausgewählten Form wird nun im Bereich **Auswahl** hervorgehoben.

Verwenden Sie den Namen der Form, um einen Zeichenfolgenwert für den Schlüssel **PowerPointShapeNameToRemove** anzugeben. 

Beispiel: Der Name der Form ist **fc**. Geben Sie den Wert `fc` an, um die Form mit diesem Namen zu entfernen.

- Key: **PowerPointShapeNameToRemove**

- Wert: \<**PowerPoint shape name**> 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{PowerPointShapeNameToRemove="fc"}
```

Wenn Sie mehr als eine PowerPoint-Form entfernen möchten, geben Sie so viele Werte an, wie die zu entfernenden Formen vorhanden sind.

Standardmäßig werden nur die Masterfolien auf Kopf- oder Fußzeilen überprüft. Wenn Sie diese Suche auf alle Folien ausweiten möchten (dieser Prozess ist jedoch wesentlich ressourcenintensiver), verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **RemoveExternalContentMarkingInAllSlides**:

- Key: **RemoveExternalContentMarkingInAllSlides**

- Wert: **true**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{RemoveExternalContentMarkingInAllSlides="True"}
```

## <a name="disable-custom-permissions-in-file-explorer"></a>Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig wird Benutzern eine Option mit dem Namen **schützen mit benutzerdefinierten Berechtigungen** angezeigt, wenn Sie mit der rechten Maustaste in den Datei-Explorer klicken und **klassifizieren und schützen**auswählen. Mit dieser Option können Sie Ihre eigenen Schutzeinstellungen festlegen, mit denen alle Schutzeinstellungen außer Kraft gesetzt werden können, die Sie möglicherweise in einer Bezeichnungs Konfiguration enthalten haben. Benutzer können außerdem eine Option zum Entfernen des Schutzes sehen. Wenn Sie diese Einstellung konfigurieren, werden den Benutzern diese Optionen nicht angezeigt.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Schlüssel: **EnableCustomPermissions**

- Wert: **FALSE**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}
```

## <a name="for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer"></a>Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die erweiterte Client Einstellung so konfigurieren, dass Benutzer [definierte Berechtigungen im Datei-Explorer deaktiviert](#disable-custom-permissions-in-file-explorer)werden, können Benutzer benutzerdefinierte Berechtigungen, die bereits in einem geschützten Dokument festgelegt sind, nicht anzeigen oder ändern.

Es gibt jedoch eine andere erweiterte Client Einstellung, die Sie angeben können, damit Benutzer benutzerdefinierte Berechtigungen für ein geschütztes Dokument sehen und ändern können, wenn Sie den Datei-Explorer verwenden und mit der rechten Maustaste auf die Datei klicken.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Schlüssel: **enablecustompermissionsforcustomprotectedfiles**

- Wert: **true**

PowerShell-Beispiel Befehl:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissionsForCustomProtectedFiles="True"}
```

## <a name="for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments"></a>Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht

Diese Konfiguration verwendet [Erweiterte Richtlinien Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Diese Einstellung gilt für den Fall, dass Benutzer eine Bezeichnung Dokumente an eine e-Mail anfügen und die e-Mail-Nachricht nicht selbst bezeichnen. In diesem Szenario wird automatisch eine Bezeichnung für Sie ausgewählt, basierend auf den Klassifizierungs Bezeichnungen, die auf die Anlagen angewendet werden. Die höchste Klassifizierungs Bezeichnung ist ausgewählt.

Die Anlage muss eine physische Datei und kein Link zu einer Datei sein (z. b. ein Link zu einer Datei in Microsoft SharePoint oder onedrive).

Sie können diese Einstellung auf " **empfohlen**" festlegen, damit Benutzer mit einer anpassbaren QuickInfo aufgefordert werden, die ausgewählte Bezeichnung auf Ihre e-Mail-Nachricht anzuwenden. Benutzer können die Empfehlung akzeptieren oder ablehnen. Oder Sie können diese Einstellung auf " **automatisch**" festlegen, wobei die ausgewählte Bezeichnung automatisch angewendet wird, Benutzer aber die Bezeichnung entfernen oder eine andere Bezeichnung auswählen können, bevor Sie die e-Mail senden.

> [!NOTE]
> Wenn die Anlage mit der höchsten Klassifizierungs Bezeichnung für den Schutz mit der Einstellung benutzerdefinierter Berechtigungen konfiguriert ist:
> 
> - Wenn die benutzerdefinierten Berechtigungen der Bezeichnung Outlook (nicht weiterleiten) einschließen, wird diese Bezeichnung ausgewählt und der Schutz nicht weiterleiten auf die e-Mail angewendet.
> - Wenn die benutzerdefinierten Berechtigungen der Bezeichnung nur für Word, Excel, PowerPoint und den Datei-Explorer gelten, wird diese Bezeichnung nicht auf die e-Mail-Nachricht angewendet, und keines ist der Schutz.
> 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Schlüssel 1: **attachmentaction**

- Schlüsselwert 1: **empfohlen** oder **automatisch**

- Schlüssel 2: **attachmentaktiontip**

- Schlüsselwert 2: " \<customized tooltip> "

Die angepasste QuickInfo unterstützt nur eine einzige Sprache.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{AttachmentAction="Automatic"}
```

## <a name="add-report-an-issue-for-users"></a>Add "Report an Issue" for users ("Problem melden" für Benutzer hinzufügen)

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die folgende erweiterte Clienteinstellung angeben, wird Benutzern die Option **Problem melden** angezeigt, die sie aus dem Clientdialogfeld **Hilfe und Feedback** auswählen können. Geben Sie eine HTTP-Zeichenfolge für den Link an. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **ReportAnIssueLink**

- Wert **\<HTTP string>**

Beispielwert für eine Website: `https://support.contoso.com`

Beispielwert für eine E-Mail-Adresse: `mailto:helpdesk@contoso.com`

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{ReportAnIssueLink="mailto:helpdesk@contoso.com"}
```

## <a name="implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent"></a>Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben

Diese Konfiguration verwendet [Erweiterte Richtlinien Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die folgenden erweiterten Clienteinstellungen erstellen und konfigurieren, werden Benutzern Popupmeldungen in Outlook angezeigt, die sie vor dem Senden einer E-Mail warnen können, oder sie nach einer Legitimierung fragen, warum sie eine E-Mail versenden, oder sie aus folgenden Gründen davon abhalten, eine E-Mail zu senden:

- **Die E-Mail oder der E-Mail-Anhang hat eine bestimmte Bezeichnung:**
    - Der Anhang kann einen beliebigen Dateityp haben

- **Die E-Mail oder der E-Mail-Anhang hat keine bestimmte Bezeichnung:**
    - Der Anhang kann ein Office-Dokument oder ein PDF-Dokument sein

Wenn diese Bedingungen erfüllt sind, wird dem Benutzer eine Popup Meldung mit einer der folgenden Aktionen angezeigt:

- **Warnung**: der Benutzer kann die Bestätigung durchsetzen und senden oder Abbrechen.

- **Rechtfertigen**: der Benutzer wird zur Begründung aufgefordert (vordefinierte Optionen oder Freiform).  Der Benutzer kann dann die E-Mail senden oder abbrechen. Der Legitimationstext wird in den X-Header der E-Mail geschrieben, sodass dieser von anderen Systemen gelesen werden kann. Zum Beispiel von Diensten, die der Verhinderung von Datenverlust dienen.

- **Blockieren**: der Benutzer wird daran gehindert, die e-Mail zu senden, während die Bedingung verbleibt. Die Nachricht beinhaltet den Grund dafür, warum die E-Mail blockiert wird, sodass der Benutzer das Problem aufheben kann. So kann er z.B. bestimmte Empfänger entfernen, oder der E-Mail eine Bezeichnung hinzufügen. 

Wenn sich die Popup Meldungen für eine bestimmte Bezeichnung befinden, können Sie Ausnahmen für Empfänger nach Domänen Name konfigurieren.

> [!TIP]
> Eine exemplarische Vorgehensweise zum Konfigurieren dieser Einstellungen finden Sie im Video [Azure Information Protection Outlook-Popup Konfiguration](https://azure.microsoft.com/resources/videos/how-to-configure-azure-information-protection-popup-for-outlook/) .

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren für bestimme Bezeichnungen implementiert:

Erstellen Sie für die ausgewählte Richtlinie mindestens eine der folgenden erweiterten Einstellungen mit den folgenden Schlüsseln. Geben Sie für die Werte eine oder mehrere Bezeichnungen durch die GUIDs an, die jeweils durch ein Komma getrennt sind.

Beispiel Wert für mehrere Bezeichnungs-GUIDs als durch Trennzeichen getrennte Zeichenfolge: 

```sh
dcf781ba-727f-4860-b3c1-73479e31912b,1ace2cc3-14bc-4142-9125-bf946a70542c,3e9df74d-3168-48af-8b11-037e3021813f
```

- Warnmeldungen:
    
    - Schlüssel: **outlookwarnuntreudkollaborationlabel**
    
    - Wert: \<**label GUIDs, comma-separated**>

- Legitimationsmeldungen:
    
    - Schlüssel: **outlookjustilyuntreudkollaborationlabel**
    
    - Wert: \<**label GUIDs, comma-separated**>

- Blockiermeldungen:
    
    - Schlüssel: **outlookblockuntreudkollaborationlabel**
    
    - Wert: \<**label GUIDs, comma-separated**>


PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookWarnUntrustedCollaborationLabel="8faca7b8-8d20-48a3-8ea2-0f96310a848e,b6d21387-5d34-4dc8-90ae-049453cec5cf,bb48a6cb-44a8-49c3-9102-2d2b017dcead,74591a94-1e0e-4b5d-b947-62b70fc0f53a,6c375a97-2b9b-4ccd-9c5b-e24e4fd67f73"}

Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyUntrustedCollaborationLabel="dc284177-b2ac-4c96-8d78-e3e1e960318f,d8bb73c3-399d-41c2-a08a-6f0642766e31,750e87d4-0e91-4367-be44-c9c24c9103b4,32133e19-ccbd-4ff1-9254-3a6464bf89fd,74348570-5f32-4df9-8a6b-e6259b74085b,3e8d34df-e004-45b5-ae3d-efdc4731df24"}

Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockUntrustedCollaborationLabel="0eb351a6-0c2d-4c1d-a5f6-caa80c9bdeec,40e82af6-5dad-45ea-9c6a-6fe6d4f1626b"}
```

#### <a name="to-exempt-domain-names-for-pop-up-messages-configured-for-specific-labels"></a>So nehmen Sie Domänen Namen für Popup Nachrichten aus, die für bestimmte Bezeichnungen konfiguriert sind

Für die Bezeichnungen, die Sie mit diesen Popup Nachrichten angegeben haben, können Sie bestimmte Domänen Namen ausnehmen, damit Benutzer die Nachrichten für Empfänger, die diesen Domänen Namen enthalten, nicht in Ihrer e-Mail-Adresse sehen. In diesem Fall werden die E-Mails problemlos gesendet. Wenn Sie mehrere Domänen angeben möchten, fügen Sie sie kommagetrennt als einzelne Zeichenfolge hinzu.

Eine übliche Konfiguration ist es, die Popupmeldungen nur für die Empfänger anzuzeigen, die nicht zu Ihrer Organisation gehören, oder die keine für Ihre Organisation autorisierte Partner sind. In diesem Fall geben Sie alle E-Mail-Domänen an, die von Ihrer Organisation und von Ihren Partnern verwendet werden.

Erstellen Sie für dieselbe Bezeichnungs Richtlinie die folgenden erweiterten Client Einstellungen, und geben Sie für den Wert eine oder mehrere Domänen an, die jeweils durch ein Komma getrennt sind.

Beispielwert für mehrere Domänen als kommagetrennte Zeichenfolge: `contoso.com,fabrikam.com,litware.com`

- Warnmeldungen:
    
    - Schlüssel: **outlookwarntreuddomains**
    
    - Wert **\<**domain names, comma separated**>**

- Legitimationsmeldungen:
    
    - Schlüssel: **outlookjustifytreuddomains**
    
    - Wert **\<**domain names, comma separated**>**

- Blockiermeldungen:
    
    - Schlüssel: **outlookblocktreuhänddomains**
    
    - Wert **\<**domain names, comma separated**>**

Sie haben beispielsweise die Einstellung für den erweiterten Client " **outlookblockuntreudkollaborationlabel** " für die Bezeichnung " **vertraulich\alle Mitarbeiter** " angegeben. Nun geben Sie die zusätzliche erweiterte Client Einstellung " **outlookjustifytreuddomains** " und " **contoso.com**" an. Dies hat zur Folge, dass ein Benutzer eine e-Mail an senden kann, john@sales.contoso.com Wenn er **vertraulich \ alle Mitarbeiter** heißt, aber das Senden einer e-Mail mit derselben Bezeichnung an ein Gmail-Konto blockiert wird.

PowerShell-Beispiel Befehle, deren Bezeichnung "Global" lautet:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockTrustedDomains="gmail.com"}

Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyTrustedDomains="contoso.com,fabrikam.com,litware.com"}
```

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-emails-or-attachments-that-dont-have-a-label"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren von E-Mails oder Anhängen implementiert, die keine Bezeichnung haben:

Erstellen Sie für dieselbe Bezeichnungs Richtlinie die folgende erweiterte Client Einstellung mit einem der folgenden Werte:

- Warnmeldungen:
    
    - Schlüssel: **outlookunlabeledcollaborationaction**
    
    - Wert: **warnen**

- Legitimationsmeldungen:
    
    - Schlüssel: **outlookunlabeledcollaborationaction**
    
    - Wert: **rechtfertigen**

- Blockiermeldungen:
    
    - Schlüssel: **outlookunlabeledcollaborationaction**
    
    - Wert: **Block**

- Diese Meldungen deaktivieren:
    
    - Schlüssel: **outlookunlabeledcollaborationaction**
    
    - Wert: **aus**


PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationAction="Warn"}
```

#### <a name="to-define-specific-file-name-extensions-for-the-warn-justify-or-block-pop-up-messages-for-email-attachments-that-dont-have-a-label"></a>So definieren Sie für e-Mail-Anhänge, die keine Bezeichnung aufweisen, bestimmte Dateinamen Erweiterungen für die Warn-, rechtfertigen oder Blockierungs-Popup Meldungen

Standardmäßig gelten die Popup Nachrichten warnen, rechtfertigen oder blockieren für alle Office-Dokumente und PDF-Dokumente. Sie können diese Liste verfeinern, indem Sie angeben, welche Dateinamen Erweiterungen die Warn-, Recht-oder Sperr Nachrichten mit einer zusätzlichen erweiterten Einstellung und eine durch Trennzeichen getrennte Liste von Dateinamen Erweiterungen anzeigen sollen.

Beispiel Wert für mehrere Dateinamen Erweiterungen, die als durch Trennzeichen getrennte Zeichenfolge definiert werden sollen: `.XLSX,.XLSM,.XLS,.XLTX,.XLTM,.DOCX,.DOCM,.DOC,.DOCX,.DOCM,.PPTX,.PPTM,.PPT,.PPTX,.PPTM`

In diesem Beispiel führt ein PDF-Dokument ohne Bezeichnung nicht zu Warn-, rechtfertigen oder Blockierungs Nachrichten.

Geben Sie für dieselbe Bezeichnungs Richtlinie die folgenden Zeichen folgen ein: 


- Key: **outlookoverride unlabeledcollaborationextensions**

- Wert **\<**file name extensions to display messages, comma separated**>**


PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookOverrideUnlabeledCollaborationExtensions=".PPTX,.PPTM,.PPT,.PPTX,.PPTM"}
```

#### <a name="to-specify-a-different-action-for-email-messages-without-attachments"></a>So geben Sie eine andere Aktion für e-Mail ohne Anlagen an

Standardmäßig gilt: der Wert, den Sie für outlookunlabeledcollaborationaction angeben, um Popup Nachrichten zu warnen, zu begründen oder zu blockieren, gilt für e-Mails oder Anhänge, die keine Bezeichnung aufweisen. Sie können diese Konfiguration verfeinern, indem Sie eine andere erweiterte Einstellung für e-Mail-Nachrichten mit Anlagen angeben.

Erstellen Sie die folgende erweiterte Clienteinstellung mit einem der folgenden Werte:

- Warnmeldungen:
    
    - Schlüssel: **outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **warnen**

- Legitimationsmeldungen:
    
    - Schlüssel: **outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **rechtfertigen**

- Blockiermeldungen:
    
    - Schlüssel: **outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **Block**

- Diese Meldungen deaktivieren:
    
    - Schlüssel: **outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **aus**

Wenn Sie diese Client Einstellung nicht angeben, wird der Wert, den Sie für "outlookunlabeledcollaborationaction" angeben, für nicht beschriftete e-Mail-Nachrichten ohne Anhänge und nicht bezeichnete e-Mail-Nachrichten mit Anlagen verwendet.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior="Warn"}
```

## <a name="disable-sending-audit-data-to-azure-information-protection-analytics"></a>Deaktivieren des Sendens von Überwachungsdaten an Azure Information Protection Analytics

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Der Azure Information Protection Unified Bezeichnung-Client unterstützt die Zentrale Berichterstellung und sendet seine Überwachungsdaten standardmäßig an [Azure Information Protection Analytics](../reports-aip.md). Weitere Informationen zu den gesendeten und gespeicherten Informationen finden Sie im Abschnitt [Informationen zu den gesammelten und an Microsoft gesendeten](../reports-aip.md#information-collected-and-sent-to-microsoft) Informationen aus der Dokumentation zu Central Reporting.

Um dieses Verhalten so zu ändern, dass diese Informationen nicht vom Unified Label-Client gesendet werden, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Schlüssel: **EnableAudit**

- Wert: **FALSE**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableAudit="False"}
```

## <a name="send-information-type-matches-to-azure-information-protection-analytics"></a>Senden von Informationstypen Übereinstimmungen an Azure Information Protection Analytics
 
Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig sendet der Unified-Bezeichnungs Client keine Inhalts Übereinstimmungen für sensible Informationstypen an [Azure Information Protection Analytics](../reports-aip.md). Weitere Informationen zu diesen zusätzlichen Informationen, die gesendet werden können, finden Sie im Abschnitt [Inhalts Übereinstimmungen für eine tiefere Analyse](../reports-aip.md#content-matches-for-deeper-analysis) in der Dokumentation zur zentralen Berichterstellung.

Um Inhalts Übereinstimmungen zu senden, wenn vertrauliche Informationstypen gesendet werden, erstellen Sie die folgende erweiterte Client Einstellung in einer Bezeichnungs Richtlinie: 

- Schlüssel: **logmatchedcontent**

- Wert: **true**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{LogMatchedContent="True"}
```

## <a name="limit-cpu-consumption"></a>Begrenzen der CPU-Auslastung

Ab der Überprüfungs Version 2.7. x. x empfiehlt es sich, die CPU-Auslastung mithilfe der folgenden erweiterten **scannermaxcpu** -und **scannermincpu** -Einstellungs Methode einzuschränken. 

> [!IMPORTANT]
> Wenn die folgende Thread Einschränkungs Richtlinie verwendet wird, werden die erweiterten Einstellungen **scannermaxcpu** und **scannermincpu** ignoriert. Um die CPU-Auslastung mithilfe der erweiterten Einstellungen **scannermaxcpu** und **scannermincpu** einzuschränken, brechen Sie die Verwendung von Richtlinien ab, die die Anzahl der Threads begrenzen. 

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Zum Begrenzen der CPU-Auslastung auf dem Überprüfungs Computer können Sie zwei Erweiterte Einstellungen erstellen: **scannermaxcpu** und **scannermincpu**. 

**Scannermaxcpu** ist standardmäßig auf 100 festgelegt, was bedeutet, dass es keine Beschränkung der maximalen CPU-Auslastung gibt. In diesem Fall versucht der Überprüfungsprozess, die gesamte verfügbare CPU-Zeit zu nutzen, um die Scan Raten zu maximieren.

Wenn Sie **scannermaxcpu** auf einen niedrigeren Wert als 100 festlegen, wird die CPU-Auslastung in den letzten 30 Minuten vom Scanner überwacht. wenn die maximale CPU den von Ihnen festgelegten Grenzwert überschritten hat, wird die Anzahl der Threads, die neuen Dateien zugeordnet sind, verringert. Der Grenzwert für die Anzahl der Threads wird fortgesetzt, solange der CPU-Verbrauch höher als der für **scannermaxcpu**festgelegte Grenzwert ist.

**Scannermincpu**ist nur aktiviert, wenn **scannermaxcpu** nicht gleich 100 ist. **Scannermincpu** kann nicht auf eine Zahl höher festgelegt werden, die höher als die **scannermaxcpu** -Nummer ist. Es wird empfohlen, **scannermincpu** mindestens 15 Punkte als den Wert von  **scannermaxcpu**festzulegen.   

Der Standardwert dieser Einstellung ist 50, d. h., wenn die CPU-Auslastung in den letzten 30 Minuten niedriger als dieser Wert ist, beginnt die Überprüfung, neue Threads hinzuzufügen, um weitere Dateien parallel zu scannen, bis die CPU-Auslastung die für **scannermaxcpu**-15 festgelegte Stufe erreicht. 

## <a name="limit-the-number-of-threads-used-by-the-scanner"></a>Begrenzen der Anzahl der von der Überprüfung verwendeten Threads

> [!IMPORTANT]
> Wenn die folgende Thread Einschränkungs Richtlinie verwendet wird, werden die erweiterten Einstellungen **scannermaxcpu** und **scannermincpu** ignoriert. Um die CPU-Auslastung mithilfe der erweiterten Einstellungen **scannermaxcpu** und **scannermincpu** einzuschränken, brechen Sie die Verwendung von Richtlinien ab, die die Anzahl der Threads begrenzen. 

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig verwendet die Überprüfung alle verfügbaren Prozessorressourcen des Computers, auf dem der Überprüfungsdienst ausgeführt wird. Wenn Sie die CPU-Auslastung einschränken müssen, während der Dienst gescannt wird, erstellen Sie die folgende erweiterte Einstellung in einer Bezeichnungs Richtlinie. 

Geben Sie als Wert die Anzahl von gleichzeitigen Threads an, die von der Überprüfung parallel ausgeführt werden dürfen. Die Überprüfung verwendet für jede Datei, die überprüft wird, einen separaten Thread, daher definiert diese Drosselungskonfiguration auch die Anzahl von Dateien, die parallel überprüft werden können. 

Wenn Sie den Wert zu Testzwecken zum ersten Mal konfigurieren, empfehlen wir Ihnen, „2 pro Kern“ anzugeben und die Ergebnisse zu überwachen. Wenn Sie die Überprüfung z.B. auf einem Computer mit vier Kernen ausführen, legen Sie den Wert auf „8“ fest. Erhöhen oder verringern Sie den Wert nach Bedarf – je nachdem, welche Leistung Sie für den Überprüfungscomputer und die Überprüfungshäufigkeit benötigen. 

- Schlüssel: **Scannerkonfigurations-Level**

- Wert **\<number of concurrent threads>**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Scanner" hat:

```PowerShell
Set-LabelPolicy -Identity Scanner -AdvancedSettings @{ScannerConcurrencyLevel="8"}
```

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Diese Konfiguration ist nicht kompatibel mit geschützten PDF-Dateien mit der Dateinamenerweiterung ppdf. Diese Dateien können nicht vom Client mit dem Datei-Explorer oder PowerShell geöffnet werden.

Bei Office-Dokumenten, die von Secure Islands bezeichnet werden, können Sie diese Dokumente mit einer Vertraulichkeits Bezeichnung versehen, indem Sie eine von Ihnen definierte Zuordnung verwenden. Mit dieser Methode können Sie auch Bezeichnungen aus anderen Lösungen wiederverwenden, wenn diese Bezeichnungen sich in Office-Dokumenten befinden. 

Als Ergebnis dieser Konfigurationsoption wird die neue Vertraulichkeits Bezeichnung vom Azure Information Protection Unified Label-Client wie folgt angewendet:

- Für Office-Dokumente: Wenn das Dokument in der Desktop-App geöffnet wird, wird die neue Vertraulichkeits Bezeichnung als festgelegt angezeigt und beim Speichern des Dokuments angewendet.

- Für PowerShell: " [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel) " und " [Set-aipfileclassificiations](/powershell/module/azureinformationprotection/set-aipfileclassification) " können die neue Vertraulichkeits Bezeichnung anwenden.

- Im Datei-Explorer: im Dialogfeld Azure Information Protection wird die neue Vertraulichkeits Bezeichnung angezeigt, aber nicht festgelegt.

Diese Konfiguration erfordert, dass Sie für jede Vertraulichkeits Bezeichnung, die Sie der alten Bezeichnung zuordnen möchten, eine erweiterte Einstellung mit dem Namen " **labelbycustomproperties** " angeben. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Geben Sie einen Namen für die Migrationsregel an. Verwenden Sie einen beschreibenden Namen, mit dem Sie identifizieren können, wie eine oder mehrere Bezeichnungen aus Ihrer vorherigen Bezeichnungs Lösung der Vertraulichkeits Bezeichnung zugeordnet werden sollen.

Beachten Sie, dass durch diese Einstellung keine ursprüngliche Bezeichnung aus dem Dokument bzw. keine optische Kennzeichnung im Dokument entfernt wird, die von der ursprünglichen Bezeichnung möglicherweise angewendet wurde. Informationen zum Entfernen von Kopf-und Fußzeilen finden Sie im vorherigen Abschnitt [Entfernen von Kopf-und Fußzeilen aus anderen Beschriftungslösungen](#remove-headers-and-footers-from-other-labeling-solutions).

#### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Beispiel 1: Eine 1:1-Zuordnung des gleichen Bezeichnungsnamens

Anforderung: Dokumente mit der Bezeichnung "vertraulich" der sicheren Insel sollten von Azure Information Protection als "vertraulich" neu berechnet werden.

In diesem Beispiel:

- Die Secure Islands-Bezeichnung lautet **Vertraulich** und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Die erweiterte Einstellung:

- Key: **labelbycustomproperties**

- Wert: die **Bezeichnung "sichere Inseln" ist vertraulich, Klassifizierung, vertraulich** .

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "vertraulich" heißt:

```PowerShell
Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Confidential,Classification,Confidential"}
```

#### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Beispiel 2: Eine 1:1-Zuordnung für einen anderen Bezeichnungsnamen

Anforderung: Dokumente, die von Secure Islands als "vertraulich" bezeichnet werden, sollten durch Azure Information Protection als "streng vertraulich" neu zugeordnet werden.

In diesem Beispiel:

- Die Secure Islands-Bezeichnung lautet **Sensitive** (Sensibel) und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Die erweiterte Einstellung:

- Key: **labelbycustomproperties**

- Value: die **Bezeichnung "sichere Inseln" ist sensibel, Klassifizierung,** vertraulich.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "streng vertraulich" lautet:

```PowerShell
Set-Label -Identity "Highly Confidential" -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Sensitive,Classification,Sensitive"}
```

#### <a name="example-3-many-to-one-mapping-of-label-names"></a>Beispiel 3: n:1-Zuordnung von Bezeichnungsnamen

Anforderung: Sie verfügen über zwei sichere Inseln-Bezeichnungen, die das Wort "Internal" enthalten, und Sie möchten, dass Dokumente, die eine dieser sicheren Inseln-Bezeichnungen aufweisen, vom Azure Information Protection Unified Label-Client als "Allgemein" neu berechnet werden.

In diesem Beispiel:

- Die Secure Islands-Bezeichnungen enthalten den Begriff **Internal** (intern) und sind in der benutzerdefinierten Eigenschaft namens **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

- Key: **labelbycustomproperties**

- Wert: die **Bezeichnung sichere Inseln enthält interne Klassifizierungen,. \* Intern. \* **

Beispiel für einen PowerShell-Befehl, bei dem Ihre Bezeichnung "Allgemein" lautet:

```PowerShell
Set-Label -Identity General -AdvancedSettings @{labelByCustomProperties="Secure Islands label contains Internal,Classification,.*Internal.*"}
```

#### <a name="example-4-multiple-rules-for-the-same-label"></a>Beispiel 4: mehrere Regeln für die gleiche Bezeichnung

Wenn Sie mehrere Regeln für dieselbe Bezeichnung benötigen, definieren Sie mehrere Zeichen folgen Werte für denselben Schlüssel. 

In diesem Beispiel werden die Secure Islands-Bezeichnungen "Confidential" und "Secret" in der benutzerdefinierten Eigenschaft " **Classification**" gespeichert, und Sie möchten, dass der Azure Information Protection Unified Label-Client die Vertraulichkeits Bezeichnung "Confidential" anwendet:

```PowerShell
Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}
```

### <a name="extend-your-label-migration-rules-to-emails"></a>Erweitern Sie Ihre Regeln für die Bezeichnung der Migration auf e-Mails.

Sie können die erweiterten Einstellungen von labelbycustomproperties mit Outlook-e-Mails zusätzlich zu Office-Dokumenten verwenden, indem Sie eine zusätzliche Einstellung für die erweiterte Bezeichnungs Richtlinie angeben. Diese Einstellung hat jedoch eine bekannte negative Auswirkung auf die Leistung von Outlook. Konfigurieren Sie diese zusätzliche Einstellung daher nur, wenn Sie eine starke geschäftliche Anforderung dafür haben, und denken Sie daran, Sie auf einen NULL-Zeichen folgen Wert festzulegen, wenn Sie die Migration von der anderen Bezeichnungs Lösung abgeschlossen haben.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **enablelabelbymailheader**

- Wert: **true**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableLabelByMailHeader="True"}
```

### <a name="extend-your-label-migration-rules-to-sharepoint-properties"></a>Erweitern der Regeln für die Bezeichnung der Migration auf SharePoint-Eigenschaften

Sie können die erweiterten labelbycustomproperties-Einstellungen mit SharePoint-Eigenschaften verwenden, die Sie möglicherweise als Spalten für Benutzer verfügbar machen.

Diese Einstellung wird unterstützt, wenn Sie Word, Excel und PowerPoint verwenden.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Schlüssel: **enablelabelbysharepointproperties**

- Wert: **true**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableLabelBySharePointProperties="True"}
```

## <a name="apply-a-custom-property-when-a-label-is-applied"></a>Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Es gibt möglicherweise einige Szenarios, in denen Sie zusätzlich zu den Metadaten, die durch eine Vertraulichkeits Bezeichnung angewendet werden, eine oder mehrere benutzerdefinierte Eigenschaften auf ein Dokument oder eine e-Mail-Nachricht anwenden möchten.

Beispiel:

- Sie sind gerade dabei, [von einer anderen Bezeichnungs Lösung zu migrieren](#migrate-labels-from-secure-islands-and-other-labeling-solutions), z. b. sichere Inseln. Für die Interoperabilität während der Migration sollten Vertraulichkeits Bezeichnungen auch eine benutzerdefinierte Eigenschaft anwenden, die von der anderen Bezeichnungs Lösung verwendet wird.

- Für Ihr Content Management-System (z. b. SharePoint oder eine Dokument Verwaltungs Lösung von einem anderen Anbieter) möchten Sie einen konsistenten benutzerdefinierten Eigenschaftsnamen mit unterschiedlichen Werten für die Bezeichnungen und mit benutzerfreundlichen Namen anstelle der GUID für die Bezeichnung verwenden.

Für Office-Dokumente und Outlook-e-Mails, die Benutzer mit dem Azure Information Protection Unified Label-Client bezeichnen, können Sie eine oder mehrere benutzerdefinierte Eigenschaften hinzufügen, die Sie definieren. Sie können diese Methode auch verwenden, damit der Unified Label-Client eine benutzerdefinierte Eigenschaft als Bezeichnung aus anderen Projektmappen für Inhalte anzeigt, die noch nicht vom Unified Label-Client bezeichnet werden.

Als Ergebnis dieser Konfigurationsoption werden alle weiteren benutzerdefinierten Eigenschaften vom Azure Information Protection Unified-Bezeichnungs Client wie folgt angewendet:

- Für Office-Dokumente: Wenn das Dokument in der Desktop-App bezeichnet wird, werden beim Speichern des Dokuments die zusätzlichen benutzerdefinierten Eigenschaften angewendet.

- Für Outlook-e-Mails: Wenn die e-Mail-Nachricht in Outlook bezeichnet wird, werden die zusätzlichen Eigenschaften auf den x-Header angewendet, wenn die e-Mail gesendet wird.

- Für PowerShell: " [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel) " und " [Set-aipfileclassificiations](/powershell/module/azureinformationprotection/set-aipfileclassification) " wendet die zusätzlichen benutzerdefinierten Eigenschaften an, wenn das Dokument beschriftet und gespeichert wird. [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) zeigt benutzerdefinierte Eigenschaften als zugeordnete Bezeichnung an, wenn eine Vertraulichkeits Bezeichnung nicht angewendet wird.

- Im Datei-Explorer: Wenn der Benutzer mit der rechten Maustaste auf die Datei klickt und die Bezeichnung anwendet, werden die benutzerdefinierten Eigenschaften angewendet.

Diese Konfiguration erfordert, dass Sie für jede Vertraulichkeits Bezeichnung, die die zusätzlichen benutzerdefinierten Eigenschaften anwenden soll, eine erweiterte Einstellung mit dem Namen " **custompropertiesbylabel** " angeben. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

```sh
[custom property name],[custom property value]
```

> [!IMPORTANT]
> Durch die Verwendung von Leerzeichen in der Zeichenfolge wird die Anwendung der Bezeichnungen verhindert.

#### <a name="example-1-add-a-single-custom-property-for-a-label"></a>Beispiel 1: Hinzufügen einer einzelnen benutzerdefinierten Eigenschaft für eine Bezeichnung

Anforderung: Dokumente, die vom Azure Information Protection Unified Label-Client als "vertraulich" bezeichnet werden, sollten über die zusätzliche benutzerdefinierte Eigenschaft "Klassifizierung" mit dem Wert "Secret" verfügen.

In diesem Beispiel:

- Die **Vertraulichkeits** Bezeichnung heißt vertraulich und erstellt eine benutzerdefinierte Eigenschaft mit dem Namen **Classification** mit dem Wert **Secret**.

Die erweiterte Einstellung:

- Schlüssel: **custompropertiesbylabel**

- Wert: **Klassifizierung, Geheimnis**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "vertraulich" heißt:

```PowerShell
    Set-Label -Identity Confidential -AdvancedSettings @{customPropertiesByLabel="Classification,Secret"}
```

#### <a name="example-2-add-multiple-custom-properties-for-a-label"></a>Beispiel 2: Hinzufügen mehrerer benutzerdefinierter Eigenschaften für eine Bezeichnung

Wenn Sie mehr als eine benutzerdefinierte Eigenschaft für dieselbe Bezeichnung hinzufügen möchten, müssen Sie mehrere Zeichen folgen Werte für denselben Schlüssel definieren.

Beispiel für einen PowerShell-Befehl, bei dem Ihre Bezeichnung "Allgemein" heißt, und Sie möchten eine benutzerdefinierte Eigenschaft mit dem Namen " **Classification** " mit dem Wert " **General** " und eine zweite benutzerdefinierte Eigenschaft mit dem Namen " **Sensitivität** " mit dem Wert " **internal**

```PowerShell
Set-Label -Identity General -AdvancedSettings @{customPropertiesByLabel=ConvertTo-Json("Classification,General", "Sensitivity,Internal")}
```

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden

Diese Konfiguration verwendet [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Verwenden Sie diese Einstellungen nur, wenn Sie über eine funktionierende [S/MIME-Bereitstellung](https://docs.microsoft.com/microsoft-365/security/office-365-security/s-mime-for-message-signing-and-encryption) verfügen und möchten, dass eine Bezeichnung diese Schutzmethode automatisch für e-Mails anwendet, anstatt Rights Management Schutz vor Azure Information Protection. Der resultierende Schutz ist derselbe wie bei der manuellen Auswahl von S/MIME-Optionen in Outlook.

Um eine erweiterte Einstellung für eine digitale S/MIME-Signatur zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **smimesign**

- Wert: **true**

Um eine erweiterte Einstellung für die S/MIME-Verschlüsselung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **smimeverschlüsseln**

- Wert: **true**

Wenn die von Ihnen angegebene Bezeichnung für die Verschlüsselung konfiguriert ist, ersetzt der S/MIME-Schutz für den Azure Information Protection Unified Label-Client den Rights Management Schutz nur in Outlook. Die allgemein verfügbare Version des Unified Label-Clients verwendet weiterhin die für die Bezeichnung im Admin Center angegebenen Verschlüsselungseinstellungen. Bei Office-Apps mit integrierter Bezeichnung wenden diese nicht den S/MIME-Schutz an, sondern wenden den Schutz von "nicht weiterleiten" an.

Wenn die Bezeichnung nur in Outlook sichtbar sein soll, konfigurieren Sie die Bezeichnung so, dass die Verschlüsselung **nur auf e-Mail-Nachrichten in Outlook**angewendet wird.

PowerShell-Beispiel Befehle, bei denen ihre Bezeichnung "nur Empfänger" heißt:

```PowerShell
Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeSign="True"}

Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeEncrypt="True"}
```

## <a name="specify-a-default-sublabel-for-a-parent-label"></a>Festlegen einer Standard untergeordneten Bezeichnung für eine übergeordnete Bezeichnung

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie einer Bezeichnung eine untergeordnete Bezeichnung hinzufügen, können Benutzer die übergeordnete Bezeichnung nicht mehr auf ein Dokument oder eine e-Mail anwenden. Standardmäßig wählen Benutzer die übergeordnete Bezeichnung aus, um die anzuwendenden untergeordneten Bezeichnungen anzuzeigen, und wählen dann eine dieser untergeordneten Bezeichnungen aus. Wenn Sie diese erweiterte Einstellung konfigurieren und Benutzer die übergeordnete Bezeichnung auswählen, wird automatisch eine untergeordnete Bezeichnung ausgewählt und darauf angewendet: 

- Schlüssel: **defaultsublabelid**

- Wert: \<sublabel GUID>

Beispiel für einen PowerShell-Befehl, bei dem die übergeordnete Bezeichnung "Confidential" heißt und die untergeordnete Bezeichnung "All Employees" eine GUID von 8faka7b8-8d20-48a3-8ea2-0F 96310a848e:

```PowerShell
Set-Label -Identity "Confidential" -AdvancedSettings @{DefaultSubLabelId="8faca7b8-8d20-48a3-8ea2-0f96310a848e"}
```

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Aktivieren der dauerhaft im Hintergrund ausgeführten Klassifizierung

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen. Diese Einstellung befindet sich in der Vorschauversion und kann sich ändern.

Wenn Sie diese Einstellung konfigurieren, wird das Standardverhalten geändert, wie der Azure Information Protection Unified Label-Client automatische und empfohlene Bezeichnungen auf Dokumente anwendet:

Für Word, Excel und PowerPoint wird die automatische Klassifizierung für Dokumente ständig im Hintergrund ausgeführt.

Das Verhalten für Outlook ändert sich nicht.
Wenn der Azure Information Protection Unified-Bezeichnungs Client regelmäßig Dokumente auf die von Ihnen angegebenen Bedingungs Regeln prüft, ermöglicht dieses Verhalten die automatische und empfohlene Klassifizierung und den Schutz für Dokumente, die in SharePoint gespeichert werden. Große Dateien werden schneller gespeichert, da die Bedingungsregeln bereits ausgeführt wurden.

Diese Bedingungsregeln werden nicht in Echtzeit, während der Benutzer tippt, ausgeführt. Stattdessen werden sie regelmäßig als Hintergrundaufgabe ausgeführt, wenn das Dokument geändert wird.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **RunPolicyInBackground**
- Wert: **true**



PowerShell-Beispiel Befehl: 

```PowerShell
Set-LabelPolicy -Identity PolicyName -AdvancedSettings @{RunPolicyInBackground = "true"}
```

## <a name="specify-a-color-for-the-label"></a>Farbe für die Bezeichnung angeben

Diese Konfiguration verwendet [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Verwenden Sie diese erweiterte Einstellung, um eine Farbe für eine Bezeichnung festzulegen. Um die Farbe anzugeben, geben Sie einen Hexadezimal Code für die Komponenten rot, grün und blau (RGB) der Farbe ein. Beispielsweise ist #40e0d0 der RGB-Hexadezimalwert für türkis.

Wenn Sie einen Verweis auf diese Codes benötigen, finden Sie eine hilfreiche Tabelle auf der [\<color>](https://developer.mozilla.org/docs/Web/CSS/color_value) Seite der MSDN-Webdokumentation. Außerdem finden Sie diese Codes in vielen Anwendungen, mit denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

Um die erweiterte Einstellung für die Farbe einer Bezeichnung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **Farbe**

- Wert: \<RGB hex value>

Beispiel für einen PowerShell-Befehl, bei dem Ihre Bezeichnung "Public" lautet:

```PowerShell
Set-Label -Identity Public -AdvancedSettings @{color="#40e0d0"}
```

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als anderer Benutzer anmelden, wenn Sie den Azure Information Protection Unified-Bezeichnungs Client verwenden. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

Mit dem Dialogfeld **Microsoft Azure Information Protection** können Sie überprüfen, welches Konto Sie gerade angemeldet sind: Öffnen Sie eine Office-Anwendung, und wählen Sie auf der Registerkarte **Startseite** die **Vertraulichkeits** Schaltfläche aus, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. Ein Symptom der Verwendung des falschen Kontos ist, dass die Bezeichnungen nicht heruntergeladen werden können oder dass die von Ihnen erwarteten Bezeichnungen oder das erwartete Verhalten nicht angezeigt werden.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und wählen Sie im Abschnitt aktualisierter **Client Status** die Option **Anmelden** aus.

Darüber hinaus gilt:

- Wenn der Azure Information Protection Unified Bezeichnung-Client nach dem Ausführen dieser Schritte weiterhin mit dem alten Konto angemeldet ist, löschen Sie alle Cookies aus Internet Explorer, und wiederholen Sie dann die Schritte 1 und 2.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich bei Windows abmelden und mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Tokendatei gelöscht haben. Der Azure Information Protection Unified Bezeichnung-Client wird dann automatisch mithilfe Ihres aktuell angemeldeten Benutzerkontos authentifiziert.

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- Sie können die Option **Einstellungen zurücksetzen** unter **Hilfe und Feedback** verwenden, um sich anzumelden und die derzeit heruntergeladenen Bezeichnungen und Richtlinien Einstellungen aus dem Office 365 Security & Compliance Center, dem Microsoft 365 Security Center oder dem Microsoft 365 Compliance Center zu löschen.


## <a name="support-for-disconnected-computers"></a>Unterstützung für getrennte Computer

> [!IMPORTANT]
> Getrennte Computer werden für die folgenden Bezeichnungs Szenarien unterstützt: Datei-Explorer, PowerShell, Office-Apps und Scanner.

Standardmäßig versucht der Azure Information Protection Unified Label-Client automatisch, eine Verbindung mit dem Internet herzustellen, um die Bezeichnungen und Bezeichnungs Richtlinien Einstellungen aus Ihrem Label Management Center herunterzuladen: Office 365 Security & Compliance Center, das Microsoft 365 Security Center oder das Microsoft 365 Compliance Center. Wenn Sie über Computer verfügen, die für einen bestimmten Zeitraum keine Verbindung mit dem Internet herstellen können, können Sie Dateien exportieren und kopieren, die die Richtlinie für den Unified-Bezeichnungs Client manuell verwalten.

Anleitung:

1. Wählen Sie ein Benutzerkonto in Azure AD aus, das Sie zum Herunterladen von Bezeichnungen und Richtlinien Einstellungen verwenden, die Sie auf dem nicht verbundenen Computer verwenden möchten, oder erstellen Sie ein Benutzerkonto.

2. Deaktivieren Sie als zusätzliche Bezeichnungs Richtlinien Einstellung für dieses Konto das Senden von Überwachungs [Daten an Azure Information Protection Analytics](#disable-sending-audit-data-to-azure-information-protection-analytics) mithilfe der erweiterten Einstellung **EnableAudit** .
    
    Dieser Schritt wird empfohlen, denn wenn der getrennte Computer über regelmäßige Internet Konnektivität verfügt, sendet er Protokollierungs Informationen an Azure Information Protection Analytics, der den Benutzernamen aus Schritt 1 enthält. Das Benutzerkonto kann sich von dem lokalen Konto unterscheiden, das Sie auf dem getrennten Computer verwenden.

3. Laden Sie auf einem Computer mit Internet Konnektivität, auf dem der Unified Label-Client installiert ist und der mit dem Benutzerkonto aus Schritt 1 angemeldet ist, die Bezeichnungen und Richtlinien Einstellungen herunter.

4. Exportieren Sie die Protokolldateien auf diesem Computer.
    
    Führen Sie beispielsweise das Cmdlet [Export-aiplogs](https://docs.microsoft.com/powershell/module/azureinformationprotection/export-aiplogs) aus, oder verwenden Sie im Dialogfeld [Hilfe und Feedback](clientv2-admin-guide.md#installing-and-supporting-the-azure-information-protection-unified-labeling-client) des Clients die Option **Protokolle exportieren** . 
    
    Die Protokolldateien werden als einzelne komprimierte Datei exportiert.

5.  Öffnen Sie die komprimierte Datei, und kopieren Sie aus dem Ordner MSIP alle Dateien mit der Dateinamenerweiterung XML.

6. Fügen Sie diese Dateien in den Ordner **%LocalAppData%\microsoft\msip** auf dem getrennten Computer ein.

7. Wenn Ihr ausgewähltes Benutzerkonto in der Regel eine Verbindung mit dem Internet herstellt, aktivieren Sie das Senden von Überwachungsdaten erneut, indem Sie den **EnableAudit** -Wert auf " **true**" festlegen.

Wenn ein Benutzer auf diesem Computer die Option **Einstellungen zurücksetzen** unter [Hilfe und Feedback](clientv2-admin-guide.md#help-and-feedback-section)auswählt, löscht diese Aktion die Richtlinien Dateien und rendert den Client als nicht funktionsfähig, bis Sie die Dateien manuell ersetzen oder der Client eine Verbindung mit dem Internet herstellt und die Dateien herunterlädt.

Wenn der nicht verbundene Computer den Azure Information Protection Scanner ausführen soll, müssen Sie zusätzliche Konfigurationsschritte ausführen. Weitere Informationen finden Sie unter [Einschränkung: der Scanner-Server kann keine Internet Konnektivität](../deploy-aip-scanner-prereqs.md#restriction-the-scanner-server-cannot-have-internet-connectivity) aus den Überprüfungs Anweisungen für die Überprüfung haben.

## <a name="change-the-local-logging-level"></a>Ändern des lokalen Protokolliergrads

Standardmäßig schreibt der Azure Information Protection Unified Bezeichnung-Client Client Protokolldateien in den Ordner **%LocalAppData%\microsoft\msip** . Diese Dateien dienen zur Problembehandlung durch den Microsoft-Support.
 
Um den Protokolliergrad für diese Dateien zu ändern, suchen Sie in der Registrierung nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf den erforderlichen Protokolliergrad fest:

**HKEY_CURRENT_USER \software\microsoft\msip\loglevel**

Legen Sie den Protokolliergrad auf einen der folgenden Werte fest:

- **Aus**: keine lokale Protokollierung.

- **Fehler**: nur Fehler.

- **Warnung**: Fehler und Warnungen.

- **Info**: minimale Protokollierung, die keine Ereignis-IDs (die Standardeinstellung für den Scanner) enthält.

- **Debug**: vollständige Informationen.

- Ablauf **Verfolgung**: ausführliche Protokollierung (die Standardeinstellung für Clients).

Mit dieser Registrierungs Einstellung werden die Informationen, die an Azure Information Protection für die [zentrale Berichterstattung](../reports-aip.md)gesendet werden, nicht geändert.

## <a name="skip-or-ignore-files-during-scans-depending-on-file-attributes"></a>Dateien während Scans in Abhängigkeit von Dateiattributen überspringen oder ignorieren

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig scannt der Azure Information Protection Unified-Beschriftungs Scanner alle relevanten Dateien. Möglicherweise möchten Sie jedoch bestimmte Dateien definieren, die übersprungen werden sollen, z. b. für archivierte Dateien oder Dateien, die verschoben wurden. 

Aktivieren Sie die Überprüfung, um bestimmte Dateien basierend auf Ihren Dateiattributen mithilfe der erweiterten **scannerfsattributestoskip** -Einstellung zu überspringen. Listen Sie im Einstellungs Wert die Dateiattribute auf, mit denen die Datei übersprungen werden kann, wenn Sie alle auf **true**festgelegt sind. Diese Liste von Dateiattributen verwendet die-und die-Logik.

Die folgenden PowerShell-Beispiel Befehle veranschaulichen, wie diese erweiterte Einstellung mit der Bezeichnung "Global" verwendet wird.

**Schreibgeschützte und archivierte Dateien überspringen**

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{ ScannerFSAttributesToSkip =" FILE_ATTRIBUTE_READONLY, FILE_ATTRIBUTE_ARCHIVE"}
```

**Lese-oder archivierte Dateien überspringen**

Wenn Sie eine-oder-Logik verwenden möchten, führen Sie die gleiche Eigenschaft mehrmals aus. Beispiel:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{ ScannerFSAttributesToSkip =" FILE_ATTRIBUTE_READONLY"}
Set-LabelPolicy -Identity Global -AdvancedSettings @{ ScannerFSAttributesToSkip =" FILE_ATTRIBUTE_ARCHIVE"}
```

> [!TIP]
> Es wird empfohlen, dass Sie die Überprüfung für das Überspringen von Dateien mit den folgenden Attributen in Erwägung ziehen:
> * FILE_ATTRIBUTE_SYSTEM
> * FILE_ATTRIBUTE_HIDDEN
> * FILE_ATTRIBUTE_DEVICE
> * FILE_ATTRIBUTE_OFFLINE
> * FILE_ATTRIBUTE_RECALL_ON_DATA_ACCESS
> * FILE_ATTRIBUTE_RECALL_ON_OPEN
> * FILE_ATTRIBUTE_TEMPORARY

Eine Liste aller Dateiattribute, die in der erweiterten Einstellung **scannerf sattributestoskip** definiert werden können, finden Sie unter [Win32-Datei Attribut Konstanten](https://docs.microsoft.com/windows/win32/fileio/file-attribute-constants) .

## <a name="preserve-ntfs-owners-during-labeling-public-preview"></a>Beibehalten von NTFS-Besitzern während der Bezeichnung (öffentliche Vorschau)

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig behalten die Bezeichnung Scanner, PowerShell und Datei-Explorer-Erweiterung den NTFS-Besitzer nicht bei, der vor der Bezeichnung definiert wurde. 

Um sicherzustellen, dass der NTFS-Besitzer Wert beibehalten wird, legen Sie für die ausgewählte Bezeichnungs Richtlinie die erweiterte Einstellung **usecopyandkonservientfsowner** auf **true** fest.

> [!CAUTION]
> Definieren Sie diese erweiterte Einstellung nur, wenn Sie eine zuverlässige Netzwerkverbindung mit geringer Latenz zwischen dem Scanner und dem gescannten Repository sicherstellen können. Ein Netzwerkfehler während des automatischen Bezeichnungs Prozesses kann dazu führen, dass die Datei verloren geht.

PowerShell-Beispiel Befehl, wenn Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

```PowerShell
Set-LabelPolicy -Identity Global -AdvancedSettings @{ UseCopyAndPreserveNTFSOwner ="true"}
```

## <a name="customize-justification-prompt-texts-for-modified-labels"></a>Anpassen von Bezeichnungs Text-Eingabeaufforderung für geänderte Bezeichnungen

Passen Sie die entsprechenden Eingabe Aufforderungen an, die sowohl in Office als auch im AIP-Client angezeigt werden, wenn Endbenutzer Klassifizierungs Bezeichnungen in Dokumenten und e-Mails ändern.

Beispielsweise können Sie als Administrator Ihre Benutzer daran erinnern, keine Kunden identifizierenden Informationen in diesem Feld hinzuzufügen:

:::image type="content" source="../media/justification-office.png" alt-text="Eingabeaufforderung für angepasste Begründung":::

Um den standardmäßigen **anderen** Text zu ändern, der angezeigt wird, verwenden Sie die erweiterte Eigenschaft "Recht **cationtextforusertext** " mit dem [Set-labelpolicy](https://docs.microsoft.com/powershell/module/exchange/set-labelpolicy) -Cmdlet. Legen Sie den Wert auf den Text fest, den Sie stattdessen verwenden möchten.

Beispiel:

``` PowerShell

[Set-LabelPolicy](https://docs.microsoft.com/powershell/module/exchange/set-labelpolicy) -Identity Global -AdvancedSettings @{JustificationTextForUserText="Other (please explain) - Do not enter sensitive info"}
```

## <a name="customize-outlook-popup-messages"></a>Anpassen von Outlook-Popup Meldungen

AIP-Administratoren können die Popup Meldungen anpassen, die Endbenutzern in Outlook angezeigt werden, wie z. b.:

- Nachrichten für blockierte e-Mails
- Warnmeldungen, die Benutzer auffordern, den Inhalt zu überprüfen, den Sie senden
- Ausrichtungmeldungen, die Benutzer anfordert, den Inhalt zu rechtfertigen, den Sie senden

**So passen Sie Outlook-Popup Meldungen an:**

1. Erstellen Sie **JSON** -Dateien mit einer Regel, die konfiguriert, wie Outlook Popup Nachrichten für Ihre Benutzer anzeigt. Weitere Informationen finden Sie unter [Regel Wert. JSON-Syntax](#rule-value-json-syntax) und [beispielpopup-customziierung. JSON-Code](#sample-popup-customziation-json-code).

1. Definieren Sie mithilfe von PowerShell Erweiterte Einstellungen, mit denen die Popup Meldungen gesteuert werden, die Sie konfigurieren. Führen Sie einen separaten Satz von Befehlen für jede Regel aus, die Sie konfigurieren möchten.

    Jeder Satz von PowerShell-Befehlen muss den Namen der Richtlinie enthalten, die Sie konfigurieren, sowie den Schlüssel und den Wert, der die Regel definiert.

    Verwenden Sie die folgende Syntax:

    ```PowerShell
    $filedata = Get-Content "<Path to json file>”
    Set-LabelPolicy -Identity <Policy name> -AdvancedSettings @{<Key> ="$filedata"}
    ```
    Hierbei gilt Folgendes: 

    - `<Path to json file>` ist der Pfad zur JSON-Datei, die Sie erstellt haben. Beispiel: **c:\users\msanchez\desktop\ \dlp\OutlookCollaborationRule_1.json**.
    - `<Policy name>` der Name der Richtlinie, die Sie konfigurieren möchten. 
    - `<Key>` ist ein Name für die Regel. Verwenden Sie die folgende Syntax, wobei **<#>** die Seriennummer Ihrer Regel ist: 
    
        `OutlookCollaborationRule_<x>` 

    Weitere Informationen finden Sie unter [Anordnen von Outlook-Regeln für customziierung](#ordering-your-outlook-customziation-rules) und [Regel Wert-JSON-Syntax](#rule-value-json-syntax).

   
> [!TIP]
> Benennen Sie Ihre Datei für zusätzliche Organisationen mit der gleichen Zeichenfolge wie der Schlüssel, der in Ihrem PowerShell-Befehl verwendet wird. Benennen Sie z. b. die Datei **OutlookCollaborationRule_1.js,** und verwenden Sie **OutlookCollaborationRule_1** als Schlüssel.
> 

### <a name="ordering-your-outlook-customziation-rules"></a>Bestellen der Outlook-customziationsregeln

AIP verwendet die Seriennummer in dem eingegebenen Schlüssel, um die Reihenfolge zu bestimmen, in der die Regeln verarbeitet werden. Wenn Sie die für jede Regel verwendeten Schlüssel definieren, definieren Sie die restriktiveren Regeln mit niedrigeren Zahlen, gefolgt von weniger restriktiven Regeln mit höheren Zahlen.

Sobald eine bestimmte Regel Übereinstimmung gefunden wird, beendet AIP die Verarbeitung der Regeln und führt die der abgleichsregel zugeordnete Aktion aus. (**Erste Übereinstimmung >** Beendigungs Logik)
    
**Beispiel:**

Nehmen wir an, Sie möchten alle **internen** e-Mails mit einer bestimmten **Warn** Meldung konfigurieren, aber Sie sollten Sie nicht in der Regel blockieren. Allerdings möchten Sie, dass Benutzer Anlagen, die als **geheim**klassifiziert sind, auch als **interne** e-Mails blockieren. 

Ordnen Sie in diesem Szenario ihren **Sperr Geheimnis** -Regel Schlüssel (die spezifischere Regel) vor ihrer allgemeineren **Warnung für den internen** Regel Schlüssel an:
- Für die **Block** Meldung: **OutlookCollaborationRule_1**
- Für die **Warn** Meldung: **OutlookCollaborationRule_2**

### <a name="rule-value-json-syntax"></a>Regelwert. JSON-Syntax

Definieren Sie die JSON-snytax Ihrer Regel wie folgt:

``` JSON
"type" : "And",
"nodes" : []
```

Sie müssen über mindestens zwei Knoten verfügen, der erste, der die Bedingung Ihrer Regel darstellt, und den letzten Vorgang, der die Aktion der Regel darstellt. Weitere Informationen finden Sie unter:

- [Syntax der Regel Bedingung](#rule-condition-syntax)
- [Syntax der Regel Aktion](#rule-action-syntax)

##### <a name="rule-condition-syntax"></a>Syntax der Regel Bedingung

Regel Bedingungs Knoten müssen den Knotentyp und dann die Bedingungen selbst enthalten. 

Zu den unterstützten Knoten Typen gehören:

|Knotentyp  |Beschreibung  |
|---------|---------|
| **Und**   | Führt *und* für alle untergeordneten Knoten aus.     |
| **Oder**    |Führt *oder* für alle untergeordneten Knoten aus.       |
| **Hätten**   | Führt *nicht* für das eigene untergeordnete Element aus.      |
| **Davon**    | Gibt *nicht* für das eigene untergeordnete Element zurück und bewirkt, dass es sich als **all** verhält.        |
| **SentTo,** gefolgt von **Domänen: ListofDomains**    |Überprüft eine der folgenden Aktionen: </br>-Wenn das übergeordnete Element **außer ist, überprüft,** ob sich **alle** Empfänger in einer der Domänen befinden.</br>-Wenn das übergeordnete Element etwas anderes ist **, aber außer, prüft,** ob einer der Empfänger in einer der Domänen **vorhanden** ist.   |
| **EmailLabel,** gefolgt von Bezeichnung | Einer der folgenden:  </br>-Die Bezeichnungs-ID </br>-NULL, wenn keine Bezeichnung             |
| **Attachmentlabel,** gefolgt von **Label** und **supportedextensions**    | Einer der folgenden:  </br></br>**Fall** </br>-Wenn das übergeordnete Element **außer ist, überprüft,** ob **alle** Anlagen mit einer unterstützten Erweiterung innerhalb der Bezeichnung vorhanden sind.</br>-Wenn das übergeordnete Element etwas anderes ist **, aber außer, prüft,** ob **eine** der Anlagen mit einer unterstützten Erweiterung innerhalb der Bezeichnung vorhanden ist. </br>-Wenn nicht bezeichnet, und **Bezeichnung = NULL** </br></br> **false:** Für alle anderen Fälle 
| | |

#### <a name="rule-action-syntax"></a>Syntax der Regel Aktion

Regel Aktionen können eines der folgenden sein:

|Aktion  |Syntax  |Beispielnachricht  |
|---------|---------|---------|
|**Blockieren**     |    `Block (List<language, [title, body]>)`     |    ***E-Mail blockiert***</br></br>  *Sie sind im Begriff, Inhalte, die als **geheim** klassifiziert sind, an einen oder mehrere nicht vertrauenswürdige Empfänger zu senden:*</br>*`rsinclair@contoso.com`*</br></br>*Diese Aktion wird von ihrer Organisations Richtlinie nicht zugelassen. Entfernen Sie diese Empfänger, oder ersetzen Sie den Inhalt.*|
|**Warnen**     | `Warn (List<language,[title,body]>)`        |  ***Bestätigung erforderlich***</br></br>*Sie sind im Begriff, Inhalte, die als **Allgemein** klassifiziert sind, an einen oder mehrere nicht vertrauenswürdige Empfänger zu senden:*</br>*`rsinclair@contoso.com`*</br></br>*Ihre Organisations Richtlinie erfordert eine Bestätigung, dass Sie diesen Inhalt senden müssen.*       |
|**Fertigte**     | `Justify (numOfOptions, hasFreeTextOption, List<language, [Title, body, options1,options2….]> )` </br></br>Einschließlich bis zu drei Optionen.        |  ***Begründung erforderlich*** </br></br>*Ihre Organisations Richtlinie erfordert eine Begründung, um Inhalte zu senden, die als **Allgemein** an nicht vertrauenswürdige Empfänger klassifiziert sind.*</br></br>*-Ich bestätige, dass die Empfänger für die Freigabe dieses Inhalts genehmigt sind.*</br>*-Mein Manager hat die Freigabe dieses Inhalts genehmigt*</br>*-Andere, wie erläutert* |
| | | |

##### <a name="action-parameters"></a>Aktionsparameter

Wenn für eine Aktion keine Parameter bereitgestellt werden, verfügen die Popups über den Standardtext. 

Alle Texte unterstützen die folgenden dynamischen Parameter: 

|Parameter  |Beschreibung  |
|---------|---------|
| `${MatchedRecipientsList}`  | Die letzte Entsprechung für die **SentTo** -Bedingungen.       |
| `${MatchedLabelName}`      | Die **Bezeichnung** "Mail/Anlage" mit dem lokalisierten Namen aus der Richtlinie               |
| `${MatchedAttachmentName}` | Der Name der Anlage aus der letzten Entsprechung für die **attachmentlabel** -Bedingung. |
| | |

> [!NOTE]
> Alle Meldungen enthalten die Option " **Weitere Informationen** " sowie die Dialogfelder " **Hilfe** " und " **Feedback** ".
>
> Die **Sprache** ist der **cultureName** für den Gebiets Schema Namen, z. b.: **Englisch**  =  `en-us` ; **Spanisch** = `es-es`
>
> Nur übergeordnete Sprachnamen werden unterstützt, z `en` . b..
> 

### <a name="sample-popup-customziation-json-code"></a>Beispielpopup-Beispiel für customziierung. JSON-Code

Die folgenden Sätze von **JSON** -Code veranschaulichen, wie Sie eine Reihe von Regeln definieren können, die Steuern, wie Outlook Popup Meldungen für Ihre Benutzer anzeigt.

- [**Beispiel 1**: blockieren interner e-Mails oder Anhänge](#example-1-block-internal-emails-or-attachments)
- [**Beispiel 2**: Blockieren von nicht klassifizierten Office-Anlagen](#example-2-block-unclassified-office-attachments)
- [**Beispiel 3**: verlangen Sie, dass der Benutzer das Senden einer vertraulichen e-Mail oder Anlage akzeptiert.](#example-3-require-the-user-to-accept-sending-a-confidential-email-or-attachment)
- [**Beispiel 4**: warnen bei e-Mail ohne Bezeichnung und einer Anlage mit einer bestimmten Bezeichnung](#example-4-warn-on-mail-with-no-label-and-an-attachment-with-a-specific-label)
- [**Beispiel 5**: Aufforderung zur Eingabe eines rechtfertigen Befehls mit zwei vordefinierten Optionen und einer zusätzlichen Free-Text-Option](#example-5-prompt-for-a-justificaiton-with-two-predefined-options-and-an-extra-free-text-option)

#### <a name="example-1-block-internal-emails-or-attachments"></a>Beispiel 1: blockieren interner e-Mails oder Anhänge

Der folgende **JSON** -Code verhindert, dass e-Mails oder Anhänge, die als **intern** klassifiziert werden, auf externe Empfänger festgelegt werden.

In diesem Beispiel ist **89a453df-5df4-4976-8191-259d0cf9560a** die ID der **internen** Bezeichnung, und interne Domänen enthalten **contoso.com** und **Microsoft.com**.

```powershell
{   
    "type" : "And",     
    "nodes" : [         
        {           
            "type" : "Except" ,             
            "node" :{               
                "type" : "SentTo",                  
                "Domains" : [                   
                    "contoso.com",                  
              "microsoft.com"
                ]               
            }       
        },
        {           
            "type" : "Or",          
            "nodes" : [                 
                {           
                    "type" : "AttachmentLabel",             
                    "LabelId" : "89a453df-5df4-4976-8191-259d0cf9560a"      
                },{                     
                    "type" : "EmailLabel",                  
                    "LabelId" : "89a453df-5df4-4976-8191-259d0cf9560a"              
                }
            ]
        },      
        {           
            "type" : "Block",           
            "LocalizationData": {               
                "en-us": {                
                    "Title": "Email Blocked",                 
                    "Body": "The email or at least one of the attachments is classified as <Bold>${MatchedLabelName}</Bold>. Documents classified as <Bold> ${MatchedLabelName}</Bold> cannot be sent to external recipients (${MatchedRecipientsList}).<br><br>List of attachments classified as <Bold>${MatchedLabelName}</Bold>:<br><br>${MatchedAttachmentName}<br><br><br>This message will not be sent.<br>You are responsible for ensuring compliance with classification requirements as per Contoso’s policies."               
                },              
                "es-es": {                
                    "Title": "Correo electrónico bloqueado",                  
                    "Body": "El correo electrónico o al menos uno de los archivos adjuntos se clasifica como <Bold> ${MatchedLabelName}</Bold>."                
                }           
            },          
            "DefaultLanguage": "en-us"      
        }   
    ] 
}
```

#### <a name="example-2-block-unclassified-office-attachments"></a>Beispiel 2: Blockieren von nicht klassifizierten Office-Anlagen

Mit dem folgenden **JSON** -Code wird verhindert, dass nicht klassifizierte Office-Anlagen oder e-Mails an externe-eints gesendet werden.

Im folgenden Beispiel ist die Anlagen Liste, die eine Bezeichnung erfordert,: **. doc,. DOCM,. docx,. dot,. dotm,. DOTX,. POTM,. POTX,. PPS,. ppsm,. ppsx,. ppt,. pptm,. pptx,. VDW,. vsd,. vsdm,. vsdx,. VSS,. VSSM,. VST,. VSTM,. vssx,. vstx,. xls,. xlsb,. xlt,. xlsm,. xlsx,. xltm,. xltx**

```powershell
{   
    "type" : "And",     
    "nodes" : [         
        {           
            "type" : "Except" ,             
            "node" :{               
                "type" : "SentTo",                  
                "Domains" : [                   
                    "contoso.com",                  
                    "microsoft.com"
                ]               
            }       
        },
        {           
            "type" : "Or",          
            "nodes" : [                 
                {           
                    "type" : "AttachmentLabel",
                     "LabelId" : null,
                    "Extensions": [
                                    ".doc",
                                    ".docm",
                                    ".docx",
                                    ".dot",
                                    ".dotm",
                                    ".dotx",
                                    ".potm",
                                    ".potx",
                                    ".pps",
                                    ".ppsm",
                                    ".ppsx",
                                    ".ppt",
                                    ".pptm",
                                    ".pptx",
                                    ".vdw",
                                    ".vsd",
                                    ".vsdm",
                                    ".vsdx",
                                    ".vss",
                                    ".vssm",
                                    ".vst",
                                    ".vstm",
                                    ".vssx",
                                    ".vstx",
                                    ".xls",
                                    ".xlsb",
                                    ".xlt",
                                    ".xlsm",
                                    ".xlsx",
                                    ".xltm",
                                    ".xltx"
                                 ]
                    
                },{                     
                    "type" : "EmailLabel",
                     "LabelId" : null
                }
            ]
        },      
        {           
            "type" : "Email Block",             
            "LocalizationData": {               
                "en-us": {                
                    "Title": "Emailed Blocked",                   
                    "Body": "Classification is necessary for attachments to be sent to external recipients.<br><br>List of attachments that are not classified:<br><br>${MatchedAttachmentName}<br><br><br>This message will not be sent.<br>You are responsible for ensuring compliance to classification requirement as per Contoso’s policies.<br><br>For MS Office documents, classify and send again.<br><br>For PDF files, classify the document or classify the email (using the most restrictive classification level of any single attachment or the email content) and send again."               
                },              
                "es-es": {                
                    "Title": "Correo electrónico bloqueado",                  
                    "Body": "La clasificación es necesaria para que los archivos adjuntos se envíen a destinatarios externos."              
                }           
            },          
            "DefaultLanguage": "en-us"      
        }   
    ] 
}
```

#### <a name="example-3-require-the-user-to-accept-sending-a-confidential-email-or-attachment"></a>Beispiel 3: verlangen Sie, dass der Benutzer das Senden einer vertraulichen e-Mail oder Anlage akzeptiert.

Im folgenden Beispiel wird in Outlook eine Meldung angezeigt, in der der Benutzer gewarnt wird, dass Sie eine **vertrauliche** e-Mail oder eine Anlage an externe Empfänger sendet. Außerdem muss der Benutzer die **Annahme**auswählen. 

Diese Art von Warnmeldung wird technisch gesehen als eine Begründung betrachtet, da der Benutzer **Ich akzeptiere**auswählen muss.

``` powershell
{   
    "type" : "And",     
    "nodes" : [         
        {           
            "type" : "Except" ,             
            "node" :{               
                "type" : "SentTo",                  
                "Domains" : [                   
                    "contoso.com",                  
                    "microsoft.com"
                ]               
            }       
        },
        {           
            "type" : "Or",          
            "nodes" : [                 
                {           
                    "type" : "AttachmentLabel",             
                    "LabelId" : "3acd2acc-2072-48b1-80c8-4da23e245613"      
                },{                     
                    "type" : "EmailLabel",                  
                    "LabelId" : "3acd2acc-2072-48b1-80c8-4da23e245613"              
                }
            ]
        },      
        {           
            "type" : "Justify",             
            "LocalizationData": {               
                "en-us": {                
                    "Title": "Warning",                   
                    "Body": "You are sending a document that is classified as <Bold>${MatchedLabelName}</Bold> to at least one external recipient. Please make sure that the content is correctly classified and that the recipients are entitled to receive this document.<br><br>List of attachments classified as <Bold>${MatchedLabelName}</Bold>:<br><br>${MatchedAttachmentName}<br><br><Bold>List of external email addresses:</Bold><br>${MatchedRecipientsList})<br><br>You are responsible for ensuring compliance to classification requirement as per Contoso’s policies.<br><br><Bold>Acknowledgement</Bold><br>By clicking <Bold>I accept<\Bold> below, you confirm that the recipient is entitled to receive the content and the communication complies with CS Policies and Standards",
                    "Options": [                        
                        "I accept"              
                    ] 
                },              
                "es-es": {                
                    "Title": "Advertencia",                   
                    "Body": "Está enviando un documento clasificado como <Bold>${MatchedLabelName}</Bold> a al menos un destinatario externo. Asegúrese de que el contenido esté correctamente clasificado y que los destinatarios tengan derecho a recibir este documento.",
                    "Options": [                        
                        "Acepto"                    
                    ]                   
                }           
            },          
            "HasFreeTextOption":"false",            
            "DefaultLanguage": "en-us"      
        }   
    ] 
}
```

#### <a name="example-4-warn-on-mail-with-no-label-and-an-attachment-with-a-specific-label"></a>Beispiel 4: warnen bei e-Mail ohne Bezeichnung und einer Anlage mit einer bestimmten Bezeichnung

Der folgende **JSON-Code** bewirkt, dass Outlook den Benutzer warnt, wenn er eine interne e-Mail sendet, die keine Bezeichnung hat und eine Anlage mit einer bestimmten Bezeichnung aufweist. 

In diesem Beispiel ist **bcbef25a-c4db-446b-9496-1b558d9edd0e** die ID der Bezeichnung der Anlage.

Standardmäßig erhalten e-Mails mit der Bezeichnung Anhänge nicht automatisch dieselbe Bezeichnung.

```powershell
{   
    "type" : "And",     
    "nodes" : [         
        {           
            "type" : "EmailLabel",
                     "LabelId" : null           
        },
        {
          "type": "AttachmentLabel",
          "LabelId": "bcbef25a-c4db-446b-9496-1b558d9edd0e",
          "Extensions": [
                ".docx",
                ".xlsx",
                ".pptx"
             ]
        },
    {           
            "type" : "SentTo",              
            "Domains" : [               
                "contoso.com",              
            ]           
        },      
        {           
            "type" : "Warn" 
        }   
    ] 
}
```

#### <a name="example-5-prompt-for-a-justificaiton-with-two-predefined-options-and-an-extra-free-text-option"></a>Beispiel 5: Aufforderung zur Eingabe eines rechtfertigen Befehls mit zwei vordefinierten Optionen und einer zusätzlichen Free-Text-Option

Der folgende **JSON** -Code bewirkt, dass Outlook den Benutzer zur Eingabe einer Begründung für seine Aktion auffordert. Der Text für die Begründung enthält zwei vordefinierte Optionen sowie eine dritte, freie Text Option.

```PowerShell
{   
    "type" : "And",     
    "nodes" : [         
        {           
            "type" : "Except" ,             
            "node" :{               
                "type" : "SentTo",                  
                "Domains" : [                   
                    "contoso.com",                                  
                ]               
            }       
        },      
        {           
            "type" : "EmailLabel",          
            "LabelId" : "34b8beec-40df-4219-9dd4-553e1c8904c1"      
        },      
        {           
            "type" : "Justify",             
            "LocalizationData": {               
                "en-us": {                  
                    "Title": "Justification Required",                  
                    "Body": "Your organization policy requires justification for you to send content classified as <Bold> ${MatchedLabelName}</Bold>,to untrusted recipients:<br>Recipients are: ${MatchedRecipientsList}",                     
                    "Options": [                        
                        "I confirm the recipients are approved for sharing this content",                   
                        "My manager approved sharing of this content",                      
                        "Other, as explained"                   
                    ]               
                },              
                "es-es": {                  
                    "Title": "Justificación necesaria",                     
                    "Body": "La política de su organización requiere una justificación para que envíe contenido clasificado como <Bold> ${MatchedLabelName}</Bold> a destinatarios que no sean de confianza.",                  
                    "Options": [                        
                        "Confirmo que los destinatarios están aprobados para compartir este contenido.",
                        "Mi gerente aprobó compartir este contenido",
                        "Otro, como se explicó"                     
                    ]               
                }           
            },          
            "HasFreeTextOption":"true",             
            "DefaultLanguage": "en-us"      
        }   
    ] 
}
```

## <a name="configure-sharepoint-timeouts"></a>Konfigurieren von SharePoint-Timeouts

Standardmäßig beträgt das Timeout für SharePoint-Interaktionen zwei Minuten, nach denen der versuchte AIP-Vorgang fehlschlägt.

Ab [Version 2.8.85](unifiedlabelingclient-version-release-history.md#version-2885-public-preview)können AIP-Administratoren dieses Timeout mithilfe der folgenden erweiterten Eigenschaften steuern, indem Sie eine **hh: mm: SS** -Syntax verwenden, um die Timeouts zu definieren:

- **Sharepointwebrequesttimeout**. Bestimmt das Timeout für alle AIP-Webanforderungen für SharePoint. Standardwert = 2 Minuten.

    Wenn Ihre Richtlinie beispielsweise **Global**benannt ist, aktualisiert der folgende PowerShell-Beispiel Befehl den Timeout Wert für die Webanforderung auf 5 Minuten.

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{SharepointWebRequestTimeout="00:05:00"}
    ```

- **Sharepointfilewebrequesttimeout**. Bestimmt das Timeout speziell für SharePoint-Dateien über AIP-Webanforderungen. Standardwert = 15 Minuten

    Wenn Ihre Richtlinie beispielsweise **Global**benannt ist, aktualisiert der folgende PowerShell-Beispiel Befehl den Timeout Wert für die Datei-Webanforderung auf 10 Minuten.

    ```PowerShell
    Set-LabelPolicy -Identity Global -AdvancedSettings @{SharepointFileWebRequestTimeout="00:10:00"}
    ```

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client angepasst haben, finden Sie in den folgenden Ressourcen weitere Informationen, die Sie möglicherweise benötigen, um diesen Client zu unterstützen:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
