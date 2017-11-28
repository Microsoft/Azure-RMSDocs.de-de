---
title: "Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client"
description: "Informationen zum Anpassen des Azure Information Protection-Clients für Windows"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/20/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 0bd05c0553cdcab792c674c6945d7dfea5f02eaf
ms.sourcegitcommit: f1d0b899e6d79ebef3829f24711f947316bca8ef
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/20/2017
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-client"></a>Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie bei der Verwaltung des Azure Information Protection-Clients möglicherweise für spezifische Szenarien oder eine Teilmenge der Benutzer benötigen.

Einige dieser Einstellungen erfordern die Bearbeitung der Registrierung. Andere sind erweiterte Einstellungen, die Sie im Azure-Portal konfigurieren und anschließend für das Herunterladen durch Clients veröffentlichen müssen.  

### <a name="how-to-configure-advanced-client-configuration-settings-in-the-portal"></a>Konfigurieren erweiterter Clientkonfigurationseinstellungen im Portal

1. Sofern nicht bereits geschehen, melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an, und navigieren Sie zum Blatt **Azure Information Protection**.

2. Wählen Sie auf dem ersten Azure Information Protection-Blatt **Bereichsbezogene Richtlinien** aus.

3. Rufen Sie auf dem Blatt **Azure Information Protection – Bereichsbezogene Richtlinien** das Kontextmenü (**...** ) neben der Richtlinie mit den erweiterten Einstellungen auf. Wählen Sie dann **Erweiterte Einstellungen** aus.
    
    Sie können erweiterte Einstellungen für die globale Richtlinie sowie für bereichsbezogene Richtlinien konfigurieren.

4. Geben Sie auf dem Blatt **Erweiterte Einstellungen** den Namen und Wert der erweiterten Einstellung ein, und klicken Sie dann auf **Speichern und schließen**.

5. Klicken Sie auf **Veröffentlichen**, und stellen Sie sicher, dass Benutzer, für die diese Richtlinie gilt, alle Office-Anwendungen neu starten, die geöffnet waren.

6. Wenn Sie die Einstellung nicht mehr benötigen und zum Standardverhalten zurückkehren möchten, gehen Sie so vor: Rufen Sie auf dem Blatt **Erweiterte Einstellungen** das Kontextmenü (**...** ) neben der Einstellung auf, die Sie nicht mehr benötigen, und wählen Sie dann **Löschen** aus. Klicken Sie dann auf **Speichern und schließen**, und veröffentlichen Sie die geänderte Richtlinie erneut.

## <a name="prevent-sign-in-prompts-for-ad-rms-only-computers"></a>Verhindern von Anmeldeaufforderungen für Computer, die nur AD RMS verwenden

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen. Diese Konfiguration kann bei Computern, die nur mit AD RMS kommunizieren, zu einer unnötigen Anmeldeaufforderung für Benutzer führen. Sie können diese Anmeldeaufforderung verhindern, indem Sie das Verzeichnis bearbeiten:

