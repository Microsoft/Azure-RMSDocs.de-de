---
title: Bezeichnung, Klassifizierung und Schutz der Azure Information Protection (AIP)
description: Erfahren Sie, wie Azure Information Protection (AIP) Dokumente und e-Mails bezeichnen kann, um Ihre Daten zu klassifizieren und zu schützen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 09/14/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
Customer intent: As an administrator, I want to label documents and emails to classify and protect my organization's data, wherever it resides.
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: 71f07f5ffb9167ab61653cef10c610968ff74786
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97384195"
---
# <a name="azure-information-protection-aip-labeling-classification-and-protection"></a>Bezeichnung, Klassifizierung und Schutz der Azure Information Protection (AIP)

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
> ***Relevant für**: [Azure Information Protection Unified-Bezeichnungs Client und klassischer Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Azure Information Protection (AIP) ist eine cloudbasierte Lösung, die Organisationen das Klassifizieren und Schützen von Dokumenten und E-Mails durch Anwendung von Bezeichnungen ermöglicht. 

Der Administrator konfiguriert beispielsweise eine Bezeichnung mit Regeln, die vertrauliche Daten erkennen, also z. B. Kreditkarteninformationen. In diesem Fall kann jedem Benutzer, der Kreditkarteninformationen in einer Word-Datei speichert, oben im Dokument eine QuickInfo mit der Empfehlung angezeigt werden, die für dieses Szenario relevante Bezeichnung anzuwenden.

Bezeichnungen können Ihre Dokumente [klassifizieren](#how-labels-apply-classification-with-aip) und optional auch [schützen](#how-aip-protects-your-data). Damit erhalten Sie folgende Möglichkeiten:

- **Nachverfolgen und Steuern** der Verwendung Ihrer Inhalte
- **Analysieren von Datenflüssen** zum Gewinnen von Erkenntnissen zum Geschäft **– Erkennen von riskanten Verhaltensweisen** und Ergreifen von Korrekturmaßnahmen
- **Nachverfolgen des Dokumentzugriffs** und Verhindern von Datenlecks oder Datenmissbrauch
- Und vieles mehr...

## <a name="how-labels-apply-classification-with-aip"></a>So wenden Bezeichnungen mit AIP Klassifizierungen an

Das bezeichnen ihres Inhalts mit AIP umfasst Folgendes:

- Die **Klassifizierung**, die unabhängig davon erkannt werden kann, wo die Daten gespeichert oder von wem sie freigegeben werden
- **Visuelle Kennzeichnungen**, z. b. Kopfzeilen, Fußzeilen oder Wasserzeichen.
- **Metadaten**, in Klartext zu Dateien und e-Mail-Headern hinzugefügt. Dieser Klartextmetadaten stellen sicher, dass andere Dienste die Klassifizierung identifizieren und entsprechende Maßnahmen ergreifen können.

In der folgenden Abbildung hat die Bezeichnung z. b. eine e-Mail-Nachricht als *Allgemein* klassifiziert:

:::image type="content" source="media/example-email-footerv2.png" alt-text="E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung":::

In diesem Beispiel hat die Bezeichnung auch folgende Schritte durchgeführt:

- **Der e-Mail-Nachricht wurde eine Fußzeile mit *Sensitivität hinzugefügt: Allgemein***. Dieser Fußzeile ist ein visueller Indikator für alle Empfänger, das allgemeine Unternehmensdaten nicht an Empfänger außerhalb der Organisation gesendet werden dürfen.
- **Eingebettete Metadaten in den e-Mail-Headern**. Headerdaten ermöglichen es E-Mail-Diensten, die Bezeichnung zu überprüfen und theoretisch einen Überwachungseintrag zu erstellen oder zu verhindern, dass sie außerhalb der Organisation versendet wird.

Bezeichnungen können von Administratoren automatisch mithilfe von Regeln und Bedingungen, manuell von Benutzern oder mithilfe einer Kombination angewendet werden, in der Administratoren die Empfehlungen definieren, die Benutzern angezeigt werden.

## <a name="how-aip-protects-your-data"></a>So schützt AIP Ihre Daten

Azure Information Protection verwendet den [*Azure Rights Management-Dienst* (Azure RMS)](what-is-azure-rms.md), um Ihre Daten zu schützen. 

Azure RMS ist mit anderen Microsoft-Clouddiensten und -Anwendungen integriert, z. B. Office 365 und Azure Active Directory, und kann auch mit Ihren eigenen Anwendungen oder Drittanbieteranwendungen sowie Information Protection-Lösungen verwendet werden. Azure RMS funktioniert sowohl mit lokalen Lösungen als auch mit Cloudlösungen.

Azure RMS verwendet Verschlüsselung, Identitäten und Autorisierungsrichtlinien. Ähnlich wie bei AIP-Bezeichnungen bleibt der durch Azure RMS angewendete Schutz in den Dokumenten und E-Mails unabhängig vom Speicherort der Dokumente oder der E-Mails. So wird sichergestellt, dass Sie die Kontrolle über Ihre Inhalte behalten, auch wenn diese mit anderen Benutzern geteilt werden.

Für Schutzeinstellungen kann Folgendes gelten:

- **Teil ihrer** Bezeichnungs Konfiguration, sodass Benutzer Dokumente und e-Mails einfach durch Anwenden einer Bezeichnung klassifizieren und schützen. 
- Wird eigenständig von Anwendungen und Diensten **verwendet**, die den Schutz unterstützen, aber keine Bezeichnung. 

    Für Anwendungen und Dienste, die nur den Schutz unterstützen, werden die Schutzeinstellungen als [Rights Management-Vorlagen](#rights-management-templates) verwendet.

Beispielsweise sollten Sie ein Berichtsdokument oder eine Tabelle mit Verkaufsprognosen so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können. In diesem Fall würden Sie Schutzeinstellungen anwenden, um zu steuern, ob das Dokument bearbeitet werden kann, es auf den Schreibschutz einschränken, oder verhindern, dass es gedruckt wird.

E-Mails können ähnliche Schutzeinstellungen aufweisen, um zu verhindern, dass sie weitergeleitet werden oder die Option „Alle antworten“ verwendet wird.

### <a name="rights-management-templates"></a>Rights Management-Vorlagen

Sobald der Azure Rights Management-Dienst aktiviert ist, stehen Ihnen zwei Standardvorlagen für die Rechteverwaltung zur Verfügung, mit denen Sie den Datenzugriff auf Benutzer innerhalb Ihrer Organisation beschränken können. Verwenden Sie diese Vorlagen sofort, oder konfigurieren Sie eigene Schutzeinstellungen, um restriktivere Kontrollen in neuen Vorlagen anzuwenden.

Rights Management-Vorlagen können in beliebigen Anwendungen oder Diensten verwendet werden, die Azure Rights Management unterstützen.

Die folgende Abbildung zeigt ein Beispiel aus dem Exchange Admin Center, in dem Sie z. B. Exchange Online-E-Mail-Flussregeln für die Verwendung der RMS-Vorlagen konfigurieren können:

:::image type="content" source="media/templates-exchangeonline-callouts.png" alt-text="Beispiel für die Auswahl von Vorlagen für Exchange Online":::

> [!NOTE]
> Beim Erstellen einer AIP-Bezeichnung, die Schutzeinstellungen enthält, wird auch eine entsprechende Rights Management-Vorlage erstellt, die separat von der Bezeichnung verwendet werden kann. 
>  

Weitere Informationen finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md)

## <a name="aip-and-end-user-integration-for-documents-and-emails"></a>AIP- und Endbenutzerintegration für Dokumente und E-Mails

Der AIP-Client installiert die Information Protection-Leiste in Office-Anwendungen und ermöglicht es Endbenutzern, AIP in ihre Dokumente und E-Mails zu integrieren.

Beispielsweise in Excel:

![Beispiel für die Azure Information Protection-Leiste in Excel](./media/excelproplus-infoprotect-bar.png)

Obwohl Bezeichnungen automatisch auf Dokumente und E-Mails angewendet werden können, Unwägbarkeiten für Benutzer entfernt oder die Richtlinien einer Organisation eingehalten werden können, ermöglicht es die Information Protection-Leiste Endbenutzern, selbst Bezeichnungen auszuwählen und Klassifizierungen anzuwenden.

Außerdem ermöglicht der AIP-Client Benutzern das gleichzeitige Klassifizieren und Schützen zusätzlicher Dateitypen oder mehrerer Dateien über das Kontextmenü in Windows-Explorer. Beispiel:

:::image type="content" source="media/right-click-classify-protect-folder.png" alt-text="Klassifizieren und Schützen über das Explorer-Kontextmenü mithilfe von Azure Informationen Protection":::

Die Menüoption **Klassifizieren und schützen** funktioniert ähnlich wie die Information Protection-Leiste in Office-Anwendungen, wodurch Benutzer eine Bezeichnung auswählen oder benutzerdefinierte Berechtigungen festlegen können.

> [!TIP]
> Hauptbenutzer (oder Administratoren) finden die Verwendung von PowerShell-Befehlen zum Verwalten und Festlegen von Klassifizierung und Schutz für mehrere Dateien möglicherweise effizienter. [Relevante PowerShell-Befehle](https://docs.microsoft.com/powershell/module/azureinformationprotection) sind im Client enthalten und können auch separat installiert werden.

Benutzer und Administratoren können die Website zur Dokumentenverfolgung verwenden, um geschützte Dokumente zu überwachen, zu überwachen, wer auf sie zugreift und wann auf diese zugegriffen wird. Wenn sie einen Missbrauch vermuten, können sie auch den Zugriff auf diese Dokumente entziehen. Beispiel:

![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](./media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>Zusätzliche Integration für E-Mails

Die Verwendung von AIP mit Exchange Online bietet den zusätzlichen Vorteil, dass geschützte E-Mails an jeden Benutzer gesendet werden, wobei sichergestellt wird, dass diese die E-Mail auf jedem Gerät lesen können.

Das ist beispielsweise nützlich, wenn Sie vertrauliche Informationen an persönliche E-Mail-Adressen senden müssen, die ein **Gmail**-, **Hotmail**- oder **Microsoft**-Konto verwenden, oder wenn Benutzer kein Konto von Office 365 oder Azure AD besitzen. Diese E-Mails sollten im ruhenden Zustand und bei der Übertragung verschlüsselt und nur von den ursprünglichen Empfängern gelesen werden.

Für dieses Szenario sind die [Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) erforderlich. Wenn die Empfänger die geschützte e-Mail nicht in Ihrem integrierten e-Mail-Client öffnen können, können Sie eine einmalige Kennung verwenden, um die sensiblen Informationen in einem Browser zu lesen.

Einem Gmail-Benutzer wird möglicherweise die folgende Aufforderung in einer empfangenen E-Mail angezeigt:

:::image type="content" source="media/ome-message.png" alt-text="Meldung für Gmail-Empfänger in OME und AIP":::

Für den Benutzer, der die E-Mail sendet, sind dieselben Aktionen wie für das Senden einer geschützten E-Mail an einen Benutzer in der eigenen Organisation erforderlich. Klicken Sie dazu beispielsweise auf die Schaltfläche **Nicht weiterleiten**, die der AIP-Client dem Outlook-Menüband hinzufügen kann. 

Alternativ können Sie die Funktion **nicht weiterleiten** in eine Bezeichnung integrieren, die Benutzer auswählen können, um die Klassifizierung und den Schutz auf diese e-Mail anzuwenden. Beispiel:

![Auswählen einer Bezeichnung, für die die Option „Nicht weiterleiten“ konfiguriert ist](./media/recipients-only-label2.png)

Alternativ können Administratoren ebenfalls anhand von E-Mail-Flussregeln, bei denen Rechteschutz angewendet wird, automatisch Schutz für Benutzer gewährleisten.

Alle an diese E-Mails angefügten Office-Dokumente werden ebenfalls automatisch geschützt.

## <a name="scanning-for-existing-content-to-classify-and-protect"></a>Suchen nach vorhandenen Inhalten zum Klassifizieren und Schützen

Im Idealfall bezeichnen Sie Dokumente und E-Mails, wenn sie erstellt werden. Sie besitzen aber wahrscheinlich viele Dokumente, die entweder lokal oder in der Cloud gespeichert sind, und möchten diese auch klassifizieren und schützen.

Verwenden Sie eine der folgenden Methoden, um vorhandene Inhalte zu klassifizieren und zu schützen:

- **Lokaler Speicher:** Verwenden Sie die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md), um Dokumente in Netzwerkfreigaben und Microsoft SharePoint Server-Standorten und -Bibliotheken zu erkennen, zu klassifizieren und zu schützen.

    Die Überprüfung wird als Dienst auf Windows Server ausgeführt und verwendet die gleichen Richtlinienregeln, um vertrauliche Informationen zu erkennen und bestimmte Bezeichnungen auf Dokumente anzuwenden. 

    Verwenden Sie die Überprüfung alternativ, um Standardbezeichnung auf alle Dokumente in einem Datenrepository anzuwenden, ohne den Inhalt der Datei zu überprüfen. Zudem haben Sie die Möglichkeit, die Überprüfung auch nur im Berichterstellungsmodus zu verwenden, um vertrauliche Daten zu finden, von denen Sie vielleicht nicht wissen, dass sie vorhanden sind.

- **Clouddatenspeicher:** Verwenden Sie [Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/azip-integration), um Ihre Bezeichnungen für Dokumente in Box, SharePoint und OneDrive anzuwenden. Ein zugehöriges Tutorial finden Sie unter [Automatisches Anwenden von Azure Information Protection-Klassifizierungsbezeichnungen](https://docs.microsoft.com/cloud-app-security/use-case-information-protection). 


## <a name="next-steps"></a>Nächste Schritte

Mit unseren Schnellstart Anleitungen und Tutorials finden Sie Azure Information Protection für sich selbst.

- [Schnellstart: Bereitstellen des Clients für einheitliche Bezeichnungen](quickstart-deploy-client.md)
- [Tutorial: Installieren des Azure Information Protection-Scanners (AIP) für einheitliche Bezeichnungen](tutorial-install-scanner.md)
- [Tutorial: Erkennen vertraulicher Inhalte mit dem Azure Information Protection-Scanner (AIP)](tutorial-scan-networks-and-content.md)
- [Tutorial: Verhindern übermäßiger Freigaben in Outlook mit Azure Information Protection (AIP)](tutorial-preventing-oversharing.md)

Wenn Sie schon soweit sind, dass Sie diesen Dienst für Ihre Organisation bereitstellen möchten, wechseln Sie direkt zu den [Schrittanleitungen](how-to-guides.md).
