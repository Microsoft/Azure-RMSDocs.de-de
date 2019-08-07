---
title: Vergleich von Azure Information Protection und AD RMS – AIP
description: Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen unterscheidet.
author: cabailey
ms.author: cabailey
manager: barbkess
ms.date: 07/15/2019
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: cbeaa6b8cd46d7e53efd076de16b0f4b2b36dcee
ms.sourcegitcommit: 9968a003865ff2456c570cf552f801a816b1db07
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/05/2019
ms.locfileid: "68789606"
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Vergleich von Azure Information Protection und AD RMS

>*Gilt für: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*

Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen als Lösung für den Schutz von Daten unterscheidet.

Einige der Hauptunterschiede von Azure Information Protection:

- **Keine Serverinfrastruktur erforderlich**: Azure Information Protection benötigt nicht die zusätzlichen Server und PKI-Zertifikate, die AD RMS erfordert, da sich Microsoft Azure für Sie darum kümmert. Dadurch kann diese Cloudlösung schneller bereitgestellt werden und ist leichter zu verwalten.

- **Cloudbasierte Authentifizierung**: Azure Information Protection verwendet Azure AD für die Authentifizierung – sowohl für interne Benutzer als auch für Benutzer anderer Organisationen. Dies bedeutet, dass Ihre Benutzer auch dann authentifiziert werden können, wenn Sie nicht mit Ihrem internen Netzwerk verbunden sind. Außerdem ist es einfacher, geschützte Inhalte für Benutzer aus anderen Organisationen freizugeben. Viele Organisationen verfügen bereits über Benutzerkonten in Azure AD, da sie Azure-Dienste ausführen oder Office 365 haben. Wenn dies nicht der Fall ist, können Benutzer in Microsoft Rights Management for Individuals ein kostenloses Konto erstellen. Alternativ kann ein Microsoft-Konto für [Anwendungen verwendet werden, die diese Authentifizierung für Azure Information Protection unterstützen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents). Sie müssen explizite Vertrauensstellungen mit jeder Organisation konfigurieren, um von AD RMS geschützten Inhalt für andere Organisationen freizugeben.

- **Integrierter Support für mobile Geräte**: Für die Azure Information Protection zur Unterstützung mobiler Geräte und Macintosh-Computer sind keine Änderungen an der Bereitstellung erforderlich. Sie müssen die Mobilgeräteerweiterung installieren, AD FS für den Verbund konfigurieren und zusätzliche Datensätze für Ihren öffentlichen DNS-Dienst erstellen, damit diese Geräte von AD RMS unterstützt werden.

- **Standardvorlagen**: Azure Information Protection erstellt automatisch Standardvorlagen, mit denen der Zugriff auf die Inhalte auf Ihre eigene Organisation beschränkt wird. Diese Vorlagen erleichtern es, sofort mit dem Schutz sensibler Daten zu beginnen. Es gibt keine Standardvorlagen für AD RMS.

- **Abteilungsvorlagen**: Auch bekannt als „bereichsbezogene Vorlagen“. Azure Information Protection unterstützt Abteilungsvorlagen für zusätzlich von Ihnen erstellte Vorlagen. Mit dieser Konfiguration können Sie eine Teilmenge von Benutzern angeben, um bestimmte Vorlagen in deren Clientanwendungen anzuzeigen. Das Reduzieren der Anzahl von Vorlagen, die Benutzern angezeigt werden, erleichtert es ihnen, die richtige Richtlinie auszuwählen, die Sie für unterschiedliche Benutzergruppen definieren. AD RMS unterstützt keine Abteilungsvorlagen.

- **Dokumentenverfolgung und Sperrung**: Azure Information Protection unterstützt diese Features mit dem Azure Information Protection Client (klassisch), während AD RMS nicht.

