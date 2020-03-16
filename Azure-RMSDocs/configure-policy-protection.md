---
title: Konfigurieren einer Azure Information Protection-Bezeichnung für den Schutz – AIP
description: Beim Konfigurieren einer Bezeichnung zur Verwendung von Rights Management-Schutz können Sie Ihre sensibelsten Dokumente und E-Mails schützen.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 0f98ea44bc223f3b484836fdcf53ecd452b352ce
ms.sourcegitcommit: 2917e822a5d1b21bf465f2cb93cfe46937b1faa7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2020
ms.locfileid: "79404452"
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>Konfigurieren einer Bezeichnung für Rights Management-Schutz

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*


> [!NOTE]
> Diese Anweisungen gelten für den Azure Information Protection-Client (klassisch) und nicht für den Azure Information Protection-Client für einheitliche Bezeichnungen. Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client) an.
> 
> Informationen zum Konfigurieren einer Vertraulichkeitsbezeichnung zum Anwenden des Rights Management-Schutzes finden Sie in der Dokumentation zur Microsoft 365-Compliance. Ein Beispiel ist der Artikel [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels).

Sie können Ihre sensibelsten Dokumente und E-Mails mithilfe des Rights Management-Diensts schützen. Dieser Dienst verwendet Verschlüsselungs-, Identitäts- und Autorisierungsrichtlinien, um Datenverlust zu verhindern. Der Schutz wird mit einer Bezeichnung angewendet, die so konfiguriert ist, dass der Rights Management-Schutz für Dokumente und E-Mails verwendet wird, und Benutzer können auch auf die Schaltfläche **Nicht weiterleiten** in Outlook klicken.

Wenn eine Bezeichnung mit der Schutzeinstellung **Azure (Cloud-Schlüssel)** konfiguriert wird, wird hierdurch im Hintergrund eine Schutzvorlage erstellt und eingerichtet. Auf diese kann dann über Dienste und Anwendungen zugegriffen werden, die in die Rights Management-Vorlagen integriert sind. Beispiele sind Exchange Online mit Regeln für den E-Mail-Fluss sowie Outlook on the Web. 

## <a name="how-the-protection-works"></a>Funktionsweise des Schutzes

Wenn ein Dokument oder eine E-Mail von einem Rights Management-Dienst geschützt wird, wird es oder sie im Ruhezustand und während der Übertragung verschlüsselt. Die Entschlüsselung kann dann nur durch einen autorisierten Benutzer erfolgen. Diese Verschlüsselung wird auch dann beibehalten, wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und Einschränkungen konfigurieren. Nachfolgend sind einige Beispiele aufgeführt:

- Nur Benutzer innerhalb Ihrer Organisation können das vertrauliche, geschäftliche Dokument oder die E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung können das Dokument oder die E-Mail zu einer bevorstehenden Werbeaktion bearbeiten oder drucken. Alle anderen Benutzer in Ihrer Organisation können das Dokument oder die E-Mail lediglich lesen.

- Benutzer können keine E-Mails weiterleiten oder darin enthaltene Informationen kopieren, die Nachrichten über eine interne Neuorganisation enthalten.

- Die aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem angegebenen Datum nicht mehr geöffnet werden.

Weitere Informationen zum Azure Rights Management-Schutz und dessen Funktionsweise finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md)

> [!IMPORTANT]
> Um eine Bezeichnung zur Anwendung dieses Schutzes zu konfigurieren, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](activate-service.md).

Wenn die Bezeichnung Schutz anwendet, ist ein geschütztes Dokument nicht für die Speicherung auf SharePoint oder OneDrive geeignet. Diese Speicherorte unterstützen die folgenden Features für geschützte Dateien nicht: gemeinsamen Dokument Erstellung, Office für das Web, Suche, Dokument Vorschau, Miniaturansicht, eDiscovery und Verhinderung von Datenverlust (Data Loss Prevention, DLP).

> [!TIP]
> Wenn Sie Ihre [Bezeichnungen zu vereinheitlichten Vertraulichkeitsbezeichnungen migrieren](configure-policy-migrate-labels.md) und diese von einem der Admin Center für Bezeichnungen (wie beispielsweise dem Microsoft 365 Compliance Center) aus veröffentlichen, werden Bezeichnungen, die Schutz anwenden, für diese Speicherorte unterstützt. Weitere Informationen finden Sie unter [Aktivieren von Vertraulichkeitsbezeichnungen für Office-Dateien in SharePoint und OneDrive (öffentliche Vorschauversion)](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files).

Exchange muss für Azure Information Protection nicht konfiguriert werden, damit Benutzer in Outlook Bezeichnungen zum Schutz ihrer E-Mails verwenden können. Sie können jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn für Azure Information Protection Exchange konfiguriert wird. Ohne diese Konfiguration können Benutzer beispielsweise geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook im Web anzeigen, derartige E-Mails können nicht für die Suche indiziert werden, und Sie können für Exchange Online DLP nicht den Rights Management-Schutz konfigurieren. In den folgenden Artikeln erhalten Sie Informationen, mit denen Sie sicherstellen können, dass Exchange diese zusätzlichen Szenarios unterstützt:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration).

