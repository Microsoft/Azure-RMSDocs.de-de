---
title: Was ist Azure Information Protection?
description: Eine Übersicht über den Azure Information Protection-Dienst.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/16/2018
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: 22cb2afc014ce7538d7163edc3b12e7d7a137c72
ms.sourcegitcommit: 758e0cfeb6c05f4c6f5310dc36fbf0c02c256eed
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="what-is-azure-information-protection"></a>Was ist Azure Information Protection?

>*Gilt für: Azure Information Protection*

Azure Information Protection (zuweilen auch als AIP bezeichnet) ist eine cloudbasierte Lösung, die Organisationen beim Klassifizieren, Bezeichnen und Schützen von Dokumenten und E-Mails unterstützt. Dies kann automatisch durch Administratoren, die Regeln und Bedingungen definieren, manuell durch Benutzer oder durch eine Kombination beider Verfahren erfolgen, indem Benutzern Vorschläge angezeigt werden. 

Die folgende Abbildung zeigt ein Beispiel für Azure Information Protection in Aktion. Der Administrator hat Regeln zum Erkennen vertraulicher Daten (in diesem Fall Kreditkarteninformationen) konfiguriert. Wenn ein Benutzer ein Word-Dokument speichert, das Kreditkarteninformationen enthält, wird eine benutzerdefinierte QuickInfo angezeigt, in der eine bestimmte, vom Administrator konfigurierte Bezeichnung empfohlen wird,. Diese Bezeichnung klassifiziert und schützt abhängig von der Konfiguration optional das Dokument. 

![Beispiel für die empfohlene Klassifizierung mit Azure Information Protection](../media/info-protect-recommend-calloutsv2.png)

Nachdem Ihr Inhalt klassifiziert (und optional geschützt) wurde, können Sie nachverfolgen und steuern, wie er verwendet wird. Sie können die Datenflüsse analysieren, um Einblicke in Ihr Geschäft zu erhalten, riskante Verhalten zu erkennen und Korrekturmaßnahmen zu ergreifen, den Zugriff auf Dokumente zu verfolgen, Datenverluste oder Missbrauch zu verhindern usw.

## <a name="how-labels-apply-classification"></a>Wie Bezeichnungen Klassifizierungen anwenden

Sie verwenden Azure Information Protection-Bezeichnungen, um die Klassifizierung auf Dokumente und E-Mails anzuwenden. Damit ist die Klassifizierung jederzeit identifizierbar – unabhängig davon, wo die Daten gespeichert sind oder für wen sie freigegeben wurden. Die Bezeichnungen beinhalten visuelle Markierungen wie Kopfzeilen, Fußzeilen oder Wasserzeichen. Metadaten werden Datei- und E-Mail-Header als Klartext hinzugefügt. Dieser Klartext stellt sicher, dass andere Dienste (z.B. Lösungen zur Verhinderung von Datenverlusten) die Klassifizierung identifizieren und entsprechende Maßnahmen ergreifen können. 

Die folgende E-Mail-Nachricht wurde beispielsweise als „Allgemein“ klassifiziert. Diese Bezeichnung wird der E-Mail-Nachricht als eine Fußzeile hinzugefügt. Dieser Fußzeile ist ein visueller Indikator für alle Empfänger, das allgemeine Unternehmensdaten nicht an Empfänger außerhalb der Organisation gesendet werden dürfen. Die Bezeichnung wird auch in die E-Mail-Header eingebettet, sodass E-Mail-Dienste diesen Wert überprüfen können, um z.B. einen Überwachungseintrag zu erstellen oder zu verhindern, dass sie an Empfänger außerhalb der Organisation gesendet werden.

![E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung](../media/example-email-footerv2.png)


## <a name="how-data-is-protected"></a>So werden die Daten geschützt

Die Schutztechnologie verwendet *Azure Rights Management* (oft als Azure RMS abgekürzt). Diese Technologie ist in andere Microsoft-Clouddienste und -Anwendungen integriert, wie z.B. Office 365 und Azure Active Directory. Er kann auch mit Ihren eigenen Branchenanwendungen und Informationsschutzlösungen von Softwareherstellern verwendet werden. Dabei kann es sich sowohl um lokale als auch um Cloudanwendungen und -lösungen handeln.

Diese Schutztechnologie verwendet Verschlüsselung, Identitäten und Autorisierungsrichtlinien. Wie bei Bezeichnern, die angewendet werden, bleibt der mithilfe von Rights Management angewendete Schutz unabhängig vom Ort an die Dateien und E-Mails gebunden – sowohl innerhalb oder als auch außerhalb Ihrer Organisation bzw. der Netzwerke, Dateiserver und Anwendungen. Dank dieser Lösung für den Schutz von Informationen behalten Sie stets die Kontrolle über Ihre Daten, auch wenn sie für andere Personen freigegeben werden.

Beispielsweise können Sie ein Berichtsdokument oder eine Tabelle mit Verkaufsprognosen so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können, oder Sie können steuern, ob das Dokument bearbeitet werden kann oder als schreibgeschützt gilt oder ob es gedruckt werden darf. Sie können E-Mails ganz ähnlich konfigurieren und noch zusätzlich verhindern, dass sie weitergeleitet werden, bzw. die Verwendung der Option „Allen antworten“ unterbinden. 

