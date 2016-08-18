---
title: "So ermitteln Sie, ob Ihre Benutzer sich für RMS for Individuals registriert haben | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f355da35dff62ecee111737eb1793ae286dc93e
ms.openlocfilehash: e577366be26f7296079751e72fb6531b9e28c504


---


# So ermitteln Sie, ob Ihre Benutzer sich für RMS for Individuals registriert haben

*Gilt für: Azure Rights Management*

Wie erfahren Sie als Administrator, ob Ihre Benutzer sich für RMS für Einzelpersonen registriert haben? Sie können eine bzw. eine beliebige Kombination der folgenden Methoden verwenden:

-   Fragen Sie Benutzer, wie sie sehr vertrauliche Dateien schützen, insbesondere bei der Zusammenarbeit mit anderen Personen außerhalb der Organisation.

-   Wenn Sie ein Azure-Abonnement für Ihre Organisation besitzen, verwenden Sie das Cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx), um festzustellen, ob **RIGHTSMANAGEMENT_ADHOC** als eines der Abonnements zurückgegeben wird. Ist dies der Fall, ist dies das "RMS für Einzelpersonen"-Abonnement, das der Organisation gewährt wurde, mit einem Pool aktiver Einheiten, die Benutzern zur Verfügung stehen, um den Self-Service-Anmeldevorgang zu verwenden.

-   Verwenden Sie eine Systemvewaltungslösung wie System Center Configuration Manager, um installierte und in Verwendung befindliche Software zu inventarisieren. Die Rights Management-Freigabeanwendung mithilfe des **ipviewer.exe** -Programms ausgeführt, und Sie können [die Anwendung kostenlos herunterladen und installieren die Anwendung](http://go.microsoft.com/fwlink/?LinkId=303970) , um andere Eigenschaften dieser Anwendung zu identifizieren, die Sie dann für Ihren Softwarebestand nutzen.

-   Achten Sie auf Dateinamenerweiterungen, die von der Rights Management-Freigabeanwendung erstellt werden. Die Dateinamenerweiterungen „PFILE“ und „PPDF“ sind die offensichtlichsten Beispiele, doch es gibt noch andere Dateien, die ihre Dateinamenerweiterung ändern, wenn sie durch Rights Management systemeigen geschützt sind. Weitere Informationen finden Sie im Abschnitt [Unterstützte Dateitypen und Dateinamenerweiterungen](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) im [Rights Management-Freigabeanwendung – Administratorhandbuch](http://technet.microsoft.com/library/dn339003.aspx).




<!--HONumber=Jul16_HO3-->


