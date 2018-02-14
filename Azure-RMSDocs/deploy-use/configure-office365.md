---
title: "Konfiguration für Office 365-Clients und -Onlinedienste zur Verwendung von Azure RMS über AIP"
description: "Dieser Artikel enthält Informationen und Anweisungen für Administratoren, die Office 365 so konfigurieren möchten, dass es mit dem Azure Rights Management-Dienst von Azure Information Protection verwendet werden kann."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/18/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0a6ce612-1b6b-4e21-b7fd-bcf79e492c3b
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 367c41d91d4e4250370016bdff80bd9e2e366924
ms.sourcegitcommit: e21fb3385de6f0e251167e5dc973e90f0e7f2bcf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2018
---
# <a name="office-365-configuration-for-clients-and-online-services-to-use-the-azure-rights-management-service"></a>Office 365: Konfiguration für Clients und Onlinedienste zur Verwendung des Azure Rights Management-Diensts

>*Gilt für: Azure Information Protection, Office 365*

Da Office 365 den Azure Rights Management-Dienst von Azure Information Protection nativ unterstützt, ist zur Unterstützung der IRM-Features (Information Rights Management) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Web keine Clientcomputerkonfiguration erforderlich. Benutzer müssen sich lediglich mit ihren [!INCLUDE[o365_1](../includes/o365_1_md.md)]-Anmeldeinformationen bei ihren Office-Anwendungen anmelden. Anschließend können sie Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

Es empfiehlt sich allerdings, diese Anwendungen durch den Azure Information Protection-Client zu ergänzen, damit die Benutzer von dem Office-Add-In und der Unterstützung zusätzlicher Dateitypen profitieren können. Weitere Informationen finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

