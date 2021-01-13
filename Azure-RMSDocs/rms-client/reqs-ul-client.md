---
title: Zusätzliche Anforderungen für die Installation des Azure Information Protection Unified Bezeichnung-Clients
description: Informationen für Administratoren, die die zusätzlichen Systemanforderungen für die Installation des Unified-Bezeichnungs Clients in Unternehmensnetzwerken verstehen müssen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/07/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: dbd9d86e1ce2103f144e51314950cf67be31eef6
ms.sourcegitcommit: 78c7ab80be7c292ea4bc62954a4e29c449e97439
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "98164384"
---
# <a name="additional-requirements-for-installing-the-unified-labeling-client-on-enterprise-networks"></a>Zusätzliche Anforderungen für die Installation des Unified-Bezeichnungs Clients in Unternehmensnetzwerken

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen [unter AIP für Windows und Office-Versionen unter Erweiterter Support](../known-issues.md#aip-for-windows-and-office-versions-in-extended-support).*
>
>***Relevant für**: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie im [klassischen Client Administrator Handbuch](client-admin-guide-install.md). *

Überprüfen Sie vor der Installation des Azure Information Protection Unified Bezeichnung-Clients in Ihrem Unternehmensnetzwerk, ob die Computer über die erforderlichen Betriebssystemversionen und Anwendungen für Azure Information Protection verfügen: [Anforderungen für Azure Information Protection](../requirements.md). 

Vergewissern Sie sich anschließend, dass Sie über die zusätzlichen Elemente verfügen, die zum Installieren des Azure Information Protection Unified-Bezeichnungs Clients erforderlich sind

> [!NOTE]
> Nicht alle diese Anforderungen werden von der Installationssoftware überprüft.
>

## <a name="microsoft-net-framework-requirements"></a>Microsoft .NET Framework-Anforderungen

Die vollständige Installation des Azure Information Protection Unified Bezeichnung-Clients erfordert standardmäßig eine Mindestversion von Microsoft .NET Framework 4.6.2. 

Wenn dieses Framework fehlt, versucht der Setup-Assistent des ausführbaren Installationsprogramms, diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.  

Wenn Sie den [Azure Information Protection Viewer](clientv2-view-use-files.md) eigenständig installieren, müssen Sie über eine Mindestversion von Microsoft .NET Framework 4.5.2 verfügen. 

> [!IMPORTANT]
> Wenn für die Viewer-Installation mindestens eine Version von Microsoft .NET Framework 4.5.2 fehlt, wird Sie von der Installationssoftware *nicht* heruntergeladen oder installiert.
> 

### <a name="disable-exploit-protection-net-2-or-3-only"></a>Exploit-Schutz deaktivieren (nur .NET 2 oder 3)

Der AIP-Client wird auf Computern mit .NET 2 oder 3, für die der [Exploit-Schutz](/windows/security/threat-protection/microsoft-defender-atp/enable-exploit-protection) aktiviert ist, nicht unterstützt. 

In solchen Fällen empfiehlt es sich, die .NET-Version zu aktualisieren. 

Wenn Sie die .NET-Version 2 oder 3 beibehalten müssen, stellen Sie sicher, dass Sie den [Exploit-Schutz deaktivieren](../known-issues.md#known-issues-for-aip-and-exploit-protection) , bevor Sie den AIP-Client installieren.

## <a name="windows-powershell-minimum-requirements"></a>Mindestanforderungen für Windows PowerShell

Das PowerShell-Modul für den Client erfordert eine Mindestversion von Windows PowerShell 4,0.

Wenn Sie ein älteres Betriebssystem verwenden, müssen Sie möglicherweise alle PowerShell-Skripts manuell durcharbeiten. Weitere Informationen finden Sie unter [How to Install Windows PowerShell 4.0](https://social.technet.microsoft.com/wiki/contents/articles/21016.how-to-install-windows-powershell-4-0.aspx) (Installieren von Windows PowerShell 4.0). 

> [!IMPORTANT]
> Diese Voraussetzung wird vom Installationsprogramm *nicht* überprüft oder installiert. 
>
> Zum Überprüfen, welche Version von Windows PowerShell auf dem Computer ausgeführt wird, geben Sie `$PSVersionTable` in einer PowerShell-Sitzung ein.  
> 


## <a name="screen-resolution-requirements"></a>Anforderungen an die Bildschirmauflösung

Client Computer mit Auflösungen von **800 x 600** und niedriger können das Dialogfeld **klassifizieren und schützen-Azure Information Protection** nicht vollständig anzeigen, wenn Sie mit der rechten Maustaste auf eine Datei oder einen Ordner im Datei-Explorer klicken.   

## <a name="admin-permissions"></a>Administrator Berechtigungen

Um den Azure Information Protection Unified Bezeichnung-Client zu installieren, müssen Sie auf dem Client Computer über lokale Administratorrechte verfügen.
        
## <a name="windows-10-requirements"></a>Windows 10-Anforderungen

Für Computer, auf denen Office 2010 ausgeführt wird, ist die **Microsoft Online Services-Anmelde-Assistent-Version 7.250.4303.0** erforderlich, die in der Client Installation enthalten ist. 

Wenn Sie über eine spätere Version des Anmelde-Assistenten verfügen, deinstallieren Sie diese, bevor Sie den Azure Information Protection Unified Bezeichnung-Client installieren. 

Überprüfen Sie beispielsweise die Version, und deinstallieren Sie den Anmelde Assistenten mithilfe der **System Steuerungs** Option  >  **Programm und Features**  >  **deinstallieren oder ändern Sie ein Programm**. 

Installieren Sie [1. März 2019 – KB4482887 (Betriebssystembuild 17763.348)](https://support.microsoft.com/help/4482887/windows-10-update-kb4482887) nur für die Windows 10-Version 1809 mit Betriebssystembuilds, die älter sind als 17763.348, damit die Information Protection-Leiste in Office-Anwendungen korrekt angezeigt wird. Dieses Update ist nicht nötig, wenn Sie Office 365 in der Version 1902 oder höher haben.    

## <a name="configure-your-group-policy-to-prevent-disabling-aip"></a>Konfigurieren Sie die Gruppenrichtlinie, um das Deaktivieren von AIP zu verhindern.

Für Office-Versionen 2013 und höher wird empfohlen, die Gruppenrichtlinie so zu konfigurieren, dass das **Microsoft Azure Information Protection** -Add-in für Office-Anwendungen immer aktiviert ist.  Ohne dieses Add-in können Benutzer Ihre Dokumente oder e-Mails in Office-Anwendungen nicht bezeichnen.   

Verwenden Sie für Word, Excel, PowerPoint und Outlook die Liste mit den Gruppenrichtlinien Einstellungen **der verwalteten Add-ins** , die in [keine Add-Ins geladen wurden, die aufgrund von Gruppenrichtlinien Einstellungen für Office 2013-und Office 2016-Programme geladen](https://support.microsoft.com/help/2733070/no-add-ins-loaded-due-to-group-policy-settings-for-office-2013-and-off)wurden. 

Geben Sie die folgenden programmgesteuerten Bezeichner (ProgID) für AIP an, und legen Sie die Option auf **1 fest: das Add-in ist immer aktiviert**.

|Application  |ProgID  |
|---------|---------|
|Word     |     `MSIP.WordAddin`    |
|Excel     |  `MSIP.ExcelAddin`       |
|PowerPoint     |   `MSIP.PowerPointAddin`      |
|Outlook | `MSIP.OutlookAddin` |
| | | 

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie mit  [dem Administrator Handbuch fort: Installieren Sie den Azure Information Protection Unified Bezeichnung-Client für Benutzer](clientv2-admin-guide-install.md).

Weitere Informationen finden Sie unter

- [Clientdateien und Nutzungsprotokollierung](clientv2-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](clientv2-admin-guide-file-types.md)

- [PowerShell-Befehle](clientv2-admin-guide-powershell.md)