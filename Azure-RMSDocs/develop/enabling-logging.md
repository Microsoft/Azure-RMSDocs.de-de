---
title: Gewusst wie&#58; Aktivieren der Fehler- und Leistungsprotokollierung | Azure RMS
description: "Mit dem Microsoft Rights Management SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 9a81746a17988f788503ca706f19a4ed89702c4e


---

# <a name="how-to-enable-error-and-performance-logging"></a>Gewusst wie: Aktivieren der Fehler- und Leistungsprotokollierung
Mit dem Microsoft Rights Management SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet.

## <a name="overview"></a>Übersicht ##
Sie können die Benutzerfreundlichkeit und Problembehandlung für Benutzer verbessern, indem Sie automatische Uploads von Diagnose-, Leistungs- und Telemetrieprotokolldaten auf Server von Microsoft aktivieren. 

> [!IMPORTANT] 
> Um die Datenschutzaspekte für Benutzer zu berücksichtigen, müssen Sie als App-Entwickler den Benutzer um seine Zustimmung bitten, bevor Sie die automatische Protokollierung aktivieren.

> [!NOTE]
> Hier ist als Beispiel eine Standardnachricht, die Microsoft zur Protokollierungsbenachrichtigung nutzt: 
>
> *Durch Aktivieren der Fehler- und Leistungsprotokollierung stimmen Sie dem Senden von Fehler- und Leistungsdaten an Microsoft zu.  Microsoft erfasst Fehler- und Leistungsdaten automatisch über das Internet („Daten“).  Microsoft verwendet diese Daten, um die Qualität, Sicherheit und Integrität von Microsoft-Produkten und -Diensten sicherzustellen und zu verbessern.  Beispielsweise analysieren wir die Leistung und Zuverlässigkeit, die von Ihnen verwendeten Features, die Reaktionsschnelligkeit der Features, die Geräteleistung, Interaktionen mit der Benutzeroberfläche und etwaige Probleme, die bei der Nutzung des Produkts auftreten.  Zu den Daten gehören auch Informationen zur Konfiguration Ihrer Software, z. B. der Software, die derzeit ausgeführt wird, und die IP-Adresse.*  

Sie verwalten die Protokollierung mit zwei Eigenschaften.

-   Aktivieren Sie die Protokollierung mit der **IpcCustomerExperienceDataCollectionEnabled**-Eigenschaft. Die Einstellung ist für alle Gerätezurücksetzungen gleich.
-   Steuern Sie die Protokollierungsebene mit der **IpcLogLevel**-Eigenschaft, indem Sie die folgenden Einstellungen verwenden:

    * 1 – Ausführlich
    * 2 – Information
    * 3 – Warnung
    * 4 – Fehler
    * 5 – Kritisch

In allen folgenden Beispielcodeausschnitten kann die aufrufende Anwendung die Eigenschaft festlegen oder abfragen.

### <a name="android"></a>Android ###
Automatische Protokollierung aktivieren

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## <a name="ios"></a>iOS ##
Automatische Protokollierung aktivieren

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
        [prefs setBool:FALSE forKey:@&quot;IpcCustomerExperienceDataCollectionEnabled”];
        [[NSUserDefaults standardUserDefaults] synchronize];

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcCustomerExperienceDataCollectionEnabled&quot;];

Protokollebenensteuerung festlegen

    NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
      [prefs setInteger:1 forKey:@&quot;IpcLogLevel”];
      [[NSUserDefaults standardUserDefaults] synchronize];

Einstellung für Protokollebenensteuerung abrufen

    [[NSUserDefaults standardUserDefaults] boolForKey:@&quot;IpcLogLevel&quot;];
 

## <a name="windows"></a>Windows ##
Automatische Protokollierung aktivieren

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

Weitere Informationen zu optionalen Einstellungen finden Sie unter [CustomerExperienceOptions](https://msdn.microsoft.com/library/microsoft.rightsmanagement.customerexperienceoptions.aspx).

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**Hinweis**: Die obigen Windows-Codeausschnitte sind in C++ geschrieben. Aktualisieren Sie die Syntax für C\# mit „.“ anstelle von „::“.

**Linux/C++**: Dieses SDK verfügt über einige grundlegende Funktionen für die Protokollierung, die nicht so umfangreich wie die Funktionen anderer Plattformen sind. Weitere Informationen finden Sie im Abschnitt **Troubleshooting** der Datei „README.md“ unter [RMS SDK for portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting) (RMS SDK für portables C++).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO1-->


