---
title: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client
description: Informationen zum Anpassen des Azure Information Protection-Clients für Windows
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 03/20/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: de1febc25d5fa5518f7ffca5d51895bebd2cd56b
ms.sourcegitcommit: 3a3f1051c5a58c2bd2f230f1c8ece919df3dc23e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/20/2019
ms.locfileid: "58221081"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie bei der Verwaltung des Azure Information Protection-Clients möglicherweise für spezifische Szenarien oder eine Teilmenge der Benutzer benötigen.

Einige dieser Einstellungen erfordern die Bearbeitung der Registrierung. Andere sind erweiterte Einstellungen, die Sie im Azure-Portal konfigurieren und anschließend für das Herunterladen durch Clients veröffentlichen müssen.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Konfigurieren erweiterter Clientkonfigurationseinstellungen im Portal

1. Melden Sie sich ggf. in einem neuen Browserfenster beim [Azure-Portal](../configure-policy.md#signing-in-to-the-azure-portal) an, und navigieren Sie zum Blatt **Azure Information Protection**.

2. Über die Menüoptionen **Klassifizierungen** > **Bezeichnungen**: Wählen Sie **Richtlinien** aus.

3. Auf dem Blatt **Azure Information Protection – Richtlinien** wählen Sie das Kontextmenü (**...**) neben der Richtlinie aus, um die erweiterten Einstellungen einzuschließen. Wählen Sie dann **Erweiterte Einstellungen** aus.
    
    Sie können erweiterte Einstellungen für die globale Richtlinie sowie für bereichsbezogene Richtlinien konfigurieren.

4. Geben Sie auf dem Blatt **Erweiterte Einstellungen** den Namen und Wert der erweiterten Einstellung ein, und klicken Sie dann auf **Speichern und schließen**.

5. Stellen Sie sicher, dass Benutzer, für die diese Richtlinie gilt, alle Office-Anwendungen neu starten, die geöffnet waren.

6. Wenn Sie die Einstellung nicht mehr benötigen und zum Standardverhalten zurückkehren möchten: Rufen Sie auf dem Blatt **Erweiterte Einstellungen** das Kontextmenü (**...**) neben der Einstellung auf, die Sie nicht mehr benötigen, und wählen Sie dann **Löschen** aus. Klicken Sie anschließend auf **Speichern und Schließen**.

#### <a name="available-advanced-client-settings"></a>Verfügbare erweiterte Clienteinstellungen

|Einstellung|Szenario und Anweisungen|
|----------------|---------------|
|DisableDNF|[Ausblenden der Schaltfläche „Nicht weiterleiten“ in Outlook](#hide-or-show-the-do-not-forward-button-in-outlook)|
|CompareSubLabelsInAttachmentAction|[Aktivieren der Unterstützung der Reihenfolge für untergeordnete Bezeichnungen](#enable-order-support-for-sublabels-on-attachments) 
|EnableBarHiding|[Die Azure Information Protection-Leiste dauerhaft ausblenden](#permanently-hide-the-azure-information-protection-bar)|
|EnableCustomPermissions|[Verfügbar- oder Nicht-Verfügbarmachen der Optionen für benutzerdefinierte Berechtigungen für Benutzer](#make-the-custom-permissions-options-available-or-unavailable-to-users)|
|EnableCustomPermissionsForCustomProtectedFiles|[Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien](#for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer) |
|EnablePDFv2Protection|[Schützen Sie keine PDF-Dateien mithilfe des ISO-Standards für die PDF-Verschlüsselung.](#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption)|
|LabelbyCustomProperty|[Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions)|
|LabelToSMIME|[Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden](#configure-a-label-to-apply-smime-protection-in-outlook)|
|LogLevel|[Ändern des lokalen Protokolliergrads](#change-the-local-logging-level)
|OutlookBlockUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookCollaborationTrustedDomains|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookDefaultLabel|[Festlegen einer anderen Standardbezeichnung für Outlook](#set-a-different-default-label-for-outlook)|
|OutlookJustifyUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|OutlookRecommendationEnabled|[Die empfohlene Klassifizierung in Outlook aktivieren](#enable-recommended-classification-in-outlook)|
|OutlookWarnUntrustedCollaborationLabel|[Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben](#implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent)|
|PostponeMandatoryBeforeSave|[Deaktivieren der Option „Nicht jetzt“ für Dokumente bei Verwendung der obligatorischen Bezeichnung](#remove-not-now-for-documents-when-you-use-mandatory-labeling)|
|ProcessUsingLowIntegrity|[Deaktivieren der niedrigen Integritätsebene für den Scanner](#disable-the-low-integrity-level-for-the-scanner)|
|PullPolicy|[Unterstützung für getrennte Computer](#support-for-disconnected-computers)
|RemoveExternalContentMarkingInApp|[Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen](#remove-headers-and-footers-from-other-labeling-solutions)|
|ReportAnIssueLink|[Add "Report an Issue" for users](#add-report-an-issue-for-users) ("Problem melden" für Benutzer hinzufügen)|
|RunPolicyInBackground|[Aktivieren der dauerhaft im Hintergrund ausgeführten Klassifizierung](#turn-on-classification-to-run-continuously-in-the-background)|
|ScannerConcurrencyLevel|[Begrenzen der Anzahl der von der Überprüfung verwendeten Threads](#limit-the-number-of-threads-used-by-the-scanner)|
|SyncPropertyName|[Hinzufügen einer Bezeichnung zu einem Office-Dokument über eine bereits bestehende benutzerdefinierte Eigenschaft](#label-an-office-document-by-using-an-existing-custom-property)|
|SyncPropertyState|[Hinzufügen einer Bezeichnung zu einem Office-Dokument über eine bereits bestehende benutzerdefinierte Eigenschaft](#label-an-office-document-by-using-an-existing-custom-property)|

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Verhindern von Anmeldeaufforderungen für Computer, die nur AD RMS verwenden

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen. Diese Konfiguration kann bei Computern, die nur mit AD RMS kommunizieren, zu einer unnötigen Anmeldeaufforderung für Benutzer führen. Sie können diese Anmeldeaufforderung verhindern, indem Sie die Registrierung bearbeiten:

 - Suchen Sie nach dem folgenden Wertnamen, und legen Sie anschließend die Wertdaten auf **0** fest:
    
    **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Unabhängig von dieser Einstellung folgt der Azure Information Protection-Client dem [Prozess zur RMS-Diensterkennung](client-deployment-notes.md#rms-service-discovery), um sein AD RMS-Cluster zu finden.

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als ein anderer Benutzer anmelden, wenn sie den Azure Information Protection-Client verwenden. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

Mithilfe des Dialogfelds **Microsoft Azure Information Protection** können Sie prüfen, an welchem Konto Sie derzeit angemeldet sind: Öffnen Sie eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen) und anschließend auf **Help and feedback** (Hilfe und Feedback). Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. Ein Hinweis auf das Verwenden des falschen Kontos können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige der Bezeichnungen oder unerwartete Verhaltensweisen sein.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Wenn der Azure Information Protection-Client nach Abschluss dieser Schritte noch mit dem alten Konto angemeldet ist, löschen Sie im Internet Explorer alle Cookies, und wiederholen Sie dann die Schritte 1 und 2.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich bei Windows abmelden und mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Tokendatei gelöscht haben. Der Azure Information Protection-Client wird automatisch mit Ihrem aktuell angemeldeten Benutzerkonto authentifiziert.

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- Sie können die Option **Einstellungen zurücksetzen** unter **Hilfe und Feedback** verwenden, um sich abzumelden und die aktuell heruntergeladene Azure Information Protection-Richtlinie zu löschen.


## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Erzwingen des reinen Schutzmodus, wenn die Organisation über eine Kombination verschiedener Lizenzen verfügt

Wenn Ihre Organisation keine Lizenzen für Azure Information Protection besitzt, aber über Lizenzen für Office 365 verfügt, die den Azure Rights Management-Dienst für den Datenschutz umfassen, wird der Azure Information Protection-Client für Windows automatisch im [reinen Schutzmodus](client-protection-only-mode.md) ausgeführt.

Wenn Ihre Organisation jedoch über ein Abonnement für Azure Information Protection verfügt, können standardmäßig alle Windows-Computer die Azure Information Protection-Richtlinie herunterladen. Der Azure Information Protection-Client ist nicht für die Überprüfung und Erzwingung von Lizenzen zuständig. 

Wenn einige Ihrer Benutzer keine Lizenz für Azure Information Protection, aber eine Lizenz für Office 365 haben, die den Azure Rights Management-Dienst umfasst, bearbeiten Sie die Registrierung auf den Computern dieser Benutzer, um zu verhindern, dass diese Benutzer die nicht lizenzierten Klassifizierungs- und Bezeichnungsfeatures von Azure Information Protection ausführen.

Suchen Sie nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Überprüfen Sie außerdem, ob auf diesen Computern eine Datei namens **Policy.msip** im Ordner **%LocalAppData%\Microsoft\MSIP** vorhanden ist. Wenn diese Datei vorhanden ist, löschen Sie sie. Diese Datei enthält die Azure Information Protection-Richtlinie und wurde möglicherweise heruntergeladen, bevor Sie die Registrierung bearbeitet haben. Die Datei kann auch vorhanden sein, wenn der Azure Information Protection-Client mit der Demooption installiert wurde.

## <a name="add-report-an-issue-for-users"></a>Add "Report an Issue" for users ("Problem melden" für Benutzer hinzufügen)

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie die folgende erweiterte Clienteinstellung angeben, wird Benutzern die Option **Problem melden** angezeigt, die sie aus dem Clientdialogfeld **Hilfe und Feedback** auswählen können. Geben Sie eine HTTP-Zeichenfolge für den Link an. Beispiele dafür sind eine benutzerdefinierte Webseite, über die Benutzer Probleme melden, oder eine E-Mail-Adresse, die E-Mails an Ihren Helpdesk weiterleitet. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **ReportAnIssueLink**

- Wert: **\<HTTP-Zeichenfolge>**

Beispielwert für eine Website: `https://support.contoso.com`

Beispielwert für eine E-Mail-Adresse: `mailto:helpdesk@contoso.com`

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ausblenden der Menüoption „Klassifizieren und schützen“ im Windows-Dateiexplorer

Erstellen Sie den folgenden DWORD-Wert (mit beliebigen Wertdaten):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Unterstützung für getrennte Computer

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen, um die neueste Azure Information Protection-Richtlinie herunterzuladen. Wenn Sie über Computer verfügen, von denen Sie wissen, dass sie für einen bestimmten Zeitraum keine Verbindung mit dem Internet herstellen können, können Sie den Client durch Bearbeiten der Registrierung am Verbindungsversuch mit dem Dienst hindern. 

Beachten Sie, dass ohne Internetverbindung der Client keinen Schutz durch den cloudbasierten Schlüssel Ihrer Organisation anwenden (oder entfernen) kann. Stattdessen ist der Client auf die Verwendung von Bezeichnungen beschränkt, für die ausschließlich die Klassifizierung verwendet wird, oder auf den Schutz mit [HYOK](../configure-adrms-restrictions.md).

Sie können eine Anmeldeaufforderung für den Azure Information Protection-Dienst verhindern, indem Sie eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal) verwenden. Diese müssen Sie im Azure-Portal konfigurieren und die Richtlinie dann für Computer herunterladen. Darüber hinaus können Sie dies diese Anmeldeaufforderung verhindern, indem Sie die Registrierung bearbeiten:

- So konfigurieren Sie die erweiterte Clienteinstellung:
    
    1. Geben Sie die folgende Zeichenfolge ein:
    
        - Legende: **PullPolicy**
        
        - Wert: **False**
    
    2. Laden Sie die Richtlinie mit dieser Einstellung herunter und installieren Sie sie auf Computern, indem Sie die folgenden Anweisungen befolgen.

- Alternativ können Sie auch die Registrierung bearbeiten:
    
    - Suchen Sie nach dem folgenden Wertnamen, und legen Sie anschließend die Wertdaten auf **0** fest:
    
        **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 


Der Client benötigt eine gültige Richtliniendatei **Policy.msip** im Ordner **%LocalAppData%\Microsoft\MSIP**.

Sie können die globale oder eine bereichsbezogene Richtlinie aus dem Azure-Portal exportieren und die exportierte Datei auf den Clientcomputer kopieren. Sie können mithilfe dieser Methode auch eine veraltete Richtliniendatei durch die neueste Richtlinie ersetzen. Der Export der Richtlinie unterstützt jedoch nicht das Szenario, in dem ein Benutzer zu mehr als einer bereichsbezogenen Richtlinie gehört. Beachten Sie auch Folgendes: Wenn Benutzer die Option **Einstellungen zurücksetzen** aus [Hilfe und Feedback](client-admin-guide.md#help-and-feedback-section) auswählen, löscht diese Aktion die Richtliniendatei und macht den Client funktionsunfähig, bis Sie die Richtliniendatei manuell ersetzen, oder der Client eine Verbindung mit dem Dienst zum Herunterladen der Richtlinie herstellt.

Wenn Sie die Richtlinie aus dem Azure-Portal exportieren, wird eine ZIP-Datei heruntergeladen, die mehrere Versionen der Richtlinie enthält. Diese Richtlinienversionen entsprechen verschiedenen Versionen des Azure Information Protection-Clients:

1. Entzippen Sie die Datei, und verwenden Sie die folgende Tabelle, um zu identifizieren, welche Richtliniendatei Sie benötigen. 
    
    |Dateiname|Entsprechende Clientversion|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |Version 1.2|
    |Policy1.2.msip |Version 1.3 – 1.7|
    |Policy1.3.msip |Version 1.8 – 1.29|
    |Policy1.4.msip |Version 1.32 und höher|
    
2. Benennen Sie die identifizierte Datei zu **Policy.msip** um, und kopieren Sie sie in den Ordner **%LocalAppData%\Microsoft\MSIP** auf Computern, auf denen der Azure Information Protection-Client installiert ist. 

Wenn auf dem nicht verbundenen Computer die Vorschauversion des Azure Information Protection-Scanners ausgeführt wird, müssen Sie zusätzliche Konfigurationsschritte durchführen. Weitere Informationen hierzu finden Sie unter [Einschränkung: Der Überprüfungsserver kann über keine Internetkonnektivität verfügen](../deploy-aip-scanner-preview.md#restriction-the-scanner-server-cannot-have-internet-connectivity) in den Anweisungen zur Bereitstellung des Scanners.

## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ausblenden oder Anzeigen der Schaltfläche „Nicht weiterleiten“ in Outlook

Das empfohlene Vorgehen zum Konfigurieren dieser Option ist die Verwendung der [Richtlinieneinstellung](../configure-policy-settings.md) **Add the Do Not Forward button to the Outlook ribbon** (Die Schaltfläche „Nicht weiterleiten“ dem Outlook-Menüband hinzufügen). Allerdings können Sie diese Option auch mithilfe einer [erweiterten Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal) konfigurieren. Dies können Sie über das Azure-Portal durchführen.

Wenn Sie diese Einstellung konfigurieren, wird die Schaltfläche **Nicht weiterleiten** auf dem Menüband in Outlook ausgeblendet oder angezeigt. Diese Einstellung hat keine Auswirkung auf die Option „Nicht weiterleiten“ der Office-Menüs.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **DisableDNF**

- Wert: **TRUE** zum Ausblenden der Schaltfläche, **FALSE** zum Anzeigen der Schaltfläche

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Verfügbar- oder Nicht-Verfügbarmachen der Optionen für benutzerdefinierte Berechtigungen für Benutzer

Das empfohlene Vorgehen zum Konfigurieren dieser Option ist die Verwendung der [Richtlinieneinstellung](../configure-policy-settings.md) **Make the custom permissions option available for users** (Die benutzerdefinierte Berechtigungsoption für Benutzer verfügbar machen). Allerdings können Sie diese Option auch mithilfe einer [erweiterten Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal) konfigurieren. Dies können Sie über das Azure-Portal durchführen. 

Wenn Sie diese Einstellung konfigurieren und die Richtlinie für Benutzer veröffentlichen, werden die benutzerdefinierten Berechtigungsoptionen für Benutzer sichtbar, woraufhin diese ihre eigenen Schutzeinstellungen auswählen können. Alternativ werden die Optionen ausgeblendet, damit Benutzer ihre Schutzeinstellungen nicht auswählen können, es sei denn, sie werden dazu aufgefordert.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **EnableCustomPermissions**

- Wert: **TRUE**, um die Option für benutzerdefinierte Berechtigungen anzuzeigen, **FALSE**, um diese Option auszublenden

## <a name="for-files-protected-with-custom-permissions-always-display-custom-permissions-to-users-in-file-explorer"></a>Ständiges Anzeigen von benutzerdefinierten Berechtigungen für Benutzer im Dateiexplorer für mit benutzerdefinierten Berechtigungen geschützte Dateien

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Diese Einstellung befindet sich derzeit in der Vorschau und erfordert die Vorschauversion des Clients.

Wenn Sie die [Richtlinieneinstellung](../configure-policy-settings.md) **Option für benutzerdefinierte Berechtigungen für Benutzer verfügbar machen** oder die entsprechende Clienteinstellung im vorherigen Abschnitt konfigurieren, können Benutzer benutzerdefinierte Berechtigungen nicht sehen oder ändern, die für ein geschütztes Dokument bereits festgelegt wurden. 

Wenn Sie diese erweiterte Clienteinstellung erstellen und konfigurieren, können Benutzer Berechtigungen für ein geschütztes Dokument sehen und ändern, wenn sie den Dateiexplorer verwenden, und mit der rechten Maustaste auf die Datei klicken. Die Option **Benutzerdefinierte Berechtigungen** über die Schaltfläche **Schützen** auf dem Office-Menüband bleibt ausgeblendet.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **EnableCustomPermissionsForCustomProtectedFiles**

- Wert: **True**

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Azure Information Protection-Leiste dauerhaft ausblenden

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Verwenden Sie diese nur, wenn die [Richtlinieneinstellung](../configure-policy-settings.md) **Display the Information Protection bar in Office apps** (Die Information Protection-Leiste in Office-Apps anzeigen) auf **Ein** festgelegt ist.

Wenn ein Benutzer standardmäßig die Option **Leiste anzeigen** von der Registerkarte **Start** entfernt, werden die **Schutzgruppe**, die Schaltfläche **Schützen** und die Leiste „Information Protection“ nicht länger in der Office-App angezeigt. Die Leiste wird jedoch automatisch wieder beim nächsten Öffnen der Office-App angezeigt.

Verwenden Sie diese Clienteinstellung, um zu verhindern, dass die Leiste automatisch wieder angezeigt wird, nachdem der Benutzer diese ausgeblendet hat. Diese Einstellung hat keine Auswirkung, wenn der Benutzer die Leiste mithilfe des Symbols **Diese Leiste schließen** schließt.

Obwohl die Azure Information Protection-Leiste ausgeblendet bleibt, können Benutzer weiterhin eine Bezeichnung auf einer vorübergehend angezeigten Leiste auswählen, wenn Sie die empfohlene Klassifizierung konfiguriert haben oder ein Dokument oder eine E-Mail eine Bezeichnung aufweisen muss. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **EnableBarHiding**

- Wert: **True**

## <a name="enable-order-support-for-sublabels-on-attachments"></a>Aktivieren der Unterstützung der Reihenfolge für untergeordnete Bezeichnungen bei Anlagen

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Verwenden Sie diese Einstellung, wenn Sie über untergeordnete Bezeichnungen verfügen und die folgende [Richtlinieneinstellung](../configure-policy-settings.md) konfiguriert haben:

- **Für E-Mail-Nachrichten mit Anlagen eine Bezeichnung anwenden, die der höchsten Einstufung dieser Anlagen entspricht**

Konfigurieren Sie die folgenden Zeichenfolgen:

- Legende: **CompareSubLabelsInAttachmentAction**

- Wert: **True**

Ohne diese Einstellung wird die erste untergeordnete Bezeichnung, die unter der höchsten übergeordneten Bezeichnung gefunden wird, auf die E-Mail angewendet.

## <a name="enable-recommended-classification-in-outlook"></a>Aktivieren der empfohlenen Klassifizierung in Outlook

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Diese Einstellung befindet sich in der Vorschauversion und kann sich ändern.

Wenn Sie eine Bezeichnung für die empfohlene Klassifizierung konfigurieren, werden Benutzer dazu aufgefordert, die empfohlene Bezeichnung in Word, Excel und PowerPoint anzunehmen oder abzulehnen. Diese Einstellung erweitert diese Bezeichnungsempfehlung, sodass sie auch in Outlook angezeigt wird.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **OutlookRecommendationEnabled**

- Wert: **True**

## <a name="implement-pop-up-messages-in-outlook-that-warn-justify-or-block-emails-being-sent"></a>Implementieren von Popupmeldungen in Outlook, die E-Mails während des Sendens legitimieren, blockieren oder Warnungen für sie ausgeben

Diese Konfiguration verwendet mehrere [erweiterte Clienteinstellungen](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Diese Einstellung befindet sich derzeit in der Vorschau und erfordert die Vorschauversion des Clients.

Wenn Sie die folgenden erweiterten Clienteinstellungen erstellen und konfigurieren, werden Benutzern Popupmeldungen in Outlook angezeigt, die sie vor dem Senden einer E-Mail warnen können, oder sie nach einer Legitimierung fragen, warum sie eine E-Mail versenden, oder sie aus folgenden Gründen davon abhalten, eine E-Mail zu senden:

- **Die E-Mail oder der E-Mail-Anhang hat eine bestimmte Bezeichnung:**
    - Der Anhang kann einen beliebigen Dateityp haben

- **Die E-Mail oder der E-Mail-Anhang hat keine bestimmte Bezeichnung:**
    - Der Anhang kann ein Office-Dokument oder ein PDF-Dokument sein

Wenn diese Bedingungen erfüllt sind, und die E-Mail-Adresse des Empfängers nicht in einer Liste zulässiger Domänennamen enthalten ist, die Sie festgelegt haben, wird dem Benutzer eine Popupmeldung mit einer der folgenden Aktionen angezeigt:

- **Warnung:** Der Benutzer kann bestätigen und senden, oder abbrechen.

- **Justify** (Legitimation): Der Benutzer wird zu einer Legitimierung aufgefordert (mit vordefinierten Optionen oder Freiform).  Der Benutzer kann dann die E-Mail senden oder abbrechen. Der Legitimationstext wird in den X-Header der E-Mail geschrieben, sodass dieser von anderen Systemen gelesen werden kann. Zum Beispiel von Diensten, die der Verhinderung von Datenverlust dienen.

- **Blockieren:** Der Benutzer wird davon abgehalten, die E-Mail zu senden, solange die Bedingung besteht. Die Nachricht beinhaltet den Grund dafür, warum die E-Mail blockiert wird, sodass der Benutzer das Problem aufheben kann. So kann er z.B. bestimmte Empfänger entfernen, oder der E-Mail eine Bezeichnung hinzufügen. 

Die daraus resultierende Aktion wird im lokalen Windows-Ereignisprotokoll protokolliert: **Anwendungs- und Dienstprotokolle** > **Azure Information Protection**:

- Warnmeldungen: Informations-ID 301

- Legitimationsmeldungen: Informations-ID 302

- Blockiermeldungen: Informations-ID 303

Beispielereigniseintrag aus einer Legitimationsmeldung:

```
Client Version: 1.48.1.0
Client Policy ID: e5287fe6-f82c-447e-bf44-6fa8ff146ef4
Item Full Path: Price list.msg
Item Name: Price list
Process Name: OUTLOOK
Action: Justify
User Justification: My manager approved sharing of this content
Action Source: 
User Response: Confirmed
```


### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-specific-labels"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren für bestimme Bezeichnungen implementiert:

Um die Popupmeldungen für bestimmte Bezeichnungen implementieren zu können, benötigen Sie die Bezeichnungs-ID der entsprechenden Bezeichnungen. Der Wert der Bezeichnungs-ID wird auf dem Blatt **Bezeichnung** angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal anzeigen oder konfigurieren. Bei Dateien, auf die Bezeichnungen angewendet wurden, können Sie auch das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) ausführen, um die Bezeichnungs-ID (MainLabelId oder SubLabelId) zu identifizieren. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, geben Sie immer die ID einer untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung.

Erstellen Sie mit den folgenden Schlüsseln eine oder mehr der folgenden erweiterten Clienteinstellungen. Geben Sie als Werte ein oder mehrere Bezeichnungen mit deren IDs an, und trennen Sie die einzelnen Werte mit Kommas.

Beispielwert für mehrere Bezeichnungs-IDs als kommagetrennte Zeichenfolge: `dcf781ba-727f-4860-b3c1-73479e31912b,1ace2cc3-14bc-4142-9125-bf946a70542c,3e9df74d-3168-48af-8b11-037e3021813f`


- Warnmeldungen:
    
    - Legende: **OutlookWarnUntrustedCollaborationLabel**
    
    - Wert: \<**Label-IDs, kommagetrennt**>

- Legitimationsmeldungen:
    
    - Legende: **OutlookJustifyUntrustedCollaborationLabel**
    
    - Wert: \<**Label-IDs, kommagetrennt**>

- Blockiermeldungen:
    
    - Legende: **OutlookBlockUntrustedCollaborationLabel**
    
    - Wert: \<**Label-IDs, kommagetrennt**>


### <a name="to-implement-the-warn-justify-or-block-pop-up-messages-for-emails-or-attachments-that-dont-have-a-label"></a>So werden die Popupmeldungen zum Warnen, zur Legitimation oder zum Blockieren von E-Mails oder Anhängen implementiert, die keine Bezeichnung haben:

Erstellen Sie die folgende erweiterte Clienteinstellung mit einem der folgenden Werte:

- Warnmeldungen:
    
    - Legende: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Warnung**

- Legitimationsmeldungen:
    
    - Legende: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Justify** (Legitimation)

- Blockiermeldungen:
    
    - Legende: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Blockieren**

- Diese Meldungen deaktivieren:
    
    - Legende: **OutlookUnlabeledCollaborationAction**
    
    - Wert: **Deaktiviert**

### <a name="to-specify-the-allowed-domain-names-for-recipients-exempt-from-the-pop-up-messages"></a>Angeben der zulässigen Domänennamen für Empfänger, die von den Popupmeldungen ausgenommen sind

Wenn Sie in einer erweiterten Clienteinstellung einen Domänenname angeben, werden Benutzern keine Popupmeldungen für Empfänger angezeigt, in deren E-Mail-Adresse dieser Domänenname enthalten ist. In diesem Fall werden die E-Mails problemlos gesendet. Wenn Sie mehrere Domänen angeben möchten, fügen Sie sie kommagetrennt als einzelne Zeichenfolge hinzu.

Eine übliche Konfiguration ist es, die Popupmeldungen nur für die Empfänger anzuzeigen, die nicht zu Ihrer Organisation gehören, oder die keine für Ihre Organisation autorisierte Partner sind. In diesem Fall geben Sie alle E-Mail-Domänen an, die von Ihrer Organisation und von Ihren Partnern verwendet werden.

Erstellen Sie den folgenden Schlüssel für eine erweiterte Clienteinstellung. Geben Sie als Werte eine oder mehrere Domänen an, und trennen Sie die einzelnen Werte mit Kommas.

Beispielwert für mehrere Domänen als kommagetrennte Zeichenfolge: `contoso.com,fabrikam.com,litware.com`

- Legende: **OutlookCollaborationTrustedDomains**

- Wert: **\<** Domänenname, kommagetrennt**>**

Wenn Sie z.B. den Domänenname „contoso.com“ angeben, werden für Benutzer in Outlook keine Popupmeldungen angezeigt, wenn diese E-Mails an john@sales.contoso.com versenden.

## <a name="set-a-different-default-label-for-outlook"></a>Festlegen anderer Standardbezeichnung für Outlook

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie diese Einstellung konfigurieren, wendet Outlook für die Einstellung **Standardbezeichnung auswählen** nicht die in der Azure Information Protection-Richtlinie konfigurierte Standardbezeichnung an. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden.

Um eine andere Bezeichnung anzuwenden, müssen Sie die Bezeichnungs-ID angeben. Der Wert der Bezeichnungs-ID wird auf dem Blatt **Bezeichnung** angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal anzeigen oder konfigurieren. Bei Dateien, auf die Bezeichnungen angewendet wurden, können Sie auch das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) ausführen, um die Bezeichnungs-ID (MainLabelId oder SubLabelId) zu identifizieren. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, geben Sie immer die ID einer untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung.

Damit Outlook nicht die Standardbezeichnung anwendet, geben Sie **None** (Keine) an.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **OutlookDefaultLabel**

- Wert: \<**Bezeichnungs-ID**> oder **None** (Keine)

## <a name="configure-a-label-to-apply-smime-protection-in-outlook"></a>Konfigurieren einer Bezeichnung, um die S/MIME-Schutz in Outlook anzuwenden

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Verwenden Sie diese Einstellung nur, wenn Sie eine funktionierende [S/MIME-Bereitstellung](https://docs.microsoft.com/office365/SecurityCompliance/s-mime-for-message-signing-and-encryption) haben und eine Bezeichnung diese Schutzmethode automatisch auf E-Mails anwenden soll und nicht den Rights Management-Schutz vor Azure Information Protection. Der resultierende Schutz ist derselbe wie bei der manuellen Auswahl von S/MIME-Optionen in Outlook.

In dieser Konfiguration müssen Sie eine erweiterte Clienteinstellung namens **LabelToSMIME** für jede Azure Information Protection-Bezeichnung angeben, die S/MIME-Schutz anwenden soll. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[Azure Information Protection label ID];[S/MIME action]`

Der Wert der Bezeichnungs-ID wird auf dem Blatt **Bezeichnung** angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal anzeigen oder konfigurieren. Um S/MIME mit einer untergeordneten Bezeichnung zu verwenden, geben Sie immer die ID der untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung. Wenn Sie eine untergeordnete Bezeichnung angegeben, muss sich die übergeordnete Bezeichnung im gleichen Bereich oder in der globalen Richtlinie befinden.

Folgende S/MIME-Aktionen sind möglich:

- `Sign;Encrypt`: Zum Anwenden einer digitalen Signatur und der S/MIME-Verschlüsselung

- `Encrypt`: Nur zum Anwenden der S/MIME-Verschlüsselung

- `Sign`: Nur zum Anwenden einer digitalen Signatur

Beispielwerte für eine Bezeichnungs-ID von **dcf781ba-727f-4860-b3c1-73479e31912b**:

- Zum Anwenden einer digitalen Signatur und der S/MIME-Verschlüsselung:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign;Encrypt**

- Nur zum Anwenden der S/MIME-Verschlüsselung:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Encrypt**
    
- Nur zum Anwenden einer digitalen Signatur:
    
    **dcf781ba-727f-4860-b3c1-73479e31912b;Sign**

Aufgrund dieser Konfiguration wird bei der Anwendung der Bezeichnung für eine E-Mail-Nachricht zusätzlich zur Klassifizierung der Bezeichnung auch der S/MIME-Schutz für die E-Mail angewendet.

Wenn die von Ihnen angegebene Bezeichnung für den Rights Management-Schutz im Azure-Portal konfiguriert ist, ersetzt der S/MIME-Schutz den Rights Management-Schutz nur in Outlook. Für alle anderen Szenarien, die eine Bezeichnung unterstützen, wird der Rights Management-Schutz angewendet.

Wenn die Bezeichnung nur in Outlook sichtbar sein soll, konfigurieren Sie sie so, dass sie die einzelne benutzerdefinierte Aktion **Do Not Forward** (Nicht weiterleiten) anwendet. Eine Anleitung dazu finden Sie im folgenden Artikel: [Schnellstart: Konfigurieren einer Bezeichnung für Benutzer zum einfachen Schützen von E-Mails, die vertrauliche Informationen enthalten](../quickstart-label-dnf-protectedemail.md).

## <a name="remove-not-now-for-documents-when-you-use-mandatory-labeling"></a>„Not now“ („Nicht jetzt“) für Dokumente bei Verwendung der obligatorischen Bezeichnung entfernen

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie die [Richtlinieneinstellung](../configure-policy-settings.md) **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung haben) verwenden, werden die Benutzer beim ersten Speichern eines Offices-Dokuments und beim Senden einer E-Mail dazu aufgefordert, eine Bezeichnung zu wählen. Bei Office-Dokumenten können Benutzer **Not now** (nicht jetzt) wählen, um die Aufforderung zum Auswählen einer Bezeichnung vorübergehend zu schließen und zum Dokument zurückzukehren. Sie können das gespeicherte Dokument jedoch nicht schließen, ohne es zu bezeichnen. 

Wenn Sie diese Einstellung konfigurieren, wird die Option **Not now** (nicht jetzt) entfernt, sodass die Benutzer eine Bezeichnung wählen müssen, wenn das Dokument zum ersten Mal gespeichert wird.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **PostponeMandatoryBeforeSave**

- Wert: **False**

## <a name="turn-on-classification-to-run-continuously-in-the-background"></a>Aktivieren der dauerhaft im Hintergrund ausgeführten Klassifizierung

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Diese Einstellung befindet sich in der Vorschauversion und kann sich ändern.

Wenn Sie diese Einstellung konfigurieren, ändert sich das [Standardverhalten](../configure-policy-classification.md#how-automatic-or-recommended-labels-are-applied), wie der Azure Information Protection-Client automatische und empfohlene Bezeichnungen auf Dokumente anwendet, wie folgt: 

- Für Word, Excel und PowerPoint wird die automatische Klassifizierung für Dokumente ständig im Hintergrund ausgeführt.  

Das Verhalten für Outlook ändert sich nicht.

Wenn der Azure Information Protection-Client Dokumente im Hintergrund periodisch auf die von Ihnen festgelegten Bedingungsregeln überprüft, aktiviert dieses Verhalten die automatische und empfohlene Klassifizierung und den Schutz für Dokumente, die in SharePoint Online gespeichert sind. Große Dateien werden schneller gespeichert, da die Bedingungsregeln bereits ausgeführt wurden. 

Diese Bedingungsregeln werden nicht in Echtzeit, während der Benutzer tippt, ausgeführt. Stattdessen werden sie regelmäßig als Hintergrundaufgabe ausgeführt, wenn das Dokument geändert wird.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Legende: **RunPolicyInBackground**

- Wert: **True**

## <a name="dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption"></a>Schützen Sie keine PDF-Dateien mithilfe des ISO-Standards für die PDF-Verschlüsselung

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn die aktuelle Version des Azure Information Protection-Clients eine PDF-Datei schützt, verbleibt die daraus resultierende Erweiterung bei PDF und entspricht somit dem ISO-Standard für die Verschlüsselung von PDF-Dateien. Weitere Informationen zu diesem Standard finden Sie im Abschnitt **7.6 Encryption** (7.6 Verschlüsselung) aus dem [Dokument, das von ISO 32000-1 abgeleitet](https://www.adobe.com/content/dam/acom/en/devnet/pdf/pdfs/PDF32000_2008.pdf) und von Adobe Systems Incorporated veröffentlicht wird.

Wenn Sie möchten, dass der Client zu dem Verhalten in älteren Versionen des Clients zurückkehrt, bei dem PDF-Dateien mit der .ppdf-Dateinamenerweiterung geschützt werden, verwenden Sie die folgende erweiterte Einstellung, indem Sie diese Zeichenfolge eingeben:

- Legende: **EnablePDFv2Protection**

- Wert: **False**

Sie könnten diese Einstellung zum Beispiel für alle Benutzer benötigen, wenn Sie einen PDF-Reader verwenden, der den ISO-Standard für die PDF-Verschlüsselung nicht unterstützt. Oder Sie müssen sie möglicherweise für einige Benutzer konfigurieren, wenn Sie nach und nach zu einem PDF-Reader wechseln, der das neue Format unterstützt. Ein weiterer möglicher Grund für die Verwendung dieser Einstellung besteht, wenn Sie signierten PDF-Dokumenten Schutz hinzufügen müssen. Signierte PDF-Dokumente können zusätzlich mit dem PPDF-Format geschützt werden, da dieser Schutz als Wrapper für die Datei implementiert wird. 

Damit die Azure Information Protection-Überprüfung die neue Einstellung verwenden, muss der Überprüfungsdienst neu gestartet werden. Darüber hinaus schützt die Überprüfung nicht mehr standardmäßig PDF-Dokumente. Wenn Sie möchten, dass PDF-Dokumente durch die Überprüfung geschützt werden sollen, wenn EnablePDFv2Protection auf „False“ festgelegt ist, müssen Sie die [Registrierung bearbeiten](../deploy-aip-scanner.md#editing-the-registry-for-the-scanner).

Weitere Informationen zu dieser neuen PDF-Verschlüsselung finden Sie im Blogbeitrag [Neue Unterstützung für die PDF-Verschlüsselung mit Microsoft Information Protection](https://techcommunity.microsoft.com/t5/Azure-Information-Protection/New-support-for-PDF-encryption-with-Microsoft-Information/ba-p/262757).

Eine Liste von PDF-Readern, die den ISO-Standard für PDF-Verschlüsselung unterstützen, und Reader, die ältere Formate unterstützen, finden Sie unter [Unterstützte Reader für PDF-Dokumente für Microsoft Azure Information Protection](protected-pdf-readers.md).

### <a name="to-convert-existing-ppdf-files-to-protected-pdf-files"></a>Konvertieren vorhandener PPDF-Dateien in geschützte PDF-Dateien

Wenn der Azure Information Protection-Client die Clientrichtlinie mit der neuen Einstellung heruntergeladen hat, können Sie mit PowerShell-Befehlen vorhandene PPDF-Dateien in geschützte PDF-Dateien konvertieren, die den ISO-Standard für die PDF-Verschlüsselung verwenden. 

Wenn Sie die folgenden Anweisungen für Dateien verwenden möchten, die Sie nicht selbst geschützt haben, benötigen Sie [Rights Management-Nutzungsrechte](../configure-usage-rights.md) zum Entfernen des Schutzes aus Dateien oder Administratorrechte. Informationen zum Aktivieren der Administratorfunktion und zum Konfigurieren Ihres Kontos als Administrator finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder die Datenwiederherstellung](../configure-super-users.md).

Außerdem werden Sie zum [RMS-Aussteller](../configure-usage-rights.md#rights-management-issuer-and-rights-management-owner), wenn Sie diese Anweisungen für Dateien verwenden, die Sie nicht selbst geschützt haben. In diesem Szenario kann der Benutzer, der das Dokument ursprünglich geschützt hat, es nicht mehr nachverfolgen und den Zugriff darauf nicht mehr widerrufen. Wenn Benutzer ihre geschützten PDF-Dokumente nachverfolgen und den Zugriff darauf widerrufen möchten, müssen sie die Bezeichnung manuell entfernen und mit dem Datei-Explorer per Rechtsklick erneut anwenden.

So verwenden Sie PowerShell-Befehle zum Konvertieren vorhandener PPDF-Dateien in geschützte PDF-Dateien, die den ISO-Standard für die PDF-Verschlüsselung verwenden:

1. Verwenden Sie den Befehl [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) für die PPDF-Datei. Beispiel:
    
        Get-AIPFileStatus -Path \\Finance\Projectx\sales.ppdf

2. Beachten Sie bei der Ausgabe die folgenden Parameterwerte:
    
   - Den Wert (GUID) für **SubLabelId** (falls vorhanden). Wenn dieser Wert leer ist, wurde keine untergeordnete Bezeichnung verwendet. Verwenden Sie in diesem Fall stattdessen den Wert für **MainLabelId**.
    
     Hinweis: Wenn es auch keinen Wert für **MainLabelId** gibt, erhält die Datei keine Bezeichnung. In diesem Fall können Sie die Befehle [Unprotect-RMSFile](/powershell/module/azureinformationprotection/unprotect-rmsfile) und [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) anstelle der Befehle in Schritt 3 und 4 verwenden.
    
   - Den Wert für **RMSTemplateId**. Wenn dieser Wert **Eingeschränkter Zugriff** lautet, hat ein Benutzer die Datei mit benutzerdefinierten Berechtigungen und nicht mit Schutzeinstellungen, die für die Bezeichnung konfiguriert wurden, geschützt. Wenn Sie fortfahren, werden diese benutzerdefinierten Berechtigungen durch die Schutzeinstellungen der Bezeichnung überschrieben. Fahren Sie fort, oder bitten Sie den Benutzer (angezeigter Wert für **RMSIssuer**), die Bezeichnung zu entfernen und mit den ursprünglichen benutzerdefinierten Berechtigungen erneut anzuwenden.

3. Entfernen Sie die Bezeichnung mithilfe von [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) mit dem Parameter *RemoveLabel*. Wenn Sie die [Richtlinieneinstellung](../configure-policy-settings.md) für **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung festlegen, eine Bezeichnung oder den Schutz entfernen möchten** verwenden, müssen Sie für den Parameter *Begründung* den Grund angeben. Beispiel: 
    
        Set-AIPFileLabel \\Finance\Projectx\sales.ppdf -RemoveLabel -JustificationMessage 'Removing .ppdf protection to replace with .pdf ISO standard'

4. Übernehmen Sie erneut die ursprüngliche Bezeichnung, indem Sie den Wert für die Bezeichnung angeben, den Sie in Schritt 1 identifiziert haben. Beispiel:
    
        Set-AIPFileLabel \\Finance\Projectx\sales.pdf -LabelId d9f23ae3-1234-1234-1234-f515f824c57b

Die Datei behält die PDF-Erweiterung, wird jedoch wie zuvor klassifiziert und mit dem ISO-Standard für die PDF-Verschlüsselung geschützt.

## <a name="support-for-files-protected-by-secure-islands"></a>Unterstützung von durch Secure Islands geschützten Dateien

Diese Konfigurationsoption ist zurzeit als Vorschau verfügbar und unterliegt Änderungen.

Wenn Sie Secure Islands zum Schützen von Dokumenten verwendet haben, verfügen Sie aufgrund dieses Schutzes möglicherweise über geschützte Text- und Bilddateien sowie generisch geschützte Dateien. Zum Beispiel Dateien mit den Erweiterungen PTXT, PJPEG oder PFILE. Wenn Sie die Registrierung wie folgt bearbeiten, können diese Dateien von Azure Information Protection entschlüsselt werden:


Fügen Sie den DWORD-Wert **EnableIQPFormats** in den folgenden Registrierungspfad ein, und legen Sie den Wert „data“ (Daten) auf **1** fest:

- Für eine 64-Bit-Version von Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\WOW6432Node\\Microsoft\\MSIP

- Für eine 32-Bit-Version von Windows: HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\MSIP

Aufgrund dieser Änderung in der Registrierung werden die folgenden Szenarios unterstützt:

- Der Azure Information Protection-Viewer kann diese geschützten Dateien öffnen.

- Die Azure Information Protection-Überprüfung kann diese Dateien auf vertrauliche Informationen prüfen.

- Datei-Explorer, PowerShell und die Azure Information Protection-Überprüfung können diese Dateien bezeichnen. Dementsprechend können Sie eine Azure Information Protection-Bezeichnung anwenden, die neuen Schutz von Azure Information Protection anwendet oder vorhandenen Schutz von Secure Islands entfernt.

- Mit der [Clientanpassung für die Bezeichnungsmigration](#migrate-labels-from-secure-islands-and-other-labeling-solutions) können Sie die Secure Islands-Bezeichnung dieser geschützten Dateien automatisch in eine Azure Information Protection-Bezeichnung konvertieren.

## <a name="migrate-labels-from-secure-islands-and-other-labeling-solutions"></a>Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen migrieren

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Diese Konfiguration ist derzeit nicht mit dem neuen Standardverhalten kompatibel, das PDF-Dateien mithilfe des ISO-Standards für die PDF-Verschlüsselung schützt. In diesem Szenario können PPDF-Dateien nicht mit Datei-Explorer, PowerShell oder der Überprüfung geöffnet werden. Um dieses Problem zu beheben, verwenden Sie die erweiterte Clienteinstellung, mit der [der ISO-Standard nicht für die PDF-Verschlüsselung verwendet wird](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption).

Sie können Office- und PDF-Dokumente, die eine Bezeichnung von Secure Islands erhalten haben, mit einer neuen Azure Information Protection-Bezeichnung versehen, indem Sie eine von Ihnen definierte Zuordnung verwenden. Mit dieser Methode können Sie auch Bezeichnungen aus anderen Lösungen wiederverwenden, wenn diese Bezeichnungen sich in Office-Dokumenten befinden. 

> [!NOTE]
> Wenn Sie über andere von Secure Islands geschützte Dateien verfügen, die keine PDF- und Office-Dokumente sind, können Sie diesen eine neue Bezeichnung geben, nachdem Sie die Registrierung wie im [vorherigen Abschnitt](#support-for-files-protected-by-secure-islands) beschrieben bearbeitet haben. 

Diese Konfigurationsoption führt dazu, dass die neue Azure Information Protection-Bezeichnung folgendermaßen vom Azure Information Protection-Client angewendet wird:

- Bei Office-Dokumenten: Wenn das Dokument in der Desktop-App geöffnet wird, wird die neue Azure Information Protection-Bezeichnung als festgelegt angezeigt und beim Speichern des Dokuments angewendet.

- Im Datei-Explorer: Die neue Azure Information Protection-Bezeichnung wird im Azure Information Protection-Dialogfeld als festgelegt angezeigt und dann angewendet, wenn der Benutzer **Anwenden** auswählt. Wenn der Benutzer **Abbrechen** auswählt, wird die neue Bezeichnung nicht angewendet.

- In PowerShell: [Set-AIPFileLabel](/powershell/module/azureinformationprotection/set-aipfilelabel) wendet die neue Azure Information Protection-Bezeichnung an. [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) zeigt die neue Azure Information Protection-Bezeichnung erst dann an, wenn sie von einer anderen Methode festgelegt wird.

- Für die Azure Information Protection-Überprüfung: Die Ermittlung meldet das Festlegen der neuen Azure Information Protection-Bezeichnung, und diese Bezeichnung kann mit dem Erzwingungsmodus angewendet werden.

In dieser Konfiguration müssen Sie eine erweiterte Clienteinstellung namens **LabelbyCustomProperty** für jede Azure Information Protection-Bezeichnung angeben, die Sie der alten Bezeichnung zuordnen möchten. Geben Sie dann für jeden Eintrag mithilfe der folgenden Syntax den Wert an:

`[Azure Information Protection label ID],[migration rule name],[Secure Islands custom property name],[Secure Islands metadata Regex value]`

Der Wert der Bezeichnungs-ID wird auf dem Blatt **Bezeichnung** angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal anzeigen oder konfigurieren. Damit eine untergeordnete Bezeichnung angegeben werden kann, muss sich die übergeordnete Bezeichnung im gleichen Bereich oder in der globalen Richtlinie befinden.

Geben Sie einen Namen für die Migrationsregel an. Verwenden Sie einen aussagekräftigen Namen, der angibt, wie Bezeichnungen aus Ihrer vorherigen Bezeichnungslösung zu einer Azure Information Protection-Bezeichnung zugeordnet werden sollen. Der Name wird in den Scannerberichten und in der Ereignisanzeige angezeigt. Beachten Sie, dass durch diese Einstellung keine ursprüngliche Bezeichnung aus dem Dokument bzw. keine optische Kennzeichnung im Dokument entfernt wird, die von der ursprünglichen Bezeichnung möglicherweise angewendet wurde. Weitere Informationen zum Entfernen von Kopf- und Fußzeilen finden Sie im nächsten Abschnitt unter [Remove headers and footers from other labeling solutions (Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen)](#remove-headers-and-footers-from-other-labeling-solutions).

### <a name="example-1-one-to-one-mapping-of-the-same-label-name"></a>Beispiel 1: 1:1-Zuordnung des gleichen Bezeichnungsnamens

Anforderung: Dokumente mit der Secure Islands-Bezeichnung „Confidential“ sollten in Azure Information Protection die Bezeichnung „Vertraulich“ erhalten.

In diesem Beispiel:

- Die Azure Information Protection-Bezeichnung, die Sie verwenden werden, lautet **Vertraulich**. Sie hat die Bezeichnungs-ID **1ace2cc3-14bc-4142-9125-bf946a70542c**. 

- Die Secure Islands-Bezeichnung lautet **Vertraulich** und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

    
|Name|Wert|
|---------------------|---------|
|LabelbyCustomProperty|1ace2cc3-14bc-4142-9125-bf946a70542c,"Secure Islands label is Confidential",Classification,Confidential|

### <a name="example-2-one-to-one-mapping-for-a-different-label-name"></a>Beispiel 2: 1:1-Zuordnung für einen anderen Bezeichnungsnamen

Anforderung: Dokumente mit der Secure Islands-Bezeichnung „Sensitive“ sollten in Azure Information Protection die Bezeichnung „Streng vertraulich“ erhalten.

In diesem Beispiel:

- Die Azure Information Protection-Bezeichnung, die Sie verwenden werden, lautet **Streng vertraulich** und hat die Bezeichnungs-ID **3e9df74d-3168-48af-8b11-037e3021813f**.

- Die Secure Islands-Bezeichnung lautet **Sensitive** (Sensibel) und ist in der benutzerdefinierten Eigenschaft **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

    
|Name|Wert|
|---------------------|---------|
|LabelbyCustomProperty|3e9df74d-3168-48af-8b11-037e3021813f,"Secure Islands label is Sensitive",Classification,Sensitive|


### <a name="example-3-many-to-one-mapping-of-label-names"></a>Beispiel 3: n:1-Zuordnung von Bezeichnungsnamen

Anforderung: Sie verfügen über zwei Secure Islands-Bezeichnungen, die das Wort „Internal“ enthalten, und Sie möchten Dokumente, die eine dieser beiden Secure Islands-Bezeichnungen enthalten, in Azure Information Protection als „Allgemein“ bezeichnen.

In diesem Beispiel:

- Die Azure Information Protection-Bezeichnung, die Sie verwenden werden, lautet **Allgemein** und hat die Bezeichnungs-ID **2beb8fe7-8293-444c-9768-7fdc6f75014d**.

- Die Secure Islands-Bezeichnungen enthalten den Begriff **Internal** (intern) und sind in der benutzerdefinierten Eigenschaft namens **Classification** (Klassifizierung) gespeichert.

Erweiterte Clienteinstellung:

    
|Name|Wert|
|---------------------|---------|
|LabelbyCustomProperty|2beb8fe7-8293-444c-9768-7fdc6f75014d,"Secure Islands label contains Internal",Classification,.\*Internal.\*|


## <a name="remove-headers-and-footers-from-other-labeling-solutions"></a>Entfernen von Kopf- und Fußzeilen aus anderen Bezeichnungslösungen

Diese Konfiguration verwendet mehrere [erweiterte Clienteinstellungen](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Diese Einstellungen befinden sich in der Vorschauversion und können sich ändern.

Mit diesen Einstellungen können Sie textbasierte Kopf- und Fußzeilen in Dokumenten entfernen oder ersetzen, wenn diese optischen Kennzeichnungen von einer anderen Bezeichnungslösung angewendet wurden. Die ältere Fußzeile enthält beispielsweise den Namen einer alten Bezeichnung, die Sie nun mit einem neuen Bezeichnungsnamen und einer eigenen Fußzeile zu Azure Information Protection migriert haben.

Wenn der Client diese Konfiguration in seiner Richtlinie abruft, werden die alten Kopf- oder Fußzeilen entfernt oder ersetzt, wenn das Dokument in der Office-App geöffnet wird und Azure Information Protection-Bezeichnungen auf das Dokument angewendet wurden.

Diese Konfiguration wird für Outlook nicht unterstützt. Beachten Sie außerdem, dass die Verwendung mit Word, Excel und PowerPoint sich negativ auf die Leistung dieser Apps für Benutzer auswirken kann. Mithilfe der Konfiguration können Sie Einstellungen für jede einzelne Anwendung definieren, z.B. die Suche nach Text in Kopf- oder Fußzeilen von Word-Dokumenten, jedoch nicht von Excel-Tabellen oder PowerPoint-Präsentationen.

Da der Musterabgleich sich auf die Leistung für Benutzer auswirkt, wird empfohlen, Office-Anwendungstypen (**W**ord, **E**xcel, **P**owerPoint) auf diejenigen einzuschränken, die durchsucht werden müssen:

- Legende: **RemoveExternalContentMarkingInApp**

- Wert: \<**Office-Anwendungstypen WXP**> 

Beispiele:

- Geben Sie **W** an, um nur Word-Dokumente zu durchsuchen.

- Geben Sie **WP** an, um Word-Dokumente und PowerPoint-Präsentationen zu durchsuchen.

Sie benötigen dann mindestens eine weitere erweiterte Clienteinstellung, **ExternalContentMarkingToRemove**, um die Inhalte der Kopf- oder Fußzeile anzugeben und diese zu entfernen oder zu ersetzen.

### <a name="how-to-configure-externalcontentmarkingtoremove"></a>Konfigurieren von ExternalContentMarkingToRemove

Wenn Sie den Zeichenfolgenwert für den Schlüssel **ExternalContentMarkingToRemove** angeben, stehen drei Optionen zur Verfügung, die reguläre Ausdrücke verwenden:

- Partielle Übereinstimmung, um alles aus der Kopf- oder Fußzeile zu entfernen.
    
    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten diese Kopf- oder Fußzeilen vollständig entfernen. Geben Sie den Wert `*TEXT*` an.

- Vollständige Übereinstimmung, um nur bestimmte Wörter aus der Kopf- oder Fußzeile zu entfernen.
    
    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten nur das Wort **TEXT** entfernen, wodurch die Zeichenfolge der Kopf- oder Fußzeile **TO REMOVE** entspricht. Geben Sie den Wert `TEXT ` an.

- Vollständige Übereinstimmung, um alles aus der Kopf- oder Fußzeile zu entfernen.
    
    Beispiel: Kopf- oder Fußzeilen enthalten die Zeichenfolge **TEXT TO REMOVE**. Sie möchten die Kopf- oder Fußzeilen entfernen, die genau diese Zeichenfolge enthalten. Geben Sie den Wert `^TEXT TO REMOVE$` an.
    

Der Musterabgleich für die angegebene Zeichenfolge berücksichtigt keine Groß- und Kleinschreibung. Die maximale Zeichenfolgenlänge beträgt 255 Zeichen.

Da einige Dokumente unsichtbare Zeichen oder andere Arten von Leerzeichen oder Tabstopps enthalten können, wird die Zeichenfolge, die Sie für einen Begriff oder einen Satz angeben, möglicherweise nicht erkannt. Geben Sie nach Möglichkeit immer ein einzelnes unterscheidendes Wort für den Wert an, und testen Sie die Ergebnisse, bevor Sie diese für die Produktion bereitstellen.

- Legende: **ExternalContentMarkingToRemove**

- Value: \<**zu vergleichende Zeichenfolge; als regulärer Ausdruck definiert**> 

#### <a name="multiline-headers-or-footers"></a>Mehrzeilige Kopf- oder Fußzeilen

Wenn der Text in einer Kopf- oder Fußzeile mehr als eine Zeile umfasst, erstellen Sie einen Schlüssel und einen Wert für jede Zeile. Angenommen, folgende Fußzeile mit zwei Zeilen ist vorhanden:

**The file is classified as Confidential**

**Label applied manually**

Erstellen Sie folgende Einträge, um diese mehrzeilige Fußzeile zu entfernen:

- Schlüssel 1: **ExternalContentMarkingToRemove**

- Schlüsselwert 1: **\*Vertraulich***

- Schlüssel 2: **ExternalContentMarkingToRemove**

- Schlüsselwert 2: **\*Label applied*** (Bezeichnung angewendet) 

#### <a name="optimization-for-powerpoint"></a>Optimierung für PowerPoint

In PowerPoint werden Fußzeilen als Formen implementiert. Wenn Sie vermeiden möchten, dass Formen entfernt werden, die den angegeben Text enthalten, jedoch keine Kopf- oder Fußzeilen sind, verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **PowerPointShapeNameToRemove**. Es wird empfohlen, diese Einstellung ebenfalls zu verwenden, um zu verhindern, dass der Text in allen Formen überprüft wird, denn dieser Prozess ist sehr ressourcenintensiv.

Wenn Sie diese zusätzliche erweiterte Clienteinstellung nicht angeben und PowerPoint im Schlüsselwert **RemoveExternalContentMarkingInApp** eingeschlossen ist, werden alle Formen auf den Text überprüft, den Sie im Wert **ExternalContentMarkingToRemove** angeben. 

So finden Sie den Namen der Form, die Sie als Kopf- oder Fußzeile verwenden:

1. Zeigen Sie in PowerPoint den Bereich **Auswahl** an: Registerkarte **Format** > **Arrange** group (Gruppe anordnen) > **Auswahlbereich**.

2. Wählen Sie die Form auf der Folie aus, die die Kopf- oder Fußzeile enthält. Der Name der ausgewählten Form wird nun im Bereich **Auswahl** hervorgehoben.

Verwenden Sie den Namen der Form, um einen Zeichenfolgenwert für den Schlüssel **PowerPointShapeNameToRemove** anzugeben. 

Beispiel: Der Name der Form ist **fc**. Geben Sie den Wert `fc` an, um die Form mit diesem Namen zu entfernen.

- Legende: **PowerPointShapeNameToRemove**

- Wert: \<**Name der PowerPoint-Form**> 

Wenn mehr als eine PowerPoint-Form entfernt werden soll, erstellen Sie so viele **PowerPointShapeNameToRemove**-Schlüssel wie Sie Formen entfernen möchten. Geben Sie für jeden Eintrag den Namen der zu entfernenden Form an.

Standardmäßig werden nur die Masterfolien auf Kopf- oder Fußzeilen überprüft. Wenn Sie diese Suche auf alle Folien ausweiten möchten (dieser Prozess ist jedoch wesentlich ressourcenintensiver), verwenden Sie eine zusätzliche erweiterte Clienteinstellung namens **RemoveExternalContentMarkingInAllSlides**:

- Legende: **RemoveExternalContentMarkingInAllSlides**

- Wert: **True**

## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Hinzufügen einer Bezeichnung zu einem Office-Dokument über eine bereits bestehende benutzerdefinierte Eigenschaft

> [!NOTE]
> Wenn Sie diese Konfiguration und die Konfiguration zum [Migrieren von Bezeichnungen von Secure Islands und anderen Bezeichnungslösungen](#migrate-labels-from-secure-islands-and-other-labeling-solutions) verwenden, erhält die Einstellung für die Bezeichnungsmigration Vorrang. 

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie diese Einstellung konfigurieren, können Sie ein Office-Dokument klassifizieren (und unter Umständen schützen), wenn es über eine benutzerdefinierte Eigenschaft mit einem Wert verfügt, der einem Ihrer Bezeichnungsnamen entspricht. Diese benutzerdefinierte Eigenschaft kann aus einer Klassifizierungslösung stammen oder von SharePoint als eine Eigenschaft festgelegt worden sein.

Diese Konfiguration hat zur Folge, dass einem Dokument, das ohne eine Azure Information Protection-Bezeichnung von einem Benutzer in einer Office-App geöffnet oder gespeichert wird, eine Bezeichnung zugeordnet wird, die mit dem entsprechenden Eigenschaftswert übereinstimmt. 

Bevor Sie diese Konfiguration verwenden können, müssen Sie zunächst zwei erweiterte Einstellungen angeben, die miteinander interagieren. Die erste Einstellung wird **SyncPropertyName** genannt. Es handelt sich dabei um den benutzerdefinierten Eigenschaftsnamen, der von der anderen Klassifizierungslösung festgelegt worden ist, oder um eine Eigenschaft, die von SharePoint festgelegt wurde. Bei der zweiten Einstellung handelt es sich um **SyncPropertyState**. Diese muss auf „OneWay“ festgelegt sein.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel 1: **SyncPropertyName**

- Wert von Schlüssel 1: \<**Eigenschaftenname**> 

- Schlüssel 2: **SyncPropertyState**

- Schlüsselwert 2: **OneWay**

Verwenden Sie diesen Schlüssel und die entsprechenden Werte für lediglich eine benutzerdefinierte Eigenschaft.

Es gibt zum Beispiel eine SharePoint-Spalte mit dem Namen **Klassifizierung** und den möglichen Werten **Öffentlich**, **Allgemein** und **Streng vertraulich\Alle Mitarbeiter**. Dokumente werden in SharePoint gespeichert, wobei deren Werte für die Klassifizierungseigenschaft auf **Öffentlich**, **Allgemein** oder **Streng vertraulich\Alle Mitarbeiter** festgelegt sind.

Um einem Office-Dokument eine Bezeichnung dieser Klassifizierungswerte zuzuweisen, legen Sie **SyncPropertyName** auf **Classification** und **SyncPropertyState** auf **OneWay** fest. 

Wenn ein Benutzer nun eines dieser Office-Dokumente öffnet und speichert, wird diesem eine der folgenden Bezeichnungen zugeordnet: **Öffentlich**, **Allgemein** oder **Streng vertraulich\Alle Mitarbeiter**. Dies geschieht allerdings nur, wenn Bezeichnungen mit diesen Namen in der Azure Information Protection-Richtlinie vorhanden sind. Wenn es keine Bezeichnungen mit diesen Namen gibt, erhält das Dokument keine Bezeichnung.

## <a name="limit-the-number-of-threads-used-by-the-scanner"></a>Begrenzen der Anzahl der von der Überprüfung verwendeten Threads

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Standardmäßig verwendet die Überprüfung alle verfügbaren Prozessorressourcen des Computers, auf dem der Überprüfungsdienst ausgeführt wird. Wenn Sie die CPU-Nutzung während der Überprüfungsvorgänge des Diensts begrenzen müssen, erstellen Sie die folgende erweiterte Einstellung. 

Geben Sie als Wert die Anzahl von gleichzeitigen Threads an, die von der Überprüfung parallel ausgeführt werden dürfen. Die Überprüfung verwendet für jede Datei, die überprüft wird, einen separaten Thread, daher definiert diese Drosselungskonfiguration auch die Anzahl von Dateien, die parallel überprüft werden können. 

Wenn Sie den Wert zu Testzwecken zum ersten Mal konfigurieren, empfehlen wir Ihnen, „2 pro Kern“ anzugeben und die Ergebnisse zu überwachen. Wenn Sie die Überprüfung z.B. auf einem Computer mit vier Kernen ausführen, legen Sie den Wert auf „8“ fest. Erhöhen oder verringern Sie den Wert nach Bedarf – je nachdem, welche Leistung Sie für den Überprüfungscomputer und die Überprüfungshäufigkeit benötigen. 

- Legende: **ScannerConcurrencyLevel**

- Wert: **\<Anzahl von gleichzeitigen Threads>**

## <a name="disable-the-low-integrity-level-for-the-scanner"></a>Deaktivieren der niedrigen Integritätsebene für den Scanner

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Die Vorschauversion der Azure Information Protection-Überprüfung wird standardmäßig mit einer niedrigen Integritätsebene ausgeführt. Diese Einstellung bietet eine höhere Sicherheitsisolationsstufe, beeinträchtigt jedoch die Leistung. Eine niedrige Integritätsebene eignet sich, wenn Sie den Scanner mit einem Konto ausführen, das privilegierte Zugriffsrechte hat (z.B. ein lokales Administratorkonto), da diese Einstellung den Computer schützt, der den Scanner ausführt.

Wenn das Dienstkonto, das den Scanner ausführt, nur über die unter [Voraussetzungen für die Azure Information Protection-Überprüfung](../deploy-aip-scanner.md#prerequisites-for-the-azure-information-protection-scanner) dokumentierten Rechte verfügt, ist eine niedrige Integritätsebene weder erforderlich noch empfehlenswert, da sie sich negativ auf die Leistung auswirkt. 

Weitere Informationen zu den Windows-Integritätsebenen finden Sie unter [What is the Windows Integrity Mechanism? (Was ist der Windows-Integritätsmechanismus?)](https://msdn.microsoft.com/library/bb625957.aspx).

Wenn Sie diese erweiterte Einstellung so konfigurieren möchten, dass der Scanner mit einer automatisch von Windows zugewiesenen Integritätsebene ausgeführt wird (ein Standardbenutzerkonto wird mit einer mittleren Integritätsebene ausgeführt), geben Sie die folgenden Zeichenfolgen ein:

- Legende: **ProcessUsingLowIntegrity**

- Wert: **False**


## <a name="change-the-local-logging-level"></a>Ändern des lokalen Protokolliergrads

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Der Azure Information Protection-Client schreibt Clientprotokolldateien standardmäßig in den Ordner **%localappdata%\Microsoft\MSIP**. Diese Dateien dienen zur Problembehandlung durch den Microsoft-Support.
 
Zum Ändern des Protokolliergrads für diese Dateien konfigurieren Sie die folgende erweiterte Clienteinstellung:

- Legende: **LogLevel**

- Wert: **\<Protokolliergrad>**

Legen Sie den Protokolliergrad auf einen der folgenden Werte fest:

- **Off**: Keine lokale Protokollierung.

- **Fehler**: Nur Fehler.

- **Info**: Minimale Protokollierung, bei der keine Ereignis-IDs einbezogen werden (die Standardeinstellung für den Scanner).

- **Debug**: Vollständige Informationen.

- **Trace**: Ausführliche Protokollierung (die Standardeinstellung für Clients). Für den Scanner bringt diese Einstellung eine erhebliche Beeinträchtigung der Leistung mit sich und sollte für den Scanner nur aktiviert werden, wenn der Microsoft Support dazu auffordert. Wenn Sie angewiesen werden, diesen Protokolliergrad für den Scanner festzulegen, denken Sie nach dem Sammeln der relevanten Protokolle daran, einen anderen Wert festzulegen.

Durch diese erweiterte Clienteinstellung ändern sich weder die Informationen, die für die [zentrale Berichterstellung](../reports-aip.md) an Azure Information Protection gesendet werden, noch die Informationen, die in das lokale [Ereignisprotokoll](client-admin-guide-files-and-logging.md#usage-logging-for-the-azure-information-protection-client) geschrieben werden.

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integration in die Exchange-Nachrichtenklassifizierung für eine Lösung zur Bezeichnung mobiler Geräte

Obwohl Outlook im Web noch keine systemeigene Unterstützung für die Klassifizierung und den Schutz durch Azure Information Protection bietet, können Sie Ihre Azure Information Protection-Bezeichnungen mithilfe der Exchange-Nachrichtenklassifizierung auf Ihre mobilen Benutzer erweitern, sofern sie Outlook im Web verwenden. Outlook Mobile unterstützt keine Exchange-Nachrichtenklassifizierung.

So erreichen Sie diese Lösung 

1. Verwenden Sie das Exchange PowerShell-Cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400), um Nachrichtenklassifizierungen mit der Name-Eigenschaft zu erstellen, die Ihren Bezeichnungsnamen in der Azure Information Protection-Richtlinie zugeordnet wird. 

2. Erstellen Sie für jede Bezeichnung eine Exchange-E-Mail-Flussregel: Wenden Sie die Regel an, wenn Nachrichteneigenschaften die von Ihnen konfigurierte Klassifizierung enthalten, und ändern Sie dann die Nachrichteneigenschaften, um einen Nachrichtenheader festzulegen. 

     Für den Nachrichtenheader finden Sie die anzugebenden Informationen, indem Sie die Internetheader einer E-Mail untersuchen, die Sie mithilfe Ihrer Azure Information Protection-Bezeichnung gesendet und klassifiziert haben. Suchen Sie nach den Header **msip_labels** und die darauf folgende Zeichenfolge, bis zu und einschließlich dem Semikolon. Beispiel:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Geben Sie dann für den Nachrichtenheader in der Regel **msip_labels** für den Header und den Rest der Zeichenfolge für den Headerwert an. Beispiel:
    
    ![Beispielregel für den E-Mail-Verkehr von Exchange Online, die den Nachrichtenheader für eine bestimmte Azure Information Protection-Bezeichnung festlegt](../media/exchange-rule-for-message-header.png)
    
    Hinweis: Wenn die Bezeichnung eine untergeordnete Bezeichnung ist, müssen Sie im Headerwert vor der untergeordneten Bezeichnung auch die übergeordnete Bezeichnung im gleichen Format angeben. Wenn Ihre untergeordnete Bezeichnung z. B. die GUID 27efdf94-80a0-4d02-b88c-b615c12d69a9 aufweist, kann Ihr Wert wie folgt aussehen: `MSIP_Label_ab70158b-bdcc-42a3-8493-2a80736e9cbd_Enabled=True;MSIP_Label_27efdf94-80a0-4d02-b88c-b615c12d69a9_Enabled=True;`

Bevor Sie diese Konfiguration testen, beachten Sie, dass es häufig zu einer Verzögerung beim Erstellen oder Bearbeiten von Regeln für den E-Mail-Verkehr kommt (warten Sie eine Stunde). Bei aktivierter Regel treten nun die folgenden Ereignisse ein, wenn Benutzer Outlook im Web verwenden: 

- Benutzer wählen die Exchange-Nachrichtenklassifizierung aus, und senden die E-Mail.

- Die Exchange-Regel erkennt die Exchange-Klassifizierung und ändert entsprechend den Nachrichtenheader, um die Azure Information Protection-Klassifizierung hinzuzufügen.

- Wenn interne Empfänger die E-Mail in Outlook anzeigen und der Azure Information Protection-Client installiert ist, sehen sie, dass die Azure Information Protection-Bezeichnung zugewiesen ist. 

Wenn Ihre Azure Information Protection-Bezeichnungen Schutz anwenden, fügen Sie diesen Schutz zur Regelkonfiguration hinzu: Wählen Sie die Option zum Ändern der Nachrichtensicherheit aus, wenden Sie den Rechteschutz an, und wählen Sie dann die Schutzvorlage oder die Option „Nicht weiterleiten“ aus.

Sie können Regeln für den E-Mail-Verkehr auch so konfigurieren, dass sie die umgekehrte Zuordnung vornehmen. Wenn eine Azure Information Protection-Bezeichnung erkannt wird, legen Sie eine entsprechende Exchange-Nachrichtenklassifizierung fest:

- Für jede Azure Information Protection-Bezeichnung: Erstellen Sie eine E-Mail-Flussregel, die angewendet wird, wenn der Header **msip_labels** den Namen Ihrer Bezeichnung enthält (z. B. **Allgemein**). Wenden Sie zudem eine Nachrichtenklassifizierung an, die dieser Bezeichnung zugeordnet wird.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection-Client angepasst haben, lesen Sie die folgenden Artikel, die Sie eventuell zur Unterstützung dieses Clients benötigen:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


