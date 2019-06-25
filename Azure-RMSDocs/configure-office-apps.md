---
title: Konfiguration für Clients zum Verwenden von Office-Apps mit Azure RMS von AIP
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Office-Apps für den Einsatz mit dem Azure Rights Management-Dienst von Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 06/24/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.suite: ems
ms.openlocfilehash: 09f7eaaaafb6c1ecbce584876a7e8bf254e0c0d5
ms.sourcegitcommit: 2af2297319265c1f91aa76eb227c6f4d316df42a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348808"
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Office-Apps: Konfiguration für Clients zur Verwendung des Azure Rights Management-Diensts

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Ermitteln Sie anhand dieser Informationen, was zu tun ist, damit Office-Apps zusammen mit dem Azure Rights Management-Dienst von Azure Information Protection funktionieren.

## <a name="office365-apps-office-2019-office-2016-and-office-2013"></a>Office 365-apps, Office 2019, Office 2016 und Office 2013
Da diese neueren Versionen von Office native Unterstützung für den Azure Rights Management-Dienst bieten, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Internet zu unterstützen. Alle Benutzer für diese apps auf Windows ausführen, ist bei ihren Office-Anwendungen mit ihren Office 365-Anmeldeinformationen anmelden. Sie können dann Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

### <a name="user-instructions-for-office-for-mac"></a>Anweisungen für Benutzer für Office für Mac

Benutzer mit Office für Mac müssen zunächst ihre Anmeldeinformationen überprüfen, bevor sie Inhalte schützen können. Zum Beispiel:

1. Öffnen Sie Outlook, und erstellen Sie ein Profil mit Ihrem Geschäfts-, Schul- oder Unikonto bei Office 365. 

2. Erstellen Sie eine neue Nachricht und klicken Sie auf die **Optionen** Registerkarte **Berechtigungen**, und wählen Sie dann **Anmeldeinformationen überprüfen**. Geben Sie nach entsprechender Aufforderung die Details zu Ihrem Geschäfts-, Schul- oder Unikonto bei Office 365 an, und wählen Sie **Anmelden**.
    
    Dadurch wird heruntergeladen, die Azure Rights Management-Vorlagen und **Anmeldeinformationen überprüfen** wurde ersetzt durch Optionen wie **keine Einschränkungen**, **nicht weiterleiten**, und Alle Azure Rights Management-Vorlagen, die für Ihren Mandanten veröffentlicht werden. 

3. Sie können diese neue Nachricht nun abbrechen.

4. So schützen Sie eine E-Mail-Nachricht oder ein Dokument: Auf der **Optionen** Registerkarte **Berechtigungen** , und wählen Sie eine Option oder die Vorlage, die Ihre e-Mail-Adresse oder Ihr Dokument schützt.

## <a name="office2010"></a>Office 2010
Damit Clientcomputer den Azure Rights Management-Dienst mit Office 2010 verwenden müssen sie den Azure Information Protection-Client (klassisch) verfügen. Es ist keine weitere Konfiguration erforderlich, als dass sich Benutzer mit ihren Office 365-Anmeldeinformationen anmelden müssen, damit sie dann Dateien schützen sowie von anderen geschützte Dateien verwenden können.

Weitere Informationen zu den Azure Information Protection-Client (klassisch), finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

