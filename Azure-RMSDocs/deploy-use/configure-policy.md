---
title: Konfigurieren der Azure Information Protection-Richtlinie
description: "Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 06/12/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: 7a4922384a228457b683653e80afe4b8c8db6df2
ms.sourcegitcommit: 04eb4990e2bf0004684221592cb93df35e6acebe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2017
---
# <a name="configuring-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

## <a name="subscription-support"></a>Abonnementsupport

Die Azure Information Protection-Richtlinie unterstützt verschiedene Abonnementebenen:

- Azure Information Protection P2: Unterstützung für alle Klassifizierungs-, Bezeichnungs- und Schutzfunktionen

- Azure Information Protection P1: Unterstützung für die meisten Klassifizierungs-, Bezeichnungs- und Schutzfunktionen, jedoch keine automatische Klassifizierung oder HYOK

- Office 365, einschließlich des Azure Rights Management-Diensts: Unterstützung für Schutzfunktionen, jedoch keine Klassifizierung und Bezeichnung

Optionen, die ein Azure Information Protection P2-Abonnement erfordern, werden nun im Portal identifiziert.

Wenn Sie über eine Kombination aus Abonnements für Benutzer Ihres Mandanten verfügen, müssen Sie sicherstellen, dass die von den Benutzern heruntergeladene Azure Information Protection-Richtlinie ausschließlich für ihr Konto lizenzierte Konfigurationsoptionen enthält. Wenn Sie Optionen konfigurieren, für die nicht alle Benutzer eine Lizenz besitzen, stellen Sie mithilfe von bereichsbezogenen Richtlinien sicher, dass die Benutzer nur zur Verwendung von für sie lizenzierten Funktionen konfiguriert werden.

Weitere Informationen zu Abonnements finden Sie unter [Welches Abonnement benötige ich für Azure Information Protection, und welche Features sind enthalten?](../get-started/faqs.md#what-subscription-do-i-need-for-azure-information-protection-and-what-features-are-included)

Weitere Informationen zum Konfigurieren von bereichsbezogenen Richtlinien finden Sie unter [Konfigurieren der Richtlinie für bestimmte Benutzer mithilfe bereichsbezogener Richtlinien](configure-policy-scope.md).

## <a name="how-to-configure-the-azure-information-protection-policy"></a>Informationen zum Konfigurieren der Azure Information Protection-Richtlinie

1. Melden Sie sich in einem neuen Browserfenster als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Weitere Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 
    
    Wenn Sie zum ersten Mal eine Verbindung mit dem Dienst herstellen, wird die Seite **Schnellstart** automatisch geöffnet. Um die Richtlinie zu konfigurieren, die alle Benutzer erhalten, klicken Sie auf **Globale Richtlinie**, um das Blatt **Richtlinie: Global** zu öffnen. Dieses Blatt wird für nachfolgende Verbindungen mit dem Dienst geöffnet, sodass Sie die globale Richtlinie, die alle Benutzer erhalten, anzeigen und bearbeiten können. 
    
    Die Azure Information Protection-Richtlinie enthält die folgenden Elemente, die Sie konfigurieren können:
    
    - Bezeichnungen, mit denen Sie und Ihre Benutzer Dokumente und E-Mails klassifizieren können.
    
    - Einen Titel und eine QuickInfo für die Information Protection-Leiste, die in den Office-Anwendungen von Benutzern angezeigt wird.
    
    - Die Option zum Erzwingen einer Klassifizierung, wenn Benutzer Dokumente speichern und E-Mails senden.
    
    - Die Option zum Festlegen einer Standardbezeichnung als Ausgangspunkt für die Klassifizierung von Dokumenten und E-Mails.
    
    - Die Option, um Benutzer zur Angabe einer Begründung aufzufordern, wenn sie eine Bezeichnung mit einer niedrigeren Vertraulichkeitsstufe wählen.
    
    - Die Möglichkeit zum automatischen Bezeichnen einer E-Mail-Nachricht nach deren Anlagen.
    
    - Die Möglichkeit zum Bereitstellen eines benutzerdefinierten Hilfelinks für Benutzer.

Azure Information Protection enthält eine [Standardrichtlinie](configure-policy-default.md) mit fünf Hauptbezeichnungen. Diese Bezeichnungen können mit dem vollständigen Bereich von Daten verwendet werden, die ein Unternehmen in der Regel erstellt und speichert, von der niedrigsten Klassifizierung für persönliche Daten bis zur höchsten Klassifizierung für streng vertrauliche Daten. 

Sie können die Standardbezeichnungen unverändert verwenden, diese Bezeichnungen anpassen oder löschen und neue Bezeichnungen erstellen. Weitere Informationen zu den gewünschten Optionen und deren Konfiguration finden Sie unter den Links im nächsten Abschnitt. 

Wenn Sie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

Klicken Sie auf **Publish** (Veröffentlichen), wenn Sie alle gewünschten Änderungen vorgenommen haben. 

Beim Start einer unterstützten Office-Anwendung prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Gegebenenfalls lädt der Client diese Änderungen dann als neueste Azure Information Protection-Richtlinie herunter. Folgende zusätzliche Trigger aktualisieren die Richtlinie im Client ebenfalls:

- Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen.

- Ausführen der [PowerShell-Cmdlets](../rms-client/client-admin-guide-powershell.md) zur Bezeichnung und zum Schutz (Get-AIPFileStatus, Set-AIPFileClassification und Set-AIPFileLabel).

- Alle 24 Stunden.

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
