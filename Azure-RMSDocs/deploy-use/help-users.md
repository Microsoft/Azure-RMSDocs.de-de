---
title: "Unterstützen von Benutzern beim Schützen von Dateien mithilfe von Azure RMS – AIP"
description: "Informationen, anhand derer Sie Unterstützung für Benutzer, Administratoren und Ihren Helpdesk bieten können, nachdem Sie den Azure Rights Management-Dienst von Azure Information Protection bereitgestellt und konfiguriert haben."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/02/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: f1d2db08951c1d017ea4f011855d99423fa9d577
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="helping-users-to-protect-files-by-using-the-azure-rights-management-service"></a>Unterstützen von Benutzern beim Schützen von Dateien mit dem Azure Rights Management-Dienst

>*Gilt für: Azure Information Protection, Office 365*

Nachdem Sie Azure Information Protection für Ihre Organisation bereitgestellt und konfiguriert haben, können Sie Ihren Benutzern und Administratoren sowie Ihrem Helpdesk Hilfe und Anleitung bieten:

-   **Endbenutzerinformationen:**

    Informieren Sie Benutzer darüber, wie und wann sie Dokumente und E-Mails, die sensible Informationen enthalten, schützen können. Stellen Sie diese Informationen wann immer möglich für ihre vorhandenen Workflows bereit, sodass sie die zusätzlichen Schritte in einen bereits vertrauten Prozess implementieren können, anstatt völlig neue Prozesse einzuführen. Stellen Sie sicher, dass sie die Vorteile (und Risiken) kennenlernen, die für Ihr Geschäft spezifisch sind, und bieten Sie Ihnen Anleitung, wann Dateien und E-Mails geschützt werden sollten. Wenn Sie [benutzerdefinierte Vorlagen](configure-custom-templates.md) konfiguriert haben, sollten Sie Anleitungen zur Auswahl bereitstellen, wenn der Vorlagenname und die Beschreibung nicht aussagekräftig genug sind, um die richtige Vorlage auswählen zu können.

    > [!TIP]
    > Beispielvideos für Endbenutzer:
    >
    > -   [Azure RMS-Benutzererfahrung](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience)
    > -   [Azure RMS-Dokumentenverfolgung und -widerruf](http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation)

-   **Administratorinformationen:**

    Einige Anwendungen wenden automatisch Informationsschutz an, indem sie Richtlinien und Einstellungen verwenden, die von Administratoren konfiguriert werden. Für diese Anwendungen müssen Sie möglicherweise Anleitungen für andere Administratoren bereitstellen, die diese Anwendungen und Dienste verwalten. Weitere Informationen finden Sie unter [Unterstützung des Azure Rights Management-Diensts durch Anwendungen](../understand-explore/applications-support.md) und [Konfigurieren von Anwendungen für den Azure Rights Management-Dienst](configure-applications.md).

