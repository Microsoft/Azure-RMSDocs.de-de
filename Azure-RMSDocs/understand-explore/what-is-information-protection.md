---
title: Was ist Azure Information Protection?
description: "Eine Übersicht über den Azure Information Protection-Dienst."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/30/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: 0ca0c2aa3d7b21c3e1143af51c9518aa85b7ee93
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
<a id="what-is-azure-information-protection" class="xliff"></a>

# Was ist Azure Information Protection?

>*Gilt für: Azure Information Protection*

Azure Information Protection ist eine cloudbasierte Lösung, die Organisationen beim Klassifizieren, Bezeichnen und Schützen von Dokumenten und E-Mails unterstützt. Dies kann automatisch durch Administratoren, die Regeln und Bedingungen definieren, manuell durch Benutzer oder durch eine Kombination beider Verfahren erfolgen, indem Benutzern Vorschläge angezeigt werden. 

Die folgende Abbildung zeigt ein Beispiel für Azure Information Protection in Aktion. Der Administrator hat Regeln zum Erkennen vertraulicher Daten (in diesem Fall Kreditkarteninformationen) konfiguriert. Wenn ein Benutzer ein Word-Dokument speichert, das Kreditkarteninformationen enthält, wird eine benutzerdefinierte QuickInfo angezeigt, in der eine bestimmte, vom Administrator konfigurierte Bezeichnung empfohlen wird, die das Dokument klassifiziert und optional schützt. 

