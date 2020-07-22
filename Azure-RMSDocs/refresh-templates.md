---
title: Aktualisieren von Azure RMS-Vorlagen – AIP
description: Wenn Sie den Azure Rights Management-Dienst verwenden, werden Vorlagen automatisch auf Clientcomputer heruntergeladen, sodass Benutzer sie aus Ihren Anwendungen heraus auswählen können. Allerdings müssen Sie möglicherweise zusätzliche Schritte ausführen, wenn Sie Änderungen an der Vorlage vornehmen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/20/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8c2064f0-dd71-4ca5-9040-1740ab8876fb
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: a5afc20e616809a41d1e724ba657bb99667da858
ms.sourcegitcommit: 16d2c7477b96c5e8f6e4328a61fe1dc3d12c878d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86927623"
---
# <a name="refreshing-templates-for-users-and-services"></a>Aktualisieren von Vorlagen für Benutzer und Dienste

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn Sie den Azure Rights Management-Dienst von Azure Information Protection verwenden, werden Schutz Vorlagen automatisch auf Client Computer heruntergeladen, sodass Benutzer Sie aus Ihren Anwendungen auswählen können. Allerdings müssen Sie möglicherweise zusätzliche Schritte ausführen, wenn Sie Änderungen an der Vorlage vornehmen:

