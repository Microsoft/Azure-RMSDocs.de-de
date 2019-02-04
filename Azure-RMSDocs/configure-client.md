---
title: Azure Information Protection-Client &colon; Installieren und Konfigurieren
description: Informationen für Administratoren zum Bereitstellen des Azure Information Protection-Clients auf Windows-Computern und mobilen Geräten.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/17/2019
ms.topic: conceptual
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 10fc4c158cd4669b67c28e4968b0a3c4e7b889ad
ms.sourcegitcommit: b1e08bc29d50187532f00dc215ab331e0a7dbebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2019
ms.locfileid: "55146841"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Azure Information Protection-Client: Installation und Konfiguration für Clients

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Computer mit Office 2010 erfordern den Azure Information Protection-Client (oder die Rights Management-Freigabeanwendung) für die Authentifizierung beim Azure Rights Management-Dienst und beim Azure Information Protection-Dienst. Dieser Client wird außerdem für alle Windows-Computer und iOS- sowie Android-Geräte empfohlen, die den Azure Rights Management-Dienst und Azure Information Protection unterstützen. 

Der Azure Information Protection-Client integriert sich in Office-Anwendungen, indem ein Office-Add-In installiert wird, sodass Benutzer Dokumente und E-Mails ganz einfach direkt über das Office-Menüband bezeichnen und schützen können. Dieser Client bietet auch Bezeichnung und Schutz für Dateitypen, die nicht nativ vom Azure Rights Management-Dienst unterstützt werden, sowie einen Viewer für geschützte Dateien und eine Website zur Nachverfolgung von Dokumenten, auf der Benutzer von ihnen geschützte Dateien verfolgen und sperren können.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Azure Information Protection-Client für Windows: Installation und Konfiguration
Informationen zur Installation und Konfiguration des Clients für Windows in Unternehmen finden Sie im [Azure Information Protection-Administratorhandbuch](./rms-client/client-admin-guide.md).

> [!TIP]
> Wenn Sie den Azure Information Protection-Client schnell auf einem einzelnen Computer installieren und testen möchten, finden Sie weitere Informationen unter [Herunterladen und Installieren des Azure Information Protection-Clients](./rms-client/install-client-app.md) im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>Azure Information Protection-Client für iOS und Android: Installation und Verwaltung
Wenn Sie den Azure Information Protection-Client für diese gängigen mobilen Plattformen installieren möchten, können Sie die relevante App über die Links auf der Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) herunterladen. Es ist keine Konfiguration erforderlich.

> [!NOTE]
> Für Macintosh-Computer können die RMS-Freigabe-Apps für mobile Geräte über Links auf dieser Seite heruntergeladen werden. Diese Computer unterstützen den Azure Information Protection-Client nicht.

**Bei Verwendung von Microsoft Intune**: Da die Azure Information Protection-App mit dem Microsoft Intune App Software Development Kit erstellt wurde, können Sie, wenn iOS- und Android-Geräte von Intune angemeldet werden, die Azure Information Protection-App für diese Geräte bereitstellen und verwalten:

- Für die Bereitstellung der App [fügen Sie Intune die Azure Information Protection-App hinzu](/intune/apps-add) und [weisen diese Benutzern zu](/intune/apps-deploy).

- Verwenden Sie zum Verwalten der App die [App-Schutzrichtlinien](/intune/app-protection-policies) von Intune.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie den Azure Information Protection-Client installiert und konfiguriert haben, möchten Sie möglicherweise mehr darüber erfahren, wie der Client die unterschiedlichen Nutzungsrechte interpretiert, die zum Schutz von Dokumenten und E-Mails verwendet werden können. Weitere Informationen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md).
