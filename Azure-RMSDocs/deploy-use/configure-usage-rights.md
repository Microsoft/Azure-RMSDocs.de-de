---
title: "Konfigurieren von Nutzungsrechten für Azure Rights Management | Azure Information Protection"
description: "Lernen Sie die spezifischen Berechtigungen kennen, die verwendet werden, wenn Sie Dateien oder E-Mails mithilfe des Azure Rights Management-Diensts von Azure Information Protection schützen."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7068e0529409eb783f16bc207a17be27cd5d82a8
ms.openlocfilehash: 8b3926bf9e985eb8954449b0e88d0d953f4fb339


---

# <a name="configuring-usage-rights-for-azure-rights-management"></a>Konfigurieren von Nutzungsrechten für Azure Rights Management

>*Gilt für: Azure Information Protection, Office 365*

Wenn Sie Schutz für Dateien oder E-Mails mithilfe des Azure Rights Management-Diensts von Azure Information Protection festlegen und keine Vorlage verwenden, müssen Sie die Nutzungsrechte selbst konfigurieren. Wenn Sie benutzerdefinierte Vorlagen für Azure Rights Management konfigurieren, wählen Sie außerdem die Nutzungsrechte, die dann automatisch angewendet werden, wenn die Vorlage von Benutzern, Administratoren oder konfigurierten Diensten ausgewählt wird. Im klassischen Azure-Portal können Sie beispielsweise Rollen auswählen, die eine logische Gruppierung von Nutzungsrechten konfigurieren, oder Sie können die einzelnen Berechtigungen konfigurieren:

Verwenden Sie diesen Artikel, um die gewünschten Nutzungsrechte für die verwendete Anwendung zu konfigurieren und um zu verstehen, wie diese Rechte von den Anwendungen interpretiert werden.

## <a name="usage-rights-and-descriptions"></a>Nutzungsrechte und Beschreibungen
In der folgende Tabelle werden die von Rights Management unterstützten Benutzerrechte aufgezählt und beschrieben und wird beschrieben, wie sie genutzt und interpretiert werden. Sie werden nach **Allgemeiner Name** aufgelistet, also in der Regel das, was Sie als das Nutzungsrecht sehen, das als die benutzerfreundlichere Version des Einzelwortwerts angezeigt oder referenziert wird, der im Code verwendet wird (der **Richtliniencodierung**-Wert). Die **API-Konstante oder der API-Wert** ist der SDK-Name für einen MSIPC API-Aufruf, der verwendet wird, wenn Sie eine RMS-fähige Anwendung schreiben, die auf ein Nutzungsrecht überprüft oder einer Richtlinie ein Nutzungsrecht hinzufügt.


