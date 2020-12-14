---
title: 'Azure Information Protection-Client: Installation und Konfiguration'
description: Informationen für Administratoren zum Bereitstellen der Azure Information Protection Clients auf Windows-Computern und mobilen Geräten.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/16/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ca4dfed92aafb690da28e5164496b924c9c3fe7e
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383600"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Azure Information Protection-Client: Installation und Konfiguration für Clients

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE]
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Für Computer, auf denen Office 2010 ausgeführt wird, muss sich der Azure Information Protection Client beim Azure Information Protection-Dienst authentifizieren.

Der AIP Unified Label-Client wird für alle Windows-Computer empfohlen, da er ein Office-Add-in installiert, das Benutzern das einfache bezeichnen und schützen von Dokumenten direkt über das Office-Menüband ermöglicht. Der Client bietet auch Bezeichnung und Schutz für Dateitypen, die nicht vom integrierten Schutzdienst (Azure Rights Management) unterstützt werden, sowie einen Viewer für geschützte Dateien, die nicht von Office-Apps geöffnet werden können. Es gibt einen ähnlichen Viewer für IOS und Android.

Wenn Sie den klassischen AIP-Client installiert haben, verfügen Sie auch über eine Website zum Nachverfolgen von Dokumenten, auf der Benutzer geschützte Dateien verfolgen und widerrufen können.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Azure Information Protection-Client für Windows: Installation und Konfiguration

Informationen zu einer Unternehmens Installation und-Konfiguration des Clients für Windows finden Sie im [Azure Information Protection Unified-Bezeichnung Client Administrator Handbuch](./rms-client/clientv2-admin-guide.md).

Wenn Sie diese Clients schnell für einen einzelnen Computer installieren und testen möchten, finden Sie weitere Informationen unter [herunterladen und Installieren des Azure Information Protection Unified Bezeichnung-Clients](./rms-client/install-unifiedlabelingclient-app.md).

**Nur klassischer Client**: Wenn Sie den klassischen-Client installiert haben, verwenden Sie stattdessen die folgenden Links:

- [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md)
- [Laden Sie den Azure Information Protection Client herunter, und installieren Sie](./rms-client/install-client-app.md)ihn.

## <a name="the-azure-information-protection-app-for-ios-and-android-installation-and-management"></a>Die Azure Information Protection-App für IOS und Android: Installation und Verwaltung

Verwenden Sie die Links auf der [Seite Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970), um den Azure Information Protection App-Viewer für IOS und Android zu installieren. Es ist keine Konfiguration erforderlich.

> [!NOTE]
> Für Mac-Computer können die RMS-Freigabe-Apps über Links auf dieser Seite heruntergeladen werden. Diese Computer unterstützen den Azure Information Protection-Client nicht.

### <a name="integration-with-intune"></a>Integration in Intune

Da die Azure Information Protection Viewer-APP das Microsoft InTune App Software Development Kit verwendet, können Sie die Azure Information Protection Viewer-App für diese Geräte bereitstellen und verwalten, wenn IOS-und Android-Geräte von InTune angemeldet werden:

1. [Hinzufügen der Azure Information Protection-App zu Intune](/intune/apps/apps-add)

2. Führen Sie dazu eine der beiden folgenden Aktionen aus:

    - Bereitstellen der App durch [Zuweisen zu Benutzern](/intune/apps/apps-deploy)

    - Verwalten der App durch Verwendung von [App-Schutzrichtlinien](/intune/apps/app-protection-policies)

Zusätzliche Informationen zum Hinzufügen der Azure Information Protection-App zu Intune:

- Für ios: Suchen Sie die app in InTune, und fügen Sie Sie hinzu.

- Für Android: Verwenden Sie beim Hinzufügen der APP die folgende **AppStore-URL**:

    ```md
    https://play.google.com/store/apps/details?id=com.microsoft.ipviewer
    ```

Wenn die Azure Information Protection-App für eine App-Schutzrichtlinie für Android-Geräte konfiguriert wurde, kann diese App nicht nur geschützte Texte, Bilder und PDF-Dokumente öffnen, sondern auch Audio- und Videodateien. Weitere Informationen finden Sie unter [Anzeigen von Mediendateien mit der Azure Information Protection-App](/intune/fundamentals/end-user-mam-apps-android#view-media-files-with-the-azure-information-protection-app).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Azure Information Protection Clients installiert und konfiguriert haben, müssen Sie möglicherweise mehr darüber erfahren, wie der Client die verschiedenen Nutzungsrechte interpretiert, die zum Schutz von Dokumenten und e-Mails verwendet werden können. Weitere Informationen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Information Management](configure-usage-rights.md).
