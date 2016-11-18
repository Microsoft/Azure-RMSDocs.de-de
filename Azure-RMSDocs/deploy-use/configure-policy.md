---
title: Konfigurieren der Richtlinie | Azure Information Protection
description: "Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 09/25/2016
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: ba0e8119-886c-4830-bd26-f98fb14b2933
ms.reviewer: eymanor
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 9d8354f2d68f211d349226970fd2f83dd0ce810b
ms.openlocfilehash: 055470948a1bf21d4ee1ee83f345f49a98c1bf31


---

# <a name="configuring-azure-information-protection-policy"></a>Konfigurieren der Azure Information Protection-Richtlinie

>*Gilt für: Azure Information Protection*

Um eine Klassifizierung, Bezeichnungen und den Schutz zu konfigurieren, müssen Sie die Azure Information Protection-Richtlinie konfigurieren. Diese Richtlinie wird dann auf Computer heruntergeladen, auf denen der [Azure Information Protection-Client](https://www.microsoft.com/en-us/download/details.aspx?id=53018) installiert ist.

So konfigurieren Sie die der Azure Information Protection-Richtlinie

1. Melden Sie sich in einem neuen Browserfenster als globaler Administrator beim [Azure-Portal](https://portal.azure.com) an.

2. Navigieren Sie zum Blatt **Azure Information Protection**: Klicken Sie im Hubmenü beispielsweise auf **Weitere Dienste**, und beginnen Sie, **Information Protection** in das Feld „Filter“ einzugeben. Wählen Sie aus den Ergebnissen **Azure Information Protection** aus. 

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

## <a name="configuring-your-organizations-policy"></a>Konfigurieren der Richtlinie Ihrer Organisation

Über die folgenden Links können Sie auf Informationen zum Konfigurieren Ihrer Azure Information Protection-Richtlinie zugreifen:

- [Die Azure Information Protection-Standardrichtlinie](configure-policy-default.md)

- [Konfigurieren der globalen Richtlinieneinstellungen für Azure Information Protection](configure-policy-settings.md)

- [Erstellen einer neuen Bezeichnung für Azure Information Protection](configure-policy-new-label.md)

- [Löschen oder Ändern der Position einer Bezeichnung für Azure Information Protection](configure-policy-delete-reorder.md)

- [Ändern oder Anpassen einer vorhandenen Bezeichnung für Azure Information Protection](configure-policy-change-label.md)

- [Konfigurieren einer Bezeichnung, um den Rights Management-Schutz anzuwenden](configure-policy-protection.md)

- [Konfigurieren einer Bezeichnung für visuelle Kennzeichnungen für Azure Information Protection](configure-policy-markings.md)

- [Konfigurieren von Bedingungen für die automatische und die empfohlene Klassifizierung für Azure Information Protection](configure-policy-classification.md)

## <a name="next-steps"></a>Nächste Schritte

Ein Beispiel für die Anpassung der Standardrichtlinie sowie das resultierende Verhalten in einer Office-Anwendung finden Sie im [Schnellstart-Tutorial für Azure Information Protection](../get-started/infoprotect-quick-start-tutorial.md).




<!--HONumber=Nov16_HO2-->


