---
title: "Migrieren von AD RMS-Azure Information Protection – Phase 1"
description: Phase 1 der Migration von AD RMS zu Azure Information Protection deckt die Schritte 1 bis 4 der Migration von AD RMS zu Azure Information Protection ab.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: bbd5cd5be72dfe72f8312f7ee5049dec2e46ac96
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="migration-phase-1---server-side-configuration-for-ad-rms"></a>Migrationsphase 1 – serverseitige Konfiguration für AD RMS

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Verwenden Sie die folgenden Informationen für Phase 1 der Migration von AD RMS zu Azure Information Protection. Diese Verfahren decken die Schritte 1 bis 4 der [Migration von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) ab.


## <a name="step-1-download-the-azure-rights-management-administration-tool"></a>Schritt 1: Herunterladen des Azure Rights Management-Verwaltungstools
Wechseln Sie zum Microsoft Download Center, und laden Sie das [Azure Rights Management-Verwaltungstool](https://go.microsoft.com/fwlink/?LinkId=257721) herunter, welches das Azure Rights Management-Verwaltungsmodul für Windows PowerShell enthält. Azure Rights Management (Azure RMS) ist der Dienst, der den Schutz von Daten für Azure Information Protection bereitstellt.

Installieren Sie das Tool. Anweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

> [!NOTE]
> Wenn Sie dieses Windows PowerShell-Modul bereits heruntergeladen haben, überprüfen Sie anhand des folgenden Befehls, ob Sie Version 2.5.0.0 oder höher verwenden: `(Get-Module aadrm -ListAvailable).Version`

## <a name="step-2-export-configuration-data-from-ad-rms-and-import-it-to-azure-information-protection"></a>Schritt 2. Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure Information Protection
Dieser Schritt ist ein zweistufiger Vorgang:

1.  Exportieren Sie die Konfigurationsdaten aus AD RMS, indem Sie die vertrauenswürdigen Veröffentlichungsdomänen (TPDs) in eine XML-Datei exportieren. Dieser Vorgang ist für alle Migrationen gleich.

2.  Importieren Sie die Konfigurationsdaten in Azure Information Protection. In Abhängigkeit von der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure RMS-Mandantenschlüssel, gibt es verschiedene Vorgehensweisen für diesen Schritt.

### <a name="export-the-configuration-data-from-ad-rms"></a>Exportieren der Konfigurationsdaten aus AD RMS

Führen Sie das folgende Verfahren auf allen AD RMS-Clustern für alle vertrauenswürdigen Veröffentlichungsdomänen aus, die Inhalt für Ihre Organisation geschützt haben. Auf reinen Lizenzierungsclustern müssen Sie es nicht ausführen.

#### <a name="to-export-the-configuration-data-trusted-publishing-domain-information"></a>So exportieren Sie die Konfigurationsdaten (Informationen zu vertrauenswürdigen Veröffentlichungsdomänen)

1.  Melden Sie sich beim AD RMS-Cluster als Benutzer mit AD RMS-Administratorberechtigungen an.

2.  Erweitern Sie in der AD RMS-Verwaltungskonsole (**Active Directory-Rechteverwaltungsdienste**) den Namen des AD RMS-Clusters, erweitern Sie dann die **Vertrauensrichtlinien**, und klicken Sie auf **Vertrauenswürdige Veröffentlichungsdomänen**.

3.  Wählen Sie im Ergebnisbereich die vertrauenswürdige Veröffentlichungsdomäne aus, und klicken Sie dann im Aktionsbereich auf **Vertrauenswürdige Veröffentlichungsdomäne exportieren**.

4.  Gehen Sie im Dialogfeld **Vertrauenswürdige Veröffentlichungsdomäne exportieren** wie folgt vor:

    -   Klicken Sie auf **Speichern unter** , und geben Sie für die Speicherung einen Pfad und einen Dateinamen Ihrer Wahl ein. Stellen Sie sicher, dass Sie **.xml** als Dateinamenerweiterung angeben (diese wird nicht automatisch angefügt).

    -   Geben Sie ein sicheres Kennwort an, und bestätigen Sie es. Merken Sie sich dieses Kennwort, da Sie es später beim Importieren der Konfigurationsdaten in Azure Information Protection benötigen.

    -   Aktivieren Sie das Kontrollkästchen zum Speichern der vertrauenswürdigen Domänendatei in RMS Version 1.0 nicht.

Wenn Sie alle vertrauenswürdigen Veröffentlichungsdomänen exportiert haben, können Sie mit dem Importieren dieser Daten in Azure Information Protection beginnen.

Beachten Sie, dass vertrauenswürdige Veröffentlichungsdomänen die Schlüssel zum Entschlüsseln zuvor geschützter Dateien enthalten. Daher ist es wichtig, dass Sie über die derzeit aktive Domäne hinaus auch sämtliche vertrauenswürdige Veröffentlichungsdomänen exportieren (und später in Azure importieren).

Zum Beispiel verfügen Sie über mehrere vertrauenswürdige Veröffentlichungsdomänen, wenn Sie ein Upgrade Ihrer AD RMS-Server von Kryptografiemodus 1 auf Kryptografiemodus 2 durchgeführt haben. Wenn Sie die vertrauenswürdigen Veröffentlichungsdomänen mit den archivierten Schlüsseln, die den Kryptografiemodus 1 verwendet haben, nicht exportieren und importieren, werden die Benutzer nach Abschluss der Migration keine Inhalte öffnen können, die mit dem Schlüssel für den Kryptografiemodus 1 geschützt wurden.


### <a name="import-the-configuration-data-to-azure-information-protection"></a>Importieren der Konfigurationsdaten in Azure Information Protection
Die genaue Vorgehensweise bei diesem Schritt richtet sich nach der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure Information Protection-Mandantenschlüssel.

Die aktuelle AD RMS-Bereitstellung wird eine der folgenden Konfigurationen für den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) verwenden:

