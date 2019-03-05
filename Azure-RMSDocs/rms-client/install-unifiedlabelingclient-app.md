---
title: Herunterladen und Installieren des Azure Information Protection-Clients für einheitliche Bezeichnungen (Vorschau)
description: Anweisungen für Benutzer zum Installieren der Vorschauversion des Azure Information Protection-Clients für einheitliche Bezeichnungen für Windows, damit diese ihre Dokumente und E-Mails klassifizieren und schützen können.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/26/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 2bf09690-9dba-43b7-9e0a-0110915d4081
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: cbe97fc619de9b7bda73ebb419bfc254f237f372
ms.sourcegitcommit: 55782e58508051f0ecf460e8b126f70ab9b9ceec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/25/2019
ms.locfileid: "56756129"
---
# <a name="download-and-install-the-azure-information-protection-unified-labeling-client-preview"></a>Herunterladen und Installieren des Azure Information Protection-Clients für einheitliche Bezeichnungen (Vorschau)

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

> [!NOTE]
> Der Client befindet sich noch in der Vorschauphase. Es können also noch Änderungen vorgenommen werden. Er verwendet einen Speicher für einheitliche Bezeichnungen und lädt Richtlinien für Vertraulichkeitsbezeichnungen aus dem Office 365 Security & Compliance Center herunter. Damit diese Bezeichnungen verwendet werden können, müssen sie zunächst über das Security & Compliance Center veröffentlicht werden. [Weitere Informationen](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492)

Sie müssen ein lokaler Administrator für Ihren PC sein, um diesen Client in der Vorschau zu installieren, damit er Ihren Dokumenten und E-Mails Bezeichnungen zuordnen und diese schützen kann.

Zusätzlich:

- Der Azure Information Protection-Client für einheitliche Bezeichnungen erfordert Microsoft .NET Framework 4.6.2 oder höher. Wenn diese Version fehlt, versucht das Installationsprogramm diese erforderliche Komponente herunterzuladen und zu installieren. Wenn diese Voraussetzung im Rahmen der Clientinstallation installiert wird, muss der Computer neu gestartet werden.

- Wenn Sie Windows 7 SP1 verwenden, erfordert der Azure Information Protection-Client für einheitliche Bezeichnungen das Update KB 2533623. Wenn Ihr PC dieses Update benötigt, es aber nicht installiert ist, wird die Installation zwar abgeschlossen, aber die Meldung angezeigt, dass der Azure Information Protection-Client für einheitliche Bezeichnungen dieses Update benötigt. Solange dieses Update nicht installiert ist, können Sie nicht alle Features des Azure Information Protection-Clients für einheitliche Bezeichnungen nutzen. 

## <a name="to-download-and-install-the-azure-information-protection-unified-labeling-client"></a>So laden Sie den Azure Information Protection-Client für einheitliche Bezeichnungen herunter und installieren ihn

Bevor Sie den Azure Information Protection-Client für einheitliche Bezeichnungen installieren, sollten Sie überprüfen, ob Sie im Office 365 Security & Compliance Center über Vertraulichkeitsbezeichnungen verfügen, die für Benutzer veröffentlicht werden. 

Wenn Sie über Bezeichnungen verfügen, die derzeit über das Azure-Portal für Azure Information Protection veröffentlicht werden, können Sie diese Bezeichnungen in das Security & Compliance Center [migrieren](../configure-policy-migrate-labels.md).

1. Laden Sie den Client in der Vorschauversion über das [Microsoft Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=57440) herunter.

2. Führen Sie die heruntergeladene ausführbare Datei **AzInfoProtection_For_Unified_Labeling.exe** aus. Wenn Sie aufgefordert werden, den Vorgang fortzusetzen, klicken Sie auf **Ja**.    

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

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zu dem Speicher für einheitliche Bezeichnungen zu erhalten, die das Security & Compliance-Center von Office 365 jetzt verwendet, lesen Sie folgenden Blogbeitrag: [Bekanntgabe der Verfügbarkeit der Verwaltung einheitlicher Bezeichnungen im Security & Compliance Center](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Announcing-the-availability-of-unified-labeling-management-in/ba-p/262492).
