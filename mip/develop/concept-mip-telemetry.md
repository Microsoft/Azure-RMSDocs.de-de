---
title: 'Konzepte: die grundlegenden Konzepte im MIP SDK-Telemetrie-Steuerelement'
description: In diesem Artikel erfahren Sie, wie Sie die Telemetrie abonnieren und welche Ereignisse weiterhin gesendet werden, wenn Sie sich abmelden.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.date: 10/01/2019
ms.author: tommos
ms.openlocfilehash: 22f98a6781dc0ff0b43d1da73c72c2029c960021
ms.sourcegitcommit: 36413b0451ae28045193c04cbe2d3fb2270e9773
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/15/2020
ms.locfileid: "86403373"
---
# <a name="microsoft-information-protection-sdk---telemetry-configuration"></a>Microsoft Information Protection SDK-telemetriekonfiguration

## <a name="telemetry"></a>Telemetrie

Standardmäßig sendet das Microsoft Information Protection SDK Telemetriedaten an Microsoft. Diese Telemetriedaten sind nützlich für die Behandlung von Fehlern, Qualitäts-und Leistungsproblemen in der SDK-Installationsbasis, die bei unseren internen Tests möglicherweise nicht erfasst werden. Wenn Sie Ihre Anwendung mit dem SDK implementieren, ist es wichtig, Benutzern und Administratoren die Möglichkeit zu einräumen, die Telemetriedaten bei Bedarf zu entscheiden.

## <a name="telemetry-configuration"></a>Telemetriekonfiguration

