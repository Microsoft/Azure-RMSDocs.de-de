---
title: "Handbuch für die Schnellbereitstellung von Azure Rights Management | Azure Information Protection"
description: "Ein Leitfaden, der Sie bei der schnelleren Bereitstellung und Verwendung des Azure Rights Management-Diensts zum Schutz der Daten Ihrer Organisation unterstützt. Treffen Sie zuerst eine Auswahl aus einer Liste mit spezifischen Szenarios für die Implementierung."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: c994d616-cff6-4930-9228-a7f7d198a160
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: ffed64826982756072456be18cced0226b6bb6cc
ms.openlocfilehash: abe3de4cb972053179a87023c91509168ffeffc4


---

# <a name="rapid-deployment-guide-for-azure-rights-management"></a>Handbuch für die Schnellbereitstellung von Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Verwenden Sie dieses Handbuch ergänzend zu den Konfigurationsinformationen im Abschnitt **Bereitstellen und Verwenden**, damit Sie eine Lösung für den ausschließlichen Schutz schneller bereitstellen können, die den Azure Rights Management-Dienst von Azure Information Protection verwendet. Treffen Sie eine Auswahl aus einer Liste mit spezifischen Szenarien für die Implementierung.

> [!NOTE]
> Zu diesem Zeitpunkt enthält das Handbuch Szenarien für den ausschließlichen Schutz und keine Szenarien für die Klassifizierung und den Schutz oder den Azure Information Protection-Client. 

Diese Szenarien enthalten sowohl Anweisungen für Administratoren als auch eine entsprechende Dokumentation für die Endbenutzer. Bevor Sie die Dokumentation (Anweisungen oder Ankündigungen) an die Endbenutzer weitergeben, müssen Sie sie an Ihre geschäftlichen Anforderungen und Arbeitsabläufe anpassen. Ein Beispielsatz mit Anweisungen oder eine Ankündigung zeigt, wie die endgültigen Endbenutzerdokumentation aussehen könnte.

Jedes Szenario umfasst eine Liste der Anforderungen mit Links zu weiteren Informationen (bei Bedarf), damit Sie diese Lösungen unabhängig voneinander und in beliebiger Reihenfolge bereitstellen können.

Die hier aufgeführten Szenarien sind ein Beispiel für die gängigsten Lösungen. Da Azure Information Protection zum Schutz von Informationen in einer Vielzahl von Szenarios sowohl innerhalb einer Organisation als auch organisationsübergreifend verwendet werden kann, können Sie Ihre eigenen Szenarios definieren und für Ihre Umgebung und Ihre Benutzer mithilfe des gleichen Modells bereitstellen. Durch die Fokussierung auf bestimmte Szenarios wird Ihre Azure Information Protection-Bereitstellung genauer auf Ihre geschäftlichen Ziele ausgerichtet. Darüber hinaus neigen Benutzer unserer Erfahrung nach dazu, szenariospezifische Anweisungen erheblich strikter und systematischer zu befolgen als allgemeinen Leitfaden, wie "Schützen Sie vertrauliche Dokumente".

Vor der Einführung dieser Lösungen empfiehlt es sich, Endbenutzern eine umfangreiche Ankündigung zu senden, in der Sie sie bezüglich der bevorstehenden Änderungen zum Schutz von Unternehmensdaten informieren. Weisen Sie sie außerdem darauf hin, dass dadurch auch Änderungen ihrerseits erforderlich sein können. Eine Beispielkommunikation finden Sie nach der folgenden Tabelle.

Wenn Sie Fragen und Kommentare zu diesem Handbuch haben, nutzen Sie die Feedback-Mechanismen auf dieser Seite, oder senden Sie eine E-Mail an [AskIPTeam@Microsoft.com](mailto:%20askipteam@microsoft.com?subject=Rapid%20Deployment%20Guide%20feedback).

## <a name="scenarios-for-azure-information-protection"></a>Szenarios für Azure Information Protection
Damit Sie Azure Information Protection schneller bereitstellen können, um bestimmte Geschäftsprobleme zu lösen, wählen Sie die Szenarios aus, die Ihren Unternehmenszielen am nächsten kommen, und passen Sie sie gegebenenfalls an.



**Sie senden eine Office-Datei sicher an Benutzer in einer anderen Organisation, wobei Sie die daraus resultierenden Zugriffe verfolgen können (B2B-Zusammenarbeit)**

Beispiele:

- Senden einer Preisliste, Roadmap oder Versionspläne an einen Kunden

- Senden eines Arbeitsauftrags oder einer Marketingspezifikation an einen Anbieter

- Senden eines Angebots oder einer Angebotsanforderung an einen Partner

Siehe: [Szenario – Freigeben einer Office-Datei für Benutzer in einer anderen Organisation](scenario-share-office-file-externally.md)

**Sie möchten sicherstellen, dass in einer SharePoint-Bibliothek gespeicherte Dokumente unter Ihrer Kontrolle bleiben**

Beispiele:

- Abteilungsspezifische Kalkulationstabellen und Berichte.

- Teamübergreifende Zusammenarbeit zum Erstellen von Dokumenten oder Erbringen anderer Leistungen

Siehe: [Szenario – Beibehalten der Kontrolle über in SharePoint gespeicherte Dokumente](scenario-sharepoint.md)

**Führungskräfte sollen vertrauliche Informationen sicher per E-Mail austauschen können**

Beispiele:

- Freigeben von Übernahmeplänen

- Diskutieren oder Verbreiten rechtlicher Probleme

