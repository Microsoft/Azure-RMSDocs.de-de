---
title: "Häufig gestellte Fragen zum Azure Rights Management-Dienst von Azure Information Protection für den Schutz von Daten | Azure Information Protection"
description: "Hier finden Sie einige häufig gestellte Fragen zum Azure Rights Management-Dienst (Azure RMS) von Azure Information Protection für den Schutz von Daten."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/16/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: eb9b9c1308abe6b1b5803cba7ba254d54cbac812
ms.openlocfilehash: d3d11dba936ca8901b701008e55df8d73be8bded


---

# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Häufig gestellte Fragen zum Schutz von Daten in Azure Information Protection

>*Gilt für: Azure Information Protection, Office 365*

Haben Sie eine Frage zum Azure Rights Management-Dienst von Azure Information Protection für den Schutz von Daten? Vielleicht finden Sie hier eine Antwort darauf. 

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Müssen sich Dateien in der Cloud befinden, um von Azure Rights Management geschützt werden zu können?
Nein, das ist ein weit verbreitetes Missverständnis. Für den Prozess zum Schutz von Daten des Azure Rights Management-Diensts (und von Microsoft) gilt, dass er Ihre Daten weder sieht noch speichert. Informationen, die Sie schützen, werden niemals an Azure gesendet oder dort gespeichert – es sei denn, dass Sie diese explizit in Azure speichern oder einen anderen Cloud-Dienst verwenden, der sie in Azure speichert. 

Weitere Informationen finden Sie unter [Funktionsweise von Azure RMS. Details](../understand-explore/how-does-it-work.md). Dort ist beschrieben, wie eine geheime Cola-Formel, die lokal erstellt und gespeichert wurde, von Azure Rights Management geschützt wird, aber lokal bleibt.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Was ist der Unterschied zwischen Azure Rights Management-Verschlüsselung und Verschlüsselung in andere Microsoft-Clouddiensten?

Microsoft stellt mehrere Verschlüsselungstechnologien zum Schutz Ihrer Daten in verschiedenen und häufig sich ergänzenden Szenarien zur Verfügung. Während Office 365 z. B. Verschlüsselung von in Office 365 gespeicherten ruhenden Daten bietet, verschlüsselt und schützt der Azure Rights Management-Dienst von Azure Information Protection Ihre Daten unabhängig von Speicherort oder Übertragungsmethode.

Diese Verschlüsselungstechnologien ergänzen sich, und zur Verwendung müssen Sie sie unabhängig voneinander aktivieren und konfigurieren. Dabei besteht möglicherweise die Option, einen eigenen Schlüssel für die Verschlüsselung bereitzustellen, ein Szenario, das auch als BYOK (Bring-Your-Own-Key) bezeichnet wird. Das Aktivieren von BYOK für eine dieser Technologien hat keinen Einfluss auf andere. Sie können BYOK z. B. für Azure Information Protection verwenden und für andere Verschlüsselungstechniken nicht verwenden (und umgekehrt). Die von den unterschiedlichen Technologien verwendeten Schlüssel können gleich oder verschieden sein, je nachdem, wie Sie die Verschlüsselungsoptionen für die einzelnen Dienste konfigurieren.

## <a name="can-i-integrate-the-azure-rights-management-service-with-my-onpremises-servers"></a>Kann ich den Azure Rights Management-Dienst auf lokalen Servern integrieren?
Ja. Azure Rights Management kann in lokale Server, etwa Exchange Server, SharePoint und Windows-Dateiserver, integriert werden. Dazu verwenden Sie den [Rights Management-Connector](../deploy-use/deploy-rms-connector.md). Wenn Sie nur an der Nutzung der Dateiklassifizierungsinfrastruktur (FCI, File Classification Infrastructure) mit Windows Server interessiert sind, können Sie auch die [RMS Protection-Cmdlets](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx) verwenden. Sie können Ihre Active Directory-Domänencontroller auch mit Azure AD synchronisieren und zusammenführen, um eine übergangslosere Authentifizierungshandhabung für Benutzer zu erreichen. Dazu können Sie beispielsweise [Azure AD Connect](http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/)verwenden.

