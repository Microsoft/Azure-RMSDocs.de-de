---
title: Erste Schritte – AIP-App für iOS und Android
description: Anzeigen von E-Mails oder Dateien mit der Azure Information Protection-App für iOS und Android
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 07/07/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 3d5d18d8-7b2e-456c-bb45-48da4eb55544
ms.reviewer: esaggese
ms.suite: ems
ms.custom: user
ms.openlocfilehash: 622786bc1192d6727ef748df970adeb53733f4f8
ms.sourcegitcommit: d1f6f10c9cb95de535d8121e90b211f421825caf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/28/2020
ms.locfileid: "87298083"
---
# <a name="get-started-with-the-microsoft-azure-information-protection-app-for-ios-and-android"></a>Erste Schritte mit der Microsoft Azure Information Protection-App für iOS und Android

*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Auf dieser Seite wird beschrieben, wie Sie die Azure Information Protection-Apps für IOS oder Android testen.

Die meisten Benutzer verwenden in der Regel die Azure Information Protection-App, wenn sie eine geschützte E-Mail oder Datei öffnen müssen. Wenn Sie jedoch ein Administrator sind, der die APP für Ihre Benutzer testet, oder wenn Sie ihn einfach ausprobieren möchten, bevor Sie ihn benötigen, verwenden Sie die nachfolgenden Anweisungen, um geschützte Dateien auf Ihrem Gerät anzuzeigen.

> [!IMPORTANT]
> Bevor Sie beginnen, lesen Sie die Anforderungen und Anweisungen dazu, [was die Azure Information Protection-App für IOS oder Android ist?](mobile-app-faq.md)
> 

## <a name="access-a-protected-file-from-your-device"></a>Zugreifen auf eine geschützte Datei von Ihrem Gerät aus

Um das AIP-Mobile App zu testen, stellen Sie sicher, dass Sie auf einen der folgenden Typen geschützter Dateien von Ihrem Gerät aus zugreifen können:

|Dateityp  |Anweisungen  |
|---------|---------|
|**Eine rpmsg-Datei**     | Eine durch Rechte geschützte e-Mail-Nachricht. Wenn Ihre Mobile e-Mail-App den Rights Management-Schutz von Daten nicht nativ unterstützt, werden geschützte e-Mails als e-Mail-Anhänge angezeigt. </br></br>Verwenden Sie ein anderes Gerät, z.b. Outlook, von einem Windows-Computer aus, um sich selbst eine durch Rechte geschützte e-Mail-Nachricht zu senden, auf die Sie über Ihr mobiles Gerät zugreifen können </br></br>**Hinweis:** Eine Liste der e-Mail-Clients, die Rights Management unterstützen, finden Sie unter **e-Mail-** Zeilen in [Anwendungen, die Azure Rights Management Datenschutz unterstützen](../requirements-applications.md). |
|**Eine durch Rechte geschützte PDF-Datei**     | 1. schützen Sie auf einem Windows-Computer eine PDF-Datei mit dem [klassischen](client-classify-protect.md) AIP-oder [Unified-Bezeichnung-Client](clientv2-classify-protect.md) Client. </br>2. senden Sie die geschützte PDF-Datei, oder laden Sie Sie in eine geschützte SharePoint-Bibliothek hoch, und geben Sie Sie an Ihre eigene e-Mail-Adresse        |
|**Eine ptxt-oder pjpg-oder ppng-Datei**     | 1. schützen Sie auf einem Windows-Computer eine Text-oder Bilddatei mit dem [klassischen](client-classify-protect.md) AIP-oder [Unified-Bezeichnung-Client](clientv2-classify-protect.md) Client. </br></br>2. senden Sie die geschützte Datei, oder laden Sie Sie in eine geschützte SharePoint-Bibliothek hoch, und geben Sie Sie für Ihre eigene e-Mail-Adresse frei. </br></br>**Hinweis:** Weitere Informationen finden Sie [unter Unterstützte Dateitypen für Klassifizierung und Schutz](client-admin-guide-file-types.md#supported-file-types-for-classification-and-protection) .   |
| | |

### <a name="open-the-protected-file-on-your-mobile"></a>Öffnen Sie die geschützte Datei auf Ihrem Mobilgerät.

1. Tippen Sie auf den e-Mail-Anhang oder-Link, um den geschützten Inhalt zu

1. Wenn Sie dazu aufgefordert werden, wählen Sie die **AIP Viewer** -App aus, um den geschützten Inhalt anzuzeigen.

1. Melden Sie sich bei entsprechender Aufforderung mit Ihrem Geschäfts-oder Schul Konto an, oder wählen Sie ein Zertifikat aus.

Nachdem die Anwendung authentifiziert wurde, zeigt die AIP Viewer-APP die e-Mail oder Datei an.

> [!NOTE]
> Öffnen Sie immer die AIP-APP, indem Sie geschützte Inhalte öffnen. Versuchen Sie nicht, sich bei der App anzumelden, bis Sie dazu aufgefordert werden, oder öffnen Sie eine geschützte Datei in der AIP Viewer-app.
> 

## <a name="next-steps"></a>Nächste Schritte

Verwenden Sie eine der folgenden Methoden, um Feedback zu den mobilen AIP-apps bereitzustellen:

- Wechseln Sie zu **Einstellungen**  >  **Feedback senden** .
- Veröffentlichen Sie Ihre Frage auf unserer [Yammer-Website](https://www.yammer.com/AskIPTeam)