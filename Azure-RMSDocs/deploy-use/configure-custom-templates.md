---
title: "Konfigurieren benutzerdefinierter Vorlagen für Azure RMS – AIP"
description: "Informationen und Anweisungen für Administratoren zum Konfigurieren und Verwalten von Vorlagen für Nutzungsrechte. Mit Vorlagen können Benutzer und andere Administratoren ganz einfach Richtlinien auf sensible Dateien anwenden, die den Zugriff auf autorisierte Benutzer beschränken."
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 02/08/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 27ffbc6eb9e88840f1b33c59b76bdaa5d028cc36
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="configuring-custom-templates-for-the-azure-rights-management-service"></a>Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst

>*Gilt für: Azure Information Protection, Office 365*

Nachdem Sie den Azure Rights Management-Dienst [aktiviert](activate-service.md) haben, sind Benutzer automatisch in der Lage, zwei Standardvorlagen zu verwenden, die ihnen die Anwendung von Rechteverwaltungsrichtlinien auf vertrauliche Dateien erleichtern, mit denen der Zugriff auf autorisierte Benutzer in Ihrer Organisation beschränkt wird. Diese zwei Vorlagen enthalten die folgenden Rechterichtlinieneinschränkungen:

-   Schreibgeschützte Anzeige geschützter Inhalte

    -   Anzeigename: **&lt;Organisationsname&gt; – Nur vertrauliche Ansicht**

    -   Bestimmte Berechtigung: Inhalt anzeigen

-   Lese- oder Änderungsberechtigungen für geschützten Inhalt

    -   Anzeigename: **&lt;Organisationsname&gt; – Vertraulich**

    -   Bestimmte Berechtigungen: Inhalt anzeigen, Datei speichern, Inhalt bearbeiten, Zugewiesene Rechte anzeigen, Makros zulassen, Weiterleiten, Antworten, Allen antworten

Darüber hinaus ermöglicht es der [Azure Information Protection-Client](../rms-client/aip-client.md) den Benutzern, eine eigene Gruppe mit Berechtigungen zu definieren. Außerdem können Benutzer für den Outlook-Client sowie für Outlook Web Access die Option [Nicht weiterleiten](../deploy-use/configure-usage-rights.md#do-not-forward-option-for-emails) auswählen.

Für viele Organisationen sind die Standardvorlagen möglicherweise ausreichend. Wenn Sie aber eigene, benutzerdefinierte Vorlagen für Rechterichtlinien erstellen möchten, können Sie dies tun. Gründe zum Erstellen einer benutzerdefinierten Vorlage umfassen unter anderem die folgenden:

-   Sie möchten, dass eine Vorlage einer Untergruppe von Benutzern in der Organisation Rechte gewährt statt allen Benutzern.

-   Sie möchten, dass eine Vorlage (Abteilungsvorlage) nicht von allen Benutzern, sondern nur von einer Teilmenge der Benutzer aus Anwendungen angezeigt und ausgewählt werden kann.

-   Sie möchten ein benutzerdefiniertes Recht für eine Vorlage definieren, beispielsweise Anzeigen und Bearbeiten, aber nicht Kopieren und Drucken.

-   Sie möchten zusätzliche Optionen in einer Vorlage konfigurieren, die ein Ablaufdatum umfassen und ob auf den Inhalt ohne Internetverbindung zugegriffen werden kann.

Damit Benutzer eine benutzerdefinierte Vorlage auswählen können, die solche Einstellungen enthält, müssen Sie zuerst eine benutzerdefinierte Vorlage erstellen, konfigurieren und dann veröffentlichen. Sie benötigen wahrscheinlich nur einige Vorlagen, aber in Azure ist es möglich, maximal 500 gespeicherte benutzerdefinierte Vorlagen zu verwenden. 

In den folgenden Abschnitten finden Sie Informationen, wie Sie benutzerdefinierte Vorlagen konfigurieren und verwenden:

-   [Erstellen, Konfigurieren und Veröffentlichen einer benutzerdefinierten Vorlage](create-template.md)

-   [Kopieren einer Vorlage](copy-template.md)

-   [Entfernen (Archivieren) von Vorlagen](remove-template.md)

-   [Aktualisieren von Vorlagen für Benutzer](refresh-templates.md)

-   [PowerShell-Referenz für benutzerdefinierte Vorlagen](configure-templates-with-powershell.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

