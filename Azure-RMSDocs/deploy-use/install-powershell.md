---
title: "Installieren von PowerShell für Azure Rights Management – AIP"
description: "Hier finden Sie Anweisungen zum Installieren der Windows PowerShell für den Azure Rights Management-Dienst von Azure Information Protection. Der Name dieses Moduls lautet AADRM."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/13/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 5946ab7315b646abf119cb32cd66ac62535253c9
ms.sourcegitcommit: c157636577db2e2a2ba5df81eb985800cdb82054
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2018
---
# <a name="installing-windows-powershell-for-azure-rights-management"></a>Installieren der Windows PowerShell für Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Die folgenden Informationen helfen Ihnen beim Installieren des Windows PowerShell-Moduls für den Azure Rights Management-Dienst von Azure Information Protection.

Mithilfe dieses PowerShell-Moduls können Sie den Azure Rights Management-Dienst über die Befehlszeile verwalten, indem Sie einen Computer verwenden, der über eine Internetverbindung verfügt und die im nächsten Abschnitt aufgeführten Voraussetzungen erfüllt. Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] unterstützt die Skripterstellung für die Automatisierung oder kann für erweiterte Konfigurationsszenarien erforderlich sein. Weitere Informationen zu den Verwaltungsaufgaben und Konfigurationen, die das Modul unterstützt, finden Sie unter [Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md).

## <a name="prerequisites"></a>Voraussetzungen
In dieser Tabelle sind die Voraussetzungen für die Installation und Verwendung von Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] aufgeführt.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Eine Version von Windows, die das [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul unterstützt|Überprüfen Sie die Liste der unterstützten Betriebssysteme im Bereich **Systemanforderungen** der [Downloadseite für das Azure Rights Management-Verwaltungstool](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Mindestens erforderliche Version von Windows PowerShell: 3.0|Sie können die von Ihnen ausgeführte Version von Windows PowerShell überprüfen, indem Sie in einer PowerShell-Sitzung `$PSVersionTable` eingeben. <br /><br /> Wenn Sie eine neuere Version von Windows PowerShell installieren müssen, finden Sie weitere Informationen dazu unter [Aktualisieren einer vorhandenen Version von Windows PowerShell](/powershell/scripting/setup/installing-windows-powershell#upgrading-existing-windows-powershell).|
|Mindestversion von Microsoft .NET Framework: 4.5<br /><br />Hinweis: Diese Version von Microsoft .NET Framework ist im Lieferumfang neuerer Betriebssysteme enthalten. Deshalb sollten Sie eine manuelle Installation nur dann durchführen müssen, wenn Sie ein Clientbetriebssystem vor Windows 8.0 oder ein Serverbetriebssystem vor Windows Server 2012 verwenden.|Wenn die Mindestversion von Microsoft .NET Framework noch nicht installiert ist, können Sie [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653) herunterladen.<br /><br />Diese Mindestversion von Microsoft .NET Framework ist für einige Klassen erforderlich, die vom [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul verwendet werden.|

> [!NOTE]
> Ab Version 2.5.0.0 des Rights Management-Verwaltungsmoduls ist der Microsoft Online Services-Anmeldeassistent nicht mehr erforderlich.
> 
> Wenn Sie eine frühere Version des Rights Management-Verwaltungsmoduls installiert haben, deinstallieren Sie **Windows Azure AD Rights Management-Verwaltung** über **Programme und Funktionen**, bevor Sie die neueste Version installieren.


## <a name="how-to-install-the-rights-management-administration-module"></a>Installieren des Rights Management-Administrationsmoduls

1. Wechseln Sie zum Microsoft Download Center, und suchen Sie das [Azure Rights Management-Verwaltungstool](https://go.microsoft.com/fwlink/?LinkId=257721), in dem das [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Verwaltungsmodul für Windows PowerShell enthalten ist.

2. Laden Sie die [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Installationsdatei (**WindowsAzureADRightsManagementAdministration_x64**) herunter, und speichern Sie diese. Doppelklicken Sie anschließend auf diese Datei, um den Assistenten für das Setup der Azure AD Rights Management-Administration zu starten.

3.  Schließen Sie den Assistenten ab.

Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ist jetzt installiert.

## <a name="next-steps"></a>Nächste Schritte
Starten Sie eine Windows PowerShell-Sitzung, und überprüfen Sie die Version des installierten Moduls. Diese Überprüfung ist besonders wichtig, wenn Sie ein Upgrade von einer älteren Version durchgeführt haben:

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

Vor dem Ausführen von Befehlen, die den [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Dienst konfigurieren, müssen Sie mithilfe des Cmdlets [Connect-AadrmService](/powershell/aadrm/vlatest/connect-aadrmservice) eine Verbindung mit dem Dienst herstellen. 

Wenn Sie die gewünschten Konfigurationsbefehle ausgeführt haben, trennen Sie als Best Practice den Dienst mithilfe des Cmdlets [Disconnect-AadrmService](/powershell/aadrm/vlatest/disconnect-aadrmservice). Wenn Sie die Verbindung nicht trennen, wird sie nach einiger Zeit der Inaktivität automatisch getrennt. Aufgrund des Verhaltens zum automatischen Trennen der Verbindung kann es vorkommen, dass Sie während einer PowerShell-Sitzung gelegentlich die Verbindung neu herstellen müssen. 

> [!NOTE]
> Wenn der Azure Rights Management-Dienst noch nicht aktiviert wurde, können Sie dies nach dem Herstellen der Verbindung mit dem Dienst mithilfe des Cmdlets [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm) nachholen.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]