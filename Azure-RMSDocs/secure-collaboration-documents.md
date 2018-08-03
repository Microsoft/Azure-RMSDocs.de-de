---
title: Sicheres Zusammenarbeiten an Dokumenten mithilfe von Azure Information Protection
description: End-to-End-Workflow für das Zusammenarbeiten an Dokumenten, die mit Azure Information Protection geschützt werden
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/21/2018
ms.topic: get-started-article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4895c429-959f-47c7-9007-b8f032f6df6f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: e8f2facdeda749987bb1fffae84a3f1bf033e1ad
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39474717"
---
# <a name="secure-document-collaboration-by-using-azure-information-protection"></a>Sicheres Zusammenarbeiten an Dokumenten mithilfe von Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Mit Azure Information Protection können Sie Ihre Dokumente schützen, ohne Einbußen bei der Zusammenarbeit für autorisierte Benutzer hinnehmen zu müssen. Die meisten Dokumente, die ein Benutzer erstellt und dann für andere zur Ansicht und Bearbeitung freigibt, sind Office-Dokumente aus Word, Excel und PowerPoint. Diese Dokumente unterstützen nativen Schutz. Das bedeutet, dass zusätzlich zur Autorisierung und Verschlüsselung auch eingeschränkte Berechtigungen für eine präzisere Kontrolle unterstützt werden. 

Diese Berechtigungen heißten „Nutzungsrechte“ und umfassen Berechtigungen wie „anzeigen“, „bearbeiten“ und „drucken“. Nutzungsrechte lassen sich beim Schützen eines Dokuments individuell definieren. Alternativ können Sie eine Gruppe von Nutzungsrechten definieren, sogenannte Berechtigungsebenen. Berechtigungsebenen erleichtern die Auswahl von Nutzungsrechten, die in der Regel zusammen verwendet werden, z.B. „Prüfer“ und „Mitautor“. Weitere Informationen zu den Nutzungsberechtigungen und Berechtigungsebenen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](./deploy-use/configure-usage-rights.md).

Wenn Sie diese Berechtigungen konfigurieren, können Sie angeben, für welche Benutzer sie gedacht sind:

- **Für Benutzer in Ihrer oder einer anderen Organisation, die Azure Active Directory verwendet:** Sie können Azure AD-Benutzerkonten, Azure AD-Gruppen oder alle Benutzer in der Organisation angeben. 

- **Für Benutzer ohne Azure Active Directory-Konto:** Geben Sie eine E-Mail-Adresse an, die mit einem Microsoft-Konto verwendet werden wird. Dieses Konto kann bereits vorhanden sein. Alternativ können es Benutzer dann erstellen, wenn sie das geschützte Dokument öffnen. 
    
    Um Dokumente mit einem Microsoft-Konto zu öffnen, müssen Benutzer Office 2016-Klick-und-Los verwenden. In anderen Office-Editionen und -Versionen wird das Öffnen von mit Office geschützten Dokumenten mit einem Microsoft-Konto noch nicht unterstützt.

- **Für alle authentifizierten Benutzer**: Diese Option ist geeignet, wenn Sie nicht steuern müssen, wer auf das geschützte Dokument zugreift, solange der Benutzer authentifiziert werden kann. Die Authentifizierung kann durch Azure AD, durch die Verwendung eines Microsoft-Kontos oder sogar durch einen Verbundanbieter sozialer Netzwerke oder eine Einmalkennung erfolgen, wenn der Inhalt durch die neuen Funktionen der Office 365-Nachrichtenverschlüsselung geschützt ist. 

Als Administrator können Sie eine Azure Information Protection-Bezeichnung konfigurieren, die auf die Berechtigungen und auf die autorisierten Benutzer angewendet werden soll. Diese Konfiguration erleichtert es Benutzern und anderen Administratoren, die richtigen Schutzeinstellungen anzuwenden, denn sie können einfach die Bezeichnung nutzen, ohne Details angeben zu müssen. In den folgenden Abschnitten finden Sie eine exemplarische Vorgehensweise, die eine sichere Zusammenarbeit mit internen und externen Benutzern unterstützt. Damit können Sie ein Dokument schützen.


