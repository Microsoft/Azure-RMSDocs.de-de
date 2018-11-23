---
title: Vergleich von Azure Information Protection und AD RMS
description: Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen unterscheidet.
author: cabailey
ms.author: cabailey
manager: mbaldwin
ms.date: 08/16/2018
ms.topic: conceptual
ms.service: information-protection
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.openlocfilehash: d9b79ddc859f4e53f53f55efa0a9e0167987cf20
ms.sourcegitcommit: 26a2c1becdf3e3145dc1168f5ea8492f2e1ff2f3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2018
ms.locfileid: "44148208"
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Vergleich von Azure Information Protection und AD RMS

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](http://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen als Lösung für den Schutz von Daten unterscheidet.

Einige der Hauptunterschiede von Azure Information Protection:

- **Keine Serverinfrastruktur erforderlich:** Azure Information Protection benötigt nicht die zusätzlichen Server und PKI-Zertifikate, die AD RMS erfordert, da sich Microsoft Azure für Sie darum kümmert. Dadurch kann diese Cloudlösung schneller bereitgestellt werden und ist leichter zu verwalten.

- **Cloudbasierte Authentifizierung:** Azure Information Protection verwendet Azure AD für die Authentifizierung – sowohl für interne als auch für Benutzer anderer Organisationen. Das bedeutet, dass Ihre mobilen Benutzer authentifiziert werden können, selbst wenn sie nicht mit Ihrem internen Netzwerk verbunden sind. Außerdem ist es einfacher, geschützte Inhalte für Benutzer aus anderen Organisationen freizugeben. Viele Organisationen verfügen bereits über Benutzerkonten in Azure AD, da sie Azure-Dienste ausführen oder Office 365 haben. Wenn dies nicht der Fall ist, können Benutzer in Microsoft Rights Management for Individuals ein kostenloses Konto erstellen. Alternativ kann ein Microsoft-Konto für [Anwendungen verwendet werden, die diese Authentifizierung für Azure Information Protection unterstützen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents). Sie müssen explizite Vertrauensstellungen mit jeder Organisation konfigurieren, um von AD RMS geschützten Inhalt für andere Organisationen freizugeben.

- **Integrierter Support für mobile Geräte**: Es sind keine Bereitstellungsänderungen erforderlich, damit Azure RMS mobile Geräte und Macintosh-Computer unterstützt. Sie müssen die Mobilgeräteerweiterung installieren, AD FS für den Verbund konfigurieren und zusätzliche Datensätze für Ihren öffentlichen DNS-Dienst erstellen, damit diese Geräte von AD RMS unterstützt werden.

- **Standardvorlagen:** Azure Information Protection erstellt zwei Standardvorlagen, sobald der Schutzdienst aktiviert ist. Dadurch ist es einfach, sofort mit dem Schützen wichtiger Daten zu beginnen. Es gibt keine Standardvorlagen für AD RMS.

- **Abteilungsvorlagen:** Azure Information Protection unterstützt Abteilungsvorlagen als eine Konfigurationseinstellung für die zusätzlichen Vorlagen, die Sie erstellen. Mit dieser Konfiguration können Sie eine Teilmenge von Benutzern angeben, um bestimmte Vorlagen in deren Clientanwendungen anzuzeigen. Das Reduzieren der Anzahl von Vorlagen, die Benutzern angezeigt werden, erleichtert es ihnen, die richtige Richtlinie auszuwählen, die Sie für unterschiedliche Benutzergruppen definieren. AD RMS unterstützt keine Abteilungsvorlagen.

- **Dokumentenverfolgung und Sperrung**: Azure Information Protection unterstützt diese Features mit dem Azure Information Protection-Client, während dies bei AD RMS nicht der Fall ist.

- **Klassifizierungen und Bezeichnungen:** Azure Information Protection unterstützt diese Features über den Azure Information Protection-Client, der in Office-Anwendungen und den Datei-Explorer integriert ist, während dies bei AD RMS nicht der Fall ist.


Zudem kann Azure Information Protection neue Features und Fixes schneller bereitstellen als eine lokale, serverbasierte Lösung, da es sich dabei um einen Clouddienst handelt. Es sind keine neuen Features für AD RMS unter Windows Server 2016 geplant.

Weitere Informationen und Unterschiede finden Sie in der folgenden Tabelle, die eine vergleichende Gegenüberstellung der Features und Vorteile von Azure Information Protection und AD RMS zeigt. Antworten auf sicherheitsbezogene Fragen, die den Vergleich betreffen, finden Sie im Abschnitt [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Artikel.

> [!NOTE]
> Um diesen Vergleich zu erleichtern, werden hier einige Informationen aus [Voraussetzungen für Azure Information Protection](requirements.md) wiederholt. In dieser Quelle finden Sie spezifischere Informationen zur Unterstützung und den Versionen von Azure Rights Management.

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Unterstützt IRM-Funktionen (Verwaltung von Informationsrechten) in Microsoft Online Services wie Exchange Online und SharePoint Online sowie in Office 365.<br /><br />Unterstützt ebenfalls lokale Microsoft-Serverprodukte wie Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden.|Unterstützt lokale Microsoft-Serverprodukte wie Exchange Server, SharePoint Server und Dateiserver, die unter Windows Server ausgeführt werden und die Dateiklassifizierungsinfrastruktur verwenden.|
|Aktiviert automatisch die sichere Kollaboration an Dokumenten mit jeder beliebigen Organisation, die ebenso Azure AD für die Authentifizierung verwendet. Das bedeutet, dass Organisationen Dokumente schützen können, die sie intern oder für andere Organisationen freigeben.|Eine sichere Zusammenarbeit an Dokumenten außerhalb der Organisation erfordert, dass die Vertrauensstellung der Authentifizierung explizit in einer direkten Punkt-zu-Punkt-Beziehung zwischen den beiden Organisationen definiert ist. Sie müssen entweder vertrauenswürdige Benutzerdomänen (TUDs) oder Verbundvertrauensstellungen konfigurieren, die Sie mithilfe der Active Directory-Verbunddienste (AD FS) erstellen.|
|Senden Sie eine geschützte E-Mail (optional mit Office-Dokumentanlagen, die automatisch geschützt sind) an Benutzer, wenn keine Vertrauensstellungsbeziehung für die Authentifizierung existiert. Dieses Szenario wird durch die Verwendung eines Verbunds mit sozialen Netzwerken oder einer Einmalkennung und eines Webbrowsers zur Ansicht möglich gemacht.|Unterstützt nicht das Senden geschützter E-Mails, wenn keine Vertrauensstellung für die Authentifizierung besteht.|
|Stellt zwei Standardvorlagen für Rechterichtlinien bereit, die den Zugriff auf die Inhalte auf Ihre eigene Organisation beschränken. Eine, die die schreibgeschützte Anzeige geschützter Inhalte bietet, und eine andere Vorlage, die Schreib- oder Änderungsberechtigungen für den geschützten Inhalt bereitstellt.<br /><br />Sie können auch eigene benutzerdefinierte Vorlagen erstellen, wozu Abteilungsvorlagen gehören, die nur für eine Teilmenge von Benutzern sichtbar sind. Weitere Informationen finden Sie unter [Konfigurieren und Verwalten von Vorlagen in der Azure Information Protection-Richtlinie](configure-policy-templates.md).<br /><br />Zusätzlich können Benutzer ihren eigenen Berechtigungssatz definieren, wenn die Vorlagen nicht ausreichen.|Es sind keine standardmäßigen Vorlagen verfügbar. Sie müssen Ihre eigenen Vorlagen erstellen und dann verteilen. Weitere Informationen finden Sie unter [Überlegungen zur AD RMS-Richtlinienvorlage](http://go.microsoft.com/fwlink/?LinkId=154765).<br /><br />Zusätzlich können Benutzer ihren eigenen Berechtigungssatz definieren, wenn die Vorlagen nicht ausreichen.|
|Die unterstützte Mindestversion von Microsoft Office ist Office 2010, wofür der [Azure Information Protection-Client](./rms-client/aip-client.md) oder die RMS-Freigabeanwendung erforderlich ist.<br /><br />Microsoft Office für Mac:<br /><br />– Microsoft Office für Mac 2016: Wird unterstützt|Die unterstützte Mindestversion von Microsoft Office ist Office 2010.<br /><br />Microsoft Office für Mac:<br /><br />– Microsoft Office für Mac 2016: Wird unterstützt|
|Unterstützt den [Azure Information Protection-Client](./rms-client/aip-client.md) für Windows, iOS und Android. Mac-Computer und Windows Phone-Geräte werden weiterhin von der RMS-Freigabeanwendung unterstützt.<br /><br />Zudem unterstützt der Azure Information Protection-Client Folgendes:<br /><br />– Freigeben für Personen in einer anderen Organisation<br /><br />– Eine Website für die Dokumentnachverfolgung für Benutzer mit der Möglichkeit, ein Dokument zu widerrufen|Unterstützt den [Azure Information Protection-Client](./rms-client/aip-client.md) für Windows, iOS und Android. Macintosh-Computer und Windows Phone-Geräte werden weiterhin von der RMS-Freigabeanwendung unterstützt. Allerdings unterstützt Freigeben weder ein Freigeben für Benutzer in einer anderen Organisation noch die Dokumentenverfolgung oder die Möglichkeit für Benutzer, Dokumente zu widerrufen.|
|Die meisten [Dateitypen](./rms-client/client-admin-guide-file-types.md) können mithilfe des Azure Information Protection-Clients klassifiziert und geschützt werden.<br /><br />Weitere Informationen zu anderen Anwendungen finden Sie in der Tabelle im [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](./requirements-applications.md).|Die meisten [Dateitypen](./rms-client/client-admin-guide-file-types.md) können mithilfe des Azure Information Protection-Clients geschützt werden.<br /><br />Weitere Informationen zu anderen Anwendungen finden Sie in der Tabelle im [Anwendungen mit Unterstützung für den Azure Rights Management-Schutz von Daten](./requirements-applications.md).|
|Die unterstützte Mindestversion des Windows-Clients ist Windows 7 SP1.|Die unterstützte Mindestversion des Windows-Clients ist Windows 7 SP1.|
|Die Unterstützung mobiler Geräte umfasst Windows Phone, Android, iOS und Windows RT.<br /><br />E-Mail-Unterstützung durch Verwendung von Exchange ActiveSync IRM wird ebenfalls auf allen mobilen Geräteplattformen unterstützt, die dieses Protokoll unterstützen.|Die Unterstützung mobiler Geräte umfasst Windows Phone, Android, iOS und Windows RT und erfordert die [mobile Erweiterung für Active Directory-Rechteverwaltungsdienste](http://technet.microsoft.com/library/dn673574.aspx).<br /><br />E-Mail-Unterstützung durch Verwendung von Exchange ActiveSync IRM wird auf allen mobilen Geräteplattformen unterstützt, die dieses Protokoll unterstützen.|
|Unterstützt Multi-Factor Authentication (MFA) für Computer und mobile Geräte.<br /><br />Weitere Informationen finden Sie unter [Multi-Factor Authentication (MFA) und Azure Information Protection](./requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Unterstützt Smartcard-Authentifizierung, wenn IIS so konfiguriert ist, dass Zertifikate angefordert werden.|
|Unterstützt den Kryptografiemodus 2 ohne zusätzliche Konfiguration, der höhere Sicherheit für Schlüssellängen und Verschlüsselungsalgorithmus bietet.<br /><br />Weitere Informationen finden Sie im Artikel [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Thema und in [AD RMS-Kryptografiemodi](http://go.microsoft.com/fwlink/?LinkId=266659).|Unterstützt standardmäßig den Kryptografiemodus 1 und erfordert eine zusätzliche Konfiguration zur Unterstützung des Kryptografiemodus 2 für höhere Sicherheit.<br /><br />Weitere Informationen finden Sie im Artikel [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Thema und in [AD RMS-Kryptografiemodi](http://go.microsoft.com/fwlink/?LinkId=266659).|
|Unterstützt die Migration von AD RMS und, falls erforderlich, zu AD RMS:<br /><br />- [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)<br /><br />- [Außerbetriebsetzen und Deaktivieren von Azure Information Protection](decommission-deactivate.md)|Unterstützt das Migrieren zu und von Azure Information Protection:<br /><br />- [Außerbetriebsetzen und Deaktivieren von Azure Rights Management](decommission-deactivate.md)<br /><br />- [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md)|
|Erfordert eine Azure Information Protection-Lizenz oder Azure Rights Management-Lizenz mit Office 365, um Inhalte zu schützen. Es ist keine Lizenz erforderlich, um Inhalte zu verwenden, die mit Azure Information Protection geschützt wurden (./einschließlich Benutzern aus einer anderen Organisation).<br /><br />Weitere Informationen finden Sie in der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website.|Erfordert eine RMS-Lizenz, um Inhalte zu schützen, sowie zum Verwenden von Inhalten, die mit AD RMS geschützt wurden.<br /><br />Weitere, allgemeine Informationen zur Lizenzierung für AD RMS finden Sie unter [Clientzugriffslizenzen und Management-Lizenzen](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) . Wenn Sie spezifische Informationen benötigen, wenden Sie sich bitte an Ihren Microsoft-Partner oder den für Sie zuständigen Mitarbeiter von Microsoft.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Kryptografiesteuerelemente zum Signieren und Verschlüsseln
Azure Information Protection verwendet standardmäßig RSA 2048 für alle Kryptografieaufgaben mit öffentlichem Schlüssel und SHA 256 für Signaturvorgänge. Im Vergleich unterstützt AD RMS RSA 1024 und RSA 2048 sowie SHA 1 und SHA 256 für Signaturvorgänge.

Sowohl Azure Information Protection als auch AD RMS verwenden AES 128 für die symmetrische Verschlüsselung.

Azure Information Protection ist mit FIPS 140-2 kompatibel, wenn Ihre Mandanten 2048-Bit-Schlüssel verwenden, dem Standard, wenn der Azure Rights Management-Dienst aktiviert wird. 

Weitere Informationen über die kryptografischen Steuerelemente finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellänge](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Nächste Schritte
Wenn Sie eine Migration von AD RMS zu Azure Information Protection durchführen möchten, lesen Sie unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md) nach.

