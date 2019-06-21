---
title: Benutzerdefinierte Konfigurationen – Azure Information Protection unified bezeichnungs-client
description: Informationen zum Anpassen von Azure Information Protection unified bezeichnungs-Client für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: maayan
ms.suite: ems
ms.openlocfilehash: 41b4d44babb9941820c95a7f842f119c444a4b06
ms.sourcegitcommit: 478081129d9ea8382ce08fae0bae1a08cab23893
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/20/2019
ms.locfileid: "67298275"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-unified-labeling-client"></a>Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection unified bezeichnungs-client

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Verwenden Sie die folgende Informationen für erweiterte Konfigurationen, die Sie möglicherweise für spezifische Szenarien oder eine Teilmenge von Benutzern bei der Verwaltung des Azure Information Protection unified bezeichnungs-Clients.

Diese Einstellungen sind erforderlich, dass die Bearbeitung der Registrierung oder das Angeben erweiterter Einstellungen mithilfe von Office 365 Security & Compliance Center und PowerShell.

### <a name="how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell"></a>Vorgehensweise: Konfigurieren Sie erweiterte Einstellungen für den Client mithilfe von Office 365 Security & Compliance Center und PowerShell

Bei Verwendung von [Office 365 Security & Compliance Center und PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/office-365-scc-powershell?view=exchange-ps), können Sie erweiterte Einstellungen, die Unterstützung von Anpassungen für die Bezeichnung Richtlinien und Bezeichnungen konfigurieren. Zum Beispiel:

- Die Einstellung zum Anzeigen der Information Protection-Leiste in Office-apps ist eine ***Bezeichnung der Richtlinie, die erweiterte Einstellung***.
- Die Einstellung aus, um eine bezeichnungsfarbe angeben, wird eine ***Bezeichnung, die erweiterte Einstellung***.

In beiden Fällen geben Sie die *AdvancedSettings* Parameter mit der Identität (Name oder GUID) der Gruppenrichtlinie oder die Beschriftung, und geben Sie Schlüssel-Wert-Paare in einer [Hashtabelle](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_hash_tables), mithilfe der folgenden Syntax:

Für eine Bezeichnung richtlinieneinstellung Einzelwert-als Zeichenfolge:

    Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key="value1,value2"}

Für Bezeichnung Richtlinieneinstellungen mehrere Zeichenfolgenwerte für denselben Schlüssel:

    Set-LabelPolicy -Identity <PolicyName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}

Für eine Bezeichnung-Einstellung, die einzelne String-Wert aus:

    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key="value1,value2"}

Für die bezeichnungseinstellungen mehrere Zeichenfolgenwerte für denselben Schlüssel:

    Set-Label -Identity <LabelGUIDorName> -AdvancedSettings @{Key=ConvertTo-Json("value1", "value2")}

Um eine erweiterte Einstellung zu entfernen, verwenden Sie die gleiche Syntax, aber geben Sie den Wert null-Zeichenfolge.


#### <a name="examples-for-setting-advanced-settings"></a>Beispiele zum Festlegen von erweiterter Einstellungen

Beispiel 1: Eine Bezeichnungsrichtlinie, die erweiterte Einstellungen für einen einzelnen Zeichenfolgenwert festgelegt werden:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}

Beispiel 2: Festlegen einer Bezeichnung, die erweiterte Einstellungen für einen einzelnen Zeichenfolgenwert:

    Set-Label -Identity Internal -AdvancedSettings @{smimesign="true"}

Beispiel 3: Festlegen einer Bezeichnung, die erweiterte Einstellungen für mehrere Zeichenfolgenwerte an:

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}

Beispiel 4: Entfernen Sie eine Bezeichnungsrichtlinie, die erweiterte Einstellung durch Angabe eines Werts von null-Zeichenfolge:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions=""}

#### <a name="specifying-the-identity-for-the-label-policy-or-label"></a>Angeben der Identität für die Bezeichnungsrichtlinie oder einer Bezeichnung

Angeben des Namens des Label-Richtlinie für die PowerShell *Identität* Parameter ist einfach, da Sie nur ein Richtlinienname im Administrationscenter finden Sie unter Sie Ihre Richtlinien für die Bezeichnung verwalten. Allerdings für Bezeichnungen, sehen Sie sowohl eine **Namen** und **Anzeigenamen** in das Admin Center. In einigen Fällen wird der Wert für beide identisch sein, aber sie können unterschiedlich sein:

- **Namen** ist der ursprüngliche Name der Bezeichnung, und es ist für alle Ihre Bezeichnungen eindeutig. Wenn Sie den Namen Ihrer Bezeichnung ändern, nachdem es erstellt wurde, bleibt dieser Wert gleich.

- **Anzeigename des** ist der Name der Bezeichnung, die Benutzern angezeigt, und es muss keine für alle Ihre Bezeichnungen eindeutig sein. Z. B. Benutzer finden Sie in einem **alle Mitarbeiter** sublabel für die **vertraulich** Bezeichnung und einen anderen **alle Mitarbeiter** sublabel für die **streng vertraulich**  Bezeichnung. Diese unterbezeichnungen den gleichen Namen angezeigt, aber sind nicht dieselbe Bezeichnung und verschiedene Einstellungen haben.

Verwenden Sie für die Konfiguration der Bezeichnung Erweiterte Einstellungen, die **Namen** Wert. Z. B. um die Bezeichnung in der folgenden Abbildung zu identifizieren, würden Sie angeben `-Identity "All Company"`:

![Verwenden Sie "Name" statt "Anzeigename" um eine sensible Beschriftung zu identifizieren.](../media/labelname_scc.png)

Wenn Sie die GUID der Bezeichnung angeben möchten, wird dieser Wert nicht im Administrationscenter angezeigt, in dem Sie Ihre Bezeichnungen verwalten. Jedoch können Sie den folgenden Office 365 Security & Compliance Center und PowerShell-Befehl, um diesen Wert zu ermitteln:

    Get-Label | Format-Table -Property DisplayName, Name, Guid


#### <a name="order-of-precedence---how-conflicting-settings-are-resolved"></a>Rangfolge – wie im Konflikt stehende Einstellungen aufgelöst werden.

Verwenden eines der Admin Center, in dem Sie Ihre vertraulichkeitsbezeichnungen verwalten, können Sie die folgenden Richtlinieneinstellungen für die Bezeichnung konfigurieren:

- **Diese Bezeichnung nicht standardmäßig auf Dokumente und e-Mails anwenden**

- **Benutzer müssen eine Begründung zum Entfernen einer Bezeichnung oder eine niedrigere klassifizierungsbezeichnung**

- **Erfordern, dass Benutzer ihre e-Mail-Adresse oder das Dokument eine Bezeichnung zuweisen**

- **Geben Sie Benutzern einen Link zu einer Seite für benutzerdefinierte Hilfe**

