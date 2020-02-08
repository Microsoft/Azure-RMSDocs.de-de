---
title: Azure Information Protection vereinheitlichte Bezeichnung für den Client Versionsverlauf & Unterstützungs Richtlinie
description: Weitere Informationen zum Release des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 02/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.reviewer: elkamins
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 3f30cd7aea2498c101937aacc8f3cbf3ffdc6364
ms.sourcegitcommit: d9465ec12b78c24d4d630295d4e5ffae0ba8d647
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/06/2020
ms.locfileid: "77044965"
---
# <a name="azure-information-protection-unified-labeling-client---version-release-history-and-support-policy"></a>Azure Information Protection Unified Bezeichnungs Verlauf des Client Versions Verlaufs und der Support Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


Sie können den Azure Information Protection Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018)herunterladen.

Nach einer kurzen Verzögerung von in der Regel einige Wochen ist die neueste Version der allgemeinen Verfügbarkeit auch im Microsoft Update Katalog mit dem Produktnamen **Microsoft Azure Information Protection** > **Microsoft Azure Information Protection Unified**-Bezeichnungs Client und der Klassifizierung von **Updates**enthalten. Diese Aufnahme in den Katalog bedeutet, dass Sie den Client mithilfe von WSUS oder Configuration Manager oder anderen Softwarebereitstellungsmechanismen, die Microsoft Update verwenden, aktualisieren können.

