---
title: "Installieren der Windows PowerShell für Azure Rights Management | Azure Information Protection"
description: "Hier finden Sie Anweisungen zum Installieren der Windows PowerShell für den Azure Rights Management-Dienst von Azure Information Protection. Der Name dieses Moduls lautet AADRM."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 0d665ed6-b1de-4d63-854a-bc57c1c49844
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 11f884779316626f81b3f75b9562ce58646f6ba3


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
|Mindestversion von Windows PowerShell: 2.0|Die Unterstützung für das [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul wurde in Windows PowerShell 2.0 eingeführt.<br /><br />Standardmäßig werden die meisten Windows-Betriebssysteme mindestens mit Version 2.0 der Windows PowerShell installiert. Wenn Sie Windows PowerShell 2.0 installieren müssen, finden Sie Informationen dazu unter [Installieren von Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx).<br /><br />Tipp: Sie können die von Ihnen ausgeführte Version von Windows PowerShell überprüfen, indem Sie in einer PowerShell-Sitzung `$PSVersionTable` eingeben.|
|Mindestversion von Microsoft .NET Framework: 4.5<br /><br />Hinweis: Diese Version von Microsoft .NET Framework ist im Lieferumfang neuerer Betriebssysteme enthalten. Deshalb sollten Sie eine manuelle Installation nur dann durchführen müssen, wenn Sie ein Clientbetriebssystem vor Windows 8.0 oder ein Serverbetriebssystem vor Windows Server 2012 verwenden.|Wenn die Mindestversion von Microsoft .NET Framework noch nicht installiert ist, können Sie [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653) herunterladen.<br /><br />Diese Mindestversion von Microsoft .NET Framework ist für einige Klassen erforderlich, die vom [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Administrationsmodul verwendet werden.|

> [!NOTE]
> Ab Version 2.5.0.0 des Rights Management-Verwaltungsmoduls ist der Microsoft Online Services-Anmeldeassistent nicht mehr erforderlich.
> 
> Wenn Sie eine frühere Version des Rights Management-Verwaltungsmoduls installiert haben, deinstallieren Sie **Windows Azure AD Rights Management-Verwaltung** über **Programme und Funktionen**, bevor Sie die neueste Version installieren.


## <a name="how-to-install-the-rights-management-administration-module"></a>Installieren des Rights Management-Administrationsmoduls

1.  Wechseln Sie zum Microsoft Download Center, und [laden Sie das Azure Rights Management-Verwaltungstool herunter](https://go.microsoft.com/fwlink/?LinkId=257721), in dem das [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Verwaltungsmodul für Windows PowerShell enthalten ist.

2.  Doppelklicken Sie in dem Ordner, in den Sie die [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Installationsprogrammdatei heruntergeladen und gespeichert haben, auf die ausführbare Datei, die Sie für Ihre Plattform (WindowsAzureADRightsManagementAdministration_x64.exe oder WindowsAzureADRightsManagementAdministration_x86.exe) heruntergeladen haben, um den Installations-Assistenten für die Azure AD Rights Management-Administration zu starten.

3.  Schließen Sie den Assistenten ab.

Windows PowerShell für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ist jetzt installiert.

## <a name="next-steps"></a>Nächste Schritte
Um anzuzeigen, welche Cmdlets verfügbar sind, starten Sie die Windows PowerShell mit der Option **Als Administrator ausführen** , und geben Sie Folgendes ein:

```
Get-Command -Module aadrm
```
Verwenden Sie den Befehl `the Get-Help <cmdlet_name>` , um die Hilfe für ein bestimmtes Cmdlet anzuzeigen.

Weitere Informationen finden Sie unter:

-   Vollständige Liste verfügbarer Cmdlets: [Azure Rights Management-Cmdlets](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

-   Liste mit den Hauptkonfigurationsszenarien, die Windows PowerShell unterstützen: [Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md)

Vor dem Ausführen von Befehlen, die den [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Dienst konfigurieren, müssen Sie mithilfe des Cmdlets [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) eine Verbindung mit dem Dienst herstellen. Wenn Sie die gewünschten Konfigurationsbefehle ausgeführt haben, trennen Sie den Dienst mithilfe des [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) -Cmdlets.

> [!NOTE]
> Azure Rights Management-Dienst noch nicht aktiviert wurde, können Sie dies nach dem Herstellen der Verbindung mit dem Dienst mithilfe des Cmdlets [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) nachholen.

## <a name="see-also"></a>Weitere Informationen
[Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](administer-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


