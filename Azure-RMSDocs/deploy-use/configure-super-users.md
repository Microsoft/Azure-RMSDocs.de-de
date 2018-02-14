---
title: "Konfigurieren von Administratoren für Azure Rights Management – AIP"
description: "Verstehen und Implementieren der Administratorfunktion des Azure Rights Management-Diensts aus Azure Information Protection, sodass autorisierte Personen und Dienste immer auf die Daten, die mit Azure Rights Management für Ihre Organisation geschützt werden, zugreifen und diese überprüfen können. Diese Fähigkeit wird gelegentlich als „Schlussfolgern über Daten“ (reasoning over data) bezeichnet und ist ein ausschlaggebendes Element dabei, die Kontrolle über die Daten Ihrer Organisation zu behalten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a134d6619f67bfc3d26cb1726fe07e8ffca403cd
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung

>*Gilt für: Azure Information Protection, Office 365*

Die Administratorfunktion des Azure Rights Management-Diensts aus Azure Information Protection stellt sicher, dass autorisierte Personen und Dienste immer auf die Daten, die mit Azure Rights Management für Ihre Organisation geschützt werden, zugreifen und diese überprüfen können. Bei Bedarf können diese Personen/Dienste auch den zuvor angewendeten Schutz aufheben oder ändern. 

Ein Administrator verfügt immer über das Rights Management-[Nutzungsrecht](configure-usage-rights.md) zum Vollzugriff auf durch den Azure Information Protection-Mandanten Ihrer Organisation geschützte Dokumente und E-Mails. Diese Fähigkeit wird gelegentlich als „Schlussfolgern über Daten“ (reasoning over data) bezeichnet und ist ein ausschlaggebendes Element dabei, die Kontrolle über die Daten Ihrer Organisation zu behalten. Sie verwenden diese Funktion beispielsweise für die folgenden Szenarien:

- Ein Mitarbeiter verlässt die Organisation, und Sie müssen alle Dateien lesen können, die von dieser Person geschützt wurden.

- Ein IT-Administrator muss die aktuelle Schutzrichtlinie entfernen, die für Dateien konfiguriert wurde, und eine neue Schutzrichtlinie anwenden.

- Exchange Server muss Postfächer für Suchvorgänge indizieren.

- Sie verfügen über IT-Dienste für DLP-Lösungen (Data Loss Prevention, Verhinderung von Datenverlust), über Inhaltsverschlüsselungsgateways (Content Encryption Gateways, CEGs) und Antischadsoftware, die Dateien überprüfen müssen, die bereits geschützt sind.

- Sie müssen große Mengen von Dateien in einem Zug zu Überwachungszwecken oder aus rechtlichen oder anderen Compliance-Gründen entschlüsseln.

Standardmäßig ist die Administratorfunktion nicht aktiviert, und dieser Rolle sind keine Benutzer zugeordnet. Sie wird jedoch automatisch aktiviert, wenn Sie den Rights Management-Connector für Exchange konfigurieren. Für Standarddienste, die unter Exchange Online, SharePoint Online oder SharePoint Server ausgeführt werden, ist sie nicht erforderlich.

Wenn Sie die Administratorfunktion manuell aktivieren müssen, verwenden Sie das PowerShell-Cmdlet [Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature), und ordnen Sie dann mithilfe des Cmdlets [Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser) nach Bedarf Benutzer (oder Dienstkonten) zu. Verwenden Sie alternativ das Cmdlet [Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup), und fügen Sie dieser Gruppe die entsprechenden Benutzer (oder andere Gruppen) hinzu. 

Obwohl es einfacher ist, eine Gruppe für Ihre Administratoren zu verwalten, seien Sie sich bewusst, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). Wenn Sie also einen neuen Benutzer als Administrator bestimmen müssen, um Inhalt sofort zu entschlüsseln, fügen Sie diesen Benutzer mithilfe von „Add-AadrmSuperUser“ hinzu, statt den Benutzer einer vorhandenen Gruppe zuzuordnen, die Sie mithilfe von „Set-AadrmSuperUserGroup“ konfiguriert haben.