![Beispiel für die empfohlene Klassifizierung mit Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Nachdem Ihr Inhalt klassifiziert (und optional geschützt) wurde, können Sie nachverfolgen und steuern, wie er verwendet wird. Sie können die Datenflüsse analysieren, um Einblicke in Ihr Geschäft zu erhalten, riskante Verhalten zu erkennen und Korrekturmaßnahmen zu ergreifen, den Zugriff auf Dokumente zu verfolgen, Datenverluste oder Missbrauch zu verhindern usw.

<a id="how-labels-apply-classification" class="xliff"></a>

## Wie Bezeichnungen Klassifizierungen anwenden

Sie verwenden Azure Information Protection-Bezeichnungen, um die Klassifizierung auf Dokumente und E-Mails anzuwenden. Damit ist die Klassifizierung jederzeit identifizierbar – unabhängig davon, wo die Daten gespeichert sind oder für wen sie freigegeben wurden. Die Bezeichnungen beinhalten visuelle Markierungen wie Kopfzeilen, Fußzeilen oder Wasserzeichen. Metadaten werden Datei- und E-Mail-Header als Klartext hinzugefügt, sodass andere Dienste (z.B. Lösungen zur Verhinderung von Datenverlusten) die Klassifizierung identifizieren und entsprechende Maßnahmen ergreifen können. 

Die folgende E-Mail-Nachricht wurde beispielsweise als „Internal“ klassifiziert. Diese Bezeichnung wird der E-Mail-Nachricht als eine Fußzeile hinzugefügt, um als visueller Indikator für alle Empfänger anzugeben, dass sie für die interne Verwendung vorgesehen ist und nicht an Empfänger außerhalb des Unternehmens gesendet werden darf. Diese Bezeichnung wird auch in die E-Mail-Header eingebettet, sodass E-Mail-Dienste diesen Wert überprüfen können, um z.B. einen Überwachungseintrag zu erstellen oder zu verhindern, dass sie an Empfänger außerhalb der Organisation gesendet werden.

![E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung](../media/example-email-footerv2.png)


<a id="how-data-is-protected" class="xliff"></a>

## So werden die Daten geschützt

Die Schutztechnologie verwendet *Azure Rights Management* (oft als Azure RMS abgekürzt). Diese Technologie ist in andere Microsoft-Clouddienste und -Anwendungen integriert, wie z.B. Office 365 und Azure Active Directory. Er kann auch mit Ihren eigenen Branchenanwendungen und Informationsschutzlösungen von Softwareherstellern verwendet werden. Dabei kann es sich sowohl um lokale als auch um Cloudanwendungen und -lösungen handeln.

Diese Schutztechnologie verwendet Verschlüsselung, Identitäten und Autorisierungsrichtlinien. Wie bei Bezeichnern, die angewendet werden, bleibt der mithilfe von Rights Management angewendete Schutz unabhängig vom Ort an die Dateien und E-Mails gebunden – sowohl innerhalb oder als auch außerhalb Ihrer Organisation bzw. der Netzwerke, Dateiserver und Anwendungen. Dank dieser Lösung für den Schutz von Informationen behalten Sie stets die Kontrolle über Ihre Daten, auch wenn sie für andere Personen freigegeben werden.

Beispielsweise können Sie ein Berichtsdokument oder eine Tabelle mit Verkaufsprognosen so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können, oder Sie können steuern, ob das Dokument bearbeitet werden kann oder als schreibgeschützt gilt oder ob es gedruckt werden darf. Sie können E-Mails ganz ähnlich konfigurieren und noch zusätzlich verhindern, dass sie weitergeleitet werden, bzw. die Verwendung der Option „Allen antworten“ unterbinden. Diese Schutzaufgaben können mithilfe von *Rights Management-Vorlagen* vereinfacht und optimiert werden.

<a id="rights-management-templates" class="xliff"></a>

### Rights Management-Vorlagen

Sobald Sie den Azure Rights Management-Dienst aktivieren, werden zwei Standardvorlagen für Sie erstellt, die den Datenzugriff auf Benutzer in Ihrer Organisation beschränken. Mit diesen Vorlagen können Sie sofort verhindern, dass Daten außerhalb Ihrer Organisation offengelegt werden. Sie können diese Standardvorlagen auch ergänzen, indem Sie eigene benutzerdefinierten Vorlagen konfigurieren, die noch restriktivere Kontrollen anwenden.

Diese Vorlagen können Teil einer Bezeichnungskonfiguration sein – wenn also eine bestimmte Bezeichnung auf ein Dokument (oder eine E-Mail-Nachricht) angewendet wird, sind die Daten sowohl klassifiziert als auch automatisch geschützt. Die Vorlagen können auch von Benutzern oder Administratoren in Produkten und Diensten, die die Azure Rights Management-Technologie unterstützen, ausgewählt werden.

Dieses Beispiel zeigt, wie Sie eine Vorlage für eine Bezeichnung auswählen, wenn Sie die Azure Information Protection-Richtlinie im Azure-Portal konfigurieren:

![Beispiel für die Auswahl von Vorlagen im Azure-Portal](../media/info-protect-template-callout.png)

Dieselben Vorlagen können über das Exchange Admin Center ausgewählt werden, um Regeln für den E-Mail-Fluss in Exchange Online, das die Azure Rights Management-Technologie unterstützt, zu konfigurieren:

![Beispiel für die Auswahl von Vorlagen für Exchange Online](../media/templates-exchangeonline-callouts.png)

Weitere Informationen zum Azure Rights Management-Schutz finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md).

<a id="integration-with-end-user-workflows" class="xliff"></a>

## Integration in Endbenutzer-Workflows

Azure Information Protection kann in vorhandene Endbenutzer-Workflows integriert werden, wenn der Azure Information Protection-Client installiert ist. Dieser Client installiert die Information Protection-Leiste für Office-Anwendungen, die in der ersten Abbildung zu sehen war. Dieselbe Leiste wird in Excel, PowerPoint und Outlook hinzugefügt. Beispiel:

![Beispiel für die Azure Information Protection-Leiste in Excel](../media/excel2016-infoprotect-barv2.png)

Diese Information Protection-Leiste vereinfacht die Auswahl der Bezeichnungen für die richtige Klassifizierung für die Endbenutzer. Bei Bedarf können diese Bezeichnungen auch automatisch ihre Dokumente und E-Mails schützen.

Benutzer können mit der rechten Maustaste auf Dateien oder einen Ordner im Windows-Datei-Explorer klicken, um zusätzliche Dateitypen zu klassifizieren und zu schützen sowie mehrere Dateien gleichzeitig zu unterstützen:

