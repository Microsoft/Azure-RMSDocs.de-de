---
title: Der Client für Azure Information Protection-aip
description: Microsoft Azure Information Protection stellt eine Client/Server-Lösung zum Schutz der Daten einer Organisation bereit. Der Client (Azure Information Protection-Client oder Rights Management-Client) ist in Anwendungen integriert, die auf Computern und mobilen Geräten ausgeführt werden.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/20/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.suite: ems
ms.custom: admin
search.appverid:
- MET150
ms.openlocfilehash: fcd21a58dabe65f1de88694f97dc57975bc19450
ms.sourcegitcommit: ee20112ada09165b185d9c0c9e7f1179fc39e7cf
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/21/2021
ms.locfileid: "98659067"
---
# <a name="the-client-side-of-azure-information-protection"></a>Die Clientseite von Azure Information Protection

>***Gilt für**: Active Directory Rights Management Services, [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection),[Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows 10, Windows 8.1, Windows 8, Windows Server 2019, Windows Server 2016, Windows Server 2012 R2, Windows Server 2012 *
>
>*Wenn Sie über Windows 7 oder Office 2010 verfügen, finden Sie weitere Informationen unter [AIP und ältere Windows-und Office-Versionen](../known-issues.md#aip-and-legacy-windows-and-office-versions).*
>
>***Relevant für:** [AIP-Client für einheitliche Bezeichnungen und den klassischen Client](../faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients)*

>[!NOTE] 
> Der **klassische Azure Information Protection-Client** und die **Bezeichnungsverwaltung** im Azure-Portal werden am **31. März 2021** **eingestellt**, um eine vereinheitlichte und optimierte Kundenumgebung zu gewährleisten. Dieser Zeitrahmen ermöglicht allen aktuellen Azure Information Protection-Kunden den Umstieg auf die Microsoft Information Protection-Plattform für einheitliche Bezeichnungen. Weitere Informationen erhalten Sie im offiziellen [Hinweis zu veralteten Funktionen](https://aka.ms/aipclassicsunset).


Der Azure Information Protection Unified-Bezeichnungs Client stellt eine Client/Server-Lösung bereit, die den Schutz der Dokumente und e-Mails einer Organisation unterstützt, und stellt eine Alternative zur [integrierten Bezeichnungs Lösung für Microsoft Office](/microsoft-365/compliance/sensitivity-labels)dar. 

Neben der direkten Integration in Office-Anwendungen bietet der Unified-Bezeichnung-Client Unterstützung für den Datei-Explorer und PowerShell, sodass Sie Dateien außerhalb von Office klassifizieren und schützen können. Zu den zusätzlichen Komponenten gehören ein Viewer für geschützte PDF-Dateien und Images sowie ein Scanner für lokale Datenspeicher.

Der Unified-Bezeichnung-Client muss separat in Office-Apps installiert werden.

Der Dienst befindet sich in der Cloud oder lokal:

- Der clouddienst ist **Azure Information Protection** und verwendet den Azure Rights Management-Dienst für den Schutz von Daten.
- Der lokale Dienst wird **Active Directory Rights Management Services** (AD RMS).

## <a name="choose-your-windows-labeling-solution"></a>Auswählen Ihrer Windows-Lösung für Bezeichnungen

Bezeichnungen erleichtern Ihren Benutzern die Anwendung von Schutz und sorgen auch für die Klassifizierung, sodass Sie Ihre Daten nachverfolgen und verwalten können. 

Beachten Sie bei der Auswahl einer Windows-beschriftungslösung die folgenden grundlegenden Unterschiede:

- **Wo Bezeichnungen und Bezeichnungs Richtlinien heruntergeladen werden** 

    Die integrierte Bezeichnungs Lösung und der AIP Unified-Bezeichnung-Client verwenden eines der folgenden Admin Center: 
    
    - Office 365 Security & Compliance Center 
    - Microsoft 365 Security Center 
    - Microsoft 365 Compliance Center
      
    Wenn Sie den klassischen AIP-Client verwenden, werden die Bezeichnungen und die Beschriftungs Richtlinien im Azure-Portal heruntergeladen und verwaltet. 

- **Installationsanforderungen**

    Die integrierte Bezeichnungs Lösung erfordert keine separate Installation.

    Der AIP Unified-Bezeichnungs Client und der klassische Legacy Client benötigen jeweils eine separate Installation für Office. Laden Sie den Unified Bezeichnung-Client aus dem [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=53018)herunter, und installieren Sie ihn.  

    Wenn Sie den klassischen Legacy Client herunterladen und installieren müssen, wenden Sie sich an den Support, und öffnen Sie ein Ticket für den Zugriff auf die Installationsdatei. 

Anhand der folgenden Abschnitte können Sie bestimmen, welcher Client für Ihre Organisation am besten geeignet ist:

- [Integrierte Office-beschriftungslösung](#built-in-office-labeling-solution)
- [Azure Information Protection-Client für einheitliche Bezeichnungen](#azure-information-protection-unified-labeling-client)
- [Klassischer Azure Information Protection-Client](#azure-information-protection-classic-client)
- [Verwenden mehrerer Clients in derselben Umgebung](#using-multiple-clients-in-the-same-environment)

Weitere Informationen finden Sie unter: [ausführliche Vergleiche der AIP-Clients](#detailed-comparisons-for-the-azure-information-protection-clients) und [Features, die für den Unified-Bezeichnungs Client nicht geplant](#features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client)sind.

> [!NOTE]
> Mit der neuesten Version des Unified-Bezeichnungs Clients wird die Parität der Features mit dem klassischen Client geschlossen. Wenn diese Lücke geschlossen wird, können Sie davon ausgehen, dass neue Features nur dem Unified-Beschriftungs Client hinzugefügt werden. 
>
> Es wird empfohlen, dass Sie den Unified-Bezeichnungs Client bereitstellen, wenn der aktuelle Funktionsumfang und seine Funktionalität ihren Geschäftsanforderungen entsprechen.
> 

### <a name="built-in-office-labeling-solution"></a>Integrierte Office-beschriftungslösung

Die in Microsoft Office integrierte Bezeichnungs Lösung:

- Erfordert einen Windows-Computer mit Microsoft 365 Anwendungen, mindestens Version 1910
- Ermöglicht das Freigeben von Bezeichnungen und Richtlinien Einstellungen, die auch von macOS, IOS und Android verwendet werden können.
- Unterstützt Wechsel Konten
- Bietet eine bessere Leistung in Office-Anwendungen
- Erfordert keine separate Installation und Wartung
- Kann nicht deaktiviert werden.

**Verwenden** Sie den integrierten Office-Beschriftungs Client nicht, wenn Sie nur die Azure Information Protection Clients bereitgestellt haben, z. b. die Information Protection Leiste im Menüband. Diese Leiste ermöglicht die Auswahl und Sichtbarkeit von Bezeichnungen.

### <a name="azure-information-protection-unified-labeling-client"></a>Azure Information Protection-Client für einheitliche Bezeichnungen

Der Unified Label-Client erfordert einen Windows-Computer und ermöglicht das Freigeben von Bezeichnungen und Richtlinien Einstellungen, die auch von macOS, IOS und Android verwendet werden können.

**Verwenden** Sie den Unified Label-Client nicht, wenn Sie Bezeichnungen in der Azure-Portal konfiguriert haben, die Sie noch nicht [zum vereinheitlichten Bezeichnungs Speicher migriert](../configure-policy-migrate-labels.md)haben.

### <a name="azure-information-protection-classic-client"></a>Klassischer Azure Information Protection-Client

Der klassische Client ist der AIP-Legacy Client, unterstützt ähnliche Features wie der Unified-Bezeichnungs Client und muss auch separat für Office-Apps installiert werden. 

Der klassische Client wird [im März 2021](https://aka.ms/aipclassicsunset)eingestellt.

Verwenden Sie den klassischen Client nur, wenn Sie noch nicht zu Unified-Bezeichnung migriert haben. Weitere Informationen finden Sie unter [Tutorial: Migrieren vom klassischen Azure Information Protection-Client (AIP) zum Client für einheitliche Bezeichnungen](../tutorial-migrating-to-ul.md).

Der klassische Client hat unterschiedliche Richtlinien Einstellungen für macOS, IOS und Android. Obwohl Sie möglicherweise die zusätzlichen Features verwenden möchten, müssen Sie mit einem separaten Verwaltungs Portal und Benutzeroberflächen arbeiten, um Inhalte über Betriebssysteme hinweg zu schützen.

Wir empfehlen, nach Möglichkeit den Unified-Bezeichnungs Client anstelle des klassischen Clients zu verwenden.

### <a name="using-multiple-clients-in-the-same-environment"></a>Verwenden mehrerer Clients in derselben Umgebung

Sie können verschiedene Clients in derselben Umgebung verwenden, um unterschiedliche Geschäftsanforderungen zu unterstützen, wie im folgenden Beispiel für die Bereitstellung veranschaulicht. In einer gemischten Client Umgebung empfiehlt es sich, einheitliche Bezeichnungen zu verwenden, damit Clients denselben Satz von Bezeichnungen für die einfache Verwaltung verwenden. Neue Kunden haben standardmäßig einheitliche Bezeichnungen, da sich Ihre Mandanten auf der vereinheitlichten Beschriftungs Plattform befinden. Weitere Informationen finden Sie unter [wie kann ich feststellen, ob mein Mandant auf der Unified-Beschriftungs Plattform ist?](../faqs.md#how-can-i-determine-if-my-tenant-is-on-the-unified-labeling-platform)

Wenn Sie über einen Windows-Computer verfügen, auf dem Microsoft 365-apps ausgeführt wird, die mindestens Version 1910 und einer der Azure Information Protection Clients installiert sind, ist die integrierte Bezeichnungs Lösung in Office-Apps standardmäßig deaktiviert. Sie können dieses Verhalten jedoch ändern, um die integrierte Bezeichnungs Lösung nur für Ihre Office-Apps zu verwenden. Mit dieser Konfiguration ist der Azure Information Protection Client für die Bezeichnung im Datei-Explorer, in PowerShell und im Scanner verfügbar. Anweisungen zum Deaktivieren des Azure Information Protection Clients in Microsoft 365-apps finden Sie im Abschnitt [integrierte Bezeichnungs Lösung für Office und der Azure Information Protection-Client](/microsoft-365/compliance/sensitivity-labels-office-apps#office-built-in-labeling-client-and-the-azure-information-protection-client) aus der Dokumentation zur Microsoft 365 Konformität.

##### <a name="sample-deployment-strategy"></a>Beispiel Bereitstellungs Strategie

- Für die Mehrheit der Benutzer stellen Sie den Azure Information Protection Unified-Bezeichnungs Client bereit, da dieser Client die geschäftlichen Anforderungen für diese Benutzer erfüllt. 
    
    Für diese Benutzer ist Ihre Bezeichnung in Windows, Mac, IOS und Android ähnlich, da Ihnen dieselben Bezeichnungen und die gleichen Richtlinien Einstellungen zur Verfügung stehen. Als Administrator verwalten Sie diese Bezeichnungen und Richtlinien Einstellungen im selben Verwaltungs Center.

- Außerdem installieren Sie den Unified-Bezeichnung-Client für sich selbst, um den Azure Information Protection Scanner zu testen.

- Für eine Teilmenge der Benutzer stellen Sie den klassischen Client bereit, da diese Benutzer Bezeichnungen benötigen, die den[Hyok](../configure-adrms-restrictions.md)-Schutz (Hold Your Own Key) anwenden.
    
    Diese Benutzer haben bei der Verwendung dieses Clients eine etwas andere Bezeichnung. Beispielsweise wird eine Schaltfläche **schützen** anstelle einer **Vertraulichkeits** Schaltfläche in Office-Apps angezeigt. Als Administrator müssen Sie Ihre Bezeichnungen für Hyok-Einstellungen und Richtlinien Einstellungen in einem anderen Verwaltungs Center mit den Bezeichnungen und Einstellungen für die anderen Client Plattformen verwalten.

- Sie verfügen über lokale Datenspeicher mit Dokumenten, die auf sensible Informationen überprüft oder klassifiziert und geschützt werden müssen. Zur Verwendung in der Produktion stellen Sie den Unified-Bezeichnung-Client auf Servern bereit, um den [Azure Information Protection Scanner](../deploy-aip-scanner.md)auszuführen.

#### <a name="rights-management-client"></a>Rights Management-Client

Der RMS-Client bietet nur Schutz und wird automatisch mit einigen Anwendungen installiert, einschließlich Office-Anwendungen, der Unified-Bezeichnung von AIP und klassischen Clients sowie RMS-fähigen Anwendungen von anderen Softwareanbietern. 

Sie können [den RMS-Client auch selbst installieren](https://www.microsoft.com/download/details.aspx?id=38396), um die [Synchronisierung von Dateien aus mit unm geschützten Bibliotheken und onedrive](/onedrive/deploy-on-windows)zu unterstützen, sowie für Entwickler, die den Rights Management-Schutz in Branchen Anwendungen integrieren möchten.

## <a name="compare-the-labeling-solutions-for-windows-computers"></a>Vergleichen der Bezeichnungslösungen für Windows-Computer

Verwenden Sie die folgende Tabelle, um zu vergleichen, welche Funktionen von den drei Bezeichnungs Lösungen für Windows-Computer unterstützt werden.

In der Dokumentation zur Microsoft 365 Konformität finden Sie Informationen zu den Funktionen [zur Vertraulichkeits Bezeichnung in-apps](/microsoft-365/compliance/sensitivity-labels-office-apps#support-for-sensitivity-label-capabilities-in-apps), um die integrierten Funktionen für die Vertraulichkeits Bezeichnung von Office auf verschiedenen Betriebssystemplattformen (Windows, macOS, IOS und Android) und für das Web zu vergleichen. Diese Dokumentation enthält auch die Office-Buildnummern oder Informationen zum Office-Update Kanal für die unterstützten Funktionen.

Weitere Informationen finden Sie auch unter:
- [Ausführliche Vergleiche der Azure Information Protection Clients](#detailed-comparisons-for-the-azure-information-protection-clients)
- [Features, die im Azure Information Protection Unified-Bezeichnungs Client nicht geplant sind](#features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client)

|Funktion|Klassischer Client|Einheitlicher Bezeichnungs Client|Integrierte Office-beschriftungslösung|
|:------|:------------:|:---------------------:|:-----------------------------:|
|**Manuelle Bezeichnung**| ![ja](../media/yes-icon.png)   | ![ja](../media/yes-icon.png)   |![ja](../media/yes-icon.png) |
|**Standard Bezeichnung**| ![ja](../media/yes-icon.png)| ![ja](../media/yes-icon.png)| ![ja](../media/yes-icon.png)|
|**Empfohlene oder automatische Bezeichnung** <br />Für Word, Excel, PowerPoint, Outlook|![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |
|**Obligatorische Bezeichnung**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|
|**Benutzerdefinierte Berechtigungen für eine Bezeichnung**: <br />Nicht weiterleiten für e-Mails| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |
|**Benutzerdefinierte Berechtigungen für eine Bezeichnung**: <br />Benutzerdefinierte Berechtigungen für Word, Excel, PowerPoint| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |
|**Unterstützung mehrerer Sprachen für Bezeichnungen**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |![ja](../media/yes-icon.png) |
|**Vererbung von e-Mail-Anhängen**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png)  | ![nein](../media/no-icon.png)|
|**Anpassungen, die Folgendes umfassen**:<br />– Standardbezeichnung für E-Mails<br />: Popup Meldungen in Outlook <br />– S/MIME-Unterstützung<br />– Option zum Melden eines Problems| ![Ja ](../media/yes-icon.png) <sup>1</sup> | ![Ja ](../media/yes-icon.png) <sup>2</sup> |  ![nein](../media/no-icon.png)|
|**Scanner für lokale Datenspeicher**| ![ja](../media/yes-icon.png) |  ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|
|**Zentrale Berichterstellung (Analytics)**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|
|**Benutzerdefinierte Berechtigungen, die unabhängig von einer Bezeichnung festgelegt wurden**| ![ja](../media/yes-icon.png) | ![Ja ](../media/yes-icon.png) <sup>3</sup>|  ![nein](../media/no-icon.png)|
|**Information Protection Leiste in Office-Apps**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png)|  ![nein](../media/no-icon.png)|
|**Visuelle Kennzeichnungen als Bezeichnungs Aktion**<br> (Kopfzeile, Fußzeile, Wasserzeichen)| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png)|
|**Visuelle Kennzeichnungen pro App**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![Ja ](../media/yes-icon.png) <sup>9</sup>|
|**Dynamische visuelle Kennzeichnungen mit Variablen**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![Ja ](../media/yes-icon.png) <sup>9</sup>|
|**Externe Inhalts Markierung in App entfernen**| ![ja](../media/yes-icon.png)| ![ja](../media/yes-icon.png)| ![nein](../media/no-icon.png)|
|**Bezeichnung mit dem Datei-Explorer**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|
|**Ein Viewer für geschützte Dateien** <br> (Text, Bilder, PDF, Pfile-Datei)| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![nein](../media/no-icon.png)|
|**Ppdf-Unterstützung für das Anwenden von Bezeichnungen**| ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|  ![nein](../media/no-icon.png)|
|**Cmdlets für die PowerShell-Bezeichnung**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png)  |  ![nein](../media/no-icon.png)|
|**Offline Unterstützung für Schutz Aktionen**| ![ja](../media/yes-icon.png) | ![Ja ](../media/yes-icon.png) <sup>4</sup> | ![ja](../media/yes-icon.png) |
|**Manuelle Richtlinien Dateiverwaltung für nicht verbundene Computer**| ![ja](../media/yes-icon.png) |![ja](../media/yes-icon.png)|  ![nein](../media/no-icon.png)|
|**Hyok-Unterstützung**| ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|  ![nein](../media/no-icon.png)|
|**Verwendungs Protokollierung in Ereignisanzeige**| ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)| ![nein](../media/no-icon.png)|
|**Schaltfläche „Nicht weiterleiten“ in Outlook anzeigen**| ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|  ![nein](../media/no-icon.png)|
|**Geschützte Dokumente nachverfolgen**| ![Ja ](../media/yes-icon.png) <sup>5</sup> | ![Ja ](../media/yes-icon.png) <sup>5</sup> |  ![nein](../media/no-icon.png)|
|**Geschützte Dokumente widerrufen**| ![Ja ](../media/yes-icon.png) <sup>5</sup> |  ![Ja ](../media/yes-icon.png) <sup>5</sup>|  ![nein](../media/no-icon.png)|
|**Nur Schutzmodus** (keine Bezeichnungen)| ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|  ![nein](../media/no-icon.png)|
|**Unterstützung für Kontowechsel**|  ![nein](../media/no-icon.png)|  ![nein](../media/no-icon.png)| ![ja](../media/yes-icon.png) |
|**Unterstützung für Remotedesktopdienste**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |
|**Unterstützung für AD RMS**| ![ja](../media/yes-icon.png) |  ![Nein ](../media/no-icon.png) <sup>6</sup> |  ![nein](../media/no-icon.png)|
|**Unterstützung für Microsoft Office 97-2003-Formate**| ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) |  ![Nein ](../media/no-icon.png) <sup>8</sup>|
|**Doppelte Schlüssel Verschlüsselung**|  ![nein](../media/no-icon.png)| ![ja](../media/yes-icon.png) |  ![nein](../media/no-icon.png)|
|**Government-Community-Cloud** | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png) | ![ja](../media/yes-icon.png)|
| | | | |

**Fußnoten**:

<sup>1</sup> diese Einstellungen und viele weitere werden als [Erweiterte Client Einstellungen unterstützt, die Sie im Azure-Portal konfigurieren](client-admin-guide-customizations.md#how-to-configure-advanced-classic-client-configuration-settings-in-the-portal).

<sup>2</sup> diese Einstellungen und viele weitere werden als erweiterte Einstellungen unterstützt, [die Sie mit PowerShell konfigurieren](clientv2-admin-guide-customizations.md#configuring-advanced-settings-for-the-client-via-powershell).

<sup>3</sup> wird vom Datei-Explorer und PowerShell unterstützt. In Office-Apps können Benutzer **Dateiinformationen**  >  **Schutz Dokument**  >  **einschränken Zugriff** auswählen.

<sup>4</sup> für den Datei-Explorer und PowerShell-Befehlen muss der Benutzer mit dem Internet verbunden sein, um Dateien zu schützen.

<sup>5</sup> Weitere Informationen finden Sie unter: **Unified Bezeichnung Client**: [Admin Guide (Public Preview)](track-and-revoke-admin.md)  |   [User Guide (Public Preview)](revoke-access-user.md). Die Nachverfolgung wird nur für globale Administratoren unterstützt. **Klassischer Client**: [](client-admin-guide-document-tracking.md)  |  [Benutzerhandbuch](client-track-revoke.md)zum Administrator Handbuch. Administratoren können mit der [zentralen Berichterstattung](../reports-aip.md) auch ermitteln, ob auf geschützte Dokumente von Windows-Computern zugegriffen wird und ob der Zugriff gewährt oder verweigert wurde.

<sup>6</sup> Bezeichnungs-und Schutz Aktionen werden nicht unterstützt. Allerdings kann der Viewer bei einer AD RMS Bereitstellung geschützte Dokumente öffnen, wenn Sie die [Active Directory Rights Management Services-Erweiterung für mobile Geräte](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn673574\(v=ws.11\))verwenden.

<sup>8</sup> die AIP-Clients unterstützen sowohl Microsoft Office 97-2003-Dateiformate, wie z **. b. doc**, als auch Office Open XML-Formate, wie z **. b.. docx**, die integrierte Bezeichnung unterstützt jedoch nur Open XML-Formate.

<sup>9</sup> Weitere Informationen zur Unterstützung von dynamischen Inhalts Markierungen und App-Inhalts Markierungen für die integrierte Bezeichnungs Lösung finden Sie in der [Microsoft 365-Dokumentation](/microsoft-365/compliance/sensitivity-labels-office-apps#dynamic-markings-with-variables).

### <a name="detailed-comparisons-for-the-azure-information-protection-clients"></a>Ausführliche Vergleiche der Azure Information Protection Clients

Wenn die Azure Information Protection des klassischen Clients und der Azure Information Protection Unified-Bezeichnung-Client dieselbe Funktion unterstützen, verwenden Sie die folgenden Listen, um einige funktionale Unterschiede zwischen den beiden Clients zu identifizieren:


|Funktionalität |Klassischer Client|Einheitlicher Bezeichnungs Client|
|--------------|-----------------------------------|-----------------------------------------------------------|
|**Einrichtung**| Option zum Installieren der lokalen Demorichtlinie | Keine lokale Demorichtlinie|
|**Auswahl und Anzeige von Bezeichnungen in Office-Apps**|Über die Schaltfläche **Schützen** im Menüband <br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|Über die Schaltfläche **Vertraulichkeit** im Menüband<br /><br /> Über die Information Protection-Navigationsleiste (horizontale Leiste unter dem Menüband)|
|**Verwalten der Information Protection Leiste in Office-Apps**|**Für Benutzer**:<br />Option zum Anzeigen oder Ausblenden des Balkens auf der Schaltfläche " **schützen** " im Menüband<br /><br>Wenn ein Benutzer auswählt, den Balken auszublenden, wird die Leiste standardmäßig in dieser APP ausgeblendet, aber weiterhin automatisch in neu geöffneten apps angezeigt. <br /><br /> **Für Administratoren**: <br />Richtlinien Einstellungen zum automatischen anzeigen oder Ausblenden der Leiste, wenn eine APP zum ersten Mal geöffnet wird, und Steuern, ob die Leiste für neu geöffnete Apps automatisch ausgeblendet bleibt, nachdem ein Benutzer die Leiste ausgeblendet hat|**Für Benutzer**: <br />Option zum Anzeigen oder Ausblenden des Balkens auf der **Vertraulichkeits** Schaltfläche im Menüband. <br><br />Wenn ein Benutzer das Ausblenden der Leiste auswählt, wird die Leiste in der APP und auch in neu geöffneten apps ausgeblendet. <br /><br />**Für Administratoren**: <br />PowerShell-Einstellung zum Verwalten der Leiste |
|**Bezeichnungs Farbe**| Konfigurieren im Azure-Portal | Nach der Bezeichnungs Migration beibehalten und mit [PowerShell](clientv2-admin-guide-customizations.md#specify-a-color-for-the-label) konfigurierbar|
|**Bezeichnungen unterstützen unterschiedliche Sprachen**| Konfigurieren im Azure-Portal | Konfigurieren mithilfe von [Office 365 Security & Compliance PowerShell](/microsoft-365/compliance/create-sensitivity-labels#additional-label-settings-with-office-365-security--compliance-center-powershell)|
|**Richtlinien Aktualisierung**| -Wenn eine Office-App geöffnet wird <br /> : Wenn Sie mit der rechten Maustaste zum klassifizieren und schützen einer Datei oder eines Ordners klicken <br />: Wenn Sie die PowerShell-Cmdlets für die Bezeichnung und den Schutz ausführen<br />-Alle 24 Stunden <br />-Für den Scanner: stündlich und wenn der Dienst gestartet wird und die Richtlinie älter als eine Stunde ist| -Wenn eine Office-App geöffnet wird <br />: Wenn Sie mit der rechten Maustaste zum klassifizieren und schützen einer Datei oder eines Ordners klicken <br />: Wenn Sie die PowerShell-Cmdlets für die Bezeichnung und den Schutz ausführen<br />-Alle 4 Stunden <br />-Für den Scanner: alle 4 Stunden|
|**Unterstützte Formate für PDF**| **Schutz**: <br /> – ISO-Standard für die PDF-Verschlüsselung (Standardeinstellung) <br /> – PPDF <br /><br> **Verbrauch**: <br /> – ISO-Standard für die PDF-Verschlüsselung <br />– PPDF<br />– SharePoint-IRM-Schutz| **Schutz**: <br /> – ISO-Standard für die PDF-Verschlüsselung <br /> <br /> **Verbrauch**: <br /> – ISO-Standard für die PDF-Verschlüsselung <br />– PPDF<br />– SharePoint-IRM-Schutz|
|**Mit dem Viewer geöffnete generisch geschützte Dateien (Pfile)**| Die Datei wird in der ursprünglichen app geöffnet, in der Sie angezeigt, geändert und ohne Schutz gespeichert werden kann. | Die Datei wird in der ursprünglichen app geöffnet, in der Sie angezeigt und geändert, jedoch nicht gespeichert werden kann.|
|**Unterstützte Cmdlets**| -Cmdlets für die Bezeichnung <br> -Cmdlets für den reinen Schutz | **Cmdlets für die Bezeichnung**:<br /> " [Set-aipfileclassification](/powershell/module/azureinformationprotection/get-aipfileclassification) " und " [Set-aipfilelabel](/powershell/module/azureinformationprotection/get-aipfilelabel) " unterstützen den **Owner** -Parameter nicht. <br /> Darüber hinaus gibt es einen einzelnen Kommentar „Keine anzuwendende Bezeichnung“ für alle Szenarien, in denen keine Bezeichnung angewendet wird <br /><br /> " [Set-aipfileclassification](/powershell/module/azureinformationprotection/get-aipfileclassification) " unterstützt den Parameter " **WhatIf** ", damit er im Ermittlungs Modus ausgeführt werden kann. <br /><br /> " [Set-aipfilelabel](/powershell/module/azureinformationprotection/get-aipfilelabel) " unterstützt den Parameter " *enabletracking* " nicht. <br /><br /> [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) gibt keine Bezeichnungs Informationen von anderen Mandanten zurück und zeigt den **rmsissuedtime** -Parameter nicht an.<br />Außerdem zeigt der Parameter " **labelingmethod** " für " [Get-aipfilestatus](/powershell/module/azureinformationprotection/get-aipfilestatus) " den Wert " **privilegiert** " oder " **Standard**" anstelle von **manuell** oder **automatisch** an.|
|**Entsprechende Eingabe Aufforderungen (sofern konfiguriert) pro Aktion in Office** | -Frequency: pro Datei <br /> -Verringern der Empfindlichkeitsstufe <br /> -Entfernen einer Bezeichnung<br /> -Schutz wird entfernt | -Frequency: pro Sitzung <br /> -Verringern der Empfindlichkeitsstufe<br />-Entfernen einer Bezeichnung|
|**Angewendete Bezeichnungs Aktionen entfernen** | Benutzer wird zur Bestätigung aufgefordert <br /><br />Die Standard Bezeichnung oder eine automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App nicht automatisch angewendet.  | Der Benutzer wird nicht zur Bestätigung aufgefordert.<br /><br /> Die Standard Bezeichnung oder eine automatische Bezeichnung (sofern konfiguriert) wird beim nächsten Öffnen der Datei durch die Office-App automatisch angewendet.|
|**Automatische und empfohlene Bezeichnungen** | Wird im Azure-Portal als [Bezeichnungsbedingungen](../configure-policy-classification.md) mit integrierten Informationstypen und benutzerdefinierten Bedingungen konfiguriert, die Begriffe oder reguläre Ausdrücke verwenden <br /><br />Zu den Konfigurationsoptionen gehören: <br />– Anzahl eindeutiger und nicht eindeutiger Vorkommnisse <br /> – Mindestanzahl| Konfiguration in den Admin-Centers mit integrierten vertraulichen Informationstypen und [benutzerdefinierten Informationstypen](/microsoft-365/compliance/create-a-custom-sensitive-information-type)<br /><br />Zu den Konfigurationsoptionen gehören:  <br />– Nur Anzahl eindeutiger Vorkommnisse <br />– Mindest- und Höchstanzahl <br />– Unterstützung von AND und OR bei Informationstypen <br />– Wörterbuch mit Schlüsselwörtern<br />– Anpassbare Vertraulichkeitsstufe und Zeichennähe|
|**Unterstützung für untergeordnete Bezeichnungen auf Anlagen anordnen** | Aktiviert mit einer [erweiterten Client Einstellung](client-admin-guide-customizations.md#enable-order-support-for-sublabels-on-attachments) | Standardmäßig aktiviert, keine Konfiguration erforderlich|
|**Ändern des standardmäßigen Schutz Verhaltens für Dateitypen**| Verwenden von [Registrierungs Änderungen](client-admin-guide-file-types.md#changing-the-default-protection-level-of-files) zum Überschreiben der Standardwerte von System eigenem und generischem Schutz | Verwenden Sie [PowerShell](clientv2-admin-guide-customizations.md#change-which-file-types-to-protect) , um zu ändern, welche Dateitypen geschützt werden.|
|**Automatisches neuskaliert** | Vollständige Neueinstellungen werden automatisch ausgeführt, wenn der Scanner eine Änderung der Richtlinie oder der Beschriftungs Einstellungen erkennt. | Ab Version [2.8.85.0](unifiedlabelingclient-version-release-history.md#version-28850)können Administratoren eine vollständige erneute Überprüfung überspringen, nachdem Sie die Einstellungen für die Richtlinie oder den Inhaltsüberprüfungs Auftrag geändert haben. |
|**Netzwerkermittlung** |Die Netzwerk Ermittlungs Funktionen sind für den klassischen Scanner nicht verfügbar. | Administratoren können zusätzliche riskante Depots ermitteln, indem Sie eine bestimmte IP-Adresse oder einen bestimmten Bereich Scannen.|
| | | |

### <a name="features-not-planned-to-be-in-the-azure-information-protection-unified-labeling-client"></a>Features, die im Azure Information Protection Unified-Bezeichnungs Client nicht geplant sind

Obwohl sich der Azure Information Protection Unified Bezeichnung-Client noch in der Entwicklungsphase befindet, sind die folgenden Features und Verhaltensunterschiede vom klassischen Client derzeit nicht für die Verfügbarkeit in zukünftigen Versionen des Unified-Bezeichnungs Clients geplant: 

- Benutzerdefinierte Berechtigungen als [separate Option, die Benutzer in Office-Apps auswählen können: Word, Excel und PowerPoint](client-classify-protect.md#set-custom-permissions-for-a-document)

- In der Symbolleiste Sensitivität wird weder der **Vertraulichkeits** Titel noch eine QuickInfo angezeigt. Der Balken selbst wird im Unified-Beschriftungs Client angezeigt.

- [Nur Schutzmodus](client-protection-only-mode.md) (keine Bezeichnungen) mithilfe von Vorlagen

- PDF-Dokument als [ppdf-Datei (älteres Format)](client-admin-guide-customizations.md#dont-protect-pdf-files-by-using-the-iso-standard-for-pdf-encryption) schützen

- Anzeigen der Schaltfläche " **nicht weiterleiten** " in Outlook

- Demorichtlinien

- Unabhängige PowerShell-Cmdlets zur Verbindung mit einem Rights Management-Dienst

- Anzeige der Benutzeridentität, die eine Bezeichnung angewendet hat


### <a name="parent-labels-and-their-sublabels"></a>Übergeordnete und untergeordnete Bezeichnungen 

Der Azure Information Protection klassischen Client unterstützt keine Konfigurationen, die eine übergeordnete Bezeichnung mit untergeordneten Bezeichnungen angeben. Diese Konfigurationen umfassen die Angabe einer Standardbezeichnung sowie einer Bezeichnung für die empfohlene oder automatische Klassifizierung. Wenn eine Bezeichnung über untergeordnete Bezeichnungen verfügt, können Sie eine der untergeordneten Bezeichnungen angeben, aber nicht die übergeordnete Bezeichnung.

Aus Paritätsgründen unterstützt der Azure Information Protection-Client für einheitliche Bezeichnungen die Anwendung von übergeordneten Bezeichnungen mit untergeordneten Bezeichnungen ebenfalls nicht, auch wenn Sie diese Bezeichnungen in den Admin-Centers auswählen können. In diesem Szenario wendet der Azure Information Protection-Client für einheitliche Bezeichnungen die übergeordnete Bezeichnung nicht an.

## <a name="next-steps"></a>Nächste Schritte

Informationen zum Installieren und Konfigurieren des Azure Information Protection Unified Bezeichnung-Clients finden Sie unter:

- [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](clientv2-admin-guide.md)
- [Azure Information Protection Unified-Bezeichnung (Benutzerhandbuch)](clientv2-user-guide.md)

Weitere Informationen zur Verwendung der integrierten Bezeichnungs Lösung für Microsoft 365-apps finden Sie unter [Vertraulichkeits Bezeichnungen in Office-Apps](/microsoft-365/compliance/sensitivity-labels-office-apps).
