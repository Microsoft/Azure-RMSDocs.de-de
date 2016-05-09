---
title: TEST: Konfigurieren von Nutzungsrechten für Azure Rights Management
ms.custom: na
ms.reviewer: na
ms.service: rights-management
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: TEST
author: Cabailey
---
# VORHER: Konfigurieren von Nutzungsrechten für Azure Rights Management
Wenn Sie Schutz für Dateien oder E-Mails mithilfe von Azure Rights Management (Azure RMS) festlegen und keine Vorlage verwenden, müssen Sie die Nutzungsrechte selbst konfigurieren. Wenn Sie benutzerdefinierte Vorlagen für Azure RMS konfigurieren, wählen Sie außerdem die Nutzungsrechte, die dann automatisch angewendet werden, wenn die Vorlage von Benutzern, Administratoren oder konfigurierten Diensten ausgewählt wird. Im klassischen Azure-Portal können Sie beispielsweise Rollen auswählen, die eine logische Gruppierung von Nutzungsrechten konfigurieren, oder Sie können die einzelnen Berechtigungen konfigurieren:

Verwenden Sie diesen Artikel, um die gewünschten Nutzungsrechte für die verwendete Anwendung zu konfigurieren und zu verstehen, wie diese Rechte von den Anwendungen interpretiert werden.

## Nutzungsrechte und Beschreibungen
In den folgenden Abschnitten werden die von Rights Management unterstützten Benutzerrechte aufgezählt, und es wird beschrieben, wie sie genutzt und interpretiert werden. In diesen Abschnitten wird das Nutzungsrecht in der Regel als **Allgemeiner Name** angezeigt bzw. referenziert. Es ist eine benutzerfreundlichere Version des Einzelwortwerts, der im Code verwendet wird (der **Richtliniencodierung**-Wert). Die **API-Konstante oder der API-Wert** ist der SDK-Name für einen MSIPC API-Aufruf, der verwendet wird, wenn Sie eine RMS-fähige Anwendung schreiben, die auf ein Nutzungsrecht überprüft oder einer Richtlinie ein Nutzungsrecht hinzufügt.

### Allgemeiner Name: Inhalt bearbeiten, Bearbeiten

**Richtliniencodierung:**

- DOCEDIT

**Beschreibung:**

- Ermöglicht es dem Benutzer, den Inhalt in der Anwendung zu ändern, neu anzuordnen, zu formatieren oder zu filtern. Gewährt nicht das Recht, die bearbeitete Kopie speichern zu können.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als Teil der Optionen **Ändern** und **Vollzugriff** .

**Name im klassischen Azure-Portal:**

- **Inhalt bearbeiten**

**Name in AD RMS-Vorlagen:**

- **Bearbeiten**

**API-Konstante oder -Wert**

- Nicht zutreffend

**Zusätzliche Informationen:**

- In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu speichern.

---

### Allgemeiner Name: Speichern

**Richtliniencodierung:**

- EDIT

**Beschreibung:**

- Ermöglicht es dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als Teil der Optionen **Ändern** und **Vollzugriff** .

**Name im klassischen Azure-Portal:**

- **Datei speichern**

**Name in AD RMS-Vorlagen:**

- Speichern

**API-Konstante oder -Wert**

- IPC_GENERIC_WRITEL"EDIT"

**Zusätzliche Informationen:**

- In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu ändern.

---

### Allgemeiner Name: Kommentar

**Richtliniencodierung:**

- COMMENT

**Beschreibung:**

- Aktiviert die Option, dem Inhalt Anmerkungen oder Kommentare hinzufügen zu können.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Nicht implementiert.

**Name im klassischen Azure-Portal:**

- Nicht implementiert.

**Name in AD RMS-Vorlagen:**

- Nicht implementiert.

**API-Konstante oder -Wert**

- IPC_GENERIC_COMMENTL"COMMENT

**Zusätzliche Informationen:**

- Dieses Recht ist im SDK verfügbar, ist als eine Ad-hoc-Richtlinie im RMS-Schutz-Modul (RMSProtection) für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwarelieferanten implementiert. Es wird allerdings nicht häufig verwendet und wird derzeit nicht vom Office-Anwendungen unterstützt.

