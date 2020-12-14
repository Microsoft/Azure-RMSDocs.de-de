---
title: Konfiguration für Clients zum Verwenden von Office-Apps mit Azure RMS von AIP
description: Informationen und Anweisungen für Administratoren zum Konfigurieren von Office-Apps für den Einsatz mit dem Azure Rights Management-Dienst von Azure Information Protection.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/30/2019
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: ec269afe-4e87-4cc1-9144-5fbb594b412e
ms.subservice: azurerms
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: ea6b8afa02b9555924bcd1df5dfae1b7b37a217a
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383532"
---
# <a name="office-apps-configuration-for-clients-to-use-the-azure-rights-management-service"></a>Office-Apps: Konfiguration für Clients zur Verwendung des Azure Rights Management-Diensts

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified-Bezeichnungs Client und klassischer Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*


Ermitteln Sie anhand dieser Informationen, was zu tun ist, damit Office-Apps zusammen mit dem Azure Rights Management-Dienst von Azure Information Protection funktionieren.

## <a name="office-365-apps-office-2019-office-2016-and-office-2013"></a>Office 365-Apps, Office 2019, Office 2016 und Office 2013

Da diese neueren Versionen von Office integrierte Unterstützung für den Azure Rights Management-Dienst bieten, ist keine Client Computerkonfiguration erforderlich, um die Features für die Verwaltung von Informationsrechten (Information Rights Management, unm) für Anwendungen wie Word, Excel, PowerPoint, Outlook und Outlook im Web zu unterstützen. 

Alle Benutzer müssen für diese apps unter Windows Vorgehen, sich mit Ihren Microsoft 365 Anmelde Informationen bei Ihren Office-Anwendungen anmelden. Sie können dann Dateien und E-Mails schützen sowie Dateien und E-Mails verwenden, die von anderen geschützt werden.

### <a name="user-instructions-for-office-for-mac"></a>Benutzeranweisungen für Office für Mac

Benutzer mit Office für Mac müssen zunächst Ihre Anmelde Informationen überprüfen, bevor Sie Inhalte schützen können. Zum Beispiel:

1. Öffnen Sie Outlook, und erstellen Sie ein Profil mit Ihrem Microsoft 365 Geschäfts-, Schul-oder unikonto. 

2. Erstellen Sie eine neue Nachricht, und wählen Sie auf der Registerkarte **Optionen die Option** **Berechtigungen** und dann **Anmelde Informationen überprüfen** aus. Wenn **Sie dazu** aufgefordert werden, geben Sie die Details Ihres Microsoft 365 Geschäfts-, Schul-oder unikontos erneut an
    
    Mit dieser Aktion werden die Azure-Rights Management Vorlagen heruntergeladen und **überprüft, ob die Anmelde** Informationen jetzt durch Optionen ersetzt werden, die **keine Einschränkungen**, nicht **weiterleiten** und alle Azure Rights Management Vorlagen enthalten, die für Ihren Mandanten veröffentlicht werden. 

3. Sie können diese neue Nachricht jetzt abbrechen.

4. So schützen Sie eine e-Mail-Nachricht oder ein Dokument: Wählen Sie auf der Registerkarte **Optionen** die Option **Berechtigungen** aus, und wählen Sie eine Option oder eine Vorlage aus, mit der Ihre e-Mail

## <a name="office-2010"></a>Office 2010

Damit Clientcomputer den Azure Rights Management-Dienst mit Office 2010 verwenden können, müssen sie über den Azure Information Protection-Client verfügen. Es ist keine weitere Konfiguration erforderlich, außer wenn sich Benutzer mit Ihren Microsoft 365 Anmelde Informationen anmelden müssen, und Sie können dann Dateien schützen und von anderen geschützte Dateien verwenden.

Weitere Informationen finden Sie unter [Azure Information Protection-Client: Installation und Konfiguration für Clients](configure-client.md).

