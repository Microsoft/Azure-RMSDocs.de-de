---
title: Versions Veröffentlichungs Verlauf und Unterstützungs Richtlinie für das Microsoft Information Protection (MIP) SDK
description: Ein Schnellstart zum Schreiben der Initialisierungslogik für Clientanwendungen eines Microsoft Information Protection (MIP) SDK.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 01/08/2019
ms.author: mbaldwin
manager: barbkess
ms.openlocfilehash: c2a5d89bf318d9e685d00033ba3ad53915659cdb
ms.sourcegitcommit: fcde8b31f8685023f002044d3a1d1903e548d207
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/21/2019
ms.locfileid: "69882665"
---
# <a name="microsoft-information-protection-mip-sdk-version-release-history-and-support-policy"></a>Versions Veröffentlichungs Verlauf und Unterstützungs Richtlinie für das Microsoft Information Protection (MIP) SDK

## <a name="servicing"></a>Deten 

Jede allgemein verfügbare Version (General Availability, GA) wird sechs Monate lang unterstützt, nachdem die nächste GA-Version veröffentlicht wurde. In der Dokumentation sind möglicherweise keine Informationen zu nicht unterstützten Versionen enthalten. Korrekturen und neue Funktionen werden nur auf die neueste Version der allgemeinen Verfügbarkeit angewendet.

Vorschau Versionen sollten nicht in der Produktionsumgebung bereitgestellt werden. Verwenden Sie stattdessen die neueste Vorschauversion, um neue Funktionen oder Korrekturen zu testen, die in der nächsten GA-Version verfügbar sind. Nur die aktuelle Vorschauversion wird unterstützt.

## <a name="release-history"></a>Verlauf der Releases

Verwenden Sie die folgenden Informationen, um zu sehen, was für eine unterstützte Version neu ist oder geändert wurde. Die neueste Version ist zuerst aufgeführt. 

> [!NOTE]
> Kleinere Korrekturen sind nicht aufgelistet. Wenn Sie also ein Problem mit dem SDK haben, sollten Sie überprüfen, ob es mit der neuesten Version der allgemeinen Verfügbarkeit behoben ist. Wenn das Problem weiterhin besteht, überprüfen Sie die aktuelle Vorschauversion.
>  
> Technische Unterstützung finden Sie im [Stack Overflow Microsoft Information Protection-Forum](https://stackoverflow.com/questions/tagged/microsoft-information-protection). 


## <a name="version-130"></a>Version 1.3.0

**Veröffentlichungsdatum**: TBD

## <a name="version-120"></a>Version 1.2.0

**Veröffentlichungsdatum**: 15. April 2019

## <a name="version-110"></a>Version 1.1.0

**Veröffentlichungsdatum**: 15. Januar 2019

Mit dieser Version wird die Unterstützung für die folgenden Plattformen eingeführt:

  - .NET
  - IOS SDK (Richtlinien-API)
  - Android SDK (Richtlinien-API und Schutz-API)

**Neue Funktionen:**

- ADRMS-Unterstützung
- Schutz-API-Vorgänge sind tatsächlich asynchron (auf Win32) und ermöglichen gleichzeitige, nicht blockierende Verschlüsselungs-/Entschlüsselungs Vorgänge.
  - Anwendungs Rückrufe (authdelegat, httpdelegat usw.) können jetzt in *jedem* Hintergrund Thread aufgerufen werden.
- Von IT-Administratoren festgelegte benutzerdefinierte Bezeichnungs Eigenschaften können jetzt über MIP:: Label:: getcustomsettings gelesen werden.
- Die serialisierte Veröffentlichungs Lizenz kann jetzt direkt aus einer Datei ohne http-Vorgänge über MIP:: fileHandler:: getserializedpublishinglicense abgerufen werden.
- Anwendungen werden benachrichtigt, ob ein HTTP-Vorgang erforderlich ist, um die Erstellung eines MIP:: fileengine/MIP::P olicyengine über MIP:: fileprofile:: Observer:: onaddpolicyenginestarting/MIP::P olicyprofile:: Observer:: onaddenginestarting abzuschließen.
- Die Erkennung, ob geschützte Inhalte ein Ablaufdatum aufweisen oder nicht, wurde mit der Hilfsmethode "MIP::P rotectiondescriptor::D oescontentexpire" vereinfacht.
- Ordnung
  - Empfindlichkeits Typen (Regex-Ausdrücke für CC-, Passport # s usw.) können vom SCC-Dienst abgerufen werden.
    - Aktivieren Sie das Feature, indem Sie MIP:: fileengine:: Settings/MIP::P olicyengine:: Settings-Flag festlegen.
    - Lese Typen über MIP:: fileengine:: listsensitivitytypes/MIP::P olicyengine:: listsensitivitytypes
  - Klassifizierungs Ergebnisse aus externen Dokumentenscanner können per MIP an MIP weitergeleitet werden, um empfohlene/erforderliche Bezeichnungen basierend auf Dokument Inhalten zu steuern.
    - Ergebnisse an MIP über MIP:: fileexecutionstate:: getclassificationresults/MIP:: executionstate:: getclassificationresults übergeben
    - MIP:: applylabelaction und MIP:: RecommendLabelAction können von MIP::P olicyengine:: computeactions zurückgegeben werden, wenn Klassifizierungs Ergebnisse einer Richtlinien Regel entsprechen, die erforderliche/Empfohlene Bezeichnungen anzeigt.

- Neue Anforderungen:
  - Erzwungene Auffüllung von ID/Name-/Versionsfeldern MIP:: ApplicationInfo beim Erstellen von MIP:: fileprofile, MIP::P olicyprofile und MIP::P rotectionprofile
  - Anwendungen müssen beim Erstellen von MIP:: filehandlers die neue MIP:: fileexecutionstate-Schnittstelle implementieren.
  
- Aktualisierte Ausnahmen:
  - MIP:: noauthtokenerror wird ausgelöst, wenn der authdelegat der Anwendung ein leeres Token zurückgibt (aufgrund eines Abbruchs).
    - Gilt für die Erstellung von:
      - MIP:: fileengine
      - MIP:: fileHandler
      - mip::PolicyEngine
      - MIP::P rotectionhandler
  - MIP:: nopolicyerror wird ausgelöst, wenn der Mandant nicht für Bezeichnungen konfiguriert ist.
    - Gilt für die Erstellung von:
      - MIP:: fileengine
      - mip::PolicyEngine
  - MIP:: servicedisablederror wird ausgelöst, wenn der RMS-Dienst für einen bestimmten Benutzer/Gerät/Plattform/Mandanten deaktiviert ist.
    - Gilt für die Erstellung von:
      - MIP:: fileHandler
      - MIP::P rotectionhandler
  - MIP:: nopermissionserror wird ausgelöst, wenn ein Benutzer nicht über die Berechtigung zum Entschlüsseln eines Dokuments verfügt oder der Inhalt abgelaufen ist.
    - Gilt für die Erstellung von:
      - MIP:: fileHandler
      - MIP::P rotectionhandler

**Fixes**:

TBD

## <a name="next-steps"></a>Nächste Schritte

- Weitere Informationen zu unterstützten Plattformen und mehr finden Sie unter [FAQs und Probleme im MIP SDK](faqs-known-issues.md) .
- Informationen zu den ersten Schritten mit dem MIP SDK finden Sie unter [MIP SDK-Setup und Konfiguration](setup-configure-mip.md) .
