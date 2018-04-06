---
title: Vorbereiten der Umgebung für Azure RMS und AD RMS
description: Leitfaden, wenn Sie Azure Rights Management mit AD RMS bereitgestellt haben
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a233ddab67832e2de59b1fc0727296a8f3017db7
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Vorbereiten der Umgebung für Azure Rights Management, wenn Sie auch über Active Directory-Rechteverwaltungsdienste (AD RMS) verfügen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Wichtiger Leitfaden, wenn Sie bereits Active Directory Rights Management Services (AD RMS) nutzen und eines der folgenden Szenarios vorliegt:

- [Ihr Abonnement mit Azure Rights Management wurde im Februar 2018 oder danach erworben.](#your-subscription-was-purchased-during-or-after-february-2018)

- [Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal konfigurieren.](#you-see-an-option-to activate-azure-rights-management-when-you-configure-azure-information-protection)

## <a name="your-subscription-was-purchased-during-or-after-february-2018"></a>Ihr Abonnement wurde im Februar 2018 oder danach erworben

Ab Ende Februar 2018 ist Azure Rights Management in neuen Abonnements mit Azure Information Protection standardmäßig aktiviert. Wenn dieser Dienst automatisch für Sie aktiviert wurde und Sie auch Active Directory Rights Management Services (AD RMS) verwenden, ist diese Kombination nicht kompatibel. Ohne zusätzliche Schritte werden einige Computer eventuell automatisch mithilfe des Azure Rights Management-Diensts gestartet und mit Ihrem AD RMS-Cluster verbunden. Dieses Szenario wird nicht unterstützt und hat unzuverlässige Ergebnisse zur Folge. Es ist daher wichtig, dass Sie den Azure Rights Management-Dienst möglichst schnell deaktivieren. 

Wenn Sie Computer von AD RMS in den Azure Rights Management-Dienst verschieben möchten, können Sie den Migrationsprozess starten. Einer der Schritte bei der Migration ist das erneute Aktivieren des Diensts. Diesen Schritt führen Sie jedoch erst aus, nachdem Sie Konfigurationsinformationen von AD RMS in den Azure Rights Management-Dienst exportiert haben. Diese Reihenfolge stellt sicher, dass Dokumente und E-Mails, die durch AD RMS geschützt wurden, immer noch geöffnet werden können.

Der erste Schritt besteht darin, den Azure Rights Management-Dienst zu deaktivieren.

### <a name="step-1-deactivate-azure-rights-management"></a>Schritt 1: Deaktivieren Sie Azure Rights Management
Verwenden Sie eine der folgenden Methoden, um [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] zu deaktivieren.

> [!TIP]
> Sie können auch das Windows PowerShell-Cmdlet [Disable-Aadrm](http://msdn.microsoft.com/library/windowsazure/dn629422.aspx)zum Deaktivieren von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]verwenden.

#### <a name="to-deactivate-rights-management-from-the-office-365-admin-center"></a>So deaktivieren Sie Rights Management über das Office 365 Admin Center

1. Wechseln Sie zur [Rights Management-Seite](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) für Office 365-Administratoren.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie das Konto eines globalen Administrators für Office 365.

2. Klicken Sie auf der Seite **Rights Management** auf **Deaktivieren**.

3.  Wenn die Aufforderung **Möchten Sie Rights Management deaktivieren?** angezeigt wird, klicken Sie auf **Deaktivieren**.

Es sollte jetzt die Meldung **Rights Management ist nicht aktiviert** sowie die Option zum Aktivieren angezeigt werden.

#### <a name="to-deactivate-rights-management-from-the-azure-portal"></a>So deaktivieren Sie Rights Management über das Azure-Portal

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**.
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.
    
    Wenn Sie zuvor noch nie auf das Blatt „Azure Information Protection“ zugegriffen haben, sehen Sie sich die einmaligen [zusätzlichen Schritte](configure-policy.md#to-access-the-azure-information-protection-blade-for-the-first-time) an, um dieses Blatt dem Portal hinzuzufügen.

2. Wählen Sie auf dem ersten **Azure Information Protection**-Blatt **Protection activation** (Schutzaktivierung) aus. 

3.  Wählen Sie auf dem Blatt **„Protection activation“ (Schutzaktivierung) von Azure Information Protection** **Deaktivieren** aus. Klicken Sie zum Bestätigen Ihrer Auswahl auf **Ja**.

Die Informationsleiste zeigt daraufhin **Deactivation finished successfully** (Deaktivierung erfolgreich ausgeführt) an, und **Deaktivieren** wird nun durch **Aktivieren** ersetzt. 

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen Sie mit der Planung der Migration

Informationen hierzu finden Sie im Migrationsleitfaden [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie Azure Information Protection konfigurieren.

Das Blatt **Azure Information Protection – Schutzaktivierung** verfügt über eine Option zum Aktivieren des Diensts für Azure Rights Management (Azure RMS).  

Wenn Sie auch Active Directory Rights Management Services (AD RMS) verwenden, wählen Sie nicht die Option **Aktivieren** aus. Das Aktivieren von Azure Rights Management, wenn Sie auch über AD RS verfügen, ist keine kompatible Kombination. Dieses Szenario wird nicht unterstützt und hat unzuverlässige Ergebnisse zur Folge. Es ist daher wichtig, dass Sie Azure Rights Management zu diesem Zeitpunkt nicht aktivieren.  

Wenn Sie Computer von AD RMS in den Azure Rights Management-Dienst verschieben möchten, können Sie einen Migrationsprozess starten. Einer der Schritte bei der Migration ist das Aktivieren des Diensts. Dies machen Sie jedoch erst, nachdem Sie Informationen zur Konfiguration von AD RMS in den Azure Rights Management-Dienst exportiert haben. Dieser Prozess stellt sicher, dass Dokumente und E-Mails, die durch AD RMS geschützt wurden, immer noch geöffnet werden können. 

Wenn der Azure Rights Management-Dienst nicht aktiviert ist, können Sie Azure Information Protection weiterhin für Bezeichnungen verwenden, die nur für die Klassifizierung gelten. Eine spezielle Standardrichtlinie wurde für Sie erstellt, die den Datenschutz nicht einschließt, und diese Konfigurationsoptionen bleiben nicht verfügbar, bis der Azure Rights Management-Dienst aktiviert ist.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Schritt 1: Konfigurieren Sie Ihre Azure Information Protection-Richtlinie für die Klassifizierung und Bezeichnung – ohne Schutz

Klicken Sie auf dem ersten Blatt **Azure Information Protection** auf **Globale Richtlinie**, um Ihre Standardrichtlinie anzuzeigen und zu konfigurieren, die keine Optionen für den Datenschutz enthält. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen Sie mit der Planung der Migration

Informationen hierzu finden Sie im Migrationsleitfaden [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Schritt 3: Beginnen Sie mit der Konfiguration der Bezeichnungen für den Schutz

Nachdem Sie den Azure Rights Management-Dienst im Rahmen des Migrationsprozesses aktiviert haben, können Sie Bezeichnungen für den Schutz von Daten konfigurieren. Wenn Sie jedoch Benutzer in Batches migrieren, sollten Sie sicherstellen, dass Bezeichnungen, die Schutz anwenden, nur auf die migrierten Benutzer ausgerichtet sind.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

