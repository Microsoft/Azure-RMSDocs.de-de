---
title: TEST: Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TEST
author: Cabailey
---
# ZUVOR: Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management
Nachdem Sie Azure Rights Management (Azure RMS) aktiviert haben, sind Benutzer automatisch in der Lage, zwei Standardvorlagen zu verwenden, die ihnen die Anwendung von Richtlinien auf vertrauliche Dateien erleichtern, die den Zugriff auf autorisierte Benutzer in Ihrer Organisation beschränken. Diese zwei Vorlagen enthalten die folgenden Rechterichtlinieneinschränkungen:

-   Schreibgeschützte Anzeige geschützter Inhalte

    -   Anzeigename: **<Unternehmensname> – Nur vertrauliche Ansicht**

    -   Bestimmte Berechtigung: Inhalt anzeigen

-   Lese- oder Änderungsberechtigungen für geschützten Inhalt

    -   Anzeigename: **<Unternehmensname> – Vertraulich**

    -   Bestimmte Berechtigungen: Inhalt anzeigen, Datei speichern, Inhalt bearbeiten, Zugewiesene Rechte anzeigen, Makros zulassen, Weiterleiten, Antworten, Allen antworten

Darüber hinaus ermöglicht es die [RMS-Freigabe-Anwendung](http://technet.microsoft.com/library/dn339006.aspx) Benutzern, eine eigene Gruppe von Berechtigungen zu definieren. Außerdem können Benutzer für den Outlook-Client sowie für Outlook Web Access die Option **Nicht weiterleiten** für E-Mails auswählen.

Für viele Organisationen sind die Standardvorlagen möglicherweise ausreichend. Wenn Sie aber eigene, benutzerdefinierte Vorlagen für Rechterichtlinien erstellen möchten, können Sie dies tun. Gründe zum Erstellen einer benutzerdefinierten Vorlage umfassen unter anderem die folgenden:

-   Sie möchten, dass eine Vorlage einer Untergruppe von Benutzern in der Organisation Rechte gewährt statt allen Benutzern.

-   Sie möchten, dass eine Vorlage (Abteilungsvorlage) nicht von allen Benutzern, sondern nur von einer Teilmenge der Benutzer aus Anwendungen angezeigt und ausgewählt werden kann.

-   Sie möchten ein benutzerdefiniertes Recht für eine Vorlage definieren, beispielsweise Anzeigen und Bearbeiten, aber nicht Kopieren und Drucken.

-   Sie möchten zusätzliche Optionen in einer Vorlage konfigurieren, die ein Ablaufdatum umfassen und ob auf den Inhalt ohne Internetverbindung zugegriffen werden kann.

Damit Benutzer eine benutzerdefinierte Vorlage auswählen können, die solche Einstellungen enthält, müssen Sie zuerst eine benutzerdefinierte Vorlage erstellen, konfigurieren und dann veröffentlichen.

In den folgenden Abschnitte finden Sie Informationen, wie Sie benutzerdefinierte Vorlagen konfigurieren und verwenden:

-   [Erstellen, Konfigurieren und Veröffentlichen einer benutzerdefinierten Vorlage](configure-custom-templates.md#BKMK_HowToConfigureCustomTemplates)

-   [Kopieren einer Vorlage](configure-custom-templates.md#BKMK_HowToCopyTemplates)

-   [Entfernen (Archivieren) von Vorlagen](configure-custom-templates.md#BKMK_HowToArchiveTemplates)

-   [Aktualisieren von Vorlagen für Benutzer](configure-custom-templates.md#BKMK_RefreshingTemplates)

-   [Windows PowerShell-Referenz](configure-custom-templates.md#BKMK_PowerShellTemplates)

## Erstellen, Konfigurieren und Veröffentlichen einer benutzerdefinierten Vorlage
Benutzerdefinierte Vorlagen erstellen und verwalten Sie im klassischen Azure-Portal. Sie können dies direkt im klassischen Azure-Portal durchführen, oder Sie können sich beim Office 365 Admin Center anmelden und die **erweiterten Funktionen** für Rights Management auswählen, über die Sie zum klassischen Azure-Portal weitergeleitet werden.

Verwenden Sie die folgenden Verfahren, um benutzerdefinierte Vorlagen für Rights Management zu erstellen, zu konfigurieren und zu veröffentlichen.

#### So erstellen Sie eine benutzerdefinierte Vorlage

1.  Je nachdem, ob Sie sich beim Office 365 Admin Center oder beim klassischen Azure-Portal angemeldet haben, führen Sie eine der folgenden Aktionen aus:

    -   Vom [Office 365 Admin Center](https://portal.office.com/):

        1.  Klicken Sie im linken Bereich auf **Diensteinstellungen**.

        2.  Klicken Sie auf der Seite **Diensteinstellungen** auf **Rechteverwaltung**.

        3.  Klicken Sie im Abschnitt **Schützen Sie Ihre Informationen** auf **Verwalten**.

        4.  Klicken Sie im Abschnitt **Rechteverwaltung** auf **Erweiterte Features**.

            > [!NOTE]
            > Wenn Sie Rights Management nicht aktiviert haben, klicken Sie zuerst auf **Aktivieren** , und bestätigen Sie Ihre Aktion. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](activate-service.md).
            > 
            > Wenn Sie zuvor noch nicht auf **Erweiterte Funktionen** geklickt haben, befolgen Sie nach der Aktivierung von Rights Management die Anweisungen auf dem Bildschirm, um ein kostenloses Azure-Abonnement zu erhalten, das für den Zugriff auf das klassische Azure-Portal erforderlich ist.

            Beim Klicken auf **Erweiterte Funktionen** lädt Azure das klassische Azure-Portal. Dort können Sie **RIGHTS MANAGEMENT** für Azure Active Directory in Ihrer Organisation verwalten.

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

#### So konfigurieren und veröffentlichen Sie eine benutzerdefinierte Vorlage

1.  Wählen Sie auf der Seite **VORLAGEN** im klassischen Azure-Portal Ihre neu erstellte Vorlage aus.

2.  Klicken Sie auf der Schnellstartseite **Ihre Vorlage wurde hinzugefügt** auf **Erste Schritte** aus Schritt 1, **Rechte für Benutzer und Gruppen konfigurieren** , klicken Sie daraufhin auf **ERSTE SCHRITTE** oder **HINZUFÜGEN**, und wählen Sie dann die Benutzer und Gruppen aus, die Rechte besitzen sollen, um den Inhalt zu benutzen, der durch die neue Vorlage geschützt ist.

    > [!NOTE]
    > Die von Ihnen ausgewählten Benutzer oder Gruppen müssen über eine E-Mail-Adresse verfügen. In einer Produktionsumgebung ist dies praktisch immer der Fall, aber in einer einfachen Testumgebung müssen Sie eventuell Benutzerkonten oder Gruppen E-Mail-Adressen hinzufügen.

    Als bewährte Methode verwenden Sie besser Gruppen als Benutzer, was die Verwaltung der Vorlagen vereinfacht. Wenn Sie Active Directory lokal haben und Synchronisierung mit Azure AD vornehmen, können Sie E-Mail-fähige Gruppen verwenden, die entweder Sicherheits- oder Verteilergruppen sind. Wenn Sie jedoch allen Benutzern in der Organisation Rechte erteilen möchten, ist es effizienter, eine der Standardvorlagen zu kopieren, anstatt mehrere Gruppen anzugeben. Weitere Informationen finden Sie im Abschnitt [Kopieren einer Vorlage](configure-custom-templates.md#BKMK_HowToCopyTemplates) dieses Themas.

    > [!TIP]
    > Sie können der Vorlage später Benutzer von außerhalb Ihrer Organisation hinzufügen. Dazu verwenden Sie das [Windows PowerShell-Modul für Azure Rights Management](https://technet.microsoft.com/library/jj585012.aspx) und verwenden eine der folgenden Methoden:
    > 
    > -   **Verwenden eines Rechtedefinitionsobjekts zum Aktualisieren einer Vorlage**: Geben Sie die externen E-Mail-Adressen und ihre Rechte in einem Rechtedefinitionsobjekt an, das Sie dann zum Aktualisieren der Vorlage verwenden. Sie geben das Rechtedefinitionsobjekt an, indem Sie mit dem [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)-Cmdlet eine Variable erstellen und diese Variable anschließend mit dem [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)-Cmdlet für den -RightsDefinition-Parameter bereitstellen, um eine vorhandene Vorlage zu ändern. Wenn Sie jedoch diese Benutzer zu einer vorhandenen Vorlage hinzufügen, müssen Sie nicht nur für die neuen externen Benutzer Rechtedefinitionsobjekte definieren, sondern auch für die vorhandenen Gruppen in den Vorlagen.
    > -   **Exportieren, Bearbeiten und Importieren der aktualisierten Vorlage**: Exportieren Sie die Vorlage mithilfe des [Export-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)-Cmdlets in eine Datei, und bearbeiten Sie diese, indem Sie die externen Adressen dieser Benutzer und ihre Rechte den vorhandenen Gruppen und Rechten hinzufügen. Importieren Sie diese Änderung anschließend mit dem [Import-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)-Cmdlet wieder in Azure RMS.

3.  Klicken Sie auf die Schaltfläche "Weiter", und weisen Sie dann Ihren ausgewählten Benutzern und Gruppen eins der aufgeführten Rechte zu.

    In der angezeigten Beschreibung finden Sie weitere Informationen zu jedem der Rechte (sowie zu benutzerdefinierten Rechten). Ausführlichere Informationen finden Sie auch unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md). Anwendungen, die RMS unterstützen, unterscheiden sich möglicherweise darin, wie sie diese Rechte implementieren Lesen Sie die Dokumentationen der Anwendungen, und führen Sie eigene Tests mit den Anwendungen aus, die von Benutzer verwendet werden, um das Verhalten zu überprüfen, bevor Sie die Vorlage für Benutzer bereitstellen. Um diese Vorlage für diese Tests nur für Administratoren sichtbar zu machen, legen Sie diese Vorlage als Abteilungsvorlage fest (Schritt 6).

4.  Wenn Sie **Benutzerdefiniert**ausgewählt haben, klicken Sie auf die Schaltfläche „Weiter“, und wählen Sie dann diese benutzerdefinierten Rechte aus.

    Obwohl Sie jede Kombination aus den verfügbaren, einzelnen Rechten verwenden können, können in manchen Anwendungen einige Rechte von anderen einzelnen Rechten abhängig sein. Wenn dies der Fall ist, werden die abhängigen Rechte automatisch für Sie ausgewählt.

    > [!TIP]
    > Fügen Sie ggf. das Recht **Inhalt kopieren und extrahieren** hinzu, und gewähren Sie es ausgewählten Administratoren oder Mitarbeitern in anderen Rollen, die für die Informationswiederherstellung verantwortlich sind. Durch die Gewährung dieses Rechts können sie Schutz bei Bedarf von Dateien und E-Mails entfernen, die durch die Verwendung dieser Vorlage geschützt werden. Diese Fähigkeit zum Entfernen des Schutzes auf Vorlagenebene bietet eine präzisere Kontrolle als die Verwendung der Administratorfunktion.

5.  Klicken Sie auf die Schaltfläche "Fertig stellen".

6.  Wenn Sie möchten, dass die Vorlage nur für eine Teilmenge der Benutzer sichtbar ist, wenn sie eine Liste der Vorlagen in Anwendungen anzeigen: Klicken Sie auf **BEREICH** , um die Vorlage als Abteilungsvorlage zu konfigurieren, und klicken Sie auf **ERSTE SCHRITTE**. Andernfalls springen Sie zum Schritt 9.

    Weitere Informationen zu Abteilungsvorlagen: Standardmäßig sehen alle Benutzer in Ihrem Azure-Verzeichnis alle veröffentlichten Vorlagen, und die Benutzer können dann die Vorlagen aus Anwendungen auswählen, wenn Inhalt geschützt werden soll. Wenn Sie möchten, dass nur bestimmte Benutzer einige der veröffentlichten Vorlagen sehen können, müssen Sie den Bereich der Vorlagen auf diese Benutzer beschränken. Dann können diese Vorlagen nur von diesen Benutzern ausgewählt werden. Andere Benutzer, die Sie nicht angegeben haben, sehen die Vorlagen nicht und können diese daher nicht auswählen. Diese Vorgehensweise kann das Auswählen der richtigen Vorlage für Benutzer vereinfachen, insbesondere wenn Sie Vorlagen erstellen, die für eine Verwendung durch bestimmte Gruppen oder Abteilungen vorgesehen sind. Benutzer sehen dann nur die Vorlagen, die für sie entwickelt wurden.

    Angenommen, Sie haben eine Vorlage für die Personalabteilung erstellt, die Leseberechtigung für Mitarbeiter der Finanzabteilung erteilt. Damit nur Mitarbeiter der Personalabteilung diese Vorlage anwenden können, wenn sie die Rights Management-Freigabeanwendung verwenden, legen Sie den Bereich der Vorlage auf die E-Mail-aktivierte Gruppe "Personalabteilung" fest. Dann können nur Mitglieder dieser Gruppe diese Vorlage sehen und anwenden.

7.  Wählen Sie auf der Seite **VORLAGENSICHTBARKEIT** die Benutzer und Gruppen aus, denen es möglich sein soll, die Vorlage in den RMS-fähige Anwendungen auswählen zu können. Wie bereits zuvor sollten Sie Gruppen statt Benutzer verwenden, und die Gruppen oder Benutzer, die Sie auswählen, müssen E-Mail-Adressen haben.

8.  Klicken Sie auf die Schaltfläche "Weiter", und entscheiden Sie, ob Anwendungskompatibilität für Ihre Abteilungsvorlage konfiguriert werden muss. Wenn ja, klicken Sie auf **ANWENDUNGSKOMPATIBILITÄT**, aktivieren Sie das Kontrollkästchen, und klicken Sie auf **Vollständig**.

    Warum müssen Sie möglicherweise Anwendungskompatibilität konfigurieren? Nicht alle Anwendungen können Abteilungsvorlagen unterstützen. Dazu muss sich die Anwendung zunächst beim RMS-Dienst authentifizieren, bevor die Vorlagen heruntergeladen werden. Wird der Authentifizierungsprozess nicht ausgeführt, wird standardmäßig keine der Abteilungsvorlagen heruntergeladen. Sie können dieses Verhalten außer Kraft setzen, indem Sie angeben, dass alle Abteilungsvorlagen heruntergeladen werden sollen. Dazu konfigurieren Sie die Anwendungskompatibilität und aktivieren das Kontrollkästchen **Zeigen Sie diese Vorlage allen Benutzern, wenn die Anwendungen die Benutzeridentität nicht unterstützen** .

    Wenn Sie beispielsweise keine Anwendungskompatibilität für die Abteilungsvorlage im Personalabteilungsbeispiel konfigurieren, können nur Benutzer in der Personalabteilung die Abteilungsvorlage sehen, wenn sie die RMS-Freigabeanwendung verwenden. Benutzer, die Outlook Web Access (OWA) aus Exchange Server 2013 verwenden, können die Abteilungsvorlage dagegen nicht sehen, weil Exchange OWA und Exchange ActiveSync zurzeit keine Abteilungsvorlagen unterstützen. Wenn Sie dieses Standardverhalten außer Kraft setzen, indem Sie die Anwendungskompatibilität konfigurieren, können nur Benutzer in der Personalabteilung die Abteilungsvorlage sehen, wenn sie die RMS-Freigabeanwendung verwenden, aber alle Benutzer können die Abteilungsvorlage sehen, wenn sie Outlook Web Access (OWA) verwenden. Wenn Benutzer OWA oder Exchange ActiveSync aus Exchange Online verwenden, können entweder alle Benutzer die Abteilungsvorlagen sehen oder kein Benutzer, je nach dem Status der Vorlage ("Archivierung" oder "Veröffentlicht") in Exchange Online.

    Office 2016 bietet systemeigene Unterstützung von Abteilungsvorlagen. Das gilt auch für Office 2013 mit den neuesten Office-Updates ([KB 3054853](https://support.microsoft.com/kb/3054853)).

    > [!NOTE]
    > Wenn Sie Anwendungen haben, die Abteilungsvorlagen noch nicht direkt unterstützen, können Sie ein benutzerdefiniertes Skript zum Herunterladen von RMS-Vorlagen oder andere Tools verwenden, um diese Vorlagen im lokalen RMS-Clientordner bereitzustellen. Anschließend werden die Abteilungsvorlagen von diesen Anwendungen richtigerweise nur für die Benutzer und Gruppen angezeigt, die Sie für den Vorlagenbereich ausgewählt haben:
    > 
    > -   Für Office 2010 ist der Clientordner **%localappdata%\Microsoft\DRM\Templates**.
    > -   Von einem Clientcomputer, auf den alle Vorlagen heruntergeladen wurden, können Sie die Vorlagendateien kopieren und dann auf anderen Computern einfügen.
    > 
    > Sie können [das benutzerdefinierte RMS-Vorlagenskript von der Microsoft Connect-Website herunterladen](http://go.microsoft.com/fwlink/?LinkId=524506). Wenn nach dem Klicken auf diesen Link eine Fehlermeldung angezeigt wird, haben Sie sich wahrscheinlich noch nicht bei Microsoft Connect registriert.   So registrieren Sie sich:
    > 
    > 1.  Wechseln Sie zur [Microsoft Connect-Website](http://www.connect.microsoft.com), und melden Sie sich mit Ihrem Microsoft-Konto an.
    > 2.  Klicken Sie auf **Verzeichnis**, und wählen Sie die Kategorie **Connect-Produkte anzeigen, für die derzeit kein Feedback angenommen wird** aus.
    > 3.  Suchen Sie nach **Rights Management Services**, und klicken Sie für das Programm **Microsoft RMS Enterprise Features** auf **Beitreten**.

9. Klicken Sie auf **KONFIGURIEREN** , und fügen Sie zusätzliche Sprachen hinzu, die von Benutzern verwendet werden, zusammen mit dem Namen und der Beschreibung dieser Vorlage in dieser Sprache. Wenn Sie mehrsprachige Benutzer haben, ist es wichtig, jede von diesen verwendete Sprache hinzuzufügen sowie einen Namen und eine Beschreibung in der jeweiligen Sprache bereitzustellen. Benutzer sehen dann den Namen und die Beschreibung der Vorlage in derselben Sprache wie der ihres Clientbetriebssystems, wodurch sichergestellt wird, dass sie die auf ein Dokument oder eine E-Mail angewendete Richtlinie verstehen. Liegt keine Übereinstimmung mit ihrem Clientbetriebssystem vor, werden Name und Beschreibung in der Sprache angezeigt, die Sie beim ersten Erstellen der Vorlage angegeben haben.

    Überprüfen Sie dann, ob Sie Änderungen an den folgenden Einstellungen vornehmen möchten:

    |Einstellung|Weitere Informationen|
    |-----------|--------------------|
    |**Inhalt läuft ab am**|Definieren Sie ein Datum oder eine Anzahl von Tagen für diese Vorlage, nach deren Ablauf Dateien, die durch diese Vorlage geschützt sind, nicht mehr geöffnet werden sollen. Sie können ein Datum oder eine Anzahl von Tagen angeben, beginnend ab dem Zeitpunkt, zu dem der Schutz auf die Datei angewendet wird.<br /><br />Wenn Sie ein Datum angeben, wird der Schutz ab Mitternacht in Ihrer aktuellen Zeitzone wirksam.|
    |**Offlinezugriff**|Verwenden Sie diese Einstellung, um Sicherheitsanforderungen zu erfüllen, wenn Benutzer in der Lage sein müssen, geschützte Dateien ohne Internetverbindung öffnen zu können.<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und Zugriffe werden protokolliert. Sollte dies eintreten, werden Benutzer, wenn ihre Anmeldeinformationen nicht zwischengespeichert wurden, aufgefordert, sich anzumelden, bevor sie die Datei öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden die Richtlinie und die Benutzergruppenmitgliedschaft erneut ausgewertet. Dies bedeutet, dass es bei Benutzern für dieselbe Datei zu unterschiedlichen Zugriffsergebnissen kommen kann, wenn sich seit ihrem letzten Zugriff auf die Datei Änderungen an der Richtlinie oder ihrer Gruppenmitgliedschaft ereignet haben.|

10. Wenn Sie sicher sind, dass die Vorlage für Ihre Benutzer ordnungsgemäß konfiguriert wurde, klicken Sie auf **VERÖFFENTLICHEN** , um die Vorlage für Benutzer sichtbar zu machen, und klicken Sie auf **Speichern**.

11. Klicken Sie im klassischen Azure-Portal auf die Schaltfläche „Zurück“, um zur Seite **VORLAGEN** zurückzukehren, wo Ihre Vorlage nun den aktualisierten Status **Veröffentlicht** hat.

Um Änderungen an Ihrer Vorlage vorzunehmen, wählen Sie diese aus, und verwenden Sie erneut die Schnellstartschritte. Alternativ können Sie eine der folgenden Optionen auswählen:

-   Um weitere Benutzer und Gruppen hinzuzufügen und die Rechte für diese zu definieren: Klicken Sie auf **RECHTE**und dann auf **HINZUFÜGEN**.

-   Um zuvor ausgewählte Benutzer oder Gruppen zu entfernen: Klicken Sie auf **RECHTE**, wählen Sie den Benutzer oder die Gruppe aus der Liste aus, und klicken Sie dann auf **LÖSCHEN**.

-   Um zu ändern, welche Benutzer die Vorlagen sehen können, um sie in Anwendungen auszuwählen: Klicken Sie auf **BEREICH**und anschließend auf **HINZUFÜGEN** , **LÖSCHEN**oder **ANWENDUNGSKOMPATIBILITÄT**.

-   Um die Vorlage für alle Benutzer auszublenden: Klicken Sie auf **KONFIGURIEREN**, auf **ARCHIVIEREN**und anschließend auf **SPEICHERN**.

-   Um andere Konfigurationsänderungen vorzunehmen: Klicken Sie auf **KONFIGURIEREN**, nehmen Sie Ihre Änderungen vor, und klicken Sie auf **SPEICHERN**.

> [!WARNING]
> Wenn Sie Änderungen an einer zuvor gespeicherten Vorlage vornehmen, werden diese Vorlagenänderungen bei Clients erst sichtbar, nachdem die Vorlagen auf deren Computern aktualisiert wurden. Weitere Informationen finden Sie im Abschnitt [Aktualisieren von Vorlagen für Benutzer](configure-custom-templates.md#BKMK_RefreshingTemplates) dieses Themas.

## Kopieren einer Vorlage
Wenn Sie eine neue Vorlage erstellen möchten, die über sehr ähnliche Einstellungen verfügt wie eine bereits vorhandene Vorlage, wählen Sie die Originalvorlage auf der Seite **VORLAGEN** aus, klicken Sie auf **KOPIEREN**, geben Sie einen eindeutigen Namen an, und nehmen Sie dann die erforderlichen Änderungen vor.

> [!IMPORTANT]
> Wenn Sie eine Vorlage kopieren, wird ebenfalls der Status **Veröffentlicht** oder **Archiviert** kopiert. Wenn Sie eine veröffentlichte Vorlage kopieren, wird ihr unmittelbarer Status veröffentlicht, wenn Sie ihn nicht ändern.

Sie können sowohl benutzerdefinierte Vorlagen als auch die Standardvorlagen kopieren. Kopieren Sie als bewährte Methode eine der Standardvorlagen, anstatt eine neue benutzerdefinierte Vorlage zu erstellen, wenn die Vorlage allen Benutzern in Ihrer Organisation Rechte erteilen soll. Diese Methode bedeutet, dann Sie nicht mehrere Gruppen erstellen oder auswählen müssen, um alle Benutzer anzugeben. Stellen Sie in diesem Szenario jedoch sicher, dass ein neuer Name und eine Beschreibung für die kopierte Vorlage für weitere Sprachen angegeben werden.

## Entfernen (Archivieren) von Vorlagen
Die Standardvorlagen können nicht gelöscht werden. Sie können jedoch archiviert werden, damit sie Benutzern nicht angezeigt werden.

Wenn Sie eine benutzerdefinierte Vorlage veröffentlicht haben, diese aber für Benutzer ausblenden möchten, können Sie die Vorlage bearbeiten und dann auf der Seite **KONFIGURIEREN** die Optionen **ARCHIVIEREN** und **SPEICHERN** auswählen. Alternativ können Sie sie auf der Seite **VORLAGEN** auswählen, und auf **ARCHIVIEREN**klicken.

Da Sie die Standardvorlagen nicht bearbeiten können, müssen Sie zum Archivieren dieser Vorlagen die Option **ARCHIVIEREN** auf der Seite **VORLAGEN** verwenden. Sie können nicht die Outlook-Option **Nicht weiterleiten** archivieren.

#### So entfernen Sie eine Standardvorlage

-   Wählen Sie auf der Seite **VORLAGEN** die Standardvorlage aus, und klicken Sie auf **ARCHIVIEREN**.

Der Status ändert sich von **Veröffentlicht** zu **Archiviert**. Wenn Sie sich anders entscheiden, wählen Sie die Vorlage aus, und klicken Sie auf **VERÖFFENTLICHEN**.

## Aktualisieren von Vorlagen für Benutzer
Wenn Sie Azure RMS verwenden, werden Vorlagen automatisch auf Clientcomputer heruntergeladen, sodass Benutzer sie aus Ihren Anwendungen heraus auswählen können. Allerdings müssen Sie möglicherweise zusätzliche Schritte ausführen, wenn Sie Änderungen an der Vorlage vornehmen:

|Anwendung oder Dienst|Aktualisierungsmethode nach Änderungen|
|--------------------------|---------------------------------------------|
|Exchange Online|Manuelle Konfiguration erforderlich zum Aktualisieren von Vorlagen.<br /><br />Erweitern Sie für die Konfigurationsschritte den folgenden Abschnitt [Nur Exchange Online nur: Konfigurieren von Exchange für das Herunterladen geänderter, benutzerdefinierter Vorlagen](configure-custom-templates.md#BKMK_ExchangeOnlineTemplatesUpdate).|
|Office 365|Automatische Aktualisierung, es sind keine weiteren Schritte erforderlich.|
|Office 2016 und Office 2013<br /><br />RMS-Freigabeanwendung für Windows|Automatische Aktualisierung nach einem Zeitplan:<br /><br />Für diese neueren Office-Versionen: Das Standardaktualisierungsintervall ist alle 7 Tage.<br /><br />Für die RMS-Freigabeanwendung für Windows: Ab Version 1.0.1784.0 ist das Standardaktualisierungsintervall jeden Tag. Frühere Versionen haben ein Standardaktualisierungsintervall von alle 7 Tage.<br /><br />Um vor diesem Zeitplan eine Aktualisierung zu erzwingen, erweitern Sie den folgenden Abschnitt [Office 2016, Office 2013 und RMS-Freigabeanwendung für Windows: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage](#BKMK_Office2013ForceUpdate).|
|Office 2010|Aktualisierung bei der Benutzeranmeldung.<br /><br />Um eine Aktualisierung zu erzwingen, bitten oder zwingen Sie Benutzer, sich abzumelden und erneut anzumelden. Oder lesen Sie den folgenden Abschnitt: [Nur Office 2010: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage](#BKMK_Office2010ForceUpdate).|
Bei mobilen Geräten, die die RMS-Freigabeanwendung verwenden, werden Vorlagen ohne zusätzliche Konfiguration automatisch heruntergeladen (und erforderlichenfalls aktualisiert).

### Nur Exchange Online: Konfigurieren von Exchange für das Herunterladen geänderter, benutzerdefinierter Vorlagen
Wenn Sie die Verwaltung von Informationsrechten (IRM) für Exchange Online bereits konfiguriert haben, werden benutzerdefinierte Vorlagen für Benutzer erst heruntergeladen, nachdem Sie die folgenden Änderungen mithilfe der Windows PowerShell in Exchange Online vorgenommen haben.

> [!NOTE]
> Weitere Informationen zur Verwendung von Windows PowerShell in Exchange Online finden Sie unter [Verwenden von PowerShell mit Exchange Online](https://technet.microsoft.com/library/jj200677%28v=exchg.160%29.aspx).

Sie müssen dieses Verfahren jedes Mal ausführen, wenn Sie eine Vorlage ändern.

##### So aktualisieren Sie Vorlagen für Exchange Online

1.  Stellen Sie unter Verwendung von Windows PowerShell in Exchange Online eine Verbindung mit dem Dienst her:

    1.  Geben Sie Ihren Office 365-Benutzernamen und das Kennwort an:

        ```
        $Cred = Get-Credential
        ```

    2.  Stellen Sie eine Verbindung mit dem Exchange Online-Dienst her, indem Sie die folgenden beiden Befehle ausführen:

        ```
        $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection
        ```

        ```
        Import-PSSession $Session
        ```

2.  Verwenden Sie das [Import-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200724%28v=exchg.160%29.aspx)-Cmdlet, um Ihre vertrauenswürdige Veröffentlichungsdomäne (TPD, Trusted Publishing Domain) aus Azure RMS erneut zu importieren:

    ```
    Import-RMSTrustedPublishingDomain -Name "<TPD name>" -RefreshTemplates -RMSOnline
    ```
    Wenn der TPD-Name beispielsweise **RMS Online - 1** lautet (ein typischer Name für viele Organisationen), geben Sie Folgendes ein: **Import-RMSTrustedPublishingDomain-Name "RMS Online - 1" -RefreshTemplates-RMSOnline**.

    > [!NOTE]
    > Zur Überprüfung des TPD-Namens können Sie das Cmdlet [Get-RMSTrustedPublishingDomain](http://technet.microsoft.com/library/jj200707%28v=exchg.160%29.aspx) verwenden.

3.  Um zu überprüfen, ob die Vorlagen erfolgreich importiert wurden, warten Sie ein paar Minuten. Führen Sie dann das Cmdlet [Get-RMSTemplate](http://technet.microsoft.com/library/dd297960%28v=exchg.160%29.aspx) aus, und legen Sie den Wert von "Typ" auf "Alle" fest. Beispiel:

    ```
    Get-RMSTemplate -TrustedPublishingDomain "RMS Online - 1" -Type All
    ```
    > [!TIP]
    > Es ist sinnvoll, eine Kopie der Ausgabe zu behalten, damit Sie die Namen oder GUIDs der Vorlagen problemlos kopieren können, wenn Sie eine Vorlage später archivieren.

4.  Für jede importierte Vorlage, die in der Outlook Web App verfügbar sein soll, müssen Sie das [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx)-Cmdlet verwenden und den Wert von "Typ" auf "Verteilt" festlegen:

    ```
    Set-RMSTemplate -Identity "<name  or GUID of the template>" -Type Distributed
    ```
    Da Outlook Web Access die Benutzeroberfläche für 24 Stunden zwischenspeichert, sehen Benutzer die neue Vorlage möglicherweise erst nach bis zu einem Tag.

Darüber hinaus, wenn Sie eine (benutzerdefinierte oder Standard) Vorlage archivieren und Exchange Online mit Office 365 verwenden, können Benutzer die archivierten Vorlagen weiterhin sehen, wenn sie die Outlook Web App oder mobile Geräte verwenden, die das Exchange ActiveSync-Protokoll verwenden.

Damit Benutzer diese Vorlagen nicht mehr sehen, stellen Sie unter Verwendung von Windows PowerShell in Exchange Online eine Verbindung mit dem Dienst her, und verwenden Sie das Cmdlet [Set-RMSTemplate](http://technet.microsoft.com/library/hh529923%28v=exchg.160%29.aspx), indem Sie folgenden Befehl ausführen:

```
Set-RMSTemplate -Identity "<name or GUID of the template>" -Type Archived
```

### Office 2016, Office 2013 und die RMS-Freigabeanwendung für Windows: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage
Durch Bearbeiten der Registrierung auf Computern, auf denen Office 2016, Office 2013 oder die RMS-Freigabeanwendung (Rights Management) für Windows ausgeführt wird, können Sie den automatischen Zeitplan ändern, sodass geänderte Vorlagen auf Computern häufiger als gemäß dem Standardwert aktualisiert werden. Sie können auch eine sofortige Aktualisierung erzwingen, indem Sie die in einem Registrierungswert vorhandenen Daten löschen.

> [!WARNING]
> Die unsachgemäße Verwendung des Registrierungs-Editors kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen können. Microsoft kann nicht garantieren, dass Sie Probleme, die durch die fehlerhafte Verwendung des Registrierungs-Editors entstehen, beheben können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

##### So ändern Sie den automatischen Zeitplan

1.  Verwenden Sie einen Registrierungs-Editor, um einen der folgenden Registrierungswerte zu erstellen und festzulegen:

    -   So legen Sie eine Aktualisierungshäufigkeit in Tagen fest (mindestens 1 Tag):  Erstellen Sie einen neuen Registrierungswert namens **TemplateUpdateFrequency** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Tagen angibt. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem dieser neue Registrierungswert erstellt werden soll.

        |Registrierungspfad|Typ|Wert|
        |-----------------|--------|---------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequency|

    -   So legen Sie eine Aktualisierungshäufigkeit in Sekunden fest (mindestens 1 Sekunde):  Erstellen Sie einen neuen Registrierungswert namens **TemplateUpdateFrequencyInSeconds** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Sekunden angibt. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem dieser neue Registrierungswert erstellt werden soll.

        |Registrierungspfad|Typ|Wert|
        |-----------------|--------|---------|
        |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC|REG_DWORD|TemplateUpdateFrequencyInSeconds|

    Sie dürfen nur einen der beiden Registrierungswerte erstellen und festlegen (nicht beide). Wenn beide vorhanden sind, wird **TemplateUpdateFrequency** ignoriert.

2.  Wenn Sie eine sofortige Aktualisierung der Vorlagen erzwingen möchten, führen Sie die nächste Schrittfolge aus. Starten Sie andernfalls jetzt Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.

##### So erzwingen Sie eine sofortige Aktualisierung

1.  Löschen Sie mithilfe eines Registrierungs-Editors die Daten für den Wert **LastUpdatedTime** . Es kann beispielsweise **2015-04-20T15:52** angezeigt werden. Löschen Sie "2015-04-20T15:52", sodass keine Daten angezeigt werden. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem diese Registrierungswertdaten gelöscht werden sollen.

    |Registrierungspfad|Typ|Wert|
    |-----------------|--------|---------|
    |HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\&lt;MicrosoftRMS_FQDN&gt;\Template|REG_SZ|LastUpdatedTime|
    > [!TIP]
    > Im Registrierungspfad bezieht sich *<MicrosoftRMS_FQDN>* auf den FQDN Ihres Microsoft RMS-Diensts. Wenn Sie diesen Wert überprüfen möchten:
    > 
    > 1.  Führen Sie das [Get-AadrmConfiguration](https://msdn.microsoft.com/library/windowsazure/dn629410.aspx) -Cmdlet für Azure RMS aus. Wenn Sie das Windows PowerShell-Modul für Azure RMS noch nicht installiert haben, lesen Sie [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).
    > 2.  Identifizieren Sie in der Ausgabe den **LicensingIntranetDistributionPointUrl** -Wert.
    > 
    >     Beispiel: **LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing**
    > 3.  Entfernen Sie **https://** und **/_wmcs/licensing** aus dieser Zeichenfolge des Werts. Bei dem verbleibenden Wert handelt es sich um den FQDN Ihres Microsoft RMS-Diensts. In unserem Beispiel hat der FQDN des Microsoft RMS-Diensts folgenden Wert:
    > 
    >     **5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com**

2.  Löschen Sie den folgenden Ordner und alle darin enthaltenen Dateien: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Starten Sie Ihre Office-Anwendungen und Instanzen von Datei-Explorer neu.

### Nur Office 2010: Erzwingen der Aktualisierung einer geänderten, benutzerdefinierten Vorlage
Durch Bearbeiten der Registrierung auf Computern mit Office 2010 können Sie einen Wert festlegen, sodass geänderte Vorlagen auf Computern aktualisiert werden, ohne dass darauf gewartet wird, dass sich Benutzer ab- und wieder anmelden. Sie können auch eine sofortige Aktualisierung erzwingen, indem Sie die in einem Registrierungswert vorhandenen Daten löschen.

> [!WARNING]
> Die unsachgemäße Verwendung des Registrierungs-Editors kann zu schwerwiegenden Problemen führen, die eine Neuinstallation des Betriebssystems erforderlich machen können. Microsoft kann nicht garantieren, dass Sie Probleme, die durch die fehlerhafte Verwendung des Registrierungs-Editors entstehen, beheben können. Die Verwendung des Registrierungs-Editors erfolgt auf Ihr eigenes Risiko.

##### So ändern Sie die Aktualisierungshäufigkeit

1.  Erstellen Sie mit einem Registrierungs-Editor einen neuen Registrierungswert namens **UpdateFrequency** , und definieren Sie einen ganzzahligen Wert für die Daten, der die Häufigkeit für das Herunterladen von Änderungen an einer heruntergeladenen Vorlage in Tagen angibt. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem dieser neue Registrierungswert erstellt werden soll.

    |Registrierungspfad|Typ|Wert|
    |-----------------|--------|---------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_DWORD|UpdateFrequency|

2.  Wenn Sie eine sofortige Aktualisierung der Vorlagen erzwingen möchten, führen Sie die nächste Schrittfolge aus. Starten Sie andernfalls jetzt Ihre Office-Anwendungen neu.

##### So erzwingen Sie eine sofortige Aktualisierung

1.  Löschen Sie mithilfe eines Registrierungs-Editors die Daten für den Wert **LastUpdatedTime** . Es kann beispielsweise **2015-04-20T15:52** angezeigt werden. Löschen Sie "2015-04-20T15:52", sodass keine Daten angezeigt werden. Verwenden Sie die folgende Tabelle, um den Registrierungspfad zu finden, in dem diese Registrierungswertdaten gelöscht werden sollen.

    |Registrierungspfad|Typ|Wert|
    |-----------------|--------|---------|
    |HKEY_CURRENT_USER\Software\Microsoft\MSDRM\TemplateManagement|REG_SZ|lastUpdatedTime|

2.  Löschen Sie den folgenden Ordner und alle darin enthaltenen Dateien: **%localappdata%\Microsoft\MSIPC\Templates**

3.  Starten Sie Ihre Office-Anwendungen neu.

## Windows PowerShell-Referenz
Alle Vorgänge, die Sie im klassischen Azure-Portal zum Erstellen und Verwalten von Vorlagen ausführen können, können Sie auch mithilfe von Windows PowerShell über die Befehlszeile durchführen. Darüber hinaus können Sie Vorlagen exportieren und importieren, sodass Sie Vorlagen zwischen Mandanten kopieren oder Massenbearbeitungen komplexer Eigenschaften in Vorlagen, z. B. von mehrsprachigen Namen und Beschreibungen, ausführen können.

Sie können das Exportieren und Importieren auch zum Sichern und Wiederherstellen der benutzerdefinierten Vorlagen verwenden. Als bewährte Methode wird empfohlen, regelmäßig eine Sicherungskopie der benutzerdefinierten Vorlagen zu erstellen. So können Sie jederzeit leicht zur vorherigen Version zurückwechseln, falls Sie einmal eine unbeabsichtigte Änderung vornehmen sollten.

> [!IMPORTANT]
> Um Windows PowerShell zum Erstellen und Verwalten von Azure RMS-Rechterichtlinienvorlagen zu verwenden, benötigen Sie mindestens Version 2.0.0.0 des [Windows PowerShell-Moduls für Azure RMS](http://go.microsoft.com/fwlink/?LinkId=257721).
> 
> Wenn Sie dieses Windows PowerShell-Modul bereits zuvor installiert hatten, führen Sie den folgenden Befehl in einem PowerShell-Fenster aus, um die Versionsnummer zu überprüfen: `(Get-Module aadrm -ListAvailable).Version`

Installationsanweisungen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](install-powershell.md).

Die Cmdlets, die das Erstellen und Verwalten von Vorlagen unterstützen:

-   [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)

-   [Expodert-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727078.aspx)

-   [Get-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727079.aspx)

-   [Get-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727081.aspx)

-   [Impodert-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727077.aspx)

-   [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)

-   [Remove-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727082.aspx)

-   [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)

## Nächste Schritte
Nachdem Sie benutzerdefinierte Vorlagen für Azure Rights Management konfiguriert haben, können Sie die [Roadmap für die Bereitstellung von Azure Rights Management](deployment-roadmap.md) verwenden, um herauszufinden, ob Sie vor dem Rollout von [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] für Benutzer und Administratoren weitere Konfigurationsschritte ausführen möchten. Wenn keine weiteren Konfigurationsschritte ausgeführt werden müssen, lesen Sie [Verwenden von Azure Rights Management](using-azure-rights-management.md), um Hilfestellung zum Betrieb zu erhalten, damit eine erfolgreiche Bereitstellung für Ihre Organisation unterstützt wird.

## Siehe auch
[Konfigurieren von Azure Rights Management](configuring-azure-rights-management.md)

<!--HONumber=Apr16_HO3-->