-   **Helpdesk-Informationen:**

    Eines der nützlichsten Helpdesktools ist der [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Helpdesk-Operatoren können das Tool mit der Azure RMS-Administratoroption ausführen und Benutzer dazu auffordern, es mit der Azure RMS-Benutzeroption auszuführen. Dieses Tool unterstützt Sie nicht nur bei der Fehlersuche, sondern behebt gefundene Probleme und zeichnet, sofern der Fehler nicht behoben werden konnte, Ablaufverfolgungsprotokolle auf.
    
    Wenn Benutzer den Azure Information Protection-Client ausführen, können Helpdesk-Operatoren sie auffordern, die Option **Hilfe und Feedback**, **Ausführen von Diagnosen** zu verwenden und danach den Client zurückzusetzen. Im Gegensatz zu RMS Analyzer loggt die Zurücksetzung jedoch den Benutzer nicht aus und führt auch keinen erneuten Bootstrap auf dem Client aus. Zusätzlich wird keine automatische Wartung durchgeführt.

    Stellen Sie bei legitimen Anforderungen für den Vollzugriff auf geschützte Dokumente – z.B. eine Anfrage von der Rechtsabteilung oder einem Vorgesetzten, nachdem ein Mitarbeiter die Organisation verlassen hat – sicher, dass der Helpdesk über Prozesse verfügt, mit denen dies unter Verwendung des Azure Rights Management-[Administratorfeatures](configure-super-users.md) angefordert werden kann.

    Darüber hinaus finden Sie im Folgenden einige der möglicherweise auftretenden Probleme:

    -   **Hilfe bei der Anmeldung:**

        Benutzer werden möglicherweise zur Eingabe von Anmeldeinformationen aufgefordert, wenn mit dem Azure Rights Management-Dienst ein Benutzer authentifiziert werden muss und dazu keine zwischengespeicherten Anmeldeinformationen verwendet werden können. Dies ist dann das Geschäfts- oder Schulkonto des Benutzers, das Ihrem Office 365- oder Azure Active Directory-Mandanten zugeordnet ist. Es handelt sich nicht um ein Microsoft-Konto (früher Microsoft Live ID) oder ein privates E-Mail-Konto des Benutzers, weil diese zurzeit vom Azure Rights Management-Dienst nicht unterstützt werden. Stellen Sie Benutzern und Ihrem Helpdesk Anweisungen bereit, welches Konto zu verwenden ist, wenn bei Verwendung dieser Anwendungen mit dem Azure Rights Management-Dienst Anmeldeinformationen abgefragt werden.

    -   **Probleme beim Schützen oder Nutzen von Inhalten:**

        Stellen Sie sicher, dass den Benutzern entsprechende Anweisungen für die verwendeten Anwendungen vorliegen und dass sie Anwendungen und Geräte verwenden, die vom Azure Rights Management-Dienst unterstützt werden. Weitere Informationen zu unterstützten Anwendungen und Geräten finden Sie unter [Anforderungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

        Wenn Benutzern beim Versuch, Inhalte zu schützen oder zu öffnen, eine Fehlermeldung angezeigt wird, fordern Sie sie auf, den [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) als Azure RMS-Benutzer auszuführen.

        Wenn Benutzer melden, dass sie geschützte Inhalte zwar öffnen können, jedoch nicht über die erforderlichen Berechtigungen verfügen, fordern Sie sie dazu auf, den [RMS Analyzer](https://www.microsoft.com/en-us/download/details.aspx?id=46437) als Azure RMS-Benutzer auszuführen und die Vorlagen herunterzuladen und anzuzeigen. Hierdurch wird bestätigt, dass sie die Vorlagen erfolgreich heruntergeladen haben und welche Rechte die Vorlage bereitstellt. Die Ursache hierfür könnte sein, dass sich der Benutzer nicht in der Gruppe befindet, die für die Vorlage konfiguriert wurde, oder dass die Vorlage für den Benutzer neu konfiguriert werden muss.

Verwenden Sie folgende Abschnitte für anwendungsspezifische Informationen, um Benutzern beim Schützen sensibler Dokumente und E-Mails zu helfen.

## <a name="using-information-protection-with-the-azure-information-protection-client"></a>Verwenden des Informationsschutzes mit dem Azure Information Protection-Client
Der Azure Information Protection-Client ist möglicherweise erforderlich, damit Benutzer geschützte Dokumente und E-Mails schützen und nutzen können, wenn sie Office 2010 verwenden. Er wird aber auch für Computer und mobile Geräte empfohlen.

Der Azure Information Protection-Client erleichtert es Benutzern, wichtige Dokumente zu schützen, die von ihnen geschützten Dokumente nachzuverfolgen und, falls nötig, den Zugriff darauf zu widerrufen.

Anweisungen zur Verwendung dieses Clients für Windows-Computer finden Sie im [Azure Information Protection-Client – Benutzerhandbuch](../rms-client/client-user-guide.md).


## <a name="using-information-protection-with-office-365-office-2016-or-office-2013"></a>Verwenden von Informationsschutz mit Office 365, Office 2016 oder Office 2013
Wenn Sie den Azure Rights Management-Dienst verwenden und den Azure Information Protection-Client nicht installiert haben, wird die Azure Information Protection-Leiste nicht in den Office-Desktopanwendungen der Benutzer angezeigt. Auch die Schaltfläche **Schützen** wird nicht im Menüband oder die Option **Klassifizieren und schützen** für den Datei-Explorer angezeigt. Mithilfe dieser Optionen können die Dateien einfacher geschützt werden. Diese Benutzer müssen ähnliche Anleitungen wie die nachfolgenden befolgen.

> [!TIP]
> Um anwendungsspezifische Hilfe und Anleitungen zur Verwendung des Informationsschutzes mit diesen Anwendungen zu finden, suchen Sie nach **IRM** sowie dem Anwendungsnamen und der -version.

#### <a name="to-protect-a-document-in-word-2013"></a>So schützten Sie ein Dokument in Word 2013

1.  Erstellen Sie in Microsoft Word ein neues Dokument.

2.  Klicken Sie im Menü **Datei** auf **Info**, **Dokument schützen**, **Zugriff beschränken**, und wählen Sie dann eine Vorlage aus, um schnell die entsprechenden Nutzungsrechte anzuwenden, oder klicken Sie auf **Zugriff beschränken** , und wählen Sie die Nutzungsrechte selbst aus.

    > [!NOTE]
    > Wenn Sie zum ersten Mal Rights Management verwendet haben, stellen Sie eine Verbindung mit dem [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)]-Dienst her, und Sie werden zur Eingabe von Anmeldeinformationen aufgefordert, um den Office IRM-Client zu konfigurieren.

3.  Speichern Sie das Dokument.

Wenn das Dokument von anderen geöffnet wird, werden sie zuerst authentifiziert. Wenn Sie nicht autorisiert sind, um das Dokument zu öffnen, wird es nicht geöffnet. Wenn sie zum Öffnen des Dokuments autorisiert sind, wird es mit den eingeschränkten Nutzungsrechten, die für diesen Benutzer angegeben wurden, geöffnet. Beispielsweise gestattet ein Nutzungsrecht „Nur anzeigen“ dem Benutzer nicht das Bearbeiten oder Speichern des Dokuments, auch nicht, wenn es vorher an einen anderen Speicherort kopiert wird. Die Nutzungsrechte werden am oberen Rand des Dokuments in einem Einschränkungsbanner angezeigt. In dem Banner können die Berechtigungen angezeigt werden, die auf das Dokument angewendet werden, oder es kann ein Link zu deren Anzeige vorhanden sein.

#### <a name="to-protect-an-email-message-using-outlook-2013-and-exchange-online"></a>So schützten Sie eine E-Mail mithilfe von Outlook 2013 und Exchange Online

1.  Erstellen Sie in Outlook eine neue E-Mail, die an einen Empfänger in Ihrer Organisation adressiert ist.

2.  Klicken Sie auf der Registerkarte **OPTIONEN** auf **Berechtigung**, und wählen Sie dann eine Option aus. Beispiel: **Nicht weiterleiten**, **&lt;Unternehmensname&gt; – Vertraulich** oder **&lt;Unternehmensname&gt; – Nur vertrauliche Ansicht**.

3.  Senden Sie die Nachricht.

Ähnlich wie beim Anzeigen eines geschützten Dokuments, werden die Empfänger der E-Mail bei deren Empfang zuerst authentifiziert. Wenn sie zum Anzeigen der E-Mail autorisiert sind, wird sie mit den eingeschränkten Nutzungsrechten, die für diesen Benutzer angegeben wurden, geöffnet. Wenn Sie beispielsweise **Nicht weiterleiten**ausgewählt haben, ist die Schaltfläche „Weiterleiten“ im Menüband nicht verfügbar.

#### <a name="to-protect-an-email-message-using-the-outlook-web-app"></a>So schützten Sie eine E-Mail mithilfe von Outlook Web App

1.  Erstellen Sie in Outlook Web App eine neue E-Mail, die an einen Empfänger in Ihrer Organisation adressiert ist.

2.  Klicken Sie auf **...**, auf **Berechtigung festlegen**, und wählen Sie dann eine Option aus. Beispiel: **Nicht weiterleiten**, **Nicht allen antworten**, **&lt;Unternehmensname&gt; – Vertraulich** oder **&lt;Unternehmensname&gt; – Nur vertrauliche Ansicht**.

3.  Senden Sie die Nachricht.

Ähnlich wie beim Anzeigen eines geschützten Dokuments, werden die Empfänger der E-Mail bei deren Empfang zuerst authentifiziert. Wenn sie zum Anzeigen der E-Mail autorisiert sind, wird sie mit den eingeschränkten Nutzungsrechten, die für diesen Benutzer angegeben wurden, geöffnet. Wenn Sie beispielsweise **Nicht allen antworten**ausgewählt haben, ist die Option **ALLEN ANTWORTEN** im Nachrichtenfenster nicht verfügbar.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

