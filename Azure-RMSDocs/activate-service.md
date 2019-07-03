---
title: Aktivieren des schutzdiensts von Azure Information Protection
description: Der Azure Rights Management-Schutzdienst muss aktiviert werden, bevor Ihre Organisation damit beginnen kann, schützen Dokumente und e-Mails mit Anwendungen und Dienste, die diese datenschutzlösung unterstützen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/03/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 16c3ded1ea8f5d7c2191b994ec63132bd5f9bf1e
ms.sourcegitcommit: a5f595f8a453f220756fdc11fd5d466c71d51963
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2019
ms.locfileid: "67520318"
---
# <a name="activating-the-protection-service-from-azure-information-protection"></a>Aktivieren des schutzdiensts von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Diese Konfigurationsinformationen richten sich an Administratoren, die für einen Dienst zuständig sind, der für alle Benutzer in einer Organisation gilt. Wenn Sie Hilfe und Informationen zur Verwendung der Rights Management-Funktionen für eine bestimmte Anwendung oder zum Öffnen einer Datei oder E-Mail suchen, die mit Rechten geschützt ist, verwenden Sie die zur Anwendung gehörende Hilfe und Anleitungen.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM**ein. Informationen zum Azure Information Protection-Client für Windows finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/client-user-guide.md).
>
> Technischen Support und Antworten auf Fragen zum Dienst finden Sie unter [Support options and community resources (Supportoptionen und Communityressourcen)](information-support.md#support-options-and-community-resources).

Wenn für Ihre Organisation der Schutzdienst für Azure Information Protection aktiviert ist, können Administratoren und Benutzer starten, so schützen wichtige Daten mithilfe von Anwendungen und Dienste, die diese datenschutzlösung unterstützen. Administratoren können außerdem geschützte Dokumente und E-Mails, die Ihrer Organisation gehören, verwalten und überwachen. 


## <a name="do-you-need-to-activate-the-protection-service-azure-rights-management"></a>Möchten Sie den Schutzdienst Azure Rights Management aktivieren?

Wenn Sie über einen Serviceplan verfügen, der Azure Rights Management einschließt, müssen Sie den Dienst möglicherweise nicht aktivieren:

- **Wenn Ihr Abonnement Azure Rights Management oder Azure Information Protection einschließt und Ende Februar 2018 oder danach erworben wurde:** Der Dienst wird automatisch für Sie aktiviert. Sie müssen den Dienst nur dann aktivieren, wenn Sie oder ein anderer globaler Administrator Ihrer Organisation Azure Rights Management deaktiviert hat.

- **Wenn Ihr Abonnement Azure Rights Management oder Azure Information Protection einschließt und vor oder im Februar 2018 erworben wurde:** Microsoft wird gestartet, um den Azure Rights Management-Dienst für diese Abonnements zu aktivieren, wenn Ihr Mandant Exchange Online verwendet wird. Bei diesen Abonnements beginnt das Rollout der automatischen Aktivierung am 1. August 2018. Der Dienst wird für Sie aktiviert, sofern Sie bei Ausführung von [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration?view=exchange-ps) nicht feststellen, dass **AutomaticServiceUpdateEnabled** auf **false** festgelegt ist. 

Wenn keines der nachfolgenden Szenarien auf Sie zutrifft, müssen Sie den Schutzdienst manuell aktivieren. 

Wenn der Dienst aktiviert ist, können alle Benutzer in Ihrer Organisation den Informationsschutz auf die eigenen Dokumente und E-Mails anwenden und Dokumente und E-Mails öffnen (nutzen), die durch den Azure Rights Management-Dienst geschützt werden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

## <a name="how-to-activate-or-confirm-the-status-of-the-protection-service"></a>Aktivieren oder bestätigen Sie den Status des schutzdiensts 

> [!IMPORTANT]
> Den Schutzdienst kann nicht aktiviert werden, wenn Sie Active Directory Rights Management Services (AD RMS) für Ihre Organisation bereitgestellt haben. [Weitere Informationen](prepare-environment-adrms.md)

Wenn Sie diese Lösung zum Schutz von Daten verwenden möchten, muss Ihre Organisation über einen Serviceplan verfügen, der den Azure Rights Management-Dienst von Azure Information Protection beinhaltet. Der Schutzdienst kann nicht aktiviert werden, ohne diesen Schritt. Sie müssen eine der folgenden Komponenten besitzen:

- Einen [Azure Information Protection-Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- Einen [Office 365-Plan, der Rights Management enthält](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Wenn der Schutzdienst aktiviert ist, alle Benutzer in Ihrer Organisation den Schutz von Informationen auf ihre Dokumente und e-Mails anwenden können und können alle Benutzer öffnen (nutzen) Dokumente und e-Mails, die von diesem Dienst geschützt wurden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

## <a name="choosing-your-activation-method"></a>Auswählen der Aktivierungsmethode

Anweisungen zum Aktivieren des schutzdiensts über Ihr Verwaltungsportal auswählen, ob das Microsoft 365 Administrationscenter oder das Azure-Portal verwenden:

- [Microsoft 365 Admin Center:](activate-office365.md) erfordert ein globales Administratorkonto

- [Azure-Portal:](activate-azure.md) erfordert kein globales Administratorkonto

Alternativ können Sie die folgenden PowerShell-Befehle verwenden:

1. Installieren Sie das AIPService Modul, konfigurieren und Verwalten des schutzdiensts. Anweisungen hierzu finden Sie unter [AIPService PowerShell-Modul installieren](install-powershell.md).

2. Führen Sie aus einer PowerShell-Sitzung [Connect-AipService](/powershell/module/aipservice/connect-aipservice), und geben Sie bei Aufforderung die Details des globalen Administrators für Ihren Azure Information Protection-Mandanten.

3. Führen Sie [Get-AipService](/powershell/module/aipservice/get-aipservice) zu bestätigen, dass der Schutzdienst aktiviert ist. Falls als Status **Aktiviert** angezeigt wird, wurde der Dienst aktiviert. Bei **Deaktiviert** wurde der Dienst deaktiviert.

4. Führen Sie zum Aktivieren des Diensts [aktivieren-AipService](/powershell/module/aipservice/enable-aipservice).

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurieren der Onboardingsteuerungsrichtlinien für eine Bereitstellung in Phasen
Wenn Sie nicht, dass alle Benutzer, um Dokumente und e-Mails mithilfe von Azure Information Protection direkt schützen zu können möchten, können Sie die Onboarding-Steuerelemente für Benutzer konfigurieren, mit der [Set-AipServiceOnboardingControlPolicy](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy) PowerShell -Befehl. Sie können diesen Befehl ausführen, bevor oder nachdem Sie den Azure Rights Management-Dienst aktivieren.

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

Weitere Informationen zu diesem Cmdlet und zusätzliche Beispiele finden Sie unter den [Set-AipServiceOnboardingControlPolicy](/powershell/module/aipservice/set-aipserviceonboardingcontrolpolicy) helfen.

Wenn Sie diese Onboarding-Steuerelemente verwenden, können alle Benutzer in der Organisation immer geschützte Inhalte nutzen, die durch Ihre Teilmenge von Benutzern geschützt wurde, können aber Informationsschutz aus Clientanwendungen nicht selbst anwenden. Z. B. in ihren Office-apps sehen Sie nicht die Standardvorlagen für den Schutz, die automatisch veröffentlicht werden, wenn der Schutzdienst aktiviert ist, oder benutzerdefinierte Vorlagen, die Sie konfigurieren können. Serverseitigen Anwendungen, wie z.B. Exchange können eigene Steuerelemente pro Benutzer, um das gleiche Ergebnis erzielen implementieren. Sie können beispielsweise verhindern, dass Benutzer E-Mails in Outlook im Web schützen, indem Sie [Set-OwaMailboxPolicy](/powershell/module/exchange/client-access/set-owamailboxpolicy?view=exchange-ps) verwenden, um den Parameter *IRMEnabled* auf *$false* zu setzen.


## <a name="next-steps"></a>Nächste Schritte
Wenn für Ihre Organisation der Schutzdienst aktiviert ist, verwenden Sie die [Roadmap für die Bereitstellung von Azure Information Protection](deployment-roadmap.md) überprüft, ob es weitere Konfigurationsschritte ausführen, die Sie benötigen sind Sie vor dem Rollout von Azure Schutz von Informationen für Benutzer und Administratoren. 

Beispielsweise möchten Sie verwenden [Vorlagen](configure-policy-templates.md) um Benutzern das Anwenden von Schutz auf Dateien zu vereinfachen, verbinden Sie Ihre lokalen Server Verwendung des schutzdiensts durch die Installation von der [Rights Management-verbindungsdiensts](deploy-rms-connector.md), und Bereitstellen der [Azure Information Protection-Client](./rms-client/aip-client.md) , die Schutz aller Dateitypen auf allen Geräten unterstützt. 

Office-Dienste (z.B. Exchange Online und SharePoint Online) erfordern zusätzliche Konfigurationsschritte, bevor Sie deren IRM-Features (Information Rights Management) verwenden können. Weitere Informationen zur Funktionsweise von Anwendungen mit der Azure Rights Management-Schutzdienst finden Sie unter [Unterstützung der Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

