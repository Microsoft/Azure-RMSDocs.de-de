---
title: "Office 365&colon; Konfiguration für Clients und Onlinedienste | Azure RMS"
description: "Da Office 365 systemeigene Unterstützung für Azure RMS bietet, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und die Outlook Web App zu unterstützen. Die Benutzer müssen sich lediglich bei ihren Office-Anwendungen mit ihren Microsoft Office 365-Anmeldeinformationen anmelden, und sie können Dateien und E-Mails schützen sowie von anderen geschützte Dateien und E-Mails verwenden."
author: cabailey
manager: mbaldwin
ms.date: 07/13/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0a6ce612-1b6b-4e21-b7fd-bcf79e492c3b
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 09f152ef910cf9c08c9a693f79c40f491263c5d3


---

# Office 365: Konfigurationen für Clients und Onlinedienste

>*Gilt für: Azure Rights Management, Office 365*

Da Office 365 systemeigene Unterstützung für Azure RMS bietet, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und die Outlook Web App zu unterstützen. Die Benutzer müssen sich lediglich bei ihren Office-Anwendungen mit ihren [!INCLUDE[o365_1](../includes/o365_1_md.md)]-Anmeldeinformationen anmelden, und sie können Dateien und E-Mails schützen sowie von anderen geschützte Dateien und E-Mails verwenden.

Wir empfehlen jedoch, dass Sie diese Anwendungen durch die Rights Management-Freigabeanwendung ergänzen, damit Ihre Benutzer von dem Office-Add-In profitieren können. Weitere Informationen finden Sie unter [Rights Management-Freigabeanwendung: Installation und Konfiguration für Clients](configure-sharing-app.md).

