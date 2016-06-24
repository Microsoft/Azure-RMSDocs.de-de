---
# required metadata

title: Migration von AD RMS zu Azure Rights Management – Phase 1 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 5a189695-40a6-4b36-afe6-0823c94993ef

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Migrationsphase 1 – serverseitige Konfiguration für AD RMS

*Gilt für: Active Directory Rights Management Services, Azure Rights Management*

Verwenden Sie die folgende Informationen für Phase 1 der Migration von AD RMS zu Azure Rights Management (Azure RMS). Diese Verfahren beziehen sich auf die Schritte 1 bis 4 der [Migration von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Schritt 1: Herunterladen des Azure Rights Management-Verwaltungstools
Wechseln Sie zum Microsoft Download Center und [laden Sie das Azure Rights Management-Verwaltungstool herunter](http://go.microsoft.com/fwlink/?LinkId=257721), das das Azure RMS-Verwaltungsmodul für Windows PowerShell enthält.

Installieren Sie das Tool. Anweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

## Schritt 2. Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS
Dieser Schritt ist ein zweistufiger Vorgang:

1.  Exportieren Sie die Konfigurationsdaten aus AD RMS, indem Sie die vertrauenswürdigen Veröffentlichungsdomänen (TPDs) in eine XML-Datei exportieren. Dieser Vorgang ist für alle Migrationen gleich.

2.  Importieren Sie die Konfigurationsdaten in Azure RMS. In Abhängigkeit von der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure RMS-Mandantenschlüssel, gibt es verschiedene Vorgehensweisen für diesen Schritt.

### Exportieren der Konfigurationsdaten aus AD RMS
Führen Sie das folgende Verfahren auf allen AD RMS-Clustern für alle vertrauenswürdigen Veröffentlichungsdomänen aus, die Inhalt für Ihre Organisation geschützt haben. Auf reinen Lizenzierungsclustern müssen Sie es nicht ausführen.

> [!NOTE] Wenn Sie Windows Server 2003 Rights Management nutzen, befolgen Sie anstelle dieser Anweisungen das Verfahren [Export SLC, TUD, TPD and RMS private key](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) (Exportieren von SLC, TUD, TPD und dem privaten RMS-Schlüssel) im Artikel [Migrating from Windows RMS to AD RMS in a Different Infrastructure](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) (Migration von Windows RMS auf AD RMS in einer anderen Infrastruktur).

#### So exportieren Sie die Konfigurationsdaten (Informationen zu vertrauenswürdigen Veröffentlichungsdomänen)

1.  Melden Sie sich beim AD RMS-Cluster als Benutzer mit AD RMS-Administratorberechtigungen an.

2.  Erweitern Sie in der AD RMS-Verwaltungskonsole (**Active Directory-Rechteverwaltungsdienste**) den Namen des AD RMS-Clusters, erweitern Sie dann die **Vertrauensrichtlinien**, und klicken Sie auf **Vertrauenswürdige Veröffentlichungsdomänen**.

3.  Wählen Sie im Ergebnisbereich die vertrauenswürdige Veröffentlichungsdomäne aus, und klicken Sie dann im Aktionsbereich auf **Vertrauenswürdige Veröffentlichungsdomäne exportieren**.

4.  Gehen Sie im Dialogfeld **Vertrauenswürdige Veröffentlichungsdomäne exportieren** wie folgt vor:

    -   Klicken Sie auf **Speichern unter** , und geben Sie für die Speicherung einen Pfad und einen Dateinamen Ihrer Wahl ein. Stellen Sie sicher, dass Sie **.xml** als Dateinamenerweiterung angeben (diese wird nicht automatisch angefügt).

    -   Geben Sie ein sicheres Kennwort an, und bestätigen Sie es. Merken Sie sich dieses Kennwort, da Sie es später beim Importieren der Konfigurationsdaten in Azure RMS benötigen.

    -   Aktivieren Sie das Kontrollkästchen zum Speichern der vertrauenswürdigen Domänendatei in RMS Version 1.0 nicht.

Wenn Sie alle vertrauenswürdigen Veröffentlichungsdomänen exportiert haben, können Sie mit dem Importieren dieser Daten in das Azure RMS-Hardwaresicherheitsmodul (HSM) von Thales beginnen. Weitere Informationen 

### Importieren der Konfigurationsdaten in Azure RMS
Die genaue Vorgehensweise bei diesem Schritt richtet sich nach der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure RMS-Mandantenschlüssel.

Die aktuelle AD RMS-Bereitstellung wird eine der folgenden Konfigurationen für den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) verwenden:

-   Kennwortschutz in der AD RMS-Datenbank. Dies ist die Standardkonfiguration.

-   HSM-Schutz mithilfe eines Thales-Hardwaresicherheitsmoduls (HSM).

-   HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales.

-   Kennwortschutz mithilfe eines externen Kryptografieanbieters.

> [!NOTE] Weitere Informationen zur Verwendung von Hardwaresicherheitsmodulen mit AD RMS finden Sie unter [Verwenden von AD RMS mit Hardwaresicherheitsmodulen](http://technet.microsoft.com/library/jj651024.aspx).

Folgende zwei Optionen sind für die Azure RMS-Mandantenschlüsseltopologie verfügbar: Ihr Mandantenschlüssel wird von Microsoft (**von Microsoft verwaltet**) oder von Ihnen (**vom Kunden verwaltet**) verwaltet. Ein Szenario, in dem Sie Ihren eigenen Azure RMS-Mandantenschlüssel verwalten, wird auch als "Bring Your Own Key" (BYOK) bezeichnet und erfordert ein Hardwaresicherheitsmodul (HSM) von Thales. Weitere Informationen finden Sie im Artikel [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md).

> [!IMPORTANT]
> Exchange Online ist derzeit nicht mit Azure RMS BYOK kompatibel.  Wenn Sie BYOK nach der Migration verwenden möchten und die Verwendung von Exchange planen, sollten Sie verstehen, wie diese Konfiguration die IRM-Funktionalität für Exchange Online einschränkt. Gehen Sie die Informationen im Abschnitt [BYOK – Preise und Einschränkungen](byok-price-restrictions.md) durch, um die beste Azure RMS-Mandantenschlüsseltopologie für Ihre Migration zu wählen.

Bestimmen Sie anhand der folgende Tabelle, welche Vorgehensweise für Ihre Migration zu verwenden ist. Kombinationen, die nicht aufgeführt sind, werden nicht unterstützt.

|Aktuelle AD RMS-Bereitstellung|Gewählte Azure RMS-Mandantenschlüsseltopologie|Migrationsanweisungen|
|-----------------------------|----------------------------------------|--------------------------|
|Kennwortschutz in der AD RMS-Datenbank|Microsoft-verwaltet|Gehen Sie das Verfahren zur **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dies ist der einfachste Migrationspfad, bei dem Sie nur Ihre Konfigurationsdaten an Azure RMS übertragen müssen.|
|HSM-Schutz mithilfe eines Thales nShield-Hardwaresicherheitsmoduls (HSM)|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren zur **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dies erfordert das BYOK-Toolset, und es müssen zwei Gruppen von Schritten ausgeführt werden, um erst den Schlüssel aus Ihrem lokalen HSM an die Azure RMS-HSMs zu übertragen und dann Ihre Konfigurationsdaten an Azure RMS zu übertragen.|
|Kennwortschutz in der AD RMS-Datenbank|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren **Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln** unter dieser Tabelle durch.<br /><br />Dies erfordert das BYOK-Toolset, und es müssen drei Gruppen von Schritten ausgeführt werden, um erst den Softwareschlüssel zu extrahieren und in ein lokales HSM zu importieren, dann den Schlüssel aus Ihrem lokalen HSM an die Azure RMS-HSMs zu übertragen und schließlich Ihre Konfigurationsdaten an Azure RMS zu übertragen.|
|HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres HSM, um Anweisungen zur Übertragung Ihres Schlüssels aus diesem HSM in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
|Kennwortschutz mithilfe eines externen Kryptografieanbieters|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres Kryptografieanbieters, um Anweisungen zur Übertragung Ihres Schlüssels in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
Bevor Sie mit diesen Verfahren beginnen, stellen Sie sicher, dass Sie auf die XML-Dateien, die Sie zuvor beim Exportieren der vertrauenswürdigen Veröffentlichungsdomänen erstellt haben, zugreifen können. Diese können z. B. auf einem USB-Stick gespeichert sein, den Sie von Ihrem AD RMS-Server abziehen und an eine Arbeitsstation mit Internetverbindung anschließen.

> [!NOTE] Verwenden Sie ungeachtet der Speichermethode bewährte Sicherheitsmethoden zum Schutz dieser Dateien, da diese Daten Ihren privaten Schlüssel enthalten.


Um Schritt 2 auszuführen, wählen Sie die Anweisungen für Ihren Migrationspfad aus: 


- [Softwareschlüssel zu Softwareschlüssel](migrate-softwarekey-to-softwarekey.md)
- [HSM-Schlüssel zu HSM-Schlüssel](migrate-hsmkey-to-hsmkey.md)
- [Softwareschlüssel zu HSM-Schlüssel](migrate-softwarekey-to-hsmkey.md)


## Schritt 3: Aktivieren des RMS-Mandanten
Sämtliche Anweisungen zu diesem Schritt finden Sie im Artikel [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).


> [!TIP]
> Wenn Sie über ein Office 365-Abonnement verfügen, können Sie Azure RMS über das Office 365 Admin Center oder das klassische Azure-Portal aktivieren. Die Verwendung des klassischen Azure-Portals wird empfohlen, da Sie den nächsten Schritt in diesem Verwaltungsportal ausführen.

**Was geschieht, wenn Ihr Azure RMS-Mandant bereits aktiviert wurde?** Wenn der Azure RMS-Dienst für Ihre Organisation bereits aktiviert ist, verwenden Benutzer Azure RMS möglicherweise schon, um Inhalte mit einem automatisch generierten Mandantenschlüssel (und den Standardvorlagen) anstelle der vorhandenen Schlüssel (und Vorlagen) von AD RMS zu schützen. Dies ist unwahrscheinlich auf Computern, die in Ihrem Intranet ordnungsgemäß verwaltet werden, da diese automatisch für die AD RMS-Infrastruktur konfiguriert werden. Aber es kann auf dem Arbeitsgruppencomputern oder Computern passieren, die selten mit dem Intranet verbunden sind. Leider ist es auch schwierig, diese Computer zu identifizieren, weshalb wir empfehlen, dass Sie den Dienst nicht vor dem Import der Konfigurationsdaten aus AD RMS aktivieren.

Wenn Ihr Azure RMS-Mandant bereits aktiviert ist und Sie diese Computer identifizieren können, stellen Sie sicher, dass Sie das Skript "CleanUpRMS_RUN_Elevated.cmd" auf diesen Computern wie in Schritt 5 beschrieben ausführen. Durch das Ausführen dieses Skripts erzwingen sie, die Benutzerumgebung erneut zu initialisieren, damit sie den aktualisierten Mandantenschlüssel und die importierten Vorlagen herunterladen.

## Schritt 4: Konfigurieren importierter Vorlagen
Da die importierten Vorlagen den Standardstatus **Archiviert**haben, müssen Sie diesen Status in **Veröffentlicht** ändern, wenn Benutzer in der Lage sein sollen, diese Vorlagen mit Azure RMS zu verwenden.

Wenn für Ihre Vorlagen in AD RMS die Gruppe **JEDER** verwendet wurde, wird diese Gruppe beim Importieren der Vorlagen in Azure RMS automatisch entfernt. In diesem Fall müssen Sie den importierten Vorlagen manuell die äquivalente Gruppe oder äquivalente Benutzer und dieselben Rechte hinzufügen. Die entsprechende Gruppe für Azure RMS heißt **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<Mandantenname>.onmicrosoft.com**. Diese Gruppe kann beispielsweise für Contoso wie folgt aussehen: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**.

Wenn Sie nicht sicher sind, ob Ihre AD RMS-Vorlagen die Gruppe JEDER enthalten, können Sie diese Vorlagen mithilfe des Windows PowerShell-Beispielskripts ermitteln. Weitere Informationen zur Verwendung von Windows PowerShell mit AD RMS finden Sie unter [Verwalten von AD RMS mit Windows PowerShell](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Sie können die für Ihre Organisation automatisch erstellte Gruppe sehen, wenn Sie eine der Standardrichtlinienvorlagen für Rechte im klassischen Azure-Portal kopieren und dann auf der Seite **RECHTE** den **BENUTZERNAMEN** identifizieren. Allerdings können Sie diese Gruppe nicht über das klassische Azure-Portal einer Vorlage hinzufügen, die manuell erstellt oder importiert wurde, sondern müssen eine der folgenden Azure RMS PowerShell-Optionen verwenden:

-   Verwenden Sie das PowerShell-Cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) zum Definieren der Gruppe "AllStaff" und der Rechte als ein Rechtedefinitionsobjekt. Wiederholen Sie diesen Befehl für alle anderen Gruppen oder Benutzer, denen in der ursprünglichen Vorlage zusätzlich zur Gruppe JEDER bereits Rechte gewährt wurden. Fügen Sie anschließend alle diese Rechtedefinitionsobjekte den Vorlagen mithilfe des Cmdlets [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) hinzu.

-   Exportieren Sie die Vorlage mithilfe des Cmdlets [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) in eine XML-Datei, die Sie so bearbeiten können, dass die Gruppe "AllStaff" und die Rechte den vorhandenen Gruppen und Berechtigungen hinzugefügt werden. Importieren Sie anschließend diese Änderung über das Cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) in Azure RMS zurück.

> [!NOTE] Die äquivalente Gruppe „AllStaff“ ist nicht exakt mit der Gruppe ANYONE in AD RMS identisch: Die Gruppe „AllStaff“ enthält alle Benutzer aus Ihrem Azure-Mandanten, während die Gruppe ANYONE alle authentifizierten Benutzer enthält, die sich auch außerhalb Ihrer Organisation befinden können.
> 
> Wegen dieses Unterschieds zwischen den beiden Gruppen müssen Sie möglicherweise zusätzlich zur Gruppe „AllStaff“ noch externe Benutzer hinzufügen. Externe E-Mail-Adressen für Gruppen werden derzeit nicht unterstützt.

Vorlagen, die Sie aus AD RMS importieren, sind im Aussehen und Verhalten mit benutzerdefinierten Vorlagen identisch, die Sie im klassischen Azure-Portal erstellen können. Wenn Sie importierte Vorlagen ändern möchten, sodass sie veröffentlicht werden und Benutzer diese sehen und in Anwendungen auswählen können, oder wenn Sie andere Änderungen an den Vorlagen vornehmen möchten, informieren Sie sich unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).

> [!TIP]
> Damit eine konsistente Umgebung für Benutzer während der Migration gewahrt bleibt, sollten Sie an den importierten Vorlagen außer diesen beiden Änderungen keine weiteren vornehmen. Veröffentlichen Sie auch nicht die beiden Standardvorlagen, die in Azure RMS enthalten sind, und erstellen Sie keine neuen Vorlagen zu diesem Zeitpunkt. Warten Sie stattdessen, bis der Migrationsvorgang abgeschlossen ist und die AD RMS-Server außer Betrieb gesetzt wurden.

### Windows PowerShell-Beispielskript zum Bestimmen von AD RMS-Vorlagen, die die Gruppe JEDER enthalten
Dieser Abschnitt enthält das Beispielskript, mit dessen Hilfe Sie AD RMS-Vorlagen bestimmen können, in denen die Gruppe JEDER definiert ist, wie im vorherigen Abschnitt beschrieben.

**Haftungsausschluss**: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Dieses Beispielskript wird OHNE jede Gewährleistung bereitgestellt.*

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


## Nächste Schritte
Wechseln Sie zu [Phase 2: Clientseitige Konfiguration](migrate-from-ad-rms-phase2.md).



<!--HONumber=May16_HO3-->


