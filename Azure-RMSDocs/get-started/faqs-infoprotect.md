---
title: "Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen | Azure Information Protection"
description: Haben Sie eine Frage zum Vorschaurelease von Azure Information Protection? Vielleicht finden Sie hier eine Antwort darauf.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/09/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 946daa8dedba71d5887dd96f6853e8d90400bfb1
ms.openlocfilehash: 125752671ec0ca556cc6967a2a3011fb0bf7d9ab


---

# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort darauf. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Was kann ich mit den Klassifizierungsfunktionen in Azure Information Protection tun?

Der Azure Information Protection-Client fügt Microsoft Office-Anwendungen eine Information Protection-Leiste hinzu, mit der Sie zugewiesene Klassifizierungsbezeichnungen zu Daten anzeigen und ändern können. Die Klassifizierung kann manuell erfolgen oder, was empfohlen wird, automatisch angewendet werden. Für die Klassifizierungen, die Sie angeben, können Daten mithilfe eines Rights Management-Diensts geschützt werden.  

Die Klassifizierungsbezeichnungen und das -verhalten werden im Azure-Portal konfiguriert. Sie können die integrierte Standardrichtlinie verwenden, um Azure Information Protection sehr schnell auszuwerten, oder Sie können Ihre eigenen Richtlinien vollständig anpassen. Sie können die Farben, Namen und die Reihenfolge der Klassifizierungsbezeichnungen ändern, die Benutzern angezeigt werden. Sie können auch QuickInfos und optische Klassifizierungskennzeichnungen, wie z.B. Kopf-, Fußzeile oder ein Wasserzeichen konfigurieren.

Probieren Sie unser Schnellstart-Tutorial aus, um zu sehen, wie dies innerhalb weniger Minuten funktioniert: [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).

Die aktuelle Version unterliegt den folgenden Einschränkungen. Achten Sie auf Ankündigungen im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) (Informationen in englischer Sprache zu Enterprise Mobility und Security) und auf unserer [Yammer-Seite](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), um zu erfahren, wann zusätzliche Features und Funktionen verfügbar sind:

- Bezeichnungsnamen und QuickInfos werden nur in einer Sprache unterstützt.

- Es gibt keine zentrale Protokollierung für die Klassifizierung und die Bezeichnung.

- Bedingungen für die automatische Klassifizierung müssen Ausdrücke oder Muster sein.

- Office-Apps für mobile Geräte (iOS und Android) und Mac-Computer und die Office Web Apps (Office Online) werden nicht unterstützt.

- Keine Integration mit Exchange Online oder SharePoint Online.

- Das SDK für Partner und Entwickler ist nicht verfügbar.

