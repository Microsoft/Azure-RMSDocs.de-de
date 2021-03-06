---
title: 'Vom Kunden verwaltet: Lebenszyklusvorgänge für AIP-Mandantenschlüssel'
description: Informationen zu den Lebenszyklusvorgängen, die relevant sind, wenn Ihr Mandantenschlüssel für Azure Information Protection von Ihnen verwaltet wird (BYOK-Szenario, „Bring Your Own Key“).
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/11/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.subservice: kms
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 662d38aefb6736d262f46047aaaffa62e8d528d5
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809408"
---
# <a name="customer-managed-tenant-key-life-cycle-operations"></a>Vom Kunden verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Wenn Ihr Mandantenschlüssel für Azure Information Protection von Ihnen verwaltet wird (BYOK-Szenario), finden Sie in den folgenden Abschnitten weitere Informationen zu den Lebenszyklusvorgängen, die für diese Topologie relevant sind.

## <a name="revoke-your-tenant-key"></a>Widerrufen Ihres Mandantenschlüssels

Es gibt nur wenige Szenarios, in denen Sie ggf. ihren Schlüssel widerrufen müssen, anstatt Sie neu zu konfigurieren. Wenn Sie Ihren Schlüssel widerrufen, können alle Inhalte, die mit diesem Schlüssel von Ihrem Mandanten geschützt wurden, nicht für alle Benutzer (einschließlich Microsoft, ihre globalen Administratoren und Administratoren) zugänglich sein, es sei denn, Sie haben eine Sicherung des Schlüssels, den Sie wiederherstellen können. Nachdem Sie Ihren Schlüssel widerrufen haben, können Sie erst dann neue Inhalte schützen, wenn Sie einen neuen Mandanten Schlüssel für Azure Information Protection erstellt und konfiguriert haben. 

Um Ihren vom Kunden verwalteten Mandanten Schlüssel zu widerrufen, ändern Sie in Azure Key Vault die Berechtigungen für den Schlüssel Tresor, der Ihren Azure Information Protection Mandanten Schlüssel enthält, sodass der Azure Rights Management-Dienst nicht mehr auf den Schlüssel zugreifen kann. Durch diese Aktion wird der Mandanten Schlüssel für Azure Information Protection wirksam widerrufen.

Wenn Sie Ihr Abonnement für Azure Information Protection kündigen, wird Ihr Mandantenschlüssel in Azure Information Protection nicht mehr verwendet. Es ist keine weitere Aktion erforderlich.

## <a name="rekey-your-tenant-key"></a>Neuerstellung Ihres Mandantenschlüssels

Die Neuerstellung eines Schlüssels wird auch als „Rollover“ bezeichnet. Wenn Sie diesen Vorgang ausführen, verwendet Azure Information Protection nicht mehr den vorhandenen Mandantenschlüssel zum Schützen von Dokumenten und E-Mails sondern einen anderen Schlüssel. Richtlinien und Vorlagen werden umgehend erneut signiert. Diese Umstellung erfolgt jedoch gestaffelt für vorhandene Kunden und Dienste, die Azure Information Protection verwenden. Daher werden neue Inhalte eine Zeit lang noch durch den alten Mandantenschlüssel geschützt.

Um einen neuen Schlüssel zu erstellen, müssen Sie das Mandantenschlüsselobjekt konfigurieren und den alternativen Schlüssel angeben, der verwendet werden soll. Anschließend wird der zuvor verwendete Schlüssel für Azure Information Protection automatisch als archiviert gekennzeichnet. Diese Konfiguration stellt sicher, dass der Inhalt, der mithilfe dieses Schlüssels geschützt wurde, weiterhin zugänglich ist.

Beispiele für Fälle, in denen Sie möglicherweise einen neuen Schlüssel für Azure Information Protection erstellen müssen:

