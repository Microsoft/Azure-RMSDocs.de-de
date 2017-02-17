---
title: "Klassifizieren und Schützen einer Datei oder E-Mail mithilfe von Azure Information Protection | Azure Information Protection"
description: "Anweisungen zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 171a47f9c22dec24f72f8f21392d6577efd807a5
ms.openlocfilehash: d050629999c3a886eb8d422f4f38c22d586e0824


---

# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Klassifizieren und Schützen einer Datei oder E-Mail mithilfe von Azure Informationen Protection

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

**[Diese Version des Clients ist eine Vorschau und unterliegt Änderungen.]**

Die einfachste Möglichkeit zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails bietet sich, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können Dateien jedoch auch über den **Datei-Explorer** klassifizieren und schützen, der zusätzliche Dateitypen unterstützt und eine bequeme Methode zum gleichzeitigen Klassifizieren und Schützen mehrerer Dateien darstellt.

## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails

Verwenden Sie die Azure Information Protection-Leiste, und wählen Sie eine der Bezeichnungen aus, die für Sie konfiguriert wurde. Beispiel:

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-bar-not-set-callout.png)


## <a name="using-file-explorer-to-classify-and-protect-files"></a>Verwenden des Datei-Explorer zum Klassifizieren und Schützen von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie eine einzelne Datei, mehrere Dateien oder einen Ordner schnell klassifizieren und schützen. 

Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch für die Klassifizierungs- und Schutzoptionen ausgewählt, die Sie festlegen. Neue Dateien, die Sie in diesem Ordner oder Unterordner erstellen, werden jedoch nicht automatisch mit diesen Optionen konfiguriert.

Wenn Sie den Datei-Explorer zum Klassifizieren und Schützen Ihrer Dateien verwenden, werden Sie möglicherweise bemerken, dass die Bezeichnungen nicht immer verfügbar sind. Dieses Problem tritt auf, wenn die von Ihnen ausgewählten Dateien die Klassifizierung nicht unterstützen. Für diese Dateien können Sie nur eine Bezeichnung auswählen, wenn Ihr Administrator die Bezeichnung konfiguriert hat, um Schutz zu bieten. Alternativ können Sie auch eigene Schutzeinstellungen angeben. 

