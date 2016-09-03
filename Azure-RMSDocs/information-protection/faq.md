---
title: "Häufig gestellte Fragen zur Vorschau von Azure Information Protection | Azure Information Protection"
description: Haben Sie eine Frage zum Vorschaurelease von Azure Information Protection? Vielleicht finden Sie hier eine Antwort darauf.
author: cabailey
manager: mbaldwin
ms.date: 08/22/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: c9f9211e7c1dcf293caf81475515114b5433d6a7
ms.openlocfilehash: 55d56786150d38b36ae8185c4a7ac4c8a5c51ba4


---

# Häufig gestellte Fragen zur Vorschau von Azure Information Protection

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Haben Sie eine Frage zum Vorschaurelease von Azure Information Protection?  Vielleicht finden Sie hier eine Antwort darauf. 

Sie können damit rechnen, dass diese Liste stetig aktualisiert wird, da einige Informationen in die Hauptdokumentation verschoben werden und wir neue Fragen einschließen, die wir von Kunden erhalten. 

## Was kann ich mit dem Vorschaurelease von Azure Information Protection machen, und was sind die aktuellen Einschränkungen?

Dieses Vorschaurelease fügt Microsoft Office-Anwendungen eine Information Protection-Leiste hinzu, mit der Sie zugewiesene Klassifizierungsbezeichnungen zu Daten anzeigen und ändern können. Die Klassifizierung kann manuell erfolgen oder, was empfohlen wird, automatisch angewendet werden. Für die Klassifizierungen, die Sie angeben, können Daten mithilfe einer Vorlage von Azure Rights Management geschützt werden.  

Die Klassifizierungsbezeichnungen und das -verhalten werden im Azure-Portal konfiguriert. Sie können die integrierten Standardrichtlinien verwenden, um Azure Information Protection sehr schnell auszuwerten, oder Sie können Ihre eigenen Richtlinien vollständig anpassen. Sie können die Farben, Namen und die Reihenfolge der Klassifizierungsbezeichnungen ändern, die Benutzern angezeigt werden. Sie können auch QuickInfos und optische Klassifizierungskennzeichnungen, wie z.B. Kopf-, Fußzeile oder ein Wasserzeichen konfigurieren.

Probieren Sie unser Schnellstart-Tutorial aus, um zu sehen, wie dies innerhalb weniger Minuten funktioniert: [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).

Beachten Sie, dass Sie in der Vorschau den neuen **Premium P2-Serviceplan** ausprobieren können und dass einige erweiterte Funktionen, wie z.B. die automatische und empfohlene Bezeichnung, in Ihrem aktuellen Plan bei allgemeiner Verfügbarkeit möglicherweise nicht verfügbar sind. Informationen zu den verschiedenen Serviceplänen (Azure Information Protection Premium P1 und Azure Information Protection Premium P2) finden Sie im folgenden Blogbeitrag: [Introducing Enterprise Mobility + Security](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/07/introducing-enterprise-mobility-security/) (Einführung in Enterprise Mobility und Security).

Dieses Vorschaurelease unterliegt den folgenden Einschränkungen. Achten Sie auf Ankündigungen im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) (Informationen in englischer Sprache zu Enterprise Mobility und Security) und auf unserer [Yammer-Seite](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), um zu erfahren, wann zusätzliche Features und Funktionen verfügbar sind:

- Es gibt keine zentrale Protokollierung für die Klassifizierung und die Bezeichnung.

- Bezeichnungsnamen und QuickInfos werden nur in einer Sprache unterstützt.

- Bedingungen für die automatische Klassifizierung müssen Ausdrücke oder Muster sein.

- Dateien können nicht vom Windows-Datei-Explorer aus klassifiziert werden.

- Office-Apps für mobile Geräte (iOS und Android) und Mac-Computer und die Office Web Apps (Office Online) werden nicht unterstützt.

- Keine Integration mit Exchange Online oder SharePoint Online.

- Das SDK für Partner und Entwickler ist nicht verfügbar.

## Welches Abonnement brauche ich, um Azure Information Protection auszuprobieren?

