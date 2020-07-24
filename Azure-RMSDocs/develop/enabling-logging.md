---
title: Gewusst wie&#58; Aktivieren der Fehler- und Leistungsprotokollierung | Azure RMS
description: Mit dem Microsoft Rights Management SDK 4.2 wird das Hochladen von Diagnose- und Leistungsprotokollen über eine einzelne Geräteeigenschaft verwaltet.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: F5AD3826-2292-4A25-AF5C-D17D083F5742
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: 4a9f0b375f9e152d44f4d5b5251a9259456db53c
ms.sourcegitcommit: 84b45c949d85a7291c088a050d2a66d356fc9af2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2020
ms.locfileid: "87135707"
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
> *Durch Aktivieren der Fehler-und Leistungs Protokollierung Stimmen Sie zu, Fehler-und Leistungsdaten an Microsoft zu senden.  Microsoft sammelt Fehler-und Leistungsdaten über das Internet ("Daten").  Microsoft verwendet diese Daten, um die Qualität, Sicherheit und Integrität von Microsoft-Produkten und-Diensten sicherzustellen und zu verbessern.  Beispielsweise analysieren wir die Leistung und Zuverlässigkeit, wie z. b. welche Features Sie verwenden, wie schnell die Features Antworten, die Geräteleistung, Interaktionen mit der Benutzeroberfläche und alle Probleme, die mit dem Produkt auftreten können.  Zu den Daten gehören auch Informationen zur Konfiguration Ihrer Software, wie z. b. die Software, die Sie gerade ausführen, und die IP-Adresse.*  

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

```java
SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
SharedPreferences.Editor editor = preferences.edit();
editor.putBoolean("IpcCustomerExperienceDataCollectionEnabled", true);
editor.commit();
```

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

```java
SharedPreferences preferences = PreferenceManager.getDefaultSharedPreferences(context);
Boolean isLogUploadEnabled = preferences.getBoolean(&quot;IpcCustomerExperienceDataCollectionEnabled&quot;, false);
```

## <a name="ios"></a>iOS ##
Automatische Protokollierung aktivieren

```objectivec
NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
    [prefs setBool:FALSE forKey:@"IpcCustomerExperienceDataCollectionEnabled"];
    [[NSUserDefaults standardUserDefaults] synchronize];
```

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

```java
[[NSUserDefaults standardUserDefaults] boolForKey:@"IpcCustomerExperienceDataCollectionEnabled"];
```

Protokollebenensteuerung festlegen

```java
NSUserDefaults \*prefs = [NSUserDefaults standardUserDefaults];
    [prefs setInteger:1 forKey:@"IpcLogLevel"];
    [[NSUserDefaults standardUserDefaults] synchronize];
```

Einstellung für Protokollebenensteuerung abrufen

```java
[[NSUserDefaults standardUserDefaults] boolForKey:@"IpcLogLevel"];
```

## <a name="windows"></a>Windows ##
Automatische Protokollierung aktivieren

```cpp
CustomerExperienceConfiguration::Option = CustomerExperienceOptions::LoggingEnabledNow;
```

Weitere Informationen zu optionalen Einstellungen finden Sie unter [CustomerExperienceOptions](https://msdn.microsoft.com/library/microsoft.rightsmanagement.customerexperienceoptions.aspx).

Aktuelle Einstellung für Protokollierungssteuerungs-Flag abrufen

```cpp
CustomerExperienceOptions loggingOption = CustomerExperienceConfiguration::Option;
```

**Hinweis**: Die obigen Windows-Codeausschnitte sind in C++ geschrieben. Aktualisieren Sie die Syntax für C\# mit „.“ anstelle von „::“.

**Linux/C++**: Dieses SDK verfügt über einige grundlegende Funktionen für die Protokollierung, die nicht so umfangreich wie die Funktionen anderer Plattformen sind. Weitere Informationen finden Sie im Abschnitt **Troubleshooting** der Datei „README.md“ unter [RMS SDK for portable C++](https://github.com/AzureAD/rms-sdk-for-cpp#troubleshooting) (RMS SDK für portables C++).