Eine Liste der vom Datei-Explorer unterstützten Dateitypen finden Sie im Abschnitt [Für Klassifizierung und Schutz unterstützte Dateitypen](#file-types-supported-for-classification-and-protection) auf dieser Seite.


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>So klassifizieren und schützen Sie eine Datei mithilfe des Datei-Explorer

1.  Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen (Vorschau)**, und wählen Sie dadurch diese Option aus. 

2. Verwenden Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Bezeichnungen wie in einer Office-Anwendung, wodurch die Klassifizierung und der Schutz gemäß der Definition Ihres Administrators festgelegt werden. Wenn eine Bezeichnung nicht ausgewählt werden kann (sie ist nicht verfügbar), unterstützt die ausgewählte Datei die Klassifizierung nicht, aber Sie können sie schützen.

3. Wenn Sie lieber eigene Schutzeinstellungen angeben möchten, anstatt die Schutzeinstellungen zu verwenden, die der Administrator für Ihre Bezeichnung konfiguriert hat, wählen Sie **Mit benutzerdefinierten Berechtigungen schützen** aus.
    
    Die von Ihnen angegebenen benutzerdefinierten Berechtigungen sind keine Ergänzung der vom Administrator für Ihre ausgewählte Bezeichnung definierten Schutzeinstellungen, sondern ersetzen diese.  

4. Wenn Sie die Option der benutzerdefinierten Berechtigungen ausgewählt haben, geben Sie jetzt Folgendes an:

    - **Berechtigungen auswählen**: Wählen Sie die Zugriffsebene, die die Benutzer erhalten sollen, wenn Sie die ausgewählte(n) Datei(en) schützen.
    
    - **Benutzer auswählen**: Geben Sie die Personen an, die die Berechtigungen erhalten sollen, die Sie für Ihre Datei(en) ausgewählt haben. Für Benutzer und Gruppen in Ihrer Organisation können Sie das Adressbuch durchsuchen, und diese dann auswählen. Für Personen in einer anderen Organisation müssen Sie die vollständige E-Mail-Adresse angeben. Stellen Sie sicher, dass Sie eine geschäftliche E-Mail-Adresse verwenden, da persönliche E-Mail-Adressen derzeit nicht unterstützt werden.
        
    - **Ablaufzugriff**: Wählen Sie diese Option nur für zeitempfindliche Dateien aus, damit die von Ihnen angegebenen Personen die ausgewählte(n) Datei(en) nach einem von Ihnen angegebenen Datum nicht mehr öffnen können. Sie können weiterhin die ursprüngliche Datei öffnen, aber nach Mitternacht (aktuelle Zeitzone) können die Personen an dem von Ihnen angegebenen Tag die Datei nicht mehr öffnen.

5. Klicken Sie auf **Anwenden** und dann auf **Schließen**.

Die ausgewählte(n) Datei(en) werden jetzt gemäß Ihrer Auswahl klassifiziert und geschützt. In einigen Fällen (wenn die Dateinamenerweiterung durch Hinzufügen des Schutzes geändert wird) wird die ursprüngliche Datei im Datei-Explorer durch eine neue Datei mit dem Schlosssymbol für Azure Information Protection ersetzt. Beispiel:

![Geschützte Datei mit Schlosssymbol für Azure Information Protection](../media/Pfile.png)

Wenn Sie Ihre Meinung hinsichtlich Klassifizierung und Schutz ändern oder Ihre Einstellungen später ändern müssen, wiederholen Sie diesen Prozess mit den neuen Einstellungen.

Die Klassifizierung und der Schutz, die Sie angegeben haben, bleiben der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. Wenn Sie die Datei geschützt haben, können Sie verfolgen, wie sie von Personen verwendet wird und den Zugriff ggf. widerrufen. Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer geschützten Dokumente bei Verwendung von Azure Information Protection](client-track-revoke.md). 

#### <a name="file-types-supported-for-classification-and-protection"></a>Für Klassifizierung und Schutz unterstützte Dateitypen

Die ausschließliche Klassifizierung wird für die folgenden Dateitypen unterstützt. Andere Dateitypen unterstützen die Klassifizierung, wenn sie zudem geschützt sind.

- **Microsoft Visio**: .vsdx, .vsdm, .vssx, .vssm, .vsd, .vdw, .vst

- **Microsoft Project**: .mpp, .mpt

- **Microsoft Publisher**: .pub

- **Microsoft Office 97, Office 2010, Office 2003**: .xls, .xlt, .doc, .dot, .ppt, .pps, .pot

- **Microsoft XPS**: .xps .oxps

- **Bilder**: .jpg, .jpe, .jpeg, .jif, .jfif, .jfi.png, .tif, .tiff

- **SolidWorks**: .sldprt, .slddrw, .sldasm

- **Autodesk Design Review 2013**: .dwfx

- **Adobe Photoshop**: .psd

- **Digital Negative**: .dng


Der Schutz mithilfe des Rights Management Service wird für die Dateitypen unterstützt, die in der [Datei-API-Konfiguration](../develop/file-api-configuration.md) dokumentiert sind. Dieser Schutz kann automatisch angewendet werden, wenn Sie eine vom Administrator konfigurierte Bezeichnung auswählen, oder Sie können Ihre eigenen Schutzeinstellungen mithilfe von [Berechtigungsstufen](../deploy-use/configure-usage-rights.md#rights-included-in-permissions-levels) angeben. 


## <a name="other-instructions"></a>Sonstige Anweisungen
Anweisungen zur Vorgehensweise finden Sie in den folgenden Abschnitten des Azure Information Protection-Benutzerhandbuchs:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Jan17_HO4-->


