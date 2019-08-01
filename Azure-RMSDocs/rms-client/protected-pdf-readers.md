---
title: Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection
description: Installieren eines Readers für PDF-Dokumente, die für Klassifizierung und Schutz bezeichnet werden
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/31/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
search.appverid:
- MET150
ms.openlocfilehash: fae4a3f0e95e0ee3cf548c59aee55fc6e1a39831
ms.sourcegitcommit: 0ff7941832bd8476d53810d2c849c56efa0303fa
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/01/2019
ms.locfileid: "68701607"
---
# <a name="install-a-pdf-reader-that-supports-microsoft-information-protection"></a>Installieren Sie einen PDF-Reader, der Microsoft unterstützt Information Protection

Wenn Sie ein PDF-Dokument öffnen müssen, das von Microsoft Information Protection geschützt ist, verwenden Sie die folgenden Links und Informationen.

## <a name="choose-your-pdf-reader"></a>Auswählen des PDF-Readers

Die folgenden PDF-Reader können geschützte PDF-Dokumente öffnen, die dem ISO-Standard für die PDF-Verschlüsselung entsprechen:

|Betriebssystem|Unterstützte Reader und Link zum Herunterladen|
|----------------|-----------------------------------|
|Windows 10 und frühere Versionen<br />über Windows 7 Service Pack 1|Adobe Acrobat-Reader (bevorzugt):<br /> 1. Lesen Sie die [Allgemeinen Nutzungsbedingungen von Adobe](https://www.adobe.com/legal/terms.html) <br /> 2. Installieren von Adobe Reader für Windows von der [Adobe-Website](https://www.adobe.com/)<br /> 3. Installieren des [Adobe-Plug-ins](https://go.microsoft.com/fwlink/?linkid=2050049) für Windows <br /> 4. Wenn Sie dazu aufgefordert werden, fordern Sie Ihren Administrator auf, das [Plug-In zu autorisieren](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-integration-with/ba-p/298396) <br /><br /> Azure Information Protection-Viewer: [Herunterladen](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Foxit Reader: [Download](https://www.foxitsoftware.com/pdf-reader/)|
|MacOS-Versionen 10,12-10,14 |Adobe Acrobat Reader:<br /> 1. Lesen Sie die [Allgemeinen Nutzungsbedingungen von Adobe](https://www.adobe.com/legal/terms.html) <br /> 2. Installieren von Adobe Reader für Mac von der [Adobe-Website](https://www.adobe.com/)<br /> 3. Installieren des [Adobe-Plug-ins](https://go.microsoft.com/fwlink/?linkid=2050049) für Mac <br /> 4. Wenn Sie dazu aufgefordert werden, fordern Sie Ihren Administrator auf, das [Plug-In zu autorisieren](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-integration-with/ba-p/298396)|
|Android|Azure Information Protection-App: [Herunterladen](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Azure Information Protection-App: [Herunterladen](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>Unterstützung für vorherige Formate

Die PDF-Reader in der nächsten Tabelle unterstützen geschützte PDF-Dokumente, die eine ppdf-Dateinamenerweiterung und ältere Formate mit der Dateinamenerweiterung ". pdf" aufweisen.

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

Weitere Informationen finden Sie in den folgenden Blogbeiträgen: 

- [Allgemeine Verfügbarkeit der Integration von Adobe Acrobat Reader in Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-Integration-with/ba-p/298396)

- [FAQs zu Adobe Reader und Microsoft Information Protection-Integration](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Adobe-reader-and-Microsoft-Information-Protection-integration/ba-p/482219)
