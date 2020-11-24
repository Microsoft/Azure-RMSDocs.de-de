---
title: Konfigurieren von Administratoren für Azure Rights Management – AIP
description: Verstehen und implementieren Sie die Administrator Funktion des Azure-Rights Management Diensts von Azure Information Protection, damit autorisierte Personen und Dienste jederzeit die geschützten Daten Ihrer Organisation lesen und überprüfen können.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 09/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: bf7b4d46c2dd63c87f48c244f38a515c7376fc1a
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568237"
---
# <a name="configuring-super-users-for-azure-information-protection-and-discovery-services-or-data-recovery"></a>Configuring super users for Azure Information Protection and discovery services or data recovery (Konfigurieren von Administratoren für Azure Information Protection und Ermittlungsdienste oder Wiederherstellung von Daten)

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Die Administratorfunktion des Azure Rights Management-Diensts aus Azure Information Protection stellt sicher, dass autorisierte Personen und Dienste immer auf die Daten, die mit Azure Rights Management für Ihre Organisation geschützt werden, zugreifen und diese überprüfen können. Bei Bedarf kann der Schutz anschließend entfernt oder geändert werden.

Ein Administrator verfügt immer über das Rights Management-[Nutzungsrecht](configure-usage-rights.md) zum Vollzugriff auf durch den Azure Information Protection-Mandanten Ihrer Organisation geschützte Dokumente und E-Mails. Diese Fähigkeit wird gelegentlich als „Schlussfolgern über Daten“ (reasoning over data) bezeichnet und ist ein ausschlaggebendes Element dabei, die Kontrolle über die Daten Ihrer Organisation zu behalten. Sie verwenden diese Funktion beispielsweise für die folgenden Szenarien:

- Ein Mitarbeiter verlässt die Organisation, und Sie müssen alle Dateien lesen können, die von dieser Person geschützt wurden.

- Ein IT-Administrator muss die aktuelle Schutzrichtlinie entfernen, die für Dateien konfiguriert wurde, und eine neue Schutzrichtlinie anwenden.

- Exchange Server muss Postfächer für Suchvorgänge indizieren.

- Sie verfügen über IT-Dienste für DLP-Lösungen (Data Loss Prevention, Verhinderung von Datenverlust), über Inhaltsverschlüsselungsgateways (Content Encryption Gateways, CEGs) und Antischadsoftware, die Dateien überprüfen müssen, die bereits geschützt sind.

- Sie müssen große Mengen von Dateien in einem Zug zu Überwachungszwecken oder aus rechtlichen oder anderen Compliance-Gründen entschlüsseln.

## <a name="configuration-for-the-super-user-feature"></a>Konfiguration für das Administratorfeature

Standardmäßig ist die Administratorfunktion nicht aktiviert, und dieser Rolle sind keine Benutzer zugeordnet. Sie wird automatisch für Sie aktiviert, wenn Sie den Rights Management Connector für Exchange konfigurieren. Dies ist für Standarddienste, die Exchange Online, Microsoft SharePoint Server oder SharePoint in Microsoft 365 ausführen, nicht erforderlich.

Wenn Sie die Administrator Funktion manuell aktivieren müssen, verwenden Sie das PowerShell-Cmdlet [enable-aipservicesuperuserfeature](/powershell/module/aipservice/enable-aipservicesuperuserfeature), und weisen Sie dann Benutzer (oder Dienst Konten) nach Bedarf mithilfe des Cmdlets [Add-aipservicesuperuser](/powershell/module/aipservice/add-aipservicesuperuser) oder des Cmdlets [Set-aipservicesuperusergroup](/powershell/module/aipservice/set-aipservicesuperusergroup) zu, und fügen Sie dieser Gruppe ggf. Benutzer (oder andere Gruppen) hinzu. 

