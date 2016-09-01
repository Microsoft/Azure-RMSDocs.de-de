---
title: "Installieren der Windows PowerShell für Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 08/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 5f8672b1f4d8e1b5ed707e89e88c9ba50d24f486
ms.openlocfilehash: 4120aeeae7c2c48168e4f01de6558da5034bf019


---

# Installieren der Windows PowerShell für Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*

Verwenden Sie die folgenden Informationen als Hilfestellung bei der Installation von Windows PowerShell für Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS).

Mithilfe dieses PowerShell-Moduls können Sie [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] über die Befehlszeile verwalten, indem Sie einen Computer verwenden, der eine Internetverbindung besitzt und die im nächsten Abschnitt aufgeführten Voraussetzungen erfüllt. Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] unterstützt die Skripterstellung für die Automatisierung oder kann für erweiterte Konfigurationsszenarien erforderlich sein. Weitere Informationen zu den Verwaltungsaufgaben und Konfigurationen, die das Modul unterstützt, finden Sie unter [Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md).

## Voraussetzungen
In dieser Tabelle sind die Voraussetzungen für die Installation und Verwendung von Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] aufgeführt.

|Anforderung|Weitere Informationen|
|---------------|--------------------|
|Eine Version von Windows, die das [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul unterstützt|Überprüfen Sie die Liste der unterstützten Betriebssysteme im Bereich **Systemanforderungen** der [Downloadseite für das Azure Rights Management-Verwaltungstool](http://go.microsoft.com/fwlink/?LinkId=257721).|
|Mindestversion von Windows PowerShell: 2.0|Die Unterstützung für das [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul wurde in Windows PowerShell 2.0 eingeführt.<br /><br />Standardmäßig werden die meisten Windows-Betriebssysteme mindestens mit Version 2.0 der Windows PowerShell installiert. Wenn Sie Windows PowerShell 2.0 installieren müssen, finden Sie Informationen dazu unter [Installieren von Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx).<br /><br />Tipp: Sie können die von Ihnen ausgeführte Version von Windows PowerShell überprüfen, indem Sie in einer PowerShell-Sitzung `$PSVersionTable` eingeben.|
|Mindestversion von Microsoft .NET Framework: 4.5<br /><br />Hinweis: Diese Version von Microsoft .NET Framework ist im Lieferumfang neuerer Betriebssysteme enthalten. Deshalb sollten Sie eine manuelle Installation nur dann durchführen müssen, wenn Sie ein Clientbetriebssystem vor Windows 8.0 oder ein Serverbetriebssystem vor Windows Server 2012 verwenden.|Wenn die Mindestversion von Microsoft .NET Framework noch nicht installiert ist, können Sie [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653) herunterladen.<br /><br />Diese Mindestversion von Microsoft .NET Framework ist für einige Klassen erforderlich, die vom [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul verwendet werden.|

> [!NOTE]
> Ab Version 2.5.0.0 des Rights Management-Verwaltungsmoduls ist der Microsoft Online Services-Anmeldeassistent nicht mehr erforderlich.
> 
> Wenn Sie eine frühere Version des Rights Management-Verwaltungsmoduls installiert haben, deinstallieren Sie **Windows Azure AD Rights Management-Verwaltung** über **Programme und Funktionen**, bevor Sie die neueste Version installieren.


## Installieren des Rights Management-Administrationsmoduls

1.  Wechseln Sie zum Microsoft Download Center, und [laden Sie das Azure Rights Management-Verwaltungstool herunter](https://go.microsoft.com/fwlink/?LinkId=257721), in dem das [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Verwaltungsmodul für Windows PowerShell enthalten ist.

2.  Doppelklicken Sie in dem Ordner, in den Sie die [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Installationsprogrammdatei heruntergeladen und gespeichert haben, auf die ausführbare Datei, die Sie für Ihre Plattform (WindowsAzureADRightsManagementAdministration_x64.exe oder WindowsAzureADRightsManagementAdministration_x86.exe) heruntergeladen haben, um den Installations-Assistenten für die Azure AD Rights Management-Administration zu starten.

3.  Schließen Sie den Assistenten ab.

Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ist jetzt installiert.

## Nächste Schritte
Um anzuzeigen, welche Cmdlets verfügbar sind, starten Sie die Windows PowerShell mit der Option **Als Administrator ausführen** , und geben Sie Folgendes ein:

```
Get-Command -Module aadrm
```
Verwenden Sie den Befehl `the Get-Help <cmdlet_name>` , um die Hilfe für ein bestimmtes Cmdlet anzuzeigen.

Weitere Informationen finden Sie unter:

-   Vollständige Liste verfügbarer Cmdlets: [Azure Rights Management-Cmdlets](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Liste mit den Hauptkonfigurationsszenarien, die Windows PowerShell unterstützen: [Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md)

Vor dem Ausführen von Befehlen, die den [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Dienst konfigurieren, müssen Sie mithilfe des [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx)-Cmdlets eine Verbindung mit dem Dienst herstellen. Wenn Sie die gewünschten Konfigurationsbefehle ausgeführt haben, trennen Sie den Dienst mithilfe des [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) -Cmdlets.

> [!NOTE]
> Wenn Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] noch nicht aktiviert haben, können Sie dies nach der Dienstverbindung mithilfe des [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx)-Cmdlets nachholen.

## Siehe auch
[Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md)



<!--HONumber=Aug16_HO3-->