## <a name="example-configuration-for-a-label-to-apply-protection-to-support-internal-and-external-collaboration"></a>Beispielkonfiguration für eine Schutzbezeichnung, mit der die interne und externe Zusammenarbeit unterstützt wird

In diesem Beispiel werden Sie durch die Konfiguration einer vorhandenen Bezeichnung geführt, mit der Schutz angewendet wird, damit Benutzer in Ihrer Organisation gemeinsam mit Benutzern oder Gruppen aus einer anderen Organisation, in der Office 365 oder Azure AD genutzt wird, und mit Benutzern, die kein Azure AD-Konto haben und stattdessen ihre Gmail-Adresse verwenden, an Dokumenten arbeiten können.

Da das Szenario den Zugriff auf bestimmte Personen einschränkt, enthält es keine Einstellungen für authentifizierte Benutzer. Ein Beispiel, wie Sie eine Bezeichnung mit dieser Einstellung konfigurieren können, finden Sie in [Beispiel 5: Bezeichnung, die Inhalte verschlüsselt, aber nicht einschränkt, wer darauf zugreifen kann](./deploy-use/configure-policy-protection.md#example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it).  

1. Wählen Sie die Bezeichnung aus, die bereits in der globalen oder einer bereichsbezogenen Richtlinie enthalten ist. Stellen Sie sicher, dass auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Gehen Sie auf dem Blatt **Berechtigungen hinzufügen** wie folgt vor: 
    
    - Für die interne Gruppe: Klicken Sie auf **Browse directory** (Verzeichnis durchsuchen), um die Gruppe auszuwählen, für die die E-Mail-Funktion aktiviert sein muss.
    
    - Für alle Benutzer in der ersten externen Organisation: Klicken Sie auf **Geben Sie Details ein**, und geben Sie im Mandanten der Organisation den Namen einer Domain ein. Beispiel: fabrikam.com.
    
    - Für die Gruppe in der zweiten externen Organisation: Geben Sie auf der Registerkarte **Details eingeben** die E-Mail-Adresse der Gruppe im Mandanten der Organisation ein. Beispiel: sales@contoso.com.
    
    - Für den Benutzer ohne Azure AD-Konto: Geben Sie auf der Registerkarte **Details eingeben** die E-Mail-Adresse des Benutzers ein. Beispiel: bengi.turan@gmail.com. 

4. Wenn Sie allen Benutzern dieselben Berechtigungen erteilen möchten: Wählen Sie für **Berechtigungen aus Voreinstellung auswählen** die Berechtigung **Mitbesitzer**, **Mitautor**, **Prüfer** oder **Benutzerdefiniert** aus.
    
    Die konfigurierten Berechtigungen können beispielsweise wie folgt aussehen:
        
    ![Konfigurieren von Berechtigungen für eine sichere Zusammenarbeit](./media/collaboration-permissions.png)

5. Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** auf **OK**.

6. Klicken Sie auf auf dem Blatt **Schutz** auf **OK**.

7. Wählen Sie auf dem Blatt **Bezeichnung** die Option **Speichern** aus. 

## <a name="applying-the-label-that-supports-secure-collaboration"></a>Anwenden der Bezeichnung, die die sichere Zusammenarbeit unterstützt

Da die Bezeichnung nun konfiguriert ist, kann sie auf verschiedene Weise auf Dokumente angewendet werden. Dazu zählen z.B. folgende:

|Verschiedene Anwendungsmöglichkeiten der Bezeichnung|Weitere Informationen|
|---------------|----------|
|Der Benutzer wählt die Bezeichnung bei der Erstellung des Dokuments manuell in der Office-Anwendung aus.|Benutzer wählen die Bezeichnung im Office-Menüband über die Schaltfläche **Schützen** oder über die Azure Information Protection-Leiste aus.|
|Benutzer werden beim Speichern eines neuen Dokuments dazu aufgefordert, eine Bezeichnung auszuwählen.|Sie haben die Azure Information Protection-[Richtlinieneinstellung](./deploy-use/configure-policy-settings.md) namens **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen) konfiguriert.|
|Ein Benutzer gibt das Dokument per E-Mail frei und wählt die Bezeichnung manuell in Outlook aus.|Benutzer wählen die Bezeichnung im Office-Menüband über die Schaltfläche **Schützen** oder über die Azure Information Protection-Leiste aus, und das angefügte Dokument wird automatisch mit den gleichen Einstellungen geschützt.|
|Ein Administrator wendet die Bezeichnung mit PowerShell auf das Dokument an.|Mithilfe des Cmdlets [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) lässt sich die Bezeichnung auf ein bestimmtes Dokument oder auf alle Dokumente in einem Ordner anwenden.|
|Sie haben die Bezeichnung so konfiguriert, dass die automatische Klassifizierung jetzt mit dem Azure Information Protection-Scanner oder mit PowerShell angewendet werden kann.|Weitere Informationen finden Sie unter [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](./deploy-use/configure-policy-classification.md).|

