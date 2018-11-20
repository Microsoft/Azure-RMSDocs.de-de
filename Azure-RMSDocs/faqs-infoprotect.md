---
title: Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen – AIP
description: Haben Sie Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen bei Azure Information Protection beziehen? Vielleicht finden Sie hier eine Antwort darauf.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/14/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.openlocfilehash: 2c0d391e2d00ec7d0bc09d98de3fe6f502f999a4
ms.sourcegitcommit: 4c4af9766342272eaa18df720ba3738d44ba99c8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2018
ms.locfileid: "51707741"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort darauf. 

## <a name="what-can-i-do-with-the-classification-capabilities-in-azure-information-protection"></a>Was kann ich mit den Klassifizierungsfunktionen in Azure Information Protection tun?

Absolvieren Sie unser [Tutorial: Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md), um diese in nur wenigen Minuten selbst in Aktion zu sehen.

Achten Sie auf Ankündigungen im [Enterprise Mobility + Security Blog](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/bg-p/enterprisemobilityandsecurity/label-name/Azure%20Information%20Protection) (Informationen in englischer Sprache zu Enterprise Mobility und Security) und auf unserer [Yammer-Seite](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all), um zu erfahren, wann zusätzliche Klassifizierungsfeatures und -funktionen verfügbar sind. Die aktuelle Version hat einige Einschränkungen, einschließlich der Folgenden:

- Keine Bezeichnungsoption in Office-Web-Apps (Office Online)

- Keine Klassifizierungs- und Bezeichnungsintegration mit Exchange Online oder SharePoint Online.

> [!NOTE]
> **Jetzt in der Vorschau:**
> - Zentralisierte Berichterstellung für die Klassifizierung und Bezeichnung. Weitere Informationen finden Sie unter [Zentrale Berichterstellung für Azure Information Protection](reports-aip.md).
> - Bezeichnungsoption in Office-Apps für mobile Geräte (iOS und Android) und Mac-Computer für Kunden des [Office Insider-Programms](https://support.office.com/article/what-is-office-insider-f4208185-b63a-4b68-9c7a-9a32d2411c16). Weitere Informationen finden Sie unter [Anwenden von Vertraulichkeitsbezeichnungen auf Dokumente und E-Mails in Office](https://aka.ms/officemipdocs).


Fragen Sie neue Funktionen an, und stimmen Sie auf der [UserVoice-Website](https://msip.uservoice.com/) für Azure Information Protection über die Anforderungen ab.

## <a name="do-i-need-to-be-a-global-admin-to-configure-classification-and-labels"></a>Muss ich ein globaler Administrator sein, um Klassifizierungen und Bezeichnungen zu konfigurieren?

Mit der neu eingeführten Administratorrolle von Information Protection wurde diese Frage auf der Hauptseite für FAQs beantwortet: [Benötigt man globale Administratorrechte, um Azure Information Protection zu konfigurieren, oder kann ich das an andere Administratoren delegieren?](faqs.md#do-you-need-to-be-a-global-admin-to-configure-azure-information-protection-or-can-i-delegate-to-other-administrators)

Wenn Sie die Option zum Installieren der Demorichtlinie bei der Installation des [Azure Information Protection-Clients](https://www.microsoft.com/en-us/download/details.aspx?id=53018) auswählen, müssen Sie sich nicht beim Portal anmelden, um die Bezeichnungsfunktion testen zu können. Die Demorichtlinie installiert lokal eine Standardrichtlinie für Azure Information Protection, damit Sie das Bezeichnen von Dokumenten und E-Mails ausprobieren können. Sie können neue Bezeichnungen jedoch nicht ändern oder hinzufügen, ohne sich beim Azure-Portal anzumelden. 

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet: eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Vertraulich** Unterbezeichnungen wie z.B. **Legal** (Recht) und **Finance** (Finanzen) enthalten. Sie können unterschiedliche visuelle Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Vertraulich** nicht selbst auswählen, sondern nur eine der untergeordneten Bezeichnungen, z.B. **Legal** (Recht). Daher wird als festgelegte Bezeichnung **Confidential \ Legal** (Vertraulich\Recht) angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Confidential** (Vertraulich), eine benutzerdefinierte Texteigenschaft für **Legal** (Recht) und eine weitere mit beiden Werten (**Confidential Legal** (Vertraulich Recht)). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen für die übergeordnete und deren untergeordnete Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Wie hindere ich jemanden daran, eine Bezeichnung zu entfernen oder zu ändern?

Es gibt zwar eine [Richtlinieneinstellung](configure-policy-settings.md), für die Benutzer angeben müssen, warum sie die Klassifizierungsbezeichnung senken oder den Schutz entfernen, jedoch verhindert dieses Einstellung diese Aktionen nicht. Um Benutzer daran zu hindern, eine Bezeichnung zu entfernen oder zu ändern, muss der Inhalt bereits geschützt sein. Die Schutzberechtigungen erteilen dem Benutzer nicht das [Nutzungsrecht](configure-usage-rights.md) „Exportieren“ oder „Vollzugriff“. 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anhänge erhalten keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Office-Anlagen angewendet.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. 

Weitere Informationen und Beispiele für die Verwendung dieser Metadaten mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren von Exchange Online-Nachrichtenflussregeln für Azure Information Protection-Bezeichnungen](configure-exo-rules.md).

## <a name="how-is-azure-information-protection-classification-for-emails-different-from-exchange-message-classification"></a>Wie unterscheidet sich die Azure Information Protection-Klassifizierung für E-Mails von der Exchange-Nachrichtenklassifizierung?

Die Exchange-Nachrichtenklassifizierung ist ein älteres Feature, das unabhängig von einer Azure Information Protection-Klassifizierung implementiert wird, und mit dem E-Mails klassifiziert werden können. 

Sie können jedoch beide Lösungen integrieren, damit die Azure Information Protection-Klassifizierung und entsprechende Bezeichnungsmarkierungen automatisch hinzugefügt werden, wenn Benutzer eine E-Mail mithilfe von Outlook im Web und einiger mobiler E-Mail-Anwendungen klassifizieren. 

Auf dieselbe Weise können Sie Ihre Bezeichnungen mit Outlook im Web und diesen mobilen E-Mail-Anwendungen verwenden.

Die Konfigurationsschritte finden Sie unter [Integrieren der Exchange-Nachrichtenklassifizierung mit Azure Information Protection für eine Lösung zur Bezeichnung von Mobilgeräten](./rms-client/client-admin-guide-customizations.md#integration-with-exchange-message-classification-for-a-mobile-device-labeling-solution). 



