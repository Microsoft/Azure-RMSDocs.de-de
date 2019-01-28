---
title: Verwalten personenbezogener Daten für Azure Information Protection
description: Informationen zu den personenbezogenen Daten, die von Azure Information Protection verwendet werden, und wie Sie diese anzeigen, exportieren und löschen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.openlocfilehash: 08ae5875437a1e443247a5a57b1bb621b6627ce3
ms.sourcegitcommit: cf52083dde756ad3620c05fc74f012d8a7abacf3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/24/2019
ms.locfileid: "54898782"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Verwalten personenbezogener Daten für Azure Information Protection

Wenn Sie Azure Information Protection konfigurieren und verwenden, werden E-Mail-Adressen und IP-Adressen von Azure Information Protection gespeichert und verwendet. Diese personenbezogenen Daten können Sie den folgenden Ressourcen entnehmen:

- Azure Information Protection-Richtlinie

- Schutzvorlagen für den Azure Rights Management-Dienst

- Administratoren und delegierte Administratoren des Azure Rights Management-Diensts 

- Administrationsprotokolle des Azure Rights Management-Diensts

- Verwendungsprotokolle des Azure Rights Management-Diensts

- Dokumentnachverfolgungsprotokolle

- Verwendungsprotokolle des Azure Information Protection- und RMS-Clients 


