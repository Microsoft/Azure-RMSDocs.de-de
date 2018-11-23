---
title: Was ist Azure Information Protection?
description: Eine Übersicht über den Azure Information Protection-Dienst.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/05/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: cd8a88e2-3555-4be2-9637-3cdee992f2c8
ms.openlocfilehash: 979f0acfc2177ba05e57f7c36d5bf3ca3840a65f
ms.sourcegitcommit: 80de8762953bdea2553c48b02259cd107d0c71dd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/05/2018
ms.locfileid: "51026690"
---
# <a name="what-is-azure-information-protection"></a>Was ist Azure Information Protection?

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Azure Information Protection (zuweilen auch als AIP bezeichnet) ist eine cloudbasierte Lösung, die Organisationen beim Klassifizieren und optional auch beim Schützen von Dokumenten und E-Mails durch die Anwendung von Bezeichnungen unterstützt. Bezeichnungen können automatisch durch Administratoren, die Regeln und Bedingungen definieren, manuell durch Benutzer oder durch eine Kombination beider Verfahren angewendet werden, indem Benutzern Empfehlungen angezeigt werden. 

Die folgende Abbildung zeigt ein Beispiel für Azure Information Protection in Aktion auf dem Computer eines Benutzers. Der Administrator hat eine Bezeichnung mit Regeln konfiguriert, die sensible Daten erkennen (in unserem Beispiel sind dies Kreditkarteninformationen). Wenn ein Benutzer ein Word-Dokument speichert, das eine Kreditkartennummer enthält, wird eine benutzerdefinierte QuickInfo angezeigt, in der die vom Administrator konfigurierte Bezeichnung empfohlen wird. Diese Bezeichnung klassifiziert das Dokument und schützt es. 

![Beispiel für die empfohlene Klassifizierung mit Azure Information Protection](./media/info-protect-recommend-calloutsv2.png)

Nachdem Ihr Inhalt klassifiziert (und optional geschützt) wurde, können Sie nachverfolgen und steuern, wie er verwendet wird. Sie können die Datenflüsse analysieren, um Einblicke in Ihr Geschäft zu erhalten, riskante Verhalten zu erkennen und Korrekturmaßnahmen zu ergreifen, den Zugriff auf Dokumente zu verfolgen, Datenverluste oder Missbrauch zu verhindern usw.

## <a name="how-labels-apply-classification"></a>Wie Bezeichnungen Klassifizierungen anwenden

Sie verwenden Azure Information Protection-Bezeichnungen, um die Klassifizierung auf Dokumente und E-Mails anzuwenden. Damit ist die Klassifizierung identifizierbar – unabhängig davon, wo die Daten gespeichert sind oder für wen sie freigegeben wurden. Die Bezeichnungen können optische Kennzeichnungen wie Kopfzeilen, Fußzeilen oder Wasserzeichen enthalten. Metadaten werden Datei- und E-Mail-Header als Klartext hinzugefügt. Dieser Klartext stellt sicher, dass andere Dienste (z.B. Lösungen zur Verhinderung von Datenverlusten) die Klassifizierung identifizieren und entsprechende Maßnahmen ergreifen können. 

Die folgende E-Mail-Nachricht wurde beispielsweise als „Allgemein“ klassifiziert. Die Bezeichnung hat eine Fußzeile „Vertraulichkeit: Allgemein“ zur E-Mail-Nachricht hinzugefügt. Dieser Fußzeile ist ein visueller Indikator für alle Empfänger, das allgemeine Unternehmensdaten nicht an Empfänger außerhalb der Organisation gesendet werden dürfen. Die Bezeichnung wird in die E-Mail-Header eingebettet, sodass E-Mail-Dienste diesen Wert überprüfen können, um z.B. einen Überwachungseintrag zu erstellen oder zu verhindern, dass sie an Empfänger außerhalb der Organisation gesendet werden.

