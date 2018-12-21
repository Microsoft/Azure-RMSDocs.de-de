---
title: Schritt-für-Schritt-Anweisungen für häufige Szenarien, in denen Azure Information Protection verwendet wird
description: In diesem Artikel werden Anwendungsfälle vorgestellt, bei denen Daten Ihrer Organisation mithilfe von Azure Information Protection klassifiziert und geschützt werden.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/08/2018
ms.topic: conceptual
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7986648999a830985c4dbd1f31855bb222a443c2
ms.sourcegitcommit: 2a1c0882d2b0400f4da6370dbc1830df09867e3d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/11/2018
ms.locfileid: "53218373"
---
# <a name="how-to-guides-for-common-scenarios-that-use-azure-information-protection"></a>Schrittanleitungen für häufige Szenarien, in denen Azure Information Protection verwendet wird

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Es gibt viele Möglichkeiten, wie Sie mit Azure Information Protection Dokumente und E-Mails Ihrer Organisation klassifizieren und optional schützen können. 

Die erfolgreichsten Bereitstellungen sind diejenigen, bei denen spezielle Anwendungsfälle identifiziert werden, die die größten geschäftlichen Vorteile für die Organisation bieten. Verwenden Sie die folgende Liste an gängigen Szenarien und Anweisungen, um Ihre Bereitstellung durchzuführen.

## <a name="common-scenarios"></a>Häufige Szenarien

|Szenario: Ziel ...|Anweisungen|
|----------------|---------------|
|Nach vertraulichen Informationen suchen, die meine Organisation lokal speichert|[Schnellstart: Suchen nach vertraulichen Informationen in lokal gespeicherten Dateien](quickstart-findsensitiveinfo.md)|
|Es Benutzern einfacher machen, E-Mails, die vertrauliche Informationen enthalten, zu schützen|[Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails, die vertrauliche Informationen enthalten](quickstart-label-dnf-protectedemail.md)|
|Es Benutzern einfacher machen, Daten beim Erstellen oder Bearbeiten zu klassifizieren und zu schützen, wenn diese vertrauliche Informationen enthalten| [Tutorial: Bearbeiten der Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)|
|Es Benutzern einfacher machen, an einem geschützten Dokument zusammenzuarbeiten|[Konfigurieren einer sicheren Zusammenarbeit an Dokumenten mithilfe von Azure Information Protection](secure-collaboration-documents.md)|
|E-Mails von Benutzern, die außerhalb der Organisation gesendet werden, automatisch schützen| [Konfigurieren von Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen](configure-exo-rules.md)
|Automatisch vorhandene Daten in meinen lokalen Datenspeichern klassifizieren und schützen|[Bereitstellen der Azure Information Protection-Überprüfung](deploy-aip-scanner.md)|
|Mit dem eigenen Schlüssel Daten von meiner Organisation schützen| [Planen und Implementieren des Mandantenschlüssels](plan-implement-tenant-key.md)|
|Von AD RMS migrieren|[Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|

## <a name="additional-deployment-instructions"></a>Zusätzliche Anweisungen zur Bereitstellung

Unser [technisches Blog zu Azure Information Protection](https://aka.ms/AIPblog) enthält schrittweise Anleitungen unseres Customer Experience Engineering-Teams. Beispiel:

- [Mithilfe von Azure Information Protection zum Schutz des PDF-Datei und Adobe Acrobat Reader, um sie anzuzeigen](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Using-Azure-Information-Protection-to-protect-PDF-s-and-Adobe/ba-p/282010)

- [Katalogisieren Ihrer sensiblen Daten mit AIP, sogar vor dem Konfigurieren von Bezeichnungen.](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Cataloging-your-Sensitive-Data-with-AIP-Even-Before-Configuring/ba-p/267241)

- [Expressinstallation der Azure Information Protection-Überprüfung](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-Scanner-Express-Installation/ba-p/265424)

- [Ermittlung von sensiblen Daten mit dem AIP-Scanner (AIP-Premium-P1)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discovery-of-Sensitive-Data-Using-the-AIP-Scanner-AIP-Premium-P1/ba-p/252040)

## <a name="next-steps"></a>Nächste Schritte

Wird Ihr Szenario nicht aufgeführt? Sehen Sie sich die [Roadmap für die Bereitstellung](deployment-roadmap.md) an, um eine vollständige Liste der Planungs- und Bereitstellungsschritte einzusehen.

Wenn Sie mit Azure Information Protection nicht vertraut sind, lesen Sie den kurzen Einführungsartikel zum Dienst [Was ist Azure Information Protection?](what-is-information-protection.md), bevor Sie mit der Durchführung der Bereitstellung beginnen.