---

### Allgemeiner Name: Speichern unter, Exportieren

**Richtliniencodierung:**

- EXPORTIEREN

**Beschreibung:**

- Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). Je nach Anwendung kann die Datei ohne Schutz gespeichert werden.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als Teil der Optionen **Ändern** und **Vollzugriff** .

**Name im klassischen Azure-Portal:**

- **Inhalt exportieren (Speichern unter)**

**Name in AD RMS-Vorlagen:**

- **Exportieren (Speichern unter)**

**API-Konstante oder -Wert**

- IPC_GENERIC_EXPORTL"EXPORT"

**Zusätzliche Informationen:**

- Durch dieses Recht hat der Benutzer auch die Möglichkeit, andere Exportoptionen in Anwendungen auszuführen, beispielsweise **An OneNote senden**.

---

### Allgemeiner Name: Weiterleiten

**Richtliniencodierung:**

- FORWARD

**Beschreibung:**

- Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in den Zeilen **An** und **Cc** .

**Implementierung in benutzerdefinierten Office-Rechten:**

- Verweigert, wenn die Standardrichtlinie **Nicht weiterleiten** verwendet wird.

**Name im klassischen Azure-Portal:**

- **Weiterleiten**

**Name in AD RMS-Vorlagen:**

- **Weiterleiten**

**API-Konstante oder -Wert**

- IPC_EMAIL_FORWARDL"FORWARD"

**Zusätzliche Informationen:**

- Gestattet es dem Weiterleiter nicht, anderen Benutzern Berechtigungen als Teil des Weiterleitungsvorgangs zu gewähren.

---

### Allgemeiner Name: Vollzugriff

**Richtliniencodierung:**

- OWNER

**Beschreibung:**

- Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als benutzerdefinierte **Vollzugriff** -Option.

**Name im klassischen Azure-Portal:**

- **Vollzugriff**

**Name in AD RMS-Vorlagen:**

- **Vollzugriff**

**API-Konstante oder -Wert**

- IPC_GENERIC_ALLL"OWNER"

**Zusätzliche Informationen:**

- Umfasst die Möglichkeit, den Schutz zu entfernen.

---

### Allgemeiner Name: Drucken

**Richtliniencodierung:**

- PRINT

**Beschreibung:**

- Aktiviert die Optionen zum Drucken des Inhalts.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als Option **Inhalt drucken** in benutzerdefinierten Berechtigungen. Keine Pro-Empfänger-Einstellung.

**Name im klassischen Azure-Portal:**

- **Drucken**

**Name in AD RMS-Vorlagen:**

- **Drucken**

**API-Konstante oder -Wert**

- IPC_GENERIC_PRINTL"PRINT

---

### Allgemeiner Name: Antwort

**Richtliniencodierung:**

- REPLY

**Beschreibung:**

- Aktiviert die Option „Antwort“ in einem E-Mail-Client, ohne Änderungen in der Zeile **An** oder **Cc** zuzulassen.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Nicht zutreffend

**Name im klassischen Azure-Portal:**

- **Antwort**

**Name in AD RMS-Vorlagen:**

- **Antwort**

**API-Konstante oder -Wert**

- IPC_EMAIL_REPLY

---

### Allgemeiner Name: Allen antworten

**Richtliniencodierung:**

- REPLYALL

**Beschreibung:**

- Aktiviert die Option **Allen antworten** in einem E-Mail-Client, ermöglicht es dem Benutzer jedoch nicht, der Zeile **An** oder **Cc** Empfänger hinzuzufügen.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Nicht zutreffend

**Name im klassischen Azure-Portal:**

- **Allen antworten**

**Name in AD RMS-Vorlagen:**

- **Allen antworten**

**API-Konstante oder -Wert**

- IPC_EMAIL_REPLYALLL"REPLYALL"

---

### Allgemeiner Name: Anzeigen, Öffnen, Lesen

**Richtliniencodierung:**

- ANZEIGEN

**Beschreibung:**

- Ermöglicht es dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als benutzerdefinierte Richtlinie **Lesen** , Option **Anzeigen** .

**Name im klassischen Azure-Portal:**

- **Inhalt anzeigen**

