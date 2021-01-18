---
title: Hyok-Schutz (Hold Your Own Key) für Azure Information Protection
description: Übersicht über den HYOK-Schutz (AD RMS) mit Azure Information Protection und die dazugehörigen Szenarios, Einschränkungen, Voraussetzungen und Empfehlungen.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 10/13/2020
ms.topic: how-to
ms.collection: M365-security-compliance
ms.service: information-protection
ms.assetid: 7667b5b0-c2e9-4fcf-970f-05577ba51126
ROBOTS: NOINDEX
ms.subservice: hyok
ms.custom: admin
ms.openlocfilehash: 129c07876106d02174b1bab1d4eea82205160b69
ms.sourcegitcommit: af7ac2eeb8f103402c0036dd461c77911fbc9877
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "98559573"
---
# <a name="hold-your-own-key-hyok-details-for-azure-information-protection"></a>Hold Your Own Key (Hyok)-Details für Azure Information Protection

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection)*
>
>***Relevant für**: [Azure Information Protection klassischen Client für Windows](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum Unified-Bezeichnungs Client finden Sie unter [doppelte Schlüssel Verschlüsselung](plan-implement-tenant-key.md#double-key-encryption-dke). *

> [!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).

Mithilfe von Hold Your Own Key (Hyok)-Konfigurationen können AIP-Kunden mit dem klassischen Client äußerst sensiblen Inhalt schützen und gleichzeitig die vollständige Kontrolle über den Schlüssel behalten. Hyok verwendet einen zusätzlichen, vom Kunden gehaltenen Schlüssel, der lokal für hochsensible Inhalte gespeichert ist, sowie den standardmäßigen cloudbasierten Schutz, der für andere Inhalte verwendet wird. 

Weitere Informationen zu den standardmäßigen cloudbasierten Mandanten Stamm Schlüsseln finden [Sie unter Planning and Implementierungs your Azure Information Protection Tenant Key](plan-implement-tenant-key.md).

## <a name="cloud-based-protection-vs-hyok"></a>Cloudbasierter Schutz im Vergleich zu Hyok

Der Schutz sensibler Dokumente und e-Mails mithilfe von Azure Information Protection verwendet in der Regel einen cloudbasierten Schlüssel, der entweder [von Microsoft](plan-implement-tenant-key.md#tenant-root-keys-generated-by-microsoft) oder [vom Kunden mithilfe einer Byok-Konfiguration](byok-price-restrictions.md)generiert wird. 

Cloudbasierte Schlüssel werden in Azure Key Vault verwaltet, was Kunden die folgenden Vorteile bietet:

- **Keine Serverinfrastruktur Anforderungen**. Cloudlösungen sind schneller und kostengünstiger, als lokale Lösungen bereitzustellen und zu verwalten.

- Die **cloudbasierte Authentifizierung** ermöglicht eine einfachere Freigabe für Partner und Benutzer anderer Organisationen. 

- **Enge Integration mit anderen Azure-und Microsoft 365-Diensten**, z. b. Suche, Web-Viewer, pivotierte Ansichten, Antischadsoftware, eDiscovery und Delta.

- **Dokumentenverfolgung**, Sperrung und **e-Mail-Benachrichtigungen** für sensible **Dokumente, die** Sie freigegeben haben.

Allerdings haben einige Organisationen möglicherweise gesetzliche Anforderungen, die erfordern, dass bestimmte Inhalte mit einem Schlüssel verschlüsselt werden, der von der Cloud isoliert ist. Diese Isolation bedeutet, dass verschlüsselter Inhalt nur von lokalen Anwendungen und lokalen Diensten gelesen werden kann.

Bei Hyok-Konfigurationen verfügen Kunden Mandanten sowohl über einen [cloudbasierten Schlüssel](plan-implement-tenant-key.md) zur Verwendung mit Inhalt, der in der Cloud gespeichert werden kann, als auch über einen lokalen Schlüssel für Inhalte, die nur lokal geschützt werden müssen.

## <a name="hyok-guidance-and-best-practices"></a>HYOK-Leitfaden und Best Practices

Beachten Sie beim Konfigurieren von Hyok die folgenden Empfehlungen:

- [Für Hyok geeigneter Inhalt](#content-suitable-for-hyok)
- [Hiermit werden die Benutzer definiert, die Hyok-konfigurierte Bezeichnungen sehen können.](#define-the-users-who-can-see-hyok-configured-labels)
- [Hyok und e-Mail-Support](#hyok-and-email-support)

> [!IMPORTANT]
> Eine Hyok-Konfiguration für Azure Information Protection ist kein Ersatz für eine vollständige AD RMS und Azure Information Protection Bereitstellung oder eine Alternative zum [Migrieren AD RMS zu Azure Information Protection](migrate-from-ad-rms-to-azure-rms.md). 
>
> Hyok wird nur durch Anwenden von Bezeichnungen unterstützt, bietet keine Funktions Parität mit AD RMS und unterstützt nicht alle AD RMS Bereitstellungs Konfigurationen.

### <a name="content-suitable-for-hyok"></a>Für Hyok geeigneter Inhalt

Der Hyok-Schutz bietet nicht die Vorteile des cloudbasierten Schutzes und führt häufig zu den Kosten für "Daten Deckkraft", da auf den Inhalt nur durch lokale Anwendungen und Dienste zugegriffen werden kann. Sogar für Organisationen, die den Hyok-Schutz verwenden, ist es in der Regel nur für eine kleine Anzahl von Dokumenten geeignet. 

Es wird empfohlen, dass Sie Hyok nur für Inhalte verwenden, die den folgenden Kriterien entsprechen:

- Inhalt mit der höchsten Klassifizierung in Ihrer Organisation ("Oberstes Geheimnis"), bei der der Zugriff auf nur wenige Personen beschränkt ist
- Inhalt, der nicht außerhalb der Organisation freigegeben wird
- Inhalt, der nur im internen Netzwerk verwendet wird.

### <a name="define-the-users-who-can-see-hyok-configured-labels"></a>Hiermit werden die Benutzer definiert, die Hyok-konfigurierte Bezeichnungen sehen können.

Um sicherzustellen, dass nur Benutzer, die Hyok-Schutz anwenden müssen, die in Hyok konfigurierten Bezeichnungen sehen, konfigurieren Sie die Richtlinie für Benutzer mit Bereichs bezogenen [Richtlinien](configure-policy-scope.md).

### <a name="hyok-and-email-support"></a>Hyok und e-Mail-Support

Microsoft 365 Dienste und andere Onlinedienste können durch Hyok geschützte Inhalte nicht entschlüsseln.

Bei e-Mails umfasst dieser Funktionsverlust z. b. schadsoftwarescanner, verschlüsselungsgeschützter Schutz, DLP-Lösungen (Data Loss Prevention, Verhinderung von Datenverlust), e-Mail-Routing Regeln, Journal Funktionen, eDiscovery, Archivierungslösungen und Exchange ActiveSyn

Benutzer werden möglicherweise nicht verstehen, warum einige Geräte keine Hyok-geschützten e-Mails öffnen können. Dies führt zu weiteren aufrufen Ihres Helpdesks. Beachten Sie diese strengen Einschränkungen beim Konfigurieren des Hyok-Schutzes mit e-Mails.

## <a name="supported-applications-for-hyok"></a>Unterstützte Anwendungen für Hyok

Verwenden Sie Azure Information Protection Bezeichnungen, um Hyok auf bestimmte Dokumente und e-Mails anzuwenden. Hyok wird für Office-Versionen 2013 und höher unterstützt.

Hyok ist eine Administrator Konfigurationsoption für Bezeichnungen, und Workflows bleiben unverändert, unabhängig davon, ob der Inhalt als cloudbasierter Schlüssel oder Hyok verwendet wird.

In den folgenden Tabellen sind die unterstützten Szenarien für den Schutz und die Verwendung von Inhalten mit Hyok-konfigurierten Bezeichnungen aufgeführt:

- [Windows-Anwendungsunterstützung für Hyok](#windows-application-support-for-hyok)
- [Unterstützung von macOS-Anwendungen für Hyok](#macos-application-support-for-hyok)
- [IOS-Anwendungsunterstützung für Hyok](#ios-application-support-for-hyok)
- [Android-Anwendungsunterstützung für Hyok](#android-application-support-for-hyok)

> [!NOTE]
> Office Web-und universelle Anwendungen werden für Hyok nicht unterstützt.

### <a name="windows-application-support-for-hyok"></a>Windows-Anwendungsunterstützung für Hyok

|Application  |Schutz  |Nutzung  |
|---------|---------|---------|
|Azure Information Protection Clients mit Microsoft 365 apps, Office 2019, Office 2016 und Office 2013:</br>Word, Excel, PowerPoint, Outlook     | ![ja](media/yes-icon.png)        | ![ja](media/yes-icon.png)        |
|Azure Information Protection-Client mit Datei-Explorer     | ![ja](media/yes-icon.png)        | ![ja](media/yes-icon.png) |
|Azure Information Protection-Viewer     |   Nicht zutreffend      |  ![ja](media/yes-icon.png)       |
|Azure Information Protection-Client PowerShell-Cmdlets für die Bezeichnung     | ![ja](media/yes-icon.png)        | ![ja](media/yes-icon.png)        |
|Azure Information Protection-Überprüfung     |![ja](media/yes-icon.png)       |   ![ja](media/yes-icon.png)      |
| | | |

### <a name="macos-application-support-for-hyok"></a>Unterstützung von macOS-Anwendungen für Hyok

|Application|Schutz|Nutzung|
|----------------------|----------|-----------|
|Office für Mac: </br>Word, Excel, PowerPoint, Outlook|![nein](media/no-icon.png)|![ja](media/yes-icon.png)|
| | | |

### <a name="ios-application-support-for-hyok"></a>IOS-Anwendungsunterstützung für Hyok

|Application|Schutz|Nutzung|
|----------------------|----------|-----------|
|Office Mobile: </br>Word, Excel, PowerPoint|![nein](media/no-icon.png)| ![ja](media/yes-icon.png)|
|Office Mobile: </br>Nur Outlook|![nein](media/no-icon.png)|![nein](media/no-icon.png)|
|Azure Information Protection-Viewer|Nicht zutreffend|![ja](media/yes-icon.png)|

### <a name="android-application-support-for-hyok"></a>Android-Anwendungsunterstützung für Hyok

|Application|Schutz|Nutzung|
|----------------------|----------|-----------|
|Office Mobile: </br>Word, Excel, PowerPoint|![nein](media/no-icon.png)| ![ja](media/yes-icon.png)|
|Office Mobile: </br>Nur Outlook|![nein](media/no-icon.png)|![nein](media/no-icon.png)|
|Azure Information Protection-Viewer|Nicht zutreffend| ![ja](media/yes-icon.png)|


## <a name="implementing-hyok"></a>Implementieren von HYOK

Azure Information Protection unterstützt Hyok, wenn Sie über eine Active Directory Rights Management Services (AD RMS) verfügen, die allen [unten aufgeführten Anforderungen](#requirements-for-ad-rms-to-support-hyok)entspricht.

Die Richtlinien für Nutzungsrechte und der private Schlüssel der Organisation, die diese Richtlinien schützen, werden lokal verwaltet und aufbewahrt, während die Azure Information Protection-Richtlinie für die Bezeichnung und Klassifizierung weiterhin verwaltet und in Azure gespeichert wird.

So implementieren Sie den Hyok-Schutz:

1. [Stellen Sie sicher, dass Ihr System die AD RMS Anforderungen erfüllt.](#requirements-for-ad-rms-to-support-hyok)
1. [Suchen Sie die Informationen, die Sie schützen möchten.](#locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label)

Wenn Sie bereit sind, fahren Sie mit dem [Konfigurieren einer Bezeichnung für Rights Management Schutz](configure-policy-protection.md)fort.

### <a name="requirements-for-ad-rms-to-support-hyok"></a>Anforderungen für die Unterstützung für HYOK von AD RMS

Eine AD RMS Bereitstellung muss die folgenden Anforderungen erfüllen, um den Hyok-Schutz für Azure Information Protection Bezeichnungen zu gewährleisten:

|Anforderung  |BESCHREIBUNG  |
|---------|---------|
|**AD RMS Konfiguration**     |Das AD RMS System muss auf spezielle Weise konfiguriert werden, um Hyok zu unterstützen. Weitere Informationen finden Sie weiter [unten](#ad-rms-configuration-requirements).          |
|**Verzeichnissynchronisierung**     |Die Verzeichnis Synchronisierung muss zwischen dem lokalen Active Directory und dem Azure Active Directory konfiguriert werden. </br></br>Benutzer, die Hyok-Schutz Bezeichnungen verwenden, müssen für einmaliges Anmelden konfiguriert werden.         |
|**Konfiguration für explizit definierte Vertrauens Stellungen**     |Wenn Sie Hyok-geschützte Inhalte für andere Personen außerhalb Ihrer Organisation freigeben, müssen AD RMS für explizit definierte Vertrauens Stellungen in einer direkten Punkt-zu-Punkt-Beziehung mit den anderen Organisationen konfiguriert werden. </br></br>Verwenden Sie hierfür vertrauenswürdige Benutzer Domänen (Trusted User Domains, TUDs) oder Verbund Vertrauensstellungen, die mit Active Directory-Verbunddienste (AD FS) (AD FS) erstellt werden.         |
|**Unterstützte Version Microsoft Office**     | Benutzer, die Hyok-geschützte Inhalte schützen oder nutzen, müssen über Folgendes verfügen: </br></br>-Eine Version von Office, die Information Rights Management (unm) unterstützt </br>-Microsoft Office Professional Plus Version 2013 oder höher mit Service Pack 1, die unter Windows 7 Service Pack 1 oder höher ausgeführt wird. </br>-Für die Microsoft Installer (MSI)-basierte Edition von Office 2016 müssen Sie [über das Update 4018295 für Microsoft Office 2016 verfügen, das am 6. März 2018 veröffentlicht wurde](https://support.microsoft.com/help/4018295/march-6-2018-update-for-office-2016-kb4018295). </br></br>**Hinweis**: Office 2010 und Office 2007 werden nicht unterstützt.  Weitere Informationen finden Sie unter [AIP und ältere Windows-und Office-Versionen](known-issues.md#aip-and-legacy-windows-and-office-versions).      |

> [!IMPORTANT]
> Um die hohe Sicherheit zu erfüllen, die Hyok-Schutz bietet, empfehlen wir Folgendes:
> - Suchen Ihrer AD RMS Server außerhalb ihrer DMZ und sicherstellen, dass Sie nur von verwalteten Geräten verwendet werden.
>
> - Konfigurieren Sie den AD RMS Cluster mit einem Hardware Sicherheitsmodul (HSM). Dadurch wird sichergestellt, dass der private Schlüssel des Server Licensor Certificate (SLC) nicht verfügbar gemacht oder gestohlen werden kann, wenn Ihre AD RMS Bereitstellung jemals verletzt oder kompromittiert werden soll.

> [!TIP]
> Weitere Informationen zur Bereitstellung sowie Anweisungen für AD RMS finden Sie unter [Active Directory Rights Management Services](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831364(v=ws.11)) in der Windows Server-Bibliothek. 

#### <a name="ad-rms-configuration-requirements"></a>AD RMS Konfigurations Anforderungen

Um Hyok zu unterstützen, stellen Sie sicher, dass das AD RMS System über die folgenden Konfigurationen verfügt:

|Anforderung  |BESCHREIBUNG  |
|---------|---------|
|**Windows-Version**     |Mindestens eine der folgenden Windows-Versionen: </br></br>**Produktionsumgebungen**: Windows Server 2012 R2</br>**Test-/Auswertungs Umgebungen**: Windows Server 2008 R2 mit Service Pack 1        |
|**Topologie**     |Hyok erfordert eine der folgenden Topologien: </br>-Eine einzelne Gesamtstruktur mit einem einzelnen AD RMS Cluster </br>: Mehrere Gesamtstrukturen mit AD RMS Cluster. </br></br>**Lizenzierung für mehrere Gesamtstrukturen**</br> Wenn Sie über mehrere Gesamtstrukturen verfügen, gibt jeder AD RMS Cluster eine Lizenzierungs-URL frei, die auf denselben AD RMS Cluster zeigt. </br>Importieren Sie auf diesem AD RMS Cluster alle Zertifikate der vertrauenswürdigen Benutzer Domäne (TUD) aus allen anderen AD RMS Clustern. </br>Weitere Informationen zu dieser Topologie finden Sie unter [Trusted User Domain (Vertrauenswürdige Benutzerdomäne)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd983944(v=ws.10)). </br></br>**Globale Richtlinien Bezeichnungen für mehrere Gesamtstrukturen**</br>Wenn Sie über mehrere AD RMS-Cluster in separaten Gesamtstrukturen verfügen, löschen Sie Bezeichnungen in der globalen Richtlinie, die HYOK-Schutz (AD RMS) anwenden, und konfigurieren Sie eine [bereichsbezogene Richtlinie](configure-policy-scope.md) für jeden Cluster. <br>Weisen Sie die Benutzer für jeden Cluster ihrer Bereichs bezogenen Richtlinie zu, und stellen Sie sicher, dass Sie keine Gruppen verwenden, die dazu führen würden, dass ein Benutzer mehr als einer Bereichs bezogenen Richtlinie zugewiesen wird.</br>Jeder Benutzer sollte letztendlich Bezeichnungen für nur einen AD RMS-Cluster besitzen.          |
|**Kryptografiemodus**     | Ihr AD RMS muss mit dem [Kryptografiemodus 2](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10))konfiguriert werden. </br>Bestätigen Sie den Modus, indem Sie auf der Registerkarte **Allgemein** auf der Registerkarte Eigenschaften des AD RMS        |
|**Konfiguration der Zertifizierungs-URL**     | Jeder AD RMS Server muss für die Zertifizierungs-URL konfiguriert werden. </br>Weitere Informationen finden Sie weiter [unten](#configuring-ad-rms-servers-to-locate-the-certification-url).        |
|**Dienst Verbindungspunkte**     | Ein Dienst Verbindungspunkt (Service Connection Point, SCP) wird nicht verwendet, wenn Sie AD RMS Schutz mit Azure Information Protection verwenden. </br></br>**Wenn Sie einen SCP für Ihre AD RMS-Bereitstellung registriert haben**, entfernen Sie ihn, um sicherzustellen, dass die [Dienst](./rms-client/client-deployment-notes.md#rms-service-discovery) Ermittlung für den Azure-Rights Management Schutz erfolgreich war. </br></br>**Wenn Sie einen neuen AD RMS Cluster für Hyok installieren**, registrieren Sie den SCP beim Konfigurieren des ersten Knotens nicht. Stellen Sie für jeden weiteren Knoten sicher, dass der Server für die Zertifizierungs-URL konfiguriert ist, bevor Sie die AD RMS-Rolle hinzufügen und dem vorhandenen Cluster beitreten.         |
|**SSL/TLS**     |In Produktionsumgebungen müssen die AD RMS Server für die Verwendung von SSL/TLS mit einem gültigen x. 509-Zertifikat konfiguriert werden, das von den verbundenen Clients als vertrauenswürdig eingestuft wird. </br></br>Dies ist für Test-oder Evaluierungs Zwecke nicht erforderlich.         |
|**Rechte Vorlagen**     |Sie müssen Rechte Vorlagen für Ihre AD RMS konfiguriert haben.         |
|**Exchange-irren**    |Ihr AD RMS kann nicht für Exchange-irren konfiguriert werden.         |
|**Mobile Geräte/Macintosh-Computer**     | Die [Active Directory Rights Management Services Mobile-Geräte Erweiterung](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574(v=ws.11)) muss installiert und konfiguriert sein.        |


#### <a name="configuring-ad-rms-servers-to-locate-the-certification-url"></a>Konfigurieren von AD RMS-Servern zum Finden der Zertifizierungs-URL

1. Erstellen Sie auf jedem AD RMS-Server im Cluster den folgenden Registrierungseintrag:

    ```sh
    Computer\HKEY_LOCAL_MACHINE\Software\Microsoft\DRMS\GICURL = "<string>"`
    ```

    Geben Sie für das \<string value> eine der folgenden Zeichen folgen an:

    |Umgebung  |Zeichenfolgenwert  |
    |---------|---------|
    |**Produktion** </br>(AD RMS Cluster mit SSL/TLS)     | `https://<cluster_name>/_wmcs/certification/certification.asmx`        |
    |**Testen/evaluieren** </br>(kein SSL/TLS)     |`http://<cluster_name>/_wmcs/certification/certification.asmx`         |

2. Starten Sie IIS neu.

### <a name="locating-the-information-to-specify-ad-rms-protection-with-an-azure-information-protection-label"></a>Suchen von Informationen zum Angeben des AD RMS-Schutzes mit einer Azure Information Protection-Bezeichnung

Zum Konfigurieren von Hyok-Schutz Bezeichnungen müssen Sie die Lizenzierungs-URL Ihres AD RMS Clusters angeben. 

Außerdem müssen Sie entweder eine Vorlage angeben, die Sie mit den Berechtigungen konfiguriert haben, die Sie Benutzern zuweisen möchten, oder Sie können Benutzern ermöglichen, Berechtigungen und Benutzer zu definieren. 

Gehen Sie folgendermaßen vor, um die Vorlagen-GUID und die Lizenzierungs-URL-Werte in der Active Directory Rights Management Services-Konsole

#### <a name="locate-a-template-guid"></a>Suchen einer Vorlagen-GUID

1. Erweitern Sie den Cluster, und klicken Sie auf **Vorlagen für Benutzerrechterichtlinien**. 

1. Kopieren Sie aus den **Vorlagen für verteilte Rechte Richtlinien Vorlagen** die GUID aus der Vorlage, die Sie verwenden möchten. 

Beispiel: **82bf 3474-6efe-4fa1-8827-d1bd93339119** 

#### <a name="locate-the-licensing-url"></a>Lizenzierungs-URL suchen

1. Klicken Sie auf den Clusternamen.
 
1. Kopieren Sie aus der Information **Clusterdetails** den Wert **Lizenzierung** minus der Zeichenfolge **/_wmcs/licensing**. 

Beispiel: **https://rmscluster.contoso.com** 
    
> [!NOTE]
> Wenn Sie über verschiedene Extranet-und intranetlizenzierungs Werte verfügen, geben Sie den extranetwert nur an, wenn Sie geschützte Inhalte für Partner freigeben möchten. Partner, die geschützte Inhalte freigeben, müssen mit expliziten Punkt-zu-Punkt-Vertrauens Stellungen definiert werden. 
> 
> Wenn Sie geschützte Inhalte nicht freigeben, verwenden Sie den intranetwert, und stellen Sie sicher, dass alle Client Computer, die AD RMS-Schutz mit Azure Information Protection verwenden, eine Verbindung über eine Intranetverbindung herstellen. Beispielsweise müssen Remote Computer eine VPN-Verbindung verwenden.
> 

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie das System für die Unterstützung von Hyok konfiguriert haben, fahren Sie mit dem Konfigurieren von Bezeichnungen für den Hyok-Schutz fort. Weitere Informationen finden Sie unter [Konfigurieren einer Bezeichnung für den Rights Management-Schutz](configure-policy-protection.md).