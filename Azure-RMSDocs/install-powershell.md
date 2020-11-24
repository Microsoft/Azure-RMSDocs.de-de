---
title: Installieren Sie das PowerShell-Modul "aipservice" für Azure Information Protection
description: Anweisungen zum Installieren von PowerShell für den Schutzdienst von Azure Information Protection. Der Name dieses Moduls ist aipservice.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 57d8ac29ea58eab7820d642876e246b5ff985c4e
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568339"
---
# <a name="installing-the-aipservice-powershell-module"></a>Installieren des PowerShell-Moduls für AIPService

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Verwenden Sie die folgenden Informationen, um das Windows PowerShell-Modul für den Schutzdienst von Azure Information Protection zu installieren. Der Name dieses Moduls ist aipservice und ersetzt die vorherige Version mit dem Namen aadrm.

Sie können dieses PowerShell-Modul verwenden, um den Schutzdienst (Azure Rights Management) über die Befehlszeile zu verwalten, indem Sie einen beliebigen Windows-Computer verwenden, der über eine Internetverbindung verfügt und die im nächsten Abschnitt aufgeführten Voraussetzungen erfüllt. Windows PowerShell für Azure Information Protection unterstützt Skripts für die Automatisierung oder kann für erweiterte Konfigurationsszenarien erforderlich sein. Weitere Informationen zu den Verwaltungsaufgaben und Konfigurationen, die das Modul unterstützt, finden [Sie unter Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Voraussetzungen

In dieser Tabelle sind die Voraussetzungen für die Installation und Verwendung des aipservice-PowerShell-Moduls für den Schutzdienst von Azure Information Protection aufgeführt.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Mindestens erforderliche Version von Windows PowerShell: 3.0|Sie können die von Ihnen ausgeführte Version von Windows PowerShell überprüfen, indem Sie in einer PowerShell-Sitzung `$PSVersionTable` eingeben. <br /><br /> Falls Sie eine höhere Version von Windows PowerShell installieren müssen, lesen Sie die Informationen unter [Aktualisieren einer vorhandenen Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Mindestversion von Microsoft .NET Framework: 4.5<br /><br />Hinweis: Diese Version von Microsoft .NET Framework ist im Lieferumfang neuerer Betriebssysteme enthalten. Deshalb sollten Sie eine manuelle Installation nur dann durchführen müssen, wenn Sie ein Clientbetriebssystem vor Windows 8.0 oder ein Serverbetriebssystem vor Windows Server 2012 verwenden.|Wenn die Mindestversion des Microsoft .NET Frameworks nicht bereits installiert ist, können Sie [Microsoft .NET Framework 4,5](https://www.microsoft.com/download/details.aspx?id=30653)herunterladen.<br /><br />Diese Mindestversion des Microsoft .NET Frameworks ist für einige der Klassen erforderlich, die das aipservice-Modul verwendet.|

## <a name="if-you-have-the-aadrm-module-installed"></a>Wenn Sie das aadrm-Modul installiert haben

Das aipservice-Modul ersetzt das ältere Modul aadrm. Wenn Sie das ältere Modul installiert haben, deinstallieren Sie es, und installieren Sie dann das aipservice-Modul.

Das neuere Modul verfügt über Aliase für die Cmdlet-Namen im älteren Modul, sodass alle vorhandenen Skripts weiterhin funktionieren. Planen Sie jedoch, diese Verweise zu aktualisieren, bevor das alte Modul nicht mehr unterstützt wird. Die Unterstützung für das aadrm-Modul endet am 15. Juli 2020.

Wenn Sie das aadrm-Modul von der PowerShell-Katalog installiert haben, starten Sie zum Deinstallieren eine PowerShell-Sitzung mit der Option **als Administrator ausführen** , und geben Sie Folgendes ein:

```ps
Uninstall-Module -Name AADRM
```

Wenn Sie das aadrm-Modul mit dem Azure Rights Management-Verwaltungs Tool installiert haben, verwenden Sie **Programme und Funktionen** , um **Windows Azure AD Rights Management Administration** zu deinstallieren.

## <a name="how-to-install-the-aipservice-module"></a>Installieren des aipservice-Moduls

Das aipservice-Modul befindet sich auf dem [PowerShell-Katalog](https://www.powershellgallery.com/) und ist im Microsoft Download Center nicht verfügbar.

### <a name="to-install-the-aipservice-module-from-the-powershell-gallery"></a>So installieren Sie das aipservice-Modul über das PowerShell-Katalog

Wenn Sie noch nicht mit dem PowerShell-Katalog vertraut sind, finden Sie unter [Erste Schritte mit dem PowerShell-Katalog](/powershell/scripting/gallery/getting-started) weitere Informationen. Folgen Sie den Anweisungen, die zur Erfüllung der Kataloganforderungen erforderlich sind. Hierzu zählt die Installation des PowerShellGet-Moduls und des NuGet-Anbieters.

Weitere Informationen zum aipservice-Modul auf dem PowerShell-Katalog finden Sie auf der [Seite aipservice](https://www.powershellgallery.com/packages/AIPService).

Um das aipservice-Modul zu installieren, starten Sie eine PowerShell-Sitzung mit der Option **als Administrator ausführen** , und geben Sie Folgendes ein:

```ps
Install-Module -Name AIPService
```

Wenn Sie vor dem Installieren von einem nicht vertrauenswürdigen Repository gewarnt werden, können Sie Y zum Bestätigen drücken. Oder drücken Sie N, und konfigurieren Sie die PowerShell-Katalog als vertrauenswürdiges Repository mit dem Befehl, und führen Sie `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted` dann den Befehl erneut aus, um das aipservice-Modul zu installieren.  

Wenn Sie eine frühere Version des aipservice-Moduls aus dem Katalog installiert haben, aktualisieren Sie Sie auf den neuesten Wert, indem Sie Folgendes eingeben:

```ps
Update-Module -Name AIPService
```

## <a name="next-steps"></a>Nächste Schritte

Überprüfen Sie in einer Windows PowerShell-Sitzung die Version des installierten Moduls. Diese Überprüfung ist besonders wichtig, wenn Sie ein Upgrade von einer älteren Version durchgeführt haben:

```ps
(Get-Module AIPService –ListAvailable).Version
```

> [!NOTE]
> Wenn dieser Befehl fehlschlägt, führen Sie zuerst **Import-Module aipservice** aus.
> 

Geben Sie Folgendes ein, um die verfügbaren Cmdlets anzuzeigen:

```ps
Get-Command -Module AIPService
```

Verwenden Sie den Befehl `Get-Help <cmdlet_name>`, um Hilfe zu einem spezifischen Cmdlet anzuzeigen. Verwenden Sie den Parameter **-online**, um die neueste Hilfe auf der Microsoft-Dokumentationswebsite anzuzeigen. Beispiel:

```powershell
Get-Help Connect-AipService -online
```

Weitere Informationen finden Sie unter:

- Vollständige Liste der verfügbaren Cmdlets: [aipservice-Modul](/powershell/module/aipservice/)

- Liste der Haupt Konfigurationsszenarien, die PowerShell unterstützen: [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](administer-powershell.md)

Bevor Sie Befehle ausführen können, mit denen der Schutzdienst konfiguriert wird, müssen Sie eine Verbindung mit dem Dienst herstellen, indem Sie das Cmdlet [Connect-aipservice](/powershell/module/aipservice/connect-aipservice) verwenden.

Wenn Sie Ihre Konfigurations Befehle ausgeführt haben, sollten Sie als bewährte Vorgehensweise die Verbindung mit dem Dienst mithilfe des [Disconnect-aipservice](/powershell/module/aipservice/disconnect-aipservice) -Cmdlets trennen. Wenn Sie die Verbindung nicht trennen, wird sie nach einiger Zeit der Inaktivität automatisch getrennt. Aufgrund des Verhaltens zum automatischen Trennen der Verbindung kann es vorkommen, dass Sie während einer PowerShell-Sitzung gelegentlich die Verbindung neu herstellen müssen.

> [!NOTE]
> Wenn der Schutzdienst noch nicht aktiviert ist, können Sie dies nach dem Herstellen einer Verbindung mit dem Dienst durchführen, indem Sie das Cmdlet [enable-aipservice](/powershell/module/aipservice/enable-aipservice) verwenden.