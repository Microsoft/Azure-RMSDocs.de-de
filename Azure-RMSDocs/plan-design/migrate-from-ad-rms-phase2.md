---
# required metadata

title: Migration von AD RMS zu Azure Rights Management – Phase 2 | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793


# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
# Migrationsphase 2: Clientseitige Konfiguration

*Gilt für: Active Directory Rights Management Services, Azure Rights Management*

Verwenden Sie die folgenden Informationen für Phase 2 der Migration von AD RMS zu Azure Rights Management (Azure RMS). Diese Verfahren beziehen sich auf Schritt 5 der [Migration von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md)..


## Schritt 5: Neukonfigurieren von Clients zur Verwendung von Azure RMS
Für Windows-Clients:

1.  [Herunterladen der Migrationsskripts](http://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Diese Skripts setzen die Konfiguration auf Windows-Computern zurück, sodass sie den Azure RMS-Dienst anstelle von AD RMS verwenden.

2.  Befolgen Sie die Anweisungen im Umleitungsskript (Redirect_OnPrem.cmd), um das Skript so zu ändern, dass es auf Ihren neuen Azure RMS-Mandanten zeigt.

3.  Führen Sie diese Skripts auf den Windows-Computern mit erhöhten Rechten im Kontext des Benutzers aus.

Für Clients für mobile Geräte und Mac-Computer:

-   Entfernen Sie die DNS-SRV-Einträge, die Sie bei der Bereitstellung der [AD RMS-Erweiterung für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx) erstellt haben..

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

    Jeder Eintrag weist den REG_SZ-Wert **https://OldRMSserverURL/_wmcs/licensing** mit Daten im folgenden Format auf: **https://&lt;IhreMandantenURL&gt;/_wmcs/licensing**..

    > [!NOTE]
    > *&lt;YourTenantURL&gt;* weist das folgende Format auf: **{GUID}.rms.[Region].aadrm.com**..
    > 
    > Beispiel: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Finden Sie diesen Wert durch Identifizieren des Werts **RightsManagementServiceId** , wenn Sie das [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS ausführen.


## Nächste Schritte
Wechseln Sie zu dem Artikel [phase 3 - supporting services configuration](migrate-from-ad-rms-phase3.md) (Migrationsphase 3: Unterstützung der Dienstekonfiguration), um die Migration fortzusetzen..

<!--HONumber=Apr16_HO4-->