Um diese exemplarische Vorgehensweise manuell abzuschließen, wenden Sie die Bezeichnung an, während Sie das Dokument in der Office-Anwendung erstellen: 

1. Falls Sie die Office-Anwendung bereits auf einem Clientcomputer geöffnet haben, schließen Sie sie, und öffnen Sie sie erneut, um die neuesten Richtlinienänderungen abzurufen, die die neu konfigurierte Bezeichnung enthalten. 

2. Wenden Sie die Bezeichnung auf ein Dokument an, und speichern Sie es.

Geben Sie das geschützte Dokument frei, indem Sie es an eine E-Mail anfügen, und senden Sie es den für die Bearbeitung autorisierten Personen.

## <a name="opening-and-editing-the-protected-document"></a>Öffnen und Bearbeiten des geschützten Dokuments

Wenn von Ihnen autorisierte Benutzer das Dokument zum Bearbeiten öffnen, wird ein Banner angezeigt, das auf eingeschränkte Berechtigungen hinweist. Beispiel:

![Beispielbanner zu Azure Information Protection-Berechtigungen](./media/example-restricted-access-banner.png)

Mit einem Klick auf die Schaltfläche **View Permission** (Berechtigung anzeigen) können diese die eigenen Berechtigungen aufrufen. Im folgenden Beispiel können Benutzer das Dokument anzeigen und bearbeiten:

![Beispieldialogfeld zu Azure Information Protection-Berechtigungen](./media/example-permisisons-popup.png)

Hinweis: Wenn das Dokument von externen Benutzern geöffnet wird, die ebenfalls Azure Information Protection verwenden, zeigt die Office-Anwendung Ihre Klassifizierungsbezeichnung für das Dokument nicht an, obwohl alle optischen Kennzeichnungen aus der Bezeichnung erhalten bleiben. Stattdessen können externe Benutzer ihre eigene Bezeichnung entsprechend der Klassifizierungstaxonomie ihrer Organisation anwenden. Wenn diese externen Benutzer dann das bearbeitete Dokument an Sie zurücksenden, zeigt Office beim erneuten Öffnen des Dokuments Ihre ursprüngliche Klassifizierungsbezeichnung an.

Vor dem Öffnen des geschützten Dokuments wird einer der folgenden Authentifizierungsflows durchlaufen:

- Benutzer, die über ein Azure AD-Konto verfügen, authentifizieren sich über ihre Azure AD-Anmeldeinformationen bei Azure AD. Daraufhin wird das Dokument geöffnet. 

