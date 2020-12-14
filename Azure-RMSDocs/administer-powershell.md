---
title: Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell
description: Erfahren Sie, wie Sie das PowerShell-Modul für den Schutzdienst von Azure Information Protection verwenden können, um diesen Dienst für Ihren Mandanten zu verwalten.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 04/28/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 8ae0df982453206ec1069767dc0c25e74a996c1d
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384116"
---
# <a name="administering-protection-from-azure-information-protection-by-using-powershell"></a>Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Müssen Sie PowerShell verwenden, um den Schutzdienst über Azure Information Protection zu verwalten? Dies ist unter Umständen nicht erforderlich, wenn all Ihre Konfigurationen im Azure-Portal oder im Microsoft 365 Admin Center ausgeführt werden können. Allerdings müssen Sie PowerShell für einige erweiterte Konfigurationen verwenden. Außerdem bevorzugen Sie möglicherweise die Verwendung von PowerShell für eine effizientere Steuerung und Skripterstellung über die Befehlszeile.

Die Tabelle im nächsten Abschnitt enthält einige Szenarien mit erweiterter Konfiguration, die PowerShell verwenden. Wenn die Konfiguration auch ohne PowerShell durchgeführt werden kann, sind diese Informationen ebenfalls in der Tabelle enthalten.

Eine umfassende Liste der verfügbaren Cmdlets für dieses Modul mit weiteren Informationen zu den einzelnen Cmdlets finden Sie unter [aipservice](/powershell/module/aipservice/#aipservice).

Informationen zum Installieren dieses PowerShell-Moduls finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

> [!TIP]
> Zusätzlich zu diesem dienstseitigen PowerShell-Modul installiert der Azure Information Protection-Client ein zusätzliches PowerShell-Modul, **AzureInformationProtection**. 
>
> Dieses Clientmodul unterstützt das Klassifizieren und Schützen von mehreren Dateien, sodass Sie beispielsweise alle Dateien in einem Ordner in einem Schritt schützen können. Weitere Informationen finden Sie im Administrator Handbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/clientv2-admin-guide-powershell.md) .

## <a name="cmdlets-grouped-by-administration-task"></a>Nach Verwaltungsaufgabe gruppierte Cmdlets

