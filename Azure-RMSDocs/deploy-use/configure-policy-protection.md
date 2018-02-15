---
title: "Konfigurieren einer Azure Information Protection-Bezeichnung für den Schutz"
description: "Sie können Ihre hochsensiblen Dokumente und E-Mails schützen, indem Sie eine Bezeichnung für die Verwendung des Rights Management-Schutzes konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: d42a561e61991a6299e83c5054ceb2ed8151ebf6
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>So konfigurieren Sie eine Bezeichnung für den Rights Management-Schutz

>*Gilt für: Azure Information Protection*

Sie können Ihre hochsensiblen Dokumente und E-Mails schützen, indem Sie einen Rights Management-Dienst verwenden. Dieser Dienst verwendet Verschlüsselung, Identität und Autorisierungsrichtlinien, um Datenverluste zu verhindern. Der Schutz wird mit einer Bezeichnung angewendet, die für die Verwendung des Rights Management-Schutzes für Dokumente und E-Mails konfiguriert ist. Benutzer können auch die Schaltfläche **Nicht weiterleiten** in Outlook verwenden. 

## <a name="how-the-protection-works"></a>So funktioniert der Schutz

Wenn Dokumente oder E-Mails durch einen Rights Management-Dienst geschützt sind, werden sie im Ruhezustand und während der Übertragung verschlüsselt. Sie können nur von autorisierten Benutzern entschlüsselt werden. Diese Verschlüsselung bleibt bei dem Dokument oder der E-Mail, auch wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und -einschränkungen konfigurieren, wie z.B. die folgenden:

- Nur Benutzer innerhalb Ihrer Organisation dürfen das vertrauliche Unternehmensdokument oder die vertrauliche Unternehmens-E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung dürfen ein Dokument oder eine E-Mail mit der Ankündigung einer Werbeaktion bearbeiten und drucken. Alle anderen Benutzer dürfen das Dokument bzw. die E-Mail nur lesen.

- Benutzer dürfen eine E-Mail nicht weiterleiten oder Informationen daraus kopieren, die Informationen zu einer internen Neuorganisation enthält.

- Eine aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem bestimmten Datum nicht mehr geöffnet werden.

Weitere Informationen zum Azure Rights Management-Schutz und seiner Funktionsweise finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Damit Sie eine Bezeichnung konfigurieren können, um diesen Schutz anzuwenden, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

Wenn durch eine Bezeichnung Schutz angewendet wird, ist das geschützte Dokument nicht zum Speichern auf SharePoint oder OneDrive geeignet. Diese Speicherorte unterstützen die folgenden Funktionen für geschützte Dateien nicht: gemeinsame Dokumenterstellung, Office Online, Suche, Dokumentvorschau, Miniaturansicht, eDiscovery und Verhinderung von Datenverlust (Data Loss Prevention, DLP). 

