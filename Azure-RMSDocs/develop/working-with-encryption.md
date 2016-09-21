---
title: "Gewusst wie: Arbeiten mit Verschlüsselungseinstellungen | Azure RMS"
description: "Orientierung für die Azure RMS-Verschlüsselungspakete und Codeausschnitte für deren Nutzung."
keywords: 
author: bruceperlerms
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: B1D2C227-F43D-4B18-9956-767B35145792
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 83c4eb741c484018a2837840465aca3276c785c1
ms.openlocfilehash: b128a9adf75ae8558a33181f63881e2243e840bb


---

# Exemplarische Vorgehensweise: Arbeiten mit Verschlüsselungseinstellungen

Dieses Thema erläutert unsere Verschlüsselungspakete und zeigt einige Codeausschnitte für deren Verwendung.

## Unterstützung für AES 256, der neue Standard

Für die Verwendung der *AES 256*-basierten Verschlüsselung ist kein zusätzlicher Code erforderlich, da es sich um den neuen Standard handelt, vorausgesetzt, Sie entwickeln mit dem RMS SDK 2.1-Update vom März 2015 oder neuer. Wir empfehlen Ihnen dringend, Ihre Anwendungen mit dieser Version aufgrund der zusätzlichen Sicherheitsvorteile von *AES 256* zu aktualisieren.

> [!IMPORTANT]
> Unterstützung der Nutzung von *AES 256*-geschützten Dateien ist seit der [Version vom Oktober 2014](release-notes-rtm.md) vorhanden. Wenn Sie Anwendungen ausführen, die mit einer Version des SDK vor Oktober 2014 erstellt wurden, werden diese Anwendungen durch dieses Update nicht mehr funktionieren. Stellen Sie sicher, dass Kunden der von Ihnen entwickelten Programme das aktualisierte SDK verwenden oder bereit sind, sofort auf die neueste Version der Anwendung zu aktualisieren.

 
## Unterstützung der API-Verschlüsselung

Seit dem [Update vom März 2015](release-notes-rtm.md) haben wir die drei folgenden Flags in unsere API und die zugehörigen Verschlüsselungpakete integriert:

-   IPC\_ENCRYPTION\_PACKAGE\_AES256\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_CBC4K
-   IPC\_ENCRYPTION\_PACKAGE \_AES128\_ECB (auch als veraltete Algorithmen bezeichnet)

Die Verschlüsselungpaketflags (siehe [**Bevorzugte Verschlüsselung**](/rights-management/sdk/2.1/api/win/constants#msipc_preferred_encryption)) können in Verbindung mit unserem neuen Lizenzeigenschaftsflag **IPC\_LI\_PREFERRED\_ENCRYPTION\_PACKAGE** verwendet werden.

Es folgend einige einfache Codeausschnitte, die die Verwendung der neuen Lizenzeigenschaft veranschaulichen.

## Veraltete Algorithmen

Das Flag **IPC\_LI\_DEPRECATED\_ENCRYPTION\_ALGORITHMS** wird in unserer API nicht länger zur Verfügung gestellt. Zukünftige Anwendungen werden daher nicht mehr kompiliert, wenn sie auf dieses Flag verweisen, aber bereits entwickelte Anwendungen, die es verwenden, sind weiterhin funktionsfähig, da wir das Flag privat im API-Code berücksichtigen.

Die Vorteile des veralteten Verschlüsselungsalgorithmusflags können weiterhin durch einfaches Ändern eines Flags erreicht werden. Beispiele finden Sie in den folgenden Codeausschnitten.

## Schützen von Dateien mit AES 256 CBC4K

Keine Änderung im Code erforderlich, *AES 256* CBC4K ist der Standard.

    C++

    hr = IpcCreateLicenseFromTemplateID(pcTil-&gt;aTi[0].wszID,
                                    0,
                                    NULL,
                                    &amp;pLicenseHandle);


## Schützen von Dateien mit AES-128 CBC4K 

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


## Schützen von Dateien mit AES-128 ECB (veraltete Algorithmen)

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

 

 



<!--HONumber=Sep16_HO2-->


