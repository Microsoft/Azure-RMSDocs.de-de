---
title: Technische Übersicht für die RMS-Freigabeanwendung – AIP
description: Technische Details für Administratoren in Unternehmensnetzwerken, die für die Bereitstellung der RMS-Freigabeanwendung für Windows verantwortlich sind.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/02/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: f7b13fa4-4f8e-489a-ba46-713d7a79f901
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ec0c231e2036dc66b941be7f764bb5e5fd5c518a
ms.sourcegitcommit: d06594550e7ff94b4098a2aa379ef2b19bc6123d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53023785"
---
# <a name="technical-overview-and-protection-details-for-the-microsoft-rights-management-sharing-application"></a>Technische Übersicht und Details zur Schutzfunktion der Microsoft Rights Management-Freigabeanwendung

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*


Die Microsoft Rights Management-Freigabeanwendung ist eine optional herunterladbare Anwendung für Microsoft Windows und andere Plattformen, die Folgendes bereitstellt:

-   Schutz einzelner Dateien, mehrerer Dateien gleichzeitig oder aller in einem ausgewählten Ordner enthaltenen Dateien.

-   Vollständige Unterstützung für den Schutz beliebiger Dateitypen sowie eine integrierte Anzeige für häufig verwendete Text- und Bilddateitypen.

-   Allgemeiner Schutz für Dateien, die RMS-Schutz nicht unterstützen.

-   Vollständige Interoperabilität mit Dateien, die mit Office Information Rights Management (IRM) geschützt sind.

-   Vollständige Interoperabilität mit PDF-Dateien, die mit der Dateiklassifizierungsinfrastruktur (FCI) geschützt sind, sowie unterstützte PDF-Erstellungstools.

