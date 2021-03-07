---
title: Aktivieren des Schutz Dienstanbieter von Azure Information Protection (AIP)
description: Erfahren Sie, wie Sie den Azure Rights Management Protection-Dienst aktivieren, um Ihre Dokumente und e-Mails zu schützen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/30/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e3089134dc3b289d024c507aec886d622e4d6e16
ms.sourcegitcommit: 74b8d03d1ede3da12842b84546417e63897778bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2021
ms.locfileid: "102414768"
---
# <a name="activating-the-protection-service-from-azure-information-protection"></a>Aktivieren des Schutz Dienstanbieter von Azure Information Protection

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

In diesem Artikel wird beschrieben, wie Administratoren den Azure Rights Management Protection Service for Azure Information Protection (AIP) aktivieren können. Wenn der Schutzdienst für Ihre Organisation aktiviert ist, können Administratoren und Benutzer wichtige Daten mithilfe von Anwendungen und Diensten schützen, die diese Lösung für den Informationsschutz unterstützen. Administratoren können außerdem geschützte Dokumente und E-Mails, die Ihrer Organisation gehören, verwalten und überwachen.

> [!NOTE]
> Diese Konfigurationsinformationen richten sich an Administratoren, die für einen Dienst zuständig sind, der für alle Benutzer in einer Organisation gilt. Wenn Sie Hilfe und Informationen zur Verwendung der Rights Management-Funktionen für eine bestimmte Anwendung oder zum Öffnen einer Datei oder E-Mail suchen, die mit Rechten geschützt ist, verwenden Sie die zur Anwendung gehörende Hilfe und Anleitungen.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM** ein. Informationen zum Azure Information Protection-Client für Windows finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/clientv2-user-guide.md).
>
> Technischen Support und Antworten auf Fragen zum Dienst finden Sie unter [Support options and community resources (Supportoptionen und Communityressourcen)](information-support.md#support-options-and-community-resources).

## <a name="automatic-activation-for-azure-rights-management"></a>Automatische Aktivierung für Azure Rights Management

Wenn Sie über einen Serviceplan verfügen, der Azure Rights Management enthält, müssen Sie den Dienst möglicherweise nicht aktivieren:

- **Wenn Ihr Abonnement, das Azure Rights Management oder Azure Information Protection umfasst, bis Ende Februar 2018 oder höher abgerufen wurde,** wird der Dienst automatisch für Sie aktiviert. Sie müssen den Dienst nur dann aktivieren, wenn Sie oder ein anderer globaler Administrator Ihrer Organisation Azure Rights Management deaktiviert hat.

- **Wenn Ihr Abonnement, das Azure Rights Management oder Azure Information Protection umfasst, vor oder während Februar 2018 abgerufen wurde**: aktiviert Microsoft den Azure Rights Management-Dienst für diese Abonnements, wenn Ihr Mandant Exchange Online verwendet. Für diese Abonnements wird der Dienst für Sie aktiviert, es sei denn, Sie sehen, dass **automaticserviceupdateaktivierte** auf **false** festgelegt ist, wenn Sie [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration)ausführen. 

Wenn keines der aufgeführten Szenarien auf Sie zutrifft, müssen Sie den Schutzdienst manuell aktivieren. 

Wenn der Dienst aktiviert ist, können alle Benutzer in Ihrer Organisation den Informationsschutz auf die eigenen Dokumente und E-Mails anwenden und Dokumente und E-Mails öffnen (nutzen), die durch den Azure Rights Management-Dienst geschützt werden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

## <a name="how-to-activate-or-confirm-the-status-of-the-protection-service"></a>Aktivieren oder bestätigen des Status des Schutz Dienstanbieter 

> [!IMPORTANT]
> Aktivieren Sie den Schutzdienst nicht, wenn Sie Active Directory Rights Management Services (AD RMS) für Ihre Organisation bereitgestellt haben. [Weitere Informationen](prepare-environment-adrms.md)

Wenn Sie diese Lösung zum Schutz von Daten verwenden möchten, muss Ihre Organisation über einen Serviceplan verfügen, der den Azure Rights Management-Dienst von Azure Information Protection beinhaltet. Ohne diesen kann der Schutzdienst nicht aktiviert werden. Sie müssen eine der folgenden Komponenten besitzen:

- Ein [Azure Information Protection Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- Einen [Office 365-Plan, der Rights Management enthält](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Wenn der Schutzdienst aktiviert ist, können alle Benutzer in Ihrer Organisation Informationsschutz auf Ihre Dokumente und e-Mails anwenden, und alle Benutzer können Dokumente und e-Mails öffnen (nutzen), die durch diesen Dienst geschützt wurden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

## <a name="supported-activation-methods"></a>Unterstützte Aktivierungsmethoden

Um zu erfahren, wie Sie den Schutzdienst über ihr Verwaltungs Portal aktivieren, wählen Sie aus, ob das Microsoft 365 Admin Center oder das Azure-Portal verwendet werden soll:

- [Microsoft 365 Admin Center:](activate-office365.md) erfordert ein globales Administratorkonto

- [Azure-Portal:](activate-azure.md) erfordert kein globales Administratorkonto

Alternativ können Sie die folgenden PowerShell-Befehle verwenden:

1. Installieren Sie das aipservice-Modul, um den Schutzdienst zu konfigurieren und zu verwalten. Anweisungen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](install-powershell.md).

2. Führen Sie in einer PowerShell [-Sitzung Connect-aipservice](/powershell/module/aipservice/connect-aipservice)aus, und geben Sie, wenn Sie dazu aufgefordert werden, die Details des globalen Administrator Kontos für Ihren Azure Information Protection Mandanten an.

3. Führen [Sie Get-aipservice](/powershell/module/aipservice/get-aipservice) aus, um zu überprüfen, ob der Schutzdienst aktiviert ist. Falls als Status **Aktiviert** angezeigt wird, wurde der Dienst aktiviert. Bei **Deaktiviert** wurde der Dienst deaktiviert.

4. Um den Dienst zu aktivieren, führen Sie [enable-aipservice](/powershell/module/aipservice/enable-aipservice)aus.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurieren der Onboardingsteuerungsrichtlinien für eine Bereitstellung in Phasen
Wenn Sie nicht möchten, dass alle Benutzer Dokumente und e-Mails direkt mithilfe von Azure Information Protection schützen können, können Sie die Onboarding-Steuerelemente für Benutzer mithilfe des PowerShell-Befehls [Set-aipserviceonboardingcontrolpolicy](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy) konfigurieren. Sie können diesen Befehl ausführen, bevor oder nachdem Sie den Azure Rights Management-Dienst aktivieren.

Wenn Sie beispielsweise möchten, dass zunächst nur Administratoren der Gruppe "IT-Abteilung" (die die Objekt-ID "fbb99ded-32a0-45f1-b038-38b519009503" hat) in der Lage sein sollen, Inhalte zu Testzwecken zu schützen, verwenden Sie den folgenden Befehl:

```
Set-AipServiceOnboardingControlPolicy -UseRmsUserLicense $False -SecurityGroupObjectId "fbb99ded-32a0-45f1-b038-38b519009503"
```

Beachten Sie, dass Sie für diese Konfigurationsoption eine Gruppe angeben müssen. Sie können keine einzelnen Benutzer angeben. Verwenden Sie Azure AD PowerShell, um die Objekt-ID für die Gruppe zu erhalten – z.b. den Befehl [Get-MsolGroup](/powershell/msonline/v1/get-msolgroup), für Version 1.0 des Moduls. Oder Sie können den **Objekt-ID**-Wert der Gruppe aus dem Azure-Portal kopieren.

Oder Sie möchten sicherstellen, dass nur Benutzer, die ordnungsgemäß für die Verwendung von Azure Information Protection lizenziert sind, Inhalte schützen können:

```
Set-AipServiceOnboardingControlPolicy -UseRmsUserLicense $True
```

Wenn Sie nicht länger Onboarding-Steuerelemente verwenden müssen, egal, ob Sie eine Gruppen- oder Lizenzierungsoption verwendet haben, führen Sie Folgendes aus:

```
Set-AipServiceOnboardingControlPolicy -UseRmsUserLicense $False
```

Weitere Informationen zu diesem Cmdlet und zusätzlichen Beispielen finden Sie in der Hilfe zu [Set-aipserviceonboardingcontrolpolicy](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy) .

Wenn Sie diese Onboarding-Steuerelemente verwenden, können alle Benutzer in der Organisation immer geschützte Inhalte nutzen, die durch Ihre Teilmenge von Benutzern geschützt wurde, können aber Informationsschutz aus Clientanwendungen nicht selbst anwenden. Beispielsweise sehen Sie in Ihren Office-Apps nicht die standardmäßigen Schutz Vorlagen, die automatisch veröffentlicht werden, wenn der Schutzdienst aktiviert wird, oder benutzerdefinierte Vorlagen, die Sie möglicherweise konfigurieren. Server seitige Anwendungen wie Exchange können eigene Steuerelemente pro Benutzer implementieren, um das gleiche Ergebnis zu erzielen. Sie können beispielsweise verhindern, dass Benutzer E-Mails in Outlook im Web schützen, indem Sie [Set-OwaMailboxPolicy](/powershell/module/exchange/client-access/set-owamailboxpolicy) verwenden, um den Parameter *IRMEnabled* auf *$false* zu setzen.


## <a name="next-steps"></a>Nächste Schritte
Wenn der Schutzdienst für Ihre Organisation aktiviert ist, verwenden Sie die Roadmap für die [Bereitstellung von Azure Information Protection](deployment-roadmap.md) , um zu überprüfen, ob Sie vor dem Rollout von Azure Information Protection für Benutzer und Administratoren weitere Konfigurationsschritte ausführen müssen. 

Beispielsweise können Sie [Vorlagen](configure-policy-templates.md) verwenden, um es den Benutzern zu erleichtern, Schutz auf Dateien anzuwenden, ihre lokalen Server mit dem Schutzdienst zu verbinden, indem Sie den [Rights Management-Connector](deploy-rms-connector.md)installieren und den [Azure Information Protection Client](./rms-client/aip-client.md) bereitstellen, der den Schutz aller Dateitypen auf allen Geräten unterstützt. 

Office-Dienste, wie z. b. Exchange Online und Microsoft SharePoint, erfordern zusätzliche Konfigurationen, bevor Sie Ihre Informationen Rights Management (unm)-Features verwenden können. Informationen dazu, wie Ihre Anwendungen mit dem Schutzdienst (Azure-Rights Management) funktionieren, finden Sie [unter Unterstützung des Azure Rights Management-Dienstanbieter durch Anwendungen](applications-support.md).

