---
title: Ihr Azure Information Protection-Mandantenschlüssel
description: Anstatt Microsoft den Stamm Schlüssel für Azure Information Protection zu verwalten, empfiehlt es sich, diesen Schlüssel (als "Bring your own Key" oder Byok bezeichnet) für Ihren Mandanten zu erstellen und zu verwalten, um bestimmte Vorschriften einzuhalten.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/14/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 35c898ded852970e380c8061ba8f97d040860017
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97386388"
---
# <a name="planning-and-implementing-your-azure-information-protection-tenant-key"></a>Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Der Azure Information Protection-Mandantenschlüssel ist ein Stammschlüssel für Ihre Organisation. Andere Schlüssel können von diesem Stamm Schlüssel abgeleitet werden, einschließlich Benutzer Schlüsseln, Computer Schlüsseln oder Dokument Verschlüsselungsschlüsseln. Wenn Azure Information Protection diese Schlüssel für Ihre Organisation verwendet, werden Sie kryptografisch mit Ihrem Azure Information Protection root-Mandanten Schlüssel verkettet.

Zusätzlich zum Mandanten Stamm Schlüssel benötigt Ihre Organisation möglicherweise lokale Sicherheit für bestimmte Dokumente. Der lokale Schlüsselschutz wird in der Regel nur für eine kleine Menge an Inhalten benötigt und daher mit einem Mandanten Stamm Schlüssel konfiguriert.

## <a name="azure-information-protection-key-types"></a>Azure Information Protection Schlüsseltypen

Der Stamm Schlüssel Ihres Mandanten kann wie folgt lauten:

