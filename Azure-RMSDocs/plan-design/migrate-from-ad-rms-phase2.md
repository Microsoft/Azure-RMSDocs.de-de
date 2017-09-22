---
title: "Migrieren von AD RMS-Azure Information Protection – Phase 2"
description: Phase 2 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 4 bis 6 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/19/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3274cb1ddd457647159034b955c47e9ab775f00c
ms.sourcegitcommit: f7ef0f040ae4af4bf1283ebcb0750b65b6939313
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2017
---
# <a name="migration-phase-2---server-side-configuration-for-ad-rms"></a>Migrationsphase 2: serverseitige Konfiguration für AD RMS

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Verwenden Sie die folgenden Informationen für Phase 2 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 4 bis 6 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.


## <a name="step-4-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection"></a>Schritt 4: Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure Information Protection
Dieser Schritt ist ein zweistufiger Vorgang:

1. Exportieren Sie die Konfigurationsdaten aus AD RMS, indem Sie die vertrauenswürdigen Veröffentlichungsdomänen (TPDs) in eine XML-Datei exportieren. Dieser Vorgang ist für alle Migrationen gleich.

2. Importieren Sie die Konfigurationsdaten in Azure Information Protection. In Abhängigkeit von der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure RMS-Mandantenschlüssel, gibt es verschiedene Vorgehensweisen für diesen Schritt.

### <a name="export-the-configuration-data-from-ad-rms"></a>Exportieren der Konfigurationsdaten aus AD RMS

Führen Sie das folgende Verfahren auf allen AD RMS-Clustern für alle vertrauenswürdigen Veröffentlichungsdomänen aus, die Inhalt für Ihre Organisation geschützt haben. Auf reinen Lizenzierungsclustern müssen Sie diese Prozedur nicht ausführen.

#### <a name="to-export-the-configuration-data-trusted-publishing-domain-information"></a>So exportieren Sie die Konfigurationsdaten (Informationen zu vertrauenswürdigen Veröffentlichungsdomänen)

1. Melden Sie sich beim AD RMS-Cluster als Benutzer mit AD RMS-Administratorberechtigungen an.

2. Erweitern Sie in der AD RMS-Verwaltungskonsole (**Active Directory-Rechteverwaltungsdienste**) den Namen des AD RMS-Clusters, erweitern Sie dann die **Vertrauensrichtlinien**, und klicken Sie auf **Vertrauenswürdige Veröffentlichungsdomänen**.

3. Wählen Sie im Ergebnisbereich die vertrauenswürdige Veröffentlichungsdomäne aus, und klicken Sie dann im Aktionsbereich auf **Vertrauenswürdige Veröffentlichungsdomäne exportieren**.

4. Gehen Sie im Dialogfeld **Vertrauenswürdige Veröffentlichungsdomäne exportieren** wie folgt vor:

    - Klicken Sie auf **Speichern unter** , und geben Sie für die Speicherung einen Pfad und einen Dateinamen Ihrer Wahl ein. Stellen Sie sicher, dass Sie **.xml** als Dateinamenerweiterung angeben (diese wird nicht automatisch angefügt).

    - Geben Sie ein sicheres Kennwort an, und bestätigen Sie es. Merken Sie sich dieses Kennwort, da Sie es später beim Importieren der Konfigurationsdaten in Azure Information Protection benötigen.

    - Aktivieren Sie das Kontrollkästchen zum Speichern der vertrauenswürdigen Domänendatei in RMS Version 1.0 nicht.

Wenn Sie alle vertrauenswürdigen Veröffentlichungsdomänen exportiert haben, können Sie mit dem Importieren dieser Daten in Azure Information Protection beginnen.

Beachten Sie, dass die vertrauenswürdigen Veröffentlichungsdomänen die SLC-Schlüssel (Server Licensor Certificate) zum Entschlüsseln zuvor geschützter Dateien enthalten. Daher ist es wichtig, dass Sie über die derzeit aktive Domäne hinaus auch sämtliche vertrauenswürdigen Veröffentlichungsdomänen exportieren (und später in Azure importieren).