**Name in AD RMS-Vorlagen:**

- **Anzeigen**

**API-Konstante oder -Wert**

- IPC_GENERIC_READL"VIEW"

---

### Allgemeiner Name: Rechte anzeigen

**Richtliniencodierung:**

- ANZEIGENRIGHTSDATA

**Beschreibung:**

- Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie anzuzeigen.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Nicht implementiert.

**Name im klassischen Azure-Portal:**

- **Zugewiesene Rechte anzeigen**

**Name in AD RMS-Vorlagen:**

- **Rechte anzeigen**

**API-Konstante oder -Wert**

- IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

---

### Allgemeiner Name: Rechte anzeigen

**Richtliniencodierung:**

- ANZEIGENRIGHTSDATA

**Beschreibung:**

- Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie anzuzeigen.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Nicht implementiert.

**Name im klassischen Azure-Portal:**

- **Zugewiesene Rechte anzeigen**

**Name in AD RMS-Vorlagen:**

- **Rechte anzeigen**

**API-Konstante oder -Wert**

- IPC_READ_RIGHTSL"VIEWRIGHTSDATA"

**Zusätzliche Informationen:**

- Von einigen Anwendungen ignoriert.

---

### Allgemeiner Name: Rechte ändern

**Richtliniencodierung:**

- EDITRIGHTSDATA

**Beschreibung:**

- Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie zu ändern. Beinhaltet das Entfernen des Schutzes.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Nicht implementiert.

**Name im klassischen Azure-Portal:**

- **Rechte ändern**

**Name in AD RMS-Vorlagen:**

- **Rechte bearbeiten**

**API-Konstante oder -Wert**

- IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"

---

### Allgemeiner Name: Makros zulassen

**Richtliniencodierung:**

- OBJMODEL

**Beschreibung:**

- Aktiviert die Option, Makros oder anderen programmgesteuerten oder remoten Zugriff auf den Inhalt eines Dokuments ausführen zu können.

**Implementierung in benutzerdefinierten Office-Rechten:**

- Als benutzerdefinierte Richtlinienoption zum **Zulassen von programmgesteuertem Zugriff** . Keine Pro-Empfänger-Einstellung.

**Name im klassischen Azure-Portal:**

- **Makros zulassen**

**Name in AD RMS-Vorlagen:**

- **Makros zulassen**

**API-Konstante oder -Wert**

- Nicht zutreffend

---


