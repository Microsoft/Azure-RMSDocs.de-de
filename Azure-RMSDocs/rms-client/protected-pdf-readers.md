---
title: Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection
description: Informationen Sie zu den PDF-Dokumente mit der Bezeichnung für Klassifizierung und Schutz und wie diese angezeigt werden.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/23/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
search.appverid:
- MET150
ms.openlocfilehash: 9a1deef0cc63861560e528aa06cd44857ab86515
ms.sourcegitcommit: 47182b6a65bfae3561cb34be3d6a6852a1edccb9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/24/2019
ms.locfileid: "68446859"
---
# <a name="supported-pdf-readers-for-microsoft-information-protection"></a>Unterstützte Reader für PDF-Dokumente für Microsoft Azure Information Protection

Mithilfe der folgenden Informationen erfahren Sie mehr zu PDF-Dokumenten, die für die Klassifizierung und den Schutz gekennzeichnet sind, und wie diese Dokumente angezeigt werden.

Durch die Kollaboration zwischen Microsoft und Adobe profitieren Sie von einer einfacheren und konsistenteren Handhabung von PDF-Dokumenten, die klassifiziert und optional geschützt wurden. Diese Kollaboration stellt die Unterstützung für die native Adobe Acrobat-Integration in Microsoft Azure Information Protection-Lösungen bereit, wie z.B. [Azure Information Protection](../what-is-information-protection.md). 

Diese native Integration bringt folgende Vorteile mit sich:

- Sie können PDF-Dokumente anzeigen, die geschützt wurden, da sie vertrauliche Informationen enthalten.

- Sie können den Klassifizierungswert für die Bezeichnung Ihrer Organisation sehen, der auf das Dokument angewendet wurde.

- Die Unterstützung für den ISO-Standard für die PDF-Verschlüsselung.
    
    Sofern diese Funktion nicht von einem [Administrator deaktiviert wurde](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption), ist dieses geschützte PDF-Dateiformat nun standardmäßig in der neuesten Version des Azure Information Protection-Clients aktiviert.

Weitere Informationen finden Sie im folgenden Blogbeitrag: [Starting Today! Use Adobe Acrobat Reader for PDFs protected by Microsoft Information Protection (Ab heute: Verfügbarkeit von Adobe Acrobat Reader für mit Microsoft Information Protection geschützte PDFs)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Starting-October-use-Adobe-Acrobat-Reader-for-PDFs-protected-by/ba-p/262738).

## <a name="supported-pdf-readers"></a>Unterstützte PDF-Reader

Die folgenden PDF-Reader können geschützte PDF-Dateien öffnen, die dem ISO-Standard für die PDF-Verschlüsselung unterstehen:

|Betriebssystem|Unterstützte Reader und Link zum Herunterladen|
|----------------|-----------------------------------|
|Windows 10 und frühere Versionen<br />über Windows 7 Service Pack 1|Adobe Acrobat-Reader (bevorzugt):<br />-  1. Lesen Sie die [Allgemeinen Nutzungsbedingungen von Adobe](https://www.adobe.com/legal/terms.html) <br />- 2. Installieren von Adobe Reader für Windows von der [Adobe-Website](https://www.adobe.com/)<br />- 3. Installieren des [Adobe-Plug-ins](https://go.microsoft.com/fwlink/?linkid=2050049) für Windows <br />- 4. Wenn Sie dazu aufgefordert werden, fordern Sie Ihren Administrator auf, das [Plug-In zu autorisieren](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-integration-with/ba-p/298396) <br /><br /> Azure Information Protection-Viewer: [Herunterladen](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Foxit Reader: [Download](https://www.foxitsoftware.com/pdf-reader/)|
|macOS-Versionen 10,12-10,14 |Adobe Acrobat Reader:<br />-  1. Lesen Sie die [Allgemeinen Nutzungsbedingungen von Adobe](https://www.adobe.com/legal/terms.html) <br />- 2. Installieren von Adobe Reader für Mac von der [Adobe-Website](https://www.adobe.com/)<br />- 3. Installieren des [Adobe-Plug-ins](https://go.microsoft.com/fwlink/?linkid=2050049) für Mac <br />- 4. Wenn Sie dazu aufgefordert werden, fordern Sie Ihren Administrator auf, das [Plug-In zu autorisieren](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-integration-with/ba-p/298396)|
|Android|Azure Information Protection-App: [Herunterladen](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Azure Information Protection-App: [Herunterladen](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>Unterstützung für vorherige Formate

Die PDF-Reader in der nächsten Tabelle unterstützen geschützte PDF-Dokumente, die über die Dateinamenerweiterung .ppdf verfügen sowie ältere Formate, die eine .pdf-Dateinamenerweiterung besitzen.

Derzeit verwenden SharePoint Online und SharePoint (lokal) ein älteres Ordnerformat für PDF-Dokumente in IRM-geschützten Bibliotheken.


|Betriebssystem|Unterstützte Reader|
|----------------|-----------------------------------|
|Windows 10 und frühere Versionen<br />über Windows 7 Service Pack 1|Azure Information Protection-Viewer<br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br /> Nuance Power-PDF<br /><br />RMS-Freigabe-App|
|Android|Azure Information Protection-App<br /><br />Foxit MobilePDF mit RMS<br /><br />GigaTrust App für Android|
|iOS|Azure Information Protection-App<br /><br />Foxit MobilePDF mit RMS<br /><br />TITUS-Dokumentation|
