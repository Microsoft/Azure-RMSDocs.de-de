---
title: 'Konzepte: die grundlegenden Konzepte im MIP SDK-mipcontext'
description: Dieser Artikel hilft Ihnen dabei, das Core SDK-Konzept namens mipcontext zu verstehen, das die Anwendungs Initialisierung steuert.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 07/30/2019
ms.author: mbaldwin
ms.openlocfilehash: aac40c5ba5f06e705aaf5c6d42c6963d851d2764
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69893734"
---
# <a name="microsoft-information-protection-sdk---mipcontext-object-concepts"></a>Microsoft Information Protection SDK-mipcontext-Objekt Konzepte

## <a name="mipcontext"></a>Mipcontext

`MipContext`ist das Objekt der höchsten Ebene im SDK. Er ist verantwortlich für die Verwaltung des Zustands über alle Profile hinweg, die als Teil einer Anwendung oder eines Dienstanbieter erstellt werden können. Außerdem wird die Freigabe von MIP SDK-Ressourcen verarbeitet, sobald das mipcontext-Objekt zerstört wurde.

Insbesondere wird `MipContext` Folgendes festgelegt:

- `mip::ApplicationInfo`im gesamten SDK, verwendet für die Anwendungs-ID, die Version und den Anwendungsnamen.
- Der Pfad, in dem die MIP-Zustandsinformationen gespeichert werden sollen, sofern aktiviert.
- Protokolliergrad.
- Ein benutzerdefinierter Protokollierungs Delegat, wenn gewünscht.
- Überschreiben der telemetriekonfiguration.
- Aktivieren Sie die Vorschau Features im SDK, die sich hinter Merkmals Flags befinden.

Nachdem ein Objekt von `mip::MipContext` erstellt wurde, kann das `MipContext` -Objekt zum Erstellen `mip::FileProfile` von-Objekten (oder `PolicyProfile` / `ProtectionProfile`) verwendet werden.

### <a name="mipcontext-functions"></a>Mipcontext-Funktionen

`mip::MipContext`macht drei wichtige statische Funktionen verfügbar, mit denen- `MipContext` Objekte erstellt und zerstört werden.

#### `mip::MipContext::Create()`

Erstellt eine neue mipcontext-Instanz, die beim Initialisieren von Profilen verwendet werden soll. Diese Funktion akzeptiert Folgendes:

- `mip::ApplicationInfo`
- Ein Pfad für den MIP-Speicher Cache.
- `mip::LogLevel`
- (Optional) `mip::LoggerDelegate`
- (Optional) `mip::TelemetryConfiguration`

#### `mip::MipContext::CreateWithCustomFeatureSettings()`

Erstellt eine neue mipcontext-Instanz, die beim Initialisieren von Profilen mit aktivierten benutzerdefinierten Featureeinstellungen verwendet werden soll.

- `mip::ApplicationInfo`
- Ein Pfad für den MIP-Speicher Cache.
- `mip::LogLevel`
- (Optional) `mip::LoggerDelegate`
- (Optional) `mip::TelemetryConfiguration`
- `mip::FlightingFeature`

#### `mip::mipContext::Shutdown()`

Gibt alle MIP-Ressourcen frei. Sollte vor dem Herunterfahren der app aufgerufen werden. Der `MipContext` Dekonstruktor ruft diese auch auf, `MipContext` wenn das Objekt zerstört wird.

## <a name="next-steps"></a>Nächste Schritte

- Erfahren Sie im nächsten Schritt mehr über [Authentifizierungskonzepte](concept-authentication-cpp.md) und [Observer-Objekte](concept-async-observers.md). MIP bietet ein erweiterbares Authentifizierungsmodell, während Observer-Objekte verwendet werden, um Ereignisbenachrichtigungen für asynchrone Ereignisse bereitzustellen. Beides sind grundlegende Konzepte, die für alle MIP-API-Sätze gelten.
- Anschließend arbeiten Sie das Profil- und Enginekonzept für die File-, Policy- und Protection-APIs durch.
  - [Profilkonzepte der File-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der File-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Policy-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Policy-API](concept-profile-engine-file-engine-cpp.md)
  - [Profilkonzepte der Protection-API](concept-profile-engine-file-profile-cpp.md)
  - [Enginekonzepte der Protection-API](concept-profile-engine-file-engine-cpp.md)