|Aufgabe|Zu verwendendes Cmdlet|
|-------------------|------------------------------|
|Migrieren von lokalem Rights Management (AD RMS oder Windows RMS) zu Azure Information Protection|[Import-aipservicetpd](/powershell/module/aipservice/import-aipservicetpd)<br /><br />[Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties)|
|Herstellen einer Verbindung mit dem Rights Management-Dienst für Ihre Organisation oder Trennen dieser Verbindung.|[Connect-aipservice](/powershell/module/aipservice/connect-aipservice)<br /><br />[Disconnect-aipserviceservice](/powershell/module/aipservice/disconnect-aipservice)|
|Generieren und Verwalten Ihres eigenen Mandantenschlüssels (BYOK-Szenario).|[Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties)<br /><br />[Verwenden Sie-aipservicekeyvaultkey.](/powershell/module/aipservice/use-aipservicekeyvaultkey)<br /><br />[Get-aipservicekeys](/powershell/module/aipservice/get-aipservicekeys)|
|Aktivieren oder Deaktivieren des Rights Management-Diensts für Ihre Organisation.<br /><br />Sie können diese Aktionen auch über die Verwaltungsportale durchführen. Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](activate-service.md).|[Enable-aipservice](/powershell/module/aipservice/enable-aipservice)<br /><br />[Deaktivieren-aipservice](/powershell/module/aipservice/disable-aipservice)|
|Konfigurieren der Onboarding-Steuerelemente für eine stufenweise Bereitstellung des Azure Rights Management-Diensts|[Get-aipserviceonboardingcontrolpolicy](/powershell/module/aipservice/get-aipserviceonboardingcontrolpolicy)<br /><br />[Set-aipserviceonboardingcontrolpolicy](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy)|
|Erstellen und verwalten Sie Rights Management-Vorlagen für Ihre Organisation.<br /><br />Sie können die meisten der folgenden Aktionen auch über das Azure-Portal durchführen, obwohl PowerShell eine differenziertere Kontrolle ermöglicht. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).|[Add-aipservicetemplate](/powershell/module/aipservice/add-aipservicetemplate)<br /><br />[Export-aipservicetemplate](/powershell/module/aipservice/export-aipservicetemplate)<br /><br />[Get-aipservicetemplate](/powershell/module/aipservice/get-aipservicetemplate)<br /><br />[Get-aipservicetemplateproperty](/powershell/module/aipservice/get-aipservicetemplateproperty)<br /><br />[Import-aipservicetemplate](/powershell/module/aipservice/import-aipservicetemplate)<br /><br />[New-aipservicerighzdefinition](/powershell/module/aipservice/new-aipservicerightsdefinition)<br /><br />[Remove-aipservicetemplate](/powershell/module/aipservice/remove-aipservicetemplate)<br /><br />[Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty)|
|Konfigurieren Sie die maximale Anzahl von Tagen, auf die Inhalte, die Ihr Unternehmen schützt, ohne Internetverbindung (die Gültigkeitsdauer der Nutzungslizenz) zugreifen können.|[Get-aipservicemaxuselicenabvaliditytime](/powershell/module/aipservice/get-aipservicemaxuselicensevaliditytime)<br /><br />[Set-aipservicemaxuselicensevaliditytime](/powershell/module/aipservice/set-aipservicemaxuselicensevaliditytime)|
|Verwalten der Administratorfunktion von Rights Management für Ihre Organisation.|[Enable-aipservicesuperuserfeature](/powershell/module/aipservice/enable-aipservicesuperuserfeature)<br /><br />[Deaktivieren-aipservicesuperuserfeature](/powershell/module/aipservice/disable-aipservicesuperuserfeature)<br /><br />[Add-aipservicesuperuser](/powershell/module/aipservice/add-aipservicesuperuser)<br /><br />[Get-aipservicesuperuser](/powershell/module/aipservice/get-aipservicesuperuser)<br /><br />[Remove-aipservicesuperuser](/powershell/module/aipservice/remove-aipservicesuperuser)<br /><br />[Set-aaipservicesuperusergroup](/powershell/module/aipservice/set-aipservicesuperusergroup)<br /><br />[Get-aipservicesuperusergroup](/powershell/module/aipservice/get-aipservicesuperusergroup)<br /><br />[Clear-aipservicesuperusergroup](/powershell/module/aipservice/clear-aipservicesuperusergroup)|
|Verwalten von Benutzern und Gruppen, die zur Administration des Rights Management-Diensts für Ihre Organisation autorisiert sind.|[Add-AIP-servicerolebasedadministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator)<br /><br />[Get-AIP-servicerolebasedadministrator](/powershell/module/aipservice/get-aipservicerolebasedadministrator)<br /><br />[Remove-AIP-servicerolebasedadministrator](/powershell/module/aipservice/remove-aipservicerolebasedadministrator)|
|Abrufen eines Protokolls der administrativen Rights Management-Aufgaben für Ihre Organisation.|[Get-aipserviceadminlog](/powershell/module/aipservice/get-aipserviceadminlog)|
|Protokollieren und Analysieren der Nutzungsprotokollierung für Rights Management.|[Get-aipserviceuserlog](/powershell/module/aipservice/get-aipserviceuserlog)|
|Anzeigen der aktuellen Konfiguration des Rights Management-Diensts für Ihre Organisation.|[Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration)|
|Migrieren Ihrer Organisation von Azure Information Protection zu einer lokalen AD RMS-Bereitstellung|[Set-aipservicemigrationurl](/powershell/module/aipservice/set-aipservicemigrationurl)<br /><br />[Get-aipservicemigrationurl](/powershell/module/aipservice/get-aipservicemigrationurl)|
|Verwalten Sie die Website für die Dokumentnachverfolgung für Azure Information Protection.<br><br>**Relevant für**: nur klassischer Client|[Deaktivieren-aipservicedocumenttrackingfeature](/powershell/module/aipservice/disable-aipservicedocumenttrackingfeature)<br /><br />[Enable-aipservicedocumenttrackingfeature](/powershell/module/aipservice/enable-aipservicedocumenttrackingfeature)<br /><br />[Get-aipservicedocumenttrackingfeature](/powershell/module/aipservice/get-aipservicedocumenttrackingfeature)<br /><br />[Set-aipservicedonottrackusergroup](/powershell/module/aipservice/set-aipservicedonottrackusergroup)<br /><br />[Clear-aipservicedonottrackusergroup](/powershell/module/aipservice/Clear-AipServiceDoNotTrackUserGroup)<br /><br />[Get-aipservicedonottrackusergroup](/powershell/module/aipservice/get-AipServiceDoNotTrackUserGroup)<br /><br />[Get-aipservicetrackinglog](/powershell/module/aipservice/Get-AipServiceTrackingLog)<br /><br />[Get-aipservicedocumentlog](/powershell/module/aipservice/Get-AipServiceDocumentLog)|
| | |
