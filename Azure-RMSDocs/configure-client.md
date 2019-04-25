---
title: 'Azure Information Protection-Client: Installation und Konfiguration'
description: Informationen für Administratoren zum Bereitstellen des Azure Information Protection-Clients auf Windows-Computern und mobilen Geräten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 02/05/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 79d4dbb1d6339f0261d57b32cf77addee9ca9744
ms.sourcegitcommit: fff4c155c52c9ff20bc4931d5ac20c3ea6e2ff9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/24/2019
ms.locfileid: "60180340"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Azure Information Protection-Client: Installation und Konfiguration für clients

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Computer mit Office 2010 erfordern den Azure Information Protection-Client für die Authentifizierung beim Azure Rights Management-Dienst und beim Azure Information Protection-Dienst. Dieser Client wird außerdem für alle Windows-Computer und iOS- sowie Android-Geräte empfohlen, die den Azure Rights Management-Dienst und Azure Information Protection unterstützen. 

Der Azure Information Protection-Client integriert sich in Office-Anwendungen, indem ein Office-Add-In installiert wird, sodass Benutzer Dokumente und E-Mails ganz einfach direkt über das Office-Menüband bezeichnen und schützen können. Dieser Client bietet auch Bezeichnung und Schutz für Dateitypen, die nicht nativ vom Azure Rights Management-Dienst unterstützt werden, sowie einen Viewer für geschützte Dateien und eine Website zur Nachverfolgung von Dokumenten, auf der Benutzer von ihnen geschützte Dateien verfolgen und sperren können.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Azure Information Protection-Client für Windows: Installation und Konfiguration

Informationen zur Installation und Konfiguration des Clients für Windows in Unternehmen finden Sie im [Azure Information Protection-Administratorhandbuch](./rms-client/client-admin-guide.md).

> [!TIP]
> Wenn Sie den Azure Information Protection-Client schnell auf einem einzelnen Computer installieren und testen möchten, finden Sie weitere Informationen unter [Herunterladen und Installieren des Azure Information Protection-Clients](./rms-client/install-client-app.md) im [Azure Information Protection-Client – Benutzerhandbuch](./rms-client/client-user-guide.md).

## <a name="the-azure-information-protection-client-for-ios-and-android-installation-and-management"></a>Azure Information Protection-Client für iOS und Android: Installation und Verwaltung

Wenn Sie den Azure Information Protection-Client für diese gängigen mobilen Plattformen installieren möchten, können Sie die relevante App über die Links auf der Seite [Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970) herunterladen. Es ist keine Konfiguration erforderlich.

> [!NOTE]
> Für Mac-Computer können die RMS-Freigabe-Apps über Links auf dieser Seite heruntergeladen werden. Diese Computer unterstützen den Azure Information Protection-Client nicht.

### <a name="integration-with-intune"></a>Integration in Intune

Da die Azure Information Protection-App das Microsoft Intune App Software Development Kit verwendet, können Sie, wenn iOS- und Android-Geräte von Intune angemeldet werden, die Azure Information Protection-App für diese Geräte bereitstellen und verwalten:

1. [Hinzufügen der Azure Information Protection-App zu Intune](/intune/apps-add) 

2. Führen Sie dazu eine der beiden folgenden Aktionen aus:
    
    - Bereitstellen der App durch [Zuweisen zu Benutzern](/intune/apps-deploy)
    
    - Verwalten der App durch Verwendung von [App-Schutzrichtlinien](/intune/app-protection-policies)

Zusätzliche Informationen zum Hinzufügen der Azure Information Protection-App zu Intune:

- Für iOS: Suchen Sie nach der App, und fügen Sie die App von Intune zu.

- Für Android: Verwenden Sie die folgende **App Store-URL**, wenn Sie die App hinzufügen:
        
        https://play.google.com/store/apps/details?id=com.microsoft.ipviewer

Wenn die Azure Information Protection-App für eine App-Schutzrichtlinie für Android-Geräte konfiguriert wurde, kann diese App nicht nur geschützte Texte, Bilder und PDF-Dokumente öffnen, sondern auch Audio- und Videodateien. Weitere Informationen finden Sie unter [Anzeigen von Mediendateien mit der Azure Information Protection-App](/intune/end-user-mam-apps-android#view-media-files-with-the-azure-information-protection-app).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie den Azure Information Protection-Client installiert und konfiguriert haben, möchten Sie möglicherweise mehr darüber erfahren, wie der Client die unterschiedlichen Nutzungsrechte interpretiert, die zum Schutz von Dokumenten und E-Mails verwendet werden können. Weitere Informationen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md).
