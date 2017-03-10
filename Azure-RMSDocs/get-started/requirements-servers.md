---
title: "Serverunterstützung für den Azure RMS-Datenschutz – AIP"
description: "Lokale Serverprodukte, die den Azure Rights Management-Dienst von Azure Information Protection über den Rights Management-Connector verwenden können."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 0278d07ae5afdfc95ffdf3945e5d3df7eae2f459
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten

>*Gilt für: Azure Information Protection, Office 365*

Bei Verwendung des Azure Rights Management-Connectors werden die folgenden lokalen Serverprodukte mit Azure Information Protection unterstützt. Dieser Connector dient als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und dem Azure Rights Management-Dienst, über den durch Azure Information Protection Office-Dokumente und E-Mails geschützt werden. 

Für die Verwendung des Connectors müssen Sie die Verzeichnissynchronisierung zwischen Ihren Active Directory-Gesamtstrukturen und Azure Active Directory konfigurieren.

-   **Exchange Server**:

    -   Exchange Server 2016

    -   Exchange Server 2013

    -   Exchange Server 2010

-   **Office SharePoint Server**:

    -   Office SharePoint Server 2016

    -   Office SharePoint Server 2013

    -   Office SharePoint Server 2010

-   **Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden**:

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Da Dateiserver, auf denen Windows Server 2008 R2 ausgeführt wird, über keine integrierte Taskaktion zum Anwenden des Rights Management-Schutzes verfügen, können Sie den Rights Management-Connector für dieses Szenario nicht verwenden. Sie können jedoch die Dateiklassifizierungsinfrastruktur und Azure RMS auf diesen Betriebssystemen verwenden, wenn Sie einen benutzerdefinierten Dateiverwaltungstask konfigurieren, über den eine Datei oder ein Skript ausgeführt wird, um die Dateien mithilfe von Azure RMS zu schützen. Beispielsweise ein Windows PowerShell-Skript, in dem die [AzureInformationProtection-Cmdlets](/powershell/azureinformationprotection/vlatest/aip) verwendet werden.
    > 
    > Sie können diese Cmdlets auch mit Servern mit höheren Versionen von Windows Server verwenden. Dies hat den Vorteil, dass diese Cmdlets alle Dateitypen schützen können. Der RMS-Connector schützt nur Office-Dateien. Anweisungen zur Vorgehensweise finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](../rms-client/configure-fci.md).

Der Rights Management-Connector wird unter Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 ausgeführt.

Weitere Informationen zum Konfigurieren des Rights Management-Connectors für diese lokalen Server finden Sie unter [Bereitstellen des Azure Rights Management-Connectors](../deploy-use/deploy-rms-connector.md).

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Voraussetzungen für Azure Rights Management](requirements-azure-rms.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]