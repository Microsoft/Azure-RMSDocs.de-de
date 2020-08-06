---
title: Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen – AIP
description: Haben Sie Fragen, die sich speziell auf Klassifizierungen und Bezeichnungen bei Azure Information Protection beziehen? Vielleicht finden Sie hier eine Antwort.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 03/16/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 4b595b6a-7eb0-4438-b49a-686431f95ddd
ms.reviewer: adhall
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 20698241962b8dfe3e1fd81b7f0538a7ddfdd46a
ms.sourcegitcommit: dec5df81b569283a72f0a983d3f53b82cbbc562c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87802180"
---
# <a name="frequently-asked-questions-about-classification-and-labeling-in-azure-information-protection"></a>Häufig gestellte Fragen zu Klassifizierungen und Bezeichnungen in Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenumgebung zu gewährleisten, werden **Azure Information Protection-Client (klassisch)** und **Bezeichnungsverwaltung** im Azure-Portal zum **31. März 2021** **eingestellt**. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Haben Sie Fragen zu Azure Information Protection, die sich speziell auf Klassifizierungen und Bezeichnungen beziehen?  Vielleicht finden Sie hier eine Antwort. 

## <a name="which-client-do-i-install-for-testing-new-functionality"></a>Welchen Client installiere ich zum Testen neuer Funktionen?

Derzeit gibt es zwei Azure Information Protection Clients für Windows: 

- Der **Azure Information Protection Unified** Label-Client, der Bezeichnungen und Richtlinien Einstellungen von einem der folgenden Admin Center herunterlädt: Office 365 Security & Compliance Center, Microsoft 365 Security Center, Microsoft 365 Compliance Center. Dieser Client ist nun allgemein verfügbar und verfügt möglicherweise über eine Vorschauversion, um zusätzliche Funktionen für eine zukünftige Version zu testen.

- Der **Azure Information Protection-Client (klassisch)** , der Bezeichnungen und Richtlinien Einstellungen aus dem Azure-Portal herunterlädt. Dieser Client baut auf früheren Versionen der allgemeinen Verfügbarkeit des Clients auf.

Wir empfehlen Ihnen, mit dem Unified-Bezeichnungs Client zu testen, wenn der aktuelle Funktionsumfang und die Funktionalität ihren Geschäftsanforderungen entsprechen. Falls nicht, oder wenn Sie Bezeichnungen in der Azure-Portal konfiguriert haben, die Sie noch nicht [zum vereinheitlichten Bezeichnungs Speicher migriert](configure-policy-migrate-labels.md)haben, verwenden Sie den klassischen Client.

