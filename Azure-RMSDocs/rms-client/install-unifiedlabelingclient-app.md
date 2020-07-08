---
title: Herunterladen & installieren des Azure Information Protection Unified Bezeichnung-Clients
description: Anweisungen für Benutzer zum Installieren des Azure Information Protection Unified Bezeichnung-Clients für Windows, damit Sie Ihre Dokumente und e-Mails klassifizieren und schützen können.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 05/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 586122e55c8eddc2e14864bcffbe9f6ef99e17e8
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86046435"
---
# <a name="user-guide-download-and-install-the-azure-information-protection-unified-labeling-client"></a>Benutzerhandbuch: herunterladen und Installieren des Azure Information Protection Unified Bezeichnung-Client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Wenn Ihr Administrator den Azure Information Protection Unified-Bezeichnung-Client nicht für Sie installiert, können Sie dies selbst tun. Sie müssen ein lokaler Administrator für Ihren PC sein, um diesen Client zu installieren, damit er Ihre Dokumente und E-Mails bezeichnen und schützen kann.

Außerdem:

- Der Azure Information Protection-Client für einheitliche Bezeichnungen erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.


## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>So laden Sie den Azure Information Protection-Client für einheitliche Bezeichnungen herunter und installieren ihn

Vergewissern Sie sich vor der Installation des Azure Information Protection Unified Label-Clients, dass der Administrator oder das Helpdesk die [Vertraulichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) zum klassifizieren und schützen von Dokumenten und e-Mails verwenden.

1. Laden Sie **AzInfoProtection_UL.exe** aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunter.

2. Führen Sie die heruntergeladene ausführbare Datei aus, und klicken Sie auf **Ja**, wenn Sie aufgefordert werden, den Vorgang fortzusetzen.

3. Klicken Sie auf der Seite **Azure Information Protection-Client installieren** auf **Ich stimme zu**, wenn Sie die Lizenzbedingungen gelesen haben.

4. Klicken Sie auf **Ja**, wenn eine Aufforderung zum Fortfahren angezeigt wird, und warten Sie bis die Installation abgeschlossen wurde.

6. Klicken Sie auf **Schließen**. Gehen Sie wie folgt vor, bevor Sie den Azure Information Protection-Client für einheitliche Bezeichnungen verwenden:

    - Wenn Ihr Computer mit Office 2010 ausgeführt wird, starten Sie den Computer neu, und fahren Sie mit dem letzten Schritt im nächsten Abschnitt fort.    
        
    - Für andere Versionen von Office starten Sie alle Office-Anwendungen und alle Instanzen des Datei-Explorers neu. Die Installation ist nun abgeschlossen, und Sie können den Client zum Benennen und Schützen Ihrer Dokumente und E-Mails verwenden.

### <a name="installing-the-azure-information-protection-unified-labeling-client-with-office-2010"></a>Installieren des Azure Information Protection-Clients für einheitliche Bezeichnungen mit Office 2010

Gehen Sie wie folgt vor, nachdem Sie den Azure Information Protection-Client für einheitliche Bezeichnungen mithilfe der vorherigen Anweisungen installiert haben:

1. Öffnen Sie Microsoft Word. Wenn Sie zum ersten Mal eine Office 2010-Anwendung ausführen, nachdem Sie den Azure Information Protection-Client installiert haben, sehen Sie das Dialogfeld **Microsoft Azure Information Protection**. Dieses Dialogfeld zeigt Ihnen, dass Administratoranmeldeinformationen erforderlich sind, um den Anmeldeprozess abzuschließen.

2. Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **OK**.

3. Wenn das Dialogfeld **Benutzerzugriffssteuerung** angezeigt wird, klicken Sie auf **Ja**, damit der Azure Information Protection-Client die Registrierung aktualisieren kann.

Die Installation ist nun abgeschlossen, und Sie können den Azure Information Protection-Client für einheitliche Bezeichnungen zum Benennen und Schützen Ihrer Dokumente und E-Mails verwenden.

## <a name="other-instructions"></a>Sonstige Anweisungen    
Weitere Anleitungen finden Sie im Benutzerhandbuch für das Azure Information Protection Unified Bezeichnung-Client:

- [Wie möchten Sie vorgehen?](clientv2-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Weitere Informationen finden Sie im [Administrator Handbuch](clientv2-admin-guide.md)unter [Installieren des Azure Information Protection Unified Bezeichnung-Clients für Benutzer](clientv2-admin-guide-install.md) .
