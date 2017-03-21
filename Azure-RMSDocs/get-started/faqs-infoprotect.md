---
title: "Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen – AIP"
description: Haben Sie Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen bei Azure Information Protection beziehen? Vielleicht finden Sie hier eine Antwort darauf.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 854de3beea1f4b6e05461dee58cec6ca91f79034
ms.sourcegitcommit: 117e4016794d0cb9b7bd95603fb6c79114d65360
translationtype: HT
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort darauf. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Was kann ich mit den Klassifizierungsfunktionen in Azure Information Protection tun?

Probieren Sie unser Schnellstart-Tutorial aus, um zu sehen, wie dies innerhalb weniger Minuten funktioniert: [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).

Achten Sie auf Ankündigungen im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) (Informationen in englischer Sprache zu Enterprise Mobility und Security) und auf unserer [Yammer-Seite](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), um zu erfahren, wann zusätzliche Klassifizierungsfeatures und -funktionen verfügbar sind: Die aktuelle Version hat einige Einschränkungen, einschließlich der Folgenden:

- Bezeichnungsnamen und QuickInfos werden nur in einer Sprache unterstützt.

- Es gibt keine zentrale Protokollierung für die Klassifizierung und die Bezeichnung.

- Bedingungen für die automatische Klassifizierung müssen Ausdrücke oder Muster sein.

- Keine Bezeichnungsmöglichkeit für Office-Apps für mobile Geräte (iOS und Android) und Mac-Computer oder für die Office Web Apps (Office Online).

- Keine Klassifizierungs- und Bezeichnungsintegration mit Exchange Online oder SharePoint Online.

- Das SDK für Partner und Entwickler enthält noch keine Klassifizierung und Bezeichnung.

Die Version von Februar entfernt viele zuvor enthaltene Einschränkungen. Weitere Informationen finden Sie in der [Ankündigung zum Blogbeitrag](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/08/azure-information-protection-december-update-moves-to-general-availability/).

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>Muss ich ein globaler Administrator sein, um Klassifizierungen und Bezeichnungen zu konfigurieren?

Damit Sie die Azure Information Protection-Richtlinie konfigurieren können, müssen Sie sich im Azure-Portal als ein globaler Administrator für Azure Active Directory anmelden.

