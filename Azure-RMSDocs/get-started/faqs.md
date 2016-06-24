---
# required metadata

title: Häufig gestellte Fragen zu Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 06/07/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 71ce491f-41c1-4d15-9646-455a6eaa157d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Häufig gestellte Fragen zu Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*

Einige häufig gestellte Fragen zu Microsoft [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)], das auch als Azure RMS bezeichnet wird:

## Was benötige ich, um Azure RMS bereitzustellen, und wie stelle ich das an?
Überprüfen Sie zunächst [Anforderungen für Azure Rights Management](requirements-azure-rms.md). Darin sind Informationen über Cloud-Abonnementoptionen enthalten, und es wird gezeigt, wie Sie Ihre lokalen Server mit Azure RMS verwenden können, welche Bereitstellungsszenarien zurzeit nicht unterstützt werden und welche Geräte und Anwendungen Azure RMS unterstützen. Zudem enthält das Thema einen Link für den Fall, dass Sie eine Liste von IP-Adressen und Domänennamen für Firewalls oder Proxyserver benötigen. Sie sollten sich darüber hinaus die anderen Artikel im Abschnitt **Erste Schritte** und im Abschnitt **Verstehen & Erkunden** ansehen, um ein grundlegendes Verständnis dafür zu entwickeln, wie [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] den Schutz der Daten Ihrer Organisation unterstützen kann, wie es mit Anwendungen funktioniert, wie es sich im Vergleich zur lokalen Version von Active Directory Rights Management verhält und welche Begriffe und Abkürzungen für [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] spezifisch sind.

## Müssen sich Dateien in der Cloud befinden, um von Azure RMS geschützt werden zu können?
Nein, das ist ein weit verbreitetes Missverständnis. Für den Datenschutzprozess des Azure Rights Management-Diensts (und von Microsoft) gilt, dass er Ihre Daten weder sieht noch speichert. Informationen, die Sie schützen, werden niemals an Azure gesendet oder dort gespeichert – es sei denn, dass Sie diese explizit in Azure speichern oder einen anderen Cloud-Dienst verwenden, der sie in Azure speichert. 

Weitere Informationen finden Sie unter [Funktionsweise von Azure RMS. Details](../understand-explore/how-does-it-work.md). Dort ist beschrieben, wie eine geheime Cola-Formel, die lokal erstellt und gespeichert wurde, von Azure RMS geschützt wird, aber lokal bleibt.

## Kann ich Azure RMS in meine lokalen Server integrieren?
Ja. Azure RMS kann in Ihre lokalen Server, etwa Exchange Server, SharePoint und Windows-Dateiserver, integriert werden. Dazu verwenden Sie den [Rights Management-Connector](../deploy-use/deploy-rms-connector.md). Wenn Sie nur an der Nutzung der Dateiklassifizierungsinfrastruktur (FCI, File Classification Infrastructure) mit Windows Server interessiert sind, können Sie auch die [RMS Protection-Cmdlets](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx) verwenden. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine übergangslosere Authentifizierungshandhabung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)verwenden.

Azure RMS generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf, sodass es keine lokale PKI verwendet. Weitere Informationen zur Verwendung von Zertifikaten in Azure RMS finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsaufnahme](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) unter [Funktionsweise von Azure RMS](../understand-explore/how-does-it-work.md).

## Ich habe eine Hybridbereitstellung von Exchange mit einigen Benutzern auf Exchange Online und anderen auf Exchange Server – wird dies von Azure RMS unterstützt?
Ja, und das Gute ist, dass Benutzer über zwei Exchange-Bereitstellungen hinweg E-Mails und Anlagen nahtlos schützen sowie geschützte E-Mails und Anlagen nutzen können. Führen Sie für diese Konfiguration folgende Schritte aus: [Aktivieren von Azure RMS](../deploy-use/activate-service.md) , [Aktivieren von IRM für Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)und [Bereitstellen und Konfigurieren des RMS-Connectors](../deploy-use/deploy-rms-connector.md) für Exchange Server.

