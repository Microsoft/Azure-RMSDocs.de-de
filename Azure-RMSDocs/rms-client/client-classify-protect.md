---
title: Klassifizieren und Schützen von Dateien und E-Mails mithilfe von Azure Information Protection
description: Anweisungen zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/12/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b1d46cb3c98c520ab6900f910f691af920337334
ms.sourcegitcommit: 9dc6da0fb7f96b37ed8eadd43bacd1c8a1a55af8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2019
ms.locfileid: "54393466"
---
# <a name="user-guide-classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Benutzerhandbuch: Klassifizieren und Schützen einer Datei oder E-Mail mithilfe von Azure Informationen Protection

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

> [!NOTE]
> Mithilfe dieser Anleitung können Sie Ihre Dokumente und E-Mails klassifizieren und schützen. Wenn Sie Ihre Dokumente und E-Mails nur klassifizieren und nicht schützen müssen, lesen Sie die [Anleitung zum Klassifizieren](client-classify.md). Wenn Sie nicht sicher sind, welche Anleitung Sie verwenden sollen, wenden Sie sich an Ihren Systemadministrator oder den Helpdesk.

Ihre Dokumente und E-Mails können Sie am einfachsten klassifizieren und schützen, indem Sie diese in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können jedoch auch Dateien mithilfe des **Datei-Explorers** klassifizieren und schützen. Diese Methode unterstützt weitere Dateitypen und ist ein bequemer Weg zum Klassifizieren und Schützen mehrerer Dateien gleichzeitig. Diese Methode unterstützt den Schutz von Office-Dokumenten, PDF-Dateien, Text- und Bilddateien sowie einer Vielzahl anderer Dateien. 

Wenn Ihre Bezeichnung Schutz für ein Dokument anwendet, ist das geschütztes Dokument nicht für die Speicherung auf SharePoint oder OneDrive geeignet. Folgende Funktionen werden von diesen Speicherorten für geschützte Dateien nicht unterstützt: Gemeinsame Dokumenterstellung, Office Online, Suche, Dokumentvorschau, Miniaturansicht und eDiscovery. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Sichere Freigabe einer Datei für Personen außerhalb Ihrer Organisation

Geschützte Dateien können für andere Personen sicher freigegeben werden. Sie hängen z.B. ein geschütztes Dokument an eine E-Mail an.

Bevor Sie Dateien mit Personen außerhalb Ihrer Organisation teilen, wenden Sie sich an den Helpdesk oder Ihren Administrator, um herauszufinden, wie Dateien für externe Benutzer geschützt werden.

Wenn Ihre Organisation z.B. regelmäßig mit Personen einer anderen Organisation kommuniziert, hat Ihr Administrator womöglich Bezeichnungen konfiguriert, die Schutz in einem Umfang festlegen, damit diese Personen geschützte Dokumente lesen und verwenden können. Wählen Sie anschließend diese Bezeichnungen aus, um die Dokumente, die geteilt werden sollen, zu klassifizieren und zu schützen.

Falls alternativ für externe Benutzer [Business-to-Business-Konten (B2B)](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) erstellt worden sind, können Sie Ihre [Office-App zum Festlegen von Berechtigungen](#set-custom-permissions-for-a-document) oder [Datei-Explorer zum Festlegen benutzerdefinierter Berechtigungen](#using-file-explorer-to-classify-and-protect-files) für ein Dokument verwenden, bevor Sie es teilen. Wenn Sie Ihre eigenen benutzerdefinierten Berechtigungen festlegen und das Dokument bereits für die interne Verwendung geschützt ist, erstellen Sie zunächst eine Kopie der Datei, um die ursprünglichen Berechtigungen beizubehalten. Verwenden Sie dann die Kopie, um die benutzerdefinierten Berechtigungen festzulegen.


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails

Verwenden Sie die Azure Information Protection-Leiste oder die Schaltfläche **Schützen** auf dem Menüband, um eine der Bezeichnungen auszuwählen, die für Sie konfiguriert wurde. 

Die folgende Abbildung zeigt beispielsweise, dass das Dokument noch keine Bezeichnung erhalten hat, da für **Vertraulichkeit** die Option **Nicht festgelegt** auf der Azure Information Protection-Leiste angezeigt wird. Um eine Bezeichnung wie „Allgemein“ festzulegen, klicken Sie auf **Allgemein**. Wenn Sie nicht sicher sind, welche Bezeichnung auf das aktuelle Dokument oder die E-Mail angewendet werden soll, verwenden Sie die QuickInfos für Bezeichnungen, um weitere Informationen zu den einzelnen Bezeichnungen und ihrer Anwendung zu erhalten. 

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-bar-not-set-callout.png)