Diese Schutzeinstellungen können Teil der Konfiguration Ihrer Bezeichnungen sein, sodass Benutzer Dokumente und E-Mails ganz einfach durch Hinzufügen einer Bezeichnung klassifizieren und schützen können. Diese Schutzeinstellungen können jedoch auch von Anwendungen und Diensten verwendet werden, die zwar den Schutz unterstützen, aber nicht die Anwendung von Bezeichnungen. Für diese Anwendungen und Dienste werden die Schutzeinstellungen als *Rights Management-Vorlagen* bereitgestellt.

### <a name="rights-management-templates"></a>Rights Management-Vorlagen

Sobald Sie den Azure Rights Management-Dienst aktivieren, stehen Ihnen zwei Standardvorlagen zur Verfügung, die den Datenzugriff auf Benutzer in Ihrer Organisation beschränken. Mit diesen Vorlagen können Sie sofort verhindern, dass Daten außerhalb Ihrer Organisation offengelegt werden. Sie können diese Standardvorlagen auch ergänzen, indem Sie eigene Schutzeinstellungen konfigurieren, durch die noch restriktivere Kontrollen angewendet werden.

Wenn Sie eine Bezeichnung für Azure Information Protection erstellen, die Schutzeinstellungen umfasst, erstellt diese Aktion im Hintergrund eine entsprechende Rights Management-Vorlage. Sie können diese Vorlage dann zusätzlich in Anwendungen und Diensten verwenden, die Azure Rights Management unterstützen.

Im Exchange Admin Center können Sie z.B. Exchange Online-E-Mail-Flussregeln für die Verwendung dieser Vorlagen konfigurieren:

![Beispiel für die Auswahl von Vorlagen für Exchange Online](../media/templates-exchangeonline-callouts.png)

Weitere Informationen zum Azure Rights Management-Schutz finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md).

## <a name="integration-with-end-user-workflows-for-documents-and-emails"></a>Integration in Endbenutzerworkflows für Dokumente und E-Mails

Azure Information Protection kann in vorhandene Endbenutzer-Workflows integriert werden, wenn der Azure Information Protection-Client installiert ist. Dieser Client installiert die Information Protection-Leiste für Office-Anwendungen, die in der ersten Abbildung zu sehen war, auf der die Leiste in Word angezeigt wird. Dieselbe Leiste wird in Information Protection, Excel, PowerPoint und Outlook hinzugefügt. Beispiel:

![Beispiel für die Azure Information Protection-Leiste in Excel](../media/excel2016-infoprotect-barv2.png)

Diese Information Protection-Leiste erleichtert es dem Endbenutzer, Bezeichnungen für die richtige Klassifizierung auszuwählen. Bei Bedarf können Bezeichnungen auch automatisch angewendet werden, um Unwägbarkeiten für Benutzer zu entfernen, und damit sie mit den Richtlinien Ihrer Organisation übereinstimmen.

Benutzer können mit der rechten Maustaste auf Dateien oder einen Ordner im Windows-Datei-Explorer klicken, um zusätzliche Dateitypen zu klassifizieren und zu schützen sowie mehrere Dateien gleichzeitig zu unterstützen:

![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](../media/right-click-classify-protect-folder.png)

Wenn ein Benutzer die Menüoption **Klassifizieren und schützen** im Datei-Explorer auswählt, dann kann er eine Bezeichnung auf ähnliche Weise wie über die Information Protection-Leiste in seinen Office-Desktopanwendungen auswählen. Sie können bei Bedarf auch ihre eigenen benutzerdefinierten Berechtigungen festlegen.

Hauptbenutzer (und Administratoren) finden die Verwendung von PowerShell-Befehlen zum Verwalten und Festlegen von Klassifizierung und Schutz für mehrere Dateien möglicherweise effizienter. Die für diese Aktionen erforderlichen PowerShell-Befehle sind automatisch mit dem Client verfügbar, obwohl Sie das PowerShell-Modul auch separat installieren können.

Nachdem ein Dokument geschützt wurde, können die Benutzer und Administratoren eine Website für die Dokumentenverfolgung verwenden, um zu überwachen, wer wann auf die Dokumente zugreift. Wenn sie eine missbräuchliche Verwendung vermuten, können sie den Zugriff auf diese Dokumente auch widerrufen:

![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](../media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>Zusätzliche Integration für E-Mails

Wenn Sie Azure Information Protection mit Exchange Online verwenden, profitieren Sie von einem weiteren Vorteil: Sie können geschützte E-Mails an Benutzer senden, mit der Gewissheit, dass sie diese auf jedem Gerät lesen können.

Dies ist beispielsweise nützlich, wenn Benutzer über ein **Gmail**-, **Hotmail**- oder **Microsoft**-Konto vertrauliche Informationen an persönliche E-Mail-Konten senden müssen. Auch für Benutzer, die kein Office 365- oder Azure AD-Konto besitzen, ist dies hilfreich. Diese E-Mails sollten im ruhenden Zustand und bei der Übertragung verschlüsselt und nur von den ursprünglichen Empfängern gelesen werden.

Für dieses Szenario sind die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) erforderlich. Wenn die Empfänger die geschützte E-Mail nicht in ihrem nativen E-Mail-Client öffnen können, können sie die vertraulichen Informationen mithilfe einer Einmalkennung in einem Browser lesen.

