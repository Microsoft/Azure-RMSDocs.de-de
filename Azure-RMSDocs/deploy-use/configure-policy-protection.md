---
title: Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung
description: Beim Konfigurieren einer Bezeichnung zur Verwendung von Rights Management-Schutz können Sie Ihre sensibelsten Dokumente und E-Mails schützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.openlocfilehash: 00305b1ba4f9ff750dd0fde9eb6a524cead39094
ms.sourcegitcommit: aae04d78ff301921a4e29ac23bd932fb24a83dbe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/22/2018
ms.locfileid: "34444213"
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurieren einer Bezeichnung für Rights Management-Schutz

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Sie können Ihre sensibelsten Dokumente und E-Mails mithilfe des Rights Management-Diensts schützen. Dieser Dienst verwendet Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien, um Datenverlust zu verhindern. Der Schutz wird mit einer Bezeichnung angewendet, die so konfiguriert ist, dass der Rights Management-Schutz für Dokumente und E-Mails verwendet wird, und Benutzer können auch auf die Schaltfläche **Nicht weiterleiten** in Outlook klicken.

Wenn eine Bezeichnung mit der Schutzeinstellung **Azure (Cloud-Schlüssel)** konfiguriert wird, wird hierdurch im Hintergrund eine Schutzvorlage erstellt und eingerichtet. Auf diese kann dann über Dienste und Anwendungen zugegriffen werden, die in die Rights Management-Vorlagen integriert sind. Beispiele sind Exchange Online mit Regeln für den E-Mail-Fluss sowie Outlook on the Web. 

## <a name="how-the-protection-works"></a>Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail von einem Rights Management-Dienst geschützt wird, wird es oder sie im Ruhezustand und während der Übertragung verschlüsselt. Die Entschlüsselung kann dann nur durch einen autorisierten Benutzer erfolgen. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das vertrauliche, geschäftliche Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail zu einer bevorstehenden Werbeaktion bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich lesen.

- Benutzer können keine E-Mails weiterleiten oder darin enthaltene Informationen kopieren, die Nachrichten über eine interne Neuorganisation enthalten.

- Die aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zum Azure Rights Management-Schutz und dessen Funktionsweise finden Sie unter [Was ist Azure Rights Management?](../understand-explore/what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung dieses Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

Wenn die Bezeichnung Schutz anwendet, ist ein geschütztes Dokument nicht für die Speicherung auf SharePoint oder OneDrive geeignet. Diese Speicherorte unterstützen die folgenden Features für geschützte Dateien nicht: gemeinsame Dokumentenerstellung, Office Online, Suche, Dokumentvorschau, Vorschauminiatur, eDiscovery und Verhinderung von Datenverlust (Data Loss Prevention, DLP). 

Exchange muss für Azure Information Protection nicht konfiguriert werden, damit Benutzer in Outlook Bezeichnungen zum Schutz ihrer E-Mails verwenden können. Sie können jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn für Azure Information Protection Exchange konfiguriert wird. Ohne diese Konfiguration können Benutzer beispielsweise geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook im Web anzeigen, derartige E-Mails können nicht für die Suche indiziert werden, und Sie können für Exchange Online DLP nicht den Rights Management-Schutz konfigurieren. In den folgenden Artikeln erhalten Sie Informationen, mit denen Sie sicherstellen können, dass Exchange diese zusätzlichen Szenarios unterstützt:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration).

