---
title: "Gewusst wie: Debuggen einer rechtlich geschützten Anwendung | Azure RMS"
description: Im folgenden Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: da5a9fa1a2c2eaccb6768914a0c425983b14fdbe


---

# <a name="how-to-debug-a-rights-enabled-application"></a>Exemplarische Vorgehensweise: Debuggen einer rechtlich geschützten Anwendung

Im folgenden Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.

## <a name="debugging-your-application"></a>Debuggen der Anwendung

Im Rights Management Services SDK 2.1 sind die Anti-Debuggingüberprüfungen in der Entwicklerversion Ihrer Laufzeit deaktiviert.

Sie können die Debugablaufverfolgung aktivieren, indem Sie den folgenden Registrierungsschlüssel verwenden. (Um die Debugablaufverfolgung zu deaktivieren, ändern Sie den Wert in 0.) Für das Debuggen in dieser Version müssen keine weiteren Anforderungen erfüllt werden.


```
HKEY_LOCAL_MACHINE
   SOFTWARE
      Microsoft
         MSIPC
            "Trace" = 00000001
            Data type
            dword
```

### <a name="application-logging-by-using-the-windows-event-log"></a>Anwendungsprotokollierung per Windows-Ereignisprotokoll

Der Name des Ereignisprotokolls lautet „Microsoft-RMS-MSIPC/Debug“. Dies bedeutet, dass das Protokoll in der Windows-Ereignisanzeige als „Application and Services Logs\\Microsoft\\RMS\\MSIPC\\Debug“ angezeigt wird.

**Hinweis**: Das Protokoll ist standardmäßig aktiviert und auf den Ausführlichkeitsgrad 3 festgelegt.

 

Um die Einstellungen für die Protokollierungsfunktion zu ändern, können Sie entweder die Benutzeroberfläche der Windows-Ereignisanzeige oder Wevtutil, ein in Windows integriertes Befehlszeilentool, verwenden.

Über die Wevtutil-Oberfläche können Sie den Ausführlichkeitsgrad des Protokolls steuern.

Derzeit werden drei Protokollierungsebenen unterstützt:

-   Ebene 2 – Fehler
-   Ebene 3 – Warnung
-   Ebene 4 – Information

Mit dem folgenden Befehl wird beispielsweise das MSIPC-Ereignisprotokoll aktiviert und der Ausführlichkeitsgrad auf „Information“ festgelegt.

**wevtutil sl Microsoft-RMS-MSIPC/Debug /e:true /l:4**

**Hinweis**: Wählen Sie in der Windows-Ereignisanzeige im Menü **Ansicht** die Option **Analytische und Debugprotokolle einblenden**, um das MSIPC-Debugprotokoll anzuzeigen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


