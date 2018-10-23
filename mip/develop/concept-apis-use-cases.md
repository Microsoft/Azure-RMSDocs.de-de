---
title: 'Konzepte: APIs im MIP SDK'
description: Dieser Artikel wird Ihnen helfen, 3 Arten von APIs im MIP SDK und ihre Beziehung zueinander zu verstehen. Außerdem werden Anwendungsfälle für die Verwendung jeder dieser APIs vorgestellt.
author: BryanLa
ms.service: information-protection
ms.topic: conceptual
ms.date: 09/27/2018
ms.author: bryanla
ms.openlocfilehash: a625df159a00a955d155850ff4e326d1e0d204e5
ms.sourcegitcommit: 823a14784f4b34288f221e3b3cb41bbd1d5ef3a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/29/2018
ms.locfileid: "47453331"
---
# <a name="microsoft-information-protection-sdk---api-concepts"></a>Microsoft Information Protection SDK: API-Konzepte

Das MIP SDK besteht aus drei APIs:

- [Protection-API](#protection-api)
- [Policy-API](#policy-api)
- [File-API](#file-api)

## <a name="protection-api"></a>Protection-API

Die Protection-API bietet Softwareentwicklern die Möglichkeit, Klartextdatenströme in Datenströme mit Rechteverwaltung zu konvertieren und umgekehrt.

### <a name="protection-api-use-cases"></a>Anwendungsfälle für die Protection-API

- Ihrer Organisation entwickelt Software für 3D-Drucker, die ein proprietäres Format verwendet. Sie möchten MIP verwenden, um die Datei zu schützen, sodass sie nur von bestimmten Benutzern gedruckt werden kann. Mit der Protection-API können Sie Schutz auf die Datei anwenden, sodass nur autorisierte Nutzer diese öffnen und/oder drucken können. 

- Ihre Organisation entwickelt eine eDiscovery-Lösung, die Exchange-Postfächer und PST-Dateien verarbeitet. Ihre Anwendung muss in der Lage sein, Nachrichten zu entschlüsseln, um vollständige eDiscovery-Vorgänge ausführen zu können. Mithilfe eines benutzerdefinierten Nachrichten-/RPMSG-Parsers und eines mit ausreichenden Berechtigungen ausgestatteten Kontos können Sie die RMS-API nutzen, um die verschlüsselte Datei zu entschlüsseln, den Inhalt zu scannen und zu verwerfen, wenn er außerhalb des Bereichs liegt, oder ein Paket zu erstellen, wenn er im Bereich liegt.

## <a name="policy-api"></a>Policy-API

Die Policy-API oder UPE (Universal Policy Engine) bietet Softwareentwicklern die Möglichkeit, Bezeichnungsrichtlinien für einen bestimmten Benutzer abzurufen und dann die Aktionen zu „berechnen“, die diese Bezeichnungen durchführen sollen.

Die Policy-API wird in erster Linie von Clientanwendungen genutzt, bei denen der Entwickler die Schnittstelle und das Dateiformat steuert, oder bei denen die einzige Anforderung darin besteht, die Benutzerrichtlinie abzurufen und nicht notwendigerweise Dateien direkt zu kennzeichnen. 

### <a name="policy-api-use-cases"></a>Anwendungsfälle für die Policy-API

- Ihre Organisation entwickelt 3D-Entwurfssoftware, die ein proprietäres Dateiformat verwendet. Ihre Kunden verwenden Microsoft Information Protection und möchten Bezeichnungen nativ in Ihrer Anwendung anwenden. Als Softwareentwickler würden Sie die Policy-API und ein benutzerdefiniertes Steuerelement verwenden, um die für den authentifizierten Benutzer verfügbaren Bezeichnungen anzuzeigen. Sobald der Benutzer eine Bezeichnung auswählt, würden Sie die Computeaktionsmethode der API aufrufen, um genau zu wissen, was hinsichtlich Metadaten, Inhaltsmarkierung und Schutz angewendet werden soll.

- Ihre Organisation entwickelt einen DLP-Dienst, der es Ihren Kunden ermöglicht, über ein zentrales Verwaltungsportal DLP-Richtlinien zu konfigurieren. Sie haben Kunden, die Microsoft Information Protection verwenden und in der Lage sein möchten, AIP-Bezeichnungen als Teil der DLP-Richtlinien zu lesen oder anzuwenden. Als Softwareentwickler können Sie die Policy-API zum Abrufen einer Liste von Bezeichnungen für die Kundenorganisation verwenden und diese Bezeichnungen dann als Teil einer DLP-Regel lesen oder die Bezeichnungsinformationen als Teil einer Regelaktion anwenden.

## <a name="file-api"></a>File-API

Die File-API ist eine Abstraktion der Protection- und der Policy-APIs. Sie stellt einfach zu verwendende Schnittstellen zum Lesen von Bezeichnungen aus dem Dienst, zum Anwenden von Bezeichnungen auf definierte Dateitypen sowie zum Lesen von Bezeichnungen aus diesen Dateitypen bereit. Die File-API wird von beliebigen Diensten oder Anwendungen verwendet, bei denen ein unterstützter Dateityp vorhanden ist und Bezeichnungen gelesen oder geschrieben bzw. Inhalte geschützt oder entschlüsselt werden müssen.

### <a name="file-api-use-cases"></a>Anwendungsfälle für die File-API

- Sie sind Softwareentwickler bei einem Finanzdienstleistungsinstitut. Sie möchten sicher sein, dass Daten aus Ihren Branchenanwendungen (in der Regel im Excel-Format exportiert) beim Export basierend auf dem Inhalt mit Bezeichnungen versehen werden. Die File-API kann verwendet werden, um verfügbare Bezeichnungen aufzulisten und dann die entsprechende Bezeichnung auf ein unterstütztes Dateiformat anzuwenden.

- Ihre Organisation entwickelt einen CASB (Cloud Access Security Broker). Ihre Kunden wünschen sich die Möglichkeit, MIP-Bezeichnungen auf Microsoft Office- und PDF-Dokumente anzuwenden. Die File-API ermöglicht es Ihnen, eine Liste der konfigurierten Bezeichnungen anzuzeigen und Ihren Kunden die Möglichkeit zu geben, Regeln zu erstellen, die die gewünschte Bezeichnung anwenden. Die File-API würde bei Übergabe der Bezeichnungs-ID die restliche Verarbeitung für Dateien übernehmen, die die Kriterien des Kunden erfüllen.

- Ihr Unternehmen stellt eine dienstbasierte Lösung zur Vermeidung von Datenverlust und/oder einen CASB bereit, der SaaS-Anwendungen auf Dateiaktivitäten überwacht. Um das Risiko von Datenverlust oder -offenlegung zu verringern, wenn Daten mit MIP geschützt sind, muss Ihr Dienst in der Lage sein, den Inhalt geschützter Dateien zu scannen. Mit der File-API für die unterstützten Formate können Sie, wenn der Dienst ein privilegierter Benutzer ist, den Schutz aufheben, den Inhalt auf eingeschränkte oder sensible Inhalte scannen, das Klartextergebnis verwerfen und eine Dienstregel anwenden, um das Risiko zu melden oder zu beheben, wenn es gefunden wird.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie sich nun einen Überblick über die verfügbaren MIP-APIs und deren Verwendung verschafft haben, fahren Sie mit [Konzepte für Profile- und Engine-Objekte](concept-profile-engine-cpp.md) fort. Diese Konzepte sind grundlegend und gelten für alle MIP-API-Sätze.