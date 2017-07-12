---
title: "Verwalten von Azure Rights Management mit Windows PowerShell – AIP"
description: "Erfahren Sie, wie Sie das PowerShell-Modul für den Azure Rights Management-Dienst (AADRM) von Azure Information Protection verwenden können, um diesen Dienst für Ihre Organisation zu verwalten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 018d04dc408230bf9a104f460930797d0a558ce7
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="administering-the-azure-rights-management-service-by-using-windows-powershell" class="xliff"></a>

# Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell

>*Gilt für: Azure Information Protection, Office 365*

Müssen Sie PowerShell zum Verwalten des Azure Rights Management-Diensts für Azure Information Protection verwenden? Dies ist möglicherweise nicht erforderlich, wenn Sie ein globaler Administrator sind und die einzige für diesen Dienst erforderliche Konfiguration darin besteht, ihn zu aktivieren (oder zu deaktivieren) und Rights Management-Vorlagen zu konfigurieren.

Sie müssen PowerShell jedoch für komplexere Konfigurationen und auch dann verwenden, wenn Sie kein globaler Administrator sind, sondern die Berechtigungen zum Verwalten des Diensts von einem globalen Administrator erhalten haben. Möglicherweise bevorzugen Sie die Verwendung von PowerShell auch zur effizienteren Kontrolle der Befehlszeile und für die Skripterstellung.

Die Tabelle im nächsten Abschnitt enthält einige Szenarien mit erweiterter Konfiguration, die PowerShell verwenden. Wenn die Konfiguration auch ohne PowerShell durchgeführt werden kann, sind diese Informationen ebenfalls in der Tabelle enthalten.

Eine vollständige Liste der verfügbaren Cmdlets für dieses Modul mit weiteren Informationen über die einzelnen Aktionen finden Sie unter [AADRM](/powershell/module/aadrm/?view=azureipps#aadrm).

> [!NOTE]
> Informationen zum Installieren dieses PowerShell-Moduls finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Zusätzlich zu diesem dienstseitigen PowerShell-Modul installiert der Azure Information Protection-Client ein zusätzliches PowerShell-Modul, **AzureInformationProtection**. Dieses Clientmodul unterstützt das Klassifizieren und Schützen von mehreren Dateien, sodass Sie beispielsweise alle Dateien in einem Ordner in einem Schritt schützen können. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](../rms-client/client-admin-guide-powershell.md).

<a id="cmdlets-grouped-by-administration-task" class="xliff"></a>

## Nach Verwaltungsaufgabe gruppierte Cmdlets

