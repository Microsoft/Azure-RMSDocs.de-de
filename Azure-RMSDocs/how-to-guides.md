---
title: Anleitungen für Azure Information Protection gängige Szenarien
description: Identifizieren Sie Anwendungsfälle, in denen die Daten Ihrer Organisation mithilfe Azure Information Protection klassifiziert und geschützt werden.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 11/30/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.reviewer: eymanor
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 56d465d8efbc0b5bc2c6b87e1b60e34cb4e091f8
ms.sourcegitcommit: b763a7204421a4c5f946abb7c5cbc06e2883199c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2020
ms.locfileid: "95567580"
---
# <a name="how-to-guides-for-common-scenarios-that-use-azure-information-protection"></a>Schrittanleitungen für häufige Szenarien, in denen Azure Information Protection verwendet wird

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Es gibt viele Möglichkeiten, wie Sie mit Azure Information Protection Dokumente und E-Mails Ihrer Organisation klassifizieren und optional schützen können. 

Die erfolgreichsten Bereitstellungen sind diejenigen, bei denen spezielle Anwendungsfälle identifiziert werden, die die größten geschäftlichen Vorteile für die Organisation bieten. Verwenden Sie die folgende Liste an gängigen Szenarien und Anweisungen, um Ihre Bereitstellung durchzuführen.

## <a name="common-scenarios"></a>Häufige Szenarios

|Szenario: Gewünschter Vorgang|Instructions|
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

Unser [Azure Information Protection Technical Blog](https://aka.ms/AIPblog) enthält zusätzliche Anleitungen aus den Gräben.

Zum Beispiel eine Methodik mit bewährten Methoden für Entscheidungsträger und IT-Implementierer:

- [Azure Information Protection Deployment Acceleration Guide](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-Deployment-Acceleration-Guide/ba-p/334423)

Schrittweise Anleitungen:

- [Erstellen eines benutzerdefinierten AIP-Überwachungs Portals](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/How-to-Build-a-Custom-AIP-Tracking-Portal/ba-p/875849)

- [Erstellen Sie umfangreichere Berichte mit Microsoft Information Protection und Azure AD Anmeldedaten](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Create-richer-reports-with-Microsoft-Information-Protection-and/ba-p/392713)

- [Nutzen Sie Microsoft Cloud App Security, um Azure Information Protection Bezeichnungen in der Cloud anzuwenden.](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Leverage-Microsoft-Cloud-App-Security-to-apply-Azure-Information/ba-p/388638)

- [Vorbereiten eines Azure Information Protection "Cloud Exit"-Plans](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/How-to-prepare-an-Azure-Information-Protection-Cloud-Exit-plan/ba-p/382631)

- [Mandanten übergreifende Bezeichnungs Visualisierung](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Cross-Tenant-Label-Visualization/ba-p/356588)

- [Mithilfe von Azure Information Protection zum Schutz des PDF-Datei und Adobe Acrobat Reader, um sie anzuzeigen](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Using-Azure-Information-Protection-to-protect-PDF-s-and-Adobe/ba-p/282010)

- [Katalogisieren Ihrer sensiblen Daten mit AIP, sogar vor dem Konfigurieren von Bezeichnungen.](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Cataloging-your-Sensitive-Data-with-AIP-Even-Before-Configuring/ba-p/267241)

- [Expressinstallation der Azure Information Protection-Überprüfung](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Azure-Information-Protection-Scanner-Express-Installation/ba-p/265424)

- [Ermittlung von sensiblen Daten mit dem AIP-Scanner (AIP-Premium-P1)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Discovery-of-Sensitive-Data-Using-the-AIP-Scanner-AIP-Premium-P1/ba-p/252040)

## <a name="next-steps"></a>Nächste Schritte

Wird Ihr Szenario nicht aufgeführt? Eine vollständige Liste der Planungs-und Bereitstellungs Schritte finden Sie in den [Bereitstellungs-Roadmaps](deployment-roadmap.md) .

Wenn Sie mit Azure Information Protection nicht vertraut sind, lesen Sie den kurzen Einführungsartikel zum Dienst [Was ist Azure Information Protection?](what-is-information-protection.md), bevor Sie mit der Durchführung der Bereitstellung beginnen.
