---
title: Herunterladen und Installieren des Azure Information Protection-Clients
description: Anweisungen für Benutzer zum Installieren des Azure Information Protection-Clients für Windows, damit Sie Ihre Dokumente und E-Mails klassifizieren und schützen können.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: d45c13a0cf3c7725c5b817339e9aadec96f27477
ms.sourcegitcommit: 1d2912b4f0f6e8d7596cbf31e2143a783158ab11
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/12/2018
ms.locfileid: "53305221"
---
# <a name="user-guide-download-and-install-the-azure-information-protection-client"></a>Leitfaden: Herunterladen und Installieren des Azure Information Protection-Clients

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Wenn Ihr Administrator den Azure Information Protection-Client nicht für Sie installiert, können Sie dies selbst übernehmen. Sie müssen ein lokaler Administrator für Ihren PC sein, um diesen Client zu installieren, damit er Ihre Dokumente und E-Mails bezeichnen und schützen kann.

Zusätzlich:

- Der Azure Information Protection-Client erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.

- Wenn Sie Windows 7 SP1 verwenden, erfordert der Azure Information Protection-Client ein bestimmtes Update, KB 2533623. Wenn Ihr PC dieses Update benötigt, es aber nicht installiert ist, wird die Installation abgeschlossen, aber eine Meldung angezeigt, dass der Azure Information Protection-Client dieses Update benötigt. Solange dieses Update nicht installiert ist, können Sie nicht alle Features des Azure Information Protection-Clients nutzen. 

## <a name="to-download-and-install-the-azure-information-protection-client"></a>So laden Sie den Azure Information Protection-Client herunter und installieren ihn    

1.  Wechseln Sie auf der Microsoft-Website zur Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970).

    Diese Seite enthält Links für alle gängigen möglicherweise verwendeten Geräte, sodass Sie bei Bedarf problemlos eine Viewer-Anwendung herunterladen können, um geschützte Dateien zu öffnen. Wenn Sie kein lokaler Administrator für Ihren PC sind, können Sie immer noch die Viewer-App für Windows installieren. Diese Anweisungen installieren allerdings den vollständigen Client, mit dem Sie Dateien mit Bezeichnungen versehen und schützen können. 

2. Suchen Sie den Abschnitt **Azure Information Protection-Client**, und klicken Sie auf das Windows-Symbol. Klicken Sie auf **Herunterladen**, und speichern Sie die Datei **AzInfoProtection.exe**.     

3. Führen Sie die EXE-Datei aus, die heruntergeladen wurde. Wenn Sie aufgefordert werden, den Vorgang fortzusetzen, klicken Sie auf **Ja**.    

4. Auf der Seite **Installieren des Azure Information Protection-Clients**:     
    - Wenn Sie sich nicht mit der Cloud verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer Demorichtlinie, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.    

    - Klicken Sie auf **Ich stimme zu**, wenn Sie die Lizenzbedingungen gelesen haben.    

5. Klicken Sie auf **Ja**, wenn eine Aufforderung zum Fortfahren angezeigt wird, und warten Sie bis die Installation abgeschlossen wurde.    

6. Klicken Sie auf **Schließen**. Bevor Sie den Azure Information Protection-Client verwenden:    

    - Wenn Ihr Computer mit Office 2010 ausgeführt wird, starten Sie den Computer neu, und fahren Sie mit dem letzten Schritt im nächsten Abschnitt fort.    
        
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. Die Installation ist nun abgeschlossen, und Sie können den Client zum Benennen und Schützen Ihrer Dokumente und E-Mails verwenden.    

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Installieren des Azure Information Protection-Clients mit Office 2010    
Nachdem Sie den Azure Information Protection-Client mithilfe der vorherigen Anweisungen installiert haben:    

1. Öffnen Sie Microsoft Word. Wenn Sie zum ersten Mal eine Office 2010-Anwendung ausführen, nachdem Sie den Azure Information Protection-Client installiert haben, sehen Sie das Dialogfeld **Microsoft Azure Information Protection**. Dieses Dialogfeld zeigt Ihnen, dass Administratoranmeldeinformationen erforderlich sind, um den Anmeldeprozess abzuschließen.

2. Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **OK**.

3. Wenn das Dialogfeld **Benutzerzugriffssteuerung** angezeigt wird, klicken Sie auf **Ja**, damit der Azure Information Protection-Client die Registrierung aktualisieren kann.

Die Installation ist nun abgeschlossen, und Sie können Azure Information Protection zum Benennen und Schützen Ihrer Dokumente und E-Mails verwenden.

## <a name="other-instructions"></a>Sonstige Anweisungen    
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

- [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Weitere Informationen finden Sie im [Administratorhandbuch](client-admin-guide.md) unter [Installieren des Azure Information Protection-Clients für Benutzer](client-admin-guide-install.md).
 
  
