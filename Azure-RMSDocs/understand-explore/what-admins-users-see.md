---
title: "Ansicht für Administratoren und Benutzer in Azure RMS – AIP"
description: "Hier finden Sie einige typische Beispiele dafür, wie Administratoren und Benutzern die Azure Rights Management-Technologie (Azure RMS) angezeigt wird und wie sie verwendet werden kann, um sensible oder vertrauliche Informationen zu schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 013e0eb4-49a7-4e81-9e4d-f56c0ceb017f
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 254386ad7cda2d3e178eb9520e6282abe609c158
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="azure-rms-in-action-what-administrators-and-users-see"></a>Azure RMS in Aktion: Was für Administratoren und Benutzer angezeigt wird

>*Gilt für: Azure Information Protection, Office 365*

Dieser Artikel zeigt einige typische Beispiele dafür, wie Administratoren und Benutzern Azure Rights Management (Azure RMS) angezeigt wird und wie Azure RMS verwendet werden kann, um sensible oder vertrauliche Informationen zu schützen.

> [!NOTE]
> In allen diesen Beispielen, in denen Azure RMS Daten schützt, verfügt der Besitzer der Inhalte auch weiterhin über Vollzugriff auf die Daten (Dateien oder E-Mail). Dies gilt selbst dann, wenn der angewendete Schutz Berechtigungen für eine Gruppe gewährt, in der der Besitzer nicht Mitglied war, oder wenn der angewendete Schutz ein Ablaufdatum enthält.
>
> Entsprechend kann die IT stets ohne Einschränkungen mithilfe der Funktion „Administrator“ von Rights Management auf die geschützten Daten zugreifen. Diese Funktion gewährt autorisierten Benutzern oder Diensten, die Sie angeben, delegierten Zugriff. Darüber hinaus können die IT-Mitarbeiter die Nutzung für Daten verfolgen und überwachen, die geschützt werden – z. B., wer auf die Daten zugreift und wann dies geschieht.

