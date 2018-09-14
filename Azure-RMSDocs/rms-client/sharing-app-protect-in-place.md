---
title: Direkter Schutz mithilfe der RMS-Freigabeanwendung – AIP
description: Anweisungen zum sicheren Speichern einer Datei auf Ihrem Computer, einem Server oder einem anderen Speichergerät.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 33920329-5247-4f6c-8651-6227afb4a1fa
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 218f20f7ad42b3f7b6e1a47a8c1f57556df612c3
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44150720"
---
# <a name="protect-a-file-on-a-device-protect-in-place-by-using-the-rights-management-sharing-application"></a>Schützen einer Datei auf einem Gerät (direkt schützen) durch Verwenden der Rights Management-Freigabeanwendung

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1*

Wenn Sie eine Datei direkt schützen, wird die ursprüngliche, nicht geschützte Datei ersetzt. Sie können die Datei dann dort belassen, wo sie ist, sie in einen anderen Ordner oder auf ein anderes Gerät kopieren oder den Ordner freigeben, in dem sie sich befindet. Die Datei bleibt in jedem Fall geschützt. Sie können die geschützte Datei auch an eine E-Mail anfügen, aber es empfiehlt sich, eine geschützte Datei direkt aus dem Datei-Explorer oder aus einer Office-Anwendung per E-Mail freizugeben. (Weitere Informationen finden Sie unter [Schützen einer per E-Mail freigegebenen Datei mithilfe der Rights Management-Freigabeanwendung](sharing-app-protect-by-email.md).)

> [!TIP]
> Werden Fehler angezeigt, wenn Sie versuchen, Dateien zu schützen, sollten Sie [Häufig gestellte Fragen (FAQ) zur Rights Management-Freigabeanwendung für Windows](http://go.microsoft.com/fwlink/?LinkId=303971)lesen.

## <a name="to-protect-a-file-on-a-device-protect-in-place"></a>So schützen Sie eine Datei auf einem Gerät (direkt schützen)

1.  Wählen Sie im Datei-Explorer eine Datei aus, die Sie schützen möchten. Klicken Sie mit der rechten Maustaste, und wählen Sie **Mit RMS schützen** und anschließend **Direkt schützen** aus. Beispiel:

    ![Menüoption für direkt schützen](../media/ADRMS_MSRMSApp_SP_CompanyDefined.png)

    > [!NOTE]
    > Wenn die Option **Mit RMS schützen** nicht angezeigt wird, ist es wahrscheinlich, dass die RMS-Freigabeanwendung nicht auf Ihrem Computer installiert ist oder der Computer neu gestartet werden muss, um die Installation abzuschließen. Weitere Informationen zum Installieren der RMS-Freigabeanwendung finden Sie unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

2.  Führen Sie eines der folgenden Verfahren aus:

    -   Wählen Sie eine Richtlinienvorlage aus: Hierbei handelt es sich um vordefinierte Berechtigungen, die üblicherweise den Zugriff und die Verwendung auf Personen in Ihrer Organisation beschränken. Wenn der Name Ihrer Organisation z.B. „Contoso, Ltd“ lautet, wird unter Umständen **Contoso, Ltd – Nur vertrauliche Ansicht** angezeigt. Falls dies das erste Mal ist, dass Sie eine Datei auf diesem Computer geschützt haben, müssen Sie zunächst **Unternehmensdefinierter Schutz** auswählen, um die Vorlagen herunterzuladen.

        Wenn Sie das nächste Mal auf die Option **Direkt schützen** klicken, werden Ihnen bis zu 10 Vorlagen zur Auswahl angezeigt. Wenn mehr als 10 Vorlagen vorhanden sind und die gewünschte nicht angezeigt wird, klicken Sie auf **Unternehmensdefinierter Schutz**, um alle Vorlagen anzuzeigen und herunterzuladen.

        Wenn Sie eine Richtlinienvorlage auswählen, können Sie auch mehrere Dateien und Ordner schützen. Wenn Sie einen Ordner auswählen, werden alle Dateien in diesem Ordner automatisch für den Schutz ausgewählt, aber neue Dateien, die Sie in diesem Ordner erstellen, werden nicht automatisch geschützt.

    -   Wählen Sie **Benutzerdefinierte Berechtigungen**aus: Wählen Sie diese Option aus, wenn die Vorlagen nicht das Maß an Schutz bieten, das Sie benötigen, oder wenn Sie die Schutzoptionen explizit selbst festlegen möchten. Geben Sie die gewünschten Optionen für diese Datei im Dialogfeld [Schutz hinzufügen](sharing-app-dialog-box.md) an, und klicken Sie dann auf **Übernehmen**.

3.  Möglicherweise wird sehr schnell ein Dialogfeld mit der Meldung angezeigt, dass die Datei geschützt wird, und der Fokus wird dann an den Datei-Explorer zurückgegeben. Die ausgewählten Dateien sind nun geschützt. In einigen Fällen (wenn die Dateinamenerweiterung durch Hinzufügen des Schutzes geändert wird) wird die ursprüngliche Datei im Datei-Explorer durch eine neue Datei mit dem Schlosssymbol für den Rights Management-Schutz ersetzt. Beispiel:

    ![Geschützte Datei mit Schlosssymbol für die RMS-Freigabeanwendung](../media/ADRMS_MSRMSApp_Pfile.png)

Wenn Sie Ihre Meinung hinsichtlich der Berechtigungen ändern oder die Berechtigungen später ändern müssen, schützen Sie die Datei einfach erneut.

Wenn Sie später den Schutz einer Datei aufheben müssen, gehen Sie entsprechend den Beschreibungen unter [Entfernen des Schutzes von einer Datei mithilfe der Rights Management-Freigabeanwendung](sharing-app-remove-protection.md) vor.

## <a name="examples-and-other-instructions"></a>Beispiele und weitere Anweisungen
Beispiele für die Verwendung der Rights Management-Freigabeanwendung sowie weitere Anweisungen finden Sie in den folgenden Abschnitten des Benutzerhandbuchs für die Rights Management-Freigabeanwendung

-   [Beispiele für die Nutzung der RMS-Freigabeanwendung](sharing-app-user-guide.md#examples-for-using-the-rms-sharing-application)

-   [Was möchten Sie tun?](sharing-app-user-guide.md#what-do-you-want-to-do)

## <a name="see-also"></a>Siehe auch
[Rights Management-Freigabeanwendung – Benutzerhandbuch](sharing-app-user-guide.md)