## Gibt es schrittweise Anweisungen, wie Exchange Online zur Verwendung von Azure RMS konfiguriert wird?

Ja. Unter [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration.md ) finden Sie einen typischen Satz von Befehlen, mit denen Exchange Online die Verwendung von Azure RMS ermöglicht wird. Sie erfahren, warum die Outlook Web App die **Berechtigungen festlegen**-Menüoptionen nicht sofort anzeigt, und erhalten Informationen zum Befehl, der ausgeführt werden muss, wenn Sie die Azure-RMS-Vorlagen geändert oder aktualisiert haben. 

## Wenn ich Azure RMS in der Produktion bereitstelle, ist mein Unternehmen dann an die Lösung gebunden und läuft andernfalls Gefahr, den Zugriff auf Inhalte zu verlieren, die wir mit Azure RMS geschützt haben?
Nein, Sie behalten immer die Kontrolle über Ihre Daten und können weiterhin darauf zugreifen, selbst wenn Sie sich entscheiden, Azure RMS nicht mehr zu verwenden. Weitere Informationen finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md).

Bevor Sie Ihre Azure RMS-Bereitstellung außer Betrieb setzen, würden wir jedoch gerne erfahren bzw. verstehen, warum Sie diese Entscheidung getroffen haben. Wenn Azure RMS Ihren geschäftlichen Anforderungen nicht gerecht wird, können Sie Kontakt mit uns aufnehmen, um zu erfahren, ob in naher Zukunft neue Funktionen geplant oder ob Alternativen verfügbar sind. Senden Sie eine E-Mail-Nachricht an [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS) . Wir freuen uns darauf, Ihre technischen und geschäftlichen Anforderungen mit Ihnen zu besprechen.