- Für lokales Exchange müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-protection-settings"></a>So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen

1. Öffnen Sie ein neues Browserfenster und [melden Sie sich beim Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies noch nicht getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Beispielsweise im Suchfeld für Ressourcen, Dienste und Dokumente: beginnen Sie mit der Eingabe von **Informationen** , und wählen Sie **Azure Information Protection**aus.

2. Über die Menüoption **Klassifizierungen** > **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die Bezeichnung aus, die Sie ändern möchten. 

3. Suchen Sie im Bereich **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus:
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit zum Anwenden von Schutz konfiguriert ist und die ausgewählte Bezeichnung keinen Schutz mehr anwenden soll. Fahren Sie dann mit Schritt 11 fort.
        
        Die bereits konfigurierten Schutzeinstellungen werden in Form einer archivierten Schutzvorlage beibehalten und werden angezeigt, wenn Sie die Option wieder in **Protect** (Schützen) ändern. Diese Vorlage sehen Sie nicht im Azure-Portal. Sie können die Vorlage aber über [PowerShell](configure-templates-with-powershell.md) verwalten. Das bedeutet, dass Inhalt weiterhin zugänglich ist, wenn er über diese Bezeichnung und die zuvor angewendeten Schutzeinstellungen verfügt.
        
        Wenn eine Bezeichnung mit dieser **Nicht konfiguriert**-Schutzeinstellung angewendet wird:
        
         - Wenn der Inhalt zuvor ohne diese Bezeichnung geschützt wurde, bleibt der Schutz erhalten. 
         
         - Wenn der Inhalt zuvor mit einer Bezeichnung geschützt wurde, wird der Schutz entfernt, wenn der Benutzer, der die Bezeichnung anwendet, Berechtigungen hat, um den Rights Management-Schutz zu entfernen. Diese Anforderung bedeutet, dass Benutzer über das **Nutzungsrecht** **Exportieren** oder [Vollzugriff](configure-usage-rights.md) verfügen müssen. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](configure-super-users.md) fungieren.
             
             Wenn der Benutzer nicht über die Berechtigung zum Entfernen des Schutzes verfügt, kann die Bezeichnung nicht angewendet werden, und die folgende Meldung wird angezeigt: **Azure Information Protection diese Bezeichnung nicht anwenden können. Wenn dieses Problem weiterhin besteht, wenden Sie sich an Ihren Administrator**. 
    
    - **Schützen**: Wählen Sie diese Option aus, um Schutz anzuwenden, und fahren Sie dann mit Schritt 4 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn ein Dokument oder eine E-Mail-Adresse geschützt ist. Fahren Sie dann mit Schritt 11 fort.
        
        Wenn der Schutz mit einer Bezeichnungs- oder Schutzvorlage angewendet wurde, werden die Schutzeinstellungen in Form einer archivierten Schutzvorlage beibehalten und werden angezeigt, wenn Sie die Option wieder in **Schützen** ändern. Diese Vorlage sehen Sie nicht im Azure-Portal. Sie können die Vorlage aber über [PowerShell](configure-templates-with-powershell.md) verwalten. Das bedeutet, dass Inhalt weiterhin zugänglich ist, wenn er über diese Bezeichnung und die zuvor angewendeten Schutzeinstellungen verfügt.
        
        Beachten Sie, dass Benutzer zum erfolgreichen Anwenden einer Bezeichnung mit dieser Option die Berechtigungen benötigen, um den Rights Management-Schutz zu entfernen. Diese Anforderung bedeutet, dass Benutzer über das **Nutzungsrecht** **Exportieren** oder [Vollzugriff](configure-usage-rights.md) verfügen müssen. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](configure-super-users.md) fungieren. 
        
        Wenn der Benutzer, der die Bezeichnung mit dieser Einstellung anwendet, nicht über Berechtigungen zum Entfernen Rights Management Schutzes verfügt, kann die Bezeichnung nicht angewendet werden, und die folgende Meldung wird angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Wenn dieses Problem weiterhin besteht, wenden Sie sich an Ihren Administrator.**

4. Wenn Sie **Schützen** ausgewählt haben, wird der Bereich **Schutz** automatisch geöffnet, wenn zuvor eine der anderen Optionen ausgewählt wurde. Klicken Sie auf **Schutz**, wenn dieser neue Bereich nicht automatisch geöffnet wird:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png)

5. Klicken Sie im Bereich **Schutz** auf die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) oder **HYOK (AD RMS)** .
    
    In den meisten Fällen wählen Sie **Azure (cloud key)** (Azure (Cloud-Schlüssel)) für Ihre Berechtigungseinstellungen aus. Wählen Sie nicht **HYOK (AD RMS)** aus, es sei denn, Sie haben die Voraussetzungen und Einschränkungen verstanden, die mit dieser „*Hold-your-own-key*“-Konfiguration (HYOK) einhergehen. Weitere Informationen finden Sie unter [Hold your own key (HYOK) requirements and restrictions for AD RMS protection](configure-adrms-restrictions.md) (Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz). Um die Konfiguration für HYOK (AD RMS) fortzufahren, gehen Sie zu Schritt 9.
    
