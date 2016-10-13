---
title: "Registrieren von Benutzern für RMS for Individuals | Azure Information Protection"
description: "Anweisungen zur Registrierung für dieses kostenlose Konto und technische Informationen zur Funktionsweise dieses Verfahrens."
author: cabailey
manager: mbaldwin
ms.date: 10/05/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a60731bd-f78d-4f00-bb3e-354637b312ab
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 78b975c2babad347fc5be7956d504c7283508962
ms.openlocfilehash: 093bce2835b0606c127d9bcecab5ec353160833c


---

# Registrieren für RMS for Individuals

>*Gilt für: Azure Information Protection*

Um sich für dieses kostenlose Konto zu registrieren, müssen Sie die Seite [Microsoft Azure Rights Management-Seite](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload) aufrufen Ihre geschäftliche E-Mail-Adresse angeben. Der häufigste Auslöser dafür, dass Sie zu dieser Anmeldeseite weitergeleitet werden, ist, dass Sie eine E-Mail-Nachricht mit einem geschützten Anhang empfangen haben, die Anweisungen enthält, wie Sie sich registrieren können. Sie erhalten eine E-Mail als Antwort von Microsoft und können den Registrierungsprozess dann abschließen, indem Sie Details eingeben, um Ihr Konto zu erstellen. Wenn dies abgeschlossen ist, wird eine Seite angezeigt, auf der Sie die Freigabeanwendung für verschiedene Geräte herunterladen können sowie ein Link zum Benutzerhandbuch und ein Link für eine aktuelle Liste der Anwendungen, die den Rights Management-Schutz nativ unterstützen. 

## So registrieren Sie sich für RMS for Individuals

