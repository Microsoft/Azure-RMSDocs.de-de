---
title: Vergleich von Azure Information Protection und AD RMS – AIP
description: Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen unterscheidet.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 11/08/2020
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 8123bd62-1814-4d79-b306-e20c1a00e264
ms.reviewer: esaggese
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 8e7cce8032a713f77f40714650fb37bfae257ec4
ms.sourcegitcommit: 8a141858e494dd1d3e48831e6cd5a5be48ac00d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2020
ms.locfileid: "97383906"
---
# <a name="comparing-azure-information-protection-and-ad-rms"></a>Vergleich von Azure Information Protection und AD RMS

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), [Office 365](https://download.microsoft.com/download/E/C/F/ECF42E71-4EC0-48FF-AA00-577AC14D5B5C/Azure_Information_Protection_licensing_datasheet_EN-US.pdf)*
>
>***Relevant für**: [AIP Unified Bezeichnung Client und Classic Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). *

>[!NOTE] 
> Um eine einheitliche und optimierte Kundenfreundlichkeit zu gewährleisten, werden **Azure Information Protection klassische Client** -und Bezeichnungs **Verwaltung** im Azure- **Portal ab dem** **31. März 2021** eingestellt. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Wenn Sie Active Directory Rights Management Services (AD RMS) bereits kennen oder bereitgestellt haben, fragen Sie sich vielleicht, wie sich Azure Information Protection in Bezug auf die Funktionen und Anforderungen als Lösung für den Schutz von Daten unterscheidet.

Zu den Haupt Unterschieden bei Azure Information Protection gehören:

|Unterschied  |Beschreibung  |
|---------|---------|
|**Keine Serverinfrastruktur erforderlich**     |  Azure Information Protection benötigt nicht die zusätzlichen Server und PKI-Zertifikate, die AD RMS erfordert, da sich Microsoft Azure für Sie darum kümmert. <br><br>Dadurch kann diese Cloudlösung schneller bereitgestellt werden und ist leichter zu verwalten.       |
|**Cloudbasierte Authentifizierung**     |  Azure Information Protection verwendet Azure AD für die Authentifizierung – sowohl für interne Benutzer als auch für Benutzer anderer Organisationen. <br><br>Dies bedeutet, dass Ihre Benutzer auch dann authentifiziert werden können, wenn Sie nicht mit Ihrem internen Netzwerk verbunden sind. Außerdem ist es einfacher, geschützte Inhalte für Benutzer aus anderen Organisationen freizugeben. <br><br>Viele Organisationen verfügen bereits über Benutzerkonten in Azure AD, da Sie Azure-Dienste ausführen oder über Microsoft 365 verfügen. Wenn dies nicht der Fall ist, können Benutzer in Microsoft Rights Management for Individuals ein kostenloses Konto erstellen. Alternativ kann ein Microsoft-Konto für [Anwendungen verwendet werden, die diese Authentifizierung für Azure Information Protection unterstützen](secure-collaboration-documents.md#supported-scenarios-for-opening-protected-documents). <br><br>Wenn Sie AD RMS geschützten Inhalt in einer anderen Organisation freigeben möchten, müssen Sie für jede Organisation explizite Vertrauens Stellungen konfigurieren.       |
|**Integrierte Unterstützung für mobile Geräte**     | Für die Azure Information Protection zur Unterstützung mobiler Geräte und Macintosh-Computer sind keine Änderungen an der Bereitstellung erforderlich. <br><br>Sie müssen die Mobilgeräteerweiterung installieren, AD FS für den Verbund konfigurieren und zusätzliche Datensätze für Ihren öffentlichen DNS-Dienst erstellen, damit diese Geräte von AD RMS unterstützt werden.        |
|**Standardvorlagen**     |  Azure Information Protection erstellt automatisch Standardvorlagen, mit denen der Zugriff auf die Inhalte auf Ihre eigene Organisation beschränkt wird. Diese Vorlagen erleichtern es, sofort mit dem Schutz sensibler Daten zu beginnen. <br><br>Es gibt keine Standardvorlagen für AD RMS.       |
|**Abteilungs Vorlagen**     | Auch bekannt als „bereichsbezogene Vorlagen“. Azure Information Protection unterstützt Abteilungsvorlagen für zusätzlich von Ihnen erstellte Vorlagen. <br><br>Mit dieser Konfiguration können Sie eine Teilmenge von Benutzern angeben, um bestimmte Vorlagen in deren Clientanwendungen anzuzeigen. Das Reduzieren der Anzahl von Vorlagen, die Benutzern angezeigt werden, erleichtert es ihnen, die richtige Richtlinie auszuwählen, die Sie für unterschiedliche Benutzergruppen definieren. <br><br>AD RMS unterstützt keine Abteilungsvorlagen.        |
|**Dokumentenverfolgung und-Sperrung**     |  Azure Information Protection unterstützt diese Funktionen nur mit dem klassischen Azure Information Protection-Client, während AD RMS überhaupt nicht.       |
|**Klassifizierung und Bezeichnung**     | Azure Information Protection unterstützt Bezeichnungen, die die Klassifizierung und optional Schutz anwenden. Diese Funktionen werden sowohl mit der [einheitlichen Bezeichnung AIP als auch mit den klassischen Clients](rms-client/use-client.md#choose-your-windows-labeling-solution)bereitgestellt. <br><br>Verwenden Sie den AIP-Client, um Klassifizierungen und Bezeichnungen mit Office-Anwendungen, dem Datei-Explorer, PowerShell und einem Scanner für lokale Datenspeicher zu integrieren. <br><br>   AD RMS unterstützt diese Klassifizierungs-und Beschriftungs Funktionen nicht.        |
| | |

Zudem kann Azure Information Protection neue Features und Fixes schneller bereitstellen als eine lokale, serverbasierte Lösung, da es sich dabei um einen Clouddienst handelt. Es sind keine neuen Features für AD RMS unter Windows Server geplant.


### <a name="detailed-comparison-between-aip-and-ad-rms"></a>Detaillierter Vergleich zwischen AIP und AD RMS

Weitere Informationen finden Sie in der folgenden Tabelle für einen parallelen Vergleich. 

Antworten auf sicherheitsbezogene Fragen, die den Vergleich betreffen, finden Sie im Abschnitt [Kryptografiesteuerelemente zum Signieren und Verschlüsseln](#cryptographic-controls-for-signing-and-encryption) in diesem Artikel.


|Unterschied|Azure Information Protection|AD RMS|
|----------|-----------------------------------------------------------------------------------------|--------------------------------------------------------|
| **Information Rights Management (IRM)**|Unterstützt die unm-Funktionen sowohl für Microsoft Online Services als auch für lokale Microsoft-Server Produkte.|Unterstützt die unm-Funktionen für lokale Microsoft-Server Produkte und Exchange Online.|
| **Sichere Zusammenarbeit**|Aktiviert automatisch die sichere Kollaboration an Dokumenten mit jeder beliebigen Organisation, die ebenso Azure AD für die Authentifizierung verwendet.|Eine sichere Zusammenarbeit an Dokumenten außerhalb der Organisation erfordert, dass die Vertrauensstellung der Authentifizierung explizit in einer direkten Punkt-zu-Punkt-Beziehung zwischen den beiden Organisationen definiert ist. <br><br>Sie müssen entweder vertrauenswürdige Benutzerdomänen (TUDs) oder Verbundvertrauensstellungen konfigurieren, die Sie mithilfe der Active Directory-Verbunddienste (AD FS) erstellen.|
| **Geschützte e-Mails**|Senden Sie eine geschützte E-Mail (optional mit Office-Dokumentanlagen, die automatisch geschützt sind) an Benutzer, wenn keine Vertrauensstellungsbeziehung für die Authentifizierung existiert. <br><br>Dieses Szenario wird durch die Verwendung eines Verbunds mit sozialen Netzwerken oder einer Einmalkennung und eines Webbrowsers zur Ansicht möglich gemacht.|Unterstützt nicht das Senden geschützter E-Mails, wenn keine Vertrauensstellung für die Authentifizierung besteht.|
| **Client Unterstützung**|Unterstützt sowohl die vereinheitlichte AIP-Bezeichnung als auch klassische Clients für Schutz-und Nutzungs Aktivitäten. |Unterstützt den AIP Unified-Bezeichnungs Client nur für die Nutzung und erfordert, dass Sie die [Active Directory Rights Management Services Mobile-Geräte Erweiterung](./active-directory-rights-manage-mobile-device.md)installieren. <br><br>Unterstützt den klassischen AIP-Client für Schutz-und verbrauchsaktivitäten. 
| **So funktioniert's: Azure Multi-Factor Authentication**|Unterstützt MFA für Computer und mobile Geräte.<br /><br />Weitere Informationen finden Sie unter [Multi-Factor Authentication (MFA) und Azure Information Protection](./requirements-azure-ad.md#multi-factor-authentication-mfa-and-azure-information-protection).|Unterstützt Smartcard-Authentifizierung, wenn IIS so konfiguriert ist, dass Zertifikate angefordert werden.|
| **Kryptografiemodus**|Unterstützt standardmäßig den Kryptografiemodus 2, um ein empfohlenes Sicherheitsniveau für Schlüssellängen und Verschlüsselungsalgorithmen bereitzustellen.|Unterstützt standardmäßig den Kryptografiemodus 1 und erfordert eine zusätzliche Konfiguration zur Unterstützung des Kryptografiemodus 2 für ein empfohlenes Sicherheitsniveau.<br /><br />Weitere Informationen finden Sie unter [AD RMS-Kryptografiemodi](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
| **Lizenzierung**|Erfordert eine Azure Information Protection Lizenz oder eine Azure Rights Management-Lizenz mit Microsoft 365, um Inhalte zu schützen. <br /><br />Es ist keine Lizenz erforderlich, um Inhalte zu verwenden, die durch AIP geschützt sind (einschließlich Benutzer aus einer anderen Organisation).<br /><br />Weitere Informationen zur Lizenzierung, einschließlich der Unterschiede zwischen einer P1-und P2-Lizenz, finden Sie in der [Featureliste](https://www.microsoft.com/cloud-platform/azure-information-protection-features) der Azure Information Protection Website.|Erfordert eine RMS-Lizenz, um Inhalte zu schützen, sowie zum Verwenden von Inhalten, die mit AD RMS geschützt wurden.<br /><br />Weitere Informationen zur Lizenzierung finden Sie unter [Client Zugriffs Lizenzen und Verwaltungs Lizenzen](https://www.microsoft.com/Licensing/product-licensing/client-access-license.aspx) , um allgemeine Informationen zu erhalten, wenden Sie sich jedoch an Ihren Microsoft-Partner oder Microsoft-Vertreter, um spezifische Informationen zu erhalten|
| | | |

## <a name="cryptographic-controls-for-signing-and-encryption"></a>Kryprotgrafiesteuerelemente zum Signieren und Verschlüsseln
Azure Information Protection verwendet standardmäßig RSA 2048 für alle Kryptografieaufgaben mit öffentlichem Schlüssel und SHA 256 für Signaturvorgänge. Im Vergleich unterstützt AD RMS RSA 1024 und RSA 2048 sowie SHA 1 und SHA 256 für Signaturvorgänge.

Sowohl Azure Information Protection als auch AD RMS verwenden AES 128 für die symmetrische Verschlüsselung.

Azure Information Protection ist mit FIPS 140-2 kompatibel, wenn Ihre Mandanten 2048-Bit-Schlüssel verwenden, dem Standard, wenn der Azure Rights Management-Dienst aktiviert wird. 

Weitere Informationen über die kryptografischen Steuerelemente finden Sie unter [Von Azure RMS verwendete kryptografische Steuerelemente: Algorithmen und Schlüssellänge](how-does-it-work.md#cryptographic-controls-used-by-azure-rms-algorithms-and-key-lengths).


## <a name="next-steps"></a>Nächste Schritte
Ausführlichere Anforderungen zur Verwendung von Azure Information Protection, z. b. Geräte Unterstützung und Mindestversionen, finden Sie unter [Anforderungen für Azure Information Protection](requirements.md).

Wenn Sie von AD RMS zu Azure Information Protection migrieren möchten, finden Sie weitere Informationen unter [Migrieren von AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md).

Beginnen Sie mit [Active Directory Rights Management Services Erweiterung für mobile Geräte](./active-directory-rights-manage-mobile-device.md). 

Möglicherweise interessieren Sie sich für die folgenden FAQs:
- [Was ist der Unterschied zwischen Azure Information Protection und Microsoft Information Protection?](faqs.md#whats-the-difference-between-azure-information-protection-and-microsoft-information-protection)
- [Was ist der Unterschied zwischen Azure Information Protection und Azure Rights Management?](faqs.md#whats-the-difference-between-azure-information-protection-and-azure-rights-management)