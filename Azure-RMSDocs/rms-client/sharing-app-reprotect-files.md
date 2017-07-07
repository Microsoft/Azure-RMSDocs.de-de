---
title: "Ändern von Berechtigungen für RMS-geschützte Dateien – AIP"
description: "Wenn eine Datei mit Rights Management geschützt wurde, können Sie die Berechtigungen ändern, indem Sie die Datei erneut schützen. Dabei können Sie angeben, welche Benutzer Zugriff auf die Datei erhalten und über welche Berechtigungen sie verfügen sollen."
keywords: 
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 5ac121b3-d7a0-40e4-8fe7-90bf4cf796f1
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3290b9436f75c2d0d37c401dd2e0be11bcf2d554
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="change-permissions-on-files-that-have-been-protected-by-rights-management"></a>Ändern von Berechtigungen für Dateien, die mit Rights Management geschützt wurden

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Wenn eine Datei mit Rights Management geschützt wurde, können Sie die Berechtigungen ändern, indem Sie die Datei erneut schützen. Dabei können Sie angeben, welche Benutzer Zugriff auf die Datei erhalten und über welche Berechtigungen sie verfügen sollen.

> [!IMPORTANT]
> Dies ist keine schrittweise Änderung, sondern die Einstellungen werden vollständig überschrieben. Sie schützen die Datei vollständig neu, und zwar mit dem vollständigen gewünschten Satz an Berechtigungen.
> 
>  Wenn der Dateischutz z.B. ausschließlich zulässt, dass die Marketing-Abteilung die Datei öffnen kann, Sie die Datei aber auch für die Vertriebsabteilung freigeben wollen, müssen Sie die Datei erneut schützen, damit beide Abteilungen auf die Datei zugreifen können.
>
> Wenn Sie eine Berechtigung hinzufügen oder entfernen möchten, dürfen Sie nicht bloß die Berechtigung angeben, die Sie hinzufügen oder entfernen möchten, sondern Sie müssen alle Berechtigungen angeben, über die die angegebenen Benutzer verfügen sollen.

