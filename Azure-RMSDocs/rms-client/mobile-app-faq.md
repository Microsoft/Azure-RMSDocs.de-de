---
title: Apps für IOS & Android Azure Information Protection
description: Grundlegende Informationen zu den Azure Information Protection-Apps (AIP) für IOS-und Android-Geräte
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/07/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 0f849dfefa6af9ffd95dcca0c731ed216f465b11
ms.sourcegitcommit: 223e26b0ca4589317167064dcee82ad0a6a8d663
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "86046401"
---
# <a name="what-is-the-azure-information-protection-app-for-ios-or-android"></a>Was ist die Azure Information Protection-App für IOS oder Android?

*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Mit den Azure Information Protection-Apps (AIP) für IOS und Android können Sie durch Rechte geschützte e-Mail-Nachrichten (**rpmsg** -Dateien) anzeigen, wenn Ihre e-Mail-App den Rights Management-Datenschutz nicht nativ unterstützt.  

Mit den AIP-Apps können Sie auch durch Rechte geschützte PDF-Dokumente (geschützte PDF-und**ppdf** -Dateien), Bilder und Textdateien anzeigen.

> [!NOTE]
> Bei den AIP-apps handelt es sich nur um Viewer, und Sie können keine neuen oder Antworten auf geschützte e-Mail-Nachrichten erstellen oder geschützte Dateien erstellen oder bearbeiten. Die apps können auch keine Anlagen für Dateien öffnen, die Sie anzeigen, z. b. Anlagen für geschützte PDF-Dokumente oder e-Mail-Nachrichten.
>

## <a name="aip-mobile-app-requirements"></a>AIP-Mobile App Anforderungen

Die mobilen AIP-Apps für IOS und Android können mit den folgenden Systemen verwendet werden:

- [Unterstützte Versionen von mobilen Betriebssystemen](#supported-mobile-os-versions)
- [Unterstützte Anmelde Informationen](#supported-sign-in-credentials)
- [Unterstützte Dateierweiterungen](#supported-file-extensions)

### <a name="supported-mobile-os-versions"></a>Unterstützte Versionen von mobilen Betriebssystemen

Die mobilen AIP-apps erfordern eines der folgenden minimalen mobilen Betriebssysteme: 

- iOS 11 
- Android 6,0 

> [!NOTE]
> Die mobilen AIP-apps werden auf Intel-CPUs nicht unterstützt.
> 

### <a name="supported-sign-in-credentials"></a>Unterstützte Anmelde Informationen

Verwenden Sie für die Anmeldung bei AIP eine der folgenden Aktionen: 

- **Anmelde Informationen für Geschäfts-oder Schul Konto** Verwenden Sie, wenn Ihre Organisation bereits AD RMS lokal mit der Erweiterung für mobile Geräte oder Azure Information Protection verwendet.
 
- **Eine Microsoft-Konto**. Wenn Ihre persönliche e-Mail-Adresse zum Schutz der Datei verwendet wurde, melden Sie sich mit einem [Microsoft-Konto](https://signup.live.com)an. 

    - Sie können Ihre eigenen Hotmail, Gmail oder andere e-Mail-Adressen verwenden, die Sie besitzen, wenn Sie eine Microsoft-Konto beantragen.
    
> [!NOTE]
> Nicht alle Anwendungen können geschützte Inhalte öffnen, wenn ein Microsoft-Konto verwendet wird. Weitere Informationen finden Sie [unter Unterstützte Szenarien für das Öffnen geschützter Dokumente](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).
> 

### <a name="supported-file-extensions"></a>Unterstützte Dateierweiterungen

Sie können Dateien mit den Erweiterungen „.rpmsg“, „.pdf“, „.ppdf“, „.pjpg“, „.pjpeg“, „.ptiff“, „.ppng“, „.ptxt“, „.pxml“ sowie viele weitere Text- und Bilddateiformate öffnen.

Die vollständige Liste der Dateinamenerweiterungen für Text- und Bilddateien finden Sie in der ersten Tabelle im Abschnitt [Unterstützte Dateitypen für Klassifizierung und Schutz](clientv2-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) des Administratorhandbuchs.

## <a name="installing-your-aip-mobile-apps-and-viewing-files"></a>Installieren von mobilen AIP-apps und Anzeigen von Dateien

Wenn Ihr mobiles Gerät von Microsoft InTune verwaltet wird, können Sie die apps möglicherweise über das Unternehmensportal herunterladen.

Andernfalls greifen Sie auf die apps von folgenden Berechtigungen zu:

- Der [iTunes](https://apps.apple.com/app/microsoft-rights-management/id689516635) -oder [Google Play](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) Store
- Die [Azure Information Protection Downloadseite](https://portal.azurerms.com/#/download). Wählen Sie die [IOS](https://apps.apple.com/app/microsoft-rights-management/id689516635) -oder [Android](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) -Symbole im Abschnitt **Mobile Geräte** aus.

Warten Sie nach der Installation, bis Sie eine geschützte e-Mail oder Datei erhalten haben, und wählen Sie den **AIP-Viewer** aus, wenn Sie ihn öffnen.

Sie werden aufgefordert, sich mit Ihrem Geschäfts-, Schul-oder unikonto anzumelden, oder Sie werden aufgefordert, ein Zertifikat auszuwählen. Nachdem Sie authentifiziert wurden, wird Ihre e-Mail oder Datei geöffnet, und Sie können den Inhalt lesen.

> [!TIP]
> Um dies sofort auszuprobieren, senden Sie sich selbst eine geschützte e-Mail oder Datei an, die Sie anzeigen können. 
>
> Weitere Informationen finden Sie unter [Einstieg in die Microsoft Azure Information Protection-App für IOS und Android](mobile-app-get-started.md).
> 

## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie eine der folgenden Methoden, um Feedback zu den mobilen AIP-apps bereitzustellen:

- Wechseln Sie zu **Einstellungen**  >  **Feedback senden** .
- Veröffentlichen Sie Ihre Frage auf unserer [Yammer-Website](https://www.yammer.com/AskIPTeam)
