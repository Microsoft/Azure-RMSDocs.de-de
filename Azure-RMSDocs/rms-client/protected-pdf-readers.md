---
title: Reader für geschützte PDF-Dokumente für Microsoft Azure Information Protection
description: Installieren eines Readers für PDF-Dokumente, die für Klassifizierung und Schutz bezeichnet werden
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/29/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: aab59e02-930b-4a17-8442-2d5d081fe1a6
ms.reviewer: kartikka
ms.suite: ems
ms.custom: user
search.appverid:
- MET150
ms.openlocfilehash: 16623f1182b248647ef0018ec6b4b21a2cf6f329
ms.sourcegitcommit: f6d536b6a3b5e14e24f0b9e58d17a3136810213b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/26/2021
ms.locfileid: "98809861"
---
# <a name="which-pdf-readers-are-supported-for-protected-pdfs"></a>Welche PDF-Reader werden für geschützte PDF-Funktionen unterstützt?

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Mit PDF-Lesern für klassifizierte und/oder geschützte PDF-Datei können Sie verschlüsselte PDF-Datei öffnen, die vertrauliche Informationen enthalten.

Durch das Verschlüsseln von PDF-Dateien mit [Azure Information Protection (AIP)](../what-is-information-protection.md) wird sichergestellt, dass nicht autorisierte Personen den Inhalt der Datei nicht lesen können.

Geschützte PDF-Leser, die Azure Information Protection unterstützen, stellen sicher, dass Ihnen Berechtigungen zum Öffnen des Dokuments erteilt wurden, und entschlüsseln auch den Inhalt.

Die folgende Abbildung zeigt z. b. ein verschlüsseltes Dokument, das in Adobe Acrobat Reader geöffnet ist. Der Balken oben gibt an, dass das Dokument durch eine Microsoft Information Protection-Lösung geschützt wird.

:::image type="content" source="../media/protected-pdf-in-adobe-reader.png" alt-text="Geschützte PDF-Datei in Adobe Acrobat Reader öffnen":::

Anweisungen finden Sie in den folgenden Abschnitten:

- [Anzeigen geschützter PDF-Geräte in Microsoft Edge unter Windows oder Mac](#viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac)

- [Installieren eines geschützten PDF-Readers für Windows oder Mac](#installing-a-protected-pdf-reader-for-windows-or-mac)

- [Installieren eines geschützten PDF-Readers für mobile Geräte (IOS/Android)](#installing-a-protected-pdf-reader-for-mobile-iosandroid)

> [!TIP]
> Wenn das Dokument nach der Installation eines empfohlenen Readers nicht geöffnet wird, kann das Dokument in einem älteren Format geschützt werden. 
>
> Probieren Sie in diesem Fall einen der als unterstützt für vorherige Formate aufgeführten Leser aus. Weitere Informationen finden Sie [unter Unterstützung für vorherige Formate](#support-for-previous-formats).
> 
### <a name="iso-standards-for-pdf-encryption"></a>ISO-Standards für die PDF-Verschlüsselung

Mit den auf dieser Seite referenzierten PDF-Lesern können alle geschützten Dokumente geöffnet werden, die dem ISO-Standard für die PDF-Verschlüsselung entsprechen. 

Dieser Standard wird standardmäßig vom AIP-Client verwendet.

> [!NOTE]
> **Nur klassischer Client**: Wenn Sie über den klassischen AIP-Client verfügen, wurde dieser möglicherweise [von einem Administrator deaktiviert](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption).
> 

### <a name="viewing-protected-pdfs-in-adobe-acrobat-reader"></a>Anzeigen geschützter PDF-Funktionen in Adobe Acrobat Reader

Adobe Acrobat Reader lässt sich in Microsoft Information Protection-Lösungen integrieren, wie z. b. [Azure Information Protection](../what-is-information-protection.md) , um Benutzern eine vereinfachte und konsistente Darstellung für klassifizierte und/oder geschützte PDF-Informationen bereitzustellen.

Der Adobe Acrobat Reader mit der Microsoft Information Protection-Integration wird für [Windows](#installing-a-protected-pdf-reader-for-windows-or-mac) und [macOS](#installing-a-protected-pdf-reader-for-windows-or-mac)unterstützt.

Weitere Informationen finden Sie in den folgenden Blogbeiträgen: 

- [Allgemeine Verfügbarkeit der Integration von Adobe Acrobat Reader in Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-Integration-with/ba-p/298396)

- [FAQs zu Adobe Reader und Microsoft Information Protection-Integration](https://techcommunity.microsoft.com/t5/Microsoft-Information-Protection/Adobe-reader-and-Microsoft-Information-Protection-integration/ba-p/482219)

## <a name="viewing-protected-pdfs-in-microsoft-edge-on-windows-or-mac"></a>Anzeigen geschützter PDF-Geräte in Microsoft Edge unter Windows oder Mac

Microsoft Edge bietet integrierte Unterstützung für die Anzeige von PDF-Dateien, die klassifiziert und geschützt sind. Durch die Verwendung von Microsoft Edge wird sichergestellt, dass Benutzer geschützte PDF-Dateien nahtlos öffnen können, ohne zusätzliche Einstellungen oder Software installieren oder konfigurieren zu müssen.

Folgende Versionen werden unterstützt:

- **Windows**: Windows 10 und frühere Versionen über Windows 8. 
    
    Weitere Informationen zu früheren Versionen finden Sie [unter Unterstützung für vorherige Formate](#support-for-previous-formats).

- **Mac**: macOS-Versionen 10,12 und höher 


**Anweisungen**: 

1. Überprüfen Sie, welche [Microsoft Edge-Version](https://support.microsoft.com/help/4027011/microsoft-edge-find-out-which-version-you-have) auf Ihrem System installiert ist. 
1. Wenn die Microsoft Edge-Version 83.0.478.37 oder höher ist, können Sie geschützte Dateien direkt im Edge-Browser öffnen. 

1. Um PDF-Dateien in SharePoint zu öffnen , klicken Sie auf Öffnen  >  **in Browser** öffnen. 

    :::image type="content" source="../media/edge_open_browser.png" alt-text="Öffnen einer geschützten PDF-Datei mithilfe von Microsoft Edge über den Browser mithilfe der Option in Browser öffnen":::
 
## <a name="installing-a-protected-pdf-reader-for-windows-or-mac"></a>Installieren eines geschützten PDF-Readers für Windows oder Mac

Zum Öffnen eines geschützten PDF-Dokuments auf dem Desktop Computer wird empfohlen, das relevante [Microsoft Information Protection (MIP)-Plug-in für Acrobat und Acrobat Reader](https://go.microsoft.com/fwlink/?linkid=2050049) für Ihr Betriebssystem zu installieren.

**Anweisungen**:

1. Wenn Sie dies noch nicht getan haben, installieren Sie den Adobe Reader von der [Adobe-Website](https://www.adobe.com/).

    Stellen Sie sicher, dass Sie die [allgemeinen Nutzungsbedingungen für Adobe](https://www.adobe.com/legal/terms.html)lesen und akzeptieren.

1. Installieren Sie das [MIP-Plug-in für Acrobat und Acrobat Reader](https://go.microsoft.com/fwlink/?linkid=2050049) für Ihr Betriebssystem.  

    Download: [ ![MIP-Plug-in für Acrobat-und Acrobat Reader herunterladen](../media/download.png "Herunterladen des MIP-Plug-Ins für Acrobat-und Acrobat Reader")](https://go.microsoft.com/fwlink/?linkid=2050049)

    Folgende Versionen werden unterstützt:

    - **Windows**: Windows 10 und frühere Versionen über Windows 8. 
    
        Weitere Informationen zu früheren Versionen finden Sie [unter Unterstützung für vorherige Formate](#support-for-previous-formats).

    - **Mac**: macOS-Versionen 10,12-10,14 

1. Wenn Sie zur Administrator Genehmigung aufgefordert werden, bitten Sie den Administrator, das Plug-in zu autorisieren.

    Beispiel:
    
    :::image type="content" source="../media/admin-approval-for-mip-in-adobe-reader.png" alt-text="Erforderliche Administrator Genehmigung zum Installieren des MIP-Plug-Ins für Acrobat-und Acrobat Reader":::
    
> [!NOTE]
> Weitere Informationen finden Sie in der [Microsoft Information Protection-und Adobe Release-Ankündigung](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/General-Availability-of-Adobe-Acrobat-Reader-integration-with/ba-p/298396).
> 

### <a name="alternative-protected-pdf-readers-for-windows"></a>Alternative geschützte PDF-Reader für Windows

Alternativ dazu können Sie einen der folgenden PDF-Reader für Windows verwenden, die dem ISO-Standard für die PDF-Verschlüsselung entsprechen:

- Azure Information Protection Viewer [ ![den AIP-Viewer herunterladen](../media/download.png "AIP-Viewer herunterladen")](https://go.microsoft.com/fwlink/?linkid=838993) 

- Foxit Reader [ ![herunterladen des Foxit Reader Viewer](../media/download.png "Herunterladen von Foxit Reader Viewer")](https://www.foxitsoftware.com/pdf-reader/)

## <a name="installing-a-protected-pdf-reader-for-mobile-iosandroid"></a>Installieren eines geschützten PDF-Readers für mobile Geräte (IOS/Android)

Zum Öffnen einer geschützten PDF-Datei auf Ihrem IOS-oder Android-Gerät müssen Sie die APP für Ihr Betriebssystem herunterladen und installieren:

- Azure Information Protection-App für IOS [ ![herunterladen der Azure Information Protection-App für IOS](../media/download.png "Azure Information Protection-App für IOS")  ](https://go.microsoft.com/fwlink/?LinkId=325338)

- Azure Information Protection App für Android [ ![herunterladen der Azure Information Protection-App für Android](../media/download.png "Azure Information Protection-App für Android")](https://go.microsoft.com/fwlink/?LinkId=325340)

Weitere Informationen finden Sie unter [Was ist die Azure Information Protection-App für IOS oder Android?](mobile-app-faq.md).

## <a name="support-for-previous-formats"></a>Unterstützung für vorherige Formate

Die folgenden PDF-Reader unterstützen sowohl geschützte PDF-Dateien mit der Erweiterung **ppdf** als auch ältere Formate mit der Erweiterung **. PDF** .

Wenn Sie die geschützte PDF-Datei nicht mithilfe des empfohlenen Readers öffnen können, wird das Dokument möglicherweise in einem früheren Format geschützt. Beispielsweise verwendet Microsoft SharePoint derzeit ein älteres Format für PDF-Dokumente in durch unm geschützten Bibliotheken.

- **Windows 10/frühere Versionen über Windows 7 Service Pack 1**

    - [Azure Information Protection Viewer](https://go.microsoft.com/fwlink/?linkid=838993)
    - Gaaiho Doc
    - GigaTrust Desktop PDF Client for Adobe
    - Foxit Reader
    - Nitro PDF Reader
    - Nuance Power-PDF
    - Edge-Chrom

- **Android**:

    - [Azure Information Protection-App](mobile-app-faq.md)
    - Foxit MobilePDF mit RMS
    - GigaTrust App für Android

- **IOS**:

    - [Azure Information Protection-App](mobile-app-faq.md)
    - Foxit MobilePDF mit RMS
    - TITUS-Dokumentation

- **MacOS Catalina**: Edge-Chrom

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie nach der Installation weitere Hilfe benötigen, befolgen Sie die Anweisungen und die Dokumentation für die einzelnen Leser. Informationen hierzu finden Sie beispielsweise in den folgenden Artikeln:

- [Benutzerhandbuch: Anzeigen geschützter Dateien mit dem Azure Information Protection Unified Bezeichnung-Client](clientv2-view-use-files.md)
- [Was ist die Azure Information Protection-App für IOS oder Android?](mobile-app-faq.md)