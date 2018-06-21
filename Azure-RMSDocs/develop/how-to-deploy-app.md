---
title: So stellen sie eine App bereit – AIP
description: Dieser Artikel beschreibt den Prozess der Bereitstellung einer Dienstanwendung in einen anderen Mandanten als jenen, mit dem sie ursprünglich entwickelt wurde.
keywords: ''
author: kkanakas
ms.author: kartikk
manager: mbaldwin
ms.date: 02/27/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 34dc6d6f-cfe4-4848-9b11-8d90c4b38ef7
audience: developer
ms.reviewer: kartikk
ms.suite: ems
ms.openlocfilehash: 3b7ff758abeb3f1ddc1ae82349233e437d05dacc
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
ms.locfileid: "20232835"
---
# <a name="deploying-a-service-application-into-a-different-tenant"></a>Bereitstellen einer Dienstanwendung in einen anderen Mandanten

Dieser Artikel beschreibt den Prozess der Bereitstellung einer Dienstanwendung. In diesem Szenario verändern wir die Anwendung im Hinblick darauf, dass sie nicht länger mit ihrem ursprünglichen Entwicklungs-AD-Mandanten registriert ist, sondern nun mit einem anderen Produktions-AD-Mandanten des Unternehmens.

> [!Note]
> Dieses Szenario ist nur relevant, wenn die Dienstanwendung die Authentifizierung mit einem symmetrischen Schlüssel verwendet.

## <a name="scenario"></a>Szenario
Das Unternehmen *CoolApp* hat eine Dienstanwendung mithilfe von Azure Information Protection (AIP) entwickelt, die Dokumente verschlüsselt, bezeichnet und schützt, wenn Benutzer aus einer Unternehmensanwendung exportieren, z.B. aus Dynamics, SAP oder Salesforce. Für dieses Szenario kauft die Firma *ABC* die neue Anwendung von *CoolApp*, daher muss das *CoolApp*-Team seine Lösung in der *ABC*-Umgebung bereitstellen. 

![Beispielfluss zur Erstellung eines symmetrischen Schlüssels in einem anderen Mandanten](../media/develop/service-app-provision.jpg)

## <a name="flow-1-coolapp-provides-a-ui-dialog-to-abc-to-implement-the-deployment"></a>Fluss 1: *CoolApp* stellt ein Benutzeroberflächendialogfeld für *ABC* zum Implementieren der Bereitstellung bereit.

Sobald *ABC* die Lösung von *CoolApp* kauft, muss der IT-Administrator bei *ABC* den *CoolApp*-Dienstprinzipal erstellen und die Anwendung im Azure AD-Mandanten von *ABC* registrieren. 

Die Schritte dafür stehen Ihnen im Abschnitt **Erstellen eines Dienstprinzipals** unter [Entwickeln Ihrer Anwendung](developing-your-application.md) zur Verfügung.

![Beispiel der Benutzeroberfläche für den IT-Administrator für die Eingabe für Ihre Anwendung](../media/develop/how-to-deploy-app-UI.png)

> [!Note]
> Zum Erstellen eines Dienstprinzipals in einem Mandanten müssen Sie über Mandantenadministratorrechte verfügen.

Der IT-Administrator von *ABC* startet daraufhin die *CoolApp*-Anwendung als Dienst in ihrer Umgebung und bettet die Details für die *CoolApp*-Anwendung ein, damit diese funktioniert, z.B. Anwendungs-ID, Mandanten-ID und der symmetrische Schlüssel.

Wenn dem IT-Administrator von *ABC* kein Benutzeroberflächendialogfeld für die Dienstprizipalinformation bereitgestellt wird, dann ist **Fluss 2** die Methode, die ausgewählt werden sollte.

## <a name="flow-2-abc-it-administrator-provides-the-key-to-the-coolapp-team"></a>Fluss 2: Der *ABC*-IT-Administrator stellt den Schlüssel für das *CoolApp*-Team bereit

Sobald der IT-Administrator von *ABC* den Dienstprinzipal erstellt, so wie in **Bild 1** gezeigt, stellt *ABC* die Informationen für das *CoolApp*-Team bereit. Das *CoolApp*-Team bettet dann weiterhin die Informationen in die *CoolApp*-Anwendung ein, um sie im *ABC*-Mandanten zu verwenden.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]