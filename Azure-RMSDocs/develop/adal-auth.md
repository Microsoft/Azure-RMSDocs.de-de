---
title: Konfigurieren Ihrer App für die ADAL-Authentifizierung – AIP
description: Schritte zur Konfiguration der Azure Information Protection-App für die Nutzung der ADAL-basierten Authentifizierung
keywords: authentication, RMS, ADAL, Information Protection,
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 03/13/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev, has-adal-ref
ms.openlocfilehash: 3e071a6ef2a51180a16748e4acb595866d17be78
ms.sourcegitcommit: 298843953f9792c5879e199fd1695abf3d25aa70
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/08/2020
ms.locfileid: "82971964"
---
# <a name="configure-your-app-for-adal-authentication"></a>Konfigurieren Ihrer App für die ADAL-Authentifizierung

Dieses Thema beschreibt die Schritte zum Konfigurieren Ihrer App für die ADAL-basierte (Azure Active Directory Authentication Library) Authentifizierung.

## <a name="azure-authentication-setup"></a>Einrichten der Azure-Authentifizierung

Sie benötigen Folgendes:

- Ein [Abonnement für Microsoft Azure](https://azure.microsoft.com/) (eine kostenlose Testversion ist ausreichend). Weitere Informationen finden Sie im Artikel zum [Registrieren für RMS for Individuals](../rms-for-individuals-user-sign-up.md).
- Ein Abonnement für Microsoft Azure Rights Management (ein kostenloses [RMS für Einzelpersonen](https://technet.microsoft.com/library/dn592127.aspx)-Konto ist ausreichend).

> [!NOTE]
> Fragen Sie Ihren IT-Administrator, ob Sie über ein Abonnement für Microsoft Azure Rights Management verfügen oder nicht, und lassen Sie Ihren IT-Administrator die nachstehenden Schritte ausführen. Wenn Ihre Organisation nicht über ein Abonnement verfügt, sollte Ihr IT-Administrator eines erstellen. Außerdem sollte Ihr IT-Administrator ein Geschäfts-, *Schul-oder unikonto*abonnieren, anstatt eine *Microsoft-Konto* (z.b. Hotmail).

Nach der Registrierung für Microsoft Azure:

- Melden Sie sich beim [Azure-Verwaltungsportal](https://manage.windowsazure.com) für Ihre Organisation über ein Konto mit Administratorrechten an.

![Azure-Anmeldung](../media/AzurePortalLogin.png)

- Navigieren Sie nach unten zur **Active Directory**-Anwendung auf der linken Seite des Portals.

![Active Directory auswählen](../media/AzureADPick.png)

- Wenn Sie noch kein Verzeichnis erstellt haben, wählen Sie die Schaltfläche **Neu** aus, die sich in der unteren linken Ecke des Portals befindet.

![Auswählen von NEU](../media/AzureNewBtn.png)

- Wählen Sie die Registerkarte **Rights Management** aus, und stellen Sie sicher, dass der **Rights Management-Status** entweder **Aktiv**, **Unbekannt** oder **Nicht autorisiert** ist. Wenn der Status **Inaktiv** ist, wählen Sie die Schaltfläche **Aktivieren** im unteren mittleren Bereich des Portals aus, und bestätigen Sie Ihre Auswahl.

![Auswählen von AKTIVIEREN](../media/RMTab.png)

- Erstellen Sie nun eine neue *Native Anwendung* in Ihrem Verzeichnis, indem Sie Ihr Verzeichnis und „Anwendungen“ auswählen.

![Auswählen von ANWENDUNGEN](../media/CreateNativeApp.png)

- Wählen Sie dann die Schaltfläche **Hinzufügen** aus, die sich im unteren, mittleren Bereich des Portals befindet.

![Auswählen von HINZUFÜGEN](../media/AddAppBtn.png)

- Wählen Sie an der Eingabeaufforderung **Eine von meinem Unternehmen entwickelte Anwendung hinzufügen** aus.

![Auswählen von „Eine von meinem Unternehmen entwickelte Anwendung hinzufügen“](../media/AddAnAppPick.png)

- Benennen Sie Ihre Anwendung, indem Sie **NATIVE CLIENTANWENDUNG** und die Schaltfläche **Weiter** auswählen.

![Benennen Ihrer App](../media/TellUsInput.png)

- Fügen Sie einen Umleitungs-URI hinzu, und wählen Sie „Weiter“ aus.
  Der Umleitungs-URI muss ein gültiger URI und in Ihrem Verzeichnis einmalig sein. Beispielsweise könnten Sie etwas wie `https://contoso.azurewebsites.net/.auth/login/done` verwenden.

![Hinzufügen eines Umleitungs-URI](../media/RedirectURI.png)

- Wählen Sie Ihre Anwendung im Verzeichnis und anschließend **KONFIGURIEREN** aus.

![Auswählen von KONFIGURIEREN](../media/ConfigYourApp.png)

>[!NOTE]
> Kopieren Sie die **CLIENT-ID** und den **UMLEITUNGS-URI**, und speichern Sie diese für die spätere Verwendung bei der Konfiguration des RMS-Clients.

- Navigieren Sie zum unteren Rand Ihrer Anwendungseinstellungen, und wählen Sie unter **Berechtigungen für andere Anwendungen** die Schaltfläche **Anwendung hinzufügen** aus.

>[!NOTE]
> Die für Windows Azure Active Directory angezeigten **delegierten Berechtigungen** sind standardmäßig korrekt – es darf nur eine Option ausgewählt sein, und dies ist **Ermöglichen der Anmeldung und Lesen des Benutzerprofils**.

![Auswählen von „Anwendung hinzufügen“](../media/PermissionsToOtherBtn.png)

- Wählen Sie das Pluszeichen neben **Microsoft Rights Management** aus.

![Auswählen des Pluszeichens (+)](../media/ChoosePlusBtn.png)

- Klicken Sie nun auf das Häkchen in der unteren linken Ecke des Dialogfelds.

![Klicken des Häkchens](../media/choosecheck01.png)

- Nun können Sie Ihrer Anwendung für Azure RMS eine Abhängigkeit hinzufügen. Wählen Sie zum Hinzufügen der Abhängigkeit den neuen Eintrag **Microsoft Rights Management Services** unter **Berechtigungen für andere Anwendungen** aus, und aktivieren Sie das Kontrollkästchen **Create and access protected content for users** (Geschützten Inhalt für Benutzer erstellen und darauf zugreifen) in der Dropdownliste bei **Delegierte Berechtigungen:**.

![Einrichten von Berechtigungen](../media/AddDependency.png)

- Speichern Sie Ihre Anwendung, um die Änderungen beizubehalten, indem Sie das Symbol **Speichern** im unteren, mittleren Bereich des Portals auswählen.

![Auswählen von SPEICHERN](../media/SaveApplication.png)
