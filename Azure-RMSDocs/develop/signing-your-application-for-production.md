---
# required metadata

title: Signieren Ihrer Anwendung für die Produktion | Azure RMS
description: In diesem Thema werden Sie durch das Signieren Ihrer Anwendung für den Produktionsmodus geführt.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c73fde39-6e16-470c-800e-59ab04c78f5f

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# Signieren Ihrer Anwendung für die Produktion

In diesem Thema werden Sie durch das Signieren Ihrer Anwendung für den Produktionsmodus geführt.

## Signieren Ihrer rechtlich geschützten Anwendung

Bei diesen Schritten wird vorausgesetzt, dass Sie Ihre Anwendung bereits für eine Präproduktionshierarchie signiert haben. Falls Sie dies noch nicht durchgeführt haben, können Sie den unter [Testen Ihrer rechtlich geschützten Anwendung](running-your-first-application.md) beschriebenen Prozess durchlaufen.

Nachdem Sie das Produktionszertifikat von Microsoft erhalten haben, verfügen Sie über die folgenden Dateien:

-   YourPrivateKey.dat
-   YourPublicKey.dat
-   ProductionCertificate.xml

Legen Sie sie in demselben Verzeichnis ab, in dem *GenManifest.exe* und Ihre Anwendungsbinärdatei (.exe) enthalten ist.

-   Im Prozess unten werden Sie durch die Erstellung einer neuen MCF-Datei mit Produktionszertifikat geführt:

    -   Erstellen Sie ein neues Verzeichnis, und fügen Sie Dateien in dieses neue Verzeichnis ein. Verwenden Sie „Notepad.exe“, um eine MCF-Datei für Ihre Anwendung zu erstellen. Die Datei sollte Folgendes enthalten:

        ``` syntax
        AUTO-GUID
        .\\YourPrivateKey.dat
        modulelist
        req     .\\<yourappname>.exe
        POLICYLIST
        INCLUSION
        PUBLICKEY .\\YourPublicKey.dat
        EXCLUSION
        ```

    -   Führen Sie den folgenden Befehl aus, um die Anwendung zu signieren:

        **genmanifest.exe -chain ProductionCertificate.xml** *NameIhrerApp***.mcf** *NameIhrerApp***.exe.man**

        Wenn Genmanifest erfolgreich ausgeführt wurde, wird der folgende Text angezeigt:

        Falls für Genmanifest ein Fehler auftritt, wird eine Fehlermeldung angezeigt.

    -   Sie sollten die Datei „*NameIhrerApp*.exe.man“ immer in demselben Verzeichnis wie „*NameIhrerApp*.exe“ ablegen.

### Verwandte Themen

* [Vorgehensweise](how-to-use-msipc.md)
* [Testen Ihrer rechtlich geschützten Anwendung](running-your-first-application.md)
 

 





<!--HONumber=Apr16_HO3-->


