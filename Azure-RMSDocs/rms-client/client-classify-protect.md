---
title: "Klassifizieren und Schützen mithilfe von Azure Informationen Protection"
description: "Anweisungen zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 75268245-6f14-4218-b904-202f63fb3ce6
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 3db62d81976267155764abf7e45598628259710d
ms.lasthandoff: 02/24/2017


---

# <a name="classify-and-protect-a-file-or-email-by-using-azure-information-protection"></a>Klassifizieren und Schützen einer Datei oder E-Mail mithilfe von Azure Informationen Protection

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1*

Die einfachste Möglichkeit zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails bietet sich, wenn Sie sie in Ihren Office-Desktopanwendungen erstellen oder bearbeiten: **Word**, **Excel**, **PowerPoint**, **Outlook**. 

Sie können Dateien jedoch auch über den **Datei-Explorer** klassifizieren und schützen, der zusätzliche Dateitypen unterstützt und eine bequeme Methode zum gleichzeitigen Klassifizieren und Schützen mehrerer Dateien darstellt. Diese Methode unterstützt den Schutz von Office-Dokumenten, PDF-Dateien, Text- und Bilddateien sowie einer Vielzahl anderer Dateien. 

### <a name="safely-share-a-file-with-people-outside-your-organization"></a>Sichere Freigabe einer Datei für Personen außerhalb Ihrer Organisation

Geschützte Dateien können für andere Personen sicher freigegeben werden. Sie können die Datei z. B. an eine E-Mail anhängen oder eine Einladung von Ihrer SharePoint-Website senden.

