---
title: Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer
description: Anweisungen und Informationen für Administratoren zum Bereitstellen des Azure Information Protection Unified Bezeichnung-Clients für Windows in Unternehmensnetzwerken.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/21/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 8c2441a9272e62577fcaf88c14fb7e6bb6cdbdde
ms.sourcegitcommit: 5e5631e03959034f37705b4f61aead3d35e8cd8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2021
ms.locfileid: "98540170"
---
# <a name="admin-guide-install-the-azure-information-protection-unified-labeling-client-for-users"></a>Administrator Handbuch: Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen [unter AIP für Windows und Office-Versionen unter Erweiterter Support](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support).*
>
>***Relevant für**: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie im [klassischen Client Administrator Handbuch](client-admin-guide-install.md). *

Überprüfen Sie vor der Installation des Azure Information Protection Unified Bezeichnung-Clients in Ihrem Unternehmensnetzwerk, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen: [Anforderungen für Azure Information Protection](../requirements.md) und [zusätzliche Anforderungen für die Installation des Unified-Bezeichnungs Clients in Unternehmensnetzwerken](reqs-ul-client.md).

## <a name="supported-applications-for-the-unified-labeling-client"></a>Unterstützte Anwendungen für den Unified-Bezeichnungs Client

Der Azure Information Protection Unified Label-Client kann Dokumente und e-Mails mit den Office-Anwendungen Word, Excel, PowerPoint und Outlook aus einer der folgenden Office-Editionen bezeichnen und schützen:

- **Office-Apps** für die in der [Tabelle der unterstützten Versionen für Microsoft 365-Apps nach Updatekanal](/officeupdates/update-history-microsoft365-apps-by-date) aufgeführten Versionen von Microsoft 365 Apps for Business oder Microsoft 365 Business Premium, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Microsoft 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.
- **Microsoft 365 Apps for Enterprise**
- **Office Professional Plus 2019**
- **Office Professional Plus 2016**
- **Office Professional Plus 2013 mit Service Pack 1**
- **Office Professional Plus 2010 mit Service Pack 2**

Andere Editionen von Office (z. b. **Standard**) können Dokumente und e-Mails nicht mithilfe eines Rights Management Dienstanbieter schützen. Für diese Editionen wird Azure Information Protection nur für die **Bezeichnung** unterstützt. 

Folglich werden Bezeichnungen, die Schutz anwenden, den Benutzern auf der Schaltfläche "Azure Information Protection Sensitivität" oder der Leiste nicht angezeigt.

Informationen dazu, welche Office-Editionen den Datenschutzdienst unterstützen, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../requirements-applications.md).

