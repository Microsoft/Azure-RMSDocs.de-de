---
title: Voraussetzungen für den einheitlichen Bezeichnungs Scanner Azure Information Protection (AIP)
description: Listet die Voraussetzungen für die Installation und Bereitstellung des Azure Information Protection Unified Beschriftung Scanner auf.
author: batamig
ms.author: bagol
manager: rkarlin
ms.date: 01/27/2021
ms.topic: conceptual
ms.collection: M365-security-compliance
ms.service: information-protection
ms.subservice: scanner
ms.reviewer: demizets
ms.suite: ems
ms.custom: admin
ms.openlocfilehash: 4e8c4444aad6185b54a6f5b5178fa225857b71d2
ms.sourcegitcommit: 74b8d03d1ede3da12842b84546417e63897778bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/07/2021
ms.locfileid: "102414955"
---
# <a name="requirements-for-installing-and-deploying-the-azure-information-protection-unified-labeling-scanner"></a>Anforderungen für die Installation und Bereitstellung des Azure Information Protection Unified-Beschriftungs Scanners

>***Gilt für**: [Azure Information Protection](https://azure.microsoft.com/pricing/details/information-protection), Windows Server 2019, Windows Server 2016, Windows Server 2012 R2 *
>
>***Relevant für**: [nur AIP Unified Bezeichnung Client](faqs.md#whats-the-difference-between-the-azure-information-protection-classic-and-unified-labeling-clients). Informationen zum klassischen Client finden Sie unter [Voraussetzungen für klassische Client Scanner](deploy-aip-scanner-prereqs-classic.md) .*

Vergewissern Sie sich vor der Installation des Azure Information Protection lokalen Scanners, dass Ihr System die grundlegenden [Azure Information Protection Anforderungen](requirements.md)erfüllt.

Außerdem gelten die folgenden Anforderungen speziell für den Scanner:

- [Windows Server-Anforderungen](#windows-server-requirements)
- [Dienstkontenanforderungen](#service-account-requirements)
- [SQL Server-Anforderungen](#sql-server-requirements)
- [Zusätzliche Voraussetzungen für den Azure Information Protection-Client](#azure-information-protection-client-requirements)
- [Bezeichnungs Konfigurations Anforderungen](#label-configuration-requirements)
- [SharePoint-Anforderungen](#sharepoint-requirements)
- [Microsoft Office Anforderungen](#microsoft-office-requirements)
- [Dateipfad-Anforderungen](#file-path-requirements)

Wenn Sie nicht alle Anforderungen erfüllen, die für den Scanner aufgeführt sind, weil Sie von ihren Organisations Richtlinien nicht zugelassen werden, lesen Sie den Abschnitt [Alternative Konfigurationen](#deploying-the-scanner-with-alternative-configurations) .

Wenn Sie den Scanner in der Produktionsumgebung bereitstellen oder die Leistung mehrerer Scanner testen, finden Sie weitere Informationen unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

Wenn Sie bereit sind, mit der Installation und Bereitstellung Ihres Scanners zu beginnen, können Sie mit der Bereitstellung [des Azure Information Protection Scanners fortfahren, um Dateien automatisch zu klassifizieren](deploy-aip-scanner-configure-install.md)

## <a name="windows-server-requirements"></a>Windows Server-Anforderungen

Sie müssen über einen Windows Server-Computer verfügen, auf dem die Überprüfung ausgeführt werden kann. diese verfügt über die folgenden Systemspezifikationen:

|Spezifikation  |Details  |
|---------|---------|
|**Prozessor**     |4-Kern Prozessoren         |
|**RAM**     |8 GB         |
|**Speicherplatz**     |10 GB freier Speicherplatz (Durchschnitt) für temporäre Dateien. </br></br>Die Überprüfung erfordert ausreichend Speicherplatz, um für jede Datei, die überprüft wird, temporäre Dateien zu erstellen, d.h. vier Dateien pro Kern. </br></br>Der empfohlene Speicherplatz von 10 GB ermöglicht Prozessoren mit 4 Kernen, 16 Dateien mit einer Dateigröße von jeweils 625 MB zu überprüfen.
|**Betriebssystem**     |-Windows Server 2019 </br>- Windows Server 2016 </br>Windows Server 2012 R2 </br></br>**Hinweis**: zu Test-oder Evaluierungs Zwecken in einer nicht-Produktionsumgebung können Sie auch ein beliebiges Windows-Betriebssystem verwenden, das [vom Azure Information Protection-Client unterstützt](requirements.md#client-devices)wird.
|**Netzwerkverbindungen**     | Bei dem Überprüfungs Computer kann es sich um einen physischen oder virtuellen Computer mit einer schnellen und zuverlässigen Netzwerkverbindung mit den zu überprüfenden Daten speichern handeln. </br></br> Wenn die Internetverbindung aufgrund ihrer Organisations Richtlinien nicht möglich ist, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations). </br></br>Stellen Sie andernfalls sicher, dass dieser Computer über eine Internetverbindung verfügt, die die folgenden URLs über HTTPS (Port 443) zulässt:</br><br />-  \*. aadrm.com <br />-  \*. azurerms.com<br />-  \*. informationprotection.Azure.com <br /> -informationprotection.Hosting.Portal.Azure.net <br /> - \*. Aria.Microsoft.com <br />-  \*. Protection.Outlook.com |
|**NFS-Freigaben** |Dienste für NFS müssen auf dem Überprüfungs Computer bereitgestellt werden, um Scans für NFS-Freigaben zu unterstützen. <br><br>Navigieren Sie auf Ihrem Computer zum Dialogfeld "Einstellungen" (Windows- **Funktionen aktivieren oder deaktivieren)** , und wählen Sie die folgenden Elemente **aus: Dienste für NFS**  >  -**Verwaltungs Tools** und **Client für NFS**. |
| | |

## <a name="service-account-requirements"></a>Dienstkontenanforderungen

Sie müssen über ein Dienst Konto verfügen, um den Überprüfungs Dienst auf dem Windows Server-Computer auszuführen. Außerdem müssen Sie sich bei Azure AD authentifizieren und die Azure Information Protection-Richtlinie herunterladen.

Ihr Dienst Konto muss ein Active Directory Konto sein und mit Azure AD synchronisiert werden.

Wenn Sie dieses Konto aufgrund ihrer Organisations Richtlinien nicht synchronisieren können, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

Für dieses Dienstkonto gelten die folgenden Anforderungen:

|Anforderung  |Details  |
|---------|---------|
|**Lokale** Benutzerrechte Zuweisung anmelden     |Erforderlich, um die Überprüfung zu installieren und zu konfigurieren, aber nicht zum Ausführen von Scans erforderlich.  </br></br>Nachdem Sie sich vergewissert haben, dass die Überprüfung Dateien ermitteln, klassifizieren und schützen kann, können Sie diese direkt aus dem Dienst Konto entfernen.  </br></br>Wenn diese Berechtigung auch für kurze Zeit nicht möglich ist, ist dies aufgrund ihrer Organisations Richtlinien nicht möglich. Weitere Informationen hierzu finden Sie unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).         |
|**Anmeldung als Dienst** für die Zuweisung von Benutzerrechten.     |  Diese Berechtigung wird dem Dienstkonto während der Installation automatisch gewährt und ist für die Installation, Konfiguration und den Betrieb der Überprüfung erforderlich.        |
|**Berechtigungen für die Daten Depots**     |- **Dateifreigaben oder lokale Dateien**: erteilen **Sie Lese**-, **Schreib**-und Änderungs Berechtigungen zum Scannen der **Dateien und zum** anschließenden Anwenden von Klassifizierung und Schutz.  <br /><br />- **SharePoint**: Sie müssen **voll** Zugriffsberechtigungen für das Scannen der Dateien erteilen und dann Klassifizierung und Schutz auf die Dateien anwenden, die die Bedingungen in der Azure Information Protection Richtlinie erfüllen.  <br /><br />- Ermittlungs **Modus**: um die Überprüfung nur im Ermittlungs Modus auszuführen, genügt die **Lese** Berechtigung.         |
|**Für Bezeichnungen, die den Schutz erneut schützen oder entfernen**     | Um sicherzustellen, dass die Überprüfung stets Zugriff auf geschützte Dateien hat, machen Sie dieses Konto als [Administrator für Azure Information Protection](configure-super-users.md) , und stellen Sie sicher, dass die Administrator Funktion aktiviert ist. </br></br>Wenn Sie [Onboarding](activate-service.md#configuring-onboarding-controls-for-a-phased-deployment) -Steuerelemente für eine stufenweise Bereitstellung implementiert haben, stellen Sie außerdem sicher, dass das Dienst Konto in den Onboarding-Steuerelementen enthalten ist, die Sie konfiguriert haben.|
|**Bestimmte** Überprüfung auf URL-Ebene: |Um Standorte und untergeordnete Standorte [unter einer bestimmten URL](#deploying-the-scanner-with-alternative-configurations)zu überprüfen und zu ermitteln, erteilen Sie dem Scanner-Konto auf Farmebene **Site Collector-Prüfer** Rechte.|
| | |

## <a name="sql-server-requirements"></a>SQL Server-Anforderungen

Verwenden Sie zum Speichern der Überprüfungs Konfigurationsdaten einen SQL-Server mit den folgenden Anforderungen:

- **Eine lokale Instanz oder eine Remote Instanz.**

    Es wird empfohlen, SQL Server und den Scanner-Dienst auf unterschiedlichen Computern zu verwenden, es sei denn, Sie arbeiten mit einer kleinen Bereitstellung. Außerdem wird empfohlen, dass Sie über eine dedizierte SQL-Instanz verfügen, die nur für die Überprüfungs Datenbank dient und die nicht mit anderen Anwendungen gemeinsam genutzt wird.

    Wenn Sie an einem freigegebenen Server arbeiten, stellen Sie sicher, dass die [Empfohlene Anzahl von Kernen](#windows-server-requirements) für die Ausführung der Überprüfungs Datenbank frei ist.

    SQL Server 2016 ist die Mindestversion für die folgenden Editionen:

    - SQL Server Enterprise

    - SQL Server Standard

    - SQL Server Express (nur für Testumgebungen empfohlen)

- **Ein Konto mit der sysadmin-Rolle zum Installieren des Scanners.**

    Die sysadmin-Rolle ermöglicht dem Installationsvorgang das automatische Erstellen der Überprüfungs Konfigurationsdatenbank und das Erteilen der erforderlichen **db_owner** Rolle für das Dienst Konto, von dem die Überprüfung ausgeführt wird.

    Wenn Ihnen die sysadmin-Rolle nicht gewährt werden kann oder wenn Ihre Organisations Richtlinien erfordern, dass Datenbanken manuell erstellt und konfiguriert werden, finden Sie weitere Informationen unter Bereitstellen [des Scanners mit alternativen Konfigurationen](#deploying-the-scanner-with-alternative-configurations).

- **Capacity** (Kapazität): Informationen zur Kapazitäts Orientierung finden Sie unter [Speicheranforderungen und Kapazitätsplanung für SQL Server](#storage-requirements-and-capacity-planning-for-sql-server).

- **[Sortierung](/sql/relational-databases/collations/collation-and-unicode-support)ohne Beachtung**

> [!NOTE]
> Mehrere Konfigurations Datenbanken auf demselben SQL Server werden unterstützt, wenn Sie einen benutzerdefinierten Cluster Namen für die Überprüfung angeben oder wenn Sie die Vorschauversion der Überprüfung verwenden.
>
### <a name="storage-requirements-and-capacity-planning-for-sql-server"></a>Speicheranforderungen und Kapazitätsplanung für SQL Server

Der erforderliche Speicherplatz für die Konfigurations Datenbank des Scanners und die Angabe des Computers, auf dem SQL Server ausgeführt wird, kann je nach Umgebung variieren. Daher empfehlen wir Ihnen, ihre eigenen Tests durchzuführen. Verwenden Sie die folgende Anleitung als Ausgangspunkt.

Weitere Informationen finden Sie unter [Optimieren der Leistung des Scanners](deploy-aip-scanner-configure-install.md#optimize-scanner-performance).

Die Datenträger Größe für die scannerkonfigurationsdatenbank variiert für jede Bereitstellung. Verwenden Sie die folgende Gleichung als Leitfaden:

```cli
100 KB + <file count> *(1000 + 4* <average file name length>)
```

Um z. b. 1 Million Dateien mit einer durchschnittlichen Dateinamen Länge von 250 Bytes zu scannen, müssen Sie 2 GB Speicherplatz zuweisen.

Für mehrere Scanner:

- **Bis zu 10 Scanner**, verwenden Sie Folgendes:

    - 4-Kern Prozessoren
    - 8 GB RAM empfohlen

- **Mehr als 10 Scanner** (max. 40), verwenden Sie Folgendes:
    - 8-Kern-Prozesse
    - 16 GB RAM empfohlen

## <a name="azure-information-protection-client-requirements"></a>Zusätzliche Voraussetzungen für den Azure Information Protection-Client

Auf dem Windows Server-Computer muss entweder die [aktuelle Version der allgemeinen Verfügbarkeit](./rms-client/unifiedlabelingclient-version-release-history.md) des Azure Information Protection-Clients installiert sein.

Weitere Informationen finden Sie unter [Unified Bezeichnung Client Admin Guide](./rms-client/clientv2-admin-guide.md#installing-the-azure-information-protection-scanner).

> [!IMPORTANT]
> Sie müssen den kompletten Client für die Überprüfung installieren. Installieren Sie den Client nicht nur mit dem PowerShell-Modul.
>

## <a name="label-configuration-requirements"></a>Bezeichnungs Konfigurations Anforderungen

Sie müssen mindestens eine Vertraulichkeits Bezeichnung in einer der Microsoft 365 die die Bezeichnung admin Centers für das Scanner-Konto konfiguriert haben, um die Klassifizierung und optional Schutz zu übernehmen.

Microsoft 365 bezeichnen admin Centers umfasst die Microsoft 365 Security Center, das Microsoft 365 Compliance Center und das Microsoft 365 Security and Compliance Center. 

Das *Scanner-Konto* ist das Konto, das Sie im **delegateduser** -Parameter des Cmdlets " [Set-aipauthentication](/powershell/module/azureinformationprotection/set-aipauthentication) " angeben, wenn Sie den Scanner konfigurieren. 

Wenn Ihre Bezeichnungen keine automatischen Bezeichnungen aufweisen, sehen Sie sich die [Anweisungen für alternative Konfigurationen unten an](#restriction-your-labels-do-not-have-auto-labeling-conditions) .

Weitere Informationen finden Sie unter

- [Informationen zu Empfindlichkeits Bezeichnungen](/microsoft-365/compliance/sensitivity-labels)
- [Automatisches Anwenden einer Vertraulichkeitsbezeichnung auf Inhalte](/microsoft-365/compliance/apply-sensitivity-label-automatically)
- [Einschränken des Zugriffs auf Inhalte mithilfe der Verschlüsselung in Vertraulichkeitsbezeichnungen](/microsoft-365/compliance/encryption-sensitivity-labels)
- [Konfigurieren und Installieren des Azure Information Protection Unified-Beschriftungs Scanner](deploy-aip-scanner-configure-install.md)

## <a name="sharepoint-requirements"></a>SharePoint-Anforderungen

Stellen Sie sicher, dass Ihr SharePoint-Server die folgenden Anforderungen erfüllt, um SharePoint-Dokument Bibliotheken und-Ordner zu überprüfen:

|Anforderung  |BESCHREIBUNG  |
|---------|---------|
|**Unterstützte Versionen** | Folgende Versionen werden unterstützt: SharePoint 2019, SharePoint 2016 und SharePoint 2013. <br> Andere Versionen von SharePoint werden für die Überprüfung nicht unterstützt.     |
|**Versionsverwaltung**     |  Wenn Sie die [Versions](/sharepoint/governance/versioning-content-approval-and-check-out-planning)Verwaltung verwenden, wird die zuletzt veröffentlichte Version vom Scanner überprüft und beschriftet. <br><br>Wenn die Überprüfung eine Datei und eine [Genehmigung von Inhalten](/sharepoint/governance/versioning-content-approval-and-check-out-planning#plan-content-approval) erfordert, muss die bezeichnete Datei als verfügbar für Benutzer verfügbar sein.       |
|**Große SharePoint-Farmen** |Überprüfen Sie für große SharePoint-Farmen, ob Sie den Schwellwert der Listenansicht (standardmäßig 5.000) erhöhen müssen, damit der Scanner auf alle Dateien zugreifen kann. <br><br>Weitere Informationen finden Sie unter [Verwalten von großen Listen und Bibliotheken in SharePoint](https://support.office.com/article/manage-large-lists-and-libraries-in-sharepoint-b8588dae-9387-48c2-9248-c24122f07c59#__bkmkchangelimit&ID0EAABAAA=Server). |
|**Lange Dateipfade**  |Wenn Sie über lange Dateipfade in SharePoint verfügen, stellen Sie sicher, dass der [HttpRuntime. maxurllength](/dotnet/api/system.web.configuration.httpruntimesection.maxurllength) -Wert des SharePoint-Servers größer als die Standard-260-Zeichen ist. <br><br>Weitere Informationen finden Sie unter [vermeiden von Überprüfungs Timeouts in SharePoint](rms-client/clientv2-admin-guide-customizations.md#avoid-scanner-timeouts-in-sharepoint). | 
| | |

## <a name="microsoft-office-requirements"></a>Microsoft Office Anforderungen

Zum Scannen von Office-Dokumenten müssen Ihre Dokumente in einem der folgenden Formate vorliegen:

- Microsoft Office 97-2003
- Office Open XML-Formate für Word, Excel und PowerPoint

Weitere Informationen finden Sie [unter vom Azure Information Protection Unified Bezeichnung-Client unterstützte Dateitypen](./rms-client/clientv2-admin-guide-file-types.md).

## <a name="file-path-requirements"></a>Dateipfad-Anforderungen

Zum Scannen von Dateien müssen standardmäßig die Dateipfade maximal 260 Zeichen enthalten.

Zum Überprüfen von Dateien mit Dateipfaden mit mehr als 260 Zeichen installieren Sie die Überprüfung auf einem Computer mit einer der folgenden Windows-Versionen, und konfigurieren Sie den Computer nach Bedarf:

|Windows-Version  |BESCHREIBUNG  |
|---------|---------|
|**Windows 2016 oder höher**     |   Konfigurieren des Computers zur Unterstützung von langen Pfaden      |
|**Windows 10 oder Windows Server 2016**     | Definieren Sie die folgende [Gruppenrichtlinien Einstellung](/archive/blogs/jeremykuhne/net-4-6-2-and-long-paths-on-windows-10): **lokale Computer Richtlinie**  >  **Computerkonfiguration**  >  **Administrative Vorlagen**  >  **alle Einstellungen**  >  **aktivieren Win32 Long-Pfade**.    </br></br>Weitere Informationen zur Unterstützung von langen Dateipfaden in diesen Versionen finden Sie im Abschnitt [Maximale Pfadlängen Beschränkung](/windows/desktop/FileIO/naming-a-file#maximum-path-length-limitation) in der Windows 10-Entwicklerdokumentation.    |
|**Windows 10, Version 1607 oder höher**     |  Entscheiden Sie sich für die aktualisierten **MAX_PATH** Funktionen. Weitere Informationen finden Sie unter [Aktivieren von langen Pfaden in Windows 10, Version 1607 und](/windows/win32/fileio/naming-a-file#enable-long-paths-in-windows-10-version-1607-and-later)höher.      |
| | |


## <a name="deploying-the-scanner-with-alternative-configurations"></a>Bereitstellen der Überprüfung mit alternativen Konfigurationen

Die oben aufgeführten Voraussetzungen sind die Standardanforderungen für die Scanner-Bereitstellung und werden empfohlen, da Sie die einfachste Überprüfungs Konfiguration unterstützen.

Die Standardanforderungen sollten für die ersten Tests geeignet sein, damit Sie die Funktionen des Scanners überprüfen können.

In einer Produktionsumgebung können sich die Richtlinien Ihrer Organisation jedoch von den Standardanforderungen unterscheiden. Der Scanner kann die folgenden Änderungen mit zusätzlicher Konfiguration unterstützen:

- [Alle Sites und untergeordneten Sites unter einer bestimmten URL ermitteln und überprüfen](#discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url)

- [Einschränkung: der Überprüfungs Server kann keine Internetverbindung haben.](#restriction-the-scanner-server-cannot-have-internet-connectivity)

- [Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.](#restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity)

- [Einschränkung: dem Dienst Konto für die Überprüfung kann nicht die Berechtigung zum **lokalen anmelden** erteilt werden.](#restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right)

- [Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.](#restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually)

- [Einschränkung: ihre Bezeichnungen haben keine automatischen Beschriftungs Bedingungen.](#restriction-your-labels-do-not-have-auto-labeling-conditions)

### <a name="discover-and-scan-all-sharepoint-sites-and-subsites-under-a-specific-url"></a>Alle SharePoint-Sites und-untergeordneten Sites unter einer bestimmten URL ermitteln und überprüfen

Der Scanner kann alle SharePoint-Sites und-untergeordneten Sites unter einer bestimmten URL mit der folgenden Konfiguration ermitteln und überprüfen:

1. Starten Sie die **SharePoint-zentral Administration**.

1. Klicken Sie auf der Website der **SharePoint-zentral Administration** im Abschnitt **Anwendungs Verwaltung** auf **Webanwendungen verwalten**.

1. Klicken Sie hierauf, um die Webanwendung hervorzuheben, deren Berechtigungs Richtlinien Ebene Sie verwalten möchten.

1. Wählen Sie die relevante Farm aus, und klicken Sie dann auf **Berechtigungen verwalten Richtlinien Ebenen**.

1. Wählen Sie in den Berechtigungen für die **Website Sammlungs Berechtigungen** die Option **Website Sammlungs Prüfer** aus, erteilen Sie in der Liste der Berechtigungen die Option **Anwendungs Seiten anzeigen** , und benennen Sie die neue Richtlinie für **AIP Scanner Site Collection Auditor und Viewer**.

1. Fügen Sie den scannerbenutzer der neuen Richtlinie hinzu, und erteilen Sie die **Website Sammlung** in der Berechtigungs Liste.   

1. Fügen Sie eine URL des SharePoint-Hosts hinzu, der Websites oder unter Websites hostet, die überprüft werden müssen. Weitere Informationen finden Sie unter [configure the Scanner in the Azure-Portal](deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal).

Weitere Informationen zum Verwalten von SharePoint-Richtlinien Ebenen finden Sie unter [Verwalten von Berechtigungs Richtlinien für eine Webanwendung](/sharepoint/administration/manage-permission-policies-for-a-web-application).

### <a name="restriction-the-scanner-server-cannot-have-internet-connectivity"></a>Einschränkung: der Überprüfungs Server kann keine Internetverbindung haben.

Obwohl der Unified Label-Client keinen Schutz ohne Internetverbindung anwenden kann, kann der Scanner weiterhin Bezeichnungen auf der Grundlage importierter Richtlinien anwenden.

Verwenden Sie eine der folgenden Methoden, um einen getrennten Computer zu unterstützen:

- [Verwenden des Azure-Portal](#use-the-azure-portal-with-a-disconnected-computer) (empfohlen, wenn möglich)

- [Verwenden von PowerShell](#use-powershell-with-a-disconnected-computer)

#### <a name="use-the-azure-portal-with-a-disconnected-computer"></a>Verwenden des Azure-Portal mit einem getrennten Computer

Führen Sie die folgenden Schritte aus, um einen vom Azure-Portal getrennten Computer zu unterstützen:

1.  Konfigurieren Sie Bezeichnungen in der Richtlinie, und verwenden Sie dann das [Verfahren zur Unterstützung von getrennten Computern](rms-client/clientv2-admin-guide-customizations.md#support-for-disconnected-computers) , um die Offline Klassifizierung und-Bezeichnung zu aktivieren

1. Aktivieren Sie die Offline Verwaltung für Inhalts-und Netzwerk Scanaufträge wie folgt:

    **Aktivieren Sie die Offline Verwaltung für Inhalts Scanaufträge**:

    1. Legen Sie den Scanner mithilfe des Cmdlets [Set-aipscannerconfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) im **Offline** Modus fest.

    1. Konfigurieren Sie die Überprüfung in der Azure-Portal, indem Sie einen Scanner-Cluster erstellen. Weitere Informationen finden Sie unter [configure the Scanner in the Azure-Portal](deploy-aip-scanner-configure-install.md#configure-the-scanner-in-the-azure-portal).

    1. Exportieren Sie den Inhalts Auftrag aus dem Bereich **Azure Information Protection-Inhalts Scanaufträge** mithilfe der **Export** Option.
    
    1. Importieren Sie die Richtlinie mithilfe des [Import-aipscannerconfiguration-](/powershell/module/azureinformationprotection/import-aipscannerconfiguration) Cmdlets. 
    
    Die Ergebnisse für Offline-Inhalts Scanaufträge befinden sich unter: **%LocalAppData%\microsoft\msip\scanner\reports** .
    
    **Offline Verwaltung von Netzwerk Scan Aufträgen aktivieren**:

    1. Legen Sie mithilfe des Cmdlets [Set-mipnetworkdiscoveryconfiguration](/powershell/module/azureinformationprotection/set-mipnetworkdiscoveryconfiguration) den Netzwerk Ermittlungsdienst (Public Preview) für die Funktion im Offline Modus fest.

    1. Konfigurieren Sie den Netzwerk Scanauftrag in der Azure-Portal. Weitere Informationen finden Sie unter [Erstellen eines Netzwerk Scan Auftrags](deploy-aip-scanner-configure-install.md#create-a-network-scan-job-public-preview).
    
    1. Exportieren Sie den Netzwerküberprüfungs-Auftrag mithilfe der **Export** Option aus dem Bereich **Azure Information Protection-Netzwerk Scanaufträge (Vorschau)** . 
    
    1.  Importieren Sie den Netzwerk Scanauftrag mithilfe der Datei, die mit dem Cluster Namen übereinstimmt, mithilfe des [Import-mipnetworkdiscoveryconfiguration](/powershell/module/azureinformationprotection/import-mipnetworkdiscoveryconfiguration) -Cmdlets.  
    
    Die Ergebnisse für Offline-Netzwerk Scanaufträge befinden sich unter: **%LocalAppData%\microsoft\msip\scanner\reports** .

#### <a name="use-powershell-with-a-disconnected-computer"></a>Verwenden von PowerShell mit einem getrennten Computer

Führen Sie das folgende Verfahren aus, um einen nicht verbundenen Computer nur mit PowerShell zu unterstützen.

> [!IMPORTANT]
> Administratoren von [Azure China 21ViaNet-Überprüfungs Servern](/microsoft-365/admin/services-in-china/parity-between-azure-information-protection#manage-azure-information-protection-content-scan-jobs) *müssen* dieses Verfahren verwenden, um Ihre Inhalts Scanaufträge zu verwalten.
> 

**Verwalten Sie Ihre Inhalts Scanaufträge nur mit PowerShell**:

1. Legen Sie den Scanner mithilfe des Cmdlets [Set-aipscannerconfiguration](/powershell/module/azureinformationprotection/set-aipscannerconfiguration) im **Offline** Modus fest.

1. Erstellen Sie mit dem Cmdlet " [Set-aipscannercontentscanjob](/powershell/module/azureinformationprotection/set-aipscannercontentscanjob) " einen neuen inhaltscanauftrag, und verwenden Sie dabei den obligatorischen `-Enforce On` Parameter.

1. Fügen Sie Ihre Depots mithilfe des Cmdlets [Add-aipscannerrepository](/powershell/module/azureinformationprotection/add-aipscannerrepository) mit dem Pfad zu dem Repository hinzu, das Sie hinzufügen möchten.

    > [!TIP]
    > Um zu verhindern, dass das Repository Einstellungen aus Ihrem inhaltscanauftrag erbt, fügen Sie den `OverrideContentScanJob On` Parameter sowie die Werte für zusätzliche Einstellungen hinzu.
    >
    > Um Details für ein vorhandenes Repository zu bearbeiten, verwenden Sie den Befehl [Set-aipscannerrepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) .
    >
 
1. Verwenden Sie die Cmdlets [Get-aipscannercontentscanjob](/powershell/module/azureinformationprotection/get-aipscannercontentscanjob) und [Get-aipscannerrepository](/powershell/module/azureinformationprotection/get-aipscannerrepository) , um Informationen zu den aktuellen Einstellungen Ihres Inhalts Scan Auftrags zurückzugeben. 

1. Verwenden Sie den Befehl [Set-aipscannerrepository](/powershell/module/azureinformationprotection/set-aipscannerrepository) , um Details für ein vorhandenes Repository zu aktualisieren.

1. Führen Sie den Content Scan-Auftrag mit dem Cmdlet [Start-aipscan](/powershell/module/azureinformationprotection/start-aipscan) sofort aus, wenn dies erforderlich ist. 

    Die Ergebnisse für Offline-Inhalts Scanaufträge befinden sich unter: **%LocalAppData%\microsoft\msip\scanner\reports** .

1. Wenn Sie ein Repository oder einen gesamten inhaltscanauftrag entfernen müssen, verwenden Sie die folgenden Cmdlets:

    - [Remove-aipscannercontentscanjob](/powershell/module/azureinformationprotection/remove-aipscannercontentscanjob)
    - [Remove-AIPScannerRepository](/powershell/module/azureinformationprotection/remove-aipscannerrepository)

### <a name="restriction-you-cannot-be-granted-sysadmin-or-databases-must-be-created-and-configured-manually"></a>Einschränkung: Die Sysadmin-Rolle kann nicht gewährt werden oder Datenbanken müssen manuell erstellt und konfiguriert werden.

Verwenden Sie die folgenden Verfahren, um bei Bedarf manuell Datenbanken zu erstellen und die **db_owner** Rolle zu erteilen.

- [Verfahren für die Scanner-Datenbank](#manually-create-a-database-and-user-for-the-scanner-and-grant-db_owner-rights)
- [Verfahren für die Netzwerk Ermittlungs Datenbank](#manually-create-a-database-and-user-for-the-network-discovery-service-and-grant-db_owner-rights)

Wenn Sie die sysadmin-Rolle *vorübergehend* zur Installation der Überprüfung erhalten können, können Sie diese Rolle entfernen, wenn die Überprüfung des Scanners beendet ist.

Führen Sie je nach den Anforderungen Ihrer Organisation einen der folgenden Schritte aus:

|Einschränkung  |BESCHREIBUNG  |
|---------|---------|
|**Die sysadmin-Rolle kann vorübergehend vorhanden sein.**     |  Wenn Sie vorübergehend über die sysadmin-Rolle verfügen, wird die Datenbank automatisch für Sie erstellt, und dem Dienst Konto für den Scanner werden automatisch die erforderlichen Berechtigungen erteilt. <br><br>Das Benutzerkonto, das die Überprüfung konfiguriert, erfordert jedoch weiterhin die **db_owner** Rolle für die scannerkonfigurationsdatenbank. Wenn Sie nur über die sysadmin-Rolle verfügen, bis die Überprüfung des Scanners fertiggestellt ist, erteilen Sie dem Benutzerkonto die **db_owner** Rolle manuell.       |
|**Sie können nicht über die sysadmin-Rolle verfügen.**     |  Wenn Sie die sysadmin-Rolle nicht auch vorübergehend erhalten können, müssen Sie einen Benutzer mit sysadmin-Berechtigung bitten, vor der Installation des Scanners manuell eine Datenbank zu erstellen. <br><br>Für diese Konfiguration muss die **db_owner** Rolle den folgenden Konten zugewiesen werden: <br>-Dienst Konto für den Scanner<br>-Benutzerkonto für die Scannerinstallation<br>-Benutzerkonto für Scannerkonfiguration <br><br>In der Regel verwenden Sie dasselbe Benutzerkonto, um die Überprüfung zu installieren und zu konfigurieren. Wenn Sie unterschiedliche Konten verwenden, benötigen beide die **db_owner** Rolle für die scannerkonfigurationsdatenbank. Erstellen Sie diesen Benutzer und die Rechte bei Bedarf. Wenn Sie einen eigenen Cluster Namen angeben, wird die Konfigurations Datenbank **AIPScannerUL_<cluster_name>** benannt.  |
| | |

Außerdem zu beachten:

- Sie müssen ein lokaler Administrator auf dem Server sein, auf dem die Überprüfung ausgeführt wird.
- Das Dienst Konto, unter dem der Scanner ausgeführt wird, muss über Vollzugriff auf die folgenden Registrierungsschlüssel verfügen:

    - `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\MSIPC\Server`
    - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\Server`

Wenn nach dem Konfigurieren dieser Berechtigungen ein Fehler angezeigt wird, wenn Sie den Scanner installieren, kann der Fehler ignoriert werden, und Sie können den Überprüfungs Dienst manuell starten.

#### <a name="manually-create-a-database-and-user-for-the-scanner-and-grant-db_owner-rights"></a>Manuelles Erstellen einer Datenbank und eines Benutzers für die Überprüfung und erteilen db_owner Rechte

Wenn Sie Ihre Scanner-Datenbank manuell erstellen und/oder einen Benutzer erstellen und **db_owner** Rechte für die Datenbank erteilen müssen, bitten Sie den sysadmin, die folgenden Schritte auszuführen:

1. Erstellen Sie eine Datenbank für Scanner:

    ```sql
    **CREATE DATABASE AIPScannerUL_[clustername]**

    **ALTER DATABASE AIPScannerUL_[clustername] SET TRUSTWORTHY ON**
    ```

2. Erteilen Sie dem Benutzer, der den Installations Befehl ausführt, Rechte, und wird zum Ausführen von Überprüfungs Verwaltungs Befehlen verwendet. Führen Sie das folgende Skript aus:

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    USE DBName IF NOT EXISTS (select * from sys.database_principals where sid = SUSER_SID('domain\user')) BEGIN declare @X nvarchar(500) Set @X = 'CREATE USER ' + quotename('domain\user') + ' FROM LOGIN ' + quotename('domain\user'); exec sp_addrolemember 'db_owner', 'domain\user' exec(@X) END
    ```

3. Erteilen Sie die Rechte für das Scanner-Dienst Konto. Führen Sie das folgende Skript aus:

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    ```

#### <a name="manually-create-a-database-and-user-for-the-network-discovery-service-and-grant-db_owner-rights"></a>Manuelles Erstellen einer Datenbank und eines Benutzers für den Netzwerk Ermittlungsdienst und erteilen db_owner Rechte

Wenn Sie die Datenbank für die [Netzwerk](deploy-aip-scanner-configure-install.md#create-a-network-scan-job-public-preview) Ermittlung manuell erstellen und/oder einen Benutzer erstellen und **db_owner** Rechte für die Datenbank erteilen müssen, bitten Sie den sysadmin, die folgenden Schritte auszuführen:

1. Erstellen Sie eine Datenbank für den Netzwerk Ermittlungsdienst:

    ```sql
    **CREATE DATABASE AIPNetworkDiscovery_[clustername]**

    **ALTER DATABASE AIPNetworkDiscovery_[clustername] SET TRUSTWORTHY ON**
    ```

2. Erteilen Sie dem Benutzer, der den Installations Befehl ausführt, Rechte, und wird zum Ausführen von Überprüfungs Verwaltungs Befehlen verwendet. Führen Sie das folgende Skript aus:

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    USE DBName IF NOT EXISTS (select * from sys.database_principals where sid = SUSER_SID('domain\user')) BEGIN declare @X nvarchar(500) Set @X = 'CREATE USER ' + quotename('domain\user') + ' FROM LOGIN ' + quotename('domain\user'); exec sp_addrolemember 'db_owner', 'domain\user' exec(@X) END
    ```

3. Erteilen Sie dem Überprüfungs Dienst Konto Rechte. Führen Sie das folgende Skript aus:

    ```sql
    if not exists(select * from master.sys.server_principals where sid = SUSER_SID('domain\user')) BEGIN declare @T nvarchar(500) Set @T = 'CREATE LOGIN ' + quotename('domain\user') + ' FROM WINDOWS ' exec(@T) END
    ```
### <a name="restriction-the-service-account-for-the-scanner-cannot-be-granted-the-log-on-locally-right"></a>Einschränkung: Die Berechtigung zur **lokalen Anmeldung** kann nicht für das Dienstkonto gewährt werden.

Wenn Ihre Organisations Richtlinien das **lokale anmelden** für Dienst Konten verbieten, verwenden Sie den *onbehalfof* -Parameter mit "Set-aipauthentication".

Weitere Informationen finden Sie unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

### <a name="restriction-the-scanner-service-account-cannot-be-synchronized-to-azure-active-directory-but-the-server-has-internet-connectivity"></a>Einschränkung: das Überprüfungs Dienst Konto kann nicht mit Azure Active Directory synchronisiert werden, aber der Server verfügt über eine Internetverbindung.

Sie können ein Konto haben, um den Überprüfungsdienst auszuführen, und ein anderes Konto für die Authentifizierung bei Azure Active Directory verwenden:

- Verwenden Sie **für das Scanner-Dienst Konto** ein lokales Windows-Konto oder ein Active Directory Konto.

- Geben Sie **für das Azure Active Directory-Konto** Ihr lokales Konto für den *onbehalfof* -Parameter mit "Set-aipauthentication" an. Weitere Informationen finden Sie unter [Unbeaufsichtigtes Bezeichnen von Dateien für Azure Information Protection](./rms-client//clientv2-admin-guide-powershell.md#how-to-label-files-non-interactively-for-azure-information-protection).

### <a name="restriction-your-labels-do-not-have-auto-labeling-conditions"></a>Einschränkung: ihre Bezeichnungen haben keine automatischen Beschriftungs Bedingungen.

Wenn Ihre Bezeichnungen keine automatischen Bezeichnungen aufweisen, sollten Sie beim Konfigurieren Ihres Scanners eine der folgenden Optionen verwenden:

|Option  |BESCHREIBUNG  |
|---------|---------|
|**Alle Informationstypen ermitteln**     |  Legen Sie in Ihrem [inhaltscanauftrag](deploy-aip-scanner-configure-install.md#create-a-content-scan-job)die Option zu **ermittelnde Informationstypen** auf **alle** fest. </br></br>Mit dieser Option wird der Inhalts Überprüfungs Auftrag so festgelegt, dass der Inhalt auf alle sensiblen Informationstypen überprüft wird.      |
|**Empfohlene Bezeichnung verwenden**     |  Legen Sie im [Inhalts Überprüfungs Auftrag](deploy-aip-scanner-configure-install.md#create-a-content-scan-job)die Option **Empfohlene Bezeichnung als automatisch behandeln** auf ein **fest.**</br></br> Mit dieser Einstellung wird der Scanner so konfiguriert, dass alle empfohlenen Bezeichnungen automatisch auf ihren Inhalt angewendet werden.      |
|**Definieren einer Standard Bezeichnung**     |   Definieren Sie eine Standard Bezeichnung in der [Richtlinie](/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do), im [Inhalts Scanauftrag](deploy-aip-scanner-configure-install.md#create-a-content-scan-job)oder im [Repository](deploy-aip-scanner-configure-install.md#apply-a-default-label-to-all-files-in-a-data-repository). </br></br>In diesem Fall wendet der Scanner die Standard Bezeichnung auf alle gefundenen Dateien an.       |
| | |

## <a name="next-steps"></a>Nächste Schritte

Wenn Sie sich vergewissert haben, dass Ihr System die Überprüfungs Voraussetzungen erfüllt, fahren Sie mit dem bereitstellen [des Azure Information Protection Scanners fort, um Dateien automatisch zu klassifizieren und zu schützen](deploy-aip-scanner-configure-install.md)

Eine Übersicht über den Scanner finden Sie unter Bereitstellen [des Azure Information Protection Scanners zum automatischen klassifizieren und schützen von Dateien](deploy-aip-scanner.md).

**Weitere Informationen**:

- Interessiert es Sie, wie das Core Services Engineering and Operations-Team bei Microsoft diese Überprüfung implementiert hat?  Lesen Sie die technische Fallstudie [Automatisieren des Datenschutzes mit der Azure Information Protection-Überprüfung](https://www.microsoft.com/itshowcase/Article/Content/1070/Automating-data-protection-with-Azure-Information-Protection-scanner).

- Sie können Dateien auch mit PowerShell interaktiv klassifizieren und von Ihrem Desktopcomputer aus schützen. Weitere Informationen zu diesem und anderen Szenarien, in denen PowerShell verwendet wird, finden [Sie unter Verwenden von PowerShell mit dem Azure Information Protection Unified Bezeichnung-Client](./rms-client/clientv2-admin-guide-powershell.md).