## <a name="exchange-online-irm-configuration"></a>Exchange Online: IRM-Konfiguration
Informationen zur Zusammenarbeit zwischen Exchance Online IRM und dem Azure Rights Management-Dienst finden Sie im Abschnitt **Verstehen und Kennenlernen** unter [Exchange Online und Exchange Server](../understand-explore/office-apps-services-support.md#exchange-online-and-exchange-server).

Informationen zum Konfigurieren von Exchange Online zur Verwendung des Azure Rights Management-Diensts finden Sie unter [Set up new Office 365 Message Encryption capabilities built on top of Azure Information Protection](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) (Einrichten von neuen, auf Azure Information Protection basierenden Funktionen in der Office 365-Nachrichtenverschlüsselung).

Wenn Sie Exchange Online für IRM bereits durch Importieren Ihrer vertrauenswürdigen Veröffentlichungsdomäne (Trusted Publishing Domain, TPD) aus dem Azure Rights Management-Dienst konfiguriert haben, gehen Sie auf die gleiche Weise vor, um die neuen Funktionen in Exchange Online zu aktivieren.

Nachdem Sie Exchange Online für die Verwendung des Azure Rights Management-Diensts konfiguriert haben, können Sie Features mit automatischer Anwendung des Informationsschutzes konfigurieren. Hierzu zählen beispielsweise [Transportregeln](https://technet.microsoft.com/library/dd302432.aspx), [DLP-Richtlinien (Data Loss Prevention)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) und [Voicemail-Schutz](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).

## <a name="sharepoint-online-and-onedrive-for-business-irm-configuration"></a>SharePoint Online und OneDrive for Business: IRM-Konfiguration

Informationen zur Zusammenarbeit zwischen SharePoint Online IRM und dem Azure Rights Management-Dienst finden Sie im Abschnitt **Verstehen und Kennenlernen** unter [SharePoint Online und SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server).

Um SharePoint Online und OneDrive für die Unterstützung des Azure Rights Management-Diensts zu konfigurieren, müssen Sie zunächst den IRM-Dienst (Information Rights Management) für SharePoint Online über das SharePoint Admin Center aktivieren. Anschließend können Websitebesitzer ihre SharePoint-Listen und -Dokumentbibliotheken und Benutzer ihre OneDrive for Business-Bibliothek mit IRM schützen, sodass Dokumente, die dort gespeichert und mit anderen Benutzern geteilt werden, automatisch durch den Azure Rights Management-Dienst geschützt werden.

> [!NOTE]
> Durch IRM geschützte Bibliotheken für SharePoint und OneDrive for Business erfordern die neuste Version des neuen OneDrive-Synchronisierungsclients („OneDrive.exe“). Weitere Informationen finden Sie unter [Enable users to sync IRM-protected files with the OneDrive sync client (Preview)](https://support.office.com/en-us/article/6778d4de-b5f8-423c-af43-a1b2449e9b99) (Ermöglichen des Synchronisierens von durch IRM geschützten Dateien mit dem OneDrive-Synchronisierungsclient (Vorschauversion)).

Eine Anleitung zum Aktivieren des IRM-Diensts (Information Rights Management) für SharePoint Online finden Sie auf der folgenden Office-Website:

- [Einrichten von Information Rights Management (IRM, Verwaltung von Informationsrechten) im SharePoint Admin Center](https://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx)

Diese Konfiguration erfolgt durch den Office 365-Administrator.

### <a name="configuring-irm-for-libraries-and-lists"></a>Konfigurieren von IRM für Listen und Bibliotheken
Nachdem Sie den IRM-Dienst für SharePoint aktiviert haben, können Websitebesitzer ihre SharePoint-Dokumentbibliotheken und -listen mit IRM schützen. Eine entsprechende Anleitung finden Sie auf der Office-Website:

- [Anwenden der Verwaltung von Informationsrechten auf eine Liste oder Bibliothek](https://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Diese Konfiguration erfolgt durch den SharePoint-Websiteadministrator.

### <a name="configuring-irm-for-onedrive-for-business"></a>Konfigurieren von IRM für OneDrive for Business
Nach Aktivierung des IRM-Diensts für SharePoint Online kann die OneDrive for Business-Dokumentbibliothek der Benutzer für den Rights Management-Schutz konfiguriert werden.  Benutzer können dieses Feature über das Symbol **Einstellungen** auf ihrem OneDrive selbst konfigurieren. Zwar können Administratoren Rights Management nicht mithilfe des SharePoint Admin Centers für OneDrive for Business der Benutzer konfigurieren, Sie können dafür jedoch Windows PowerShell verwenden.

> [!NOTE]
> Weitere Informationen zum Konfigurieren von OneDrive for Business finden Sie in der Office-Dokumentation unter [OneDrive for Business – Administratorhilfe](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb).

#### <a name="configuration-for-users"></a>Konfiguration für Benutzer
Stellen Sie Benutzern diese Anleitungen zur Verfügung, damit sie OneDrive for Business konfigurieren und ihre Geschäftsdateien mit IRM schützen können.

1.  Klicken Sie in OneDrive auf das Symbol **Einstellungen**, um das Einstellungsmenü zu öffnen, und klicken Sie dann auf **Websiteinhalt**.

2.  Zeigen Sie auf die Kachel **Dokumente**, klicken Sie auf die Auslassungspunkte (**...**), und klicken Sie anschließend auf **EINSTELLUNGEN**.

3.  Klicken Sie auf der Seite **Einstellungen** im Abschnitt **Berechtigungen und Verwaltung** auf **Information Rights Management**.

4.  Aktivieren Sie auf der Seite **Einstellungen für Information Rights Management** das Kontrollkästchen **Berechtigungen für diese Bibliothek beim Herunterladen einschränken**. Geben Sie den gewünschten Namen und eine Beschreibung für die Berechtigungen ein, und klicken Sie optional auf **OPTIONEN ANZEIGEN**, um optionale Konfigurationen vorzunehmen. Klicken Sie anschließend auf **OK**.

    Weitere Informationen zu den Konfigurationsoptionen finden Sie in der Office-Dokumentation in den Anweisungen unter [Anwenden der Verwaltung von Informationsrechten auf eine Liste oder Bibliothek](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1).

Da diese Konfiguration für den IRM-Schutz der OneDrive for Business-Bibliothek nicht von einem Administrator, sondern von den Benutzern durchgeführt wird, informieren Sie die Benutzer über die Vorteile des Dateischutzes und über die entsprechende Vorgehensweise. Erläutern Sie beispielsweise, dass bei der Freigabe eines Dokuments aus OneDrive for Business nur vom Benutzer autorisierte Personen darauf zugreifen können und dass dabei die vom Benutzer konfigurierten Einschränkungen gelten, auch wenn die Datei umbenannt und an einen anderen Ort kopiert wird.

#### <a name="configuration-for-administrators"></a>Konfiguration für Administratoren
Zwar können Sie IRM nicht mithilfe des SharePoint Admin Centers für OneDrive for Business der Benutzer konfigurieren, Sie können dafür aber Windows PowerShell verwenden. Führen Sie zum Aktivieren von IRM für diese Bibliotheken die folgenden Schritte aus:

1.  Laden Sie das [SharePoint Online-Clientkomponenten-SDK](https://www.microsoft.com/en-us/download/details.aspx?id=42038) herunter, und installieren Sie es.

2.  Laden Sie die [SharePoint Online-Verwaltungsshell](https://www.microsoft.com/en-us/download/details.aspx?id=35588) herunter, und installieren Sie sie.

3.  Kopieren Sie den Inhalt des folgenden Skripts, und nennen Sie die Datei „Set-IRMOnOneDriveForBusiness.ps1“ auf Ihrem Computer.

    *&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Es wird in der vorliegenden Form ohne jegliche Gewährleistung bereitgestellt.

    ```
    # Requires Windows PowerShell version 3

    <#
      Description:

        Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists

     Script Installation Requirements:

       SharePoint Online Client Components SDK
       https://www.microsoft.com/en-us/download/details.aspx?id=42038

       SharePoint Online Management Shell
       https://www.microsoft.com/en-us/download/details.aspx?id=35588

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

4.  Sehen Sie sich das Skript an, und nehmen Sie folgende Änderungen vor:

    1.  Suchen Sie nach `$sharepointAdminCenterUrl`, und ersetzen Sie den Beispielwert durch die URL Ihres eigenen SharePoint Admin Centers.

        Sie finden diesen Wert als Basis-URL, wenn Sie zum SharePoint Admin Center wechseln. Der Wert hat das folgende Format: https://*&lt;Mandantenname&gt;*-admin.sharepoint.com

        Wenn der Mandantenname also beispielsweise „contoso“ lautet, geben Sie Folgendes an: **https://contoso-admin.sharepoint.com**

    2.  Suchen Sie nach `$tenantAdmin`, und ersetzen Sie den Beispielwert durch Ihr eigenes, vollqualifiziertes globales Administratorkonto für Office 365.

        Dieser Wert entspricht dem Wert, mit dem Sie sich beim Office 365-Verwaltungsportal als globaler Administrator anmelden, und hat das folgende Format: <Benutzername>@*&lt;Mandantendomänenname&gt;*.com

        Wenn der Office 365-Benutzername des globalen Administrators für die Mandantendomäne „contoso.com“ also beispielsweise „admin“ lautet, sieht die Eingabe wie folgt aus: **admin@contoso.com**

    3.  Suchen Sie nach `$webUrls`, und ersetzen Sie die Beispielwerte durch die OneDrive for Business-Web-URLs Ihrer Benutzer. Dabei können Sie beliebig viele Einträge hinzufügen oder löschen.

        Falls Sie stattdessen eine CSV-Datei mit allen zu konfigurierenden URLs importieren möchten, informieren Sie sich anhand der Kommentare im Skript über die entsprechende Vorgehensweise.  Wir haben ein weiteres Beispielskript bereitgestellt, mit dem Sie automatisch nach den URLs für die CSV-Datei suchen und sie extrahieren können. Wenn Sie dazu bereit sind, wechseln Sie direkt im Anschluss an diese Schritte zum Abschnitt [Zusätzliches Skript zur Ausgabe aller OneDrive for Business-URLs in eine CSV-Datei](#additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file).

        Die Web-URL für das OneDrive for Business des Benutzers hat folgendes Format: https://*&lt;Mandantenname&gt;*-my.sharepoint.com/personal/*&lt;Benutzername&gt;*_*&lt;Mandantenname&gt;*_com

        Wenn der Benutzer im Mandanten „contoso“ also beispielsweise den Benutzernamen „rsimone“ hat, sieht die Angabe wie folgt aus: **https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

    4.  Da wir das Skript verwenden, um OneDrive for Business zu konfigurieren, lassen Sie den Wert **Documents** für die Variable `$listTitle` unverändert.

    5.  Suchen Sie nach `ADMIN INSTRUCTIONS`. Wenn Sie keine Änderungen an diesem Abschnitt vornehmen, wird die OneDrive for Business-Instanz des Benutzers für IRM mit dem Richtlinientitel „Protected Files“ und der Beschreibung „This policy restricts access to authorized users“ konfiguriert.  Es werden keine weiteren IRM-Optionen festgelegt, was für die meisten Umgebungen angemessen sein dürfte. Sie können den vorgeschlagenen Richtlinientitel und die Beschreibung jedoch ändern und außerdem alle anderen IRM-Optionen hinzufügen, die für Ihre Umgebung geeignet sind. Informationen, die Ihnen dabei helfen, Ihren eigenen Satz von Parametern für den Befehl „Set-IrmConfiguration“ zu erstellen, finden Sie im kommentierten Beispiel innerhalb des Skripts.

5.  Speichern Sie das Skript, und signieren Sie es. Die Signatur erhöht die Sicherheit. Wenn Sie das Skript nicht signieren, muss Windows PowerShell auf Ihrem Computer für die Ausführung nicht signierter Skripts konfiguriert werden. Führen Sie hierzu eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen** aus, und geben Sie Folgendes ein: **Set-ExecutionPolicy Unrestricted**. Bei dieser Konfiguration können allerdings alle nicht signierten Skripts ausgeführt werden, was weniger sicher ist.

    Weitere Informationen zum Signieren von Windows PowerShell-Skripts finden Sie in der PowerShell-Dokumentationsbibliothek unter [about_Signing](https://technet.microsoft.com/library/hh847874.aspx).

6.  Führen Sie das Skript aus, und geben Sie das Kennwort für das Office-365-Administratorkonto ein, wenn Sie dazu aufgefordert werden. Wenn Sie das Skript ändern und es in der gleichen Windows PowerShell-Sitzung ausführen, werden Sie nicht zur Eingabe von Anmeldeinformationen aufgefordert.

> [!TIP]
> Sie können dieses Skript auch verwenden, um IRM für eine SharePoint Online-Bibliothek zu konfigurieren. Bei dieser Konfiguration empfiehlt es sich in der Regel, die zusätzliche Option **Benutzer dürfen keine Dokumente hochladen, die IRM nicht unterstützen** aktivieren, um sicherzustellen, dass die Bibliothek nur geschützte Dokumente enthält.    Fügen Sie hierzu dem Befehl „Set-IrmConfiguration“ im Skript den Parameter `-IrmReject` hinzu.
>
> Darüber hinaus müssen Sie die Variable `$webUrls` (Beispiel: **https://contoso.sharepoint.com**) und die Variable `$listTitle` (Beispiel: **$Reports**) ändern.

Wenn Sie IRM für OneDrive for Business-Bibliotheken eines Benutzers deaktivieren müssen, lesen Sie den Abschnitt [Skript zum Deaktivieren von IRM für OneDrive for Business](#script-to-disable-irm-for-onedrive-for-business).

##### <a name="additional-script-to-output-all-onedrive-for-business-urls-to-a-csv-file"></a>Zusätzliches Skript zur Ausgabe aller OneDrive for Business-URLs in eine CSV-Datei
Für Schritt 4c weiter oben können Sie das folgende Windows PowerShell-Skript verwenden, um die URLs für die OneDrive for Business-Bibliotheken aller Benutzer zu extrahieren, die Sie dann überprüfen, gegebenenfalls bearbeiten und anschließend in das Hauptskript importieren können.

Dieses Skript setzt ebenfalls das [SharePoint Online-Clientkomponenten-SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) und die [SharePoint Online-Verwaltungsshell](http://www.microsoft.com/en-us/download/details.aspx?id=35588) voraus. Befolgen Sie die gleichen Anweisungen zum Kopieren und Einfügen, speichern Sie die Datei lokal (beispielsweise unter dem Namen „Report-OneDriveForBusinessSiteInfo.ps1“), ändern Sie wie zuvor die Werte `$sharepointAdminCenterUrl` und `$tenantAdmin`, und führen Sie anschließend das Skript aus.

*&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Es wird in der vorliegenden Form ohne jegliche Gewährleistung bereitgestellt.

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

##### <a name="script-to-disable-irm-for-onedrive-for-business"></a>Skript zum Deaktivieren von IRM für OneDrive for Business
Verwenden Sie das folgende Beispielskript, wenn Sie IRM für OneDrive for Business der Benutzer deaktivieren müssen.

Dieses Skript setzt ebenfalls das [SharePoint Online-Clientkomponenten-SDK](http://www.microsoft.com/en-us/download/details.aspx?id=42038) und die [SharePoint Online-Verwaltungsshell](http://www.microsoft.com/en-us/download/details.aspx?id=35588) voraus. Kopieren Sie den Inhalt, und fügen Sie ihn ein. Speichern Sie die Datei lokal (beispielsweise unter dem Namen „Disable-IRMOnOneDriveForBusiness.ps1“), und ändern Sie die Werte `$sharepointAdminCenterUrl` und `$tenantAdmin`. Geben Sie die OneDrive for Business-URLs manuell an, oder verwenden Sie das Skript aus dem vorherigen Abschnitt, um sie zu importieren. Führen Sie anschließend das Skript aus.

*&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Es wird in der vorliegenden Form ohne jegliche Gewährleistung bereitgestellt.

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

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
