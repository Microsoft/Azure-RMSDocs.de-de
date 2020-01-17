---
title: Serverunterstützung für den Azure RMS-Datenschutz – AIP
description: Lokale Serverprodukte, die den Azure Rights Management-Dienst von Azure Information Protection über den Rights Management-Connector verwenden können.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.subservice: prereqs
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: e8ce88ed734177fd35c733f115f157c94b70627d
ms.sourcegitcommit: ad3e55f8dfccf1bc263364990c1420459c78423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/16/2020
ms.locfileid: "76117934"
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

    -   Windows Server 2012 R2


    > 
    > Sie können diese Cmdlets auch mit Servern mit höheren Versionen von Windows Server verwenden. Dies hat den Vorteil, dass diese Cmdlets alle Dateitypen schützen können. Der RMS-Connector schützt nur Office-Dateien. Anweisungen zur Vorgehensweise finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](./rms-client/configure-fci.md).

Der Rights Management-Connector wird unter Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 unterstützt.

Weitere Informationen zum Konfigurieren des Rights Management-Connectors für diese lokalen Server finden Sie unter [Bereitstellen des Azure Rights Management-Connectors](deploy-rms-connector.md).

## <a name="next-steps"></a>Nächste Schritte
Weitere Anforderungen finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).