Obwohl es einfacher ist, eine Gruppe für Ihre Administratoren zu verwalten, seien Sie sich bewusst, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](prepare.md#group-membership-caching-by-azure-information-protection). Wenn Sie also einen neuen Benutzer als Administrator zuweisen müssen, um Inhalt sofort zu entschlüsseln, fügen Sie diesen Benutzer mithilfe von Add-aipservicesuperuser hinzu, anstatt ihn zu einer vorhandenen Gruppe hinzuzufügen, die Sie mithilfe von Set-aipservicesuperusergroup konfiguriert haben.

> [!NOTE]
> Wenn Sie das Windows PowerShell-Modul für Azure Rights Management noch nicht installiert haben, finden Sie weitere Informationen unter [Installieren des PowerShell-Moduls für aipservice](install-powershell.md).

Es spielt keine Rolle, wann Sie das Administratorfeature aktivieren oder wann Sie Benutzer als Administratoren hinzufügen. Wenn Sie beispielsweise das Feature am Donnerstag aktivieren und einen Benutzer am Freitag hinzufügen, kann dieser Benutzer sofort den Inhalt öffnen, der zu Wochenbeginn geschützt wurde.

## <a name="security-best-practices-for-the-super-user-feature"></a>Bewährte Sicherheitsmethoden für das Administratorfeature

- Beschränken und überwachen Sie die Administratoren, die als globaler Administrator für Ihre Microsoft 365 oder Azure Information Protection Mandanten zugewiesen sind oder denen mithilfe des Cmdlets [Add-aipservicerolebasedadministrator](/powershell/module/aipservice/add-aipservicerolebasedadministrator) die Rolle "Global Administrator" zugewiesen ist. Diese Benutzer können die Administratorfunktion aktivieren und Benutzer (und sich selbst) als Administratoren festlegen und damit potenziell alle Dateien entschlüsseln, die von Ihrer Organisation geschützt werden.

- Verwenden Sie das Cmdlet [Get-aipservicesuperuser](/powershell/module/aipservice/get-aipservicesuperuser) , um anzuzeigen, welche Benutzer und Dienst Konten einzeln als Administratoren zugewiesen werden. 

- Um festzustellen, ob eine Administrator Gruppe konfiguriert ist, verwenden Sie das Cmdlet [Get-aipservicesuperusergroup](/powershell/module/aipservice/get-aipservicesuperusergroup) und ihre Standardbenutzer Verwaltungs Tools, um zu überprüfen, welche Benutzer Mitglied dieser Gruppe sind. 

- Wie alle Verwaltungs Aktionen werden auch das Aktivieren oder Deaktivieren der Administrator Funktion sowie das Hinzufügen oder Entfernen von Administratoren protokolliert und können mithilfe des Befehls [Get-aipserviceadminlog](/powershell/module/aipservice/get-aipserviceadminlog) überwacht werden. Informationen hierzu finden Sie beispielsweise [unter Beispiel Überwachung für die Administrator Funktion](#example-auditing-for-the-super-user-feature).

- Wenn Administratoren Dateien entschlüsseln, wird dieser Vorgang ebenfalls protokolliert und kann mit der [Verwendungsprotokollierung](log-analyze-usage.md) überwacht werden.

    > [!NOTE]
    > Obwohl die Protokolle Details zur Entschlüsselung enthalten, einschließlich des Benutzers, der die Datei entschlüsselt hat, bemerken Sie nicht, wenn der Benutzer ein Administrator ist. Verwenden Sie die Protokolle zusammen mit den oben aufgeführten Cmdlets, um zunächst eine Liste von Administratoren zu erfassen, die Sie in den Protokollen identifizieren können.
    >

- Wenn Sie die Administrator Funktion für die alltäglichen Dienste nicht benötigen, aktivieren Sie die Funktion nur, wenn Sie Sie benötigen, und deaktivieren Sie Sie mithilfe des Cmdlets " [Deaktivieren-aipservicesuperuserfeature](/powershell/module/aipservice/disable-aipservicesuperuserfeature) " erneut.

### <a name="example-auditing-for-the-super-user-feature"></a>Beispielüberprüfung für das Administratorfeature

Der folgende Protokollauszug zeigt einige Beispiel Einträge aus der Verwendung des Cmdlets [Get-aipserviceadminlog](/powershell/module/aipservice/get-aipserviceadminlog) . 

In diesem Beispiel bestätigt der Administrator von Contoso Ltd., dass die Administratorfunktion deaktiviert ist, fügt Richard Simone als Administrator hinzu, überprüft, ob Richard der einzige für den Azure Rights Management-Dienst konfigurierte Administrator ist, und aktiviert dann die Administratorfunktion, damit Richard nun einige Dateien entschlüsseln kann, die zuvor von einem Mitarbeiter geschützt wurden, der das Unternehmen mittlerweile verlassen hat.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>Skriptoptionen für Administratoren
Eine Person, die als Administrator für Azure Rights Management fungiert, muss häufig den Schutz von mehreren Dateien an mehreren Speicherorten aufheben. Dies kann zwar manuell erfolgen, es ist jedoch effizienter (und häufig auch zuverlässiger), wenn ein Skript verwendet wird. Verwenden Sie dazu die Cmdlets [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) und [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile). 

Wenn Sie die Klassifizierung und den Schutz verwenden, können Sie auch das Cmdlet [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) nutzen, um eine neue Bezeichnung ohne Schutz anzuwenden, oder die Bezeichnung entfernen, die einen entsprechenden Schutz angewendet hat. 

Weitere Informationen zu diesen Cmdlets finden Sie im Administratorhandbuch für den Azure Information Protection-Client unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md).

> [!NOTE]
> Das azureinformationprotection-Modul unterscheidet sich von und ergänzt das [aipservice-PowerShell-Modul](administer-powershell.md) , das den Azure Rights Management-Dienst für Azure Information Protection verwaltet.

### <a name="guidance-for-using-unprotect-rmsfile-for-ediscovery"></a>Anleitung für die Verwendung von Unprotect-RMSFile für eDiscovery

Obwohl Sie das Cmdlet Unprotect-RMSFile zum Entschlüsseln geschützter Inhalte in PST-Dateien verwenden können, sollten Sie dieses Cmdlet strategisch als Teil des eDiscovery-Prozesses verwenden. Die Ausführung von Unprotect-RMSFile für große Dateien auf einem Computer ist ressourcenintensiv (Arbeitsspeicher und Speicherplatz auf dem Datenträger), und die maximal unterstützte Dateigröße für dieses Cmdlet beträgt 5 GB.

Im Idealfall verwenden Sie [eDiscovery in Microsoft 365](/microsoft-365/compliance/ediscovery) , um geschützte e-Mails und geschützte Anlagen in e-Mails zu suchen und zu extrahieren. Die Administratorfähigkeit ist automatisch in Exchange Online integriert, sodass eDiscovery im Office 365 Security & Compliance Center oder das Microsoft 365 Compliance Center vor dem Export nach verschlüsselten Elementen suchen oder verschlüsselte E-Mails beim Export entschlüsseln kann.

Wenn Sie Microsoft 365 eDiscovery nicht verwenden können, verfügen Sie möglicherweise über eine andere eDiscovery-Lösung, die in den Azure Rights Management-Dienst integriert ist, um die Daten zu überdenken. Wenn Ihre eDiscovery-Lösung geschützte Inhalte nicht automatisch lesen und entschlüsseln kann, können Sie diese Lösung auch weiterhin in einem mehrstufigen Prozess verwenden, mit dem Sie Unprotect-RMSFile effizienter ausführen können:

1. Exportieren Sie die betreffende E-Mail aus Exchange Online oder Exchange Server oder von der Arbeitsstation, auf der der Benutzer seine E-Mail-Nachrichten gespeichert hat, in eine PST-Datei.

2. Importieren Sie die PST-Datei in Ihr eDiscovery-Tool. Da das Tool keine geschützten Inhalte lesen kann, wird davon ausgegangen, dass diese Elemente Fehler generieren.

3. Generieren Sie aus allen Elementen, die das Tool nicht öffnen konnte, eine neue PST-Datei, die dieses Mal nur geschützte Elemente enthält. Diese zweite PST-Datei wird wahrscheinlich wesentlich kleiner als die ursprüngliche PST-Datei sein.

4. Führen Sie Unprotect-RMSFile für diese zweite PST-Datei zum Entschlüsseln der Inhalte dieser deutlich kleineren Datei aus. Importieren Sie aus der Ausgabe die nun entschlüsselte PST-Datei in Ihr Erkennungstool.

Ausführlichere Informationen und Anleitungen zur Durchführung von eDiscovery für Postfächer und PST-Dateien finden Sie im folgenden Blogbeitrag zu [Azure Information Protection und eDiscovery-Prozesse](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-and-eDiscovery-Processes/ba-p/270216).