Ein Gmail-Benutzer sieht z.B. den folgenden Inhalt in einer E-Mail-Nachricht:

![Option für Gmail-Empfänger in OME und AIP](../media/ome-message.png)

Geschützte E-Mails, die an einen Benutzer in derselben Organisation gerichtet sind, werden über den gewohnten Workflow zum Senden von E-Mails gesendet. Beispielsweise können sie die Schaltfläche **Nicht weiterleiten** auswählen, die der Azure Information Protection-Client dem Outlook-Menüband hinzufügen kann. Die Funktion „Nicht weiterleiten“ kann auch in eine für Benutzer auswählbare Bezeichnung integriert werden, sodass die E-Mail klassifiziert und geschützt wird:

![Auswählen einer Bezeichnung, für die die Option „Nicht weiterleiten“ konfiguriert ist](../media/recipients-only-label.png)

Alternativ können Sie anhand von E-Mail-Flussregeln, bei denen Rechteschutz angewendet wird, automatisch Schutz für Benutzer gewährleisten. 

Wenn Sie Office-Dokumente an diese E-Mails anhängen, werden diese Dokumente ebenfalls automatisch geschützt.

## <a name="resources-for-azure-information-protection"></a>Ressourcen für Azure Information Protection

- Kostenlose Testversion: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Download des Clients: [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- Download des anpassbaren Benutzerhandbuchs: [Azure Information Protection End User Adoption Guide (Benutzerhandbuch für die Einführung in Azure Information Protection)](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

- Häufig gestellte Fragen: [Häufig gestellte Fragen zu Azure Information Protection](../get-started/faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/AskIPTeam)


Darüber hinaus werden bei **Microsoft Ignite 2017** viele auf Abruf verfügbare Sitzungen für Azure Information Protection zur Verfügung gestellt. Eine Zusammenfassung der Ankündigungen, die auf dieser Konferenz stattgefunden haben, finden Sie unter [What’s new in Azure Information Protection @ Ignite 2017 (Neues in Azure Information Protection @ Ignite 2017)](https://cloudblogs.microsoft.com/ENTERPRISEMOBILITY/2017/09/27/whats-new-in-azure-information-protection-ignite-2017/). 

Sie können die Sitzungen [suchen und finden](https://myignite.microsoft.com/videos?q=%2522azure%2520information%2520protection%2522), die für Azure Information Protection auf der Ignite-Website gekennzeichnet sind. Jedoch empfiehlt es sich, mit den folgenden Sitzungen zu beginnen:

- [Protecting complete data lifecycle using Microsoft information protection capabilities (Schützen des gesamten Datenlebenszyklus mithilfe der Microsoft Information Protection-Funktionen)](https://myignite.microsoft.com/videos/55397)

- [Accelerate Azure information protection deployment and adoption (Beschleunigen der Azure Information Protection-Bereitstellung und Einführung)](https://myignite.microsoft.com/videos/53454)

- [Discover what’s new in Azure Information Protection and learn about the roadmap and strategy (Erkunden, was es Neues zu Azure Information Protection gibt sowie Informationen zur Roadmap und Strategie)](https://myignite.microsoft.com/videos/53453)

- [Encryption key management strategies for compliance (Verwaltungsstrategien für die Konformität von Verschlüsselungsschlüsseln)](https://myignite.microsoft.com/videos/53455)

- [Protect and control your sensitive emails with new Office 365 Message Encryption capabilities (Schützen und Steuern Ihrer vertraulichen E-Mails mit den neuen Funktionen der Office 365-Nachrichtenverschlüsselung)](https://myignite.microsoft.com/videos/53230)


## <a name="next-steps"></a>Nächste Schritte

Lesen Sie den Blogbeitrag [Azure Information Protection: Ready, set, protect! (Azure Information Protection: Auf die Plätze, Fertig, Schützen!)](https://cloudblogs.microsoft.com/enterprisemobility/2017/02/21/azure-information-protection-ready-set-protect/).

Konfigurieren und testen Sie Azure Information Protection selbst mit dem [Schnellstarttutorial](../get-started/infoprotect-quick-start-tutorial.md) in fünf Schritten. Wenn Sie hingegen Azure Information Protection für Ihre Organisation bereitstellen möchten, finden Sie weiterführende Informationen in der [Roadmap für die Bereitstellung von Azure Information Protection](../plan-design/deployment-roadmap.md).

Es kann sein, dass Sie Azure Informationen Protection nur unter einem anderen Namen kennen. Dann finden Sie weitere Informationen dazu in [der Liste alternativer Benennungen für den Dienst](azure-rms-aka.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
