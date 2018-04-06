---
title: Der Client für Azure Information Protection
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ROBOTS: noindex,nofollow
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: efbc164b27e1dfe1b839e2ace893c4e3c5e656aa
ms.sourcegitcommit: dbbfadc72f4005f81c9f28c515119bc3098201ce
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2018
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann der Azure Information Protection-Client oder der Rights Management-Client sein. Er ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden. 

- Der Dienst wird in der Cloud (Azure Information Protection verwendet den Azure Rights Management-Dienst für den Schutz von Daten) oder lokal (Active Directory Rights Management Services) ausgeführt. 

Der Azure Information Protection-Client unterstützt zusätzlich zum Schutz noch Klassifizierungen und Bezeichnungen. Dieser Client kann in Office-Anwendung integriert werden und muss separat installiert werden.

Der Rights Management-Client (RMS) wird automatisch mit einigen Anwendungen installiert, z. B. Office-Anwendungen, der Azure Information Protection-Client und RMS-fähige Anwendungen von Softwareanbietern. Er kann jedoch auch einzeln installiert werden, was z. B. Entwickler unterstützt, die den Rights Management-Schutz in Branchenanwendungen integrieren möchten.

Die folgende Dokumentation enthält weitere Informationen zum Bereitstellen und Verwenden dieser Clients, die in Verbindung mit Azure Information Protection und Active Directory Rights Management Services verwendet werden können, um die Daten Ihrer Organisation zu schützen:

- [Azure Information Protection-Client](AIP-client.md)

- [Hinweise zur Bereitstellung des RMS-Clients](client-deployment-notes.md)

- [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](configure-fci.md)

- [Rights Management-Freigabeanwendung für Windows](sharing-app-windows.md)

Beachten Sie, dass die Rights Management-Freigabeanwendung für Windows und das RMS Protection Tool jetzt durch den Azure Information Protection-Client ersetzt wurden. 


## <a name="see-also"></a>Siehe auch
[Vergleich von Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]