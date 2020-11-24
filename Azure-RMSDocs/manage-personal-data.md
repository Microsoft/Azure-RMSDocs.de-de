---
title: Verwalten personenbezogener Daten für Azure Information Protection
description: Informationen zu den personenbezogenen Daten, die von Azure Information Protection verwendet werden, und wie Sie diese anzeigen, exportieren und löschen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/04/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 99a51862-83e9-4a1e-873a-a84ae1465f07
ms.reviewer: aashishr
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 89f46156ec8e22c0e44a99c9e3d8d5f79b260129
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567640"
---
# <a name="manage-personal-data-for-azure-information-protection"></a>Verwalten personenbezogener Daten für Azure Information Protection

Wenn Sie Azure Information Protection konfigurieren und verwenden, werden E-Mail-Adressen und IP-Adressen von Azure Information Protection gespeichert und verwendet. Diese personenbezogenen Daten können Sie den folgenden Ressourcen entnehmen:

- Azure Information Protection-Richtlinie

- Vorlagen für den Schutzdienst

- Administratoren und Delegierte Administratoren für den Schutzdienst 

- Verwaltungs Protokolle für den Schutzdienst

- Verwendungs Protokolle für den Schutzdienst

- Dokumentnachverfolgungsprotokolle

- Verwendungs Protokolle für die Azure Information Protection Clients und den RMS-Client 


[!INCLUDE [GDPR-related guidance](./includes/gdpr-intro-sentence.md)]


## <a name="viewing-personal-data-that-azure-information-protection-uses"></a>Anzeigen personenbezogener Daten, die von Azure Information Protection verwendet werden

Ein Administrator kann über das Azure-Portal E-Mail-Adressen für Richtlinien mit einem bestimmten Geltungsbereich und für Schutzeinstellungen innerhalb einer Bezeichnungskonfiguration angeben. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Für Bezeichnungen, die so konfiguriert sind, dass Sie Schutz von Azure Rights Management Service anwenden, kann die e-Mail-Adresse auch in Schutz Vorlagen mithilfe von PowerShell-Cmdlets aus dem [aipservice-Modul](/powershell/module/aipservice)gefunden werden. Mit diesem PowerShell-Modul können Administratoren außerdem Benutzer anhand deren E-Mail-Adressen als [Administrator](configure-super-users.md) oder als Administrator für den Azure Rights Management-Dienst festlegen. 

Wenn Azure Information Protection verwendet wird, um Dokumente und E-Mails zu klassifizieren und schützen, werden E-Mail-Adressen und IP-Adressen von Benutzern möglicherweise in Protokolldateien gespeichert.


### <a name="protection-templates"></a>Schutzvorlagen

Führen Sie das Cmdlet " [Get-aipservicetemplate](/powershell/module/aipservice/get-aipservicetemplate) " aus, um eine Liste mit Schutz Vorlagen zu erhalten. Sie können mit der Vorlagen-ID Details zu einer bestimmten Vorlage abfragen. Das `RightsDefinitions`-Objekt zeigt personenbezogene Daten an, falls diese vorhanden sind. 

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

### <a name="super-users-and-delegated-administrators-for-the-protection-service"></a>Administratoren und Delegierte Administratoren für den Schutzdienst

Führen Sie das Cmdlet [Get-aipservicesuperuser](/powershell/module/aipservice/get-aipservicesuperuser) und das Cmdlet [Get-aipservicerolebasedadministrator](/powershell/module/aipservice/get-aipservicerolebasedadministrator) aus, um anzuzeigen, welchen Benutzern die Rolle "Administrator" oder "globaler Administrator" für den Schutzdienst (Azure Rights Management) von Azure Information Protection zugewiesen wurde. Die E-Mail-Adressen der Benutzer, denen eine dieser Rollen zugewiesen wurde, werden angezeigt.


### <a name="administration-logs-for-the-protection-service"></a>Verwaltungs Protokolle für den Schutzdienst

Führen Sie das Cmdlet [Get-aipserviceadminlog](/powershell/module/aipservice/get-aipserviceadminlog) aus, um ein Protokoll der Administrator Aktionen für den Schutzdienst (Azure Rights Management) von Azure Information Protection zu erhalten. Dieses Protokoll enthält personenbezogene Daten in der Form von E-Mail-Adressen und IP-Adressen. Das Protokoll ist im Klartextformat. Nachdem es heruntergeladen wurde, können die genauen Angaben eines bestimmten Administrators offline gesucht werden.

