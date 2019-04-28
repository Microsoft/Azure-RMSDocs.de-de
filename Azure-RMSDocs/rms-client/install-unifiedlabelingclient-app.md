---
title: Herunterladen Sie und installieren Sie den Azure Information Protection unified bezeichnungs-client
description: Anweisungen für Benutzer, um die einheitliche Azure Information Protection-Bezeichnung-Client für Windows, zu installieren, damit Sie klassifizieren und Ihrer Dokumente und e-Mails schützen können.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.openlocfilehash: 563ddb6d91ef59ee96cf00dba973b7e612bbc780
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60180952"
---
# <a name="user-guide-download-and-install-the-azure-information-protection-unified-labeling-client"></a>Leitfaden: Herunterladen Sie und installieren Sie den Azure Information Protection unified bezeichnungs-client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Wenn Ihr Administrator die einheitlichen Azure Information Protection-Bezeichnung-Client für Sie nicht installiert ist, können Sie dies selbst übernehmen. Sie müssen ein lokaler Administrator für Ihren PC sein, um diesen Client zu installieren, damit er Ihre Dokumente und E-Mails bezeichnen und schützen kann.

Zusätzlich:

- Der Azure Information Protection-Client für einheitliche Bezeichnungen erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.

- Wenn Sie Windows 7 SP1 verwenden, erfordert der Azure Information Protection-Client für einheitliche Bezeichnungen das Update KB 2533623. Wenn Ihr PC dieses Update benötigt, es aber nicht installiert ist, wird die Installation zwar abgeschlossen, aber die Meldung angezeigt, dass der Azure Information Protection-Client für einheitliche Bezeichnungen dieses Update benötigt. Solange dieses Update nicht installiert ist, können Sie nicht alle Features des Azure Information Protection-Clients für einheitliche Bezeichnungen nutzen. 

## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>So laden Sie den Azure Information Protection-Client für einheitliche Bezeichnungen herunter und installieren ihn

Vor der Installation des einheitlichen Bezeichnung Azure Information Protection-Clients, vergewissern Sie sich mit Ihrem Administrator oder den Helpdesk, dass Sie Office 365-vertraulichkeitsbezeichnungen verwenden.

1. Herunterladen **AzInfoProtection_UL.exe** aus der [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=53018).

2. Führen Sie die ausführbare Datei, die heruntergeladen wurde, und wenn Sie aufgefordert werden, um den Vorgang fortzusetzen, klicken Sie auf **Ja**.

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
Weitere Anweisungen zur Vorgehensweise finden die Azure Information Protection unified bezeichnungs Client – Benutzerhandbuch:

- [Was möchten Sie tun?](clientv2-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Finden Sie unter [Installieren des einheitlichen Azure Information Protection-Bezeichnung-Clients für Benutzer](clientv2-admin-guide-install.md) aus der [Administratorhandbuch](clientv2-admin-guide.md).
