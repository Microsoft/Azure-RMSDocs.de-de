---
title: Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen – AIP
description: Haben Sie Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen bei Azure Information Protection beziehen? Vielleicht finden Sie hier eine Antwort.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/12/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: d4bfec07900404c39a17a90468a726f6632078fe
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97382274"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Weitere Informationen finden Sie auch in den häufig gestellten Fragen [zum klassischen Client](faqs-classic.md). *

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort. 

## <a name="which-client-do-i-install-for-testing-new-functionality"></a>Welchen Client installiere ich zum Testen neuer Funktionen?

Es wird empfohlen, den **Azure Information Protection Unified Bezeichnung-Client** zu installieren. Der Unified Label-Client lädt Bezeichnungen und Richtlinien Einstellungen von einem der folgenden admin Centers herunter: 

- Office 365 Security & Compliance Center
- Microsoft 365 Security Center
- Microsoft 365 Compliance Center.

Dieser Client ist nun allgemein verfügbar und verfügt möglicherweise über eine Vorschauversion, um zusätzliche Funktionen für eine zukünftige Version zu testen.

Wenn Sie weiterhin Bezeichnungen in der Azure-Portal konfiguriert haben, die Sie noch nicht [zum vereinheitlichten Bezeichnungs Speicher migriert](configure-policy-migrate-labels.md)haben, verwenden Sie stattdessen den **klassischen Azure Information Protection-Client** .

Weitere Informationen, einschließlich einer Funktions-und Funktionalitäts Vergleichstabelle, finden [Sie unter Auswählen der Windows-beschriftungslösung](rms-client/use-client.md#choose-your-windows-labeling-solution).

> [!TIP]
> Der Azure Information Protection-Client wird nur unter Windows unterstützt. 
>
> Verwenden Sie zum klassifizieren und schützen von Dokumenten und e-Mails auf Ios, Android, macOS und im Web [Office-Apps, die die integrierte Bezeichnung unterstützen](/microsoft-365/compliance/sensitivity-labels-office-apps#support-for-sensitivity-label-capabilities-in-apps). 
> 

## <a name="where-can-i-find-information-about-using-sensitivity-labels-for-office-apps"></a>Wo finde ich Informationen zur Verwendung von Vertraulichkeits Bezeichnungen für Office-Apps?

Weitere Informationen finden Sie in den folgenden Dokumentations Ressourcen:

- [Informationen zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels) 

- [Verwenden von Vertraulichkeitsbezeichnungen in Office-Apps](/microsoft-365/compliance/sensitivity-labels-office-apps)

- [Aktivieren von Vertraulichkeits Bezeichnungen für Office-Dateien in SharePoint und onedrive](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files)

- [Anwenden von Vertraulichkeits Bezeichnungen auf Ihre Dokumente und e-Mails innerhalb von Office](https://support.office.com/article/Apply-sensitivity-labels-to-your-documents-and-email-within-Office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9#ID0EBFAAA=Office_365)

Weitere Informationen zu anderen Szenarien, die Vertraulichkeits Bezeichnungen unterstützen, finden Sie unter [häufige Szenarien für Vertraulichkeits Bezeichnungen](/microsoft-365/compliance/get-started-with-sensitivity-labels#common-scenarios-for-sensitivity-labels).

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet: eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Vertraulich** Unterbezeichnungen wie z.B. **Legal** (Recht) und **Finance** (Finanzen) enthalten. Sie können unterschiedliche visuelle Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Vertraulich** nicht selbst auswählen, sondern nur eine der untergeordneten Bezeichnungen, z.B. **Legal** (Recht). Daher wird als festgelegte Bezeichnung **Confidential \ Legal** (Vertraulich\Recht) angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Confidential** (Vertraulich), eine benutzerdefinierte Texteigenschaft für **Legal** (Recht) und eine weitere mit beiden Werten (**Confidential Legal** (Vertraulich Recht)). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen für die übergeordnete und deren untergeordnete Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Wie hindere ich jemanden daran, eine Bezeichnung zu entfernen oder zu ändern?

Um Benutzer daran zu hindern, eine Bezeichnung zu entfernen oder zu ändern, muss der Inhalt bereits geschützt sein. Die Schutzberechtigungen erteilen dem Benutzer nicht das [Nutzungsrecht](configure-usage-rights.md) „Exportieren“ oder „Vollzugriff“. 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anhänge erhalten keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Office-Anlagen angewendet.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. 

Beispiele für die Verwendung dieser Metadaten mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren von Exchange Online-Nachrichtenflussregeln für Azure Information Protection-Bezeichnungen](configure-exo-rules.md).