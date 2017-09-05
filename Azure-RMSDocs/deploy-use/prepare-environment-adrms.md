---
title: "Vorbereiten der Umgebung für Azure RMS und AD RMS"
description: Leitfaden, wenn Sie Azure Rights Management mit AD RMS bereitgestellt haben
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 2e8f6596216e06e2af773c0a19a2c5eaafd096b8
ms.sourcegitcommit: 13e95906c24687eb281d43b403dcd080912c54ec
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/30/2017
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Vorbereiten der Umgebung für Azure Rights Management, wenn Sie auch über Active Directory-Rechteverwaltungsdienste (AD RMS) verfügen

>*Gilt für: Azure Information Protection, Office 365*

Wichtiger Leitfaden, wenn Sie bereits Active Directory Rights Management Services (AD RMS) nutzen und das folgende Szenario vorliegt:

## <a name="you-see-an-option-to-activate-azure-rms-when-you-configure-azure-information-protection"></a>Sie sehen eine Option zum Aktivieren von Azure RMS, wenn Sie Azure Information Protection konfigurieren

Das Blatt **Azure Information Protection – Einstellungen für RMS** verfügt über eine Option zum Aktivieren des Diensts für Azure Rights Management (Azure RMS). 

Wenn Sie auch Active Directory Rights Management Services (AD RMS) verwenden, wählen Sie nicht die Option **Aktivieren** aus. Das Aktivieren von Azure Rights Management, wenn Sie auch über AD RS verfügen, ist keine kompatible Kombination. Dieses Szenario wird nicht unterstützt und hat unzuverlässige Ergebnisse zur Folge. Es ist daher wichtig, dass Sie Azure Rights Management zu diesem Zeitpunkt nicht aktivieren. 

Wenn Sie Computer von AD RMS in den Azure Rights Management-Dienst verschieben möchten, können Sie einen Migrationsprozess starten. Einer der Schritte bei der Migration ist das Aktivieren des Diensts. Dies machen Sie jedoch erst, nachdem Sie Informationen zur Konfiguration von AD RMS in den Azure Rights Management-Dienst exportiert haben. Dieser Prozess stellt sicher, dass Dokumente und E-Mails, die durch AD RMS geschützt wurden, immer noch geöffnet werden können.

Wenn der Azure Rights Management-Dienst nicht aktiviert ist, können Sie Azure Information Protection weiterhin für Bezeichnungen verwenden, die nur für die Klassifizierung gelten. Eine spezielle Standardrichtlinie wurde für Sie erstellt, die den Datenschutz nicht einschließt, und diese Konfigurationsoptionen bleiben nicht verfügbar, bis der Azure Rights Management-Dienst aktiviert ist.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Schritt 1: Konfigurieren Sie Ihre Azure Information Protection-Richtlinie für die Klassifizierung und Bezeichnung – ohne Schutz

Klicken Sie auf dem ersten Blatt **Azure Information Protection** auf **Globale Richtlinie**, um Ihre Standardrichtlinie anzuzeigen und zu konfigurieren, die keine Optionen für den Datenschutz enthält. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen Sie mit der Planung der Migration

Folgen Sie dem Migrationsleitfaden: [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Schritt 3: Beginnen Sie mit der Konfiguration der Bezeichnungen für den Schutz

Nachdem Sie den Azure Rights Management-Dienst im Rahmen des Migrationsprozesses aktiviert haben, können Sie Bezeichnungen für den Schutz von Daten konfigurieren. Wenn Sie jedoch Benutzer in Batches migrieren, stellen Sie sicher, dass Bezeichnungen, die Schutz anwenden, nur auf die migrierten Benutzer [ausgerichtet](configure-policy-scope.md) sind.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


