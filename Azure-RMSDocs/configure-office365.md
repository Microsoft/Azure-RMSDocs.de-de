---
title: Konfiguration für Office 365-Dienste zur Verwendung Azure RMS-aip
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Office 365-Diensten für die Zusammenarbeit mit dem Azure Rights Management-Dienst von Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0a6ce612-1b6b-4e21-b7fd-bcf79e492c3b
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 3ee5ab34b2e7a502157ea4f788b6d172c683506e
ms.sourcegitcommit: 8499602fba94fbfa28d7682da2027eeed6583c61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2020
ms.locfileid: "83746864"
---
# <a name="office365-configuration-for-online-services-to-use-the-azure-rights-management-service"></a>Office 365: Konfiguration für Onlinedienste die Verwendung des Azure Rights Management-Dienstanbieter

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

In den folgenden Abschnitten finden Sie Informationen zum Konfigurieren von Exchange Online, Microsoft SharePoint und Microsoft onedrive für die Verwendung des Azure-Rights Management Dienstanbieter von Azure Information Protection.

## <a name="exchangeonline-irm-configuration"></a>Exchange Online: IRM-Konfiguration
Informationen zur Funktionsweise von Exchange Online mit dem Azure Rights Management-Dienst finden Sie im Abschnitt [Exchange Online und Exchange Server](office-apps-services-support.md#exchange-online-and-exchange-server) , in dem erläutert wird, [wie Office-Anwendungen und-Dienste Azure Rights Management unterstützen](office-apps-services-support.md).

Möglicherweise ist Azure Rights Management schon für Exchange Online aktiviert. Sie können dies herausfinden, indem Sie die folgenden Befehle ausführen:

1. Wenn Sie Windows PowerShell für Exchange Online zum ersten Mal auf Ihrem Computer verwenden, müssen Sie Windows PowerShell zum Ausführen von signierten Skripts konfigurieren. Starten Sie Ihre Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen**, und geben Sie dann Folgendes ein:
    
        Set-ExecutionPolicy RemoteSigned
    
    Drücken Sie zum Bestätigen **Y**.

2. Melden Sie in Ihrer Windows PowerShell-Sitzung bei Exchange Online mit einem Konto an, das für den Remoteshellzugriff aktiviert ist. Standardmäßig sind alle Konten, die in Exchange Online erstellt werden, für den remoteshellzugriff aktiviert. Dies kann jedoch mithilfe des Befehls [Set-User &lt; UserIdentity &gt; -remotepowershellaktivideaktiviert](https://technet.microsoft.com/library/jj984292%28v=exchg.160%29.aspx) (und aktiviert) werden.
    
    Geben Sie zum Anmelden zunächst Folgendes ein:
    
        $Cred = Get-Credential
   
    Geben Sie dann im Dialogfeld **Bei Windows PowerShell anmelden** Ihren Office 365-Benutzernamen und Ihr Kennwort ein.

3. Stellen Sie eine Verbindung mit Exchange Online her, indem Sie zunächst eine Variable festlegen:
    
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
    
    Führen Sie dann den folgenden Befehl aus:
    
        Import-PSSession $Session

4. Führen Sie den Befehl [Get-IRMConfiguration](https://technet.microsoft.com/library/dd776120(v=exchg.160).aspx) aus, um die Exchange Online-Konfiguration des Schutzdiensts anzuzeigen:
    
        Get-IRMConfiguration
    
    Machen Sie in der Ausgabe den Wert für **AzureRMSLicensingEnabled** ausfindig:
    
    - Wenn AzureRMSLicensingEnabled auf **TRUE** festgelegt ist, ist Azure Rights Management bereits für Exchange Online aktiviert. 
    
    - Wenn AzureRMSLicensingEnabled auf **FALSE** festgelegt ist, führen Sie den folgenden Befehl aus, um Exchange Online für den Azure Rights Management-Dienst zu aktivieren: `Set-IRMConfiguration -AzureRMSLicensingEnabled $true`

5. Führen Sie den folgenden Befehl aus, um zu prüfen, ob Exchange Online erfolgreich konfiguriert wurde:
    ```
    Test-IRMConfiguration -Sender <user email address>
    ```
    Beispiel: <strong>Test-IRMConfiguration -Sender adams@contoso.com</strong>
    
    Dieser Befehl führt eine Reihe von Überprüfungen aus. Dazu zählen das Überprüfen der Verbindung mit dem Dienst sowie das Abrufen von Konfiguration-URIs, Lizenzen und Vorlagen. In der Windows PowerShell-Sitzung werden die Ergebnisse der einzelnen Überprüfungen angezeigt. Wenn alle diese Tests bestanden wurden, wird Folgendes eingeblendet: **GESAMTERGEBNIS: ERFOLG**

Wenn Azure Rights Management für Exchange Online aktiviert ist, können Sie Features konfigurieren, die den Informationsschutz automatisch anwenden. Hierzu gehören z.B. [E-Mail-Flussregeln](https://support.office.com/article/define-mail-flow-rules-to-encrypt-email-messages-in-office-365-9b7daf19-d5f2-415b-bc43-a0f5f4a585e8), [DLP-Richtlinien (Data Loss Prevention)](https://technet.microsoft.com/library/jj150527%28v=exchg.150%29.aspx) und [geschützte Voicemail](https://technet.microsoft.com/library/dn198211%28v=exchg.150%29.aspx) (Unified Messaging).

## <a name="sharepoint-in-microsoft-365-and-onedrive-irm-configuration"></a>SharePoint in Microsoft 365 und onedrive: unm-Konfiguration

Weitere Informationen zur Funktionsweise von SharePoint-IRiM mit dem Azure Rights Management-Dienst finden Sie unter [SharePoint in Microsoft 365 und SharePoint Server im](office-apps-services-support.md#sharepoint-in-microsoft-365-and-sharepoint-server) Abschnitt **Rights Management Protection** in dieser Dokumentation.

Um SharePoint in Microsoft 365 und onedrive für die Unterstützung des Azure Rights Management-Dienstanbieter zu konfigurieren, müssen Sie zunächst den Dienst für Informationsrechte Verwaltung (Information Rights Management, unm) für SharePoint über das SharePoint Admin Center aktivieren. Anschließend können Website Besitzer Ihre SharePoint-Listen und Dokument Bibliotheken mit dem Schutz Ihrer SharePoint-Listen und-Dateien schützen, und Benutzer können Ihre onedrive-Bibliothek mit einem unm schützen, sodass Dokumente, die dort gespeichert und mit anderen Benutzern geteilt werden, automatisch durch den Azure Rights Management-Dienst geschützt werden.

> [!NOTE]
> Für in Microsoft 365 und onedrive geschützte Bibliotheken für SharePoint ist die neueste Version des neuen onedrive-Synchronisierungs Clients (onedrive. exe) und die Version des [RMS-Clients aus dem Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=38396)erforderlich. Installieren Sie diese Version des RMS-Clients, auch wenn Sie bereits den Azure Information Protection-Client installiert haben. Weitere Informationen zu diesem Bereitstellungsszenario finden Sie unter [Bereitstellen des neuen OneDrive-Synchronisierungsclients in einer Unternehmensumgebung](https://support.office.com/article/Deploy-the-new-OneDrive-sync-client-in-an-enterprise-environment-3f3a511c-30c6-404a-98bf-76f95c519668).

Informationen zum Aktivieren des Dienst Informationsrechte Verwaltung (Information Rights Management, unm) für SharePoint finden Sie in den folgenden Anweisungen der Office-Dokumentation:

- [Einrichten von Informations Rights Management (unm) im SharePoint Admin Center](https://docs.microsoft.com/microsoft-365/compliance/set-up-irm-in-sp-admin-center)

Diese Konfiguration erfolgt durch den Office 365-Administrator.

### <a name="configuring-irm-for-libraries-and-lists"></a>Konfigurieren von IRM für Listen und Bibliotheken
Nachdem Sie den IRM-Dienst für SharePoint aktiviert haben, können Websitebesitzer ihre SharePoint-Dokumentbibliotheken und -listen mit IRM schützen. Eine entsprechende Anleitung finden Sie auf der Office-Website:

- [Anwenden der Verwaltung von Informationsrechten auf eine Liste oder Bibliothek](https://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx)

Diese Konfiguration erfolgt durch den SharePoint-Websiteadministrator.

### <a name="configuring-irm-for-onedrive"></a>Konfigurieren von unm für onedrive
Nachdem Sie den "unm"-Dienst für SharePoint aktiviert haben, können die onedrive-Dokumentbibliothek oder einzelne Ordner der Benutzer für den Rights Management Schutz konfiguriert werden. Benutzer haben die Möglichkeit, dies selbst über ihre OneDrive-Website einzurichten. Administratoren können diesen Schutz für sie nicht über das SharePoint Admin Center, sondern nur über Windows PowerShell konfigurieren.

> [!NOTE]
> Weitere Informationen zum Konfigurieren von onedrive finden Sie in der Office-Dokumentation unter [Einrichten von onedrive in Office 365](https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb).

#### <a name="configuration-for-users"></a>Konfiguration für Benutzer
Erteilen Sie den Benutzern die folgenden Anweisungen, damit Sie Ihr onedrive zum Schutz Ihrer Geschäftsdateien konfigurieren können.

1. Melden Sie sich bei Office 365 mit Ihrem Geschäfts-, Schul- oder Unikonto an, und wechseln Sie zur [OneDrive-Website](https://admin.microsoft.com/onedrive).

2. Wählen Sie im Navigationsbereich unten **Zurück zum klassischen OneDrive** aus.

3. Klicken Sie auf das Symbol **Einstellungen**. Aktivieren Sie im Bereich **Einstellungen** das **Menüband**, falls dafür bisher die Einstellung **Aus** verwendet wird.

4. Wenn Sie alle zu schützenden onedrive-Dateien konfigurieren möchten, wählen Sie im Menüband die Registerkarte **Bibliothek** aus, und klicken Sie dann auf **Bibliotheks Einstellungen**.

5. Wählen Sie auf der Seite **Dokumente > Einstellungen** im Bereich **Berechtigungen und Verwaltung** die Option **Information Rights Management** aus.

6. Aktivieren Sie auf der Seite **Information Rights Management-Einstellungen** das Kontrollkästchen neben **Berechtigungen für diese Bibliothek beim Herunterladen einschränken**. Geben Sie den gewünschten Namen und eine Beschreibung der Berechtigungen an, und klicken Sie optional auf **OPTIONEN ANZEIGEN**, um zusätzliche Konfigurationen einzurichten. Klicken Sie danach auf **OK**.

    Weitere Informationen zu den Konfigurationsoptionen finden Sie in der Office-Dokumentation in den Anweisungen unter [Anwenden der Verwaltung von Informationsrechten auf eine Liste oder Bibliothek](https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1).

Da diese Konfiguration von Benutzern anstelle eines Administrators abhängig ist, um Ihre onedrive-Dateien zu schützen, informieren Sie die Benutzer über die Vorteile des Datei Schutzes und über die entsprechende Vorgehensweise. Erklären Sie sich beispielsweise, dass bei der Freigabe eines Dokuments aus onedrive nur Personen, die Sie autorisieren, mit den von Ihnen konfigurierten Einschränkungen darauf zugreifen können, selbst wenn die Datei umbenannt und an eine andere Stelle kopiert wurde.

#### <a name="configuration-for-administrators"></a>Konfiguration für Administratoren
Sie können das Benutzerkonto für onedrive nicht mithilfe des SharePoint admin Centers konfigurieren, aber Sie können dazu Windows PowerShell verwenden. Führen Sie zum Aktivieren von IRM für diese Bibliotheken die folgenden Schritte aus:

1. Laden Sie das [SharePoint Client Components SDK](https://www.microsoft.com/en-us/download/details.aspx?id=42038)herunter, und installieren Sie es.

2. Installieren Sie die [SharePoint-Verwaltungsshell](https://www.microsoft.com/en-us/download/details.aspx?id=35588), und installieren Sie Sie.

3. Kopieren Sie den Inhalt des folgenden Skripts, und nennen Sie die Datei „Set-IRMOnOneDriveForBusiness.ps1“ auf Ihrem Computer.

   *&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Es wird in der vorliegenden Form ohne jegliche Gewährleistung bereitgestellt.

   ```
   # Requires Windows PowerShell version 3

   <#
     Description:

       Configures IRM policy settings for OneDrive and can also be used for SharePoint libraries and lists

    Script Installation Requirements:

      SharePoint Client Components SDK
      https://www.microsoft.com/en-us/download/details.aspx?id=42038

      SharePoint Management Shell
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
                   Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=42038"
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
                           Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=35588"
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

   # Add the credentials to the client context and SharePoint service connection

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

   # connect to Office365 first, required for SharePoint cmdlets to run

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

4. Sehen Sie sich das Skript an, und nehmen Sie folgende Änderungen vor:

   1. Suchen Sie nach `$sharepointAdminCenterUrl`, und ersetzen Sie den Beispielwert durch die URL Ihres eigenen SharePoint Admin Centers.

      Sie finden diesen Wert als Basis-URL, wenn Sie zum SharePoint Admin Center wechseln und das folgende Format aufweist: https://<em> &lt; tenant_name &gt; </em>-admin.SharePoint.com

      Wenn der Mandanten Name beispielsweise "Configuration Manager" lautet, geben Sie Folgendes an:**https://contoso-admin.sharepoint.com**

   2. Suchen Sie nach `$tenantAdmin`, und ersetzen Sie den Beispielwert durch Ihr eigenes, vollqualifiziertes globales Administratorkonto für Office 365.

      Dieser Wert entspricht dem Wert, mit dem Sie sich beim Microsoft 365 Admin Center als globaler Administrator anmelden, und hat das folgende Format: user_name@ Mandanten* &lt; Domänen Name &gt; *. com

      Wenn der Benutzername des globalen Administrators von Office 365 z. b. "admin" für die Mandanten Domäne "contoso.com" lautet, geben Sie Folgendes an:<strong>admin@contoso.com</strong>

   3. Suchen `$webUrls` und ersetzen Sie die Beispiel Werte durch die onedrive-Web-URLs Ihrer Benutzer, indem Sie beliebig viele Einträge hinzufügen oder löschen.

      Falls Sie stattdessen eine CSV-Datei mit allen zu konfigurierenden URLs importieren möchten, informieren Sie sich anhand der Kommentare im Skript über die entsprechende Vorgehensweise.  Wir haben ein weiteres Beispielskript bereitgestellt, mit dem Sie automatisch nach den URLs für die CSV-Datei suchen und sie extrahieren können. Wenn Sie dazu bereit sind, verwenden Sie das [zusätzliche Skript, um alle onedrive-URLs an einen auszugeben. Abschnitt CSV-Datei](#additional-script-to-output-all-onedrive-urls-to-a-csv-file) direkt nach diesen Schritten.

      Die Web-URL für das onedrive des Benutzers weist das folgende Format auf: https://<em> &lt; Tenant &gt; Name</em>-My.SharePoint.com/Personal/* &lt; user_name &gt; *_* &lt; Tenant &gt; Name*_com

      Wenn z. b. der Benutzer im Mandanten "%%% quot;" den Benutzernamen "rsimone" hat, geben Sie Folgendes an:**https://contoso-my.sharepoint.com/personal/rsimone_contoso_com**

   4. Da wir das Skript verwenden, um onedrive zu konfigurieren, ändern Sie nicht den Wert der **Dokumente** für die `$listTitle` Variable.

   5. Suchen Sie nach `ADMIN INSTRUCTIONS`. Wenn Sie keine Änderungen an diesem Abschnitt vornehmen, wird das onedrive des Benutzers für "TSM" mit dem Richtlinien Titel "geschützte Dateien" und der Beschreibung "Diese Richtlinie schränkt den Zugriff auf autorisierte Benutzer einschränken" konfiguriert.  Es werden keine weiteren IRM-Optionen festgelegt, was für die meisten Umgebungen angemessen sein dürfte. Sie können den vorgeschlagenen Richtlinientitel und die Beschreibung jedoch ändern und außerdem alle anderen IRM-Optionen hinzufügen, die für Ihre Umgebung geeignet sind. Informationen, die Ihnen dabei helfen, Ihren eigenen Satz von Parametern für den Befehl „Set-IrmConfiguration“ zu erstellen, finden Sie im kommentierten Beispiel innerhalb des Skripts.

5. Speichern Sie das Skript, und signieren Sie es. Die Signatur erhöht die Sicherheit. Wenn Sie das Skript nicht signieren, muss Windows PowerShell auf Ihrem Computer für die Ausführung nicht signierter Skripts konfiguriert werden. Führen Sie hierzu eine Windows PowerShell-Sitzung mit der Option **Als Administrator ausführen** aus, und geben Sie Folgendes ein: **Set-ExecutionPolicy Unrestricted**. Bei dieser Konfiguration können allerdings alle nicht signierten Skripts ausgeführt werden, was weniger sicher ist.

   Weitere Informationen zum Signieren von Windows PowerShell-Skripts finden Sie in der PowerShell-Dokumentationsbibliothek unter [about_Signing](https://technet.microsoft.com/library/hh847874.aspx).

6. Führen Sie das Skript aus, und geben Sie das Kennwort für das Office-365-Administratorkonto ein, wenn Sie dazu aufgefordert werden. Wenn Sie das Skript ändern und es in der gleichen Windows PowerShell-Sitzung ausführen, werden Sie nicht zur Eingabe von Anmeldeinformationen aufgefordert.

> [!TIP]
> Sie können dieses Skript auch verwenden, um für eine SharePoint-Bibliothek "unm" zu konfigurieren. Für diese Konfiguration möchte Sie vermutlich die zusätzliche Option **Benutzer dürfen keine Dokumente hochladen, die IRM nicht unterstützen** aktivieren, um sicherzustellen, dass die Bibliothek nur geschützte Dokumente enthält.    Fügen Sie hierzu dem Befehl „Set-IrmConfiguration“ im Skript den Parameter `-IrmReject` hinzu.
>
> Außerdem müssen Sie die `$webUrls` Variable (z. b. **https: \/ /contoso.SharePoint.com**) und die `$listTitle` Variable (z. b. **$Reports**) ändern.

Wenn Sie "irren" für die onedrive-Bibliotheken eines Benutzers deaktivieren müssen, finden Sie weitere Informationen im Abschnitt [Skript zum Deaktivieren von "IRiM für onedrive](#script-to-disable-irm-for-onedrive) ".

##### <a name="additional-script-to-output-all-onedrive-urls-to-a-csv-file"></a>Zusätzliches Skript zum Ausgeben aller onedrive-URLs an eine. CSV-Datei
Für Schritt 4C weiter oben können Sie das folgende Windows PowerShell-Skript verwenden, um die URLs für die onedrive-Bibliotheken aller Benutzer zu extrahieren, die Sie dann überprüfen, ggf. Bearbeiten und dann in das Hauptskript importieren können.

Dieses Skript erfordert auch das [SharePoint-Client Komponenten-SDK](https://www.microsoft.com/en-us/download/details.aspx?id=42038) und die [SharePoint-Verwaltungsshell](https://www.microsoft.com/en-us/download/details.aspx?id=35588). Befolgen Sie die gleichen Anweisungen zum Kopieren und Einfügen, speichern Sie die Datei lokal (beispielsweise unter dem Namen „Report-OneDriveForBusinessSiteInfo.ps1“), ändern Sie wie zuvor die Werte `$sharepointAdminCenterUrl` und `$tenantAdmin`, und führen Sie anschließend das Skript aus.

*&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Es wird in der vorliegenden Form ohne jegliche Gewährleistung bereitgestellt.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Queries the search service of an Office 365 tenant to retrieve all OneDrive sites.  
    Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_<date>.csv").

 Script Installation Requirements:

   SharePoint Client Components SDK
   https://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Management Shell
   https://www.microsoft.com/en-us/download/details.aspx?id=35588

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
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=42038"
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
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=35588"
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

# Add the credentials to the client context and SharePoint service connection

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

# run a query against the Office 365 tenant search service to retrieve all OneDrive URLs

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

##### <a name="script-to-disable-irm-for-onedrive"></a>Skript zum Deaktivieren von "IRiM" für onedrive
Verwenden Sie das folgende Beispielskript, wenn Sie die "URM" für das onedrive der Benutzer deaktivieren müssen.

Dieses Skript erfordert auch das [SharePoint-Client Komponenten-SDK](https://www.microsoft.com/en-us/download/details.aspx?id=42038) und die [SharePoint-Verwaltungsshell](https://www.microsoft.com/en-us/download/details.aspx?id=35588). Kopieren Sie den Inhalt, und fügen Sie ihn ein. Speichern Sie die Datei lokal (beispielsweise unter dem Namen „Disable-IRMOnOneDriveForBusiness.ps1“), und ändern Sie die Werte `$sharepointAdminCenterUrl` und `$tenantAdmin`. Geben Sie die onedrive-URLs manuell an, oder verwenden Sie das Skript im vorherigen Abschnitt, damit Sie diese importieren können, und führen Sie dann das Skript aus.

*&#42;&#42;Haftungsausschluss&#42;&#42;*: Dieses Beispielskript wird unter keinem Microsoft-Standardsupportprogramm oder -dienst unterstützt. Es wird in der vorliegenden Form ohne jegliche Gewährleistung bereitgestellt.

```
# Requires Windows PowerShell version 3

<#
  Description:

    Disables IRM for OneDrive and can also be used for SharePoint libraries and lists

 Script Installation Requirements:

   SharePoint Client Components SDK
   https://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Management Shell
   https://www.microsoft.com/en-us/download/details.aspx?id=35588

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
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=42038"
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
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: https://www.microsoft.com/en-us/download/details.aspx?id=35588"
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

# Add the credentials to the client context and SharePoint service connection

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

# connect to Office365 first, required for SharePoint cmdlets to run

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