Weitere Screenshots und Videos, die RMS in Aktion zeigen, finden Sie im [Enterprise Mobility and Security Blog](https://blogs.technet.microsoft.com/enterprisemobility/?product=azure-rights-management-services) (Informationen in englischer Sprache zu Enterprise Mobility und Sicherheit).

## <a name="activating-and-configuring-rights-management"></a>Aktivieren und Konfigurieren von Rights Management
Obwohl Sie Windows PowerShell zum Aktivieren und Konfigurieren von Azure RMS verwenden können, geschieht dies am einfachsten über das Verwaltungsportal. Sobald der Dienst aktiviert wurde, stehen Ihnen zwei Standardvorlagen zur Verfügung, die Administratoren und Benutzer auswählen können, um schnell und einfach Schutz von Informationen auf Dateien anzuwenden. Sie können aber auch eigene benutzerdefinierten Vorlagen für zusätzliche Optionen und Einstellungen erstellen.

![Screenshots aus den Verwaltungsportalen, die die Option zum Aktivieren des Azure Rights Management-Diensts zeigen](../media/AzRMS_StoryboardActivate_small1.png)


**WAS ADMINISTRATOREN IN SCHRITT 1 ANGEZEIGT WIRD**: Zum Aktivieren von RMS können Sie entweder das Office 365-Administrationscenter (erstes Bild) oder das klassische Azure-Portal (zweites Bild) verwenden.<br /><br />Sie benötigen nur einen Klick zum Aktivieren und einen weiteren Klick zum Bestätigen – dann ist der Schutz von Informationen für Administratoren und Benutzer in Ihrer Organisation aktiviert.

---

![Screenshots aus dem klassischen Azure-Portal, die die zwei Standardvorlagen und den Start des Assistenten zum Erstellen einer neuen Vorlage zeigen](../media/AzRMS_TemplatesPortal_small.png)

**WAS ADMINISTRATOREN IN SCHRITT 2 ANGEZEIGT WIRD**: Nach der Aktivierung stehen zwei Vorlagen für Benutzerrechterichtlinien automatisch für Ihre Organisation zur Verfügung. Eine Vorlage ist für den schreibgeschützten Zugriff (**Confidential View Only** ist im Namen enthalten) vorgesehen, die andere für den Lese- und Änderungszugriff (**Confidential**).

Wenn diese Vorlagen auf Dateien oder E-Mail-Nachrichten angewendet werden, schränken sie den Zugriff auf Benutzer in Ihrer Organisation ein. Auf diese Weise können Sie sehr schnell und einfach verhindern, dass Firmendaten an Personen außerhalb Ihrer Organisation gelangen.

> [!TIP]
> Diese Standardvorlagen können Sie leicht erkennen, da ihnen der Name Ihrer Organisation automatisch vorangestellt wird. In unserem Beispiel lautet er **VanArsdel, Ltd**.

Wenn Sie Benutzer diese Vorlagen nicht anzeigen sollen oder wenn Sie eigene Vorlagen erstellen möchten, verwenden Sie das klassische Azure-Portal. Wie in dieser Abbildung gezeigt wird, führt Sie ein Assistent durch den Erstellungsvorgang für benutzerdefinierte Vorlagen.

---

![Screenshots aus dem klassischen Azure-Portal, die einige der Vorlagenkonfigurationsoptionen zeigen](../media/AzRMS_TemplatesSettings3.png)

**WAS ADMINISTRATOREN IN SCHRITT 3 ANGEZEIGT WIRD**: Offlinezugriff, Ablaufeinstellungen und ob die Vorlage sofort veröffentlicht (Sichtbarmachen in Anwendungen, die Rights Management unterstützen) werden soll, sind einige der Konfigurationseinstellungen, die Ihnen beim Erstellen eigener Vorlagen zur Verfügung stehen.

---

![Screenshots aus dem Datei-Explorer und Word, die die verfügbaren Vorlagen zum Auswählen für Benutzer zeigen](../media/AzRMS_TemplatesPortal_ExplorerWord3.png)

**WAS BENUTZERN IN SCHRITT 4 ANGEZEIGT WIRD**: Durch das Veröffentlichen dieser Vorlagen können Benutzer sie nun in Anwendungen, z. B. Datei-Explorer und Microsoft Word, auswählen:

- Ein Benutzer kann z. B. die Standardvorlage **VanArsdel, Ltd – Vertraulich** auswählen. Anschließend können nur Mitarbeiter des Unternehmens VanArsdel dieses Dokument öffnen und verwenden. Dies gilt selbst dann, wenn es später per E-Mail an jemanden außerhalb des Unternehmens gesendet oder an einem öffentlichen Speicherort gespeichert wird.

- Ein Benutzer kann die benutzerdefinierte Vorlage auswählen, die der Administrator erstellt hat: **Vertrieb und Marketing – Nur lesen und drucken**. Dann ist die Datei nicht nur vor Personen außerhalb des Unternehmens geschützt, sondern sie ist auch auf Mitarbeiter aus der Vertriebs und Marketingabteilung beschränkt. Darüber hinaus besitzen diese Mitarbeiter keinen Vollzugriff auf das Dokument, sondern können es nur lesen und drucken. Sie können es z. B. nicht ändern oder Teile daraus kopieren.

---

**Weitere Informationen zu diesem Szenario:**

- Eine schrittweise Anleitung finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md) und [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).

- Informationen zum Schützen wichtiger Unternehmensdateien durch Benutzer finden Sie unter [Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst](../deploy-use/help-users.md).

Im Folgenden finden Sie einige Beispiele dafür, wie Administratoren die Vorlagen anwenden können, um automatisch den Datenschutz für Dateien und E-Mails zu konfigurieren.

## <a name="automatically-protecting-files-on-file-servers-running-windows-server-and-file-classification-infrastructure"></a>Automatischer Schutz von Dateien auf Dateiservern, auf denen Windows Server und Dateiklassifizierungsinfrastruktur ausgeführt wird

Dieses Beispiel zeigt, wie Sie Azure RMS verwenden können, um Dateien auf Dateiservern automatisch zu schützen, die mindestens Windows Server 2012 ausführen und für die Verwendung der Dateiklassifizierungsinfrastruktur konfiguriert sind.

Es gibt viele Möglichkeiten, Klassifizierungswerte auf Dateien anzuwenden. Sie können z. B. den Inhalt von Dateien untersuchen und entsprechend integrierte Klassifizierungen wie Vertraulichkeit und personenbezogene Informationen anwenden. Ein Administrator erstellt jedoch in diesem Beispiel eine benutzerdefinierte Klassifizierung von **Marketing** , die automatisch für alle Benutzerdokumente gilt, die im Ordner **Marketingaktionen** gespeichert werden. Obwohl dieser Ordner durch NTFS-Berechtigungen geschützt ist, die den Zugriff auf Mitglieder der Gruppe Marketing einschränken, weiß der Administrator, dass diese Berechtigungen verloren gehen können, wenn jemand aus dieser Gruppe die Dateien verschiebt oder per E-Mail sendet. In diesem Fall könnte auf die Informationen in den Dateien durch nicht autorisierte Benutzer zugegriffen werden.

