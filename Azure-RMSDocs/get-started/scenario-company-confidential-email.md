---
title: "AIP-Szenario – Vertrauliche geschäftliche E-Mail senden"
description: "In diesem Szenario und der unterstützenden Benutzerdokumentation wird der Azure Rights Management-Schutz verwendet, sodass alle Benutzer innerhalb der Organisation E-Mail-Nachrichten sicher senden können, die außerhalb der Organisation nicht lesbar sind."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: get-started-article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 950799e9-2289-48c7-b95a-f54a8ead520a
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 2131f40b51f34de7637c242909f10952b1fa7d9f
ms.openlocfilehash: 04d8e694aa33bcc00deca602737e0ab11eafb53d
ms.lasthandoff: 02/24/2017


---

# <a name="scenario---send-a-company-confidential-email"></a>Szenario – Vertrauliche geschäftliche E-Mail senden

>*Gilt für: Azure Information Protection, Office 365*

In diesem Szenario und der unterstützenden Benutzerdokumentation wird die Azure Rights Management-Technologie von Azure Information Protection verwendet, sodass alle Benutzer innerhalb der Organisation E-Mail-Nachrichten sicher senden können, die außerhalb der Organisation nicht lesbar sind. Dies ist beispielsweise der Fall, wenn ein Mitarbeiter eine E-Mail-Nachricht an eine Person in einer anderen Organisation oder an ein persönliches E-Mail-Konto weiterleitet. Die E-Mail-Nachrichten und Anlagen werden durch Azure Rights Management und eine Vorlage geschützt, die Benutzer aus dem E-Mail-Client auswählen.

Die einfachste Möglichkeit zum Aktivieren dieses Szenarios ist die Verwendung einer der integrierten Standardvorlagen, die automatisch den Zugriff auf alle Benutzer innerhalb Ihrer Organisation beschränken. Sie können den Zugriff bei Bedarf weiter einschränken, indem Sie eine benutzerdefinierte Vorlage erstellen, die den Zugriff beispielsweise auf eine Teilmenge von Benutzern beschränkt oder andere Einschränkungen wie Schreibschutz oder ein Ablaufdatum aufweist oder die Weiterleitungsschaltfläche im E-Mail-Client deaktiviert.

> [!IMPORTANT]
> Während Sie in diesem Szenario bei einer benutzerdefinierten Vorlage das **Weiterleitungsrecht** entfernen können, wodurch die Weiterleitungsschaltfläche im E-Mail-Client deaktiviert wird, verhindert diese Konfiguration nicht das Übermitteln der E-Mail an andere autorisierte Benutzer. Der Empfänger kann die E-Mail-Adresse (und Anlagen) speichern und die Informationen anschließend mithilfe anderer Mechanismen weiterleiten.
> 
> Beispiel: Bob sendet eine E-Mail-Nachricht an Alice. Er verwendet eine benutzerdefinierte Vorlage, die der Marketinggruppe die Rechte zum Speichern der Datei und zum Bearbeiten des Inhalts gibt, aber keine Weiterleitung erlaubt. Alice kann die E-Mail zwar nicht an andere Personen weiterleiten, aber sie hat die Möglichkeit, die Nachricht und alle Anlagen auf einem USB-Laufwerk oder in einer Dateiserverfreigabe zu speichern, wo sie von allen Mitgliedern der Marketinggruppe gelesen und bearbeitet werden können, sofern sie Zugriff auf diese Dateien haben. Benutzer, die nicht in der Marketinggruppe angehören, können den Inhalt nicht öffnen.

Die Anweisungen sind unter den folgenden Umständen geeignet:

-   Benutzer innerhalb der Organisation möchten Informationen mit anderen Mitarbeitern innerhalb der Organisation teilen, aber diese Informationen sollen die Organisation nicht verlassen.

-   Die weiterzuleitenden Informationen können in der E-Mail-Nachricht oder einer Anlage enthalten sein.

-   Benutzer müssen die Vorlage manuell in ihren E-Mail-Client auswählen.

## <a name="deployment-instructions"></a>Anweisungen zur Bereitstellung
![Administrator-Anweisungen für die Schnellbereitstellung von Azure RMS](../media/AzRMS_AdminBanner.png)

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, bevor Sie mit der Benutzerdokumentation fortfahren.