[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Anzeigen personenbezogener Daten, die von Azure Information Protection verwendet werden

Ein Administrator kann über das Azure-Portal E-Mail-Adressen für Richtlinien mit einem bestimmten Geltungsbereich und für Schutzeinstellungen innerhalb einer Bezeichnungskonfiguration angeben. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Für Bezeichnungen, die so konfiguriert sind, dass sie Schutz über den Azure Rights Management-Dienst anwenden, können E-Mail-Adressen auch in Schutzvorlagen mithilfe von PowerShell-Cmdlets des [AADRM-Moduls](/powershell/module/aadrm) gefunden werden. Mit diesem PowerShell-Modul können Administratoren außerdem Benutzer anhand deren E-Mail-Adressen als [Administrator](configure-super-users.md) oder als Administrator für den Azure Rights Management-Dienst festlegen. 

Wenn Azure Information Protection verwendet wird, um Dokumente und E-Mails zu klassifizieren und schützen, werden E-Mail-Adressen und IP-Adressen von Benutzern möglicherweise in Protokolldateien gespeichert.


### <a name="protection-templates"></a>Schutzvorlagen

Führen Sie das Cmdlet [Get-AadrmTemplate](/powershell/module/aadrm/get-aadrmtemplate) aus, um eine Liste von Schutzvorlagen zu erhalten. Sie können mit der Vorlagen-ID Details zu einer bestimmten Vorlage abfragen. Das `RightsDefinitions`-Objekt zeigt personenbezogene Daten an, falls diese vorhanden sind. 

Beispiel:
```
PS C:\Users> Get-AadrmTemplate -TemplateId fcdbbc36-1f48-48ca-887f-265ee1268f51 | select *


TemplateId              : fcdbbc36-1f48-48ca-887f-265ee1268f51
Names                   : {1033 -> Confidential}
Descriptions            : {1033 -> This data includes sensitive business information. Exposing this data to
                          unauthorized users may cause damage to the business. Examples for Confidential information
                          are employee information, individual customer projects or contracts and sales account data.}
Status                  : Archived
RightsDefinitions       : {admin@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT,
                          REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER,
                          AllStaff-7184AB3F-CCD1-46F3-8233-3E09E9CF0E66@aip500.onmicrosoft.com -> VIEW,
                          VIEWRIGHTSDATA, EDIT, DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT,
                          EDITRIGHTSDATA, OBJMODEL, OWNER, admin2@aip500.onmicrosoft.com -> VIEW, VIEWRIGHTSDATA, EDIT,
                          DOCEDIT, PRINT, EXTRACT, REPLY, REPLYALL, FORWARD, EXPORT, EDITRIGHTSDATA, OBJMODEL, OWNER}
ContentExpirationDate   : 1/1/0001 12:00:00 AM
ContentValidityDuration : 0
ContentExpirationOption : Never
LicenseValidityDuration : 7
ReadOnly                : False
LastModifiedTimeStamp   : 1/26/2018 6:17:00 PM
ScopedIdentities        : {}
EnableInLegacyApps      : False
LabelId                 :
```

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Administratoren und delegierte Administratoren des Azure Rights Management-Diensts

Führen Sie die Cmdlets [Get-AadrmSuperUser](/powershell/module/aadrm/get-aadrmsuperuser) und [Get-AadrmRoleBasedAdministrator](/powershell/module/aadrm/get-aadrmrolebasedadministrator) aus, um anzuzeigen, welchen Benutzern die Administratorrolle oder die Rolle des globalen Administrators für den Azure Rights Management-Dienst zugewiesen wurde. Die E-Mail-Adressen der Benutzer, denen eine dieser Rollen zugewiesen wurde, werden angezeigt.


### <a name="administration-logs-for-the-azure-rights-management-service"></a>Administrationsprotokolle des Azure Rights Management-Diensts

Führen Sie das Cmdlet [Get-AadrmAdminLog](/powershell/module/aadrm/get-aadrmadminlog) aus, um ein Protokoll der Administratoraktionen für den Azure Rights Management-Dienst abzurufen, wodurch Daten von Azure Information Protection geschützt werden. Dieses Protokoll enthält personenbezogene Daten in der Form von E-Mail-Adressen und IP-Adressen. Das Protokoll ist im Klartextformat. Nachdem es heruntergeladen wurde, können die genauen Angaben eines bestimmten Administrators offline gesucht werden.

Beispiel:
```
PS C:\Users> Get-AadrmAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-azure-rights-management-service"></a>Verwendungsprotokolle des Azure Rights Management-Diensts
Führen Sie das Cmdlet [Get-AadrmUserLog](/powershell/module/aadrm/get-aadrmuserlog) aus, um ein Protokoll von Endbenutzeraktionen abzurufen, die den Azure Rights Management-Dienst verwenden. Dieser Dienst schützt Daten für Azure Information Protection. Dieses Protokoll enthält möglicherweise personenbezogene Daten in der Form von E-Mail-Adressen und IP-Adressen. Das Protokoll ist im Klartextformat. Nachdem es heruntergeladen wurde, können die genauen Angaben eines bestimmten Administrators offline gesucht werden.

Beispiel:
```
PS C:\Users> Get-AadrmUserLog -Path '.\Desktop\' -FromDate 4/1/2018 -ToDate 4/30/2018 -NumberOfThreads 10
Acquiring access to your user log…
Downloading the log for 2018-04-01.
Downloading the log for 2018-04-03.
Downloading the log for 2018-04-06.
Downloading the log for 2018-04-09.
Downloading the log for 2018-04-10.
Downloaded the log for 2018-04-01. The log is available at .\Desktop\rmslog-2018-04-01.log.
Downloaded the log for 2018-04-03. The log is available at .\Desktop\rmslog-2018-04-03.log.
Downloaded the log for 2018-04-06. The log is available at .\Desktop\rmslog-2018-04-06.log.
Downloaded the log for 2018-04-09. The log is available at .\Desktop\rmslog-2018-04-09.log.
Downloaded the log for 2018-04-10. The log is available at .\Desktop\rmslog-2018-04-10.log.
Downloading the log for 2018-04-12.
Downloading the log for 2018-04-13.
Downloading the log for 2018-04-14.
Downloading the log for 2018-04-16.
Downloading the log for 2018-04-18.
Downloaded the log for 2018-04-12. The log is available at .\Desktop\rmslog-2018-04-12.log.
Downloaded the log for 2018-04-13. The log is available at .\Desktop\rmslog-2018-04-13.log.
Downloaded the log for 2018-04-14. The log is available at .\Desktop\rmslog-2018-04-14.log.
Downloaded the log for 2018-04-16. The log is available at .\Desktop\rmslog-2018-04-16.log.
Downloaded the log for 2018-04-18. The log is available at .\Desktop\rmslog-2018-04-18.log.
Downloading the log for 2018-04-24.
Downloaded the log for 2018-04-24. The log is available at .\Desktop\rmslog-2018-04-24.log.
```   

### <a name="document-tracking-logs"></a>Dokumentnachverfolgungsprotokolle

Führen Sie das Cmdlet [Get-AadrmDocumentLog](/powershell/module/aadrm/get-aadrmdocumentlog) aus, um Informationen zu einem bestimmten Benutzer von der Website zur Dokumentnachverfolgung abzurufen. Verwenden Sie das Cmdlet [Get-AadrmTrackingLog](/powershell/module/aadrm/get-aadrmtrackinglog?view=azureipps), um mit dem Dokumentprotokoll in Verbindung stehende Nachverfolgungsinformationen abzurufen.

Beispiel:
```
PS C:\Users> Get-AadrmDocumentLog -UserEmail "admin@aip500.onmicrosoft.com"


ContentId             : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer                : admin@aip500.onmicrosoft.com
Owner                 : admin@aip500.onmicrosoft.com
ContentName           :
CreatedTime           : 3/6/2018 10:24:00 PM
Recipients            : {
                        PrimaryEmail: johndoe@contoso.com
                        DisplayName: JOHNDOE@CONTOSO.COM
                        UserType: External,
                        PrimaryEmail: alice@contoso0110.onmicrosoft.com
                        DisplayName: ALICE@CONTOSO0110.ONMICROSOFT.COM
                        UserType: External
                        }
TemplateId            :
PolicyExpires         :
EULDuration           :
SendRegistrationEmail : True
NotificationInfo      : Enabled: False
                        DeniedOnly: False
                        Culture:
                        TimeZoneId:
                        TimeZoneOffset: 0
                        TimeZoneDaylightName:
                        TimeZoneStandardName:

RevocationInfo        : Revoked: False
                        RevokedTime:
                        RevokedBy:


PS C:\Users> Get-AadrmTrackingLog -UserEmail "admin@aip500.onmicrosoft.com"

ContentId            : 6326fcb2-c465-4c24-a7f6-1cace7a9cb6f
Issuer               : admin@aip500.onmicrosoft.com
RequestTime          : 3/6/2018 10:45:57 PM
RequesterType        : External
RequesterEmail       : johndoe@contoso.com
RequesterDisplayName : johndoe@contoso.com
RequesterLocation    : IP: 167.220.1.54
                       Country: US
                       City: redmond
                       Position: 47.6812453974602,-122.120736471666

Rights               : {VIEW,OBJMODEL}
Successful           : False
IsHiddenInfo         : False
```

Sie können nicht nach ObjectID suchen. Sie werden jedoch nicht vom Parameter `-UserEmail` eingeschränkt. Die E-Mail-Adresse, die Sie angeben, muss nicht Teil Ihres Mandanten sein. Wenn die angegebene E-Mail-Adresse an einer Stelle in den Dokumentnachverfolgungsprotokollen gespeichert ist, wird der Dokumentnachverfolgungseintrag in der Cmdlet-Ausgabe zurückgegeben.

### <a name="usage-logs-for-the-azure-information-protection-client-and-rms-client"></a>Verwendungsprotokolle des Azure Information Protection- und RMS-Clients

Wenn Bezeichnungen und Schutz auf Dokumente und E-Mails angewendet werden, werden E-Mail-Adressen und IP-Adressen möglicherweise in Protokolldateien auf dem Computer des Benutzers an den folgenden Stellen gespeichert:

- Azure Information Protection-Client: %localappdata%\Microsoft\MSIP\Logs

- RMS-Client: %localappdata%\Microsoft\MSIPC\msip\Logs

Zusätzlich protokolliert der Azure Information Protection-Client diese personebezogenen Daten im lokalen Windows-Ereignisprotokoll unter **Anwendungen und Dienstprotokolle** > **Azure Information Protection**.

Wenn der Azure Information Protection-Client den Scanner ausführt, werden personenbezogene Daten auf dem Windows Server-Computer, der den Scanner ausführt, unter %localappdata%\Microsoft\MSIP\Scanner\Reports gespeichert.

Sie können das Protokollieren von Informationen für den Azure Information Protection-Client und den Scanner mithilfe der folgenden Konfigurationen deaktivieren:

- Für den Azure Information Protection-Client: Erstellen Sie eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#change-the-local-logging-level), mit der **LogLevel** auf **Off** gesetzt wird.

- Für den Azure Information Protection-Scanner: Verwenden Sie das Cmdlet [Set-AIPScannerConfiguration](/azureinformationprotection/set-aipscannerconfiguration), um den Parameter *ReportLevel* auf **Off** zu setzen.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Sichern und Steuern des Zugriffs auf personenbezogene Informationen
Auf die personenbezogenen Daten, die Sie im Azure-Portal anzeigen und angeben, kann nur von Benutzern zugegriffen werden, denen eine der folgenden [Administratorrollen für Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) zugewiesen wurde:
    
- **Information Protection-Administrator**

- **Sicherheitsadministrator**

- **Globaler Administrator/Unternehmensadministrator**

Auf personenbezogene Daten, die Sie mithilfe des AADRM-Moduls anzeigen und angeben, kann nur von den Benutzern zugegriffen werden, denen die Rolle **Information Protection-Administrator** oder **Globaler Administrator bzw. Unternehmensadministrator** in Azure Active Directory oder die Rolle „Globaler Administrator“ im Azure Rights Management-Dienst zugewiesen wurde.  

## <a name="updating-personal-data"></a>Aktualisieren von personenbezogenen Daten

Sie können E-Mail-Adressen für bereichsbezogene Richtlinien und Schutzeinstellungen in der Azure Information Protection-Richtlinie aktualisieren. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Für die Schutzeinstellungen können Sie diese Informationen aktualisieren, indem Sie PowerShell-Cmdlets über das [AADRM-Modul](/powershell/module/aadrm) verwenden.

Sie können keine E-Mail-Adressen für Administratoren und delegierte Administratoren aktualisieren. Entfernen Sie stattdessen das angegebene Benutzerkonto, und fügen Sie das Benutzerkonto mit der aktualisierten E-Mail-Adresse erneut hinzu. 

### <a name="protection-templates"></a>Schutzvorlagen

Führen Sie das Cmdlet [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) aus, um die Schutzvorlage zu aktualisieren. Da die personenbezogenen Daten sich in der Eigenschaft `RightsDefinitions` befinden, müssen Sie ebenfalls das Cmdlet [New-AadrmRightsDefinition](/powershell/module/aadrm/new-aadrmrightsdefinition) verwenden, um ein RightsDefinitions-Objekt mit den aktualisierten Informationen zu erstellen und dieses mit dem `Set-AadrmTemplateProperty`-Cmdlet verwenden.

### <a name="super-users-and-delegated-administrators-for-the-azure-rights-management-service"></a>Administratoren und delegierte Administratoren des Azure Rights Management-Diensts

Wenn Sie die E-Mail-Adresse eines Administrators aktualisieren müssen:

1. Verwenden Sie [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser), um den Benutzer und die alte E-Mail-Adresse zu entfernen.

2. Verwenden Sie [Add-AadrmSuperUser](/powershell/module/aadrm/Add-AadrmSuperUser), um den Benutzer und die neue E-Mail-Adresse hinzuzufügen.

Wenn Sie die E-Mail-Adresse eines delegierten Administrators aktualisieren müssen:

1. Verwenden Sie [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator), um den Benutzer und die alte E-Mail-Adresse zu entfernen.

2. Verwenden Sie [Add-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Add-AadrmRoleBasedAdministrator), um den Benutzer und die neue E-Mail-Adresse hinzuzufügen.

## <a name="deleting-personal-data"></a>Löschen von personenbezogenen Daten
Sie können E-Mail-Adressen für bereichsbezogene Richtlinien und Schutzeinstellungen in der Azure Information Protection-Richtlinie löschen. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Für die Schutzeinstellungen können Sie diese Informationen löschen, indem Sie PowerShell-Cmdlets über das [AADRM-Modul](/powershell/module/aadrm) verwenden.

Wenn Sie die E-Mail-Adressen von Administratoren und delegierten Administratoren löschen möchten, entfernen Sie diese Benutzer, indem Sie die Cmdlets [Remove-AadrmSuperUser](/powershell/module/aadrm/Remove-AadrmSuperUser) und [Remove-AadrmRoleBasedAdministrator](/powershell/module/aadrm/Remove-AadrmRoleBasedAdministrator) verwenden. 

Wenn Sie personenbezogene Daten in Dokumentnachverfolgungsprotokollen, Verwaltungsprotokollen oder Nutzungsprotokollen des Azure Rights Management-Diensts löschen möchten, finden Sie im folgenden Abschnitt weitere Informationen zum Stellen einer Anforderung an den Microsoft-Support.

Wenn Sie personenbezogene Daten in den Clientprotokolldateien und in den Scannerprotokollen löschen möchten, die auf den Computern gespeichert sind, verwenden Sie beliebige Windows-Standardtools, um die Dateien oder personenbezogene Daten aus den Dateien zu löschen. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Löschen personenbezogener Daten mit dem Microsoft-Support

Befolgen Sie diese drei Schritte, um anzufordern, dass Microsoft personenbezogene Daten aus Dokumentnachverfolgungsprotokollen, Verwaltungsprotokollen oder Nutzungsprotokollen des Azure Rights Management-Diensts löscht. 

**Schritt 1: Initiieren der Löschanforderung**
[Wenden Sie sich an den Microsoft-Support](information-support.md#to-contact-microsoft-support), und öffnen Sie eine Azure Information Protection-Supportanfrage für das Löschen von Daten aus Ihrem Mandanten. Sie müssen nachweisen, dass Sie der Administrator des Azure Information Protection-Mandanten sind. Beachten Sie, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Während Sie Ihre Anforderung übermitteln, müssen Sie zusätzliche Informationen bereitstellen, die von den Daten abhängig sind, die gelöscht werden sollen.

- Wenn Sie das Verwaltungsprotokoll löschen möchten, stellen Sie das **Enddatum** bereit. Alle Verwaltungsprotokolle bis zu diesem Enddatum werden gelöscht.
- Wenn Sie Nutzungsprotokolle löschen möchten, stellen Sie das **Enddatum** bereit. Alle Nutzungsprotokolle bis zu diesem Enddatum werden gelöscht.
- Wenn Sie die Dokumentnachverfolgungsprotokolle löschen möchten, stellen Sie die **E-Mail-Adresse des Benutzers** bereit. Alle Informationen der Dokumentnachverfolgung, die mit der E-Mail-Adresse dieses Benutzers in Zusammenhang stehen, werden gelöscht.

Diese Daten werden dauerhaft gelöscht. Sie können nicht wiederhergestellt werden, sobald die Löschanforderung durchgeführt wurde. Es wird empfohlen, dass Administratoren die erforderlichen Daten exportieren, bevor eine Löschanforderung übermittelt wird.

**Schritt 2: Warten auf Überprüfung** Microsoft überprüft, ob Ihre Löschanforderung für ein oder mehrere Protokolle legitim ist. Der Vorgang kann bis zu fünf Werktagen dauern.

**Schritt 3: Bestätigung der Löschung** Sie erhalten eine E-Mail von Microsoft Customer Support Services (CSS), in der bestätigt wird, dass die Daten gelöscht wurden. 

## <a name="exporting-personal-data"></a>Exportieren von personenbezogenen Daten
Wenn Sie die AADRM-PowerShell-Cmdlets verwenden, können personenbezogene Daten gesucht und als PowerShell-Objekt exportiert werden. Das PowerShell-Objekt kann in das JSON-Format konvertiert und mithilfe des `ConvertTo-Json`-Cmdlets gespeichert werden.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Einschränken der Verwendung von personenbezogenen Daten für die Profilerstellung oder für Marketing ohne Zustimmung
Azure Information Protection befolgt die [Datenschutzrichtlinien](https://privacy.microsoft.com/privacystatement) von Microsoft für die Profilerstellung oder für Marketing auf Grundlage von personenbezogenen Daten.

## <a name="auditing-and-reporting"></a>Nachverfolgung und Berichterstellung
Nur Benutzer mit [Administratorberechtigungen](#securing-and-controlling-access-to-personal-information) können das AADRM-Modul für die Suche nach und das Exportieren von personenbezogenen Daten verwenden. Diese Vorgänge werden im Verwaltungsprotokoll aufgezeichnet. Dieses können Sie herunterladen.

Bei Löschaktionen fungiert die Supportanforderung als Nachverfolgung und Berichterstellung für von Microsoft durchgeführte Aktionen. Gelöschte Daten können nicht mehr gesucht und exportiert werden. Der Administrator kann dies überprüfen, indem er die Get-Cmdlets des AADRM-Moduls verwendet.