- [Von Microsoft generiert](#tenant-root-keys-generated-by-microsoft)
- Wird von Kunden mit [Bring your own Key-Schutz (Byok)](#bring-your-own-key-byok-protection) generiert.

Wenn Sie über äußerst sensiblen Inhalt verfügen, der zusätzlichen, lokalen Schutz erfordert, empfehlen wir die Verwendung von [Double Key Encryption (DKE)](#double-key-encryption-dke).

> [!TIP]
> Wenn Sie den klassischen Client verwenden und zusätzlichen lokalen Schutz benötigen, verwenden Sie stattdessen [Hold Your Own Key (Hyok)](#hold-your-own-key-hyok) .
>

## <a name="tenant-root-keys-generated-by-microsoft"></a>Von Microsoft generierte Mandanten Stamm Schlüssel

Der Standardschlüssel, der automatisch von Microsoft generiert wird, ist der Standardschlüssel, der ausschließlich für Azure Information Protection verwendet wird, um die meisten Aspekte des Lebenszyklus Ihres Mandanten Schlüssels zu verwalten.

Verwenden Sie weiterhin den standardmäßigen Microsoft-Schlüssel, wenn Sie Azure Information Protection schnell und ohne spezielle Hardware, Software oder ein Azure-Abonnement bereitstellen möchten. Beispiele hierfür sind das Testen von Umgebungen oder Organisationen ohne gesetzliche Anforderungen für die Schlüsselverwaltung.

Für den Standardschlüssel sind keine weiteren Schritte erforderlich, und Sie können direkt zu den ersten Schritten [mit Ihrem](get-started-tenant-root-keys.md)Mandanten Stamm Schlüssel wechseln.

> [!NOTE]
> Der von Microsoft generierte Standardschlüssel ist die einfachste Option mit dem niedrigsten Verwaltungsaufwand.
>
> In den meisten Fällen wissen Sie möglicherweise nicht einmal, dass Sie über einen Mandanten Schlüssel verfügen, da Sie sich für Azure Information Protection registrieren können und der Rest des Schlüssel Verwaltungsprozesses von Microsoft verarbeitet wird.

## <a name="bring-your-own-key-byok-protection"></a>Bring your own Key-Schutz (Byok)

Byok-Protection verwendet Schlüssel, die von Kunden erstellt werden, entweder in der Azure Key Vault oder lokal in der Kundenorganisation. Diese Schlüssel werden dann zur weiteren Verwaltung an Azure Key Vault übertragen.

Verwenden Sie Byok, wenn Ihre Organisation Konformitäts Bestimmungen für die Schlüsselgenerierung hat, einschließlich der Kontrolle über alle Lebenszyklus Vorgänge. Dies ist beispielsweise der Fall, wenn Ihr Schlüssel durch ein Hardware Sicherheitsmodul geschützt werden muss.

Weitere Informationen finden Sie unter [Konfigurieren des Byok-Schutzes](byok-price-restrictions.md). 

Nachdem Sie die Konfiguration durchgeführt haben, fahren Sie [mit dem ersten Einstieg in ihren](get-started-tenant-root-keys.md) Mandanten Stamm Schlüssel fort, um weitere Informationen zum verwenden und Verwalten Ihres Schlüssels

## <a name="double-key-encryption-dke"></a>Double Key Encryption (DKE)

**Relevant für**: nur AIP Unified Bezeichnung Client

Der DKE-Schutz bietet zusätzliche Sicherheit für Ihre Inhalte, indem zwei Schlüssel verwendet werden: eine, die von Microsoft in Azure erstellt und gespeichert wird, und eine andere, die vom Kunden erstellt und gespeichert wird.

Die DKE erfordert, dass beide Schlüssel auf geschützte Inhalte zugreifen, um sicherzustellen, dass Microsoft und andere dritte niemals auf geschützte Daten zugreifen können.

DKE kann entweder in der Cloud oder lokal bereitgestellt werden und bietet so eine vollständige Flexibilität für Speicherorte.

Verwenden Sie DKE, wenn Ihre Organisation:

- Sie möchten sicherstellen, dass nur Sie in allen Fällen geschützte Inhalte entschlüsseln können.
- Sie möchten nicht, dass Microsoft selbst Zugriff auf geschützte Daten hat.
- Verfügt über gesetzliche Anforderungen, um Schlüssel innerhalb einer geografischen Grenze zu halten. Mit DKE werden Kundenschlüssel im Kunden Rechenzentrum verwaltet.

> [!NOTE]
> DKE ähnelt dem Feld für die Sicherheitsüberprüfung, bei dem sowohl ein Bank Schlüssel als auch ein Kundenschlüssel erforderlich sind, um Zugriff zu erhalten.
> Der DKE-Schutz erfordert sowohl den von Microsoft gehaltenen Schlüssel als auch den Kundenschlüssel, um geschützte Inhalte zu entschlüsseln.

Weitere Informationen finden Sie unter [doppelte Schlüssel Verschlüsselung](/microsoft-365/compliance/double-key-encryption) in der Microsoft 365-Dokumentation.

## <a name="hold-your-own-key-hyok"></a>Hold Your Own Key (Hyok)

**Relevant für**: nur AIP Classic Client

Hyok-Protection verwendet einen Schlüssel, der von Kunden erstellt und gespeichert wird, an einem Standort, der von der Cloud isoliert ist. Da Hyok-Protection nur den Zugriff auf Daten für lokale Anwendungen und Dienste ermöglicht, verfügen Kunden, die Hyok verwenden, auch über einen cloudbasierten Schlüssel für clouddokumente.

Verwenden Sie Hyok für folgende Dokumente:

- Auf nur wenige Personen beschränkt
- Nicht freigegeben außerhalb der Organisation
- Werden nur im internen Netzwerk verwendet.

Diese Dokumente verfügen in der Regel über die höchste Klassifizierung in Ihrer Organisation, als "Oberstes Geheimnis".

Inhalt kann nur dann mit dem Hyok-Schutz verschlüsselt werden, wenn Sie über den klassischen Client verfügen. Wenn Sie jedoch Hyok-geschützte Inhalte haben, können Sie Sie sowohl im klassischen als auch im einheitlichen Bezeichnungs Client anzeigen.  

Weitere Informationen finden Sie unter [Hold Your Own Key (Hyok) Details](configure-adrms-restrictions.md).