Beispiel:
```
PS C:\Users> Get-AipServiceAdminLog -Path '.\Desktop\admin.log' -FromTime 4/1/2018 -ToTime 4/30/2018 -Verbose
The Rights Management administration log was successfully generated and can be found at .\Desktop\admin.log.
```

### <a name="usage-logs-for-the-protection-service"></a>Verwendungs Protokolle für den Schutzdienst
Führen Sie das Cmdlet [Get-aipserviceuserlog](/powershell/module/aipservice/get-aipserviceuserlog) aus, um ein Protokoll mit Endbenutzer Aktionen abzurufen, die den Schutzdienst von Azure Information Protection verwenden. Dieses Protokoll enthält möglicherweise personenbezogene Daten in der Form von E-Mail-Adressen und IP-Adressen. Das Protokoll ist im Klartextformat. Nachdem es heruntergeladen wurde, können die genauen Angaben eines bestimmten Administrators offline gesucht werden.

Beispiel:
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

Führen Sie das Cmdlet [Get-aipservicedocumentlog](/powershell/module/aipservice/get-aipservicedocumentlog) aus, um Informationen über einen bestimmten Benutzer von der Website für die Dokument Nachverfolgung abzurufen. Verwenden Sie das Cmdlet [Get-aipservicetrackinglog](/powershell/module/aipservice/get-aipservicetrackinglog) , um die mit den Dokument Protokollen verknüpften Überwachungsinformationen zu erhalten.

Beispiel:
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

### <a name="usage-logs-for-the-azure-information-protection-clients-and-rms-client"></a>Verwendungs Protokolle für die Azure Information Protection Clients und den RMS-Client

Wenn Bezeichnungen und Schutz auf Dokumente und E-Mails angewendet werden, werden E-Mail-Adressen und IP-Adressen möglicherweise in Protokolldateien auf dem Computer des Benutzers an den folgenden Stellen gespeichert:

- Für den Azure Information Protection Unified-Bezeichnungs Client und den Azure Information Protection-Client:%localappdata%\microsoft\msip\logs

- RMS-Client: %localappdata%\Microsoft\MSIPC\msip\Logs

Außerdem protokolliert der Azure Information Protection Client diese personenbezogenen Daten in den lokalen Windows-Ereignisprotokoll **-Anwendungs-und Dienst Protokollen**  >  **Azure Information Protection**.

Wenn der Azure Information Protection-Client den Scanner ausführt, werden personenbezogene Daten auf dem Windows Server-Computer, der den Scanner ausführt, unter %localappdata%\Microsoft\MSIP\Scanner\Reports gespeichert.

Sie können das Protokollieren von Informationen für den Azure Information Protection-Client und den Scanner mithilfe der folgenden Konfigurationen deaktivieren:

