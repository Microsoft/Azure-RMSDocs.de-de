---
title: Häufig gestellte Fragen zum Azure Information Protection des klassischen Clients
description: Einige häufig gestellte Fragen zu Azure Information Protection und dem dazugehörigen Schutzdienst, Azure Rights Management (Azure RMS). Die hier aufgeführten FAQs sind nur für den klassischen AIP-Client relevant.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 03/07/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: 9f53544a201d3500f63c472b5cdd58e01c69dc1f
ms.sourcegitcommit: 8a45d209273d748ee0f2a96c97893288c0b7efa5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2021
ms.locfileid: "102446897"
---
# <a name="frequently-asked-questions-for-the-azure-information-protection-classic-client"></a>Häufig gestellte Fragen zum Azure Information Protection klassischen Clients

>***Gilt für:** [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified Bezeichnung nur klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Weitere Informationen finden Sie unter [häufig gestellte Fragen zu Azure Information Protection](faqs.md). *

In diesem Artikel werden häufig gestellte Fragen im Zusammenhang mit dem klassischen Azure Information Protection-Client aufgeführt.

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

## <a name="is-the-azure-information-protection-client-only-for-subscriptions-that-include-classification-and-labeling"></a>Ist der Azure Information Protection-Client nur für Abonnements geeignet, die Funktionen für Klassifizierung und Bezeichnung umfassen?

Nein. Der klassische AIP-Client kann auch mit Abonnements verwendet werden, die nur den Azure Rights Management-Dienst zum Schutz von Daten enthalten.

Wenn der klassische Client ohne eine Azure Information Protection Richtlinie installiert wird, wird der Client automatisch im reinen [Schutzmodus](./rms-client/client-protection-only-mode.md)betrieben, sodass Benutzer Rights Management Vorlagen und benutzerdefinierte Berechtigungen anwenden können. 

Wenn Sie zu einem späteren Zeitpunkt ein Abonnement erwerben, das Klassifizierungen und Bezeichnungen umfasst, wechselt der Client beim Herunterladen der Azure Informationen Protection-Richtlinie automatisch in den Standardmodus.


## <a name="whats-the-difference-between-windows-server-fci-and-the-azure-information-protection-scanner"></a>Worin besteht der Unterschied zwischen der Windows Server-FCI und der Azure Information Protection Scanner?

Die Windows Server-Dateiklassifizierungsinfrastruktur war eine Option, um Dokumente zu klassifizieren und diese dann mithilfe des [Rights Management-Connectors](deploy-rms-connector.md) (nur Office-Dokumente) oder einem [PowerShell-Skript](./rms-client/configure-fci.md) (alle Dateitypen) zu schützen. 

Jetzt können Sie die empfohlene [Azure Information Protection-Überprüfung](deploy-aip-scanner.md) verwenden. Die Überprüfung nutzt den Azure Information Protection-Client und Ihre Azure Information Protection-Richtlinie, um Dokumente (alle Dateitypen) zu bezeichnen, sodass diese Dokumente alle klassifiziert und optional auch geschützt werden.

Zwischen den beiden Lösungen bestehen die folgenden wesentlichen Unterschiede:

|  |Windows Server-Dateiklassifizierungsinfrastruktur  |Azure Information Protection-Überprüfung  |
|---------|---------|---------|
|**Unterstützte Datenspeicher**    | Lokale Ordner unter Windows Server        | – Windows-Dateifreigaben und Network Attached Storage<br /><br />– SharePoint Server 2016 und SharePoint Server 2013 SharePoint Server 2010 wird außerdem für Kunden unterstützt, die über [erweiterten Support für diese Version von SharePoint](https://support.microsoft.com/lifecycle/search?alpha=SharePoint%20Server%202010) verfügen.        |
|**Betriebsmodus**     |Echtzeit         |Die Datenspeicher werden systematisch einmal oder wiederholt durchsucht.         |
|**Unterstützte Dateitypen**     | – Standardmäßig werden alle Dateitypen geschützt. <br /><br />– Bestimmte Dateitypen können vom Schutz ausgeschlossen werden, indem Sie die Registrierung bearbeiten.|Unterstützung für Dateitypen: <br /><br />– Die Office-Dateiformate und PDF-Dokumente werden standardmäßig geschützt. <br /><br />– Weitere Dateitypen können ebenfalls geschützt werden, indem Sie die Registrierung bearbeiten.|

### <a name="setting-rights-management-owners"></a>Festlegen von Rights Management Besitzern

Standardmäßig wird für die Windows Server-FCI und den Azure Information Protection Scanner der [Rights Management Besitzer](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner) auf das Konto festgelegt, mit dem die Datei geschützt wird.

Überschreiben Sie die Standardeinstellungen wie folgt:

- **Windows Server-FCI**: Legen Sie für den Rights Management Besitzer ein einzelnes Konto für alle Dateien fest, oder legen Sie den Rights Management Besitzer für jede Datei dynamisch fest. 

    Um den Rights Management-Besitzer dynamisch festzulegen, verwenden Sie den Parameter **-OwnerMail [Source File Owner Email]** und seinen Wert. Durch diese Konfiguration wird die E-Mail-Adresse des Benutzers von Active Directory mithilfe des Benutzerkontonamens in der Owner-Eigenschaft der Datei abgerufen.

- **Azure Information Protection Scanner**: Legen Sie für neu geschützte Dateien für den Rights Management Besitzer ein einzelnes Konto für alle Dateien in einem angegebenen Datenspeicher fest, indem Sie die Einstellung **-Standard Besitzer** im Überprüfungs Profil angeben. 

    Das dynamische Festlegen des Rights Management Besitzers für jede Datei wird nicht unterstützt, und der Besitzer der Rights Management wird für zuvor geschützte Dateien nicht geändert. 

    > [!NOTE]
    > Wenn der Scanner Dateien auf Websites und in Bibliotheken von SharePoint schützt, wird der Rights Management-Besitzer dynamisch für jede Datei mithilfe des SharePoint-Editorwerts festgelegt.

## <a name="can-a-file-have-more-than-one-classification"></a>Kann eine Datei über mehr als eine Klassifizierung verfügen?

Benutzer können für jedes Dokument und jede E-Mail immer nur eine Bezeichnung gleichzeitig auswählen, was oft zu nur einer Klassifizierung führt. Wenn Benutzer jedoch eine untergeordnete Bezeichnung auswählen, werden zwei Bezeichnungen zur gleichen Zeit angewendet: eine primäre Bezeichnung und eine sekundäre Bezeichnung. Durch die Verwendung von untergeordneten Bezeichnungen kann eine Datei über zwei Klassifizierungen verfügen, die eine Über-/Untergeordnet-Beziehung für eine zusätzliche Kontrollebene markieren.

Beispielsweise könnte die Bezeichnung **Vertraulich** Unterbezeichnungen wie z.B. **Legal** (Recht) und **Finance** (Finanzen) enthalten. Sie können unterschiedliche visuelle Klassifizierungskennzeichnungen und unterschiedliche Rights Management-Vorlagen auf diese Unterbezeichnungen anwenden. Ein Benutzer kann die Bezeichnung **Vertraulich** nicht selbst auswählen, sondern nur eine der untergeordneten Bezeichnungen, z.B. **Legal** (Recht). Daher wird als festgelegte Bezeichnung **Confidential \ Legal** (Vertraulich\Recht) angezeigt. Die Metadaten für diese Datei enthalten eine benutzerdefinierte Texteigenschaft für **Confidential** (Vertraulich), eine benutzerdefinierte Texteigenschaft für **Legal** (Recht) und eine weitere mit beiden Werten (**Confidential Legal** (Vertraulich Recht)). 

Bei der Verwendung von untergeordneten Bezeichnungen konfigurieren Sie optische Kennzeichnungen, Schutz und Bedingungen für die primäre Bezeichnung. Bei der Verwendung von Unterebenen konfigurieren Sie diese Einstellungen nur für die untergeordnete Bezeichnung. Wenn Sie diese Einstellungen für die übergeordnete und deren untergeordnete Bezeichnung konfigurieren, haben die Einstellungen der untergeordneten Bezeichnung Vorrang.
## <a name="how-do-i-prevent-somebody-from-removing-or-changing-a-label"></a>Wie hindere ich jemanden daran, eine Bezeichnung zu entfernen oder zu ändern?

Es gibt zwar eine [Richtlinien Einstellung](configure-policy-settings.md) , bei der Benutzer angeben müssen, warum Sie eine Klassifizierungs Bezeichnung herabsetzen, eine Bezeichnung entfernen oder den Schutz entfernen, aber diese Einstellung verhindert diese Aktionen nicht. Um Benutzer daran zu hindern, eine Bezeichnung zu entfernen oder zu ändern, muss der Inhalt bereits geschützt sein, und die Schutz Berechtigungen gewähren dem Benutzer nicht das [Nutzungsrecht](configure-usage-rights.md) "Exportieren" oder "Vollzugriff".

## <a name="how-can-dlp-solutions-and-other-applications-integrate-with-azure-information-protection"></a>Wie können DLP-Lösungen und andere Anwendungen in Azure Information Protection integriert werden?

Da Azure Information Protection persistente Metadaten für die Klassifizierung verwendet, die eine Klartextbezeichnung enthalten, können diese Informationen von DLP-Lösungen und anderen Anwendungen gelesen werden. 

Weitere Informationen zu diesen Metadaten finden Sie unter [In E-Mails und Dokumenten gespeicherte Bezeichnungsinformationen](configure-policy.md#label-information-stored-in-emails-and-documents).

Beispiele für die Verwendung dieser Metadaten mit Exchange Online-Nachrichtenflussregeln finden Sie unter [Konfigurieren von Exchange Online-Nachrichtenflussregeln für Azure Information Protection-Bezeichnungen](configure-exo-rules.md).

## <a name="can-i-create-a-document-template-that-automatically-includes-the-classification"></a>Kann ich eine Dokumentvorlage erstellen, die automatisch die Klassifizierung umfasst?

Ja. Sie können eine Bezeichnung konfigurieren, um [eine Kopf- oder Fußzeile anzuwenden, die den Namen der Bezeichnung enthält](configure-policy-markings.md). Wenn dies jedoch nicht Ihren Anforderungen entspricht, können Sie für den Azure Information Protection klassischen Client nur eine Dokument Vorlage mit der gewünschten Formatierung erstellen und die Klassifizierung als Feldcode hinzufügen. 

Beispielsweise könnten Sie eine Tabelle in der Kopfzeile des Dokuments einrichten, die die Klassifizierung angezeigt. Verwenden Sie alternativ eine bestimmte Formulierung für eine Einführung, die auf die Klassifizierung des Dokuments verweist.

So fügen Sie diesen Feldcode Ihrem Dokument hinzu:

1. Geben Sie dem Dokument eine Bezeichnung, und speichern Sie es. So werden neue Metadatenfelder erstellt, die Sie jetzt für Ihren Feldcode verwenden können.

2. Positionieren Sie den Cursor im Dokument dort, wo Sie die Bezeichnung der Klassifizierung hinzufügen möchten, und wählen Sie anschließend auf der Registerkarte **Einfügen****Text** > **Schnellbausteine** > **Feld** aus.

3. Wählen Sie im Dialogfeld **Feld** in der Dropdownliste **Kategorien****Dokumentinformationen** aus. Wählen Sie dann in der Dropdownliste **Feldernamen****DocProperty** aus.

4. Wählen Sie in der Dropdownliste **Eigenschaft****Vertraulichkeit** und dann **OK**.

Die aktuelle Klassifizierung der Bezeichnung wird im Dokument angezeigt, und dieser Wert wird automatisch aktualisiert, wenn Sie das Dokument öffnen oder die Vorlage verwenden. Wenn sich also die Bezeichnung ändert, wird die Klassifizierung, die für diesen Feldcode angezeigt wird, automatisch im Dokument aktualisiert.

## <a name="how-is-classification-for-emails-using-azure-information-protection-different-from-exchange-message-classification"></a>Wie unterscheidet sich die Klassifizierung für e-Mails mit Azure Information Protection von der Exchange-Nachrichtenklassifizierung?

Die Exchange-Nachrichtenklassifizierung ist ein älteres Feature, mit dem e-Mails klassifiziert werden können, und es wird unabhängig von Azure Information Protection Bezeichnungen oder Vertraulichkeits Bezeichnungen implementiert, die die Klassifizierung anwenden.

Sie können dieses ältere Feature jedoch in Bezeichnungen integrieren, sodass Benutzer, die eine e-Mail mithilfe von Outlook im Web klassifizieren und einige Mobile Mail-Anwendungen verwenden, automatisch die Bezeichnung Klassifizierung und entsprechende Bezeichnungs Markierungen hinzufügen.

Auf dieselbe Weise können Sie Ihre Bezeichnungen mit Outlook im Web und diesen mobilen E-Mail-Anwendungen verwenden.

Beachten Sie, dass dies nicht erforderlich ist, wenn Sie Outlook im Web mit Exchange Online verwenden, da diese Kombination eine integrierte Bezeichnung unterstützt, wenn Sie Vertraulichkeits Bezeichnungen aus dem Office 365 Security & Compliance Center, Microsoft 365 Security Center oder Microsoft Compliance Center veröffentlichen.

Wenn Sie die integrierte Bezeichnung nicht mit Outlook im Web verwenden können, finden Sie weitere Informationen in den Konfigurationsschritten für diese Problem Umgehung: [Integration in die Legacy-Exchange-Nachrichtenklassifizierung](rms-client/client-admin-guide-customizations.md#integration-with-the-legacy-exchange-message-classification) .

## <a name="how-do-i-configure-a-mac-computer-to-protect-and-track-documents"></a>Wie konfiguriere ich einen Mac-Computer zum Schützen und Nachverfolgen von Dokumenten?

Stellen Sie zuerst anhand des Softwareinstallationslinks unter https://admin.microsoft.com sicher, dass Office für Mac installiert ist. Vollständige Anweisungen finden [Sie unter herunterladen und installieren oder Neuinstallieren von Microsoft 365 oder Office 2019 auf einem PC oder Mac](https://support.office.com/article/Download-and-install-or-reinstall-Office-365-or-Office-2016-on-a-PC-or-Mac-4414EAAF-0478-48BE-9C42-23ADC4716658).

Öffnen Sie Outlook, und erstellen Sie ein Profil mit Ihrem Microsoft 365 Geschäfts-, Schul-oder unikonto. Erstellen Sie anschließend eine neue Nachricht, und führen Sie die folgenden Schritte aus, um Office so zu konfigurieren, dass Dokumente und E-Mails mithilfe von Azure Rights Management-Service geschützt werden können:

1. Klicken Sie in der neuen Nachricht auf der Registerkarte **Optionen** auf **Berechtigungen**, und klicken Sie dann auf **Anmeldeinformationen überprüfen**.

2. Wenn **Sie dazu** aufgefordert werden, geben Sie die Details Ihres Microsoft 365 Geschäfts-, Schul-oder unikontos erneut an

    Die Azure Rights Management-Vorlagen werden nun heruntergeladen, und **Anmeldeinformationen überprüfen** wird durch Optionen wie **Keine Einschränkungen**, **Nicht weiterleiten** und alle Azure Rights Management-Vorlagen ersetzt, die für Ihren Mandanten veröffentlicht werden. Sie können diese neue Nachricht jetzt abbrechen.

So schützen Sie eine E-Mail-Nachricht oder ein Dokument: Klicken Sie auf der Registerkarte **Optionen** auf **Berechtigungen**, und wählen Sie eine Option oder eine Vorlage aus, die Ihre E-Mail oder Ihr Dokument schützt.

Zum Nachverfolgen eines Dokuments nach dem Schutz: über einen Windows-Computer, auf dem der Azure Information Protection Classic-Client installiert ist, registrieren Sie das Dokument mithilfe einer Office-Anwendung oder eines Datei-Explorers bei der Website für die Dokument Nachverfolgung. Anweisungen hierzu finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente](./rms-client/client-track-revoke.md). Auf Ihrem Mac können Sie nun über Ihren Webbrowser zur Website für die Dokumentenverfolgung (https://track.azurerms.com)) navigieren, um dieses Dokument nachzuverfolgen und zu widerrufen.

## <a name="when-i-test-revocation-in-the-document-tracking-site-i-see-a-message-that-says-people-can-still-access-the-document-for-up-to-30-daysis-this-time-period-configurable"></a>Wenn ich den Widerruf auf der Dokumentnachverfolgungsseite teste, sehe ich eine Meldung, die besagt, dass Personen bis zu 30 Tage lang auf das Dokument zugreifen können. Ist dieser Zeitraum konfigurierbar?

Ja. Diese Meldung gibt die [Nutzungslizenz](configure-usage-rights.md#rights-management-use-license) für diese bestimmte Datei an.

Wenn Sie eine Datei widerrufen, kann diese Aktion nur erzwungen werden, wenn sich der Benutzer bei Azure Rights Management Service authentifiziert. Wenn eine Datei also eine Gültigkeitsdauer der Nutzungslizenz von 30 Tagen aufweist und der Benutzer das Dokument bereits geöffnet hat, hat dieser Benutzer für die Dauer der Nutzungslizenz weiterhin Zugriff auf das Dokument. Wenn die Nutzungslizenz abläuft, muss sich der Benutzer erneut authentifizieren. Daraufhin wird dem Benutzer der Zugriff verweigert, da das Dokument nun widerrufen ist.

Der Benutzer, der das Dokument geschützt hat (der [Rights Management-Herausgeber](configure-usage-rights.md#rights-management-issuer-and-rights-management-owner)), ist von diesem Widerruf ausgenommen und kann jederzeit auf seine Dokumente zugreifen.

Der Standardwert für den Gültigkeitszeitraum der Nutzungslizenz für einen Mandanten beträgt 30 Tage. Diese Einstellung kann durch eine restriktivere Einstellung in einer Bezeichnung oder einer Vorlage überschrieben werden. Weitere Informationen zur Nutzungslizenz und deren Konfiguration finden Sie in der Dokumentation zur [Rights Management-Nutzungslizenz](configure-usage-rights.md#rights-management-use-license).

## <a name="whats-the-difference-between-byok-and-hyok-and-when-should-i-use-them"></a>Worin besteht der Unterschied zwischen Byok und Hyok, und wann sollte ich Sie verwenden?

**Bring Your Own Key** (BYOK) im Kontext von Azure Information Protection bedeutet, dass Sie Ihren eigenen Schlüssel für den Schutz von Azure Rights Management lokal erstellen. Anschließend übertragen Sie diesen Schlüssel an ein Hardwaresicherheitsmodul (HSM) in Azure Key Vault, wo Sie weiterhin Besitzer des Schlüssels sind und diesen verwalten. Wenn Sie nicht so vorgegangen wären, würde der Schutz von Azure Rights Management einen Schlüssel verwenden, der automatisch für Sie in Azure erstellt und verwaltet wird. Diese Standardkonfiguration wird als „von Microsoft verwaltet“ und nicht als „vom Kunden verwaltet“ (Option BYOK) bezeichnet.

Weitere Informationen zu BYOK und dazu, ob Sie diese Schlüsseltopologie für Ihre Organisation auswählen sollten, finden Sie unter [Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](plan-implement-tenant-key.md).

**Hold Your Own Key** (HYOK) im Kontext von Azure Information Protection eignet sich für einige wenige Organisationen, die über eine Teilmenge von Dokumenten oder E-Mails verfügen, die nicht durch einen Schlüssel geschützt werden können, der in der Cloud gespeichert ist. Für diese Organisationen gilt diese Einschränkung selbst dann, wenn sie den Schlüssel erstellt haben und mit BYOK verwalten. Die Einschränkung kann oft aus rechtlichen oder Konformitätsgründen erfolgen, und die HYOK-Konfiguration sollte nur auf Informationen des Typs „Top Secret“ angewendet werden, die niemals außerhalb der Organisation freigegeben werden, nur im internen Netzwerk genutzt werden und nicht von mobilen Geräten aus zugänglich sein müssen.

Für diese Ausnahmen (in der Regel weniger als 10 % des gesamten zu schützenden Inhalts) können Unternehmen eine lokale Lösung (Active Directory Rights Management Services) verwenden, um den Schlüssel zu erstellen, der lokal gespeichert bleibt. Mit dieser Lösung erhalten Computer ihre Azure Information Protection-Richtlinie aus der Cloud, aber diese identifizierten Inhalte können durch Verwendung des lokalen Schlüssels geschützt werden.

Weitere Informationen zu HYOK und zu den Grenzen und Einschränkungen von HYOK sowie Hinweise zur Verwendung finden Sie unter [HYOK-Anforderungen (Hold Your Own Key) und -Einschränkungen für den AD RMS-Schutz](configure-adrms-restrictions.md).

## <a name="what-do-i-do-if-my-question-isnt-here"></a>Was kann ich tun, wenn meine Frage hier nicht angezeigt wird?

Überprüfen Sie zunächst die unten aufgeführten häufig gestellten Fragen, die für die Klassifizierung und Bezeichnung spezifisch sind bzw. für die Datensicherheit spezifisch sind. Der [Azure Rights Management-Dienst (Azure RMS)](what-is-azure-rms.md) stellt die Datenschutztechnologie für Azure Information Protection bereit. Azure RMS kann zusammen mit einer Klassifizierung oder Bezeichnung verwendet werden. Es kann aber auch eigenständig genutzt werden. 

- [Häufig gestellte Fragen zu Azure Information Protection](faqs.md)

- [Häufig gestellte Fragen zur Klassifizierung und Kennzeichnung](faqs-infoprotect.md)

- [Häufig gestellte Fragen zum Datenschutz](faqs-rms.md)

Wenn Ihre Frage nicht beantwortet wird, lesen Sie die Links und Ressourcen, die unter [Informationen und Support für Azure Information Protection](information-support.md)aufgeführt sind.

Darüber hinaus gibt es häufig gestellte Fragen (FAQs) für Benutzer:

- [Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android](./rms-client/mobile-app-faq.md)

- [Häufig gestellte Fragen (FAQ) zur RMS-Freigabeanwendung für Mac-Computer](/previous-versions/msdn10/dn451248(v=msdn.10))