- Ihr Unternehmen wurde in zwei oder mehr Unternehmen aufgeteilt. Wenn Sie Ihren Mandantenschlüssel neu erstellen, hat das neue Unternehmen keinen Zugriff auf neue Inhalte, die von Ihren Mitarbeitern veröffentlicht werden. Sie können auf den alten Inhalt zugreifen, wenn sie eine Kopie des alten Mandantenschlüssels besitzen.

- Sie möchten eine andere Schlüsselverwaltungstopologie verwenden. 

- Sie glauben, dass die Masterkopie Ihres Mandantenschlüssels (die in Ihrem Besitz befindliche Kopie) kompromittiert wurde.

Zur Nutzung eines anderen verwalteten Schlüssels können Sie entweder einen neuen Schlüssel in Azure Key Vault erstellen oder einen anderen, bereits in Azure Key Vault vorhandenen Schlüssel verwenden. Führen Sie anschließend dieselben Schritte aus wie beim Implementieren von BYOK für Azure Information Protection. 

1. Nur, wenn sich der neue Schlüssel in einem anderen Schlüssel Tresor befindet, den Sie bereits für Azure Information Protection verwenden: autorisieren Sie Azure Information Protection, den Schlüssel Tresor zu verwenden, indem Sie das Cmdlet [Set-azkeyvaultaccesspolicy](/powershell/module/az.keyvault/set-azkeyvaultaccesspolicy) verwenden.

1. Wenn Azure Information Protection den Schlüssel, den Sie verwenden möchten, nicht bereits kennen, führen Sie das Cmdlet [use-aipservicekeyvaultkey](/powershell/module/aipservice/use-aipservicekeyvaultkey) aus.

1. Konfigurieren Sie das Mandanten Schlüsselobjekt mithilfe des Cmdlets [Set-aipservicekeyproperties](/powershell/module/aipservice/set-aipservicekeyproperties) ausführen.

Weitere Informationen zu den jeweiligen Schritten erhalten Sie wie Folgt:

- Informationen zum erneuten Schlüssel für einen anderen Schlüssel, den Sie verwalten, finden Sie unter [Planen und Implementieren Ihres Azure Information Protection Mandanten Schlüssels](plan-implement-tenant-key.md).

    
    Wenn Sie für einen durch HSM geschützten Schlüssel, den Sie lokal erstellt und an Key Vault übermittelt haben, neue Schlüssel erstellen, können Sie die gleiche Sicherheitsumgebung sowie Zugriffskarten verwenden wie bei Ihrem aktuellen Schlüssel.

