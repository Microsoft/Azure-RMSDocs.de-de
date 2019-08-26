---
title: Benutzerdefinierte Konfigurationen-Azure Information Protection Unified-Beschriftungs Client
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 08/19/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.subservice: v2client
ms.reviewer: maayan
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: f60c1bdc8dabd586e96c758afe1f93f46d6afb16
ms.sourcegitcommit: 0d336e4b5386f4861db9492c7dce2ef0e8cf0d6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017658"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-unified-labeling-client"></a>Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection Unified-Bezeichnungs Client

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection Unified Bezeichnung-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie möglicherweise für bestimmte Szenarien oder eine Teilmenge von Benutzern benötigen, wenn Sie den Azure Information Protection Unified Bezeichnung-Client verwalten.

Für diese Einstellungen müssen Sie die Registrierung bearbeiten oder erweiterte Einstellungen angeben. Die erweiterten Einstellungen verwenden [Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps).

### <a name="how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell"></a>Konfigurieren erweiterter Einstellungen für den Client mithilfe von Office 365 Security & Compliance Center PowerShell

Wenn Sie Office 365 Security & Compliance Center PowerShell verwenden, können Sie erweiterte Einstellungen konfigurieren, die Anpassungen für Bezeichnungs Richtlinien und Bezeichnungen unterstützen. Zum Beispiel:

- Die Einstellung zum Anzeigen der Information Protection Leiste in Office-Apps ist eine ***Erweiterte Einstellung der Bezeichnung "Bezeichnung***".
- Die Einstellung zum Angeben einer Bezeichnungs Farbe ist eine ***Erweiterte Einstellung***für die Bezeichnung.

Geben Sie in beiden Fällen nach dem [Herstellen einer Verbindung mit Office 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell?view=exchange-ps)den Parameter *advancedsettings* mit der Identität (Name oder GUID) der Richtlinie oder Bezeichnung an, und geben Sie Schlüssel-Wert-Paare in einer [Hash Tabelle](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables)an. Verwenden Sie die folgende Syntax:

Für eine Bezeichnungs Richtlinieneinstellung ist ein einzelner Zeichen folgen Wert:

    Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key="value1,value2"}

Für Bezeichnungs Richtlinien Einstellungen werden mehrere Zeichen folgen Werte für den gleichen Schlüssel angezeigt:

    Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}

Für eine Bezeichnungs Einstellung lautet der Wert einer einzelnen Zeichenfolge:

    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key="value1,value2"}

Für Bezeichnungs Einstellungen werden mehrere Zeichen folgen Werte für denselben Schlüssel angezeigt:

    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}

Verwenden Sie die gleiche Syntax, und geben Sie einen NULL-Zeichen folgen Wert an, um eine erweiterte Einstellung zu entfernen.


#### <a name="examples-for-setting-advanced-settings"></a>Beispiele für das Festlegen von erweiterten Einstellungen

Beispiel 1: Legen Sie für einen einzelnen Zeichen folgen Wert eine erweiterte Einstellung für die Bezeichnungs Richtlinie fest:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}

Beispiel 2: Legen Sie die Einstellung für die erweiterte Bezeichnung für einen einzelnen Zeichen folgen Wert fest:

    Set-Label -Identity Internal -AdvancedSettings @{smimesign="true"}

Beispiel 3: Legen Sie für mehrere Zeichen folgen Werte eine Einstellung für die erweiterte Bezeichnung fest:

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}

Beispiel 4: Entfernen Sie eine erweiterte Einstellung für eine Bezeichnungs Richtlinie durch Angabe eines NULL-Zeichen folgen Werts:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions=""}

#### <a name="specifying-the-identity-for-the-label-policy-or-label"></a>Angeben der Identität für die Bezeichnungs Richtlinie oder-Bezeichnung

Das Angeben des Namens der Bezeichnungs Richtlinie für den PowerShell- *Identitäts* Parameter ist einfach, da im Admin Center nur ein Richtlinien Name angezeigt wird, in dem Sie Ihre Bezeichnungs Richtlinien verwalten. Für Bezeichnungen werden jedoch sowohl ein **Name** als auch ein **Anzeige Name** in den Admin Centers angezeigt. In einigen Fällen ist der Wert für beide identisch, aber Sie können sich unterscheiden:

- **Name** ist der ursprüngliche Name der Bezeichnung, der in allen Bezeichnungen eindeutig ist. Wenn Sie den Namen der Bezeichnung nach der Erstellung ändern, bleibt dieser Wert unverändert. Bei Bezeichnungen, die von Azure Information Protection migriert wurden, wird möglicherweise die Bezeichnungs-ID der Bezeichnung aus der Azure-Portal angezeigt.

- Der **Anzeige Name** ist der Name der Bezeichnung, die Benutzern angezeigt wird, und Sie muss in allen Bezeichnungen nicht eindeutig sein. Beispielsweise sehen Benutzer eine unter geordnete Bezeichnung für " **vertraulich** " und eine andere untergeordnete Bezeichnung für die Bezeichnung " **streng vertraulich** ". Diese untergeordneten Bezeichnungen sehen beide denselben Namen, sind jedoch nicht die gleiche Bezeichnung und haben andere Einstellungen.

Verwenden Sie zum Konfigurieren der erweiterten Einstellungen für die Bezeichnung den Wert " **Name** ". Um z. b. die Bezeichnung in der folgenden Abbildung zu identifizieren, geben `-Identity "All Company"`Sie Folgendes an:

![Verwenden Sie "Name" anstelle von "Anzeige Name", um eine Vertraulichkeits Bezeichnung zu identifizieren.](../media/labelname_scc.png)

Wenn Sie die GUID der Bezeichnung angeben möchten, wird dieser Wert nicht im Admin Center angezeigt, in dem Sie Ihre Bezeichnungen verwalten. Sie können jedoch den folgenden Office 365 Security & Compliance Center PowerShell-Befehl verwenden, um diesen Wert zu finden:

    Get-Label | Format-Table -Property DisplayName, Name, Guid


#### <a name="order-of-precedence---how-conflicting-settings-are-resolved"></a>Rangfolge: so werden widersprüchliche Einstellungen aufgelöst

Mit einem der Admin Center, in dem Sie Ihre Vertraulichkeits Bezeichnungen verwalten, können Sie die folgenden Bezeichnungs Richtlinien Einstellungen konfigurieren:

- **Diese Bezeichnung standardmäßig auf Dokumente und e-Mails anwenden**

- **Benutzer müssen eine Begründung angeben, um eine Bezeichnung oder eine niedrigere Klassifizierungs Bezeichnung zu entfernen.**

- **Erzwingen, dass Benutzer eine Bezeichnung auf Ihre e-Mail oder Ihr Dokument anwenden**

- **Bereitstellen eines Links zu einer benutzerdefinierten Hilfeseite für Benutzer**