Wenn Sie der Besitzer der erneut zu schützenden Datei sind (die ursprünglich z.B. mithilfe der Freigabeanwendung geschützt wurde), verfügen Sie automatisch über die Berechtigung, die Datei erneut zu schützen. Wenn Sie nicht der Besitzer sind, hängt Ihre Berechtigung, die Datei erneut zu schützen, von den aktuellen Berechtigungen der geschützten Datei ab. Sie müssen über das [Nutzungsrecht „Vollzugriff“](../deploy-use/configure-usage-rights.md#usage-rights-and-descriptions) verfügen, um eine Datei erneut schützen zu können.

Angenommen, eine andere Person hat die Datei mithilfe der Rights Management-Freigabeanwendung geschützt und eine Gruppe, der Sie angehören, und einen **Mitbesitzer** als benutzerdefinierte Berechtigung angegeben, dann verfügen Sie über die Berechtigung, die Datei erneut zu schützen. Wenn jedoch weder Ihr Name noch eine Gruppe, der Sie angehören, angegeben wurde oder wenn **Prüfer - Anzeigen und Bearbeiten** oder eine Vorlage aktiviert wurde, die nicht zulässt, dass Sie Berechtigungen entfernen, dann sind Sie nicht in der Lage, die Datei erneut zu schützen. Der einfachste Weg, dies zu ermitteln, ist der Versuch, die Datei erneut zu schützen.

Weitere Informationen zum vollständigen Entfernen aller Berechtigungen, sodass die Datei nicht länger geschützt wird, finden Sie unter [Entfernen des Schutzes von einer Datei](sharing-app-remove-protection.md).

## <a name="to-re-protect-a-file-in-place"></a>So schützen Sie eine Datei direkt erneut

1.  Wählen Sie im Datei-Explorer eine Datei aus, die Sie schützen möchten. Klicken Sie mit der rechten Maustaste, und wählen Sie **Mit RMS schützen** und anschließend **Direkt schützen** aus. Beispiel:

    ![Menüoption für direkt schützen](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Wenn die Option **Mit RMS schützen** nicht angezeigt wird, ist es wahrscheinlich, dass die RMS-Freigabeanwendung nicht auf Ihrem Computer installiert ist oder der Computer neu gestartet werden muss, um die Installation abzuschließen. Weitere Informationen zum Installieren der RMS-Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

2.  Führen Sie eines der folgenden Verfahren aus:

    -   Wählen Sie eine Richtlinienvorlage aus: Hierbei handelt es sich um vordefinierte Berechtigungen, die üblicherweise den Zugriff und die Verwendung auf Personen in Ihrer Organisation beschränken. Wenn der Name Ihrer Organisation z.B. „Contoso, Ltd“ lautet, wird unter Umständen **Contoso, Ltd – Nur vertrauliche Ansicht** angezeigt. Falls dies das erste Mal ist, dass Sie eine Datei auf diesem Computer geschützt haben, müssen Sie zunächst **Unternehmensdefinierter Schutz** auswählen, um die Vorlagen herunterzuladen.

        Wenn Sie das nächste Mal auf die Option **Direkt schützen** klicken, werden Ihnen bis zu 10 Vorlagen zur Auswahl angezeigt. Wenn mehr als 10 Vorlagen vorhanden sind und die gewünschte nicht angezeigt wird, klicken Sie auf **Unternehmensdefinierter Schutz**, um alle Vorlagen anzuzeigen und herunterzuladen.

        Wenn Sie eine Richtlinienvorlage auswählen, können Sie auch mehrere Dateien und Ordner schützen. Wenn Sie einen Ordner auswählen, werden alle Dateien in diesem Ordner automatisch für den Schutz ausgewählt, aber neue Dateien, die Sie in diesem Ordner erstellen, werden nicht automatisch geschützt.

    -   Wählen Sie **Benutzerdefinierte Berechtigungen**aus: Wählen Sie diese Option aus, wenn die Vorlagen nicht das Maß an Schutz bieten, das Sie benötigen, oder wenn Sie die Schutzoptionen explizit selbst festlegen möchten. Geben Sie die gewünschten Optionen für diese Datei im Dialogfeld [Schutz hinzufügen](sharing-app-dialog-box.md) an, und klicken Sie dann auf **Übernehmen**.

3. Wenn Sie nicht über die Berechtigungen verfügen, die Datei erneut zu schützen, wird Ihnen die Nachricht **Unable to protect content** (Der Inhalt konnte nicht geschützt werden.) zusammen mit der E-Mail-Adresse der Kontaktperson (der Besitzer des Dokuments) angezeigt, bei der Sie eine Änderung der Berechtigungen veranlassen können.

    Sollten Sie über die Berechtigung zum erneuten Schützen der Datei verfügen, wird sehr schnell ein Dialogfeld mit der Meldung angezeigt, dass die Datei geschützt wird, und der Fokus wird anschließend an den Datei-Explorer zurückgegeben. Die ausgewählte(n) Datei(en) ist bzw. sind nun mit Ihren Änderungen geschützt. 

> [!NOTE]
> Bevor Sie die Datei erneut schützen können, muss der Rights Management-Dienst erst bestätigen, dass Sie dazu berechtigt sind. Dazu überprüft er Ihren Benutzernamen und Ihr Kennwort. In einigen Fällen können Ihre Anmeldeinformationen zwischengespeichert sein, und Sie sehen keine Eingabeaufforderung, in der nach diesen Informationen gefragt wird. In anderen Fällen werden Sie aufgefordert, Ihre Anmeldeinformationen einzugeben.
>
> Wenn Ihre Organisation weder Azure Information Protection noch AD RMS verwendet, können Sie ein kostenloses Konto beantragen, für das Ihre Anmeldeinformationen akzeptiert werden, sodass Sie von RMS geschützte Dateien verwenden können:
>
> -   Um dieses Konto zu beantragen, klicken Sie auf den Link, um [RMS for Individuals](http://go.microsoft.com/fwlink/?LinkId=309469)zu beantragen.
>
>     Wenn Sie sich anmelden, verwenden Sie Ihre Unternehmens-E-Mail-Adresse anstelle einer privaten E-Mail-Adresse. Wenn Sie sich anmelden, weil Sie per E-Mail eine geschützte Dateianlage erhalten haben, verwenden Sie die E-Mail-Adresse, die zum Senden der E-Mail-Nachricht an Sie verwendet wurde.
> -   Weitere Informationen finden Sie unter [RMS for Individuals und Azure Rights Management](../understand-explore/rms-for-individuals.md).

## <a name="to-re-protect-a-file-that-you-have-emailed"></a>So schützen Sie eine Datei erneut, die Sie per E-Mail versendet haben

Wenn Sie Berechtigungen für eine Datei ändern möchten, die Sie per E-Mail versendet haben, gehen Sie wie folgt vor:

- **So richten Sie für einen größeren Personenkreis einen Lesezugriff auf die Datei ein**: Senden Sie ihnen die Datei per E-Mail, wie unter [Schützen einer per E-Mail freigegebenen Datei](sharing-app-protect-by-email.md) beschrieben.

- **So ändern Sie die Berechtigungen für die Datei**: Senden Sie die Datei erneut per E-Mail, wie unter [Schützen einer per E-Mail freigegebenen Datei](sharing-app-protect-by-email.md) beschrieben, und wählen Sie die neuen, gewünschten Berechtigungen aus. 

    Sie können die vorherigen Berechtigungen für die ursprünglich per E-Mail versandte Datei nicht löschen, sondern nur durch neue ersetzen. Deshalb sollten Sie in Erwägung ziehen die zuvor per E-Mail gesandte Datei zurückzurufen, damit die Empfänger diese Dokumentversion nicht mehr öffnen können. Eine Widerrufung ist angebracht, wenn Sie die Berechtigungen restriktiver gestalten müssen (z.B. Personen entfernen müssen, die keinen Zugriff mehr auf die Datei haben sollten oder sie nicht mehr bearbeiten können sollten).

    Weitere Informationen zur Widerrufung einer per E-Mail versendeten Datei finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente](sharing-app-track-revoke.md).


## <a name="examples-and-other-instructions"></a>Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Siehe auch
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]