- Für den Azure Information Protection Client: Erstellen Sie eine [Erweiterte Client Einstellung](./rms-client/client-admin-guide-customizations.md#change-the-local-logging-level) , mit der der **LogLevel** auf **Off** festgelegt wird.

- Für den Azure Information Protection Scanner: Verwenden Sie das Cmdlet [Set-aipscannerconfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) , um den *Report Level* -Parameter auf **Off** festzulegen.

[!INCLUDE [GDPR-related guidance](./includes/gdpr-hybrid-note.md)]

## <a name="securing-and-controlling-access-to-personal-information"></a>Sichern und Steuern des Zugriffs auf personenbezogene Informationen
Auf die personenbezogenen Daten, die Sie im Azure-Portal anzeigen und angeben, kann nur von Benutzern zugegriffen werden, denen eine der folgenden [Administratorrollen für Azure Active Directory](/azure/active-directory/active-directory-assign-admin-roles-azure-portal) zugewiesen wurde:
    
- **Azure Information Protection-Administrator**

- **Complianceadministrator**

- **Compliancedatenadministrator**

- **Sicherheitsadministrator**

- **Sicherheitsleseberechtigter**

- **Globaler Administrator**

- **Globaler Leser**

Personenbezogene Daten, die Sie mit dem aipservice-Modul (oder dem älteren Modul, aadrm) anzeigen und angeben, können nur für Benutzer zugänglich gemacht werden, denen die Rollen **Azure Information Protection Administrator**, **Compliance-Administrator**, Kompatibilitäts **Daten Administrator** oder **globaler Administrator** von Azure Active Directory oder der Rolle globaler Administrator für den Schutzdienst zugewiesen wurden.

## <a name="updating-personal-data"></a>Aktualisieren von personenbezogenen Daten

Sie können E-Mail-Adressen für bereichsbezogene Richtlinien und Schutzeinstellungen in der Azure Information Protection-Richtlinie aktualisieren. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Für die Schutzeinstellungen können Sie die gleichen Informationen aktualisieren, indem Sie PowerShell-Cmdlets aus dem [aipservice-Modul](/powershell/module/aipservice)verwenden.

Sie können keine E-Mail-Adressen für Administratoren und delegierte Administratoren aktualisieren. Entfernen Sie stattdessen das angegebene Benutzerkonto, und fügen Sie das Benutzerkonto mit der aktualisierten E-Mail-Adresse erneut hinzu. 

### <a name="protection-templates"></a>Schutzvorlagen

Führen Sie das [Set-aipservicetemplateproperty-](/powershell/module/aipservice/set-aipservicetemplateproperty) Cmdlet aus, um die Schutz Vorlage zu aktualisieren. Da sich die persönlichen Daten innerhalb der- `RightsDefinitions` Eigenschaft befinden, müssen Sie auch das [New-aipservicerighundefinition-](/powershell/module/aipservice/new-aipservicerightsdefinition) Cmdlet verwenden, um ein Rechte Definitions Objekt mit den aktualisierten Informationen zu erstellen, und das Rechte Definitions Objekt mit dem `Set-AipServiceTemplateProperty` Cmdlet verwenden.

### <a name="super-users-and-delegated-administrators-for-the-protection-service"></a>Administratoren und Delegierte Administratoren für den Schutzdienst

Wenn Sie die E-Mail-Adresse eines Administrators aktualisieren müssen:

1. Verwenden Sie [Remove-aipservicesuperuser](/powershell/module/aipservice/Remove-AipServiceSuperUser) , um den Benutzer und die alte e-Mail-Adresse zu entfernen.

2. Fügen Sie mit [Add-aipservicesuperuser](/powershell/module/aipservice/Add-AipServiceSuperUser) den Benutzer und die neue e-Mail-Adresse hinzu.

Wenn Sie die E-Mail-Adresse eines delegierten Administrators aktualisieren müssen:

1. Entfernen Sie den Benutzer und die alte e-Mail-Adresse mit [Remove-aipservicerolebasedadministrator](/powershell/module/aipservice/Remove-AipServiceRoleBasedAdministrator) .

2. Fügen Sie mit [Add-aipservicerolebasedadministrator](/powershell/module/aipservice/Add-AipServiceRoleBasedAdministrator) den Benutzer und die neue e-Mail-Adresse hinzu.

## <a name="deleting-personal-data"></a>Löschen von personenbezogenen Daten
Sie können E-Mail-Adressen für bereichsbezogene Richtlinien und Schutzeinstellungen in der Azure Information Protection-Richtlinie löschen. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md) und [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md). 

Sie können die gleichen Informationen für die Schutzeinstellungen mithilfe von PowerShell-Cmdlets aus dem [aipservice-Modul](/powershell/module/aipservice)löschen.

Um e-Mail-Adressen für Administratoren und Delegierte Administratoren zu löschen, entfernen Sie diese Benutzer mithilfe des Cmdlets [Remove-aipservicesuperuser](/powershell/module/aipservice/Remove-AipServiceSuperUser) und [Remove-aipservicerolebasedadministrator](/powershell/module/aipservice/Remove-AipServiceRoleBasedAdministrator). 

Zum Löschen von personenbezogenen Daten in Dokumenten Verfolgungs Protokollen, Verwaltungs Protokollen oder Verwendungs Protokollen für den Schutzdienst verwenden Sie den folgenden Abschnitt, um eine Anforderung mit Microsoft-Support zu erhalten.

Wenn Sie personenbezogene Daten in den Clientprotokolldateien und in den Scannerprotokollen löschen möchten, die auf den Computern gespeichert sind, verwenden Sie beliebige Windows-Standardtools, um die Dateien oder personenbezogene Daten aus den Dateien zu löschen. 

