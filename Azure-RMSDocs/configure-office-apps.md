---
title: Konfiguration für Clients zum Verwenden von Office-Apps mit Azure RMS von AIP
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Office-Apps für den Einsatz mit dem Azure Rights Management-Dienst von Azure Information Protection.
author: mlottner
ms.author: mlottner
manager: rkarlin
ms.date: 11/30/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 7746a412225248808e02731433133fc4182874a9
ms.sourcegitcommit: 551e3f5b8956da49383495561043167597a230d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/08/2020
ms.locfileid: "86136268"
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Office-Apps: Konfiguration für Clients zur Verwendung des Azure Rights Management-Diensts

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*


Ermitteln Sie anhand dieser Informationen, was zu tun ist, damit Office-Apps zusammen mit dem Azure Rights Management-Dienst von Azure Information Protection funktionieren.

## <a name="office365-apps-office-2019-office-2016-and-office-2013"></a>Office 365-Apps, Office 2019, Office 2016 und Office 2013
Da diese neueren Versionen von Office native Unterstützung für den Azure Rights Management-Dienst bieten, ist keine Clientcomputerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (IRM) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Internet zu unterstützen. Alle Benutzer müssen für diese apps unter Windows Vorgehen, sich mit Ihren Office 365-Anmelde Informationen bei Ihren Office-Anwendungen anmelden. Sie können dann Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

### <a name="user-instructions-for-office-for-mac"></a>Benutzeranweisungen für Office für Mac

Benutzer mit Office für Mac müssen zunächst Ihre Anmelde Informationen überprüfen, bevor Sie Inhalte schützen können. Beispiel:

1. Öffnen Sie Outlook, und erstellen Sie ein Profil, indem Sie Ihr Office 365-Geschäfts-, Schul- oder Unikonto verwenden. 

2. Erstellen Sie eine neue Nachricht, und wählen Sie auf der Registerkarte **Optionen die Option** **Berechtigungen**und dann **Anmelde Informationen überprüfen**aus. Wenn Sie dazu aufgefordert werden, geben Sie die Details Ihres Office 365-Geschäfts-, Schul- oder Unikontos erneut an, und wählen Sie dann **Anmelden** aus.
    
    Mit dieser Aktion werden die Azure-Rights Management Vorlagen heruntergeladen und **überprüft, ob die Anmelde** Informationen jetzt durch Optionen ersetzt werden, die **keine Einschränkungen**, nicht **weiterleiten**und alle Azure Rights Management Vorlagen enthalten, die für Ihren Mandanten veröffentlicht werden. 

3. Sie können diese neue Nachricht jetzt abbrechen.

4. So schützen Sie eine e-Mail-Nachricht oder ein Dokument: Wählen Sie auf der Registerkarte **Optionen** die Option **Berechtigungen** aus, und wählen Sie eine Option oder eine Vorlage aus, mit der Ihre e-Mail

## <a name="office2010"></a>Office 2010
Damit Client Computer den Azure Rights Management-Dienst mit Office 2010 verwenden können, müssen Sie über den Azure Information Protection-Client (klassisch) verfügen. Es ist keine weitere Konfiguration erforderlich, als dass sich Benutzer mit ihren Office 365-Anmeldeinformationen anmelden müssen, damit sie dann Dateien schützen sowie von anderen geschützte Dateien verwenden können.

Weitere Informationen zum Azure Information Protection-Client (klassisch) finden Sie unter [Azure Information Protection Client: Installation und Konfiguration für Clients](configure-client.md).