Für die Vorschauversion können Sie ein beliebiges Office 365-Abonnement verwenden, das den Schutz von Office-Dokumenten und E-Mails mithilfe von Azure Rights Management umfasst. Azure Information Protection ist in allen Regionen verfügbar. Weitere Informationen zu den verfügbaren Abonnements und Links zu kostenlosen Testversionen finden Sie im Abschnitt [Office 365-Abonnement](../get-started/requirements-subscriptions.md#office-365-subscription) in der Dokumentation zu den Azure RMS-Anforderungen.

Sie müssen über ein Azure-Abonnement verfügen, um die Azure Information Protection-Richtlinien im Azure-Portal zu konfigurieren. Falls Sie noch kein Azure-Abonnement für Ihre Organisation besitzen, können Sie sich für eine kostenlose Testversion anmelden: Folgen Sie den Anweisungen auf der [Seite für die ersten Schritten mit Azure](https://account.windowsazure.com/organization).

Alle Änderungen an den Abonnementanforderungen werden im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection) angekündigt (Informationen in englischer Sprache zu Enterprise Mobility und Security).

## Muss ich über globale Administratorrechte verfügen, um die Vorschau von Azure Information Protection ausprobieren zu können?

Nur beim Preview-Release können alle Benutzer, die von Azure authentifiziert sind, die Azure Information Protection-Richtlinie Ihres Mandanten für die Klassifizierung und Bezeichnung im Azure-Portal sehen und konfigurieren. Sie müssen als globaler Administrator für Azure Active Directory angemeldet sein, um eine Bezeichnung so konfigurieren zu können, dass sie eine Azure Rights Management-Vorlage anwendet.

Wenn Sie die Option zum Installieren der Demorichtlinie bei der Installation des [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) auswählen, müssen Sie sich nicht einmal beim Portal anmelden, um die Vorschau auszuprobieren. Die Demorichtlinie installiert lokal die Standardrichtlinie für Azure Information Protection. Sie können daher versuchen, Dokumente und E-Mails zu bezeichnen. Sie werden jedoch nicht in der Lage sein, neue Bezeichnungen zu ändern oder hinzuzufügen, ohne sich beim Azure-Portal anzumelden. 

Wenn Sie die Dokumente und E-Mails schützen möchten, die Sie klassifizieren und bezeichnen, und Sie Azure Rights Management noch nicht aktiviert haben, benötigen Sie für den Aktivierungsprozess besondere Administratorrechte. Weitere Informationen finden Sie unter [Werden zum Konfigurieren von Azure RMS globale Administratorrechte benötigt, oder kann ich diese Aufgabe an andere Administratoren delegieren?](../get-started/faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators)


## Unterstützt Azure Information Protection lokale und hybride Szenarios?

Azure Information Protection ist eine cloudbasierte Lösung. Wenn Sie Interesse an der Bereitstellung von Azure Information Protection für ein hybrides Szenario haben, wenden Sie sich an das Information Protection-Team, indem Sie eine E-Mail an askipteam@microsoft.com senden.

## Welche Clientplattformen und -anwendungen werden von Azure Information Protection unterstützt?

Dies ist jetzt dokumentiert und wird unter [Requirements for Azure Information Protection](requirements-azure-infoprotect.md) (Anforderungen für Azure Information Protection) aktualisiert.


## Wie erhalten Computer die Richtlinieninformationen von Azure Information Protection, und wie oft werden diese aktualisiert?

Jedes Mal, wenn ein Benutzer eine Office-Anwendung öffnet, überprüft der Azure Information Protection-Client, ob eine höhere Version der Azure Information Protection-Richtlinie verfügbar ist. Wenn eine höhere Version verfügbar ist, lädt der Client sie herunter, wobei er einen HTTPS-Link verwendet, um die Daten zu sichern. 

Wenn bei der Veröffentlichung einer neuen Azure Information Protection-Richtlinie mehrere Instanzen der Office-Anwendung geladen sind, müssen Sie alle Instanzen schließen, um die aktuelle Version der Richtlinie abzurufen. Beispiel: Sie haben zwei Word-Dokumente geöffnet, möchten die aktualisierte Azure Information Protection-Richtlinie jedoch nur in einem Dokument testen: Schließen Sie beide Word-Dokumente, und öffnen Sie das Dokument erneut, das mit der aktuellen Richtlinie verwendet werden soll.

## Wo können Dateien gespeichert werden, um Azure Information Protection zu verwenden? 

Da Azure Information Protection persistente Bezeichnungen und persistenten Schutz für Dateien und E-Mails anwendet, ist es egal, wo die Dateien gespeichert werden.

## Kann ich nur neue Daten klassifizieren, oder kann ich auch vorhandene Daten klassifizieren?

Aktionen der Azure Information Protection-Richtlinie werden wirksam, wenn Dokumente gespeichert und E-Mails versendet werden. Dies gilt für neuen Inhalt und für Änderungen an bestehendem Inhalt. 

Wenn Sie die Dateien, die Sie klassifizieren möchten, gespeichert haben, öffnen Sie diese einfach in der Office-Anwendung, und speichern Sie sie. 

Aktuell können Sie die Klassifizierung nicht für mehrere Dokumente auf einmal überprüfen und anwenden. Sie müssen jedes Dokument einzeln in der Office-Anwendung öffnen und speichern. 

## Kann ich Azure Information Protection nur für die Klassifizierung verwenden, ohne die Verschlüsselung und die Einschränkung von Nutzungsrechten zu erzwingen?

Ja. Sie können eine Azure Information Protection-Richtlinie konfigurieren, die nur eine Bezeichnung anwendet. Wir erwarten sogar, dass dies bei Bereitstellungsnetzwerken, in denen nur ein Teil der Dokumente oder E-Mails geschützt werden müssen, die eine besondere Datenverwaltung erfordern, mehrheitlich der Fall sein wird.

## Wie funktioniert die automatische Klassifizierung?

Im Azure-Portal können Sie vordefinierte Muster wie z.B. „Kreditkartennummern“ oder „US-Sozialversicherungsnummer“ verwenden. Oder Sie können eine benutzerdefinierte Zeichenfolge oder ein benutzerdefiniertes Muster als Bedingung für die automatische Klassifizierung definieren.

Ein Beispiel hierzu finden Sie unter [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection). 

Die Genauigkeit der Klassifizierung hängt davon ab, wie Sie die Klassifizierungsregel konfigurieren, die auf Bedingungen basiert. Derzeit unterstützen Bedingungen Textmuster und reguläre Ausdrücke. Eine Erläuterung der einzelnen Optionen, die während der Vorschauphase verfügbar sind, sowie eine Reihe von Beispielen, die Sie testen können, finden Sie unter [Konfigurieren von Bedingungen für die automatische und empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md). Die Erkennung wird ausgeführt, wenn das Dokument gespeichert wird oder eine E-Mail gesendet wird.

Es wird empfohlen, dass Sie zunächst mit benutzerempfohlenen Aktionen beginnen, anstatt vollautomatische Aktionen anzuwenden, um eine bestmögliche Benutzererfahrung und die Geschäftskontinuität zu gewährleisten. Dadurch haben Ihre Benutzer die Möglichkeit, die Bezeichnungs- oder Schutzaktion zu akzeptieren oder diese Vorschläge außer Kraft zu setzen.   

## Kann Azure Information Protection Benutzer dazu auffordern, die Klassifizierung von Dateien selbst vorzunehmen, anstatt die automatische Klassifizierung zu verwenden? 

Ja. Verwenden Sie das Azure-Portal, um zu konfigurieren, ob die automatische Klassifizierung verwendet werden oder eine Empfehlung für Benutzer erfolgen soll, indem Sie die Option **Select how this label is applied: automatically or recommended to user** (Auswählen, wie diese Bezeichnung angewendet wird: automatisch oder für Benutzer empfohlen) auf **Recommended** (Empfohlen) festlegen.

Ein Beispiel hierzu finden Sie unter [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).  

## Kann ich erzwingen, dass alle Dokumente klassifiziert werden?

Ja. Wenn Sie möchten, dass die Benutzer alle Dateien, die sie speichern, klassifizieren, legen Sie im Azure-Portal die Einstellung **All documents and emails must have a label** (Alle Dokumente und E-Mails müssen eine Bezeichnung haben) auf **On** (Aktiviert) fest. 

## Kann ich die Klassifizierung einer Datei entfernen?

Ja. Um die Klassifizierung einer Datei zu entfernen, öffnen Sie die Datei in der Office-Anwendung, klicken Sie auf das Symbol **Edit label** (Bezeichnung bearbeiten) auf der Information Protection-Leiste, klicken Sie auf das Symbol **Remove label** (Bezeichnung entfernen), und klicken Sie anschließend auf **OK**, um die Aktion zu bestätigen. 


## Kann ich Benutzer dazu auffordern, zu begründen, warum sie die Klassifizierungsstufe ändern?

Ja. Legen Sie im Azure-Portal die Option **Users must provide justification when lowering the sensitivity level** (Benutzer müssen eine Begründung bereitstellen, wenn sie die Vertraulichkeitsstufe herabsetzen) auf **On** (Aktiviert) fest, um sicherzustellen, dass Benutzer die Änderung der Klassifizierung begründen. Wenn sie dies tun, wird ihre Aktion und Begründung in ihrem lokalen Windows-Ereignisprotokoll protokolliert: **Anwendung** > **Microsoft Azure Information Protection**.

## Wie kann ich den Inhalt automatisch schützen, nachdem er klassifiziert wurde?

Im Azure-Portal können Sie eine Azure Rights Management-Vorlage auswählen, um den Inhalt automatisch entsprechend der angegebenen Klassifizierungsstufe zu schützen.

Ein Beispiel hierzu finden Sie unter [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection). Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden](configure-policy-protection.md).

