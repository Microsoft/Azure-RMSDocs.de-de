---
title: Konfigurieren der Azure Information Protection-Richtlinie
description: Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 11/13/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 9813f71535de9058c2cb3382ae590ba5f8102fd1
ms.sourcegitcommit: ad37950f6a747c86f6496c6de859e18446f9b03f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2018
ms.locfileid: "51644793"
---
# <a name="configuring-the-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*

Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

Die Richtlinie enthält Bezeichnungen und Einstellungen:

- Durch Bezeichnungen erhalten Dokumente und E-Mails einen Klassifizierungswert: Diese Inhalte können optional durch Bezeichnungen geschützt werden. Der Azure Information Protection-Client zeigt diese Bezeichnungen für Ihre Benutzer in Office-Apps, und wenn Benutzer im Datei-Explorer mit der rechten Maustaste klicken, an. Diese Bezeichnungen können auch mithilfe von PowerShell und der Azure Information Protection-Überprüfung angewendet werden.

- Diese Einstellungen ändern das Standardverhalten des Azure Information Protection-Clients. Sie können beispielsweise eine Standardbezeichnung auswählen, die angibt, ob alle Dokumente und E-Mails über eine Bezeichnung verfügen müssen, und ob die Azure Information Protection-Leiste in Office-Apps angezeigt wird.

## <a name="subscription-support"></a>Abonnementsupport

Azure Information Protection unterstützt verschiedene Abonnementebenen:

- Azure Information Protection P2: Unterstützung für alle Klassifizierungs-, Bezeichnungs- und Schutzfunktionen

- Azure Information Protection P1: Unterstützung für die meisten Klassifizierungs-, Bezeichnungs- und Schutzfunktionen, jedoch keine automatische Klassifizierung oder HYOK

- Office 365, einschließlich des Azure Rights Management-Diensts: Unterstützung für Schutzfunktionen, jedoch keine Klassifizierung und Bezeichnung

Optionen, die ein Azure Information Protection P2-Abonnement erfordern, werden im Portal identifiziert.

Wenn in Ihrer Organisation eine Kombination aus verschiedenen Abonnements vorhanden ist, liegt es in Ihrer Verantwortung, sicherzustellen, dass Benutzer keine Features verwenden, für die ihr Konto nicht lizenziert ist. Der Azure Information Protection-Client ist nicht für die Überprüfung und Erzwingung von Lizenzen zuständig. Wenn Sie Optionen konfigurieren, für die nicht alle Benutzer eine Lizenz besitzen, verwenden Sie bereichsbezogene Richtlinien oder eine Registrierungseinstellung, um sicherzustellen, dass Ihre Organisation die Lizenzbestimmungen einhält:

- **In Ihrer Organisation ist eine Kombination aus Azure Information Protection P1- und Azure Information Protection P2-Lizenzen vorhanden**: Erstellen und verwenden Sie mindestens eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für Benutzer mit einer P2-Lizenz, wenn Sie Optionen konfigurieren, die eine Azure Information Protection P2-Lizenz erfordern. Stellen Sie sicher, dass Ihre globale Richtlinie keine Optionen umfasst, die eine Azure Information Protection P2-Lizenz erfordern.

