---
title: Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android
description: ''
keywords: Einige häufig gestellte Fragen, die Ihnen beim Verwenden der Azure Information Protection-App für iOS und Android helfen sollen
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/21/2018
ms.topic: article
ms.prod: azure
ms.service: information-protection
ms.technology: techgroup-identity
ms.custom: askipteam
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 09e75b1d8fd841295924dccfbacf8dcb6d753182
ms.sourcegitcommit: 949bf02d5d12bef8e26d89ad5d6a0d5cc7826135
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/02/2018
ms.locfileid: "39473473"
---
# <a name="faqs-for-microsoft-azure-information-protection-app-for-ios-and-android"></a>Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android

*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Auf dieser Seite finden Sie Antworten auf einige häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android.

## <a name="what-can-i-do-with-the-azure-information-protection-app"></a>Was kann ich mit der Azure Information Protection-App machen?

Mit dieser App können Sie durch Rechte geschützte E-Mail-Nachrichten anzeigen (RPMSG-Dateien), wenn Ihre E-Mail-App von sich aus keinen Datenschutz durch Rechteverwaltung unterstützt. Mit dieser App können Sie außerdem durch Rechte geschützte PDF-Dateien, Bilder und Textdateien anzeigen. Derzeit können Sie mit dieser App keine neuen geschützten E-Mail-Nachrichten erstellen oder beantworten und keine geschützten Dateien erstellen oder bearbeiten.

## <a name="can-i-open-pdf-files-that-are-in-sharepoint-protected-libraries-and-onedrive-for-business"></a>Kann ich PDF-Dateien aus geschützten SharePoint-Bibliotheken und OneDrive for Business öffnen?

Ja, Sie können geschützte PDF-Dateien öffnen, die andere über SharePoint und OneDrive for Business für Sie freigegeben haben. Tippen Sie auf den Link, und wählen Sie diese App für das Öffnen der Datei aus. 

Diese App kann auch PDF-Dateien öffnen, die außerhalb von SharePoint und OneDrive for Business geschützt wurden (geschützte PDF- und PPDF-Dateien).

## <a name="can-my-mobile-device-run-the-azure-information-protection-app"></a>Kann die Azure Information Protection-App auf meinem Gerät ausgeführt werden?

Die Azure Information Protection-App erfordert mindestens die Versionen **iOS 8** oder **Android 4.4**.

Wenn Sie über diese oder höhere Versionen verfügen, können Sie die App zur Ausführung auf Ihrem mobilen Gerät installieren:

- Wenn Ihr Gerät über Microsoft Intune verwaltet wird, können Sie die Azure Information Protection-App möglicherweise von Ihrem Unternehmensportal installieren.

- Wenn Ihr mobiles Gerät nicht über Microsoft Intune verwaltet wird oder die Azure Information Protection-App nicht in Ihrem Unternehmensportal verfügbar ist, können Sie die App entweder direkt aus dem iTunes-Store bzw. dem Google Play-Store installieren, oder Sie installieren die App, indem Sie mit der rechten Maustaste im Abschnitt **Mobile Geräte** der [Downloadseite von Azure Information Protection](https://portal.azurerms.com/#/download) auf das iOS- oder Android-Symbol klicken. 

## <a name="how-do-i-get-started-with-the-viewer-app"></a>Wie beginne ich mit der Viewer-App?

Nachdem Sie die App installiert haben, müssen Sie zu diesem Zeitpunkt nichts weiter tun. Warten Sie, bis Sie eine geschützte E-Mail oder Datei erhalten, die Sie anzeigen möchten, und wählen Sie dann **AIP Viewer** aus, um sie zu öffnen. Anschließend werden Sie gebeten, sich mit Ihrem Arbeits- oder Schulkonto anzumelden oder aufgefordert, ein Zertifikat auszuwählen. Nachdem diese Anmeldeinformationen authentifiziert wurden, können Sie den Inhalt lesen.

Wenn Sie nicht warten möchten, können Sie die folgenden Anweisungen verwenden, um sich selbst eine geschützte E-Mail oder Datei zum Anzeigen zu senden: [Get started with the Microsoft Azure Information Protection app for iOS and Android (Erste Schritte mit der Microsoft Azure Information Protection-App für iOS und Android)](mobile-app-get-started.md) 

## <a name="what-credentials-should-i-use-to-sign-in-to-this-app"></a>Welche Anmeldeinformationen sollte ich bei dieser App verwenden?

Wenn Ihre Organisation lokal bereits AD RMS (mit der Erweiterung für mobile Geräte) oder Azure Rights Management verwendet, melden Sie sich mit Ihren geschäftlichen Anmeldeinformationen an. 

Wenn die Datei mit Ihrer privaten E-Mail-Adresse geschützt wurde, melden Sie sich mit den Anmeldeinformationen eines kostenlosen [Microsoft-Kontos](https://signup.live.com) an.

## <a name="can-i-sign-up-for-the-free-account-with-my-personal-email-address-such-as-a-hotmail-or-gmail-account"></a>Kann ich für die Anmeldung bei einem kostenlosen Konto eine persönliche E-Mail-Adresse, z.B. ein Hotmail- oder Gmail-Konto, verwenden?

Ja, wenn Sie ein Microsoft-Konto beantragen, können Sie Ihre Hotmail- oder Gmail-Adresse oder eine andere E-Mail-Adresse angeben, die Sie besitzen. 

Obwohl dieser Viewer mit diesem Konto geschützte Dateien öffnen kann, können nicht alle Anwendungen geschützte Inhalte öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="which-file-extensions-can-i-open-with-this-app"></a>Welche Dateierweiterungen kann ich mit dieser App öffnen?

Sie können Dateien mit den Erweiterungen „.rpmsg“, „.pdf“, „.ppdf“, „.pjpg“, „.pjpeg“, „.ptiff“, „.ppng“, „.ptxt“, „.pxml“ sowie viele weitere Text- und Bilddateiformate öffnen.

Die vollständige Liste der Dateinamenerweiterungen für Text- und Bilddateien finden Sie in der ersten Tabelle im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](client-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) des Administratorhandbuchs.

##  <a name="how-do-i-provide-feedback-about-this-app"></a>Wie gebe ich Feedback zu dieser App?

Wechseln Sie in der App zu **Einstellungen** > **Feedback senden**.


## <a name="my-question-has-not-been-answeredwhat-should-i-do"></a>Meine Frage wurde hier nicht beantwortet – was soll ich tun?

Posten Sie Ihre Fragen auf unserer [Yammer-Website](https://www.yammer.com/AskIPTeam).
