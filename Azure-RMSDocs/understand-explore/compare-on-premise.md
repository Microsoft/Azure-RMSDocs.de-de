---
title: Vergleich von Azure Information Protection und AD RMS
description: Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen unterscheidet.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 03/06/2017
ms.topic: article
ms.prod: 
ms.service: information-protection
ms.technology: techgroup-identity
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: 3ac73576f67bee8d63c714352bfa4e75413ab972
ms.sourcegitcommit: 31e128cc1b917bf767987f0b2144b7f3b6288f2e
translationtype: HT
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Vergleich von Azure Information Protection und AD RMS

>*Gilt für: Active Directory Rights Management Services, Azure Information Protection, Office 365*

Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen als Lösung für den Schutz von Daten unterscheidet.

Einige der Hauptunterschiede von Azure Information Protection:

- **Keine Serverinfrastruktur erforderlich:** Azure Information Protection benötigt nicht die zusätzlichen Server und PKI-Zertifikate, die AD RMS erfordert, da sich Microsoft Azure für Sie darum kümmert. Dadurch kann diese Cloudlösung schneller bereitgestellt werden und ist leichter zu verwalten.

- **Cloudbasierte Authentifizierung:** Azure Information Protection verwendet Azure AD für die Authentifizierung – sowohl für interne als auch für Benutzer anderer Organisationen. Das bedeutet, dass Ihre mobilen Benutzer authentifiziert werden können, selbst wenn sie nicht mit Ihrem internen Netzwerk verbunden sind. Außerdem ist es einfacher, geschützte Inhalte für Benutzer aus anderen Organisationen freizugeben. Viele Organisationen verfügen bereits über Benutzerkonten in Azure AD, da sie Azure-Dienste ausführen oder Office 365 haben. Falls dies nicht der Fall ist, lässt RMS for Individuals Benutzer ein kostenloses Konto erstellen. Sie müssen explizite Vertrauensstellungen mit jeder Organisation konfigurieren, um von AD RMS geschützten Inhalt für andere Organisationen freizugeben.

- **Integrierter Support für mobile Geräte**: Es sind keine Bereitstellungsänderungen erforderlich, damit Azure RMS mobile Geräte und Macintosh-Computer unterstützt. Sie müssen die Mobilgeräteerweiterung installieren, AD FS für den Verbund konfigurieren und zusätzliche Datensätze für Ihren öffentlichen DNS-Dienst erstellen, damit diese Geräte von AD RMS unterstützt werden.

- **Standardvorlagen:** Azure Information Protection erstellt zwei Standardvorlagen, sobald der Schutzdienst aktiviert ist. Dadurch ist es sehr einfach, sofort mit dem Schützen wichtiger Daten zu beginnen. Es gibt keine Standardvorlagen für AD RMS.

- **Abteilungsvorlagen:** Azure Information Protection unterstützt Abteilungsvorlagen als eine Konfigurationseinstellung für die zusätzlichen Vorlagen, die Sie erstellen. Durch diese Einstellung können Sie angeben, welchen Benutzern die Vorlage in ihren Clientanwendungen (wie z.B. Office-Apps) angezeigt wird. Dadurch wird ihnen das Auswählen der richtigen Richtlinie erleichtert, die Sie für verschiedene Benutzergruppen definieren. AD RMS unterstützt keine Abteilungsvorlagen.

- **Dokumentenverfolgung und Sperrung**: Azure Information Protection unterstützt diese Features mit dem Azure Information Protection-Client, während dies bei AD RMS nicht der Fall ist.

- **Klassifizierungen und Bezeichnungen:** Azure Information Protection unterstützt diese Features über den Azure Information Protection-Client, der in Office-Anwendungen und den Datei-Explorer integriert ist, während dies bei AD RMS nicht der Fall ist.


Zudem kann Azure Information Protection neue Features und Fixes schneller bereitstellen als eine lokale, serverbasierte Lösung, da es sich dabei um einen Clouddienst handelt. Es sind keine neuen Features für AD RMS unter Windows Server 2016 geplant.

