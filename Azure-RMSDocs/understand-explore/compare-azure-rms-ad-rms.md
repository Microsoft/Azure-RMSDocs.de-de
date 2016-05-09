---
# required metadata

title: Vergleich zwischen Azure Rights Management und AD RMS | Azure RMS
description:
keywords:
author: cabailey
manager: mbaldwin
ms.date: 04/28/2016
ms.topic: article
ms.prod: azure
ms.service: rights-management
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: esaggese
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Vergleich zwischen Azure Rights Management und AD RMS
Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] (Azure RMS) in Bezug auf die Funktionen und Anforderungen unterscheidet. In der folgenden Tabelle finden Sie eine vergleichende Gegenüberstellung der Features und Vorteile von Azure RMS und AD RMS. Antworten auf sicherheitsbezogene Fragen, die den Vergleich betreffen, finden Sie im Abschnitt [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](compare-azure-rms-ad-rms.md#cryptographic-controls-for-signing-and-encryption) in diesem Artikel.

> [!NOTE]
> Um diesen Vergleich zu erleichtern, werden hier einige Informationen aus [Voraussetzungen für Azure Rights Management](../get-started/requirements-azure-rms.md) wiederholt. In diesem Artikel finden Sie spezifischere Support- und Versionsinformationen zu [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Azure RMS|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Unterstützt IRM-Funktionen (Verwaltung von Informationsrechten) in Microsoft Online Services wie Exchange Online und SharePoint Online sowie in Office 365.<br /><br />Unterstützt ebenfalls lokale Microsoft-Serverprodukte wie Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden.|Unterstützt lokale Microsoft-Serverprodukte wie Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden.|
|Ermöglicht implizite Vertrauensstellungen zwischen Organisationen und Benutzern in jeder Organisation. Dies bedeutet, dass geschützter Inhalt zwischen Benutzern innerhalb derselben Organisation oder zwischen Organisationen freigegeben werden kann, wenn die Benutzer [!INCLUDE[o365_1](../includes/o365_1_md.md)], or [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] haben oder sich für RMS für Einzelpersonen registrieren.|Vertrauensstellungen müssen ausdrücklich in einer direkten Punkt-zu-Punkt-Beziehung zwischen Organisationen definiert werden, indem entweder vertrauenswürdige Benutzerdomänen oder Verbundvertrauensstellungen verwendet werden, die Sie mithilfe der Active Directory-Verbunddienste (Active Directory Federation Services, AD FS) erstellen.|
|Stellt zwei Standardvorlagen für Rechterichtlinien bereit, die den Zugriff auf die Inhalte auf Ihre eigene Organisation beschränken. Eine, die die schreibgeschützte Anzeige geschützter Inhalte bietet, und eine andere Vorlage, die Schreib- oder Änderungsberechtigungen für den geschützten Inhalt bereitstellt.<br /><br />Sie können auch eigene benutzerdefinierte Vorlagen erstellen, wozu Abteilungsvorlagen gehören, die nur für eine Teilmenge von Benutzern sichtbar sind. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für Azure Rights Management](../deploy-use/configure-custom-templates.md).<br /><br />Zusätzlich können Benutzer ihren eigenen Berechtigungssatz definieren, wenn die Vorlagen nicht ausreichen.|Es sind keine standardmäßigen Vorlagen für Benutzerrechterichtlinien verfügbar. Sie müssen diese erstellen und dann verteilen. Weitere Informationen finden Sie unter [Überlegungen zur AD RMS-Richtlinienvorlage](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Zusätzlich können Benutzer ihren eigenen Berechtigungssatz definieren, wenn die Vorlagen nicht ausreichen.|
|Die unterstützte Mindestversion von Microsoft Office ist Office 2010, wofür die [RMS-Freigabeanwendung](../rms-client/sharing-app-windows.md) erforderlich ist.<br /><br />Microsoft Office für Mac:<br /><br />Microsoft Office für Mac 2016: Wird unterstützt<br /><br />Microsoft Office für Mac 2011: Wird nicht unterstützt|Die unterstützte Mindestversion von Microsoft Office ist Office 2007.<br /><br />Microsoft Office für Mac:<br /><br />Microsoft Office für Mac 2016: Wird unterstützt<br /><br />Microsoft Office für Mac 2011: Wird unterstützt|
|Unterstützt die [RMS-Freigabeanwendung](../rms-client/sharing-app-windows.md) für Windows, für Mac-Computer und für mobile Geräte.<br /><br />Zusätzlich unterstützt die RMS-Freigabeanwendung Folgendes:<br /><br />Freigeben für Personen in einer anderen Organisation<br /><br />E-Mail-Benachrichtigungen, die den Absender informieren, wenn jemand versucht, eine geschützte Anlage zu öffnen<br /><br />Eine Website für Dokumentnachverfolgung mit der Möglichkeit, ein Dokument zu widerrufen|Unterstützt die [RMS-Freigabeanwendung](../rms-client/sharing-app-windows.md) für Windows, für Mac-Computer und für mobile Geräte. Allerdings unterstützt Freigeben weder ein Freigeben für Benutzer in einer anderen Organisation, noch E-Mail-Benachrichtigungen oder die Dokumentnachverfolgung noch die Möglichkeit für Benutzer, Dokumente zu widerrufen.|
|Alle Dateitypen können bei Verwendung der RMS-Freigabeanwendung mit [nativem oder allgemeinem Schutz](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) geschützt werden.<br /><br />Für andere Anwendungen sind die Informationen in der [Tabelle mit den Funktionen der Clientgeräte](../get-started/requirements-client-devices.md#client-device-capabilities) enthalten.|Alle Dateitypen können bei Verwendung der RMS-Freigabeanwendung mit [nativem oder allgemeinem Schutz](../rms-client/sharing-app-admin-guide-technical.md#levels-of-protection-native-and-generic) geschützt werden.<br /><br />Für andere Anwendungen sind die Informationen in der [Tabelle mit den Funktionen der Clientgeräte](../get-started/requirements-client-devices.md#client-device-capabilities) enthalten.|
|Die unterstützte Mindestversion des Windows-Clients ist Windows 7.|Die unterstützte Mindestversion des Windows-Clients ist Windows Vista Service Pack 2.|
|Die Unterstützung mobiler Geräte umfasst Windows Phone, Android, iOS und Windows RT.<br /><br />E-Mail-Unterstützung durch Verwendung von Exchange ActiveSync IRM wird ebenfalls auf allen mobilen Geräteplattformen unterstützt, die dieses Protokoll unterstützen.|Die Unterstützung mobiler Geräte umfasst Windows Phone, Android, iOS und Windows RT und erfordert die [mobile Erweiterung für Active Directory-Rechteverwaltungsdienste](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />E-Mail-Unterstützung durch Verwendung von Exchange ActiveSync IRM wird auf allen mobilen Geräteplattformen unterstützt, die dieses Protokoll unterstützen.|
|Unterstützt Multi-Factor Authentication (MFA) für Computer und mobile Geräte.<br /><br />Weitere Informationen finden Sie unter [Multi-Factor Authentication (MFA) und Azure RMS](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-rms).|Unterstützt Smartcard-Authentifizierung, wenn IIS so konfiguriert ist, dass Zertifikate angefordert werden.|
|Unterstützt den Kryptografiemodus 2 ohne zusätzliche Konfiguration, der höhere Sicherheit für Schlüssellängen und Verschlüsselungsalgorithmus bietet.<br /><br />Weitere Informationen finden Sie im Artikel [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Thema und in [AD RMS-Kryptografiemodi](http://go.microsoft.com/fwlink/?LinkId=266659).|Unterstützt standardmäßig den Kryptografiemodus 1 und erfordert eine zusätzliche Konfiguration zur Unterstützung des Kryptografiemodus 2 für höhere Sicherheit.<br /><br />Weitere Informationen finden Sie im Artikel [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Thema und in [AD RMS-Kryptografiemodi](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Unterstützt die Migration von AD RMS und, falls erforderlich, zu AD RMS:<br /><br />[Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />[Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md)|Unterstützt die Migration von AD RMS und zu Azure RMS:<br /><br />[Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md)<br /><br />[Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|Erfordert eine RMS-Lizenz, um Inhalte zu schützen. Es ist keine RMS-Lizenz erforderlich, um Inhalte zu verwenden, die mit Azure RMS geschützt wurden (einschließlich Benutzern aus einer anderen Organisation).<br /><br />Weitere Informationen finden Sie unter [Cloud-Abonnements, die Azure RMS unterstützen](../get-started/requirements-subscriptions.md).|Erfordert eine RMS-Lizenz, um Inhalte zu schützen, sowie zum Verwenden von Inhalten, die mit AD RMS geschützt wurden.<br /><br />Weitere, allgemeine Informationen zur Lizenzierung für AD RMS finden Sie unter [Clientzugriffslizenzen und Management-Lizenzen](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) . Wenn Sie spezifische Informationen benötigen, wenden Sie sich bitte an Ihren Microsoft-Partner oder den für Sie zuständigen Mitarbeiter von Microsoft.|

## Kryptografiesteuerelemente zum Signieren und Verschlüsseln
[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] verwendet immer RSA 2048 für Kryptografieaufgaben mit öffentlichem Schlüssel und SHA 256 für Signaturvorgänge. Im Vergleich unterstützt AD RMS RSA 1024 und RSA 2048 sowie SHA 1 und SHA 256 für Signaturvorgänge.

Sowohl [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] als auch AD RMS verwenden AES 128 für die symmetrische Verschlüsselung.

[!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] ist mit FIPS 140-2 kompatibel, wenn Ihr Mandantenschlüssel von Microsoft erstellt und verwaltet wird (Standard), oder wenn Sie Ihren eigenen Mandantenschlüssel verwalten (bekannt als BYOK). Weitere Informationen zur Verwaltung des Mandantenschlüssels finden Sie unter [Planen und Implementieren Ihres Azure Rights Management-Mandantenschlüssels](../plan-design/plan-implement-tenant-key.md).

## Nächste Schritte
Wenn Sie die Migration von AD RMS zu Azure RMS durchführen möchten, helfen Ihnen die Informationen unter [Migration von AD RMS zu Azure Rights Management](../plan-design/migrate-from-ad-rms-to-azure-rms.md) weiter.




<!--HONumber=Apr16_HO3-->


