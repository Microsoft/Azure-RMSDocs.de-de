---
title: Konfigurieren von Administratoren für Azure Rights Management – AIP
description: Verstehen und implementieren Sie die Administratorfunktion des Azure Rights Management-Diensts von Azure Information Protection, sodass autorisierte Personen und Dienste immer lesen und untersuchen können ("fundierte") Ihrer Organisation die geschützten Daten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/02/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: acb4c00b-d3a9-4d74-94fe-91eeb481f7e3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 9aa95d164f0211248a45f2376345608f50bac5f6
ms.sourcegitcommit: f9077101a974459a4252e763b5fafe51ff15a16f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64767873"
---
# <a name="configuring-super-users-for-azure-rights-management-and-discovery-services-or-data-recovery"></a>Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Die Administratorfunktion des Azure Rights Management-Diensts aus Azure Information Protection stellt sicher, dass autorisierte Personen und Dienste immer auf die Daten, die mit Azure Rights Management für Ihre Organisation geschützt werden, zugreifen und diese überprüfen können. Bei Bedarf kann der Schutz anschließend entfernt oder geändert werden.

Ein Administrator verfügt immer über das Rights Management-[Nutzungsrecht](configure-usage-rights.md) zum Vollzugriff auf durch den Azure Information Protection-Mandanten Ihrer Organisation geschützte Dokumente und E-Mails. Diese Fähigkeit wird gelegentlich als „Schlussfolgern über Daten“ (reasoning over data) bezeichnet und ist ein ausschlaggebendes Element dabei, die Kontrolle über die Daten Ihrer Organisation zu behalten. So verwenden Sie diese Funktion beispielsweise für alle der folgenden Szenarien:

- Ein Mitarbeiter verlässt die Organisation, und Sie müssen alle Dateien lesen können, die von dieser Person geschützt wurden.

- Ein IT-Administrator muss die aktuelle Schutzrichtlinie entfernen, die für Dateien konfiguriert wurde, und eine neue Schutzrichtlinie anwenden.

- Exchange Server muss Postfächer für Suchvorgänge indizieren.

- Sie verfügen über IT-Dienste für DLP-Lösungen (Data Loss Prevention, Verhinderung von Datenverlust), über Inhaltsverschlüsselungsgateways (Content Encryption Gateways, CEGs) und Antischadsoftware, die Dateien überprüfen müssen, die bereits geschützt sind.

- Sie müssen massenhaft Dateien entschlüsseln, aus Gründen der Überwachung, rechtlichen oder anderen Compliance-Gründen.

## <a name="configuration-for-the-super-user-feature"></a>Konfiguration für das Administratorfeature

In der Standardeinstellung ist die Administratorfunktion nicht aktiviert, und der Rolle sind keine Benutzer zugewiesen. Sie wird jedoch automatisch aktiviert, wenn Sie den Rights Management-Connector für Exchange konfigurieren; für Standarddienste, die unter Exchange Online, SharePoint Online oder SharePoint Server ausgeführt werden, ist sie nicht erforderlich.

Wenn Sie die Administratorfunktion manuell aktivieren müssen, verwenden Sie das PowerShell-Cmdlet [Enable-AadrmSuperUserFeature](/powershell/aadrm/vlatest/enable-aadrmsuperuserfeature), und ordnen Sie dann mithilfe des Cmdlets [Add-AadrmSuperUser](/powershell/aadrm/vlatest/add-aadrmsuperuser) nach Bedarf Benutzer (oder Dienstkonten) zu, oder verwenden Sie das Cmdlet [Set-AadrmSuperUserGroup](/powershell/aadrm/vlatest/set-aadrmsuperusergroup), und fügen Sie dieser Gruppe die entsprechenden Benutzer (oder andere Gruppen) hinzu. 

