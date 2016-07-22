---
title: "Roadmap für die Bereitstellung von Azure Rights Management | Azure RMS"
description: 
keywords: 
author: cabailey
manager: mbaldwin
ms.date: 05/09/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 086600c2-c5d8-47ec-a4c0-c782e1797486
ms.reviewer: esaggese
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 7f8a4d53665dd79a6d0e02d340b0e7a09d995e00
ms.openlocfilehash: 96ee0aa3151ede8b8a263f3ce6c3d2e5b8ec9c81


---

# Roadmap für die Bereitstellung von Azure Rights Management

*Gilt für: Azure Rights Management, Office 365*

Führen Sie die folgenden Schritte aus, um Azure Rights Management (Azure RMS) für Ihre Organisation vorzubereiten, zu implementieren und zu verwalten.

Falls Sie Azure RMS einmal schnell selbst ausprobieren möchten, anstatt die Anwendung in eine Produktionsumgebung einzuführen, helfen Ihnen die Informationen unter [Schnellstart-Lernprogramm für Azure Rights Management](../get-started/quick-start-tutorial.md) weiter.

Eine Übersicht über bestimmte Szenarios und die dazugehörigen Konfigurationsschritte sowie die Endbenutzerdokumentation finden Sie unter [Handbuch für die Schnellbereitstellung von Azure Rights Management](../get-started/rapid-deployment-guide.md).

> [!IMPORTANT]
> Lesen Sie sich vor dem Ausführen der folgenden Schritte den Artikel [Anforderungen für Azure Rights Management](../get-started/requirements-azure-rms.md) durch.

## Schritt 1: Sicherstellen, dass Sie über ein Abonnement verfügen, das Azure Rights Management umfasst
Es gibt mehrere Abonnementtypen, die [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] enthalten. Weitere Informationen finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md). Stellen Sie außerdem sicher, dass Ihr Abonnement die Funktionen umfasst, die Sie in Ihrer Organisation verwenden möchten, indem Sie die Tabelle unter [Vergleich der Rights Management Services (RMS)-Angebote](https://technet.microsoft.com/dn858608) heranziehen. Sie müssen jedem Benutzer Ihres Unternehmens eine Lizenz dieses Abonnements zuweisen, um Dateien und E-Mails mit Azure RMS zu schützen.

## Schritt 2: Vorbereiten Ihres Mandanten für die Verwendung von Rights Management
Bevor Sie mit der Verwendung von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] beginnen, führen Sie folgende Vorbereitungsschritte aus:

1.  Stellen Sie sicher, dass Ihr Azure- oder Office 365-Mandant die Benutzerkonten und -gruppen enthält, die zum Authentifizieren von Benutzern in Ihrer Organisation durch Azure RMS verwendet werden. Falls erforderlich, erstellen Sie diese Konten und Gruppen, oder synchronisieren Sie diese über Ihr lokales Verzeichnis. Weitere Informationen finden Sie unter [Vorbereiten für Azure Rights Management](prepare.md).

2.  Entscheiden Sie, ob Sie möchten, dass Microsoft Ihren Mandantenschlüssel verwaltet (Standard), oder ob Sie Ihren Mandantenschlüssel selber generieren und verwalten möchten (bekannt als BYOK, Bring Your Own Key). Beachten Sie, dass Sie derzeit BYOK nicht verwenden können, wenn Sie Exchange Online nutzen. Weitere Informationen finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](plan-implement-tenant-key.md).

3.  Installieren Sie das Windows PowerShell-Modul für [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] auf mindestens einem Computer, der Zugang zum Internet hat. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Installieren der Windows PowerShell für Azure Rights Management](../deploy-use/install-powershell.md).

4.  Wenn Sie derzeit lokale Rights Management Services verwenden: Führen Sie eine Migration durch, um die Schlüssel, Vorlagen und URLs in die Cloud zu verschieben. Weitere Informationen finden Sie unter [Migration von AD RMS zu Azure Rights Management](migrate-from-ad-rms-to-azure-rms.md).