Exchange muss nicht für Information Rights Management (IRM) konfiguriert werden, bevor Benutzer Bezeichnungen in Outlook anwenden können, um ihre E-Mails zu schützen. Wenn Exchange allerdings nicht für IRM konfiguriert ist, können Sie nicht die volle Funktionalität des Azure Rights Management-Schutzes in Exchange nutzen. Einige Beispiele: Benutzer können geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook im Web anzeigen, geschützte E-Mails können nicht für die Suche indiziert werden, und Sie können Exchange Online DLP nicht für den Rights Management-Schutz konfigurieren. Informationen zum Konfigurieren von Exchange für die Unterstützung dieser zusätzlichen Szenarien finden Sie in den folgenden Quellen:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Für Exchange lokal müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](../deploy-use/deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-rights-management-protection"></a>So konfigurieren Sie eine Bezeichnung für den Rights Management-Schutz

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie beispielsweise im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gelten soll, bleiben Sie auf dem Blatt **Azure Information Protection – globale Richtlinie**. Wenn sich die zu konfigurierende Bezeichnung jedoch in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer gilt, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann auf dem Blatt **Azure Information Protection – bereichsbezogene Richtlinien** Ihre bereichsbezogene Richtlinie aus.

3. Wählen Sie die Bezeichnung aus, die Sie konfigurieren möchten. Daraufhin wird das Blatt **Bezeichnung** geöffnet. 

4. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus:
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit so konfiguriert ist, dass der Schutz angewendet wird, und Sie den Schutz durch diese Bezeichnung nicht mehr wünschen. Fahren Sie dann mit Schritt 11 fort.
    
    - **Schützen**: Wählen Sie diese Option aus, um den Schutz anzuwenden, und fahren Sie dann mit Schritt 5 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn ein Dokument oder eine E-Mail geschützt ist. Fahren Sie dann mit Schritt 11 fort.
        
        Beachten Sie, dass Benutzer, die eine Bezeichnung mit dieser Option anwenden möchten, über Berechtigungen zum Entfernen des Rights Management-Schutzes verfügen müssen. Diese Anforderung bedeutet, dass Benutzer über das [Nutzungsrecht](../deploy-use/configure-usage-rights.md) zum **Exportieren** oder für den **Vollzugriff** verfügen müssen. Alternativ dazu können die Benutzer auch Rights Management-Besitzer (damit wird das Nutzungsrecht „Vollzugriff“ automatisch gewährt) oder [Administrator für Azure Rights Management](../deploy-use/configure-super-users.md) sein. Die Azure Rights Management-Standardvorlagen beinhalten nicht die Nutzungsrechte, die es Benutzern erlauben, den Schutz zu entfernen. 
        
        Wenn Benutzer nicht über die Berechtigung zum Entfernen des Rights Management-Schutzes verfügen und eine Bezeichnung auswählen, die mit dieser Option **Schutz entfernen** konfiguriert ist, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Wenn das Problem weiterhin besteht, wenden Sie sich an Ihren Administrator.**

5. Wenn Sie **Schützen** ausgewählt haben, wählen Sie jetzt **Schutz** aus, um das Blatt **Schutz**  zu öffnen:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar-configured.png)

6. Wählen Sie auf dem Blatt **Schutz** entweder **Azure (Cloudschlüssel)** oder **HYOK (AD RMS)** aus.
    
    In den meisten Fällen werden Sie **Azure (Cloudschlüssel)** für Ihre Berechtigungseinstellungen auswählen. Wählen Sie **HYOK (AD RMS)** nur dann aus, wenn Sie die Voraussetzungen und Einschränkungen gelesen haben und genau kennen, die mit dieser *Hold Your Own Key*-Konfiguration (lokal gehosteter Schlüssel) einhergehen. Weitere Informationen finden Sie unter [Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz](configure-adrms-restrictions.md). Um die Konfiguration für HYOK (AD RMS) einzurichten, fahren Sie mit Schritt 10 fort.
    