Wenn Sie die Option zum Installieren der Demorichtlinie bei der Installation des [Azure Information Protection-Clients](https://www.microsoft.com/en-us/download/details.aspx?id=53018) auswählen, müssen Sie sich nicht beim Portal anmelden, um die Bezeichnungsfunktion testen zu können. Die Demorichtlinie installiert lokal die Standardrichtlinie für Azure Information Protection. Sie können daher versuchen, Dokumente und E-Mails zu bezeichnen. Sie werden jedoch nicht in der Lage sein, neue Bezeichnungen zu ändern oder hinzuzufügen, ohne sich beim Azure-Portal anzumelden. 

## <a name="which-options-in-the-azure-portal-are-p1-or-p2"></a>Welche Optionen im Azure-Portal sind P1 oder P2?

Informationen dazu, welche Features im Abonnement **Azure Information Protection Premium 1** (P1) im Vergleich mit dem Abonnement **Azure Information Protection Premium 2** (P2) enthalten sind, finden Sie in der [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website. Als allgemeine Richtlinie sind die erweiterten Features wie automatische Klassifizierung und Hold Your Own Key (HYOK) jedoch für das Abonnement von Azure Informationen Protection Premium 2 spezifisch.

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet – eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Geheim** Unterbezeichnungen wie z.B. **Recht** und **Finanzen** enthalten. Sie können unterschiedliche optische Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Geheim** nicht selbst auswählen; nur eine der untergeordneten Bezeichnungen wie z.B. **Recht**. Daher wird als festgelegte Bezeichnung **Geheim\Recht** angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Geheim**, eine benutzerdefinierte Texteigenschaft für **Recht** und eine weitere mit beiden Werten (**Geheim Recht**). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen auf der übergeordneten und ihrer untergeordneten Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anlagen erhalten entweder keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Anlagen angewendet.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Wie unterscheidet sich die Azure Information Protection-Klassifizierung für E-Mails von der Exchange-Nachrichtenklassifizierung?

Die Exchange-Nachrichtenklassifizierung ist ein älteres Feature, das unabhängig von einer Azure Information Protection-Klassifizierung implementiert wird, und mit dem E-Mails klassifiziert werden können. Sie können jedoch beide Lösungen integrieren, damit die Azure Information Protection-Klassifizierung und entsprechende Bezeichnungsmarkierungen automatisch hinzugefügt werden, wenn Benutzer eine E-Mail mithilfe der Outlook Web-App und einiger mobiler E-Mail-Anwendungen klassifizieren. Exchange fügt die Klassifizierung hinzu und der Azure Information Protection-Client wendet die entsprechenden Bezeichnungseinstellungen für diese Klassifizierung an.

Obwohl die Outlook Web-App die Azure Information Protection-Klassifizierung und den Schutz noch nicht systemintern unterstützt, können Sie diese Technik dazu verwenden, um Ihre Bezeichnungen zusätzlich zum Outlook-Desktopclient mit diesem E-Mail-Client zu nutzen.

So erreichen Sie diese Lösung 

1. Verwenden Sie das Exchange PowerShell-Cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400), um Nachrichtenklassifizierungen mit der Name-Eigenschaft zu erstellen, die Ihren Bezeichnungsnamen in der Azure Information Protection-Richtlinie zugeordnet wird. 

2. Erstellen Sie eine Exchange-Transportregel für jede Bezeichnung. Wenden Sie die Regel an, wenn Nachrichteneigenschaften die von Ihnen konfigurierte Klassifizierung enthalten, und ändern Sie dann die Nachrichteneigenschaften, um einen Nachrichtenheader festzulegen. 

    Für den Nachrichtenheader finden Sie die anzugebenden Informationen, indem Sie die Eigenschaften einer von Ihnen mit der Azure Information Protection-Bezeichnung klassifizierten Office-Datei untersuchen. Identifizieren Sie die Dateieigenschaft mit dem Format **MSIP_Label_<GUID>_Enabled**, und geben Sie diese Zeichenfolge für den Nachrichtenheader und dann **True** für den Headerwert an. Ihr Nachrichtenheader kann z. B. wie die folgende Zeichenfolge aussehen: **MSIP_Label_132616b8-f72d-5d1e-aec1-dfd89eb8c5b2_Enabled**.


Jetzt geschieht Folgendes, wenn Benutzer die Outlook Web Access-App oder einen Client auf einem mobilen Gerät verwenden, das den Rechteverwaltungsschutz unterstützt: 

- Benutzer wählen die Exchange-Nachrichtenklassifizierung aus, und senden die E-Mail.

- Die Exchange-Regel erkennt die Exchange-Klassifizierung und ändert entsprechend den Nachrichtenheader, um die Azure Information Protection-Klassifizierung hinzuzufügen.

- Wenn Empfänger, die den Azure Information Protection-Client ausführen, die E-Mail in Outlook anzeigen, sehen sie, dass die Azure Information Protection-Bezeichnung sowie alle entsprechenden Kopfzeilen, Fußzeilen oder Wasserzeichen der E-Mail zugewiesen sind. 

Wenn die Azure Information Protection-Bezeichnungen einen entsprechenden Rechteverwaltungsschutz anwenden, fügen Sie diesen zur Regelkonfiguration hinzu, indem Sie die Option zum Ändern der Nachrichtensicherheit ändern, den Rechteschutz anwenden und dann die RMS-Vorlage oder die Option „Nicht weiterleiten“ auswählen.

Sie können Transportregeln auch so konfigurieren, dass sie die umgekehrte Zuordnung vornehmen: Wenn eine Azure Information Protection-Bezeichnung erkannt wird, legen Sie eine entsprechende Exchange-Nachrichtenklassifizierung fest. Dazu gehen Sie folgendermaßen vor:

- Erstellen Sie für jede Azure Information Protection-Bezeichnung eine Transportregel, die angewendet wird, wenn der Header **msip_labels** den Namen Ihrer Bezeichnung enthält (z.B. **Vertraulich**), und wenden Sie eine Nachrichtenklassifizierung an, die dieser Bezeichnung zugeordnet wird.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. In Dateien werden diese Metadaten in benutzerdefinierten Eigenschaften gespeichert. In E-Mails befinden sich diese Informationen in den E-Mail-Kopfzeilen.

## <a name="how-do-i-sign-in-as-a-different-user"></a>Wie kann ich mich als anderer Benutzer anmelden?

Bei Verwendung des Azure Information Protection-Clients müssen Sie sich in einer Produktionsumgebung in der Regel nicht als anderer Benutzer anmelden. Dies kann jedoch der Fall sein, wenn Sie über mehrere Mandanten verfügen. Dies gilt z.B., wenn Ihre Organisation zusätzlich zu einem Office 365- oder einem Azure-Mandanten auch einen Testmandanten verwendet.

Sie können mithilfe des Dialogfelds **Microsoft Azure Information Protection** überprüfen, mit welchem Konto Sie gerade angemeldet sind: Öffnen Sie dazu eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie – insbesondere bei Nutzung eines Administratorkontos – den angezeigten Domänennamen des angemeldeten Kontos. Beispiel: Wenn Sie ein Administratorkonto für zwei verschiedene Mandanten haben, kann leicht übersehen werden, dass Sie zwar mit dem richtigen Kontonamen, aber mit der falschen Domäne angemeldet sind. Ein Hinweis darauf können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige erwarteter Bezeichnungen oder unerwartete Verhaltensweisen sein.

Um sich als anderer Benutzer anzumelden, müssen Sie derzeit die Registrierung bearbeiten:

1. Navigieren Sie in einem Registrierungs-Editor zu **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**, und löschen Sie den **TokenCache**-Wert.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Wenn Sie das einmalige Anmelden verwenden, müssen Sie sich nach dem Bearbeiten der Registrierung von Windows abmelden und dann mit Ihrem anderen Benutzerkonto wieder anmelden. Der Azure Information Protection-Client wird automatisch mit Ihrem aktuell angemeldeten Benutzerkonto authentifiziert.

- Um die Umgebung für den Azure Rights Management-Dienst (auch bekannt als Bootstrapping) erneut zu initialisieren, verwenden Sie die Option **Zurücksetzen** im [RMS Analyzer Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Um die gerade heruntergeladene Azure Information Protection-Richtlinie wieder zu entfernen, löschen Sie die Datei **Policy.msip** aus dem Ordner „%localappdata%\Microsoft\MSIP“.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]