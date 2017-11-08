---
title: Konfigurieren der Azure Information Protection-Richtlinie
description: "Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 10/25/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: b04c7881f982b33094107b6de33920a83b17b960
ms.sourcegitcommit: a7cdf911088fdf663e43894484530ea15150284f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2017
---
# <a name="configuring-the-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

## <a name="subscription-support"></a>Abonnementsupport

Azure Information Protection unterstützt verschiedene Abonnementebenen:

- Azure Information Protection P2: Unterstützung für alle Klassifizierungs-, Bezeichnungs- und Schutzfunktionen

- Azure Information Protection P1: Unterstützung für die meisten Klassifizierungs-, Bezeichnungs- und Schutzfunktionen, jedoch keine automatische Klassifizierung oder HYOK

- Office 365, einschließlich des Azure Rights Management-Diensts: Unterstützung für Schutzfunktionen, jedoch keine Klassifizierung und Bezeichnung

Optionen, die ein Azure Information Protection P2-Abonnement erfordern, werden im Portal identifiziert.

Wenn in Ihrer Organisation eine Kombination aus verschiedenen Abonnements vorhanden ist, liegt es in Ihrer Verantwortung, sicherzustellen, dass Benutzer keine Features verwenden, für die ihr Konto nicht lizenziert ist. Der Azure Information Protection-Client ist nicht für die Überprüfung und Erzwingung von Lizenzen zuständig. Wenn Sie Optionen konfigurieren, für die nicht alle Benutzer eine Lizenz besitzen, verwenden Sie bereichsbezogene Richtlinien oder eine Registrierungseinstellung, um sicherzustellen, dass Ihre Organisation die Lizenzbestimmungen einhält:

- **In Ihrer Organisation ist eine Kombination aus Azure Information Protection P1- und Azure Information Protection P2-Lizenzen vorhanden**: Erstellen und verwenden Sie mindestens eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für Benutzer mit einer P2-Lizenz, wenn Sie Optionen konfigurieren, die eine Azure Information Protection P2-Lizenz erfordern. Stellen Sie sicher, dass Ihre globale Richtlinie keine Optionen umfasst, die eine Azure Information Protection P2-Lizenz erfordern.

