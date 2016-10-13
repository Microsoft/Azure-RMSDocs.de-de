---
title: "Rights Management-Freigabeanwendung&colon;Installation und Konfiguration für Clients | Azure Information Protection"
description: "Informationen für Administratoren zum Bereitstellen der RMS-Freigabeanwendung (Rights Management) auf Windows-Computern und mobilen Geräten."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b9af5dc3-73d4-4147-b7ef-f6803b0d5216
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 635c499dfd2ec82064b659823117cd78b268e74c
ms.openlocfilehash: 200b64f0f6ea13890068cfe0bd2b3858b73b648e


---

# Rights Management-Freigabeanwendung: Installation und Konfiguration für Clients

>*Gilt für: Azure Information Protection, Office 365*

Die Rights Management-Freigabeanwendung (RMS) ist für Clientcomputer erforderlich, damit diese den Azure Rights Management-Dienst mit Office 2010 verwenden können. Sie wird darüber hinaus für alle Computer und mobilen Geräte empfohlen, die den Azure Rights Management-Dienst über Azure Information Protection unterstützen. Die RMS-Freigabeanwendung integriert sich in Office-Anwendungen, indem ein Office-Add-In- installiert wird, sodass Benutzer Dateien und E-Mails ganz einfach direkt über das Menüband schützen können. Diese Anwendung bietet auch allgemeinen Schutz für Dateitypen, die nicht nativ vom Azure Rights Management-Dienst unterstützt werden, sowie eine Website zur Dokumentkontrolle, auf der Benutzer geschützte Dateien verfolgen und sperren können.

## Die RMS-Freigabeanwendung für Windows: Installation und Konfiguration
Informationen zum Installieren und Konfigurieren der RMS-Freigabeanwendung für Windows für eine Unternehmensbereitstellung finden Sie im [Rights Management-Freigabeanwendung – Administratorhandbuch](../rms-client/sharing-app-admin-guide.md).

> [!TIP]
> Wenn Sie die RMS-Freigabeanwendung für einen einzelnen Computer schnell installieren und testen möchten, finden Sie Informationen dazu unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](../rms-client/install-sharing-app.md) im [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md).

## Die RMS-Freigabeanwendung für mobile Plattformen: Installation und Verwaltung
Um die RMS-Freigabeanwendung für mobile Plattformen zu installieren, laden Sie die entsprechende App herunter, indem Sie die Links auf der Seite [Microsoft Rights Management](http://go.microsoft.com/fwlink/?LinkId=303970)verwenden. Für die Verwendung des Azure Rights Management-Diensts mit dieser App ist keine Konfiguration erforderlich.

> [!NOTE]
> Die RMS-Freigabeanwendung für iOS und Android wird ab sofort von der Azure Information Protection-App ersetzt.

**Wenn Sie Microsoft Intune besitzen:** Da die Azure Information Protection-App das Microsoft Intune App Software Development Kit umfasst, können Sie, wenn iOS- und Android-Geräte von Intune angemeldet werden, die Azure Information Protection-App für diese Geräte bereitstellen und verwalten. Weitere Informationen finden Sie in der Intune-Dokumentation unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console). Verwenden Sie für Schritt 2 die Anleitung zum Veröffentlichen einer richtlinienverwalteten App.






<!--HONumber=Sep16_HO4-->