## Kann ich steuern, welche Benutzer Azure RMS verwenden können, um Inhalte zu schützen?
Ja, hat Azure RMS hat hierfür Steuerelemente zum Einbinden (Onboarding) von Benutzern. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboardingsteuerungsrichtlinien für eine stufenweise Bereitstellung](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) im Artikel [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

## Kann ich verhindern, dass Benutzer geschützte Dokumente für bestimmte Organisationen freigeben?
Einer der größten Vorteile von Azure RMS besteht darin, dass es B2B-Zusammenarbeit unterstützt, ohne dass Sie explizite Vertrauensstellungen für jede Partnerorganisation konfigurieren müssen, denn Azure AD übernimmt die Authentifizierung für Sie.

Es gibt keine Verwaltungsoption, mit der verhindert werden kann, dass Benutzer Dokumente geschützt für bestimmte Organisationen freigeben. Angenommen, Sie möchten eine Organisation blockieren, der Sie nicht vertrauen oder die ein konkurrierendes Unternehmen hat. Azure RMS daran zu hindern, geschützte Dokumente an Benutzer in dieser Organisationen zu senden, wäre nicht sinnvoll, da Benutzer ihre Dokumente dann ungeschützt freigeben würden, und dies ist wahrscheinlich genau das, was in diesem Szenario nicht geschehen soll! Beispielsweise könnten Sie nicht erkennen, wer vertrauliche Unternehmensdokumente für welche Benutzer in dieser Organisation freigibt, wogegen Sie dies erkennen können, wenn das Dokument (oder die E-Mail) durch Azure RMS geschützt wird.

## Wenn ich ein geschütztes Dokument für eine Person außerhalb meiner Firma freigebe, wie wird dieser Benutzer authentifiziert?
Azure RMS verwendet immer ein Azure Active Directory-Konto und eine zugeordnete E-Mail-Adresse für die Benutzerauthentifizierung, wodurch sich eine nahtlose Business-to-Business-Zusammenarbeit für Administratoren ergibt. Wenn die andere Organisation Azure-Dienste verwendet, haben Benutzer bereits Konten in Azure Active Directory, selbst wenn diese Konten lokal erstellt und verwaltet und dann mit Azure synchronisiert werden.  Wird in der Organisation Office 365 verwendet, verwendet dieser Dienst (im Hintergrund) ebenfalls Azure Active Directory für die Benutzerkonten.  Wenn die Organisation des Benutzers keine verwalteten Konten in Azure hat, können sich Benutzer für [RMS for Individuals](../understand-explore/rms-for-individuals.md)registrieren. Dadurch werden ein nicht verwalteter Azure-Mandant und ein Verzeichnis für die Organisation mit einem Konto für den Benutzer erstellt, sodass dieser Benutzer dann für Azure RMS authentifiziert werden kann.

Die Authentifizierungsmethode für diese Konten kann unterschiedlich sein, je nachdem, wie der Administrator in der anderen Organisation die Azure Active Directory-Konten konfiguriert hat. Beispielsweise können Kennwörter, die für diese Konten erstellt wurden, Multi-Factor Authentication (MFA, mehrstufige Authentifizierung), Verbund oder Kennwörter verwendet werden, die in Active Directory-Domänendienste erstellt und dann mit Azure Active Directory synchronisiert wurden.

## Kann ich Benutzer, die nicht zu meinem Unternehmen gehören, zu benutzerdefinierten Vorlagen hinzufügen?
Ja. Ein Erstellen von benutzerdefinierten Vorlagen, die Endbenutzer (und Administratoren) in Anwendungen auswählen können, ermöglicht es Benutzern, schnell und problemlos Informationsschutz anzuwenden, indem sie vordefinierte Richtlinien verwenden, die Sie definiert haben. Eine der Einstellungen in der Vorlage bestimmt, wer auf den Inhalt zugreifen kann, und Sie können Benutzer und Gruppen aus Ihrer Organisation sowie Benutzer angeben, die nicht zu Ihrer Organisation gehören.

Um Benutzer anzugeben, die nicht Ihrer Organisation angehören, fügen Sie diese als Kontakte einer Gruppe hinzu, die Sie beim Konfigurieren Ihrer Vorlagen im klassischen Azure-Portal auswählen. Sie können auch das [Windows PowerShell-Modul für Azure Rights Management](../deploy-use/install-powershell.md) verwenden:

-   **Erstellen oder Aktualisieren der Vorlage mithilfe eines Rechtedefinitionsobjekts**.    Geben Sie die externen E-Mail-Adressen und ihre Rechte in einem Rechtedefinitionsobjekt an, das Sie dann zum Erstellen oder Aktualisieren einer Vorlage verwenden. Sie geben das Rechtedefinitionsobjekt an, indem Sie mit dem [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)-Cmdlet eine Variable erstellen und diese Variable anschließend mit dem [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)-Cmdlet (für eine neue Vorlage) oder mit dem [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)-Cmdlet (zum Ändern einer vorhandenen Vorlage) für den „-RightsDefinition“-Parameter bereitstellen. Wenn Sie jedoch diese Benutzer zu einer vorhandenen Vorlage hinzufügen, müssen Sie nicht nur für die externen Benutzer Rechtedefinitionsobjekte definieren, sondern auch für die vorhandenen Gruppen in den Vorlagen.

Weitere Informationen zu benutzerdefinierten Vorlagen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für die Rechteverwaltung](../deploy-use/configure-custom-templates.md).

## Funktioniert Azure RMS mit dynamischen Gruppen in Azure AD?
Mit einer Azure AD Premium-Funktion können Sie die dynamische Mitgliedschaft für Gruppen durch Angeben von [attributbasierten Regeln](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) konfigurieren. Beim Erstellen einer Sicherheitsgruppe in Azure AD unterstützt dieser Gruppentyp die dynamische Mitgliedschaft, aber keine E-Mail-Adresse und kann daher nicht mit Azure RMS verwendet werden. Allerdings können Sie jetzt einen neuen Gruppentyp in Azure AD erstellen, der die dynamische Mitgliedschaft und E-Mails unterstützt. Wenn Sie eine neue Gruppe im klassischen Azure-Portal hinzufügen, können Sie als **GRUPPENTYP** die Option **Office 365-„Vorschau“** auswählen. Da diese Gruppe E-Mail-fähig ist, können Sie sie mit Azure RMS verwenden.