Einige der oben aufgeführten Einschränkungen sind jetzt in der Vorschau verfügbar. Weitere Informationen finden Sie in der Blogbeitragsankündigung: [Azure Information Protection – Dezember-Vorschau jetzt verfügbar](https://blogs.technet.microsoft.com/enterprisemobility/2016/12/07/azure-information-protection-december-preview-now-available/).


## <a name="do-i-need-to-be-a-global-admin-to-try-azure-information-protection"></a>Muss ich über globale Administratorrechte verfügen, um Azure Information Protection testen zu können?

Damit Sie die Azure Information Protection-Richtlinie konfigurieren können, müssen Sie sich im Azure-Portal als ein globaler Administrator für Azure Active Directory anmelden.

Wenn Sie jedoch die Option zum Installieren der Demorichtlinie bei der Installation des [Azure Information Protection-Clients](https://www.microsoft.com/en-us/download/details.aspx?id=53018) auswählen, müssen Sie sich nicht beim Portal anmelden, um die Bezeichnungsfunktion testen zu können. Die Demorichtlinie installiert lokal die Standardrichtlinie für Azure Information Protection. Sie können daher versuchen, Dokumente und E-Mails zu bezeichnen. Sie werden jedoch nicht in der Lage sein, neue Bezeichnungen zu ändern oder hinzuzufügen, ohne sich beim Azure-Portal anzumelden. 

## <a name="which-options-in-the-azure-portal-are-p1-or-p2"></a>Welche Optionen im Azure-Portal sind P1 oder P2?

Informationen dazu, welche Features im Abonnement **Azure Information Protection Premium 1** (P1) im Vergleich mit dem Abonnement **Azure Information Protection Premium 2** (P2) enthalten sind, finden Sie in der [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website. Als allgemeine Richtlinie sind die erweiterten Features wie automatische Klassifizierung und Hold Your Own Key (HYOK) jedoch für das Abonnement von Azure Informationen Protection Premium 2 spezifisch.

## <a name="does-azure-information-protection-support-on-premises-and-hybrid-scenarios"></a>Unterstützt Azure Information Protection lokale und hybride Szenarios?

Azure Information Protection ist eine cloudbasierte Lösung. Wenn Sie Interesse an der Bereitstellung von Azure Information Protection für ein hybrides Szenario haben, wenden Sie sich an das Information Protection-Team, indem Sie eine E-Mail an askipteam@microsoft.com senden.

## <a name="how-do-computers-get-the-policy-information-from-azure-information-protection-and-how-often-is-it-refreshed"></a>Wie erhalten Computer die Richtlinieninformationen von Azure Information Protection, und wie oft werden diese aktualisiert?

Jedes Mal, wenn ein Benutzer eine Office-Anwendung öffnet, überprüft der Azure Information Protection-Client, ob eine höhere Version der Azure Information Protection-Richtlinie verfügbar ist. Office-Programme führen diese Prüfung zusätzlich alle 24 Stunden durch. Wenn eine höhere Version verfügbar ist, lädt der Client sie herunter, wobei er einen HTTPS-Link verwendet, um die Daten zu sichern. 

Wenn bei der Veröffentlichung einer neuen Azure Information Protection-Richtlinie mehrere Instanzen der Office-Anwendung geladen sind, müssen Sie alle Instanzen schließen, um die aktuelle Version der Richtlinie abzurufen. Beispiel: Sie haben zwei Word-Dokumente geöffnet, möchten die aktualisierte Azure Information Protection-Richtlinie jedoch nur in einem Dokument testen: Schließen Sie beide Word-Dokumente, und öffnen Sie das Dokument erneut, das mit der aktuellen Richtlinie verwendet werden soll.

## <a name="where-can-files-be-stored-to-use-azure-information-protection"></a>Wo können Dateien gespeichert werden, um Azure Information Protection zu verwenden? 

Da Azure Information Protection persistente Bezeichnungen und persistenten Schutz für Dateien und E-Mails anwendet, ist es egal, wo die Dateien gespeichert werden.

## <a name="can-i-classify-only-new-data-or-can-i-also-classify-existing-data"></a>Kann ich nur neue Daten klassifizieren, oder kann ich auch vorhandene Daten klassifizieren?

Aktionen der Azure Information Protection-Richtlinie werden wirksam, wenn Dokumente gespeichert und E-Mails versendet werden. Dies gilt für neuen Inhalt und für Änderungen an bestehendem Inhalt.

Wenn Sie über den Preview-Client verfügen, können Sie auch schnell vorhandene Dateien aus dem Datei-Explorer klassifizieren (und optional schützen). 

## <a name="can-i-use-azure-information-protection-for-classification-only-without-enforcing-encryption-and-restricting-usage-rights"></a>Kann ich Azure Information Protection nur für die Klassifizierung verwenden, ohne die Verschlüsselung und die Einschränkung von Nutzungsrechten zu erzwingen?

Ja. Sie können eine Azure Information Protection-Richtlinie konfigurieren, die nur die Klassifizierung ohne Schutz anwendet, wenn der Dateityp diese Aktion unterstützt. Wir erwarten sogar, dass dies bei Bereitstellungsnetzwerken, in denen nur ein Teil der Dokumente oder E-Mails geschützt werden müssen, die eine besondere Datenverwaltung erfordern, mehrheitlich der Fall sein wird.

## <a name="how-does-automatic-classification-work"></a>Wie funktioniert die automatische Klassifizierung?

Im Azure-Portal können Sie vordefinierte Muster wie z.B. „Kreditkartennummern“ oder „US-Sozialversicherungsnummer“ verwenden. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren.

Ein Beispiel hierzu finden Sie unter [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection). 

Die Genauigkeit der Klassifizierung hängt davon ab, wie Sie die Klassifizierungsregel konfigurieren, die auf Bedingungen basiert. Derzeit unterstützen Bedingungen Textmuster und reguläre Ausdrücke. Eine Erläuterung der einzelnen Optionen, die während der Vorschauphase verfügbar sind, sowie eine Reihe von Beispielen, die Sie testen können, finden Sie unter [Konfigurieren von Bedingungen für die automatische und empfohlene Klassifizierung für Azure Information Protection](../deploy-use/configure-policy-classification.md). Die Erkennung wird ausgeführt, wenn das Dokument gespeichert wird oder eine E-Mail gesendet wird.

Es wird empfohlen, dass Sie zunächst mit benutzerempfohlenen Aktionen beginnen, anstatt vollautomatische Aktionen anzuwenden, um eine bestmögliche Benutzererfahrung und die Geschäftskontinuität zu gewährleisten. Dadurch haben Ihre Benutzer die Möglichkeit, die Bezeichnungs- oder Schutzaktion zu akzeptieren oder diese Vorschläge außer Kraft zu setzen.   

## <a name="can-azure-information-protection-prompt-users-to-classify-files-themselves-rather-than-use-automatic-classification"></a>Kann Azure Information Protection Benutzer dazu auffordern, die Klassifizierung von Dateien selbst vorzunehmen, anstatt die automatische Klassifizierung zu verwenden? 

Ja. Verwenden Sie das Azure-Portal, um zu konfigurieren, ob die automatische Klassifizierung verwendet werden oder eine Empfehlung für Benutzer erfolgen soll, indem Sie die Option **Select how this label is applied: automatically or recommended to user** (Auswählen, wie diese Bezeichnung angewendet wird: automatisch oder für Benutzer empfohlen) auf **Recommended** (Empfohlen) festlegen.

Ein Beispiel hierzu finden Sie unter [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).  

## <a name="can-i-force-all-documents-to-be-classified"></a>Kann ich erzwingen, dass alle Dokumente klassifiziert werden?

Ja. Wenn Sie möchten, dass die Benutzer alle Dateien, die sie speichern, klassifizieren, legen Sie im Azure-Portal die Richtlinieneinstellung **Alle Dokumente und E-Mails müssen eine Bezeichnung aufweisen** auf **On** (Aktiviert) fest. 

## <a name="can-i-remove-classification-from-a-file"></a>Kann ich die Klassifizierung einer Datei entfernen?

Ja. Um die Klassifizierung einer Datei zu entfernen, öffnen Sie die Datei in der Office-Anwendung, klicken Sie auf das Symbol **Edit label** (Bezeichnung bearbeiten) auf der Information Protection-Leiste, klicken Sie auf das Symbol **Remove label** (Bezeichnung entfernen), und klicken Sie anschließend auf **OK**, um die Aktion zu bestätigen. 


## <a name="can-i-prompt-users-to-justify-why-they-are-changing-the-classification-level"></a>Kann ich Benutzer dazu auffordern, zu begründen, warum sie die Klassifizierungsstufe ändern?

Ja. Legen Sie im Azure-Portal die Option **Benutzer müssen eine Begründung angeben, wenn sie eine niedrigere Klassifizierungsbezeichnung verwenden, eine Bezeichnung entfernen oder den Schutz entfernen möchten** auf **Ein** fest, um sicherzustellen, dass Benutzer Änderungen an Klassifikationen begründen. Wenn sie dies tun, wird ihre Aktion und Begründung in ihrem lokalen Windows-Ereignisprotokoll protokolliert: **Anwendungs- und Dienstprotokolle** > **Microsoft Azure Information Protection**.

## <a name="how-can-i-automatically-protect-the-content-after-its-been-classified"></a>Wie kann ich den Inhalt automatisch schützen, nachdem er klassifiziert wurde?

Im Azure-Portal können Sie eine Rights Management-Vorlage auswählen, um den Inhalt automatisch entsprechend der angegebenen Klassifizierungsstufe zu schützen.

Ein Beispiel hierzu finden Sie unter [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection). Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden](../deploy-use/configure-policy-protection.md).

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet – eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Geheim** Unterbezeichnungen wie z.B. **Recht** und **Finanzen** enthalten. Sie können unterschiedliche optische Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Geheim** nicht selbst auswählen; nur eine der untergeordneten Bezeichnungen wie z.B. **Recht**. Daher wird als festgelegte Bezeichnung **Geheim\Recht** angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Geheim**, eine benutzerdefinierte Texteigenschaft für **Recht** und eine weitere mit beiden Werten (**Geheim Recht**). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen auf der übergeordneten und ihrer untergeordneten Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anlagen erhalten entweder keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Anlagen angewendet.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Wie unterscheidet sich die Azure Information Protection-Klassifizierung für E-Mails von der Exchange-Nachrichtenklassifizierung?

Die Exchange-Nachrichtenklassifizierung ist ein älteres Feature, das unabhängig von einer Azure Information Protection-Klassifizierung implementiert wird, und mit dem E-Mails klassifiziert werden können. Sie können jedoch beide Lösungen integrieren, damit die Azure Information Protection-Klassifizierung und entsprechende Bezeichnungsmarkierungen automatisch hinzugefügt werden, wenn Benutzer eine E-Mail mithilfe der Outlook Web-App und einiger mobiler E-Mail-Anwendungen klassifizieren. Exchange fügt die Klassifizierung hinzu und die Vorschauversion des Azure Information Protection-Clients wendet die entsprechenden Bezeichnungseinstellungen für diese Klassifizierung an.

Obwohl die Outlook Web-App die Azure Information Protection-Klassifizierung und den Schutz noch nicht systemintern unterstützt, können Sie diese Technik dazu verwenden, um Ihre Bezeichnungen zusätzlich zum Outlook-Desktopclient mit diesem E-Mail-Client zu nutzen.

So erreichen Sie diese Lösung 

1. Verwenden Sie das Exchange PowerShell-Cmdlet [New-MessageClassification](https://technet.microsoft.com/library/bb124400), um Nachrichtenklassifizierungen mit der Name-Eigenschaft zu erstellen, die Ihren Bezeichnungsnamen in der Azure Information Protection-Richtlinie zugeordnet wird. 

2. Erstellen Sie eine Exchange-Transportregel für jede Bezeichnung. Wenden Sie die Regel an, wenn Nachrichteneigenschaften die von Ihnen konfigurierte Klassifizierung enthalten, und ändern Sie dann die Nachrichteneigenschaften, um einen Nachrichtenheader festzulegen. 

    Für den Nachrichtenheader finden Sie die anzugebenden Informationen, indem Sie die Eigenschaften einer von Ihnen mit der Azure Information Protection-Bezeichnung klassifizierten Office-Datei untersuchen. Identifizieren Sie die Dateieigenschaft mit dem Format **MSIP_Label_<GUID>_Enabled**, und geben Sie diese Zeichenfolge für den Nachrichtenheader und dann **True** für den Headerwert an. Ihr Nachrichtenheader kann z. B. wie die folgende Zeichenfolge aussehen: **MSIP_Label_132616b8-f72d-5d1e-aec1-dfd89eb8c5b2_Enabled**.


Jetzt geschieht Folgendes, wenn Benutzer die Outlook Web Access-App oder einen Client auf einem mobilen Gerät verwenden, das den Rechteverwaltungsschutz unterstützt: 

- Benutzer wählen die Exchange-Nachrichtenklassifizierung aus, und senden die E-Mail.

- Die Exchange-Regel erkennt die Exchange-Klassifizierung und ändert entsprechend den Nachrichtenheader, um die Azure Information Protection-Klassifizierung hinzuzufügen.

- Wenn Empfänger, die die Vorschauversion des Azure Information Protection-Clients ausführen, die E-Mail in Outlook anzeigen, sehen sie, dass die Azure Information Protection-Bezeichnung sowie alle entsprechenden Kopfzeilen, Fußzeilen oder Wasserzeichen der E-Mail zugewiesen sind. 

Wenn die Azure Information Protection-Bezeichnungen einen entsprechenden Rechteverwaltungsschutz anwenden, fügen Sie diesen zur Regelkonfiguration hinzu, indem Sie die Option zum Ändern der Nachrichtensicherheit ändern, den Rechteschutz anwenden und dann die RMS-Vorlage oder die Option „Nicht weiterleiten“ auswählen.

Sie können Transportregeln auch so konfigurieren, dass sie die umgekehrte Zuordnung vornehmen: Wenn eine Azure Information Protection-Bezeichnung erkannt wird, legen Sie eine entsprechende Exchange-Nachrichtenklassifizierung fest. Dazu gehen Sie folgendermaßen vor:

- Erstellen Sie für jede Azure Information Protection-Bezeichnung eine Transportregel, die angewendet wird, wenn der Header **msip_labels** den Namen Ihrer Bezeichnung enthält (z.B. **Vertraulich**), und wenden Sie eine Nachrichtenklassifizierung an, die dieser Bezeichnung zugeordnet wird.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. In Dateien werden diese Metadaten in benutzerdefinierten Eigenschaften gespeichert. In E-Mails befinden sich diese Informationen in den E-Mail-Kopfzeilen.

## <a name="how-does-document-tracking-and-revocation-work-for-azure-information-protection"></a>Wie funktionieren die Dokumentkontrolle und die Sperrungsarbeit für Azure Information Protection?

Die Dokumentkontrolle für Dateien, die Sie mithilfe von Azure Information Protection klassifizieren und schützen, arbeitet mit Azure Rights Management und der RMS-Freigabeanwendung zusammen. Sie können auf die Website für die Dokumentnachverfolgung auch mit dem Azure Information Protection-Client zugreifen (Version 1.0.233 oder höher): 

- Klicken Sie in einer Office-Anwendung auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**  >  **Verwendung nachverfolgen**. 

Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](../rms-client/sharing-app-track-revoke.md).

## <a name="can-i-control-which-users-can-use-azure-information-protection-to-classify-and-protect-content"></a>Kann ich steuern, welche Benutzer Azure Information Protection zum Klassifizieren und Schützen von Inhalten verwenden können?

Sie können einschränken, welche Benutzer Daten klassifizieren und schützen, indem Sie die Verteilung des Azure Information Protection-Client steuern. Sie fügen beim Konfigurieren einer [bereichsbezogenen Richtlinie](../deploy-use\configure-policy-scope.md) lediglich für die angegebenen Benutzer neue Bezeichnungen hinzu. 

Dateien und E-Mails, die von Azure Information Protection klassifiziert werden, können von jedem Benutzer genutzt oder bearbeitet werden, unabhängig davon, ob der Azure Information Protection-Client installiert ist oder nicht. 

## <a name="how-do-i-sign-in-as-a-different-user"></a>Wie kann ich mich als anderer Benutzer anmelden?

Bei Verwendung des Azure Information Protection-Clients müssen Sie sich in einer Produktionsumgebung in der Regel nicht als anderer Benutzer anmelden. Dies kann jedoch der Fall sein, wenn Sie über mehrere Mandanten verfügen. Dies gilt z.B., wenn Ihre Organisation zusätzlich zu einem Office 365- oder einem Azure-Mandanten auch einen Testmandanten verwendet.

Sie können mithilfe des Dialogfelds **Microsoft Azure Information Protection** überprüfen, mit welchem Konto Sie gerade angemeldet sind: Öffnen Sie dazu eine Office-Anwendung, und klicken Sie auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**, und klicken Sie dann auf **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie – insbesondere bei Nutzung eines Administratorkontos – den angezeigten Domänennamen des angemeldeten Kontos. Beispiel: Wenn Sie ein Administratorkonto für zwei verschiedene Mandanten haben, kann leicht übersehen werden, dass Sie zwar mit dem richtigen Kontonamen, aber mit der falschen Domäne angemeldet sind. Ein Hinweis darauf können Fehler beim Herunterladen der Azure Information Protection-Richtlinie, die fehlende Anzeige erwarteter Bezeichnungen oder unerwartete Verhaltensweisen sein.

Um sich als anderer Benutzer anzumelden, müssen Sie derzeit die Registrierung bearbeiten:

1. Navigieren Sie in einem Registrierungs-Editor zu **HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP**, und löschen Sie den **TokenCache**-Schlüssel.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn in Ihrer Office-Anwendung keine Eingabeaufforderung für die Anmeldung beim Azure Information Protection-Dienst angezeigt wird, kehren Sie zum Dialogfeld **Microsoft Azure Information Protection** zurück, und klicken Sie im aktualisierten Abschnitt **Clientstatus** auf **Anmelden**.

Darüber hinaus gilt:

- Um die Umgebung für den Azure Rights Management-Dienst (auch bekannt als Bootstrapping) erneut zu initialisieren, verwenden Sie die Option **Zurücksetzen** im [RMS Analyzer Tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437).

- Um die gerade heruntergeladene Azure Information Protection-Richtlinie wieder zu entfernen, löschen Sie die Datei **Policy.msip** aus dem Ordner „%localappdata%\Microsoft\MSIP“.

## <a name="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection"></a>Wie kann ich ein Problem melden oder Feedback zu Azure Information Protection übermitteln?

Wenn Sie ein Problem mit Azure Information Protection haben und die aktuelle Version des Clients verwenden: Klicken Sie in der Office-Anwendung auf der Registerkarte **Start** im Bereich **Schutz** auf **Schützen** und dann auf **Hilfe und Feedback**. Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **Send feedback** (Feedback senden). Dadurch senden Sie eine E-Mail an das Information Protection-Team, wobei automatisch Protokolldateien von Ihrem PC angehängt werden, die dabei helfen sollen, das Problem zu diagnostizieren. 

Wenn Sie Fragen oder Feedback haben, verwenden Sie die Yammer-Seite [Azure Information Protection](https://www.yammer.com/askipteam/). 


<!--HONumber=Dec16_HO2-->

