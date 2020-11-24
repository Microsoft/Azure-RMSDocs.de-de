---
title: Mobile Apps für IOS & Android Azure Information Protection
description: Erfahren Sie mehr über die Grundlagen zu den mobilen Apps für Azure Information Protection (AIP) für IOS-und Android-Geräte
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/24/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 17f1efc5c5e0c01f33e638d1ef674a81b17494f8
ms.sourcegitcommit: 5b7235f7bb77cc88716f15dda0aa0d832e0f7063
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734963"
---
# <a name="what-is-the-azure-information-protection-app-for-ios-or-android"></a>Was ist die Azure Information Protection-App für IOS oder Android?

*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Die Azure Information Protection-Mobile App für IOS und Android ist eine Viewer-APP, mit der Sie geschützte e-Mail-Nachrichten, PDF-Dateien, Bilder und Textdateien anzeigen können. Sie sind hilfreich, wenn ihre regulären Apps für diese Dateitypen keinen Schutz unterstützen. 

Wenn beispielsweise geschützte e-Mails in ihren regulären e-Mail-Mobile App als Anlagen angezeigt werden, können Sie die AIP-Mobile App verwenden, um diese e-Mail anzuzeigen.

Weitere Informationen finden Sie unter [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../requirements-applications.md).

> [!NOTE]
> Bei den mobilen AIP-apps handelt es sich *nur um Viewer,* mit denen Sie keine neuen e-Mails erstellen oder geschützte Dateien erstellen oder bearbeiten können. Die mobilen AIP-Apps können auch keine Anlagen in geschützten PDF-oder e-Mail-Geräten öffnen.
> 

## <a name="download-and-install-the-aip-app-for-your-device"></a>Herunterladen und Installieren der AIP-App für Ihr Gerät

Herunterladen und Installieren von mobilen AIP-Apps über einen der folgenden Speicherorte:

**iTunes**

:::image type="content" source="../media/develop/ios-icon.png" alt-text="iTunes" link="https://apps.apple.com/app/microsoft-rights-management/id689516635" border="false":::

**Google Play**

:::image type="content" source="../media/develop/android-icon.png" alt-text="Google Play" link="https://play.google.com/store/apps/details?id=com.microsoft.ipviewer" border="false":::

**AIP-Downloadseite**

:::image type="content" source="../media/aip-icon.png" alt-text="Azure Information Protection Downloadseite" border="false":::

