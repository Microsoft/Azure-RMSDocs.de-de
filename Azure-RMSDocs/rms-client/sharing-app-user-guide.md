---
title: "Rights Management-Freigabeanwendung – Benutzerhandbuch | Azure Information Protection"
description: "Die Microsoft Rights Management-Freigabeanwendung (RMS) für Windows hilft Ihnen, wichtige Dokumente und Bilder vor Personen zu schützen, die diese Dateien nicht sehen dürfen – sogar, wenn Sie die Dateien per E-Mail senden oder auf einem anderen Gerät speichern."
author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: eaf6d02c-aa36-4915-856e-49bb71ab1484
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: aac3c6c7b5167d729d9ac89d9ae71c50dd1b6a10
ms.openlocfilehash: c89c82350768222da44c631dd88c97bcdb0db4d5


---

# Rights Management-Freigabeanwendung – Benutzerhandbuch

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Die Microsoft Rights Management-Freigabeanwendung (RMS) für Windows hilft Ihnen, wichtige Dokumente und Bilder vor Personen zu schützen, die diese Dateien nicht sehen dürfen – sogar, wenn Sie die Dateien per E-Mail senden oder auf einem anderen Gerät speichern. Sie können mit dieser Anwendung auch Dateien öffnen und verwenden, die von anderen Personen mit derselben Rights Management-Schutztechnologie geschützt wurden.

