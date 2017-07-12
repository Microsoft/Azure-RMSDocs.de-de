---
title: "Häufig gestellte Fragen zu Azure Information Protection"
description: "Hier finden Sie einige häufig gestellte Fragen zu Azure Information Protection und dem zugehörigen Dienst zum Schutz von Daten, Azure Rights Management (Azure RMS)."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/15/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: cbceb3f3e68c558576cc275793dac6feb3b9245b
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="frequently-asked-questions-for-azure-information-protection" class="xliff"></a>

# Häufig gestellte Fragen zu Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Haben Sie eine Frage zu Azure Information Protection oder zum Azure Rights Management-Dienst (Azure RMS)? Vielleicht finden Sie hier eine Antwort darauf.

Diese Seiten mit häufig gestellten Fragen werden regelmäßig aktualisiert. Dabei werden die neuen Beiträge in den Ankündigungen zu den monatlichen Dokumentationsupdates im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) (Informationen in englischer Sprache zu Enterprise Mobility und Sicherheit) aufgelistet.

<a id="whats-the-difference-between-azure-information-protection-and-azure-rights-management" class="xliff"></a>

## Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?

Azure Information Protection stellt Klassifizierungen, Bezeichnungen und den Schutz für Dokumente und E-Mails einer Organisation bereit. Die Schutztechnologie nutzt den Azure Rights Management-Dienst, der nun eine Komponente von Azure Information Protection ist.

<a id="what-is-the-role-of-identity-management-for-azure-information-protection" class="xliff"></a>

## Welche Rolle spielt das Identitätsmanagement für Azure Information Protection?

Benutzer benötigen einen gültigen Benutzernamen und ein Kennwort, um auf durch Azure Information Protection geschützte Inhalte zuzugreifen. Weitere Informationen zum Schutz Ihrer Daten mit Azure Information Protection finden Sie unter [Die Rolle von Azure Information Protection beim Schützen von Daten](/enterprise-mobility-security/solutions/azure-information-protection-securing-data). 

<a id="what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included" class="xliff"></a>

## Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?
Informationen dazu finden Sie in den [Abonnementinformationen](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) und der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website. 

Wenn Sie über ein Office 365-Abonnement verfügen, das Rights Management umfasst, laden Sie das [Datenblatt zur Azure Information Protection-Lizenz](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) von der Seite **Features** herunter.

<a id="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling" class="xliff"></a>

## Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein. Zwar wird bei den meisten Präsentationen und Demos zum Azure Information Protection-Client gezeigt, wie dieser Klassifizierungen und Bezeichnungen unterstützt, Sie können den Client aber auch in Abonnements verwenden, die zum Datenschutz lediglich den Azure Rights Management-Dienst enthalten.

Wenn der Azure Information Protection-Client für Windows installiert ist, aber keine Azure Information Protection-Richtlinie vorhanden ist, wird der Client automatisch im [reinen Schutzmodus](../rms-client/client-protection-only-mode.md) betrieben. In diesem Modus können Benutzer problemlos Rights Management-Vorlagen und benutzerdefinierte Berechtigungen anwenden. Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.

Wenn Sie zurzeit die Rights Management-Freigabeanwendung für Windows verwenden, empfehlen wir, diese durch den Azure Information Protection-Client zu ersetzen. Die Unterstützung für die Freigabeanwendung endet am 31. Januar 2018. Informationen zum Übergang finden Sie unter [Üblicherweise mit der RMS-Freigabeanwendung ausgeführte Aufgaben](../rms-client/upgrade-client-app.md).

<a id="does-azure-information-protection-support-on-premises-and-hybrid-scenarios" class="xliff"></a>

## Unterstützt Azure Information Protection lokale und hybride Szenarios?

Ja. Obwohl Azure Information Protection eine cloudbasierte Lösung ist, können damit Dokumente und E-Mails, die sowohl lokal als auch in der Cloud gespeichert sind, klassifiziert, bezeichnet und geschützt werden.

