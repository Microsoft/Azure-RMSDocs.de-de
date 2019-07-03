---
title: Installieren Sie das AIPService-PowerShell-Modul für Azure Information Protection
description: Anweisungen zum Installieren von PowerShell für den Schutzdienst von Azure Information Protection. Der Name dieses Moduls ist AIPService.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c986b34f3138a3410cb0d675c016206a752ad0c8
ms.sourcegitcommit: a2542aec8cd2bf96e94923740bf396badff36b6a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67535021"
---
# <a name="installing-the-aipservice-powershell-module"></a>Installieren des AIPService PowerShell-Moduls

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Verwenden Sie die folgende Informationen, um Ihnen bei der Installation des Windows PowerShell-Moduls für den Schutzdienst von Azure Information Protection. Der Name dieses Moduls ist AIPService und ersetzt die vorherige Version, die AADRM benannt wurde.

Sie können dieses PowerShell-Modul verwenden zum Verwalten des schutzdiensts (Azure Rights Management) von der Befehlszeile aus mit einem beliebigen Computer, die über eine Internetverbindung verfügt und, die im nächsten Abschnitt aufgeführten Voraussetzungen erfüllt. Windows PowerShell für Azure Information Protection unterstützt die Skripterstellung für die Automatisierung oder kann für erweiterte Konfigurationsszenarien erforderlich sein. Weitere Informationen zu den Verwaltungsaufgaben und Konfigurationen, die das Modul unterstützt, finden Sie unter [Schutz von Azure Information Protection mithilfe von PowerShell verwalten](administer-powershell.md).