Weitere Informationen finden Sie unter [aktualisieren und Verwalten des Azure Information Protection Unified Bezeichnung-Clients](clientv2-admin-guide.md#upgrading-and-maintaining-the-azure-information-protection-unified-labeling-client).

### <a name="servicing-information-and-timelines"></a>Wartungsinformationen und Zeitachsen

Jede allgemein verfügbare Version des Azure Information Protection Unified Bezeichnung-Clients wird bis zu sechs Monate nach der Veröffentlichung der nachfolgenden GA-Version unterstützt. Die Dokumentation enthält keine Informationen über nicht unterstützte Versionen des Clients. Problembehebungen und neue Funktionen gelten immer ausschließlich für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht für Endbenutzer in Produktionsnetzwerken bereitgestellt werden. Verwenden Sie stattdessen die neuste Vorschauversion, um neue Funktionen oder Problembehebungen kennenzulernen und zu testen, die in der nächsten allgemein verfügbaren Version enthalten sein sollen. Veraltete Vorschauversionen werden nicht mehr unterstützt.

##### <a name="general-availability-versions-that-are-no-longer-supported"></a>Allgemein verfügbare Versionen, die nicht mehr unterstützt werden:

|Clientversion|Datum der Veröffentlichung|
|--------------|-------------|
|2.2.14.0|07/15/2019|
|2.0.779.0|05/01/2019|
|2.0.778.0|04/16/2019|

Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.


### <a name="release-information"></a>Informationen zum Release

Verwenden Sie die folgenden Informationen, um zu erfahren, was für eine unterstützte Version des Azure Information Protection Unified Bezeichnung-Clients für Windows neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. Das Datumsformat, das auf dieser Seite verwendet wird, ist *Monat/Tag/Jahr*.

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem Unified-Bezeichnungs Client haben, sollten Sie überprüfen, ob es mit der neuesten GA-Version behoben wurde. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion (falls verfügbar).
>  
> Technischen Support finden Sie in den Informationen unter [Supportoptionen und Communityressourcen](../information-support.md#support-options-and-community-resources). Wir laden Sie auch dazu ein, sich mit dem Azure Information Protection-Team auf seiner [Yammer-Website](https://www.yammer.com/askipteam/) in Verbindung zu setzen.

Dieser Client ersetzt den Azure Information Protection Client (klassisch). Informationen zum Vergleichen von Features und Funktionen mit dem klassischen Client finden Sie unter [vergleichen der Bezeichnung für Clients für Windows-Computer](use-client.md#compare-the-labeling-clients-for-windows-computers).

## <a name="version-261010-preview"></a>Version 2.6.101.0 (Vorschau)

**Veröffentlicht** 1/15/2020

**Neue Funktionen:**

- Die Änderung des [PowerShell](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-powershell) -Cmdlets **Set-aipfilelabel** auf ermöglicht das Entfernen des Schutzes von PST-, rar-, 7zip-und MSG-Dateien. 

- Die Möglichkeit, Azure Information Protection Administratoren zu steuern, wann die Pfile-Erweiterungen für Dateien verwendet werden. Erfahren Sie mehr über das [ändern geschützter Dateitypen](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#change-which-file-types-to-protect). 

- Unterstützung für dynamisches visuelles Element für Anwendungen und Variablen hinzugefügt. Weitere Informationen zum Konfigurieren von [Bezeichnungen für visuelle Kennzeichnungen](https://docs.microsoft.com/azure/information-protection/configure-policy-markings). 

- Verbesserungen an [anpassbaren Richtlinien Tipps für automatische und empfohlene Bezeichnungen](use-client.md).   

- Unterstützung für [Offline Beschriftungs Funktionen](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#support-for-disconnected-computers) mit Office-Apps im Unified-Bezeichnungs Client hinzugefügt.

- Die neue **wordshapenametoremove** Advanced-Eigenschaft ermöglicht das Entfernen von Inhalts Markierungen in Word-Dokumenten, die von Anwendungen von Drittanbietern erstellt wurden. Erfahren Sie mehr darüber, wie [Sie vorhandene Shape-Namen identifizieren und mithilfe von **wordshapenametoremove**zum Entfernen definieren](https://docs.microsoft.com/azure/information-protection/rms-client/clientv2-admin-guide-customizations#remove-headers-and-footers-from-other-labeling-solutions). 

- Funktionen für [Scanner](../deploy-aip-scanner.md) :
    - [Einfachere lokale und untergeordnete SharePoint-](https://docs.microsoft.com/azure/information-protection/quickstart-findsensitiveinfo#permission-users-to-scan-sharepoint-repositories)Ermittlung. Das Festlegen der einzelnen Standorte ist nicht mehr erforderlich. 
    - Erweiterte Eigenschaft für die SQL-Segment [Größen](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#storage-requirements-and-capacity-planning-for-sql-server) Änderung hinzugefügt.
    - Administratoren haben jetzt die Möglichkeit, [vorhandene Scans anzuhalten und eine erneute Überprüfung durchzuführen](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#stop-a-scan) , wenn die Standard Bezeichnung geändert wurde.
    - Standardmäßig legt Scanner jetzt minimale Telemetrie für schnellere Scans und eine reduzierte Protokoll Größe fest, und Informationstypen werden nun in der Datenbank zwischengespeichert. Erfahren Sie mehr über die [Scanner-Optimierung](https://docs.microsoft.com/azure/information-protection/deploy-aip-scanner#optimizing-the-performance-of-the-scanner). 

**Fixes**

- Scanner unterstützt jetzt separate bereit Stellungen für die Datenbank und den Dienst, während **sysadmin** -Rechte nur für die Daten Bank Bereitstellung erforderlich sind. 
- In Fällen, in denen Benutzer erfolglos versuchten, geschützte TIFF-Dateien und TIFF-Dateien zu öffnen, die von RightFax erstellt wurden, werden die TIFF-Dateien nun geöffnet und bleiben erwartungsgemäß stabil.  
- Vorherige Beschädigungen geschützter txt-und PDF-Dateien werden aufgelöst.
- In Log Analytics wurde eine inkonsistente Bezeichnung zwischen **automatischen** und **manuellen** Bezeichnungen korrigiert. 
- Unerwartete Vererbungs Probleme, die zwischen neuen e-Mails und der zuletzt geöffneten e-Mail eines Benutzers erkannt wurden, sind nun behoben.  
- Der Schutz von. msg-Dateien als. msg. pfiles funktioniert jetzt erwartungsgemäß. 
- Die von den benutzerdefinierten Office-Einstellungen hinzugefügten Berechtigungen für Mitbesitzer werden nun wie erwartet angewendet. 
- Wenn Sie die Berechtigungs Herabstufung eingeben, kann Text nicht mehr eingegeben werden, wenn bereits andere Optionen ausgewählt sind. 


## <a name="version-25330"></a>Version 2.5.33.0

**Veröffentlicht**: 10/23/2019

**Neue Funktionen:**

- Vorschauversion des [Scanners](../deploy-aip-scanner.md), um lokale Datenspeicher zu überprüfen und zu bezeichnen. Mit dieser Version des Scanners:
    
    - Wenn Sie die Scanner für die Verwendung desselben Scanner-Profils konfigurieren, können mehrere Scanner dieselbe SQL Server Datenbank gemeinsam nutzen. Diese Konfiguration erleichtert die Verwaltung mehrerer Scanner und führt zu schnelleren Scanzeiten. Wenn Sie diese Konfiguration verwenden, warten Sie immer, bis die Installation eines Scanners abgeschlossen ist, bevor Sie einen weiteren Scanner mit dem gleichen Profil installieren.
    
    - Sie müssen ein Profil angeben, wenn Sie den Scanner installieren, und die Scannerdatenbank hat den Namen **AIPScannerUL_\<profile_name >** . Der Parameter " *profile* " ist auch für "Set-aipscanner" obligatorisch.
    
    - Sie können in allen Dokumenten eine Standard Bezeichnung festlegen, auch wenn Dokumente bereits mit der Bezeichnung versehen sind. Legen Sie in den Überprüfungs Profil-oder Repository-Einstellungen die Option **Dateien** neu bezeichnen auf ein fest **, und aktivieren** Sie das Kontrollkästchen neue **Bezeichnung Standard Bezeichnung erzwingen** .
    
    - Sie können vorhandene Bezeichnungen aus allen Dokumenten entfernen, und dieser Vorgang umfasst das Entfernen des Schutzes, wenn dieser zuvor durch eine Bezeichnung angewendet wurde. Der Schutz, der unabhängig von einer Bezeichnung angewendet wird, wird beibehalten. Diese Scannerkonfiguration wird in den Einstellungen für das Scanner-Profil oder im Repository mit den folgenden Einstellungen erreicht:
        - Bezeichnungs **Dateien basierend auf dem Inhalt**: **Off**
        - **Standard Bezeichnung**: **keine**
        - **Dateien**neu bezeichnen: **aktivieren** Sie das Kontrollkästchen **Standard Bezeichnung erzwingen** ausgewählt haben.
    
    - Wie bei der Überprüfung des klassischen Clients schützt der Scanner standardmäßig Office-Dateien und PDF-Dateien. Sie können andere Dateitypen schützen, wenn Sie eine [Erweiterte PowerShell-Einstellung](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect)verwenden.
    
    - Ereignis-IDs für die Start-und Beendigungs Zyklen der Scanner werden nicht in das Windows-Ereignisprotokoll geschrieben. Verwenden Sie stattdessen die Azure-Portal für diese Informationen.
    
    - Bekanntes Problem: neue und umbenannte Bezeichnungen können nicht als Standard Bezeichnung für das Scanner-Profil oder die Repository-Einstellungen ausgewählt werden. Problemumgehungen:
        - Für neue Bezeichnungen: Fügen Sie im Azure-Portal [die Bezeichnung](../configure-policy-add-remove-label.md) , die Sie verwenden möchten, der globalen Richtlinie oder einer Bereichs bezogenen Richtlinie hinzu.
        - Umbenannte Bezeichnungen: Schließen Sie die Azure-Portal, und öffnen Sie Sie erneut.
    
    Sie können Scanner über den Azure Information Protection-Client (klassisch) aktualisieren. Nach dem Upgrade, mit dem eine neue Datenbank erstellt wird, werden bei der ersten Ausführung des Scanners alle Dateien neu erstellt. Anweisungen finden Sie unter [Aktualisieren des Azure Information Protection Scanners](clientv2-admin-guide.md#upgrading-the-azure-information-protection-scanner) im Administrator Handbuch.
    
    Weitere Informationen finden Sie im Blogbeitrag Ankündigung: [Unified-Bezeichnung AIP Scanner Preview sorgt für horizontales hochskalieren und mehr.](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Unified-labeling-AIP-scanner-preview-brings-scaling-out-and-more/ba-p/862552)

- Das PowerShell-Cmdlet " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " verfügt über neue Parameter ("*AppID*", " *appsecret*", " *tenantid*", " *delegateduser*" und " *onbehalfof*"), wenn Sie Dateien nicht interaktiv bezeichnen möchten, und auch ein neues Verfahren zum Registrieren einer APP in Azure AD. Beispiele für Szenarien sind der Scanner und automatisierte PowerShell-Skripts zum bezeichnen von Dokumenten. Anweisungen finden Sie unter Vorgehens [Weise beim nicht interaktiven bezeichnen von Dateien](clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection) im Administrator Handbuch.
    
    Beachten Sie, dass *delegateduser* ein neuer Parameter seit der letzten Vorschauversion des Unified-Bezeichnungs Clients ist und dass die API-Berechtigungen für die registrierte App folglich geändert wurden.

- Neue PowerShell-Bezeichnung für erweiterte Einstellungen, um [die zu schützenden Dateitypen zu ändern](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect).

- Neue PowerShell-Bezeichnung für erweiterte Einstellungen, um [die Regeln für die Bezeichnung Migration auf SharePoint-Eigenschaften auszuweiten](clientv2-admin-guide-customizations.md#extend-your-label-migration-rules-to-sharepoint-properties).

- Übereinstimmende benutzerdefinierte vertrauliche Informationstypen werden an [Azure Information Protection Analytics](../reports-aip.md)gesendet.

- Die angewendete Bezeichnung zeigt die konfigurierte Farbe für die Bezeichnung an, wenn eine [Farbe konfiguriert](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label)wurde.

- Beim Hinzufügen oder Ändern von Schutzeinstellungen zu einer Bezeichnung wird die Bezeichnung vom Client erneut mit den neuesten Schutzeinstellungen angewendet, wenn das Dokument das nächste Mal gespeichert wird. Auf ähnliche Weise wendet der Scanner die Bezeichnung erneut mit diesen aktuellen Schutzeinstellungen an, wenn das Dokument im Erzwingungs Modus das nächste Mal gescannt wird.

- [Unterstützung für nicht verbundene Computer](clientv2-admin-guide-customizations.md#support-for-disconnected-computers) durch Exportieren von Dateien von einem Client und manuelles Kopieren der Computer auf den getrennten Computer. Beachten Sie, dass diese Konfiguration für die Bezeichnung mit dem Datei-Explorer, PowerShell und dem Scanner unterstützt wird. Diese Konfiguration wird für die Bezeichnung mit Office-Apps nicht unterstützt.

- Neues Cmdlet " [Export-aiplogs](https://docs.microsoft.com/powershell/module/azureinformationprotection/export-aiplogs)", um alle Protokolldateien aus "%LocalAppData%\microsoft\msip\logs" zu erfassen und Sie in einer einzelnen komprimierten Datei mit dem ZIP-Format zu speichern. Diese Datei kann dann an Microsoft-Support gesendet werden, wenn Sie zum Untersuchen eines gemeldeten Problems aufgefordert werden, Protokolldateien zu senden.

**Fixes**

- Sie können mit dem Datei-Explorer erfolgreich Änderungen an einer geschützten Datei vornehmen und mit der rechten Maustaste klicken, nachdem ein Kennwort für die Datei entfernt wurde.

- Sie können nativ geschützte Dateien im Viewer öffnen, ohne dass das [Nutzungsrecht](../configure-usage-rights.md#usage-rights-and-descriptions)"Speichern unter", "exportieren (exportieren)" erforderlich ist.

- Bezeichnungen und Richtlinien Einstellungen werden erwartungsgemäß aktualisiert, ohne dass " [Clear-aipauthentication](/powershell/module/azureinformationprotection/clear-aipauthentication?)" ausgeführt werden muss, oder Sie müssen den Ordner "%LocalAppData%\microsoft\msip\mip" manuell löschen.

**Weitere Änderungen**

- Durch [Zurücksetzen](clientv2-admin-guide.md#more-information-about-the-reset-settings-option) werden nun die\>Ordner%LocalAppData%\microsoft\msip\mip\\ *\<ProcessName. exe* anstelle des Ordners%LocalAppData%\microsoft\msip\mip\\ *\<ProcessName\>* \mip gelöscht.

- " [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) " enthält jetzt die Inhalts-ID für ein geschütztes Dokument.

## <a name="version-22210"></a>Version 2.2.21.0

**Veröffentlicht**: 09/03/2019

Unterstützt durch 04/23/2020

**Fixes**

- Wenn Sie die erweiterte Einstellung [outlookdefaultlabel](clientv2-admin-guide-customizations.md#set-a-different-default-label-for-outlook) verwenden, um eine andere Standard Bezeichnung für Outlook festzulegen, und die angegebene Bezeichnung keine Unterbezeichnungen für die Bezeichnungs Richtlinie hat, wird die Bezeichnung ordnungsgemäß angewendet.

- Wenn der Azure Information Protection-Client in einer Office-App verwendet wird, wird ein Benutzer mit einem Active Directory Konto, das nicht für Single Sign-On konfiguriert ist, aufgefordert, sich für Azure Information Protection zu authentifizieren. Nach der erfolgreichen Authentifizierung wird der Client Status ordnungsgemäß in Online geändert, wodurch Bezeichnungs Funktionen aktiviert werden.

## <a name="version-22190"></a>Version 2.2.19.0

**Veröffentlicht**: 08/06/2019

Unterstützt durch 03/03/2020

**Fixes**

- Der Client kann seine Richtlinie herunterladen und die aktuellen Vertraulichkeits Bezeichnungen anzeigen. Diese Korrektur ist nach dem Upgrade von einer früheren Version erforderlich, und Sie haben keine benutzerdefinierten Informationstypen in Ihrem Beschriftungs Center konfiguriert.

- Allgemeine Verbesserungen der Leistung und Stabilität.

## <a name="next-steps"></a>Nächste Schritte

Nicht sicher, ob dies der richtige Client für die Installation ist?  Weitere Informationen finden [Sie unter Auswählen des zu verwendenden Kunden für Windows-Computer](use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

Weitere Informationen zum Installieren und verwenden dieses Clients finden Sie unter: 

- Für Benutzer: [Herunterladen und Installieren des Clients](install-unifiedlabelingclient-app.md)

- Für Administratoren: [Azure Information Protection Unified-Bezeichnung Client Administrator Handbuch](clientv2-admin-guide.md)

