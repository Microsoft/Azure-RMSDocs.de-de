---
title: Was ist Azure Information Protection (AIP)?
description: Azure Information Protection (AIP) ist ein Dienst, der Organisationen bei der Bezeichnung von Dokumenten und E-Mails unterstützt. AIP klassifiziert und schützt Daten unabhängig davon, wo diese gespeichert sind.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 06/23/2020
ms.topic: overview
ms.collection: M365-security-compliance
ms.service: information-protection
Customer intent: As an administrator, I want to label documents and emails to classify and protect my organization's data, wherever it resides.
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: 25b520e08d8379580226d589fec511d502065156
ms.sourcegitcommit: 6b159e050176a2cc1b308b1e4f19f52bb4ab1340
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2020
ms.locfileid: "91588404"
---
# <a name="what-is-azure-information-protection"></a>Was ist Azure Information Protection?

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection (AIP) ist eine cloudbasierte Lösung, die Organisationen das Klassifizieren und Schützen von Dokumenten und E-Mails durch Anwendung von Bezeichnungen ermöglicht. Bezeichnungen können folgendermaßen angewendet werden:

- **Automatisch** durch Administrator mithilfe von Regeln und Bedingungen
- **Manuell** durch Benutzer
- **Durch eine Kombination** dieser Optionen, bei der Administratoren die Empfehlungen definieren, die den Benutzern angezeigt werden

Der Administrator konfiguriert beispielsweise eine Bezeichnung mit Regeln, die vertrauliche Daten erkennen, also z. B. Kreditkarteninformationen. In diesem Fall kann jedem Benutzer, der Kreditkarteninformationen in einer Word-Datei speichert, oben im Dokument eine QuickInfo mit der Empfehlung angezeigt werden, die für dieses Szenario relevante Bezeichnung anzuwenden.

