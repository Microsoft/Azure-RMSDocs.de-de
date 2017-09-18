---
title: "Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung"
description: "Beim Konfigurieren einer Bezeichnung zur Verwendung von Rights Management-Schutz können Sie Ihre sensibelsten Dokumente und E-Mails schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: fce3c905f2f48c2723ee7f0b55ff5ddb77f6258a
ms.sourcegitcommit: 94a9b6714c555b95f6064088e77ed94f08224a15
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/13/2017
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurieren einer Bezeichnung für Rights Management-Schutz

>*Gilt für: Azure Information Protection*

Sie können Ihre sensibelsten Dokumente und E-Mails mithilfe des Rights Management-Diensts schützen. Dieser Dienst verwendet Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien, um Datenverlust zu verhindern. Der Schutz wird angewendet, wenn Sie eine Bezeichnung so konfigurieren, dass sie Rights Management-Schutz für Dokumente und E-Mails oder die Option **Nicht weiterleiten** für Outlook-E-Mail-Nachrichten verwendet. 

## <a name="how-the-protection-works"></a>Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail mit Rights Management geschützt wird, werden die Inhalte in ruhendem Zustand und während der Übertragung verschlüsselt. Eine Entschlüsselung ist nur durch autorisierte Benutzer möglich. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das vertrauliche, geschäftliche Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail zu einer bevorstehenden Werbeaktion bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich lesen.

- Benutzer können keine E-Mails weiterleiten oder darin enthaltene Informationen kopieren, die Nachrichten über eine interne Neuorganisation enthalten.

- Die aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zum Azure Rights Management-Schutz und dessen Funktionsweise finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung dieses Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Wenn Sie den Dienst noch nicht aktiviert haben, finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md) weitere Informationen.

Wenn die Bezeichnung Schutz anwendet, ist ein geschütztes Dokument nicht für die Speicherung auf SharePoint oder OneDrive geeignet. Diese Speicherorte unterstützen für geschützte Dateien keine gemeinsame Dokumentenerstellung, Office Online, Suche, Dokumentvorschau, Vorschauminiatur, eDiscovery und Verhinderung von Datenverlust (Data Loss Prevention, DLP). 

Exchange muss für Information Rights Management (IRM) nicht konfiguriert sein, damit Benutzer in Outlook Bezeichnungen zum Schutz ihrer E-Mails verwenden können. Sie können jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn Exchange für IRM konfiguriert ist. Ohne diese Konfiguration können Benutzer beispielsweise geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook im Web anzeigen, derartige E-Mails können nicht für die Suche indiziert werden, und Sie können Exchange Online DLP nicht für den Rights Management-Schutz konfigurieren. Weitere Informationen zum Konfigurieren von Exchange, um diese zusätzlichen Szenarien zu unterstützen, finden Sie in den folgenden Ressourcen:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Für lokales Exchange müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](../deploy-use/deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-rights-management-protection"></a>Konfigurieren einer Bezeichnung für Rights Management-Schutz

1. Sofern nicht bereits geschehen, öffnen Sie ein neues Browserfenster, und melden Sie sich als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Weitere Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Wenn die zu konfigurierende Bezeichnung für alle Benutzer gilt, bleiben Sie auf dem Blatt **Azure Information Protection - Global policy** (Azure Information Protection – Globale Richtlinien). Wenn sich die Bezeichnung, die Sie konfigurieren möchten, jedoch in einer [bereichsbezogenen Richtlinie](configure-policy-scope.md) befindet, sodass sie nur für ausgewählte Benutzer zutrifft, klicken Sie in der Menüauswahl **RICHTLINIEN** auf **Bereichsbezogene Richtlinien**. Wählen Sie dann Ihre bereichsbezogene Richtlinie auf dem Blatt **Azure Information Protection - Scoped policies** (Azure Information Protection – Bereichsbezogene Richtlinien).

3. Wählen die Bezeichnung aus, die Sie konfigurieren möchten. Dadurch wird das Blatt **Bezeichnung** geöffnet. 

4. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus.
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit zum Anwenden von Schutz konfiguriert ist und die ausgewählte Bezeichnung keinen Schutz mehr anwenden soll. Fahren Sie dann mit Schritt 11 fort.
    
    - **Schützen**: Wählen Sie diese Option aus, um Schutz anzuwenden, und fahren Sie dann mit Schritt 5 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn ein Dokument oder eine E-Mail-Adresse geschützt ist. Fahren Sie dann mit Schritt 11 fort.
        
        Beachten Sie, dass Benutzer zum Anwenden einer Bezeichnung mit dieser Option die Berechtigungen benötigen, um den Rights Management-Schutz zu entfernen. Diese Anforderung bedeutet, dass Benutzer über das **Nutzungsrecht** **Exportieren** oder [Vollzugriff](../deploy-use/configure-usage-rights.md) verfügen müssen. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](../deploy-use/configure-super-users.md) fungieren. Die Azure Rights Management-Standardvorlagen umfassen nicht die Nutzungsrechte, die Benutzer zum Aufheben des Schutzes benötigen. 
        
        Wenn ein Benutzer keine Berechtigungen zum Entfernen des Rights Management-Schutzes hat und eine mit der Option **Schutz entfernen** konfigurierte Bezeichnung auswählt, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**

