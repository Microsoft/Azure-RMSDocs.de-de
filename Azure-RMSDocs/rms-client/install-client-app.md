---
title: Herunterladen und Installieren des Azure Information Protection-Clients | Azure Information Protection
description: "Anweisungen für Benutzer zum Installieren des Azure Information Protection-Clients für Windows, damit Sie Ihre Dokumente und E-Mails klassifizieren und schützen können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/13/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 22af60687ad030e686ba843ced6d450487353a0e
ms.openlocfilehash: 72266181c5334ed7e03b2022df61c4065f1c3ac7


---

# <a name="download-and-install-the-azure-information-protection-client"></a>Herunterladen und Installieren des Azure Information Protection-Clients

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

**[Diese Version des Clients ist eine Vorschau und unterliegt Änderungen.]**

Wenn Ihr Administrator den Azure Information Protection-Client nicht für Sie installiert, können Sie dies selbst übernehmen. Sie müssen ein lokaler Administrator für Ihren PC sein, um diesen Client zu installieren. 

### <a name="office-2010-only"></a>Nur Office 2010

Wenn Sie diese Version von Office verwenden, muss der Azure Information Protection-Client Registrierungsschlüssel festlegen, die Administratorberechtigungen erfordern: 

Verwenden Sie die Anleitungen zum Herunterladen und Installieren des Clients, und verwenden Sie dann die Anleitungen in den folgenden Abschnitten für Office 2010.

## <a name="to-download-and-install-the-azure-information-protection-client"></a>So laden Sie den Azure Information Protection-Client herunter und installieren ihn

1.  Wechseln Sie zur [Microsoft-Downloadwebsite](https://www.microsoft.com/en-us/download/details.aspx?id=53018), und laden Sie die **Vorschauversion** des Azure Information Protection-Clients herunter.

2. Doppelklicken Sie auf die ausführbare Datei, die heruntergeladen wurde. 

3. Auf der Seite **Installieren des Azure Information Protection-Clients**: 
    
    - Wenn Sie sich nicht mit der Cloud verbinden können, jedoch die clientseitige Darstellung von Azure Information Protection testen möchten, wählen Sie die Option zum Installieren einer Demorichtlinie, bei der zu Demonstrationszwecken eine lokale Richtlinie verwendet wird. Wenn Ihr Client sich mit einem Azure Information Protection-Dienst verbindet, wird diese Demorichtlinie durch die Azure Information Protection-Richtlinie Ihrer Organisation ersetzt.
    
    - Klicken Sie auf **Ich stimme zu**, wenn Sie die Lizenzbedingungen gelesen haben.

4. Klicken Sie auf **Ja**, wenn eine Aufforderung zum Fortfahren angezeigt wird, und warten Sie bis die Installation abgeschlossen wurde.

3. Klicken Sie auf **Schließen**. Bevor Sie den Azure Information Protection-Client verwenden:

    - Wenn Ihr Computer mit Office 2010 ausgeführt wird, starten Sie den Computer neu, und fahren Sie mit dem letzten Schritt im nächsten Abschnitt fort.
    
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. Die Installation ist nun abgeschlossen, und Sie können den Client zum Benennen und Schützen Ihrer Dokumente und E-Mails verwenden.

> [!NOTE]
> Wenn Sie Windows 7 SP1 verwenden, erfordert der Azure Information Protection-Client ein bestimmtes Update, [KB 2533623](https://support.microsoft.com/en-us/kb/2533623). Wenn Ihr PC dieses Update benötigt, es aber nicht installiert ist, wird eine Meldung angezeigt, wenn Sie versuchen, den Client zu verwenden, dass dieses Update installiert werden muss, bevor Sie alle Features des Azure Information Protection-Clients verwenden können.

### <a name="installing-the-azure-information-protection-client-with-office-2010"></a>Installieren des Azure Information Protection-Clients mit Office 2010

Nachdem Sie den Azure Information Protection-Client mithilfe der vorherigen Anweisungen installiert haben:

1. Öffnen Sie Microsoft Word. Wenn Sie zum ersten Mal eine Office 2010-Anwendung ausführen, nachdem Sie den Azure Information Protection-Client installiert haben, sehen Sie das Dialogfeld **Microsoft Azure Information Protection**. Dieses Dialogfeld zeigt Ihnen, dass Administratoranmeldeinformationen erforderlich sind, um den Anmeldeprozess abzuschließen.

2. Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **OK**.

2. Wenn das Dialogfeld **Benutzerzugriffssteuerung** angezeigt wird, klicken Sie auf **Ja**, damit der Azure Information Protection-Client die Registrierung aktualisieren kann.

Die Installation ist nun abgeschlossen, und Sie können Azure Information Protection zum Benennen und Schützen Ihrer Dokumente und E-Mails verwenden.

## <a name="other-instructions"></a>Sonstige Anweisungen
Anweisungen zur Vorgehensweise finden Sie in den folgenden Abschnitten des Azure Information Protection-Benutzerhandbuchs:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren
[Installieren des Azure Information Protection-Clients](info-protect-client.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO2-->