|Aufgabe|Zu verwendendes Cmdlet|
|-------------------|------------------------------|
|Migrieren von lokalem Rights Management (AD RMS oder Windows RMS) zu Azure Information Protection|[Import-AadrmTpd](/powershell/aadrm/vlatest/import-aadrmtpd)<br /><br />[Set-AadrmKeyProperties](/powershell/module/aadrm/set-aadrmkeyproperties)|
|Herstellen einer Verbindung mit dem [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Dienst für Ihre Organisation oder Trennen dieser Verbindung.|[Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice)<br /><br />[Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice)|
|Generieren und Verwalten Ihres eigenen Mandantenschlüssels (BYOK-Szenario).|[Use-AadrmKeyVaultKey](/powershell/aadrm/vlatest/use-aadrmkeyvaultkey)<br /><br />[Get-AadrmKeys](/powershell/aadrm/vlatest/get-aadrmkeys)|
|Aktivieren oder Deaktivieren des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation.<br /><br />Sie können diese Aktionen auch über die Verwaltungsportale durchführen. Weitere Informationen finden Sie unter [Aktivieren des Azure Rights Management-Diensts](activate-service.md).|[Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm)<br /><br />[Disable-Aadrm](/powershell/aadrm/vlatest/disable-aadrm)|
|Deaktivieren oder Aktivieren der Website für die Dokumentkontrolle für Azure Information Protection|[Disable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/disable-aadrmdocumenttrackingfeature)<br /><br />[Enable-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/enable-aadrmdocumenttrackingfeature)<br /><br />[Get-AadrmDocumentTrackingFeature](/powershell/aadrm/vlatest/get-aadrmdocumenttrackingfeature)<br /><br />[Set-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/set-aadrmdonottrackusergroup)<br /><br />[Clear-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/Clear-AadrmDoNotTrackUserGroup)<br /><br />[Get-AadrmDoNotTrackUserGroup](/powershell/module/aadrm/get-AadrmDoNotTrackUserGroup)|
|Konfigurieren der Onboarding-Steuerelemente für eine stufenweise Bereitstellung des Azure Rights Management-Diensts|[Get-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/get-aadrmonboardingcontrolpolicy)<br /><br />[Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy)|
|Erstellen und verwalten Sie Rights Management-Vorlagen für Ihre Organisation.<br /><br />Sie können die meisten der folgenden Aktionen auch über das klassische Azure-Portal durchführen, obwohl PowerShell eine differenziertere Kontrolle ermöglicht. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](configure-custom-templates.md).|[Add-AadrmTemplate](/powershell/aadrm/vlatest/add-aadrmtemplate)<br /><br />[Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate)<br /><br />[Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate)<br /><br />[Get-AadrmTemplateProperty](/powershell/aadrm/vlatest/get-aadrmtemplateproperty)<br /><br />[Import-AadrmTemplate](/powershell/aadrm/vlatest/import-aadrmtemplate)<br /><br />[New-AadrmRightsDefinition](/powershell/aadrm/vlatest/new-aadrmrightsdefinition)<br /><br />[Remove-AadrmTemplate](/powershell/aadrm/vlatest/remove-aadrmtemplate)<br /><br />[Set-AadrmTemplateProperty](/powershell/aadrm/vlatest/set-aadrmtemplateproperty)|
|Konfigurieren der maximalen Anzahl von Tagen, während denen auf Inhalte, die Ihr Unternehmen schützt, ohne Internetverbindung (die Nutzungslizenz-Gültigkeitsdauer) zugegriffen werden kann.|[Get-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/get-aadrmmaxuselicensevaliditytime)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](/powershell/aadrm/vlatest/set-aadrmmaxuselicensevaliditytime)|
|Verwalten des Superuser-Features von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] für Ihre Organisation.|[Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature)<br /><br />[Disable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/disable-aadrmsuperuserfeature)<br /><br />[Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser)<br /><br />[Get-AadrmSuperUser](/powershell/aadrm/vlatest/get-aadrmsuperuser)<br /><br />[Remove-AadrmSuperUser](/powershell/aadrm/vlatest/remove-aadrmsuperuser)<br /><br />[Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup)<br /><br />[Get-AadrmSuperUserGroup](/powershell/aadrm/vlatest/get-aadrmsuperusergroup)<br /><br />[Clear-AadrmSuperUserGroup](/powershell/aadrm/vlatest/clear-aadrmsuperusergroup)|
|Verwalten von Benutzern und Gruppen, die zur Administration des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation autorisiert sind.|[Add-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/add-aadrmrolebasedadministrator)<br /><br />[Get-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/get-aadrmrolebasedadministrator)<br /><br />[Remove-AadrmRoleBasedAdministrator](/powershell/aadrm/vlatest/remove-aadrmrolebasedadministrator)|
|Abrufen eines Protokolls der administrativen [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Aufgaben für Ihre Organisation.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Protokollieren und Analysieren der Nutzungsprotokollierung für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](/powershell/aadrm/vlatest/get-aadrmuserlog)|
|Anzeigen der aktuellen Konfiguration des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation.|[Get-AadrmConfiguration](/powershell/aadrm/vlatest/get-aadrmconfiguration)|
|Migrieren Ihrer Organisation von Azure Information Protection zu einer lokalen AD RMS-Bereitstellung|[Set-AadrmMigrationUrl](/powershell/aadrm/vlatest/set-aadrmmigrationurl)<br /><br />[Get-AadrmMigrationUrl](/powershell/aadrm/vlatest/get-aadrmmigrationurl)|

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