Suchen Sie nach dem folgenden Wertnamen, und legen Sie anschließend die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Unabhängig von dieser Einstellung folgt der Azure Information Protection-Client dem [Prozess zur RMS-Diensterkennung](../rms-client/client-deployment-notes.md#rms-service-discovery), um sein AD RMS-Cluster zu finden.

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als ein anderer Benutzer anmelden, wenn sie den Azure Information Protection-Client verwenden. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

Sie können mithilfe des Dialogfelds **Microsoft Azure Information Protection** überprüfen, mit welchem Konto Sie gerade angemeldet sind: Öffnen Sie dazu eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. Ein Hinweis auf das Verwenden des falschen Kontos können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige der Bezeichnungen oder unerwartete Verhaltensweisen sein.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich von Windows abmelden und sich mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Registrierung bearbeitet haben. Der Azure Information Protection-Client wird automatisch mit Ihrem aktuell angemeldeten Benutzerkonto authentifiziert.

- Sie können die Option **Einstellungen zurücksetzen** unter **Hilfe und Feedback** verwenden, um sich abzumelden und die aktuell heruntergeladene Azure Information Protection-Richtlinie zu löschen.

## <a name="enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses"></a>Erzwingen des reinen Schutzmodus, wenn die Organisation über eine Kombination verschiedener Lizenzen verfügt

Wenn Ihre Organisation keine Lizenzen für Azure Information Protection besitzt, aber über Lizenzen für Office 365 verfügt, die den Azure Rights Management-Dienst für den Datenschutz umfassen, wird der Azure Information Protection-Client für Windows automatisch im [reinen Schutzmodus](../rms-client/client-protection-only-mode.md) ausgeführt.

Wenn Ihre Organisation jedoch über ein Abonnement für Azure Information Protection verfügt, können standardmäßig alle Windows-Computer die Azure Information Protection-Richtlinie herunterladen. Der Azure Information Protection-Client ist nicht für die Überprüfung und Erzwingung von Lizenzen zuständig. 

Wenn einige Ihrer Benutzer keine Lizenz für Azure Information Protection, aber eine Lizenz für Office 365 haben, die den Azure Rights Management-Dienst umfasst, bearbeiten Sie die Registrierung auf den Computern dieser Benutzer, um zu verhindern, dass diese Benutzer die nicht lizenzierten Klassifizierungs- und Bezeichnungsfeatures von Azure Information Protection ausführen.

Suchen Sie nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Überprüfen Sie außerdem, ob auf diesen Computern eine Datei namens **Policy.msip** im Ordner **%LocalAppData%\Microsoft\MSIP** vorhanden ist. Wenn diese Datei vorhanden ist, löschen Sie sie. Diese Datei enthält die Azure Information Protection-Richtlinie und wurde möglicherweise heruntergeladen, bevor Sie die Registrierung bearbeitet haben. Die Datei kann auch vorhanden sein, wenn der Azure Information Protection-Client mit der Demooption installiert wurde.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ausblenden der Menüoption „Klassifizieren und schützen“ im Windows-Dateiexplorer

Erstellen Sie den folgenden DWORD-Wert (mit beliebigen Wertdaten):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Unterstützung für getrennte Computer

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen, um die neueste Azure Information Protection-Richtlinie herunterzuladen. Wenn Sie über einen Computer verfügen, von dem Sie wissen, dass er für einen bestimmten Zeitraum keine Verbindung mit dem Internet herstellen kann, können Sie den Client durch Bearbeiten der Registrierung am Verbindungsversuch mit dem Dienst hindern. 

Suchen Sie nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Stellen Sie sicher, dass der Client über eine gültige Richtliniendatei namens **Policy.msip** im Ordner **%localappdata%\Microsoft\MSIP** verfügt. Falls erforderlich, können Sie die Richtlinie aus dem Azure-Portal exportieren und die exportierte Datei auf den Clientcomputer kopieren. Sie können mithilfe dieser Methode auch eine veraltete Richtliniendatei durch die neueste veröffentlichte Richtlinie ersetzen.

Beim Exportieren der Richtlinie wird von dieser Aktion auch eine gezippte Datei mit mehreren Versionen der Richtlinie heruntergeladen, die mit unterschiedlichen Versionen des Azure Information Protection-Clients übereinstimmen:

1. Entzippen Sie die Datei, und verwenden Sie die folgende Tabelle, um zu identifizieren, welche Richtliniendatei Sie benötigen. 
    
    |Dateiname|Entsprechende Clientversion|
    |--------------------------|---------------------------------------------|
    |Policy1.1.msip |Version 1.2|
    |Policy1.2.msip |Version 1.3 – 1.7|
    |Policy1.3.msip |Version 1.8 und höher|
    
2. Benennen Sie die identifizierte Datei zu **Policy.msip** um, und kopieren Sie sie in den Ordner **%LocalAppData%\Microsoft\MSIP** auf Computern, auf denen der Azure Information Protection-Client installiert ist. 


## <a name="hide-or-show-the-do-not-forward-button-in-outlook"></a>Ausblenden oder Anzeigen der Schaltfläche „Nicht weiterleiten“ in Outlook

Das empfohlene Vorgehen zum Konfigurieren dieser Option ist die Verwendung der [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md) **Add the Do Not Forward button to the Outlook ribbon** (Die Schaltfläche „Nicht weiterleiten“ dem Outlook-Menüband hinzufügen). Allerdings können Sie diese Option auch mithilfe einer [erweiterten Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal) konfigurieren. Dies können Sie über das Azure-Portal durchführen.

Wenn Sie diese Einstellung konfigurieren, wird die Schaltfläche **Nicht weiterleiten** auf dem Menüband in Outlook ausgeblendet oder angezeigt. Diese Einstellung hat keine Auswirkung auf die Option „Nicht weiterleiten“ der Office-Menüs.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **DisableDNF**

- Wert: **TRUE** zum Ausblenden der Schaltfläche, **FALSE** zum Anzeigen der Schaltfläche

## <a name="make-the-custom-permissions-options-available-or-unavailable-to-users"></a>Verfügbar- oder Nicht-Verfügbarmachen der Optionen für benutzerdefinierte Berechtigungen für Benutzer

Das empfohlene Vorgehen zum Konfigurieren dieser Option ist die Verwendung der [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md) **Make the custom permissions option available for users** (Die benutzerdefinierte Berechtigungsoption für Benutzer verfügbar machen). Allerdings können Sie diese Option auch mithilfe einer [erweiterten Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal) konfigurieren. Dies können Sie über das Azure-Portal durchführen. 

Wenn Sie diese Einstellung konfigurieren und die Richtlinie für Benutzer veröffentlichen, werden die benutzerdefinierten Berechtigungsoptionen für Benutzer verfügbar, woraufhin diese ihre eigenen Schutzeinstellungen auswählen können. Alternativ werden die Optionen nicht verfügbar gemacht, damit Benutzer ihre Schutzeinstellungen nicht wählen können, es sei denn, sie werden dazu aufgefordert.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **EnableCustomPermissions**

- Wert: **TRUE**, um die benutzerdefinierte Berechtigungsoption verfügbar zu machen; **FALSE**, um diese Option abzublenden.

> [!IMPORTANT]
> Sofern Sie nicht die aktuelle Vorschauversion des Clients verwenden, legen Sie diese Option nicht auf **FALSE** fest, wenn Sie über Bezeichnungen verfügen, für die benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint und den Datei-Explorer konfiguriert sind. Wenn Sie dies tun, wenn die Bezeichnung angewendet ist, werden Benutzer nicht dazu aufgefordert, die benutzerdefinierten Berechtigungen zu konfigurieren. Das führt dazu, dass das Dokument bezeichnet ist, aber nicht über den von Ihnen beabsichtigten Schutz verfügt.

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Azure Information Protection-Leiste dauerhaft ausblenden

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Verwenden Sie diese nur, wenn die [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md) **Display the Information Protection bar in Office apps** (Die Information Protection-Leiste in Office-Apps anzeigen) auf **Ein** festgelegt ist.

Wenn Sie diese Einstellung konfigurieren, die Richtlinie für Benutzer veröffentlichen und ein Benutzer die Azure Information Protection-Leiste nicht in seinen Office-Anwendungen anzeigen möchte, bleibt die Leiste ausgeblendet. Dies geschieht, wenn der Benutzer auf der Registerkarte **Start** in der Gruppe **Schutz** unter **Schützen** die Option **Leiste anzeigen** deaktiviert. Diese Einstellung hat keine Auswirkung, wenn der Benutzer die Leiste mithilfe des Symbols **Diese Leiste schließen** schließt.

Obwohl die Azure Information Protection-Leiste ausgeblendet bleibt, können Benutzer weiterhin eine Bezeichnung auf der vorübergehend angezeigten Leiste auswählen, wenn Sie die empfohlene Klassifizierung konfiguriert haben oder ein Dokument oder eine E-Mail-eine Bezeichnung aufweisen muss. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **EnableBarHiding**

- Wert: **TRUE**


## <a name="enable-recommended-classification-in-outlook"></a>Aktivieren der empfohlenen Klassifizierung in Outlook

Diese Konfigurationsoption ist zurzeit als Vorschau verfügbar und unterliegt Änderungen.

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen.

Wenn Sie eine Bezeichnung für die empfohlene Klassifizierung konfigurieren, werden Benutzer dazu aufgefordert, die empfohlene Bezeichnung in Word, Excel und PowerPoint anzunehmen oder abzulehnen. Diese Einstellung erweitert diese Bezeichnungsempfehlung, sodass sie auch in Outlook angezeigt wird.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **OutlookRecommendationEnabled**

- Wert: **TRUE**


## <a name="set-a-different-default-label-for-outlook"></a>Festlegen anderer Standardbezeichnung für Outlook

Diese Konfigurationsoption ist zurzeit als Vorschau verfügbar und unterliegt Änderungen. Außerdem erfordert sie die Vorschauversion des Clients.

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie diese Einstellung konfigurieren, wendet Outlook für die Einstellung **Standardbezeichnung auswählen** nicht die in der Azure Information Protection-Richtlinie konfigurierte Standardbezeichnung an. Stattdessen kann Outlook eine andere Standardbezeichnung oder gar keine Bezeichnung anwenden.

Um eine andere Bezeichnung anzuwenden, müssen Sie die Bezeichnungs-ID angeben. Der Wert der Bezeichnungs-ID wird auf dem Blatt **Bezeichnung** angezeigt, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal anzeigen oder konfigurieren. Bei Dateien, auf die Bezeichnungen angewendet wurden, können Sie auch das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) ausführen, um die Bezeichnungs-ID (MainLabelId oder SubLabelId) zu identifizieren. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, geben Sie immer die ID einer untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung.