- **In Ihrer Organisation ist ein Abonnement für Azure Information Protection vorhanden, einige Benutzer verfügen aber nur über eine Lizenz für Office 365, die den Azure Rights Management-Dienst umfasst**: Bearbeiten Sie die Registrierung auf den Computern derjenigen Benutzer, die keine Lizenz für Azure Information Protection besitzen, damit diese Benutzer die Azure Information Protection-Richtlinie nicht herunterladen können. Anweisungen dazu finden Sie im Administratorhandbuch für die folgende Anpassung: [Erzwingen des reinen Schutzmodus, wenn die Organisation über eine Kombination verschiedener Lizenzen verfügt](./rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Weitere Informationen zu Abonnements finden Sie unter [Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?](faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="signing-in-to-the-azure-portal"></a>Anmelden beim Azure-Portal

So melden Sie sich beim Azure-Portal an, um Azure Information Protection zu konfigurieren und zu verwalten:

- Verwenden Sie den folgenden Link: https://portal.azure.com

- Verwenden Sie ein Konto mit einer der folgenden [Administratorrollen](/azure/active-directory/active-directory-assign-admin-roles-azure-portal):
    
    - **Information Protection-Administrator**

    - **Sicherheitsadministrator**

    - **Globaler Administrator/Unternehmensadministrator**
    
    > [!NOTE] 
    > Wenn Ihr Mandant zum einheitlichen Bezeichnungsspeicher migriert wurde, um Bezeichnungen über das Azure-Portal zu verwalten, benötigt Ihr Konto auch Zugriffsberechtigungen für das Office 365 Security & Compliance Center. [Weitere Informationen](configure-policy-migrate-labels.md#important-information-about-administrative-roles)

## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Der Erste Zugriff auf das Blatt „Azure Information Protection“

1. Melden Sie sich im Azure-Portal an.

2. Wählen Sie im Hubmenü die Option **Ressource erstellen** aus, und geben Sie dann im Suchfeld für den Marketplace **Azure Information Protection** ein. 
    
3. Wählen Sie aus den Ergebnisliste **Azure Information Protection** aus. Klicken Sie auf dem Blatt **Azure Information Protection** auf **Erstellen**.
    
    > [!TIP] 
    > Wählen Sie optional **An Dashboard anheften** aus, um eine **Azure Information Protection**-Kachel auf Ihrem Dashboard zu erstellen, damit Sie bei der nächsten Anmeldung beim Portal nicht erneut nach dem Dienst suchen müssen können.
    
    Klicken Sie erneut auf **Erstellen**.

4. Beachten Sie die Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Durchsuchen Sie die empfohlenen Ressourcen, oder verwenden Sie andere Menüoptionen. Verwenden Sie das folgende Verfahren, um Bezeichnungen, die Benutzer auswählen können, zu konfigurieren.

Wenn Sie das nächste Mal auf das Blatt **Azure Information Protection** zugreifen, wählt es automatisch die Option **Bezeichnungen** aus, damit Sie die Bezeichnungen für alle Benutzer anzeigen und konfigurieren können. Über das Menü **Allgemein** können Sie zur **Schnellstart**-Seite zurückkehren.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Informationen zum Konfigurieren der Azure Information Protection-Richtlinie

1. Stellen Sie sicher, dass Sie sich beim Azure-Portal mit einer der folgenden Administratorrollen angemeldet haben: Information Protection-Administrator, Sicherheitsadministrator oder globaler Administrator. Im [vorherigen Abschnitt](#signing-in-to-the-azure-portal) finden Sie weitere Informationen zu diesen Administratorrollen.

2. Wenn nötig, navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Alle Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 
    
    Das Blatt **Azure Information Protection: Bezeichnungen** wird automatisch geöffnet, damit Sie die verfügbaren Bezeichnungen anzeigen und bearbeiten können. Die Bezeichnungen können allen Benutzern, ausgewählten Benutzern oder keinem Benutzer zur Verfügung gestellt werden, indem diese zu einer Richtlinie hinzugefügt oder daraus entfernt werden.

3. Wählen Sie aus den Menüoptionen die Option **Richtlinien** aus, um die Richtlinien anzuzeigen und zu bearbeiten. Wählen Sie die Richtlinie **Global** aus, um die Richtlinie anzuzeigen und zu bearbeiten, die von sämtlichen Benutzern abgerufen werden kann. Klicken Sie auf **Neue Richtlinie hinzufügen**, um eine benutzerdefinierte Richtlinie für ausgewählte Benutzer zu erstellen.
    

### <a name="making-changes-to-the-policy"></a>Vornehmen von Änderungen an der Richtlinie

Sie können eine beliebige Anzahl von Bezeichnungen erstellen. Wenn jedoch so viele Bezeichnungen vorhanden sind, dass Benutzer nur schwer die richtige auswählen können, sollten Sie bereichsbezogene Richtlinien erstellen, damit Benutzern nur relevante Bezeichnungen angezeigt werden. Die Höchstgrenze für Bezeichnungen, die Schutz anwenden, beträgt 500.

Wenn Sie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen. Wenn Sie Änderungen in einer Richtlinie speichern oder Änderungen an Bezeichnungen vornehmen, die zu Richtlinien hinzugefügt werden, werden diese Änderungen automatisch veröffentlicht. Es gibt keine gesonderte Veröffentlichungsoption.

Beim Start einer unterstützten Office-Anwendung prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Gegebenenfalls lädt der Client diese Änderungen dann als neueste Azure Information Protection-Richtlinie herunter. Folgende zusätzliche Trigger aktualisieren die Richtlinie im Client ebenfalls:

- Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen.

- Ausführen der [PowerShell-Cmdlets](./rms-client/client-admin-guide-powershell.md) zur Bezeichnung und zum Schutz (Get-AIPFileStatus, Set-AIPFileClassification und Set-AIPFileLabel).

- Alle 24 Stunden.

- Für die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md): Wenn der Dienst gestartet wird (wenn die Richtlinie älter als eine Stunde ist) und jede Stunde während des Vorgangs.


>[!NOTE]
>Wenn der Client die Richtlinie herunterlädt, sollten Sie mit einigen Minuten Wartezeit rechnen, bevor sie vollständig einsatzbereit ist. Die tatsächliche Zeit hängt von Faktoren wie der Größe und Komplexität der Richtlinienkonfiguration und der Netzwerkkonnektivität ab. Wenn die resultierende Aktion Ihrer Bezeichnungen nicht mit Ihren letzten Änderungen übereinstimmt, sollten Sie bis zu 15 Minuten warten und es dann erneut versuchen.

### <a name="configuring-your-organizations-policy"></a>Konfigurieren der Richtlinie Ihrer Organisation

Über die folgenden Links können Sie auf Informationen zum Konfigurieren der Azure Information Protection-Richtlinie zugreifen:

- [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md)

- [Konfigurieren der Richtlinieneinstellungen](configure-policy-settings.md)

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Hinzufügen oder Entfernen einer Bezeichnung](configure-policy-add-remove-label.md)
 
- [Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection](configure-policy-delete-reorder.md)

- [Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection](configure-policy-change-label.md)

- [Konfigurieren einer Bezeichnung zum Schutz](configure-policy-protection.md)

- [Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection](configure-policy-markings.md)

- [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)

- [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md)

- [Informationen zum Konfigurieren und Verwalten von Vorlagen](configure-policy-templates.md)

- [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md)

- [Migrieren von Azure Information Protection-Bezeichnungen zum Office 365 Security & Compliance Center](configure-policy-migrate-labels.md)

## <a name="next-steps"></a>Nächste Schritte

Beispiele zum Anpassen der Azure Information Protection-Richtlinie und das resultierende Verhalten für Benutzer finden Sie in den folgenden Tutorials:

- [Tutorial: Bearbeiten der Azure Information Protection-Richtlinie und Erstellen einer neuen Bezeichnung](infoprotect-quick-start-tutorial.md)

- [Tutorial: Konfigurieren von Azure Information Protection-Richtlinieneinstellungen, die nahtlos funktionieren](infoprotect-settings-tutorial.md)

Unter [Berichterstellung für Azure Information Protection](reports-aip.md) erfahren Sie, wie Ihre Richtlinie ausgeführt wird.
