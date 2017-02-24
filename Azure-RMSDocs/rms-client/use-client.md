---
title: Der Client | Azure Information Protection
description: "Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ROBOTS: noindex,nofollow
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 190b5d2a25dc9479aa2ba34fd884795e0de40238
ms.openlocfilehash: f52f3e04f41e33828bd9a9c5c1aad3ef460b2d23


---

# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, Azure Rights Management, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1.*

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


## <a name="see-also"></a>Weitere Informationen:
[Vergleich von Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Feb17_HO2-->


