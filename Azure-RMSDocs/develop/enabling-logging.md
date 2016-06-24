---
# required metadata

title: Gewusst wie&#58; Aktivieren der Fehler- und Leistungsprotokollierung | Azure RMS
description: Mit dem Microsoft Rights Management SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Gewusst wie: Aktivieren der Fehler- und Leistungsprotokollierung
Mit dem Microsoft Rights Management SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet.

## Übersicht ##
Sie können die Benutzerfreundlichkeit und Problembehandlung für Benutzer verbessern, indem Sie automatische Uploads von Diagnose- und Leistungsprotokollen auf Server von Microsoft aktivieren. Um die Datenschutzaspekte für Benutzer zu berücksichtigen, müssen Sie als App-Entwickler den Benutzer um seine Zustimmung bitten, bevor Sie die automatische Protokollierung aktivieren.

Sie verwalten die Protokollierung mit zwei Eigenschaften.

-   Aktivieren Sie die Protokollierung mit der **IpcCustomerExperienceDataCollectionEnabled**-Eigenschaft. Die Einstellung ist für alle Gerätezurücksetzungen gleich.
-   Steuern Sie die Protokollierungsebene mit der **IpcLogLevel**-Eigenschaft, indem Sie die folgenden Einstellungen verwenden:

    * 1 – Ausführlich
    * 2 – Information
    * 3 – Warnung
    * 4 – Fehler
    * 5 – Kritisch

In allen folgenden Beispielcodeausschnitten kann die aufrufende Anwendung die Eigenschaft festlegen oder abfragen.

### Android ###
Automatische Protokollierung aktivieren

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    SharedPreferences.Editor editor = preferences.edit();
    editor.putBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, true);
    editor.commit();

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

    SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
    Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);

## iOS ##
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
 

## Windows ##
Automatische Protokollierung aktivieren

    CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;

Weitere Informationen zu optionalen Einstellungen finden Sie unter [CustomerExperienceOptions](/rights-management/sdk/4.2/api/winrt/Microsoft.RightsManagement#msipcthin2_customerexperienceoptions).

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

    CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;


**Hinweis**: Die obigen Windows-Codeausschnitte sind in C++ geschrieben. Aktualisieren Sie die Syntax für C\# mit „.“ anstelle von „::“.

**Linux/C++**: Dieses SDK verfügt über einige grundlegende Funktionen für die Protokollierung, die nicht so umfangreich wie die Funktionen anderer Plattformen sind. Weitere Informationen finden Sie im Abschnitt **Troubleshooting** der Datei „README.md“ unter [RMS SDK for portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting) (RMS SDK für portables C++).

 

 


<!--HONumber=Apr16_HO4-->


