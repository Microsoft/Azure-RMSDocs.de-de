---
title: "Erstellen, Konfigurieren und Veröffentlichen einer benutzerdefinierten Vorlage | Azure RMS"
description: "Benutzerdefinierte Vorlagen erstellen und verwalten Sie im klassischen Azure-Portal. Sie können dies direkt im klassischen Azure-Portal durchführen, oder Sie können sich beim Office 365 Admin Center anmelden und die erweiterten Funktionen für Rights Management auswählen, über die Sie zum klassischen Azure-Portal weitergeleitet werden."
author: cabailey
manager: mbaldwin
ms.date: 07/15/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: d6e9aa0c-1694-4a53-8898-4939f31cc13f
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 26b043f1f9e7a1e0cd00c2f31c28f7d6685f0232
ms.openlocfilehash: 64beb891fda54da3718a322f6628a2987ff35111


---


# Erstellen, Konfigurieren und Veröffentlichen einer benutzerdefinierten Vorlage

>*Gilt für: Azure Rights Management, Office 365*


Benutzerdefinierte Vorlagen erstellen und verwalten Sie im klassischen Azure-Portal. Sie können dies direkt im klassischen Azure-Portal durchführen, oder Sie können sich beim Office 365 Admin Center anmelden und die **erweiterten Funktionen** für Rights Management auswählen, über die Sie zum klassischen Azure-Portal weitergeleitet werden.

Sie müssen über globale Administratorrechte verfügen, um Vorlagen im klassischen Azure-Portal zu erstellen und zu verwalten. Wenn Sie die globale Administratorrolle für Azure RMS anderen Benutzern zugewiesen haben, können diese ebenfalls Vorlagen erstellen und verwalten, müssen jedoch [PowerShell](configure-templates-with-powershell.md) verwenden. Weitere Informationen finden Sie unter [Werden zum Konfigurieren von Azure RMS globale Administratorrechte benötigt, oder kann ich diese Aufgabe an andere Administratoren delegieren?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators) 

Verwenden Sie die folgenden Verfahren, um benutzerdefinierte Vorlagen für Rights Management zu erstellen, zu konfigurieren und zu veröffentlichen.

## So erstellen Sie eine benutzerdefinierte Vorlage

1.  Je nachdem, ob Sie sich beim Office 365 Admin Center oder beim klassischen Azure-Portal angemeldet haben, führen Sie eine der folgenden Aktionen aus:

    -   Vom [Office 365 Admin Center](https://portal.office.com/):

        1.  Klicken Sie im linken Bereich auf **Diensteinstellungen**.

        2.  Klicken Sie auf der Seite **Diensteinstellungen** auf **Rechteverwaltung**.

        3.  Klicken Sie im Abschnitt **Schützen Sie Ihre Informationen** auf **Verwalten**.

        4.  Klicken Sie im Abschnitt **Rechteverwaltung** auf **Erweiterte Features**.

            > [!NOTE]
            > Wenn Sie Rights Management nicht aktiviert haben, klicken Sie zuerst auf **Aktivieren**, und bestätigen Sie Ihre Aktion. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](activate-service.md).
            > 
            > Wenn Sie zuvor noch nicht auf **Erweiterte Funktionen** geklickt haben, befolgen Sie nach der Aktivierung von Rights Management die Anweisungen auf dem Bildschirm, um ein kostenloses Azure-Abonnement zu erhalten, das für den Zugriff auf das klassische Azure-Portal erforderlich ist.

            Beim Klicken auf **Erweiterte Funktionen** lädt Azure das klassische Azure-Portal. Darin können Sie **RIGHTS MANAGEMENT** für Azure Active Directory in Ihrer Organisation verwalten.

    -   Gehen Sie im [klassischen Azure-Portal](http://go.microsoft.com/fwlink/p/?LinkID=275081) wie folgt vor:

        1.  Klicken Sie im linken Bereich auf **ACTIVE DIRECTORY**.

        2.  Klicken Sie auf der Seite **Active Directory** auf **RIGHTS MANAGEMENT**.

        3.  Wählen Sie das Verzeichnis aus, für das Sie Rights Management verwalten möchten.

        4.  Wenn Sie Rights Management noch nicht aktiviert haben, klicken Sie auf **AKTIVIEREN** , und bestätigen Sie Ihre Aktion.

            > [!NOTE]
            > Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](activate-service.md).

