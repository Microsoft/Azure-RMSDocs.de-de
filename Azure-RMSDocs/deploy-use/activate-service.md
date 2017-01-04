---
title: Aktivieren von Azure Rights Management | Azure Information Protection
description: "Sie müssen den Azure Rights Management-Dienst aktivieren, damit Ihre Organisation damit beginnen kann, Dokumente und E-Mails mithilfe von Anwendungen und Diensten zu schützen, die diese Lösung für den Informationsschutz unterstützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/09/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ced42d0856b992d3539575d64f5a49706f1768b3
ms.openlocfilehash: 80fd7a7ce1ac6b7a8b2867729dd3e09e9b106d9b


---

# <a name="activating-azure-rights-management"></a>Aktivieren von Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Wenn der Azure Rights Management-Dienst für Azure Information Protection aktiviert wurde, kann Ihre Organisation damit beginnen, wichtige Daten mithilfe von Anwendungen und Diensten zu schützen, die diese Lösung für den Informationsschutz unterstützen. Administratoren können außerdem geschützte Dateien und E-Mails, die Ihrer Organisation gehören, verwalten und überwachen. Dieser Dienst muss aktiviert werden, bevor Sie beginnen können, IRM-Features (Information Rights Management) in Office, SharePoint und Exchange zu verwenden und sensible oder vertrauliche Dateien zu schützen.

Wenn Sie weitere Informationen zum Azure Rights Management-Dienst benötigen, bevor Sie ihn aktivieren (z.B. welche geschäftlichen Probleme gelöst werden, einige typische Anwendungsfälle sowie Informationen zur Funktionsweise), helfen Ihnen die Informationen unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md) weiter.

> [!IMPORTANT]
> Bevor Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktivieren, sollten Sie sicherstellen, dass Ihre Organisation über einen Diensttarif verfügt, der Azure Rights Management-Datenschutz umfasst. Ist dies nicht der Fall, können Sie Azure Rights Management nicht aktivieren.
>
> Die benötigen entweder einen [Azure Information Protection Premium-Plan](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-pricing) oder einen [Office 365-Plan, der Rights Management umfasst](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Wenn der Azure Rights Management-Dienst aktiviert wurde, können alle Benutzer in Ihrer Organisation Information Protection (Informationsschutz) auf die eigenen Dateien anwenden und Dateien öffnen (nutzen), die durch den Azure Rights Management-Dienst geschützt wurden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

Wählen Sie aus, ob Sie das Office 365 Admin Center (Vorschau oder klassisch) oder das klassische Azure-Verwaltungsportal verwenden möchten, um eine Anleitung zum Aktivieren des Rights Management-Diensts über Ihr Verwaltungsportal zu erhalten:


- [Office 365 Admin Center – Vorschau](activate-office365-preview.md)
- [Office 365 Admin Center – Klassisch](activate-office365-classic.md)
- [Klassisches Azure-Portal](activate-azure-classic.md)

Alternativ können Sie zum Aktivieren von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] PowerShell verwenden:

1. Installieren Sie das Verwaltungstool für Azure Rights Management, das wiederum das Azure Rights Management-Verwaltungsmodul installiert. Anweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2. Führen Sie in einer PowerShell-Sitzung [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) aus, und geben Sie, wenn Sie dazu aufgefordert werden, die Details des globalen Administratorkontos für Ihren Azure Information Protection-Mandanten an.

3. Führen Sie [Enable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629412.aspx) aus, um den Azure Rights Management-Dienst zu aktivieren.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung
Sollen nicht alle Benutzer sofort die Möglichkeit haben, Dateien mithilfe von Azure Rights Management zu schützen, können Sie mit dem PowerShell-Befehl [Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) Benutzereinbindungsrichtlinien (Onboardingsteuerungsrichtlinien) konfigurieren. Sie können diesen Befehl ausführen, bevor oder nachdem Sie den Azure Rights Management-Dienst aktivieren.

> [!IMPORTANT]
> Damit Sie diesen Befehl verwenden können, benötigen Sie mindestens Version **2.1.0.0** des [ PowerShell-Moduls für Azure Rights Management](http://go.microsoft.com/fwlink/?LinkId=257721).
>
> Führen Sie den folgenden Befehl aus, um die Version zu überprüfen, die installiert ist: **(Get-Module aadrm –ListAvailable).Version**

Wenn Sie beispielsweise möchten, dass zunächst nur Administratoren der Gruppe "IT-Abteilung" (die die Objekt-ID "fbb99ded-32a0-45f1-b038-38b519009503" hat) in der Lage sein sollen, Inhalte zu Testzwecken zu schützen, verwenden Sie den folgenden Befehl:

```
Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503
```
Beachten Sie, dass Sie für diese Konfigurationsoption eine Gruppe angeben müssen. Sie können keine einzelnen Benutzer angeben. Verwenden Sie Azure AD Powershell, um die Objekt-ID für die Gruppe zu erhalten – z.b. den Befehl [Get-MsolGroup](https://msdn.microsoft.com/library/azure/dn194130\(v=azure.98\).aspx), für [Version 1.0](https://msdn.microsoft.com/library/azure/jj151815\(v=azure.98\).aspx) des Moduls.

Oder Sie möchten sicherstellen, dass nur Benutzer, die ordnungsgemäß für die Verwendung von Azure Information Protection lizenziert sind, Inhalte schützen können:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true
```

Weitere Informationen zu diesem Cmdlet und zusätzliche Beispiele finden Sie auf der Hilfeseite [Set-AadrmOnboardingControlPolicy](https://msdn.microsoft.com/library/dn857521.aspx).

Wenn Sie diese Onboarding-Steuerelemente verwenden, können alle Benutzer in der Organisation immer geschützte Inhalte nutzen, die durch Ihre Teilmenge von Benutzern geschützt wurde, können aber Informationsschutz aus Clientanwendungen nicht selbst anwenden. Beispielsweise sehen sie nicht die Standardvorlagen in ihren Office-Clients, die automatisch veröffentlicht werden, wenn der Azure Rights Management-Dienst aktiviert ist, oder benutzerdefinierte Vorlagen, die Sie ggf. konfiguriert haben.  Serverseitige Anwendung wie z.B. Exchange können eigene Steuerelemente pro Benutzer für die Rights Management-Integration implementieren, um das gleiche Ergebnis zu erzielen.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] jetzt für Ihre Organisation aktiviert haben, verwenden Sie die [Roadmap für die Bereitstellung von Azure Information Protection](../plan-design/deployment-roadmap.md), um herauszufinden, ob Sie vor dem Rollout von Azure Information Protection für Benutzer und Administratoren ggf. weitere Konfigurationsschritte ausführen müssen. 

Angenommen, Sie möchten [benutzerdefinierte Vorlagen](configure-custom-templates.md) verwenden, um es den Benutzern zu erleichtern, Informationsschutz auf Dateien anzuwenden, Ihre lokalen Server durch Installation des [Rights Management-Connectors](deploy-rms-connector.md) für die Verwendung von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verbinden und die [Rights Management-Freigabeanwendung](../rms-client/sharing-app-windows.md) bereitzustellen, die den Schutz aller Dateitypen auf allen Geräten unterstützt. 

Office-Dienste (z.B. Exchange Online und SharePoint Online) erfordern zusätzliche Konfigurationsschritte, bevor Sie deren IRM-Features (Information Rights Management) verwenden können. Informationen dazu, wie Ihre Anwendungen mit dem Rights Management-Dienst funktionieren, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](../understand-explore/applications-support.md).

## <a name="comments"></a>Kommentare

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Dec16_HO2-->


