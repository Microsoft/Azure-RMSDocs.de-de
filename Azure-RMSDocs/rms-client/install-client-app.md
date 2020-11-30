---
title: Herunterladen und Installieren des Azure Information Protection-Clients
description: Anweisungen für Benutzer zum Installieren des Azure Information Protection-Clients für Windows, damit Sie Ihre Dokumente und E-Mails klassifizieren und schützen können.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/17/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.subservice: v1client
ms.reviewer: eymanor
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 26e9f85a4e5d171232dc8d30f4502557808ac538
ms.sourcegitcommit: d31cb53de64bafa2097e682550645cadc612ec3e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "96316618"
---
# <a name="user-guide-download-and-install-the-azure-information-protection-client"></a>Benutzerhandbuch: Herunterladen und Installieren des Azure Information Protection-Clients

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


Wenn Ihr Administrator den Azure Information Protection-Client nicht für Sie installiert, können Sie dies selbst übernehmen. Sie müssen ein lokaler Administrator für Ihren PC sein, um diesen Client zu installieren, damit er Ihre Dokumente und E-Mails bezeichnen und schützen kann.

Zusätzlich:

- Der Azure Information Protection-Client erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.


## <a name="to-download-and-install-the-azure-information-protection-client"></a>So laden Sie den Azure Information Protection-Client herunter und installieren ihn

Der Azure Information Protection klassische Client wird im März 2021 eingestellt. 

Zum Bereitstellen des klassischen AIP-Clients eröffnen Sie ein Supportticket, um Zugriff auf den Download zu erhalten.

1. Führen Sie die **AzInfoProtection.exe** Datei aus, um die Installation zu starten. Wenn Sie zum Fortfahren aufgefordert werden, klicken Sie auf **Ja**.    

1. Auf der Seite **Installieren des Azure Information Protection-Clients**:     
    - Wenn Sie sich nicht mit der Cloud verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer Demorichtlinie, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.    

    - Klicken Sie auf **Ich stimme zu**, wenn Sie die Lizenzbedingungen gelesen haben.    

1. Klicken Sie auf **Ja**, wenn eine Aufforderung zum Fortfahren angezeigt wird, und warten Sie bis die Installation abgeschlossen wurde.    

1. Klicken Sie auf **Schließen**. Bevor Sie den Azure Information Protection-Client verwenden:    

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
 
  