Weitere Informationen finden Sie unter [bekannte Probleme von AIP in Office-Anwendungen](../known-issues.md#aip-known-issues-in-office-applications).

## <a name="unified-labeling-client-installation-options"></a>Unified Bezeichnungs Client-Installationsoptionen

Es gibt zwei Optionen zum Installieren des Clients für Benutzer:

|Option  |BESCHREIBUNG  | I
|---------|---------|
|**Ausführen der ausführbaren Version (. exe) des Clients**     |   Die empfohlene Installationsmethode, die Sie interaktiv oder im Hintergrund ausführen können. <br><br>Diese Methode bietet die größte Flexibilität und wird empfohlen, da das Installationsprogramm eine Vielzahl der erforderlichen Komponenten überprüft und fehlende erforderliche Komponenten automatisch installieren kann. <br><br>Weitere Informationen finden Sie unter [Installieren des AIP Unified Bezeichnung-Clients mit dem ausführbaren Installations](#install-the-aip-unified-labeling-client-using-the-executable-installer)Programm.|
|**Bereitstellen der Windows Installer-Version (. msi) des Clients**     |     Wird nur für Installationen im Hintergrund unterstützt, die einen zentralen Bereitstellungsmechanismus verwenden, z. B. Gruppenrichtlinien, Configuration Manager und Microsoft Intune. <br><br>Diese Methode ist für Windows 10-PCs erforderlich, die von Intune und der Verwaltung mobiler Geräte (MDM) verwaltet werden, da bei diesen Computern keine ausführbaren Dateien für die Installation unterstützt werden. <br><br> Wenn Sie dennoch diese Installationsmethode verwenden, müssen Sie die abhängige Software, die das Installationsprogramm für jeden Computer für die ausführbare Datei ausführen würde, manuell überprüfen und installieren oder deinstallieren. <br><br>Weitere Informationen finden Sie unter [Installieren des Unified-Bezeichnung-Clients mit dem MSI-Installations](#install-the-unified-labeling-client-using-the-msi-installer)Programm. |
|     |         |


Nachdem der Azure Information Protection Unified Bezeichnung-Client installiert wurde, können Sie diesen Client aktualisieren, indem Sie die ausgewählte Installationsmethode wiederholen, oder Windows Update verwenden, um den Client automatisch zu aktualisieren. 

Weitere Informationen zum Upgrade finden Sie im Abschnitt [Upgraden und Verwalten des Azure Information Protection-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

## <a name="install-the-aip-unified-labeling-client-using-the-executable-installer"></a>Installieren des AIP Unified Bezeichnung-Clients mit dem ausführbaren Installationsprogramm

Verwenden Sie die folgenden Anweisungen, um den-Client zu installieren, wenn Sie *nicht* den Microsoft Update Katalog verwenden, oder stellen Sie [die **MSI**](#install-the-unified-labeling-client-using-the-msi-installer) -Datei mithilfe einer zentralen Bereitstellungs Methode wie InTune bereit.

So installieren Sie den Unified-Bezeichnungs **Client mithilfe der exe-Datei**:

1. Laden Sie die ausführbare Version des Azure Information Protection Unified Bezeichnung Client (Dateiname **AzInfoProtection_UL**) aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunter. 
    
    > [!IMPORTANT]
    > Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen. 
    >
 
1. Für eine Standardinstallation führen Sie einfach die ausführbare Datei aus, z. b. **AzInfoProtection_UL.exe**. 

    Um alle Installationsoptionen anzuzeigen, führen Sie zuerst die ausführbare Datei mit **/Help** aus: `AzInfoProtection_UL.exe /help`

    Beispiel: 
    - So installieren Sie den Client unbeaufsichtigt: `AzInfoProtection_UL.exe /quiet`
    
    - So installieren Sie nur die PowerShell-Cmdlets: `AzInfoProtection_UL.exe  PowerShellOnly=true /quiet`
    
    Diese zusätzlichen Parameter sind im Hilfebildschirm nicht aufgelistet:
        
    |Parameter  |BESCHREIBUNG  |
    |---------|---------|
    |**Allowtelemetry = 0**     |    Verwenden Sie diesen Parameter, um die Installationsoption **Senden Sie Nutzungsstatistiken an Microsoft, und helfen Sie so mit, Azure Information Protection zu verbessern** zu deaktivieren.     |
    |**ServiceLocation**     |  Verwenden Sie diesen Parameter, wenn Sie den Client auf Computern installieren, die Office 2010 ausführen und Ihre Benutzer keine lokalen Administratoren auf ihren Computern sind, oder wenn Sie keine Eingabeaufforderung für die Benutzer anzeigen lassen möchten. <br><br>Weitere Informationen finden Sie unter <br>- [Weitere Informationen zum **servicelokation** -Installationsparameter](#more-information-about-the-servicelocation-installation-parameter) <br> - [AIP für Windows und Office-Versionen in erweiterter Unterstützung](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)      |
    | | |

1. So schließen Sie die Installation ab: 

    - **Wenn auf Ihrem Computer [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)** ausgeführt wird, starten Sie den Computer neu. 
        
        Wenn der Client nicht mit dem **serviceloationsparameter** installiert wurde, müssen Sie beim ersten Öffnen einer der Office-Anwendungen, die den Azure Information Protection Unified Client (z. b. Word) verwenden, alle Eingabe Aufforderungen bestätigen, um die Registrierung für diese erstmalige Verwendung zu aktualisieren. 

        [Dienstermittlung](client-deployment-notes.md#rms-service-discovery) wird verwendet, um die Registrierungsschlüssel aufzufüllen. 
    
    - **Für andere Versionen von Office** starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. 
        
1. Vergewissern Sie sich, dass die Installation erfolgreich war, indem Sie die Installationsprotokoll Datei überprüfen, die standardmäßig im Ordner " **% Temp%** " erstellt wird. 

    Die Installationsprotokoll Datei weist das folgende Namensformat auf: `Microsoft_Azure_Information_Protection_<number>_<number>_MSIP.Setup.Main.msi.log`
    
    Beispiel: **Microsoft_Azure_Information_Protection_20161201093652_000_MSIP.Setup.Main.msi.log**
    
    Suchen Sie in dieser Protokolldatei nach der folgenden Zeichenfolge: **Product: Microsoft Azure Information Protection--Installation wurde erfolgreich abgeschlossen**. Wenn Fehler bei der Installation auftreten, enthält diese Protokolldatei Informationen, anhand derer Sie Probleme erkennen und diese beheben können.

    > [!TIP]
    > Sie können den Speicherort der Installationsprotokoll Datei mit dem **/Log** -Installationsparameter ändern. 
    >  
### <a name="more-information-about-the-servicelocation-installation-parameter"></a>Weitere Informationen zum ServiceLocation-Installationsparameter

Wenn Sie den-Client für Benutzer installieren, die über [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support) verfügen und über keine lokalen Administrator Berechtigungen verfügen, geben Sie den **serviceloationsparameter** und die URL für Ihren Azure Rights Management-Dienst an. 

Dieser Parameter und Wert erstellt die folgenden Registrierungsschlüssel und legt sie fest:

`HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\Activation`

`HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing`

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing`

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation`


**So identifizieren Sie den Wert, der für den serviceloationsparameter angegeben werden soll:**

1. Führen Sie in einer PowerShell-Sitzung zuerst [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) aus, und geben Sie Ihre Administrator Anmelde Informationen an, um eine Verbindung mit dem Azure Rights Management-Dienst herzustellen Führen [Sie dann Get-aipserviceconfiguration](/powershell/module/aipservice/get-aipserviceconfiguration)aus. 
 
    Wenn Sie das PowerShell-Modul für den Azure Rights Management-Dienst noch nicht installiert haben, finden Sie weitere Informationen unter [Installieren des PowerShell-Moduls für aipservice](../install-powershell.md).

2. Identifizieren Sie in der Ausgabe den Wert von **LicensingIntranetDistributionPointUrl**.

    Beispiel: **LicensingIntranetDistributionPointUrl: https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**

3. Entfernen Sie in dem Wert **/_wmcs/licensing** aus der Zeichenfolge. Beispiel: **https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

    Die verbleibende Zeichenfolge ist der Wert, der für Ihren ServiceLocation-Parameter angegeben wird.

So installieren Sie den Client z. b. automatisch für [Office 2010](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support) und Azure RMS:

```powershell
AzInfoProtection_UL.exe /quiet ServiceLocation=https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com
```


## <a name="install-the-unified-labeling-client-using-the-msi-installer"></a>Installieren des Unified-Bezeichnungs Clients mit dem MSI-Installationsprogramm

Verwenden Sie für die zentrale Bereitstellung die folgenden Informationen, die für die **MSI** -Installationsversion des Azure Information Protection Unified Bezeichnung-Clients spezifisch sind. 

Wenn Sie Intune als Bereitstellungsmethode für Ihre Software verwenden, berücksichtigen Sie neben diesen Anweisungen auch die Informationen unter [Hinzufügen von Apps mit Microsoft Intune](/mem/intune/apps/apps-add).

**So installieren Sie den Unified-Bezeichnungs Client mit der MSI-Datei**

1. Laden Sie die **MSI** -Version des Azure Information Protection Unified Bezeichnung-Clients (**AzInfoProtection_UL**) aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunter. 
    
    > [!IMPORTANT]
    > Wenn eine Vorschauversion verfügbar ist, behalten Sie diese Version nur für Testzwecke. Sie ist nicht für Endbenutzer in einer Produktionsumgebung vorgesehen.
    > 

1. Für jeden Computer, auf dem die **MSI** -Datei ausgeführt wird, müssen Sie sicherstellen, dass die folgenden Software Abhängigkeiten vorhanden sind. 

    Verpacken Sie diese z **. b.** mit der MSI-Version des Clients, oder stellen Sie Sie nur auf Computern bereit, die diese Abhängigkeiten erfüllen:
    
    |Office-Version|Betriebssystem|Software|Aktion|
    |--------------------|--------------|----------------|---------------------|
    |**Alle Versionen akzeptieren Office 365, Version 1902 und höher**|Nur Windows 10 Version 1809 mit Betriebssystembuilds, die älter als 17763.348 sind|[4482887 KB](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887)|Installieren|
    |**Office 2016**|Alle unterstützten Versionen|64-Bit: [KB3178666](https://www.microsoft.com/download/details.aspx?id=55007)<br /><br />32-Bit: [KB3178666](https://www.microsoft.com/download/details.aspx?id=54999)<br /><br /> Version: 1.0|Installieren|
    |**Office 2013**|Alle unterstützten Versionen|64-Bit: [KB3172523](https://www.microsoft.com/download/details.aspx?id=54992)<br /><br /> 32-Bit: [KB3172523](https://www.microsoft.com/download/details.aspx?id=54979) <br /><br />Version: 1.0|Installieren|
    |[**Office 2010**](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)|Alle unterstützten Versionen|[Microsoft Online Services-Anmelde-Assistent](https://www.microsoft.com/download/details.aspx?id=28177)<br /><br /> Version: 2.1|Installieren|
    |[**Office 2010**](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)|Windows 8.1 und Windows Server 2012 R2|[KB2843630](https://www.microsoft.com/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren Sie diese, wenn KB2843630 oder KB2919355 nicht installiert sind.|
    |[**Office 2010**](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support)|Windows 8 und Windows Server 2012|[KB2843630](https://www.microsoft.com/download/details.aspx?id=41708)<br /><br /> Im Dateinamen enthaltene Versionsnummer: v3|Installieren|
    | | | | |

1. Führen Sie die MSI-Datei bei einer Standardinstallation mit **/quiet** aus, z.B. `AzInfoProtection_UL.msi /quiet`.

    Möglicherweise müssen Sie zusätzliche Installationsparameter angeben. Weitere Informationen finden Sie in den [Anweisungen zum Installationsprogramm für ausführbare](#install-the-aip-unified-labeling-client-using-the-executable-installer)Dateien.

    > [!NOTE]
    > Standardmäßig ist die Option zur **Verbesserung Azure Information Protection durch das Senden von Nutzungsstatistiken an die Microsoft** -Installation aktiviert. Um diese Option zu deaktivieren, stellen Sie sicher, dass Sie eine der folgenden Aktionen ausführen:
    >
    >- Geben Sie während der Installation **allowtelemetry = 0** an.
    >- Aktualisieren Sie den Registrierungsschlüssel nach der Installation wie folgt: **enabletelemetry = 0**.
    >

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection Unified Bezeichnung-Client installiert haben, finden Sie hier weitere Informationen, die Sie möglicherweise zur Unterstützung dieses Clients benötigen:

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)