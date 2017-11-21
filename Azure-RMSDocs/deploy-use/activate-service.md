---
title: "Aktivieren von Azure Rights Management – AIP"
description: "Sie müssen den Azure Rights Management-Dienst aktivieren, damit Ihre Organisation damit beginnen kann, Dokumente und E-Mails mithilfe von Anwendungen und Diensten zu schützen, die diese Lösung für den Informationsschutz unterstützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 75c0bf83c84cb8b5d2116b05dbf2def790562b4e
ms.sourcegitcommit: fd3932ab19a00229b56efc3e301abaf9cff3f70b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/17/2017
---
# <a name="activating-azure-rights-management"></a>Aktivieren von Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

> [!NOTE]
> Diese Konfigurationsinformationen richten sich an Administratoren, die für einen Dienst zuständig sind, der für alle Benutzer in einer Organisation gilt. Wenn Sie Hilfe und Informationen zur Verwendung der Rights Management-Funktionen für eine bestimmte Anwendung oder zum Öffnen einer Datei oder E-Mail suchen, die mit Rechten geschützt ist, verwenden Sie die zur Anwendung gehörende Hilfe und Anleitungen.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM**ein. Informationen zum Azure Information Protection-Client für Windows finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](../rms-client/client-user-guide.md).
>
> Technischen Support und Antworten auf Fragen zum Dienst finden Sie unter [Support options and community resources (Supportoptionen und Communityressourcen)](../get-started/information-support.md#support-options-and-community-resources).

Wenn der Azure Rights Management-Dienst für Azure Information Protection für Ihren Mandanten aktiviert wurde, kann Ihre Organisation von nun an wichtige Daten mithilfe von Anwendungen und Diensten schützen, die diese Lösung zum Schutz von Informationen unterstützen. Administratoren können außerdem geschützte Dateien und E-Mails, die Ihrer Organisation gehören, verwalten und überwachen. Dieser Dienst muss aktiviert werden, bevor Sie beginnen können, IRM-Features (Information Rights Management) in Office, SharePoint und Exchange zu verwenden und sensible oder vertrauliche Dateien zu schützen.

Wenn Sie weitere Informationen zum Azure Rights Management-Dienst benötigen, bevor Sie ihn aktivieren (z.B. welche geschäftlichen Probleme gelöst werden, einige typische Anwendungsfälle sowie Informationen zur Funktionsweise), helfen Ihnen die Informationen unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md) weiter.

> [!IMPORTANT]
> Aktivieren Sie den Azure Rights Management-Dienst nicht, wenn Sie Active Directory Rights Management Services (AD RMS) für Ihre Organisation bereitgestellt haben. [Weitere Informationen](prepare-environment-adrms.md)

Bevor Sie [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] aktivieren, sollten Sie sicherstellen, dass Ihre Organisation über einen Diensttarif verfügt, der Azure Rights Management-Datenschutz umfasst. Ist dies nicht der Fall, können Sie Azure Rights Management nicht aktivieren. Sie müssen eine der folgenden Komponenten besitzen:

