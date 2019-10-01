---
title: Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell
description: Erfahren Sie, wie Sie das PowerShell-Modul für den Schutzdienst von Azure Information Protection verwenden können, um diesen Dienst für Ihren Mandanten zu verwalten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 2dcb20c2bdc3f690f86968e8f3c45ae49849b827
ms.sourcegitcommit: 28c1de5f9d1426f160f0e0bafcf9f76769e662b6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71679094"
---
# <a name="administering-protection-from-azure-information-protection-by-using-powershell"></a>Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Müssen Sie PowerShell verwenden, um den Schutzdienst über Azure Information Protection zu verwalten? Dies ist unter Umständen nicht erforderlich, wenn all Ihre Konfigurationen im Azure-Portal oder im Microsoft 365 Admin Center ausgeführt werden können. Allerdings müssen Sie PowerShell für einige erweiterte Konfigurationen verwenden. Außerdem bevorzugen Sie möglicherweise die Verwendung von PowerShell für eine effizientere Steuerung und Skripterstellung über die Befehlszeile.

Die Tabelle im nächsten Abschnitt enthält einige Szenarien mit erweiterter Konfiguration, die PowerShell verwenden. Wenn die Konfiguration auch ohne PowerShell durchgeführt werden kann, sind diese Informationen ebenfalls in der Tabelle enthalten.

Eine umfassende Liste der verfügbaren Cmdlets für dieses Modul mit weiteren Informationen zu den einzelnen Cmdlets finden Sie unter [aipservice](/powershell/module/aipservice/?view=azureipps#aipservice).

> [!NOTE]
> Informationen zum Installieren dieses PowerShell-Moduls finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

Zusätzlich zu diesem dienstseitigen PowerShell-Modul installiert der Azure Information Protection-Client ein zusätzliches PowerShell-Modul, **AzureInformationProtection**. Dieses Clientmodul unterstützt das Klassifizieren und Schützen von mehreren Dateien, sodass Sie beispielsweise alle Dateien in einem Ordner in einem Schritt schützen können. Weitere Informationen finden Sie im Administratorhandbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).

## <a name="cmdlets-grouped-by-administration-task"></a>Nach Verwaltungsaufgabe gruppierte Cmdlets

