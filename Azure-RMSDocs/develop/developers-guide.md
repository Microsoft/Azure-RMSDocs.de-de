---
title: Azure Information Protection-Entwicklerhandbuch
description: Entwickler können mithilfe von Azure Information Protection Dateien aller Typen schützen und verwalten.
author: msmbaldwin
ms.author: mbaldwin
manager: barbkess
ms.date: 10/11/2017
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: a53c2df2-a0a2-4f1f-995b-75ba55e4489b
ms.suite: ems
ms.reviewer: kartikk
ms.custom: has-adal-ref
ms.openlocfilehash: 1ce4499d20da066eddac8d01c29ef1b52ccea250
ms.sourcegitcommit: d01580c266de1019de5f895d65c4732f2c98456b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2020
ms.locfileid: "95567967"
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

PowerShell-Cmdlets, die von Administratoren für Azure Rights Management verwendet werden, sind außerdem beim Entwickeln und Testen Ihrer Dienstanwendungen hilfreich. Weitere Informationen finden Sie unter [Verwenden von PowerShell mit dem Azure Information Protection-Client](../rms-client/client-admin-guide-powershell.md).

## <a name="user-applications"></a>Benutzeranwendungen

Benutzeranwendungen können mit dem RMS SDK 2.1 oder dem RMS SDK 4.2 erstellt werden.
Die Version 4.2 basiert auf dem REST-Client mit betriebssystemspezifischen APIs für eine Reihe beliebter Betriebssysteme wie iOS/OSX, Android, Linux und Windows. Version 2.1 dient zum Erstellen nativer Windows-basierter Anwendungen.

### <a name="user-application-development-guides"></a>Anleitungen zur Entwicklung von Benutzeranwendungen

- [Entwickeln Ihrer Anwendung](developing-your-application.md)
- [Testen Ihrer Anwendung](how-to-set-up-your-test-environment.md)
- [Bereitstellen der Anwendung](deploying-your-application.md)

### <a name="user-application-samples"></a>Benutzeranwendungsbeispiele

