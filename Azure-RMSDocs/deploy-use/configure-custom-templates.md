---
# required metadata

title: Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 05/23/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 1775d8d0-9a59-42c8-914f-ce285b71ac1c

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*

[Nachdem Sie Azure Rights Management (Azure RMS) aktiviert haben](activate-service.md), sind Benutzer automatisch in der Lage, zwei Standardvorlagen zu verwenden, die ihnen die Anwendung von Richtlinien auf vertrauliche Dateien erleichtern, mit denen der Zugriff auf autorisierte Benutzer in Ihrer Organisation beschränkt wird. Diese zwei Vorlagen enthalten die folgenden Rechterichtlinieneinschränkungen:

-   Schreibgeschützte Anzeige geschützter Inhalte

    -   Anzeigename: **&lt;Organisationsname&gt; – Nur vertrauliche Ansicht**

    -   Bestimmte Berechtigung: Inhalt anzeigen

-   Lese- oder Änderungsberechtigungen für geschützten Inhalt

    -   Anzeigename: **&lt;Organisationsname&gt; – Vertraulich**

    -   Bestimmte Berechtigungen: Inhalt anzeigen, Datei speichern, Inhalt bearbeiten, Zugewiesene Rechte anzeigen, Makros zulassen, Weiterleiten, Antworten, Allen antworten

Darüber hinaus ermöglicht es die [RMS-Freigabeanwendung](../rms-client/sharing-app-windows.md) Benutzern, eine eigene Gruppe mit Berechtigungen zu definieren. Außerdem können Benutzer für den Outlook-Client sowie für Outlook Web Access die Option **Nicht weiterleiten** für E-Mails auswählen.

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

-   [Gewusst wie: Aktualisieren von Vorlagen für Benutzer](refresh-templates.md)

-   [Verwenden von PowerShell zum Verwalten von Vorlagen](configure-templates-with-powershell.md)




<!--HONumber=May16_HO5-->