## <a name="prerequisites"></a>Vorraussetzungen
Diese Tabelle enthält die Voraussetzungen zum Installieren und verwenden das AIPService-PowerShell-Modul für den Schutzdienst von Azure Information Protection.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Die Mindestversion von Windows PowerShell: 3.0|Sie können die von Ihnen ausgeführte Version von Windows PowerShell überprüfen, indem Sie in einer PowerShell-Sitzung `$PSVersionTable` eingeben. <br /><br /> Wenn Sie eine neuere Version von Windows PowerShell installieren müssen, finden Sie weitere Informationen dazu unter [Aktualisieren einer vorhandenen Version von Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Mindestversion von Microsoft .NET Framework: 4.5<br /><br />Hinweis: Diese Version von Microsoft .NET Framework ist in der neuerer Betriebssysteme enthalten, deshalb sollten Sie eine manuelle Installation nur dann, wenn das Clientbetriebssystem vor Windows 8.0 oder Serverbetriebssystem kleiner als Windows Server 2012 müssen.|Wenn die Mindestversion von Microsoft .NET Framework noch nicht installiert ist, können Sie [Microsoft .NET Framework 4.5](https://www.microsoft.com/download/details.aspx?id=30653) herunterladen.<br /><br />Diese Mindestversion von Microsoft .NET Framework ist erforderlich für einige der Klassen, die das Modul AIPService verwendet.|

## <a name="if-you-have-the-aadrm-module-installed"></a>Wenn Sie das AADRM-Modul installiert haben

Das AIPService-Modul ersetzt das ältere Modul AADRM. Wenn Sie das ältere-Modul installiert haben, deinstallieren Sie sie aus, und klicken Sie dann installieren Sie das AIPService-Modul zu.

Das neuere Modul verfügt über Aliase, um die Cmdlet-Namen im älteren-Modul aus, damit alle vorhandenen Skripts weiterhin funktionsfähig ist. Planen Sie jedoch so aktualisieren Sie diese Verweise, bevor das alte-Modul nicht mehr unterstützt fällt. Unterstützung für das AADRM-Modul wird 15 Juli 2020 beendet.

Wenn Sie das AADRM-Modul mit dem Azure Rights Management-Verwaltungstool installiert haben, verwenden Sie **Programme und Funktionen** Deinstallieren **Verwaltung von Windows Azure AD Rights Management**.


## <a name="how-to-install-the-aipservice-module"></a>Gewusst wie: Installieren des Moduls AIPService

Das AIPService-Modul ist, auf die [PowerShell-Katalog](/powershell/gallery/readme) und nicht aus dem Microsoft Download Center verfügbar ist. 

### <a name="to-install-the-aipservice-module-from-the-powershell-gallery"></a>Zum Installieren des AIPService-Moduls aus dem PowerShell-Katalog

Wenn Sie noch nicht mit dem PowerShell-Katalog vertraut sind, finden Sie unter [Erste Schritte mit dem PowerShell-Katalog](/powershell/gallery/psgallery/psgallery_gettingstarted) weitere Informationen. Folgen Sie den Anweisungen, die zur Erfüllung der Kataloganforderungen erforderlich sind. Hierzu zählt die Installation des PowerShellGet-Moduls und des NuGet-Anbieters.

Details zum AIPService-Modul im PowerShell-Katalog finden auf die [AIPService Seite](https://www.powershellgallery.com/packages/AIPService).

Um das AIPService-Modul zu installieren, starten Sie eine PowerShell-Sitzung mit dem **als Administrator ausführen** Option, und geben:

    Install-Module -Name AIPService

Wenn Sie vor dem Installieren von einem nicht vertrauenswürdigen Repository gewarnt werden, können Sie Y zum Bestätigen drücken. Alternativ drücken Sie N und Konfigurieren der PowerShell-Katalog als vertrauenswürdiges Repository mithilfe des Befehls `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted` und führen Sie den Befehl zum Installieren des Moduls AIPService erneut aus.  

Wenn Sie eine frühere Version des Moduls AIPService aus dem Katalog installiert haben, aktualisieren Sie es auf die neueste Version, indem Sie eingeben:

    Update-Module -Name AIPService


## <a name="next-steps"></a>Nächste Schritte
Überprüfen Sie in einer Windows PowerShell-Sitzung die Version des installierten Moduls. Diese Überprüfung ist besonders wichtig, wenn Sie ein Upgrade von einer älteren Version durchgeführt haben:

```
(Get-Module AIPService –ListAvailable).Version
```

Hinweis: Wenn Sie diesen Befehl ein Fehler auftritt, führen Sie zunächst **Import-Module AIPService**.

Geben Sie Folgendes ein, um die verfügbaren Cmdlets anzuzeigen:

```
Get-Command -Module AIPService
```

Verwenden Sie den Befehl `Get-Help <cmdlet_name>`, um Hilfe zu einem spezifischen Cmdlet anzuzeigen. Verwenden Sie den Parameter **-online**, um die neueste Hilfe auf der Microsoft-Dokumentationswebsite anzuzeigen. Zum Beispiel:

```
Get-Help Connect-AipService -online
```

Weitere Informationen finden Sie unter:

-   Vollständige Liste der verfügbaren Cmdlets: [AIPService-Modul](/powershell/module/aipservice/?view=azureipps#aipservice)

-   Liste der hauptkonfigurationsszenarien, die PowerShell unterstützen: [Verwalten von Schutz von Azure Information Protection mithilfe von PowerShell](administer-powershell.md)

Bevor Sie Befehle, die den Schutzdienst zu konfigurieren ausführen können, Sie müssen eine Verbindung herstellen mit dem Dienst mithilfe der [Connect-AipService](/powershell/module/aipservice/connect-aipservice) Cmdlet.

Wenn Sie die gewünschten Konfigurationsbefehle ausgeführt, als bewährte Methode abgeschlossen haben, trennen Sie den Dienst mithilfe der [Disconnect-AipService](/powershell/module/aipservice/disconnect-aipservice) Cmdlet. Wenn Sie die Verbindung nicht trennen, wird sie nach einiger Zeit der Inaktivität automatisch getrennt. Aufgrund des Verhaltens zum automatischen Trennen der Verbindung kann es vorkommen, dass Sie während einer PowerShell-Sitzung gelegentlich die Verbindung neu herstellen müssen. 

> [!NOTE]
> Wenn Sie noch nicht der Schutzdienst aktiviert ist, hierzu können Sie nach dem Sie mit dem Dienst verbunden haben, mit der [aktivieren-AipService](/powershell/module/aipservice/enable-aipservice) Cmdlet.