Wie der Optionsname deutlich zeigt, befindet sich dieser neue Gruppentyp noch in der Vorschauphase. Mit zusätzlichen Funktionen und einer neuen Dokumentation kann also in Zukunft gerechnet werden. In der Zwischenzeit möchten wir bestätigen, dass Sie diesen neuen Gruppentyp mit Azure RMS verwenden können.


## Welche Geräte und welche Dateitypen werden von Azure RMS unterstützt?
Eine Liste der unterstützten Geräte finden Sie unter [Clientgeräte, die Azure RMS unterstützen](../get-started/requirements-client-devices.md). Da derzeit nicht alle unterstützten Geräte alle RMS-Funktionen unterstützen können, sollten Sie sich auch die [Clientgerätefunktionen](../get-started/requirements-client-devices.md#client-device-capabilities)-Tabelle im gleichen Thema ansehen.

Azure RMS kann alle Dateitypen unterstützen. Für Text-, Bild-, Microsoft Office-Dateien (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen stellt Azure RMS systemeigenen Schutz bereit, der Verschlüsselung und die Durchsetzung von Rechten (Berechtigungen) umfasst. Für alle anderen Anwendungen und Dateitypen bietet generischer Schutz Dateiverkapselung und Authentifizierung, damit überprüft wird, ob ein Benutzer zum Öffnen der Datei autorisiert ist.

Eine Liste der Dateinamenerweiterungen, für die Azure RMS systemeigene Unterstützung bietet, finden Sie im Abschnitt [Unterstützte Dateitypen und Dateinamenerweiterungen](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) des [Administratorhandbuchs der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md). Nicht aufgeführte Dateinamenerweiterungen werden mithilfe der RMS-Freigabeanwendung unterstützt, die automatisch generischen Schutz auf diese Dateien anwendet.

## Wenn ich ein RMS-geschütztes Office-Dokument öffne, wird die dazugehörige temporäre Datei ebenfalls von RMS geschützt?

Nein. Die dazugehörige temporäre Datei enthält in diesem Szenario keine Daten aus dem Originaldokument, sondern nur das, was der Benutzer eingibt, während die Datei geöffnet ist. Im Gegensatz zur ursprünglichen Datei soll die temporäre Datei offensichtlich nicht freigegeben werden und verbleibt auf dem Gerät, geschützt durch lokale Sicherheitskontrollen wie BitLocker und EFS.

## Ab wann wird Migration von AD RMS unterstützt?
Zunächst hat Azure RMS Migration von einer lokalen Bereitstellung von Rights Management, z. B. AD RMS, nicht unterstützt. Eine solche Migration wird aber jetzt unterstützt.

Weitere Informationen finden Sie unter [Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md).

## Wir möchten BYOK mit Azure RMS verwenden, haben jedoch erfahren, dass diese Kombination nicht mit Exchange Online kompatibel ist. Wie lautet Ihre Empfehlung?
Lassen Sie sich durch diese aktuelle Einschränkung nicht von der Azure RMS-Bereitstellung abbringen. Wenn Sie Exchange Online verwenden und BYOK (Bring Your Own Key) nutzen möchten, empfehlen wir, dass Sie Azure RMS im Standard-Schlüsselverwaltungsmodus bereitstellen, in dem Microsoft Ihren Schlüssel generiert und verwaltet. Auf diese Weise erhalten Sie jetzt alle Vorteile bezüglich des Schutzes wichtiger Dateien und E-Mails mit der Option, zu einem späteren Zeitpunkt zu BYOK zu wechseln (z. B. wenn Exchange Online BYOK unterstützt).

Wenn Ihre Unternehmensrichtlinien jedoch erfordern, dass Sie ein Hardwaresicherheitsmodul (HSM) verwenden, und dies würde Ihre Azure RMS-Bereitstellung blockieren, können Sie alternativ jetzt Azure RMS mit BYOK bereitstellen, mit verminderter RMS-Funktionalität für Exchange. Weitere Informationen finden Sie unter [BYOK – Preise und Einschränkungen](../plan-design/byok-price-restrictions.md) in [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

## Eine Funktion, die ich suche, scheint nicht mit SharePoint-geschützten Bibliotheken zu funktionieren – ist die Unterstützung dieser Funktion geplant?
Derzeit unterstützt SharePoint RMS-geschützte Dokumente durch Verwenden von IRM-geschützten Bibliotheken, die weder benutzerdefinierte Vorlagen, noch Dokumentnachverfolgung noch einige andere Funktionen unterstützen. Weitere Informationen finden Sie im Abschnitt [SharePoint Online und SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) im Artikel [Office-Anwendungen und -Dienste](../understand-explore/office-apps-services-support.md).

Wenn Sie an einer bestimmten Funktion interessiert sind, die noch nicht unterstützt wird, sollten Sie die Ankündigungen im [RMS Team Blog](http://blogs.technet.com/b/rms/)verfolgen.

## Wie konfiguriere ich OneDrive for Business in SharePoint Online, sodass Benutzer ihre Dateien sicher für Personen innerhalb und außerhalb des Unternehmens freigeben können?
Als Office 365-Administrator konfigurieren Sie dies normalerweise nicht. Eine solche Konfiguration erfolgt durch Benutzer.

Als SharePoint-Websiteadministrator aktivieren und konfigurieren Sie IRM für eine SharePoint-Bibliothek, deren Besitzer Sie sind. OneDrive for Business ist so konzipiert, dass die Benutzer IRM für ihre eigene OneDrive for Business-Bibliothek aktivieren und konfigurieren.  Mithilfe von PowerShell können Sie das jedoch für sie übernehmen. Anweisungen finden Sie im Abschnitt [SharePoint Online und OneDrive for Business: IRM-Konfiguration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) im Artikel [Office 365: Konfigurationen für Clients und Onlinedienste](../deploy-use/configure-office365.md).

## Gibt es besondere Tipps und Tricks für eine erfolgreiche RMS-Bereitstellung?
Nachdem wir viele Bereitstellungen begleitet und uns mit Kunden, Partnern, Beratern und Supportmitarbeitern unterhalten haben – ist das einer der größten Tipps, die wir aus unserer Erfahrung weitergeben können: **Entwerfen Sie einfache Rechterichtlinien, und stellen Sie sie entsprechend bereit**.

Da Azure RMS sichere Freigaben mit praktisch jedermann unterstützt, können Sie bei der Reichweite Ihres Informationsschutzes Ehrgeiz entwickeln. Seien Sie aber konservativ bei Ihren Rechterichtlinien. Für die meisten Organisationen hat die Vermeidung von Datenlecks durch Anwenden der standardmäßigen Rechterichtlinienvorlage, die den Zugriff auf Personen in der eigenen Organisation einschränkt, die größte geschäftliche Bedeutung. Natürlich können Sie Rechte, wenn nötig, viel kleinteiliger festlegen – etwa indem Sie Personen am Drucken, Bearbeiten usw. hindern. Behandeln Sie die kleinteiligeren Einschränkungen jedoch als Ausnahme für Dokumente, die wirklich hohe Sicherheitsstufen benötigen, und implementieren Sie diese restriktiveren Richtlinien nicht am ersten Tag, sondern gehen Sie eher stufenweise vor.

## Welche Features können mit verschiedenen Abonnements für Azure RMS verwendet werden?
Bei kostenpflichtigen Abonnements, die Azure RMS unterstützen (Office 365, Azure RMS Premium und Enterprise Mobility Suite), gibt es hinsichtlich der unterstützten RMS-Features einige Unterschiede. Eine Liste dieser Funktionen finden Sie unter [Vergleich der Rights Management Services(RMS)-Angebote](http://technet.microsoft.com/dn858608).

Das kostenlose Abonnement, das Azure RMS unterstützt (RMS for Individuals), unterstützt das Nutzen von Inhalten, die durch die Azure RMS geschützt sind. Weitere Informationen finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md).

## Wo kann ich technische Informationen über das kostenlose Azure RMS-Abonnement (RMS for Individuals) erhalten – um beispielsweise Informationen über die tatsächliche Funktionsweise, die Steuerung der Konten und Domänen zu erhalten, die nicht verwendet werden können?
Antworten auf diese Fragen finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md) und in verwandten Artikeln.

## Wie erhalten wir erneut Zugriff auf Dateien, die von einem Mitarbeiter geschützt wurden, der die Organisation verlassen hat?
Verwenden Sie die Administratorfunktion von Azure RMS, über die autorisierte Benutzer volle Besitzerrechte für alle Nutzungslizenzen erhalten, die vom RMS-Mandanten Ihrer Organisation gewährt wurden. Dieselbe Funktion ermöglicht darüber hinaus autorisierten Diensten ggf. die Indizierung und Inspektion von Dateien.

Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md).

## Kann Rights Management Bildschirmaufnahmen verhindern?
Rights Management kann dadurch, dass es das **Nutzungsrecht** [Kopieren](../deploy-use/configure-usage-rights.md) nicht gewährt, für viele Bildschirmaufnahmetools, die häufig auf Windows-Plattformen (Windows 7, Windows 8.1, Windows 10, Windows Phone) und unter Android verwendet werden, das Erstellen von Bildschirmaufnahmen (Screenshots) verhindern. Auf iOS- und Mac-Geräten ist es aber für keine App zulässig, Bildschirmaufnahmen zu verhindern, und Browser (z. B. bei Verwendung mit Outlook Web App und Office Online) können ebenfalls keine Bildschirmaufnahmen verhindern.

Das Verhindern von Bildschirmaufnahmen kann dabei helfen, versehentliche oder fahrlässige Offenlegung von vertraulichen oder sensiblen Informationen zu vermeiden. Es gibt aber viele Möglichkeiten, wie Benutzer die auf dem Bildschirm angezeigten Daten weitergeben können. Das Erstellen von Screenshots ist nur eine davon. Beispielsweise kann ein Benutzer, der die angezeigten Informationen vorsätzlich weitergeben möchte, sie mit der Kamera seines Handys abfotografieren, sie abtippen oder einfach mündlich einer anderen Person mitteilen.

Wie diese Beispiele zeigen, kann Technologie selbst dann, wenn alle Plattformen und jegliche Software die Rights Management-APIs unterstützen würden, um Bildschirmaufnahmen zu blockieren, nicht allein Benutzer davon abhalten, Daten offenzulegen, für die dies nicht passieren sollte. Rights Management kann helfen, Ihre wichtigen Daten mithilfe von Autorisierungen und Nutzungsrichtlinien zu schützen, aber Sie sollten diese Lösung für die Rechteverwaltung im Unternehmen durch andere Kontrollmaßnahmen ergänzen. Arbeiten Sie z. B. mit physischen Sicherheitskontrollen, prüfen und überwachen Sie die Mitarbeiter, die zum Zugriff auf Unternehmens- oder Organisationsdaten autorisiert sind, und investieren Sie in Benutzerschulungen, damit die Benutzer verstehen, welche Daten nicht weitergegeben oder geteilt werden dürfen.

## Welcher Unterschied besteht zwischen dem Schützen einer E-Mail mit der Option „Nicht weiterleiten“ und dem Schützen mit einer Vorlage, die die Berechtigung „Weiterleiten“ nicht gewährt?

Trotz ihres Namens und ihres Erscheinungsbilds ist die Option **Nicht weiterleiten** weder das Gegenteil der Berechtigung „Weiterleiten“, noch eine Vorlage. Es handelt sich vielmehr um eine Reihe von Berechtigungen, die neben dem Beschränken des Weiterleitens von E-Mail-Nachrichten das Kopieren, Drucken und Speichern von Anhängen beschränkt. Die Berechtigungen werden über die ausgewählten Empfänger dynamisch auf Benutzer angewendet, und nicht statisch durch den Administrator zugewiesen. Weitere Informationen finden Sie im Abschnitt [Option „Nicht weiterleiten“ für E-Mails](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) in [Konfigurieren von Nutzungsrechten für Azure Rights Management](../deploy-use/configure-usage-rights.md).


## Wo finde ich weitere Informationen zur Azure RMS – wie z. B. rechtliche Hinweise, Informationen zur Kompatibilität und SLAs?
Azure RMS unterstützt weitere Dienste und verwendet zusätzliche Dienste. Wenn Sie Informationen zur Azure RMS suchen, jedoch nicht zur Verwendung des Azure RMS-Diensts, sehen Sie sich folgende Ressourcen an:

**Rechtliche Hinweise und Datenschutz:**

-   Informationen zur Microsoft Azure-Vereinbarung: [Microsoft Azure-Vereinbarung](http://azure.microsoft.com/support/legal/subscription-agreement/)

-   Informationen zum Microsoft Azure-Datenschutz: [Datenschutzerklärung zu Microsoft Azure](http://azure.microsoft.com/support/legal/privacy-statement/)

**Sicherheit, Compliance und Überwachung:**

Weitere Informationen finden Sie im Abschnitt [Sicherheits-, Compliance- und gesetzliche Anforderungen](../understand-explore/azure-rms-problems-it-solves.md#security-compliance-and-regulatory-requirements) im Artikel [Welche Probleme werden von Azure RMS gelöst?](../understand-explore/azure-rms-problems-it-solves.md). Zusätzlich:

-   Informationen zu externen Zertifizierungen für Azure RMS: [Microsoft Azure Trust Center](http://azure.microsoft.com/support/trust-center/)

-   FIPS 140-Informationen: [FIPS 140-Überprüfung](https://technet.microsoft.com/library/security/cc750357.aspx)

**Vereinbarungen zum Servicelevel:**

-   Vereinbarungen zum Servicelevel für Azure RMS nach ausgewählter Region: [Herunterladen von der Produktlizenzierungs-Suchseite](http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37)

    - Klicken Sie beispielsweise auf **OnlineSvcsConsolidatedSLA(WW)(English)(March2016)**, um die Vereinbarung zum Servicelevel für Nordamerika vom März 2016 herunterzuladen.

-   Vereinbarung zum Servicelevel für Azure Active Directory: [Vereinbarungen zum Servicelevel](http://azure.microsoft.com/support/legal/sla/)

**Dokumentation:**

-   Azure Active Directory-Dokumentationswebsite: [Azure Active Directory](http://azure.microsoft.com/documentation/services/active-directory/)

-   Azure Active Directory-Bibliothek: [Azure Active Directory](http://msdn.microsoft.com/library/azure/jj673460.aspx)

-   Office 365-Bibliothek: [Office 365](http://technet.microsoft.com/library/dn127064%28v=office.14%29.aspx)

## Wie gehe ich vor, wenn meine Frage hier nicht behandelt wird?
Verwenden Sie die Links und Ressourcen, die unter [Informationen und Support für Azure Rights Management](information-support.md) aufgelistet sind.

Darüber hinaus gibt es häufig gestellte Fragen (FAQs) für Endbenutzer:

-   [Häufig gestellte Fragen zur Rights Management-Freigabeanwendung für Windows](https://technet.microsoft.com/dn467883)

-   [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für mobile und für Mac-Plattformen](https://technet.microsoft.com/dn451248)

-   [Häufig gestellte Fragen zur Dokumentenverfolgung](http://go.microsoft.com/fwlink/?LinkId=523977)

Diese FAQ-Seite wird regelmäßig aktualisiert. Dabei werden die neuen Beiträge in den Ankündigungen zu den monatlichen Dokumentationsaktualisierungen im Blog des [RMS-Teams (Microsoft Rights Management)](http://blogs.technet.com/b/rms/) aufgelistet.

> [!TIP]Sie können das [docs-Tag](http://blogs.technet.com/b/rms/archive/tags/docs/) im Blog verwenden, um diese Dokumentationsankündigungen leichter zu finden.




<!--HONumber=Jun16_HO2-->


