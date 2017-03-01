---
title: "Konfigurieren von Administratoren für Azure Rights Management – AIP"
description: "Lernen Sie die Administratorfunktion des Azure Rights Management-Diensts aus Azure Information Protection kennen, und implementieren Sie sie. So können autorisierte Personen und Dienste immer auf die Daten, die mit Azure Rights Management für Ihre Organisation geschützt werden, zugreifen und diese überprüfen. Diese Fähigkeit wird gelegentlich als „Schlussfolgern über Daten“ (reasoning over data) bezeichnet und ist ein ausschlaggebendes Element dabei, die Kontrolle über die Daten Ihrer Organisation zu behalten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: f1c50d67ba03cee9846e81f98aad6da0da33a951
ms.lasthandoff: 02/24/2017


---

# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung

>*Gilt für: Azure Information Protection, Office 365*

Die Administratorfunktion des Azure Rights Management-Diensts aus Azure Information Protection stellt sicher, dass autorisierte Personen und Dienste immer auf die Daten, die mit Azure Rights Management für Ihre Organisation geschützt werden, zugreifen und diese überprüfen können. Falls notwendig, können diese Personen/Dienste auch den zuvor angewendeten Schutz aufheben oder ändern. Ein Administrator verfügt immer über die vollständigen Besitzerrechte für alle Nutzungslizenzen, die vom Azure Information Protection-Mandanten der Organisation gewährt wurden. Diese Fähigkeit wird gelegentlich als "Schlussfolgern über Daten" (reasoning over data) bezeichnet und ist ein ausschlaggebendes Element dabei, die Kontrolle über die Daten Ihrer Organisation zu behalten. So verwenden Sie diese Funktion beispielsweise für alle der folgenden Szenarien:

-   Ein Mitarbeiter verlässt die Organisation, und Sie müssen alle Dateien lesen können, die von dieser Person geschützt wurden.

-   Ein IT-Administrator muss die aktuelle Schutzrichtlinie entfernen, die für Dateien konfiguriert wurde, und eine neue Schutzrichtlinie anwenden.

-   Exchange Server muss Postfächer für Suchvorgänge indizieren.

-   Sie verfügen über IT-Dienste für DLP-Lösungen (Data Loss Prevention, Verhinderung von Datenverlust), über Inhaltsverschlüsselungsgateways (Content Encryption Gateways, CEGs) und Antischadsoftware, die Dateien überprüfen müssen, die bereits geschützt sind.

-   Sie müssen große Mengen von Dateien in einem Zug zu Überwachungszwecken oder aus rechtlichen oder anderen Compliance-Gründen entschlüsseln.

Standardmäßig ist die Administratorfunktion nicht aktiviert, und dieser Rolle sind keine Benutzer zugeordnet. Sie wird jedoch automatisch aktiviert, wenn Sie den Rights Management-Connector für Exchange konfigurieren; für Standarddienste, die unter Exchange Online, SharePoint Online oder SharePoint Server ausgeführt werden, ist sie nicht erforderlich.