- Benutzer, die kein Azure AD-Konto besitzen, sehen die Seite **Konten**, wenn sie nicht mit einem Konto bei Office angemeldet sind, das zum Öffnen des Dokuments berechtigt ist. 
    
   Klicken Sie auf der Seite **Konten** auf **Konto hinzufügen**:
   
    ![Microsoft-Konto hinzufügen, um ein geschütztes Dokument zu öffnen](./media/add-account-msa.png)

   Klicken Sie auf der Seite **Anmelden** auf **Jetzt erstellen**, und befolgen Sie die Anweisungen zum Erstellen eines neuen Microsoft-Kontos mit der E-Mail-Adresse, mit der die Berechtigungen erteilt wurden:
    
    ![Microsoft-Konto erstellen, um ein geschütztes Dokument zu öffnen](./media/create-account-msa.png)
    
    Wenn das neue Microsoft-Konto erstellt ist, wird das lokale Konto auf das neue Microsoft-Konto umgestellt, und der Benutzer kann das Dokument öffnen.


### <a name="supported-scenarios-for-opening-protected-documents"></a>Unterstützte Szenarios für das Öffnen geschützter Dokumente

In der folgenden Tabelle werden die verschiedenen Authentifizierungsmethoden zusammengefasst, die für das Anzeigen und Bearbeiten geschützter Dokumente unterstützt werden.

Zusätzlich wird die Dokumentanzeige durch folgende Szenarien unterstützt:

- Der Azure Information Protection-Viewer für Windows sowie für iOS und Android kann Dateien als Vorschau öffnen, indem er ein Microsoft-Konto verwendet. 

- In einem Browser können geschützte Anlagen geöffnet werden, wenn Anbieter sozialer Netzwerke und Einmalkennungen für die Authentifizierung bei Exchange Online und den neuen Funktionen der Office 365-Nachrichtenverschlüsselung verwendet werden. 

|Plattformen zum Anzeigen und Bearbeiten von Dokumenten: <br />Word, Excel, PowerPoint|Authentifizierungsmethode:<br />Azure AD|Authentifizierungsmethode:<br />Microsoft-Konto|
|---------------|----------|-----------|-----------|
|Windows|Ja [[1]](#footnote-1)|Ja [[2]](#footnote-2)|
|iOS|Ja [[1]](#footnote-1)|Nein|
|Android|Ja [[1]](#footnote-1)|Nein|
|MacOS|Ja [[1]](#footnote-1)|Nein|

###### <a name="footnote-1"></a>Fußnote 1
Unterstützt die Benutzerkonten, Gruppen mit aktivierter E-Mail-Funktion, alle Mitglieder. Benutzerkonten und Gruppen mit aktivierter E-Mail-Funktion schließen Gastkonten mit ein. Mitglieder beinhalten keine Gastkonten.

###### <a name="footnote-2"></a>Fußnote 2
Wird derzeit nur von Office 2016-Klick-und-Los unterstützt.




## <a name="next-steps"></a>Nächste Schritte

Weitere Informationen zu Schutzbezeichnungen für übliche Szenarios finden Sie unter [Beispielkonfigurationen](./deploy-use/configure-policy-protection.md#example-configurations). Dieser Artikel enthält außerdem ausführliche Informationen zu den Schutzeinstellungen.

Weitere Informationen zu den anderen Optionen und Einstellungen, die Sie für Ihre Bezeichnung konfigurieren können, finden Sie unter [Konfigurieren der Azure Information Protection-Richtlinie](./deploy-use/configure-policy.md). 

Die Bezeichnung, die in diesem Artikel konfiguriert wurde, erstellt auch eine Schutzvorlage mit demselben Namen. Falls einige Ihrer Anwendungen und Dienste eine Integration mit Vorlagen aus Azure Information Protection unterstützen, können sie diese Vorlage anwenden. Beispiel: DLP-Lösungen und E-Mail-Flow-Regeln. Outlook im Web zeigt Schutzvorlagen aus der globalen Azure Information Protection-Richtlinie automatisch an. 