- **Klassifizierungen und Bezeichnungen**: Azure Information Protection unterstützt diese Features mit dem [Azure Information Protection Client (klassisch) und dem Azure Information Protection Unified-Bezeichnung-Client](./rms-client/use-client.md#choose-which-azure-information-protection-client-to-use). Diese Clients können in Office-Anwendungen und im Datei-Explorer integriert werden, AD RMS jedoch nicht. Zudem kann Azure Information Protection neue Features und Fixes schneller bereitstellen als eine lokale, serverbasierte Lösung, da es sich dabei um einen Clouddienst handelt. Es sind keine neuen Features für AD RMS unter Windows Server geplant.

Für andere Unterschiede verwenden Sie die folgende Tabelle für einen parallelen Vergleich. Antworten auf sicherheitsbezogene Fragen, die den Vergleich betreffen, finden Sie im Abschnitt [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Artikel.

|Azure Information Protection|AD RMS|
|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
|Unterstützt Funktionen für die Verwaltung von Informationsrechten (Information Rights Management, unm) in Microsoft Online Services und lokalen Microsoft-Server Produkten.|In werden die Funktionen zur Verwaltung von Informationsrechten (Information Rights Management, unm) für lokale Microsoft-Server Produkte und Exchange Online unterstützt.|
|Aktiviert automatisch die sichere Kollaboration an Dokumenten mit jeder beliebigen Organisation, die ebenso Azure AD für die Authentifizierung verwendet.|Eine sichere Zusammenarbeit an Dokumenten außerhalb der Organisation erfordert, dass die Vertrauensstellung der Authentifizierung explizit in einer direkten Punkt-zu-Punkt-Beziehung zwischen den beiden Organisationen definiert ist. Sie müssen entweder vertrauenswürdige Benutzerdomänen (TUDs) oder Verbundvertrauensstellungen konfigurieren, die Sie mithilfe der Active Directory-Verbunddienste (AD FS) erstellen.|
|Senden Sie eine geschützte E-Mail (optional mit Office-Dokumentanlagen, die automatisch geschützt sind) an Benutzer, wenn keine Vertrauensstellungsbeziehung für die Authentifizierung existiert. Dieses Szenario wird durch die Verwendung eines Verbunds mit sozialen Netzwerken oder einer Einmalkennung und eines Webbrowsers zur Ansicht möglich gemacht.|Unterstützt nicht das Senden geschützter E-Mails, wenn keine Vertrauensstellung für die Authentifizierung besteht.|
|Unterstützt den Azure Information Protection Client (klassisch) und den Azure Information Protection Unified-Beschriftungs Client.|Unterstützt die Azure Information Protection Client-(klassisch) und die Verbrauchs Unterstützung nur für den Azure Information Protection Unified-Bezeichnungs Client, wenn Sie auch die [Active Directory Rights Management Services-Erweiterung für mobile Geräte] installieren.
|Unterstützt Multi-Factor Authentication (MFA) für Computer und mobile Geräte.<br /><br />Weitere Informationen finden Sie unter [Multi-Factor Authentication (MFA) und Azure Information Protection](./requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Unterstützt Smartcard-Authentifizierung, wenn IIS so konfiguriert ist, dass Zertifikate angefordert werden.|
|Unterstützt standardmäßig den Kryptografiemodus 2, um ein empfohlenes Sicherheitsniveau für Schlüssellängen und Verschlüsselungsalgorithmen bereitzustellen.|Unterstützt standardmäßig den Kryptografiemodus 1 und erfordert eine zusätzliche Konfiguration zur Unterstützung des Kryptografiemodus 2 für ein empfohlenes Sicherheitsniveau.<br /><br />Weitere Informationen finden Sie unter [AD RMS kryptografiemodi](https://go.microsoft.com/fwlink/?LinkId=266659).|
|Erfordert eine Azure Information Protection-Lizenz oder Azure Rights Management-Lizenz mit Office 365, um Inhalte zu schützen. Es ist keine Lizenz erforderlich, um Inhalte zu verwenden, die mit Azure Information Protection geschützt wurden (einschließlich Benutzern aus einer anderen Organisation).<br /><br />Weitere Informationen finden Sie in der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) auf der Azure Information Protection-Website.|Erfordert eine RMS-Lizenz, um Inhalte zu schützen, sowie zum Verwenden von Inhalten, die mit AD RMS geschützt wurden.<br /><br />Weitere, allgemeine Informationen zur Lizenzierung für AD RMS finden Sie unter [Clientzugriffslizenzen und Management-Lizenzen](https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx) . Wenn Sie spezifische Informationen benötigen, wenden Sie sich bitte an Ihren Microsoft-Partner oder den für Sie zuständigen Mitarbeiter von Microsoft.|

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Kryptografiesteuerelemente zum Signieren und Verschlüsseln
Azure Information Protection verwendet standardmäßig RSA 2048 für alle Kryptografieaufgaben mit öffentlichem Schlüssel und SHA 256 für Signaturvorgänge. Im Vergleich unterstützt AD RMS RSA 1024 und RSA 2048 sowie SHA 1 und SHA 256 für Signaturvorgänge.

Sowohl Azure Information Protection als auch AD RMS verwenden AES 128 für die symmetrische Verschlüsselung.

Azure Information Protection ist mit FIPS 140-2 kompatibel, wenn Ihre Mandanten 2048-Bit-Schlüssel verwenden, dem Standard, wenn der Azure Rights Management-Dienst aktiviert wird. 

Weitere Informationen über die kryptografischen Steuerelemente finden Sie unter [Cryptographic controls used by Azure RMS: Algorithms and key length (Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellänge).](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths)


## <a name="next-steps"></a>Nächste Schritte
Ausführlichere Anforderungen zur Verwendung von Azure Information Protection, z. b. Geräte Unterstützung und Mindestversionen, finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

Wenn Sie von AD RMS zu Azure Information Protection migrieren möchten, finden Sie weitere Informationen unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

Möglicherweise interessieren Sie sich für die folgenden FAQs:
- [Worin besteht der Unterschied zwischen Azure Information Protection und Microsoft Information Protection?](faqs.md#whats-the-difference-between-azure-information-protection-and-microsoft-information-protection)
- [Worin besteht der Unterschied zwischen Azure Information Protection und Azure Rights Management?](faqs.md#whats-the-difference-between-azure-information-protection-and-azure-rights-management)

