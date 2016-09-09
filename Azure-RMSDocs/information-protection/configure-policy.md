---
title: Konfigurieren der Azure Information Protection-Richtlinie | Azure RMS
description: "Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
manager: mbaldwin
ms.date: 08/25/2016
ms.topic: article
ms.prod: 
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: da0145444a7d0abb6407ed2ccbb581d4dcdd10d6
ms.openlocfilehash: e5b8054b3b5cb38adf2f5ae1d2f4f399d98f6e23


---

# Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection (Preview)*

**[ Diese Informationen sind vorläufig und können geändert werden. ]**

Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

So konfigurieren Sie die Azure Information Protection-Richtlinie während der Vorschauphase von Azure Information Protection:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Durchsuchen**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 

    Das Blatt **Azure Information Protection** wird geöffnet, auf dem Sie die Azure Information Protection-Richtlinie konfigurieren können. Diese Richtlinie umfasst folgende Elemente:

    - Einen Titel und eine QuickInfo für die Information Protection-Leiste, die in den Office-Anwendungen von Benutzern angezeigt wird.

    - Bezeichnungen, mit denen Sie und Ihre Benutzer Dokumente und E-Mails klassifizieren können.

    - Die Option zum Erzwingen einer Klassifizierung, wenn Benutzer Dokumente speichern und E-Mails senden.

    - Die Option zum Festlegen einer Standardbezeichnung als Ausgangspunkt für die Klassifizierung von Dokumenten und E-Mails.

    - Die Option, um Benutzer zur Angabe einer Begründung aufzufordern, wenn sie eine Bezeichnung mit einer niedrigeren Vertraulichkeitsstufe wählen.


Azure Information Protection umfasst eine [Standardrichtlinie](configure-policy-default.md), die die Bezeichnungen **Personal** (Persönlich), **Public** (Öffentlich), **Internal** (Intern), **Confidential** (Vertraulich) und **Secret** (Geheim) beinhaltet. Sie können die Standardbezeichnungen unverändert verwenden, diese Bezeichnungen anpassen oder löschen und neue Bezeichnungen erstellen.

Wenn Sie auf einem Azure Information Protection-Blatt Änderungen vorgenommen haben, klicken Sie auf **Save** (Speichern), um die Änderungen zu speichern, oder auf **Discard** (Verwerfen), um die zuletzt gespeicherten Einstellungen wiederherzustellen. 

Klicken Sie auf **Publish** (Veröffentlichen), wenn Sie alle gewünschten Änderungen vorgenommen haben. 

Beim Start einer unterstützten Office-Anwendung prüft der Azure Information Protection-Client, ob Änderungen vorgenommen wurden. Gegebenenfalls lädt er diese Änderungen dann als Azure Information Protection-Richtlinie herunter.

## Konfigurieren der Richtlinie Ihrer Organisation

Über die folgenden Links können Sie auf Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zugreifen:

- [Die Information Protection-Standardrichtlinie](configure-policy-default.md)

- [Konfigurieren der globalen Richtlinieneinstellungen](configure-policy-settings.md)

- [Erstellen einer neuen Bezeichnung](configure-policy-new-label.md)

- [Löschen oder Ändern der Position einer Bezeichnung](configure-policy-delete-reorder.md)

- [Ändern oder Anpassen einer vorhandenen Bezeichnung](configure-policy-change-label.md)

- [Konfigurieren einer Bezeichnung, um den Schutz anzuwenden](configure-policy-protection.md)

- [Konfigurieren einer Bezeichnung, um visuelle Kennzeichnungen anzuwenden](configure-policy-markings.md)

- [Konfigurieren von Bedingungen für die automatische und empfohlene Klassifizierung](configure-policy-classification.md)

## Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](infoprotect-quick-start-tutorial.md).




<!--HONumber=Aug16_HO4-->