Wenn mehr als eine Bezeichnungsrichtlinie für einen Benutzer konfiguriert ist, jeweils unterschiedliche Richtlinieneinstellungen, die letzte richtlinieneinstellung gilt nach der Reihenfolge der Richtlinien in das Administrationscenter. Weitere Informationen finden Sie unter [Richtlinie Priorität (Reihenfolge von Bedeutung) Bezeichnung](https://docs.microsoft.com/Office365/SecurityCompliance/sensitivity-labels#label-policy-priority-order-matters)

Bezeichnung, die erweiterten Einstellungen führen Sie die gleiche Logik für die Rangfolge: Wenn eine Bezeichnung in mehrere Richtlinien für die Bezeichnung ist, und diese Bezeichnung verfügt über Einstellungen erweiterte, wird die letzte erweiterte Einstellung nach der Reihenfolge der Richtlinien in das Administrationscenter angewendet.

Label-Richtlinie, die erweiterten Einstellungen werden in umgekehrter Reihenfolge angewendet: Mit einer Ausnahme werden die erweiterten Einstellungen aus der ersten Richtlinie angewendet, entsprechend der Reihenfolge der Richtlinien in das Administrationscenter. Die Ausnahme ist die erweiterte Einstellung *OutlookDefaultLabel*, wodurch eine andere standardbezeichnung für Outlook. Für diese Bezeichnungsrichtlinie gilt erweiterte Einstellung nur die letzte Einstellung nach der Reihenfolge der Richtlinien in das Administrationscenter.

#### <a name="available-advanced-settings-for-label-policies"></a>Erweiterte Einstellungen für Richtlinien für die Bezeichnung verfügbar

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|AttachmentAction|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments)
|AttachmentActionTip|[Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht](#for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments) 
|EnableCustomPermissions|[Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer](#disable-custom-permissions-in-file-explorer)|
|EnableCustomPermissionsForCustomProtectedFiles|[Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer) |
|EnableLabelByMailHeader|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|labelByCustomProperties|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|LogMatchedContent|[Deaktivieren der Übereinstimmungen des Sendeinformationstyps für eine Teilmenge von Benutzern](#disable-sending-information-type-matches-for-a-subset-of-users)|
|OutlookBlockTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookBlockUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookDefaultLabel|[Festlegen einer anderen Standardbezeichnung für Outlook](#set-a-different-default-label-for-outlook)|
|OutlookJustifyTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookJustifyUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookRecommendationEnabled|[Die empfohlene Klassifizierung in Outlook aktivieren](#enable-recommended-classification-in-outlook)|
|OutlookOverrideUnlabeledCollaborationExtensions|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookWarnUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|PostponeMandatoryBeforeSave|[Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|RemoveExternalContentMarkingInApp|[Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Add "Report an Issue" for users](#add-report-an-issue-for-users) ("Problem melden" für Benutzer hinzufügen)|
|RunAuditInformationTypeDiscovery|[Aktivieren von Azure Information Protection-Analysen zur Erkennung vertraulicher Informationen in Dokumenten](#enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents)|

Beispiel-PowerShell-Befehl zum Überprüfen Ihrer Bezeichnung-Richtlinieneinstellungen für eine Bezeichnungsrichtlinie mit dem Namen "Global" aus:

    (Get-LabelPolicy -Identity Global).settings

#### <a name="available-advanced-settings-for-labels"></a>Verfügbaren erweiterten Einstellungen für Bezeichnungen

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|Farbe|[Geben Sie eine Farbe für die Bezeichnung](#specify-a-color-for-the-label)|
|customPropertyByLabel|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|DefaultSubLabelId|[Geben Sie eine standardmäßige untergeordnete Bezeichnung für eine übergeordnete Bezeichnung](#specify-a-default-sublabel-for-a-parent-label) 
|labelByCustomProperties|[Wenden Sie eine benutzerdefinierte Eigenschaft an, wenn eine Bezeichnung angewendet wird](#apply-a-custom-property-when-a-label-is-applied)|
|SMimeEncrypt|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|
|SMimeSign|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|

Beispiel-PowerShell-Befehl überprüfen Sie Ihre Einstellungen für eine Bezeichnung mit dem Namen "Public" aus:

    (Get-Label -Identity Public).settings

## <a name="display-the-information-protection-bar-in-office-apps"></a>Information Protection-Leiste in Office-Apps anzeigen

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Standardmäßig müssen Benutzer auswählen den **Leiste anzeigen** option die **Vertraulichkeit** Schaltfläche, um die Information Protection-Leiste in Office-apps angezeigt wird. Verwenden der **HideBarByDefault** gedrückt, und legen Sie den Wert **"false"** automatisch diese Leiste für Benutzer angezeigt wird, damit sie Bezeichnungen in der Leiste oder die Schaltfläche auswählen können. 

Geben Sie für die ausgewählte Bezeichnung-Richtlinie die folgenden Zeichenfolgen:

- Schlüssel: **HideBarByDefault**

- Wert: **False**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{HideBarByDefault="False"}

## <a name="enable-recommended-classification-in-outlook"></a>Aktivieren der empfohlenen Klassifizierung in Outlook

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie eine Bezeichnung für die empfohlene Klassifizierung konfigurieren, werden Benutzer dazu aufgefordert, die empfohlene Bezeichnung in Word, Excel und PowerPoint anzunehmen oder abzulehnen. Diese Einstellung erweitert diese Bezeichnungsempfehlung, sodass sie auch in Outlook angezeigt wird.

Geben Sie für die ausgewählte Bezeichnung-Richtlinie die folgenden Zeichenfolgen:

- Schlüssel: **OutlookRecommendationEnabled**

- Wert: **True**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookRecommendationEnabled="True"}

## <a name="set-a-different-default-label-for-outlook"></a>Festlegen anderer Standardbezeichnung für Outlook

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie diese Einstellung konfigurieren, gilt Outlook nicht die standardbezeichnung, die als richtlinieneinstellung für die Option konfiguriert ist **diese Bezeichnung nicht standardmäßig auf Dokumente und e-Mails anwenden**. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden.

Geben Sie für die ausgewählte Bezeichnung-Richtlinie die folgenden Zeichenfolgen:

- Schlüssel: **OutlookDefaultLabel**

- Wert: \< **Bezeichnung GUID**> oder **keine**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookDefaultLabel="None"}


## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>„Not now“ („Nicht jetzt“) für Dokumente bei Verwendung der obligatorischen Bezeichnung entfernen

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Bei Verwendung die Einstellung der Bezeichnung **alle Dokumente und e-Mails müssen eine Bezeichnung haben**, Benutzer werden aufgefordert, beim ersten Speichern eines Office-Dokuments und beim Senden einer e-Mail eine Bezeichnung zu wählen. Bei Office-Dokumenten können Benutzer **Not now** (nicht jetzt) wählen, um die Aufforderung zum Auswählen einer Bezeichnung vorübergehend zu schließen und zum Dokument zurückzukehren. Sie können das gespeicherte Dokument jedoch nicht schließen, ohne es zu bezeichnen. 

Wenn Sie diese Einstellung konfigurieren, wird die Option **Not now** (nicht jetzt) entfernt, sodass die Benutzer eine Bezeichnung wählen müssen, wenn das Dokument zum ersten Mal gespeichert wird.

Geben Sie für die ausgewählte Bezeichnung-Richtlinie die folgenden Zeichenfolgen:

- Schlüssel: **PostponeMandatoryBeforeSaveProperty**

- Wert: **False**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{PostponeMandatoryBeforeSaveProperty="False"}

## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen

Diese Konfiguration verwendet die Richtlinie [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Mit diesen Einstellungen können Sie textbasierte Kopf- und Fußzeilen in Dokumenten entfernen oder ersetzen, wenn diese optischen Kennzeichnungen von einer anderen Bezeichnungslösung angewendet wurden. Beispielsweise enthält die alten Fußzeile für den Namen einer alten Bezeichnung, die Sie nun zu vertraulichkeitsbezeichnungen verwenden Sie einen neuen Bezeichnungsnamen und eine eigene Fußzeile migriert haben.

Wenn der einheitliche bezeichnungs-Client diese Konfiguration in der eigenen Richtlinie erhält, werden die alten Kopf- und Fußzeilen entfernt oder ersetzt werden, wenn das Dokument, in der Office-app geöffnet wird, und eine sensible Beschriftung für das Dokument angewendet wird.

Diese Konfiguration wird für Outlook nicht unterstützt. Beachten Sie außerdem, dass die Verwendung mit Word, Excel und PowerPoint sich negativ auf die Leistung dieser Apps für Benutzer auswirken kann. Mithilfe der Konfiguration können Sie Einstellungen für jede einzelne Anwendung definieren, z.B. die Suche nach Text in Kopf- oder Fußzeilen von Word-Dokumenten, jedoch nicht von Excel-Tabellen oder PowerPoint-Präsentationen.

Da die Leistung für Benutzer den Musterabgleich beeinflusst werden, es wird empfohlen, dass Sie die Office-Anwendungstypen einschränken (**W**Ord, **E**XCEL zurück, **P**PowerPoint), sondern nur für jene die durchsucht werden müssen.

Geben Sie für die ausgewählte Bezeichnung-Richtlinie die folgenden Zeichenfolgen:

- Schlüssel: **RemoveExternalContentMarkingInApp**

- Wert: \<**Office-Anwendungstypen WXP**> 

Beispiele:

- Geben Sie **W** an, um nur Word-Dokumente zu durchsuchen.

- Geben Sie **WP** an, um Word-Dokumente und PowerPoint-Präsentationen zu durchsuchen.

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

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

Geben Sie z. B. die Bezeichnung die folgenden Zeichenfolgen:

- Schlüssel: **ExternalContentMarkingToRemove**

- Value: \<**zu vergleichende Zeichenfolge; als regulärer Ausdruck definiert**> 

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*TEXT*"}

#### <a name="multiline-headers-or-footers"></a>Mehrzeilige Kopf- oder Fußzeilen

Wenn der Text in einer Kopf- oder Fußzeile mehr als eine Zeile umfasst, erstellen Sie einen Schlüssel und einen Wert für jede Zeile. Angenommen, folgende Fußzeile mit zwei Zeilen ist vorhanden:

**The file is classified as Confidential**

**Label applied manually**

Um dieser mehrzeiligen Fußzeile zu entfernen, erstellen Sie die folgenden zwei Einträge für die gleiche Bezeichnungsrichtlinie aus:

- Schlüssel: **ExternalContentMarkingToRemove**

- Schlüsselwert 1: **\*Vertraulich***

- Schlüsselwert 2: **\*Label applied*** (Bezeichnung angewendet) 

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ExternalContentMarkingToRemove="*Confidential*,*Label applied*"}


#### <a name="optimization-for-powerpoint"></a>Optimierung für PowerPoint

In PowerPoint werden Fußzeilen als Formen implementiert. Wenn Sie vermeiden möchten, dass Formen entfernt werden, die den angegeben Text enthalten, jedoch keine Kopf- oder Fußzeilen sind, verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **PowerPointShapeNameToRemove**. Es wird empfohlen, diese Einstellung ebenfalls zu verwenden, um zu verhindern, dass der Text in allen Formen überprüft wird, denn dieser Prozess ist sehr ressourcenintensiv.

Wenn Sie diese zusätzliche erweiterte Clienteinstellung nicht angeben und PowerPoint im Schlüsselwert **RemoveExternalContentMarkingInApp** eingeschlossen ist, werden alle Formen auf den Text überprüft, den Sie im Wert **ExternalContentMarkingToRemove** angeben. 

So finden Sie den Namen der Form, die Sie als Kopf- oder Fußzeile verwenden:

1. Zeigen Sie in PowerPoint den Bereich **Auswahl** an: Registerkarte **Format** > **Arrange** group (Gruppe anordnen) > **Auswahlbereich**.

2. Wählen Sie die Form auf der Folie aus, die die Kopf- oder Fußzeile enthält. Der Name der ausgewählten Form wird nun im Bereich **Auswahl** hervorgehoben.

Verwenden Sie den Namen der Form, um einen Zeichenfolgenwert für den Schlüssel **PowerPointShapeNameToRemove** anzugeben. 

Beispiel: Der Name der Form ist **fc**. Geben Sie den Wert `fc` an, um die Form mit diesem Namen zu entfernen.

- Schlüssel: **PowerPointShapeNameToRemove**

- Wert: \<**Name der PowerPoint-Form**> 

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{PowerPointShapeNameToRemove="fc"}

Wenn Sie mehr als eine PowerPoint-Form entfernt haben, geben Sie so viele Werte, wie Sie Formen zum Entfernen.

Standardmäßig werden nur die Masterfolien auf Kopf- oder Fußzeilen überprüft. Wenn Sie diese Suche auf alle Folien ausweiten möchten (dieser Prozess ist jedoch wesentlich ressourcenintensiver), verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **RemoveExternalContentMarkingInAllSlides**:

- Schlüssel: **RemoveExternalContentMarkingInAllSlides**

- Wert: **True**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RemoveExternalContentMarkingInAllSlides="True"}


## <a name="disable-custom-permissions-in-file-explorer"></a>Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Standardmäßig sehen Benutzer eine Option, mit dem Namen **mit benutzerdefinierten Berechtigungen schützen** Wenn sie mit der rechten Maustaste im Datei-Explorer, und wählen Sie **klassifizieren und schützen**. Mit dieser Option können sie ihre eigenen schutzeinstellungen festlegen, die keine der schutzeinstellungen, die Sie in einer bezeichnungskonfiguration eingeschlossen haben möglicherweise außer Kraft setzen können. Benutzer können außerdem eine Option zum Entfernen des Schutzes sehen. Wenn Sie diese Einstellung konfigurieren, werden diese Optionen von Benutzern nicht angezeigt.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die Richtlinie für die ausgewählte Bezeichnung ein:

- Schlüssel: **EnableCustomPermissions**

- Wert: **False**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissions="False"}

## <a name="for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer"></a>Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie die erweiterte Clienteinstellung zum Konfigurieren [Deaktivieren von benutzerdefinierten Berechtigungen im Datei-Explorer](#disable-custom-permissions-in-file-explorer), Benutzer werden standardmäßig nicht anzeigen oder Ändern von benutzerdefinierten Berechtigungen, die bereits in einem geschützten Dokument festgelegt werden.

Es ist jedoch eine andere erweiterte Clienteinstellung, dass Sie angeben können, damit Benutzer können in diesem Szenario finden Sie unter und benutzerdefinierte Berechtigungen für ein geschütztes Dokument ändern, wenn sie die Datei-Explorer verwenden und mit der rechten Maustaste in der das.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die Richtlinie für die ausgewählte Bezeichnung ein:

- Schlüssel: **EnableCustomPermissionsForCustomProtectedFiles**

- Wert: **True**

Beispiel-PowerShell-Befehl:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableCustomPermissionsForCustomProtectedFiles="True"}


## <a name="for-email-messages-with-attachments-apply-a-label-that-matches-the-highest-classification-of-those-attachments"></a>Wenden Sie für E-Mail-Nachrichten mit Anlagen eine Bezeichnung an, die der höchsten Einstufung dieser Anlagen entspricht

Diese Konfiguration verwendet die Richtlinie [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Diese Einstellung ist für ein, wenn Benutzer Dokumente an eine e-Mail anfügen, und führen Sie die e-Mail-Nachricht selbst nicht beschriftet. In diesem Szenario wird eine Bezeichnung automatisch ausgewählt, für sie basierend auf dem die klassifizierungsbezeichnungen, die auf die Anlagen angewendet werden. Die höchste klassifizierungsbezeichnung ausgewählt ist.

Die Anlage muss eine physische Datei sein, es darf sich nicht um einen Link zu einer Datei handeln (beispielsweise um einen Link zu einer Datei in SharePoint oder OneDrive for Business).

Sie können diese Einstellung konfigurieren **empfohlen**, sodass der Benutzer aufgefordert werden, die die ausgewählte Bezeichnung für ihre e-Mail-Nachricht mit einer anpassbaren QuickInfo gilt. Benutzer können die Empfehlung akzeptieren oder ablehnen. Oder Sie können diese Einstellung konfigurieren **automatische**, wobei die ausgewählte Bezeichnung automatisch angewendet, aber Benutzer können die Bezeichnung entfernen oder eine andere Bezeichnung auswählen, vor dem Senden der e-Mail.

Hinweis: Wenn die Anlage mit die höchste klassifizierungsbezeichnung für den Schutz mit der Einstellung von benutzerdefinierten Berechtigungen konfiguriert ist:

- Wenn der Bezeichnung benutzerdefinierte gehören Berechtigungen (nicht weiterleiten), Outlook, dass die Bezeichnung ausgewählt ist, und nicht weiterleiten Schutz wird angewendet, um die e-Mail-Adresse. 
- Wenn der Bezeichnung benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und Datei-Explorer sind, diese Bezeichnung wird nicht auf die e-Mail-Nachricht angewendet, und ist weder Schutz.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die Richtlinie für die ausgewählte Bezeichnung ein:

- Schlüssel 1: **AttachmentAction**

- Schlüsselwert 1: **Empfohlene** oder **automatische**

- Schlüssel 2: **AttachmentActionTip**

- Schlüssel-Wert 2: "\<angepasst QuickInfo >"


Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{AttachmentAction="Automatic"}

## <a name="add-report-an-issue-for-users"></a>Add "Report an Issue" for users ("Problem melden" für Benutzer hinzufügen)

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie die folgende erweiterte Clienteinstellung angeben, wird Benutzern die Option **Problem melden** angezeigt, die sie aus dem Clientdialogfeld **Hilfe und Feedback** auswählen können. Geben Sie eine HTTP-Zeichenfolge für den Link an. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die Richtlinie für die ausgewählte Bezeichnung ein:

- Schlüssel: **ReportAnIssueLink**

- Wert: **\<HTTP-Zeichenfolge>**

Beispielwert für eine Website: `https://support.contoso.com`

Beispielwert für eine E-Mail-Adresse: `mailto:helpdesk@contoso.com`

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{ReportAnIssueLink="mailto:helpdesk@contoso.com"}

## <a name="implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent"></a>Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben

Diese Konfiguration verwendet die Richtlinie [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie die folgenden erweiterten Clienteinstellungen erstellen und konfigurieren, werden Benutzern Popupmeldungen in Outlook angezeigt, die sie vor dem Senden einer E-Mail warnen können, oder sie nach einer Legitimierung fragen, warum sie eine E-Mail versenden, oder sie aus folgenden Gründen davon abhalten, eine E-Mail zu senden:

- **Die E-Mail oder der E-Mail-Anhang hat eine bestimmte Bezeichnung:**
    - Der Anhang kann einen beliebigen Dateityp haben

- **Die E-Mail oder der E-Mail-Anhang hat keine bestimmte Bezeichnung:**
    - Der Anhang kann ein Office-Dokument oder ein PDF-Dokument sein

Wenn diese Bedingungen erfüllt sind, und die e-Mail-Adresse des Empfängers befindet sich nicht in einer Liste von zulässigen Domänennamen, die Sie angegeben haben, erhält der Benutzer eine Popupmeldung mit einem der folgenden Aktionen aus:

- **Warnung:** Der Benutzer kann bestätigen und senden, oder abbrechen.

- **Justify** (Legitimation): Der Benutzer wird zu einer Legitimierung aufgefordert (mit vordefinierten Optionen oder Freiform).  Der Benutzer kann dann die E-Mail senden oder abbrechen. Der Legitimationstext wird in den X-Header der E-Mail geschrieben, sodass dieser von anderen Systemen gelesen werden kann. Zum Beispiel von Diensten, die der Verhinderung von Datenverlust dienen.

- **Blockieren**: Der Benutzer wird davon abgehalten, die E-Mail zu senden, solange die Bedingung besteht. Die Nachricht beinhaltet den Grund dafür, warum die E-Mail blockiert wird, sodass der Benutzer das Problem aufheben kann. So kann er z.B. bestimmte Empfänger entfernen, oder der E-Mail eine Bezeichnung hinzufügen. 

Die daraus resultierende Aktion wird im lokalen Windows-Ereignisprotokoll protokolliert: **Anwendungs- und Dienstprotokolle** > **Azure Information Protection**:

- Warnmeldungen: Informations-ID 301

- Legitimationsmeldungen: Informations-ID 302

- Blockiermeldungen: Informations-ID 303

Beispielereigniseintrag aus einer Legitimationsmeldung:

```
Client Version: 2.0.779.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Price list.msg
Item Name: Price list
Process Name: OUTLOOK
Action: Justify
User Justification: My manager approved sharing of this content
Action Source: 
User Response: Confirmed
```
Die folgenden Abschnitte enthalten Anweisungen für jedes erweiterte Clienteinstellung an.

> [!TIP]
> Obwohl das Lernprogramm für den Azure Information Protection-Client anstelle der einheitlichen bezeichnungs-Client ist, sehen Sie die erweiterten Einstellungen in der Aktion selbst mit [Lernprogramm: Konfigurieren von Azure Information Protection, um zu steuern, der Informationen, die mithilfe von Outlook oversharing](../infoprotect-oversharing-tutorial.md).

### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren für bestimme Bezeichnungen implementiert:

Erstellen Sie für die ausgewählte Richtlinie eine oder mehrere der folgenden erweiterten Einstellungen mit den folgenden Schlüsseln ein. Geben Sie für die Werte eine oder mehrere Bezeichnungen anhand ihrer GUIDs, die jeweils durch ein Komma getrennt ein.

Beispiel für einen Wert für mehrere Bezeichnung GUIDs als durch Trennzeichen getrennte Zeichenfolge: `dcf781ba-727f-4860-b3c1-73479e31912b,1ace2cc3-14bc-4142-9125-bf946a70542c,3e9df74d-3168-48af-8b11-037e3021813f`


- Warnmeldungen:
    
    - Schlüssel: **OutlookWarnUntrustedCollaborationLabel**
    
    - Wert: \< **-GUIDs, die durch Trennzeichen getrennte Bezeichnung**>

- Legitimationsmeldungen:
    
    - Schlüssel: **OutlookJustifyUntrustedCollaborationLabel**
    
    - Wert: \< **-GUIDs, die durch Trennzeichen getrennte Bezeichnung**>

- Blockiermeldungen:
    
    - Schlüssel: **OutlookBlockUntrustedCollaborationLabel**
    
    - Wert: \< **-GUIDs, die durch Trennzeichen getrennte Bezeichnung**>


Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookWarnUntrustedCollaborationLabel="8faca7b8-8d20-48a3-8ea2-0f96310a848e,b6d21387-5d34-4dc8-90ae-049453cec5cf,bb48a6cb-44a8-49c3-9102-2d2b017dcead,74591a94-1e0e-4b5d-b947-62b70fc0f53a,6c375a97-2b9b-4ccd-9c5b-e24e4fd67f73"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyUntrustedCollaborationLabel="dc284177-b2ac-4c96-8d78-e3e1e960318f,d8bb73c3-399d-41c2-a08a-6f0642766e31,750e87d4-0e91-4367-be44-c9c24c9103b4,32133e19-ccbd-4ff1-9254-3a6464bf89fd,74348570-5f32-4df9-8a6b-e6259b74085b,3e8d34df-e004-45b5-ae3d-efdc4731df24"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockUntrustedCollaborationLabel="0eb351a6-0c2d-4c1d-a5f6-caa80c9bdeec,40e82af6-5dad-45ea-9c6a-6fe6d4f1626b"}


### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-emails-or-attachments-that-dont-have-a-label"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren von E-Mails oder Anhängen implementiert, die keine Bezeichnung haben:

Erstellen Sie z. B. die Bezeichnung die folgenden erweiterten Clienteinstellung mit einem der folgenden Werte ein:

- Warnmeldungen:
    
    - Schlüssel: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Warnung**

- Legitimationsmeldungen:
    
    - Schlüssel: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Justify** (Legitimation)

- Blockiermeldungen:
    
    - Schlüssel: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Blockieren**

- Diese Meldungen deaktivieren:
    
    - Schlüssel: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Deaktiviert**


Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookUnlabeledCollaborationAction="Warn"}


#### <a name="to-define-specific-file-name-extensions-for-the-warn-justify-or-block-pop-up-messages-for-email-attachments-that-dont-have-a-label"></a>Um bestimmte Dateinamenerweiterungen Weitere Erweiterungen für die Warnung zu definieren, begründen oder Popupmeldungen für e-Mail-Anlagen, die eine Bezeichnung aufweisen, nicht blockieren

Standardmäßig wird die Warnung zu rechtfertigen, oder blockieren Popupmeldungen gelten für alle Office-Dokumente und PDF-Dokumente. Sie können diese Liste durch Angabe verfeinern, Dateierweiterungen sollten die Warnung anzuzeigen, zu rechtfertigen, oder Blockieren von Nachrichten mit einem zusätzlichen erweiterte Einstellung und eine durch Trennzeichen getrennte Liste der Dateinamenerweiterungen.

Beispiel für einen Wert für mehrere Dateinamenerweiterungen, als eine durch Trennzeichen getrennte Zeichenfolge zu definieren: `.XLSX,.XLSM,.XLS,.XLTX,.XLTM,.DOCX,.DOCM,.DOC,.DOCX,.DOCM,.PPTX,.PPTM,.PPT,.PPTX,.PPTM`

In diesem Beispiel ist ein PDF-Dokument noch nicht gekennzeichneten führt nicht in warnen, begründen oder Popupmeldungen blockieren.

Geben Sie z. B. die Bezeichnung die folgenden Zeichenfolgen: 


- Schlüssel: **OutlookOverrideUnlabeledCollaborationExtensions**

- Wert: **\<** Dateinamenerweiterungen zum Anzeigen von Nachrichten, die durch Trennzeichen getrennte **>**


Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookOverrideUnlabeledCollaborationExtensions=".PPTX,.PPTM,.PPT,.PPTX,.PPTM"}

### <a name="to-specify-the-allowed-domain-names-for-recipients-exempt-from-the-pop-up-messages"></a>Angeben der zulässigen Domänennamen für Empfänger, die von den Popupmeldungen ausgenommen sind

Wenn Sie in einer zusätzlichen erweiterten Clienteinstellung Domänennamen angeben, werden Benutzer nicht die Popupmeldungen für Empfänger angezeigt mit diesem Domänennamen in ihre e-Mail-Adresse enthalten. In diesem Fall werden die E-Mails problemlos gesendet. Wenn Sie mehrere Domänen angeben möchten, fügen Sie sie kommagetrennt als einzelne Zeichenfolge hinzu.

Eine übliche Konfiguration ist es, die Popupmeldungen nur für die Empfänger anzuzeigen, die nicht zu Ihrer Organisation gehören, oder die keine für Ihre Organisation autorisierte Partner sind. In diesem Fall geben Sie alle E-Mail-Domänen an, die von Ihrer Organisation und von Ihren Partnern verwendet werden.

Klicken Sie z. B. die Bezeichnung erstellen Sie die folgenden erweiterten Clienteinstellungen, und geben Sie für den Wert einer oder mehreren Domänen, die jeweils durch ein Komma getrennt.

Beispielwert für mehrere Domänen als kommagetrennte Zeichenfolge: `contoso.com,fabrikam.com,litware.com`

- Warnmeldungen:
    
    - Schlüssel: **OutlookWarnTrustedDomains**
    
    - Wert: **\<** Domänenname, kommagetrennt **>**

- Legitimationsmeldungen:
    
    - Schlüssel: **OutlookJustifyTrustedDomains**
    
    - Wert: **\<** Domänenname, kommagetrennt **>**

- Blockiermeldungen:
    
    - Schlüssel: **OutlookBlockTrustedDomains**
    
    - Wert: **\<** Domänenname, kommagetrennt **>**

Geben Sie z. B. um e-Mails an Benutzer mit einer e-Mail-Adresse von "contoso.com" nicht zu blockieren, den erweiterten Client-Einstellung **OutlookBlockTrustedDomains** und **"contoso.com"** . Benutzern werden daher nicht die Popup Warnmeldungen in Outlook angezeigt, beim Senden einer e-Mail um john@sales.contoso.com.

PowerShell-Beispielbefehle,, in denen die Bezeichnungsrichtlinie heißt "Global":

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookBlockTrustedDomains="gmail.com"}

    Set-LabelPolicy -Identity Global -AdvancedSettings @{OutlookJustifyTrustedDomains="contoso.com,fabrikam.com,litware.com"}

## <a name="enable-azure-information-protection-analytics-to-discover-sensitive-information-in-documents"></a>Aktivieren von Azure Information Protection-Analysen zur Erkennung vertraulicher Informationen in Dokumenten

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

[Azure Information Protection-Analytics](../reports-aip.md) ermitteln können, und Melden von Azure Information Protection gespeicherte Dokumenten unified bezeichnungs-Clients, bei der, dass der Inhalt vertrauliche Informationen enthält. Standardmäßig werden diese Informationen nicht an Azure Information Protection-Analysen gesendet.

Um dieses Verhalten zu ändern, damit diese Informationen vom einheitlichen bezeichnungs-Client gesendet wird, geben Sie die folgenden Zeichenfolgen für die Richtlinie für die ausgewählte Bezeichnung ein:

- Schlüssel: **RunAuditInformationTypeDiscovery**

- Wert: **True**

Wenn Sie nicht diesen erweiterten Client festlegen festlegen, auditergebnisse weiterhin vom einheitlichen bezeichnungs-Client gesendet werden die Informationen ist jedoch beschränkt auf die berichterstellung, wenn ein Benutzer mit Bezeichnung Inhalt zugegriffen hat.

Zum Beispiel:

- Ohne diese Einstellung können Sie sehen, dass ein Benutzer auf die mit **Vertraulich\Vertrieb** bezeichnete Datei „Finanzen.docx“ zugegriffen hat.

- Und mit dieser Einstellung sehen Sie, dass „Finanzen.docx“ sechs Kreditkartennummern enthält.
    
    - Wenn Sie zusätzlich [Inhaltsübereinstimmungen für umfassendere Analysen](../reports-aip.md#content-matches-for-deeper-analysis) aktivieren, sind außerdem die tatsächlichen Kreditkartennummern einsehbar.

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{RunAuditInformationTypeDiscovery="True"}

## <a name="disable-sending-information-type-matches-for-a-subset-of-users"></a>Deaktivieren der Übereinstimmungen des Sendeinformationstyps für eine Teilmenge von Benutzern

Diese Konfiguration verwendet eine Richtlinie [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie das Kontrollkästchen für [Azure Information Protection-Analysen](../reports-aip.md) aktivieren, das die Inhaltsübereinstimmungen für Ihre vertraulichen Informationstypen oder Ihre benutzerdefinierten Bedingungen sammelt, werden diese Informationen standardmäßig von allen Benutzern gesendet. Wenn Sie einige Benutzer, die keine Daten senden soll haben, erstellen Sie die folgenden erweiterten Clienteinstellung in einer Bezeichnungsrichtlinie für diese Benutzer: 

- Schlüssel: **LogMatchedContent**

- Wert: **Deaktivieren**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{LogMatchedContent="Disable"}

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren

Diese Konfiguration verwendet eine Bezeichnung [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Diese Konfiguration ist nicht kompatibel mit geschützte PDF-Dateien, die eine ppdf-Dateinamenerweiterung haben. Diese Dateien können nicht von Datei-Explorer, PowerShell oder die Überprüfung nicht geöffnet werden.

Für Office-Dokumente, die von Secure Islands erhalten werden, können Sie diese Dokumente mit einer vertraulichkeitsbezeichnung bezeichnen, mit der eine Zuordnung, die Sie definieren. Mit dieser Methode können Sie auch Bezeichnungen aus anderen Lösungen wiederverwenden, wenn diese Bezeichnungen sich in Office-Dokumenten befinden. 

Diese Konfigurationsoption ist die neue vertraulichkeitsbezeichnung wie folgt durch den Azure Information Protection unified bezeichnungs-Client angewendet:

- Bei Office-Dokumenten: Wenn das Dokument in der desktop-app geöffnet wird, wird die neue vertraulichkeitsbezeichnung als festgelegt angezeigt und angewendet wird, wenn das Dokument gespeichert wird.

- In PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) und [Set-AIPFileClassificiation](/powershell/module/azureinformationprotection/set-aipfileclassification) können die neue vertraulichkeitsbezeichnung anwenden. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) die neue vertraulichkeitsbezeichnung nicht angezeigt werden, bis es mit einer anderen Methode festgelegt wird.

- Im Datei-Explorer: Klicken Sie im Dialogfeld "Azure Information Protection" wird die neue vertraulichkeitsbezeichnung aber nicht festgelegt.

Diese Konfiguration müssen Sie angeben, eine erweiterte Einstellung mit dem Namen **LabelByCustomProperties** für jede vertraulichkeitsbezeichnung, die Sie der alten Bezeichnung zuordnen möchten. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Geben Sie einen Namen für die Migrationsregel an. Verwenden Sie einen beschreibenden Namen, die Ihnen dabei hilft, wie eine oder mehrere Bezeichnungen aus Ihrer vorherigen bezeichnungslösung zu identifizieren sollte vertraulichkeitsbezeichnung zugeordnet werden. Der Name wird in den Scannerberichten und in der Ereignisanzeige angezeigt.

Beachten Sie, dass durch diese Einstellung keine ursprüngliche Bezeichnung aus dem Dokument bzw. keine optische Kennzeichnung im Dokument entfernt wird, die von der ursprünglichen Bezeichnung möglicherweise angewendet wurde. Zum Entfernen von Kopf- und Fußzeilen finden Sie unter des vorherigen Abschnitts, [Entfernen von Kopf- und Fußzeilen aus anderen bezeichnungslösungen](#remove-headers-and-footers-from-other-labeling-solutions).

#### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Beispiel 1: 1:1-Zuordnung des gleichen Bezeichnungsnamens

Anforderung: Dokumente mit der Secure Islands-Bezeichnung „Confidential“ sollten in Azure Information Protection die Bezeichnung „Vertraulich“ erhalten.

In diesem Beispiel:

- Die Secure Islands-Bezeichnung lautet **Vertraulich** und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Die erweiterte Einstellung:

- Schlüssel: **LabelByCustomProperties**

- Wert: **Secure Islands-Bezeichnung ist vertraulich, Klassifizierung, vertraulich**

Beispiel für PowerShell-Befehl, in dem die Bezeichnung "Confidential" heißt:

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Confidential,Classification,Confidential"}

#### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Beispiel 2: 1:1-Zuordnung für einen anderen Bezeichnungsnamen

Anforderung: Dokumente mit der Secure Islands-Bezeichnung „Sensitive“ sollten in Azure Information Protection die Bezeichnung „Streng vertraulich“ erhalten.

In diesem Beispiel:

- Die Secure Islands-Bezeichnung lautet **Sensitive** (Sensibel) und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Die erweiterte Einstellung:

- Schlüssel: **LabelByCustomProperties**

- Wert: **Secure Islands-Bezeichnung ist, Klassifizierung, Unterscheidung nach Akzent**

Beispiel für PowerShell-Befehl, in dem die Bezeichnung "Streng vertraulich" benannt wird:

    Set-Label -Identity "Highly Confidential" -AdvancedSettings @{labelByCustomProperties="Secure Islands label is Sensitive,Classification,Sensitive"}

#### <a name="example-3-many-to-one-mapping-of-label-names"></a>Beispiel 3: n:1-Zuordnung von Bezeichnungsnamen

Anforderung: Sie haben zwei Secure Islands-Bezeichnungen, die das Wort "Internal" enthalten, und Sie möchten Dokumente, die dieser Secure Islands-Bezeichnungen, "Allgemein" die Bezeichnung erhalten haben, durch den Azure Information Protection unified bezeichnungs-Client.

In diesem Beispiel:

- Die Secure Islands-Bezeichnungen enthalten den Begriff **Internal** (intern) und sind in der benutzerdefinierten Eigenschaft namens **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

- Schlüssel: **LabelByCustomProperties**

- Wert: **Secure Islands-Bezeichnung enthält intern, Klassifizierung. \*Interne.\***

Beispiel für PowerShell-Befehl, in dem die Bezeichnung "Allgemein" mit dem Namen wird:

    Set-Label -Identity General -AdvancedSettings @{labelByCustomProperties="Secure Islands label contains Internal,Classification,.*Internal.*"}

#### <a name="example-4-multiple-rules-for-the-same-label"></a>Beispiel 4: Mehrere Regeln für die gleiche Bezeichnung

Wenn Sie mehrere Regeln für die gleiche Bezeichnung benötigen, definieren Sie mehrere Zeichenfolgenwerte für denselben Schlüssel. 

In diesem Beispiel:

- Der Secure Islands-Bezeichnungen benannte "Confidential" und "Geheimnis" werden gespeichert, in der benutzerdefinierten Eigenschaft, die mit dem Namen ** Klassifizierung, und den einheitlichen Azure Information Protection-Bezeichnung-Client die vertraulichkeitsbezeichnung, die mit dem Namen "Confidential" angewendet werden soll:

    Set-Label -Identity Confidential -AdvancedSettings @{labelByCustomProperties=ConvertTo-Json("Migrate Confidential label,Classification,Confidential", "Migrate Secret label,Classification,Secret")}

### <a name="extend-your-label-migration-rules-to-emails"></a>Erweitern Sie Ihre Bezeichnung Migrationsregeln-e-Mails

Sie können Ihre Einstellungen mit Outlook-e-Mails zusätzlich zu Office-Dokumenten durch Angabe einer erweiterten richtlinieneinstellung zusätzliche Bezeichnung erweiterte LabelByCustomProperties verwenden. Diese Einstellung hat jedoch einen bekannten negative Auswirkungen auf die Leistung von Outlook, so konfigurieren Sie diese zusätzlichen Einstellung nur wenn Sie eine hohe geschäftsanforderung dafür haben und denken Sie daran, es auf einen null-Zeichenfolge-Wert festgelegt, Sie nach Abschluss die Migration von der andere einer anderen Lösung.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die Richtlinie für die ausgewählte Bezeichnung ein:

- Schlüssel: **EnableLabelByMailHeader**

- Wert: **DI**

Beispiel für PowerShell-Befehl, in denen die Bezeichnungsrichtlinie "Global" heißt:

    Set-LabelPolicy -Identity Global -AdvancedSettings @{EnableLabelByMailHeader="True"}

## <a name="apply-a-custom-property-when-a-label-is-applied"></a>Wenden Sie eine benutzerdefinierte Eigenschaft an, wenn eine Bezeichnung angewendet wird

Diese Konfiguration verwendet eine Bezeichnung [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Es gibt möglicherweise einige Szenarios, wenn Sie eine oder mehrere benutzerdefinierte Eigenschaften auf ein Dokument oder eine e-Mail-Nachricht zusätzlich zu den Metadaten, die von einem vertraulichkeitsbezeichnung angewendet wird, anwenden möchten.

Zum Beispiel:

- Sie sind dabei [Migration von einer anderen bezeichnungslösung](#migrate-labels-from-secure-islands-and-other-labeling-solutions), z. B. Secure Islands. Für eine Interoperabilität bei der Migration sollten Sie die vertraulichkeitsbezeichnungen eine benutzerdefinierte Eigenschaft anwenden, die von der anderen bezeichnungs-Lösung verwendet wird.

- Für das Content Managementsystem (z. B. SharePoint oder eine dokumentverwaltungslösung eines anderen Anbieters), den Sie einen konsistente benutzerdefinierter Eigenschaftenname mit unterschiedlichen Werten für die Bezeichnungen und anhand Benutzerfreundlicher Namen statt der Bezeichnung GUID verwenden möchten.

Für Office-Dokumenten und Outlook-e-Mails können diese Benutzer Bezeichnung mit dem einheitlichen Bezeichnung Azure Information Protection-Client Sie eine oder mehrere benutzerdefinierte Eigenschaften hinzufügen, die Sie definieren. Sie können auch diese Methode für den einheitlichen bezeichnungs-Client verwenden, um eine benutzerdefinierte Eigenschaft als eine Bezeichnung aus anderen Lösungen für den Inhalt anzuzeigen, die vom einheitlichen bezeichnungs-Client noch keine Bezeichnung ist nicht.

Diese Konfigurationsoption befindet werden alle zusätzlichen Eigenschaften, benutzerdefinierte wie folgt durch den Azure Information Protection unified bezeichnungs-Client angewendet:

- Bei Office-Dokumenten: Wenn das Dokument in der desktop-app bezeichnet wird, werden die zusätzlichen benutzerdefinierten Eigenschaften angewendet, wenn das Dokument gespeichert wird.

- Für Outlook-e-Mails: Wenn die e-Mail-Nachricht in Outlook bezeichnet wird, werden die zusätzlichen Eigenschaften für den X-Header angewendet, wenn die e-Mail-Adresse gesendet wird.

- In PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) und [Set-AIPFileClassificiation](/powershell/module/azureinformationprotection/set-aipfileclassification) gilt die zusätzlichen benutzerdefinierten Eigenschaften aus, wenn das Dokument mit der Bezeichnung und gespeichert wird. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) werden die benutzerdefinierten Eigenschaften wie die zugeordnete Bezeichnung angezeigt, wenn eine vertraulichkeitsbezeichnung nicht angewendet wird.

- Im Datei-Explorer: Wenn der Benutzer die Datei mit der rechten Maustaste, und die Bezeichnung wendet, werden die benutzerdefinierten Eigenschaften angewendet.

Diese Konfiguration müssen Sie angeben, eine erweiterte Einstellung mit dem Namen **CustomPropertyByLabel** für jede vertraulichkeitsbezeichnung, die auf die zusätzlichen benutzerdefinierten Eigenschaften angewendet werden soll. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[custom property name],[custom property value]`

#### <a name="example-1-add-a-single-custom-property-for-a-label"></a>Beispiel 1: Fügen Sie eine einzelne benutzerdefinierte Eigenschaft für eine Bezeichnung hinzu

Anforderung: Dokumente, die als "Confidential", durch den Azure Information Protection unified bezeichnungs-Client bezeichnet werden müssen die zusätzliche benutzerdefinierte Eigenschaft mit dem Namen "Klassifizierung" mit dem Wert von "Secret".

In diesem Beispiel:

- Die vertraulichkeitsbezeichnung heißt **vertraulich** und erstellt eine benutzerdefinierte Eigenschaft mit dem Namen **Klassifizierung** mit dem Wert des **Geheimnis**.

Die erweiterte Einstellung:

- Key: **customPropertyByLabel**

- Wert: **Classification,Secret**

Beispiel für PowerShell-Befehl, in dem die Bezeichnung "Confidential" heißt:

    Set-Label -Identity Confidential -AdvancedSettings @{customPropertyByLabel="Classification,Secret"}

#### <a name="example-2-add-multiple-custom-properties-for-a-label"></a>Beispiel 2: Mehrere benutzerdefinierte Eigenschaften für eine Bezeichnung hinzufügen

Um mehr als eine benutzerdefinierte Eigenschaft für die gleiche Bezeichnung hinzuzufügen, müssen Sie mehrere Zeichenfolgenwerte für denselben Schlüssel zu definieren.

Beispiel-PowerShell-Befehl, wobei den Namen Ihrer Bezeichnung "Allgemein" und eine benutzerdefinierte Eigenschaft mit dem Namen hinzugefügt werden soll **Klassifizierung** mit dem Wert des **allgemeine** und eine zweite benutzerdefinierte Eigenschaft mit dem Namen **Vertraulichkeit** mit dem Wert des **intern**:

    Set-Label -Identity General -AdvancedSettings @{customPropertyByLabel=ConvertTo-Json("Classification,General", "Sensitivity,Internal")}

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden

Diese Konfiguration verwendet die Bezeichnung [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Verwenden Sie diese Einstellungen nur, wenn Sie eine funktionierende haben [S/MIME-Bereitstellung](https://docs.microsoft.com/office365/SecurityCompliance/s-mime-for-message-signing-and-encryption) und eine Bezeichnung für diese Schutzmethode für e-Mails anstelle von Rights Management-Schutz von Azure Information Protection automatisch angewendet werden soll. Der resultierende Schutz ist derselbe wie bei der manuellen Auswahl von S/MIME-Optionen in Outlook.

Um eine erweiterte Einstellung für eine digitale Signaturen von S/MIME zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **SMimeSign**

- Wert: **True**

Um eine erweiterte Einstellung für die S/MIME-Verschlüsselung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **SMimeEncrypt**

- Wert: **True**

Wenn die Bezeichnung, die Sie angeben, für die Verschlüsselung für die Vorschauversion des Azure Information Protection unified bezeichnungs-Clients konfiguriert ist ersetzt S/MIME-Schutz der Rights Management-Schutz nur in Outlook. Die allgemein verfügbare Version des einheitlichen bezeichnungs-Clients weiterhin die Einstellungen für die datenverschlüsselung für die Bezeichnung im Administrationscenter angegeben. Für Office-apps mit integrierten Bezeichnungen diese gelten nicht den Schutz von S/MIME- aber stattdessen nicht weiterleiten Schutz anwenden.

Wenn Sie die Bezeichnung nur in Outlook angezeigt werden soll, konfigurieren Sie die Bezeichnung zum Anwenden der Verschlüsselung **nur e-Mail-Nachrichten in Outlook**.

Beispiel für PowerShell-Befehlen, in dem die Bezeichnung "Nur Empfänger" benannt wird:

    Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeSign="True"}

    Set-Label -Identity "Recipients Only" -AdvancedSettings @{SMimeEncrypt="True"}

## <a name="specify-a-default-sublabel-for-a-parent-label"></a>Geben Sie eine standardmäßige untergeordnete Bezeichnung für eine übergeordnete Bezeichnung

Diese Konfiguration verwendet eine Bezeichnung [erweiterte Einstellung](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren. Sie wird von der Preview-Version des einheitlichen bezeichnungs-Clients nur unterstützt.

Wenn Sie eine untergeordnete Bezeichnung zu einer Bezeichnung hinzufügen, können Benutzer nicht mehr zu einem Dokument oder die e-Mail-Adresse die übergeordneten Bezeichnung anwenden. Wählen Sie in der Standardeinstellung Benutzer die übergeordneten Bezeichnung, um die untergeordneten Bezeichnungen anzuzeigen, dass sie anwenden können, und Sie dann eine dieser untergeordneten Bezeichnungen wählen. Wenn Sie diese erweiterte Einstellung konfigurieren, wenn Benutzer die übergeordnete Bezeichnung auswählen, wird eine untergeordnete Bezeichnung automatisch ausgewählt und für sie übernommen: 

- Schlüssel: **DefaultSubLabelId**

- Wert: \<sublabel GUID >

Beispiel-PowerShell-Befehl, in dem die übergeordnete Bezeichnung wird mit der Bezeichnung "Confidential" und die "Alle Mitarbeiter" untergeordnete Bezeichnung eine GUID vom 8faca7b8 - 8d 20-48a3-8ea2-0f96310a848e:

    Set-Label -Identity "Confidential" -AdvancedSettings @{defaultsublabels="8faca7b8-8d20-48a3-8ea2-0f96310a848e"}

## <a name="specify-a-color-for-the-label"></a>Geben Sie eine Farbe für die Bezeichnung

Diese Konfiguration verwendet die Bezeichnung [Erweiterte Einstellungen](#how-to-configure-advanced-settings-for-the-client-by-using-office-365-security--compliance-center-powershell) müssen Sie mithilfe von Office 365 Security & Compliance Center und PowerShell konfigurieren.

Verwenden Sie diese erweiterte Einstellung, um eine Farbe für eine Bezeichnung festlegen. Um die Farbe anzugeben, geben Sie ein hexadezimales Tripel für die Komponenten roten, grünen und blauen (RGB) der Farbe ein. #40e0d0 ist z. B. den hexadezimalen RGB-Wert für Türkis.

Wenn Sie einen Verweis für diese Codes benötigen, finden Sie eine hilfreiche Tabelle aus der [ \<Farbe >](https://developer.mozilla.org/docs/Web/CSS/color_value) Seite aus der MSDN-Web-Dokumentation. Sie finden diese Codes auch in vielen Anwendungen, in denen Sie Bilder bearbeiten können. Beispielsweise können Sie bei Microsoft Paint eine benutzerdefinierte Farbe aus einer Palette auswählen, wobei die RGB-Werte automatisch angezeigt werden, die Sie dann kopieren können.

Um die erweiterte Einstellung für die Farbe des einer Bezeichnung zu konfigurieren, geben Sie die folgenden Zeichenfolgen für die ausgewählte Bezeichnung ein:

- Schlüssel: **Farbe**

- Wert: \<RGB-Hexadezimalwert >

Beispiel für PowerShell-Befehl, in dem die Bezeichnung "Public" heißt:

    Set-Label -Identity Public -AdvancedSettings @{color="#40e0d0"}

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer produktionsumgebung müssen Benutzer in der Regel nicht anmelden, da ein anderer Benutzer bei der Verwendung von Azure Information Protection die Bezeichnung Client unified. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

Mithilfe des Dialogfelds **Microsoft Azure Information Protection** können Sie prüfen, an welchem Konto Sie derzeit angemeldet sind: Öffnen Sie eine officeanwendung und klicken Sie auf die **Startseite** Registerkarte die **Vertraulichkeit** Schaltfläche, und wählen Sie dann **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. Ein Symptom für mit dem falschen Konto enthält Fehler beim Herunterladen der Bezeichnungen, oder wird nicht angezeigt, die Bezeichnungen oder unerwartete Verhaltensweisen.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn Sie eine Eingabeaufforderung in der Office-Anwendung für die Anmeldung an den Azure Information Protection-Dienst nicht angezeigt werden, zurück zu den **Microsoft Azure Information Protection** , und wählen Sie im Dialogfeld **melden Sie sich** aus der aktualisiert **Clientstatus** Abschnitt.

Darüber hinaus gilt:

- Wenn der einheitliche Bezeichnung Azure Information Protection-Client mit dem alten Konto weiterhin nach Abschluss dieser Schritte angemeldet ist, löschen Sie alle Cookies in Internet Explorer, und wiederholen Sie dann die Schritte 1 und 2.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich bei Windows abmelden und mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Tokendatei gelöscht haben. Authentifiziert die einheitliche Bezeichnung Azure Information Protection-Client anschließend automatisch mit Ihrem aktuell angemeldeten Benutzerkonto.

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- Können Sie die **Einstellungen zurücksetzen** option **Hilfe und Feedback** melden Sie sich ab, und löschen die aktuell heruntergeladene Bezeichnungen und die Richtlinieneinstellungen von Office 365 Security & Compliance Center die Microsoft 365 Security Center oder Microsoft 365 Compliance Center.


## <a name="change-the-local-logging-level"></a>Ändern des lokalen Protokolliergrads

In der Standardeinstellung für die Azure Information Protection bezeichnungs Client schreibt Client-Dateien in unified der **%localappdata%\Microsoft\MSIP** Ordner. Diese Dateien dienen zur Problembehandlung durch den Microsoft-Support.
 
Um den Protokolliergrad für diese Dateien zu ändern, finden Sie in der Registrierung die folgenden Wertnamen, und setzen Sie den Wert auf den gewünschten Protokollierungsgrad:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\LogLevel**

Legen Sie den Protokolliergrad auf einen der folgenden Werte fest:

- **Off**: Keine lokale Protokollierung.

- **Fehler**: Nur Fehler.

- **Info**: Minimale Protokollierung, die keine Ereignis-IDs umfasst.

- **Debug**: Vollständige Informationen.

- **Trace**: Ausführliche Protokollierung (die Standardeinstellung für Clients).

Diese Einstellung in der Registrierung ändert sich nicht auf die Informationen an Azure Information Protection für die gesendeten [zentralen reporting](../reports-aip.md).


## <a name="next-steps"></a>Nächste Schritte
Nun, da Sie den Azure Information Protection unified bezeichnungs-Client angepasst haben, finden Sie unter den folgenden Ressourcen für zusätzliche Informationen, Sie zur Unterstützung dieses Clients müssen eventuell:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