Damit Outlook nicht die Standardbezeichnung anwendet, geben Sie **None** (Keine) an.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **OutlookDefaultLabel**

- Wert: \<**Bezeichnungs-ID**> oder **None** (Keine)

## <a name="label-an-office-document-by-using-an-existing-custom-property"></a>Hinzufügen einer Bezeichnung zu einem Office-Dokument über eine bereits bestehende benutzerdefinierte Eigenschaft

Diese Konfigurationsoption ist zurzeit als Vorschau verfügbar und unterliegt Änderungen. 

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie diese Einstellung konfigurieren, können Sie ein Office-Dokument klassifizieren (und unter Umständen schützen), wenn es über eine benutzerdefinierte Eigenschaft mit einem Wert verfügt, der einem Ihrer Bezeichnungsnamen entspricht. Diese benutzerdefinierte Eigenschaft kann aus einer Klassifizierungslösung stammen oder von SharePoint als eine Eigenschaft festgelegt worden sein.

Diese Konfiguration hat zur Folge, dass einem Dokument, das ohne eine Azure Information Protection-Bezeichnung von einem Benutzer in einer Office-App geöffnet oder gespeichert wird, eine Bezeichnung zugeordnet wird, die mit dem entsprechenden Eigenschaftswert übereinstimmt. 

