---
title: "Vorbereiten der Umgebung für Azure RMS und AD RMS"
description: Hier finden Sie eine Anleitung, falls Sie Azure Rights Management und AD RMS bereitgestellt haben.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 11ffa730-c5dc-4b6b-9c1e-c58eff8aafc2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 6d7a1d2ed61e1d12d6ca50db50c5b516e6e4f54e
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="preparing-the-environment-for-azure-rights-management-when-you-also-have-active-directory-rights-management-services-ad-rms"></a>Vorbereiten der Umgebung für Azure Rights Management bei gleichzeitiger Verwendung von Active Directory Rights Management Services (AD RMS)

>*Gilt für: Azure Information Protection, Office 365*

Hier finden Sie wichtige Hinweise, wenn Sie bereits Active Directory Rights Management Services (AD RMS) verwenden und das folgende Szenario vorliegt:

## <a name="you-see-an-option-to-activate-protection-when-you-configure-azure-information-protection"></a>Eine Option zum Aktivieren des Schutzes wird angezeigt, wenn Sie Azure Information Protection konfigurieren.

Auf dem Blatt **Azure Information Protection - Protection activation** (Azure Information Protection – Schutzaktivierung) wird eine Option zum Aktivieren des Azure Rights Management-Diensts (Azure RMS) angezeigt. 

Wenn Sie außerdem Active Directory Rights Management Services (AD RMS) verwenden, wählen Sie nicht die Option **Aktivieren**. Azure Rights Management kann nicht aktiviert werden, wenn Sie AD RS nutzen. Dieses Szenario wird nicht unterstützt und führt zu unzuverlässigen Ergebnissen. Daher ist es wichtig, Azure Rights Management zu diesem Zeitpunkt nicht zu aktivieren. 

Wenn Sie Computer von AD RMS zum Azure Rights Management-Dienst migrieren möchten, können Sie einen Migrationsprozess starten. Einer der Schritte bei der Migration besteht im Aktivieren des Diensts. Sie führen diesen Schritt jedoch erst aus, nachdem Sie Konfigurationsinformationen aus AD RMS in den Azure Rights Management-Dienst exportiert haben. Durch diese Vorgehensweise wird sichergestellt, dass durch AD RMS geschützte Dokumente und E-Mails weiterhin geöffnet werden können.

Wenn der Azure Rights Management-Dienst nicht aktiviert ist, können Sie dennoch Azure Information Protection für Bezeichnungen verwenden, die nur für die Klassifizierung gelten. Eine spezielle Standardrichtlinie wird für Sie erstellt, die keinen Schutz von Daten beinhaltet, und diese Konfigurationsoptionen sind bis zur Aktivierung des Azure Rights Management-Diensts nicht verfügbar.

### <a name="step-1-configure-your-azure-information-protection-policy-for-classification-and-labeling---without-protection"></a>Schritt 1: Konfigurieren der Azure Information Protection-Richtlinie für die Klassifizierung und Bezeichnung – ohne Schutz

Klicken Sie auf dem Startblatt **Azure Information Protection** auf **Globale Richtlinie**, um Ihre Standardrichtlinie anzuzeigen und zu konfigurieren, die keine Optionen für den Schutz von Daten beinhaltet. Weitere Informationen finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](configure-policy.md).

### <a name="step-2-start-planning-for-migration"></a>Schritt 2: Beginnen mit der Planung für die Migration

Befolgen Sie die Anweisungen zur Migration unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

### <a name="step-3-start-to-configure-labels-for-protection"></a>Schritt 3: Beginnen mit dem Konfigurieren von Bezeichnungen für den Schutz

Nachdem Sie den Azure Rights Management-Dienst im Rahmen der Migration aktiviert haben, können Sie Bezeichnungen für den Schutz von Daten konfigurieren. Beim Migrieren von Benutzern in Batches müssen Sie jedoch sicherstellen, dass der [Geltungsbereich](configure-policy-scope.md) von Bezeichnungen zum Anwenden von Schutz auf die migrierten Benutzer begrenzt ist.


[!INCLUDE[Commenting house rules](../includes/houserules.md)]


