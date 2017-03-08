---
title: Azure Information Protection-Entwicklerhandbuch | Microsoft-Dokumentation
description: "Entwickler können mithilfe von Azure Information Protection Dateien aller Typen schützen und verwalten."
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.date: 02/09/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
translationtype: Human Translation
ms.sourcegitcommit: 9a8b37f8e4e6d3a22c5ae4b43ffb82bfd0482037
ms.openlocfilehash: ee257e733177077caaf3cf3b579a1b3718479121
ms.lasthandoff: 02/10/2017

---
# <a name="azure-information-protection-developers-guide"></a>Azure Information Protection-Entwicklerhandbuch

Dieses Handbuch ist auf Tools zum Erweitern und Integrieren des Rechteverwaltungsdiensts von Azure Information Protection ausgerichtet. Mithilfe dieses Handbuchs soll es Entwicklern, die das Rechteverwaltungssystem nutzen möchten, ermöglicht werden, verschiedene Arten von Anwendungen für eine Reihe unterstützter Plattformen zu erstellen.

>Das aktuelle Azure Information Protection-SDK verfügt über die Komponente zur Rechteverwaltung und die Klassifizierung und Bezeichnung befinden sich in der Entwicklung.

## <a name="service-applications"></a>Dienstanwendungen

Dienstanwendungen bieten Funktionen zum Schutz von Informationen beim Exportieren aus einem Enterprise Content Management-System, aus einer Geschäftsanwendung oder einer cloudbasierten Geschäftslösung. DLP (Data Loss Prevention) und CAS (Cloud Application Security) sind Beispiele für Dienstanwendungen. Unser SDK zum Entwickeln von Dienstanwendungen steht über zwei Programmiermodelle zur Verfügung.

