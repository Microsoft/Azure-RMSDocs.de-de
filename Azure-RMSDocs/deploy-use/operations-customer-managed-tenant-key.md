---
# required metadata

title: "Vom Kunden verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel | Azure RMS"
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---


# Vom Kunden verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel

*Gilt für: Azure Rights Management, Office 365*

Wenn Ihr Mandantenschlüssel für Azure RMS von Ihnen verwaltet wird (BYOK-Szenario, „Bring Your Own Key“), finden Sie in den folgenden Abschnitten weitere Informationen zu den Lebenszyklusvorgängen, die für diese Topologie relevant sind.

## Widerrufen Ihres Mandantenschlüssels
Wenn Sie Ihr Abonnement von Azure RMS kündigen, beendet Azure RMS die Verwendung Ihres Mandantenschlüssels, und von Ihnen ist keine weitere Aktion mehr erforderlich.

## Neuvergabe (Rollover) Ihres Mandantenschlüssels
Die Neuvergabe Ihres Schlüssels wird auch als „Rollover“ bezeichnet. Führen Sie eine Neuvergabe Ihres Mandantenschlüssels nur durch, wenn es wirklich notwendig ist. Ältere Clients wie Office 2010 wurden nicht darauf ausgelegt, problemlos mit Schlüsseländerungen umzugehen. In diesem Szenario müssen Sie den RMS-Zustand auf Computern löschen, indem Sie eine Gruppenrichtlinie oder einen entsprechenden Mechanismus verwenden. Es gibt jedoch einige berechtigte Ereignisse, die Sie zwingen können, Ihren Mandantenschlüssel neu zu vergeben. Beispiel:

-   Ihr Unternehmen wurde in zwei oder mehr Unternehmen aufgeteilt. Wenn Sie Ihren Mandantenschlüssel neu vergeben, hat das neue Unternehmen keinen Zugriff auf neue Inhalte, die von Ihren Mitarbeitern veröffentlicht werden. Sie können auf den alten Inhalt zugreifen, wenn sie eine Kopie des alten Mandantenschlüssels besitzen.

-   Sie glauben, dass die Masterkopie Ihres Mandantenschlüssels (die in Ihrem Besitz befindliche Kopie) kompromittiert wurde.

Wenn Sie Ihren Mandantenschlüssel neu vergeben, wird neuer Inhalt unter Verwendung des neuen Mandantenschlüssels geschützt. Dies geschieht in einer gestaffelten Weise, sodass für einen gewissen Zeitraum neue Inhalte noch teilweise durch den alten Mandantenschlüssel geschützt sind. Zuvor geschützte Inhalte bleiben durch den alten Mandantenschlüssel geschützt. Um dieses Szenario zu unterstützen, behält Azure RMS Ihren alten Mandantenschlüssel bei, damit es Lizenzen für alte Inhalte erteilen kann.

Gehen Sie wie folgt vor, wenn Sie Ihren Mandantenschlüssel neu vergeben möchten: Generieren und erstellen Sie einen neuen Schlüssel über das Internet oder persönlich, indem Sie die Verfahren im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](..\plan-design\plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) im Thema [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](..\plan-design\plan-implement-tenant-key.md) verwenden.

## Sicherung und Wiederherstellung Ihres Mandantenschlüssels
Sie sind für das Sichern Ihres Mandantenschlüssels verantwortlich. Wenn Sie Ihren Mandantenschlüssel in einem Thales HSM generiert haben, sichern Sie einfach die Tokenschlüsseldatei, die World-Datei und die Administrator Cards, um den Mandantenschlüssel zu sichern.

Wenn Sie den Schlüssel gemäß den Verfahren im Abschnitt [Implementierung von „Bring Your Own Key“ (BYOK)](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) des Artikels [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md) übertragen haben, speichert Azure RMS die Tokenschlüsseldatei dauerhaft, um Schutz vor Ausfällen jeglicher Azure RMS-Knoten zu bieten. Sie sollten dies aber nicht als vollwertige Sicherung ansehen. Wenn Sie nämlich jemals eine Klartextkopie Ihres Schlüssels zur Verwendung außerhalb eines Thales HSM benötigen, kann Azure RMS diese nicht abrufen, weil er lediglich über eine nicht wiederherstellbare Kopie verfügt.