Wenn auf das Dokument bereits eine Bezeichnung angewendet wurde und Sie diese ändern möchten, können Sie eine andere Bezeichnung auswählen. Wenn die Bezeichnungen nicht auf der Leiste angezeigt werden, klicken Sie zunächst neben dem aktuellen Bezeichnungswert auf das Symbol **Edit label** (Bezeichnung bearbeiten).

Neben der manuellen Auswahl von Bezeichnungen können Bezeichnungen auch auf die folgende Weise angewendet werden:

- Ihr Administrator konfiguriert eine Standardbezeichnung, die Sie beibehalten oder ändern können.

- Ihr Administrator konfiguriert empfohlene Aufforderungen zum Auswählen einer bestimmten Bezeichnung, wenn vertrauliche Daten erkannt wurden. Sie können die Empfehlung übernehmen (und die Bezeichnung anwenden) oder zurückweisen (empfohlene Bezeichnung wird nicht angewendet).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Ausnahmen für die Azure Information Protection-Leiste 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Wenn diese Information Protection-Leiste in Ihren Office-Apps nicht angezeigt wird:

Mögliche Gründe:

- Der Azure Information Protection-Client ist auf Ihrem Computer [nicht installiert](install-client-app.md).

- Der Client ist installiert, jedoch hat Ihr Administrator eine Einstellung vorgenommen, sodass die Leiste nicht angezeigt wird. Wählen Sie stattdessen Bezeichnungen über die Schaltfläche **Schützen** auf der Registerkarte **Datei** im Office-Menüband aus. 

- Ihr Client wird im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt.
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>Wird die erwartete Bezeichnung nicht angezeigt? 

Mögliche Gründe:

- Wenn Ihr Administrator kürzlich eine neue Bezeichnung für Sie konfiguriert hat, schließen Sie alle Instanzen der Office-App und öffnen Sie sie anschließend erneut. Durch diese Aktion werden Änderungen an den Bezeichnungen gesucht.

- Wenn die fehlende Bezeichnung den Schutz anwendet, verwenden Sie möglicherweise eine Version von Office, die das Anwenden des Rights Management-Schutzes nicht unterstützt. Klicken Sie zum Überprüfen auf **Schützen** > **Hilfe und Feedback** Prüfen Sie im Dialogfeld, ob sich im Abschnitt für den **Clientstatus** eine Nachricht mit der Information befindet, dass **dieser Client nicht für Office Professional Plus lizenziert ist**. 
    
    Office Professional Plus ist nicht erforderlich, wenn Sie Office 2016-Apps mit Version 1805 oder höher (Build 9330.2078) nutzen und Ihrem Konto eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“) zugewiesen ist.

- Die Bezeichnung befindet sich möglicherweise in einer bereichsbezogenen Richtlinie, die Ihr Konto nicht umfasst. Wenden Sie sich an den Helpdesk oder Ihren Administrator.

### <a name="set-custom-permissions-for-a-document"></a>Festlegen von benutzerdefinierten Berechtigungen für ein Dokument

Sie können – sofern von Ihrem Administrator erlaubt – eigene Schutzeinstellungen angeben, anstatt die Schutzeinstellungen zu verwenden, die der Administrator für Ihre Bezeichnung konfiguriert hat. Diese Option gilt nur für Dokumente und ist nicht in Outlook verfügbar.

1. Klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen** > **Benutzerdefinierte Berechtigungen**:

    ![Option „Benutzerdefinierte Berechtigungen“](../media/custom-permissions-callout.png)
    
    Wenn keine **benutzerdefinierten Berechtigungen** angezeigt werden, erlaubt Ihr Administrator Ihnen die Verwendung dieser Option nicht.
    
    Beachten Sie Folgendes: Die von Ihnen angegebenen benutzerdefinierten Berechtigungen sind keine Ergänzung der vom Administrator für Ihre ausgewählte Bezeichnung definierten Schutzeinstellungen, sondern ersetzen diese.  

