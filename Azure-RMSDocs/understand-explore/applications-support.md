---
title: "Unterstützung des Azure Rights Management-Diensts durch Anwendungen | Azure Information Protection"
description: "Erfahren Sie, wie die am häufigsten verwendeten Anwendungen (z.B. Office-Anwendungen, Word, Excel, PowerPoint und Outlook) und Dienste (z.B. Exchange und SharePoint) für Endbenutzer den Azure Rights Management-Dienst von Azure Information Protection verwenden können, um die Dokumente und E-Mails Ihrer Organisation zu schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c8ffebad1130c8ba084c0feb83aa3ec54692ad54
ms.openlocfilehash: f3e0be224f2a9e587f5be1bbdbbdb3e81b7a4bca


---

# <a name="how-applications-support-the-azure-rights-management-service"></a>Unterstützung des Azure Rights Management-Diensts durch Anwendungen

>*Gilt für: Azure Information Protection, Office 365*

Erfahren Sie anhand der folgenden Informationen, wie die am häufigsten verwendeten Anwendungen (z.B. Office-Anwendungen, Word, Excel, PowerPoint und Outlook) und Dienste (z.B. Exchange und SharePoint) für Endbenutzer den Azure Rights Management-Dienst von Azure Information Protection verwenden können, um die Dokumente und E-Mails Ihrer Organisation zu schützen. 
> [!NOTE]
> Die Anwendungen und Versionen, die der Azure Rights Management-Dienst unterstützt, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-applications.md).

In einigen Fällen wendet der Azure Rights Management-Dienst den Schutz automatisch gemäß den Richtlinien an, die von Administratoren konfiguriert wurden. Dies ist beispielsweise bei SharePoint-Bibliotheken, klassifizierten Dateien und Exchange-Transportregeln der Fall. In anderen Fällen müssen Endbenutzer den Informationsschutz selbst aus ihren Anwendungen heraus anwenden – durch Auswählen von Vorlagen oder Optionen. Dies ist beispielsweise der Fall, wenn Benutzer eine Datei per E-Mail teilen oder eine Datei direkt schützen, indem sie den Zugriff oder die Verwendung auf ausgewählte Benutzer bzw. auf Benutzer außerhalb der Organisation einschränken.

Vorlagen erleichtern den Benutzern (und den Administratoren, die Richtlinien konfigurieren) das Anwenden der richtigen Schutzstufe und das Einschränken des Zugriffs auf Personen innerhalb Ihrer Organisation. Zwar verfügt der Azure Rights Management-Dienst über zwei Standardvorlagen, doch Sie können benutzerdefinierte Vorlagen erstellen, damit die Benutzer nicht so häufig einzelne Optionen angeben müssen. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).

In den Fällen, in denen Benutzer Informationsschutz selber anwenden müssen, stellen Sie sicher, dass Sie ihnen Anweisungen und Anleitungen geben, wie und wann dies zu erfolgen hat. Die Anweisungen sollten spezifisch für die Anwendung und Version sein, die verwendet wird, sowie für deren Verwendungsart. Außerdem sollte die Anleitung dafür, wann und wie Informationsschutz angewendet werden sollte, für Ihr Geschäft geeignet sein. Weitere Informationen finden Sie unter [Unterstützung von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](../deploy-use/help-users.md).

Informationen dazu, wie diese Anwendungen für den Azure Rights Management-Dienst von Azure Information Protection konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

> [!TIP]
> Beispiele und Screenshots von Anwendungen, die den Azure Rights Management-Diensts verwenden, finden Sie unter [Azure RMS in Aktion: Was für Administratoren und Benutzer angezeigt wird](what-admins-users-see.md).

Suchdienste können auf unterschiedliche Weise in Rights Management integriert werden. Beispiel: 

- Exchange Online und Exchange Server verwenden die dienstseitige Indizierung, sodass die RMS-geschützten E-Mails eines Benutzers automatisch in ihren Suchergebnissen angezeigt werden. 

- SharePoint Online und SharePoint Server wenden den Rights Management-Schutz auf Dateien nur beim Download an. Das heißt, dass sich diese Dokumentenschutzlösung nicht auf die Indizierung und die Suchergebnisse von SharePoint auswirkt. Wenn Sie jedoch ein Dokument haben, das Sie in SharePoint speichern möchten, und das nicht in den Suchergebnissen zurückgegeben werden sollte, schützen Sie die Datei mit RMS, bevor sie in SharePoint hochgeladen wird.

- Die Windows-Desktopsuche verwendet einen gemeinsam genutzten Index zwischen verschiedenen Benutzern des Geräts. Damit die Daten in den geschützten Dokumenten sicher bleiben, indiziert sie keine RMS-geschützten Dateien. Das bedeutet, dass Sie sicher sein können, dass Ihre Dateien mit sensiblen Daten nicht in den Suchergebnissen anderer Benutzer angezeigt werden, die sich an Ihrem PC anmelden oder eine Verbindung zu ihm herstellen könnten, obwohl Ihre Suchergebnisse keine Dateien enthalten, die Sie geschützt haben. 



## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie der Azure Rights Management-Dienst von den folgenden Komponenten unterstützt wird:

-   [RMS-Freigabeanwendung für Windows und mobile Plattformen](sharing-app-support.md)

-   [Office-Anwendungen und -Dienste](office-apps-services-support.md)

-   [Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI) verwenden](file-server-support.md)

-   [Sonstige Anwendungen, die die RMS-APIs unterstützen](api-support.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