![Screenshots, die die Installation und Konfiguration des Rights Management-Connectors zeigen](../media/AzRMS_FCI_ConnectorSmall.png)

**WAS ADMINISTRATOREN IN SCHRITT 1 ANGEZEIGT WIRD**: Der Administrator installiert und konfiguriert den Rights Management (RMS) Connector, der als Relais zwischen lokalen Servern und Azure RMS fungiert.

---

![Screenshots, die einige „Konfiguration“-Dialogfelder zum Konfigurieren der Dateiklassifizierungsinfrastruktur unter Windows Server zeigen](../media/AzRMS_ExampleFCI_ConfigurationSmall.png)

**WAS ADMINISTRATOREN IN SCHRITT 2 ANGEZEIGT WIRD**: Auf dem Dateiserver konfiguriert der Administrator die Klassifizierungsregeln und -aufgaben, damit alle Benutzerdateien im Ordner **Marketingaktionen** automatisch als **Marketing** klassifiziert und mit RMS-Verschlüsselung geschützt werden.

Er wählt die benutzerdefinierte RMS-Vorlage aus, die im ersten Beispiel erstellt wurde, die den Zugriff auf die Mitglieder der Vertriebs- und Marketingabteilungen einschränkt: **Vertrieb und Marketing – nur Lesen und Drucken**

Dies hat zur Folge, dass alle Dokumente in diesem Ordner automatisch mit der Marketing-Klassifizierung konfiguriert und durch die Vertriebs- und Marketingvorlage von RMS geschützt werden.

---

![Screenshots, die eine Beispiel-E-Mail zeigt, die ein Benutzer zusammen mit einem geschützten Anhang erhält, worin er zur Authentifizierung aufgefordert wird, bevor dieser geöffnet werden kann](../media/AzRMS_FCI_EmailSmall.png)

**WAS BENUTZERN IN SCHRITT 3 ANGEZEIGT WIRD**: So verhindert RMS, dass Daten an Personen gelangen, die keinen Zugriff auf sensible oder vertrauliche Informationen besitzen sollten:

- Julia aus der Marketingabteilung, sendet per E-Mail einen vertraulichen Bericht aus dem Ordner Marketing Promotions. Dieser Bericht enthält neue Produktfeatures und Werbepläne und wird von einem Kollegen angefordert, der derzeit auf Geschäftsreise ist. Julia sendet den Bericht allerdings versehentlich per E-Mail an die falsche Person. Sie hat nicht bemerkt, dass sie versehentlich einen Empfänger mit einem ähnlichen Namen in einem anderen Unternehmen ausgewählt hat.<br><br>
Der Empfänger kann den vertraulichen Bericht nicht lesen, weil er kein Mitglied der Gruppe Vertrieb und Marketing ist.

---

**Weitere Informationen zu diesem Szenario:**

- Eine schrittweise Anleitung finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

## <a name="automatically-protecting-emails-with-exchange-online-and-data-loss-prevention-policies"></a>Automatischer Schutz für E-Mail-Nachrichten mit Exchange Online und Richtlinien zum Schutz vor Datenverlust

Im vorherigen Beispiel wurde gezeigt, wie Sie Dateien automatisch schützen können, die vertrauliche Informationen enthalten. Doch was geschieht, wenn die Informationen nicht in einer Datei, sondern in einer E-Mail-Nachricht enthalten sind? Hier greifen die Richtlinien zur Verhinderung von Datenverlusten (Data Loss Prevention, DLP) von Exchange Online, die Sie zum Anwenden von Schutz von Informationen (mithilfe von Richtlinientipps) auffordern oder diesen automatisch (mithilfe von Transportregeln) anwenden.

In diesem Beispiel konfiguriert der Administrator eine Richtlinie, damit die Organisation den US-Bestimmungen zum Schutz personenbezogener Daten genügt. Es können jedoch auch Regeln für andere Genehmigungsregelungen bzw. benutzerdefinierte Regeln konfiguriert werden, die Sie definieren.

![Beispiel-Screenshot für einige der Konfigurationsoptionen zum Konfigurieren der Verhinderung von Datenverlust für Exchange Online](../media/AzRMS_DLPExample1.png)