- [AzureIP Test](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) ist ein Beispiel einer Konsolenanwendung, mit der Sie Dokumente mit einer Azure-Vorlage oder einer Ad-hoc-Richtlinie verschlüsseln können.
- [IPCNotepad](https://github.com/Azure-Samples/Azure-Information-Protection-Samples/tree/master/AzureIP_Test) ist eine RMS-fähige Beispielanwendung, die Sie durch die grundlegenden Schritte führt, die jede RMS-fähige Anwendung zum Schutz und zur Nutzung eingeschränkter Inhalte ausführen sollten.
- [RmsDocumentInspector](https://github.com/Azure-Samples/active-directory-dotnet-rms) ist ein Tool, mit dem Sie Informationen zu einer beliebigen RMS-geschützten Datei erhalten können, wie z. B. Inhalts-ID oder Benutzerrechte.

## <a name="development-environment-setup"></a>Einrichtung der Entwicklungsumgebung

Die folgenden Anleitungen führen Sie durch betriebssystemspezifische Einrichtungsschritte für eine Anwendungsentwicklungsumgebung mithilfe häufig verwendeter Tools.

[ ![ IOS/OSX-Setup](../media/develop/ios-icon.png)](ios-sdk.md) 
 [ ![ Android-Setup](../media/develop/android-icon.png)](android-sdk.md) 
 [ ![ Windows Phone](../media/develop/windows-phone-icon.png)](windows-phone-apps.md)Einrichten von Windows- 
 [ ![ Dienst Setup](../media/develop/windows-icon.png)](install-the-rms-sdk.md)Linux- 
 [ ![ Setup](../media/develop/linux-icon.png)](linux-setup.md)


## <a name="how-tos"></a>Gewusst wie

Jedes der folgenden Themen enthält spezifische Anleitungen für einen Aspekt der Implementierung Ihrer Anwendung. Dienstanwendungen werden mit dem RMS SDK 2.x erstellt. Benutzeranwendungen werden mit dem RMS SDK 4.x erstellt. Der Artikellink umfasst als Attribut den Anwendungstyp, d. h. Dienst oder Benutzer.

### <a name="general"></a>Allgemein

- [Aktivieren von Dokumentenverfolgung und -widerruf (Dienst)](tracking-content.md)
- [So stellen Sie Ihren Client bereit](../rms-client/client-deployment-notes.md)
- [Bereitstellen der Dienst-App in einem anderen Mandanten](how-to-deploy-app.md)
- [Installieren und Konfigurieren eines RMS-Servers (Dienst)](how-to-install-and-configure-an-rms-server.md)
- [Verwenden der Dokumentenverfolgung (Benutzer)](how-to-use-document-tracking.md)
- [So erneuern Sie einen symmetrischen Schlüssel in Azure Information Protection](how-to-renew-symmetric-key.md)

### <a name="security-and-authentication"></a>Sicherheit und Authentifizierung

- [Konfigurieren Ihrer APP Service-Anwendung für die Verwendung Azure Active Directory Anmelde namens](/azure/app-service-mobile/app-service-mobile-how-to-configure-active-directory-authentication)
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
- [Häufig gestellte Fragen zu Azure Information Protection](../faqs.md)

### <a name="support-articles"></a>Supportartikel

- [Unterstützte Dateiformate](supported-file-formats.md)
- [Unterstützte Plattformen](supported-platforms.md)
- [Grundlegendes zu Nutzungseinschränkungen](understanding-usage-restrictions.md)

### <a name="message-protocol-and-file-formats"></a>Nachrichtenprotokoll und Dateiformate

- [Client-an-Server-Protokolle](/openspecs/windows_protocols/ms-rmpr/d8ed4b1e-e605-4668-b173-6312cba6977e)
- [E-Mail-Objektprotokoll mit verwalteten Rechten](/openspecs/exchange_server_protocols/ms-oxormms/a121dda4-48f3-41f8-b12f-170f533038bb)
- [Format für die Verbunddatei der Binärdatei](/openspecs/windows_protocols/ms-cfb/53989ce4-7b05-4f8d-829b-d08d6148375b)

#### <a name="rights-managed-email-message"></a>E-Mail-Nachricht mit verwalteten Rechten

- [.MSG Dateiformat (Teil 1)](/archive/blogs/openspecification/msg-file-format-part-1)
- [.MSG Dateiformat (Teil 2)](/archive/blogs/openspecification/msg-file-format-rights-managed-email-message-part-2)

### <a name="api-reference"></a>API-Referenz

- [Windows-API-Referenz](/previous-versions/windows/desktop/msipc/msipc-reference)
  - [Windows SDK-Fehlercodes](/previous-versions/windows/desktop/msipc/error-codes)
- [API-Referenz für Windows Phone und Windows Store](/previous-versions/windows/desktop/msipcthin2/winrt)
- [iOS/OSX-API-Referenz](/previous-versions/windows/desktop/msipcthin2/ios)
- [Android-API-Referenz](/previous-versions/windows/desktop/msipcthin2/android)
- [Linux-API-Referenz](https://azuread.github.io/rms-sdk-for-cpp/annotated.html)

### <a name="previous-versions"></a>Vorherige Versionen

- Das [AD RMS-SDK](/previous-versions/windows/desktop/adrms_sdk/active-directory-rights-management-services-sdk-portal) ist die erste Version des RMS-SDKs.
- Das [AD RMS-Skripttool](/previous-versions/windows/desktop/adrms_script/adrms-script-portal) ist ein Verwaltungstool für eine AD RMS-Installation.

### <a name="see-also"></a>Siehe auch

- [Entwicklerterminologie](terms.md)
- [Terminologie zu Azure Information Protection – ITPro](../terminology.md)