- Eine Anleitung zur Nutzung eines anderen, von Microsoft verwalteten Schlüssel finden Sie im Abschnitt [Neuerstellung Ihres Mandantenschlüssels](operations-microsoft-managed-tenant-key.md#rekey-your-tenant-key) für von Microsoft verwaltete Vorgänge.

## <a name="backup-and-recover-your-tenant-key"></a>Sicherung und Wiederherstellung Ihres Mandantenschlüssels

Da Sie Ihren Mandantenschlüssel verwalten, sind Sie verantwortlich für das Sichern des Schlüssels, den Azure Information Protection verwendet. 

Wenn Sie Ihren Mandanten Schlüssel lokal generiert haben, in einem nchiffre-HSM: um den Schlüssel zu sichern, sichern Sie die tokenschlüsseldatei, die World-Datei und die Administrator Karten. Wenn Sie Ihren Schlüssel in Azure Key Vault übertragen, speichert der Dienst die Tokenschlüsseldatei, um vor Fehlern der Dienstknoten zu schützen. Diese Datei ist an den Sicherheitsbereich für die bestimmte Azure-Region oder -Instanz gebunden. Sie sollten diese Tokenschlüsseldatei aber nicht als vollwertige Sicherung ansehen. Wenn Sie z. b. jemals eine nur-Text-Kopie Ihres Schlüssels zur Verwendung außerhalb eines nchiffre-HSM benötigen, kann Azure Key Vault ihn nicht für Sie abrufen, da er nur über eine nicht wiederherstellbare Kopie verfügt.

Azure Key Vault besitzt ein [Sicherungs-Cmdlet](/powershell/module/az.keyvault/backup-azkeyvaultkey), das Sie zum Sichern eines Schlüssels verwenden können, indem Sie dieses herunterladen und in einer Datei speichern. Da der heruntergeladene Inhalt verschlüsselt ist, kann dieser nicht außerhalb von Azure Key Vault verwendet werden. 

## <a name="export-your-tenant-key"></a>Exportieren Ihres Mandantenschlüssels

Wenn Sie BYOK verwenden, können Sie Ihren Mandantenschlüssel nicht aus Azure Key Vault oder Azure Information Protection exportieren. Die Kopie in Azure Key Vault ist nicht wiederherstellbar. 

## <a name="respond-to-a-breach"></a>Reaktion auf eine Sicherheitsverletzung

Kein Sicherheitssystem, egal wie stark es ist, kommt vollständig ohne einen Prozess für Reaktion auf eine Sicherheitsverletzung aus. Ihr Mandantenschlüssel könnte kompromittiert oder gestohlen werden. Auch wenn er gut geschützt ist, können Sicherheitslücken in der Schlüsseltechnologie der aktuellen Generation oder bei aktuellen Schlüssellängen und Algorithmen auftreten.

Microsoft hat ein dediziertes Team, um auf Sicherheitsvorfälle bei eigenen Produkten und Diensten zu reagieren. Sobald ein glaubhafter Bericht über einen Vorfall vorliegt, kümmert sich dieses Team um die Untersuchung des Umfangs, der Ursache und um Abhilfen. Wenn sich dieser Vorfall auf Ihre Assets auswirkt, benachrichtigt Microsoft den globalen Administrator Ihres Mandanten per e-Mail.

Wenn bei Ihnen eine Sicherheitsverletzung aufgetreten ist, hängt die beste Vorgehensweise auf Ihrer und auf Microsofts Seite vom Umfang der Sicherheitsverletzung ab. Microsoft führt diesen Prozess gemeinsam mit Ihnen durch. In der folgenden Tabelle finden Sie einige typische Situationen und die wahrscheinliche Reaktion darauf, obgleich die exakte Reaktion immer von allen Informationen abhängt, die im Rahmen der Untersuchung gewonnen werden.

|Beschreibung des Vorfalls|Wahrscheinliche Reaktion|
|------------------------|-------------------|
|Ihr Mandantenschlüssel wurde abgegriffen.|Erstellen Sie Ihren Mandantenschlüssel neu. Weitere Informationen finden [Sie unter neuschlüssel Ihres Mandanten Schlüssels](#rekey-your-tenant-key).|
|Eine nicht autorisierte Person oder Schadsoftware hat Rechte zur Verwendung Ihres Mandantenschlüssels erlangt, aber nicht den Schlüssel selbst.|Die Neuerstellung Ihres Mandantenschlüssels schafft hierbei keine Abhilfe, stattdessen ist eine Ursachenanalyse erforderlich. Wenn ein Prozess- oder Softwarefehler dafür verantwortlich war, dass die nicht autorisierte Person Zugriff erlangt hat, muss dieser Zustand behoben werden.|
|Entdeckte Sicherheitslücke in HSM-Technologie der aktuellen Generation.|Microsoft muss die HSMs aktualisieren. Wenn es Anlass gibt, zu glauben, dass durch die Sicherheitslücke Schlüssel kompromittiert wurden, weist Microsoft alle Kunden an, ihre Mandantenschlüssel neu zu erstellen.|
|Im RSA-Algorithmus oder bei der Schlüssellänge entdeckte Sicherheitslücken oder auch Brute-Force-Angriffe werden von der Rechenleistung her möglich.|Microsoft muss Azure Key Vault oder Azure Information Protection so aktualisieren, dass neue, robuste Algorithmen und längere Schlüssellängen unterstützt werden, und alle Kunden anweisen, ihre Mandantenschlüssel neu zu erstellen.|
| | |