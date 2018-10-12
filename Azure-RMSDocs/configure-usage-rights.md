---
title: Konfigurieren von Nutzungsrechten für Azure Rights Management – AIP
description: Lernen Sie die spezifischen Berechtigungen kennen, die verwendet werden, wenn Sie Dateien oder E-Mails mithilfe des Azure Rights Management-Diensts von Azure Information Protection schützen.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/18/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 698d92cc38081a8b56f27ede4005cf8b514ed212
ms.sourcegitcommit: a327dc124974c8b489340993d4b2b364ecf5fec5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2018
ms.locfileid: "46289276"
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Konfigurieren von Nutzungsrechten für Azure Rights Management

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Wenn Sie Schutz für Dateien oder E-Mails mithilfe des Azure Rights Management-Diensts von Azure Information Protection festlegen und keine Vorlage verwenden, müssen Sie die Nutzungsrechte selbst konfigurieren. Wenn Sie Vorlagen oder Bezeichnungen für den Azure Rights Management-Schutz konfigurieren, wählen Sie außerdem die Nutzungsrechte, die dann automatisch angewendet werden, wenn die Vorlage oder die Bezeichnung von Benutzern, Administratoren oder konfigurierten Diensten ausgewählt wird. Im Azure-Portal können Sie beispielsweise Rollen auswählen, die eine logische Gruppierung von Nutzungsrechte konfigurieren, oder Sie können die einzelnen Berechtigungen konfigurieren:

Verwenden Sie diesen Artikel, um die gewünschten Nutzungsrechte für die verwendete Anwendung zu konfigurieren und um zu verstehen, wie diese Rechte von den Anwendungen interpretiert werden.

> [!NOTE] 
> Der Vollständigkeit halber enthält dieser Artikel Werte des klassischen Azure-Portals, das am 8. Januar 2018 eingestellt wurde.
>
> Lesen Sie folgenden Artikel, um die Migration leichter durchführen zu können: [Tasks that you used to do with the Azure classic portal (Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben)](migrate-portal.md).

## <a name="usage-rights-and-descriptions"></a>Nutzungsrechte und Beschreibungen
In der folgende Tabelle werden die von Rights Management unterstützten Benutzerrechte aufgezählt und beschrieben und wird beschrieben, wie sie genutzt und interpretiert werden. Sie werden nach ihrem **allgemeinen Namen** aufgelistet, also in der Regel das, was Sie als das Nutzungsrecht sehen, das als die benutzerfreundlichere Version des Einzelwortwerts angezeigt oder referenziert wird. Dieser Wert wird im Code verwendet (der Wert **Richtliniencodierung**). 

Die **API-Konstante oder der API-Wert** ist der SDK-Name für einen MSIPC API-Aufruf, der verwendet wird, wenn Sie eine RMS-fähige Anwendung schreiben, die auf ein Nutzungsrecht überprüft oder einer Richtlinie ein Nutzungsrecht hinzufügt.


