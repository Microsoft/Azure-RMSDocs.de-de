---
title: Konfigurieren von Anwendungen für Azure Rights Management – AIP
description: Hier finden Sie Anleitung für Administratoren zum Konfigurieren von Anwendungen und Diensten für die Unterstützung des Azure Rights Management-Schutzdiensts für Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/01/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 445f68f102764444551b13b49ea327a0b58046e4
ms.sourcegitcommit: f9077101a974459a4252e763b5fafe51ff15a16f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64767779"
---
# <a name="configuring-applications-for-azure-rights-management"></a>Konfigurieren von Anwendungen für Azure Rights Management

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

> [!NOTE]
> Diese Informationen sind für IT-Administratoren und Berater bestimmt, die Azure Information Protection bereitgestellt haben. Wenn Sie Hilfe und Informationen zur Verwendung der Rights Management-Funktionen für eine bestimmte Anwendung oder zum Öffnen einer Datei suchen, die mit Rights Management geschützt ist, verwenden Sie die Hilfe und Anleitungen, die zu der Anwendung gehören.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM**ein. Informationen zum Azure Information Protection-Client für Windows finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/client-user-guide.md).

Nachdem Sie Azure Information Protection für Ihre Organisation bereitgestellt haben, verwenden Sie die folgenden Informationen, um Anwendungen, den Azure Information Protection-Client und Dienste zu konfigurieren. Beispielsweise Office-Anwendungen wie Word 2016, Word 2013 und Word 2010. Auch Dienste wie Exchange Online (Transportregeln, Verhinderung von Datenverlust, Unterbinden der Weiterleitung und Nachrichtenverschlüsselung) und SharePoint Online (geschützte Bibliotheken). Informationen dazu, wie diese Anwendungen und Dienste den Datenschutzdienst von Azure Information Protection unterstützen, finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

> [!IMPORTANT]
> Informationen zu unterstützten Versionen und anderen Anforderungen finden Sie unter [Voraussetzungen für Azure Rights Management](requirements.md).

-   [Office 365: Konfigurationen für Clients und Onlinedienste](configure-office365.md)

    -   [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration)

    -   [SharePoint Online und OneDrive for Business: IRM-Konfiguration](configure-office365.md#sharepointonline-and-onedrive-for-business-irm-configuration)

- [Office-Anwendungen: Konfiguration für Clients](configure-office-apps.md)

    -   [Office 2016 und Office 2013](configure-office-apps.md#office2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office2010)

-   [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md)

Informationen zum Konfigurieren von lokalen Servern, z.B. Exchange Server und SharePoint Server, finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

Zusätzlich zu diesen Anwendungen und Diensten gibt es noch andere Anwendungen, die die Rights Management-APIs unterstützen. Diese Kategorie umfasst Branchenanwendungen, die intern mithilfe des Rights Management-SDK geschrieben wurden, sowie Anwendungen von Softwareherstellern, die mithilfe des Rights Management-SDK geschrieben wurden. Befolgen Sie für diese Anwendungen die Anweisungen, die zusammen mit der jeweiligen Anwendung bereitgestellt werden.

## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie Ihre Anwendungen für die Unterstützung des Azure Rights Management-Diensts konfiguriert haben, können Sie die [Roadmap für die Bereitstellung von Azure Information Protection](deployment-roadmap.md) verwenden, um herauszufinden, ob Sie vor dem Rollout von Azure Information Protection für Benutzer und Administratoren weitere Konfigurationsschritte ausführen möchten. Wenn dies nicht der Fall ist, helfen Ihnen unter Umständen die folgenden Informationen weiter:

- [Überprüfen des Azure Rights Management-Diensts](verify.md)

- [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](help-users.md)

- [Protokollieren und Analysieren des Azure Rights Management-Diensts](log-analyze-usage.md)

- [Vorgänge für Ihren Azure Information Protection-Mandantenschlüssel](operations-tenant-key.md)


