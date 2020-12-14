---
title: 'Häufig gestellte Fragen (FAQs) zu Azure RMS: AIP'
description: Einige häufig gestellte Fragen zum Datenschutzdienst Azure Rights Management (Azure RMS) aus Azure Information Protection.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 12/02/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 3d376446354e591f9a5742d415b7b7cba75bf887
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97382257"
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Häufig gestellte Fragen zum Schutz von Daten in Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Weitere Informationen finden Sie auch in den häufig gestellten Fragen [zum klassischen Client](faqs-classic.md). *

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Haben Sie eine Frage zum Datenschutzdienst Azure Rights Management (Azure RMS) aus Azure Information Protection? Vielleicht finden Sie hier eine Antwort.

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Müssen Dateien in der Cloud gespeichert sein, um durch Azure Rights Management geschützt zu werden?

Nein, das ist ein weit verbreitetes Missverständnis. Der Azure Rights Management Service (und Microsoft) sieht oder speichert Ihre Daten nicht als Teil des Informationsschutzprozesses. Informationen, die Sie schützen, werden niemals an Azure gesendet oder in Azure gespeichert, es sei denn, Sie speichern sie explizit in Azure oder verwenden einen anderen Clouddienst, der sie in Azure speichert.

Weitere Informationen finden Sie unter [wie funktioniert Azure RMS? Im](./how-does-it-work.md) Hintergrund wird erläutert, wie eine geheime Cola-Formel, die lokal erstellt und gespeichert wird, durch den Azure-Rights Management Service geschützt wird, aber lokal bleibt.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Worin besteht der Unterschied zwischen Azure Rights Management Verschlüsselung und Verschlüsselung in anderen Microsoft Cloud Services?

Microsoft stellt mehrere Verschlüsselungstechnologien bereit, die Sie zum Schutz Ihrer Daten in verschiedenen und sich häufig ergänzenden Szenarien verwenden können. Wenn Microsoft 365 z. b. die Verschlüsselung ruhender Daten für in Microsoft 365 gespeicherte Daten bietet, verschlüsselt der Azure-Rights Management Dienst von Azure Information Protection Ihre Daten unabhängig davon, wo Sie sich befinden oder wie Sie übertragen werden.

Diese Verschlüsselungstechnologien ergänzen einander, und ihre Verwendung erfordert, dass sie unabhängig voneinander aktiviert und konfiguriert werden. Wenn Sie so vorgehen, besteht ggf. die Option, einen eigenen Schlüssel für die Verschlüsselung zu verwenden, ein Szenario, das auch als „BYOK“ bezeichnet wird. Die Aktivierung von BYOK für eine dieser Technologien wirkt sich nicht auf die anderen Technologien aus. Sie können BYOK z.B. für Azure Information Protection und nicht für andere Verschlüsselungstechnologien verwenden und umgekehrt. Die Schlüssel, die von diesen verschiedenen Technologien verwendet werden, können gleich oder unterschiedlich sein, je nachdem, wie Sie die Verschlüsselungsoptionen für jeden Dienst konfigurieren.

## <a name="can-i-now-use-byok-with-exchange-online"></a>Kann ich BYOK jetzt mit Exchange Online verwenden?

