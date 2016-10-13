---
title: "Vom Kunden verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel | Azure Information Protection"
description: "Informationen zu den Lebenszyklusvorgängen, die relevant sind, wenn Ihr Mandantenschlüssel für Azure Information Protection von Ihnen verwaltet wird (BYOK-Szenario, „Bring Your Own Key“)."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c5b19c59-812d-420c-9c54-d9776309636c
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: d5b6a1fc3fa0a19f3a6b65aa7b8815eda7432cd7
ms.openlocfilehash: b380bc6662ee374b5a750de6e1f50f417f5dd900


---


# Vom Kunden verwaltet: Lebenszyklusvorgänge für Mandantenschlüssel

>*Gilt für: Azure Information Protection, Office 365*

Wenn Ihr Mandantenschlüssel für Azure Information Protection von Ihnen verwaltet wird (BYOK-Szenario, „Bring Your Own Key“), finden Sie in den folgenden Abschnitten weitere Informationen zu den Lebenszyklusvorgängen, die für diese Topologie relevant sind.

## Widerrufen Ihres Mandantenschlüssels
In Azure Key Vault können Sie die Berechtigungen für den Schlüsseltresor mit Ihrem Azure Information Protection-Mandantenschlüssel ändern, sodass der Azure Rights Management-Dienst nicht mehr auf den Schlüssel zugreifen kann. In diesem Fall kann jedoch niemand Dokumente und E-Mails öffnen, die Sie zuvor mit dem Azure Rights Management-Dienst geschützt haben.

Wenn Sie Ihr Abonnement für Azure Information Protection kündigen, wird Ihr Mandantenschlüssel in Azure Information Protection nicht mehr verwendet. Es ist keine weitere Aktion erforderlich.


## Neuvergabe (Rollover) Ihres Mandantenschlüssels
Die Neuvergabe Ihres Schlüssels wird auch als „Rollover“ bezeichnet. Führen Sie eine Neuvergabe Ihres Mandantenschlüssels nur durch, wenn es wirklich notwendig ist. Ältere Clients wie Office 2010 wurden nicht darauf ausgelegt, problemlos mit Schlüsseländerungen umzugehen. In diesem Szenario müssen Sie den Rights Management-Status auf Computern löschen, indem Sie eine Gruppenrichtlinie oder einen entsprechenden Mechanismus verwenden. Es gibt jedoch einige berechtigte Ereignisse, die Sie zwingen können, Ihren Mandantenschlüssel neu zu vergeben. Beispiel:

-   Ihr Unternehmen wurde in zwei oder mehr Unternehmen aufgeteilt. Wenn Sie Ihren Mandantenschlüssel neu vergeben, hat das neue Unternehmen keinen Zugriff auf neue Inhalte, die von Ihren Mitarbeitern veröffentlicht werden. Sie können auf den alten Inhalt zugreifen, wenn sie eine Kopie des alten Mandantenschlüssels besitzen.

-   Sie glauben, dass die Masterkopie Ihres Mandantenschlüssels (die in Ihrem Besitz befindliche Kopie) kompromittiert wurde.

Wenn Sie Ihren Mandantenschlüssel neu vergeben, wird neuer Inhalt unter Verwendung des neuen Mandantenschlüssels geschützt. Dies geschieht in einer gestaffelten Weise, sodass für einen gewissen Zeitraum neue Inhalte noch teilweise durch den alten Mandantenschlüssel geschützt sind. Zuvor geschützte Inhalte bleiben durch den alten Mandantenschlüssel geschützt. Zur Unterstützung dieses Szenarios wird Ihr alter Mandantenschlüssel in Azure Information Protection beibehalten, damit Lizenzen für alte Inhalte erteilt werden können.

Um Ihren Mandantenschlüssel zu erneuern, müssen Sie zunächst Ihren Azure Information Protection-Mandantenschlüssel in Key Vault erneuern. Führen Sie dann das Cmdlet „Add-AadrmKeyVaultKey“ erneut aus, und geben Sie dabei die neue Schlüssel-URL an.

## Sicherung und Wiederherstellung Ihres Mandantenschlüssels
Sie sind für das Sichern Ihres Mandantenschlüssels verantwortlich. Wenn Sie Ihren Mandantenschlüssel in einem Thales HSM generiert haben, sichern Sie einfach die Tokenschlüsseldatei, die World-Datei und die Administrator Cards, um den Mandantenschlüssel zu sichern.

