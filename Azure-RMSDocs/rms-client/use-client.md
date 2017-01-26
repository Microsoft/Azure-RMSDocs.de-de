---
title: Der Client | Azure Information Protection
description: "Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a6fa85be-f92a-4e00-9efc-9dbfd4dfbfcb
ROBOTS: noindex,nofollow
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ed836a1f64ccb3f7e176ad19d27af1021c423cd9
ms.openlocfilehash: 11f4be72cfe1ab50286254bd4de18b66def0a6cb


---

# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>*Gilt für: Active Directory Rights Management Services, Azure Rights Management, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1.*

Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Dokumente und E-Mails einer Organisation bereit:

- Der Client kann der Azure Information Protection-Client oder der Rights Management-Client sein. Er ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden. 

- Der Dienst wird in der Cloud (Azure Information Protection verwendet den Azure Rights Management-Dienst für den Schutz von Daten) oder lokal (Active Directory Rights Management Services) ausgeführt. 

Der Azure Information Protection-Client unterstützt zusätzlich zum Schutz noch Klassifizierungen und Bezeichnungen. Dieser Client kann in Office-Anwendung integriert werden und muss separat installiert werden.

Der RMS-Client (Rights Management) wird automatisch mit einigen Anwendungen installiert, z.B. Office-Anwendungen, die RMS-Freigabeanwendung und RMS-fähige Anwendungen von Softwareherstellern. Er kann jedoch auch einzeln installiert werden, was z.B. Entwickler unterstützt, die den Rights Management-Schutz in Ihre Branchenanwendungen integrieren möchten, sowie Administratoren oder Hauptbenutzer, die viele Dateien mit dem RMS Protection Tool schützen möchten.

Die folgende Dokumentation enthält weitere Informationen zum Bereitstellen und Verwenden dieser Clients, die in Verbindung mit Azure Information Protection und Active Directory Rights Management Services verwendet werden können, um die Daten Ihrer Organisation zu schützen:

- [Installieren des Azure Information Protection-Clients](info-protect-client.md)

- [Hinweise zur Bereitstellung des RMS-Clients](client-deployment-notes.md)

- [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](configure-fci.md)

- [Rights Management-Freigabeanwendung für Windows](sharing-app-windows.md)


## <a name="see-also"></a>Weitere Informationen:
[Vergleich von Azure Information Protection und AD RMS](../understand-explore/compare-azure-rms-ad-rms.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]


<!--HONumber=Jan17_HO4-->