![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

Wenn ein Benutzer die Menüoption **Klassifizieren und schützen** im Datei-Explorer auswählt, dann kann er eine Bezeichnung auf ähnliche Weise wie über die Information Protection-Leiste in seinen Office-Desktopanwendungen auswählen. Sie können bei Bedarf auch ihre eigenen benutzerdefinierten Berechtigungen festlegen.

Hauptbenutzer (und Administratoren) finden die Verwendung von PowerShell-Befehlen zum Verwalten und Festlegen von Klassifizierung und Schutz für mehrere Dateien möglicherweise effizienter. Die dazu erforderlichen PowerShell-Befehle sind automatisch mit dem Client verfügbar, obwohl Sie das PowerShell-Modul auch separat installieren können.

Nachdem ein Dokument geschützt wurde, können die Benutzer und Administratoren eine Website für die Dokumentenverfolgung verwenden, um zu überwachen, wer wann auf die Dokumente zugreift. Wenn sie eine missbräuchliche Verwendung vermuten, können sie den Zugriff auf diese Dokumente auch widerrufen:

![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](../media/tracking-site-revoke-access-icon.png)


<a id="resources-for-azure-information-protection" class="xliff"></a>

## Ressourcen für Azure Information Protection

- Ankündigung: [Azure Information Protection ist jetzt allgemein verfügbar](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/04/azure-information-protection-is-now-generally-available/)

- Kostenlose Testversion: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Download des Clients: [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- Häufig gestellte Fragen: [Häufig gestellte Fragen zu Azure Information Protection](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/askipteam/#/threads/inGroup?type=in_group&feedId=8652489&view=all)

- Video: „Top 5 Tips for Information Protection“ (Die 5 besten Tipps für Information Protection)

    <iframe width="560" height="315" src="https://www.youtube.com/embed/GWcnZFMPcnE" frameborder="0" allowfullscreen></iframe>

    Darüber hinaus bietet Microsoft Ignite 2016 viele auf Abruf verfügbare Sitzungen für Azure Information Protection:

    - [BRK2127: Adopt a comprehensive identity-driven solution for protecting and sharing data securely (BRK2127: Einführen einer umfassenden identitätsgesteuerten Lösung für den Schutz und die sichere Freigabe von Dateien)](https://myignite.microsoft.com/videos?q=BRK2127)
    
    - [THR2107: Collaborate securely using Azure Information Protection (THR2107: Sichere Zusammenarbeit mithilfe von Azure Information Protection)](https://myignite.microsoft.com/videos?q=THR2107)
    
    - [THR2108: Ensure comprehensive protection of your data with Azure Information Protection (THR2108: Sicherstellen des umfassenden Schutzes Ihrer Daten mit Azure Information Protection)](https://myignite.microsoft.com/videos?q=THR2108)
    
    - [BRK3095: Learn how classification, labeling, and protection delivers persistent data protection (BRK3095: Erlernen, wie Klassifizierung, Bezeichnung und Schutz persistenten Datenschutz bieten)](https://myignite.microsoft.com/videos?q=BRK3095)
    
    - [BRK2128: Send secure email to anyone with the power of Microsoft Office 365 and Azure Information Protection (BRK2128: Senden von sicheren E-Mails mithilfe von Microsoft Office 365 und Azure Information Protection)](https://myignite.microsoft.com/videos?q=BRK2128)


<a id="next-steps" class="xliff"></a>

## Nächste Schritte

Lesen Sie den Blogbeitrag [Azure Information Protection: Ready, set, protect! (Azure Information Protection: Auf die Plätze, Fertig, Schützen!)](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/21/azure-information-protection-ready-set-protect/).

Konfigurieren und testen Sie Azure Information Protection selbst mit dem [Schnellstarttutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md) in fünf Schritten.

Kennen Sie vielleicht Azure Information Protection oder Azure Rights Management unter einem anderen Namen? Weitere Informationen dazu finden Sie in [unserer Liste alternativer Benennungen für den Dienst](azure-rms-aka.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]