2. Geben Sie im Dialogfeld **Microsoft Azure Information Protection** Folgendes an:

    - **Mit benutzerdefinierten Berechtigungen schützen**: Stellen Sie sicher, dass diese Option aktiviert ist, damit Sie Ihre benutzerdefinierten Berechtigungen angeben und anwenden können. Deaktivieren Sie diese Option, um alle benutzerdefinierten Berechtigungen zu entfernen.
    
    - **Berechtigungen auswählen**: Wenn Sie die Datei so schützen möchten, dass nur Sie darauf zugreifen können, wählen Sie **Nur für mich** aus. Wählen Sie anderenfalls die Zugriffsebene aus, die Sie den Personen gewähren möchten.
    
    - **Benutzer, Gruppen oder Organisationen auswählen**: Geben Sie die Personen an, die die Berechtigungen erhalten sollen, die Sie für Ihre Datei(en) ausgewählt haben. Geben Sie für jeden Benutzer in dieser Organisation die vollständige E-Mail-Adresse, eine Gruppen-E-Mail-Adresse oder einen Domänennamen der Organisation ein. 
        
        Sie können mithilfe des Adressbuchsymbols Benutzer oder Gruppen aus dem Outlook-Adressbuch auswählen.
    
    - **Ablaufzugriff**: Wählen Sie diese Option nur für zeitkritische Dateien aus, damit die von Ihnen angegebenen Personen die ausgewählte(n) Datei(en) nach einem von Ihnen festgelegten Datum nicht mehr öffnen können. Sie können weiterhin die ursprüngliche Datei öffnen, aber nach Mitternacht (aktuelle Zeitzone) können die Personen an dem von Ihnen festgelegten Tag die Datei nicht mehr öffnen.

5. Klicken Sie auf **Übernehmen**, und warten Sie auf die Nachricht **Die benutzerdefinierten Berechtigungen wurden angewendet**. Klicken Sie anschließend auf **Schließen**.

### <a name="safely-sharing-by-email"></a>Sichere Freigabe per E-Mail

Wenn Sie ein Office-Dokument per E-Mail freigeben, können Sie dieses an eine geschützte E-Mail anfügen. Das Dokument wird in diesem Fall automatisch mit denselben Einschränkungen geschützt, die auf die E-Mail angewendet werden. 

Empfohlen wird jedoch, das Dokument erst zu schützen und anschließend an die E-Mail anzufügen. Sie sollten die E-Mail auch schützen, wenn diese vertrauliche Informationen enthält. Das Schützen und anschließende Anfügen eines Dokuments an eine E-Mail bietet zwei Vorteile:

- Sie können das Dokument nachverfolgen und ggf. widerrufen, nachdem Sie es per E-Mail gesendet haben.

- Sie können für das Dokument und die E-Mail unterschiedliche Berechtigungen festlegen.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>Verwenden des Datei-Explorer zum Klassifizieren und Schützen von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie eine einzelne Datei, mehrere Dateien oder einen Ordner schnell klassifizieren und schützen. 

Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch für die Klassifizierungs- und Schutzoptionen ausgewählt, die Sie festlegen. Neue Dateien, die Sie in diesem Ordner oder Unterordner erstellen, werden jedoch nicht automatisch mit diesen Optionen konfiguriert.

Wenn Sie den Datei-Explorer zum Klassifizieren und Schützen Ihrer Dateien verwenden und eine oder mehrere der Bezeichnungen abgeblendet angezeigt werden, unterstützen die ausgewählten Dateien die Klassifizierung nicht. Für diese Dateien können Sie nur eine Bezeichnung auswählen, wenn Ihr Administrator die Bezeichnung konfiguriert hat, um Schutz zu bieten. Alternativ können Sie auch eigene Schutzeinstellungen angeben. 

Einige Dateien werden automatisch von der Klassifizierung und der Schutzfunktion ausgeschlossen, da die Ausführung Ihres PCs möglicherweise beendet wird, wenn Sie sie ändern. Obwohl Sie diese Dateien auswählen können, werden sie wie ein ausgeschlossener Ordner oder eine ausgeschlossene Datei übersprungen. Beispiele umfassen ausführbare Dateien und Ihren Windows-Ordner.

Das Administratorhandbuch enthält eine vollständige Liste der unterstützten Dateitypen sowie die Dateien und Ordner, die automatisch ausgeschlossen werden: [Vom Azure Information Protection-Client unterstützte Dateitypen](client-admin-guide-file-types.md).


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>So klassifizieren und schützen Sie eine Datei mithilfe des Datei-Explorer

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**. Beispiel:
    
    ![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

2. Verwenden Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Bezeichnungen wie in einer Office-Anwendung, wodurch die Klassifizierung und der Schutz gemäß der Definition Ihres Administrators festgelegt werden. 

   - Wenn keine der Bezeichnungen ausgewählt werden kann (Bezeichnungen sind abgeblendet): Die ausgewählte Datei unterstützt die Klassifizierung nicht, aber Sie können sie mit benutzerdefinierten Berechtigungen (Schritt 3) schützen. Beispiel:

     ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“** verfügbar](../media/info-protect-dialog-labels-dimmed.png)
    
   - Wenn keine Bezeichnung, aber eine Option für **unternehmensdefinierten Schutz** in diesem Dialogfeld angezeigt wird: Der Client wird im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt. Wählen Sie eine vom Administrator konfigurierte Vorlage zum Anwenden von Schutz oder die Option **Benutzerdefinierte Berechtigungen** aus, um eigene Schutzeinstellungen anzugeben, und wechseln Sie dann zu Schritt 4.
    
     ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“**](../media/info-protect-dialog-labels-protection-only.png)
    