2.  Erstellen einer neuen Vorlage:

    -   Klicken Sie im klassischen Azure-Portal auf der Schnellstartseite **Erste Schritte mit Rights Management** auf **Neue Richtlinienvorlage für Rechte erstellen**.

        Wenn Sie diese Seite nicht sofort nach dem Ausführen der Anweisungen für Office 365 sehen, befolgen Sie die oben aufgeführten Navigationsanweisungen für das klassische Azure-Portal.

3.  Wählen Sie auf der Seite **Neue Richtlinienvorlage für Rechte hinzufügen** eine Sprache aus, in der Sie den Namen und die Beschreibung der Vorlage eingeben möchten, die Benutzern angezeigt werden (Sie können später weitere Sprachen hinzufügen). Geben Sie dann einen eindeutigen Namen und eine Beschreibung ein, und klicken Sie auf die Schaltfläche "Fertig stellen".

Klicken Sie auf der Schnellstartseite **Erste Schritte mit der Rechteverwaltung** auf **Vorlagen für Benutzerrechterichtlinien verwalten**. Ihre neu erstellte Vorlage wird mit dem Status **Archiviert**in der Liste der Vorlagen angezeigt. Zu diesem Zeitpunkt ist die Vorlage zwar erstellt, aber noch nicht konfiguriert und für die Benutzer noch nicht sichtbar.

## So konfigurieren und veröffentlichen Sie eine benutzerdefinierte Vorlage

1.  Wählen Sie auf der Seite **VORLAGEN** im klassischen Azure-Portal Ihre neu erstellte Vorlage aus.

2.  Klicken Sie auf der Schnellstartseite **Ihre Vorlage wurde hinzugefügt** auf **Erste Schritte** aus Schritt 1, **Rechte für Benutzer und Gruppen konfigurieren** , klicken Sie daraufhin auf **ERSTE SCHRITTE** oder **HINZUFÜGEN**, und wählen Sie dann die Benutzer und Gruppen aus, die Rechte besitzen sollen, um den Inhalt zu benutzen, der durch die neue Vorlage geschützt ist.

    > [!NOTE]
    > Die von Ihnen ausgewählten Benutzer oder Gruppen müssen über eine E-Mail-Adresse verfügen. In einer Produktionsumgebung ist dies praktisch immer der Fall, aber in einer einfachen Testumgebung müssen Sie eventuell Benutzerkonten oder Gruppen E-Mail-Adressen hinzufügen.

    Als bewährte Methode verwenden Sie besser Gruppen als Benutzer, was die Verwaltung der Vorlagen vereinfacht. Wenn Sie Active Directory lokal haben und Synchronisierung mit Azure AD vornehmen, können Sie E-Mail-fähige Gruppen verwenden, die entweder Sicherheits- oder Verteilergruppen sind. Wenn Sie jedoch allen Benutzern in der Organisation Rechte erteilen möchten, ist es effizienter, eine der Standardvorlagen zu kopieren, anstatt mehrere Gruppen anzugeben. Weitere Informationen finden Sie unter [Kopieren einer Vorlage](copy-template.md).

    > [!TIP]
    > Sie können Ihrer Vorlage Benutzer von außerhalb Ihrer Organisation („externe Benutzer“) hinzufügen, indem Sie eine E-Mail-aktivierte Gruppe auswählen, die Kontakte aus Office 365 oder Exchange Online enthält. Dadurch können Sie diesen Benutzern genau wie Benutzern in Ihrer Organisation Rechte zuweisen. Beispielsweise können Sie verhindern, dass Kunden eine von Ihnen gesendete Preisliste bearbeiten. Verwenden Sie diese Vorlagenkonfiguration nicht zum Schutz von E-Mails, wenn Benutzer von außerhalb Ihrer Organisation die geschützten E-Mails mit Outlook Web App lesen.
    > 
    > Außerdem können Sie der Vorlage später Benutzer von außerhalb Ihrer Organisation hinzufügen, indem Sie das [Windows PowerShell-Modul für Azure Rights Management](install-powershell.md) und eine der folgenden Methoden verwenden:
    > 
    > -  **Verwenden eines Rechtedefinitionsobjekts zum Aktualisieren einer Vorlage**: Geben Sie die externen E-Mail-Adressen und die dazugehörigen Rechte in einem Rechtedefinitionsobjekt an, das Sie dann zum Aktualisieren der Vorlage verwenden. Sie geben das Rechtedefinitionsobjekt an, indem Sie mit dem [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)-Cmdlet eine Variable erstellen und diese Variable anschließend mit dem [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)-Cmdlet für den -RightsDefinition-Parameter bereitstellen, um eine vorhandene Vorlage zu ändern. Wenn Sie jedoch diese Benutzer zu einer vorhandenen Vorlage hinzufügen, müssen Sie nicht nur für die neuen externen Benutzer Rechtedefinitionsobjekte definieren, sondern auch für die vorhandenen Gruppen in den Vorlagen.
    > -  **Exportieren, Bearbeiten und Importieren der aktualisierten Vorlage**: Exportieren Sie die Vorlage mithilfe des [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)-Cmdlets in eine Datei, und bearbeiten Sie diese, indem Sie die externen Adressen dieser Benutzer und ihre Rechte den vorhandenen Gruppen und Rechten hinzufügen. Importieren Sie diese Änderung anschließend mit dem [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)-Cmdlet wieder in Azure RMS.