Da Sie den Schlüssel gemäß den Verfahren im Artikel [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md) im Abschnitt [Implementieren von „Bring Your Own Key“ (BYOK)](../plan-design/plan-implement-tenant-key.md#implementing-your-azure-rights-management-tenant-key) übertragen haben, speichert Key Vault die Tokenschlüsseldatei dauerhaft, um Schutz vor Ausfällen jeglicher Dienstknoten zu bieten. Diese Datei ist an den Sicherheitsbereich für die bestimmte Azure-Region oder -Instanz gebunden. Sie sollten dies aber nicht als vollwertige Sicherung ansehen. Wenn Sie beispielsweise jemals eine Klartextkopie Ihres Schlüssels zur Verwendung außerhalb eines Thales-HSM benötigen, kann Azure Key Vault diese nicht abrufen, weil die Lösung lediglich über eine nicht wiederherstellbare Kopie verfügt.

## Exportieren Ihres Mandantenschlüssels
Wenn Sie BYOK verwenden, können Sie Ihren Mandantenschlüssel nicht aus Azure Key Vault oder Azure Information Protection exportieren. Die Kopie in Azure Key Vault ist nicht wiederherstellbar. 

## Reaktion auf eine Sicherheitsverletzung
Kein Sicherheitssystem, egal wie stark es ist, kommt vollständig ohne einen Prozess für Reaktion auf eine Sicherheitsverletzung aus. Ihr Mandantenschlüssel könnte kompromittiert oder gestohlen werden. Auch wenn er gut geschützt ist, können Sicherheitslücken in der HSM-Technologie der aktuellen Generation oder bei aktuellen Schlüssellängen und Algorithmen gefunden werden.

Microsoft hat ein dediziertes Team, um auf Sicherheitsvorfälle bei eigenen Produkten und Diensten zu reagieren. Sobald ein glaubhafter Bericht über einen Vorfall vorliegt, kümmert sich dieses Team um die Untersuchung des Umfangs, der Ursache und um Abhilfen. Wenn sich dieser Vorfall auf Ihre Objekte auswirkt, wird Ihr Azure Information Protection-Mandantenadministrator per E-Mail von Microsoft unter der Adresse benachrichtigt, die Sie beim Abschluss des Abonnements angegeben haben.

Wenn bei Ihnen eine Sicherheitsverletzung aufgetreten ist, hängt die beste Vorgehensweise auf Ihrer und auf Microsofts Seite vom Umfang der Sicherheitsverletzung ab. Microsoft führt diesen Prozess gemeinsam mit Ihnen durch. In der folgenden Tabelle finden Sie einige typische Situationen und die wahrscheinliche Reaktion darauf, obgleich die exakte Reaktion immer von allen Informationen abhängt, die im Rahmen der Untersuchung gewonnen werden.

|Beschreibung des Vorfalls|Wahrscheinliche Reaktion|
|------------------------|-------------------|
|Ihr Mandantenschlüssel wurde abgegriffen.|Vergeben Sie Ihren Mandantenschlüssel neu. Weitere Informationen finden Sie unter [Neuvergabe (Rollover) Ihres Mandantenschlüssels](#re-key-your-tenant-key).|
|Eine nicht autorisierte Person oder Schadsoftware hat Rechte zur Verwendung Ihres Mandantenschlüssels erlangt, aber nicht den Schlüssel selbst.|Die Neuvergabe (Rollover) Ihres Mandantenschlüssels schafft hierbei keine Abhilfe und erfordert eine Ursachenanalyse. Wenn ein Prozess- oder Softwarefehler dafür verantwortlich war, dass die nicht autorisierte Person Zugriff erlangt hat, muss dieser Zustand behoben werden.|
|Entdeckte Sicherheitslücke in HSM-Technologie der aktuellen Generation.|Microsoft muss die HSMs aktualisieren. Wenn es Anlass gibt, zu glauben, dass durch die Sicherheitslücke Schlüssel kompromittiert wurden, wird Microsoft alle Kunden anweisen, ihre Mandantenschlüssel zu erneuern.|
|Im RSA-Algorithmus oder bei der Schlüssellänge entdeckte Sicherheitslücken oder auch Brute-Force-Angriffe werden von der Rechenleistung her möglich.|Microsoft muss Azure Key Vault oder Azure Information Protection so aktualisieren, dass neue, robuste Algorithmen und längere Schlüssellängen unterstützt werden, und alle Kunden anweisen, ihre Mandantenschlüssel zu erneuern.|





<!--HONumber=Sep16_HO4-->


