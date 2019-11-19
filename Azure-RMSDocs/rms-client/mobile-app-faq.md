---
title: Häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android
description: Einige häufig gestellte Fragen, die Ihnen beim Verwenden der Azure Information Protection-App für iOS und Android helfen sollen
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 11/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.custom: user
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: a8f6871f322765abf07087ce3c7bd629bfc9748f
ms.sourcegitcommit: 9484744702a82b8adc45f78e0b127a3857794d29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2019
ms.locfileid: "74160820"
---
# <a name="faqs-for-microsoft-azure-information-protection-app-for-ios-and-android"></a>Häufig gestellte Fragen zur Microsoft Azure Information Protection-App für iOS und Android

*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Auf dieser Seite finden Sie Antworten auf einige häufig gestellte Fragen zur Azure Information Protection-App für iOS und Android.

## <a name="what-can-i-do-with-the-azure-information-protection-app"></a>Was kann ich mit der Azure Information Protection-App machen?

Mit dieser App können Sie durch Rechte geschützte E-Mail-Nachrichten anzeigen (RPMSG-Dateien), wenn Ihre E-Mail-App von sich aus keinen Datenschutz durch Rechteverwaltung unterstützt. Mit dieser App können Sie außerdem durch Rechte geschützte PDF-Dokumente, Bilder und Textdateien anzeigen. 

Da es sich bei dieser App um einen Viewer handelt, können Sie damit keine geschützten E-Mail-Nachrichten erstellen oder beantworten und keine geschützten Dateien erstellen oder bearbeiten. Ferner können Sie mit der App auch keine Anlagen für angezeigte Dateien öffnen, wie Anlagen in geschützten PDF-Dokumenten oder in rechtegeschützten E-Mail-Nachrichten.

## <a name="can-i-open-pdf-files-that-are-in-sharepoint-protected-libraries-and-onedrive-for-business"></a>Kann ich PDF-Dateien aus geschützten SharePoint-Bibliotheken und OneDrive for Business öffnen?

Ja, Sie können geschützte PDF-Dateien öffnen, die andere über SharePoint und OneDrive for Business für Sie freigegeben haben. Tippen Sie auf den Link, und wählen Sie diese App für das Öffnen der Datei aus. 

Diese App kann auch PDF-Dateien öffnen, die außerhalb von SharePoint und OneDrive for Business geschützt wurden (geschützte PDF- und PPDF-Dateien).

## <a name="can-my-mobile-device-run-the-azure-information-protection-app"></a>Kann die Azure Information Protection-App auf meinem Gerät ausgeführt werden?

Die Azure Information Protection-App erfordert eine Mindestversion von **IOS 11** oder **Android 6,0**.

Wenn Sie über diese oder höhere Versionen verfügen, können Sie die App zur Ausführung auf Ihrem mobilen Gerät installieren:

- Wenn Ihr Gerät über Microsoft Intune verwaltet wird, können Sie die Azure Information Protection-App möglicherweise von Ihrem Unternehmensportal installieren.

- Wenn Ihr mobiles Gerät nicht über Microsoft Intune verwaltet wird oder die Azure Information Protection-App nicht in Ihrem Unternehmensportal verfügbar ist, können Sie die App entweder direkt aus dem iTunes-Store bzw. dem Google Play-Store installieren, oder Sie installieren die App, indem Sie mit der rechten Maustaste im Abschnitt **Mobile Geräte** der [Downloadseite von Azure Information Protection](https://portal.azurerms.com/#/download) auf das iOS- oder Android-Symbol klicken. 

## <a name="how-do-i-get-started-with-the-viewer-app"></a>Wie beginne ich mit der Viewer-App?

Nachdem Sie die App installiert haben, müssen Sie zu diesem Zeitpunkt nichts weiter tun. Warten Sie, bis Sie eine geschützte E-Mail oder Datei erhalten, die Sie anzeigen möchten, und wählen Sie dann **AIP Viewer** aus, um sie zu öffnen. Anschließend werden Sie gebeten, sich mit Ihrem Arbeits- oder Schulkonto anzumelden oder aufgefordert, ein Zertifikat auszuwählen. Nachdem diese Anmeldeinformationen authentifiziert wurden, können Sie den Inhalt lesen.

Wenn Sie nicht warten möchten, können Sie die folgenden Anweisungen verwenden, um sich selbst eine geschützte E-Mail oder Datei zum Anzeigen zu senden: [Get started with the Microsoft Azure Information Protection app for iOS and Android (Erste Schritte mit der Microsoft Azure Information Protection-App für iOS und Android)](mobile-app-get-started.md) 

## <a name="what-credentials-should-i-use-to-sign-in-to-this-app"></a>Welche Anmeldeinformationen sollte ich bei dieser App verwenden?

Wenn Ihre Organisation bereits AD RMS lokal (mit der Erweiterung für mobile Geräte) oder Azure Information Protection verwendet, verwenden Sie Ihre Anmelde Informationen für die Anmeldung. 

Wenn die Datei mit Ihrer privaten E-Mail-Adresse geschützt wurde, melden Sie sich mit den Anmeldeinformationen eines kostenlosen [Microsoft-Kontos](https://signup.live.com) an.

## <a name="can-i-sign-up-for-the-free-account-with-my-personal-email-address-such-as-a-hotmail-or-gmail-account"></a>Kann ich für die Anmeldung bei einem kostenlosen Konto eine persönliche E-Mail-Adresse, z.B. ein Hotmail- oder Gmail-Konto, verwenden?

Ja, wenn Sie ein Microsoft-Konto beantragen, können Sie Ihre Hotmail- oder Gmail-Adresse oder eine andere E-Mail-Adresse angeben, die Sie besitzen. 

Obwohl dieser Viewer mit diesem Konto geschützte Dateien öffnen kann, können nicht alle Anwendungen geschützte Inhalte öffnen, wenn ein Microsoft-Konto für die Authentifizierung verwendet wird. [Weitere Informationen](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents)

## <a name="which-file-extensions-can-i-open-with-this-app"></a>Welche Dateierweiterungen kann ich mit dieser App öffnen?

Sie können Dateien mit den Erweiterungen „.rpmsg“, „.pdf“, „.ppdf“, „.pjpg“, „.pjpeg“, „.ptiff“, „.ppng“, „.ptxt“, „.pxml“ sowie viele weitere Text- und Bilddateiformate öffnen.

Die vollständige Liste der Dateinamenerweiterungen für Text- und Bilddateien finden Sie in der ersten Tabelle im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](clientv2-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) des Administratorhandbuchs.

##  <a name="how-do-i-provide-feedback-about-this-app"></a>Wie gebe ich Feedback zu dieser App?

Wechseln Sie in der App zu **Einstellungen** > **Feedback senden**.


## <a name="my-question-has-not-been-answeredwhat-should-i-do"></a>Meine Frage wurde hier nicht beantwortet – was soll ich tun?

Posten Sie Ihre Fragen auf unserer [Yammer-Website](https://www.yammer.com/AskIPTeam).