3.  Klicken Sie auf die Schaltfläche "Weiter", und weisen Sie dann Ihren ausgewählten Benutzern und Gruppen eins der aufgeführten Rechte zu.

    In der angezeigten Beschreibung finden Sie weitere Informationen zu jedem der Rechte (sowie zu benutzerdefinierten Rechten). Ausführlichere Informationen finden Sie auch unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md). Anwendungen, die RMS unterstützen, unterscheiden sich möglicherweise darin, wie sie diese Rechte implementieren Lesen Sie die Dokumentationen der Anwendungen, und führen Sie eigene Tests mit den Anwendungen aus, die von Benutzer verwendet werden, um das Verhalten zu überprüfen, bevor Sie die Vorlage für Benutzer bereitstellen. Um diese Vorlage für diese Tests nur für Administratoren sichtbar zu machen, legen Sie diese Vorlage als Abteilungsvorlage fest (Schritt 6).

4.  Wenn Sie **Benutzerdefiniert**ausgewählt haben, klicken Sie auf die Schaltfläche „Weiter“, und wählen Sie dann diese benutzerdefinierten Rechte aus.

    Obwohl Sie jede Kombination aus den verfügbaren, einzelnen Rechten verwenden können, können in manchen Anwendungen einige Rechte von anderen einzelnen Rechten abhängig sein. Wenn dies der Fall ist, werden die abhängigen Rechte automatisch für Sie ausgewählt.

    > [!TIP]
    > Fügen Sie ggf. das Recht **Inhalt kopieren und extrahieren** hinzu, und gewähren Sie es ausgewählten Administratoren oder Mitarbeitern in anderen Rollen, die für die Informationswiederherstellung verantwortlich sind. Durch die Gewährung dieses Rechts können sie Schutz bei Bedarf von Dateien und E-Mails entfernen, die durch die Verwendung dieser Vorlage geschützt werden. Diese Fähigkeit zum Entfernen des Schutzes auf Vorlagenebene bietet eine präzisere Kontrolle als die Verwendung der Administratorfunktion.

5.  Klicken Sie auf die Schaltfläche "Fertig stellen".

