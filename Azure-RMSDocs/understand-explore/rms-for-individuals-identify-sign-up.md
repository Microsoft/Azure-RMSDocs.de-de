---
title: "So ermitteln Sie, ob Ihre Benutzer sich für RMS for Individuals registriert haben | Azure RMS"
description: "Als Administrator können Sie jede der in diesem Artikel beschriebenen Methoden (oder auch eine Kombination mehrerer Methoden) verwenden, um festzustellen, ob Ihre Benutzer sich für RMS for Individuals registriert haben."
author: cabailey
manager: mbaldwin
ms.date: 09/01/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: a36c3d99-a794-4f7a-aafb-64a950f1fcf9
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 79d098e47cdfe608bc62ed385a5c8236fb7c6d3c
ms.openlocfilehash: 6a8a6ac7aae7c8e370af47e1d39a9f69acc1e12c


---


# So ermitteln Sie, ob Ihre Benutzer sich für RMS for Individuals registriert haben

>*Gilt für: Azure Rights Management*

Wie erfahren Sie als Administrator, ob Ihre Benutzer sich für RMS for Individuals registriert haben? Sie können eine dieser Methoden bzw. eine beliebige Kombination der folgenden Methoden verwenden:

-   Fragen Sie Benutzer, wie sie sehr vertrauliche Dateien schützen, insbesondere bei der Zusammenarbeit mit anderen Personen außerhalb der Organisation.

-   Wenn Sie ein Azure-Abonnement für Ihre Organisation besitzen, verwenden Sie das Cmdlet [Get-MsolAccountSku](https://msdn.microsoft.com/library/azure/dn194118.aspx), um festzustellen, ob **RIGHTSMANAGEMENT_ADHOC** als eines der Abonnements zurückgegeben wird. Ist dies der Fall, ist dies das RMS for Individuals-Abonnement, das der Organisation gewährt wurde, mit einem Pool aktiver Einheiten, die Benutzern zur Verfügung stehen, um den Self-Service-Anmeldevorgang zu verwenden.

-   Verwenden Sie eine Systemvewaltungslösung wie System Center Configuration Manager, um installierte und in Verwendung befindliche Software zu inventarisieren. Die Rights Management-Freigabeanwendung mithilfe des **ipviewer.exe** -Programms ausgeführt, und Sie können [die Anwendung kostenlos herunterladen und installieren die Anwendung](http://go.microsoft.com/fwlink/?LinkId=303970) , um andere Eigenschaften dieser Anwendung zu identifizieren, die Sie dann für Ihren Softwarebestand nutzen.

-   Achten Sie auf Dateinamenerweiterungen, die von der Rights Management-Freigabeanwendung erstellt werden. Die Dateinamenerweiterungen „PFILE“ und „PPDF“ sind die offensichtlichsten Beispiele, doch es gibt noch andere Dateien, die ihre Dateinamenerweiterung ändern, wenn sie durch Rights Management systemeigen geschützt sind. Weitere Informationen finden Sie im Abschnitt [Unterstützte Dateitypen und Dateinamenerweiterungen](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) im [Rights Management-Freigabeanwendung – Administratorhandbuch](http://technet.microsoft.com/library/dn339003.aspx).




<!--HONumber=Sep16_HO1-->