|Allgemeiner Name|Richtliniencodierung|Beschreibung|Implementierung in benutzerdefinierten Office-Rechten|Name im klassischen Azure-Portal|Name in den AD RMS-Vorlagen|API constant oder value|Zusätzliche Informationen|
|---------------|----------------------|---------------|------------------------------------------|-------------------------------------|----------------------------|-------------------------|--------------------------|
|Inhalt bearbeiten, Bearbeiten|DOCEDIT|Ermöglicht es dem Benutzer, den Inhalt in der Anwendung zu ändern, neu anzuordnen, zu formatieren oder zu filtern. Gewährt nicht das Recht, die bearbeitete Kopie speichern zu können.|Als Teil der Optionen **Ändern** und **Vollzugriff** .|**Inhalt bearbeiten**|**Bearbeiten**|Nicht verfügbar|In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu speichern.|
|Speichern|EDIT|Ermöglicht es dem Benutzer, das Dokument am aktuellen Speicherort zu speichern.|Als Teil der Optionen **Ändern** und **Vollzugriff** .|**Datei speichern**|**Speichern**|IPC_GENERIC_WRITEL"EDIT"|In Office-Anwendungen ermöglicht dieses Recht es den Benutzern auch, das Dokument zu ändern.|
|Kommentar|COMMENT|Aktiviert die Option, dem Inhalt Anmerkungen oder Kommentare hinzufügen zu können.|Nicht implementiert.|Nicht implementiert.|Nicht implementiert.|IPC_GENERIC_COMMENTL"COMMENT"|Dieses Recht ist im SDK verfügbar, ist als eine Ad-hoc-Richtlinie im RMS-Schutz-Modul (RMSProtection) für Windows PowerShell verfügbar und wurde in einigen Anwendungen von Softwarelieferanten implementiert. Es wird allerdings nicht häufig verwendet und wird derzeit nicht von Office-Anwendungen unterstützt.|
|Speichern unter, Exportieren|EXPORTIEREN|Aktiviert die Option zum Speichern des Inhalts unter einem anderen Dateinamen (Speichern unter). Je nach Anwendung kann die Datei ohne Schutz gespeichert werden.|Als Teil der Optionen **Ändern** und **Vollzugriff** .|**Inhalt exportieren (Speichern unter)**|**Exportieren (Speichern unter)**|IPC_GENERIC_EXPORTL"EXPORT"|Durch dieses Recht hat der Benutzer auch die Möglichkeit, andere Exportoptionen in Anwendungen auszuführen, beispielsweise **An OneNote senden**.|
|Weiterleiten|FORWARD|Aktiviert die Option zum Weiterleiten einer E-Mail-Nachricht und zum Hinzufügen von Empfängern in den Zeilen **An** und **Cc** .|Verweigert, wenn die Standardrichtlinie **Nicht weiterleiten** verwendet wird.|**Weiterleiten**|**Weiterleiten**|IPC_EMAIL_FORWARDL"FORWARD"|Gestattet es dem Weiterleiter nicht, anderen Benutzern Berechtigungen als Teil des Weiterleitungsvorgangs zu gewähren.|
|Vollzugriff|OWNER|Gewährt alle Berechtigungen für das Dokument, und alle verfügbaren Aktionen können ausgeführt werden.|Als benutzerdefinierte **Vollzugriff** -Option.|**Vollzugriff**|**Vollständige Kontrolle**|IPC_GENERIC_ALLL"OWNER"|Umfasst die Möglichkeit, den Schutz zu entfernen.|
|Drucken|PRINT|Aktiviert die Optionen zum Drucken des Inhalts.|Als Option **Inhalt drucken** in benutzerdefinierten Berechtigungen. Keine Pro-Empfänger-Einstellung.|**Drucken**|**Drucken**|IPC_GENERIC_PRINTL"PRINT|Keine weiteren Informationen|
|Antworten|REPLY|Aktiviert die Option „Antwort“ in einem E-Mail-Client, ohne Änderungen in der Zeile **An** oder **Cc** zuzulassen.|Nicht verfügbar|**Antwort**|**Antworten**|IPC_EMAIL_REPLY|Keine weiteren Informationen|
|Allen antworten|REPLYALL|Aktiviert die Option **Allen antworten** in einem E-Mail-Client, ermöglicht es dem Benutzer jedoch nicht, der Zeile **An** oder **Cc** Empfänger hinzuzufügen.|Nicht verfügbar|**Allen antworten**|**Allen antworten**|IPC_EMAIL_REPLYALLL"REPLYALL"|Keine weiteren Informationen|
|Anzeigen, Öffnen, Lesen|ANZEIGEN|Ermöglicht es dem Benutzer, das Dokument zu öffnen und den Inhalt zu sehen.|Als benutzerdefinierte Richtlinie **Lesen** , Option **Anzeigen** .|**Inhalt anzeigen**|**Anzeigen**|IPC_GENERIC_READL"VIEW"|Keine weiteren Informationen|
|Copy|EXTRACT|Aktiviert Optionen zum Kopieren von Daten (einschließlich Screenshots) aus dem Dokument in dasselbe oder ein anderes Dokument.|Als benutzerdefinierte Richtlinienoption **Benutzern mit Lesezugriff das Kopieren des Inhalts erlauben** .|**Inhalt kopieren und extrahieren**|**Extrahieren**|IPC_GENERIC_EXTRACTL"EXTRACT"|In einigen Anwendungen ermöglicht es auch, dass das gesamte Dokument ungeschützt gespeichert werden kann.|
|Rechte anzeigen|ANZEIGENRIGHTSDATA|Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie anzuzeigen.|Nicht implementiert.|**Zugewiesene Rechte anzeigen**|**Rechte anzeigen**|IPC_READ_RIGHTSL"VIEWRIGHTSDATA"|Von einigen Anwendungen ignoriert.|
|Rechte ändern|EDITRIGHTSDATA|Ermöglicht es dem Benutzer, die auf das Dokument angewendete Richtlinie zu ändern. Beinhaltet das Entfernen des Schutzes.|Nicht implementiert.|**Rechte ändern**|**Rechte bearbeiten**|IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"|Keine weiteren Informationen|
|Makros zulassen|OBJMODEL|Aktiviert die Option, Makros oder anderen programmgesteuerten oder remoten Zugriff auf den Inhalt eines Dokuments ausführen zu können.|Als benutzerdefinierte Richtlinienoption zum **Zulassen von programmgesteuertem Zugriff** . Keine Pro-Empfänger-Einstellung.|**Makros zulassen**|**Makros zulassen**|Nicht verfügbar|Keine weiteren Informationen|

