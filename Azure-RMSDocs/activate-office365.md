---
title: Aktivieren von Azure RMS aus dem Microsoft 365 Admin Center-aip
description: Erfahren Sie, wie Sie den Azure Rights Management-Dienst über das Microsoft 365 Admin Center aktivieren.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/27/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a2b3e1a2-59a0-4191-bf4c-4485ae7a70a9
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 24787eda3b248cab2e6cc3c055611378e39b5c3c
ms.sourcegitcommit: 74b8d03d1ede3da12842b84546417e63897778bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2021
ms.locfileid: "102414785"
---
# <a name="activate-azure-rights-management-protection-from-the-microsoft-365-admin-center"></a>Aktivieren von Azure Rights Management Protection über das Microsoft 365 Admin Center

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

In diesem Artikel wird beschrieben, wie globale Administratoren mit Zugriff auf den Azure Rights Management-Dienst aus dem Microsoft 365 Admin Center Azure-Rights Management aktivieren können.

## <a name="prerequisites"></a>Voraussetzungen

Zum Aktivieren des Azure Rights Management-Diensts benötigen Sie entweder einen [Azure Information Protection Premium-Plan](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) oder einen [Office 365-Plan, der Rights Management umfasst](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf). Beispielsweise verfügt Ihre Organisation über einen Plan für Office 365 E3 oder Office 365 E5. 

Wenn Sie Fragen zu den Abonnementanforderungen haben oder Sie Hilfe bei der Aktivierung des Diensts benötigen, [wenden Sie sich an den Microsoft-Support](information-support.md#to-contact-microsoft-support), oder nutzen Sie die üblichen Supportkanäle.

## <a name="activating-azure-rights-management"></a>Aktivieren von Azure Rights Management

1. Wenn Sie bestätigt haben, dass Ihre Organisation einen Plan hat, der Azure Rights Management beinhaltet, gehen Sie zur Seite [Rights Management](https://account.activedirectory.windowsazure.com/RmsOnline/Manage.aspx) im Microsoft 365 Admin Center.
    
    Wenn Sie aufgefordert werden, sich anzumelden, verwenden Sie ein Konto, das ein globaler Administrator für Microsoft 365 ist.
    
    > [!TIP]
    > Hilfe zum Admin Center finden Sie unter [Informationen zu Microsoft 365 Admin Center](/office365/admin/admin-overview/about-the-admin-center).
    
    Wenn Sie lieber zur **Rights Management** -Seite über das Admin Center wechseln möchten: **Settings**  >  **org Settings**  >  **Services** Registerkarte > **Microsoft Azure Information Protection**  >  **Manage Microsoft Azure Information Protection Settings**

2. Klicken Sie auf der Seite **Rights Management** auf **Aktivieren**.

3. Wenn die Meldung **Möchten Sie Rights Management aktivieren?** angezeigt wird, klicken Sie auf **Aktivieren**.

Es sollten jetzt **Rights Management ist aktiviert** und die Option zum Deaktivieren angezeigt werden.

## <a name="next-steps"></a>Nächste Schritte

Lesen Sie [die Informationen unter Aktivieren des Schutz Dienstanbieter aus Azure Information Protection](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment).