- [C++](https://www.microsoft.com/en-us/download/details.aspx?id=38397)
- [C#-verwaltete API](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>Beispiele für Dienstanwendungen

- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist eine RMS-fähige DLP-Anwendung (Data Leak Protection), die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige DLP-Anwendung mithilfe der RMS-Datei-API zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollte.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Beispiel für die Verwendung des RMS SDK in Azure-Anwendungen, um Daten im Azure Blob-Speicher zu schützen.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Beispiel, das veranschaulicht, wie eine Windows-Anwendung erstellt wird, die Verzeichnisse im Dateisystem überwacht, und RMS-Schutzrichtlinien bei jeder Änderung anwendet, z. B. beim Hinzufügen oder Ändern einer Datei.
- [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir) ist ein Beispiel für eine einfache Konsolenanwendung, die ein Verzeichnis als Eingabe verwendet und ohne Rekursion ausschließlich alle Dateien in diesem Verzeichnis schützt.

## <a name="powershell-guides"></a>PowerShell-Anleitungen

Diese Skripts, die im Allgemeinen von Administratoren für Azure Rights Management verwendet werden, sind beim Entwickeln und Testen Ihrer Dienstanwendungen hilfreich.

- Mit [Azure Rights Management-Cmdlets](https://msdn.microsoft.com/library/azure/dn629398.aspx) können Sie Azure RMS über die Befehlszeile verwalten. Auf diese Weise wird einerseits Automatisierung ermöglicht, andererseits werden aber auch zuverlässige und wiederholte Prozesse unterstützt, um den Verwaltungsaufwand zu verringern. Außerdem erfordern einige erweiterte Azure RMS-Konfigurationen und -Vorgänge Azure PowerShell.
- [RMS Protection-Cmdlets](https://msdn.microsoft.com/library/azure/mt433195.aspx) können mit dem Azure Rights Management-Datenschutz (Azure RMS) in Azure Information Protection oder mit Active Directory Rights Management Services (AD RMS) verwendet werden und andere PowerShell-Module für diese Rights Management-Bereitstellungen ergänzen. Mit diesen RMS Protection-Cmdlets können Sie Dateien beliebiger Typen in einem Massenvorgang schützen bzw. deren Schutz aufheben.

## <a name="user-applications"></a>Benutzeranwendungen

Benutzeranwendungen können mit dem RMS SDK 2.1 oder dem RMS SDK 4.2 erstellt werden.
Die Version 4.2 basiert auf dem REST-Client mit betriebssystemspezifischen APIs für eine Reihe beliebter Betriebssysteme wie iOS/OSX, Android, Linux und Windows. Version 2.1 dient zum Erstellen systemeigener Windows-basierter Anwendungen.

### <a name="user-application-development-guides"></a>Anleitungen zur Entwicklung von Benutzeranwendungen

- [Entwickeln Ihrer Anwendung](developing-your-application.md)
- [Testen der Anwendung](how-to-set-up-your-test-environment.md)
- [Bereitstellen der Anwendung](deploying-your-application.md)

### <a name="user-application-samples"></a>Benutzeranwendungsbeispiele

- [AzureIP Test](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) ist ein Beispiel einer Konsolenanwendung, mit der Sie Dokumente mit einer Azure-Vorlage oder einer Ad-hoc-Richtlinie verschlüsseln können.
- [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) ist eine RMS-fähige Beispielanwendung, die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige Anwendung zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollten.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Tool, mit dem Sie Informationen zu einer beliebigen RMS-geschützten Datei erhalten können, wie z. B. Inhalts-ID oder Benutzerrechte.

## <a name="development-environment-setup"></a>Einrichtung der Entwicklungsumgebung

Die folgenden Anleitungen führen Sie durch betriebssystemspezifische Einrichtungsschritte für eine Anwendungsentwicklungsumgebung mithilfe häufig verwendeter Tools.

[![iOS/OSX-Setup](../media/develop/ios-icon.png)](ios-sdk.md)
[![Android-Setup](../media/develop/android-icon.png)](android-sdk.md)
[![Windows Phone-Setup](../media/develop/windows-phone-icon.png)](windows-phone-apps.md)
[![Windows Service-Setup](../media/develop/windows-icon.png)](install-the-rms-sdk.md)
[![Linux-Setup](../media/develop/linux-icon.png)](linux-setup.md)


## <a name="how-tos"></a>Vorgehensweisen

Jedes der folgenden Themen enthält spezifische Anleitungen für einen Aspekt der Implementierung Ihrer Anwendung. Dienstanwendungen werden mit dem RMS SDK 2.x erstellt. Benutzeranwendungen werden mit dem RMS SDK 4.x erstellt. Der Artikellink umfasst als Attribut den Anwendungstyp, d. h. Dienst oder Benutzer.

### <a name="general"></a>Allgemein

- [Aktivieren von Dokumentenverfolgung und -widerruf (Dienst)](tracking-content.md)
- [So stellen Sie Ihren Client bereit](../rms-client/client-deployment-notes.md)
- [Installieren und Konfigurieren eines RMS-Servers (Dienst)](how-to-install-and-configure-an-rms-server.md)
- [Verwenden der Dokumentenverfolgung (Benutzer)](how-to-use-document-tracking.md)


### <a name="security-and-authentication"></a>Sicherheit und Authentifizierung

- [Konfigurieren Ihrer App-Dienstanwendung für die Azure Active Directory-Anmeldung](https://docs.microsoft.com/en-us/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
- [Verwenden der Azure Active Directory-Authentifizierung (ADAL)](how-to-use-adal-authentication.md)
- [Konfigurieren von Azure RMS für die Authentifizierung (Dienst)](adal-auth.md)
- [Festlegen des API-Sicherheitsmodus (Dienst)](setting-the-api-security-mode-api-mode.md)
- [Aktivieren von Anwendungen für Azure RMS (Dienst)](how-to-use-file-api-with-aadrm-cloud.md)
- [Registrieren Ihrer App für Azure AD und Aktivieren der App für RMS (Benutzer)](authentication-integration.md)

### <a name="configuration-and-performance-management"></a>Konfiguration und Leistungsverwaltung

- [Hinzufügen expliziter Besitzerrechte (Dienst)](add-explicit-owner-rights.md)
- [Datei-API-Konfiguration (Dienst)](file-api-configuration.md)
- [Verwenden integrierter Rechte (Benutzer)](built-in-rights-usage-restriction-reference.md)
- [Aktivieren der Fehler- und Leistungsprotokollierung (Benutzer)](enabling-logging.md)

## <a name="videos"></a>Videos

Dan Plastina von Microsoft bietet diese [Einführung in Azure Information Protection](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection).

Diese Videos stammen von der Microsoft 2016 Ignite-Konferenz.

- [E-Mail-Sicherheit im Unternehmen](https://myignite.microsoft.com/videos/2787)
- [Einführen einer umfassenden identitätsgesteuerten Lösung für den Schutz und die sichere Freigabe von Dateien](https://myignite.microsoft.com/videos/2784)
- [Informationen zum persistenten Datenschutz durch Klassifizierung, Bezeichnung und Schutz](https://myignite.microsoft.com/videos/2786)

## <a name="other-resources"></a>Weitere Ressourcen

- [Anleitung zur bewährten Sicherheitsmethode](security-guidelines.md)
- [RMS Developer's Corner (Blog)](https://blogs.msdn.microsoft.com/rms/)
- [Häufig gestellte Fragen zu Azure Information Protection](https://docs.microsoft.com/en-us/information-protection/get-started/faqs)

### <a name="support-articles"></a>Supportartikel

- [Unterstützte Dateiformate](supported-file-formats.md)
- [Unterstützte Plattformen](supported-platforms.md)
- [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md)

### <a name="api-reference"></a>API-Referenz

- [Windows-API-Referenz](https://msdn.microsoft.com/en-us/library/hh535292.aspx)
  - [Windows SDK-Fehlercodes](https://msdn.microsoft.com/library/hh535248.aspx)
- [API-Referenz für Windows Phone und Windows Store](https://msdn.microsoft.com/library/dn891914.aspx)
- [iOS/OSX-API-Referenz](https://msdn.microsoft.com/en-us/library/dn758306.aspx)
- [Android-API-Referenz](https://msdn.microsoft.com/en-us/library/dn758245.aspx)
- [Linux-API-Referenz](http://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>Frühere Versionen

- Das [AD RMS-SDK](https://msdn.microsoft.com/en-us/library/cc530379.aspx) ist die erste Version des RMS-SDKs.
- Das [AD RMS-Skripttool](https://msdn.microsoft.com/en-us/library/bb968797.aspx) ist ein Verwaltungstool für eine AD RMS-Installation.

### <a name="see-also"></a>Weitere Informationen:

- [Entwicklerterminlogie](terms.md)
- [Terminologie zu Azure Information Protection – ITPro](../get-started/terminology.md)

[!INCLUDE[Commenting house rules](../includes/houserules.md)]
