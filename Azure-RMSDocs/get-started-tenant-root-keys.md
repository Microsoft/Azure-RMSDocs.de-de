---
title: Beginnen Sie mit der Verwendung und Verwaltung Ihres Mandanten Stamm Schlüssels.
description: Informieren Sie sich über die nächsten Schritte nach dem Planen der Stamm Schlüsselverwaltung für Mandanten, einschließlich des von Microsoft und Byok-Schutz generierten Standard Schlüssels.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 9756710e29c82ef953633697cb989942d1844496
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97382240"
---
# <a name="getting-started-with-tenant-root-keys"></a>Ersten Schritte mit Mandanten Stamm Schlüsseln

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Nachdem [Sie Ihren Mandanten Schlüssel nach Bedarf geplant, erstellt und konfiguriert](plan-implement-tenant-key.md) haben, fahren Sie mit den folgenden Schritten fort:

- [Beginnen Sie mit der Verwendung Ihres Mandanten Schlüssels](#start-using-your-tenant-key)
- [Verwendungs Protokollierung beachten](#consider-usage-logging)

Weitere Informationen zu den Lebenszyklus Vorgängen, die für Ihren Mandanten Schlüssel unterstützt werden, finden [Sie unter Vorgänge für Ihren Azure Information Protection Mandanten Schlüssel](./operations-tenant-key.md).

Wenn Ihre Organisation lokalen Schutz für streng sensible Inhalte erfordert, konfigurieren Sie den [DKE-Schutz](plan-implement-tenant-key.md#double-key-encryption-dke) (nur Unified-Bezeichnungs Client).

Wenn Sie lokalen Schutz benötigen und den klassischen Client verwenden, sollten Sie stattdessen den [Hyok-Schutz](configure-adrms-restrictions.md) konfigurieren.
 

## <a name="start-using-your-tenant-key"></a>Beginnen Sie mit der Verwendung Ihres Mandanten Schlüssels

Aktivieren Sie den Rights Management Dienst, wenn er noch nicht aktiviert ist, damit Ihre Organisation mit der Verwendung von Azure Information Protection beginnen kann. Benutzer beginnen sofort mit der Verwendung Ihres Mandanten Schlüssels.

Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](./activate-service.md).

> [!NOTE]
> Wenn Sie sich für die Verwaltung Ihres eigenen Mandanten Schlüssels entschieden haben, nachdem der Rights Management-Dienst aktiviert wurde, werden die Benutzer im Laufe von einigen Wochen allmählich vom alten Schlüssel auf den neuen Schlüssel umgestellt.
>
>Während dieses Übergangs sind Dokumente und Dateien, die mit dem alten Mandanten Schlüssel geschützt wurden, autorisierten Benutzern weiterhin zugänglich.

## <a name="consider-usage-logging"></a>Verwendungs Protokollierung beachten

Die Verwendungs Protokollierung protokolliert jede Transaktion, die der Azure Rights Management-Dienst ausführt.

Abhängig von Ihrer Schlüssel Verwaltungsmethode können die Protokollierungs Informationen Details über ihren Mandanten Schlüssel enthalten. Die folgende Abbildung zeigt ein Beispiel aus einer in Excel angezeigten Protokolldatei, in der die Anforderungs Typen **keyvaultdecryptrequest** und **keyvaultsignrequest** anzeigen, dass der Mandanten Schlüssel verwendet wird.
    
![Protokolldatei in Excel, in der der Mandantenschlüssel verwendet wird.](./media/RMS_Logging.png)
    
Weitere Informationen zur Verwendungs Protokollierung finden Sie unter [protokollieren und Analysieren der Schutz Verwendung von Azure Information Protection](./log-analyze-usage.md).
