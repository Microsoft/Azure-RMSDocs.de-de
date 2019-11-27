---
title: 'Konzepte: die grundlegenden Konzepte im MIP SDK-Telemetrie-Steuerelement'
description: In diesem Artikel erfahren Sie, wie Sie die Telemetrie abonnieren und welche Ereignisse weiterhin gesendet werden, wenn Sie sich abmelden.
author: tommoser
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 10/01/2019
ms.author: tommos
ms.openlocfilehash: 3d97bdbf5307d7f0faefe6b6434b1df1ebc67798
ms.sourcegitcommit: 487e681c9683b8adb7ae6fcfb374830bf0e5ad72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/25/2019
ms.locfileid: "74484852"
---
# <a name="microsoft-information-protection-sdk---telemetry-configuration"></a>Microsoft Information Protection SDK-telemetriekonfiguration

## <a name="telemetry"></a>Telemetrie

Standardmäßig sendet das Microsoft Information Protection SDK Telemetriedaten an Microsoft. Diese Telemetriedaten sind nützlich für die Behandlung von Fehlern, Qualitäts-und Leistungsproblemen in der SDK-Installationsbasis, die bei unseren internen Tests möglicherweise nicht erfasst werden. Wenn Sie Ihre Anwendung mit dem SDK implementieren, ist es wichtig, Benutzern und Administratoren die Möglichkeit zu einräumen, die Telemetriedaten bei Bedarf zu entscheiden.

## <a name="telemetry-configuration"></a>Telemetriekonfiguration

