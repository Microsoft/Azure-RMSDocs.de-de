---
# required metadata

title: Grundlegendes zu Zertifikatketten | Azure RMS
description: Eine rechtefähige Anwendung erfordert ein öffentliches Schlüsselpaar und eine Zertifikatkette, die wieder zurück zu einem Microsoft-Zertifikat an der Stammzertifizierungsstelle führt.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6AEA2162-82BF-4867-9285-111CD3FCD2F6
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---
** Dieser SDK-Inhalt ist nicht aktuell. Für kurze Zeit finden Sie die [aktuelle Version](https://msdn.microsoft.com/library/windows/desktop/hh535290(v=vs.85).aspx) der Dokumentation auf MSDN. **
# Grundlegendes zu Zertifikatketten

Das Entwickeln einer rechtefähigen Anwendung erfordert ein öffentliches Schlüsselpaar und eine Zertifikatkette, die wieder zu einem Microsoft-Zertifikat an der Stammzertifizierungsstelle führt.

## Zertifikattypen

Jede Lizenz und jedes Zertifikat, die bzw. das in einer RMS-Umgebung (Rights Management Services) verwendet wird, besteht aus einer Kette von Zertifikaten, die wieder zu einer Microsoft-Zertifizierungsstelle (CA) führt. Microsoft bietet zwei Ketten, in die eine Lizenz oder ein Zertifikat geschachtelt werden kann, eine Pre-Production-Zertifikatkette und eine Produktionskette. Sie sollten die Pre-Production-Hierarchie verwenden, wenn Sie eine Anwendung entwickeln, sodass Sie ohne Signieren eines *Produktionslizenzvertrags* für Microsoft arbeiten können. Beachten Sie, dass auch der RMS-Server für Pre-Production konfiguriert werden muss.

Sie müssen zu einer Produktionskette wechseln, bevor Sie die Anwendung veröffentlichen. Durch ein Pre-Production-Zertifikat geschützte Inhalte sind weniger sicher als bei einem Schutz durch ein Produktionszertifikat.

Die öffentlichen und privaten Schlüssel und das Pre-Production-Zertifikat sind im SDK in den folgenden Dateien im `%MsipcSDKDir%\Bin`-Ordner enthalten.

- **ISVTier5AppSigningPrivKey.dat** enthält den privaten Schlüssel zum Signieren eines Manifests für die Verwendung während der Anwendungsentwicklung.
- **ISVTier5AppSigningPubKey.dat** enthält den öffentlichen Schlüssel, der in der Pre-Production-Zertifikatshierarchie signiert ist.
- **ISVTier5AppSignSDK_Client.xml** enthält das Pre-Production-Zertifikat zum Generieren eines Manifests für die Verwendung während der Anwendungsentwicklung.

 

Sie verwenden das Zertifikat und den privaten Schlüssel, um ein Manifest zu erstellen und zu signieren, das die Dateien identifiziert, die in den Prozessbereich der Anwendung geladen werden können oder müssen und die nicht geladen werden müssen. Das Manifest wird dann von der Plattform geladen.

Wenn Sie die Anwendung freigeben möchten, unabhängig davon, ob Sie ein Pre-Production-Zertifikat während der Anwendungsentwicklung verwendet haben, müssen Sie ein neues Schlüsselpaar generieren, ein Produktionszertifikat von Microsoft abrufen und den neuen privaten Schlüssel und das Zertifikat verwenden, um ein Anwendungsmanifest zu erstellen und signieren.

Weitere Informationen zum Verwenden von Zertifikatketten und der Anwendungssignierung finden Sie unter [Wechseln zur Produktionsumgebung](switching-to-the-production-environment.md).

## Verwandte Themen

* [Entwicklerkonzepte](ad-rms-concepts-nav.md)
* [Wechseln zur Produktionsumgebung](switching-to-the-production-environment.md)
 

 


<!--HONumber=Jun16_HO1-->


