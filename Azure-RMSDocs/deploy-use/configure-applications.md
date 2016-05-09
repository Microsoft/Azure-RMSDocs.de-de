---
# required metadata

title: Konfigurieren von Anwendungen für Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ea09cbc5-b98b-444e-8b60-5bc3cb199c36

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurieren von Anwendungen für Azure Rights Management
> [!NOTE]
> Diese Informationen sind für IT-Administratoren und Berater bestimmt, die Azure Rights Management bereitgestellt haben. Wenn Sie Hilfe und Informationen zur Verwendung von Rights Management für eine bestimmte Anwendung oder zum Öffnen einer Datei suchen, die mit Rights Management geschützt ist, verwenden Sie die Hilfe und Anleitungen, die zu der Anwendung gehören.
>
> Klicken Sie bei Office-Anwendungen z. B. auf das Hilfesymbol, und geben Sie Suchbegriffe wie **Rights Management** oder **IRM**ein. Informationen zur RMS-Freigabeanwendung für Windows finden Sie unter [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md).

Nachdem Sie Azure Rights Management (Azure RMS) für Ihre Organisation bereitgestellt haben, verwenden Sie die folgenden Informationen, um Anwendungen und Dienste für die Unterstützung von Azure RMS zu konfigurieren. Hierzu gehören unter anderem Office-Anwendungen wie Word 2013 und Word 2010 sowie Exchange Online (Transportregeln, Verhinderung von Datenverlust, Unterbinden der Weiterleitung und Nachrichtenverschlüsselung) und SharePoint Online (geschützte Bibliotheken). Informationen dazu, wie diese Anwendungen und Dienste Rights Management unterstützen, finden Sie unter [Unterstützung von Azure Rights Management durch Anwendungen](../understand-explore/applications-support.md).

> [!IMPORTANT]
> Informationen zu unterstützten Versionen und anderen Anforderungen finden Sie unter [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

-   [Office 365: Konfigurationen für Clients und Onlinedienste](configure-office365.md)

    -   [Exchange Online: IRM-Konfiguration](configure-office365.md#exchange-online-irm-configuration)

    -   [SharePoint Online und OneDrive for Business: IRM-Konfiguration](configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration)

- [Office-Anwendungen: Konfiguration für Clients](configure-office-apps.md)

    -   [Office 2016 und Office 2013](configure-office-apps.md#office-2016-and-office-2013)

    -   [Office 2010](configure-office-apps.md#office-2010)

-   [Rights Management-Freigabeanwendung: Installation und Konfiguration für Clients](configure-sharing-app.md)

    -   [Die RMS-Freigabeanwendung für Windows: Installation und Konfiguration](configure-sharing-app.md#the-rms-sharing-application-for-windows-installation-and-configuration)

    -   [Die RMS-Freigabeanwendung für mobile Plattformen: Installation und Verwaltung](configure-sharing-app.md#the-rms-sharing-application-for-mobile-platforms-installation-and-management)


Informationen zum Konfigurieren von lokalen Servern, z.B. Exchange Server und SharePoint Server, finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](deploy-rms-connector.md).

> [!TIP]
> Allgemeine Beispiele und Screenshots von Anwendungen, die für die Verwendung von Azure RMS konfiguriert sind, finden Sie unter [Azure RMS in Aktion: Was für Administratoren und Benutzer angezeigt wird](../understand-explore/what-admins-users-see.md).


Zusätzlich zu diesen Anwendungen und Diensten gibt es noch andere Anwendungen, die die RMS-APIs unterstützen. Diese Kategorie umfasst Branchenanwendungen, die intern mithilfe des RMS SDK geschrieben wurden, sowie Anwendungen von Softwareherstellern, die mithilfe des RMS SDK geschrieben wurden. Befolgen Sie für diese Anwendungen die Anweisungen, die zusammen mit der jeweiligen Anwendung bereitgestellt werden.

## Nächste Schritte
Nachdem Sie Ihre Anwendungen für die Unterstützung von Azure Rights Management konfiguriert haben, können Sie die [Roadmap für die Bereitstellung von Azure Rights Management](../plan-design/deployment-roadmap.md) verwenden, um herauszufinden, ob Sie vor dem Rollout von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] für Benutzer und Administratoren weitere Konfigurationsschritte ausführen möchten. Wenn dies nicht der Fall ist, helfen Ihnen unter Umständen die folgenden Informationen weiter:

- [Überprüfen von Azure Rights Management](verify.md)

- [Unterstützung von Benutzern beim Schützen von Dateien unter Verwendung von Azure Rights Management](help-users.md)

- [Protokollieren und Analysieren von Azure Rights Management](log-analyze-usage.md)

- [Vorgänge für Ihren Azure Rights Management-Mandantenschlüssel](operations-tenant-key.md)




<!--HONumber=Apr16_HO3-->


