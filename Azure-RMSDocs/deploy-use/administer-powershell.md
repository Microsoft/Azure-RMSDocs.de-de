---
title: Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell | Azure Information Protection
description: "Erfahren Sie, wie Sie das Windows PowerShell-Modul für den Azure Rights Management-Dienst (AADRM) von Azure Information Protection verwenden können, um diesen Dienst für Ihre Organisation zu verwalten."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: dfd8a2716d60bb4ea466f4e3911e4ba9a0333241


---

# Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell

>*Gilt für: Azure Information Protection, Office 365*

Sie können den Azure Rights Management-Dienst für Azure Information Protection mithilfe des [!INCLUDE[o365_2](../includes/o365_2_md.md)] Admin Centers oder des klassischen Azure-Portals aktivieren, Sie können hierfür jedoch auch das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (AADRM) verwenden.

Nachdem Sie den Azure Rights Management-Dienst aktiviert haben, ist eventuell keine weitere Administration des Diensts mehr notwendig. Bei einigen komplexeren Konfigurationsszenarios kann es jedoch erforderlich sein, das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verwenden. In der folgenden Tabelle werden einige der komplexeren Konfigurationsszenarios aufgeführt, bei denen Windows PowerShell verwendet wird. Eine vollständige Liste der verfügbaren Cmdlets mit weiteren Informationen über die einzelnen Aktionen finden Sie unter [Azure Rights Management – Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> Informationen zum Installieren des Windows PowerShell-Moduls für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Es gibt noch das ergänzende Windows PowerShell-Modul **RMSProtection**, das sowohl den Azure Rights Management-Dienst (Azure RMS) als auch Active Directory Rights Management Services (AD RMS) unterstützt. Dieses Modul unterstützt Schützen sowie Entfernen des Schutzes von mehreren Dateien, sodass Sie beispielsweise alle Dateien in einem Ordner in einem Schritt schützen können. Weitere Informationen finden Sie im Abschnitt [Skriptoptionen für Administratoren](configure-super-users.md#scripting-options-for-super-users) des Artikels [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](configure-super-users.md).

|Aufgabe|Zu verwendendes Cmdlet|
|-------------------|------------------------------|
|Migrieren von lokalem Rights Management (AD RMS oder Windows RMS) zu Azure Information Protection|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)|
|Herstellen einer Verbindung mit dem [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Dienst für Ihre Organisation oder Trennen dieser Verbindung.|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx)<br /><br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx)|
|Generieren und Verwalten Ihres eigenen Mandantenschlüssels (BYOK-Szenario).|[Use-AadrmKeyVaultKey](https://msdn.microsoft.com/library/azure/mt759829.aspx)<br /><br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx)|
|Aktivieren oder Deaktivieren des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation.|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx)<br /><br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx)|
|Deaktivieren oder Aktivieren der Website für die Dokumentkontrolle für Azure Information Protection|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx)<br /><br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx)<br /><br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx)|
|Konfigurieren der Onboarding-Steuerelemente für eine stufenweise Bereitstellung des Azure Rights Management-Diensts|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx)<br /><br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx)|
|Erstellen und Verwalten von Richtlinienvorlagen für Rechte für Ihre Organisation.|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx)<br /><br />[Expodert-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx)<br /><br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx)<br /><br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx)<br /><br />[Impodert-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx)<br /><br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx)<br /><br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx)<br /><br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx)|
|Konfigurieren der maximalen Anzahl von Tagen, während denen auf Inhalte, die Ihr Unternehmen schützt, ohne Internetverbindung (die Nutzungslizenz-Gültigkeitsdauer) zugegriffen werden kann.|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx)<br /><br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx)|
|Verwalten des Superuser-Features von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] für Ihre Organisation.|[Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx)<br /><br />[Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx)<br /><br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx)<br /><br />[Get-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629408.aspx)<br /><br />[Remove-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629405.aspx)<br /><br />[Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx)<br /><br />[Get-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653942.aspx)<br /><br />[Clear-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653944.aspx)|
|Verwalten von Benutzern und Gruppen, die zur Administration des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation autorisiert sind.|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx)<br /><br />[Get-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629407.aspx)<br /><br />[Remove-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629424.aspx)|
|Abrufen eines Protokolls der administrativen [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Aufgaben für Ihre Organisation.|[Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx)|
|Protokollieren und Analysieren der Nutzungsprotokollierung für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)].|[Get-AadrmUserLog](https://msdn.microsoft.com/library/azure/mt653941.aspx)|
|Anzeigen der aktuellen Konfiguration des [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Diensts für Ihre Organisation.|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx)|
|Migrieren Ihrer Organisation von Azure Information Protection zu einer lokalen AD RMS-Bereitstellung|[Set-AadrmMigrationUrl](https://msdn.microsoft.com/library/azure/dn629429.aspx)<br /><br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx)|






<!--HONumber=Sep16_HO4-->


