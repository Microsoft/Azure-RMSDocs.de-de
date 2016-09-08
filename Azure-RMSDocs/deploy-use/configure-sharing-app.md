---
title: "Rights Management-Freigabeanwendung&colon; Installation und Konfiguration für Clients | Azure RMS"
description: "Die Rights Management (RMS)-Freigabeanwendung ist für Clientcomputer erforderlich, damit diese Azure RMS mit Office 2010 verwenden können, und wird für alle Computer und mobilen Geräte empfohlen, die Azure RMS unterstützen. Die RMS-Freigabeanwendung integriert sich in Office-Anwendungen, indem ein Office-Add-In- installiert wird, sodass Benutzer Dateien und E-Mails ganz einfach direkt über das Menüband schützen können. Diese Anwendung bietet auch allgemeinen Schutz für Dateitypen, die nicht systemeigen von Azure Rights Management unterstützt werden, und eine Website zur Dokumentverfolgung, auf der Benutzer geschützte Dateien verfolgen und sperren können, die sie geschützt haben."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: b9af5dc3-73d4-4147-b7ef-f6803b0d5216
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: bf7cd8007b5423efaa13849101af5c4688cf0975


---

# Rights Management-Freigabeanwendung: Installation und Konfiguration für Clients

>*Gilt für: Azure Rights Management, Office 365*

Die Rights Management (RMS)-Freigabeanwendung ist für Clientcomputer erforderlich, damit diese Azure RMS mit Office 2010 verwenden können, und wird für alle Computer und mobilen Geräte empfohlen, die Azure RMS unterstützen. Die RMS-Freigabeanwendung integriert sich in Office-Anwendungen, indem ein Office-Add-In- installiert wird, sodass Benutzer Dateien und E-Mails ganz einfach direkt über das Menüband schützen können. Diese Anwendung bietet auch allgemeinen Schutz für Dateitypen, die nicht systemeigen von Azure Rights Management unterstützt werden, und eine Website zur Dokumentverfolgung, auf der Benutzer geschützte Dateien verfolgen und sperren können, die sie geschützt haben.

## Die RMS-Freigabeanwendung für Windows: Installation und Konfiguration
Informationen zum Installieren und Konfigurieren der RMS-Freigabeanwendung für Windows für eine Unternehmensbereitstellung finden Sie im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).

> [!TIP]
> Wenn Sie die RMS-Freigabeanwendung für einen einzelnen Computer schnell installieren und testen möchten, finden Sie Informationen dazu unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](../rms-client/install-sharing-app.md) im [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md).

## Die RMS-Freigabeanwendung für mobile Plattformen: Installation und Verwaltung
Um die RMS-Freigabeanwendung für mobile Plattformen zu installieren, laden Sie die entsprechende App herunter, indem Sie die Links auf der Seite [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)verwenden. Für die Verwendung von Azure RMS mit dieser App ist keine Konfiguration erforderlich.

**Bei Verwendung von Microsoft Intune**: Da die RMS-Freigabe-App das Microsoft Intune App Software Development Kit enthält, haben Sie folgenden Optionen:

-   Für Geräte, die von Intune registriert werden, können Sie die RMS-Freigabe-App für Geräte bereitstellen und verwalten, auf denen iOS und Android ausgeführt wird. Weitere Informationen finden Sie in der Intune-Dokumentation unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console). Verwenden Sie für Schritt 2 die Anleitung zum Veröffentlichen einer richtlinienverwalteten App.

-   Für Geräte, die nicht von Intune registriert werden, können Sie die RMS-Freigabe-App für Geräte verwalten, auf denen Android ausgeführt wird. Weitere Informationen finden Sie unter [Erstellen und Bereitstellen von Verwaltungsrichtlinien für mobile Apps mit Microsoft Intune](/intune/deploy-use/create-and-deploy-mobile-app-management-policies-with-microsoft-intune).




<!--HONumber=Aug16_HO4-->


