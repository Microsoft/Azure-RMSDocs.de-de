---
title: Unterstützung von Azure Rights Management durch Apps von AIP
description: Erfahren Sie, wie die am häufigsten verwendeten Anwendungen (z.B. Office-Anwendungen, Word, Excel, PowerPoint und Outlook) und Dienste (z.B. Exchange und SharePoint) für Endbenutzer den Azure Rights Management-Dienst von Azure Information Protection verwenden können, um die Dokumente und E-Mails Ihrer Organisation zu schützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/31/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 2cdc7bde-4044-4021-b887-11476f99afd9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f529b761ef757612b621e948a49805448f9414ba
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39474667"
---
# <a name="how-applications-support-the-azure-rights-management-service"></a>Unterstützung des Azure Rights Management-Diensts durch Anwendungen

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Erfahren Sie anhand der folgenden Informationen, wie die am häufigsten verwendeten Anwendungen und Dienste für Endbenutzer den Azure Rights Management-Dienst von Azure Information Protection verwenden können, um die Dokumente und E-Mails Ihrer Organisation zu schützen. Diese Anwendungen sind unter anderem Word, Excel, PowerPoint und Outlook. Die Dienste sind unter anderem Exchange und SharePoint.

> [!NOTE]
> Die Anwendungen und Versionen, die der Azure Rights Management-Dienst unterstützt, finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](./requirements-applications.md).

In einigen Fällen wendet der Azure Rights Management-Dienst den Schutz automatisch gemäß den Richtlinien an, die von Administratoren konfiguriert wurden. Dies ist beispielsweise bei SharePoint-Bibliotheken und Exchange-Transportregeln der Fall. In anderen Fällen müssen Endbenutzer den Schutz selbst von ihren Anwendungen anwenden. Beispielsweise wählen Benutzer eine Klassifizierungsbezeichnung, die zum Anwenden des Schutzes konfiguriert ist, oder sie wählen eine Vorlage oder bestimmte Optionen aus. Von Benutzern angewendeter Schutz ist typisch, wenn Benutzer eine freizugebende Datei schützen und sie auch den Zugriff oder die Verwendung auf ausgewählte Benutzer oder auf Benutzer außerhalb der Organisation einschränken.

Vorlagen erleichtern den Benutzern (und den Administratoren, die Richtlinien konfigurieren) das Anwenden der richtigen Schutzstufe und das Einschränken des Zugriffs auf Personen innerhalb Ihrer Organisation. Zwar verfügt der Azure Rights Management-Dienst über zwei Standardvorlagen, doch Sie können benutzerdefinierte Vorlagen erstellen, damit die Benutzer und Administratoren nicht so häufig einzelne Optionen angeben müssen. Weitere Informationen zu Vorlagen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](./deploy-use/configure-policy-templates.md).

In den Fällen, in denen Benutzer den Schutz selber anwenden müssen, stellen Sie sicher, dass Sie ihnen Anweisungen und Anleitungen geben, wie und wann dies zu erfolgen hat. Geben Sie die Anweisungen für die Anwendung und Versionen speziell an, die sie verwenden sollen sowie wie diese verwendet werden sollen. Stellen Sie auch Hilfestellung bereit, wann und wie Benutzer den Schutz, der für Ihr Unternehmen geeignet ist, anwenden müssen. Weitere Informationen finden Sie unter [Unterstützung von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](./deploy-use/help-users.md).

Informationen dazu, wie diese Anwendungen für den Azure Rights Management-Dienst von Azure Information Protection konfiguriert werden, finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](./deploy-use/configure-applications.md).

Suchdienste können auf unterschiedliche Weise in Rights Management integriert werden. Beispiel: 

- Exchange Online und Exchange Server verwenden die dienstseitige Indizierung, sodass die geschützten E-Mails eines Benutzers automatisch in ihren Suchergebnissen angezeigt werden. 

- SharePoint Online und SharePoint-Server wenden Rights Management-Schutz auf Dateien nur beim Download an. Diese Implementierung bedeutet, dass die Indizierung und Suchergebnisse auf SharePoint von dieser Lösung zum Schutz von Dokumenten nicht betroffen sind. Wenn Sie jedoch ein Dokument haben, das Sie in SharePoint speichern möchten, und dieses Dokument nicht in den Suchergebnissen zurückgegeben werden sollte, schützen Sie es, bevor es in SharePoint hochgeladen wird.

- Die Windows-Desktopsuche verwendet einen gemeinsam genutzten Index zwischen verschiedenen Benutzern des Geräts. Damit die Daten in den geschützten Dokumenten sicher bleiben, indiziert sie keine geschützten Dateien. Das bedeutet, dass Sie sicher sein können, dass Ihre Dateien mit sensiblen Daten nicht in den Suchergebnissen anderer Benutzer angezeigt werden, die sich an Ihrem PC anmelden oder eine Verbindung zu Ihrem PC herstellen könnten, obwohl Ihre Suchergebnisse keine Dateien enthalten, die Sie geschützt haben. 

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie, wie der Azure Rights Management-Dienst von den folgenden Anwendungen und Diensten unterstützt wird:

-   [RMS-Freigabeanwendung für Windows und mobile Plattformen](sharing-app-support.md)

-   [Office-Anwendungen und -Dienste](office-apps-services-support.md)

-   [Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI) verwenden](file-server-support.md)

-   [Sonstige Anwendungen, die die RMS-APIs unterstützen](api-support.md)