|Nutzungsrecht|Beschreibung|Implementierung|
|-------------------------------|---------------------------|-----------------|
|Allgemeiner Name: **Inhalt bearbeiten, Bearbeiten** <br /><br />Richtliniencodierung: **DOCEDIT**|Ermöglicht es dem Benutzer, den Inhalt innerhalb der Anwendung zu ändern, neu anzuordnen, zu formatieren oder zu sortieren. Gewährt nicht das Recht, die bearbeitete Kopie speichern zu können.<br /><br />In Word ist dieses Recht nur bei Office 365 ProPlus mit einer Mindestversion von [1807](https://docs.microsoft.com/officeupdates/monthly-channel-2018#version-1807-july-25) ausreichend, um **Änderungen nachverfolgen** zu aktivieren oder zu deaktivieren oder alle Features zum Nachverfolgen von Änderungen zu verwenden. Ist dies nicht der Fall, ist das Recht **Vollzugriff** erforderlich, um alle Optionen der Änderungsnachverfolgung zu verwenden. |Benutzerdefinierte Office-Rechte: als Teil der Optionen **Ändern** und **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Inhalt bearbeiten**<br /><br />Name im Azure-Portal: **Edit Content, Edit (DOCEDIT)** (Inhalt bearbeiten, Bearbeiten (DOCEDIT))<br /><br />Name in den AD RMS-Vorlagen: **Bearbeiten** <br /><br />API-Konstante oder -Wert: nicht anwendbar|
|Allgemeiner Name: **Speichern** <br /><br />Richtliniencodierung: **EDIT**|Ermöglicht es dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.<br /><br />In Office-Anwendungen ermöglicht dieses Recht dem Benutzer, das Dokument zu ändern und unter einem neuen Namen zu speichern, wenn das ausgewählte Dateiformat nativ Unterstützung für den Rights Management-Schutz bietet. Die Dateiformatbeschränkung stellt dabei sicher, dass der ursprüngliche Schutz nicht aus der Datei entfernt werden kann.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Ändern** und **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Datei speichern**<br /><br />Name im Azure-Portal: **Save (EDIT)** (Speichern (EDIT))<br /><br />Name in den AD RMS-Vorlagen: **Speichern** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_WRITE L"EDIT"`|
|Allgemeiner Name: **Kommentar** <br /><br />Richtliniencodierung: **COMMENT**|Aktiviert die Option, dem Inhalt Anmerkungen oder Kommentare hinzufügen zu können.<br /><br />Dieses Recht ist im SDK und als Ad-hoc-Richtlinie im AzureInformationProtection- und RMS-Schutzmodul für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwarelieferanten implementiert. Es wird allerdings nicht häufig verwendet und wird derzeit nicht von Office-Anwendungen unterstützt.|Benutzerdefinierte Office-Rechte: nicht implementiert <br /><br />Name im klassischen Azure-Portal: nicht implementiert<br /><br />Name im Azure-Portal: nicht implementiert<br /><br />Name in den AD RMS-Vorlagen: nicht implementiert <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_COMMENT L"COMMENT`|
|Allgemeiner Name: **Speichern unter, Exportieren** <br /><br />Richtliniencodierung: **EXPORT**|Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). <br /><br />Für Office-Dokumente und den Azure Information Protection-Client kann die Datei ohne Schutz gespeichert und auch mit neuen Einstellungen und Berechtigungen erneut geschützt werden. Diese zulässigen Aktionen bedeuten, dass ein Benutzer, der über dieses Recht verfügt, eine Azure Information Protection-Bezeichnung aus einem geschützten Dokument oder einer geschützten E-Mail ändern oder entfernen kann. <br /><br />Durch dieses Recht hat der Benutzer auch die Möglichkeit, andere Exportoptionen in Anwendungen auszuführen, beispielsweise **An OneNote senden**.<br /><br /> Hinweis: Wenn dieses Recht nicht gewährt wird, lassen Office-Anwendungen einen Benutzer ein Dokument unter einem neuen Namen speichern, wenn das ausgewählte Dateiformat nativ Unterstützung für den Rights Management-Schutz bietet.|Benutzerdefinierte Office-Rechte: als Teil der Option **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Inhalt exportieren (Speichern unter)** <br /><br />Name im Azure-Portal: **Speichern unter, Exportieren (EXPORT)**<br /><br />Name in den AD RMS-Vorlagen: **Exportieren (Speichern unter)** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Allgemeiner Name: **Weiterleiten** <br /><br />Richtliniencodierung: **FORWARD**|Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in den Zeilen **An** und **Cc** . Dieses Recht wird nicht auf Dokumente sondern nur auf E-Mails angewendet.<br /><br />Gestattet es dem Weiterleiter nicht, anderen Benutzern Berechtigungen als Teil des Weiterleitungsvorgangs zu gewähren. <br /><br />Wenn Sie diese Berechtigung gewähren, gewähren Sie auch die Berechtigung **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name) sowie **Speichern** (allgemeiner Name), um sicherzustellen, dass die geschützte E-Mail nicht als Anhang versendet wird. Legen Sie diese Berechtigungen außerdem fest, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Des Weiteren ist diese Berechtigung für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts aufgrund der Implementierung von [Onboarding-Steuerelementen](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) ausgeschlossen sind.|Benutzerdefinierte Office-Rechte: verweigert, wenn die Standardrichtlinie **Nicht weiterleiten** verwendet wird<br /><br />Name im klassischen Azure-Portal: **Weiterleiten**<br /><br />Name im Azure-Portal: **Weiterleiten (FORWARD)**<br /><br />Name in den AD RMS-Vorlagen: **Weiterleiten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Allgemeiner Name: **Vollzugriff** <br /><br />Richtliniencodierung: **OWNER**|Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.<br /><br />Umfasst die Möglichkeit, den Schutz zu entfernen, und das Dokument erneut zu schützen. <br /><br />Beachten Sie, dass dieses Nutzungsrecht nicht mit [Rights Management-Besitzer](#rights-management-issuer-and-rights-management-owner) übereinstimmt.|Benutzerdefinierte Office-Rechte: als benutzerdefinierte Option **Vollzugriff**<br /><br />Name im klassischen Azure-Portal: **Vollzugriff**<br /><br />Name im Azure-Portal: **Vollzugriff (OWNER)**<br /><br />Name in den AD RMS-Vorlagen: **Vollzugriff** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_ALL L"OWNER"`|
|Allgemeiner Name: **Drucken** <br /><br />Richtliniencodierung: **PRINT**|Aktiviert die Optionen zum Drucken des Inhalts.|Benutzerdefinierte Office-Rechte: als Option **Inhalt drucken** in benutzerdefinierten Berechtigungen Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Drucken**<br /><br />Name im Azure-Portal: **Drucken (PRINT)**<br /><br />Name in den AD RMS-Vorlagen: **Drucken** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_PRINT L"PRINT"`|
|Allgemeiner Name: **Antwort** <br /><br />Richtliniencodierung: **REPLY**|Aktiviert die Option **Antwort** in einem E-Mail-Client, ohne Änderungen in der Zeile **An** oder **Cc** zuzulassen.<br /><br />Wenn Sie diese Berechtigung gewähren, gewähren Sie auch die Berechtigung **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name) sowie **Speichern** (allgemeiner Name), um sicherzustellen, dass die geschützte E-Mail nicht als Anhang versendet wird. Legen Sie diese Berechtigungen außerdem fest, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Des Weiteren ist diese Berechtigung für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts aufgrund der Implementierung von [Onboarding-Steuerelementen](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) ausgeschlossen sind.|Benutzerdefinierte Office-Rechte: nicht anwendbar<br /><br />Name im klassischen Azure-Portal: **Antworten**<br /><br />Name im klassischen Azure-Portal: **Antworten (REPLY)**<br /><br />Name in den AD RMS-Vorlagen: **Antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLY`|
|Allgemeiner Name: **Allen antworten** <br /><br />Richtliniencodierung: **REPLYALL**|Aktiviert die Option **Allen antworten** in einem E-Mail-Client, ermöglicht es dem Benutzer jedoch nicht, der Zeile **An** oder **Cc** Empfänger hinzuzufügen.<br /><br />Wenn Sie diese Berechtigung gewähren, gewähren Sie auch die Berechtigung **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name) sowie **Speichern** (allgemeiner Name), um sicherzustellen, dass die geschützte E-Mail nicht als Anhang versendet wird. Legen Sie diese Berechtigungen außerdem fest, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Des Weiteren ist diese Berechtigung für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts aufgrund der Implementierung von [Onboarding-Steuerelementen](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) ausgeschlossen sind.|Benutzerdefinierte Office-Rechte: nicht anwendbar<br /><br />Name im klassischen Azure-Portal: **Allen antworten**<br /><br />Name im Azure-Portal: **Reply All (REPLY ALL)** (Allen antworten, (REPLY ALL))<br /><br />Name in den AD RMS-Vorlagen: **Allen antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Allgemeiner Name: **Anzeigen, Öffnen, Lesen** <br /><br />Richtliniencodierung: **VIEW**|Ermöglicht es dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.<br /><br /> In Excel reicht dieses Recht nicht aus, um Daten zu sortieren, sodass folgendes Recht erforderlich ist: **Inhalt bearbeiten, Bearbeiten**. Zum Filtern von Daten in Excel, benötigen Sie die folgenden Rechte: **Inhalt bearbeiten, Bearbeiten** und **Kopieren**.|Benutzerdefinierte Office-Rechte: als benutzerdefinierte Option **Lesen**, Option **Anzeigen**<br /><br />Name im klassischen Azure-Portal: **Anzeigen**<br /><br />Name im Azure-Portal: **Anzeigen, Öffnen, Lesen (VIEW)**<br /><br />Name in den AD RMS-Vorlagen: **Lesen** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_READ L"VIEW"`|
|Allgemeiner Name: **Kopieren** <br /><br />Richtliniencodierung: **EXTRACT**|Aktiviert Optionen zum Kopieren von Daten (einschließlich Screenshots) aus dem Dokument in dasselbe oder ein anderes Dokument.<br /><br />In einigen Anwendungen ermöglicht dies auch, dass das gesamte Dokument ungeschützt gespeichert werden kann.<br /><br />In Skype for Business und ähnlichen Anwendungen mit Bildschirmfreigabe muss der Referent über dieses Recht verfügen, um ein geschütztes Dokument erfolgreich präsentieren zu können. Wenn der Referent nicht über dieses Recht verfügt, können die Teilnehmer das Dokument nicht sehen, und stattdessen wird ein schwarzer Bildschirm angezeigt.|Benutzerdefinierte Office-Rechte: als die benutzerdefinierte Richtlinienoption **Benutzern mit Lesezugriff das Kopieren des Inhalts erlauben**<br /><br />Name im klassischen Azure-Portal: **Inhalt kopieren und extrahieren**<br /><br />Name im Azure-Portal: **Kopieren (EXTRACT)**<br /><br />Name in den AD RMS-Vorlagen: **Extrahieren** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Allgemeiner Name: **Rechte anzeigen** <br /><br />Richtliniencodierung: **VIEWRIGHTSDATA**|Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie anzuzeigen.|Benutzerdefinierte Office-Rechte: nicht implementiert<br /><br />Name im klassischen Azure-Portal: **Zugewiesene Rechte anzeigen**<br /><br />Name im Azure-Portal: **Rechte anzeigen (VIEWRIGHTSDATA)**<br /><br />Name in den AD RMS-Vorlagen: **Rechte anzeigen** <br /><br />API-Konstante oder -Wert: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|Allgemeiner Name: **Rechte ändern** <br /><br />Richtliniencodierung: **EDITRIGHTSDATA**|Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie zu ändern. Beinhaltet das Entfernen des Schutzes.|Benutzerdefinierte Office-Rechte: nicht implementiert<br /><br />Name im klassischen Azure-Portal: **Rechte ändern**<br /><br />Name im Azure-Portal: **Rechte bearbeiten (EDITRIGHTSDATA)**<br /><br />Name in den AD RMS-Vorlagen: **Rechte bearbeiten** <br /><br />API-Konstante oder -Wert: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|Allgemeiner Name: **Makros zulassen** <br /><br />Richtliniencodierung: **OBJMODEL**|Aktiviert die Option, Makros oder anderen programmgesteuerten oder remoten Zugriff auf den Inhalt eines Dokuments ausführen zu können.|Benutzerdefinierte Office-Rechte: als benutzerdefinierte Richtlinienoption **Programmgesteuerten Zugriff zulassen** Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Makros zulassen**<br /><br />Name im klassischen Azure-Portal: **Makros zulassen (OBJMODEL)**<br /><br />Name in den AD RMS-Vorlagen: **Makros zulassen** <br /><br />API-Konstante oder -Wert: nicht implementiert|

## <a name="rights-included-in-permissions-levels"></a>In Berechtigungsstufen enthaltene Rechte

In einigen Anwendungen werden Nutzungsrechte in Berechtigungsstufen gruppiert. Dadurch wird es einfacher, Nutzungsrechte auszuwählen, die in der Regel gemeinsam verwendet werden. Diese Berechtigungsstufen lassen das Vergeben von Nutzungsrechten für die Benutzer weniger komplex erscheinen, weil sie unter rollenbasierten Optionen auswählen können.  Beispiele: **Prüfer** und **Mitautor**. Obwohl diese Optionen den Benutzern oft eine Zusammenfassung der Rechte anzeigen, enthalten sie möglicherweise nicht alle in der vorherigen Tabelle aufgeführten Rechte.

In der folgenden Tabelle finden Sie eine Liste dieser Berechtigungsstufen und alle darin enthaltenen Nutzungsrechte. Die Nutzungsrechte sind nach ihrem [allgemeinen Namen](#usage-rights-and-descriptions) aufgelistet.

|Berechtigungsstufe|Applications|Enthaltene Nutzungsrechte|
|---------------------|----------------|---------------------------------|
|Anzeigender Benutzer|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br /> Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Rechte anzeigen; Antworten [[1]](#footnote-1); Allen antworten [[1]](#footnote-1); Makros zulassen [[2]](#footnote-2)<br /><br />Hinweis: Verwenden Sie für E-Mails den Prüfer statt dieser Berechtigungsebene, um sicherzustellen, dass eine Antwort auch als E-Mail und nicht als Anhang verschickt wird. Der Prüfer ist außerdem erforderlich, wenn Sie eine E-Mail an eine andere Organisation versenden, die den Outlook-Client oder Outlook Web App verwendet. Des Weiteren ist diese Berechtigung für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts aufgrund der Implementierung von [Onboarding-Steuerelementen](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) ausgeschlossen sind.|
|Prüfer|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Antworten; Allen Antworten[[3]](#footnote-3); Weiterleiten [[3]](#footnote-3); Makros zulassen [[2]](#footnote-2)|
|Mitautor|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Makros zulassen; Speichern unter, Exportieren [[4]](#footnote-4); Drucken; Antworten [[3]](#footnote-3); Allen Antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3)|
|Mitbesitzer|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Speichern unter, Exportieren; Drucken; Antworten [[3]](#footnote-3); Allen Antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3); Vollzugriff|

----

###### <a name="footnote-1"></a>Fußnote 1

Nicht im Azure-Portal vorhanden.

###### <a name="footnote-2"></a>Fußnote 2

Für den Azure Information Protection-Client für Windows ist dieses Recht derzeit für die Information Protection-Leiste in Office-Apps erforderlich.

###### <a name="footnote-3"></a>Fußnote 3
Gilt nicht für den Azure Information Protection-Client für Windows oder die Rights Management-Freigabeanwendung für Windows.

###### <a name="footnote-4"></a>Fußnote 4
Nicht im Azure-Portal oder Azure Information Protection-Client für Windows enthalten.

## <a name="rights-included-in-the-default-templates"></a>In den Standardvorlagen enthaltene Rechte
In der folgenden Tabelle werden die Nutzungsrechte aufgelistet, die enthalten sind, wenn die Standardvorlagen erstellt werden. Die Nutzungsrechte sind nach ihrem [allgemeinen Namen](#usage-rights-and-descriptions) aufgelistet.

Diese Standardvorlagen werden beim Erwerb Ihres Abonnements erstellt. Die Namen und Nutzungsrechte können im Azure-Portal [geändert](configure-policy-templates.md) werden. 

|Anzeigename der Vorlage|Nutzungsrechte vom 6. Oktober 2017 bis zum aktuellen Datum|Nutzungsrechte vor dem 6. Oktober 2017|
|----------------|--------------------|----------|
|\<*Name der Organisation> – Nur vertrauliche Ansicht* <br /><br />oder<br /><br /> *Streng vertraulich\Alle Mitarbeiter*|Anzeigen, Öffnen, Lesen; Kopieren; Rechte anzeigen; Makros zulassen; Drucken, Weiterleiten; Antworten; Allen antworten; Speichern, Inhalt bearbeiten, Bearbeiten|Anzeigen, Öffnen, Lesen|
|\<*Name der Organisation >– Vertraulich* <br /><br />oder <br /><br />*Vertraulich\Alle Mitarbeiter*|Anzeigen, Öffnen, Lesen; Speichern unter, Exportieren; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Drucken, Weiterleiten; Antworten; Allen antworten; Speichern; Inhalt bearbeiten, Bearbeiten; Vollzugriff|Anzeigen, Öffnen, Lesen; Speichern unter, Exportieren; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Makros zulassen; Weiterleiten; Antworten; Allen antworten|

## <a name="do-not-forward-option-for-emails"></a>Option „Nicht weiterleiten“ für E-Mails

Exchange-Clients und -Dienste (z.B. der Outlook-Client, die Outlook Web Access-App und Exchange-Regeln zum E-Mail-Fluss) haben eine zusätzliche Option zur Verwaltung von Informationsrechten für E-Mails: **Nicht weiterleiten**. 

Obwohl diese Option für Benutzer (und Exchange-Administratoren) wie eine Rights Management-Standardvorlage angezeigt wird, die ausgewählt werden kann, handelt es sich bei **Nicht weiterleiten** um keine Vorlage. Aus diesem Grund wird sie nicht im Azure-Portal angezeigt, wenn Sie Vorlagen für Azure RMS aufrufen und verwalten. Stattdessen stellt die Option **Nicht weiterleiten** eine Reihe von Berechtigungen dar, die von Benutzern dynamisch auf ihre E-Mail-Empfänger angewendet werden.

Wenn die Option **Nicht weiterleiten** auf eine E-Mail angewendet wird, wird sie verschlüsselt, und Empfänger müssen authentifiziert werden. So können die Empfänger keine E-Mails weiterleiten, drucken oder Teile aus diesen kopieren. Im Outlook-Client ist beispielsweise die Schaltfläche „Weiterleiten“ nicht verfügbar, die Menüoptionen **Speichern unter** und **Drucken** sind nicht verfügbar, und Sie können keine Empfänger in den Feldern **An**, **Cc** und **Bcc** hinzufügen oder ändern.

An eine E-Mail angehängte, ungeschützte [Office-Dokumente](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM) unterliegen automatisch denselben Einschränkungen. Für diese Dokumente gelten folgende Nutzungsrechte: **Inhalt bearbeiten, Bearbeiten**; **Speichern**; **Anzeigen, Öffnen, Lesen** und **Makros zulassen**. Wenn für einen Anhang andere Nutzungsrechte gelten sollen oder es sich um ein Office-Dokument handelt, das diesen geerbten Schutz nicht unterstützt, schützen Sie die Datei, bevor Sie sie an eine E-Mail anhängen. So können Sie die nötigen Nutzungsrechte zuweisen. 

### <a name="difference-between-do-not-forward-and-not-granting-the-forward-usage-right"></a>Unterschied zwischen der Option „Nicht weiterleiten“ und dem Nichtgewähren des Nutzungsrechts „Weiterleiten“

Es besteht ein wichtiger Unterschied zwischen dem Anwenden der Option **Nicht weiterleiten** und dem Anwenden einer Vorlage, die das Nutzungsrecht **Weiterleiten** für eine E-Mail nicht gewährt: Bei der Option **Nicht weiterleiten** wird eine dynamische Liste autorisierter Benutzer verwendet, der die vom Benutzer ausgewählten Empfänger der ursprünglichen E-Mail zugrunde liegen. Für die Berechtigungen in der Vorlage gilt hingegen eine statische Liste autorisierter Benutzer, die zuvor vom Administrator festgelegt wurde. Wie wirkt sich dieser Unterschied aus? Betrachten Sie das folgende Beispiel: 

Ein Benutzer möchte bestimmten Personen in der Marketingabteilung Informationen per E-Mail zusenden, die jedoch nicht für andere Personen zugänglich sein sollen. Sollte er die E-Mail mit einer Vorlage schützen, die die Rechte (Anzeigen, Antworten und Speichern) auf die Marketingabteilung beschränkt?  Oder sollte er die Option **Nicht weiterleiten** auswählen? In beiden Fällen wären die Empfänger nicht in der Lage, die E-Mail weiterzuleiten. 

- Wenn die Vorlage angewendet wird, können die Empfänger die Informationen an andere Personen in der Marketingabteilung weitergeben. Ein Empfänger könnte beispielsweise im Explorer die E-Mail per Drag & Drop in ein freigegebenes Verzeichnis oder an ein USB-Laufwerk verschieben. Nun können alle Mitarbeiter der Marketingabteilung (sowie der Besitzer der E-Mail) mit Zugriff auf diesen Speicherort die Informationen aus der E-Mail einsehen.
 
- Wird hingegen die Option **Nicht weiterleiten** angewendet, können die Empfänger die Informationen nicht an andere Personen in der Marketingabteilung übermitteln, indem Sie sie an einen anderen Speicherort verschieben. In diesem Szenario können nur die ursprünglichen Empfänger (und der E-Mail-Besitzer) die Informationen in der E-Mail einsehen.

> [!NOTE] 
> Verwenden Sie **Nicht weiterleiten**, wenn es wichtig ist, dass nur die vom Absender ausgewählten Empfänger die Informationen in der E-Mail einsehen können. Verwenden Sie eine Vorlage für E-Mail-Nachrichten, um Berechtigungen auf eine zuvor vom Administrator angegebene Gruppe von Personen zu beschränken, und zwar unabhängig von den Empfängern, die der Absender ausgewählt hat.

## <a name="encrypt-only-option-for-emails"></a>Option „Encrypt Only“ (Nur verschlüsseln) für E-Mails

Wenn für Exchange Online die neuen Funktionen für Office 365-Nachrichtenverschlüsselung verwendet werden, wird die E-Mail-Option **Encrypt Only** (Nur verschlüsseln) verfügbar.

Diese Option steht Mandanten zur Verfügung, die Exchange Online verwenden. Sie kann in Outlook im Web als weitere Option zum Schutz der Rechte für eine E-Mail-Flussregel und in Outlook ausgewählt werden, wenn Sie Office 365 ProPlus Version [1804](/officeupdates/monthly-channel-2018#outlook-feature-updates-4) oder höher nutzen. Weitere Informationen finden Sie in der folgenden Ankündigung zum Blogbeitrag des Office-Teams: [Encrypt only rolling out in Office 365 Message Encryption (Einführung von „Nur verschlüsseln“ in der Office 365-Nachrichtenverschlüsselung)](https://aka.ms/omefeb2018).

Wenn diese Option aktiviert ist, wird die E-Mail verschlüsselt, und Empfänger müssen authentifiziert werden. Anschließend verfügen die Empfänger über alle Nutzungsrechte außer **Speichern unter, Exportieren** und **Vollzugriff**. Durch diese Kombination von Nutzungsrechten gilt für Empfänger als einzige Einschränkung, dass sie den Schutz nicht entfernen können. Sie können eine E-Mail aber kopieren, ausdrucken und weiterleiten. 

Ebenso übernehmen ungeschützte [Office-Dokumente](https://support.office.com/article/bb643d33-4a3f-4ac7-9770-fd50d95f58dc#FileTypesforIRM), die an die E-Mail angehängt sind, standardmäßig die gleichen Berechtigungen. Diese Dokumente sind automatisch geschützt, und sie können von den Empfängern nach dem Herunterladen aus Office-Anwendungen gespeichert, bearbeitet, kopiert und ausgedruckt werden. Wenn ein Empfänger ein Dokument speichert, hat er die Möglichkeit, ihm einen neuen Namen zu geben und sogar ein anderes Format zu verwenden. Zur Auswahl stehen jedoch nur Dateiformate, die den Schutz unterstützten. So ist sichergestellt, dass dieser nicht durch Speichern umgangen wird. Wenn für einen Anhang andere Nutzungsrechte gelten sollen oder es sich um ein Office-Dokument handelt, das diesen geerbten Schutz nicht unterstützt, schützen Sie die Datei, bevor Sie sie an eine E-Mail anhängen. So können Sie die nötigen Nutzungsrechte zuweisen.

Alternativ können Sie die Vererbung des Schutzes von Dokumenten ändern, indem Sie einen der folgenden Konfigurationsparameter verwenden, die Sie mit dem [Exchange Online PowerShell](/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps)-Befehl **Set-IRMConfiguration** festgelegt haben. Verwenden Sie diese Optionen, wenn Sie den ursprünglichen Schutz für das Dokument nach der Authentifizierung des Benutzers nicht beibehalten müssen:

- So entfernen Sie den Schutz eines Dokuments für alle Empfänger: `Set-IRMConfiguration -DecryptAttachmentForEncryptOnly $true`. Wenn diese Empfänger die E-Mail-Nachricht öffnen, wird das Dokument nicht geschützt.

- So entfernen Sie den Schutz eines Dokuments nur für Empfänger, die das Dokument in ihrem Browser anzeigen (in der Regel, weil es an eine Adresse eines Anbieters wie Gmail gesendet wurde): `Set-IRMConfiguration -DecryptAttachmentFromPortal $true`. Wenn diese Empfänger das Dokument herunterladen, wird der Schutz entfernt.

Weitere Informationen zum Entfernen des Schutzes für die Empfänger, die das Dokument in ihrem Browser anzeigen, finden Sie im Office-Blogbeitrag [Admin control for attachments now available in Office 365 Message Encryption (Administratorsteuerung für Anlagen ist nun in der Office 365-Nachrichtenverschlüsselung verfügbar)](https://techcommunity.microsoft.com/t5/Security-Privacy-and-Compliance/Admin-control-for-attachments-now-available-in-Office-365/ba-p/204007). Wenn der ursprüngliche Schutz eines angefügten Dokuments beibehalten werden soll, finden Sie weitere Informationen unter [Sicheres Zusammenarbeiten an Dokumenten mithilfe von Azure Information Protection](secure-collaboration-documents.md).

## <a name="rights-management-issuer-and-rights-management-owner"></a>Rights Management-Aussteller und Rights Management-Besitzer

Wenn ein Dokument oder eine E-Mail durch den Azure Rights Management-Dienst geschützt ist, wird das Konto, dass diesen Inhalt schützt, automatisch der Rights Management-Aussteller für diesen Inhalt. Dieses Konto ist unter [usage logs](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs) (Nutzungsprotokolle) als **Aussteller** protokolliert. 

Der Rights Management-Aussteller verfügt immer über das Nutzungsrecht „Vollzugriff“ für das Dokument oder die E-Mail. Zusätzlich hat er auch folgende Berechtigungen:

- Wenn die Schutzeinstellungen ein Ablaufdatum enthalten, kann der Rights Management-Aussteller das Dokument bzw. die E-Mail auch nach Ablauf dieses Datums öffnen und bearbeiten.

- Der Rights Management-Aussteller kann immer offline auf das Dokument oder die E-Mail zugreifen.

- Der Rights Management-Aussteller kann ein Dokument auch dann noch öffnen, wenn es gesperrt wurde. 

Standardmäßig ist dieses Konto auch der **Rights Management-Besitzer** für diesen Inhalt; dies tritt ein, wenn der Benutzer, der das Dokument oder die E-Mail erstellt hat, den Schutz initiiert. Es gibt jedoch auch einige Szenarios, in denen ein Administrator oder ein Dienst Inhalt im Namen eines Benutzers schützen kann. Beispiel:

- Ein Administrator führt einen Massenschutzvorgang für Dateien in einer Dateifreigabe durch: Das Administratorkonto in Azure AD schützt die Dokumente für die Benutzer.

- Der Rights Management-Connector schützt Office-Dokumente in einem Windows Server-Ordner: Das Dienstprinzipalkonto in Azure AD, das für den RMS-Connector erstellt wurde, schützt die Dokumente für die Benutzer.

In diesen Szenarios kann der Rights Management-Aussteller den Rights Management-Besitzer mithilfe der Azure Information Protection SDKs oder PowerShell einem anderen Konto zuweisen. Wenn Sie beispielsweise das [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile) PowerShell-Cmdlet mit dem Azure Information Protection-Client verwenden, können Sie den Parameter **OwnerEmail** angeben, um den Rights Management-Besitzer einem anderen Konto zuzuweisen. 

Wenn der Rights Management-Aussteller im Namen von Benutzern schützt, stellt das Zuweisen des Rights Management-Besitzers sicher, dass das ursprüngliche Dokument oder die ursprüngliche E-Mail über die gleiche Kontrollebene für ihren geschützten Inhalt verfügen, als hätten sie den Schutz selbst initiiert. 

Der Benutzer, der das Dokument erstellt hat, kann dieses z.B. drucken, obwohl dieses mit einer Vorlage geschützt ist, die keine Druckberechtigung enthält. Der gleiche Benutzer hat immer Zugriff auf sein Dokument, unabhängig von der Offlineeinstellung und dem Ablaufdatum, die möglicherweise für die Vorlage konfiguriert wurden. Aufgrund des Nutzungsrechts „Vollzugriff“ kann dieser Benutzer außerdem das Dokument erneut schützen, um weiteren Benutzern Zugriff zu gewähren. Dadurch wird dieser Benutzer gleichzeitig zum Rights Management-Aussteller und -Besitzer und kann außerdem sogar den Schutz aufheben. Aber nur der Rights Management-Aussteller kann ein Dokument nachverfolgen und sperren.

Der Rights Management-Besitzer eines Dokuments oder einer E-Mail ist als **owner-email**-Feld in den [Nutzungsprotokollen](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs) protokolliert.

Beachten Sie, dass der Rights Management-Besitzer vom Dateisystembesitzer von Windows unabhängig ist. Häufig stimmen sie überein, können aber auch unterschiedlich sein, auch wenn Sie weder die SDKs noch PowerShell verwenden.

## <a name="rights-management-use-license"></a>Rights Management-Nutzungslizenz

Wenn ein Benutzer ein Dokument oder eine E-Mail öffnet, die von Azure Rights Management geschützt wird, erhält der Benutzer eine Rights Management-Nutzungslizenz für diesen Inhalt. Diese Nutzungslizenz ist ein Zertifikat, das die Nutzungsrechte des Benutzers für das Dokument oder die E-Mail-Nachricht und den Verschlüsselungsschlüssel enthält, der zum Verschlüsseln des Inhalts verwendet wurde. Die Nutzungslizenz enthält auch ein Ablaufdatum, falls dies festgelegt wurde, sowie Angaben darüber, wie lange diese gültig ist.

Ein Benutzer muss zum Öffnen des Inhalts zusätzlich zu einer gültigen Nutzungslizenz über ein Rechtekontozertifikat (RAC) verfügen. Dieses Zertifikat wird erteilt, wenn die [Benutzerumgebung](how-does-it-work.md#initializing-the-user-environment) initialisiert wird, und es wird anschließend alle 31 Tage erneuert.

Für die Dauer der Nutzungslizenz wird der Benutzer für den Inhalt nicht erneut authentifiziert oder autorisiert. Dadurch kann der Benutzer das geschützte Dokument oder die geschützte E-Mail weiterhin ohne Internetverbindung öffnen. Wenn die Gültigkeitsdauer der Nutzungslizenz abläuft, muss der Benutzer beim nächsten Zugriff auf das geschützte Dokument oder die geschützte E-Mail erneut authentifiziert und autorisiert werden. 

Wenn Dokumente und E-Mail-Nachrichten durch eine Bezeichnung oder eine Vorlage geschützt sind, die die Schutzeinstellungen definieren, können Sie diese Einstellungen in Ihrer Bezeichnung oder Vorlage ändern, ohne den Inhalt erneut schützen zu müssen. Wenn der Benutzer bereits auf den Inhalt zugegriffen hat, werden die Änderungen wirksam, nachdem dessen Nutzungslizenz abgelaufen ist. Wenn der Benutzer jedoch benutzerdefinierte Berechtigungen anwendet (auch als Ad-hoc-Richtlinie für Rechte bekannt) und diese Berechtigungen geändert werden müssen, nachdem das Dokument oder die E-Mail geschützt wurden, muss der Inhalt erneut mit den neuen Berechtigungen geschützt werden. Benutzerdefinierte Berechtigungen für E-Mail-Nachrichten werden über die Option „Nicht weiterleiten“ implementiert.

Der Standardwert für die Gültigkeitsdauer der Nutzungslizenz beträgt für einen Mandanten 30 Tage, und Sie können diesen Wert mithilfe des PowerShell-Cmdlets [Set-AadrmMaxUseLicenseValidityTime](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime) konfigurieren. Sie können eine restriktivere Einstellung konfigurieren, wenn der Schutz durch eine Bezeichnung oder eine Vorlage angewendet wird:

- Wenn Sie eine Bezeichnung oder eine Vorlage im Azure-Portal konfigurieren, erhält die Gültigkeitsdauer der Nutzungslizenz ihren Wert aus der Einstellung **Offlinezugriff zulassen**. 
    
    Weitere Informationen und Anleitungen zum Konfigurieren dieser Einstellung im Azure-Portal finden Sie in der Tabelle [Informationen zu Schutzeinstellungen](configure-policy-protection.md#information-about-the-protection-settings) der Anleitung zum Konfigurieren einer Bezeichnung für Azure Rights Management.

- Wenn Sie eine Vorlage mithilfe von PowerShell konfigurieren, erhält die Gültigkeitsdauer der Nutzungslizenz ihren Wert aus dem Parameter *LicenseValidityDuration* in den Cmdlets [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) und [Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate).
    
    Weitere Informationen und Anleitungen zum Konfigurieren dieser Einstellung mithilfe von PowerShell finden Sie in der Hilfe für jedes Cmdlet.

## <a name="see-also"></a>Weitere Informationen
[Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md)

[Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder die Datenwiederherstellung](configure-super-users.md)
