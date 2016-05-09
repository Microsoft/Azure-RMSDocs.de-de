---
# required metadata

title: Konfigurieren von Nutzungsrechten für Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 97ddde38-b91b-42a5-8eb4-3ce6ce15393d

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurieren von Nutzungsrechten für Azure Rights Management
Wenn Sie Schutz für Dateien oder E-Mails mithilfe von Azure Rights Management (Azure RMS) festlegen und keine Vorlage verwenden, müssen Sie die Nutzungsrechte selbst konfigurieren. Wenn Sie benutzerdefinierte Vorlagen für Azure RMS konfigurieren, wählen Sie außerdem die Nutzungsrechte, die dann automatisch angewendet werden, wenn die Vorlage von Benutzern, Administratoren oder konfigurierten Diensten ausgewählt wird. Im klassischen Azure-Portal können Sie beispielsweise Rollen auswählen, die eine logische Gruppierung von Nutzungsrechten konfigurieren, oder Sie können die einzelnen Berechtigungen konfigurieren:

Verwenden Sie diesen Artikel, um die gewünschten Nutzungsrechte für die verwendete Anwendung zu konfigurieren und um zu verstehen, wie diese Rechte von den Anwendungen interpretiert werden.

## Nutzungsrechte und Beschreibungen
In den folgenden Abschnitten werden die von Rights Management unterstützten Benutzerrechte aufgezählt und beschrieben und wird beschrieben, wie sie genutzt und interpretiert werden. Sie werden nach **Allgemeiner Name** aufgelistet, also in der Regel das, was Sie als das Nutzungsrecht sehen, das als die benutzerfreundlichere Version des Einzelwortwerts angezeigt oder referenziert wird, der im Code verwendet wird (der **Richtliniencodierung**-Wert). Die **API-Konstante oder der API-Wert** ist der SDK-Name für einen MSIPC API-Aufruf, der verwendet wird, wenn Sie eine RMS-fähige Anwendung schreiben, die auf ein Nutzungsrecht überprüft oder einer Richtlinie ein Nutzungsrecht hinzufügt.


### Inhalt bearbeiten, Bearbeiten

Ermöglicht es dem Benutzer, den Inhalt in der Anwendung zu ändern, neu anzuordnen, zu formatieren oder zu filtern. Gewährt nicht das Recht, die bearbeitete Kopie speichern zu können.

**Richtliniencodierung**: DOCEDIT

**Implementierung in benutzerdefinierten Office-Rechten**: als Teil der Optionen *Ändern* und *Vollzugriff*.**

**Name im klassischen Azure-Portal**: *Inhalt bearbeiten*

**Name in den AD RMS-Vorlagen**: *Bearbeiten*

**API-Konstante oder -Wert**: *Nicht zutreffend*

In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu speichern.

---

### Speichern

Ermöglicht es dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.

**Richtliniencodierung**: EDIT

**Implementierung in benutzerdefinierten Office-Rechten**: als Teil der Optionen *Ändern* und *Vollzugriff*.

**Name im klassischen Azure-Portal**: *Datei speichern*

**Name in den AD RMS-Vorlagen**: *Speichern*

**API-Konstante oder -Wert**: IPC_GENERIC_WRITEL"EDIT"

In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu ändern.

---

### Kommentar

Aktiviert die Option, dem Inhalt Anmerkungen oder Kommentare hinzufügen zu können.

**Richtliniencodierung**: COMMENT

**Implementierung in benutzerdefinierten Office-Rechten**: Nicht implementiert.

**Name im klassischen Azure-Portal**: Nicht implementiert.

**Name in den AD RMS-Vorlagen**: Nicht implementiert.

**API-Konstante oder -Wert**: IPC_GENERIC_COMMENTL"COMMENT

Dieses Recht ist im SDK verfügbar, ist als eine Ad-hoc-Richtlinie im RMS-Schutz-Modul (RMSProtection) für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwarelieferanten implementiert. Es wird allerdings nicht häufig verwendet und wird derzeit nicht von Office-Anwendungen unterstützt.

---

### Speichern unter, Exportieren

Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). Je nach Anwendung kann die Datei ohne Schutz gespeichert werden.