3. Sie können, sofern es von Ihrem Administrator erlaubt ist, eigene Schutzeinstellungen angeben, anstatt die Schutzeinstellungen zu verwenden, die der Administrator für Ihre Bezeichnung konfiguriert hat. Wählen Sie zu diesem Zweck die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen) aus.
    
    Wenn Ihnen die Option **Mit benutzerdefinierten Berechtigungen schützen** nicht angezeigt wird, erlaubt Ihr Administrator Ihnen die Verwendung dieser Option nicht.
    
    Die von Ihnen angegebenen benutzerdefinierten Berechtigungen sind keine Ergänzung der vom Administrator für Ihre ausgewählte Bezeichnung definierten Schutzeinstellungen, sondern ersetzen diese.  

4. Wenn Sie die Option der benutzerdefinierten Berechtigungen ausgewählt haben, geben Sie jetzt Folgendes an:

   - **Berechtigungen auswählen**: Wählen Sie die Zugriffsebene aus, die die Benutzer erhalten sollen, wenn Sie die ausgewählte(n) Datei(en) schützen.
    
   - **Benutzer, Gruppen oder Organisationen auswählen**: Geben Sie die Personen an, die die Berechtigungen erhalten sollen, die Sie für Ihre Datei(en) ausgewählt haben. Geben Sie für jeden Benutzer in dieser Organisation die vollständige E-Mail-Adresse, eine Gruppen-E-Mail-Adresse oder einen Domänennamen der Organisation ein. 
    
     Alternativ dazu können Sie das Adressbuchsymbol verwenden, um Benutzer oder Gruppen aus dem Outlook-Adressbuch auszuwählen.
        
   - **Ablaufzugriff**: Wählen Sie diese Option nur für zeitkritische Dateien aus, damit die von Ihnen angegebenen Personen die ausgewählte(n) Datei(en) nach einem von Ihnen festgelegten Datum nicht mehr öffnen können. Sie können weiterhin die ursprüngliche Datei öffnen, aber nach Mitternacht (Ihre aktuelle Zeitzone) an dem von Ihnen festgelegten Tag können die betreffenden Personen die Datei nicht mehr öffnen.
    
     Hinweis: Wenn diese Einstellung zuvor mit benutzerdefinierten Berechtigungen über eine Office 2010-App konfiguriert wurde, wird das angegebene Ablaufdatum zwar nicht in diesem Dialogfeld angezeigt, ist jedoch nach wie vor festgelegt. Dieses Anzeigeproblem tritt lediglich auf, wenn das Ablaufdatum in Office 2010 konfiguriert wurde.

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.

Die ausgewählte(n) Datei(en) werden jetzt gemäß Ihrer Auswahl klassifiziert und geschützt. In einigen Fällen (wenn die Dateinamenerweiterung durch Hinzufügen des Schutzes geändert wird) wird die ursprüngliche Datei im Datei-Explorer durch eine neue Datei mit dem Schlosssymbol für Azure Information Protection ersetzt. Beispiel:

![Geschützte Datei mit Schlosssymbol für Azure Information Protection](../media/Pfile.png)

Wenn Sie Ihre Meinung hinsichtlich Klassifizierung und Schutz ändern oder Ihre Einstellungen später ändern müssen, wiederholen Sie diesen Prozess mit den neuen Einstellungen.

Die Klassifizierung und der Schutz, die Sie angegeben haben, bleiben der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. Wenn Sie die Datei geschützt haben, können Sie verfolgen, wie sie von Personen verwendet wird und den Zugriff ggf. widerrufen. Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer geschützten Dokumente bei Verwendung von Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    
Konfigurationsanweisungen zum Aktivieren der Richtlinieneinstellung **Make the custom permissions option available to users** (Die Option der benutzerdefinierten Berechtigungen Benutzern zur Verfügung stellen) finden Sie unter [Konfigurieren der Richtlinieneinstellungen für Azure Information Protection](../configure-policy-settings.md).

Sonstige Konfigurationsanweisungen: [Konfigurieren der Azure Information Protection-Richtlinie](../configure-policy.md).