-   Kennwortschutz in der AD RMS-Datenbank. Dies ist die Standardkonfiguration.

-   HSM-Schutz mithilfe eines Thales-Hardwaresicherheitsmoduls (HSM).

-   HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales.

-   Kennwortschutz mithilfe eines externen Kryptografieanbieters.

> [!NOTE]
> Weitere Informationen zur Verwendung von Hardwaresicherheitsmodulen mit AD RMS finden Sie unter [Verwenden von AD RMS mit Hardwaresicherheitsmodulen](http://technet.microsoft.com/library/jj651024.aspx).

Folgende zwei Optionen sind für die Azure Information Protection-Mandantenschlüsseltopologie verfügbar: Ihr Mandantenschlüssel wird von Microsoft (**von Microsoft verwaltet**) oder von Ihnen (**vom Kunden verwaltet**) in Azure Key Vault verwaltet. Das Szenario, bei dem Sie Ihren eigenen Azure Information Protection-Mandantenschlüssel verwalten, wird auch als „Bring Your Own Key“ (BYOK) bezeichnet und erfordert ein Hardwaresicherheitsmodul (HSM) von Thales. Weitere Informationen finden Sie im Artikel [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

> [!IMPORTANT]
> Exchange Online ist derzeit nicht mit BYOK in Azure Information Protection kompatibel. Wenn Sie BYOK nach der Migration verwenden möchten und die Verwendung von Exchange planen, sollten Sie verstehen, wie diese Konfiguration die IRM-Funktionalität für Exchange Online einschränkt. Lesen Sie die Informationen im Abschnitt [BYOK – Preise und Einschränkungen](byok-price-restrictions.md), um die beste Azure Information Protection-Mandantenschlüsseltopologie für Ihre Migration auszuwählen.

Bestimmen Sie anhand der folgende Tabelle, welche Vorgehensweise für Ihre Migration zu verwenden ist. Kombinationen, die nicht aufgeführt sind, werden nicht unterstützt.

|Aktuelle AD RMS-Bereitstellung|Auswählen der Azure Information Protection-Mandantenschlüsseltopologie|Migrationsanweisungen|
|-----------------------------|----------------------------------------|--------------------------|
|Kennwortschutz in der AD RMS-Datenbank|Microsoft-verwaltet|Gehen Sie das Verfahren zur **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dies ist der einfachste Migrationspfad, bei dem Sie nur Ihre Konfigurationsdaten an Azure Information Protection übertragen müssen.|
|HSM-Schutz mithilfe eines Thales nShield-Hardwaresicherheitsmoduls (HSM)|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren zur **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dazu ist das Azure Key Vault-BYOK-Toolset erforderlich, und es müssen drei Verfahren ausgeführt werden, um erst den Schlüssel aus Ihrem lokalen HSM an die Azure Key Vault-HSMs zu übertragen, dann den Azure Rights Management-Dienst für die Verwendung Ihres Mandantenschlüssels zu autorisieren und schließlich Ihre Konfigurationsdaten an Azure Information Protection zu übertragen.|
|Kennwortschutz in der AD RMS-Datenbank|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln** unter dieser Tabelle durch.<br /><br />Dazu ist das Azure Key Vault-BYOK-Toolset erforderlich, und es müssen vier Verfahren ausgeführt werden, um erst den Softwareschlüssel zu extrahieren und in ein lokales HSM zu importieren, dann den Schlüssel aus Ihrem lokalen HSM an die Azure Information Protection-HSMs zu übertragen, die Key Vault-Daten an Azure Information Protection zu übertragen und schließlich Ihre Konfigurationsdaten an Azure Information Protection zu übertragen.|
|HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres HSM, um Anweisungen zur Übertragung Ihres Schlüssels aus diesem HSM in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
|Kennwortschutz mithilfe eines externen Kryptografieanbieters|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres Kryptografieanbieters, um Anweisungen zur Übertragung Ihres Schlüssels in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
Bevor Sie mit diesen Verfahren beginnen, stellen Sie sicher, dass Sie auf die XML-Dateien, die Sie zuvor beim Exportieren der vertrauenswürdigen Veröffentlichungsdomänen erstellt haben, zugreifen können. Diese können z. B. auf einem USB-Stick gespeichert sein, den Sie von Ihrem AD RMS-Server abziehen und an eine Arbeitsstation mit Internetverbindung anschließen.

> [!NOTE]
> Verwenden Sie ungeachtet der Speichermethode bewährte Sicherheitsmethoden zum Schutz dieser Dateien, da diese Daten Ihren privaten Schlüssel enthalten.


Um Schritt 2 auszuführen, wählen Sie die Anweisungen für Ihren Migrationspfad aus: 


- [Softwaregeschützter Schlüssel zu softwaregeschütztem Schlüssel](migrate-softwarekey-to-softwarekey.md)
- [HSM-geschützter Schlüssel zu HSM-geschütztem Schlüssel](migrate-hsmkey-to-hsmkey.md)
- [Softwaregeschützter Schlüssel zu HSM-geschütztem Schlüssel](migrate-softwarekey-to-hsmkey.md)


## <a name="step-3-activate-your-azure-information-protection-tenant"></a>Schritt 3: Aktivieren Ihres Azure Information Protection-Mandanten
Dieser Schritt erfordert die Aktivierung des Azure Rights Management-Diensts. Sämtliche Anweisungen finden Sie im Artikel [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).


> [!TIP]
> Wenn Sie über ein Office 365-Abonnement verfügen, können Sie Azure Rights Management über das Office 365 Admin Center oder das klassische Azure-Portal aktivieren. Die Verwendung des klassischen Azure-Portals wird empfohlen, da Sie den nächsten Schritt in diesem Verwaltungsportal ausführen.

**Was geschieht, wenn Ihr Azure Information Protection-Mandant bereits aktiviert wurde?** Wenn der Azure Rights Management-Dienst für Ihre Organisation bereits aktiviert ist, verwenden Benutzer Azure Information Protection möglicherweise schon, um Inhalte mit einem automatisch generierten Mandantenschlüssel (und den Standardvorlagen) anstelle der vorhandenen Schlüssel (und Vorlagen) von AD RMS zu schützen. Dies ist unwahrscheinlich auf Computern, die in Ihrem Intranet ordnungsgemäß verwaltet werden, da diese automatisch für die AD RMS-Infrastruktur konfiguriert werden. Aber es kann auf dem Arbeitsgruppencomputern oder Computern passieren, die selten mit dem Intranet verbunden sind. Leider ist es auch schwierig, diese Computer zu identifizieren, weshalb wir empfehlen, dass Sie den Dienst nicht vor dem Import der Konfigurationsdaten aus AD RMS aktivieren.

Wenn Ihr Azure Information Protection-Mandant bereits aktiviert ist und Sie diese Computer identifizieren können, stellen Sie sicher, dass Sie das Skript „CleanUpRMS_RUN_Elevated.cmd“ auf diesen Computern wie in Schritt 5 beschrieben ausführen. Durch das Ausführen dieses Skripts erzwingen sie, die Benutzerumgebung erneut zu initialisieren, damit sie den aktualisierten Mandantenschlüssel und die importierten Vorlagen herunterladen.

Falls Sie außerdem benutzerdefinierte Vorlagen erstellt haben, die Sie nach der Migration verwenden möchten, müssen Sie diese zunächst exportieren und wieder importieren. Diese Prozedur wird im nächsten Schritt behandelt. 

## <a name="step-4-configure-imported-templates"></a>Schritt 4: Konfigurieren importierter Vorlagen
Da die importierten Vorlagen den Standardstatus **Archiviert** haben, müssen Sie diesen Status in **Veröffentlicht** ändern, wenn Benutzer in der Lage sein sollen, diese Vorlagen mit dem Azure Rights Management-Dienst zu verwenden.

Vorlagen, die Sie aus AD RMS importieren, sind im Aussehen und Verhalten mit benutzerdefinierten Vorlagen identisch, die Sie im klassischen Azure-Portal erstellen können. Unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md) erfahren Sie, wie Sie die für die Veröffentlichung vorgesehenen importierten Vorlagen so ändern können, dass die Vorlagen für Benutzer in Anwendungen sichtbar sind und ausgewählt werden können.

Abgesehen von der Veröffentlichung der neu importierten Vorlagen müssen Sie vor der Fortsetzung der Migration möglicherweise noch zwei wichtige Änderungen an den Vorlagen vornehmen. Nehmen Sie keine weiteren Änderungen an den importierten Vorlagen vor, um eine konsistentere Benutzererfahrung während der Migration sicherzustellen. Veröffentlichen Sie ebenso wenig die beiden Standardvorlagen, die in Azure Information Protection enthalten sind, und erstellen Sie zu diesem Zeitpunkt keine neuen Vorlagen. Warten Sie stattdessen, bis der Migrationsvorgang abgeschlossen ist und die AD RMS-Server außer Betrieb gesetzt wurden.

Die Änderungen an der Vorlage, die Sie für diesen Schritt möglicherweise vornehmen müssen:

- Wenn Sie vor der Migration benutzerdefinierte Vorlagen in Azure Information Protection erstellt haben, müssen Sie diese manuell exportieren und erneut importieren.

- Wenn Ihre Vorlagen in AD RMS die Gruppe **JEDER** verwendet haben, müssen Sie die entsprechende Gruppe und die Berechtigungen manuell hinzufügen.

## <a name="procedure-if-you-created-custom-templates-before-the-migration"></a>Prozedur, falls Sie benutzerdefinierte Vorlagen vor der Migration erstellt haben

Wenn Sie vor der Migration (entweder vor oder nach der Aktivierung des Azure Rights Management-Diensts) benutzerdefinierte Vorlagen erstellt haben, sind diese nach der Migration nicht für Benutzer verfügbar, selbst wenn sie zuvor auf **Veröffentlicht** festgelegt wurden. Sie müssen folgende Schritte ausführen, um Benutzern die Vorlagen zur Verfügung zu stellen: 

1. Ermitteln Sie, um welche Vorlagen es sich handelt, und notieren Sie sich die Vorlagen-ID durch Ausführen von [Get-AadrmTemplate](https://msdn.microsoft.com/library/dn727079.aspx). 

2. Exportieren Sie die Vorlagen mithilfe des Azure RMS-PowerShell-Cmdlets [Export-AadrmTemplate](https://msdn.microsoft.com/library/dn727078.aspx).

3. Importieren Sie die Vorlagen mithilfe des Azure RMS-PowerShell-Cmdlets [Import-AadrmTemplate](https://msdn.microsoft.com/library/dn727077.aspx).

Sie können diese Vorlagen wie jede andere Vorlage veröffentlichen oder archivieren, die Sie nach der Migration erstellen.


## <a name="procedure-if-your-templates-in-ad-rms-used-the-anyone-group"></a>Prozedur, wenn Ihre Vorlagen in AD RMS die Gruppe **JEDER** verwendet haben

Wenn Ihre Vorlagen in AD RMS die Gruppe **JEDER** verwendet haben, wird diese Gruppe beim Importieren der Vorlagen in Azure Information Protection automatisch entfernt. In diesem Fall müssen Sie den importierten Vorlagen manuell die entsprechende Gruppe oder die entsprechenden Benutzer hinzufügen und dieselben Rechte zuweisen. Die entsprechende Gruppe für Azure Information Protection heißt **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<Mandantenname>.onmicrosoft.com**. Für Contoso kann diese Gruppe folgendermaßen aussehen: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**.

Wenn Sie nicht sicher sind, ob Ihre AD RMS-Vorlagen die Gruppe JEDER enthalten, können Sie diese Vorlagen mithilfe des folgenden Windows PowerShell-Beispielskripts ermitteln. Weitere Informationen zur Verwendung von Windows PowerShell mit AD RMS finden Sie unter [Verwalten von AD RMS mit Windows PowerShell](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Sie können die für Ihre Organisation automatisch erstellte Gruppe sehen, wenn Sie eine der Standardrichtlinienvorlagen für Rechte im klassischen Azure-Portal kopieren und dann auf der Seite **RECHTE** den **BENUTZERNAMEN** identifizieren. Allerdings können Sie diese Gruppe nicht über das klassische Azure-Portal einer Vorlage hinzufügen, die manuell erstellt oder importiert wurde, sondern müssen eine der folgenden Azure RMS PowerShell-Optionen verwenden:

-   Verwenden Sie das PowerShell-Cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) zum Definieren der Gruppe „AllStaff“ und der Rechte als ein Rechtedefinitionsobjekt. Wiederholen Sie diesen Befehl für alle anderen Gruppen oder Benutzer, denen in der ursprünglichen Vorlage zusätzlich zur Gruppe JEDER bereits Rechte gewährt wurden. Fügen Sie anschließend den Vorlagen alle diese Rechtedefinitionsobjekte mithilfe des Cmdlets [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx) hinzu.

-   Exportieren Sie die Vorlage mithilfe des Cmdlets [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) in eine XML-Datei, die Sie so bearbeiten können, dass die Gruppe „AllStaff“ und die Rechte den vorhandenen Gruppen und Berechtigungen hinzugefügt werden. Importieren Sie anschließend diese Änderung über das Cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) in Azure Information Protection zurück.

> [!NOTE]
> Die äquivalente Gruppe "AllStaff" ist nicht exakt mit der Gruppe JEDER in AD RMS identisch: Die Gruppe "AllStaff" enthält alle Benutzer aus Ihrem Azure-Mandanten, während die Gruppe JEDER alle authentifizierten Benutzer enthält, die sich auch außerhalb Ihrer Organisation befinden können.
> 
> Wegen dieses Unterschieds zwischen den beiden Gruppen müssen Sie möglicherweise zusätzlich zur Gruppe „AllStaff“ noch externe Benutzer hinzufügen. Externe E-Mail-Adressen für Gruppen werden derzeit nicht unterstützt.


### <a name="sample-windows-powershell-script-to-identify-ad-rms-templates-that-include-the-anyone-group"></a>Windows PowerShell-Beispielskript zum Bestimmen von AD RMS-Vorlagen, die die Gruppe JEDER enthalten
Dieser Abschnitt enthält das Beispielskript, mit dessen Hilfe Sie AD RMS-Vorlagen bestimmen können, in denen die Gruppe JEDER definiert ist, wie im vorherigen Abschnitt beschrieben.

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
Wechseln Sie zu [Phase 2: Clientseitige Konfiguration](migrate-from-ad-rms-phase2.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