## Kann eine Datei mit zwei verschiedenen Klassifizierungen klassifiziert werden?

Falls erforderlich, können Sie Unterbezeichnungen erstellen, um die Unterkategorien für eine bestimmte Vertraulichkeitsbezeichnung besser zu beschreiben. Beispielsweise könnte die Hauptbezeichnung **Geheim** Unterbezeichnungen wie z.B. **Geheim – Recht** und **Geheim – Finanzen** enthalten. Sie können dann unterschiedliche optische Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf verschiedene Unterbezeichnungen anwenden.

Obwohl Sie aktuell optische Kennzeichnungen, den Schutz und die Bedingungen auf beiden Ebenen festlegen können, konfigurieren Sie diese Einstellungen, wenn Sie Unterebenen verwenden, nur auf der Unterebene. Wenn Sie die gleichen Einstellungen auf einer übergeordneten und ihrer untergeordneten Ebene konfigurieren, haben die Einstellungen der untergeordneten Ebene Vorrang.

## Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. In Dateien werden diese Metadaten in benutzerdefinierten Eigenschaften gespeichert. In E-Mails befinden sich diese Informationen in den E-Mail-Kopfzeilen.

## Wie funktionieren die Dokumentkontrolle und die Sperrungsarbeit für Azure Information Protection?

