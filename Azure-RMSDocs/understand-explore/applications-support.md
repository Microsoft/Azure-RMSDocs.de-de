---
title: "Unterstützung von Azure Rights Management durch Anwendungen | Azure RMS"
description: "Die folgenden Informationen sollen Ihnen dabei helfen zu verstehen, wie die am häufigsten verwendeten Anwendungen Ihrer Endbenutzer (z.B. Office-Anwendungen, Word, Excel, PowerPoint und Outlook) und Dienste (z.B. Exchange und SharePoint) Microsoft Azure Rights Management verwenden können, um die Daten Ihrer Organisation besser zu schützen."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: df66b53238acecd4173b7d1bc57a611c403ec256


---

# Unterstützung von Azure Rights Management durch Anwendungen

>*Gilt für: Azure Rights Management, Office 365*

Die folgenden Informationen sollen Ihnen dabei helfen zu verstehen, wie die am häufigsten verwendeten Anwendungen Ihrer Endbenutzer (z.B. Office-Anwendungen, Word, Excel, PowerPoint und Outlook) und die Dienste (z.B. Exchange und SharePoint) Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] verwenden können, um die Daten Ihrer Organisation besser zu schützen. 
> [!NOTE]
> Informationen zum Überprüfen der Anwendungen und Versionen, die [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) unterstützt, finden Sie unter [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

In manchen Fällen wird Informationsschutz automatisch gemäß den von Ihnen konfigurierten Richtlinien angewendet. Dies ist beispielsweise bei SharePoint-Bibliotheken, klassifizierten Dateien und Exchange-Transportregeln der Fall. In anderen Fällen müssen Benutzer Informationsschutz selbst aus ihren Anwendungen heraus anwenden, entweder durch Auswählen einer Vorlage oder durch Auswahl bestimmter Optionen. Dies ist beispielsweise der Fall, wenn Benutzer eine Datei per E-Mail teilen oder eine Datei direkt schützen, indem sie den Zugriff oder die Verwendung auf ausgewählte Benutzer bzw. auf Benutzer außerhalb der Organisation einschränken.

Vorlagen erleichtern den Benutzern (und den Administratoren, die Richtlinien konfigurieren) das Anwenden der richtigen Schutzstufe und das Einschränken des Zugriffs auf Personen innerhalb Ihrer Organisation. Zwar verfügt [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] über zwei Standardvoralgen, doch Sie werden vermutlich benutzerdefinierte Vorlagen anlegen wollen, um die Zeiten zu minimieren, in denen einzelne Optionen angegeben werden müssen. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).

In den Fällen, in denen Benutzer Informationsschutz selber anwenden müssen, stellen Sie sicher, dass Sie ihnen Anweisungen und Anleitungen geben, wie und wann dies zu erfolgen hat. Die Anweisungen sollten spezifisch für die Anwendung und Version sein, die verwendet wird, sowie für deren Verwendungsart. Außerdem sollte die Anleitung dafür, wann und wie Informationsschutz angewendet werden sollte, für Ihr Geschäft geeignet sein. Weitere Informationen finden Sie unter [Unterstützung von Benutzern beim Schützen von Dateien unter Verwendung von Azure Rights Management](../deploy-use/help-users.md).

Informationen dazu, wie diese Anwendungen für Azure RMS konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

> [!TIP]
> Beispiele und Screenshots von Anwendungen, für die Azure RMS verwendet wird, finden Sie unter [Azure RMS in Aktion: Was für Administratoren und Benutzer angezeigt wird](what-admins-users-see.md).

Suchdienste können auf unterschiedliche Weise in Rights Management integriert werden. Beispiel: 

- Exchange Online und Exchange Server verwenden die dienstseitige Indizierung, sodass die RMS-geschützten E-Mails eines Benutzers automatisch in ihren Suchergebnissen angezeigt werden. 

- SharePoint Online und SharePoint-Server wenden den RMS-Schutz auf Dateien nur beim Download an. D.h., dass sich diese Dokumentenschutzlösung nicht auf die Indizierung und die Suchergebnisse auf SharePoint auswirkt. Wenn Sie jedoch ein Dokument haben, das Sie in SharePoint speichern möchten, und das nicht in den Suchergebnissen zurückgegeben werden sollte, schützen Sie die Datei mit RMS, bevor sie in SharePoint hochgeladen wird.

- Die Windows-Desktopsuche verwendet einen gemeinsam genutzten Index zwischen verschiedenen Benutzern des Geräts. Damit die Daten in den geschützten Dokumenten sicher bleiben, indiziert sie keine RMS-geschützten Dateien. Das bedeutet, dass Sie sicher sein können, dass Ihre Dateien mit sensiblen Daten nicht in den Suchergebnissen anderer Benutzer angezeigt werden, die sich an Ihrem PC anmelden oder eine Verbindung zu ihm herstellen könnten, obwohl Ihre Suchergebnisse keine Dateien enthalten, die Sie geschützt haben. 



## Nächste Schritte

Informieren Sie sich darüber, wie Azure RMS von den folgenden Komponenten unterstützt wird:

-   [RMS-Freigabeanwendung für Windows und mobile Plattformen](sharing-app-support.md)

-   [Office-Anwendungen und -Dienste](office-apps-services-support.md)

-   [Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden](file-server-support.md)

-   [Sonstige Anwendungen, die die RMS-APIs unterstützen](api-support.md)




<!--HONumber=Aug16_HO4-->


