---
title: Roadmap für die Bereitstellung von Azure Information Protection (AIP) nur für den Schutz
description: Führen Sie diese Schritte aus, um Azure Information Protection (AIP) für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten, wenn Sie nur den Schutz implementieren möchten.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/23/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 40303d80ef0e1e9274d8b2258b4e400616dd875a
ms.sourcegitcommit: efeb486e49c3e370d7fd8244687cd3de77cd8462
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/16/2020
ms.locfileid: "97583641"
---
# <a name="azure-information-protection-deployment-roadmap-for-protection-only"></a>Azure Information Protection bereitstellungsroadmap nur für den Schutz

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [Azure Information Protection klassischer Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

> [!TIP]
> Alternativ können Sie einen der folgenden Artikel suchen:
> - [Leitfaden zur AIP-Bereitstellung für Klassifizierung, Bezeichnung und Schutz](deployment-roadmap-classify-label-protect.md)
> - [Schrittanleitungen für häufige Szenarien, in denen Azure Information Protection verwendet wird](how-to-guides.md)
> - [Azure Information Protection releaseroadmap](information-support.md#information-about-new-releases-and-updates)

Verwenden Sie die folgenden Schritte als Empfehlungen, die Sie beim vorbereiten, implementieren und Verwalten von Azure Information Protection für Ihre Organisation unterstützen, wenn Sie nur den Schutz von Daten implementieren möchten.

Diese Roadmap wird für Kunden mit einem Abonnement empfohlen, das nicht sowohl Klassifizierung als auch Bezeichnungen unterstützt, aber den Schutz ohne Bezeichnungen unterstützt. Der klassische AIP-Client muss installiert sein. 

## <a name="deployment-process"></a>Bereitstellungsprozess

Führen Sie die folgenden Schritte aus:

1. [Vergewissern Sie sich, dass Sie über ein Abonnement verfügen, das den AIP-Schutzdienst enthält](#confirm-that-you-have-a-subscription-that-includes-the-aip-protection-service) 
1. [Vorbereiten Ihres Mandanten für Azure Information Protection](#prepare-your-tenant-to-use-azure-information-protection)
1. [Installieren Sie die Azure Information Protection Classic und Client configure Applications and Services for Rights Management](#install-the-azure-information-protection-classic-and-client-configure-applications-and-services-for-rights-management)
1. [Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten](#use-and-monitor-your-data-protection-solutions)
1. [Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto](#administer-the-protection-service-for-your-tenant-account-as-needed)

## <a name="confirm-that-you-have-a-subscription-that-includes-the-aip-protection-service"></a>Vergewissern Sie sich, dass Sie über ein Abonnement verfügen, das den AIP-Schutzdienst enthält

Stellen Sie sicher, dass Ihre Organisation über ein Abonnement verfügt, das die von Ihnen erwarteten Funktionen und Features umfasst. Sie können die Abonnement Informationen und Featureliste auf der Seite [Azure Information Protection Preise](https://azure.microsoft.com/pricing/details/information-protection) verwenden.

Weisen Sie jedem Benutzer in Ihrer Organisation, der Dokumente und e-Mails schützen soll, eine Lizenz aus diesem Abonnement zu.

> [!IMPORTANT]
> Weisen Sie keine Benutzerlizenzen manuell aus dem kostenlosen RMS for Individuals-Abonnement zu, und verwenden Sie diese Lizenz nicht zum Verwalten des Azure Rights Management-Diensts für Ihre Organisation. 
>
> Für diese Lizenzen wird im Microsoft 365 Admin Center **Rights Management Ad-hoc** und beim Ausführen des Azure AD PowerShell-Cmdlets [Get-MsolAccountSku](/previous-versions/azure/dn194118(v=azure.100))**RIGHTSMANAGEMENT_ADHOC** angezeigt. 
>
> Weitere Informationen dazu, wie das RMS for Individuals-Abonnement automatisch gewährt und Benutzern zugewiesen wird, finden Sie unter [RMS for Individuals und Azure Information Protection](./rms-for-individuals.md).

## <a name="prepare-your-tenant-to-use-azure-information-protection"></a>Vorbereiten Ihres Mandanten für Azure Information Protection

Führen Sie die folgende Vorbereitungsschritte aus, bevor Sie mit der Verwendung des Schutzdiensts von Azure Information Protection beginnen:

1. **Einrichten von Benutzerkonten und Gruppen für aip**

    Stellen Sie sicher, dass Ihr Microsoft 365 Mandanten die Benutzerkonten und-Gruppen enthält, die von Azure Information Protection zum Authentifizieren und Autorisieren von Benutzern in Ihrer Organisation verwendet werden. Erstellen Sie bei Bedarf diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. 

    Weitere Informationen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md).

1. **Entscheiden Sie, wie Sie Ihren Mandanten Schlüssel verwalten möchten.**

    Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Implementieren Sie für zusätzliche Sicherheit den Hyok-Schutz (Hold Your Own Key). 

    Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

1. **Installieren von PowerShell für aip**

    Installieren Sie das PowerShell-Modul für aipservice auf mindestens einem Computer, der über Internet Zugriff verfügt. Sie können diesen Schritt jetzt oder später durchführen. 

    Weitere Informationen finden Sie unter [Installieren des aipservice-PowerShell-Moduls](./install-powershell.md).

1. **Nur AD RMS: Migrieren Sie Ihre Daten in die Cloud.**

    Wenn Sie derzeit AD RMS verwenden: Führen Sie eine Migration durch, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. 

    Weitere Informationen finden Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

1. **Schutz aktivieren**

    Stellen Sie sicher, dass der Schutzdienst aktiviert ist, damit Sie mit dem Schützen von Dokumenten und E-Mails beginnen können. Wenn Sie in Phasen bereitstellen, konfigurieren Sie die Onboarding-Steuerelemente für Benutzer, um die Fähigkeit der Benutzer einzuschränken, Schutz anzuwenden. 

    Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](./activate-service.md).

1. **Optionale Features nach Bedarf konfigurieren**

    Es empfiehlt sich, eine der folgenden Features entweder jetzt oder später zu konfigurieren.
    
    |Funktion  |BESCHREIBUNG  |
    |---------|---------|
    |**Benutzerdefinierte Vorlagen für Schutzeinstellungen**     |  Wenn die Standardvorlagen für Ihre Organisation nicht ausreichen, konfigurieren Sie benutzerdefinierte Vorlagen. </br>Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](./configure-policy-templates.md).       |
    |**Nutzungsprotokollierung**     | Konfigurieren Sie die Verwendungs Protokollierung, um zu überwachen, wie Ihre Organisation den Schutzdienst verwendet. </br>Weitere Informationen finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).        |
    | | |

## <a name="install-the-azure-information-protection-classic-and-client-configure-applications-and-services-for-rights-management"></a>Installieren Sie die Azure Information Protection Classic und Client configure Applications and Services for Rights Management

Führen Sie die folgenden Schritte aus:

1. **Bereitstellen des Azure Information Protection des klassischen Clients**
    
    Installieren Sie den klassischen Client für Benutzer, um Office 2010 zu unterstützen, um andere Dateien als Office-Dokumente und e-Mails zu schützen und geschützte Dokumente zu verfolgen und Benutzer Schulungen für diesen Client bereitzustellen. 

    Weitere Informationen finden Sie unter [Azure Information Protection Classic-Client für Windows](./rms-client/aip-client.md) und [AIP für Windows und Office-Versionen in erweiterter Unterstützung](known-issues.md#aip-for-windows-and-office-versions-in-extended-support).

2. **Konfigurieren von Office-Anwendungen und -Diensten**
    
    Konfigurieren Sie Office-Anwendungen und-Dienste für die Features für die Verwaltung von Informationsrechten in SharePoint oder Exchange Online. 

    Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](./configure-applications.md).

3. **Konfigurieren des Administratorfeatures für die Datenwiederherstellung**
    
    Wenn vorhandene IT-Dienste von Azure Information Protection geschützte Dateien überprüfen müssen (z.B. DLP-Lösungen, Gateways zur Inhaltsverschlüsselung und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure Rights Management. 

    Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Information Protection-und Ermittlungsdienste oder Datenwiederherstellung](./configure-super-users.md).

4. **Massenschützen vorhandener Dateien** 
    
    Sie können PowerShell-Cmdlets verwenden, um mehrere Dateitypen massenzuschützen oder den Schutz aufzuheben. 

    Weitere Informationen finden Sie im Administrator Handbuch unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](./rms-client/client-admin-guide-powershell.md) .
    
    Für Dateien auf Windows-basierten Dateiservern können Sie diese Cmdlets mit einem Skript und der Windows Server-Dateiklassifizierungsinfrastruktur verwenden. Weitere Informationen finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](./rms-client/configure-fci.md).

5. **Bereitstellen des Connectors für lokale Server**
    
    Wenn Sie über lokale Dienste verfügen, die Sie mit dem Schutzdienst verwenden möchten, installieren und konfigurieren Sie den Rights Management-Connector. 

    Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](./deploy-rms-connector.md).

## <a name="use-and-monitor-your-data-protection-solutions"></a>Verwenden und Überwachen Ihrer Lösungen zum Schutz von Daten

Sie sind jetzt bereit, Ihre Daten zu schützen und zu protokollieren, wie Ihr Unternehmen den Schutzdienst verwendet. 

Weitere Informationen finden Sie unter

- [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](./help-users.md)
- [Protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md)

## <a name="administer-the-protection-service-for-your-tenant-account-as-needed"></a>Bedarfsgesteuertes Verwalten des Schutzdiensts für Ihr Mandantenkonto

Wenn Sie mit der Verwendung des Schutzdiensts beginnen, kann PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. PowerShell kann ebenfalls für einige der erweiterten Konfigurationen erforderlich sein. 

Weitere Informationen finden Sie unter [Verwalten des Schutzes von Azure Information Protection mithilfe von PowerShell](./administer-powershell.md).

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie Azure Information Protection bereitstellen, ist es möglicherweise hilfreich, die [häufig gestellten Fragen](faqs.md)und die Seite [Informationen und Support](information-support.md) für weitere Ressourcen zu überprüfen.