Bevor Sie diese Konfiguration verwenden können, müssen Sie zunächst zwei erweiterte Einstellungen angeben, die miteinander interagieren. Die erste Einstellung wird **SyncPropertyName** genannt. Es handelt sich dabei um den benutzerdefinierten Eigenschaftsnamen, der von der anderen Klassifizierungslösung festgelegt worden ist, oder um eine Eigenschaft, die von SharePoint festgelegt wurde. Bei der zweiten Einstellung handelt es sich um **SyncPropertyState**. Diese muss auf „OneWay“ festgelegt sein.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel 1: **SyncPropertyName**

- Wert von Schlüssel 1: \<**Eigenschaftenname**> 

- Schlüssel 2: **SyncPropertyState**

- Wert von Schlüssel 2: **OneWay**

Verwenden Sie diesen Schlüssel und die entsprechenden Werte für lediglich eine benutzerdefinierte Eigenschaft.

Es gibt zum Beispiel eine SharePoint-Spalte mit dem Namen **Classification** und den möglichen Werten **Public**, **General** und **Confidential**. Dokumente werden in SharePoint gespeichert, und für sie ist einer dieser Werte für die Klassifizierungseigenschaft festgelegt.

Um einem Office-Dokument eine Bezeichnung dieser Klassifizierungswerte zuzuweisen, legen Sie **SyncPropertyName** auf **Classification** und **SyncPropertyState** auf **OneWay** fest. 

Wenn ein Benutzer jetzt eins dieser Office-Dokumente öffnet und speichert, wird diesem eine der folgenden Bezeichnungen zugeordnet: **Public**, **General** oder **Confidential**. Dies geschieht allerdings nur, wenn Bezeichnungen mit diesen Namen in der Azure Information Protection-Richtlinie vorhanden sind. Wenn es keine Bezeichnungen mit diesen Namen gibt, erhält das Dokument keine Bezeichnung.

