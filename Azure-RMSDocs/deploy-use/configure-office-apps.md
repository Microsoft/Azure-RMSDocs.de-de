---
title: "Konfiguration für Clients zum Verwenden von Office-Apps mit Azure RMS von AIP"
description: "Informationen und Anweisungen für Administratoren zum Konfigurieren von Office-Apps für den Einsatz mit dem Azure Rights Management-Dienst von Azure Information Protection."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 52b3942d7918ada46cbdd7b45ed3925817e75f45
ms.sourcegitcommit: 55a71f83947e7b178930aaa85a8716e993ffc063
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2017
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Office-Apps: Konfiguration für Clients zur Verwendung des Azure Rights Management-Diensts

>*Gilt für: Azure Information Protection, Office 365*


Ermitteln Sie anhand dieser Informationen, was zu tun ist, damit Office-Apps zusammen mit dem Azure Rights Management-Dienst von Azure Information Protection funktionieren.

## <a name="office-2016-and-office-2013"></a>Office 2016 und Office 2013
Da diese neueren Versionen von Office native Unterstützung für den Azure Rights Management-Dienst bieten, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Internet zu unterstützen. Alles, was Benutzer tun müssen, ist, sich bei Ihren Office-Anwendungen mit ihren [!INCLUDE[o365_1](../includes/o365_1_md.md)]-Anmeldeinformationen anzumelden. Sie können dann Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

Wir empfehlen jedoch, dass Sie diese Anwendungen durch den Azure Information Protection-Client ergänzen, damit Ihre Benutzer von dem Office-Add-In und der Unterstützung zusätzlicher Dateitypen profitieren können. Weitere Informationen finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

## <a name="office-2010"></a>Office 2010
Damit Clientcomputer den Azure Rights Management-Dienst mit Office 2010 verwenden können, müssen sie über den Azure Information Protection-Client oder die Rights Management-Freigabeanwendung für Windows verfügen. Es ist keine weitere Konfiguration erforderlich, als dass sich Benutzer mit ihren [!INCLUDE[o365_1](../includes/o365_1_md.md)]-Anmeldeinformationen anmelden müssen, damit sie dann Dateien schützen sowie von anderen geschützte Dateien verwenden können.

Weitere Informationen zum Azure Information Protection-Client finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