## In Berechtigungsstufen enthaltene Rechte
In einigen Anwendungen werden Nutzungsrechte in Berechtigungsstufen gruppiert. Dadurch wird es einfacher, Nutzungsrechte auszuwählen, die in der Regel gemeinsam verwendet werden. Diese Berechtigungsstufen lassen das Vergeben von Nutzungsrechten für die Benutzer weniger komplex erscheinen, weil sie unter rollenbasierten Optionen auswählen können.  Beispiele: **Prüfer** und **Mitautor**. Obwohl diese Optionen den Benutzern oft eine Zusammenfassung der Rechte anzeigen, enthalten sie möglicherweise nicht alle in der vorherigen Tabelle aufgeführten Rechte.

In der folgenden Tabelle finden Sie eine Liste dieser Berechtigungsstufen und alle darin enthaltenen Rechte.

|Berechtigungsstufe|Anwendungen|Enthaltene Rechte (allgemeiner Name)|
|---------------------|----------------|---------------------------------|
|Anzeigender Benutzer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen<br /><br />Antworten<br /><br />Allen antworten|
|Prüfer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen<br /><br />Speichern<br /><br />Inhalt bearbeiten, Bearbeiten<br /><br />Antwort [Fußnote 1]<br /><br />Allen antworten [Fußnote 1]<br /><br />Weiterleiten [Fußnote 1]|
|Mitautor|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen<br /><br />Speichern<br /><br />Inhalt bearbeiten, Bearbeiten<br /><br />Kopieren<br /><br />Rechte anzeigen<br /><br />Rechte ändern<br /><br />Makros zulassen<br /><br />Speichern unter, Exportieren<br /><br />Drucken<br /><br />Antwort [Fußnote 1]<br /><br />Allen antworten [Fußnote 1]<br /><br />Weiterleiten [Fußnote 1]|
|Mitbesitzer|Klassisches Azure-Portal<br /><br />Rights Management-Freigabeanwendung für Windows|Anzeigen, Öffnen, Lesen<br /><br />Speichern<br /><br />Inhalt bearbeiten, Bearbeiten<br /><br />Kopieren<br /><br />Rechte anzeigen<br /><br />Rechte ändern<br /><br />Makros zulassen<br /><br />Speichern unter, Exportieren<br /><br />Drucken<br /><br />Antwort [Fußnote 1]<br /><br />Allen antworten [Fußnote 1]<br /><br />Weiterleiten [Fußnote 1]<br /><br />Vollzugriff|
Fußnote 1: Gilt nicht für die Rights Management-Freigabeanwendung für Windows.

## In den Standardvorlagen enthaltene Rechte
In den Standardvorlagen sind folgende Rechte enthalten:

|Anzeigename|Enthaltene Rechte (allgemeiner Name)|
|----------------|---------------------------------|
|<Unternehmensname> – Nur vertrauliche Ansicht|Anzeigen, Öffnen, Lesen|
|<Unternehmensname> – Vertraulich|Anzeigen, Öffnen, Lesen<br /><br />Speichern<br /><br />Inhalt bearbeiten, Bearbeiten<br /><br />Rechte anzeigen<br /><br />Makros zulassen<br /><br />Weiterleiten<br /><br />Antworten<br /><br />Allen antworten|

## Weitere Informationen
[Konfigurieren von Azure Rights Management](configuring-azure-rights-management.md)



<!--HONumber=Apr16_HO3-->


