---
title: Klassifizieren von & Protect-Azure Information Protection Unified-Bezeichnungs Client
description: Anleitungen zur Klassifizierung und zum Schutz Ihrer Dokumente und e-Mails bei Verwendung des Azure Information Protection Unified Bezeichnung-Clients für Windows.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 08/04/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: v2client
ms.suite: ems
ms.custom: user
ms.openlocfilehash: fc46174efcbcda170a060c49ef6dbb069f6b9770
ms.sourcegitcommit: dec5df81b569283a72f0a983d3f53b82cbbc562c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87802095"
---
# <a name="user-guide-classify-and-protect-with-the-azure-information-protection-unified-labeling-client"></a>Benutzerhandbuch: klassifizieren und schützen mit dem Azure Information Protection Unified-Beschriftungs Client

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8*
>
> **Kunden mit erweitertem Microsoft-Support für Windows 7 und Office 2010 können auch Azure Information Protection Unterstützung für diese Versionen erhalten. Wenden Sie sich an Ihren Support, um ausführliche Informationen zu erhalten.*
>
> *Anweisungen für: [Azure Information Protection Unified-Bezeichnungs Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

> [!NOTE]
> Mithilfe dieser Anleitung können Sie Ihre Dokumente und E-Mails klassifizieren und schützen. Wenn Sie Ihre Dokumente und E-Mails nur klassifizieren und nicht schützen müssen, lesen Sie die [Anleitung zum Klassifizieren](clientv2-classify.md). Wenn Sie nicht sicher sind, welche Anleitung Sie verwenden sollen, wenden Sie sich an Ihren Systemadministrator oder den Helpdesk.

Die einfachste Möglichkeit zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails bietet sich, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können jedoch auch Dateien mithilfe des **Datei-Explorers** klassifizieren und schützen. Diese Methode unterstützt weitere Dateitypen und ist ein bequemer Weg zum Klassifizieren und Schützen mehrerer Dateien gleichzeitig. Diese Methode unterstützt den Schutz von Office-Dokumenten, PDF-Dateien, Text- und Bilddateien sowie einer Vielzahl anderer Dateien. 

Wenn Ihre Bezeichnung den Schutz für ein Dokument anwendet, ist das geschützte Dokument möglicherweise nicht für die Speicherung auf SharePoint oder onedrive geeignet. Überprüfen Sie, ob der Administrator [Vertraulichkeits Bezeichnungen für Office-Dateien in SharePoint und onedrive aktiviert](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files)hat.

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Sichere Freigabe einer Datei für Personen außerhalb Ihrer Organisation

Geschützte Dateien können für andere Personen sicher freigegeben werden. Sie hängen z.B. ein geschütztes Dokument an eine E-Mail an.

Bevor Sie Dateien mit Personen außerhalb Ihrer Organisation teilen, wenden Sie sich an den Helpdesk oder Ihren Administrator, um herauszufinden, wie Dateien für externe Benutzer geschützt werden.

Wenn Ihre Organisation z.B. regelmäßig mit Personen einer anderen Organisation kommuniziert, hat Ihr Administrator womöglich Bezeichnungen konfiguriert, die Schutz in einem Umfang festlegen, damit diese Personen geschützte Dokumente lesen und verwenden können. Wählen Sie anschließend diese Bezeichnungen aus, um die Dokumente, die geteilt werden sollen, zu klassifizieren und zu schützen.

Wenn für die externen Benutzer [B2B-Konten (Business-to-Business](/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) ) erstellt wurden, können Sie alternativ den Datei-Explorer verwenden, [um benutzerdefinierte Berechtigungen](#using-file-explorer-to-classify-and-protect-files) für ein Dokument festzulegen, bevor Sie es freigeben. Wenn Sie Ihre eigenen benutzerdefinierten Berechtigungen festlegen und das Dokument bereits für die interne Verwendung geschützt ist, erstellen Sie zunächst eine Kopie der Datei, um die ursprünglichen Berechtigungen beizubehalten. Verwenden Sie dann die Kopie, um die benutzerdefinierten Berechtigungen festzulegen.


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails

Wählen Sie auf der Registerkarte **Startseite** die **Vertraulichkeits** Schaltfläche im Menüband aus, und wählen Sie dann eine der Bezeichnungen aus, die für Sie konfiguriert wurde. Beispiel:

![Beispiel für sensible Schaltfläche](../media/sensitivity-not-set-callout.png)

Wenn Sie in der **Vertraulichkeits** Schaltfläche **Leiste anzeigen** ausgewählt haben, können Sie auf der Azure Information Protection Leiste eine Bezeichnung auswählen. Beispiel:

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-barv2-not-set-callout.png)

Um eine Bezeichnung festzulegen, z. b. "**vertrauliche**  \  **alle Mitarbeiter**", wählen Sie **vertraulich** und dann **alle Mitarbeiter**aus. Wenn Sie nicht sicher sind, welche Bezeichnung auf das aktuelle Dokument oder die E-Mail angewendet werden soll, verwenden Sie die QuickInfos für Bezeichnungen, um weitere Informationen zu den einzelnen Bezeichnungen und ihrer Anwendung zu erhalten.

Wenn auf das Dokument bereits eine Bezeichnung angewendet wurde und Sie diese ändern möchten, können Sie eine andere Bezeichnung auswählen. Wenn Sie die Azure Information Protection Leiste angezeigt haben und die Bezeichnungen nicht auf der Leiste angezeigt werden, die Sie auswählen können, klicken Sie zuerst auf das Symbol " **Bezeichnung bearbeiten** " neben dem Wert der aktuellen Bezeichnung.

Neben der manuellen Auswahl von Bezeichnungen können Bezeichnungen auch auf die folgende Weise angewendet werden:

- Ihr Administrator konfiguriert eine Standardbezeichnung, die Sie beibehalten oder ändern können.

- Der Administrator hat Bezeichnungen so konfiguriert, dass Sie automatisch festgelegt werden, wenn sensible Informationen erkannt werden.

- Ihr Administrator hat Empfohlene Bezeichnungen konfiguriert, wenn vertrauliche Informationen erkannt werden, und Sie werden aufgefordert, die Empfehlung zu akzeptieren (und die Bezeichnung wird angewendet), oder Sie ablehnen (die empfohlene Bezeichnung wird nicht angewendet).

### <a name="exceptions-for-the-sensitivity-button"></a>Ausnahmen für die Vertraulichkeits Schaltfläche

##### <a name="dont-see-the-sensitivity-button-in-your-office-apps"></a>Wird die Vertraulichkeits Schaltfläche in Ihren Office-Apps nicht angezeigt?

- Möglicherweise ist der Azure Information Protection Unified Bezeichnung-Client nicht [installiert](install-unifiedlabelingclient-app.md).

- Wenn auf dem Menüband keine **Vertraulichkeits** Schaltfläche angezeigt wird, aber stattdessen die Schaltfläche **schützen** mit Bezeichnungen angezeigt wird, ist der Azure Information Protection Client (klassisch) installiert und nicht der Azure Information Protection Unified Label-Client. [Weitere Informationen](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed"></a>Wird die erwartete Bezeichnung nicht angezeigt? 

Mögliche Gründe:

- Wenn Ihr Administrator kürzlich eine neue Bezeichnung für Sie konfiguriert hat, schließen Sie alle Instanzen der Office-App und öffnen Sie sie anschließend erneut. Durch diese Aktion werden Änderungen an den Bezeichnungen gesucht.

- Wenn die fehlende Bezeichnung den Schutz anwendet, verwenden Sie möglicherweise eine Version von Office, die das Anwenden des Rights Management-Schutzes nicht unterstützt. Klicken Sie zum Überprüfen auf **Sensitivität**  >  **Hilfe und Feedback**. Prüfen Sie im Dialogfeld, ob sich im Abschnitt für den **Clientstatus** eine Nachricht mit der Information befindet, dass **dieser Client nicht für Office Professional Plus lizenziert ist**. 
    
    Sie benötigen Office Professional Plus nicht, wenn Sie über Office-Apps von Office 365 Business oder Microsoft 365 Business verfügen, wenn dem Benutzer eine Azure Rights Management-Lizenz (in Office 365 auch „Azure Information Protection“ genannt) zugewiesen wurde.

- Die Bezeichnung befindet sich möglicherweise in einer bereichsbezogenen Richtlinie, die Ihr Konto nicht umfasst. Wenden Sie sich an den Helpdesk oder Ihren Administrator.


### <a name="safely-sharing-by-email"></a>Sichere Freigabe per E-Mail

Wenn Sie ein Office-Dokument per E-Mail freigeben, können Sie dieses an eine geschützte E-Mail anfügen. Das Dokument wird in diesem Fall automatisch mit denselben Einschränkungen geschützt, die auf die E-Mail angewendet werden. 

Sie sollten das Dokument jedoch zuerst schützen und dann an die e-Mail anfügen. Sie sollten die E-Mail auch schützen, wenn diese vertrauliche Informationen enthält. Ein Vorteil beim Schützen des Dokuments, bevor Sie es an eine e-Mail anfügen, besteht darin, dass Sie unterschiedliche Berechtigungen auf das Dokument anwenden können als auf die e-Mail-Nachricht.

## <a name="using-file-explorer-to-classify-and-protect-files"></a>Verwenden des Datei-Explorer zum Klassifizieren und Schützen von Dateien

Wenn Sie den Datei-Explorer verwenden, können Sie eine einzelne Datei, mehrere Dateien oder einen Ordner schnell klassifizieren und schützen. 

Wenn Sie einen Ordner auswählen, werden alle Dateien und Unterordner in diesem Ordner automatisch für die Klassifizierungs- und Schutzoptionen ausgewählt, die Sie festlegen. Neue Dateien, die Sie in diesem Ordner oder Unterordner erstellen, werden jedoch nicht automatisch mit diesen Optionen konfiguriert.

Wenn Sie den Datei-Explorer zum Klassifizieren und Schützen Ihrer Dateien verwenden und eine oder mehrere der Bezeichnungen abgeblendet angezeigt werden, unterstützen die ausgewählten Dateien die Klassifizierung nicht. Für diese Dateien können Sie nur eine Bezeichnung auswählen, wenn Ihr Administrator die Bezeichnung konfiguriert hat, um Schutz zu bieten. Alternativ können Sie auch eigene Schutzeinstellungen angeben. 

Einige Dateien werden automatisch von der Klassifizierung und der Schutzfunktion ausgeschlossen, da die Ausführung Ihres PCs möglicherweise beendet wird, wenn Sie sie ändern. Obwohl Sie diese Dateien auswählen können, werden sie wie ein ausgeschlossener Ordner oder eine ausgeschlossene Datei übersprungen. Beispiele umfassen ausführbare Dateien und Ihren Windows-Ordner.

Das Administrator Handbuch enthält eine vollständige Liste der unterstützten Dateitypen sowie die Dateien und Ordner, die automatisch ausgeschlossen werden: [Dateitypen, die vom Azure Information Protection Unified-Bezeichnung-Client unterstützt](clientv2-admin-guide-file-types.md)werden.


### <a name="to-classify-and-protect-a-file-by-using-file-explorer"></a>So klassifizieren und schützen Sie eine Datei mithilfe des Datei-Explorer

1. Wählen Sie im Datei-Explorer die Datei, mehrere Dateien oder einen Ordner aus. Klicken Sie mit der rechten Maustaste auf **Klassifizieren und schützen**. Beispiel:
    
    ![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

2. Verwenden Sie im Dialogfeld **Klassifizieren und schützen – Azure Information Protection** die Bezeichnungen wie in einer Office-Anwendung, wodurch die Klassifizierung und der Schutz gemäß der Definition Ihres Administrators festgelegt werden. 

   - Wenn keine der Bezeichnungen ausgewählt werden kann (abgeblendet): Die ausgewählte Datei unterstützt die Klassifizierung nicht, aber Sie können sie mit benutzerdefinierten Berechtigungen (Schritt 3) schützen. Beispiel:

     ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“** verfügbar](../media/v2info-protect-dialog-labels-dimmed.png)

3. Sie können Ihre eigenen Schutzeinstellungen angeben, anstatt die Schutzeinstellungen zu verwenden, die Ihr Administrator möglicherweise in der gewählten Bezeichnung enthalten hat. Wählen Sie zu diesem Zweck die Option **Protect with custom permissions** (Mit benutzerdefinierten Berechtigungen schützen) aus.
    
    Die von Ihnen angegebenen benutzerdefinierten Berechtigungen sind keine Ergänzung der vom Administrator für Ihre ausgewählte Bezeichnung definierten Schutzeinstellungen, sondern ersetzen diese.  

4. Wenn Sie die Option der benutzerdefinierten Berechtigungen ausgewählt haben, geben Sie jetzt Folgendes an:

   - **Berechtigungen auswählen**: Wählen Sie die Zugriffsebene, die die Benutzer erhalten sollen, wenn Sie die ausgewählte(n) Datei(en) schützen.
    
   - **Benutzer, Gruppen oder Organisationen auswählen**: Geben Sie die Personen an, die die Berechtigungen erhalten sollen, die Sie für Ihre Datei(en) ausgewählt haben. Geben Sie für jeden Benutzer in dieser Organisation die vollständige E-Mail-Adresse, eine Gruppen-E-Mail-Adresse oder einen Domänennamen der Organisation ein. 
    
     Alternativ dazu können Sie das Adressbuchsymbol verwenden, um Benutzer oder Gruppen aus dem Outlook-Adressbuch auszuwählen.
        
    - **Ablauf des Zugriffs**: Wählen Sie diese Option nur für Zeit empfindliche Dateien aus, damit die Personen, die Sie angegeben haben, Ihre ausgewählten Dateien nach einem von Ihnen festgelegten Datum nicht mehr öffnen können. Sie können weiterhin die ursprüngliche Datei öffnen, aber nach Mitternacht (aktuelle Zeitzone) können die Personen an dem von Ihnen festgelegten Tag die Datei nicht mehr öffnen.
    
     Hinweis: Wenn diese Einstellung zuvor mit benutzerdefinierten Berechtigungen über eine Office 2010-App konfiguriert wurde, wird das angegebene Ablaufdatum zwar nicht in diesem Dialogfeld angezeigt, ist jedoch nach wie vor festgelegt. Dieses Anzeigeproblem tritt lediglich auf, wenn das Ablaufdatum in Office 2010 konfiguriert wurde.

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.

Die ausgewählte(n) Datei(en) werden jetzt gemäß Ihrer Auswahl klassifiziert und geschützt. In einigen Fällen (wenn die Dateinamenerweiterung durch Hinzufügen des Schutzes geändert wird) wird die ursprüngliche Datei im Datei-Explorer durch eine neue Datei mit dem Schlosssymbol für Azure Information Protection ersetzt. Beispiel:

![Geschützte Datei mit Schlosssymbol für Azure Information Protection](../media/Pfile.png)

Wenn Sie Ihre Meinung hinsichtlich Klassifizierung und Schutz ändern oder Ihre Einstellungen später ändern müssen, wiederholen Sie diesen Prozess mit den neuen Einstellungen.

Die Klassifizierung und der Schutz, die Sie angegeben haben, bleiben der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. 

## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anleitungen finden Sie im Benutzerhandbuch für Azure Information Protection Unified Bezeichnung-Client:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

## <a name="additional-information-for-administrators"></a>Weitere Informationen für Administratoren    

Weitere [Informationen finden Sie unter Informationen zu Sensitivität](/microsoft-365/compliance/sensitivity-labels).