**Richtliniencodierung**: EXPORT

**Implementierung in benutzerdefinierten Office-Rechten**: als Teil der Optionen *Ändern* und *Vollzugriff*.

**Name im klassischen Azure-Portal**: *Inhalt exportieren (Speichern unter)*

**Name in den AD RMS-Vorlagen**: *Exportieren (Speichern unter)*

**API-Konstante oder -Wert**: IPC_GENERIC_EXPORTL"EXPORT"

Durch dieses Recht hat der Benutzer auch die Möglichkeit, andere Exportoptionen in Anwendungen auszuführen, beispielsweise *An OneNote senden*.

---

### Weiterleiten

Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in den Zeilen *An* und *Cc* .

**Richtliniencodierung**: FORWARD

**Implementierung in benutzerdefinierten Office-Rechten**: verweigert, wenn die Standardrichtlinie *Nicht weiterleiten* verwendet wird.

**Name im klassischen Azure-Portal**: *Weiterleiten*

**Name in den AD RMS-Vorlagen**: *Weiterleiten*

**API-Konstante oder -Wert:** IPC_EMAIL_FORWARDL"FORWARD"

Gestattet es dem Weiterleiter nicht, anderen Benutzern Berechtigungen als Teil des Weiterleitungsvorgangs zu gewähren.

---

### Vollzugriff

Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.

**Richtliniencodierung**: OWNER

**Implementierung in benutzerdefinierten Office-Rechten**: als benutzerdefinierte Option *Vollzugriff*.

**Name im klassischen Azure-Portal**: *Vollzugriff*

**Name in den AD RMS-Vorlagen**: *Vollzugriff*

**API-Konstante oder -Wert**: IPC_GENERIC_ALLL"OWNER"

Umfasst die Möglichkeit, den Schutz zu entfernen.

---

### Drucken

Aktiviert die Optionen zum Drucken des Inhalts.

**Richtliniencodierung**: PRINT

**Implementierung in benutzerdefinierten Office-Rechten**: als Option *Inhalt drucken* in benutzerdefinierten Berechtigungen. Keine Pro-Empfänger-Einstellung.

**Name im klassischen Azure-Portal**: *Drucken*

**Name in den AD RMS-Vorlagen**: *Drucken*

**API-Konstante oder -Wert**: IPC_GENERIC_PRINTL"PRINT"

---

### Antwort

Aktiviert die Option „Antwort“ in einem E-Mail-Client, ohne Änderungen in der Zeile *An* oder *Cc* zuzulassen.

**Richtliniencodierung**: REPLY

**Implementierung in benutzerdefinierten Office-Rechten**: Nicht zutreffend

**Name im klassischen Azure-Portal**: *Antworten*

**Name in den AD RMS-Vorlagen**: *Antworten*

**API-Konstante oder -Wert:** IPC_EMAIL_REPLY

---

### Allen antworten

Aktiviert die Option *Allen antworten* in einem E-Mail-Client, ermöglicht es dem Benutzer jedoch nicht, der Zeile *An* oder *Cc* Empfänger hinzuzufügen.

**Richtliniencodierung**: REPLYALL

**Implementierung in benutzerdefinierten Office-Rechten**: Nicht zutreffend

**Name im klassischen Azure-Portal**: *Allen antworten*

**Name in den AD RMS-Vorlagen**: *Allen antworten*

**API-Konstante oder -Wert**: IPC_EMAIL_REPLYALLL"REPLYALL"

---

### Anzeigen, Öffnen, Lesen

Ermöglicht es dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.

**Richtliniencodierung**: VIEW

**Implementierung in benutzerdefinierten Office-Rechten**: als benutzerdefinierte Option *Lesen*, Option *Anzeigen*.

**Name im klassischen Azure-Portal**: *Inhalt anzeigen*

**Name in den AD RMS-Vorlagen**: *Anzeigen*

**API-Konstante oder -Wert**: IPC_GENERIC_READL"VIEW"

---

### Rechte anzeigen

Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie anzuzeigen.

**Richtliniencodierung**: VIEWRIGHTSDATA

**Implementierung in benutzerdefinierten Office-Rechten**: Nicht implementiert.

