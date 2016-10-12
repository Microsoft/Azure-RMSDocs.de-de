---
title: "Szenario – Schutz Ihrer wertvollsten Dateien | Azure Information Protection"
description: "In diesem Szenario und der unterstützenden Benutzerdokumentation wird Azure Rights Management verwendet, um Ihre wertvollsten Dateien manuell und benutzerdefiniert zu schützen. Dies gewährleistet das höchste Maß an Schutz vor nicht autorisiertem Zugriff."
author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 95f1844a-612c-4e67-bbe6-4b6b92295221
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 0f5c138b7a27c7577e5bff23d521ba36264ecc2a
ms.openlocfilehash: 6687ed42bca5e773d6bbc97285f12e3c91ff9f32


---

# Szenario – Schutz Ihrer wertvollsten Dateien

>*Gilt für: Azure Information Protection, Office 365*

In diesem Szenario und der unterstützenden Benutzerdokumentation wird die Azure Rights Management-Technologie von Azure Information Protection verwendet, um Ihre wertvollsten Dateien manuell und benutzerdefiniert zu schützen. Dies gewährleistet das höchste Maß an Schutz vor nicht autorisiertem Zugriff. Dies sind in der Regel Dateien, auf die nur wenige Personen Zugriff haben sollten. Hierzu zählen beispielsweise die Rezepte der bekanntesten Lebensmittelprodukte Ihres Unternehmens oder Übernahmepläne, die nicht vor einem bestimmten Datum veröffentlicht werden dürfen.

Die Anweisungen sind unter den folgenden Umständen geeignet:

-   Sie haben die kleinen Gruppe der zu schützenden Dateien identifiziert.

-   Die Dateien liegen in einem der Office-Dateiformate vor, die Rights Management unterstützen. Wenn die Dateien in anderen Formaten vorliegen (z. B. als CAD-Dateien), stellen Sie sicher, dass diese Formate Azure RMS unterstützen. Stellen Sie außerdem Anwendungen bereit, die Azure RMS von Haus aus unterstützen. Weitere Informationen finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](../understand-explore/applications-support.md).

-   Die Dateien enthalten streng vertrauliche, sensible Informationen, die nur wenigen Personen zugänglich sein sollen.

-   Dass es für die individuelle Zugriffsautorisierung einer Internetverbindung bedarf, ist angesichts der höheren Sicherheit ein akzeptabler Kompromiss.

-   Für diese Benutzer besteht kein Bedarf, die Informationen mit anderen zu teilen. Sie können sie jedoch bearbeiten und die Änderungen speichern.

-   Der Administrator muss in der Lage sein, nachzuverfolgen, wer wann auf die Dateien zugreift, und den Zugriff bei Bedarf zu widerrufen.

## Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, und führen Sie dann die Anweisungen für die unterstützenden Verfahren durch, bevor Sie mit der Benutzerdokumentation fortfahren.