Obwohl das Verwenden einer Gruppe für Ihren Administrator einfacher zu verwalten ist, seien Sie sich bewusst, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](prepare.md#group-membership-caching-by-azure-information-protection). Wenn Sie also einen neuen Benutzer als Administrator bestimmen müssen, um Inhalt sofort zu entschlüsseln, fügen Sie diesen Benutzer hinzu, indem Sie Add-AadrmSuperUser benutzen, statt diesen Benutzer einer vorhandenen Gruppe zuzuordnen, die Sie mithilfe von Set-AadrmSuperUserGroup konfiguriert haben.

> [!NOTE]
> Wenn Sie das Windows PowerShell-Modul für Azure Rights Management noch nicht installieren haben, finden Sie Informationen dazu unter [Installieren des PowerShell-Moduls für AADRM](install-powershell.md).

Es spielt keine Rolle, wann Sie das Administratorfeature aktivieren oder wann Sie Benutzer als Administratoren hinzufügen. Wenn Sie beispielsweise das Feature am Donnerstag aktivieren und einen Benutzer am Freitag hinzufügen, kann dieser Benutzer sofort den Inhalt öffnen, der zu Wochenbeginn geschützt wurde.

## <a name="security-best-practices-for-the-super-user-feature"></a>Bewährte Sicherheitsmethoden für das Administratorfeature

- Beschränken und überwachen Sie die Administratoren, die als globale Administratoren für Ihren Office 365- oder Azure Information Protection-Mandanten fungieren oder denen mithilfe des Cmdlets [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/add-aadrmrolebasedadministrator) die Rolle „GlobalAdministrator“ zugewiesen wurde. Diese Benutzer können die Administratorfunktion aktivieren und Benutzer (einschließlich der eigenen Person) als Administratoren festlegen und damit potenziell alle Dateien entschlüsseln, die von Ihrer Organisation geschützt werden.

- Wenn Sie sehen möchten, welche Benutzer und Dienstkonten einzeln als Administratoren zugeordnet sind, verwenden Sie das [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser)-Cmdlet. Wenn Sie feststellen möchten, ob eine Administratorgruppe konfiguriert ist, verwenden Sie das [Get-AadrmSuperUserGroup](/powershell/module/aadrm/get-aadrmsuperusergroup)-Cmdlet und Ihre Standardtools für die Benutzerverwaltung, um zu überprüfen, welche Benutzer zu dieser Gruppe gehören. Wie alle administrativen Vorgänge werden auch das Aktivieren oder Deaktivieren der Administratorfunktion sowie das Hinzufügen oder Entfernen von Administratoren protokolliert und können mithilfe des Befehls [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) überwacht werden. Ein Beispiel finden Sie im nächsten Abschnitt. Wenn Administratoren Dateien entschlüsseln, wird dieser Vorgang ebenfalls protokolliert und kann mit der [Verwendungsprotokollierung](log-analyze-usage.md) überwacht werden.

- Wenn Sie die Administratorfunktion für die alltäglichen Dienste nicht benötigen, sollten Sie diese Funktion nur im Bedarfsfall aktivieren und mit dem Cmdlet [Disable-AadrmSuperUserFeature](/powershell/module/aadrm/disable-aadrmsuperuserfeature) wieder deaktivieren.

### <a name="example-auditing-for-the-super-user-feature"></a>Beispielüberprüfung für das Administratorfeature

Der folgende Protokollauszug zeigt einige Beispieleinträge, die mit dem Cmdlet [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) erstellt wurden. 

In diesem Beispiel bestätigt der Administrator von Contoso Ltd., dass die Administratorfunktion deaktiviert ist, fügt Richard Simone als Administrator hinzu, überprüft, dass Richard der einzige für den Azure Rights Management-Dienst konfigurierte Administrator ist, und aktiviert dann die Administratorfunktion, damit Richard nun einige Dateien entschlüsseln kann, die zuvor von einem Mitarbeiter geschützt wurden, der das Unternehmen mittlerweile verlassen hat.

`2015-08-01T18:58:20    admin@contoso.com   GetSuperUserFeatureState    Passed  Disabled`

`2015-08-01T18:59:44    admin@contoso.com   AddSuperUser -id rsimone@contoso.com    Passed  True`

`2015-08-01T19:00:51    admin@contoso.com   GetSuperUser    Passed  rsimone@contoso.com`

`2015-08-01T19:01:45    admin@contoso.com   SetSuperUserFeatureState -state Enabled Passed  True`

## <a name="scripting-options-for-super-users"></a>Skriptoptionen für Administratoren
Eine Person, die als Administrator für Azure Rights Management fungiert, muss häufig den Schutz von mehreren Dateien an mehreren Speicherorten aufheben. Dies kann zwar manuell erfolgen, es ist jedoch effizienter (und häufig auch zuverlässiger), wenn ein Skript verwendet wird. Verwenden Sie dazu die Cmdlets [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) und [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) gemäß Ihren Anforderungen. 

Wenn Sie die Klassifizierung und den Schutz verwenden, können Sie auch das Cmdlet [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) verwenden, um eine neue Bezeichnung ohne Schutz anzuwenden, oder die Bezeichnung entfernen, die einen entsprechenden Schutz angewendet hat. 

Weitere Informationen zu diesen Cmdlets finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md) im Administratorhandbuch für den Azure Information Protection-Client.

