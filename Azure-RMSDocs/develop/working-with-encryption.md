---
title: 'Gewusst wie: Arbeiten mit Verschlüsselungseinstellungen | Azure RMS'
description: Orientierung für die Azure RMS-Verschlüsselungspakete und Codeausschnitte für deren Nutzung.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 44567c4f083ed482a7fd27963e11b65d9a366c86
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56259897"
---
# <a name="how-to-work-with-encryption-settings"></a>Exemplarische Vorgehensweise: Arbeiten mit Verschlüsselungseinstellungen

Dieses Thema erläutert unsere Verschlüsselungspakete und zeigt einige Codeausschnitte für deren Verwendung.

## <a name="support-for-aes-256-the-new-default"></a>Unterstützung für AES 256, der neue Standard

Für die Verwendung der *AES 256*-basierten Verschlüsselung ist kein zusätzlicher Code erforderlich, da es sich um den neuen Standard handelt, vorausgesetzt, Sie entwickeln mit dem RMS SDK 2.1-Update vom März 2015 oder neuer. Wir empfehlen Ihnen dringend, Ihre Anwendungen mit dieser Version aufgrund der zusätzlichen Sicherheitsvorteile von *AES 256* zu aktualisieren.

> [!IMPORTANT]
> Unterstützung der Nutzung von *AES 256*-geschützten Dateien ist seit der [Version vom Oktober 2014](release-notes-rtm.md) vorhanden. Wenn Sie Anwendungen ausführen, die mit einer Version des SDK vor Oktober 2014 erstellt wurden, werden diese Anwendungen durch dieses Update nicht mehr funktionieren. Stellen Sie sicher, dass Kunden der von Ihnen entwickelten Programme das aktualisierte SDK verwenden oder bereit sind, sofort auf die neueste Version der Anwendung zu aktualisieren.

 
## <a name="api-encryption-support"></a>Unterstützung der API-Verschlüsselung

Seit dem [Update vom März 2015](release-notes-rtm.md) haben wir die drei folgenden Flags in unsere API und die zugehörigen Verschlüsselungpakete integriert:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (auch als veraltete Algorithmen bezeichnet)

Die Verschlüsselungpaketflags (siehe [Bevorzugte Verschlüsselung](https://msdn.microsoft.com/library/dn974065.aspx)) können in Verbindung mit dem Lizenzeigenschaftsflag *IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE* verwendet werden.

Es folgend einige einfache Codeausschnitte, die die Verwendung der neuen Lizenzeigenschaft veranschaulichen.

## <a name="deprecated-algorithms"></a>Veraltete Algorithmen

Das Flag *IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS* wird in unserer API nicht länger zur Verfügung gestellt. Zukünftige Anwendungen werden daher nicht mehr kompiliert, wenn sie auf dieses Flag verweisen, aber bereits entwickelte Anwendungen, die es verwenden, sind weiterhin funktionsfähig, da wir das Flag privat im API-Code berücksichtigen.

Die Vorteile des veralteten Verschlüsselungsalgorithmusflags können weiterhin durch einfaches Ändern eines Flags erreicht werden. Beispiele finden Sie in den folgenden Codeausschnitten.

## <a name="protect-files-with-aes-256-cbc4k"></a>Schützen von Dateien mit AES 256 CBC4K

Keine Änderung im Code erforderlich, *AES 256* CBC4K ist der Standard.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## <a name="protect-files-with-aes-128-cbc4k"></a>Schützen von Dateien mit AES-128 CBC4K 

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_CBC4K;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);


## <a name="protect-files-with-aes-128-ecb-deprecated-algorithms"></a>Schützen von Dateien mit AES-128 ECB (veraltete Algorithmen)

Dieses Beispiel zeigt außerdem die neue Methode zur Unterstützung von *veralteten Algorithmen*.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);

    DWORD dwEncryptionMode = IPC_ENCRYPTION_PACKAGE_AES128_ECB;

    hr = IpcSetLicenseProperty(pLicenseHandle,
                           false,
                           IPC_LI_PREFERRED_ENCRYPTION_PACKAGE,
                           &amp;dwEncryptionMode);