**WAS ADMINISTRATOREN IN SCHRITT 1 ANGEZEIGT WIRD**: Im Exchange Admin Center wird die Exchange-Vorlage namens **USA – Daten mit persönlich identifizierbaren Informationen (PII)** vom Administrator zum Erstellen und Konfigurieren einer neuen DLP-Richtlinie verwendet. Diese Vorlage sucht nach Informationen in E-Mail-Nachrichten, z. B. nach Sozialversicherungsnummern und Führerscheinnummern.

Die Regeln sind so konfiguriert, dass auf E-Mail-Nachrichten, die diese Informationen enthalten und an Empfänger außerhalb des Unternehmens gesendet werden, automatisch Rechteschutz mithilfe einer RMS-Vorlage angewendet wird, die den Zugriff ausschließlich auf Mitarbeiter des Unternehmens einschränkt.

Hier wird die Regel so konfiguriert, dass eine der Standardvorlagen verwendet wird: **VanArsdel, Ltd – Vertraulich**aus unserem ersten Beispiel. Sie können jedoch auch sehen, dass die Vorlagenauswahl alle benutzerdefinierten Vorlagen enthält, die Sie erstellt haben, sowie eine Option **Nicht weiterleiten**, die für Exchange spezifisch ist.

> [!NOTE]
> Wenn die angezeigten Konfigurationsoptionen von der Abbildung abweichen, müssen Sie beim Konfigurieren der Regel möglicherweise zunächst **Weitere Optionen** auswählen. Anschließend können Sie **Nachrichtensicherheit ändern** > **Rechteschutz anwenden** und dann die RMS-Vorlage auswählen.

---

![Screenshot einer Beispiel-E-Mail, die eine US-Sozialversicherungsnummer enthält](../media/AzRMS_DLPUnprotectedEmail_small.png)

**WAS BENUTZERN IN SCHRITT 2 ANGEZEIGT WIRD**: Der Personalleiter schreibt eine E-Mail-Nachricht, die die Sozialversicherungsnummer eines kürzlich eingestellten Mitarbeiters enthält. Er sendet diese E-Mail-Nachricht an Sherrie in der Personalabteilung.

---

![Screenshot der Beispiel-E-Mail, die nun mit Azure Rights Management geschützt ist, da sie außerhalb der Organisation versendet wird](../media/AzRMS_DLPProtectedEmail_small.png)

**WAS BENUTZERN IN SCHRITT 3 ANGEZEIGT WIRD**: Wenn diese E-Mail-Nachricht an jemanden außerhalb des Unternehmens gesendet oder weitergeleitet wird, wendet die DLP-Regel automatisch Rechteschutz an.

Die E-Mail wird verschlüsselt, wenn sie die Infrastruktur der Organisation verlässt, damit die Sozialversicherungsnummer in der E-Mail-Nachricht während der Übertragung oder im Posteingang des Empfängers nicht gelesen werden kann. Der Empfänger ist nur dann in der Lage, die Nachricht zu lesen, wenn er ein Mitarbeiter von VanArsdel ist.

---

**Weitere Informationen zu diesem Szenario:**

