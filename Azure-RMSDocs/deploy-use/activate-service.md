---
title: Aktivieren von Azure Rights Management | Azure RMS
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/16/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: bf5e3561ef24d8f44e791ff7bdc8450a73f79705
ms.openlocfilehash: d66e4e6bca253bc2bf9d12ba22ed0202cba2edaf


---

# Aktivieren von Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*

Wenn Sie [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) aktivieren, kann Ihre Organisation damit beginnen, wichtige Daten mithilfe von Anwendungen und Diensten zu schützen, die diese Informationschutzlösung unterstützen. Administratoren können außerdem geschützte Dateien und E-Mails, die Ihrer Organisation gehören, verwalten und überwachen. Sie müssen [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktivieren, bevor Sie beginnen können, IRM-Features (Information Rights Management) in Office, SharePoint und Exchange zu verwenden und sensible oder vertrauliche Dateien zu schützen.

Wenn Sie weitere Informationen zu Azure Rights Management benötigen, bevor Sie den Dienst aktivieren (z.B. welche geschäftlichen Probleme gelöst werden, einige typische Anwendungsfälle sowie Informationen zur Funktionsweise), helfen Ihnen die Informationen unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md) weiter.

> [!IMPORTANT]
> Bevor Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktivieren, sollten Sie sicherstellen, dass Ihre Organisation einen Serviceplan hat, der [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Dienste beinhaltet. Ist dies nicht der Fall, können Sie Azure RMS nicht aktivieren.
>
> Weitere Informationen finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).

Nachdem Sie Azure RMS aktiviert haben, können alle Benutzer in Ihrer Organisation Information Protection (Informationsschutz) auf die eigenen Dateien anwenden und Dateien öffnen (nutzen), die über Azure RMS geschützt wurden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

Wählen Sie aus, ob Sie das Office 365 Admin Center (Vorschau oder klassisch) oder das klassische Azure-Verwaltungsportal verwenden möchten, um eine Anleitung zum Aktivieren von Rights Management über Ihr Verwaltungsportal zu erhalten:


- [Office 365 Admin Center – Vorschau](activate-office365-preview.md)
- [Office 365 Admin Center – Klassisch](activate-office365-classic.md)
- [Klassisches Azure-Portal](activate-azure-classic.md)

Alternativ können Sie zum Aktivieren von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] Windows PowerShell verwenden:

1. Installieren Sie das Verwaltungstool für Azure Rights Management, das wiederum das Azure Rights Management-Verwaltungsmodul installiert. Anweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2. Führen Sie in einer Windows PowerShell-Sitzung [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) aus, und geben Sie, wenn Sie dazu aufgefordert werden, die Details des globalen Administratorkontos für Ihren Azure RMS-Mandanten an.

3. Führen Sie [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx) aus, wodurch der Azure RMS-Dienst aktiviert wird.

## Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung
Sollen nicht alle Benutzer sofort die Möglichkeit haben, Dateien mithilfe von Azure RMS zu schützen, können Sie mit dem Windows PowerShell-Befehl [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Benutzereinbindungsrichtlinien (Onboardingsteuerungsrichtlinien) konfigurieren. Sie können diesen Befehl ausführen, bevor oder nachdem Sie Azure RMS aktivieren.

> [!IMPORTANT]
> Damit Sie diesen Befehl verwenden können, benötigen Sie mindestens Version **2.1.0.0** des [Azure RMS Windows PowerShell-Moduls](http://go.microsoft.com/fwlink/?LinkId=257721).
>
> Führen Sie den folgenden Befehl aus, um die Version zu überprüfen, die installiert ist: **(Get-Module aadrm –ListAvailable).Version**

Wenn Sie beispielsweise möchten, dass zunächst nur Administratoren der Gruppe "IT-Abteilung" (die die Objekt-ID "fbb99ded-32a0-45f1-b038-38b519009503" hat) in der Lage sein sollen, Inhalte zu Testzwecken zu schützen, verwenden Sie den folgenden Befehl:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Beachten Sie, dass Sie für diese Konfigurationsoption eine Gruppe angeben müssen. Sie können keine einzelnen Benutzer angeben.

Oder Sie möchten sicherstellen, dass nur Benutzer, die ordnungsgemäß für die Verwendung von Azure RMS lizenziert sind, Inhalte schützen können:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```
Wenn Sie diese Onboarding-Steuerelemente verwenden, können alle Benutzer in der Organisation immer geschützte Inhalte nutzen, die durch Ihre Teilmenge von Benutzern geschützt wurde, können aber Informationsschutz aus Clientanwendungen nicht selbst anwenden. Beispielsweise sehen sie nicht die Standardvorlagen in ihren Office-Clients, die automatisch veröffentlicht werden, wenn Azure RMS aktiviert ist, oder benutzerdefinierte Vorlagen, die Sie ggf. konfiguriert haben.  Serverseitige Anwendung wie z. B. Exchange können eigene Steuerelemente pro Benutzer für die RMS-Integration implementieren, um das gleiche Ergebnis zu erzielen.


## Nächste Schritte
Nachdem Sie jetzt [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] für Ihre Organisation aktiviert haben, verwenden Sie die [Roadmap für die Bereitstellung von Azure Rights Management](../plan-design/deployment-roadmap.md), um herauszufinden, ob Sie vor dem Rollout von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] für Benutzer und Administratoren ggf. weitere Konfigurationsschritte ausführen müssen. 

Angenommen, Sie möchten [benutzerdefinierte Vorlagen](configure-custom-templates.md) verwenden, um es den Benutzern zu erleichtern, Informationsschutz auf Dateien anzuwenden, Ihre lokalen Server durch Installation des [RMS-Verbindungsdiensts](deploy-rms-connector.md) für die Verwendung von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verbinden und die [Rights Management-Freigabeanwendung](../rms-client/sharing-app-windows.md) bereitzustellen, die den Schutz aller Dateitypen auf allen Geräten unterstützt. 

Office-Dienste (z.B. Exchange Online und SharePoint Online) erfordern zusätzliche Konfigurationsschritte, bevor Sie deren IRM-Features (Information Rights Management) verwenden können. Informationen dazu, wie Ihre Anwendungen mit [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] funktionieren, finden Sie unter [Unterstützung von Azure Rights Management durch Anwendungen](../understand-explore/applications-support.md).




<!--HONumber=Jun16_HO4-->


