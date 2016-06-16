---
# erforderliche Metadaten

title: Exemplarische Vorgehensweise: Debuggen einer rechtlich geschützten Anwendung | Azure RMS-Beschreibung: Im folgenden Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.
keywords: author: bruceperlerms manager: mbaldwin ms.date: 04/28/2016 ms.topic: article ms.prod: azure ms.service: rights-management ms.technology: techgroup-identity ms.assetid: 6F6C7651-6A6E-45DD-A0C5-F036F803249B
# optionale Metadaten

#ROBOTS:
Zielgruppe: Entwickler
#ms.devlang:
ms.reviewer: shubhamp ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Exemplarische Vorgehensweise: Debuggen einer rechtlich geschützten Anwendung

Im folgenden Thema wird veranschaulicht, wie Sie Ihre Anwendung debuggen und das Windows-Ereignisprotokoll verwenden.

## Debuggen der Anwendung

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

### Anwendungsprotokollierung per Windows-Ereignisprotokoll

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

 

## Verwandte Themen

 

 


<!--HONumber=Jun16_HO2-->


