---
title: "Schnellstart-Tutorial für Azure Information Protection | Azure Rights Management"
description: "Ein Einführungstutorial, in dem beschrieben wird, wie Sie Microsoft Azure Information Protection in nur vier Schritten und weniger als 15 Minuten für Ihre Organisation testen können."
author: cabailey
manager: mbaldwin
ms.date: 07/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1260b9e5-dba1-41de-84fd-609076587842
translationtype: Human Translation
ms.sourcegitcommit: cac95dec84f99d2e6caa3458dc8284defe2324bc
ms.openlocfilehash: 7dc988365c1fa86827d1a7edc33c0a2eb6180f0e


---

# Schnellstart-Tutorial für Azure Information Protection 

*Gilt für: Azure Information Protection (Preview)*

Verwenden Sie dieses Tutorial, um die Vorschau von Azure Information Protection ohne großen Zeitaufwand für Ihr Unternehmen zu testen – mit nur vier Schritten, die weniger als 15 Minuten in Anspruch nehmen. Optional aktivieren Sie den Azure Rights Management-Dienst, überprüfen und ändern die Standardrichtlinie von Azure Information Protection, installieren den Azure Information Protection-Client und verwenden anschließend ein Word-Dokument, um die Klassifizierung, Bezeichnung und den Schutz in Aktion anzuzeigen.

Dieses Tutorial richtet sich an IT-Administratoren und Berater, die Azure Information Protection als Lösung zum Schutz von Unternehmensinformationen für eine Organisation evaluieren. In einer Produktionsumgebung würden die Anweisungen zum Aktivieren des Dienst, zur Konfiguration der Information Protection-Richtlinie und zur Installation des Clients für Benutzer von einem Administrator ausgeführt werden. Die Anweisungen zum Bezeichnen des Dokuments würden vom Endbenutzer ausgeführt werden. Beide Vorgehensweisen sind Teil dieses Tutorials und veranschaulichen das End-to-End-Szenario für die Klassifizierung, Bezeichnung und den Schutz der Daten Ihrer Organisation. 

Falls Sie Probleme beim Abschließen dieses Tutorials oder beim Verwenden dieses Vorschaurelease von Azure Information Protection haben oder wissen möchten, was andere darüber sagen, besuchen Sie die [Yammer-Website von Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all).

## Voraussetzungen 
Voraussetzungen für dieses Tutorial:

- Alle Abonnements, die Azure Rights Management umfasst, die Ihnen Zugriff auf das Vorschaurelease von Azure Information Protection gewähren. Azure Information Protection ist in allen Regionen verfügbar, die Azure Rights Management unterstützen. Weitere Informationen zu den verfügbaren Abonnements und Links zu kostenlosen Testversionen finden Sie unter [Azure RMS-Anforderungen: Cloudabonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).

- Sie müssen über ein Azure-Abonnement verfügen, um die Azure Information Protection-Richtlinien im Azure-Portal zu konfigurieren. Falls Sie noch kein Azure-Abonnement für Ihre Organisation besitzen, können Sie sich für eine kostenlose Testversion anmelden: Folgen Sie den Anweisungen auf der [Seite für die ersten Schritten mit Azure](https://account.windowsazure.com/organization).

  > [!TIP] 
  > Wenn Sie eines oder beide dieser Abonnements erwerben müssen, sollten Sie dies rechtzeitig erledigen, da dies einige Zeit in Anspruch nehmen kann.

- Ein globales Administratorkonto zur Anmeldung beim Office 365 Admin Center oder beim klassischen Azure-Portal, wenn Sie den Rights Management-Dienst aktivieren müssen. Dieses Konto muss auch über eine E-Mail-Adresse und einen funktionierenden E-Mail-Dienst (z. B. Exchange Online oder Exchange Server) verfügen.

- Ein Computer unter Windows (mindestens Windows 7 mit Service Pack 1), auf dem entweder Office 2016, Office 2013 mit Service Pack 1 oder Office 2010 installiert ist. 

- Falls Sie Active Directory Rights Management Services (AD RMS) in Ihrer Organisation bereitgestellt haben, muss der Computer ein Arbeitsgruppencomputer sein, auf dem zuvor noch nicht AD RMS verwendet wurde. Dies ist erforderlich, wenn Sie Dokumente schützen möchten, und es wird sichergestellt, dass der Computer nur Vorlagen von Azure Rights Management herunterlädt. Eine gleichzeitige Verbindung zu AD RMS und Azure RMS wird nicht unterstützt. Weitere Informationen zur Migration finden Sie unter [Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).   

Los geht’s!

>[!div class="step-by-step"]
[&#187; Schritt 1](infoprotect-tutorial-step1.md)





<!--HONumber=Jul16_HO3-->


