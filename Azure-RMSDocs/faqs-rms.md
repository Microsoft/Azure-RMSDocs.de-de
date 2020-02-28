---
title: Häufig gestellte Fragen zu Azure RMS – AIP
description: Hier finden Sie einige häufig gestellte Fragen zum Azure Rights Management-Dienst (Azure RMS) von Azure Information Protection für den Schutz von Daten.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 1/06/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 90df11c5-355c-4ae6-a762-351b05d0fbed
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 184d1b69c7256d85e162edc5a2993b1bff066500
ms.sourcegitcommit: 275d31ef762c702b6c63025cbba0a45ca9528ce5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/27/2020
ms.locfileid: "77778635"
---
# <a name="frequently-asked-questions-about-data-protection-in-azure-information-protection"></a>Häufig gestellte Fragen zum Schutz von Daten in Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Haben Sie eine Frage zum Azure Rights Management-Dienst von Azure Information Protection für den Schutz von Daten? Vielleicht finden Sie hier eine Antwort darauf.

## <a name="do-files-have-to-be-in-the-cloud-to-be-protected-by-azure-rights-management"></a>Müssen sich Dateien in der Cloud befinden, um von Azure Rights Management geschützt werden zu können?
Nein, das ist ein weit verbreitetes Missverständnis. Für den Prozess zum Schutz von Daten des Azure Rights Management-Diensts (und von Microsoft) gilt, dass er Ihre Daten weder sieht noch speichert. Informationen, die Sie schützen, werden niemals an Azure gesendet oder dort gespeichert – es sei denn, dass Sie diese explizit in Azure speichern oder einen anderen Cloud-Dienst verwenden, der sie in Azure speichert.

Weitere Informationen finden Sie unter [wie funktioniert Azure RMS? Im](./how-does-it-work.md) Hintergrund wird erläutert, wie eine geheime Cola-Formel, die lokal erstellt und gespeichert wird, durch den Azure-Rights Management Service geschützt wird, aber lokal bleibt.

## <a name="whats-the-difference-between-azure-rights-management-encryption-and-encryption-in-other-microsoft-cloud-services"></a>Was ist der Unterschied zwischen Azure Rights Management-Verschlüsselung und Verschlüsselung in andere Microsoft-Clouddiensten?

Microsoft stellt mehrere Verschlüsselungstechnologien zum Schutz Ihrer Daten in verschiedenen und häufig sich ergänzenden Szenarien zur Verfügung. Während Office 365 z. B. Verschlüsselung von in Office 365 gespeicherten ruhenden Daten bietet, verschlüsselt und schützt der Azure Rights Management-Dienst von Azure Information Protection Ihre Daten unabhängig von Speicherort oder Übertragungsmethode.

Diese Verschlüsselungstechnologien ergänzen sich, und zur Verwendung müssen Sie sie unabhängig voneinander aktivieren und konfigurieren. Dabei besteht möglicherweise die Option, einen eigenen Schlüssel für die Verschlüsselung bereitzustellen, ein Szenario, das auch als „BYOK“ (Bring-Your-Own-Key) bezeichnet wird. Das Aktivieren von BYOK für eine dieser Technologien hat keinen Einfluss auf andere. Sie können BYOK z. B. für Azure Information Protection verwenden und für andere Verschlüsselungstechniken nicht verwenden (und umgekehrt). Die von den unterschiedlichen Technologien verwendeten Schlüssel können gleich oder verschieden sein, je nachdem, wie Sie die Verschlüsselungsoptionen für die einzelnen Dienste konfigurieren.

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Was ist der Unterschied zwischen BYOK und HYOK, und wann sollte ich welche Option verwenden?

**Bring Your Own Key** (BYOK) bedeutet im Kontext von Azure Information Protection, dass Sie Ihren eigenen Schlüssel für Azure Rights Management-Schutz lokal erzeugen. Sie übertragen diesen Schlüssel anschließend auf ein Hardwaresicherheitsmodul (HSM) in Azure Key Vault, bleiben nach wie vor Besitzer des Schlüssels und verwalten ihn weiterhin. Wenn Sie diesen Schritt nicht durchführen, würde Azure Rights Management Protection einen Schlüssel verwenden, der automatisch erstellt und für Sie in Azure verwaltet wird. Diese Standardkonfiguration wird als „von Microsoft-verwaltet“ bezeichnet, im Gegensatz zu „Kundenverwaltet“ (BYOK-Option).

Weitere Informationen zu BYOK und dazu, ob Sie diese Schlüsseltopologie für Ihre Organisation auswählen sollten, finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

