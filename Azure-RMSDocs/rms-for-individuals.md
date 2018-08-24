---
title: RMS for individuals und Azure Information Protection
description: Informationen zu RMS for Individuals, einem kostenlosen Self-Service-Abonnement für Benutzer, denen vertrauliche Dateien zugesandt wurden, die aber nicht authentifiziert werden können, da die für die Benutzer zuständige IT-Abteilung kein Konto in Azure verwaltet.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 07/17/2018
ms.topic: article
ms.service: information-protection
ms.assetid: 2efcb440-fefd-45e9-872b-f471573aadf2
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: c64cd1fc572e8d7b70db5291a963d3178e599c0c
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42806935"
---
# <a name="rms-for-individuals-and-azure-information-protection"></a>RMS for individuals und Azure Information Protection

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

RMS for Individuals ist ein kostenloses Self-Service-Abonnement für Benutzer, die durch Azure Information Protection geschützte Dateien öffnen müssen. Wenn diese Benutzer nicht von Azure Active Directory authentifiziert werden können, kann dieser kostenlose Anmeldedienst ein Konto für einen Benutzer in Azure Active Directory erstellen. Solche Benutzer können sich nun mit ihrer geschäftlichen E-Mail-Adresse authentifizieren und anschließend die geschützten Dateien auf einem Computer oder mobilen Gerät lesen.

RMS for Individuals verwendet die Azure Active Directory-Self-Service-Registrierung. Wenn Benutzer mithilfe dieses Abonnements Konten für Ihr Unternehmen erstellt haben, können Sie als Administrator für Ihr Unternehmen den Besitz dieser Konten beanspruchen, und die [Kontrolle über diese Konten übernehmen](/active-directory/domains-admin-takeover#external-admin-takeover). 


> [!NOTE]
> Das kostenlose Abonnement stellt eine Möglichkeit dar, sicherzustellen, dass autorisierte Personen außerhalb Ihrer Organisation jederzeit Dateien lesen können, die durch Ihre Organisation geschützt werden. Eine weitere Möglichkeit besteht in dem Senden von Dokumenten per E-Mail mithilfe der [Office 365-Nachrichtenverschlüsselung mit neuen Funktionen](https://support.office.com/article/7ff0c040-b25c-4378-9904-b1b50210d00e). Diese E-Mail-Lösung kann für sämtliche E-Mail-Adressen auf allen Geräten verwendet werden und wird zur sicheren Freigabe von Informationen und zur Anzeige von Office-Dokumenten empfohlen, die über einen Browser für Personen außerhalb Ihrer Organisation freigegeben werden.
> 
> Eine andere Möglichkeit ist die Verwendung von Microsoft-Konten. Es können jedoch nicht alle Anwendungen geschützten Inhalt öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents) 

Um sich für dieses kostenlose Konto zu registrieren, rufen Benutzer die Seite [Microsoft Azure Information Protection](https://aka.ms/rms-signup) auf und geben Ihre geschäftliche E-Mail-Adresse an. Sie erhalten eine E-Mail als Antwort von Microsoft, und können den Registrierungsprozess dann abschließen, indem sie die Angaben machen, um ihr Konto zu erstellen. 

Wenn das Konto erstellt wurde, finden Sie auf der letzten Seite Links zum Herunterladen des Azure Information Protection-Clients oder -Viewers, einen Link zum Benutzerhandbuch und einen Link zu einer aktuellen Liste der Anwendungen, die den Rights Management-Schutz nativ unterstützen. 

## <a name="to-sign-up-for-rms-for-individuals"></a>So registrieren Sie sich für RMS for Individuals

1. Rufen Sie auf einem Windows- oder Mac-Computer oder mobilen Gerät die Seite [Microsoft Azure Information Protection](https://aka.ms/rms-signup) auf.

2. Geben Sie die E-Mail-Adresse ein, die zum Schützen des Dokuments verwendet wurde, das Sie öffnen möchten.

3. Klicken Sie auf **Registrieren**.

    Microsoft verwendet Ihre E-Mail-Adresse, um zu überprüfen, ob Ihre Organisation bereits über ein [Abonnement für Azure Information Protection Premium](https://www.microsoft.com/cloud-platform/azure-information-protection-pricing) oder ein [Office 365-Abonnement mit Datenschutz per Azure Rights Management](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf) verfügt. Wenn eines dieser beiden Abonnements gefunden wird, ist es nicht nötig, dass Sie über RMS for Individuals verfügen. Sie werden sofort angemeldet, und die Self-Service-Registrierung für RMS for Individuals wird abgebrochen. Wird eines dieser Abonnements nicht gefunden, fahren Sie mit dem nächsten Schritt fort.

4. Warten Sie darauf, dass eine Bestätigungs-E-Mail an die von Ihnen angegebene Adresse gesendet wird. Diese E-Mail wird vom Office 365-Team (support@email.microsoftonline.com) gesendet und hat den Betreff **Finish signing up for Microsoft Azure Information Protection** (Registrierung für Microsoft Azure Information Protection beenden).

5. Wenn Sie die E-Mail erhalten, klicken Sie auf **Yes, that‘s me** (Ja, das bin ich), um Ihre E-Mail-Adresse zu bestätigen und den Registrierungsprozess abzuschließen.

6. Es wird nun eine Seite **Nur noch eines...** angezeigt, mit der Sie Details zu Ihrem Konto angeben. Geben Sie Ihren Vornamen, Ihren Nachnamen und ein Kennwort Ihrer Wahl ein, und klicken Sie auf **Start**.

7. Wenn Ihr Konto erstellt wurde, wird Ihnen eine neue Microsoft Azure Information Protection-Seite angezeigt, über die Sie den Azure Information Protection-Client herunterladen und installieren können. Sie können auch auf den Link zum [Benutzerhandbuch](./rms-client/client-user-guide.md) klicken, um eine Anleitung für Windows-Computer zu erhalten.

Wenn Sie nach Erstellung des Kontos aufgefordert werden, sich anzumelden, um geschützte Dateien zu lesen, geben Sie dieselben Informationen – E-Mail-Adresse und Kennwort – ein, mit denen Sie das Konto für RMS for Individuals erstellt haben.

> [!IMPORTANT]
> Sie können jetzt mit diesem Konto auch Dateien schützen; dies sollten Sie jedoch erst tun, wenn Ihre Organisation über ein [Testabonnement oder gebührenpflichtiges Abonnement](https://azure.microsoft.com/pricing/details/information-protection/) für Azure Information Protection verfügt. Wenn Sie Dateien und E-Mails mit diesem kostenlosen Abonnement schützen und Ihre Organisation dann die Kontrolle über Ihr Konto übernimmt, kann auf zuvor geschützte Inhalte möglicherweise nicht mehr zugegriffen werden.


## <a name="next-steps"></a>Nächste Schritte
RMS for Individuals ist ein Beispiel für eine Self-Service-Anmeldung, die von Azure Active Directory unterstützt wird. Weitere Informationen zur Funktionsweise finden Sie unter [Was ist die Self-Service-Registrierung für Azure?](/active-directory/active-directory-self-service-signup) in der Dokumentation zu Azure Active Directory.