![E-Mail-Beispielfußzeile und -header mit der Azure Information Protection-Klassifizierung](./media/example-email-footerv2.png)


## <a name="how-data-is-protected"></a>So werden die Daten geschützt

Die Schutztechnologie verwendet *Azure Rights Management* (oft als Azure RMS abgekürzt). Diese Technologie ist in andere Microsoft-Clouddienste und -Anwendungen integriert, wie z.B. Office 365 und Azure Active Directory. Er kann auch mit Ihren eigenen Branchenanwendungen und Informationsschutzlösungen von Softwareherstellern verwendet werden. Dabei kann es sich sowohl um lokale als auch um Cloudanwendungen und -lösungen handeln.

Diese Schutztechnologie verwendet Verschlüsselung, Identitäten und Autorisierungsrichtlinien. Wie bei Bezeichnern, die angewendet werden, bleibt der mithilfe von Rights Management angewendete Schutz unabhängig vom Ort an die Dateien und E-Mails gebunden – sowohl innerhalb oder als auch außerhalb Ihrer Organisation bzw. der Netzwerke, Dateiserver und Anwendungen. Dank dieser Lösung für den Schutz von Informationen behalten Sie stets die Kontrolle über Ihre Daten, auch wenn sie für andere Personen freigegeben werden.

Beispielsweise können Sie ein Berichtsdokument oder eine Tabelle mit Verkaufsprognosen so konfigurieren, dass nur Personen in Ihrer Organisation darauf zugreifen können, oder Sie können steuern, ob das Dokument bearbeitet werden kann oder als schreibgeschützt gilt oder ob es gedruckt werden darf. Sie können E-Mails ganz ähnlich konfigurieren und noch zusätzlich verhindern, dass sie weitergeleitet werden, bzw. die Verwendung der Option „Allen antworten“ unterbinden. 

Diese Schutzeinstellungen können Teil der Konfiguration Ihrer Bezeichnungen sein, sodass Benutzer Dokumente und E-Mails ganz einfach durch Hinzufügen einer Bezeichnung klassifizieren und schützen können. Diese Schutzeinstellungen können jedoch auch von Anwendungen und Diensten verwendet werden, die zwar den Schutz unterstützen, aber nicht die Anwendung von Bezeichnungen. Für diese Anwendungen und Dienste werden die Schutzeinstellungen als *Rights Management-Vorlagen* bereitgestellt.

### <a name="rights-management-templates"></a>Rights Management-Vorlagen

Sobald der Azure Rights Management-Dienst aktiviert ist, stehen Ihnen zwei Standardvorlagen zur Verfügung, die den Datenzugriff auf Benutzer in Ihrer Organisation beschränken. Mit diesen Vorlagen können Sie sofort verhindern, dass Daten außerhalb Ihrer Organisation offengelegt werden. Sie können diese Standardvorlagen auch ergänzen, indem Sie eigene Schutzeinstellungen konfigurieren, durch die noch restriktivere Kontrollen angewendet werden.

Wenn Sie eine Bezeichnung für Azure Information Protection erstellen, die Schutzeinstellungen umfasst, erstellt diese Aktion im Hintergrund eine entsprechende Rights Management-Vorlage. Sie können diese Vorlage dann zusätzlich in Anwendungen und Diensten verwenden, die Azure Rights Management unterstützen.

Im Exchange Admin Center können Sie z.B. Exchange Online-E-Mail-Flussregeln für die Verwendung dieser Vorlagen konfigurieren:

![Beispiel für die Auswahl von Vorlagen für Exchange Online](./media/templates-exchangeonline-callouts.png)

Weitere Informationen zum Azure Rights Management-Schutz finden Sie unter [Was ist Azure Rights Management?](what-is-azure-rms.md)

## <a name="integration-with-end-user-workflows-for-documents-and-emails"></a>Integration in Endbenutzerworkflows für Dokumente und E-Mails

