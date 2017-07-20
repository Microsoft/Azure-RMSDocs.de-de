---
title: "Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client"
description: "Informationen zum Anpassen des Azure Information Protection-Clients für Windows"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/18/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 5b5f8b336e1946bc4c394b9154eed50844b6b72b
ms.sourcegitcommit: 1c3ebf4ad64b55db4fec3ad007fca71ab7d38c02
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/18/2017
---
# <a name="custom-configurations-for-the-azure-information-protection-client"></a>Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie bei der Verwaltung des Azure Information Protection-Clients möglicherweise für spezifische Szenarien oder eine Teilmenge der Benutzer benötigen.

Einige dieser Einstellungen erfordern die Bearbeitung der Registrierung. Andere sind erweiterte Einstellungen, die Sie im Azure-Portal konfigurieren und anschließend für das Herunterladen durch Clients veröffentlichen müssen. 

Darüber hinaus stehen einige Einstellungen möglicherweise nur in einer Vorschauversion des Azure Information Protection-Clients zur Verfügung. Für diese Einstellungen ist eine Mindestversion des Clients angegeben. Für Einstellungen und Konfigurationen, die in der allgemein verfügbaren Version des Clients unterstützt werden, ist keine Mindestversion des Clients angegeben.

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

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als ein anderer Benutzer anmelden, wenn sie den Azure Information Protection-Client verwenden. Allerdings müssen Sie sich als Administrator möglicherweise als ein anderer Benutzer anmelden. Dies gilt z.B., wenn Ihre Organisation zusätzlich zu einem Office 365- oder einem Azure-Mandanten auch einen Testmandanten in der Produktionsumgebung verwendet.

Sie können mithilfe des Dialogfelds **Microsoft Azure Information Protection** überprüfen, mit welchem Konto Sie gerade angemeldet sind: Öffnen Sie dazu eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie – insbesondere bei Nutzung eines Administratorkontos – den angezeigten Domänennamen des angemeldeten Kontos. Beispiel: Wenn Sie ein Administratorkonto für zwei verschiedene Mandanten haben, kann leicht übersehen werden, dass Sie zwar mit dem richtigen Kontonamen, aber mit der falschen Domäne angemeldet sind. Ein Hinweis auf das Verwenden des falschen Kontos können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige der Bezeichnungen oder unerwartete Verhaltensweisen sein.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie im Registrierungs-Editor zu **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**, und löschen Sie den **TokenCache**-Wert (und die zugehörigen Wertdaten).

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich von Windows abmelden und sich mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Registrierung bearbeitet haben. Der Azure Information Protection-Client wird automatisch mit Ihrem aktuell angemeldeten Benutzerkonto authentifiziert.

- Wenn Sie die Benutzereinstellungen des Azure Rights Management-Diensts zurücksetzen möchten, Sie können dazu die Option **Hilfe und Feedback** nutzen.

- Wenn Sie die aktuell heruntergeladene Azure Information Protection-Richtlinie löschen möchten, löschen Sie die Datei **Policy.msip** aus dem Ordner **%localappdata%\Microsoft\MSIP**.

## <a name="hide-the-classify-and-protect-menu-option-in-windows-file-explorer"></a>Ausblenden der Menüoption „Klassifizieren und schützen“ im Windows-Dateiexplorer

Sie können diese erweiterte Konfiguration einrichten, indem Sie die Registrierung bearbeiten, wenn Sie den Azure Information Protection-Client in der Version 1.3.0.0 oder höher verwenden. 

Erstellen Sie den folgenden DWORD-Wert (mit beliebigen Wertdaten):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

## <a name="support-for-disconnected-computers"></a>Unterstützung für getrennte Computer

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen, um die neueste Azure Information Protection-Richtlinie herunterzuladen. Wenn Sie über einen Computer verfügen, von dem Sie wissen, dass er für einen bestimmten Zeitraum keine Verbindung mit dem Internet herstellen kann, können Sie den Client durch Bearbeiten der Registrierung am Verbindungsversuch mit dem Dienst hindern. 

