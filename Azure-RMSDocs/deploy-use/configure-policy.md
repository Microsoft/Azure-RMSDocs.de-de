---
title: Konfigurieren der Azure Information Protection-Richtlinie
description: "Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 05/05/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
ms.openlocfilehash: f412d36e8c58d874360c55c5c90416c2629ed69e
ms.sourcegitcommit: e3974cc1490581414084669632cad54b12b05d5a
ms.translationtype: HT
ms.contentlocale: de-DE
---
# <a name="configuring-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

So konfigurieren Sie die der Azure Information Protection-Richtlinie

1. Melden Sie sich in einem neuen Browserfenster als Sicherheitsadministrator oder globaler Administrator beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Weitere Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 

    Beim Laden des Blatts **Azure Information Protection** wird automatisch das Blatt **Richtlinie: Global** geladen, damit Sie die globale Richtlinie anzeigen und bearbeiten können, die für alle Benutzer konfiguriert wird. Sie können optional jedoch auch bereichsbezogene Richtlinien hinzufügen und bearbeiten. Die Azure Information Protection-Richtlinien enthalten die folgenden Elemente, die Sie konfigurieren können:

    - Bezeichnungen, mit denen Sie und Ihre Benutzer Dokumente und E-Mails klassifizieren können.

    - Einen Titel und eine QuickInfo für die Information Protection-Leiste, die in den Office-Anwendungen von Benutzern angezeigt wird.

    - Die Option zum Erzwingen einer Klassifizierung, wenn Benutzer Dokumente speichern und E-Mails senden.

    - Die Option zum Festlegen einer Standardbezeichnung als Ausgangspunkt für die Klassifizierung von Dokumenten und E-Mails.

    - Die Option, um Benutzer zur Angabe einer Begründung aufzufordern, wenn sie eine Bezeichnung mit einer niedrigeren Vertraulichkeitsstufe wählen.

    - Die Möglichkeit zum automatischen Bezeichnen einer E-Mail-Nachricht nach deren Anlagen.

    - Die Möglichkeit zum Bereitstellen eines benutzerdefinierten Hilfelinks für Benutzer.

Azure Information Protection enthält eine [Standardrichtlinie](configure-policy-default.md) mit fünf Hauptbezeichnungen. Diese Bezeichnungen können mit dem vollständigen Bereich von Daten verwendet werden, die ein Unternehmen in der Regel erstellt und speichert, von der niedrigsten Klassifizierung für persönliche Daten bis zur höchsten Klassifizierung für streng vertrauliche Daten. Sie können die Standardbezeichnungen unverändert verwenden, diese Bezeichnungen anpassen oder löschen und neue Bezeichnungen erstellen.

Wenn Sie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

Klicken Sie auf **Publish** (Veröffentlichen), wenn Sie alle gewünschten Änderungen vorgenommen haben. 

Beim Start einer unterstützten Office-Anwendung prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Gegebenenfalls lädt der Client diese Änderungen dann als neueste Azure Information Protection-Richtlinie herunter. Folgende zusätzliche Trigger aktualisieren die Richtlinie im Client ebenfalls:

- Klicken mit der rechten Maustaste, um eine Datei oder einen Ordner zu klassifizieren und zu schützen.

- Ausführen der PowerShell-Cmdlets für Bezeichnung und Schutz (Get-AIPFileStatus und Set-AIPFileLabel).

- Alle 24 Stunden.

>[!NOTE]
>Wenn der Client die Richtlinie herunterlädt, sollten Sie mit einigen Minuten Wartezeit rechnen, bevor sie vollständig einsatzbereit ist. Die tatsächliche Zeit hängt von Faktoren wie der Größe und Komplexität der Richtlinienkonfiguration und der Netzwerkkonnektivität ab. Wenn die resultierenden Bezeichnungen nicht mit Ihren letzten Änderungen übereinstimmen, sollten Sie bis zu 15 Minuten warten und es dann erneut versuchen.

## <a name="configuring-your-organizations-policy"></a>Konfigurieren der Richtlinie Ihrer Organisation

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

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
