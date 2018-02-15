---
title: "Konfigurieren von Nutzungsrechten für Azure Rights Management – AIP"
description: "Lernen Sie die speziellen Berechtigungen kennen, die verwendet werden, wenn Sie Dateien oder E-Mails mithilfe des Azure Rights Management-Diensts von Azure Information Protection aus schützen, und identifizieren Sie sie."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 01/29/2018
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: ceada043abfa1bee18c6407b3804815d95e89453
ms.sourcegitcommit: 972acdb468ac32a28e3e24c90694aff4b75206fc
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/29/2018
---
# <a name="configuring-usage-rights-for-azure-rights-management"></a>Konfigurieren von Nutzungsrechten für Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Wenn Sie Schutz für Dateien oder E-Mails mithilfe des Azure Rights Management-Diensts von Azure Information Protection festlegen, und Sie keine Vorlage verwenden, müssen Sie die Nutzungsrechte selbst konfigurieren. Wenn Sie Vorlagen oder Bezeichnungen für Azure Rights Management-Schutz konfigurieren, wählen Sie außerdem die Nutzungsrechte, die dann automatisch angewendet werden, wenn die Vorlage oder Bezeichnung von Benutzern, Administratoren oder konfigurierten Diensten ausgewählt wird. Sie können z.B. im Azure-Portal Rollen auswählen, die eine logische Gruppierung von Nutzungsrechten konfigurieren, oder Sie können die einzelnen Berechtigungen konfigurieren.

Verwenden Sie diesen Artikel zum Konfigurieren der Nutzungsrechte, die Sie für die Anwendung wünschen, die Sie verwenden, und um zu verstehen, wie diese Rechte von Anwendungen interpretiert werden.

> [!NOTE] 
> Aus Gründen der Vollständigkeit enthält der Artikel Werte aus dem klassischen Azure-Portal, das am 8. Januar 2018 außer Kraft gesetzt wurde.
>
> Wie Sie zum neuen Portal migrieren, erfahren Sie unter [Aufgaben, die Sie bisher über das klassische Azure-Portal ausgeführt haben](migrate-portal.md).

## <a name="usage-rights-and-descriptions"></a>Nutzungsrechte und Beschreibungen
In der folgenden Tabelle sind die Nutzungsrechte aufgelistet und beschrieben, die Rights Management unterstützt, und wie sie verwendet und interpretiert werden. Sie sind mit ihrem **allgemeinen Namen** aufgelistet, wie die Nutzungsrechte in der Regel angezeigt werden, bzw. über den auf sie verwiesen wird, als benutzerfreundlichere Version des Einzelwortwerts, der im Code verwendet wird (der **Richtliniencodierungswert**). 

Die **API-Konstante oder der API-Wert** ist der SDK-Name für einen MSIPC API-Aufruf, der verwendet wird, wenn Sie eine RMS-fähige Anwendung schreiben, die überprüft, ob ein Nutzungsrecht vorhanden ist, oder einer Richtlinie ein Nutzungsrecht hinzufügt.


