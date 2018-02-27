---
title: "Aktualisieren von Azure RMS-Vorlagen – AIP"
description: "Wenn Sie den Azure Rights Management-Dienst verwenden, werden Vorlagen automatisch auf Clientcomputer heruntergeladen, sodass Benutzer sie aus Ihren Anwendungen heraus auswählen können. Allerdings müssen Sie möglicherweise zusätzliche Schritte ausführen, wenn Sie Änderungen an der Vorlage vornehmen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/17/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e8d7f34d020157ed38bb8458c4d5f4ddb6986f75
ms.sourcegitcommit: 31c79d948ec3089a4dc65639f1842c07c7aecba6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/20/2018
---
# <a name="refreshing-templates-for-users-and-services"></a>Aktualisieren von Vorlagen für Benutzer und Dienste

>*Gilt für: Azure Information Protection, Office 365*

Wenn Sie den Azure Rights Management-Dienst von Azure Information Protection verwenden, werden Vorlagen automatisch auf Clientcomputer heruntergeladen, sodass Benutzer sie aus Ihren Anwendungen heraus auswählen können. Allerdings müssen Sie möglicherweise zusätzliche Schritte ausführen, wenn Sie Änderungen an der Vorlage vornehmen:

|Anwendung oder Dienst|Aktualisierungsmethode nach Änderungen|
|--------------------------|---------------------------------------------|
|Exchange Online<br /><br />Gilt für Transportregeln und Outlook Web App |Automatische Aktualisierung innerhalb einer Stunde. Weitere Schritte sind nicht erforderlich.<br /><br />Gilt bei Verwendung der [Office 365-Nachrichtenverschlüsselung mit neuen Funktionen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Wenn Sie bereits Exchange Online für die Verwendung des Azure Rights Management-Diensts konfiguriert haben, indem Sie eine vertrauenswürdige Veröffentlichungsdomäne (TPD) importieren haben, verwenden Sie dieselben Anweisungen, um die neuen Funktionen in Exchange Online zu aktivieren.|
|Azure Information Protection-Client|Automatische Aktualisierung, wenn die Azure Information Protection-Richtlinie auf dem Client aktualisiert wird:<br /><br /> – Öffnen einer Office-Anwendung, die die Azure Information Protection-Leiste unterstützt. <br /><br /> – Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen. <br /><br /> – Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz (Get-AIPFileStatus und Set-AIPFileLabel).<br /><br /> – Wenn der Azure Information Protection-Überprüfungsdienst beginnt. Zusätzlich sucht der Überprüfungsdienst einmal pro Stunde nach Veränderungen und verwendet diese Änderungen beim nächsten Überprüfungszyklus.<br /><br /> – Alle 24 Stunden.<br /><br /> Da der Azure Information Protection-Client eng in Office integriert ist, werden alle aktualisierten Vorlagen für Office 2016 oder Office 2013 auch für den Azure Information Protection-Client aktualisiert.|
|Office 2016 und Office 2013<br /><br />RMS-Freigabeanwendung für Windows|Automatische Aktualisierung nach einem Zeitplan:<br /><br />– Für diese neueren Office-Versionen: Das Standardaktualisierungsintervall ist alle 7 Tage.<br /><br />– Für die RMS-Freigabeanwendung für Windows: Ab Version 1.0.1784.0 gilt ein Standardaktualisierungsintervall von einem Tag. Frühere Versionen haben ein Standardaktualisierungsintervall von alle 7 Tage.<br /><br />Um vor dem Zeitplan eine Aktualisierung zu erzwingen, lesen Sie den folgenden Abschnitt: [Office 2016, Office 2013 und RMS-Freigabeanwendung für Windows: Erzwingen der Aktualisierung einer geänderten benutzerdefinierten Vorlage](#office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template).|
|Office 2010|Automatische Aktualisierung, wenn Benutzer sich von Windows ab- und wieder anmelden und bis zu einer Stunde warten.|
|Lokales Exchange mit dem Rights Management-Connector<br /><br />Gilt für Transportregeln und Outlook Web App|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich. Outlook Web App speichert allerdings die UI für einen Tag zwischen.|
|Office 2016 für Mac|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich.|
|Die RMS-Freigabeanwendung für Mac-Computer|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich.|

Beim Herunterladen von Vorlagen (beim ersten Mal oder bei Aktualisierungen mit Änderungen) durch Clientanwendungen müssen Sie voraussichtlich etwa bis zu 15 Minuten warten, bis der Download abgeschlossen ist und die neuen bzw. aktualisierten Vorlagen voll funktionsfähig sind. Die tatsächliche Zeit hängt von Faktoren wie der Größe und Komplexität der Vorlagenkonfiguration und der Netzwerkkonnektivität ab. 

## <a name="office-2016--office-2013-and-rms-sharing-application-for-windows-how-to-force-a-refresh-for-a-changed-custom-template"></a>Office 2016, Office 2013 und die RMS-Freigabeanwendung für Windows: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage
Durch Bearbeiten der Registrierung auf Computern, auf denen Office 2016, Office 2013 oder die RMS-Freigabeanwendung (Rights Management) für Windows ausgeführt wird, können Sie den automatischen Zeitplan ändern, sodass geänderte Vorlagen auf Computern häufiger als gemäß dem Standardwert aktualisiert werden. Sie können auch eine sofortige Aktualisierung erzwingen, indem Sie die in einem Registrierungswert vorhandenen Daten löschen.

> [!WARNING]
> Die unsachgemäße Verwendung des Registrierungs-Editors kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen können. Microsoft kann nicht garantieren, dass Sie Probleme, die durch die fehlerhafte Verwendung des Registrierungs-Editors entstehen, beheben können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

### <a name="to-change-the-automatic-schedule"></a>So ändern Sie den automatischen Zeitplan

1.  Verwenden Sie einen Registrierungs-Editor, um einen der folgenden Registrierungswerte zu erstellen und festzulegen:

    - So legen Sie eine Aktualisierungshäufigkeit in Tagen fest (mindestens 1 Tag):  Erstellen Sie einen neuen Registrierungswert namens **TemplateUpdateFrequency** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Tagen angibt. Verwenden Sie die folgenden Informationen, um den Registrierungspfad zu finden, um diesen neuen Registrierungswert zu erstellen.

        **Registrierungspfad:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wert:** TemplateUpdateFrequency

    - So legen Sie eine Aktualisierungshäufigkeit in Sekunden fest (mindestens 1 Sekunde):  Erstellen Sie einen neuen Registrierungswert namens **TemplateUpdateFrequencyInSeconds** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Sekunden angibt. Verwenden Sie die folgenden Informationen, um den Registrierungspfad zu finden, um diesen neuen Registrierungswert zu erstellen.

        **Registrierungspfad:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC

        **Typ:** REG_DWORD

        **Wert**: TemplateUpdateFrequencyInSeconds

    Sie dürfen nur einen der beiden Registrierungswerte erstellen und festlegen (nicht beide). Wenn beide vorhanden sind, wird **TemplateUpdateFrequency** ignoriert.

2.  Wenn Sie eine sofortige Aktualisierung der Vorlagen erzwingen möchten, führen Sie die nächste Schrittfolge aus. Starten Sie andernfalls jetzt Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.

### <a name="to-force-an-immediate-refresh"></a>So erzwingen Sie eine sofortige Aktualisierung

1.  Löschen Sie mithilfe eines Registrierungs-Editors die Daten für den Wert **LastUpdatedTime** . Es kann beispielsweise **2015-04-20T15:52** angezeigt werden. Löschen Sie "2015-04-20T15:52", sodass keine Daten angezeigt werden. Verwenden Sie die folgende Informationen, um den Registrierungspfad zu finden, in dem diese Registrierungswertdaten gelöscht werden sollen.

    **Registrierungspfad:** HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\<*MicrosoftRMS_FQDN*>\Template

    **Typ:** REG_SZ

    **Wert:** LastUpdatedTime

    > [!TIP]
        > Im Registrierungspfad bezieht sich <*MicrosoftRMS_FQDN*> auf den FQDN Ihres Microsoft RMS-Diensts. Wenn Sie diesen Wert überprüfen möchten:

    > 1.  Führen Sie das [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS aus. Wenn Sie das Windows PowerShell-Modul für Azure RMS noch nicht installiert haben, lesen Sie [Installieren des AADRM-PowerShell-Moduls](install-powershell.md).
    > 2.  Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.
    >
    >     Beispiel: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Entfernen Sie **https://** und **/_wmcs/licensing** aus dieser Zeichenfolge des Werts. Bei dem verbleibenden Wert handelt es sich um den FQDN Ihres Microsoft RMS-Diensts. In unserem Beispiel hat der FQDN des Microsoft RMS-Diensts folgenden Wert:
    >
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Löschen Sie den folgenden Ordner und alle darin enthaltenen Dateien: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Starten Sie Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.


## <a name="see-also"></a>Weitere Informationen
[Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](../deploy-use/configure-policy-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