Wenn Sie über Exchange Server, SharePoint Server und Windows-Dateiserver verfügen, können Sie den [Rights Management-Connector](../deploy-use/deploy-rms-connector.md) bereitstellen, damit diese lokalen Server den Azure Rights Management-Dienst verwenden können, um Ihre E-Mails und Dokumente zu schützen. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine übergangslosere Authentifizierungshandhabung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)verwenden.

Der Azure Rights Management-Dienst generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf und verwendet daher keine lokale PKI. Weitere Informationen zur Verwendung von Zertifikaten in Azure Rights Management finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsnutzung](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) des Artikels [Funktionsweise von Azure RMS](../understand-explore/how-does-it-work.md).

<a id="ive-heard-a-new-release-is-going-to-be-available-soon-for-azure-information-protectionwhen-will-it-be-released" class="xliff"></a>

## Ich habe gehört, dass bald eine neue Version von Azure Information Protection verfügbar sein wird. Wann wird diese veröffentlicht?

Die technische Dokumentation enthält keine Informationen zu bevorstehenden Releases. Lesen Sie für solche Informationen den [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-information-protection,azure-rights-management-services) und die neuesten Updates von [Dan Plastina@TheRMSGuy](https://twitter.com/TheRMSGuy) auf Twitter. Wenn Sie an einem Office-Release interessiert sind, lesen Sie auch den [Office Blog](https://blogs.office.com/).

<a id="where-can-i-find-supporting-information-for-azure-information-protectionsuch-as-legal-compliance-and-slas" class="xliff"></a>

## Wo finde ich weitere Informationen zu Azure Information Protection – z.B. rechtliche Hinweise, Informationen zur Compliance und SLAs?

Lesen Sie hierzu [Kompatibilitätsinformationen und ergänzende Informationen zu Azure Information Protection](../understand-explore/compliance.md).

<a id="how-can-i-report-a-problem-or-send-feedback-for-azure-information-protection" class="xliff"></a>

## Wie kann ich ein Problem melden oder Feedback zu Azure Information Protection übermitteln?

Wenden Sie sich an Ihre Standardsupportkanäle oder an den [Microsoft Support](information-support.md#to-contact-microsoft-support), um technischen Support zu erhalten.

Feedback in Form von Verbesserungsvorschlägen oder neuen Features: Klicken Sie in der Office-Anwendung auf der Registerkarte **Start** in der Gruppe **Protection** (Schutz) auf **Protect** (Schützen), und anschließend auf **Help and Feedback** (Hilfe und Feedback). Klicken Sie im Dialogfeld **Microsoft Azure Information Protection** auf **Send Us Feedback** (Feedback senden). Dadurch wird eine E-Mail-Nachricht an das Information Protection-Team geöffnet. Wir laden Sie auch dazu ein, sich mit unserem Engineering-Team auf seiner [Yammer-Website zu Azure Information Protection](https://www.yammer.com/askipteam/) in Verbindung zu setzen. 

<a id="what-do-i-do-if-my-question-isnt-here" class="xliff"></a>

## Wie gehe ich vor, wenn meine Frage hier nicht behandelt wird?

Prüfen Sie zunächst die häufig gestellten Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen oder speziell auf den Schutz von Daten beziehen. Der Azure Rights Management-Dienst (Azure RMS) stellt die Technologie zum Schutz von Daten für Azure Information Protection bereit. Azure RMS kann mit und ohne Klassifizierungen und Bezeichnungen verwendet werden: 

- [Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen](faqs-infoprotect.md)

- [Häufig gestellte Fragen zum Schutz von Daten](faqs-rms.md)

Wenn Ihre Frage hier nicht beantwortet wird, verwenden Sie die Links und Ressourcen, die unter [Informationen zu und Unterstützung von Azure Information Protection](information-support.md) aufgelistet sind.

Darüber hinaus gibt es häufig gestellte Fragen (FAQs) für Endbenutzer:

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](../rms-client/mobile-app-faq.md)

- [Häufig gestellte Fragen zur RMS-Freigabeanwendung für Macintosh-Computer und Windows Phone](https://technet.microsoft.com/dn451248)

- [Häufig gestellte Fragen zur Rights Management-Freigabeanwendung für Windows](https://technet.microsoft.com/dn467883)


[!INCLUDE[Commenting house rules](../includes/houserules.md)]