|Nutzungsrecht|Description|Implementierung|
|-------------------------------|---------------------------|-----------------|
|Allgemeiner Name: **Inhalt bearbeiten, Bearbeiten** <br /><br />Richtliniencodierung: **DOCEDIT**|Ermöglicht dem Benutzer, den Inhalt in der Anwendung zu ändern, neu anzuordnen, zu formatieren oder filtern. Gewährt nicht das Recht, die bearbeitete Kopie zu speichern.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Änderung** und **Vollzugriff**. <br /><br />Name im klassischen Azure-Portal: **Inhalt bearbeiten**<br /><br />Name im Azure-Portal: **Inhalt bearbeiten, Bearbeiten (DOCEDIT)**<br /><br />Name in AD RMS-Vorlagen: **Bearbeiten** <br /><br />API-Konstante oder -Wert: nicht zutreffend.|
|Allgemeiner Name: **Speichern** <br /><br />Richtliniencodierung: **EDIT**|Ermöglicht dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.<br /><br />In Office-Anwendungen ermöglicht dieses Recht dem Benutzer auch, das Dokument zu ändern.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Änderung** und **Vollzugriff**. <br /><br />Name im klassischen Azure-Portal: **Datei speichern**<br /><br />Name im Azure-Portal: **Speichern (EDIT)**<br /><br />Name in AD RMS-Vorlagen: **Speichern** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_WRITE L"EDIT"`|
|Allgemeiner Name: **Kommentar** <br /><br />Richtliniencodierung: **COMMENT**|Ermöglicht der Option, dem Inhalt Anmerkungen oder Kommentare hinzuzufügen.<br /><br />Dieses Recht ist im SDK verfügbar, als Ad-hoc-Richtlinie in AzureInformationProtection und dem RMS-Schutz-Modul für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwareherstellern implementiert. Es wird allerdings nicht häufig verwendet und derzeit nicht von Office-Anwendungen unterstützt.|Benutzerdefinierte Office-Rechte: nicht implementiert. <br /><br />Name im klassischen Azure-Portal: nicht implementiert.<br /><br />Name im Azure-Portal: nicht implementiert.<br /><br />Name in AD RMS-Vorlagen: nicht implementiert. <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_COMMENT L"COMMENT`|
|Allgemeiner Name: **Speichern unter, Exportieren** <br /><br />Richtliniencodierung: **EXPORT**|Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). Für Office-Dokumente und den Azure Information Protection-Client kann die Datei ohne Schutz gespeichert werden.<br /><br />Dieses Recht ermöglicht dem Benutzer auch, andere Exportoptionen in Anwendungen auszuführen, z.B. **An OneNote senden**.<br /><br /> Hinweis: Wenn dieses Recht nicht erteilt wird, können Benutzer in Office-Anwendungen Dokumente unter einem neuen Namen speichern, wenn das ausgewählte Dateiformat nativ Rights Management-Schutz unterstützt.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Änderung** und **Vollzugriff**. <br /><br />Name im klassischen Azure-Portal: **Inhalt exportieren (Speichern unter)** <br /><br />Name im Azure-Portal: **Speichern unter, Exportieren (EXPORT)**<br /><br />Name in AD RMS-Vorlagen: **Exportieren (Speichern unter)** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Allgemeiner Name: **Weiterleiten** <br /><br />Richtliniencodierung: **FORWARD**|Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in der **An**- und **Cc**-Zeile. Dieses Recht wird nicht auf Dokumente angewendet, sondern nur auf E-Mail-Nachrichten.<br /><br />Erlaubt der Weiterleitung nicht, als Teil des Weiterleitungsvorgangs anderen Benutzern Berechtigungen zu gewähren. <br /><br />Wenn Sie dieses Recht gewähren, gewähren Sie auch das Recht **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name), um sicherzustellen, dass die ursprüngliche E-Mail Teil der weitergeleiteten E-Mail-Nachricht und keine Anlage ist. Dieses Recht ist auch erforderlich, wenn Sie eine E-Mail an eine andere Organisation senden, die den Outlook-Client oder die Outlook-Web-App verwendet. Es ist ebenfalls für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts ausgenommen sind, weil Sie [Onboardingsteuerelemente](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) implementiert haben.|Benutzerdefinierte Office-Rechte: Bei Verwendung der Standardrichtlinie **Nicht weiterleiten** verweigert.<br /><br />Name im klassischen Azure-Portal: **Weiterleiten**<br /><br />Name im Azure-Portal: **Weiterleiten (FORWARD)**<br /><br />Name in AD RMS-Vorlagen: **Weiterleiten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Allgemeiner Name: **Vollzugriff** <br /><br />Richtliniencodierung: **OWNER**|Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.<br /><br />Bietet die Möglichkeit zum Entfernen des Schutzes und erneuten Schützen eines Dokuments. <br /><br />Beachten Sie, dass dieses Nutzungsrecht nicht mit dem des [Rights Management-Besitzers](#rights-management-issuer-and-rights-management-owner) identisch ist.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Option **Vollzugriff**.<br /><br />Name im klassischen Azure-Portal: **Vollzugriff**<br /><br />Name im Azure-Portal: **Vollzugriff (OWNER)**<br /><br />Name in AD RMS-Vorlagen: **Vollzugriff** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_ALL L"OWNER"`|
|Allgemeiner Name: **Drucken** <br /><br />Richtliniencodierung: **PRINT**|Aktiviert die Optionen zum Drucken des Inhalts.|Benutzerdefinierte Office-Rechte: wie die Option **Inhalt drucken** in benutzerdefinierten Berechtigungen. Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Drucken**<br /><br />Name im Azure-Portal: **Drucken (PRINT)**<br /><br />Name in AD RMS-Vorlagen: **Drucken** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_PRINT L"PRINT"`|
|Allgemeiner Name: **Antworten** <br /><br />Richtliniencodierung: **REPLY**|Aktiviert die **Antworten**-Option in einem E-Mail-Client, ohne Änderungen in der **An**- oder **Cc**-Zeile zuzulassen.<br /><br />Wenn Sie dieses Recht gewähren, gewähren Sie auch das Recht **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name), um sicherzustellen, dass die ursprüngliche E-Mail Teil der weitergeleiteten E-Mail-Nachricht und keine Anlage ist. Dieses Recht ist auch erforderlich, wenn Sie eine E-Mail an eine andere Organisation senden, die den Outlook-Client oder die Outlook-Web-App verwendet. Es ist ebenfalls für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts ausgenommen sind, weil Sie [Onboardingsteuerelemente](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) implementiert haben.|Benutzerdefinierte Office-Rechte: nicht zutreffend.<br /><br />Name im klassischen Azure-Portal: **Antworten**<br /><br />Name im klassischen Azure-Portal: **Antworten (REPLY)**<br /><br />Name in AD RMS-Vorlagen: **Antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLY`|
|Allgemeiner Name: **Allen Antworten** <br /><br />Richtliniencodierung: **REPLYALL**|Aktiviert die **Allen Antworten**-Option in einem E-Mail-Client, erlaubt dem Benutzer jedoch nicht, in der **An**- oder **Cc**-Zeile Empfänger hinzuzufügen.<br /><br />Wenn Sie dieses Recht gewähren, gewähren Sie auch das Recht **Inhalt bearbeiten, Bearbeiten** (allgemeiner Name), um sicherzustellen, dass die ursprüngliche E-Mail Teil der weitergeleiteten E-Mail-Nachricht und keine Anlage ist. Dieses Recht ist auch erforderlich, wenn Sie eine E-Mail an eine andere Organisation senden, die den Outlook-Client oder die Outlook-Web-App verwendet. Es ist ebenfalls für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts ausgenommen sind, weil Sie [Onboardingsteuerelemente](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) implementiert haben.|Benutzerdefinierte Office-Rechte: nicht zutreffend.<br /><br />Name im klassischen Azure-Portal: **Allen antworten**<br /><br />Name im Azure-Portal: **Allen antworten (REPLY ALL)**<br /><br />Name in AD RMS-Vorlagen: **Allen antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Allgemeiner Name: **Anzeigen, Öffnen, Lesen** <br /><br />Richtliniencodierung: **VIEW**|Ermöglicht dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Richtlinie **Lesen**, Option **Anzeigen**.<br /><br />Name im klassischen Azure-Portal: **Anzeigen**<br /><br />Name im Azure-Portal: **Anzeigen, Öffnen, Lesen (VIEW)**<br /><br />Name in AD RMS-Vorlagen: **Allen antworten** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_READ L"VIEW"`|
|Allgemeiner Name: **Kopieren** <br /><br />Richtliniencodierung: **EXTRACT**|Aktiviert Optionen zum Kopieren von Daten (einschließlich Screenshots) aus dem Dokument in dasselbe oder ein anderes Dokument.<br /><br />In einigen Anwendungen wird auch das Speichern des gesamten Dokuments in ungeschützter Form ermöglicht.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Richtlinienoption **Benutzern mit Lesezugriff das Kopieren des Inhalts erlauben**.<br /><br />Name im klassischen Azure-Portal: **Inhalt kopieren und extrahieren**<br /><br />Name im Azure-Portal: **Kopieren (EXTRACT)**<br /><br />Name in AD RMS-Vorlagen: **Extrahieren** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Allgemeiner Name: **Rechte anzeigen** <br /><br />Richtliniencodierung: **VIEWRIGHTSDATA**|Ermöglicht dem Benutzer, die Richtlinie anzuzeigen, die auf das Dokument angewendet wird.|Benutzerdefinierte Office-Rechte: nicht implementiert.<br /><br />Name im klassischen Azure-Portal: **Zugewiesene Rechte anzeigen**<br /><br />Name im Azure-Portal: **Rechte anzeigen (VIEWRIGHTSDATA)**.<br /><br />Name in AD RMS-Vorlagen: **Rechte anzeigen** <br /><br />API-Konstante oder -Wert: `IPC_READ_RIGHTS L"VIEWRIGHTSDATA"`|
|Allgemeiner Name: **Rechte ändern** <br /><br />Richtliniencodierung: **EDITRIGHTSDATA**|Ermöglicht dem Benutzer, die Richtlinie zu ändern, die auf das Dokument angewendet wird. Beinhaltet, das Entfernen des Schutzes einzubeziehen.|Benutzerdefinierte Office-Rechte: nicht implementiert.<br /><br />Name im klassischen Azure-Portal: **Rechte ändern**<br /><br />Name im Azure-Portal: **Rechte bearbeiten (EDITRIGHTSDATA)**.<br /><br />Name in AD RMS-Vorlagen: **Rechte bearbeiten** <br /><br />API-Konstante oder -Wert: `PC_WRITE_RIGHTS L"EDITRIGHTSDATA"`|
|Allgemeiner Name: **Makros zulassen** <br /><br />Richtliniencodierung: **OBJMODEL**|Aktiviert die Option zum Ausführen von Makros oder anderem programmgesteuertem oder Remotezugriff auf den Inhalt in einem Dokument.|Benutzerdefinierte Office-Rechte: wie die benutzerdefinierte Richtlinienoption **Programmgesteuerten Zugriff zulassen**. Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Makros zulassen**<br /><br />Name im Azure-Portal: **Makros zulassen (OBJMODEL)**<br /><br />Name in AD RMS-Vorlagen: **Makros zulassen** <br /><br />API-Konstante oder -Wert: nicht implementiert.|

## <a name="rights-included-in-permissions-levels"></a>In Berechtigungsstufen enthaltene Rechte

Einige Anwendungen gruppieren Nutzungsrechte in Berechtigungsstufen, um die Auswahl von Nutzungsrechten zu vereinfachen, die in der Regel zusammen verwendet werden. Diese Berechtigungsstufen unterstützen das Abstrahieren eines Komplexitätsniveaus vor den Benutzern, damit sie rollenbasierte Optionen auswählen können.  Beispiel: **Prüfer** und **Mitautor**. Obwohl diese Optionen Benutzern häufig eine Zusammenfassung der Rechte anzeigen, enthalten sie möglicherweise nicht jede Berechtigung, die in der vorherigen Tabelle aufgelistet wird.

In der folgenden Tabelle finden Sie eine Liste dieser Berechtigungsstufen und eine vollständige Liste der Nutzungsrechte, die sie enthalten. Die Nutzungsrechte sind nach ihren [allgemeinen Namen](#usage-rights-and-descriptions) aufgelistet.

|Berechtigungsstufe|Anwendungen|Enthaltene Nutzungsrechte|
|---------------------|----------------|---------------------------------|
|Viewer|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br /> Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Rechte anzeigen; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Makros zulassen [[2]](#footnote-2)<br /><br />Hinweis: Verwenden Sie für E-Mails „Prüfer“ statt dieser Berechtigungsstufe, um sicherzustellen, dass eine E-Mail-Antwort als E-Mail-Nachricht und nicht als Anlage empfangen wird. „Prüfer“ ist auch erforderlich, wenn Sie eine E-Mail an eine andere Organisation senden, die den Outlook-Client oder die Outlook-Web-App verwendet. Es ist ebenfalls für Benutzer in Ihrer Organisation erforderlich, die von der Verwendung des Azure Rights Management-Diensts ausgenommen sind, weil Sie [Onboardingsteuerelemente](/powershell/module/aadrm/set-aadrmonboardingcontrolpolicy) implementiert haben.|
|Prüfer|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Antworten: Allen antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3); Makros zulassen [[2]](#footnote-2)|
|Mitautor|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Makros zulassen; Speichern unter, Exportieren [[4]](#footnote-4); Drucken; Antworten [[3]](#footnote-3); Allen antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3)|
|Mitbesitzer|Klassisches Azure-Portal <br /><br />Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Speichern unter, Exportieren; Drucken; Antworten [[3]](#footnote-3); Allen antworten [[3]](#footnote-3); Weiterleiten [[3]](#footnote-3); Vollzugriff|

----

###### <a name="footnote-1"></a>Fußnote 1

Im Azure-Portal nicht enthalten.

###### <a name="footnote-2"></a>Fußnote 2

Für den Azure Information Protection-Client für Windows ist dieses Recht derzeit für die Information Protection-Leiste in Office-Apps erforderlich.

###### <a name="footnote-3"></a>Fußnote 3
Gilt nicht für den Azure Information Protection-Client für Windows oder die Rights Management-Freigabeanwendung für Windows.

###### <a name="footnote-4"></a>Fußnote 4
Nicht im Azure-Portal oder dem Azure Information Protection-Client für Windows enthalten.

## <a name="rights-included-in-the-default-templates"></a>In den Standardvorlagen enthaltene Rechte
Die folgende Tabelle enthält die Nutzungsrechte, die enthalten sind, wenn die Standardvorlagen erstellt werden. Die Nutzungsrechte sind nach ihren [allgemeinen Namen](#usage-rights-and-descriptions) aufgelistet.

Diese Standardvorlagen werden beim Erwerb Ihres Abonnements erstellt, und die Namen und Nutzungsrechte können im Azure-Portal [geändert](configure-policy-templates.md) werden. 

|Anzeigename der Vorlage|Nutzungsrechte vom 6. Oktober 2017 bis zum aktuellen Datum|Nutzungsrechte vor dem 6. Oktober 2017|
|----------------|--------------------|----------|
|\<*Name der Organisation> – nur vertrauliche Ansicht* <br /><br />oder<br /><br /> *Streng vertraulich \ alle Mitarbeiter*|Anzeigen, Öffnen, Lesen; Kopieren; Rechte anzeigen; Makros zulassen; Drucken; Weiterleiten; Antworten; Allen antworten; Speichern; Inhalt bearbeiten, Bearbeiten|Anzeigen, Öffnen, Lesen|
|\<*Name der Organisation> – vertraulich* <br /><br />oder <br /><br />*Vertraulich \ alle Mitarbeiter*|Anzeigen, Öffnen, Lesen; Speichern unter; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Drucken; Weiterleiten; Antworten; Allen antworten; Speichern; Inhalt bearbeiten, Bearbeiten; Vollzugriff|Anzeigen, Öffnen, Lesen; Speichern unter; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Makros zulassen; Weiterleiten; Antworten; Allen antworten|

## <a name="do-not-forward-option-for-emails"></a>„Nicht weiterleiten“-Option für E-Mails

Exchange-Clients und -Dienste (z.B. Outlook-Client, Outlook Web Access-App und Exchange-Transportregeln) haben eine zusätzliche Information Rights-Schutzoption für E-Mails: **Nicht weiterleiten**. 

Obwohl diese Option für Benutzer (und Exchange-Administratoren) so angezeigt wird, als sei sie eine Rights Management-Standardvorlage, die sie auswählen können, ist **Nicht weiterleiten** keine Vorlage. Dies erklärt, warum sie im Azure-Portal nicht angezeigt wird, wenn Sie Vorlagen für Azure Rights Management anzeigen und verwalten. Stattdessen sind die **Nicht weiterleiten**-Optionen eine Reihe von Berechtigungen, die von Benutzern dynamisch auf ihre E-Mail-Empfänger angewendet werden.

Wenn die **Nicht weiterleiten**-Option auf eine E-Mail-Nachricht angewendet wird, können die Empfänger sie weder weiterleiten oder drucken, noch daraus kopieren, Anlagen speichern oder sie unter einem anderen Namen speichern. Beispielsweise ist im Outlook-Client die Schaltfläche „Weiterleiten“ nicht verfügbar, die Menüoptionen **Speichern unter**, **Anlage speichern** und **Drucken** sind nicht verfügbar, und Sie können keine Empfänger in den Feldern **An**, **Cc** oder **Bcc** hinzufügen oder ändern.

Es besteht ein wichtiger Unterschied zwischen dem Anwenden der **Nicht weiterleiten**-Option und dem Anwenden einer Vorlage, die nicht die Berechtigung zum Weiterleiten einer E-Mail-Nachricht gewährt: Die **Nicht weiterleiten**-Option verwendet eine dynamische Liste von autorisierten Benutzern, die auf den vom Benutzer ausgewählten Empfängern der ursprünglichen E-Mail basiert, während den Rechten in der Vorlage eine statische Liste autorisierter Benutzer zugrunde liegt, die der Administrator zuvor angegeben hat. Wo liegt der Unterschied? Ein Beispiel sollte das Verständnis vereinfachen: 

Ein Benutzer möchte per E-Mail einige Informationen an bestimmte Personen in der Marketingabteilung senden, die sonst niemand erfahren soll. Sollte er die E-Mail-Nachricht mit einer Vorlage schützen, die die Rechte (Anzeigen, Antworten und Speichern) auf die Marketingabteilung beschränkt?  Oder sollte er die **Nicht weiterleiten**-Option wählen? Beides würde dazu führen, dass die Empfänger die E-Mail nicht weiterleiten können. 

- Wenn er die Vorlage anwendet, können die Empfänger die Informationen noch für andere in der Marketingabteilung freigeben. Ein Empfänger könnte die E-Mail z.B. im Explorer ziehen und auf einem freigegebenen Speicherort oder einem USB-Laufwerk ablegen. Nun können alle Mitarbeiter der Marketingabteilung, die Zugriff auf diesen Speicherort haben (sowie der Besitzer der E-Mail), die Informationen in der E-Mail anzeigen.
 
- Wenn er die **Nicht weiterleiten**-Option angewendet hat, können die Empfänger die Informationen nicht für andere in der Marketingabteilung freigeben, indem sie die E-Mail an einen anderen Speicherort verschieben. In diesem Szenario können nur die ursprünglichen Empfänger (und der E-Mail-Besitzer) die Informationen in der E-Mail anzeigen.

> [!NOTE] 
> Verwenden Sie **Nicht weiterleiten**, wenn es wichtig ist, dass nur die vom Absender ausgewählten Empfänger die Informationen in der E-Mail einsehen. Verwenden Sie eine Vorlage für E-Mails, um die Rechte auf eine Gruppe von Personen zu beschränken, die der Administrator unabhängig von der Empfängerauswahl des Absenders im Voraus festlegt.

## <a name="rights-management-issuer-and-rights-management-owner"></a>Rights Management-Aussteller und Rights Management-Besitzer

Wenn ein Dokument oder eine E-Mail mithilfe des Azure Rights Management-Diensts geschützt ist, wird das Konto, das diesen Inhalt schützt, automatisch der Rights Management-Aussteller dieses Inhalts. Dieses Konto wird als **issuer**-Feld in den [Verwendungsprotokollen](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs) protokolliert. 

Dem Rights Management-Aussteller wird immer das Nutzungsrecht „Vollzugriff“ für das Dokument oder die E-Mail gewährt, und darüber hinaus:

- Wenn die Schutzeinstellungen ein Ablaufdatum umfassen, kann der Rights Management-Aussteller das Dokument oder die E-Mail nach diesem Datum immer noch öffnen und bearbeiten.

- Der Rights Management-Aussteller kann stets offline auf das Dokument oder die E-Mail zugreifen.

- Der Rights Management-Aussteller kann ein Dokument immer noch öffnen, nachdem es widerrufen wurde. 

Standardmäßig ist dieses Konto auch der **Rights Management-Besitzer** dieses Inhalts, was der Fall ist, wenn ein Benutzer, der das Dokument oder die E-Mail erstellt hat, den Schutz initiiert. Aber es gibt einige Szenarien, in denen ein Administrator oder Dienst Inhalte im Auftrag von Benutzern schützen kann. Zum Beispiel:

- Ein Administrator schützt viele Dateien auf einer Dateifreigabe auf einmal: Das Administratorkonto in Azure AD schützt die Dokumente für die Benutzer.

- Der Rights Management-Connector schützt Office-Dokumente in einem Windows Server-Ordner: Das Dienstprinzipalkonto in Azure AD, das für den RMS-Connector erstellt wird, schützt die Dokumente für die Benutzer.

In diesen Szenarien kann der Rights Management-Aussteller den Rights Management-Besitzer mithilfe der Azure Information Protection-SDKs oder von PowerShell einem anderen Konto zuweisen. Wenn Sie z.B. das [Protect-RMSFile](/powershell/module/azureinformationprotection/protect-rmsfile)-PowerShell-Cmdlet mit dem Azure Information Protection-Client verwenden, können Sie den **OwnerEmail**-Parameter angeben, um den Rights Management-Besitzer einem anderen Konto zuzuweisen. 

Wenn der Rights Management-Aussteller im Auftrag von Benutzern schützt, stellt das Zuweisen des Rights Management-Besitzers sicher, dass der ursprüngliche Dokument- oder E-Mail-Besitzer das gleiche Maß an Kontrolle über seinen geschützten Inhalt hat, als hätte er den Schutz selbst initiiert. 

Beispielsweise kann der Benutzer, der das Dokument erstellt hat, es drucken, obwohl es jetzt mit einer Vorlage geschützt ist, die das Nutzungsrecht „Drucken“ nicht enthält. Derselbe Benutzer kann stets unabhängig von der Einstellung für Offlinezugriff oder Ablaufdatum, die in dieser Vorlage konfiguriert sein könnten, auf sein Dokument zugreifen. Da der Rights Management-Besitzer über das Nutzungsrecht „Vollzugriff“ verfügt, kann dieser Benutzer darüber hinaus sein Dokument auch erneut schützen, um weiteren Benutzern Zugriff zu gewähren (an diesem Punkt wird der Benutzer dann sowohl zum Rights Management-Aussteller als auch Rights Management-Besitzer), und dieser Benutzer kann sogar den Schutz entfernen. Allerdings kann nur der Rights Management-Aussteller ein Dokument nachverfolgen und widerrufen.

Der Rights Management-Besitzer für ein Dokument oder eine E-Mail wird im Feld **owner-email** der [Verwendungsprotokolle](log-analyze-usage.md#how-to-interpret-your-azure-rights-management-usage-logs) protokolliert.

Beachten Sie, dass der Rights Management-Besitzer vom Besitzer des Windows-Dateisystems unabhängig ist. Sie sind häufig identisch, können jedoch unterschiedlich sein, auch wenn Sie nicht die SDKs oder PowerShell verwenden.

## <a name="rights-management-use-license"></a>Rights Management-Nutzungslizenz

Wenn ein Benutzer ein Dokument oder eine E-Mail öffnet, das/die von Azure Rights Management geschützt wurde, erhält der Benutzer eine Rights Management-Nutzungslizenz für diesen Inhalt. Diese Nutzungslizenz ist ein Zertifikat, das die Nutzungsrechte für das Dokument oder die E-Mail-Nachricht und den Verschlüsselungsschlüssel enthält, der zum Verschlüsseln des Inhalts verwendet wurde. Die Lizenz enthält auch ein ggf. festgelegtes Ablaufdatum und die Gültigkeitsdauer der Nutzungslizenz.

Für die Dauer der Nutzungslizenz wird der Benutzer nicht erneut authentifiziert oder autorisiert. Auf diese Weise kann der Benutzer das Öffnen des geschützten Dokuments oder der E-Mail ohne Internetverbindung fortsetzen. Beim nächsten Zugriff des Benutzers auf das geschützte Dokument oder die geschützte E-Mail nach Ablauf der Gültigkeitsdauer der Nutzungslizenz muss der Benutzer erneut authentifiziert und autorisiert werden. 

Wenn Dokumente und E-Mail-Nachrichten mithilfe einer Bezeichnung oder Vorlage geschützt werden, die die Schutzeinstellungen definiert, können Sie diese Einstellungen in Ihrer Bezeichnung oder Vorlage ändern, ohne den Inhalt erneut schützen zu müssen. Wenn der Benutzer bereits auf den Inhalt zugegriffen hat, werden die Änderungen wirksam, wenn seine Nutzungslizenz abgelaufen ist. Wenn Benutzer jedoch benutzerdefinierte Berechtigungen (auch bekannt als Ad-hoc-Rechterichtlinie) anwenden, und diese Berechtigungen geändert werden müssen, nachdem das Dokument oder die E-Mail geschützt worden ist, muss dieser Inhalt erneut mit den neuen Berechtigungen geschützt werden. Benutzerdefinierte Berechtigungen für eine E-Mail-Nachricht werden mit der Option „Nicht weiterleiten“ implementiert.

Die Standardgültigkeitsdauer der Nutzungslizenz für einen Mandanten beträgt 30 Tage, und Sie können diesen Wert mithilfe des PowerShell-Cmdlets [Set-AadrmMaxUseLicenseValidityTime](/powershell/module/aadrm/set-aadrmmaxuselicensevaliditytime) konfigurieren. Sie können mithilfe einer Bezeichnung oder Vorlage eine restriktivere Einstellung dafür konfigurieren, wann Schutz angewendet wird:

- Wenn Sie eine Bezeichnung oder Vorlage im Azure-Portal konfigurieren, wird der Wert für die Gültigkeitsdauer der Nutzungslizenz von der **Einstellung „Offlinezugriff zulassen“** übernommen. 
    
    Weitere Informationen und Anleitungen zum Konfigurieren dieser Einstellung im Azure-Portal finden Sie in der Tabelle in Schritt 9 von [Konfigurieren einer Bezeichnung für Rights Management-Schutz](configure-policy-protection.md).

- Wenn Sie eine Vorlage mithilfe von PowerShell konfigurieren, wird der Wert für die Gültigkeitsdauer der Nutzungslizenz vom *LicenseValidityDuration*-Parameter in den Cmdlets [Set-AadrmTemplateProperty](/powershell/module/aadrm/set-aadrmtemplateproperty) und [ Add-AadrmTemplate](/powershell/module/aadrm/add-aadrmtemplate) übernommen.
    
    Weitere Informationen und Anleitungen zum Konfigurieren dieser Einstellung mithilfe von PowerShell finden Sie in der Hilfe zu dem jeweiligen Cmdlet.


## <a name="see-also"></a>Weitere Informationen finden Sie unter
[Konfigurieren und Verwalten von Vorlagen für Azure Information Protection](configure-policy-templates.md)

[Konfigurieren von Administratoren für Azure Rights Management und Ermittlungsdienste oder Datenwiederherstellung](configure-super-users.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

