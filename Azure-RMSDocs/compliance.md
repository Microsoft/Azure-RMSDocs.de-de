---
title: Kompatibilitätsinformationen zu Azure Information Protection
description: Ergänzende Informationen zu Azure Information Protection, darunter rechtliche Hinweise, Informationen zur Kompatibilität und SLAs.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 12/06/2018
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 4f611f97309851364324618e436ca13d4bd9fee7
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56254712"
---
# <a name="compliance-and-supporting-information-for-azureinformation-protection"></a>Konformitätsinformationen und ergänzende Informationen zu Azure Information Protection

Azure Information Protection unterstützt weitere Dienste und verwendet zusätzliche Dienste. Wenn Sie Informationen zu Azure Information Protection suchen, jedoch nicht zur Verwendung des Azure Information Protection-Diensts, sehen Sie sich folgende Ressourcen an:

## <a name="suitability-for-different-countries"></a>Eignung für verschiedene Länder

Aufgrund der Unterschiede zwischen Gesetzen und Bestimmungen in verschiedenen Ländern, zwischen Anwendungsfällen und-szenarios und aufgrund der verschiedenen Anforderungen in unterschiedlichen Geschäftssektoren müssen Sie mit Ihrem Rechtsberater sprechen, um zu bestimmen, ob Azure Information Protection für Ihr Land geeignet ist.

Hier finden Sie einige relevante Informationen, die Ihrem Rechtsberater bei der Beantwortung dieser Frage helfen können:

- Azure Information Protection verwendet AES 256 und 128 zum Verschlüsseln von Dokumenten. [Weitere Informationen](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Alle Verschlüsselungsschlüssel, die von Azure Information Protection verwendet werden, werden mit einem kundenspezifischen Stammschlüssel geschützt, der RSA 2048-Bit verwendet. RSA 1024-Bit wird zur Rückwärtskompatibilität auch unterstützt. [Weitere Informationen](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Kundenspezifische Stammschlüssel werden entweder von Microsoft verwaltet oder vom Kunden in einem Thales-HSM mit [Bring Your Own Key (BYOK)](plan-implement-tenant-key.md) bereitgestellt. Azure Information Protection unterstützt zudem eingeschränkte Funktionen mit einem lokalen Schlüssel durch [Hold Your Own Key (HYOK)](configure-adrms-restrictions.md) für Inhalte, für die erforderlich ist, dass sie nicht mit einem cloudbasierten Schlüssel geschützt werden.

- Azure Information Protection wird weltweit in regionalen Rechenzentren gehostet. Schlüssel und Richtlinien von Azure Information Protection bleiben immer in der Region, in der sie ursprünglich bereitgestellt wurden.
 
- Azure Information Protection überträgt keine Dokumentinhalte von Clients an den Azure Information Protection-Dienst. Vorgänge zum Ver- und Entschlüsseln von Inhalten werden direkt auf den Clientgerät durchgeführt. Für dienstbasiertes Rendern können diese Vorgänge auch im Dienst durchgeführt werden, der den Inhalt rendert. [Weitere Informationen](./how-does-it-work.md)

## <a name="legal-and-privacy"></a>Rechtliche Hinweise und Datenschutz

- Informationen zur Microsoft Azure-Vereinbarung: [Microsoft Azure-Vereinbarung](https://azure.microsoft.com/support/legal/subscription-agreement/)

- Informationen zum Microsoft Azure-Datenschutz: [Datenschutzerklärung zu Microsoft Azure](https://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>Sicherheit, Konformität und Überwachung

Weitere Informationen über spezifische Zertifizierungen für den Azure Rights Management-Dienst finden Sie im Artikel [Welche Probleme werden von Azure RMS gelöst?](./azure-rms-problems-it-solves.md) im Abschnitt [Sicherheits-, Compliance- und gesetzliche Anforderungen](./what-is-azure-rms.md#security-compliance-and-regulatory-requirements). Zusätzlich:

- Informationen zu externen Zertifizierungen für Azure Information Protection: [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/)

- FIPS 140-Informationen: [FIPS 140-Validierung](https://technet.microsoft.com/library/security/cc750357.aspx)

Weitere ausführliche technische Informationen über die Funktionsweise der Schutztechnologie finden Sie unter [Funktionsweise von Azure RMS](./how-does-it-work.md). 

## <a name="service-level-agreements"></a>Vereinbarungen zum Service Level

- [SLA für Azure Information Protection](https://azure.microsoft.com/support/legal/sla/information-protection/v1_0/)

- [SLA für Azure Active Directory](https://azure.microsoft.com/support/legal/sla/active-directory/v1_0/)

- [SLA für Azure Key Vault](https://azure.microsoft.com/support/legal/sla/key-vault/v1_0/)

## <a name="documentation"></a>Dokumentation

- Dokumentation zu Azure Active Directory: [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis)

- Office 365 Enterprise-Dokumentation: [Office 365](https://docs.microsoft.com/en-us/Office365/Enterprise/)

