---
title: 'Unterstützte Dateitypen: Microsoft Information Protection SDK'
description: Technische Details zu unterstützten Dateitypen, Dateinamen Erweiterungen und Schutz Ebenen für Administratoren, die für das Microsoft Information Protection Software Development Kit zuständig sind.
author: msmbaldwin
ms.author: mbaldwin
ms.date: 08/16/2020
ms.topic: conceptual
ms.service: information-protection
ms.openlocfilehash: e247a31b364c40f270538d73815464491fca7647
ms.sourcegitcommit: 8e48016754e6bc6d051138b3e3e3e3edbff56ba5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2021
ms.locfileid: "97864854"
---
# <a name="file-types-supported-by-the-microsoft-information-protection-sdk"></a>Vom Microsoft Information Protection SDK Unterstützte Dateitypen

Das Microsoft Information Protection SDK kann Folgendes auf Dokumente und e-Mails anwenden:

- Nur Klassifizierung

- Klassifizierung und Schutz

- Nur Schutz

Das Microsoft Information Protection SDK kann auch den Inhalt einiger Dateitypen mithilfe von bekannten sensiblen Informationstypen oder regulären Ausdrücken untersuchen, die Sie definieren.

Verwenden Sie die folgenden Informationen, um zu überprüfen, welche Dateitypen das Microsoft Information Protection SDK unterstützt, welche verschiedenen Schutz Ebenen Sie verwenden und wie Sie die Standardschutz Ebene ändern können, und um festzustellen, welche Dateien von der Klassifizierung und dem Schutz automatisch ausgeschlossen (übersprungen) werden.

## <a name="file-types-supported-for-classification-only"></a>Nur für die Klassifizierung unterstützte Dateitypen

Folgende Dateitypen können klassifiziert werden, auch wenn diese nicht geschützt sind.

- **Adobe Portable Document Format**: .pdf

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft XPS**: .xps .oxps

- **Bilder**: JPG, JPE, JPEG, JIF, JFIF, JFI PNG, TIF, TIFF

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng

- **Microsoft Office**: Dateitypen in der folgenden Tabelle.

    Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und Office Open XML für die folgenden Office-Programme: Word, Excel und PowerPoint.

    | Office-Dateityp                                                                                                                                                                                                                                               | Office-Dateityp                                                                                                                                                                                                                                 |
    | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
    | .doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />VDW<br /><br />.vsd | VSDM<br /><br /> VSDX<br /><br />VSS<br /><br />VSSM<br /><br />VST<br /><br />VSTM<br /><br />VSSX<br /><br />VSTX<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx |

Zusätzliche Dateitypen unterstützen die Klassifizierung, wenn sie zudem geschützt sind. Weitere Informationen zu diesen Dateitypen finden Sie im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).

Wenn beispielsweise eine Bezeichnung **Allgemein**, die Klassifizierung anwendet und keinen Schutz anwendet, können Sie die **Allgemeine** Bezeichnung auf eine Datei mit dem Namen sales.pdf anwenden, aber Sie können diese Bezeichnung nicht auf eine Datei mit dem Namen sales.txt anwenden.

Wenn außerdem eine Bezeichnung **vertraulich \ alle Mitarbeiter** Klassifizierung und Schutz anwenden, können Sie diese Bezeichnung auf eine Datei namens sales.pdf und eine Datei mit dem Namen sales.txt anwenden. Sie können den Schutz auch ohne die Klassifizierung auf diese Dateien anwenden.

## <a name="file-types-supported-for-protection"></a>Für den Schutz unterstützte Dateitypen

Das Microsoft Information Protection SDK unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben.