Wählen Sie die [IOS](https://apps.apple.com/app/microsoft-rights-management/id689516635) -oder [Android](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer) -Symbole im Abschnitt **Mobile Geräte** aus.

**Ihr Unternehmensportal**

Wenn Ihr mobiles Gerät von Microsoft InTune verwaltet wird, können Sie die mobilen AIP-Apps möglicherweise über das Unternehmensportal herunterladen. 

Wenden Sie sich an Ihren Systemadministrator, um weitere Informationen zu erhalten.

## <a name="ios-view-protected-files-on-your-device"></a>iOS: geschützte Dateien auf Ihrem Gerät anzeigen

Nachdem Sie [das AIP-Mobile App installiert](#download-and-install-the-aip-app-for-your-device)haben, öffnen Sie eine geschützte e-Mail oder Datei. 

1. Wenn Sie zum Auswählen einer APP aufgefordert werden, um die Datei zu öffnen, tippen Sie auf die Schaltfläche freigeben, um stattdessen die Datei freizugeben.

    Wählen Sie **Datei freigeben über..** . aus, und wählen Sie dann **in AIP-Viewer kopieren aus.**

    Beispiel:

    :::image type="content" source="../media/ios-share-to-aip-viewer.png" alt-text="Freigabe für AIP-Viewer in ios" border="false":::

1. Melden Sie sich an, oder wählen Sie ein Zertifikat wie angefordert aus.

    Nachdem Sie authentifiziert wurden, wird Ihre e-Mail oder Datei im AIP-Viewer geöffnet.
 
## <a name="android-view-protected-files-on-your-device"></a>Android: geschützte Dateien auf Ihrem Gerät anzeigen

Nachdem Sie [das AIP-Mobile App installiert](#download-and-install-the-aip-app-for-your-device)haben, öffnen Sie eine geschützte e-Mail oder Datei. 

1. Wenn Sie zum Auswählen einer APP aufgefordert werden, wählen Sie den AIP-Viewer aus:

    :::image type="content" source="../media/select-aip-viewer.png" alt-text="Wählen Sie den AIP-Viewer aus Mobile App":::

1. Melden Sie sich an, oder wählen Sie ein Zertifikat wie angefordert aus.

    Nachdem Sie authentifiziert wurden, wird Ihre e-Mail oder Datei im AIP-Viewer geöffnet.

## <a name="aip-mobile-app-requirements"></a>AIP-Mobile App Anforderungen

Die mobilen AIP-Apps für IOS und Android unterstützen die folgenden Dateitypen und Umgebungen:

|Anforderung  |BESCHREIBUNG  |
|---------|---------|
|**Unterstützte Betriebssystemversionen**     | Die Mindestanforderungen für mobile Betriebssysteme sind: </br>-IOS 11  </br>-Android 6,0 </br></br>**Hinweis:** Die mobilen AIP-apps werden auf Intel-CPUs nicht unterstützt.  |
|**Unterstützte Anmelde Informationen**     | Melden Sie sich mit einer der folgenden Aktionen bei den mobilen AIP-apps an: </br></br>**Anmelde Informationen für Geschäfts-oder Schul Konto** Melden Sie sich mit den Anmelde Informationen Ihres Geschäfts-oder Schul Kontos an. Wenn Sie Fragen haben, wenden Sie sich an Ihren Administrator, um zu verstehen, ob Ihr Unternehmen lokal mit der Erweiterung für mobile Geräte AD RMS oder Azure Information Protection verwendet. </br></br>**Eine Microsoft-Konto**. Wenn Ihre persönliche e-Mail-Adresse zum Schutz der Datei verwendet wurde, melden Sie sich mit einem [Microsoft-Konto](https://signup.live.com)an. Wenn Sie sich für eine Microsoft-Konto bewerben müssen, können Sie dazu ihren eigenen Hotmail, Gmail oder jede andere e-Mail-Adresse verwenden. </br></br>**Hinweis:** Nicht alle Anwendungen können Inhalte öffnen, die mit einem Microsoft-Konto geschützt sind. Weitere Informationen finden Sie [unter Unterstützte Szenarien für das Öffnen geschützter Dokumente](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).|
|**Unterstützte Dateitypen**     | Zu den unterstützten Dateitypen zählen geschützte e-Mail-Nachrichten, PDF-Dateien, Bilder und Textdateien. </br></br>Diese Dateien enthalten beispielsweise die folgenden Erweiterungen: **rpmsg,** **PDF,** **ppdf,** **pjpg,** **pjpeg,** **ptiff,** **ppng,** **ptxt,** **pxml** </br></br>Eine vollständige Liste der unterstützten Dateitypen finden Sie [im AIP-Client Administrator Handbuch](clientv2-admin-guide-file-types.md#supported-file-types-for-classification-and-protection).|
| | |

## <a name="admins-testing-the-aip-mobile-apps"></a>Administratoren: Testen der mobilen AIP-apps

Die meisten Benutzer verwenden normalerweise den AIP-Mobile App, um eine geschützte e-Mail oder Datei zu öffnen, die nicht mithilfe ihrer regulären mobilen apps geöffnet werden kann.

Wenn Sie ein Systemadministrator sind, der die mobilen AIP-Apps für Ihre Organisation testen möchte, oder Sie einfach selbst ausprobieren möchten, befolgen Sie die nachfolgenden Anweisungen, um Sie durch den gesamten Prozess zu führen.

1. Stellen Sie sicher, dass Sie Zugriff auf einen Dateityp haben, der von der AIP-Mobile App auf Ihrem Gerät unterstützt wird. 

    Senden Sie z. b. eine der folgenden durch Rechte geschützten Dateien:

    |Dateityp  |Instructions  |
    |---------|---------|
    |**E-Mail (. rpmsg)**     | Verwenden Sie ein anderes Gerät, z.b. Outlook, von einem Windows-Computer aus, um sich selbst eine durch Rechte geschützte e-Mail-Nachricht zu senden, auf die Sie über Ihr mobiles Gerät zugreifen können  |
    |**PDF**     | 1. schützen Sie auf einem Windows-Computer eine PDF-Datei mit dem [klassischen](client-classify-protect.md) AIP-oder [Unified-Bezeichnung](clientv2-classify-protect.md) -Client. </br>2. senden Sie die geschützte PDF-Datei, oder laden Sie Sie in eine geschützte SharePoint-Bibliothek hoch, und geben Sie Sie an Ihre eigene e-Mail-Adresse        |
    |**Bild (ptxt-, pjpg-oder ppng-Datei)**     | 1. schützen Sie auf einem Windows-Computer eine Text-oder Bilddatei mit dem [klassischen](client-classify-protect.md) AIP-oder [Unified-Bezeichnung](clientv2-classify-protect.md) -Client. </br></br>2. senden Sie die geschützte Datei, oder laden Sie Sie in eine geschützte SharePoint-Bibliothek hoch, und geben Sie Sie für Ihre eigene e-Mail-Adresse frei.   |
| | |

1. Öffnen Sie die geschützte Datei auf Ihrem mobilen Gerät mithilfe der e-Mail-Anlage oder des Links, die Sie an Sie gesendet haben.

    Geschützte e-Mails werden z. b. in ihren regulären e-Mail-Mobile App als Anlagen angezeigt. 

1. Wenn Sie zum Auswählen einer APP aufgefordert werden, um die geschützte e-Mail oder Datei zu öffnen, wählen Sie die **AIP Viewer** -App aus.

1. Melden Sie sich an, oder wählen Sie ein Zertifikat aus. 

    Nachdem die Anwendung authentifiziert wurde, zeigt die AIP Viewer-APP die e-Mail oder Datei an.

> [!NOTE]
> Öffnen Sie immer die AIP-APP, indem Sie geschützte Inhalte öffnen. Versuchen Sie nicht, sich bei der App anzumelden, bis Sie dazu aufgefordert werden, oder öffnen Sie eine geschützte Datei in der AIP Viewer-app.
> 

## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie eine der folgenden Methoden, um Feedback zu den mobilen AIP-apps bereitzustellen:

- Wechseln Sie zu **Einstellungen**  >  **Feedback senden** .
- Veröffentlichen Sie Ihre Frage auf unserer [Yammer-Website](https://www.yammer.com/AskIPTeam)
