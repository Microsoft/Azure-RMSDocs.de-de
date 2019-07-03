---
title: Verwalten personenbezogener Daten für Azure Information Protection
description: Informationen zu den personenbezogenen Daten, die von Azure Information Protection verwendet werden, und wie Sie diese anzeigen, exportieren und löschen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.openlocfilehash: 900b447f67bab09e0cfcb2ed243f2c6a3de71135
ms.sourcegitcommit: a5f595f8a453f220756fdc11fd5d466c71d51963
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67521185"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Verwalten personenbezogener Daten für Azure Information Protection

Wenn Sie Azure Information Protection konfigurieren und verwenden, werden E-Mail-Adressen und IP-Adressen von Azure Information Protection gespeichert und verwendet. Diese personenbezogenen Daten können Sie den folgenden Ressourcen entnehmen:

- Azure Information Protection-Richtlinie

- Vorlagen für den Schutzdienst

- Administratoren und delegierte Administratoren für den Schutzdienst 

- Verwaltung von Protokolle für den Schutzdienst

- Protokolle für den Schutzdienst

- Dokumentnachverfolgungsprotokolle

- Protokolle für die Azure Information Protection-Clients und die RMS-client 


[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Anzeigen personenbezogener Daten, die von Azure Information Protection verwendet werden

Ein Administrator kann über das Azure-Portal E-Mail-Adressen für Richtlinien mit einem bestimmten Geltungsbereich und für Schutzeinstellungen innerhalb einer Bezeichnungskonfiguration angeben. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Bezeichnungen, die konfiguriert sind, um aus dem Azure Rights Management-Dienst-Schutz anzuwenden, e-Mail-Adresse kann auch finden Sie im schutzvorlagen, mithilfe von PowerShell-Cmdlets aus dem [AIPService Modul](/powershell/module/aipservice). Mit diesem PowerShell-Modul können Administratoren außerdem Benutzer anhand deren E-Mail-Adressen als [Administrator](configure-super-users.md) oder als Administrator für den Azure Rights Management-Dienst festlegen. 

Wenn Azure Information Protection verwendet wird, um Dokumente und E-Mails zu klassifizieren und schützen, werden E-Mail-Adressen und IP-Adressen von Benutzern möglicherweise in Protokolldateien gespeichert.


### <a name="protection-templates"></a>Schutzvorlagen

Führen Sie die [Get-AipServiceTemplate](/powershell/module/aipservice/get-aipservicetemplate) -Cmdlet zum Abrufen einer Liste von schutzvorlagen. Sie können mit der Vorlagen-ID Details zu einer bestimmten Vorlage abfragen. Das `RightsDefinitions`-Objekt zeigt personenbezogene Daten an, falls diese vorhanden sind. 

Beispiel:
```
PS C:\Users> Get-AipServiceTemplate -TemplateId fcdbbc36-1f48-48ca-887f-265ee1268f51 | select *


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

### <a name="super-users-and-delegated-administrators-for-the-protection-service"></a>Administratoren und delegierte Administratoren für den Schutzdienst

Führen Sie die [Get-AipServiceSuperUser](/powershell/module/aipservice/get-aipservicesuperuser) Cmdlet und [Get-Aipservicerolebasedadministrator](/powershell/module/aipservice/get-aipservicerolebasedadministrator) Cmdlet, um anzuzeigen, welche Benutzer der Administrator-Rolle oder globaler Administrator für den Schutz zugewiesen wurden Dienst (Azure Rights Management) von Azure Information Protection. Die E-Mail-Adressen der Benutzer, denen eine dieser Rollen zugewiesen wurde, werden angezeigt.


### <a name="administration-logs-for-the-protection-service"></a>Verwaltung von Protokolle für den Schutzdienst

Führen Sie die [Get-AipServiceAdminLog](/powershell/module/aipservice/get-aipserviceadminlog) -Cmdlet zum Abrufen eines Protokolls der Administratoraktionen für den Schutzdienst (Azure Rights Management) von Azure Information Protection. Dieses Protokoll enthält personenbezogene Daten in der Form von E-Mail-Adressen und IP-Adressen. Das Protokoll ist im Klartextformat. Nachdem es heruntergeladen wurde, können die genauen Angaben eines bestimmten Administrators offline gesucht werden.

Zum Beispiel:
```
PS C:\Users> Get-AipServiceAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-protection-service"></a>Protokolle für den Schutzdienst
Führen Sie die [Get-AipServiceUserLog](/powershell/module/aipservice/get-aipserviceuserlog) Cmdlet, um ein Protokoll der Endbenutzeraktionen abzurufen, die den Schutzdienst von Azure Information Protection zu verwenden. Dieses Protokoll enthält möglicherweise personenbezogene Daten in der Form von E-Mail-Adressen und IP-Adressen. Das Protokoll ist im Klartextformat. Nachdem es heruntergeladen wurde, können die genauen Angaben eines bestimmten Administrators offline gesucht werden.

Zum Beispiel:
```
PS C:\Users> Get-AipServiceUserLog -Path '.\Desktop\' -FromDate 4/1/2018 -ToDate 4/30/2018 -NumberOfThreads 10
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

Führen Sie die [Get-AipServiceDocumentLog](/powershell/module/aipservice/get-aipservicedocumentlog) -Cmdlet zum Abrufen von Informationen aus der Website zu einem bestimmten Benutzer für die dokumentnachverfolgung. Um den Dokument-Protokollen zugeordnet änderungsnachverfolgungsinformationen abzurufen, verwenden Sie die [Get-AipServiceTrackingLog](/powershell/module/aipservice/get-aipservicetrackinglog?view=azureipps) Cmdlet.

Zum Beispiel:
```
PS C:\Users> Get-AipServiceDocumentLog -UserEmail "admin@aip500.onmicrosoft.com"


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


PS C:\Users> Get-AipServiceTrackingLog -UserEmail "admin@aip500.onmicrosoft.com"

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

### <a name="usage-logs-for-the-azure-information-protection-clients-and-rms-client"></a>Protokolle für die Azure Information Protection-Clients und die RMS-client

Wenn Bezeichnungen und Schutz auf Dokumente und E-Mails angewendet werden, werden E-Mail-Adressen und IP-Adressen möglicherweise in Protokolldateien auf dem Computer des Benutzers an den folgenden Stellen gespeichert:

- Für den Azure Information Protection-unified-bezeichnungs-Client und der Azure Information Protection-Client: %localappdata%\Microsoft\MSIP\Logs

- RMS-Client: %localappdata%\Microsoft\MSIPC\msip\Logs

Zusätzlich protokolliert der Azure Information Protection-Client diese personebezogenen Daten im lokalen Windows-Ereignisprotokoll unter **Anwendungen und Dienstprotokolle** > **Azure Information Protection**.

Wenn der Azure Information Protection-Client den Scanner ausführt, werden personenbezogene Daten auf dem Windows Server-Computer, der den Scanner ausführt, unter %localappdata%\Microsoft\MSIP\Scanner\Reports gespeichert.

Sie können das Protokollieren von Informationen für den Azure Information Protection-Client und den Scanner mithilfe der folgenden Konfigurationen deaktivieren:

- Für den Azure Information Protection-Client: Erstellen Sie eine [erweiterte Clienteinstellung](./rms-client/client-admin-guide-customizations.md#change-the-local-logging-level), mit der **LogLevel** auf **Off** gesetzt wird.

- Für die Azure Information Protection-Überprüfung: Verwenden Sie das Cmdlet [Set-AIPScannerConfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration), um den Parameter *ReportLevel* auf **Off** zu setzen.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Sichern und Steuern des Zugriffs auf personenbezogene Informationen
Auf die personenbezogenen Daten, die Sie im Azure-Portal anzeigen und angeben, kann nur von Benutzern zugegriffen werden, denen eine der folgenden [Administratorrollen für Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) zugewiesen wurde:
    
- **Azure Information Protection-administrator**

- **Complianceadministrator**

- **Complianceadministrator-Daten**

- **Sicherheitsadministrator**

- **Globaler Administrator**

Personenbezogene Daten, die Sie anzeigen und angeben, indem Sie das Modul AIPService (oder das ältere Modul AADRM) steht ausschließlich Benutzer, die zugewiesen wurden die **Azure Information Protection-Administrator**, **Compliance Administrator**, **Daten complianceadministrator**, oder **globaler Administrator** Rollen in Azure Active Directory oder der globalen Administratorrolle für den Schutzdienst.

## <a name="updating-personal-data"></a>Aktualisieren von personenbezogenen Daten

Sie können E-Mail-Adressen für bereichsbezogene Richtlinien und Schutzeinstellungen in der Azure Information Protection-Richtlinie aktualisieren. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Sie können die gleiche Informationen mithilfe von PowerShell-Cmdlets aus aktualisieren, für die Einstellungen für den Schutz der [AIPService Modul](/powershell/module/aipservice).

Sie können keine E-Mail-Adressen für Administratoren und delegierte Administratoren aktualisieren. Entfernen Sie stattdessen das angegebene Benutzerkonto, und fügen Sie das Benutzerkonto mit der aktualisierten E-Mail-Adresse erneut hinzu. 

### <a name="protection-templates"></a>Schutzvorlagen

Führen Sie die [Set-AipServiceTemplateProperty](/powershell/module/aipservice/set-aipservicetemplateproperty) Cmdlet, um die schutzvorlage aktualisieren. Da die personenbezogenen Daten in ist die `RightsDefinitions` -Eigenschaft, müssen Sie auch mit der [New-AipServiceRightsDefinition](/powershell/module/aipservice/new-aipservicerightsdefinition) Cmdlet ein Objekt des Rechte-Definitionen mit den aktualisierten Informationen erstellen und verwenden Sie die Rechte Definitionen Objekt mit der `Set-AipServiceTemplateProperty` Cmdlet.

### <a name="super-users-and-delegated-administrators-for-the-protection-service"></a>Administratoren und delegierte Administratoren für den Schutzdienst

Wenn Sie die E-Mail-Adresse eines Administrators aktualisieren müssen:

1. Verwendung [Remove-AipServiceSuperUser](/powershell/module/aipservice/Remove-AipServiceSuperUser) um den Benutzer und die alte e-Mail-Adresse zu entfernen.

2. Verwendung [hinzufügen-AipServiceSuperUser](/powershell/module/aipservice/Add-AipServiceSuperUser) zum Hinzufügen der Benutzer und eine neue e-Mail-Adresse.

Wenn Sie die E-Mail-Adresse eines delegierten Administrators aktualisieren müssen:

1. Verwendung [Remove-AipServiceRoleBasedAdministrator](/powershell/module/aipservice/Remove-AipServiceRoleBasedAdministrator) um den Benutzer und die alte e-Mail-Adresse zu entfernen.

2. Verwendung [hinzufügen-AipServiceRoleBasedAdministrator](/powershell/module/aipservice/Add-AipServiceRoleBasedAdministrator) zum Hinzufügen der Benutzer und eine neue e-Mail-Adresse.

## <a name="deleting-personal-data"></a>Löschen von personenbezogenen Daten
Sie können E-Mail-Adressen für bereichsbezogene Richtlinien und Schutzeinstellungen in der Azure Information Protection-Richtlinie löschen. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Sie können die gleiche Informationen mithilfe von PowerShell-Cmdlets aus löschen, für die Einstellungen für den Schutz der [AIPService Modul](/powershell/module/aipservice).

Um e-Mail-Adressen für Administratoren und delegierte Administratoren löschen, entfernen Sie diese Benutzer mithilfe der [Remove-AipServiceSuperUser](/powershell/module/aipservice/Remove-AipServiceSuperUser) Cmdlet und [Remove-AipServiceRoleBasedAdministrator](/powershell/module/aipservice/Remove-AipServiceRoleBasedAdministrator). 

Verwenden Sie zum Löschen von personenbezogenen Daten in Protokollen, Verwaltung, Protokolle oder nutzungsprotokolle für den Schutzdienst zum Nachverfolgen von Dokumenten im folgenden Abschnitt zum Auslösen einer Anforderung für den Microsoft Support.

Wenn Sie personenbezogene Daten in den Clientprotokolldateien und in den Scannerprotokollen löschen möchten, die auf den Computern gespeichert sind, verwenden Sie beliebige Windows-Standardtools, um die Dateien oder personenbezogene Daten aus den Dateien zu löschen. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Löschen personenbezogener Daten mit dem Microsoft-Support

Verwenden Sie die folgenden drei Schritte, um anzufordern, dass Microsoft die personenbezogenen Daten in Protokollen, Verwaltung, Protokolle oder nutzungsprotokolle für den Schutzdienst zum Nachverfolgen von Dokumenten werden gelöscht. 

**Schritt 1: Initiieren der Löschanforderung**
[Wenden Sie sich an den Microsoft-Support](information-support.md#to-contact-microsoft-support), und öffnen Sie eine Azure Information Protection-Supportanfrage für das Löschen von Daten aus Ihrem Mandanten. Sie müssen nachweisen, dass Sie der Administrator des Azure Information Protection-Mandanten sind. Beachten Sie, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Während Sie Ihre Anforderung übermitteln, müssen Sie zusätzliche Informationen bereitstellen, die von den Daten abhängig sind, die gelöscht werden sollen.

- Wenn Sie das Verwaltungsprotokoll löschen möchten, stellen Sie das **Enddatum** bereit. Alle Verwaltungsprotokolle bis zu diesem Enddatum werden gelöscht.
- Wenn Sie Nutzungsprotokolle löschen möchten, stellen Sie das **Enddatum** bereit. Alle Nutzungsprotokolle bis zu diesem Enddatum werden gelöscht.
- Wenn Sie die Dokumentnachverfolgungsprotokolle löschen möchten, stellen Sie die **E-Mail-Adresse des Benutzers** bereit. Alle Informationen der Dokumentnachverfolgung, die mit der E-Mail-Adresse dieses Benutzers in Zusammenhang stehen, werden gelöscht.

Diese Daten werden dauerhaft gelöscht. Sie können nicht wiederhergestellt werden, sobald die Löschanforderung durchgeführt wurde. Es wird empfohlen, dass Administratoren die erforderlichen Daten exportieren, bevor eine Löschanforderung übermittelt wird.

**Schritt 2: Warten auf Überprüfung** Microsoft überprüft, ob Ihre Löschanforderung für ein oder mehrere Protokolle legitim ist. Der Vorgang kann bis zu fünf Werktagen dauern.

**Schritt 3: Bestätigung der Löschung** Sie erhalten eine E-Mail von Microsoft Customer Support Services (CSS), in der bestätigt wird, dass die Daten gelöscht wurden. 

## <a name="exporting-personal-data"></a>Exportieren von personenbezogenen Daten
Wenn Sie die AIPService oder AADRM-PowerShell-Cmdlets verwenden, werden die personenbezogenen Daten als ein PowerShell-Objekt für die Suche und Export verfügbar gemacht. Das PowerShell-Objekt kann in das JSON-Format konvertiert und mithilfe des `ConvertTo-Json`-Cmdlets gespeichert werden.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Einschränken der Verwendung von personenbezogenen Daten für die Profilerstellung oder für Marketing ohne Zustimmung
Azure Information Protection befolgt die [Datenschutzrichtlinien](https://privacy.microsoft.com/privacystatement) von Microsoft für die Profilerstellung oder für Marketing auf Grundlage von personenbezogenen Daten.

## <a name="auditing-and-reporting"></a>Nachverfolgung und Berichterstellung
Nur Benutzer, die zugewiesen wurden [Administratorberechtigungen](#securing-and-controlling-access-to-personal-information) können das Modul AIPService oder ADDRM für die Suche und Exportieren von persönlichen Daten. Diese Vorgänge werden im Verwaltungsprotokoll aufgezeichnet. Dieses können Sie herunterladen.

Bei Löschaktionen fungiert die Supportanforderung als Nachverfolgung und Berichterstellung für von Microsoft durchgeführte Aktionen. Nach dem Löschen die gelöschten Daten werden nicht zur Verfügung, für die Suche und Export, und der Administrator kann die Überprüfung dies mithilfe der Cmdlets "Get" aus dem Modul AIPService.
