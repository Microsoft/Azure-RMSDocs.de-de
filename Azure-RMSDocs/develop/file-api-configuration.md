---
# required metadata

title: Datei-API-Konfiguration | Azure RMS
description: Das Datei-API-Verhalten kann durch Einstellungen in der Registrierung konfiguriert werden.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 00674664-22ed-44da-adb8-61f25c44aa6c

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
# Datei-API-Konfiguration


Das Datei-API-Verhalten kann durch Einstellungen in der Registrierung konfiguriert werden.

Die Datei-API bietet zwei Arten von Schutz – systemeigenen Schutz und PFile-Schutz.

-   **Systemeigener Schutz** – die Datei ist in einem AD RMS-Format geschützt, das auf dem MIME-Typ (Dateinamenerweiterung) basiert.
-   **PFile-Schutz** – die Datei ist im AD RMS-PFile-Format (Protected File) geschützt.

Weitere Informationen zu unterstützten Dateiformaten finden Sie unter **Datei-API-Unterstützungsdetails** in diesem Thema.

## Schlüssel/Schlüsselwerttypen und -beschreibungen

Die folgenden Abschnitte beschreiben die Schlüssel und Schlüsselwerte, die die Verschlüsselung steuern.


### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection

*Typ*: Key

*Beschreibung*: Enthält die allgemeine Konfiguration für die Datei-API.

### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;

*Typ: Key

*Beschreibung: Gibt Konfigurationsinformationen für eine bestimmte Dateierweiterung an, z. B. TXT, JPG usw.

- Das Platzhalterzeichen „*“ ist zulässig. Eine Einstellung für eine bestimmte Erweiterung hat jedoch Vorrang vor der Platzhaltereinstellung. Das Platzhalterzeichen wirkt sich nicht auf Einstellungen für Microsoft Office-Dateien aus. Diese müssen explizit nach Dateityp deaktiviert werden.
- Verwenden Sie „.“, um Dateien ohne Erweiterung anzugeben.
- Geben Sie das „.“-Zeichen nicht beim Angeben des Schlüssels für eine bestimmte Dateierweiterung an. Verwenden Sie beispielsweise `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\TXT`, um Einstellungen für TXT-Dateien anzugeben. (Verwenden Sie nicht `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\.TXT`).

Legen Sie den Wert *Encryption* im Schlüssel zum Angeben des Schutzverhaltens fest. Wenn der Wert *Encryption* nicht festgelegt ist, wird das Standardverhalten für den Dateityp verwendet.


### HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\&lt;EXT&gt;\Encryption*

*Typ: REG_SZ*

*Beschreibung: Enthält einen von drei Werten:

- *Off*: Verschlüsselung ist deaktiviert.

> [AZURE.NOTE] Diese Einstellung hat keinen Einfluss auf die Entschlüsselung. Jede verschlüsselte Datei, die mit Pfile- oder systemeigenen Schutz verschlüsselt ist, kann entschlüsselt werden, sofern der Benutzer über die Berechtigung EXTRACT verfügt.

- *Native*: Systemeigene Verschlüsselung wird verwendet. Für Office-Dateien hat die verschlüsselte Datei die gleiche Erweiterung wie die ursprüngliche Datei. Beispielsweise wird eine Datei mit der Dateierweiterung DOCX-Datei in eine Datei mit der Erweiterung DOCX verschlüsselt. Für andere Dateien, auf die der systemeigene Schutz angewendet werden kann, wird die Datei in eine Datei mit der Erweiterung im Format p**zzz** verschlüsselt, wobei **zzz** die ursprüngliche Dateierweiterung ist. Eine TXT-Datei wird z. B. in eine Datei mit der Erweiterung PTXT verschlüsselt. Unten finden Sie eine Liste der Dateierweiterungen, auf die der systemeigenene Schutz angewendet werden kann.

- *Pfile*: PFile-Verschlüsselung wird verwendet. Der verschlüsselten Datei wird „.pfile“ an die ursprüngliche Erweiterung angefügt. Zum Beispiel hat eine TXT-Datei nach der Verschlüsselung die Erweiterung „.txt.pfile“.