Weitere Informationen sowie eine Tabelle zum Vergleich der Features und Funktionen finden Sie unter [Auswählen des zu verwendenden Azure Information Protection-Clients](./rms-client/use-client.md#choose-which-labeling-client-to-use-for-windows-computers).

## <a name="where-can-i-find-information-about-using-sensitivity-labels-for-office-apps"></a>Wo finde ich Informationen zur Verwendung von Vertraulichkeits Bezeichnungen für Office-Apps?

Weitere Informationen finden Sie in den folgenden Dokumentations Ressourcen:

- [Informationen zu Empfindlichkeits Bezeichnungen](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) 

- [Vertraulichkeits Bezeichnungen in Office-Apps](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-office-apps)

- [Anwenden von Vertraulichkeits Bezeichnungen auf Ihre Dokumente und e-Mails innerhalb von Office](https://support.office.com/article/Apply-sensitivity-labels-to-your-documents-and-email-within-Office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9#ID0EBFAAA=Office_365)

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet: eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Vertraulich** Unterbezeichnungen wie z.B. **Legal** (Recht) und **Finance** (Finanzen) enthalten. Sie können unterschiedliche visuelle Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Vertraulich** nicht selbst auswählen, sondern nur eine der untergeordneten Bezeichnungen, z.B. **Legal** (Recht). Daher wird als festgelegte Bezeichnung **Confidential \ Legal** (Vertraulich\Recht) angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Confidential** (Vertraulich), eine benutzerdefinierte Texteigenschaft für **Legal** (Recht) und eine weitere mit beiden Werten (**Confidential Legal** (Vertraulich Recht)). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen für die übergeordnete und deren untergeordnete Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.

## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Wie hindere ich jemanden daran, eine Bezeichnung zu entfernen oder zu ändern?

Es gibt zwar eine [Richtlinien Einstellung](configure-policy-settings.md) , bei der Benutzer angeben müssen, warum Sie eine Klassifizierungs Bezeichnung herabsetzen, eine Bezeichnung entfernen oder den Schutz entfernen, aber diese Einstellung verhindert diese Aktionen nicht. Um Benutzer daran zu hindern, eine Bezeichnung zu entfernen oder zu ändern, muss der Inhalt bereits geschützt sein. Die Schutzberechtigungen erteilen dem Benutzer nicht das [Nutzungsrecht](configure-usage-rights.md) „Exportieren“ oder „Vollzugriff“. 

## <a name="when-an-email-is-labeled-do-any-attachments-automatically-get-the-same-labeling"></a>Wenn eine E-Mail eine Bezeichnung umfasst, erhalten Anlagen dann automatisch dieselbe Bezeichnung?

Nein. Wenn Sie einer E-Mail-Nachricht mit Anlagen eine Bezeichnung zuweisen, erben die Anlagen nicht dieselbe Bezeichnung. Die Anhänge erhalten keine Bezeichnung, oder es wird eine separate Bezeichnung angewendet. Wenn aber mit der Bezeichnung für die E-Mail ein Schutz konfiguriert wird, wird dieser Schutz auch auf die Office-Anlagen angewendet.

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. 

Weitere Informationen zu diesen Metadaten finden Sie unter [In E-Mails und Dokumenten gespeicherte Bezeichnungsinformationen](configure-policy.md#label-information-stored-in-emails-and-documents).

Beispiele für die Verwendung dieser Metadaten mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren von Exchange Online-Nachrichtenflussregeln für Azure Information Protection-Bezeichnungen](configure-exo-rules.md).

## <a name="can-i-create-a-document-template-that-automatically-includes-the-classification"></a>Kann ich eine Dokumentvorlage erstellen, die automatisch die Klassifizierung umfasst?

Ja. Sie können eine Bezeichnung konfigurieren, um [eine Kopf- oder Fußzeile anzuwenden, die den Namen der Bezeichnung enthält](configure-policy-markings.md). Wenn dies jedoch nicht Ihren Anforderungen entspricht, können Sie nur für den Azure Information Protection Client (klassisch) eine Dokument Vorlage mit der gewünschten Formatierung erstellen und die Klassifizierung als Feldcode hinzufügen. 

Beispielsweise könnten Sie eine Tabelle in der Kopfzeile des Dokuments einrichten, die die Klassifizierung angezeigt. Verwenden Sie alternativ eine bestimmte Formulierung für eine Einführung, die auf die Klassifizierung des Dokuments verweist.

So fügen Sie diesen Feldcode Ihrem Dokument hinzu:

1. Geben Sie dem Dokument eine Bezeichnung, und speichern Sie es. So werden neue Metadatenfelder erstellt, die Sie jetzt für Ihren Feldcode verwenden können.

2. Positionieren Sie den Cursor im Dokument dort, wo Sie die Bezeichnung der Klassifizierung hinzufügen möchten, und wählen Sie anschließend auf der Registerkarte **Einfügen****Text** > **Schnellbausteine** > **Feld** aus.

3. Wählen Sie im Dialogfeld **Feld** in der Dropdownliste **Kategorien****Dokumentinformationen** aus. Wählen Sie dann in der Dropdownliste **Feldernamen****DocProperty** aus.

4. Wählen Sie in der Dropdownliste **Eigenschaft****Vertraulichkeit** und dann **OK**.

Die aktuelle Klassifizierung der Bezeichnung wird im Dokument angezeigt, und dieser Wert wird automatisch aktualisiert, wenn Sie das Dokument öffnen oder die Vorlage verwenden. Wenn sich also die Bezeichnung ändert, wird die Klassifizierung, die für diesen Feldcode angezeigt wird, automatisch im Dokument aktualisiert.

## <a name="how-is-classification-for-emails-using-azure-information-protection-different-from-exchange-message-classification"></a>Wie unterscheidet sich die Klassifizierung für e-Mails mit Azure Information Protection von der Exchange-Nachrichtenklassifizierung?

Die Exchange-Nachrichtenklassifizierung ist ein älteres Feature, mit dem e-Mails klassifiziert werden können, und es wird unabhängig von Azure Information Protection Bezeichnungen oder Vertraulichkeits Bezeichnungen implementiert, die die Klassifizierung anwenden.

Sie können dieses ältere Feature jedoch in Bezeichnungen integrieren, sodass Benutzer, die eine e-Mail mithilfe von Outlook im Web klassifizieren und einige Mobile Mail-Anwendungen verwenden, automatisch die Bezeichnung Klassifizierung und entsprechende Bezeichnungs Markierungen hinzufügen.

Auf dieselbe Weise können Sie Ihre Bezeichnungen mit Outlook im Web und diesen mobilen E-Mail-Anwendungen verwenden.

Beachten Sie, dass dies nicht erforderlich ist, wenn Sie Outlook im Web mit Exchange Online verwenden, da diese Kombination eine integrierte Bezeichnung unterstützt, wenn Sie Vertraulichkeits Bezeichnungen aus dem Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft Compliance Center veröffentlichen.

Wenn Sie die integrierte Bezeichnung nicht mit Outlook im Web verwenden können, finden Sie weitere Informationen in den Konfigurationsschritten für diese Problem Umgehung: [Integration in die Legacy-Exchange-Nachrichtenklassifizierung](rms-client/client-admin-guide-customizations.md#integration-with-the-legacy-exchange-message-classification) .