7. Wählen Sie eine der folgenden Optionen aus:
    
    - **Berechtigungen festlegen**: Hiermit definieren Sie neue Schutzeinstellungen in diesem Portal.
    
    - **Benutzerdefinierte Berechtigungen festlegen (Vorschau)**: Hiermit ermöglichen Sie es Benutzern anzugeben, wem Berechtigungen gewährt werden sollen und was diese Berechtigungen umfassen. Sie können diese Option genauer definieren und „Nur Outlook“, „Word“, „Excel“, „PowerPoint“ oder „Datei-Explorer“ auswählen. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für die [automatische Klassifizierung](configure-policy-classification.md) konfiguriert ist.
        
        Bei Auswahl der Option für Outlook gilt Folgendes: Die Bezeichnung wird in Outlook angezeigt, und wenn Benutzer diese anwenden, ist das Verhalten das gleiche wie bei der Option „Nicht weiterleiten“.
        
        Bei Auswahl der Option für Word, Excel, PowerPoint und Datei-Explorer gilt Folgendes: Wenn diese Option festgelegt ist, wird die Bezeichnung in diesen Anwendungen angezeigt. Nachdem die Benutzer die Bezeichnung angewendet haben, wird ein Dialogfeld zur Auswahl von benutzerdefinierten Berechtigungen angezeigt. In diesem Dialogfeld müssen die Benutzer die Berechtigungen, die zutreffenden Benutzer oder Gruppen sowie möglicherweise ein Ablaufdatum angeben. Stellen Sie sicher, dass die Benutzer über die notwendigen Anweisungen und Anleitungen zum Bereitstellen dieser Werte verfügen.
    
    - **Vordefinierte Vorlage auswählen**: Hiermit wird nur eine der Standardvorlagen oder eine von Ihnen konfigurierte benutzerdefinierte Vorlage verwendet. Beachten Sie, dass diese Option nicht angezeigt wird, wenn Sie eine Bezeichnung bearbeiten, für die zuvor die Option **Berechtigungen festlegen** verwendet wurde.
    
    Damit Sie eine vordefinierte Vorlage auswählen können, muss die Vorlage veröffentlicht (nicht archiviert) sein und darf nicht bereits mit einer anderen Bezeichnung verknüpft sein. Wenn Sie diese Option auswählen, können Sie die Schaltfläche **Vorlage bearbeiten** verwenden, um [die Vorlage in eine Bezeichnung zu konvertieren](configure-policy-templates.md#to-convert-templates-to-labels).
    
    Tipp: Wenn Sie mit dem Erstellen und Bearbeiten benutzerdefinierter Vorlagen vertraut sind, finden Sie unter [Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben](migrate-portal.md) nützliche Informationen.

8. Wenn Sie **Berechtigungen festlegen** für **Azure (Cloudschlüssel)** ausgewählt haben, können Sie die gleichen Einstellungen konfigurieren wie in einer Vorlage. 
    
    Wählen Sie **Berechtigungen hinzufügen** aus. Auf dem Blatt **Berechtigungen hinzufügen** wählen Sie die erste Gruppe mit Benutzern und Gruppen aus, die über die Rechte verfügen sollen, die mit der ausgewählten Bezeichnung geschützten Inhalte zu verwenden:
    
    - Klicken Sie auf **Aus Liste auswählen**, um alle Benutzer aus Ihrer Organisation hinzuzufügen oder das Verzeichnis zu durchsuchen.
        
        Die Benutzer oder Gruppen müssen über E-Mail-Adressen verfügen. In einer Produktionsumgebung besitzen Benutzer und Gruppen fast immer E-Mail-Adressen, aber in einer einfachen Testumgebung müssen Sie Benutzerkonten oder Gruppen möglicherweise erst E-Mail-Adressen hinzufügen.
        
    - Wählen Sie **Details eingeben** aus, um manuell E-Mail-Adressen für einzelne Benutzer oder Gruppen (intern oder extern) anzugeben. Sie können diese Option auch dazu verwenden, alle Benutzer in einer anderen Organisation anzugeben, indem Sie einen Domänennamen für diese Organisation eingeben. Wenn Sie nur einen Domänennamen eingeben, verwenden Sie keinen Domänennamen eines Anbieters sozialer Netzwerke, der private E-Mail-Konten unterstützt. Geben Sie z.B. nicht **gmail.com**, **hotmail.com** oder **outlook.com** ein.
        
    >[!NOTE]
    >Wenn sich eine E-Mail-Adresse ändert, nachdem Sie den Benutzer oder die Gruppe ausgewählt haben, finden Sie im Abschnitt [Überlegungen für Azure Information Protection bei E-Mail-Adressänderungen](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) der Planungsdokumentation weitere Informationen.
    
    Verwenden Sie eher Gruppen als Benutzer. Mit dieser Strategie ist Ihre Konfiguration einfacher, und es ist weniger wahrscheinlich, dass Sie Ihre Bezeichnungskonfiguration später aktualisieren und den Inhaltsschutz erneut anwenden müssen. Wenn Sie jedoch die Gruppe ändern, denken Sie daran, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Wenn Sie die erste Gruppe mit Benutzern und Gruppen angegeben haben, wählen Sie die Berechtigungen aus, die diesen Benutzern und Gruppen gewährt werden sollen. Weitere Informationen zu den Berechtigungen, die Sie auswählen können, finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md). Bei den Anwendungen, die diesen Schutz unterstützen, kann es jedoch Unterschiede hinsichtlich der Implementierung dieser Berechtigungen geben. Lesen Sie die jeweilige Dokumentation, und führen Sie eigene Tests mit den Anwendungen durch, die von den Benutzern verwendet werden, um das Verhalten zu prüfen, bevor Sie die Vorlage für Benutzer bereitstellen.
    
    Falls erforderlich, können Sie jetzt eine zweite Gruppe mit Benutzern und Gruppen mit Nutzungsrechten hinzufügen. Wiederholen Sie den Vorgang, bis Sie alle Benutzer und Gruppen mit den jeweiligen Berechtigungen angegeben haben.

    >[!TIP]
    >Fügen Sie ggf. die benutzerdefinierte Berechtigung **Inhalt kopieren und extrahieren** hinzu, und weisen Sie diese Berechtigung Administratoren für die Datenwiederherstellung oder Mitarbeitern in anderen Rollen zu, die für die Wiederherstellung von Informationen zuständig sind. Falls erforderlich, können diese Benutzer dann den Schutz von Dateien und E-Mails entfernen, die mit dieser Bezeichnung oder Vorlage geschützt werden. Diese Möglichkeit zum Entfernen des Schutzes für ein Dokument oder eine E-Mail auf Berechtigungsebene bietet eine genauere Steuerung als die [Administratorfunktion](configure-super-users.md).
    
    Überprüfen Sie jetzt auf dem Blatt **Schutz** für alle angegebenen Benutzer und Gruppen, ob Sie Änderungen an den folgenden Einstellungen vornehmen möchten. Beachten Sie, dass diese Einstellungen – ebenso wie die Berechtigungen – weder für den [Rights Management-Aussteller und Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) noch für einen von Ihnen zugewiesenen [Administrator](configure-super-users.md) gelten.
    
    |Einstellung|Weitere Informationen|Empfohlene Einstellung
    |-----------|--------------------|--------------------|
    |**Inhaltsablauf**|Definieren Sie ein Datum oder eine Anzahl von Tagen, nach dem bzw. nach denen Dokumente oder E-Mails, die durch diese Einstellungen geschützt werden, für bestimmte Benutzer nicht mehr geöffnet werden sollen. Sie können ein Datum oder eine Anzahl von Tagen ab dem Zeitpunkt angeben, an dem der Schutz auf den Inhalt angewendet wird.<br /><br />Wenn Sie ein Datum angeben, beginnt die Gültigkeit um Mitternacht in Ihrer aktuellen Zeitzone.|**Inhalt läuft nie ab**, sofern für den Inhalt keine bestimmte zeitgebundene Begrenzung gilt.|
    |**Offlinezugriff zulassen**|Verwenden Sie diese Einstellung, um geltende Sicherheitsanforderungen (einschließlich Zugriff nach Widerruf) mit der Möglichkeit in Einklang zu bringen, ausgewählten Benutzern das Öffnen geschützter Inhalte zu gestatten, wenn keine Internetverbindung vorhanden ist.<br /><br />Wenn Sie angeben, dass für Inhalte eine Internetverbindung erforderlich ist oder Inhalte nur für eine bestimmte Anzahl von Tagen verfügbar sind und dieser Schwellenwert erreicht wird, müssen diese Benutzer erneut authentifiziert werden, und ihr Zugriff wird protokolliert. Wenn in diesem Fall die Anmeldeinformationen nicht zwischengespeichert wurden, werden die Benutzer aufgefordert, sich anzumelden, bevor sie das Dokument oder die E-Mail öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden Richtlinie und Mitgliedschaft in der Benutzergruppe erneut ausgewertet. Das bedeutet, dass Benutzer beim Zugriff auf das gleiche Dokument oder die gleiche E-Mail unterschiedliche Ergebnisse feststellen werden, wenn sich nach ihrem letzten Zugriff auf den Inhalt die Richtlinie oder Gruppenmitgliedschaft geändert hat. Dies könnte bedeuten, dass kein Zugriff möglich ist, wenn das Dokument [widerrufen](../rms-client/client-track-revoke.md) wurde.|Je nach Vertraulichkeit des Inhalts:<br /><br />- **Anzahl der Tage, die der Inhalt ohne Internetverbindung verfügbar ist** = **7** für vertrauliche Geschäftsdaten, die bei Freigabe an nicht autorisierte Personen dem Geschäft schaden könnten. Diese Empfehlung bietet einen ausgewogenen Kompromiss zwischen Flexibilität und Sicherheit. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebskontodaten.<br /><br />- **Nie** für sehr vertrauliche Geschäftsdaten, die bei Freigabe an nicht autorisierte Personen dem Geschäft schaden. Bei dieser Empfehlung wird der Sicherheit eine höhere Priorität eingeräumt als der Flexibilität. Diese Einstellung stellt sicher, dass bei Widerruf eines Dokuments der Zugriff auf das Dokument durch autorisierte Benutzer sofort gesperrt wird. Beispiele hierfür sind Mitarbeiter- und Kundendaten, Kennwörter, Quellcode und vorab angekündigte Finanzberichte.|
    
    Wenn Sie mit dem Konfigurieren der Berechtigungen fertig sind, klicken Sie auf **OK**. 
    
    Diese Gruppe von Einstellungen erstellt eine benutzerdefinierte Vorlage für den Azure Rights Management-Dienst. Diese Vorlagen können für Anwendungen und Dienste verwendet werden, die in Azure Rights Management integriert sind. Informationen zum Herunterladen und Aktualisieren dieser Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

