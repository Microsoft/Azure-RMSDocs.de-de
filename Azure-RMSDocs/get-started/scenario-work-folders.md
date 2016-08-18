---
title: "Szenario – Arbeitsordner für dauerhaften Schutz konfigurieren | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/20/2016
ms.topic: get-started-article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1f189345-a69e-4bf5-8a45-eb0fe5bb542b
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 332e102cb27854314b93a71bfeae82a95c9a7812
ms.openlocfilehash: 35ad445e229eac3feeca5522a41b9e3b25fd1180


---

# Szenario – Arbeitsordner für dauerhaften Schutz konfigurieren

*Gilt für: Azure Rights Management, Office 365*

In diesem Szenario und der unterstützende Benutzerdokumentation wird Azure Rights Management verwendet, um Office-Dokumente in [Arbeitsordnern](https://technet.microsoft.com/library/dn265974.aspx) dauerhaft zu schützen. Arbeitsordner verwenden einen Rollendienst für Dateiserver, die unter Windows Server ausgeführt werden. Sie bieten Benutzern eine konsistente Möglichkeit, um auf ihren PCs und Geräten auf ihre Arbeitsdateien zuzugreifen. Arbeitsordner bieten eine eigene Verschlüsselung zum Schutz der Dateien. Dieser Schutz geht jedoch verloren, wenn die Dateien aus den Arbeitsordnern verschoben werden. Dies ist beispielsweise der Fall, wenn Benutzer die synchronisierten Dateien kopieren und in einem Speicher ablegen, der nicht der Kontrolle der IT-Abteilung unterliegt, oder wenn sie die Dateien anderen Personen per E-Mail senden.

Der zusätzliche Schutz durch Azure Rights Management trägt dazu bei, versehentliche Datenverluste zu verhindern. Damit wird unterbunden, dass Dateien von Personen außerhalb Ihrer Organisation angezeigt werden. Zu diesem Zweck können Sie eine der integrierten Standardvorlagen für Benutzerrechterichtlinien verwenden. Bevor Sie dieses Szenario jedoch bereitstellen, sollten Sie erwägen, ob Benutzer diese Dateien möglicherweise legitim an Personen außerhalb der Organisation weiterleiten müssen. Dies ist beispielsweise der Fall, wenn ein Benutzer nach der Arbeit an einer Preisliste die endgültige Version per E-Mail an einen Kunden in einer anderen Organisation sendet. Wenn Sie die Rights Management-Standardvorlage für Arbeitsordner verwenden, kann der Kunden in der anderen Organisation das per E-Mail gesendete Dokument nicht lesen. Um dies zu ermöglichen, können Sie eine benutzerdefinierte Vorlage erstellen, mit der Benutzer eine neue Benutzerrechterichtlinie auf die Datei anwenden können. Diese ersetzt die ursprüngliche Beschränkung für alle Mitarbeiter durch die Beschränkung für den in der E-Mail angegebenen Empfänger.

> [!NOTE]
> Wenn Sie die für dieses Szenario beschriebene benutzerdefinierte Vorlage verwenden, können Benutzer zwar absichtlich Dateien mit Personen teilen, die Sie nicht in der Vorlage definiert haben, aber der zusätzliche Schutz durch Azure Rights Management bietet zahlreiche Vorteile. Dieser zusätzliche Schutz verhindert versehentliche Datenverluste, wenn der Inhalt aus den Arbeitsordnern verschoben wird. Er bleibt sowohl an seinem Speicherort als auch während der Übertragung vor nicht autorisierten Zugriffen geschützt. Dies ist beispielsweise der Fall, wenn ein Gerät, auf dem Arbeitsordner verwendet werden, verloren geht oder gestohlen wird, oder wenn der mit dem Gerät synchronisierte Inhalt über eine unsichere Infrastruktur übertragen wird.
> 
> Wenn ein Benutzer den Inhalt mit einer anderen Person in einer anderen Organisation mithilfe der geschützten Freigabefunktion der Rights Management-Freigabeanwendung teilt, ersetzt dieser Benutzer den ursprünglichen Schutz durch eine eigene Schutzrichtlinie. Daher bleibt der Inhalt weiterhin vor nicht autorisiertem Zugriff geschützt und ist nur für die vom Benutzer festgelegten Personen zugänglich.

Sie können diesen dauerhafte Schutz auf alle Office-Dokumente in den Arbeitsordnern der Benutzer oder nur auf Dateien anwenden, die sensible oder geschäftskritische Daten enthalten.

Die Anweisungen sind unter den folgenden Umständen geeignet:

-   Die dauerhaft zu schützenden Dateien in Arbeitsordnern sind Office-Dateien. Diese Dateien können direkt von Azure Rights Management geschützt werden. Sie behalten ihre Dateinamenerweiterung bei und können mit dem gewohnten Workflow geöffnet werden.

-   Sie möchten alle Office-Dateien in den Arbeitsordnern der Benutzern oder bestimmte Dateien, die mithilfe der Dateiklassifizierungsinfrastruktur des Ressourcen-Managers für Dateiserver in Windows Server identifiziert wurden, dauerhaft schützen.

-   Für Dateien, die für Personen freigegeben werden müssen, die nicht in der Vorlage für Benutzerrechterichtlinien angegeben sind (z. B. Benutzer in einer anderen Organisation), müssen Benutzer eine neue Benutzerrechterichtlinie anwenden, um den Schutz durch die ursprüngliche Benutzerrechterichtlinie zu ersetzen.

## Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, und führen Sie dann die Anweisungen für die unterstützenden Verfahren durch, bevor Sie mit der Benutzerdokumentation fortfahren.

## Anforderungen bei diesem Szenario
Damit die Anweisungen in diesem Szenario funktionieren, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Sie haben Ihre lokalen Active Directory-Benutzerkonten, einschließlich ihrer E-Mail-Adressen, mit Azure Active Directory oder Office 365 synchronisiert. Dies ist für alle Benutzer erforderlich, die Arbeitsordner verwenden.|[Vorbereiten für Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Eine der folgenden Komponenten:<br /><br />– Um eine Standardvorlage für alle Benutzer zu verwenden, mit der Benutzer keine neue Benutzerrechterichtlinien anwenden dürfen: Sie haben die Standardvorlage **&lt;Organisationsname&gt; – Vertraulich** nicht archiviert<br /><br />– Um eine benutzerdefinierte Vorlage zu verwenden, mit der Benutzer eine neue Benutzerrechterichtlinie anwenden können: Sie verwenden die folgenden Anweisungen, um eine benutzerdefinierte Vorlage zu erstellen|[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Der Rights Management-Verbindungsdienst ist installiert, für den Windows Server-Computer autorisiert und für die **FCI Server**-Rolle konfiguriert.|[Bereitstellen des Azure Rights Management-Verbindungsdiensts](https://technet.microsoft.com/library/dn375964.aspx)|
|Die Rights Management-Freigabeanwendung wird auf Benutzercomputern bereitgestellt, auf denen Windows ausgeführt wird.|[Automatische Bereitstellung für die Microsoft Rights Management-Freigabeanwendung](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|

### Konfigurieren der benutzerdefinierten Vorlage für Benutzerrechterichtlinien, sodass Benutzer Dateien aus Arbeitsordnern außerhalb der Organisation freigeben können

1.  Melden Sie sich bei dem klassischen Azure-Portal an, und navigieren Sie zu den Azure Rights Management-Vorlagen.

2.  Kopieren Sie die Vorlage **&lt;Organisationsname&gt; – Vertraulich**, und geben Sie einen Namen und eine Beschreibung für dieses Arbeitsordnerszenario ein. Wir empfehlen Folgendes:

    -   Name: **Durch Arbeitsordner geschützte Inhalte**

    -   Beschreibung: **Dieser Inhalt wird durch Arbeitsordner geschützt und ist Mitarbeitern des Unternehmens vorbehalten. Um diesen Inhalt für Personen außerhalb der Organisation freizugeben, fügen Sie das Dokument an eine E-Mail-Nachricht an, und verwenden Sie die Funktion "Geschützt freigeben".**

3.  Auf der Seite **RECHTE**:

    -   Ändern Sie die vorhandenen Berechtigungen von **Benutzerdefiniert** in **Mitbesitzer**.

4.  Auf der Seite **KONFIGURIEREN**:

    -   Stellen Sie sicher, dass der **STATUS** auf **VERÖFFENTLICHEN** festgelegt ist.

    -   Löschen Sie unter **Name und Beschreibung** die Einträge der Sprachen, die Sie nicht verwenden. Für die Sprachen, die Sie verwenden, aktualisieren Sie die Felder **NAME** und **BESCHREIBUNG** entsprechend dem Namen und der Beschreibung dieser Vorlage in der angegebenen Sprache.

5.  Speichern Sie die Vorlage.

### Konfigurieren von Arbeitsordnern für dauerhaften Schutz von Office-Dateien

1.  Legen Sie Arbeitsordner für Benutzer an, sodass lokal gespeicherte Dateien in einem Dateiserverordner synchronisiert werden. Dies wird als *Synchronisierungsfreigabe* bezeichnet. Die Synchronisierungsfreigabe auf dem Dateiserver darf nicht auf demselben Server erfolgen, auf dem der Rights Management-Verbindungsdienst ausgeführt wird.

    Für diese Lösung ist der Rollendienst für Arbeitsordner im Server-Manager für die Datei- und Speicherdienste-Rolle erforderlich. Auf dem Dateiserver muss als Mindestversion Windows Server 2012 R2 ausgeführt werden. Dieser Dateiserver kann lokal oder auf einem virtuellen Computer in Azure vorhanden sein. Weitere Informationen über Arbeitsordner finden Sie unter [Übersicht: Arbeitsordner](https://technet.microsoft.com/library/dn265974.aspx).

    Anweisungen zur Bereitstellung finden Sie unter [Bereitstellen von Arbeitsordnern](https://technet.microsoft.com/library/dn528861.aspx). Stellen Sie sicher, dass Sie die integrierte Verschlüsselung aktivieren (die Option **Arbeitsordner verschlüsseln**), die zusätzlich zur Azure Rights Management-Verschlüsselung angewendet wird. Zusätzlich:

    -   Beim Binden des SSL-Zertifikats auf dem Synchronisierungsserver (Schritt 4): Verwenden Sie den Befehl Netsh (statt der IIS-Verwaltungskonsole), um das Zertifikat an die Standard-HTTPS-Schnittstelle der Website zu binden.

    -   Damit Benutzer beim Einrichten der Arbeitsordner nicht die Fehlermeldung **Problem beim Anwenden der Sicherheitsrichtlinien** erhalten und sich auf ihren Domänencomputern nicht als lokaler Administrator anmelden müssen: Verwenden Sie das [Set-SyncShare](https://technet.microsoft.com/library/dn296649%28v=wps.630%29.aspx)-Cmdlet mit dem PasswordAutolockExcludeDomain-Parameter, und geben Sie die Namen der Domänen an, in denen sich diese Computer befinden (z. B. contoso.com).

2.  So konfigurieren Sie für den Rights Management-Verbindungsdienst:

    1.  Erstellen Sie mit dem Ressourcen-Manager für Dateiserver eine Dateiverwaltungsaufgabe, die den Ordner für die Synchronisierungsfreigabe als Bereich identifiziert.

    2.  Wählen Sie für die Aktion die **RMS-Verschlüsselung** und eine Vorlage:

        -   Wenn Sie keine benutzerdefinierte Vorlage erstellt haben, da Sie nicht möchten, dass Benutzer Dateien für Personen außerhalb der Organisation freigeben können, wählen Sie den Vorlagennamen **&lt;Organisationsname&gt; – Vertraulich** aus. Verwenden Sie beispielsweise **VanArsdel, Ltd – Vertraulich**.

        -   Wenn Sie eine benutzerdefinierte Vorlage mithilfe der zuvor beschriebenen Anweisungen erstellt haben, wählen Sie diese Vorlage aus. Wählen Sie beispielsweise **Durch Arbeitsordner geschützte Inhalte** aus.

    3.  Geben Sie einen Zeitplan, der ausreichend Zeit zum Verschlüsseln aller Office-Dateien mit Azure Rights Management bietet. Aktivieren Sie die Option **Für neue Dateien fortlaufend ausführen**.

3.  Um diese Konfiguration manuell zu testen, stellen Sie sicher, dass der Ordner mehrere Office-Dateien enthält. Aktivieren Sie dann die Option **Dateiverwaltungsaufgabe jetzt ausführen**, und wählen Sie **Warten, bis die Aufgabe abgeschlossen ist**.

    Warten Sie, bis das Dialogfeld **Dateiverwaltungsaufgabe wird ausgeführt** geschlossen wurde, und sehen Sie sich dann die Ergebnisse im automatisch angezeigten Bericht an. Daraufhin sollte die Anzahl der Dateien im ausgewählten Ordner im Feld **Dateien** angezeigt werden. Vergewissern Sie sich, dass die Dateien im ausgewählten Ordner jetzt durch Azure Rights Management geschützt sind. Öffnen Sie beispielsweise eine Datei, und vergewissern Sie sich, dass am oberen Rand des Dokuments das Informationsbanner mit dem Namen und der Beschreibung der Rights Management-Vorlage angezeigt wird.

4.  Wenn Sie Dateien mithilfe der Dateiklassifizierungsinfrastruktur selektiv schützen möchten, konfigurieren Sie die Klassifizierungsregel und den Zeitplan. Beziehen Sie dann diese Klassifizierungseigenschaft als Bedingung in die Dateiverwaltungsaufgabe ein.

## Anweisungen für Benutzerdokumentation
Wenn die Dateien, die Sie mit Azure Rights Management schützen, nicht für Personen außerhalb Ihrer Organisation freigegeben werden müssen, müssen Sie Benutzern möglicherweise neben den Anweisungen zur Verwendung von Arbeitsordnern keine zusätzlichen Anweisungen bereitstellen. Wenn Benutzer die mit Azure Rights Management und der Standardvorlage geschützten Dateien öffnen, werden die Dateien wie gewohnt in Office angezeigt. Einziger Unterschied ist, dass Benutzer gegebenenfalls zur Authentifizierung aufgefordert werden. In diesem Fall wird am oberen Rand des Dokuments in einer Informationsleiste angezeigt, dass der Inhalt vertrauliche Informationen enthält, die nur zur internen Verwendung vorgesehen sind.

Wenn Sie die benutzerdefinierte Vorlage wie für dieses Szenario beschrieben konfiguriert haben, sehen Benutzer in der Informationsleiste die Vorlagenbeschreibung: **Dieser Inhalt wird durch Arbeitsordnern geschützt und ist Mitarbeitern des Unternehmens vorbehalten. Um diesen Inhalt für Personen außerhalb der Organisation freizugeben, fügen Sie das Dokument an eine E-Mail-Nachricht an, und verwenden Sie die Funktion "Geschützt freigeben".** Diese Beschreibung bietet zwar eine Übersicht, wie die Datei außerhalb der Organisation freigegeben werden kann, aber die Benutzer benötigen vermutlich detaillierte Anweisungen, insbesondere bei der ersten Freigabe. Verwenden Sie für dieses Folgeszenario die Administrator- und Endbenutzeranweisungen unter [Szenario – Freigeben einer Office-Datei für Benutzer in einer anderen Organisation](scenario-share-office-file-externally.md).

> [!TIP]
> Wenn Sie die in diesen Anweisungen beschriebene benutzerdefinierte Vorlage nicht verwenden möchten, da Benutzer diese Dateien nicht unbeaufsichtigt außerhalb der Organisation freigeben können sollen, informieren Sie das Helpdesk, dass bei legitimen Freigabeanforderungen der für Ihr Unternehmen geeignete Mechanismus verwendet werden kann. Dies ist beispielsweise der Fall, wenn ein [Administrator](https://technet.microsoft.com/library/mt147272.aspx) eine neue Vorlage auf den Inhalt anwenden könnte, die dem anfordernden Benutzer Vollzugriff gewährt, sodass dieser Benutzer die Funktion "Geschützt freigeben" verwenden kann.
> 
> Wenn Sie nach gewisser Zeit feststellen, dass viele dieser Anforderungen eingehen, können Sie eine eigene benutzerdefinierte Vorlage für dieses Szenario definieren, die nur bestimmten Benutzern (z. B. Manager oder dem Helpdesk) die Mitbesitzeroption gewährt, während Standardbenutzer Rechte als Mitautor oder sonstige gewünschte [Rechte](https://technet.microsoft.com/library/mt169423.aspx) erhalten.




<!--HONumber=Jun16_HO4-->


