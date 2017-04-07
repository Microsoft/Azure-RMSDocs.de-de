---
title: "Veranlassen, dass Benutzer sich für RMS for Individuals registrieren – AIP"
description: "Wie erfahren Sie als Administrator, ob Ihre Benutzer sich für RMS for Individuals registriert haben? Sie können beliebige Methoden oder eine Kombination aus den Methoden in diesem Artikel verwenden."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 10dfa64146587fe816df6a555e0a3b43c1290c45
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-find-out-if-your-users-have-signed-up-for-rms-for-individuals"></a>So ermitteln Sie, ob Ihre Benutzer sich für RMS for Individuals registriert haben

>*Gilt für: Azure Information Protection*

Wie erfahren Sie als Administrator, ob Ihre Benutzer sich für RMS for Individuals registriert haben? Sie können eine dieser Methoden bzw. eine beliebige Kombination der folgenden Methoden verwenden:

-   Fragen Sie Benutzer, wie sie sehr vertrauliche Dateien schützen, insbesondere bei der Zusammenarbeit mit anderen Personen außerhalb der Organisation.

-   Wenn Sie ein Azure-Abonnement für Ihre Organisation besitzen, verwenden Sie das Cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx), um festzustellen, ob einem der Benutzer die Lizenz **RIGHTSMANAGEMENT_ADHOC** zugeordnet ist. Die Lizenz stammt aus dem „RMS for Individuals“-Abonnement, das der Organisation gewährt wurde, mit einem Pool aktiver Einheiten, die Benutzern zur Verfügung stehen, um den Self-Service-Anmeldevorgang zu verwenden.

-   Verwenden Sie eine Systemvewaltungslösung wie System Center Configuration Manager, um installierte und in Verwendung befindliche Software zu inventarisieren. Suchen Sie beispielsweise nach der Datei **MSIP.App.exe**, die vom Azure Information Protection-Client verwendet wird, und nach der Datei **ipviewer.exe** für die Rights Management-Freigabeanwendung. Sie können diesen Client und die Anwendung kostenlos herunterladen und installieren, um andere Eigenschaften zu identifizieren, die Sie dann für die Softwareinventur verwenden.

-   Achten Sie auf Dateierweiterungen, die vom Azure Information Protection-Client oder der Rights Management-Freigabeanwendung erstellt werden. Die Dateinamenerweiterungen PFILE und PPDF sind die offensichtlichsten Beispiele, doch es gibt noch andere Dateien, die ihre Dateinamenerweiterung ändern, wenn sie vom Rights Management-Dienst nativ geschützt sind. Weitere Informationen finden Sie im Administratorhandbuch zum Azure Information Protection-Client unter [Für den Schutz unterstützte Dateitypen](../rms-client/client-admin-guide-file-types.md#file-types-supported-for-protection).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]