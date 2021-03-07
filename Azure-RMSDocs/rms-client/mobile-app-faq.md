---
title: Mobile Viewer-Apps für Azure Information Protection (IOS und Android)-aip
description: Erfahren Sie, wie Sie geschützte Dateien auf Ihren IOS-und Android-Geräten mithilfe der Azure Information Protection (AIP)-Viewer-apps anzeigen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 02/22/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 539b4ff8-5d3b-4c4d-9c84-c14da83ff76d
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 1f0e3de4a8548761cd58cc69216a7e80fe0128e5
ms.sourcegitcommit: 74b8d03d1ede3da12842b84546417e63897778bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2021
ms.locfileid: "102415343"
---
# <a name="mobile-viewer-apps-for-azure-information-protection-on-ios-and-android"></a>Mobile Viewer-Apps für Azure Information Protection unter IOS und Android

>***Gilt für**: Active Directory Rights Management Services [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

Mit den mobilen Azure Information Protection (AIP)-Apps können Sie geschützte e-Mails, PDF-Dateien, Bilder und Textdateien anzeigen, wenn Sie Sie nicht mit ihren regulären Apps für diese Dateitypen öffnen können. Wenn beispielsweise geschützte e-Mails in ihren regulären e-Mail-Mobile App als Anlagen angezeigt werden, können Sie die AIP-Mobile App verwenden, um diese e-Mail anzuzeigen.

**Schutz-und Vertraulichkeits Bezeichnungen werden in mobilen Office-Versionen unterstützt**. Wenn Sie Mobile Office-Apps auf Ihrem Gerät installiert haben, wird empfohlen, dass Sie die Office-Apps zum Anzeigen geschützter Dateien verwenden. Weitere Informationen finden Sie unter [Vertraulichkeits Bezeichnungs Funktionen in Word, Excel und PowerPoint](/microsoft-365/compliance/sensitivity-labels-office-apps#sensitivity-label-capabilities-in-word-excel-and-powerpoint).

**Wenn Sie die Datei auf einem Desktop öffnen**, verwenden Sie die [Desktop Version des AIP-Viewers](clientv2-view-use-files.md). 

> [!NOTE]
> Bei den mobilen AIP-apps handelt es sich *nur um Viewer,* mit denen Sie keine neuen e-Mails erstellen oder geschützte Dateien erstellen oder bearbeiten können. Die mobilen AIP-Apps können auch keine Anlagen in geschützten PDF-oder e-Mail-Geräten öffnen.
> 

## <a name="aip-mobile-viewer-app-requirements"></a>Anforderungen an die AIP Mobile Viewer-App

Die AIP Mobile Viewer-Apps für IOS und Android unterstützen die folgenden Dateitypen und Umgebungen:

|Anforderung  |BESCHREIBUNG  |
|---------|---------|
|**Unterstützte Betriebssystemversionen**     | Die Mindestanforderungen für mobile Betriebssysteme sind: </br>-IOS 11  </br>-Android 6,0 </br></br>**Hinweis**: die AIP Mobile Viewer-apps werden auf Intel-CPUs nicht unterstützt.  |
|**Unterstützte Anmelde Informationen**     | Melden Sie sich mit einer der folgenden Aktionen bei den AIP Mobile Viewer-apps an: </br></br>**Anmelde Informationen für Geschäfts-oder Schul Konto** Melden Sie sich mit den Anmelde Informationen Ihres Geschäfts-oder Schul Kontos an. Wenn Sie Fragen haben, wenden Sie sich an Ihren Administrator, um zu verstehen, ob Ihr Unternehmen lokal mit der Erweiterung für mobile Geräte AD RMS oder Azure Information Protection verwendet. </br></br>**Eine Microsoft-Konto.** Wenn Ihre persönliche e-Mail-Adresse zum Schutz der Datei verwendet wurde, melden Sie sich mit einem [Microsoft-Konto](https://signup.live.com)an. Wenn Sie sich für eine Microsoft-Konto bewerben müssen, können Sie dazu ihren eigenen Hotmail, Gmail oder jede andere e-Mail-Adresse verwenden. </br></br>**Hinweis**: nicht alle Anwendungen können Inhalte öffnen, die mit einem Microsoft-Konto geschützt sind. Weitere Informationen finden Sie [unter Unterstützte Szenarien für das Öffnen geschützter Dokumente](../secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents).|
|**Unterstützte Dateitypen**     | Zu den unterstützten Dateitypen zählen geschützte e-Mail-Nachrichten, PDF-Dateien, Bilder und Textdateien. </br></br>Diese Dateien enthalten beispielsweise die folgenden Erweiterungen: **rpmsg**, **PDF**, **ppdf**, **pjpg**, **pjpeg**, **ptiff**, **ppng**, **ptxt**, **pxml** </br></br>Eine vollständige Liste der unterstützten Dateitypen finden Sie [im AIP-Client Administrator Handbuch](clientv2-admin-guide-file-types.md#supported-file-types-for-classification-and-protection).|
| | |

## <a name="download-and-install-the-aip-app-for-your-device"></a>Herunterladen und Installieren der AIP-App für Ihr Gerät

Wenn Sie nicht über [Office-Apps](/microsoft-365/compliance/sensitivity-labels-office-apps#sensitivity-label-capabilities-in-word-excel-and-powerpoint) verfügen, mit denen Sie geschützte Dateien öffnen können, laden Sie AIP Mobile Viewer-apps herunter, und installieren Sie Sie.

Laden Sie die Mobile Viewer-apps von folgenden Speicherorten herunter, und installieren Sie Sie:

|Standort  |Details/Link  |
|---------|---------|
|**iTunes**     | [![Installation über iTunes.](../media/small/ios-icon-small.png)](https://apps.apple.com/app/microsoft-rights-management/id689516635)        |
|**Google Play**     |[![Installieren Sie von Google Play.](../media/small/android-icon-small.png)](https://play.google.com/store/apps/details?id=com.microsoft.ipviewer)         |
|**Ihr Unternehmensportal**     |  Wenn Ihr mobiles Gerät von Microsoft InTune verwaltet wird, können Sie die AIP Mobile Viewer-Apps möglicherweise über das Unternehmensportal herunterladen. <br><br>Wenden Sie sich an Ihren Systemadministrator, um weitere Informationen zu erhalten.        |
|     |         |

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


## <a name="admins-testing-the-aip-mobile-viewer-apps"></a>Administratoren: Testen der AIP Mobile Viewer-apps

Die meisten Benutzer verwenden normalerweise den AIP-Mobile App, um eine geschützte e-Mail oder Datei zu öffnen, die nicht mithilfe ihrer regulären mobilen apps geöffnet werden kann.

Wenn Sie ein Systemadministrator sind, der die AIP Mobile Viewer-Apps für Ihre Organisation testen möchte, oder Sie einfach selbst ausprobieren möchten, befolgen Sie die nachfolgenden Anweisungen, um Sie durch den gesamten Prozess zu führen.

1. Stellen Sie sicher, dass Sie Zugriff auf einen Dateityp haben, der von der AIP-Mobile App auf Ihrem Gerät unterstützt wird. 

    Senden Sie z. b. eine der folgenden durch Rechte geschützten Dateien:

    |Dateityp  |Instructions  |
    |---------|---------|
    |**E-Mail (. rpmsg)**     | Verwenden Sie ein anderes Gerät, z.b. Outlook, von einem Windows-Computer aus, um sich selbst eine durch Rechte geschützte e-Mail-Nachricht zu senden, auf die Sie über Ihr mobiles Gerät zugreifen können  |
    |**PDF**     | 1. schützen Sie auf einem Windows [-Computer eine PDF-](clientv2-classify-protect.md) Datei mit dem AIP-Client. </br>2. senden Sie die geschützte PDF-Datei, oder laden Sie Sie in eine geschützte SharePoint-Bibliothek hoch, und geben Sie Sie an Ihre eigene e-Mail-Adresse        |
    |**Bild (ptxt-, pjpg-oder ppng-Datei)**     | 1. schützen Sie auf einem Windows-Computer [eine Text-oder Bilddatei](clientv2-classify-protect.md) mit dem AIP-Client. </br></br>2. senden Sie die geschützte Datei, oder laden Sie Sie in eine geschützte SharePoint-Bibliothek hoch, und geben Sie Sie für Ihre eigene e-Mail-Adresse frei.   |
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

Verwenden Sie eine der folgenden Methoden, um Feedback zu den AIP Mobile Viewer-apps bereitzustellen:

- Wechseln Sie zu **Einstellungen**  >  **Feedback senden** .
- Veröffentlichen Sie Ihre Frage auf unserer [Yammer-Website](https://www.yammer.com/AskIPTeam)

Weitere Informationen zu den Schutz Features, die in ihren apps unterstützt werden, finden Sie [unter Anwendungen, die Azure Rights Management Datenschutz unterstützen](../requirements-applications.md).
