---
title: "Rights Management-Freigabeanwendung&colon; Verlauf der Versionsveröffentlichungen | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 06/17/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: b19eadd408837ebcd77b3ae2f9520f5286fcf41f
ms.openlocfilehash: cad9d01735d8e649875bc6bba73d29573891e1d8


---

# Rights Management-Freigabeanwendung: Verlauf der Versionsveröffentlichungen

*Gilt für: Active Directory Rights Management Services, Azure Rights Management, Windows 10, Windows 7 mit SP1, Windows 8, Windows 8.1.*

Das Rights Management-Team aktualisiert die Rights Management-Freigabeanwendung regelmäßig, um Fixes und neue Funktionen zu implementieren. Verwenden Sie die folgenden Informationen, um zu sehen, welche Neuerungen oder Änderungen eine Version bietet. Die neueste Version ist zuerst aufgeführt.

Versionen vor dem 1. Januar 2015 sind nicht aufgeführt.

> [!NOTE]
> Wenn Sie Feedback oder Fragen zur RMS-Freigabeanwendung haben, senden Sie eine E-Mail an [AskIPTeam](mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question).

## Version 1.0.2191.0
**Veröffentlicht**: 16.6.2016

**Fixes**:

- Die Website zur Dokumentnachverfolgung zeigt nun für jedes nachverfolgte Dokument die korrekte Anzahl von Ansichten an.

- Die Vorlagen für alle Gebietsschemas werden jetzt als für Benutzer verfügbar angezeigt.

- Wenn Sie „Geschütztes Freigeben“ für eine PowerPoint-Datei verwenden, werden Änderungen an der lokalen Version der Datei jetzt richtig gespeichert.

- Geringe Anzahl kleinerer Fehler und Verbesserungen an Fehlermeldungen.


## Version 1.0.2004.0
**Veröffentlicht**: 11.12.2015

**Fixes**:

-   Nur der Besitzer der Datei und Personen mit der Berechtigungsebene **Mitbesitzer** können den Schutz von Dateien aufheben. Bisher konnten der Besitzer und Personen mit den Berechtigungsebenen **Mitautor** und **Mitbesitzer** den Schutz von Dateien aufheben.

-   Nativer Schutz für **TIF**-Dateien (zusätzlich zu TIFF-Dateien), um eine schreibgeschützte **PTIF**-Datei mit RMS-Schutz zu erstellen.

-   Verbesserungen bei Fehlermeldungen (Genauigkeit und Klarheit).

-   Leistungsverbesserungen beim Verschlüsseln und Entschlüsseln von Inhalt.

**Neue Features**:

-   Eine Installation ohne Administratorrechte wird unterstützt, sodass Standardbenutzer die RMS-Freigabeanwendung installieren können.

    Für Standardbenutzer, die Office 2010 verwenden, bestehen einige Einschränkungen. Weitere Informationen finden Sie im Abschnitt [Wenn Sie kein lokaler Administrator sind und Office 2010 verwenden](install-sharing-app.md#if-you-are-not-a-local-administrator-and-use-office-2010) der Benutzeranleitung unter [Herunterladen und Installieren der Rights Management-Freigabeanwendung](install-sharing-app.md).

## Version 1.0.1908.0
**Veröffentlicht**: 16.09.2015

**Fixes**:

-   Unterstützung für mehrstufige Authentifizierung (MFA) für Azure RMS, wodurch auch die Abhängigkeit vom Microsoft Anmelde-Assistenten für Anwendungen, die eine moderne Authentifizierung verwenden, entfernt wird.

    Weitere Informationen finden Sie im Abschnitt [Multi-Factor Authentication (MFA) und Azure RMS](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms) unter [Anforderungen für Azure Rights Management](../get-started/requirements-azure-rms.md).

## Version 1.0.1784.0
**Veröffentlicht**: 30.07.2015

**Fixes**:

-   Das Standardaktualisierungsintervall für Vorlagen für Benutzerrechterichtlinien wurde von 7 Tagen auf 1 Tag reduziert.

-   Kleine Anzahl von Regressionen und kleinere Fehler.

## Version 1.0.1770.0
**Veröffentlicht**: 25.04.2015

**Fixes**:

-   Nun können nur Besitzer und Mitbesitzer den jeweiligen Schutz entfernen. Mitautoren können den Schutz nicht aufheben.

-   Dateien, die sich auf einer Netzwerkfreigabe befinden, können jetzt geschützt werden.

**Neue Features**:

-   Unterstützung für Dokumentnachverfolgung und -widerruf. Weitere Informationen finden Sie unter [Nachverfolgen und Widerrufen Ihrer Dokumente bei Verwendung der RMS-Freigabeanwendung](sharing-app-track-revoke.md).

-   Vorlagenunterstützung, wenn Sie **Geschützt freigeben**auswählen:

    -   Sie können nun Vorlagen auswählen.

    -   Statt des Schiebereglers wird ein Listenfeld angezeigt, das Vorlagen und benutzerdefinierte Berechtigungen beinhaltet.

    -   Es werden keine Optionen für **Nutzung auf allen Geräten zulassen** und **Nutzungsbeschränkungen erzwingen**mehr angezeigt. Stattdessen wird je nach Dateityp automatisch **Generischer Schutz** ausgewählt.

    Weitere Informationen finden Sie unter [Dialogfeldoptionen für die Rights Management-Freigabeanwendung](sharing-app-dialog-box.md).

## Version 1.0.1667.0
**Veröffentlicht**: 19.01.2015

**Fixes**:

-   Unterstützung für chinesische Schriftzeichen im PPDF-Viewer der RMS-Freigabeanwendung.

-   Verbesserte Fehlerbehandlung und -benachrichtigungen.

-   Fix für ein Problem mit der automatischen Updatebenachrichtigung, wenn eine neuere Version der Anwendung zum Download zur Verfügung steht.

**Neue Features**:

-   **Unterstützung für mehrere E-Mail-Domänen innerhalb der Organisation**: Wenn Sie AD RMS verwenden und Benutzer in Ihrer Organisation über mehrere E-Mail-Domänen verfügen, können die Benutzer durch dieses Update Inhalte verwenden, die von Benutzern in Ihrer Organisation in anderen Domänen geschützt wurden. Weitere Informationen finden Sie im Abschnitt [Nur AD RMS: Unterstützung für mehrere E-Mail-Domänen innerhalb Ihrer Organisation](sharing-app-admin-guide.md#ad-rms-only-support-for-multiple-email-domains-within-your-organization) im [Rights Management-Freigabeanwendung – Administratorhandbuch](sharing-app-admin-guide.md).




<!--HONumber=Jul16_HO2-->


