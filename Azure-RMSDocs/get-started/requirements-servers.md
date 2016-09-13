---
title: "Azure RMS-Anforderungen: Lokale Server, die Azure Rights Management unterstützen | Azure RMS"
description: "Identifizieren Sie die lokalen Serverprodukte, die mit Azure RMS unterstützt werden, wenn Sie den Azure RMS-Connector verwenden."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: e7d91f2d-d6a7-4c7e-821f-c94e4be9967d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 81426cf43f31625c6e83d443fa925f6426eb89da
ms.openlocfilehash: 0f9f1dc09d1b0d831b1c96d25b7bb763086aa9c9


---


# Azure RMS-Anforderungen: Lokale Server, die Azure RMS unterstützen

>*Gilt für: Azure Rights Management, Office 365*

Die folgenden lokalen Serverprodukte werden mit Azure RMS unterstützt, wenn Sie den Azure RMS-Verbindungsdienst verwenden, der als Kommunikationsschnittstelle (Relay) zwischen den lokalen Servern und Azure RMS fungiert. Zusätzlich erfordert diese Konfiguration, dass Sie die Verzeichnissynchronisierung zwischen Ihren Active Directory-Gesamtstrukturen und Azure Active Directory konfigurieren.

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
    > Da Dateiserver, auf denen Windows Server 2008 R2 ausgeführt wird, nicht über eine integrierte Taskaktion zum Anwenden des RMS-Schutzes verfügen, können Sie den RMS-Connector für dieses Szenario verwenden. Sie können jedoch die Dateiklassifizierungsinfrastruktur und Azure RMS auf diesen Betriebssystemen verwenden, wenn Sie einen benutzerdefinierten Dateiverwaltungstask konfigurieren, über den eine Datei oder ein Skript ausgeführt wird, um die Dateien mithilfe von Azure RMS zu schützen. Beispielsweise ein Windows PowerShell-Skript, in dem die [RMS-Schutz-Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx) verwendet werden.
    > 
    > Sie können diese Cmdlets auch mit Servern mit höheren Versionen von Windows Server verwenden. Dies hat den Vorteil, dass diese Cmdlets alle Dateitypen schützen können. Der RMS-Connector schützt nur Office-Dateien. Anweisungen zur Vorgehensweise finden Sie unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](../rms-client/configure-fci.md).

Der RMS-Verbindungsdienst wird unter Windows Server 2012 R2, Windows Server 2012 und Windows Server 2008 R2 unterstützt.

Weitere Informationen dazu, wie Sie den RMS-Connector für diese lokalen Server konfigurieren, finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

## Nächste Schritte
Weitere Anforderungen finden Sie unter [Voraussetzungen für Azure Rights Management](requirements-azure-rms.md).



<!--HONumber=Aug16_HO4-->


