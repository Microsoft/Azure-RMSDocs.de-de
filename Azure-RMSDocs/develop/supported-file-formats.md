---
# required metadata

title: Unterstützte Dateiformate | Azure RMS
description: Die aktuelle Version der Datei-API unterstützt den nativen Schutz für MS Office-Dateien und PDFs und den PFile-Schutz für alle anderen Dateiformate.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: deb9a110-c098-4834-8319-05d5a28a0ccd

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
# Unterstützte Dateiformate

Die Datei-API unterstützt native Formate und das PFile-Format.

## Unterstützte Dateiformate

Die aktuelle Version der Datei-API unterstützt den nativen Schutz für MS Office-Dateien und PDF-Dateien und den PFile-Schutz für alle anderen Dateiformate. Auf PDF-Dateien kann optional der PFile-Schutz angewendet werden.

-   **Nativer Schutz**: Beim nativen Schutz wird die Datei in einem AD RMS-Dateiformat verschlüsselt, das auf ihrem MIME-Typ (Dateinamenerweiterung) basiert. Dateien, die dem nativen Schutz durch die Datei-API unterliegen, sind konsistent mit dem Format, das von AD RMS-fähigen Anwendungen mit nativem Schutz erwartet wird. Beispiele hierfür sind Office 2013, Office 2010 und der FoxIt PDF Reader. Der native Schutz wird nur für Office-Dateien, PDF-Dateien und einige andere Dateitypen unterstützt. Weitere Informationen zu den Dateitypen, für die der native Schutz unterstützt wird, finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).
-   **PFile-Schutz**: Beim PFile-Schutz werden Dateien mit dem Format „Protected File“ (PFile) von AD RMS verschlüsselt. Die Datei wird in einer Datei mit der Erweiterung „.pfile“ verschlüsselt. Der PFile-Schutz wird für alle Dateiformate mit Ausnahme von Office-Dateien unterstützt.

Administratoren können Registrierungsschlüssel festlegen, um zu konfigurieren, ob und wie Dateien basierend auf ihrer Dateinamenerweiterung geschützt werden sollten. Weitere Informationen zur Konfiguration des Dateischutzes beim Verwenden der Datei-API finden Sie unter [Datei-API-Konfiguration](file-api-configuration.md).

### Verwandte Themen

* [Hinweise für Entwickler](developer-notes.md)
* [Datei-API-Konfiguration](file-api-configuration.md)
 

 





<!--HONumber=Apr16_HO3-->