> [!NOTE]
> Das AzureInformationProtection-Modul unterscheidet sich vom [AADRM PowerShell-Modul](administer-powershell.md), das den Azure Rights Management-Dienst für Azure Information Protection verwaltet.

### <a name="guidance-for-using-unprotect-rmsfile-for-ediscovery"></a>Anleitung für die Verwendung von Unprotect-RMSFile für eDiscovery

Obwohl Sie das Cmdlet Unprotect-RMSFile zum Entschlüsseln geschützter Inhalte in PST-Dateien verwenden können, sollten Sie dieses Cmdlet strategisch als Teil des eDiscovery-Prozesses verwenden. Die Ausführung von Unprotect-RMSFile für große Dateien auf einem Computer ist ressourcenintensiv (Arbeitsspeicher und Speicherplatz auf dem Datenträger), und die maximal unterstützte Dateigröße für dieses Cmdlet beträgt 5 GB.

Im Idealfall verwenden Sie [Office 365 eDiscovery](/office365/securitycompliance/ediscovery), um geschützte E-Mails und geschützte Anlagen in E-Mails zu suchen und zu extrahieren. Die Administratorfähigkeit ist automatisch in Exchange Online integriert, sodass eDiscovery im Office 365 Security & Compliance Center oder das Microsoft 365 Compliance Center vor dem Export nach verschlüsselten Elementen suchen oder verschlüsselte E-Mails beim Export entschlüsseln kann.

Wenn Sie Office 365 eDiscovery nicht verwenden können, verfügen Sie möglicherweise über eine andere eDiscovery-Lösung, die in den Azure Rights Management-Dienst integriert werden kann, um ähnlich über Daten zu urteilen. Wenn Ihre eDiscovery-Lösung geschützte Inhalte nicht automatisch lesen und entschlüsseln kann, können Sie diese Lösung auch weiterhin in einem mehrstufigen Prozess verwenden, mit dem Sie Unprotect-RMSFile effizienter ausführen können:

1. Exportieren Sie die betreffende E-Mail aus Exchange Online oder Exchange Server oder von der Arbeitsstation, auf der der Benutzer seine E-Mail-Nachrichten gespeichert hat, in eine PST-Datei.

2. Importieren Sie die PST-Datei in Ihr eDiscovery-Tool. Da das Tool keine geschützten Inhalte lesen kann, wird davon ausgegangen, dass diese Elemente Fehler generieren.

3. Generieren Sie aus allen Elementen, die das Tool nicht öffnen konnte, eine neue PST-Datei, die dieses Mal nur geschützte Elemente enthält. Diese zweite PST-Datei wird wahrscheinlich wesentlich kleiner als die ursprüngliche PST-Datei sein.

4. Führen Sie Unprotect-RMSFile für diese zweite PST-Datei zum Entschlüsseln der Inhalte dieser deutlich kleineren Datei aus. Importieren Sie aus der Ausgabe die nun entschlüsselte PST-Datei in Ihr Erkennungstool.

Ausführlichere Informationen und Anleitungen zur Durchführung von eDiscovery über Postfächer und PST-Dateien hinweg finden Sie im folgenden Blogbeitrag: [Azure Information Protection und eDiscovery-Prozesse](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-and-eDiscovery-Processes/ba-p/270216).

