---
title: 'Schnellstart: Schutz des Active Directory-Rechteverwaltungsservers'
description: Diese Schnellstartanleitung zeigt, wie Sie das MIP SDK für die Verwendung des Active Directory-Rechteverwaltungsservers (AD RMS) konfigurieren.
author: tommoser
ms.service: information-protection
ms.topic: quickstart
ms.date: 04/17/2019
ms.author: tommos
ms.custom: has-adal-ref
ms.openlocfilehash: cf76a81525d06cf987f24d1966b85ade78f8f8ff
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91588290"
---
# <a name="quickstart-active-directory-rights-management-server-ad-rms-protection"></a>Schnellstart: Schutz des Active Directory-Rechteverwaltungsservers (AD RMS)

Diese Schnellstartanleitung zeigt, wie Sie die Unterstützung für den Active Directory-Rechteverwaltungsserver (AD RMS) mit dem MIP SDK implementieren.

> [!NOTE]
> Die hier beschriebenen Schritte gelten nur für die Datei-API für C# oder C++ und die Schutz-API für C++.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie Folgendes sicher, sofern dies noch nicht geschehen ist:

- Schließen Sie zuerst den [Schnellstart für die Initialisierung der Clientanwendung (C++)](quick-app-initialization-cpp.md) ab, in dem Sie eine Visual Studio-Projektmappe für den Einstieg erstellen.
- Schließen Sie zuerst den [Schnellstart Auflisten der Vertraulichkeitsbezeichnungen (C++)](quick-file-list-labels-cpp.md) oder den [Schnellstart: Auflisten von Vertraulichkeitsbezeichnungen (C#)](quick-file-list-labels-csharp.md) ab.
- Stellen Sie AD RMS mit [Mobilgeräteerweiterung](/azure/information-protection/active-directory-rights-manage-mobile-device) bereit.
- Stellen Sie optional sicher, dass der [DNS SRV-Eintrag für AD RMS MDE](/azure/information-protection/active-directory-rights-manage-mobile-device#specifying-the-dns-srv-records-for-the-ad-rms-mobile-device-extension) veröffentlicht wurde.

## <a name="service-discovery"></a>Dienstermittlung

Das SDK führt eine Dienstermittlung basierend auf dem über `FileEngineSettings` oder `ProtectionEngineSettings` bereitgestellten `mip::Identity`-Element aus. Dabei wird der UPN oder das E-Mail-Adresssuffix verwendet. Zuerst wird in der Domänenhierarchie nach dem *_rmsdisco*-Eintrag für MDE gesucht. Weitere Informationen zu diesem Prozess finden Sie unter [Festlegen der DNS SRV-Einträge für die AD RMS-Mobilgeräteerweiterung](/azure/information-protection/active-directory-rights-manage-mobile-device#specifying-the-dns-srv-records-for-the-ad-rms-mobile-device-extension). Wenn dieser DNS SRV-Eintrag nicht gefunden wird, wird als Dienststandort standardmäßig der Azure Information Protection-Dienst verwendet.

Wenn keine Identität verfügbar ist oder der DNS SRV-Eintrag für MDE nicht veröffentlicht wurde, kann der Dienstermittlungsprozess außer Kraft gesetzt werden, indem explizit der [Cloudendpunkt-URL](./reference/class_mip_fileengine_settings.md#setpolicycloudendpointbaseurl-function) festgelegt wird.

## <a name="configuring-file-api-in-c-to-use-ad-rms"></a>Konfigurieren der Datei-API in C# zur Verwendung von AD RMS

Wenn Ihre Anwendung die Active Directory-Authentifizierungsbibliothek (Active Directory Authentication Library, ADAL) und die Datei-API in C# verwendet, sind zwei geringfügige Änderungen erforderlich. Das `FileEngineSettings`-Objekt und der `AuthenticationContext`-Konstruktor müssen aktualisiert werden, damit sie mit AD RMS und den Active Directory-Verbunddiensten (AD FS) funktionieren.

Wenn Sie den DNS SRV-Eintrag für die Mobilgeräteerweiterung bereitgestellt haben und planen, einen Benutzerprinzipalnamen oder eine E-Mail-Adresse zu übergeben, [befolgen Sie die Anweisungen zum Verwenden einer Identität](#update-the-file-engine-settings-to-use-ad-rms-with-an-identity).

Wenn Sie nicht über den DNS SRV-Eintrag für die Mobilgeräteerweiterung verfügen oder zur Laufzeit keine Identität zur Verfügung stehen wird, [befolgen Sie die Anweisungen zur expliziten Angabe eines Endpunkts](#update-the-file-engine-settings-to-use-ad-rms-with-an-explicit-endpoint).

### <a name="update-the-file-engine-settings-to-use-ad-rms-with-an-identity"></a>Aktualisieren der Datei-Engine-Einstellungen für die Verwendung von AD RMS mit einer Identität

Wenn der DNS SRV-Eintrag für MDE veröffentlicht und `Microsoft.InformationProtection.Identity` als Teil der Engine-Einstellungen angegeben wurde, besteht die einzige erforderliche Codeänderung darin, `FileEngineSettings.ProtectionOnlyEngine = true` festzulegen. Diese Eigenschaft muss festgelegt werden, weil Bezeichnungsvorgänge (Richtlinie) für Endpunkte für den AD RMS-Schutz nicht unterstützt werden.

```csharp
// Configure FileEngineSettings as protection only engine.
var engineSettings = new FileEngineSettings("", authDelegate, "", "en-US")
{
     // Provide the identity for service discovery.
     Identity = identity,
     // Set ProtectionOnlyEngine to true for AD RMS as labeling isn't supported
     ProtectionOnlyEngine = true
};
```

### <a name="update-the-file-engine-settings-to-use-ad-rms-with-an-explicit-endpoint"></a>Aktualisieren der Datei-Engine-Einstellungen für die Verwendung von AD RMS mit einem expliziten Endpunkt

Wenn der DNS SRV-Eintrag für MDE nicht veröffentlicht wurde oder `Microsoft.InformationProtection.Identity` diesen beim Erstellen der `FileEngine` nicht übergeben kann, sind zwei Codeänderungen erforderlich. Legen Sie `FileEngineSettings.ProtectionOnlyEngine = true` fest. Diese Eigenschaft muss festgelegt werden, weil Bezeichnungsvorgänge (Richtlinie) für Endpunkte für den AD RMS-Schutz nicht unterstützt werden.

```csharp
// Configure FileEngineSettings as protection only engine and generate a unique engine id.
var engineSettings = new FileEngineSettings("", authDelegate, "", "en-US")
{
     // Set ProtectionOnlyEngine to true for AD RMS as labeling isn't supported
     ProtectionOnlyEngine = true,
     // Provide the explicit AD RMS endpoint
     ProtectionCloudEndpointBaseUrl = "https://rms.contoso.com"
};
```

### <a name="update-the-authentication-delegate"></a>Aktualisieren des Authentifizierungsdelegaten

Wenn Sie die ADAL in Ihrer .NET-Anwendung verwenden, müssen Sie eine Änderung an der `Microsoft.InformationProtection.AuthDelegate`-Implementierung vornehmen, um die Autoritätsüberprüfung zu deaktivieren. Deaktivieren Sie die Autoritätsüberprüfung, indem Sie `validateAuthority` im `AuthenticationContext`-Konstruktor auf **false** festlegen.

   ```csharp
   AuthenticationContext authContext = new AuthenticationContext(authority, false, tokenCache);
   ```

## <a name="configuring-file-api-in-c-to-use-ad-rms"></a>Konfigurieren der Datei-API in C++ zur Verwendung von AD RMS

Wenn Sie den DNS SRV-Eintrag für die Mobilgeräteerweiterung bereitgestellt haben und planen, einen Benutzerprinzipalnamen oder eine E-Mail-Adresse zu übergeben, [befolgen Sie die Anweisungen zum Verwenden einer Identität](#update-the-fileenginesettings-to-use-ad-rms-with-an-identity).

Wenn Sie nicht über den DNS SRV-Eintrag für die Mobilgeräteerweiterung verfügen oder zur Laufzeit keine Identität zur Verfügung stehen wird, [befolgen Sie die Anweisungen zur expliziten Angabe eines Endpunkts](#update-the-fileenginesettings-to-use-ad-rms-with-an-explicit-endpoint).

### <a name="update-the-fileenginesettings-to-use-ad-rms-with-an-identity"></a>Aktualisieren von „FileEngine::Settings“ für die Verwendung von AD RMS mit einer Identität

Wenn der DNS SRV-Eintrag für MDE veröffentlicht und `mip::Identity` in `FileEngine::Settings` angegeben wurde, müssen Sie nur noch die Engine als reine Schutz-Engine festlegen.

```cpp
FileEngine::Settings engineSettings(mip::Identity(mUsername), "");
engineSettings.SetProtectionOnlyEngine = true;
```

### <a name="update-the-fileenginesettings-to-use-ad-rms-with-an-explicit-endpoint"></a>Aktualisieren von „FileEngine::Settings“ für die Verwendung von AD RMS mit einem expliziten Endpunkt

Wenn der DNS SRV-Eintrag für MDE nicht veröffentlicht wurde oder keine Identität für die Dienstermittlung verfügbar ist, muss die Engine auf einen reinen Schutzmodus festgelegt und der explizite Cloudendpunkt-URL über `SetProtectionCloudEndpointBaseUrl()` bereitgestellt werden.

```cpp
FileEngine::Settings engineSettings("", authDelegate, "");
engineSettings.SetProtectionOnlyEngine = true;
engineSettings.SetProtectionCloudEndpointBaseUrl("https://rms.contoso.com");
```

## <a name="configuring-protection-api-in-c-to-use-ad-rms"></a>Konfigurieren der Schutz-API in C++ zur Verwendung von AD RMS

Wenn Sie den DNS SRV-Eintrag für die Mobilgeräteerweiterung bereitgestellt haben und planen, einen Benutzerprinzipalnamen oder eine E-Mail-Adresse zu übergeben, [befolgen Sie die Anweisungen zum Verwenden einer Identität](#set-the-protectionenginesettings-to-use-ad-rms-with-an-identity).

Wenn Sie nicht über den DNS SRV-Eintrag für die Mobilgeräteerweiterung verfügen oder zur Laufzeit keine Identität zur Verfügung stehen wird, [befolgen Sie die Anweisungen zur expliziten Angabe eines Endpunkts](#set-the-protectionenginesettings-to-use-ad-rms-with-an-explicit-endpoint).

### <a name="set-the-protectionenginesettings-to-use-ad-rms-with-an-identity"></a>Festlegen von „ProtectionEngine::Settings“ für die Verwendung von AD RMS mit einer Identität

Wenn der DNS SRV-Eintrag für die Mobilgeräteerweiterung veröffentlicht und in `ProtectionEngine::Settings` eine Identität angegeben wurde, sind für die Verwendung von AD RMS keine weiteren Codeänderungen erforderlich. Die Dienstermittlung findet den AD RMS-Endpunkt und verwendet ihn für Schutzvorgänge.

```cpp
ProtectionEngine::Settings engineSettings(mip::Identity(mUsername), authDelegate, "");
```

### <a name="set-the-protectionenginesettings-to-use-ad-rms-with-an-explicit-endpoint"></a>Festlegen von „ProtectionEngine::Settings“ für die Verwendung von AD RMS mit einem expliziten Endpunkt

Wenn der DNS SRV-Eintrag nicht veröffentlicht oder in `ProtectionEngine::Settings` keine Identität angegeben wurde, muss der Schutzendpunkt-URL explizit über `SetProtectionCloudEndpointBaseUrl()` festgelegt werden.

```cpp
ProtectionEngine::Settings engineSettings("", authDelegate, "");
engineSettings.SetProtectionCloudEndpointBaseUrl("https://RMS.CONTOSO.COM");
```

## <a name="remove-or-comment-label-references"></a>Entfernen oder Kommentieren von Bezeichnungsverweisen

Wenn Sie die Anwendung mithilfe einer der Schnellstartanleitungen erstellen, werden Sie feststellen, dass die Anwendungen in Form von `fileEngine.SensitivityLabels` oder `engine->ListSensitivityLabels();` Verweise auf Bezeichnungen aufweist. Da die Anwendung auf einen reinen Schutzmodus festgelegt wurde, müssen diese Codeblöcke auskommentiert oder entfernt werden, weil ihre Ausführung eine Ausnahme auslösen würde.

## <a name="next-steps"></a>Nächste Schritte

Sie haben alle Änderungen vorgenommen, um AD RMS zu unterstützen, und jetzt kann Ihre Anwendung mithilfe des AD RMS-Diensts als Schutzanbieter reine Schutzvorgänge ausführen.