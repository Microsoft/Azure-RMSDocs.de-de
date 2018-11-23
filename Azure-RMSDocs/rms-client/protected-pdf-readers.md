---
title: Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection
description: ''
keywords: ''
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/13/2018
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.openlocfilehash: ab3d141394a9a042a8a3e15e35d1daffab20ad98
ms.sourcegitcommit: 1e6394044d646278ae582c7713cac8ffb9bf4c1e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49170251"
---
# <a name="supported-pdf-readers-for-microsoft-information-protection"></a>Unterstützte Reader für PDF-Dokumente für Microsoft Azure Information Protection

Mithilfe der folgenden Informationen erfahren Sie mehr zu PDF-Dokumenten, die für die Klassifizierung und den Schutz gekennzeichnet sind, und wie diese Dokumente angezeigt werden.

Durch die Kollaboration zwischen Microsoft und Adobe profitieren Sie von einer einfacheren und konsistenteren Handhabung von PDF-Dokumenten, die klassifiziert und optional geschützt wurden. Diese Kollaboration stellt die Unterstützung für die native Adobe Acrobat-Integration in Microsoft Azure Information Protection-Lösungen bereit, wie z.B. [Azure Information Protection](../what-is-information-protection.md). 

Diese native Integration bringt folgende Vorteile mit sich:

- Sie können PDF-Dokumente anzeigen, die geschützt wurden, da sie vertrauliche Informationen enthalten.

- Sie können den Klassifizierungswert für die Bezeichnung Ihrer Organisation sehen, der auf das Dokument angewendet wurde.

- Die Unterstützung für den ISO-Standard für die PDF-Verschlüsselung.
    
    Dieses geschützte PDF-Dateiformat muss [vom Administrator aktiviert werden](client-admin-guide-customizations.md#protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption). Wenn dieses Konfiguration durchgeführt wird, bleibt die Dateinamenerweiterung „.pdf“ und ändert sich nicht in „.ppdf“.

Weitere Informationen finden Sie im folgenden Blogbeitrag [Starting Today! Use Adobe Acrobat Reader for PDFs protected by Microsoft Information Protection (Ab heute: Verfügbarkeit von Adobe Acrobat Reader für mit Microsoft Information Protection geschützte PDFs)](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/Starting-October-use-Adobe-Acrobat-Reader-for-PDFs-protected-by/ba-p/262738).

## <a name="supported-pdf-readers"></a>Unterstützte PDF-Reader

Die folgenden PDF-Reader können geschützte PDF-Dateien öffnen, die dem ISO-Standard für die PDF-Verschlüsselung unterstehen:

|Betriebssystem|Unterstützte Reader und Link zum Herunterladen|
|----------------|-----------------------------------|
|Windows 10 und frühere Versionen<br />über Windows 7 Service Pack 1|Adobe Acrobat-Reader (bevorzugt):<br />-  [Lesen Sie die allgemeinen Nutzungsbedingungen von Adobe](https://www.adobe.com/legal/terms.html) <br />- [Laden Sie die Vorschauversion herunter](https://ardownload2.adobe.com/pub/adobe/reader/win/AcrobatDC/misc/MIP_Preview/1900820120/Adobe_MIP_Preview_1900820120.zip) <br /><br /> Azure Information Protection-Viewer: [Herunterladen](https://go.microsoft.com/fwlink/?linkid=838993)<br /><br />Foxit Reader [Herunterladen](https://www.foxitsoftware.com/pdf-reader/)|
|Android|Azure Information Protection-App: [Herunterladen](https://go.microsoft.com/fwlink/?LinkId=325340)|
|iOS|Azure Information Protection-App: [Herunterladen](https://go.microsoft.com/fwlink/?LinkId=325338)|

### <a name="support-for-previous-formats"></a>Unterstützung für vorherige Formate

Die PDF-Reader in der nächsten Tabelle unterstützen geschützte PDF-Dokumente, die über die Dateinamenerweiterung .ppdf verfügen sowie ältere Formate, die eine .pdf-Dateinamenerweiterung besitzen.

Derzeit verwenden SharePoint Online und SharePoint (lokal) ein älteres Ordnerformat für PDF-Dokumente in IRM-geschützten Bibliotheken.


|Betriebssystem|Unterstützte Reader|
|----------------|-----------------------------------|
|Windows 10 und frühere Versionen<br />über Windows 7 Service Pack 1|Azure Information Protection-Viewer<br /><br />Gaaiho Doc<br /><br />GigaTrust Desktop PDF Client for Adobe<br /><br />Foxit Reader<br /><br />Nitro PDF Reader<br /><br />RMS-Freigabeanwendung|
|Android|Azure Information Protection-App<br /><br />Foxit MobilePDF mit RMS<br /><br />GigaTrust App für Android|
|iOS|Azure Information Protection-App<br /><br />Foxit MobilePDF mit RMS<br /><br />TITUS-Dokumentation|