|Right|Beschreibung|Implementierung|
|-------------------------------|---------------------------|-----------------|
|Allgemeiner Name: **Inhalt bearbeiten, Bearbeiten** <br /><br />Richtliniencodierung: **DOCEDIT**|Ermöglicht es dem Benutzer, den Inhalt in der Anwendung zu ändern, neu anzuordnen, zu formatieren oder zu filtern. Gewährt nicht das Recht, die bearbeitete Kopie speichern zu können.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Ändern** und **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Inhalt bearbeiten**<br /><br />Name in den AD RMS-Vorlagen: **Bearbeiten** <br /><br />API-Konstante oder -Wert: nicht anwendbar|
|Allgemeiner Name: **Speichern** <br /><br />Richtliniencodierung: **EDIT**|Ermöglicht es dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.<br /><br />In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu ändern.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Ändern** und **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Datei speichern**<br /><br />Name in den AD RMS-Vorlagen: **Speichern** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_WRITE L"EDIT"`|
|Allgemeiner Name: **Kommentar** <br /><br />Richtliniencodierung: **COMMENT**|Aktiviert die Option, dem Inhalt Anmerkungen oder Kommentare hinzufügen zu können.<br /><br />Dieses Recht ist im SDK verfügbar, ist als eine Ad-hoc-Richtlinie im RMS-Schutz-Modul (RMSProtection) für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwarelieferanten implementiert. Es wird allerdings nicht häufig verwendet und wird derzeit nicht von Office-Anwendungen unterstützt.|Benutzerdefinierte Office-Rechte: nicht implementiert <br /><br />Name im klassischen Azure-Portal: nicht implementiert<br /><br />Name in den AD RMS-Vorlagen: nicht implementiert <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_COMMENT L"COMMENT`|
|Allgemeiner Name: **Speichern unter, Exportieren** <br /><br />Richtliniencodierung: **EXPORT**|Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). Für Office-Dokumente und den Azure Information Protection-Client kann die Datei ohne Schutz gespeichert werden.<br /><br />Durch dieses Recht hat der Benutzer auch die Möglichkeit, andere Exportoptionen in Anwendungen auszuführen, beispielsweise **An OneNote senden**.|Benutzerdefinierte Office-Rechte: als Teil der Optionen **Ändern** und **Vollzugriff** <br /><br />Name im klassischen Azure-Portal: **Inhalt exportieren (Speichern unter)**<br /><br />Name in den AD RMS-Vorlagen: **Exportieren (Speichern unter)** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXPORT L"EXPORT"`|
|Allgemeiner Name: **Weiterleiten** <br /><br />Richtliniencodierung: **FORWARD**|Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in den Zeilen **An** und **Cc** . Dieses Recht wird nicht auf Dokumente sondern nur auf E-Mails angewendet.<br /><br />Gestattet es dem Weiterleiter nicht, anderen Benutzern Berechtigungen als Teil des Weiterleitungsvorgangs zu gewähren.|Benutzerdefinierte Office-Rechte: verweigert, wenn die Standardrichtlinie **Nicht weiterleiten** verwendet wird<br /><br />Name im klassischen Azure-Portal: **Weiterleiten**<br /><br />Name in den AD RMS-Vorlagen: **Weiterleiten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_FORWARD L"FORWARD"`|
|Allgemeiner Name: **Vollzugriff** <br /><br />Richtliniencodierung: **OWNER**|Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.<br /><br />Umfasst die Möglichkeit, den Schutz zu entfernen, und das Dokument neu zu schützen.|Benutzerdefinierte Office-Rechte: als benutzerdefinierte Option **Vollzugriff**<br /><br />Name im klassischen Azure-Portal: **Vollzugriff**<br /><br />Name in den AD RMS-Vorlagen: **Vollzugriff** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_ALL L"OWNER"`|
|Allgemeiner Name: **Drucken** <br /><br />Richtliniencodierung: **PRINT**|Aktiviert die Optionen zum Drucken des Inhalts.|Benutzerdefinierte Office-Rechte: als Option **Inhalt drucken** in benutzerdefinierten Berechtigungen Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Drucken**<br /><br />Name in den AD RMS-Vorlagen: **Drucken** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_PRINT L"PRINT"`|
|Allgemeiner Name: **Antwort** <br /><br />Richtliniencodierung: **REPLY**|Aktiviert die Option **Antwort** in einem E-Mail-Client, ohne Änderungen in der Zeile **An** oder **Cc** zuzulassen.|Benutzerdefinierte Office-Rechte: nicht anwendbar<br /><br />Name im klassischen Azure-Portal: **Antworten**<br /><br />Name in den AD RMS-Vorlagen: **Antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLY`|
|Allgemeiner Name: **Allen antworten** <br /><br />Richtliniencodierung: **REPLYALL**|Aktiviert die Option **Allen antworten** in einem E-Mail-Client, ermöglicht es dem Benutzer jedoch nicht, der Zeile **An** oder **Cc** Empfänger hinzuzufügen.|Benutzerdefinierte Office-Rechte: nicht anwendbar<br /><br />Name im klassischen Azure-Portal: **Allen antworten**<br /><br />Name in den AD RMS-Vorlagen: **Allen antworten** <br /><br />API-Konstante oder -Wert: `IPC_EMAIL_REPLYALL L"REPLYALL"`|
|Allgemeiner Name: **Anzeigen, Öffnen, Lesen** <br /><br />Richtliniencodierung: **VIEW**|Ermöglicht es dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.|Benutzerdefinierte Office-Rechte: als benutzerdefinierte Option **Lesen**, Option **Anzeigen**<br /><br />Name im klassischen Azure-Portal: **Anzeigen**<br /><br />Name in den AD RMS-Vorlagen: **Allen antworten** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_READ L"VIEW"`|
|Allgemeiner Name: **Kopieren** <br /><br />Richtliniencodierung: **EXTRACT**|Aktiviert Optionen zum Kopieren von Daten (einschließlich Screenshots) aus dem Dokument in dasselbe oder ein anderes Dokument.<br /><br />In einigen Anwendungen ermöglicht es auch, dass das gesamte Dokument ungeschützt gespeichert werden kann.|Benutzerdefinierte Office-Rechte: als die benutzerdefinierte Richtlinienoption **Benutzern mit Lesezugriff das Kopieren des Inhalts erlauben**<br /><br />Name im klassischen Azure-Portal: **Inhalt kopieren und extrahieren**<br /><br />Name in den AD RMS-Vorlagen: **Extrahieren** <br /><br />API-Konstante oder -Wert: `IPC_GENERIC_EXTRACT L"EXTRACT"`|
|Allgemeiner Name: **Makros zulassen** <br /><br />Richtliniencodierung: **OBJMODEL**|Aktiviert die Option, Makros oder anderen programmgesteuerten oder remoten Zugriff auf den Inhalt eines Dokuments ausführen zu können.|Benutzerdefinierte Office-Rechte: als benutzerdefinierte Richtlinienoption **Programmgesteuerten Zugriff zulassen** Keine Pro-Empfänger-Einstellung.<br /><br />Name im klassischen Azure-Portal: **Makros zulassen**<br /><br />Name in den AD RMS-Vorlagen: **Makros zulassen** <br /><br />API-Konstante oder -Wert: nicht implementiert|