- Für lokales Exchange müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](../deploy-use/deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-protection-settings"></a>So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Blatt **Azure Information Protection**. 
    
    Klicken Sie z.B. im Hubmenü auf **Alle Dienste**, und geben Sie im Filterfeld den Begriff **Information** ein. Wählen Sie **Azure Information Protection** aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen**: Wählen Sie auf dem Blatt **Azure Information Protection: Bezeichnungen** die Bezeichnung aus, die Sie ändern möchten. 

3. Suchen Sie auf dem Blatt **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus:
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit zum Anwenden von Schutz konfiguriert ist und die ausgewählte Bezeichnung keinen Schutz mehr anwenden soll. Fahren Sie dann mit Schritt 11 fort.
        
        Die bereits konfigurierten Schutzeinstellungen werden in Form einer archivierten Schutzvorlage beibehalten und werden angezeigt, wenn Sie die Option wieder in **Protect** (Schützen) ändern. Diese Vorlage sehen Sie nicht im Azure-Portal. Sie können die Vorlage aber über [PowerShell](configure-templates-with-powershell.md) verwalten. Das bedeutet, dass Inhalt weiterhin zugänglich ist, wenn er über diese Bezeichnung und die zuvor angewendeten Schutzeinstellungen verfügt.
    
    - **Schützen**: Wählen Sie diese Option aus, um Schutz anzuwenden, und konfigurieren Sie sie wie in Schritt 5 beschrieben.
    
    Hinweis: Sie können eine neue Bezeichnung auch ohne weitere Konfiguration speichern. Wenn Sie dies tun, ist sie so konfiguriert, dass nur die Person, die sie anwendet, das Dokument oder die E-Mail öffnen kann. Für sie gelten dabei uneingeschränkte Nutzungsrechte. Dies kann z.B. nützlich sein, wenn sichergestellt werden soll, dass das Dokument an einem beliebigen Ort gespeichert aber nur von dieser Person geöffnet werden darf. Wenn dies genau das gewünschte Ergebnis ist und keine anderen Personen Zugriff auf den geschützten Inhalt benötigen, fahren Sie mit Schritt 12 statt mit Schritt 5 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn ein Dokument oder eine E-Mail-Adresse geschützt ist. Fahren Sie dann mit Schritt 11 fort.
        
        Die bereits konfigurierten Schutzeinstellungen werden in Form einer archivierten Schutzvorlage beibehalten und werden angezeigt, wenn Sie die Option wieder in **Protect** (Schützen) ändern. Diese Vorlage sehen Sie nicht im Azure-Portal. Sie können die Vorlage aber über [PowerShell](configure-templates-with-powershell.md) verwalten. Das bedeutet, dass Inhalt weiterhin zugänglich ist, wenn er über diese Bezeichnung und die zuvor angewendeten Schutzeinstellungen verfügt.
        
        Beachten Sie, dass Benutzer zum Anwenden einer Bezeichnung mit dieser Option die Berechtigungen benötigen, um den Rights Management-Schutz zu entfernen. Diese Anforderung bedeutet, dass Benutzer über das **Nutzungsrecht** **Exportieren** oder [Vollzugriff](../deploy-use/configure-usage-rights.md) verfügen müssen. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](../deploy-use/configure-super-users.md) fungieren. Die Azure Rights Management-Standardvorlagen umfassen nicht die Nutzungsrechte, die Benutzer zum Aufheben des Schutzes benötigen. 
        
        Wenn ein Benutzer keine Berechtigungen zum Entfernen des Rights Management-Schutzes hat und eine mit der Option **Schutz entfernen** konfigurierte Bezeichnung auswählt, wird folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**

4. Wenn Sie **Schützen** ausgewählt haben, klicken Sie jetzt auf **Schutz**, um das Blatt **Schutz** zu öffnen:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](../media/info-protect-protection-bar-configured.png)

5. Wählen Sie auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) oder **HYOK (AD RMS)** aus.
    
    In den meisten Fällen wählen Sie **Azure (cloud key)** (Azure (Cloud-Schlüssel)) für Ihre Berechtigungseinstellungen aus. Wählen Sie nicht **HYOK (AD RMS)** aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser „*Hold-your-own-key*“-Konfiguration (HYOK) einhergehen. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz). Um die Konfiguration für HYOK (AD RMS) fortzufahren, gehen Sie zu Schritt 9.
    