6. Wählen Sie eine der folgenden Optionen aus:
    
   - **Berechtigungen festlegen**: Definieren neuer Schutzeinstellungen in diesem Portal.
    
   - **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** : Benutzer können angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option dann verfeinern und nur Outlook oder Word, Excel, PowerPoint und den Datei-Explorer auswählen. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für eine [automatische Klassifizierung](configure-policy-classification.md) konfiguriert wurde.
        
       Wenn Sie die Option für Outlook wählen: Die Bezeichnung wird in Outlook angezeigt und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das gleiche wie bei der Option [Nicht weiterleiten](configure-usage-rights.md#do-not-forward-option-for-emails).
        
       Wenn Sie die Option für Word, Excel, PowerPoint und den Datei-Explorer auswählen: Wenn diese Option festgelegt wird, wird die Bezeichnung in diesen Anwendungen angezeigt. Das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das Anzeigen des Dialogfelds, in dem die Benutzer die benutzerdefinierten Berechtigungen auswählen können. In diesem Dialogfeld wählen Benutzer eine der [vordefinierten Berechtigungsstufen](configure-usage-rights.md#rights-included-in-permissions-levels) aus, navigieren dann zu dem Benutzer oder der Gruppe (bzw. geben diese an) und legen optional ein Ablaufdatum fest. Versichern Sie sich, dass die Benutzer über die Anweisungen und den Leitfaden zum Bereitstellen dieser Werte verfügen.
    
   - **Vordefinierte Vorlage auswählen**: Zum Verwenden einer der Standardvorlagen oder einer benutzerdefinierten Vorlage, die Sie konfiguriert haben. Beachten Sie, dass diese Option nicht zur Anzeige für neue Bezeichnungen verfügbar ist, oder wenn Sie eine Bezeichnung bearbeiten, die zuvor die Option **Berechtigungen festlegen** verwendet hat.
    
     Diese Vorlage muss veröffentlicht werden (nicht archiviert) und darf nicht bereits mit einer anderen Bezeichnung verknüpft sein, damit Sie eine vordefinierte Vorlage auswählen können. Wenn Sie diese Option auswählen, können Sie die Schaltfläche **Vorlage bearbeiten** verwenden, um [die Vorlage in eine Bezeichnung umzuwandeln](configure-policy-templates.md#to-convert-templates-to-labels).
    
     Wenn Sie es gewohnt sind, benutzerdefinierte Vorlagen zu erstellen und zu bearbeiten, sind die [Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben](migrate-portal.md), möglicherweise nützlich für Sie.

7. Wenn Sie **Berechtigungen festlegen** für **Azure (Cloudschlüssel)** ausgewählt haben, können Sie über diese Option Benutzer und Nutzungsrechte auswählen. 
    
    Wenn Sie keine Benutzer auswählen und **OK** in diesem Bereich auswählen, gefolgt von **Speichern** im Bereich " **Bezeichnung** ": die Bezeichnung ist so konfiguriert, dass Sie den Schutz anwendet, sodass nur die Person, die die Bezeichnung anwendet, das Dokument oder die e-Mail ohne Einschränkungen öffnen kann. Diese Konfiguration wird gelegentlich als „Nur für mich“ bezeichnet und ist möglicherweise erforderlich, um sicherzustellen, dass das Dokument an einem beliebigen Ort gespeichert, aber nur von dieser Person geöffnet werden kann. Wenn dies genau das gewünschte Ergebnis ist und keine anderen Personen Zugriff auf den geschützten Inhalt benötigen, wählen Sie nicht **Berechtigungen hinzufügen** aus. Nach dem Speichern der Bezeichnung wird Ihnen beim nächsten Öffnen des Bereichs **Schutz** für **Benutzer** die Option **IPC_USER_ID_OWNER** und für **Berechtigungen** die Option **Mitbesitzer** angezeigt, um diese Konfiguration widerzuspiegeln.
    
    Um die Benutzer anzugeben, die geschützte Dokumente und E-Mails öffnen können sollen, wählen Sie **Berechtigungen hinzufügen**. Wählen Sie dann im Bereich **Berechtigungen hinzufügen** die ersten Benutzer und Gruppen aus, die die Rechte besitzen sollen, den von der ausgewählten Bezeichnung geschützten Inhalt nutzen zu können:
    
   - Wählen Sie **Aus der Liste auswählen**, wo Sie dann **Hinzufügen \<Organisationsname> – Alle Mitglieder** auswählen können, um alle Benutzer Ihrer Organisation hinzuzufügen. Diese Einstellung schließt Gastkonten aus. Sie können auch **Alle authentifizierten Benutzer hinzufügen** auswählen oder das Verzeichnis durchsuchen.
        
       Wenn Sie alle Mitglieder auswählen oder das Verzeichnis durchsuchen, müssen die Benutzer oder Gruppen eine E-Mail-Adresse haben. In einer Produktionsumgebung verfügen Benutzer und Gruppen fast immer über eine E-Mail-Adresse. In einer einfachen Testumgebung müssen Sie eventuell Benutzerkonten oder -gruppen E-Mail-Adressen hinzufügen.
        
       ###### <a name="more-information-about-add-any-authenticated-users"></a>Weitere Informationen zu **Keine authentifizierten Benutzer hinzufügen** 
       Diese Einstellung schränkt nicht ein, wer auf den von der Bezeichnung geschützten Inhalt zugreifen kann, während der Inhalt dennoch verschlüsselt wird und Ihnen Optionen zur Verfügung stehen, wie der Inhalt verwendet (Berechtigungen) und wie auf ihn zugegriffen werden kann (Ablauf und Offlinezugriff). Die Anwendung, die den geschützten Inhalt öffnet, muss jedoch die verwendete Authentifizierung unterstützen. Aus diesem Grund sollten Verbundanbieter sozialer Netzwerke wie Google und die Authentifizierung per Einmalkennung nur für E-Mails verwendet werden, und nur, wenn Sie Exchange Online und die neuen Funktionen der Office 365-Nachrichtenverschlüsselung verwenden. Microsoft-Konten können mit dem Azure Information Protection-Viewer und Klick-und-Los von Office 365-Apps verwendet werden. 
          
       Einige typische Szenarios für die Einstellung „Keine authentifizierten Benutzer“:
       - Ihnen ist egal, wer den Inhalt sehen kann, Sie möchten jedoch einschränken, wie dieser verwendet wird. Beispielsweise soll der Inhalt nicht bearbeitet, kopiert oder gedruckt werden.
       - Sie müssen nicht einschränken, wer auf den Inhalt zugreift, aber Sie möchten nachvollziehen können, wer ihn öffnet, und ihn möglicherweise widerrufen.
       - Sie haben die Anforderung, dass der Inhalt im Ruhezustand und während der Übertragung verschlüsselt sein muss, aber es ist keine Zugriffssteuerung erforderlich.
        
   - Wählen Sie **Details eingeben** aus, um manuell E-Mail-Adressen für einzelne Benutzer oder Gruppen (intern oder extern) anzugeben. Sie können diese Option auch verwenden, um alternativ alle Benutzer in einer Organisation durch die Eingabe eines beliebigen Domänennamens aus dieser Organisation anzugeben. Außerdem können Sie diese Option für soziale Netzwerke verwenden, indem Sie den Domänennamen, z.B. **gmail.com**, **hotmail.com** oder **outlook.com** eingeben.
        
     >[!NOTE]
     >Wenn sich eine E-Mail-Adresse ändert, nachdem Sie den Benutzer oder die Gruppe ausgewählt haben, lesen Sie die Informationen im Abschnitt [Überlegungen bei einer Änderung der E-Mail-Adressen](prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) in der Planungsdokumentation.
    
     Als bewährte Methode verwenden Sie Gruppen statt Benutzer. Durch diese Strategie bleibt Ihre Konfiguration einfacher, und Sie müssen später wahrscheinlich nicht Ihre Bezeichnungskonfiguration aktualisieren und den Inhalt erneut schützen. Wenn Sie jedoch Änderungen an der Gruppe durchführen, denken Sie daran, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Wenn Sie den ersten Satz von Benutzern und Gruppen angegeben haben, wählen Sie die Berechtigungen aus, die für diese Benutzer und Gruppen gewährt werden sollen. Weitere Informationen zu den auswählbaren Berechtigungen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Information Protection](configure-usage-rights.md). Anwendungen, die diesen Schutz unterstützen, unterscheiden sich jedoch möglicherweise darin, wie sie diese Berechtigungen implementieren. Lesen Sie die Dokumentationen der Anwendungen, und führen Sie eigene Tests mit den Anwendungen aus, die von Benutzer verwendet werden, um das Verhalten zu überprüfen, bevor Sie die Vorlage für Benutzer bereitstellen.
    
     Falls erforderlich, können Sie jetzt einen zweiten Satz von Benutzern und Gruppen mit Nutzungsrechten hinzufügen. Wiederholen Sie diesen Prozess, bis Sie alle Benutzer und Gruppen mit den jeweiligen Berechtigungen angegeben haben.

     >[!TIP]
     >Fügen Sie ggf. die benutzerdefinierte Berechtigung **Speichern unter, Exportieren** hinzu, und gewähren Sie diese Administratoren für Datenwiederherstellung oder Mitarbeitern in anderen Rollen, die für die Informationswiederherstellung verantwortlich sind. Falls nötig können diese Benutzer dann den Schutz für Dateien und E-Mails entfernen, die mithilfe dieser Bezeichnung oder Vorlage geschützt werden. Diese Fähigkeit zum Entfernen des Schutzes auf Berechtigungsebene für ein Dokument oder eine E-Mail bietet eine präzisere Kontrolle als die [Administratorfunktion](configure-super-users.md).
    
     Überprüfen Sie nun im Bereich **Schutz** für alle Benutzer und Gruppen, die Sie angegeben haben, ob Sie Änderungen an den folgenden Einstellungen vornehmen möchten. Beachten Sie, dass diese Einstellungen wie bei den Berechtigungen nicht für den [Rights Management-Aussteller oder Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) oder einen beliebigen zugewiesenen [Administrator](configure-super-users.md) gelten.
    
     ###### <a name="information-about-the-protection-settings"></a>Informationen zu Schutzeinstellungen
    
     |Einstellung|Weitere Informationen|Empfohlene Einstellung
     |-----------|--------------------|--------------------|
     |**Ablauf des Dateiinhalts**|Definieren Sie ein Datum oder eine Anzahl von Tagen, nach deren Ablauf Dokumente, die durch diese Einstellungen geschützt sind, nicht mehr von ausgewählten Benutzern geöffnet werden sollen. Bei E-Mails wird dieses Ablaufdatum aufgrund von Cachemechanismen, die von manchen E-Mail-Clients verwendet werden, nicht immer erzwungen.<br /><br />Sie können ein Datum oder eine Anzahl von Tagen beginnend ab dem Zeitpunkt angeben, an dem der Schutz auf den Inhalt angewendet wird.<br /><br />Wenn Sie ein Datum angeben, wird der Schutz ab Mitternacht in Ihrer aktuellen Zeitzone wirksam.|**Inhalt läuft nie ab**, sofern für den Inhalt keine bestimmten zeitgebundenen Anforderungen vorliegen.|
     |**Offlinezugriff zulassen**|Mit dieser Einstellung können Sie mit der Möglichkeit für ausgewählte Benutzer, geschützte Inhalte zu öffnen, wenn keine Internetverbindung besteht, Ihre bestehenden Sicherheitsanforderungen abstimmen (einschließlich des Zugriffs nach einem Widerruf).<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich diese Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und ihre Zugriffe werden protokolliert. Wenn ihre Anmeldeinformationen nicht zwischengespeichert wurden, werden Benutzer in diesem Fall aufgefordert, sich anzumelden, bevor sie das Dokument oder die E-Mail öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden die Richtlinie und die Benutzergruppenmitgliedschaft erneut ausgewertet. Dies bedeutet, dass es bei Benutzern für dasselbe Dokument oder dieselbe E-Mail zu unterschiedlichen Zugriffsergebnissen kommen kann, wenn sich seit ihrem letzten Zugriff auf den Inhalt Änderungen an der Richtlinie oder ihrer Gruppenmitgliedschaft ereignet haben. Dies könnte dazu führen, dass der Zugriff verweigert wird, wenn das Dokument [widerrufen](./rms-client/client-track-revoke.md) wurde.|Je nach Wichtigkeit des Inhalts:<br /><br />- **Anzahl der Tage, die der Inhalt ohne Internetverbindung verfügbar ist** = **7** für sensible Geschäftsdaten, die dem Unternehmen schaden können, wenn sie an unbefugte Personen weitergegeben werden. Diese Empfehlung bietet einen ausgewogenen Kompromiss zwischen Flexibilität und Sicherheit. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebsdaten.<br /><br />- **Nie** bei sehr sensiblen Geschäftsdaten, die dem Unternehmen schaden würden, wenn sie an Unbefugte weitergegeben werden. Diese Empfehlung räumt der Sicherheit Vorrang gegenüber Flexibilität ein und stellt sicher, dass unmittelbar nach einem Widerruf des Dokument keine der autorisierten Benutzer das Dokument öffnen können. Beispiele hierfür sind Mitarbeiter- und Kundeninformationen, Kennwörter, Quellcode und vorangekündigte Finanzberichte.|
    
     Wenn Sie das Konfigurieren der Berechtigungen und Einstellungen abgeschlossen haben, klicken Sie auf **OK**. 
    
     Bei dieser Gruppierung von Einstellungen wird eine benutzerdefinierte Vorlage für den Azure Rights Management-Dienst erstellt. Diese Vorlagen können in Anwendungen und Diensten verwendet werden, die in Azure Rights Management integriert sind. Informationen zum Herunterladen und Aktualisieren dieser Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

8. Falls Sie **Vordefinierte Vorlage auswählen** für **Azure (cloud key)** (Azure (Cloud-Schlüssel)) ausgewählt haben, klicken Sie im Dropdownmenü auf die [Vorlage](configure-policy-templates.md), die verwendet werden soll, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen. Archivierte Vorlagen oder Vorlagen, die bereits für eine andere Bezeichnung ausgewählt wurden, werden nicht angezeigt.
    
    Bei Auswahl einer **Abteilungsvorlage** oder wenn Sie [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben:
    
    - Benutzer, die sich außerhalb des konfigurierten Bereichs der Vorlage befinden oder von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen sind, können die Bezeichnung weiterhin anzeigen, sie aber nicht anwenden. Wenn Sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection diese Bezeichnung nicht anwenden können. Wenn dieses Problem weiterhin besteht, wenden Sie sich an Ihren Administrator.**
        
        Beachten Sie, dass immer alle veröffentlichten Vorlagen angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Konfigurieren Sie z. B. eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die Vorlagen, die Sie auswählen können, sind nicht auf Vorlagen beschränkt, die auf den Bereich „Marketing“ bezogen sind, und es ist möglich, eine abteilungsbezogene Vorlage auszuwählen, die Ihre ausgewählten Benutzer nicht verwenden können. Zur Vereinfachung der Konfiguration und zum Minimieren der Problembehandlung können Sie die Abteilungsvorlage gemäß der Bezeichnung in der bereichsbezogenen Richtlinie benennen. 

9. Wenn Sie **HYOK (AD RMS)** ausgewählt haben, klicken Sie entweder auf **Set AD RMS templates details** (Festlegen von Vorlagendetails für AD RMS) oder auf **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** . Geben Sie dann die Lizenzierungs-URL Ihres AD RMS-Clusters an.
    
    Anweisungen zum Angeben einer Vorlagen-GUID oder Ihrer Lizenzierungs-URL finden Sie unter [Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Mit der Option für benutzerdefinierte Berechtigungen können Benutzer angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option dann verfeinern und nur Outlook wählen (Standardeinstellung) oder Word, Excel, PowerPoint und den Datei-Explorer. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für eine [automatische Klassifizierung](configure-policy-classification.md) konfiguriert wurde.
    
    Wenn Sie die Option für Outlook wählen: Die Bezeichnung wird in Outlook angezeigt und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das gleiche wie bei der Option [Nicht weiterleiten](configure-usage-rights.md#do-not-forward-option-for-emails).
    
    Wenn Sie die Option für Word, Excel, PowerPoint und den Datei-Explorer auswählen: Wenn diese Option festgelegt wird, wird die Bezeichnung in diesen Anwendungen angezeigt. Das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist das Anzeigen des Dialogfelds, in dem die Benutzer die benutzerdefinierten Berechtigungen auswählen können. In diesem Dialogfeld wählen Benutzer eine der [vordefinierten Berechtigungsstufen](configure-usage-rights.md#rights-included-in-permissions-levels) aus, navigieren dann zu dem Benutzer oder der Gruppe (bzw. geben diese an) und legen optional ein Ablaufdatum fest. Versichern Sie sich, dass die Benutzer über die Anweisungen und den Leitfaden zum Bereitstellen dieser Werte verfügen.

10. Klicken Sie auf **OK**, um den Bereich **Schutz** zu schließen und die Auswahl für **Benutzerdefiniert** bzw. die ausgewählte Vorlage für die Option **Schutz** im Bereich **Bezeichnung** anzuzeigen.

11. Klicken Sie im Bereich **Bezeichnung** auf **Speichern**.

12. Verwenden Sie im Bereich **Azure Information Protection** die Spalte **PROTECTION** (Schutz), um zu bestätigen, dass Ihre Bezeichnung nun die gewünschten Schutzeinstellungen darstellt:
    
    - Ein Häkchen, falls Sie den Schutz konfiguriert haben. 
    
    - Das Zeichen „x“, um den Abbruch anzugeben, wenn Sie eine Bezeichnung zum Entfernen des Schutzes konfiguriert haben.
    
    - Ein leeres Feld, wenn der Schutz nicht festgelegt ist. 

Sobald Sie auf **Speichern** klicken, werden Ihre vorgenommenen Änderungen automatisch Benutzern und Diensten zur Verfügung gestellt. Es gibt keine gesonderte Veröffentlichungsoption mehr.


## <a name="example-configurations"></a>Beispielkonfigurationen

Die untergeordneten Bezeichnungen **Alle Mitarbeiter** und **Nur Empfänger** der Bezeichnungen **Vertraulich** und **Streng vertraulich** aus der [Standardrichtlinie](configure-policy-default.md) stellen Beispiele für das Konfigurieren von Bezeichnungen, die Schutz anwenden, dar. Die folgenden Beispiele sollten Ihnen ebenfalls beim Konfigurieren von Schutz für verschiedene Szenarios helfen. 

Wählen Sie für jedes folgende Beispiel im Bereich \<*Bezeichnungsname*> die Option **Schützen** aus. Klicken Sie auf **Schutz**, um diesen Bereich zu öffnen, wenn der Bereich **Schutz** nicht automatisch geöffnet wird. Dort können Sie die Konfigurationsoptionen für den Schutz auswählen:

![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Beispiel 1: Bezeichnung für die Anwendung von „Nicht weiterleiten“ zum Senden einer geschützten E-Mail an ein Gmail-Konto

Diese Bezeichnung ist nur in Outlook verfügbar und geeignet, wenn Exchange Online für die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist. Weisen Sie die Benutzer an, diesen Bezeichner auszuwählen, wenn sie eine geschützte E-Mail an ein Gmail-Konto (bzw. jedes andere E-Mail-Konto, das nicht zu ihrer Organisation gehört) senden müssen. 

Ihre Benutzer geben dann die E-Mail-Adresse von Gmail in das Feld **An** ein.  Sie wählen anschließend die Bezeichnung aus, und die Option „Nicht weiterleiten“ wird der E-Mail automatisch hinzugefügt. Das Ergebnis ist, dass die Empfänger die e-Mail nicht weiterleiten oder drucken, kopieren oder die e-Mail außerhalb Ihres Postfachs speichern können, indem Sie die Option **Speichern** unter verwenden. 

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Wählen Sie die Option **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus.

3. Stellen Sie sicher, dass die folgende Option ausgewählt ist: **In Outlook apply Do Not Forward** („Nicht weiterleiten“ in Outlook anwenden).

4. Wenn die Option ausgewählt ist, deaktivieren Sie die folgende Option: **In Word, Excel, PowerPoint and File Explorer prompt user for custom permissions** (Vom Benutzer in Word, Excel, PowerPoint und dem Datei-Explorer benutzerdefinierte Berechtigungen verlangen).

5. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Beispiel 2: Bezeichnung, die schreibgeschützte Berechtigungen für alle Benutzer in einer anderen Organisation einschränkt und sofortiges Sperren unterstützt

Diese Bezeichnung eignet sich für die (schreibgeschützte) Freigabe von streng vertraulichen Dokumenten, für deren Ansicht stets eine Internetverbindung erforderlich ist. Gesperrten Benutzer wird das Dokument beim nächsten Öffnen nicht mehr angezeigt.

Diese Bezeichnung ist für E-Mails nicht geeignet.

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass die Option **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Klicken Sie im Bereich **Berechtigungen hinzufügen** auf **Details eingeben**.

4. Geben Sie den Namen einer Domäne aus der anderen Organisation, z.B. **fabrikam.com**, ein. Wählen Sie **Hinzufügen** aus.

5. Wählen Sie zunächst **Viewer**aus **Berechtigungen aus Voreinstellung auswählen** und anschließend **OK** aus.

6. Wählen Sie im Bereich **Schutz** für die Einstellung **Offlinezugriff zulassen** erneut **Nie** aus.

7. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.


### <a name="example-3-add-external-users-to-an-existing-label-that-protects-content"></a>Beispiel 3: Hinzufügen von externen Benutzern zu einer bestehenden Bezeichnung, die Inhalte schützt

Die neu von Ihnen hinzugefügten Benutzer können Dokumente und E-Mails öffnen, die bereits durch diese Bezeichnung geschützt sind. Die Berechtigungen, die Sie diesen Benutzern erteilen, können von den Berechtigungen der bestehenden Benutzer abweichen.

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Gehen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Klicken Sie im Bereich **Berechtigungen hinzufügen** auf **Details eingeben**.

4. Geben Sie die E-Mail-Adresse des ersten hinzuzufügenden Benutzers (oder der Gruppe) ein, und wählen Sie **Hinzufügen** aus.

5. Wählen Sie die Berechtigungen für den Benutzer (oder die Gruppe) aus.

6. Wiederholen Sie die Schritte 4 und 5 für jeden Benutzer (oder jede Gruppe), den (oder die) Sie dieser Bezeichnung hinzufügen wollen. Klicken Sie dann auf **OK**.

7. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Beispiel 4: Bezeichnung für geschützte E-Mails, die weniger einschränkende Berechtigungen als „Nicht weiterleiten“ unterstützt

Diese Bezeichnung kann nicht auf Outlook beschränkt sein, sondern stellt weniger einschränkende Kontrollen dar als „Nicht weiterleiten“. Beispielsweise sollten Empfänger aus einer E-Mail oder einem Anhang kopieren oder einen Anhang speichern und bearbeiten können.

Wenn Sie externe Benutzer angeben, die kein Azure AD-Konto haben, gilt Folgendes:

- Die Bezeichnung eignet sich für E-Mails, wenn Exchange Online die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) verwendet. 
 
- Für Office-Anlagen, die automatisch geschützt sind, stehen diese Dokumente für eine Browservorschau zur Verfügung. Um diese Dokumente zu bearbeiten, laden Sie sie herunter, und bearbeiten Sie sie mit Office 365-Apps (Klick-und-Los) und einem Microsoft-Konto, das dieselbe E-Mail-Adresse verwendet. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)


> [!NOTE]
> In Exchange Online wird eine neue Option eingeführt: [Encrypt-Only](configure-usage-rights.md#encrypt-only-option-for-emails). Diese Option ist für das Konfigurieren von Bezeichnungen nicht verfügbar. Wenn Sie die Empfänger jedoch kennen, können Sie mit diesem Beispiel eine Bezeichnung mit denselben Nutzungsrechten konfigurieren. 

Wenn Ihre Benutzer die E-Mail-Adressen in dem Feld **An** angeben, müssen diese Adressen für dieselben Benutzer sein, die Sie für diese Bezeichnung festgelegt haben. Da Benutzer zu Gruppen gehören und mehr als eine E-Mail-Adresse haben können, muss die von ihnen angegebene E-Mail-Adresse nicht mit der von Ihnen für die Berechtigung angegebenen E-Mail-Adresse übereinstimmen. Die Angabe derselben E-Mail-Adresse ist allerdings der einfachste Weg, um sicherzustellen, dass der Empfänger erfolgreich autorisiert wird. Weitere Informationen zur Vorgehensweise bei der Autorisierung von Benutzern für Berechtigungen finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md). 

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Klicken Sie im Bereich **Berechtigungen hinzufügen** : um Benutzern in Ihrer Organisation Berechtigungen zu erteilen, wählen Sie **Hinzufügen \<Organisationsname >-Alle Mitglieder** aus, um alle Benutzer in Ihrem Mandanten auszuwählen. Diese Einstellung schließt Gastkonten aus. Alternativ dazu klicken Sie auf **Verzeichnis durchsuchen**, um eine bestimmte Gruppe auszuwählen. Klicken Sie auf **Details eingeben**, und geben Sie die E-Mail-Adresse des Benutzers oder die Azure AD-Gruppe oder einen Domänennamen ein, um externen Benutzern Berechtigungen zu erteilen oder wenn Sie die E-Mail-Adresse lieber manuell eingeben möchten.
    
    Wiederholen Sie diesen Schritt, um zusätzliche Benutzer anzugeben, die über dieselben Berechtigungen verfügen sollen.

4. Wählen Sie für **Berechtigungen aus Voreinstellung auswählen** **Mitbesitzer**, **Mitautor**, **Prüfer** oder **Benutzerdefiniert** aus, um die Berechtigungen, die Sie erteilen möchten, auszuwählen.
    
    Hinweis: Wählen Sie für E-Mails nicht die Option **Viewer** aus, und wenn Sie **Benutzerdefiniert** auswählen, stellen Sie sicher, dass Sie **Bearbeiten und speichern** hinzufügen.
    
    Um dieselben Berechtigungen wie bei der neuen Exchange Online-Option **Nur verschlüsseln** zu haben, wählen Sie **Benutzerdefiniert** aus. Gewähren Sie dann alle Berechtigungen außer **Speichern unter, Exportieren (EXPORT)** und **Vollzugriff (OWNER)** .

5. Wiederholen Sie die Schritte 3 und 4, um zusätzliche Benutzer anzugeben, die über andere Berechtigungen verfügen sollen.

6. Klicken Sie im Bereich **Berechtigungen hinzufügen** auf **OK**.

7. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.


### <a name="example-5-label-that-encrypts-content-but-doesnt-restrict-who-can-access-it"></a>Beispiel 5: Bezeichnung, die Inhalt verschlüsselt, aber nicht einschränkt, wer darauf zugreifen kann

Diese Konfiguration hat den Vorteil, dass Sie keine Benutzer, Gruppen oder Domänen angeben müssen, um eine E-Mail oder ein Dokument zu schützen. Der Inhalt wird weiterhin verschlüsselt, und Sie können weiterhin Nutzungsrechte, ein Ablaufdatum und einen Offlinezugriff festlegen. Verwenden Sie diese Konfiguration nur, wenn Sie nicht einschränken müssen, wer das geschützte Dokument oder die E-Mail öffnen darf. [Weitere Informationen zu dieser Einstellung](#more-information-about-add-any-authenticated-users)

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Achten Sie darauf, dass **Berechtigungen festlegen** ausgewählt ist, und klicken Sie anschließend auf **Berechtigungen hinzufügen**.

3. Klicken Sie im Bereich **Berechtigungen hinzufügen** auf der Registerkarte **Aus Liste auswählen** auf die Option **Alle authentifizierten Benutzer hinzufügen**.

4. Wählen Sie die gewünschten Berechtigungen aus, und klicken Sie auf **OK**.

5. Konfigurieren Sie im Bereich **Schutz** bei Bedarf die Einstellungen für **Ablauf des Dateiinhalts** und **Offlinezugriff zulassen**, und klicken Sie dann auf **OK**.

6. Klicken Sie im Bereich **Bezeichnung** auf **Speichern**.


### <a name="example-6-label-that-applies-just-for-me-protection"></a>Beispiel 6: Bezeichnung, die "nur für mich"-Schutz anwendet

Diese Konfiguration bietet das Gegenteil der sicheren Zusammenarbeit für Dokumente: mit Ausnahme eines Administratoren kann nur die Person, die die Bezeichnung [anwendet, den](configure-super-users.md)geschützten Inhalt ohne Einschränkungen öffnen. Diese Konfiguration wird oft als „Nur für mich“-Schutz bezeichnet und eignet sich, um sicherzustellen, dass das Dokument an einem beliebigen Ort gespeichert, aber nur von dieser Person geöffnet werden kann.

Die Bezeichnungskonfiguration wirkt zunächst einfach:

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Klicken Sie auf **OK**, ohne dabei Benutzer auszuwählen oder Einstellungen in diesem Bereich zu konfigurieren.
    
    Obwohl Sie Einstellungen für **Ablauf des Dateiinhalts** und **Offlinezugriff zulassen** konfigurieren können, können diese Zugriffseinstellungen nicht angewendet werden, wenn Sie keine Benutzer und deren Berechtigungen angeben. Das liegt daran, dass die Person, die den Schutz anwendet, der [Rights Management-Aussteller](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) für den Inhalt ist. Diese Rolle bildet eine Ausnahme für diese Zugriffseinschränkungen.

3. Klicken Sie im Bereich **Bezeichnung** auf **Speichern**.

## <a name="next-steps"></a>Nächste Schritte

Um weitere Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zu erhalten, klicken Sie auf die Links im Abschnitt [Konfigurieren der Richtlinie für Ihre Organisation](configure-policy.md#configuring-your-organizations-policy). 

Mit den Nachrichtenflussregeln von Exchange können auch Schutzaktionen basierend auf Ihren Bezeichnungen angewendet werden. Weitere Informationen und Beispiele finden Sie unter [Konfigurieren von Exchange Online-Regeln für den Nachrichtenfluss für Azure Information Protection-Bezeichnungen](configure-exo-rules.md).  