- Einen [Azure Information Protection-Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- Einen [Office 365-Plan, der Rights Management enthält](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Wenn der Azure Rights Management-Dienst aktiviert wurde, können alle Benutzer in Ihrer Organisation Information Protection (Informationsschutz) auf die eigenen Dateien anwenden und Dateien öffnen (nutzen), die durch den Azure Rights Management-Dienst geschützt wurden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

Wählen Sie aus, ob Sie Office 365 Admin Center oder das Azure-Portal verwenden möchten, um Anweisungen zum Aktivieren des Rights Management-Diensts über Ihr Verwaltungsportal zu erhalten:

- [**Office 365 Admin Center**](activate-office365.md): erfordert ein globales Administratorkonto

- [**Azure-Portal**](activate-azure.md): erfordert ein globales Administratorkonto oder ein [Sicherheitsadministratorkonto](https://docs.microsoft.com/azure/active-directory/active-directory-assign-admin-roles)

Alternativ können Sie zum Aktivieren von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] PowerShell verwenden:

1. Installieren Sie das Verwaltungstool für Azure Rights Management, das wiederum das Azure Rights Management-Verwaltungsmodul installiert. Anweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

2. Führen Sie in einer PowerShell-Sitzung [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) aus, und geben Sie, wenn Sie dazu aufgefordert werden, die Details des globalen Administratorkontos für Ihren Azure Information Protection-Mandanten an.

3. Führen Sie [Enable-Aadrm](/powershell/module/aadrm/enable-aadrm) aus, um den Azure Rights Management-Dienst zu aktivieren.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung
Sollen nicht alle Benutzer sofort die Möglichkeit haben, Dateien mithilfe von Azure Rights Management zu schützen, können Sie mit dem PowerShell-Befehl [Set-AadrmOnboardingControlPolicy](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) Benutzereinbindungsrichtlinien (Onboardingsteuerungsrichtlinien) konfigurieren. Sie können diesen Befehl ausführen, bevor oder nachdem Sie den Azure Rights Management-Dienst aktivieren.

> [!IMPORTANT]
> Damit Sie diesen Befehl verwenden können, benötigen Sie mindestens Version **2.1.0.0** des [ PowerShell-Moduls für Azure Rights Management](https://go.microsoft.com/fwlink/?LinkId=257721).
>
> Führen Sie den folgenden Befehl aus, um die Version zu überprüfen, die installiert ist: **(Get-Module aadrm –ListAvailable).Version**

Wenn Sie beispielsweise möchten, dass zunächst nur Administratoren der Gruppe "IT-Abteilung" (die die Objekt-ID "fbb99ded-32a0-45f1-b038-38b519009503" hat) in der Lage sein sollen, Inhalte zu Testzwecken zu schützen, verwenden Sie den folgenden Befehl:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fbb99ded-32a0-45f1-b038-38b519009503"
```

Beachten Sie, dass Sie für diese Konfigurationsoption eine Gruppe angeben müssen. Sie können keine einzelnen Benutzer angeben. Verwenden Sie Azure AD PowerShell, um die Objekt-ID für die Gruppe zu erhalten – z.b. den Befehl [Get-MsolGroup](/powershell/msonline/v1/get-msolgroup), für Version 1.0 des Moduls. Oder Sie können den **Objekt-ID**-Wert der Gruppe aus dem Azure-Portal kopieren.

Oder Sie möchten sicherstellen, dass nur Benutzer, die ordnungsgemäß für die Verwendung von Azure Information Protection lizenziert sind, Inhalte schützen können:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $True
```

Wenn Sie nicht länger Onboarding-Steuerelemente verwenden müssen, egal, ob Sie eine Gruppen- oder Lizenzierungsoption verwendet haben, führen Sie Folgendes aus:

```
Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $False
```


Weitere Informationen zu diesem Cmdlet und zusätzliche Beispiele finden Sie auf der Hilfeseite [Set-AadrmOnboardingControlPolicy](/powershell/aadrm/vlatest/set-aadrmonboardingcontrolpolicy).

Wenn Sie diese Onboarding-Steuerelemente verwenden, können alle Benutzer in der Organisation immer geschützte Inhalte nutzen, die durch Ihre Teilmenge von Benutzern geschützt wurde, können aber Informationsschutz aus Clientanwendungen nicht selbst anwenden. Beispielsweise sehen sie nicht die Standardvorlagen in ihren Office-Clients, die automatisch veröffentlicht werden, wenn der Azure Rights Management-Dienst aktiviert ist, oder benutzerdefinierte Vorlagen, die Sie ggf. konfiguriert haben.  Serverseitige Anwendung wie z.B. Exchange können eigene Steuerelemente pro Benutzer für die Rights Management-Integration implementieren, um das gleiche Ergebnis zu erzielen.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] jetzt für Ihre Organisation aktiviert haben, verwenden Sie die [Roadmap für die Bereitstellung von Azure Information Protection](../plan-design/deployment-roadmap.md), um herauszufinden, ob Sie vor dem Rollout von Azure Information Protection für Benutzer und Administratoren ggf. weitere Konfigurationsschritte ausführen müssen. 

Angenommen, Sie möchten [Vorlagen](configure-policy-templates.md) verwenden, um es den Benutzern zu erleichtern, Informationsschutz auf Dateien anzuwenden, Ihre lokalen Server durch Installation des [Rights Management-Connectors](deploy-rms-connector.md) für die Verwendung von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu verbinden und den [Azure Information Protection-Client](../rms-client/aip-client.md) bereitzustellen, der den Schutz aller Dateitypen auf allen Geräten unterstützt. 

Office-Dienste (z.B. Exchange Online und SharePoint Online) erfordern zusätzliche Konfigurationsschritte, bevor Sie deren IRM-Features (Information Rights Management) verwenden können. Informationen dazu, wie Ihre Anwendungen mit dem Rights Management-Dienst funktionieren, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](../understand-explore/applications-support.md).


[!INCLUDE[Commenting house rules](../includes/houserules.md)]