Weitere Informationen und Unterschiede finden Sie in der folgenden Tabelle, die eine vergleichende Gegenüberstellung der Features und Vorteile von Azure Information Protection und AD RMS zeigt. Antworten auf sicherheitsbezogene Fragen, die den Vergleich betreffen, finden Sie im Abschnitt [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Artikel.

> [!NOTE]
> Um diesen Vergleich zu erleichtern, werden hier einige Informationen aus [Voraussetzungen für Azure Information Protection](../get-started/requirements-azure-rms.md) wiederholt. In dieser Quelle finden Sie spezifischere Support- und Versionsinformationen zu [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)].

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Unterstützt IRM-Funktionen (Verwaltung von Informationsrechten) in Microsoft Online Services wie Exchange Online und SharePoint Online sowie in Office 365.<br /><br />Unterstützt ebenfalls lokale Microsoft-Serverprodukte wie Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden.|Unterstützt lokale Microsoft-Serverprodukte wie Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden.|
|Ermöglicht implizite Vertrauensstellungen zwischen Organisationen und Benutzern in jeder Organisation. Dies bedeutet, dass geschützter Inhalt zwischen Benutzern innerhalb derselben Organisation oder zwischen Organisationen freigegeben werden kann, wenn die Benutzer über [!INCLUDE[o365_1](../includes/o365_1_md.md)] oder [!INCLUDE[aad_rightsmanagement_1](../includes/aad_rightsmanagement_1_md.md)] verfügen oder sich für RMS for Individuals registrieren.|Vertrauensstellungen müssen ausdrücklich in einer direkten Punkt-zu-Punkt-Beziehung zwischen Organisationen definiert werden, indem entweder vertrauenswürdige Benutzerdomänen oder Verbundvertrauensstellungen verwendet werden, die Sie mithilfe der Active Directory-Verbunddienste (Active Directory Federation Services, AD FS) erstellen.|
|Stellt zwei Standardvorlagen für Rechterichtlinien bereit, die den Zugriff auf die Inhalte auf Ihre eigene Organisation beschränken. Eine, die die schreibgeschützte Anzeige geschützter Inhalte bietet, und eine andere Vorlage, die Schreib- oder Änderungsberechtigungen für den geschützten Inhalt bereitstellt.<br /><br />Sie können auch eigene benutzerdefinierte Vorlagen erstellen, wozu Abteilungsvorlagen gehören, die nur für eine Teilmenge von Benutzern sichtbar sind. Weitere Informationen finden Sie unter [Konfigurieren benutzerdefinierter Vorlagen für den Azure Rights Management-Dienst](../deploy-use/configure-custom-templates.md).<br /><br />Zusätzlich können Benutzer ihren eigenen Berechtigungssatz definieren, wenn die Vorlagen nicht ausreichen.|Es sind keine standardmäßigen Vorlagen für Benutzerrechterichtlinien verfügbar. Sie müssen diese erstellen und dann verteilen. Weitere Informationen finden Sie unter [Überlegungen zur AD RMS-Richtlinienvorlage](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Zusätzlich können Benutzer ihren eigenen Berechtigungssatz definieren, wenn die Vorlagen nicht ausreichen.|
|Die unterstützte Mindestversion von Microsoft Office ist Office 2010, wofür der [Azure Information Protection-Client](../rms-client/aip-client.md) oder die RMS-Freigabeanwendung erforderlich ist.<br /><br />Microsoft Office für Mac:<br /><br />– Microsoft Office für Mac 2016: Wird unterstützt<br /><br />– Microsoft Office für Mac 2011: Wird nicht unterstützt|Die unterstützte Mindestversion von Microsoft Office ist Office 2007.<br /><br />Microsoft Office für Mac:<br /><br />– Microsoft Office für Mac 2016: Wird unterstützt<br /><br />– Microsoft Office für Mac 2011: Wird unterstützt|
|Unterstützt den [Azure Information Protection-Client](../rms-client/aip-client.md) für Windows, iOS und Android. Macintosh-Computer und Windows Phone-Geräte werden weiterhin von der RMS-Freigabeanwendung unterstützt.<br /><br />Zudem unterstützt der Azure Information Protection-Client Folgendes:<br /><br />– Freigeben für Personen in einer anderen Organisation<br /><br />– Eine Website für die Dokumentnachverfolgung für Benutzer mit der Möglichkeit, ein Dokument zu widerrufen|Unterstützt den [Azure Information Protection-Client](../rms-client/aip-client.md) für Windows, iOS und Android. Macintosh-Computer und Windows Phone-Geräte werden weiterhin von der RMS-Freigabeanwendung unterstützt. Allerdings unterstützt Freigeben weder ein Freigeben für Benutzer in einer anderen Organisation noch die Dokumentenverfolgung oder die Möglichkeit für Benutzer, Dokumente zu widerrufen.|
|Die meisten [Dateitypen](../rms-client/client-admin-guide-file-types.md) können mithilfe des Azure Information Protection-Clients klassifiziert und geschützt werden.<br /><br />Weitere Informationen zu anderen Anwendungen finden Sie in der Tabelle im [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-applications.md).|Die meisten [Dateitypen](../rms-client/client-admin-guide-file-types.md) können mithilfe des Azure Information Protection-Clients geschützt werden.<br /><br />Weitere Informationen zu anderen Anwendungen finden Sie in der Tabelle im [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](../get-started/requirements-applications.md).|
|Die unterstützte Mindestversion des Windows-Clients ist Windows 7 SP1.|Die unterstützte Mindestversion des Windows-Clients ist Windows Vista Service Pack 2.|
|Die Unterstützung mobiler Geräte umfasst Windows Phone, Android, iOS und Windows RT.<br /><br />E-Mail-Unterstützung durch Verwendung von Exchange ActiveSync IRM wird ebenfalls auf allen mobilen Geräteplattformen unterstützt, die dieses Protokoll unterstützen.|Die Unterstützung mobiler Geräte umfasst Windows Phone, Android, iOS und Windows RT und erfordert die [mobile Erweiterung für Active Directory-Rechteverwaltungsdienste](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />E-Mail-Unterstützung durch Verwendung von Exchange ActiveSync IRM wird auf allen mobilen Geräteplattformen unterstützt, die dieses Protokoll unterstützen.|
|Unterstützt Multi-Factor Authentication (MFA) für Computer und mobile Geräte.<br /><br />Weitere Informationen finden Sie unter [Multi-Factor Authentication (MFA) und Azure Information Protection](../get-started/requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Unterstützt Smartcard-Authentifizierung, wenn IIS so konfiguriert ist, dass Zertifikate angefordert werden.|
|Unterstützt den Kryptografiemodus 2 ohne zusätzliche Konfiguration, der höhere Sicherheit für Schlüssellängen und Verschlüsselungsalgorithmus bietet.<br /><br />Weitere Informationen finden Sie im Artikel [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Thema und in [AD RMS-Kryptografiemodi](http://go.microsoft.com/fwlink/?LinkId=266659).|Unterstützt standardmäßig den Kryptografiemodus 1 und erfordert eine zusätzliche Konfiguration zur Unterstützung des Kryptografiemodus 2 für höhere Sicherheit.<br /><br />Weitere Informationen finden Sie im Artikel [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Thema und in [AD RMS-Kryptografiemodi](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Unterstützt die Migration von AD RMS und, falls erforderlich, zu AD RMS:<br /><br />- [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](../deploy-use/decommission-deactivate.md)|Unterstützt das Migrieren zu und von Azure Information Protection:<br /><br />- [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](../deploy-use/decommission-deactivate.md)<br /><br />- [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md)|
|Erfordert eine Azure Information Protection-Lizenz oder Azure Rights Management-Lizenz mit Office 365, um Inhalte zu schützen. Es ist keine Lizenz erforderlich, um Inhalte zu verwenden, die mit Azure Information Protection geschützt wurden (einschließlich Benutzern aus einer anderen Organisation).<br /><br />Weitere Informationen finden Sie in der [Featureliste](https://www.microsoft.com/en-us/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website.|Erfordert eine RMS-Lizenz, um Inhalte zu schützen, sowie zum Verwenden von Inhalten, die mit AD RMS geschützt wurden.<br /><br />Weitere, allgemeine Informationen zur Lizenzierung für AD RMS finden Sie unter [Clientzugriffslizenzen und Management-Lizenzen](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) . Wenn Sie spezifische Informationen benötigen, wenden Sie sich bitte an Ihren Microsoft-Partner oder den für Sie zuständigen Mitarbeiter von Microsoft.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Kryptografiesteuerelemente zum Signieren und Verschlüsseln
Azure Information Protection verwendet standardmäßig RSA 2048 für alle Kryptografieaufgaben mit öffentlichem Schlüssel und SHA 256 für Signaturvorgänge. Im Vergleich unterstützt AD RMS RSA 1024 und RSA 2048 sowie SHA 1 und SHA 256 für Signaturvorgänge.

Sowohl Azure Information Protection als auch AD RMS verwenden AES 128 für die symmetrische Verschlüsselung.

Azure Information Protection ist mit FIPS 140-2 kompatibel, wenn Ihre Mandanten 2.048-Bit-Schlüssel verwenden, dem Standard, wenn der Azure Rights Management-Dienst aktiviert wird. 

Weitere Informationen über die kryptografischen Steuerelemente finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellänge](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Nächste Schritte
Wenn Sie eine Migration von AD RMS zu Azure Information Protection durchführen möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](../plan-design/migrate-from-ad-rms-to-azure-rms.md) nach.

[!INCLUDE[Commenting house rules](../includes/houserules.md)]