## <a name="requirements-for-this-scenario"></a>Anforderungen bei diesem Szenario
Damit die Anweisungen in diesem Szenario funktionieren, muss Folgendes vorhanden sein:

|Anforderungen|Wenn Sie weitere Informationen benötigen|
|---------------|--------------------------------|
|Sie haben Konten und Gruppen für Office 365 oder Azure Active Directory vorbereitet.|[Vorbereiten für Azure Information Protection](../plan-design/prepare.md)|
|Ihr Azure Information Protection-Mandantenschlüssel wird von Microsoft verwaltet. Sie verwenden nicht BYOK (Bring Your Own Key, eigenen Schlüssel verwenden).|[Planen und Implementieren Ihres Azure Information Protection-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md)|
|Azure Rights Management ist aktiviert|[Aktivieren von Azure Rights Management](../deploy-use/activate-service.md)|
|Eine der folgenden Komponenten:<br /><br />– Exchange Online ist für Azure Rights Management aktiviert<br /><br />– Der RMS-Connector ist für die lokale Exchange-Anwendung installiert und konfiguriert|Für Exchange Online: Informationen finden Sie im Abschnitt **Exchange Online: IRM-Konfiguration** unter [Office 365: Konfigurationen für Clients und Onlinedienste](../deploy-use/configure-office365.md).<br /><br />Für lokales Exchange: [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md)|
|Sie haben die Azure Rights Management-Standardvorlage **&lt;Organisation&gt; – Vertraulich** nicht archiviert. Oder Sie haben eine benutzerdefinierte Vorlage für diesen Zweck konfiguriert, da Sie eine restriktivere Einstellung benötigen oder nur eine Teilmenge der Benutzer in der Organisation die geschützten E-Mails lesen können soll.|[Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md)<br /><br />Tipp: Wenn Sie restriktivere Nutzungsrichtlinieneinstellungen für alle Benutzer in Ihrer Organisation benötigen, kopieren Sie eine der Standardvorlagen, und bearbeiten Sie diese, anstatt eine von Grund auf neue Vorlage zu erstellen.<br /><br />Aktualisierte Vorlagen werden für die E-Mail-Clients in diesem Szenario nicht sofort aktualisiert. Weitere Informationen finden Sie im Artikel [Aktualisieren von Vorlagen für Benutzer](../deploy-use/refresh-templates.md).|
|Benutzer, die die geschützte E-Mail senden, verwenden Outlook 2013 oder 2016 oder Outlook Web Access.<br /><br />Benutzer, die die E-Mail empfangen, verwenden einen E-Mail-Client, der Azure Rights Management unterstützt.|Sie können Outlook 2010 verwenden, müssen aber die [Rights Management-Freigabeanwendung für Windows installieren](../rms-client/sharing-app-admin-guide.md#automatic-deployment-for-the-microsoft-rights-management-sharing-application) und die Benutzeranweisungen entsprechend anpassen.<br /><br />Eine Liste der E-Mail-Clients, die Azure Rights Management unterstützen, finden Sie in der **E-Mail**-Spalte der Tabelle unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-applications.md).|

## <a name="user-documentation-instructions"></a>Anweisungen für Benutzerdokumentation
Verwenden Sie die folgende Vorlage, kopieren Sie die Benutzeranweisungen, und fügen Sie sie in eine Nachricht für die Endbenutzer ein. Nehmen Sie als Anpassung an Ihre Umgebung die folgenden Änderungen vor:

1.  Ersetzen Sie alle Instanzen von *&lt;Organisationsname&gt;* durch den Namen Ihrer Organisation.

2.  Ersetzen Sie alle Instanzen von *&lt;Organisationsname – Vertraulich&gt;* durch den Namen Ihre standardmäßigen oder benutzerdefinierten Vorlage.

3.  Ersetzen Sie die Screenshots, sodass sie die Namen der Vorlagen Ihrer Organisation enthalten.

4.  Ersetzen Sie die *&lt;Kontaktdetails&gt;* durch Anweisungen dazu, wie sich Benutzer an das Helpdesk wenden können, z.B. über einen Link zur Website, eine E-Mail-Adresse oder eine Telefonnummer.

5.  **Zudem können Sie folgende Änderungen vornehmen:**

    -   Wenn es der Einfachheit halber von Vorteil ist, die Anweisungen auf einen E-Mail-Client zu beschränken, löschen Sie den anderen Satz von Anweisungen.

    -   Wenn Sie anstelle der vorgeschlagenen Standardvorlage eine benutzerdefinierte Vorlage verwenden, überarbeiten Sie die Formulierung entsprechend:

        -   Verwenden Sie einen spezifischeren Titel.

        -   Geben Sie in Schritt 1 die auszuwählenden Benutzer oder Gruppen an.

        -   Geben Sie in Schritt 2 den Namen der benutzerdefinierten Vorlage an.

        -   Ändern Sie den letzten Absatz, um die für die Empfänger geltenden Einschränkungen zu erläutern.

6.  Nehmen Sie jegliche sonstigen Änderungen an den Anweisungen vor, und senden Sie sie an diese Benutzer.

7.  Da einige Clients Rights Management nicht unterstützen, müssen Sie den Empfängern dieser geschützte E-Mail-Nachrichten Anleitungen und Empfehlungen bereitstellen. Diese Informationen richten sich danach, welche Geräte und E-Mail-Anwendungen in Ihrer Organisation verwendet werden und welche Einstellungen Sie nutzen. Empfehlen Sie beispielsweise iOS-Benutzern, geschützte E-Mails anstatt mit dem systemeigenen iOS-Mail-Client vorzugsweise mit Outlook für iPad und iPhone zu lesen.

    Weitere Informationen zu den E-Mail-Clients finden Sie in der **E-Mail-Spalte** der Tabelle mit den [Funktionen der Clientgeräte](https://technet.microsoft.com/library/dn655136.aspx) unter [Voraussetzungen für Azure Rights Management](https://technet.microsoft.com/library/dn655136.aspx).

Die Beispieldokumentation veranschaulicht, wie diese Anweisungen für Benutzer nach Ihren Anpassungen aussehen können.

![Benutzerdokumentationsvorlage für die Azure RMS-Schnellbereitstellung](../media/AzRMS_UsersBanner.png)

### <a name="how-to-send-emails-that-contain-company-confidential-information-using-outlook"></a>Senden von E-Mails mit vertrauliche Unternehmensinformationen mit Outlook

1.  Erstellen Sie in Outlook eine neue E-Mail-Nachricht, fügen Sie gegebenenfalls Anlagen hinzu, und wählen Sie unter *&lt;Organisationsname&gt;* Benutzer oder Gruppen aus.

2.  Klicken Sie auf der Registerkarte **OPTIONEN** auf **Berechtigung**, und wählen Sie anschließend **&lt;Organisationsname – Vertraulich&gt;**:

    ![Ein Screenshot, der anzeigt, wie E-Mails mit vertraulichen geschäftlichen Informationen mithilfe von Outlook versendet werden](../media/AzRMS_OutlookTemplate.PNG)

3.  Senden Sie die Nachricht.

### <a name="how-to-send-emails-that-contain-company-confidential-information-using-outlook-web-app"></a>Senden von E-Mails mit vertrauliche Unternehmensinformationen mit Outlook Web App

1.  Erstellen Sie in Outlook Web App eine neue E-Mail-Nachricht, fügen Sie gegebenenfalls Anlagen hinzu, und wählen Sie unter *&lt;Organisationsname&gt;* Benutzer oder Gruppen aus dem Adressbuch aus.

2.  Klicken Sie auf **...** und auf **Berechtigungen festlegen**, und wählen Sie **&lt;Organisationsname – Vertraulich&gt;** aus:

    ![Ein Screenshot, der anzeigt, wie E-Mails mit vertraulichen geschäftlichen Informationen mithilfe von Outlook Web App versendet werden](../media/AzRMS_OWATemplate.png)

3.  Senden Sie die Nachricht.

Wenn die in den Zeilen **An**, **Cc** oder **Bcc** angegebenen Benutzer diese E-Mail empfangen, werden sie möglicherweise aufgefordert, sich zu authentifizieren, bevor sie die Nachricht lesen können. Dies stellt sicher, dass sie der Gruppe *&lt;Organisationsname&gt;* angehören. Es kann auch vorkommen, dass Benutzer nicht zur Authentifizierung aufgefordert werden, da sie bereits authentifiziert sind.

Benutzer, an die Sie die E-Mail senden, können diese zwar an andere Personen weiterleiten, lesbar ist sie jedoch nur für Benutzer der Gruppe *&lt;Organisationsname&gt;*. Wenn Sie ein Office-Dokument anfügen, gilt dafür der gleiche Schutz, selbst wenn die Anlage unter einem anderen Namen oder an einem anderen Ort gespeichert wird. Allerdings ist es authentifizierten Benutzern möglich, den Inhalt der E-Mail oder Anlage zu kopieren oder zu drucken. Wenn Sie einen restriktiveren Schutz benötigen, der derartige Aktionen verhindert, wenden Sie sich an das Helpdesk.

**Benötigen Sie Unterstützung?**

-   Wenden Sie sich an den Helpdesk:

    -   *&lt;Kontaktinformationen&gt;*

### <a name="example-customized-user-documentation"></a>Beispiel für eine angepasste Benutzerdokumentation
![Beispielbenutzerdokumentation für die Azure RMS-Schnellbereitstellung](../media/AzRMS_ExampleBanner.png)

#### <a name="how-to-send-emails-that-contain-company-confidential-information-using-outlook"></a>Senden von E-Mails mit vertrauliche Unternehmensinformationen mit Outlook

1.  Erstellen Sie in Outlook eine neue E-Mail-Nachricht, fügen Sie gegebenenfalls Anlagen hinzu, und wählen Sie im Adressbuch VanArsdel-Benutzer oder -Gruppen aus.

2.  Klicken Sie auf der Registerkarte **OPTIONEN** auf **Berechtigung**, und wählen Sie dann **VanArsdel, Ltd - Vertraulich**: aus.

    ![Ein Screenshot, der anzeigt, wie E-Mails mit vertraulichen geschäftlichen Informationen mithilfe von Outlook versendet werden](../media/AzRMS_OutlookTemplate.PNG)

3.  Senden Sie die Nachricht.

#### <a name="how-to-send-emails-that-contain-company-confidential-information-using-outlook-web-app"></a>Senden von E-Mails mit vertrauliche Unternehmensinformationen mit Outlook Web App

1.  Erstellen Sie in Outlook Web App eine neue E-Mail-Nachricht, fügen Sie gegebenenfalls Anlagen hinzu, und wählen Sie im Adressbuch VanArsdel-Benutzer oder -Gruppen aus.

2.  Klicken Sie auf **...** und dann auf **Berechtigungen festlegen**, und wählen Sie **VanArsdel, Ltd – Vertraulich** aus:

    ![Ein Screenshot, der anzeigt, wie E-Mails mit vertraulichen geschäftlichen Informationen mithilfe von Outlook Web App versendet werden](../media/AzRMS_OWATemplate.png)

3.  Senden Sie die Nachricht.

Wenn in der Zeile **An**, **Cc** oder **Bcc** angegebene Benutzer diese E-Mail empfangen, werden sie möglicherweise aufgefordert, sich zu authentifizieren, bevor sie die Nachricht lesen können. Dies stellt sicher, dass sie der Gruppe VanArsdel, Ltd angehören. Es kann auch vorkommen, dass Benutzer nicht zur Authentifizierung aufgefordert werden, da sie bereits authentifiziert sind.

Benutzer, an die Sie die E-Mail senden, können diese zwar an andere Personen weiterleiten, lesbar ist sie jedoch nur für Benutzer der Gruppe VanArsdel. Wenn Sie ein Office-Dokument anfügen, gilt dafür der gleiche Schutz, selbst wenn die Anlage unter einem anderen Namen oder an einem anderen Ort gespeichert wird. Allerdings ist es authentifizierten Benutzern möglich, den Inhalt der E-Mail oder Anlage zu kopieren oder zu drucken. Wenn Sie einen restriktiveren Schutz benötigen, der derartige Aktionen verhindert, wenden Sie sich an das Helpdesk.

**Benötigen Sie Unterstützung?**

-   Wenden Sie sich an den Helpdesk:

    -   E-Mail: helpdesk@vanarsdelltd.com

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

