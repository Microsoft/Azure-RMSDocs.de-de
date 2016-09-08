---
title: Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell | Azure RMS
description: "Sie können Microsoft Azure RMS mithilfe des Office 365 Admin Centers oder des klassischen Azure-Portals aktivieren, aber Sie können hierfür auch das PowerShell-Modul für AADRM verwenden."
author: cabailey
manager: mbaldwin
ms.date: 08/18/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 26988d2e9b6e2ff320e424fa94051afa0055d234


---

# Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell

>*Gilt für: Azure Rights Management, Office 365*

Sie können Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) mithilfe des [!INCLUDE[o365_2](../includes/o365_2_md.md)] Admin Centers oder des klassischen Azure-Portals aktivieren, aber Sie können hierfür auch das PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (AADRM) verwenden.

Nachdem Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktiviert haben, ist eventuell keine weitere Administration des Diensts mehr notwendig. Bei einigen komplexeren Konfigurationsszenarios kann es jedoch erforderlich sein, das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verwenden. In der folgenden Tabelle werden einige der komplexeren Konfigurationsszenarios aufgeführt, bei denen Windows PowerShell verwendet wird. Eine vollständige Liste der verfügbaren Cmdlets mit weiteren Informationen über die einzelnen Aktionen finden Sie unter [Azure Rights Management – Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Informationen zum Installieren des Windows PowerShell-Moduls für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Es gibt auch ein zusätzliches Windows PowerShell-Modul, **RMSProtection**, das Azure RMS und AD RMS unterstützt. Dieses Modul unterstützt Schützen sowie Entfernen des Schutzes von mehreren Dateien, sodass Sie beispielsweise alle Dateien in einem Ordner in einem Schritt schützen können. Weitere Informationen finden Sie im Abschnitt [Skriptoptionen für Administratoren](configure-super-users.md#scripting-options-for-super-users) des Artikels [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](configure-super-users.md).

|Aufgabe|Zu verwendendes Cmdlet|
|-------------------|------------------------------|
|Migrieren von lokalem Rights Management (AD RMS oder Windows RMS) zu [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Herstellen einer Verbindung mit dem [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Dienst für Ihre Organisation oder Trennen dieser Verbindung.|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Generieren und Verwalten Ihres eigenen Mandantenschlüssels (BYOK-Szenario).|[Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Aktivieren oder Deaktivieren des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation.|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Deaktivieren oder Aktivieren der Website für Dokumentnachverfolgung für Azure Rights Management.|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Konfigurieren der Onboarding-Steuerelemente für eine stufenweise Bereitstellung von Azure Rights Management.|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Erstellen und Verwalten von Richtlinienvorlagen für Rechte für Ihre Organisation.|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Expodert-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Impodert-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Konfigurieren der maximalen Anzahl von Tagen, während denen auf Inhalte, die Ihr Unternehmen schützt, ohne Internetverbindung (die Nutzungslizenz-Gültigkeitsdauer) zugegriffen werden kann.|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Verwalten des Superuser-Features von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] für Ihre Organisation.|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|Verwalten von Benutzern und Gruppen, die zur Administration des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation autorisiert sind.|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Abrufen eines Protokolls der administrativen [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Aufgaben für Ihre Organisation.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Protokollieren und Analysieren der Nutzungsprotokollierung für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|Anzeigen der aktuellen Konfiguration des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migrieren Ihrer Organisation von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu einer lokalen AD RMS-Bereitstellung.|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|






<!--HONumber=Aug16_HO4-->


