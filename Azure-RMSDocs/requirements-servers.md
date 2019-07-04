---
title: Serverunterstützung für den Azure RMS-Datenschutz – AIP
description: Lokale Serverprodukte, die den Azure Rights Management-Dienst von Azure Information Protection über den Rights Management-Connector verwenden können.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/18/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e94d624c1fa59d44399b9c83959534d75c912d6b
ms.sourcegitcommit: 6c6fda77e131e071c94c2a2fd7b27e4031266fa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/03/2019
ms.locfileid: "67544975"
---
# <a name="on-premises-servers-that-support-azure-rights-management-data-protection"></a>Lokale Server mit Unterstützung für den Azure Rights Management-Schutz von Daten

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

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

    -   Windows Server 2016

    -   Windows Server 2012 R2

    -   Windows Server 2012

    > [!NOTE]
    > Da Dateiserver, auf denen Windows Server 2008 R2 ausgeführt wird, über keine integrierte Taskaktion zum Anwenden des Rights Management-Schutzes verfügen, können Sie den Rights Management-Connector für dieses Szenario nicht verwenden. Sie können jedoch die Dateiklassifizierungsinfrastruktur und Azure RMS auf diesen Betriebssystemen verwenden, wenn Sie einen benutzerdefinierten Dateiverwaltungstask konfigurieren, über den eine Datei oder ein Skript ausgeführt wird, um die Dateien mithilfe von Azure RMS zu schützen. Beispielsweise ein Windows PowerShell-Skript, in dem die [AzureInformationProtection-Cmdlets](/powershell/azureinformationprotection/vlatest/aip) verwendet werden.
    > 
    > Sie können diese Cmdlets auch mit Servern mit höheren Versionen von Windows Server verwenden. Dies hat den Vorteil, dass diese Cmdlets alle Dateitypen schützen können. Der RMS-Connector schützt nur Office-Dateien. Anweisungen zur Vorgehensweise finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](./rms-client/configure-fci.md).

Der Rights Management-Connector wird unter Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 ausgeführt.

Weitere Informationen zum Konfigurieren des Rights Management-Connectors für diese lokalen Server finden Sie unter [Bereitstellen des Azure Rights Management-Connectors](deploy-rms-connector.md).

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