## Exchange Online: IRM-Konfiguration
Um Exchange Online für die Unterstützung von Azure RMS zu konfigurieren, müssen Sie den IRM-Dienst für Exchange Online konfigurieren. Zu diesem Zweck verwenden Sie Windows PowerShell (es muss kein separates Modul installiert werden) und führen [PowerShell-Befehle für Exchange Online](https://technet.microsoft.com/library/jj200677.aspx) aus.

> [!NOTE]
> Sie können Exchange Online derzeit nicht für die Unterstützung von Azure RMS konfigurieren, wenn Sie einen vom Kunden verwalteten Mandantenschlüssel (BYOK) für Azure RMS anstelle der Standardkonfiguration mit einem von Microsoft verwalteten Mandantenschlüssel verwenden. Weitere Informationen finden Sie unter [BYOK – Preise und Einschränkungen](../plan-design/byok-price-restrictions.md).
>
> Wenn Sie versuchen, Exchange Online konfigurieren, wenn Azure RMS mit BYOK arbeitet, missling der Befehl zum Importieren des Schlüssels (Schritt 5 im folgenden Verfahren) mit der Fehlermeldung **[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]**.

Die folgenden Schritte bieten eine Reihe von Befehlen, die Sie ausführen müssen, um Exchange Online für die Verwendung von Azure RMS zu aktivieren:

1.  Wenn dies das erste Mal ist, dass Sie Windows PowerShell für Exchange Online auf Ihrem Computer verwendet haben, müssen Sie Windows PowerShell für das Ausführen signierter Skripts konfigurieren. Starten Sie Ihre Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen** , und geben Sie dann Folgendes ein:

    ```
    Set-ExecutionPolicy RemoteSigned
    ```

2.  Melden Sie in Ihrer Windows PowerShell-Sitzung bei Exchange Online mit einem Konto an, das für den Remoteshellzugriff aktiviert ist. Standardmäßig sind alle Konten, die in Exchange Online erstellt werden, für den Remoteshellzugriff aktiviert. Diese Einstellung kann über den Befehl [Set-User &lt;UserIdentity&gt; -RemotePowerShellEnabled](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) deaktiviert (und wieder aktiviert) werden.

    Um sich anzumelden, geben Sie Folgendes ein:

    ```
    $Cred = Get-Credential
    ```
    Geben Sie im Dialogfeld **Bei Windows PowerShell anmelden** Ihren Office 365-Benutzernamen und Ihr Kennwort ein.

3.  Stellen Sie eine Verbindung mit dem Exchange Online-Dienst her, indem Sie die folgenden beiden Befehle ausführen:

    ```
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    ```

    ```
    Import-PSSession $Session
    ```

4.  Geben Sie den Speicherort des Azure RMS-Mandantenschlüssels entsprechend dem Standort an, an dem der Mandant Ihrer Organisation erstellt wurde:

    Für Nordamerika (und Abonnements von Behörden):

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Europa:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Asien:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"
    ```
    Für Südamerika:

    ```
    Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"
    ```

5.  Importieren Sie Konfigurationsdaten aus Azure RMS in Exchange Online in Form der vertrauenswürdigen Veröffentlichungsdomäne (Trusted Publishing Domain, TPD). Dies umfasst den Azure RMS-Mandantenschlüssel und Azure RMS-Vorlagen:

    ```
    Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"
    ```
    In diesem Befehl wird der Name **RMS Online** als Basisnamen für die vertrauenswürdige Veröffentlichungsdomäne für Azure RMS in Exchange Online verwendet. Nach dem Importieren der vertrauenswürdigen Veröffentlichungsdomäne lautet der Name in Exchange Online **RMS Online - 1**.

6.  Aktivieren Sie Azure RMS-Funktionalität, damit IRM-Features für Exchange Online zur Verfügung stehen:

    ```
    Set-IRMConfiguration -InternalLicensingEnabled $true
    ```
    Nach der Ausführung dieses Befehls wird Rights Management für den Outlook-Client, Outlook Web App und Exchange Active Sync automatisch aktiviert.

7.  Testen Sie optional mit dem folgenden Befehl, ob diese Konfiguration erfolgreich ist:

    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Beispiel: **Test-IRMConfiguration -Sender adams@contoso.com**

    Dieser Befehl führt eine Reihe von Überprüfungen aus. Dazu zählen das Überprüfen der Verbindung mit dem Dienst sowie das Abrufen von Konfiguration-URIs, Lizenzen und Vorlagen. In der Windows PowerShell-Sitzung werden die Ergebnisse der einzelnen Überprüfungen angezeigt. Wenn alle diese Tests bestanden wurden, wird Folgendes eingeblendet: **GESAMTERGEBNIS: ERFOLG**

8.  Trennen Sie die PowerShell-Remotesitzung:

    ```
    Remove-PSSession $Session
    ```

Benutzer können ihre E-Mail-Nachrichten jetzt mithilfe von Azure RMS schützen. Wählen Sie in Outlook Web App im erweiterten Menü ( **...** ) den Befehl**Berechtigungen festlegen**und dann **Nicht weiterleiten** oder eine der verfügbaren Vorlagen aus, um den Informationsschutz auf die E-Mail-Nachricht und sämtliche Anlagen anzuwenden. Da die Outlook Web App jedoch die Benutzeroberfläche für einen Tag zwischenspeichert, warten Sie diesen Zeitraum ab, bevor Sie versuchen, den Informationsschutz auf E-Mail-Nachrichten anzuwenden, nachdem Sie diese Konfigurationsbefehle ausgeführt haben. Ehe Benutzeroberfläche entsprechend der neuen Konfiguration aktualisiert wird, sehen Sie keine Optionen im Menü **Berechtigungen festlegen** .

> [!IMPORTANT]
> Bei Erstellung neuer [benutzerdefinierter Vorlagen](configure-custom-templates.md) für Azure RMS oder Aktualisierung der Vorlagen müssen Sie jedes Mal den folgenden Exchange Online-PowerShell-Befehl ausführen (falls erforderlich, führen Sie die Schritte 2 und 3 zuerst aus), um diese Änderungen mit Exchange Online zu synchronisieren: `Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline`

Als Exchange-Administrator können Sie jetzt Features konfigurieren, die den Informationsschutz automatisch anwenden, wie z. B. [Transportregeln](https://technet.microsoft.com/library/dd302432.aspx), [DLP-Richtlinien (Data Loss Prevention, Verhinderung von Datenverlust](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx)und [geschützte Voicemail](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).

Weitere Informationen zum Konfigurieren von Exchange Online zum Aktivieren von IRM-Funktionen finden Sie in der Dokumentation in der Exchange-Bibliothek. Beispiel:

-   [Herstellen einer Verbindung mit Exchange Online über Remote-PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.160%29.aspx)

-   [Konfigurieren von IRM für die Verwendung von Azure Rights Management](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)

### Office 365-Nachrichtenverschlüsselung
Führen Sie dieselben im vorherigen Abschnitt beschriebenen Schritte aus. Wenn Sie aber nicht möchten, dass Vorlagen angezeigt werden, führen Sie vor Schritt 6 den folgenden Befehl aus, um zu verhindern, dass IRM-Vorlagen in der Outlook Web App und im Outlook-Client verfügbar sind: `Set-IRMConfiguration -ClientAccessServerEnabled $false`

Wenn Sie anschließend bereit sind, [Transportregeln](https://technet.microsoft.com/library/dd302432.aspx) für das automatische Ändern der Nachrichtensicherheit zu konfigurieren, wenn sich Empfänger außerhalb der Organisation befinden, wählen Sie die Option **Office 365-Nachrichtenverschlüsselung anwenden** aus.

Weitere Informationen zur Verschlüsselung von Nachrichten finden Sie unter [Verschlüsselung in Office 365](https://technet.microsoft.com/library/dn569286.aspx) in der Exchange-Bibliothek.

## SharePoint Online und OneDrive for Business: IRM-Konfiguration
Um SharePoint Online und OneDrive für die Unterstützung von Azure RMS zu konfigurieren, müssen Sie zunächst den IRM-Dienst für SharePoint Online über das SharePoint Admin Center aktivieren. Anschließend können Websitebesitzer ihre SharePoint-Listen und Dokumentbibliotheken und Benutzer ihre OneDrive for Business-Bibliothek mit IRM schützen, sodass Dokumente, die dort gespeichert und mit anderen Benutzern geteilt werden, automatisch von Azure RMS geschützt sind.

Um den IRM-Dienst für SharePoint Online zu aktivieren, lesen Sie die folgenden Anweisungen auf der Office-Website:

-   [Einrichten der Verwaltung von Informationsrechten (IRM) im SharePoint Admin Center](http://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Diese Konfiguration erfolgt durch den Office 365-Administrator.

### Konfigurieren von IRM für Listen und Bibliotheken
Nachdem Sie den IRM-Dienst für SharePoint aktiviert haben, können Websitebesitzer ihre SharePoint-Dokumentbibliotheken und -listen mit IRM schützen. Anleitungen hierzu finden Sie in den folgenden Ressourcen auf der Office-Website:

-   [Anwenden der Verwaltung von Informationsrechten (IRM) auf eine Liste oder Bibliothek](http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Diese Konfiguration erfolgt durch die SharePoint-Websiteadministrator.

### Konfigurieren von IRM für OneDrive for Business
Nachdem Sie den IRM-Dienst für SharePoint Online aktiviert haben, kann die OneDrive for Business-Dokumentbibliothek der Benutzer für den Rights Management-Schutz konfiguriert werden.  Benutzer können dies selbst über das Symbol **Einstellungen** auf ihrem OneDrive konfigurieren. Zwar können Administratoren Rights Management nicht mithilfe des SharePoint Admin Centers für OneDrive for Business der Benutzer konfigurieren, doch Sie können dies mithilfe der Windows PowerShell tun.

> [!NOTE]
> Weitere Informationen zum Konfigurieren von OneDrive for Business finden Sie in der Office-Dokumentation unter [Einrichten von OneDrive for Business in Office 365](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb).

#### Konfiguration für Benutzer
Geben Sie Benutzern diese Anleitungen, damit sie ihr OneDrive for Business konfigurieren und ihre Geschäftsdateien mit IRM schützen können.

1.  Klicken Sie in OneDrive auf das Symbol **Einstellungen** , um das Menü "Einstellungen" zu öffnen, und klicken Sie dann auf **Website-Inhalte**.

2.  Bewegen Sie den Mauszeiger über der Kachel **Dokumente** , wählen Sie die Auslassungspunkte (**...**), und klicken Sie dann auf **EINSTELLUNGEN**.

3.  Klicken Sie auf der Seite **Einstellungen** im Bereich **Berechtigungen und Verwaltung** auf **Information Rights Management**.

4.  Aktivieren Sie auf der Seite **Information Rights Management-Einstellungen** das Kontrollkästchen **Berechtigungen für diese Bibliothek beim Herunterladen einschränken** . Geben Sie den gewünschten Namen und eine Beschreibung für die Berechtigungen ein, und klicken Sie optional auf **OPTIONEN ANZEIGEN** , um optionale Konfigurationen zu konfigurieren. Klicken Sie dann auf **OK**.

    Weitere Informationen zu den Konfigurationsoptionen finden Sie in den Anweisungen in [Anwenden der Verwaltung von Informationsrechten (IRM) auf eine Liste oder Bibliothek](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1) in der Office-Dokumentation.

Da diese Konfiguration eher von Benutzern als von einem Administrator durchgeführt wird, um die OneDrive for Business-Bibliothek der Benutzer mit IRM zu schützen, informieren Sie die Benutzer über die Vorteile des Dateischutzes und über die hierfür erforderliche Vorgehensweise. Erläutern Sie beispielsweise, dass bei der Freigabe eines Dokuments aus OneDrive for Business nur vom Benutzer autorisierte Personen Zugriff darauf haben, und zwar mit den Einschränkungen, die er konfiguriert. Vermitteln Sie, dass dies selbst dann gilt, wenn die Datei umbenannt und an eine andere Stelle kopiert wurde.

#### Konfiguration für Administratoren
Zwar können Sie IRM nicht mithilfe das SharePoint Admin Centers für OneDrive for Business der Benutzer konfigurieren, doch Sie können dies mithilfe der Windows PowerShell tun. Führen Sie zum Aktivieren von IRM für diese Bibliotheken die folgenden Schritte aus:

1.  Laden Sie das [SharePoint Online-Clientkomponenten-SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) herunter, und installieren Sie es.

2.  Laden Sie die [SharePoint Online-Verwaltungsshell](http://www.microsoft.com/en-us/download/details.aspx?id=35588) herunter, und installieren Sie sie.

3.  Kopieren Sie den Inhalt des folgenden Skripts, und nennen Sie die Datei "Set-IRMOnOneDriveForBusiness.ps1" auf Ihrem Computer.

    *&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Dieses Beispielskript wird OHNE jede Gewährleistung bereitgestellt.

    ```
    # Requires Windows PowerShell version 3

    <#
      Description:

        Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists

     Script Installation Requirements:

       SharePoint Online Client Components SDK
       http://www.microsoft.com/en-us/download/details.aspx?id=42038

       SharePoint Online Management Shell
       http://www.microsoft.com/en-us/download/details.aspx?id=35588

    ======
    #>

    # URL will be in the format https://<tenant-name>-admin.sharepoint.com
    $sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

    $tenantAdmin = "admin@contoso.com"

    $webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
                 "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
                 "https://contoso-my.sharepoint.com/personal/user3_contoso_com")

    <# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
       Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

    #>

    $listTitle = "Documents"

    function Load-SharePointOnlineClientComponentAssemblies
    {
        [cmdletbinding()]
        param()

        process
        {
            # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
            try
            {
                Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
                [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

                return $true
            }
            catch
            {
                if($_.Exception.Message -match "Could not load file or assembly")
                {
                    Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
                }
                else
                {
                    Write-Error -Exception $_.Exception
                }
                return $false
            }
        }
    }

    function Load-SharePointOnlineModule
    {
        [cmdletbinding()]
        param()

        process
        {
            do
            {
                # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
                $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

                if(-not $spoModule)
                {
                    try
                    {
                        Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                        return $true
                    }
                    catch
                    {
                        if($_.Exception.Message -match "Could not load file or assembly")
                        {
                            Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                        }
                        else
                        {
                            Write-Error -Exception $_.Exception
                        }
                        return $false
                    }
                }
                else
                {
                    return $true
                }
            }
            while(-not $spoModule)
        }
    }

    function Set-IrmConfiguration
    {
        [cmdletbinding()]
        param(
            [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List,
            [parameter(Mandatory=$true)][string]$PolicyTitle,
            [parameter(Mandatory=$true)][string]$PolicyDescription,
            [parameter(Mandatory=$false)][switch]$IrmReject,
            [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate,
            [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView,
            [parameter(Mandatory=$false)][switch]$AllowPrint,
            [parameter(Mandatory=$false)][switch]$AllowScript,
            [parameter(Mandatory=$false)][switch]$AllowWriteCopy,
            [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays,
            [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays,
            [parameter(Mandatory=$false)][string]$GroupName
        )

        process
        {
            Write-Verbose "Applying IRM Configuration on '$($List.Title)'"

            # reset the value to the default settings
            $list.InformationRightsManagementSettings.Reset()

            $list.IrmEnabled = $true

            # IRM Policy title and description

                $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle
                $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription

            # Set additional IRM library settings

                # Do not allow users to upload documents that do not support IRM
                $list.IrmReject = $IrmReject.IsPresent

                $parsedDate = Get-Date
                if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate))
                {
                    # Stop restricting access to the library at <date>
                    $list.IrmExpire = $true
                    $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate
                }

                # Prevent opening documents in the browser for this Document Library
                $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent

            # Configure document access rights

                # Allow viewers to print
                $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent

                # Allow viewers to run script and screen reader to function on downloaded documents
                $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent

                # Allow viewers to write on a copy of the downloaded document
                $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent

                if($DocumentAccessExpireDays)
                {
                    # After download, document access rights will expire after these number of days (1-365)
                    $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true
                    $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays
                }

            # Set group protection and credentials interval

                if($LicenseCacheExpireDays)
                {
                    # Users must verify their credentials using this interval (days)
                    $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true
                    $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays
                }

                if($GroupName)
                {
                    # Allow group protection. Default group:
                    $list.InformationRightsManagementSettings.EnableGroupProtection = $true
                    $list.InformationRightsManagementSettings.GroupName             = $GroupName
                }
        }
        end
        {
            if($list)
            {
                Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
                $list.InformationRightsManagementSettings.Update()
                $list.Update()
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()
            }
        }
    }

    function Get-CredentialFromCredentialCache
    {
        [cmdletbinding()]
        param([string]$CredentialName)

        #if( Test-Path variable:\global:CredentialCache )
        if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
        {
            if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
            {
                Write-Verbose "Credential Cache Hit: $CredentialName"
                return $global:O365TenantAdminCredentialCache[$CredentialName]
            }
        }
        Write-Verbose "Credential Cache Miss: $CredentialName"
        return $null
    }

    function Add-CredentialToCredentialCache
    {
        [cmdletbinding()]
        param([System.Management.Automation.PSCredential]$Credential)

        if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
        {
            Write-Verbose "Initializing the Credential Cache"
            $global:O365TenantAdminCredentialCache = @{}
        }

        Write-Verbose "Adding Credential to the Credential Cache"
        $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
    }

    # load the required assemblies and Windows PowerShell modules

        if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

    # Add the credentials to the client context and SharePoint Online service connection

        # check for cached credentials to use
        $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

        if(-not $o365TenantAdminCredential)
        {
            # when credentials are not cached, prompt for the tenant admin credentials
            $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

            if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
            {
                Write-Error -Message "Could not validate the supplied tenant admin credentials"
                return
            }

            # add the credentials to the cache
            Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
        }

    # connect to Office365 first, required for SharePoint Online cmdlets to run

        Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

    # enumerate each of the specified site URLs

        foreach($webUrl in $webUrls)
        {
            $grantedSiteCollectionAdmin = $false

            try
            {
                # establish the client context and set the credentials to connect to the site
                $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
                $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

                # initialize the site and web context
                $script:clientContext.Load($script:clientContext.Site)
                $script:clientContext.Load($script:clientContext.Web)
                $script:clientContext.ExecuteQuery()

                # load and ensure the tenant admin user account if present on the target SharePoint site
                $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
                $script:clientContext.Load($tenantAdminUser)
                $script:clientContext.ExecuteQuery()

                # check if the tenant admin is a site admin
                if( -not $tenantAdminUser.IsSiteAdmin )
                {
                    try
                    {
                        # grant the tenant admin temporary admin rights to the site collection
                        Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                        $grantedSiteCollectionAdmin = $true
                    }
                    catch
                    {
                        Write-Error $_.Exception
                        return
                    }
                }

                try
                {
                    # load the list orlibrary using CSOM

                    $list = $null
                    $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                    $script:clientContext.Load($list)
                    $script:clientContext.ExecuteQuery()

                    # **************  ADMIN INSTRUCTIONS  **************
                    # If necessary, modify the following Set-IrmConfiguration parameters to match your required values
                    # The supplied options and values are for example only
                    # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90

                    Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users"  
                }
                catch
                {
                    Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
                }
           }
           finally
           {
                if($grantedSiteCollectionAdmin)
                {
                    # remove the temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
                }
           }
        }

    Disconnect-SPOService -ErrorAction SilentlyContinue
    ```

4.  Überprüfen Sie das Skript, und nehmen Sie folgende Änderungen vor:

    1.  Suche Sie nach `$sharepointAdminCenterUrl`, und ersetzen Sie den Beispielwert durch die URL Ihres eigenen SharePoint Admin Centers.

        Sie finden diesen Wert als Basis-URL, wenn Sie zum SharePoint Admin Center wechseln, wobei diese folgendes Format hat: https://*&lt;Mandantenname&gt;*-admin.sharepoint.com

        Wenn der Mandantenname beispielsweise "contoso" ist, geben Sie an: **https://contoso-admin.sharepoint.com**

    2.  Suche Sie nach `$tenantAdmin`, und ersetzen Sie den Beispielwert durch Ihr eigenes, vollqualifiziertes globales Administratorkonto für Office 365.

        Dieser Wert ist mit dem identisch, mit dem Sie sich beim Office 365-Verwaltungsportal als der globale Administrator anmelden, und hat folgendes Format: Benutzername@*&lt;Mandantendomänenname&gt;*.com

        Wenn der globale Office 365-Administratorbenutzername für die Mandantendomäne "contoso.com" beispielsweise "admin" ist, würden Sie angeben: **admin@contoso.com**

    3.  Suchen Sie nach `$webUrls`, und ersetzen Sie die Beispielwerte durch die OneDrive for Business-Web-URLs Ihrer Benutzer, wobei Sie so viele Einträge hinzufügen oder löschen, wie Sie benötigen.

        Alternativ finden Sie Informationen in den Kommentaren in dem Skript dazu, wie Sie dieses Array ersetzen, indem Sie eine CSV-Datei importieren, die alle URLs enthält, die Sie konfigurieren müssen.  Wir haben ein weiteres Beispielskript bereitgestellt, mit dem Sie automatisch nach den URLs suchen und diese extrahieren können, mit denen die CSV-Datei aufzufüllen ist. Wenn Sie dazu bereit sind, verwenden Sie sofort nach diesen Schritten den Abschnitt [Zusätzliches Skript zur Ausgabe aller OneDrive for Business-URLs in eine CSV-Datei](#additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file).

        Die Web-URL für das OneDrive for Business des Benutzers hat folgendes Format: https://*&lt;Mandantenname&gt;*-my.sharepoint.com/personal/*&lt;Benutzername&gt;*_*&lt;Mandantenname&gt;*_com

        Wenn der Benutzer im "contoso"-Mandanten beispielsweise den Benutzernamen "rsimone" hat, würden Sie angeben: **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

    4.  Da wir das Skript verwenden, um OneDrive for Business zu konfigurieren, ändern Sie nicht den Wert von **Documents** für die `$listTitle`-Variable.

    5.  Suchen Sie nach `ADMIN INSTRUCTIONS`. Wenn Sie keine Änderungen an diesem Abschnitt vornehmen, wird das OneDrive for Business des Benutzers für IRM mit dem Richtlinientitel "Geschützte Dateien" und der Beschreibung "Diese Richtlinie schränkt den Zugriff auf autorisierte Benutzer ein." konfiguriert.  Keine andere IRM-Optionen werden festgelegt, was wahrscheinlich für die meisten Umgebungen angebracht ist. Sie können den vorgeschlagenen Richtlinientitel und die Beschreibung jedoch ändern und außerdem alle anderen IRM-Optionen hinzufügen, die für Ihre Umgebung geeignet sind. Informationen, die Ihnen dabei helfen, Ihren eigenen Satz von Parametern für den Befehl "Set-IrmConfiguration" zu erstellen, finden Sie in dem kommentierten Beispiel in dem Skript.

5.  Speichern Sie das Skript, und signieren Sie es. Wenn Sie das Skript nicht signieren (höhere Sicherheit), muss Windows PowerShell auf Ihrem Computer für die Ausführung nicht signierter Skripts konfiguriert werden. Führen Sie hierzu eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen** aus, und geben Sie Folgendes ein: **Set-ExecutionPolicy Unrestricted**. Diese Konfiguration ermöglicht allerdings die Ausführung aller unsignierten Skripts (weniger sicher).

    Weitere Informationen zum Signieren von Windows PowerShell-Skripts finden Sie unter [about_Signing](https://technet.microsoft.com/library/hh847874.aspx) in der PowerShell-Dokumentationsbibliothek.

6.  Führen Sie das Skript aus, und geben Sie, wenn Sie dazu aufgefordert werden, das Kennwort für das Office-365-Administratorkonto ein. Wenn Sie das Skript ändern und es in derselben Windows PowerShell-Sitzung ausführen, werden Sie nicht zur Eingabe der Anmeldeinformationen aufgefordert.

> [!TIP]
> Sie können dieses Skript auch verwenden, um IRM für eine SharePoint Online-Bibliothek zu konfigurieren. Für diese Konfiguration möchte Sie vermutlich die zusätzliche Option **Benutzer dürfen keine Dokumente hochladen, die IRM nicht unterstützen** aktivieren, um sicherzustellen, dass die Bibliothek nur geschützte Dokumente enthält.    Fügen Sie hierzu dem Befehl "Set-IrmConfiguration" im Skript den `-IrmReject`-Parameter hinzu.
>
> Außerdem müssten Sie die `$webUrls`-Variable ändern (z. B. **https://contoso.sharepoint.com**) sowie die `$listTitle`-Variable (z. B. **$Reports**).

Wenn Sie IRM für OneDrive for Business-Bibliotheken eines Benutzers deaktivieren müssen, finden Sie Informationen im Abschnitt [Skript zum Deaktivieren von IRM für OneDrive for Business](#script-to-disable-irm-for-onedrive-for-business).

##### Zusätzliches Skript zur Ausgabe aller OneDrive for Business-URLs in eine CSV-Datei
Für Schritt 4c weiter oben können Sie das folgende Windows PowerShell-Skript verwenden, um die URLs für die OneDrive for Business-Bibliotheken aller Benutzer zu extrahieren, die Sie dann überprüfen, gegebenenfalls bearbeiten und dann in das Hauptskript importieren können.

Dieses Skript erfordert auch das [SharePoint Online-Clientkomponenten-SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) sowie die [SharePoint Online-Verwaltungsshell](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Befolgen Sie dieselben Anweisungen zum Kopieren und Einfügen, speichern Sie die Datei lokal (z. B. „Report-OneDriveForBusinessSiteInfo.ps1“), ändern Sie die Werte `$sharepointAdminCenterUrl` und `$tenantAdmin` wie vorher, und führen Sie dann das Skript aus.

*&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Dieses Beispielskript wird OHNE jede Gewährleistung bereitgestellt.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites.  
    Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv").

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

# URL will be in the format https://<tenant-name>-admin.sharepoint.com
$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.onmicrosoft.com"                           

$reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv"

$oneDriveForBusinessSiteUrls= @()
$resultsProcessed = 0

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# establish the client context and set the credentials to connect to the site

    $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl)
    $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

# run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs

    do
    {
        # build the query object
        $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext)
        $query.TrimDuplicates        = $false
        $query.RowLimit              = 500
        $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site"
        $query.StartRow              = $resultsProcessed
        $query.TotalRowsExactMinimum = 500000

        # run the query
        $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext)
        $queryResults = $searchExecutor.ExecuteQuery($query)
        $clientContext.ExecuteQuery()

        # enumerate the search results and store the site URLs
        $queryResults.Value[0].ResultRows | % {
            $oneDriveForBusinessSiteUrls += $_.Path
            $resultsProcessed++
        }
    }
    while($resultsProcessed -lt $queryResults.Value.TotalRows)

$oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
```

##### Skript zum Deaktivieren von IRM für OneDrive for Business
Verwenden Sie das folgende Beispielskript, wenn Sie IRM für OneDrive for Business der Benutzer deaktivieren müssen.

Dieses Skript erfordert auch das [SharePoint Online-Clientkomponenten-SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) sowie die [SharePoint Online-Verwaltungsshell](http://www.microsoft.com/en-us/download/details.aspx?id=35588). Kopieren Sie den Inhalt, und fügen Sie ihn ein. Speichern Sie die Datei lokal (z. B. „Disable-IRMOnOneDriveForBusiness.ps1“), und ändern Sie die Werte `$sharepointAdminCenterUrl` und `$tenantAdmin`. Geben Sie die OneDrive for Business-URLs manuell an, oder verwenden Sie das Skript aus dem vorherigen Abschnitt, sodass Sie diese importieren können, und führen Sie dann das Skript aus.

*&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Dieses Beispielskript wird OHNE jede Gewährleistung bereitgestellt.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists

 Script Installation Requirements:

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

======
#>

$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.com"

$webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
             "https://contoso-my.sharepoint.com/personal/person3_contoso_com")

<# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row).
   Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

#>

$listTitle = "Documents"

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Remove-IrmConfiguration
{
    [cmdletbinding()]
    param(
        [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List
    )

    process
    {
        Write-Verbose "Disabling IRM Configuration on '$($List.Title)'"

        $List.IrmEnabled = $false
        $List.IrmExpire  = $false
        $List.IrmReject  = $false
        $List.InformationRightsManagementSettings.Reset()
    }
    end
    {
        if($List)
        {
            Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
            $list.InformationRightsManagementSettings.Update()
            $list.Update()
            $script:clientContext.Load($list)
            $script:clientContext.ExecuteQuery()
        }
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }

# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        {
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }

# connect to Office365 first, required for SharePoint Online cmdlets to run

    Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential

# enumerate each of the specified site URLs

    foreach($webUrl in $webUrls)
    {
        $grantedSiteCollectionAdmin = $false

        try
        {
            # establish the client context and set the credentials to connect to the site
            $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
            $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

            # initialize the site and web context
            $script:clientContext.Load($script:clientContext.Site)
            $script:clientContext.Load($script:clientContext.Web)
            $script:clientContext.ExecuteQuery()

            # load and ensure the tenant admin user account if present on the target SharePoint site
            $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
            $script:clientContext.Load($tenantAdminUser)
            $script:clientContext.ExecuteQuery()

            # check if the tenant admin is a site admin
            if( -not $tenantAdminUser.IsSiteAdmin )
            {
                try
                {
                    # grant the tenant admin temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                    $grantedSiteCollectionAdmin = $true
                }
                catch
                {
                    Write-Error $_.Exception
                    return
                }
            }

            try
            {
                # load the list orlibrary using CSOM

                $list = $null
                $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()

               Remove-IrmConfiguration -List $list                 
            }
            catch
            {
                Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
            }
       }
       finally
       {
            if($grantedSiteCollectionAdmin)
            {
                # remove the temporary admin rights to the site collection
                Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
            }
       }
    }

Disconnect-SPOService -ErrorAction SilentlyContinue
```




<!--HONumber=Aug16_HO4-->