- **In Ihrer Organisation ist ein Abonnement für Azure Information Protection vorhanden, einige Benutzer verfügen aber nur über eine Lizenz für Office 365, die den Azure Rights Management-Dienst umfasst**: Bearbeiten Sie die Registrierung auf den Computern derjenigen Benutzer, die keine Lizenz für Azure Information Protection besitzen, damit diese Benutzer die Azure Information Protection-Richtlinie nicht herunterladen können. Anweisungen dazu finden Sie im Administratorhandbuch für die folgende Anpassung: [Erzwingen des reinen Schutzmodus, wenn die Organisation über eine Kombination verschiedener Lizenzen verfügt](../rms-client/client-admin-guide-customizations.md#enforce-protection-only-mode-when-your-organization-has-a-mix-of-licenses).

Weitere Informationen zu Abonnements finden Sie unter [Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

## <a name="to-access-the-azure-information-protection-blade-for-the-first-time"></a>Der Erste Zugriff auf das Blatt „Azure Information Protection“

1. Melden Sie sich als globaler Administrator oder Sicherheitsadministrator für Ihren Mandanten beim [Azure-Portal](https://portal.azure.com) an.

2. Klicken Sie im Hubmenü auf **Neu**, und wählen Sie dann in der Liste **MARKETPLACE** die Option **Sicherheit und Identität** aus. 
    
3. Wählen Sie auf dem Blatt **Sicherheit und Identität** in der Liste **AUSGEWÄHLTE APPS** die Option **Azure Information Protection** aus. Klicken Sie dann auf dem Blatt **Azure Information Protection** auf **Erstellen**.
    
    Dadurch wird das Blatt **Azure Information Protection** für Ihren Mandanten erstellt. Wenn Sie sich das nächste Mal beim Portal anmelden, können Sie den Dienst im Hubmenü aus der Liste unter **Weitere Dienste** auswählen. 
    
    > [!TIP] 
    > Wählen Sie **An das Dashboard anheften** zum Erstellen einer **Azure Information Protection**-Kachel auf Ihrem Dashboard aus, damit Sie bei der nächsten Anmeldung nicht erneut nach dem Dienst suchen müssen können.

4. Beachten Sie die Seite **Schnellstart**, die automatisch geöffnet wird, wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen. Durchsuchen Sie die empfohlenen Ressourcen, oder verwenden Sie andere Menüoptionen. Verwenden Sie das folgende Verfahren, um Bezeichnungen, die Benutzer auswählen können, zu konfigurieren.

Wenn Sie das nächste Mal auf das Blatt **Azure Information Protection** zugreifen, wählt es automatisch die Option **Richtlinien** > **Globale Richtlinie** aus, damit Sie die Bezeichnungen für alle Benutzer konfigurieren können. Über das Menü **Allgemein** können Sie zur **Schnellstart**-Seite zurückkehren.

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Informationen zum Konfigurieren der Azure Information Protection-Richtlinie

1. Überprüfen Sie, ob Sie im [Azure-Portal](https://portal.azure.com) als Sicherheitsadministrator oder globaler Administrator angemeldet sind.

2. Wenn nötig, navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Weitere Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 
    
    Das Blatt **Azure Information Protection: Globale Richtlinien** öffnet sich automatisch, damit Sie die globale Richtlinie ansehen und bearbeiten können, die für alle Benutzer konfiguriert wird. 
    
    Die Azure Information Protection-Richtlinie enthält die folgenden Elemente, die Sie konfigurieren können:
    
    - Bezeichnungen, mit denen Sie und Ihre Benutzer Dokumente und E-Mails klassifizieren können.
    
    - Einen Titel und eine QuickInfo für die Information Protection-Leiste, die in den Office-Anwendungen von Benutzern angezeigt wird.
    
    - Die Option zum Erzwingen einer Klassifizierung, wenn Benutzer Dokumente speichern und E-Mails senden.
    
    - Die Option zum Festlegen einer Standardbezeichnung als Ausgangspunkt für die Klassifizierung von Dokumenten und E-Mails.
    
    - Die Option, um Benutzer zur Angabe einer Begründung aufzufordern, wenn sie eine Bezeichnung mit einer niedrigeren Vertraulichkeitsstufe wählen.
    
    - Die Möglichkeit zum automatischen Bezeichnen einer E-Mail-Nachricht nach deren Anlagen.
    
    - Die Möglichkeit zum Bereitstellen eines benutzerdefinierten Hilfelinks für Benutzer.

Azure Information Protection enthält eine [Standardrichtlinie](configure-policy-default.md) mit fünf Hauptbezeichnungen. Zwei dieser Bezeichnungen enthalten untergeordnete Bezeichnungen für Unterkategorien, falls diese benötigt werden. Wenn eine Bezeichnung für untergeordnete Bezeichnungen konfiguriert wird, können Benutzer den Hauptbezeichner nicht auswählen und müssen stattdessen eine der untergeordneten Bezeichnungen auswählen.

Die Azure Information Protection-Bezeichnungen können mit dem vollständigen Bereich von Daten verwendet werden, die ein Unternehmen in der Regel erstellt und speichert – von der niedrigsten Klassifizierung für persönliche Daten bis zur höchsten Klassifizierung für streng vertrauliche Daten. 

Sie können die Standardbezeichnungen unverändert verwenden, diese Bezeichnungen anpassen oder löschen und neue Bezeichnungen erstellen. Weitere Informationen zu den gewünschten Optionen und deren Konfiguration finden Sie unter den Links im nächsten Abschnitt.

Sie können eine beliebige Anzahl von Bezeichnungen erstellen. Wenn jedoch so viele Bezeichnungen vorhanden sind, dass Benutzer nur schwer die richtige auswählen können, sollten Sie bereichsbezogene Richtlinien erstellen, damit Benutzern nur relevante Bezeichnungen angezeigt werden. Die Höchstgrenze für Bezeichnungen, die Schutz anwenden, beträgt 500.

Wenn Sie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen.

Klicken Sie auf **Publish** (Veröffentlichen), wenn Sie alle gewünschten Änderungen vorgenommen haben. 

Beim Start einer unterstützten Office-Anwendung prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Gegebenenfalls lädt der Client diese Änderungen dann als neueste Azure Information Protection-Richtlinie herunter. Folgende zusätzliche Trigger aktualisieren die Richtlinie im Client ebenfalls:

- Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen.

- Ausführen der [PowerShell-Cmdlets](../rms-client/client-admin-guide-powershell.md) zur Bezeichnung und zum Schutz (Get-AIPFileStatus, Set-AIPFileClassification und Set-AIPFileLabel).

- Alle 24 Stunden.

- Für die [Azure Information Protection-Überprüfung](deploy-aip-scanner.md): Wenn der Dienst gestartet wird sowie jede Stunde.


>[!NOTE]
>Wenn der Client die Richtlinie herunterlädt, sollten Sie mit einigen Minuten Wartezeit rechnen, bevor sie vollständig einsatzbereit ist. Die tatsächliche Zeit hängt von Faktoren wie der Größe und Komplexität der Richtlinienkonfiguration und der Netzwerkkonnektivität ab. Wenn die resultierende Aktion Ihrer Bezeichnungen nicht mit Ihren letzten Änderungen übereinstimmt, sollten Sie bis zu 15 Minuten warten und es dann erneut versuchen.

### <a name="configuring-your-organizations-policy"></a>Konfigurieren der Richtlinie Ihrer Organisation

Über die folgenden Links können Sie auf Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zugreifen:

- [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md)

- [Konfigurieren der Richtlinieneinstellungen](configure-policy-settings.md)

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection](configure-policy-delete-reorder.md)

- [Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection](configure-policy-change-label.md)

- [Konfigurieren einer Bezeichnung zum Schutz](configure-policy-protection.md)

- [Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection](configure-policy-markings.md)

- [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)

- [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md)

- [Informationen zum Konfigurieren und Verwalten von Vorlagen](configure-policy-templates.md)

- [Informationen zum Konfigurieren von Bezeichnungen für verschiedene Sprachen](configure-policy-languages.md)

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