Wenn für einen Benutzer mehr als eine Bezeichnungs Richtlinie konfiguriert ist, von denen jede möglicherweise unterschiedliche Richtlinien Einstellungen hat, wird die letzte Richtlinien Einstellung gemäß der Reihenfolge der Richtlinien im Admin Center angewendet. Weitere Informationen finden Sie unter [Bezeichnung der Richtlinien Priorität (Reihenfolge wichtig)](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels#label-policy-priority-order-matters) .

Die erweiterten Einstellungen für die Bezeichnung Folgen der gleichen Logik für die Rangfolge: Wenn sich eine Bezeichnung in mehreren Bezeichnungs Richtlinien befindet und diese Bezeichnung Erweiterte Einstellungen aufweist, wird die letzte erweiterte Einstellung gemäß der Reihenfolge der Richtlinien im Admin Center angewendet.

Erweiterte Einstellungen der Bezeichnungs Richtlinie werden in umgekehrter Reihenfolge angewendet: Mit einer Ausnahme werden die erweiterten Einstellungen der ersten Richtlinie entsprechend der Reihenfolge der Richtlinien im Admin Center angewendet. Bei der Ausnahme handelt es sich um die erweiterte Einstellung *outlookdefaultlabel*, mit der eine andere Standard Bezeichnung für Outlook festgelegt wird. Bei dieser Einstellung für die erweiterte Bezeichnung "Bezeichnung" wird die letzte Einstellung gemäß der Reihenfolge der Richtlinien im Admin Center angewendet.

#### <a name="available-advanced-settings-for-label-policies"></a>Verfügbare erweiterte Einstellungen für Bezeichnungs Richtlinien

Verwenden Sie den *advancedsettings* -Parameter mit [New-labelpolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-labelpolicy?view=exchange-ps) und [Set-labelpolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-labelpolicy?view=exchange-ps).

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|Attachmentaction|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
|Attachmentaktiontip|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments) 
|Disablemandatoryinoutlook|[Ausschließen von Outlook-Nachrichten von der obligatorischen Bezeichnung](#exempt-outlook-messages-from-mandatory-labeling)
|EnableAudit|[Deaktivieren des Sendens von Überwachungsdaten an Azure Information Protection Analytics](#disable-sending-audit-data-to-azure-information-protection-analytics)|
|EnableCustomPermissions|[Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer](#disable-custom-permissions-in-file-explorer)|
|EnableCustomPermissionsForCustomProtectedFiles|[Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer) |
|EnableLabelByMailHeader|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|Hidebarbydefault|[Information Protection-Leiste in Office-Apps anzeigen](##display-the-information-protection-bar-in-office-apps)|
|LogMatchedContent|[Deaktivieren der Übereinstimmungen des Sendeinformationstyps für eine Teilmenge von Benutzern](#disable-sending-information-type-matches-for-a-subset-of-users)|
|OutlookBlockTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookBlockUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookDefaultLabel|[Festlegen einer anderen Standardbezeichnung für Outlook](#set-a-different-default-label-for-outlook)|
|OutlookJustifyTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookJustifyUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookRecommendationEnabled|[Die empfohlene Klassifizierung in Outlook aktivieren](#enable-recommended-classification-in-outlook)|
|OutlookOverrideUnlabeledCollaborationExtensions|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|Outlookunlabeledcollaborationaktionoverridemailbodybehavior|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|PostponeMandatoryBeforeSave|[Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|RemoveExternalContentMarkingInApp|[Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Add "Report an Issue" for users](#add-report-an-issue-for-users) ("Problem melden" für Benutzer hinzufügen)|
|Runauditinformationtypesdiscovery|[Hiermit wird das Senden von ermittelten sensiblen Informationen in Dokumenten an Azure Information Protection Analytics deaktiviert.](#disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics)|

PowerShell-Beispiel Befehl zum Überprüfen Ihrer Bezeichnungs Richtlinien Einstellungen für eine Bezeichnungs Richtlinie mit dem Namen "Global":

    (Get-LabelPolicy -Identity Global).settings

#### <a name="available-advanced-settings-for-labels"></a>Verfügbare erweiterte Einstellungen für Bezeichnungen

Verwenden Sie den *advancedsettings* -Parameter mit [New-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-label?view=exchange-ps) und [Set-Label](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/set-label?view=exchange-ps).

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|Farbe|[Farbe für die Bezeichnung angeben](#specify-a-color-for-the-label)|
|custompropertiesbylabel|[Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird](#apply-a-custom-property-when-a-label-is-applied)|
|DefaultSubLabelId|[Festlegen einer Standard untergeordneten Bezeichnung für eine übergeordnete Bezeichnung](#specify-a-default-sublabel-for-a-parent-label) 
|labelbycustomproperties|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|SMimeEncrypt|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|
|SMimeSign|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|

PowerShell-Beispiel Befehl zum Überprüfen Ihrer Bezeichnungs Einstellungen für eine Bezeichnung mit dem Namen "Public":

    (Get-Label -Identity Public).settings

## <a name="display-the-information-protection-bar-in-office-apps"></a>Information Protection-Leiste in Office-Apps anzeigen

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig müssen Benutzer die Option **Leiste anzeigen** auf der Vertraulichkeits Schaltfläche auswählen, um die Information Protection Leiste in Office-Apps anzuzeigen. Verwenden Sie den **hidebarbydefault** -Schlüssel, und legen Sie den Wert auf " **false** " fest, um diese Leiste für Benutzer automatisch anzuzeigen, damit Sie Bezeichnungen aus der Leiste oder der Schaltfläche auswählen können. 

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **HideBarByDefault**

- Wert: **False**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{HideBarByDefault="False"}

## <a name="exempt-outlook-messages-from-mandatory-labeling"></a>Ausschließen von Outlook-Nachrichten von der obligatorischen Bezeichnung

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die Bezeichnungs Richtlinien Einstellung für **alle Dokumente aktivieren und e-Mails über eine Bezeichnung verfügen müssen**, muss für alle gespeicherten Dokumente und gesendeten e-Mails standardmäßig eine Bezeichnung angewendet werden. Wenn Sie die folgende erweiterte Einstellung konfigurieren, gilt die Richtlinien Einstellung nur für Office-Dokumente und nicht für Outlook-Nachrichten.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **Disablemandatoryinoutlook**

- Wert: **True**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{DisableMandatoryInOutlook="True"}

## <a name="enable-recommended-classification-in-outlook"></a>Aktivieren der empfohlenen Klassifizierung in Outlook

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie eine Bezeichnung für die empfohlene Klassifizierung konfigurieren, werden Benutzer dazu aufgefordert, die empfohlene Bezeichnung in Word, Excel und PowerPoint anzunehmen oder abzulehnen. Diese Einstellung erweitert diese Bezeichnungsempfehlung, sodass sie auch in Outlook angezeigt wird.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **OutlookRecommendationEnabled**

- Wert: **True**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookRecommendationEnabled="True"}

## <a name="set-a-different-default-label-for-outlook"></a>Festlegen anderer Standardbezeichnung für Outlook

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie diese Einstellung konfigurieren, wendet Outlook nicht die Standard Bezeichnung an, die als Richtlinien Einstellung für die Option **diese Bezeichnung standardmäßig auf Dokumente und e-Mails anwenden**konfiguriert ist. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **OutlookDefaultLabel**

- Wert: \<Bezeichnungs- **GUID**> oder **None**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookDefaultLabel="None"}


## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>„Not now“ („Nicht jetzt“) für Dokumente bei Verwendung der obligatorischen Bezeichnung entfernen

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die Bezeichnung "Bezeichnung" für **alle Dokumente verwenden, und e-Mails müssen eine Bezeichnung aufweisen**, werden die Benutzer beim ersten Speichern eines Office-Dokuments und beim Senden einer e-Mail aufgefordert, eine Bezeichnung auszuwählen. Bei Office-Dokumenten können Benutzer **Not now** (nicht jetzt) wählen, um die Aufforderung zum Auswählen einer Bezeichnung vorübergehend zu schließen und zum Dokument zurückzukehren. Sie können das gespeicherte Dokument jedoch nicht schließen, ohne es zu bezeichnen. 

Wenn Sie diese Einstellung konfigurieren, wird die Option **Not now** (nicht jetzt) entfernt, sodass die Benutzer eine Bezeichnung wählen müssen, wenn das Dokument zum ersten Mal gespeichert wird.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **PostponeMandatoryBeforeSave**

- Wert: **False**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{PostponeMandatoryBeforeSave="False"}

## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen

Diese Konfiguration verwendet [Erweiterte Richtlinien Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Mit diesen Einstellungen können Sie textbasierte Kopf- und Fußzeilen in Dokumenten entfernen oder ersetzen, wenn diese optischen Kennzeichnungen von einer anderen Bezeichnungslösung angewendet wurden. Beispielsweise enthält die alte Fußzeile den Namen einer alten Bezeichnung, die Sie nun zu den Vertraulichkeits Bezeichnungen migriert haben, um einen neuen Bezeichnungs Namen und eine eigene Fußzeile zu verwenden.

Wenn der Unified Label-Client diese Konfiguration in der Richtlinie abruft, werden die alten Kopf-und Fußzeilen entfernt oder ersetzt, wenn das Dokument in der Office-App geöffnet wird und jede Vertraulichkeits Bezeichnung auf das Dokument angewendet wird.

Diese Konfiguration wird für Outlook nicht unterstützt. Beachten Sie außerdem, dass die Verwendung mit Word, Excel und PowerPoint sich negativ auf die Leistung dieser Apps für Benutzer auswirken kann. Mithilfe der Konfiguration können Sie Einstellungen für jede einzelne Anwendung definieren, z.B. die Suche nach Text in Kopf- oder Fußzeilen von Word-Dokumenten, jedoch nicht von Excel-Tabellen oder PowerPoint-Präsentationen.

Da der Musterabgleich die Leistung für Benutzer beeinflusst, empfiehlt es sich, die Office-Anwendungs Typen (**W**Ord, **E**Xcel, **P**owerpoint) nur auf die zu durchsuchenden Personen einzuschränken.

Geben Sie für die ausgewählte Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **RemoveExternalContentMarkingInApp**

- Wert: \<**Office-Anwendungstypen WXP**> 

Beispiele:

- Geben Sie **W** an, um nur Word-Dokumente zu durchsuchen.

- Geben Sie **WP** an, um Word-Dokumente und PowerPoint-Präsentationen zu durchsuchen.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

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

Geben Sie für dieselbe Bezeichnungs Richtlinie die folgenden Zeichen folgen an:

- Key: **ExternalContentMarkingToRemove**

- Value: \<**zu vergleichende Zeichenfolge; als regulärer Ausdruck definiert**> 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*TEXT*"}

#### <a name="multiline-headers-or-footers"></a>Mehrzeilige Kopf- oder Fußzeilen

Wenn der Text in einer Kopf- oder Fußzeile mehr als eine Zeile umfasst, erstellen Sie einen Schlüssel und einen Wert für jede Zeile. Angenommen, folgende Fußzeile mit zwei Zeilen ist vorhanden:

**The file is classified as Confidential**

**Label applied manually**

Um diese mehrzeilige Fußzeile zu entfernen, erstellen Sie die folgenden zwei Einträge für die gleiche Bezeichnungs Richtlinie:

- Key: **ExternalContentMarkingToRemove**

- Schlüsselwert 1: **\*Vertraulich***

- Schlüsselwert 2: **\*Label applied*** (Bezeichnung angewendet) 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*Confidential*,*Label applied*"}


#### <a name="optimization-for-powerpoint"></a>Optimierung für PowerPoint

In PowerPoint werden Fußzeilen als Formen implementiert. Wenn Sie vermeiden möchten, dass Formen entfernt werden, die den angegeben Text enthalten, jedoch keine Kopf- oder Fußzeilen sind, verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **PowerPointShapeNameToRemove**. Es wird empfohlen, diese Einstellung ebenfalls zu verwenden, um zu verhindern, dass der Text in allen Formen überprüft wird, denn dieser Prozess ist sehr ressourcenintensiv.

Wenn Sie diese zusätzliche erweiterte Clienteinstellung nicht angeben und PowerPoint im Schlüsselwert **RemoveExternalContentMarkingInApp** eingeschlossen ist, werden alle Formen auf den Text überprüft, den Sie im Wert **ExternalContentMarkingToRemove** angeben. 

So finden Sie den Namen der Form, die Sie als Kopf- oder Fußzeile verwenden:

1. Zeigen Sie in PowerPoint den Bereich **Auswahl** an: Registerkarte **Format** > **Arrange** group (Gruppe anordnen) > **Auswahlbereich**.

2. Wählen Sie die Form auf der Folie aus, die die Kopf- oder Fußzeile enthält. Der Name der ausgewählten Form wird nun im Bereich **Auswahl** hervorgehoben.

Verwenden Sie den Namen der Form, um einen Zeichenfolgenwert für den Schlüssel **PowerPointShapeNameToRemove** anzugeben. 

Beispiel: Der Name der Form ist **fc**. Geben Sie den Wert `fc` an, um die Form mit diesem Namen zu entfernen.

- Key: **PowerPointShapeNameToRemove**

- Wert: \<**Name der PowerPoint-Form**> 

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{PowerPointShapeNameToRemove="fc"}

Wenn Sie mehr als eine PowerPoint-Form entfernen möchten, geben Sie so viele Werte an, wie die zu entfernenden Formen vorhanden sind.

Standardmäßig werden nur die Masterfolien auf Kopf- oder Fußzeilen überprüft. Wenn Sie diese Suche auf alle Folien ausweiten möchten (dieser Prozess ist jedoch wesentlich ressourcenintensiver), verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **RemoveExternalContentMarkingInAllSlides**:

- Key: **RemoveExternalContentMarkingInAllSlides**

- Wert: **True**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RemoveExternalContentMarkingInAllSlides="True"}


## <a name="disable-custom-permissions-in-file-explorer"></a>Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Standardmäßig wird Benutzern eine Option mit dem Namen **schützen mit benutzerdefinierten Berechtigungen** angezeigt, wenn Sie mit der rechten Maustaste in den Datei-Explorer klicken und **klassifizieren und schützen**auswählen. Mit dieser Option können Sie Ihre eigenen Schutzeinstellungen festlegen, mit denen alle Schutzeinstellungen außer Kraft gesetzt werden können, die Sie möglicherweise in einer Bezeichnungs Konfiguration enthalten haben. Benutzer können außerdem eine Option zum Entfernen des Schutzes sehen. Wenn Sie diese Einstellung konfigurieren, werden den Benutzern diese Optionen nicht angezeigt.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **EnableCustomPermissions**

- Wert: **False**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}

## <a name="for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer"></a>Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die erweiterte Client Einstellung so konfigurieren, dass Benutzer [definierte Berechtigungen im Datei-Explorer deaktiviert](#disable-custom-permissions-in-file-explorer)werden, können Benutzer benutzerdefinierte Berechtigungen, die bereits in einem geschützten Dokument festgelegt sind, nicht anzeigen oder ändern.

Es gibt jedoch eine andere erweiterte Client Einstellung, die Sie angeben können, damit Benutzer benutzerdefinierte Berechtigungen für ein geschütztes Dokument sehen und ändern können, wenn Sie den Datei-Explorer verwenden und mit der rechten Maustaste auf die Datei klicken.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **EnableCustomPermissionsForCustomProtectedFiles**

- Wert: **True**

PowerShell-Beispiel Befehl:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissionsForCustomProtectedFiles="True"}


## <a name="for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments"></a>Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht

Diese Konfiguration verwendet [Erweiterte Richtlinien Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Diese Einstellung gilt für den Fall, dass Benutzer eine Bezeichnung Dokumente an eine e-Mail anfügen und die e-Mail-Nachricht nicht selbst bezeichnen. In diesem Szenario wird automatisch eine Bezeichnung für Sie ausgewählt, basierend auf den Klassifizierungs Bezeichnungen, die auf die Anlagen angewendet werden. Die höchste Klassifizierungs Bezeichnung ist ausgewählt.

Die Anlage muss eine physische Datei sein, es darf sich nicht um einen Link zu einer Datei handeln (beispielsweise um einen Link zu einer Datei in SharePoint oder OneDrive for Business).

Sie können diese Einstellung auf " **empfohlen**" festlegen, damit Benutzer mit einer anpassbaren QuickInfo aufgefordert werden, die ausgewählte Bezeichnung auf Ihre e-Mail-Nachricht anzuwenden. Benutzer können die Empfehlung akzeptieren oder ablehnen. Oder Sie können diese Einstellung auf " **automatisch**" festlegen, wobei die ausgewählte Bezeichnung automatisch angewendet wird, Benutzer aber die Bezeichnung entfernen oder eine andere Bezeichnung auswählen können, bevor Sie die e-Mail senden.

Hinweis: Wenn die Anlage mit der höchsten Klassifizierungs Bezeichnung für den Schutz mit der Einstellung benutzerdefinierter Berechtigungen konfiguriert ist:

- Wenn die benutzerdefinierten Berechtigungen der Bezeichnung Outlook (nicht weiterleiten) einschließen, wird diese Bezeichnung ausgewählt und der Schutz nicht weiterleiten auf die e-Mail angewendet.
- Wenn die benutzerdefinierten Berechtigungen der Bezeichnung nur für Word, Excel, PowerPoint und den Datei-Explorer gelten, wird diese Bezeichnung nicht auf die e-Mail-Nachricht angewendet, und keines ist der Schutz.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Schlüssel 1: **Attachmentaction**

- Schlüsselwert 1: **Empfohlen** oder **automatisch**

- Schlüssel 2: **AttachmentActionTip**

- Schlüsselwert 2: "\<angepasste QuickInfo->"

Die angepasste QuickInfo unterstützt nur eine einzige Sprache.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{AttachmentAction="Automatic"}

## <a name="add-report-an-issue-for-users"></a>Add "Report an Issue" for users ("Problem melden" für Benutzer hinzufügen)

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die folgende erweiterte Clienteinstellung angeben, wird Benutzern die Option **Problem melden** angezeigt, die sie aus dem Clientdialogfeld **Hilfe und Feedback** auswählen können. Geben Sie eine HTTP-Zeichenfolge für den Link an. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **ReportAnIssueLink**

- Wert: **\<HTTP-Zeichenfolge>**

Beispielwert für eine Website: `https://support.contoso.com`

Beispielwert für eine E-Mail-Adresse: `mailto:helpdesk@contoso.com`

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ReportAnIssueLink="mailto:helpdesk@contoso.com"}

## <a name="implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent"></a>Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben

Diese Konfiguration verwendet [Erweiterte Richtlinien Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie die folgenden erweiterten Clienteinstellungen erstellen und konfigurieren, werden Benutzern Popupmeldungen in Outlook angezeigt, die sie vor dem Senden einer E-Mail warnen können, oder sie nach einer Legitimierung fragen, warum sie eine E-Mail versenden, oder sie aus folgenden Gründen davon abhalten, eine E-Mail zu senden:

- **Die E-Mail oder der E-Mail-Anhang hat eine bestimmte Bezeichnung:**
    - Der Anhang kann einen beliebigen Dateityp haben

- **Die E-Mail oder der E-Mail-Anhang hat keine bestimmte Bezeichnung:**
    - Der Anhang kann ein Office-Dokument oder ein PDF-Dokument sein

Wenn diese Bedingungen erfüllt sind, wird dem Benutzer eine Popup Meldung mit einer der folgenden Aktionen angezeigt:

- **Warnung:** Der Benutzer kann bestätigen und senden, oder abbrechen.

- **Justify** (Legitimation): Der Benutzer wird zu einer Legitimierung aufgefordert (mit vordefinierten Optionen oder Freiform).  Der Benutzer kann dann die E-Mail senden oder abbrechen. Der Legitimationstext wird in den X-Header der E-Mail geschrieben, sodass dieser von anderen Systemen gelesen werden kann. Zum Beispiel von Diensten, die der Verhinderung von Datenverlust dienen.

- **Blockieren**: Der Benutzer wird davon abgehalten, die E-Mail zu senden, solange die Bedingung besteht. Die Nachricht beinhaltet den Grund dafür, warum die E-Mail blockiert wird, sodass der Benutzer das Problem aufheben kann. So kann er z.B. bestimmte Empfänger entfernen, oder der E-Mail eine Bezeichnung hinzufügen. 

Wenn sich die Popup Meldungen für eine bestimmte Bezeichnung befinden, können Sie Ausnahmen für Empfänger nach Domänen Name konfigurieren.

> [!TIP]
> Obwohl das Lernprogramm für den Azure Information Protection-Client anstelle des Unified-Bezeichnungs Clients vorgesehen ist, können Sie diese erweiterten Einstellungen in Aktion [für sich selbst mit Tutorial anzeigen: Konfigurieren Sie Azure Information Protection, um das Überschreiben von Informationen](../infoprotect-oversharing-tutorial.md)mithilfe von Outlook zu steuern.

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren für bestimme Bezeichnungen implementiert:

Erstellen Sie für die ausgewählte Richtlinie mindestens eine der folgenden erweiterten Einstellungen mit den folgenden Schlüsseln. Geben Sie für die Werte eine oder mehrere Bezeichnungen durch die GUIDs an, die jeweils durch ein Komma getrennt sind.

Beispiel Wert für mehrere Bezeichnungs-GUIDs als durch Trennzeichen getrennte Zeichenfolge:`dcf781ba-727f-4860-b3c1-73479e31912b,1ace2cc3-14bc-4142-9125-bf946a70542c,3e9df74d-3168-48af-8b11-037e3021813f`


- Warnmeldungen:
    
    - Key: **OutlookWarnUntrustedCollaborationLabel**
    
    - Wert: \< **Bezeichnungs-GUIDs, durch Trennzeichen getrennt**>

- Legitimationsmeldungen:
    
    - Key: **OutlookJustifyUntrustedCollaborationLabel**
    
    - Wert: \< **Bezeichnungs-GUIDs, durch Trennzeichen getrennt**>

- Blockiermeldungen:
    
    - Key: **OutlookBlockUntrustedCollaborationLabel**
    
    - Wert: \< **Bezeichnungs-GUIDs, durch Trennzeichen getrennt**>


PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookWarnUntrustedCollaborationLabel="8faca7b8-8d20-48a3-8ea2-0f96310a848e,b6d21387-5d34-4dc8-90ae-049453cec5cf,bb48a6cb-44a8-49c3-9102-2d2b017dcead,74591a94-1e0e-4b5d-b947-62b70fc0f53a,6c375a97-2b9b-4ccd-9c5b-e24e4fd67f73"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyUntrustedCollaborationLabel="dc284177-b2ac-4c96-8d78-e3e1e960318f,d8bb73c3-399d-41c2-a08a-6f0642766e31,750e87d4-0e91-4367-be44-c9c24c9103b4,32133e19-ccbd-4ff1-9254-3a6464bf89fd,74348570-5f32-4df9-8a6b-e6259b74085b,3e8d34df-e004-45b5-ae3d-efdc4731df24"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockUntrustedCollaborationLabel="0eb351a6-0c2d-4c1d-a5f6-caa80c9bdeec,40e82af6-5dad-45ea-9c6a-6fe6d4f1626b"}

#### <a name="to-exempt-domain-names-for-pop-up-messages-configured-for-specific-labels"></a>So nehmen Sie Domänen Namen für Popup Nachrichten aus, die für bestimmte Bezeichnungen konfiguriert sind

Für die Bezeichnungen, die Sie mit diesen Popup Nachrichten angegeben haben, können Sie bestimmte Domänen Namen ausnehmen, damit Benutzer die Nachrichten für Empfänger, die diesen Domänen Namen enthalten, nicht in Ihrer e-Mail-Adresse sehen. In diesem Fall werden die E-Mails problemlos gesendet. Wenn Sie mehrere Domänen angeben möchten, fügen Sie sie kommagetrennt als einzelne Zeichenfolge hinzu.

Eine übliche Konfiguration ist es, die Popupmeldungen nur für die Empfänger anzuzeigen, die nicht zu Ihrer Organisation gehören, oder die keine für Ihre Organisation autorisierte Partner sind. In diesem Fall geben Sie alle E-Mail-Domänen an, die von Ihrer Organisation und von Ihren Partnern verwendet werden.

Erstellen Sie für dieselbe Bezeichnungs Richtlinie die folgenden erweiterten Client Einstellungen, und geben Sie für den Wert eine oder mehrere Domänen an, die jeweils durch ein Komma getrennt sind.

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

Sie haben beispielsweise die Einstellung für den erweiterten Client " **outlookblockuntreudkollaborationlabel** " für die Bezeichnung " **vertraulich\alle Mitarbeiter** " angegeben. Nun geben Sie die zusätzliche erweiterte Client Einstellung " **outlookjustifytreuddomains** " und " **contoso.com**" an. Dies hat zur Folge, dass ein Benutzer eine e-Mail an john@sales.contoso.com senden kann, wenn er **vertraulich \ alle Mitarbeiter** heißt, aber das Senden einer e-Mail mit derselben Bezeichnung an ein Gmail-Konto blockiert wird.

PowerShell-Beispiel Befehle, deren Bezeichnung "Global" lautet:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockTrustedDomains="gmail.com"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyTrustedDomains="contoso.com,fabrikam.com,litware.com"}

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-emails-or-attachments-that-dont-have-a-label"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren von E-Mails oder Anhängen implementiert, die keine Bezeichnung haben:

Erstellen Sie für dieselbe Bezeichnungs Richtlinie die folgende erweiterte Client Einstellung mit einem der folgenden Werte:

- Warnmeldungen:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Warnung**

- Legitimationsmeldungen:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Justify** (Legitimation)

- Blockiermeldungen:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Blockieren**

- Diese Meldungen deaktivieren:
    
    - Key: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Deaktiviert**


PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationAction="Warn"}


#### <a name="to-define-specific-file-name-extensions-for-the-warn-justify-or-block-pop-up-messages-for-email-attachments-that-dont-have-a-label"></a>So definieren Sie für e-Mail-Anhänge, die keine Bezeichnung aufweisen, bestimmte Dateinamen Erweiterungen für die Warn-, rechtfertigen oder Blockierungs-Popup Meldungen

Standardmäßig gelten die Popup Nachrichten warnen, rechtfertigen oder blockieren für alle Office-Dokumente und PDF-Dokumente. Sie können diese Liste verfeinern, indem Sie angeben, welche Dateinamen Erweiterungen die Warn-, Recht-oder Sperr Nachrichten mit einer zusätzlichen erweiterten Einstellung und eine durch Trennzeichen getrennte Liste von Dateinamen Erweiterungen anzeigen sollen.

Beispiel Wert für mehrere Dateinamen Erweiterungen, die als durch Trennzeichen getrennte Zeichenfolge definiert werden sollen:`.XLSX,.XLSM,.XLS,.XLTX,.XLTM,.DOCX,.DOCM,.DOC,.DOCX,.DOCM,.PPTX,.PPTM,.PPT,.PPTX,.PPTM`

In diesem Beispiel führt ein PDF-Dokument ohne Bezeichnung nicht zu Warn-, rechtfertigen oder Blockierungs Nachrichten.

Geben Sie für dieselbe Bezeichnungs Richtlinie die folgenden Zeichen folgen ein: 


- Key: **OutlookOverrideUnlabeledCollaborationExtensions**

- Wert: **\<** Dateinamen Erweiterungen zum Anzeigen von Nachrichten, durch Kommas getrennt **>**


PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookOverrideUnlabeledCollaborationExtensions=".PPTX,.PPTM,.PPT,.PPTX,.PPTM"}

#### <a name="to-specify-a-different-action-for-email-messages-without-attachments"></a>So geben Sie eine andere Aktion für e-Mail ohne Anlagen an

Standardmäßig gilt: der Wert, den Sie für outlookunlabeledcollaborationaction angeben, um Popup Nachrichten zu warnen, zu begründen oder zu blockieren, gilt für e-Mails oder Anhänge, die keine Bezeichnung aufweisen. Sie können diese Konfiguration verfeinern, indem Sie eine andere erweiterte Einstellung für e-Mail-Nachrichten mit Anlagen angeben.

Erstellen Sie die folgende erweiterte Clienteinstellung mit einem der folgenden Werte:

- Warnmeldungen:
    
    - Key: **Outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **Warnung**

- Legitimationsmeldungen:
    
    - Key: **Outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **Justify** (Legitimation)

- Blockiermeldungen:
    
    - Key: **Outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **Blockieren**

- Diese Meldungen deaktivieren:
    
    - Key: **Outlookunlabeledcollaborationaktionoverridemailbodybehavior**
    
    - Wert: **Deaktiviert**

Wenn Sie diese Client Einstellung nicht angeben, wird der Wert, den Sie für "outlookunlabeledcollaborationaction" angeben, für nicht beschriftete e-Mail-Nachrichten ohne Anhänge und nicht bezeichnete e-Mail-Nachrichten mit Anlagen verwendet.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationActionOverrideMailBodyBehavior="Warn"}

## <a name="disable-sending-audit-data-to-azure-information-protection-analytics"></a>Deaktivieren des Sendens von Überwachungsdaten an Azure Information Protection Analytics

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Der Azure Information Protection Unified Bezeichnung-Client unterstützt die Zentrale Berichterstellung und sendet seine Überwachungsdaten standardmäßig an [Azure Information Protection Analytics](../reports-aip.md). Weitere Informationen zu den gesendeten und gespeicherten Informationen finden Sie im Abschnitt [Informationen zu den gesammelten und an Microsoft gesendeten](../reports-aip.md#information-collected-and-sent-to-microsoft) Informationen aus der Dokumentation zu Central Reporting.

Um dieses Verhalten so zu ändern, dass diese Informationen nicht vom Unified Label-Client gesendet werden, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **EnableAudit**

- Wert: **False**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableAudit="False"}


## <a name="disable-sending-discovered-sensitive-information-in-documents-to-azure-information-protection-analytics"></a>Hiermit wird das Senden von ermittelten sensiblen Informationen in Dokumenten an Azure Information Protection Analytics deaktiviert.

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn der Azure Information Protection Unified Bezeichnung-Client in Office-Apps verwendet wird, sucht er nach vertraulichen Informationen in Dokumenten, wenn diese zum ersten Mal gespeichert werden. Das Bereitstellen der Einstellung " [EnableAudit](#disable-sending-audit-data-to-azure-information-protection-analytics) Advanced" ist nicht auf " **false**" festgelegt, und alle gefundenen sensiblen Informationstypen (vordefiniert oder Benutzer definiert) werden dann an Azure Information Protection Analytics gesendet.

Um dieses Verhalten so zu ändern, dass vertrauliche Informationstypen, die vom Unified Label-Client gefunden werden, nicht an Azure Information Protection Analytics gesendet werden, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **Runauditinformationtypesdiscovery**

- Wert: **False**

Wenn Sie diese erweiterte Client Einstellung festlegen, können Überwachungsinformationen weiterhin vom Client gesendet werden. die Informationen sind jedoch auf die Berichterstattung beschränkt, wenn ein Benutzer auf den gekennzeichneten Inhalt zugegriffen hat.

Zum Beispiel:

- Mit dieser Einstellung können Sie sehen, dass ein Benutzer auf "Financial. docx" mit der Bezeichnung " **vertraulich \ Sales**" zugegriffen hat.

- Ohne diese Einstellung können Sie sehen, dass "Financial. docx" 6 Kreditkartennummern enthält.
    
    - Wenn Sie zusätzlich [Inhaltsübereinstimmungen für umfassendere Analysen](../reports-aip.md#content-matches-for-deeper-analysis) aktivieren, sind außerdem die tatsächlichen Kreditkartennummern einsehbar.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RunAuditInformationTypesDiscovery="False"}

## <a name="disable-sending-information-type-matches-for-a-subset-of-users"></a>Deaktivieren der Übereinstimmungen des Sendeinformationstyps für eine Teilmenge von Benutzern

Diese Konfiguration verwendet eine [Erweiterte Richtlinien Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) , die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie das Kontrollkästchen für [Azure Information Protection Analytics](../reports-aip.md) aktivieren, das eine tiefere Analyse Ihrer sensiblen Daten ermöglicht, sammelt die Inhalts Übereinstimmungen für Ihre sensiblen Informationstypen oder Ihre benutzerdefinierten Bedingungen standardmäßig die folgenden Informationen: wird von allen Benutzern gesendet, einschließlich Dienst Konten, die den Azure Information Protection Scanner ausführen. Wenn Sie einige Benutzer haben, die diese Daten nicht senden dürfen, erstellen Sie die folgende erweiterte Client Einstellung in einer Bezeichnungs Richtlinie für diese Benutzer: 

- Key: **LogMatchedContent**

- Wert: **False**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{LogMatchedContent="Disable"}

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Diese Konfiguration ist nicht kompatibel mit geschützten PDF-Dateien mit der Dateinamenerweiterung ppdf. Diese Dateien können nicht vom Client mit dem Datei-Explorer oder PowerShell geöffnet werden.

Bei Office-Dokumenten, die von Secure Islands bezeichnet werden, können Sie diese Dokumente mit einer Vertraulichkeits Bezeichnung versehen, indem Sie eine von Ihnen definierte Zuordnung verwenden. Mit dieser Methode können Sie auch Bezeichnungen aus anderen Lösungen wiederverwenden, wenn diese Bezeichnungen sich in Office-Dokumenten befinden. 

Als Ergebnis dieser Konfigurationsoption wird die neue Vertraulichkeits Bezeichnung vom Azure Information Protection Unified Label-Client wie folgt angewendet:

- Bei Office-Dokumenten: Wenn das Dokument in der Desktop-App geöffnet wird, wird die neue Vertraulichkeits Bezeichnung als festgelegt angezeigt und beim Speichern des Dokuments angewendet.

- In PowerShell: " [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel) " und " [Set-aipfileclassificiations](/powershell/module/azureinformationprotection/set-aipfileclassification) " können die neue Vertraulichkeits Bezeichnung anwenden.

- Im Datei-Explorer: Im Dialogfeld Azure Information Protection wird die neue Vertraulichkeits Bezeichnung angezeigt, aber nicht festgelegt.

Diese Konfiguration erfordert, dass Sie für jede Vertraulichkeits Bezeichnung, die Sie der alten Bezeichnung zuordnen möchten, eine erweiterte Einstellung mit dem Namen " **labelbycustomproperties** " angeben. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Geben Sie einen Namen für die Migrationsregel an. Verwenden Sie einen beschreibenden Namen, mit dem Sie identifizieren können, wie eine oder mehrere Bezeichnungen aus Ihrer vorherigen Bezeichnungs Lösung der Vertraulichkeits Bezeichnung zugeordnet werden sollen.

Beachten Sie, dass durch diese Einstellung keine ursprüngliche Bezeichnung aus dem Dokument bzw. keine optische Kennzeichnung im Dokument entfernt wird, die von der ursprünglichen Bezeichnung möglicherweise angewendet wurde. Informationen zum Entfernen von Kopf-und Fußzeilen finden Sie im vorherigen Abschnitt [Entfernen von Kopf-und Fußzeilen aus anderen Beschriftungslösungen](#remove-headers-and-footers-from-other-labeling-solutions).

#### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Beispiel 1: 1:1-Zuordnung des gleichen Bezeichnungsnamens

Anforderung: Dokumente mit der Secure Islands-Bezeichnung „Confidential“ sollten in Azure Information Protection die Bezeichnung „Vertraulich“ erhalten.

Für dieses Beispiel gilt Folgendes:

- Die Secure Islands-Bezeichnung lautet **Vertraulich** und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Die erweiterte Einstellung:

- Key: **labelbycustomproperties**

- Wert: **Die Bezeichnung "sichere Inseln" ist vertraulich, Klassifizierung, vertraulich.**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "vertraulich" heißt:

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Confidential,Classification,Confidential"}

#### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Beispiel 2: 1:1-Zuordnung für einen anderen Bezeichnungsnamen

Anforderung: Dokumente mit der Secure Islands-Bezeichnung „Sensitive“ sollten in Azure Information Protection die Bezeichnung „Streng vertraulich“ erhalten.

Für dieses Beispiel gilt Folgendes:

- Die Secure Islands-Bezeichnung lautet **Sensitive** (Sensibel) und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Die erweiterte Einstellung:

- Key: **labelbycustomproperties**

- Wert: **Die Bezeichnung "sichere Inseln" ist sensibel, Klassifizierung, vertraulich.**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "streng vertraulich" lautet:

    Set-Label -Identity "Highly Confidential" -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Sensitive,Classification,Sensitive"}

#### <a name="example-3-many-to-one-mapping-of-label-names"></a>Beispiel 3: n:1-Zuordnung von Bezeichnungsnamen

Anforderung: Sie verfügen über zwei sichere Inseln-Bezeichnungen, die das Wort "Internal" enthalten, und Sie möchten, dass Dokumente, die eine dieser sicheren Inseln bezeichnen, vom Azure Information Protection Unified Label-Client als "Allgemein" neu berechnet werden.

Für dieses Beispiel gilt Folgendes:

- Die Secure Islands-Bezeichnungen enthalten den Begriff **Internal** (intern) und sind in der benutzerdefinierten Eigenschaft namens **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

- Key: **labelbycustomproperties**

- Wert: **Die Bezeichnung "Secure Islands" enthält interne, Klassifizierungen. \*Intern.\***

Beispiel für einen PowerShell-Befehl, bei dem Ihre Bezeichnung "Allgemein" lautet:

    Set-Label -Identity General -AdvancedSettings @{labelByCustomProperties="Secure Islands label contains Internal,Classification,.*Internal.*"}

#### <a name="example-4-multiple-rules-for-the-same-label"></a>Beispiel 4: Mehrere Regeln für dieselbe Bezeichnung

Wenn Sie mehrere Regeln für dieselbe Bezeichnung benötigen, definieren Sie mehrere Zeichen folgen Werte für denselben Schlüssel. 

In diesem Beispiel werden die Secure Islands-Bezeichnungen mit dem Namen "Confidential" und "Secret" in der benutzerdefinierten Eigenschaft " **Classification**" gespeichert, und Sie möchten, dass der Azure Information Protection Unified Label-Client die Vertraulichkeits Bezeichnung " Vertraulich ":

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}

### <a name="extend-your-label-migration-rules-to-emails"></a>Erweitern Sie Ihre Regeln für die Bezeichnung der Migration auf e-Mails.

Sie können die erweiterten Einstellungen von labelbycustomproperties mit Outlook-e-Mails zusätzlich zu Office-Dokumenten verwenden, indem Sie eine zusätzliche Einstellung für die erweiterte Bezeichnungs Richtlinie angeben. Diese Einstellung hat jedoch eine bekannte negative Auswirkung auf die Leistung von Outlook. Konfigurieren Sie diese zusätzliche Einstellung daher nur, wenn Sie eine starke geschäftliche Anforderung dafür haben, und denken Sie daran, Sie auf einen NULL-Zeichen folgen Wert festzulegen, wenn Sie die Migration von der andere Bezeichnungs Lösung.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnungs Richtlinie ein:

- Key: **EnableLabelByMailHeader**

- Wert: **True**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnungs Richtlinie den Namen "Global" hat:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableLabelByMailHeader="True"}

## <a name="apply-a-custom-property-when-a-label-is-applied"></a>Anwenden einer benutzerdefinierten Eigenschaft, wenn eine Bezeichnung angewendet wird

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Es gibt möglicherweise einige Szenarios, in denen Sie zusätzlich zu den Metadaten, die durch eine Vertraulichkeits Bezeichnung angewendet werden, eine oder mehrere benutzerdefinierte Eigenschaften auf ein Dokument oder eine e-Mail-Nachricht anwenden möchten.

Beispiel:

- Sie sind gerade dabei, [von einer anderen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)Bezeichnungs Lösung zu migrieren, z. b. sichere Inseln. Für die Interoperabilität während der Migration sollten Vertraulichkeits Bezeichnungen auch eine benutzerdefinierte Eigenschaft anwenden, die von der anderen Bezeichnungs Lösung verwendet wird.

- Für Ihr Content Management-System (z. b. SharePoint oder eine Dokument Verwaltungs Lösung von einem anderen Anbieter) möchten Sie einen konsistenten benutzerdefinierten Eigenschaftsnamen mit unterschiedlichen Werten für die Bezeichnungen und mit benutzerfreundlichen Namen anstelle der GUID für die Bezeichnung verwenden.

Für Office-Dokumente und Outlook-e-Mails, die Benutzer mit dem Azure Information Protection Unified Label-Client bezeichnen, können Sie eine oder mehrere benutzerdefinierte Eigenschaften hinzufügen, die Sie definieren. Sie können diese Methode auch verwenden, damit der Unified Label-Client eine benutzerdefinierte Eigenschaft als Bezeichnung aus anderen Projektmappen für Inhalte anzeigt, die noch nicht vom Unified Label-Client bezeichnet werden.

Als Ergebnis dieser Konfigurationsoption werden alle weiteren benutzerdefinierten Eigenschaften vom Azure Information Protection Unified-Bezeichnungs Client wie folgt angewendet:

- Bei Office-Dokumenten: Wenn das Dokument in der Desktop-App bezeichnet wird, werden beim Speichern des Dokuments die zusätzlichen benutzerdefinierten Eigenschaften angewendet.

- Für Outlook-e-Mails: Wenn die e-Mail-Nachricht in Outlook bezeichnet wird, werden die zusätzlichen Eigenschaften beim Senden der e-Mail auf den x-Header angewendet.

- In PowerShell: " [Set-aipfilelabel](/powershell/module/azureinformationprotection/set-aipfilelabel) " und " [Set-aipfileclassificiations](/powershell/module/azureinformationprotection/set-aipfileclassification) " wendet die zusätzlichen benutzerdefinierten Eigenschaften an, wenn das Dokument beschriftet und gespeichert wird. [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) zeigt benutzerdefinierte Eigenschaften als zugeordnete Bezeichnung an, wenn eine Vertraulichkeits Bezeichnung nicht angewendet wird.

- Im Datei-Explorer: Wenn der Benutzer mit der rechten Maustaste auf die Datei klickt und die Bezeichnung anwendet, werden die benutzerdefinierten Eigenschaften angewendet.

Diese Konfiguration erfordert, dass Sie für jede Vertraulichkeits Bezeichnung, die die zusätzlichen benutzerdefinierten Eigenschaften anwenden soll, eine erweiterte Einstellung mit dem Namen " **custompropertiesbylabel** " angeben. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[custom property name],[custom property value]`

#### <a name="example-1-add-a-single-custom-property-for-a-label"></a>Beispiel 1: Fügen Sie eine einzelne benutzerdefinierte Eigenschaft für eine Bezeichnung hinzu.

Anforderung: Dokumente, die vom Azure Information Protection Unified Label-Client als "vertraulich" bezeichnet werden, sollten über die zusätzliche benutzerdefinierte Eigenschaft "Klassifizierung" mit dem Wert "Secret" verfügen.

Für dieses Beispiel gilt Folgendes:

- Die Vertraulichkeits Bezeichnung heißt **vertraulich** und erstellt eine benutzerdefinierte Eigenschaft mit dem Namen **Classification** mit dem Wert **Secret**.

Die erweiterte Einstellung:

- Schlüssel: **custompropertiesbylabel**

- Wert: **Klassifizierung, Geheimnis**

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "vertraulich" heißt:

    Set-Label -Identity Confidential -AdvancedSettings @{customPropertiesByLabel="Classification,Secret"}

#### <a name="example-2-add-multiple-custom-properties-for-a-label"></a>Beispiel 2: Mehrere benutzerdefinierte Eigenschaften für eine Bezeichnung hinzufügen

Wenn Sie mehr als eine benutzerdefinierte Eigenschaft für dieselbe Bezeichnung hinzufügen möchten, müssen Sie mehrere Zeichen folgen Werte für denselben Schlüssel definieren.

PowerShell-Beispiel Befehl, bei dem Ihre Bezeichnung "Allgemein" heißt, und Sie möchten eine benutzerdefinierte Eigenschaft mit dem Namen " **Klassifizierung** " mit dem Wert " **Allgemein** " und eine zweite benutzerdefinierte Eigenschaft mit dem Namen " **Sensitivität** " mit dem Wert " **internal** :

    Set-Label -Identity General -AdvancedSettings @{customPropertiesByLabel=ConvertTo-Json("Classification,General", "Sensitivity,Internal")}

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden

Diese Konfiguration verwendet [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Verwenden Sie diese Einstellungen nur, wenn Sie über eine funktionierende [S/MIME-Bereitstellung](https://docs.microsoft.com/office365/SecurityCompliance/s-mime-for-message-signing-and-encryption) verfügen und möchten, dass eine Bezeichnung diese Schutzmethode automatisch für e-Mails anwendet, anstatt Rights Management Schutz vor Azure Information Protection. Der resultierende Schutz ist derselbe wie bei der manuellen Auswahl von S/MIME-Optionen in Outlook.

Um eine erweiterte Einstellung für eine digitale S/MIME-Signatur zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnung ein:

- Key: **SMimeSign**

- Wert: **True**

Um eine erweiterte Einstellung für die S/MIME-Verschlüsselung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnung ein:

- Key: **SMimeEncrypt**

- Wert: **True**

Wenn die von Ihnen angegebene Bezeichnung für die Verschlüsselung konfiguriert ist, ersetzt der S/MIME-Schutz für den Azure Information Protection Unified Label-Client den Rights Management Schutz nur in Outlook. Die allgemein verfügbare Version des Unified Label-Clients verwendet weiterhin die für die Bezeichnung im Admin Center angegebenen Verschlüsselungseinstellungen. Bei Office-Apps mit integrierter Bezeichnung wenden diese nicht den S/MIME-Schutz an, sondern wenden den Schutz von "nicht weiterleiten" an.

Wenn die Bezeichnung nur in Outlook sichtbar sein soll, konfigurieren Sie die Bezeichnung so, dass die Verschlüsselung **nur auf e-Mail-Nachrichten in Outlook**angewendet wird.

PowerShell-Beispiel Befehle, bei denen ihre Bezeichnung "nur Empfänger" heißt:

    Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeSign="True"}

    Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeEncrypt="True"}

## <a name="specify-a-default-sublabel-for-a-parent-label"></a>Festlegen einer Standard untergeordneten Bezeichnung für eine übergeordnete Bezeichnung

Diese Konfiguration verwendet eine [Erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Wenn Sie einer Bezeichnung eine untergeordnete Bezeichnung hinzufügen, können Benutzer die übergeordnete Bezeichnung nicht mehr auf ein Dokument oder eine e-Mail anwenden. Standardmäßig wählen Benutzer die übergeordnete Bezeichnung aus, um die anzuwendenden untergeordneten Bezeichnungen anzuzeigen, und wählen dann eine dieser untergeordneten Bezeichnungen aus. Wenn Sie diese erweiterte Einstellung konfigurieren und Benutzer die übergeordnete Bezeichnung auswählen, wird automatisch eine untergeordnete Bezeichnung ausgewählt und darauf angewendet: 

- Key: **DefaultSubLabelId**

- Wert: \<GUID für untergeordnete Bezeichnung >

Beispiel für einen PowerShell-Befehl, bei dem die übergeordnete Bezeichnung "Confidential" heißt und die untergeordnete Bezeichnung "All Employees" eine GUID von 8faka7b8-8d20-48a3-8ea2-0F 96310a848e:

    Set-Label -Identity "Confidential" -AdvancedSettings @{DefaultSubLabelId="8faca7b8-8d20-48a3-8ea2-0f96310a848e"}

## <a name="specify-a-color-for-the-label"></a>Farbe für die Bezeichnung angeben

Diese Konfiguration verwendet [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) für die Bezeichnung, die Sie mithilfe von Office 365 Security & Compliance Center PowerShell konfigurieren müssen.

Verwenden Sie diese erweiterte Einstellung, um eine Farbe für eine Bezeichnung festzulegen. Um die Farbe anzugeben, geben Sie einen Hexadezimal Code für die Komponenten rot, grün und blau (RGB) der Farbe ein. Beispielsweise ist #40e0d0 der RGB-Hexadezimalwert für türkis.

Wenn Sie einen Verweis auf diese Codes benötigen, finden Sie eine hilfreiche Tabelle auf der [ \<Seite Color >](https://developer.mozilla.org/docs/Web/CSS/color_value) aus den MSDN-Webdocs. Sie finden diese Codes auch in vielen Anwendungen, in denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

Um die erweiterte Einstellung für die Farbe einer Bezeichnung zu konfigurieren, geben Sie die folgenden Zeichen folgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **Farbe**

- Wert: \<RGB-Hex-Wert >

Beispiel für einen PowerShell-Befehl, bei dem Ihre Bezeichnung "Public" lautet:

    Set-Label -Identity Public -AdvancedSettings @{color="#40e0d0"}

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als anderer Benutzer anmelden, wenn Sie den Azure Information Protection Unified-Bezeichnungs Client verwenden. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

Mithilfe des Dialogfelds **Microsoft Azure Information Protection** können Sie prüfen, an welchem Konto Sie derzeit angemeldet sind: Öffnen Sie eine Office-Anwendung, und wählen Sie auf der Registerkarte **Start** die Schaltfläche Vertraulichkeit aus, und wählen Sie dann **Hilfe und Feedback**aus. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. Ein Symptom der Verwendung des falschen Kontos ist, dass die Bezeichnungen nicht heruntergeladen werden können oder dass die von Ihnen erwarteten Bezeichnungen oder das erwartete Verhalten nicht angezeigt werden.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und wählen Sie im Abschnitt aktualisierter **Client Status** die Option **Anmelden** aus.

Darüber hinaus gilt:

- Wenn der Azure Information Protection Unified Bezeichnung-Client nach dem Ausführen dieser Schritte weiterhin mit dem alten Konto angemeldet ist, löschen Sie alle Cookies aus Internet Explorer, und wiederholen Sie dann die Schritte 1 und 2.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich bei Windows abmelden und mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Tokendatei gelöscht haben. Der Azure Information Protection Unified Bezeichnung-Client wird dann automatisch mithilfe Ihres aktuell angemeldeten Benutzerkontos authentifiziert.

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- Sie können die Option **Einstellungen zurücksetzen** unter **Hilfe und Feedback** verwenden, um sich anzumelden und die derzeit heruntergeladenen Bezeichnungen und Richtlinien Einstellungen aus dem Office 365-Security & Compliance Center, dem Microsoft 365 Security Center oder dem Microsoft 365 Kompatibilitäts Center.


## <a name="change-the-local-logging-level"></a>Ändern des lokalen Protokolliergrads

Standardmäßig schreibt der Azure Information Protection Unified Bezeichnung-Client Client Protokolldateien in den Ordner **%LocalAppData%\microsoft\msip** . Diese Dateien dienen zur Problembehandlung durch den Microsoft-Support.
 
Um den Protokolliergrad für diese Dateien zu ändern, suchen Sie in der Registrierung nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf den erforderlichen Protokolliergrad fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\LogLevel**

Legen Sie den Protokolliergrad auf einen der folgenden Werte fest:

- **Off**: Keine lokale Protokollierung.

- **Fehler**: Nur Fehler.

- **Info**: Minimale Protokollierung, die keine Ereignis-IDs umfasst.

- **Debug**: Vollständige Informationen.

- **Trace**: Ausführliche Protokollierung (die Standardeinstellung für Clients).

Mit dieser Registrierungs Einstellung werden die Informationen, die an Azure Information Protection für die [zentrale Berichterstattung](../reports-aip.md)gesendet werden, nicht geändert.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client angepasst haben, finden Sie in den folgenden Ressourcen weitere Informationen, die Sie möglicherweise benötigen, um diesen Client zu unterstützen:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
