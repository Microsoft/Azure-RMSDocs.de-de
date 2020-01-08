---
title: 'Konzepte: APIs im MIP SDK'
description: Dieser Artikel wird Ihnen helfen, 3 Arten von APIs im MIP SDK und ihre Beziehung zueinander zu verstehen. Außerdem werden Anwendungsfälle für die Verwendung jeder dieser APIs vorgestellt.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.date: 10/16/2018
ms.author: mbaldwin
ms.openlocfilehash: 580e2c14d60c60ccb42d5d8553d4f37a705b4c0f
ms.sourcegitcommit: 99eccfe44ca1ac0606952543f6d3d767088de425
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2019
ms.locfileid: "75556281"
---
# <a name="microsoft-information-protection-sdk---api-concepts"></a>Microsoft Information Protection SDK: API-Konzepte

Das Microsoft Information Protection SDK (MSIP SDK) besteht aus drei APIs, wie in der folgenden Abbildung dargestellt:

[![MSIP SDK – API-Diagramm](media/concept-apis-use-cases/mip-sdk-components.png)](media/concept-apis-use-cases/mip-sdk-components.png#lightbox)

Abhängig von den Anforderungen Ihrer Anwendung können Sie eine Schnittstelle auf Datei-API-Ebene oder direkt auf der Richtlinien- bzw. Schutz-API-Ebene verwenden.

## <a name="file-api"></a>File-API

Die File-API ist eine Abstraktion der Protection- und der Policy-APIs. Sie stellt einfach zu verwendende Schnittstellen zum Lesen von Bezeichnungen aus dem Dienst, zum Anwenden von Bezeichnungen auf definierte Dateitypen und zum Lesen von Bezeichnungen aus diesen Dateitypen bereit. Die Datei-API wird von Diensten und Anwendungen verwendet, wenn:

- Ein unterstützter Dateityp erforderlich ist,
- Bezeichnungen gelesen oder geschrieben werden müssen und
- Inhalte geschützt oder entschlüsselt werden müssen.

### <a name="file-api-use-cases"></a>Anwendungsfälle für die File-API

- Sie sind Softwareentwickler bei einem Finanzdienstleistungsinstitut. Sie möchten sicher sein, dass Daten aus Ihren Branchenanwendungen (in der Regel im Excel-Format exportiert) beim Export basierend auf dem Inhalt mit Bezeichnungen versehen werden. Die Datei-API kann verwendet werden, um verfügbare Bezeichnungen aufzulisten und dann die entsprechende Bezeichnung auf ein unterstütztes Dateiformat anzuwenden.

- Ihre Organisation entwickelt einen CASB (Cloud Access Security Broker). Ihre Kunden wünschen sich die Möglichkeit, MIP-Bezeichnungen auf Microsoft Office- und PDF-Dokumente anzuwenden. Mit der Datei-API können Sie eine Liste von konfigurierten Bezeichnungen anzeigen und Ihren Kunden ermöglichen, Regeln zu erstellen, die die gewünschte Bezeichnung anwenden. Die Datei-API würde beim Erfassen der Bezeichnungs-ID die restliche Verarbeitung der Dateien übernehmen, die die Kriterien des Kunden erfüllen.

- Ihr Unternehmen stellt eine dienstbasierte Lösung zur Vermeidung von Datenverlust oder einen CASB bereit, der SaaS-Anwendungen auf Dateiaktivitäten überwacht. Um das Risiko von Datenverlust oder -offenlegung zu verringern, wenn Daten mit MSIP geschützt sind, muss Ihr Dienst den Inhalt geschützter Dateien scannen. Wenn Sie die Datei-API für die unterstützten Formate verwenden und der Dienst ein berechtigter Benutzer ist, können Sie:

  1. Schutz entfernen
  2. Inhalte auf eingeschränkten und vertraulichen Content überprüfen
  3. Klartextergebnisse verwerfen
  4. Dienstregeln zum Melden oder Beheben von Risiken anwenden (sofern erkannt)

## <a name="policy-api"></a>Policy-API

Die Richtlinien-API oder UPE (Universal Policy Engine) bietet Softwareentwicklern die Möglichkeit, Bezeichnungsrichtlinien für einen bestimmten Benutzer abzurufen. Sie kann dann die Aktionen dann „berechnen“, die diese Bezeichnungen durchführen sollen.

Die Richtlinien-API wird hauptsächlich von Clientanwendungen verwendet, bei denen der Entwickler die Schnittstelle und das Dateiformat steuert. Sie wird auch verwendet, wenn die einzige Anforderung darin besteht, die Benutzerrichtlinie abzurufen und Dateien nicht direkt zu bezeichnen. 

### <a name="policy-api-use-cases"></a>Anwendungsfälle für die Policy-API

- Ihre Organisation entwickelt 3D-Entwurfssoftware, die ein proprietäres Dateiformat verwendet. Ihre Kunden verwenden MSIP und möchten Bezeichnungen nativ in Ihrer Anwendung anwenden. Sie als Softwareentwickler verwenden die Richtlinien-API und ein benutzerdefiniertes Steuerelement, um die für den authentifizierten Benutzer verfügbaren Bezeichnungen anzuzeigen. Nachdem der Benutzer eine Bezeichnung ausgewählt hat, rufen Sie die API-Methode zum Berechnen der Aktion auf. Die API teilt Ihnen genau mit, was in Bezug auf Metadaten, Inhaltskennzeichnung und Schutz angewendet werden soll.

- Ihre Organisation entwickelt einen Dienst zur Verhinderung von Datenverlust (DLP), mit dem Ihre Kunden DLP-Richtlinien über ein zentrales Verwaltungsportal konfigurieren können. Sie haben Kunden, die MSIP verwenden und AIP-Bezeichnungen im Rahmen von DLP-Richtlinien lesen oder anwenden. Als Softwareentwickler können Sie die Richtlinien-API verwenden, um eine Liste von Bezeichnungen für die Kundenorganisation abzurufen. Sie können diese Bezeichnungen dann im Rahmen einer DLP-Regel lesen oder die Bezeichnungsinformationen als Teil einer Regelaktion anwenden.

## <a name="protection-api"></a>Protection-API

Die Schutz-API bietet Softwareentwicklern die Möglichkeit, Klartextdatenströme in Datenströme mit Rechteverwaltung zu konvertieren und umgekehrt.

### <a name="protection-api-use-cases"></a>Anwendungsfälle für die Protection-API

- Ihrer Organisation entwickelt Software für 3D-Drucker, die ein proprietäres Format verwendet. Sie möchten MIP verwenden, um die Datei zu schützen, sodass sie nur von bestimmten Benutzern gedruckt werden kann. Mit der Schutz-API können Sie Schutz auf die Datei anwenden, sodass nur autorisierte Benutzer diese öffnen und drucken können. 

- Ihre Organisation entwickelt eine eDiscovery-Lösung, die Exchange-Postfächer und PST-Dateien verarbeitet. Ihre Anwendung muss Benutzern ermöglichen, Nachrichten zu entschlüsseln, um eDiscovery auszuführen. Mit einem benutzerdefinierten Nachrichten-/RPMSG-Parser und einem Konto, das über die entsprechenden Berechtigungen verfügt, können Sie mit der RMS-API:
  - Verschlüsselte Datei entschlüsseln
  - Inhalte überprüfen
  - Elemente außerhalb eines Bereichs verwerfen oder innerhalb eines Bereichs verpacken

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie sich nun einen Überblick über die verfügbaren MIP-APIs und deren Verwendung verschafft haben, fahren Sie mit [Konzepte für Profile- und Engine-Objekte](concept-profile-engine-cpp.md) fort. Diese Konzepte sind grundlegend und gelten für alle MIP-API-Sätze.
