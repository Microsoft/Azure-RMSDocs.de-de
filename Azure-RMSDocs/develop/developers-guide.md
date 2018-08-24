---
title: Azure Information Protection-Entwicklerhandbuch
description: Entwickler können mithilfe von Azure Information Protection Dateien aller Typen schützen und verwalten.
author: lleonard-msft
ms.author: alleonar
manager: mbaldwin
ms.date: 10/11/2017
ms.topic: article
ms.service: information-protection
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.openlocfilehash: 59c9a2db3f0959a5c4bfb9e65248598b14276825
ms.sourcegitcommit: 7ba9850e5bb07b14741bb90ebbe98f1ebe057b10
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/23/2018
ms.locfileid: "42808558"
---
# <a name="azure-information-protection-developers-guide"></a>Azure Information Protection-Entwicklerhandbuch

Dieses Handbuch ist auf Tools zum Erweitern und Integrieren des Rechteverwaltungsdiensts von Azure Information Protection ausgerichtet.

>Das derzeitige Azure Information Protection SDK verfügt über die Komponente zur Rechteverwaltung. Eine Klassifizierung und eine Bezeichnungskomponente werden entwickelt.

## <a name="service-applications"></a>Dienstanwendungen

Dienstanwendungen bieten Funktionen zum Schutz von Informationen beim Exportieren aus einem Enterprise Content Management-System, einer Geschäftsanwendung oder einer cloudbasierten Geschäftslösung. DLP (Data Loss Prevention) und CAS (Cloud Application Security) sind Beispiele für Dienstanwendungen. Unser SDK zum Entwickeln von Dienstanwendungen steht über zwei Programmiermodelle zur Verfügung.

- [C++](https://www.microsoft.com/download/details.aspx?id=38397)
- [C#-verwaltete API](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/IpcManagedAPI)

### <a name="examples-of-service-applications"></a>Beispiele für Dienstanwendungen

- [IpcDlp](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist eine RMS-fähige DLP-Anwendung (Data Leak Protection), die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige DLP-Anwendung mithilfe der RMS-Datei-API zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollte.
- [IpcAzureApp](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Beispiel für die Verwendung des RMS SDK in Azure-Anwendungen, um Daten im Azure Blob-Speicher zu schützen.
- [RmsFileWatcher](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Beispiel, das veranschaulicht, wie eine Windows-Anwendung erstellt wird, die Verzeichnisse im Dateisystem überwacht, und RMS-Schutzrichtlinien bei jeder Änderung anwendet, z. B. beim Hinzufügen oder Ändern einer Datei.
- [ProtectFilesInDir](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/ProtectFilesInDir) ist ein Beispiel für eine einfache Konsolenanwendung, die ein Verzeichnis als Eingabe verwendet und ohne Rekursion ausschließlich alle Dateien in diesem Verzeichnis schützt.

## <a name="powershell-guides"></a>PowerShell-Anleitungen

PowerShell-Cmdlets, die von Administratoren für Azure Rights Management verwendet werden, sind außerdem beim Entwickeln und Testen Ihrer Dienstanwendungen hilfreich. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](/azure/information-protection/rms-client/client-admin-guide-powershell).

## <a name="user-applications"></a>Benutzeranwendungen

Benutzeranwendungen können mit dem RMS SDK 2.1 oder dem RMS SDK 4.2 erstellt werden.
Die Version 4.2 basiert auf dem REST-Client mit betriebssystemspezifischen APIs für eine Reihe beliebter Betriebssysteme wie iOS/OSX, Android, Linux und Windows. Version 2.1 dient zum Erstellen nativer Windows-basierter Anwendungen.

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
- [Bereitstellen der Dienst-App in einem anderen Mandanten] (how-to-deploy-app.md)
- [Installieren und Konfigurieren eines RMS-Servers (Dienst)](how-to-install-and-configure-an-rms-server.md)
- [Verwenden der Dokumentenverfolgung (Benutzer)](how-to-use-document-tracking.md)
- [So erneuern Sie einen symmetrischen Schlüssel in Azure Information Protection](how-to-renew-symmetric-key.md)

### <a name="security-and-authentication"></a>Sicherheit und Authentifizierung

- [Konfigurieren Ihrer App-Dienstanwendung für die Azure Active Directory-Anmeldung](https://docs.microsoft.com/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
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

## <a name="introduction-and-datasheets"></a>Einführung und Datenblätter

[Einführung in Azure Information Protection](https://www.microsoft.com/cloud-platform/azure-information-protection)

## <a name="other-resources"></a>Weitere Ressourcen

- [Anleitung zur bewährten Sicherheitsmethode](security-guidelines.md)
- [RMS Developer's Corner (Blog)](https://blogs.msdn.microsoft.com/rms/)
- [Häufig gestellte Fragen zu Azure Information Protection](https://docs.microsoft.com/information-protection/get-started/faqs)

### <a name="support-articles"></a>Supportartikel

- [Unterstützte Dateiformate](supported-file-formats.md)
- [Unterstützte Plattformen](supported-platforms.md)
- [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md)

### <a name="message-protocol-and-file-formats"></a>Nachrichtenprotokoll und Dateiformate

- [Client-an-Server-Protokolle](https://msdn.microsoft.com/library/cc243191.aspx)
- [E-Mail-Objektprotokoll mit verwalteten Rechten](https://msdn.microsoft.com/library/cc463909(v=EXCHG.80).aspx)
- [Format für die Verbunddatei der Binärdatei](https://msdn.microsoft.com/library/dd942138.aspx)

#### <a name="rights-managed-email-message"></a>E-Mail-Nachricht mit verwalteten Rechten

- [.MSG Dateiformat (Teil 1)](https://blogs.msdn.microsoft.com/openspecification/2009/11/06/msg-file-format-part-1/)
- [.MSG Dateiformat (Teil 2)](https://blogs.msdn.microsoft.com/openspecification/2010/06/20/msg-file-format-rights-managed-email-message-part-2/)

### <a name="api-reference"></a>API-Referenz

- [Windows-API-Referenz](https://msdn.microsoft.com/library/hh535292.aspx)
  - [Windows SDK-Fehlercodes](https://msdn.microsoft.com/library/hh535248.aspx)
- [API-Referenz für Windows Phone und Windows Store](https://msdn.microsoft.com/library/dn891914.aspx)
- [iOS/OSX-API-Referenz](https://msdn.microsoft.com/library/dn758306.aspx)
- [Android-API-Referenz](https://msdn.microsoft.com/library/dn758245.aspx)
- [Linux-API-Referenz](http://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>Frühere Versionen

- Das [AD RMS-SDK](https://msdn.microsoft.com/library/cc530379.aspx) ist die erste Version des RMS-SDKs.
- Das [AD RMS-Skripttool](https://msdn.microsoft.com/library/bb968797.aspx) ist ein Verwaltungstool für eine AD RMS-Installation.

### <a name="see-also"></a>Siehe auch

- [Entwicklerterminologie](terms.md)
- [Terminologie zu Azure Information Protection – ITPro](../terminology.md)

