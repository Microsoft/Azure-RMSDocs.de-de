---
title: Konfiguration für Clients zum Verwenden von Office-Apps mit Azure RMS von AIP
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Office-Apps für den Einsatz mit dem Azure Rights Management-Dienst von Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: ''
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 14582c362fe94e1e6ed44f3cc8e152d484d869cf
ms.sourcegitcommit: 5fdf013fe05b65517b56245e1807875d80be6e70
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39491063"
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Office-Apps: Konfiguration für Clients zur Verwendung des Azure Rights Management-Diensts

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Ermitteln Sie anhand dieser Informationen, was zu tun ist, damit Office-Apps zusammen mit dem Azure Rights Management-Dienst von Azure Information Protection funktionieren.

## <a name="office-2016-and-office-2013"></a>Office 2016 und Office 2013
Da diese neueren Versionen von Office native Unterstützung für den Azure Rights Management-Dienst bieten, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Internet zu unterstützen. Benutzer müssen sich lediglich mit ihren Rights Management-Anmeldeinformationen bei den Office-Anwendungen anmelden. Sie können dann Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

Wir empfehlen jedoch, dass Sie diese Anwendungen durch den Azure Information Protection-Client ergänzen, damit Ihre Benutzer von dem Office-Add-In und der Unterstützung zusätzlicher Dateitypen profitieren können. Weitere Informationen finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

## <a name="office-2010"></a>Office 2010
Damit Clientcomputer den Azure Rights Management-Dienst mit Office 2010 verwenden können, müssen sie über den Azure Information Protection-Client oder die Rights Management-Freigabeanwendung für Windows verfügen. Es ist keine weitere Konfiguration erforderlich, als dass sich Benutzer mit ihren Rights Management-Anmeldeinformationen anmelden müssen, damit sie dann Dateien schützen sowie von anderen geschützte Dateien verwenden können.

Weitere Informationen zum Azure Information Protection-Client finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

