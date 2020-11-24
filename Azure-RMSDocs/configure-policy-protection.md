---
title: Konfigurieren einer Azure Information Protection-Bezeichnung für den Schutz – AIP
description: Sie können Ihre hochsensiblen Dokumente und E-Mails schützen, indem Sie eine Bezeichnung für die Verwendung des Rights Management-Schutzes konfigurieren.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: df26430b-315a-4012-93b5-8f5f42e049cc
ms.subservice: aiplabels
ms.custom: admin
ms.openlocfilehash: 3ff562aba7243964275314875a52152ec7053fe2
ms.sourcegitcommit: 3780bd234c0af60d4376f1cae093b8b0ab035a9f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/09/2020
ms.locfileid: "95568486"
---
# <a name="how-to-configure-a-label-for-rights-management-protection"></a>So konfigurieren Sie eine Bezeichnung für den Rights Management-Schutz

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> *Anweisungen für: [Azure Information Protection-Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

> [!NOTE]
> Diese Anweisungen gelten für den Azure Information Protection-Client (klassisch) und nicht für den Azure Information Protection-Client für einheitliche Bezeichnungen. Wenn Sie nicht sicher sind, was der Unterschied zwischen diesen Clients ist, sehen Sie sich diese [FAQ](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients) an.
> 
> Informationen zum Konfigurieren einer Vertraulichkeits Bezeichnung zum Anwenden Rights Management Schutzes finden Sie in der Dokumentation zur Microsoft 365 Konformität. Ein Beispiel ist der Artikel [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels).

Sie können Ihre hochsensiblen Dokumente und E-Mails schützen, indem Sie einen Rights Management-Dienst verwenden. Dieser Dienst verwendet Verschlüsselung, Identität und Autorisierungsrichtlinien, um Datenverluste zu verhindern. Der Schutz wird mit einer Bezeichnung angewendet, die für die Verwendung des Rights Management-Schutzes für Dokumente und E-Mails konfiguriert ist. Benutzer können auch die Schaltfläche **Nicht weiterleiten** in Outlook verwenden.

Wenn eine Bezeichnung mit der Schutzeinstellung **Azure (Cloud-Schlüssel)** konfiguriert wird, wird hierdurch im Hintergrund eine Schutzvorlage erstellt und eingerichtet. Auf diese kann dann über Dienste und Anwendungen zugegriffen werden, die in die Rights Management-Vorlagen integriert sind. Beispiele sind Exchange Online mit Regeln für den E-Mail-Fluss sowie Outlook on the Web. 

## <a name="how-the-protection-works"></a>So funktioniert der Schutz

Wenn Dokumente oder E-Mails durch einen Rights Management-Dienst geschützt sind, werden sie im Ruhezustand und während der Übertragung verschlüsselt. Sie können nur von autorisierten Benutzern entschlüsselt werden. Diese Verschlüsselung bleibt bei dem Dokument oder der E-Mail, auch wenn das Dokument oder die E-Mail umbenannt wird. Darüber hinaus können Sie Nutzungsrechte und -einschränkungen konfigurieren, wie z.B. die folgenden:

- Nur Benutzer innerhalb Ihrer Organisation dürfen das vertrauliche Unternehmensdokument oder die vertrauliche Unternehmens-E-Mail öffnen.

- Nur Benutzer in der Marketingabteilung dürfen ein Dokument oder eine E-Mail mit der Ankündigung einer Werbeaktion bearbeiten und drucken. Alle anderen Benutzer dürfen das Dokument bzw. die E-Mail nur lesen.

- Benutzer dürfen eine E-Mail nicht weiterleiten oder Informationen daraus kopieren, die Informationen zu einer internen Neuorganisation enthält.

- Eine aktuelle Preisliste, die an Geschäftspartner gesendet wird, kann nach einem bestimmten Datum nicht mehr geöffnet werden.

Weitere Informationen zum Azure Rights Management-Schutz und seiner Funktionsweise finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md)

> [!IMPORTANT]
> Damit Sie eine Bezeichnung konfigurieren können, um diesen Schutz anzuwenden, muss der Azure Rights Management-Dienst für Ihre Organisation aktiviert sein. Weitere Informationen finden Sie unter [Aktivieren des Schutzdiensts von Azure Information Protection](activate-service.md).

Wenn durch eine Bezeichnung Schutz angewendet wird, ist das geschützte Dokument nicht zum Speichern auf SharePoint oder OneDrive geeignet. Diese Speicherorte unterstützen die folgenden Features für geschützte Dateien nicht: gemeinsamen Dokument Erstellung, Office für das Web, Suche, Dokument Vorschau, Miniaturansicht, eDiscovery und Verhinderung von Datenverlust (Data Loss Prevention, DLP).

> [!TIP]
> Wenn Sie Ihre [Bezeichnungen zu vereinheitlichten Vertraulichkeitsbezeichnungen migrieren](configure-policy-migrate-labels.md) und diese von einem der Admin Center für Bezeichnungen (wie beispielsweise dem Microsoft 365 Compliance Center) aus veröffentlichen, werden Bezeichnungen, die Schutz anwenden, für diese Speicherorte unterstützt. Weitere Informationen finden Sie unter  [Aktivieren von Vertraulichkeits Bezeichnungen für Office-Dateien in SharePoint und onedrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files).