- Informationen zu möglichen Kündigung oder anderen sensiblen Themen

Siehe: [Szenario – Führungskräfte tauschen vertrauliche Informationen sicher aus](scenario-executives-email.md)

**Sie möchten automatisch alle Dateien auf einem Dateiserver schützen**

Beispiele:

- CAD-Dokumente, die interne aufbewahrt werden müssen, um den Verlust von geistigem Eigentum zu verhindern

- Marketingpläne und Datumsangaben, die geheim gehalten werden müssen, um einen Wettbewerbsvorteil sicherzustellen

Siehe: [Szenario - Dateien auf einer Dateiserverfreigabe schützen](scenario-fci.md)

**Sie möchten Ihre hochvertraulichen, geschäftskritischen Dokumente besonders schützen**

Beispiele:

- Spezielle Rezepte oder Formeln Ihres Unternehmens

- Hochvertrauliche Übernahme- oder Fusionspläne

- Informationen zur Erkundung von natürlichen Ressourcen

Siehe: [Szenario – Schutz Ihrer wertvollsten Dateien](scenario-secure-most-valuable-files.md)

**Sie möchten vertrauliche geschäftliche E-Mails und Anlagen senden**

Beispiele:

- Zielsetzung des Unternehmens

- Organigramme, Mitteilungen bezüglich einer Umstrukturierung oder Angebotsankündigungen

- Informationen zu Unternehmensrichtlinien

Siehe: [Szenario – Vertrauliche geschäftliche E-Mail senden](scenario-company-confidential-email.md)

**Sie möchten Office-Dateien in Arbeitsordnern dauerhaft schützen**

Beispiele:

- Lokal bearbeitete Word-Dokumente für ein vertrauliche Unternehmensprojekte

- Lokal erstellte Arbeitsblätter, die vertrauliche oder geschäftskritische Daten enthalten

- Lokal gespeicherte, in Arbeit befindliche PowerPoint-Präsentationen, die bis zur Fertigstellung weder durchsickern oder versehentlich an Personen außerhalb der Organisation weitergegeben werden dürfen.

Siehe: [Szenario – Arbeitsordner für dauerhaften Schutz konfigurieren](scenario-work-folders.md)




## <a name="announcement-for-users-before-rollout"></a>Ankündigung für Benutzer vor der Einführung
Sie können als Beispiel die folgende Mitteilung verwenden, um Benutzer zu informieren, dass mit der Bereitstellung von Azure Information Protection verschiedene Änderungen auf sie zukommen. Kopieren Sie den folgenden Text, und fügen Sie ihn in eine E-Mail ein. Lassen Sie diese von einer Ihrer Führungskräfte, vorzugsweise Ihrem Geschäftsführer, an alle Mitarbeiter senden. Ändern Sie den Text gegebenenfalls, um die Nachricht auf die Mitarbeiter Ihrer Organisation abzustimmen.

![Beispiel-Benutzerdokumentationsbanner für die schnelle Bereitstellung von Azure RMS](../media/AzRMS_ExampleBanner.png)

### <a name="changes-were-making-to-safeguard-our-data"></a>Bevorstehende Änderungen zum Schutz unserer Daten
Haben Sie sich schon einmal gewünscht, Sie könnten den Zugriff auf ein Dokument, das Sie versehentlich Ihren Partnern geschickt haben, sperren? Haben Sie sich gefragt, ob es eine Möglichkeit gibt, zu erfahren, welche Ihrer Kunden die neuesten von Ihnen gesendeten Produktinformationen gelesen haben? Müssen Sie vertrauliche Produktinformationen übermitteln, die nicht an andere Personen weitergeleitet werden dürfen?

All dies ist demnächst möglich, da die IT-Abteilung dabei ist, diverse Änderungen einzuführen und dabei Microsoft Azure Information Protection als Lösung zum Schutz von Unternehmensdaten zu implementieren. Viele dieser Lösungen sorgen automatisch für den erforderlichen Schutz, ohne dass sich irgendetwas an Ihrer Vorgehensweise ändern. Andere Änderungen hingegen erfordern eine etwas andere Verfahrensweise. In diesen Fällen erhalten Sie von der IT-Abteilung Informationen und Anweisungen. Bei Fragen oder Problemen können Sie sich jederzeit an das Helpdesk wenden.

Beispiel: Zum Verfolgen (und gegebenenfalls Widerrufen) der von Ihnen übermittelten Dokumente verwenden Sie die Website für die Dokumentenverfolgung:

![Screenshots zur Azure RMS-Dokumentenverfolgung](../media/AzRMS_Tutorial_5_Screenshots.png)

Einen ersten Einblick in die Funktionsweise erhalten Sie in dem zweiminütigen Video [Azure RMS-Dokumentenverfolgung und -widerruf](https://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation).

Zu den wichtigsten Vermögenswerten des Unternehmens zählen die Daten, die wir täglich generieren, speichern und verwenden. Sie verleihen uns unseren Wettbewerbsvorteil und tragen zu unserem Erfolg bei. Daher ist es wichtig, dass wir die Kontrolle über unsere Daten behalten und sicherstellen, dass nicht autorisierte Personen keinen Zugriff darauf erhalten.

Die neu implementierten Lösungen helfen uns dabei, unsere wertvollen Daten zu schützen. Mit den bereitgestellten Tools behalten Sie die Kontrolle über die Daten. Vielen Dank für Ihre Unterstützung bei der Einführung dieser Änderungen.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]



<!--HONumber=Feb17_HO2-->


