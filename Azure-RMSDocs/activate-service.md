---
title: Aktivieren von Azure Rights Management – AIP
description: Sie müssen den Azure Rights Management-Dienst aktivieren, damit Ihre Organisation damit beginnen kann, Dokumente und E-Mails mithilfe von Anwendungen und Diensten zu schützen, die diese Lösung für den Informationsschutz unterstützen.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/12/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2f05b95477405a2262b7dc0e129f17f9f5ff46db
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56256395"
---
# <a name="activating-azure-rights-management"></a>Aktivieren von Azure Rights Management

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Diese Konfigurationsinformationen richten sich an Administratoren, die für einen Dienst zuständig sind, der für alle Benutzer in einer Organisation gilt. Wenn Sie Hilfe und Informationen zur Verwendung der Rights Management-Funktionen für eine bestimmte Anwendung oder zum Öffnen einer Datei oder E-Mail suchen, die mit Rechten geschützt ist, verwenden Sie die zur Anwendung gehörende Hilfe und Anleitungen.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM**ein. Informationen zum Azure Information Protection-Client für Windows finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/client-user-guide.md).
>
> Technischen Support und Antworten auf Fragen zum Dienst finden Sie unter [Support options and community resources (Supportoptionen und Communityressourcen)](information-support.md#support-options-and-community-resources).

Nachdem der Azure Rights Management-Dienst für Azure Information Protection für Ihre Organisation aktiviert wurde, können Administratoren und Benutzer wichtige Daten mithilfe von Anwendungen und Diensten schützen, die diese Lösung zum Schutz von Informationen unterstützen. Administratoren können außerdem geschützte Dokumente und E-Mails, die Ihrer Organisation gehören, verwalten und überwachen. 


## <a name="do-you-need-to-activate-azure-rights-management"></a>Ist eine Aktivierung von Azure Rights Management erforderlich?

Wenn Sie über einen Serviceplan verfügen, der Azure Rights Management einschließt, müssen Sie den Dienst möglicherweise nicht aktivieren:

- **Wenn Ihr Abonnement Azure Rights Management oder Azure Information Protection einschließt und Ende Februar 2018 oder danach erworben wurde:** Der Dienst wird automatisch für Sie aktiviert. Sie müssen den Dienst nur dann aktivieren, wenn Sie oder ein anderer globaler Administrator Ihrer Organisation Azure Rights Management deaktiviert hat.

- **Wenn Ihr Abonnement Azure Rights Management oder Azure Information Protection einschließt und vor oder im Februar 2018 erworben wurde:** Microsoft wird gestartet, um den Azure Rights Management-Dienst für diese Abonnements zu aktivieren, wenn Ihr Mandant Exchange Online verwendet wird. Bei diesen Abonnements beginnt das Rollout der automatischen Aktivierung am 1. August 2018. Der Dienst wird für Sie aktiviert, sofern Sie bei Ausführung von [Get-IRMConfiguration](/powershell/module/exchange/encryption-and-certificates/get-irmconfiguration?view=exchange-ps) nicht feststellen, dass **AutomaticServiceUpdateEnabled** auf **false** festgelegt ist. 

Wenn keines der nachfolgenden Szenarien auf Sie zutrifft, müssen Sie den Schutzdienst manuell aktivieren. 

Wenn der Dienst aktiviert ist, können alle Benutzer in Ihrer Organisation den Informationsschutz auf die eigenen Dokumente und E-Mails anwenden und Dokumente und E-Mails öffnen (nutzen), die durch den Azure Rights Management-Dienst geschützt werden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

## <a name="how-to-activate-or-confirm-the-status-of-the-azure-rights-management-service"></a>Aktivieren oder Bestätigen des Azure Rights Management-Dienststatus 

> [!IMPORTANT]
> Aktivieren Sie den Azure Rights Management-Dienst nicht, wenn Sie Active Directory Rights Management Services (AD RMS) für Ihre Organisation bereitgestellt haben. [Weitere Informationen](prepare-environment-adrms.md)

Wenn Sie diese Lösung zum Schutz von Daten verwenden möchten, muss Ihre Organisation über einen Serviceplan verfügen, der den Azure Rights Management-Dienst von Azure Information Protection beinhaltet. Ohne den entsprechenden Serviceplan kann der Azure Rights Management-Dienst nicht aktiviert werden. Sie müssen eine der folgenden Komponenten besitzen:

- Einen [Azure Information Protection-Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) 

- Einen [Office 365-Plan, der Rights Management enthält](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf).

Wenn der Azure Rights Management-Dienst aktiviert ist, können alle Benutzer in Ihrer Organisation den Informationsschutz auf die eigenen Dokumente und E-Mails anwenden und Dokumente und E-Mails öffnen (nutzen), die durch den Azure Rights Management-Dienst geschützt werden. Bei Bedarf können Sie jedoch einschränken, wer Informationsschutz anwenden kann, indem Sie Onboardingsteuerungsrichtlinien für eine in Phasen vorgenommene Bereitstellung verwenden. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](#configuring-onboarding-controls-for-a-phased-deployment) in diesem Artikel.

## <a name="choosing-your-activation-method"></a>Auswählen der Aktivierungsmethode

Wählen Sie aus, ob Sie Office 365 Admin Center oder das Azure-Portal verwenden möchten, um Anweisungen zum Aktivieren des Rights Management-Diensts über Ihr Verwaltungsportal zu erhalten:

- [Office 365 Admin Center:](activate-office365.md) erfordert ein globales Administratorkonto

- [Azure-Portal:](activate-azure.md) erfordert kein globales Administratorkonto

Alternativ können Sie die folgenden PowerShell-Befehle verwenden:

1. Installieren Sie das AADRM-Modul, um den Schutzdienst zu konfigurieren und zu verwalten. Anweisungen finden Sie unter [Installieren des AADRM-PowerShell-Moduls](install-powershell.md).

2. Führen Sie in einer PowerShell-Sitzung [Connect-AadrmService](/powershell/module/aadrm/connect-aadrmservice) aus, und geben Sie die Details des globalen Administratorkontos für Ihren Azure Information Protection-Mandanten an, wenn Sie dazu aufgefordert werden.

3. Führen Sie [Get-Aadrm](/powershell/aadrm/vlatest/get-aadrm) aus, um zu überprüfen, ob der Azure Rights Management-Dienst aktiviert ist. Falls als Status **Aktiviert** angezeigt wird, wurde der Dienst aktiviert. Bei **Deaktiviert** wurde der Dienst deaktiviert.

4. Führen Sie zum Aktivieren des Diensts [Enable-Aadrm](/powershell/aadrm/vlatest/enable-aadrm) aus.

## <a name="configuring-onboarding-controls-for-a-phased-deployment"></a>Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung
Wenn nicht alle Benutzer sofort die Möglichkeit haben sollen, Dokumente und E-Mails mithilfe von Azure Rights Management zu schützen, können Sie mit dem PowerShell-Befehl [Set-AadrmOnboardingControlPolicy](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) benutzerbasierte Onboardingrichtlinien konfigurieren. Sie können diesen Befehl ausführen, bevor oder nachdem Sie den Azure Rights Management-Dienst aktivieren.

> [!IMPORTANT]
> Damit Sie diesen Befehl verwenden können, benötigen Sie mindestens Version **2.1.0.0** des [ PowerShell-Moduls für Azure Rights Management](https://www.powershellgallery.com/packages/AADRM).
>
> Um die installierte Version zu überprüfen, führen Sie Folgendes aus: **(Get-Module aadrm –ListAvailable).Version**

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

Wenn Sie diese Onboarding-Steuerelemente verwenden, können alle Benutzer in der Organisation immer geschützte Inhalte nutzen, die durch Ihre Teilmenge von Benutzern geschützt wurde, können aber Informationsschutz aus Clientanwendungen nicht selbst anwenden. Beispielsweise sehen sie nicht die Standardvorlagen in ihren Office-Apps, die automatisch veröffentlicht werden, wenn der Azure Rights Management-Dienst aktiviert ist, oder benutzerdefinierte Vorlagen, die Sie ggf. konfiguriert haben. Serverseitige Anwendung wie z.B. Exchange können eigene Steuerelemente pro Benutzer für die Rights Management-Integration implementieren, um das gleiche Ergebnis zu erzielen. Sie können beispielsweise verhindern, dass Benutzer E-Mails in Outlook im Web schützen, indem Sie [Set-OwaMailboxPolicy](/powershell/module/exchange/client-access/set-owamailboxpolicy?view=exchange-ps) verwenden, um den Parameter *IRMEnabled* auf *$false* zu setzen.


## <a name="next-steps"></a>Nächste Schritte
Wenn der Azure Rights Management-Dienst für Ihre Organisation aktiviert wird, ist es erforderlich, dass Sie die [Roadmap für die Bereitstellung von Azure Information Protection](deployment-roadmap.md) verwenden, um zu überprüfen, ob Sie vor dem Rollout von Azure Information Protection für Benutzer und Administratoren ggf. weitere Konfigurationsschritte ausführen müssen. 

Angenommen, Sie möchten [Vorlagen](configure-policy-templates.md) verwenden, um es den Benutzern zu erleichtern, Informationsschutz auf Dateien anzuwenden, Ihre lokalen Server durch Installation des [Rights Management-Connectors](deploy-rms-connector.md) für die Verwendung von Azure Rights Management zu verbinden und den [Azure Information Protection-Client](./rms-client/aip-client.md) bereitzustellen, der den Schutz aller Dateitypen auf allen Geräten unterstützt. 

Office-Dienste (z.B. Exchange Online und SharePoint Online) erfordern zusätzliche Konfigurationsschritte, bevor Sie deren IRM-Features (Information Rights Management) verwenden können. Informationen dazu, wie Ihre Anwendungen mit dem Rights Management-Dienst funktionieren, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).


