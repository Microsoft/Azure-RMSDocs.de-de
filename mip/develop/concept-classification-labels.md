---
title: 'Konzepte: Klassifizierungsbezeichnungen'
description: Dieser Artikel hilft Ihnen zu verstehen, wie Bezeichnungen für die Klassifizierung von Daten verwendet werden.
author: msmbaldwin
ms.service: information-protection
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.date: 09/27/2018
ms.author: mbaldwin
ms.openlocfilehash: e1101bd505a35e02fdeeed032d5dec61364bfb8d
ms.sourcegitcommit: 474cd033de025bab280cb7a9721ac7ffc2d60b55
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "60175240"
---
# <a name="microsoft-information-protection-sdk---classification-label-concepts"></a>Microsoft Information Protection SDK: Klassifizierungsbezeichnungskonzepte

Im Rahmen einer umfassenden Datenschutzstrategie sollten Unternehmen ein Datenklassifizierungssystem implementieren, das die Sensibilität der Daten innerhalb des Unternehmens umreißt, und diesen Klassifizierungen dann Dokumentattribute zuordnen.

Attribute, die sich auf die Klassifizierung beziehen, beinhalten typischerweise das **Risiko** für das Unternehmen, wenn dieses Dokument oder diese Daten verloren gehen oder unbeabsichtigt für Personen offengelegt werden. In bekannten Klassifizierungssystem der US-Regierung gibt es drei Klassifizierungsebenen. Jede verfügt über eine Definition, die beschreibt, wann diese Klassifizierung angewendet werden soll:

* **Top Secret** (streng geheim): Wird auf Informationen angewendet, bei deren unbefugter Weitergabe davon auszugehen ist, dass sie der nationalen Sicherheit wahrscheinlich außergewöhnlich schweren Schaden zufügen, den die ursprüngliche Klassifizierungsbehörde identifizieren oder beschreiben kann.
* **Secret** (geheim): Wird auf Informationen angewendet, bei deren unbefugter Weitergabe davon auszugehen ist, dass sie der nationalen Sicherheit wahrscheinlich schweren Schaden zufügen, den die ursprüngliche Klassifizierungsbehörde identifizieren oder beschreiben kann.
* **Confidential** (vertraulich): Wird auf Informationen angewendet, bei deren unbefugter Weitergabe davon auszugehen ist, dass sie der nationalen Sicherheit wahrscheinlich Schaden zufügen, den die ursprüngliche Klassifizierungsbehörde identifizieren oder beschreiben kann.
* **Unclassified** (nicht klassifiziert): Dies ist tatsächlich keine Klassifizierung, sondern stattdessen das Fehlen einer der oben genannten drei Klassifizierungen.

In einer kommerziellen Anwendung oder einer Anwendung im privaten Sektor können wir eine Liste mit angefügten Geldwerten definieren, die der Standardliste von Azure Information Protection Service ähnlich ist.

* **Highly Confidential** (streng vertraulich): Wird auf Informationen angewendet, deren unbefugte Weitergabe wahrscheinlich einen Schaden von mehr als 1 Million USD verursachen könnte.
* **Confidential** (vertraulich): Wird auf Informationen angewendet, deren unbefugte Weitergabe wahrscheinlich einen Schaden von mehr als 100.000 USD verursachen könnte.
* **General** (allgemein): Wird auf Informationen angewendet, deren unbefugte Weitergabe nur einen kaum messbaren Schaden verursachen könnte.
* **Public** (öffentlich): Wird auf Informationen angewendet, die für die öffentliche, externe Nutzung vorgesehen sind. 
* **Non-Business** (nicht geschäftlich): Wird auf Informationen angewendet, die nichts mit dem direkten oder indirekten Geschäft des Unternehmens zu tun haben.

Jede Klassifizierung beschreibt das Risiko für das Unternehmen im Falle einer unbefugten Weitergabe dieser Informationen. Nach der Identifizierung dieser Klassifizierung und Bedingungen sollten Attribute identifiziert werden, die den Besitzern von Daten helfen zu verstehen, welche Klassifizierung anzuwenden ist.

## <a name="labeling"></a>Bezeichnungen

Der Vorgang der Zuordnung einer Datenklassifizierung zu einem Satz von Informationen wird als **Versehen mit Bezeichnungen** bezeichnet. Da das MIP SDK Klassifizierungs**bezeichnungen** auf Dokumente anwendet, beziehen wir uns nicht auf Klassifizierungen, sondern auf Bezeichnungen. Ein Benutzer oder Prozess hat die Daten aufgrund der Kenntnis der Informationen bereits  **klassifiziert**: Das MIP SDK wird dann die Informationen mit einer **Bezeichnung** versehen.

## <a name="labels-in-the-mip-sdk"></a>Bezeichnungen im MIP SDK

Bezeichnungen sind eine wesentliche Komponente des MIP SDK. Bezeichnungen steuern die Tags, den Schutz und die Inhaltsmarkierung aller Dokumente, die mit dem SDK verwendet werden. Das SDK kann die folgenden Aktionen ausführen:

* Anwenden von Bezeichnungen auf Dokumente
* Lesen vorhandener Bezeichnung für Dokumente
* Ändern einer vorhandenen Bezeichnung und Anordnen einer Rechtfertigung, wenn dies gemäß der Richtlinie erforderlich ist
* Entfernen einer Bezeichnung von einem Dokument

Die Bezeichnung wendet Schutz und Inhaltsmarkierung basierend auf der Konfiguration an, die Bezeichnungsadministratoren im Security & Compliance Center definiert haben. 

## <a name="miplabel-vs-mipcontentlabel"></a>mip::Label im Vergleich zu mip::ContentLabel

Es gibt zwei Typen von Bezeichnungen im MIP SDK. `Label` und `ContentLabel`.

* Label: Eine Bezeichnung, die von einem Benutzer oder Prozess wie in der Organisationsrichtlinie definiert angewendet werden kann.
* ContentLabel: Eine Bezeichnung, die bereits für ein Dokument oder Informationen vorhanden ist. Sie kann gelesen, aktualisiert oder entfernt werden. 

Dies bedeutet, dass das `ContentLabel`-Element ein `Label`-Element ist, das auf eine Information angewendet wurde.

## <a name="metadata"></a>Metadaten

Das SDK unterstützt auch das Hinzufügen von zusätzlichen Metadaten zu Dokumenten in Form von Schlüssel-Wert-Paaren. Wenn Ihre Organisation Unterklassifizierungen oder Tags verwendet, die die Informationen auf spezifischere Weise beschreiben, kann das SDK verwendet werden, um diese Metadaten anzuwenden.

## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zum Klassifizierungssystem der US-Regierung finden Sie unter https://www.gpo.gov/fdsys/pkg/FR-2010-01-05/html/E9-31418.htm.
