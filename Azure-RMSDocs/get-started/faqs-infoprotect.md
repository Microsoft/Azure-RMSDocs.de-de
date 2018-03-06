---
title: "Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen – AIP"
description: Haben Sie Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen bei Azure Information Protection beziehen? Vielleicht finden Sie hier eine Antwort darauf.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/22/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: d3f82cde42985bb837fe47f7d01d7180462bccd3
ms.sourcegitcommit: 23d98a405057d61a737313c8dfef042996131d3e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2018
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort darauf. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Was kann ich mit den Klassifizierungsfunktionen in Azure Information Protection tun?

Probieren Sie unser Schnellstart-Tutorial aus, um zu sehen, wie dies innerhalb weniger Minuten funktioniert: [Quick start tutorial for Azure Information Protection](infoprotect-quick-start-tutorial.md) (Schnellstart-Tutorial für Azure Information Protection).

Achten Sie auf Ankündigungen im [Enterprise Mobility and Security Blog](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-information-protection) (Informationen in englischer Sprache zu Enterprise Mobility und Security) und auf unserer [Yammer-Seite](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), um zu erfahren, wann zusätzliche Klassifizierungsfeatures und -funktionen verfügbar sind: Die aktuelle Version hat einige Einschränkungen, einschließlich der Folgenden:

- Es gibt keine zentrale Protokollierung für die Klassifizierung und die Bezeichnung.

- Keine Bezeichnungsmöglichkeit in Office-Apps für mobile Geräte (iOS und Android) und Mac-Computer oder für die Office Web Apps (Office Online).

- Keine Klassifizierungs- und Bezeichnungsintegration mit Exchange Online oder SharePoint Online.

Anfordern neuer Features und Abstimmen für Anforderungen durch Besuchen der [User Voice-Website](https://msip.uservoice.com/) für Azure Information Protection.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>Muss ich ein globaler Administrator sein, um Klassifizierungen und Bezeichnungen zu konfigurieren?

Mit der neu eingeführten Administratorrolle von Information Protection wurde diese Frage auf der Hauptseite für FAQs beantwortet: [Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

Wenn Sie die Option zum Installieren der Demorichtlinie bei der Installation des [Azure Information Protection-Clients](https://www.microsoft.com/en-us/download/details.aspx?id=53018) auswählen, müssen Sie sich nicht beim Portal anmelden, um die Bezeichnungsfunktion testen zu können. Die Demorichtlinie installiert lokal eine Standardrichtlinie für Azure Information Protection, damit Sie das Bezeichnen von Dokumenten und E-Mails ausprobieren können. Sie können neue Bezeichnungen jedoch nicht ändern oder hinzufügen, ohne sich beim Azure-Portal anzumelden. 

## <a name="which-options-in-the-azure-portal-are-p2"></a>Welche Optionen im Azure-Portal sind P2?

Die Optionen im Azure-Portal, die ein **Azure Information Protection Premium 2**(P2)-Abonnement erfordern, werden nun zur Identifizierung mit einer Informationspopupmeldung angezeigt. Weitere Informationen darüber, welche Funktionen in P1- und P2-Abonnements enthalten sind, finden Sie in der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website.

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet: eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Vertraulich** Unterbezeichnungen wie z.B. **Legal** (Recht) und **Finance** (Finanzen) enthalten. Sie können unterschiedliche visuelle Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Vertraulich** nicht selbst auswählen, sondern nur eine der untergeordneten Bezeichnungen, z.B. **Legal** (Recht). Daher wird als festgelegte Bezeichnung **Confidential \ Legal** (Vertraulich\Recht) angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Confidential** (Vertraulich), eine benutzerdefinierte Texteigenschaft für **Legal** (Recht) und eine weitere mit beiden Werten (**Confidential Legal** (Vertraulich Recht)). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen für die übergeordnete und deren untergeordnete Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Wie hindere ich jemanden daran, eine Bezeichnung zu entfernen oder zu ändern?

Es gibt zwar eine [Richtlinieneinstellung](../deploy-use/configure-policy-settings.md), für die Benutzer angeben müssen, warum sie die Klassifizierungsbezeichnung senken oder den Schutz entfernen, jedoch verhindert dieses Einstellung diese Aktionen nicht. Um Benutzer daran zu hindern, eine Bezeichnung zu entfernen oder zu ändern, muss der Inhalt bereits geschützt sein. Die Schutzberechtigungen erteilen dem Benutzer nicht das [Nutzungsrecht](../deploy-use/configure-usage-rights.md) „Exportieren“ oder „Vollzugriff“. 

# <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anhänge erhalten keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Anlagen angewendet.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. 

- Für Word-Dokumente (DOC and DOCX), Excel-Tabellen (XLS and XLSX), PowerPoint-Präsentationen (PPT und PPTX) und PDF-Dokumente (PDF) werden diese Metadaten in der folgenden benutzerdefinierten Eigenschaft gespeichert: **MSIP_Label_\<GUID>_Enabled=True**.  

- In E-Mails werden diese Informationen im X-Header gespeichert: **msip_labels: MSIP_Label_\<GUID>_Enabled=True;**.  

Suchen Sie nach dem Wert der Bezeichnungs-ID auf dem Blatt „Bezeichnung“, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal abrufen oder konfigurieren, um die GUID für eine Bezeichnung zu ermitteln. Bei Dateien, auf die Bezeichnungen angewendet wurden, können Sie auch das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) ausführen, um die GUID (MainLabelId oder SubLabelId) zu identifizieren. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, geben Sie immer die GUID einer untergeordneten Bezeichnung an, nicht die der übergeordneten Bezeichnung.

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Wie unterscheidet sich die Azure Information Protection-Klassifizierung für E-Mails von der Exchange-Nachrichtenklassifizierung?

Die Exchange-Nachrichtenklassifizierung ist ein älteres Feature, das unabhängig von einer Azure Information Protection-Klassifizierung implementiert wird, und mit dem E-Mails klassifiziert werden können. 

Sie können jedoch beide Lösungen integrieren, damit die Azure Information Protection-Klassifizierung und entsprechende Bezeichnungsmarkierungen automatisch hinzugefügt werden, wenn Benutzer eine E-Mail mithilfe von Outlook im Web und einiger mobiler E-Mail-Anwendungen klassifizieren. 

Auf dieselbe Weise können Sie Ihre Bezeichnungen mit Outlook im Web und diesen mobilen E-Mail-Anwendungen verwenden.

Die Konfigurationsschritte finden Sie unter [Integrieren der Exchange-Nachrichtenklassifizierung mit Azure Information Protection für eine Lösung zur Bezeichnung von Mobilgeräten](../rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



[!INCLUDE[Commenting house rules](../includes/houserules.md)]