6.  Wenn Sie möchten, dass die Vorlage nur für eine Teilmenge der Benutzer sichtbar ist, wenn sie eine Liste der Vorlagen in Anwendungen anzeigen: Klicken Sie auf **BEREICH** , um die Vorlage als Abteilungsvorlage zu konfigurieren, und klicken Sie auf **ERSTE SCHRITTE**. Andernfalls springen Sie zum Schritt 9.

    Weitere Informationen zu Abteilungsvorlagen: Standardmäßig sehen alle Benutzer in Ihrem Azure-Verzeichnis alle veröffentlichten Vorlagen, und die Benutzer können dann die Vorlagen aus Anwendungen auswählen, wenn Inhalt geschützt werden soll. Wenn Sie möchten, dass nur bestimmte Benutzer einige der veröffentlichten Vorlagen sehen können, müssen Sie den Bereich der Vorlagen auf diese Benutzer beschränken. Dann können diese Vorlagen nur von diesen Benutzern ausgewählt werden. Andere Benutzer, die Sie nicht angegeben haben, sehen die Vorlagen nicht und können diese daher nicht auswählen. Diese Vorgehensweise kann das Auswählen der richtigen Vorlage für Benutzer vereinfachen, insbesondere wenn Sie Vorlagen erstellen, die für eine Verwendung durch bestimmte Gruppen oder Abteilungen vorgesehen sind. Benutzer sehen dann nur die Vorlagen, die für sie entwickelt wurden.

    Angenommen, Sie haben eine Vorlage für die Personalabteilung erstellt, mit der die Leseberechtigung für Mitarbeiter der Finanzabteilung erteilt wird. Damit nur Mitarbeiter der Personalabteilung diese Vorlage anwenden können, wenn sie die Rights Management-Freigabeanwendung verwenden, legen Sie den Bereich der Vorlage auf die E-Mail-aktivierte Gruppe "Personalabteilung" fest. Dann können nur Mitglieder dieser Gruppe diese Vorlage sehen und anwenden.

7.  Wählen Sie auf der Seite **VORLAGENSICHTBARKEIT** die Benutzer und Gruppen aus, für die es möglich sein soll, die Vorlage in den RMS-fähigen Anwendungen auszuwählen. Wie bereits zuvor sollten Sie Gruppen statt Benutzer verwenden, und die Gruppen oder Benutzer, die Sie auswählen, müssen E-Mail-Adressen haben.