9. Wenn Sie **Vordefinierte Vorlage auswählen** für **Azure (Cloudschlüssel)** ausgewählt haben, klicken Sie auf das Dropdownfeld und wählen die [Vorlage](../deploy-use/configure-policy-templates.md) aus, die Sie verwenden möchten, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen. Es werden keine archivierten Vorlagen oder Vorlagen angezeigt, die bereits für eine andere Bezeichnung ausgewählt wurden.
    
    Wenn Sie eine **Abteilungsvorlage** ausgewählt oder [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, gilt Folgendes:
    
    - Benutzer außerhalb des konfigurierten Bereichs der Vorlage oder Benutzer, die von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen wurden, sehen die Bezeichnung weiterhin, können sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Wenn das Problem weiterhin besteht, wenden Sie sich an Ihren Administrator.**
        
        Beachten Sie, dass alle veröffentlichten Vorlagen immer angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Ein Beispiel: Sie konfigurieren eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die zur Auswahl stehenden Vorlagen sind nicht auf diejenigen Vorlagen beschränkt, die nur für den Bereich der Gruppe „Marketing“ gelten, und es ist möglich, eine Abteilungsvorlage auszuwählen, die Ihre gewünschten Benutzer nicht verwenden können. Um die Konfiguration zu vereinfachen und potenzielle Probleme zu minimieren, sollten Sie erwägen, die Abteilungsvorlage entsprechend der Bezeichnung in Ihrer bereichsbezogenen Richtlinie zu benennen. 

10. Wenn Sie **HYOK (AD RMS)** ausgewählt haben, wählen Sie entweder **AD RMS-Vorlagendetails festlegen** oder **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus. Geben Sie dann die Lizenzierungs-URL Ihres AD RMS-Clusters an.
    
    Anweisungen zum Angeben einer Vorlagen-GUID und Ihrer Lizenzierungs-URL finden Sie unter [Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Mit der Option für benutzerdefinierte Berechtigungen können Benutzer angeben, wem Berechtigungen gewährt werden sollen und was diese Berechtigungen umfassen. Sie können diese Option genauer definieren und „Nur Outlook“ (Standardeinstellung), „Word“, „Excel“, „PowerPoint“ oder „Datei-Explorer“ auswählen. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für die [automatische Klassifizierung](configure-policy-classification.md) konfiguriert ist.
    
    Bei Auswahl der Option für Outlook gilt Folgendes: Die Bezeichnung wird in Outlook angezeigt, und wenn Benutzer diese anwenden, ist das Verhalten das gleiche wie bei der Option „Nicht weiterleiten“.
    
    Bei Auswahl der Option für Word, Excel, PowerPoint und Datei-Explorer, wird die Bezeichnung in diesen Anwendungen angezeigt. Nachdem die Benutzer die Bezeichnung angewendet haben, wird ein Dialogfeld zur Auswahl von benutzerdefinierten Berechtigungen angezeigt. In diesem Dialogfeld müssen die Benutzer die Berechtigungen, die zutreffenden Benutzer oder Gruppen sowie möglicherweise ein Ablaufdatum angeben. Stellen Sie sicher, dass die Benutzer über die notwendigen Anweisungen und Anleitungen zum Bereitstellen dieser Werte verfügen. Beachten Sie Folgendes: Sofern Sie nicht die Vorschauversion des Clients verwenden, nutzt diese Option für den Datei-Explorer immer den Azure RMS-Schutz, nicht den Schutz über HYOK (AD RMS).

11. Klicken Sie auf **OK**, um das Blatt **Schutz** zu schließen. Es wird Ihre Auswahl an **benutzerdefinierten** Einstellungen oder Ihre ausgewählte Vorlage für die Option **Schutz** auf dem Blatt **Bezeichnung** angezeigt.

12. Klicken Sie auf dem Blatt **Bezeichnung** auf **Speichern**.

13. Verwenden Sie auf dem Blatt **Azure Information Protection** die Spalte **SCHUTZ**, um zu überprüfen, ob Ihre Bezeichnung jetzt die gewünschte Schutzeinstellung anzeigt:
    
    - Ein Häkchen, wenn Sie den Schutz konfiguriert haben 
    
    - Ein X zum Kennzeichnen eines Abbruchs, wenn Sie eine Bezeichnung zum Entfernen des Schutzes konfiguriert haben
    
    - Ein leeres Feld, wenn der Schutz nicht eingerichtet ist 

13. Um Ihre Änderungen den Benutzern zur Verfügung zu stellen, klicken Sie auf **Veröffentlichen**.

## <a name="example-configurations"></a>Beispielkonfigurationen

Die untergeordneten Bezeichnungen **Alle Mitarbeiter** und **Nur Empfänger** der Bezeichnungen **Vertraulich** und **Streng vertraulich** aus der [Standardrichtlinie](configure-policy-default.md) bieten Beispiele dafür, wie Sie Bezeichnungen zum Anwenden des Schutzes konfigurieren können. Sie können auch die folgenden Beispiele verwenden, um den Schutz für verschiedene Szenarien zu konfigurieren. 

Wählen Sie bei jedem der folgenden Beispiele auf dem Blatt \<*Name der Bezeichnung*> nacheinander die Optionen **Schützen** und **Schutz** aus, um das Blatt **Schutz** zu öffnen.

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Beispiel 1: Bezeichnung, die „Nicht weiterleiten“ anwendet, um eine geschützte E-Mail an ein Gmail-Konto zu senden

Diese Bezeichnung ist nur in Outlook verfügbar und eignet sich in Fällen, in denen Exchange Online für die [neuen Funktionen bei der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist. Weisen Sie Ihre Benutzer an, diese Bezeichnung auszuwählen, wenn sie eine geschützte E-Mail an Personen senden müssen, die ein Gmail-Konto (oder ein anderes E-Mail-Konto außerhalb Ihrer Organisation) verwenden. 

Die Benutzer geben die Gmail-Adresse in das Feld **An** ein.  Danach wählen sie die Bezeichnung aus, und die Option „Nicht weiterleiten“ wird der E-Mail automatisch hinzugefügt. Dies führt dazu, dass die Empfänger die E-Mail weder weiterleiten noch drucken oder Inhalte daraus kopieren, Anhänge speichern oder die E-Mail unter einem anderen Namen speichern können. 

1. Stellen Sie auf dem Blatt **Schutz** sicher, dass **Azure (Cloudschlüssel)** ausgewählt ist.
    
2. Wählen Sie **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus.

3. Stellen Sie sicher, dass die folgende Option ausgewählt ist: **"Nicht weiterleiten" in Outlook anwenden**.

4. Deaktivieren Sie die folgende Option, falls sie ausgewählt ist: **Benutzer in Word, Excel, PowerPoint und Datei-Explorer zur Angabe von benutzerdefinierten Berechtigungen auffordern**.

5. Klicken Sie auf dem Blatt **Schutz** auf **OK**, und veröffentlichen Sie Ihre Änderungen.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Beispiel 2: Bezeichnung, die den Schreibschutz auf alle Benutzer in einer anderen Organisation anwendet und den sofortigen Widerruf unterstützt

Diese Bezeichnung eignet sich für die (schreibgeschützte) Freigabe streng vertraulicher Dokumente, für deren Ansicht immer eine Internetverbindung erforderlich ist. Wenn ein solches Dokument widerrufen wird, kann es von Benutzern nicht mehr angezeigt werden, wenn diese versuchen, es erneut zu öffnen.

Diese Bezeichnung eignet sich nicht für E-Mails.

1. Stellen Sie auf dem Blatt **Schutz** sicher, dass **Azure (Cloudschlüssel)** ausgewählt ist.
    
2. Stellen Sie sicher, dass die Option **Berechtigungen festlegen** ausgewählt ist, und wählen Sie dann **Berechtigungen hinzufügen** aus.

3. Wählen Sie auf dem Blatt **Berechtigungen hinzufügen** die Option **Details eingeben** aus.

4. Geben Sie den Namen einer Domäne der anderen Organisation ein, z.B. **fabrikam.com**. Klicken Sie anschließend auf **Hinzufügen**.

5. Wählen Sie unter **Berechtigungen aus Voreinstellung auswählen** die Option **Viewer** aus, und klicken Sie dann auf **OK**.

6. Wählen Sie auf dem Blatt **Schutz** für die Einstellung **Offlinezugriff zulassen** die Option **Nie** aus.

7. Klicken Sie auf dem Blatt **Schutz** auf **OK**, und veröffentlichen Sie Ihre Änderungen.


### <a name="example-3-add-external-users-to-an-existing-label"></a>Beispiel 3: Hinzufügen externer Benutzer zu einer vorhandenen Bezeichnung

Die von Ihnen hinzugefügten neuen Benutzer können Dokumente und E-Mails öffnen, die bereits mit dieser Bezeichnung geschützt sind. Die Berechtigungen, die Sie diesen Benutzern zuweisen, können sich von den Berechtigungen unterscheiden, über die vorhandene Benutzer verfügen.

1. Stellen Sie auf dem Blatt **Schutz** sicher, dass **Azure (Cloudschlüssel)** ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und wählen Sie dann **Berechtigungen hinzufügen** aus.

3. Wählen Sie auf dem Blatt **Berechtigungen hinzufügen** die Option **Details eingeben** aus.

4. Geben Sie die E-Mail-Adresse des ersten Benutzers oder der ersten Gruppe ein, den bzw. die Sie hinzufügen möchten, und wählen Sie dann **Hinzufügen** aus.

5. Wählen Sie die Berechtigungen für diesen Benutzer bzw. diese Gruppe aus.

6. Wiederholen Sie die Schritte 4 und 5 für jeden Benutzer oder jede Gruppe, den bzw. die Sie dieser Bezeichnung hinzufügen möchten. Klicken Sie dann auf **OK**.

7. Klicken Sie auf dem Blatt **Schutz** auf **OK**, und veröffentlichen Sie Ihre Änderungen.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Beispiel 4: Bezeichnung für geschützte E-Mails, die weniger restriktive Berechtigungen als „Nicht weiterleiten“ unterstützt

Diese Bezeichnung kann nicht auf Outlook beschränkt werden, bietet jedoch eine weniger restriktive Steuerung als „Nicht weiterleiten“. Sie eignet sich z.B. dann, wenn Sie möchten, dass die Empfänger Inhalte aus der E-Mail oder einem Anhang kopieren oder einen Anhang drucken und speichern können. Wenn Sie externe Benutzer angeben, die kein Konto in Azure AD besitzen, stellen Sie sicher, dass Sie Ihre Benutzer anweisen, diese Bezeichnung nur für E-Mails zu verwenden, nicht für Dokumente. Um diese externen Benutzer zu unterstützen, muss Exchange Online für die [neuen Funktionen bei der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert werden.  

Wenn Ihre Benutzer die E-Mail-Adressen im Feld **An** angeben, müssen die Adressen zu den Benutzern gehören, die Sie für diese Bezeichnungskonfiguration angegeben haben. Da Benutzer zu Gruppen gehören und über mehrere E-Mail-Adressen verfügen können, muss die E-Mail-Adresse, die sie verwenden, nicht mit der E-Mail-Adresse übereinstimmen, die Sie für die Berechtigungen angegeben haben. Die Angabe derselben E-Mail-Adresse ist jedoch die einfachste Möglichkeit, um sicherzustellen, dass der Empfänger erfolgreich autorisiert wird. Weitere Informationen dazu, wie Benutzer für Berechtigungen autorisiert werden, finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](../plan-design/prepare.md). 

1. Stellen Sie auf dem Blatt **Schutz** sicher, dass **Azure (Cloudschlüssel)** ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und wählen Sie dann **Berechtigungen hinzufügen** aus.

3. Gehen Sie auf dem Blatt **Berechtigungen hinzufügen** folgendermaßen vor: Wenn Sie Benutzern in Ihrer Organisation Berechtigungen gewähren, klicken Sie auf **\<Name der Organisation> hinzufügen – alle Mitglieder**, um alle Benutzer in Ihrem Mandanten auszuwählen, oder klicken Sie auf **Verzeichnis durchsuchen**, um eine bestimmte Gruppe auszuwählen. Wenn Sie externen Benutzern Berechtigungen gewähren oder die E-Mail-Adressen lieber eingeben möchten, wählen Sie **Details eingeben** aus, und geben Sie die E-Mail-Adresse des Benutzers oder der Azure AD-Gruppe ein.
    
    Wiederholen Sie diesen Schritt, um weitere Benutzer anzugeben, die über die gleichen Berechtigungen verfügen sollen.

4. Klicken Sie unter **Berechtigungen aus Voreinstellung auswählen** auf **Mitbesitzer**, **Mitautor**, **Prüfer** oder **Benutzerdefiniert**, um die gewünschten Berechtigungen auszuwählen. 
    
    Hinweis: Wählen Sie für E-Mails nicht **Viewer** aus, und wenn Sie **Benutzerdefiniert** auswählen, stellen Sie sicher, dass Sie die Berechtigung **Bearbeiten und speichern** einschließen. 

5. Um weitere Benutzer anzugeben, die über unterschiedliche Berechtigungen verfügen sollen, wiederholen Sie die Schritte 3 und 4.

6. Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** auf **OK**. 

7. Klicken Sie auf dem Blatt **Schutz** auf **OK**, und veröffentlichen Sie Ihre Änderungen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]