### <a name="to-delete-personal-data-with-microsoft-support"></a>Löschen personenbezogener Daten mit dem Microsoft-Support

Verwenden Sie die folgenden drei Schritte, um anzufordern, dass Microsoft persönliche Daten in Dokumenten Verfolgungs Protokollen, Verwaltungs Protokollen oder Verwendungs Protokollen für den Schutzdienst löscht. 

**Schritt 1: Initiieren der DELETE-Anforderung** 
 [Wenden Sie](information-support.md#to-contact-microsoft-support) sich an Microsoft-Support, um eine Azure Information Protection Support Anfrage mit einer Anforderung zum Löschen von Daten aus Ihrem Mandanten zu öffnen. Sie müssen nachweisen, dass Sie der Administrator des Azure Information Protection-Mandanten sind. Beachten Sie, dass die Bestätigung für diesen Prozess mehrere Tage dauert. Während Sie Ihre Anforderung übermitteln, müssen Sie zusätzliche Informationen bereitstellen, die von den Daten abhängig sind, die gelöscht werden sollen.

- Wenn Sie das Verwaltungsprotokoll löschen möchten, stellen Sie das **Enddatum** bereit. Alle Verwaltungsprotokolle bis zu diesem Enddatum werden gelöscht.
- Wenn Sie Nutzungsprotokolle löschen möchten, stellen Sie das **Enddatum** bereit. Alle Nutzungsprotokolle bis zu diesem Enddatum werden gelöscht.
- Wenn Sie die Dokumentnachverfolgungsprotokolle löschen möchten, stellen Sie die **E-Mail-Adresse des Benutzers** bereit. Alle Informationen der Dokumentnachverfolgung, die mit der E-Mail-Adresse dieses Benutzers in Zusammenhang stehen, werden gelöscht.

Diese Daten werden dauerhaft gelöscht. Sie können nicht wiederhergestellt werden, sobald die Löschanforderung durchgeführt wurde. Es wird empfohlen, dass Administratoren die erforderlichen Daten exportieren, bevor eine Löschanforderung übermittelt wird.

**Schritt 2: Warten auf Überprüfung** Microsoft überprüft, ob Ihre Löschanforderung für ein oder mehrere Protokolle legitim ist. Der Vorgang kann bis zu fünf Werktagen dauern.

**Schritt 3: Bestätigung der Löschung** Sie erhalten eine E-Mail von Microsoft Customer Support Services (CSS), in der bestätigt wird, dass die Daten gelöscht wurden. 

## <a name="exporting-personal-data"></a>Exportieren von personenbezogenen Daten
Wenn Sie die PowerShell-Cmdlets aipservice oder aadrm verwenden, werden die personenbezogenen Daten als PowerShell-Objekt für die Suche und den Export verfügbar gemacht. Das PowerShell-Objekt kann in das JSON-Format konvertiert und mithilfe des `ConvertTo-Json`-Cmdlets gespeichert werden.

## <a name="restricting-the-use-of-personal-data-for-profiling-or-marketing-without-consent"></a>Einschränken der Verwendung der personenbezogenen Daten für die Profilerstellung oder das Marketing ohne Zustimmung
Azure Information Protection befolgt die [Datenschutzrichtlinien](https://privacy.microsoft.com/privacystatement) von Microsoft für die Profilerstellung oder für Marketing auf Grundlage von personenbezogenen Daten.

## <a name="auditing-and-reporting"></a>Überwachung und Berichterstellung
Nur Benutzer, denen [Administrator Berechtigungen](#securing-and-controlling-access-to-personal-information) zugewiesen wurden, können das aipservice-oder addrm-Modul verwenden, um personenbezogene Daten zu suchen und zu exportieren. Diese Vorgänge werden im Verwaltungsprotokoll aufgezeichnet. Dieses können Sie herunterladen.

Bei Löschaktionen fungiert die Supportanforderung als Nachverfolgung und Berichterstellung für von Microsoft durchgeführte Aktionen. Nach dem Löschen stehen die gelöschten Daten nicht für die Suche und den Export zur Verfügung, und der Administrator kann dies mithilfe der Get-Cmdlets aus dem aipservice-Modul überprüfen.