8.  Klicken Sie auf die Schaltfläche "Weiter", und entscheiden Sie, ob Anwendungskompatibilität für Ihre Abteilungsvorlage konfiguriert werden muss. Wenn ja, klicken Sie auf **ANWENDUNGSKOMPATIBILITÄT**, aktivieren Sie das Kontrollkästchen, und klicken Sie auf **Vollständig**.

    Warum müssen Sie möglicherweise Anwendungskompatibilität konfigurieren? Nicht alle Anwendungen können Abteilungsvorlagen unterstützen. Dazu muss sich die Anwendung zunächst beim RMS-Dienst authentifizieren, bevor die Vorlagen heruntergeladen werden. Wird der Authentifizierungsprozess nicht ausgeführt, wird standardmäßig keine der Abteilungsvorlagen heruntergeladen. Sie können dieses Verhalten außer Kraft setzen, indem Sie angeben, dass alle Abteilungsvorlagen heruntergeladen werden sollen. Dazu konfigurieren Sie die Anwendungskompatibilität und aktivieren das Kontrollkästchen **Zeigen Sie diese Vorlage allen Benutzern, wenn die Anwendungen die Benutzeridentität nicht unterstützen** .

    Wenn Sie beispielsweise keine Anwendungskompatibilität für die Abteilungsvorlage im Personalabteilungsbeispiel konfigurieren, können nur Benutzer in der Personalabteilung die Abteilungsvorlage sehen, wenn sie die RMS-Freigabeanwendung verwenden. Benutzer, die Outlook Web Access (OWA) aus Exchange Server 2013 verwenden, können die Abteilungsvorlage dagegen nicht sehen, weil Exchange OWA und Exchange ActiveSync zurzeit keine Abteilungsvorlagen unterstützen. Wenn Sie dieses Standardverhalten außer Kraft setzen, indem Sie die Anwendungskompatibilität konfigurieren, können nur Benutzer in der Personalabteilung die Abteilungsvorlage sehen, wenn sie die RMS-Freigabeanwendung verwenden, aber alle Benutzer können die Abteilungsvorlage sehen, wenn sie Outlook Web Access (OWA) verwenden. Wenn Benutzer OWA oder Exchange ActiveSync aus Exchange Online verwenden, können entweder alle Benutzer die Abteilungsvorlagen sehen oder kein Benutzer, je nach dem Status der Vorlage ("Archivierung" oder "Veröffentlicht") in Exchange Online.

    Office 2016 unterstützt Abteilungsvorlagen nativ, und Gleiches gilt für Office 2013 ab Version 15.0.4727.1000, die im Juni 2015 als Bestandteil von [KB 3054853](https://support.microsoft.com/kb/3054853) veröffentlicht wurde.

    > [!NOTE]
    > Wenn Sie über Anwendungen verfügen, die noch keine native Unterstützung für Abteilungsvorlagen bieten, können Sie ein benutzerdefiniertes RMS-Vorlagen-Downloadskript oder andere Tools verwenden, um diese Vorlagen im lokalen RMS-Clientordner bereitzustellen. Anschließend werden die Abteilungsvorlagen von diesen Anwendungen richtigerweise nur für die Benutzer und Gruppen angezeigt, die Sie für den Vorlagenbereich ausgewählt haben:
    > 
    > -   Für Office 2010 ist der Clientordner **%localappdata%\Microsoft\DRM\Templates**.
    > -   Von einem Clientcomputer, auf den alle Vorlagen heruntergeladen wurden, können Sie die Vorlagendateien kopieren und dann auf anderen Computern einfügen.
    > 
    > Sie können [das benutzerdefinierte RMS-Vorlagenskript von der Microsoft Connect-Website herunterladen](http://go.microsoft.com/fwlink/?LinkId=524506). Wenn nach dem Klicken auf diesen Link eine Fehlermeldung angezeigt wird, haben Sie sich wahrscheinlich noch nicht bei Microsoft Connect registriert. So registrieren Sie sich:
    > 
    > 1.  Wechseln Sie zur [Microsoft Connect-Website](http://www.connect.microsoft.com), und melden Sie sich mit Ihrem Microsoft-Konto an.
    > 2.  Klicken Sie auf **Verzeichnis**, und wählen Sie die Kategorie **Connect-Produkte anzeigen, für die derzeit kein Feedback angenommen wird** aus.
    > 3.  Suchen Sie nach **Rights Management Services**, und klicken Sie für das Programm **Microsoft RMS Enterprise Features** auf **Beitreten**.

9. Klicken Sie auf **KONFIGURIEREN** , und fügen Sie zusätzliche Sprachen hinzu, die von Benutzern verwendet werden, zusammen mit dem Namen und der Beschreibung dieser Vorlage in dieser Sprache. Wenn Sie mehrsprachige Benutzer haben, ist es wichtig, jede verwendete Sprache hinzuzufügen sowie einen Namen und eine Beschreibung in der jeweiligen Sprache bereitzustellen. Benutzer sehen dann den Namen und die Beschreibung der Vorlage in derselben Sprache wie der ihres Clientbetriebssystems, wodurch sichergestellt wird, dass sie die auf ein Dokument oder eine E-Mail angewendete Richtlinie verstehen. Liegt keine Übereinstimmung mit ihrem Clientbetriebssystem vor, werden Name und Beschreibung in der Sprache angezeigt, die Sie beim ersten Erstellen der Vorlage angegeben haben.

    Überprüfen Sie dann, ob Sie Änderungen an den folgenden Einstellungen vornehmen möchten:

    |Einstellung|Weitere Informationen|
    |-----------|--------------------|
    |**Inhalt läuft ab am**|Definieren Sie ein Datum oder eine Anzahl von Tagen für diese Vorlage, nach deren Ablauf Dateien, die durch diese Vorlage geschützt sind, nicht mehr geöffnet werden sollen. Sie können ein Datum oder eine Anzahl von Tagen angeben, beginnend ab dem Zeitpunkt, zu dem der Schutz auf die Datei angewendet wird.<br /><br />Wenn Sie ein Datum angeben, wird der Schutz ab Mitternacht in Ihrer aktuellen Zeitzone wirksam.|
    |**Offlinezugriff**|Verwenden Sie diese Einstellung, um Sicherheitsanforderungen zu erfüllen, wenn Benutzer in der Lage sein müssen, geschützte Dateien ohne Internetverbindung zu öffnen.<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und Zugriffe werden protokolliert. Sollte dies eintreten, werden Benutzer, wenn ihre Anmeldeinformationen nicht zwischengespeichert wurden, aufgefordert, sich anzumelden, bevor sie die Datei öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden die Richtlinie und die Benutzergruppenmitgliedschaft erneut ausgewertet. Dies bedeutet, dass es bei Benutzern für dieselbe Datei zu unterschiedlichen Zugriffsergebnissen kommen kann, wenn sich seit ihrem letzten Zugriff auf die Datei Änderungen an der Richtlinie oder ihrer Gruppenmitgliedschaft ereignet haben.|

10. Wenn Sie sicher sind, dass die Vorlage für Ihre Benutzer ordnungsgemäß konfiguriert wurde, klicken Sie auf **VERÖFFENTLICHEN** , um die Vorlage für Benutzer sichtbar zu machen, und klicken Sie auf **Speichern**.

11. Klicken Sie im klassischen Azure-Portal auf die Schaltfläche „Zurück“, um zur Seite **VORLAGEN** zurückzukehren, wo Ihre Vorlage nun den aktualisierten Status **Veröffentlicht** hat.

Um Änderungen an Ihrer Vorlage vorzunehmen, wählen Sie diese aus, und verwenden Sie erneut die Schnellstartschritte. Alternativ können Sie eine der folgenden Optionen auswählen:

-   Um weitere Benutzer und Gruppen hinzuzufügen und die Rechte für diese zu definieren: Klicken Sie auf **RECHTE**und dann auf **HINZUFÜGEN**.

-   Um zuvor ausgewählte Benutzer oder Gruppen zu entfernen: Klicken Sie auf **RECHTE**, wählen Sie den Benutzer oder die Gruppe aus der Liste aus, und klicken Sie dann auf **LÖSCHEN**.

-   Um zu ändern, welche Benutzer die Vorlagen sehen können, um sie in Anwendungen auszuwählen: Klicken Sie auf **BEREICH**und anschließend auf **HINZUFÜGEN** , **LÖSCHEN**oder **ANWENDUNGSKOMPATIBILITÄT**.

-   Um die Vorlage für alle Benutzer auszublenden: Klicken Sie auf **KONFIGURIEREN**, auf **ARCHIVIEREN**und anschließend auf **SPEICHERN**.

-   Um andere Konfigurationsänderungen vorzunehmen: Klicken Sie auf **KONFIGURIEREN**, nehmen Sie Ihre Änderungen vor, und klicken Sie auf **SPEICHERN**.

> [!WARNING]
> Wenn Sie Änderungen an einer zuvor gespeicherten Vorlage vornehmen, werden diese Vorlagenänderungen bei Clients erst sichtbar, nachdem die Vorlagen auf deren Computern aktualisiert wurden. Weitere Informationen finden Sie unter [Aktualisieren von Vorlagen für Benutzer](refresh-templates.md).

## Weitere Informationen
[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](configure-custom-templates.md)


<!--HONumber=Aug16_HO4-->