Die Dokumentkontrolle für Dateien, die Sie mithilfe von Azure Information Protection klassifizieren und schützen, funktioniert genauso wie bei Azure Rights Management und der RMS-Freigabeanwendung. Sie können auf die Website für die Dokumentnachverfolgung auch mit dem Azure Information Protection-Client zugreifen (Version 1.0.233 oder höher): 

- Klicken Sie in einer Office-Anwendung auf der Registerkarte **Start** in der Gruppe **Schutz** auf **Schützen**  >  **Verwendung nachverfolgen**. 

Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](../rms-client/sharing-app-track-revoke.md).

## Wie erzwingt Azure Information Protection die Richtlinien, die ich konfiguriere?

Wenn ein Dokument mithilfe einer Azure Rights Management-Vorlage geschützt ist, wird der Benutzer zunächst authentifiziert, um sicherzustellen, dass er die Berechtigung für das Dokument hat. Anschließend wird die Richtlinie zu Nutzungsrechten von der Anwendung erzwungen. 

## Wie wird Azure Active Directory von Azure Information Protection verwendet?

Azure Information Protection verwendet Azure Active Directory für die Benutzerauthentifizierung.

## Kann ich steuern, welche Benutzer Azure Information Protection zum Klassifizieren und Schützen von Inhalten verwenden können?

Sie können einschränken, welche Benutzer Daten klassifizieren und schützen, indem Sie die Verteilung des Azure Information Protection-Client steuern. 

Dateien und E-Mails, die von Azure Information Protection klassifiziert werden, können von jedem Benutzer genutzt oder bearbeitet werden, unabhängig davon, ob der Azure Information Protection-Client installiert ist oder nicht. 

## Wie kann ich ein Problem melden oder ein Feedback für diese Vorschau senden?

Wenn Sie bei der Verwendung dieses Vorschaurelease auf ein Problem stoßen, klicken Sie in der Office-Anwendung auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen), und anschließend auf **Help and Feedback** (Hilfe und Feedback). Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **Send feedback** (Feedback senden). Dadurch senden Sie eine E-Mail an das Information Protection-Team, wobei automatisch Protokolldateien von Ihrem PC angehängt werden, die dabei helfen sollen, das Problem zu diagnostizieren. 

Wenn Sie Fragen oder Feedback haben, verwenden Sie die Yammer-Seite [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all). 

## Wie gehe ich vor, wenn meine Frage hier nicht behandelt wird?

Überprüfen Sie zunächst, ob Ihre Frage nicht in der [Azure Information Protection-Preview-Ankündigung](https://blogs.technet.microsoft.com/enterprisemobility/2016/07/12/azure-information-protection-public-preview-available-now/) auf dem Enterprise Mobility and Security Blog (Informationen in englischer Sprache zu Enterprise Mobility und Security) enthalten ist.

Besuchen Sie anschließend unsere [Yammer-Seite](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), um nachzusehen, ob schon jemand anderes die gleiche Frage gestellt hat. Wenn dies nicht der Fall ist, stellen Sie dort Ihre Frage.







<!--HONumber=Aug16_HO4-->