Bezeichnungen können Ihre Dokumente [klassifizieren](#how-labels-apply-classification-with-aip) und optional auch [schützen](#how-aip-protects-your-data). Damit erhalten Sie folgende Möglichkeiten:

- **Nachverfolgen und Steuern** der Verwendung Ihrer Inhalte
- **Analysieren von Datenflüssen** zum Gewinnen von Erkenntnissen zum Geschäft **– Erkennen von riskanten Verhaltensweisen** und Ergreifen von Korrekturmaßnahmen
- **Nachverfolgen des Dokumentzugriffs** und Verhindern von Datenlecks oder Datenmissbrauch
- Und vieles mehr...

## <a name="how-labels-apply-classification-with-aip"></a>So wenden Bezeichnungen mit AIP Klassifizierungen an

Verwenden Sie Azure Information Protection, um Klassifizierungsbezeichnungen sowohl auf Dokumente als auch auf E-Mails anzuwenden.

Der Inhalt der Bezeichnung umfasst Folgendes:

- Die **Klassifizierung**, die unabhängig davon erkannt werden kann, wo die Daten gespeichert oder von wem sie freigegeben werden
- **Optische Kennzeichnungen**, zum Beispiel Kopfzeilen, Fußzeilen oder Wasserzeichen
- **Metadaten**, die Dateien und E-Mail-Headern als Klartext hinzugefügt werden Dieser Klartextmetadaten stellen sicher, dass andere Dienste die Klassifizierung identifizieren und entsprechende Maßnahmen ergreifen können.

Auf der folgenden Abbildung hat die Bezeichnung z. B. eine E-Mail-Nachricht als *Allgemein* klassifiziert, wobei der [Client für einheitliche Bezeichnungen](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients) verwendet wurde:

:::image type="content" source="media/example-email-footerv2.png" alt-text="E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung":::

In diesem Beispiel hat die Bezeichnung auch folgende Schritte durchgeführt:

- **Eine Fußzeile *Vertraulichkeit: Allgemein* der E-Mail-Nachricht hinzugefügt** Dieser Fußzeile ist ein visueller Indikator für alle Empfänger, das allgemeine Unternehmensdaten nicht an Empfänger außerhalb der Organisation gesendet werden dürfen.
- **In E-Mail-Header eingebettete Metadaten.** Headerdaten ermöglichen es E-Mail-Diensten, die Bezeichnung zu überprüfen und theoretisch einen Überwachungseintrag zu erstellen oder zu verhindern, dass sie außerhalb der Organisation versendet wird.

## <a name="how-aip-protects-your-data"></a>So schützt AIP Ihre Daten

Azure Information Protection verwendet den [*Azure Rights Management-Dienst* (Azure RMS)](what-is-azure-rms.md), um Ihre Daten zu schützen. 

Azure RMS ist in andere Microsoft-Clouddienste und -Anwendungen integriert, z. B. Microsoft 365 und Azure Active Directory, und kann auch mit Ihren eigenen Anwendungen oder Drittanbieteranwendungen sowie Lösungen zum Schutz von Daten verwendet werden. Azure RMS funktioniert sowohl mit lokalen Lösungen als auch mit Cloudlösungen.

Azure RMS verwendet Verschlüsselung, Identitäten und Autorisierungsrichtlinien. Ähnlich wie bei AIP-Bezeichnungen bleibt der durch Azure RMS angewendete Schutz in den Dokumenten und E-Mails unabhängig vom Speicherort der Dokumente oder der E-Mails. So wird sichergestellt, dass Sie die Kontrolle über Ihre Inhalte behalten, auch wenn diese mit anderen Benutzern geteilt werden.

Für Schutzeinstellungen kann Folgendes gelten:

- Sie können **Teil der Konfiguration Ihrer Bezeichnungen sein**, sodass Benutzer Dokumente und E-Mails ganz einfach durch Anwenden einer Bezeichnung klassifizieren und schützen können. 
- Sie können von Anwendungen und Diensten **separat verwendet werden**, die zwar den Schutz unterstützen, aber keine Bezeichnungen. 

    Für Anwendungen und Dienste, die nur den Schutz unterstützen, werden die Schutzeinstellungen als [Rights Management-Vorlagen](#rights-management-templates) verwendet.

Beispielsweise sollten Sie ein Berichtsdokument oder eine Tabelle mit Verkaufsprognosen so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können. In diesem Fall würden Sie Schutzeinstellungen anwenden, um zu steuern, ob das Dokument bearbeitet werden kann, es auf den Schreibschutz einschränken, oder verhindern, dass es gedruckt wird.

E-Mails können ähnliche Schutzeinstellungen aufweisen, um zu verhindern, dass sie weitergeleitet werden oder die Option „Alle antworten“ verwendet wird.

### <a name="rights-management-templates"></a>Rights Management-Vorlagen

Sobald der Azure Rights Management-Dienst aktiviert ist, stehen Ihnen zwei Standardvorlagen für die Rechteverwaltung zur Verfügung, mit denen Sie den Datenzugriff auf Benutzer innerhalb Ihrer Organisation beschränken können. Verwenden Sie diese Vorlagen sofort, oder konfigurieren Sie eigene Schutzeinstellungen, um restriktivere Kontrollen in neuen Vorlagen anzuwenden.

Rights Management-Vorlagen können in beliebigen Anwendungen oder Diensten verwendet werden, die Azure Rights Management unterstützen.

Die folgende Abbildung zeigt ein Beispiel aus dem Exchange Admin Center, in dem Sie z. B. Exchange Online-E-Mail-Flussregeln für die Verwendung der RMS-Vorlagen konfigurieren können:

:::image type="content" source="media/templates-exchangeonline-callouts.png" alt-text="E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung":::

> [!NOTE]
> Beim Erstellen einer AIP-Bezeichnung, die Schutzeinstellungen enthält, wird auch eine entsprechende Rights Management-Vorlage erstellt, die separat von der Bezeichnung verwendet werden kann. 
>  

Weitere Informationen finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md)

## <a name="aip-and-end-user-integration-for-documents-and-emails"></a>AIP- und Endbenutzerintegration für Dokumente und E-Mails

Der AIP-Client installiert die Information Protection-Leiste in Office-Anwendungen und ermöglicht es Endbenutzern, AIP in ihre Dokumente und E-Mails zu integrieren.

Verwenden Sie beispielsweise in Excel den [Client für einheitliche Bezeichnungen](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients):

![Beispiel für die Azure Information Protection-Leiste in Excel](./media/excelproplus-infoprotect-bar.png)

Obwohl Bezeichnungen automatisch auf Dokumente und E-Mails angewendet werden können, Unwägbarkeiten für Benutzer entfernt oder die Richtlinien einer Organisation eingehalten werden können, ermöglicht es die Information Protection-Leiste Endbenutzern, selbst Bezeichnungen auszuwählen und Klassifizierungen anzuwenden.

Außerdem ermöglicht der AIP-Client Benutzern das gleichzeitige Klassifizieren und Schützen zusätzlicher Dateitypen oder mehrerer Dateien über das Kontextmenü in Windows-Explorer. Beispiel:

:::image type="content" source="media/right-click-classify-protect-folder.png" alt-text="E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung":::

Die Menüoption **Klassifizieren und schützen** funktioniert ähnlich wie die Information Protection-Leiste in Office-Anwendungen, wodurch Benutzer eine Bezeichnung auswählen oder benutzerdefinierte Berechtigungen festlegen können.

> [!TIP]
> Hauptbenutzer (oder Administratoren) finden die Verwendung von PowerShell-Befehlen zum Verwalten und Festlegen von Klassifizierung und Schutz für mehrere Dateien möglicherweise effizienter. [Relevante PowerShell-Befehle](/powershell/module/azureinformationprotection) sind im Client enthalten und können auch separat installiert werden.

Benutzer und Administratoren können die Website zur Dokumentenverfolgung verwenden, um geschützte Dokumente zu überwachen, zu überwachen, wer auf sie zugreift und wann auf diese zugegriffen wird. Wenn sie einen Missbrauch vermuten, können sie auch den Zugriff auf diese Dokumente entziehen. Beispiel:

![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](./media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>Zusätzliche Integration für E-Mails

Die Verwendung von AIP mit Exchange Online bietet den zusätzlichen Vorteil, dass geschützte E-Mails an jeden Benutzer gesendet werden, wobei sichergestellt wird, dass diese die E-Mail auf jedem Gerät lesen können.

Das ist beispielsweise nützlich, wenn Sie vertrauliche Informationen an persönliche E-Mail-Adressen senden müssen, die ein **Gmail**-, **Hotmail**- oder **Microsoft**-Konto verwenden, oder wenn Benutzer kein Microsoft 365- oder Azure AD-Konto besitzen. Diese E-Mails sollten im ruhenden Zustand und bei der Übertragung verschlüsselt und nur von den ursprünglichen Empfängern gelesen werden.

Für dieses Szenario sind die [Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) erforderlich. Wenn die Empfänger die geschützte E-Mail nicht in ihrem nativen E-Mail-Client öffnen können, können sie die vertraulichen Informationen mithilfe einer Einmalkennung in einem Browser lesen.

Einem Gmail-Benutzer wird möglicherweise die folgende Aufforderung in einer empfangenen E-Mail angezeigt:

:::image type="content" source="media/ome-message.png" alt-text="E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung":::

Für den Benutzer, der die E-Mail sendet, sind dieselben Aktionen wie für das Senden einer geschützten E-Mail an einen Benutzer in der eigenen Organisation erforderlich. Klicken Sie dazu beispielsweise auf die Schaltfläche **Nicht weiterleiten**, die der AIP-Client dem Outlook-Menüband hinzufügen kann. 

Alternativ kann die Funktion „Nicht weiterleiten“ in eine Bezeichnung integrieren werden, die Benutzer dann auswählen können, um sowohl die Klassifizierung als auch den Schutz auf diese E-Mail anzuwenden. Ein Beispiel ist der [Client für einheitliche Bezeichnungen](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients):

![Auswählen einer Bezeichnung, für die die Option „Nicht weiterleiten“ konfiguriert ist](./media/recipients-only-label2.png)

Alternativ können Administratoren ebenfalls anhand von E-Mail-Flussregeln, bei denen Rechteschutz angewendet wird, automatisch Schutz für Benutzer gewährleisten.

Alle an diese E-Mails angefügten Office-Dokumente werden ebenfalls automatisch geschützt.

## <a name="scanning-for-existing-content-to-classify-and-protect"></a>Suchen nach vorhandenen Inhalten zum Klassifizieren und Schützen

Im Idealfall bezeichnen Sie Dokumente und E-Mails, wenn sie erstellt werden. Sie besitzen aber wahrscheinlich viele Dokumente, die entweder lokal oder in der Cloud gespeichert sind, und möchten diese auch klassifizieren und schützen.

Verwenden Sie eine der folgenden Methoden, um vorhandene Inhalte zu klassifizieren und zu schützen:

- **Lokaler Speicher:** Verwenden Sie die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md), um Dokumente in Netzwerkfreigaben und Microsoft SharePoint Server-Standorten und -Bibliotheken zu erkennen, zu klassifizieren und zu schützen.

    Die Überprüfung wird als Dienst auf Windows Server ausgeführt und verwendet die gleichen Richtlinienregeln, um vertrauliche Informationen zu erkennen und bestimmte Bezeichnungen auf Dokumente anzuwenden. 

    Verwenden Sie die Überprüfung alternativ, um Standardbezeichnung auf alle Dokumente in einem Datenrepository anzuwenden, ohne den Inhalt der Datei zu überprüfen. Zudem haben Sie die Möglichkeit, die Überprüfung auch nur im Berichterstellungsmodus zu verwenden, um vertrauliche Daten zu finden, von denen Sie vielleicht nicht wissen, dass sie vorhanden sind.

- **Clouddatenspeicher:** Verwenden Sie [Microsoft Cloud App Security](/cloud-app-security/azip-integration), um Ihre Bezeichnungen für Dokumente in Box, SharePoint und OneDrive anzuwenden. Ein zugehöriges Tutorial finden Sie unter [Automatisches Anwenden von Azure Information Protection-Klassifizierungsbezeichnungen](/cloud-app-security/use-case-information-protection). 

## <a name="latest-labeling-updates-for-microsoft-365"></a>Neueste Updates zu den Bezeichnungen für Microsoft 365

Hier finden Sie die neuesten Informationen dazu, wie Azure Information Protection Sie dabei unterstützt, Ihre vertraulichen Informationen mithilfe von Microsoft 365 zu ermitteln, zu klassifizieren, zu schützen und zu überwachen – unabhängig davon, wo diese Informationen gespeichert sind:

> [!VIDEO https://www.youtube.com/embed/UI0p9xqMNfI]

Weitere Informationen finden Sie in folgenden Quellen:

- [Neuerungen in Microsoft 365 Admin Center](/microsoft-365/admin/whats-new-in-preview)
- [Neuerungen in SharePoint Admin Center](/sharepoint/what-s-new-in-admin-center)

## <a name="additional-azure-information-protection-resources"></a>Zusätzliche Azure Information Protection-Ressourcen

- **Kostenlose Testversion:** [Enterprise Mobility + Security E5](https://admin.microsoft.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- **Abonnementoptionen und Preise:** [Azure Information Protection – Preise](https://azure.microsoft.com/pricing/details/information-protection)

- **Herunterladen des Clients:** [Azure Information Protection-Client](https://www.microsoft.com/download/details.aspx?id=53018)

- **Herunterladen eines anpassbaren Leitfadens für Endbenutzer:** [Azure Information Protection End User Adoption Guide](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf) (Endbenutzerhandbuch für die Einführung in Azure Information Protection)

- **Häufig gestellte Fragen:** [Häufig gestellte Fragen zu Azure Information Protection](faqs.md)

- **Yammer:** [Azure Information Protection](https://www.yammer.com/AskIPTeam)

- **Twitter-Feed zur Dokumentation:** [https://twitter.com/docsmsft](https://twitter.com/docsmsft)

**Zusätzliche Ressourcen:** [Informationen zu und Unterstützung von Azure Information Protection](information-support.md)

### <a name="microsoft-ignite"></a>Microsoft Ignite

Die Microsoft Ignite 2019 in Orlando war ein großer Erfolg! Dort konnten Sie viele nützliche Informationen zu Azure Information Protection und den neuesten Updates und Verbesserungen erhalten. Wenn Sie nicht teilnehmen konnten, können Sie sich später eine Aufzeichnung der Sitzungen ansehen.

Im Folgenden finden Sie die fünf Sitzungen, die wir Ihnen empfehlen:

- [BRK2119: „Secure your sensitive data!“ (Sichern Sie Ihre vertraulichen Daten!) Grundlegendes zu den neuesten Funktionen von Microsoft Information Protection](https://myignite.techcommunity.microsoft.com/sessions/81172?source=sessions)
 
- [THR3067: „Know your data“ (Details zu Ihren Daten): Die besten fünf Tipps und Tricks zum besseren Verständnis Ihrer vertraulichen Daten](https://myignite.techcommunity.microsoft.com/sessions/81183)

- [BRK3103: „Protecting sensitive files and data can be hard.“ (Der Schutz vertraulicher Dateien und Daten kann schwierig sein.) Auswahl der richtigen Datenschutzoptionen mit dem richtigen Verhältnis zwischen Sicherheit und Mitarbeiterproduktivität](https://myignite.techcommunity.microsoft.com/sessions/81177?source=sessions)

- [BRK2120: „Got Azure Information Protection?“ (Haben Sie Azure Information Protection schon?) Sicherer Umgang mit einheitlichen Bezeichnungen, Richtlinienkonfiguration, Clients und Analysen](https://myignite.techcommunity.microsoft.com/sessions/81178?source=sessions)

- [BRK2121: Extend the power of sensitivity labeling and protection to your own apps and ISV solutions with the Microsoft Information Protection SDK. (Nutzen Sie mit dem Microsoft Information Protection SDK leistungsstarke Vertraulichkeitsbezeichnungen und Schutzfunktionen für Ihre eigenen Apps und ISV-Lösungen.)](https://myignite.techcommunity.microsoft.com/sessions/81179?source=sessions)

Letzter Blogbeitrag: [Grundlegende Informationen zum Speicherort sensibler Daten und dem intelligenten Schutz mit Microsoft 365](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Understand-where-your-sensitive-data-is-located-and/ba-p/960465)


## <a name="next-steps"></a>Nächste Schritte

Konfigurieren und testen Sie Azure Information Protection selbst mit den [Schnellstarts](quickstart-viewpolicy.md) und [Tutorials](infoprotect-quick-start-tutorial.md). 

Wenn Sie schon soweit sind, dass Sie diesen Dienst für Ihre Organisation bereitstellen möchten, wechseln Sie direkt zu den [Schrittanleitungen](how-to-guides.md).