Telemetrieoptionen im MIP SDK können über [telemetryconfiguration](https://docs.microsoft.com/dotnet/api/microsoft.informationprotection.telemetryconfiguration?view=mipsdk-dotnet)gesteuert werden. Erstellen Sie eine Instanz dieser Klasse, und legen Sie dann **istelemetryoptedout** auf true fest. Geben Sie das Objekt der Klasse **telemetryconfiguration** der Funktion an, die zum Erstellen von **mipcontext**verwendet wird.

Beginnend mit der MIP SDK-Version 1,6 deaktiviert die Einstellungs Option die Telemetrie **vollständig** . In Verisons 1,5 und früher senden wir einen Satz von minimalen Telemetriedaten.

### <a name="minimum-telemetry-events"></a>Minimale telemetrieereignisse

Wenn für die Telemetrie in MIP SDK 1,6 und höher der Wert für die *Abmeldung*festgelegt ist, **werden keine telemetrieereignisse gesendet.** Versionen vor 1,6 weisen folgendes Verhalten auf.

Wenn für die Telemetrie festgelegt ist, wird ein minimal Satz an *Daten an Microsoft*gesendet. Alle persönlich identifizierbaren Informationen werden anhand dieser Informationen bereinigt. Diese Daten enthalten Takt Informationen, um zu verstehen, dass das SDK verwendet wird, und System Metadaten. **Es sind keine Benutzerinhalte oder Endbenutzer identifizierbaren Informationen auf den Dienst festgelegt.**

Überprüfen Sie die folgenden Tabellen, um genau zu sehen, welche Ereignisse und Daten mit dem minimalen telemetriesatz gesendet werden.

#### <a name="event-heartbeat"></a>Ereignis: Takt

| Name                                 | BESCHREIBUNG                                                                            | Bereinigt |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------- |
| App. ApplicationId                    | Der Anwendungs Bezeichner, der über MIP:: ApplicationInfo bereitgestellt wird.                          | Nein       |
| App. ApplicationName                  | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | Nein       |
| App. applicationVersion               | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | Nein       |
| ApplicationId                        | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | Nein       |
| ApplicationName                      | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | Nein       |
| CreationTime                         | Das Zeit Ereignis wurde generiert.                                                              | Nein       |
| DefaultLabel.Id                      | Standard-ID der Mandanten Bezeichnung.                                                               | Nein       |
| Engine. tenantid                      | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | Nein       |
| Engine. userobjectid                  | Benutzerobjekt-ID in Azure Active Directory.                                              | Nein       |
| Event. CorrelationId                  | Generierte eindeutige ID, die dem Objekt zugeordnet ist, das das Ereignis ausgelöst hat.                   | Nein       |
| Event. correlationiddescription       | Der Name der C++-Klasse des Objekts, das das Ereignis ausgelöst hat.                                     | Nein       |
| Event. parametricorrelationid            | Korrelation-ID des übergeordneten Ereignisses.                                                           | Nein       |
| Event. parametricorrelationiddescription | Es wurde eine eindeutige ID generiert, die dem übergeordneten Objekt zugeordnet ist, das das Ereignis ausgelöst hat. | Nein       |
| Event. UniqueId                       | Generierte eindeutige ID, die dem Ereignis zugewiesen ist.                                             | Nein       |
| MachineName                          | Der Name des Systems, das das Ereignis generiert hat.                                           | **Ja**  |
| MIP. Version                          | Version des MIP SDK.                                                                | Nein       |
| Vorgang                            | Heartbeat                                                                              | Nein       |
| OrganizationId                       | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | Nein       |
| Plattform                             | Betriebssystemversion.                                                              | Nein       |
| ProcessName                          | Der Name des Prozesses mit dem SDK.                                                     | Nein       |
| ProductVersion                       | Identisch mit "App. applicationVersion".                                                      | Nein       |
| SDKVersion                           | Identisch mit MIP. Version.                                                                   | Nein       |
| UserId                               | E-Mail-Adresse des Benutzers                                                             | **Ja**  |
| UserObjectId                         | Azure AD Objekt-ID des Benutzers.                                                        | Nein       |
| Version                              | Audit Version Schema ("1,1").                                                          | Nein       |

#### <a name="event-discovery"></a>Ereignis: Ermittlung

| Name                                 | BESCHREIBUNG                                                                            | Bereinigt |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------- |
| ActionID                             | Eindeutige Aktions-ID für dieses Ereignis, die für die Ereignis Korrelation verwendet wird.                           | Nein       |
| App. ApplicationId                    | Der Anwendungs Bezeichner, der über MIP:: ApplicationInfo bereitgestellt wird.                          | Nein       |
| App. ApplicationName                  | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | Nein       |
| App. applicationVersion               | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | Nein       |
| ApplicationId                        | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | Nein       |
| ApplicationName                      | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | Nein       |
| CreationTime                         | Das Zeit Ereignis wurde generiert.                                                              | Nein       |
| Datastate                            | Der Zustand der Daten, während die Anwendung auf "Rest", "Motion", "Use" agiert.           | Nein       |
| DefaultLabel.Id                      | Standard Bezeichner der Mandanten Bezeichnung.                                                       | Nein       |
| Engine. tenantid                      | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | Nein       |
| Engine. userobjectid                  | Benutzerobjekt Bezeichner in Azure Active Directory.                                      | Nein       |
| Event. CorrelationId                  | Generierte eindeutige ID, die dem Objekt zugeordnet ist, das das Ereignis ausgelöst hat.                   | Nein       |
| Event. correlationiddescription       | Der Name der C++-Klasse des Objekts, das das Ereignis ausgelöst hat.                                     | Nein       |
| Event. parametricorrelationid            | Korrelation-ID des übergeordneten Ereignisses.                                                           | Nein       |
| Event. parametricorrelationiddescription | Es wurde eine eindeutige ID generiert, die dem übergeordneten Objekt zugeordnet ist, das das Ereignis ausgelöst hat. | Nein       |
| Event. UniqueId                       | Generierte eindeutige ID, die dem Ereignis zugewiesen ist.                                             | Nein       |
| LabelId                              | Der Bezeichner für die Inhalts Bezeichnung der geöffneten Datei oder der geöffneten Daten.                                   | Nein       |
| MachineName                          | Der Name des Systems, das das Ereignis generiert hat.                                           | **Ja**  |
| MIP. Version                          | Version des MIP SDK.                                                                | Nein       |
| ObjectId                             | Dateipfad/Beschreibung der Datei oder der Daten.                                             | **Ja**  |
| Vorgang                            | "Ermittlung".                                                                           | Nein       |
| OrganizationId                       | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | Nein       |
| Plattform                             | Betriebssystemversion.                                                              | Nein       |
| ProcessName                          | Der Name des Prozesses mit dem SDK.                                                     | Nein       |
| Protected                            | Boolescher Wert, der angibt, ob die Datei geschützt ist.                                       | Nein       |
| Schutz                           | Der Schutz Vorlagen Bezeichner.                                                    | **Ja**  |
| Schutz Besitzer                      | E-Mail-Adresse des Schutz Besitzers.                                                 | **Ja**  |
| SDKVersion                           | Identisch mit MIP. Version.                                                                   | Nein       |
| UserId                               | E-Mail-Adresse des Benutzers                                                             | **Ja**  |
| UserObjectId                         | Azure AD Objekt-ID des Benutzers.                                                        | Nein       |
| Version                              | Audit Version Schema ("1,1").                                                          | Nein       |

#### <a name="event-label-change"></a>Ereignis: Bezeichnungs Änderung

| Name                                 | BESCHREIBUNG                                                                            | Bereinigt |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------- |
| ActionID                             | Eindeutige Aktions-ID für dieses Ereignis, die für die Ereignis Korrelation verwendet wird.                           | Nein       |
| "Aktionidbefore"                       | Vorherige Aktions-ID. Wird zum Verketten zur neuen Aktions-ID verwendet.                                    | Nein       |
| Aktions Quelle                         | Der Wert MIP:: aktionsource.                                                            | Nein       |
| App. ApplicationId                    | Die Anwendungs-ID, die über MIP:: ApplicationInfo bereitgestellt wird.                                  | Nein       |
| App. ApplicationName                  | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | Nein       |
| App. applicationVersion               | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | Nein       |
| ApplicationId                        | Die Anwendungs-ID, die über MIP:: ApplicationInfo bereitgestellt wird.                                  | Nein       |
| ApplicationName                      | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | Nein       |
| CreationTime                         | Die Uhrzeit, zu der das Ereignis generiert wurde.                                                          | Nein       |
| Datastate                            | Der Zustand der Daten, während die Anwendung auf "Rest", "Motion", "Use" agiert.           | Nein       |
| DefaultLabel.Id                      | Standard Bezeichner der Mandanten Bezeichnung.                                                       | Nein       |
| Engine. tenantid                      | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | Nein       |
| Engine. userobjectid                  | Benutzerobjekt Bezeichner in Azure Active Directory.                                      | Nein       |
| Event. CorrelationId                  | Generierte eindeutige ID, die dem Objekt zugeordnet ist, das das Ereignis ausgelöst hat.                   | Nein       |
| Event. correlationiddescription       | Der Name der C++-Klasse des Objekts, das das Ereignis ausgelöst hat.                                     | Nein       |
| Event. parametricorrelationid            | Korrelation-ID des übergeordneten Ereignisses.                                                           | Nein       |
| Event. parametricorrelationiddescription | Es wurde eine eindeutige ID generiert, die dem übergeordneten Objekt zugeordnet ist, das das Ereignis ausgelöst hat. | Nein       |
| Event. UniqueId                       | Generierte eindeutige ID, die dem Ereignis zugewiesen ist.                                             | Nein       |
| Islabelchanged                       | Boolescher Wert, der angibt, ob die Bezeichnung geändert                                                  | Nein       |
| Isprotectionchanged                  | Bool, das angibt, ob der Schutz geändert wurde.                                                 | Nein       |
| LabelId                              | Bezeichnungs-ID, die auf die Datei oder die Daten angewendet werden soll.                                    | Nein       |
| Labelidbefore                        | ID der vorherigen Bezeichnung, die in der Datei oder den Daten gespeichert war.                                        | Nein       |
| MachineName                          | Der Name des Systems, das das Ereignis generiert hat.                                           | **Ja**  |
| MIP. Version                          | Version des MIP SDK.                                                                | Nein       |
| ObjectId                             | Dateipfad/Beschreibung der Datei oder der Daten.                                             | **Ja**  |
| Vorgang                            | "Ändern".                                                                              | Nein       |
| OrganizationId                       | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | Nein       |
| Plattform                             | Betriebssystemversion.                                                              | Nein       |
| ProcessName                          | Der Name des Prozesses mit dem SDK.                                                     | Nein       |
| Produktversion                      |                                                                                        | Nein       |
| Protected                            | Boolescher Wert, der angibt, ob die Datei geschützt ist.                                       | Nein       |
| Geschützt vor                     | Boolescher Wert, der angibt, ob die Datei zuvor geschützt war.                           | Nein       |
| Schutz                           | Der Schutz Vorlagen Bezeichner.                                                    | Nein       |
| Schutz vor                    | Der vorherige Schutz Vorlagen Bezeichner.                                           | Nein       |
| Schutzcontentid                  | Der neue Inhalts Bezeichner (GUID).                                                     | Nein       |
| Schutzcontentidbefore            | Der vorherige Inhalts Bezeichner (GUID).                                                | Nein       |
| Schutz Besitzer                      | E-Mail-Adresse des Schutz Besitzers.                                                 | **Ja**  |
| Schutz Eigentümer vor                | Vorherige e-Mail-Adresse des Schutz Besitzers.                                        | **Ja**  |
| SDKVersion                           | Identisch mit MIP. Version.                                                                   | Nein       |
| UserId                               | E-Mail-Adresse des Benutzers                                                             | **Ja**  |
| UserObjectId                         | Azure AD Objekt-ID des Benutzers.                                                        | Nein       |
| Version                              | Audit Version Schema ("1,1").                                                          | Nein       |


### <a name="opting-out-in-c"></a>Opt out in C++

Um nur die Telemetrie auf minimal festzulegen, erstellen Sie einen freigegebenen Zeiger von **MIP:: telemetryconfiguration ()** , und legen Sie **istelemetryoptedout** auf true fest. Übergeben Sie das Konfigurationsobjekt in an **mipcontent:: Create ()**.

```cpp
auto telemetryConfig = std::make_shared<mip::TelemetryConfiguration>();                                     
telemetryConfig->isTelemetryOptedOut = true;
                       
// Create MipContext, passing in mip::TelemetryConfiguration object.
mMipContext = mip::MipContext::Create(
    mAppInfo,
    "mip_data",
    mip::LogLevel::Trace,
    false,
    nullptr /*loggerDelegateOverride*/,
    telemetryConfig /*telemetryOverride*/
);
```

### <a name="opting-out-in-net"></a>Ablehnen in .net

Um nur die Telemetrie auf minimal festzulegen, erstellen Sie ein **telemetryconfiguration ()** -Objekt, und legen Sie **istelemetryoptedout** auf true fest. Übergeben Sie das Konfigurationsobjekt in **MIP. "Kreatemipcontext ()**".

```csharp
TelemetryConfiguration telemetryConfiguration = new TelemetryConfiguration();
telemetryConfiguration.IsTelemetryOptedOut = true;

// Create MipContext, passing in TelemetryConfiguration object.
mipContext = MIP.CreateMipContext(appInfo, 
    "mip_data", 
    LogLevel.Trace, 
    null, 
    telemetryConfiguration);
```

