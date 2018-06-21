---
title: Installieren von PowerShell für AADRM – AIP
description: Hier finden Sie Anweisungen zum Installieren der Windows PowerShell für den Azure Rights Management-Dienst von Azure Information Protection. Der Name dieses Moduls lautet AADRM.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 04/23/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e69714fdb983d7235c7fca940bebc37a14892397
ms.sourcegitcommit: 5892db302bdf96538ecb3af8e3c2f678f5d1ebe2
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31817143"
---
# <a name="installing-the-aadrm-powershell-module"></a>Installieren des PowerShell-Moduls für AADRM

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Die folgenden Informationen helfen Ihnen beim Installieren des Windows PowerShell-Moduls für den Azure Rights Management-Dienst von Azure Information Protection. Der Name dieses Moduls lautet AADRM.

Mithilfe dieses PowerShell-Moduls können Sie den Azure Rights Management-Dienst über die Befehlszeile verwalten, indem Sie einen Computer verwenden, der über eine Internetverbindung verfügt und die im nächsten Abschnitt aufgeführten Voraussetzungen erfüllt. Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] unterstützt die Skripterstellung für die Automatisierung oder kann für erweiterte Konfigurationsszenarien erforderlich sein. Weitere Informationen zu den Verwaltungsaufgaben und Konfigurationen, die das Modul unterstützt, finden Sie unter [Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Voraussetzungen
Die folgende Tabelle enthält Installations- und Benutzungsanforderungen an das AADRM-PowerShell-Modul für den Azure Rights Management-Dienst von Azure Information Protection.

|Anforderungen|Weitere Informationen|
|---------------|--------------------|
|Mindestens erforderliche Version von Windows PowerShell: 3.0|Sie können die von Ihnen ausgeführte Version von Windows PowerShell überprüfen, indem Sie in einer PowerShell-Sitzung `$PSVersionTable` eingeben. <br /><br /> Wenn Sie eine neuere Version von Windows PowerShell installieren müssen, finden Sie weitere Informationen dazu unter [Aktualisieren einer vorhandenen Version von Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Mindestversion von Microsoft .NET Framework: 4.5<br /><br />Hinweis: Diese Version von Microsoft .NET Framework ist im Lieferumfang neuerer Betriebssysteme enthalten. Deshalb sollten Sie eine manuelle Installation nur dann durchführen müssen, wenn Sie ein Clientbetriebssystem vor Windows 8.0 oder ein Serverbetriebssystem vor Windows Server 2012 verwenden.|Wenn die Mindestversion von Microsoft .NET Framework noch nicht installiert ist, können Sie [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653) herunterladen.<br /><br />Diese Mindestversion von Microsoft .NET Framework ist für einige Klassen erforderlich, die vom AADRM-Modul verwendet werden.|

Ab Version 2.5.0.0 des AADRM-Moduls ist der Microsoft Online Services-Anmeldeassistent nicht mehr erforderlich.

> [!NOTE]
> 
> Wenn Sie eine Version des AADRM-Moduls mit dem Azure Rights Management Verwaltungstool installiert haben, nutzen Sie **Programme und Features**, um **Windows Azure AD Rights Management Administration** zu deinstallieren, bevor Sie die neueste Version des AADRM-Moduls aus dem PowerShell-Katalog installieren.


## <a name="how-to-install-the-aadrm-module"></a>Installieren des AADRM-Moduls

Das AADRM-Modul wurde in den [PowerShell-Katalog](/powershell/gallery/readme) verschoben, und ist nicht mehr aus dem Microsoft Download Center verfügbar. 

### <a name="to-install-the-aadrm-module-from-the-powershell-gallery"></a>Installieren des AADRM-Moduls über den PowerShell-Katalog

Wenn Sie noch nicht mit dem PowerShell-Katalog vertraut sind, finden Sie unter [Erste Schritte mit dem PowerShell-Katalog](/powershell/gallery/psgallery/psgallery_gettingstarted) weitere Informationen. Folgen Sie den Anweisungen, die zur Erfüllung der Kataloganforderungen erforderlich sind. Hierzu zählt die Installation des PowerShellGet-Moduls und des NuGet-Anbieters.

Details zum AADRM-Modul im PowerShell-Katalog finden Sie auf der [AADRM-Seite](https://www.powershellgallery.com/packages/AADRM).

Um das AADRM-Modul zu installieren, starten Sie eine PowerShell-Sitzung mit der Option **Als Administrator ausführen**, und geben Folgendes ein:

    Install-Module -Name AADRM

Wenn Sie vor dem Installieren von einem nicht vertrauenswürdigen Repository gewarnt werden, können Sie Y zum Bestätigen drücken. Alternativ drücken Sie N, und konfigurieren den PowerShell-Katalog als vertrauenswürdiges Repository mithilfe des Befehls `Set-PSRepository -Name PSGallery -InstallationPolicy Trusted`, und führen den Befehl zum Installieren des AADRM-Moduls dann erneut aus.  

Wenn Sie eine frühere Version des AADRM-Moduls aus dem Katalog installiert haben, aktualisieren Sie es, indem Sie Folgendes eingeben:

    Update-Module -Name AADRM


## <a name="next-steps"></a>Nächste Schritte
Überprüfen Sie in einer Windows PowerShell-Sitzung die Version des installierten Moduls. Diese Überprüfung ist besonders wichtig, wenn Sie ein Upgrade von einer älteren Version durchgeführt haben:

```
(Get-Module AADRM –ListAvailable).Version
```

Hinweis: Wenn dieser Befehl nicht erfolgreich ist, führen Sie zunächst **Import-Module AADRM** aus.

Geben Sie Folgendes ein, um die verfügbaren Cmdlets anzuzeigen:

```
Get-Command -Module AADRM
```

Verwenden Sie den Befehl `Get-Help <cmdlet_name>`, um Hilfe zu einem spezifischen Cmdlet anzuzeigen. Verwenden Sie den Parameter **-online**, um die neueste Hilfe auf der Microsoft-Dokumentationswebsite anzuzeigen. Beispiel:

```
Get-Help Connect-AadrmService -online
```

Weitere Informationen finden Sie unter:

-   Vollständige Liste der verfügbaren Cmdlets: [AADRM-Modul](/powershell/aadrm/vlatest/rightsmanagement)

-   Liste mit den Hauptkonfigurationsszenarien, die PowerShell unterstützen: [Verwalten des Azure Rights Management-Diensts mithilfe von Windows PowerShell](administer-powershell.md)

Vor dem Ausführen von Befehlen, die den [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Dienst konfigurieren, müssen Sie mithilfe des Cmdlets [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) eine Verbindung mit dem Dienst herstellen. Wenn Sie die gewünschten Konfigurationsbefehle ausgeführt haben, trennen Sie als Best Practice den Dienst mithilfe des Cmdlets [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). Wenn Sie die Verbindung nicht trennen, wird sie nach einiger Zeit der Inaktivität automatisch getrennt. Aufgrund des Verhaltens zum automatischen Trennen der Verbindung kann es vorkommen, dass Sie während einer PowerShell-Sitzung gelegentlich die Verbindung neu herstellen müssen. 

> [!NOTE]
> Wenn der Azure Rights Management-Dienst noch nicht aktiviert wurde, können Sie dies nach dem Herstellen der Verbindung mit dem Dienst mithilfe des Cmdlets [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm) nachholen.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]