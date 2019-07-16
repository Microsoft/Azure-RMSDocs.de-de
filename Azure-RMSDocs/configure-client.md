---
title: 'Azure Information Protection-Client: Installation und Konfiguration'
description: Informationen für Administratoren zum Bereitstellen der Azure Information Protection Clients auf Windows-Computern und mobilen Geräten.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/15/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b1a19ae7-db26-40da-9e21-6620af3d0b02
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4daf9bfa058aa179e9297e439518202cf965f4ac
ms.sourcegitcommit: 9d99385bab62478de6c00faae15d8b27f80239e5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2019
ms.locfileid: "68229861"
---
# <a name="azure-information-protection-client-installation-and-configuration-for-clients"></a>Azure Information Protection-Client: Installation und Konfiguration für Clients

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Computer, auf denen Office 2010 ausgeführt wird, benötigen entweder den Azure Information Protection Client (klassisch) oder den Azure Information Protection Unified-Bezeichnung-Client, um sich beim Azure Information Protection Dienst zu authentifizieren.

Der Unterschied zwischen diesen beiden Clients ist nicht sicher?  Siehe [worin besteht der Unterschied zwischen dem Azure Information Protection-Client und dem Azure Information Protection Unified-Bezeichnungs Client?](faqs.md#whats-the-difference-between-azure-information-protection-and-microsoft-information-protection)

Diese Clients werden auch für alle Windows-Computer empfohlen, da Sie ein Office-Add-in installieren, sodass Benutzer Dokumente und e-Mails ganz einfach direkt über das Office-Menüband bezeichnen und schützen können. Diese Clients bieten außerdem Bezeichnungen und Schutz für Dateitypen, die nicht nativ vom Schutzdienst (Azure Rights Management) unterstützt werden, und einen Viewer für geschützte Dateien, die nicht von Office-Apps geöffnet werden können. Es gibt einen ähnlichen Viewer für IOS und Android.

Der klassische Client unterstützt auch eine Website zum Nachverfolgen von Dokumenten, auf der Benutzer geschützte Dateien verfolgen und widerrufen können.

## <a name="the-azure-information-protection-client-for-windows-installation-and-configuration"></a>Azure Information Protection-Client für Windows: Installation und Konfiguration

Informationen zu einer Unternehmens Installation und-Konfiguration des Clients für Windows finden Sie in den folgenden Administrator Handbüchern:

- Einheitlicher Bezeichnungs Client: [Azure Information Protection Unified Bezeichnung-Client Administrator Handbuch](./rms-client/clientv2-admin-guide.md)] (./rms-client/client-admin-guide.md)

- Klassischer Client: [Azure Information Protection-Client – Administratorhandbuch](./rms-client/client-admin-guide.md)

Wenn Sie diese Clients jedoch schnell für einen einzelnen Computer installieren und testen möchten, finden Sie die folgenden Anweisungen in den Benutzerhandbüchern:

- Einheitlicher Bezeichnungs Client: [Herunterladen und Installieren des Azure Information Protection Unified Bezeichnung-Client](./rms-client/install-unifiedlabelingclient-app.md)

- Klassischer Client: [Laden Sie den Azure Information Protection Client](./rms-client/install-client-app.md) aus dem [Azure Information Protection Client-Benutzerhandbuch](./rms-client/client-user-guide.md)herunter, und installieren Sie ihn.

## <a name="the-azure-information-protection-app-for-ios-and-android-installation-and-management"></a>Die Azure Information Protection-App für IOS und Android: Installation und Verwaltung

Verwenden Sie die Links auf der [Seite Microsoft Azure Information Protection](https://go.microsoft.com/fwlink/?LinkId=303970), um den Azure Information Protection App-Viewer für IOS und Android zu installieren. Es ist keine Konfiguration erforderlich.

> [!NOTE]
> Für Mac-Computer können die RMS-Freigabe-Apps über Links auf dieser Seite heruntergeladen werden. Diese Computer unterstützen den Azure Information Protection-Client nicht.

### <a name="integration-with-intune"></a>Integration in Intune

Da die Azure Information Protection Viewer-APP das Microsoft InTune App Software Development Kit verwendet, können Sie die Azure Information Protection Viewer-App für diese Geräte bereitstellen und verwalten, wenn IOS-und Android-Geräte von InTune angemeldet werden:

1. [Hinzufügen der Azure Information Protection-App zu Intune](/intune/apps-add) 

2. Führen Sie dazu eine der beiden folgenden Aktionen aus:
    
    - Bereitstellen der App durch [Zuweisen zu Benutzern](/intune/apps-deploy)
    
    - Verwalten der App durch Verwendung von [App-Schutzrichtlinien](/intune/app-protection-policies)

Zusätzliche Informationen zum Hinzufügen der Azure Information Protection-App zu Intune:

- Für ios: Suchen Sie nach der App, und fügen Sie die App von Intune zu.

- Für Android: Verwenden Sie die folgende **App Store-URL**, wenn Sie die App hinzufügen:
        
        https://play.google.com/store/apps/details?id=com.microsoft.ipviewer

Wenn die Azure Information Protection-App für eine App-Schutzrichtlinie für Android-Geräte konfiguriert wurde, kann diese App nicht nur geschützte Texte, Bilder und PDF-Dokumente öffnen, sondern auch Audio- und Videodateien. Weitere Informationen finden Sie unter [Anzeigen von Mediendateien mit der Azure Information Protection-App](/intune/end-user-mam-apps-android#view-media-files-with-the-azure-information-protection-app).

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie Azure Information Protection Clients installiert und konfiguriert haben, müssen Sie möglicherweise mehr darüber erfahren, wie der Client die verschiedenen Nutzungsrechte interpretiert, die zum Schutz von Dokumenten und e-Mails verwendet werden können. Weitere Informationen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Information Management](configure-usage-rights.md).
