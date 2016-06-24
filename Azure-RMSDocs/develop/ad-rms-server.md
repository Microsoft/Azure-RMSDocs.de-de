---
# required metadata

title: AD RMS-Server | Azure RMS
description: Die Serverkomponente von Rights Management Services (RMS) wird durch eine Reihe von Webdiensten implementiert, die in Microsoft-Internetinformationsdienste (IIS) ausgeführt werden.
keywords:
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 17B05780-B0EF-4805-8304-52DCDEB3AADB
# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Server

In diesem Thema werden der Zweck und die Funktionen des RMS-Servers für Azure und Windows Server beschrieben.

**Azure RMS**: Weitere Informationen zum Verwenden des Azure Rights Management Service finden Sie unter [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md).

> [!IMPORTANT] Es empfiehlt sich, Ihre Anwendung über Azure RMS zu entwickeln und zu testen.

**Windows Server**: Für RMS auf lokalen Servern können Sie den RMS-Dienst ab Windows Server 2008 installieren und konfigurieren, indem Sie ihn als Rolle hinzufügen. Um den Dienst unter früheren Betriebssystemen zu installieren, laden Sie ihn aus dem Microsoft Downloadcenter unter [Microsoft Windows Rights Management Services mit Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909) herunter.

Von den vielen installierten Webdiensten sind die folgenden für die Anwendungsentwicklung mit RMS-Server unter Windows Server am wichtigsten.

| Dienst | Beschreibung |
|---------|-------------|
| Verwaltung | Hostet die Verwaltungswebsite, mit der Sie RMS verwalten können. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt. Sie können mit der Active Directory Rights Management Services-Skripterstellungs-API Verwaltungsskripts schreiben.|
| Kontozertifizierung |Erstellt Computerzertifikate, die Computer in der RMS-Zertifikathierarchie identifizieren, und Rechtekontozertifikate, über die Benutzer bestimmten Computern zugeordnet werden. Weitere Informationen finden Sie unter „Aktivieren eines Computers“ und „Aktivieren eines Benutzers“.<p><p>Dieser Dienst wird auf dem Stammzertifizierungsserver ausgeführt. |
|Lizenzierung | Stellt eine *Endbenutzerlizenz* aus. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|
|Veröffentlichung | Erstellt eine *Veröffentlichungslizenz*, die die Richtlinien definiert, die in einer Endbenutzerlizenz aufgelistet werden können. Weitere Informationen finden Sie unter [Erstellen einer Veröffentlichungslizenz](https://msdn.microsoft.com/library/Aa362355).<p><p>Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|
|Vorzertifizierung | Ermöglicht es einem Server, ein *Rechtekontozertifikat* im Auftrag eines Benutzers anzufordern. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|
|Dienstlocator | Stellt die URL der Dienste zur Zertifizierung, Lizenzierung und Veröffentlichung von Konten für Active Directory bereit, damit diese von RMS-Clients gefunden werden können. Der Dienst wird auf Stammzertifizierungsservern und Lizenzierungsservern ausgeführt.|

## Verwandte Themen ##
* [Übersicht](ad-rms-overview.md)
* [Microsoft Internetinformationsdienste](http://www.iis.net/overview)
* [Ermöglichen der Verwendung von cloudbasiertem RMS für Ihre Dienstanwendung](how-to-use-file-api-with-aadrm-cloud.md)
* [Microsoft Windows Rights Management Services mit Service Pack 2](http://www.microsoft.com/download/en/details.aspx?id=4909)
* [Active Directory Rights Management Services (AD RMS)-Skripterstellungs-API](https://msdn.microsoft.com/library/Bb968797)
* [Aktivieren eines Computers](https://msdn.microsoft.com/library/Cc530377)
* [Aktivieren eines Benutzers](https://msdn.microsoft.com/library/Cc530378)
* [Erstellen einer Veröffentlichungslizenz](https://msdn.microsoft.com/library/Aa362355)

 

 


<!--HONumber=Jun16_HO2-->


