---
title: Kompatibilitätsinformationen zu Azure Information Protection
description: Ergänzende Informationen zu Azure Information Protection, darunter rechtliche Hinweise, Informationen zur Konformität und SLAs.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/08/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: b3a7127b-6d24-4439-bc4e-2a0a325e8ea3
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 708d39a5f69182225a1eea23c625b4a53a7172cd
ms.sourcegitcommit: 74b8d03d1ede3da12842b84546417e63897778bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2021
ms.locfileid: "102414751"
---
# <a name="compliance-and-supporting-information-for-azure-information-protection"></a>Kompatibilitätsinformationen und ergänzende Informationen zu Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Azure Information Protection unterstützt weitere Dienste und verwendet zusätzliche Dienste. Wenn Sie Informationen zu Azure Information Protection suchen, jedoch nicht zur Verwendung des Azure Information Protection-Diensts, sehen Sie sich folgende Ressourcen an:

## <a name="suitability-for-different-countries"></a>Eignung für verschiedene Länder

Aufgrund der Unterschiede zwischen Gesetzen und Bestimmungen in verschiedenen Ländern, zwischen Anwendungsfällen und-szenarios und aufgrund der verschiedenen Anforderungen in unterschiedlichen Geschäftssektoren müssen Sie mit Ihrem Rechtsberater sprechen, um zu bestimmen, ob Azure Information Protection für Ihr Land geeignet ist.

Hier finden Sie einige relevante Informationen, die Ihrem Rechtsberater bei der Beantwortung dieser Frage helfen können:

- Azure Information Protection verwendet AES 256 und 128 zum Verschlüsseln von Dokumenten. [Weitere Informationen](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Alle Verschlüsselungsschlüssel, die von Azure Information Protection verwendet werden, werden mit einem kundenspezifischen Stammschlüssel geschützt, der RSA 2048-Bit verwendet. RSA 1024-Bit wird zur Rückwärtskompatibilität auch unterstützt. [Weitere Informationen](./how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)

- Kundenspezifische Stamm Schlüssel werden entweder von Microsoft verwaltet oder vom Kunden in einem nchiffre-HSM bereitgestellt, indem "Bring your own Key" (Byok) verwendet wird. Azure Information Protection unterstützt auch Features für den lokalen Schutz, für Inhalte, die nicht mit einem cloudbasierten Schlüssel geschützt werden können. Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

- Azure Information Protection wird weltweit in regionalen Rechenzentren gehostet. Schlüssel und Richtlinien von Azure Information Protection bleiben immer in der Region, in der sie ursprünglich bereitgestellt wurden.

    > [!NOTE]
    > Azure Information Protection Richtlinien sind nur für den klassischen AIP-Client relevant.
    >
  
- Azure Information Protection überträgt keine Dokumentinhalte von Clients an den Azure Information Protection-Dienst. Vorgänge zum Ver- und Entschlüsseln von Inhalten werden direkt auf den Clientgerät durchgeführt. Für dienstbasiertes Rendern können diese Vorgänge auch im Dienst durchgeführt werden, der den Inhalt rendert. [Weitere Informationen](./how-does-it-work.md)

## <a name="legal-and-privacy"></a>Rechtliche Hinweise und Datenschutz

- Informationen zur Microsoft Azure-Vereinbarung: [Microsoft Azure-Vereinbarung](https://azure.microsoft.com/support/legal/subscription-agreement/)

- Informationen zum Microsoft Azure-Datenschutz: [Datenschutzerklärung zu Microsoft Azure](https://azure.microsoft.com/support/legal/privacy-statement/)

## <a name="security-compliance-and-auditing"></a>Sicherheit, Konformität und Überwachung

Informationen zu bestimmten Zertifizierungen für den Azure Rights Management-Dienst finden Sie im Abschnitt [Sicherheits-, Konformitäts-und gesetzliche Anforderungen](./what-is-azure-rms.md#security-compliance-and-regulatory-requirements) im Artikel [Was ist Azure RMS?](./what-is-azure-rms.md) . Zusätzlich:

- Informationen zu externen Zertifizierungen für Azure Information Protection: [Microsoft Azure Trust Center](https://azure.microsoft.com/support/trust-center/)

- FIPS 140-Informationen: [FIPS 140-Überprüfung](/windows/security/threat-protection/fips-140-validation)

Weitere ausführliche technische Informationen über die Funktionsweise der Schutztechnologie finden Sie unter [Funktionsweise von Azure RMS](./how-does-it-work.md). 

## <a name="service-level-agreements"></a>Vereinbarungen zum Servicelevel (SLAs)

- [SLA für Azure Information Protection](https://azure.microsoft.com/support/legal/sla/information-protection/v1_0/)

- [SLA für Azure Active Directory](https://azure.microsoft.com/support/legal/sla/active-directory/v1_0/)

- [SLA für Azure Key Vault](https://azure.microsoft.com/support/legal/sla/key-vault/v1_0/)

## <a name="documentation"></a>Dokumentation

- Dokumentation zu Azure Active Directory: [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-whatis)

- Microsoft 365 Dokumentation: [Microsoft 365 für Dokumentation und Ressourcen von Unternehmen](/Office365/Enterprise/)