-   Weitere Informationen zur Funktionsweise von Azure RMS mit Exchange Online finden Sie im Abschnitt [Exchange Online und Exchange Server](office-apps-services-support.md#exchange-online-and-exchange-server) unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

-   Eine schrittweise Anleitung zum Konfigurieren von Exchange Online für Azure RMS finden Sie im Abschnitt [Exchange Online: IRM-Konfiguration](../deploy-use/configure-office365.md#exchange-online-irm-configuration) unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

## <a name="automatically-protecting-files-with-sharepoint-online-and-protected-libraries"></a>Automatisches Schützen von Dateien mit SharePoint Online und geschützten Bibliotheken

Dies zeigt, wie leicht Sie Dokumente schützen können, wenn Sie SharePoint Online und geschützte Bibliotheken verwenden.

In diesem Beispiel hat der SharePoint-Administrator für Contoso eine Bibliothek für jede Abteilung erstellt, die zum zentralen Speichern und Auschecken von Dokumenten für die Bearbeitung und Versionskontrolle verwendet wird. Beispielsweise ist eine Bibliothek für den Vertrieb, eine Bibliothek für Marketing, eine Bibliothek für die Personalabteilung usw. vorhanden. Wenn ein neues Dokument hochgeladen oder in einer dieser geschützten Bibliotheken erstellt wird, erbt dieses Dokument den Schutz der Bibliothek (es ist nicht erforderlich, eine Rechterichtlinienvorlage auszuwählen), und dieses Dokument wird automatisch geschützt und bleibt geschützt, auch wenn es aus der SharePoint-Bibliothek verschoben wird.

![Screenshot, der die SharePoint Online-Option zum Aktivieren von IRM zeigt](../media/AzRMS_StoryboardSPO_small1.png)

**WAS ADMINISTRATOREN IN SCHRITT 1 ANGEZEIGT WIRD**: Der Administrator aktiviert Information Rights Management für die SharePoint-Website.

---

![Screenshot, der die SharePoint Online-Option zum Schützen einer Bibliothek mit IRM zeigt](../media/AzRMS_StoryboardSPO_small2.png)

**WAS ADMINISTRATOREN IN SCHRITT 2 ANGEZEIGT WIRD**: Anschließend aktiviert er die Verwaltung von Informationsrechten für eine Bibliothek. Auch wenn weitere Optionen vorhanden sind, ist diese einfache Einstellung häufig die einzige erforderliche.

Wenn Dokumente nun aus dieser Bibliothek heruntergeladen werden, sind sie automatisch durch Rights Management geschützt. Sie erben den Schutz, der für die Bibliothek konfiguriert ist.

---

![Screenshot, der ein Dokument zeigt, das aus einer geschützten SharePoint Online-Bibliothek heruntergeladen wurde und ein Banner mit Informationen, das angibt, dass das Dokument geschützt ist](../media/AzRMS_StoryboardSPO_small3.png)

**WAS BENUTZERN IN SCHRITT 3 ANGEZEIGT WIRD**: Wenn ein Mitarbeiter aus der Vertriebsabteilung diesen Umsatzbericht aus der Bibliothek auscheckt, kann er anhand des oben angezeigten Informationsbanners klar erkennen, dass es sich um ein geschütztes Dokument mit eingeschränktem Zugriff handelt.

Das Dokument bleibt selbst dann geschützt, wenn der Benutzer es umbenennt, an einem anderen Speicherort speichert oder per E-Mail freigibt. Unabhängig davon, welchen Namen die Datei trägt, wo sie gespeichert ist oder ob sie per E-Mail freigegeben wird, kann sie nur von Mitgliedern der Vertriebsabteilung gelesen werden.

---

**Weitere Informationen zu diesem Szenario:**

-   Weitere Informationen zur Funktionsweise von Azure RMS mit SharePoint finden Sie im Abschnitt [SharePoint Online und SharePoint Server](office-apps-services-support.md#sharepoint-online-and-sharepoint-server) unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](applications-support.md).

-   Eine schrittweise Anleitung zum Konfigurieren von SharePoint für Azure RMS finden Sie im Abschnitt [SharePoint Online und OneDrive for Business: IRM-Konfiguration](../deploy-use/configure-office365.md#sharepoint-online-and-onedrive-for-business-irm-configuration) unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

## <a name="users-safely-share-attachments-with-mobile-users"></a>Benutzer geben auf sichere Weise Anlagen für mobile Benutzer frei

Die vorherigen Beispiele haben verdeutlicht, wie Administratoren den Informationsschutz automatisch auf vertrauliche Daten anwenden können. In bestimmten Fällen müssen die Benutzer diesen Schutz jedoch eventuell selbst anwenden. Dies gilt beispielsweise, wenn sie mit Partnern in einer anderen Organisation zusammenarbeiten, wenn sie benutzerdefinierte Berechtigungen oder Einstellungen benötigen, die nicht in Vorlagen definiert sind oder die für Ad-hoc-Situationen vorgesehen sind, die nicht von den vorherigen Beispielen abgedeckt sind. In diesen Fällen können Benutzer die RMS-Vorlagen selbst anwenden oder benutzerdefinierte Berechtigungen konfigurieren.

Dieses Beispiel zeigt, wie Benutzer ein Dokument problemlos für Personen aus einem anderen Unternehmen freigeben können, mit denen sie zusammenarbeiten. Das Dokument wird dabei immer noch geschützt, und der Empfänger ist in der Lage, das Dokument sogar mit einem gängigen mobilen Gerät zu lesen. Dieses Szenario verwendet die RMS-Freigabeanwendung, die automatisch auf Windows-Computern in Ihrer Organisation bereitgestellt werden kann. Sie kann jedoch auch von Benutzern selbst installiert werden.

In diesem Beispiel sendet die Mitarbeiterin Alice von Contoso ein vertrauliches Word-Dokument per E-Mail an Bob, der bei Fabrikam arbeitet. Er liest das Dokument auf seinem iPad. Er könnte es jedoch auch auf ebenso einfache Weise auf einem iPhone, einem Android-Tablet oder -Telefon, einem Macintosh-Computer oder einem Windows Phone oder -Computer lesen.

![Screenshot, der eine Beispiel-E-Mail mit einem Anhang sowie das Dialogfeld „Geschützt freigeben“ der Rights Management-Freigabeanwendung zeigt](../media/AzRMS_StoryboardEmail_small1.png)

**WAS BENUTZERN IN SCHRITT 1 ANGEZEIGT WIRD**: Auf ihrem Windows-PC erstellt Alice eine E-Mail-Standardnachricht und fügt ein Dokument an.

Sie klickt in der Multifunktionsleiste auf **Geschütztes Freigeben** . Dadurch wird das Dialogfeld **Geschütztes Freigeben** aus der RMS-Freigabeanwendung geladen.

Da Bob nach dem Willen von Alice das Dokument nur anzeigen und bearbeiten, nicht jedoch kopieren oder drucken können soll, wählt sie **PRÜFER – Anzeigen und Bearbeiten**aus. Sie möchte auch eine E-Mail erhalten, wenn jemand versucht, das Dokument öffnen, und Sie möchte die Möglichkeit haben, das Dokument später bei Bedarf zu sperren und zu wissen, dass die Sperrung sofort wirksam wird.

---

![Screenshot, der die E-Mail an einen iPad-Benutzer zeigt, die die Nachricht, Anhänge und Anweisungen enthält](../media/AzRMS_StoryboardEmail_small2.png)

**WAS BENUTZERN IN SCHRITT 2 ANGEZEIGT WIRD**: Bob sieht die E-Mail auf seinem iPad.

Er erhält nicht nur die Nachricht und die Anlage von Alice, sondern auch Anweisungen, die er zum Registrieren und Installieren der RMS-Freigabeanwendung auf seinem iPad befolgt.

---

![Screenshot, der zeigt, dass der Benutzer den geschützten Anhang auf dem iPad liest.](../media/AzRMS_StoryboardEmail_small3.png)

**WAS BENUTZERN IN SCHRITT 3 ANGEZEIGT WIRD**: Jetzt kann Bob die Anlage öffnen. Er wird zuerst aufgefordert, sich anzumelden, um zu bestätigen, dass er der beabsichtigte Empfänger ist.

Wenn Bob das Dokument anzeigt, sieht er auch Informationen zum eingeschränkten Zugriff, die ihn informieren, dass er das Dokument anzeigen und bearbeiten, jedoch nicht kopieren oder drucken kann.

---

![Der Bildschirm zeigt eine Beispiel-E-Mail zur Bestätigung für den Sender](../media/AzRMS_StoryboardEmail_small4.png)

**WAS BENUTZERN IN SCHRITT 4 ANGEZEIGT WIRD**: Alice erhält eine E-Mail-Nachricht, die sie informiert, dass Bob das von ihr gesendete Dokument erfolgreich geöffnet hat und wann dies geschehen ist.

Wenn Bob seine E-Mail-Nachricht mit der Anlage weiterleitet oder an einem Speicherort speichert, an dem andere Benutzer darauf zugreifen können, oder die Nachricht im Netzwerk abgefangen wird, sind andere Personen nicht in der Lage, das Dokument zu lesen.

---

**Weitere Informationen zu diesem Szenario:**

- Eine schrittweise Anleitung finden Sie unter [Schützen einer Datei, die per E-Mail freigeben ist](../rms-client/sharing-app-protect-by-email.md) und [Anzeigen und Verwenden von Dateien, die geschützt wurden](../rms-client/sharing-app-view-use-files.md) im [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md).

- Das [Schnellstart-Lernprogramm für Azure Rights Management](../get-started/quick-start-tutorial.md) enthält eine schrittweise Anleitung für dieses Szenario.

## <a name="next-steps"></a>Nächste Schritte

Nachdem Sie nun einige Beispiele für die Möglichkeiten von Azure RMS kennengelernt haben, möchten Sie ggf. mehr über die Funktionsweise erfahren. Technische Informationen zur Funktionsweise von Azure RMS finden Sie unter [Funktionsweise von Azure RMS](how-does-it-work.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]