> [AZURE.NOTE] Diese Einstellung hat keinen Einfluss auf Office-Dateiformate. Wenn der `HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\FileProtection\DOCX\Encryption`-Wert z. B. auf „Pfile“ festgelegt wird, werden DOCX-Dateien weiterhin mit dem systemeigenen Schutz verschlüsselt, und die verschlüsselte Datei hat weiterhin die Dateierweiterung DOCX.

Das Festlegen eines anderen Werts oder keines Werts führt zum Standardverhalten.

## Standardverhalten für unterschiedliche Dateiformate**

-   **Office-Dateien** – systemeigene Verschlüsselung wird aktiviert.
-   **TXT-, XML-, JPEG-, PDF-, PNG-, TIFF-, BMP-, GIF-, GIFF-, JPE., JFIF-, JIF-Dateien** – systemeigene Verschlüsselung wird aktiviert (XXX wird zu PXXX).
-   **Alle anderen Dateien** – Verschlüsselung ist pfile-fähig (XXX wird zu XXX.PFILE)

Wenn die Verschlüsselung für einen Dateityp ausgeführt wird, der blockiert ist, tritt ein [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes)-Fehler auf.

### Datei-API – Dateiunterstützungsdetails

Systemeigene Unterstützung kann für einen beliebigen Dateityp (Erweiterung) hinzugefügt werden. Zum Beispiel wird eine beliebige Erweiterung &lt;ext&gt; (nicht Office), \*.p&lt;ext&gt; verwendet, wenn die Administratorkonfiguration für diese Erweiterung NATIVE lautet.

**Office-Dateien**

-   Dateierweiterungen: DOC, DOT, XLA, XLS, XLT, PPS, PPT, DOCM, DOCX, DOTM, DOTX, XLAM, XLSB, XLSM, XLSX, XLTM, XLTX, XPS, POTM, POTX, PPSX, PPSM, PPTM, PPTX, THMX.
-   Protection type = Native (default): „sample.docx“ wird in „sample.docx“ verschlüsselt.
-   Protection type = Pfile: hat für Office-Dateien dieselbe Auswirkung wie systemeigen.
-   Off: deaktiviert Verschlüsselung.

**PDF-Dateien**

-   Protection type = Native: „sample.pdf“ wird als „sample.ppdf“ verschlüsselt und benannt.
-   Protection type = Pfile: „sample.pdf“ wird als „sample.pdf.pfile“ verschlüsselt und benannt.
-   Off: deaktiviert Verschlüsselung.

**Alle anderen Dateiformate**

-   Protection type = Pfile: sample. *zzz* wird als „sample.*zzz*.pfile“ verschlüsselt und benannt, wobei „zzz“ die ursprüngliche Dateierweiterung ist.
-   Off: deaktiviert Verschlüsselung.

### Beispiele

Die folgenden Einstellungen aktivieren PFile-Verschlüsselung für TXT-Dateien. Für Office-Dateien wird systemeigener Schutz aktiviert (standardmäßig), für TXT-Dateien wird PFile-Schutz aktiviert, und für alle anderen Dateien wird der Schutz blockiert (standardmäßig).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               txt
                  Encryption = Pfile
```

Die folgenden Einstellungen aktivieren PFile-Verschlüsselung für alle Nicht-Office-Dateien außer TXT-Dateien. Für Office-Dateien wird systemeigener Schutz aktiviert (standardmäßig), für TXT-Dateien wird Schutz blockiert, und für alle anderen Dateien wird PFile-Schutz angewendet.

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               *
                  Encryption = Pfile
               txt
                  Encryption = Off
```

Die folgenden Einstellungen deaktivieren systemeigene Verschlüsselung für DOCX-Dateien. Für Office-Dateien, mit Ausnahme von DOCX-Dateien, wird systemeigener Schutz angewendet (standardmäßig), und für alle anderen Dateien wird Schutz blockiert (standardmäßig).

```
HKEY_LOCAL_MACHINE
   Software
      Microsoft
         MSIPC
            FileProtection
               docx
                  Encryption = Off
```

### Verwandte Themen

* [Hinweise für Entwickler](developer-notes.md)
* [**IPCERROR\_FILE\_ENCRYPT\_BLOCKED**](/rights-management/sdk/2.1/api/win/error%20codes)
 

 





<!--HONumber=Apr16_HO3-->

