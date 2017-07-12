---
title: "Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client"
description: "Informationen zum Anpassen des Azure Information Protection-Clients für Windows"
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 6ab5465db1527e6236d2dca466936c36b260f03d
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="custom-configurations-for-the-azure-information-protection-client" class="xliff"></a>

# Benutzerdefinierte Konfigurationen für den Azure Information Protection-Client

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012*

Verwenden Sie die folgenden Informationen für erweiterte Konfigurationen, die Sie bei der Verwaltung des Azure Information Protection-Clients möglicherweise für spezifische Szenarien oder eine Teilmenge der Benutzer benötigen. 

<a id="prevent-sign-in-prompts-for-ad-rms-only-computers" class="xliff"></a>

## Verhindern von Anmeldeaufforderungen für Computer, die nur AD RMS verwenden

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen. Dies kann bei Computern, die nur mit AD RMS kommunizieren, zu einer unnötigen Anmeldeaufforderung für Benutzer führen. Sie können diese Anmeldeaufforderung verhindern, indem Sie das Verzeichnis bearbeiten:

Suchen Sie nach dem folgenden Wertnamen, und legen Sie anschließend die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Unabhängig von dieser Einstellung folgt der Azure Information Protection-Client dem [Prozess zur RMS-Diensterkennung](../rms-client/client-deployment-notes.md#rms-service-discovery), um sein AD RMS-Cluster zu finden.

<a id="sign-in-as-a-different-user" class="xliff"></a>

## Anmelden als ein anderer Benutzer

In einer Produktionsumgebung müssen sich Benutzer in der Regel nicht als ein anderer Benutzer anmelden, wenn sie den Azure Information Protection-Client verwenden. Als Administrator ist dies jedoch möglicherweise erforderlich, wenn Sie über mehrere Mandanten verfügen. Dies gilt z.B., wenn Ihre Organisation zusätzlich zu einem Office 365- oder einem Azure-Mandanten auch einen Testmandanten verwendet.

Sie können mithilfe des Dialogfelds **Microsoft Azure Information Protection** überprüfen, mit welchem Konto Sie gerade angemeldet sind: Öffnen Sie dazu eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie – insbesondere bei Nutzung eines Administratorkontos – den angezeigten Domänennamen des angemeldeten Kontos. Beispiel: Wenn Sie ein Administratorkonto für zwei verschiedene Mandanten haben, kann leicht übersehen werden, dass Sie zwar mit dem richtigen Kontonamen, aber mit der falschen Domäne angemeldet sind. Ein Hinweis darauf können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige erwarteter Bezeichnungen oder unerwartete Verhaltensweisen sein.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie im Registrierungs-Editor zu **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**, und löschen Sie den **TokenCache**-Wert (und die zugehörigen Wertdaten).

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich von Windows abmelden und sich mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Registrierung bearbeitet haben. Der Azure Information Protection-Client wird automatisch mit Ihrem aktuell angemeldeten Benutzerkonto authentifiziert.

- Um die Umgebung für den Azure Rights Management-Dienst (auch bekannt als Bootstrapping) erneut zu initialisieren, verwenden Sie die Option **Zurücksetzen** im [RMS Analyzer Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Wenn Sie die aktuell heruntergeladene Azure Information Protection-Richtlinie löschen möchten, löschen Sie die Datei **Policy.msip** aus dem Ordner **%localappdata%\Microsoft\MSIP**.

<a id="hide-the-classify-and-protect-menu-option-in-windows-file-explorer" class="xliff"></a>

## Ausblenden der Menüoption „Klassifizieren und schützen“ im Windows-Dateiexplorer

Sie können diese erweiterte Konfiguration einrichten, indem Sie die Registrierung bearbeiten, wenn Sie den Azure Information Protection-Client in der Version 1.3.0.0 oder höher verwenden. 

Erstellen Sie den folgenden DWORD-Wert (mit beliebigen Wertdaten):

**HKEY_CLASSES_ROOT\AllFilesystemObjects\shell\Microsoft.Azip.RightClick\LegacyDisable**

<a id="support-for-disconnected-computers" class="xliff"></a>

## Unterstützung für getrennte Computer

Der Azure Information Protection-Client versucht standardmäßig, eine Verbindung mit dem Azure Information Protection-Dienst herzustellen, um die neueste Azure Information Protection-Richtlinie herunterzuladen. Wenn Sie über einen Computer verfügen, von dem Sie wissen, dass er für einen bestimmten Zeitraum keine Verbindung mit dem Internet herstellen kann, können Sie den Client durch Bearbeiten der Registrierung am Verbindungsversuch mit dem Dienst hindern. Suchen Sie nach dem folgenden Wertnamen, und legen Sie die Wertdaten auf **0** fest:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\EnablePolicyDownload** 

Stellen Sie sicher, dass der Client über eine gültige Richtliniendatei namens **Policy.msip** im Ordner **%localappdata%\Microsoft\MSIP** verfügt. Falls erforderlich, können Sie die Richtlinie aus dem Azure-Portal exportieren und die exportierte Datei auf den Clientcomputer kopieren. Sie können mithilfe dieser Methode auch eine veraltete Richtliniendatei durch die neueste veröffentlichte Richtlinie ersetzen.

<a id="integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution" class="xliff"></a>

## Integration in die Exchange-Nachrichtenklassifizierung für eine Lösung zur Bezeichnung mobiler Geräte

Obwohl Outlook im Web noch keine systemeigene Unterstützung für die Klassifizierung und den Schutz durch Azure Information Protection bietet, können Sie Ihre Azure Information Protection-Bezeichnungen mithilfe der Exchange-Nachrichtenklassifizierung auf Ihre mobilen Benutzer erweitern.

So erreichen Sie diese Lösung 

1. Verwenden Sie das Exchange PowerShell-Cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400), um Nachrichtenklassifizierungen mit der Name-Eigenschaft zu erstellen, die Ihren Bezeichnungsnamen in der Azure Information Protection-Richtlinie zugeordnet wird. 

2. Erstellen Sie eine Exchange-Transportregel für jede Bezeichnung. Wenden Sie die Regel an, wenn Nachrichteneigenschaften die von Ihnen konfigurierte Klassifizierung enthalten, und ändern Sie dann die Nachrichteneigenschaften, um einen Nachrichtenheader festzulegen. 

    Für den Nachrichtenheader finden Sie die anzugebenden Informationen, indem Sie die Internetheader einer E-Mail untersuchen, die Sie mithilfe Ihrer Azure Information Protection-Bezeichnung gesendet und klassifiziert haben. Suchen Sie nach den Header **msip_labels** und die darauf folgende Zeichenfolge, bis zu und einschließlich dem Semikolon. Verwenden des vorherigen Beispiels:
    
    **msip_labels: MSIP_Label_0e421e6d-ea17-4fdb-8f01-93a3e71333b8_Enabled=True;**
    
    Geben Sie dann für den Nachrichtenheader in der Regel **msip_labels** für den Header und den Rest der Zeichenfolge für den Headerwert an. Beispiel:
    
    ![Beispieltransportregel für Exchange Online, die den Nachrichtenheader für eine bestimmte Azure Information Protection-Bezeichnung festlegt](../media/exchange-rule-for-message-header.png)

Bevor Sie dies testen, beachten Sie, dass es häufig zu einer Verzögerung beim Erstellen oder Bearbeiten von Transportregeln kommt (warten Sie eine Stunde). Ist die Regel in Kraft, geschieht Folgendes, wenn Benutzer Outlook im Web oder einen Client für mobile Geräte mit Unterstützung für den Rights Management-Schutz verwenden: 

- Benutzer wählen die Exchange-Nachrichtenklassifizierung aus, und senden die E-Mail.

- Die Exchange-Regel erkennt die Exchange-Klassifizierung und ändert entsprechend den Nachrichtenheader, um die Azure Information Protection-Klassifizierung hinzuzufügen.

- Wenn Empfänger, die den Azure Information Protection-Client ausführen, die E-Mail in Outlook anzeigen, sehen sie, dass die Azure Information Protection-Bezeichnung sowie alle entsprechenden Kopfzeilen, Fußzeilen oder Wasserzeichen der E-Mail zugewiesen sind. 

Wenn die Azure Information Protection-Bezeichnungen einen entsprechenden Rechteverwaltungsschutz anwenden, fügen Sie diesen zur Regelkonfiguration hinzu, indem Sie die Option zum Ändern der Nachrichtensicherheit ändern, den Rechteschutz anwenden und dann die RMS-Vorlage oder die Option „Nicht weiterleiten“ auswählen.

Sie können Transportregeln auch so konfigurieren, dass sie die umgekehrte Zuordnung vornehmen: Wenn eine Azure Information Protection-Bezeichnung erkannt wird, legen Sie eine entsprechende Exchange-Nachrichtenklassifizierung fest. Dazu gehen Sie folgendermaßen vor:

- Erstellen Sie für jede Azure Information Protection-Bezeichnung eine Transportregel, die angewendet wird, wenn der Header **msip_labels** den Namen Ihrer Bezeichnung enthält (z.B. **Allgemein**), und wenden Sie eine Nachrichtenklassifizierung an, die dieser Bezeichnung zugeordnet wird.


<a id="next-steps" class="xliff"></a>

## Nächste Schritte
Nachdem Sie den Azure Information Protection-Client angepasst haben, lesen Sie folgende zusätzliche Informationen, die Sie eventuell zur Unterstützung dieses Clients benötigen:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Dokumentenverfolgung](client-admin-guide-document-tracking.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]