|Anwendung oder Dienst|Aktualisierungsmethode nach Änderungen|
|--------------------------|---------------------------------------------|
|Exchange Online<br /><br />Gilt für Transportregeln und Outlook Web App |Automatische Aktualisierung innerhalb einer Stunde. Weitere Schritte sind nicht erforderlich.|
|Azure Information Protection-Client|Automatische Aktualisierung, wenn die Azure Information Protection-Richtlinie auf dem Client aktualisiert wird:<br /><br /> – Öffnen einer Office-Anwendung, die die Azure Information Protection-Leiste unterstützt. <br /><br /> – Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen. <br /><br /> – Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz (Get-AIPFileStatus und Set-AIPFileLabel).<br /><br /> – Wenn der Microsoft Azure Information Protection-Überprüfungsdienst gestartet wird und die lokale Richtlinie älter als eine Stunde ist. Zusätzlich sucht der Überprüfungsdienst einmal pro Stunde nach Veränderungen und verwendet diese Änderungen beim nächsten Überprüfungszyklus.<br /><br /> – Alle 24 Stunden.<br /><br /> Da dieser Client eng in Office integriert ist, werden alle aktualisierten Vorlagen für Office 365-Apps, Office 2019, Office 2016 oder Office 2013 auch für den Azure Information Protection-Client aktualisiert.|
|Azure Information Protection-Client für einheitliche Bezeichnungen|Bei Office-Apps werden die Vorlagen automatisch aktualisiert, wenn die APP geöffnet wird.<br /><br /> Da dieser Client eng in Office integriert ist, werden alle aktualisierten Vorlagen für Office 365-Apps, Office 2019, Office 2016 oder Office 2013 auch für den Azure Information Protection-Client für einheitliche Bezeichnung aktualisiert.<br /><br /> Für den Datei-Explorer, PowerShell und den Scanner lädt der Client keine Vorlagen herunter, sondern greift auf diese online zu. es sind keine zusätzlichen Schritte erforderlich.|
|Office 365-Apps, Office 2019, Office 2016 und Office 2013|Automatische Aktualisierung nach einem Zeitplan:<br /><br />– Für diese neueren Office-Versionen: Das Standardaktualisierungsintervall ist alle 7 Tage.<br /><br />Weitere Informationen zum Erzwingen einer Aktualisierung vor dem Zeitplan finden Sie im folgenden Abschnitt [: Office 365-apps, Office 2019, Office 2016 und Office 2013: Erzwingen einer Aktualisierung für Vorlagen](#office-365-apps-office-2019-office-2016-and-office-2013-how-to-force-a-refresh-for-templates).|
|Office 2010|Automatische Aktualisierung, wenn Benutzer sich von Windows ab- und wieder anmelden und bis zu einer Stunde warten.|
|Lokales Exchange mit dem Rights Management-Connector<br /><br />Gilt für Transportregeln und Outlook Web App|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich. Outlook Web App speichert allerdings die UI für einen Tag zwischen.|
|Office 2019 für Mac und Office 2016 für Mac|Wird automatisch aktualisiert, wenn Sie geschützte Inhalte öffnen. Informationen zum Erzwingen einer Aktualisierung finden Sie im folgenden Abschnitt [Office 2019 für Mac und Office 2016 für Mac: Erzwingen einer Aktualisierung für Vorlagen](#office-2019-for-mac-and-office-2016-for-mac-how-to-force-a-refresh-for-templates).|
|Die RMS-Freigabeanwendung für Mac-Computer|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich.|
|[Microsoft 365 von Apps für Unternehmen](https://www.microsoft.com/microsoft-365/partners/smb-sku-rename) mit [integrierter Bezeichnung](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps#support-for-sensitivity-label-capabilities-in-apps)|Dieser integrierte Bezeichnungs Client lädt keine Vorlagen herunter, greift jedoch auf diese online zu. es sind keine zusätzlichen Schritte erforderlich.|

Wenn Client Anwendungen Vorlagen herunterladen müssen (anfänglich oder aktualisiert für Änderungen), sollten Sie bis zu 30 Minuten warten, bis der Download abgeschlossen ist und die neuen oder aktualisierten Vorlagen voll funktionstüchtig sind. Die tatsächliche Zeit hängt von Faktoren wie der Größe und Komplexität der Vorlagenkonfiguration und der Netzwerkkonnektivität ab. 

## <a name="office-365-apps-office-2019-office-2016-and-office-2013-how-to-force-a-refresh-for-templates"></a>Office 365-apps, Office 2019, Office 2016 und Office 2013: Erzwingen der Aktualisierung von Vorlagen
Durch Bearbeiten der Registrierung auf Computern, auf denen Office 365-Apps, Office 2019, Office 2016 oder Office 2013 ausgeführt wird, können Sie den automatischen Zeitplan ändern, sodass geänderte Vorlagen auf Computern häufiger als gemäß dem Standardwert aktualisiert werden. Sie können auch eine sofortige Aktualisierung erzwingen, indem Sie die in einem Registrierungswert vorhandenen Daten löschen.

> [!WARNING]
> Durch eine unsachgemäße Verwendung des Registrierungs-Editors können schwerwiegende Fehler auftreten, die möglicherweise eine Neuinstallation des Betriebssystems erforderlich machen. Microsoft kann nicht garantieren, dass Probleme, die aufgrund einer unsachgemäßen Verwendung des Registrierungs-Editors entstehen, behoben werden können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

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

1. Löschen Sie mithilfe eines Registrierungs-Editors die Daten für den Wert **LastUpdatedTime**. Die Daten könnten beispielsweise als **2015-04-20T15:52** angezeigt werden. Löschen Sie „2015-04-20T15:52“, sodass keine Daten angezeigt werden. Verwenden Sie die folgende Informationen, um den Registrierungspfad zu finden, in dem diese Registrierungswertdaten gelöscht werden sollen.

   **Registrierungs Pfad:** HKEY_CURRENT_USER \software\classes\local settings\software\microsoft\msipc \\ < *MicrosoftRMS_FQDN*> \TEMPLATE \\ < *user_alias*>

   **Typ:** REG_SZ

   **Wert:** LastUpdatedTime

   > [!TIP]
   > Im Registrierungspfad bezieht sich <*MicrosoftRMS_FQDN*> auf den FQDN Ihres Microsoft RMS-Diensts. Wenn Sie diesen Wert überprüfen möchten:
   > 
   > Führen Sie das Cmdlet [Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration) für Azure Information Protection aus. Wenn Sie das PowerShell-Modul für aipservice noch nicht installiert haben, finden Sie weitere Informationen unter [Installieren des PowerShell-Moduls für aipservice](install-powershell.md).
   > 
   > Identifizieren Sie in der Ausgabe den Wert von **LicensingIntranetDistributionPointUrl**.
   > 
   > Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
   > 
   > Entfernen Sie **https://** und **/_wmcs/licensing** aus dieser Zeichenfolge des Werts. Bei dem verbleibenden Wert handelt es sich um den FQDN Ihres Microsoft RMS-Diensts. In unserem Beispiel hat der FQDN des Microsoft RMS-Diensts folgenden Wert:
   > 
   > **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2. Löschen Sie den folgenden Ordner und alle darin enthaltenen Dateien: **%localappdata%\Microsoft\MSIPC\Templates**

3. Starten Sie Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.

## <a name="office-2019-for-mac-and-office-2016-for-mac-how-to-force-a-refresh-for-templates"></a>Office 2019 für Mac und Office 2016 für Mac: Erzwingen der Aktualisierung von Vorlagen

In diesen Versionen von Office für Mac werden Vorlagen aktualisiert, wenn Sie geschützte Inhalte öffnen oder Inhalte mithilfe einer Vertraulichkeits Bezeichnung schützen, die für die Anwendung der Verschlüsselung neu konfiguriert wurde. Wenn Sie eine Aktualisierung der Vorlagen erzwingen müssen, können Sie die folgenden Anweisungen verwenden. Mit dem Befehl in den Anweisungen werden jedoch die Vorlagen, der RMS-Tokencache in der Schlüsselkette und lokale Nutzungslizenzen für alle zuvor geöffneten geschützten Inhalte gelöscht. Daher müssen Sie sich erneut authentifizieren, und Sie müssen über eine Internetverbindung verfügen, um die zuvor geöffneten geschützten Inhalte zu öffnen.

1. Öffnen Sie das Terminal, und geben Sie den folgenden Befehl ein:
    
    ```sh
    defaults write ~/Library/Containers/com.microsoft.Outlook/Data/Library/Preferences/com.microsoft.Outlook ResetRMSCache 1
    ```

2. Starten Sie Outlook für Mac neu.

3. Erstellen Sie eine neue e-Mail, wählen Sie **verschlüsseln**aus, und **überprüfen**Sie die Anmelde Informationen.


## <a name="see-also"></a>Weitere Informationen
[Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](configure-policy-templates.md)