## Exportieren Ihres Mandantenschlüssels
Wenn Sie BYOK verwenden, können Sie Ihren Mandantenschlüssel nicht aus Azure RMS exportieren. Die Kopie in Azure RMS ist nicht wiederherstellbar. Wenn Sie diesen Schlüssel löschen möchten, sodass er nicht mehr verwendet werden kann, wenden Sie sich an Microsoft-Kundendienst und -Support (CSS).

## Reaktion auf eine Sicherheitsverletzung
Kein Sicherheitssystem, egal wie stark es ist, kommt vollständig ohne einen Prozess für Reaktion auf eine Sicherheitsverletzung aus. Ihr Mandantenschlüssel könnte kompromittiert oder gestohlen werden. Auch wenn er gut geschützt ist, können Sicherheitslücken in der HSM-Technologie der aktuellen Generation oder bei aktuellen Schlüssellängen und Algorithmen gefunden werden.

Microsoft hat ein dediziertes Team, um auf Sicherheitsvorfälle bei eigenen Produkten und Diensten zu reagieren. Sobald ein glaubhafter Bericht über einen Vorfall vorliegt, kümmert sich dieses Team um die Untersuchung des Umfangs, der Ursache und um Abhilfen. Wenn sich dieser Vorfall auf Ihre Objekte auswirkt, wird Ihr Azure RMS-Mandantenadministrator per E-Mail von Microsoft unter der Adresse benachrichtig, die Sie beim Abschluss des Abonnements angegeben haben.

Wenn bei Ihnen eine Sicherheitsverletzung aufgetreten ist, hängt die beste Vorgehensweise auf Ihrer und auf Microsofts Seite vom Umfang der Sicherheitsverletzung ab. Microsoft führt diesen Prozess gemeinsam mit Ihnen durch. In der folgenden Tabelle finden Sie einige typische Situationen und die wahrscheinliche Reaktion darauf, obgleich die exakte Reaktion immer von allen Informationen abhängt, die im Rahmen der Untersuchung gewonnen werden.

|Beschreibung des Vorfalls|Wahrscheinliche Reaktion|
|------------------------|-------------------|
|Ihr Mandantenschlüssel wurde abgegriffen.|Vergeben Sie Ihren Mandantenschlüssel neu. Weitere Informationen finden Sie unter [Neuvergabe (Rollover) Ihres Mandantenschlüssels](#re-key-your-tenant-key)..|
|Eine nicht autorisierte Person oder Schadsoftware hat Rechte zur Verwendung Ihres Mandantenschlüssels erlangt, aber nicht den Schlüssel selbst.|Die Neuvergabe (Rollover) Ihres Mandantenschlüssels schafft hierbei keine Abhilfe und erfordert eine Ursachenanalyse. Wenn ein Prozess- oder Softwarefehler dafür verantwortlich war, dass die nicht autorisierte Person Zugriff erlangt hat, muss dieser Zustand behoben werden.|
|Entdeckte Sicherheitslücke in HSM-Technologie der aktuellen Generation.|Microsoft muss die HSMs aktualisieren. Wenn es Anlass gibt, zu glauben, dass durch die Sicherheitslücke Schlüssel kompromittiert wurden, wird Microsoft alle Kunden anweisen, ihre Mandantenschlüssel zu erneuern.|
|Im RSA-Algorithmus oder bei der Schlüssellänge entdeckte Sicherheitslücken oder auch Brute-Force-Angriffe werden von der Rechenleistung her möglich.|Microsoft muss den Azure RMS so aktualisieren, dass neue Algorithmen und längere Schlüssellängen unterstützt werden, die robust sind, und alle Kunden anweisen, ihre Mandantenschlüssel zu erneuern.|




<!--HONumber=Apr16_HO4-->


