---
title: Unterstützte Dateiformate | Azure RMS
description: Die aktuelle Version der Datei-API unterstützt den nativen Schutz für MS Office-Dateien und PDFs und den PFile-Schutz für alle anderen Dateiformate.
keywords: ''
author: bryanla
ms.author: bryanla
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: EC831494-7F2C-4C70-9063-B02CDDEA14EE
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: 6fa4571bd04211f3e09843ef89f142b4ebbe7af5
ms.sourcegitcommit: a78d4236cbeff743703c44b150e69c1625a2e9f4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/14/2019
ms.locfileid: "56255936"
---
# <a name="supported-file-formats"></a>Unterstützte Dateiformate

Die Datei-API unterstützt native Formate und das PFile-Format.

## <a name="supported-file-formats"></a>Unterstützte Dateiformate

Die aktuelle Version der Datei-API unterstützt den nativen Schutz für MS Office-Dateien und PDF-Dateien und den PFile-Schutz für alle anderen Dateiformate. Auf PDF-Dateien kann optional der PFile-Schutz angewendet werden.

-   **Nativer Schutz**: Beim nativen Schutz wird die Datei in einem AD RMS-Dateiformat verschlüsselt, das auf ihrem MIME-Typ (Dateinamenerweiterung) basiert. Dateien, die dem nativen Schutz durch die Datei-API unterliegen, sind konsistent mit dem Format, das von AD RMS-fähigen Anwendungen mit nativem Schutz erwartet wird. Beispiele hierfür sind Office 2013, Office 2010 und der FoxIt PDF Reader. Der native Schutz wird nur für Office-Dateien, PDF-Dateien und einige andere Dateitypen unterstützt. Weitere Informationen zu den Dateitypen, für die der native Schutz unterstützt wird, finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).
-   **PFile-Schutz**: Beim PFile-Schutz werden Dateien mit dem Format „Protected File“ (PFile) von AD RMS verschlüsselt. Die Datei wird in einer Datei mit der Erweiterung „.pfile“ verschlüsselt. Der PFile-Schutz wird für alle Dateiformate mit Ausnahme von Office-Dateien unterstützt.

Administratoren können Registrierungsschlüssel festlegen, um zu konfigurieren, ob und wie Dateien basierend auf ihrer Dateinamenerweiterung geschützt werden sollten. Weitere Informationen zur Konfiguration des Dateischutzes beim Verwenden der Datei-API finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

## <a name="related-topics"></a>Verwandte Themen

* [Hinweise für Entwickler](developer-notes.md)
* [Datei-API-Konfiguration](file-api-configuration.md)
 