Telemetrieoptionen im MIP SDK können über [telemetryconfiguration](https://docs.microsoft.com/dotnet/api/microsoft.informationprotection.telemetryconfiguration?view=mipsdk-dotnet)gesteuert werden. Erstellen Sie eine Instanz dieser Klasse, und legen Sie dann **istelemetryoptedout** auf true fest. Geben Sie das Objekt der Klasse **telemetryconfiguration** der Funktion an, die zum Erstellen von **mipcontext**verwendet wird. Dadurch werden Telemetriedaten nicht vollständig eliminiert, aber auf einen minimalen Satz reduziert, bei dem alle identifizierbaren Endbenutzer Informationen bereinigt werden.

### <a name="minimum-telemetry-events"></a>Minimale telemetrieereignisse

Wenn für die Telemetrie festgelegt ist, wird ein minimal Satz an *Daten an Microsoft*gesendet. Alle persönlich identifizierbaren Informationen werden anhand dieser Informationen bereinigt. Diese Daten enthalten Takt Informationen, um zu verstehen, dass das SDK verwendet wird, und System Metadaten. **Es sind keine Benutzerinhalte oder Endbenutzer identifizierbaren Informationen auf den Dienst festgelegt.**

Überprüfen Sie die folgenden Tabellen, um genau zu sehen, welche Ereignisse und Daten mit dem minimalen telemetriesatz gesendet werden.

#### <a name="event-heartbeat"></a>Ereignis: Takt

| Name                                 | Description                                                                            | Bereinigt |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------- |
| App. ApplicationId                    | Der Anwendungs Bezeichner, der über MIP:: ApplicationInfo bereitgestellt wird.                          | nein       |
| App. ApplicationName                  | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | nein       |
| App. applicationVersion               | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | nein       |
| ApplicationId                        | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | nein       |
| ApplicationName                      | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | nein       |
| CreationTime                         | Das Zeit Ereignis wurde generiert.                                                              | nein       |
| DefaultLabel.Id                      | Standard-ID der Mandanten Bezeichnung.                                                               | nein       |
| Engine. tenantid                      | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | nein       |
| Engine. userobjectid                  | Benutzerobjekt-ID in Azure Active Directory.                                              | nein       |
| Event. CorrelationId                  | Generierte eindeutige ID, die dem Objekt zugeordnet ist, das das Ereignis ausgelöst hat.                   | nein       |
| Event. correlationiddescription       | C++der Klassenname des Objekts, das das Ereignis ausgelöst hat.                                     | nein       |
| Event. parametricorrelationid            | Korrelation-ID des übergeordneten Ereignisses.                                                           | nein       |
| Event. parametricorrelationiddescription | Es wurde eine eindeutige ID generiert, die dem übergeordneten Objekt zugeordnet ist, das das Ereignis ausgelöst hat. | nein       |
| Event. UniqueId                       | Generierte eindeutige ID, die dem Ereignis zugewiesen ist.                                             | nein       |
| MachineName                          | Der Name des Systems, das das Ereignis generiert hat.                                           | **Ja**  |
| MIP. Version                          | Version des MIP SDK.                                                                | nein       |
| Vorgang                            | Takt                                                                              | nein       |
| OrganizationId                       | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | nein       |
| Platform                             | Betriebssystemversion.                                                              | nein       |
| ProcessName                          | Der Name des Prozesses mit dem SDK.                                                     | nein       |
| ProductVersion                       | Identisch mit "App. applicationVersion".                                                      | nein       |
| SDKVersion                           | Identisch mit MIP. Version.                                                                   | nein       |
| UserId                               | E-Mail-Adresse des Benutzers                                                             | **Ja**  |
| UserObjectId                         | Azure AD Objekt-ID des Benutzers.                                                        | nein       |
| Version                              | Audit Version Schema ("1,1").                                                          | nein       |

#### <a name="event-discovery"></a>Ereignis: Ermittlung

| Name                                 | Description                                                                            | Bereinigt |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------- |
| ActionID                             | Eindeutige Aktions-ID für dieses Ereignis, die für die Ereignis Korrelation verwendet wird.                           | nein       |
| App. ApplicationId                    | Der Anwendungs Bezeichner, der über MIP:: ApplicationInfo bereitgestellt wird.                          | nein       |
| App. ApplicationName                  | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | nein       |
| App. applicationVersion               | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | nein       |
| ApplicationId                        | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | nein       |
| ApplicationName                      | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | nein       |
| CreationTime                         | Das Zeit Ereignis wurde generiert.                                                              | nein       |
| datastate                            | Der Zustand der Daten, während die Anwendung auf "Rest", "Motion", "Use" agiert.           | nein       |
| DefaultLabel.Id                      | Standard Bezeichner der Mandanten Bezeichnung.                                                       | nein       |
| Engine. tenantid                      | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | nein       |
| Engine. userobjectid                  | Benutzerobjekt Bezeichner in Azure Active Directory.                                      | nein       |
| Event. CorrelationId                  | Generierte eindeutige ID, die dem Objekt zugeordnet ist, das das Ereignis ausgelöst hat.                   | nein       |
| Event. correlationiddescription       | C++der Klassenname des Objekts, das das Ereignis ausgelöst hat.                                     | nein       |
| Event. parametricorrelationid            | Korrelation-ID des übergeordneten Ereignisses.                                                           | nein       |
| Event. parametricorrelationiddescription | Es wurde eine eindeutige ID generiert, die dem übergeordneten Objekt zugeordnet ist, das das Ereignis ausgelöst hat. | nein       |
| Event. UniqueId                       | Generierte eindeutige ID, die dem Ereignis zugewiesen ist.                                             | nein       |
| LabelId                              | Der Bezeichner für die Inhalts Bezeichnung der geöffneten Datei oder der geöffneten Daten.                                   | nein       |
| MachineName                          | Der Name des Systems, das das Ereignis generiert hat.                                           | **Ja**  |
| MIP. Version                          | Version des MIP SDK.                                                                | nein       |
| ObjectID                             | Dateipfad/Beschreibung der Datei oder der Daten.                                             | **Ja**  |
| Vorgang                            | "Ermittlung".                                                                           | nein       |
| OrganizationId                       | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | nein       |
| Platform                             | Betriebssystemversion.                                                              | nein       |
| ProcessName                          | Der Name des Prozesses mit dem SDK.                                                     | nein       |
| Geschützt                            | Boolescher Wert, der angibt, ob die Datei geschützt ist.                                       | nein       |
| Schutz                           | Der Schutz Vorlagen Bezeichner.                                                    | **Ja**  |
| Schutz Besitzer                      | E-Mail-Adresse des Schutz Besitzers.                                                 | **Ja**  |
| SDKVersion                           | Identisch mit MIP. Version.                                                                   | nein       |
| UserId                               | E-Mail-Adresse des Benutzers                                                             | **Ja**  |
| UserObjectId                         | Azure AD Objekt-ID des Benutzers.                                                        | nein       |
| Version                              | Audit Version Schema ("1,1").                                                          | nein       |

#### <a name="event-label-change"></a>Ereignis: Bezeichnungs Änderung

| Name                                 | Description                                                                            | Bereinigt |
| ------------------------------------ | -------------------------------------------------------------------------------------- | -------- |
| ActionID                             | Eindeutige Aktions-ID für dieses Ereignis, die für die Ereignis Korrelation verwendet wird.                           | nein       |
| "Aktionidbefore"                       | Vorherige Aktions-ID. Wird zum Verketten zur neuen Aktions-ID verwendet.                                    | nein       |
| Aktions Quelle                         | Der Wert MIP:: aktionsource.                                                            | nein       |
| App. ApplicationId                    | Die Anwendungs-ID, die über MIP:: ApplicationInfo bereitgestellt wird.                                  | nein       |
| App. ApplicationName                  | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | nein       |
| App. applicationVersion               | Die Anwendungs Version, die über MIP:: ApplicationInfo profitet wird.                             | nein       |
| ApplicationId                        | Die Anwendungs-ID, die über MIP:: ApplicationInfo bereitgestellt wird.                                  | nein       |
| ApplicationName                      | Der über MIP:: ApplicationInfo bereitgestellte Anwendungsname.                                | nein       |
| CreationTime                         | Uhrzeit, zu der das Ereignis generiert wurde.                                                          | nein       |
| datastate                            | Der Zustand der Daten, während die Anwendung auf "Rest", "Motion", "Use" agiert.           | nein       |
| DefaultLabel.Id                      | Standard Bezeichner der Mandanten Bezeichnung.                                                       | nein       |
| Engine. tenantid                      | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | nein       |
| Engine. userobjectid                  | Benutzerobjekt Bezeichner in Azure Active Directory.                                      | nein       |
| Event. CorrelationId                  | Generierte eindeutige ID, die dem Objekt zugeordnet ist, das das Ereignis ausgelöst hat.                   | nein       |
| Event. correlationiddescription       | C++der Klassenname des Objekts, das das Ereignis ausgelöst hat.                                     | nein       |
| Event. parametricorrelationid            | Korrelation-ID des übergeordneten Ereignisses.                                                           | nein       |
| Event. parametricorrelationiddescription | Es wurde eine eindeutige ID generiert, die dem übergeordneten Objekt zugeordnet ist, das das Ereignis ausgelöst hat. | nein       |
| Event. UniqueId                       | Generierte eindeutige ID, die dem Ereignis zugewiesen ist.                                             | nein       |
| Islabelchanged                       | Boolescher Wert, der angibt, ob die Bezeichnung geändert                                                  | nein       |
| Isprotectionchanged                  | Bool, das angibt, ob der Schutz geändert wurde.                                                 | nein       |
| LabelId                              | Bezeichnungs-ID, die auf die Datei oder die Daten angewendet werden soll.                                    | nein       |
| LabelIdBefore                        | ID der vorherigen Bezeichnung, die in der Datei oder den Daten gespeichert war.                                        | nein       |
| MachineName                          | Der Name des Systems, das das Ereignis generiert hat.                                           | **Ja**  |
| MIP. Version                          | Version des MIP SDK.                                                                | nein       |
| ObjectID                             | Dateipfad/Beschreibung der Datei oder der Daten.                                             | **Ja**  |
| Vorgang                            | "Ändern".                                                                              | nein       |
| OrganizationId                       | Privat Mandanten-GUID des authentifizierten Benutzers.                                            | nein       |
| Platform                             | Betriebssystemversion.                                                              | nein       |
| ProcessName                          | Der Name des Prozesses mit dem SDK.                                                     | nein       |
| Produktversion                      |                                                                                        | nein       |
| Geschützt                            | Boolescher Wert, der angibt, ob die Datei geschützt ist.                                       | nein       |
| Geschützt vor                     | Boolescher Wert, der angibt, ob die Datei zuvor geschützt war.                           | nein       |
| Schutz                           | Der Schutz Vorlagen Bezeichner.                                                    | nein       |
| Schutz vor                    | Der vorherige Schutz Vorlagen Bezeichner.                                           | nein       |
| Schutzcontentid                  | Der neue Inhalts Bezeichner (GUID).                                                     | nein       |
| Schutzcontentidbefore            | Der vorherige Inhalts Bezeichner (GUID).                                                | nein       |
| Schutz Besitzer                      | E-Mail-Adresse des Schutz Besitzers.                                                 | **Ja**  |
| ProtectionOwnerBefore                | Vorherige e-Mail-Adresse des Schutz Besitzers.                                        | **Ja**  |
| SDKVersion                           | Identisch mit MIP. Version.                                                                   | nein       |
| UserId                               | E-Mail-Adresse des Benutzers                                                             | **Ja**  |
| UserObjectId                         | Azure AD Objekt-ID des Benutzers.                                                        | nein       |
| Version                              | Audit Version Schema ("1,1").                                                          | nein       |


### <a name="opting-out-in-c"></a>Opt out inC++

Um nur die Telemetrie auf minimal festzulegen, erstellen Sie einen freigegebenen Zeiger von **MIP:: telemetryconfiguration ()** , und legen Sie **istelemetryoptedout** auf true fest. Übergeben Sie das Konfigurationsobjekt in an **mipcontent:: Create ()** .

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

Um nur die Telemetrie auf minimal festzulegen, erstellen Sie ein **telemetryconfiguration ()** -Objekt, und legen Sie **istelemetryoptedout** auf true fest. Übergeben Sie das Konfigurationsobjekt in **MIP. "Kreatemipcontext ()** ".

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