5.  Aktivieren Sie Rights Management, damit Sie mit der Verwendung des Diensts beginnen können. Wenn eine Bereitstellung in Phasen erforderlich ist, konfigurieren Sie benutzerbezogene Steuerungsrichtlinien für die Einbindung (Onboarding), um die Nutzung auf bestimmte Benutzer zu beschränken. Weitere Informationen finden Sie unter [Aktivieren von Azure Rights Management](../deploy-use/activate-service.md).

Erwägen Sie optional die Konfigurierung folgender Funktionen:

-   Benutzerdefinierte Vorlagen, wenn die Standardvorlagen für Rechterichtlinien für Ihre Organisation nicht ausreichend sind. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).

-   Nutzungsprotokollierung, sodass Sie überwachen können, wie Ihre Organisation Rights Management verwendet. Sie können diesen Schritt jetzt oder später durchführen. Weitere Informationen finden Sie unter [Protokollieren und Analysieren der Nutzung von Azure Rights Management](../deploy-use/log-analyze-usage.md).

## Schritt 3: Konfigurieren Ihrer Anwendungen und Dienste für Rights Management
Die Konfiguration Ihrer Anwendungen und Dienste kann das Installieren der Rights Management-Freigabeanwendung sowie die Aktivierung von Unterstützung für IRM-Features in SharePoint Online oder Exchange Online umfassen. Weitere Informationen finden Sie unter [Konfigurieren von Anwendungen für Azure Rights Management](../deploy-use/configure-applications.md).

Wenn Sie über vorhandene IT-Dienste verfügen, mit denen von Azure RMS zu schützende Dateien überprüft werden müssen (z.B. DLP-Lösungen, Gateways zur Inhaltsverschlüsselung und Antischadsoftware), konfigurieren Sie die Dienstkonten mit Administratorberechtigungen für Azure RMS. Weitere Informationen finden Sie unter [Konfigurieren von Administratoren für Azure Rights Management und Discovery Services oder die Datenwiederherstellung](../deploy-use/configure-super-users.md).

Installieren Sie das RMS Protection Tool, das das gleichnamige PowerShell-Modul verwendet, um alle Dateitypen gleichzeitig schützen zu können oder den Schutz gleichzeitig für alle Dateitypen aufzuheben. Weitere Informationen finden Sie im Thema zu [RMS Protection-Cmdlets](https://msdn.microsoft.com/library/mt433195.aspx).

Wenn Sie über lokale Dienste verfügen, die Sie mit Azure Rights Management verwenden möchten, installieren und konfigurieren Sie den Rights Management-Verbindungsdienst. Weitere Informationen finden Sie unter [Bereitstellen des Azure Rights Management-Verbindungsdiensts](../deploy-use/deploy-rms-connector.md).

## Schritt 4: Veröffentlichen und Nutzen rechtegeschützter Inhalte
Sie können jetzt geschützte Inhalte veröffentlichen und nutzen sowie die Nutzung von Rights Management durch Ihre Organisation protokollieren. Weitere Informationen finden Sie unter [Unterstützung von Benutzern beim Schützen von Dateien unter Verwendung von Azure Rights Management](../deploy-use/help-users.md) und [Protokollieren und Analysieren der Nutzung von Azure Rights Management](../deploy-use/log-analyze-usage.md).

Wenn Sie sich für den automatischen Schutz von Dateien mithilfe der Dateiklassifizierungsinfrastruktur auf einem Windows-basierten Dateiserver interessieren, lesen Sie den Artikel [RMS-Schutz mit Windows Server-Dateiklassifizierungsinfrastruktur (File Classification Infrastructure, FCI)](../rms-client/configure-fci.md).

## Schritt 5: Bedarfsweises Verwalten von Rights Management für Ihr Mandantenkonto
Wenn Sie mit der Verwendung von [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)] beginnen, kann das [!INCLUDE[aad_rightsmanagement_2](../includes/aad_rightsmanagement_2_md.md)]-Modul für Windows PowerShell nützlich sein, um administrative Änderungen skriptgestützt oder automatisiert durchzuführen. Weitere Informationen finden Sie unter [Verwaltung von Azure Rights Management mithilfe von Windows PowerShell](../deploy-use/administer-powershell.md).





<!--HONumber=Jul16_HO3-->


