---
title: Azure Information Protection-Client &colon; Installieren und Konfigurieren
description: "Informationen für Administratoren zum Bereitstellen des Azure Information Protection-Clients auf Windows-Computern und mobilen Geräten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 39d2fb244be91d7fc655efbdda24e4e268ac1329
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Azure Information Protection-Client: Installation und Konfiguration für Clients

>*Gilt für: Azure Information Protection, Office 365*

Computer mit Office 2010 erfordern den Azure Information Protection-Client (oder die Rights Management-Freigabeanwendung) für die Authentifizierung beim Azure Rights Management-Dienst und beim Azure Information Protection-Dienst. Dieser Client wird außerdem für alle Windows-Computer und iOS- sowie Android-Geräte empfohlen, die den Azure Rights Management-Dienst und Azure Information Protection unterstützen. 

Der Azure Information Protection-Client integriert sich in Office-Anwendungen, indem ein Office-Add-In installiert wird, sodass Benutzer Dokumente und E-Mails ganz einfach direkt über das Office-Menüband bezeichnen und schützen können. Dieser Client bietet auch Bezeichnung und Schutz für Dateitypen, die nicht nativ vom Azure Rights Management-Dienst unterstützt werden, sowie einen Viewer für geschützte Dateien und eine Website zur Nachverfolgung von Dokumenten, auf der Benutzer von ihnen geschützte Dateien verfolgen und sperren können.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Azure Information Protection-Client für Windows: Installation und Konfiguration
Informationen zur Installation und Konfiguration des Clients für Windows in Unternehmen finden Sie im [Azure Information Protection-Administratorhandbuch](../rms-client/client-admin-guide.md).

> [!TIP]
> Wenn Sie den Azure Information Protection-Client schnell auf einem einzelnen Computer installieren und testen möchten, finden Sie weitere Informationen unter [Herunterladen und Installieren des Azure Information Protection-Clients](../rms-client/install-client-app.md) im [Azure Information Protection-Client – Benutzerhandbuch](../rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>Azure Information Protection-Client für iOS und Android: Installation und Verwaltung
Wenn Sie den Azure Information Protection-Client für diese gängigen mobilen Plattformen installieren möchten, können Sie die relevante App über die Links auf der Seite [Microsoft Azure Information Protection](http://go.microsoft.com/fwlink/?LinkId=303970) herunterladen. Es ist keine Konfiguration erforderlich.

> [!NOTE]
> Für Macintosh-Computer und Windows Phone können die RMS-Freigabe-Apps für mobile Geräte über Links auf dieser Seite heruntergeladen werden. Diese Geräte unterstützen den Azure Information Protection-Client derzeit nicht.

**Wenn Sie Microsoft Intune besitzen:** Da die Azure Information Protection-App das Microsoft Intune App Software Development Kit umfasst, können Sie, wenn iOS- und Android-Geräte von Intune angemeldet werden, den Azure Information Protection-Viewer für diese Geräte bereitstellen und verwalten. Weitere Informationen finden Sie in der Intune-Dokumentation unter [Konfigurieren und Bereitstellen von Verwaltungsrichtlinien für mobile Anwendungen in der Microsoft Intune-Konsole](/intune/deploy-use/configure-and-deploy-mobile-application-management-policies-in-the-microsoft-intune-console). Verwenden Sie für Schritt 2 die Anleitung zum Veröffentlichen einer richtlinienverwalteten App.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