Azure Information Protection kann in vorhandene Endbenutzer-Workflows integriert werden, wenn der Azure Information Protection-Client installiert ist. Dieser Client installiert die Information Protection-Leiste für Office-Anwendungen, die in der ersten Abbildung zu sehen war, auf der die Leiste in Word angezeigt wird. Dieselbe Leiste wird in Information Protection, Excel, PowerPoint und Outlook hinzugefügt. Beispiel:

![Beispiel für die Azure Information Protection-Leiste in Excel](./media/excel2016-infoprotect-barv2.png)

Diese Information Protection-Leiste erleichtert es dem Endbenutzer, Bezeichnungen für die richtige Klassifizierung auszuwählen. Bei Bedarf können Bezeichnungen auch automatisch angewendet werden, um Unwägbarkeiten für Benutzer zu entfernen, und damit sie mit den Richtlinien Ihrer Organisation übereinstimmen.

Benutzer können mit der rechten Maustaste auf Dateien oder einen Ordner im Windows-Datei-Explorer klicken, um zusätzliche Dateitypen zu klassifizieren und zu schützen sowie mehrere Dateien gleichzeitig zu unterstützen:

![Klassifizieren und Schützen über das Kontextmenü des Datei-Explorer mithilfe von Azure Informationen Protection](./media/right-click-classify-protect-folder.png)

Wenn ein Benutzer die Menüoption **Klassifizieren und schützen** im Datei-Explorer auswählt, dann kann er eine Bezeichnung auf ähnliche Weise wie über die Information Protection-Leiste in seinen Office-Desktopanwendungen auswählen. Sie können bei Bedarf auch ihre eigenen benutzerdefinierten Berechtigungen festlegen.

Hauptbenutzer (und Administratoren) finden die Verwendung von PowerShell-Befehlen zum Verwalten und Festlegen von Klassifizierung und Schutz für mehrere Dateien möglicherweise effizienter. Die für diese Aktionen erforderlichen PowerShell-Befehle sind automatisch mit dem Client verfügbar, obwohl Sie das PowerShell-Modul auch separat installieren können.

Nachdem ein Dokument geschützt wurde, können die Benutzer und Administratoren eine Website für die Dokumentenverfolgung verwenden, um zu überwachen, wer wann auf die Dokumente zugreift. Wenn sie eine missbräuchliche Verwendung vermuten, können sie den Zugriff auf diese Dokumente auch widerrufen:

![Symbol zum Widerrufen des Zugriffs auf der Website für die Dokumentenverfolgung](./media/tracking-site-revoke-access-icon.png)

### <a name="additional-integration-for-email"></a>Zusätzliche Integration für E-Mails

Wenn Sie Azure Information Protection mit Exchange Online verwenden, profitieren Sie von einem weiteren Vorteil: Sie können geschützte E-Mails an Benutzer senden, mit der Gewissheit, dass sie diese auf jedem Gerät lesen können.

Dies ist beispielsweise nützlich, wenn Benutzer vertrauliche Informationen an persönliche E-Mail-Adressen senden müssen, die ein **Gmail**-, **Hotmail**- oder **Microsoft**-Konto verwenden. Dies ist auch hilfreich, wenn vertrauliche Informationen an Benutzer gesendet werden müssen, die kein Office 365- oder Azure AD-Konto besitzen. Diese E-Mails sollten im ruhenden Zustand und bei der Übertragung verschlüsselt und nur von den ursprünglichen Empfängern gelesen werden.

Für dieses Szenario sind die [neuen Funktionen der Office 365-Nachrichtenverschlüsselung](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801) erforderlich. Wenn die Empfänger die geschützte E-Mail nicht in ihrem nativen E-Mail-Client öffnen können, können sie die vertraulichen Informationen mithilfe einer Einmalkennung in einem Browser lesen.

Ein Gmail-Benutzer sieht z.B. den folgenden Inhalt in einer E-Mail-Nachricht:

![Option für Gmail-Empfänger in OME und AIP](./media/ome-message.png)

Geschützte E-Mails, die an einen Benutzer in derselben Organisation gerichtet sind, werden über den gewohnten Workflow zum Senden von E-Mails gesendet. Beispielsweise können sie die Schaltfläche **Nicht weiterleiten** auswählen, die der Azure Information Protection-Client dem Outlook-Menüband hinzufügen kann. Die Funktion „Nicht weiterleiten“ kann auch in eine für Benutzer auswählbare Bezeichnung integriert werden, sodass die E-Mail klassifiziert und geschützt wird:

![Auswählen einer Bezeichnung, für die die Option „Nicht weiterleiten“ konfiguriert ist](./media/recipients-only-label.png)

Alternativ können Sie anhand von E-Mail-Flussregeln, bei denen Rechteschutz angewendet wird, automatisch Schutz für Benutzer gewährleisten. 

Wenn Sie Office-Dokumente an diese E-Mails anhängen, werden diese Dokumente ebenfalls automatisch geschützt.

## <a name="classifying-and-protecting-existing-documents"></a>Klassifizieren und Schützen vorhandener Dokumente

Im Idealfall werden Dokumente und E-Mails bei deren Erstellung mit einer Bezeichnung versehen. Aber Sie verfügen wahrscheinlich über viele vorhandene Dokumente in Datenspeichern und möchten diese auch klassifizieren und schützen. Diese Datenspeicher können sich in der lokalen Umgebung oder in der Cloud befinden.

Verwenden Sie für Ihre lokalen Datenspeicher die Azure Information Protection-Überprüfung, um Dokumente in lokalen Ordnern, Netzwerkfreigaben und SharePoint Server-Standorten und -Bibliotheken zu erkennen, zu klassifizieren und zu schützen. Die Überprüfung wird als Dienst unter Windows Server ausgeführt. Sie können die gleichen Regeln in der Richtlinie verwenden, um vertrauliche Informationen zu erkennen und für Dokumente spezielle Bezeichnungen anzuwenden. Oder Sie können eine Standardbezeichnung auf alle Dokumente in einem Datenrepository anwenden, ohne den Inhalt der Datei zu überprüfen. Zudem haben Sie die Möglichkeit, die Überprüfung auch nur im Berichterstellungsmodus zu verwenden, um vertrauliche Daten zu finden, von denen Sie vielleicht nicht wissen, dass sie vorhanden sind. 

Weitere Informationen zur Bereitstellung und Verwendung der Überprüfung finden Sie im Artikel zum [Bereitstellen der Azure Rights Management-Überprüfung zum automatischen Klassifizieren und Schützen von Dateien](deploy-aip-scanner.md).

Verwenden Sie für Ihre Clouddatenspeicher Microsoft Cloud App Security, um Ihre Bezeichnungen für Dokumente in Box, SharePoint Online und OneDrive for Business anzuwenden. Weitere Informationen finden Sie unter [Automatisches Anwenden von Azure Information Protection-Klassifizierungsbezeichnungen](/cloud-app-security/use-case-information-protection) und [Integration mit Azure Information Protection](/cloud-app-security/azip-integration).


## <a name="resources-for-azure-information-protection"></a>Ressourcen für Azure Information Protection

