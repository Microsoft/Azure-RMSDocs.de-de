---
title: "Szenario - Dateien auf einer Dateiserverfreigabe schützen | Azure RMS"
description: "In diesem Szenario und der unterstützenden Benutzerdokumentation wird Azure Rights Management zum Schutz aller von Ihnen gewünschten Dateien auf einem Dateiserver verwendet. Dies stellt sicher, dass nur Mitarbeiter Ihrer Organisation darauf zugreifen können, selbst wenn die Dateien kopiert und an einem Ort gespeichert werden, der nicht unter der Kontrolle Ihrer IT-Abteilung liegt, oder wenn sie per E-Mail an andere Benutzer gesendet werden."
author: cabailey
manager: mbaldwin
ms.date: 08/24/2016
ms.topic: get-started-article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 283c7db3-5730-439e-a215-40a1088ed506
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 024a29d7c7db2e4c0578a95c93e22f8e7a5b173e
ms.openlocfilehash: adc8ebd3063d8ac4b3710c517f0177fc25a16845


---

# Szenario - Dateien auf einer Dateiserverfreigabe schützen

>*Gilt für: Azure Rights Management, Office 365*

In diesem Szenario und der unterstützenden Benutzerdokumentation wird Azure Rights Management zum Schutz aller von Ihnen gewünschten Dateien auf einem Dateiserver verwendet. Dies stellt sicher, dass nur Mitarbeiter Ihrer Organisation darauf zugreifen können, selbst wenn die Dateien kopiert und an einem Ort gespeichert werden, der nicht unter der Kontrolle Ihrer IT-Abteilung liegt, oder wenn sie per E-Mail an andere Benutzer gesendet werden.

Diese Anweisungen verwenden eine der Standardvorlagen, die den Zugriff auf alle Mitarbeiter mit allen Nutzungsrechten beschränkt. Bei Bedarf können Sie jedoch die Zugriffs- und Nutzungsrechte weiter einschränken, indem Sie anstatt einer Standardvorlage eine benutzerdefinierte Vorlage konfigurieren.

Die Anweisungen sind unter den folgenden Umständen geeignet:

-   Sie müssen neben Office-Dateien auch alle anderen Dateitypen schützen. Dateien, die nicht direkt von Azure RMS geschützt werden können, werden generisch geschützt.

-   Alle Dateien im angegebenen Pfad (einschließlich Unterordner) werden geschützt.

-   Der Schutz wird regelmäßig erneut auf alle Dateien angewendet, um sicherzustellen, dass alle Änderungen an den Vorlagen für Benutzerrechterichtlinien auf die geschützten Dateien angewendet werden.

## Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, und führen Sie dann die Anweisungen für die unterstützenden Verfahren durch, bevor Sie mit der Benutzerdokumentation fortfahren.