> [!NOTE]
> Wenn Sie das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] noch nicht installiert haben, lesen Sie die Informationen unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Bewährte Sicherheitsmethoden für die Administratorfunktion:

- Beschränken und überwachen Sie die Administratoren, die als globale Administratoren für Ihren Office 365- oder Azure Information Protection-Mandanten fungieren oder denen mithilfe des Cmdlets [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) die Rolle „GlobalAdministrator“ zugewiesen wurde. Diese Benutzer können die Administratorfunktion aktivieren und Benutzer (und sich selbst) als Administratoren festlegen und damit potenziell alle Dateien entschlüsseln, die von Ihrer Organisation geschützt werden.

- Wenn Sie sehen möchten, welche Benutzer und Dienstkonten einzeln als Administratoren zugeordnet sind, verwenden Sie das Cmdlet [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser). Wenn Sie ermitteln möchten, ob eine Administratorgruppe konfiguriert ist, verwenden Sie das Cmdlet [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperusergroup) und Ihre Standardtools für die Benutzerverwaltung, um zu überprüfen, welche Benutzer zu dieser Gruppe gehören. Wie alle administrativen Vorgänge werden auch das Aktivieren oder Deaktivieren der Administratorfunktion sowie das Hinzufügen oder Entfernen von Administratoren protokolliert und können mithilfe des Befehls [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) überwacht werden. Wenn Administratoren Dateien entschlüsseln, wird dieser Vorgang ebenfalls protokolliert und kann mit der [Verwendungsprotokollierung](log-analyze-usage.md) überwacht werden.

- Wenn Sie die Administratorfunktion für die alltäglichen Dienste nicht benötigen, sollten Sie diese Funktion nur im Bedarfsfall aktivieren und mit dem Cmdlet [Disable-AadrmSuperUserFeature](/powershell/module/aadrm/disable-aadrmsuperuserfeature) wieder deaktivieren.

Der folgende Protokollauszug zeigt einige Beispieleinträge, die mit dem Cmdlet „Get-AadrmAdminLog“ erstellt wurden. In diesem Beispiel bestätigt der Administrator von Contoso Ltd., dass die Administratorfunktion deaktiviert ist, fügt Richard Simone als Administrator hinzu, überprüft, ob Richard der einzige für den Azure Rights Management-Dienst konfigurierte Administrator ist, und aktiviert dann die Administratorfunktion, damit Richard nun einige Dateien entschlüsseln kann, die zuvor von einem Mitarbeiter geschützt wurden, der das Unternehmen mittlerweile verlassen hat.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>Skriptoptionen für Administratoren
Häufig muss eine Person, die als Administrator für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] fungiert, den Schutz von mehreren Dateien an mehreren Speicherorten aufheben. Dies kann zwar manuell erfolgen, es ist jedoch effizienter (und häufig auch zuverlässiger), wenn ein Skript verwendet wird. Verwenden Sie dazu die Cmdlets [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) und [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile). 

Wenn Sie die Klassifizierung und den Schutz verwenden, können Sie auch das Cmdlet [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) nutzen, um eine neue Bezeichnung ohne Schutz anzuwenden, oder die Bezeichnung entfernen, die einen entsprechenden Schutz angewendet hat. 

Weitere Informationen zu diesen Cmdlets finden Sie im Administratorhandbuch für den Azure Information Protection-Client unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](../rms-client/client-admin-guide-powershell.md).

> [!NOTE]
> Das AzureInformationProtection-Modul ersetzt das PowerShell-Modul für den RMS-Schutz, das mit dem Tool für den RMS-Schutz installiert wurde. Beide Module unterscheiden sich vom [Windows PowerShell-Modul für Azure Rights Management](administer-powershell.md) und ergänzen es. Das AzureInformationProtection-Modul unterstützt Azure Information Protection, den Azure Rights Management-Dienst (Azure RMS) für Azure Information Protection sowie Active Directory Rights Management Services (AD RMS).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