Zum Beispiel verfügen Sie über mehrere vertrauenswürdige Veröffentlichungsdomänen, wenn Sie ein Upgrade Ihrer AD RMS-Server von Kryptografiemodus 1 auf Kryptografiemodus 2 durchgeführt haben. Wenn Sie die vertrauenswürdigen Veröffentlichungsdomänen mit den archivierten Schlüsseln, die den Kryptografiemodus 1 verwendet haben, nicht exportieren und importieren, werden die Benutzer nach Abschluss der Migration keine Inhalte öffnen können, die mit dem Schlüssel für den Kryptografiemodus 1 geschützt wurden.


### <a name="import-the-configuration-data-to-azure-information-protection"></a>Importieren der Konfigurationsdaten in Azure Information Protection
Die genaue Vorgehensweise bei diesem Schritt richtet sich nach der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure Information Protection-Mandantenschlüssel.

Die aktuelle AD RMS-Bereitstellung verwendet eine der folgenden Konfigurationen für den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC):

- Kennwortschutz in der AD RMS-Datenbank. Dies ist die Standardkonfiguration.

- HSM-Schutz mithilfe eines Thales-Hardwaresicherheitsmoduls (HSM).

- HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales.

- Kennwortschutz mithilfe eines externen Kryptografieanbieters.