Azure Rights Management generiert und verwaltet XrML-Zertifikate automatisch nach Bedarf und verwendet daher keine lokale PKI. Weitere Informationen zur Verwendung von Zertifikaten in Azure Rights Management finden Sie im Abschnitt [Exemplarische Vorgehensweise zur Funktionsweise von Azure RMS: Erste Verwendung, Inhaltsschutz, Inhaltsnutzung](../understand-explore/how-does-it-work.md#walkthrough-of-how-azure-rms-works-first-use-content-protection-content-consumption) des Artikels [Funktionsweise von Azure RMS](../understand-explore/how-does-it-work.md).

## <a name="where-can-i-find-information-about-3rd-party-solutions-that-integrate-with-azure-rms"></a>Wo finde ich Informationen zu Drittanbieterlösungen, die in Azure RMS integrierbar sind?

Viele Softwarehersteller verfügen bereits über Lösungen oder sind dabei, Lösungen zu implementieren, die in Azure Rights Management integrierbar sind – und die Liste erweitert sich sehr schnell. Es könnte hilfreich sein, den [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) und die neuesten Updates von [Dan Plastina@TheRMSGuy](https://twitter.com/TheRMSGuy) auf Twitter zu lesen. Wenn Sie jedoch eine spezifische Frage haben, schicken Sie eine E-Mail an das Information Protection-Team: askipteam@microsoft.com.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Gibt es ein Management Pack oder einen ähnlichen Überwachungsmechanismus für den RMS-Connector?

Obwohl der Rights Management-Connector Informationen, Warn- und Fehlermeldungen im Ereignisprotokoll protokolliert, gibt es kein Management Pack, das die Überwachung für diese Ereignisse enthält. Eine Liste der Ereignisse und der dazugehörigen Beschreibungen mit Informationen, die Sie bei Ihren Entscheidungen hinsichtlich Korrekturmaßnahmen unterstützen, finden Sie jedoch unter [Überwachen des Azure Rights Management-Connectors](../deploy-use/monitor-rms-connector.md).

## <a name="do-you-need-to-be-a-global-admin-to-configure-azure-rms-or-can-i-delegate-to-other-administrators"></a>Werden zum Konfigurieren von Azure RMS globale Administratorrechte benötigt, oder kann ich diese Aufgabe an andere Administratoren delegieren?

Globale Administratoren für einen Office 365- oder Azure AD-Mandanten können natürlich alle administrativen Aufgaben für den Azure Rights Management-Dienst ausführen. Wenn Sie jedoch anderen Benutzern Administratorrechte zuweisen möchten, können Sie hierfür das Azure RMS-PowerShell-Cmdlet [Add-AadrmRoleBasedAdministrator](https://msdn.microsoft.com/library/dn629417.aspx) verwenden. Sie können diese Administratorrolle über ein Benutzerkonto oder eine Gruppe zuweisen. Es sind zwei Rollen verfügbar: **globaler Administrator** und **Connector-Administrator**. 

Wie die Namen erkennen lassen, gewährt die erste Rolle die Berechtigungen zum Ausführen aller administrativen Aufgaben für Azure Rights Management (ohne dass globale Administratorrechte für andere Clouddienste gewährt werden). Die zweite Rolle gewährt nur die Berechtigungen zum Ausführen des Rights Management-Connectors (RMS).

Einige Dinge sind zu beachten:

- Nur globale Administratoren für Office 365 und globale Administratoren für Azure AD können die Verwaltungsportale (Office 365 Admin Center oder das klassische Azure-Portal) zum Konfigurieren von Azure RMS verwenden. Benutzer, denen Sie die Rolle „GlobalAdministrator“ für Azure RMS zuweisen, müssen Azure RMS-PowerShell-Befehle zum Konfigurieren von Azure RMS verwenden. Hilfe dazu, wie Sie die richtigen Cmdlets für bestimmte Aufgaben finden, erhalten Sie unter [Verwalten von Azure Rights Management unter Verwendung der Windows PowerShell](../deploy-use/administer-powershell.md).

- Wenn Sie [Onboarding-Steuerelemente](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) konfiguriert haben, wird die Fähigkeit zum Verwalten von Azure RMS mit Ausnahme des RMS-Connectors hierdurch nicht beeinflusst. Wenn sie Onboarding-Steuerelemente beispielsweise so konfiguriert haben, dass die Fähigkeit, Inhalte zu schützen, auf die Gruppe „IT-Abteilung“ beschränkt ist, muss das von Ihnen zum Installieren und Konfigurieren des RMS-Connectors verwendete Konto ein Member dieser Gruppe sein. 

- Kein Administrator für Azure RMS (weder der globale Administrator des Mandanten noch ein globaler Azure RMS-Administrator) kann automatisch den Schutz von Dokumenten oder E-Mails entfernen, die von Azure RMS geschützt wurden. Dies ist nur Benutzern möglich, denen Administratorrechte für Azure RMS zugewiesen sind, und zwar nur dann, wenn das Superuserfeature aktiviert ist. Jedoch können der globale Administrator des Mandanten und jeder globale Azure RMS-Administrator Benutzern Administratorrechte zuweisen, einschließlich des eigenen Kontos. Sie können auch das Superuserfeature aktivieren. Diese Aktionen werden im Azure RMS-Administratorprotokoll aufgezeichnet. Weitere Informationen finden Sie im Abschnitt „Bewährte Sicherheitsmethoden“ unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md). 


## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Ich habe eine Hybridbereitstellung von Exchange mit einigen Benutzern auf Exchange Online und anderen auf Exchange Server – wird dies von Azure RMS unterstützt?
Ja, und das Gute ist, dass Benutzer über zwei Exchange-Bereitstellungen hinweg E-Mails und Anlagen nahtlos schützen sowie geschützte E-Mails und Anlagen nutzen können. Führen Sie für diese Konfiguration folgende Schritte aus: [Aktivieren von Azure RMS](../deploy-use/activate-service.md) , [Aktivieren von IRM für Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx)und [Bereitstellen und Konfigurieren des RMS-Connectors](../deploy-use/deploy-rms-connector.md) für Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Wenn ich diesen Schutz in meiner Produktionsumgebung verwende, ist mein Unternehmen dann an die Lösung gebunden und läuft andernfalls Gefahr, den Zugriff auf Inhalte zu verlieren, die wir mit Azure RMS geschützt haben?
Nein, Sie behalten immer die Kontrolle über Ihre Daten und können weiterhin darauf zugreifen, selbst wenn Sie sich entscheiden, den Azure Rights Management-Dienst nicht mehr zu verwenden. Weitere Informationen finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md).

Bevor Sie Ihre Azure RMS-Bereitstellung außer Betrieb setzen, würden wir jedoch gerne erfahren bzw. verstehen, warum Sie diese Entscheidung getroffen haben. Wenn Azure Rights Management Ihren geschäftlichen Anforderungen nicht gerecht wird, können Sie Kontakt mit uns aufnehmen, um zu erfahren, ob in naher Zukunft neue Funktionen geplant oder ob Alternativen verfügbar sind. Senden Sie eine E-Mail-Nachricht an [AskIPTeam@Microsoft.com](mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS). Wir freuen uns darauf, Ihre technischen und geschäftlichen Anforderungen mit Ihnen zu besprechen.

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Kann ich steuern, welche Benutzer Azure RMS verwenden können, um Inhalte zu schützen?
Ja, der Azure Rights Management-Dienst verfügt für dieses Szenario über Onboarding-Steuerelemente. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboardingsteuerungsrichtlinien für eine stufenweise Bereitstellung](../deploy-use/activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) im Artikel [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Kann ich verhindern, dass Benutzer geschützte Dokumente für bestimmte Organisationen freigeben?
Einer der größten Vorteile der Verwendung des Azure Rights Management-Diensts für den Schutz von Daten besteht darin, dass er B2B-Zusammenarbeit unterstützt, ohne dass Sie explizite Vertrauensstellungen für jede Partnerorganisation konfigurieren müssen, denn Azure AD übernimmt die Authentifizierung für Sie.

Es gibt keine Verwaltungsoption, mit der verhindert werden kann, dass Benutzer Dokumente geschützt für bestimmte Organisationen freigeben. Angenommen, Sie möchten eine Organisation blockieren, der Sie nicht vertrauen oder die ein konkurrierendes Unternehmen hat. Den Azure Rights Management-Dienst daran zu hindern, geschützte Dokumente an Benutzer in dieser Organisationen zu senden, wäre nicht sinnvoll, da Benutzer ihre Dokumente dann ungeschützt freigeben würden, und das ist wahrscheinlich genau das, was in diesem Szenario nicht geschehen soll! Beispielsweise könnten Sie nicht erkennen, wer vertrauliche Unternehmensdokumente für welche Benutzer in dieser Organisation freigibt, dies können Sie jedoch, wenn das Dokument (oder die E-Mail) durch den Azure Rights Management-Dienst geschützt wird.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Wenn ich ein geschütztes Dokument für eine Person außerhalb meiner Firma freigebe, wie wird dieser Benutzer authentifiziert?
Der Azure Rights Management-Dienst verwendet immer ein Azure Active Directory-Konto und eine zugeordnete E-Mail-Adresse für die Benutzerauthentifizierung, sodass sich eine nahtlose Business-to-Business-Zusammenarbeit für Administratoren ergibt. Wenn die andere Organisation Azure-Dienste verwendet, haben Benutzer bereits Konten in Azure Active Directory, selbst wenn diese Konten lokal erstellt und verwaltet und dann mit Azure synchronisiert werden. Wird in der Organisation Office 365 verwendet, verwendet dieser Dienst (im Hintergrund) ebenfalls Azure Active Directory für die Benutzerkonten. Wenn die Organisation des Benutzers nicht über verwaltete Konten in Azure verfügt, können sich Benutzer für [RMS for Individuals](../understand-explore/rms-for-individuals.md) registrieren. Dadurch werden ein nicht verwalteter Azure-Mandant und ein Verzeichnis für die Organisation mit einem Konto für den Benutzer erstellt, sodass dieser Benutzer (und weitere Benutzer) dann für den Azure Rights Management-Dienst authentifiziert werden kann.

Die Authentifizierungsmethode für diese Konten kann unterschiedlich sein, je nachdem, wie der Administrator in der anderen Organisation die Azure Active Directory-Konten konfiguriert hat. Beispielsweise können Kennwörter, die für diese Konten erstellt wurden, Multi-Factor Authentication (MFA, mehrstufige Authentifizierung), Verbund oder Kennwörter verwendet werden, die in Active Directory-Domänendienste erstellt und dann mit Azure Active Directory synchronisiert wurden.

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Kann ich externe Benutzer (die nicht zu meinem Unternehmen gehören) zu benutzerdefinierten Vorlagen hinzufügen?
Ja. Ein Erstellen von benutzerdefinierten Vorlagen, die Endbenutzer (und Administratoren) in Anwendungen auswählen können, ermöglicht es Benutzern, schnell und problemlos Informationsschutz anzuwenden, indem sie vordefinierte Richtlinien verwenden, die Sie definiert haben. Eine der Einstellungen in der Vorlage bestimmt, wer auf den Inhalt zugreifen kann, und Sie können Benutzer und Gruppen aus Ihrer Organisation sowie Benutzer angeben, die nicht zu Ihrer Organisation gehören.

Um Benutzer anzugeben, die nicht Ihrer Organisation angehören, fügen Sie diese als Kontakte einer Gruppe hinzu, die Sie beim Konfigurieren Ihrer Vorlagen im klassischen Azure-Portal auswählen. Sie können auch das [Windows PowerShell-Modul für Azure Rights Management](../deploy-use/install-powershell.md) verwenden:

-   **Erstellen oder Aktualisieren der Vorlage mithilfe eines Rechtedefinitionsobjekts**.    Geben Sie die externen E-Mail-Adressen und ihre Rechte in einem Rechtedefinitionsobjekt an, das Sie dann zum Erstellen oder Aktualisieren einer Vorlage verwenden. Sie geben das Rechtedefinitionsobjekt an, indem Sie mit dem [New-AadrmRightsDefinition](https://msdn.microsoft.com/library/azure/dn727080.aspx)-Cmdlet eine Variable erstellen und diese Variable anschließend mit dem [Add-AadrmTemplate](https://msdn.microsoft.com/library/azure/dn727075.aspx)-Cmdlet (für eine neue Vorlage) oder mit dem [Set-AadrmTemplateProperty](https://msdn.microsoft.com/library/azure/dn727076.aspx)-Cmdlet (zum Ändern einer vorhandenen Vorlage) für den „-RightsDefinition“-Parameter bereitstellen. Wenn Sie jedoch diese Benutzer zu einer vorhandenen Vorlage hinzufügen, müssen Sie nicht nur für die externen Benutzer Rechtedefinitionsobjekte definieren, sondern auch für die vorhandenen Gruppen in den Vorlagen.

Weitere Informationen zu benutzerdefinierten Vorlagen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).

## <a name="does-azure-rms-work-with-dynamic-groups-in-azure-ad"></a>Funktioniert Azure RMS mit dynamischen Gruppen in Azure AD?
Mit einer Azure AD Premium-Funktion können Sie die dynamische Mitgliedschaft für Gruppen durch Angeben von [attributbasierten Regeln](https://azure.microsoft.com/documentation/articles/active-directory-accessmanagement-groups-with-advanced-rules/) konfigurieren. Beim Erstellen einer Sicherheitsgruppe in Azure AD unterstützt dieser Gruppentyp die dynamische Mitgliedschaft, aber keine E-Mail-Adresse. Er kann daher nicht mit dem Azure Rights Management-Dienst verwendet werden. Allerdings können Sie jetzt einen neuen Gruppentyp in Azure AD erstellen, der die dynamische Mitgliedschaft und E-Mails unterstützt. Wenn Sie eine neue Gruppe im klassischen Azure-Portal hinzufügen, können Sie als **GRUPPENTYP** die Option **Office 365-„Vorschau“** auswählen. Da diese Gruppe E-Mail-fähig ist, können Sie sie mit Azure Rights Management-Schutz verwenden.

Wie der Optionsname deutlich zeigt, befindet sich dieser neue Gruppentyp noch in der Vorschauphase. Mit zusätzlichen Funktionen und einer neuen Dokumentation kann also in Zukunft gerechnet werden. In der Zwischenzeit möchten wir bestätigen, dass Sie diesen neuen Gruppentyp mit Azure Rights Management-Schutz verwenden können.


## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Welche Geräte und welche Dateitypen werden von Azure RMS unterstützt?
Eine Liste mit Geräten, die den Azure Rights Management-Dienst unterstützen, finden Sie unter [Clientgeräte mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-client-devices.md). Da derzeit nicht alle unterstützten Geräte alle Rights Management-Funktionen unterstützen, sollten Sie sich auch die Tabelle unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-applications.md) ansehen.

Der Azure Rights Management-Diensts kann sämtliche Dateitypen unterstützen. Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen stellt Azure Rights Management nativen Schutz bereit, der Verschlüsselung und die Durchsetzung von Rechten (Berechtigungen) umfasst. Für alle anderen Anwendungen und Dateitypen bietet generischer Schutz Dateiverkapselung und Authentifizierung, damit überprüft wird, ob ein Benutzer zum Öffnen der Datei autorisiert ist.

Eine Liste der Dateierweiterungen, für die Azure Rights Management native Unterstützung bietet, finden Sie im Abschnitt [Unterstützte Dateitypen und Dateierweiterungen](../rms-client/sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) des [Administratorhandbuchs der Rights Management-Freigabeanwendung](../rms-client/sharing-app-admin-guide.md). Nicht aufgeführte Dateinamenerweiterungen werden mithilfe der RMS-Freigabeanwendung unterstützt, die automatisch generischen Schutz auf diese Dateien anwendet.

## <a name="when-i-open-an-rmsprotected-office-document-does-the-associated-temporary-file-become-rmsprotected-as-well"></a>Wenn ich ein RMS-geschütztes Office-Dokument öffne, wird die dazugehörige temporäre Datei ebenfalls von RMS geschützt?

Nein. Die dazugehörige temporäre Datei enthält in diesem Szenario keine Daten aus dem Originaldokument, sondern nur das, was der Benutzer eingibt, während die Datei geöffnet ist. Im Gegensatz zur ursprünglichen Datei soll die temporäre Datei offensichtlich nicht freigegeben werden und verbleibt auf dem Gerät, geschützt durch lokale Sicherheitskontrollen wie BitLocker und EFS.

## <a name="we-really-want-to-use-byok-with-azure-information-protection-but-learned-that-this-isnt-compatible-with-exchange-onlinewhats-your-advice"></a>Wir möchten BYOK mit Azure Information Protection verwenden, haben jedoch erfahren, dass diese Kombination nicht mit Exchange Online kompatibel ist. Wie lautet Ihre Empfehlung?
Nehmen Sie diese derzeitige Einschränkung nicht zum Anlass für eine Verzögerung der Einführung des Azure Rights Management-Diensts von Azure Information Protection. Wenn Sie Exchange Online verwenden und BYOK (Bring Your Own Key) nutzen möchten, empfehlen wir, dass Sie Azure Information Protection im Standard-Schlüsselverwaltungsmodus bereitstellen, in dem Microsoft Ihren Schlüssel generiert und verwaltet. Auf diese Weise erhalten Sie jetzt alle Vorteile bezüglich des Schutzes wichtiger Dateien und E-Mails mit der Option, zu einem späteren Zeitpunkt zu BYOK zu wechseln (z. B. wenn Exchange Online BYOK unterstützt). Wenn Sie zu BYOK wechseln, bleiben Ihre zuvor geschützten Dokumente und E-Mails über einen archivierten Schlüssel zugänglich.

Wenn Ihre Unternehmensrichtlinien jedoch erfordern, dass Sie ein Hardwaresicherheitsmodul (HSM) verwenden, und dies Ihre Azure Information Protection-Bereitstellung blockieren würde, können Sie auch jetzt Azure Information Protection mit BYOK bereitstellen und für Exchange eine verminderte Rights Management-Schutzfunktion verwenden. Weitere Informationen finden Sie unter [BYOK – Preise und Einschränkungen](../plan-design/byok-price-restrictions.md) in [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Eine Funktion, die ich suche, scheint nicht mit SharePoint-geschützten Bibliotheken zu funktionieren – ist die Unterstützung dieser Funktion geplant?
Derzeit unterstützt SharePoint mit Rights Management geschützte Dokumente durch Verwenden von IRM-geschützten Bibliotheken, die weder benutzerdefinierte Vorlagen noch Dokumentkontrolle noch einige andere Funktionen unterstützen. Weitere Informationen finden Sie im Abschnitt [SharePoint Online und SharePoint Server](../understand-explore/office-apps-services-support.md#sharepoint-online-and-sharepoint-server) im Artikel [Office-Anwendungen und -Dienste](../understand-explore/office-apps-services-support.md).

Wenn Sie an einer bestimmten Funktion interessiert sind, die noch nicht unterstützt wird, sollten Sie die Ankündigungen im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) (Informationen in englischer Sprache zu Enterprise Mobility und Sicherheit) verfolgen.

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Wie konfiguriere ich OneDrive for Business in SharePoint Online, sodass Benutzer ihre Dateien sicher für Personen innerhalb und außerhalb des Unternehmens freigeben können?
Als Office 365-Administrator konfigurieren Sie dies normalerweise nicht. Eine solche Konfiguration erfolgt durch Benutzer.

Als SharePoint-Websiteadministrator aktivieren und konfigurieren Sie IRM für eine SharePoint-Bibliothek, deren Besitzer Sie sind. OneDrive for Business ist so konzipiert, dass die Benutzer IRM für ihre eigene OneDrive for Business-Bibliothek aktivieren und konfigurieren.  Mithilfe von PowerShell können Sie das jedoch für sie übernehmen. Anweisungen finden Sie im Abschnitt [SharePoint Online und OneDrive for Business: IRM-Konfiguration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) im Artikel [Office 365: Konfigurationen für Clients und Onlinedienste](../deploy-use/configure-office365.md).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Gibt es besondere Tipps und Tricks für eine erfolgreiche Bereitstellung?
Nachdem wir viele Bereitstellungen begleitet und uns mit Kunden, Partnern, Beratern und Supportmitarbeitern unterhalten haben – ist das einer der größten Tipps, die wir aus unserer Erfahrung weitergeben können: **Entwerfen Sie einfache Rechterichtlinien, und stellen Sie sie entsprechend bereit**.

Da Azure Information Protection sichere Freigaben mit praktisch jeder Person unterstützt, können Sie bei der Reichweite des Schutzes Ihrer Daten Ehrgeiz entwickeln. Seien Sie aber konservativ bei Ihren Rechterichtlinien. Für die meisten Organisationen hat die Vermeidung von Datenlecks durch Anwenden der standardmäßigen Rechterichtlinienvorlage, die den Zugriff auf Personen in der eigenen Organisation einschränkt, die größte geschäftliche Bedeutung. Natürlich können Sie Rechte, wenn nötig, viel kleinteiliger festlegen – etwa indem Sie Personen am Drucken, Bearbeiten usw. hindern. Behandeln Sie die kleinteiligeren Einschränkungen jedoch als Ausnahme für Dokumente, die wirklich hohe Sicherheitsstufen benötigen, und implementieren Sie diese restriktiveren Richtlinien nicht am ersten Tag, sondern gehen Sie eher stufenweise vor.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Wie erhalten wir erneut Zugriff auf Dateien, die von einem Mitarbeiter geschützt wurden, der die Organisation verlassen hat?
Verwenden Sie die Administratorfunktion von Azure RMS, über die autorisierte Benutzer volle Besitzerrechte für alle Nutzungslizenzen erhalten, die vom RMS-Mandanten Ihrer Organisation gewährt wurden. Dieselbe Funktion ermöglicht darüber hinaus autorisierten Diensten ggf. die Indizierung und Inspektion von Dateien.

Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md).

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Wenn ich die Sperrung in der Website zur Dokumentnachverfolgung teste, erhalte ich eine Meldung, die angibt, dass Personen für bis zu 30 Tage auf das Dokument zugreifen können. Kann ich diesen Zeitraum konfigurieren?

Ja. Diese Meldung gibt die Nutzungslizenz für diese bestimmte Datei wieder. Eine Nutzungslizenz ist ein pro-Dokument-Zertifikat, das einem Benutzer gewährt wird, der eine geschützte Datei- oder E-Mail-Nachricht öffnet. Dieses Zertifikat enthält Benutzerrechte für die Datei oder E-Mail-Nachricht und den Verschlüsselungsschlüssel, der zum Verschlüsseln des Inhalts verwendet wurde, und zusätzliche Zugriffseinschränkungen, die in der Richtlinie für das Dokument definiert wurden. Wenn die Gültigkeitsdauer der Nutzungslizenz abgelaufen ist, und der Benutzer versucht, die Datei oder die E-Mail zu öffnen, müssen deren Benutzeranmeldeinformationen neu an den Azure Rights Management-Dienst übermittelt werden. 

Wenn Sie eine Datei widerrufen, kann diese Aktion nur erzwungen werden, wenn der Benutzer sich beim Azure Rights Management-Dienst authentifiziert. Wenn eine Datei über eine gültige Nutzungslizenz von 30 Tagen verfügt, und der Benutzer das Dokument bereits geöffnet hat, erhält dieser Benutzer weiterhin Zugriff auf das Dokument, solange die Nutzungslizenz gültig ist. Wenn die Nutzungslizenz ausläuft, muss sich der Benutzer erneut authentifizieren. Zu diesem Zeitpunkt wird der Zugriff für den Benutzer verweigert, da das Dokument nun gesperrt ist.

Der Standardwert für die Gültigkeitsdauer der Nutzungslizenz beträgt für einen Mandanten 30 Tage, und Sie können diesen Wert mithilfe des PowerShell-Cmdlets [Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx) konfigurieren. Diese Einstellung kann durch eine restriktivere Einstellung in einer benutzerdefinierten Vorlage überschrieben werden. 

Die Mandanteneinstellung und die Vorlageneinstellung können von Benutzern überschrieben werden, wenn sie die RMS-Freigabeanwendung verwenden und die Option **Zulassen, dass ich den Zugriff auf diese Dokumente sofort widerrufe** auswählen. Diese Einstellung legt effektiv die Gültigkeitsdauer der Nutzungslizenz auf 0 fest. 

Weitere Informationen und Beispiele für die Funktionsweise der Nutzungslizenz finden Sie in der ausführlichen Beschreibung für [Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx).

## <a name="can-rights-management-prevent-screen-captures"></a>Kann Rights Management Bildschirmaufnahmen verhindern?
Rights Management kann dadurch, dass es das **Nutzungsrecht** [Kopieren](../deploy-use/configure-usage-rights.md) nicht gewährt, für viele Bildschirmaufnahmetools, die häufig auf Windows-Plattformen (Windows 7, Windows 8.1, Windows 10, Windows Phone) und unter Android verwendet werden, das Erstellen von Bildschirmaufnahmen (Screenshots) verhindern. Auf iOS- und Mac-Geräten ist es aber für keine App zulässig, Bildschirmaufnahmen zu verhindern, und Browser (z. B. bei Verwendung mit Outlook Web App und Office Online) können ebenfalls keine Bildschirmaufnahmen verhindern.

Das Verhindern von Bildschirmaufnahmen kann dabei helfen, versehentliche oder fahrlässige Offenlegung von vertraulichen oder sensiblen Informationen zu vermeiden. Es gibt aber viele Möglichkeiten, wie Benutzer die auf dem Bildschirm angezeigten Daten weitergeben können. Das Erstellen von Screenshots ist nur eine davon. Beispielsweise kann ein Benutzer, der die angezeigten Informationen vorsätzlich weitergeben möchte, sie mit der Kamera seines Handys abfotografieren, sie abtippen oder einfach mündlich einer anderen Person mitteilen.

Wie diese Beispiele zeigen, kann Technologie selbst dann, wenn alle Plattformen und jegliche Software die Rights Management-APIs unterstützen würden, um Bildschirmaufnahmen zu blockieren, nicht allein Benutzer davon abhalten, Daten offenzulegen, für die dies nicht passieren sollte. Rights Management kann helfen, Ihre wichtigen Daten mithilfe von Autorisierungen und Nutzungsrichtlinien zu schützen, aber Sie sollten diese Lösung für die Rechteverwaltung im Unternehmen durch andere Kontrollmaßnahmen ergänzen. Arbeiten Sie z. B. mit physischen Sicherheitskontrollen, prüfen und überwachen Sie die Mitarbeiter, die zum Zugriff auf Unternehmens- oder Organisationsdaten autorisiert sind, und investieren Sie in Benutzerschulungen, damit die Benutzer verstehen, welche Daten nicht weitergegeben oder geteilt werden dürfen.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Welcher Unterschied besteht zwischen dem Schützen einer E-Mail mit der Option „Nicht weiterleiten“ und dem Schützen mit einer Vorlage, die die Berechtigung „Weiterleiten“ nicht gewährt?

Trotz ihres Namens und ihres Erscheinungsbilds ist die Option **Nicht weiterleiten** weder das Gegenteil der Berechtigung „Weiterleiten“, noch eine Vorlage. Es handelt sich vielmehr um eine Reihe von Berechtigungen, die neben dem Beschränken des Weiterleitens von E-Mail-Nachrichten das Kopieren, Drucken und Speichern von Anhängen beschränkt. Die Berechtigungen werden über die ausgewählten Empfänger dynamisch auf Benutzer angewendet, und nicht statisch durch den Administrator zugewiesen. Weitere Informationen finden Sie im Abschnitt [Option „Nicht weiterleiten“ für E-Mails](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) in [Konfigurieren von Nutzungsrechten für Azure Rights Management](../deploy-use/configure-usage-rights.md).






<!--HONumber=Nov16_HO3-->

