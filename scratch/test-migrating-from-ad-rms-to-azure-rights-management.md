---
title: TEST: Migration von AD RMS zu Azure Rights Management
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TEST
author: Cabailey
---
# ZUVOR: Migration von AD RMS zu Azure Rights Management
Befolgen Sie die folgenden Anweisungen, um Ihre AD RMS-Bereitstellung (Active Directory Rights Management Services) zu Azure Rights Management (Azure RMS) zu migrieren. Nach der Migration haben Benutzer weiter Zugriff auf Dokumente und E-Mail-Nachrichten, die Ihre Organisation mithilfe von AD RMS geschützt hat. Für neue zu schützende Inhalte wird Azure RMS verwendet.

Nicht sicher, ob diese Migration von AD RMS für Ihre Organisation geeignet ist?

-   Eine Einführung in Azure RMS, die geschäftlichen Probleme, die damit gelöst werden können, die Benutzeroberfläche für Administratoren und Benutzer sowie die Funktionsweise werden unter [Was ist Azure Rights Management?](what-is-azure-rms.md) vorgestellt.

-   Einen Vergleich von Azure RMS mit AD RMS finden Sie unter [Vergleich zwischen Azure Rights Management und AD RMS](compare-azure-rms-ad-rms.md).

## Voraussetzungen für die Migration von AD RMS zu Azure RMS
Stellen Sie vor der Migration zu Azure RMS sicher, dass die folgenden Voraussetzungen erfüllt sind und Sie alle etwaigen Einschränkungen kennen.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Unterstützte RMS-Bereitstellung|Alle AD RMS-Versionen von Windows Server 2008 bis Windows Server 2012 R2 unterstützen die Migration zu Azure RMS:<br /><br />Windows Server 2008 (x86 oder x64)<br /><br />Windows Server 2008 R2 (x64)<br /><br />Windows Server 2012 (x64)<br /><br />Windows Server 2012 R2 (x64)<br /><br />Alle gültigen AD RMS-Topologien werden unterstützt:<br /><br />Einzelne Gesamtstruktur, einzelner RMS-Cluster<br /><br />Einzelne Gesamtstruktur, mehrere reine RMS-Lizenzierungscluster<br /><br />Mehrere Gesamtstrukturen, mehrere RMS-Cluster<br /><br />**Hinweis**: Mehrere RMS-Cluster werden standardmäßig zu einem einzelnen Azure RMS-Mandanten migriert. Wenn Sie weitere RMS-Mandanten wünschen, müssen Sie sie als weitere Migrationen behandeln. Ein Schlüssel von einem RMS-Cluster kann nur in einen einzigen Azure RMS-Mandanten importiert werden.|
|Alle Anforderungen zum Ausführen von Azure RMS, einschließlich eines Azure RMS-Mandanten (nicht aktiviert)|Informationen finden Sie unter [Voraussetzungen für Azure Rights Management](requirements-azure-rms.md).<br /><br />Obwohl Sie einen Azure RMS-Mandanten benötigen, damit Sie von AD RMS aus migrieren können, empfehlen wir, dass die den Rights Management-Dienst nicht vor der Migration aktivieren. Sie führen diesen Schritt während der Migration aus, nachdem Sie die Schlüssel und Vorlagen aus AD RMS exportiert und in Azure RMS importiert haben. Wenn Azure RMS jedoch schon aktiviert wurde, können Sie immer noch von AD RMS migrieren.|
|Vorbereitung für Azure RMS:<br /><br />Verzeichnissynchronisierung zwischen Ihrem lokalen Verzeichnis und Azure Active Directory<br /><br />E-Mail-aktivierte Gruppen in Azure Active Directory|Informationen finden Sie unter [Vorbereiten für Azure Rights Management](prepare.md).|
|Wenn Sie die IRM-Funktionalität (Information Rights Management) von Exchange Server (zum Beispiel Transportregeln und Outlook Web Access) oder SharePoint Server mit AD RMS verwendet haben:<br /><br />Planen Sie einen kurzen Zeitraum ein, in dem IRM nicht auf diesen Servern zur Verfügung steht.|Nach der Migration können Sie IRM weiterhin auf diesen Servern mit Azure RMS verwenden. Allerdings wird in einem der Migrationsschritte der IRM-Dienst vorübergehend deaktiviert, um einen Verbindungsdienst zu installieren und zu konfigurieren und die Server neu zu konfigurieren. Danach wird IRM wieder aktiviert.<br /><br />Dies ist die einzige Dienstunterbrechung während der Migration.|
Einschränkungen:

-   Obwohl der Migrationsvorgang die Migration des Schlüssels Ihres lizenzgebenden Serverzertifikats (SLC) zu einem Hardwaresicherheitsmodul (HSM) für Azure RMS unterstützt, wird diese Konfiguration derzeit von Exchange Online nicht unterstützt. Wenn Sie die vollständige IRM-Funktionalität mit Exchange Online nutzen möchten, nachdem Sie zu Azure RMS migriert haben, muss Ihr Azure RMS-Mandantenschlüssel [von Microsoft verwaltet](http://technet.microsoft.com/library/dn440580.aspx) werden. Alternativ können Sie IRM mit eingeschränkter Funktionalität in Exchange Online ausführen, wenn Ihr Azure RMS-Mandant von Ihnen verwaltet wird (BYOK). Weitere Informationen zur Verwendung von Exchange Online mit Azure RMS finden Sie unter [Schritt 6. Konfigurieren der IRM-Integration mit Exchange Online](#BKMK_Step6Migration) in diesen Anweisungen.

-   Falls Sie Software und Clients besitzen, die nicht in Azure RMS unterstützt werden, können diese den durch Azure RMS geschützten Inhalt nicht schützen oder nutzen. Überprüfen Sie unbedingt den Abschnitt zu den unterstützten Anwendungen und Clients im Thema [Anforderungen für Azure Rights Management](requirements-azure-rms.md).

-   Wenn Sie Ihren lokalen Schlüssel in Azure RMS als archiviert importieren (indem Sie die vertrauenswürdige Veröffentlichungsdomäne während des Importvorgangs nicht als aktiv festlegen) und Benutzer in einer phasenweisen Migration in Batches migrieren, sind neu von den migrierten Benutzern geschützte Inhalte nicht für Benutzer verfügbar, die in AD RMS bleiben. Halten Sie in diesem Szenario die Migrationszeit möglichst kurz, und migrieren Sie Benutzer in logischen Gruppen, d. h. wenn Benutzer zusammen arbeiten, sollten sie gemeinsam migriert werden.

    Diese Einschränkung gilt nicht, wenn Sie die vertrauenswürdige Veröffentlichungsdomäne während des Importvorgangs auf aktiv festlegen, da alle Benutzer Inhalte mit dem gleichen Schlüssel schützen werden. Diese Konfiguration wird empfohlen, da sie alle Benutzer unabhängig voneinander und in Ihrem eigenen Tempo migrieren können.

-   Wenn Sie mit externen Partnern zusammenarbeiten (z. B. mithilfe von vertrauenswürdigen Benutzerdomänen oder Verbund), müssen diese ebenfalls auf Azure RMS migrieren, entweder zur gleichen Zeit wie Sie oder so bald wie möglich danach. Damit der Zugriff auf Inhalte, die Ihre Organisation zuvor mit AD RMS geschützt hat, weiterhin möglich ist, müssen Ihre Partner ähnliche Änderungen an der Clientkonfiguration wie Sie vornehmen (in diesem Dokument erläutert).

    Aufgrund der möglichen Konfigurationsvarianten Ihrer Partner können in diesem Dokument keine genauen Anweisungen für diese Neukonfiguration gegeben werden. Wenn Sie Hilfe benötigen, wenden Sie sich an Microsoft Customer Support Services (CSS).

## Schritte zum Migrieren von AD RMS zu Azure RMS

|Migrationsschritte|Weitere Informationen|
|------------------|--------------------|
|**1. Herunterladen der Azure RMS-Verwaltungstools**|Anweisungen finden Sie unter [Schritt 1: Herunterladen des Azure Rights Management-Verwaltungstools](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step1Migration).|
|**2. Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS**|Sie exportieren die Konfigurationsdaten (Schlüssel, Vorlagen, URLs) aus AD RMS in eine XML-Datei und laden dann diese Datei mithilfe des Windows PowerShell-Cmdlets "Import-AadrmTPD" in Azure RMS hoch. Je nach AD RMS-Schlüsselkonfiguration sind möglicherweise weitere Schritte erforderlich:<br /><br />**Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln**: Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem von Microsoft verwalteten Azure RMS-Mandantenschlüssel. Dies ist der einfachste Migrationspfad, bei dem keine weiteren Schritte erforderlich sind.<br /><br />**Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln**: Schlüssel, die für AD RMS in einem vom Kunden verwalteten Azure RMS-Mandantenschlüssel gespeichert werden (das „Bring Your Own Key“- oder BYOK-Szenario). Hier sind zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM an das Azure RMS-HSM erforderlich. Ihre vorhandenen HSM-geschützten Schlüssel müssen modulgeschützt sein. OCS-geschützte Schlüssel werden vom BYOK-Toolset nicht unterstützt.<br /><br />**Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln**: Zentral verwaltete, kennwortbasierte Schlüssel in AD RMS zu einem kundenverwalteten Azure RMS-Mandantenschlüssel (das „Bring Your Own Key“- oder BYOK-Szenario). Dieses Szenario erfordert die meisten Konfigurationsschritte, da Sie zunächst den Softwareschlüssel extrahieren und in ein lokales HSM importieren und dann zusätzliche Schritte zum Übertragen des Schlüssels aus Ihrem lokalen Thales-HSM in das Azure RMS-HSM ausführen müssen.<br /><br />Anweisungen finden Sie unter [Schritt 2. Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step2Migration).|
|**3. Aktivieren des RMS-Mandanten**|Falls möglich, führen Sie diesen Schritt nach dem Importvorgang und nicht davor aus.<br /><br />Weitere Informationen und Anweisungen hierzu finden Sie unter [Schritt 3. Aktivieren des RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).|
|**4. Konfigurieren importierter Vorlagen**|Wenn Sie Ihre Vorlagen für Benutzerrechterichtlinien importieren, lautet deren Status "Archiviert". Falls Benutzer in der Lage sein sollen, diese anzuzeigen und zu verwenden, müssen Sie den Vorlagenstatus im klassischen Azure-Portal in „Veröffentlicht“ ändern.<br /><br />Anweisungen finden Sie unter [Schritt 4. Konfigurieren importierter Vorlagen](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step4Migration).|
|**5. Neukonfigurieren von Clients zur Verwendung von Azure RMS**|Vorhandene Windows-Computer müssen neu konfiguriert werden, um den Azure RMS-Dienst anstelle von AD RMS zu verwenden. Dieser Schritt gilt für Computer in Ihrer Organisation und für Computer in Partnerorganisationen, wenn Sie mit diesen zusammengearbeitet haben, während AS RMS ausgeführt wurde.<br /><br />Außerdem müssen Sie, wenn Sie die [Erweiterungen für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx) zur Unterstützung mobiler Geräte wie iOS-Telefone und iPads, Android-Telefone und Tablets, Windows Phone und Mac-Computer bereitgestellt haben, die SRV-Einträge im DNS entfernen, die diese Clients zum Verwenden von AD RMS umgeleitet haben.<br /><br />Anweisungen finden Sie unter [Schritt 5. Neukonfigurieren von Clients zur Verwendung von Azure RMS](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step5Migration).|
|**6. Konfigurieren der IRM-Integration mit Exchange Online**|Dieser Schritt ist erforderlich, wenn Sie Exchange Online mit Azure RMS verwenden möchten.<br /><br />Anweisungen finden Sie unter [Schritt 6. Konfigurieren der IRM-Integration mit Exchange Online](#BKMK_Step6Migration).|
|**7. Bereitstellen des RMS-Connectors**|Dieser Schritt ist erforderlich, wenn Sie einen der folgenden lokalen Dienste mit Azure RMS verwenden möchten:<br /><br />Exchange Server (z. B. Transportregeln und Outlook Web Access)<br /><br />SharePoint Server<br /><br />Windows Server mit Dateiklassifizierungsinfrastruktur<br /><br />Anweisungen finden Sie unter [Schritt 7. Bereitstellen des RMS-Verbindungsdiensts](#BKMK_Step7Migration).|
|**8. Außerbetriebsetzung von AD RMS**|Wenn sichergestellt ist, dass alle Clients Azure RMS verwenden und nicht mehr auf die AD RMS-Server zugreifen, können Sie Ihre AD RMS-Bereitstellung außer Betrieb setzen.<br /><br />Anweisungen finden Sie unter [Schritt 8. Außerbetriebsetzung von AD RMS](#BKMK_Step8Migration).|
|**9. Ändern des Azure RMS-Mandantenschlüssels**|Dieser Schritt ist erforderlich, wenn Sie den Kryptografiemodus 2 vor der Migration nicht ausgeführt haben, und wird für alle anderen Migrationen als optionaler Schritt empfohlen, um die Sicherheit Ihres Azure RMS-Mandantenschlüssels zu gewährleisten.<br /><br />Anweisungen finden Sie unter [Schritt 9. Ändern des Azure RMS-Mandantenschlüssels](#BKMK_Step9Migration).|

### <a name="BKMK_Step1Migration"></a>Schritt 1: Herunterladen des Azure Rights Management-Verwaltungstools
Wechseln Sie zum Microsoft Download Center und [laden Sie das Azure Rights Management-Verwaltungstool herunter](http://go.microsoft.com/fwlink/?LinkId=257721), das das Azure RMS-Verwaltungsmodul für Windows PowerShell enthält.

### <a name="BKMK_Step2Migration"></a>Schritt 2. Exportieren der Konfigurationsdaten aus AD RMS und Importieren dieser Daten in Azure RMS
Dieser Schritt ist ein zweistufiger Vorgang:

1.  Exportieren Sie die Konfigurationsdaten aus AD RMS, indem Sie die vertrauenswürdigen Veröffentlichungsdomänen (TPDs) in eine XML-Datei exportieren. Dieser Vorgang ist für alle Migrationen gleich.

2.  Importieren Sie die Konfigurationsdaten in Azure RMS. In Abhängigkeit von der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure RMS-Mandantenschlüssel, gibt es verschiedene Vorgehensweisen für diesen Schritt.

#### Exportieren der Konfigurationsdaten aus AD RMS
Führen Sie das folgende Verfahren auf allen AD RMS-Clustern für alle vertrauenswürdigen Veröffentlichungsdomänen aus, die Inhalt für Ihre Organisation geschützt haben. Auf reinen Lizenzierungsclustern müssen Sie es nicht ausführen.

> [!NOTE]
> Wenn Sie Windows Server 2003 Rights Management nutzen, befolgen Sie anstelle dieser Anweisungen dem Verfahren [Exportieren von SLC, TUD, TPD und privatem RMS-Schlüssel](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) aus dem Thema [Migration von Windows RMS auf AD RMS in einer anderen Infrastruktur](http://technet.microsoft.com/library/jj835767%28v=ws.10%29.aspx) .

###### So exportieren Sie die Konfigurationsdaten (Informationen zu vertrauenswürdigen Veröffentlichungsdomänen)

1.  Melden Sie sich beim AD RMS-Cluster als Benutzer mit AD RMS-Administratorberechtigungen an.

2.  Erweitern Sie in der AD RMS-Verwaltungskonsole (**Active Directory-Rechteverwaltungsdienste**) den Namen des AD RMS-Clusters, erweitern Sie dann die **Vertrauensrichtlinien**, und klicken Sie auf **Vertrauenswürdige Veröffentlichungsdomänen**.

3.  Wählen Sie im Ergebnisbereich die vertrauenswürdige Veröffentlichungsdomäne aus, und klicken Sie dann im Aktionsbereich auf **Vertrauenswürdige Veröffentlichungsdomäne exportieren**.

4.  Gehen Sie im Dialogfeld **Vertrauenswürdige Veröffentlichungsdomäne exportieren** wie folgt vor:

    -   Klicken Sie auf **Speichern unter** , und geben Sie für die Speicherung einen Pfad und einen Dateinamen Ihrer Wahl ein. Stellen Sie sicher, dass Sie **.xml** als Dateinamenerweiterung angeben (diese wird nicht automatisch angefügt).

    -   Geben Sie ein sicheres Kennwort an, und bestätigen Sie es. Merken Sie sich dieses Kennwort, da Sie es später beim Importieren der Konfigurationsdaten in Azure RMS benötigen.

    -   Aktivieren Sie das Kontrollkästchen zum Speichern der vertrauenswürdigen Domänendatei in RMS Version 1.0 nicht.

Wenn Sie alle vertrauenswürdigen Veröffentlichungsdomänen exportiert haben, können Sie mit dem Importieren dieser Daten in Azure RMS beginnen.

#### Importieren der Konfigurationsdaten in Azure RMS
Die genaue Vorgehensweise bei diesem Schritt richtet sich nach der aktuellen Konfiguration Ihrer AD RMS-Bereitstellung und Ihrer bevorzugten Topologie für Ihren Azure RMS-Mandantenschlüssel.

Die aktuelle AD RMS-Bereitstellung wird eine der folgenden Konfigurationen für den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) verwenden:

-   Kennwortschutz in der AD RMS-Datenbank. Dies ist die Standardkonfiguration.

-   HSM-Schutz mithilfe eines Thales-Hardwaresicherheitsmoduls (HSM).

-   HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales.

-   Kennwortschutz mithilfe eines externen Kryptografieanbieters.

> [!NOTE]
> Weitere Informationen zur Verwendung von Hardwaresicherheitsmodulen mit AD RMS finden Sie unter [Verwenden von AD RMS mit Hardwaresicherheitsmodulen](http://technet.microsoft.com/library/jj651024.aspx).

Folgende zwei Optionen sind für die Azure RMS-Mandantenschlüsseltopologie verfügbar: Ihr Mandantenschlüssel wird von Microsoft (**von Microsoft verwaltet**) oder von Ihnen (**vom Kunden verwaltet**) verwaltet. Ein Szenario, in dem Sie Ihren eigenen Azure RMS-Mandantenschlüssel verwalten, wird auch als "Bring Your Own Key" (BYOK) bezeichnet und erfordert ein Hardwaresicherheitsmodul (HSM) von Thales. Weitere Informationen finden Sie im Abschnitt [Wählen Sie Ihre Mandantenschlüsseltopologie aus: Verwaltet von Microsoft (Standard) oder verwaltet von Ihnen (BYOK)](plan-implement-tenant-key.md#BKMK_ChooseTenantKey) unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md).

> [!IMPORTANT]
> Exchange Online ist derzeit nicht mit Azure RMS BYOK kompatibel.  Wenn Sie BYOK nach der Migration verwenden möchten und die Verwendung von Exchange planen, sollten Sie verstehen, wie diese Konfiguration die IRM-Funktionalität für Exchange Online einschränkt. Überprüfen Sie die Informationen im Abschnitt [BYOK – Preise und Einschränkungen](plan-implement-tenant-key.md#BKMK_Pricing) im Thema [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md), um die beste Azure RMS-Mandantenschlüsseltopologie für Ihre Migration auszuwählen.

Bestimmen Sie anhand der folgende Tabelle, welche Vorgehensweise für Ihre Migration zu verwenden ist. Kombinationen, die nicht aufgeführt sind, werden nicht unterstützt.

|Aktuelle AD RMS-Bereitstellung|Gewählte Azure RMS-Mandantenschlüsseltopologie|Migrationsanweisungen|
|-----------------------------|----------------------------------------|--------------------------|
|Kennwortschutz in der AD RMS-Datenbank|Microsoft-verwaltet|Gehen Sie das Verfahren **Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln** hinter dieser Tabelle durch.<br /><br />Dies ist der einfachste Migrationspfad, bei dem Sie nur Ihre Konfigurationsdaten an Azure RMS übertragen müssen.|
|HSM-Schutz mithilfe eines Thales nShield-Hardwaresicherheitsmoduls (HSM)|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dies erfordert das BYOK-Toolset, und es müssen zwei Gruppen von Schritten ausgeführt werden, um erst den Schlüssel aus Ihrem lokalen HSM an die Azure RMS-HSMs zu übertragen und dann Ihre Konfigurationsdaten an Azure RMS zu übertragen.|
|Kennwortschutz in der AD RMS-Datenbank|Kundenverwaltet (BYOK)|Gehen Sie das Verfahren**Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.<br /><br />Dies erfordert das BYOK-Toolset, und es müssen drei Gruppen von Schritten ausgeführt werden, um erst den Softwareschlüssel zu extrahieren und in ein lokales HSM zu importieren, dann den Schlüssel aus Ihrem lokalen HSM an die Azure RMS-HSMs zu übertragen und schließlich Ihre Konfigurationsdaten an Azure RMS zu übertragen.|
|HSM-Schutz mithilfe eines Hardwaresicherheitsmoduls (HSM) von einem anderen Lieferanten als Thales|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres HSM, um Anweisungen zur Übertragung Ihres Schlüssels aus diesem HSM in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
|Kennwortschutz mithilfe eines externen Kryptografieanbieters|Kundenverwaltet (BYOK)|Wenden Sie sich an den Lieferanten Ihres Kryptografieanbieters, um Anweisungen zur Übertragung Ihres Schlüssels in ein Thales nShield-Hardwaresicherheitsmodul (HSM) zu erhalten. Gehen Sie anschließend die Anweisungen für das Verfahren **Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln** unterhalb dieser Tabelle durch.|
Bevor Sie mit diesen Verfahren beginnen, stellen Sie sicher, dass Sie auf die XML-Dateien, die Sie zuvor beim Exportieren der vertrauenswürdigen Veröffentlichungsdomänen erstellt haben, zugreifen können. Diese können z. B. auf einem USB-Stick gespeichert sein, den Sie von Ihrem AD RMS-Server abziehen und an eine Arbeitsstation mit Internetverbindung anschließen.

> [!NOTE]
> Verwenden Sie ungeachtet der Speichermethode bewährte Sicherheitsmethoden zum Schutz dieser Dateien, da diese Daten Ihren privaten Schlüssel enthalten.

##### Migration softwaregeschützter Schlüssel zu softwaregeschützten Schlüsseln
Verwenden Sie dieses Verfahren zum Importieren der AD RMS-Konfiguration in Azure RMS, um Ihren Azure RMS-Mandantenschlüssel zu erhalten, der von Microsoft verwaltet wird.

###### So importieren Sie die Konfigurationsdaten in Azure RMS

1.  Laden Sie auf einer Arbeitsstation mit Internetverbindung das Windows PowerShell-Modul für Azure RMS (Mindestversion 2.1.0.0) herunter, das das [Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx)-Cmdlet enthält, und installieren Sie es.

    > [!TIP]
    > Wenn Sie das Modul bereits heruntergeladen und installiert haben, überprüfen Sie die Versionsnummer, indem Sie Folgendes ausführen: `(Get-Module aadrm -ListAvailable).Version`

    Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

2.  Starten Sie Windows PowerShell mit der Option **Als Administrator ausführen** , und stellen Sie mit dem Cmdlet [Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) eine Verbindung mit dem Azure RMS-Dienst her:

    ```
    Connect-AadrmService
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Administratoranmeldeinformationen des [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Mandanten ein (in der Regel verwenden Sie das Konto eines globalen Administrators für Azure Active Directory oder Office 365).

3.  Laden Sie mit dem [Import-AadrmTdp](http://msdn.microsoft.com/library/azure/dn857523.aspx)-Cmdlet die erste exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -Active $True -Verbose
    ```
    Beispiel: **Import-AadrmTpd -TpdFile E:\contosokey1.xml –ProtectionPassword –Active $true -Verbose**

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

4.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 3 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Für diese Dateien legen Sie aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen. Beispiel: **Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose**

5.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 3 fortfahren. Aktivieren des RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).

##### Migration HSM-geschützter Schlüssel zu HSM-geschützten Schlüsseln

> [!NOTE]
> Für diese Anweisungen wird angenommen, dass Ihr AD RMS-Schlüssel modulgeschützt ist. Dies ist der Normalfall. Wenn Ihr AD RMS-Schlüssel mit OCS geschützt ist, wenden Sie sich an [AskIPTeam@microsoft.com](mailto: askipteam@microsoft.com?subject=AD%20RMS%20migration%20with%20OCS-protected%20key), bevor Sie diese Anweisungen verwenden.

Das Verfahren zum Importieren des HSM-Schlüssels und der AD RMS-Konfiguration in Azure RMS, um den von Ihnen verwalteten Azure RMS-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in zwei Phasen.

Sie müssen zuerst Ihren HSM-Schlüssel verpacken, damit er an Azure RMS übertragen werden kann, und ihn dann mit den Konfigurationsdaten importieren.

###### Teil 1: Verpacken Ihres HSM-Schlüssel, damit er an Azure RMS übertragen werden kann

1.  Führen Sie die Schritte im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md) mithilfe der Prozedur **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet** mit den folgenden Ausnahmen aus:

    -   Führen Sie nicht die Schritten zum **Generieren Ihres Mandantenschlüssels**aus, da Sie bereits über das Äquivalent aus Ihrer AD RMS-Bereitstellung verfügen. Sie müssen den vom AD RMS-Server verwendeten Schlüssel aus der Thales-Installation bestimmen und diesen Schlüssel während der Migration verwenden. Verschlüsselte Thales-Schlüsseldateien weisen meist einen Namen nach dem Muster **Schlüssel_(Schlüsselanwendungsname)_(Schlüsselbezeichner)** auf dem lokalen Server auf.

    -   Führen Sie nicht die Schritte zum **Übertragen Ihres Mandantenschlüssels an Azure RMS** aus, da hier der Befehl „Add-AadrmKey“ verwendet wird.  Stattdessen übertragen Sie Ihren vorbereiteten HSM-Schlüssel beim Hochladen der exportierten vertrauenswürdigen Veröffentlichungsdomäne mithilfe des Befehls „Import-AadrmTpd“.

2.  Stellen Sie auf der Arbeitsstation mit Internetzugang in der Windows PowerShell-Sitzung erneut eine Verbindung mit dem Azure RMS-Dienst her.

Nun, da Sie Ihren HSM-Schlüssel für Azure RMS vorbereitet haben, können Sie die HSM-Schlüsseldatei und die AD RMS-Konfigurationsdaten importieren.

###### Teil 2: Importieren des HSM-Schlüssels und der Konfigurationsdaten in Azure RMS

1.  Laden Sie auf der mit dem Internet verbundenen Arbeitsstation und in der Windows PowerShell-Sitzung die erste exportierte XML-Datei mit einer vertrauenswürdigen Veröffentlichungsdomäne hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToBYOKPackage> -Active $True -Verbose
    ```
    Beispiel: **Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose**

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

2.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 1 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Für diese Dateien legen Sie aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen.  Beispiel: **Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose**

3.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 3 fortfahren. Aktivieren des RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).

##### Migration softwaregeschützter Schlüssel zu HSM-geschützten Schlüsseln
Das Verfahren zum Importieren der AD RMS-Konfiguration in Azure RMS, um den von Ihnen verwalteten Azure RMS-Mandantenschlüssel (BYOK) zu erhalten, gliedert sich in drei Phasen.

Sie müssen zuerst den Schlüssel Ihres lizenzgebenden Serverzertifikats (SLC) aus den Konfigurationsdaten extrahieren und an ein lokales Thales-HSM übertragen, dann Ihren HSM-Schlüssel verpacken und an Azure RMS übertragen und schließlich die Konfigurationsdaten importieren.

###### Teil 1: Extrahieren des SLC aus den Konfigurationsdaten und Importieren des Schlüssels in das lokale HSM

1.  Verwenden Sie die folgenden Schritte im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) im Thema [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md):

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Vorbereiten Ihrer Arbeitsstation mit Internetverbindung**

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Vorbereiten Ihrer nicht verbundenen Arbeitsstation**

    Führen Sie die Schritte zum Generieren Ihres Mandantenschlüssels nicht aus, da Sie bereits über das Äquivalent in der XML-Datei mit den exportierten Konfigurationsdaten verfügen. Führen Sie stattdessen einen Befehl zum Extrahieren dieses Schlüssels aus der Datei und Importieren des Schlüssels in das lokale HSM aus.

2.  Führen Sie auf der nicht verbundenen Arbeitsstation den folgenden Befehl aus:

    ```
    KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath <TPD> -ProtectionPassword -KeyIdentifier <KeyID> -ExchangeKeyPackage <BYOK-KEK-pka-Region> -NewSecurityWorldPackage <BYOK-SecurityWorld-pkg-Region>
    ```
    Beispiel für Nordamerika: **KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;**

    Zusätzliche Informationen:

    -   Der Parameter "ImportRmsCentrallyManagedKey" gibt an, dass es sich um den Vorgang zum Importieren des SLC-Schlüssels handelt.

    -   Wenn Sie das Kennwort im Befehl nicht angeben, werden Sie zur Angabe aufgefordert.

    -   Der Parameter "KeyIdentifier" ist für einen Schlüsselanzeigenamen da, der den Schlüsseldateinamen erstellt. Sie dürfen nur kleingeschriebene ASCII-Zeichen verwenden.

    -   Der Parameter "ExchangeKeyPackage" gibt ein regionsspezifisches KEK-Paket (Paket mit Schlüsselaustauschschlüssel) an, dessen Name mit BYOK-KEK-pkg- beginnt.

    -   Der Parameter "NewSecurityWorldPackage" gibt ein regionsspezifisches Security World-Paket an, dessen Name mit BYOK-SecurityWorld-pkg- beginnt.

    Mit diesem Befehl ergibt sich Folgendes:

    -   Eine HSM-Schlüsseldatei: %NFAST_KMDATA%\local\key_mscapi_&lt;Schlüssel-ID&gt;

    -   RMS-Konfigurationsdatendatei mit entferntem SLC: %NFAST_KMDATA%\local\no_key_tpd_&lt;Schlüssel-ID&gt;.xml

3.  Wenn mehrere RMS-Konfigurationsdatendateien vorliegen, wiederholen Sie Schritt 2 für die restlichen Dateien.

Nachdem Ihr SLC nun extrahiert wurde, sodass Sie über einen HSM-basierten Schlüssel verfügen, können Sie ihn verpacken und an Azure RMS übertragen.

###### Teil 2: Verpacken des HSM-Schlüssels und Übertragen des Schlüssels an Azure RMS

1.  Verwenden Sie die folgenden Schritte im Abschnitt [Implementierung von"Bring Your Own Key" (BYOK)](plan-implement-tenant-key.md#BKMK_ImplementBYOK) im Thema [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md):

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Vorbereiten Ihres Mandantenschlüssels für die Übertragung**

    -   **Generieren und Übertragen Ihres Mandantenschlüssels – über das Internet**: **Übertragen Ihres Mandantenschlüssels an Azure RMS**

Nachdem Sie nun Ihren HSM-Schlüssel an Azure RMS übertragen haben, können Sie Ihre AD RMS-Konfigurationsdaten importieren, die nur einen Zeiger auf den gerade übertragenen Mandantenschlüssel enthalten.

###### Teil 3: Importieren der Konfigurationsdaten in Azure RMS

1.  Kopieren Sie auf der Arbeitsstation mit Internetverbindung und in der Windows PowerShell-Sitzung die RMS-Konfigurationsdateien mit entferntem SLC (aus der nicht verbundenen Arbeitsstation, (%NFAST_KMDATA%\local\no_key_tpd_<Schlüssel-ID>.xml).

2.  Laden Sie die erste Datei hoch. Wenn Sie mehr als eine XML-Datei haben, weil Sie mehrere vertrauenswürdige Veröffentlichungsdomänen hatten, wählen Sie die Datei aus, die die exportierte vertrauenswürdige Veröffentlichungsdomäne enthält, die dem HSM-Schlüssel entspricht, den Sie in Azure RMS verwenden möchten, um Inhalte nach der Migration zu schützen. Verwenden Sie den folgenden Befehl:

    ```
    Import-AadrmTpd -TpdFile <PathToNoKeyTpdPackageFile> -ProtectionPassword -HsmKeyFile <PathToKeyTransferPackage> -Active $true -Verbose
    ```
    Beispiel: **Import -TpdFile E:\no_key_tpd_contosorms1key.xml –ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok –Active $true -Verbose**

    Geben Sie bei entsprechender Aufforderung das Kennwort ein, das Sie zuvor angegeben haben, und bestätigen Sie, dass Sie diese Aktion ausführen möchten.

3.  Wenn der Befehl abgeschlossen ist, wiederholen Sie Schritt 2 für jede verbleibende XML-Datei, die Sie durch den Export Ihrer vertrauenswürdigen Veröffentlichungsdomänen erstellt haben. Für diese Dateien legen Sie aber **-Active** auf **false** fest, wenn Sie den Importbefehl ausführen. Beispiel: **Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose**

4.  Verwenden Sie das Cmdlet [Disconnect-AadrmService](http://msdn.microsoft.com/library/windowsazure/dn629416.aspx) , um die Verbindung mit dem Azure RMS-Dienst zu trennen:

    ```
    Disconnect-AadrmService
    ```

Sie können jetzt mit [Schritt 3 fortfahren. Aktivieren des RMS-Mandanten](migrate-from-ad-rms-to-azure-rms.md#BKMK_Step3Migration).

### <a name="BKMK_Step3Migration"></a>Schritt 3: Aktivieren des RMS-Mandanten
Sämtliche Anweisungen zu diesem Schritt finden Sie im Thema [Aktivieren von Azure Rights Management](activate-service.md).

> [!TIP]
> Wenn Sie über ein Office 365-Abonnement verfügen, können Sie Azure RMS über das Office 365 Admin Center oder das klassische Azure-Portal aktivieren. Die Verwendung des klassischen Azure-Portals wird empfohlen, da Sie den nächsten Schritt in diesem Verwaltungsportal ausführen.

**Was geschieht, wenn Ihr Azure RMS-Mandant bereits aktiviert wurde?** Wenn der Azure RMS-Dienst für Ihre Organisation bereits aktiviert ist, verwenden Benutzer Azure RMS möglicherweise schon, um Inhalte mit einem automatisch generierten Mandantenschlüssel (und den Standardvorlagen) anstelle der vorhandenen Schlüssel (und Vorlagen) von AD RMS zu schützen. Dies ist unwahrscheinlich auf Computern, die in Ihrem Intranet ordnungsgemäß verwaltet werden, da diese automatisch für die AD RMS-Infrastruktur konfiguriert werden. Aber es kann auf dem Arbeitsgruppencomputern oder Computern passieren, die selten mit dem Intranet verbunden sind. Leider ist es auch schwierig, diese Computer zu identifizieren, weshalb wir empfehlen, dass Sie den Dienst nicht vor dem Import der Konfigurationsdaten aus AD RMS aktivieren.

Wenn Ihr Azure RMS-Mandant bereits aktiviert ist und Sie diese Computer identifizieren können, stellen Sie sicher, dass Sie das Skript "CleanUpRMS_RUN_Elevated.cmd" auf diesen Computern wie in Schritt 5 beschrieben ausführen. Durch das Ausführen dieses Skripts erzwingen sie, die Benutzerumgebung erneut zu initialisieren, damit sie den aktualisierten Mandantenschlüssel und die importierten Vorlagen herunterladen.

### <a name="BKMK_Step4Migration"></a>Schritt 4: Konfigurieren importierter Vorlagen
Da die importierten Vorlagen den Standardstatus **Archiviert**haben, müssen Sie diesen Status in **Veröffentlicht** ändern, wenn Benutzer in der Lage sein sollen, diese Vorlagen mit Azure RMS zu verwenden.

Wenn für Ihre Vorlagen in AD RMS die Gruppe **JEDER** verwendet wurde, wird diese Gruppe beim Importieren der Vorlagen in Azure RMS automatisch entfernt. In diesem Fall müssen Sie den importierten Vorlagen manuell die äquivalente Gruppe oder äquivalente Benutzer und dieselben Rechte hinzufügen. Die entsprechende Gruppe für Azure RMS heißt **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@<Mandantenname>.onmicrosoft.com**. Diese Gruppe kann beispielsweise für Contoso wie folgt aussehen: **AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@contoso.onmicrosoft.com**.

Wenn Sie nicht sicher sind, ob Ihre AD RMS-Vorlagen die Gruppe JEDER enthalten, erweitern Sie den Abschnitt [Windows PowerShell-Beispielskript zum Bestimmen von AD RMS-Vorlagen, die die Gruppe JEDER enthalten](#BKMK_ScriptForANYONE) in diesem Schritt, um das PowerShell-Beispielskript zu kopieren und mit seiner Hilfe diese Vorlagen zu bestimmen. Weitere Informationen zur Verwendung von Windows PowerShell mit AD RMS finden Sie unter [Verwalten von AD RMS mit Windows PowerShell](https://technet.microsoft.com/library/ee221079%28v=ws.10%29.aspx).

Sie können die für Ihre Organisation automatisch erstellte Gruppe sehen, wenn Sie eine der Standardrichtlinienvorlagen für Rechte im klassischen Azure-Portal kopieren und dann auf der Seite **RECHTE** den **BENUTZERNAMEN** identifizieren. Allerdings können Sie diese Gruppe nicht über das klassische Azure-Portal einer Vorlage hinzufügen, die manuell erstellt oder importiert wurde, sondern müssen eine der folgenden Azure RMS PowerShell-Optionen verwenden:

-   Verwenden Sie das PowerShell-Cmdlet [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx) zum Definieren der Gruppe "AllStaff" und der Rechte als ein Rechtedefinitionsobjekt. Wiederholen Sie diesen Befehl für alle anderen Gruppen oder Benutzer, denen in der ursprünglichen Vorlage zusätzlich zur Gruppe JEDER bereits Rechte gewährt wurden. Fügen Sie anschließend alle diese Rechtedefinitionsobjekte den Vorlagen mithilfe des Cmdlets [Set-AadrmTemplateProperty](https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx) hinzu.

-   Exportieren Sie die Vorlage mithilfe des Cmdlets [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx) in eine XML-Datei, die Sie so bearbeiten können, dass die Gruppe "AllStaff" und die Rechte den vorhandenen Gruppen und Berechtigungen hinzugefügt werden. Importieren Sie anschließend diese Änderung über das Cmdlet [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx) in Azure RMS zurück.

> [!NOTE]
> Die äquivalente Gruppe "AllStaff" ist nicht exakt mit der Gruppe JEDER in AD RMS identisch: Die Gruppe "AllStaff" enthält alle Benutzer aus Ihrem Azure-Mandanten, während die Gruppe JEDER alle authentifizierten Benutzer enthält, die sich auch außerhalb Ihrer Organisation befinden können.
> 
> Wegen dieses Unterschieds zwischen den beiden Gruppen müssen Sie möglicherweise zusätzlich zur Gruppe „AllStaff“ noch externe Benutzer hinzufügen. Externe E-Mail-Adressen für Gruppen werden derzeit nicht unterstützt.

Vorlagen, die Sie aus AD RMS importieren, sind im Aussehen und Verhalten mit benutzerdefinierten Vorlagen identisch, die Sie im klassischen Azure-Portal erstellen können. Wenn Sie importierte Vorlagen ändern möchten, sodass sie veröffentlicht werden und Benutzer diese sehen und in Anwendungen auswählen können, oder wenn Sie andere Änderungen an den Vorlagen vornehmen möchten, informieren Sie sich unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](configure-custom-templates.md).

> [!TIP]
> Damit eine konsistente Umgebung für Benutzer während der Migration gewahrt bleibt, sollten Sie an den importierten Vorlagen außer diesen beiden Änderungen keine weiteren vornehmen. Veröffentlichen Sie auch nicht die beiden Standardvorlagen, die in Azure RMS enthalten sind, und erstellen Sie keine neuen Vorlagen zu diesem Zeitpunkt. Warten Sie stattdessen, bis der Migrationsvorgang abgeschlossen ist und die AD RMS-Server außer Betrieb gesetzt wurden.

#### <a name="BKMK_ScriptForANYONE"></a>Windows PowerShell-Beispielskript zum Bestimmen von AD RMS-Vorlagen, die die Gruppe JEDER enthalten
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

### <a name="BKMK_Step5Migration"></a>Schritt 5: Neukonfigurieren von Clients zur Verwendung von Azure RMS
Für Windows-Clients:

1.  [Herunterladen der Migrationsskripts](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Diese Skripts setzen die Konfiguration auf Windows-Computern zurück, sodass sie den Azure RMS-Dienst anstelle von AD RMS verwenden.

2.  Befolgen Sie die Anweisungen im Umleitungsskript (Redirect_OnPrem.cmd), um das Skript so zu ändern, dass es auf Ihren neuen Azure RMS-Mandanten zeigt.

3.  Führen Sie diese Skripts auf den Windows-Computern mit erhöhten Rechten im Kontext des Benutzers aus.

Für Clients für mobile Geräte und Mac-Computer:

-   Entfernen Sie die DNS-SRV-Einträge, die Sie bei der Bereitstellung der [AD RMS-Erweiterung für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx)bereitgestellt haben.

#### Von den Migrationsskripts vorgenommene Änderungen
In diesem Abschnitt werden die Änderungen beschrieben, die von den Migrationsskripts vorgenommen werden. Sie können diese Informationen nur zu Referenzzwecken, zur Problembehandlung oder auch dann verwenden, wenn Sie diese Änderungen selbst vornehmen möchten.

CleanUpRMS_RUN_Elevated.cmd:

-   Löschen des Inhalts der Ordner "%userprofile%\AppData\Local\Microsoft\DRM" und "%userprofile%\AppData\Local\Microsoft\MSIPC", einschließlich Unterordner und Dateien mit langen Dateinamen.

-   Löschen des Inhalts der folgenden Registrierungsschlüssel:

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM

    -   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation

-   Löschen der folgenden Registrierungswerte:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Erstellen der folgenden Registrierungswerte für jede als Parameter bereitgestellte URL unter jedem der folgenden Speicherorte:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Jeder Eintrag hat den REG_SZ-Wert **https://OldRMSserverURL/_wmcs/licensing** mit den Daten im folgenden Format: **https://<IhreMandanten-URL>/_wmcs/licensing**.

    > [!NOTE]
    > *<IhreMandanten-URL>* weist das folgende Format auf: **{GUID}.rms.[Region].aadrm.com**.
    > 
    > Beispiel: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Finden Sie diesen Wert durch Identifizieren des Werts **RightsManagementServiceId** , wenn Sie das [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS ausführen.

### <a name="BKMK_Step6Migration"></a>Schritt 6: Konfigurieren der IRM-Integration mit Exchange Online
Wenn Sie Ihre TDP von AD RMS mit Exchange Online bereits importiert haben, müssen Sie diese TDP entfernen, um in Konflikt stehende Vorlagen und Richtlinien zu vermeiden, nachdem Sie zu Azure RMS migriert haben. Verwenden Sie hierzu das Cmdlet [Remove-RMSTrustedPublishingDomain](https://technet.microsoft.com/en-us/library/jj200720%28v=exchg.150%29.aspx) von Exchange Online.

Bei Verwendung der Azure RMS-Mandantenschlüsseltopologie **von Microsoft verwaltet**:

-   Informationen finden Sie im Abschnitt [Exchange Online: IRM-Konfiguration](configure-applications.md#BKMK_ExchangeOnline) unter [Konfigurieren von Anwendungen für Azure Rights Management](configure-applications.md). Dieser Abschnitt enthält typische auszuführenden Befehle, die eine Verbindung mit dem Exchange Online-Dienst herstellen, den Mandantenschlüssel aus Azure RMS importieren und IRM-Funktionen für Exchange Online ermöglichen. Nachdem Sie diese Schritte abgeschlossen haben, verfügen Sie über die volle RMS-Funktionalität mit Exchange Online.

Bei Verwendung einer Azure RMS-Mandantenschlüsseltopologie **vom Kunden verwaltet (BYOK)**:

-   Sie erhalten eine eingeschränkte RMS-Funktionalität mit Exchange Online, wie in [BYOK – Preise und Einschränkungen](plan-implement-tenant-key.md#BKMK_Pricing) unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md) beschrieben.

### <a name="BKMK_Step7Migration"></a>Schritt 7: Bereitstellen des RMS-Connectors
Wenn Sie die Funktion zur Verwaltung von Informationsrechten (IRM) von Exchange Server oder SharePoint Server mit AD RMS verwendet haben, müssen Sie zuerst IRM auf diesen Servern deaktivieren und die AD RMS-Konfiguration entfernen. Anschließend stellen Sie den Rights Management-Verbindungsdienst (RMS-Verbindungsdienst) bereit, der als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und Azure RMS fungiert.

Wenn Sie mehrere vertrauenswürdige Veröffentlichungsdomänen (TPDs) zum Schutz von E-Mail-Nachrichten in Azure RMS importiert haben, müssen Sie zum Schluss noch die Registrierung auf den Exchange Server-Computern manuell bearbeiten, um alle TPD-URLs an den RMS-Verbindungsdienst umzuleiten.

> [!NOTE]
> Überprüfen Sie zuerst, welche Versionen von lokalen Servern vom RMS-Verbindungsdienst unterstützt werden. Sie finden diese unter „Lokale Server, die Azure RMS unterstützen“ im Abschnitt [Anwendungen, die Azure RMS unterstützen](requirements-azure-rms.md#BKMK_SupportedApplications) des Themas [Voraussetzungen für Azure Rights Management](requirements-azure-rms.md).

##### Deaktivieren von IRM auf Exchange Servern und Entfernen der AD RMS-Konfiguration

1.  Suchen Sie auf jedem Exchange Server den folgenden Ordner, und löschen Sie alle Einträge in diesem Ordner: \ProgramData\Microsoft\DRM\Server\S-1-5-18

2.  Verwenden Sie auf einem der Exchange Server das Exchange-Cmdlet [Set_IRMConfiguration](http://technet.microsoft.com/library/dd979792.aspx) , um zuerst IRM-Funktionen für Nachrichten, die an interne Empfänger gesendet werden, zu deaktivieren:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $false
    ```

3.  Verwenden Sie dann das gleiche Cmdlet, um IRM-Funktionen für Nachrichten, die an externe Empfänger gesendet werden, zu deaktivieren:

    ```
    Set-IRMConfiguration -ExternalLicensingEnabled $false
    ```

4.  Verwenden Sie als Nächstes das gleiche Cmdlet, um IRM in Microsoft Office Outlook Web App und Microsoft Exchange ActiveSync zu deaktivieren:

    ```
    Set-IRMConfiguration -ClientAccessServerEnabled $false
    ```

5.  Verwenden Sie schließlich das gleiche Cmdlet, um alle zwischengespeicherten Zertifikate zu löschen:

    ```
    Set-IRMConfiguration -RefreshServerCertificates
    ```

6.  Setzen Sie nun IIS auf jedem Exchange Server zurück, z. B. indem Sie eine Eingabeaufforderung als Administrator ausführen und **iisreset** eingeben.

##### Deaktivieren von IRM auf SharePoint Servern und Entfernen der AD RMS-Konfiguration

1.  Stellen Sie sicher, dass keine Dokumente aus RMS-geschützten Bibliotheken ausgecheckt sind. Wenn dies der Fall ist, kann am Ende dieses Verfahrens nicht mehr darauf zugegriffen werden.

2.  Klicken Sie auf der Website der Microsoft SharePoint-Zentraladministration im Abschnitt **Schnellstart** auf **Sicherheit**.

3.  Klicken Sie auf der Seite **Sicherheit** im Abschnitt **Informationsrichtlinie** auf **Verwaltung von Informationsrechten konfigurieren**.

4.  Wählen Sie auf der Seite **Information Rights Management** im Abschnitt **Information Rights Management** **Verwenden Sie IRM nicht auf diesem Server**, und klicken Sie dann auf **OK**.

5.  Löschen Sie auf jedem der SharePoint Server-Computer den Inhalt des Ordners „\ProgramData\Microsoft\MSIPC\Server\<SID des Kontos, das SharePoint Server ausführt>“.

##### Installieren und Konfigurieren des RMS-Verbindungsdiensts

-   Verwenden Sie die Anweisungen im Thema [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

##### Nur für Exchange und mehrere TPDs: Bearbeiten der Registrierung

-   Fügen Sie auf jedem Exchange Server die folgenden Registrierungsschlüssel manuell für jede zusätzlich importierte TPD hinzu, um die TPD-URLs an den RMS-Verbindungsdienst umzuleiten. Diese Registrierungseinträge sind migrationsspezifisch und werden nicht vom Serverkonfigurationstool für den Microsoft RMS-Verbindungsdienst hinzugefügt.

    Gehen Sie beim Vornehmen dieser Änderungen an der Registrierung wie folgt vor:

    -   Ersetzen Sie *ConnectorFQDN* durch den Namen, den Sie im DNS für den Verbindungsdienst definiert haben. Beispielsweise **rmsconnector.contoso.com**.

    -   Verwenden Sie das HTTP- oder HTTPS-Präfix für die Verbindungsdienst-URL, je nachdem, ob Sie HTTP oder HTTPS für die Kommunikation zwischen dem Verbindungsdienst und Ihren lokalen Servern konfiguriert haben.

    **Für Exchange 2013:**

    |Registrierungspfad|Typ|Wert|Daten|
    |-----------------|--------|---------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://<AD RMS-Intranetlizenzierungs-URL>/_wmcs/licensing|Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:<br /><br />http://&lt;Verbindungsdienst-FQDN&gt;/_wmcs/licensing<br /><br />https://&lt;Verbindungsdienstname&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection|Reg_SZ|https://<AD RMS-Extranetlizenzierungs-URL>/_wmcs/licensing|Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:<br /><br />http://&lt;Verbindungsdienst-FQDN&gt;/_wmcs/licensing<br /><br />https://&lt;Verbindungsdienst-FQDN&gt;/_wmcs/licensing|
    **Für Exchange Server 2010:**

    |Registrierungspfad|Typ|Wert|Daten|
    |-----------------|--------|---------|--------|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://<AD RMS-Intranetlizenzierungs-URL>/_wmcs/licensing|Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:<br /><br />http://&lt;Verbindungsdienstname&gt;/_wmcs/licensing<br /><br />https://&lt;Verbindungsdienstname&gt;/_wmcs/licensing|
    |HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection|Reg_SZ|https://<AD RMS-Extranetlizenzierungs-URL>/_wmcs/licensing|Einer der folgenden Einträge, je nachdem, ob Sie HTTP oder HTTPS von Ihrem Exchange-Server zum RMS-Connector verwenden:<br /><br />http://&lt;Verbindungsdienstname&gt;/_wmcs/licensing<br /><br />https://&lt;Verbindungsdienstname&gt;/_wmcs/licensing|

Nachdem Sie diese Verfahren ausgeführt haben, sollten Sie unbedingt den Abschnitt **Nächste Schritte** im Thema [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md) lesen.

### <a name="BKMK_Step8Migration"></a>Schritt 8: Außerbetriebsetzung von AD RMS
Optional: Entfernen Sie den Dienstverbindungspunkt (Service Connection Point, SCP) aus Active Directory, um zu verhindern, dass Computer Ihre lokale Rights Management-Infrastruktur ermitteln. Dies ist aufgrund der Umleitung, die Sie in der Registrierung konfiguriert haben (z. B. durch Ausführen des Migrationsskripts), optional. Um den Service Connection Point zu entfernen, verwenden Sie das AD-SCP-Register-Tool aus dem [Rights Management Services-Verwaltungstoolkit](http://www.microsoft.com/download/details.aspx?id=1479).

Überwachen Sie die Aktivität Ihrer AD RMS-Server, z. B. durch Überprüfen der [Anforderungen im Systemintegritätsbericht](https://technet.microsoft.com/library/ee221012%28v=ws.10%29.aspx)und der [ServiceRequest-Tabelle](http://technet.microsoft.com/library/dd772686%28v=ws.10%29.aspx) oder durch [Überwachung des Benutzerzugriffs auf geschützte Inhalte](http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx). Wenn Sie bestätigt haben, dass RMS-Clients nicht mehr mit diesen Servern kommunizieren und Clients erfolgreich Azure RMS verwenden, können Sie die AD RMS-Serverrolle von diesen Servern entfernen. Wenn Sie dedizierte Server verwenden, können Sie auch als Vorsichtsmaßnahme zuerst die Server für einen gewissen Zeitraum herunterfahren, um zu gewährleisten, dass keine Probleme gemeldet werden, die möglicherweise einen Neustart dieser Server erfordern. Damit wird Dienstkontinuität sichergestellt, während Sie untersuchen, warum Clients Azure RMS nicht verwenden.

Nach der Außerbetriebsetzung Ihrer AD RMS-Server haben Sie die Gelegenheit, Ihre Vorlagen im klassischen Azure-Portal zu überprüfen und zu konsolidieren, sodass sich Benutzer unter weniger Vorlagen entscheiden müssen. Sie können die Vorlagen zu diesem Zeitpunkt auch neu konfigurieren oder sogar neue Vorlagen hinzufügen. Außerdem wäre dies ein guter Zeitpunkt, um die Standardvorlagen zu veröffentlichen. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](configure-custom-templates.md).

### <a name="BKMK_Step9Migration"></a>Schritt 9: Ändern des Azure RMS-Mandantenschlüssels
Dieser Schritt ist nach abgeschlossener Migration erforderlich, wenn Ihre AD RMS-Bereitstellung den RMS-Kryptografiemodus 1 verwendet hat. Bei einer Schlüsseländerung wird ein neuer Mandantenschlüssel erstellt, der RMS-Kryptografiemodus 2 verwendet. Die Verwendung von Azure RMS mit Kryptografiemodus 1 wird nur während der Migration unterstützt.

Wenn Sie RMS-Kryptografiemodus 2 ausgeführt haben, ist dieser Schritt nach der Migration optional, seine Ausführung empfiehlt sich jedoch, da so Ihr Azure RMS-Mandantenschlüssel vor potenziellen Sicherheitsverletzungen, die auf Ihren AD RMS-Schlüssel abzielen, geschützt ist. Wenn Sie Ihren Azure RMS-Mandantenschlüssel ändern (oder "neu vergeben"), wird ein neuer Schlüssel erstellt und der ursprüngliche Schlüssel archiviert. Da der Wechsel von einem Schlüssel zu einem anderen jedoch nicht sofort erfolgt, sondern sich über einige Wochen zieht, sollten Sie nicht warten, bis Sie eine Verletzung Ihres ursprünglichen Schlüssels vermuten, sondern Ihren RMS-Mandantenschlüssel ändern, sobald die Migration abgeschlossen ist.

Gehen Sie zum Ändern Ihres Azure RMS-Mandantenschlüssels wie folgt vor:

-   Wenn Ihr RMS-Mandantenschlüssel von Microsoft verwaltet wird: Rufen Sie Microsoft Customer Support Services (CSS) an, und weisen Sie sich als RMS-Mandantenadministrator aus.

-   Wenn Ihr RMS-Mandantenschlüssel von Ihnen (BYOK) verwaltet wird: Wiederholen Sie das BYOK-Verfahren zum Generieren eines neuen Schlüssels über das Internet oder persönlich.

Weitere Informationen zum Verwalten des RMS-Mandantenschlüssels finden Sie unter [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](operations-tenant-key.md).

## Siehe auch
[Konfigurieren von Azure Rights Management](configuring-azure-rights-management.md)



<!--HONumber=Apr16_HO3-->