**Hold Your Own Key** (HYOK) ist im Kontext von Azure Information Protection für bestimmte Organisationen bestimmt, die über eine Teilmenge von Dokumenten oder E-Mails verfügen, die nicht durch einen in der Cloud gespeicherten Schlüssel geschützt werden können. Für diese Unternehmen gilt diese Einschränkung auch dann, wenn sie den Schlüssel mit BYOK erstellt haben und verwalten. Die Einschränkung gilt häufig aufgrund von gesetzlichen oder Compliancegründen. Die HYOK-Konfiguration sollte nur auf „streng geheime“ Informationen angewendet werden, die niemals außerhalb der Organisation freigegeben und nur im internen Netzwerk verwendet werden und auf die nicht über mobile Geräte zugegriffen werden muss.

Für diese Ausnahmen (in der Regel weniger als 10 % des gesamten Inhalts, der geschützt werden muss), können Organisationen den Schlüssel mit einer lokalen Lösung (Active Directory Rights Management Services) erstellen und lokal speichern. Mit dieser Lösung erhalten Computer die Azure Information Protection-Richtlinie aus der Cloud, aber dieser spezielle Inhalt kann mit dem lokalen Schlüssel geschützt werden.

Weitere Informationen zu HYOK und zum Verständnis der dafür geltenden Einschränkungen sowie Hinweise dazu, wann Sie HYOK verwenden sollten, finden Sie unter [Anforderungen an Hold Your Own Key (HYOK) und Einschränkungen für AD RMS-Schutz](configure-adrms-restrictions.md).

## <a name="can-i-now-use-byok-with-exchange-online"></a>Kann ich ab jetzt BYOK mit Exchange Online verwenden?

Ja, Sie können von nun an BYOK mit Exchange Online verwenden, wenn Sie den Anweisungen unter [Set up new Office 365 Message Encryption capabilities built on top of Azure Information Protection (Einrichten von neuen, auf Azure Information Protection basierenden Funktionen in der Office 365-Nachrichtenverschlüsselung)](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e) folgen. Hierdurch werden die neuen Funktionen in Exchange Online aktiviert, mit denen sowohl BYOK für Azure Information Protection als auch die neue Office 365-Nachrichtenverschlüsselung unterstützt werden.