Ja, Sie können Byok jetzt mit Exchange Online verwenden, wenn Sie die Anweisungen unter [Einrichten neuer Microsoft 365 Nachrichten Verschlüsselungsfunktionen befolgen, die auf Azure Information Protection basieren](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Diese Anweisungen ermöglichen die neuen Funktionen in Exchange Online, die BYOK für den Schutz von Azure-Informationen unterstützen, sowie die neue Office 365-Nachrichtenverschlüsselung.

Weitere Informationen zu dieser Änderung finden Sie in der Blogankündigung: [Office 365-Nachrichtenverschlüsselung mit den neuen Funktionen](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Wo finde ich Informationen zu Lösungen von Drittanbietern, die in Azure RMS integriert werden können?

Viele Softwareanbieter verfügen bereits über Lösungen oder implementieren Lösungen, die sich in Azure Rights Management integrieren lassen, und die Liste wächst rasant. Möglicherweise ist es hilfreich, die Liste der [RMS-fähigen Anwendungen](requirements-applications.md#) zu überprüfen und die neuesten Updates von [Microsoft Mobility@MSFTMobility ](https://twitter.com/MSFTMobility) auf Twitter zu erhalten. Lesen Sie auch den [Entwicklerleitfaden](./develop/developers-guide.md), und stellen Sie spezifische Integrationsfragen auf der [Yammer ](https://www.yammer.com/AskIPTeam)-Website von Azure Information Protection.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Gibt es ein Management Pack oder einen ähnlichen Überwachungsmechanismus für den RMS-Connector?

Obwohl der Rights Management-Connector Informationen, Warnungen und Fehlermeldungen im Ereignisprotokoll protokolliert, gibt es keine Management Pack, die die Überwachung für diese Ereignisse einschließt. Die Liste der Ereignisse und ihrer Beschreibungen mit weiteren Informationen, die Ihnen helfen, Korrekturmaßnahmen zu ergreifen, ist jedoch unter [Überwachen des Azure Rights Management-Connectors](monitor-rms-connector.md) dokumentiert.

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Wie erstelle ich eine neue benutzerdefinierte Vorlage im Azure-Portal?

Benutzerdefinierte Vorlagen wurden in das Azure-Portal verschoben, wo Sie sie weiterhin als Vorlagen verwalten oder in Bezeichnungen konvertieren können. Um eine neue Vorlage zu erstellen, erstellen Sie eine neue Bezeichnung und konfigurieren die Datenschutzeinstellungen für Azure RMS. Im Hintergrund wird eine neue Vorlage erstellt, auf die dann Dienste und Anwendungen zugreifen können, die in Rights Management-Vorlagen integriert sind.

Weitere Informationen zu Vorlagen im Azure-Portal finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>Ich habe ein Dokument geschützt und möchte nun die Nutzungsrechte ändern oder Benutzer hinzufügen. Muss ich das Dokument erneut schützen?

Wenn das Dokument mit einer Bezeichnung oder einer Vorlage geschützt wurde, besteht keine Notwendigkeit, das Dokument erneut zu schützen. Ändern Sie die Bezeichnung oder Vorlage, indem Sie Ihre Änderungen an den Nutzungsrechten vornehmen oder neue Gruppen (oder Benutzer) hinzufügen und diese Änderungen dann speichern:

- Wenn ein Benutzer nicht auf das Dokument zugegriffen hat, bevor Sie die Änderungen vorgenommen haben, werden die Änderungen wirksam, sobald der Benutzer das Dokument öffnet.

- Wenn ein Benutzer bereits auf das Dokument zugegriffen hat, werden diese Änderungen wirksam, wenn seine [Nutzungslizenz](configure-usage-rights.md#rights-management-use-license) abläuft. Schützen Sie das Dokument nur dann erneut, wenn Sie nicht warten können, bis die Nutzungslizenz abgelaufen ist. Durch das erneute Schützen wird eine neue Version des Dokuments und damit eine neue Nutzungslizenz für den Benutzer erstellt.

Wenn Sie bereits eine Gruppe für die erforderlichen Berechtigungen konfiguriert haben, können Sie alternativ die Gruppenzugehörigkeit ändern, um Benutzer ein- oder auszuschließen, und es ist nicht erforderlich, die Bezeichnung oder die Vorlage zu ändern. Es kann eine kleine Verzögerung bis zum Inkrafttreten der Änderungen geben, da die Gruppenmitgliedschaft durch den Azure Rights Management Service [zwischengespeichert](prepare.md#group-membership-caching-by-azure-information-protection) wird.

Wenn das Dokument mit benutzerdefinierten Berechtigungen geschützt wurde, können Sie die Berechtigungen für das vorhandene Dokument nicht ändern. Sie müssen das Dokument erneut schützen und alle Benutzer und alle Nutzungsrechte angeben, die für diese neue Version des Dokuments erforderlich sind. Um ein geschütztes Dokument erneut zu schützen, müssen Sie über das Nutzungsrecht „Vollzugriff“ verfügen.

Tipp: Verwenden Sie das PowerShell-Cmdlet [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus), um zu überprüfen, ob ein Dokument durch eine Vorlage oder durch die Verwendung benutzerdefinierter Berechtigungen geschützt wurde. Es wird immer die Vorlagenbeschreibung **Eingeschränkter Zugriff** für benutzerdefinierte Berechtigungen mit einer eindeutigen Vorlagen-ID angezeigt, die nicht angezeigt wird, wenn Sie [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate) ausführen.

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Ich verwende eine Hybridbereitstellung von Exchange mit einigen Benutzern unter Exchange Online und anderen unter Exchange Server. Wird dies von Azure RMS unterstützt?
Ja, und das Gute ist, dass Benutzer für zwei Exchange-Bereitstellungen E-Mails und Anlagen nahtlos schützen sowie geschützte E-Mails und Anlagen nutzen können. Aktivieren Sie für diese Konfiguration [Azure RMS](activate-service.md) und [IRM für Exchange Online](/microsoft-365/enterprise/activate-rms-in-microsoft-365), und stellen Sie dann den [RMS-Connector](deploy-rms-connector.md) für Exchange Server bereit, und konfigurieren Sie ihn.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azure-rms"></a>Wenn ich diesen Schutz für meine Produktionsumgebung verwende, ist mein Unternehmen dann an die Lösung gebunden oder riskiert es, den Zugriff auf Inhalte zu verlieren, die wir mit Azure RMS geschützt haben?
Nein, Sie behalten immer die Kontrolle über Ihre Daten und können weiterhin darauf zugreifen, auch wenn Sie sich entscheiden, Azure Rights Management Service nicht mehr zu nutzen. Weitere Informationen finden Sie unter Außerbetriebsetzen [und Deaktivieren von Azure-Rights Management](decommission-deactivate.md).

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Kann ich steuern, welche Benutzer Azure RMS verwenden können, um Inhalte zu schützen?
Ja, Azure Rights Management Service verfügt für dieses Szenario über Onboarding-Steuerelemente für Benutzer. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) im Artikel [Aktivieren des Schutz dienstanweises in Azure Information Protection](activate-service.md) .

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Kann ich verhindern, dass Benutzer geschützte Dokumente für bestimmte Organisationen freigeben?
Einer der größten Vorteile der Verwendung von Azure Rights Management Service für den Datenschutz besteht darin, dass die Zusammenarbeit zwischen Unternehmen unterstützt wird, ohne dass Sie explizite Vertrauensstellungen für jede Partnerorganisation konfigurieren müssen, da Azure AD die Authentifizierung für Sie übernimmt.

Es gibt keine Verwaltungsoption, die Benutzer daran hindert, Dokumente sicher mit bestimmten Organisationen auszutauschen. Beispielsweise möchten Sie eine Organisation blockieren, der Sie nicht vertrauen oder die ein konkurrierendes Unternehmen hat. Das Senden geschützter Dokumente an Benutzer in diesen Organisationen durch den Azure Rights Management-Dienst zu verhindern, wäre nicht sinnvoll, da die Benutzer Ihre Dokumente dann ungeschützt freigeben würden. Dies ist wahrscheinlich das letzte, was Sie in diesem Szenario tun möchten. Beispielsweise könnten Sie nicht erkennen, wer vertrauliche Unternehmensdokumente für welche Benutzer in diesen Organisationen freigibt, was Sie tun können, wenn das Dokument (oder die e-Mail) durch den Azure Rights Management-Dienst geschützt wird.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Wenn ich ein geschütztes Dokument mit jemandem außerhalb meines Unternehmens teile, wie wird dieser Benutzer authentifiziert?

Standardmäßig verwendet Azure Rights Management Service ein Azure Active Directory-Konto und eine zugehörige E-Mail-Adresse für die Benutzerauthentifizierung, wodurch die Zusammenarbeit zwischen Unternehmen für Administratoren nahtlos wird. Wenn die andere Organisation Azure-Dienste verwendet, haben Benutzer bereits Konten in Azure Active Directory, selbst wenn diese Konten lokal erstellt und verwaltet und dann mit Azure synchronisiert werden. Wenn die Organisation über Microsoft 365 verfügt, verwendet dieser Dienst im Unternehmen Azure Active Directory auch für die Benutzerkonten. Wenn die Organisation des Benutzers keine verwalteten Konten in Azure hat, können sich Benutzer für [RMS for Individuals](./rms-for-individuals.md)registrieren. Dadurch werden ein nicht verwalteter Azure-Mandant und ein Verzeichnis für die Organisation mit einem Konto für den Benutzer erstellt, sodass dieser Benutzer (und nachfolgende Benutzer) für den Azure Rights Management-Dienst authentifiziert werden kann.

Die Authentifizierungsmethode für diese Konten kann unterschiedlich sein, je nachdem, wie der Administrator in der anderen Organisation die Azure Active Directory-Konten konfiguriert hat. Beispielsweise können Kennwörter, die für diese Konten erstellt wurden, Verbund oder Kennwörter verwendet werden, die in Active Directory Domain Services erstellt und dann mit Azure Active Directory synchronisiert wurden.

Andere Authentifizierungsmethoden:

- Wenn Sie eine E-Mail mit einer Office-Dokumentanlage an einen Benutzer schützen, der kein Konto in Azure AD besitzt, ändert sich die Authentifizierungsmethode. Der Azure Rights Management Service bildet einen Verbund mit einigen beliebten sozialen Netzwerken als Identitätsanbieter, z.B. mit Google Mail. Wenn der E-Mail-Anbieter des Benutzers unterstützt wird, kann sich der Benutzer bei diesem Dienst anmelden, und sein E-Mail-Anbieter ist für die Authentifizierung verantwortlich. Wenn der E-Mail-Anbieter des Benutzers nicht unterstützt wird (oder als Präferenz), kann der Benutzer einen einmaligen Passcode beantragen, der ihn authentifiziert und die E-Mail mit dem geschützten Dokument in einem Webbrowser anzeigt.

- Azure Information Protection kann Microsoft-Konten für unterstützte Anwendungen verwenden. Derzeit können nicht alle Anwendungen geschützten Inhalt öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Kann ich externe Benutzer (Personen außerhalb meiner Firma) benutzerdefinierten Vorlagen hinzufügen?

Ja. Mit den [Schutzeinstellungen](configure-policy-protection.md), die Sie im Azure-Portal konfigurieren können, können Sie für Benutzer und Gruppen außerhalb Ihrer Organisation und sogar für alle Benutzer in einer anderen Organisation Berechtigungen hinzufügen. Das ausführliche Beispiel [Secure document collaboration by using Azure Information Protection (Sichere Dokumentenzusammenarbeit durch Azure Information Protection)](secure-collaboration-documents.md) ist womöglich nützlich für Sie. 

Beachten Sie Folgendes: Wenn Sie Azure Information Protection-Bezeichnungen verwenden, müssen Sie Ihre benutzerdefinierte Vorlage zunächst in eine Bezeichnung konvertieren, bevor Sie diese Schutzeinstellungen im Azure-Portal konfigurieren können. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md).

Alternativ können Sie mithilfe von PowerShell externe Benutzer benutzerdefinierten Vorlagen (und Bezeichnungen) hinzufügen. Diese Konfiguration erfordert, dass Sie ein Rechtedefinitionsobjekt verwenden, mit dem Sie Ihre Vorlage aktualisieren:

1. Geben Sie die externen e-Mail-Adressen und ihre Rechte in einem Rechte Definitions Objekt an, indem Sie das Cmdlet [New-aipservicerighundefinition](/powershell/module/aipservice/new-aipservicerightsdefinition) verwenden, um eine Variable zu erstellen.

2. Stellen Sie diese Variable mit dem Cmdlet " [Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty) " für den rightiondefinition-Parameter bereit.

    Wenn Sie Benutzer einer vorhandenen Vorlage hinzufügen, müssen Sie zusätzlich zu den neuen Benutzern Rechtedefinitionsobjekte für die vorhandenen Benutzer in den Vorlagen definieren. Für dieses Szenario finden Sie möglicherweise **Beispiel 3: Hinzufügen neuer Benutzer und Rechte zu einer benutzerdefinierten Vorlage** aus dem Abschnitt [Beispiele](/powershell/module/aipservice/set-aipservicetemplateproperty#examples) für das Cmdlet hilfreich.

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Welche Art von Gruppen kann ich mit Azure RMS verwenden?
In den meisten Szenarien können Sie alle Gruppentypen in Azure AD verwenden, die über eine E-Mail-Adresse verfügen. Diese Faustregel gilt immer dann, wenn Sie Nutzungsrechte zuweisen, aber einige Ausnahmen für die Verwaltung von Azure Rights Management Service bestehen. Weitere Informationen finden Sie unter [Azure Information Protection-Anforderungen für Gruppenkonten](prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Wie sende ich eine geschützte E-Mail an ein Google Mail- oder Hotmail-Konto?

Wenn Sie Exchange Online und Azure Rights Management Service nutzen, senden Sie die E-Mail einfach als geschützte Nachricht an den Benutzer. Sie können beispielsweise die neue Schaltfläche **Schützen** in der Befehlsleiste in Outlook im Web auswählen, die Outlook-Schaltfläche **Nicht weiterleiten** oder die Menüoption verwenden. Oder Sie können eine Azure Information Protection-Bezeichnung auswählen, die automatisch „Nicht weiterleiten“ für Sie anwendet und die E-Mail klassifiziert.

Dem Empfänger wird eine Option angezeigt, mit der dieser sich bei seinem Gmail-, Yahoo- oder Microsoft-Konto anmelden und die geschützte E-Mail anschließend lesen kann. Alternativ können sie die Option für einen einmaligen Passcode auswählen, um die E-Mail in einem Browser zu lesen.

Damit dieses Szenario unterstützt wird, muss Exchange Online für Azure Rights Management Service und die neuen Funktionen in der Office 365-Nachrichtenverschlüsselung aktiviert sein. Weitere Informationen zu dieser Konfiguration finden Sie unter [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration).

Weitere Informationen zu den neuen Funktionen, zu denen auch die Unterstützung aller E-Mail-Konten auf allen Geräten gehört, finden Sie im folgenden Blogbeitrag: [Ankündigung neuer Funktionen, die in der Office 365-Nachrichtenverschlüsselung verfügbar sind](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Welche Geräte und Dateitypen werden von Azure RMS unterstützt?

Eine Liste der Geräte, die Azure Rights Management Service unterstützen, finden Sie unter [Clientgeräte, die Azure Rights Management-Datenschutz unterstützen](./requirements.md#client-devices). Da derzeit nicht alle unterstützten Geräte alle Rights Management Funktionen unterstützen, achten Sie auch darauf, die Tabellen auf [RMS-Anwendungen](./requirements-applications.md)zu überprüfen.

Azure Rights Management Service kann alle Dateitypen unterstützen. Für Text-, Bild-, Microsoft Office-Dateien (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen stellt Azure Rights Management nativen Schutz bereit, der sowohl Verschlüsselung als auch Durchsetzung von Rechten (Berechtigungen) umfasst. Für alle anderen Anwendungen und Dateitypen bietet der generische Schutz Dateikapselung und Authentifizierung, um zu überprüfen, ob ein Benutzer berechtigt ist, die Datei zu öffnen.

Eine Liste der Dateinamenerweiterungen, die nativ von Azure Rights Management unterstützt werden, finden Sie unter [Vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md). Nicht aufgeführte Dateinamenerweiterungen werden unterstützt, indem der Azure Information Protection-Client verwendet wird, der automatisch generischen Schutz auf diese Dateien anwendet.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Wenn ich ein durch RMS geschütztes Office-Dokument öffne, wird die zugehörige temporäre Datei ebenfalls durch RMS geschützt?
Nein. In diesem Szenario enthält die zugehörige temporäre Datei keine Daten aus dem Originaldokument, sondern nur das, was der Benutzer eingibt, während die Datei geöffnet ist. Im Gegensatz zur ursprünglichen Datei ist die temporäre Datei offensichtlich nicht für die Freigabe vorgesehen und würde auf dem Gerät verbleiben, geschützt durch lokale Sicherheitsmechanismen wie BitLocker und EFS.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Eine Funktion, die ich Suche, scheint nicht mit SharePoint-geschützten Bibliotheken zu funktionieren – ist die Unterstützung für meine Funktion geplant?
Derzeit unterstützt Microsoft SharePoint RMS-geschützte Dokumente mithilfe von unm-geschützten Bibliotheken, die Rights Management Vorlagen, die dokumentenverfolgung und einige andere Funktionen nicht unterstützen. Weitere Informationen finden Sie im Abschnitt [SharePoint in Microsoft 365 und SharePoint Server](./office-apps-services-support.md#sharepoint-in-microsoft-365-and-sharepoint-server) im Artikel [Office-Anwendungen und-Dienste](./office-apps-services-support.md) .

Wenn Sie an einer bestimmten Funktion interessiert sind, die noch nicht unterstützt wird, sollten Sie die Ankündigungen im [Blog zu Enterprise Mobility + Security](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-rights-management-services) im Auge behalten.

## <a name="how-do-i-configure-one-drive-in-sharepoint-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Gewusst wie Konfigurieren eines Laufwerks in SharePoint, sodass Benutzer Ihre Dateien sicher für Personen innerhalb und außerhalb des Unternehmens freigeben können?
Standardmäßig wird dies als Microsoft 365 Administrator nicht konfiguriert. Benutzer.

Ebenso wie ein SharePoint-Website Administrator für eine SharePoint-Bibliothek, deren Besitzer er ist, "unm" aktiviert und konfiguriert, ist onedrive für Benutzer so konzipiert, dass Sie für Ihre eigene onedrive-Bibliothek "IRiM" aktivieren und konfigurieren können. Mit PowerShell können Sie diese Aufgabe jedoch für sie übernehmen. Anweisungen hierzu finden Sie unter [SharePoint in Microsoft 365 und onedrive: unm-Konfiguration](configure-office365.md#sharepoint-in-microsoft-365-and-onedrive-irm-configuration).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Kennen Sie Tipps und Tricks für eine erfolgreiche Bereitstellung?

Nachdem wir viele Bereitstellungen betreut und unseren Kunden, Partnern, Beratern und Supportengineers zugehört haben, ist einer der besten Tipps, die wir aus Erfahrung weitergeben können: **Entwerfen und implementieren Sie einfache Richtlinien**.

Da Azure Information Protection die sichere Freigabe von Daten für jedermann unterstützt, können Sie es sich leisten, ehrgeizig zu sein, wenn es um den Schutz Ihrer Daten geht. Seien Sie jedoch vorsichtig, wenn Sie Einschränkungen der Rechteverwendung konfigurieren. Für viele Unternehmen ist die größte Auswirkung auf das Geschäft die Verhinderung von Datendiebstahl durch die Beschränkung des Zugriffs auf Personen im Unternehmen. Natürlich können Sie viel differenziertere erhalten, als wenn Sie – Personen am drucken, bearbeiten usw. hindern müssen. Behalten Sie jedoch die präziseteren Einschränkungen als Ausnahme für Dokumente bei, die wirklich eine hohe Sicherheit benötigen, und implementieren Sie diese restriktiveren Nutzungsrechte nicht am ersten Tag, sondern planen Sie einen mehrstufigen Ansatz.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Wie erhalten wir erneut Zugriff auf Dateien, die von einem Mitarbeiter geschützt wurden, der das Unternehmen inzwischen verlassen hat?
Verwenden Sie das [Feature Administrator (super user)](configure-super-users.md), das autorisierten Benutzern das Nutzungsrecht „Vollzugriff“ für alle Dokumente und E-Mails gewährt, die durch Ihren Mandanten geschützt sind. Administratoren können diesen geschützten Inhalt immer lesen und bei Bedarf den Schutz aufheben oder den Inhalt erneut für andere Benutzer schützen. Mit diesem Feature können autorisierte Dienste bei Bedarf Dateien indizieren und untersuchen.

Wenn Ihre Inhalte in SharePoint oder onedrive gespeichert sind, können Administratoren das [Unlock-sensitivitylabelverschlüsseltedfile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedfile) -Cmdlet ausführen, um die Vertraulichkeits Bezeichnung und die Verschlüsselung zu entfernen. Weitere Informationen finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels-sharepoint-onedrive-files#remove-encryption-for-a-labeled-document).

## <a name="can-rights-management-prevent-screen-captures"></a>Kann Rights Management Bildschirmaufnahmen verhindern?
Wenn Sie das [Nutzungsrecht](configure-usage-rights.md)" **Kopieren** " nicht gewähren, können Rights Management Bildschirmaufnahmen von vielen der häufig verwendeten Bildschirm Erfassungs Tools auf Windows-Plattformen (Windows 7, Windows 8.1, Windows 10, Windows 10 Mobile) und Android verhindern. iOS- und Mac-Geräte erlauben Apps jedoch das Verhindern von Bildschirmaufnahmen nicht. Ferner können Browser auf Geräten, gleich welchen, keine Bildschirmaufnahmen verhindern. Die Browser Verwendung umfasst Outlook im Web und Office für das Web.

Das Verhindern von Bildschirmaufnahmen kann helfen, eine versehentliche oder fahrlässige Offenlegung vertraulicher oder sensibler Informationen zu vermeiden. Es gibt jedoch viele Möglichkeiten, wie ein Benutzerdaten freigeben kann, die auf einem Bildschirm angezeigt werden, und ein Screenshot ist nur eine Methode. Beispielsweise kann ein Benutzer, der beabsichtigt, angezeigte Informationen zu teilen, mit seiner Smartphonekamera ein Foto davon machen, die Daten erneut eingeben oder sie einfach mündlich an eine andere Person weitergeben.

Wie diese Beispiele zeigen, kann Technologie allein nicht immer verhindern, dass Benutzer Daten unerlaubt gemeinsam nutzen, selbst wenn alle Plattformen und die gesamte Software die Rights Management-APIs zur Blockierung von Bildschirmaufnahmen unterstützten. Rights Management kann Ihnen dabei helfen, Ihre wichtigen Daten durch die Verwendung von Autorisierung und Nutzungsrichtlinien zu schützen, aber diese Lösung für die Verwaltung von Unternehmensrechten sollte zusammen mit anderen Kontrollmechanismen verwendet werden. Implementieren Sie beispielsweise physische Sicherheit, überprüfen und überwachen Sie sorgfältig Personen, die autorisierten Zugriff auf die Daten Ihres Unternehmens besitzen, und investieren Sie in die Schulung der Benutzer, damit Benutzer verstehen, welche Daten nicht geteilt werden sollten.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Worin besteht der Unterschied zwischen einem Benutzer, der eine E-Mail mit „Nicht weiterleiten“ schützt, und einer Vorlage, die das Recht „Weiterleiten“ nicht enthält?

Trotz des Namens und des Erscheinungsbilds ist **Nicht weiterleiten** nicht das Gegenteil des Rechts „Weiterleiten“ oder einer Vorlage. Es handelt sich eigentlich um einen Satz von Rechten, die das Einschränken von kopieren, Drucken und Speichern der e-Mail außerhalb des Postfachs, zusätzlich zum Einschränken der Weiterleitung von e-Mails, beinhalten. Die Rechte werden auf Benutzer über die ausgewählten Empfänger dynamisch angewendet und nicht statisch vom Administrator zugewiesen. Weitere Informationen finden Sie im Abschnitt "nicht [weiterleiten" für e-Mails](configure-usage-rights.md#do-not-forward-option-for-emails) unter [Konfigurieren von Nutzungsrechten für Azure Information Protection](configure-usage-rights.md).