Exchange muss für Azure Information Protection nicht konfiguriert werden, damit Benutzer in Outlook Bezeichnungen zum Schutz ihrer E-Mails verwenden können. Sie können jedoch den vollen Funktionsumfang des Azure Rights Management-Schutzes mit Exchange erst nutzen, wenn für Azure Information Protection Exchange konfiguriert wird. Einige Beispiele: Benutzer können geschützte E-Mails nicht auf Mobiltelefonen oder in Outlook im Web anzeigen, geschützte E-Mails können nicht für die Suche indiziert werden, und Sie können Exchange Online DLP nicht für den Rights Management-Schutz konfigurieren. In den folgenden Artikeln erhalten Sie Informationen, mit denen Sie sicherstellen können, dass Exchange diese zusätzlichen Szenarios unterstützt:

- Anweisungen für Exchange Online finden Sie unter [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration).

- Für Exchange lokal müssen Sie den [RMS-Connector bereitstellen und Ihre Exchange-Server konfigurieren](deploy-rms-connector.md). 

## <a name="to-configure-a-label-for-protection-settings"></a>So konfigurieren Sie eine Bezeichnung für Schutzeinstellungen

1. Öffnen Sie ein neues Browserfenster, und [melden Sie sich am Azure-Portal an](configure-policy.md#signing-in-to-the-azure-portal), falls Sie dies nicht bereits getan haben. Navigieren Sie anschließend zum Bereich **Azure Information Protection**. 
    
    Geben Sie im Suchfeld für Ressourcen, Dienste und Dokumente zunächst **Information** ein, und klicken Sie dann auf **Azure Information Protection**.

2. Über die Menüoption **Klassifizierungen**  >  **Bezeichnungen** : Wählen Sie im Bereich **Azure Information Protection-Bezeichnungen** die Bezeichnung aus, die Sie ändern möchten. 

3. Suchen Sie im Bereich **Bezeichnung** die Option **Berechtigungen für Dokumente und E-Mails mit dieser Bezeichnung festlegen**, und wählen Sie eine der folgenden Optionen aus:
    
    - **Nicht konfiguriert**: Wählen Sie diese Option aus, wenn die Bezeichnung derzeit so konfiguriert ist, dass der Schutz angewendet wird, und Sie den Schutz durch diese Bezeichnung nicht mehr wünschen. Fahren Sie dann mit Schritt 11 fort.
        
        Die bereits konfigurierten Schutzeinstellungen werden in Form einer archivierten Schutzvorlage beibehalten und werden angezeigt, wenn Sie die Option wieder in **Protect** (Schützen) ändern. Diese Vorlage sehen Sie nicht im Azure-Portal. Sie können die Vorlage aber über [PowerShell](configure-templates-with-powershell.md) verwalten. Das bedeutet, dass Inhalt weiterhin zugänglich ist, wenn er über diese Bezeichnung und die zuvor angewendeten Schutzeinstellungen verfügt.
        
        Wenn eine Bezeichnung mit dieser **Nicht konfiguriert**-Schutzeinstellung angewendet wird:
        
         - Wenn der Inhalt zuvor ohne diese Bezeichnung geschützt wurde, bleibt der Schutz erhalten. 
         
         - Wenn der Inhalt zuvor mit einer Bezeichnung geschützt wurde, wird der Schutz entfernt, wenn der Benutzer, der die Bezeichnung anwendet, Berechtigungen hat, um den Rights Management-Schutz zu entfernen. Diese Anforderung bedeutet, dass der Benutzer über das [Nutzungsrecht](configure-usage-rights.md)" **exportieren** " oder " **voll** Zugriff" verfügen muss. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](configure-super-users.md) fungieren.
             
             Wenn der Benutzer nicht über die Berechtigung zum Entfernen des Schutzes verfügt, kann die Bezeichnung nicht angewendet werden, und die folgende Meldung wird angezeigt: **Azure Information Protection diese Bezeichnung nicht anwenden können. Wenn dieses Problem weiterhin besteht, wenden Sie sich an Ihren Administrator**. 
    
    - **Schützen**: Wählen Sie diese Option aus, um Schutz anzuwenden, und fahren Sie dann mit Schritt 4 fort.
    
    - **Schutz entfernen**: Wählen Sie diese Option aus, um den Schutz zu entfernen, wenn ein Dokument oder eine E-Mail geschützt ist. Fahren Sie dann mit Schritt 11 fort.
        
        Wenn der Schutz mit einer Bezeichnungs- oder Schutzvorlage angewendet wurde, werden die Schutzeinstellungen in Form einer archivierten Schutzvorlage beibehalten und werden angezeigt, wenn Sie die Option wieder in **Schützen** ändern. Diese Vorlage sehen Sie nicht im Azure-Portal. Sie können die Vorlage aber über [PowerShell](configure-templates-with-powershell.md) verwalten. Das bedeutet, dass Inhalt weiterhin zugänglich ist, wenn er über diese Bezeichnung und die zuvor angewendeten Schutzeinstellungen verfügt.
        
        Beachten Sie, dass Benutzer zum erfolgreichen Anwenden einer Bezeichnung mit dieser Option die Berechtigungen benötigen, um den Rights Management-Schutz zu entfernen. Diese Anforderung bedeutet, dass der Benutzer über das [Nutzungsrecht](configure-usage-rights.md)" **exportieren** " oder " **voll** Zugriff" verfügen muss. Alternativ muss der Benutzer der Rights Management-Besitzer sein (wodurch er automatisch Vollzugriff erhält) oder als [Administrator für Azure Rights Management](configure-super-users.md) fungieren. 
        
        Wenn der Benutzer, der die Bezeichnung mit dieser Einstellung anwendet, nicht über Berechtigungen zum Entfernen Rights Management Schutzes verfügt, kann die Bezeichnung nicht angewendet werden, und die folgende Meldung wird angezeigt: **Azure Information Protection kann diese Bezeichnung nicht anwenden. Wenn dieses Problem weiterhin besteht, wenden Sie sich an Ihren Administrator.**