## Anforderungen bei diesem Szenario
Für dieses Szenario muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Sie haben Konten und Gruppen für Office 365 oder Azure Active Directory vorbereitet:<br /><br />– Eine E-Mail-aktivierte Gruppe namens **Privilegierter Zugriff**, der die wenigen Personen angehören, die Zugriff auf diese streng vertraulichen Dokumente haben sollen<br /><br />– Eine E-Mail-aktivierte Gruppe namens **IT-Compliance-Manager**, der die Personen angehören, zu deren Aufgabe eDiscovery, Überwachung und Überprüfung zählt<br /><br />– Eine E-Mail-aktivierte Gruppe namens **RMS-Administratoren**, der alle Administratoren angehören, die Azure RMS konfigurieren|[Vorbereiten für Azure Information Protection](../plan-design/deployment-roadmap.md)|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|
|Sie haben wie nachfolgend beschrieben eine benutzerdefinierte Vorlage konfiguriert.|[Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md)|
|Die Rights Management-Freigabeanwendung wird auf Ihrem Windows-Computer bereitgestellt, damit Sie diese Dateien wie im nächsten Abschnitt beschrieben lokal schützen können.|[Herunterladen und Installieren der Rights Management-Freigabeanwendung](../rms-client/install-sharing-app.md)|
|Autorisierte Benutzer verfügen als Mindestversion über Office 2013.|Benutzer mit Office 2010 müssen zusätzlich die Rights Management-Freigabeanwendung installieren.|
|Ihr Azure Information Protection-Abonnement umfasst die Dokumentenverfolgung.|Wenn Ihr Abonnement keine Dokumentenverfolgung und -sperrung beinhaltet, können Sie die Website für die Dokumentenverfolgung nicht verwenden, um festzustellen, wer auf die Dokumente zugreift, und den Zugriff bei Bedarf zu widerrufen. Erwerben Sie in diesem Fall entweder ein Abonnement, das die Dokumentenverfolgung unterstützt, oder akzeptieren Sie diese Einschränkung. Sie sollten auch die Funktionen zur [Nutzungsprotokollierung](../deploy-use/log-analyze-usage.md) des Azure Rights Management-Diensts in Erwägung ziehen. Diese können Auskunft darüber geben, wer wann auf jede Datei zugegriffen hat, um potenziell verdächtige Verhaltensweisen zu erkennen.<br /><br />Überprüfen Sie die [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website.|

### So konfigurieren Sie benutzerdefinierte Vorlagen

1.  Im klassischen Azure-Portal: Erstellen Sie eine neue benutzerdefinierte Vorlage für Azure Rights Management, die die folgenden Werte und Einstellungen enthält:

    -   Name: **Privilegierter Zugriff**

    -   Rechte: Erteilen Sie der E-Mail-aktivierten Gruppe **Privilegierter Zugriff** Rechte als **Mitautor**.

    -   Bereich: Wählen Sie die E-Mail-aktivierten Gruppen **Privilegierter Zugriff**, **IT-Compliance-Manager** und **RMS-Administratoren** aus.

    -   Offline-Zugriff: **Inhalt ist nur mit Internetverbindung verfügbar**.

2.  Veröffentlichen Sie die neue Vorlage.

### So schützen Sie die Dateien lokal

1.  Navigieren Sie im Datei-Explorer zum ersten Ordner mit zu schützenden Dateien:

    -   Wenn Sie alle Dateien im Ordner schützen möchten, wählen Sie den Ordner aus.

    -   Wenn Sie nur einen Teil der Dateien im Ordner schützen möchten, wählen Sie die zu schützenden Dateien aus.

2.  Klicken Sie mit der rechten Maustaste, und wählen Sie **Mit RMS schützen** und anschließend **Direkt schützen** aus.

3.  Wählen Sie **Privilegierter Zugriff** aus.

4.  Sie werden möglicherweise zum Eingeben von Anmeldeinformationen aufgefordert. Warten Sie, bis die Dateien geschützt sind, und klicken Sie auf **Schließen**, wenn die Seite **Dateien wurden geschützt** angezeigt wird.

5.  Wenn Sie weitere Dateien in anderen Ordnern schützen möchten, wiederholen Sie die Schritte 1 bis 4 für jeden Ordner.

Weitere Informationen zum direkten Schutz von Dateien finden Sie unter [Schützen einer Datei auf einem Gerät (direkt schützen) mithilfe der Rights Management-Freigabeanwendung](../rms-client/sharing-app-protect-in-place.md).

> [!TIP]
> Wenn die Anzahl der zu schützenden Dateien für den manuellen Prozess zu groß ist, können Sie die Dateien mit dem [RMS-Schutztool](https://www.microsoft.com/en-us/download/details.aspx?id=47256) in einem Durchgang mit der Vorlage schützen.

### So überwachen und sperren Sie die Dateien (falls erforderlich)

1.  Klicken Sie im Datei-Explorer mit der rechten Maustaste auf die geschützte Datei, und wählen Sie **Mit RMS schützen** und dann **Verwendung nachverfolgen** aus.

2.  Wenn Sie dazu aufgefordert werden, melden Sie sich auf der Website für die Dokumentenverfolgung an.

3.  Überprüfen Sie, wer auf die von Ihnen geschützten Dateien zugegriffen hat. Achten Sie insbesondere auf fehlgeschlagene Versuche. Diese können auf ein verdächtiges Verhalten hinweisen. Bei Bedarf können Sie den Zugriff auf jede Datei widerrufen.

## Anweisungen für Benutzerdokumentation
Es gibt keine spezifischen Benutzeranweisungen für dieses Szenario, da diese Dateien keine besondere Aktionen von Benutzern verlangen. Die Dateien wurde von Ihnen geschützt und werden durch Sie überwacht. Allerdings müssen Sie gegebenenfalls die Benutzer und Ihre Supportkanäle informieren, welche Dateien geschützt sind und wie dies die Nutzung der Dokumente einschränken kann. Beispiel: Wenn autorisierte Benutzer keinen Internetzugang haben, können sie die Datei nicht öffnen.

Verwenden Sie die folgende Vorlage, kopieren Sie die Ankündigung, und fügen Sie sie in eine Nachricht für die Endbenutzer ein. Nehmen Sie die folgenden Änderungen vor:

1.  Geben Sie den tatsächlichen Namen der Dateien oder eine klare Referenz ein, die autorisierte Benutzer verstehen.

2.  Ersetzen Sie *&lt;Kontaktdetails&gt;* durch Informationen darüber, wie diese Benutzer das Helpdesk oder die IT-Abteilung über einen eskalierten Supportkanal kontaktieren können, der der Bedeutung dieser Dokumente entspricht. Geben Sie beispielsweise für Supportanrufe mit hohem Schweregrad eine rund um die Uhr erreichbare Telefonnummer ein.

3.  Nehmen Sie jegliche sonstigen Änderungen an der Ankündigung vor, und senden Sie sie anschließend an diese Benutzer.

Die Beispieldokumentation veranschaulicht, wie diese Ankündigung für Benutzer nach Ihren Anpassungen aussehen könnte.

![Benutzerdokumentationsvorlage für die Azure RMS-Schnellbereitstellung](../media/AzRMS_UsersBanner.png)

### IT-Ankündigung: Schutz der geheimsten Dokumente von &lt;Organisationsname&gt;
Auf die folgenden Dateien wurde jetzt ein sehr hoher Schutzgrad angewendet, sodass nur &lt;Benutzer mit eingeschränktem Zugriff&gt; auf diese Dateien zugreifen und sie ändern können. Zum Schutz vor nicht autorisiertem Zugriff fordert die Anwendung bei jedem Aufruf der Dateien automatisch eine Autorisierung an. Sie benötigen daher zum Öffnen eine Internetverbindung und müssen möglicherweise Ihre Anmeldeinformationen eingeben:

-   &lt;Streng geheimes Dokument, Typ oder Speicherort 1&gt;

-   &lt;Streng geheimes Dokument, Typ oder Speicherort 2&gt;

-   &lt;Streng geheimes Dokument, Typ oder Speicherort 3&gt;

**Benötigen Sie Unterstützung?**

-   Wenn Sie keinen Zugriff auf diese Dateien haben oder verdächtige Änderungen in den Dateien feststellen, nutzen Sie die angegebenen &lt;Maßnahmen und Kontaktdetails&gt;.

#### Beispiel für eine angepasste Benutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

##### IT-Ankündigung: Schutz der geheimsten Dokumente von VanArsdel
Auf die folgenden Dateien wurde jetzt ein sehr hoher Schutzgrad angewendet, sodass nur die in der Empfängerzeile angegebenen Personen Zugriff auf diese Dateien haben und sie ändern können. Zum Schutz vor nicht autorisiertem Zugriff fordert die Anwendung bei jedem Aufruf der Dateien automatisch eine Autorisierung an. Sie benötigen daher zum Öffnen eine Internetverbindung und müssen möglicherweise Ihre Anmeldeinformationen eingeben:

-   Designspezifikationen für Codename "Mercury"

-   Designspezifikationen für Codename "Jupiter"

-   Designspezifikationen für Codename "Saturn"

-   Designspezifikationen für Codename "Neptune"

**Benötigen Sie Unterstützung?**

-   Wenn Sie keinen Zugriff auf diese Dateien haben oder verdächtige Änderungen in den Dateien feststellen, rufen Sie den rund um die Uhr verfügbaren Supporteskalationskanal an, der Ihnen von der IT-Abteilung in einer geschützten E-Mail-Nachricht zugesendet wurde.




<!--HONumber=Oct16_HO1-->


