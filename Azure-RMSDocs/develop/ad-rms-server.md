---
title: AD RMS-Server | Azure RMS
description: Die Serverkomponente von Rights Management Services (RMS) wird durch eine Reihe von Webdiensten implementiert, die in Microsoft-Internetinformationsdienste (IIS) ausgeführt werden.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: eae7071115f417e6ea66a98c1bf8820440938718
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95567961"
---
# <a name="server"></a>Server

In diesem Thema werden der Zweck und die Funktionen des RMS-Servers für Azure und Windows Server beschrieben.

**Azure RMS**: Weitere Informationen zum Verwenden des Azure Rights Management Service finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

> [!IMPORTANT] 
> Es empfiehlt sich, Ihre Anwendung über Azure RMS zu entwickeln und zu testen.

**Windows Server**: Für RMS auf lokalen Servern können Sie den RMS-Dienst ab Windows Server 2008 installieren und konfigurieren, indem Sie ihn als Rolle hinzufügen. Um den Dienst unter früheren Betriebssystemen zu installieren, laden Sie ihn aus dem Microsoft Downloadcenter unter [Microsoft Windows Rights Management Services mit Service Pack 2](https://www.microsoft.com/download/details.aspx?id=4909) herunter.

Von den vielen installierten Webdiensten sind die folgenden für die Anwendungsentwicklung mit RMS-Server unter Windows Server am wichtigsten.

| Dienst | BESCHREIBUNG |
|---------|-------------|
| Verwaltung | Hostet die Verwaltungswebsite, mit der Sie RMS verwalten können. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt. Sie können mit der Active Directory Rights Management Services-Skripterstellungs-API Verwaltungsskripts schreiben.|
| Kontozertifizierung |Erstellt Computerzertifikate, die Computer in der RMS-Zertifikathierarchie identifizieren, und Rechtekontozertifikate, über die Benutzer bestimmten Computern zugeordnet werden. Weitere Informationen finden Sie unter „Aktivieren eines Computers“ und „Aktivieren eines Benutzers“.<p><p>Dieser Dienst wird auf dem Stammzertifizierungsserver ausgeführt. |
|Lizenzierung | Stellt eine *Endbenutzerlizenz* aus. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|
|Veröffentlichen | Erstellt eine *Veröffentlichungslizenz*, die die Richtlinien definiert, die in einer Endbenutzerlizenz aufgelistet werden können. Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichungslizenz](/previous-versions/windows/desktop/adrms_sdk/creating-an-issuance-license).<p><p>Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|
|Vorzertifizierung | Ermöglicht es einem Server, ein *Rechtekontozertifikat* im Auftrag eines Benutzers anzufordern. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|
|Dienstlocator | Stellt die URL der Dienste zur Zertifizierung, Lizenzierung und Veröffentlichung von Konten für Active Directory bereit, damit diese von RMS-Clients gefunden werden können. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|

## <a name="related-topics"></a>Verwandte Themen ##
* [Übersicht](ad-rms-overview.md)
* [Microsoft-Internetinformationsdienste](https://www.iis.net/overview)
* [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows Rights Management Services mit Service Pack 2](https://www.microsoft.com/download/details.aspx?id=4909)
* [Active Directory Rights Management Services Scripting API (Active Directory Rights Management Services-Skripterstellungs-API)](/previous-versions/windows/desktop/adrms_script/adrms-script-portal)
* [Aktivieren eines Computers](/previous-versions/windows/desktop/adrms_sdk/activating-a-computer)
* [Aktivieren eines Benutzers](/previous-versions/windows/desktop/adrms_sdk/activating-a-user)
* [Erstellen einer Veröffentlichungslizenz](/previous-versions/windows/desktop/adrms_sdk/creating-an-issuance-license)