## Anforderungen bei diesem Szenario
Damit die Anweisungen in diesem Szenario funktionieren, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx)|
|Sie haben Ihre lokalen Active Directory-Benutzerkonten, einschließlich ihrer E-Mail-Adressen, mit Azure Active Directory oder Office 365 synchronisiert. Dies ist für alle Benutzer erforderlich, die möglicherweise auf Dateien zugreifen müssen, nachdem diese mit FCI und Azure Rights Management geschützt wurden.|[Vorbereiten für Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx)|
|Eine der folgenden Komponenten:<br /><br />– Zum Verwenden einer Standardvorlage für alle Benutzer: Sie haben die Standardvorlage &lt;Organisationsname&gt; – Vertraulich nicht archiviert<br /><br />– Zum Verwenden einer benutzerdefinierten Vorlage für bestimmte Benutzer: Sie haben diese benutzerdefinierte Vorlage erstellt und veröffentlicht|[Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx)|
|Die Rights Management-Freigabeanwendung wird auf Benutzercomputern bereitgestellt, auf denen Windows ausgeführt wird.|[Automatische Bereitstellung für die Microsoft Rights Management-Freigabeanwendung.](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx)|
|Sie haben das RMS-Schutztool heruntergeladen und die erforderlichen Komponenten für Azure RMS konfiguriert.|Anweisungen zum Herunterladen des Tools und zum Erfüllen der Voraussetzungen: [RMS-Schutz-Cmdlets](https://msdn.microsoft.com/library/mt433195.aspx)<br /><br />Informationen zum Konfigurieren zusätzlich erforderlicher Komponenten für Azure RMS wie dem Dienstprinzipalkonto: [About_RMSProtection_AzureRMS](https://msdn.microsoft.com/library/mt433202.aspx)|

### Konfigurieren eines Dateiservers zum Schutz aller Dateien mithilfe von Azure RMS und dem Ressourcen-Manager für Dateiserver mit Dateiklassifizierungsinfrastruktur

1.  Starten Sie eine Windows PowerShell-Sitzung. Sie müssen diese Sitzung nicht als Administrator ausführen.

2.  Authentifizieren Sie sich bei Azure RMS:

    ```
    Set-RMSServerAuthentication
    ```
    Wenn Sie dazu aufgefordert werden, geben Sie die Werte für das Dienstprinzipalkonto ein, das Sie als erforderliche Komponente für die RMS-Schutz-Cmdlets erstellt haben.

3.  Führen Sie Folgendes aus, um die zum Schutz der Dateien verwendete Vorlagen-ID zu identifizieren:

    ```
    Get-RMSTemplate
    ```
    Suchen Sie nach dem Vorlagennamen **&lt;Organisationsname&gt; – Vertraulich**, um die Standardvorlage zu verwenden, die Zugriff auf alle Mitarbeiter mit allen Nutzungsrechten einschränkt. Verwenden Sie beispielsweise **VanArsdel, Ltd – Vertraulich**.

4.  Befolgen Sie die schrittweisen Anweisungen unter [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](https://technet.microsoft.com/library/mt601315%28v=ws.10%29.aspx).

    Dabei wird ein Windows PowerShell-Skript einbezogen, das Sie angeben, um im Ressourcen-Manager für Dateiserver eine benutzerdefinierte ausführbare Datei auszuführen. Die Anweisungen beinhalten außerdem, wie zu prüfen ist, dass die Dateien durch Azure Rights Management geschützt sind.

## Anweisungen für Benutzerdokumentation
Wenn es sich bei den zu schützenden Dateien nur um Office-Dateien handelt, müssen Sie Benutzern möglicherweise keine Anweisungen zu den geschützten Dateien bereitstellen. Wenn autorisierte Benutzer die Dokumente öffnen, werden diese wie gewohnt in Office angezeigt. Einziger Unterschied ist, dass Benutzer gegebenenfalls zur Authentifizierung aufgefordert werden. In diesem Fall wird am oberen Rand des Dokuments in einer Informationsleiste angezeigt, dass das Dokument geschützt ist.

Wenn die geschützten Dateien eine **.ppdf**-Erweiterung haben oder es sich um geschützte Text- oder Bilddateien handelt (beispielsweise mit der Dateinamenerweiterung **.ptxt** oder **.pjpg**), sind diese Dateien schreibgeschützt und können nicht bearbeitet werden. Benutzer können sie mit dem Viewer für RMS-Freigabeanwendungen anzeigen, der automatisch für diese Dateitypen geladen wird. Diese Dateien werden direkt von Azure RMS geschützt. Dabei werden alle Richtlinieneinstellungen aus der gewählten Vorlage angewendet, mit Ausnahme der Nutzungsrechte, da die Datei an sich schreibgeschützt ist. Sofern Sie diese Dateitypen nicht schützen möchten, benötigen Sie in der Regel keine Anweisungen für dieses Szenario. Sie sollten jedoch das Helpdesk informieren, da dieses Benutzern gegebenenfalls erklären muss, warum diese Dateien nicht bearbeitbar sind.

Wenn die geschützten Dateien die Dateinamenerweiterung **.pfile** haben, können Benutzer diese Dateien anzeigen, müssen sie jedoch zum Bearbeiten und Speichern der Änderungen unter dem ursprünglichen Dateinamen speichern (und die Erweiterung ".pfile" entfernen). Diese Dateien werden generell durch Azure RMS geschützt. Die Nutzungsrechte aus der von Ihnen angewendeten Vorlage können nicht erzwungen werden. Der Schutz der Datei geht daher verloren, wenn sie unter einem neuen Namen gespeichert wird. Für dieses Szenario sind Anweisungen für Benutzer erforderlich.

Verwenden Sie die folgende Vorlage, und kopieren Sie die Anweisungen für die Endbenutzer, damit sie wissen, wie sie generisch geschützte Dateien bearbeiten können. Nehmen Sie entsprechend Ihrer Umgebung die folgenden Änderungen vor:

-   Ersetzen Sie *&lt;Dateityp&gt;* und *&lt;Dateiserverfreigabe&gt;* durch den generisch geschützten Dateityp und den Name der Dateiserverfreigabe.

-   Ersetzen Sie *&lt;Organisationsname&gt;* durch den Namen Ihrer Organisation, wie er in Ihren Azure Rights Management-Standardvorlagen angezeigt wird.

-   Ersetzen Sie *&lt;Organisationsname&gt;* durch den Namen Ihrer Organisation.

-   Ersetzen Sie *&lt;Anweisungen zum Speichern der Datei und zum Entfernen der Dateinamenerweiterung .pfile&gt;* durch anwendungsspezifische Anweisungen für diesen Dateityp.

-   Ersetzen Sie auch die Kontaktdetails durch Anweisungen dazu, wie sich Benutzer an das Helpdesk wenden können, z. B. über einen Link zur Website, eine E-Mail-Adresse oder eine Telefonnummer.

-   Nehmen Sie jegliche sonstigen Änderungen an den Anweisungen vor, und senden Sie sie an diese Benutzer.

Die Beispieldokumentation veranschaulicht, wie diese Anweisungen für Benutzer nach Ihren Anpassungen aussehen können.

![Benutzerdokumentationsvorlage für die Azure RMS-Schnellbereitstellung](../media/AzRMS_UsersBanner.png)

### So bearbeiten Sie einen &lt;Dateityp&gt; aus der &lt;Dateiserverfreigabe&gt;

1.  Doppelklicken Sie auf die Datei, um sie zu öffnen. Sie werden möglicherweise zur Eingabe Ihrer Anmeldeinformationen aufgefordert.

2.  In einem Dialogfeld für **geschützte Dateien** der Microsoft Rights Management-Freigabeanwendung wird angegeben, dass Sie die Berechtigungen für **&lt;Organisationsname&gt; – Vertraulich** beachten müssen. Dies bedeutet, dass Sie dieses Dokument nicht an anderen Personen weitergeben dürfen, die keine Mitarbeiter von &lt;Organisationsname&gt; sind.

3.  Klicken Sie auf **Öffnen**.

4.  Um die Datei zu bearbeiten, speichern Sie sie zuerst, und entfernen Sie die Dateinamenerweiterung ".pfile":

    -   &lt;Anweisungen zum Speichern der Datei und zum Entfernen der Dateinamenerweiterung „.pfile“&gt;

5.  Sie können die Datei jetzt wie gewohnt bearbeiten und speichern.

Die Datei wird in regelmäßigen Abständen erneut geschützt, wobei sie wieder die Erweiterung ".pfile" erhält, sodass Sie diese Schritte wiederholen müssen.

**Benötigen Sie Unterstützung?**

-   Zusätzliche Informationen:

    -   [Anzeigen und Verwenden von Dateien, die geschützt wurden](https://technet.microsoft.com/library/dn574741%28v=ws.10%29)

-   Wenden Sie sich an den Helpdesk:

    -   *&lt;Kontaktinformationen&gt;*

### Beispiel für eine angepasste Benutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

#### Bearbeiten von CAD-Zeichnungen aus der ProjectNextGen-Freigabe

1.  Doppelklicken Sie auf die Datei, um sie zu öffnen. Sie werden möglicherweise zur Eingabe Ihrer Anmeldeinformationen aufgefordert.

2.  In einem Dialogfeld für **geschützte Dateien** der Microsoft Rights Management-Freigabeanwendung wird angegeben, dass Sie die Berechtigungen für **VanArsdel, Ltd – Vertraulich** beachten müssen. Dies bedeutet, dass Sie dieses Dokument nicht an anderen Personen weitergeben dürfen, die keine Mitarbeiter von VanArsdel, Ltd sind.

3.  Klicken Sie auf **Öffnen**.

4.  Um die Datei zu bearbeiten, speichern Sie sie zuerst, und entfernen Sie die Dateinamenerweiterung ".pfile":

    -   **Datei** &gt; **Speichern unter**

    -   Löschen Sie die Erweiterung **.pfile** am Ende des Dateinamens, und klicken Sie auf **OK**.

5.  Sie können die Datei jetzt wie gewohnt bearbeiten und speichern.

Die Datei wird in regelmäßigen Abständen erneut geschützt, wobei sie wieder die Erweiterung ".pfile" erhält, sodass Sie diese Schritte wiederholen müssen.

**Benötigen Sie Unterstützung?**

-   Zusätzliche Informationen:

    -   [Anzeigen und Verwenden von Dateien, die geschützt wurden](https://technet.microsoft.com/library/dn574741%28v=ws.10%29)

-   Wenden Sie sich an das Helpdesk: helpdesk@vanarsdelltd.com




<!--HONumber=Aug16_HO4-->