1.  Rufen Sie auf einem Windows- oder Mac-Computer oder einem mobilen Gerät die Seite [Microsoft Azure Rights Management](https://portal.office.com/signup?sku=rms&ru=https%3A%2F%2Fportal.azurerms.com%2F%23%2Fdownload) auf.

2.  Geben Sie die E-Mail-Adresse ein, die Sie für Ihre Organisation verwenden, z. B. **janetm@contoso.com** oder **p.dover@fabrikam.com**.

    > [!IMPORTANT]
    > Private E-Mail-Konten werden nicht unterstützt. Geben Sie also kein Microsoft-Konto (früher Microsoft Live ID-Konto) oder ein anderes privates Konto ein, das Sie zu Hause von Ihrem Internetanbieter verwenden.

3.  Klicken Sie auf **Registrieren**.

    Microsoft prüft anhand Ihrer E-Mail-Adresse, ob Ihre Organisation bereits ein [kostenpflichtiges Abonnement hat, das Azure RMS umfasst](../get-started/requirements-subscriptions.md). Wenn dies der Fall ist, benötigen Sie RMS for Individuals nicht, und Sie werden sofort angemeldet, und die Self-Service-Registrierung für RMS for Individuals wird abgebrochen. Wird kein kostenpflichtiges Abonnement für Azure RMS gefunden, führen Sie den nächsten Schritt aus.

4.  Warten Sie darauf, dass eine Bestätigungs-E-Mail an die von Ihnen angegebene Adresse gesendet wird. Diese E-Mail wird vom Office 365-Team (support@email.microsoftonline.com) versendet und hat den Betreff **Finish signing up for Microsoft Azure Rights Management** (Registrierung für Microsoft Azure Rights Management beenden).

5.  Wenn Sie die E-Mail erhalten, klicken Sie auf **Yes, that‘s me** (Ja, das bin ich), um Ihre E-Mail-Adresse zu bestätigen und den Registrierungsprozess abzuschließen.

6.  Es wird nun eine Seite **Nur noch eines...** angezeigt, mit der Sie Details zu Ihrem Konto angeben. Geben Sie Ihren Vornamen, Ihren Nachnamen und ein Kennwort Ihrer Wahl ein, und klicken Sie auf **Start**.

7. Wenn Ihr Konto erstellt wurde, wird eine neue Microsoft Rights Management-Seite angezeigt, von der Sie die Freigabeanwendung herunterladen und installieren können. Klicken Sie alternativ auf den Link [Weitere Informationen](../rms-client/sharing-app-user-guide.md), um das Handbuch für die Freigabeanwendung zu lesen.

Nun ist Ihr Konto erstellt, und Sie sind bereit, um Dateien zu schützen und von anderen geschützte Dateien zu lesen. Falls Sie aufgefordert werden, sich anzumelden, um Dateien zu schützen oder geschützte Dateien zu lesen, geben Sie dieselbe E-Mail-Adresse und dasselbe Kennwort ein, mit denen Sie das Konto für RMS for Individuals erstellt haben.

## Technische Übersicht über den Anmeldevorgang
RMS for Individuals verwendet einen Self-Service-Registrierungsprozess, der auch von anderen Diensten verwendet wird, die Cloudtechnologie von Microsoft zur Authentifizierung von Benutzern verwenden.

Dies geschieht im Hintergrund, wenn sich ein Benutzer für RMS for Individuals registriert und seine Organisation kein Office 365-Abonnement oder Azure-Abonnement besitzt und daher auch kein Verzeichnis in Azure, um Benutzer zu authentifizieren:

1.  Wenn der erste Benutzer einer Organisation ein Abonnement für RMS for Individuals anfordert, wird der in der E-Mail-Adresse angegebene Domänenname überprüft, um festzustellen, ob er bereits einem Azure-Mandanten zugeordnet ist. Ist kein Mandant vorhanden, wird automatisch ein neuer Mandant und ein neues Azure-Verzeichnis für die Organisation erstellt, die ein Konto für diesen ersten Benutzer enthält. Im Gegensatz zu einem kostenpflichtigen Abonnement für Azure ist dieses erste Konto kein globaler Administrator, sondern ein Standardbenutzer. Das neue Konto verwendet die E-Mail-Adresse und das Kennwort, das der Benutzer angegeben hat.

    > [!NOTE]
    > Manche Domänennamen können nicht zum Erstellen des Verzeichnisses verwendet werden, weshalb sie auch nicht für RMS for Individuals verwendet werden können.

    Wurde ein vorhandener Mandant gefunden, wird er überprüft, um zu festzustellen, ob er bereits ein Abonnement für Azure RMS hat. Wird kein Abonnement gefunden, kann das kostenlose RMS for Individuals-Abonnement hinzugefügt werden.

2.  Der Organisation wird das RMS for Individuals-Abonnement gewährt. Nun kann dieser Benutzer von Azure authentifiziert werden und Azure Rights Management dazu verwenden, Dateien zu schützen sowie Dateien zu lesen, die von anderen geschützt wurden. Um Dateien zu schützen und geschützte Dateien zu lesen, muss der Benutzer eine RMS-fähige Anwendung haben, beispielsweise die kostenlose [Rights Management-Freigabeanwendung](../rms-client/sharing-app-windows.md).

3.  Wenn der zweite Benutzer aus derselben Organisation ein RMS for Individuals-Abonnement anfordert, wird dem zuvor erstellten Azure-Verzeichnis ein neues Benutzerkonto hinzugefügt, indem das RMS for Individuals-Abonnement der Organisation verwendet wird. Dieser zweite Benutzer kann alle Aktionen ausführen, die auch der erste Benutzer ausführen kann (Dateien schützen und geschützte Dateien lesen), aber zusätzlich können diese beiden Benutzer nun einfacher sicher zusammenarbeiten, weil sie schnell Standardvorlagen auf Dateien anwenden können, die den Zugriff auf Konten im Azure-Verzeichnis ihrer Organisation einschränken.

4.  Nachfolgende Benutzer aus derselben Organisation folgen demselben Muster, und dem Azure-Verzeichnis der Organisation werden (wenn sich neue Benutzer registrieren) Benutzerkonten hinzugefügt. Je mehr Konten dem Verzeichnis hinzugefügt werden, desto mehr Benutzer können sicher mit Kollegen und Partnern zusammenarbeiten und einfacher verhindern, dass nicht autorisierte Personen ihre Dateien lesen, die keinen Zugriff darauf haben sollten.

Während des gesamten Prozesses fallen keine Kosten für die Organisation an, und es ist keine Arbeit seitens der IT-Abteilung erforderlich. Die IT-Abteilung kann allerdings, wenn sie möchte, die folgenden Aktionen ausführen:

-   **Verwalten der Konten und des Anmeldevorgangs**: IT-Administratoren können den Besitz der automatisch erstellten Verzeichnisse und Konten in Azure übernehmen. Sie können dann die Konten verwalten, indem sie Verzeichnisintegrationslösungen wie Kennwortsynchronisierung und einmaliges Anmelden implementieren. Oder sie können Benutzer daran hindern, Konten zu erstellen oder sich für RMS for Individuals zu registrieren.

    Weitere Informationen finden Sie unter [Möglichkeiten der Kontrolle über die für RMS for Individuals erstellten Konten durch Administratoren](rms-for-individuals-take-control.md).

-   **Verwalten von Rights Management**: IT-Administratoren können das RMS for Individuals-Abonnement für die Organisation in ein kostenpflichtiges Abonnement umwandeln, das Azure Rights Management enthält. Wenn sie dies tun, bleiben das vorhandene Azure-Verzeichnis und die Konten erhalten, um einen nahtlosen Übergang von vorhandenen Benutzern, die bisher RMS for Individuals verwendet haben, zu gewährleisten. Alle Dateien, die zuvor geschützt waren, bleiben mit denselben Richtlinien geschützt, und die Personen, denen Berechtigungen für die Nutzung der Dateien gewährt wurden, können die Dateien weiterhin auf dieselbe Weise verwenden.

    Wenn Sie so vorgehen, profitiert Ihre Organisation davon, dass sie in der Lage ist, Rights Management in die eigenen Workflows, Dienste und Datenspeicher zu integrieren. Zusätzlich können Sie dann Rights Management verwalten, weil Sie die Kontrolle über den Mandantenschlüssel Ihrer Organisation für Azure Rights Management haben. Sie können jetzt Folgendes machen:

    -   Exchange und SharePoint so konfigurieren, dass Azure Rights Management auch bei lokaler Ausführung unterstützt wird. Exchange und SharePoint werden für die Online Services systemeigen unterstützt sowie von einem Connector für die lokalen Server. Weitere Informationen finden Sie unter den folgenden Links:

        -   Abschnitte zu Exchange Online und SharePoint Online unter [Office 365: Konfigurationen für Clients und Onlinedienste](../deploy-use/configure-office365.md)

        -   [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md)

    -   Führen Sie eine eDiscovery in den unternehmenseigenen Daten durch, damit Sie ggf. Dateien entschlüsseln können, die mithilfe von Rights Management geschützt wurden. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md).

    -   Alle Aktivitäten für Rights Management protokollieren, wie sie in Ihrer Organisation verwendet werden. Dies ist sehr leistungsfähig, weil Sie nicht nur überwachen können, welche Dateien geschützt werden und wer erfolgreich auf diese geschützten Dateien zugreift, sondern auch potenziell verdächtiges Verhalten nicht autorisierter Personen identifizieren können, die versuchen, auf geschützte Dateien zuzugreifen. Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Verwendung des Azure Rights Management-Diensts](../deploy-use/log-analyze-usage.md).

    -   Geben Sie Benutzern die Möglichkeit, ihre geschützten Dokumente nachzuverfolgen und zu widerrufen, sofern diese Features von Ihrem [Azure RMS-Abonnement](https://technet.microsoft.com/dn858608)unterstützt werden. Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen von Dateien](../rms-client/sharing-app-track-revoke.md) im [Rights Management-Freigabeanwendung – Benutzerhandbuch](../rms-client/sharing-app-user-guide.md).

    -   Eine BYOK-Lösung (Bring Your Own Key) implementieren, sodass Ihr Mandantenschlüssel für Azure Rights Management lokal und gemäß Ihren IT-Richtlinien generiert und sicher unter Verwendung eines HSM (Hardwaresicherheitsmodul) an Microsoft übertragen wird. Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).


## Nächste Schritte
Weitere Informationen finden Sie unter [Möglichkeiten der Kontrolle über die für RMS for Individuals erstellten Konten durch Administratoren](rms-for-individuals-take-control.md).





<!--HONumber=Oct16_HO1-->