Wenn Sie Dateien regelmäßig für Personen außerhalb Ihrer Organisation freigeben, kann Ihr Administrator eine Bezeichnung für Sie konfigurieren, mit der der Schutz so festgelegt wird, dass die Dateien von diesen Personen gelesen werden können. Alternativ können Sie den [Datei-Explorer zum Festlegen von benutzerdefinierten Berechtigungen](#using-file-explorer-to-classify-and-protect-files) für eine Datei verwenden, bevor Sie sie freigeben. 

Wenn Sie Ihre eigenen benutzerdefinierten Berechtigungen festlegen und die Datei bereits für die interne Verwendung geschützt ist, erstellen Sie zunächst eine Kopie der Datei. Verwenden Sie diese Kopie, um die benutzerdefinierten Berechtigungen festzulegen.  

Wenn die Datei mit Ihren benutzerdefinierten Berechtigungen geschützt ist, verwenden Sie den üblichen Freigabemechanismus zum Freigeben der Datei. Ist dies das erste Mal, dass diese Personen eine geschützte Datei per Freigabe erhalten, benötigen sie möglicherweise entsprechende Anweisungen zum Anzeigen der Datei. Für diese Personen können Sie die folgende Nachricht kopieren und einfügen: **Diese Datei ist mit Microsoft Azure Information Protection geschützt. Informationen zur erstmaligen Verwendung finden Sie in diesen [Anweisungen](https://aka.ms/rms-signup).**


## <a name="using-office-apps-to-classify-and-protect-your-documents-and-emails"></a>Verwenden von Office-Apps zum Klassifizieren und Schützen Ihrer Dokumente und E-Mails

Verwenden Sie die Azure Information Protection-Leiste, und wählen Sie eine der Bezeichnungen aus, die für Sie konfiguriert wurde. 

Die folgende Abbildung zeigt beispielsweise, dass das Dokument noch keine Bezeichnung erhalten hat, da für **Vertraulichkeit** die Option **Nicht festgelegt** angezeigt wird. Klicken Sie zum Festlegen einer Bezeichnung wie „Intern“ auf **Intern**. Wenn Sie nicht sicher sind, welche Bezeichnung auf das aktuelle Dokument oder die E-Mail angewendet werden soll, verwenden Sie die QuickInfos für Bezeichnungen, um weitere Informationen zu den einzelnen Bezeichnungen und ihrer Anwendung zu erhalten.

![Beispiel zur Azure Information Protection-Leiste](../media/info-protect-bar-not-set-callout.png)

Wenn auf das Dokument bereits eine Bezeichnung angewendet wurde und Sie diese ändern möchten, können Sie eine andere Bezeichnung auswählen. Wenn die Bezeichnungen nicht auf der Leiste angezeigt werden, klicken Sie zunächst neben dem aktuellen Bezeichnungswert auf das Symbol **Edit label** (Bezeichnung bearbeiten).

Neben der manuellen Auswahl von Bezeichnungen können Bezeichnungen auch auf die folgende Weise angewendet werden:

- Ihr Administrator konfiguriert eine Standardbezeichnung, die Sie beibehalten oder ändern können.

- Ihr Administrator konfiguriert empfohlene Aufforderungen zum Auswählen einer bestimmten Bezeichnung, wenn vertrauliche Daten erkannt wurden. Sie können die Empfehlung übernehmen (und die Bezeichnung anwenden) oder zurückweisen (empfohlene Bezeichnung wird nicht angewendet).

### <a name="exceptions-for-the-azure-information-protection-bar"></a>Ausnahmen für die Azure Information Protection-Leiste 

##### <a name="dont-see-this-information-protection-bar-in-your-office-apps"></a>Wenn diese Information Protection-Leiste in Ihren Office-Apps nicht angezeigt wird:

- Möglicherweise ist der Azure Information Protection-Client nicht [installiert](install-client-app.md) oder der Client wird im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt.
 
##### <a name="is-the-label-that-you-expect-to-see-not-displayed-on-the-bar"></a>Wenn die erwartete Bezeichnung auf der Leiste nicht angezeigt wird: 

- Wenn Ihr Administrator kürzlich eine neue Bezeichnung für Sie konfiguriert hat, schließen Sie alle Instanzen der Office-App und öffnen Sie sie anschließend erneut. Durch diese Aktion werden Änderungen an den Bezeichnungen gesucht.

- Wenn die fehlende Bezeichnung den Schutz anwendet, verwenden Sie möglicherweise eine Version von Office, die das Anwenden des Rights Management-Schutzes nicht unterstützt. Klicken Sie zum Überprüfen auf **Protect (Schützen)** > **Help and Feedback (Hilfe und Feedback)** und prüfen Sie, ob sich im Abschnitt für den **Clientstatus** eine Nachricht mit der Information befindet, dass **dieser Client nicht für Office Professional Plus lizenziert ist**. 

- Die Bezeichnung befindet sich möglicherweise in einer bereichsbezogenen Richtlinie, die Ihr Konto nicht umfasst. Wenden Sie sich an den Helpdesk oder Ihren Administrator.

### <a name="keyboard-shortcuts-for-the-azure-information-protection-bar"></a>Tastenkombinationen für die Azure Information Protection-Leiste

Für den Zugriff auf die Azure Information Protection-Leiste über Tastenkürzel können Sie die folgenden Tastenkombinationen nutzen:

- Drücken Sie **STRG** + **UMSCHALT** + **~** 

Verwenden Sie dann die TAB-TASTE, um die Bezeichnungen und andere Steuerelemente auf der Leiste auszuwählen (die Symbole **Hide Labels ** (Bezeichnungen ausblenden) und **Delete Label** (Bezeichnung löschen)), und drücken Sie die EINGABETASTE, um sie auszuwählen.

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

    - Wenn keine der Bezeichnungen ausgewählt werden kann (abgeblendet): Die ausgewählte Datei unterstützt die Klassifizierung nicht, aber Sie können sie mit benutzerdefinierten Berechtigungen (Schritt 3) schützen. Beispiel:

    ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“** verfügbar](../media/info-protect-dialog-labels-dimmed.png)
    
    - Wenn keine Bezeichnung, aber eine Option für **unternehmensdefinierten Schutz** in diesem Dialogfeld angezeigt wird: Der Client wird im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt. Wählen Sie eine vom Administrator konfigurierte Vorlage zum Anwenden von Schutz oder die Option **Benutzerdefinierte Berechtigungen** aus, um eigene Schutzeinstellungen anzugeben, und wechseln Sie dann zu Schritt 4.
    
    ![Keine Bezeichnungen im Dialogfeld „Klassifizieren und schützen – Azure Information Protection“**](../media/info-protect-dialog-labels-protection-only.png)
    
3. Wenn Sie lieber eigene Schutzeinstellungen angeben möchten, anstatt die Schutzeinstellungen zu verwenden, die der Administrator für Ihre Bezeichnung konfiguriert hat, wählen Sie **Mit benutzerdefinierten Berechtigungen schützen** aus.
    
    Die von Ihnen angegebenen benutzerdefinierten Berechtigungen sind keine Ergänzung der vom Administrator für Ihre ausgewählte Bezeichnung definierten Schutzeinstellungen, sondern ersetzen diese.  

4. Wenn Sie die Option der benutzerdefinierten Berechtigungen ausgewählt haben, geben Sie jetzt Folgendes an:

    - **Berechtigungen auswählen**: Wählen Sie die Zugriffsebene, die die Benutzer erhalten sollen, wenn Sie die ausgewählte(n) Datei(en) schützen.
    
    - **Benutzer auswählen**: Geben Sie die Personen an, die die Berechtigungen erhalten sollen, die Sie für Ihre Datei(en) ausgewählt haben. Für Benutzer und Gruppen in Ihrer Organisation können Sie das Adressbuch durchsuchen, und diese dann auswählen. Für Personen in einer anderen Organisation müssen Sie die vollständige E-Mail-Adresse angeben. Stellen Sie sicher, dass Sie eine geschäftliche E-Mail-Adresse verwenden, da persönliche E-Mail-Adressen derzeit nicht unterstützt werden.
        
    - **Ablaufzugriff**: Wählen Sie diese Option nur für zeitempfindliche Dateien aus, damit die von Ihnen angegebenen Personen die ausgewählte(n) Datei(en) nach einem von Ihnen angegebenen Datum nicht mehr öffnen können. Sie können weiterhin die ursprüngliche Datei öffnen, aber nach Mitternacht (aktuelle Zeitzone) können die Personen an dem von Ihnen angegebenen Tag die Datei nicht mehr öffnen.

5. Klicken Sie auf **Übernehmen** und warten Sie auf die Nachricht **Work finished** (Vorgang abgeschlossen), um die Ergebnisse zu sehen. Klicken Sie anschließend auf **Schließen**.

Die ausgewählte(n) Datei(en) werden jetzt gemäß Ihrer Auswahl klassifiziert und geschützt. In einigen Fällen (wenn die Dateinamenerweiterung durch Hinzufügen des Schutzes geändert wird) wird die ursprüngliche Datei im Datei-Explorer durch eine neue Datei mit dem Schlosssymbol für Azure Information Protection ersetzt. Beispiel:

![Geschützte Datei mit Schlosssymbol für Azure Information Protection](../media/Pfile.png)

Wenn Sie Ihre Meinung hinsichtlich Klassifizierung und Schutz ändern oder Ihre Einstellungen später ändern müssen, wiederholen Sie diesen Prozess mit den neuen Einstellungen.

Die Klassifizierung und der Schutz, die Sie angegeben haben, bleiben der Datei zugeordnet, auch wenn Sie die Datei per E-Mail senden oder an einem anderen Ort speichern. Wenn Sie die Datei geschützt haben, können Sie verfolgen, wie sie von Personen verwendet wird und den Zugriff ggf. widerrufen. Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer geschützten Dokumente bei Verwendung von Azure Information Protection](client-track-revoke.md). 


## <a name="other-instructions"></a>Sonstige Anweisungen
Weitere Anweisungen zur Vorgehensweise finden Sie im Azure Information Protection-Benutzerhandbuch:

-   [Was möchten Sie tun?](client-user-guide.md#what-do-you-want-to-do)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

