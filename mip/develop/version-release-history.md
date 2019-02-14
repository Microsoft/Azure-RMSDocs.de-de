---
title: Microsoft Information Protection (MIP) SDK-Version Versionsgeschichte und Supportrichtlinie
description: Ein Schnellstart zum Schreiben der Initialisierungslogik für Clientanwendungen eines Microsoft Information Protection (MIP) SDK.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 01/08/2019
ms.author: bryanla
manager: barbkess
ms.openlocfilehash: da4b737082153f47cc0072e8b259da4c0c89c6e4
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56252689"
---
# <a name="microsoft-information-protection-mip-sdk-version-release-history-and-support-policy"></a>Microsoft Information Protection (MIP) SDK-Version Versionsgeschichte und Supportrichtlinie

## <a name="servicing"></a>Wartung 

Jede Version zur allgemeinen Verfügbarkeit (GA) ist für sechs Monate nach der nächste Allgemein verfügbaren Version Release wird unterstützt. Die Dokumentation kann nicht mit Informationen über nicht unterstütze Versionen enthalten. Fehlerbehebungen und neue Funktionen gelten nur für die neuste allgemein verfügbare Version.

Vorschauversionen sollten nicht in der Produktion bereitgestellt werden. Verwenden Sie stattdessen die neueste Vorschauversion zum Testen der neuen Funktionalität oder Fixes, die in der nächsten Allgemein verfügbaren Version an. Nur die aktuelle Preview-Version wird unterstützt.

## <a name="release-history"></a>Verlauf der Releases

Verwenden Sie die folgende Informationen, um anzuzeigen, welche neuerungen oder Änderungen in Bezug auf eine unterstützte Version bietet. Die neueste Version ist zuerst aufgeführt. 

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet werden, wenn Sie ein Problem mit dem SDK auftreten, sollten Sie überprüfen, ob das Problem behoben ist mit der neuesten GA-Version. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion.
>  
> Technischen Support finden Sie auf die [Microsoft Information Protection von Stack Overflow-Forum](https://stackoverflow.com/questions/tagged/microsoft-information-protection). 

## <a name="version-110"></a>Version 1.1.0

**Veröffentlichungsdatum**: TBD

Diese Version bietet Unterstützung für die folgenden Plattformen:

  - .NET
  - iOS SDK (API-Richtlinie)
  - Android-SDK (Policy-API und die Datenschutz-API)

**Neue Funktionen:**

- AD RMS-Unterstützung
- Datenschutz-API-Vorgänge sind wahre asynchrone (auf Win32) ermöglicht gleichzeitige Vorgänge für nicht blockierende verschlüsseln/entschlüsseln
  - Anwendungsrückruffunktionen (AuthDelegate, HTTPDelegate usw.) können nun aufgerufen werden, auf *alle* Hintergrundthread
- Benutzerdefinierte Eigenschaften festlegen, indem IT-Administratoren können jetzt über Mip::Label::GetCustomSettings gelesen werden
- Serialisierte Veröffentlichungslizenz kann jetzt direkt aus einer Datei ohne HTTP-Vorgänge über Mip::FileHandler::GetSerializedPublishingLicense abgerufen werden
- Anwendungen werden benachrichtigt, ob ein HTTP-Vorgang erforderlich ist, um die Erstellung von einem:: fileengine-Klasse /:: policyengine-Klasse über Mip::FileProfile::Observer::OnAddPolicyEngineStarting abzuschließen / Mip::PolicyProfile::Observer::OnAddEngineStarting
- Gibt an, ob geschützter Inhalte ein Ablaufdatum oder nicht verfügt erkannt wurde vereinfacht, mit der Einfachheit halber Methode mip::ProtectionDescriptor::DoesContentExpire
- Klassifizierung:
  - Vertraulichkeit-Typen (Regex-Ausdrücke für # des, Passport # usw.) aus SCC-Dienst abgerufen werden können
    - Feature aktivieren, indem Sie die Einstellung Mip::FileEngine::Settings / Mip::PolicyEngine::Settings kennzeichnen
    - Lesen Sie die Typen über Mip::FileEngine::ListSensitivityTypes / Mip::PolicyEngine::ListSensitivityTypes
  - Klassifizierungsergebnisse externe Document Scanner Hilfsprogrammen können MIP zum Steuern der empfohlene/erforderlichen Bezeichnungen, die basierend auf den Inhalt des Dokuments eingelesen werden
    - Übergeben von Ergebnissen an MIP über Mip::FileExecutionState::GetClassificationResults / Mip::ExecutionState::GetClassificationResults
    - MIP::ApplyLabelAction und mip::RecommendLabelAction können von Mip::PolicyEngine::ComputeActions zurückgegeben werden Wenn Klassifizierungsergebnisse übereinstimmt, der eine Regel, der angibt, erforderlich/empfohlen, Bezeichnungen

- Neue Anforderungen:
  - Erzwungene Auffüllung der ID/Name und Version Felder mip::ApplicationInfo beim Erstellen von:: fileprofile-Klasse, mip::PolicyProfile und:: protectionprofile-Klasse
  - Anwendungen müssen neue mip::FileExecutionState-Schnittstelle implementieren, wenn mip::FileHandlers erstellen
  
- Aktualisierte Ausnahmen:
  - wird ausgelöst, wenn der Anwendung AuthDelegate MIP::NoAuthTokenError gibt ein leeres Tokens (aufgrund von Abbruch) zurück.
    - Gilt für die Erstellung von:
      - mip::FileEngine
      - mip::FileHandler
      - mip::PolicyEngine
      - mip::ProtectionHandler
  - MIP::NoPolicyError ausgelöst, wenn der Mandant nicht für Bezeichnungen konfiguriert ist
    - Gilt für die Erstellung von:
      - mip::FileEngine
      - mip::PolicyEngine
  - MIP::ServiceDisabledError ausgelöst, wenn der RMS-Dienst für einen bestimmten Benutzer/Gerät/Plattform/Mandanten deaktiviert ist
    - Gilt für die Erstellung von:
      - mip::FileHandler
      - mip::ProtectionHandler
  - wird ausgelöst, wenn ein Benutzer nicht über Rechte verfügt, um ein Dokument oder den Inhalt zu entschlüsseln MIP::NoPermissionsError ist abgelaufen.
    - Gilt für die Erstellung von:
      - mip::FileHandler
      - mip::ProtectionHandler

**Fixes**:

TBD

## <a name="next-steps"></a>Nächste Schritte

- Finden Sie unter [MIP SDK häufig gestellte Fragen und Probleme](faqs-known-issues.md) Informationen zu unterstützten Plattformen und vieles mehr.
- Finden Sie unter [MIP SDK-Setup und Konfiguration](setup-configure-mip.md) Informationen zum Einstieg in das MIP SDK.