> [!NOTE]
> Weitere Informationen zur Verwendung von Hardwaresicherheitsmodulen mit AD RMS finden Sie unter [Verwenden von AD RMS mit Hardwaresicherheitsmodulen](http://technet.microsoft.com/library/jj651024.aspx).

Folgende zwei Optionen sind für die Azure Information Protection-Mandantenschlüsseltopologie verfügbar: Ihr Mandantenschlüssel wird von Microsoft (**von Microsoft verwaltet**) oder von Ihnen (**vom Kunden verwaltet**) in Azure Key Vault verwaltet. Das Szenario, bei dem Sie Ihren eigenen Azure Information Protection-Mandantenschlüssel verwalten, wird auch als „Bring Your Own Key“ (BYOK) bezeichnet und erfordert ein Hardwaresicherheitsmodul (HSM) von Thales. Weitere Informationen finden Sie im Artikel [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

> [!IMPORTANT]
> Exchange Online ist derzeit nicht mit BYOK in Azure Information Protection kompatibel. Wenn Sie BYOK nach der Migration verwenden möchten und die Verwendung von Exchange planen, sollten Sie verstehen, wie diese Konfiguration die IRM-Funktionalität für Exchange Online einschränkt. Lesen Sie die Informationen im Abschnitt [BYOK – Preise und Einschränkungen](byok-price-restrictions.md), um die beste Azure Information Protection-Mandantenschlüsseltopologie für Ihre Migration auszuwählen.

Bestimmen Sie anhand der folgende Tabelle, welche Vorgehensweise für Ihre Migration zu verwenden ist. 

|Aktuelle AD RMS-Bereitstellung|Auswählen der Azure Information Protection-Mandantenschlüsseltopologie|Migrationsanweisungen|
|-----------------------------|----------------------------------------|--------------------------|
|Kennwortschutz in der AD RMS-Datenbank|Microsoft-verwaltet|Gehen Sie das Verfahren zur **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dies ist der einfachste Migrationspfad, bei dem Sie nur Ihre Konfigurationsdaten an Azure Information Protection übertragen müssen.|
|HSM-Schutz mithilfe eines Thales nShield-Hardwaresicherheitsmoduls (HSM) |Kundenverwaltet (BYOK)|Gehen Sie das Verfahren zur **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dazu ist das Azure Key Vault-BYOK-Toolset erforderlich, und es müssen drei Verfahren ausgeführt werden, um erst den Schlüssel aus Ihrem lokalen HSM an die Azure Key Vault-HSMs zu übertragen, dann den Azure Rights Management-Dienst für die Verwendung Ihres Mandantenschlüssels zu autorisieren und schließlich Ihre Konfigurationsdaten an Azure Information Protection zu übertragen.|
|Kennwortschutz in der AD RMS-Datenbank|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln** unter dieser Tabelle durch.<br /><br />Dazu ist das Azure Key Vault-BYOK-Toolset erforderlich, und es müssen vier Verfahren ausgeführt werden, um erst den Softwareschlüssel zu extrahieren und in ein lokales HSM zu importieren, dann den Schlüssel aus Ihrem lokalen HSM an die Azure Information Protection-HSMs zu übertragen, die Key Vault-Daten an Azure Information Protection zu übertragen und schließlich Ihre Konfigurationsdaten an Azure Information Protection zu übertragen.|
|HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales |Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres HSM, um Anweisungen zur Übertragung Ihres Schlüssels aus diesem HSM in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
|Kennwortschutz mithilfe eines externen Kryptografieanbieters|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres Kryptografieanbieters, um Anweisungen zur Übertragung Ihres Schlüssels in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|

Wenn Sie einen HSM-geschützten Schlüssel haben, den Sie nicht exportieren können, können Sie immer noch zu Azure Information Protection migrieren, indem Sie Ihren AD RMS-Cluster für einen schreibgeschützten Modus konfigurieren. In diesem Modus kann zuvor geschützter Inhalt zwar geöffnet werden, jedoch verwendet neu geschützter Inhalt einen neuen Mandantenschlüssel, der von Ihnen (BYOK) oder von Microsoft verwaltet wird. Weitere Informationen finden Sie unter [An update is available for Office to support migrations from AD RMS to Azure RMS (Ein Update ist für Office verfügbar, um Migrationen von AD RMS auf Azure RMS zu unterstützen)](https://support.microsoft.com/help/4023955/an-update-is-available-for-office-to-support-migrations-from-ad-rms-to).

Bevor Sie mit diesen Schlüssel-Migrationsverfahren beginnen, stellen Sie sicher, dass Sie auf die XML-Dateien, die Sie zuvor beim Exportieren der vertrauenswürdigen Veröffentlichungsdomänen erstellt haben, zugreifen können. Diese können z. B. auf einem USB-Stick gespeichert sein, den Sie von Ihrem AD RMS-Server abziehen und an eine Arbeitsstation mit Internetverbindung anschließen.

> [!NOTE]
> Verwenden Sie ungeachtet der Speichermethode bewährte Sicherheitsmethoden zum Schutz dieser Dateien, da diese Daten Ihren privaten Schlüssel enthalten.

Um Schritt 4 auszuführen, wählen Sie die Anweisungen für Ihren Migrationspfad aus: 

- [Softwaregeschützter Schlüssel zu softwaregeschütztem Schlüssel](migrate-softwarekey-to-softwarekey.md)
- [HSM-geschützter Schlüssel zu HSM-geschütztem Schlüssel](migrate-hsmkey-to-hsmkey.md)
- [Softwaregeschützter Schlüssel zu HSM-geschütztem Schlüssel](migrate-softwarekey-to-hsmkey.md)

## <a name="step-5-activate-the-azure-rights-management-service"></a>Schritt 5: Aktivieren des Azure Rights Management-Diensts

Öffnen Sie eine PowerShell-Sitzung, und führen Sie die folgenden Befehle aus.

1. Stellen Sie eine Verbindung mit dem Azure Rights Management-Dienst her, und geben Sie Ihre globalen Administratoranmeldeinformationen an, wenn Sie dazu aufgefordert werden:
    
        Connect-Aadrmservice

2. Aktivieren des Azure Rights Management-Diensts:
    
        Enable-Aadrm

**Was geschieht, wenn Ihr Azure Information Protection-Mandant bereits aktiviert wurde?** Wenn der Azure Rights Management-Dienst für Ihre Organisation bereits aktiviert ist, verwenden Benutzer Azure Information Protection möglicherweise schon, um Inhalte mit einem automatisch generierten Mandantenschlüssel (und den Standardvorlagen) anstelle der vorhandenen Schlüssel (und Vorlagen) von AD RMS zu schützen. Dies ist unwahrscheinlich auf Computern, die in Ihrem Intranet ordnungsgemäß verwaltet werden, da diese automatisch für die AD RMS-Infrastruktur konfiguriert sind. Aber es kann auf dem Arbeitsgruppencomputern oder Computern passieren, die selten mit dem Intranet verbunden sind. Leider ist es auch schwierig, diese Computer zu identifizieren, weshalb wir empfehlen, dass Sie den Dienst nicht vor dem Import der Konfigurationsdaten aus AD RMS aktivieren.

Wenn Ihr Azure Information Protection-Mandant bereits aktiviert ist und Sie diese Computer identifizieren können, stellen Sie sicher, dass Sie das Skript „CleanUpRMS.cmd“ auf diesen Computern wie in [Schritt 7](migrate-from-ad-rms-phase3.md#step-7-reconfigure-clients-to-use-azure-information-protection) beschrieben ausführen. Durch das Ausführen dieses Skripts erzwingen sie, die Benutzerumgebung erneut zu initialisieren, damit sie den aktualisierten Mandantenschlüssel und die importierten Vorlagen herunterladen.

Falls Sie außerdem benutzerdefinierte Vorlagen erstellt haben, die Sie nach der Migration verwenden möchten, müssen Sie diese Vorlagen zunächst exportieren und wieder importieren. Diese Prozedur wird im nächsten Schritt behandelt. 

## <a name="step-6-configure-imported-templates"></a>Schritt 6: Konfigurieren importierter Vorlagen

Da die importierten Vorlagen den Standardstatus **Archiviert** haben, müssen Sie diesen Status in **Veröffentlicht** ändern, wenn Benutzer in der Lage sein sollen, diese Vorlagen mit dem Azure Rights Management-Dienst zu verwenden.

Vorlagen, die Sie aus AD RMS importieren, sind im Aussehen und Verhalten mit benutzerdefinierten Vorlagen identisch, die Sie im Azure-Portal erstellen können. Unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](../deploy-use/configure-policy-templates.md) erfahren Sie, wie Sie importierte Vorlagen, die veröffentlicht werden sollen, so ändern können, dass die Vorlagen für Benutzer in Anwendungen sicht- und auswählbar sind.

Abgesehen von der Veröffentlichung der neu importierten Vorlagen müssen Sie vor der Fortsetzung der Migration möglicherweise noch zwei wichtige Änderungen an den Vorlagen vornehmen. Nehmen Sie keine weiteren Änderungen an den importierten Vorlagen vor, um eine konsistentere Benutzererfahrung während der Migration sicherzustellen. Veröffentlichen Sie ebenso wenig die beiden Standardvorlagen, die in Azure Information Protection enthalten sind, und erstellen Sie zu diesem Zeitpunkt keine neuen Vorlagen. Warten Sie stattdessen, bis der Migrationsvorgang abgeschlossen ist und die Bereitstellung der AD RMS-Server aufgehoben wurden.

Die Änderungen an der Vorlage, die Sie für diesen Schritt möglicherweise vornehmen müssen:

- Wenn Sie vor der Migration benutzerdefinierte Vorlagen in Azure Information Protection erstellt haben, müssen Sie diese manuell exportieren und erneut importieren.

- Wenn Ihre Vorlagen in AD RMS die Gruppe **Jeder** verwendet haben, müssen Sie möglicherweise Benutzer oder Gruppen von außerhalb Ihrer Organisation hinzufügen. 
    
    In AD RMS hat die Gruppe „Jeder“ allen authentifizierten Benutzern Rechte gewährt. Diese Gruppe wird automatisch in alle Benutzer in Ihrem Azure AD-Mandanten konvertiert. Wenn Sie nicht noch zusätzlichen Benutzern Rechte gewähren müssen, ist keine weitere Aktion erforderlich. Wenn Sie jedoch die Gruppe „Jeder“ verwendet haben, um externe Benutzer einzuschließen, müssen Sie diese Benutzer sowie die Rechte, die Sie diesen gewähren möchten, manuell hinzufügen.

### <a name="procedure-if-you-created-custom-templates-before-the-migration"></a>Prozedur, falls Sie benutzerdefinierte Vorlagen vor der Migration erstellt haben

Wenn Sie vor der Migration (entweder vor oder nach der Aktivierung des Azure Rights Management-Diensts) benutzerdefinierte Vorlagen erstellt haben, sind diese nach der Migration nicht für Benutzer verfügbar, selbst wenn sie zuvor auf **Veröffentlicht** festgelegt wurden. Sie müssen folgende Schritte ausführen, um Benutzern die Vorlagen zur Verfügung zu stellen: 

1. Ermitteln Sie, um welche Vorlagen es sich handelt, und notieren Sie sich die Vorlagen-ID durch Ausführen von [Get-AadrmTemplate](/powershell/aadrm/vlatest/get-aadrmtemplate). 

2. Exportieren Sie die Vorlagen mithilfe des Azure RMS-PowerShell-Cmdlets [Export-AadrmTemplate](/powershell/aadrm/vlatest/export-aadrmtemplate).

3. Importieren Sie die Vorlagen mithilfe des Azure RMS-PowerShell-Cmdlets [Import-AadrmTemplate](/powershell/aadrm/vlatest/Import-AadrmTpd).

Sie können diese Vorlagen wie jede andere Vorlage veröffentlichen oder archivieren, die Sie nach der Migration erstellen.

### <a name="procedure-if-your-templates-in-ad-rms-used-the-anyone-group"></a>Prozedur, wenn Ihre Vorlagen in AD RMS die Gruppe **JEDER** verwendet haben

Wenn Ihre Vorlagen in AD RMS die Gruppe **Jeder** verwendet haben, wird diese Gruppe automatisch in die Gruppe mit dem Namen **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@\<tenant_name>.onmicrosoft.com** konvertiert. Für Contoso kann diese Gruppe folgendermaßen aussehen: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**. Diese Gruppe enthält alle Benutzer aus Ihrem Azure AD-Mandanten.

Bei der Verwaltung von Vorlagen und Bezeichnungen im Azure-Portal wird diese Gruppe als Domänenname Ihres Mandanten in Azure AD angezeigt. Für Contoso kann diese Gruppe beispielsweise wie folgt aussehen: **contoso.onmicrosoft.com**. Um diese Gruppe hinzuzufügen, zeigt die Option **\<Name der Organisation> – Alle Mitglieder hinzufügen** an.

Wenn Sie nicht sicher sind, ob Ihre AD RMS-Vorlagen die Gruppe JEDER enthalten, können Sie diese Vorlagen mithilfe des folgenden Windows PowerShell-Beispielskripts ermitteln. Weitere Informationen zur Verwendung von Windows PowerShell mit AD RMS finden Sie unter [Using Windows PowerShell to Administer AD RMS (Verwalten von AD RMS mit Windows PowerShell)](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Sie können externe Benutzer problemlos zu Vorlagen hinzufügen, wenn Sie diese Vorlagen im Azure-Portal in Bezeichnungen konvertieren. Klicken Sie anschließend auf dem Blatt **Berechtigungen hinzufügen** auf **Enter Details** (Details eingeben), um die E-Mail-Adressen für diese Benutzer manuell anzugeben. 

Weitere Informationen zu dieser Konfiguration finden Sie unter [Konfigurieren einer Bezeichnung für Rights Management-Schutz](../deploy-use/configure-policy-protection.md).

#### <a name="sample-windows-powershell-script-to-identify-ad-rms-templates-that-include-the-anyone-group"></a>Windows PowerShell-Beispielskript zum Bestimmen von AD RMS-Vorlagen, die die Gruppe JEDER enthalten
Dieser Abschnitt enthält das Beispielskript, mit dessen Hilfe Sie AD RMS-Vorlagen, in denen die Gruppe „Jeder“ definiert ist, wie im vorherigen Abschnitt beschrieben bestimmen können.

**Haftungsausschluss**: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Dieses Beispielskript wird OHNE jede Gewährleistung bereitgestellt.

```
import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id

                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright

     $templateName=$Template.DefaultDisplayName 

        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline

                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
```


## <a name="next-steps"></a>Nächste Schritte
Wechseln Sie zu [Phase 3: Clientseitige Konfiguration](migrate-from-ad-rms-phase2.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]