Die Microsoft Rights Management-Freigabeanwendung verwendet die [AD RMS-Client 2.1-Runtime](http://www.microsoft.com/download/details.aspx?id=38396). Mithilfe der Funktionalität von AD RMS 2.1 stellt die Microsoft Rights Management-Freigabeanwendung Endbenutzern einen einfachen Schutz und eine einfache Nutzung bereit.

Ab der RMS-Version von Oktober 2013 können Sie Dokumente nativ mithilfe von Office 2010 schützen und an andere Personen in einem anderen Unternehmen senden, die diese dann mithilfe des Azure Rights Management-Diensts von Azure Information Protection nutzen können. Darüber hinaus können Sie mit dieser Version bei Verwendung von AD RMS im Kryptografiemodus 2 RMS for Individuals verwenden und Inhalte von Personen in einem anderen Unternehmen, das den Azure Rights Management-Dienst verwendet, nutzen. Weitere Informationen zum Kryptografiemodus 2 finden Sie unter [AD RMS-Kryptografiemodi](https://technet.microsoft.com/library/hh867439%28v=ws.10%29.aspx).

Informationen zur Bereitstellung finden Sie unter [Automatische Bereitstellung für die Microsoft Rights Management-Freigabeanwendung](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application).

## <a name="levels-of-protection--native-and-generic"></a>Schutzebenen – systemeigen und generisch
Die Microsoft Rights Management-Freigabeanwendung unterstützt den Schutz auf zwei unterschiedlichen Ebenen, wie in der folgenden Tabelle beschrieben wird.

|Typ des Schutzes|Systemeigenes Format|Generisch|
|----------------------|----------|-----------|
|Beschreibung|Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen, die einen Rights Management-Dienst unterstützen, stellt der native Schutz eine starke Schutzebene bereit, die Verschlüsselung und Durchsetzung von Rechten (Berechtigungen) umfasst.|Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz eine Schutzebene, die Dateiverkapselung mit dem PFILE-Dateityp und Authentifizierung umfasst, um zu überprüfen, ob ein Benutzer zum Öffnen der Datei autorisiert ist.|
|Schutz|Dateien werden vollständig verschlüsselt, und der Schutz folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei per E-Mail oder Zugriffsberechtigung über Datei- oder Freigabeberechtigungen erhalten<br /><br />– Außerdem werden Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, wenn Dateien geschützt werden, vollständig erzwungen, wenn der Inhalt im IP-Viewer (für geschützte Text- und Bilddateien) oder in der zugeordneten Anwendung (für alle anderen unterstützten Dateitypen) gerendert wird|Dateischutz wird folgendermaßen erzwungen:<br /><br />– Bevor geschützter Inhalt gerendert wird, muss eine erfolgreiche Authentifizierung für diejenigen stattfinden, die die Datei öffnen dürfen und Zugriff darauf haben Wenn die Autorisierung fehlschlägt, wird die Datei nicht geöffnet.<br /><br />– Die Nutzungsrechte und Richtlinien, die vom Besitzer des Inhalts festgelegt werden, werden angezeigt, um autorisierte Benutzer über die Richtlinie für die vorgesehene Verwendung zu informieren<br /><br />– Eine Überwachungsprotokollierung der autorisierten Benutzer, die auf Dateien zugreifen und diese öffnen, findet statt, es werden aber keine Nutzungsrechte durch nicht unterstützende Anwendungen erzwungen|
|Standard für Dateitypen|Dies ist die Standardschutzebene für die folgenden Dateitypen:<br /><br />– Text- und Bilddateien<br /><br />– Microsoft Office-Dateien (Word, Excel, PowerPoint)<br /><br />– Portable Document Format (PDF)<br /><br />Weitere Informationen finden Sie im folgenden Abschnitt: [Unterstützte Dateitypen und Dateinamenerweiterungen](#supported-file-types-and-file-name-extensions).|Dies ist der Standardschutz für alle anderen Dateitypen (z.B. VSDX, RTF usw.), die nicht durch den vollständigen Schutz unterstützt werden.|
Sie können die Standardschutzebene ändern, die die RMS-Freigabeanwendung anwendet. Sie können die Standardebene von systemeigen zu generisch oder von generisch zu systemeigen ändern und sogar verhindern, dass die RMS-Freigabeanwendung Schutz anwendet. Weitere Informationen finden Sie im Abschnitt [Ändern der Standardschutzebene von Dateien](#changing-the-default-protection-level-of-files) dieses Artikels.

## <a name="supported-file-types-and-file-name-extensions"></a>Unterstützte Dateitypen und Dateinamenerweiterungen
Die folgende Tabelle enthält die Dateitypen, die systemeigen von der Microsoft Rights Management-Freigabeanwendung unterstützt werden. Für diese Dateitypen wird die ursprüngliche Namenserweiterung geändert, wenn systemeigener Schutz angewendet wird, und diese Dateien schreibgeschützt werden.

Wenn die RMS-Freigabeanwendung darüber hinaus systemeigen eine Word-, Excel- oder PowerPoint-Datei schützt, die Benutzer durch Freigabe schützen, erstellt diese Aktion automatisch eine zweite Datei, die eine Kopie des Originals mit demselben Namen darstellt, aber mit der **PPDF** -Dateinamenerweiterung ¹. Diese Version der Datei stellt sicher, dass der Empfänger, die die RMS-Freigabeanwendung installiert, immer die Datei öffnen kann, die über systemeigenen Schutz verfügt.

Für Dateien, die generisch geschützt sind, wird die ursprüngliche Namenserweiterung immer in PFILE geändert.

> [!WARNING]
> Wenn Sie Firewalls, Webproxys oder Sicherheitssoftware haben, die Dateinamenerweiterungen überprüfen und entsprechende Maßnahmen ergreifen, müssen Sie diese möglicherweise zur Unterstützung der neuen Dateinamenerweiterungen neu konfigurieren.

|Ursprüngliche Dateinamenerweiterung|RMS-geschützte Dateinamenerweiterung|
|--------------------------------|-------------------------------------|
|TXT|PTXT|
|XML|PXML|
|JPG|PJPG|
|JPEG|PJEG|
|PDF|PPDF|
|PNG|PPNG|
|TIF|PTIF|
|TIFF|PTIFF|
|BMP|PBMP|
|GIF|PGIF|
|JPE|PJPE|
|JFIF|PJFIF|
|JT|PJT|
¹ PDF-Rendering unterstützt von Foxit. Copyright © 2003–2014, Foxit Corporation.

In der folgenden Tabelle werden die Dateitypen aufgeführt, die von der Microsoft Rights Management-Freigabeanwendung in Microsoft Office 2016, Office 2013 und Office 2010 nativ unterstützt werden. Für diese Dateitypen bleiben die Dateierweiterungen nach dem Schutz der Dateien durch einen Rights Management-Dienst unverändert.

|Von Office unterstützte Dateitypen|Von Office unterstützte Dateitypen|
|----------------------------------|----------------------------------|
|DOC<br /><br />DOCM<br /><br />DOCX<br /><br />DOT<br /><br />DOTM<br /><br />DOTX<br /><br />POTM<br /><br />POTX<br /><br />PPS<br /><br />PPSM<br /><br />PPSX<br /><br />PPT<br /><br />PPTM|PPTX<br /><br />THMX<br /><br />XLA<br /><br />XLAM<br /><br />XLS<br /><br />XLSB<br /><br />XLT<br /><br />XLSM<br /><br />XLSX<br /><br />XLTM<br /><br />XLTX<br /><br />XPS|

### <a name="changing-the-default-protection-level-of-files"></a>Ändern der Standardschutzebene von Dateien
Sie können ändern, wie die RMS-Freigabeanwendung Dateien durch Bearbeiten der Registrierung schützt. Beispielsweise können Sie erzwingen, dass Dateien, die systemeigenen Schutz unterstützen, durch die RMS-Freigabeanwendung generisch geschützt werden.

Dafür kann es folgende Gründe geben:

-   Um sicherzustellen, dass alle Benutzer die Datei auf ihren mobilen Geräten öffnen können.

-   Um sicherzustellen, dass alle Benutzer die Datei öffnen können, wenn sie keine Anwendung haben, die systemeigenen Schutz unterstützt.

-   Um Sicherheitssysteme zu unterstützen, die Maßnahmen für Dateien anhand der Dateinamenerweiterung ergreifen und neu konfiguriert werden können, um die PFILE-Erweiterung zu unterstützen, aber nicht neu konfiguriert werden können, um mehrere Dateinamenerweiterungen für den systemeigenen Schutz zu unterstützen.

Auf ähnliche Weise können Sie erzwingen, dass die RMS-Freigabeanwendung systemeigenen Schutz auf Dateien anwendet, die in der Standardeinstellung durch generischen Schutz geschützt würden. Dies ist möglicherweise geeignet, wenn Sie eine Anwendung haben, die RMS-APIs unterstützt, zum Beispiel eine Line-of-Business-Anwendung, die von Ihren internen Entwicklern geschrieben wurde, oder eine Anwendung, die von einem unabhängigen Softwareanbieter (ISV) erworben wurde.

Sie können auch erzwingen, dass die RMS-Freigabeanwendung den Schutz von Dateien blockiert (der systemeigene oder generische Schutz wird nicht angewendet). Dies kann z. B. erforderlich sein, wenn Sie eine automatische Anwendung oder einen automatischen Dienst haben, die bzw. der eine bestimmte Datei öffnen muss, um ihren Inhalt zu verarbeiten. Wenn Sie den Schutz für einen Dateityp blockieren, können Benutzer die RMS-Freigabeanwendung nicht verwenden, um eine Datei mit diesem Dateityp zu schützen. Wenn sie es versuchen, wird eine Meldung angezeigt, dass der Administrator den Schutz verhindert hat, und sie müssen ihre Aktion zum Schutz der Datei abbrechen.

Bearbeiten Sie die folgenden Registrierungseinträge, um die RMS-Freigabeanwendung so zu konfigurieren, dass sie generischen Schutz auf alle Dateien anwendet, die in der Standardeinstellung durch native Schutzfunktionen geschützt würden. Beachten Sie, dass Sie die Schlüssel „RmsSharingApp“ oder „FileProtection“ manuell erstellen müssen, falls diese nicht vorhanden sind.

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection**: Erstellen Sie einen neuen Schlüssel mit dem Namen *.

    Diese Einstellung gibt Dateien mit beliebiger Erweiterung an.

2.  Erstellen Sie im neu hinzugefügten Schlüssel für HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\\\* einen neuen Zeichenfolgenwert (REG_SZ) namens **Encryption** mit dem Datenwert **Pfile**.

    Diese Einstellung führt dazu, dass die RMS-Freigabeanwendung generischen Schutz anwendet.

Diese beiden Einstellungen führen dazu, dass die RMS-Freigabeanwendung generischen Schutz auf alle Dateien mit einer Dateinamenerweiterung anwendet. Wenn dies Ihr Ziel ist, ist keine weitere Konfiguration erforderlich. Sie können aber auch Ausnahmen für bestimmte Dateitypen definieren, damit diese weiterhin systemeigen geschützt werden. Zu diesem Zweck müssen Sie drei zusätzliche Registrierungseinträge für jeden Dateityp bearbeiten:

1.  **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection**: Fügen Sie einen neuen Schlüssel mit dem Namen der Dateinamenerweiterung (ohne vorangestellten Punkt) hinzu.

    Für Dateien mit der Erweiterung „.docx“ erstellen Sie beispielsweise einen Schlüssel namens **DOCX**.

2.  Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z.B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\DOCX**) einen neuen DWORD-Wert namens **AllowPFILEEncryption** mit dem Wert **0**.

3.  Erstellen Sie im neu hinzugefügten Dateitypschlüssel (z.B. **HKEY_LOCAL_MACHINE\Software\Microsoft\MSIPC\RmsSharingApp\FileProtection\DOCX**) einen neuen Zeichenfolgenwert namens **Encryption** mit dem Wert **Native**.

Durch diese Einstellungen sind alle Dateien generisch geschützt, mit Ausnahme der Dateien mit der Erweiterung DOCX, die systemeigen durch die RMS-Freigabeanwendung geschützt werden.

Wiederholen Sie diese drei Schritte für andere Dateitypen, die Sie als Ausnahmen definieren möchten, weil sie systemeigenen Schutz unterstützen und nicht durch die RMS-Freigabeanwendung generisch geschützt werden sollen.

Sie können ähnliche Registrierungseinträge für andere Szenarien durch Ändern des Werts der **Encryption** -Zeichenfolge vornehmen, die die folgenden Werte unterstützt:

-   **Pfile**: Allgemeiner Schutz

-   **Native**: systemeigener Schutz

-   **Off**: Schutz blockieren

## <a name="see-also"></a>Weitere Informationen
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)