Suchen Sie nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Stellen Sie sicher, dass der Client über eine gültige Richtliniendatei namens **Policy.msip** im Ordner **%localappdata%\Microsoft\MSIP** verfügt. Falls erforderlich, können Sie die Richtlinie aus dem Azure-Portal exportieren und die exportierte Datei auf den Clientcomputer kopieren. Sie können mithilfe dieser Methode auch eine veraltete Richtliniendatei durch die neueste veröffentlichte Richtlinie ersetzen.

## <a name="hide-the-do-not-forward-button-in-outlook"></a>Ausblenden der Schaltfläche „Nicht weiterleiten“ in Outlook

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. Diese Einstellung erfordert auch eine Vorschauversion des Azure Information Protection-Clients mit der Mindestversion **1.8.41.0**.

Wenn Sie diese Einstellung konfigurieren, wird die Schaltfläche **Nicht weiterleiten** auf dem Menüband in Outlook ausgeblendet. In Office-Menüs wird diese Option nicht ausgeblendet.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **DisableDNF**

- Wert: **TRUE**

## <a name="make-the-custom-permissions-options-unavailable-to-users"></a>Die Optionen für benutzerdefinierte Berechtigungen für Benutzer nicht verfügbar machen

Diese Konfiguration verwendet eine [erweiterte Clienteinstellung](#how-to-configure-advanced-client-configuration-settings-in-the-portal), die Sie im Azure-Portal konfigurieren müssen. 

Wenn Sie diese Einstellung konfigurieren und die Richtlinie für Benutzer veröffentlichen, sind die Optionen für benutzerdefinierte Berechtigungen an den folgenden Speicherorten für Benutzer nicht auswählbar:

- In Office-Anwendungen: Registerkarte **Start** > Gruppe **Schutz** > **Schützen** > **Benutzerdefinierte Berechtigungen**

- In Datei-Explorer: Klicken mit der rechten Maustaste > **Klassifizieren und schützen** > **Benutzerdefinierte Berechtigungen**

Diese Einstellung hat keine Auswirkungen auf benutzerdefinierte Berechtigungen, die Sie über Office-Menüoptionen konfigurieren können. 

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **EnableCustomPermissions**

- Wert: **FALSE**

## <a name="permanently-hide-the-azure-information-protection-bar"></a>Azure Information Protection-Leiste dauerhaft ausblenden

Diese Konfiguration verwendet eine erweiterte Einstellung, die Sie im Azure-Portal konfigurieren müssen. Diese Einstellung erfordert auch eine Vorschauversion des Azure Information Protection-Clients mit der Mindestversion **1.9.58.0**.

Wenn Sie diese Einstellung konfigurieren, die Richtlinie für Benutzer veröffentlichen und ein Benutzer die Azure Information Protection-Leiste nicht in seinen Office-Anwendungen anzeigen möchte, bleibt die Leiste ausgeblendet. Dies geschieht, wenn der Benutzer auf der Registerkarte **Start** in der Gruppe **Schutz** unter **Schützen** die Option **Leiste anzeigen** deaktiviert. Diese Einstellung hat keine Auswirkung, wenn der Benutzer die Leiste mithilfe des Symbols **Diese Leiste schließen** schließt.

Obwohl die Azure Information Protection-Leiste ausgeblendet bleibt, können Benutzer weiterhin eine Bezeichnung auf der vorübergehend angezeigten Leiste auswählen, wenn Sie die empfohlene Klassifizierung konfiguriert haben oder ein Dokument oder eine E-Mail-eine Bezeichnung aufweisen muss. Die Einstellung wirkt sich auch nicht auf Bezeichnungen, die Sie oder andere konfigurieren, wie z.B. manuelle oder automatische Klassifizierung, oder das Festlegen einer Standardbezeichnung aus.

Um diese erweiterte Einstellung zu konfigurieren, geben Sie die folgenden Zeichenfolgen ein:

- Schlüssel: **EnableBarHiding**

- Wert: **TRUE**

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
