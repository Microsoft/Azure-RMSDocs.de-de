---
title: Benutzerdefinierte Konfigurationen – Azure Information Protection unified bezeichnungs-client
description: Informationen zum Anpassen von Azure Information Protection unified bezeichnungs-Client für Windows.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 04/17/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 5eb3a8a4-3392-4a50-a2d2-e112c9e72a78
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: a889e29079865d41405727010e3d2060ff870e95
ms.sourcegitcommit: f9077101a974459a4252e763b5fafe51ff15a16f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2019
ms.locfileid: "64767714"
---
# <a name="admin-guide-custom-configurations-for-the-azure-information-protection-unified-labeling-client"></a>Administratorhandbuch: Benutzerdefinierte Konfigurationen für den Azure Information Protection unified bezeichnungs-client

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows 7 mit SP1, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012, Windows Server 2008 R2*
>
> *Anweisungen für: [Azure Information Protection – einheitliche bezeichnungs-Client für Windows](../faqs.md#whats-the-difference-between-the-azure-information-protection-client-and-the-azure-information-protection-unified-labeling-client)*

Verwenden Sie die folgende Informationen für erweiterte Konfigurationen, die Sie möglicherweise für spezifische Szenarien oder eine Teilmenge von Benutzern bei der Verwaltung des Azure Information Protection unified bezeichnungs-Clients.

Diese Einstellungen sind erforderlich, die Registrierung bearbeiten.  

## <a name="sign-in-as-a-different-user"></a>Anmelden als ein anderer Benutzer

In einer produktionsumgebung müssen Benutzer in der Regel nicht anmelden, da ein anderer Benutzer bei der Verwendung von Azure Information Protection die Bezeichnung Client unified. Allerdings müssen Sie sich als Administrator während einer Testphase möglicherweise als anderer Benutzer anmelden. 

Mithilfe des Dialogfelds **Microsoft Azure Information Protection** können Sie prüfen, an welchem Konto Sie derzeit angemeldet sind: Öffnen Sie eine officeanwendung und klicken Sie auf die **Startseite** Registerkarte die **Vertraulichkeit** Schaltfläche, und wählen Sie dann **Hilfe und Feedback**. Ihr Kontoname wird im Abschnitt **Clientstatus** angezeigt.

Überprüfen Sie auf jeden Fall auch den Domänennamen des angezeigten angemeldeten Kontos. Es lässt sich leicht übersehen, dass Sie mit dem richtigen Kontonamen, aber bei der falschen Domäne angemeldet sind. Ein Symptom für mit dem falschen Konto enthält Fehler beim Herunterladen der Bezeichnungen, oder wird nicht angezeigt, die Bezeichnungen oder unerwartete Verhaltensweisen.

So melden Sie sich als ein anderer Benutzer an:

1. Navigieren Sie zu **%localappdata%\Microsoft\MSIP**, und löschen Sie die Datei **TokenCache**.

2. Starten Sie alle offenen Office-Anwendungen neu, und melden Sie sich mit einem anderen Benutzerkonto an. Wenn Sie eine Eingabeaufforderung in der Office-Anwendung für die Anmeldung an den Azure Information Protection-Dienst nicht angezeigt werden, zurück zu den **Microsoft Azure Information Protection** , und wählen Sie im Dialogfeld **melden Sie sich** aus der aktualisiert **Clientstatus** Abschnitt.

Darüber hinaus gilt:

- Wenn der einheitliche Bezeichnung Azure Information Protection-Client mit dem alten Konto weiterhin nach Abschluss dieser Schritte angemeldet ist, löschen Sie alle Cookies in Internet Explorer, und wiederholen Sie dann die Schritte 1 und 2.

- Wenn Sie einmaliges Anmelden nutzen, müssen Sie sich bei Windows abmelden und mit einem anderen Benutzerkonto erneut anmelden, nachdem Sie die Tokendatei gelöscht haben. Authentifiziert die einheitliche Bezeichnung Azure Information Protection-Client anschließend automatisch mit Ihrem aktuell angemeldeten Benutzerkonto.

- Diese Lösung wird unterstützt, wenn Sie sich als anderer Benutzer des gleichen Mandanten anmelden möchten. Diese Lösung wird nicht unterstützt, wenn Sie sich als anderer Benutzer eines anderen Mandanten anmelden möchten. Um Azure Information Protection mit mehreren Mandanten zu testen, verwenden Sie verschiedene Computer.

- Können Sie die **Einstellungen zurücksetzen** option **Hilfe und Feedback** melden Sie sich ab, und löschen die aktuell heruntergeladene Bezeichnungen und die Richtlinieneinstellungen von Office 365 Security & Compliance Center die Microsoft 365 Security Center oder Microsoft 365 Compliance Center.


## <a name="change-the-local-logging-level"></a>Ändern des lokalen Protokolliergrads

In der Standardeinstellung für die Azure Information Protection bezeichnungs Client schreibt Client-Dateien in unified der **%localappdata%\Microsoft\MSIP** Ordner. Diese Dateien dienen zur Problembehandlung durch den Microsoft-Support.
 
Um den Protokolliergrad für diese Dateien zu ändern, finden Sie in der Registrierung die folgenden Wertnamen, und setzen Sie den Wert auf den gewünschten Protokollierungsgrad:

**HKEY_CURRENT_USER\SOFTWARE\Microsoft\MSIP\LogLevel**

Legen Sie den Protokolliergrad auf einen der folgenden Werte fest:

- **Off**: Keine lokale Protokollierung.

- **Fehler**: Nur Fehler.

- **Info**: Minimale Protokollierung, die keine Ereignis-IDs umfasst.

- **Debug**: Vollständige Informationen.

- **Trace**: Ausführliche Protokollierung (die Standardeinstellung für Clients).

Diese Einstellung in der Registrierung ändert sich nicht auf die Informationen an Azure Information Protection für die gesendeten [zentralen reporting](../reports-aip.md).


## <a name="next-steps"></a>Nächste Schritte
Nun, da Sie den Azure Information Protection unified bezeichnungs-Client angepasst haben, finden Sie unter den folgenden Ressourcen für zusätzliche Informationen, Sie zur Unterstützung dieses Clients müssen eventuell:

- [Clientdateien und Nutzungsprotokollierung](client-admin-guide-files-and-logging.md)

- [Unterstützte Dateitypen](client-admin-guide-file-types.md)

- [PowerShell-Befehle](client-admin-guide-powershell.md)