**Name im klassischen Azure-Portal**: *Zugewiesene Rechte anzeigen*

**Name in den AD RMS-Vorlagen**: *Rechte anzeigen*

**API-Konstante oder -Wert**: IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

---

### Allgemeiner Name: Rechte anzeigen

Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie anzuzeigen.

**Richtliniencodierung**: VIEWRIGHTSDATA

**Implementierung in benutzerdefinierten Office-Rechten**: Nicht implementiert.

**Name im klassischen Azure-Portal**: *Zugewiesene Rechte anzeigen*

**Name in den AD RMS-Vorlagen**: *Rechte anzeigen*

**API-Konstante oder -Wert**: IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

Von einigen Anwendungen ignoriert.

---

### Rechte ändern

Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie zu ändern. Beinhaltet das Entfernen des Schutzes.

**Richtliniencodierung**: EDITRIGHTSDATA

**Implementierung in benutzerdefinierten Office-Rechten**: Nicht implementiert.

**Name im klassischen Azure-Portal**: *Rechte ändern*

**Name in den AD RMS-Vorlagen**: *Rechte bearbeiten*

**API-Konstante oder -Wert**: IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"

---

### Makros zulassen

Aktiviert die Option, Makros oder anderen programmgesteuerten oder remoten Zugriff auf den Inhalt eines Dokuments ausführen zu können.

**Richtliniencodierung**: OBJMODEL

**Implementierung in benutzerdefinierten Office-Rechten**: als benutzerdefinierte Richtlinienoption *Programmgesteuerten Zugriff zulassen*. Keine Pro-Empfänger-Einstellung.

**Name im klassischen Azure-Portal**: *Makros zulassen*

**Name in den AD RMS-Vorlagen**: *Makros zulassen*

**API-Konstante oder -Wert**: Nicht zutreffend


## In Berechtigungsstufen enthaltene Rechte

In einigen Anwendungen werden Nutzungsrechte in Berechtigungsstufen gruppiert. Dadurch wird es einfacher, Nutzungsrechte auszuwählen, die in der Regel gemeinsam verwendet werden. Diese Berechtigungsstufen lassen das Vergeben von Nutzungsrechten für die Benutzer weniger komplex erscheinen, weil sie unter rollenbasierten Optionen auswählen können.  Beispiele: **Prüfer** und **Mitautor**. Obwohl diese Optionen den Benutzern oft eine Zusammenfassung der Rechte anzeigen, enthalten sie möglicherweise nicht alle in der vorherigen Tabelle aufgeführten Rechte.

In der folgenden Tabelle finden Sie eine Liste dieser Berechtigungsstufen und alle darin enthaltenen Rechte.

|Berechtigungsstufe|Anwendungen|Enthaltene Rechte (allgemeiner Name)|
|---------------------|----------------|---------------------------------|
|Anzeigender Benutzer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen; Antworten; Allen Antworten|
|Prüfer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Weiterleiten [[1]](#footnote-1)|
|Mitautor|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Speichern unter, Exportieren; Drucken; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Weiterleiten [[1]](#footnote-1)|
|Mitbesitzer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Kopieren; Rechte anzeigen; Rechte ändern; Makros zulassen; Speichern unter, Exportieren; Drucken; Antworten [[1]](#footnote-1); Allen Antworten [[1]](#footnote-1); Weiterleiten [[1]](#footnote-1); Vollzugriff|

----

###### Fußnote 1
Gilt nicht für die Rights Management-Freigabeanwendung für Windows.

## In den Standardvorlagen enthaltene Rechte
In den Standardvorlagen sind folgende Rechte enthalten:

|Anzeigename|Enthaltene Rechte (allgemeiner Name)|
|----------------|---------------------------------|
|<*Unternehmensname*> *– Nur vertrauliche Ansicht*|Anzeigen, Öffnen, Lesen|
|<*Unternehmensname*> *– Vertraulich*|Anzeigen, Öffnen, Lesen; Speichern; Inhalt bearbeiten, Bearbeiten; Rechte anzeigen; Makros zulassen; Weiterleiten; Antworten; Allen antworten|

## Siehe auch
[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](configure-custom-templates.md)



<!--HONumber=Apr16_HO3-->