Wenn Sie die Administratorfunktion manuell aktivieren müssen, verwenden Sie das Windows PowerShell-Cmdlet [Enable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629400.aspx), und ordnen Sie dann mithilfe des Cmdlets [Add-AadrmSuperUser](https://msdn.microsoft.com/library/azure/dn629411.aspx) nach Bedarf Benutzer (oder Dienstkonten) zu, oder verwenden Sie das Cmdlet [Set-AadrmSuperUserGroup](https://msdn.microsoft.com/library/azure/mt653943.aspx), und fügen Sie dieser Gruppe die entsprechenden Benutzer (oder anderen Gruppen) hinzu. 

> [!NOTE]
> Wenn Sie das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] noch nicht installiert haben, lesen Sie [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Bewährte Sicherheitsmethoden für die Administratorfunktion:

-   Beschränken und überwachen Sie die Administratoren, die als globale Administratoren für Ihren Office 365- oder Azure Information Protection-Mandanten fungieren oder denen mithilfe des Cmdlets [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/azure/dn629417.aspx) die Rolle „GlobalAdministrator“ zugewiesen wurde. Diese Benutzer können die Administratorfunktion aktivieren und Benutzer (einschließlich der eigenen Person) als Administratoren festlegen und damit potenziell alle Dateien entschlüsseln, die von Ihrer Organisation geschützt werden.

-   Wenn Sie sehen möchten, welche Benutzer und Dienstkonten einzeln als Administratoren zugeordnet sind, verwenden Sie das [Get-AadrmSuperUser-Cmdlet](https://msdn.microsoft.com/library/azure/dn629408.aspx). Wenn Sie feststellen möchten, ob eine Administratorgruppe konfiguriert ist, verwenden Sie das [Get-AadrmSuperUser-Cmdlet](https://msdn.microsoft.com/library/azure/mt653942.aspx) und Ihre Standardtools für die Benutzerverwaltung, um zu überprüfen, welche Benutzer zu dieser Gruppe gehören. Wie alle administrativen Vorgänge werden auch das Aktivieren oder Deaktivieren der Administratorfunktion sowie das Hinzufügen oder Entfernen von Administratoren protokolliert und können mithilfe des Befehls [Get-AadrmAdminLog](https://msdn.microsoft.com/library/azure/dn629430.aspx) überwacht werden. Wenn Administratoren Dateien entschlüsseln, wird dieser Vorgang ebenfalls protokolliert und kann mit der [Verwendungsprotokollierung](log-analyze-usage.md) überwacht werden.

-   Wenn Sie die Administratorfunktion für die alltäglichen Dienste nicht benötigen, sollten Sie diese Funktion nur im Bedarfsfall aktivieren und mit dem Cmdlet [Disable-AadrmSuperUserFeature](https://msdn.microsoft.com/library/azure/dn629428.aspx) wieder deaktivieren.

Der folgende Protokollauszug zeigt einige Beispieleinträge, die mit dem Cmdlet „Get-AadrmAdminLog“ erstellt wurden. In diesem Beispiel bestätigt der Administrator von Contoso Ltd., dass die Administratorfunktion deaktiviert ist, fügt Richard Simone als Administrator hinzu, überprüft, dass Richard der einzige für den Azure Rights Management-Dienst konfigurierte Administrator ist, und aktiviert dann die Administratorfunktion, damit Richard nun einige Dateien entschlüsseln kann, die zuvor von einem Mitarbeiter geschützt wurden, der das Unternehmen mittlerweile verlassen hat.

`2015-08-01T18:58:20    admin@contoso.com    GetSuperUserFeatureState    Passed    Disabled`

`2015-08-01T18:59:44    admin@contoso.com    AddSuperUser -id rsimone@contoso.com    Passed    True`

`2015-08-01T19:00:51    admin@contoso.com    GetSuperUser    Passed    rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com    SetSuperUserFeatureState -state Enabled    Passed    True`

## <a name="scripting-options-for-super-users"></a>Skriptoptionen für Administratoren
Eine Person, die als Administrator für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] fungiert, muss häufig den Schutz von mehreren Dateien an mehreren Speicherorten aufheben. Dies kann zwar manuell erfolgen, es ist jedoch effizienter (und häufig auch zuverlässiger), wenn ein Skript verwendet wird. Verwenden Sie dazu die Cmdlets [Unprotect-RMSFile](/powershell/azureinformationprotection/vlatest/unprotect-rmsfile) und [Protect-RMSFile](/powershell/azureinformationprotection/vlatest/protect-rmsfile) gemäß Ihren Anforderungen. 

Wenn Sie die Klassifizierung und den Schutz verwenden, können Sie auch das Cmdlet [Set-AIPFileLabel](/powershell/azureinformationprotection/vlatest/set-aipfilelabel) verwenden, um eine neue Bezeichnung ohne Schutz anzuwenden, oder die Bezeichnung entfernen, die einen entsprechenden Schutz angewendet hat. 

Weitere Informationen zu diesen Cmdlets finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](../rms-client/client-admin-guide-powershell.md) im Administratorhandbuch für den Azure Information Protection-Client.

> [!NOTE]
> Das AIP-Modul ersetzt das PowerShell-Modul „RMS Protection“, das mit dem RMS Protection Tool installiert wurde. Beide Module unterscheiden sich vom [Windows PowerShell-Modul für Azure Rights Management](administer-powershell.md) und ergänzen es. Das AIP-Modul unterstützt Azure Information Protection, den Azure Rights Management-Dienst (Azure RMS) für Azure Information Protection und auch Active Directory Rights Management Services (AD RMS).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


