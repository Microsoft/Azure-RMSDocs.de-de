---
title: Konfiguration für Clients zum Verwenden von Office-Apps mit Azure RMS von AIP
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Office-Apps für den Einsatz mit dem Azure Rights Management-Dienst von Azure Information Protection.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 09/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 6bde980df23bdfa11bd137966ab48221bdbe6512
ms.sourcegitcommit: 319c0691509748e04aecf839adaeb3b5cac2d2cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2019
ms.locfileid: "71684207"
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Office-Apps: Konfiguration für Clients zur Verwendung des Azure Rights Management-Diensts

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Ermitteln Sie anhand dieser Informationen, was zu tun ist, damit Office-Apps zusammen mit dem Azure Rights Management-Dienst von Azure Information Protection funktionieren.

## <a name="office365-apps-office-2019-office-2016-and-office-2013"></a>Office 365-apps, Office 2019, Office 2016 und Office 2013
Da diese neueren Versionen von Office native Unterstützung für den Azure Rights Management-Dienst bieten, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Internet zu unterstützen. Alle Benutzer müssen für diese apps unter Windows Vorgehen, sich mit Ihren Office 365-Anmelde Informationen bei Ihren Office-Anwendungen anmelden. Sie können dann Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

### <a name="user-instructions-for-office-for-mac"></a>Benutzeranweisungen für Office für Mac

Benutzer mit Office für Mac müssen zunächst Ihre Anmelde Informationen überprüfen, bevor Sie Inhalte schützen können. Zum Beispiel:

1. Öffnen Sie Outlook, und erstellen Sie ein Profil mit Ihrem Geschäfts-, Schul- oder Unikonto bei Office 365. 

2. Erstellen Sie eine neue Nachricht, und wählen Sie auf der Registerkarte **Optionen die Option** **Berechtigungen**und dann **Anmelde Informationen überprüfen**aus. Geben Sie nach entsprechender Aufforderung die Details zu Ihrem Geschäfts-, Schul- oder Unikonto bei Office 365 an, und wählen Sie **Anmelden**.
    
    Mit dieser Aktion werden die Azure-Rights Management Vorlagen heruntergeladen und **überprüft, ob die Anmelde** Informationen jetzt durch Optionen ersetzt werden, die **keine Einschränkungen**, nicht **weiterleiten**und alle Azure Rights Management Vorlagen enthalten, die für Ihre Tenant. 

3. Sie können diese neue Nachricht nun abbrechen.

4. So schützen Sie eine E-Mail-Nachricht oder ein Dokument: Wählen Sie auf der Registerkarte **Optionen** **Berechtigungen** aus, und wählen Sie eine Option oder eine Vorlage aus, die Ihre e-Mail oder Ihr Dokument schützt.

## <a name="office2010"></a>Office 2010
Damit Client Computer den Azure Rights Management-Dienst mit Office 2010 verwenden können, müssen Sie über den Azure Information Protection-Client (klassisch) verfügen. Es ist keine weitere Konfiguration erforderlich, als dass sich Benutzer mit ihren Office 365-Anmeldeinformationen anmelden müssen, damit sie dann Dateien schützen sowie von anderen geschützte Dateien verwenden können.

Weitere Informationen zum Azure Information Protection-Client (klassisch) finden Sie unter [azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