4. Wenn Sie **Schützen** ausgewählt haben, wird der Bereich **Schutz** automatisch geöffnet, wenn zuvor eine der anderen Optionen ausgewählt wurde. Klicken Sie auf **Schutz**, wenn dieser neue Bereich nicht automatisch geöffnet wird:
    
    ![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png)

5. Klicken Sie im Bereich **Schutz** auf die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) oder **HYOK (AD RMS)**.
    
    In den meisten Fällen werden Sie **Azure (Cloudschlüssel)** für Ihre Berechtigungseinstellungen auswählen. Wählen Sie **HYOK (AD RMS)** nur dann aus, wenn Sie die Voraussetzungen und Einschränkungen gelesen haben und genau kennen, die mit dieser *Hold Your Own Key*-Konfiguration (lokal gehosteter Schlüssel) einhergehen. Weitere Informationen finden Sie unter [Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz](configure-adrms-restrictions.md). Um die Konfiguration für HYOK (AD RMS) fortzufahren, gehen Sie zu Schritt 9.
    
6. Wählen Sie eine der folgenden Optionen aus:
    
   - **Berechtigungen festlegen**: Hiermit definieren Sie neue Schutzeinstellungen in diesem Portal.
    
   - **Benutzerdefinierte Berechtigungen festlegen (Vorschau)**: Benutzer können angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option genauer definieren und „Nur Outlook“, „Word“, „Excel“, „PowerPoint“ oder „Datei-Explorer“ auswählen. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für die [automatische Klassifizierung](configure-policy-classification.md) konfiguriert ist.
        
       Wenn Sie die Option für Outlook auswählen: die Bezeichnung wird in Outlook angezeigt, und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist identisch mit der Option [nicht weiterleiten](configure-usage-rights.md#do-not-forward-option-for-emails) .
        
       Bei Auswahl der Option für Word, Excel, PowerPoint und Datei-Explorer gilt Folgendes: Wenn diese Option festgelegt ist, wird die Bezeichnung in diesen Anwendungen angezeigt. Nachdem die Benutzer die Bezeichnung angewendet haben, wird ein Dialogfeld zur Auswahl von benutzerdefinierten Berechtigungen angezeigt. In diesem Dialogfeld wählen Benutzer eine der [vordefinierten Berechtigungsstufen](configure-usage-rights.md#rights-included-in-permissions-levels) aus, navigieren dann zu dem Benutzer oder der Gruppe (bzw. geben diese an) und legen optional ein Ablaufdatum fest. Stellen Sie sicher, dass die Benutzer über die notwendigen Anweisungen und Anleitungen zum Bereitstellen dieser Werte verfügen.

        > [!NOTE]
        > Azure Information Protection Unterstützung für das Festlegen von benutzerdefinierten Berechtigungen befindet sich derzeit in der Vorschau Phase. In den [zusätzlichen Nutzungsbestimmungen für Microsoft Azure-Vorschauen](https://azure.microsoft.com/support/legal/preview-supplemental-terms/) finden Sie weitere rechtliche Bedingungen, die für Azure-Features gelten, die sich in der Beta- oder Vorschauversion befinden oder anderweitig noch nicht zur allgemeinen Verfügbarkeit freigegeben sind. 
        >
     
   - **Vordefinierte Vorlage auswählen**: Hiermit wird nur eine der Standardvorlagen oder eine von Ihnen konfigurierte benutzerdefinierte Vorlage verwendet. Beachten Sie, dass diese Option nicht zur Anzeige für neue Bezeichnungen verfügbar ist, oder wenn Sie eine Bezeichnung bearbeiten, die zuvor die Option **Berechtigungen festlegen** verwendet hat.
    
     Damit Sie eine vordefinierte Vorlage auswählen können, muss die Vorlage veröffentlicht (nicht archiviert) sein und darf nicht bereits mit einer anderen Bezeichnung verknüpft sein. Wenn Sie diese Option auswählen, können Sie die Schaltfläche **Vorlage bearbeiten** verwenden, um [die Vorlage in eine Bezeichnung zu konvertieren](configure-policy-templates.md#to-convert-templates-to-labels).
    
     Wenn Sie es gewohnt sind, benutzerdefinierte Vorlagen zu erstellen und zu bearbeiten, sind die [Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben](migrate-portal.md), möglicherweise nützlich für Sie.

7. Wenn Sie **Berechtigungen festlegen** für **Azure (Cloudschlüssel)** ausgewählt haben, können Sie über diese Option Benutzer und Nutzungsrechte auswählen. 
    
    Wenn Sie keine Benutzer auswählen und **OK** in diesem Bereich auswählen, gefolgt von **Speichern** im Bereich " **Bezeichnung** ": die Bezeichnung ist so konfiguriert, dass Sie den Schutz anwendet, sodass nur die Person, die die Bezeichnung anwendet, das Dokument oder die e-Mail ohne Einschränkungen öffnen kann. Diese Konfiguration wird gelegentlich als „Nur für mich“ bezeichnet und ist möglicherweise erforderlich, um sicherzustellen, dass das Dokument an einem beliebigen Ort gespeichert, aber nur von dieser Person geöffnet werden kann. Wenn dies genau das gewünschte Ergebnis ist und keine anderen Personen Zugriff auf den geschützten Inhalt benötigen, wählen Sie nicht **Berechtigungen hinzufügen** aus. Nach dem Speichern der Bezeichnung wird Ihnen beim nächsten Öffnen des Bereichs **Schutz** für **Benutzer** die Option **IPC_USER_ID_OWNER** und für **Berechtigungen** die Option **Mitbesitzer** angezeigt, um diese Konfiguration widerzuspiegeln.
    
    Um die Benutzer anzugeben, die geschützte Dokumente und E-Mails öffnen können sollen, wählen Sie **Berechtigungen hinzufügen**. Wählen Sie dann im Bereich **Berechtigungen hinzufügen** die ersten Benutzer und Gruppen aus, die die Rechte besitzen sollen, den von der ausgewählten Bezeichnung geschützten Inhalt nutzen zu können:
    
   - Wählen Sie **aus der Liste auswählen aus** , in der Sie dann alle Benutzer aus Ihrer Organisation hinzufügen können, indem Sie **Add \<organization name> -All Members** auswählen. Diese Einstellung schließt Gastkonten aus. Sie können auch **Alle authentifizierten Benutzer hinzufügen** auswählen oder das Verzeichnis durchsuchen.
        
       Wenn Sie alle Mitglieder auswählen oder das Verzeichnis durchsuchen, müssen die Benutzer oder Gruppen eine E-Mail-Adresse haben. In einer Produktionsumgebung besitzen Benutzer und Gruppen fast immer E-Mail-Adressen, aber in einer einfachen Testumgebung müssen Sie Benutzerkonten oder Gruppen möglicherweise erst E-Mail-Adressen hinzufügen.
        
       ###### <a name="more-information-about-add-any-authenticated-users"></a>Weitere Informationen zu **Keine authentifizierten Benutzer hinzufügen** 
       Diese Einstellung schränkt nicht ein, wer auf den von der Bezeichnung geschützten Inhalt zugreifen kann, während der Inhalt dennoch verschlüsselt wird und Ihnen Optionen zur Verfügung stehen, wie der Inhalt verwendet (Berechtigungen) und wie auf ihn zugegriffen werden kann (Ablauf und Offlinezugriff). Die Anwendung, die den geschützten Inhalt öffnet, muss jedoch die verwendete Authentifizierung unterstützen. Aus diesem Grund sollten Verbundanbieter sozialer Netzwerke wie Google und die Authentifizierung per Einmalkennung nur für E-Mails verwendet werden, und nur, wenn Sie Exchange Online und die neuen Funktionen der Office 365-Nachrichtenverschlüsselung verwenden. Microsoft-Konten können mit dem Azure Information Protection-Viewer und Klick-und-Los von Office 365-Apps verwendet werden. 
          
       Einige typische Szenarios für die Einstellung „Keine authentifizierten Benutzer“:
       - Ihnen ist egal, wer den Inhalt sehen kann, Sie möchten jedoch einschränken, wie dieser verwendet wird. Beispielsweise soll der Inhalt nicht bearbeitet, kopiert oder gedruckt werden.
       - Sie müssen nicht einschränken, wer auf den Inhalt zugreift, aber Sie möchten nachvollziehen können, wer ihn öffnet, und ihn möglicherweise widerrufen.
       - Sie haben die Anforderung, dass der Inhalt im Ruhezustand und während der Übertragung verschlüsselt sein muss, aber es ist keine Zugriffssteuerung erforderlich.
        
   - Wählen Sie **Details eingeben** aus, um manuell E-Mail-Adressen für einzelne Benutzer oder Gruppen (intern oder extern) anzugeben. Sie können diese Option auch verwenden, um alternativ alle Benutzer in einer Organisation durch die Eingabe eines beliebigen Domänennamens aus dieser Organisation anzugeben. Außerdem können Sie diese Option für soziale Netzwerke verwenden, indem Sie den Domänennamen, z.B. **gmail.com**, **hotmail.com** oder **outlook.com** eingeben.
        
     >[!NOTE]
     >Wenn sich eine E-Mail-Adresse ändert, nachdem Sie den Benutzer oder die Gruppe ausgewählt haben, finden Sie im Abschnitt [Überlegungen für Azure Information Protection bei E-Mail-Adressänderungen](prepare.md#considerations-for-azure-information-protection-if-email-addresses-change) der Planungsdokumentation weitere Informationen.
    
     Verwenden Sie eher Gruppen als Benutzer. Mit dieser Strategie ist Ihre Konfiguration einfacher, und es ist weniger wahrscheinlich, dass Sie Ihre Bezeichnungskonfiguration später aktualisieren und den Inhaltsschutz erneut anwenden müssen. Wenn Sie jedoch die Gruppe ändern, denken Sie daran, dass Azure Rights Management aus Leistungsgründen [die Gruppenmitgliedschaft zwischenspeichert](prepare.md#group-membership-caching-by-azure-information-protection). 
    
    Wenn Sie die erste Gruppe mit Benutzern und Gruppen angegeben haben, wählen Sie die Berechtigungen aus, die diesen Benutzern und Gruppen gewährt werden sollen. Weitere Informationen zu den auswählbaren Berechtigungen finden Sie unter [Konfigurieren von Nutzungsrechten für Azure Information Protection](configure-usage-rights.md). Bei den Anwendungen, die diesen Schutz unterstützen, kann es jedoch Unterschiede hinsichtlich der Implementierung dieser Berechtigungen geben. Lesen Sie die jeweilige Dokumentation, und führen Sie eigene Tests mit den Anwendungen durch, die von den Benutzern verwendet werden, um das Verhalten zu prüfen, bevor Sie die Vorlage für Benutzer bereitstellen.
    
     Falls erforderlich, können Sie jetzt eine zweite Gruppe mit Benutzern und Gruppen mit Nutzungsrechten hinzufügen. Wiederholen Sie den Vorgang, bis Sie alle Benutzer und Gruppen mit den jeweiligen Berechtigungen angegeben haben.

     >[!TIP]
     >Fügen Sie ggf. die benutzerdefinierte Berechtigung **Speichern unter, Exportieren** hinzu, und gewähren Sie diese Administratoren für Datenwiederherstellung oder Mitarbeitern in anderen Rollen, die für die Informationswiederherstellung verantwortlich sind. Falls erforderlich, können diese Benutzer dann den Schutz von Dateien und E-Mails entfernen, die mit dieser Bezeichnung oder Vorlage geschützt werden. Diese Möglichkeit zum Entfernen des Schutzes für ein Dokument oder eine E-Mail auf Berechtigungsebene bietet eine genauere Steuerung als die [Administratorfunktion](configure-super-users.md).
    
     Überprüfen Sie nun im Bereich **Schutz** für alle Benutzer und Gruppen, die Sie angegeben haben, ob Sie Änderungen an den folgenden Einstellungen vornehmen möchten. Beachten Sie, dass diese Einstellungen – ebenso wie die Berechtigungen – weder für den [Rights Management-Aussteller und Rights Management-Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) noch für einen von Ihnen zugewiesenen [Administrator](configure-super-users.md) gelten.
    
     ###### <a name="information-about-the-protection-settings"></a>Informationen zu Schutzeinstellungen
    
     |Einstellung|Weitere Informationen|Empfohlene Einstellung
     |-----------|--------------------|--------------------|
     |**Ablauf des Dateiinhalts**|Definieren Sie ein Datum oder eine Anzahl von Tagen, nach deren Ablauf Dokumente, die durch diese Einstellungen geschützt sind, nicht mehr von ausgewählten Benutzern geöffnet werden sollen. Bei E-Mails wird dieses Ablaufdatum aufgrund von Cachemechanismen, die von manchen E-Mail-Clients verwendet werden, nicht immer erzwungen.<br /><br />Sie können ein Datum oder eine Anzahl von Tagen ab dem Zeitpunkt angeben, an dem der Schutz auf den Inhalt angewendet wird.<br /><br />Wenn Sie ein Datum angeben, beginnt die Gültigkeit um Mitternacht in Ihrer aktuellen Zeitzone.|**Inhalt läuft nie ab**, sofern für den Inhalt keine bestimmte zeitgebundene Begrenzung gilt.|
     |**Offlinezugriff zulassen**|Mit dieser Einstellung können Sie mit der Möglichkeit für ausgewählte Benutzer, geschützte Inhalte zu öffnen, wenn keine Internetverbindung besteht, Ihre bestehenden Sicherheitsanforderungen abstimmen (einschließlich des Zugriffs nach einem Widerruf).<br /><br />Wenn Sie angeben, dass Inhalte ohne Internetverbindung nicht verfügbar oder nur für eine bestimmte Anzahl von Tagen verfügbar sind, müssen sich diese Benutzer bei Erreichen dieses Schwellenwerts erneut authentifizieren, und ihre Zugriffe werden protokolliert. Wenn in diesem Fall die Anmeldeinformationen nicht zwischengespeichert wurden, werden die Benutzer aufgefordert, sich anzumelden, bevor sie das Dokument oder die E-Mail öffnen können.<br /><br />Zusätzlich zur erneuten Authentifizierung werden Richtlinie und Mitgliedschaft in der Benutzergruppe erneut ausgewertet. Das bedeutet, dass Benutzer beim Zugriff auf das gleiche Dokument oder die gleiche E-Mail unterschiedliche Ergebnisse feststellen werden, wenn sich nach ihrem letzten Zugriff auf den Inhalt die Richtlinie oder Gruppenmitgliedschaft geändert hat. Dies könnte bedeuten, dass kein Zugriff möglich ist, wenn das Dokument [widerrufen](./rms-client/client-track-revoke.md) wurde.|Je nach Vertraulichkeit des Inhalts:<br /><br />- **Anzahl der Tage, die der Inhalt ohne Internetverbindung**  =  verfügbar ist **7** für sensible Geschäftsdaten, die dem Unternehmen Schaden zufügen können, wenn Sie für nicht autorisierte Personen freigegeben werden. Diese Empfehlung bietet einen ausgewogenen Kompromiss zwischen Flexibilität und Sicherheit. Beispiele hierfür sind Verträge, Sicherheitsberichte, Prognosen und Vertriebskontodaten.<br /><br />- **Nie** für sehr vertrauliche Geschäftsdaten, die bei Freigabe an nicht autorisierte Personen dem Geschäft schaden. Bei dieser Empfehlung wird der Sicherheit eine höhere Priorität eingeräumt als der Flexibilität. Diese Einstellung stellt sicher, dass bei Widerruf eines Dokuments der Zugriff auf das Dokument durch autorisierte Benutzer sofort gesperrt wird. Beispiele hierfür sind Mitarbeiter- und Kundendaten, Kennwörter, Quellcode und vorab angekündigte Finanzberichte.|
    
     Wenn Sie das Konfigurieren der Berechtigungen und Einstellungen abgeschlossen haben, klicken Sie auf **OK**. 
    
     Diese Gruppe von Einstellungen erstellt eine benutzerdefinierte Vorlage für den Azure Rights Management-Dienst. Diese Vorlagen können für Anwendungen und Dienste verwendet werden, die in Azure Rights Management integriert sind. Informationen zum Herunterladen und Aktualisieren dieser Vorlagen durch Computer und Dienste finden Sie unter [Aktualisieren von Vorlagen für Benutzer und Dienste](refresh-templates.md).

8. Wenn Sie **Vordefinierte Vorlage auswählen** für **Azure (Cloudschlüssel)** ausgewählt haben, klicken Sie auf das Dropdownfeld und wählen die [Vorlage](configure-policy-templates.md) aus, die Sie verwenden möchten, um Dokumente und E-Mails mit dieser Bezeichnung zu schützen. Es werden keine archivierten Vorlagen oder Vorlagen angezeigt, die bereits für eine andere Bezeichnung ausgewählt wurden.
    
    Wenn Sie eine **Abteilungsvorlage** ausgewählt oder [Onboardingsteuerelemente](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, gilt Folgendes:
    
    - Benutzer außerhalb des konfigurierten Bereichs der Vorlage oder Benutzer, die von der Anwendung des Azure Rights Management-Schutzes ausgeschlossen wurden, sehen die Bezeichnung weiterhin, können sie aber nicht anwenden. Wenn Sie die Bezeichnung auswählen, wird die folgende Meldung angezeigt: **Azure Information Protection diese Bezeichnung nicht anwenden können. Wenn dieses Problem weiterhin besteht, wenden Sie sich an Ihren Administrator.**
        
        Beachten Sie, dass alle veröffentlichten Vorlagen immer angezeigt werden, auch wenn Sie eine bereichsbezogene Richtlinie konfigurieren. Ein Beispiel: Sie konfigurieren eine bereichsbezogene Richtlinie für die Gruppe „Marketing“. Die zur Auswahl stehenden Vorlagen sind nicht auf diejenigen Vorlagen beschränkt, die nur für den Bereich der Gruppe „Marketing“ gelten, und es ist möglich, eine Abteilungsvorlage auszuwählen, die Ihre gewünschten Benutzer nicht verwenden können. Um die Konfiguration zu vereinfachen und potenzielle Probleme zu minimieren, sollten Sie erwägen, die Abteilungsvorlage entsprechend der Bezeichnung in Ihrer bereichsbezogenen Richtlinie zu benennen. 

9. Wenn Sie **HYOK (AD RMS)** ausgewählt haben, wählen Sie entweder **AD RMS-Vorlagendetails festlegen** oder **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus. Geben Sie dann die Lizenzierungs-URL Ihres AD RMS-Clusters an.
    
    Anweisungen zum Angeben einer Vorlagen-GUID und Ihrer Lizenzierungs-URL finden Sie unter [Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung](configure-adrms-restrictions.md#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label).
    
    Mit der Option für benutzerdefinierte Berechtigungen können Benutzer angeben, wem welche Berechtigungen erteilt werden. Sie können diese Option genauer definieren und „Nur Outlook“ (Standardeinstellung), „Word“, „Excel“, „PowerPoint“ oder „Datei-Explorer“ auswählen. Diese Option wird nicht unterstützt und funktioniert nicht, wenn eine Bezeichnung für die [automatische Klassifizierung](configure-policy-classification.md) konfiguriert ist.
    
    Wenn Sie die Option für Outlook auswählen: die Bezeichnung wird in Outlook angezeigt, und das resultierende Verhalten, wenn Benutzer die Bezeichnung anwenden, ist identisch mit der Option [nicht weiterleiten](configure-usage-rights.md#do-not-forward-option-for-emails) .
    
    Bei Auswahl der Option für Word, Excel, PowerPoint und Datei-Explorer gilt Folgendes: Wenn diese Option festgelegt ist, wird die Bezeichnung in diesen Anwendungen angezeigt. Nachdem die Benutzer die Bezeichnung angewendet haben, wird ein Dialogfeld zur Auswahl von benutzerdefinierten Berechtigungen angezeigt. In diesem Dialogfeld wählen Benutzer eine der [vordefinierten Berechtigungsstufen](configure-usage-rights.md#rights-included-in-permissions-levels) aus, navigieren dann zu dem Benutzer oder der Gruppe (bzw. geben diese an) und legen optional ein Ablaufdatum fest. Stellen Sie sicher, dass die Benutzer über die notwendigen Anweisungen und Anleitungen zum Bereitstellen dieser Werte verfügen.

10. Klicken Sie auf **OK**, um den Bereich **Schutz** zu schließen und die Auswahl für **Benutzerdefiniert** bzw. die ausgewählte Vorlage für die Option **Schutz** im Bereich **Bezeichnung** anzuzeigen.

11. Klicken Sie im Bereich **Bezeichnung** auf **Speichern**.

12. Verwenden Sie im Bereich **Azure Information Protection** die Spalte **PROTECTION** (Schutz), um zu bestätigen, dass Ihre Bezeichnung nun die gewünschten Schutzeinstellungen darstellt:
    
    - Ein Häkchen, wenn Sie den Schutz konfiguriert haben 
    
    - Ein X zum Kennzeichnen eines Abbruchs, wenn Sie eine Bezeichnung zum Entfernen des Schutzes konfiguriert haben
    
    - Ein leeres Feld, wenn der Schutz nicht eingerichtet ist 

Sobald Sie auf **Speichern** klicken, werden Ihre vorgenommenen Änderungen automatisch Benutzern und Diensten zur Verfügung gestellt. Es gibt keine gesonderte Veröffentlichungsoption mehr.


## <a name="example-configurations"></a>Beispielkonfigurationen

Die untergeordneten Bezeichnungen **Alle Mitarbeiter** und **Nur Empfänger** der Bezeichnungen **Vertraulich** und **Streng vertraulich** aus der [Standardrichtlinie](configure-policy-default.md) bieten Beispiele dafür, wie Sie Bezeichnungen zum Anwenden des Schutzes konfigurieren können. Sie können auch die folgenden Beispiele verwenden, um den Schutz für verschiedene Szenarien zu konfigurieren. 

Wählen Sie für jedes nachfolg folgende Beispiel in Ihrem Bereich \<*label name*> **schützen** aus. Klicken Sie auf **Schutz**, um diesen Bereich zu öffnen, wenn der Bereich **Schutz** nicht automatisch geöffnet wird. Dort können Sie die Konfigurationsoptionen für den Schutz auswählen:

![Konfigurieren des Schutzes für eine Azure Information Protection-Bezeichnung](./media/info-protect-protection-bar-configured.png)

### <a name="example-1-label-that-applies-do-not-forward-to-send-a-protected-email-to-a-gmail-account"></a>Beispiel 1: Bezeichnung, die „Nicht weiterleiten“ anwendet, um eine geschützte E-Mail an ein Gmail-Konto zu senden

Diese Bezeichnung ist nur in Outlook verfügbar und eignet sich in Fällen, in denen Exchange Online für die [neuen Funktionen bei der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) konfiguriert ist. Weisen Sie Ihre Benutzer an, diese Bezeichnung auszuwählen, wenn sie eine geschützte E-Mail an Personen senden müssen, die ein Gmail-Konto (oder ein anderes E-Mail-Konto außerhalb Ihrer Organisation) verwenden. 

Die Benutzer geben die Gmail-Adresse in das Feld **An** ein.  Danach wählen sie die Bezeichnung aus, und die Option „Nicht weiterleiten“ wird der E-Mail automatisch hinzugefügt. Das Ergebnis ist, dass die Empfänger die e-Mail nicht weiterleiten oder drucken, kopieren oder die e-Mail außerhalb Ihres Postfachs speichern können, indem Sie die Option **Speichern** unter verwenden. 

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Wählen Sie die Option **Benutzerdefinierte Berechtigungen festlegen (Vorschau)** aus.

3. Stellen Sie sicher, dass die folgende Option ausgewählt ist: **In Outlook apply Do Not Forward** („Nicht weiterleiten“ in Outlook anwenden).

4. Wenn die Option ausgewählt ist, deaktivieren Sie die folgende Option: **In Word, Excel, PowerPoint and File Explorer prompt user for custom permissions** (Vom Benutzer in Word, Excel, PowerPoint und dem Datei-Explorer benutzerdefinierte Berechtigungen verlangen).

5. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.


### <a name="example-2-label-that-restricts-read-only-permission-to-all-users-in-another-organization-and-that-supports-immediate-revocation"></a>Beispiel 2: Bezeichnung, die den Schreibschutz auf alle Benutzer in einer anderen Organisation anwendet und den sofortigen Widerruf unterstützt

Diese Bezeichnung eignet sich für die (schreibgeschützte) Freigabe von streng vertraulichen Dokumenten, für deren Ansicht stets eine Internetverbindung erforderlich ist. Wenn ein solches Dokument widerrufen wird, kann es von Benutzern nicht mehr angezeigt werden, wenn diese versuchen, es erneut zu öffnen.

Diese Bezeichnung eignet sich nicht für E-Mails.

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass die Option **Berechtigungen festlegen** ausgewählt ist, und wählen Sie dann **Berechtigungen hinzufügen** aus.

3. Klicken Sie im Bereich **Berechtigungen hinzufügen** auf **Details eingeben**.

4. Geben Sie den Namen einer Domäne der anderen Organisation ein, z.B. **fabrikam.com**. Wählen Sie anschließend **Hinzufügen**.

5. Wählen Sie unter **Berechtigungen aus Voreinstellung auswählen** die Option **Viewer** aus, und klicken Sie dann auf **OK**.

6. Wählen Sie im Bereich **Schutz** für die Einstellung **Offlinezugriff zulassen** erneut **Nie** aus.

7. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.


### <a name="example-3-add-external-users-to-an-existing-label-that-protects-content"></a>Beispiel 3: Hinzufügen von externen Benutzern zu einer bestehenden Bezeichnung, die Inhalte schützt

Die von Ihnen hinzugefügten neuen Benutzer können Dokumente und E-Mails öffnen, die bereits mit dieser Bezeichnung geschützt sind. Die Berechtigungen, die Sie diesen Benutzern zuweisen, können sich von den Berechtigungen unterscheiden, über die vorhandene Benutzer verfügen.

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und wählen Sie dann **Berechtigungen hinzufügen** aus.

3. Klicken Sie im Bereich **Berechtigungen hinzufügen** auf **Details eingeben**.

4. Geben Sie die E-Mail-Adresse des ersten Benutzers oder der ersten Gruppe ein, den bzw. die Sie hinzufügen möchten, und wählen Sie dann **Hinzufügen** aus.

5. Wählen Sie die Berechtigungen für diesen Benutzer bzw. diese Gruppe aus.

6. Wiederholen Sie die Schritte 4 und 5 für jeden Benutzer oder jede Gruppe, den bzw. die Sie dieser Bezeichnung hinzufügen möchten. Klicken Sie dann auf **OK**.

7. Klicken Sie im Bereich **Schutz** auf **OK** und im Bereich **Bezeichnung** auf **Speichern**.

### <a name="example-4-label-for-protected-email-that-supports-less-restrictive-permissions-than-do-not-forward"></a>Beispiel 4: Bezeichnung für geschützte E-Mails, die weniger restriktive Berechtigungen als „Nicht weiterleiten“ unterstützt

Diese Bezeichnung kann nicht auf Outlook beschränkt werden, bietet jedoch eine weniger restriktive Steuerung als „Nicht weiterleiten“. Beispielsweise sollten Empfänger aus einer E-Mail oder einem Anhang kopieren oder einen Anhang speichern und bearbeiten können.

Wenn Sie externe Benutzer angeben, die kein Azure AD-Konto haben, gilt Folgendes:

- Die Bezeichnung eignet sich für E-Mails, wenn Exchange Online die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) verwendet. 
 
- Für Office-Anlagen, die automatisch geschützt sind, stehen diese Dokumente für eine Browservorschau zur Verfügung. Um diese Dokumente zu bearbeiten, laden Sie sie herunter, und bearbeiten Sie sie mit Office 365-Apps (Klick-und-Los) und einem Microsoft-Konto, das dieselbe E-Mail-Adresse verwendet. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)


> [!NOTE]
> In Exchange Online wird eine neue Option eingeführt: [Encrypt-Only](configure-usage-rights.md#encrypt-only-option-for-emails). Diese Option ist für das Konfigurieren von Bezeichnungen nicht verfügbar. Wenn Sie die Empfänger jedoch kennen, können Sie mit diesem Beispiel eine Bezeichnung mit denselben Nutzungsrechten konfigurieren. 

Wenn Ihre Benutzer die E-Mail-Adressen im Feld **An** angeben, müssen die Adressen zu den Benutzern gehören, die Sie für diese Bezeichnungskonfiguration angegeben haben. Da Benutzer zu Gruppen gehören und über mehrere E-Mail-Adressen verfügen können, muss die E-Mail-Adresse, die sie verwenden, nicht mit der E-Mail-Adresse übereinstimmen, die Sie für die Berechtigungen angegeben haben. Die Angabe derselben E-Mail-Adresse ist jedoch die einfachste Möglichkeit, um sicherzustellen, dass der Empfänger erfolgreich autorisiert wird. Weitere Informationen dazu, wie Benutzer für Berechtigungen autorisiert werden, finden Sie unter [Vorbereiten von Benutzern und Gruppen für Azure Information Protection](prepare.md). 

1. Stellen Sie sicher, dass im Bereich **Schutz** die Option **Azure (cloud key)** (Azure (Cloudschlüssel)) ausgewählt ist.
    
2. Stellen Sie sicher, dass **Berechtigungen festlegen** ausgewählt ist, und wählen Sie dann **Berechtigungen hinzufügen** aus.

3. Wählen Sie im Bereich **Berechtigungen hinzufügen** : um Benutzern in Ihrer Organisation Berechtigungen zu erteilen, wählen Sie **Hinzufügen \<organization name> -Alle Mitglieder** aus, um alle Benutzer in Ihrem Mandanten auszuwählen. Diese Einstellung schließt Gastkonten aus. Alternativ dazu klicken Sie auf **Verzeichnis durchsuchen**, um eine bestimmte Gruppe auszuwählen. Klicken Sie auf **Details eingeben**, und geben Sie die E-Mail-Adresse des Benutzers oder die Azure AD-Gruppe oder einen Domänennamen ein, um externen Benutzern Berechtigungen zu erteilen oder wenn Sie die E-Mail-Adresse lieber manuell eingeben möchten.
    
    Wiederholen Sie diesen Schritt, um weitere Benutzer anzugeben, die über die gleichen Berechtigungen verfügen sollen.

4. Klicken Sie unter **Berechtigungen aus Voreinstellung auswählen** auf **Mitbesitzer**, **Mitautor**, **Prüfer** oder **Benutzerdefiniert**, um die gewünschten Berechtigungen auszuwählen.
    
    Hinweis: Wählen Sie für E-Mails nicht **Viewer** aus, und wenn Sie **Benutzerdefiniert** auswählen, stellen Sie sicher, dass Sie die Berechtigung **Bearbeiten und speichern** einschließen.
    
    Um dieselben Berechtigungen wie bei der neuen Exchange Online-Option **Nur verschlüsseln** zu haben, wählen Sie **Benutzerdefiniert** aus. Gewähren Sie dann alle Berechtigungen außer **Speichern unter, Exportieren (EXPORT)** und **Vollzugriff (OWNER)**.

5. Um weitere Benutzer anzugeben, die über unterschiedliche Berechtigungen verfügen sollen, wiederholen Sie die Schritte 3 und 4.

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