---
title: Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection
description: Installieren eines Readers für PDF-Dokumente, die für Klassifizierung und Schutz bezeichnet werden
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 08/22/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.custom: user
search.appverid:
- MET150
ms.openlocfilehash: 390eb0bd48b4b9ca6f36957a2ac63ed6903a83fc
ms.sourcegitcommit: 84190253d8682032912b36e291f17105d7f9d7f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2019
ms.locfileid: "69974784"
---
# <a name="pdf-readers-that-support-microsoft-information-protection"></a>PDF-Leser, die Microsoft Information Protection unterstützen

Wenn Sie ein PDF-Dokument öffnen müssen, das von Microsoft Information Protection geschützt ist, verwenden Sie die folgenden Links und Informationen.

## <a name="install-pdf-readers-for-your-device"></a>Installieren von PDF-Lesern für Ihr Gerät

Wählen Sie das Gerät aus, das Sie zum Installieren eines PDF-Readers verwenden, der geschützte PDF-Dokumente öffnen kann. Alle diese Leser können geschützte Dokumente öffnen, die dem ISO-Standard für die PDF-Verschlüsselung entsprechen:

- **Computer**: [Windows](protected-pdf-readers-windows.md) | [MacOS](protected-pdf-readers-mac.md)

- **Mobile Geräte**: [Android](protected-pdf-readers-android.md) | [iOS](protected-pdf-readers-ios.md)

### <a name="support-for-previous-formats"></a>Unterstützung für vorherige Formate

Die PDF-Reader in der folgenden Tabelle unterstützen geschützte PDF-Dokumente, die eine ppdf-Dateinamenerweiterung und ältere Formate mit der Dateinamenerweiterung ". pdf" aufweisen. 

Derzeit verwenden SharePoint Online und SharePoint (lokal) ein älteres Ordnerformat für PDF-Dokumente in IRM-geschützten Bibliotheken.


|Betriebssystem|Unterstützte Reader|
|----------------|-----------------------------------|
|Windows 10 und frühere Versionen<br />über Windows 7 Service Pack 1|Azure Information Protection-Viewer<br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br /> Nuance Power-PDF<br /><br />RMS-Freigabe-App|
|Android|Azure Information Protection-App<br /><br />Foxit MobilePDF mit RMS<br /><br />GigaTrust App für Android|
|iOS|Azure Information Protection-App<br /><br />Foxit MobilePDF mit RMS<br /><br />TITUS-Dokumentation|

## <a name="using-adobe-acrobat-reader-with-the-adobe-plug-in"></a>Verwenden von Adobe Acrobat Reader mit dem Adobe-Plug-in

Eine Zusammenarbeit zwischen Microsoft und Adobe bietet eine vereinfachte und konsistente Darstellung von PDF-Dokumenten, die klassifiziert und optional geschützt wurden. Diese Kollaboration stellt die Unterstützung für die native Adobe Acrobat-Integration in Microsoft Azure Information Protection-Lösungen bereit, wie z.B. [Azure Information Protection](../what-is-information-protection.md). 

Diese native Integration bringt folgende Vorteile mit sich:

- Sie können PDF-Dokumente anzeigen, die geschützt wurden, da sie vertrauliche Informationen enthalten.

- Sie können den Klassifizierungswert für die Bezeichnung Ihrer Organisation sehen, der auf das Dokument angewendet wurde.

- Die Unterstützung für den ISO-Standard für die PDF-Verschlüsselung.
    
    Wenn diese Funktion nicht [von einem Administrator deaktiviert](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption)wurde, ist dieses geschützte PDF-Dateiformat standardmäßig für den Azure Information Protection Client (klassisch) aktiviert und wird immer vom Azure Information Protection Unified-Bezeichnungs Client verwendet.

Sie können das Adobe-Plug-in mit [Windows](protected-pdf-readers-windows.md) und [MacOS](protected-pdf-readers-mac.md)verwenden.

Weitere Informationen finden Sie in den folgenden Blogbeiträgen: 

- [Allgemeine Verfügbarkeit der Integration von Adobe Acrobat Reader in Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-Integration-with/ba-p/298396)

- [FAQs zu Adobe Reader und Microsoft Information Protection-Integration](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Adobe-reader-and-Microsoft-Information-Protection-integration/ba-p/482219)