## <a name="rights-included-in-permissions-levels"></a>In Berechtigungsstufen enthaltene Rechte

In einigen Anwendungen werden Nutzungsrechte in Berechtigungsstufen gruppiert. Dadurch wird es einfacher, Nutzungsrechte auszuwählen, die in der Regel gemeinsam verwendet werden. Diese Berechtigungsstufen lassen das Vergeben von Nutzungsrechten für die Benutzer weniger komplex erscheinen, weil sie unter rollenbasierten Optionen auswählen können.  Beispiele: **Prüfer** und **Mitautor**. Obwohl diese Optionen den Benutzern oft eine Zusammenfassung der Rechte anzeigen, enthalten sie möglicherweise nicht alle in der vorherigen Tabelle aufgeführten Rechte.

In der folgenden Tabelle finden Sie eine Liste dieser Berechtigungsstufen und alle darin enthaltenen Rechte.

|Berechtigungsstufe|Anwendungen|Enthaltene Rechte (allgemeiner Name)|
|---------------------|----------------|---------------------------------|
|Anzeigender Benutzer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows (Vorschau)|Anzeigen, Öffnen, Lesen; Antworten; Allen Antworten|
|Prüfer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows (Vorschau)|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Weiterleiten [[1]](#footnote-1)|
|Mitautor|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows (Vorschau)|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Makros zulassen; Speichern unter, Exportieren [[2]](#footnote-2); Drucken; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Weiterleiten [[1]](#footnote-1)|
|Mitbesitzer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows<br /><br />Azure Information Protection-Client für Windows (Vorschau)|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Makros zulassen; Speichern unter, Exportieren; Drucken; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Weiterleiten [[1]](#footnote-1); Vollzugriff|

----

###### <a name="footnote-1"></a>Fußnote 1
Gilt nicht für die Rights Management-Freigabeanwendung für Windows oder den Azure Information Protection-Client für Windows (Vorschau).

###### <a name="footnote-2"></a>Fußnote 2
Nicht im Azure Information Protection-Client für Windows (Vorschau) enthalten. In diesem Client umfasst das Nutzungsrecht zum Exportieren die Möglichkeit zum Aufheben des Schutzes.


## <a name="rights-included-in-the-default-templates"></a>In den Standardvorlagen enthaltene Rechte
In den Standardvorlagen sind folgende Rechte enthalten:

|Anzeigename|Enthaltene Rechte (allgemeiner Name)|
|----------------|---------------------------------|
|&lt;*Name der Organisation*&gt; *– Vertraulich, nur Anzeige*|Anzeigen, Öffnen, Lesen|
|&lt;*Name der Organisation*&gt; *– Vertraulich*|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Makros zulassen; Weiterleiten; Antworten; Allen antworten|

## <a name="do-not-forward-option-for-emails"></a>Option „Nicht weiterleiten“ für E-Mails

Exchange-Clients und -Dienste (z.B. der Outlook-Client, die Outlook Web Access-App und Exchange-Transportregeln) haben eine zusätzliche Option zur Verwaltung von Informationsrechten für E-Mails: **Nicht weiterleiten**. 

Obwohl diese Option für Benutzer (und Exchange-Administratoren) wie eine Rights Management-Standardvorlage angezeigt wird, die ausgewählt werden kann, handelt es sich bei **Nicht weiterleiten** um keine Vorlage. Aus diesem Grund wird sie nicht im klassischen Azure-Portal angezeigt, wenn Sie Vorlagen für Azure Rights Management anzeigen und verwalten. Stattdessen stellt die Option **Nicht weiterleiten** eine Reihe von Berechtigungen dar, die von Benutzern dynamisch auf ihre E-Mail-Empfänger angewendet werden.

Wenn die Option **Nicht weiterleiten** auf eine E-Mail-Nachricht angewendet wird, kann diese von den Empfängern nicht weitergeleitet, gedruckt, vollständig oder teilweise kopiert werden, ihre Anhänge können nicht gespeichert werden, und sie kann nicht unter einem anderen Namen gespeichert werden. Im Outlook-Client ist beispielsweise die Schaltfläche „Weiterleiten“ nicht verfügbar, die Menüoptionen **Speichern unter**, **Anlage speichern** und **Drucken** sind nicht verfügbar, und Sie können keine Empfänger in den Feldern **An**, **Ccc** und **Bcc** hinzufügen oder ändern.

Es besteht ein wichtiger Unterschied zwischen dem Anwenden der Option **Nicht weiterleiten** und dem Anwenden einer Vorlage, die die Berechtigung „Weiterleiten“ für eine E-Mail nicht gewährt: Bei der Option **Nicht weiterleiten** wird eine dynamische Liste autorisierter Benutzer verwendet, der die vom Benutzer ausgewählten Empfänger der ursprünglichen E-Mail zugrunde liegen; für die Berechtigungen in der Vorlage gilt hingegen eine statische Liste autorisierter Benutzer, die zuvor vom Administrator festgelegt wurden. Wie wirkt sich dieser Unterschied aus? Betrachten Sie das folgende Beispiel: 

Ein Benutzer möchte bestimmten Personen in der Marketingabteilung Informationen per E-Mail zusenden, die jedoch nicht für andere Personen zugänglich sein sollen. Sollte er die E-Mail mit einer Vorlage schützen, die die Rechte (Anzeigen, Antworten und Speichern) auf die Marketingabteilung beschränkt?  Oder sollte er die Option **Nicht weiterleiten** auswählen? In beiden Fällen wären die Empfänger nicht in der Lage, die E-Mail weiterzuleiten. 

- Wenn die Vorlage angewendet wird, können die Empfänger die Informationen an andere Personen in der Marketingabteilung weitergeben. Ein Empfänger könnte beispielsweise im Explorer die E-Mail per Drag & Drop in ein freigegebenes Verzeichnis oder an ein USB-Laufwerk verschieben. Nun können alle Mitarbeiter der Marketingabteilung (sowie der Besitzer der E-Mail) mit Zugriff auf diesen Speicherort die Informationen aus der E-Mail einsehen.
 
- Wird hingegen die Option **Nicht weiterleiten** angewendet, können die Empfänger die Informationen nicht an andere Personen in der Marketingabteilung übermitteln, indem Sie sie an einen anderen Speicherort verschieben. In diesem Szenario können nur die ursprünglichen Empfänger (und der E-Mail-Besitzer) die Informationen in der E-Mail einsehen.

> [!NOTE] 
> Verwenden Sie **Nicht weiterleiten**, wenn es wichtig ist, dass nur die vom Absender ausgewählten Empfänger die Informationen in der E-Mail einsehen können. Verwenden Sie eine Vorlage für E-Mail-Nachrichten, um Berechtigungen auf eine zuvor vom Administrator angegebene Gruppe von Personen zu beschränken, und zwar unabhängig von den Empfängern, die der Absender ausgewählt hat.




## <a name="see-also"></a>Siehe auch
[Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](configure-custom-templates.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]




<!--HONumber=Jan17_HO4-->


