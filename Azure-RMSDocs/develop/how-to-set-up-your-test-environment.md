---
# required metadata

title: Einrichten der Testumgebung | Azure RMS
description: Ihre rechtlich geschützte Anwendung kann mit anderen Serveroptionen getestet werden.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4d32682c-754d-4e30-977d-95b08e0662cc

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

﻿
# Einrichten der Testumgebung

Ihre rechtlich geschützte Anwendung kann mit anderen Serveroptionen getestet werden.

**Wichtig**  Eine bewährte Methode besteht darin, die Rights Management Services SDK 2.1-Anwendung zuerst mit der AD RMS-Präproduktionsumgebung auf einem AD RMS-Server zu testen. Soll Ihr Kunde dann die Möglichkeit erhalten, Ihre Anwendung mit dem Azure RMS-Dienst zu verwenden, testen Sie in dieser Umgebung. Weitere Informationen finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

 

### Voraussetzungen

-   [Installieren des SDKs](create-your-first-rights-aware-application.md)

Anweisungen

### Schritt 1: Einrichten der Testumgebung

Um die rechtlich geschützte Anwendung zu testen, führen Sie sie auf einem RMS-Server aus, die für die Präproduktion konfiguriert ist. Ein RMS-Server für die Präproduktion verwendet zum Verschlüsseln und Entschlüsseln von Dateien die Hierarchie Präproduktion/ISV-Zertifikat.

Weitere Informationen zur AD RMS-Zertifikathierarchie finden Sie unter [Grundlegendes zu Zertifikatketten](understanding-certificate-chains.md).

Es gibt zwei Optionen zum Testen der Anwendung auf einem RMS-Server:

-   Sie können die Anwendung in der AD RMS ISV-Umgebung für einen Computer ausführen. Wenn Sie Windows Server 2012, Windows Server 2008 R2 oder Windows Server 2008 ausführen und Hyper-V installiert haben, können Sie die AD RMS ISV-Umgebung für einen Computer bereitstellen. Richten Sie zu diesem Zweck mit der VHD-Datei für AD RMS für einen Computer einen virtuellen Computer ein. Die AD RMS ISV-Umgebung für einen Computer bietet einen für die Präproduktion konfigurierten RMS-Server sowie den installierten Active Directory Rights Management Services Client 2.1. Registrierungseinstellungen für den RMS-Server und den Client sind bereits konfiguriert. Um die Anwendung zu testen, führen Sie sie auf dem virtuellen Computer aus, auf dem die Umgebung für einen Computer bereitgestellt wird.
-   **Sie können die Anwendung auf einem für die Präproduktion konfigurierten RMS-Server ausführen, der in Ihrem Netzwerk bereitgestellt wurde**. In diesem Fall müssen Sie auch den AD RMS-Client 2.1 auf dem Computer installieren und konfigurieren, auf dem die Anwendung ausgeführt wird. Informationen hierzu finden Sie unter [Konfigurieren des Clients](how-to-configure-the-ad-rms-client-2-0.md). Informationen dazu, wie Sie einen RMS-Server bereitstellen und für die Präproduktion konfigurieren, finden Sie unter [Installieren und Konfigurieren des Servers](how-to-install-and-configure-an-rms-server.md).

### Verwandte Themen

* [Vorgehensweise](how-to-use-msipc.md)
* [Downloadseite für Begleitmaterial zum AD RMS SDK-Webinar](https://connect.microsoft.com/site1170/Downloads/DownloadDetails.aspx?DownloadID=42440)
* [Konfigurieren des Clients](how-to-configure-the-ad-rms-client-2-0.md)
* [Installieren des SDKs](create-your-first-rights-aware-application.md)
* [Installieren und Konfigurieren des Servers](how-to-install-and-configure-an-rms-server.md)
* [Grundlegendes zu Zertifikatketten](understanding-certificate-chains.md)
 

 





<!--HONumber=Apr16_HO3-->


