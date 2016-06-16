---
# required metadata

title: Konfigurieren von Azure RMS für die ADAL-Authentifizierung | Azure RMS
description: Erläutert die Schritte zum Konfigurieren der Azure ADAL-basierten Authentifizierung
keywords: authentication, RMS, ADAL
author: bruceperlerms
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: f89f59b7-33d1-4ab3-bb64-1e9bda269935

# optional metadata

#ROBOTS:
audience: developer
#ms.devlang:
ms.reviewer: shubhamp
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurieren von Azure RMS für die ADAL-Authentifizierung

In diesem Thema werden die Schritte zum Konfigurieren der Azure ADAL-basierten Authentifizierung beschrieben.

## Interne Authentifizierung

Folgendes wird benötigt:

- Ein [Abonnement für Microsoft Azure](https://azure.microsoft.com/en-us/) (eine kostenlose Testversion ist ausreichend):
- Ein Abonnement für Microsoft Azure Rights Management (ein kostenloses [RMS für Einzelpersonen](https://technet.microsoft.com/en-us/library/dn592127.aspx)-Konto ist ausreichend).

> [!NOTE] Fragen Sie Ihren IT-Administrator, ob Sie über ein Abonnement für Microsoft Azure Rights Management verfügen oder nicht, und lassen Sie Ihren IT-Administrator die nachstehenden Schritte ausführen. Wenn Ihre Organisation nicht über ein Abonnement verfügt, sollte Ihr IT-Administrator eines erstellen. Ihr IT-Administrator sollte das Abonnement zudem mit einem *Geschäfts-, Schul- oder Unikonto* und nicht mit einem *Microsoft-Konto* (z.B. Hotmail) erstellen.

Nach der Registrierung für Microsoft Azure:

- Melden Sie sich beim [Azure-Verwaltungsportal](https://manage.windowsazure.com) für Ihre Organisation über ein Konto mit Administratorrechten an.

![Azure-Anmeldung](../media/AzurePortalLogin.png)

- Navigieren Sie nach unten zur **Active Directory**-Anwendung auf der linken Seite des Portals.

![Auswählen von „Active Directory“](../media/AzureADPick.png)

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
  Der Umleitungs-URI muss ein gültiger URI und in Ihrem Verzeichnis einmalig sein. Beispielsweise könnten Sie etwas wie `com.mycompany.myapplication://authorize` verwenden.

![Hinzufügen eines Umleitungs-URI](../media/RedirectURI.png)

- Wählen Sie Ihre Anwendung im Verzeichnis und anschließend **KONFIGURIEREN** aus.

![Auswählen von KONFIGURIEREN](../media/ConfigYourApp.png)

>[!NOTE] Kopieren Sie die **CLIENT-ID** und den **UMLEITUNGS-URI**, und speichern Sie diese für die spätere Verwendung bei der Konfiguration des RMS-Clients.

- Navigieren Sie zum unteren Rand Ihrer Anwendungseinstellungen, und wählen Sie unter **Berechtigungen für andere Anwendungen** die Schaltfläche **Anwendung hinzufügen** aus.

>[!NOTE] Die für Windows Azure Active Directory angezeigten **delegierten Berechtigungen** sind standardmäßig korrekt – es darf nur eine Option ausgewählt sein, und dies ist **Ermöglichen der Anmeldung und Lesen des Benutzerprofils**.

![Auswählen von „Anwendung hinzufügen“](../media/PermissionsToOtherBtn.png)

- Geben Sie nun die GUID `00000012-0000-0000-c000-000000000000` in das Eingabefeld **Beginnend mit** ein, und klicken Sie auf das Häkchen.

![Hinzufügen der GUID](../media/AddGUID.png)

- Wählen Sie das Pluszeichen neben **Microsoft Rights Management** aus.

![Auswählen des Pluszeichens (+)](../media/ChoosePlusBtn.png)

- Klicken Sie nun auf das Häkchen in der unteren linken Ecke des Dialogfelds.

![Klicken des Häkchens](../media/ChooseCheck.png)

- Nun können Sie Ihrer Anwendung für Azure RMS eine Abhängigkeit hinzufügen. Wählen Sie zum Hinzufügen der Abhängigkeit den neuen Eintrag **Microsoft Rights Management Services** unter **Berechtigungen für andere Anwendungen** aus, und aktivieren Sie das Kontrollkästchen **Create and access protected content for users** (Geschützten Inhalt für Benutzer erstellen und darauf zugreifen) in der Dropdownliste bei **Delegierte Berechtigungen:**.

![Einrichten von Berechtigungen](../media/AddDependency.png)

- Speichern Sie Ihre Anwendung, damit die Änderungen beibehalten werden, indem Sie das Symbol **Speichern** im unteren, mittleren Bereich des Portals auswählen.

![Auswählen von SPEICHERN](../media/SaveApplication.png)


<!--HONumber=Jun16_HO2-->


