---
title: "Migration von AD RMS zu Azure Rights Management – Phase 2 | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e3fd9bd9-3638-444a-a773-e1d5101b1793
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 437afd88efebd9719a3db98f8ab0ae07403053f7
ms.openlocfilehash: ca2dae71dceae4c59d12243c386eaded8ebb11f9


---
# Migrationsphase 2: Clientseitige Konfiguration

*Gilt für: Active Directory Rights Management Services, Azure Rights Management*

Verwenden Sie die folgenden Informationen für Phase 2 der Migration von AD RMS zu Azure Rights Management (Azure RMS). Diese Verfahren beziehen sich auf Schritt 5 der [Migration von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).


## Schritt 5: Neukonfigurieren von Clients zur Verwendung von Azure RMS
Für Windows-Clients:

1.  [Herunterladen der Migrationsskripts](https://go.microsoft.com/fwlink/?LinkId=524619):

    -   CleanUpRMS_RUN_Elevated.cmd

    -   Redirect_OnPrem.cmd

    Diese Skripts setzen die Konfiguration auf Windows-Computern zurück, sodass sie den Azure RMS-Dienst anstelle von AD RMS verwenden.

2.  Befolgen Sie die Anweisungen im Umleitungsskript (Redirect_OnPrem.cmd), um das Skript so zu ändern, dass es auf Ihren neuen Azure RMS-Mandanten zeigt.

    > [!IMPORTANT]
    > Diese Anleitung behandelt auch das Ersetzen der Beispieladressen **adrms** und **adrms.contoso.com** durch de Adressen Ihrer eigenen AD RMS-Server. Wenn Sie diese Änderungen vornehmen, sollten Sie auf zusätzliche Leerzeichen vor und hinter Ihren Adressen achten. Da sie das Migrationsskript fehlschlagen lassen und schwer als Problemursache zu identifizieren sind, dürfen dort keine Leerzeichen vorhanden sein. Nach dem Einfügen von Text fügen einige Bearbeitungstools automatisch ein Leerzeichen an.

3. Für Office 2016-Benutzer: Es gibt noch kein Update, weshalb die Skripts noch keine Konfiguration für Office 2016 enthalten. Wenn Benutzer also diese Office-Version nutzen, müssen Sie die Skripts manuell aktualisieren:

    - Für **CleanUpRMS.cmd** – Suchen Sie die Zeile `reg delete HKCU\Software\Microsoft\Office\15.0\Common\DRM /f`, und fügen Sie direkt darunter folgende Zeile hinzu:

            reg delete HKCU\Software\Microsoft\Office\16.0\Common\DRM /f

    - Für **Redirect_Onprem.cmd** – Suchen Sie die Zeile `reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F1`, und fügen Sie direkt darunter die folgenden zwei Zeilen hinzu:

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServerUrl" /d "https://%CloudRMS%/_wmcs/licensing" /F 

            reg add "HKEY_CURRENT_USER\Software\Microsoft\Office\16.0\Common\DRM" /t REG_SZ /v "DefaultServer" /d "%CloudRMS%" /F

    Optional: Die Skripts verweisen in den Kommentaren nicht auf Office 2016. Wenn Sie die Kommentare entsprechend dieser Ergänzungen für Office 2016 aktualisieren möchten, nehmen Sie die folgenden Änderungen an **Redirect_Onprem.cmd** vor:

    - Suchen Sie nach `::     or MSIPC (Office 2013) with on-premises AD RMS`, und ersetzen Sie es durch Folgendes:
    
            ::     or MSIPC (Office 2013 and 2016) with on-premises AD RMS

    - Suchen Sie nach `echo Redirect SCP for Office 2013`, und ersetzen Sie es durch Folgendes:
    
            echo Redirect SCP for Office versions based on MSIPC

    - Suchen Sie nach `echo Redirect MSIPC for Office 2013`, und ersetzen Sie es durch Folgendes:
    
            echo Redirect MSIPC for Office versions based on MSIPC

4.  Auf Windows-Computern:

    - Führen Sie diese Skripts mit erhöhten Rechten im Kontext des Benutzers aus.

    Für Clients für mobile Geräte und Mac-Computer:

    -  Entfernen Sie die DNS-SRV-Einträge, die Sie bei der Bereitstellung der [AD RMS-Erweiterung für mobile Geräte](http://technet.microsoft.com/library/dn673574.aspx)bereitgestellt haben.

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

-   Hinzufügen der folgenden Registrierungswerte:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer

Redirect_OnPrem.cmd:

-   Erstellen der folgenden Registrierungswerte für jede als Parameter bereitgestellte URL unter jedem der folgenden Speicherorte:

    -   HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection

    -   HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection

    Jeder Eintrag weist den REG_SZ-Wert **https://OldRMSserverURL/_wmcs/licensing** mit Daten im folgenden Format auf: **https://&lt;IhreMandantenURL&gt;/_wmcs/licensing**.

    > [!NOTE]
    > *&lt;IhreMandantenURL&gt;* weist das folgende Format auf: **{GUID}.rms.[Region].aadrm.com**.
    > 
    > Beispiel: 5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
    > 
    > Finden Sie diesen Wert durch Identifizieren des Werts **RightsManagementServiceId** , wenn Sie das [Get-AadrmConfiguration](http://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS ausführen.


## Nächste Schritte
Fahren Sie mit [Phase 3: Unterstützung der Dienstekonfiguration](migrate-from-ad-rms-phase3.md) fort, um die Migration fortzusetzen.


<!--HONumber=Aug16_HO3-->