| Art des Schutzes     | Systemeigenes Format                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | Allgemein                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Beschreibung            | Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.                                                                                                                                                                                                                                                                                       | Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Sicherheitsebene, zu der Dateikapselung mithilfe des Dateityps PFILE und Authentifizierung gehören, um zu überprüfen, ob ein Benutzer berechtigt ist, die Datei zu öffnen.                                                                                                                                                                                                                                                                                              |
| Schutz             | Der Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts beim Schützen der Dateien festgelegt wurden, erzwungen, wenn der Inhalt im Azure Information Protection-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird | Der Schutz der Dateien wird auf folgende Weise erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für Personen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben. Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Die Überwachungsprotokollierung von autorisierten Benutzern, die Dateien öffnen und auf diese zugreifen kommt vor. Nutzungsrechte werden jedoch nicht erzwungen. |
| Standardebene für Dateitypen | Dies ist die Standardebene des Schutzes für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt, [Unterstützte Dateitypen für Klassifizierung und Schutz](#supported-file-types-for-classification-and-protection).                                                                                                                                                                              | Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den nativen Schutz unterstützt werden.                                                                                                                                                                                                                                                                                                                                                                                             |

Sie können die Standardschutz Ebene ändern, die das Microsoft Information Protection SDK anwendet. Sie können die Standard Ebene von System eigen in generisch, von generisch zu System eigen ändern und sogar verhindern, dass das Microsoft Information Protection SDK Schutz anwendet.

### <a name="file-sizes-supported-for-protection"></a>Für den Schutz unterstützte Dateigrößen

Ab Microsoft Information Protection SDK 1,6 beträgt die maximale Standarddatei Größe 6 GB. Diese Einstellung kann bei Bedarf überschrieben werden. Es gelten noch weniger Standardeinstellungen für ältere Office-Plattformen.


- **Bei Office-Dateien:**

  | Office-Anwendung                                                                                                          | Maximale unterstützte Dateigröße                                                                                                |
  | --------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
  | Word 2007 (nur von AD RMS unterstützt)<br /><br />Word 2010<br /><br />Word 2013<br /><br />Word 2016                         | 32-Bit: 512 MB<br /><br />64-Bit: 512 MB                                                                                   |
  | Excel 2007 (nur von AD RMS unterstützt)<br /><br />Excel 2010<br /><br />Excel 2013<br /><br />Excel 2016                     | 32-Bit: 2 GB<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt                                            |
  | PowerPoint 2007 (nur von AD RMS unterstützt)<br /><br />PowerPoint 2010<br /><br />PowerPoint 2013<br /><br />PowerPoint 2016 | 32-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt<br /><br />64-Bit: nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt |

- **Bei allen anderen Dateien**:

    Zum Schutz anderer Dateitypen und zum Entfernen des Schutzes für diese Dateitypen mit dem SDK: die maximale Dateigröße wird nur durch den verfügbaren Speicherplatz und Arbeitsspeicher beschränkt.

### <a name="supported-file-types-for-classification-and-protection"></a>Unterstützte Dateitypen für Klassifizierung und Schutz

In der folgenden Tabelle ist eine Teilmenge der Dateitypen aufgeführt, die den systemeigenen Schutz durch das Microsoft Information Protection SDK unterstützen und auch klassifiziert werden können.

Diese Dateitypen sind separat aufgeführt, da wenn sie nativ geschützt sind, die Namenserweiterung der ursprünglichen Datei geändert wird und diese Dateien dadurch schreibgeschützt werden. Beachten Sie, dass wenn Dateien generisch geschützt sind, die ursprüngliche Namenserweiterung immer in PFILE geändert wird.

> [!WARNING]
> Wenn Sie über Firewalls, Webproxys oder Sicherheitssoftware verfügen, die Erweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie die Netzwerkgeräte und die Software möglicherweise zur Unterstützung der neuen Erweiterungen neu konfigurieren.

| Ursprüngliche Dateinamenerweiterung | Geschützte Dateierweiterung |
| ---------------------------- | ----------------------------- |
| .txt                         | PTXT                         |
| .xml                         | PXML                         |
| .jpg                         | PJPG                         |
| JPEG                        | PJPEG                        |
| .pdf                         | PPDF [[1]](#footnote-1)      |
| .png                         | PPNG                         |
| .tif                         | PTIF                         |
| TIFF                        | PTIFF                        |
| BMP                         | PBMP                         |
| .gif                         | PFIG                         |
| JPE                         | PJPE                         |
| JFIF                        | PJFIF                        |

###### <a name="footnote-1"></a>Fußnote 1
Mit der neuesten Version des Microsoft Information Protection SDK wird die Dateinamenerweiterung des geschützten PDF-Dokuments als PDF-Datei angezeigt.

In der nächsten Tabelle sind die verbleibenden Dateitypen aufgeführt, die den systemeigenen Schutz durch das Microsoft Information Protection SDK unterstützen und auch klassifiziert werden können. Sie erkennen diese als Dateitypen für Microsoft Office-Apps. Die unterstützten Dateiformate für diese Dateitypen sind die 97-2003-Dateiformate und Office Open XML für die folgenden Office-Programme: Word, Excel und PowerPoint.

Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

| Von Office unterstützte Dateitypen                                                                                                                                                                                                                  | Von Office unterstützte Dateitypen                                                                                                                                                                                                                  |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| .doc<br /><br />.docm<br /><br />.docx<br /><br />.dot<br /><br />.dotm<br /><br />.dotx<br /><br />.potm<br /><br />.potx<br /><br />.pps<br /><br />.ppsm<br /><br />.ppsx<br /><br />.ppt<br /><br />.pptm<br /><br />.pptx<br /><br />VSDM | VSDX<br /><br />VSSM<br /><br />VSSX<br /><br />VSTM<br /><br />VSTX<br /><br />.xla<br /><br />.xlam<br /><br />.xls<br /><br />.xlsb<br /><br />.xlt<br /><br />.xlsm<br /><br />.xlsx<br /><br />.xltm<br /><br />.xltx<br /><br />.xps |

### <a name="limitations-for-container-files-such-as-zip-msg-files"></a>Einschränkungen für Container Dateien, z. b. zip-, msg-Dateien

Containerdateien sind Dateien, die andere Dateien enthalten. Ein typisches Beispiel sind ZIP-Dateien, die komprimierte Dateien enthalten. Weitere Beispiele hierfür sind. rar,. 7z,. msg-Dateien, rpmsg-Dateien und PDF-Dokumente, die Anhänge enthalten.

Sie können diese Containerdateien klassifizieren und schützen, jedoch werden die Klassifizierung und der Schutz nicht auf jede Datei im Container angewendet. Ebenso kann eine geschützte Containerdatei mit dem SDK nicht geschützt werden, aber der Schutz (falls angewendet) auf Dateien im Container wird nicht durch den Schutz Vorgang für den Schutz in der Containerdatei rekursiv entfernt. Die Anwendungsentwickler sind für das rekursierende und das Aufheben des Schutzes von Dateien innerhalb der Container zuständig.

Bei einer Containerdatei, die klassifizierte und geschützte Dateien enthält, müssen Sie zuerst die Dateien extrahieren, um die Einstellungen für die Klassifizierung oder den Schutz zu ändern.
