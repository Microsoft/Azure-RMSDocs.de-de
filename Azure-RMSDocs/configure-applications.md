---
title: Konfigurieren von Anwendungen für Azure Rights Management – AIP
description: Hier finden Sie Anleitung für Administratoren zum Konfigurieren von Anwendungen und Diensten für die Unterstützung des Azure Rights Management-Schutzdiensts für Azure Information Protection.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.subservice: azurerms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 1f8100e22f1608ebbd678ec5f97f77b4abd53ff0
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383651"
---
# <a name="configuring-applications-for-azure-rights-management"></a>Konfigurieren von Anwendungen für Azure Rights Management

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> [!NOTE]
> Diese Informationen sind für IT-Administratoren und Berater bestimmt, die Azure Information Protection bereitgestellt haben. Wenn Sie Hilfe und Informationen zur Verwendung der Rights Management-Funktionen für eine bestimmte Anwendung oder zum Öffnen einer Datei suchen, die mit Rights Management geschützt ist, verwenden Sie die Hilfe und Anleitungen, die zu der Anwendung gehören.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM** ein. Informationen zum Azure Information Protection-Client für Windows finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/clientv2-user-guide.md).

Nachdem Sie Azure Information Protection für Ihre Organisation bereitgestellt haben, verwenden Sie die folgenden Informationen zum Konfigurieren von Anwendungen, des Azure Information Protection Clients und der Dienste, wie z. b.:

- **Office-Anwendungen**, wie z. b. Word 2019, Word 2016 und Word 2013. 
- **Dienste** wie Exchange Online (Transport Regeln, Verhinderung von Datenverlust, nicht weiterleiten und Nachrichten Verschlüsselung) und Microsoft SharePoint (geschützte Bibliotheken). 

Informationen dazu, wie diese Anwendungen und Dienste den Datenschutzdienst von Azure Information Protection unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

> [!IMPORTANT]
> Informationen zu unterstützten Versionen und anderen Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

-   [Office 365: Konfiguration für Onlinedienste](configure-office365.md)

    -   [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration)

    -   [SharePoint in Microsoft 365 und onedrive: unm-Konfiguration](configure-office365.md#sharepoint-in-microsoft-365-and-onedrive-irm-configuration)

- [Office-Anwendungen: Konfiguration für Clients](configure-office-apps.md)

    -   [Office 365-Apps, Office 2019, Office 2016 und Office 2013](configure-office-apps.md#office365-apps-office-2019-office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office2010)

-   [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md)

Informationen zum Konfigurieren von lokalen Servern, z. b. Exchange Server und SharePoint Server, finden Sie unter Bereitstellen [des Azure Rights Management-Verbindungs](deploy-rms-connector.md)Punkts.

Zusätzlich zu diesen Anwendungen und Diensten gibt es noch andere Anwendungen, die die Rights Management-APIs unterstützen. Diese Kategorie umfasst Branchenanwendungen, die intern mithilfe des Rights Management-SDK geschrieben wurden, sowie Anwendungen von Softwareherstellern, die mithilfe des Rights Management-SDK geschrieben wurden. Befolgen Sie für diese Anwendungen die Anweisungen, die zusammen mit der jeweiligen Anwendung bereitgestellt werden.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Ihre Anwendungen für die Unterstützung des Azure-Rights Management Dienstanbieter konfiguriert haben, verwenden Sie die [AIP-Bereitstellungs Roadmap für Klassifizierung, Bezeichnung und Schutz](deployment-roadmap-classify-label-protect.md) , um zu überprüfen, ob Sie vor dem Rollout Azure Information Protection für Benutzer und Administratoren weitere Konfigurationsschritte ausführen möchten. 

Wenn dies nicht der Fall ist, helfen Ihnen unter Umständen die folgenden Informationen weiter:

- [Überprüfen des Azure Rights Management-Diensts](verify.md)

- [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](help-users.md)

- [Protokollieren und Analysieren des Azure Rights Management-Diensts](log-analyze-usage.md)

- [Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel](operations-tenant-key.md)