6. Wählen Sie eine der folgenden Optionen aus:
    
    - **Berechtigungen festlegen**: Definieren neuer Schutzeinstellungen in diesem Portal.
    
    - **Benutzerdefinierte Berechtigungen festlegen (Vorschau)**: Benutzer können angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option dann verfeinern und nur Outlook oder Word, Excel, PowerPoint und den Datei-Explorer auswählen. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für eine [automatische Klassifizierung](configure-policy-classification.md) konfiguriert wurde.
        
        Wenn Sie die Option für Outlook wählen: Die Bezeichnung wird in Outlook angezeigt und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das gleiche wie bei der Option „Nicht weiterleiten“.
        
        Wenn Sie die Option für Word, Excel, PowerPoint und den Datei-Explorer auswählen: Wenn diese Option festgelegt wird, wird die Bezeichnung in diesen Anwendungen angezeigt. Das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das Anzeigen des Dialogfelds, in dem die Benutzer die benutzerdefinierten Berechtigungen auswählen können. In diesem Dialogfeld müssen Benutzer die Berechtigungen, die Benutzer oder Gruppen und ein beliebiges Ablaufdatum angeben. Versichern Sie sich, dass die Benutzer über die Anweisungen und den Leitfaden zum Bereitstellen dieser Werte verfügen.
    
    - **Vordefinierte Vorlage auswählen**: Zum Verwenden einer der Standardvorlagen oder einer benutzerdefinierten Vorlage, die Sie konfiguriert haben. Beachten Sie, dass diese Option nicht angezeigt wird, wenn Sie eine Bezeichnung bearbeiten, die zuvor die Option **Berechtigungen festlegen** verwendet hat.
    
    Diese Vorlage muss veröffentlicht werden (nicht archiviert) und darf nicht bereits mit einer anderen Bezeichnung verknüpft sein, damit Sie eine vordefinierte Vorlage auswählen können. Wenn Sie diese Option auswählen, können Sie die Schaltfläche **Vorlage bearbeiten** verwenden, um [die Vorlage in eine Bezeichnung umzuwandeln](configure-policy-templates.md#to-convert-templates-to-labels).
    
    Tipp: Wenn Sie es gewohnt sind, benutzerdefinierte Vorlagen zu erstellen und zu bearbeiten, sind die [Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben](migrate-portal.md), möglicherweise nützlich für Sie.

7. Wenn Sie **Festlegen von Berechtigungen** für **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt haben, können Sie durch diese Option die gleichen Einstellungen konfigurieren, die Sie in einer Vorlage konfigurieren können. 
    
    Wählen Sie **Berechtigungen hinzufügen**, und wählen Sie auf dem Blatt **Berechtigungen hinzufügen** den ersten Satz von Benutzern und Gruppen, der die Rechte besitzt, den von der ausgewählten Bezeichnung geschützten Inhalt zu nutzen:
    
    - Klicken Sie auf **Aus der Liste auswählen**, und wählen Sie **Hinzufügen \<Organisationsname> – Alle Mitglieder** aus, um alle Benutzer Ihrer Organisation hinzuzufügen. Diese Einstellung schließt Gastkonten aus. Sie können auch das Verzeichnis durchsuchen.
        
        Die Benutzer oder Gruppen müssen über eine E-Mail-Adresse verfügen. In einer Produktionsumgebung verfügen Benutzer und Gruppen fast immer über eine E-Mail-Adresse. In einer einfachen Testumgebung müssen Sie eventuell Benutzerkonten oder -gruppen E-Mail-Adressen hinzufügen.
        
    - Wählen Sie **Details eingeben** aus, um manuell E-Mail-Adressen für einzelne Benutzer oder Gruppen (intern oder extern) anzugeben. Sie können diese Option auch verwenden, um alternativ alle Benutzer in einer Organisation durch die Eingabe eines beliebigen Domänennamens aus dieser Organisation anzugeben. Außerdem können Sie diese Option für soziale Netzwerke verwenden, indem Sie den Domänennamen, z.B. **gmail.com**, **hotmail.com** oder **outlook.com** eingeben.
        
    >[!NOTE]
    >Wenn sich eine E-Mail-Adresse ändert, nachdem Sie den Benutzer oder die Gruppe ausgewählt haben, lesen Sie die Informationen im Abschnitt [Überlegungen bei einer Änderung der E-Mail-Adressen](../plan-design/prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) in der Planungsdokumentation.
    
    Als bewährte Methode verwenden Sie Gruppen statt Benutzer. Durch diese Strategie bleibt Ihre Konfiguration einfacher, und Sie müssen später wahrscheinlich nicht Ihre Bezeichnungskonfiguration aktualisieren und den Inhalt erneut schützen. Wenn Sie jedoch Änderungen an der Gruppe durchführen, denken Sie daran, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](../plan-design/prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Wenn Sie den ersten Satz von Benutzern und Gruppen angegeben haben, wählen Sie die Berechtigungen aus, die für diese Benutzer und Gruppen gewährt werden sollen. Weitere Informationen zu den Berechtigungen, die Sie auswählen können, finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Rights Management](configure-usage-rights.md). Anwendungen, die diesen Schutz unterstützen, unterscheiden sich jedoch möglicherweise darin, wie sie diese Berechtigungen implementieren. Lesen Sie die Dokumentationen der Anwendungen, und führen Sie eigene Tests mit den Anwendungen aus, die von Benutzer verwendet werden, um das Verhalten zu überprüfen, bevor Sie die Vorlage für Benutzer bereitstellen.
    
    Falls erforderlich, können Sie jetzt einen zweiten Satz von Benutzern und Gruppen mit Nutzungsrechten hinzufügen. Wiederholen Sie diesen Prozess, bis Sie alle Benutzer und Gruppen mit den jeweiligen Berechtigungen angegeben haben.

    >[!TIP]
    >Fügen Sie ggf. die benutzerdefinierte Berechtigung **Speichern unter, Exportieren** hinzu, und gewähren Sie diese Administratoren für Datenwiederherstellung oder Mitarbeitern in anderen Rollen, die für die Informationswiederherstellung verantwortlich sind. Falls nötig können diese Benutzer dann den Schutz für Dateien und E-Mails entfernen, die mithilfe dieser Bezeichnung oder Vorlage geschützt werden. Diese Fähigkeit zum Entfernen des Schutzes auf Berechtigungsebene für ein Dokument oder eine E-Mail bietet eine präzisere Kontrolle als die [Administratorfunktion](configure-super-users.md).
    
    Überprüfen Sie nun auf dem Blatt **Schutz** für alle Benutzer und Gruppen, die Sie angegeben haben, ob Sie Änderungen an folgenden Einstellungen vornehmen möchten. Beachten Sie, dass diese Einstellungen wie bei den Berechtigungen nicht für den [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder einen beliebigen zugewiesenen [Administrator](configure-super-users.md) gelten.
    
    ###### <a name="information-about-the-protection-settings"></a>Informationen zu Schutzeinstellungen
    
    |Einstellung|Weitere Informationen|Empfohlene Einstellung
    |-----------|--------------------|--------------------|
    |**Inhalt läuft ab am**|Definieren Sie ein Datum oder eine Anzahl von Tagen, nach deren Ablauf Dokumente oder E-Mails, die durch diese Einstellungen geschützt sind, nicht mehr von ausgewählten Benutzern geöffnet werden sollen. Sie können ein Datum oder eine Anzahl von Tagen beginnend ab dem Zeitpunkt angeben, an dem der Schutz auf den Inhalt angewendet wird.<br /><br />Wenn Sie ein Datum angeben, wird der Schutz ab Mitternacht in Ihrer aktuellen Zeitzone wirksam.|**Inhalt läuft nie ab**, sofern für den Inhalt keine bestimmten zeitgebundenen Anforderungen vorliegen.|
    |**Offlinezugriff zulassen**|Mit dieser Einstellung können Sie Ihre bestehenden Sicherheitsanforderungen abstimmen (einschließlich des Zugriffs nach einem Widerruf) mit der Möglichkeit für ausgewählte Benutzer, geschützte Inhalte zu öffnen, wenn keine Internetverbindung besteht.<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich diese Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und ihre Zugriffe werden protokolliert. Wenn ihre Anmeldeinformationen nicht zwischengespeichert wurden, werden Benutzer in diesem Fall aufgefordert, sich anzumelden, bevor sie das Dokument oder die E-Mail öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden die Richtlinie und die Benutzergruppenmitgliedschaft erneut ausgewertet. Dies bedeutet, dass es bei Benutzern für dasselbe Dokument oder dieselbe E-Mail zu unterschiedlichen Zugriffsergebnissen kommen kann, wenn sich seit ihrem letzten Zugriff auf den Inhalt Änderungen an der Richtlinie oder ihrer Gruppenmitgliedschaft ereignet haben. Dies könnte dazu führen, dass der Zugriff verweigert wird, wenn das Dokument [widerrufen](../rms-client/client-track-revoke.md) wurde.|Je nach Wichtigkeit des Inhalts:<br /><br />- **Anzahl der Tage, die der Inhalt ohne Internetverbindung verfügbar ist** = **7** für sensible Geschäftsdaten, die dem Unternehmen schaden können, wenn sie an unbefugte Personen weitergegeben werden. Diese Empfehlung bietet einen ausgewogenen Kompromiss zwischen Flexibilität und Sicherheit. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebsdaten.<br /><br />- **Nie** bei sehr sensiblen Geschäftsdaten, die dem Unternehmen schaden würden, wenn sie an Unbefugte weitergegeben werden. Diese Empfehlung räumt der Sicherheit Vorrang gegenüber Flexibilität ein und stellt sicher, dass unmittelbar nach einem Widerruf des Dokument keine der autorisierten Benutzer das Dokument öffnen können. Beispiele hierfür sind Mitarbeiter- und Kundeninformationen, Kennwörter, Quellcode und vorangekündigte Finanzberichte.|
    
    Wenn Sie das Konfigurieren der Berechtigungen und Einstellungen abgeschlossen haben, klicken Sie auf **OK**. 
    
    Bei dieser Gruppierung von Einstellungen wird eine benutzerdefinierte Vorlage für den Azure Rights Management-Dienst erstellt. Diese Vorlagen können in Anwendungen und Diensten verwendet werden, die in Azure Rights Management integriert sind. Informationen zum Herunterladen und Aktualisieren dieser Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

8. Falls Sie **Vordefinierte Vorlage auswählen** für **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt haben, klicken Sie im Dropdownmenü auf die [Vorlage](../deploy-use/configure-policy-templates.md), die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen. Archivierte Vorlagen oder Vorlagen, die bereits für eine andere Bezeichnung ausgewählt wurden, werden nicht angezeigt.
    
    Bei Auswahl einer **Abteilungsvorlage** oder wenn Sie [Onboardingsteuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
    - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Falls dieses Problem weiterhin besteht, wenden Sie sich an den Administrator.**
        
        Beachten Sie, dass immer alle veröffentlichten Vorlagen angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Konfigurieren Sie z. B. eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die Vorlagen, die Sie auswählen können, sind nicht auf Vorlagen beschränkt, die auf den Bereich „Marketing“ bezogen sind, und es ist möglich, eine abteilungsbezogene Vorlage auszuwählen, die Ihre ausgewählten Benutzer nicht verwenden können. Zur Vereinfachung der Konfiguration und zum Minimieren der Problembehandlung können Sie die Abteilungsvorlage gemäß der Bezeichnung in der bereichsbezogenen Richtlinie benennen. 

9. Wenn Sie **HYOK (AD RMS)** ausgewählt haben, klicken Sie entweder auf **Set AD RMS templates details** (Festlegen von Vorlagendetails für AD RMS) oder auf **Benutzerdefinierte Berechtigungen festlegen (Vorschau)**. Geben Sie dann die Lizenzierungs-URL Ihres AD RMS-Clusters an.
    
    Anweisungen zum Angeben einer Vorlagen-GUID oder Ihrer Lizenzierungs-URL finden Sie unter [Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Mit der Option für benutzerdefinierte Berechtigungen können Benutzer angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option dann verfeinern und nur Outlook wählen (Standardeinstellung) oder Word, Excel, PowerPoint und den Datei-Explorer. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für eine [automatische Klassifizierung](configure-policy-classification.md) konfiguriert wurde.
    
    Wenn Sie die Option für Outlook wählen: Die Bezeichnung wird in Outlook angezeigt und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das gleiche wie bei der Option „Nicht weiterleiten“.
    
    Wenn Sie die Option für Word, Excel, PowerPoint und den Datei-Explorer wählen: Die Bezeichnung wird in diesen Anwendungen angezeigt. Das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das Anzeigen des Dialogfelds, in dem die Benutzer die benutzerdefinierten Berechtigungen auswählen können. In diesem Dialogfeld müssen Benutzer die Berechtigungen, die Benutzer oder Gruppen und ein beliebiges Ablaufdatum angeben. Versichern Sie sich, dass die Benutzer über die Anweisungen und den Leitfaden zum Bereitstellen dieser Werte verfügen.

10. Klicken Sie auf **OK**, um das Blatt **Schutz** zu schließen und die Auswahl für **Benutzerdefiniert** bzw. die ausgewählte Vorlage für die Option **Schutz** auf dem Blatt **Bezeichnung** anzuzeigen.

11. Klicken Sie auf dem Blatt **Bezeichnung** auf **Speichern**.

12. Verwenden Sie auf dem Blatt **Azure Information Protection** die Spalte **PROTECTION** (Schutz), um zu bestätigen, dass Ihre Bezeichnung nun die gewünschten Schutzeinstellungen darstellt:
    
    - Ein Häkchen, falls Sie den Schutz konfiguriert haben. 
    
    - Das Zeichen „x“, um den Abbruch anzugeben, wenn Sie eine Bezeichnung zum Entfernen des Schutzes konfiguriert haben.
    
    - Ein leeres Feld, wenn der Schutz nicht festgelegt ist. 

Sobald Sie auf **Speichern** klicken, werden Ihre vorgenommenen Änderungen automatisch Benutzern und Diensten zur Verfügung gestellt. Es gibt keine gesonderte Veröffentlichungsoption mehr.


## <a name="example-configurations"></a>Beispielkonfigurationen

Die untergeordneten Bezeichnungen **Alle Mitarbeiter** und **Nur Empfänger** der Bezeichnungen **Vertraulich** und **Streng vertraulich** aus der [Standardrichtlinie](configure-policy-default.md) stellen Beispiele für das Konfigurieren von Bezeichnungen, die Schutz anwenden, dar. Die folgenden Beispiele sollten Ihnen ebenfalls beim Konfigurieren von Schutz für verschiedene Szenarios helfen. 

Wählen Sie für jedes der folgenden Beispiele auf dem Blatt \<*Beizeichnungsname*> **Schutz** aus, um das Blatt **Schutz** zu öffnen.

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Beispiel 1: Bezeichnung für die Anwendung von „Nicht weiterleiten“ zum Senden einer geschützten E-Mail an ein Gmail-Konto

Diese Bezeichnung ist nur in Outlook verfügbar und geeignet, wenn Exchange Online für die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist. Weisen Sie die Benutzer an, diesen Bezeichner auszuwählen, wenn sie eine geschützte E-Mail an ein Gmail-Konto (bzw. jedes andere E-Mail-Konto, das nicht zu ihrer Organisation gehört) senden müssen. 

Ihre Benutzer geben dann die E-Mail-Adresse von Gmail in das Feld **An** ein.  Sie wählen anschließend die Bezeichnung aus, und die Option „Nicht weiterleiten“ wird der E-Mail automatisch hinzugefügt. Dadurch können Empfänger die E-Mail nicht weiterleiten, drucken, etwas daraus kopieren, Anhänge speichern oder die E-Mail unter einem anderem Namen speichern. 

1. Stellen Sie sicher, dass auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt ist.
    
2. Wählen Sie die Option **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus.

3. Stellen Sie sicher, dass die folgende Option ausgewählt ist: **In Outlook apply Do Not Forward** („Nicht weiterleiten“ in Outlook anwenden).

4. Wenn die Option ausgewählt ist, deaktivieren Sie die folgende Option: **In Word, Excel, PowerPoint and File Explorer prompt user for custom permissions** (Vom Benutzer in Word, Excel, PowerPoint und dem Datei-Explorer benutzerdefinierte Berechtigungen verlangen).

5. Klicken Sie auf dem Blatt **Schutz** auf **OK**.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Beispiel 2: Bezeichnung, die schreibgeschützte Berechtigungen für alle Benutzer in einer anderen Organisation einschränkt und sofortiges Sperren unterstützt

Diese Bezeichnung eignet sich für die (schreibgeschützte) Freigabe von streng vertraulichen Dokumenten, für deren Ansicht stets eine Internetverbindung erforderlich ist. Gesperrten Benutzer wird das Dokument beim nächsten Öffnen nicht mehr angezeigt.

Diese Bezeichnung ist für E-Mails nicht geeignet.

1. Stellen Sie sicher, dass auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass die Option **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Klicken Sie auf der Seite **Berechtigungen hinzufügen** auf **Details eingeben**.

4. Geben Sie den Namen einer Domäne aus der anderen Organisation, z.B. **fabrikam.com**, ein. Wählen Sie **Hinzufügen** aus.

5. Wählen Sie zunächst **Viewer**aus **Berechtigungen aus Voreinstellung auswählen** und anschließend **OK** aus.

6. Wählen Sie erneut auf der Seite **Schutz** für die Einstellung **Allow offline access setting** (Offlinezugang zulassen) **Nie** aus.

7. Klicken Sie auf dem Blatt **Schutz** auf **OK**.


### <a name="example-3-add-external-users-to-an-existing-label"></a>Beispiel 3: Hinzufügen von externen Benutzern zu einer bestehenden Bezeichnung

Die neu von Ihnen hinzugefügten Benutzer können Dokumente und E-Mails öffnen, die bereits durch diese Bezeichnung geschützt sind. Die Berechtigungen, die Sie diesen Benutzern erteilen, können von den Berechtigungen der bestehenden Benutzer abweichen.

1. Stellen Sie sicher, dass auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt ist.
    
2. Gehen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Klicken Sie auf der Seite **Berechtigungen hinzufügen** auf **Details eingeben**.

4. Geben Sie die E-Mail-Adresse des ersten hinzuzufügenden Benutzers (oder der Gruppe) ein, und wählen Sie **Hinzufügen** aus.

5. Wählen Sie die Berechtigungen für den Benutzer (oder die Gruppe) aus.

6. Wiederholen Sie die Schritte 4 und 5 für jeden Benutzer (oder jede Gruppe), den (oder die) Sie dieser Bezeichnung hinzufügen wollen. Klicken Sie dann auf **OK**.

7. Klicken Sie auf auf dem Blatt **Schutz** auf **OK**.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Beispiel 4: Bezeichnung für geschützte E-Mails, die weniger einschränkende Berechtigungen als „Nicht weiterleiten“ unterstützt

Diese Bezeichnung kann nicht auf Outlook beschränkt sein, sondern stellt weniger einschränkende Kontrollen dar als „Nicht weiterleiten“. Beispielsweise sollten Empfänger aus einer E-Mail oder einem Anhang kopieren oder einen Anhang speichern und bearbeiten können.

Wenn Sie externe Benutzer angeben, die kein Azure AD-Konto haben, gilt Folgendes:

- Die Bezeichnung eignet sich für E-Mails, wenn Exchange Online die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) verwendet. 
 
- Für Office-Anhänge, die automatisch geschützt sind, stehen diese Dokumente für eine Browservorschau zur Verfügung. Um diese Dokumente zu bearbeiten, laden Sie sie herunter, und bearbeiten Sie sie mit Office 2016-Klick-und-Los und einem Microsoft-Konto, das dieselbe E-Mail-Adresse verwendet. [Weitere Informationen](../get-started/secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)


> [!NOTE]
> In Exchange Online wird eine neue Option eingeführt: [Encrypt-Only](configure-usage-rights.md#encrypt-only-option-for-emails). Diese Option ist für das Konfigurieren von Bezeichnungen nicht verfügbar. Sie können mit diesem Beispiel jedoch eine Bezeichnung mit denselben Nutzungsrechten konfigurieren.

Wenn Ihre Benutzer die E-Mail-Adressen in dem Feld **An** angeben, müssen diese Adressen für dieselben Benutzer sein, die Sie für diese Bezeichnung festgelegt haben. Da Benutzer zu Gruppen gehören und mehr als eine E-Mail-Adresse haben können, muss die von ihnen angegebene E-Mail-Adresse nicht mit der von Ihnen für die Berechtigung angegebenen E-Mail-Adresse übereinstimmen. Die Angabe derselben E-Mail-Adresse ist allerdings der einfachste Weg, um sicherzustellen, dass der Empfänger erfolgreich autorisiert wird. Weitere Informationen zur Vorgehensweise bei der Autorisierung von Benutzern für Berechtigungen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](../plan-design/prepare.md). 

1. Stellen Sie sicher, dass auf dem Blatt **Schutz** die Option **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Wählen Sie auf dem Blatt **Berechtigungen hinzufügen** die Option **Hinzufügen \<Organisationsname> – Alle Mitglieder** aus, um sämtliche Benutzer in Ihrem Mandanten auszuwählen und ihnen Berechtigungen zu erteilen. Diese Einstellung schließt Gastkonten aus. Alternativ dazu klicken Sie auf **Verzeichnis durchsuchen**, um eine bestimmte Gruppe auszuwählen. Klicken Sie auf **Details eingeben**, und geben Sie die E-Mail-Adresse des Benutzers oder die Azure AD-Gruppe oder einen Domänennamen ein, um externen Benutzern Berechtigungen zu erteilen oder wenn Sie die E-Mail-Adresse lieber manuell eingeben möchten.
    
    Wiederholen Sie diesen Schritt, um zusätzliche Benutzer anzugeben, die über dieselben Berechtigungen verfügen sollen.

4. Wählen Sie für **Berechtigungen aus Voreinstellung auswählen** **Mitbesitzer**, **Mitautor**, **Prüfer** oder **Benutzerdefiniert** aus, um die Berechtigungen, die Sie erteilen möchten, auszuwählen.
    
    Hinweis: Wählen Sie für E-Mails nicht die Option **Viewer** aus, und wenn Sie **Benutzerdefiniert** auswählen, stellen Sie sicher, dass Sie **Bearbeiten und speichern** hinzufügen.
    
    Um dieselben Berechtigungen wie bei der neuen Exchange Online-Option **Nur verschlüsseln** zu haben, wählen Sie **Benutzerdefiniert** aus. Gewähren Sie dann alle Berechtigungen außer **Speichern unter, Exportieren (EXPORT)** und **Vollzugriff (OWNER)**.

5. Wiederholen Sie die Schritte 3 und 4, um zusätzliche Benutzer anzugeben, die über andere Berechtigungen verfügen sollen.

6. Klicken Sie auf dem Blatt **Berechtigungen hinzufügen** auf **OK**.

7. Klicken Sie auf auf dem Blatt **Schutz** auf **OK**.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy).  

[!INCLUDE[Commenting house rules](../includes/houserules.md)]