5. Wenn Sie **Schützen** ausgewählt haben, klicken Sie jetzt auf **Schutz**, um das Blatt **Schutz** zu öffnen:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar-configured.png)

6. Wählen Sie auf dem Blatt **Schutz** die Option **Azure RMS** oder **Azure (cloud key)** (Azure (Cloud-Schlüssel)) aus, oder wählen Sie **HYOK (AD RMS)** aus. Die erste Option wird zurzeit umbenannt.
    
    In den meisten Fällen wählen Sie **Azure RMS** oder **Azure (cloud key)** für Ihre Berechtigungseinstellungen. Wählen Sie nicht **HYOK (AD RMS)** aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser „*Hold-your-own-key*“-Konfiguration (HYOK) einhergehen. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz). Um mit der Konfiguration für HYOK (AD RMS) fortzufahren, wechseln Sie zu Schritt 10.
    
7. Wählen Sie eine der folgenden Optionen aus:
    
    - **Vordefinierte Vorlage auswählen**: Zum Verwenden einer der Standardvorlagen oder einer benutzerdefinierten Vorlage, die Sie konfiguriert haben. Diese Vorlage muss veröffentlicht werden (nicht archiviert) und darf nicht bereits mit einer anderen Bezeichnung verknüpft werden. Wenn Sie diese Option auswählen, können Sie die Schaltfläche **Vorlage bearbeiten** verwenden, um [die Vorlage in eine Bezeichnung umzuwandeln](configure-policy-templates.md#to-convert-templates-to-labels).
    
    - **Berechtigungen festlegen**: Definieren neuer Schutzeinstellungen in diesem Portal.
    
    - **Festlegen benutzerdefinierter Berechtigungen (Vorschauversion)**: Benutzer können angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option dann verfeinern und nur Outlook wählen (Standardeinstellung) oder Word, Excel, PowerPoint und den Datei-Explorer. 
        
        Wenn Sie die Option für Outlook wählen: Die Bezeichnung wird in Outlook angezeigt und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das gleiche wie bei der Option „Nicht weiterleiten“.
        
        Wenn Sie die Option für Word, Excel, PowerPoint und den Datei-Explorer wählen: Diese Option erfordert die Vorschauversion des Azure Information Protection-Clients. Wenn diese Option festgelegt ist und Benutzer den Client der Vorschauversion besitzen, wird die Bezeichnung in diesen Anwendungen angezeigt. Das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das Anzeigen des Dialogfelds, in dem die Benutzer die benutzerdefinierten Berechtigungen auswählen können. In diesem Dialogfeld müssen Benutzer die Berechtigungen, die Benutzer oder Gruppen und ein beliebiges Ablaufdatum angeben. Versichern Sie sich, dass die Benutzer über die Anweisungen und den Leitfaden zum Bereitstellen dieser Werte verfügen.

8. Falls Sie **Vordefinierte Vorlage auswählen** für **Azure RMS** oder **Azure (cloud key)** ausgewählt haben, klicken Sie im Dropdownfeld auf die [Vorlage](../deploy-use/configure-policy-templates.md), die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen. Archivierte Vorlagen oder Vorlagen, die bereits für eine andere Bezeichnung ausgewählt wurden, werden nicht angezeigt.
    
    Bei Auswahl einer **Abteilungsvorlage** oder wenn Sie [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
    - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**
        
        Beachten Sie, dass immer alle veröffentlichten Vorlagen angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Konfigurieren Sie z. B. eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die Vorlagen, die Sie auswählen können, sind nicht auf Vorlagen beschränkt, die auf den Bereich „Marketing“ bezogen sind, und es ist möglich, eine abteilungsbezogene Vorlage auszuwählen, die Ihre ausgewählten Benutzer nicht verwenden können. Zur Vereinfachung der Konfiguration und zum Minimieren der Problembehandlung können Sie die Abteilungsvorlage gemäß der Bezeichnung in der bereichsbezogenen Richtlinie benennen. 
            
9. Wenn Sie **Festlegen von Berechtigungen** für **Azure RMS** oder **Azure (cloud key)** ausgewählt haben, können Sie durch diese Option die gleichen Einstellungen konfigurieren, die Sie in einer Vorlage konfigurieren können. 
    
    Wählen Sie **Berechtigungen hinzufügen**, und wählen Sie auf dem Blatt **Berechtigungen hinzufügen** den ersten Satz von Benutzern und Gruppen, der die Rechte besitzt, den von der ausgewählten Bezeichnung geschützten Inhalt zu nutzen:
    
    - Wählen Sie **Aus der Liste auswählen** aus, um alle Benutzer von Ihrer Organisation hinzuzufügen oder um sich das Verzeichnis anzusehen.
        
        Die Benutzer oder Gruppen müssen über eine E-Mail-Adresse verfügen. In einer Produktionsumgebung ist dies praktisch immer der Fall, aber in einer einfachen Testumgebung müssen Sie eventuell Benutzerkonten oder Gruppen E-Mail-Adressen hinzufügen.
        
    - Wählen Sie **Details eingeben** aus, um manuell E-Mail-Adressen für einzelne Benutzer oder Gruppen (intern oder extern) anzugeben. Sie können dies auch tun, um alternativ alle Benutzer in einer Organisation durch die Eingabe eines Domänennamens aus dieser Organisation anzugeben. 
        
    >[!NOTE]
    >Wenn sich eine E-Mail-Adresse ändert, nachdem Sie den Benutzer oder die Gruppe ausgewählt haben, lesen Sie die Informationen im Abschnitt [Überlegungen bei einer Änderung der E-Mail-Adressen](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) in der Planungsdokumentation.
    
    Als bewährte Methode verwenden Sie Gruppen statt Benutzer. Durch diese Strategie bleibt Ihre Konfiguration einfacher, und Sie müssen später wahrscheinlich nicht Ihre Bezeichnungskonfiguration aktualisieren und den Inhalt erneut schützen. Wenn Sie jedoch Änderungen an der Gruppe durchführen, denken Sie daran, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](../plan-design/prepare.md#group-membership-caching-by-azure-rights-management ). 
    
    Wenn Sie den ersten Satz von Benutzern und Gruppen angegeben haben, wählen Sie die Berechtigungen aus, die für diese Benutzer und Gruppen gewährt werden sollen. Weitere Informationen zu den Berechtigungen, die Sie auswählen können, finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md). Anwendungen, die diesen Schutz unterstützen, unterscheiden sich jedoch möglicherweise darin, wie sie diese Berechtigungen implementieren. Lesen Sie die Dokumentationen der Anwendungen, und führen Sie eigene Tests mit den Anwendungen aus, die von Benutzer verwendet werden, um das Verhalten zu überprüfen, bevor Sie die Vorlage für Benutzer bereitstellen.
    
    Falls erforderlich, können Sie jetzt einen zweiten Satz von Benutzern und Gruppen mit Nutzungsrechten hinzufügen. Wiederholen Sie diesen Prozess, bis Sie alle Benutzer und Gruppen mit den jeweiligen Berechtigungen angegeben haben.

    >[!TIP]
    >Fügen Sie ggf. die benutzerdefinierte Berechtigung **Inhalt kopieren und extrahieren** hinzu, und gewähren Sie es Administratoren für Datenwiederherstellung oder Mitarbeitern in anderen Rollen, die für die Informationswiederherstellung verantwortlich sind. Falls nötig können diese Benutzer dann den Schutz für Dateien und E-Mails entfernen, die mithilfe dieser Bezeichnung oder Vorlage geschützt werden. Diese Fähigkeit zum Entfernen des Schutzes auf Berechtigungsebene für ein Dokument oder eine E-Mail bietet eine präzisere Kontrolle als die [Administratorfunktion](configure-super-users.md).
    
    Überprüfen Sie nun auf dem Blatt **Schutz** für alle Benutzer und Gruppen, die Sie angegeben haben, ob Sie Änderungen an folgenden Einstellungen vornehmen möchten. Beachten Sie, dass diese Einstellungen wie bei den Berechtigungen nicht für den [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder einen beliebigen zugewiesenen [Administrator](configure-super-users.md) gelten.
    
    |Einstellung|Weitere Informationen|Empfohlene Einstellung
    |-----------|--------------------|--------------------|
    |**Inhalt läuft ab am**|Definieren Sie ein Datum oder eine Anzahl von Tagen für diese Vorlage, nach deren Ablauf Dokumente oder E-Mails, die durch diese Vorlage geschützt sind, nicht mehr von ausgewählten Benutzern geöffnet werden sollen. Sie können ein Datum oder eine Anzahl von Tagen beginnend ab dem Zeitpunkt angeben, an dem der Schutz auf den Inhalt angewendet wird.<br /><br />Wenn Sie ein Datum angeben, wird der Schutz ab Mitternacht in Ihrer aktuellen Zeitzone wirksam.|**Inhalt läuft nie ab**, sofern für den Inhalt keine bestimmten zeitgebundenen Anforderungen vorliegen.|
    |**Offlinezugriff zulassen**|Mit dieser Einstellung können Sie Ihre bestehenden Sicherheitsanforderungen abstimmen (einschließlich des Zugriffs nach einem Widerruf) mit der Möglichkeit für ausgewählte Benutzer, geschützte Inhalte zu öffnen, wenn keine Internetverbindung besteht.<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich diese Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und ihre Zugriffe werden protokolliert. Wenn ihre Anmeldeinformationen nicht zwischengespeichert wurden, werden Benutzer in diesem Fall aufgefordert, sich anzumelden, bevor sie das Dokument oder die E-Mail öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden die Richtlinie und die Benutzergruppenmitgliedschaft erneut ausgewertet. Dies bedeutet, dass es bei Benutzern für dasselbe Dokument oder dieselbe E-Mail zu unterschiedlichen Zugriffsergebnissen kommen kann, wenn sich seit ihrem letzten Zugriff auf den Inhalt Änderungen an der Richtlinie oder ihrer Gruppenmitgliedschaft ereignet haben. Dies könnte dazu führen, dass der Zugriff verweigert wird, wenn das Dokument [widerrufen](../rms-client/client-track-revoke.md) wurde.|Je nach Wichtigkeit des Inhalts:<br /><br />- **Anzahl der Tage, die der Inhalt ohne Internetverbindung verfügbar ist** = **7** für sensible Geschäftsdaten, die dem Unternehmen schaden können, wenn sie an unbefugte Personen weitergegeben werden. Diese Empfehlung bietet einen ausgewogenen Kompromiss zwischen Flexibilität und Sicherheit. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebsdaten.<br /><br />- **Nie** bei sehr sensiblen Geschäftsdaten, die dem Unternehmen schaden würden, wenn sie an Unbefugte weitergegeben werden. Diese Empfehlung räumt der Sicherheit Vorrang gegenüber Flexibilität ein und stellt sicher, dass unmittelbar nach einem Widerruf des Dokument keine der autorisierten Benutzer das Dokument öffnen können. Beispiele hierfür sind Mitarbeiter- und Kundeninformationen, Kennwörter, Quellcode und vorangekündigte Finanzberichte.|
    
    Wenn Sie das Konfigurieren der Berechtigungen abgeschlossen haben, klicken Sie auf **OK**. 
    
    Bei dieser Gruppierung von Einstellungen wird eine benutzerdefinierte Vorlage für den Azure Rights Management-Dienst erstellt. Diese Vorlagen können in Anwendungen und Diensten verwendet werden, die in Azure Rights Management integriert sind. Informationen zum Herunterladen und Aktualisieren dieser Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

10. Wenn Sie **HYOK (AD RMS)** ausgewählt haben, klicken Sie entweder auf **Set AD RMS templates details** (Festlegen von Vorlagendetails für AD RMS) oder auf **Benutzerdefinierte Berechtigungen festlegen (Vorschau)**, und geben Sie dann die Lizenzierungs-URL Ihres AD RMS-Clusters an.
    
    Anweisungen zum Angeben einer Vorlagen-GUID oder Ihrer Lizenzierungs-URL finden Sie unter [Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Sie müssen die Vorschauversion des Azure Information Protection-Clients besitzen, um die Option für benutzerdefinierte Berechtigungen zu verwenden. Durch diese Option können Benutzer angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option dann verfeinern und nur Outlook wählen (Standardeinstellung) oder Word, Excel, PowerPoint und den Datei-Explorer. 
    
    Wenn Sie die Option für Outlook wählen: Die Bezeichnung wird in Outlook angezeigt und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das gleiche wie bei der Option „Nicht weiterleiten“.
    
    Wenn Sie die Option für Word, Excel, PowerPoint und den Datei-Explorer wählen: Die Bezeichnung wird in diesen Anwendungen angezeigt. Das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das Anzeigen des Dialogfelds, in dem die Benutzer die benutzerdefinierten Berechtigungen auswählen können. In diesem Dialogfeld müssen Benutzer die Berechtigungen, die Benutzer oder Gruppen und ein beliebiges Ablaufdatum angeben. Versichern Sie sich, dass die Benutzer über die Anweisungen und den Leitfaden zum Bereitstellen dieser Werte verfügen. Derzeit verwendet diese Option im Datei-Explorer immer den Azure RMS-Schutz statt dem HYOK-Schutz (AD RMS).

11. Klicken Sie auf **OK**, um das Blatt **Schutz** zu schließen und die Auswahl für **Nicht weiterleiten** bzw. die ausgewählte Vorlage für die Option **Schutz** auf dem Blatt **Bezeichnung** anzuzeigen.

12. Klicken Sie auf dem Blatt **Bezeichnung** auf **Speichern**.

13. Verwenden Sie auf dem Blatt **Azure Information Protection** die Spalte **PROTECTION** (Schutz), um zu bestätigen, dass Ihre Bezeichnung nun die gewünschten Schutzeinstellungen darstellt:
    
    - **Azure RMS** oder **HYOK (AD RMS)** oder ein Häkchen, falls Sie den Schutz konfiguriert haben. 
    
    - **Schutz entfernen** oder das Zeichen „x“, um den Abbruch anzugeben, wenn Sie eine Bezeichnung zum Entfernen von Schutz konfiguriert haben.
    
    - Ein leeres Feld, wenn der Schutz nicht festgelegt ist. 

13. Klicken Sie auf **Publish** (Veröffentlichen), um Ihre Änderungen für Benutzer verfügbar zu machen.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]