Weitere Informationen zu dieser Änderung finden Sie in der Blog-Ankündigung [Office 365 Message Encryption with the new capabilities (Office 365-Nachrichtenverschlüsselung mit neuen Funktionen)](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="where-can-i-find-information-about-third-party-solutions-that-integrate-with-azure-rms"></a>Wo finde ich Informationen zu Lösungen von Drittanbietern, die in Azure RMS integrierbar sind?

Viele Softwarehersteller verfügen bereits über Lösungen oder sind dabei, Lösungen zu implementieren, die in Azure Rights Management integrierbar sind – und die Liste erweitert sich schnell. Werfen Sie für weitere Informationen einen Blick auf die Liste der [RMS-aktivierten Lösungen](requirements-applications.md#rms-enlightened-solutions), und lesen Sie die neuesten Mitteilungen von [MicrosoftMobility@MSFTMobility](https://twitter.com/MSFTMobility) auf Twitter. Ziehen Sie zudem das [Entwicklerhandbuch](./develop/developers-guide.md) zu Rate, und posten Sie Fragen zur Integration auf der [Yammer-Website](https://www.yammer.com/AskIPTeam) von Azure Information Protection.

## <a name="is-there-a-management-pack-or-similar-monitoring-mechanism-for-the-rms-connector"></a>Gibt es ein Management Pack oder einen ähnlichen Überwachungsmechanismus für den RMS-Connector?

Obwohl der Rights Management-Connector Informationen, Warn- und Fehlermeldungen im Ereignisprotokoll protokolliert, gibt es kein Management Pack, das die Überwachung für diese Ereignisse enthält. Eine Liste der Ereignisse und der dazugehörigen Beschreibungen mit Informationen, die Sie bei Ihren Entscheidungen hinsichtlich Korrekturmaßnahmen unterstützen, finden Sie jedoch unter [Überwachen des Azure Rights Management-Connectors](monitor-rms-connector.md).

## <a name="how-do-i-create-a-new-custom-template-in-the-azure-portal"></a>Wie erstelle ich eine neue benutzerdefinierte Vorlage im Azure-Portal?

Benutzerdefinierte Vorlagen werden zum Azure-Portal migriert, in dem Sie diese weiterhin als Vorlagen verwalten oder in Bezeichnungen konvertieren können. Um eine neue Vorlage zu erstellen, erstellen Sie eine neue Bezeichnung und konfigurieren Sie die Datenschutzeinstellungen für Azure RMS. Im Hintergrund wird hierdurch eine neue Vorlage erstellt, auf die dann über Dienste und Anwendungen, die in Rights Management-Vorlagen integriert werden, zugegriffen werden kann.

Weitere Informationen zu Vorlagen im Azure-Portal finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](configure-policy-templates.md).

## <a name="ive-protected-a-document-and-now-want-to-change-the-usage-rights-or-add-usersdo-i-need-to-reprotect-the-document"></a>Ich habe ein Dokument geschützt und möchte nun die Nutzungsrechte ändern oder Benutzer hinzufügen – muss ich das Dokument erneut schützen?

Wenn das Dokument durch eine Bezeichnung oder eine Vorlage geschützt war, muss es nicht erneut geschützt werden. Ändern Sie die Bezeichnung oder Vorlage, indem Sie Ihre Änderungen an den Nutzungsrechten vornehmen oder neue Gruppen (oder Benutzer) hinzufügen und diese Änderungen dann speichern:

- Wenn ein Benutzer noch nicht auf dieses Dokument zugegriffen hat, bevor Sie die Änderungen vorgenommen haben, werden die Änderungen wirksam, sobald der Benutzer das Dokument öffnet.

- Wenn ein Benutzer bereits auf das Dokument zugegriffen hat, werden diese Änderungen wirksam, wenn dessen [Nutzungslizenz](configure-usage-rights.md#rights-management-use-license) abläuft. Schützen Sie das Dokument nur erneut, wenn Sie nicht darauf warten können, dass die Nutzungslizenz abläuft. Das erneute Schützen erstellt im Grunde eine neue Version des Dokuments und somit eine neue Nutzungslizenz für den Benutzer.

Wenn Sie bereits eine Gruppe für die erforderlichen Berechtigungen konfiguriert haben, können Sie alternativ die Gruppenmitgliedschaft ändern, um Benutzer ein- oder auszuschließen, damit die Bezeichnung oder Vorlage nicht geändert werden muss. Die Änderungen werden möglicherweise mit einer kurzen Verzögerung wirksam, da die Gruppenmitgliedschaft vom Azure Rights Management-Dienst [zwischengespeichert](prepare.md#group-membership-caching-by-azure-information-protection) wird.

Wenn das Dokument mithilfe von benutzerdefinierten Berechtigungen geschützt wurde, können Sie die Berechtigungen für das vorhandene Dokument nicht ändern. Sie müssen das Dokument erneut schützen und alle Benutzer und Nutzungsrechte angeben, die für die neue Version des Dokument erforderlich sind. Sie müssen über das Nutzungsrecht „Vollzugriff“ verfügen, um ein geschütztes Dokument erneut zu schützen.

Tipp: Um zu sehen, ob ein Dokument durch eine Vorlage oder eine benutzerdefinierte Berechtigung geschützt war, können Sie das [Get-AIPFileStatus](/powershell/module/azureinformationprotection/get-aipfilestatus) PowerShell-Cmdlet verwenden. Sie sehen immer eine Beschreibung der Vorlage der **Zugriffsbeschränkung** für benutzerdefinierte Berechtigungen mit einer einzigartigen Vorlagen-ID, der nicht angezeigt wird wenn Sie [Get-RMSTemplate](/powershell/module/azureinformationprotection/get-rmstemplate) ausführen.

## <a name="i-have-a-hybrid-deployment-of-exchange-with-some-users-on-exchange-online-and-others-on-exchange-serveris-this-supported-by-azure-rms"></a>Ich habe eine Hybridbereitstellung von Exchange mit einigen Benutzern auf Exchange Online und anderen auf Exchange Server – wird dies von Azure RMS unterstützt?
Ja, und das Gute ist, dass Benutzer für zwei Exchange-Bereitstellungen E-Mails und Anlagen nahtlos schützen sowie geschützte E-Mails und Anlagen nutzen können. Führen Sie für diese Konfiguration folgende Schritte aus: [Aktivieren von Azure RMS](activate-service.md), [Aktivieren von IRM für Exchange Online](https://technet.microsoft.com/library/dn151475%28v=exchg.150%29.aspx) und [Bereitstellen und Konfigurieren des RMS-Connectors](deploy-rms-connector.md) für Exchange Server.

## <a name="if-i-use-this-protection-for-my-production-environment-is-my-company-then-locked-into-the-solution-or-risk-losing-access-to-content-that-we-protected-with-azurerms"></a>Wenn ich diesen Schutz in meiner Produktionsumgebung verwende, ist mein Unternehmen dann an die Lösung gebunden und läuft andernfalls Gefahr, den Zugriff auf Inhalte zu verlieren, die wir mit Azure RMS geschützt haben?
Nein, Sie behalten immer die Kontrolle über Ihre Daten und können weiterhin darauf zugreifen, selbst wenn Sie sich entscheiden, den Azure Rights Management-Dienst nicht mehr zu verwenden. Weitere Informationen finden Sie unter [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md).

## <a name="can-i-control-which-of-my-users-can-use-azure-rms-to-protect-content"></a>Kann ich steuern, welche Benutzer Azure RMS verwenden können, um Inhalte zu schützen?
Ja, der Azure Rights Management-Dienst verfügt für dieses Szenario über Onboarding-Steuerelemente. Weitere Informationen finden Sie im Abschnitt [Konfigurieren von Onboarding-Steuerelementen für eine stufenweise Bereitstellung](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) im Artikel [Aktivieren des Schutz dienstanweises in Azure Information Protection](activate-service.md) .

## <a name="can-i-prevent-users-from-sharing-protected-documents-with-specific-organizations"></a>Kann ich verhindern, dass Benutzer geschützte Dokumente für bestimmte Organisationen freigeben?
Einer der größten Vorteile der Verwendung des Azure Rights Management-Diensts für den Schutz von Daten besteht darin, dass er B2B-Zusammenarbeit unterstützt, ohne dass Sie explizite Vertrauensstellungen für jede Partnerorganisation konfigurieren müssen, denn Azure AD übernimmt die Authentifizierung für Sie.

Es gibt keine Verwaltungsoption, mit der verhindert werden kann, dass Benutzer Dokumente geschützt für bestimmte Organisationen freigeben. Angenommen, Sie möchten eine Organisation blockieren, der Sie nicht vertrauen oder die ein konkurrierendes Unternehmen hat. Den Azure Rights Management-Dienst daran zu hindern, geschützte Dokumente an Benutzer in diesen Organisationen zu senden, wäre nicht sinnvoll, da die Benutzer ihre Dokumente dann ungeschützt freigeben würden. Dies ist wahrscheinlich genau das, was in diesem Szenario nicht geschehen soll. Beispielsweise könnten Sie nicht erkennen, wer vertrauliche Unternehmensdokumente für welche Benutzer in dieser Organisation freigibt, dies können Sie jedoch, wenn das Dokument (oder die E-Mail) durch den Azure Rights Management-Dienst geschützt wird.

## <a name="when-i-share-a-protected-document-with-somebody-outside-my-company-how-does-that-user-get-authenticated"></a>Wenn ich ein geschütztes Dokument für eine Person außerhalb meiner Firma freigebe, wie wird dieser Benutzer authentifiziert?

Der Azure Rights Management-Dienst verwendet standardmäßig ein Azure Active Directory-Konto und eine zugeordnete E-Mail-Adresse für die Benutzerauthentifizierung, sodass sich eine nahtlose Business-to-Business-Zusammenarbeit für Administratoren ergibt. Wenn die andere Organisation Azure-Dienste verwendet, haben Benutzer bereits Konten in Azure Active Directory, selbst wenn diese Konten lokal erstellt und verwaltet und dann mit Azure synchronisiert werden. Wird in der Organisation Office 365 verwendet, verwendet dieser Dienst (im Hintergrund) ebenfalls Azure Active Directory für die Benutzerkonten. Wenn die Organisation des Benutzers nicht über verwaltete Konten in Azure verfügt, können sich Benutzer für [RMS for Individuals](./rms-for-individuals.md) registrieren. Dadurch werden ein nicht verwalteter Azure-Mandant und ein Verzeichnis für die Organisation mit einem Konto für den Benutzer erstellt, sodass dieser Benutzer (und weitere Benutzer) dann für den Azure Rights Management-Dienst authentifiziert werden kann.

Die Authentifizierungsmethode für diese Konten kann unterschiedlich sein, je nachdem, wie der Administrator in der anderen Organisation die Azure Active Directory-Konten konfiguriert hat. Beispielsweise können Kennwörter, die für diese Konten erstellt wurden, Verbund oder Kennwörter verwendet werden, die in Active Directory Domain Services erstellt und dann mit Azure Active Directory synchronisiert wurden.

Andere Authentifizierungsmethoden:

- Wenn Sie eine E-Mail mit einer Office-Dokumentanlage an einen Benutzer senden, der über ein Konto in Azure AD verfügt, und diese E-Mail schützen, ändert sich die Authentifizierungsmethode. Für den Azure Rights Management-Dienst ist ein Verbund mit einigen bekannten Identitätsanbietern sozialer Netzwerke wie Gmail vorhanden. Wenn der E-Mail-Anbieter des Benutzers unterstützt wird, kann der Benutzer sich bei diesem Dienst anmelden. Der Anbieter ist in diesem Fall für die Authentifizierung der Benutzer verantwortlich. Wenn der E-Mail-Anbieter des Benutzers nicht unterstützt wird oder der Benutzer eine andere Vorgehensweise bevorzugt, kann Letzterer eine einmalige Kennung anfordern, mit der dieser authentifiziert wird und mit der die E-Mail mit dem geschützten Dokument in einem Webbrowser angezeigt wird.

- Azure Information Protection kann Microsoft-Konten für unterstützte Anwendungen verwenden. Derzeit können nicht alle Anwendungen geschützten Inhalt öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="can-i-add-external-users-people-from-outside-my-company-to-custom-templates"></a>Kann ich externe Benutzer (die nicht zu meinem Unternehmen gehören) zu benutzerdefinierten Vorlagen hinzufügen?

Ja. Über die [Schutzeinstellungen](configure-policy-protection.md), die Sie im Azure-Portal konfigurieren können, können Sie Berechtigungen für Benutzer und Gruppen, die nicht Ihrer Organisation angehören, sowie sogar für sämtliche Benutzer einer anderen Organisation hinzufügen. Das ausführliche Beispiel [Secure document collaboration by using Azure Information Protection (Sichere Dokumentenzusammenarbeit durch Azure Information Protection)](secure-collaboration-documents.md) ist womöglich nützlich für Sie. 

Beachten Sie, dass Sie erst ihre benutzerdefinierte Vorlage in eine Bezeichnung konvertieren müssen, wenn Azure Information Protection-Bezeichnungen vorhanden sind, bevor Sie diese Schutzeinstellungen im Azure-Portal konfigurieren können. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](configure-policy-templates.md).

Stattdessen können Sie mithilfe von PowerShell externe Benutzer für benutzerdefinierte Dokumente (und Bezeichnungen) hinzufügen. Für die Konfiguration müssen Sie ein Rechtedefinitionsobjekt zum Aktualisieren Ihrer Vorlage verwenden:

1. Geben Sie die externen e-Mail-Adressen und ihre Rechte in einem Rechte Definitions Objekt an, indem Sie das Cmdlet [New-aipservicerighundefinition](/powershell/module/aipservice/new-aipservicerightsdefinition) verwenden, um eine Variable zu erstellen.

2. Stellen Sie diese Variable mit dem Cmdlet " [Set-aipservicetemplateproperty](/powershell/module/aipservice/set-aipservicetemplateproperty) " für den rightiondefinition-Parameter bereit.

    Wenn Sie Benutzer zu einer vorhanden Vorlage hinzufügen, müssen Sie die Rechtedefinitionsobjekte zusätzlich zu den neuen Benutzern auch für die in der Vorlage vorhanden Benutzer definieren. Bei diesem Szenario hilft Ihnen möglicherweise **Beispiel 3: Hinzufügen von neuen Benutzern und Rechten zu einer benutzerdefinierten Vorlage** im Abschnitt [Beispiele](/powershell/module/aipservice/set-aipservicetemplateproperty#examples) für das Cmdlet.

## <a name="what-type-of-groups-can-i-use-with-azure-rms"></a>Welche Art von Gruppen kann ich mit Azure RMS verwenden?
Für die meisten Szenarios können Sie alle Gruppentypen in Azure AD verwenden, die über eine E-Mail-Adresse verfügen. Diese Faustregel gilt immer dann, wenn Sie Nutzungsrechte zuweisen, es aber einige Ausnahmen beim Verwalten des Azure Rights Management-Diensts gibt. Weitere Informationen finden Sie unter [Azure Information Protection-Anforderungen für Gruppenkonten](prepare.md#azure-information-protection-requirements-for-group-accounts).

## <a name="how-do-i-send-a-protected-email-to-a-gmail-or-hotmail-account"></a>Wie sende ich eine geschützte E-Mail an ein Gmail- oder Hotmail-Konto?

Wenn Sie Exchange Online und den Azure Rights Management-Dienst verwenden, senden Sie die E-Mail einfach als geschützte Nachricht an den Benutzer. Beispielsweise können Sie die neue Schaltfläche **Schützen** in der Befehlsleiste in Outlook im Web auswählen und die Schaltfläche bzw. Menüoption **Nicht weiterleiten** in Outlook verwenden. Stattdessen können Sie auch eine Azure Information Protection-Bezeichnung auswählen, die automatisch „Nicht weiterleiten“ anwendet und die E-Mail klassifiziert.

Dem Empfänger wird eine Option angezeigt, mit der dieser sich bei seinem Gmail-, Yahoo- oder Microsoft-Konto anmelden und die geschützte E-Mail anschließend lesen kann. Alternativ können Empfänger die Option zur Anforderung einer einmaligen Kennung verwenden, mit der sie die E-Mail in einem Browser lesen können.

Für dieses Szenario muss Exchange Online für den Azure Rights Management-Dienst und für die neuen Funktionen in der Office 365-Nachrichtenverschlüsselung aktiviert sein. Weitere Informationen zu dieser Konfiguration finden Sie unter [Exchange Online: IRM-Konfiguration](configure-office365.md#exchangeonline-irm-configuration).

Weitere Informationen zu den neuen Funktionen, die sämtliche E-Mail-Konten auf allen Geräten unterstützen, finden Sie im Blogbeitrag [Announcing new capabilities available in Office 365 Message Encryption (Ankündigung neuer Funktionen in der Office 365-Nachrichtenverschlüsselung)](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Email-Encryption-and-Rights-Protection/ba-p/110801).

## <a name="what-devices-and-which-file-types-are-supported-by-azure-rms"></a>Welche Geräte und welche Dateitypen werden von Azure RMS unterstützt?
Eine Liste mit Geräten, die den Azure Rights Management-Dienst unterstützen, finden Sie unter [Clientgeräte mit Unterstützung für den Azure Rights Management-Schutz von Daten](./requirements-client-devices.md). Da derzeit nicht alle unterstützten Geräte alle Rights Management-Funktionen unterstützen, sehen Sie sich auch die Tabelle unter [RMS-aktivierte Anwendungen](./requirements-applications.md#rms-enlightened-applications) an.

Der Azure Rights Management-Diensts kann sämtliche Dateitypen unterstützen. Für Text-, Bild-, Microsoft Office- (Word, Excel, PowerPoint), PDF-Dateien und einige andere Anwendungsdateitypen stellt Azure Rights Management nativen Schutz bereit, der Verschlüsselung und die Durchsetzung von Rechten (Berechtigungen) umfasst. Für alle anderen Anwendungen und Dateitypen bietet generischer Schutz Dateiverkapselung und Authentifizierung, damit überprüft wird, ob ein Benutzer zum Öffnen der Datei autorisiert ist.

Eine Liste der Dateierweiterungen, die systemintern von Azure Rights Management unterstützt werden, finden Sie unter [Vom Azure Information Protection-Client unterstützte Dateitypen](./rms-client/client-admin-guide-file-types.md). Nicht aufgeführte Dateierweiterungen werden mithilfe des Azure Information Protection-Clients unterstützt, der automatisch generischen Schutz auf diese Dateien anwendet.

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Wie konfiguriere ich einen Macintosh-Computer für den Schutz und die Nachverfolgung von Dokumenten?

Stellen Sie zuerst anhand des Softwareinstallationslinks unter https://admin.microsoft.com sicher, dass Office für Mac installiert ist. Vollständige Anweisungen finden Sie unter [Herunterladen und Installieren oder Neuinstallieren von Office 365 oder Office 2019 auf einem PC oder Mac](https://support.office.com/en-us/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Öffnen Sie Outlook, und erstellen Sie ein Profil mit Ihrem Geschäfts-, Schul- oder Unikonto bei Office 365. Erstellen Sie dann eine neue Nachricht, und führen Sie folgende Schritte durch, um Office für den Schutz von Dokumenten und E-Mails anhand des Azure Rights Management-Diensts zu konfigurieren:

1. Klicken Sie in der neuen Nachricht auf der Registerkarte **Optionen** auf **Berechtigungen** und anschließend auf **Anmeldeinformationen überprüfen**.

2. Geben Sie nach entsprechender Aufforderung die Details zu Ihrem Geschäfts-, Schul- oder Unikonto bei Office 365 an, und wählen Sie **Anmelden**.

    Daraufhin werden die Azure Rights Management-Vorlagen heruntergeladen. Zudem wird **Anmeldeinformationen überprüfen** nun durch Optionen ersetzt, die **Keine Einschränkungen**, **Nicht weiterleiten** sowie alle Azure Rights Management-Vorlagen umfassen, die für Ihren Mandanten veröffentlicht wurden. Sie können diese neue Nachricht nun abbrechen.

So schützen Sie eine E-Mail-Nachricht oder ein Dokument: Klicken Sie auf der Registerkarte **Optionen** auf **Berechtigungen**, und wählen Sie eine Option oder eine Vorlage zum Schutz Ihrer E-Mail oder Ihres Dokuments aus.

So verfolgen Sie ein Dokument nach, nachdem Sie es geschützt haben: Registrieren Sie auf einem Windows-Computer, auf dem der Azure Information Protection-Client installiert ist, das Dokument mit der Website für die Dokumentnachverfolgung. Verwenden Sie hierzu entweder eine Office-Anwendung oder den Datei-Explorer. Weitere Anweisungen finden Sie unter [Nachverfolgen und Widerrufen von Dokumenten](./rms-client/client-track-revoke.md). Auf Ihrem Mac können Sie nun über Ihren Webbrowser zur Website für die Dokumentenverfolgung (https://track.azurerms.com)) navigieren, um dieses Dokument nachzuverfolgen und zu widerrufen.

## <a name="when-i-open-an-rms-protected-office-document-does-the-associated-temporary-file-become-rms-protected-as-well"></a>Wenn ich ein RMS-geschütztes Office-Dokument öffne, wird die dazugehörige temporäre Datei ebenfalls von RMS geschützt?
Nein. Die dazugehörige temporäre Datei enthält in diesem Szenario keine Daten aus dem Originaldokument, sondern nur das, was der Benutzer eingibt, während die Datei geöffnet ist. Im Gegensatz zur ursprünglichen Datei soll die temporäre Datei offensichtlich nicht freigegeben werden und verbleibt auf dem Gerät, geschützt durch lokale Sicherheitskontrollen wie BitLocker und EFS.

## <a name="a-feature-i-am-looking-for-doesnt-seem-to-work-with-sharepoint-protected-librariesis-support-for-my-feature-planned"></a>Eine Funktion, die ich suche, scheint nicht mit SharePoint-geschützten Bibliotheken zu funktionieren – ist die Unterstützung dieser Funktion geplant?
Derzeit unterstützt SharePoint mit RMS geschützte Dokumente durch Verwenden von IRM-geschützten Bibliotheken, die weder Rights Management-Vorlagen noch Dokumentkontrolle noch einige andere Funktionen unterstützen. Weitere Informationen finden Sie im Abschnitt [SharePoint Online und SharePoint Server](./office-apps-services-support.md#sharepoint-online-and-sharepoint-server) im Artikel [Office-Anwendungen und -Dienste](./office-apps-services-support.md).

Wenn Sie an einer bestimmten Funktion interessiert sind, die noch nicht unterstützt wird, sollten Sie die Ankündigungen im [Enterprise Mobility and Security Blog](https://cloudblogs.microsoft.com/enterprisemobility/?product=azure-rights-management-services) (Informationen in englischer Sprache zu Enterprise Mobility und Sicherheit) verfolgen.

## <a name="how-do-i-configure-one-drive-for-business-in-sharepoint-online-so-that-users-can-safely-share-their-files-with-people-inside-and-outside-the-company"></a>Wie konfiguriere ich OneDrive for Business in SharePoint Online, sodass Benutzer ihre Dateien sicher für Personen innerhalb und außerhalb des Unternehmens freigeben können?
Als Office 365-Administrator konfigurieren Sie dies normalerweise nicht. Eine solche Konfiguration erfolgt durch Benutzer.

Als SharePoint-Websiteadministrator aktivieren und konfigurieren Sie IRM für eine SharePoint-Bibliothek, deren Besitzer Sie sind. OneDrive for Business ist so konzipiert, dass die Benutzer IRM für ihre eigene OneDrive for Business-Bibliothek aktivieren und konfigurieren. Mithilfe von PowerShell können Sie das jedoch für sie übernehmen. Anweisungen finden Sie im Abschnitt [SharePoint Online und OneDrive for Business: IRM-Konfiguration](configure-office365.md#sharepointonline-and-onedrive-for-business-irm-configuration) im Artikel [Office 365: Konfigurationen für Clients und Onlinedienste](configure-office365.md).

## <a name="do-you-have-any-tips-or-tricks-for-a-successful-deployment"></a>Gibt es besondere Tipps und Tricks für eine erfolgreiche Bereitstellung?

Nachdem wir zahlreiche Bereitstellungen begleitet und uns mit Kunden, Partnern, Beratern und Supportmitarbeitern unterhalten haben, ist das einer der wichtigsten Tipps, den wir aus unserer Erfahrung weitergeben können: **Entwerfen Sie einfache Richtlinien, und stellen Sie sie entsprechend bereit**.

Da Azure Information Protection sichere Freigaben mit praktisch jeder Person unterstützt, können Sie bei der Reichweite des Schutzes Ihrer Daten Ehrgeiz entwickeln. Sie sollten bei der Einschränkung von Nutzungsrechten allerdings konservativ vorgehen. Für die meisten Organisationen hat die Vermeidung von Datenlecks durch eine Zugriffsbeschränkung auf organisationsinterne Personen die größte geschäftliche Bedeutung. Natürlich können Sie viel differenziertere erhalten, als wenn Sie – Personen am drucken, bearbeiten usw. hindern müssen. Behalten Sie jedoch die präziseteren Einschränkungen als Ausnahme für Dokumente bei, die wirklich eine hohe Sicherheit benötigen, und implementieren Sie diese restriktiveren Nutzungsrechte nicht am ersten Tag, sondern planen Sie einen mehrstufigen Ansatz.

## <a name="how-do-we-regain-access-to-files-that-were-protected-by-an-employee-who-has-now-left-the-organization"></a>Wie erhalten wir erneut Zugriff auf Dateien, die von einem Mitarbeiter geschützt wurden, der die Organisation verlassen hat?
Verwenden Sie die [Administratorfunktion](configure-super-users.md). Mit dieser erhalten autorisierte Benutzer Vollzugriff auf alle Dokumente und E-Mails, die durch Ihren Mandanten geschützt sind. Administratoren können diesen geschützten Inhalt immer lesen und bei Bedarf den Schutz aufheben oder den Inhalt erneut für andere Benutzer schützen. Dieselbe Funktion ermöglicht darüber hinaus autorisierten Diensten ggf. die Indizierung und Inspektion von Dateien.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Wenn ich die Sperrung in der Website zur Dokumentnachverfolgung teste, erhalte ich eine Meldung, die angibt, dass Personen für bis zu 30 Tage auf das Dokument zugreifen können. Kann ich diesen Zeitraum konfigurieren?

Ja. Diese Meldung gibt die [Nutzungslizenz](configure-usage-rights.md#rights-management-use-license) für diese bestimmte Datei wieder.

Wenn Sie eine Datei widerrufen, kann diese Aktion nur erzwungen werden, wenn der Benutzer sich beim Azure Rights Management-Dienst authentifiziert. Wenn eine Datei über eine gültige Nutzungslizenz von 30 Tagen verfügt, und der Benutzer das Dokument bereits geöffnet hat, erhält dieser Benutzer weiterhin Zugriff auf das Dokument, solange die Nutzungslizenz gültig ist. Wenn die Nutzungslizenz ausläuft, muss sich der Benutzer erneut authentifizieren. Zu diesem Zeitpunkt wird der Zugriff für den Benutzer verweigert, da das Dokument nun gesperrt ist.

Der Benutzer, der das Dokument geschützt hat, der [Rights Management-Aussteller](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) wird von diesem Widerruf ausgeschlossen und kann immer auf ihre Dokumente zugreifen.

Der Standardwert für die Gültigkeitsdauer der Nutzungslizenz für einen Mandanten beträgt 30 Tage. Diese Einstellung kann nicht von einer restriktiveren Einstellung in einer Bezeichnung oder Vorlage überschrieben werden. Weitere Informationen zur Nutzungslizenz und deren Konfiguration finden Sie in der Dokumentation [Rights Management-Nutzungslizenz](configure-usage-rights.md#rights-management-use-license).

## <a name="can-rights-management-prevent-screen-captures"></a>Kann Rights Management Bildschirmaufnahmen verhindern?
Wenn Sie das [Nutzungsrecht](configure-usage-rights.md)" **Kopieren** " nicht gewähren, können Rights Management Bildschirmaufnahmen von vielen der häufig verwendeten Bildschirm Erfassungs Tools auf Windows-Plattformen (Windows 7, Windows 8.1, Windows 10, Windows 10 Mobile) und Android verhindern. iOS- und Mac-Geräte erlauben Apps jedoch das Verhindern von Bildschirmaufnahmen nicht. Ferner können Browser auf Geräten, gleich welchen, keine Bildschirmaufnahmen verhindern. Die Browser Verwendung umfasst Outlook im Web und Office für das Web.

Das Verhindern von Bildschirmaufnahmen kann dabei helfen, versehentliche oder fahrlässige Offenlegung von vertraulichen oder sensiblen Informationen zu vermeiden. Es gibt jedoch viele Möglichkeiten, wie ein Benutzerdaten freigeben kann, die auf einem Bildschirm angezeigt werden, und ein Screenshot ist nur eine Methode. Beispielsweise kann ein Benutzer, der die angezeigten Informationen vorsätzlich weitergeben möchte, sie mit der Kamera seines Handys abfotografieren, sie abtippen oder einfach mündlich einer anderen Person mitteilen.

Wie diese Beispiele zeigen, kann Technologie selbst dann, wenn alle Plattformen und jegliche Software die Rights Management-APIs unterstützen würden, um Bildschirmaufnahmen zu blockieren, nicht allein Benutzer davon abhalten, Daten offenzulegen, für die dies nicht passieren sollte. Rights Management kann helfen, Ihre wichtigen Daten mithilfe von Autorisierungen und Nutzungsrichtlinien zu schützen, aber Sie sollten diese Lösung für die Rechteverwaltung im Unternehmen durch andere Kontrollmaßnahmen ergänzen. Arbeiten Sie z. B. mit physischen Sicherheitskontrollen, prüfen und überwachen Sie die Mitarbeiter, die zum Zugriff auf Unternehmens- oder Organisationsdaten autorisiert sind, und investieren Sie in Benutzerschulungen, damit die Benutzer verstehen, welche Daten nicht weitergegeben oder geteilt werden dürfen.

## <a name="whats-the-difference-between-a-user-protecting-an-email-with-do-not-forward-and-a-template-that-doesnt-include-the-forward-right"></a>Welcher Unterschied besteht zwischen dem Schützen einer E-Mail mit der Option „Nicht weiterleiten“ und dem Schützen mit einer Vorlage, die die Berechtigung „Weiterleiten“ nicht gewährt?

Trotz ihres Namens und ihrer Darstellung ist die Option **Nicht weiterleiten** weder das Gegenteil der Berechtigung „Weiterleiten“ noch eine Vorlage. Es handelt sich eigentlich um einen Satz von Rechten, die das Einschränken von kopieren, Drucken und Speichern der e-Mail außerhalb des Postfachs, zusätzlich zum Einschränken der Weiterleitung von e-Mails, beinhalten. Die Berechtigungen werden über die ausgewählten Empfänger dynamisch auf Benutzer angewendet, und nicht statisch durch den Administrator zugewiesen. Weitere Informationen finden Sie im Abschnitt "nicht [weiterleiten" für e-Mails](configure-usage-rights.md#do-not-forward-option-for-emails) unter [Konfigurieren von Nutzungsrechten für Azure Information Protection](configure-usage-rights.md).