|Aufgabe|Zu verwendendes Cmdlet|
|-------------------|------------------------------|
|Migrieren von lokalem Rights Management (AD RMS oder Windows RMS) zu Azure Information Protection|[Import-AipServiceTpd](/powershell/module/aipservice/import-aipservicetpd)<br /><br />[Set-AipServiceKeyProperties](/powershell/module/aipservice/set-aipservicekeyproperties)|
|Herstellen einer Verbindung mit dem Rights Management-Dienst für Ihre Organisation oder Trennen dieser Verbindung.|[Connect-AipService](/powershell/module/aipservice/connect-aipservice)<br /><br />[Disconnect-AipServiceService](/powershell/module/aipservice/disconnect-aipservice)|
|Generieren und Verwalten Ihres eigenen Mandantenschlüssels (BYOK-Szenario).|[Set-AipServiceKeyProperties](/powershell/module/aipservice/set-aipservicekeyproperties)<br /><br />[Use-AipServiceKeyVaultKey](/powershell/module/aipservice/use-aipservicekeyvaultkey)<br /><br />[Get-AipServiceKeys](/powershell/module/aipservice/get-aipservicekeys)|
|Aktivieren oder Deaktivieren des Rights Management-Diensts für Ihre Organisation.<br /><br />Sie können diese Aktionen auch über die Verwaltungsportale durchführen. Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](activate-service.md).|[Enable-aipservice](/powershell/module/aipservice/enable-aipservice)<br /><br />[Deaktivieren-aipservice](/powershell/module/aipservice/disable-aipservice)|
|Verwalten Sie die Website für die Dokumentnachverfolgung für Azure Information Protection.|[Disable-AipServiceDocumentTrackingFeature](/powershell/module/aipservice/disable-aipservicedocumenttrackingfeature)<br /><br />[Enable-AipServiceDocumentTrackingFeature](/powershell/module/aipservice/enable-aipservicedocumenttrackingfeature)<br /><br />[Get-AipServiceDocumentTrackingFeature](/powershell/module/aipservice/get-aipservicedocumenttrackingfeature)<br /><br />[Set-AipServiceDoNotTrackUserGroup](/powershell/module/aipservice/set-aipservicedonottrackusergroup)<br /><br />[Clear-AipServiceDoNotTrackUserGroup](/powershell/module/aipservice/Clear-AipServiceDoNotTrackUserGroup)<br /><br />[Get-AipServiceDoNotTrackUserGroup](/powershell/module/aipservice/get-AipServiceDoNotTrackUserGroup)<br /><br />[Get-AipServiceTrackingLog](/powershell/module/aipservice/Get-AipServiceTrackingLog)<br /><br />[Get-AipServiceDocumentLog](/powershell/module/aipservice/Get-AipServiceDocumentLog)|
|Konfigurieren der Onboarding-Steuerelemente für eine stufenweise Bereitstellung des Azure Rights Management-Diensts|[Get-AipServiceOnboardingControlPolicy](/powershell/module/aipservice/get-aipserviceonboardingcontrolpolicy)<br /><br />[Set-AipServiceOnboardingControlPolicy](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy)|
|Erstellen und verwalten Sie Rights Management-Vorlagen für Ihre Organisation.<br /><br />Sie können die meisten der folgenden Aktionen auch über das Azure-Portal durchführen, obwohl PowerShell eine differenziertere Kontrolle ermöglicht. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](configure-policy-templates.md).|[Add-aipservicetemplate](/powershell/module/aipservice/add-aipservicetemplate)<br /><br />[Export-aipservicetemplate](/powershell/module/aipservice/export-aipservicetemplate)<br /><br />[Get-AipServiceTemplate](/powershell/module/aipservice/get-aipservicetemplate)<br /><br />[Get-AipServiceTemplateProperty](/powershell/module/aipservice/get-aipservicetemplateproperty)<br /><br />[Import-AipServiceTemplate](/powershell/module/aipservice/import-aipservicetemplate)<br /><br />[New-AipServiceRightsDefinition](/powershell/module/aipservice/new-aipservicerightsdefinition)<br /><br />[Remove-aipservicetemplate](/powershell/module/aipservice/remove-aipservicetemplate)<br /><br />[Set-AipServiceTemplateProperty](/powershell/module/aipservice/set-aipservicetemplateproperty)|
|Konfigurieren der maximalen Anzahl von Tagen, während denen auf Inhalte, die Ihr Unternehmen schützt, ohne Internetverbindung (die Nutzungslizenz-Gültigkeitsdauer) zugegriffen werden kann.|[Get-AipServiceMaxUseLicenseValidityTime](/powershell/module/aipservice/get-aipservicemaxuselicensevaliditytime)<br /><br />[Set-AipServiceMaxUseLicenseValidityTime](/powershell/module/aipservice/set-aipservicemaxuselicensevaliditytime)|
|Verwalten der Administratorfunktion von Rights Management für Ihre Organisation.|[Enable-AipServiceSuperUserFeature](/powershell/module/aipservice/enable-aipservicesuperuserfeature)<br /><br />[Disable-AipServiceSuperUserFeature](/powershell/module/aipservice/disable-aipservicesuperuserfeature)<br /><br />[Add-AipServiceSuperUser](/powershell/module/aipservice/add-aipservicesuperuser)<br /><br />[Get-AipServiceSuperUser](/powershell/module/aipservice/get-aipservicesuperuser)<br /><br />[Remove-AipServiceSuperUser](/powershell/module/aipservice/remove-aipservicesuperuser)<br /><br />[Set-AAipServiceSuperUserGroup](/powershell/module/aipservice/set-aipservicesuperusergroup)<br /><br />[Get-AipServiceSuperUserGroup](/powershell/module/aipservice/get-aipservicesuperusergroup)<br /><br />[Clear-AipServiceSuperUserGroup](/powershell/module/aipservice/clear-aipservicesuperusergroup)|
|Verwalten von Benutzern und Gruppen, die zur Administration des Rights Management-Diensts für Ihre Organisation autorisiert sind.|[Add-Aip-ServiceRoleBasedAdministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator)<br /><br />[Get-Aip-ServiceRoleBasedAdministrator](/powershell/module/aipservice/get-aipservicerolebasedadministrator)<br /><br />[Remove-AIP-servicerolebasedadministrator](/powershell/module/aipservice/remove-aipservicerolebasedadministrator)|
|Abrufen eines Protokolls der administrativen Rights Management-Aufgaben für Ihre Organisation.|[Get-AipServiceAdminLog](/powershell/module/aipservice/get-aipserviceadminlog)|
|Protokollieren und Analysieren der Nutzungsprotokollierung für Rights Management.|[Get-AipServiceUserLog](/powershell/module/aipservice/get-aipserviceuserlog)|
|Anzeigen der aktuellen Konfiguration des Rights Management-Diensts für Ihre Organisation.|[Get-AipServiceConfiguration](/powershell/module/aipservice/get-aipserviceconfiguration)|
|Migrieren Ihrer Organisation von Azure Information Protection zu einer lokalen AD RMS-Bereitstellung|[Set-AipServiceMigrationUrl](/powershell/module/aipservice/set-aipservicemigrationurl)<br /><br />[Get-AipServiceMigrationUrl](/powershell/module/aipservice/get-aipservicemigrationurl)|

