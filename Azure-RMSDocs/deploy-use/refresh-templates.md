---
# required metadata

title: Aktualisieren von Vorlagen | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Aktualisieren von Vorlagen für Benutzer
Wenn Sie Azure RMS verwenden, werden Vorlagen automatisch auf Clientcomputer heruntergeladen, sodass Benutzer sie aus Ihren Anwendungen heraus auswählen können. Allerdings müssen Sie möglicherweise zusätzliche Schritte ausführen, wenn Sie Änderungen an der Vorlage vornehmen:

|Anwendung oder Dienst|Aktualisierungsmethode nach Änderungen|
|--------------------------|---------------------------------------------|
|Exchange Online|Manuelle Konfiguration erforderlich zum Aktualisieren von Vorlagen.<br /><br />Die Konfigurationsschritte finden Sie im folgenden Abschnitt [Nur Exchange Online nur: Konfigurieren von Exchange für das Herunterladen geänderter, benutzerdefinierter Vorlagen](#exchange-online-only-how-to-configure-exchange-to-download-changed-custom-templates).|
|Office 365|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich.|
|Office 2016 und Office 2013<br /><br />RMS-Freigabeanwendung für Windows|Automatische Aktualisierung nach einem Zeitplan:<br /><br />Für diese neueren Office-Versionen: Das Standardaktualisierungsintervall ist alle 7 Tage.<br /><br />Für die RMS-Freigabeanwendung für Windows: Ab Version 1.0.1784.0 ist das Standardaktualisierungsintervall jeden Tag. Frühere Versionen haben ein Standardaktualisierungsintervall von alle 7 Tage.<br /><br />Um vor diesem Zeitplan eine Aktualisierung zu erzwingen, lesen Sie den folgenden Abschnitt [Office 2016, Office 2013 und RMS-Freigabeanwendung für Windows: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage](#office-2016-office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template).|
|Office 2010|Aktualisierung bei der Benutzeranmeldung.<br /><br />Um eine Aktualisierung zu erzwingen, bitten oder zwingen Sie Benutzer, sich abzumelden und erneut anzumelden. Oder lesen Sie den folgenden Abschnitt: [Nur Office 2010: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage](#office-2010-only-how-to-force-a-refresh-for-a-changed-custom-template).|
Bei mobilen Geräten, die die RMS-Freigabeanwendung verwenden, werden Vorlagen ohne zusätzliche Konfiguration automatisch heruntergeladen (und erforderlichenfalls aktualisiert).

## Nur Exchange Online: Konfigurieren von Exchange für das Herunterladen geänderter, benutzerdefinierter Vorlagen
Wenn Sie die Verwaltung von Informationsrechten (IRM) für Exchange Online bereits konfiguriert haben, werden benutzerdefinierte Vorlagen für Benutzer erst heruntergeladen, nachdem Sie die folgenden Änderungen mithilfe der Windows PowerShell in Exchange Online vorgenommen haben.

> [!NOTE]
> Weitere Informationen zur Verwendung von Windows PowerShell in Exchange Online finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Sie müssen dieses Verfahren jedes Mal ausführen, wenn Sie eine Vorlage ändern.

### So aktualisieren Sie Vorlagen für Exchange Online

1.  Stellen Sie unter Verwendung von Windows PowerShell in Exchange Online eine Verbindung mit dem Dienst her:

    1.  Geben Sie Ihren Office 365-Benutzernamen und das Kennwort an:

        ```
        $Cred = Get-Credential
        ```

    2.  Stellen Sie eine Verbindung mit dem Exchange Online-Dienst her, indem Sie die folgenden beiden Befehle ausführen:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Verwenden Sie das [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx)-Cmdlet, um Ihre vertrauenswürdige Veröffentlichungsdomäne (TPD, Trusted Publishing Domain) aus Azure RMS erneut zu importieren:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Wenn der TPD-Name beispielsweise **RMS Online - 1** lautet (ein typischer Name für viele Organisationen), geben Sie Folgendes ein: **Import-RMSTrustedPublishingDomain-Name "RMS Online - 1" -RefreshTemplates-RMSOnline**.

    > [!NOTE]
    > Zur Überprüfung des TPD-Namens können Sie das Cmdlet [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) verwenden.

3.  Um zu überprüfen, ob die Vorlagen erfolgreich importiert wurden, warten Sie ein paar Minuten. Führen Sie dann das Cmdlet [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) aus, und legen Sie den Wert von "Typ" auf "Alle" fest. Beispiel:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Es ist sinnvoll, eine Kopie der Ausgabe zu behalten, damit Sie die Namen oder GUIDs der Vorlagen problemlos kopieren können, wenn Sie eine Vorlage später archivieren.

4.  Für jede importierte Vorlage, die in der Outlook Web App verfügbar sein soll, müssen Sie das [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx)-Cmdlet verwenden und den Wert von "Typ" auf "Verteilt" festlegen:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Da Outlook Web Access die Benutzeroberfläche für 24 Stunden zwischenspeichert, sehen Benutzer die neue Vorlage möglicherweise erst nach bis zu einem Tag.

Darüber hinaus, wenn Sie eine (benutzerdefinierte oder Standard) Vorlage archivieren und Exchange Online mit Office 365 verwenden, können Benutzer die archivierten Vorlagen weiterhin sehen, wenn sie die Outlook Web App oder mobile Geräte verwenden, die das Exchange ActiveSync-Protokoll verwenden.

Damit Benutzer diese Vorlagen nicht mehr sehen, stellen Sie unter Verwendung von Windows PowerShell in Exchange Online eine Verbindung mit dem Dienst her, und verwenden Sie das Cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx), indem Sie folgenden Befehl ausführen:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

## Office 2016, Office 2013 und die RMS-Freigabeanwendung für Windows: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage
Durch Bearbeiten der Registrierung auf Computern, auf denen Office 2016, Office 2013 oder die RMS-Freigabeanwendung (Rights Management) für Windows ausgeführt wird, können Sie den automatischen Zeitplan ändern, sodass geänderte Vorlagen auf Computern häufiger als gemäß dem Standardwert aktualisiert werden. Sie können auch eine sofortige Aktualisierung erzwingen, indem Sie die in einem Registrierungswert vorhandenen Daten löschen.

> [!WARNING]
> Die unsachgemäße Verwendung des Registrierungs-Editors kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen können. Microsoft kann nicht garantieren, dass Sie Probleme, die durch die fehlerhafte Verwendung des Registrierungs-Editors entstehen, beheben können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

### So ändern Sie den automatischen Zeitplan

1.  Verwenden Sie einen Registrierungs-Editor, um einen der folgenden Registrierungswerte zu erstellen und festzulegen:

    - So legen Sie eine Aktualisierungshäufigkeit in Tagen fest (mindestens 1 Tag):  Erstellen Sie einen neuen Registrierungswert namens **TemplateUpdateFrequency** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Tagen angibt. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem dieser neue Registrierungswert erstellt werden soll.

        **Registrierungspfad:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wert:** TemplateUpdateFrequency


    - To set an update frequency in seconds (minimum of 1 second):  Create a new registry value named **TemplateUpdateFrequencyInSeconds** and define an integer value for the data, which specifies the frequency in seconds to download any changes to a downloaded template. Use the following table to locate the registry path to create this new registry value.

        **Registry path:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Type:** REG_DWORD

        **Value:** TemplateUpdateFrequencyInSeconds

    Make sure that you create and set one of these registry values, not both. If both are present, **TemplateUpdateFrequency** is ignored.

2.  Wenn Sie eine sofortige Aktualisierung der Vorlagen erzwingen möchten, führen Sie die nächste Schrittfolge aus. Starten Sie andernfalls jetzt Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.

### So erzwingen Sie eine sofortige Aktualisierung

1.  Löschen Sie mithilfe eines Registrierungs-Editors die Daten für den Wert **LastUpdatedTime** . Es kann beispielsweise **2015-04-20T15:52** angezeigt werden. Löschen Sie "2015-04-20T15:52", sodass keine Daten angezeigt werden. Verwenden Sie die folgende Informationen, um den Registrierungspfad zu finden, in dem diese Registrierungswertdaten gelöscht werden sollen.

    **Registrierungspfad:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<*MicrosoftRMS_FQDN*>\Template

    **Typ:** REG_SZ

    **Wert:** LastUpdatedTime

    > [!TIP]
        > Im Registrierungspfad bezieht sich <*MicrosoftRMS_FQDN*> auf den FQDN Ihres Microsoft RMS-Diensts. Wenn Sie diesen Wert überprüfen möchten:

    > 1.  Führen Sie das [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS aus. Wenn Sie das Windows PowerShell-Modul für Azure RMS noch nicht installiert haben, lesen Sie [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).
    > 2.  Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.
    > 
    >     Beispiel: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Entfernen Sie **https://** und **/_wmcs/licensing** aus dieser Zeichenfolge des Werts. Bei dem verbleibenden Wert handelt es sich um den FQDN Ihres Microsoft RMS-Diensts. In unserem Beispiel hat der FQDN des Microsoft RMS-Diensts folgenden Wert:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Löschen Sie den folgenden Ordner und alle darin enthaltenen Dateien: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Starten Sie Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.

## Nur Office 2010: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage
Durch Bearbeiten der Registrierung auf Computern mit Office 2010 können Sie einen Wert festlegen, sodass geänderte Vorlagen auf Computern aktualisiert werden, ohne dass darauf gewartet wird, dass sich Benutzer ab- und wieder anmelden. Sie können auch eine sofortige Aktualisierung erzwingen, indem Sie die in einem Registrierungswert vorhandenen Daten löschen.

> [!WARNING]
> Die unsachgemäße Verwendung des Registrierungs-Editors kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen können. Microsoft kann nicht garantieren, dass Sie Probleme, die durch die fehlerhafte Verwendung des Registrierungs-Editors entstehen, beheben können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

### So ändern Sie die Aktualisierungshäufigkeit

1.  Erstellen Sie mit einem Registrierungs-Editor einen neuen Registrierungswert namens **UpdateFrequency** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Tagen angibt. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem dieser neue Registrierungswert erstellt werden soll.

    **Registrierungspfad:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **Typ:** REG_DWORD

    **Wert:** UpdateFrequency

2.  Wenn Sie eine sofortige Aktualisierung der Vorlagen erzwingen möchten, führen Sie die nächste Schrittfolge aus. Starten Sie andernfalls jetzt Ihre Office-Anwendungen neu.

### So erzwingen Sie eine sofortige Aktualisierung

1.  Löschen Sie mithilfe eines Registrierungs-Editors die Daten für den Wert **LastUpdatedTime** . Es kann beispielsweise **2015-04-20T15:52** angezeigt werden. Löschen Sie "2015-04-20T15:52", sodass keine Daten angezeigt werden. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem diese Registrierungswertdaten gelöscht werden sollen.

    **Registrierungspfad:** HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement

    **Typ:** REG_SZ

    **Wert:** lastUpdatedTime


2.  Löschen Sie den folgenden Ordner und alle darin enthaltenen Dateien: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Starten Sie Ihre Office-Anwendungen neu.

## Siehe auch
[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](configure-custom-templates.md)

<!--HONumber=Apr16_HO3-->


