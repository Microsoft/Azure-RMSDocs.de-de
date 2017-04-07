---
title: 'Gewusst wie: Verwenden der Dokumentenverfolgung | Azure RMS'
description: "Die Funktion für die Dokumentenverfolgung erfordert einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung bei dem Dienst."
keywords: 
author: bruceperlerms
ms.author: bruceper
manager: mbaldwin
ms.date: 02/23/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.openlocfilehash: bae83de7d91d30ce39d2edb1311fac55ca2dafad
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="how-to-use-document-tracking"></a>Vorgehensweise: Verwenden der Dokumentenverfolgung

Zum Verwenden der Funktion für die Dokumentenverfolgung sind einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung bei dem Dienst erforderlich.

## <a name="managing-document-tracking-metadata"></a>Verwalten der Metadaten für die Dokumentenverfolgung

Die Betriebssysteme, die die Dokumentenverfolgung unterstützen, weisen ähnliche Implementierungen auf. Dazu gehören eine Reihe von Eigenschaften (die Metadaten), ein neuer Parameter, der den Erstellungsmethoden für Benutzerrichtlinien hinzugefügt wurde, sowie eine Methode zum Registrieren der Richtlinie, die mit dem Dokumentenverfolgungsdienst verfolgt werden soll.

Im Prinzip sind nur für die Dokumentenverfolgung nur das **contentName**- und das **notificationType**-Objekt erforderlich.

Führen Sie zum Einrichten der Dokumentenverfolgung für einen bestimmten Inhalt folgende Schritte aus:

-   Erstellen Sie ein **Lizenzmetadaten**-Objekt, und legen Sie dann den **Inhaltsnamen** und den **Benachrichtigungstyp** fest. Dies sind die einzigen erforderlichen Eigenschaften.
   - Android – [LicenseMetadata](https://msdn.microsoft.com/library/mt573675.aspx)
   -  iOS – [MSLicenseMetadata](https://msdn.microsoft.com/library/mt573683.aspx)

Auswählen des Richtlinientyps; Vorlage oder Ad-hoc:
- Erstellen Sie für die vorlagenbasierte Dokumentenverfolgung ein **UserPolicy**-Objekts, das die Lizenzmetadaten als Parameter übergibt.
  - Android – [UserPolicy.create](https://msdn.microsoft.com/library/dn790887.aspx)
  - iOS – [MSUserPolicy.userPolicyWithTemplateDescriptor](https://msdn.microsoft.com/library/dn790808.aspx)

- Legen Sie für die Ad-hoc-basierte Dokumentenverfolgung die **LicenseMetadata**-Eigenschaft auf das **PolicyDescriptor**-Objekt fest.
  - Android – [PolicyDescriptor.setLicenseMetadata](https://msdn.microsoft.com/library/mt573698.aspx)
  - iOS – [MSPolicyDescriptor.licenseMetadata](https://msdn.microsoft.com/library/mt573693.aspx)

    **Hinweis**  Das LicenseMetadata-Objekt ist nur während des Einrichtens der Dokumentenverfolgung für die angegebene Benutzerrichtlinie direkt zugänglich. Sobald das Benutzerrichtlinien-Objekt erstellt wurde, kann nicht mehr auf die zugehörigen Lizenzmetadaten zugegriffen werden, d.h., die Werte der Lizenzmetadaten lassen sich nicht mehr ändern.

     

-   Rufen Sie zuletzt die Plattformregistrierungsmethode für die Dokumentnachverfolgung auf.
  - Android – [UserPolicy.registerForDocTracking asynchronous](https://msdn.microsoft.com/library/mt573699.aspx) oder [UserPolicy.registerForDocTracking synchronous](https://msdn.microsoft.com/library/mt631387.aspx)
  - iOS – [MSUserPolicy.registerForDocTracking](https://msdn.microsoft.com/library/mt573694.aspx)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]