- Kostenlose Testversion: [Enterprise Mobility + Security E5](https://portal.office.com/Signup/Signup.aspx?OfferId=87dd2714-d452-48a0-a809-d2f58c4f68b7)

- Abonnementoptionen und Preise: [Preise zu Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)

- Download des Clients: [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018)

- Download des anpassbaren Benutzerhandbuchs: [Azure Information Protection End User Adoption Guide (Benutzerhandbuch für die Einführung in Azure Information Protection)](https://download.microsoft.com/download/7/1/2/712A280C-1C66-4EF9-8DC3-88EE43BEA3D4/Azure_Information_Protection_End_User_Adoption_Guide_EN_US.pdf)

- Häufig gestellte Fragen: [Häufig gestellte Fragen zu Azure Information Protection](faqs.md)

- Yammer: [Azure Information Protection](https://www.yammer.com/AskIPTeam)

Zusätzliche Ressourcen: [Informationen und Support für Azure Information Protection](information-support.md)

### <a name="microsoft-ignite"></a>Microsoft Ignite

Bei der Microsoft Ignite 2018-Konferenz in Orlando gab es viele Präsentationen zum Thema [Azure Information Protection](https://myignite.techcommunity.microsoft.com/sessions?q=Azure%2520Information%2520Protection). Alle Präsentationen wurden aufgezeichnet, wenn Sie also nicht teilnehmen konnten, können Sie sich die Präsentationen immer noch ansehen. Hier sind die besten fünf empfohlenen Präsentationen:

- [BRK2006 - Use Microsoft Information Protection (MIP) to help protect your sensitive data everywhere, throughout its lifecycle (Verwenden von Microsoft Information Protection (MIP) zum Schutz Ihrer sensiblen Daten überall und über den gesamten Lebenszyklus hinweg)](https://myignite.techcommunity.microsoft.com/sessions/64297) – sehen Sie sich das [Video auf YouTube](https://youtu.be/gmHVF-1cLXA) an.
 
- [BRK3002 - Understanding how Microsoft Information Protection capabilities work together to protect sensitive information across devices, apps, and services (Wie die Funktionen von Microsoft Information Protection zusammenarbeiten, um sensible Informationen über Geräte, Apps und Dienste hinweg zu schützen)](https://myignite.techcommunity.microsoft.com/sessions/64299) – sehen Sie sich das [Video auf YouTube](https://youtu.be/kL9Y7NGTyQQ) an.

- [BRK3009 - Accelerate deployment and adoption of Microsoft Information Protection solutions (Beschleunigen der Bereitstellung und der Einführung von Microsoft Information Protection-Lösungen)](https://myignite.techcommunity.microsoft.com/sessions/64283) – sehen Sie sich das [Video auf YouTube](https://www.youtube.com/watch?v=JsCyIVyQJmE) an.

- [BRK3397 - Protect and control your sensitive emails with Office 365 Message Encryption (Schützen und Steuern von sensiblen E-Mails mit der Nachrichtenverschlüsselung von Office 365)](https://myignite.techcommunity.microsoft.com/sessions/64327) – sehen Sie sich das [Video auf YouTube](https://www.youtube.com/watch?v=Ld4b4pFua0g) an.

- [THR2003 - Data discovery, Usage reporting and analytics for all your data with Microsoft Information Protection (Datenermittlung, Verwendungsberichte und Analysen für alle Ihre Daten mit Microsoft Information Protection)](https://myignite.techcommunity.microsoft.com/sessions/64301) – sehen Sie sich das [Video auf YouTube](https://www.youtube.com/watch?v=nzDIXd0XaeA) an.

Eine Zusammenfassung der Ankündigungen dieser Ignite-Konferenz finden Sie im Blogbeitrag [Announcing availability of information protection capabilities to help protect your sensitive data (Ankündigung der Verfügbarkeit von Information Protection-Funktionen zum Schutz Ihrer sensiblen Daten)](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Announcing-availability-of-information-protection-capabilities/ba-p/261967).


## <a name="next-steps"></a>Nächste Schritte

Konfigurieren und testen Sie Azure Information Protection selbst mit den [Schnellstarts](quickstart-viewpolicy.md) und [Tutorials](infoprotect-quick-start-tutorial.md). Wenn Sie diesen Dienst für Ihre Organisation bereitstellen möchten, können Sie auch zu den [Schrittanleitungen für häufige Szenarien](how-to-guides.md) übergehen.