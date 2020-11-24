---
title: 'Gewusst wie: Verwenden der Dokumentenverfolgung | Azure RMS'
description: Die Funktion für die Dokumentenverfolgung erfordert einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung bei dem Dienst.
keywords: ''
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 02/23/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 70E10936-7953-49B0-B0DC-A5E7C4772E60
audience: developer
ms.reviewer: shubhamp
ms.suite: ems
ms.custom: dev
ms.openlocfilehash: dfcb4c616be2f5891b242a918a06abf2708c12cc
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95568198"
---
# <a name="how-to-use-document-tracking"></a>Vorgehensweise: Verwenden der Dokumentenverfolgung

[!INCLUDE [deprecation notice](../includes/deprecation-warning.md)]

Zum Verwenden der Funktion für die Dokumentenverfolgung sind einige grundlegende Kenntnisse bezüglich der Verwaltung der zugehörigen Metadaten und der Registrierung bei dem Dienst erforderlich.

## <a name="managing-document-tracking-metadata"></a>Verwalten der Metadaten für die Dokumentenverfolgung

Die Betriebssysteme, die die Dokumentenverfolgung unterstützen, weisen ähnliche Implementierungen auf. Dazu gehören eine Reihe von Eigenschaften (die Metadaten), ein neuer Parameter, der den Erstellungsmethoden für Benutzerrichtlinien hinzugefügt wurde, sowie eine Methode zum Registrieren der Richtlinie, die mit dem Dokumentenverfolgungsdienst verfolgt werden soll.

Im Prinzip sind nur für die Dokumentenverfolgung nur das **contentName**- und das **notificationType**-Objekt erforderlich.

Führen Sie zum Einrichten der Dokumentenverfolgung für einen bestimmten Inhalt folgende Schritte aus:

- Erstellen Sie ein **Lizenzmetadaten**-Objekt, und legen Sie dann den **Inhaltsnamen** und den **Benachrichtigungstyp** fest. Dies sind die einzigen erforderlichen Eigenschaften.
  - Android – [LicenseMetadata](/previous-versions/windows/desktop/msipcthin2/licensemetadata-interface-java)
  -  iOS – [MSLicenseMetadata](/previous-versions/windows/desktop/msipcthin2/mslicensemetadata-class-objc)

Auswählen des Richtlinientyps; Vorlage oder Ad-hoc:
- Erstellen Sie für die vorlagenbasierte Dokumentenverfolgung ein **UserPolicy**-Objekts, das die Lizenzmetadaten als Parameter übergibt.
  - Android – [UserPolicy.create](/previous-versions/windows/desktop/msipcthin2/userpolicy-class-java)
  - iOS – [MSUserPolicy.userPolicyWithTemplateDescriptor](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-templatedescriptor-property-objc)

- Legen Sie für die Ad-hoc-basierte Dokumentenverfolgung die **LicenseMetadata**-Eigenschaft auf das **PolicyDescriptor**-Objekt fest.
  - Android – [PolicyDescriptor.setLicenseMetadata](/previous-versions/windows/desktop/msipcthin2/policydescriptor-setlicensemetadata-java)
  - iOS – [MSPolicyDescriptor.licenseMetadata](/previous-versions/windows/desktop/msipcthin2/mspolicydescriptor-licensemetadata-property-objc)

    **Hinweis**    Der Zugriff auf das License Metadata-Objekt ist nur während der Einrichtung der Dokument Nachverfolgung für die jeweilige Benutzer Richtlinie direkt möglich. Sobald das Benutzerrichtlinien-Objekt erstellt wurde, kann nicht mehr auf die zugehörigen Lizenzmetadaten zugegriffen werden, d.h., die Werte der Lizenzmetadaten lassen sich nicht mehr ändern.

     

- Rufen Sie zuletzt die Plattformregistrierungsmethode für die Dokumentnachverfolgung auf.
  - Android – [UserPolicy.registerForDocTracking asynchronous](/previous-versions/windows/desktop/msipcthin2/userpolicy-registerfordoctracking-boolean--sting--authenticationcallback--creationcallback--java) oder [UserPolicy.registerForDocTracking synchronous](/previous-versions/windows/desktop/msipcthin2/userpolicy-registerfordoctracking-synchronous-method-java)
  - iOS – [MSUserPolicy.registerForDocTracking](/previous-versions/windows/desktop/msipcthin2/msuserpolicy-registerfordoctracking-userid-authenticationcallback-completionblock-method-objc)