Sie benötigen dafür lediglich einen Computer, auf dem mindestens Windows 7 mit Service Pack 1 ausgeführt wird. Anschließend können diese kostenlose Anwendung von Microsoft [herunterladen und installieren](http://go.microsoft.com/fwlink/?LinkId=303970) .

Wenn Sie Fragen haben, die in diesem Handbuch nicht beantwortet werden, lesen Sie [Häufig gestellte Fragen zur Microsoft Rights Management-Freigabeanwendung für Windows](http://go.microsoft.com/fwlink/?LinkId=303971). Diese Seite enthält außerdem Informationen zur Problembehandlung, die bei Problemen hilfreich sind.

## Beispiele für die Nutzung der RMS-Freigabeanwendung
Hier einige Beispiele für die mögliche Nutzung der RMS-Freigabeanwendung zum Schutz Ihrer Dateien.

|Ziel ...|Vorgehensweise|
|----------------|------------------|
|**… Ich möchte Finanzinformationen auf sichere Weise für Personen meines Vertrauens freigeben, die in einer anderen Organisation arbeiten**<br /><br />Sie arbeiten mit einem Partnerunternehmen zusammen und möchten eine Excel-Tabelle per E-Mail senden, die geplante Vertriebszahlen enthält. Sie möchten, dass die Empfänger die Zahlen anzeigen, jedoch nicht ändern können.|Klicken Sie auf die Schaltfläche **Geschützt freigeben** im Excel-Menüband, geben Sie die E-Mail-Adressen der beiden Personen im Partnerunternehmen ein, mit denen Sie zusammenarbeiten, wählen Sie **Anzeigender Benutzer – Nur anzeigen**aus, und klicken Sie auf **Senden**.<br /><br />Wenn die E-Mail im Partnerunternehmen ankommt, können nur die Empfänger der E-Mail die Tabelle anzeigen, können diese jedoch nicht speichern, bearbeiten, drucken oder weiterleiten.<br /><br />Schritt für Schritt: [Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung](sharing-app-protect-by-email.md).|
|**… Ich möchte auf sichere Weise ein Dokument an eine Person senden, die ein iOS-Gerät verwendet**<br /><br />Sie können ein streng vertrauliches Word-Dokument an einen Kollegen senden, von dem Sie wissen, dass er regelmäßig seine E-Mails auf seinem iOS-Gerät abruft.|Verwenden Sie den Datei-Explorer, um mit der rechten Maustaste auf die Datei zu klicken und **Geschützt freigeben** auszuwählen und die Datei als Anlage an Ihre Kollegin zu senden.<br /><br />Die Empfängerin erhält die E-Mail auf ihrem iOS-Gerät. Da sie nicht über Office für iPad und iPhone verfügt, klickt sie in der E-Mail auf den Link mit den Informationen zum Herunterladen der Freigabeanwendung, installiert die Version für iOS-Geräte und zeigt anschließend das Dokument an¹.<br /><br />Schritt für Schritt: [Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung](sharing-app-protect-by-email.md).|
|**… Ich möchte überprüfen, wer wann meine geschützten Dokumente geöffnet hat und den Zugriff bei Bedarf widerrufen**<br /><br />Sie haben ein vertrauliches Entwurfsdokument auf sichere Weise für potenzielle Anbieter freigegeben und möchten nun wissen, wer wann und von wo auf das Dokument zugegriffen hat. Nachdem Sie dann einem der Anbieter den Zuschlag für das Projekt erteilt haben, möchten Sie den Zugriff auf das ursprüngliche Dokument widerrufen, sodass es von den Personen, für die Sie das Dokument freigegeben haben, nicht mehr gelesen werden kann.|Nachdem Sie ein Dokument per E-Mail freigegeben haben, wechseln Sie zur [Website zum Nachverfolgen von Dokumenten](http://go.microsoft.com/fwlink/?LinkId=529562) , um zu sehen, wer wann auf das Dokument zugegriffen hat. Wenn Sie die Freigabe beenden möchten, wählen Sie die Option zum Widerrufen des Zugriffs aus.<br /><br />Schritt für Schritt: [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](sharing-app-track-revoke.md).|
|**… Sie möchten ein Dokument lesen, das Sie als eine auf sichere Weise freigegebene E-Mail-Anlage erhalten haben, können es jedoch nicht lesen, da Ihr Unternehmen nicht mit Rights Management arbeitet.**<br /><br />Der Absender der E-Mail ist eine Person Ihres Vertrauens, da Sie schon früher geschäftliche Kontakte zu der Person gepflegt haben, und Sie nehmen an, dass die Person Ihnen Informationen zu einer neuen potenziellen Geschäftschance senden möchte.|Sie folgen den Anleitungen in der E-Mail und klicken auf den Link, um sich für Microsoft Rights Management anzumelden. Microsoft bestätigt, dass Ihre Organisation nicht über ein Abonnement verfügt, das Azure Information Protection umfasst und sendet Ihnen eine E-Mail, mit der Sie das kostenlose Anmeldeverfahren abschließen können. Anschließend melden Sie sich mit Ihrem neuen Konto an. Sie klicken auf den zweiten Link in der E-Mail, um die Rights Management-Freigabeanwendung zu installieren, und können anschließend die E-Mail-Anlage lesen und sich zu der neuen Geschäftschance informieren.<br /><br />Schritt für Schritt: [Anzeigen und Verwenden von Dateien, die mit Rights Management geschützt wurden](sharing-app-view-use-files.md).|
|**… Ich möchte die vertraulichen Unternehmensdateien auf meinem Laptop schützen, damit keine Personen von außerhalb des Unternehmens darauf zugreifen können**<br /><br />Sie sind häufig auf Reisen und verwenden Ihren Laptop, um auf Dateien in einem Ordner zuzugreifen und diese zu aktualisieren, der vor unbefugtem Zugriff geschützt werden muss.|Auf Ihrem Laptop ist die RMS-Freigabeanwendung installiert. Sie verwenden den Datei-Explorer, um die Dateien mithilfe einer Vorlage zu schützen, mit der alle Dateien im Handumdrehen geschützt werden können. Auch wenn Ihr Laptop gestohlen wird, müssen Sie sich nun keine Sorgen darüber machen, dass Personen von außerhalb des Unternehmens auf diese Dokumente zugreifen könnten.<br /><br />Schritt für Schritt: [Schützen einer Datei auf einem Gerät &#40;direkt schützen&#41; durch Verwenden der Rights Management-Freigabeanwendung](sharing-app-protect-in-place.md).|
¹ PDF-Rendering unterstützt von Foxit. Copyright © 2003–2014, Foxit Corporation.

## Was möchten Sie tun?
> [!NOTE]
> Weitere technische Informationen, z.B. zu [unterstützten Dateitypen](sharing-app-admin-guide-technical.md#supported-file-types-and-file-name-extensions) und der [Installation der Anwendung in einem Unternehmensnetzwerk](sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application), finden Sie im [Administratorhandbuch der Rights Management-Freigabeanwendung](sharing-app-admin-guide.md).

- [Herunterladen und Installieren der Freigabeanwendung](install-sharing-app.md)

- [Schützen einer Datei auf einem Gerät (direkt schützen)](sharing-app-protect-in-place.md)

- [Schützen einer Datei, die per E-Mail freigegeben ist](sharing-app-protect-by-email.md)

- [Ändern von Berechtigungen für geschützte Dateien](sharing-app-reprotect-files.md)

- [Verfolgen und Widerrufen von Dokumenten](sharing-app-track-revoke.md)

- [Anzeigen und Verwenden von Dateien, die geschützt wurden](sharing-app-view-use-files.md)

- [Entfernen des Schutzes von einer Datei](sharing-app-remove-protection.md)

- [Verwenden von Tastenkombinationen](sharing-app-keyboard-shortcuts.md)

- [Festlegen von Einstellungen im Dialogfeld](sharing-app-dialog-box.md)






<!--HONumber=Sep16_HO4-->