## <a name="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution"></a>Integration in die Exchange-Nachrichtenklassifizierung für eine Lösung zur Bezeichnung mobiler Geräte

Obwohl Outlook im Web noch keine systemeigene Unterstützung für die Klassifizierung und den Schutz durch Azure Information Protection bietet, können Sie Ihre Azure Information Protection-Bezeichnungen mithilfe der Exchange-Nachrichtenklassifizierung auf Ihre mobilen Benutzer erweitern.

So erreichen Sie diese Lösung 

1. Verwenden Sie das Exchange PowerShell-Cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400), um Nachrichtenklassifizierungen mit der Name-Eigenschaft zu erstellen, die Ihren Bezeichnungsnamen in der Azure Information Protection-Richtlinie zugeordnet wird. 

2. Erstellen Sie eine Exchange-Transportregel für jede Bezeichnung. Wenden Sie die Regel an, wenn Nachrichteneigenschaften die von Ihnen konfigurierte Klassifizierung enthalten, und ändern Sie dann die Nachrichteneigenschaften, um einen Nachrichtenheader festzulegen. 

    Für den Nachrichtenheader finden Sie die anzugebenden Informationen, indem Sie die Internetheader einer E-Mail untersuchen, die Sie mithilfe Ihrer Azure Information Protection-Bezeichnung gesendet und klassifiziert haben. Suchen Sie nach den Header **msip_labels** und die darauf folgende Zeichenfolge, bis zu und einschließlich dem Semikolon. Verwenden des vorherigen Beispiels:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Geben Sie dann für den Nachrichtenheader in der Regel **msip_labels** für den Header und den Rest der Zeichenfolge für den Headerwert an. Beispiel:
    
    ![Beispieltransportregel für Exchange Online, die den Nachrichtenheader für eine bestimmte Azure Information Protection-Bezeichnung festlegt](../media/exchange-rule-for-message-header.png)

Bevor Sie diese Konfiguration testen, beachten Sie, dass es häufig zu einer Verzögerung beim Erstellen oder Bearbeiten von Transportregeln kommt (warten Sie eine Stunde). Ist die Regel in Kraft, geschieht Folgendes, wenn Benutzer Outlook im Web oder einen Client für mobile Geräte mit Unterstützung für den Rights Management-Schutz verwenden: 

- Benutzer wählen die Exchange-Nachrichtenklassifizierung aus, und senden die E-Mail.

- Die Exchange-Regel erkennt die Exchange-Klassifizierung und ändert entsprechend den Nachrichtenheader, um die Azure Information Protection-Klassifizierung hinzuzufügen.

- Wenn Empfänger die E-Mail in Outlook anzeigen und der Azure Information Protection-Client installiert ist, sehen sie, dass die Azure Information Protection-Bezeichnung sowie alle entsprechenden Kopfzeilen, Fußzeilen oder Wasserzeichen der E-Mail zugewiesen sind. 

Wenn die Azure Information Protection-Bezeichnungen einen entsprechenden Rechteverwaltungsschutz anwenden, fügen Sie diesen Schutz zur Regelkonfiguration hinzu, indem Sie die Option zum Ändern der Nachrichtensicherheit ändern, den Rechteschutz anwenden und dann die RMS-Vorlage oder die Option „Nicht weiterleiten“ auswählen.

Sie können Transportregeln auch so konfigurieren, dass sie die umgekehrte Zuordnung vornehmen. Wenn eine Azure Information Protection-Bezeichnung erkannt wird, legen Sie eine entsprechende Exchange-Nachrichtenklassifizierung fest:

- Erstellen Sie für jede Azure Information Protection-Bezeichnung eine Transportregel, die angewendet wird, wenn der Header **msip_labels** den Namen Ihrer Bezeichnung enthält (z.B. **Allgemein**), und wenden Sie eine Nachrichtenklassifizierung an, die dieser Bezeichnung zugeordnet wird.


## <a name="next-steps"></a>Nächste Schritte
Nachdem Sie den Azure Information Protection-Client angepasst haben, lesen Sie die folgenden Artikel, die Sie eventuell zur Unterstützung dieses Clients benötigen:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
